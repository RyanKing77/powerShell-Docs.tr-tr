---
title: MacOS’ta PowerShell Core yükleme
description: Macos'ta PowerShell Core yükleme hakkında bilgi
ms.date: 11/02/2018
ms.openlocfilehash: 162e841bf71d708e9db84ea1bb2dbef13924783b
ms.sourcegitcommit: f4247d3f91d06ec392c4cd66921ce7d0456a2bd9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/05/2018
ms.locfileid: "50998512"
---
# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="7f6bf-103">MacOS’ta PowerShell Core yükleme</span><span class="sxs-lookup"><span data-stu-id="7f6bf-103">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="7f6bf-104">PowerShell Core macOS 10.12 ve üstünü destekler.</span><span class="sxs-lookup"><span data-stu-id="7f6bf-104">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="7f6bf-105">Tüm paketleri bizim Github'da kullanılabilir [sürümleri][] sayfası.</span><span class="sxs-lookup"><span data-stu-id="7f6bf-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="7f6bf-106">Paket yüklendikten sonra Çalıştır `pwsh` bir terminalden.</span><span class="sxs-lookup"><span data-stu-id="7f6bf-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

## <a name="about-brew"></a><span data-ttu-id="7f6bf-107">Brew hakkında</span><span class="sxs-lookup"><span data-stu-id="7f6bf-107">About Brew</span></span>

<span data-ttu-id="7f6bf-108">[Homebrew] [ brew] macOS için tercih edilen bir paket yöneticisidir.</span><span class="sxs-lookup"><span data-stu-id="7f6bf-108">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="7f6bf-109">Varsa `brew` komutu bulunamazsa, Homebrew aşağıdakileri yüklemeniz gerekir [kendi yönergeleri][brew].</span><span class="sxs-lookup"><span data-stu-id="7f6bf-109">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="7f6bf-110">Homebrew aracılığıyla en son kararlı sürüm MacOS 10.12 veya üzeri yüklemesi</span><span class="sxs-lookup"><span data-stu-id="7f6bf-110">Installation of latest stable release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="7f6bf-111">Bkz: [hakkında Brew](#about-brew) Brew hakkında bilgi için.</span><span class="sxs-lookup"><span data-stu-id="7f6bf-111">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="7f6bf-112">Şimdi, PowerShell'i yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7f6bf-112">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="7f6bf-113">Son olarak, yükleme işleminiz düzgün çalıştığını doğrulayın:</span><span class="sxs-lookup"><span data-stu-id="7f6bf-113">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="7f6bf-114">PowerShell'in yeni sürümü yayımlandığında, yalnızca formüllerini Homebrew'ın güncelleştirin ve PowerShell yükseltme:</span><span class="sxs-lookup"><span data-stu-id="7f6bf-114">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="7f6bf-115">Yukarıdaki komutlar içindeki bir PowerShell (pwsh) ana çağrılabilir, ancak daha sonra PowerShell Kabuk çıkıldı ve gereken $PSVersionTable içinde gösterilen değerleri yenileyin ve yükseltmeyi tamamlamak için bilgisayarınızın yeniden başlatılması.</span><span class="sxs-lookup"><span data-stu-id="7f6bf-115">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in $PSVersionTable.</span></span>

[brew]: http://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="7f6bf-116">En son Önizleme yüklenmesini Homebrew macOS 10.12 ya da daha yüksek sürüm</span><span class="sxs-lookup"><span data-stu-id="7f6bf-116">Installation of latest preview release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="7f6bf-117">Bkz: [hakkında Brew](#about-brew) Brew hakkında bilgi için.</span><span class="sxs-lookup"><span data-stu-id="7f6bf-117">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="7f6bf-118">Homebrew yükledikten sonra PowerShell'i yükleme kolaydır.</span><span class="sxs-lookup"><span data-stu-id="7f6bf-118">Once you've installed Homebrew, installing PowerShell is easy.</span></span>
<span data-ttu-id="7f6bf-119">İlk olarak, yükleme [Cask sürümleri] [ cask-versions] olanak sağlayan diğer sürümlerini cask paketleri yükleyin:</span><span class="sxs-lookup"><span data-stu-id="7f6bf-119">First, install [Cask-Versions][cask-versions] which lets you install alternative versions of cask packages:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="7f6bf-120">Şimdi, PowerShell'i yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7f6bf-120">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="7f6bf-121">Son olarak, yükleme işleminiz düzgün çalıştığını doğrulayın:</span><span class="sxs-lookup"><span data-stu-id="7f6bf-121">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="7f6bf-122">PowerShell'in yeni sürümü yayımlandığında, yalnızca formüllerini Homebrew'ın güncelleştirin ve PowerShell yükseltme:</span><span class="sxs-lookup"><span data-stu-id="7f6bf-122">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="7f6bf-123">Yukarıdaki komutlar içindeki bir PowerShell (pwsh) ana çağrılabilir, ancak daha sonra PowerShell Kabuk çıkıldı ve gerekir yükseltmeyi tamamlamak için bilgisayarınızın yeniden başlatılması.</span><span class="sxs-lookup"><span data-stu-id="7f6bf-123">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="7f6bf-124">ve $PSVersionTable içinde gösterilen değerleri yenileyin.</span><span class="sxs-lookup"><span data-stu-id="7f6bf-124">and refresh the values shown in $PSVersionTable.</span></span>

## <a name="installation-via-direct-download"></a><span data-ttu-id="7f6bf-125">Doğrudan indirme ile yükleme</span><span class="sxs-lookup"><span data-stu-id="7f6bf-125">Installation via Direct Download</span></span>

<span data-ttu-id="7f6bf-126">PKG paketini indirme `powershell-6.1.0-osx-x64.pkg`</span><span class="sxs-lookup"><span data-stu-id="7f6bf-126">Download the PKG package `powershell-6.1.0-osx-x64.pkg`</span></span>
<span data-ttu-id="7f6bf-127">gelen [sürümleri][] macOS makinenizde sayfaya.</span><span class="sxs-lookup"><span data-stu-id="7f6bf-127">from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="7f6bf-128">Dosyaya çift tıklayın ve yönergeleri izleyin veya terminalden yükleyin:</span><span class="sxs-lookup"><span data-stu-id="7f6bf-128">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.1.0-osx-x64.pkg -target /
```

<span data-ttu-id="7f6bf-129">Yükleme [OpenSSL](#install-openssl) olarak PowerShell uzaktan iletişim ve CIM işlemleri için bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="7f6bf-129">Install [OpenSSL](#install-openssl) as this is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="7f6bf-130">İkili Arşivi</span><span class="sxs-lookup"><span data-stu-id="7f6bf-130">Binary Archives</span></span>

<span data-ttu-id="7f6bf-131">PowerShell ikili `tar.gz` arşivleri gelişmiş dağıtım senaryoları etkinleştirmek macOS platformu için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="7f6bf-131">PowerShell binary `tar.gz` archives are provided for the macOS platform to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="7f6bf-132">Macos'ta yükleme ikili Arşivi</span><span class="sxs-lookup"><span data-stu-id="7f6bf-132">Installing binary archives on macOS</span></span>

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

<span data-ttu-id="7f6bf-133">Yükleme [OpenSSL](#install-openssl) olarak PowerShell uzaktan iletişim ve CIM işlemleri için bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="7f6bf-133">Install [OpenSSL](#install-openssl) as this is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="installing-dependencies"></a><span data-ttu-id="7f6bf-134">Bağımlılıklar yükleniyor</span><span class="sxs-lookup"><span data-stu-id="7f6bf-134">Installing dependencies</span></span>

### <a name="install-xcode-command-line-tools"></a><span data-ttu-id="7f6bf-135">XCode komut satırı araçlarını yükleyin</span><span class="sxs-lookup"><span data-stu-id="7f6bf-135">Install XCode command line tools</span></span>

```shell
xcode-select -install
```

### <a name="install-openssl"></a><span data-ttu-id="7f6bf-136">OpenSSL yükleyin</span><span class="sxs-lookup"><span data-stu-id="7f6bf-136">Install OpenSSL</span></span>

<span data-ttu-id="7f6bf-137">OpenSSL PowerShell uzaktan iletişim ve CIM işlemleri için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="7f6bf-137">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>  <span data-ttu-id="7f6bf-138">Yükleyebileceğiniz MacPorts veya Brew aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="7f6bf-138">You can install via MacPorts or Brew.</span></span>

#### <a name="install-openssl-via-brew"></a><span data-ttu-id="7f6bf-139">OpenSSL Brew aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="7f6bf-139">Install OpenSSL via Brew</span></span>

<span data-ttu-id="7f6bf-140">Bkz: [hakkında Brew](#about-brew) Brew hakkında bilgi için.</span><span class="sxs-lookup"><span data-stu-id="7f6bf-140">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="7f6bf-141">Çalıştırma `brew install openssl` OpenSSL yüklemek için.</span><span class="sxs-lookup"><span data-stu-id="7f6bf-141">Run `brew install openssl` to install OpenSSL.</span></span>

#### <a name="install-openssl-via-macports"></a><span data-ttu-id="7f6bf-142">OpenSSL MacPorts aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="7f6bf-142">Install OpenSSL via MacPorts</span></span>

1. <span data-ttu-id="7f6bf-143">Tümünü Yükle [XCode komut satırı araçları](#install-xcode-command-line-tools)</span><span class="sxs-lookup"><span data-stu-id="7f6bf-143">Instal the [XCode command line tools](#install-xcode-command-line-tools)</span></span>
1. <span data-ttu-id="7f6bf-144">MacPorts yükleyin.</span><span class="sxs-lookup"><span data-stu-id="7f6bf-144">Install MacPorts.</span></span>
   <span data-ttu-id="7f6bf-145">Bkz: [Yükleme Kılavuzu](https://guide.macports.org/chunked/installing.macports.html) yönergelere ihtiyacınız varsa.</span><span class="sxs-lookup"><span data-stu-id="7f6bf-145">See the [installation guide](https://guide.macports.org/chunked/installing.macports.html) if you need instructions.</span></span>
1. <span data-ttu-id="7f6bf-146">Çalıştırarak MacPorts güncelleştir `sudo port selfupdate`</span><span class="sxs-lookup"><span data-stu-id="7f6bf-146">Update MacPorts by running `sudo port selfupdate`</span></span>
1. <span data-ttu-id="7f6bf-147">Çalıştırarak MacPorts paketlerini yükseltin `sudo port upgrade outdated`</span><span class="sxs-lookup"><span data-stu-id="7f6bf-147">Upgrade MacPorts packages by running `sudo port upgrade outdated`</span></span>
1. <span data-ttu-id="7f6bf-148">OpenSSL çalıştırarak çalıştırıp yükleyin. `sudo port instal openssl`</span><span class="sxs-lookup"><span data-stu-id="7f6bf-148">Install OpenSSL by running by running `sudo port instal openssl`</span></span>
1. <span data-ttu-id="7f6bf-149">PowerShell kullanabilmesi kitaplıkları bağlayın.</span><span class="sxs-lookup"><span data-stu-id="7f6bf-149">Link the libraries so that PowerShell can use it.</span></span>

```shell
sudo mkdir -p /usr/local/opt/openssl
sudo ln -s /opt/local/lib /usr/local/opt/openssl/lib
```

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="7f6bf-150">PowerShell Core kaldırma</span><span class="sxs-lookup"><span data-stu-id="7f6bf-150">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="7f6bf-151">PowerShell ile Homebrew yüklü değilse, kaldırma kolaydır:</span><span class="sxs-lookup"><span data-stu-id="7f6bf-151">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="7f6bf-152">PowerShell doğrudan indirme yüklü değilse, PowerShell el ile kaldırılması gerekir:</span><span class="sxs-lookup"><span data-stu-id="7f6bf-152">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="7f6bf-153">Ek PowerShell yolları kaldırmak için lütfen bkz [yolları](#paths) bölümü bu belgede ve istenen kullanarak yollarını kaldırma `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="7f6bf-153">To remove the additional PowerShell paths, please see the [paths](#paths) section in this document and remove the desired the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="7f6bf-154">Bu, Homebrew ile yüklediyseniz gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="7f6bf-154">This is not necessary if you installed with Homebrew.</span></span>

## <a name="paths"></a><span data-ttu-id="7f6bf-155">Yollar</span><span class="sxs-lookup"><span data-stu-id="7f6bf-155">Paths</span></span>

* <span data-ttu-id="7f6bf-156">`$PSHOME` olduğu `/usr/local/microsoft/powershell/6.1.0/`</span><span class="sxs-lookup"><span data-stu-id="7f6bf-156">`$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`</span></span>
* <span data-ttu-id="7f6bf-157">Kullanıcı profillerini okuyabilir `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="7f6bf-157">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="7f6bf-158">Varsayılan profiller okuyabilir `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="7f6bf-158">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="7f6bf-159">Kullanıcı modülleri okuyabilir `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="7f6bf-159">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="7f6bf-160">Paylaşılan modülleri okuyabilir `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="7f6bf-160">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="7f6bf-161">Varsayılan modülleri okuyabilir `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="7f6bf-161">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="7f6bf-162">PSReadline geçmişi için kaydedilir `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="7f6bf-162">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="7f6bf-163">PowerShell'in konak başına yapılandırma profilleri uyar.</span><span class="sxs-lookup"><span data-stu-id="7f6bf-163">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="7f6bf-164">Varsayılan konak özel profilleri var Bu nedenle `Microsoft.PowerShell_profile.ps1` aynı konumlarda.</span><span class="sxs-lookup"><span data-stu-id="7f6bf-164">So the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="7f6bf-165">PowerShell uyar [XDG temel dizin belirtimi] [ xdg-bds] macOS üzerinde.</span><span class="sxs-lookup"><span data-stu-id="7f6bf-165">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="7f6bf-166">MacOS bir türevi BSD, ön ek olduğundan `/usr/local` yerine kullanılan `/opt`.</span><span class="sxs-lookup"><span data-stu-id="7f6bf-166">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="7f6bf-167">Bu nedenle, `$PSHOME` olduğu `/usr/local/microsoft/powershell/6.1.0/`, ve sembolik bağlantısını yerleştirilmiş olması `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="7f6bf-167">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`, and the symbolic link is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="7f6bf-168">Ek Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="7f6bf-168">Additional Resources</span></span>

* <span data-ttu-id="7f6bf-169">[Homebrew Web][brew]</span><span class="sxs-lookup"><span data-stu-id="7f6bf-169">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="7f6bf-170">[Homebrew Github deposu][GitHub]</span><span class="sxs-lookup"><span data-stu-id="7f6bf-170">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="7f6bf-171">[Homebrew Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="7f6bf-171">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[sürümleri]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
