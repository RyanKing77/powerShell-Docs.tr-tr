---
title: MacOS’ta PowerShell Core yükleme
description: Macos'ta PowerShell Core yükleme hakkında bilgi
ms.date: 12/12/2018
ms.openlocfilehash: 70f5d64aa8a697a9011d07fbcb2bb821463827e1
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229742"
---
# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="10b94-103">MacOS’ta PowerShell Core yükleme</span><span class="sxs-lookup"><span data-stu-id="10b94-103">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="10b94-104">PowerShell Core macOS 10.12 ve üstünü destekler.</span><span class="sxs-lookup"><span data-stu-id="10b94-104">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="10b94-105">Tüm paketleri bizim Github'da kullanılabilir [Yayınları][] sayfası.</span><span class="sxs-lookup"><span data-stu-id="10b94-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="10b94-106">Paket yüklendikten sonra çalıştırın `pwsh` bir terminalden.</span><span class="sxs-lookup"><span data-stu-id="10b94-106">After the package is installed, run `pwsh` from a terminal.</span></span>

## <a name="about-brew"></a><span data-ttu-id="10b94-107">Brew hakkında</span><span class="sxs-lookup"><span data-stu-id="10b94-107">About Brew</span></span>

<span data-ttu-id="10b94-108">[Homebrew] [ brew] macOS için tercih edilen bir paket yöneticisidir.</span><span class="sxs-lookup"><span data-stu-id="10b94-108">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="10b94-109">Varsa `brew` komutu bulunamazsa, Homebrew aşağıdakileri yüklemeniz gerekir [kendi yönergeleri][brew].</span><span class="sxs-lookup"><span data-stu-id="10b94-109">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>
<span data-ttu-id="10b94-110">Aksi takdirde PowerShell aracılığıyla yükleyebilirsiniz [doğrudan indirin](#installation-via-direct-download) veya [ikili arşivleri](#binary-archives).</span><span class="sxs-lookup"><span data-stu-id="10b94-110">Otherwise you may install PowerShell via [Direct Download](#installation-via-direct-download) or from [Binary Archives](#binary-archives).</span></span>

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="10b94-111">Homebrew aracılığıyla en son kararlı sürüm MacOS 10.12 veya üzeri yüklemesi</span><span class="sxs-lookup"><span data-stu-id="10b94-111">Installation of latest stable release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="10b94-112">Bkz: [hakkında Brew](#about-brew) Brew hakkında bilgi için.</span><span class="sxs-lookup"><span data-stu-id="10b94-112">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="10b94-113">Şimdi, PowerShell'i yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="10b94-113">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="10b94-114">Son olarak, yükleme işleminiz düzgün çalıştığını doğrulayın:</span><span class="sxs-lookup"><span data-stu-id="10b94-114">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="10b94-115">PowerShell'in yeni sürümü yayımlandığında, Homebrew'ın formüllerini güncelleştirin ve PowerShell yükseltme:</span><span class="sxs-lookup"><span data-stu-id="10b94-115">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="10b94-116">Yukarıdaki komutlar içindeki bir PowerShell (pwsh) ana çağrılabilir, ancak daha sonra PowerShell Kabuk çıkıldı ve gereken yükseltmesini tamamladıktan sonra gösterilen değerleri yenileme için bilgisayarınızın yeniden başlatılması `$PSVersionTable`.</span><span class="sxs-lookup"><span data-stu-id="10b94-116">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in `$PSVersionTable`.</span></span>

[brew]: http://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="10b94-117">En son Önizleme yüklenmesini Homebrew macOS 10.12 ya da daha yüksek sürüm</span><span class="sxs-lookup"><span data-stu-id="10b94-117">Installation of latest preview release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="10b94-118">Bkz: [hakkında Brew](#about-brew) Brew hakkında bilgi için.</span><span class="sxs-lookup"><span data-stu-id="10b94-118">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="10b94-119">Homebrew yükledikten sonra PowerShell'i yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="10b94-119">After you've installed Homebrew, you can install PowerShell.</span></span>
<span data-ttu-id="10b94-120">İlk olarak, yükleme [Cask sürümleri] [ cask-versions] cask paketlerin diğer sürümlerini yüklemenize olanak sağlayan paket:</span><span class="sxs-lookup"><span data-stu-id="10b94-120">First, install the [Cask-Versions][cask-versions] package that lets you install alternative versions of cask packages:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="10b94-121">Şimdi, PowerShell'i yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="10b94-121">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="10b94-122">Son olarak, yükleme işleminiz düzgün çalıştığını doğrulayın:</span><span class="sxs-lookup"><span data-stu-id="10b94-122">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="10b94-123">PowerShell'in yeni sürümü yayımlandığında, Homebrew'ın formüllerini güncelleştirin ve PowerShell yükseltme:</span><span class="sxs-lookup"><span data-stu-id="10b94-123">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="10b94-124">Yukarıdaki komutlar içindeki bir PowerShell (pwsh) ana çağrılabilir, ancak daha sonra PowerShell Kabuk çıkıldı ve gerekir yükseltmeyi tamamlamak için bilgisayarınızın yeniden başlatılması.</span><span class="sxs-lookup"><span data-stu-id="10b94-124">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="10b94-125">ve gösterilen değerleri yenileme `$PSVersionTable`.</span><span class="sxs-lookup"><span data-stu-id="10b94-125">and refresh the values shown in `$PSVersionTable`.</span></span>

## <a name="installation-via-direct-download"></a><span data-ttu-id="10b94-126">Doğrudan indirme ile yükleme</span><span class="sxs-lookup"><span data-stu-id="10b94-126">Installation via Direct Download</span></span>

<span data-ttu-id="10b94-127">PKG paketini indirme `powershell-6.2.0-osx-x64.pkg`</span><span class="sxs-lookup"><span data-stu-id="10b94-127">Download the PKG package `powershell-6.2.0-osx-x64.pkg`</span></span>
<span data-ttu-id="10b94-128">gelen [Yayınları][] macOS makinenizde sayfaya.</span><span class="sxs-lookup"><span data-stu-id="10b94-128">from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="10b94-129">Dosyaya çift tıklayın ve yönergeleri izleyin veya terminalden yükleyin:</span><span class="sxs-lookup"><span data-stu-id="10b94-129">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.2.0-osx-x64.pkg -target /
```

<span data-ttu-id="10b94-130">Yükleme [OpenSSL](#install-openssl).</span><span class="sxs-lookup"><span data-stu-id="10b94-130">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="10b94-131">OpenSSL PowerShell uzaktan iletişim ve CIM işlemleri için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="10b94-131">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="10b94-132">İkili Arşivi</span><span class="sxs-lookup"><span data-stu-id="10b94-132">Binary Archives</span></span>

<span data-ttu-id="10b94-133">PowerShell ikili `tar.gz` arşivleri gelişmiş dağıtım senaryoları etkinleştirmek macOS platformu için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="10b94-133">PowerShell binary `tar.gz` archives are provided for the macOS platform to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="10b94-134">Macos'ta yükleme ikili Arşivi</span><span class="sxs-lookup"><span data-stu-id="10b94-134">Installing binary archives on macOS</span></span>

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

<span data-ttu-id="10b94-135">Yükleme [OpenSSL](#install-openssl).</span><span class="sxs-lookup"><span data-stu-id="10b94-135">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="10b94-136">OpenSSL PowerShell uzaktan iletişim ve CIM işlemleri için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="10b94-136">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="installing-dependencies"></a><span data-ttu-id="10b94-137">Bağımlılıklar yükleniyor</span><span class="sxs-lookup"><span data-stu-id="10b94-137">Installing dependencies</span></span>

### <a name="install-xcode-command-line-tools"></a><span data-ttu-id="10b94-138">XCode komut satırı araçlarını yükleme</span><span class="sxs-lookup"><span data-stu-id="10b94-138">Install XCode command-line tools</span></span>

```sh
xcode-select --install
```

### <a name="install-openssl"></a><span data-ttu-id="10b94-139">OpenSSL yükleyin</span><span class="sxs-lookup"><span data-stu-id="10b94-139">Install OpenSSL</span></span>

<span data-ttu-id="10b94-140">OpenSSL PowerShell uzaktan iletişim ve CIM işlemleri için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="10b94-140">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span> <span data-ttu-id="10b94-141">Yükleyebileceğiniz MacPorts veya Brew aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="10b94-141">You can install via MacPorts or Brew.</span></span>

#### <a name="install-openssl-via-brew"></a><span data-ttu-id="10b94-142">OpenSSL Brew aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="10b94-142">Install OpenSSL via Brew</span></span>

<span data-ttu-id="10b94-143">Bkz: [hakkında Brew](#about-brew) Brew hakkında bilgi için.</span><span class="sxs-lookup"><span data-stu-id="10b94-143">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="10b94-144">OpenSSL yüklemek için çalıştırın `brew install openssl`.</span><span class="sxs-lookup"><span data-stu-id="10b94-144">To install OpenSSL, run `brew install openssl`.</span></span>

#### <a name="install-openssl-via-macports"></a><span data-ttu-id="10b94-145">OpenSSL MacPorts aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="10b94-145">Install OpenSSL via MacPorts</span></span>

1. <span data-ttu-id="10b94-146">Yükleme [XCode komut satırı araçları](#install-xcode-command-line-tools).</span><span class="sxs-lookup"><span data-stu-id="10b94-146">Install the [XCode command line tools](#install-xcode-command-line-tools).</span></span>
1. <span data-ttu-id="10b94-147">MacPorts yükleyin.</span><span class="sxs-lookup"><span data-stu-id="10b94-147">Install MacPorts.</span></span>
   <span data-ttu-id="10b94-148">Yönergelere ihtiyacınız varsa, başvurmak [Yükleme Kılavuzu](https://guide.macports.org/chunked/installing.macports.html).</span><span class="sxs-lookup"><span data-stu-id="10b94-148">If you need instructions, refer to the [installation guide](https://guide.macports.org/chunked/installing.macports.html).</span></span>
1. <span data-ttu-id="10b94-149">Çalıştırarak MacPorts güncelleştirme `sudo port selfupdate`.</span><span class="sxs-lookup"><span data-stu-id="10b94-149">Update MacPorts by running `sudo port selfupdate`.</span></span>
1. <span data-ttu-id="10b94-150">MacPorts paketleri çalıştırarak yükseltme `sudo port upgrade outdated`.</span><span class="sxs-lookup"><span data-stu-id="10b94-150">Upgrade MacPorts packages by running `sudo port upgrade outdated`.</span></span>
1. <span data-ttu-id="10b94-151">OpenSSL çalıştırarak yükleyin `sudo port install openssl`.</span><span class="sxs-lookup"><span data-stu-id="10b94-151">Install OpenSSL by running `sudo port install openssl`.</span></span>
1. <span data-ttu-id="10b94-152">PowerShell için kullanılabilir hale getirmek kitaplıkları Bağla:</span><span class="sxs-lookup"><span data-stu-id="10b94-152">Link the libraries to make them available to PowerShell:</span></span>

```sh
sudo mkdir -p /usr/local/opt/openssl
sudo ln -s /opt/local/lib /usr/local/opt/openssl/lib
```

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="10b94-153">PowerShell Core kaldırma</span><span class="sxs-lookup"><span data-stu-id="10b94-153">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="10b94-154">PowerShell ile Homebrew yüklü değilse, kaldırmak için aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="10b94-154">If you installed PowerShell with Homebrew, use the following command to uninstall:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="10b94-155">PowerShell doğrudan indirme yüklü değilse, PowerShell el ile kaldırılması gerekir:</span><span class="sxs-lookup"><span data-stu-id="10b94-155">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="10b94-156">Ek PowerShell yolları kaldırmak için başvurmak [yolları](#paths) bölümü bu belgede ve kullanma yolları Kaldır `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="10b94-156">To remove the additional PowerShell paths, refer to the [paths](#paths) section in this document and remove the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="10b94-157">Bu, Homebrew ile yüklediyseniz gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="10b94-157">This is not necessary if you installed with Homebrew.</span></span>

## <a name="paths"></a><span data-ttu-id="10b94-158">Yollar</span><span class="sxs-lookup"><span data-stu-id="10b94-158">Paths</span></span>

* <span data-ttu-id="10b94-159">`$PSHOME` olduğu `/usr/local/microsoft/powershell/6.2.0/`</span><span class="sxs-lookup"><span data-stu-id="10b94-159">`$PSHOME` is `/usr/local/microsoft/powershell/6.2.0/`</span></span>
* <span data-ttu-id="10b94-160">Kullanıcı profillerini okuyabilir `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="10b94-160">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="10b94-161">Varsayılan profiller okuyabilir `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="10b94-161">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="10b94-162">Kullanıcı modülleri okuyabilir `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="10b94-162">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="10b94-163">Paylaşılan modülleri okuyabilir `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="10b94-163">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="10b94-164">Varsayılan modülleri okuyabilir `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="10b94-164">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="10b94-165">PSReadline geçmişi için kaydedilir `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="10b94-165">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="10b94-166">PowerShell'in konak başına yapılandırma profilleri uyar.</span><span class="sxs-lookup"><span data-stu-id="10b94-166">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="10b94-167">Varsayılan konak özel profil var. Bu nedenle `Microsoft.PowerShell_profile.ps1` aynı konumlarda.</span><span class="sxs-lookup"><span data-stu-id="10b94-167">So the default host-specific profile exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="10b94-168">PowerShell uyar [XDG temel dizin belirtimi] [ xdg-bds] macOS üzerinde.</span><span class="sxs-lookup"><span data-stu-id="10b94-168">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="10b94-169">MacOS bir türevi BSD, ön ek olduğundan `/usr/local` yerine kullanılan `/opt`.</span><span class="sxs-lookup"><span data-stu-id="10b94-169">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="10b94-170">Bu nedenle, `$PSHOME` olduğu `/usr/local/microsoft/powershell/6.2.0/`, ve sembolik bağlantısını yerleştirilmiş olması `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="10b94-170">So, `$PSHOME` is `/usr/local/microsoft/powershell/6.2.0/`, and the symbolic link is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="10b94-171">Ek Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="10b94-171">Additional Resources</span></span>

* <span data-ttu-id="10b94-172">[Homebrew Web][brew]</span><span class="sxs-lookup"><span data-stu-id="10b94-172">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="10b94-173">[Homebrew Github deposu][GitHub]</span><span class="sxs-lookup"><span data-stu-id="10b94-173">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="10b94-174">[Homebrew Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="10b94-174">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[Yayınları]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
