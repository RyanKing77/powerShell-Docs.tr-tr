# <a name="powershell-remoting-over-ssh"></a>SSH üzerinden PowerShell Uzaktan İletişimi

## <a name="overview"></a>Genel bakış

PowerShell uzaktan iletişim bağlantı anlaşması ve veri aktarımı için normalde WinRM kullanır.
Linux ve Windows platformları için kullanıma sunulmuştur ve doğru çok platformlu PowerShell uzaktan iletişimi sağlayan SSH bu remoting uygulama için seçildi.
Ancak, WinRM Ayrıca, bu uygulama henüz yapmak PowerShell uzak oturumlar için sağlam bir barındırma modeli sağlar.
Ve bu PowerShell uzak uç nokta yapılandırması ve JEA (yalnızca yeterince yönetim) henüz desteklenmiyor, bu uygulama anlamına gelir.

PowerShell SSH remoting Windows ve Linux makineler arasındaki temel PowerShell oturumu remoting yapmanıza olanak tanır.
Bu, barındırma işlemi SSH alt sistemi olarak hedef makinede bir PowerShell oluşturarak yapılır.
Sonuç olarak bu WinRM uç nokta yapılandırması ve JEA desteklemek için işleyişi benzer bir daha genel barındırma modeli için değiştirilir.

New-PSSession, Enter-PSSession ve Invoke-Command cmdlet'leri artık bu yeni uzaktan iletişim bağlantı kolaylaştırmak için yeni bir parametre vardır

```powershell
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

Bu yeni parametre kümesi olasılıkla değişir ancak şu an için SSH komut satırından etkileşimde veya üzerinde komutları ve komut dosyaları çağırma Pssessions'dan oluşturmanıza olanak sağlar.
Ana bilgisayar adı parametresiyle hedef makine belirtin ve kullanıcı adı ile kullanıcı adını belirtin.
Cmdlet'ler PowerShell komut satırında etkileşimli olarak çalıştırırken için bir parola istenir.
Ancak, aynı zamanda SSH anahtar kimlik doğrulaması kullanmak ve bir özel anahtar dosyası yolu KeyFilePath parametresiyle sağlamak için seçeneğiniz vardır.

## <a name="general-setup-information"></a>Genel Kurulum bilgileri

SSH tüm makinelerde yüklü olması gereklidir.
Böylece remoting makinelere gelen ve giden deneyimleyebilirsiniz (ssh.exe) istemci ve sunucunun (sshd.exe) yüklemeniz gerekir.
Windows için yüklemeniz gerekecek [Win32 OpenSSH github'dan](https://github.com/PowerShell/Win32-OpenSSH/releases).
Linux için SSH (dahil olmak üzere sshd sunucu) platformunuz için uygun yüklemeniz gerekir.
Son PowerShell derleme veya SSH uzaktan erişim özelliği olan github'dan paketi de gerekir.
SSH alt sistemleri uzak makinede PowerShell işlem kurmak için kullanılır ve SSH sunucusu için yapılandırılmış olması gerekir.
Ayrıca parola kimlik doğrulaması ve isteğe bağlı olarak anahtar tabanlı kimlik doğrulamasını etkinleştirmeniz gerekir.

## <a name="setup-on-windows-machine"></a>Kurulum Windows makinesinde

1. [Windows PowerShell çekirdek en son sürümünü yükleme] []
    - Bakarak SSH remoting desteği varsa, New-PSSession için parametre kümeleri söyleyin
    ```powershell
    PS> Get-Command New-PSSession -syntax
    New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
    ```
1. En son yükleme [Win32 OpenSSH] GitHub kullanarak yapı [yükleme] yönergeleri
1. Win32 OpenSSH yüklendiği konumda sshd_config dosyayı düzenleyin.
    - Parola kimlik doğrulaması etkin olduğundan emin olun
    ```none
    PasswordAuthentication yes
    ```
    - Bir PowerShell alt sistemi girişi ekleme, değiştirme `c:/program files/powershell/6.0.0/pwsh.exe` kullanmak istediğiniz sürüm için doğru yolu ile
    ```none
    Subsystem    powershell c:/program files/powershell/6.0.0/pwsh.exe -sshs -NoLogo -NoProfile
    ```
    - İsteğe bağlı olarak anahtar kimlik doğrulamasını etkinleştir
    ```none
    PubkeyAuthentication yes
    ```
1. Sshd hizmetini yeniden başlatın
    ```powershell
    Restart-Service sshd
    ```
1. OpenSSH, yol Env değişkenini yüklendiği yolu Ekle
    - Bu satırları olmalıdır `C:\Program Files\OpenSSH\`
    - Bu ssh.exe bulunacak sağlar

## <a name="setup-on-linux-ubuntu-1404-machine"></a>Linux (Ubuntu 14.04) makinede Kurulumu

1. En son yükleme [Linux için PowerShell] Github'dan derleme
1. Yükleme [Ubuntu SSH] gerektiğinde
    ```bash
    sudo apt install openssh-client
    sudo apt install openssh-server
    ```
1. Konum /etc/ssh sshd_config dosyasını düzenleyin
    - Parola kimlik doğrulaması etkin olduğundan emin olun
    ```none
    PasswordAuthentication yes
    ```
    - Bir PowerShell alt sistemi Girişi Ekle
    ```none
    Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
    ```
    - İsteğe bağlı olarak anahtar kimlik doğrulamasını etkinleştir
    ```none
    PubkeyAuthentication yes
    ```
1. Sshd hizmetini yeniden başlatın
    ```bash
    sudo service sshd restart
    ```

## <a name="setup-on-macos-machine"></a>Kurulum MacOS makinede

1. En son yükleme [MacOS için PowerShell] derleme
    - Aşağıdaki adımları izleyerek SSH uzatan iletişimin etkinleştirildiğinden emin olun:
      - Açık `System Preferences`
      - ' Yi tıklatın `Sharing`
      - Denetleme `Remote Login` -yazması gerekir `Remote Login: On`
      - Uygun kullanıcıların erişmesine izin vermek
1. Düzen `sshd_config` konumda dosya `/private/etc/ssh/sshd_config`
    - Tercih ettiğiniz düzenleyicisi kullanın veya
    ```bash
    sudo nano /private/etc/ssh/sshd_config
    ```
    - Parola kimlik doğrulaması etkin olduğundan emin olun
    ```none
    PasswordAuthentication yes
    ```
    - Bir PowerShell alt sistemi Girişi Ekle
    ```none
    Subsystem powershell /usr/local/bin/powershell -sshs -NoLogo -NoProfile
    ```
    - İsteğe bağlı olarak anahtar kimlik doğrulamasını etkinleştir
    ```none
    PubkeyAuthentication yes
    ```
1. Sshd hizmetini yeniden başlatın
    ```bash
    sudo launchctl stop com.openssh.sshd
    sudo launchctl start com.openssh.sshd
    ```

## <a name="powershell-remoting-example"></a>PowerShell uzaktan iletişim örneği

Yalnızca tek bir makinede denemek için Remoting test etmek için en kolay yolu değil.
Burada ı Linux kutusundaki aynı makineye uzak bir oturum oluşturur.
Biz ana bilgisayarın yanı sıra parola istemi doğrulamak isteyen SSH istemleri görmek için PowerShell cmdlet'leri bir komut isteminden kullanıyorum, dikkat edin.
Remoting var. çalıştığından emin olmak için Windows makinesine ve ardından uzak ana bilgisayar adı yalnızca değiştirerek makineler arasında aynı şey yapabilirsiniz.

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

### <a name="known-issues"></a>Bilinen Sorunlar

1. sudo komutu Linux makinesinde uzaktan oturumunda çalışmaz.

[PowerShell for Windows]: https://github.com/PowerShell/PowerShell/blob/master/docs/installation/windows.md#msi
[Win32 OpenSSH]: https://github.com/PowerShell/Win32-OpenSSH
[yükleme]: https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH
[Linux için PowerShell]: https://github.com/PowerShell/PowerShell/blob/master/docs/installation/linux.md#ubuntu-1404
[Ubuntu SSH]: https://help.ubuntu.com/lts/serverguide/openssh-server.html
[MacOS için PowerShell]: https://github.com/PowerShell/PowerShell/blob/master/docs/installation/linux.md#macos-1012