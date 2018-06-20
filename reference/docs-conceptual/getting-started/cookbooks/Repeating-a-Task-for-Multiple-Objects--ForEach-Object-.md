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
ms.locfileid: "30954288"
---
# <a name="repeating-a-task-for-multiple-objects-foreach-object"></a>Birden çok nesne (ForEach-Object) için bir görev yinelenen

**ForEach-Object** ardışık her nesne üzerinde bir komut çalıştırmak olanak cmdlet kullanır komut dosyası blokları ve geçerli ardışık düzen nesne $_ tanımlayıcısı. Bu karmaşık bazı görevleri gerçekleştirmek için kullanılabilir.

Burada bu yararlı olabilir bir durum daha kullanışlı hale getirmek için veri düzenleme. Örneğin, WMI Win32_LogicalDisk sınıfından yerel her disk için boş alan bilgileri döndürmek için kullanılabilir. Veri bayt cinsinden, ancak okunması zor hale getiren verilir:

```
PS> Get-WmiObject -Class Win32_LogicalDisk

DeviceID     : C:
DriveType    : 3
ProviderName :
FreeSpace    : 50665070592
Size         : 203912880128
VolumeName   : Local Disk
```

Her değer 1024 tarafından iki kez bölerek biz FreeSpace değerini megabayt dönüştürebilirsiniz; İlk bölüm sonra verileri kilobayt cinsinden ve isteğe bağlı olarak ikinci ayırmadan sonra megabayt şeklindedir. Bunu ForEach-Object betik bloğu içinde yazarak yapabilirsiniz:

```
PS> Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {($_.FreeSpace)/1024.0/1024.0}
48318.01171875
```

Ne yazık ki, çıktı verileri ilişkili hiçbir etiketle sunulmuştur. Bu gibi WMI özellikleri salt okunur olduğundan, doğrudan FreeSpace dönüştürülemiyor. Bu yazarsanız:

```powershell
Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0}
```

Bir hata iletisi alırsınız:

```output
"FreeSpace" is a ReadOnly property.
At line:1 char:70
+ Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {$_.F <<<< r
eeSpace = ($_.FreeSpace)/1024.0/1024.0}
```

Bazı gelişmiş teknikleri kullanarak veriyi yeniden düzenlemek, ancak kullanarak yeni bir nesne oluşturmak için basit bir yaklaşım olan **Select-Object**.