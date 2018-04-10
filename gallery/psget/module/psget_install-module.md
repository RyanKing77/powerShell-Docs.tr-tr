---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: Galeri, powershell, cmdlet, psget
title: Yükleme Modülü
ms.openlocfilehash: 960e3a85a0f915dd9da00f6456550a335c619cea
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="install-module"></a>Yükleme Modülü

PowerShell modülleri çevrimiçi havuzların yerel bilgisayara yükler.

## <a name="description"></a>Açıklama

Yükleme modül cmdlet bir çevrimiçi galeriden bir veya daha fazla modül indirir, doğrular ve bunları belirtilen yükleme kapsamı yerel bilgisayara yükler.

Yükleme modül cmdlet bir çevrimiçi galeriden belirtilen ölçütleri karşılayan bir veya daha fazla modül alır, arama sonuçları geçerli modülleri ve yükleme konumuna modülü kopyalarına olduğunu doğrular.

Kapsam tanımlandığında veya kapsam parametresinin değeri AllUsers olduğunda modülü %systemdrive%:\Program Files\WindowsPowerShell\Modules yüklenir. Currentuser'a kapsam değeri modülü $home\Documents\WindowsPowerShell\Modules yüklenir.

Minimum ve tam belirtilen modülleri sürümlerine göre sonuçlarınızı filtreleyebilirsiniz.

- Windows PowerShell 5.0 veya daha yeni yan yana sürüm desteği
- Modül bağımlılık yükleme desteği
- **Komut isteminde güvenilmeyen:**kullanıcı kabul güvenilmeyen bir depodan modülleri yüklemek için gereklidir.
- -Force yüklü modül yeniden yükler
- RequiredVersion, PowerShell sürüm 5.0 veya daha yeni olan sürümleriyle SxS içinde belirtilen sürümü yükler.

### <a name="scope"></a>Kapsam
Modül yükleme kapsamını belirtir. Bu parametre için kabul edilebilir değerler: AllUsers ve Currentuser'a.

Varsayılan yükleme AllUsers kapsamıdır.

Diğer bir deyişle, bilgisayarın tüm kullanıcıları için erişilebilen bir konumda yüklü modülleri AllUsers kapsam sağlar "$env: SystemDrive\Program Files\WindowsPowerShell\Modules".

Modül yalnızca geçerli kullanıcı için kullanılabilir olmasını sağlamak Currentuser'a kapsam yalnızca "$home\Documents\WindowsPowerShell\Modules için", yüklü modülleri olanak sağlar.

## <a name="notes"></a>Notlar

Bu cmdlet, Windows PowerShell 3.0 veya sonraki sürümleri Windows PowerShell, Windows 7 veya Windows 2008 R2 ve Windows'un sonraki sürümleri üzerinde çalışır.

(Diğer bir deyişle, bir .psm1, .psd1 veya .dll dosyasının aynı ada sahip klasör içinde yoksa) yüklü bir modül içeri aktarılamıyor Force parametresini komutunuza eklemedikçe yükleme başarısız olur.

Bir bilgisayarda modül adı parametresi için belirtilen değer eşleştiğinden ve MinimumVersion veya RequiredVersion parametresini eklemediniz yükle-Module sessizce bu modül yüklemeden devam eder. MinimumVersion veya RequiredVersion parametreler belirtildi ve var olan bir modül, bu parametre değerleri eşleşmiyor, bir hata oluşur. Daha belirgin olması: şu anda yüklü modülü sürümü MinimumVersion parametresinin değerini daha düşük veya RequiredVersion parametre değerine eşit değil ise, bir hata oluşur. Yüklü Modül sürümü MinimumVersion parametresinin değerinden büyük veya eşit RequiredVersion parametresinin değeri ise, bu modül yüklemeden yükle-Module sessizce sürdürür.

Hiçbir modül belirtilen adla eşleşen çevrimiçi galeriden varsa Install-Module bir hata döndürür.

Birden çok modüllerini yüklemek için bir dizi virgülle ayırarak modül adını belirtin. Birden çok modül adlarını belirtirseniz, MinimumVersion veya RequiredVersion ekleyemezsiniz.

Varsayılan olarak, modüller Windows PowerShell istenen durum yapılandırması (DSC) kaynakları yüklerken Karışıklığı önlemek için Program Files klasörüne yüklenir. Install-Module PSGetItemInfo nesnelere iletebildiğiniz; Bu tek bir komutta yüklemek için birden fazla modülü belirtmenin başka bir yoludur.

Yüklenen kötü amaçlı kod içeren çalışan modülleri önlemeye yardımcı olmak için modülleri yüklemesi tarafından otomatik olarak alınmaz. Güvenlik açısından en iyisi, herhangi bir cmdlet veya işlevleri, bir modüle ilk defa çalıştırmadan önce modülü kod değerlendirin.


## <a name="cmdlet-syntax"></a>Cmdlet sözdizimi
```powershell
Get-Command -Name Install-Module -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a>Cmdlet çevrimiçi Yardım başvurusu

[Yükleme Modülü](http://go.microsoft.com/fwlink/?LinkID=398573)

## <a name="example-commands"></a>Örnek komutlar

```powershell

# Install a module by name
Install-Module -Name MyDscModule

# Install multiple modules
Install-Module ContosoClient,ContosoServer

# Install a module using its minimum version
Install-Module -Name ContosoServer -MinimumVersion 1.0

# Install a specific version of a module
Install-Module -Name ContosoServer -RequiredVersion 1.1.3

# Install a specific prerelease version of a module
Install-Module -Name ContosoServer -RequiredVersion 1.1.3-alpha -AllowPrerelease

# Install the latest version of a module by name, including prelrelease versions if one exists
Install-Module -Name ContosoServer -AllowPrerelease

# Install the latest version of a module to $home\Documents\WindowsPowerShell\Modules.
Install-Module -Name ContosoServer -Scope CurrentUser

# if a module is already available under $env:PSModulePath, below command fails with 'ModuleAlreadyInstalled,Install-Package,Microsoft.PowerShell.PackageManagement.Cmdlets.InstallPackage'
Install-Module ContosoServer -RequiredVersion 1.5

# if a module is already available under $env:PSModulePath, below command fails with 'ModuleAlreadyInstalled,Install-Package,Microsoft.PowerShell.PackageManagement.Cmdlets.InstallPackage'
Install-Module ContosoServer -MinimumVersion 2.5

# Install multiple modules from multiple registered repositories
Install-Module ContosoClient,ContosoServer -Repository PSGallery, PrivatePSGallery

# Install a module with -WhatIf
Install-Module ContosoClient -WhatIf

# Install a module with -Confirm. A prompt will be displayed to confirm the installation.
Install-Module ContosoClient -WhatIf

# -Force option reinstalls the installed module
Install-Module ContosoClient -Force

# Install a module with dependencies
Install-Module -Name
```

## <a name="install-module-cmdlet-in-pipeline-operations"></a>Ardışık Düzen işlemlerinde yükleme modül cmdlet

```powershell

# Find a module and install it
Find-Module -Name "MyDSC*" | Install-Module

# Find a module and install it to the CurrentUser scope
Find-Module -Name "MyDSC*" | Install-Module -Scope CurrentUser

# Find commands by name and install them
# The first command finds the specified commands in the INT repository, and then uses the pipeline operator to pass them to Install-Module to install them.
# The second command uses Get-InstalledModule to verify the modules from the prior command are installed.
Find-Command -Repository "INT" -Name Get-ContosoClient,Get-ContosoServer | Install-Module
Get-InstalledModule

# This command finds the resource named MyResource and passes it to the Install-Module cmdlet by using the pipeline operator. The Install-Module cmdlet installs the module for the resource.
# If you pipe multiple resources to the Install-Module cmdlet from the same module, Install-Module attempts to install the module only once.
Find-DscResource -Name "MyResource" | Install-Module
Get-InstalledModule

# Find multiple role capabilities and install them
Find-RoleCapability -Name MyJeaRole, Maintenance | Install-Module
Get-InstalledModule

```

## <a name="side-by-side-version-support-on-powershell-50-or-newer"></a>Yan yana sürüm desteği PowerShell 5.0 veya daha yeni

Install-modülünde PowerShellGet destekleyen yan yana (SxS) modülü sürüm desteği güncelleştirme modülü ve Windows PowerShell 5.0 veya daha yeni çalışması Yayımla-Module cmdlet'leri.

### <a name="install-module-examples"></a>Install-Module örnekleri

```powershell
# Install a version of the module
Install-Module -Name PSScriptAnalyzer -RequiredVersion 1.1.0 -Repository PSGallery
Get-Module -ListAvailable -Name PSScriptAnalyzer | Format-List Name,Version,ModuleBase

Name : PSScriptAnalyzer
Version : 1.1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.0

# Install another version of the module in Side-by-Side with already installed version.
Install-Module -Name PSScriptAnalyzer -RequiredVersion 1.1.1 -Repository PSGallery
Get-Module -ListAvailable -Name PSScriptAnalyzer | Format-List Name,Version,ModuleBase

Name       : PSScriptAnalyzer
Version    : 1.1.1
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.1
Name       : PSScriptAnalyzer
Version    : 1.1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.0

# Get all versions of an installed module
Get-InstalledModule -Name PSScriptAnalyzer -AllVersions
Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.1.0      PSScriptAnalyzer                    PSGallery            PSScriptAnalyzer provides script analysis...
1.1.1      PSScriptAnalyzer                    PSGallery            PSScriptAnalyzer provides script analysis...


```

## <a name="install-module-with-its-dependencies"></a>Bağımlılıkları ile modülünü yükleme

```powershell

# Find a module
Find-Module -Name TypePx -Repository PSGallery

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
2.0.1.20   TypePx                              PSGallery            The TypePx module adds properties and methods to the m...

# Find a module and its dependencies
Find-Module -Name TypePx -Repository PSGallery -IncludeDependencies

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
2.0.1.20   TypePx                              PSGallery            The TypePx module adds properties and methods to the m...
1.0.5.18   SnippetPx                           PSGallery            The SnippetPx module enhances the snippet experience i...

# Discover the dependencies list without adding -IncludeDependencies
$result = Find-Module -Name TypePx -Repository PSGallery
$result.Dependencies

Name                           Value
----                           -----
Name                           SnippetPx
CanonicalId                    powershellget:SnippetPx/#https://www.powershellgallery.com/api/v2/


# Now install the module along with its dependencies
Install-Module -Name TypePx -Repository PSGallery -Verbose

VERBOSE: Repository details, Name = 'PSGallery', Location = 'https://www.powershellgallery.com/api/v2/'; IsTrusted =
'False'; IsRegistered = 'True'.
VERBOSE: Using the provider 'PowerShellGet' for searching packages.
VERBOSE: Using the specified source names : 'PSGallery'.
VERBOSE: Getting the provider object for the PackageManagement Provider 'NuGet'.
VERBOSE: The specified Location is 'https://www.powershellgallery.com/api/v2/' and PackageManagementProvider is
'NuGet'.
VERBOSE: Searching repository 'https://www.powershellgallery.com/api/v2/FindPackagesById()?id='TypePx'' for ''.
VERBOSE: Total package yield:'1' for the specified package 'TypePx'.
VERBOSE: Performing the operation "Install-Module" on target "Version '2.0.1.20' of module 'TypePx'".

Untrusted repository
You are installing the modules from an untrusted repository. If you trust this repository, change its
InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the modules from
'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"): Y
VERBOSE: The installation scope is specified to be 'AllUsers'.
VERBOSE: The specified module will be installed in 'C:\Program Files\WindowsPowerShell\Modules'.
VERBOSE: The specified Location is 'NuGet' and PackageManagementProvider is 'NuGet'.
VERBOSE: Downloading module 'TypePx' with version '2.0.1.20' from the repository
'https://www.powershellgallery.com/api/v2/'.
VERBOSE: Searching repository 'https://www.powershellgallery.com/api/v2/FindPackagesById()?id='TypePx'' for ''.
VERBOSE: Searching repository 'https://www.powershellgallery.com/api/v2/FindPackagesById()?id='SnippetPx'' for ''.
VERBOSE: InstallPackage' - name='SnippetPx',
version='1.0.5.18',destination='C:\Users\manikb\AppData\Local\Temp\1027042896'
VERBOSE: DownloadPackage' - name='SnippetPx',
version='1.0.5.18',destination='C:\Users\manikb\AppData\Local\Temp\1027042896\SnippetPx\SnippetPx.nupkg',
uri='https://www.powershellgallery.com/api/v2/package/SnippetPx/1.0.5.18'
VERBOSE: Downloading 'https://www.powershellgallery.com/api/v2/package/SnippetPx/1.0.5.18'.
VERBOSE: Completed downloading 'https://www.powershellgallery.com/api/v2/package/SnippetPx/1.0.5.18'.
VERBOSE: Completed downloading 'SnippetPx'.
VERBOSE: Hash for package 'SnippetPx' does not match hash provided from the server.
VERBOSE: InstallPackageLocal' - name='SnippetPx',
version='1.0.5.18',destination='C:\Users\manikb\AppData\Local\Temp\1027042896'
VERBOSE: InstallPackage' - name='TypePx',
version='2.0.1.20',destination='C:\Users\manikb\AppData\Local\Temp\1027042896'
VERBOSE: DownloadPackage' - name='TypePx',
version='2.0.1.20',destination='C:\Users\manikb\AppData\Local\Temp\1027042896\TypePx\TypePx.nupkg',
uri='https://www.powershellgallery.com/api/v2/package/TypePx/2.0.1.20'
VERBOSE: Downloading 'https://www.powershellgallery.com/api/v2/package/TypePx/2.0.1.20'.
VERBOSE: Completed downloading 'https://www.powershellgallery.com/api/v2/package/TypePx/2.0.1.20'.
VERBOSE: Completed downloading 'TypePx'.
VERBOSE: Hash for package 'TypePx' does not match hash provided from the server.
VERBOSE: InstallPackageLocal' - name='TypePx',
version='2.0.1.20',destination='C:\Users\manikb\AppData\Local\Temp\1027042896'
VERBOSE: Installing the dependency module 'SnippetPx' with version '1.0.5.18' for the module 'TypePx'.
VERBOSE: Module 'SnippetPx' was installed successfully to path 'C:\Program
Files\WindowsPowerShell\Modules\SnippetPx\1.0.5.18'.
VERBOSE: Module 'TypePx' was installed successfully to path 'C:\Program
Files\WindowsPowerShell\Modules\TypePx\2.0.1.20'.


# Get the installed modules
Get-InstalledModule

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.0.5.18   SnippetPx                           PSGallery            The SnippetPx module enhances the snippet experience i...
2.0.1.20   TypePx                              PSGallery            The TypePx module adds properties and methods to the m...

```

## <a name="error-scenarios"></a>Hata senaryoları

```powershell

# Below command fails with 'NameShouldNotContainWildcardCharacters,Install-Module'
Install-Module ContosoServe*

# Below command fails with 'VersionRangeAndRequiredVersionCannotBeSpecifiedTogether,Install-Module'
Install-Module ContosoServer -MinimumVersion 1.0 -RequiredVersion 5.0

# Below command fails with 'VersionParametersAreAllowedOnlyWithSingleName,Install-Module'
Install-Module ContosoClient,ContosoServer -RequiredVersion 2.0

# Below command fails with 'VersionParametersAreAllowedOnlyWithSingleName,Install-Module'
Install-Module ContosoClient,ContosoServer -MinimumVersion 2.0

```