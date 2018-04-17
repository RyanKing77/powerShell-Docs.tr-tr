# <a name="installing-powershell-core-on-macos-and-linux"></a>macOS ve Linux’ta PowerShell Core yükleme

Destekler [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.04] [ u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7] [ cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 25 ] [ fed25], [Fedora 26][fed26], [Arch Linux][arch]ve [macOS 10,12][mac].

Resmi olarak desteklenmez Linux dağıtımları için kullanmayı deneyebilirsiniz [PowerShell AppImage][lai]. Ayrıca Linux kullanarak doğrudan PowerShell ikili dosyaları dağıtma deneyebilirsiniz [ `tar.gz` arşiv][tar], ancak işletim sisteminde ayrı adımlar göre gerekli bağımlılıkları ayarlamanız gerekir.

Tüm paketler bizim Github'da bulunan [serbest][] sayfası. Paket yüklendikten sonra çalıştırmak `pwsh` bir terminal gelen.

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u17]: #ubuntu-1704
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse-422
[fed25]: #fedora-25
[fed26]: #fedora-26
[arch]: #arch-linux
[lai]: #linux-appimage
[mac]: #macos-1012
[tar]: #binary-archives

## <a name="ubuntu-1404"></a>Ubuntu 14.04

### <a name="installation-via-package-repository---ubuntu-1404"></a>Paket Deposu - Ubuntu 14.04 aracılığıyla yükleme

Linux için PowerShell çekirdek paket depoları kolay yükleme (ve güncelleştirmeleri) için yayımlanır. Bu tercih edilen yöntemdir.

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
curl https://packages.microsoft.com/config/ubuntu/14.04/prod.list | sudo tee /etc/apt/sources.list.d/microsoft.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

Microsoft depo süper kullanıcı bir kez kaydolduktan sonra daha sonra kullanmak yeterlidir `sudo apt-get upgrade powershell` güncelleştirin.

### <a name="installation-via-direct-download---ubuntu-1404"></a>Doğrudan indirme - Ubuntu 14.04 aracılığıyla yükleme

Debian paketi Yükle `powershell_6.0.0-1.ubuntu.14.04_amd64.deb` gelen [serbest][] Ubuntu makine sayfaya.

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.14.04_amd64.deb
```

Ardından aşağıdaki terminale yürütün:

```sh
sudo dpkg -i powershell_6.0.0-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> Lütfen unutmayın `dpkg -i` başarısız unmet bağımlılıkları; sonraki komut `apt-get install -f` Bu çözümler ve daha sonra PowerShell paketi yapılandırma tamamlanır.

### <a name="uninstallation---ubuntu-1404"></a>Kaldırma - Ubuntu 14.04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a>Ubuntu 16.04

### <a name="installation-via-package-repository---ubuntu-1604"></a>Paket Deposu - Ubuntu 16.04 aracılığıyla yükleme

Linux için PowerShell çekirdek paket depoları kolay yükleme (ve güncelleştirmeleri) için yayımlanır.
Bu tercih edilen yöntemdir.

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list | sudo tee /etc/apt/sources.list.d/microsoft.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

Microsoft depo süper kullanıcı bir kez kaydolduktan sonra daha sonra kullanmak yeterlidir `sudo apt-get upgrade powershell` güncelleştirin.

### <a name="installation-via-direct-download---ubuntu-1604"></a>Doğrudan indirme - Ubuntu 16.04 aracılığıyla yükleme

Debian paketi Yükle `powershell_6.0.0-1.ubuntu.16.04_amd64.deb` gelen [serbest][] Ubuntu makine sayfaya:

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.16.04_amd64.deb
```

Ardından aşağıdaki terminale yürütün:

```sh
sudo dpkg -i powershell_6.0.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> Lütfen unutmayın `dpkg -i` başarısız unmet bağımlılıkları; sonraki komut `apt-get install -f` Bu çözümler ve daha sonra PowerShell paketi yapılandırma tamamlanır.

### <a name="uninstallation---ubuntu-1604"></a>Kaldırma - Ubuntu 16.04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1704"></a>Ubuntu 17.04

### <a name="installation-via-package-repository---ubuntu-1704"></a>Paket Deposu - Ubuntu 17.04 aracılığıyla yükleme

Linux için PowerShell çekirdek paket depoları kolay yükleme (ve güncelleştirmeleri) için yayımlanır.
Bu tercih edilen yöntemdir.

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
curl https://packages.microsoft.com/config/ubuntu/17.04/prod.list | sudo tee /etc/apt/sources.list.d/microsoft.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

Microsoft depo süper kullanıcı bir kez kaydolduktan sonra daha sonra kullanmak yeterlidir `sudo apt-get upgrade powershell` güncelleştirin.

### <a name="installation-via-direct-download---ubuntu-1704"></a>Doğrudan indirme - Ubuntu 17.04 aracılığıyla yükleme

Debian paketi Yükle `powershell_6.0.0-1.ubuntu.17.04_amd64.deb` gelen [serbest][] Ubuntu makine sayfaya:

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.17.04_amd64.deb
```

Ardından aşağıdaki terminale yürütün:

```sh
sudo dpkg -i powershell_6.0.0-1.ubuntu.17.04_amd64.deb
sudo apt-get install -f
```

> Lütfen unutmayın `dpkg -i` başarısız unmet bağımlılıkları; sonraki komut `apt-get install -f` Bu çözümler ve daha sonra PowerShell paketi yapılandırma tamamlanır.

### <a name="uninstallation---ubuntu-1704"></a>Kaldırma - Ubuntu 17.04

```sh
sudo apt-get remove powershell
```

## <a name="debian-8"></a>Debian 8

### <a name="installation-via-package-repository---debian-8"></a>Paket Deposu - Debian 8 aracılığıyla yükleme

Linux için PowerShell çekirdek paket depoları kolay yükleme (ve güncelleştirmeleri) için yayımlanır.
Bu tercih edilen yöntemdir.

```sh
# Install system components
sudo apt-get update
sudo apt-get install curl apt-transport-https

# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Product feed
sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-jessie-prod jessie main" > /etc/apt/sources.list.d/microsoft.list'

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

Microsoft depo süper kullanıcı bir kez kaydolduktan sonra daha sonra kullanmak yeterlidir `sudo apt-get upgrade powershell` güncelleştirin.

### <a name="installation-via-direct-download---debian-8"></a>Aracılığıyla doğrudan indirme - Debian 8 yükleme

Debian paketi Yükle `powershell_6.0.0-1.debian.8_amd64.deb` gelen [serbest][] Debian makine sayfaya:

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.debian.8_amd64.deb
```

Ardından aşağıdaki terminale yürütün:

```sh
sudo dpkg -i powershell_6.0.0-1.debian.8_amd64.deb
sudo apt-get install -f
```

> Lütfen unutmayın `dpkg -i` başarısız unmet bağımlılıkları; sonraki komut `apt-get install -f` Bu çözümler ve daha sonra PowerShell paketi yapılandırma tamamlanır.

### <a name="uninstallation---debian-8"></a>Kaldırma - Debian 8

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a>Debian 9

### <a name="installation-via-package-repository---debian-9"></a>Paket Deposu - Debian 9 aracılığıyla yükleme

Linux için PowerShell çekirdek paket depoları kolay yükleme (ve güncelleştirmeleri) için yayımlanır.
Bu tercih edilen yöntemdir.

```sh
# Install system components
sudo apt-get update
sudo apt-get install curl gnupg apt-transport-https

# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Product feed
sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch main" > /etc/apt/sources.list.d/microsoft.list'

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

Microsoft depo süper kullanıcı bir kez kaydolduktan sonra daha sonra kullanmak yeterlidir `sudo apt-get upgrade powershell` güncelleştirin.

### <a name="installation-via-direct-download---debian-9"></a>Doğrudan indirme - Debian 9 aracılığıyla yükleme

Debian paketi Yükle `powershell_6.0.0-1.debian.9_amd64.deb` gelen [serbest][] Debian makine sayfaya:

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.debian.9_amd64.deb
```

Ardından aşağıdaki terminale yürütün:

```sh
sudo dpkg -i powershell_6.0.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

> Lütfen unutmayın `dpkg -i` başarısız unmet bağımlılıkları; sonraki komut `apt-get install -f` Bu çözümler ve daha sonra PowerShell paketi yapılandırma tamamlanır.

### <a name="uninstallation---debian-9"></a>Kaldırma - Debian 9

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a>CentOS 7

> Bu paket, Oracle Linux 7'de de çalışır.

### <a name="installation-via-package-repository-preferred---centos-7"></a>Paket (önerilen) - deposu CentOS 7 aracılığıyla yükleme

Linux için PowerShell çekirdek kolay yükleme (ve güncelleştirmeleri) için resmi Microsoft depoları yayımlanır.

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

Microsoft depo süper kullanıcı bir kez kaydolduktan sonra kullanmak yeterlidir `sudo yum update powershell` PowerShell güncelleştirmek için.

### <a name="installation-via-direct-download---centos-7"></a>Doğrudan indirme - CentOS 7 aracılığıyla yükleme

Kullanarak [CentOS 7][], RPM paketi Yükle `powershell-6.0.0-1.rhel.7.x86_64.rpm` gelen [serbest][] CentOS makine sayfaya:

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

Ardından aşağıdaki terminale yürütün:

```sh
sudo yum install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

Ayrıca, indirilmesi ara adım olmadan RPM yükleyebilirsiniz:

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a>Kaldırma - CentOS 7

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a>Red Hat Enterprise Linux (RHEL) 7

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a>Paket (önerilen) - deposu Red Hat Enterprise Linux (RHEL) 7 aracılığıyla yükleme

Linux için PowerShell çekirdek kolay yükleme (ve güncelleştirmeleri) için resmi Microsoft depoları yayımlanır.

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

Microsoft depo süper kullanıcı bir kez kaydolduktan sonra kullanmak yeterlidir `sudo yum update powershell` PowerShell güncelleştirmek için.

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a>Doğrudan indirme - Red Hat Enterprise Linux (RHEL) 7 aracılığıyla yükleme

RPM paketi Yükle `powershell-6.0.0-1.rhel.7.x86_64.rpm` gelen [serbest][] Red Hat Enterprise Linux makine sayfaya:

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.debian.9_amd64.deb
```

Ardından aşağıdaki terminale yürütün:

```sh
sudo yum install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

Ayrıca, indirilmesi ara adım olmadan RPM yükleyebilirsiniz:

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a>Kaldırma - Red Hat Enterprise Linux (RHEL) 7

```sh
sudo yum remove powershell
```

## <a name="opensuse-422"></a>OpenSUSE 42.2

> **Not:** PowerShell çekirdek yüklerken `zypper` şu hata rapor edebilir:
>
> ```text
> Problem: nothing provides libcurl needed by powershell-6.0.1-1.rhel.7.x86_64
>  Solution 1: do not install powershell-6.0.1-1.rhel.7.x86_64
>  Solution 2: break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies
> ```
>
> Bu durumda, doğrulayın uyumlu bir `libcurl` kitaplığı varsa aşağıdaki gösterir komutu denetleyerek `libcurl4` paketini yüklü olarak:
>
> ```sh
> zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
> ```
>
> Ardından `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` yüklerken çözüm `powershell` paket.

### <a name="installation-via-package-repository-preferred---opensuse-422"></a>Paket (önerilen) - deposu OpenSUSE 42.2 aracılığıyla yükleme

Linux için PowerShell çekirdek kolay yükleme (ve güncelleştirmeleri) için resmi Microsoft depoları yayımlanır.

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Add the Microsoft Product feed
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/zypp/repos.d/microsoft.repo

# Install PowerShell
sudo zypper install powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---opensuse-422"></a>Doğrudan indirme - OpenSUSE 42.2 aracılığıyla yükleme

RPM paketi Yükle `powershell-6.0.0-1.rhel.7.x86_64.rpm` gelen [serbest][] OpenSUSE makine sayfaya:

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

Ayrıca, indirilmesi ara adım olmadan RPM yükleyebilirsiniz:

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-422"></a>Kaldırma - OpenSUSE 42.2

```sh
sudo zypper remove powershell
```

## <a name="fedora-25"></a>Fedora 25

### <a name="installation-via-package-repository-preferred---fedora-25"></a>Paket (önerilen) - deposu Fedora 25 aracılığıyla yükleme

Linux için PowerShell çekirdek kolay yükleme (ve güncelleştirmeleri) için resmi Microsoft depoları yayımlanır.

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Update the list of products
sudo dnf update

# Install PowerShell
sudo dnf install -y powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---fedora-25"></a>Doğrudan indirme - Fedora 25 aracılığıyla yükleme

RPM paketi Yükle `powershell-6.0.0-1.rhel.7.x86_64.rpm` gelen [serbest][] Fedora makine sayfaya:

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

Ardından aşağıdaki terminale yürütün:

```sh
sudo dnf install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

Ayrıca, indirilmesi ara adım olmadan RPM yükleyebilirsiniz:

```sh
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-25"></a>Kaldırma - Fedora 25

```sh
sudo dnf remove powershell
```

## <a name="fedora-26"></a>Fedora 26

### <a name="installation-via-package-repository-preferred---fedora-26"></a>Paket (önerilen) - deposu Fedora 26 aracılığıyla yükleme

Linux için PowerShell çekirdek kolay yükleme (ve güncelleştirmeleri) için resmi Microsoft depoları yayımlanır.

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Update the list of products
sudo dnf update

# Install a system component
sudo dnf install compat-openssl10

# Install PowerShell
sudo dnf install -y powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---fedora-26"></a>Doğrudan indirme - Fedora 26 aracılığıyla yükleme

RPM paketi Yükle `powershell-6.0.0-1.rhel.7.x86_64.rpm` gelen [serbest][] Fedora makine sayfaya:

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

Ardından aşağıdaki terminale yürütün:

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

Ayrıca, indirilmesi ara adım olmadan RPM yükleyebilirsiniz:

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-26"></a>Kaldırma - Fedora 26

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a>Linux arch

PowerShell edinilebilir [Arch Linux][] kullanıcı deposu (AUR).

* İle derlenebilir [en son sürüm etiketli][arch-release]
* Nden derlenebilir [ana son yürütme][arch-git]
* Kullanılarak yüklenebilir [ikili en son sürüm][arch-bin]

AUR paketlerinde saklanır topluluk - resmi desteği yoktur.

AUR paketleri yükleme hakkında daha fazla bilgi için bkz: [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) veya topluluk [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="linux-appimage"></a>Linux AppImage

Son Linux dağıtım kullanarak karşıdan AppImage `powershell-6.0.0-x86_64.AppImage` gelen [serbest][] Linux makine sayfaya.

Ardından aşağıdaki terminale yürütün:

```bash
chmod a+x powershell-6.0.0-x86_64.AppImage
./powershell-6.0.0-x86_64.AppImage
```

[AppImage][] yüklemeden PowerShell çalıştırmanızı sağlar. PowerShell ve bağımlılıklarını (.NET Core'nın sistem bağımlılıklar dahil olmak üzere) bağlı bir pakete sunmaktadır taşınabilir bir uygulamadır. Bu paket, kullanıcının Linux dağıtım bağımsız olarak çalışır ve tek bir ikili dosyadır.

[appimage]: http://appimage.org/

## <a name="macos-1012"></a>macOS 10,12

### <a name="installation-via-homebrew-preferred---macos-1012"></a>(Önerilen) - Homebrew macOS 10,12 aracılığıyla yükleme

[Homebrew] [ brew] macOS için eksik Paket Yöneticisi. Varsa `brew` komutu bulunamadı, Homebrew aşağıdaki yüklemenize gerek [kendi yönergeleri][brew].

Homebrew yükledikten sonra PowerShell yükleme kolaydır. İlk olarak, yükleme [Homebrew Cask][cask], daha fazla paket yükleyebilirsiniz:

```sh
brew tap caskroom/cask
```

Şimdi, PowerShell yükleyebilirsiniz:

```sh
brew cask install powershell
```

PowerShell yeni sürümleri yayımlandığında, yalnızca Homebrew'ın formül güncelleştirin ve PowerShell yükseltme:

```sh
brew update
brew cask upgrade powershell
```

> Not: Yukarıdaki komutlarda gelen içindeki bir PowerShell (pwsh) ana çağrılabilir, ancak sonra PowerShell Kabuk çıkıldı ve gerekir yükseltmeyi tamamlamak ve $PSVersionTable içinde gösterilen değerleri yenilemek için yeniden girildi.

[brew]: http://brew.sh/
[cask]: https://caskroom.github.io/

### <a name="installation-via-direct-download---macos-1012"></a>Doğrudan indirme - macOS 10,12 aracılığıyla yükleme

MacOS 10,12 kullanarak PKG paketini indirin `powershell-6.0.0-osx.10.12-x64.pkg` gelen [serbest][] macOS makine sayfaya.

Dosyaya çift tıklayın ve yönergeleri izleyin veya terminal durumundan yükleyin:

```sh
sudo installer -pkg powershell-6.0.0-osx.10.12-x64.pkg -target /
```

### <a name="uninstallation---macos-1012"></a>Kaldırma - macOS 10,12

PowerShell ile Homebrew yüklediyseniz, kaldırma işlemi kolaydır:

```sh
brew cask uninstall powershell
```

PowerShell doğrudan indirme yüklediyseniz, PowerShell el ile kaldırılması gerekir:

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

Ek PowerShell yolları (örneğin, kullanıcı profili yolu) kaldırmak için lütfen bkz [yolları] [ paths] bu belgede bölüm aşağıda ve istenen kaldırma ile yolları `sudo rm`. (Not: Bu ile Homebrew yüklediyseniz gerekli değildir.)

[paths]:#paths

## <a name="kali"></a>Kali

### <a name="installation"></a>Yükleme

```sh
# Download & Install prerequisites
sudo apt-get install libunwind8 libicu55
wget http://security.debian.org/debian-security/pool/updates/main/o/openssl/libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb
sudo dpkg -i libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb

# Download & Install PowerShell
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.16.04_amd64.deb
sudo dpkg -i powershell_6.0.0-1.ubuntu.16.04_amd64.deb

# Start PowerShell
pwsh
```

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a>PowerShell yüklemeden son Kali içinde (GNU/Linux Kali çalışırken) çalıştırın.

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.0-x86_64.AppImage

# Start PowerShell
./powershell-6.0.0-x86_64.AppImage
```

### <a name="uninstallation---kali"></a>Kaldırma - Kali

```sh
sudo dpkg -r powershell-6.0.0-x86_64.AppImage
```

## <a name="raspbian"></a>Raspbian

Şu anda, PowerShell yalnızca Raspbian Esnetme üzerinde desteklenir.

### <a name="installation"></a>Yükleme

```sh
# Install prerequisites
sudo apt-get install libunwind8

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.0.0-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

### <a name="uninstallation---raspbian"></a>Kaldırma - Raspbian

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a>İkili arşivler

PowerShell ikili `tar.gz` arşivler macOS ve gelişmiş dağıtım senaryoları etkinleştirmek için Linux platformlar için sağlanır.

### <a name="dependencies"></a>Bağımlılıklar

Linux için PowerShell tüm Linux dağıtımları için taşınabilir ikili dosyalarını oluşturur.
Ancak farklı dağıtımların farklı bağımlılıkları .NET çekirdeği çalışma zamanı gerektirir ve bu nedenle PowerShell aynı değil.

Aşağıdaki grafikte .NET Core 2.0 bağımlılıkları resmi olarak desteklenen farklı Linux dağıtımları üzerinde gösterir.

| İşletim sistemi                 | Bağımlılıklar |
| ------------------ | ------------ |
| Ubuntu 14.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6 <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52 |
| Ubuntu 16.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6 <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55 |
| Ubuntu 17.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6 <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57 |
| Debian 8 (Jessie)  | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6 <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52 |
| Debian 9 (Esnetme) | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6 <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57 |
| CentOS 7 <br> Oracle Linux 7 <br> RHEL 7 <br> OpenSUSE 42.2 <br> Fedora 25 | libunwind, libcurl, openssl kitaplıklar, libicu |
| Fedora 26          | libunwind, libcurl, openssl kitaplıklar, libicu, compat openssl10 |

Resmi olarak desteklenmez Linux dağıtımları PowerShell ikili dosyaları dağıtmak için hedef işletim sistemi için gerekli bağımlılıkları ayrı adımlarda yüklemeniz gerekir. Örneğin, bizim [Amazon Linux dockerfile] [ amazon-dockerfile] bağımlılıkları ilk yükler ve Linux ayıklar `tar.gz` arşiv.

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a>Yükleme - ikili arşivler

#### <a name="linux"></a>Linux

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/6.0.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.0.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.0.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/6.0.0/pwsh /usr/bin/pwsh
```

#### <a name="macos"></a>MacOS

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.0.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.0.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.0.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.0.0/pwsh /usr/local/bin/pwsh
```

### <a name="uninstallation---binary-archives"></a>Kaldırma - ikili arşivler

#### <a name="linux"></a>Linux

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

#### <a name="macos"></a>MacOS

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

## <a name="paths"></a>Yollar

* `$PSHOME` değil `/opt/microsoft/powershell/6.0.0/`
* Kullanıcı profillerini okuma `~/.config/powershell/profile.ps1`
* Varsayılan profiller okuma `$PSHOME/profile.ps1`
* Kullanıcı modülleri okuma `~/.local/share/powershell/Modules`
* Paylaşılan modülleri okuma `/usr/local/share/powershell/Modules`
* Varsayılan modülleri okuma `$PSHOME/Modules`
* PSReadline geçmişi için kaydedilen `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

Varsayılan ana bilgisayar özel profiller var böylece profilleri PowerShell'in başına ana bilgisayar yapılandırması saygı `Microsoft.PowerShell_profile.ps1` aynı konumlarda.

Linux ve macOS, [XDG temel dizin belirtimi] [ xdg-bds] dikkate.

MacOS yerine bir türevi BSD, çünkü unutmayın `/opt`, kullanılan öneki `/usr/local`. Bu nedenle, `$PSHOME` olan `/usr/local/microsoft/powershell/6.0.0/`, ve simgesel yerleştirilmiş olması `/usr/local/bin/pwsh`.

[serbest]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
