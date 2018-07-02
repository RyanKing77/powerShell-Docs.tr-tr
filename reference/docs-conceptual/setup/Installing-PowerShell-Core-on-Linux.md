# <a name="installing-powershell-core-on-linux"></a>Linux’ta PowerShell Core yükleme

Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.10][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].

Resmi olarak desteklenmez Linux dağıtımları için kullanmayı deneyebilirsiniz [PowerShell AppImage][lai].
Ayrıca Linux kullanarak doğrudan PowerShell ikili dosyaları dağıtma deneyebilirsiniz [ `tar.gz` arşiv][tar], ancak işletim sisteminde ayrı adımlar göre gerekli bağımlılıkları ayarlamanız gerekir.

Tüm paketler bizim Github'da bulunan [serbest][] sayfası.
Paket yüklendikten sonra çalıştırmak `pwsh` bir terminal gelen.

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u17]: #ubuntu-1710
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse-422
[fedora]: #fedora
[arch]: #arch-linux
[lai]: #linux-appimage
[tar]: #binary-archives

## <a name="installing-preview-releases"></a>Önizleme sürümleri yükleme

PowerShell çekirdek Önizleme sürümü için bir paket deposu aracılığıyla Linux yüklerken, paket adı değişiklikleri `powershell` için `powershell-preview`.

Doğrudan indirme yükleme, dosya adı dışında değiştirmez.

Çeşitli paket yöneticileri kullanarak kararlı ve önizleme paketleri yüklemek için komutları tablosu aşağıdadır:

|Distrobution(s)|Kararlı komutu | Önizleme komutu |
|---------------|---------------|-----------------|
| Ubuntu, Debian |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| CentOS, RedHat |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| openSUSE |`sudo zypper install powershell` | `sudo zypper install powershell-preview`|
| Fedora   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a>Ubuntu 14.04

### <a name="installation-via-package-repository---ubuntu-1404"></a>Paket Deposu - Ubuntu 14.04 aracılığıyla yükleme

Linux için PowerShell çekirdek paket depoları kolay yükleme (ve güncelleştirmeleri) için yayımlanır.
Bu tercih edilen yöntemdir.

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

Süper kullanıcı Microsoft depoya kaydedin.
Daha sonra kullanmak yeterlidir `sudo apt-get upgrade powershell` yüklemeyi güncelleştirmek için.

### <a name="installation-via-direct-download---ubuntu-1404"></a>Doğrudan indirme - Ubuntu 14.04 aracılığıyla yükleme

Debian paketi Yükle `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` gelen [serbest][] Ubuntu makine sayfaya.

Ardından aşağıdaki terminale yürütün:

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> `dpkg -i` Komut unmet bağımlılıkları ile başarısız olur.
> Sonraki komutu `apt-get install -f` PowerShell paketi Yapılandırma tamamlandıktan sonra bu sorunları giderir.

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
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/16.04/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

Microsoft depo süper kullanıcı bir kez kaydolduktan sonra daha sonra kullanmak yeterlidir `sudo apt-get upgrade powershell` güncelleştirin.

### <a name="installation-via-direct-download---ubuntu-1604"></a>Doğrudan indirme - Ubuntu 16.04 aracılığıyla yükleme

Debian paketi Yükle `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` gelen [serbest][] Ubuntu makine sayfaya.

Ardından aşağıdaki terminale yürütün:

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> `dpkg -i` Komut unmet bağımlılıkları ile başarısız olur.
> Sonraki komutu `apt-get install -f` PowerShell paketi Yapılandırma tamamlandıktan sonra bu sorunları giderir.

### <a name="uninstallation---ubuntu-1604"></a>Kaldırma - Ubuntu 16.04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1710"></a>Ubuntu 17.10

> [!NOTE]
> Sonra Ubuntu 17.04 desteği eklendi `6.1.0-preview.2`

### <a name="installation-via-package-repository---ubuntu-1710"></a>Paket Deposu - Ubuntu 17.10 aracılığıyla yükleme

Linux için PowerShell çekirdek paket depoları kolay yükleme (ve güncelleştirmeleri) için yayımlanır.
Bu tercih edilen yöntemdir.

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/17.10/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

Microsoft depo süper kullanıcı bir kez kaydolduktan sonra daha sonra kullanmak yeterlidir `sudo apt-get upgrade powershell` güncelleştirin.

### <a name="installation-via-direct-download---ubuntu-1710"></a>Doğrudan indirme - Ubuntu 17.10 aracılığıyla yükleme

Debian paketi Yükle `powershell_6.0.2-1.ubuntu.17.10_amd64.deb` gelen [serbest][] Ubuntu makine sayfaya.

Ardından aşağıdaki terminale yürütün:

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.17.10_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> `dpkg -i` Komut unmet bağımlılıkları ile başarısız olur.
> Sonraki komutu `apt-get install -f` PowerShell paketi Yapılandırma tamamlandıktan sonra bu sorunları giderir.

### <a name="uninstallation---ubuntu-1710"></a>Kaldırma - Ubuntu 17.10

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a>Ubuntu 18.04

> [!NOTE]
> Sonra Ubuntu 18.04 desteği eklendi `6.1.0-preview.2`

### <a name="installation-via-package-repository---ubuntu-1804"></a>Paket Deposu - Ubuntu 18.04 aracılığıyla yükleme

Linux için PowerShell çekirdek paket depoları kolay yükleme (ve güncelleştirmeleri) için yayımlanır.
Bu tercih edilen yöntemdir.

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/18.04/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

Microsoft depo süper kullanıcı bir kez kaydolduktan sonra daha sonra kullanmak yeterlidir `sudo apt-get upgrade powershell` güncelleştirin.

### <a name="installation-via-direct-download---ubuntu-1804"></a>Doğrudan indirme - Ubuntu 18.04 aracılığıyla yükleme

Debian paketi Yükle `powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb` gelen [serbest][] Ubuntu makine sayfaya.

Ardından aşağıdaki terminale yürütün:

```sh
sudo dpkg -i powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> `dpkg -i` Komut unmet bağımlılıkları ile başarısız olur.
> Sonraki komutu `apt-get install -f` PowerShell paketi Yapılandırma tamamlandıktan sonra bu sorunları giderir.

### <a name="uninstallation---ubuntu-1710"></a>Kaldırma - Ubuntu 17.10

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

Debian paketi Yükle `powershell_6.0.2-1.debian.8_amd64.deb` gelen [serbest][] Debian makine sayfaya.

Ardından aşağıdaki terminale yürütün:

```sh
sudo dpkg -i powershell_6.0.2-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> `dpkg -i` Komut unmet bağımlılıkları ile başarısız olur.
> Sonraki komutu `apt-get install -f` PowerShell paketi Yapılandırma tamamlandıktan sonra bu sorunları giderir.

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

Debian paketi Yükle `powershell_6.0.2-1.debian.9_amd64.deb` gelen [serbest][] Debian makine sayfaya.

Ardından aşağıdaki terminale yürütün:

```sh
sudo dpkg -i powershell_6.0.2-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a>Kaldırma - Debian 9

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a>CentOS 7

> [!NOTE]
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

Kullanarak [CentOS 7][], RPM paketi Yükle `powershell-6.0.2-1.rhel.7.x86_64.rpm` gelen [serbest][] CentOS makine sayfaya.

Ardından aşağıdaki terminale yürütün:

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

Ayrıca, indirilmesi ara adım olmadan RPM yükleyebilirsiniz:

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
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

RPM paketi Yükle `powershell-6.0.2-1.rhel.7.x86_64.rpm` gelen [serbest][] Red Hat Enterprise Linux makine sayfaya.

Ardından aşağıdaki terminale yürütün:

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

Ayrıca, indirilmesi ara adım olmadan RPM yükleyebilirsiniz:

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a>Kaldırma - Red Hat Enterprise Linux (RHEL) 7

```sh
sudo yum remove powershell
```

## <a name="opensuse-422"></a>OpenSUSE 42.2

PowerShell çekirdek yüklerken `zypper` şu hata rapor edebilir:

```Output
Problem: nothing provides libcurl needed by powershell-6.0.1-1.rhel.7.x86_64
 Solution 1: do not install powershell-6.0.1-1.rhel.7.x86_64
 Solution 2: break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies
```

Bu durumda, doğrulayın uyumlu bir `libcurl` kitaplığı varsa aşağıdaki gösterir komutu denetleyerek `libcurl4` paketini yüklü olarak:

```sh
zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
```

Ardından `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` PowerShell paket yüklerken çözümü.

### <a name="installation-via-package-repository-preferred---opensuse-422"></a>Paket (önerilen) - deposu OpenSUSE 42.2 aracılığıyla yükleme

Linux için PowerShell çekirdek kolay yükleme (ve güncelleştirmeleri) için resmi Microsoft depoları yayımlanır.

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Add the Microsoft Product feed
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/zypp/repos.d/microsoft.repo

# Update the list of products
sudo zypper update

# Install PowerShell
sudo zypper install powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---opensuse-422"></a>Doğrudan indirme - OpenSUSE 42.2 aracılığıyla yükleme

RPM paketi Yükle `powershell-6.0.2-1.rhel.7.x86_64.rpm` gelen [serbest][] OpenSUSE makine sayfaya.

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

Ayrıca, indirilmesi ara adım olmadan RPM yükleyebilirsiniz:

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-422"></a>Kaldırma - OpenSUSE 42.2

```sh
sudo zypper remove powershell
```

## <a name="fedora"></a>Fedora

> [!NOTE]
> Fedora 28 yalnızca PowerShell çekirdek 6.1 ve sonraki sürümleri desteklenir.

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a>Paket (önerilen) - deposu Fedora 27 Fedora 28 aracılığıyla yükleme

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a>Doğrudan indirme - Fedora 27, Fedora 28 aracılığıyla yükleme

RPM paketi Yükle `powershell-6.0.2-1.rhel.7.x86_64.rpm` gelen [serbest][] Fedora makine sayfaya.

Ardından aşağıdaki terminale yürütün:

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

Ayrıca, indirilmesi ara adım olmadan RPM yükleyebilirsiniz:

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a>Kaldırma - Fedora 27, Fedora 28

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a>Linux arch

> [!NOTE]
> Yay Deneysel desteğidir.

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

> [!NOTE]
> Deneysel AppImage desteği

Son Linux dağıtım kullanarak karşıdan AppImage `powershell-6.0.1-x86_64.AppImage` gelen [serbest][] Linux makine sayfaya.

Ardından aşağıdaki terminale yürütün:

```bash
chmod a+x powershell-6.0.1-x86_64.AppImage
./powershell-6.0.1-x86_64.AppImage
```

[AppImage][] yüklemeden PowerShell çalıştırmanızı sağlar.
PowerShell ve bağımlılıklarını (.NET Core'nın sistem bağımlılıklar dahil olmak üzere) bağlı bir pakete sunmaktadır taşınabilir bir uygulamadır.
Kullanıcının Linux dağıtım bağımsız olarak çalışır, tek bir ikili paketidir.

[appimage]: http://appimage.org/

## <a name="kali"></a>Kali

> [!NOTE]
> Kali desteği Deneysel değil.

### <a name="installation"></a>Yükleme

```sh
# Download & Install prerequisites
sudo apt-get install libunwind8 libicu55
wget http://security.debian.org/debian-security/pool/updates/main/o/openssl/libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb
sudo dpkg -i libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb

# Install PowerShell
sudo dpkg -i powershell_6.0.2-1.ubuntu.16.04_amd64.deb

# Start PowerShell
pwsh
```

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a>PowerShell yüklemeden son Kali içinde (GNU/Linux Kali çalışırken) çalıştırın.

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.2-x86_64.AppImage

# Start PowerShell
./powershell-6.0.2-x86_64.AppImage
```

### <a name="uninstallation---kali"></a>Kaldırma - Kali

```sh
sudo dpkg -r powershell_6.0.2-1.ubuntu.16.04_amd64.deb
```

## <a name="raspbian"></a>Raspbian

> [!NOTE]
> Raspbian desteği Deneysel değil.

Şu anda, PowerShell yalnızca Raspbian Esnetme üzerinde desteklenir.

Ayrıca CoreCLR (ve bu nedenle PowerShell çekirdeği) yalnızca Pi 2 ve 3 PI cihazlarda diğer cihazlar olarak gibi çalışır [Pi sıfır](https://github.com/dotnet/coreclr/issues/10605), desteklenmeyen bir işlemciye sahip.

Karşıdan [Raspbian Esnetme](https://www.raspberrypi.org/downloads/raspbian/) ve izleyin [yükleme yönergeleri](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) , Pi almak için.

### <a name="installation"></a>Yükleme

```sh
# Install prerequisites
sudo apt-get install libunwind8

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.0.2-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

İsteğe bağlı olarak, PowerShell "pwsh" ikili yoluna belirtmeden başlatabilmek için sembolik bağlantı oluşturabilirsiniz

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a>Kaldırma - Raspbian

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a>İkili arşivler

PowerShell ikili `tar.gz` arşivler gelişmiş dağıtım senaryoları etkinleştirmek Linux platformlar için sağlanır.

### <a name="dependencies"></a>Bağımlılıklar

PowerShell tüm Linux dağıtımları için taşınabilir ikili dosyalarını oluşturur.
Ancak farklı dağıtımların farklı bağımlılıkları .NET çekirdeği çalışma zamanı gerektirir ve bu nedenle PowerShell aynı değil.

Aşağıdaki grafikte farklı Linux dağıtımları üzerinde resmi olarak desteklenen .NET Core 2.0 bağımlılıkları gösterir.

| İşletim sistemi                 | Bağımlılıklar |
| ------------------ | ------------ |
| Ubuntu 14.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6 <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52 |
| Ubuntu 16.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6 <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55 |
| Ubuntu 17.10       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6 <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57 |
| Ubuntu 18.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6 <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60 |
| Debian 8 (Jessie)  | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6 <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52 |
| Debian 9 (Esnetme) | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6 <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57 |
| CentOS 7 <br> Oracle Linux 7 <br> RHEL 7 <br> OpenSUSE 42.2 | libunwind, libcurl, openssl kitaplıklar, libicu |
| Fedora 27 <br> Fedora 28 | libunwind, libcurl, openssl kitaplıklar, libicu, compat openssl10 |

Resmi olarak desteklenmez Linux dağıtımları PowerShell ikili dosyaları dağıtmak için hedef işletim sistemi için gerekli bağımlılıkları ayrı adımlarda yüklemeniz gerekir.
Örneğin, bizim [Amazon Linux dockerfile] [ amazon-dockerfile] bağımlılıkları ilk yükler ve Linux ayıklar `tar.gz` arşiv.

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a>Yükleme - ikili arşivler

#### <a name="linux"></a>Linux

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/6.0.2

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.0.2

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/6.0.2/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/6.0.2/pwsh /usr/bin/pwsh
```

### <a name="uninstalling-binary-archives"></a>Kaldırma ikili arşivler

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a>Yollar

* `$PSHOME` değil `/opt/microsoft/powershell/6.0.2/`
* Kullanıcı profillerini okuma `~/.config/powershell/profile.ps1`
* Varsayılan profiller okuma `$PSHOME/profile.ps1`
* Kullanıcı modülleri okuma `~/.local/share/powershell/Modules`
* Paylaşılan modülleri okuma `/usr/local/share/powershell/Modules`
* Varsayılan modülleri okuma `$PSHOME/Modules`
* PSReadline geçmişi için kaydedilen `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

Varsayılan ana bilgisayar özel profiller var böylece profilleri PowerShell'in başına ana bilgisayar yapılandırması saygı `Microsoft.PowerShell_profile.ps1` aynı konumlarda.

PowerShell uyar [XDG temel dizin belirtimi] [ xdg-bds] Linux üzerinde.

[serbest]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
