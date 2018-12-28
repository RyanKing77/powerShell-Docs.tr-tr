---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Nesne bölümleri seçme nesneyi seçin
ms.assetid: 72e64b1a-d351-4500-9da3-24d8a71d7a92
ms.openlocfilehash: 323c57ba4462e20d9713fb74732989584f5a993f
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53406008"
---
# <a name="selecting-parts-of-objects-select-object"></a>(Select-Object) nesne bölümleri seçme

Kullanabileceğiniz **Select-Object** bunları oluşturmak için kullandığınız nesneleri seçtiğiniz özellikleri içeren yeni, özel Windows PowerShell nesneleri oluşturmak için cmdlet'i. Yalnızca Win32_LogicalDisk WMI sınıf adı ve FreeSpace özelliklerini içeren yeni bir nesne oluşturmak için aşağıdaki komutu yazın:

```
PS> Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace

Name                                    FreeSpace
----                                    ---------
C:                                      50664845312
```

Bu komutu gönderdikten sonra veri türü göremezsiniz ancak Get-Member sonucu Select-Object sonra kanal, yeni türdeki bir nesne bir PSCustomObject sahip olduğunuzu gösterir:

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

Select-Object pek çok kullanımı vardır. Bunlardan biri daha sonra değiştirebilirsiniz veri çoğaltılıyor. Biz, önceki bölümde karşılaştık sorun artık işleyebilir. FreeSpace değerini, yeni oluşturulan nesneleri güncelleştirebilir ve çıkış açıklayıcı bir etiket içerir:

```
Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0; $_}
Name                                                                  FreeSpace
----                                                                  ---------
C:                                                                48317.7265625
```