---
ms.date: 2017-08-09
keywords: "PowerShell cmdlet, indirme, yükleme, Kurulum, windows 10, windows 8.1, windows 8.0, windows 7"
title: "Windows PowerShell'i yükleme"
ms.openlocfilehash: 781bf50b6ac649e72bcdbb708555275fb7422d94
ms.sourcegitcommit: 3720ce4efb6735694cfb53a1b793d949af5d1bc5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/29/2017
---
# <a name="installing-windows-powershell"></a><span data-ttu-id="441f2-103">Windows PowerShell'i yükleme</span><span class="sxs-lookup"><span data-stu-id="441f2-103">Installing Windows PowerShell</span></span>

<span data-ttu-id="441f2-104">PowerShell Windows 7 SP1 ve Windows Server 2008 R2 SP1 ile başlayarak, her Windows varsayılan olarak yüklenmiş olarak gelir.</span><span class="sxs-lookup"><span data-stu-id="441f2-104">PowerShell comes installed by default in every Windows, starting with Windows 7 SP1 and Windows Server 2008 R2 SP1.</span></span>

<span data-ttu-id="441f2-105">Yüklemek istediğiniz Linux, macOS ve Windows kullanıcıları **PowerShell 6** (beta), kendi makinelerine içinde gerekir:</span><span class="sxs-lookup"><span data-stu-id="441f2-105">Linux, macOS, and Windows users that would like to install **PowerShell 6** (beta), in their machines, need to:</span></span>

1. <span data-ttu-id="441f2-106">PowerShell belirli işletim sistemi ve sürümü için almanız [GitHub](https://github.com/powershell/powershell#get-powershell)</span><span class="sxs-lookup"><span data-stu-id="441f2-106">Get PowerShell for the specific OS and version, from [GitHub](https://github.com/powershell/powershell#get-powershell)</span></span>
1. <span data-ttu-id="441f2-107">Yükleme yönergelerini izleyin</span><span class="sxs-lookup"><span data-stu-id="441f2-107">Follow the installation instructions</span></span>
  - [<span data-ttu-id="441f2-108">Linux</span><span class="sxs-lookup"><span data-stu-id="441f2-108">Linux</span></span>](https://github.com/PowerShell/PowerShell/blob/master/docs/installation/linux.md)
  - [<span data-ttu-id="441f2-109">macOS</span><span class="sxs-lookup"><span data-stu-id="441f2-109">macOS</span></span>](https://github.com/PowerShell/PowerShell/blob/master/docs/installation/linux.md#macos-1012)
  - [<span data-ttu-id="441f2-110">Windows</span><span class="sxs-lookup"><span data-stu-id="441f2-110">Windows</span></span>](https://github.com/PowerShell/PowerShell/blob/master/docs/installation/windows.md#msi)

<span data-ttu-id="441f2-111">Ayrıca, Docker için PowerShell 6 kullanılabilir; bkz: [Docker yükleme](https://github.com/PowerShell/PowerShell/tree/master/docker) yönergeler.</span><span class="sxs-lookup"><span data-stu-id="441f2-111">PowerShell 6 is also available for Docker; see [Docker installation](https://github.com/PowerShell/PowerShell/tree/master/docker) instructions.</span></span>

## <a name="finding-powershell-in-windows-10-81-80-and-7"></a><span data-ttu-id="441f2-112">PowerShell Windows 10 ve 8.1, 8.0 ve 7 bulma</span><span class="sxs-lookup"><span data-stu-id="441f2-112">Finding PowerShell in Windows 10, 8.1, 8.0, and 7</span></span>

<span data-ttu-id="441f2-113">Cihazın konum bir Windows sürümünden diğerine taşır bazen PowerShell bulma konsolu veya Windows (tümleşik komut dosyası ortamı) işe zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="441f2-113">Sometimes locating PowerShell console or ISE (Integrated Scripting Environment) in Windows can be difficult, as it's location moves from one version of Windows to the next.</span></span>

<span data-ttu-id="441f2-114">Aşağıdaki tablolarda PowerShell, Windows sürümünde bulmanıza yardımcı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="441f2-114">The following tables should help you find PowerShell in your Windows version.</span></span>
<span data-ttu-id="441f2-115">Burada listelenen tüm özgün sürümü, hiçbir güncelleştirme ile serbest bırakıldı sürümleridir.</span><span class="sxs-lookup"><span data-stu-id="441f2-115">All versions listed here are the original version, as released, with no updates.</span></span>

### <a name="for-console"></a><span data-ttu-id="441f2-116">Konsolu için</span><span class="sxs-lookup"><span data-stu-id="441f2-116">For Console</span></span>

<span data-ttu-id="441f2-117">Sürüm</span><span class="sxs-lookup"><span data-stu-id="441f2-117">Version</span></span> | <span data-ttu-id="441f2-118">Konum</span><span class="sxs-lookup"><span data-stu-id="441f2-118">Location</span></span>
-- | --
<span data-ttu-id="441f2-119">Windows 10</span><span class="sxs-lookup"><span data-stu-id="441f2-119">Windows 10</span></span> | <span data-ttu-id="441f2-120">Sol alt köşesindeki Windows simgesini tıklatın, PowerShell yazmaya başlayın</span><span class="sxs-lookup"><span data-stu-id="441f2-120">Click left lower corner Windows icon, start typing PowerShell</span></span>
<span data-ttu-id="441f2-121">Windows 8.1, 8.0</span><span class="sxs-lookup"><span data-stu-id="441f2-121">Windows 8.1, 8.0</span></span> | <span data-ttu-id="441f2-122">Başlangıç ekranında PowerShell yazmaya başlayın.</span><span class="sxs-lookup"><span data-stu-id="441f2-122">On the start screen, start typing PowerShell.</span></span><br/><span data-ttu-id="441f2-123">Masaüstünde varsa, sol alt köşesindeki Windows simgesini tıklatın, PowerShell yazmaya başlayın</span><span class="sxs-lookup"><span data-stu-id="441f2-123">If on desktop, click left lower corner Windows icon, start typing PowerShell</span></span>
<span data-ttu-id="441f2-124">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="441f2-124">Windows 7 SP1</span></span> | <span data-ttu-id="441f2-125">Sol alt köşesindeki Windows, PowerShell yazarak arama kutusu başlangıç simgesine</span><span class="sxs-lookup"><span data-stu-id="441f2-125">Click left lower corner Windows icon, on the search box start typing PowerShell</span></span>

### <a name="for-ise"></a><span data-ttu-id="441f2-126">ISE için</span><span class="sxs-lookup"><span data-stu-id="441f2-126">For ISE</span></span>

<span data-ttu-id="441f2-127">Sürüm</span><span class="sxs-lookup"><span data-stu-id="441f2-127">Version</span></span> | <span data-ttu-id="441f2-128">Konum</span><span class="sxs-lookup"><span data-stu-id="441f2-128">Location</span></span>
-- | --
<span data-ttu-id="441f2-129">Windows 10</span><span class="sxs-lookup"><span data-stu-id="441f2-129">Windows 10</span></span> | <span data-ttu-id="441f2-130">Sol alt köşesindeki Windows simgesini tıklatın, işe yazmaya başlayın</span><span class="sxs-lookup"><span data-stu-id="441f2-130">Click left lower corner Windows icon, start typing ISE</span></span>
<span data-ttu-id="441f2-131">Windows 8.1, 8.0</span><span class="sxs-lookup"><span data-stu-id="441f2-131">Windows 8.1, 8.0</span></span> | <span data-ttu-id="441f2-132">Başlangıç ekranında **PowerShell ISE**.</span><span class="sxs-lookup"><span data-stu-id="441f2-132">On the start screen, type **PowerShell ISE**.</span></span><br/><span data-ttu-id="441f2-133">Masaüstünde, alt köşe Windows simgesini tıklatın bırakılırsa yazın **PowerShell ISE**</span><span class="sxs-lookup"><span data-stu-id="441f2-133">If on desktop, click left lower corner Windows icon, type **PowerShell ISE**</span></span>
<span data-ttu-id="441f2-134">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="441f2-134">Windows 7 SP1</span></span> | <span data-ttu-id="441f2-135">Sol alt köşesindeki Windows, PowerShell yazarak arama kutusu başlangıç simgesine</span><span class="sxs-lookup"><span data-stu-id="441f2-135">Click left lower corner Windows icon, on the search box start typing PowerShell</span></span>

## <a name="finding-powershell-in-windows-server-versions"></a><span data-ttu-id="441f2-136">Windows Server sürümlerinde PowerShell bulma</span><span class="sxs-lookup"><span data-stu-id="441f2-136">Finding PowerShell in Windows Server versions</span></span>

<span data-ttu-id="441f2-137">Windows Server 2008 R2 ile başlayarak, Windows işletim sistemi grafik kullanıcı arabirimi (GUI) yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="441f2-137">Starting with Windows Server 2008 R2, Windows operating system can be installed without the graphical user interface (GUI).</span></span>
<span data-ttu-id="441f2-138">GUI olmadan Windows Server sürümleri adlı **çekirdek** ve GUI içeren sürümleri adlı **Masaüstü**.</span><span class="sxs-lookup"><span data-stu-id="441f2-138">Editions of Windows Server without GUI are named **Core** editions, and editions with the GUI are named **Desktop**.</span></span>

### <a name="windows-server-core-editions"></a><span data-ttu-id="441f2-139">Windows Server Core sürümleri</span><span class="sxs-lookup"><span data-stu-id="441f2-139">Windows Server Core editions</span></span>

<span data-ttu-id="441f2-140">Sunucuda oturum açtığınızda tüm çekirdeği sürümlerinde, bir Windows komut istemi penceresi olursunuz.</span><span class="sxs-lookup"><span data-stu-id="441f2-140">In all Core editions, when you log to the server you get a Windows command prompt window.</span></span>

<span data-ttu-id="441f2-141">Tür `powershell` ve basın **ENTER** PowerShell içinde komut istemi oturumu başlatmak için.</span><span class="sxs-lookup"><span data-stu-id="441f2-141">Type `powershell` and press **ENTER** to start PowerShell inside the command prompt session.</span></span> <span data-ttu-id="441f2-142">Tür `exit` PowerShell oturumu sona erdirmek ve komut istemine geri dönmek için.</span><span class="sxs-lookup"><span data-stu-id="441f2-142">Type `exit` to terminate the PowerShell session and return to command prompt.</span></span>

### <a name="windows-server-desktop-editions"></a><span data-ttu-id="441f2-143">Windows Server Masaüstü sürümleri</span><span class="sxs-lookup"><span data-stu-id="441f2-143">Windows Server Desktop editions</span></span>

<span data-ttu-id="441f2-144">Tüm masaüstü sürümlerinde, sol alt köşesindeki Windows simgesini tıklatın, PowerShell yazmaya başlayın.</span><span class="sxs-lookup"><span data-stu-id="441f2-144">In all desktop editions, click the left lower corner Windows icon, start typing PowerShell.</span></span>
<span data-ttu-id="441f2-145">Hem konsol hem de işe seçenekleri alın.</span><span class="sxs-lookup"><span data-stu-id="441f2-145">You get both console and ISE options.</span></span>

<span data-ttu-id="441f2-146">Yukarıdaki kuralın tek özel durum, Windows Server 2008 R2 SP1 işe olan; Bu durumda, sol alt köşesindeki Windows simgesini tıklatın, PowerShell ISE yazın.</span><span class="sxs-lookup"><span data-stu-id="441f2-146">The only exception to the above rule is the ISE in Windows Server 2008 R2 SP1; in this case, click the left lower corner Windows icon, type PowerShell ISE.</span></span>

## <a name="how-to-check-the-version-of-powershell"></a><span data-ttu-id="441f2-147">PowerShell sürümü denetleme</span><span class="sxs-lookup"><span data-stu-id="441f2-147">How to check the version of PowerShell</span></span>

<span data-ttu-id="441f2-148">PowerShell hangi sürümünün yüklü olduğunu bulmak için bir PowerShell konsolunda (veya ISE) başlatın ve türü `$PSVersionTable` ve basın **ENTER**.</span><span class="sxs-lookup"><span data-stu-id="441f2-148">To find which version of PowerShell you have installed, start a PowerShell console (or the ISE) and type `$PSVersionTable` and press **ENTER**.</span></span>

## <a name="upgrading-existing-windows-powershell"></a><span data-ttu-id="441f2-149">Mevcut Windows PowerShell yükseltme</span><span class="sxs-lookup"><span data-stu-id="441f2-149">Upgrading existing Windows PowerShell</span></span>

<span data-ttu-id="441f2-150">PowerShell yükleme paketi WMF yükleyici içinde gelir.</span><span class="sxs-lookup"><span data-stu-id="441f2-150">The installation package for PowerShell comes inside a WMF installer.</span></span>
<span data-ttu-id="441f2-151">WMF yükleyici sürümü PowerShell sürümüyle eşleşen; Windows PowerShell için hiçbir tek başına yükleyici yoktur.</span><span class="sxs-lookup"><span data-stu-id="441f2-151">The version of the WMF installer matches the version of PowerShell; there's no stand alone installer for Windows PowerShell.</span></span>

<span data-ttu-id="441f2-152">Windows, aşağıdaki tabloda varolan PowerShell sürümünüz güncellemeniz gerekiyorsa için güncelleştirmek istediğiniz PowerShell sürümü için yükleyiciyi bulmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="441f2-152">If you need to update your existing version of PowerShell, in Windows, use the following table to locate the installer for the version of PowerShell you want to update to.</span></span>

<span data-ttu-id="441f2-153">Windows</span><span class="sxs-lookup"><span data-stu-id="441f2-153">Windows</span></span> | <span data-ttu-id="441f2-154">PS 3.0</span><span class="sxs-lookup"><span data-stu-id="441f2-154">PS 3.0</span></span> | <span data-ttu-id="441f2-155">PS 4.0</span><span class="sxs-lookup"><span data-stu-id="441f2-155">PS 4.0</span></span> | <span data-ttu-id="441f2-156">PS 5.0</span><span class="sxs-lookup"><span data-stu-id="441f2-156">PS 5.0</span></span> | <span data-ttu-id="441f2-157">PS 5.1</span><span class="sxs-lookup"><span data-stu-id="441f2-157">PS 5.1</span></span> |
--|--|--|--|--|
<span data-ttu-id="441f2-158">Windows 10 (Not1 bakın)</span><span class="sxs-lookup"><span data-stu-id="441f2-158">Windows 10 (see Note1)</span></span><br/><span data-ttu-id="441f2-159">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="441f2-159">Windows Server 2016</span></span> | - | - | - | <span data-ttu-id="441f2-160">yüklü</span><span class="sxs-lookup"><span data-stu-id="441f2-160">installed</span></span>
<span data-ttu-id="441f2-161">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="441f2-161">Windows 8.1</span></span><br/><span data-ttu-id="441f2-162">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="441f2-162">Windows Server 2012 R2</span></span> | - | <span data-ttu-id="441f2-163">yüklü</span><span class="sxs-lookup"><span data-stu-id="441f2-163">installed</span></span> | [<span data-ttu-id="441f2-164">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="441f2-164">WMF 5.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [<span data-ttu-id="441f2-165">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="441f2-165">WMF 5.1</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=54616)
<span data-ttu-id="441f2-166">Windows 8</span><span class="sxs-lookup"><span data-stu-id="441f2-166">Windows 8</span></span><br/><span data-ttu-id="441f2-167">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="441f2-167">Windows Server 2012</span></span> | <span data-ttu-id="441f2-168">yüklü</span><span class="sxs-lookup"><span data-stu-id="441f2-168">installed</span></span> | [<span data-ttu-id="441f2-169">WMF 4.0</span><span class="sxs-lookup"><span data-stu-id="441f2-169">WMF 4.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [<span data-ttu-id="441f2-170">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="441f2-170">WMF 5.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [<span data-ttu-id="441f2-171">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="441f2-171">WMF 5.1</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=54616)
<span data-ttu-id="441f2-172">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="441f2-172">Windows 7 SP1</span></span><br/><span data-ttu-id="441f2-173">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="441f2-173">Windows Server 2008 R2 SP1</span></span> | [<span data-ttu-id="441f2-174">WMF 3.0</span><span class="sxs-lookup"><span data-stu-id="441f2-174">WMF 3.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=34595) | [<span data-ttu-id="441f2-175">WMF 4.0</span><span class="sxs-lookup"><span data-stu-id="441f2-175">WMF 4.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [<span data-ttu-id="441f2-176">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="441f2-176">WMF 5.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [<span data-ttu-id="441f2-177">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="441f2-177">WMF 5.1</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=54616)

> <span data-ttu-id="441f2-178">**1 Not**:</span><span class="sxs-lookup"><span data-stu-id="441f2-178">**Note 1**:</span></span>
  >>
  >> <span data-ttu-id="441f2-179">İlk sürümünden Windows 10, etkin, Otomatik Güncelleştirmeler PowerShell 5.0 için 5.1 sürümünden güncelleştirilmesi.</span><span class="sxs-lookup"><span data-stu-id="441f2-179">On the initial release of Windows 10, with automatic updates enabled, PowerShell gets updated from version 5.0 to 5.1.</span></span>
  >>
  >> <span data-ttu-id="441f2-180">Windows 10 özgün sürümü aracılığıyla Windows güncelleştirmeleri güncelleştirilmezse PowerShell 5.0 sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="441f2-180">If the original version of Windows 10 is not updated through Windows Updates, the version of PowerShell is 5.0.</span></span>

## <a name="need-azure-powershell"></a><span data-ttu-id="441f2-181">Azure PowerShell gerekir</span><span class="sxs-lookup"><span data-stu-id="441f2-181">Need Azure PowerShell</span></span>

<span data-ttu-id="441f2-182">Arıyorsanız **Azure PowerShell**, ile başlayabilirsiniz [Azure PowerShell genel bakış](https://docs.microsoft.com/en-us/powershell/azure).</span><span class="sxs-lookup"><span data-stu-id="441f2-182">If you're looking for **Azure PowerShell**, you could start with [Overview of Azure PowerShell](https://docs.microsoft.com/en-us/powershell/azure).</span></span>

<span data-ttu-id="441f2-183">Aksi takdirde, gereksinim duyabileceğiniz değer [yükleyin ve Azure PowerShell yapılandırma](https://docs.microsoft.com/en-us/powershell/azure/install-azurerm-ps)</span><span class="sxs-lookup"><span data-stu-id="441f2-183">Otherwise, what you might need is [Install and configure Azure PowerShell](https://docs.microsoft.com/en-us/powershell/azure/install-azurerm-ps)</span></span>

## <a name="see-also"></a><span data-ttu-id="441f2-184">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="441f2-184">See Also</span></span>

- [<span data-ttu-id="441f2-185">Windows PowerShell sistem gereksinimleri</span><span class="sxs-lookup"><span data-stu-id="441f2-185">Windows PowerShell System Requirements</span></span>](Windows-PowerShell-System-Requirements.md)
- [<span data-ttu-id="441f2-186">Windows PowerShell'i başlatma</span><span class="sxs-lookup"><span data-stu-id="441f2-186">Starting Windows PowerShell</span></span>](Starting-Windows-PowerShell.md)
