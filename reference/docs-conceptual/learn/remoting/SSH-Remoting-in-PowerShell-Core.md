---
title: SSH üzerinden PowerShell Uzaktan İletişimi
description: SSH kullanarak PowerShell Core 'da uzaktan iletişim
ms.date: 08/14/2018
ms.openlocfilehash: d994a3888b9a372b803a65666634775a8905d63a
ms.sourcegitcommit: 118eb294d5a84a772e6449d42a9d9324e18ef6b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/22/2019
ms.locfileid: "68372143"
---
# <a name="powershell-remoting-over-ssh"></a>SSH üzerinden PowerShell Uzaktan İletişimi

## <a name="overview"></a>Genel bakış

PowerShell uzaktan iletişimi, bağlantı anlaşması ve veri aktarımı için normalde WinRM kullanır. SSH artık Linux ve Windows platformları için kullanılabilir ve gerçek çok platformlu PowerShell uzaktan iletişimini sağlar.

WinRM, PowerShell uzak oturumları için güçlü bir barındırma modeli sağlar. SSH tabanlı uzaktan iletişim şu anda uzak uç nokta yapılandırmasını ve JEA 'yı (yalnızca yeterli yönetim) desteklememektedir.

SSH Remoting, Windows ve Linux makineler arasında temel PowerShell oturumu uzaktan iletişimini yapmanızı sağlar. SSH Remoting, hedef makinede bir SSH alt sistemi olarak bir PowerShell ana bilgisayar işlemi oluşturur. Son olarak, uç nokta yapılandırmasını ve JEA 'yı desteklemek için WinRM 'ye benzer bir genel barındırma modeli uygulayacağız.

`New-PSSession`, Vecmdlet`Invoke-Command` 'leri artık bu yeni uzaktan iletişim bağlantısını destekleyecek yeni bir parametre kümesine sahip. `Enter-PSSession`

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

Uzak bir oturum oluşturmak için, hedef makineyi `HostName` parametresiyle belirtirsiniz ve Kullanıcı adını ile `UserName`sağlarsınız. Cmdlet 'leri etkileşimli olarak çalıştırırken parola girmeniz istenir. Ayrıca, `KeyFilePath` parametresi ile bir özel anahtar dosyası kullanarak SSH anahtar kimlik doğrulamasını kullanabilirsiniz.

## <a name="general-setup-information"></a>Genel Kurulum bilgileri

SSH 'nin tüm makinelere yüklenmesi gerekir. Makinelere ve makinelerinize uzak`ssh.exe`bir şekilde bağlanmak için`sshd.exe`hem SSH istemcisini () hem de sunucusunu () yükleyebilirsiniz. Windows için OpenSSH artık Windows 10 Build 1809 ve Windows Server 2019 ' de kullanılabilir. Daha fazla bilgi için bkz. [Windows Için OpenSSH](/windows-server/administration/openssh/openssh_overview). Linux için, platformunuza uygun SSH 'yi (SSHD sunucusu dahil) yüklemelisiniz. SSH uzaktan iletişim özelliğini almak için GitHub 'dan PowerShell Core ' u de yüklemeniz gerekir. SSH sunucusu, uzak makinede bir PowerShell işlemini barındırmak için bir SSH alt sistemi oluşturacak şekilde yapılandırılmalıdır. Parolayı veya anahtar tabanlı kimlik doğrulamasını etkinleştir ' i de yapılandırmanız gerekir.

## <a name="set-up-on-windows-machine"></a>Windows makinesinde ayarlama

1. [Windows Için PowerShell Core](../../install/installing-powershell-core-on-windows.md#msi) 'un en son sürümünü yükler

   - İçin parametre kümelerine bakarak SSH uzaktan iletişim desteğinin olup olmadığını söyleyebilirsiniz`New-PSSession`

   ```powershell
   Get-Command New-PSSession -syntax
   ```

   ```output
   New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
   ```

2. En son Win32 OpenSSH 'yi yükler. Yükleme yönergeleri için bkz. [OpenSSH yüklemesi](/windows-server/administration/openssh/openssh_install_firstuse).
3. `sshd_config` Konumunda`$env:ProgramData\ssh`bulunan dosyayı düzenleyin.

   - Parola kimlik doğrulamasının etkinleştirildiğinden emin olun

     ```
     PasswordAuthentication yes
     ```

     ```
     Subsystem    powershell c:/program files/powershell/6/pwsh.exe -sshs -NoLogo -NoProfile
     ```

     > [!NOTE]
     > Windows için OpenSSH içinde boşlukların alt sistem yürütülebilir yollarında çalışmasını engelleyen bir hata var. Daha fazla bilgi için [bu GitHub sorunu](https://github.com/PowerShell/Win32-OpenSSH/issues/784).

     Bir çözüm, bir PowerShell yükleme dizinine boşluk içermeyen bir oluşturmaksızın oluşturmaktır:

     ```powershell
     mklink /D c:\pwsh "C:\Program Files\PowerShell\6"
     ```

     ve ardından alt sisteme girin:

     ```
     Subsystem    powershell c:\pwsh\pwsh.exe -sshs -NoLogo -NoProfile
     ```

   - İsteğe bağlı olarak anahtar kimlik doğrulamasını etkinleştir

     ```
     PubkeyAuthentication yes
     ```

4. SSHD hizmetini yeniden başlatın

   ```powershell
   Restart-Service sshd
   ```

5. PATH ortam değişkeninizdeki OpenSSH 'nin yüklendiği yolu ekleyin. Örneğin: `C:\Program Files\OpenSSH\`. Bu giriş SSH. exe ' nin bulunabilir olmasını sağlar.

## <a name="set-up-on-linux-ubuntu-1604-machine"></a>Linux (Ubuntu 16,04) makinesinde ayarlama

1. GitHub 'dan Linux derlemesi için en son [PowerShell çekirdeğini](../../install/installing-powershell-core-on-linux.md#ubuntu-1604) yükler
2. Gereken şekilde [Ubuntu SSH](https://help.ubuntu.com/lts/serverguide/openssh-server.html) 'i yükler

   ```bash
   sudo apt install openssh-client
   sudo apt install openssh-server
   ```

3. Sshd_config dosyasını/etc/ssh konumunda düzenleme

   - Parola kimlik doğrulamasının etkinleştirildiğinden emin olun

   ```
   PasswordAuthentication yes
   ```

   - PowerShell alt sistemi girişi ekleme

   ```
   Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   - İsteğe bağlı olarak anahtar kimlik doğrulamasını etkinleştir

   ```
   PubkeyAuthentication yes
   ```

4. SSHD hizmetini yeniden başlatın

   ```bash
   sudo service sshd restart
   ```

## <a name="set-up-on-macos-machine"></a>MacOS makinesinde ayarlama

1. [MacOS derlemesi için en son PowerShell çekirdeğini](../../install/installing-powershell-core-on-macos.md) yükler

   - Aşağıdaki adımları izleyerek SSH uzaktan Iletişim özelliğinin etkinleştirildiğinden emin olun:
     - Açın`System Preferences`
     - Öğesine tıklayın`Sharing`
     - Check `Remote Login` -deyin`Remote Login: On`
     - Uygun kullanıcılara erişime izin ver

2. `sshd_config` Dosyayı konumdaki Düzenle`/private/etc/ssh/sshd_config`

   - En sevdiğiniz düzenleyiciyi kullanın veya

     ```bash
     sudo nano /private/etc/ssh/sshd_config
     ```

   - Parola kimlik doğrulamasının etkinleştirildiğinden emin olun

     ```
     PasswordAuthentication yes
     ```

   - PowerShell alt sistemi girişi ekleme

     ```
     Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
     ```

   - İsteğe bağlı olarak anahtar kimlik doğrulamasını etkinleştir

     ```
     PubkeyAuthentication yes
     ```

3. SSHD hizmetini yeniden başlatın

   ```bash
   sudo launchctl stop com.openssh.sshd
   sudo launchctl start com.openssh.sshd
   ```

## <a name="authentication"></a>Kimlik Doğrulama

SSH üzerinden PowerShell uzaktan iletişimi SSH istemcisi ile SSH hizmeti arasındaki kimlik doğrulama değişimine dayanır ve herhangi bir kimlik doğrulama düzeni uygulamaz. Bu, Multi-Factor Authentication dahil olmak üzere yapılandırılmış tüm kimlik doğrulama düzenlerinin SSH ve PowerShell 'den bağımsız olarak işlendiği anlamına gelir. Örneğin, SSH hizmetini, ek güvenlik için bir kerelik parola ve ortak anahtar kimlik doğrulaması gerektirecek şekilde yapılandırabilirsiniz. Multi-Factor Authentication yapılandırması, bu belgenin kapsamı dışındadır. Multi-Factor Authentication 'ı doğru şekilde yapılandırma hakkında SSH belgelerini inceleyin ve PowerShell Remoting ile kullanmayı denemeden önce PowerShell dışında çalıştığını doğrulayın.

## <a name="powershell-remoting-example"></a>PowerShell uzaktan Iletişim örneği

Uzaktan iletişimi test etmenin en kolay yolu bunu tek bir makinede denemenize olanak sağlar. Bu örnekte, aynı Linux makinesine bir uzak oturum oluşturacağız. PowerShell cmdlet 'lerini etkileşimli olarak kullandığımızda, SSH 'den ana bilgisayarı doğrulamak ve bir parola istemek isteyip istemediğinizi görmeniz istenir. Uzak hizmetin çalıştığından emin olmak için bir Windows makinesinde aynı şeyi yapabilirsiniz. Sonra konak adını değiştirerek makineler arasında uzaktan.

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
Linux TestUser-UbuntuVM1 4.2.0-42-generic 49~16.04.1-Ubuntu SMP Wed Jun 29 20:22:11 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

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

Sudo komutu, Linux makinesine uzak oturumda çalışmaz.

## <a name="see-also"></a>Ayrıca bkz:

[Windows için PowerShell Core](../../install/installing-powershell-core-on-windows.md#msi)

[Linux için PowerShell Core](../../install/installing-powershell-core-on-linux.md#ubuntu-1604)

[MacOS için PowerShell Core](../../install/installing-powershell-core-on-macos.md)

[Windows için OpenSSH](/windows-server/administration/openssh/openssh_overview)

[Ubuntu SSH](https://help.ubuntu.com/lts/serverguide/openssh-server.html)
