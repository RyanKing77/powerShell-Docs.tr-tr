---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Bir görev için birden çok nesne ForEach nesnesi yinelenen
ms.assetid: 6697a12d-2470-4ed6-b5bb-c35e5d525eb6
ms.openlocfilehash: 8b8002af3ade0905421760ce29cdc84b084236e9
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="repeating-a-task-for-multiple-objects-foreach-object"></a><span data-ttu-id="b902c-103">Birden çok nesne (ForEach-Object) için bir görev yinelenen</span><span class="sxs-lookup"><span data-stu-id="b902c-103">Repeating a Task for Multiple Objects (ForEach-Object)</span></span>

<span data-ttu-id="b902c-104">**ForEach-Object** ardışık her nesne üzerinde bir komut çalıştırmak olanak cmdlet kullanır komut dosyası blokları ve geçerli ardışık düzen nesne $_ tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="b902c-104">The **ForEach-Object** cmdlet uses script blocks and the $_ descriptor for the current pipeline object to let you run a command on each object in the pipeline.</span></span> <span data-ttu-id="b902c-105">Bu karmaşık bazı görevleri gerçekleştirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b902c-105">This can be used to perform some complicated tasks.</span></span>

<span data-ttu-id="b902c-106">Burada bu yararlı olabilir bir durum daha kullanışlı hale getirmek için veri düzenleme.</span><span class="sxs-lookup"><span data-stu-id="b902c-106">One situation where this can be useful is manipulating data to make it more useful.</span></span> <span data-ttu-id="b902c-107">Örneğin, WMI Win32_LogicalDisk sınıfından yerel her disk için boş alan bilgileri döndürmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b902c-107">For example, the Win32_LogicalDisk class from WMI can be used to return free space information for each local disk.</span></span> <span data-ttu-id="b902c-108">Veri bayt cinsinden, ancak okunması zor hale getiren verilir:</span><span class="sxs-lookup"><span data-stu-id="b902c-108">The data is returned in terms of bytes, however, which makes it difficult to read:</span></span>

```
PS> Get-WmiObject -Class Win32_LogicalDisk

DeviceID     : C:
DriveType    : 3
ProviderName :
FreeSpace    : 50665070592
Size         : 203912880128
VolumeName   : Local Disk
```

<span data-ttu-id="b902c-109">Her değer 1024 tarafından iki kez bölerek biz FreeSpace değerini megabayt dönüştürebilirsiniz; İlk bölüm sonra verileri kilobayt cinsinden ve isteğe bağlı olarak ikinci ayırmadan sonra megabayt şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b902c-109">We can convert the FreeSpace value to megabytes by dividing each value by 1024 twice; after the first division, the data is in kilobytes, and after the second division it is megabytes.</span></span> <span data-ttu-id="b902c-110">Bunu ForEach-Object betik bloğu içinde yazarak yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b902c-110">You can do that in a ForEach-Object script block by typing:</span></span>

```
PS> Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {($_.FreeSpace)/1024.0/1024.0}
48318.01171875
```

<span data-ttu-id="b902c-111">Ne yazık ki, çıktı verileri ilişkili hiçbir etiketle sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="b902c-111">Unfortunately, the output is now data with no associated label.</span></span> <span data-ttu-id="b902c-112">Bu gibi WMI özellikleri salt okunur olduğundan, doğrudan FreeSpace dönüştürülemiyor.</span><span class="sxs-lookup"><span data-stu-id="b902c-112">Because WMI properties such as this are read-only, you cannot directly convert FreeSpace.</span></span> <span data-ttu-id="b902c-113">Bu yazarsanız:</span><span class="sxs-lookup"><span data-stu-id="b902c-113">If you type this:</span></span>

```powershell
Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0}
```

<span data-ttu-id="b902c-114">Bir hata iletisi alırsınız:</span><span class="sxs-lookup"><span data-stu-id="b902c-114">You get an error message:</span></span>

```output
"FreeSpace" is a ReadOnly property.
At line:1 char:70
+ Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {$_.F <<<< r
eeSpace = ($_.FreeSpace)/1024.0/1024.0}
```

<span data-ttu-id="b902c-115">Bazı gelişmiş teknikleri kullanarak veriyi yeniden düzenlemek, ancak kullanarak yeni bir nesne oluşturmak için basit bir yaklaşım olan **Select-Object**.</span><span class="sxs-lookup"><span data-stu-id="b902c-115">You could reorganize the data by using some advanced techniques, but a simpler approach is to create a new object, by using **Select-Object**.</span></span>