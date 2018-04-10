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
# <a name="save-module"></a><span data-ttu-id="9e4af-103">Kaydet-Modülü</span><span class="sxs-lookup"><span data-stu-id="9e4af-103">Save-Module</span></span>

<span data-ttu-id="9e4af-104">Bir modül, yerel olarak yüklemeden kaydeder.</span><span class="sxs-lookup"><span data-stu-id="9e4af-104">Saves a module locally without installing it.</span></span>

## <a name="description"></a><span data-ttu-id="9e4af-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9e4af-105">Description</span></span>

<span data-ttu-id="9e4af-106">Kaydet-modül cmdlet modülü İnceleme için belirtilen depodan yerel olarak kaydeder.</span><span class="sxs-lookup"><span data-stu-id="9e4af-106">The Save-Module cmdlet saves a module locally from the specified repository for inspection.</span></span> <span data-ttu-id="9e4af-107">Modülü yüklü değil.</span><span class="sxs-lookup"><span data-stu-id="9e4af-107">The module is not installed.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="9e4af-108">Cmdlet sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9e4af-108">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Save-Module -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="9e4af-109">Cmdlet çevrimiçi Yardım başvurusu</span><span class="sxs-lookup"><span data-stu-id="9e4af-109">Cmdlet online help reference</span></span>

[<span data-ttu-id="9e4af-110">Kaydet-Modülü</span><span class="sxs-lookup"><span data-stu-id="9e4af-110">Save-Module</span></span>](http://go.microsoft.com/fwlink/?LinkId=531351)

## <a name="example-commands"></a><span data-ttu-id="9e4af-111">Örnek komutlar</span><span class="sxs-lookup"><span data-stu-id="9e4af-111">Example commands</span></span>

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