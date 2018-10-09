---
title: SSH üzerinden PowerShell Uzaktan İletişimi
description: SSH kullanarak PowerShell core'da uzaktan iletişim
ms.date: 08/14/2018
ms.openlocfilehash: 84c3896fe28847beb03e930f933bb4a9dfad397f
ms.sourcegitcommit: 6749f67c32e05999e10deb9d45f90f45ac21a599
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48851246"
---
# <a name="powershell-remoting-over-ssh"></a><span data-ttu-id="340fe-103">SSH üzerinden PowerShell Uzaktan İletişimi</span><span class="sxs-lookup"><span data-stu-id="340fe-103">PowerShell Remoting Over SSH</span></span>

## <a name="overview"></a><span data-ttu-id="340fe-104">Genel bakış</span><span class="sxs-lookup"><span data-stu-id="340fe-104">Overview</span></span>

<span data-ttu-id="340fe-105">PowerShell uzaktan iletişimini normalde WinRM bağlantı anlaşması ve veri aktarımı için kullanır.</span><span class="sxs-lookup"><span data-stu-id="340fe-105">PowerShell remoting normally uses WinRM for connection negotiation and data transport.</span></span> <span data-ttu-id="340fe-106">SSH, Linux ve Windows platformları için kullanıma sunulmuştur ve doğru çok platformlu PowerShell uzaktan iletişimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="340fe-106">SSH is now available for Linux and Windows platforms and allows true multiplatform PowerShell remoting.</span></span>

<span data-ttu-id="340fe-107">WinRM, uzak PowerShell oturumları için sağlam bir barındırma modeli sağlar.</span><span class="sxs-lookup"><span data-stu-id="340fe-107">WinRM provides a robust hosting model for PowerShell remote sessions.</span></span> <span data-ttu-id="340fe-108">Bu uygulama SSH tabanlı uzak şu anda değil, uzak uç nokta yapılandırması ve JEA (yeterli yönetim) destekler.</span><span class="sxs-lookup"><span data-stu-id="340fe-108">which this implementation SSH-based remoting doesn't currently support remote endpoint configuration and JEA (Just Enough Administration).</span></span>

<span data-ttu-id="340fe-109">SSH, uzak Windows ve Linux makinelerini arasındaki temel PowerShell oturumu uzaktan gerçekleştirmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="340fe-109">SSH remoting lets you do basic PowerShell session remoting between Windows and Linux machines.</span></span> <span data-ttu-id="340fe-110">SSH uzak PowerShell ana bilgisayar işlemi hedef makinede bir SSH alt oluşturur.</span><span class="sxs-lookup"><span data-stu-id="340fe-110">SSH Remoting creates a PowerShell host process on the target machine as an SSH subsystem.</span></span>
<span data-ttu-id="340fe-111">Sonunda size bir genel barındırma modeli, uç nokta yapılandırması ve JEA desteklemek için WinRM ile benzer uygulayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="340fe-111">Eventually we'll implement a general hosting model, similar to WinRM, to support endpoint configuration and JEA.</span></span>

<span data-ttu-id="340fe-112">`New-PSSession`, `Enter-PSSession`, Ve `Invoke-Command` cmdlet'leri artık bu yeni uzaktan bağlantı desteklemek için yeni bir parametre vardır.</span><span class="sxs-lookup"><span data-stu-id="340fe-112">The `New-PSSession`, `Enter-PSSession`, and `Invoke-Command` cmdlets now have a new parameter set to support this new remoting connection.</span></span>

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

<span data-ttu-id="340fe-113">Uzak oturumu oluşturmak için hedef makine ile belirtin. `HostName` parametresi ve kullanıcı adını sağlayan `UserName`.</span><span class="sxs-lookup"><span data-stu-id="340fe-113">To create a remote session, you specify the target machine with the `HostName` parameter and provide the user name with `UserName`.</span></span> <span data-ttu-id="340fe-114">Cmdlet etkileşimli olarak çalıştırırken için bir parola istenir.</span><span class="sxs-lookup"><span data-stu-id="340fe-114">When running the cmdlets interactively, you're prompted for a password.</span></span> <span data-ttu-id="340fe-115">Ayrıca, bir özel anahtar dosyası ile kullanarak SSH anahtar kimlik doğrulamasını kullanmak `KeyFilePath` parametresi.</span><span class="sxs-lookup"><span data-stu-id="340fe-115">You can also, use SSH key authentication using a private key file with the `KeyFilePath` parameter.</span></span>

## <a name="general-setup-information"></a><span data-ttu-id="340fe-116">Genel Kurulum bilgilerini</span><span class="sxs-lookup"><span data-stu-id="340fe-116">General setup information</span></span>

<span data-ttu-id="340fe-117">SSH tüm makinelerde yüklü olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="340fe-117">SSH must be installed on all machines.</span></span> <span data-ttu-id="340fe-118">SSH istemcisi yükleme (`ssh.exe`) ve sunucu (`sshd.exe`) makinelere gelen ve giden uzak yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="340fe-118">Install both the SSH client (`ssh.exe`) and server (`sshd.exe`) so that you can remote to and from the machines.</span></span> <span data-ttu-id="340fe-119">Windows için yükleme [Win32 OpenSSH github'dan](https://github.com/PowerShell/Win32-OpenSSH/releases).</span><span class="sxs-lookup"><span data-stu-id="340fe-119">For Windows, install [Win32 OpenSSH from GitHub](https://github.com/PowerShell/Win32-OpenSSH/releases).</span></span>
<span data-ttu-id="340fe-120">Linux için SSH (dahil olmak üzere sshd sunucusunu) platformunuz için uygun yükleyin.</span><span class="sxs-lookup"><span data-stu-id="340fe-120">For Linux, install SSH (including sshd server) appropriate to your platform.</span></span> <span data-ttu-id="340fe-121">Ayrıca SSH uzaktan iletişim özelliğini Al Github'dan PowerShell Core yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="340fe-121">You also need to install PowerShell Core from GitHub to get the SSH remoting feature.</span></span> <span data-ttu-id="340fe-122">SSH sunucusu, uzak makinede bir PowerShell işlem barındırmak için bir SSH alt oluşturmak için yapılandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="340fe-122">The SSH server must be configured to create an SSH subsystem to host a PowerShell process on the remote machine.</span></span> <span data-ttu-id="340fe-123">Etkin parola veya anahtar tabanlı kimlik doğrulaması yapılandırmanız da gerekir.</span><span class="sxs-lookup"><span data-stu-id="340fe-123">You also must configure enable password or key-based authentication.</span></span>

## <a name="set-up-on-windows-machine"></a><span data-ttu-id="340fe-124">Windows makinesinde ayarlama</span><span class="sxs-lookup"><span data-stu-id="340fe-124">Set up on Windows Machine</span></span>

1. <span data-ttu-id="340fe-125">En son sürümünü yükleyin [için Windows PowerShell Core](../setup/installing-powershell-core-on-windows.md#msi)</span><span class="sxs-lookup"><span data-stu-id="340fe-125">Install the latest version of [PowerShell Core for Windows](../setup/installing-powershell-core-on-windows.md#msi)</span></span>

   - <span data-ttu-id="340fe-126">SSH remoting desteği bakarak varsa, parametre için ayarlar söyleyebilirsiniz. `New-PSSession`</span><span class="sxs-lookup"><span data-stu-id="340fe-126">You can tell if it has the SSH remoting support by looking at the parameter sets for `New-PSSession`</span></span>

   ```powershell
   Get-Command New-PSSession -syntax
   ```

   ```output
   New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
   ```

2. <span data-ttu-id="340fe-127">Son yükleme [Win32 OpenSSH](https://github.com/PowerShell/Win32-OpenSSH/releases) GitHub kullanarak yapı [yükleme](https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH) yönergeleri</span><span class="sxs-lookup"><span data-stu-id="340fe-127">Install the latest [Win32 OpenSSH](https://github.com/PowerShell/Win32-OpenSSH/releases) build from GitHub using the [installation](https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH) instructions</span></span>
3. <span data-ttu-id="340fe-128">Win32 OpenSSH yüklendiği konumda sshd_config dosyasında Düzenle</span><span class="sxs-lookup"><span data-stu-id="340fe-128">Edit the sshd_config file at the location where you installed Win32 OpenSSH</span></span>

   - <span data-ttu-id="340fe-129">Parola kimlik doğrulamasının etkin olduğundan emin olun</span><span class="sxs-lookup"><span data-stu-id="340fe-129">Make sure password authentication is enabled</span></span>

     ```
     PasswordAuthentication yes
     ```

     ```
     Subsystem    powershell c:/program files/powershell/6.0.4/pwsh.exe -sshs -NoLogo -NoProfile
     ```

     > [!NOTE]
     > <span data-ttu-id="340fe-130">OpenSSH için alanları alt sistemi yürütülebilir yollarında çalışmasını engelleyen Windows hata yoktur.</span><span class="sxs-lookup"><span data-stu-id="340fe-130">There is a bug in OpenSSH for Windows that prevents spaces from working in subsystem executable paths.</span></span> <span data-ttu-id="340fe-131">Daha fazla bilgi için [bu GitHub sorunu](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span><span class="sxs-lookup"><span data-stu-id="340fe-131">For more information, see [this GitHub issue](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span></span>

     <span data-ttu-id="340fe-132">Tek bir çözüm Powershell yükleme dizinine boşluk olmayan bir sembolik bağlantısını oluşturmaktır:</span><span class="sxs-lookup"><span data-stu-id="340fe-132">One solution is to create a symlink to the Powershell installation directory that doesn't have spaces:</span></span>

     ```powershell
     mklink /D c:\pwsh "C:\Program Files\PowerShell\6.0.4"
     ```

     <span data-ttu-id="340fe-133">ve ardından alt girin:</span><span class="sxs-lookup"><span data-stu-id="340fe-133">and then enter it in the subsystem:</span></span>

     ```
     Subsystem    powershell c:\pwsh\pwsh.exe -sshs -NoLogo -NoProfile
     ```

   - <span data-ttu-id="340fe-134">İsteğe bağlı olarak anahtar kimlik doğrulamasını etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="340fe-134">Optionally enable key authentication</span></span>

     ```
     PubkeyAuthentication yes
     ```

4. <span data-ttu-id="340fe-135">Sshd hizmetini yeniden başlatın</span><span class="sxs-lookup"><span data-stu-id="340fe-135">Restart the sshd service</span></span>

   ```powershell
   Restart-Service sshd
   ```

5. <span data-ttu-id="340fe-136">OpenSSH Path ortam değişkeninize yüklendiği yolu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="340fe-136">Add the path where OpenSSH is installed to your Path environment variable.</span></span> <span data-ttu-id="340fe-137">Örneğin, `C:\Program Files\OpenSSH\`.</span><span class="sxs-lookup"><span data-stu-id="340fe-137">For example, `C:\Program Files\OpenSSH\`.</span></span> <span data-ttu-id="340fe-138">Bu giriş ssh.exe bulunmasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="340fe-138">This entry allows for the ssh.exe to be found.</span></span>

## <a name="set-up-on-linux-ubuntu-1404-machine"></a><span data-ttu-id="340fe-139">Linux (Ubuntu 14.04) makinesinde ayarlama</span><span class="sxs-lookup"><span data-stu-id="340fe-139">Set up on Linux (Ubuntu 14.04) Machine</span></span>

1. <span data-ttu-id="340fe-140">Son yükleme [Linux için PowerShell Core](../setup/installing-powershell-core-on-linux.md#ubuntu-1404) Github'dan oluşturun</span><span class="sxs-lookup"><span data-stu-id="340fe-140">Install the latest [PowerShell Core for Linux](../setup/installing-powershell-core-on-linux.md#ubuntu-1404) build from GitHub</span></span>
2. <span data-ttu-id="340fe-141">Yükleme [Ubuntu SSH](https://help.ubuntu.com/lts/serverguide/openssh-server.html) gerektiğinde</span><span class="sxs-lookup"><span data-stu-id="340fe-141">Install [Ubuntu SSH](https://help.ubuntu.com/lts/serverguide/openssh-server.html) as needed</span></span>

   ```bash
   sudo apt install openssh-client
   sudo apt install openssh-server
   ```

3. <span data-ttu-id="340fe-142">Konum /etc/ssh sshd_config dosyasını Düzenle</span><span class="sxs-lookup"><span data-stu-id="340fe-142">Edit the sshd_config file at location /etc/ssh</span></span>

   - <span data-ttu-id="340fe-143">Parola kimlik doğrulamasının etkin olduğundan emin olun</span><span class="sxs-lookup"><span data-stu-id="340fe-143">Make sure password authentication is enabled</span></span>

   ```
   PasswordAuthentication yes
   ```

   - <span data-ttu-id="340fe-144">Bir PowerShell alt sistemi Girişi Ekle</span><span class="sxs-lookup"><span data-stu-id="340fe-144">Add a PowerShell subsystem entry</span></span>

   ```
   Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   - <span data-ttu-id="340fe-145">İsteğe bağlı olarak anahtar kimlik doğrulamasını etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="340fe-145">Optionally enable key authentication</span></span>

   ```
   PubkeyAuthentication yes
   ```

4. <span data-ttu-id="340fe-146">Sshd hizmetini yeniden başlatın</span><span class="sxs-lookup"><span data-stu-id="340fe-146">Restart the sshd service</span></span>

   ```bash
   sudo service sshd restart
   ```

## <a name="set-up-on-macos-machine"></a><span data-ttu-id="340fe-147">Mac OS makinesinde ayarlama</span><span class="sxs-lookup"><span data-stu-id="340fe-147">Set up on MacOS Machine</span></span>

1. <span data-ttu-id="340fe-148">Son yükleme [MacOS için PowerShell Core](../setup/installing-powershell-core-on-macos.md) oluşturun</span><span class="sxs-lookup"><span data-stu-id="340fe-148">Install the latest [PowerShell Core for MacOS](../setup/installing-powershell-core-on-macos.md) build</span></span>

   - <span data-ttu-id="340fe-149">SSH uzaktan iletişim, aşağıdaki adımları izleyerek etkin olduğundan emin olun:</span><span class="sxs-lookup"><span data-stu-id="340fe-149">Make sure SSH Remoting is enabled by following these steps:</span></span>
     - <span data-ttu-id="340fe-150">Açık `System Preferences`</span><span class="sxs-lookup"><span data-stu-id="340fe-150">Open `System Preferences`</span></span>
     - <span data-ttu-id="340fe-151">Tıklayın `Sharing`</span><span class="sxs-lookup"><span data-stu-id="340fe-151">Click on `Sharing`</span></span>
     - <span data-ttu-id="340fe-152">Denetleme `Remote Login` -şeklinde olmalıdır `Remote Login: On`</span><span class="sxs-lookup"><span data-stu-id="340fe-152">Check `Remote Login` - Should say `Remote Login: On`</span></span>
     - <span data-ttu-id="340fe-153">Uygun kullanıcılar erişime izin ver</span><span class="sxs-lookup"><span data-stu-id="340fe-153">Allow access to appropriate users</span></span>

2. <span data-ttu-id="340fe-154">Düzen `sshd_config` dosya konumunda `/private/etc/ssh/sshd_config`</span><span class="sxs-lookup"><span data-stu-id="340fe-154">Edit the `sshd_config` file at location `/private/etc/ssh/sshd_config`</span></span>

   - <span data-ttu-id="340fe-155">Tercih ettiğiniz düzenleyiciyi kullanın veya</span><span class="sxs-lookup"><span data-stu-id="340fe-155">Use your favorite editor or</span></span>

     ```bash
     sudo nano /private/etc/ssh/sshd_config
     ```

   - <span data-ttu-id="340fe-156">Parola kimlik doğrulamasının etkin olduğundan emin olun</span><span class="sxs-lookup"><span data-stu-id="340fe-156">Make sure password authentication is enabled</span></span>

     ```
     PasswordAuthentication yes
     ```

   - <span data-ttu-id="340fe-157">Bir PowerShell alt sistemi Girişi Ekle</span><span class="sxs-lookup"><span data-stu-id="340fe-157">Add a PowerShell subsystem entry</span></span>

     ```
     Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
     ```

   - <span data-ttu-id="340fe-158">İsteğe bağlı olarak anahtar kimlik doğrulamasını etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="340fe-158">Optionally enable key authentication</span></span>

     ```
     PubkeyAuthentication yes
     ```

3. <span data-ttu-id="340fe-159">Sshd hizmetini yeniden başlatın</span><span class="sxs-lookup"><span data-stu-id="340fe-159">Restart the sshd service</span></span>

   ```bash
   sudo launchctl stop com.openssh.sshd
   sudo launchctl start com.openssh.sshd
   ```

## <a name="authentication"></a><span data-ttu-id="340fe-160">Kimlik Doğrulama</span><span class="sxs-lookup"><span data-stu-id="340fe-160">Authentication</span></span>

<span data-ttu-id="340fe-161">SSH üzerinden PowerShell uzaktan iletişimi SSH istemcisi ve SSH hizmeti arasında kimlik doğrulama değişimi kullanır ve tüm kimlik doğrulama düzenleri kendisini uygulamaz.</span><span class="sxs-lookup"><span data-stu-id="340fe-161">PowerShell remoting over SSH relies on the authentication exchange between the SSH client and SSH service and does not implement any authentication schemes itself.</span></span>
<span data-ttu-id="340fe-162">Bu, çok faktörlü kimlik doğrulaması dahil olmak üzere tüm yapılandırılmış kimlik doğrulama düzenleri işlenir, SSH ve PowerShell bağımsız anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="340fe-162">This means that any configured authentication schemes including multi-factor authentication is handled by SSH and independent of PowerShell.</span></span>
<span data-ttu-id="340fe-163">Örneğin, ek güvenlik için ortak anahtar kimlik doğrulaması ve bunun yanı sıra bir kerelik parola istemek için SSH hizmetini yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="340fe-163">For example, you can configure the SSH service to require public key authentication as well as a one-time password for added security.</span></span>
<span data-ttu-id="340fe-164">Multi-Factor Authentication bu belgenin kapsamı dışında bir yapılandırmadır.</span><span class="sxs-lookup"><span data-stu-id="340fe-164">Configuration of multi-factor authentication is outside the scope of this documentation.</span></span>
<span data-ttu-id="340fe-165">Doğru multi-Factor authentication yapılandırmanız ve PowerShell uzaktan iletişimi ile kullanmayı denemeden önce PowerShell dışında çalıştığını doğrulamak nasıl SSH için belgelere bakın.</span><span class="sxs-lookup"><span data-stu-id="340fe-165">Refer to documentation for SSH on how to correctly configure multi-factor authentication and validate it works outside of PowerShell before attempting to use it with PowerShell remoting.</span></span>

## <a name="powershell-remoting-example"></a><span data-ttu-id="340fe-166">PowerShell uzaktan iletişimini örneği</span><span class="sxs-lookup"><span data-stu-id="340fe-166">PowerShell Remoting Example</span></span>

<span data-ttu-id="340fe-167">Uzaktan test etmek için en kolay yolu, tek bir makinede denemektir.</span><span class="sxs-lookup"><span data-stu-id="340fe-167">The easiest way to test remoting is to try it on a single machine.</span></span> <span data-ttu-id="340fe-168">Bu örnekte, bir uzak oturumu yeniden aynı Linux makine oluştururuz.</span><span class="sxs-lookup"><span data-stu-id="340fe-168">In this example, we create a remote session back to the same Linux machine.</span></span> <span data-ttu-id="340fe-169">PowerShell cmdlet etkileşimli olarak görüyoruz için gelen SSH ana bilgisayar doğrulamak isteyen ve için bir parola istemi ister kullanıyoruz.</span><span class="sxs-lookup"><span data-stu-id="340fe-169">We are using PowerShell cmdlets interactively so we see prompts from SSH asking to verify the host computer and prompting for a password.</span></span> <span data-ttu-id="340fe-170">Uzaktan iletişimini çalıştığından emin olmak için bir Windows makinede aynı şey yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="340fe-170">You can do the same thing on a Windows machine to ensure remoting is working.</span></span> <span data-ttu-id="340fe-171">Ardından uzak ana bilgisayar adını değiştirerek makineler arasında.</span><span class="sxs-lookup"><span data-stu-id="340fe-171">Then remote between machines by changing the host name.</span></span>

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
 Id Name   ComputerName    ComputerType    State    ConfigurationName     Availability
 -- ----   ------------    ------------    -----    -----------------     ------------
  1 SSH1   UbuntuVM1       RemoteMachine   Opened   DefaultShell             Available
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

### <a name="known-issues"></a><span data-ttu-id="340fe-172">Bilinen Sorunlar</span><span class="sxs-lookup"><span data-stu-id="340fe-172">Known Issues</span></span>

<span data-ttu-id="340fe-173">Sudo komutu Linux makinesine uzak oturumu işe yaramaz.</span><span class="sxs-lookup"><span data-stu-id="340fe-173">The sudo command doesn't work in remote session to Linux machine.</span></span>

## <a name="see-also"></a><span data-ttu-id="340fe-174">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="340fe-174">See Also</span></span>

[<span data-ttu-id="340fe-175">İçin Windows PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="340fe-175">PowerShell Core for Windows</span></span>](../setup/installing-powershell-core-on-windows.md#msi)

[<span data-ttu-id="340fe-176">Linux için PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="340fe-176">PowerShell Core for Linux</span></span>](../setup/installing-powershell-core-on-linux.md#ubuntu-1404)

[<span data-ttu-id="340fe-177">MacOS için PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="340fe-177">PowerShell Core for MacOS</span></span>](../setup/installing-powershell-core-on-macos.md)

[<span data-ttu-id="340fe-178">Win32 OpenSSH</span><span class="sxs-lookup"><span data-stu-id="340fe-178">Win32 OpenSSH</span></span>](https://github.com/PowerShell/Win32-OpenSSH/releases)

[<span data-ttu-id="340fe-179">Ubuntu SSH</span><span class="sxs-lookup"><span data-stu-id="340fe-179">Ubuntu SSH</span></span>](https://help.ubuntu.com/lts/serverguide/openssh-server.html)