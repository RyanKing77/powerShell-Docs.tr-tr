
# <a name="powershell-remoting-over-ssh"></a><span data-ttu-id="fca6e-101">SSH üzerinden PowerShell Uzaktan İletişimi</span><span class="sxs-lookup"><span data-stu-id="fca6e-101">PowerShell Remoting Over SSH</span></span>

## <a name="overview"></a><span data-ttu-id="fca6e-102">Genel bakış</span><span class="sxs-lookup"><span data-stu-id="fca6e-102">Overview</span></span>

<span data-ttu-id="fca6e-103">PowerShell uzaktan iletişimini normalde WinRM bağlantı anlaşması ve veri aktarımı için kullanır.</span><span class="sxs-lookup"><span data-stu-id="fca6e-103">PowerShell remoting normally uses WinRM for connection negotiation and data transport.</span></span>
<span data-ttu-id="fca6e-104">Hem Linux hem de Windows platformları için kullanıma sunulmuştur ve doğru çok platformlu PowerShell uzaktan iletişimini sağlar, SSH Bu uzaktan iletişim uygulama için seçildi.</span><span class="sxs-lookup"><span data-stu-id="fca6e-104">SSH was chosen for this remoting implementation since it is now available for both Linux and Windows platforms and allows true multiplatform PowerShell remoting.</span></span>
<span data-ttu-id="fca6e-105">Ancak, WinRM bu uygulama henüz bunu PowerShell uzak oturumlar için sağlam bir barındırma modeli de sağlar.</span><span class="sxs-lookup"><span data-stu-id="fca6e-105">However, WinRM also provides a robust hosting model for PowerShell remote sessions which this implementation does not yet do.</span></span>
<span data-ttu-id="fca6e-106">Ve bu PowerShell uzak uç nokta yapılandırması ve JEA (yeterli yönetim) henüz desteklenmiyor, bu uygulamada anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="fca6e-106">And this means that PowerShell remote endpoint configuration and JEA (Just Enough Administration) is not yet supported in this implementation.</span></span>

<span data-ttu-id="fca6e-107">PowerShell SSH uzak Windows ve Linux makinelerini arasındaki temel PowerShell oturumu uzaktan gerçekleştirmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="fca6e-107">PowerShell SSH remoting lets you do basic PowerShell session remoting between Windows and Linux machines.</span></span>
<span data-ttu-id="fca6e-108">Bu, barındırma işlemi bir SSH alt olarak hedef makinede bir PowerShell oluşturarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="fca6e-108">This is done by creating a PowerShell hosting process on the target machine as an SSH subsystem.</span></span>
<span data-ttu-id="fca6e-109">Sonuçta bu WinRM uç nokta yapılandırması ve JEA desteklemek için işleyişi benzer daha genel barındırma modeliyle değiştirilecek.</span><span class="sxs-lookup"><span data-stu-id="fca6e-109">Eventually this will be changed to a more general hosting model similar to how WinRM works in order to support endpoint configuration and JEA.</span></span>

<span data-ttu-id="fca6e-110">`New-PSSession`, `Enter-PSSession` Ve `Invoke-Command` cmdlet'leri artık bu yeni uzaktan bağlantı sağlamak için yeni bir parametre vardır</span><span class="sxs-lookup"><span data-stu-id="fca6e-110">The `New-PSSession`, `Enter-PSSession` and `Invoke-Command` cmdlets now have a new parameter set to facilitate this new remoting connection</span></span>

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

<span data-ttu-id="fca6e-111">Bu yeni parametre kümesi, büyük olasılıkla değiştirir ancak şimdilik SSH komut satırından etkileşim veya komutları ve komut dosyaları, üzerinde çağırmak Pssessions'dan oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="fca6e-111">This new parameter set will likely change but for now allows you to create SSH PSSessions that you can interact with from the command line or invoke commands and scripts on.</span></span>
<span data-ttu-id="fca6e-112">Hedef makine ana bilgisayar adı parametresi belirtin ve kullanıcı adı ile kullanıcı adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="fca6e-112">You specify the target machine with the HostName parameter and provide the user name with UserName.</span></span>
<span data-ttu-id="fca6e-113">Cmdlet'ler PowerShell komut satırından etkileşimli olarak çalıştırırken için bir parola istenir.</span><span class="sxs-lookup"><span data-stu-id="fca6e-113">When running the cmdlets interactively at the PowerShell command line you will be prompted for a password.</span></span>
<span data-ttu-id="fca6e-114">Ancak, SSH anahtar kimlik doğrulamasını kullanmak ve bir özel anahtar dosyası yolu KeyFilePath parametresiyle sağlamak için seçeneğiniz de vardır.</span><span class="sxs-lookup"><span data-stu-id="fca6e-114">But you also have the option to use SSH key authentication and provide a private key file path with the KeyFilePath parameter.</span></span>

## <a name="general-setup-information"></a><span data-ttu-id="fca6e-115">Genel Kurulum bilgilerini</span><span class="sxs-lookup"><span data-stu-id="fca6e-115">General setup information</span></span>

<span data-ttu-id="fca6e-116">SSH tüm makinelerde yüklü olması gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="fca6e-116">SSH is required to be installed on all machines.</span></span>
<span data-ttu-id="fca6e-117">Hem de istemci yüklemeniz gerekir (`ssh.exe`) ve sunucu (`sshd.exe`) ve böylece uzak makinelere gelen ve giden deneyimleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fca6e-117">You should install both client (`ssh.exe`) and server (`sshd.exe`) so that you can experiment with remoting to and from the machines.</span></span>
<span data-ttu-id="fca6e-118">Windows için yüklemeniz gerekecek [Win32 OpenSSH github'dan](https://github.com/PowerShell/Win32-OpenSSH/releases).</span><span class="sxs-lookup"><span data-stu-id="fca6e-118">For Windows you will need to install [Win32 OpenSSH from GitHub](https://github.com/PowerShell/Win32-OpenSSH/releases).</span></span>
<span data-ttu-id="fca6e-119">Linux için SSH (dahil olmak üzere sshd sunucusunu) platformunuz için uygun yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="fca6e-119">For Linux you will need to install SSH (including sshd server) appropriate to your platform.</span></span>
<span data-ttu-id="fca6e-120">En son PowerShell derleme veya GitHub SSH uzaktan erişim özelliği olan bir paketten de gerekir.</span><span class="sxs-lookup"><span data-stu-id="fca6e-120">You will also need a recent PowerShell build or package from GitHub having the SSH remoting feature.</span></span>
<span data-ttu-id="fca6e-121">SSH alt sistemler, uzak makinede bir PowerShell işlem oluşturmak için kullanılır ve SSH sunucusu için yapılandırılmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="fca6e-121">SSH subsystems is used to establish a PowerShell process on the remote machine and the SSH server will need to be configured for that.</span></span>
<span data-ttu-id="fca6e-122">Ayrıca parola kimlik doğrulaması ve isteğe bağlı olarak anahtar tabanlı kimlik doğrulamasını etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="fca6e-122">In addition you will need to enable password authentication and optionally key based authentication.</span></span>

## <a name="setup-on-windows-machine"></a><span data-ttu-id="fca6e-123">Windows makinesinde Kurulumu</span><span class="sxs-lookup"><span data-stu-id="fca6e-123">Setup on Windows Machine</span></span>

1. <span data-ttu-id="fca6e-124">[İçin Windows PowerShell Core] en son sürümünü yükleyin</span><span class="sxs-lookup"><span data-stu-id="fca6e-124">Install the latest version of [PowerShell Core for Windows]</span></span>
   - <span data-ttu-id="fca6e-125">SSH remoting desteği bakarak varsa, parametre için ayarlar söyleyebilirsiniz. `New-PSSession`</span><span class="sxs-lookup"><span data-stu-id="fca6e-125">You can tell if it has the SSH remoting support by looking at the parameter sets for `New-PSSession`</span></span>

   ```powershell
   Get-Command New-PSSession -syntax
   ```

   ```output
   New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
   ```

1. <span data-ttu-id="fca6e-126">Son [Win32 OpenSSH] derleme [Kurulum] yönergeleri kullanarak Github'dan yükleyin</span><span class="sxs-lookup"><span data-stu-id="fca6e-126">Install the latest [Win32 OpenSSH] build from GitHub using the [installation] instructions</span></span>
1. <span data-ttu-id="fca6e-127">Win32 OpenSSH yüklendiği konumda sshd_config dosyasında Düzenle</span><span class="sxs-lookup"><span data-stu-id="fca6e-127">Edit the sshd_config file at the location where you installed Win32 OpenSSH</span></span>
   - <span data-ttu-id="fca6e-128">Parola kimlik doğrulamasının etkin olduğundan emin olun</span><span class="sxs-lookup"><span data-stu-id="fca6e-128">Make sure password authentication is enabled</span></span>

   ```
   PasswordAuthentication yes
   ```

    ```
    Subsystem    powershell c:/program files/powershell/6.0.0/pwsh.exe -sshs -NoLogo -NoProfile
    ```

    > [!NOTE]
    > <span data-ttu-id="fca6e-129">OpenSSH için alanları alt sistemi yürütülebilir yollarında çalışmasını engelleyen Windows hata yoktur.</span><span class="sxs-lookup"><span data-stu-id="fca6e-129">There is a bug in OpenSSH for Windows that prevents spaces from working in subsystem executable paths.</span></span>
    > <span data-ttu-id="fca6e-130">Bkz: [daha fazla bilgi için github'daki bu sorunu](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span><span class="sxs-lookup"><span data-stu-id="fca6e-130">See [this issue on GitHub for more information](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span></span>

    <span data-ttu-id="fca6e-131">Tek bir çözüm, boşluk içermeyen Powershell yükleme dizinine hedefine sembolik bağlantı oluşturmaktır:</span><span class="sxs-lookup"><span data-stu-id="fca6e-131">One solution is to create a symlink to the Powershell installation directory that does not contain spaces:</span></span>

    ```powershell
    mklink /D c:\pwsh "C:\Program Files\PowerShell\6.0.0"
    ```

    <span data-ttu-id="fca6e-132">ve ardından alt girin:</span><span class="sxs-lookup"><span data-stu-id="fca6e-132">and then enter it in the subsystem:</span></span>

    ```
    Subsystem    powershell c:\pwsh\pwsh.exe -sshs -NoLogo -NoProfile
    ```

   ```
   Subsystem    powershell c:/program files/powershell/6.0.0/pwsh.exe -sshs -NoLogo -NoProfile
   ```

   - <span data-ttu-id="fca6e-133">İsteğe bağlı olarak anahtar kimlik doğrulamasını etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="fca6e-133">Optionally enable key authentication</span></span>

   ```
   PubkeyAuthentication yes
   ```

1. <span data-ttu-id="fca6e-134">Sshd hizmetini yeniden başlatın</span><span class="sxs-lookup"><span data-stu-id="fca6e-134">Restart the sshd service</span></span>

   ```powershell
   Restart-Service sshd
   ```

1. <span data-ttu-id="fca6e-135">OpenSSH, yol Env değişkenini yüklendiği yolu Ekle</span><span class="sxs-lookup"><span data-stu-id="fca6e-135">Add the path where OpenSSH is installed to your Path Env Variable</span></span>
   - <span data-ttu-id="fca6e-136">Bu satırlar olmalıdır `C:\Program Files\OpenSSH\`</span><span class="sxs-lookup"><span data-stu-id="fca6e-136">This should be along the lines of `C:\Program Files\OpenSSH\`</span></span>
   - <span data-ttu-id="fca6e-137">Bu ssh.exe bulunmasına olanak sağlar</span><span class="sxs-lookup"><span data-stu-id="fca6e-137">This allows for the ssh.exe to be found</span></span>

## <a name="setup-on-linux-ubuntu-1404-machine"></a><span data-ttu-id="fca6e-138">Linux (Ubuntu 14.04) makinede Kur</span><span class="sxs-lookup"><span data-stu-id="fca6e-138">Setup on Linux (Ubuntu 14.04) Machine</span></span>

1. <span data-ttu-id="fca6e-139">Son [Linux için PowerShell Core] derleme Github'dan yükleyin</span><span class="sxs-lookup"><span data-stu-id="fca6e-139">Install the latest [PowerShell Core for Linux] build from GitHub</span></span>
1. <span data-ttu-id="fca6e-140">[Ubuntu SSH] gerektiği şekilde yükle</span><span class="sxs-lookup"><span data-stu-id="fca6e-140">Install [Ubuntu SSH] as needed</span></span>

   ```bash
   sudo apt install openssh-client
   sudo apt install openssh-server
   ```

1. <span data-ttu-id="fca6e-141">Konum /etc/ssh sshd_config dosyasını Düzenle</span><span class="sxs-lookup"><span data-stu-id="fca6e-141">Edit the sshd_config file at location /etc/ssh</span></span>
   - <span data-ttu-id="fca6e-142">Parola kimlik doğrulamasının etkin olduğundan emin olun</span><span class="sxs-lookup"><span data-stu-id="fca6e-142">Make sure password authentication is enabled</span></span>

   ```
   PasswordAuthentication yes
   ```

   - <span data-ttu-id="fca6e-143">Bir PowerShell alt sistemi Girişi Ekle</span><span class="sxs-lookup"><span data-stu-id="fca6e-143">Add a PowerShell subsystem entry</span></span>

   ```
   Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   - <span data-ttu-id="fca6e-144">İsteğe bağlı olarak anahtar kimlik doğrulamasını etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="fca6e-144">Optionally enable key authentication</span></span>

   ```
   PubkeyAuthentication yes
   ```

1. <span data-ttu-id="fca6e-145">Sshd hizmetini yeniden başlatın</span><span class="sxs-lookup"><span data-stu-id="fca6e-145">Restart the sshd service</span></span>

   ```bash
   sudo service sshd restart
   ```

## <a name="setup-on-macos-machine"></a><span data-ttu-id="fca6e-146">Mac OS makinesinde Kurulumu</span><span class="sxs-lookup"><span data-stu-id="fca6e-146">Setup on MacOS Machine</span></span>

1. <span data-ttu-id="fca6e-147">Son [MacOS için PowerShell Core] derleme yükleme</span><span class="sxs-lookup"><span data-stu-id="fca6e-147">Install the latest [PowerShell Core for MacOS] build</span></span>
   - <span data-ttu-id="fca6e-148">SSH uzaktan iletişim, aşağıdaki adımları izleyerek etkin olduğundan emin olun:</span><span class="sxs-lookup"><span data-stu-id="fca6e-148">Make sure SSH Remoting is enabled by following these steps:</span></span>
     - <span data-ttu-id="fca6e-149">Açık `System Preferences`</span><span class="sxs-lookup"><span data-stu-id="fca6e-149">Open `System Preferences`</span></span>
     - <span data-ttu-id="fca6e-150">Tıklayın `Sharing`</span><span class="sxs-lookup"><span data-stu-id="fca6e-150">Click on `Sharing`</span></span>
     - <span data-ttu-id="fca6e-151">Denetleme `Remote Login` -şeklinde olmalıdır `Remote Login: On`</span><span class="sxs-lookup"><span data-stu-id="fca6e-151">Check `Remote Login` - Should say `Remote Login: On`</span></span>
     - <span data-ttu-id="fca6e-152">Uygun kullanıcılar erişime izin ver</span><span class="sxs-lookup"><span data-stu-id="fca6e-152">Allow access to appropriate users</span></span>
1. <span data-ttu-id="fca6e-153">Düzen `sshd_config` dosya konumunda `/private/etc/ssh/sshd_config`</span><span class="sxs-lookup"><span data-stu-id="fca6e-153">Edit the `sshd_config` file at location `/private/etc/ssh/sshd_config`</span></span>
   - <span data-ttu-id="fca6e-154">Tercih ettiğiniz düzenleyiciyi kullanın veya</span><span class="sxs-lookup"><span data-stu-id="fca6e-154">Use your favorite editor or</span></span>

     ```bash
     sudo nano /private/etc/ssh/sshd_config
     ```

   - <span data-ttu-id="fca6e-155">Parola kimlik doğrulamasının etkin olduğundan emin olun</span><span class="sxs-lookup"><span data-stu-id="fca6e-155">Make sure password authentication is enabled</span></span>

     ```
     PasswordAuthentication yes
     ```

   - <span data-ttu-id="fca6e-156">Bir PowerShell alt sistemi Girişi Ekle</span><span class="sxs-lookup"><span data-stu-id="fca6e-156">Add a PowerShell subsystem entry</span></span>

     ```
     Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
     ```

   - <span data-ttu-id="fca6e-157">İsteğe bağlı olarak anahtar kimlik doğrulamasını etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="fca6e-157">Optionally enable key authentication</span></span>

     ```
     PubkeyAuthentication yes
     ```

1. <span data-ttu-id="fca6e-158">Sshd hizmetini yeniden başlatın</span><span class="sxs-lookup"><span data-stu-id="fca6e-158">Restart the sshd service</span></span>

   ```bash
   sudo launchctl stop com.openssh.sshd
   sudo launchctl start com.openssh.sshd
   ```

## <a name="powershell-remoting-example"></a><span data-ttu-id="fca6e-159">PowerShell uzaktan iletişimini örneği</span><span class="sxs-lookup"><span data-stu-id="fca6e-159">PowerShell Remoting Example</span></span>

<span data-ttu-id="fca6e-160">Uzaktan test etmek için en kolay yolu, tek bir makinede denemektir olmaktır.</span><span class="sxs-lookup"><span data-stu-id="fca6e-160">The easiest way to test remoting is to just try it on a single machine.</span></span>
<span data-ttu-id="fca6e-161">Burada miyim Linux kutusundaki aynı makineye bir uzak oturumu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fca6e-161">Here I will create a remote session back to the same machine on a Linux box.</span></span>
<span data-ttu-id="fca6e-162">SSH ana bilgisayar yanı sıra parola istemlerinin doğrulamak isteyen istemleri görüyoruz için PowerShell cmdlet'leri bir komut isteminden kullanıyorum, dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="fca6e-162">Notice that I am using PowerShell cmdlets from a command prompt so we see prompts from SSH asking to verify the host computer as well as password prompts.</span></span>
<span data-ttu-id="fca6e-163">Uzaktan iletişim var. çalıştığından emin olmak için Windows makine ve ardından uzak ana bilgisayar adı yalnızca değiştirerek makine arasında aynı şeyi yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fca6e-163">You can do the same thing on a Windows machine to ensure remoting is working there and then remote between machines by simply changing the host name.</span></span>

```powershell
#
# Linux to Linux
#
$session = New-PSSession -HostName UbuntuVM1 -UserName TestUser
```

```output
The authenticity of host 'UbuntuVM1 (9.129.17.107)' cannot be established.
ECDSA key fingerprint is SHA256:2kCbnhT2dUE6WCGgVJ8Hyfu1z2wE4lifaJXLO7QJy0Y.
Are you sure you want to continue connecting (yes/no)?
TestUser@UbuntuVM1s password:
```

```powershell
$session
```

```output
 Id Name            ComputerName    ComputerType    State         ConfigurationName     Availability
 -- ----            ------------    ------------    -----         -----------------     ------------
  1 SSH1            UbuntuVM1       RemoteMachine   Opened        DefaultShell             Available
```

```powershell
Enter-PSSession $session
```

```output
[UbuntuVM1]: PS /home/TestUser> uname -a
Linux TestUser-UbuntuVM1 4.2.0-42-generic 49~14.04.1-Ubuntu SMP Wed Jun 29 20:22:11 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

[UbuntuVM1]: PS /home/TestUser> Exit-PSSession
```

```powershell
Invoke-Command $session -ScriptBlock { Get-Process powershell }
```

```output
Handles  NPM(K)    PM(K)      WS(K)     CPU(s)     Id  SI ProcessName                    PSComputerName
-------  ------    -----      -----     ------     --  -- -----------                    --------------
      0       0        0         19       3.23  10635 635 powershell                     UbuntuVM1
      0       0        0         21       4.92  11033 017 powershell                     UbuntuVM1
      0       0        0         20       3.07  11076 076 powershell                     UbuntuVM1
```

```powershell
#
# Linux to Windows
#
Enter-PSSession -HostName WinVM1 -UserName PTestName
```

```output
PTestName@WinVM1s password:
```

```powershell
[WinVM1]: PS C:\Users\PTestName\Documents> cmd /c ver
```

```output
Microsoft Windows [Version 10.0.10586]
```

```powershell
#
# Windows to Windows
#
C:\Users\PSUser\Documents>pwsh.exe
```

```output
PowerShell
Copyright (c) Microsoft Corporation. All rights reserved.
```

```powershell
$session = New-PSSession -HostName WinVM2 -UserName PSRemoteUser
```

```output
The authenticity of host 'WinVM2 (10.13.37.3)' can't be established.
ECDSA key fingerprint is SHA256:kSU6slAROyQVMEynVIXAdxSiZpwDBigpAF/TXjjWjmw.
Are you sure you want to continue connecting (yes/no)?
Warning: Permanently added 'WinVM2,10.13.37.3' (ECDSA) to the list of known hosts.
PSRemoteUser@WinVM2's password:
```

```powershell
$session
```

```output
 Id Name            ComputerName    ComputerType    State         ConfigurationName     Availability
 -- ----            ------------    ------------    -----         -----------------     ------------
  1 SSH1            WinVM2          RemoteMachine   Opened        DefaultShell             Available
```

```powershell
Enter-PSSession -Session $session
```

```output
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

### <a name="known-issues"></a><span data-ttu-id="fca6e-164">Bilinen Sorunlar</span><span class="sxs-lookup"><span data-stu-id="fca6e-164">Known Issues</span></span>

- <span data-ttu-id="fca6e-165">Linux makinesi uzak oturumu sudo komutu çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="fca6e-165">sudo command does not work in remote session to Linux machine.</span></span>

## <a name="see-also"></a><span data-ttu-id="fca6e-166">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="fca6e-166">See Also</span></span>

[<span data-ttu-id="fca6e-167">İçin Windows PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="fca6e-167">PowerShell Core for Windows</span></span>](../setup/installing-powershell-core-on-windows.md#msi)

[<span data-ttu-id="fca6e-168">Linux için PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="fca6e-168">PowerShell Core for Linux</span></span>](../setup/installing-powershell-core-on-linux.md#ubuntu-1404)

[<span data-ttu-id="fca6e-169">MacOS için PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="fca6e-169">PowerShell Core for MacOS</span></span>](../setup/installing-powershell-core-on-macos.md)

[<span data-ttu-id="fca6e-170">Win32 OpenSSH</span><span class="sxs-lookup"><span data-stu-id="fca6e-170">Win32 OpenSSH</span></span>](https://github.com/PowerShell/Win32-OpenSSH/releases)

[<span data-ttu-id="fca6e-171">Yükleme</span><span class="sxs-lookup"><span data-stu-id="fca6e-171">installation</span></span>](https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH)

[<span data-ttu-id="fca6e-172">Ubuntu SSH</span><span class="sxs-lookup"><span data-stu-id="fca6e-172">Ubuntu SSH</span></span>](https://help.ubuntu.com/lts/serverguide/openssh-server.html)