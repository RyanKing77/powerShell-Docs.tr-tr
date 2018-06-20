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
# <a name="working-with-printers"></a><span data-ttu-id="d7dc8-103">Yazıcılar ile Çalışma</span><span class="sxs-lookup"><span data-stu-id="d7dc8-103">Working with Printers</span></span>

<span data-ttu-id="d7dc8-104">WMI ve WSH WScript.Network COM nesnesinden kullanarak yazıcıları yönetmek için Windows PowerShell'i kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d7dc8-104">You can use Windows PowerShell to manage printers by using WMI and the WScript.Network COM object from WSH.</span></span> <span data-ttu-id="d7dc8-105">Belirli görevleri göstermek için her iki araçları bir karışımını kullanacağız.</span><span class="sxs-lookup"><span data-stu-id="d7dc8-105">We will use a mix of both tools to demonstrate specific tasks.</span></span>

### <a name="listing-printer-connections"></a><span data-ttu-id="d7dc8-106">Yazıcı bağlantılarını listeleme</span><span class="sxs-lookup"><span data-stu-id="d7dc8-106">Listing Printer Connections</span></span>

<span data-ttu-id="d7dc8-107">Bir bilgisayarda yüklü yazıcılar listesinde en basit yolu WMI kullanmaktır **Win32_Printer** sınıfı:</span><span class="sxs-lookup"><span data-stu-id="d7dc8-107">The simplest way to list the printers installed on a computer is to use the WMI **Win32_Printer** class:</span></span>

```powershell
Get-WmiObject -Class Win32_Printer -ComputerName
```

<span data-ttu-id="d7dc8-108">Kullanarak yazıcıları listeleyebilirsiniz **WScript.Network** WSH komut dosyalarında genelde kullanılan COM nesnesi:</span><span class="sxs-lookup"><span data-stu-id="d7dc8-108">You can also list the printers by using the **WScript.Network** COM object that is typically used in WSH scripts:</span></span>

```powershell
(New-Object -ComObject WScript.Network).EnumPrinterConnections()
```

<span data-ttu-id="d7dc8-109">Bu komut, bağlantı noktası adları ve yazıcı aygıt adlarını ayırt etiketleri olmadan basit bir dize koleksiyonunu döndürdüğünden yorumlamak kolay değildir.</span><span class="sxs-lookup"><span data-stu-id="d7dc8-109">Because this command returns a simple string collection of port names and printer device names without any distinguishing labels, it is not easy to interpret.</span></span>

### <a name="adding-a-network-printer"></a><span data-ttu-id="d7dc8-110">Ağ yazıcısı ekleme</span><span class="sxs-lookup"><span data-stu-id="d7dc8-110">Adding a Network Printer</span></span>

<span data-ttu-id="d7dc8-111">Yeni bir ağ yazıcısına eklemek için kullanın **WScript.Network**:</span><span class="sxs-lookup"><span data-stu-id="d7dc8-111">To add a new network printer, use **WScript.Network**:</span></span>

```powershell
(New-Object -ComObject WScript.Network).AddWindowsPrinterConnection("\\Printserver01\Xerox5")
```

### <a name="setting-a-default-printer"></a><span data-ttu-id="d7dc8-112">Varsayılan yazıcı belirleme</span><span class="sxs-lookup"><span data-stu-id="d7dc8-112">Setting a Default Printer</span></span>

<span data-ttu-id="d7dc8-113">Varsayılan yazıcı ayarlamak için WMI kullanmak için Yazıcı Bul **Win32_Printer** koleksiyonu ve ardından çağırma **SetDefaultPrinter** yöntemi:</span><span class="sxs-lookup"><span data-stu-id="d7dc8-113">To use WMI to set the default printer, find the printer in the **Win32_Printer** collection and then invoke the **SetDefaultPrinter** method:</span></span>

```powershell
(Get-WmiObject -ComputerName . -Class Win32_Printer -Filter "Name='HP LaserJet 5Si'").SetDefaultPrinter()
```

<span data-ttu-id="d7dc8-114">**WScript.Network** içerdiğinden kullanmak, biraz daha basit olduğu bir **SetDefaultPrinter** yönteminin yalnızca yazıcı adını bağımsız değişken olarak alan:</span><span class="sxs-lookup"><span data-stu-id="d7dc8-114">**WScript.Network** is a little simpler to use, because it has a **SetDefaultPrinter** method that takes only the printer name as an argument:</span></span>

```powershell
(New-Object -ComObject WScript.Network).SetDefaultPrinter('HP LaserJet 5Si')
```

### <a name="removing-a-printer-connection"></a><span data-ttu-id="d7dc8-115">Bir yazıcı bağlantısı kaldırılıyor</span><span class="sxs-lookup"><span data-stu-id="d7dc8-115">Removing a Printer Connection</span></span>

<span data-ttu-id="d7dc8-116">Bir yazıcı bağlantısı kaldırmak için kullanın **WScript.Network RemovePrinterConnection** yöntemi:</span><span class="sxs-lookup"><span data-stu-id="d7dc8-116">To remove a printer connection, use the **WScript.Network RemovePrinterConnection** method:</span></span>

```powershell
(New-Object -ComObject WScript.Network).RemovePrinterConnection("\\Printserver01\Xerox5")
```