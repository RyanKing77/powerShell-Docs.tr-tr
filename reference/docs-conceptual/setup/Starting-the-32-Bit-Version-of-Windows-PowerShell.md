---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: "Windows PowerShell 32 Bit sürümü başlatılıyor"
ms.assetid: 12b31890-2609-4a76-8c24-0ebe78084f50
ms.openlocfilehash: d682ce45ebc92cda3a9008ab608bacf9ef8eba57
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2017
---
# <a name="starting-the-32-bit-version-of-windows-powershell"></a><span data-ttu-id="3332f-103">Windows PowerShell 32-Bit sürümünü başlatılıyor</span><span class="sxs-lookup"><span data-stu-id="3332f-103">Starting the 32-Bit Version of Windows PowerShell</span></span>
<span data-ttu-id="3332f-104">64-bit bir bilgisayarda, Windows PowerShell yüklediğinizde **Windows PowerShell (x86)**, Windows PowerShell 32-bit sürümünü yanı sıra 64-bit sürümü yüklü.</span><span class="sxs-lookup"><span data-stu-id="3332f-104">When you install Windows PowerShell on a 64-bit computer, **Windows PowerShell (x86)**, a 32-bit version of Windows PowerShell is installed in addition to the 64-bit version.</span></span> <span data-ttu-id="3332f-105">Windows PowerShell çalıştırdığınızda, varsayılan olarak 64-bit sürümünü çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="3332f-105">When you run Windows PowerShell, the 64-bit version runs by default.</span></span>

<span data-ttu-id="3332f-106">Ancak, bazen çalıştırmanız gerekebilir **Windows PowerShell (x86)**gibi bir Modülü'nü kullanırken 32-bit sürümünü gerektirir veya, bir 32 bit bilgisayara uzaktan bağlanıyorsanız olduğunda.</span><span class="sxs-lookup"><span data-stu-id="3332f-106">However, you might occasionally need to run **Windows PowerShell (x86)**, such as when you are using a module that requires the 32-bit version or when you are connecting remotely to a 32-bit computer.</span></span>

<span data-ttu-id="3332f-107">Windows PowerShell 32-bit sürümünü başlatmak için aşağıdaki yordamlardan birini kullanın.</span><span class="sxs-lookup"><span data-stu-id="3332f-107">To start a 32-bit version of Windows PowerShell, use any of the following procedures.</span></span>

#### <a name="in-windows-server-2012-r2"></a><span data-ttu-id="3332f-108">Windows Server® 2012 R2'de</span><span class="sxs-lookup"><span data-stu-id="3332f-108">In Windows Server® 2012 R2</span></span>

- <span data-ttu-id="3332f-109">Üzerinde **Başlat** ekranında, yazın **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="3332f-109">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="3332f-110">Tıklatın **Windows PowerShell x86** döşeme.</span><span class="sxs-lookup"><span data-stu-id="3332f-110">Click the **Windows PowerShell x86** tile.</span></span>

- <span data-ttu-id="3332f-111">İçinde **Sunucu Yöneticisi'ni**, gelen **Araçları** menüsünde, select **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="3332f-111">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="3332f-112">Masaüstünde, imleç bölmenin sağ üst köşedeki için Taşı'yı tıklatın **arama**, türü **PowerShell x86** ve ardından **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="3332f-112">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="3332f-113">Komut satırı girin:`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="3332f-113">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-server-2012"></a><span data-ttu-id="3332f-114">Windows Server® 2012</span><span class="sxs-lookup"><span data-stu-id="3332f-114">In Windows Server® 2012</span></span>

- <span data-ttu-id="3332f-115">Üzerinde **Başlat** ekranında, yazın **PowerShell** ve ardından **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="3332f-115">On the **Start** screen, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="3332f-116">İçinde **Sunucu Yöneticisi'ni**, gelen **Araçları** menüsünde, select **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="3332f-116">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="3332f-117">Masaüstünde, imleç bölmenin sağ üst köşedeki için Taşı'yı tıklatın **arama**, türü **PowerShell** ve ardından **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="3332f-117">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="3332f-118">Komut satırı girin:`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="3332f-118">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-81"></a><span data-ttu-id="3332f-119">Windows® 8.1</span><span class="sxs-lookup"><span data-stu-id="3332f-119">In Windows® 8.1</span></span>

- <span data-ttu-id="3332f-120">Üzerinde **Başlat** ekranında, yazın **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="3332f-120">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="3332f-121">Tıklatın **Windows PowerShell x86** döşeme.</span><span class="sxs-lookup"><span data-stu-id="3332f-121">Click the **Windows PowerShell x86** tile.</span></span>

- <span data-ttu-id="3332f-122">Çalıştırıyorsanız, [Uzak Sunucu Yönetim Araçları](http://go.microsoft.com/fwlink/?LinkID=304145) Windows 8.1 için Windows Powershell'den x86 da açabilirsiniz **Server ManagerTools** menüsü.</span><span class="sxs-lookup"><span data-stu-id="3332f-122">If you are running [Remote Server Administration Tools](http://go.microsoft.com/fwlink/?LinkID=304145) for Windows 8.1, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="3332f-123">Seçin **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="3332f-123">Select **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="3332f-124">Masaüstünde, imleç bölmenin sağ üst köşedeki için Taşı'yı tıklatın **arama**, türü **PowerShell x86** ve ardından **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="3332f-124">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>
   
- <span data-ttu-id="3332f-125">Komut satırı girin:`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="3332f-125">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-8"></a><span data-ttu-id="3332f-126">Windows® 8</span><span class="sxs-lookup"><span data-stu-id="3332f-126">In Windows® 8</span></span>

- <span data-ttu-id="3332f-127">Üzerinde **Başlat** ekranında, imleci için sağ üst köşesindeki taşıma, tıklatın **ayarları**, tıklatın **döşeme**ve ardından taşıma **Yönetimsel Araçları Göster** kaydırıcı Evet.</span><span class="sxs-lookup"><span data-stu-id="3332f-127">On the **Start** screen, move the cursor to the upper right corner, click **Settings**, click **Tiles**, and then move the **Show Administrative Tools** slider to Yes.</span></span> <span data-ttu-id="3332f-128">Ardından, yazın **PowerShell** tıklatıp **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="3332f-128">Then, type **PowerShell** and click **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="3332f-129">Çalıştırıyorsanız, [Uzak Sunucu Yönetim Araçları](http://www.microsoft.com/download/details.aspx?id=28972) Windows 8 için Windows Powershell'den x86 da açabilirsiniz **Server ManagerTools** menüsü.</span><span class="sxs-lookup"><span data-stu-id="3332f-129">If you are running [Remote Server Administration Tools](http://www.microsoft.com/download/details.aspx?id=28972) for Windows 8, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="3332f-130">Seçin **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="3332f-130">Select **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="3332f-131">Üzerinde **Başlat** ekran veya yazın, Masaüstü **PowerShell (x86)** ve ardından **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="3332f-131">On the **Start** screen or the desktop, type **PowerShell (x86)** and then click **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="3332f-132">Komut satırı girin:`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="3332f-132">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

