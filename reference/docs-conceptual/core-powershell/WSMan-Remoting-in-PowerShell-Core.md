# <a name="ws-management-wsman-remoting-in-powershell-core"></a>PowerShell çekirdek WS-Management (WSMan) uzaktan çalışma 

## <a name="instructions-to-create-a-remoting-endpoint"></a>Bir uzak uç noktası oluşturmak için yönergeler

Windows PowerShell çekirdek paket eklenti bir WinRM içeren (`pwrshplugin.dll`) ve bir yükleme komut dosyası (`Install-PowerShellRemoting.ps1`) içinde `$PSHome`.
Bu dosyalar, uç noktasında belirtildiğinde gelen PowerShell uzak bağlantıları kabul etmek PowerShell etkinleştirin.

### <a name="motivation"></a>Motivasyon

PowerShell yüklemesi PowerShell kullanarak uzak bilgisayarlardaki oturumları kurabilen `New-PSSession` ve `Enter-PSSession`.
Gelen PowerShell uzak bağlantıları kabul etmek üzere etkinleştirmek için kullanıcı bir WinRM uzaktan iletişim uç noktası oluşturmanız gerekir.
Bu kullanıcı WinRM uç noktası oluşturmak için Yükle-PowerShellRemoting.ps1 çalıştığı bir açık katılımı senaryodur.
Biz ek işlevsellik için eklenene kadar yükleme komut dosyasını kısa vadeli bir çözümdür `Enable-PSRemoting` aynı eylem gerçekleştirilemiyor.
Daha fazla ayrıntı için lütfen konuya bakın [#1193](https://github.com/PowerShell/PowerShell/issues/1193).

### <a name="script-actions"></a>Betik eylemleri

Komut dosyası

1. Eklentinin %windir%\System32\PowerShell içinde bir dizin oluşturur
1. Pwrshplugin.dll bu konuma kopyalar.
1. Bir yapılandırma dosyası oluşturur
1. WinRM ile bu eklenti kaydeder

### <a name="registration"></a>Kayıt

Komut dosyası, bir yönetici düzeyi PowerShell oturumu ve iki modda çalışır içinde yürütülmelidir.

#### <a name="executed-by-the-instance-of-powershell-that-it-will-register"></a>Kaydeder PowerShell örneği tarafından yürütülebilir.

``` powershell
Install-PowerShellRemoting.ps1
```

#### <a name="executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register"></a>Başka bir PowerShell örneği kaydeder örnek adına tarafından yürütülebilir.

``` powershell
<path to powershell>\Install-PowerShellRemoting.ps1 -PowerShellHome "<absolute path to the instance's $PSHOME>"
```

Örneğin:

``` powershell
Set-Location -Path 'C:\Program Files\PowerShell\6.0.0\'
.\Install-PowerShellRemoting.ps1 -PowerShellHome "C:\Program Files\PowerShell\6.0.0\"
```

**Not:** hemen betiği çalıştırdıktan sonra tüm mevcut PSRP oturumları sonlandırılacak şekilde remoting kayıt betik WinRM, yeniden başlatılır. Uzak oturum sırasında çalıştırırsanız, bu bağlantı sonlandırılacak.

## <a name="how-to-connect-to-the-new-endpoint"></a>Yeni uç noktasına bağlanma

Bir PowerShell oturumuna yeni PowerShell uç noktası belirterek oluşturun `-ConfigurationName "some endpoint name"`. Yukarıdaki örnek PowerShell örneğine bağlanmak için kullanın:

``` powershell
New-PSSession ... -ConfigurationName "powershell.6.0.0"
Enter-PSSession ... -ConfigurationName "powershell.6.0.0"
```

Unutmayın `New-PSSession` ve `Enter-PSSession` belirtmeyin çağrılarını `-ConfigurationName` varsayılan PowerShell uç hedeflediğini `microsoft.powershell`.
