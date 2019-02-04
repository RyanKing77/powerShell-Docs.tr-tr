---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: cd3338ae305896e282056a871974e5f899ef6ff5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686246"
---
# <a name="reporting-on-jea"></a>JEA’da Raporlama

JEA yapılandırmanızın durumunu bildirmek üzere kullanabilirsiniz:

1. **Get-PSSessionConfiguration** uç noktaları belirli bir makinede kayıtlı tüm listesini döndürmek için.
2. **Get-PSSessionCapability** yeteneklerini raporlamak için herhangi bir kullanıcı belirli bir uç noktaya sahip.

İşte bir örnek **Get-PSSessionCapability**:

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

Bildirmek üzere _eylemleri_ kullanıcılar geçen bir JEA oturumu sırasında şunları yapabilirsiniz:

1. Bu JEA uç noktası için "üzerinden güdümlü" dökümleri etkinleştirin ve her kullanıcının eylemleri için bir tam günlüğü döküm directory başvurun
2. PowerShell modülü günlük özelliğini açar ve PowerShell olay günlüklerini inceleyin.