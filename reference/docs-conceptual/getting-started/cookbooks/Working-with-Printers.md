---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Yazıcılar ile Çalışma
ms.assetid: 4f29ead3-f83b-4706-ac3e-f2154ff38dc5
ms.openlocfilehash: 5638629fdf79371c8eff9ee9194b642034250fff
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30954509"
---
# <a name="working-with-printers"></a>Yazıcılar ile Çalışma

WMI ve WSH WScript.Network COM nesnesinden kullanarak yazıcıları yönetmek için Windows PowerShell'i kullanabilirsiniz. Belirli görevleri göstermek için her iki araçları bir karışımını kullanacağız.

### <a name="listing-printer-connections"></a>Yazıcı bağlantılarını listeleme

Bir bilgisayarda yüklü yazıcılar listesinde en basit yolu WMI kullanmaktır **Win32_Printer** sınıfı:

```powershell
Get-WmiObject -Class Win32_Printer -ComputerName
```

Kullanarak yazıcıları listeleyebilirsiniz **WScript.Network** WSH komut dosyalarında genelde kullanılan COM nesnesi:

```powershell
(New-Object -ComObject WScript.Network).EnumPrinterConnections()
```

Bu komut, bağlantı noktası adları ve yazıcı aygıt adlarını ayırt etiketleri olmadan basit bir dize koleksiyonunu döndürdüğünden yorumlamak kolay değildir.

### <a name="adding-a-network-printer"></a>Ağ yazıcısı ekleme

Yeni bir ağ yazıcısına eklemek için kullanın **WScript.Network**:

```powershell
(New-Object -ComObject WScript.Network).AddWindowsPrinterConnection("\\Printserver01\Xerox5")
```

### <a name="setting-a-default-printer"></a>Varsayılan yazıcı belirleme

Varsayılan yazıcı ayarlamak için WMI kullanmak için Yazıcı Bul **Win32_Printer** koleksiyonu ve ardından çağırma **SetDefaultPrinter** yöntemi:

```powershell
(Get-WmiObject -ComputerName . -Class Win32_Printer -Filter "Name='HP LaserJet 5Si'").SetDefaultPrinter()
```

**WScript.Network** içerdiğinden kullanmak, biraz daha basit olduğu bir **SetDefaultPrinter** yönteminin yalnızca yazıcı adını bağımsız değişken olarak alan:

```powershell
(New-Object -ComObject WScript.Network).SetDefaultPrinter('HP LaserJet 5Si')
```

### <a name="removing-a-printer-connection"></a>Bir yazıcı bağlantısı kaldırılıyor

Bir yazıcı bağlantısı kaldırmak için kullanın **WScript.Network RemovePrinterConnection** yöntemi:

```powershell
(New-Object -ComObject WScript.Network).RemovePrinterConnection("\\Printserver01\Xerox5")
```