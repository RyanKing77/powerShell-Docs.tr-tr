---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Birden çok nesne ForEach nesne için bir görevi tekrarlama
ms.openlocfilehash: 1442507c4213476f65df3401c1021f8d0fc31956
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030809"
---
# <a name="repeating-a-task-for-multiple-objects-foreach-object"></a>Bir görevi tekrarlama (ForEach-Object) birden çok nesne için

**ForEach-Object** komut dosyası blokları cmdlet'ini kullanır ve `$_` işlem hattındaki her bir nesne üzerinde bir komut çalıştırın izin vermek geçerli işlem hattı nesne tanımlayıcısı. Bu, karmaşık bazı görevleri gerçekleştirmek için kullanılabilir.

Bir durum burada bu yararlı olabilir, daha kullanışlı hale getirmek için veri işleme. Örneğin, WMI Win32_LogicalDisk sınıfı yerel her disk için boş alan bilgileri döndürmek için kullanılabilir. Verilerin bayt cinsinden, ancak okunması zor hale getiren döndürülür:

```
PS> Get-WmiObject -Class Win32_LogicalDisk

DeviceID     : C:
DriveType    : 3
ProviderName :
FreeSpace    : 50665070592
Size         : 203912880128
VolumeName   : Local Disk
```

Her bir değeri 1024 iki kez bölerek biz FreeSpace değerini megabayt dönüştürebilirsiniz; İlk bölüm sonra verileri kilobayttır ve isteğe bağlı olarak ikinci bölme işleminden megabayt gelir. Bir ForEach-Object betik bloğu içinde yazarak bunu yapabilirsiniz:

```
PS> Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {($_.FreeSpace)/1024.0/1024.0}
48318.01171875
```

Ne yazık ki, çıkış verilerle ilişkili hiçbir etiket sunulmuştur. Bunun gibi WMI özellikleri salt okunur olduğundan, doğrudan FreeSpace dönüştürülemiyor. Bu türü:

```powershell
Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0}
```

Bir hata iletisi olursunuz:

```output
"FreeSpace" is a ReadOnly property.
At line:1 char:70
+ Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {$_.F <<<< r
eeSpace = ($_.FreeSpace)/1024.0/1024.0}
```

Bazı gelişmiş teknikleri kullanarak verileri yeniden düzenleme, ancak basit bir yaklaşım kullanarak yeni bir nesne oluşturmak için olan **Select-Object**.
