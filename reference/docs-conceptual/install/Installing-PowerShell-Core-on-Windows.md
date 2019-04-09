---
title: Windows’da PowerShell Core yükleme
description: Üzerinde Windows PowerShell Core yükleme hakkında bilgi
ms.date: 08/06/2018
ms.openlocfilehash: 910ee5a653fc1703bfddaf6367225f3b654d600f
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293019"
---
# <a name="installing-powershell-core-on-windows"></a><span data-ttu-id="7e4af-103">Windows’da PowerShell Core yükleme</span><span class="sxs-lookup"><span data-stu-id="7e4af-103">Installing PowerShell Core on Windows</span></span>

<span data-ttu-id="7e4af-104">İçinde Windows PowerShell Core yüklemek için birden çok yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="7e4af-104">There are multiple ways to install PowerShell Core in Windows.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7e4af-105">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="7e4af-105">Prerequisites</span></span>

<span data-ttu-id="7e4af-106">WSMan PowerShell uzaktan iletişimini etkinleştirmek için aşağıdaki önkoşulların karşılanması gerekir:</span><span class="sxs-lookup"><span data-stu-id="7e4af-106">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="7e4af-107">Yükleme [Evrensel C çalışma zamanı](https://www.microsoft.com/download/details.aspx?id=50410) önce Windows 10 Windows sürümleri üzerinde.</span><span class="sxs-lookup"><span data-stu-id="7e4af-107">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions prior to Windows 10.</span></span> <span data-ttu-id="7e4af-108">Doğrudan indirme veya Windows Update kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7e4af-108">It is available via direct download or Windows Update.</span></span> <span data-ttu-id="7e4af-109">Tam olarak düzeltme eki (isteğe bağlı paketleri dahil), desteklenen sistemleri zaten bu yüklü olacaktır.</span><span class="sxs-lookup"><span data-stu-id="7e4af-109">Fully patched (including optional packages), supported systems will already have this installed.</span></span>
- <span data-ttu-id="7e4af-110">Windows Management Framework (WMF) 4.0 veya daha yeni Windows 7 ve Windows Server 2008 R2 yükleyin.</span><span class="sxs-lookup"><span data-stu-id="7e4af-110">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span>

## <a name="a-idmsi-installing-the-msi-package"></a><span data-ttu-id="7e4af-111"><a id="msi" />MSI paketini yükleme</span><span class="sxs-lookup"><span data-stu-id="7e4af-111"><a id="msi" />Installing the MSI package</span></span>

<span data-ttu-id="7e4af-112">Bir Windows istemci veya sunucuda Windows PowerShell'i yüklemek için (Windows 7 SP1, Server 2008 R2 üzerinde çalışır ve sonraki sürümler), GitHub [sürümleri] [] sayfamızı MSI paketini indirin.</span><span class="sxs-lookup"><span data-stu-id="7e4af-112">To install PowerShell on a Windows client or Windows Server (works on Windows 7 SP1, Server 2008 R2, and later), download the MSI package from our GitHub [releases][] page.</span></span> <span data-ttu-id="7e4af-113">Ekranı aşağı kaydırarak **varlıklar** bölümü, yüklemek istediğiniz sürümü.</span><span class="sxs-lookup"><span data-stu-id="7e4af-113">Scroll down to the **Assets** section of the Release you want to install.</span></span> <span data-ttu-id="7e4af-114">Genişletmek için tıklaymanız gerekebilir. Bu nedenle, varlıklar bölüm daraltılmış.</span><span class="sxs-lookup"><span data-stu-id="7e4af-114">The Assets section may be collapsed, so you may need to click to expand it.</span></span>

<span data-ttu-id="7e4af-115">MSI dosyası şu şekilde görünür-</span><span class="sxs-lookup"><span data-stu-id="7e4af-115">The MSI file looks like this -</span></span> `PowerShell-<version>-win-<os-arch>.msi`
<!-- TODO: should be updated to point to the Download Center as well -->

<span data-ttu-id="7e4af-116">İndirildikten sonra yükleyiciye çift tıklayın ve yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="7e4af-116">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="7e4af-117">Yükleyici Windows Başlat menüsünde bir kısayol oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7e4af-117">The installer creates a shortcut in the Windows Start Menu.</span></span>

- <span data-ttu-id="7e4af-118">Varsayılan olarak, paket için yüklenir</span><span class="sxs-lookup"><span data-stu-id="7e4af-118">By default the package is installed to</span></span> `$env:ProgramFiles\PowerShell\<version>`
- <span data-ttu-id="7e4af-119">Başlat menüsü aracılığıyla PowerShell başlatabilir veya</span><span class="sxs-lookup"><span data-stu-id="7e4af-119">You can launch PowerShell via the Start Menu or</span></span> `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`

### <a name="administrative-install-from-the-command-line"></a><span data-ttu-id="7e4af-120">Komut satırından yönetici yükleme</span><span class="sxs-lookup"><span data-stu-id="7e4af-120">Administrative install from the command line</span></span>

<span data-ttu-id="7e4af-121">MSI paketleri, komut satırından yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="7e4af-121">MSI packages can be installed from the command line.</span></span> <span data-ttu-id="7e4af-122">Bu, kullanıcı etkileşimi olmadan paketlerini dağıtma olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="7e4af-122">This allows administrators to deploy packages without user interaction.</span></span> <span data-ttu-id="7e4af-123">PowerShell için MSI paketi yükleme seçeneklerini denetlemek için aşağıdaki özellikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="7e4af-123">The MSI package for PowerShell includes the following properties to control the installation options:</span></span>

- <span data-ttu-id="7e4af-124">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** -bu özellik ekleme seçeneği denetler **açık PowerShell** Windows Gezgini bağlam menüsü öğesi.</span><span class="sxs-lookup"><span data-stu-id="7e4af-124">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** - This property controls the option for adding the **Open PowerShell** item to the context menu in Windows Explorer.</span></span>
- <span data-ttu-id="7e4af-125">**ENABLE_PSREMOTING** -bu özellik, yükleme sırasında PowerShell uzaktan iletişimini etkinleştirme seçeneği denetler.</span><span class="sxs-lookup"><span data-stu-id="7e4af-125">**ENABLE_PSREMOTING** - This property controls the option for enabling PowerShell remoting during installation.</span></span>
- <span data-ttu-id="7e4af-126">**REGISTER_MANIFEST** -bu özellik, Windows olay günlüğü bildirimi kaydetme seçeneği denetler.</span><span class="sxs-lookup"><span data-stu-id="7e4af-126">**REGISTER_MANIFEST** - This property controls the option for registering the Windows Event Logging manifest.</span></span>

<span data-ttu-id="7e4af-127">Aşağıdaki örneklerde, PowerShell Core etkin tüm yükleme seçenekleri ile sessizce yüklemek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="7e4af-127">The following examples shows how to silently install PowerShell Core with all the install options enabled.</span></span>

```powershell
msiexec.exe /package PowerShell-<version>-win-<os-arch>.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
```

<span data-ttu-id="7e4af-128">Msiexec.exe komut satırı seçeneklerinin tam listesi için bkz. [komut satırı seçenekleri](/windows/desktop/Msi/command-line-options).</span><span class="sxs-lookup"><span data-stu-id="7e4af-128">For a full list of command line options for Msiexec.exe, see [Command line options](/windows/desktop/Msi/command-line-options).</span></span>

## <a name="a-idzip-installing-the-zip-package"></a><span data-ttu-id="7e4af-129"><a id="zip" />ZIP paketini yükleme</span><span class="sxs-lookup"><span data-stu-id="7e4af-129"><a id="zip" />Installing the ZIP package</span></span>

<span data-ttu-id="7e4af-130">Gelişmiş dağıtım senaryoları etkinleştirmek için PowerShell ikili ZIP arşivlerini sağlanır.</span><span class="sxs-lookup"><span data-stu-id="7e4af-130">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span> <span data-ttu-id="7e4af-131">ZIP arşivini kullanırken, önkoşul denetimi MSI paketini olduğu gibi vermeyecektir kaydedilmelidir.</span><span class="sxs-lookup"><span data-stu-id="7e4af-131">Be noted that when using the ZIP archive, you won't get the prerequisites check as in the MSI package.</span></span> <span data-ttu-id="7e4af-132">WSMan düzgün çalışması için üzerinden uzaktan iletişim için,, karşıladığınızdan emin olun [önkoşulları](#prerequisites).</span><span class="sxs-lookup"><span data-stu-id="7e4af-132">For remoting over WSMan to work properly,, ensure that you have met the [prerequisites](#prerequisites).</span></span>

## <a name="deploying-on-windows-iot"></a><span data-ttu-id="7e4af-133">Windows IOT dağıtma</span><span class="sxs-lookup"><span data-stu-id="7e4af-133">Deploying on Windows IoT</span></span>

<span data-ttu-id="7e4af-134">Windows IOT zaten PowerShell Core 6'yı dağıtmak üzere kullanacağız Windows PowerShell ile birlikte gelir.</span><span class="sxs-lookup"><span data-stu-id="7e4af-134">Windows IoT already comes with Windows PowerShell which we will use to deploy PowerShell Core 6.</span></span>

1. <span data-ttu-id="7e4af-135">Oluşturma `PSSession` hedef cihaza</span><span class="sxs-lookup"><span data-stu-id="7e4af-135">Create `PSSession` to target device</span></span>

   ```powershell
   $s = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. <span data-ttu-id="7e4af-136">ZIP paketini cihaza Kopyala</span><span class="sxs-lookup"><span data-stu-id="7e4af-136">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. <span data-ttu-id="7e4af-137">Cihaza bağlayın ve Arşiv genişletin</span><span class="sxs-lookup"><span data-stu-id="7e4af-137">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

4. <span data-ttu-id="7e4af-138">PowerShell Core 6 için'uzaktan iletişim kurma</span><span class="sxs-lookup"><span data-stu-id="7e4af-138">Setup remoting to PowerShell Core 6</span></span>

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. <span data-ttu-id="7e4af-139">Cihazda PowerShell Core 6 uç noktasına bağlanma</span><span class="sxs-lookup"><span data-stu-id="7e4af-139">Connect to PowerShell Core 6 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```

## <a name="deploying-on-nano-server"></a><span data-ttu-id="7e4af-140">Nano Sunucu'yu dağıtma</span><span class="sxs-lookup"><span data-stu-id="7e4af-140">Deploying on Nano Server</span></span>

<span data-ttu-id="7e4af-141">Bu yönergeler, tarafından oluşturuldu ve Nano sunucu görüntüsünde PowerShell sürümü zaten çalışıyor varsayar [Nano sunucu görüntü Oluşturucusu](/windows-server/get-started/deploy-nano-server).</span><span class="sxs-lookup"><span data-stu-id="7e4af-141">These instructions assume that a version of PowerShell is already running on the Nano Server image and that it has been generated by the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span></span>
<span data-ttu-id="7e4af-142">Nano sunucu "gözetimsiz" bir işletim sistemi ' dir.</span><span class="sxs-lookup"><span data-stu-id="7e4af-142">Nano Server is a "headless" OS.</span></span> <span data-ttu-id="7e4af-143">Çekirdek ikili dosyalarını olması dağıtabilir iki farklı yöntemle.</span><span class="sxs-lookup"><span data-stu-id="7e4af-143">Core binaries can be deploy using two different methods.</span></span>

1. <span data-ttu-id="7e4af-144">Çevrimdışı - Nano sunucu VHD'sini bağlayın ve bağlı görüntü içinde seçilen konumunuza ZIP dosyasının içeriğini sıkıştırmasını açın.</span><span class="sxs-lookup"><span data-stu-id="7e4af-144">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
2. <span data-ttu-id="7e4af-145">Çevrimiçi - zip dosyasını bir PowerShell oturumu üzerinden aktarım ve seçilen konumunuza sıkıştırmasını açın.</span><span class="sxs-lookup"><span data-stu-id="7e4af-145">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="7e4af-146">Her iki durumda da, Windows 10 x64 ZIP yayın gerekir paketini ve bir "Yönetici" PowerShell örneği içindeki komutları çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7e4af-146">In both cases, you will need the Windows 10 x64 ZIP release package and will need to run the commands within an "Administrator" PowerShell instance.</span></span>

### <a name="offline-deployment-of-powershell-core"></a><span data-ttu-id="7e4af-147">PowerShell Core çevrimdışı dağıtımı</span><span class="sxs-lookup"><span data-stu-id="7e4af-147">Offline Deployment of PowerShell Core</span></span>

1. <span data-ttu-id="7e4af-148">Bir dizine bağlı Nano sunucu görüntü içinde paketin sıkıştırmasını açmak için sık kullanılan sıkıştırma yardımcı programı kullanın.</span><span class="sxs-lookup"><span data-stu-id="7e4af-148">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
2. <span data-ttu-id="7e4af-149">Yansımayı ve bunu önyükleme.</span><span class="sxs-lookup"><span data-stu-id="7e4af-149">Unmount the image and boot it.</span></span>
3. <span data-ttu-id="7e4af-150">Windows PowerShell'in gelen örneğine bağlanın.</span><span class="sxs-lookup"><span data-stu-id="7e4af-150">Connect to the inbox instance of Windows PowerShell.</span></span>
4. <span data-ttu-id="7e4af-151">Uzaktan iletişimi kullanarak uç nokta oluşturmak için yönergeleri izleyin ["başka bir örnek yöntem"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="7e4af-151">Follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell-core"></a><span data-ttu-id="7e4af-152">PowerShell Core çevrimiçi dağıtımı</span><span class="sxs-lookup"><span data-stu-id="7e4af-152">Online Deployment of PowerShell Core</span></span>

<span data-ttu-id="7e4af-153">Aşağıdaki adımlar PowerShell Core dağıtımı çalışan bir Nano sunucu ve kendi uzak uç nokta yapılandırması örneği için yol.</span><span class="sxs-lookup"><span data-stu-id="7e4af-153">The following steps guide you through the deployment of PowerShell Core to a running instance of Nano Server and the configuration of its remote endpoint.</span></span>

- <span data-ttu-id="7e4af-154">Windows PowerShell gelen örneğine bağlanın</span><span class="sxs-lookup"><span data-stu-id="7e4af-154">Connect to the inbox instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="7e4af-155">Nano sunucu örneğine dosya kopyalayın</span><span class="sxs-lookup"><span data-stu-id="7e4af-155">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="7e4af-156">Oturum girin</span><span class="sxs-lookup"><span data-stu-id="7e4af-156">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="7e4af-157">ZIP dosyasını ayıklayın</span><span class="sxs-lookup"><span data-stu-id="7e4af-157">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
  ```

- <span data-ttu-id="7e4af-158">WSMan tabanlı uzak istiyorsanız, uzaktan iletişimi kullanarak uç nokta oluşturmak için yönergeleri izleyin ["başka bir örnek yöntem"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="7e4af-158">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="how-to-create-a-remoting-endpoint"></a><span data-ttu-id="7e4af-159">Uzaktan iletişim uç noktası oluşturma</span><span class="sxs-lookup"><span data-stu-id="7e4af-159">How to create a remoting endpoint</span></span>

<span data-ttu-id="7e4af-160">PowerShell Core WSMan ve SSH üzerinden PowerShell uzaktan iletişim protokolü (PSRP) destekler.</span><span class="sxs-lookup"><span data-stu-id="7e4af-160">PowerShell Core supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span> <span data-ttu-id="7e4af-161">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="7e4af-161">For more information, see:</span></span>

- <span data-ttu-id="7e4af-162">[SSH PowerShell core'da uzaktan iletişim] [ssh-uzaktan iletişim]</span><span class="sxs-lookup"><span data-stu-id="7e4af-162">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="7e4af-163">[WSMan uzak PowerShell core'da] [wsman uzaktan iletişim]</span><span class="sxs-lookup"><span data-stu-id="7e4af-163">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

<!-- [download-center]: TODO -->
[sürümleri]: https://github.com/PowerShell/PowerShell/releases [ssh-uzaktan iletişim]:... /Core-PowerShell/SSH-Remoting-in-PowerShell-Core.MD [wsman uzaktan iletişim]:... /Core-PowerShell/wsman-Remoting-in-PowerShell-Core.MD [AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
[releases]: https://github.com/PowerShell/PowerShell/releases [ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md [wsman-remoting]: ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md [AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
