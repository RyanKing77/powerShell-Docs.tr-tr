---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Yeni senaryolar ve WMF 5.1 Özellikleri
ms.openlocfilehash: b00069aad7422f86d1462a62a6c4bc8a91e46705
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085467"
---
# <a name="new-scenarios-and-features-in-wmf-51"></a>Yeni senaryolar ve WMF 5.1 Özellikleri

> Not: Bu bilgiler geçicidir ve değiştirilebilir.

## <a name="powershell-editions"></a>PowerShell Sürümleri

Sürüm 5.1’den başlayarak, PowerShell çeşitli özellik kümelerini ve platform uyumluluğunu belirten farklı sürümler halinde sağlanır.

- **Masaüstü sürümü:** .NET Framework üzerine inşa edilmiş ve Windows Masaüstü ve Windows Server Core gibi tam boyutlu sürümlerinde çalışan PowerShell sürümlerinin hedeflendiği betikler ve modüllerle uyumluluk sağlar.
- **Çekirdek sürümü:** .NET Core üzerine yapılandırılan ve Nano Server gibi Windows ve Windows IOT azaltılmış boyutlu sürümlerinde çalışan PowerShell sürümlerinin hedeflendiği betikler ve modüllerle uyumluluk sağlar.

**PowerShell sürümleri kullanma hakkında daha fazla bilgi edinin**

- [$PSVersionTable kullanarak PowerShell'in çalışan sürümü belirleme](/powershell/module/microsoft.powershell.core/about/about_automatic_variables)
- [Get-Module sonuçları PSEdition parametresini kullanarak CompatiblePSEditions göre filtrele](/powershell/module/microsoft.powershell.core/get-module)
- [Betik yürütme uyumlu bir PowerShell sürümünde çalıştırmadıkça engelle](/powershell/gallery/concepts/script-psedition-support)
- [Belirli PowerShell sürümleri için bir modülün uyumluluk bildirme](/powershell/gallery/concepts/module-psedition-support)

## <a name="catalog-cmdlets"></a>Katalog cmdlet'leri

İki yeni cmdlet eklendi [Microsoft.PowerShell.Security](/powershell/module/microsoft.powershell.security) modülü; bunlar oluşturmak ve Windows Katalog dosyaları doğrulayın.

### <a name="new-filecatalog"></a>Yeni FileCatalog
--------------------------------

FileCatalog yeni dosya ve klasörleri kümesi için bir Windows katalog dosyası oluşturur.
Bu katalog dosyası belirtilen yolda tüm dosyaların karmalarını içerir.
Kullanıcılar, bu klasörleri temsil eden karşılık gelen katalog dosyası ile birlikte klasör kümesi dağıtabilirsiniz.
Bu bilgiler, katalog oluşturma zamandan bu yana herhangi bir değişiklik klasörlere değişiklikler olup olmadığını doğrulamak yararlıdır.

```powershell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

1. ve 2 kataloğu sürümleri desteklenir.
Sürüm 1, dosya karmaları oluşturmak için SHA1 karma algoritmasını kullanır; sürüm 2 SHA256 kullanır.
Katalog sürümü 2 üzerinde desteklenmiyor *Windows Server 2008 R2* veya *Windows 7*.
Katalog sürümü 2 kullanması gereken *Windows 8*, *Windows Server 2012*ve sonraki işletim sistemleri.

![](../images/NewFileCatalog.jpg)

Bu, katalog dosyası oluşturur.

![](../images/CatalogFile1.jpg)

![](../images/CatalogFile2.jpg)

Katalog dosyası (yukarıdaki örnekte, Pester.cat) bütünlüğünü doğrulamak için onu kullanarak oturum [kümesi AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) cmdlet'i.

### <a name="test-filecatalog"></a>Test-FileCatalog
--------------------------------

Test-FileCatalog klasörleri kümesini temsil eden Kataloğu doğrular.

```powershell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../images/TestFileCatalog.jpg)

Bu cmdlet tüm dosyaların karma değerlerini karşılaştırır ve bunların göreli yollar bulunan *Kataloğu* bulunanlarla *disk*.
Dosya karmalarını ve yolları arasında herhangi bir uyuşmazlık algılarsa durumu olarak döndürür. *ValidationFailed*.
Kullanıcılar, tüm bu bilgileri kullanarak alabilir *-ayrıntılı* parametresi.
Ayrıca Kataloğu'nda imzalama durumu görüntüler *imza* çağırmakla eşdeğerdir özelliği [Get-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Get-AuthenticodeSignature) cmdlet'i katalog dosyası üzerinde.
Kullanıcılar ayrıca atlayabilirsiniz herhangi bir dosya doğrulama sırasında kullanarak *- FilesToSkip* parametresi.

## <a name="module-analysis-cache"></a>Modül çözümleme önbellek

WMF 5.1 ile başlayarak, PowerShell, bunu aktarır komutlar gibi bir modülle ilgili verileri önbelleğe almak için kullanılan dosya üzerinde denetim sağlar.

Varsayılan olarak, bu önbelleğin dosyasında depolanan `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.
Önbellek başlatma sırasında bir komut için aranırken genellikle okuma ve bir modülü içeri aktardıktan sonra bir arka plan iş parçacığında süre yazılır.

Önbelleğinin varsayılan konumu değiştirmek için Ayarla `$env:PSModuleAnalysisCachePath` PowerShell başlatmadan önce ortam değişkeni.
Bu ortam değişkeni yapılan değişiklikler, yalnızca alt işlemlerin etkiler.
Değeri, PowerShell oluşturun ve dosyalarını yazma iznine sahip bir tam yol (dosya adı dahil) adlandırmanız gerekir.
Dosya önbelleği devre dışı bırakmak için geçersiz bir konum için bu değeri örneğin ayarlayın:

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

Bu, geçersiz bir cihaza yolunu ayarlar.
PowerShell yolu yazılamıyor, hata döndürülür, ancak hata raporlama bir izleyici kullanarak görebilirsiniz:

```powershell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

Önbelleği dışına yazılırken, PowerShell modülleri için artık gereksiz derecede büyük bir önbellek önlemek için mevcut kontrol eder.
Bazen bu denetimler, bu durumda, bunları ayarlayarak kapatabilirsiniz, istenmez:

```powershell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

Bu ortam değişkenini ayarlayarak hemen geçerli işlemde etkili olur.

## <a name="specifying-module-version"></a>Modül sürümü belirtme

WMF 5.1 içinde `using module` PowerShell modülü ile ilgili diğer yapılarını aynı şekilde davranır.
Daha önce belirli bir modül sürümü belirtmek için imkanı yoktu; var olan birden çok sürüm varsa, bu hatayla sonuçlandı.

WMF 5.1:

- Kullanabileceğiniz [ModuleSpecification Oluşturucusu (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).
Bu karma tablosu olarak aynı biçimde `Get-Module -FullyQualifiedName`.

**Örnek:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`

- Birden çok modül sürümü varsa, PowerShell kullanan **aynı çözüm mantığı** olarak `Import-Module` ve bir hata--aynı davranışı döndürmüyor `Import-Module` ve `Import-DscResource`.

## <a name="improvements-to-pester"></a>Pester geliştirmeleri

3.4.0, ek olarak, işleme için 3.3.5 Pester PowerShell ile birlikte gelen sürümünü güncelleştirildi WMF 5.1 https://github.com/pester/Pester/pull/484/commits/3854ae8a1f215b39697ac6c2607baf42257b102e, hangi etkinleştirir daha iyi davranışı Pester Nano Sunucu'da için.

ChangeLog.md dosyasını inceleyerek 3.3.5 için 3.4.0 sürümlerindeki değişikliklere göz atabilirsiniz: https://github.com/pester/Pester/blob/master/CHANGELOG.md
