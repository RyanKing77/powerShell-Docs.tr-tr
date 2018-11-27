---
title: Linux’ta PowerShell Core yükleme
description: PowerShell Core yükleme üzerinde çeşitli Linux dağıtımları hakkında bilgi
ms.date: 08/06/2018
ms.openlocfilehash: afb11f053517af592fe42754d543f9f4a9966c5b
ms.sourcegitcommit: 221b7daab7f597f8b2e4864cf9b5d9dda9b9879b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52321120"
---
# <a name="installing-powershell-core-on-linux"></a>Linux’ta PowerShell Core yükleme

Destekler [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.04] [ u1804], [Ubuntu 18.10][u1810], [Debian 8][deb8], [Debian 9] [ deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [ 28 fedora][fedora], ve [Linux arch][arch].

Değil resmi olarak desteklenen Linux dağıtımları için kullanmayı deneyebilirsiniz [PowerShell Yasla paket][snap].
Linux kullanarak doğrudan PowerShell ikili dosyaları dağıtmaya de deneyebilirsiniz [ `tar.gz` arşiv][tar], ancak gerekli bağımlılıkları işletim sisteminde ayrı adımları göre ayarlamanız gerekir.

Tüm paketleri bizim Github'da kullanılabilir [sürümleri][] sayfası.
Paket yüklendikten sonra Çalıştır `pwsh` bir terminalden.

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u1804]: #ubuntu-1804
[u1810]: #ubuntu-1810
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse
[fedora]: #fedora
[arch]: #arch-linux
[snap]: #snap-package
[tar]: #binary-archives

## <a name="installing-preview-releases"></a>Önizleme sürümleri yükleme

PowerShell Core Önizleme sürümü için Paket Deposu aracılığıyla Linux yüklerken, paket adı değişiklikleri `powershell` için `powershell-preview`.

Doğrudan indirme ile yükleme, dosya adı dışında değiştirmez.

Çeşitli paket yöneticilerini kullanarak kararlı ve önizleme paketleri yüklemek için komut tablosu şu şekildedir:

|Distribution(s)|Kararlı komutu | Önizleme komutu |
|---------------|---------------|-----------------|
| Ubuntu, Debian |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| CentOS, RedHat |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| Fedora   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a>Ubuntu 14.04

### <a name="installation-via-package-repository---ubuntu-1404"></a>Paket Deposu - Ubuntu 14.04 aracılığıyla yükleme

Linux için PowerShell Core, paket depolarınızın kolay yükleme (ve güncelleştirmeleri) için yayımlanır.
Bu tercih edilen yöntemdir.

```sh
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/14.04/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

Süper kullanıcı Microsoft depoya kaydedin.
Daha sonra kullanmanız yeterlidir `sudo apt-get upgrade powershell` yüklemesini güncelleştirmek için.

### <a name="installation-via-direct-download---ubuntu-1404"></a>Doğrudan indirme - Ubuntu 14.04 aracılığıyla yükleme

Debian paketi indirin `powershell_6.1.0-1.ubuntu.14.04_amd64.deb`
gelen [sürümleri][] Ubuntu makine sayfaya.

Ardından aşağıdakileri terminalde yürütün:

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> `dpkg -i` Komutu karşılaşılmamış bağımlılıklarıyla birlikte başarısız olur.
> Sonraki komut `apt-get install -f` PowerShell paketi Yapılandırma tamamlandıktan sonra bu sorunları giderir.

### <a name="uninstallation---ubuntu-1404"></a>Kaldırma - Ubuntu 14.04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a>Ubuntu 16.04

### <a name="installation-via-package-repository---ubuntu-1604"></a>Paket Deposu - Ubuntu 16.04 aracılığıyla yükleme

Linux için PowerShell Core, paket depolarınızın kolay yükleme (ve güncelleştirmeleri) için yayımlanır.
Bu tercih edilen yöntemdir.

```sh
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

Microsoft depo süper kullanıcı bir kez kaydolduktan sonra daha sonra kullanmanız yeterlidir `sudo apt-get upgrade powershell` güncelleştirmek için.

### <a name="installation-via-direct-download---ubuntu-1604"></a>Doğrudan indirme - Ubuntu 16.04 aracılığıyla yükleme

Debian paketi indirin `powershell_6.1.0-1.ubuntu.16.04_amd64.deb`
gelen [sürümleri][] Ubuntu makine sayfaya.

Ardından aşağıdakileri terminalde yürütün:

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> `dpkg -i` Komutu karşılaşılmamış bağımlılıklarıyla birlikte başarısız olur.
> Sonraki komut `apt-get install -f` PowerShell paketi Yapılandırma tamamlandıktan sonra bu sorunları giderir.

### <a name="uninstallation---ubuntu-1604"></a>Kaldırma - Ubuntu 16.04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a>Ubuntu 18.04

> [!NOTE]
> Sonra Ubuntu 18.04 desteği eklendi `6.1.0-preview.2`

### <a name="installation-via-package-repository---ubuntu-1804"></a>Paket Deposu - Ubuntu 18.04 aracılığıyla yükleme

Linux için PowerShell Core, paket depolarınızın kolay yükleme (ve güncelleştirmeleri) için yayımlanır.
Bu tercih edilen yöntemdir.

```sh
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

Microsoft depo süper kullanıcı bir kez kaydolduktan sonra daha sonra kullanmanız yeterlidir `sudo apt-get upgrade powershell` güncelleştirmek için.

### <a name="installation-via-direct-download---ubuntu-1804"></a>Doğrudan indirme - Ubuntu 18.04 aracılığıyla yükleme

Debian paketi indirin `powershell_6.1.0-1.ubuntu.18.04_amd64.deb`
gelen [sürümleri][] Ubuntu makine sayfaya.

Ardından aşağıdakileri terminalde yürütün:

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> `dpkg -i` Komutu karşılaşılmamış bağımlılıklarıyla birlikte başarısız olur.
> Sonraki komut `apt-get install -f` PowerShell paketi Yapılandırma tamamlandıktan sonra bu sorunları giderir.

### <a name="uninstallation---ubuntu-1804"></a>Kaldırma - Ubuntu 18.04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a>Ubuntu 18.10

> [!NOTE]
> Ubuntu 18.10 desteği sonra eklenen `6.1.0-preview.3`.
> 18.10 günlük bir derleme olduğundan, yalnızca desteklenen topluluk var.

Üzerinde 18.10 yükleme aracılığıyla desteklenir `snapd`. Bkz: [Yasla paket] [ snap] için tam yönergeler;

## <a name="debian-8"></a>Debian 8

### <a name="installation-via-package-repository---debian-8"></a>Paket Deposu - Debian 8 aracılığıyla yükleme

Linux için PowerShell Core, paket depolarınızın kolay yükleme (ve güncelleştirmeleri) için yayımlanır.
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

Microsoft depo süper kullanıcı bir kez kaydolduktan sonra daha sonra kullanmanız yeterlidir `sudo apt-get upgrade powershell` güncelleştirmek için.

### <a name="installation-via-direct-download---debian-8"></a>Doğrudan indirme - Debian 8 aracılığıyla yükleme

Debian paketi indirin `powershell_6.1.0-1.debian.8_amd64.deb`
gelen [sürümleri][] Debian makine sayfaya.

Ardından aşağıdakileri terminalde yürütün:

```sh
sudo dpkg -i powershell_6.1.0-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> `dpkg -i` Komutu karşılaşılmamış bağımlılıklarıyla birlikte başarısız olur.
> Sonraki komut `apt-get install -f` PowerShell paketi Yapılandırma tamamlandıktan sonra bu sorunları giderir.

### <a name="uninstallation---debian-8"></a>Kaldırma - Debian 8

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a>Debian 9

### <a name="installation-via-package-repository---debian-9"></a>Paket Deposu - Debian 9 aracılığıyla yükleme

Linux için PowerShell Core, paket depolarınızın kolay yükleme (ve güncelleştirmeleri) için yayımlanır.
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

Microsoft depo süper kullanıcı bir kez kaydolduktan sonra daha sonra kullanmanız yeterlidir `sudo apt-get upgrade powershell` güncelleştirmek için.

### <a name="installation-via-direct-download---debian-9"></a>Doğrudan indirme - Debian 9 aracılığıyla yükleme

Debian paketi indirin `powershell_6.1.0-1.debian.9_amd64.deb`
gelen [sürümleri][] Debian makine sayfaya.

Ardından aşağıdakileri terminalde yürütün:

```sh
sudo dpkg -i powershell_6.1.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a>Kaldırma - Debian 9

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a>CentOS 7

> [!NOTE]
> Bu paket, Oracle Linux 7'de de çalışır.

### <a name="installation-via-package-repository-preferred---centos-7"></a>Paket (tercih edilir) - deposu CentOS 7 ile yükleme

Linux için PowerShell Core, resmi Microsoft depolara kolay yükleme (ve güncelleştirmeleri) için yayımlanır.

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

Microsoft depo süper kullanıcı bir kez kaydolduktan sonra kullanmak yeterlidir `sudo yum update powershell` PowerShell güncelleştirilecek.

### <a name="installation-via-direct-download---centos-7"></a>Doğrudan indirme - CentOS 7 ile yükleme

Kullanarak [CentOS 7][], RPM paketini indirme `powershell-6.1.0-1.rhel.7.x86_64.rpm`
gelen [sürümleri][] CentOS makine sayfaya.

Ardından aşağıdakileri terminalde yürütün:

```sh
sudo yum install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

RPM karşıdan ara adım olmadan da yükleyebilirsiniz:

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a>Kaldırma - CentOS 7

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a>Red Hat Enterprise Linux (RHEL) 7

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a>Paket (tercih edilir) - deposu Red Hat Enterprise Linux (RHEL) 7 aracılığıyla yükleme

Linux için PowerShell Core, resmi Microsoft depolara kolay yükleme (ve güncelleştirmeleri) için yayımlanır.

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

Microsoft depo süper kullanıcı bir kez kaydolduktan sonra kullanmak yeterlidir `sudo yum update powershell` PowerShell güncelleştirilecek.

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a>Doğrudan indirme - Red Hat Enterprise Linux (RHEL) 7 aracılığıyla yükleme

RPM paketini indirme `powershell-6.1.0-1.rhel.7.x86_64.rpm`
gelen [sürümleri][] Red Hat Enterprise Linux makine sayfaya.

Ardından aşağıdakileri terminalde yürütün:

```sh
sudo yum install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

RPM karşıdan ara adım olmadan da yükleyebilirsiniz:

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a>Kaldırma - Red Hat Enterprise Linux (RHEL) 7

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a>OpenSUSE

### <a name="installation---opensuse-423"></a>Yükleme - openSUSE 42.3

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar libicu52_1

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/6.1.0

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.1.0

# Set execute permissions
chmod +x /opt/microsoft/powershell/6.1.0/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/6.1.0/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="installation---opensuse-leap-15"></a>Yükleme - openSUSE Leap 15

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar gzip libopenssl1_0_0 libicu60_2

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/6.1.0

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.1.0

# Set execute permissions
chmod +x /opt/microsoft/powershell/6.1.0/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/6.1.0/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a>Kaldırma - openSUSE 42.3, openSUSE Leap 15

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a>Fedora

> [!NOTE]
> 28 fedora yalnızca PowerShell Core 6.1 ve üzeri sürümlerde desteklenir.

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a>Paket (tercih edilir) - deposu Fedora 27 Fedora 28 aracılığıyla yükleme

Linux için PowerShell Core, resmi Microsoft depolara kolay yükleme (ve güncelleştirmeleri) için yayımlanır.

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a>Doğrudan indirme - 27 Fedora, Fedora 28 aracılığıyla yükleme

RPM paketini indirme `powershell-6.1.0-1.rhel.7.x86_64.rpm`
gelen [sürümleri][] Fedora makine sayfaya.

Ardından aşağıdakileri terminalde yürütün:

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

RPM karşıdan ara adım olmadan da yükleyebilirsiniz:

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a>Kaldırma - 27, Fedora Fedora 28

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a>Linux arch

> [!NOTE]
> Deneysel yay desteği.

PowerShell kullanılabilir [Linux arch][] kullanıcı deposu (AUR).

* İle derlenebilir [en son sürümü etiketlendi][arch-release]
* Gelen derlenebilir [ana son kaydetme][arch-git]
* Kullanılarak yüklenebilir [ikili en son sürüm][arch-bin]

AUR paketlerinde saklanır topluluk - resmi desteği yoktur.

AUR paketlerini yükleme hakkında daha fazla bilgi için bkz: [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) veya topluluk [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).

[Linux arch]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a>Paket Yasla

### <a name="getting-snapd"></a>Snapd alma

`snapd` yaslar çalıştırmak için gereklidir.
Kullanım [bu yönergeleri](https://docs.snapcraft.io/core/install) sahip olduğunuzdan emin olmak için `snapd` yüklü.

### <a name="installation-via-snap"></a>Ek bileşeni aracılığıyla yükleme

Linux için PowerShell Core yayımlanmıştır [ek depolama](https://snapcraft.io/store) kolay yükleme (ve güncelleştirmeleri).
Bu tercih edilen yöntemdir.

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

Önizleme sürümünü yüklemek istiyorsanız, yöntemi kullanın.

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

Sonra ek yükleme otomatik olarak yükseltecek, ancak bir yükseltme kullanarak tetikleyebilirsiniz `sudo snap refresh powershell` veya `sudo snap refresh powershell-preview`.

### <a name="uninstallation"></a>Kaldırma

```sh
sudo snap remove powershell
```

veya

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a>Kali

### <a name="installation---kali"></a>Yükleme - Kali

```sh
# Download & Install prerequisites
wget http://ftp.us.debian.org/debian/pool/main/i/icu/libicu57_57.1-9_amd64.deb
dpkg -i libicu57_57.1-9_amd64.deb
apt-get update && apt-get install -y curl gnupg apt-transport-https

# Add Microsoft public repository key to APT
curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -

# Add Microsoft package repository to the source list
echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch main" | tee /etc/apt/sources.list.d/powershell.list

# Install PowerShell package
apt-get update && apt-get install -y powershell

# Start PowerShell
pwsh
```

### <a name="uninstallation---kali"></a>Kaldırma - Kali

```sh
# Uninstall PowerShell package
apt-get remove -y powershell
```

## <a name="raspbian"></a>Raspbian

> [!NOTE]
> Deneysel Raspbian desteği.

Şu anda PowerShell yalnızca Raspbian Esnetme üzerinde desteklenir.

Ayrıca CoreCLR (ve bu nedenle PowerShell Core) yalnızca Pi 2 ve Pi 3 cihazlarında diğer cihazlar gibi çalışır [Pi sıfır](https://github.com/dotnet/coreclr/issues/10605), desteklenmeyen bir işlemciye sahip.

İndirme [Raspbian Esnetme](https://www.raspberrypi.org/downloads/raspbian/) izleyin [yükleme yönergeleri](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) Pi'yi almak için.

### <a name="installation---raspbian"></a>Yükleme - Raspbian

```sh
# Install prerequisites
sudo apt-get install libunwind8

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.1.0-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

İsteğe bağlı olarak PowerShell "pwsh" ikili yol belirtmeden başlatabilmeniz için bir sembolik bağlantı oluşturabilirsiniz.

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

## <a name="binary-archives"></a>İkili Arşivi

PowerShell ikili `tar.gz` arşivleri gelişmiş dağıtım senaryoları etkinleştirmek Linux platformlar için sağlanır.

### <a name="dependencies"></a>Bağımlılıkları

PowerShell tüm Linux dağıtımları için taşınabilir ikili dosyaları oluşturur.
Ancak farklı bağımlılıklara farklı dağıtımlar üzerinde .NET Core çalışma zamanı gerektirir ve bu nedenle aynı PowerShell yapar.

Aşağıdaki tabloda farklı Linux dağıtımlarında resmi olarak desteklenen .NET Core 2.0 bağımlılıkları gösterir.

| İşletim sistemi                 | Bağımlılıkları |
| ------------------ | ------------ |
| Ubuntu 14.04       | libc6, libgcc1, libgssapi-krb5-2 liblttng-ust0, libstdc ++ 6 <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52 |
| Ubuntu 16.04       | libc6, libgcc1, libgssapi-krb5-2 liblttng-ust0, libstdc ++ 6 <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55 |
| Ubuntu 17.10       | libc6, libgcc1, libgssapi-krb5-2 liblttng-ust0, libstdc ++ 6 <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57 |
| Ubuntu 18.04       | libc6, libgcc1, libgssapi-krb5-2 liblttng-ust0, libstdc ++ 6 <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60 |
| Debian 8 (Jessie)  | libc6, libgcc1, libgssapi-krb5-2 liblttng-ust0, libstdc ++ 6 <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52 |
| Debian 9 (Esnetme) | libc6, libgcc1, libgssapi-krb5-2 liblttng-ust0, libstdc ++ 6 <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57 |
| CentOS 7 <br> Oracle Linux 7 <br> RHEL 7 | libunwind, libcurl, openssl kitaplıkları, libicu |
| OpenSUSE 42.3 | libcurl4, libopenssl1_0_0, libicu52_1 |
| openSUSE Leap 15 | libcurl4, libopenssl1_0_0, libicu60_2 |
| Fedora 27 <br> 28 fedora | libunwind, libcurl, openssl kitaplıkları, libicu, compat openssl10 |

Resmi olarak desteklenmez Linux dağıtımlarında PowerShell ikili dosyaları dağıtmak için ayrı adımları hedef işletim sistemi için gerekli bağımlılıkları yüklemeniz gerekir.
Örneğin, bizim [Amazon Linux dockerfile] [ amazon-dockerfile] ilk bağımlılıkları yükler ve ardından Linux ayıklar `tar.gz` arşiv.

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a>Yükleme - ikili Arşivi

#### <a name="linux"></a>Linux

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/6.1.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.1.0

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/6.1.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/6.1.0/pwsh /usr/bin/pwsh
```

### <a name="uninstalling-binary-archives"></a>Kaldırma ikili Arşivi

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a>Yollar

* `$PSHOME` olduğu `/opt/microsoft/powershell/6.1.0/`
* Kullanıcı profillerini okuyabilir `~/.config/powershell/profile.ps1`
* Varsayılan profiller okuyabilir `$PSHOME/profile.ps1`
* Kullanıcı modülleri okuyabilir `~/.local/share/powershell/Modules`
* Paylaşılan modülleri okuyabilir `/usr/local/share/powershell/Modules`
* Varsayılan modülleri okuyabilir `$PSHOME/Modules`
* PSReadline geçmişi için kaydedilir `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

Varsayılan konak özel profilleri var Bu nedenle, PowerShell'in konak başına yapılandırma profilleri dikkate `Microsoft.PowerShell_profile.ps1` aynı konumlarda.

PowerShell uyar [XDG temel dizin belirtimi] [ xdg-bds] Linux üzerinde.

[sürümleri]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
