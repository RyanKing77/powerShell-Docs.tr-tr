---
ms.date: 08/24/2018
keywords: PowerShell cmdlet'i
title: PowerShell komut adlarını öğrenme
ms.assetid: b4d0fd22-8298-4ee6-82ae-9b6f2907c986
ms.openlocfilehash: 8d50ca03f98ed4ca8f9c09c83ae57afbf0d7888d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086434"
---
# <a name="learning-powershell-command-names"></a>PowerShell komut adlarını öğrenme

Komutlar ve parametreler adlarını öğrenme çoğu komut satırı arabirimine sahip bir önemli zaman yatırımı gerektirir. Sorun birkaç desenleri yoktur. Anımsama komutları ve düzenli olarak kullanmak için gereken parametreleri öğrenmek için tek yoludur.

Yeni bir komut veya parametresi ile çalışırken, her zaman, zaten tanıdığınız kullanamazsınız. Ve yeni bir ad öğrenin gerekir. Geleneksel olarak, komut satırı arabirimi, küçük bir araçlar kümesi ile başlayın ve artımlı eklemeleriyle büyütün. Öğrenmek kolaydır hiçbir standart yapısı olmasının.
Her komutu ayrı bir aracı olduğundan, bu komut adlarını mantıksal görünüyor. PowerShell komut adlarını başa çıkmanın daha iyi bir yolu vardır.

## <a name="learning-command-names-in-traditional-shells"></a>Geleneksel Kabuk komut adlarını öğrenme

Çoğu komutlar, işletim sistemi veya uygulama, hizmetler veya işlemleri gibi öğeleri yönetmek için oluşturulur. Komutları ailesi ile bir çözüm karşılamayabilir veya adlara sahip. Örneğin, Windows sistemlerinde kullanabilirsiniz `net start` ve `net stop` komutları bir hizmeti durdurmak ve başlatmak. **SC.exe** Windows için başka bir hizmet denetimi araçtır. Bu ada adlandırma desenini içine uymayan **net.exe** hizmet komutları. İşlem yönetimi için Windows sahip **tasklist.exe** süreçleri Listele komutu ve **taskkill.exe** işlemleri sonlandırmak için komutu.

Ayrıca, bu komutlar, düzensiz parametresi belirtimlerine sahip. Kullanamazsınız `net start` uzak bir bilgisayarda bir hizmeti başlatmak için komutu. **Sc.exe** komut, uzak bir bilgisayarda hizmet başlayabilir. Ancak, uzak bilgisayarı belirtmek için adını çift ters eğik çizgi ile önek. DC01 adlı bir uzak bilgisayarda Biriktirici hizmetini başlatmak için yazdığınız `sc.exe \\DC01 start spooler`.
Listeye DC01 üzerinde çalışan görevler, kullandığınız **/S** parametresi ve ters eğik çizgi olmadan bilgisayar adı. Örneğin, `tasklist /S DC01`.

> [!NOTE]
> PowerShell v6 önce `sc` için bir diğer ad olduğu `Set-Content` cmdlet'i. Bu nedenle, çalıştırılacak **sc.exe** komutu v6 önce bir PowerShell sürümünde tam dosya adı içermelidir **sc.exe** dosya uzantısı dahil **exe**.

Hizmetler ve işlemler iyi tanımlanmış yaşam döngülerine sahiptir yönetilebilir bir bilgisayar öğelerde örnekleridir. Başlangıç veya hizmetleri ve işlemleri durdurun veya tüm hizmetler ve işlemlerin şu anda çalışan bir listesini alın. Bunlar arasında önemli teknik farklılıklar olsa da, hizmetler ve işlemler üzerinde gerçekleştirdiğiniz eylemleri kavramsal olarak aynı değildir. Ayrıca, biz parametreleri belirterek bir eylemin özelleştirmek için yaptığınız seçimlere de kavramsal olarak benzer olabilir.

PowerShell anlamak ve cmdlet'lerini kullanmak için bilmeniz gereken farklı ad sayısını azaltmak için bu benzerlikler yararlanan.

## <a name="cmdlets-use-verb-noun-names-to-reduce-command-memorization"></a>Cmdlet'leri, komut anımsama azaltmak için fiil-isim adları kullanın.

PowerShell, bir "fiil-isim" adlandırma sistemi kullanır. Her cmdlet adı ile belirli bir isim hecelerine standart fiil oluşur. PowerShell fiillerini her zaman İngilizce fiilleri değildir, ancak bunlar belirli eylemleri PowerShell'de express. İsimleri çok herhangi bir dilde isimleri gibi. Bunlar, sistem yönetiminde önemli olan nesneler belirli türlerini açıklar. Bazı örneklere bakarak bu iki kısımlı adlar öğrenme çaba nasıl azaltmak göstermek kolay bir işlemdir.

Standart fiiller önerilen bir dizi PowerShell sahiptir. İsimleri daha az kısıtlıdır, ancak her zaman fiili temel aldığı açıklanmaktadır. PowerShell komutları gibi sahip `Get-Process`, `Stop-Process`, `Get-Service`, ve `Stop-Service`.

Bu örnekte iki isimleri ve fiilleri o kadarlık öğrenme tutarlılık basitleştirin değil. Bu liste 10 fiilleri ve 10 isimleri standartlaştırılmış bir dizi genişletin. Artık yalnızca anlamak için 20 sözcükler vardır.
Ancak, bu sözcükleri form 100 farklı komut adlarını birleştirilebilir.

Bir PowerShell komut adını okuyarak ne yaptığını anlamak kolay bir işlemdir. Bir bilgisayarı kapatmak için komut `Stop-Computer`. Ağdaki tüm bilgisayarlarda listelemek için komut `Get-Computer`. Sistem tarihini almak için komut `Get-Date`.

Belirli bir eylemiyle dahil tüm komutları listeleyerek **fiil** parametresi için `Get-Command`. Örneğin, fiili kullanan tüm cmdlet'leri görmek için `Get`, türü:

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

Kullanım **isim** aynı nesne türünü etkileyen komutlar ailesini görmek için parametre. Örneğin, aşağıdaki hizmetleri yönetmek için kullanılabilir komutları görmek için komutu çalıştırın:

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

## <a name="cmdlets-use-standard-parameters"></a>Standart parametreler cmdlet'leri kullanın

Daha önce belirtildiği gibi geleneksel komut satırı arabirimi kullanılan komutlarını her zaman tutarlı parametre adları yok. Parametreleri genellikle tek bir karakteri ya da yazmak kolaydır, ancak yeni kullanıcılar tarafından kolayca anlaşılır olmayan sözcükler olarak kısaltılır.

Çoğu geleneksel komut satırı arabirimlerinden aksine PowerShell parametreleri doğrudan işler ve parametre adları standartlaştırmak parametreleri Geliştirici Kılavuzu ile birlikte bu doğrudan erişim kullanır. Bu kılavuz teşvik eder, ancak her cmdlet standardına uygun garanti etmez.

PowerShell parametresi ayırıcı ayrıca standart hale getirir. Parametre adları her zaman sahip bir '-' için bir PowerShell komutu ile etkileşimlidir. Aşağıdaki örnek göz önünde bulundurun:

```powershell
Get-Command -Name Clear-Host
```

Parametrenin adı **adı**, ancak olarak yazılan `-Name` komut satırında bir parametre olarak kullanıldığında.

Standart parametre adları ve kullanımları genel özelliklerinin bazıları aşağıda verilmiştir.

### <a name="the-help-parameter-"></a>Yardım parametresi (?)

Belirttiğinizde `-?` parametresi üzerinde herhangi bir cmdlet'i, PowerShell cmdlet Yardımı görüntüler.
Cmdlet yürütülmedi.

### <a name="common-parameters"></a>Ortak parametreleri

PowerShell sahip birkaç *ortak parametreleri*. Bu parametreler PowerShell altyapısı tarafından denetlenir. Ortak parametreleri her zaman aynı şekilde davranır. Ortak parametreler **WhatIf**, **Onayla**, **ayrıntılı**, **hata ayıklama**, **uyar**, **ErrorAction**, **ErrorVariable**, **OutVariable**, ve **OutBuffer**.

### <a name="recommended-parameter-names"></a>Önerilen parametre adları

PowerShell core cmdlet'leri benzer parametreler için standart adları kullanın. Bu standart adlarının kullanılmasını zorunlu değildir, ancak Standardizasyon teşvik etmek için açık yönergeler.

Örneğin, bir bilgisayara başvuruda bulunan bir parametre için önerilen ad olduğu **ComputerName**, sunucu, konak, sistem, düğümü veya başka bir ortak alternatif yerine. Diğer önemli önerilen parametre adları **zorla**, **hariç**, **INCLUDE**, **PassThru**, **yolu**, ve **CaseSensitive**.
