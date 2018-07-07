---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.topic: conceptual
contributor: vaibch
title: Ağ anahtarı Yöneticisi cmdlet'leri hatası
ms.openlocfilehash: a0f84c35974b6674faba4b0f19a28bd6e2490a96
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893163"
---
# <a name="network-switch-manager-cmdlets-failure"></a><span data-ttu-id="47925-103">Ağ anahtarı Yöneticisi cmdlet'leri hatası</span><span class="sxs-lookup"><span data-stu-id="47925-103">Network Switch Manager Cmdlets Failure</span></span>

<span data-ttu-id="47925-104">Ağ anahtarı Yöneticisi cmdlet'leri, ağ anahtarlarını WSMAN yönetmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="47925-104">The Network Switch Manager cmdlets can be used to manage network switches over WSMAN.</span></span>
<span data-ttu-id="47925-105">Bu modül bazı cmdlet'lerin işlem hatları değerlerini kabul özelliğine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="47925-105">A few cmdlets of this module are capable of accepting values from pipelines.</span></span>
<span data-ttu-id="47925-106">WMF 5.1 Önizleme'de, işlem hattından değeri kabul edebilirsiniz cmdlet'ler değerleri komut zincirleriyle geçirilmediğinde yürütülmesi başarısız.</span><span class="sxs-lookup"><span data-stu-id="47925-106">In WMF 5.1 Preview, the cmdlets that can accept value from pipeline fail to execute when the values are not passed through pipelines.</span></span>

<span data-ttu-id="47925-107">"InputObject" parametre kullanılmazsa, cmdlet hatasız yürütülecek devam etmelidir.</span><span class="sxs-lookup"><span data-stu-id="47925-107">If "InputObject" parameter is not used, the cmdlet should continue to execute without failures.</span></span>

<span data-ttu-id="47925-108">Aşağıda verilmiştir yani bu cmdlet'ler etkilenen cmdlet'ler işlem hattından "InputObject" parametresi için değer kabul edebilir.</span><span class="sxs-lookup"><span data-stu-id="47925-108">Here is the list of affected cmdlets i.e. these cmdlets can accept value for "InputObject" parameter from pipeline.</span></span>
<span data-ttu-id="47925-109">Bu değer, ardışık düzen tarafından geçirilmediğine cmdlet'inin başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="47925-109">If this value is not passed from pipeline the execution of cmdlet will fail.</span></span>

- <span data-ttu-id="47925-110">NetworkSwitchEthernetPort devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="47925-110">Disable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="47925-111">NetworkSwitchEthernetPort etkinleştir</span><span class="sxs-lookup"><span data-stu-id="47925-111">Enable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="47925-112">Remove-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="47925-112">Remove-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="47925-113">Set-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="47925-113">Set-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="47925-114">Set-NetworkSwitchPortMode</span><span class="sxs-lookup"><span data-stu-id="47925-114">Set-NetworkSwitchPortMode</span></span>
- <span data-ttu-id="47925-115">Set-NetworkSwitchPortProperty</span><span class="sxs-lookup"><span data-stu-id="47925-115">Set-NetworkSwitchPortProperty</span></span>
- <span data-ttu-id="47925-116">NetworkSwitchFeature devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="47925-116">Disable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="47925-117">NetworkSwitchFeature etkinleştir</span><span class="sxs-lookup"><span data-stu-id="47925-117">Enable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="47925-118">Remove-NetworkSwitchVlan</span><span class="sxs-lookup"><span data-stu-id="47925-118">Remove-NetworkSwitchVlan</span></span>
- <span data-ttu-id="47925-119">Set-NetworkSwitchVlanProperty</span><span class="sxs-lookup"><span data-stu-id="47925-119">Set-NetworkSwitchVlanProperty</span></span>

## <a name="resolution"></a><span data-ttu-id="47925-120">Çözüm</span><span class="sxs-lookup"><span data-stu-id="47925-120">Resolution</span></span>

<span data-ttu-id="47925-121">Inputobject parametresinin değeri geçirilir, içine işlem hattı iyi cmdlet'leri iş.</span><span class="sxs-lookup"><span data-stu-id="47925-121">The cmdlets work fine when the value of InputObject parameter are passed into it through pipeline.</span></span> <span data-ttu-id="47925-122">Yukarıdaki cmdlet'lerinden için çalışan bazı örnekler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="47925-122">A few examples that work for the above cmdlets are:</span></span>

- `Disable-NetworkSwitchEthernetPort`

  ```powershell
  $port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
  $port | Disable-NetworkSwitchEthernetPort -CimSession $cimSession
  ```

- `Enable-NetworkSwitchEthernetPort`

  ```powershell
  $port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
  $port | Enable-NetworkSwitchEthernetPort -CimSession $cimSession
  ```

- `Remove-NetworkSwitchEthernetPortIPAddress`

  ```powershell
  $port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
  $port | Remove-NetworkSwitchEthernetPortIPAddress -CimSession $cimSession
  ```

- `Set-NetworkSwitchEthernetPortIPAddress`

  ```powershell
  $port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
  $ipAddress = "192.168.10.1"
  $subnetAddress = "255.255.255.0"
  $port | Set-NetworkSwitchEthernetPortIPAddress -IpAddress $ipAddress -SubnetAddress $subnetAddress -CimSession $cimSession
  ```

- `Set-NetworkSwitchPortProperty`

  ```powershell
  $portProperties = @{Caption = "New Caption"}
  $port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
  $port | Set-NetworkSwitchPortProperty -Property $portProperties -CimSession $cimSession
  ```

- `Disable-NetworkSwitchFeature`

  ```powershell
  $feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
  $feature | Disable-NetworkSwitchFeature -CimSession $cimSession
  ```

- `Enable-NetworkSwitchFeature`

  ```powershell
  $feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
  $feature | Enable-NetworkSwitchFeature -CimSession $cimSession
  ```

- `Set-NetworkSwitchVlanProperty`

  ```powershell
  $properties = @{Caption = "New Caption"}
  $vlan = Get-CimInstance -ClassName CIM_NetworkVlan -Namespace root/interop -CimSession $cimSession | Select-Object -First 1
  $vlan | Set-NetworkSwitchVlanProperty -Property $properties -CimSession $cimSession
  ```