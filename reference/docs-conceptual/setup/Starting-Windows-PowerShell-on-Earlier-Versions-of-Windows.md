---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: "Windows'un önceki sürümlerinde Windows PowerShell'i başlatma"
ms.assetid: 57125436-3d1e-4e7f-b5c4-8f0ecb49d642
ms.openlocfilehash: 52e3acc1fd3009ecad3b7134008e38d4edfb5ca7
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2017
---
# <a name="starting-windows-powershell-on-earlier-versions-of-windows"></a><span data-ttu-id="25d99-103">Windows'un önceki sürümlerinde Windows PowerShell'i başlatma</span><span class="sxs-lookup"><span data-stu-id="25d99-103">Starting Windows PowerShell on Earlier Versions of Windows</span></span>
<span data-ttu-id="25d99-104">Bu bölümde, Windows PowerShell ve Windows PowerShell Tümleşik komut dosyası ortamı (ISE) Windows® 7, Windows Server® 2008 R2 ve Windows Server® 2008 Başlat açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="25d99-104">This section explains how to start Windows PowerShell and Windows PowerShell Integrated Scripting Environment (ISE) on Windows® 7, Windows Server® 2008 R2, and Windows Server® 2008.</span></span> <span data-ttu-id="25d99-105">Ayrıca, isteğe bağlı Windows PowerShell ISE Windows PowerShell 2.0 Windows Server® 2008 R2 ve Windows Server® 2008 için nasıl etkinleştirileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="25d99-105">It also explains how to enable the optional feature for Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server® 2008 R2 and Windows Server® 2008.</span></span>

<span data-ttu-id="25d99-106">Desteklenen sistemlerinde Windows PowerShell 4.0 sürümünü yüklemek için karşıdan yükleyip kurun [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881).</span><span class="sxs-lookup"><span data-stu-id="25d99-106">To install Windows PowerShell 4.0 on supported systems, download and install [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881).</span></span> <span data-ttu-id="25d99-107">Daha fazla bilgi için bkz: [Windows PowerShell'i yükleme](Installing-Windows-PowerShell.md).</span><span class="sxs-lookup"><span data-stu-id="25d99-107">For more information, see [Installing Windows PowerShell](Installing-Windows-PowerShell.md).</span></span>

<span data-ttu-id="25d99-108">Windows PowerShell 3.0 desteklenen sistemlerinde yüklemek için karşıdan yükleyip kurun [Windows Management Framework 3.0](http://go.microsoft.com/fwlink/?LinkID=240290).</span><span class="sxs-lookup"><span data-stu-id="25d99-108">To install Windows PowerShell 3.0 on supported systems, download and install [Windows Management Framework 3.0](http://go.microsoft.com/fwlink/?LinkID=240290).</span></span> <span data-ttu-id="25d99-109">Daha fazla bilgi için bkz: [Windows PowerShell'i yükleme](Installing-Windows-PowerShell.md).</span><span class="sxs-lookup"><span data-stu-id="25d99-109">For more information, see [Installing Windows PowerShell](Installing-Windows-PowerShell.md).</span></span>

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a><span data-ttu-id="25d99-110">Windows'un önceki sürümlerinde Windows PowerShell'i başlatma</span><span class="sxs-lookup"><span data-stu-id="25d99-110">How to Start Windows PowerShell on Earlier Versions of Windows</span></span>
<span data-ttu-id="25d99-111">Windows PowerShell 3.0 ya da Windows PowerShell 4. 0'ın yüklü sürümü uygunsa başlatmak için aşağıdaki yöntemlerden birini kullanın.</span><span class="sxs-lookup"><span data-stu-id="25d99-111">Use any of the following methods to start the installed version of Windows PowerShell 3.0, or Windows PowerShell 4.0, where applicable.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="25d99-112">Başlat menüsünden</span><span class="sxs-lookup"><span data-stu-id="25d99-112">From the Start Menu</span></span>

- <span data-ttu-id="25d99-113">Tıklatın **Başlat**, türü **PowerShell**ve ardından **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="25d99-113">Click **Start**, type **PowerShell**, and then click **Windows PowerShell**.</span></span>

- <span data-ttu-id="25d99-114">Gelen **Başlat** menüsünde tıklatın **Başlat**, tıklatın **tüm programlar**,'ı tıklatın **Donatılar**,'ı tıklatın **Windows PowerShell**  klasörünü ve ardından **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="25d99-114">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="25d99-115">Komut isteminde</span><span class="sxs-lookup"><span data-stu-id="25d99-115">At the Command Prompt</span></span>

- <span data-ttu-id="25d99-116">Cmd.exe, Windows PowerShell veya Windows PowerShell ISE, Windows PowerShell'i başlatmak için şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="25d99-116">In Cmd.exe, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

    ```
    PowerShell
    ```

    <span data-ttu-id="25d99-117">PowerShell.exe programın parametreleri, oturum özelleştirmek için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="25d99-117">You can also use the parameters of the PowerShell.exe program to customize the session.</span></span> <span data-ttu-id="25d99-118">Daha fazla bilgi için bkz: [PowerShell.exe komut satırı yardımcı](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).</span><span class="sxs-lookup"><span data-stu-id="25d99-118">For more information, see [PowerShell.exe Command-Line Help](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).</span></span>

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="25d99-119">("Yönetici olarak çalıştır") ile yönetim ayrıcalıkları</span><span class="sxs-lookup"><span data-stu-id="25d99-119">With Administrative privileges ("Run as administrator")</span></span>

1. <span data-ttu-id="25d99-120">Tıklatın **Başlat**, türü **PowerShell**, sağ **Windows PowerShell**ve ardından **yönetici olarak çalıştır**.</span><span class="sxs-lookup"><span data-stu-id="25d99-120">Click **Start**, type **PowerShell**, right-click **Windows PowerShell**, and then click **Run as administrator**.</span></span>

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="25d99-121">Önceki Windows sürümlerinde Windows PowerShell ISE başlatma</span><span class="sxs-lookup"><span data-stu-id="25d99-121">How to Start Windows PowerShell ISE on Earlier Releases of Windows</span></span>
<span data-ttu-id="25d99-122">Windows PowerShell ISE başlatmak için aşağıdaki yöntemlerden birini kullanın.</span><span class="sxs-lookup"><span data-stu-id="25d99-122">Use any of the following methods to start Windows PowerShell ISE.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="25d99-123">Başlat menüsünden</span><span class="sxs-lookup"><span data-stu-id="25d99-123">From the Start Menu</span></span>

- <span data-ttu-id="25d99-124">Tıklatın **Başlat**, türü **işe**ve ardından **Windows PowerShell ISE**.</span><span class="sxs-lookup"><span data-stu-id="25d99-124">Click **Start**, type **ISE**, and then click **Windows PowerShell ISE**.</span></span>

- <span data-ttu-id="25d99-125">Gelen **Başlat** menüsünde tıklatın **Başlat**, tıklatın **tüm programlar**,'ı tıklatın **Donatılar**,'ı tıklatın **Windows PowerShell**  klasörünü ve ardından **Windows PowerShell ISE**.</span><span class="sxs-lookup"><span data-stu-id="25d99-125">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell ISE**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="25d99-126">Komut isteminde</span><span class="sxs-lookup"><span data-stu-id="25d99-126">At the Command Prompt</span></span>

- <span data-ttu-id="25d99-127">Cmd.exe, Windows PowerShell veya Windows PowerShell ISE, Windows PowerShell'i başlatmak için şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="25d99-127">In Cmd.exe, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

    ```
    PowerShell_ISE
    ```

    <span data-ttu-id="25d99-128">veya</span><span class="sxs-lookup"><span data-stu-id="25d99-128">or</span></span>

    ```
    ISE
    ```

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="25d99-129">("Yönetici olarak çalıştır") ile yönetim ayrıcalıkları</span><span class="sxs-lookup"><span data-stu-id="25d99-129">With Administrative privileges ("Run as administrator")</span></span>

1. <span data-ttu-id="25d99-130">Tıklatın **Başlat**, türü **işe**, sağ **Windows PowerShell ISE**ve ardından **yönetici olarak çalıştır**.</span><span class="sxs-lookup"><span data-stu-id="25d99-130">Click **Start**, type **ISE**, right-click **Windows PowerShell ISE**, and then click **Run as administrator**.</span></span>

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="25d99-131">Windows'un önceki sürümlerinde Windows PowerShell ISE etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="25d99-131">How to Enable Windows PowerShell ISE on Earlier Releases of Windows</span></span>
<span data-ttu-id="25d99-132">Windows PowerShell 4.0 ve Windows PowerShell 3.0, Windows PowerShell ISE tüm Windows sürümlerinde varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="25d99-132">In Windows PowerShell 4.0 and Windows PowerShell 3.0, Windows PowerShell ISE is enabled by default on all versions of Windows.</span></span> <span data-ttu-id="25d99-133">Zaten etkin değilse, Windows Management Framework 4.0 ya da Windows Management Framework 3.0 sağlar.</span><span class="sxs-lookup"><span data-stu-id="25d99-133">If it is not already enabled, Windows Management Framework 4.0 or Windows Management Framework 3.0 enables it.</span></span>

<span data-ttu-id="25d99-134">Windows PowerShell 2. 0 ', Windows PowerShell ISE, Windows 7 üzerinde varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="25d99-134">In Windows PowerShell 2.0, Windows PowerShell ISE is enabled by default on Windows 7.</span></span> <span data-ttu-id="25d99-135">Ancak, Windows Server 2008 R2 ve Windows Server 2008 üzerinde isteğe bağlı bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="25d99-135">However, on Windows Server 2008 R2 and Windows Server 2008, it is an optional feature.</span></span>

<span data-ttu-id="25d99-136">Windows PowerShell 2.0 Windows Server 2008 R2 veya Windows Server 2008, Windows PowerShell ISE etkinleştirmek için aşağıdaki yordamı kullanın.</span><span class="sxs-lookup"><span data-stu-id="25d99-136">To enable Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server 2008 R2 or Windows Server 2008, use the following procedure.</span></span>

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="25d99-137">Windows PowerShell Tümleşik komut dosyası ortamı (ISE) etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="25d99-137">To enable Windows PowerShell Integrated Scripting Environment (ISE)</span></span>

1. <span data-ttu-id="25d99-138">Sunucu Yöneticisi'ni başlatın.</span><span class="sxs-lookup"><span data-stu-id="25d99-138">Start Server Manager.</span></span>

2. <span data-ttu-id="25d99-139">Tıklatın **özellikleri** ve ardından **Özellik Ekle**.</span><span class="sxs-lookup"><span data-stu-id="25d99-139">Click **Features** and then click **Add Features**.</span></span>

3. <span data-ttu-id="25d99-140">Özellikleri Windows PowerShell Tümleşik komut dosyası ortamı (ISE) tıklayın.</span><span class="sxs-lookup"><span data-stu-id="25d99-140">In Select Features, click Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

