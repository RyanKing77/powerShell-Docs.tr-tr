---
title: MacOS’ta PowerShell Core yükleme
description: Macos'ta PowerShell Core yükleme hakkında bilgi
ms.date: 12/12/2018
ms.openlocfilehash: 91e64cace7d4ed988da56109dde9bf2a80528eb4
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405772"
---
# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="9e0dc-103">MacOS’ta PowerShell Core yükleme</span><span class="sxs-lookup"><span data-stu-id="9e0dc-103">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="9e0dc-104">PowerShell Core macOS 10.12 ve üstünü destekler.</span><span class="sxs-lookup"><span data-stu-id="9e0dc-104">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="9e0dc-105">Tüm paketleri bizim Github'da kullanılabilir [sürümleri][] sayfası.</span><span class="sxs-lookup"><span data-stu-id="9e0dc-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="9e0dc-106">Paket yüklendikten sonra çalıştırın `pwsh` bir terminalden.</span><span class="sxs-lookup"><span data-stu-id="9e0dc-106">After the package is installed, run `pwsh` from a terminal.</span></span>

## <a name="about-brew"></a><span data-ttu-id="9e0dc-107">Brew hakkında</span><span class="sxs-lookup"><span data-stu-id="9e0dc-107">About Brew</span></span>

<span data-ttu-id="9e0dc-108">[Homebrew] [ brew] macOS için tercih edilen bir paket yöneticisidir.</span><span class="sxs-lookup"><span data-stu-id="9e0dc-108">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="9e0dc-109">Varsa `brew` komutu bulunamazsa, Homebrew aşağıdakileri yüklemeniz gerekir [kendi yönergeleri][brew].</span><span class="sxs-lookup"><span data-stu-id="9e0dc-109">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="9e0dc-110">Homebrew aracılığıyla en son kararlı sürüm MacOS 10.12 veya üzeri yüklemesi</span><span class="sxs-lookup"><span data-stu-id="9e0dc-110">Installation of latest stable release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="9e0dc-111">Bkz: [hakkında Brew](#about-brew) Brew hakkında bilgi için.</span><span class="sxs-lookup"><span data-stu-id="9e0dc-111">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="9e0dc-112">Şimdi, PowerShell'i yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9e0dc-112">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="9e0dc-113">Son olarak, yükleme işleminiz düzgün çalıştığını doğrulayın:</span><span class="sxs-lookup"><span data-stu-id="9e0dc-113">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="9e0dc-114">PowerShell'in yeni sürümü yayımlandığında, Homebrew'ın formüllerini güncelleştirin ve PowerShell yükseltme:</span><span class="sxs-lookup"><span data-stu-id="9e0dc-114">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="9e0dc-115">Yukarıdaki komutlar içindeki bir PowerShell (pwsh) ana çağrılabilir, ancak daha sonra PowerShell Kabuk çıkıldı ve gereken yükseltmesini tamamladıktan sonra gösterilen değerleri yenileme için bilgisayarınızın yeniden başlatılması `$PSVersionTable`.</span><span class="sxs-lookup"><span data-stu-id="9e0dc-115">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in `$PSVersionTable`.</span></span>

[brew]: http://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="9e0dc-116">En son Önizleme yüklenmesini Homebrew macOS 10.12 ya da daha yüksek sürüm</span><span class="sxs-lookup"><span data-stu-id="9e0dc-116">Installation of latest preview release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="9e0dc-117">Bkz: [hakkında Brew](#about-brew) Brew hakkında bilgi için.</span><span class="sxs-lookup"><span data-stu-id="9e0dc-117">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="9e0dc-118">Homebrew yükledikten sonra PowerShell'i yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e0dc-118">After you've installed Homebrew, you can install PowerShell.</span></span>
<span data-ttu-id="9e0dc-119">İlk olarak, yükleme [Cask sürümleri] [ cask-versions] cask paketlerin diğer sürümlerini yüklemenize olanak sağlayan paket:</span><span class="sxs-lookup"><span data-stu-id="9e0dc-119">First, install the [Cask-Versions][cask-versions] package that lets you install alternative versions of cask packages:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="9e0dc-120">Şimdi, PowerShell'i yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9e0dc-120">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="9e0dc-121">Son olarak, yükleme işleminiz düzgün çalıştığını doğrulayın:</span><span class="sxs-lookup"><span data-stu-id="9e0dc-121">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="9e0dc-122">PowerShell'in yeni sürümü yayımlandığında, Homebrew'ın formüllerini güncelleştirin ve PowerShell yükseltme:</span><span class="sxs-lookup"><span data-stu-id="9e0dc-122">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="9e0dc-123">Yukarıdaki komutlar içindeki bir PowerShell (pwsh) ana çağrılabilir, ancak daha sonra PowerShell Kabuk çıkıldı ve gerekir yükseltmeyi tamamlamak için bilgisayarınızın yeniden başlatılması.</span><span class="sxs-lookup"><span data-stu-id="9e0dc-123">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="9e0dc-124">ve gösterilen değerleri yenileme `$PSVersionTable`.</span><span class="sxs-lookup"><span data-stu-id="9e0dc-124">and refresh the values shown in `$PSVersionTable`.</span></span>

## <a name="installation-via-direct-download"></a><span data-ttu-id="9e0dc-125">Doğrudan indirme ile yükleme</span><span class="sxs-lookup"><span data-stu-id="9e0dc-125">Installation via Direct Download</span></span>

<span data-ttu-id="9e0dc-126">PKG paketini indirme `powershell-6.1.0-osx-x64.pkg`</span><span class="sxs-lookup"><span data-stu-id="9e0dc-126">Download the PKG package `powershell-6.1.0-osx-x64.pkg`</span></span>
<span data-ttu-id="9e0dc-127">gelen [sürümleri][] macOS makinenizde sayfaya.</span><span class="sxs-lookup"><span data-stu-id="9e0dc-127">from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="9e0dc-128">Dosyaya çift tıklayın ve yönergeleri izleyin veya terminalden yükleyin:</span><span class="sxs-lookup"><span data-stu-id="9e0dc-128">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.1.0-osx-x64.pkg -target /
```

<span data-ttu-id="9e0dc-129">Yükleme [OpenSSL](#install-openssl).</span><span class="sxs-lookup"><span data-stu-id="9e0dc-129">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="9e0dc-130">OpenSSL PowerShell uzaktan iletişim ve CIM işlemleri için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="9e0dc-130">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="9e0dc-131">İkili Arşivi</span><span class="sxs-lookup"><span data-stu-id="9e0dc-131">Binary Archives</span></span>

<span data-ttu-id="9e0dc-132">PowerShell ikili `tar.gz` arşivleri gelişmiş dağıtım senaryoları etkinleştirmek macOS platformu için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="9e0dc-132">PowerShell binary `tar.gz` archives are provided for the macOS platform to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="9e0dc-133">Macos'ta yükleme ikili Arşivi</span><span class="sxs-lookup"><span data-stu-id="9e0dc-133">Installing binary archives on macOS</span></span>

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

<span data-ttu-id="9e0dc-134">Yükleme [OpenSSL](#install-openssl).</span><span class="sxs-lookup"><span data-stu-id="9e0dc-134">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="9e0dc-135">OpenSSL PowerShell uzaktan iletişim ve CIM işlemleri için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="9e0dc-135">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="installing-dependencies"></a><span data-ttu-id="9e0dc-136">Bağımlılıklar yükleniyor</span><span class="sxs-lookup"><span data-stu-id="9e0dc-136">Installing dependencies</span></span>

### <a name="install-xcode-command-line-tools"></a><span data-ttu-id="9e0dc-137">XCode komut satırı araçlarını yükleme</span><span class="sxs-lookup"><span data-stu-id="9e0dc-137">Install XCode command-line tools</span></span>

```sh
xcode-select --install
```

### <a name="install-openssl"></a><span data-ttu-id="9e0dc-138">OpenSSL yükleyin</span><span class="sxs-lookup"><span data-stu-id="9e0dc-138">Install OpenSSL</span></span>

<span data-ttu-id="9e0dc-139">OpenSSL PowerShell uzaktan iletişim ve CIM işlemleri için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="9e0dc-139">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span> <span data-ttu-id="9e0dc-140">Yükleyebileceğiniz MacPorts veya Brew aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="9e0dc-140">You can install via MacPorts or Brew.</span></span>

#### <a name="install-openssl-via-brew"></a><span data-ttu-id="9e0dc-141">OpenSSL Brew aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="9e0dc-141">Install OpenSSL via Brew</span></span>

<span data-ttu-id="9e0dc-142">Bkz: [hakkında Brew](#about-brew) Brew hakkında bilgi için.</span><span class="sxs-lookup"><span data-stu-id="9e0dc-142">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="9e0dc-143">OpenSSL yüklemek için çalıştırın `brew install openssl`.</span><span class="sxs-lookup"><span data-stu-id="9e0dc-143">To install OpenSSL, run `brew install openssl`.</span></span>

#### <a name="install-openssl-via-macports"></a><span data-ttu-id="9e0dc-144">OpenSSL MacPorts aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="9e0dc-144">Install OpenSSL via MacPorts</span></span>

1. <span data-ttu-id="9e0dc-145">Yükleme [XCode komut satırı araçları](#install-xcode-command-line-tools).</span><span class="sxs-lookup"><span data-stu-id="9e0dc-145">Install the [XCode command line tools](#install-xcode-command-line-tools).</span></span>
1. <span data-ttu-id="9e0dc-146">MacPorts yükleyin.</span><span class="sxs-lookup"><span data-stu-id="9e0dc-146">Install MacPorts.</span></span>
   <span data-ttu-id="9e0dc-147">Yönergelere ihtiyacınız varsa, başvurmak [Yükleme Kılavuzu](https://guide.macports.org/chunked/installing.macports.html).</span><span class="sxs-lookup"><span data-stu-id="9e0dc-147">If you need instructions, refer to the [installation guide](https://guide.macports.org/chunked/installing.macports.html).</span></span>
1. <span data-ttu-id="9e0dc-148">Çalıştırarak MacPorts güncelleştirme `sudo port selfupdate`.</span><span class="sxs-lookup"><span data-stu-id="9e0dc-148">Update MacPorts by running `sudo port selfupdate`.</span></span>
1. <span data-ttu-id="9e0dc-149">MacPorts paketleri çalıştırarak yükseltme `sudo port upgrade outdated`.</span><span class="sxs-lookup"><span data-stu-id="9e0dc-149">Upgrade MacPorts packages by running `sudo port upgrade outdated`.</span></span>
1. <span data-ttu-id="9e0dc-150">OpenSSL çalıştırarak yükleyin `sudo port install openssl`.</span><span class="sxs-lookup"><span data-stu-id="9e0dc-150">Install OpenSSL by running `sudo port install openssl`.</span></span>
1. <span data-ttu-id="9e0dc-151">PowerShell için kullanılabilir hale getirmek kitaplıkları Bağla:</span><span class="sxs-lookup"><span data-stu-id="9e0dc-151">Link the libraries to make them available to PowerShell:</span></span>

```sh
sudo mkdir -p /usr/local/opt/openssl
sudo ln -s /opt/local/lib /usr/local/opt/openssl/lib
```

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="9e0dc-152">PowerShell Core kaldırma</span><span class="sxs-lookup"><span data-stu-id="9e0dc-152">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="9e0dc-153">PowerShell ile Homebrew yüklü değilse, kaldırmak için aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="9e0dc-153">If you installed PowerShell with Homebrew, use the following command to uninstall:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="9e0dc-154">PowerShell doğrudan indirme yüklü değilse, PowerShell el ile kaldırılması gerekir:</span><span class="sxs-lookup"><span data-stu-id="9e0dc-154">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="9e0dc-155">Ek PowerShell yolları kaldırmak için başvurmak [yolları](#paths) bölümü bu belgede ve kullanma yolları Kaldır `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="9e0dc-155">To remove the additional PowerShell paths, refer to the [paths](#paths) section in this document and remove the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="9e0dc-156">Bu, Homebrew ile yüklediyseniz gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="9e0dc-156">This is not necessary if you installed with Homebrew.</span></span>

## <a name="paths"></a><span data-ttu-id="9e0dc-157">Yollar</span><span class="sxs-lookup"><span data-stu-id="9e0dc-157">Paths</span></span>

* <span data-ttu-id="9e0dc-158">`$PSHOME` olduğu `/usr/local/microsoft/powershell/6.1.0/`</span><span class="sxs-lookup"><span data-stu-id="9e0dc-158">`$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`</span></span>
* <span data-ttu-id="9e0dc-159">Kullanıcı profillerini okuyabilir `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="9e0dc-159">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="9e0dc-160">Varsayılan profiller okuyabilir `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="9e0dc-160">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="9e0dc-161">Kullanıcı modülleri okuyabilir `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="9e0dc-161">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="9e0dc-162">Paylaşılan modülleri okuyabilir `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="9e0dc-162">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="9e0dc-163">Varsayılan modülleri okuyabilir `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="9e0dc-163">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="9e0dc-164">PSReadline geçmişi için kaydedilir `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="9e0dc-164">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="9e0dc-165">PowerShell'in konak başına yapılandırma profilleri uyar.</span><span class="sxs-lookup"><span data-stu-id="9e0dc-165">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="9e0dc-166">Varsayılan konak özel profil var. Bu nedenle `Microsoft.PowerShell_profile.ps1` aynı konumlarda.</span><span class="sxs-lookup"><span data-stu-id="9e0dc-166">So the default host-specific profile exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="9e0dc-167">PowerShell uyar [XDG temel dizin belirtimi] [ xdg-bds] macOS üzerinde.</span><span class="sxs-lookup"><span data-stu-id="9e0dc-167">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="9e0dc-168">MacOS bir türevi BSD, ön ek olduğundan `/usr/local` yerine kullanılan `/opt`.</span><span class="sxs-lookup"><span data-stu-id="9e0dc-168">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="9e0dc-169">Bu nedenle, `$PSHOME` olduğu `/usr/local/microsoft/powershell/6.1.0/`, ve sembolik bağlantısını yerleştirilmiş olması `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="9e0dc-169">So, `$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`, and the symbolic link is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="9e0dc-170">Ek Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="9e0dc-170">Additional Resources</span></span>

* <span data-ttu-id="9e0dc-171">[Homebrew Web][brew]</span><span class="sxs-lookup"><span data-stu-id="9e0dc-171">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="9e0dc-172">[Homebrew Github deposu][GitHub]</span><span class="sxs-lookup"><span data-stu-id="9e0dc-172">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="9e0dc-173">[Homebrew Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="9e0dc-173">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[sürümleri]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
