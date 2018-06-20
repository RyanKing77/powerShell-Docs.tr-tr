---
ms.date: 10/13/2017
keywords: DSC, powershell, yapılandırma, Kur
title: Karar Verenler için İstenen Durum Yapılandırmasına Genel Bakış
ms.openlocfilehash: f8a851c5fbc5165ebe9642c5cd60964f1584efab
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189899"
---
# <a name="desired-state-configuration-overview-for-engineers"></a>Mühendisler için İstenen Durum Yapılandırmasına Genel Bakış

Bu belge, PowerShell istenen durum yapılandırması (DSC) avantajlarını öğrenmeniz Geliştirici ve işlemleri ekipleri için tasarlanmıştır.
DSC değeri yüksek düzey bir görünümünü sağlar için lütfen bkz [istenen durum yapılandırması için genel bakış karar alıcılar](decisionMaker.md)

## <a name="benefits-of-desired-state-configuration"></a>İstenen durum yapılandırması yararları

DSC var için:

- Windows komut dosyası karmaşıklığını azaltmak
- Yineleme hızını artırmak

"Sürekli dağıtımı" kavramı daha önemli hale gelmektedir.
Sürekli dağıtım sık, potansiyel olarak birçok kez günde dağıtma yeteneği anlamına gelir.
Bu dağıtımlar amacı olan bir şey düzeltme değil ancak hızlı bir şekilde yayımlanan bir şey almak için.
Yeni özellikler işlemde geliştirme aracılığıyla sorunsuz ve mümkün olduğunca güvenilir bir şekilde alarak, saat değerini yeni iş mantığı azaltın.

Burada bir bitiş durumu ortam metin olarak bildirilen ve dağıtım altyapısına yayımlanan bir "bildirim temelli" şablonu modeli kullanan bir dağıtım çözümü gelir bulut doğru taşıyın.
Herhangi bir zamanda dağıtım son durum güvence altına almak için tutarlı bir şekilde yinelenebilir olduğundan bu dağıtım yöntemi, ölçekte hızlı değişiklik hatanın tehdide karşı esnekliği ile sağlar.
Araçlar ve işlem Otomasyonu boyunca bu stili destekleyen hizmetlerin oluşturulmasını bu değişikliklere yanıt olan.

DSC bir bildirim temelli sağlar platform ve ıdempotent (yinelenebilir) dağıtımı, yapılandırma ve uyumluluk içindir.
DSC platformu, veri merkezinizdeki bileşenlerinin hatalarını önler ve pahalı dağıtım hatalarını önler doğru yapılandırmasına sahip olmanızı sağlar.
DSC yapılandırmaları uygulama kodunun bir parçası olarak kabul ederek, DSC sürekli dağıtımı sağlar.
DSC yapılandırması uygulamayı dağıtmak için gereken bilgi her zaman güncel ve kullanılacak hazır olduğundan emin olmanın uygulama, bir parçası olarak güncelleştirilmesi gerekir.

## <a name="i-have-powershell-why-do-i-need-desired-state-configuration"></a>"I PowerShell istenen durum yapılandırması neden ihtiyacım var?"

DSC yapılandırmaları ayrı amacını veya "ne yapmak istiyorum", yürütme veya "nasıl yapılacağını istiyorum."
Bu, yürütme mantığını içindeki kaynaklara içerdiği anlamına gelir.
Kullanıcıların nasıl uygulanacağını veya bu özellik için bir DSC kaynağı kullanılabilir olduğunda bir özellik dağıtmak bilmeniz gerekmez.
Bu, kullanıcının kendi dağıtım yapısı üzerinde odaklanmanıza olanak sağlar.

Örnek olarak, PowerShell komut aşağıdaki gibi görünmelidir:
```powershell
# Create a share in Windows Server 8
New-SmbShare -Name MyShare -Path C:\Demo\Temp -FullAccess Alice -ReadAccess Bob
```
Bu komut, basit, anlaşılabilir ve kolay dosyasıdır.
Bununla birlikte, bu komut dosyası üretime geçirmeden çalışırsanız, çeşitli sorunlar çalışır.
Ne betik arka arkaya iki kez çalışan olur?
Bob paylaşıma tam erişimi daha önce varsa ne olur?

Bu sorunlar için dengelemek için komut dosyası "gerçek" sürümü gibi bir daha yakın görünür:
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

Bu komut, daha karmaşık, Eskinin mantık ve hata işleme ile dosyasıdır.
Yanıtlar, istediğiniz artık belirten olduğundan komut dosyası daha karmaşıktır, ancak *nasıl yapılacağını*.

Temel mantığını hemen soyutlanır ve DSC yapılmasını istediğinizi düşünelim sağlar.

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
          ReadAccess  = "Alice"
          FullAccess  = "Bob"
          Description = "This is an updated description for this share"
      }
   }
}
#Run the function to compile the configuration
Sample_Share
#Pass the configuration to the nodes we defined and configure them
Start-DscConfiguration Sample_Share
```

Bu komut, düzgün bir şekilde biçimlendirilmiş ve okumak basit dosyasıdır.
Hata işleme ve mantık yollarını içinde hala mevcut [kaynak](resources.md) uygulama ancak betik Yazar görünmez.

## <a name="separating-environment-from-structure"></a>Yapı ortamından ayırma

DevOps ortak desende dağıtımı için birden çok ortamları olmalıdır.
Örneğin, hızlı bir şekilde prototip yeni kod kullanılan "geliştirme" ortam olabilir.
"Geliştirme" ortamından kod burada diğer kişilerin yeni işlevselliği doğrulayın "test" ortamına gider.
Son olarak, kod "prod" ya da Canlı site üretim ortamına gider.

DSC yapılandırmaları uyum bu geliştirme test üretim ardışık düzen kullanılarak [yapılandırma verilerini](configData.md).
Bu, daha fazla yönetilen düğümler yapılandırmasından yapısını arasındaki farkı soyutlar.
Örneğin, bir SQL server, IIS sunucusu ve bir orta katman server gerektiren bir yapılandırma tanımlayabilirsiniz.
Bu yapılandırma farklı parçalarının hangi düğümleri Al bağımsız olarak, bu üç öğe her zaman mevcut olacaktır.
Üç tüm öğeleri aynı makine üç öğeleri ayrı bir test ortamı için üç farklı makinelere geliştirme ortamınız için doğru işaret edecek şekilde yapılandırma verilerini kullanabilirsiniz ve son olarak üretim ortamı için tüm üretim sunucularında doğru.
Farklı ortamlar için dağıtmak için çağırabilirsiniz **başlangıç DscConfiguration** hedeflemek istediğiniz ortam için doğru yapılandırma verileri.

## <a name="see-also"></a>Ayrıca bkz:

[Yapılandırmalar](configurations.md)

[Yapılandırma verileri](configData.md)

[Kaynaklar](resources.md)