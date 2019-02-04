---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Nesne bölümleri seçme nesneyi seçin
ms.assetid: 72e64b1a-d351-4500-9da3-24d8a71d7a92
ms.openlocfilehash: 323c57ba4462e20d9713fb74732989584f5a993f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684517"
---
# <a name="selecting-parts-of-objects-select-object"></a><span data-ttu-id="c629e-103">(Select-Object) nesne bölümleri seçme</span><span class="sxs-lookup"><span data-stu-id="c629e-103">Selecting Parts of Objects (Select-Object)</span></span>

<span data-ttu-id="c629e-104">Kullanabileceğiniz **Select-Object** bunları oluşturmak için kullandığınız nesneleri seçtiğiniz özellikleri içeren yeni, özel Windows PowerShell nesneleri oluşturmak için cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="c629e-104">You can use the **Select-Object** cmdlet to create new, custom Windows PowerShell objects that contain properties selected from the objects you use to create them.</span></span> <span data-ttu-id="c629e-105">Yalnızca Win32_LogicalDisk WMI sınıf adı ve FreeSpace özelliklerini içeren yeni bir nesne oluşturmak için aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="c629e-105">Type the following command to create a new object that includes only the Name and FreeSpace properties of the Win32_LogicalDisk WMI class:</span></span>

```
PS> Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace

Name                                    FreeSpace
----                                    ---------
C:                                      50664845312
```

<span data-ttu-id="c629e-106">Bu komutu gönderdikten sonra veri türü göremezsiniz ancak Get-Member sonucu Select-Object sonra kanal, yeni türdeki bir nesne bir PSCustomObject sahip olduğunuzu gösterir:</span><span class="sxs-lookup"><span data-stu-id="c629e-106">You cannot see the type of data after issuing that command, but if you pipe the result to Get-Member after the Select-Object, you can tell that you have a new type of object, a PSCustomObject:</span></span>

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

<span data-ttu-id="c629e-107">Select-Object pek çok kullanımı vardır.</span><span class="sxs-lookup"><span data-stu-id="c629e-107">Select-Object has many uses.</span></span> <span data-ttu-id="c629e-108">Bunlardan biri daha sonra değiştirebilirsiniz veri çoğaltılıyor.</span><span class="sxs-lookup"><span data-stu-id="c629e-108">One of them is replicating data that you can then modify.</span></span> <span data-ttu-id="c629e-109">Biz, önceki bölümde karşılaştık sorun artık işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="c629e-109">We can now handle the problem we ran across in the previous section.</span></span> <span data-ttu-id="c629e-110">FreeSpace değerini, yeni oluşturulan nesneleri güncelleştirebilir ve çıkış açıklayıcı bir etiket içerir:</span><span class="sxs-lookup"><span data-stu-id="c629e-110">We can update the value of FreeSpace in our newly-created objects and the output will include the descriptive label:</span></span>

```
Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0; $_}
Name                                                                  FreeSpace
----                                                                  ---------
C:                                                                48317.7265625
```