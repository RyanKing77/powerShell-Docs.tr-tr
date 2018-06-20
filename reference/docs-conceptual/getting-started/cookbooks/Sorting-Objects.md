---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Nesne Sıralama
ms.assetid: 8530caa8-3ed4-4c56-aed7-1295dd9ba199
ms.openlocfilehash: 272d550a67b206f9924ebe143eca2f5906c0a304
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30949987"
---
# <a name="sorting-objects"></a>Nesne Sıralama

Biz kullanarak tarama kolaylaştırmak için görüntülenen verileri düzenleyebilirsiniz **Sort-Object** cmdlet'i. **Sort-Object** sıralamak için bir veya daha fazla özellik adını alır ve bu özelliklerin değerlerini tarafından sıralanan veri döndürür.

Win32_SystemDriver örnekleri listeleme sorun göz önünde bulundurun. Sıralanacak istiyorsanız **durumu** ve sonra **adı**, biz bunu yazarak yapabilirsiniz:

```powershell
Get-WmiObject -Class Win32_SystemDriver | Sort-Object -Property State,Name | Format-Table -Property Name,State,Started,DisplayName -AutoSize -Wrap
```

Bu uzun bir görüntü olsa da, bir arada gruplandırılmış durumuyla öğeleri görebilirsiniz:

```output
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