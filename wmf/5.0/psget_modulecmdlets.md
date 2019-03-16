---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 7ad95f288e2eb7cb68341a4932500a20e7740236
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055810"
---
# <a name="powershellget-cmdlets-for-module-management"></a>Modül Yönetimi için PowerShellGet Cmdlet’leri

- [Bul-DscResource](https://technet.microsoft.com/library/mt654006.aspx)
- [Modül Bul](https://technet.microsoft.com/library/dn807167.aspx)
- [Bulma komut dosyası](https://technet.microsoft.com/library/mt654001.aspx)
- [Get-InstalledModule](https://technet.microsoft.com/library/mt653990.aspx)
- [Get-InstalledScript](https://technet.microsoft.com/library/mt653994.aspx)
- [Get-PSRepository](https://technet.microsoft.com/library/dn807170.aspx)
- [Install-Module](https://technet.microsoft.com/library/dn807162.aspx)
- [Yükleme betiği](https://technet.microsoft.com/library/mt653998.aspx)
- [Yeni ScriptFileInfo](https://technet.microsoft.com/library/mt653995.aspx)
- [Yayımlama Modülü](https://technet.microsoft.com/library/dn807163.aspx)
- [Yayımlama-komut dosyası](https://technet.microsoft.com/library/mt654003.aspx)
- [Register-PSRepository](https://technet.microsoft.com/library/dn807168.aspx)
- [Save-Module](https://technet.microsoft.com/library/mt653992.aspx)
- [Save-Script](https://technet.microsoft.com/library/mt654004.aspx)
- [Set-PSRepository](https://technet.microsoft.com/library/dn807165.aspx)
- [Test-ScriptFileInfo](https://technet.microsoft.com/library/mt654005.aspx)
- [Modül kaldırma](https://technet.microsoft.com/library/mt653996.aspx)
- [Kaldırma betiği](https://technet.microsoft.com/library/mt653989.aspx)
- [Güncelleştirme Modülü](https://technet.microsoft.com/library/dn807166.aspx)
- [Güncelleştirme ModuleManifest](https://technet.microsoft.com/library/mt654002.aspx)
- [Güncelleştirme betiği](https://technet.microsoft.com/library/mt653997.aspx)
- [Update-ScriptFileInfo](https://technet.microsoft.com/library/mt653991.aspx)
- [Kaydı-PSRepository](https://technet.microsoft.com/library/dn807161.aspx)

## <a name="module-dependency-installation-support-get-installedmodule-and-uninstall-module-cmdlets"></a>Modül bağımlılık yükleme desteği, Get-InstalledModule ve Kaldır-Module cmdlet'leri

- Modül bağımlılıkları popülasyon Publish-Module cmdlet'i eklendi. Yayımlanacak bir modül bağımlılık listesi hazırlarken PSModuleInfo RequiredModules ve NestedModules listesi kullanılır.
- Install-Module ve güncelleştirme modülü cmdlet'lerini eklenen bağımlılık yükleme desteği. Modül bağımlılıklarının yüklenir ve varsayılan olarak güncelleştirildi.
- -IncludeDependencies parametre sonuçları modülü bağımlılıkları içerecek şekilde Find-Module cmdlet'i eklendi.
- Find-Module üzerinde - MaximumVersion desteği eklendi Install-Module ve güncelleştirme modülü cmdlet'leri.
- Yeni Get-InstalledModule ve Kaldır-Module cmdlet'ler eklendi.

## <a name="powershellget-cmdlets-demo-with-module-dependencies-support"></a>Modül bağımlılıklarının ile PowerShellGet cmdlet'leri Tanıtımı destekler:

### <a name="ensure-that-module-dependencies-are-available-on-the-repository"></a>Modül bağımlılıklarının Havuzda kullanılabilir olduğundan emin olun:

```powershell
Find-Module -Repository LocalRepo -Name RequiredModule1,RequiredModule2,RequiredModule3,NestedRequiredModule1,NestedRequiredModule2,NestedRequiredModule3 | Sort-Object -Property Name

Version    Name                     Repository    Description
-------    ----                     ----------    -----------
2.5        NestedRequiredModule1    LocalRepo     NestedRequiredModule1 module
2.5        NestedRequiredModule2    LocalRepo     NestedRequiredModule2 module
2.0        NestedRequiredModule3    LocalRepo     NestedRequiredModule3 module
2.5        RequiredModule1          LocalRepo     RequiredModule1 module
2.5        RequiredModule2          LocalRepo     RequiredModule2 module
2.0        RequiredModule3          LocalRepo     RequiredModule3 module
```

### <a name="create-a-module-with-dependencies-that-are-specified-in-the-requiredmodules-and-nestedmodules-properties-of-its-module-manifest"></a>Bir modül, modül bildirimi RequiredModules ve NestedModules özelliklerinde belirtilen bağımlılıklara sahip oluşturun.

```powershell
$RequiredModules = @('RequiredModule1',
                     @{ModuleName = 'RequiredModule2'; ModuleVersion = '1.5'; },
                     @{ModuleName = 'RequiredModule3'; RequiredVersion = '2.0'; })

$NestedRequiredModules = @('TestDepWithNestedRequiredModules1.psm1', 'NestedRequiredModule1',
                            @{ModuleName = 'NestedRequiredModule2'; ModuleVersion = '1.5'; },
                            @{ModuleName = 'NestedRequiredModule3'; RequiredVersion = '2.0'; })

New-ModuleManifest -Path 'C:\Program Files\WindowsPowerShell\Modules\TestDepWithNestedRequiredModules1\TestDepWithNestedRequiredModules1.psd1' `
-NestedModules $NestedRequiredModules -RequiredModules $RequiredModules -ModuleVersion "1.0" -Description "TestDepWithNestedRequiredModules1 module"
```

### <a name="publish-two-versions-10-and-20-of-the-testdepwithnestedrequiredmodules1-module-with-dependencies-to-the-repository"></a>İki sürümü yayımlamak (**"1.0"** ve **"2.0"**) depoya bağımlılıklarla TestDepWithNestedRequiredModules1 modülü.

```powershell
Publish-Module -Name TestDepWithNestedRequiredModules1 -Repository LocalRepo -NuGetApiKey "MyNuGet-ApiKey-For-LocalRepo"
```

### <a name="find-the-testdepwithnestedrequiredmodules1-module-with-its-dependencies-by-specifying--includedependencies"></a>-IncludeDependencies belirterek TestDepWithNestedRequiredModules1 modülü ile bağımlılıkları bulun.

```powershell
Find-Module -Name TestDepWithNestedRequiredModules1 -Repository LocalRepo –IncludeDependencies -MaximumVersion "1.0"

Version    Name                                Repository  Description
-------    ----                                ----------  -----------
1.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
2.5        RequiredModule1                     LocalRepo   RequiredModule1 module
2.5        RequiredModule2                     LocalRepo   RequiredModule2 module
2.0        RequiredModule3                     LocalRepo   RequiredModule3 module
2.5        NestedRequiredModule1               LocalRepo   NestedRequiredModule1 module
2.5        NestedRequiredModule2               LocalRepo   NestedRequiredModule2 module
2.0        NestedRequiredModule3               LocalRepo   NestedRequiredModule3 module
```

### <a name="use-find-module-metadata-to-find-the-module-dependencies"></a>Modül bağımlılıklarının bulmak için bulma modülü meta verileri kullanın.

```powershell
$psgetModuleInfo = Find-Module -Repository MSPSGallery -Name ModuleWithDependencies2
$psgetModuleInfo.Dependencies.ModuleName

RequiredModule1
RequiredModule2
RequiredModule3
NestedRequiredModule1
NestedRequiredModule2
NestedRequiredModule3

$psgetModuleInfo.Dependencies

Name Value
---- -----
ModuleName RequiredModule1
CanonicalId PowerShellGet:RequiredModule1/#http://psget/psGallery/api/v2/

ModuleName RequiredModule2
ModuleVersion 2.0
CanonicalId PowerShellGet:RequiredModule2/2.0#http://psget/psGallery/api/v2/

ModuleName RequiredModule3
RequiredVersion 2.5
CanonicalId PowerShellGet:RequiredModule3/2.5#http://psget/psGallery/api/v2/

ModuleName NestedRequiredModule1
CanonicalId PowerShellGet:NestedRequiredModule1/#http://psget/psGallery/api/v2/

ModuleName NestedRequiredModule2
ModuleVersion 2.0
CanonicalId PowerShellGet:NestedRequiredModule2/2.0#http://psget/psGallery/api/v2/

ModuleName NestedRequiredModule3
RequiredVersion 2.5
CanonicalId PowerShellGet:NestedRequiredModule3/2.5#http://psget/psGallery/api/v2/
```

### <a name="install-the-testdepwithnestedrequiredmodules1-module-with-dependencies"></a>TestDepWithNestedRequiredModules1 modülü ile bağımlılıkları yükleyin.

```powershell
Install-Module -Name TestDepWithNestedRequiredModules1 -Repository LocalRepo -RequiredVersion "1.0"
Get-InstalledModule

Version    Name                    Repository   Description
-------    ----                    ----------   -----------
1.0        NestedRequiredModule1   LocalRepo    NestedRequiredModule1 module
2.5        NestedRequiredModule2   LocalRepo    NestedRequiredModule2 module
2.0        NestedRequiredModule3   LocalRepo    NestedRequiredModule3 module
1.0        RequiredModule1         LocalRepo    RequiredModule1 module
2.5        RequiredModule2                    LocalRepo    RequiredModule2 module
2.0        RequiredModule3                    LocalRepo    RequiredModule3 module
1.0        TestDepWithNestedRequiredModules1  LocalRepo    TestDepWithNestedRequiredModules1 module
```

### <a name="update-the-testdepwithnestedrequiredmodules1-module-with-dependencies"></a>TestDepWithNestedRequiredModules1 modülü bağımlılıkları ile güncelleştirin.

```powershell
Find-Module -Name TestDepWithNestedRequiredModules1 -Repository LocalRepo -AllVersions

Version    Name                                Repository  Description
-------    ----                                ----------  -----------
1.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
2.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module

Update-Module -Name TestDepWithNestedRequiredModules1 -RequiredVersion 2.0
Get-InstalledModule

Version    Name                                Repository  Description
-------    ----                                ----------  -----------
1.0        NestedRequiredModule1               LocalRepo   NestedRequiredModule1 module
2.5        NestedRequiredModule2               LocalRepo   NestedRequiredModule2 module
2.0        NestedRequiredModule3               LocalRepo   NestedRequiredModule3 module
2.5        NestedRequiredModule3               LocalRepo   NestedRequiredModule3 module
1.0        RequiredModule1                     LocalRepo   RequiredModule1 module
2.5        RequiredModule2                     LocalRepo   RequiredModule2 module
2.0        RequiredModule3                     LocalRepo   RequiredModule3 module
2.5        RequiredModule3                     LocalRepo   RequiredModule3 module
1.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
2.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
```

### <a name="run-the-uninstall-module-cmdlet-to-uninstall-a-module-that-you-installed-by-using-powershellget"></a>PowerShellGet kullanarak yüklü bir modülünü kaldırmak için Uninstall-Module cmdlet'ini çalıştırın.

PowerShellGet, başka bir modül, silmek istediğiniz modüldeki bağlıysa, bir hata oluşturur.

```powershell
Get-InstalledModule -Name RequiredModule1 | Uninstall-Module

PackageManagement\Uninstall-Package : The module 'RequiredModule1' of version '2.5' in module base folder 'C:\Program Files\WindowsPowerShell\Modules\RequiredModule1\2.5' cannot be uninstalled, because one or more other modules 'ModuleWithDependencies2' are dependent on this module. Uninstall the modules that depend on this module before uninstalling module 'RequiredModule1'.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\PSGet.psm1:1303 char:25
+ ... $null = PackageManagement\\Uninstall-Package @PSBoundParameters
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo : InvalidOperation: (Microsoft.Power...ninstallPackage:UninstallPackage) [Uninstall-Package], Exception
+ FullyQualifiedErrorId : UnableToUninstallAsOtherModulesNeedThisModule,Uninstall-Package,Microsoft.PowerShell.PackageManagement.Cmdlets.UninstallPackage
```

## <a name="save-module-cmdlet"></a>Save-Module cmdlet'i

```powershell
Save-Module -Repository MSPSGallery -Name ModuleWithDependencies2 -Path C:\MySavedModuleLocation
dir C:\MySavedModuleLocation

Directory: C:\MySavedModuleLocation

Mode LastWriteTime Length Name
---- ------------- ------ ----
d----- 4/21/2015 5:40 PM ModuleWithDependencies2
d----- 4/21/2015 5:40 PM NestedRequiredModule1
d----- 4/21/2015 5:40 PM NestedRequiredModule2
d----- 4/21/2015 5:40 PM NestedRequiredModule3
d----- 4/21/2015 5:40 PM RequiredModule1
d----- 4/21/2015 5:40 PM RequiredModule2
d----- 4/21/2015 5:40 PM RequiredModule3
```

## <a name="update-modulemanifest-cmdlet"></a>Güncelleştirme ModuleManifest cmdlet'i

Bu yeni cmdlet, güncelleştirme bildirim dosyası giriş özelliği değerlerle yardımcı olmak için kullanılır. Bu Test ModuleManifest yapan tüm parametreleri alır.

Çok fazla modül yazarları belirtmek istiyorsanız fark "\*" vb. gibi FunctionsToExport, CmdletsToExport, dışarı aktarılan değerler. PowerShell Galerisi modülü yayımlama sırasında belirtilmeyen işlevleri ve komutları düzgün galeri doldurulmaz. Bu nedenle, modül yazarları güncelleştirme kendi bildirimleri uygun değerlerle öneririz.

Özellikleri dışarı aktardığınız modülleri varsa, güncelleştirmeyi ModuleManifest belirtilen bildirim dosyası dışarı aktarılan işlevleri, cmdlet'leri, değişkenler vb. alınan bilgilerle doldurur:

```powershell
Get-Content -Path "C:\Temp\PSGTEST-TestPackageMetadata\2.5\PSGTEST-TestPackageMetadata.psd1"
@{
# Script module or binary module file associated with this manifest.
# RootModule = ''
# Version number of this module.
ModuleVersion = '2.5'
# ID used to uniquely identify this module
GUID = '610e5c5b-dc42-4eaa-8511-ebfb44066d5e'

#(Other properties removed here for Simplicity…)

# Functions to export from this module
FunctionsToExport = '*'
# Cmdlets to export from this module
CmdletsToExport = '*'
# Variables to export from this module
VariablesToExport = '*'
# Aliases to export from this module
AliasesToExport = '*'
}
```

Güncelleştirme ModuleManifest sonra:

```powershell
Update-ModuleManifest -Path "C:\Temp\PSGTEST-TestPackageMetadata\2.5\PSGTEST-TestPackageMetadata.psd1"
Get-Content -Path "C:\Temp\PSGTEST-TestPackageMetadata\2.5\PSGTEST-TestPackageMetadata.psd1"
#
# Module manifest for module 'NewManifest'
#
# Generated by: author name
#
# Generated on: 11/13/2015
#
@{
# Script module or binary module file associated with this manifest.
# RootModule = ''
# Version number of this module.
ModuleVersion = '2.5'
# ID used to uniquely identify this module
GUID = '610e5c5b-dc42-4eaa-8511-ebfb44066d5e'
# Functions to export from this module
FunctionsToExport = 'Get-FooFn Get-FooWF'
# Cmdlets to export from this module
CmdletsToExport = 'Test-PSGetTestCmdlet'
}
```

Her modül için Ayrıca ilişkili meta verileri alan vardır. Meta veri PowerShell galerisinde düzgün görüntülenmesi için güncelleştirme ModuleManifest PrivateData altında bu alanları doldurmak için kullanabilirsiniz.

```powershell
Update-ModuleManifest -Path "C:\Temp\PSGTEST-TestPackageMetadata\2.5\PSGTEST-TestPackageMetadata.psd1" -Tags "Tag1" -LicenseUri "http://license.com" -ProjectUri "http://project.com" -IconUri "http://icon.com" -ReleaseNotes "Test module"
```

Bildirim dosyası şablondan PrivateData hashtable aşağıdaki özelliklere sahiptir:

```powershell
# Private data to pass to the module specified in RootModule/ModuleToProcess. This may also contain a PSData hashtable with additional module metadata used by PowerShell.
PrivateData = @{
    PSData = @{
        # Tags applied to this module. These help with module discovery in online galleries.
        # Tags = @()

        # A URL to the license for this module.
        # LicenseUri = ''

        # A URL to the main website for this project.
        # ProjectUri = ''

        # A URL to an icon representing this module.
        # IconUri = ''

        # ReleaseNotes of this module
        # ReleaseNotes = ''

        # External dependent modules of this module
        # ExternalModuleDependencies = ''
    } # End of PSData hashtable
} # End of PrivateData hashtable
```

> [!NOTE]
> DscResourcesToExport yalnızca en son PowerShell sürüm 5.0 desteklenir. Önceki PowerShell sürümünde çalıştırıyorsanız alanın güncelleştirmek mümkün olmayacaktır.
