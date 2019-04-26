---
ms.date: 10/13/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: Mühendisler için İstenen Durum Yapılandırmasına Genel Bakış
ms.openlocfilehash: 0e599c2218cd2df29dbd0529006be5e1ef17ce5f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079991"
---
# <a name="desired-state-configuration-overview-for-engineers"></a>Mühendisler için İstenen Durum Yapılandırmasına Genel Bakış

Bu belge, PowerShell Desired State Configuration (DSC) yararlarını Geliştirici ve işlem ekipleri için tasarlanmıştır.
DSC değeri daha yüksek düzey bir görünümünü sağlar için lütfen bkz [Desired State Configuration ' ne genel bakış karar alma](decisionMaker.md)

## <a name="benefits-of-desired-state-configuration"></a>Desired State Configuration ' ın avantajları

DSC için bulunmaktadır:

- İçinde Windows scripting karmaşıklığını azaltın
- Yineleme hızını artırın

"Sürekli dağıtım" kavramı daha önemli hale gelmektedir.
Sürekli dağıtım, birden çok kez günde sık, büyük olasılıkla dağıtma yeteneği anlamına gelir.
Bu dağıtımları amacı olan bir şeyi düzeltmemeyi ancak bir kolayca yayımlanan almak için.
Yeni özellikleri geliştirme işleminde göz önünde aracılığıyla sorunsuz ve mümkün olduğunca güvenilir bir şekilde alarak, saat değeri yeni iş mantığı azaltın.

Bulut bilgi işlemin son durumu ortam burada metin olarak bildirilmiş ve bir dağıtım altyapısı için yayımlanan bir "bildirim" Şablon modeli kullanan bir dağıtım çözümü gelir doğru taşıyın.
Herhangi bir zamanda dağıtımın bir bitiş durumuna güvence altına almak için tutarlı bir şekilde yinelenebilir çünkü bu dağıtım yöntemi, uygun ölçekte, hızlı bir değişiklik tehdit hatalarına karşı dayanıklılık ile olanak tanır.
Araçlar ve bu işlemleri Otomasyon aracılığıyla stilini destekleyen hizmetleri oluşturmak, bu değişiklikleri yanıt olan.

DSC, bir bildirim temelli sağlayan bir platform ve etkili (tekrarlanabilir) dağıtım, yapılandırma ve uyumluluk içindir.
DSC platform bileşenleri veri merkezinizin hataları önler ve pahalı dağıtım hatalarını önler doğru yapılandırma olmasını sağlamak sağlar.
DSC yapılandırmaları uygulama kodunun bir parçası olarak kabul ederek, DSC sürekli dağıtımı sağlar.
DSC yapılandırması, uygulamayı dağıtmak için ihtiyacınız olan bilgileri her zaman güncel ve kullanılmaya hazır olduğundan emin olmanın uygulamanın bir parçası olarak güncelleştirilmelidir.

## <a name="i-have-powershell-why-do-i-need-desired-state-configuration"></a>"Ben PowerShell Desired State Configuration neden ihtiyacım var?"

DSC yapılandırmaları ayrı hedefi veya "ne yapmak istiyorum", yürütme veya "ne yapmak istiyorum."
Bu, yürütme mantığı içindeki kaynakların içerdiği anlamına gelir.
Kullanıcıların nasıl uygulamak veya bu özellik için bir DSC kaynağı kullanılabilir olduğunda, bir özellik dağıtmak bilmeniz gerekmez.
Bu, kullanıcının kendi dağıtım yapısı üzerinde odaklanmanıza izin verir.

Örneğin, PowerShell betikleri gibi görünmelidir:
```powershell
# Create a share in Windows Server 8
New-SmbShare -Name MyShare -Path C:\Demo\Temp -FullAccess Alice -ReadAccess Bob
```
Bu, basit, anlaşılır ve basit betiğidir.
Bununla birlikte, bu betiği üretime geçirmeden çalışırsanız, birkaç bir sorunla karşılaşırsanız çalışır.
Arka arkaya iki kez çalışan betik ne olacak?
Bob paylaşıma tam erişimi daha önce varsa ne olur?

Bu sorunlar için dengelemek için komut dosyasının "gerçek" bir sürümünü gibi bir şey daha yakından görünür:
```powershell
# But actually creating a share in an idempotent way would be

$shareExists = $false
$smbShare = Get-SmbShare -Name $Name -ErrorAction SilentlyContinue
if($smbShare -ne $null)
{
    Write-Verbose -Message "Share with name $Name exists"
    $shareExists = $true
}

if ($shareExists -eq $false)
{
    Write-Verbose "Creating share $Name to ensure it is Present"
    New-SmbShare @psboundparameters
}
else
{
    # Need to call either Set-SmbShare or *ShareAccess cmdlets
    if ($psboundparameters.ContainsKey("ChangeAccess"))
    {
       #...etc, etc, etc
    }
}
```

Bu betik, karmaşık olsun, Eskinin mantık ve hata işleme ile.
Bitti, istediğiniz artık belirten çünkü kod daha karmaşıktır ama *nasıl yapılacağını*.

Temel mantığını hemen soyutlanır ve DSC bitti istediğinizi varsayalım sağlar.

```powershell
# A configuration is a special kind of PowerShell function
Configuration Sample_Share
{
   Import-DscResource -Module xSmbShare
   # Nodes are the endpoint we wish to configure
   # A Configuration block can have zero or more Node blocks
   Node $NodeName
   {
      # Next, specify one or more resource blocks
      # Resources are simply PowerShell modules that
      # implement the logic of "how" to execute a task
      xSmbShare MySMBShare
      {
          Ensure      = "Present"
          Name        = "MyShare"
          Path        = "C:\Demo\Temp"
          ReadAccess  = "Bob"
          FullAccess  = "Alice"
          Description = "This is an updated description for this share"
      }
   }
}
#Run the function to compile the configuration
Sample_Share
#Pass the configuration to the nodes we defined and configure them
Start-DscConfiguration Sample_Share
```

Bu, düzgün bir şekilde biçimlendirilmiş ve okunamıyor basit betiğidir.
Hata işleme ve mantık yollarını hâlâ bulunan [kaynak](../resources/resources.md) uygulaması, ancak komut dosyası yazma için görünmez.

## <a name="separating-environment-from-structure"></a>Yapı ortamından ayırma

DevOps, yaygın bir düzen dağıtımı için birden çok ortamı sağlamaktır.
Örneğin, hızlı bir şekilde prototip yeni kod için kullanılan bir "dev" ortam olabilir.
"Dev" ortam koddan bir "test" ortamına burada diğer kişilerin yeni işlevselliğini doğrulamak gider.
Son olarak, kodu "prod" veya canlı site üretim ortamına gider.

DSC yapılandırmaları barındırmak bu geliştirme-test-prod işlem hattı kullanımının [yapılandırma verilerini](../configurations/configData.md).
Bu, daha fazla yönetilen düğümlere yapılandırmasından yapısını arasındaki farkı soyutlar.
Örneğin, bir SQL server, IIS sunucusu ve bir orta katman sunucusu gerektiren bir yapılandırmasını tanımlayabilir.
Hangi düğümleri Bu yapılandırmanın farklı parçaları Al bağımsız olarak, bu üç öğe her zaman mevcut olacak.
Üç tüm öğeler aynı makine için bir geliştirme ortamı, üç öğeleri ayrı bir test ortamı için üç farklı makinelere işaret edecek şekilde yapılandırma verilerini kullanabilirsiniz ve son olarak, tüm üretim sunucuları üretim ortamı için doğru.
Farklı ortamlara dağıtmak üzere, çağırabilirsiniz **Başlat-DscConfiguration** hedeflemek istediğiniz ortam için doğru yapılandırma verileri.

## <a name="see-also"></a>Ayrıca bkz:

[Yapılandırmalar](../configurations/configurations.md)

[Yapılandırma verileri](../configurations/configData.md)

[Kaynaklar](../resources/resources.md)
