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
# <a name="network-switch-manager-cmdlets-failure"></a>Ağ anahtarı Yöneticisi cmdlet'leri hatası

Ağ anahtarı Yöneticisi cmdlet'leri, ağ anahtarlarını WSMAN yönetmek için kullanılabilir.
Bu modül bazı cmdlet'lerin işlem hatları değerlerini kabul özelliğine sahiptir.
WMF 5.1 Önizleme'de, işlem hattından değeri kabul edebilirsiniz cmdlet'ler değerleri komut zincirleriyle geçirilmediğinde yürütülmesi başarısız.

"InputObject" parametre kullanılmazsa, cmdlet hatasız yürütülecek devam etmelidir.

Aşağıda verilmiştir yani bu cmdlet'ler etkilenen cmdlet'ler işlem hattından "InputObject" parametresi için değer kabul edebilir.
Bu değer, ardışık düzen tarafından geçirilmediğine cmdlet'inin başarısız olur.

- NetworkSwitchEthernetPort devre dışı bırak
- NetworkSwitchEthernetPort etkinleştir
- Remove-NetworkSwitchEthernetPortIPAddress
- Set-NetworkSwitchEthernetPortIPAddress
- Set-NetworkSwitchPortMode
- Set-NetworkSwitchPortProperty
- NetworkSwitchFeature devre dışı bırak
- NetworkSwitchFeature etkinleştir
- Remove-NetworkSwitchVlan
- Set-NetworkSwitchVlanProperty

## <a name="resolution"></a>Çözüm

Inputobject parametresinin değeri geçirilir, içine işlem hattı iyi cmdlet'leri iş. Yukarıdaki cmdlet'lerinden için çalışan bazı örnekler şunlardır:

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