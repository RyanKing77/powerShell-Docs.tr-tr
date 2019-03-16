---
ms.date: 09/26/2017
contributor: keithb
keywords: Galeri, powershell, cmdlet, psget
title: Yayın öncesi modül sürümleri
ms.openlocfilehash: eced067dd21082de0db653daf3b838217154f1dd
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056257"
---
# <a name="prerelease-module-versions"></a>Yayın öncesi modül sürümleri

1.6.0 sürümünden itibaren PowerShellGet ve PowerShell Galerisi olarak ön sürüm 1.0.0 büyüktür sürümleri etiketleme için desteği. Bu özelliği önce yayın öncesi paketleri 0 sürümü itibarıyla bulunması sınırlıydı. Bu özellikler için daha büyük destek sağlamak için hedefidir [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) geriye dönük uyumluluğu PowerShellGet, PowerShell sürüm 3 ve yukarıdaki veya mevcut sürümlerini bozucu olmadan sürüm oluşturma kuralı. Bu konu, modül özgü özellikler üzerinde odaklanır. Betikler için eşdeğer özellikleri [, yayın öncesi sürümler betikleri](script-prerelease-support.md) konu. Bu özellikleri kullanarak yayımcılar modül veya betik sürümü 2.5.0-alpha olarak tanımlamak ve daha sonra yayım öncesi bir sürümü yerine geçen bir üretime hazır sürüm 2.5.0 bırakın.

Yüksek düzeyde, yayın öncesi modülü özellikler şunlardır:

- Modül bildirimini PSData bölümünü yayın öncesi bir dize ekleme modülü yayım öncesi bir sürümü tanımlar. Modülün PowerShell Galerisi'nde yayımlanmış olan, bu verileri bildiriminden ayıklanır ve yayın öncesi paketleri tanımlamak için kullanılır.
- Yayın öncesi paketleri alınıyor gerektirir ekleme `-AllowPrerelease` PowerShellGet komutlarını bayrak `Find-Module`, `Install-Module`, `Update-Module`, ve `Save-Module`. Bayrak belirtilmezse, yayın öncesi paketleri gösterilmez.
- Modül sürümlerini tarafından görüntülenen `Find-Module`, `Get-InstalledModule`ve PowerShell galerisinde, olduğu gibi 2.5.0-alpha eklenen ön sürüm dizesi ile tek bir dize olarak görüntülenir.

Özellikler için ayrıntıları aşağıda verilmiştir.

Bu değişiklikler, PowerShell içinde yerleşik modülü sürüm desteği etkilemez ve PowerShell 3.0 ve 4.0 5 ile uyumludur.

## <a name="identifying-a-module-version-as-a-prerelease"></a>Bir modül sürümü bir yayın öncesi tanımlama

Yayın öncesi sürümleri için destek PowerShellGet modülü bildirimi içinde iki alan gerektirir:

- Yayın öncesi bir sürüm kullanılıyorsa ve mevcut PowerShell sürüm oluşturma ile uyumlu olmalıdır modül bildiriminde bulunan ModuleVersion 3 parçalı bir sürüm olmalıdır. Sürüm biçimi A.B.C, A, B ve C tüm tamsayıların nerede olacaktır.
- Modül bildirimindeki PrivateData PSData bölümünde ön sürüm dizesi belirtildi.

Ön sürüm dizesini ayrıntılı gereksinimler aşağıda verilmiştir.

Bir modül ön tanımlayan bir modül bildirimi bir örnek bölümünde aşağıdaki gibi görünür:

```powershell
@{
    ModuleVersion = '2.5.0'
    #---
    PrivateData = @{
        PSData = @{
            Prerelease = 'alpha'
        }
    }
}
```

Ön sürüm dizesi için ayrıntılı gereksinimler şunlardır:

- Yayın öncesi dize yalnızca ModuleVersion için birincil.İkincil.derleme 3 Kesimden olduğunda belirtilebilir. Bu, SemVer v1.0.0 ile hizalar.
- Derleme numarası ve ön sürüm dizesi bölücüyü tire olur. Bir tire ön dizedeki ilk karakter yalnızca eklenebilir.
- Yayın öncesi dize yalnızca ASCII alfasayısal karakterler içerebilir. [0-9A-Za - z-]. Ön sürümün süresi başlatmak için en iyi bir yöntemdir bu paketlerin listesini taranırken yayım öncesi bir sürümü olduğunu belirlemek daha kolay olacak şekilde bir alfa karakter dize.
- Şu anda yalnızca SemVer v1.0.0 ön sürüm dizeleri desteklenir. Yayın öncesi dize **gerekir** döneme içeren veya + [. +], SemVer 2. 0'verilir.
- Desteklenen bir ön sürüm dizesi örnekleri şunlardır:-alfa, - alpha1,-BETA, - update20171020

### <a name="prerelease-versioning-impact-on-sort-order-and-installation-folders"></a>Yayın öncesi sürüm oluşturma sırası ve yükleme klasörleri sıralama etkisi

Sıralama düzeni için PowerShell Galerisi yayımlama sırasında büyük/küçük harf önemlidir, bir ön sürümünü kullanırken ve modülleri PowerShellGet komutlarını kullanarak yüklerken değiştirir. Sıralama düzenini, yayın öncesi dize için iki modül belirtilirse, kısa çizgi aşağıdaki dize bölümü temel temel alır. Bu nedenle, sürüm 2.5.0-alpha 2.5.0-beta, 2.5.0-gamma değerinden küçük olan küçüktür. Modülü ön sürüm dizesi olmadan aynı ModuleVersion iki modül sahip ve tek bir ön sürüm dizesi varsa, üretime hazır sürüm olduğu varsayılır ve (içeren yayın öncesi sürüm öncesi sürümünü sürümünden daha yüksek bir sürüm olarak sıralanır dize). Karşılaştırma bıraktığında 2.5.0 ve 2.5.0-beta, 2.5.0 örnek olarak sürüm değerlendirilir iki büyük.

PowerShell Galerisi'nde yayımlama sırasında varsayılan olarak PowerShell Galerisi'nde olan önceden yayımlanan sürümü daha büyük bir sürümse yayımlanmakta modülü sürümüne sahip olmanız gerekir.

## <a name="finding-and-acquiring-prerelease-packages-using-powershellget-commands"></a>Bulma ve PowerShellGet komutlarını kullanarak yayın öncesi paketleri alınıyor

PowerShellGet bulma modülü, Install-Module güncelleştirme-Module kullanarak yayın öncesi paketleri ile ilgilenen ve Save-Module komutları gerektirir - AllowPrerelease bayrağı ekleme. -AllowPrerelease belirtilmediği takdirde, mevcut değilse yayın öncesi paketleri dahil edilir. -AllowPrerelease bayrak belirtilmezse, yayın öncesi paketleri gösterilmez.

Yalnızca bu PowerShellGet modülü komutlarda Get-InstalledModule ve bazı durumlarda kaldırma modülü ile özel durumlardır.

- Get-InstalledModule, modüller için sürüm dizesindeki her zaman yayın öncesi bilgiler otomatik olarak gösterilir.
- Kaldırma-Module varsayılan olarak kaldırılır bir modülün en son sürüm ise __sürüm__ belirtilir. Bu davranış değişmemiştir. Ancak, bir ön sürümünü kullanarak - RequiredVersion, belirtilirse - AllowPrerelease gerekli olacaktır.

## <a name="examples"></a>Örnekler

PowerShell Galerisi TestPackage modül sürümlerini 1.8.0 ve 1.9.0-alpha sahip olduğunu varsayın. Varsa `-AllowPrerelease` olan belirtilmezse, yalnızca sürüm 1.8.0 döndürülür.

```powershell
find-module TestPackage
```

```output
Version        Name           Repository  Description
-------        ----           ----------  -----------
1.8.0          TestPackage    PSGallery   Package used to validate changes to the PowerShe...
```

```powershell
find-module TestPackage -AllowPrerelease
```

```output
Version        Name           Repository  Description
-------        ----           ----------  -----------
1.9.0-alpha    TestPackage    PSGallery   Package used to validate changes to the PowerShe...
```

Bir ön sürümü yüklemek için her zaman - AllowPrerelease belirtin. Yayın öncesi sürüm dizesi belirtilmesi yeterli değildir.

```powershell
Install-module TestPackage -RequiredVersion 1.9.0-alpha
```

```output
PackageManagement\Find-Package : No match was found for the specified search criteria and module name 'TestPackage'.
Try Get-PSRepository to see all available registered module repositories.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.6.0\PSModule.psm1:1455 char:3
+         PackageManagement\Find-Package @PSBoundParameters | Microsoft ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ets.FindPackage:FindPackage) [Find-Package], Exception
    + FullyQualifiedErrorId : NoMatchFoundForCriteria,Microsoft.PowerShell.PackageManagement.Cmdlets.FindPackage
```

-AllowPrerelease belirtilmediğinden önceki komut başarısız oldu. Ekleme `-AllowPrerelease` başarılı şekilde neden olur.

```powershell
Install-module TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
Get-InstalledModule TestPackage
```

```output
Version         Name          Repository  Description
-------         ----          ----------  -----------
1.9.0-alpha     TestPackage   PSGallery   Package used to validate changes to the PowerShe...
```

Yalnızca ön sürümün süresi belirtilen nedeniyle farklı bir modül sürümlerini yan yana yüklenmesi desteklenmez. PowerShellGet kullanarak bir modülü yüklerken farklı aynı Modülü yüklü yan yana ModuleVersion kullanarak bir klasör adı oluşturarak sürümleridir. Ön sürüm dizesi olmadan ModuleVersion klasör adı olarak kullanılır. Bir kullanıcı MyModule sürüm 2.5.0-alpha yüklerse, bu şekilde yüklenecek `MyModule\2.5.0` klasör. Kullanıcı ardından 2.5.0-beta yüklerse, 2.5.0-beta sürümü olacak **üzerine** klasörünün içeriğini `MyModule\2.5.0`. Bu yaklaşımın bir avantajı, yüklemeyi gerek yayım öncesi bir sürümü üretime hazır sürümünü yükledikten sonra olmasıdır. Aşağıdaki örnekte beklenmesi gerekenler gösterilmektedir:

``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name           Repository  Description
-------         ----           ----------  -----------
1.9.0-alpha     TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.8.0           TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage    PSGallery   Package used to validate changes to the PowerShe...

C:\windows\system32> find-module TestPackage -AllowPrerelease

Version        Name            Repository  Description
-------        ----            ----------  -----------
1.9.0-beta     TestPackage     PSGallery   Package used to validate changes to the PowerShe...

C:\windows\system32> Update-Module TestPackage -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name           Repository  Description
-------         ----           ----------  -----------
1.9.0-beta      TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.8.0           TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage    PSGallery   Package used to validate changes to the PowerShe...

```

Kaldırma modülü bir modülün en son sürümünü kaldırırsanız - RequiredVersion sağlanmadı.
Belirtilen ve ön sürüm - RequiredVersion, - AllowPrerelease komutu eklenmesi gerekir.

``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name           Repository  Description
-------         ----           ----------  -----------
2.0.0-alpha1    TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.9.0-beta      TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.8.0           TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage    PSGallery   Package used to validate changes to the PowerShe...

C:\windows\system32> Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta

Uninstall-Module : The '-AllowPrerelease' parameter must be specified when using the Prerelease string in
MinimumVersion, MaximumVersion, or RequiredVersion.
At line:1 char:1
+ Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Uninstall-Module], ArgumentException
    + FullyQualifiedErrorId : AllowPrereleaseRequiredToUsePrereleaseStringInVersion,Uninstall-Module

C:\windows\system32> Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name          Repository   Description
-------         ----          ----------   -----------
2.0.0-alpha1    TestPackage   PSGallery    Package used to validate changes to the PowerShe...
1.8.0           TestPackage   PSGallery    Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage   PSGallery    Package used to validate changes to the PowerShe...

C:\windows\system32> Uninstall-Module TestPackage
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name          Repository   Description
-------         ----          ----------   -----------
1.8.0           TestPackage   PSGallery    Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage   PSGallery    Package used to validate changes to the PowerShe...
```

## <a name="more-details"></a>Daha fazla ayrıntı

- [Yayın öncesi betik sürümleri](script-prerelease-support.md)
- [Modül Bul](/powershell/module/powershellget/find-module)
- [Install-Module](/powershell/module/powershellget/install-module)
- [Save-Module](/powershell/module/powershellget/save-module)
- [Güncelleştirme Modülü](/powershell/module/powershellget/Update-Module)
- [Get-InstalledModule](/powershell/module/powershellget/get-installedmodule)
- [Modül kaldırma](/powershell/module/powershellget/uninstall-module)
