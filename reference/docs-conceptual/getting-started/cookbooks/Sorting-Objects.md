---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: "Sıralama nesneleri"
ms.assetid: 8530caa8-3ed4-4c56-aed7-1295dd9ba199
ms.openlocfilehash: 2df45c64656e74dc8b72957ce59f2a5e5ee663b6
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2017
---
# <a name="sorting-objects"></a>Sıralama nesneleri
Biz kullanarak tarama kolaylaştırmak için görüntülenen verileri düzenleyebilirsiniz **Sort-Object** cmdlet'i. **Sort-Object** sıralamak için bir veya daha fazla özellik adını alır ve bu özelliklerin değerlerini tarafından sıralanan veri döndürür.

Win32_SystemDriver örnekleri listeleme sorun göz önünde bulundurun. Sıralanacak istiyorsanız **durumu** ve sonra **adı**, biz bunu yazarak yapabilirsiniz:

```
Get-WmiObject -Class Win32_SystemDriver | Sort-Object -Property State,Name | Format-Table -Property Name,State,Started,DisplayName -AutoSize -Wrap
```

Bu uzun bir görüntü olsa da, bir arada gruplandırılmış durumuyla öğeleri görebilirsiniz:

```
Name           State   Started DisplayName
----           -----   ------- -----------
ACPI           Running    True Microsoft ACPI Driver
AFD            Running    True AFD
AmdK7          Running    True AMD K7 Processor Driver
AsyncMac       Running    True RAS Asynchronous Media Driver
...
Abiosdsk       Stopped   False Abiosdsk
ACPIEC         Stopped   False ACPIEC
aec            Stopped   False Microsoft Kernel Acoustic Echo Canceller
...
```

Belirterek nesneleri ters sırada sıralayabilirsiniz **azalan** parametresi. Bu adları ters alfabetik sıraya göre sıralanır ve sayılar boyutuna göre azalan sırada sıralanır sıralama düzenini tersine çevirir.

```
PS> Get-WmiObject -Class Win32_SystemDriver | Sort-Object -Property State,Name -Descending | Format-Table -Property Name,State,Started,DisplayName -AutoSize -Wrap

Name           State   Started DisplayName
----           -----   ------- -----------
WS2IFSL        Stopped   False Windows Socket 2.0 Non-IFS Service Provider Supp
                               ort Environment
wceusbsh       Stopped   False Windows CE USB Serial Host Driver...
...
wdmaud         Running    True Microsoft WINMM WDM Audio Compatibility Driver
Wanarp         Running    True Remote Access IP ARP Driver
...
```

