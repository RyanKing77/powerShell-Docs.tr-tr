---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
contributor: keithb
title: Yükleme ve WMF 5.1 yapılandırma
ms.openlocfilehash: e747487873c7c15c2bea3fca7136630ab2b572f7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="install-and-configure-wmf-51"></a><span data-ttu-id="1b062-103">Yükleme ve WMF 5.1 yapılandırma</span><span class="sxs-lookup"><span data-stu-id="1b062-103">Install and Configure WMF 5.1</span></span> #


## <a name="download-and-install-the-wmf-51-package"></a><span data-ttu-id="1b062-104">WMF 5.1 paketini indirin ve yükleyin</span><span class="sxs-lookup"><span data-stu-id="1b062-104">Download and install the WMF 5.1 package</span></span>

<span data-ttu-id="1b062-105">Yüklemek istediğiniz işletim sistemi ve mimarisi için WMF 5.1 paketini indirin:</span><span class="sxs-lookup"><span data-stu-id="1b062-105">Download the WMF 5.1 package for the operating system and architecture you wish to install it on:</span></span>

| <span data-ttu-id="1b062-106">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="1b062-106">Operating System</span></span>       | <span data-ttu-id="1b062-107">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="1b062-107">Prerequisites</span></span>           | <span data-ttu-id="1b062-108">Paket bağlantılar</span><span class="sxs-lookup"><span data-stu-id="1b062-108">Package Links</span></span>                          |
|------------------------|-------------------------|----------------------------------------|
| <span data-ttu-id="1b062-109">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="1b062-109">Windows Server 2012 R2</span></span> |                         | <span data-ttu-id="1b062-110">[Win8.1AndW2K12R2-KB3191564-x64.msu][]</span><span class="sxs-lookup"><span data-stu-id="1b062-110">[Win8.1AndW2K12R2-KB3191564-x64.msu][]</span></span> |
| <span data-ttu-id="1b062-111">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="1b062-111">Windows Server 2012</span></span>    |                         | <span data-ttu-id="1b062-112">[W2K12-KB3191565-x64.msu][]</span><span class="sxs-lookup"><span data-stu-id="1b062-112">[W2K12-KB3191565-x64.msu][]</span></span>            |
| <span data-ttu-id="1b062-113">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="1b062-113">Windows Server 2008 R2</span></span> | <span data-ttu-id="1b062-114">[.NET Framework 4.5.2][]</span><span class="sxs-lookup"><span data-stu-id="1b062-114">[.NET Framework 4.5.2][]</span></span>| <span data-ttu-id="1b062-115">[Win7AndW2K8R2-KB3191566-x64.ZIP][]</span><span class="sxs-lookup"><span data-stu-id="1b062-115">[Win7AndW2K8R2-KB3191566-x64.ZIP][]</span></span>    |
| <span data-ttu-id="1b062-116">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="1b062-116">Windows 8.1</span></span>            |                         | <span data-ttu-id="1b062-117">**x64:** [Win8.1AndW2K12R2-KB3191564-x64.msu][]</span><span class="sxs-lookup"><span data-stu-id="1b062-117">**x64:** [Win8.1AndW2K12R2-KB3191564-x64.msu][]</span></span></br><span data-ttu-id="1b062-118">**x86:** [Win8.1-KB3191564-x86.msu][]</span><span class="sxs-lookup"><span data-stu-id="1b062-118">**x86:** [Win8.1-KB3191564-x86.msu][]</span></span> |
| <span data-ttu-id="1b062-119">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="1b062-119">Windows 7 SP1</span></span>          | <span data-ttu-id="1b062-120">[.NET Framework 4.5.2][]</span><span class="sxs-lookup"><span data-stu-id="1b062-120">[.NET Framework 4.5.2][]</span></span>| <span data-ttu-id="1b062-121">**x64:** [Win7AndW2K8R2-KB3191566-x64.ZIP][]</span><span class="sxs-lookup"><span data-stu-id="1b062-121">**x64:** [Win7AndW2K8R2-KB3191566-x64.ZIP][]</span></span></br><span data-ttu-id="1b062-122">**x86:** [Win7-KB3191566-x86.ZIP][]</span><span class="sxs-lookup"><span data-stu-id="1b062-122">**x86:** [Win7-KB3191566-x86.ZIP][]</span></span> |

[.NET Framework 4.5.2]: https://www.microsoft.com/download/details.aspx?id=42642
[W2K12-KB3191565-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839513
[Win7-KB3191566-x86.ZIP]: https://go.microsoft.com/fwlink/?linkid=839522
[Win7AndW2K8R2-KB3191566-x64.ZIP]: https://go.microsoft.com/fwlink/?linkid=839523
[Win8.1-KB3191564-x86.msu]: https://go.microsoft.com/fwlink/?linkid=839521
[Win8.1AndW2K12R2-KB3191564-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839516

## <a name="install-wmf-51-for-windows-server-2008-r2-and-windows-7"></a><span data-ttu-id="1b062-129">Windows Server 2008 R2 ve Windows 7 için WMF 5.1 yükleyin</span><span class="sxs-lookup"><span data-stu-id="1b062-129">Install WMF 5.1 for Windows Server 2008 R2 and Windows 7</span></span>

> <span data-ttu-id="1b062-130">**Not:** yükleme yönergeleri için Windows Server 2008 R2 ve Windows 7 değişmiş ve diğer paketleri yönergelerini farklıdır.</span><span class="sxs-lookup"><span data-stu-id="1b062-130">**Note:** Installation instructions for Windows Server 2008 R2 and Windows 7 have changed, and differ from the instructions for the other packages.</span></span> <span data-ttu-id="1b062-131">Windows Server 2012 R2, Windows Server 2012 ve Windows 8.1 için yükleme yönergeleri aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1b062-131">Installation instructions for Windows Server 2012 R2, Windows Server 2012, and Windows 8.1 are below.</span></span>

<span data-ttu-id="1b062-132">**Windows Server 2008 R2 ve Windows 7 WMF 5.1 yükleme**</span><span class="sxs-lookup"><span data-stu-id="1b062-132">**Installing WMF 5.1 on Windows Server 2008 R2 and Windows 7**</span></span>

1. <span data-ttu-id="1b062-133">ZIP dosyasının yüklediğiniz klasöre gidin.</span><span class="sxs-lookup"><span data-stu-id="1b062-133">Navigate to the folder into which you downloaded the ZIP file.</span></span>

2. <span data-ttu-id="1b062-134">ZIP dosyasını sağ tıklatın ve "Extract tüm..." öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="1b062-134">Right-click on the ZIP file, and select "Extract All...".</span></span> <span data-ttu-id="1b062-135">Zip 2 dosyaları içerir: bir MSU ve yükleme WMF5.1.PS1 komut dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="1b062-135">The Zip contains 2 files: an MSU and the Install-WMF5.1.PS1 script file.</span></span>
<span data-ttu-id="1b062-136">ZIP dosyası açılmış sonra Windows 7 veya Windows Server 2008 R2 çalıştıran herhangi bir makineye içeriği kopyalayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1b062-136">Once you have unpacked the ZIP file, you can copy the contents to any machine running Windows 7 or Windows Server 2008 R2.</span></span>

3. <span data-ttu-id="1b062-137">ZIP dosyasının içeriğini ayıkladıktan, yönetici olarak PowerShell'i açın, sonra ZIP dosyasının içeriğini içeren klasöre gidin.</span><span class="sxs-lookup"><span data-stu-id="1b062-137">After extracting the ZIP file contents, open PowerShell as administrator, then navigate to the folder containing the contents of the ZIP file.</span></span>

4. <span data-ttu-id="1b062-138">Bu klasöre yükle Wmf5.1.ps1 komut dosyasını çalıştırın ve yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="1b062-138">Run the Install-Wmf5.1.ps1 script in that folder, and follow the instructions.</span></span> <span data-ttu-id="1b062-139">Bu komut dosyası yerel makine üzerinde önkoşulları denetleyin ve Önkoşullar karşılanıyorsa WMF 5.1 yükleyin.</span><span class="sxs-lookup"><span data-stu-id="1b062-139">This script will check the prerequisites on the local machine, and install WMF 5.1 if the prerequisites have been met.</span></span> <span data-ttu-id="1b062-140">Önkoşullar aşağıda listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="1b062-140">The prerequisites are listed below.</span></span>

<span data-ttu-id="1b062-141">Yükleme WMF5.1.ps1 Windows Server 2008 R2 ve Windows 7 yüklemesinde otomatikleştirme kolaylaştırmak için aşağıdaki parametreleri alır:</span><span class="sxs-lookup"><span data-stu-id="1b062-141">Install-WMF5.1.ps1 takes the following parameters to ease automating the installation on Windows Server 2008 R2 and Windows 7:</span></span>

- <span data-ttu-id="1b062-142">AcceptEula: Bu parametreyi dahil edildiğinde EULA'yı otomatik olarak kabul edilir ve görüntülenmeyecek.</span><span class="sxs-lookup"><span data-stu-id="1b062-142">AcceptEula: When this parameter is included, the EULA is automatically accepted and will not be displayed.</span></span>
- <span data-ttu-id="1b062-143">AllowRestart: Bu parametre, yalnızca AcceptEula belirtilmişse kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1b062-143">AllowRestart: This parameter can only be used if AcceptEula is specified.</span></span> <span data-ttu-id="1b062-144">Bu parametre bulunur ve WMF 5.1 yükledikten sonra bir yeniden başlatma gerekli ise, yeniden yüklemesi tamamlandıktan hemen sonra sormadan gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="1b062-144">If this parameter is included, and a restart is required after installing WMF 5.1, the restart will happen without prompting immediately after the installation is completed.</span></span>

<span data-ttu-id="1b062-145">**WMF 5.1 Windows Server 2008 R2 SP1 ve Windows 7 SP1 için Önkoşullar**</span><span class="sxs-lookup"><span data-stu-id="1b062-145">**WMF 5.1 Prerequisites for Windows Server 2008 R2 SP1 and Windows 7 SP1**</span></span>

<span data-ttu-id="1b062-146">Windows Server 2008 R2 SP1 ya da Windows 7 SP1, WMF 5.1 yükleme aşağıdakileri gerektirir:</span><span class="sxs-lookup"><span data-stu-id="1b062-146">Installation of WMF 5.1 on either Windows Server 2008 R2 SP1 or Windows 7 SP1, requires the following:</span></span>
- <span data-ttu-id="1b062-147">En son hizmet paketi yüklü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1b062-147">Latest service pack must be installed.</span></span>
- <span data-ttu-id="1b062-148">WMF 3.0 **bulunmamalıdır** yüklü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1b062-148">WMF 3.0 **must not** be installed.</span></span> <span data-ttu-id="1b062-149">WMF 3.0 WMF 5.1 yükleme diğer uygulamaların başarısız olmasına neden olabilir PSModulePath kaybına neden olur.</span><span class="sxs-lookup"><span data-stu-id="1b062-149">Installing WMF 5.1 over WMF 3.0 will result in the loss of the PSModulePath, which can cause other applications to fail.</span></span> <span data-ttu-id="1b062-150">WMF 5.1'ı yüklemeden önce ya da yüklemeyi WMF 3.0 veya PSModulePath kaydedin ve WMF 5.1 yüklemesi tamamlandıktan sonra sonra onu el ile geri yüklemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="1b062-150">Before installing WMF 5.1, you must either un-install WMF 3.0, or save the PSModulePath and then restore it manually after WMF 5.1 installation is complete.</span></span>
- <span data-ttu-id="1b062-151">WMF 5.1 en azından [.NET Framework 4.5.2](https://www.microsoft.com/en-ca/download/details.aspx?id=42642).</span><span class="sxs-lookup"><span data-stu-id="1b062-151">WMF 5.1 requires at least [.NET Framework 4.5.2](https://www.microsoft.com/en-ca/download/details.aspx?id=42642).</span></span>
<span data-ttu-id="1b062-152">Microsoft .NET Framework 4.5.2 yükleme konumundan yönergeleri izleyerek yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1b062-152">You can install Microsoft .NET Framework 4.5.2 by following the instructions at the download location.</span></span>

<span data-ttu-id="1b062-153">**WinRM bağımlılık**</span><span class="sxs-lookup"><span data-stu-id="1b062-153">**WinRM Dependency**</span></span>

<span data-ttu-id="1b062-154">Windows PowerShell istenen durum yapılandırması (DSC) üzerinde WinRM bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="1b062-154">Windows PowerShell Desired State Configuration (DSC) depends on WinRM.</span></span>
<span data-ttu-id="1b062-155">WinRM Windows Server 2008 R2 ve Windows 7 varsayılan olarak etkin değildir.</span><span class="sxs-lookup"><span data-stu-id="1b062-155">WinRM is not enabled by default on Windows Server 2008 R2 and Windows 7.</span></span>
<span data-ttu-id="1b062-156">Çalıştırma `Set-WSManQuickConfig`, Windows PowerShell'de yükseltilmiş WinRM etkinleştirmek için oturumu.</span><span class="sxs-lookup"><span data-stu-id="1b062-156">Run `Set-WSManQuickConfig`, in a Windows PowerShell elevated session, to enable WinRM.</span></span>


## <a name="install-wmf-51-for-windows-server-2012-r2-windows-server-2012-and-windows-81"></a><span data-ttu-id="1b062-157">Windows Server 2012 R2, Windows Server 2012 ve Windows 8.1 için WMF 5.1 yükleyin</span><span class="sxs-lookup"><span data-stu-id="1b062-157">Install WMF 5.1 for Windows Server 2012 R2, Windows Server 2012, and Windows 8.1</span></span>
<span data-ttu-id="1b062-158">**Windows Gezgini (veya dosya Gezgini'nde, Windows Server 2012 R2 veya Windows 8.1) yükleyin**</span><span class="sxs-lookup"><span data-stu-id="1b062-158">**Install from Windows Explorer (or File Explorer in Windows Server 2012 R2 or Windows 8.1)**</span></span>

1. <span data-ttu-id="1b062-159">MSU dosyasının yüklediğiniz klasöre gidin.</span><span class="sxs-lookup"><span data-stu-id="1b062-159">Navigate to the folder into which you downloaded the MSU file.</span></span>
2. <span data-ttu-id="1b062-160">Çalıştırmak için MSU çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="1b062-160">Double-click the MSU to run it.</span></span>

<span data-ttu-id="1b062-161">**Komut istemi kullanarak yükleme**</span><span class="sxs-lookup"><span data-stu-id="1b062-161">**Installing from the Command Prompt**</span></span>

1. <span data-ttu-id="1b062-162">Bilgisayarınızın mimarisi için doğru paket indirdikten sonra yükseltilmiş kullanıcı haklarıyla (yönetici olarak çalıştır) bir komut istemi penceresi açın.</span><span class="sxs-lookup"><span data-stu-id="1b062-162">After downloading the correct package for your computer's architecture, open a Command Prompt window with elevated user rights (Run as Administrator).</span></span> <span data-ttu-id="1b062-163">Üzerinde Sunucu Çekirdeği yükleme seçenekleri, Windows Server 2012 R2, Windows Server 2012 veya Windows Server 2008 R2 SP1, varsayılan olarak yükseltilmiş kullanıcı haklarıyla bir komut istemi açar.</span><span class="sxs-lookup"><span data-stu-id="1b062-163">On the Server Core installation options of Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1, Command Prompt opens with elevated user rights by default.</span></span>
2. <span data-ttu-id="1b062-164">Dizinleri içine varsa indirilen veya WMF 5.1 yükleme paketini kopyaladığınız klasöre gidin.</span><span class="sxs-lookup"><span data-stu-id="1b062-164">Change directories to the folder into which you have downloaded or copied the WMF 5.1 installation package.</span></span>
3. <span data-ttu-id="1b062-165">Aşağıdaki komutlardan birini çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="1b062-165">Run one of the following commands:</span></span>
   - <span data-ttu-id="1b062-166">Windows Server 2012 R2 veya Windows 8.1 x64 çalıştıran bilgisayarlarda çalıştırmak `Win8.1AndW2K12R2-KB3191564-x64.msu /quiet`.</span><span class="sxs-lookup"><span data-stu-id="1b062-166">On computers that are running Windows Server 2012 R2 or Windows 8.1 x64, run `Win8.1AndW2K12R2-KB3191564-x64.msu /quiet`.</span></span>
   - <span data-ttu-id="1b062-167">Windows Server 2012 çalıştıran bilgisayarlarda çalıştırmak `W2K12-KB3191565-x64.msu /quiet`.</span><span class="sxs-lookup"><span data-stu-id="1b062-167">On computers that are running Windows Server 2012, run `W2K12-KB3191565-x64.msu /quiet`.</span></span>
   - <span data-ttu-id="1b062-168">Windows 8.1 x86 çalıştıran bilgisayarlarda çalıştırmak `Win8.1-KB3191564-x86.msu /quiet`.</span><span class="sxs-lookup"><span data-stu-id="1b062-168">On computers that are running Windows 8.1 x86, run `Win8.1-KB3191564-x86.msu /quiet`.</span></span>

> [!NOTE]
> <span data-ttu-id="1b062-169">WMF 5.1 yüklemek için yeniden başlatma gerekir.</span><span class="sxs-lookup"><span data-stu-id="1b062-169">Installing WMF 5.1 requires a reboot.</span></span> <span data-ttu-id="1b062-170">Kullanarak `/quiet` seçeneği yeniden başlatma uyarısı olmadan sistem.</span><span class="sxs-lookup"><span data-stu-id="1b062-170">Using the `/quiet` option will reboot the system without warning.</span></span>
> <span data-ttu-id="1b062-171">Kullanım `/norestart` yeniden başlatılmasını önlemek için seçeneği.</span><span class="sxs-lookup"><span data-stu-id="1b062-171">Use the `/norestart` option to avoid rebooting.</span></span> <span data-ttu-id="1b062-172">Ancak, yeniden kadar WMF 5.1 yüklenmez.</span><span class="sxs-lookup"><span data-stu-id="1b062-172">However, WMF 5.1 will not be installed until you have rebooted.</span></span>