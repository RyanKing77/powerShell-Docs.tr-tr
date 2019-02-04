---
title: SSH üzerinden PowerShell Uzaktan İletişimi
description: SSH kullanarak PowerShell core'da uzaktan iletişim
ms.date: 08/14/2018
ms.openlocfilehash: 87ab967a30782a6ac4d86737cd1702a0ebd6ebc5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687135"
---
# <a name="powershell-remoting-over-ssh"></a>SSH üzerinden PowerShell Uzaktan İletişimi

## <a name="overview"></a>Genel bakış

PowerShell uzaktan iletişimini normalde WinRM bağlantı anlaşması ve veri aktarımı için kullanır. SSH, Linux ve Windows platformları için kullanıma sunulmuştur ve doğru çok platformlu PowerShell uzaktan iletişimini sağlar.

WinRM, uzak PowerShell oturumları için sağlam bir barındırma modeli sağlar. SSH temelli remoting, uzak uç nokta yapılandırması ve JEA (yeterli yönetim) şu anda desteklemiyor.

SSH, uzak Windows ve Linux makinelerini arasındaki temel PowerShell oturumu uzaktan gerçekleştirmenize olanak tanır. SSH uzak PowerShell ana bilgisayar işlemi hedef makinede bir SSH alt oluşturur.
Sonunda size bir genel barındırma modeli, uç nokta yapılandırması ve JEA desteklemek için WinRM ile benzer uygulayacaksınız.

`New-PSSession`, `Enter-PSSession`, Ve `Invoke-Command` cmdlet'leri artık bu yeni uzaktan bağlantı desteklemek için yeni bir parametre vardır.

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

Uzak oturumu oluşturmak için hedef makine ile belirtin. `HostName` parametresi ve kullanıcı adını sağlayan `UserName`. Cmdlet etkileşimli olarak çalıştırırken için bir parola istenir. Ayrıca, bir özel anahtar dosyası ile kullanarak SSH anahtar kimlik doğrulamasını kullanmak `KeyFilePath` parametresi.

## <a name="general-setup-information"></a>Genel Kurulum bilgilerini

SSH tüm makinelerde yüklü olması gerekir. SSH istemcisi yükleme (`ssh.exe`) ve sunucu (`sshd.exe`) makinelere gelen ve giden uzak yapabilirsiniz. OpenSSH için Windows, Windows 10 derleme 1809 ve Windows Server 2019 kullanılabilen sunulmuştur. Daha fazla bilgi için [OpenSSH için Windows](/windows-server/administration/openssh/openssh_overview). Linux için SSH (dahil olmak üzere sshd sunucusunu) platformunuz için uygun yükleyin. Ayrıca SSH uzaktan iletişim özelliğini Al Github'dan PowerShell Core yüklemeniz gerekir. SSH sunucusu, uzak makinede bir PowerShell işlem barındırmak için bir SSH alt oluşturmak için yapılandırılmalıdır. Etkin parola veya anahtar tabanlı kimlik doğrulaması yapılandırmanız da gerekir.

## <a name="set-up-on-windows-machine"></a>Windows makinesinde ayarlama

1. En son sürümünü yükleyin [için Windows PowerShell Core](../../install/installing-powershell-core-on-windows.md#msi)

   - SSH remoting desteği bakarak varsa, parametre için ayarlar söyleyebilirsiniz. `New-PSSession`

   ```powershell
   Get-Command New-PSSession -syntax
   ```

   ```output
   New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
   ```

2. En son Win32 OpenSSH yükleyin. Yükleme yönergeleri için bkz. [yükleme, OpenSSH](/windows-server/administration/openssh/openssh_install_firstuse).
3. Düzen `sshd_config` konumundaki dosya `$env:ProgramData\ssh`.

   - Parola kimlik doğrulamasının etkin olduğundan emin olun

     ```
     PasswordAuthentication yes
     ```

     ```
     Subsystem    powershell c:/program files/powershell/6/pwsh.exe -sshs -NoLogo -NoProfile
     ```

     > [!NOTE]
     > OpenSSH için alanları alt sistemi yürütülebilir yollarında çalışmasını engelleyen Windows hata yoktur. Daha fazla bilgi için [bu GitHub sorunu](https://github.com/PowerShell/Win32-OpenSSH/issues/784).

     Tek bir çözüm Powershell yükleme dizinine boşluk olmayan bir sembolik bağlantısını oluşturmaktır:

     ```powershell
     mklink /D c:\pwsh "C:\Program Files\PowerShell\6"
     ```

     ve ardından alt girin:

     ```
     Subsystem    powershell c:\pwsh\pwsh.exe -sshs -NoLogo -NoProfile
     ```

   - İsteğe bağlı olarak anahtar kimlik doğrulamasını etkinleştirme

     ```
     PubkeyAuthentication yes
     ```

4. Sshd hizmetini yeniden başlatın

   ```powershell
   Restart-Service sshd
   ```

5. OpenSSH Path ortam değişkeninize yüklendiği yolu ekleyin. Örneğin, `C:\Program Files\OpenSSH\`. Bu giriş ssh.exe bulunmasına olanak sağlar.

## <a name="set-up-on-linux-ubuntu-1404-machine"></a>Linux (Ubuntu 14.04) makinesinde ayarlama

1. Son yükleme [Linux için PowerShell Core](../../install/installing-powershell-core-on-linux.md#ubuntu-1404) Github'dan oluşturun
2. Yükleme [Ubuntu SSH](https://help.ubuntu.com/lts/serverguide/openssh-server.html) gerektiğinde

   ```bash
   sudo apt install openssh-client
   sudo apt install openssh-server
   ```

3. Konum /etc/ssh sshd_config dosyasını Düzenle

   - Parola kimlik doğrulamasının etkin olduğundan emin olun

   ```
   PasswordAuthentication yes
   ```

   - Bir PowerShell alt sistemi Girişi Ekle

   ```
   Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   - İsteğe bağlı olarak anahtar kimlik doğrulamasını etkinleştirme

   ```
   PubkeyAuthentication yes
   ```

4. Sshd hizmetini yeniden başlatın

   ```bash
   sudo service sshd restart
   ```

## <a name="set-up-on-macos-machine"></a>Mac OS makinesinde ayarlama

1. Son yükleme [MacOS için PowerShell Core](../../install/installing-powershell-core-on-macos.md) oluşturun

   - SSH uzaktan iletişim, aşağıdaki adımları izleyerek etkin olduğundan emin olun:
     - Açık `System Preferences`
     - Tıklayın `Sharing`
     - Denetleme `Remote Login` -şeklinde olmalıdır `Remote Login: On`
     - Uygun kullanıcılar erişime izin ver

2. Düzen `sshd_config` dosya konumunda `/private/etc/ssh/sshd_config`

   - Tercih ettiğiniz düzenleyiciyi kullanın veya

     ```bash
     sudo nano /private/etc/ssh/sshd_config
     ```

   - Parola kimlik doğrulamasının etkin olduğundan emin olun

     ```
     PasswordAuthentication yes
     ```

   - Bir PowerShell alt sistemi Girişi Ekle

     ```
     Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
     ```

   - İsteğe bağlı olarak anahtar kimlik doğrulamasını etkinleştirme

     ```
     PubkeyAuthentication yes
     ```

3. Sshd hizmetini yeniden başlatın

   ```bash
   sudo launchctl stop com.openssh.sshd
   sudo launchctl start com.openssh.sshd
   ```

## <a name="authentication"></a>Kimlik Doğrulama

SSH üzerinden PowerShell uzaktan iletişimi SSH istemcisi ve SSH hizmeti arasında kimlik doğrulama değişimi kullanır ve tüm kimlik doğrulama düzenleri kendisini uygulamaz.
Bu, çok faktörlü kimlik doğrulaması dahil olmak üzere tüm yapılandırılmış kimlik doğrulama düzenleri işlenir, SSH ve PowerShell bağımsız anlamına gelir.
Örneğin, ek güvenlik için ortak anahtar kimlik doğrulaması ve bunun yanı sıra bir kerelik parola istemek için SSH hizmetini yapılandırabilirsiniz.
Multi-Factor Authentication bu belgenin kapsamı dışında bir yapılandırmadır.
Doğru multi-Factor authentication yapılandırmanız ve PowerShell uzaktan iletişimi ile kullanmayı denemeden önce PowerShell dışında çalıştığını doğrulamak nasıl SSH için belgelere bakın.

## <a name="powershell-remoting-example"></a>PowerShell uzaktan iletişimini örneği

Uzaktan test etmek için en kolay yolu, tek bir makinede denemektir. Bu örnekte, bir uzak oturumu yeniden aynı Linux makine oluştururuz. PowerShell cmdlet etkileşimli olarak görüyoruz için gelen SSH ana bilgisayar doğrulamak isteyen ve için bir parola istemi ister kullanıyoruz. Uzaktan iletişimini çalıştığından emin olmak için bir Windows makinede aynı şey yapabilirsiniz. Ardından uzak ana bilgisayar adını değiştirerek makineler arasında.

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

### <a name="known-issues"></a>Bilinen Sorunlar

Sudo komutu Linux makinesine uzak oturumu işe yaramaz.

## <a name="see-also"></a>Ayrıca bkz:

[İçin Windows PowerShell Core](../../install/installing-powershell-core-on-windows.md#msi)

[Linux için PowerShell Core](../../install/installing-powershell-core-on-linux.md#ubuntu-1404)

[MacOS için PowerShell Core](../../install/installing-powershell-core-on-macos.md)

[Windows için OpenSSH](/windows-server/administration/openssh/openssh_overview)

[Ubuntu SSH](https://help.ubuntu.com/lts/serverguide/openssh-server.html)
