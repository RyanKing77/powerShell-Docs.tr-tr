# <a name="installing-powershell-core-on-windows"></a><span data-ttu-id="d81f7-101">Windows’da PowerShell Core yükleme</span><span class="sxs-lookup"><span data-stu-id="d81f7-101">Installing PowerShell Core on Windows</span></span>

## <a name="msi"></a><span data-ttu-id="d81f7-102">MSI</span><span class="sxs-lookup"><span data-stu-id="d81f7-102">MSI</span></span>

<span data-ttu-id="d81f7-103">Bir Windows istemci veya sunucuda Windows PowerShell'i yüklemek için (Windows 7 SP1, Server 2008 R2 üzerinde çalışır ve daha sonra), bizim Github'dan MSI paketini indirme [serbest][] sayfası.</span><span class="sxs-lookup"><span data-stu-id="d81f7-103">To install PowerShell on a Windows client or Windows Server (works on Windows 7 SP1, Server 2008 R2, and later), download the MSI package from our GitHub [releases][] page.</span></span>

<span data-ttu-id="d81f7-104">MSI dosyası şu şekilde görünür- `PowerShell-<version>-win-<os-arch>.msi`
<!-- TODO: should be updated to point to the Download Center as well --></span><span class="sxs-lookup"><span data-stu-id="d81f7-104">The MSI file looks like this - `PowerShell-<version>-win-<os-arch>.msi`
<!-- TODO: should be updated to point to the Download Center as well --></span></span>

<span data-ttu-id="d81f7-105">İndirildikten sonra yükleyiciye çift tıklayın ve yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="d81f7-105">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="d81f7-106">Bir kısayol Başlat menüsünde yükleme sonrasında yerleştirilen yoktur.</span><span class="sxs-lookup"><span data-stu-id="d81f7-106">There is a shortcut placed in the Start Menu upon installation.</span></span>

- <span data-ttu-id="d81f7-107">Varsayılan olarak, paket için yüklenir `$env:ProgramFiles\PowerShell\<version>`</span><span class="sxs-lookup"><span data-stu-id="d81f7-107">By default the package is installed to `$env:ProgramFiles\PowerShell\<version>`</span></span>
- <span data-ttu-id="d81f7-108">Başlat menüsü aracılığıyla PowerShell başlatabilir veya `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span><span class="sxs-lookup"><span data-stu-id="d81f7-108">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span></span>

### <a name="prerequisites"></a><span data-ttu-id="d81f7-109">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="d81f7-109">Prerequisites</span></span>

<span data-ttu-id="d81f7-110">WSMan PowerShell uzaktan iletişimini etkinleştirmek için aşağıdaki önkoşulların karşılanması gerekir:</span><span class="sxs-lookup"><span data-stu-id="d81f7-110">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="d81f7-111">Yükleme [Evrensel C çalışma zamanı](https://www.microsoft.com/download/details.aspx?id=50410) önce Windows 10 Windows sürümleri üzerinde.</span><span class="sxs-lookup"><span data-stu-id="d81f7-111">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions prior to Windows 10.</span></span>
  <span data-ttu-id="d81f7-112">Doğrudan indirme veya Windows Update kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d81f7-112">It is available via direct download or Windows Update.</span></span>
  <span data-ttu-id="d81f7-113">Tam olarak düzeltme eki (isteğe bağlı paketleri dahil), desteklenen sistemleri zaten bu yüklü olacaktır.</span><span class="sxs-lookup"><span data-stu-id="d81f7-113">Fully patched (including optional packages), supported systems will already have this installed.</span></span>
- <span data-ttu-id="d81f7-114">Windows Management Framework (WMF) 4.0 veya daha yeni Windows 7 ve Windows Server 2008 R2 yükleyin.</span><span class="sxs-lookup"><span data-stu-id="d81f7-114">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span>

## <a name="zip"></a><span data-ttu-id="d81f7-115">ZIP</span><span class="sxs-lookup"><span data-stu-id="d81f7-115">ZIP</span></span>

<span data-ttu-id="d81f7-116">Gelişmiş dağıtım senaryoları etkinleştirmek için PowerShell ikili ZIP arşivlerini sağlanır.</span><span class="sxs-lookup"><span data-stu-id="d81f7-116">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span>
<span data-ttu-id="d81f7-117">ZIP arşivini kullanırken, önkoşul denetimi MSI paketini olduğu gibi vermeyecektir kaydedilmelidir.</span><span class="sxs-lookup"><span data-stu-id="d81f7-117">Be noted that when using the ZIP archive, you won't get the prerequisites check as in the MSI package.</span></span>
<span data-ttu-id="d81f7-118">Windows 10 önceki Windows sürümlerinde düzgün çalışması için sırasıyla WSMan üzerinden uzaktan iletişim için emin olmamız gerekiyor. Bu nedenle [önkoşulları](#prerequisites) karşılanır.</span><span class="sxs-lookup"><span data-stu-id="d81f7-118">So in order for remoting over WSMan to work properly on Windows versions prior to Windows 10, you need to make sure the [prerequisites](#prerequisites) are met.</span></span>

## <a name="deploying-on-windows-iot"></a><span data-ttu-id="d81f7-119">Windows IOT dağıtma</span><span class="sxs-lookup"><span data-stu-id="d81f7-119">Deploying on Windows IoT</span></span>

<span data-ttu-id="d81f7-120">Windows IOT zaten PowerShell Core 6'yı dağıtmak üzere kullanacağız Windows PowerShell ile birlikte gelir.</span><span class="sxs-lookup"><span data-stu-id="d81f7-120">Windows IoT already comes with Windows PowerShell which we will use to deploy PowerShell Core 6.</span></span>

1. <span data-ttu-id="d81f7-121">Oluşturma `PSSession` hedef cihaza</span><span class="sxs-lookup"><span data-stu-id="d81f7-121">Create `PSSession` to target device</span></span>

   ```powershell
   $s = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. <span data-ttu-id="d81f7-122">ZIP paketini cihaza Kopyala</span><span class="sxs-lookup"><span data-stu-id="d81f7-122">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-6.0.2-win-arm32.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. <span data-ttu-id="d81f7-123">Cihaza bağlayın ve Arşiv genişletin</span><span class="sxs-lookup"><span data-stu-id="d81f7-123">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   cd u:\users\administrator\downloads
   Expand-Archive .\PowerShell-6.0.2-win-arm32.zip
   ```

4. <span data-ttu-id="d81f7-124">PowerShell Core 6 için'uzaktan iletişim kurma</span><span class="sxs-lookup"><span data-stu-id="d81f7-124">Setup remoting to PowerShell Core 6</span></span>

   ```powershell
   cd .\PowerShell-6.0.2-win-arm32
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. <span data-ttu-id="d81f7-125">Cihazda PowerShell Core 6 uç noktasına bağlanma</span><span class="sxs-lookup"><span data-stu-id="d81f7-125">Connect to PowerShell Core 6 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.6.0.2
   ```

## <a name="deploying-on-nano-server"></a><span data-ttu-id="d81f7-126">Nano Sunucu'yu dağıtma</span><span class="sxs-lookup"><span data-stu-id="d81f7-126">Deploying on Nano Server</span></span>

<span data-ttu-id="d81f7-127">Bu yönergeler, tarafından oluşturuldu ve Nano sunucu görüntüsünde PowerShell sürümü zaten çalışıyor varsayar [Nano sunucu görüntü Oluşturucusu](/windows-server/get-started/deploy-nano-server).</span><span class="sxs-lookup"><span data-stu-id="d81f7-127">These instructions assume that a version of PowerShell is already running on the Nano Server image and that it has been generated by the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span></span>
<span data-ttu-id="d81f7-128">Nano sunucu "gözetimsiz" bir işletim sistemi ' dir.</span><span class="sxs-lookup"><span data-stu-id="d81f7-128">Nano Server is a "headless" OS.</span></span> <span data-ttu-id="d81f7-129">Çekirdek ikili dosyalarını olması dağıtabilir iki farklı yöntemle.</span><span class="sxs-lookup"><span data-stu-id="d81f7-129">Core binaries can be deploy using two different methods.</span></span>

1. <span data-ttu-id="d81f7-130">Çevrimdışı - Nano sunucu VHD'sini bağlayın ve bağlı görüntü içinde seçilen konumunuza ZIP dosyasının içeriğini sıkıştırmasını açın.</span><span class="sxs-lookup"><span data-stu-id="d81f7-130">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
2. <span data-ttu-id="d81f7-131">Çevrimiçi - zip dosyasını bir PowerShell oturumu üzerinden aktarım ve seçilen konumunuza sıkıştırmasını açın.</span><span class="sxs-lookup"><span data-stu-id="d81f7-131">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="d81f7-132">Her iki durumda da, Windows 10 x64 ZIP yayın gerekir paketini ve bir "Yönetici" PowerShell örneği içindeki komutları çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d81f7-132">In both cases, you will need the Windows 10 x64 ZIP release package and will need to run the commands within an "Administrator" PowerShell instance.</span></span>

### <a name="offline-deployment-of-powershell-core"></a><span data-ttu-id="d81f7-133">PowerShell Core çevrimdışı dağıtımı</span><span class="sxs-lookup"><span data-stu-id="d81f7-133">Offline Deployment of PowerShell Core</span></span>

1. <span data-ttu-id="d81f7-134">Bir dizine bağlı Nano sunucu görüntü içinde paketin sıkıştırmasını açmak için sık kullanılan sıkıştırma yardımcı programı kullanın.</span><span class="sxs-lookup"><span data-stu-id="d81f7-134">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
2. <span data-ttu-id="d81f7-135">Yansımayı ve bunu önyükleme.</span><span class="sxs-lookup"><span data-stu-id="d81f7-135">Unmount the image and boot it.</span></span>
3. <span data-ttu-id="d81f7-136">Windows PowerShell'in gelen örneğine bağlanın.</span><span class="sxs-lookup"><span data-stu-id="d81f7-136">Connect to the inbox instance of Windows PowerShell.</span></span>
4. <span data-ttu-id="d81f7-137">Uzaktan iletişimi kullanarak uç nokta oluşturmak için yönergeleri izleyin ["başka bir örnek yöntem"](#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="d81f7-137">Follow the instructions to create a remoting endpoint using the ["another instance technique"](#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell-core"></a><span data-ttu-id="d81f7-138">PowerShell Core çevrimiçi dağıtımı</span><span class="sxs-lookup"><span data-stu-id="d81f7-138">Online Deployment of PowerShell Core</span></span>

<span data-ttu-id="d81f7-139">Aşağıdaki adımlar PowerShell Core dağıtımı çalışan bir Nano sunucu ve kendi uzak uç nokta yapılandırması örneği için yol.</span><span class="sxs-lookup"><span data-stu-id="d81f7-139">The following steps guide you through the deployment of PowerShell Core to a running instance of Nano Server and the configuration of its remote endpoint.</span></span>

- <span data-ttu-id="d81f7-140">Windows PowerShell gelen örneğine bağlanın</span><span class="sxs-lookup"><span data-stu-id="d81f7-140">Connect to the inbox instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="d81f7-141">Nano sunucu örneğine dosya kopyalayın</span><span class="sxs-lookup"><span data-stu-id="d81f7-141">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="d81f7-142">Oturum girin</span><span class="sxs-lookup"><span data-stu-id="d81f7-142">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="d81f7-143">ZIP dosyasını ayıklayın</span><span class="sxs-lookup"><span data-stu-id="d81f7-143">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
  ```

- <span data-ttu-id="d81f7-144">WSMan tabanlı uzak istiyorsanız, uzaktan iletişimi kullanarak uç nokta oluşturmak için yönergeleri izleyin ["başka bir örnek yöntem"](../core-powershell/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="d81f7-144">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"](../core-powershell/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="instructions-to-create-a-remoting-endpoint"></a><span data-ttu-id="d81f7-145">Bir uzak uç noktası oluşturmaya ilişkin yönergeler</span><span class="sxs-lookup"><span data-stu-id="d81f7-145">Instructions to Create a Remoting Endpoint</span></span>

<span data-ttu-id="d81f7-146">PowerShell Core WSMan ve SSH üzerinden PowerShell uzaktan iletişim protokolü (PSRP) destekler.</span><span class="sxs-lookup"><span data-stu-id="d81f7-146">PowerShell Core supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span>
<span data-ttu-id="d81f7-147">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="d81f7-147">For more information, see:</span></span>

- <span data-ttu-id="d81f7-148">[SSH PowerShell core'da uzaktan iletişim][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="d81f7-148">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="d81f7-149">[PowerShell core'da WSMan uzaktan iletişim][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="d81f7-149">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

## <a name="artifact-installation-instructions"></a><span data-ttu-id="d81f7-150">Yapıt yükleme yönergeleri</span><span class="sxs-lookup"><span data-stu-id="d81f7-150">Artifact Installation Instructions</span></span>

<span data-ttu-id="d81f7-151">Biz bir arşiv CoreCLR bitleri ile her bir CI yapısı ile yayımlama [AppVeyor][].</span><span class="sxs-lookup"><span data-stu-id="d81f7-151">We publish an archive with CoreCLR bits on every CI build with [AppVeyor][].</span></span>

<span data-ttu-id="d81f7-152">PowerShell Core CoreCLR yapıdan yüklemek için:</span><span class="sxs-lookup"><span data-stu-id="d81f7-152">To install PowerShell Core from the CoreCLR Artifact:</span></span>

1. <span data-ttu-id="d81f7-153">ZIP paketini indirin **yapıtları** belirli yapı sekmesi.</span><span class="sxs-lookup"><span data-stu-id="d81f7-153">Download ZIP package from **artifacts** tab of the particular build.</span></span>
2. <span data-ttu-id="d81f7-154">Engellemeyi kaldırma ZIP dosyası: dosya Gezgini'nde sağ -> Özellikler -> 'engellemeyi kaldırma kutusu ->' uygulama denetimi</span><span class="sxs-lookup"><span data-stu-id="d81f7-154">Unblock ZIP file: right-click in File Explorer -> Properties -> check 'Unblock' box -> apply</span></span>
3. <span data-ttu-id="d81f7-155">Zip dosyasını ayıklayın `bin` dizini</span><span class="sxs-lookup"><span data-stu-id="d81f7-155">Extract zip file to `bin` directory</span></span>
4. `./bin/pwsh.exe`

<!-- [download-center]: TODO -->

[serbest]: https://github.com/PowerShell/PowerShell/releases
[releases]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
