---
ms.date: 2017-08-09
keywords: "PowerShell cmdlet, indirme, yükleme, Kurulum, windows 10, windows 8.1, windows 8.0, windows 7"
title: "Windows PowerShell Yükleme"
ms.openlocfilehash: dffb6ec11ce265ebc4e6bc91f631650e1af5868d
ms.sourcegitcommit: 05d576cf107780fa52b2db4a042816be40b00fbc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2018
---
# <a name="installing-windows-powershell"></a><span data-ttu-id="e7eb5-103">Windows PowerShell Yükleme</span><span class="sxs-lookup"><span data-stu-id="e7eb5-103">Installing Windows PowerShell</span></span>
<span data-ttu-id="e7eb5-104">Windows PowerShell, Windows 7 SP1 ve Windows Server 2008 R2 SP1 ile başlayarak, her Windows varsayılan olarak yüklü gelir.</span><span class="sxs-lookup"><span data-stu-id="e7eb5-104">Windows PowerShell comes installed by default in every Windows, starting with Windows 7 SP1 and Windows Server 2008 R2 SP1.</span></span>

<span data-ttu-id="e7eb5-105">PowerShell 6 ve üzeri ilgileniyorsanız, Windows PowerShell yerine PowerShell çekirdek yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e7eb5-105">If you are interested in PowerShell 6 and later, you need to install PowerShell Core instead of Windows PowerShell.</span></span> <span data-ttu-id="e7eb5-106">Bunun için bkz: [Windows PowerShell Çekirdeğinde yükleme](Installing-PowerShell-Core-on-Windows.md).</span><span class="sxs-lookup"><span data-stu-id="e7eb5-106">For that, see [Installing PowerShell Core on Windows](Installing-PowerShell-Core-on-Windows.md).</span></span>

## <a name="finding-powershell-in-windows-10-81-80-and-7"></a><span data-ttu-id="e7eb5-107">PowerShell Windows 10 ve 8.1, 8.0 ve 7 bulma</span><span class="sxs-lookup"><span data-stu-id="e7eb5-107">Finding PowerShell in Windows 10, 8.1, 8.0, and 7</span></span>

<span data-ttu-id="e7eb5-108">Cihazın konum bir Windows sürümünden diğerine taşır bazen PowerShell bulma konsolu veya Windows (tümleşik komut dosyası ortamı) işe zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="e7eb5-108">Sometimes locating PowerShell console or ISE (Integrated Scripting Environment) in Windows can be difficult, as it's location moves from one version of Windows to the next.</span></span>

<span data-ttu-id="e7eb5-109">Aşağıdaki tablolarda PowerShell, Windows sürümünde bulmanıza yardımcı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e7eb5-109">The following tables should help you find PowerShell in your Windows version.</span></span>
<span data-ttu-id="e7eb5-110">Burada listelenen tüm özgün sürümü, hiçbir güncelleştirme ile serbest bırakıldı sürümleridir.</span><span class="sxs-lookup"><span data-stu-id="e7eb5-110">All versions listed here are the original version, as released, with no updates.</span></span>

### <a name="for-console"></a><span data-ttu-id="e7eb5-111">Konsolu için</span><span class="sxs-lookup"><span data-stu-id="e7eb5-111">For Console</span></span>

<span data-ttu-id="e7eb5-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="e7eb5-112">Version</span></span> | <span data-ttu-id="e7eb5-113">Konum</span><span class="sxs-lookup"><span data-stu-id="e7eb5-113">Location</span></span>
-- | --
<span data-ttu-id="e7eb5-114">Windows 10</span><span class="sxs-lookup"><span data-stu-id="e7eb5-114">Windows 10</span></span> | <span data-ttu-id="e7eb5-115">Sol alt köşesindeki Windows simgesini tıklatın, PowerShell yazmaya başlayın</span><span class="sxs-lookup"><span data-stu-id="e7eb5-115">Click left lower corner Windows icon, start typing PowerShell</span></span>
<span data-ttu-id="e7eb5-116">Windows 8.1, 8.0</span><span class="sxs-lookup"><span data-stu-id="e7eb5-116">Windows 8.1, 8.0</span></span> | <span data-ttu-id="e7eb5-117">Başlangıç ekranında PowerShell yazmaya başlayın.</span><span class="sxs-lookup"><span data-stu-id="e7eb5-117">On the start screen, start typing PowerShell.</span></span><br/><span data-ttu-id="e7eb5-118">Masaüstünde varsa, sol alt köşesindeki Windows simgesini tıklatın, PowerShell yazmaya başlayın</span><span class="sxs-lookup"><span data-stu-id="e7eb5-118">If on desktop, click left lower corner Windows icon, start typing PowerShell</span></span>
<span data-ttu-id="e7eb5-119">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="e7eb5-119">Windows 7 SP1</span></span> | <span data-ttu-id="e7eb5-120">Sol alt köşesindeki Windows, PowerShell yazarak arama kutusu başlangıç simgesine</span><span class="sxs-lookup"><span data-stu-id="e7eb5-120">Click left lower corner Windows icon, on the search box start typing PowerShell</span></span>

### <a name="for-ise"></a><span data-ttu-id="e7eb5-121">ISE için</span><span class="sxs-lookup"><span data-stu-id="e7eb5-121">For ISE</span></span>

<span data-ttu-id="e7eb5-122">Sürüm</span><span class="sxs-lookup"><span data-stu-id="e7eb5-122">Version</span></span> | <span data-ttu-id="e7eb5-123">Konum</span><span class="sxs-lookup"><span data-stu-id="e7eb5-123">Location</span></span>
-- | --
<span data-ttu-id="e7eb5-124">Windows 10</span><span class="sxs-lookup"><span data-stu-id="e7eb5-124">Windows 10</span></span> | <span data-ttu-id="e7eb5-125">Sol alt köşesindeki Windows simgesini tıklatın, işe yazmaya başlayın</span><span class="sxs-lookup"><span data-stu-id="e7eb5-125">Click left lower corner Windows icon, start typing ISE</span></span>
<span data-ttu-id="e7eb5-126">Windows 8.1, 8.0</span><span class="sxs-lookup"><span data-stu-id="e7eb5-126">Windows 8.1, 8.0</span></span> | <span data-ttu-id="e7eb5-127">Başlangıç ekranında **PowerShell ISE**.</span><span class="sxs-lookup"><span data-stu-id="e7eb5-127">On the start screen, type **PowerShell ISE**.</span></span><br/><span data-ttu-id="e7eb5-128">Masaüstünde, alt köşe Windows simgesini tıklatın bırakılırsa yazın **PowerShell ISE**</span><span class="sxs-lookup"><span data-stu-id="e7eb5-128">If on desktop, click left lower corner Windows icon, type **PowerShell ISE**</span></span>
<span data-ttu-id="e7eb5-129">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="e7eb5-129">Windows 7 SP1</span></span> | <span data-ttu-id="e7eb5-130">Sol alt köşesindeki Windows, PowerShell yazarak arama kutusu başlangıç simgesine</span><span class="sxs-lookup"><span data-stu-id="e7eb5-130">Click left lower corner Windows icon, on the search box start typing PowerShell</span></span>

## <a name="finding-powershell-in-windows-server-versions"></a><span data-ttu-id="e7eb5-131">Windows Server sürümlerinde PowerShell bulma</span><span class="sxs-lookup"><span data-stu-id="e7eb5-131">Finding PowerShell in Windows Server versions</span></span>

<span data-ttu-id="e7eb5-132">Windows Server 2008 R2 ile başlayarak, Windows işletim sistemi grafik kullanıcı arabirimi (GUI) yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="e7eb5-132">Starting with Windows Server 2008 R2, Windows operating system can be installed without the graphical user interface (GUI).</span></span>
<span data-ttu-id="e7eb5-133">GUI olmadan Windows Server sürümleri adlı **çekirdek** ve GUI içeren sürümleri adlı **Masaüstü**.</span><span class="sxs-lookup"><span data-stu-id="e7eb5-133">Editions of Windows Server without GUI are named **Core** editions, and editions with the GUI are named **Desktop**.</span></span>

### <a name="windows-server-core-editions"></a><span data-ttu-id="e7eb5-134">Windows Server Core sürümleri</span><span class="sxs-lookup"><span data-stu-id="e7eb5-134">Windows Server Core editions</span></span>

<span data-ttu-id="e7eb5-135">Sunucuda oturum açtığınızda tüm çekirdeği sürümlerinde, bir Windows komut istemi penceresi olursunuz.</span><span class="sxs-lookup"><span data-stu-id="e7eb5-135">In all Core editions, when you log to the server you get a Windows command prompt window.</span></span>

<span data-ttu-id="e7eb5-136">Tür `powershell` ve basın **ENTER** PowerShell içinde komut istemi oturumu başlatmak için.</span><span class="sxs-lookup"><span data-stu-id="e7eb5-136">Type `powershell` and press **ENTER** to start PowerShell inside the command prompt session.</span></span> <span data-ttu-id="e7eb5-137">Tür `exit` PowerShell oturumu sona erdirmek ve komut istemine geri dönmek için.</span><span class="sxs-lookup"><span data-stu-id="e7eb5-137">Type `exit` to terminate the PowerShell session and return to command prompt.</span></span>

### <a name="windows-server-desktop-editions"></a><span data-ttu-id="e7eb5-138">Windows Server Masaüstü sürümleri</span><span class="sxs-lookup"><span data-stu-id="e7eb5-138">Windows Server Desktop editions</span></span>

<span data-ttu-id="e7eb5-139">Tüm masaüstü sürümlerinde, sol alt köşesindeki Windows simgesini tıklatın, PowerShell yazmaya başlayın.</span><span class="sxs-lookup"><span data-stu-id="e7eb5-139">In all desktop editions, click the left lower corner Windows icon, start typing PowerShell.</span></span>
<span data-ttu-id="e7eb5-140">Hem konsol hem de işe seçenekleri alın.</span><span class="sxs-lookup"><span data-stu-id="e7eb5-140">You get both console and ISE options.</span></span>

<span data-ttu-id="e7eb5-141">Yukarıdaki kuralın tek özel durum, Windows Server 2008 R2 SP1 işe olan; Bu durumda, sol alt köşesindeki Windows simgesini tıklatın, PowerShell ISE yazın.</span><span class="sxs-lookup"><span data-stu-id="e7eb5-141">The only exception to the above rule is the ISE in Windows Server 2008 R2 SP1; in this case, click the left lower corner Windows icon, type PowerShell ISE.</span></span>

## <a name="how-to-check-the-version-of-powershell"></a><span data-ttu-id="e7eb5-142">PowerShell sürümü denetleme</span><span class="sxs-lookup"><span data-stu-id="e7eb5-142">How to check the version of PowerShell</span></span>

<span data-ttu-id="e7eb5-143">PowerShell hangi sürümünün yüklü olduğunu bulmak için bir PowerShell konsolunda (veya ISE) başlatın ve türü `$PSVersionTable` ve basın **ENTER**.</span><span class="sxs-lookup"><span data-stu-id="e7eb5-143">To find which version of PowerShell you have installed, start a PowerShell console (or the ISE) and type `$PSVersionTable` and press **ENTER**.</span></span> <span data-ttu-id="e7eb5-144">Ara `PSVersion` değeri.</span><span class="sxs-lookup"><span data-stu-id="e7eb5-144">Look for the `PSVersion` value.</span></span>

## <a name="upgrading-existing-windows-powershell"></a><span data-ttu-id="e7eb5-145">Mevcut Windows PowerShell yükseltme</span><span class="sxs-lookup"><span data-stu-id="e7eb5-145">Upgrading existing Windows PowerShell</span></span>

<span data-ttu-id="e7eb5-146">PowerShell yükleme paketi WMF yükleyici içinde gelir.</span><span class="sxs-lookup"><span data-stu-id="e7eb5-146">The installation package for PowerShell comes inside a WMF installer.</span></span>
<span data-ttu-id="e7eb5-147">WMF yükleyici sürümü PowerShell sürümüyle eşleşen; Windows PowerShell için hiçbir tek başına yükleyici yoktur.</span><span class="sxs-lookup"><span data-stu-id="e7eb5-147">The version of the WMF installer matches the version of PowerShell; there's no stand alone installer for Windows PowerShell.</span></span>

<span data-ttu-id="e7eb5-148">Windows, aşağıdaki tabloda varolan PowerShell sürümünüz güncellemeniz gerekiyorsa için güncelleştirmek istediğiniz PowerShell sürümü için yükleyiciyi bulmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="e7eb5-148">If you need to update your existing version of PowerShell, in Windows, use the following table to locate the installer for the version of PowerShell you want to update to.</span></span>

<span data-ttu-id="e7eb5-149">Windows</span><span class="sxs-lookup"><span data-stu-id="e7eb5-149">Windows</span></span> | <span data-ttu-id="e7eb5-150">PS 3.0</span><span class="sxs-lookup"><span data-stu-id="e7eb5-150">PS 3.0</span></span> | <span data-ttu-id="e7eb5-151">PS 4.0</span><span class="sxs-lookup"><span data-stu-id="e7eb5-151">PS 4.0</span></span> | <span data-ttu-id="e7eb5-152">PS 5.0</span><span class="sxs-lookup"><span data-stu-id="e7eb5-152">PS 5.0</span></span> | <span data-ttu-id="e7eb5-153">PS 5.1</span><span class="sxs-lookup"><span data-stu-id="e7eb5-153">PS 5.1</span></span> |
--|--|--|--|--|
<span data-ttu-id="e7eb5-154">Windows 10 (Not1 bakın)</span><span class="sxs-lookup"><span data-stu-id="e7eb5-154">Windows 10 (see Note1)</span></span><br/><span data-ttu-id="e7eb5-155">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="e7eb5-155">Windows Server 2016</span></span> | - | - | - | <span data-ttu-id="e7eb5-156">yüklü</span><span class="sxs-lookup"><span data-stu-id="e7eb5-156">installed</span></span>
<span data-ttu-id="e7eb5-157">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="e7eb5-157">Windows 8.1</span></span><br/><span data-ttu-id="e7eb5-158">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="e7eb5-158">Windows Server 2012 R2</span></span> | - | <span data-ttu-id="e7eb5-159">yüklü</span><span class="sxs-lookup"><span data-stu-id="e7eb5-159">installed</span></span> | [<span data-ttu-id="e7eb5-160">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="e7eb5-160">WMF 5.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [<span data-ttu-id="e7eb5-161">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="e7eb5-161">WMF 5.1</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=54616)
<span data-ttu-id="e7eb5-162">Windows 8</span><span class="sxs-lookup"><span data-stu-id="e7eb5-162">Windows 8</span></span><br/><span data-ttu-id="e7eb5-163">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="e7eb5-163">Windows Server 2012</span></span> | <span data-ttu-id="e7eb5-164">yüklü</span><span class="sxs-lookup"><span data-stu-id="e7eb5-164">installed</span></span> | [<span data-ttu-id="e7eb5-165">WMF 4.0</span><span class="sxs-lookup"><span data-stu-id="e7eb5-165">WMF 4.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [<span data-ttu-id="e7eb5-166">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="e7eb5-166">WMF 5.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [<span data-ttu-id="e7eb5-167">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="e7eb5-167">WMF 5.1</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=54616)
<span data-ttu-id="e7eb5-168">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="e7eb5-168">Windows 7 SP1</span></span><br/><span data-ttu-id="e7eb5-169">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="e7eb5-169">Windows Server 2008 R2 SP1</span></span> | [<span data-ttu-id="e7eb5-170">WMF 3.0</span><span class="sxs-lookup"><span data-stu-id="e7eb5-170">WMF 3.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=34595) | [<span data-ttu-id="e7eb5-171">WMF 4.0</span><span class="sxs-lookup"><span data-stu-id="e7eb5-171">WMF 4.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [<span data-ttu-id="e7eb5-172">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="e7eb5-172">WMF 5.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [<span data-ttu-id="e7eb5-173">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="e7eb5-173">WMF 5.1</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=54616)

> <span data-ttu-id="e7eb5-174">**1 Not**:</span><span class="sxs-lookup"><span data-stu-id="e7eb5-174">**Note 1**:</span></span>
  >>
  >> <span data-ttu-id="e7eb5-175">İlk sürümünden Windows 10, etkin, Otomatik Güncelleştirmeler PowerShell 5.0 için 5.1 sürümünden güncelleştirilmesi.</span><span class="sxs-lookup"><span data-stu-id="e7eb5-175">On the initial release of Windows 10, with automatic updates enabled, PowerShell gets updated from version 5.0 to 5.1.</span></span>
  >>
  >> <span data-ttu-id="e7eb5-176">Windows 10 özgün sürümü aracılığıyla Windows güncelleştirmeleri güncelleştirilmezse PowerShell 5.0 sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="e7eb5-176">If the original version of Windows 10 is not updated through Windows Updates, the version of PowerShell is 5.0.</span></span>

## <a name="need-azure-powershell"></a><span data-ttu-id="e7eb5-177">Azure PowerShell gerekir</span><span class="sxs-lookup"><span data-stu-id="e7eb5-177">Need Azure PowerShell</span></span>

<span data-ttu-id="e7eb5-178">Arıyorsanız **Azure PowerShell**, ile başlayabilirsiniz [Azure PowerShell genel bakış](https://docs.microsoft.com/en-us/powershell/azure).</span><span class="sxs-lookup"><span data-stu-id="e7eb5-178">If you're looking for **Azure PowerShell**, you could start with [Overview of Azure PowerShell](https://docs.microsoft.com/en-us/powershell/azure).</span></span>

<span data-ttu-id="e7eb5-179">Aksi takdirde, gereksinim duyabileceğiniz değer [yükleyin ve Azure PowerShell yapılandırma](https://docs.microsoft.com/en-us/powershell/azure/install-azurerm-ps)</span><span class="sxs-lookup"><span data-stu-id="e7eb5-179">Otherwise, what you might need is [Install and configure Azure PowerShell](https://docs.microsoft.com/en-us/powershell/azure/install-azurerm-ps)</span></span>

## <a name="see-also"></a><span data-ttu-id="e7eb5-180">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="e7eb5-180">See Also</span></span>

- [<span data-ttu-id="e7eb5-181">Windows PowerShell sistem gereksinimleri</span><span class="sxs-lookup"><span data-stu-id="e7eb5-181">Windows PowerShell System Requirements</span></span>](Windows-PowerShell-System-Requirements.md)
- [<span data-ttu-id="e7eb5-182">Windows PowerShell'i başlatma</span><span class="sxs-lookup"><span data-stu-id="e7eb5-182">Starting Windows PowerShell</span></span>](Starting-Windows-PowerShell.md)
