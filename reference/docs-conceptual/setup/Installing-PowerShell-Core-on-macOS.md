# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="4b8d4-101">MacOS’ta PowerShell Core yükleme</span><span class="sxs-lookup"><span data-stu-id="4b8d4-101">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="4b8d4-102">PowerShell Core macOS 10.12 ve üstünü destekler.</span><span class="sxs-lookup"><span data-stu-id="4b8d4-102">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="4b8d4-103">Tüm paketleri bizim Github'da kullanılabilir [sürümleri][] sayfası.</span><span class="sxs-lookup"><span data-stu-id="4b8d4-103">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="4b8d4-104">Paket yüklendikten sonra Çalıştır `pwsh` bir terminalden.</span><span class="sxs-lookup"><span data-stu-id="4b8d4-104">Once the package is installed, run `pwsh` from a terminal.</span></span>

### <a name="installation-via-homebrew-on-macos-1012"></a><span data-ttu-id="4b8d4-105">MacOS 10.12 + üzerinde Homebrew ile yükleme</span><span class="sxs-lookup"><span data-stu-id="4b8d4-105">Installation via Homebrew on macOS 10.12+</span></span>

<span data-ttu-id="4b8d4-106">[Homebrew] [ brew] macOS için tercih edilen bir paket yöneticisidir.</span><span class="sxs-lookup"><span data-stu-id="4b8d4-106">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="4b8d4-107">Bir terminal penceresinde `brew` Homebrew çalıştırılacak.</span><span class="sxs-lookup"><span data-stu-id="4b8d4-107">From a terminal window, type `brew` to run Homebrew.</span></span>  <span data-ttu-id="4b8d4-108">Varsa `brew` komutu bulunamazsa, Homebrew aşağıdakileri yüklemeniz gerekir [kendi yönergeleri][brew].</span><span class="sxs-lookup"><span data-stu-id="4b8d4-108">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

> [!NOTE]
> <span data-ttu-id="4b8d4-109">Geçmişte Homebrew yüklü değilse, bu her zaman 'güncelleştirme sıfırlama brew' çalıştırmak için iyi bir fikirdir & & 'güncelleştirme brew'.</span><span class="sxs-lookup"><span data-stu-id="4b8d4-109">If you installed Homebrew in the past, it's always a good idea to run 'brew update-reset' && 'brew update'.</span></span>
```sh
brew update-reset
brew update
```

> <span data-ttu-id="4b8d4-110">Homebrew eski sürümlerini dokunun 'caskroom/kullanım dışı, ve 'homebrew/cask' geçirilen cask', kullanılan.</span><span class="sxs-lookup"><span data-stu-id="4b8d4-110">Older versions of Homebrew used the tap 'caskroom/cask', which has been deprecated, and migrated into 'homebrew/cask'.</span></span>  <span data-ttu-id="4b8d4-111">Daha fazla bilgi şu adreste bulunabilir: [Homebrew cask][cask].</span><span class="sxs-lookup"><span data-stu-id="4b8d4-111">More information can be found at [Homebrew-cask][cask].</span></span> <span data-ttu-id="4b8d4-112">Geçerli, Tap'ları listelemek için 'brew dokunun' komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="4b8d4-112">Use the 'brew tap' command to list your current taps.</span></span>  <span data-ttu-id="4b8d4-113">' Caskroom/cask' görürseniz 'güncelleştirme brew' kullanabilirsiniz geçişi dokunma Homebrew sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="4b8d4-113">If you see 'caskroom/cask' you can use 'brew update' to have Homebrew migrate the taps.</span></span>

```sh
brew tap
brew update
```

<span data-ttu-id="4b8d4-114">PowerShell'i yükleme yüklü/Homebrew güncel sonra kolaydır.</span><span class="sxs-lookup"><span data-stu-id="4b8d4-114">Once you've installed/updated Homebrew, installing PowerShell is easy.</span></span>

<span data-ttu-id="4b8d4-115">PowerShell'i yüklemek için:</span><span class="sxs-lookup"><span data-stu-id="4b8d4-115">To install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="4b8d4-116">Son olarak, yükleme işleminiz düzgün çalıştığını doğrulayın:</span><span class="sxs-lookup"><span data-stu-id="4b8d4-116">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="4b8d4-117">PowerShell betiğinden çıkın ve bash geri dönmek için 'Çık' komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="4b8d4-117">To exit PowerShell, and return to bash, use the 'exit' command.</span></span> 
```sh
exit
```

<span data-ttu-id="4b8d4-118">PowerShell'in yeni sürümü yayımlandığında, yalnızca formüllerini Homebrew'ın güncelleştirin ve PowerShell yükseltme:</span><span class="sxs-lookup"><span data-stu-id="4b8d4-118">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="4b8d4-119">Yukarıdaki komutlar içindeki bir PowerShell (pwsh) ana çağrılabilir, ancak daha sonra PowerShell Kabuk çıkıldı ve gereken $PSVersionTable içinde gösterilen değerleri yenileyin ve yükseltmeyi tamamlamak için bilgisayarınızın yeniden başlatılması.</span><span class="sxs-lookup"><span data-stu-id="4b8d4-119">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in $PSVersionTable.</span></span>

### <a name="installing-preview-via-homebrew-on-macos-1012"></a><span data-ttu-id="4b8d4-120">MacOS üzerinde 10.12 + Önizleme Homebrew ile yükleme</span><span class="sxs-lookup"><span data-stu-id="4b8d4-120">Installing Preview via Homebrew on macOS 10.12+</span></span>

<span data-ttu-id="4b8d4-121">[Homebrew] [ brew] macOS için tercih edilen bir paket yöneticisidir.</span><span class="sxs-lookup"><span data-stu-id="4b8d4-121">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="4b8d4-122">Bir terminal penceresinde `brew` Homebrew çalıştırılacak.</span><span class="sxs-lookup"><span data-stu-id="4b8d4-122">From a terminal window, type `brew` to run Homebrew.</span></span>  <span data-ttu-id="4b8d4-123">Varsa `brew` komutu bulunamazsa, Homebrew aşağıdakileri yüklemeniz gerekir [kendi yönergeleri][brew].</span><span class="sxs-lookup"><span data-stu-id="4b8d4-123">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

> [!NOTE]
> <span data-ttu-id="4b8d4-124">Geçmişte Homebrew yüklü değilse, bu her zaman 'güncelleştirme sıfırlama brew' çalıştırmak için iyi bir fikirdir & & 'güncelleştirme brew'.</span><span class="sxs-lookup"><span data-stu-id="4b8d4-124">If you installed Homebrew in the past, it's always a good idea to run 'brew update-reset' && 'brew update'.</span></span>
```sh
brew update-reset
brew update
```

<span data-ttu-id="4b8d4-125">Ardından, dokunması gerekir `versions` casks Depo önizleme paketini almak için:</span><span class="sxs-lookup"><span data-stu-id="4b8d4-125">Then, you must tap the `versions` casks repository to get the preview package:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="4b8d4-126">PowerShell Önizleme yüklemek için:</span><span class="sxs-lookup"><span data-stu-id="4b8d4-126">To install PowerShell Preview:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="4b8d4-127">Son olarak, yükleme işleminiz düzgün çalıştığını doğrulayın:</span><span class="sxs-lookup"><span data-stu-id="4b8d4-127">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="4b8d4-128">PowerShell'in yeni sürümü yayımlandığında, yalnızca formüllerini Homebrew'ın güncelleştirin ve PowerShell Önizleme yükseltme:</span><span class="sxs-lookup"><span data-stu-id="4b8d4-128">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell Preview:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="4b8d4-129">Yukarıdaki komutlar içindeki bir PowerShell (pwsh) ana çağrılabilir, ancak daha sonra PowerShell Kabuk çıkıldı ve gereken $PSVersionTable içinde gösterilen değerleri yenileyin ve yükseltmeyi tamamlamak için bilgisayarınızın yeniden başlatılması.</span><span class="sxs-lookup"><span data-stu-id="4b8d4-129">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in $PSVersionTable.</span></span>

### <a name="installation-via-direct-download"></a><span data-ttu-id="4b8d4-130">Doğrudan indirme ile yükleme</span><span class="sxs-lookup"><span data-stu-id="4b8d4-130">Installation via Direct Download</span></span>

<span data-ttu-id="4b8d4-131">PKG paketini indirme `powershell-6.0.2-osx.10.12-x64.pkg` gelen [sürümleri][] macOS makinenizde sayfaya.</span><span class="sxs-lookup"><span data-stu-id="4b8d4-131">Download the PKG package `powershell-6.0.2-osx.10.12-x64.pkg` from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="4b8d4-132">Dosyaya çift tıklayın ve yönergeleri izleyin veya terminalden yükleyin:</span><span class="sxs-lookup"><span data-stu-id="4b8d4-132">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.0.2-osx.10.12-x64.pkg -target /
```

## <a name="binary-archives"></a><span data-ttu-id="4b8d4-133">İkili Arşivi</span><span class="sxs-lookup"><span data-stu-id="4b8d4-133">Binary Archives</span></span>

<span data-ttu-id="4b8d4-134">PowerShell ikili `tar.gz` arşivleri, macOS ve Linux platformlarında gelişmiş dağıtım senaryoları etkinleştirmek için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="4b8d4-134">PowerShell binary `tar.gz` archives are provided for macOS and Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="4b8d4-135">Macos'ta yükleme ikili Arşivi</span><span class="sxs-lookup"><span data-stu-id="4b8d4-135">Installing binary archives on macOS</span></span>

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

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="4b8d4-136">PowerShell Core kaldırma</span><span class="sxs-lookup"><span data-stu-id="4b8d4-136">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="4b8d4-137">PowerShell ile Homebrew yüklü değilse, kaldırma kolaydır:</span><span class="sxs-lookup"><span data-stu-id="4b8d4-137">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="4b8d4-138">PowerShell doğrudan indirme yüklü değilse, PowerShell el ile kaldırılması gerekir:</span><span class="sxs-lookup"><span data-stu-id="4b8d4-138">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="4b8d4-139">Ek PowerShell yolları kaldırmak için lütfen bkz [yolları][] bölümü bu belgede ve istenen kullanarak yollarını kaldırma `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="4b8d4-139">To remove the additional PowerShell paths, please see the [paths][] section in this document and remove the desired the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="4b8d4-140">Bu, Homebrew ile yüklediyseniz gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="4b8d4-140">This is not necessary if you installed with Homebrew.</span></span>

[Yolları]:#paths
[paths]:#paths

## <a name="paths"></a><span data-ttu-id="4b8d4-142">Yollar</span><span class="sxs-lookup"><span data-stu-id="4b8d4-142">Paths</span></span>

* <span data-ttu-id="4b8d4-143">`$PSHOME` olduğu `/usr/local/microsoft/powershell/6.0.2/`</span><span class="sxs-lookup"><span data-stu-id="4b8d4-143">`$PSHOME` is `/usr/local/microsoft/powershell/6.0.2/`</span></span>
* <span data-ttu-id="4b8d4-144">Kullanıcı profillerini okuyabilir `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="4b8d4-144">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="4b8d4-145">Varsayılan profiller okuyabilir `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="4b8d4-145">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="4b8d4-146">Kullanıcı modülleri okuyabilir `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="4b8d4-146">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="4b8d4-147">Paylaşılan modülleri okuyabilir `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="4b8d4-147">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="4b8d4-148">Varsayılan modülleri okuyabilir `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="4b8d4-148">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="4b8d4-149">PSReadline geçmişi için kaydedilir `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="4b8d4-149">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="4b8d4-150">PowerShell'in konak başına yapılandırma profilleri uyar.</span><span class="sxs-lookup"><span data-stu-id="4b8d4-150">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="4b8d4-151">Varsayılan konak özel profilleri var Bu nedenle `Microsoft.PowerShell_profile.ps1` aynı konumlarda.</span><span class="sxs-lookup"><span data-stu-id="4b8d4-151">So the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="4b8d4-152">PowerShell uyar [XDG temel dizin belirtimi] [ xdg-bds] macOS üzerinde.</span><span class="sxs-lookup"><span data-stu-id="4b8d4-152">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="4b8d4-153">MacOS bir türevi BSD, ön ek olduğundan `/usr/local` yerine kullanılan `/opt`.</span><span class="sxs-lookup"><span data-stu-id="4b8d4-153">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="4b8d4-154">Bu nedenle, `$PSHOME` olduğu `/usr/local/microsoft/powershell/6.0.2/`, ve sembolik bağlantısını yerleştirilmiş olması `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="4b8d4-154">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.0.2/`, and the symlink is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="4b8d4-155">Ek Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="4b8d4-155">Additional Resources</span></span>

* <span data-ttu-id="4b8d4-156">[Homebrew Web][brew]</span><span class="sxs-lookup"><span data-stu-id="4b8d4-156">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="4b8d4-157">[Homebrew Github deposu][GitHub]</span><span class="sxs-lookup"><span data-stu-id="4b8d4-157">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="4b8d4-158">[Homebrew Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="4b8d4-158">[Homebrew-Cask][cask]</span></span>


[brew]: http://brew.sh/
[GitHub]: https://github.com/Homebrew
[Cask]: https://github.com/Homebrew/homebrew-cask
[sürümleri]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
