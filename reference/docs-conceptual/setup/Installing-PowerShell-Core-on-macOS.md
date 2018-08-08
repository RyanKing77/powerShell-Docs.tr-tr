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
# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="9f474-103">MacOS’ta PowerShell Core yükleme</span><span class="sxs-lookup"><span data-stu-id="9f474-103">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="9f474-104">PowerShell Core macOS 10.12 ve üstünü destekler.</span><span class="sxs-lookup"><span data-stu-id="9f474-104">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="9f474-105">Tüm paketleri bizim Github'da kullanılabilir [sürümleri][] sayfası.</span><span class="sxs-lookup"><span data-stu-id="9f474-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="9f474-106">Paket yüklendikten sonra Çalıştır `pwsh` bir terminalden.</span><span class="sxs-lookup"><span data-stu-id="9f474-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

### <a name="installation-via-homebrew-on-macos-1012"></a><span data-ttu-id="9f474-107">MacOS 10.12 + üzerinde Homebrew ile yükleme</span><span class="sxs-lookup"><span data-stu-id="9f474-107">Installation via Homebrew on macOS 10.12+</span></span>

<span data-ttu-id="9f474-108">[Homebrew] [ brew] macOS için tercih edilen bir paket yöneticisidir.</span><span class="sxs-lookup"><span data-stu-id="9f474-108">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="9f474-109">Bir terminal penceresinde `brew` Homebrew çalıştırılacak.</span><span class="sxs-lookup"><span data-stu-id="9f474-109">From a terminal window, type `brew` to run Homebrew.</span></span>  <span data-ttu-id="9f474-110">Varsa `brew` komutu bulunamazsa, Homebrew aşağıdakileri yüklemeniz gerekir [kendi yönergeleri][brew].</span><span class="sxs-lookup"><span data-stu-id="9f474-110">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

> [!NOTE]
> <span data-ttu-id="9f474-111">Geçmişte Homebrew yüklü değilse, bu her zaman 'güncelleştirme sıfırlama brew' çalıştırmak için iyi bir fikirdir & & 'güncelleştirme brew'.</span><span class="sxs-lookup"><span data-stu-id="9f474-111">If you installed Homebrew in the past, it's always a good idea to run 'brew update-reset' && 'brew update'.</span></span>
```sh
brew update-reset
brew update
```

> <span data-ttu-id="9f474-112">Homebrew eski sürümlerini dokunun 'caskroom/kullanım dışı, ve 'homebrew/cask' geçirilen cask', kullanılan.</span><span class="sxs-lookup"><span data-stu-id="9f474-112">Older versions of Homebrew used the tap 'caskroom/cask', which has been deprecated, and migrated into 'homebrew/cask'.</span></span>  <span data-ttu-id="9f474-113">Daha fazla bilgi şu adreste bulunabilir: [Homebrew cask][cask].</span><span class="sxs-lookup"><span data-stu-id="9f474-113">More information can be found at [Homebrew-cask][cask].</span></span> <span data-ttu-id="9f474-114">Geçerli, Tap'ları listelemek için 'brew dokunun' komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="9f474-114">Use the 'brew tap' command to list your current taps.</span></span>  <span data-ttu-id="9f474-115">' Caskroom/cask' görürseniz 'güncelleştirme brew' kullanabilirsiniz geçişi dokunma Homebrew sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="9f474-115">If you see 'caskroom/cask' you can use 'brew update' to have Homebrew migrate the taps.</span></span>

```sh
brew tap
brew update
```

<span data-ttu-id="9f474-116">PowerShell'i yükleme yüklü/Homebrew güncel sonra kolaydır.</span><span class="sxs-lookup"><span data-stu-id="9f474-116">Once you've installed/updated Homebrew, installing PowerShell is easy.</span></span>

<span data-ttu-id="9f474-117">PowerShell'i yüklemek için:</span><span class="sxs-lookup"><span data-stu-id="9f474-117">To install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="9f474-118">Son olarak, yükleme işleminiz düzgün çalıştığını doğrulayın:</span><span class="sxs-lookup"><span data-stu-id="9f474-118">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="9f474-119">PowerShell betiğinden çıkın ve bash geri dönmek için 'Çık' komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="9f474-119">To exit PowerShell, and return to bash, use the 'exit' command.</span></span>
```sh
exit
```

<span data-ttu-id="9f474-120">PowerShell'in yeni sürümü yayımlandığında, yalnızca formüllerini Homebrew'ın güncelleştirin ve PowerShell yükseltme:</span><span class="sxs-lookup"><span data-stu-id="9f474-120">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="9f474-121">Yukarıdaki komutlar içindeki bir PowerShell (pwsh) ana çağrılabilir, ancak daha sonra PowerShell Kabuk çıkıldı ve gereken $PSVersionTable içinde gösterilen değerleri yenileyin ve yükseltmeyi tamamlamak için bilgisayarınızın yeniden başlatılması.</span><span class="sxs-lookup"><span data-stu-id="9f474-121">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in $PSVersionTable.</span></span>

### <a name="installing-preview-via-homebrew-on-macos-1012"></a><span data-ttu-id="9f474-122">MacOS üzerinde 10.12 + Önizleme Homebrew ile yükleme</span><span class="sxs-lookup"><span data-stu-id="9f474-122">Installing Preview via Homebrew on macOS 10.12+</span></span>

<span data-ttu-id="9f474-123">[Homebrew] [ brew] macOS için tercih edilen bir paket yöneticisidir.</span><span class="sxs-lookup"><span data-stu-id="9f474-123">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="9f474-124">Bir terminal penceresinde `brew` Homebrew çalıştırılacak.</span><span class="sxs-lookup"><span data-stu-id="9f474-124">From a terminal window, type `brew` to run Homebrew.</span></span>  <span data-ttu-id="9f474-125">Varsa `brew` komutu bulunamazsa, Homebrew aşağıdakileri yüklemeniz gerekir [kendi yönergeleri][brew].</span><span class="sxs-lookup"><span data-stu-id="9f474-125">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

> [!NOTE]
> <span data-ttu-id="9f474-126">Geçmişte Homebrew yüklü değilse, bu her zaman 'güncelleştirme sıfırlama brew' çalıştırmak için iyi bir fikirdir & & 'güncelleştirme brew'.</span><span class="sxs-lookup"><span data-stu-id="9f474-126">If you installed Homebrew in the past, it's always a good idea to run 'brew update-reset' && 'brew update'.</span></span>
```sh
brew update-reset
brew update
```

<span data-ttu-id="9f474-127">Ardından, dokunması gerekir `versions` casks Depo önizleme paketini almak için:</span><span class="sxs-lookup"><span data-stu-id="9f474-127">Then, you must tap the `versions` casks repository to get the preview package:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="9f474-128">PowerShell Önizleme yüklemek için:</span><span class="sxs-lookup"><span data-stu-id="9f474-128">To install PowerShell Preview:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="9f474-129">Son olarak, yükleme işleminiz düzgün çalıştığını doğrulayın:</span><span class="sxs-lookup"><span data-stu-id="9f474-129">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="9f474-130">PowerShell'in yeni sürümü yayımlandığında, yalnızca formüllerini Homebrew'ın güncelleştirin ve PowerShell Önizleme yükseltme:</span><span class="sxs-lookup"><span data-stu-id="9f474-130">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell Preview:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="9f474-131">Yukarıdaki komutlar içindeki bir PowerShell (pwsh) ana çağrılabilir, ancak daha sonra PowerShell Kabuk çıkıldı ve gereken $PSVersionTable içinde gösterilen değerleri yenileyin ve yükseltmeyi tamamlamak için bilgisayarınızın yeniden başlatılması.</span><span class="sxs-lookup"><span data-stu-id="9f474-131">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in $PSVersionTable.</span></span>

### <a name="installation-via-direct-download"></a><span data-ttu-id="9f474-132">Doğrudan indirme ile yükleme</span><span class="sxs-lookup"><span data-stu-id="9f474-132">Installation via Direct Download</span></span>

<span data-ttu-id="9f474-133">PKG paketini indirme `powershell-6.0.2-osx.10.12-x64.pkg` gelen [sürümleri][] macOS makinenizde sayfaya.</span><span class="sxs-lookup"><span data-stu-id="9f474-133">Download the PKG package `powershell-6.0.2-osx.10.12-x64.pkg` from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="9f474-134">Dosyaya çift tıklayın ve yönergeleri izleyin veya terminalden yükleyin:</span><span class="sxs-lookup"><span data-stu-id="9f474-134">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.0.2-osx.10.12-x64.pkg -target /
```

## <a name="binary-archives"></a><span data-ttu-id="9f474-135">İkili Arşivi</span><span class="sxs-lookup"><span data-stu-id="9f474-135">Binary Archives</span></span>

<span data-ttu-id="9f474-136">PowerShell ikili `tar.gz` arşivleri, macOS ve Linux platformlarında gelişmiş dağıtım senaryoları etkinleştirmek için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="9f474-136">PowerShell binary `tar.gz` archives are provided for macOS and Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="9f474-137">Macos'ta yükleme ikili Arşivi</span><span class="sxs-lookup"><span data-stu-id="9f474-137">Installing binary archives on macOS</span></span>

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

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="9f474-138">PowerShell Core kaldırma</span><span class="sxs-lookup"><span data-stu-id="9f474-138">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="9f474-139">PowerShell ile Homebrew yüklü değilse, kaldırma kolaydır:</span><span class="sxs-lookup"><span data-stu-id="9f474-139">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="9f474-140">PowerShell doğrudan indirme yüklü değilse, PowerShell el ile kaldırılması gerekir:</span><span class="sxs-lookup"><span data-stu-id="9f474-140">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="9f474-141">Ek PowerShell yolları kaldırmak için lütfen bkz [yolları][] bölümü bu belgede ve istenen kullanarak yollarını kaldırma `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="9f474-141">To remove the additional PowerShell paths, please see the [paths][] section in this document and remove the desired the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="9f474-142">Bu, Homebrew ile yüklediyseniz gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="9f474-142">This is not necessary if you installed with Homebrew.</span></span>

[Yolları]:#paths
[paths]:#paths

## <a name="paths"></a><span data-ttu-id="9f474-144">Yollar</span><span class="sxs-lookup"><span data-stu-id="9f474-144">Paths</span></span>

* <span data-ttu-id="9f474-145">`$PSHOME` olduğu `/usr/local/microsoft/powershell/6.0.2/`</span><span class="sxs-lookup"><span data-stu-id="9f474-145">`$PSHOME` is `/usr/local/microsoft/powershell/6.0.2/`</span></span>
* <span data-ttu-id="9f474-146">Kullanıcı profillerini okuyabilir `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="9f474-146">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="9f474-147">Varsayılan profiller okuyabilir `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="9f474-147">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="9f474-148">Kullanıcı modülleri okuyabilir `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="9f474-148">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="9f474-149">Paylaşılan modülleri okuyabilir `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="9f474-149">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="9f474-150">Varsayılan modülleri okuyabilir `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="9f474-150">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="9f474-151">PSReadline geçmişi için kaydedilir `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="9f474-151">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="9f474-152">PowerShell'in konak başına yapılandırma profilleri uyar.</span><span class="sxs-lookup"><span data-stu-id="9f474-152">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="9f474-153">Varsayılan konak özel profilleri var Bu nedenle `Microsoft.PowerShell_profile.ps1` aynı konumlarda.</span><span class="sxs-lookup"><span data-stu-id="9f474-153">So the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="9f474-154">PowerShell uyar [XDG temel dizin belirtimi] [ xdg-bds] macOS üzerinde.</span><span class="sxs-lookup"><span data-stu-id="9f474-154">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="9f474-155">MacOS bir türevi BSD, ön ek olduğundan `/usr/local` yerine kullanılan `/opt`.</span><span class="sxs-lookup"><span data-stu-id="9f474-155">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="9f474-156">Bu nedenle, `$PSHOME` olduğu `/usr/local/microsoft/powershell/6.0.2/`, ve sembolik bağlantısını yerleştirilmiş olması `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="9f474-156">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.0.2/`, and the symlink is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="9f474-157">Ek Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="9f474-157">Additional Resources</span></span>

* <span data-ttu-id="9f474-158">[Homebrew Web][brew]</span><span class="sxs-lookup"><span data-stu-id="9f474-158">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="9f474-159">[Homebrew Github deposu][GitHub]</span><span class="sxs-lookup"><span data-stu-id="9f474-159">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="9f474-160">[Homebrew Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="9f474-160">[Homebrew-Cask][cask]</span></span>


[brew]: http://brew.sh/
[GitHub]: https://github.com/Homebrew
[Cask]: https://github.com/Homebrew/homebrew-cask
[sürümleri]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
