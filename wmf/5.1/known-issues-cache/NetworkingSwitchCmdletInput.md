---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, Kur
contributor: vaibch
title: "Ağ anahtarı Yöneticisi cmdlet'leri hatası"
ms.openlocfilehash: d9fcdedbfc7d0c3f68624ed1db6259e04c3d06d1
ms.sourcegitcommit: fee03bb9802222078c8d5f6c8efb0698024406ed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2017
---
Ağ anahtarı Yöneticisi cmdlet'leri ağ anahtarları WSMAN yönetmek için kullanılabilir. Bu modülün birkaç cmdlet öğelerini ardışık düzen değerleri kabul özelliğine sahiptir. WMF 5.1 Önizleme'de, ardışık düzen değerinden kabul edebilir cmdlet'leri değerleri ardışık düzen geçmedi zaman yürütmek başarısız.

"InputObject" parametre kullanılmazsa, cmdlet hatasız yürütmek devam etmelidir.

Listenin İşte yani bu cmdlet'leri etkilenen cmdlet'leri düzenindeki "InputObject" parametresi için değer kabul edebilir. Bu değer, ardışık düzen tarafından geçmedi cmdlet'inin başarısız olur.

- NetworkSwitchEthernetPort devre dışı bırak
- Enable-NetworkSwitchEthernetPort
- Remove-NetworkSwitchEthernetPortIPAddress
- Set-NetworkSwitchEthernetPortIPAddress
- Set-NetworkSwitchPortMode
- Set-NetworkSwitchPortProperty
- NetworkSwitchFeature devre dışı bırak
- Enable-NetworkSwitchFeature
- Remove-NetworkSwitchVlan
- Set-NetworkSwitchVlanProperty

### <a name="resolution"></a>Çözüm
Inputobject parametresinin değeri geçirildiğinde içine ardışık düzen üzerinden ince cmdlet'leri iş. Yukarıdaki cmdlet için iş birkaç örnek verilmiştir:

- NetworkSwitchEthernetPort devre dışı bırak
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Disable-NetworkSwitchEthernetPort -CimSession $cimSession
```

- Enable-NetworkSwitchEthernetPort
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Enable-NetworkSwitchEthernetPort -CimSession $cimSession
```

- Remove-NetworkSwitchEthernetPortIPAddress
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Remove-NetworkSwitchEthernetPortIPAddress -CimSession $cimSession
```

- Set-NetworkSwitchEthernetPortIPAddress
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$ipAddress = "192.168.10.1"
$subnetAddress = "255.255.255.0"
$port | Set-NetworkSwitchEthernetPortIPAddress -IpAddress $ipAddress -SubnetAddress $subnetAddress -CimSession $cimSession
```

- Set-NetworkSwitchPortProperty
```powershell
$portProperties = @{Caption = "New Caption"}
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Set-NetworkSwitchPortProperty -Property $portProperties -CimSession $cimSession
```

- NetworkSwitchFeature devre dışı bırak
```powershell
$feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
$feature | Disable-NetworkSwitchFeature -CimSession $cimSession
```

- Enable-NetworkSwitchFeature
```powershell
$feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
$feature | Enable-NetworkSwitchFeature -CimSession $cimSession
```

- Set-NetworkSwitchVlanProperty
```powershell
$properties = @{Caption = "New Caption"}
$vlan = Get-CimInstance -ClassName CIM_NetworkVlan -Namespace root/interop -CimSession $cimSession | Select-Object -First 1
$vlan | Set-NetworkSwitchVlanProperty -Property $properties -CimSession $cimSession
```

