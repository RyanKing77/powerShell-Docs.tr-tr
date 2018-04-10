# <a name="ws-management-wsman-remoting-in-powershell-core"></a><span data-ttu-id="6b2a5-101">PowerShell Core’da WS-Management (WSMan) Uzaktan İletişimi</span><span class="sxs-lookup"><span data-stu-id="6b2a5-101">WS-Management (WSMan) Remoting in PowerShell Core</span></span>

## <a name="instructions-to-create-a-remoting-endpoint"></a><span data-ttu-id="6b2a5-102">Bir uzak uç noktası oluşturmak için yönergeler</span><span class="sxs-lookup"><span data-stu-id="6b2a5-102">Instructions to Create a Remoting Endpoint</span></span>

<span data-ttu-id="6b2a5-103">Windows PowerShell çekirdek paket eklenti bir WinRM içeren (`pwrshplugin.dll`) ve bir yükleme komut dosyası (`Install-PowerShellRemoting.ps1`) içinde `$PSHome`.</span><span class="sxs-lookup"><span data-stu-id="6b2a5-103">The PowerShell Core package for Windows includes a WinRM plug-in (`pwrshplugin.dll`) and an installation script (`Install-PowerShellRemoting.ps1`) in `$PSHome`.</span></span>
<span data-ttu-id="6b2a5-104">Bu dosyalar, uç noktasında belirtildiğinde gelen PowerShell uzak bağlantıları kabul etmek PowerShell etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="6b2a5-104">These files enable PowerShell to accept incoming PowerShell remote connections when its endpoint is specified.</span></span>

### <a name="motivation"></a><span data-ttu-id="6b2a5-105">Motivasyon</span><span class="sxs-lookup"><span data-stu-id="6b2a5-105">Motivation</span></span>

<span data-ttu-id="6b2a5-106">PowerShell yüklemesi PowerShell kullanarak uzak bilgisayarlardaki oturumları kurabilen `New-PSSession` ve `Enter-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="6b2a5-106">An installation of PowerShell can establish PowerShell sessions to remote computers using `New-PSSession` and `Enter-PSSession`.</span></span>
<span data-ttu-id="6b2a5-107">Gelen PowerShell uzak bağlantıları kabul etmek üzere etkinleştirmek için kullanıcı bir WinRM uzaktan iletişim uç noktası oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6b2a5-107">To enable it to accept incoming PowerShell remote connections, the user must create a WinRM remoting endpoint.</span></span>
<span data-ttu-id="6b2a5-108">Bu kullanıcı WinRM uç noktası oluşturmak için Yükle-PowerShellRemoting.ps1 çalıştığı bir açık katılımı senaryodur.</span><span class="sxs-lookup"><span data-stu-id="6b2a5-108">This is an explicit opt-in scenario where the user runs Install-PowerShellRemoting.ps1 to create the WinRM endpoint.</span></span>
<span data-ttu-id="6b2a5-109">Biz ek işlevsellik için eklenene kadar yükleme komut dosyasını kısa vadeli bir çözümdür `Enable-PSRemoting` aynı eylem gerçekleştirilemiyor.</span><span class="sxs-lookup"><span data-stu-id="6b2a5-109">The installation script is a short-term solution until we add additional functionality to `Enable-PSRemoting` to perform the same action.</span></span>
<span data-ttu-id="6b2a5-110">Daha fazla ayrıntı için lütfen konuya bakın [#1193](https://github.com/PowerShell/PowerShell/issues/1193).</span><span class="sxs-lookup"><span data-stu-id="6b2a5-110">For more details, please see issue [#1193](https://github.com/PowerShell/PowerShell/issues/1193).</span></span>

### <a name="script-actions"></a><span data-ttu-id="6b2a5-111">Betik eylemleri</span><span class="sxs-lookup"><span data-stu-id="6b2a5-111">Script Actions</span></span>

<span data-ttu-id="6b2a5-112">Komut dosyası</span><span class="sxs-lookup"><span data-stu-id="6b2a5-112">The script</span></span>

1. <span data-ttu-id="6b2a5-113">Eklentinin %windir%\System32\PowerShell içinde bir dizin oluşturur</span><span class="sxs-lookup"><span data-stu-id="6b2a5-113">Creates a directory for the plug-in within %windir%\System32\PowerShell</span></span>
1. <span data-ttu-id="6b2a5-114">Pwrshplugin.dll bu konuma kopyalar.</span><span class="sxs-lookup"><span data-stu-id="6b2a5-114">Copies pwrshplugin.dll to that location</span></span>
1. <span data-ttu-id="6b2a5-115">Bir yapılandırma dosyası oluşturur</span><span class="sxs-lookup"><span data-stu-id="6b2a5-115">Generates a configuration file</span></span>
1. <span data-ttu-id="6b2a5-116">WinRM ile bu eklenti kaydeder</span><span class="sxs-lookup"><span data-stu-id="6b2a5-116">Registers that plug-in with WinRM</span></span>

### <a name="registration"></a><span data-ttu-id="6b2a5-117">Kayıt</span><span class="sxs-lookup"><span data-stu-id="6b2a5-117">Registration</span></span>

<span data-ttu-id="6b2a5-118">Komut dosyası, bir yönetici düzeyi PowerShell oturumu ve iki modda çalışır içinde yürütülmelidir.</span><span class="sxs-lookup"><span data-stu-id="6b2a5-118">The script must be executed within an Administrator-level PowerShell session and runs in two modes.</span></span>

#### <a name="executed-by-the-instance-of-powershell-that-it-will-register"></a><span data-ttu-id="6b2a5-119">Kaydeder PowerShell örneği tarafından yürütülebilir.</span><span class="sxs-lookup"><span data-stu-id="6b2a5-119">Executed by the instance of PowerShell that it will register</span></span>

```powershell
Install-PowerShellRemoting.ps1
```

#### <a name="executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register"></a><span data-ttu-id="6b2a5-120">Başka bir PowerShell örneği kaydeder örnek adına tarafından yürütülebilir.</span><span class="sxs-lookup"><span data-stu-id="6b2a5-120">Executed by another instance of PowerShell on behalf of the instance that it will register</span></span>

```powershell
<path to powershell>\Install-PowerShellRemoting.ps1 -PowerShellHome "<absolute path to the instance's $PSHOME>"
```

<span data-ttu-id="6b2a5-121">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="6b2a5-121">For Example:</span></span>

```powershell
Set-Location -Path 'C:\Program Files\PowerShell\6.0.0\'
.\Install-PowerShellRemoting.ps1 -PowerShellHome "C:\Program Files\PowerShell\6.0.0\"
```

<span data-ttu-id="6b2a5-122">**Not:** hemen betiği çalıştırdıktan sonra tüm mevcut PSRP oturumları sonlandırılacak şekilde remoting kayıt betik WinRM, yeniden başlatılır.</span><span class="sxs-lookup"><span data-stu-id="6b2a5-122">**NOTE:** The remoting registration script will restart WinRM, so all existing PSRP sessions will terminate immediately after the script is run.</span></span> <span data-ttu-id="6b2a5-123">Uzak oturum sırasında çalıştırırsanız, bu bağlantı sonlandırılacak.</span><span class="sxs-lookup"><span data-stu-id="6b2a5-123">If run during a remote session, this will terminate the connection.</span></span>

## <a name="how-to-connect-to-the-new-endpoint"></a><span data-ttu-id="6b2a5-124">Yeni uç noktasına bağlanma</span><span class="sxs-lookup"><span data-stu-id="6b2a5-124">How to Connect to the New Endpoint</span></span>

<span data-ttu-id="6b2a5-125">Bir PowerShell oturumuna yeni PowerShell uç noktası belirterek oluşturun `-ConfigurationName "some endpoint name"`.</span><span class="sxs-lookup"><span data-stu-id="6b2a5-125">Create a PowerShell session to the new PowerShell endpoint by specifying `-ConfigurationName "some endpoint name"`.</span></span> <span data-ttu-id="6b2a5-126">Yukarıdaki örnek PowerShell örneğine bağlanmak için kullanın:</span><span class="sxs-lookup"><span data-stu-id="6b2a5-126">To connect to the PowerShell instance from the example above, use either:</span></span>

```powershell
New-PSSession ... -ConfigurationName "powershell.6.0.0"
Enter-PSSession ... -ConfigurationName "powershell.6.0.0"
```

<span data-ttu-id="6b2a5-127">Unutmayın `New-PSSession` ve `Enter-PSSession` belirtmeyin çağrılarını `-ConfigurationName` varsayılan PowerShell uç hedeflediğini `microsoft.powershell`.</span><span class="sxs-lookup"><span data-stu-id="6b2a5-127">Note that `New-PSSession` and `Enter-PSSession` invocations that do not specify `-ConfigurationName` will target the default PowerShell endpoint, `microsoft.powershell`.</span></span>