---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 7982acc111e95b4167f948314f176d53f39d3620
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
---
# <a name="reporting-on-jea"></a>JEA’da Raporlama
JEA yapılandırmanızı durumunu bildirmek üzere kullanabilirsiniz:
1.  **Get-PSSessionConfiguration** tüm listesini döndürmek için belirli bir makinede uç noktaları kayıtlı.
2.  **Get-PSSessionCapability** yeteneklerini raporlamak için herhangi bir kullanıcı belirli bir noktadaki sahiptir.

Bir örneği burada verilmiştir **Get-PSSessionCapability**:
```powershell
Get-PSSessionCapability -ConfigurationName Maintenance -Username "CONTOSO\JohnDoe"

CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           clear -> Clear-Host
Alias           cls -> Clear-Host
Alias           exsn -> Exit-PSSession
Alias           gcm -> Get-Command
Alias           measure -> Measure-Object
Alias           select -> Select-Object
Function        Clear-Host
Function        Exit-PSSession
Function        Get-Command
Function        Get-FormatData
Function        Get-Help
Function        Get-UserInfo
Function        Measure-Object
Function        Out-Default
Function        Select-Object
Cmdlet          Restart-Service                                    3.0.0.0 Microsof...


```

Raporlamak için _Eylemler_ kullanıcılar sürdü JEA oturumu sırasında şunları yapabilirsiniz:
1. Bu JEA uç noktası için "üzerinden güdümlü" dökümleri etkinleştirmek ve her kullanıcının eylemleri için bir tam günlük dökümü dizin bakın
2. PowerShell modülü günlüğünü etkinleştirmek ve PowerShell olay günlüklerini inceleyin.
