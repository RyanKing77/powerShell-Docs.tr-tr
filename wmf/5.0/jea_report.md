---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 7982acc111e95b4167f948314f176d53f39d3620
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
---
# <a name="reporting-on-jea"></a><span data-ttu-id="066f3-102">JEA’da Raporlama</span><span class="sxs-lookup"><span data-stu-id="066f3-102">Reporting on JEA</span></span>
<span data-ttu-id="066f3-103">JEA yapılandırmanızı durumunu bildirmek üzere kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="066f3-103">In order to report on the state of your JEA configuration, you can use:</span></span>
1.  <span data-ttu-id="066f3-104">**Get-PSSessionConfiguration** tüm listesini döndürmek için belirli bir makinede uç noktaları kayıtlı.</span><span class="sxs-lookup"><span data-stu-id="066f3-104">**Get-PSSessionConfiguration** to return a list of all registered endpoints on a given machine.</span></span>
2.  <span data-ttu-id="066f3-105">**Get-PSSessionCapability** yeteneklerini raporlamak için herhangi bir kullanıcı belirli bir noktadaki sahiptir.</span><span class="sxs-lookup"><span data-stu-id="066f3-105">**Get-PSSessionCapability** to report on the capabilities any given user has on a specific endpoint.</span></span>

<span data-ttu-id="066f3-106">Bir örneği burada verilmiştir **Get-PSSessionCapability**:</span><span class="sxs-lookup"><span data-stu-id="066f3-106">Here’s an example of **Get-PSSessionCapability**:</span></span>
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

<span data-ttu-id="066f3-107">Raporlamak için _Eylemler_ kullanıcılar sürdü JEA oturumu sırasında şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="066f3-107">To report on the _actions_ users took during a JEA session, you can:</span></span>
1. <span data-ttu-id="066f3-108">Bu JEA uç noktası için "üzerinden güdümlü" dökümleri etkinleştirmek ve her kullanıcının eylemleri için bir tam günlük dökümü dizin bakın</span><span class="sxs-lookup"><span data-stu-id="066f3-108">Enable the "over-the-shoulder" transcripts for that JEA endpoint and consult the transcript directory for a full log of each user's actions</span></span>
2. <span data-ttu-id="066f3-109">PowerShell modülü günlüğünü etkinleştirmek ve PowerShell olay günlüklerini inceleyin.</span><span class="sxs-lookup"><span data-stu-id="066f3-109">Turn on PowerShell module logging and inspect the PowerShell event logs.</span></span>
