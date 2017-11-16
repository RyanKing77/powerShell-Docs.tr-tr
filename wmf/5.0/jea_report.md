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
# <a name="reporting-on-jea"></a>JEA üzerinde raporlama
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

