# <a name="powershell-remoting-over-ssh"></a><span data-ttu-id="e9aca-101">SSH üzerinden PowerShell Uzaktan İletişimi</span><span class="sxs-lookup"><span data-stu-id="e9aca-101">PowerShell Remoting Over SSH</span></span>

## <a name="overview"></a><span data-ttu-id="e9aca-102">Genel bakış</span><span class="sxs-lookup"><span data-stu-id="e9aca-102">Overview</span></span>

<span data-ttu-id="e9aca-103">PowerShell uzaktan iletişim bağlantı anlaşması ve veri aktarımı için normalde WinRM kullanır.</span><span class="sxs-lookup"><span data-stu-id="e9aca-103">PowerShell remoting normally uses WinRM for connection negotiation and data transport.</span></span>
<span data-ttu-id="e9aca-104">Linux ve Windows platformları için kullanıma sunulmuştur ve doğru çok platformlu PowerShell uzaktan iletişimi sağlayan SSH bu remoting uygulama için seçildi.</span><span class="sxs-lookup"><span data-stu-id="e9aca-104">SSH was chosen for this remoting implementation since it is now available for both Linux and Windows platforms and allows true multiplatform PowerShell remoting.</span></span>
<span data-ttu-id="e9aca-105">Ancak, WinRM Ayrıca, bu uygulama henüz yapmak PowerShell uzak oturumlar için sağlam bir barındırma modeli sağlar.</span><span class="sxs-lookup"><span data-stu-id="e9aca-105">However, WinRM also provides a robust hosting model for PowerShell remote sessions which this implementation does not yet do.</span></span>
<span data-ttu-id="e9aca-106">Ve bu PowerShell uzak uç nokta yapılandırması ve JEA (yalnızca yeterince yönetim) henüz desteklenmiyor, bu uygulama anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e9aca-106">And this means that PowerShell remote endpoint configuration and JEA (Just Enough Administration) is not yet supported in this implementation.</span></span>

<span data-ttu-id="e9aca-107">PowerShell SSH remoting Windows ve Linux makineler arasındaki temel PowerShell oturumu remoting yapmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="e9aca-107">PowerShell SSH remoting lets you do basic PowerShell session remoting between Windows and Linux machines.</span></span>
<span data-ttu-id="e9aca-108">Bu, barındırma işlemi SSH alt sistemi olarak hedef makinede bir PowerShell oluşturarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="e9aca-108">This is done by creating a PowerShell hosting process on the target machine as an SSH subsystem.</span></span>
<span data-ttu-id="e9aca-109">Sonuç olarak bu WinRM uç nokta yapılandırması ve JEA desteklemek için işleyişi benzer bir daha genel barındırma modeli için değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="e9aca-109">Eventually this will be changed to a more general hosting model similar to how WinRM works in order to support endpoint configuration and JEA.</span></span>

<span data-ttu-id="e9aca-110">New-PSSession, Enter-PSSession ve Invoke-Command cmdlet'leri artık bu yeni uzaktan iletişim bağlantı kolaylaştırmak için yeni bir parametre vardır</span><span class="sxs-lookup"><span data-stu-id="e9aca-110">The New-PSSession, Enter-PSSession and Invoke-Command cmdlets now have a new parameter set to facilitate this new remoting connection</span></span>

```powershell
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

<span data-ttu-id="e9aca-111">Bu yeni parametre kümesi olasılıkla değişir ancak şu an için SSH komut satırından etkileşimde veya üzerinde komutları ve komut dosyaları çağırma Pssessions'dan oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="e9aca-111">This new parameter set will likely change but for now allows you to create SSH PSSessions that you can interact with from the command line or invoke commands and scripts on.</span></span>
<span data-ttu-id="e9aca-112">Ana bilgisayar adı parametresiyle hedef makine belirtin ve kullanıcı adı ile kullanıcı adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="e9aca-112">You specify the target machine with the HostName parameter and provide the user name with UserName.</span></span>
<span data-ttu-id="e9aca-113">Cmdlet'ler PowerShell komut satırında etkileşimli olarak çalıştırırken için bir parola istenir.</span><span class="sxs-lookup"><span data-stu-id="e9aca-113">When running the cmdlets interactively at the PowerShell command line you will be prompted for a password.</span></span>
<span data-ttu-id="e9aca-114">Ancak, aynı zamanda SSH anahtar kimlik doğrulaması kullanmak ve bir özel anahtar dosyası yolu KeyFilePath parametresiyle sağlamak için seçeneğiniz vardır.</span><span class="sxs-lookup"><span data-stu-id="e9aca-114">But you also have the option to use SSH key authentication and provide a private key file path with the KeyFilePath parameter.</span></span>

## <a name="general-setup-information"></a><span data-ttu-id="e9aca-115">Genel Kurulum bilgileri</span><span class="sxs-lookup"><span data-stu-id="e9aca-115">General setup information</span></span>

<span data-ttu-id="e9aca-116">SSH tüm makinelerde yüklü olması gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e9aca-116">SSH is required to be installed on all machines.</span></span>
<span data-ttu-id="e9aca-117">Böylece remoting makinelere gelen ve giden deneyimleyebilirsiniz (ssh.exe) istemci ve sunucunun (sshd.exe) yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e9aca-117">You should install both client (ssh.exe) and server (sshd.exe) so that you can experiment with remoting to and from the machines.</span></span>
<span data-ttu-id="e9aca-118">Windows için yüklemeniz gerekecek [Win32 OpenSSH github'dan](https://github.com/PowerShell/Win32-OpenSSH/releases).</span><span class="sxs-lookup"><span data-stu-id="e9aca-118">For Windows you will need to install [Win32 OpenSSH from GitHub](https://github.com/PowerShell/Win32-OpenSSH/releases).</span></span>
<span data-ttu-id="e9aca-119">Linux için SSH (dahil olmak üzere sshd sunucu) platformunuz için uygun yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e9aca-119">For Linux you will need to install SSH (including sshd server) appropriate to your platform.</span></span>
<span data-ttu-id="e9aca-120">Son PowerShell derleme veya SSH uzaktan erişim özelliği olan github'dan paketi de gerekir.</span><span class="sxs-lookup"><span data-stu-id="e9aca-120">You will also need a recent PowerShell build or package from GitHub having the SSH remoting feature.</span></span>
<span data-ttu-id="e9aca-121">SSH alt sistemleri uzak makinede PowerShell işlem kurmak için kullanılır ve SSH sunucusu için yapılandırılmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e9aca-121">SSH subsystems is used to establish a PowerShell process on the remote machine and the SSH server will need to be configured for that.</span></span>
<span data-ttu-id="e9aca-122">Ayrıca parola kimlik doğrulaması ve isteğe bağlı olarak anahtar tabanlı kimlik doğrulamasını etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e9aca-122">In addition you will need to enable password authentication and optionally key based authentication.</span></span>

## <a name="setup-on-windows-machine"></a><span data-ttu-id="e9aca-123">Kurulum Windows makinesinde</span><span class="sxs-lookup"><span data-stu-id="e9aca-123">Setup on Windows Machine</span></span>

1. <span data-ttu-id="e9aca-124">En son sürümünü yüklemek [Windows PowerShell çekirdek]</span><span class="sxs-lookup"><span data-stu-id="e9aca-124">Install the latest version of [PowerShell Core for Windows]</span></span>
    - <span data-ttu-id="e9aca-125">Bakarak SSH remoting desteği varsa, New-PSSession için parametre kümeleri söyleyin</span><span class="sxs-lookup"><span data-stu-id="e9aca-125">You can tell if it has the SSH remoting support by looking at the parameter sets for New-PSSession</span></span>

    ```powershell
    PS> Get-Command New-PSSession -syntax
    New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
    ```

1. <span data-ttu-id="e9aca-126">En son yükleme [Win32 OpenSSH] GitHub kullanarak yapı [yükleme] yönergeleri</span><span class="sxs-lookup"><span data-stu-id="e9aca-126">Install the latest [Win32 OpenSSH] build from GitHub using the [installation] instructions</span></span>
1. <span data-ttu-id="e9aca-127">Win32 OpenSSH yüklendiği konumda sshd_config dosyayı düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="e9aca-127">Edit the sshd_config file at the location where you installed Win32 OpenSSH</span></span>
    - <span data-ttu-id="e9aca-128">Parola kimlik doğrulaması etkin olduğundan emin olun</span><span class="sxs-lookup"><span data-stu-id="e9aca-128">Make sure password authentication is enabled</span></span>

    ```
    PasswordAuthentication yes
    ```

    - <span data-ttu-id="e9aca-129">Bir PowerShell alt sistemi girişi ekleme, değiştirme `c:/program files/powershell/6.0.0/pwsh.exe` kullanmak istediğiniz sürüm için doğru yolu ile</span><span class="sxs-lookup"><span data-stu-id="e9aca-129">Add a PowerShell subsystem entry, replace `c:/program files/powershell/6.0.0/pwsh.exe` with the correct path to the version you want to use</span></span>

    ```
    Subsystem    powershell c:/program files/powershell/6.0.0/pwsh.exe -sshs -NoLogo -NoProfile
    ```

    - <span data-ttu-id="e9aca-130">İsteğe bağlı olarak anahtar kimlik doğrulamasını etkinleştir</span><span class="sxs-lookup"><span data-stu-id="e9aca-130">Optionally enable key authentication</span></span>

    ```
    PubkeyAuthentication yes
    ```

1. <span data-ttu-id="e9aca-131">Sshd hizmetini yeniden başlatın</span><span class="sxs-lookup"><span data-stu-id="e9aca-131">Restart the sshd service</span></span>

    ```powershell
    Restart-Service sshd
    ```

1. <span data-ttu-id="e9aca-132">OpenSSH, yol Env değişkenini yüklendiği yolu Ekle</span><span class="sxs-lookup"><span data-stu-id="e9aca-132">Add the path where OpenSSH is installed to your Path Env Variable</span></span>
    - <span data-ttu-id="e9aca-133">Bu satırları olmalıdır `C:\Program Files\OpenSSH\`</span><span class="sxs-lookup"><span data-stu-id="e9aca-133">This should be along the lines of `C:\Program Files\OpenSSH\`</span></span>
    - <span data-ttu-id="e9aca-134">Bu ssh.exe bulunacak sağlar</span><span class="sxs-lookup"><span data-stu-id="e9aca-134">This allows for the ssh.exe to be found</span></span>

## <a name="setup-on-linux-ubuntu-1404-machine"></a><span data-ttu-id="e9aca-135">Linux (Ubuntu 14.04) makinede Kurulumu</span><span class="sxs-lookup"><span data-stu-id="e9aca-135">Setup on Linux (Ubuntu 14.04) Machine</span></span>

1. <span data-ttu-id="e9aca-136">En son yükleme [Linux için PowerShell çekirdek] Github'dan derleme</span><span class="sxs-lookup"><span data-stu-id="e9aca-136">Install the latest [PowerShell Core for Linux] build from GitHub</span></span>
1. <span data-ttu-id="e9aca-137">Yükleme [Ubuntu SSH] gerektiğinde</span><span class="sxs-lookup"><span data-stu-id="e9aca-137">Install [Ubuntu SSH] as needed</span></span>

    ```bash
    sudo apt install openssh-client
    sudo apt install openssh-server
    ```

1. <span data-ttu-id="e9aca-138">Konum /etc/ssh sshd_config dosyasını düzenleyin</span><span class="sxs-lookup"><span data-stu-id="e9aca-138">Edit the sshd_config file at location /etc/ssh</span></span>
    - <span data-ttu-id="e9aca-139">Parola kimlik doğrulaması etkin olduğundan emin olun</span><span class="sxs-lookup"><span data-stu-id="e9aca-139">Make sure password authentication is enabled</span></span>

    ```
    PasswordAuthentication yes
    ```

    - <span data-ttu-id="e9aca-140">Bir PowerShell alt sistemi Girişi Ekle</span><span class="sxs-lookup"><span data-stu-id="e9aca-140">Add a PowerShell subsystem entry</span></span>

    ```
    Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
    ```

    - <span data-ttu-id="e9aca-141">İsteğe bağlı olarak anahtar kimlik doğrulamasını etkinleştir</span><span class="sxs-lookup"><span data-stu-id="e9aca-141">Optionally enable key authentication</span></span>

    ```
    PubkeyAuthentication yes
    ```

1. <span data-ttu-id="e9aca-142">Sshd hizmetini yeniden başlatın</span><span class="sxs-lookup"><span data-stu-id="e9aca-142">Restart the sshd service</span></span>

    ```bash
    sudo service sshd restart
    ```

## <a name="setup-on-macos-machine"></a><span data-ttu-id="e9aca-143">Kurulum MacOS makinede</span><span class="sxs-lookup"><span data-stu-id="e9aca-143">Setup on MacOS Machine</span></span>

1. <span data-ttu-id="e9aca-144">En son yükleme [PowerShell çekirdek MacOS için] derleme</span><span class="sxs-lookup"><span data-stu-id="e9aca-144">Install the latest [PowerShell Core for MacOS] build</span></span>
    - <span data-ttu-id="e9aca-145">Aşağıdaki adımları izleyerek SSH uzatan iletişimin etkinleştirildiğinden emin olun:</span><span class="sxs-lookup"><span data-stu-id="e9aca-145">Make sure SSH Remoting is enabled by following these steps:</span></span>
      - <span data-ttu-id="e9aca-146">Açık `System Preferences`</span><span class="sxs-lookup"><span data-stu-id="e9aca-146">Open `System Preferences`</span></span>
      - <span data-ttu-id="e9aca-147">' Yi tıklatın `Sharing`</span><span class="sxs-lookup"><span data-stu-id="e9aca-147">Click on `Sharing`</span></span>
      - <span data-ttu-id="e9aca-148">Denetleme `Remote Login` -yazması gerekir `Remote Login: On`</span><span class="sxs-lookup"><span data-stu-id="e9aca-148">Check `Remote Login` - Should say `Remote Login: On`</span></span>
      - <span data-ttu-id="e9aca-149">Uygun kullanıcıların erişmesine izin vermek</span><span class="sxs-lookup"><span data-stu-id="e9aca-149">Allow access to appropriate users</span></span>
1. <span data-ttu-id="e9aca-150">Düzen `sshd_config` konumda dosya `/private/etc/ssh/sshd_config`</span><span class="sxs-lookup"><span data-stu-id="e9aca-150">Edit the `sshd_config` file at location `/private/etc/ssh/sshd_config`</span></span>
    - <span data-ttu-id="e9aca-151">Tercih ettiğiniz düzenleyicisi kullanın veya</span><span class="sxs-lookup"><span data-stu-id="e9aca-151">Use your favorite editor or</span></span>

    ```bash
    sudo nano /private/etc/ssh/sshd_config
    ```

    - <span data-ttu-id="e9aca-152">Parola kimlik doğrulaması etkin olduğundan emin olun</span><span class="sxs-lookup"><span data-stu-id="e9aca-152">Make sure password authentication is enabled</span></span>

    ```
    PasswordAuthentication yes
    ```

    - <span data-ttu-id="e9aca-153">Bir PowerShell alt sistemi Girişi Ekle</span><span class="sxs-lookup"><span data-stu-id="e9aca-153">Add a PowerShell subsystem entry</span></span>

    ```
    Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
    ```

    - <span data-ttu-id="e9aca-154">İsteğe bağlı olarak anahtar kimlik doğrulamasını etkinleştir</span><span class="sxs-lookup"><span data-stu-id="e9aca-154">Optionally enable key authentication</span></span>

    ```
    PubkeyAuthentication yes
    ```

1. <span data-ttu-id="e9aca-155">Sshd hizmetini yeniden başlatın</span><span class="sxs-lookup"><span data-stu-id="e9aca-155">Restart the sshd service</span></span>

    ```bash
    sudo launchctl stop com.openssh.sshd
    sudo launchctl start com.openssh.sshd
    ```

## <a name="powershell-remoting-example"></a><span data-ttu-id="e9aca-156">PowerShell uzaktan iletişim örneği</span><span class="sxs-lookup"><span data-stu-id="e9aca-156">PowerShell Remoting Example</span></span>

<span data-ttu-id="e9aca-157">Yalnızca tek bir makinede denemek için Remoting test etmek için en kolay yolu değil.</span><span class="sxs-lookup"><span data-stu-id="e9aca-157">The easiest way to test remoting is to just try it on a single machine.</span></span>
<span data-ttu-id="e9aca-158">Burada ı Linux kutusundaki aynı makineye uzak bir oturum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e9aca-158">Here I will create a remote session back to the same machine on a Linux box.</span></span>
<span data-ttu-id="e9aca-159">Biz ana bilgisayarın yanı sıra parola istemi doğrulamak isteyen SSH istemleri görmek için PowerShell cmdlet'leri bir komut isteminden kullanıyorum, dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="e9aca-159">Notice that I am using PowerShell cmdlets from a command prompt so we see prompts from SSH asking to verify the host computer as well as password prompts.</span></span>
<span data-ttu-id="e9aca-160">Remoting var. çalıştığından emin olmak için Windows makinesine ve ardından uzak ana bilgisayar adı yalnızca değiştirerek makineler arasında aynı şey yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e9aca-160">You can do the same thing on a Windows machine to ensure remoting is working there and then remote between machines by simply changing the host name.</span></span>

```powershell
#
# Linux to Linux
#
PS /home/TestUser> $session = New-PSSession -HostName UbuntuVM1 -UserName TestUser
The authenticity of host 'UbuntuVM1 (9.129.17.107)' cannot be established.
ECDSA key fingerprint is SHA256:2kCbnhT2dUE6WCGgVJ8Hyfu1z2wE4lifaJXLO7QJy0Y.
Are you sure you want to continue connecting (yes/no)?
TestUser@UbuntuVM1s password:

PS /home/TestUser> $session

 Id Name            ComputerName    ComputerType    State         ConfigurationName     Availability
 -- ----            ------------    ------------    -----         -----------------     ------------
  1 SSH1            UbuntuVM1       RemoteMachine   Opened        DefaultShell             Available

PS /home/TestUser> Enter-PSSession $session

[UbuntuVM1]: PS /home/TestUser> uname -a
Linux TestUser-UbuntuVM1 4.2.0-42-generic 49~14.04.1-Ubuntu SMP Wed Jun 29 20:22:11 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

[UbuntuVM1]: PS /home/TestUser> Exit-PSSession

PS /home/TestUser> Invoke-Command $session -ScriptBlock { Get-Process powershell }

Handles  NPM(K)    PM(K)      WS(K)     CPU(s)     Id  SI ProcessName                    PSComputerName
-------  ------    -----      -----     ------     --  -- -----------                    --------------
      0       0        0         19       3.23  10635 635 powershell                     UbuntuVM1
      0       0        0         21       4.92  11033 017 powershell                     UbuntuVM1
      0       0        0         20       3.07  11076 076 powershell                     UbuntuVM1


#
# Linux to Windows
#
PS /home/TestUser> Enter-PSSession -HostName WinVM1 -UserName PTestName
PTestName@WinVM1s password:

[WinVM1]: PS C:\Users\PTestName\Documents> cmd /c ver

Microsoft Windows [Version 10.0.10586]

[WinVM1]: PS C:\Users\PTestName\Documents>

#
# Windows to Windows
#
C:\Users\PSUser\Documents>pwsh.exe
PowerShell
Copyright (c) Microsoft Corporation. All rights reserved.

PS C:\Users\PSUser\Documents> $session = New-PSSession -HostName WinVM2 -UserName PSRemoteUser
The authenticity of host 'WinVM2 (10.13.37.3)' can't be established.
ECDSA key fingerprint is SHA256:kSU6slAROyQVMEynVIXAdxSiZpwDBigpAF/TXjjWjmw.
Are you sure you want to continue connecting (yes/no)?
Warning: Permanently added 'WinVM2,10.13.37.3' (ECDSA) to the list of known hosts.
PSRemoteUser@WinVM2's password:
PS C:\Users\PSUser\Documents> $session

 Id Name            ComputerName    ComputerType    State         ConfigurationName     Availability
 -- ----            ------------    ------------    -----         -----------------     ------------
  1 SSH1            WinVM2          RemoteMachine   Opened        DefaultShell             Available


PS C:\Users\PSUser\Documents> Enter-PSSession -Session $session
[WinVM2]: PS C:\Users\PSRemoteUser\Documents> $PSVersionTable

Name                           Value
----                           -----
PSEdition                      Core
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
SerializationVersion           1.1.0.1
BuildVersion                   3.0.0.0
CLRVersion
PSVersion                      6.0.0-alpha
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
GitCommitId                    v6.0.0-alpha.17


[WinVM2]: PS C:\Users\PSRemoteUser\Documents>
```

### <a name="known-issues"></a><span data-ttu-id="e9aca-161">Bilinen Sorunlar</span><span class="sxs-lookup"><span data-stu-id="e9aca-161">Known Issues</span></span>

1. <span data-ttu-id="e9aca-162">sudo komutu Linux makinesinde uzaktan oturumunda çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="e9aca-162">sudo command does not work in remote session to Linux machine.</span></span>

[Windows PowerShell çekirdek]: ../setup/installing-powershell-core-on-windows.md#msi
[PowerShell Core for Windows]: ../setup/installing-powershell-core-on-windows.md#msi
[Linux için PowerShell çekirdek]: ../setup/installing-powershell-core-on-linux.md#ubuntu-1404
[PowerShell Core for Linux]: ../setup/installing-powershell-core-on-linux.md#ubuntu-1404
[PowerShell çekirdek MacOS için]: ../setup/installing-powershell-core-on-macos.md
[PowerShell Core for MacOS]: ../setup/installing-powershell-core-on-macos.md
[Win32 OpenSSH]: https://github.com/PowerShell/Win32-OpenSSH/releases
[Yükleme]: https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH
[installation]: https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH
[Ubuntu SSH]: https://help.ubuntu.com/lts/serverguide/openssh-server.html
