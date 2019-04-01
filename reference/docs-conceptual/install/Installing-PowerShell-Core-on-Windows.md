---
title: Windows’da PowerShell Core yükleme
description: Üzerinde Windows PowerShell Core yükleme hakkında bilgi
ms.date: 08/06/2018
ms.openlocfilehash: 450a38a1ef2e2890059094774fcc3f2ad4fcda6e
ms.sourcegitcommit: 8dd4394cf867005a8b9ef0bb74b744c964fbc332
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/30/2019
ms.locfileid: "58748950"
---
# <a name="installing-powershell-core-on-windows"></a><span data-ttu-id="16c06-103">Windows’da PowerShell Core yükleme</span><span class="sxs-lookup"><span data-stu-id="16c06-103">Installing PowerShell Core on Windows</span></span>

## <a name="msi"></a><span data-ttu-id="16c06-104">MSI</span><span class="sxs-lookup"><span data-stu-id="16c06-104">MSI</span></span>

<span data-ttu-id="16c06-105">Bir Windows istemci veya sunucuda Windows PowerShell'i yüklemek için (Windows 7 SP1, Server 2008 R2 üzerinde çalışır ve daha sonra), bizim Github'dan MSI paketini indirme [Yayınları][] sayfası.</span><span class="sxs-lookup"><span data-stu-id="16c06-105">To install PowerShell on a Windows client or Windows Server (works on Windows 7 SP1, Server 2008 R2, and later), download the MSI package from our GitHub [releases][] page.</span></span>  <span data-ttu-id="16c06-106">Ekranı aşağı kaydırarak **varlıklar** bölümü, yüklemek istediğiniz sürümü.</span><span class="sxs-lookup"><span data-stu-id="16c06-106">Scroll down to the **Assets** section of the Release you want to install.</span></span>  <span data-ttu-id="16c06-107">Genişletmek için tıklaymanız gerekebilir. Bu nedenle, varlıklar bölüm daraltılmış.</span><span class="sxs-lookup"><span data-stu-id="16c06-107">The Assets section may be collapsed, so you may need to click to expand it.</span></span>

<span data-ttu-id="16c06-108">MSI dosyası şu şekilde görünür- `PowerShell-<version>-win-<os-arch>.msi`</span><span class="sxs-lookup"><span data-stu-id="16c06-108">The MSI file looks like this - `PowerShell-<version>-win-<os-arch>.msi`</span></span>
<!-- TODO: should be updated to point to the Download Center as well -->

<span data-ttu-id="16c06-109">İndirildikten sonra yükleyiciye çift tıklayın ve yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="16c06-109">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="16c06-110">Bir kısayol Başlat menüsünde yükleme sonrasında yerleştirilen yoktur.</span><span class="sxs-lookup"><span data-stu-id="16c06-110">There is a shortcut placed in the Start Menu upon installation.</span></span>

- <span data-ttu-id="16c06-111">Varsayılan olarak, paket için yüklenir `$env:ProgramFiles\PowerShell\<version>`</span><span class="sxs-lookup"><span data-stu-id="16c06-111">By default the package is installed to `$env:ProgramFiles\PowerShell\<version>`</span></span>
- <span data-ttu-id="16c06-112">Başlat menüsü aracılığıyla PowerShell başlatabilir veya `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span><span class="sxs-lookup"><span data-stu-id="16c06-112">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span></span>

### <a name="prerequisites"></a><span data-ttu-id="16c06-113">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="16c06-113">Prerequisites</span></span>

<span data-ttu-id="16c06-114">WSMan PowerShell uzaktan iletişimini etkinleştirmek için aşağıdaki önkoşulların karşılanması gerekir:</span><span class="sxs-lookup"><span data-stu-id="16c06-114">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="16c06-115">Yükleme [Evrensel C çalışma zamanı](https://www.microsoft.com/download/details.aspx?id=50410) önce Windows 10 Windows sürümleri üzerinde.</span><span class="sxs-lookup"><span data-stu-id="16c06-115">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions prior to Windows 10.</span></span>
  <span data-ttu-id="16c06-116">Doğrudan indirme veya Windows Update kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="16c06-116">It is available via direct download or Windows Update.</span></span>
  <span data-ttu-id="16c06-117">Tam olarak düzeltme eki (isteğe bağlı paketleri dahil), desteklenen sistemleri zaten bu yüklü olacaktır.</span><span class="sxs-lookup"><span data-stu-id="16c06-117">Fully patched (including optional packages), supported systems will already have this installed.</span></span>
- <span data-ttu-id="16c06-118">Windows Management Framework (WMF) 4.0 veya daha yeni Windows 7 ve Windows Server 2008 R2 yükleyin.</span><span class="sxs-lookup"><span data-stu-id="16c06-118">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span>

## <a name="zip"></a><span data-ttu-id="16c06-119">ZIP</span><span class="sxs-lookup"><span data-stu-id="16c06-119">ZIP</span></span>

<span data-ttu-id="16c06-120">Gelişmiş dağıtım senaryoları etkinleştirmek için PowerShell ikili ZIP arşivlerini sağlanır.</span><span class="sxs-lookup"><span data-stu-id="16c06-120">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span>
<span data-ttu-id="16c06-121">ZIP arşivini kullanırken, önkoşul denetimi MSI paketini olduğu gibi vermeyecektir kaydedilmelidir.</span><span class="sxs-lookup"><span data-stu-id="16c06-121">Be noted that when using the ZIP archive, you won't get the prerequisites check as in the MSI package.</span></span>
<span data-ttu-id="16c06-122">Windows 10 önceki Windows sürümlerinde düzgün çalışması için sırasıyla WSMan üzerinden uzaktan iletişim için emin olmamız gerekiyor. Bu nedenle [önkoşulları](#prerequisites) karşılanır.</span><span class="sxs-lookup"><span data-stu-id="16c06-122">So in order for remoting over WSMan to work properly on Windows versions prior to Windows 10, you need to make sure the [prerequisites](#prerequisites) are met.</span></span>

## <a name="deploying-on-windows-iot"></a><span data-ttu-id="16c06-123">Windows IOT dağıtma</span><span class="sxs-lookup"><span data-stu-id="16c06-123">Deploying on Windows IoT</span></span>

<span data-ttu-id="16c06-124">Windows IOT zaten PowerShell Core 6'yı dağıtmak üzere kullanacağız Windows PowerShell ile birlikte gelir.</span><span class="sxs-lookup"><span data-stu-id="16c06-124">Windows IoT already comes with Windows PowerShell which we will use to deploy PowerShell Core 6.</span></span>

1. <span data-ttu-id="16c06-125">Oluşturma `PSSession` hedef cihaza</span><span class="sxs-lookup"><span data-stu-id="16c06-125">Create `PSSession` to target device</span></span>

   ```powershell
   $s = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. <span data-ttu-id="16c06-126">ZIP paketini cihaza Kopyala</span><span class="sxs-lookup"><span data-stu-id="16c06-126">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. <span data-ttu-id="16c06-127">Cihaza bağlayın ve Arşiv genişletin</span><span class="sxs-lookup"><span data-stu-id="16c06-127">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

4. <span data-ttu-id="16c06-128">PowerShell Core 6 için'uzaktan iletişim kurma</span><span class="sxs-lookup"><span data-stu-id="16c06-128">Setup remoting to PowerShell Core 6</span></span>

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. <span data-ttu-id="16c06-129">Cihazda PowerShell Core 6 uç noktasına bağlanma</span><span class="sxs-lookup"><span data-stu-id="16c06-129">Connect to PowerShell Core 6 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```

## <a name="deploying-on-nano-server"></a><span data-ttu-id="16c06-130">Nano Sunucu'yu dağıtma</span><span class="sxs-lookup"><span data-stu-id="16c06-130">Deploying on Nano Server</span></span>

<span data-ttu-id="16c06-131">Bu yönergeler, tarafından oluşturuldu ve Nano sunucu görüntüsünde PowerShell sürümü zaten çalışıyor varsayar [Nano sunucu görüntü Oluşturucusu](/windows-server/get-started/deploy-nano-server).</span><span class="sxs-lookup"><span data-stu-id="16c06-131">These instructions assume that a version of PowerShell is already running on the Nano Server image and that it has been generated by the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span></span>
<span data-ttu-id="16c06-132">Nano sunucu "gözetimsiz" bir işletim sistemi ' dir.</span><span class="sxs-lookup"><span data-stu-id="16c06-132">Nano Server is a "headless" OS.</span></span> <span data-ttu-id="16c06-133">Çekirdek ikili dosyalarını olması dağıtabilir iki farklı yöntemle.</span><span class="sxs-lookup"><span data-stu-id="16c06-133">Core binaries can be deploy using two different methods.</span></span>

1. <span data-ttu-id="16c06-134">Çevrimdışı - Nano sunucu VHD'sini bağlayın ve bağlı görüntü içinde seçilen konumunuza ZIP dosyasının içeriğini sıkıştırmasını açın.</span><span class="sxs-lookup"><span data-stu-id="16c06-134">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
2. <span data-ttu-id="16c06-135">Çevrimiçi - zip dosyasını bir PowerShell oturumu üzerinden aktarım ve seçilen konumunuza sıkıştırmasını açın.</span><span class="sxs-lookup"><span data-stu-id="16c06-135">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="16c06-136">Her iki durumda da, Windows 10 x64 ZIP yayın gerekir paketini ve bir "Yönetici" PowerShell örneği içindeki komutları çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="16c06-136">In both cases, you will need the Windows 10 x64 ZIP release package and will need to run the commands within an "Administrator" PowerShell instance.</span></span>

### <a name="offline-deployment-of-powershell-core"></a><span data-ttu-id="16c06-137">PowerShell Core çevrimdışı dağıtımı</span><span class="sxs-lookup"><span data-stu-id="16c06-137">Offline Deployment of PowerShell Core</span></span>

1. <span data-ttu-id="16c06-138">Bir dizine bağlı Nano sunucu görüntü içinde paketin sıkıştırmasını açmak için sık kullanılan sıkıştırma yardımcı programı kullanın.</span><span class="sxs-lookup"><span data-stu-id="16c06-138">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
2. <span data-ttu-id="16c06-139">Yansımayı ve bunu önyükleme.</span><span class="sxs-lookup"><span data-stu-id="16c06-139">Unmount the image and boot it.</span></span>
3. <span data-ttu-id="16c06-140">Windows PowerShell'in gelen örneğine bağlanın.</span><span class="sxs-lookup"><span data-stu-id="16c06-140">Connect to the inbox instance of Windows PowerShell.</span></span>
4. <span data-ttu-id="16c06-141">Uzaktan iletişimi kullanarak uç nokta oluşturmak için yönergeleri izleyin ["başka bir örnek yöntem"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="16c06-141">Follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell-core"></a><span data-ttu-id="16c06-142">PowerShell Core çevrimiçi dağıtımı</span><span class="sxs-lookup"><span data-stu-id="16c06-142">Online Deployment of PowerShell Core</span></span>

<span data-ttu-id="16c06-143">Aşağıdaki adımlar PowerShell Core dağıtımı çalışan bir Nano sunucu ve kendi uzak uç nokta yapılandırması örneği için yol.</span><span class="sxs-lookup"><span data-stu-id="16c06-143">The following steps guide you through the deployment of PowerShell Core to a running instance of Nano Server and the configuration of its remote endpoint.</span></span>

- <span data-ttu-id="16c06-144">Windows PowerShell gelen örneğine bağlanın</span><span class="sxs-lookup"><span data-stu-id="16c06-144">Connect to the inbox instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="16c06-145">Nano sunucu örneğine dosya kopyalayın</span><span class="sxs-lookup"><span data-stu-id="16c06-145">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="16c06-146">Oturum girin</span><span class="sxs-lookup"><span data-stu-id="16c06-146">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="16c06-147">ZIP dosyasını ayıklayın</span><span class="sxs-lookup"><span data-stu-id="16c06-147">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
  ```

- <span data-ttu-id="16c06-148">WSMan tabanlı uzak istiyorsanız, uzaktan iletişimi kullanarak uç nokta oluşturmak için yönergeleri izleyin ["başka bir örnek yöntem"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="16c06-148">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="instructions-to-create-a-remoting-endpoint"></a><span data-ttu-id="16c06-149">Bir uzak uç noktası oluşturmaya ilişkin yönergeler</span><span class="sxs-lookup"><span data-stu-id="16c06-149">Instructions to Create a Remoting Endpoint</span></span>

<span data-ttu-id="16c06-150">PowerShell Core WSMan ve SSH üzerinden PowerShell uzaktan iletişim protokolü (PSRP) destekler.</span><span class="sxs-lookup"><span data-stu-id="16c06-150">PowerShell Core supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span>
<span data-ttu-id="16c06-151">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="16c06-151">For more information, see:</span></span>

- <span data-ttu-id="16c06-152">[SSH PowerShell core'da uzaktan iletişim][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="16c06-152">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="16c06-153">[PowerShell core'da WSMan uzaktan iletişim][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="16c06-153">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

## <a name="artifact-installation-instructions"></a><span data-ttu-id="16c06-154">Yapıt yükleme yönergeleri</span><span class="sxs-lookup"><span data-stu-id="16c06-154">Artifact Installation Instructions</span></span>

<span data-ttu-id="16c06-155">Biz bir arşiv CoreCLR bitleri ile her bir CI yapısı ile yayımlama [AppVeyor][].</span><span class="sxs-lookup"><span data-stu-id="16c06-155">We publish an archive with CoreCLR bits on every CI build with [AppVeyor][].</span></span>

<span data-ttu-id="16c06-156">PowerShell Core CoreCLR yapıdan yüklemek için:</span><span class="sxs-lookup"><span data-stu-id="16c06-156">To install PowerShell Core from the CoreCLR Artifact:</span></span>

1. <span data-ttu-id="16c06-157">ZIP paketini indirin **yapıtları** belirli yapı sekmesi.</span><span class="sxs-lookup"><span data-stu-id="16c06-157">Download ZIP package from **artifacts** tab of the particular build.</span></span>
2. <span data-ttu-id="16c06-158">Engellemeyi kaldırma ZIP dosyası: dosya Gezgini'nde sağ -> Özellikler -> 'engellemeyi kaldırma kutusu ->' uygulama denetimi</span><span class="sxs-lookup"><span data-stu-id="16c06-158">Unblock ZIP file: right-click in File Explorer -> Properties -> check 'Unblock' box -> apply</span></span>
3. <span data-ttu-id="16c06-159">Zip dosyasını ayıklayın `bin` dizini</span><span class="sxs-lookup"><span data-stu-id="16c06-159">Extract zip file to `bin` directory</span></span>
4. `./bin/pwsh.exe`

<!-- [download-center]: TODO -->

[Yayınları]: https://github.com/PowerShell/PowerShell/releases
[releases]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
