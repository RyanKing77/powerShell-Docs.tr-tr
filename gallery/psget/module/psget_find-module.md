---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: Galeri, powershell, cmdlet, psget
title: "Bulma Modülü"
ms.openlocfilehash: 65c466909c007ed08c3fa978f78483983b00ba73
ms.sourcegitcommit: 58371abe9db4b9a0e4e1eb82d39a9f9e187355f9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2017
---
# <a name="find-module"></a>Bulma Modülü
Belirtilen ölçütlerle eşleşen bir çevrimiçi galeriden modülleri bulur.

## <a name="description"></a>Açıklama
Bulma modülü belirtilen ölçütlere uyan kayıtlı depoları modüllerden bulur.
Bulunan her modül için bulma modülü isteğe bağlı olarak yöneltilen bir PSRepositoryItemInfo nesnesi yükle-Module modülleri yüklemek için döndürür.

- Bulma modülü için modüle bağlı filtre içeriği komutu, - DscResource, - RoleCapability ve - parametrelerini içerir.
- Bulma modülü sürüm parametrelerle filtre uygulayabilirsiniz: MinimumVersion, MaximumVersion, RequiredVersion, AllVersions.
  - Bu parametreler MinmimumVersion ve MaximumVersion dışında birbirini dışlar.
  - Bu sürümü parametreleri yalnızca bir joker karakter bulunmayan tek modülü adıyla izin verilir.
  - RequiredVersion parametresi belirtilmezse, bulma modülü en düşük bir sürüm belirtilmezse eşit veya bundan büyük belirtilen en düşük sürüm veya modülünün en son sürümünü modülü en son sürümünü döndürür. 
  - RequiredVersion parametresi belirtilirse, bulma modülü yalnızca tam olarak belirtilen sürümle eşleşen modülü sürümünü döndürür.
- Bulma modülü modülü meta filtreleyebilir Tag parametresini ile
- Bulma modülü deposu özgü arama dili filtreleyebilir - filtre parametresine sahip.
- Bulma modülü tüm veya az kayıtlı depoları modüllerden filtre uygulayabilirsiniz.

## <a name="cmdlet-syntax"></a>Cmdlet sözdizimi
```powershell
Get-Command -Name Find-Module -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a>Cmdlet çevrimiçi Yardım başvurusu

[Bulma Modülü](http://go.microsoft.com/fwlink/?LinkID=398574)

## <a name="example-commands"></a>Örnek komutlar
```powershell
# Find a specific module
Find-Module Azure

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.3.2      Azure                               PSGallery            Microsoft Azure PowerShell - Service Management

# Find multiple modules
Find-Module Azure,AzureRM

# Find modules with wildcards in -Name
Find-Module -Name AzureRM*

# Find all versions of a module
Find-Module -Name PSReadline -AllVersions

# Find a module with -MinimumVersion. 
# With MinimumVersion we can find a module whose version is greate than or equal to the specified MinimumVersion value.
Find-Module -Name PSReadline -MinimumVersion 1.0.0.12

# Find a module with MaximumVersion
Find-Module -Name PSReadline -MaximumVersion 1.0.0.13

# Find a module with both MinimumVersion and MaximumVersion range.
Find-Module -Name PSReadline -MinimumVersion 1.0.0.12 -MaximumVersion 1.0.0.13

# Find a module with exact version
Find-Module -Name AzureRM -RequiredVersion 1.3.2

# Find a module with a specific prerelease version
Find-Module -Name AzureRM -RequiredVersion 1.3.2-alpha -AllowPrerelease

# Find a module from the specified repository
Find-Module -Name Contoso -Repository MyLocalRepo

# Find available modules from all registered repositories
Find-Module

# Find available modules from few registered repositories
Find-Module -Repository PSGallery,PrivatePSGallery

# Find a module along with its dependencies
Find-Module -Name AzureRM -IncludeDependencies

# Find all modules with Dsc resources
Find-Module -Includes DscResource

# Find modules with a specific DscResource
Find-Module -DscResource xFirewall

# Find all modules with cmdlets
Find-Module -Includes Cmdlet

# Find all modules with functions
Find-Module -Includes Function

# Find all modules with Role Capabilities
Find-Module -Includes RoleCapability

# Find all modules with the specified Role Capability name
Find-Module -RoleCapability RoleCap1
Find-Module -RoleCapability RoleCap2 -Includes RoleCapability

# Find modules with specific commands
Find-Module -Command Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer
Find-Module -Command Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer -Includes Cmdlet
Find-Module -Command Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer -Includes Function

# Find modules with -Filter based search. -Filter searches in description and names
Find-Module -Filter Cookbook
Find-Module -Filter RBAC
Find-Module -Filter 'App Domain' -Includes 'DscResource'

# Find all modules with tags Azure or DSC
Find-Module -Tag Azure, DSC

# Properties of Find-Module returned object
Find-Module AzureRM.Profile | Format-List * -Force

Name                       : AzureRM.profile
Version                    : 1.0.8
Type                       : Module
Description                : Microsoft Azure PowerShell - Profile credential management cmdlets for Azure Resource
                             Manager
Author                     : Microsoft Corporation
CompanyName                : {elogeel, azure-sdk}
Copyright                  : Microsoft Corporation. All rights reserved.
PublishedDate              : 5/4/2016 9:40:33 PM
InstalledDate              :
UpdatedDate                :
LicenseUri                 : https://raw.githubusercontent.com/Azure/azure-powershell/dev/LICENSE.txt
ProjectUri                 : https://github.com/Azure/azure-powershell
IconUri                    :
Tags                       : {PSModule}
Includes                   : {Function, RoleCapability, Command, DscResource...}
PowerShellGetFormatVersion :
ReleaseNotes               : https://github.com/Azure/azure-powershell/blob/dev/ChangeLog.md
Dependencies               : {}
RepositorySourceLocation   : https://www.powershellgallery.com/api/v2/
Repository                 : PSGallery
PackageManagementProvider  : NuGet
AdditionalMetadata         : {downloadCount, description, copyright, FileList...}

```

