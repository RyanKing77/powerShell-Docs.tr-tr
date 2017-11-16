---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, Kur
ms.openlocfilehash: f3c218fc668e35fa50047459d8031d77cdf985a2
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="reporting-on-jea"></a><span data-ttu-id="79df8-102">JEA üzerinde raporlama</span><span class="sxs-lookup"><span data-stu-id="79df8-102">Reporting on JEA</span></span>
<span data-ttu-id="79df8-103">JEA yapılandırmanızı durumunu bildirmek üzere kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="79df8-103">In order to report on the state of your JEA configuration, you can use:</span></span>
1.  <span data-ttu-id="79df8-104">**Get-PSSessionConfiguration** tüm listesini döndürmek için belirli bir makinede uç noktaları kayıtlı.</span><span class="sxs-lookup"><span data-stu-id="79df8-104">**Get-PSSessionConfiguration** to return a list of all registered endpoints on a given machine.</span></span>
2.  <span data-ttu-id="79df8-105">**Get-PSSessionCapability** yeteneklerini raporlamak için herhangi bir kullanıcı belirli bir noktadaki sahiptir.</span><span class="sxs-lookup"><span data-stu-id="79df8-105">**Get-PSSessionCapability** to report on the capabilities any given user has on a specific endpoint.</span></span>

<span data-ttu-id="79df8-106">Bir örneği burada verilmiştir **Get-PSSessionCapability**:</span><span class="sxs-lookup"><span data-stu-id="79df8-106">Here’s an example of **Get-PSSessionCapability**:</span></span>
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

<span data-ttu-id="79df8-107">Raporlamak için _Eylemler_ kullanıcılar sürdü JEA oturumu sırasında şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="79df8-107">To report on the _actions_ users took during a JEA session, you can:</span></span>
1. <span data-ttu-id="79df8-108">Bu JEA uç noktası için "üzerinden güdümlü" dökümleri etkinleştirmek ve her kullanıcının eylemleri için bir tam günlük dökümü dizin bakın</span><span class="sxs-lookup"><span data-stu-id="79df8-108">Enable the "over-the-shoulder" transcripts for that JEA endpoint and consult the transcript directory for a full log of each user's actions</span></span>
2. <span data-ttu-id="79df8-109">PowerShell modülü günlüğünü etkinleştirmek ve PowerShell olay günlüklerini inceleyin.</span><span class="sxs-lookup"><span data-stu-id="79df8-109">Turn on PowerShell module logging and inspect the PowerShell event logs.</span></span>

