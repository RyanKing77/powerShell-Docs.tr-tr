---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, Kur
ms.openlocfilehash: 6cba004890fc4b1dfac40920f751f61b0530cce9
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="packagemanagement-cmdlets"></a>PackageManagement cmdlet'leri
Yazılım bulma, yükleme ve envanter (SDII) desteklemek için PackageManagement çekirdek budur. Bu işlemler için cmdlet'ler deneyin:
-   Paket Bul
-   Bul PackageProvider
-   Get-Package
-   Get-PackageProvider
-   Get-PackageSource
-   İçeri aktarma PackageProvider
-   Install-Package
-   Yükleme PackageProvider
-   Register-PackageSource
-   Kaydet-Package
-   Set-PackageSource
-   Kaldırma paketi
-   Kaydı PackageSource

PowerShell modülü PackageManagement olduğu gibi PackageManagement kendisini güncelleştirmek için aşağıdakileri yapabilirsiniz:
```powershell
PS C:\> Install-Module PackageManagement –Force
```
Bu durumda, PackageManagement yeni sürümüne geçiş için PowerShell oturumu yeniden girmeniz gerekecek.

## <a name="find-package-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890709aspx"></a>[Bul-Package cmdlet'i](https://technet.microsoft.com/en-us/library/dn890709.aspx)
Bu cmdlet, yazılım paketlerini kullanarak kullanılabilir paket kaynakları bulma paket sağlayıcıları yüklenen sağlar.
```powershell
# Find all available Windows PowerShell module packages from galleries registered
# with PowerShellGet provider
Find-Package -Provider PowerShellGet -Source PSGallery

# Find a package from a provider that is not yet installed
# This will bootstrap NuGet provider and then search for jquery package using NuGet
# with <http://www.nuget.org/api/v2/> as source
Find-Package -Name jquery –Provider NuGet -Source http://www.nuget.org/api/v2/

# Find package with name and version
# Here we are assuming that the user already registered nuget.org using
# Register-PackageSource. You can specify either the provider or the source, or
# neither. For the latter, performance may be less optimal as it searches through all
# the providers and registered sources.
Find-Package -Name jquery –Provider NuGet –RequiredVersion 2.1.4 -Source nuget.org
```

## <a name="find-packageprovider-cmdlethttpstechnetmicrosoftcomen-uslibrarymt676544aspx"></a>[Bul PackageProvider cmdlet'i](https://technet.microsoft.com/en-us/library/mt676544.aspx)
Bul PackageProvider cmdlet ile PowerShellGet kayıtlı paket kaynaklarını kullanılabilir eşleşen PackageManagement sağlayıcısı bulur. Bu paket yükleme PackageProvider cmdlet ile yükleme için kullanılabilir sağlayıcılarıdır. Varsayılan olarak, bu 'PackageManagement' ve 'Provider' etiketleri PowerShell galerisinde kullanılabilir modül içerir. 

Bul PackageProvider PackageManagement azure blob depolama burada PackageManagement boostrapper Sağlayıcısı'nı bulma ve bunları yükleme için kullanırız kullanılabilir eşleşen PackageManagement sağlayıcısı da bulur.
```powershell
#Find all available package providers in PackageManagement azure blob store as well as in PowerShellGallery.com
Find-PackageProvider

#Find all versions of a provider
Find-PackageProvider -Name "Nuget" -AllVersions

#Find a provider from a specified source
Find-PackageProvider -Name "Gistprovider" -Source "PSGallery"
```

## <a name="get-package-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890704aspx"></a>[Get-Package cmdlet'i](https://technet.microsoft.com/en-us/library/dn890704.aspx)
Bu cmdlet PackageManagement kullanılarak yüklenen tüm yazılım paketlerinin listesini döndürür.
```powershell
# Get all the packages installed by Programs provider
Get-Package –Provider Programs

# Get all the packages installed by NuGet provider at c:\test using the dynamic
# parameter destination
Get-Package –Provider NuGet -Destination c:\test
```

## <a name="get-packageprovider-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890703aspx"></a>[Get-PackageProvider cmdlet'i](https://technet.microsoft.com/en-us/library/dn890703.aspx)
Yüklenen ve yerel makinede kullanılacak hazır paket sağlayıcıları cmdlet'ini kullanarak envantere kaydedilmiş.
```powershell
# Get all currently loaded package providers
Get-PackageProvider

# The following cmdlet will show all the package providers available on the machine (including those that are not loaded):
Get-PackageProvider -ListAvailable
```

## <a name="get-packagesource-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890705aspx"></a>[Get-PackageSource cmdlet'i](https://technet.microsoft.com/en-us/library/dn890705.aspx)
Bu cmdlet için bir paket sağlayıcı kayıtlı paket kaynaklarını listesini alır.
```powershelll
# Get all package sources
Get-PackageSource

# Get all package sources for a specific provider
Get-PackageSource –ProviderName PowerShellGet
```

## <a name="import-packageprovider-cmdlethttpstechnetmicrosoftcomen-uslibrarymt676545aspx"></a>[İçeri aktarma PackageProvider cmdlet'i](https://technet.microsoft.com/en-us/library/mt676545.aspx)
Bu cmdlet geçerli oturuma paket Yönetim Paketi sağlayıcılar ekler.
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

##<a name="-install-package-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890711aspx"></a>[Install-Package cmdlet'i](https://technet.microsoft.com/en-us/library/dn890711.aspx)

Bu cmdlet'i kullanarak kullanılabilir paket kaynakları içindeki yazılım paketlerini yükleme paketini sağlayıcıları yüklenen sağlar.
```powershell
# Install a package by name.
# NuGet provider requires us to provide the dynamic parameter destination path
# when we use this provider to install. Not all providers will require you to supply
# dynamic parameters for PackageManagement cmdlets.
Install-Package -Name jquery -Source nuget.org -Destination c:\test

# Install a package by piping.
Find-Package -Name jquery –Provider NuGet | Install-Package -Destination c:\test
```

## <a name="install-packageprovider-cmdlethttpstechnetmicrosoftcomen-uslibrarymt676543aspx"></a>[Yükleme PackageProvider cmdlet'i](https://technet.microsoft.com/en-us/library/mt676543.aspx)
Bu cmdlet, bir veya daha fazla paket Yönetimi Paketi sağlayıcı yükler.
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

## <a name="register-packagesource-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890701aspx"></a>[Register-PackageSource cmdlet'i](https://technet.microsoft.com/en-us/library/dn890701.aspx)
Bu cmdlet bir paket kaynağı için belirtilen paket sağlayıcısı ekler.
Her PackageManagement sağlayıcısı, bir veya birden çok yazılım kaynakları veya depoları olabilir. PackageManagement kaynak Ekle/Kaldır/sorgu için PowerShell cmdlet'leri sağlar. Örneğin, bir paket kaynağı için NuGet sağlayıcısı kaydedebilirsiniz:
```powershell
Register-PackageSource -Name "NugetSource" -Location "http://www.nuget.org/api/v2" –ProviderName nuget
```

## <a name="save-package-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890708aspx"></a>[Kaydet-Package cmdlet'i](https://technet.microsoft.com/en-us/library/dn890708.aspx)
Bu cmdlet, paketleri yüklemeden yerel bilgisayara kaydeder.
```powershell
# Saves jquery package to c:\test using NuGetProvider
# Notes that the -Path parameter must point to an existing location
Save-Package -Name jquery –Provider NuGet -Path c:\test

# Save a package by piping.
Find-Package -Name jquery -Source http://www.nuget.org/api/v2/ | Save-Package -Path c:\test
Find-Package -source c:\test
```

## <a name="set-packagesource-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890710aspx"></a>[Set-PackageSource cmdlet'i](https://technet.microsoft.com/en-us/library/dn890710.aspx)
Bu cmdlet, var olan bir paket kaynağı ile ilgili bilgileri değiştirir. 
```powershell
#Set-PackageSource changes the values for a source that has already been registered by running the Register-PackageSource cmdlet. By #running Set-PackageSource, you can change the source name and location.
Set-PackageSource  -Name nuget.org -Location  http://www.nuget.org/api/v2 -NewName nuget2 -NewLocation https://www.nuget.org/api/v2 
```

## <a name="uninstall-package-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890702aspx"></a>[Kaldırma paket cmdlet'i](https://technet.microsoft.com/en-us/library/dn890702.aspx)
Bu cmdlet yerel bilgisayarda yüklü olan paketleri kaldırır.
```powershell
# Uninstall jquery using nuget
Uninstall-Package -Name jquery –Provider NuGet -Destination c:\test

# Uninstall a package with by piping with Get-Package
Get-Package -Name jquery –Provider NuGet -Destination c:\test | Uninstall-Package
```

## <a name="unregister-packagesource-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890707aspx"></a>[Kaydı PackageSource cmdlet'i](https://technet.microsoft.com/en-us/library/dn890707.aspx)
```powershell
# Unregister a package source for the NuGet provider. You can use command Unregister-PackageSource, to disconnect with a repository, and Get-PackageSource, to discover what the repositories are associated with that provider.
Unregister-PackageSource  -Name "NugetSource"
```

