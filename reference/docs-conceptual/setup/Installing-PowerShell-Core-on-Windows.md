# <a name="installing-powershell-core-on-windows"></a>Windows PowerShell çekirdek yükleniyor

## <a name="msi"></a>MSI

Bir Windows İstemcisi veya Windows Server PowerShell yüklemek için (Windows 7 SP1, Server 2008 R2 üzerinde çalışır ve daha sonra), bizim Github'dan MSI paketini indirin [serbest][] sayfası.

MSI dosyası şuna benzer-`PowerShell-6.0.0.<buildversion>.<os-arch>.msi`
<!-- TODO: should be updated to point to the Download Center as well -->

Yüklendikten sonra yükleyici çift tıklayın ve yönergeleri izleyin.

Yükleme sonrasında Başlat menüsü yerleştirilen bir kısayol yoktur.

* Varsayılan olarak, paket için yüklenir`$env:ProgramFiles\PowerShell\`
* Başlat menüsü aracılığıyla PowerShell başlatabilir veya`$env:ProgramFiles\PowerShell\pwsh.exe`

### <a name="prerequisites"></a>Önkoşullar

WSMan PowerShell uzaktan iletişimi etkinleştirmek için aşağıdaki önkoşulların karşılanması gerekir:

* Yükleme [Evrensel C çalışma zamanı](https://www.microsoft.com/download/details.aspx?id=50410) Windows 10'den önceki Windows sürümleri üzerinde.
  Doğrudan indirme veya Windows Update kullanılabilir.
  Tam (isteğe bağlı paketleri dahil) düzeltme eki, desteklenen sistemleri zaten bu yüklü olacaktır.
* Windows Management Framework (WMF) yükleme [4.0](https://www.microsoft.com/download/details.aspx?id=40855) ya da daha yeni ([5.1](https://www.microsoft.com/download/details.aspx?id=54616)) Windows 7 ve Windows Server 2008 R2 üzerinde.

## <a name="zip"></a>ZIP

PowerShell ikili ZIP arşivini gelişmiş dağıtım senaryoları etkinleştirmek için sağlanır.
ZIP arşivini kullanırken, VM'deki MSI paketini olduğu gibi Önkoşul denetimi vermeyecektir kaydedilmelidir.
Windows 10'den önceki Windows sürümleri üzerinde düzgün çalışması için sırasıyla WSMan üzerinden uzaktan iletişim için emin olmanız gerekir. böylece [Önkoşullar](#prerequisites) karşılanır.

## <a name="deploying-on-nano-server"></a>Nano sunucuda dağıtma

Bu yönergeleri varsayar PowerShell sürümü Nano Server görüntüde zaten çalışıyor ve onu tarafından oluşturuldu [Nano Server Image Builder](https://technet.microsoft.com/windows-server-docs/get-started/deploy-nano-server).
Nano Server "gözetimsiz" işletim sistemi ve PowerShell çekirdek ikili dosyalarının dağıtımını iki farklı şekilde oluşabilir:

1. Çevrimdışı - Nano Server VHD'nin ve seçilen konumunuza bağlı görüntü içinde ZIP dosyasının içeriğini sıkıştırmasını açın.
1. Çevrimiçi - ZIP dosyasının bir PowerShell oturumu üzerinden aktarım ve seçilen konumda sıkıştırmasını açın.

Her iki durumda da, Windows 10 x64 Zip yayın gerekir paketini ve bir "Yönetici" PowerShell örneği içindeki komutları çalıştırmanız gerekir.

### <a name="offline-deployment-of-powershell-core"></a>PowerShell çekirdek çevrimdışı dağıtımı

1. Takılı Nano Server yansıması içindeki bir dizinin paketin sıkıştırmasını açmak için sık kullanılan sıkıştırma yardımcı programı kullanın.
1. Yansımayı ve onu önyükleme.
1. Windows PowerShell gelen örneğine bağlanın.
1. Kullanarak bir uzak uç noktası oluşturmak için yönergeleri izleyin [başka bir örneği teknik](#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).

### <a name="online-deployment-of-powershell-core"></a>PowerShell çekirdek çevrimiçi dağıtımı

Aşağıdaki adımları çalışan örneği Nano Server ve onun uzak uç nokta yapılandırması için PowerShell çekirdek dağıtımıyla yol gösterecektir.

* Windows PowerShell gelen örneğine bağlanın

```powershell
$session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
```

* Dosyayı Nano Server örneğine kopyalayın

```powershell
Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
```

* Oturum girin

```powershell
Enter-PSSession $session
```

* Zip dosyasını ayıklayın

```powershell
# Insert the appropriate version.
Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
```

* WSMan tabanlı remoting istiyorsanız kullanarak bir uzak uç noktası oluşturmak için yönergeleri izleyin [başka bir örneği teknik](../core-powershell/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).

## <a name="instructions-to-create-a-remoting-endpoint"></a>Bir uzak uç noktası oluşturmak için yönergeler

PowerShell çekirdeği WSMan ve SSH üzerinden PowerShell uzaktan iletişim protokolü (PSRP) destekler. Daha fazla bilgi için bkz.:

* [SSH PowerShell çekirdek uzaktan çalışma][ssh-remoting]
* [PowerShell çekirdek WSMan uzaktan çalışma][wsman-remoting]

## <a name="artifact-installation-instructions"></a>Yapı yükleme yönergeleri

Biz her CI yapı ile CoreCLR BITS ile ilgili bir arşiv yayımlama [AppVeyor][].

## <a name="coreclr-artifacts"></a>CoreCLR yapıları

* Zip paketini indirin **yapıları** belirli yapı sekmesinde.
* Engellemeyi kaldırma zip dosyası: dosya Gezgini'nde sağ tıklatın, Özellikler -> 'Engellemeyi Kaldır kutusu ->' uygulamak onay ->
* Zip dosyasını ayıklayın `bin` dizini
* `./bin/pwsh.exe`

<!-- [download-center]: TODO -->
[serbest]: https://github.com/PowerShell/PowerShell/releases
[signing]: ../../tools/Sign-Package.ps1
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
