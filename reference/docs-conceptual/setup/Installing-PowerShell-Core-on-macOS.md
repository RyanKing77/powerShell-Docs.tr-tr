# <a name="installing-powershell-core-on-macos"></a>MacOS’ta PowerShell Core yükleme

PowerShell çekirdeği macOS 10.12 ve üstünü destekler.
Tüm paketler bizim Github'da bulunan [Sürümleri][] sayfası.
Paket yüklendikten sonra çalıştırmak `pwsh` bir terminal gelen.

### <a name="installation-via-homebrew-on-macos-1012"></a>MacOS 10,12 Homebrew aracılığıyla yükleme

[Homebrew] [ brew] macOS için tercih edilen paket yöneticisidir.
Varsa `brew` komutu bulunamadı, Homebrew aşağıdaki yüklemenize gerek [kendi yönergeleri][brew].

Homebrew yükledikten sonra PowerShell yükleme kolaydır.
İlk olarak, yükleme [Homebrew Cask][cask], daha fazla paket yükleyebilirsiniz:

```sh
brew tap caskroom/cask
```

Şimdi, PowerShell yükleyebilirsiniz:

```sh
brew cask install powershell
```

Son olarak, yükleme işleminiz düzgün şekilde çalıştığını doğrulayın:

```sh
pwsh
```

PowerShell yeni sürümleri yayımlandığında, yalnızca Homebrew'ın formül güncelleştirin ve PowerShell yükseltme:

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> Yukarıdaki komutlarda PowerShell (pwsh) ana bilgisayar içinde çağrılabilir, ancak sonra PowerShell Kabuk çıkıldı ve gerekir yükseltmesini tamamladıktan sonra $PSVersionTable içinde gösterilen değerleri yenilemek için yeniden.

[brew]: http://brew.sh/
[cask]: https://caskroom.github.io/

### <a name="installation-via-direct-download"></a>Doğrudan indirme ile yükleme

PKG paketini indirin `powershell-6.0.2-osx.10.12-x64.pkg` gelen [Sürümleri][] macOS makinenize sayfası.

Dosyaya çift tıklayın ve yönergeleri izleyin veya terminal durumundan yükleyin:

```sh
sudo installer -pkg powershell-6.0.2-osx.10.12-x64.pkg -target /
```

## <a name="binary-archives"></a>İkili arşivler

PowerShell ikili `tar.gz` arşivler macOS ve gelişmiş dağıtım senaryoları etkinleştirmek için Linux platformlar için sağlanır.

### <a name="installing-binary-archives-on-macos"></a>MacOS üzerinde yükleme ikili arşivler

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.0.2

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.0.2

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.0.2/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.0.2/pwsh /usr/local/bin/pwsh
```

## <a name="uninstalling-powershell-core"></a>PowerShell çekirdek kaldırma

PowerShell ile Homebrew yüklediyseniz, kaldırma işlemi kolaydır:

```sh
brew cask uninstall powershell
```

PowerShell doğrudan indirme yüklediyseniz, PowerShell el ile kaldırılması gerekir:

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

Ek PowerShell yolları kaldırmak için lütfen bkz [yolları][] bölümünde bu belgede ve istenen kullanarak yolları Kaldır `sudo rm`.

> [!NOTE]
> Bu Homebrew ile yüklediyseniz gerekli değildir.

[Yolları]:#paths

## <a name="paths"></a>Yollar

* `$PSHOME` değil `/usr/local/microsoft/powershell/6.0.2/`
* Kullanıcı profillerini okuma `~/.config/powershell/profile.ps1`
* Varsayılan profiller okuma `$PSHOME/profile.ps1`
* Kullanıcı modülleri okuma `~/.local/share/powershell/Modules`
* Paylaşılan modülleri okuma `/usr/local/share/powershell/Modules`
* Varsayılan modülleri okuma `$PSHOME/Modules`
* PSReadline geçmişi için kaydedilen `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

Profilleri PowerShell'in başına ana bilgisayar yapılandırması saygılı olun.
Varsayılan ana bilgisayar özel profiller var böylece `Microsoft.PowerShell_profile.ps1` aynı konumlarda.

PowerShell uyar [XDG temel dizin belirtimi] [ xdg-bds] macOS üzerinde.

MacOS BSD, önek türevi olduğundan `/usr/local` yerine kullanılan `/opt`.
Bu nedenle, `$PSHOME` olan `/usr/local/microsoft/powershell/6.0.2/`, ve simgesel yerleştirilmiş olması `/usr/local/bin/pwsh`.

[Sürümleri]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
