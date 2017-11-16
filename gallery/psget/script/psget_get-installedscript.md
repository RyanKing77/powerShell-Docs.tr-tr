---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: Galeri, powershell, cmdlet, psget
title: Get-InstalledScript
ms.openlocfilehash: f35e57cdadd1448bd9032ab007d692003c4cf4a2
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="get-installedscript"></a>Get-InstalledScript

Alır, komut dosyaları bir bilgisayarda yüklü.

## <a name="description"></a>Açıklama

Get-InstalledScript cmdlet'i bir bilgisayarda yüklü PowerShell betikleri alır.

Yüklü her komut dosyası için Get-InstalledScript isteğe bağlı olarak yöneltilen bir PSRepositoryItemInfo nesnesi kaldırma komut dosyası için yüklenen komut dosyalarını kaldırma için döndürür.

- Get-InstalledScript yüklü komut dosyalarının sürüm parametreleri adına göre filtre uygulayabilirsiniz.
- Get-InstalledScript sürüm parametrelerle filtre uygulayabilirsiniz: MinimumVersion, MaximumVersion, RequiredVersion, AllVersions.
  - Bu parametreler MinmimumVersion ve MaximumVersion dışında birbirini dışlar.
  - Bu sürümü parametreleri yalnızca bir joker karakter bulunmayan tek betiği adıyla izin verilir.
  - RequiredVersion parametresi belirtilmezse, Get-InstalledScript en düşük bir sürüm belirtilmezse eşit veya bundan büyük belirtilen en düşük sürüm veya komut dosyası en son sürümü yüklü betik en son sürümünü döndürür. 
  - RequiredVersion parametresi belirtilirse, Get-InstalledScript yalnızca belirtilen sürümü ile tam olarak yüklü komut dosyası sürümünü döndürür.

## <a name="cmdlet-syntax"></a>Cmdlet sözdizimi

```powershell
Get-Command -Name Get-InstalledScript -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a>Cmdlet çevrimiçi Yardım başvurusu

[Get-InstalledScript](http://go.microsoft.com/fwlink/?LinkId=619790)

## <a name="example-commands"></a>Örnek komutlar

```powershell

# Get all scripts installed using PowerShellGet cmdlets
Get-InstalledScript

# Get a specific installed script
Get-InstalledScript Show-Tree

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.0.0      Show-Tree                           PSGallery            Script to show the layout of PowerShell namespaces (Tr...

# Get installed script with wildcards
Get-InstalledScript -Name *Azure*

# Get all versions of an installed script
Get-InstalledScript -Name Connect-O365 -AllVersions

# Get installed script with MinimumVersion
Get-InstalledScript -Name Connect-O365 -MinimumVersion 1.1

# Get installed script with MaximumVersion
Get-InstalledScript -Name Connect-O365 -MaximumVersion 1.6.3

# Get installed script with version range
Get-InstalledScript -Name Connect-O365 -MinimumVersion 1.1 -MaximumVersion 1.6.3

# Get installed script with RequiredVersion
Get-InstalledScript -Name Connect-O365 -RequiredVersion 1.4

# Properties of Get-InstalledScript returned object
Get-InstalledScript Show-Tree | Format-List * -Force

Name                       : Show-Tree
Version                    : 1.0.0
Type                       : Script
Description                : Script to show the layout of PowerShell namespaces (Trees) using ASCII
Author                     : Jeffrey Snover
CompanyName                : jsnover
Copyright                  : (C) Microsoft Corporation. All rights reserved.
PublishedDate              : 2/15/2016 10:15:35 PM
InstalledDate              : 5/4/2016 11:44:13 PM
UpdatedDate                :
LicenseUri                 :
ProjectUri                 :
IconUri                    :
Tags                       : {Nano, PSScript}
Includes                   : {Function, RoleCapability, Command, DscResource...}
PowerShellGetFormatVersion :
ReleaseNotes               :
Dependencies               : {}
RepositorySourceLocation   : https://www.powershellgallery.com/api/v2/
Repository                 : PSGallery
PackageManagementProvider  : NuGet
AdditionalMetadata         : {description, installeddate, tags, PackageManagementProvider...}
InstalledLocation          : C:\Program Files\WindowsPowerShell\Scripts


```

