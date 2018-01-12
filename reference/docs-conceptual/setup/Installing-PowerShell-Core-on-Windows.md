# <a name="installing-powershell-core-on-windows"></a><span data-ttu-id="5e92d-101">Windows PowerShell çekirdek yükleniyor</span><span class="sxs-lookup"><span data-stu-id="5e92d-101">Installing PowerShell Core on Windows</span></span>

## <a name="msi"></a><span data-ttu-id="5e92d-102">MSI</span><span class="sxs-lookup"><span data-stu-id="5e92d-102">MSI</span></span>

<span data-ttu-id="5e92d-103">Bir Windows İstemcisi veya Windows Server PowerShell yüklemek için (Windows 7 SP1, Server 2008 R2 üzerinde çalışır ve daha sonra), bizim Github'dan MSI paketini indirin [serbest][] sayfası.</span><span class="sxs-lookup"><span data-stu-id="5e92d-103">To install PowerShell on a Windows client or Windows Server (works on Windows 7 SP1, Server 2008 R2, and later), download the MSI package from our GitHub [releases][] page.</span></span>

<span data-ttu-id="5e92d-104">MSI dosyası şuna benzer-`PowerShell-6.0.0.<buildversion>.<os-arch>.msi`</span><span class="sxs-lookup"><span data-stu-id="5e92d-104">The MSI file looks like this - `PowerShell-6.0.0.<buildversion>.<os-arch>.msi`</span></span>
<!-- TODO: should be updated to point to the Download Center as well -->

<span data-ttu-id="5e92d-105">Yüklendikten sonra yükleyici çift tıklayın ve yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="5e92d-105">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="5e92d-106">Yükleme sonrasında Başlat menüsü yerleştirilen bir kısayol yoktur.</span><span class="sxs-lookup"><span data-stu-id="5e92d-106">There is a shortcut placed in the Start Menu upon installation.</span></span>

* <span data-ttu-id="5e92d-107">Varsayılan olarak, paket için yüklenir`$env:ProgramFiles\PowerShell\`</span><span class="sxs-lookup"><span data-stu-id="5e92d-107">By default the package is installed to `$env:ProgramFiles\PowerShell\`</span></span>
* <span data-ttu-id="5e92d-108">Başlat menüsü aracılığıyla PowerShell başlatabilir veya`$env:ProgramFiles\PowerShell\pwsh.exe`</span><span class="sxs-lookup"><span data-stu-id="5e92d-108">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\pwsh.exe`</span></span>

### <a name="prerequisites"></a><span data-ttu-id="5e92d-109">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="5e92d-109">Prerequisites</span></span>

<span data-ttu-id="5e92d-110">WSMan PowerShell uzaktan iletişimi etkinleştirmek için aşağıdaki önkoşulların karşılanması gerekir:</span><span class="sxs-lookup"><span data-stu-id="5e92d-110">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

* <span data-ttu-id="5e92d-111">Yükleme [Evrensel C çalışma zamanı](https://www.microsoft.com/download/details.aspx?id=50410) Windows 10'den önceki Windows sürümleri üzerinde.</span><span class="sxs-lookup"><span data-stu-id="5e92d-111">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions prior to Windows 10.</span></span>
  <span data-ttu-id="5e92d-112">Doğrudan indirme veya Windows Update kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5e92d-112">It is available via direct download or Windows Update.</span></span>
  <span data-ttu-id="5e92d-113">Tam (isteğe bağlı paketleri dahil) düzeltme eki, desteklenen sistemleri zaten bu yüklü olacaktır.</span><span class="sxs-lookup"><span data-stu-id="5e92d-113">Fully patched (including optional packages), supported systems will already have this installed.</span></span>
* <span data-ttu-id="5e92d-114">Windows Management Framework (WMF) yükleme [4.0](https://www.microsoft.com/download/details.aspx?id=40855) ya da daha yeni ([5.1](https://www.microsoft.com/download/details.aspx?id=54616)) Windows 7 ve Windows Server 2008 R2 üzerinde.</span><span class="sxs-lookup"><span data-stu-id="5e92d-114">Install the Windows Management Framework (WMF) [4.0](https://www.microsoft.com/download/details.aspx?id=40855) or newer ([5.1](https://www.microsoft.com/download/details.aspx?id=54616)) on Windows 7 and Windows Server 2008 R2.</span></span>

## <a name="zip"></a><span data-ttu-id="5e92d-115">ZIP</span><span class="sxs-lookup"><span data-stu-id="5e92d-115">ZIP</span></span>

<span data-ttu-id="5e92d-116">PowerShell ikili ZIP arşivini gelişmiş dağıtım senaryoları etkinleştirmek için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="5e92d-116">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span>
<span data-ttu-id="5e92d-117">ZIP arşivini kullanırken, VM'deki MSI paketini olduğu gibi Önkoşul denetimi vermeyecektir kaydedilmelidir.</span><span class="sxs-lookup"><span data-stu-id="5e92d-117">Be noted that when using the ZIP archive, you won't get the prerequisites check as in the MSI package.</span></span>
<span data-ttu-id="5e92d-118">Windows 10'den önceki Windows sürümleri üzerinde düzgün çalışması için sırasıyla WSMan üzerinden uzaktan iletişim için emin olmanız gerekir. böylece [Önkoşullar](#prerequisites) karşılanır.</span><span class="sxs-lookup"><span data-stu-id="5e92d-118">So in order for remoting over WSMan to work properly on Windows versions prior to Windows 10, you need to make sure the [prerequisites](#prerequisites) are met.</span></span>

## <a name="deploying-on-nano-server"></a><span data-ttu-id="5e92d-119">Nano sunucuda dağıtma</span><span class="sxs-lookup"><span data-stu-id="5e92d-119">Deploying on Nano Server</span></span>

<span data-ttu-id="5e92d-120">Bu yönergeleri varsayar PowerShell sürümü Nano Server görüntüde zaten çalışıyor ve onu tarafından oluşturuldu [Nano Server Image Builder](https://technet.microsoft.com/windows-server-docs/get-started/deploy-nano-server).</span><span class="sxs-lookup"><span data-stu-id="5e92d-120">These instructions assume that a version of PowerShell is already running on the Nano Server image and that it has been generated by the [Nano Server Image Builder](https://technet.microsoft.com/windows-server-docs/get-started/deploy-nano-server).</span></span>
<span data-ttu-id="5e92d-121">Nano Server "gözetimsiz" işletim sistemi ve PowerShell çekirdek ikili dosyalarının dağıtımını iki farklı şekilde oluşabilir:</span><span class="sxs-lookup"><span data-stu-id="5e92d-121">Nano Server is a "headless" OS and deployment of PowerShell Core binaries can happen in two different ways:</span></span>

1. <span data-ttu-id="5e92d-122">Çevrimdışı - Nano Server VHD'nin ve seçilen konumunuza bağlı görüntü içinde ZIP dosyasının içeriğini sıkıştırmasını açın.</span><span class="sxs-lookup"><span data-stu-id="5e92d-122">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
1. <span data-ttu-id="5e92d-123">Çevrimiçi - ZIP dosyasının bir PowerShell oturumu üzerinden aktarım ve seçilen konumda sıkıştırmasını açın.</span><span class="sxs-lookup"><span data-stu-id="5e92d-123">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="5e92d-124">Her iki durumda da, Windows 10 x64 Zip yayın gerekir paketini ve bir "Yönetici" PowerShell örneği içindeki komutları çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5e92d-124">In both cases, you will need the Windows 10 x64 Zip release package and will need to run the commands within an "Administrator" PowerShell instance.</span></span>

### <a name="offline-deployment-of-powershell-core"></a><span data-ttu-id="5e92d-125">PowerShell çekirdek çevrimdışı dağıtımı</span><span class="sxs-lookup"><span data-stu-id="5e92d-125">Offline Deployment of PowerShell Core</span></span>

1. <span data-ttu-id="5e92d-126">Takılı Nano Server yansıması içindeki bir dizinin paketin sıkıştırmasını açmak için sık kullanılan sıkıştırma yardımcı programı kullanın.</span><span class="sxs-lookup"><span data-stu-id="5e92d-126">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
1. <span data-ttu-id="5e92d-127">Yansımayı ve onu önyükleme.</span><span class="sxs-lookup"><span data-stu-id="5e92d-127">Unmount the image and boot it.</span></span>
1. <span data-ttu-id="5e92d-128">Windows PowerShell gelen örneğine bağlanın.</span><span class="sxs-lookup"><span data-stu-id="5e92d-128">Connect to the inbox instance of Windows PowerShell.</span></span>
1. <span data-ttu-id="5e92d-129">Kullanarak bir uzak uç noktası oluşturmak için yönergeleri izleyin [başka bir örneği teknik](#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="5e92d-129">Follow the instructions to create a remoting endpoint using the [another instance technique](#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell-core"></a><span data-ttu-id="5e92d-130">PowerShell çekirdek çevrimiçi dağıtımı</span><span class="sxs-lookup"><span data-stu-id="5e92d-130">Online Deployment of PowerShell Core</span></span>

<span data-ttu-id="5e92d-131">Aşağıdaki adımları çalışan örneği Nano Server ve onun uzak uç nokta yapılandırması için PowerShell çekirdek dağıtımıyla yol gösterecektir.</span><span class="sxs-lookup"><span data-stu-id="5e92d-131">The following steps will guide you through the deployment of PowerShell Core to a running instance of Nano Server and the configuration of its remote endpoint.</span></span>

* <span data-ttu-id="5e92d-132">Windows PowerShell gelen örneğine bağlanın</span><span class="sxs-lookup"><span data-stu-id="5e92d-132">Connect to the inbox instance of Windows PowerShell</span></span>

```powershell
$session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
```

* <span data-ttu-id="5e92d-133">Dosyayı Nano Server örneğine kopyalayın</span><span class="sxs-lookup"><span data-stu-id="5e92d-133">Copy the file to the Nano Server instance</span></span>

```powershell
Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
```

* <span data-ttu-id="5e92d-134">Oturum girin</span><span class="sxs-lookup"><span data-stu-id="5e92d-134">Enter the session</span></span>

```powershell
Enter-PSSession $session
```

* <span data-ttu-id="5e92d-135">Zip dosyasını ayıklayın</span><span class="sxs-lookup"><span data-stu-id="5e92d-135">Extract the Zip file</span></span>

```powershell
# Insert the appropriate version.
Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
```

* <span data-ttu-id="5e92d-136">WSMan tabanlı remoting istiyorsanız kullanarak bir uzak uç noktası oluşturmak için yönergeleri izleyin [başka bir örneği teknik](../core-powershell/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="5e92d-136">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the [another instance technique](../core-powershell/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="instructions-to-create-a-remoting-endpoint"></a><span data-ttu-id="5e92d-137">Bir uzak uç noktası oluşturmak için yönergeler</span><span class="sxs-lookup"><span data-stu-id="5e92d-137">Instructions to Create a Remoting Endpoint</span></span>

<span data-ttu-id="5e92d-138">PowerShell çekirdeği WSMan ve SSH üzerinden PowerShell uzaktan iletişim protokolü (PSRP) destekler.</span><span class="sxs-lookup"><span data-stu-id="5e92d-138">PowerShell Core supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span> <span data-ttu-id="5e92d-139">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="5e92d-139">For more information, see:</span></span>

* <span data-ttu-id="5e92d-140">[SSH PowerShell çekirdek uzaktan çalışma][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="5e92d-140">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
* <span data-ttu-id="5e92d-141">[PowerShell çekirdek WSMan uzaktan çalışma][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="5e92d-141">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

## <a name="artifact-installation-instructions"></a><span data-ttu-id="5e92d-142">Yapı yükleme yönergeleri</span><span class="sxs-lookup"><span data-stu-id="5e92d-142">Artifact Installation Instructions</span></span>

<span data-ttu-id="5e92d-143">Biz her CI yapı ile CoreCLR BITS ile ilgili bir arşiv yayımlama [AppVeyor][].</span><span class="sxs-lookup"><span data-stu-id="5e92d-143">We publish an archive with CoreCLR bits on every CI build with [AppVeyor][].</span></span>

## <a name="coreclr-artifacts"></a><span data-ttu-id="5e92d-144">CoreCLR yapıları</span><span class="sxs-lookup"><span data-stu-id="5e92d-144">CoreCLR Artifacts</span></span>

* <span data-ttu-id="5e92d-145">Zip paketini indirin **yapıları** belirli yapı sekmesinde.</span><span class="sxs-lookup"><span data-stu-id="5e92d-145">Download zip package from **artifacts** tab of the particular build.</span></span>
* <span data-ttu-id="5e92d-146">Engellemeyi kaldırma zip dosyası: dosya Gezgini'nde sağ tıklatın, Özellikler -> 'Engellemeyi Kaldır kutusu ->' uygulamak onay -></span><span class="sxs-lookup"><span data-stu-id="5e92d-146">Unblock zip file: right-click in File Explorer -> Properties -> check 'Unblock' box -> apply</span></span>
* <span data-ttu-id="5e92d-147">Zip dosyasını ayıklayın `bin` dizini</span><span class="sxs-lookup"><span data-stu-id="5e92d-147">Extract zip file to `bin` directory</span></span>
* `./bin/pwsh.exe`

<!-- [download-center]: TODO -->
[serbest]: https://github.com/PowerShell/PowerShell/releases
[signing]: ../../tools/Sign-Package.ps1
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
