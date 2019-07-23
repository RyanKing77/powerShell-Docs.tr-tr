---
title: Linux’ta PowerShell Core yükleme
description: Çeşitli Linux dağıtımlarına PowerShell Core yükleme hakkında bilgi
ms.date: 07/19/2019
ms.openlocfilehash: 929b153ef784f3203cd31a0e2fc52e744a07532f
ms.sourcegitcommit: 118eb294d5a84a772e6449d42a9d9324e18ef6b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/22/2019
ms.locfileid: "68372187"
---
# <a name="installing-powershell-core-on-linux"></a>Linux’ta PowerShell Core yükleme

[Ubuntu 16,04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18,10][u1810], [de, 9][deb9],
 [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42,3][opensuse], [openSUSE artık 15][opensuse] , [Fedora 27][fedora]'idestekler, [Fedora 28][Fedora]ve [mimari Linux][arch].

Resmi olarak desteklenen Linux dağıtımları için PowerShell [Snap paketini][snap]kullanarak PowerShell 'i yüklemeyi deneyebilirsiniz. Ayrıca, Linux [ `tar.gz` Arşivi][tar]kullanarak PowerShell ikililerini doğrudan dağıtmaya da deneyebilirsiniz, ancak işletim sistemini ayrı adımlarda temel alarak gerekli bağımlılıkları ayarlamanız gerekir.

Tüm paketleri GitHub [yayınları][] sayfamızda bulabilirsiniz. Paket yüklendikten sonra bir terminalden çalıştırın `pwsh` .

[u16]: #ubuntu-1604
[u1804]: #ubuntu-1804
[u1810]: #ubuntu-1810
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse
[fedora]: #fedora
[arch]: #arch-linux
[snap]: #snap-package
[tar]: #binary-archives

## <a name="installing-preview-releases"></a>Önizleme sürümleri yükleniyor

Bir paket deposu aracılığıyla Linux için bir PowerShell Core Preview sürümü yüklerken, paket adı ' dan `powershell` `powershell-preview`' a değişir.

Doğrudan indirme aracılığıyla yükleme, dosya adından başka bir değişiklik yapmaz.

Aşağıdaki tabloda, çeşitli paket yöneticilerini kullanarak kararlı ve önizleme paketlerini yüklemeye yönelik komutlar yer almaktadır:

|Dağıtım (ler)|Stable komutu | Önizleme komutu |
|---------------|---------------|-----------------|
| Ubuntu, dene |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| CentOS, RedHat |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| Fedora   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1604"></a>Ubuntu 16.04

### <a name="installation-via-package-repository---ubuntu-1604"></a>Paket deposu aracılığıyla yükleme-Ubuntu 16,04

Linux için PowerShell Core, kolay yükleme ve güncelleştirmeler için paket depolarında yayımlanır.

Tercih edilen yöntem aşağıdaki gibidir:

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

Süper Kullanıcı olarak Microsoft Repository 'yi bir kez kaydettirin. Kayıttan sonra PowerShell 'i ile `sudo apt-get upgrade powershell`güncelleştirebilirsiniz.

### <a name="installation-via-direct-download---ubuntu-1604"></a>Doğrudan Download-Ubuntu 16,04 aracılığıyla yükleme

[yayınları][] sayfasından Ubuntu `powershell_6.2.0-1.ubuntu.16.04_amd64.deb` makinesine deleyi paketini indirin.

Ardından, terminalde aşağıdaki komutları yürütün:

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> `dpkg -i` Komut karşılanmamış bağımlılıklarla başarısız olur. Sonraki komut, `apt-get install -f` bu sorunları çözer ve PowerShell paketini yapılandırmayı tamamlar.

### <a name="uninstallation---ubuntu-1604"></a>Kaldırma-Ubuntu 16,04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a>Ubuntu 18.04

### <a name="installation-via-package-repository---ubuntu-1804"></a>Paket deposu aracılığıyla yükleme-Ubuntu 18,04

Linux için PowerShell Core, kolay yükleme ve güncelleştirmeler için paket depolarında yayımlanır.

Tercih edilen yöntem aşağıdaki gibidir:

```sh
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Enable the "universe" repositories
sudo add-apt-repository universe

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

Süper Kullanıcı olarak Microsoft Repository 'yi bir kez kaydettirin. Kayıttan sonra PowerShell 'i ile `sudo apt-get upgrade powershell`güncelleştirebilirsiniz.

### <a name="installation-via-direct-download---ubuntu-1804"></a>Doğrudan Download-Ubuntu 18,04 aracılığıyla yükleme

[yayınları][] sayfasından Ubuntu `powershell_6.2.0-1.ubuntu.18.04_amd64.deb` makinesine deleyi paketini indirin.

Ardından, terminalde aşağıdaki komutları yürütün:

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> `dpkg -i` Komut karşılanmamış bağımlılıklarla başarısız olur. Sonraki komut, `apt-get install -f` bu sorunları çözer ve PowerShell paketini yapılandırmayı tamamlar.

### <a name="uninstallation---ubuntu-1804"></a>Kaldırma-Ubuntu 18,04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a>Ubuntu 18,10

> [!NOTE]
> 18,10, geçici bir [Sürüm](https://www.ubuntu.com/about/release-cycle)olduğundan yalnızca [topluluk desteklenir](https://docs.microsoft.com/en-us/powershell/scripting/powershell-support-lifecycle?view=powershell-6).

18,10 üzerine yükleme, aracılığıyla `snapd`desteklenir. Bkz. tam yönergeler için [yaslama paketi][snap] ;

## <a name="debian-8"></a>Debian 8

### <a name="installation-via-package-repository---debian-8"></a>Paket deposu aracılığıyla yükleme-detem 8

Linux için PowerShell Core, kolay yükleme ve güncelleştirmeler için paket depolarında yayımlanır.

Tercih edilen yöntem aşağıdaki gibidir:

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

Süper Kullanıcı olarak Microsoft Repository 'yi bir kez kaydettirin. Kayıttan sonra PowerShell 'i ile `sudo apt-get upgrade powershell`güncelleştirebilirsiniz.

## <a name="debian-9"></a>Debian 9

### <a name="installation-via-package-repository---debian-9"></a>Paket deposu aracılığıyla yükleme-detem 9

Linux için PowerShell Core, kolay yükleme ve güncelleştirmeler için paket depolarında yayımlanır.

Tercih edilen yöntem aşağıdaki gibidir:

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

Süper Kullanıcı olarak Microsoft Repository 'yi bir kez kaydettirin. Kayıttan sonra PowerShell 'i ile `sudo apt-get upgrade powershell`güncelleştirebilirsiniz.

### <a name="installation-via-direct-download---debian-9"></a>Doğrudan Indirme ile yükleme-detem 9

[yayınları][] sayfasından debir makineye `powershell_6.2.0-1.debian.9_amd64.deb` olan deleyi paketini indirin.

Ardından, terminalde aşağıdaki komutları yürütün:

```sh
sudo dpkg -i powershell_6.2.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a>Kaldırma-kaldırıcı 9

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a>CentOS 7

> [!NOTE]
> Bu paket Oracle Linux 7 ' de çalışmaktadır.

### <a name="installation-via-package-repository-preferred---centos-7"></a>Paket deposu aracılığıyla yükleme (tercih edilen)-CentOS 7

Linux için PowerShell Core, kolay yükleme ve güncelleştirmeler için resmi Microsoft depolarında yayımlanır.

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

Süper Kullanıcı olarak Microsoft Repository 'yi bir kez kaydettirin. Kayıttan sonra PowerShell 'i ile `sudo yum update powershell`güncelleştirebilirsiniz.

### <a name="installation-via-direct-download---centos-7"></a>Doğrudan Indirme ile yükleme-CentOS 7

[CentOS 7][]' yi kullanarak, [yayınları][] sayfasından `powershell-6.2.0-1.rhel.7.x86_64.rpm` CentOS makinesine RPM paketini indirin.

Ardından, terminalde aşağıdaki komutları yürütün:

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

Yükleme işlemi için ara adım olmadan RPM 'yi yükleyebilirsiniz:

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a>Kaldırma-CentOS 7

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a>Red Hat Enterprise Linux (RHEL) 7

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a>Paket deposu aracılığıyla yükleme (tercih edilen)-Red Hat Enterprise Linux (RHEL) 7

Linux için PowerShell Core, kolay yükleme ve güncelleştirmeler için resmi Microsoft depolarında yayımlanır.

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

Süper Kullanıcı olarak Microsoft Repository 'yi bir kez kaydettirin. Kayıttan sonra PowerShell 'i ile `sudo yum update powershell`güncelleştirebilirsiniz.

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a>Doğrudan Indirme ile yükleme-Red Hat Enterprise Linux (RHEL) 7

Sürümler sayfasından Red Hat Enterprise Linux makineye `powershell-6.2.0-1.rhel.7.x86_64.rpm` RPM paketini [yayınları][].

Ardından, terminalde aşağıdaki komutları yürütün:

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

Yükleme işlemi için ara adım olmadan RPM 'yi yükleyebilirsiniz:

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a>Kaldırma-Red Hat Enterprise Linux (RHEL) 7

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a>openSUSE

### <a name="installation---opensuse-423"></a>Yükleme-openSUSE 42,3

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar libicu52_1

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/6.2.0

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.2.0

# Set execute permissions
chmod +x /opt/microsoft/powershell/6.2.0/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/6.2.0/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="installation---opensuse-leap-15"></a>Yükleme-openSUSE artık 15

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar gzip libopenssl1_0_0 libicu60_2

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/6.2.0

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.2.0

# Set execute permissions
chmod +x /opt/microsoft/powershell/6.2.0/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/6.2.0/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a>Kaldırma-openSUSE 42,3, openSUSE artık 15

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a>Fedora

> [!NOTE]
> Fedora 28 yalnızca PowerShell Core 6,1 ve daha yeni sürümlerde desteklenir.

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a>Paket deposu aracılığıyla yükleme (tercih edilen)-Fedora 27, Fedora 28

Linux için PowerShell Core, kolay yükleme ve güncelleştirmeler için resmi Microsoft depolarında yayımlanır.

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a>Doğrudan Indirme ile yükleme-Fedora 27, Fedora 28

`powershell-6.2.0-1.rhel.7.x86_64.rpm` [yayınları][] sayfasından Fedora makinesine RPM paketini indirin.

Ardından, terminalde aşağıdaki komutları yürütün:

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

Yükleme işlemi için ara adım olmadan RPM 'yi yükleyebilirsiniz:

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a>Kaldırma-Fedora 27, Fedora 28

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a>Mimari Linux

> [!NOTE]
> Mimari desteği deneysel.

PowerShell, [mimari Linux][] kullanıcı deposundan (AUR) kullanılabilir.

* [En son etiketli sürümle][arch-release] derlenebilir
* [En son işlemeden ana şablona][arch-git] derlenebilir
* [En son sürüm ikilisi][arch-bin] kullanılarak yüklenebilir

AUR 'teki paketler topluluk tarafından korunur; resmi olmayan destek yoktur.

AUR 'ten paket yükleme hakkında daha fazla bilgi için bkz. [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) veya Community [dockerfile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).

[Mimari Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a>Yaslama paketi

### <a name="getting-snapd"></a>Anlık görüntü alınıyor

`snapd`yapış çalıştırmak için gereklidir. Yüklediğinizden emin `snapd` olmak için [Bu yönergeleri](https://docs.snapcraft.io/core/install) kullanın.

### <a name="installation-via-snap"></a>Yaslama aracılığıyla yükleme

Linux için PowerShell Core, kolay yükleme ve güncelleştirmeler için [Snap deposunda](https://snapcraft.io/store) yayımlanır.

Tercih edilen yöntem aşağıdaki gibidir:

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

Önizleme sürümünü yüklemek için aşağıdaki yöntemi kullanın:

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

Yükleme sonrasında, yaslama otomatik olarak yükseltilir. `sudo snap refresh powershell` Veya`sudo snap refresh powershell-preview`kullanarak bir yükseltmeyi tetikleyebilirsiniz.

### <a name="uninstallation"></a>CP

```sh
sudo snap remove powershell
```

veya

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a>Kalı

### <a name="installation---kali"></a>Yükleme-kalı

```sh
# Download & Install prerequisites
wget http://ftp.us.debian.org/debian/pool/main/i/icu/libicu57_57.1-6+deb9u2_amd64.deb
dpkg -i libicu57_57.1-6+deb9u2_amd64.deb
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

### <a name="uninstallation---kali"></a>Kaldırma-kalı

```sh
# Uninstall PowerShell package
apt-get remove -y powershell
```

## <a name="raspbian"></a>Raspbian

> [!NOTE]
> Raspbian desteği deneysel.

Şu anda PowerShell yalnızca Raspbian Esnette destekleniyor.

CoreCLR ve PowerShell Core yalnızca PI 2 ve PI 3 cihazlarda, [PI sıfır](https://github.com/dotnet/coreclr/issues/10605)gibi diğer cihazlar için de çalışır ve desteklenmeyen bir işlemciye sahip olur.

[Raspbian Esnetme](https://www.raspberrypi.org/downloads/raspbian/) Indirin ve PI 'larınızın üzerine ulaşmak için [yükleme yönergelerini](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) izleyin.

### <a name="installation---raspbian"></a>Yükleme-Raspbian

```sh
###################################
# Prerequisites

# Update package lists
sudo apt-get update

# Install libunwind8 and libssl1.0
# Regex is used to ensure that we do not install libssl1.0-dev, as it is a variant that is not required
sudo apt-get install '^libssl1.0.[0-9]$' libunwind8 -y

###################################
# Download and extract PowerShell

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.2.0-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

İsteğe bağlı olarak, `pwsh` ikili dosyanın yolunu belirtmeden PowerShell 'i başlatmak için bir sembolik bağlantı oluşturabilirsiniz.

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a>Kaldırma-Raspbian

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a>İkili Arşivler

PowerShell ikili `tar.gz` arşivleri, Linux platformları için gelişmiş dağıtım senaryolarını etkinleştirmek üzere sağlanır.

### <a name="dependencies"></a>Bağımlılıkları

PowerShell, tüm Linux dağıtımları için taşınabilir ikili dosyalar oluşturur. Ancak, .NET Core çalışma zamanı farklı dağıtımlarda farklı bağımlılıklar gerektirir ve PowerShell de çok fazla yapılır.

Aşağıdaki grafikte, farklı Linux dağıtımları üzerinde resmi olarak desteklenen .NET Core 2,0 bağımlılıkları gösterilmektedir.

| İşletim sistemi                 | Bağımlılıkları |
| ------------------ | ------------ |
| Ubuntu 16.04       | libc6, libgcc1, libgssapı-krb5-2, liblttng-ust0, libstdc + + 6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu55 |
| Ubuntu 17,10       | libc6, libgcc1, libgssapı-krb5-2, liblttng-ust0, libstdc + + 6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu57 |
| Ubuntu 18.04       | libc6, libgcc1, libgssapı-krb5-2, liblttng-ust0, libstdc + + 6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu60 |
| Desek8 (Jese)  | libc6, libgcc1, libgssapı-krb5-2, liblttng-ust0, libstdc + + 6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu52 |
| Deda 9 (uzat) | libc6, libgcc1, libgssapı-krb5-2, liblttng-ust0, libstdc + + 6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.2, libicu57 |
| CentOS 7 <br> Oracle Linux 7 <br> RHEL 7 | librüzgar, Libya, OpenSSL-libs, libıu |
| openSUSE 42,3 | libcurl4, libopenssl1_0_0, libicu52_1 |
| openSUSE artık 15 | libcurl4, libopenssl1_0_0, libicu60_2 |
| Fedora 27 <br> Fedora 28 | libıwind, libkıvrık, OpenSSL-libs, libıu, COMPAT-openssl10 |

Resmi olarak desteklenmeyen Linux dağıtımlarına PowerShell ikilileri dağıtmak için, hedef işletim sistemi için gerekli bağımlılıkları ayrı adımlarda yüklemeniz gerekir. Örneğin, [Amazon Linux dockerfile][amazon-dockerfile] , önce bağımlılıkları yüklüyor ve ardından Linux `tar.gz` arşivini ayıklar.

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a>Yükleme-Ikili arşivleri

#### <a name="linux"></a>Linux

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/6.2.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.2.0

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/6.2.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/6.2.0/pwsh /usr/bin/pwsh
```

### <a name="uninstalling-binary-archives"></a>İkili arşivleri kaldırma

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a>Yollar

* `$PSHOME`eklenir`/opt/microsoft/powershell/6.2.0/`
* Kullanıcı profilleri şuradan okunacaktır`~/.config/powershell/profile.ps1`
* Varsayılan profiller buradan okunacaktır`$PSHOME/profile.ps1`
* Kullanıcı modülleri okunacaktır`~/.local/share/powershell/Modules`
* Paylaşılan modüller buradan okunacaktır`/usr/local/share/powershell/Modules`
* Varsayılan modüller okunacaktır`$PSHOME/Modules`
* PSReadline geçmişi şu şekilde kaydedilecek`~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

Profiller, PowerShell 'in konak başına yapılandırmasını kabul eder; bu nedenle, varsayılan konağa özgü profiller aynı konumlarda `Microsoft.PowerShell_profile.ps1` bulunur.

PowerShell, Linux üzerinde [xdg taban dizini belirtimine][xdg-bds] uyar.

[yayınları]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
