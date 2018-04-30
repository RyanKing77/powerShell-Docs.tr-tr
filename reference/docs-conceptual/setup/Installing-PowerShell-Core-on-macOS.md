# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="42b10-101">PowerShell çekirdeği üzerinde macOS yükleme</span><span class="sxs-lookup"><span data-stu-id="42b10-101">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="42b10-102">PowerShell çekirdeği macOS 10.12 ve üstünü destekler.</span><span class="sxs-lookup"><span data-stu-id="42b10-102">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="42b10-103">Tüm paketler bizim Github'da bulunan [serbest][] sayfası.</span><span class="sxs-lookup"><span data-stu-id="42b10-103">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="42b10-104">Paket yüklendikten sonra çalıştırmak `pwsh` bir terminal gelen.</span><span class="sxs-lookup"><span data-stu-id="42b10-104">Once the package is installed, run `pwsh` from a terminal.</span></span>

### <a name="installation-via-homebrew-on-macos-1012"></a><span data-ttu-id="42b10-105">MacOS 10,12 Homebrew aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="42b10-105">Installation via Homebrew on macOS 10.12</span></span>

<span data-ttu-id="42b10-106">[Homebrew] [ brew] macOS için tercih edilen paket yöneticisidir.</span><span class="sxs-lookup"><span data-stu-id="42b10-106">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="42b10-107">Varsa `brew` komutu bulunamadı, Homebrew aşağıdaki yüklemenize gerek [kendi yönergeleri][brew].</span><span class="sxs-lookup"><span data-stu-id="42b10-107">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

<span data-ttu-id="42b10-108">Homebrew yükledikten sonra PowerShell yükleme kolaydır.</span><span class="sxs-lookup"><span data-stu-id="42b10-108">Once you've installed Homebrew, installing PowerShell is easy.</span></span>
<span data-ttu-id="42b10-109">İlk olarak, yükleme [Homebrew Cask][cask], daha fazla paket yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="42b10-109">First, install [Homebrew-Cask][cask], so you can install more packages:</span></span>

```sh
brew tap caskroom/cask
```

<span data-ttu-id="42b10-110">Şimdi, PowerShell yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="42b10-110">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="42b10-111">Son olarak, yükleme işleminiz düzgün şekilde çalıştığını doğrulayın:</span><span class="sxs-lookup"><span data-stu-id="42b10-111">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="42b10-112">PowerShell yeni sürümleri yayımlandığında, yalnızca Homebrew'ın formül güncelleştirin ve PowerShell yükseltme:</span><span class="sxs-lookup"><span data-stu-id="42b10-112">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="42b10-113">Yukarıdaki komutlarda PowerShell (pwsh) ana bilgisayar içinde çağrılabilir, ancak sonra PowerShell Kabuk çıkıldı ve gerekir yükseltmeyi tamamlamak için yeniden.</span><span class="sxs-lookup"><span data-stu-id="42b10-113">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="42b10-114">ve $PSVersionTable içinde gösterilen değerleri yenileyin.</span><span class="sxs-lookup"><span data-stu-id="42b10-114">and refresh the values shown in $PSVersionTable.</span></span>

[brew]: http://brew.sh/
[cask]: https://caskroom.github.io/

### <a name="installation-via-direct-download"></a><span data-ttu-id="42b10-115">Doğrudan indirme ile yükleme</span><span class="sxs-lookup"><span data-stu-id="42b10-115">Installation via Direct Download</span></span>

<span data-ttu-id="42b10-116">PKG paketini indirin `powershell-6.0.2-osx.10.12-x64.pkg` gelen [serbest][] macOS makinenize sayfası.</span><span class="sxs-lookup"><span data-stu-id="42b10-116">Download the PKG package `powershell-6.0.2-osx.10.12-x64.pkg` from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="42b10-117">Dosyaya çift tıklayın ve yönergeleri izleyin veya terminal durumundan yükleyin:</span><span class="sxs-lookup"><span data-stu-id="42b10-117">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.0.2-osx.10.12-x64.pkg -target /
```

## <a name="binary-archives"></a><span data-ttu-id="42b10-118">İkili arşivler</span><span class="sxs-lookup"><span data-stu-id="42b10-118">Binary Archives</span></span>

<span data-ttu-id="42b10-119">PowerShell ikili `tar.gz` arşivler macOS ve gelişmiş dağıtım senaryoları etkinleştirmek için Linux platformlar için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="42b10-119">PowerShell binary `tar.gz` archives are provided for macOS and Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="42b10-120">MacOS üzerinde yükleme ikili arşivler</span><span class="sxs-lookup"><span data-stu-id="42b10-120">Installing binary archives on macOS</span></span>

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

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="42b10-121">PowerShell çekirdek kaldırma</span><span class="sxs-lookup"><span data-stu-id="42b10-121">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="42b10-122">PowerShell ile Homebrew yüklediyseniz, kaldırma işlemi kolaydır:</span><span class="sxs-lookup"><span data-stu-id="42b10-122">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="42b10-123">PowerShell doğrudan indirme yüklediyseniz, PowerShell el ile kaldırılması gerekir:</span><span class="sxs-lookup"><span data-stu-id="42b10-123">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="42b10-124">Ek PowerShell yolları kaldırmak için lütfen bkz [yolları][] bölümünde bu belgede ve istenen kullanarak yolları Kaldır `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="42b10-124">To remove the additional PowerShell paths, please see the [paths][] section in this document and remove the desired the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="42b10-125">Bu Homebrew ile yüklediyseniz gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="42b10-125">This is not necessary if you installed with Homebrew.</span></span>

[yolları]:#paths
[paths]:#paths

## <a name="paths"></a><span data-ttu-id="42b10-127">Yollar</span><span class="sxs-lookup"><span data-stu-id="42b10-127">Paths</span></span>

* <span data-ttu-id="42b10-128">`$PSHOME` değil `/opt/microsoft/powershell/6.0.0/`</span><span class="sxs-lookup"><span data-stu-id="42b10-128">`$PSHOME` is `/opt/microsoft/powershell/6.0.0/`</span></span>
* <span data-ttu-id="42b10-129">Kullanıcı profillerini okuma `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="42b10-129">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="42b10-130">Varsayılan profiller okuma `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="42b10-130">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="42b10-131">Kullanıcı modülleri okuma `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="42b10-131">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="42b10-132">Paylaşılan modülleri okuma `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="42b10-132">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="42b10-133">Varsayılan modülleri okuma `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="42b10-133">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="42b10-134">PSReadline geçmişi için kaydedilen `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="42b10-134">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="42b10-135">Profilleri PowerShell'in başına ana bilgisayar yapılandırması saygılı olun.</span><span class="sxs-lookup"><span data-stu-id="42b10-135">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="42b10-136">Varsayılan ana bilgisayar özel profiller var böylece `Microsoft.PowerShell_profile.ps1` aynı konumlarda.</span><span class="sxs-lookup"><span data-stu-id="42b10-136">So the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="42b10-137">PowerShell uyar [XDG temel dizin belirtimi] [ xdg-bds] macOS üzerinde.</span><span class="sxs-lookup"><span data-stu-id="42b10-137">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="42b10-138">MacOS BSD, önek türevi olduğundan `/usr/local` yerine kullanılan `/opt`.</span><span class="sxs-lookup"><span data-stu-id="42b10-138">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="42b10-139">Bu nedenle, `$PSHOME` olan `/usr/local/microsoft/powershell/6.0.0/`, ve simgesel yerleştirilmiş olması `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="42b10-139">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.0.0/`, and the symlink is placed at `/usr/local/bin/pwsh`.</span></span>

[serbest]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
