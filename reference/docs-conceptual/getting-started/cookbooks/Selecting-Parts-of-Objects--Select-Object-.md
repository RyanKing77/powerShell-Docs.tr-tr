---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: "Nesne nesneleri seçme bölümlerini seçin"
ms.assetid: 72e64b1a-d351-4500-9da3-24d8a71d7a92
ms.openlocfilehash: 8c9633e80f63e1d474c46fa772108aee4f79751d
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2017
---
# <a name="selecting-parts-of-objects-select-object"></a><span data-ttu-id="489d9-103">Nesneler (Select-Object) bölümlerini seçme</span><span class="sxs-lookup"><span data-stu-id="489d9-103">Selecting Parts of Objects (Select-Object)</span></span>
<span data-ttu-id="489d9-104">Kullanabileceğiniz **Select-Object** bunları oluşturmak için kullandığınız nesnelerden seçili özelliklerini içeren yeni, özel Windows PowerShell nesneleri oluşturmak için cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="489d9-104">You can use the **Select-Object** cmdlet to create new, custom Windows PowerShell objects that contain properties selected from the objects you use to create them.</span></span> <span data-ttu-id="489d9-105">Yalnızca ad ve FreeSpace Win32_LogicalDisk WMI sınıfının özelliklerine içeren yeni bir nesne oluşturmak için aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="489d9-105">Type the following command to create a new object that includes only the Name and FreeSpace properties of the Win32_LogicalDisk WMI class:</span></span>

```
PS> Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace

Name                                    FreeSpace
----                                    ---------
C:                                      50664845312
```

<span data-ttu-id="489d9-106">Bu komutu gönderdikten sonra veri türünü göremezsiniz, ancak sonra Select-Object Get-üyenin sonucu kanal varsa, yeni türdeki bir nesne bir PSCustomObject olduğunu anlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="489d9-106">You cannot see the type of data after issuing that command, but if you pipe the result to Get-Member after the Select-Object, you can tell that you have a new type of object, a PSCustomObject:</span></span>

```
PS> Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace| Get-Member

   TypeName: System.Management.Automation.PSCustomObject

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       System.Boolean Equals(Object obj)
GetHashCode Method       System.Int32 GetHashCode()
GetType     Method       System.Type GetType()
ToString    Method       System.String ToString()
FreeSpace   NoteProperty  FreeSpace=...
Name        NoteProperty System.String Name=C:
```

<span data-ttu-id="489d9-107">Select-Object birçok kullanımı vardır.</span><span class="sxs-lookup"><span data-stu-id="489d9-107">Select-Object has many uses.</span></span> <span data-ttu-id="489d9-108">Bunlardan birini daha sonra değiştirebilirsiniz verileri çoğaltılıyor.</span><span class="sxs-lookup"><span data-stu-id="489d9-108">One of them is replicating data that you can then modify.</span></span> <span data-ttu-id="489d9-109">Biz, önceki bölümde karşılaştık sorunu şimdi işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="489d9-109">We can now handle the problem we ran across in the previous section.</span></span> <span data-ttu-id="489d9-110">FreeSpace değerini bizim yeni oluşturulan nesneleri güncelleştirebilir ve çıktı açıklayıcı bir etiket içerir:</span><span class="sxs-lookup"><span data-stu-id="489d9-110">We can update the value of FreeSpace in our newly-created objects and the output will include the descriptive label:</span></span>

```
Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0; $_}
Name                                                                  FreeSpace
----                                                                  ---------
C:                                                                48317.7265625
```

