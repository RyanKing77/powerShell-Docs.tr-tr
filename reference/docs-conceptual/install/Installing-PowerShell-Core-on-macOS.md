---
title: MacOS’ta PowerShell Core yükleme
description: Macos'ta PowerShell Core yükleme hakkında bilgi
ms.date: 12/12/2018
ms.openlocfilehash: 7db8ca0cb6d13db8ce7f11b4a4b03b7d3f9b6feb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086468"
---
# <a name="installing-powershell-core-on-macos"></a>MacOS’ta PowerShell Core yükleme

PowerShell Core macOS 10.12 ve üstünü destekler.
Tüm paketleri bizim Github'da kullanılabilir [Yayınları][] sayfası.
Paket yüklendikten sonra çalıştırın `pwsh` bir terminalden.

## <a name="about-brew"></a>Brew hakkında

[Homebrew] [ brew] macOS için tercih edilen bir paket yöneticisidir.
Varsa `brew` komutu bulunamazsa, Homebrew aşağıdakileri yüklemeniz gerekir [kendi yönergeleri][brew].

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a>Homebrew aracılığıyla en son kararlı sürüm MacOS 10.12 veya üzeri yüklemesi

Bkz: [hakkında Brew](#about-brew) Brew hakkında bilgi için.

Şimdi, PowerShell'i yükleyebilirsiniz:

```sh
brew cask install powershell
```

Son olarak, yükleme işleminiz düzgün çalıştığını doğrulayın:

```sh
pwsh
```

PowerShell'in yeni sürümü yayımlandığında, Homebrew'ın formüllerini güncelleştirin ve PowerShell yükseltme:

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> Yukarıdaki komutlar içindeki bir PowerShell (pwsh) ana çağrılabilir, ancak daha sonra PowerShell Kabuk çıkıldı ve gereken yükseltmesini tamamladıktan sonra gösterilen değerleri yenileme için bilgisayarınızın yeniden başlatılması `$PSVersionTable`.

[brew]: http://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a>En son Önizleme yüklenmesini Homebrew macOS 10.12 ya da daha yüksek sürüm

Bkz: [hakkında Brew](#about-brew) Brew hakkında bilgi için.

Homebrew yükledikten sonra PowerShell'i yükleyebilirsiniz.
İlk olarak, yükleme [Cask sürümleri] [ cask-versions] cask paketlerin diğer sürümlerini yüklemenize olanak sağlayan paket:

```sh
brew tap homebrew/cask-versions
```

Şimdi, PowerShell'i yükleyebilirsiniz:

```sh
brew cask install powershell-preview
```

Son olarak, yükleme işleminiz düzgün çalıştığını doğrulayın:

```sh
pwsh-preview
```

PowerShell'in yeni sürümü yayımlandığında, Homebrew'ın formüllerini güncelleştirin ve PowerShell yükseltme:

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> Yukarıdaki komutlar içindeki bir PowerShell (pwsh) ana çağrılabilir, ancak daha sonra PowerShell Kabuk çıkıldı ve gerekir yükseltmeyi tamamlamak için bilgisayarınızın yeniden başlatılması.
> ve gösterilen değerleri yenileme `$PSVersionTable`.

## <a name="installation-via-direct-download"></a>Doğrudan indirme ile yükleme

PKG paketini indirme `powershell-6.2.0-osx-x64.pkg`
gelen [Yayınları][] macOS makinenizde sayfaya.

Dosyaya çift tıklayın ve yönergeleri izleyin veya terminalden yükleyin:

```sh
sudo installer -pkg powershell-6.2.0-osx-x64.pkg -target /
```

Yükleme [OpenSSL](#install-openssl). OpenSSL PowerShell uzaktan iletişim ve CIM işlemleri için gereklidir.

## <a name="binary-archives"></a>İkili Arşivi

PowerShell ikili `tar.gz` arşivleri gelişmiş dağıtım senaryoları etkinleştirmek macOS platformu için sağlanır.

### <a name="installing-binary-archives-on-macos"></a>Macos'ta yükleme ikili Arşivi

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.2.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.2.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.2.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.2.0/pwsh /usr/local/bin/pwsh
```

Yükleme [OpenSSL](#install-openssl). OpenSSL PowerShell uzaktan iletişim ve CIM işlemleri için gereklidir.

## <a name="installing-dependencies"></a>Bağımlılıklar yükleniyor

### <a name="install-xcode-command-line-tools"></a>XCode komut satırı araçlarını yükleme

```sh
xcode-select --install
```

### <a name="install-openssl"></a>OpenSSL yükleyin

OpenSSL PowerShell uzaktan iletişim ve CIM işlemleri için gereklidir. Yükleyebileceğiniz MacPorts veya Brew aracılığıyla.

#### <a name="install-openssl-via-brew"></a>OpenSSL Brew aracılığıyla yükleme

Bkz: [hakkında Brew](#about-brew) Brew hakkında bilgi için.

OpenSSL yüklemek için çalıştırın `brew install openssl`.

#### <a name="install-openssl-via-macports"></a>OpenSSL MacPorts aracılığıyla yükleme

1. Yükleme [XCode komut satırı araçları](#install-xcode-command-line-tools).
1. MacPorts yükleyin.
   Yönergelere ihtiyacınız varsa, başvurmak [Yükleme Kılavuzu](https://guide.macports.org/chunked/installing.macports.html).
1. Çalıştırarak MacPorts güncelleştirme `sudo port selfupdate`.
1. MacPorts paketleri çalıştırarak yükseltme `sudo port upgrade outdated`.
1. OpenSSL çalıştırarak yükleyin `sudo port install openssl`.
1. PowerShell için kullanılabilir hale getirmek kitaplıkları Bağla:

```sh
sudo mkdir -p /usr/local/opt/openssl
sudo ln -s /opt/local/lib /usr/local/opt/openssl/lib
```

## <a name="uninstalling-powershell-core"></a>PowerShell Core kaldırma

PowerShell ile Homebrew yüklü değilse, kaldırmak için aşağıdaki komutu kullanın:

```sh
brew cask uninstall powershell
```

PowerShell doğrudan indirme yüklü değilse, PowerShell el ile kaldırılması gerekir:

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

Ek PowerShell yolları kaldırmak için başvurmak [yolları](#paths) bölümü bu belgede ve kullanma yolları Kaldır `sudo rm`.

> [!NOTE]
> Bu, Homebrew ile yüklediyseniz gerekli değildir.

## <a name="paths"></a>Yollar

* `$PSHOME` olduğu `/usr/local/microsoft/powershell/6.2.0/`
* Kullanıcı profillerini okuyabilir `~/.config/powershell/profile.ps1`
* Varsayılan profiller okuyabilir `$PSHOME/profile.ps1`
* Kullanıcı modülleri okuyabilir `~/.local/share/powershell/Modules`
* Paylaşılan modülleri okuyabilir `/usr/local/share/powershell/Modules`
* Varsayılan modülleri okuyabilir `$PSHOME/Modules`
* PSReadline geçmişi için kaydedilir `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

PowerShell'in konak başına yapılandırma profilleri uyar.
Varsayılan konak özel profil var. Bu nedenle `Microsoft.PowerShell_profile.ps1` aynı konumlarda.

PowerShell uyar [XDG temel dizin belirtimi] [ xdg-bds] macOS üzerinde.

MacOS bir türevi BSD, ön ek olduğundan `/usr/local` yerine kullanılan `/opt`.
Bu nedenle, `$PSHOME` olduğu `/usr/local/microsoft/powershell/6.2.0/`, ve sembolik bağlantısını yerleştirilmiş olması `/usr/local/bin/pwsh`.

## <a name="additional-resources"></a>Ek Kaynaklar

* [Homebrew Web][brew]
* [Homebrew Github deposu][GitHub]
* [Homebrew Cask][cask]

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[Yayınları]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
