---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 2f05fe96ec792a31fabf3aff0f9e18b40178316c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685315"
---
# <a name="packagemanagement-cmdlets"></a>PackageManagement Cmdlet’leri

Yazılım bulma, yükleme veya envanterini (SDII) desteklemek için PackageManagement setinin budur. Bu işlemler için cmdlet'ler deneyin:

- `Find-Package`
- `Find-PackageProvider`
- `Get-Package`
- `Get-PackageProvider`
- `Get-PackageSource`
- `Import-PackageProvider`
- `Install-Package`
- `Install-PackageProvider`
- `Register-PackageSource`
- `Save-Package`
- `Set-PackageSource`
- `Uninstall-Package`
- `Unregister-PackageSource`

Bir PowerShell modülü PackageManagement olduğu gibi PackageManagement kendisini güncelleştirmek için aşağıdakileri yapabilirsiniz:

```powershell
Install-Module PackageManagement –Force
```

Bu durumda, PackageManagement yeni sürümüne geçiş yapmak için PowerShell oturumunda yeniden girmeniz gerekir.

## <a name="find-package-cmdletpowershellmodulepackagemanagementfind-package"></a>[Bul-Package cmdlet'i](/powershell/module/PackageManagement/Find-Package)

Bu cmdlet, paket sağlayıcıları bulma kullanılabilir paket kaynaklarını kullanan yazılım paketlerinin yüklü sağlar.

```powershell
# Find all available Windows PowerShell module packages from galleries registered
# with PowerShellGet provider
Find-Package -ProviderName PowerShellGet -Source as source
Find-Package -Name jquery –Provider NuGet -Source http://www.nuget.org/api/v2/

# Find package with name and version
# Here we are assuming that the user already registered nuget.org using
# Register-PackageSource. You can specify either the provider or the source, or
# neither. For the latter, performance may be less optimal as it searches through all
# the providers and registered sources.
Find-Package -Name jquery –Provider NuGet –RequiredVersion 2.1.4 -Source nuget.org
```

## <a name="find-packageprovider-cmdletpowershellmodulepackagemanagementfind-packageprovider"></a>[Bul PackageProvider cmdlet'i](/powershell/module/PackageManagement/Find-PackageProvider)

`Find-PackageProvider` Cmdlet'i ile PowerShellGet kayıtlı paket kaynakları kullanılabilir PackageManagement sağlayıcıları eşleşen bulur. Bu paket sağlayıcıları ile yükleme için kullanılabilir olan `Install-PackageProvider` cmdlet'i. Varsayılan olarak, bu 'PackageManagement' ve 'Provider' etiketleri PowerShell galerisinde kullanılabilir modül içerir.

`Find-PackageProvider` Ayrıca burada PackageManagement boostrapper sağlayıcısı bulmak ve onları yüklemek için kullandığımız PackageManagement azure blob depolama, kullanılabilir eşleşen PackageManagement sağlayıcıları bulur.

```powershell
#Find all available package providers in PackageManagement azure blob store as well as in PowerShellGallery.com
Find-PackageProvider

#Find all versions of a provider
Find-PackageProvider -Name "Nuget" -AllVersions

#Find a provider from a specified source
Find-PackageProvider -Name "Gistprovider" -Source "PSGallery"
```

## <a name="get-package-cmdletpowershellmodulepackagemanagementget-package"></a>[Get-Package cmdlet'i](/powershell/module/PackageManagement/Get-Package)

Bu cmdlet, PackageManagement kullanarak yüklenen tüm yazılım paketlerinin listesini döndürür.

```powershell
# Get all the packages installed by Programs provider
Get-Package –Provider Programs

# Get all the packages installed by NuGet provider at c:\test using the dynamic
# parameter destination
Get-Package –Provider NuGet -Destination c:\test
```

## <a name="get-packageprovider-cmdletpowershellmodulepackagemanagementget-packageprovider"></a>[Get-PackageProvider cmdlet'i](/powershell/module/PackageManagement/Get-PackageProvider)

Cmdlet'ini kullanarak yüklenir ve yerel makine üzerinde kullanılmaya hazır olan paket sağlayıcıları envantere kaydedilmiş.

```powershell
# Get all currently loaded package providers
Get-PackageProvider

# The following cmdlet will show all the package providers available on the machine (including those that are not loaded):
Get-PackageProvider -ListAvailable
```

## <a name="get-packagesource-cmdletpowershellmodulepackagemanagementget-packagesource"></a>[Get-PackageSource cmdlet'i](/powershell/module/PackageManagement/Get-PackageSource)

Bu cmdlet için bir paket sağlayıcısı kayıtlı paket kaynaklarını listesini alır.

```powershell
# Get all package sources
Get-PackageSource

# Get all package sources for a specific provider
Get-PackageSource –ProviderName PowerShellGet
```

## <a name="import-packageprovider-cmdletpowershellmodulepackagemanagementimport-packageprovider"></a>[İçeri aktarma PackageProvider cmdlet'i](/powershell/module/PackageManagement/Import-PackageProvider)

Bu cmdlet, geçerli oturum için paket Yönetimi Paketi sağlayıcıları ekler.

```powershell
# Import a package provider from the local machine
Import-PackageProvider –Name MyProvider

#The -Name parameter can be either the name of the provider or the full path to the provider. Currently, we support .dll, .exe and.psm1 for the full path case. If the name of the provider is used for the -Name parameter, then additional version parameters such as -RequiredVersion, -MinimumVersion and -MaximumVersion may be specified. Otherwise, the latest version of the provider will be imported.

#If a package provider is not yet loaded to your system, we can discover and install on-demand. You can use explicit discovery and install cmdlets to do so:
 Find-PackageProvider
 Install-PackageProvider –Name MyProvider

#After installed, follow the Import-PackageProvider to load it to your system.

# Import a specific version of a package provider. PackageManagement supports installations of multiple versions of a package provider using PackageProvider cmdlets (not by bootstrapper provider). You can install another version of a package provider given that you already have one up running by:
Find-PackageProvider –Name "Nuget" -AllVersions
Install-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.201" -Force
Get-PackageProvider –ListAvailable
Import-PackageProvider –Name "Nuget" -RequiredVersion "2.8.5.201" -Verbose
Import-PackageProvider –Name MyProvider –RequiredVersion xxxx -force
```

## <a name="-install-package-cmdletpowershellmodulepackagemanagementinstall-package"></a>[ Install-Package cmdlet'i](/powershell/module/PackageManagement/Install-Package)

Bu cmdlet'i, kullanılabilir paket kaynaklarını kullanan yazılım paketlerinin yükleme paketi sağlayıcıları yüklendi sağlar.

```powershell
# Install a package by name.
# NuGet provider requires us to provide the dynamic parameter destination path
# when we use this provider to install. Not all providers will require you to supply
# dynamic parameters for PackageManagement cmdlets.
Install-Package -Name jquery -Source nuget.org -Destination c:\test

# Install a package by piping.
Find-Package -Name jquery –Provider NuGet | Install-Package -Destination c:\test
```

## <a name="install-packageprovider-cmdletpowershellmodulepackagemanagementinstall-packageprovider"></a>[Yükleme PackageProvider cmdlet'i](/powershell/module/PackageManagement/Install-PackageProvider)

Bu cmdlet, bir veya daha fazla paket Yönetimi Paketi sağlayıcılarını yükler.

```powershell
# Install a package provider from the PowerShell Gallery
Install-PackageProvider –Name "Gistprovider" -Verbose

# Install a specified version of a package provider
Find-PackageProvider –Name "Nuget" -AllVersions
Install-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.201" -Force

# Find a provider and install it
Find-PackageProvider –Name "Gistprovider" | Install-PackageProvider -Verbose

# Install a provider to the current user’s module folder
Install-PackageProvider –Name Gistprovider –Verbose –Scope CurrentUser
```

## <a name="register-packagesource-cmdletpowershellmodulepackagemanagementregister-packagesource"></a>[Register-PackageSource cmdlet'i](/powershell/module/PackageManagement/Register-PackageSource)

Bu cmdlet bir paket kaynağı için belirtilen paket sağlayıcısı ekler.
Her PackageManagement sağlayıcısı, bir veya birden çok yazılım kaynakları veya depoları olabilir. PackageManagement kaynak ekleme/kaldırma/sorgu için PowerShell cmdlet'leri sağlar. Örneğin, bir paket kaynağı için NuGet sağlayıcısı kaydedebilirsiniz:

```powershell
Register-PackageSource -Name "NugetSource" -Location "http://www.nuget.org/api/v2" –ProviderName nuget
```

## <a name="save-package-cmdletpowershellmodulepackagemanagementsave-package"></a>[Kaydet-Package cmdlet'i](/powershell/module/PackageManagement/Save-Package)

Bu cmdlet, paketleri yüklemeden yerel bilgisayara kaydeder.

```powershell
# Saves jquery package to c:\test using NuGetProvider
# Notes that the -Path parameter must point to an existing location
Save-Package -Name jquery –Provider NuGet -Path c:\test

# Save a package by piping.
Find-Package -Name jquery -Source http://www.nuget.org/api/v2/ | Save-Package -Path c:\test
Find-Package -Source c:\test
```

## <a name="set-packagesource-cmdletpowershellmodulepackagemanagementset-packagesource"></a>[Set-PackageSource cmdlet'i](/powershell/module/PackageManagement/Set-PackageSource)

Bu cmdlet, var olan bir paket kaynağı bilgilerini değiştirir.

```powershell
#Set-PackageSource changes the values for a source that has already been registered by running the Register-PackageSource cmdlet. By #running Set-PackageSource, you can change the source name and location.
Set-PackageSource  -Name nuget.org -Location  http://www.nuget.org/api/v2 -NewName nuget2 -NewLocation https://www.nuget.org/api/v2
```

## <a name="uninstall-package-cmdletpowershellmodulepackagemanagementuninstall-package"></a>[Paket kaldırma cmdlet'i](/powershell/module/PackageManagement/Uninstall-Package)

Bu cmdlet, yerel bilgisayarda yüklü paketleri kaldırır.

```powershell
# Uninstall jquery using nuget
Uninstall-Package -Name jquery –Provider NuGet -Destination c:\test

# Uninstall a package with by piping with Get-Package
Get-Package -Name jquery –Provider NuGet -Destination c:\test | Uninstall-Package
```

## <a name="unregister-packagesource-cmdletpowershellmodulepackagemanagementunregister-packagesource"></a>[Kaydı PackageSource cmdlet'i](/powershell/module/PackageManagement/Unregister-PackageSource)

```powershell
# Unregister a package source for the NuGet provider. You can use command Unregister-PackageSource, to disconnect with a repository, and Get-PackageSource, to discover what the repositories are associated with that provider.
Unregister-PackageSource  -Name "NugetSource"
```