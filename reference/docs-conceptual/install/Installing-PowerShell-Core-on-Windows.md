---
title: Windows’da PowerShell Core yükleme
description: Üzerinde Windows PowerShell Core yükleme hakkında bilgi
ms.date: 08/06/2018
ms.openlocfilehash: 5a3c43e27f0027cfbeeefab33b045e618e0ff045
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854354"
---
# <a name="installing-powershell-core-on-windows"></a><span data-ttu-id="6bd25-103">Windows’da PowerShell Core yükleme</span><span class="sxs-lookup"><span data-stu-id="6bd25-103">Installing PowerShell Core on Windows</span></span>

<span data-ttu-id="6bd25-104">İçinde Windows PowerShell Core yüklemek için birden çok yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="6bd25-104">There are multiple ways to install PowerShell Core in Windows.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6bd25-105">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="6bd25-105">Prerequisites</span></span>

<span data-ttu-id="6bd25-106">WSMan PowerShell uzaktan iletişimini etkinleştirmek için aşağıdaki önkoşulların karşılanması gerekir:</span><span class="sxs-lookup"><span data-stu-id="6bd25-106">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="6bd25-107">Yükleme [Evrensel C çalışma zamanı](https://www.microsoft.com/download/details.aspx?id=50410) önce Windows 10 Windows sürümleri üzerinde.</span><span class="sxs-lookup"><span data-stu-id="6bd25-107">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions prior to Windows 10.</span></span> <span data-ttu-id="6bd25-108">Doğrudan indirme veya Windows Update kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6bd25-108">It is available via direct download or Windows Update.</span></span> <span data-ttu-id="6bd25-109">Tam olarak düzeltme eki (isteğe bağlı paketleri dahil), desteklenen sistemleri zaten bu yüklü olacaktır.</span><span class="sxs-lookup"><span data-stu-id="6bd25-109">Fully patched (including optional packages), supported systems will already have this installed.</span></span>
- <span data-ttu-id="6bd25-110">Windows Management Framework (WMF) 4.0 veya daha yeni Windows 7 ve Windows Server 2008 R2 yükleyin.</span><span class="sxs-lookup"><span data-stu-id="6bd25-110">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span> <span data-ttu-id="6bd25-111">WMF hakkında daha fazla bilgi için bkz: [WMF genel bakış](/powershell/wmf/overview).</span><span class="sxs-lookup"><span data-stu-id="6bd25-111">For more information about WMF, see [WMF Overview](/powershell/wmf/overview).</span></span>

## <a name="a-idmsi-installing-the-msi-package"></a><span data-ttu-id="6bd25-112"><a id="msi" />MSI paketini yükleme</span><span class="sxs-lookup"><span data-stu-id="6bd25-112"><a id="msi" />Installing the MSI package</span></span>

<span data-ttu-id="6bd25-113">Bir Windows istemci veya sunucuda Windows PowerShell'i yüklemek için (Windows 7 SP1, Server 2008 R2 üzerinde çalışır ve sonraki sürümler), GitHub [sürümleri] [] sayfamızı MSI paketini indirin.</span><span class="sxs-lookup"><span data-stu-id="6bd25-113">To install PowerShell on a Windows client or Windows Server (works on Windows 7 SP1, Server 2008 R2, and later), download the MSI package from our GitHub [releases][] page.</span></span> <span data-ttu-id="6bd25-114">Ekranı aşağı kaydırarak **varlıklar** bölümü, yüklemek istediğiniz sürümü.</span><span class="sxs-lookup"><span data-stu-id="6bd25-114">Scroll down to the **Assets** section of the Release you want to install.</span></span> <span data-ttu-id="6bd25-115">Genişletmek için tıklaymanız gerekebilir. Bu nedenle, varlıklar bölüm daraltılmış.</span><span class="sxs-lookup"><span data-stu-id="6bd25-115">The Assets section may be collapsed, so you may need to click to expand it.</span></span>

<span data-ttu-id="6bd25-116">MSI dosyası şu şekilde görünür- `PowerShell-<version>-win-<os-arch>.msi`</span><span class="sxs-lookup"><span data-stu-id="6bd25-116">The MSI file looks like this - `PowerShell-<version>-win-<os-arch>.msi`</span></span>
<!-- TODO: should be updated to point to the Download Center as well -->

<span data-ttu-id="6bd25-117">İndirildikten sonra yükleyiciye çift tıklayın ve yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="6bd25-117">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="6bd25-118">Yükleyici Windows Başlat menüsünde bir kısayol oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6bd25-118">The installer creates a shortcut in the Windows Start Menu.</span></span>

- <span data-ttu-id="6bd25-119">Varsayılan olarak, paket için yüklenir `$env:ProgramFiles\PowerShell\<version>`</span><span class="sxs-lookup"><span data-stu-id="6bd25-119">By default the package is installed to `$env:ProgramFiles\PowerShell\<version>`</span></span>
- <span data-ttu-id="6bd25-120">Başlat menüsü aracılığıyla PowerShell başlatabilir veya `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span><span class="sxs-lookup"><span data-stu-id="6bd25-120">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span></span>

### <a name="administrative-install-from-the-command-line"></a><span data-ttu-id="6bd25-121">Komut satırından yönetici yükleme</span><span class="sxs-lookup"><span data-stu-id="6bd25-121">Administrative install from the command line</span></span>

<span data-ttu-id="6bd25-122">MSI paketleri, komut satırından yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="6bd25-122">MSI packages can be installed from the command line.</span></span> <span data-ttu-id="6bd25-123">Bu, kullanıcı etkileşimi olmadan paketlerini dağıtma olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="6bd25-123">This allows administrators to deploy packages without user interaction.</span></span> <span data-ttu-id="6bd25-124">PowerShell için MSI paketi yükleme seçeneklerini denetlemek için aşağıdaki özellikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="6bd25-124">The MSI package for PowerShell includes the following properties to control the installation options:</span></span>

- <span data-ttu-id="6bd25-125">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** -bu özellik ekleme seçeneği denetler **açık PowerShell** Windows Gezgini bağlam menüsü öğesi.</span><span class="sxs-lookup"><span data-stu-id="6bd25-125">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** - This property controls the option for adding the **Open PowerShell** item to the context menu in Windows Explorer.</span></span>
- <span data-ttu-id="6bd25-126">**ENABLE_PSREMOTING** -bu özellik, yükleme sırasında PowerShell uzaktan iletişimini etkinleştirme seçeneği denetler.</span><span class="sxs-lookup"><span data-stu-id="6bd25-126">**ENABLE_PSREMOTING** - This property controls the option for enabling PowerShell remoting during installation.</span></span>
- <span data-ttu-id="6bd25-127">**REGISTER_MANIFEST** -bu özellik, Windows olay günlüğü bildirimi kaydetme seçeneği denetler.</span><span class="sxs-lookup"><span data-stu-id="6bd25-127">**REGISTER_MANIFEST** - This property controls the option for registering the Windows Event Logging manifest.</span></span>

<span data-ttu-id="6bd25-128">Aşağıdaki örneklerde, PowerShell Core etkin tüm yükleme seçenekleri ile sessizce yüklemek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="6bd25-128">The following examples shows how to silently install PowerShell Core with all the install options enabled.</span></span>

```powershell
msiexec.exe /package PowerShell-<version>-win-<os-arch>.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
```

<span data-ttu-id="6bd25-129">Msiexec.exe komut satırı seçeneklerinin tam listesi için bkz. [komut satırı seçenekleri](/windows/desktop/Msi/command-line-options).</span><span class="sxs-lookup"><span data-stu-id="6bd25-129">For a full list of command line options for Msiexec.exe, see [Command line options](/windows/desktop/Msi/command-line-options).</span></span>

## <a name="a-idzip-installing-the-zip-package"></a><span data-ttu-id="6bd25-130"><a id="zip" />ZIP paketini yükleme</span><span class="sxs-lookup"><span data-stu-id="6bd25-130"><a id="zip" />Installing the ZIP package</span></span>

<span data-ttu-id="6bd25-131">Gelişmiş dağıtım senaryoları etkinleştirmek için PowerShell ikili ZIP arşivlerini sağlanır.</span><span class="sxs-lookup"><span data-stu-id="6bd25-131">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span> <span data-ttu-id="6bd25-132">ZIP arşivini kullanırken, önkoşul denetimi MSI paketini olduğu gibi vermeyecektir kaydedilmelidir.</span><span class="sxs-lookup"><span data-stu-id="6bd25-132">Be noted that when using the ZIP archive, you won't get the prerequisites check as in the MSI package.</span></span> <span data-ttu-id="6bd25-133">WSMan düzgün çalışması için üzerinden uzaktan iletişim için,, karşıladığınızdan emin olun [önkoşulları](#prerequisites).</span><span class="sxs-lookup"><span data-stu-id="6bd25-133">For remoting over WSMan to work properly,, ensure that you have met the [prerequisites](#prerequisites).</span></span>

## <a name="deploying-on-windows-iot"></a><span data-ttu-id="6bd25-134">Windows IOT dağıtma</span><span class="sxs-lookup"><span data-stu-id="6bd25-134">Deploying on Windows IoT</span></span>

<span data-ttu-id="6bd25-135">Windows IOT zaten PowerShell Core 6'yı dağıtmak üzere kullanacağız Windows PowerShell ile birlikte gelir.</span><span class="sxs-lookup"><span data-stu-id="6bd25-135">Windows IoT already comes with Windows PowerShell which we will use to deploy PowerShell Core 6.</span></span>

1. <span data-ttu-id="6bd25-136">Oluşturma `PSSession` hedef cihaza</span><span class="sxs-lookup"><span data-stu-id="6bd25-136">Create `PSSession` to target device</span></span>

   ```powershell
   $s = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. <span data-ttu-id="6bd25-137">ZIP paketini cihaza Kopyala</span><span class="sxs-lookup"><span data-stu-id="6bd25-137">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. <span data-ttu-id="6bd25-138">Cihaza bağlayın ve Arşiv genişletin</span><span class="sxs-lookup"><span data-stu-id="6bd25-138">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

4. <span data-ttu-id="6bd25-139">PowerShell Core 6 için'uzaktan iletişim kurma</span><span class="sxs-lookup"><span data-stu-id="6bd25-139">Setup remoting to PowerShell Core 6</span></span>

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. <span data-ttu-id="6bd25-140">Cihazda PowerShell Core 6 uç noktasına bağlanma</span><span class="sxs-lookup"><span data-stu-id="6bd25-140">Connect to PowerShell Core 6 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```

## <a name="deploying-on-nano-server"></a><span data-ttu-id="6bd25-141">Nano Sunucu'yu dağıtma</span><span class="sxs-lookup"><span data-stu-id="6bd25-141">Deploying on Nano Server</span></span>

<span data-ttu-id="6bd25-142">Bu yönergeler, tarafından oluşturuldu ve Nano sunucu görüntüsünde PowerShell sürümü zaten çalışıyor varsayar [Nano sunucu görüntü Oluşturucusu](/windows-server/get-started/deploy-nano-server).</span><span class="sxs-lookup"><span data-stu-id="6bd25-142">These instructions assume that a version of PowerShell is already running on the Nano Server image and that it has been generated by the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span></span>
<span data-ttu-id="6bd25-143">Nano sunucu "gözetimsiz" bir işletim sistemi ' dir.</span><span class="sxs-lookup"><span data-stu-id="6bd25-143">Nano Server is a "headless" OS.</span></span> <span data-ttu-id="6bd25-144">Çekirdek ikili dosyalarını olması dağıtabilir iki farklı yöntemle.</span><span class="sxs-lookup"><span data-stu-id="6bd25-144">Core binaries can be deploy using two different methods.</span></span>

1. <span data-ttu-id="6bd25-145">Çevrimdışı - Nano sunucu VHD'sini bağlayın ve bağlı görüntü içinde seçilen konumunuza ZIP dosyasının içeriğini sıkıştırmasını açın.</span><span class="sxs-lookup"><span data-stu-id="6bd25-145">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
2. <span data-ttu-id="6bd25-146">Çevrimiçi - zip dosyasını bir PowerShell oturumu üzerinden aktarım ve seçilen konumunuza sıkıştırmasını açın.</span><span class="sxs-lookup"><span data-stu-id="6bd25-146">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="6bd25-147">Her iki durumda da, Windows 10 x64 ZIP yayın gerekir paketini ve bir "Yönetici" PowerShell örneği içindeki komutları çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6bd25-147">In both cases, you will need the Windows 10 x64 ZIP release package and will need to run the commands within an "Administrator" PowerShell instance.</span></span>

### <a name="offline-deployment-of-powershell-core"></a><span data-ttu-id="6bd25-148">PowerShell Core çevrimdışı dağıtımı</span><span class="sxs-lookup"><span data-stu-id="6bd25-148">Offline Deployment of PowerShell Core</span></span>

1. <span data-ttu-id="6bd25-149">Bir dizine bağlı Nano sunucu görüntü içinde paketin sıkıştırmasını açmak için sık kullanılan sıkıştırma yardımcı programı kullanın.</span><span class="sxs-lookup"><span data-stu-id="6bd25-149">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
2. <span data-ttu-id="6bd25-150">Yansımayı ve bunu önyükleme.</span><span class="sxs-lookup"><span data-stu-id="6bd25-150">Unmount the image and boot it.</span></span>
3. <span data-ttu-id="6bd25-151">Windows PowerShell'in gelen örneğine bağlanın.</span><span class="sxs-lookup"><span data-stu-id="6bd25-151">Connect to the inbox instance of Windows PowerShell.</span></span>
4. <span data-ttu-id="6bd25-152">Uzaktan iletişimi kullanarak uç nokta oluşturmak için yönergeleri izleyin ["başka bir örnek yöntem"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="6bd25-152">Follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell-core"></a><span data-ttu-id="6bd25-153">PowerShell Core çevrimiçi dağıtımı</span><span class="sxs-lookup"><span data-stu-id="6bd25-153">Online Deployment of PowerShell Core</span></span>

<span data-ttu-id="6bd25-154">Aşağıdaki adımlar PowerShell Core dağıtımı çalışan bir Nano sunucu ve kendi uzak uç nokta yapılandırması örneği için yol.</span><span class="sxs-lookup"><span data-stu-id="6bd25-154">The following steps guide you through the deployment of PowerShell Core to a running instance of Nano Server and the configuration of its remote endpoint.</span></span>

- <span data-ttu-id="6bd25-155">Windows PowerShell gelen örneğine bağlanın</span><span class="sxs-lookup"><span data-stu-id="6bd25-155">Connect to the inbox instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="6bd25-156">Nano sunucu örneğine dosya kopyalayın</span><span class="sxs-lookup"><span data-stu-id="6bd25-156">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="6bd25-157">Oturum girin</span><span class="sxs-lookup"><span data-stu-id="6bd25-157">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="6bd25-158">ZIP dosyasını ayıklayın</span><span class="sxs-lookup"><span data-stu-id="6bd25-158">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
  ```

- <span data-ttu-id="6bd25-159">WSMan tabanlı uzak istiyorsanız, uzaktan iletişimi kullanarak uç nokta oluşturmak için yönergeleri izleyin ["başka bir örnek yöntem"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="6bd25-159">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="how-to-create-a-remoting-endpoint"></a><span data-ttu-id="6bd25-160">Uzaktan iletişim uç noktası oluşturma</span><span class="sxs-lookup"><span data-stu-id="6bd25-160">How to create a remoting endpoint</span></span>

<span data-ttu-id="6bd25-161">PowerShell Core WSMan ve SSH üzerinden PowerShell uzaktan iletişim protokolü (PSRP) destekler.</span><span class="sxs-lookup"><span data-stu-id="6bd25-161">PowerShell Core supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span> <span data-ttu-id="6bd25-162">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="6bd25-162">For more information, see:</span></span>

- <span data-ttu-id="6bd25-163">[SSH PowerShell core'da uzaktan iletişim] [ssh-uzaktan iletişim]</span><span class="sxs-lookup"><span data-stu-id="6bd25-163">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="6bd25-164">[WSMan uzak PowerShell core'da] [wsman uzaktan iletişim]</span><span class="sxs-lookup"><span data-stu-id="6bd25-164">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

<!-- [download-center]: TODO -->
[sürümleri]: https://github.com/PowerShell/PowerShell/releases [ssh-uzaktan iletişim]:... /Core-PowerShell/SSH-Remoting-in-PowerShell-Core.MD [wsman uzaktan iletişim]:... /Core-PowerShell/wsman-Remoting-in-PowerShell-Core.MD [AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
[releases]: https://github.com/PowerShell/PowerShell/releases [ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md [wsman-remoting]: ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md [AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
