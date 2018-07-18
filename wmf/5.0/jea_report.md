---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 2fb2e4b0c40322b5ec78fabede22a7e3ecbbd2aa
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093771"
---
# <a name="reporting-on-jea"></a>JEA’da Raporlama

JEA yapılandırmanızın durumunu bildirmek üzere kullanabilirsiniz:

1. **Get-PSSessionConfiguration** uç noktaları belirli bir makinede kayıtlı tüm listesini döndürmek için.
1. **Get-PSSessionCapability** yeteneklerini raporlamak için herhangi bir kullanıcı belirli bir uç noktaya sahip.

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
