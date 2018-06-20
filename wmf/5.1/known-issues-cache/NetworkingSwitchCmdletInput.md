---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.topic: conceptual
contributor: vaibch
title: Ağ anahtarı Yöneticisi cmdlet'leri hatası
ms.openlocfilehash: 197a25411a82e5d256a9420706535d5411991f1b
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188692"
---
<span data-ttu-id="58754-103">Ağ anahtarı Yöneticisi cmdlet'leri ağ anahtarları WSMAN yönetmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="58754-103">The Network Switch Manager cmdlets can be used to manage network switches over WSMAN.</span></span>
<span data-ttu-id="58754-104">Bu modülün birkaç cmdlet öğelerini ardışık düzen değerleri kabul özelliğine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="58754-104">A few cmdlets of this module are capable of accepting values from pipelines.</span></span>
<span data-ttu-id="58754-105">WMF 5.1 Önizleme'de, ardışık düzen değerinden kabul edebilir cmdlet'leri değerleri ardışık düzen geçmedi zaman yürütmek başarısız.</span><span class="sxs-lookup"><span data-stu-id="58754-105">In WMF 5.1 Preview, the cmdlets that can accept value from pipeline fail to execute when the values are not passed through pipelines.</span></span>

<span data-ttu-id="58754-106">"InputObject" parametre kullanılmazsa, cmdlet hatasız yürütmek devam etmelidir.</span><span class="sxs-lookup"><span data-stu-id="58754-106">If "InputObject" parameter is not used, the cmdlet should continue to execute without failures.</span></span>

<span data-ttu-id="58754-107">Listenin İşte yani bu cmdlet'leri etkilenen cmdlet'leri düzenindeki "InputObject" parametresi için değer kabul edebilir.</span><span class="sxs-lookup"><span data-stu-id="58754-107">Here is the list of affected cmdlets i.e. these cmdlets can accept value for "InputObject" parameter from pipeline.</span></span>
<span data-ttu-id="58754-108">Bu değer, ardışık düzen tarafından geçmedi cmdlet'inin başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="58754-108">If this value is not passed from pipeline the execution of cmdlet will fail.</span></span>

- <span data-ttu-id="58754-109">NetworkSwitchEthernetPort devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="58754-109">Disable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="58754-110">Enable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="58754-110">Enable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="58754-111">Remove-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="58754-111">Remove-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="58754-112">Set-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="58754-112">Set-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="58754-113">Set-NetworkSwitchPortMode</span><span class="sxs-lookup"><span data-stu-id="58754-113">Set-NetworkSwitchPortMode</span></span>
- <span data-ttu-id="58754-114">Set-NetworkSwitchPortProperty</span><span class="sxs-lookup"><span data-stu-id="58754-114">Set-NetworkSwitchPortProperty</span></span>
- <span data-ttu-id="58754-115">NetworkSwitchFeature devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="58754-115">Disable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="58754-116">Enable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="58754-116">Enable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="58754-117">Remove-NetworkSwitchVlan</span><span class="sxs-lookup"><span data-stu-id="58754-117">Remove-NetworkSwitchVlan</span></span>
- <span data-ttu-id="58754-118">Set-NetworkSwitchVlanProperty</span><span class="sxs-lookup"><span data-stu-id="58754-118">Set-NetworkSwitchVlanProperty</span></span>

### <a name="resolution"></a><span data-ttu-id="58754-119">Çözüm</span><span class="sxs-lookup"><span data-stu-id="58754-119">Resolution</span></span>
<span data-ttu-id="58754-120">Inputobject parametresinin değeri geçirildiğinde içine ardışık düzen üzerinden ince cmdlet'leri iş.</span><span class="sxs-lookup"><span data-stu-id="58754-120">The cmdlets work fine when the value of InputObject parameter are passed into it through pipeline.</span></span> <span data-ttu-id="58754-121">Yukarıdaki cmdlet için iş birkaç örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="58754-121">A few examples that work for the above cmdlets are:</span></span>

- <span data-ttu-id="58754-122">NetworkSwitchEthernetPort devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="58754-122">Disable-NetworkSwitchEthernetPort</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Disable-NetworkSwitchEthernetPort -CimSession $cimSession
```

- <span data-ttu-id="58754-123">Enable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="58754-123">Enable-NetworkSwitchEthernetPort</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Enable-NetworkSwitchEthernetPort -CimSession $cimSession
```

- <span data-ttu-id="58754-124">Remove-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="58754-124">Remove-NetworkSwitchEthernetPortIPAddress</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Remove-NetworkSwitchEthernetPortIPAddress -CimSession $cimSession
```

- <span data-ttu-id="58754-125">Set-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="58754-125">Set-NetworkSwitchEthernetPortIPAddress</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$ipAddress = "192.168.10.1"
$subnetAddress = "255.255.255.0"
$port | Set-NetworkSwitchEthernetPortIPAddress -IpAddress $ipAddress -SubnetAddress $subnetAddress -CimSession $cimSession
```

- <span data-ttu-id="58754-126">Set-NetworkSwitchPortProperty</span><span class="sxs-lookup"><span data-stu-id="58754-126">Set-NetworkSwitchPortProperty</span></span>
```powershell
$portProperties = @{Caption = "New Caption"}
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Set-NetworkSwitchPortProperty -Property $portProperties -CimSession $cimSession
```

- <span data-ttu-id="58754-127">NetworkSwitchFeature devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="58754-127">Disable-NetworkSwitchFeature</span></span>
```powershell
$feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
$feature | Disable-NetworkSwitchFeature -CimSession $cimSession
```

- <span data-ttu-id="58754-128">Enable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="58754-128">Enable-NetworkSwitchFeature</span></span>
```powershell
$feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
$feature | Enable-NetworkSwitchFeature -CimSession $cimSession
```

- <span data-ttu-id="58754-129">Set-NetworkSwitchVlanProperty</span><span class="sxs-lookup"><span data-stu-id="58754-129">Set-NetworkSwitchVlanProperty</span></span>
```powershell
$properties = @{Caption = "New Caption"}
$vlan = Get-CimInstance -ClassName CIM_NetworkVlan -Namespace root/interop -CimSession $cimSession | Select-Object -First 1
$vlan | Set-NetworkSwitchVlanProperty -Property $properties -CimSession $cimSession
```
