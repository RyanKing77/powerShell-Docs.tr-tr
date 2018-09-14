---
title: MacOS’ta PowerShell Core yükleme
description: Macos'ta PowerShell Core yükleme hakkında bilgi
ms.date: 08/06/2018
ms.openlocfilehash: 50b8dbbf26f02580e4be45978c926d5337da6b63
ms.sourcegitcommit: b235c58b34d23317076540631f5cf83f1f309c0d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45557169"
---
# <a name="installing-powershell-core-on-macos"></a>MacOS’ta PowerShell Core yükleme

PowerShell Core macOS 10.12 ve üstünü destekler.
Tüm paketleri bizim Github'da kullanılabilir [sürümleri][] sayfası.
Paket yüklendikten sonra Çalıştır `pwsh` bir terminalden.

### <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a>En son Önizleme yüklenmesini Homebrew macOS 10.12 ya da daha yüksek sürüm

[Homebrew] [ brew] macOS için tercih edilen bir paket yöneticisidir.
Varsa `brew` komutu bulunamazsa, Homebrew aşağıdakileri yüklemeniz gerekir [kendi yönergeleri][brew].

Homebrew yükledikten sonra PowerShell'i yükleme kolaydır.
İlk olarak, yükleme [Homebrew Cask][cask], daha fazla paketleri yükleyebilirsiniz ve sağlayan yükleme [Cask-sürüm] [cask-sürüm] paketlerin diğer sürümlerini yüklemek için:

```sh
brew tap caskroom/cask
brew tap caskroom/versions
```

Şimdi, PowerShell'i yükleyebilirsiniz:

```sh
brew cask install powershell-preview
```

Son olarak, yükleme işleminiz düzgün çalıştığını doğrulayın:

```sh
pwsh-preview
```

PowerShell'in yeni sürümü yayımlandığında, yalnızca formüllerini Homebrew'ın güncelleştirin ve PowerShell yükseltme:

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> Yukarıdaki komutlar içindeki bir PowerShell (pwsh) ana çağrılabilir, ancak daha sonra PowerShell Kabuk çıkıldı ve gerekir yükseltmeyi tamamlamak için bilgisayarınızın yeniden başlatılması.
> ve $PSVersionTable içinde gösterilen değerleri yenileyin.

[brew]: http://brew.sh/
[cask]: https://caskroom.github.io/
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions

### <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a>En son Önizleme yüklenmesini Homebrew macOS 10.12 ya da daha yüksek sürüm

[Homebrew] [ brew] macOS için tercih edilen bir paket yöneticisidir.
Varsa `brew` komutu bulunamazsa, Homebrew aşağıdakileri yüklemeniz gerekir [kendi yönergeleri][brew].

Homebrew yükledikten sonra PowerShell'i yükleme kolaydır.
İlk olarak, yükleme [Homebrew Cask][cask], daha fazla paketleri yükleyebilirsiniz ve sağlayan yükleme [Cask-sürüm] [cask-sürüm] paketlerin diğer sürümlerini yüklemek için:

```sh
brew tap caskroom/cask
brew tap caskroom/versions
```

Şimdi, PowerShell'i yükleyebilirsiniz:

```sh
brew cask install powershell-preview
```

Son olarak, yükleme işleminiz düzgün çalıştığını doğrulayın:

```sh
pwsh-preview
```

PowerShell'in yeni sürümü yayımlandığında, yalnızca formüllerini Homebrew'ın güncelleştirin ve PowerShell yükseltme:

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> Yukarıdaki komutlar içindeki bir PowerShell (pwsh) ana çağrılabilir, ancak daha sonra PowerShell Kabuk çıkıldı ve gerekir yükseltmeyi tamamlamak için bilgisayarınızın yeniden başlatılması.
> ve $PSVersionTable içinde gösterilen değerleri yenileyin.

[brew]: http://brew.sh/
[cask]: https://caskroom.github.io/
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions

### <a name="installation-via-direct-download"></a>Doğrudan indirme ile yükleme

PKG paketini indirme `powershell-6.1.0-osx-x64.pkg`
gelen [sürümleri][] macOS makinenizde sayfaya.

Dosyaya çift tıklayın ve yönergeleri izleyin veya terminalden yükleyin:

```sh
sudo installer -pkg powershell-6.1.0-osx-x64.pkg -target /
```

## <a name="binary-archives"></a>İkili Arşivi

PowerShell ikili `tar.gz` arşivleri, macOS ve Linux platformlarında gelişmiş dağıtım senaryoları etkinleştirmek için sağlanır.

### <a name="installing-binary-archives-on-macos"></a>Macos'ta yükleme ikili Arşivi

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.1.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.1.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.1.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.1.0/pwsh /usr/local/bin/pwsh
```

## <a name="uninstalling-powershell-core"></a>PowerShell Core kaldırma

PowerShell ile Homebrew yüklü değilse, kaldırma kolaydır:

```sh
brew cask uninstall powershell
```

PowerShell doğrudan indirme yüklü değilse, PowerShell el ile kaldırılması gerekir:

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

Ek PowerShell yolları kaldırmak için lütfen bkz [yolları][] bölümü bu belgede ve istenen kullanarak yollarını kaldırma `sudo rm`.

> [!NOTE]
> Bu, Homebrew ile yüklediyseniz gerekli değildir.

[Yolları]:#paths

## <a name="paths"></a>Yollar

* `$PSHOME` olduğu `/usr/local/microsoft/powershell/6.1.0/`
* Kullanıcı profillerini okuyabilir `~/.config/powershell/profile.ps1`
* Varsayılan profiller okuyabilir `$PSHOME/profile.ps1`
* Kullanıcı modülleri okuyabilir `~/.local/share/powershell/Modules`
* Paylaşılan modülleri okuyabilir `/usr/local/share/powershell/Modules`
* Varsayılan modülleri okuyabilir `$PSHOME/Modules`
* PSReadline geçmişi için kaydedilir `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

PowerShell'in konak başına yapılandırma profilleri uyar.
Varsayılan konak özel profilleri var Bu nedenle `Microsoft.PowerShell_profile.ps1` aynı konumlarda.

PowerShell uyar [XDG temel dizin belirtimi] [ xdg-bds] macOS üzerinde.

MacOS bir türevi BSD, ön ek olduğundan `/usr/local` yerine kullanılan `/opt`.
Bu nedenle, `$PSHOME` olduğu `/usr/local/microsoft/powershell/6.1.0/`, ve sembolik bağlantısını yerleştirilmiş olması `/usr/local/bin/pwsh`.

## <a name="additional-resources"></a>Ek Kaynaklar

* [Homebrew Web][brew]
* [Homebrew Github deposu][GitHub]
* [Homebrew Cask][cask]

[brew]: http://brew.sh/
[GitHub]: https://github.com/Homebrew
[Cask]: https://github.com/Homebrew/homebrew-cask
[sürümleri]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
