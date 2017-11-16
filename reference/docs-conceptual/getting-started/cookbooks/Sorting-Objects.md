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
# <a name="sorting-objects"></a><span data-ttu-id="8845b-103">Sıralama nesneleri</span><span class="sxs-lookup"><span data-stu-id="8845b-103">Sorting Objects</span></span>
<span data-ttu-id="8845b-104">Biz kullanarak tarama kolaylaştırmak için görüntülenen verileri düzenleyebilirsiniz **Sort-Object** cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="8845b-104">We can organize displayed data to make it easier to scan by using the **Sort-Object** cmdlet.</span></span> <span data-ttu-id="8845b-105">**Sort-Object** sıralamak için bir veya daha fazla özellik adını alır ve bu özelliklerin değerlerini tarafından sıralanan veri döndürür.</span><span class="sxs-lookup"><span data-stu-id="8845b-105">**Sort-Object** takes the name of one or more properties to sort on, and returns data sorted by the values of those properties.</span></span>

<span data-ttu-id="8845b-106">Win32_SystemDriver örnekleri listeleme sorun göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="8845b-106">Consider the problem of listing Win32_SystemDriver instances.</span></span> <span data-ttu-id="8845b-107">Sıralanacak istiyorsanız **durumu** ve sonra **adı**, biz bunu yazarak yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8845b-107">If we want to sort by **State** and then by **Name**, we can do it by typing:</span></span>

```
Get-WmiObject -Class Win32_SystemDriver | Sort-Object -Property State,Name | Format-Table -Property Name,State,Started,DisplayName -AutoSize -Wrap
```

<span data-ttu-id="8845b-108">Bu uzun bir görüntü olsa da, bir arada gruplandırılmış durumuyla öğeleri görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8845b-108">Although this is a lengthy display, you can see items with the same state grouped together:</span></span>

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

<span data-ttu-id="8845b-109">Belirterek nesneleri ters sırada sıralayabilirsiniz **azalan** parametresi.</span><span class="sxs-lookup"><span data-stu-id="8845b-109">You can also sort the objects in reverse order by specifying the **Descending** parameter.</span></span> <span data-ttu-id="8845b-110">Bu adları ters alfabetik sıraya göre sıralanır ve sayılar boyutuna göre azalan sırada sıralanır sıralama düzenini tersine çevirir.</span><span class="sxs-lookup"><span data-stu-id="8845b-110">This reverses the sort order so that names are sorted in reverse alphabetical order and numbers are sorted by descending size.</span></span>

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

