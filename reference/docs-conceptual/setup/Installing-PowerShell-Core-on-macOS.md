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
# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="6d0a6-103">MacOS’ta PowerShell Core yükleme</span><span class="sxs-lookup"><span data-stu-id="6d0a6-103">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="6d0a6-104">PowerShell Core macOS 10.12 ve üstünü destekler.</span><span class="sxs-lookup"><span data-stu-id="6d0a6-104">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="6d0a6-105">Tüm paketleri bizim Github'da kullanılabilir [sürümleri][] sayfası.</span><span class="sxs-lookup"><span data-stu-id="6d0a6-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="6d0a6-106">Paket yüklendikten sonra Çalıştır `pwsh` bir terminalden.</span><span class="sxs-lookup"><span data-stu-id="6d0a6-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

### <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="6d0a6-107">En son Önizleme yüklenmesini Homebrew macOS 10.12 ya da daha yüksek sürüm</span><span class="sxs-lookup"><span data-stu-id="6d0a6-107">Installation of latest preview release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="6d0a6-108">[Homebrew] [ brew] macOS için tercih edilen bir paket yöneticisidir.</span><span class="sxs-lookup"><span data-stu-id="6d0a6-108">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="6d0a6-109">Varsa `brew` komutu bulunamazsa, Homebrew aşağıdakileri yüklemeniz gerekir [kendi yönergeleri][brew].</span><span class="sxs-lookup"><span data-stu-id="6d0a6-109">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

<span data-ttu-id="6d0a6-110">Homebrew yükledikten sonra PowerShell'i yükleme kolaydır.</span><span class="sxs-lookup"><span data-stu-id="6d0a6-110">Once you've installed Homebrew, installing PowerShell is easy.</span></span>
<span data-ttu-id="6d0a6-111">İlk olarak, yükleme [Homebrew Cask][cask], daha fazla paketleri yükleyebilirsiniz ve sağlayan yükleme [Cask-sürüm] [cask-sürüm] paketlerin diğer sürümlerini yüklemek için:</span><span class="sxs-lookup"><span data-stu-id="6d0a6-111">First, install [Homebrew-Cask][cask], so you can install more packages and install [Cask-Versions][cask-version] which lets you install alternative versions of packages:</span></span>

```sh
brew tap caskroom/cask
brew tap caskroom/versions
```

<span data-ttu-id="6d0a6-112">Şimdi, PowerShell'i yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6d0a6-112">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="6d0a6-113">Son olarak, yükleme işleminiz düzgün çalıştığını doğrulayın:</span><span class="sxs-lookup"><span data-stu-id="6d0a6-113">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="6d0a6-114">PowerShell'in yeni sürümü yayımlandığında, yalnızca formüllerini Homebrew'ın güncelleştirin ve PowerShell yükseltme:</span><span class="sxs-lookup"><span data-stu-id="6d0a6-114">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="6d0a6-115">Yukarıdaki komutlar içindeki bir PowerShell (pwsh) ana çağrılabilir, ancak daha sonra PowerShell Kabuk çıkıldı ve gerekir yükseltmeyi tamamlamak için bilgisayarınızın yeniden başlatılması.</span><span class="sxs-lookup"><span data-stu-id="6d0a6-115">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="6d0a6-116">ve $PSVersionTable içinde gösterilen değerleri yenileyin.</span><span class="sxs-lookup"><span data-stu-id="6d0a6-116">and refresh the values shown in $PSVersionTable.</span></span>

[brew]: http://brew.sh/
[cask]: https://caskroom.github.io/
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions

### <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="6d0a6-117">En son Önizleme yüklenmesini Homebrew macOS 10.12 ya da daha yüksek sürüm</span><span class="sxs-lookup"><span data-stu-id="6d0a6-117">Installation of latest preview release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="6d0a6-118">[Homebrew] [ brew] macOS için tercih edilen bir paket yöneticisidir.</span><span class="sxs-lookup"><span data-stu-id="6d0a6-118">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="6d0a6-119">Varsa `brew` komutu bulunamazsa, Homebrew aşağıdakileri yüklemeniz gerekir [kendi yönergeleri][brew].</span><span class="sxs-lookup"><span data-stu-id="6d0a6-119">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

<span data-ttu-id="6d0a6-120">Homebrew yükledikten sonra PowerShell'i yükleme kolaydır.</span><span class="sxs-lookup"><span data-stu-id="6d0a6-120">Once you've installed Homebrew, installing PowerShell is easy.</span></span>
<span data-ttu-id="6d0a6-121">İlk olarak, yükleme [Homebrew Cask][cask], daha fazla paketleri yükleyebilirsiniz ve sağlayan yükleme [Cask-sürüm] [cask-sürüm] paketlerin diğer sürümlerini yüklemek için:</span><span class="sxs-lookup"><span data-stu-id="6d0a6-121">First, install [Homebrew-Cask][cask], so you can install more packages and install [Cask-Versions][cask-version] which lets you install alternative versions of packages:</span></span>

```sh
brew tap caskroom/cask
brew tap caskroom/versions
```

<span data-ttu-id="6d0a6-122">Şimdi, PowerShell'i yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6d0a6-122">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="6d0a6-123">Son olarak, yükleme işleminiz düzgün çalıştığını doğrulayın:</span><span class="sxs-lookup"><span data-stu-id="6d0a6-123">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="6d0a6-124">PowerShell'in yeni sürümü yayımlandığında, yalnızca formüllerini Homebrew'ın güncelleştirin ve PowerShell yükseltme:</span><span class="sxs-lookup"><span data-stu-id="6d0a6-124">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="6d0a6-125">Yukarıdaki komutlar içindeki bir PowerShell (pwsh) ana çağrılabilir, ancak daha sonra PowerShell Kabuk çıkıldı ve gerekir yükseltmeyi tamamlamak için bilgisayarınızın yeniden başlatılması.</span><span class="sxs-lookup"><span data-stu-id="6d0a6-125">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="6d0a6-126">ve $PSVersionTable içinde gösterilen değerleri yenileyin.</span><span class="sxs-lookup"><span data-stu-id="6d0a6-126">and refresh the values shown in $PSVersionTable.</span></span>

[brew]: http://brew.sh/
[cask]: https://caskroom.github.io/
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions

### <a name="installation-via-direct-download"></a><span data-ttu-id="6d0a6-127">Doğrudan indirme ile yükleme</span><span class="sxs-lookup"><span data-stu-id="6d0a6-127">Installation via Direct Download</span></span>

<span data-ttu-id="6d0a6-128">PKG paketini indirme `powershell-6.1.0-osx-x64.pkg`</span><span class="sxs-lookup"><span data-stu-id="6d0a6-128">Download the PKG package `powershell-6.1.0-osx-x64.pkg`</span></span>
<span data-ttu-id="6d0a6-129">gelen [sürümleri][] macOS makinenizde sayfaya.</span><span class="sxs-lookup"><span data-stu-id="6d0a6-129">from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="6d0a6-130">Dosyaya çift tıklayın ve yönergeleri izleyin veya terminalden yükleyin:</span><span class="sxs-lookup"><span data-stu-id="6d0a6-130">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.1.0-osx-x64.pkg -target /
```

## <a name="binary-archives"></a><span data-ttu-id="6d0a6-131">İkili Arşivi</span><span class="sxs-lookup"><span data-stu-id="6d0a6-131">Binary Archives</span></span>

<span data-ttu-id="6d0a6-132">PowerShell ikili `tar.gz` arşivleri, macOS ve Linux platformlarında gelişmiş dağıtım senaryoları etkinleştirmek için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="6d0a6-132">PowerShell binary `tar.gz` archives are provided for macOS and Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="6d0a6-133">Macos'ta yükleme ikili Arşivi</span><span class="sxs-lookup"><span data-stu-id="6d0a6-133">Installing binary archives on macOS</span></span>

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

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="6d0a6-134">PowerShell Core kaldırma</span><span class="sxs-lookup"><span data-stu-id="6d0a6-134">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="6d0a6-135">PowerShell ile Homebrew yüklü değilse, kaldırma kolaydır:</span><span class="sxs-lookup"><span data-stu-id="6d0a6-135">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="6d0a6-136">PowerShell doğrudan indirme yüklü değilse, PowerShell el ile kaldırılması gerekir:</span><span class="sxs-lookup"><span data-stu-id="6d0a6-136">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="6d0a6-137">Ek PowerShell yolları kaldırmak için lütfen bkz [yolları][] bölümü bu belgede ve istenen kullanarak yollarını kaldırma `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="6d0a6-137">To remove the additional PowerShell paths, please see the [paths][] section in this document and remove the desired the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="6d0a6-138">Bu, Homebrew ile yüklediyseniz gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="6d0a6-138">This is not necessary if you installed with Homebrew.</span></span>

[Yolları]:#paths
[paths]:#paths

## <a name="paths"></a><span data-ttu-id="6d0a6-140">Yollar</span><span class="sxs-lookup"><span data-stu-id="6d0a6-140">Paths</span></span>

* <span data-ttu-id="6d0a6-141">`$PSHOME` olduğu `/usr/local/microsoft/powershell/6.1.0/`</span><span class="sxs-lookup"><span data-stu-id="6d0a6-141">`$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`</span></span>
* <span data-ttu-id="6d0a6-142">Kullanıcı profillerini okuyabilir `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="6d0a6-142">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="6d0a6-143">Varsayılan profiller okuyabilir `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="6d0a6-143">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="6d0a6-144">Kullanıcı modülleri okuyabilir `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="6d0a6-144">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="6d0a6-145">Paylaşılan modülleri okuyabilir `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="6d0a6-145">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="6d0a6-146">Varsayılan modülleri okuyabilir `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="6d0a6-146">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="6d0a6-147">PSReadline geçmişi için kaydedilir `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="6d0a6-147">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="6d0a6-148">PowerShell'in konak başına yapılandırma profilleri uyar.</span><span class="sxs-lookup"><span data-stu-id="6d0a6-148">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="6d0a6-149">Varsayılan konak özel profilleri var Bu nedenle `Microsoft.PowerShell_profile.ps1` aynı konumlarda.</span><span class="sxs-lookup"><span data-stu-id="6d0a6-149">So the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="6d0a6-150">PowerShell uyar [XDG temel dizin belirtimi] [ xdg-bds] macOS üzerinde.</span><span class="sxs-lookup"><span data-stu-id="6d0a6-150">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="6d0a6-151">MacOS bir türevi BSD, ön ek olduğundan `/usr/local` yerine kullanılan `/opt`.</span><span class="sxs-lookup"><span data-stu-id="6d0a6-151">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="6d0a6-152">Bu nedenle, `$PSHOME` olduğu `/usr/local/microsoft/powershell/6.1.0/`, ve sembolik bağlantısını yerleştirilmiş olması `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="6d0a6-152">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`, and the symlink is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="6d0a6-153">Ek Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="6d0a6-153">Additional Resources</span></span>

* <span data-ttu-id="6d0a6-154">[Homebrew Web][brew]</span><span class="sxs-lookup"><span data-stu-id="6d0a6-154">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="6d0a6-155">[Homebrew Github deposu][GitHub]</span><span class="sxs-lookup"><span data-stu-id="6d0a6-155">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="6d0a6-156">[Homebrew Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="6d0a6-156">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[GitHub]: https://github.com/Homebrew
[Cask]: https://github.com/Homebrew/homebrew-cask
[sürümleri]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
