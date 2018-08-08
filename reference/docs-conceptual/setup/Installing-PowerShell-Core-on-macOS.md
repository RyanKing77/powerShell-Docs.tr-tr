---
title: MacOS’ta PowerShell Core yükleme
description: Macos'ta PowerShell Core yükleme hakkında bilgi
ms.date: 08/06/2018
ms.openlocfilehash: ff1814d95b3ca3fa8497069dff249fd2ad5576ef
ms.sourcegitcommit: 01ac77cd0b00e4e5e964504563a9212e8002e5e0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/07/2018
ms.locfileid: "39587474"
---
# <a name="installing-powershell-core-on-macos"></a>MacOS’ta PowerShell Core yükleme

PowerShell Core macOS 10.12 ve üstünü destekler.
Tüm paketleri bizim Github'da kullanılabilir [sürümleri][] sayfası.
Paket yüklendikten sonra Çalıştır `pwsh` bir terminalden.

### <a name="installation-via-homebrew-on-macos-1012"></a>MacOS 10.12 + üzerinde Homebrew ile yükleme

[Homebrew] [ brew] macOS için tercih edilen bir paket yöneticisidir.
Bir terminal penceresinde `brew` Homebrew çalıştırılacak.  Varsa `brew` komutu bulunamazsa, Homebrew aşağıdakileri yüklemeniz gerekir [kendi yönergeleri][brew].

> [!NOTE]
> Geçmişte Homebrew yüklü değilse, bu her zaman 'güncelleştirme sıfırlama brew' çalıştırmak için iyi bir fikirdir & & 'güncelleştirme brew'.
```sh
brew update-reset
brew update
```

> Homebrew eski sürümlerini dokunun 'caskroom/kullanım dışı, ve 'homebrew/cask' geçirilen cask', kullanılan.  Daha fazla bilgi şu adreste bulunabilir: [Homebrew cask][cask]. Geçerli, Tap'ları listelemek için 'brew dokunun' komutunu kullanın.  ' Caskroom/cask' görürseniz 'güncelleştirme brew' kullanabilirsiniz geçişi dokunma Homebrew sağlamak için.

```sh
brew tap
brew update
```

PowerShell'i yükleme yüklü/Homebrew güncel sonra kolaydır.

PowerShell'i yüklemek için:

```sh
brew cask install powershell
```

Son olarak, yükleme işleminiz düzgün çalıştığını doğrulayın:

```sh
pwsh
```

PowerShell betiğinden çıkın ve bash geri dönmek için 'Çık' komutunu kullanın.
```sh
exit
```

PowerShell'in yeni sürümü yayımlandığında, yalnızca formüllerini Homebrew'ın güncelleştirin ve PowerShell yükseltme:

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> Yukarıdaki komutlar içindeki bir PowerShell (pwsh) ana çağrılabilir, ancak daha sonra PowerShell Kabuk çıkıldı ve gereken $PSVersionTable içinde gösterilen değerleri yenileyin ve yükseltmeyi tamamlamak için bilgisayarınızın yeniden başlatılması.

### <a name="installing-preview-via-homebrew-on-macos-1012"></a>MacOS üzerinde 10.12 + Önizleme Homebrew ile yükleme

[Homebrew] [ brew] macOS için tercih edilen bir paket yöneticisidir.
Bir terminal penceresinde `brew` Homebrew çalıştırılacak.  Varsa `brew` komutu bulunamazsa, Homebrew aşağıdakileri yüklemeniz gerekir [kendi yönergeleri][brew].

> [!NOTE]
> Geçmişte Homebrew yüklü değilse, bu her zaman 'güncelleştirme sıfırlama brew' çalıştırmak için iyi bir fikirdir & & 'güncelleştirme brew'.
```sh
brew update-reset
brew update
```

Ardından, dokunması gerekir `versions` casks Depo önizleme paketini almak için:

```sh
brew tap homebrew/cask-versions
```

PowerShell Önizleme yüklemek için:

```sh
brew cask install powershell-preview
```

Son olarak, yükleme işleminiz düzgün çalıştığını doğrulayın:

```sh
pwsh-preview
```

PowerShell'in yeni sürümü yayımlandığında, yalnızca formüllerini Homebrew'ın güncelleştirin ve PowerShell Önizleme yükseltme:

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> Yukarıdaki komutlar içindeki bir PowerShell (pwsh) ana çağrılabilir, ancak daha sonra PowerShell Kabuk çıkıldı ve gereken $PSVersionTable içinde gösterilen değerleri yenileyin ve yükseltmeyi tamamlamak için bilgisayarınızın yeniden başlatılması.

### <a name="installation-via-direct-download"></a>Doğrudan indirme ile yükleme

PKG paketini indirme `powershell-6.0.2-osx.10.12-x64.pkg` gelen [sürümleri][] macOS makinenizde sayfaya.

Dosyaya çift tıklayın ve yönergeleri izleyin veya terminalden yükleyin:

```sh
sudo installer -pkg powershell-6.0.2-osx.10.12-x64.pkg -target /
```

## <a name="binary-archives"></a>İkili Arşivi

PowerShell ikili `tar.gz` arşivleri, macOS ve Linux platformlarında gelişmiş dağıtım senaryoları etkinleştirmek için sağlanır.

### <a name="installing-binary-archives-on-macos"></a>Macos'ta yükleme ikili Arşivi

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

* `$PSHOME` olduğu `/usr/local/microsoft/powershell/6.0.2/`
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
Bu nedenle, `$PSHOME` olduğu `/usr/local/microsoft/powershell/6.0.2/`, ve sembolik bağlantısını yerleştirilmiş olması `/usr/local/bin/pwsh`.

## <a name="additional-resources"></a>Ek Kaynaklar

* [Homebrew Web][brew]
* [Homebrew Github deposu][GitHub]
* [Homebrew Cask][cask]


[brew]: http://brew.sh/
[GitHub]: https://github.com/Homebrew
[Cask]: https://github.com/Homebrew/homebrew-cask
[sürümleri]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
