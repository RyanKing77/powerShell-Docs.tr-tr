---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: "Yazıcılar ile çalışma"
ms.assetid: 4f29ead3-f83b-4706-ac3e-f2154ff38dc5
ms.openlocfilehash: c8b4d728c9fddd39e1aeb56d6f9b8ffffe4c7292
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2017
---
# <a name="working-with-printers"></a><span data-ttu-id="74e90-103">Yazıcılar ile çalışma</span><span class="sxs-lookup"><span data-stu-id="74e90-103">Working with Printers</span></span>
<span data-ttu-id="74e90-104">WMI ve WSH WScript.Network COM nesnesinden kullanarak yazıcıları yönetmek için Windows PowerShell'i kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74e90-104">You can use Windows PowerShell to manage printers by using WMI and the WScript.Network COM object from WSH.</span></span> <span data-ttu-id="74e90-105">Belirli görevleri göstermek için her iki araçları bir karışımını kullanacağız.</span><span class="sxs-lookup"><span data-stu-id="74e90-105">We will use a mix of both tools to demonstrate specific tasks.</span></span>

### <a name="listing-printer-connections"></a><span data-ttu-id="74e90-106">Yazıcı bağlantılarını listeleme</span><span class="sxs-lookup"><span data-stu-id="74e90-106">Listing Printer Connections</span></span>
<span data-ttu-id="74e90-107">Bir bilgisayarda yüklü yazıcılar listesinde en basit yolu WMI kullanmaktır **Win32_Printer** sınıfı:</span><span class="sxs-lookup"><span data-stu-id="74e90-107">The simplest way to list the printers installed on a computer is to use the WMI **Win32_Printer** class:</span></span>

```
Get-WmiObject -Class Win32_Printer -ComputerName
```

<span data-ttu-id="74e90-108">Kullanarak yazıcıları listeleyebilirsiniz **WScript.Network** WSH komut dosyalarında genelde kullanılan COM nesnesi:</span><span class="sxs-lookup"><span data-stu-id="74e90-108">You can also list the printers by using the **WScript.Network** COM object that is typically used in WSH scripts:</span></span>

```
(New-Object -ComObject WScript.Network).EnumPrinterConnections()
```

<span data-ttu-id="74e90-109">Bu komut, bağlantı noktası adları ve yazıcı aygıt adlarını ayırt etiketleri olmadan basit bir dize koleksiyonunu döndürdüğünden yorumlamak kolay değildir.</span><span class="sxs-lookup"><span data-stu-id="74e90-109">Because this command returns a simple string collection of port names and printer device names without any distinguishing labels, it is not easy to interpret.</span></span>

### <a name="adding-a-network-printer"></a><span data-ttu-id="74e90-110">Ağ yazıcısı ekleme</span><span class="sxs-lookup"><span data-stu-id="74e90-110">Adding a Network Printer</span></span>
<span data-ttu-id="74e90-111">Yeni bir ağ yazıcısına eklemek için kullanın **WScript.Network**:</span><span class="sxs-lookup"><span data-stu-id="74e90-111">To add a new network printer, use **WScript.Network**:</span></span>

```
(New-Object -ComObject WScript.Network).AddWindowsPrinterConnection("\\Printserver01\Xerox5")
```

### <a name="setting-a-default-printer"></a><span data-ttu-id="74e90-112">Varsayılan yazıcı belirleme</span><span class="sxs-lookup"><span data-stu-id="74e90-112">Setting a Default Printer</span></span>
<span data-ttu-id="74e90-113">Varsayılan yazıcı ayarlamak için WMI kullanmak için Yazıcı Bul **Win32_Printer** koleksiyonu ve ardından çağırma **SetDefaultPrinter** yöntemi:</span><span class="sxs-lookup"><span data-stu-id="74e90-113">To use WMI to set the default printer, find the printer in the **Win32_Printer** collection and then invoke the **SetDefaultPrinter** method:</span></span>

```
(Get-WmiObject -ComputerName . -Class Win32_Printer -Filter "Name='HP LaserJet 5Si'").SetDefaultPrinter()
```

<span data-ttu-id="74e90-114">**WScript.Network** içerdiğinden kullanmak, biraz daha basit olduğu bir **SetDefaultPrinter** yönteminin yalnızca yazıcı adını bağımsız değişken olarak alan:</span><span class="sxs-lookup"><span data-stu-id="74e90-114">**WScript.Network** is a little simpler to use, because it has a **SetDefaultPrinter** method that takes only the printer name as an argument:</span></span>

```
(New-Object -ComObject WScript.Network).SetDefaultPrinter('HP LaserJet 5Si')
```

### <a name="removing-a-printer-connection"></a><span data-ttu-id="74e90-115">Bir yazıcı bağlantısı kaldırılıyor</span><span class="sxs-lookup"><span data-stu-id="74e90-115">Removing a Printer Connection</span></span>
<span data-ttu-id="74e90-116">Bir yazıcı bağlantısı kaldırmak için kullanın **WScript.Network RemovePrinterConnection** yöntemi:</span><span class="sxs-lookup"><span data-stu-id="74e90-116">To remove a printer connection, use the **WScript.Network RemovePrinterConnection** method:</span></span>

```
(New-Object -ComObject WScript.Network).RemovePrinterConnection("\\Printserver01\Xerox5")
```

