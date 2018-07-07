
# <a name="powershell-remoting-over-ssh"></a>SSH üzerinden PowerShell Uzaktan İletişimi

## <a name="overview"></a>Genel bakış

PowerShell uzaktan iletişimini normalde WinRM bağlantı anlaşması ve veri aktarımı için kullanır.
Hem Linux hem de Windows platformları için kullanıma sunulmuştur ve doğru çok platformlu PowerShell uzaktan iletişimini sağlar, SSH Bu uzaktan iletişim uygulama için seçildi.
Ancak, WinRM bu uygulama henüz bunu PowerShell uzak oturumlar için sağlam bir barındırma modeli de sağlar.
Ve bu PowerShell uzak uç nokta yapılandırması ve JEA (yeterli yönetim) henüz desteklenmiyor, bu uygulamada anlamına gelir.

PowerShell SSH uzak Windows ve Linux makinelerini arasındaki temel PowerShell oturumu uzaktan gerçekleştirmenize olanak tanır.
Bu, barındırma işlemi bir SSH alt olarak hedef makinede bir PowerShell oluşturarak yapılır.
Sonuçta bu WinRM uç nokta yapılandırması ve JEA desteklemek için işleyişi benzer daha genel barındırma modeliyle değiştirilecek.

`New-PSSession`, `Enter-PSSession` Ve `Invoke-Command` cmdlet'leri artık bu yeni uzaktan bağlantı sağlamak için yeni bir parametre vardır

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

Bu yeni parametre kümesi, büyük olasılıkla değiştirir ancak şimdilik SSH komut satırından etkileşim veya komutları ve komut dosyaları, üzerinde çağırmak Pssessions'dan oluşturmanıza olanak sağlar.
Hedef makine ana bilgisayar adı parametresi belirtin ve kullanıcı adı ile kullanıcı adını belirtin.
Cmdlet'ler PowerShell komut satırından etkileşimli olarak çalıştırırken için bir parola istenir.
Ancak, SSH anahtar kimlik doğrulamasını kullanmak ve bir özel anahtar dosyası yolu KeyFilePath parametresiyle sağlamak için seçeneğiniz de vardır.

## <a name="general-setup-information"></a>Genel Kurulum bilgilerini

SSH tüm makinelerde yüklü olması gerekiyor.
Hem de istemci yüklemeniz gerekir (`ssh.exe`) ve sunucu (`sshd.exe`) ve böylece uzak makinelere gelen ve giden deneyimleyebilirsiniz.
Windows için yüklemeniz gerekecek [Win32 OpenSSH github'dan](https://github.com/PowerShell/Win32-OpenSSH/releases).
Linux için SSH (dahil olmak üzere sshd sunucusunu) platformunuz için uygun yüklemeniz gerekir.
En son PowerShell derleme veya GitHub SSH uzaktan erişim özelliği olan bir paketten de gerekir.
SSH alt sistemler, uzak makinede bir PowerShell işlem oluşturmak için kullanılır ve SSH sunucusu için yapılandırılmış olması gerekir.
Ayrıca parola kimlik doğrulaması ve isteğe bağlı olarak anahtar tabanlı kimlik doğrulamasını etkinleştirmeniz gerekir.

## <a name="setup-on-windows-machine"></a>Windows makinesinde Kurulumu

1. [İçin Windows PowerShell Core] en son sürümünü yükleyin
   - SSH remoting desteği bakarak varsa, parametre için ayarlar söyleyebilirsiniz. `New-PSSession`

   ```powershell
   Get-Command New-PSSession -syntax
   ```

   ```output
   New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
   ```

2. Son [Win32 OpenSSH] derleme [Kurulum] yönergeleri kullanarak Github'dan yükleyin
3. Win32 OpenSSH yüklendiği konumda sshd_config dosyasında Düzenle
   - Parola kimlik doğrulamasının etkin olduğundan emin olun

   ```
   PasswordAuthentication yes
   ```

    ```
    Subsystem    powershell c:/program files/powershell/6.0.0/pwsh.exe -sshs -NoLogo -NoProfile
    ```

    > [!NOTE]
    OpenSSH için alanları alt sistemi yürütülebilir yollarında çalışmasını engelleyen Windows hata yoktur.
    Bkz: [daha fazla bilgi için github'daki bu sorunu](https://github.com/PowerShell/Win32-OpenSSH/issues/784).

    Tek bir çözüm, boşluk içermeyen Powershell yükleme dizinine hedefine sembolik bağlantı oluşturmaktır:

    ```powershell
    mklink /D c:\pwsh "C:\Program Files\PowerShell\6.0.0"
    ```

    ve ardından alt girin:

    ```
    Subsystem    powershell c:\pwsh\pwsh.exe -sshs -NoLogo -NoProfile
    ```

   ```
   Subsystem    powershell c:/program files/powershell/6.0.0/pwsh.exe -sshs -NoLogo -NoProfile
   ```

   - İsteğe bağlı olarak anahtar kimlik doğrulamasını etkinleştirme

   ```
   PubkeyAuthentication yes
   ```

4. Sshd hizmetini yeniden başlatın

   ```powershell
   Restart-Service sshd
   ```

5. OpenSSH, yol Env değişkenini yüklendiği yolu Ekle
   - Bu satırlar olmalıdır `C:\Program Files\OpenSSH\`
   - Bu ssh.exe bulunmasına olanak sağlar

## <a name="setup-on-linux-ubuntu-1404-machine"></a>Linux (Ubuntu 14.04) makinede Kur

1. Son [Linux için PowerShell Core] derleme Github'dan yükleyin
2. [Ubuntu SSH] gerektiği şekilde yükle

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

## <a name="setup-on-macos-machine"></a>Mac OS makinesinde Kurulumu

1. Son [MacOS için PowerShell Core] derleme yükleme
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

## <a name="powershell-remoting-example"></a>PowerShell uzaktan iletişimini örneği

Uzaktan test etmek için en kolay yolu, tek bir makinede denemektir olmaktır.
Burada miyim Linux kutusundaki aynı makineye bir uzak oturumu oluşturur.
SSH ana bilgisayar yanı sıra parola istemlerinin doğrulamak isteyen istemleri görüyoruz için PowerShell cmdlet'leri bir komut isteminden kullanıyorum, dikkat edin.
Uzaktan iletişim var. çalıştığından emin olmak için Windows makine ve ardından uzak ana bilgisayar adı yalnızca değiştirerek makine arasında aynı şeyi yapabilirsiniz.

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

### <a name="known-issues"></a>Bilinen Sorunlar

- Linux makinesi uzak oturumu sudo komutu çalışmaz.

## <a name="see-also"></a>Ayrıca bkz:

[İçin Windows PowerShell Core](../setup/installing-powershell-core-on-windows.md#msi)

[Linux için PowerShell Core](../setup/installing-powershell-core-on-linux.md#ubuntu-1404)

[MacOS için PowerShell Core](../setup/installing-powershell-core-on-macos.md)

[Win32 OpenSSH](https://github.com/PowerShell/Win32-OpenSSH/releases)

[Yükleme](https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH)

[Ubuntu SSH](https://help.ubuntu.com/lts/serverguide/openssh-server.html)