---
ms.date: 09/26/2017
contributor: keithb
keywords: Galeri, powershell, cmdlet, psget
title: Yayın öncesi modül sürümleri
ms.openlocfilehash: 2a4fcd40353450e5ba03910984c5a05772a93d0d
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189848"
---
# <a name="prerelease-module-versions"></a>Yayın öncesi modül sürümleri

1.6.0 sürümünden başlayarak, PowerShellGet ve PowerShell Galerisi sürümleri bir yayın öncesi olarak 1.0.0 büyük etiketleme için desteği. Bu özellik önce ön öğeleri 0 ile başlayan bir sürüm olması için sınırlı. Bu özellikler için daha fazla destek sağlamak için hedefidir [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) geriye doğru sürümleriyle uyumluluk PowerShell sürümleri 3 ve yukarıdaki veya varolan PowerShellGet çiğnemekten olmadan sürüm oluşturma kuralı. Bu konu modül özgü özelliklerine odaklanır. Komut dosyaları için eşdeğer özellikler bulunan [, yayın öncesi sürümler betikleri](script-prerelease-support.md) konu. Bu özellikleri kullanarak, yayımcılar bir modül veya komut dosyası sürümü 2.5.0-alpha olarak tanımlamak ve daha sonra ön sürümü yerine geçen bir üretime hazır sürüm 2.5.0 bırakın.

Yüksek düzeyde, yayın öncesi modülü özellikleri içerir:

- Bir yayın öncesi dize modül bildirimi PSData bölümüne ekleme modülü yayın öncesi sürüm olarak tanımlar. Modül PowerShell Galerisi yayımlandığında, bu veriler bildirimden ayıklanan ve yayın öncesi öğeleri tanımlamak için kullanılan.
- Yayın öncesi öğeleri alınırken gerektirir - AllowPrerelease bayrağı PowerShellGet komutları Bul-Module, Install-Module ekleme güncelleştirme modülü ve kaydetme modülü. Bayrak belirtilmezse, yayın öncesi öğeleri gösterilmez.
- Bulma modülü, Get-InstalledModule tarafından ve PowerShell Galerisi görüntülenen modül sürümleri, 2.5.0-alpha olduğu gibi eklenmemiş ön sürüm dizesi ile tek bir dize olarak görüntülenir.

Özellikler için Ayrıntılar aşağıda verilmiştir.

Bu değişiklikler, PowerShell içinde yerleşik modülü sürüm desteği etkilemez ve PowerShell 3.0 ve 4.0 5 ile uyumludur.

## <a name="identifying-a-module-version-as-a-prerelease"></a>Bir modül sürümü yayın öncesi tanımlama

Yayın öncesi sürümler için PowerShellGet destek modülü bildirim içinde iki alanı kullanımını gerektirir:

- Bir yayın öncesi sürüm kullanılıyorsa ve varolan PowerShell sürüm oluşturma uymalıdır modül bildiriminde dahil ModuleVersion 3 parçalı sürüm olmalıdır. Sürüm biçimi A, B ve C tüm tamsayılar nerede A.B.C olacaktır.
- Yayın öncesi dize modül bildiriminde PrivateData PSData bölümünde belirtilmiştir.

Aşağıda ön dizesini ayrıntılı gereksinimler verilmektedir.

Bir modül yayın öncesi tanımlayan bir modül bildirimi örnek bölümünde aşağıdaki gibi görünür:

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

Yayın öncesi dize için ayrıntılı gereksinimleri şunlardır:

- Yayın öncesi dize yalnızca ModuleVersion birincil.İkincil.derleme için 3 kesim olduğunda belirtilebilir. SemVer v1.0.0 ile hizalar.
- Yapı numarası ve ön sürüm dizesi bölücüyü tire olur. Bir tire ilk karakteri, yalnızca yayın öncesi dizesinde eklenebilir.
- Yayın öncesi dizesi yalnızca ASCII alfasayısal içerebilir [0-9A-Za - z-]. Yayın öncesi başlamak için en iyi bir uygulamadır bu öğelerin listesini taranırken ön sürümü olduğunu belirlemek daha kolay şekilde alfasayısal bir karakterle dize.
- Şu anda yalnızca SemVer v1.0.0 yayın öncesi dizeler desteklenir. Yayın öncesi dize __bulunmamalıdır__ ya da süresi içeren veya + [. +], SemVer 2. 0'verilir.
- Desteklenen yayın öncesi dizesi örnekleri:-alfasayısal, - alpha1,-BETA, - update20171020

__Yayın öncesi sürüm etkisini sırası ve yükleme klasörleri sıralama__

Sıralama için PowerShell Galerisi yayımlarken önemlidir, bir yayın öncesi sürüm kullanırken ve PowerShellGet komutları kullanarak modülleri yüklerken değiştirir. Yayın öncesi dize için iki modülleri belirtilmediği takdirde, sıralama düzeni tire aşağıdaki dize bölümü temel alır. Bu nedenle, sürüm 2.5.0-alpha 2.5.0-beta, hangi 2.5.0-gamma değerinden azdır. Aynı ModuleVersion iki modülleri varsa ve tek bir ön sürüm dizesi içeriyor, yayın öncesi dize olmadan modül üretime hazır sürüm olduğu varsayılır ve (içeren yayın öncesi sürüm öncesi sürümünü daha büyük bir sürüm olarak sıralanmış dize). Karşılaştırma bıraktığında 2.5.0 ve 2.5.0-beta, 2.5.0 örnek olarak, sürüm göz önünde bulundurulmalı iki daha büyük.

PowerShell Galerisi yayımlama sırasında varsayılan olarak PowerShell Galerisi önceden yayımlanan sürümü daha büyük bir sürüme yayımlanmakta modülü sürümü olması gerekir.

## <a name="finding-and-acquiring-prerelease-items-using-powershellget-commands"></a>Bulma ve PowerShellGet komutları kullanarak ön öğeleri alınıyor

PowerShellGet Bul-Module, Install-modülü, Update-Module, kullanarak ön öğelerle ilgili ve kaydetme modülü komutlar gerektirir - AllowPrerelease bayrağı ekleme. -AllowPrerelease belirtilirse, mevcut olup olmadığını ön öğeleri dahil edilir. -AllowPrerelease bayrak belirtilmezse, yayın öncesi öğeleri gösterilmez.

Yalnızca bu PowerShellGet modülü komutlarda Get-InstalledModule ve bazı durumlarda kaldırma modülüyle durumlardır.

- Get-InstalledModule, Modül sürümü dizesinde her zaman yayın öncesi bilgiler otomatik olarak gösterir.
- Kaldırma modül varsayılan olarak kaldırılır bir modül en son sürümünü, __hiçbir sürüm__ belirtilir. Bu davranışı değişmemiştir. Ancak, bir yayın öncesi sürüm - RequiredVersion, kullanarak belirtilmişse, - AllowPrerelease gerekli olacaktır.

## <a name="examples"></a>Örnekler

```powershell
# Assume the PowerShell Gallery has TestPackage module versions 1.8.0 and 1.9.0-alpha.
# If -AllowPrerelease is not specified, only version 1.8.0 will be returned.
C:\windows\system32> find-module TestPackage

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.8.0          TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> find-module TestPackage -AllowPrerelease

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.9.0-alpha    TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

# To install a prerelease, always specify -AllowPrerelease. Specifying a prerelease version string is not sufficient.

C:\windows\system32> Install-module TestPackage -RequiredVersion 1.9.0-alpha
PackageManagement\Find-Package : No match was found for the specified search criteria and module name 'TestPackage'.
Try Get-PSRepository to see all available registered module repositories.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.6.0\PSModule.psm1:1455 char:3
+         PackageManagement\Find-Package @PSBoundParameters | Microsoft ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ets.FindPackage:FindPackage) [Find-Package], Exceptio
   n
    + FullyQualifiedErrorId : NoMatchFoundForCriteria,Microsoft.PowerShell.PackageManagement.Cmdlets.FindPackage

# The previous command failed because -AllowPrerelease was not specified.
# Adding -AllowPrerelease will result in success.

C:\windows\system32> Install-module TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

```

Belirtilen yalnızca yayın öncesi nedeniyle farklı bir modül sürümlerini yan yana yüklenmesi desteklenmez. PowerShellGet kullanarak bir modülü yüklerken farklı aynı Modülü yüklü yan yana ModuleVersion kullanarak bir klasör adı oluşturarak sürümleridir. Yayın öncesi dize olmadan ModuleVersion klasör adı için kullanılır. Bir kullanıcı MyModule sürüm 2.5.0-alpha yüklerse, MyModule\2.5.0 klasörüne yüklenir. Kullanıcı daha sonra 2.5.0-beta yüklerse, 2.5.0-beta sürüm olacak __atlayarak yazma__ MyModule\2.5.0 klasörünün içeriğini. Bu yaklaşımın bir avantajı vardır yüklemeyi gerek sürüm öncesi sürümünü üretime hazır sürümünü yükledikten sonra olmasıdır. Aşağıdaki örnek, beklenmesi gerekenler gösterir:

``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> find-module TestPackage -AllowPrerelease

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.9.0-beta     TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> Update-Module TestPackage -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-beta      TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

```

Kaldırma modülü bir modül en son sürümünü kaldırırsanız - RequiredVersion sağlanmadı.
-RequiredVersion belirtilir ve bir yayın öncesi ise, - AllowPrerelease komutu eklenmesi gerekir.

``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
2.0.0-alpha1    TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.9.0-beta      TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta
Uninstall-Module : The '-AllowPrerelease' parameter must be specified when using the Prerelease string in
MinimumVersion, MaximumVersion, or RequiredVersion.
At line:1 char:1
+ Unnstall-Module TestPackage -RequiredVersion 1.9.0-beta
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Uninstall-Module], ArgumentException
    + FullyQualifiedErrorId : AllowPrereleaseRequiredToUsePrereleaseStringInVersion,Uninnstall-Module



C:\windows\system32> Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
2.0.0-alpha1    TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> Uninstall-Module TestPackage
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...


```

## <a name="more-details"></a>Daha fazla ayrıntı

- [Yayın öncesi betiği sürümleri](script-prerelease-support.md)
- [Bulma Modülü](/powershell/module/powershellget/find-module)
- [Yükleme Modülü](/powershell/module/powershellget/install-module)
- [Kaydet-Modülü](/powershell/module/powershellget/save-module)
- [Güncelleştirme Modülü](/powershell/module/powershellget/Update-Module)
- [Get-InstalledModule](/powershell/module/powershellget/get-installedmodule)
- [Kaldırma Modülü](/powershell/gallery/psget/module/psget_uninstall-module)