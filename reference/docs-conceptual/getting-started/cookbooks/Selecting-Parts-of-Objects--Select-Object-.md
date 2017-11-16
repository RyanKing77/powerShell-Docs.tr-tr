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
# <a name="selecting-parts-of-objects-select-object"></a>Nesneler (Select-Object) bölümlerini seçme
Kullanabileceğiniz **Select-Object** bunları oluşturmak için kullandığınız nesnelerden seçili özelliklerini içeren yeni, özel Windows PowerShell nesneleri oluşturmak için cmdlet'i. Yalnızca ad ve FreeSpace Win32_LogicalDisk WMI sınıfının özelliklerine içeren yeni bir nesne oluşturmak için aşağıdaki komutu yazın:

```
PS> Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace

Name                                    FreeSpace
----                                    ---------
C:                                      50664845312
```

Bu komutu gönderdikten sonra veri türünü göremezsiniz, ancak sonra Select-Object Get-üyenin sonucu kanal varsa, yeni türdeki bir nesne bir PSCustomObject olduğunu anlayabilirsiniz:

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

Select-Object birçok kullanımı vardır. Bunlardan birini daha sonra değiştirebilirsiniz verileri çoğaltılıyor. Biz, önceki bölümde karşılaştık sorunu şimdi işleyebilir. FreeSpace değerini bizim yeni oluşturulan nesneleri güncelleştirebilir ve çıktı açıklayıcı bir etiket içerir:

```
Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0; $_}
Name                                                                  FreeSpace
----                                                                  ---------
C:                                                                48317.7265625
```

