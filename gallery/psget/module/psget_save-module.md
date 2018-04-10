---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: Galeri, powershell, cmdlet, psget
title: Kaydet-Modülü
ms.openlocfilehash: c9078afb03dc074ee3831c2c395c0f1e6c4ffa38
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="save-module"></a>Kaydet-Modülü

Bir modül, yerel olarak yüklemeden kaydeder.

## <a name="description"></a>Açıklama

Kaydet-modül cmdlet modülü İnceleme için belirtilen depodan yerel olarak kaydeder. Modülü yüklü değil.

## <a name="cmdlet-syntax"></a>Cmdlet sözdizimi
```powershell
Get-Command -Name Save-Module -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a>Cmdlet çevrimiçi Yardım başvurusu

[Kaydet-Modülü](http://go.microsoft.com/fwlink/?LinkId=531351)

## <a name="example-commands"></a>Örnek komutlar

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


# Find a command and save its module
# This command finds the specified command, and then passes it to Save-Module to save it to the C:\temp folder.
Find-Command -Name "Get-NestedRequiredModule4" -Repository "INT" | Save-Module -Path "C:\temp\" -Verbose


# Save the role capability modules by piping the Find-RoleCapability output to Save-Module cmdlet.
Find-RoleCapability -Name Maintenance,MyJeaRole | Save-Module -Path C:\MyModulesPath


# Save a specific prerelease version of a module to C:\MySavedModuleLocation
Save-Module -Name ContosoServer -RequiredVersion 1.1.3-alpha -Path C:\MySavedModuleLocation -AllowPrerelease

# Install the latest version of a module by name, including prelrelease versions if one exists
Install-Module -Name ContosoServer -Path C:\MySavedModuleLocation -AllowPrerelease



```