---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Nesne nesneleri seçme bölümlerini seçin
ms.assetid: 72e64b1a-d351-4500-9da3-24d8a71d7a92
ms.openlocfilehash: 323c57ba4462e20d9713fb74732989584f5a993f
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
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