---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, Kur
ms.openlocfilehash: f68847ba8292a277e464025c1baa17a5aa2752f5
ms.sourcegitcommit: 4ab9a86e47b6effe8fe22ebeb81e8fadff41d31c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2017
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

