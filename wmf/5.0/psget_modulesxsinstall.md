---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: d4168640f67cb1dd44e91d1867e87fd7a6b7f549
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218363"
---
# <a name="side-by-side-version-support-on-powershell-50-or-newer"></a><span data-ttu-id="0b778-102">Yan yana sürüm desteği PowerShell 5.0 veya daha yeni</span><span class="sxs-lookup"><span data-stu-id="0b778-102">Side-by-Side Version Support on PowerShell 5.0 or newer</span></span>

<span data-ttu-id="0b778-103">Şimdi Yükle-Module, yan yana (SxS) modülü sürüm desteği olan güncelleştirme modülü ve Windows PowerShell 5.0 veya daha yeni çalışması Yayımla-Module cmdlet'leri.</span><span class="sxs-lookup"><span data-stu-id="0b778-103">There is now side-by-side (SxS) module version support in Install-Module, Update-Module, and Publish-Module cmdlets that run in Windows PowerShell 5.0 or newer.</span></span>
<span data-ttu-id="0b778-104">Yayımlanacak sürüm belirtmek için yayımlama modülü cmdlet - RequiredVersion parametresi de ekledik.</span><span class="sxs-lookup"><span data-stu-id="0b778-104">Also, we have added a -RequiredVersion parameter to the Publish-Module cmdlet to specify the version to be published.</span></span> <span data-ttu-id="0b778-105">Path parametresi artık sürüm klasör modülü temel yolu destekler.</span><span class="sxs-lookup"><span data-stu-id="0b778-105">The Path parameter now supports the module base path with the version folder.</span></span>

<span data-ttu-id="0b778-106">**Install-Module örnekler:**</span><span class="sxs-lookup"><span data-stu-id="0b778-106">**Install-Module examples:**</span></span>
```powershell
Install-Module -Name PSScriptAnalyzer -RequiredVersion 1.1.0 -Repository PSGallery
Get-Module -ListAvailable -Name PSScriptAnalyzer | Format-List Name,Version,ModuleBase

Name : PSScriptAnalyzer
Version : 1.1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.0

Install-Module -Name PSScriptAnalyzer -RequiredVersion 1.1.1 -Repository PSGallery
Get-Module -ListAvailable -Name PSScriptAnalyzer | Format-List Name,Version,ModuleBase

Name       : PSScriptAnalyzer
Version    : 1.1.1
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.1
Name       : PSScriptAnalyzer
Version    : 1.1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.0

Get-InstalledModule -Name PSScriptAnalyzer -AllVersions

Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
1.1.0      PSScriptAnalyzer                    Module     PSGallery            PSScriptAnalyzer provides script analysis...
1.1.1      PSScriptAnalyzer                    Module     PSGallery            PSScriptAnalyzer provides script analysis...
```
