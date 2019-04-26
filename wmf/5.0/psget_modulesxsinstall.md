---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 0a481fb9d4f2aab89bc448c71b01f1d541cf24bc
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085091"
---
# <a name="side-by-side-version-support-on-powershell-50-or-newer"></a><span data-ttu-id="563bf-102">PowerShell 5.0 veya daha yeni yan yana sürüm desteği</span><span class="sxs-lookup"><span data-stu-id="563bf-102">Side-by-Side Version Support on PowerShell 5.0 or newer</span></span>

<span data-ttu-id="563bf-103">Install-Module, yan yana (SxS) modülü sürüm desteği sunuldu güncelleştirme modülü ve Windows PowerShell 5.0 veya daha yeni çalışması Publish-Module cmdlet'leri.</span><span class="sxs-lookup"><span data-stu-id="563bf-103">There is now side-by-side (SxS) module version support in Install-Module, Update-Module, and Publish-Module cmdlets that run in Windows PowerShell 5.0 or newer.</span></span>
<span data-ttu-id="563bf-104">Yayımlanacak sürümü belirtmek için Publish-Module cmdlet'e - RequiredVersion parametresi de ekledik.</span><span class="sxs-lookup"><span data-stu-id="563bf-104">Also, we have added a -RequiredVersion parameter to the Publish-Module cmdlet to specify the version to be published.</span></span> <span data-ttu-id="563bf-105">Path parametresi artık sürüm klasörle modül temel yolu destekler.</span><span class="sxs-lookup"><span data-stu-id="563bf-105">The Path parameter now supports the module base path with the version folder.</span></span>

<span data-ttu-id="563bf-106">**Install-Module örnekler:**</span><span class="sxs-lookup"><span data-stu-id="563bf-106">**Install-Module examples:**</span></span>
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
