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
# <a name="reporting-on-jea"></a><span data-ttu-id="dffda-102">JEA’da Raporlama</span><span class="sxs-lookup"><span data-stu-id="dffda-102">Reporting on JEA</span></span>

<span data-ttu-id="dffda-103">JEA yapılandırmanızın durumunu bildirmek üzere kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="dffda-103">In order to report on the state of your JEA configuration, you can use:</span></span>

1. <span data-ttu-id="dffda-104">**Get-PSSessionConfiguration** uç noktaları belirli bir makinede kayıtlı tüm listesini döndürmek için.</span><span class="sxs-lookup"><span data-stu-id="dffda-104">**Get-PSSessionConfiguration** to return a list of all registered endpoints on a given machine.</span></span>
1. <span data-ttu-id="dffda-105">**Get-PSSessionCapability** yeteneklerini raporlamak için herhangi bir kullanıcı belirli bir uç noktaya sahip.</span><span class="sxs-lookup"><span data-stu-id="dffda-105">**Get-PSSessionCapability** to report on the capabilities any given user has on a specific endpoint.</span></span>

<span data-ttu-id="dffda-106">İşte bir örnek **Get-PSSessionCapability**:</span><span class="sxs-lookup"><span data-stu-id="dffda-106">Here's an example of **Get-PSSessionCapability**:</span></span>

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

<span data-ttu-id="dffda-107">Bildirmek üzere _eylemleri_ kullanıcılar geçen bir JEA oturumu sırasında şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="dffda-107">To report on the _actions_ users took during a JEA session, you can:</span></span>
1. <span data-ttu-id="dffda-108">Bu JEA uç noktası için "üzerinden güdümlü" dökümleri etkinleştirin ve her kullanıcının eylemleri için bir tam günlüğü döküm directory başvurun</span><span class="sxs-lookup"><span data-stu-id="dffda-108">Enable the "over-the-shoulder" transcripts for that JEA endpoint and consult the transcript directory for a full log of each user's actions</span></span>
2. <span data-ttu-id="dffda-109">PowerShell modülü günlük özelliğini açar ve PowerShell olay günlüklerini inceleyin.</span><span class="sxs-lookup"><span data-stu-id="dffda-109">Turn on PowerShell module logging and inspect the PowerShell event logs.</span></span>
