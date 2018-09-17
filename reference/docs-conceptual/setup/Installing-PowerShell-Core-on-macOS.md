---
title: MacOS’ta PowerShell Core yükleme
description: Macos'ta PowerShell Core yükleme hakkında bilgi
ms.date: 08/06/2018
ms.openlocfilehash: 042c933dfa83f3ab52e315036e4f817145116d00
ms.sourcegitcommit: aa41249f153bbc6e11667ade60c878980c15abc6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45611496"
---
# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="8fb67-103">MacOS’ta PowerShell Core yükleme</span><span class="sxs-lookup"><span data-stu-id="8fb67-103">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="8fb67-104">PowerShell Core macOS 10.12 ve üstünü destekler.</span><span class="sxs-lookup"><span data-stu-id="8fb67-104">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="8fb67-105">Tüm paketleri bizim Github'da kullanılabilir [sürümleri][] sayfası.</span><span class="sxs-lookup"><span data-stu-id="8fb67-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="8fb67-106">Paket yüklendikten sonra Çalıştır `pwsh` bir terminalden.</span><span class="sxs-lookup"><span data-stu-id="8fb67-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="8fb67-107">Homebrew aracılığıyla en son kararlı sürüm MacOS 10.12 veya üzeri yüklemesi</span><span class="sxs-lookup"><span data-stu-id="8fb67-107">Installation of latest stable release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="8fb67-108">[Homebrew] [ brew] macOS için tercih edilen bir paket yöneticisidir.</span><span class="sxs-lookup"><span data-stu-id="8fb67-108">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="8fb67-109">Varsa `brew` komutu bulunamazsa, Homebrew aşağıdakileri yüklemeniz gerekir [kendi yönergeleri][brew].</span><span class="sxs-lookup"><span data-stu-id="8fb67-109">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

<span data-ttu-id="8fb67-110">Şimdi, PowerShell'i yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8fb67-110">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="8fb67-111">Son olarak, yükleme işleminiz düzgün çalıştığını doğrulayın:</span><span class="sxs-lookup"><span data-stu-id="8fb67-111">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="8fb67-112">PowerShell'in yeni sürümü yayımlandığında, yalnızca formüllerini Homebrew'ın güncelleştirin ve PowerShell yükseltme:</span><span class="sxs-lookup"><span data-stu-id="8fb67-112">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="8fb67-113">Yukarıdaki komutlar içindeki bir PowerShell (pwsh) ana çağrılabilir, ancak daha sonra PowerShell Kabuk çıkıldı ve gerekir yükseltmeyi tamamlamak için bilgisayarınızın yeniden başlatılması.</span><span class="sxs-lookup"><span data-stu-id="8fb67-113">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="8fb67-114">ve $PSVersionTable içinde gösterilen değerleri yenileyin.</span><span class="sxs-lookup"><span data-stu-id="8fb67-114">and refresh the values shown in $PSVersionTable.</span></span>

[brew]: http://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="8fb67-115">En son Önizleme yüklenmesini Homebrew macOS 10.12 ya da daha yüksek sürüm</span><span class="sxs-lookup"><span data-stu-id="8fb67-115">Installation of latest preview release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="8fb67-116">[Homebrew] [ brew] macOS için tercih edilen bir paket yöneticisidir.</span><span class="sxs-lookup"><span data-stu-id="8fb67-116">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="8fb67-117">Varsa `brew` komutu bulunamazsa, Homebrew aşağıdakileri yüklemeniz gerekir [kendi yönergeleri][brew].</span><span class="sxs-lookup"><span data-stu-id="8fb67-117">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

<span data-ttu-id="8fb67-118">Homebrew yükledikten sonra PowerShell'i yükleme kolaydır.</span><span class="sxs-lookup"><span data-stu-id="8fb67-118">Once you've installed Homebrew, installing PowerShell is easy.</span></span>
<span data-ttu-id="8fb67-119">İlk olarak, yükleme [Cask sürümleri] [ cask-versions] olanak sağlayan diğer sürümlerini cask paketleri yükleyin:</span><span class="sxs-lookup"><span data-stu-id="8fb67-119">First, install [Cask-Versions][cask-versions] which lets you install alternative versions of cask packages:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="8fb67-120">Şimdi, PowerShell'i yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8fb67-120">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="8fb67-121">Son olarak, yükleme işleminiz düzgün çalıştığını doğrulayın:</span><span class="sxs-lookup"><span data-stu-id="8fb67-121">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="8fb67-122">PowerShell'in yeni sürümü yayımlandığında, yalnızca formüllerini Homebrew'ın güncelleştirin ve PowerShell yükseltme:</span><span class="sxs-lookup"><span data-stu-id="8fb67-122">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="8fb67-123">Yukarıdaki komutlar içindeki bir PowerShell (pwsh) ana çağrılabilir, ancak daha sonra PowerShell Kabuk çıkıldı ve gerekir yükseltmeyi tamamlamak için bilgisayarınızın yeniden başlatılması.</span><span class="sxs-lookup"><span data-stu-id="8fb67-123">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="8fb67-124">ve $PSVersionTable içinde gösterilen değerleri yenileyin.</span><span class="sxs-lookup"><span data-stu-id="8fb67-124">and refresh the values shown in $PSVersionTable.</span></span>

## <a name="installation-via-direct-download"></a><span data-ttu-id="8fb67-125">Doğrudan indirme ile yükleme</span><span class="sxs-lookup"><span data-stu-id="8fb67-125">Installation via Direct Download</span></span>

<span data-ttu-id="8fb67-126">PKG paketini indirme `powershell-6.1.0-osx-x64.pkg`</span><span class="sxs-lookup"><span data-stu-id="8fb67-126">Download the PKG package `powershell-6.1.0-osx-x64.pkg`</span></span>
<span data-ttu-id="8fb67-127">gelen [sürümleri][] macOS makinenizde sayfaya.</span><span class="sxs-lookup"><span data-stu-id="8fb67-127">from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="8fb67-128">Dosyaya çift tıklayın ve yönergeleri izleyin veya terminalden yükleyin:</span><span class="sxs-lookup"><span data-stu-id="8fb67-128">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.1.0-osx-x64.pkg -target /
```

## <a name="binary-archives"></a><span data-ttu-id="8fb67-129">İkili Arşivi</span><span class="sxs-lookup"><span data-stu-id="8fb67-129">Binary Archives</span></span>

<span data-ttu-id="8fb67-130">PowerShell ikili `tar.gz` arşivleri gelişmiş dağıtım senaryoları etkinleştirmek macOS platformu için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="8fb67-130">PowerShell binary `tar.gz` archives are provided for the macOS platform to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="8fb67-131">Macos'ta yükleme ikili Arşivi</span><span class="sxs-lookup"><span data-stu-id="8fb67-131">Installing binary archives on macOS</span></span>

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

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="8fb67-132">PowerShell Core kaldırma</span><span class="sxs-lookup"><span data-stu-id="8fb67-132">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="8fb67-133">PowerShell ile Homebrew yüklü değilse, kaldırma kolaydır:</span><span class="sxs-lookup"><span data-stu-id="8fb67-133">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="8fb67-134">PowerShell doğrudan indirme yüklü değilse, PowerShell el ile kaldırılması gerekir:</span><span class="sxs-lookup"><span data-stu-id="8fb67-134">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="8fb67-135">Ek PowerShell yolları kaldırmak için lütfen bkz [yolları](#paths) bölümü bu belgede ve istenen kullanarak yollarını kaldırma `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="8fb67-135">To remove the additional PowerShell paths, please see the [paths](#paths) section in this document and remove the desired the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="8fb67-136">Bu, Homebrew ile yüklediyseniz gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="8fb67-136">This is not necessary if you installed with Homebrew.</span></span>

## <a name="paths"></a><span data-ttu-id="8fb67-137">Yollar</span><span class="sxs-lookup"><span data-stu-id="8fb67-137">Paths</span></span>

* <span data-ttu-id="8fb67-138">`$PSHOME` olduğu `/usr/local/microsoft/powershell/6.1.0/`</span><span class="sxs-lookup"><span data-stu-id="8fb67-138">`$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`</span></span>
* <span data-ttu-id="8fb67-139">Kullanıcı profillerini okuyabilir `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="8fb67-139">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="8fb67-140">Varsayılan profiller okuyabilir `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="8fb67-140">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="8fb67-141">Kullanıcı modülleri okuyabilir `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="8fb67-141">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="8fb67-142">Paylaşılan modülleri okuyabilir `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="8fb67-142">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="8fb67-143">Varsayılan modülleri okuyabilir `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="8fb67-143">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="8fb67-144">PSReadline geçmişi için kaydedilir `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="8fb67-144">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="8fb67-145">PowerShell'in konak başına yapılandırma profilleri uyar.</span><span class="sxs-lookup"><span data-stu-id="8fb67-145">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="8fb67-146">Varsayılan konak özel profilleri var Bu nedenle `Microsoft.PowerShell_profile.ps1` aynı konumlarda.</span><span class="sxs-lookup"><span data-stu-id="8fb67-146">So the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="8fb67-147">PowerShell uyar [XDG temel dizin belirtimi] [ xdg-bds] macOS üzerinde.</span><span class="sxs-lookup"><span data-stu-id="8fb67-147">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="8fb67-148">MacOS bir türevi BSD, ön ek olduğundan `/usr/local` yerine kullanılan `/opt`.</span><span class="sxs-lookup"><span data-stu-id="8fb67-148">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="8fb67-149">Bu nedenle, `$PSHOME` olduğu `/usr/local/microsoft/powershell/6.1.0/`, ve sembolik bağlantısını yerleştirilmiş olması `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="8fb67-149">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`, and the symlink is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="8fb67-150">Ek Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="8fb67-150">Additional Resources</span></span>

* <span data-ttu-id="8fb67-151">[Homebrew Web][brew]</span><span class="sxs-lookup"><span data-stu-id="8fb67-151">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="8fb67-152">[Homebrew Github deposu][GitHub]</span><span class="sxs-lookup"><span data-stu-id="8fb67-152">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="8fb67-153">[Homebrew Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="8fb67-153">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[sürümleri]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
