---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Birden çok nesne ForEach nesne için bir görevi tekrarlama
ms.assetid: 6697a12d-2470-4ed6-b5bb-c35e5d525eb6
ms.openlocfilehash: 64d85edad4a6931b2376b95b6d1f5b4d5194399f
ms.sourcegitcommit: 01ac77cd0b00e4e5e964504563a9212e8002e5e0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/07/2018
ms.locfileid: "39587270"
---
# <a name="repeating-a-task-for-multiple-objects-foreach-object"></a><span data-ttu-id="ffca4-103">Bir görevi tekrarlama (ForEach-Object) birden çok nesne için</span><span class="sxs-lookup"><span data-stu-id="ffca4-103">Repeating a Task for Multiple Objects (ForEach-Object)</span></span>

<span data-ttu-id="ffca4-104">**ForEach-Object** komut dosyası blokları cmdlet'ini kullanır ve `$_` işlem hattındaki her bir nesne üzerinde bir komut çalıştırın izin vermek geçerli işlem hattı nesne tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="ffca4-104">The **ForEach-Object** cmdlet uses script blocks and the `$_` descriptor for the current pipeline object to let you run a command on each object in the pipeline.</span></span> <span data-ttu-id="ffca4-105">Bu, karmaşık bazı görevleri gerçekleştirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ffca4-105">This can be used to perform some complicated tasks.</span></span>

<span data-ttu-id="ffca4-106">Bir durum burada bu yararlı olabilir, daha kullanışlı hale getirmek için veri işleme.</span><span class="sxs-lookup"><span data-stu-id="ffca4-106">One situation where this can be useful is manipulating data to make it more useful.</span></span> <span data-ttu-id="ffca4-107">Örneğin, WMI Win32_LogicalDisk sınıfı yerel her disk için boş alan bilgileri döndürmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ffca4-107">For example, the Win32_LogicalDisk class from WMI can be used to return free space information for each local disk.</span></span> <span data-ttu-id="ffca4-108">Verilerin bayt cinsinden, ancak okunması zor hale getiren döndürülür:</span><span class="sxs-lookup"><span data-stu-id="ffca4-108">The data is returned in terms of bytes, however, which makes it difficult to read:</span></span>

```
PS> Get-WmiObject -Class Win32_LogicalDisk

DeviceID     : C:
DriveType    : 3
ProviderName :
FreeSpace    : 50665070592
Size         : 203912880128
VolumeName   : Local Disk
```

<span data-ttu-id="ffca4-109">Her bir değeri 1024 iki kez bölerek biz FreeSpace değerini megabayt dönüştürebilirsiniz; İlk bölüm sonra verileri kilobayttır ve isteğe bağlı olarak ikinci bölme işleminden megabayt gelir.</span><span class="sxs-lookup"><span data-stu-id="ffca4-109">We can convert the FreeSpace value to megabytes by dividing each value by 1024 twice; after the first division, the data is in kilobytes, and after the second division it is megabytes.</span></span> <span data-ttu-id="ffca4-110">Bir ForEach-Object betik bloğu içinde yazarak bunu yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ffca4-110">You can do that in a ForEach-Object script block by typing:</span></span>

```
PS> Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {($_.FreeSpace)/1024.0/1024.0}
48318.01171875
```

<span data-ttu-id="ffca4-111">Ne yazık ki, çıkış verilerle ilişkili hiçbir etiket sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="ffca4-111">Unfortunately, the output is now data with no associated label.</span></span> <span data-ttu-id="ffca4-112">Bunun gibi WMI özellikleri salt okunur olduğundan, doğrudan FreeSpace dönüştürülemiyor.</span><span class="sxs-lookup"><span data-stu-id="ffca4-112">Because WMI properties such as this are read-only, you cannot directly convert FreeSpace.</span></span> <span data-ttu-id="ffca4-113">Bu türü:</span><span class="sxs-lookup"><span data-stu-id="ffca4-113">If you type this:</span></span>

```powershell
Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0}
```

<span data-ttu-id="ffca4-114">Bir hata iletisi olursunuz:</span><span class="sxs-lookup"><span data-stu-id="ffca4-114">You get an error message:</span></span>

```output
"FreeSpace" is a ReadOnly property.
At line:1 char:70
+ Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {$_.F <<<< r
eeSpace = ($_.FreeSpace)/1024.0/1024.0}
```

<span data-ttu-id="ffca4-115">Bazı gelişmiş teknikleri kullanarak verileri yeniden düzenleme, ancak basit bir yaklaşım kullanarak yeni bir nesne oluşturmak için olan **Select-Object**.</span><span class="sxs-lookup"><span data-stu-id="ffca4-115">You could reorganize the data by using some advanced techniques, but a simpler approach is to create a new object, by using **Select-Object**.</span></span>