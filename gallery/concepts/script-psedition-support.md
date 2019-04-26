---
ms.date: 06/12/2017
contributor: manikb
keywords: Galeri, powershell, cmdlet, psget
title: Komut dosyası ile uyumlu PowerShell sürümleri
ms.openlocfilehash: e364879f611429a8583e550fb7704431e456fbb1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084700"
---
# <a name="script-with-compatible-powershell-editions"></a><span data-ttu-id="c0cf4-103">Komut dosyası ile uyumlu PowerShell sürümleri</span><span class="sxs-lookup"><span data-stu-id="c0cf4-103">Script with compatible PowerShell editions</span></span>

<span data-ttu-id="c0cf4-104">Sürüm 5.1’den başlayarak, PowerShell çeşitli özellik kümelerini ve platform uyumluluğunu belirten farklı sürümler halinde sağlanır.</span><span class="sxs-lookup"><span data-stu-id="c0cf4-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="c0cf4-105">**Masaüstü sürümü:** .NET Framework üzerine inşa edilmiş ve Windows Masaüstü ve Windows Server Core gibi tam boyutlu sürümlerinde çalışan PowerShell sürümlerinin hedeflendiği betikler ve modüllerle uyumluluk sağlar.</span><span class="sxs-lookup"><span data-stu-id="c0cf4-105">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>

- <span data-ttu-id="c0cf4-106">**Çekirdek sürümü:** .NET Core üzerine yapılandırılan ve Nano Server gibi Windows ve Windows IOT azaltılmış boyutlu sürümlerinde çalışan PowerShell sürümlerinin hedeflendiği betikler ve modüllerle uyumluluk sağlar.</span><span class="sxs-lookup"><span data-stu-id="c0cf4-106">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

<span data-ttu-id="c0cf4-107">PowerShell’in çalışan sürümü, $PSVersionTable’ın PSEdition özelliğinde gösterilir.</span><span class="sxs-lookup"><span data-stu-id="c0cf4-107">The running edition of PowerShell is shown in the PSEdition property of $PSVersionTable.</span></span>

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

<span data-ttu-id="c0cf4-108">Betik yazarları, bir komut dosyası PowerShell PSEdition parametresini kullanarak uyumlu bir sürümü üzerinde çalıştırmadıkça yürütülmesini engelleyebilir bir `#requires` deyimi.</span><span class="sxs-lookup"><span data-stu-id="c0cf4-108">Script authors can prevent a script from executing unless it is run on a compatible edition of PowerShell using the PSEdition parameter on a `#requires` statement.</span></span>

```powershell
Set-Content C:\script.ps1 -Value "#requires -PSEdition Core
Get-Process -Name PowerShell"
Get-Content C:\script.ps1
#requires -PSEdition Core
Get-Process -Name PowerShell

C:\script.ps1
C:\script.ps1 : The script 'script.ps1' cannot be run because it contained a "#requires" statement for PowerShell editions 'Core'. The edition of PowerShell that is required by the script does not match the currently running PowerShell Desktop edition.
At line:1 char:1
+ C:\script.ps1
+ ~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (script.ps1:String) [], RuntimeException
    + FullyQualifiedErrorId : ScriptRequiresUnmatchedPSEdition
```

<span data-ttu-id="c0cf4-109">PowerShell Galerisi kullanıcılar, belirli bir PowerShell sürümünde desteklenen betikler listesini bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c0cf4-109">PowerShell Gallery users can find the list of scripts supported on a specific PowerShell Edition.</span></span>
<span data-ttu-id="c0cf4-110">PowerShell masaüstü sürümünde düzgün çalışması için betikler PSEdition_Desktop ve PSEdition_Core etiketi olmayan olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="c0cf4-110">Scripts without PSEdition_Desktop and PSEdition_Core tags are considered to work fine on PowerShell Desktop edition.</span></span>

```powershell
# Find scripts supported on PowerShell Desktop edition
Find-Script -Tag PSEdition_Desktop

# Find scripts supported on PowerShell Core edition
Find-Script -Tag PSEdition_Core
```

## <a name="more-details"></a><span data-ttu-id="c0cf4-111">Daha fazla ayrıntı</span><span class="sxs-lookup"><span data-stu-id="c0cf4-111">More details</span></span>

- [<span data-ttu-id="c0cf4-112">PSEditions’ı olan Modüller</span><span class="sxs-lookup"><span data-stu-id="c0cf4-112">Modules with PSEditions</span></span>](module-psedition-support.md)
- [<span data-ttu-id="c0cf4-113">PowerShellGallery pseditions'ı desteği</span><span class="sxs-lookup"><span data-stu-id="c0cf4-113">PSEditions support on PowerShellGallery</span></span>](../how-to/finding-packages/searching-by-compatibility.md)
