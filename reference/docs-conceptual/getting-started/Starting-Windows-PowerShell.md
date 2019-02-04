---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Windows Powershell Başlatma
ms.assetid: 59b649a2-c90c-4cf4-bf95-a740c59148e7
ms.openlocfilehash: 9184e8b0e508610e7f4775f1032f3a69c93bb8c1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688325"
---
# <a name="starting-windows-powershell"></a><span data-ttu-id="10fdc-103">Windows Powershell Başlatma</span><span class="sxs-lookup"><span data-stu-id="10fdc-103">Starting Windows PowerShell</span></span>
<span data-ttu-id="10fdc-104">Birden çok konaklarına katıştırılmış bir komut dosyası altyapısı dll powershell'dir.</span><span class="sxs-lookup"><span data-stu-id="10fdc-104">PowerShell is a scripting engine dll which is embedded into multiple hosts.</span></span>  <span data-ttu-id="10fdc-105">En yaygın konak, başlar, etkileşimli komut satırı PowerShell.exe ve etkileşimli betik ortamı PowerShell_ISE.exe verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="10fdc-105">The most common host you will start are the interactive command line PowerShell.exe and the Interactive Scripting Environment PowerShell_ISE.exe.</span></span>

<span data-ttu-id="10fdc-106">Windows Server® 2012 R2, Windows® 8.1, Windows Server 2012 ve Windows 8 üzerinde Windows PowerShell® başlatmak için bkz: [genel yönetim görevleri ve gezinme](https://technet.microsoft.com/library/hh831491.aspx).</span><span class="sxs-lookup"><span data-stu-id="10fdc-106">To start Windows PowerShell® on Windows Server® 2012 R2, Windows® 8.1, Windows Server 2012, and Windows 8, see [Common Management Tasks and Navigation](https://technet.microsoft.com/library/hh831491.aspx).</span></span>

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a><span data-ttu-id="10fdc-107">Önceki Windows sürümlerinde Windows PowerShell'i başlatma</span><span class="sxs-lookup"><span data-stu-id="10fdc-107">How to Start Windows PowerShell on Earlier Versions of Windows</span></span>

<span data-ttu-id="10fdc-108">Bu bölümde, Windows® 7, Windows Server® 2008 R2 ve Windows Server® 2008 Windows PowerShell ve Windows PowerShell Tümleşik komut dosyası ortamı (ISE) başlatın açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="10fdc-108">This section explains how to start Windows PowerShell and Windows PowerShell Integrated Scripting Environment (ISE) on Windows® 7, Windows Server® 2008 R2, and Windows Server® 2008.</span></span> <span data-ttu-id="10fdc-109">Ayrıca, isteğe bağlı Windows PowerShell 2.0, Windows Server® 2008 R2 ve Windows Server® 2008'de Windows PowerShell ISE için nasıl etkinleştirileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="10fdc-109">It also explains how to enable the optional feature for Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server® 2008 R2 and Windows Server® 2008.</span></span>

<span data-ttu-id="10fdc-110">Uygunsa, Windows PowerShell 3.0 veya Windows PowerShell 4. 0'ın yüklü sürümü başlatmak için aşağıdaki yöntemlerden birini kullanın.</span><span class="sxs-lookup"><span data-stu-id="10fdc-110">Use any of the following methods to start the installed version of Windows PowerShell 3.0, or Windows PowerShell 4.0, where applicable.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="10fdc-111">Başlat Menüsü'nden</span><span class="sxs-lookup"><span data-stu-id="10fdc-111">From the Start Menu</span></span>

- <span data-ttu-id="10fdc-112">Tıklayın **Başlat**, türü **PowerShell**ve ardından **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="10fdc-112">Click **Start**, type **PowerShell**, and then click **Windows PowerShell**.</span></span>
- <span data-ttu-id="10fdc-113">Gelen **Başlat** menüsünde tıklayın **Başlat**, tıklayın **tüm programlar**, tıklayın **Donatılar**, tıklayın **Windows PowerShell**  klasörünü ve ardından **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="10fdc-113">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="10fdc-114">Komut isteminde</span><span class="sxs-lookup"><span data-stu-id="10fdc-114">At the Command Prompt</span></span>

<span data-ttu-id="10fdc-115">Windows PowerShell'i başlatmak için cmd.exe, Windows PowerShell veya Windows PowerShell ISE'yi yazın:</span><span class="sxs-lookup"><span data-stu-id="10fdc-115">In Cmd.exe, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

```
PowerShell
```

<span data-ttu-id="10fdc-116">PowerShell.exe program parametreleri oturum özelleştirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="10fdc-116">You can also use the parameters of the PowerShell.exe program to customize the session.</span></span> <span data-ttu-id="10fdc-117">Daha fazla bilgi için [PowerShell.exe komut satırı yardımcı](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).</span><span class="sxs-lookup"><span data-stu-id="10fdc-117">For more information, see [PowerShell.exe Command-Line Help](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).</span></span>

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="10fdc-118">("Yönetici olarak çalıştır") ile yönetim ayrıcalıkları</span><span class="sxs-lookup"><span data-stu-id="10fdc-118">With Administrative privileges ("Run as administrator")</span></span>

<span data-ttu-id="10fdc-119">Tıklayın **Başlat**, türü **PowerShell**, sağ **Windows PowerShell**ve ardından **yönetici olarak çalıştır**.</span><span class="sxs-lookup"><span data-stu-id="10fdc-119">Click **Start**, type **PowerShell**, right-click **Windows PowerShell**, and then click **Run as administrator**.</span></span>

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="10fdc-120">Önceki Windows sürümlerinde Windows PowerShell ISE'yi başlatma</span><span class="sxs-lookup"><span data-stu-id="10fdc-120">How to Start Windows PowerShell ISE on Earlier Releases of Windows</span></span>

<span data-ttu-id="10fdc-121">Windows PowerShell ISE'yi başlatmak için aşağıdaki yöntemlerden birini kullanın.</span><span class="sxs-lookup"><span data-stu-id="10fdc-121">Use any of the following methods to start Windows PowerShell ISE.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="10fdc-122">Başlat Menüsü'nden</span><span class="sxs-lookup"><span data-stu-id="10fdc-122">From the Start Menu</span></span>

- <span data-ttu-id="10fdc-123">Tıklayın **Başlat**, türü **ISE**ve ardından **Windows PowerShell ISE**.</span><span class="sxs-lookup"><span data-stu-id="10fdc-123">Click **Start**, type **ISE**, and then click **Windows PowerShell ISE**.</span></span>
- <span data-ttu-id="10fdc-124">Gelen **Başlat** menüsünde tıklayın **Başlat**, tıklayın **tüm programlar**, tıklayın **Donatılar**, tıklayın **Windows PowerShell**  klasörünü ve ardından **Windows PowerShell ISE**.</span><span class="sxs-lookup"><span data-stu-id="10fdc-124">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell ISE**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="10fdc-125">Komut isteminde</span><span class="sxs-lookup"><span data-stu-id="10fdc-125">At the Command Prompt</span></span>

<span data-ttu-id="10fdc-126">Windows PowerShell'i başlatmak için cmd.exe, Windows PowerShell veya Windows PowerShell ISE'yi yazın:</span><span class="sxs-lookup"><span data-stu-id="10fdc-126">In Cmd.exe, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

```
PowerShell_ISE
```

<span data-ttu-id="10fdc-127">veya</span><span class="sxs-lookup"><span data-stu-id="10fdc-127">or</span></span>

```
ISE
```

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="10fdc-128">("Yönetici olarak çalıştır") ile yönetim ayrıcalıkları</span><span class="sxs-lookup"><span data-stu-id="10fdc-128">With Administrative privileges ("Run as administrator")</span></span>

<span data-ttu-id="10fdc-129">Tıklayın **Başlat**, türü **ISE**, sağ **Windows PowerShell ISE**ve ardından **yönetici olarak çalıştır**.</span><span class="sxs-lookup"><span data-stu-id="10fdc-129">Click **Start**, type **ISE**, right-click **Windows PowerShell ISE**, and then click **Run as administrator**.</span></span>

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="10fdc-130">Önceki Windows sürümlerinde bulunan Windows PowerShell ISE etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="10fdc-130">How to Enable Windows PowerShell ISE on Earlier Releases of Windows</span></span>

<span data-ttu-id="10fdc-131">Windows PowerShell 4.0 ve Windows PowerShell 3.0, Windows PowerShell ISE tüm Windows sürümlerinde varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="10fdc-131">In Windows PowerShell 4.0 and Windows PowerShell 3.0, Windows PowerShell ISE is enabled by default on all versions of Windows.</span></span> <span data-ttu-id="10fdc-132">Zaten etkin değilse, Windows Management Framework 4.0 ya da Windows Management Framework 3.0 sağlar.</span><span class="sxs-lookup"><span data-stu-id="10fdc-132">If it is not already enabled, Windows Management Framework 4.0 or Windows Management Framework 3.0 enables it.</span></span>

<span data-ttu-id="10fdc-133">Windows PowerShell 2. 0 ', Windows PowerShell ISE, Windows 7 varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="10fdc-133">In Windows PowerShell 2.0, Windows PowerShell ISE is enabled by default on Windows 7.</span></span> <span data-ttu-id="10fdc-134">Ancak, Windows Server 2008 R2 ve Windows Server 2008 üzerinde isteğe bağlı bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="10fdc-134">However, on Windows Server 2008 R2 and Windows Server 2008, it is an optional feature.</span></span>

<span data-ttu-id="10fdc-135">Windows Server 2008 R2 veya Windows Server 2008'de Windows PowerShell 2.0 Windows PowerShell ISE'de etkinleştirmek için aşağıdaki yordamı kullanın.</span><span class="sxs-lookup"><span data-stu-id="10fdc-135">To enable Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server 2008 R2 or Windows Server 2008, use the following procedure.</span></span>

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="10fdc-136">Windows PowerShell Tümleşik komut dosyası ortamı (ISE) etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="10fdc-136">To enable Windows PowerShell Integrated Scripting Environment (ISE)</span></span>

1. <span data-ttu-id="10fdc-137">Sunucu Yöneticisi'ni başlatın.</span><span class="sxs-lookup"><span data-stu-id="10fdc-137">Start Server Manager.</span></span>
2. <span data-ttu-id="10fdc-138">Tıklayın **özellikleri** ve ardından **Özellik Ekle**.</span><span class="sxs-lookup"><span data-stu-id="10fdc-138">Click **Features** and then click **Add Features**.</span></span>
3. <span data-ttu-id="10fdc-139">Özellikleri, Windows PowerShell Tümleşik komut dosyası ortamı (ISE) tıklayın.</span><span class="sxs-lookup"><span data-stu-id="10fdc-139">In Select Features, click Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

## <a name="starting-the-32-bit-version-of-windows-powershell"></a><span data-ttu-id="10fdc-140">Windows PowerShell 32 Bit sürümünü başlatma</span><span class="sxs-lookup"><span data-stu-id="10fdc-140">Starting the 32-Bit Version of Windows PowerShell</span></span>

<span data-ttu-id="10fdc-141">Bir 64 bit bilgisayarda, Windows PowerShell yüklediğinizde **Windows PowerShell (x86)**, Windows PowerShell 32 bit sürümünü yanı sıra 64-bit sürümü yüklü.</span><span class="sxs-lookup"><span data-stu-id="10fdc-141">When you install Windows PowerShell on a 64-bit computer, **Windows PowerShell (x86)**, a 32-bit version of Windows PowerShell is installed in addition to the 64-bit version.</span></span> <span data-ttu-id="10fdc-142">Windows PowerShell çalıştırdığınızda, 64-bit sürümünü çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="10fdc-142">When you run Windows PowerShell, the 64-bit version runs by default.</span></span>

<span data-ttu-id="10fdc-143">Ancak, bazen çalıştırmak ihtiyacınız olabilecek **Windows PowerShell (x86)**, 32 bit sürümü gerektiren bir modülünü kullanıyorsanız, gibi veya bir 32 bit bilgisayar için uzaktan bağlantı kurduğunuzda.</span><span class="sxs-lookup"><span data-stu-id="10fdc-143">However, you might occasionally need to run **Windows PowerShell (x86)**, such as when you are using a module that requires the 32-bit version or when you are connecting remotely to a 32-bit computer.</span></span>

<span data-ttu-id="10fdc-144">Windows PowerShell 32 bit sürümünü başlatmak için aşağıdaki yordamlardan birini kullanın.</span><span class="sxs-lookup"><span data-stu-id="10fdc-144">To start a 32-bit version of Windows PowerShell, use any of the following procedures.</span></span>

#### <a name="in-windows-server-2012-r2"></a><span data-ttu-id="10fdc-145">In Windows Server® 2012 R2</span><span class="sxs-lookup"><span data-stu-id="10fdc-145">In Windows Server® 2012 R2</span></span>

- <span data-ttu-id="10fdc-146">Üzerinde **Başlat** ekranında, yazın **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="10fdc-146">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="10fdc-147">Tıklayın **Windows PowerShell x86** Döşe.</span><span class="sxs-lookup"><span data-stu-id="10fdc-147">Click the **Windows PowerShell x86** tile.</span></span>
- <span data-ttu-id="10fdc-148">İçinde **Sunucu Yöneticisi'ni**, gelen **Araçları** menüsünde **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="10fdc-148">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="10fdc-149">İmleç bölmenin sağ üst köşedeki için masaüstünde **arama**, türü **PowerShell x86** ve ardından **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="10fdc-149">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="10fdc-150">Komut satırı girin: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="10fdc-150">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-server-2012"></a><span data-ttu-id="10fdc-151">In Windows Server® 2012</span><span class="sxs-lookup"><span data-stu-id="10fdc-151">In Windows Server® 2012</span></span>

- <span data-ttu-id="10fdc-152">Üzerinde **Başlat** ekranında, yazın **PowerShell** ve ardından **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="10fdc-152">On the **Start** screen, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="10fdc-153">İçinde **Sunucu Yöneticisi'ni**, gelen **Araçları** menüsünde **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="10fdc-153">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="10fdc-154">İmleç bölmenin sağ üst köşedeki için masaüstünde **arama**, türü **PowerShell** ve ardından **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="10fdc-154">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="10fdc-155">Komut satırı girin: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="10fdc-155">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-81"></a><span data-ttu-id="10fdc-156">8.1 Windows® içinde</span><span class="sxs-lookup"><span data-stu-id="10fdc-156">In Windows® 8.1</span></span>

- <span data-ttu-id="10fdc-157">Üzerinde **Başlat** ekranında, yazın **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="10fdc-157">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="10fdc-158">Tıklayın **Windows PowerShell x86** Döşe.</span><span class="sxs-lookup"><span data-stu-id="10fdc-158">Click the **Windows PowerShell x86** tile.</span></span>
- <span data-ttu-id="10fdc-159">Çalıştırıyorsanız [Uzak Sunucu Yönetim Araçları](https://go.microsoft.com/fwlink/?LinkID=304145) Windows 8.1 için Windows Powershell'den x86 da açabilirsiniz **sunucu ManagerTools** menüsü.</span><span class="sxs-lookup"><span data-stu-id="10fdc-159">If you are running [Remote Server Administration Tools](https://go.microsoft.com/fwlink/?LinkID=304145) for Windows 8.1, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span>
  <span data-ttu-id="10fdc-160">Seçin **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="10fdc-160">Select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="10fdc-161">İmleç bölmenin sağ üst köşedeki için masaüstünde **arama**, türü **PowerShell x86** ve ardından **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="10fdc-161">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="10fdc-162">Komut satırı girin: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="10fdc-162">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-8"></a><span data-ttu-id="10fdc-163">8 Windows® içinde</span><span class="sxs-lookup"><span data-stu-id="10fdc-163">In Windows® 8</span></span>

- <span data-ttu-id="10fdc-164">Üzerinde **Başlat** ekranında, sağ üst köşedeki imleç, tıklayın **ayarları**, tıklayın **kutucukları**ve ardından taşıma **Yönetimsel Araçları Göster** kaydırıcı Evet.</span><span class="sxs-lookup"><span data-stu-id="10fdc-164">On the **Start** screen, move the cursor to the upper right corner, click **Settings**, click **Tiles**, and then move the **Show Administrative Tools** slider to Yes.</span></span> <span data-ttu-id="10fdc-165">Ardından yazın **PowerShell** tıklatıp **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="10fdc-165">Then, type **PowerShell** and click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="10fdc-166">Çalıştırıyorsanız [Uzak Sunucu Yönetim Araçları](https://www.microsoft.com/download/details.aspx?id=28972) Windows 8 için Windows Powershell'den x86 da açabilirsiniz **sunucu ManagerTools** menüsü.</span><span class="sxs-lookup"><span data-stu-id="10fdc-166">If you are running [Remote Server Administration Tools](https://www.microsoft.com/download/details.aspx?id=28972) for Windows 8, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="10fdc-167">Seçin **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="10fdc-167">Select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="10fdc-168">Üzerinde **Başlat** ekran veya yazın, Masaüstü **PowerShell (x86)** ve ardından **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="10fdc-168">On the **Start** screen or the desktop, type **PowerShell (x86)** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="10fdc-169">Komut satırı girin: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="10fdc-169">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>