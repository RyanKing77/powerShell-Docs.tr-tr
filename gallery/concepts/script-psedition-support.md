---
ms.date: 06/12/2017
contributor: manikb
keywords: Galeri, powershell, cmdlet, psget
title: Komut dosyası ile uyumlu PowerShell sürümleri
ms.openlocfilehash: 0ab655ff1c5dd0f48ec41a16ad394251b6c70748
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/26/2018
ms.locfileid: "39267822"
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

Betik yazarları, bir komut dosyası PowerShell PSEdition parametresini kullanarak uyumlu bir sürümü üzerinde çalıştırmadıkça yürütülmesini engelleyebilir bir `#requires` deyimi.

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

PowerShell Galerisi kullanıcılar, belirli bir PowerShell sürümünde desteklenen betikler listesini bulabilirsiniz.
Betikleri PSEdition_Desktop ve PSEditon_Core olmadan PowerShell Masaüstü sürümleri için üzerinde sorunsuz çalışacak şekilde değerlendirilir.

```powershell
# Find scripts supported on PowerShell Desktop edition
Find-Script -Tag PSEditon_Desktop

# Find scripts supported on PowerShell Core editions
Find-Script -Tag PSEditon_Core
```

## <a name="more-details"></a>Daha fazla ayrıntı

- [PSEditions’ı olan Modüller](module-psedition-support.md)
- [PowerShellGallery pseditions'ı desteği](../how-to/finding-items/searching-by-psedition.md)