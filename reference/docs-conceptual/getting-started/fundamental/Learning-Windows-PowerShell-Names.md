---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: "Windows PowerShell adlarını öğrenme"
ms.assetid: b4d0fd22-8298-4ee6-82ae-9b6f2907c986
ms.openlocfilehash: 28c821c4a617b6ac775dbdda8ade3d15c3f218c3
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2017
---
# <a name="learning-windows-powershell-names"></a>Windows PowerShell adlarını öğrenme
Önemli zaman yatırım çok komut satırı arabirimi ile komutları ve komut parametreleri öğrenme adları var. Her komut ve düzenli olarak kullanmak için gereken her bir parametreyi öğrenerek öğrenmek kaldırmanın tek yolu olması için çok az desenleri olduğunu konudur.

Yeni bir komut veya parametre ile çalışırken, önceden bilmeniz genellikle kullanamazsınız; ve yeni bir ad öğrenin gerekir. Nasıl arabirimleri artımlı eklemelerle araçları küçük bir dizi işlevsellik büyümesine bakarsanız, neden yapısı standart olmayan olduğunu görmek kolaydır. Komut adlarıyla özellikle, bu yana her komutu ayrı bir araçtır, ancak komut adlarının işlemek için daha iyi bir yolu yoktur mantıksal ses.

Komutların çoğu işletim sistemi veya hizmet veya işlemler gibi uygulamaları öğelerini yönetmek için tasarlanmıştır. Komutların olabilir veya bir ailesi uygun değildir adlarını çeşitli vardır. Örneğin, Windows sistemlerinde kullanabileceğiniz **net start** ve **net stop** bir hizmeti durdurmak ve başlatmak için komutları. Windows için tamamen farklı bir ada sahip başka bir daha genelleştirilmiş hizmet denetim aracı yoktur **sc**, değil sığması için adlandırma desenine **net** hizmet komutları. İşlem yönetimi için Windows sahip **tasklist** listesi işlemlere komutunu ve **taskkill** işlemleri KILL komutu.

Parametre almaz komutları düzensiz parametre belirtimlerine sahip. Kullanamazsınız **net start** bir uzak bilgisayarda bir hizmeti başlatmak için komutu. **Sc** komutu, bir uzak bilgisayarda bir hizmet başlayacak, ancak uzak bilgisayarı belirtmek için çift ters eğik çizgi adıyla önek. Örneğin, DC01 adlı bir uzak bilgisayarda Biriktirici hizmetini başlatmak için şunu yazın **sc \\ \\DC01 Başlat biriktirici**. Listeye kullanmanıza gerek DC01 üzerinde çalışan görevler **/S** parametresi ("Sistem" için) ve kaynağı şöyle ters eğik çizgi olmadan DC01 adı: **tasklist /S DC01**.

Bir hizmet ve işlem arasındaki önemli teknik farklılıklar olsa da, bunlar öğelerinin iyi tanımlanmış bir yaşam döngüsü sahip yönetilebilir bir bilgisayarda her iki örnek verilebilir. Tüm hizmetler ve işlemlerin şu anda çalışan bir listesini alma başlatmak veya bir hizmet veya işlemi durdurmak isteyebilirsiniz. Bir hizmet ve işlem farklı işlemler olsa da, diğer bir deyişle, sizi bir hizmet veya bir işlem eylemlere genellikle kavramsal olarak aynıdır. Ayrıca, bir eylem parametrelerini belirterek özelleştirmek için yapabilir seçenekleri de kavramsal olarak benzer olabilir.

Windows PowerShell anlamak ve cmdlet'lerini kullanmak için bilmeniz gereken farklı ad sayısını azaltmak için bu benzerlikler yararlanan.

### <a name="cmdlets-use-verb-noun-names-to-reduce-command-memorization"></a>Komut anımsama zahmetinden azaltmak için fiil-isim adları cmdlet'leri kullan
Windows PowerShell, burada her cmdlet adı ile belirli bir isim kısa çizgiyle ayrılmış olarak standart bir fiil oluşan bir "fiil-isim" adlandırma sistemi kullanır. Windows PowerShell fiillerini her zaman İngilizce fiiller değildir, ancak Windows PowerShell'de belirli eylemleri express. İsimleri çok herhangi bir dilde isimleri gibi, belirli Sistem Yönetimi'nde önemli olan nesne türlerini tanımlar. Fiiller ve isimleri birkaç örnekleri bakarak bu iki parçalı adları öğrenme çaba nasıl azaltmak göstermek kolaydır.

İsimleri daha az kısıtlanmış, ancak bunlar bir komut temel aldığı her zaman açıklamalıdır. Windows PowerShell komutları gibi sahip **Get-Process**, **Stop-Process**, **Get-Service**, ve **Hizmeti Durdur**.

İki isimleri ve iki fiilleri olması durumunda tutarlılık o kadarlık öğrenme basitleştirmek değil. Ancak, standart dizi 10 fiilleri ve 10 isimleri bakarsanız, ardından anlamak için sadece 20 sözcükler sahip, ancak bu sözcükleri 100 ayrı komut adlarını oluşturmak için kullanılabilir.

Sık sık adını okuyarak komut yaptığı tanıyabilir ve genellikle görünen adı için yeni bir komut kullanılmalıdır. Örneğin, bir bilgisayar kapatma komutunu olabilir **Stop-Computer**. Ağdaki tüm bilgisayarları listeleyen bir komut olabilir **Get-bilgisayar**. Sistem tarihi alır komut **Get-Date**.

Belirli bir fiil ile dahil tüm komutları listeleyebilirsiniz **-fiil** parametresi için **Get-Command** (aşağıdakiler ele alınacaktır **Get-Command** sonraki bölümünde ayrıntılı olarak). Örneğin, fiili kullanan tüm cmdlet'leri görmek için **almak**, türü:

```
PS> Get-Command -Verb Get
CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Get-Acl                         Get-Acl [[-Path] <String[]>]...
Cmdlet          Get-Alias                       Get-Alias [[-Name] <String[]...
Cmdlet          Get-AuthenticodeSignature       Get-AuthenticodeSignature [-...
Cmdlet          Get-ChildItem                   Get-ChildItem [[-Path] <Stri...
...
```

**-İsim** parametre olduğundan daha kullanışlı, aynı nesne türünü etkileyen komutları ailesi görmenize olanak sağlar. Örneğin, görmek istiyorsanız hangi komutların türü komutu aşağıdaki hizmetleri yönetmek için kullanılabilir:

```
PS> Get-Command -Noun Service
CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Get-Service                     Get-Service [[-Name] <String...
Cmdlet          New-Service                     New-Service [-Name] <String>...
Cmdlet          Restart-Service                 Restart-Service [-Name] <Str...
Cmdlet          Resume-Service                  Resume-Service [-Name] <Stri...
Cmdlet          Set-Service                     Set-Service [-Name] <String>...
Cmdlet          Start-Service                   Start-Service [-Name] <Strin...
Cmdlet          Stop-Service                    Stop-Service [-Name] <String...
Cmdlet          Suspend-Service                 Suspend-Service [-Name] <Str... 
...
```

Yalnızca bir fiil-isim adlandırma şeması olduğundan komut bir cmdlet değil. Bir cmdlet değil ancak bir fiil-isim ada sahip yerel bir Windows PowerShell komutu örneğidir Clear-Host konsol penceresi temizlemek için komutu. Get-Command karşı çalıştırırsanız gördüğünüz Clear-Host komut gerçekte bir iç işlevi şu şekildedir:

```
PS> Get-Command -Name Clear-Host

CommandType     Name                            Definition
-----------     ----                            ----------
Function        Clear-Host                      $spaceType = [System.Managem...
```

### <a name="cmdlets-use-standard-parameters"></a>Cmdlet'leri kullanma standart parametreler
Daha önce belirtildiği gibi geleneksel komut satırı arabirimi kullanılan komutlar tutarlı parametre adları genellikle gerekmez. Bazen parametre adları hiç gerekmez. Bunu yaptıklarında, bunlar genellikle tek karakter veya hızlı bir şekilde yazılabilir, ancak yeni kullanıcılar tarafından kolayca anlaşılmayan sözcükler kısaltılır.

Çoğu diğer geleneksel komut satırı arabirimlerinden aksine Windows PowerShell parametreleri doğrudan işler ve parametre adları standartlaştırmak için bu doğrudan erişim Geliştirici Kılavuzu birlikte parametreleri için kullanır. Bu her cmdlet her zaman standartlarına uygun garanti etmez ancak bunun öneririz.

> [!NOTE]
> Parametre adları her zaman sahip bir '-' bunları açıkça bunları parametre olarak tanımlamak Windows PowerShell izin verecek şekilde kullandığınızda bunları etkileşimlidir. İçinde **Get-Command - Name Clear-Host** örnektir, parametrenin adı **adı**, ancak - olarak girilir**adı**.

Standart parametre adları ve kullanımları genel özelliklerinin bazıları aşağıda verilmiştir.

#### <a name="the-help-parameter-"></a>Yardım parametresi (?)
Belirttiğinizde **-?** herhangi bir cmdlet'i, cmdlet parametresi olarak yürütülemiyor. Bunun yerine, Windows PowerShell cmdlet'i için yardımı görüntüler.

#### <a name="common-parameters"></a>Ortak parametreleri
Windows PowerShell sahip olarak bilinen birkaç parametre *ortak parametreler*. Bir cmdlet tarafından uygulanan her Bu parametreler Windows PowerShell altyapısı tarafından kontrol edilir çünkü bunlar her zaman aynı şekilde davranır. Ortak parametreler **whatIf**, **Onayla**, **ayrıntılı**, **hata ayıklama**, **uyar**, **ErrorAction**, **ErrorVariable**, **OutVariable**, ve **OutBuffer**.

#### <a name="suggested-parameters"></a>Önerilen parametreleri
Windows PowerShell çekirdek cmdlet'lerinin benzer parametreleri için standart adlarını kullanın. Parametre adları kullanımını zorlanmaz rağmen Standartlaştırma teşvik eden kullanım için açık bir yönerge yoktur.

Örneğin, bir parametre adlar bir bilgisayar adı olarak tarafından Kılavuzu önerir **ComputerName**, sunucu, ana bilgisayar, sistem, düğüm veya ortak alternatif sözcükleri yerine. Önemli önerilen parametre arasında adlardır **zorla**, **hariç**, **INCLUDE**, **PassThru**, **yolu**, ve **CaseSensitive**.

