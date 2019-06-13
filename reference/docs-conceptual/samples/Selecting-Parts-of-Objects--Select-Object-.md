---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Nesne bölümleri seçme nesneyi seçin
ms.openlocfilehash: 4d4c89f0b5103e4701a3af3cd07fcd7c8f1c697f
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030111"
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
