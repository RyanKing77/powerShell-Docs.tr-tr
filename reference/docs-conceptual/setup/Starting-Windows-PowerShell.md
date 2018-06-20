---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Windows Powershell Başlatma
ms.assetid: 59b649a2-c90c-4cf4-bf95-a740c59148e7
ms.openlocfilehash: b56ddc2f577225646729b99f3a2abcb8cc60d307
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30953132"
---
# <a name="starting-windows-powershell"></a><span data-ttu-id="070fe-103">Windows Powershell Başlatma</span><span class="sxs-lookup"><span data-stu-id="070fe-103">Starting Windows PowerShell</span></span>
<span data-ttu-id="070fe-104">Birden çok konaklarına katıştırılmış bir komut dosyası altyapısı dll powershell'dir.</span><span class="sxs-lookup"><span data-stu-id="070fe-104">PowerShell is a scripting engine dll which is embedded into multiple hosts.</span></span>  <span data-ttu-id="070fe-105">Başlatır yaygın konak etkileşimli komut satırı PowerShell.exe ve etkileşimli komut dosyası ortamı PowerShell_ISE.exe verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="070fe-105">The most common host you will start are the interactive command line PowerShell.exe and the Interactive Scripting Environment PowerShell_ISE.exe.</span></span>

<span data-ttu-id="070fe-106">Windows Server® 2012 R2, Windows® 8.1, Windows Server 2012 ve Windows 8 Windows PowerShell® başlatmak için bkz: [genel yönetim görevleri ve gezinme](http://technet.microsoft.com/library/hh831491.aspx).</span><span class="sxs-lookup"><span data-stu-id="070fe-106">To start Windows PowerShell® on Windows Server® 2012 R2, Windows® 8.1, Windows Server 2012, and Windows 8, see [Common Management Tasks and Navigation](http://technet.microsoft.com/library/hh831491.aspx).</span></span>

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a><span data-ttu-id="070fe-107">Windows'un önceki sürümlerinde Windows PowerShell'i başlatma</span><span class="sxs-lookup"><span data-stu-id="070fe-107">How to Start Windows PowerShell on Earlier Versions of Windows</span></span>

<span data-ttu-id="070fe-108">Bu bölümde, Windows PowerShell ve Windows PowerShell Tümleşik komut dosyası ortamı (ISE) Windows® 7, Windows Server® 2008 R2 ve Windows Server® 2008 Başlat açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="070fe-108">This section explains how to start Windows PowerShell and Windows PowerShell Integrated Scripting Environment (ISE) on Windows® 7, Windows Server® 2008 R2, and Windows Server® 2008.</span></span> <span data-ttu-id="070fe-109">Ayrıca, isteğe bağlı Windows PowerShell ISE Windows PowerShell 2.0 Windows Server® 2008 R2 ve Windows Server® 2008 için nasıl etkinleştirileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="070fe-109">It also explains how to enable the optional feature for Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server® 2008 R2 and Windows Server® 2008.</span></span>

<span data-ttu-id="070fe-110">Windows PowerShell 3.0 ya da Windows PowerShell 4. 0'ın yüklü sürümü uygunsa başlatmak için aşağıdaki yöntemlerden birini kullanın.</span><span class="sxs-lookup"><span data-stu-id="070fe-110">Use any of the following methods to start the installed version of Windows PowerShell 3.0, or Windows PowerShell 4.0, where applicable.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="070fe-111">Başlat menüsünden</span><span class="sxs-lookup"><span data-stu-id="070fe-111">From the Start Menu</span></span>

- <span data-ttu-id="070fe-112">Tıklatın **Başlat**, türü **PowerShell**ve ardından **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="070fe-112">Click **Start**, type **PowerShell**, and then click **Windows PowerShell**.</span></span>
- <span data-ttu-id="070fe-113">Gelen **Başlat** menüsünde tıklatın **Başlat**, tıklatın **tüm programlar**,'ı tıklatın **Donatılar**,'ı tıklatın **Windows PowerShell**  klasörünü ve ardından **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="070fe-113">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="070fe-114">Komut isteminde</span><span class="sxs-lookup"><span data-stu-id="070fe-114">At the Command Prompt</span></span>

<span data-ttu-id="070fe-115">Cmd.exe, Windows PowerShell veya Windows PowerShell ISE, Windows PowerShell'i başlatmak için şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="070fe-115">In Cmd.exe, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

```
PowerShell
```

<span data-ttu-id="070fe-116">PowerShell.exe programın parametreleri, oturum özelleştirmek için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="070fe-116">You can also use the parameters of the PowerShell.exe program to customize the session.</span></span> <span data-ttu-id="070fe-117">Daha fazla bilgi için bkz: [PowerShell.exe komut satırı yardımcı](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).</span><span class="sxs-lookup"><span data-stu-id="070fe-117">For more information, see [PowerShell.exe Command-Line Help](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).</span></span>

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="070fe-118">("Yönetici olarak çalıştır") ile yönetim ayrıcalıkları</span><span class="sxs-lookup"><span data-stu-id="070fe-118">With Administrative privileges ("Run as administrator")</span></span>

<span data-ttu-id="070fe-119">Tıklatın **Başlat**, türü **PowerShell**, sağ **Windows PowerShell**ve ardından **yönetici olarak çalıştır**.</span><span class="sxs-lookup"><span data-stu-id="070fe-119">Click **Start**, type **PowerShell**, right-click **Windows PowerShell**, and then click **Run as administrator**.</span></span>

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="070fe-120">Önceki Windows sürümlerinde Windows PowerShell ISE başlatma</span><span class="sxs-lookup"><span data-stu-id="070fe-120">How to Start Windows PowerShell ISE on Earlier Releases of Windows</span></span>

<span data-ttu-id="070fe-121">Windows PowerShell ISE başlatmak için aşağıdaki yöntemlerden birini kullanın.</span><span class="sxs-lookup"><span data-stu-id="070fe-121">Use any of the following methods to start Windows PowerShell ISE.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="070fe-122">Başlat menüsünden</span><span class="sxs-lookup"><span data-stu-id="070fe-122">From the Start Menu</span></span>

- <span data-ttu-id="070fe-123">Tıklatın **Başlat**, türü **işe**ve ardından **Windows PowerShell ISE**.</span><span class="sxs-lookup"><span data-stu-id="070fe-123">Click **Start**, type **ISE**, and then click **Windows PowerShell ISE**.</span></span>
- <span data-ttu-id="070fe-124">Gelen **Başlat** menüsünde tıklatın **Başlat**, tıklatın **tüm programlar**,'ı tıklatın **Donatılar**,'ı tıklatın **Windows PowerShell**  klasörünü ve ardından **Windows PowerShell ISE**.</span><span class="sxs-lookup"><span data-stu-id="070fe-124">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell ISE**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="070fe-125">Komut isteminde</span><span class="sxs-lookup"><span data-stu-id="070fe-125">At the Command Prompt</span></span>

<span data-ttu-id="070fe-126">Cmd.exe, Windows PowerShell veya Windows PowerShell ISE, Windows PowerShell'i başlatmak için şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="070fe-126">In Cmd.exe, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

```
PowerShell_ISE
```

<span data-ttu-id="070fe-127">veya</span><span class="sxs-lookup"><span data-stu-id="070fe-127">or</span></span>

```
ISE
```

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="070fe-128">("Yönetici olarak çalıştır") ile yönetim ayrıcalıkları</span><span class="sxs-lookup"><span data-stu-id="070fe-128">With Administrative privileges ("Run as administrator")</span></span>

<span data-ttu-id="070fe-129">Tıklatın **Başlat**, türü **işe**, sağ **Windows PowerShell ISE**ve ardından **yönetici olarak çalıştır**.</span><span class="sxs-lookup"><span data-stu-id="070fe-129">Click **Start**, type **ISE**, right-click **Windows PowerShell ISE**, and then click **Run as administrator**.</span></span>

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="070fe-130">Windows'un önceki sürümlerinde Windows PowerShell ISE etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="070fe-130">How to Enable Windows PowerShell ISE on Earlier Releases of Windows</span></span>

<span data-ttu-id="070fe-131">Windows PowerShell 4.0 ve Windows PowerShell 3.0, Windows PowerShell ISE tüm Windows sürümlerinde varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="070fe-131">In Windows PowerShell 4.0 and Windows PowerShell 3.0, Windows PowerShell ISE is enabled by default on all versions of Windows.</span></span> <span data-ttu-id="070fe-132">Zaten etkin değilse, Windows Management Framework 4.0 ya da Windows Management Framework 3.0 sağlar.</span><span class="sxs-lookup"><span data-stu-id="070fe-132">If it is not already enabled, Windows Management Framework 4.0 or Windows Management Framework 3.0 enables it.</span></span>

<span data-ttu-id="070fe-133">Windows PowerShell 2. 0 ', Windows PowerShell ISE, Windows 7 üzerinde varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="070fe-133">In Windows PowerShell 2.0, Windows PowerShell ISE is enabled by default on Windows 7.</span></span> <span data-ttu-id="070fe-134">Ancak, Windows Server 2008 R2 ve Windows Server 2008 üzerinde isteğe bağlı bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="070fe-134">However, on Windows Server 2008 R2 and Windows Server 2008, it is an optional feature.</span></span>

<span data-ttu-id="070fe-135">Windows PowerShell 2.0 Windows Server 2008 R2 veya Windows Server 2008, Windows PowerShell ISE etkinleştirmek için aşağıdaki yordamı kullanın.</span><span class="sxs-lookup"><span data-stu-id="070fe-135">To enable Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server 2008 R2 or Windows Server 2008, use the following procedure.</span></span>

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="070fe-136">Windows PowerShell Tümleşik komut dosyası ortamı (ISE) etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="070fe-136">To enable Windows PowerShell Integrated Scripting Environment (ISE)</span></span>

1. <span data-ttu-id="070fe-137">Sunucu Yöneticisi'ni başlatın.</span><span class="sxs-lookup"><span data-stu-id="070fe-137">Start Server Manager.</span></span>
2. <span data-ttu-id="070fe-138">Tıklatın **özellikleri** ve ardından **Özellik Ekle**.</span><span class="sxs-lookup"><span data-stu-id="070fe-138">Click **Features** and then click **Add Features**.</span></span>
3. <span data-ttu-id="070fe-139">Özellikleri Windows PowerShell Tümleşik komut dosyası ortamı (ISE) tıklayın.</span><span class="sxs-lookup"><span data-stu-id="070fe-139">In Select Features, click Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

## <a name="starting-the-32-bit-version-of-windows-powershell"></a><span data-ttu-id="070fe-140">Windows PowerShell 32-Bit sürümünü başlatılıyor</span><span class="sxs-lookup"><span data-stu-id="070fe-140">Starting the 32-Bit Version of Windows PowerShell</span></span>

<span data-ttu-id="070fe-141">64-bit bir bilgisayarda, Windows PowerShell yüklediğinizde **Windows PowerShell (x86)**, Windows PowerShell 32-bit sürümünü yanı sıra 64-bit sürümü yüklü.</span><span class="sxs-lookup"><span data-stu-id="070fe-141">When you install Windows PowerShell on a 64-bit computer, **Windows PowerShell (x86)**, a 32-bit version of Windows PowerShell is installed in addition to the 64-bit version.</span></span> <span data-ttu-id="070fe-142">Windows PowerShell çalıştırdığınızda, varsayılan olarak 64-bit sürümünü çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="070fe-142">When you run Windows PowerShell, the 64-bit version runs by default.</span></span>

<span data-ttu-id="070fe-143">Ancak, bazen çalıştırmanız gerekebilir **Windows PowerShell (x86)** gibi bir Modülü'nü kullanırken 32-bit sürümünü gerektirir veya, bir 32 bit bilgisayara uzaktan bağlanıyorsanız olduğunda.</span><span class="sxs-lookup"><span data-stu-id="070fe-143">However, you might occasionally need to run **Windows PowerShell (x86)**, such as when you are using a module that requires the 32-bit version or when you are connecting remotely to a 32-bit computer.</span></span>

<span data-ttu-id="070fe-144">Windows PowerShell 32-bit sürümünü başlatmak için aşağıdaki yordamlardan birini kullanın.</span><span class="sxs-lookup"><span data-stu-id="070fe-144">To start a 32-bit version of Windows PowerShell, use any of the following procedures.</span></span>

#### <a name="in-windows-server-2012-r2"></a><span data-ttu-id="070fe-145">In Windows Server® 2012 R2</span><span class="sxs-lookup"><span data-stu-id="070fe-145">In Windows Server® 2012 R2</span></span>

- <span data-ttu-id="070fe-146">Üzerinde **Başlat** ekranında, yazın **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="070fe-146">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="070fe-147">Tıklatın **Windows PowerShell x86** döşeme.</span><span class="sxs-lookup"><span data-stu-id="070fe-147">Click the **Windows PowerShell x86** tile.</span></span>
- <span data-ttu-id="070fe-148">İçinde **Sunucu Yöneticisi'ni**, gelen **Araçları** menüsünde, select **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="070fe-148">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="070fe-149">Masaüstünde, imleç bölmenin sağ üst köşedeki için Taşı'yı tıklatın **arama**, türü **PowerShell x86** ve ardından **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="070fe-149">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="070fe-150">Komut satırı girin: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="070fe-150">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-server-2012"></a><span data-ttu-id="070fe-151">In Windows Server® 2012</span><span class="sxs-lookup"><span data-stu-id="070fe-151">In Windows Server® 2012</span></span>

- <span data-ttu-id="070fe-152">Üzerinde **Başlat** ekranında, yazın **PowerShell** ve ardından **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="070fe-152">On the **Start** screen, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="070fe-153">İçinde **Sunucu Yöneticisi'ni**, gelen **Araçları** menüsünde, select **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="070fe-153">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="070fe-154">Masaüstünde, imleç bölmenin sağ üst köşedeki için Taşı'yı tıklatın **arama**, türü **PowerShell** ve ardından **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="070fe-154">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="070fe-155">Komut satırı girin: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="070fe-155">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-81"></a><span data-ttu-id="070fe-156">In Windows® 8.1</span><span class="sxs-lookup"><span data-stu-id="070fe-156">In Windows® 8.1</span></span>

- <span data-ttu-id="070fe-157">Üzerinde **Başlat** ekranında, yazın **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="070fe-157">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="070fe-158">Tıklatın **Windows PowerShell x86** döşeme.</span><span class="sxs-lookup"><span data-stu-id="070fe-158">Click the **Windows PowerShell x86** tile.</span></span>
- <span data-ttu-id="070fe-159">Çalıştırıyorsanız, [Uzak Sunucu Yönetim Araçları](http://go.microsoft.com/fwlink/?LinkID=304145) Windows 8.1 için Windows Powershell'den x86 da açabilirsiniz **Server ManagerTools** menüsü.</span><span class="sxs-lookup"><span data-stu-id="070fe-159">If you are running [Remote Server Administration Tools](http://go.microsoft.com/fwlink/?LinkID=304145) for Windows 8.1, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span>
  <span data-ttu-id="070fe-160">Seçin **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="070fe-160">Select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="070fe-161">Masaüstünde, imleç bölmenin sağ üst köşedeki için Taşı'yı tıklatın **arama**, türü **PowerShell x86** ve ardından **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="070fe-161">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="070fe-162">Komut satırı girin: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="070fe-162">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-8"></a><span data-ttu-id="070fe-163">In Windows® 8</span><span class="sxs-lookup"><span data-stu-id="070fe-163">In Windows® 8</span></span>

- <span data-ttu-id="070fe-164">Üzerinde **Başlat** ekranında, imleci için sağ üst köşesindeki taşıma, tıklatın **ayarları**, tıklatın **döşeme**ve ardından taşıma **Yönetimsel Araçları Göster** kaydırıcı Evet.</span><span class="sxs-lookup"><span data-stu-id="070fe-164">On the **Start** screen, move the cursor to the upper right corner, click **Settings**, click **Tiles**, and then move the **Show Administrative Tools** slider to Yes.</span></span> <span data-ttu-id="070fe-165">Ardından, yazın **PowerShell** tıklatıp **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="070fe-165">Then, type **PowerShell** and click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="070fe-166">Çalıştırıyorsanız, [Uzak Sunucu Yönetim Araçları](http://www.microsoft.com/download/details.aspx?id=28972) Windows 8 için Windows Powershell'den x86 da açabilirsiniz **Server ManagerTools** menüsü.</span><span class="sxs-lookup"><span data-stu-id="070fe-166">If you are running [Remote Server Administration Tools](http://www.microsoft.com/download/details.aspx?id=28972) for Windows 8, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="070fe-167">Seçin **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="070fe-167">Select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="070fe-168">Üzerinde **Başlat** ekran veya yazın, Masaüstü **PowerShell (x86)** ve ardından **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="070fe-168">On the **Start** screen or the desktop, type **PowerShell (x86)** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="070fe-169">Komut satırı girin: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="070fe-169">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>