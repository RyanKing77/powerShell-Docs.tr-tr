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
# <a name="sorting-objects"></a><span data-ttu-id="37a47-103">Nesne Sıralama</span><span class="sxs-lookup"><span data-stu-id="37a47-103">Sorting Objects</span></span>

<span data-ttu-id="37a47-104">Biz kullanarak tarama kolaylaştırmak için görüntülenen verileri düzenleyebilirsiniz **Sort-Object** cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="37a47-104">We can organize displayed data to make it easier to scan by using the **Sort-Object** cmdlet.</span></span> <span data-ttu-id="37a47-105">**Sort-Object** sıralamak için bir veya daha fazla özellik adını alır ve bu özelliklerin değerlerini tarafından sıralanan veri döndürür.</span><span class="sxs-lookup"><span data-stu-id="37a47-105">**Sort-Object** takes the name of one or more properties to sort on, and returns data sorted by the values of those properties.</span></span>

<span data-ttu-id="37a47-106">Win32_SystemDriver örnekleri listeleme sorun göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="37a47-106">Consider the problem of listing Win32_SystemDriver instances.</span></span> <span data-ttu-id="37a47-107">Sıralanacak istiyorsanız **durumu** ve sonra **adı**, biz bunu yazarak yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="37a47-107">If we want to sort by **State** and then by **Name**, we can do it by typing:</span></span>

```powershell
Get-WmiObject -Class Win32_SystemDriver | Sort-Object -Property State,Name | Format-Table -Property Name,State,Started,DisplayName -AutoSize -Wrap
```

<span data-ttu-id="37a47-108">Bu uzun bir görüntü olsa da, bir arada gruplandırılmış durumuyla öğeleri görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="37a47-108">Although this is a lengthy display, you can see items with the same state grouped together:</span></span>

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

<span data-ttu-id="37a47-109">Belirterek nesneleri ters sırada sıralayabilirsiniz **azalan** parametresi.</span><span class="sxs-lookup"><span data-stu-id="37a47-109">You can also sort the objects in reverse order by specifying the **Descending** parameter.</span></span> <span data-ttu-id="37a47-110">Bu adları ters alfabetik sıraya göre sıralanır ve sayılar boyutuna göre azalan sırada sıralanır sıralama düzenini tersine çevirir.</span><span class="sxs-lookup"><span data-stu-id="37a47-110">This reverses the sort order so that names are sorted in reverse alphabetical order and numbers are sorted by descending size.</span></span>

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