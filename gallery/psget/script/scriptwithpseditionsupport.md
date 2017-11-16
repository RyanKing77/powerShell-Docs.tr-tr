---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: Galeri, powershell, cmdlet, psget
title: scriptwithpseditionsupport
ms.openlocfilehash: e6994b994cb15903560f3dd89c21383fb2cd367d
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="script-with-compatible-powershell-editions"></a>Komut dosyası ile uyumlu PowerShell sürümleri
Sürüm 5.1’den başlayarak, PowerShell çeşitli özellik kümelerini ve platform uyumluluğunu belirten farklı sürümler halinde sağlanır.

- **Masaüstü Sürümü:** .NET Framework üzerine yapılandırılmıştır ve Windows’un Sunucu Çekirdeği ve Windows Masaüstü gibi tam boyutlu sürümlerinde çalışan PowerShell sürümlerinin hedeflendiği betikler ve modüllerle uyumluluk sağlar.
- **Çekirdek Sürümü:** .NET Core üzerine yapılandırılmıştır ve Windows’un Nano Sunucu ve Windows IoT gibi azaltılmış boyutlu sürümlerinde çalışan PowerShell sürümlerinin hedeflendiği betikler ve modüllerle uyumluluk sağlar.

PowerShell’in çalışan sürümü, $PSVersionTable’ın PSEdition özelliğinde gösterilir.
```powershell
$PSVersionTable

Name                           Value
----                           -----
PSVersion                      5.1.14300.1000
PSEdition                      Desktop
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
CLRVersion                     4.0.30319.42000
BuildVersion                   10.0.14300.1000
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
SerializationVersion           1.1.0.1
```

Betik yazarları, #requires deyiminde PSEdition parametresini kullanarak uyumlu bir PowerShell sürümünde çalıştırılmadıkça betiğin yürütülmesini önleyebilirler.
```powershell
Set-Content C:\script.ps1 -Value "#requires -PSEdition Core
Get-Process -Name PowerShell"
Get-Content C:\script.ps1
#requires -PSEdition Core
Get-Process -Name PowerShell

C:\script.ps1
C:\script.ps1 : The script 'script.ps1' cannot be run because it contained a "#requires" statement for PowerShell Core edition. The edition of PowerShell that is required by the script does not match the currently running PowerShell Desktop edition.
At line:1 char:1
+ C:\script.ps1
+ ~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (script.ps1:String) [], RuntimeException
    + FullyQualifiedErrorId : ScriptRequiresUnmatchedPSEdition
```

PowerShell Galerisi kullanıcıların belirli bir PowerShell sürümünde desteklenen komut listesini bulabilirsiniz.
Komut dosyaları PSEdition_Desktop ve PSEditon_Core olmadan PowerShell Masaüstü sürümlerinde ince çalışmaya olarak kabul edilir.

```powershell

# Find scripts supported on PowerShell Desktop edition
Find-Script -Tag PSEditon_Desktop

# Find scripts supported on PowerShell Core editions
Find-Script -Tag PSEditon_Core

```

## <a name="more-details"></a>Daha fazla ayrıntı
### <a name="modules-with-pseditionsmodulemodulewithpseditionsupportmd"></a>[PSEditions modülleri](../module/modulewithpseditionsupport.md)
### <a name="pseditions-support-on-powershellgallerypsgallerypsgallerypseditionsmd"></a>[PowerShellGallery PSEditions desteği](../../psgallery/psgallery_pseditions.md)

