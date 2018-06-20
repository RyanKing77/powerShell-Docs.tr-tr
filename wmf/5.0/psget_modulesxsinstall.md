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
# <a name="side-by-side-version-support-on-powershell-50-or-newer"></a>Yan yana sürüm desteği PowerShell 5.0 veya daha yeni

Şimdi Yükle-Module, yan yana (SxS) modülü sürüm desteği olan güncelleştirme modülü ve Windows PowerShell 5.0 veya daha yeni çalışması Yayımla-Module cmdlet'leri.
Yayımlanacak sürüm belirtmek için yayımlama modülü cmdlet - RequiredVersion parametresi de ekledik. Path parametresi artık sürüm klasör modülü temel yolu destekler.

**Install-Module örnekler:**
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
