---
ms.date: 08/09/2017
keywords: PowerShell cmdlet'i, indirme, yükleme, Kurulum, windows 10, windows 8.1, windows 8.0, windows 7
title: Windows PowerShell Yükleme
ms.openlocfilehash: 1630ba445c88953b2729232ae7d80afa326f25e6
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405770"
---
# <a name="installing-windows-powershell"></a><span data-ttu-id="00d59-103">Windows PowerShell Yükleme</span><span class="sxs-lookup"><span data-stu-id="00d59-103">Installing Windows PowerShell</span></span>

<span data-ttu-id="00d59-104">Windows PowerShell varsayılan olarak Windows 7 SP1 ve Windows Server 2008 R2 SP1 ile başlayarak, her Windows yüklenmiş olarak sunulur.</span><span class="sxs-lookup"><span data-stu-id="00d59-104">Windows PowerShell comes installed by default in every Windows, starting with Windows 7 SP1 and Windows Server 2008 R2 SP1.</span></span>

<span data-ttu-id="00d59-105">PowerShell 6 ve üzeri ilgileniyorsanız, PowerShell Core yerine Windows PowerShell yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="00d59-105">If you are interested in PowerShell 6 and later, you need to install PowerShell Core instead of Windows PowerShell.</span></span> <span data-ttu-id="00d59-106">Bunun için bkz. [üzerinde Windows PowerShell Core yükleme](Installing-PowerShell-Core-on-Windows.md).</span><span class="sxs-lookup"><span data-stu-id="00d59-106">For that, see [Installing PowerShell Core on Windows](Installing-PowerShell-Core-on-Windows.md).</span></span>

## <a name="finding-powershell-in-windows-10-81-80-and-7"></a><span data-ttu-id="00d59-107">PowerShell, Windows 10 ve 8.1, 8.0 ve 7 bulma</span><span class="sxs-lookup"><span data-stu-id="00d59-107">Finding PowerShell in Windows 10, 8.1, 8.0, and 7</span></span>

<span data-ttu-id="00d59-108">Konumu bir Windows sürümünden diğerine taşınırken bazen PowerShell bulma konsolu veya Windows (tümleşik komut dosyası ortamı) ISE'de zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="00d59-108">Sometimes locating PowerShell console or ISE (Integrated Scripting Environment) in Windows can be difficult, as it's location moves from one version of Windows to the next.</span></span>

<span data-ttu-id="00d59-109">Aşağıdaki tablolarda, PowerShell, Windows sürümünde bulmanıza yardımcı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="00d59-109">The following tables should help you find PowerShell in your Windows version.</span></span>
<span data-ttu-id="00d59-110">Burada listelenen tüm özgün sürümle, hiçbir güncelleştirme ile serbest bırakıldı sürümleridir.</span><span class="sxs-lookup"><span data-stu-id="00d59-110">All versions listed here are the original version, as released, with no updates.</span></span>

### <a name="for-console"></a><span data-ttu-id="00d59-111">Konsolu için</span><span class="sxs-lookup"><span data-stu-id="00d59-111">For Console</span></span>

<span data-ttu-id="00d59-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="00d59-112">Version</span></span> | <span data-ttu-id="00d59-113">Konum</span><span class="sxs-lookup"><span data-stu-id="00d59-113">Location</span></span>
-- | --
<span data-ttu-id="00d59-114">Windows 10</span><span class="sxs-lookup"><span data-stu-id="00d59-114">Windows 10</span></span> | <span data-ttu-id="00d59-115">Sol alt köşedeki Windows simgesine tıklayın, PowerShell yazmaya başlayın</span><span class="sxs-lookup"><span data-stu-id="00d59-115">Click left lower corner Windows icon, start typing PowerShell</span></span>
<span data-ttu-id="00d59-116">Windows 8.1, 8.0</span><span class="sxs-lookup"><span data-stu-id="00d59-116">Windows 8.1, 8.0</span></span> | <span data-ttu-id="00d59-117">Başlangıç ekranında, PowerShell yazmaya başlayın.</span><span class="sxs-lookup"><span data-stu-id="00d59-117">On the start screen, start typing PowerShell.</span></span><br/><span data-ttu-id="00d59-118">Masaüstünde varsa, sol alt köşedeki Windows simgesine tıklayın, PowerShell yazmaya başlayın</span><span class="sxs-lookup"><span data-stu-id="00d59-118">If on desktop, click left lower corner Windows icon, start typing PowerShell</span></span>
<span data-ttu-id="00d59-119">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="00d59-119">Windows 7 SP1</span></span> | <span data-ttu-id="00d59-120">Sol alt köşedeki Windows simgesine, PowerShell yazarak arama kutusunun başlangıç tıklayın</span><span class="sxs-lookup"><span data-stu-id="00d59-120">Click left lower corner Windows icon, on the search box start typing PowerShell</span></span>

### <a name="for-ise"></a><span data-ttu-id="00d59-121">ISE için</span><span class="sxs-lookup"><span data-stu-id="00d59-121">For ISE</span></span>

<span data-ttu-id="00d59-122">Sürüm</span><span class="sxs-lookup"><span data-stu-id="00d59-122">Version</span></span> | <span data-ttu-id="00d59-123">Konum</span><span class="sxs-lookup"><span data-stu-id="00d59-123">Location</span></span>
-- | --
<span data-ttu-id="00d59-124">Windows 10</span><span class="sxs-lookup"><span data-stu-id="00d59-124">Windows 10</span></span> | <span data-ttu-id="00d59-125">Sol alt köşedeki Windows simgesine tıklayın, işe yazmaya başlayın</span><span class="sxs-lookup"><span data-stu-id="00d59-125">Click left lower corner Windows icon, start typing ISE</span></span>
<span data-ttu-id="00d59-126">Windows 8.1, 8.0</span><span class="sxs-lookup"><span data-stu-id="00d59-126">Windows 8.1, 8.0</span></span> | <span data-ttu-id="00d59-127">Başlangıç ekranında **PowerShell ISE**.</span><span class="sxs-lookup"><span data-stu-id="00d59-127">On the start screen, type **PowerShell ISE**.</span></span><br/><span data-ttu-id="00d59-128">Masaüstünde, alt köşe Windows simgesine tıklayın bırakılırsa yazın **PowerShell ISE**</span><span class="sxs-lookup"><span data-stu-id="00d59-128">If on desktop, click left lower corner Windows icon, type **PowerShell ISE**</span></span>
<span data-ttu-id="00d59-129">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="00d59-129">Windows 7 SP1</span></span> | <span data-ttu-id="00d59-130">Sol alt köşedeki Windows simgesine, PowerShell yazarak arama kutusunun başlangıç tıklayın</span><span class="sxs-lookup"><span data-stu-id="00d59-130">Click left lower corner Windows icon, on the search box start typing PowerShell</span></span>

## <a name="finding-powershell-in-windows-server-versions"></a><span data-ttu-id="00d59-131">PowerShell, Windows Server sürümlerinde bulma</span><span class="sxs-lookup"><span data-stu-id="00d59-131">Finding PowerShell in Windows Server versions</span></span>

<span data-ttu-id="00d59-132">Windows Server 2008 R2 ile başlayarak, Windows işletim sistemi grafik kullanıcı arabirimi (GUI) yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="00d59-132">Starting with Windows Server 2008 R2, Windows operating system can be installed without the graphical user interface (GUI).</span></span>
<span data-ttu-id="00d59-133">GUI içermeyen Windows Server sürümlerini adlı **çekirdek** ve GUI içeren sunucu sürümleri adlı **Masaüstü**.</span><span class="sxs-lookup"><span data-stu-id="00d59-133">Editions of Windows Server without GUI are named **Core** editions, and editions with the GUI are named **Desktop**.</span></span>

### <a name="windows-server-core-editions"></a><span data-ttu-id="00d59-134">Windows Server Core sürümleri</span><span class="sxs-lookup"><span data-stu-id="00d59-134">Windows Server Core editions</span></span>

<span data-ttu-id="00d59-135">Sunucuda oturum açtığında tüm çekirdeği sürümlerinde, bir Windows komut istemi penceresi alırsınız.</span><span class="sxs-lookup"><span data-stu-id="00d59-135">In all Core editions, when you log to the server you get a Windows command prompt window.</span></span>

<span data-ttu-id="00d59-136">Tür `powershell` basın **ENTER** PowerShell içinde komut istemi oturumu başlatmak için.</span><span class="sxs-lookup"><span data-stu-id="00d59-136">Type `powershell` and press **ENTER** to start PowerShell inside the command prompt session.</span></span>
<span data-ttu-id="00d59-137">Tür `exit` PowerShell oturumu sona erdirmek ve komut istemine dönün.</span><span class="sxs-lookup"><span data-stu-id="00d59-137">Type `exit` to terminate the PowerShell session and return to command prompt.</span></span>

### <a name="windows-server-desktop-editions"></a><span data-ttu-id="00d59-138">Windows Server Masaüstü sürümleri</span><span class="sxs-lookup"><span data-stu-id="00d59-138">Windows Server Desktop editions</span></span>

<span data-ttu-id="00d59-139">Tüm masaüstü sürümlerinde, sol alt köşedeki Windows simgesine tıklayın, PowerShell yazmaya başlayın.</span><span class="sxs-lookup"><span data-stu-id="00d59-139">In all desktop editions, click the left lower corner Windows icon, start typing PowerShell.</span></span>
<span data-ttu-id="00d59-140">Hem konsol hem de ISE seçenekler olursunuz.</span><span class="sxs-lookup"><span data-stu-id="00d59-140">You get both console and ISE options.</span></span>

<span data-ttu-id="00d59-141">Windows Server 2008 R2 SP1 ISE'de yukarıdaki kuralın tek özel durumu olan; Bu durumda, sol alt köşedeki Windows simgesine tıklayın, PowerShell ISE yazın.</span><span class="sxs-lookup"><span data-stu-id="00d59-141">The only exception to the above rule is the ISE in Windows Server 2008 R2 SP1; in this case, click the left lower corner Windows icon, type PowerShell ISE.</span></span>

## <a name="how-to-check-the-version-of-powershell"></a><span data-ttu-id="00d59-142">PowerShell sürümünü denetleme</span><span class="sxs-lookup"><span data-stu-id="00d59-142">How to check the version of PowerShell</span></span>

<span data-ttu-id="00d59-143">Hangi PowerShell sürümünü yüklediğiniz bulmak için bir PowerShell Konsolu (veya ISE) başlatın ve türü `$PSVersionTable` basın **ENTER**.</span><span class="sxs-lookup"><span data-stu-id="00d59-143">To find which version of PowerShell you have installed, start a PowerShell console (or the ISE) and type `$PSVersionTable` and press **ENTER**.</span></span> <span data-ttu-id="00d59-144">Aranacak `PSVersion` değeri.</span><span class="sxs-lookup"><span data-stu-id="00d59-144">Look for the `PSVersion` value.</span></span>

## <a name="upgrading-existing-windows-powershell"></a><span data-ttu-id="00d59-145">Mevcut Windows PowerShell yükseltme</span><span class="sxs-lookup"><span data-stu-id="00d59-145">Upgrading existing Windows PowerShell</span></span>

<span data-ttu-id="00d59-146">PowerShell yükleme paketi bir WMF yükleyici gelir.</span><span class="sxs-lookup"><span data-stu-id="00d59-146">The installation package for PowerShell comes inside a WMF installer.</span></span>
<span data-ttu-id="00d59-147">WMF yükleyicisinin sürümünü PowerShell sürümüyle eşleşmiyor; Windows PowerShell için tek başına yükleyici yok yoktur.</span><span class="sxs-lookup"><span data-stu-id="00d59-147">The version of the WMF installer matches the version of PowerShell; there's no stand alone installer for Windows PowerShell.</span></span>

<span data-ttu-id="00d59-148">Mevcut PowerShell sürümünüz güncelleştirmeniz gerekiyorsa Windows, yükleyici için güncelleştirmek istediğiniz PowerShell sürümü bulmak için aşağıdaki tabloyu kullanın.</span><span class="sxs-lookup"><span data-stu-id="00d59-148">If you need to update your existing version of PowerShell, in Windows, use the following table to locate the installer for the version of PowerShell you want to update to.</span></span>

<span data-ttu-id="00d59-149">Windows</span><span class="sxs-lookup"><span data-stu-id="00d59-149">Windows</span></span> | <span data-ttu-id="00d59-150">PS 3.0</span><span class="sxs-lookup"><span data-stu-id="00d59-150">PS 3.0</span></span> | <span data-ttu-id="00d59-151">PS 4.0</span><span class="sxs-lookup"><span data-stu-id="00d59-151">PS 4.0</span></span> | <span data-ttu-id="00d59-152">PS 5.0</span><span class="sxs-lookup"><span data-stu-id="00d59-152">PS 5.0</span></span> | <span data-ttu-id="00d59-153">PS 5.1</span><span class="sxs-lookup"><span data-stu-id="00d59-153">PS 5.1</span></span> |
--|--|--|--|--|
<span data-ttu-id="00d59-154">Windows 10 (Note1 bakın)</span><span class="sxs-lookup"><span data-stu-id="00d59-154">Windows 10 (see Note1)</span></span><br/><span data-ttu-id="00d59-155">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="00d59-155">Windows Server 2016</span></span> | - | - | - | <span data-ttu-id="00d59-156">yüklü</span><span class="sxs-lookup"><span data-stu-id="00d59-156">installed</span></span>
<span data-ttu-id="00d59-157">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="00d59-157">Windows 8.1</span></span><br/><span data-ttu-id="00d59-158">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="00d59-158">Windows Server 2012 R2</span></span> | - | <span data-ttu-id="00d59-159">yüklü</span><span class="sxs-lookup"><span data-stu-id="00d59-159">installed</span></span> | [<span data-ttu-id="00d59-160">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="00d59-160">WMF 5.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [<span data-ttu-id="00d59-161">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="00d59-161">WMF 5.1</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=54616)
<span data-ttu-id="00d59-162">Windows 8</span><span class="sxs-lookup"><span data-stu-id="00d59-162">Windows 8</span></span><br/><span data-ttu-id="00d59-163">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="00d59-163">Windows Server 2012</span></span> | <span data-ttu-id="00d59-164">yüklü</span><span class="sxs-lookup"><span data-stu-id="00d59-164">installed</span></span> | [<span data-ttu-id="00d59-165">WMF 4.0</span><span class="sxs-lookup"><span data-stu-id="00d59-165">WMF 4.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [<span data-ttu-id="00d59-166">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="00d59-166">WMF 5.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [<span data-ttu-id="00d59-167">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="00d59-167">WMF 5.1</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=54616)
<span data-ttu-id="00d59-168">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="00d59-168">Windows 7 SP1</span></span><br/><span data-ttu-id="00d59-169">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="00d59-169">Windows Server 2008 R2 SP1</span></span> | [<span data-ttu-id="00d59-170">WMF 3.0</span><span class="sxs-lookup"><span data-stu-id="00d59-170">WMF 3.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=34595) | [<span data-ttu-id="00d59-171">WMF 4.0</span><span class="sxs-lookup"><span data-stu-id="00d59-171">WMF 4.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [<span data-ttu-id="00d59-172">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="00d59-172">WMF 5.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [<span data-ttu-id="00d59-173">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="00d59-173">WMF 5.1</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=54616)

> [!NOTE]
>
> <span data-ttu-id="00d59-174">Etkin, otomatik güncelleştirmeleri ile Windows 10'in ilk sürümünden üzerindeki PowerShell 5.0 için 5.1 sürümünden güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="00d59-174">On the initial release of Windows 10, with automatic updates enabled, PowerShell gets updated from version 5.0 to 5.1.</span></span>
>
> <span data-ttu-id="00d59-175">Orijinal Windows 10 sürümünü aracılığıyla Windows güncelleştirmelerini güncelleştirilmezse, PowerShell 5.0 sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="00d59-175">If the original version of Windows 10 is not updated through Windows Updates, the version of PowerShell is 5.0.</span></span>

## <a name="need-azure-powershell"></a><span data-ttu-id="00d59-176">Azure PowerShell olması gerekir</span><span class="sxs-lookup"><span data-stu-id="00d59-176">Need Azure PowerShell</span></span>

<span data-ttu-id="00d59-177">Aradığınız varsa **Azure PowerShell**, ile başlatabilir [genel bakış, Azure PowerShell](/powershell/azure/overview).</span><span class="sxs-lookup"><span data-stu-id="00d59-177">If you're looking for **Azure PowerShell**, you could start with [Overview of Azure PowerShell](/powershell/azure/overview).</span></span>

<span data-ttu-id="00d59-178">Aksi takdirde, gerek duyabileceğiniz olduğu [yüklemek ve Azure PowerShell yapılandırma](/powershell/azure/install-azurerm-ps)</span><span class="sxs-lookup"><span data-stu-id="00d59-178">Otherwise, what you might need is [Install and configure Azure PowerShell](/powershell/azure/install-azurerm-ps)</span></span>

## <a name="see-also"></a><span data-ttu-id="00d59-179">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="00d59-179">See Also</span></span>

[<span data-ttu-id="00d59-180">Windows PowerShell sistem gereksinimleri</span><span class="sxs-lookup"><span data-stu-id="00d59-180">Windows PowerShell System Requirements</span></span>](Windows-PowerShell-System-Requirements.md)

[<span data-ttu-id="00d59-181">Windows PowerShell'i başlatma</span><span class="sxs-lookup"><span data-stu-id="00d59-181">Starting Windows PowerShell</span></span>](../getting-started/Starting-Windows-PowerShell.md)