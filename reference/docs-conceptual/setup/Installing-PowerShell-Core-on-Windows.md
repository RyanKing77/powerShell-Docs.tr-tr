# <a name="installing-powershell-core-on-windows"></a>Windows’da PowerShell Core yükleme

## <a name="msi"></a>MSI

Bir Windows İstemcisi veya Windows Server PowerShell yüklemek için (Windows 7 SP1, Server 2008 R2 üzerinde çalışır ve daha sonra), GitHub [sürümleri] [] sayfamızı MSI paketini indirin.

MSI dosyası şuna benzer- `PowerShell-<version>-win-<os-arch>.msi`
<!-- TODO: should be updated to point to the Download Center as well -->

Yüklendikten sonra yükleyici çift tıklayın ve yönergeleri izleyin.

Yükleme sonrasında Başlat menüsü yerleştirilen bir kısayol yoktur.

- Varsayılan olarak, paket için yüklenir `$env:ProgramFiles\PowerShell\<version>`
- Başlat menüsü aracılığıyla PowerShell başlatabilir veya `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`

### <a name="prerequisites"></a>Önkoşullar

WSMan PowerShell uzaktan iletişimi etkinleştirmek için aşağıdaki önkoşulların karşılanması gerekir:

- Yükleme [Evrensel C çalışma zamanı](https://www.microsoft.com/download/details.aspx?id=50410) Windows 10'den önceki Windows sürümleri üzerinde.
  Doğrudan indirme veya Windows Update kullanılabilir.
  Tam (isteğe bağlı paketleri dahil) düzeltme eki, desteklenen sistemleri zaten bu yüklü olacaktır.
- Windows Management Framework (WMF) 4.0 veya daha yeni Windows 7 ve Windows Server 2008 R2 yükleyin.

## <a name="zip"></a>ZIP

PowerShell ikili ZIP arşivini gelişmiş dağıtım senaryoları etkinleştirmek için sağlanır.
ZIP arşivini kullanırken, VM'deki MSI paketini olduğu gibi Önkoşul denetimi vermeyecektir kaydedilmelidir.
Windows 10'den önceki Windows sürümleri üzerinde düzgün çalışması için sırasıyla WSMan üzerinden uzaktan iletişim için emin olmanız gerekir. böylece [Önkoşullar](#prerequisites) karşılanır.

## <a name="deploying-on-windows-iot"></a>Üzerinde Windows IOT dağıtma

Windows IOT zaten PowerShell çekirdek 6'yı dağıtmak için kullanacağız Windows PowerShell ile birlikte gelir.

1. Oluşturma `PSSession` hedef aygıta

   ```powershell
   $s = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. ZIP paketini cihaza kopyalayın

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-6.0.2-win-arm32.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. Cihaza bağlanın ve Arşiv genişletin

   ```powershell
   Enter-PSSession $s
   cd u:\users\administrator\downloads
   Expand-Archive .\PowerShell-6.0.2-win-arm32.zip
   ```

4. Kurulum uzak PowerShell çekirdek 6

   ```powershell
   cd .\PowerShell-6.0.2-win-arm32
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. Cihaz PowerShell çekirdek 6 noktadaki bağlanın

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.6.0.2
   ```

## <a name="deploying-on-nano-server"></a>Nano sunucuda dağıtma

Bu yönergeleri varsayar PowerShell sürümü Nano Server görüntüde zaten çalışıyor ve onu tarafından oluşturuldu [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).
Nano, "gözetimsiz" işletim sistemi sunucusudur. Çekirdek ikili dosyalarını olması dağıtabilir iki farklı yöntemler kullanarak.

1. Çevrimdışı - Nano Server VHD'nin ve seçilen konumunuza bağlı görüntü içinde ZIP dosyasının içeriğini sıkıştırmasını açın.
2. Çevrimiçi - ZIP dosyasının bir PowerShell oturumu üzerinden aktarım ve seçilen konumda sıkıştırmasını açın.

Her iki durumda da, Windows 10 x64 ZIP yayın gerekir paketini ve bir "Yönetici" PowerShell örneği içindeki komutları çalıştırmanız gerekir.

### <a name="offline-deployment-of-powershell-core"></a>PowerShell çekirdek çevrimdışı dağıtımı

1. Takılı Nano Server yansıması içindeki bir dizinin paketin sıkıştırmasını açmak için sık kullanılan sıkıştırma yardımcı programı kullanın.
2. Yansımayı ve onu önyükleme.
3. Windows PowerShell gelen örneğine bağlanın.
4. Kullanarak bir uzak uç noktası oluşturmak için yönergeleri izleyin ["başka bir örneği teknik"](#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).

### <a name="online-deployment-of-powershell-core"></a>PowerShell çekirdek çevrimiçi dağıtımı

Aşağıdaki adımları çalışan örneği Nano Server ve onun uzak uç nokta yapılandırması için PowerShell çekirdek dağıtım kılavuzu.

- Windows PowerShell gelen örneğine bağlanın

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- Dosyayı Nano Server örneğine kopyalayın

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- Oturum girin

  ```powershell
  Enter-PSSession $session
  ```

- ZIP dosyasını ayıklayın

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
  ```

- WSMan tabanlı remoting istiyorsanız kullanarak bir uzak uç noktası oluşturmak için yönergeleri izleyin ["başka bir örneği teknik"](../core-powershell/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).

## <a name="instructions-to-create-a-remoting-endpoint"></a>Bir uzak uç noktası oluşturmak için yönergeler

PowerShell çekirdeği WSMan ve SSH üzerinden PowerShell uzaktan iletişim protokolü (PSRP) destekler.
Daha fazla bilgi için bkz.:

- [SSH PowerShell çekirdek Remoting] [ssh-remoting]
- [WSMan Remoting PowerShell çekirdek.] [wsman-remoting]

## <a name="artifact-installation-instructions"></a>Yapı yükleme yönergeleri

Biz her CI yapı [AppVeyor] [] ile CoreCLR BITS ile ilgili bir arşiv yayımlayın.

PowerShell çekirdek CoreCLR yapıdan yüklemek için:

1. ZIP paketini indirin **yapıları** belirli yapı sekmesinde.
2. Engellemeyi kaldırma ZIP dosyası: dosya Gezgini'nde sağ tıklatın, Özellikler -> 'Engellemeyi Kaldır kutusu ->' uygulamak onay ->
3. Zip dosyasını ayıklayın `bin` dizini
4. `./bin/pwsh.exe`

<!-- [download-center]: TODO --> [serbest]: https://github.com/PowerShell/PowerShell/releases [ssh-remoting]:... /Core-PowerShell/SSH-Remoting-in-PowerShell-Core.MD [wsman-remoting]:... /Core-PowerShell/wsman-Remoting-in-PowerShell-Core.MD [AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell