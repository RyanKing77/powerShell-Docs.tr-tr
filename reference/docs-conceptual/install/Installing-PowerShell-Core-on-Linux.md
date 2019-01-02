---
title: Linux’ta PowerShell Core yükleme
description: PowerShell Core yükleme üzerinde çeşitli Linux dağıtımları hakkında bilgi
ms.date: 08/06/2018
ms.openlocfilehash: afb11f053517af592fe42754d543f9f4a9966c5b
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405799"
---
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="c95c2-103">Linux’ta PowerShell Core yükleme</span><span class="sxs-lookup"><span data-stu-id="c95c2-103">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="c95c2-104">Destekler [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.04] [ u1804], [Ubuntu 18.10][u1810], [Debian 8][deb8], [Debian 9] [ deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [ 28 fedora][fedora], ve [Arch Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="c95c2-104">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="c95c2-105">Değil resmi olarak desteklenen Linux dağıtımları için kullanmayı deneyebilirsiniz [PowerShell Yasla paket][snap].</span><span class="sxs-lookup"><span data-stu-id="c95c2-105">For Linux distributions that are not officially supported, you can try using the [PowerShell Snap Package][snap].</span></span>
<span data-ttu-id="c95c2-106">Linux kullanarak doğrudan PowerShell ikili dosyaları dağıtmaya de deneyebilirsiniz [ `tar.gz` arşiv][tar], ancak gerekli bağımlılıkları işletim sisteminde ayrı adımları göre ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c95c2-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="c95c2-107">Tüm paketleri bizim Github'da kullanılabilir [sürümleri][] sayfası.</span><span class="sxs-lookup"><span data-stu-id="c95c2-107">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="c95c2-108">Paket yüklendikten sonra Çalıştır `pwsh` bir terminalden.</span><span class="sxs-lookup"><span data-stu-id="c95c2-108">Once the package is installed, run `pwsh` from a terminal.</span></span>

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u1804]: #ubuntu-1804
[u1810]: #ubuntu-1810
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse
[fedora]: #fedora
[arch]: #arch-linux
[snap]: #snap-package
[tar]: #binary-archives

## <a name="installing-preview-releases"></a><span data-ttu-id="c95c2-109">Önizleme sürümleri yükleme</span><span class="sxs-lookup"><span data-stu-id="c95c2-109">Installing Preview Releases</span></span>

<span data-ttu-id="c95c2-110">PowerShell Core Önizleme sürümü için Paket Deposu aracılığıyla Linux yüklerken, paket adı değişiklikleri `powershell` için `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="c95c2-110">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="c95c2-111">Doğrudan indirme ile yükleme, dosya adı dışında değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="c95c2-111">Installing via direct download does not change, other than the file name.</span></span>

<span data-ttu-id="c95c2-112">Çeşitli paket yöneticilerini kullanarak kararlı ve önizleme paketleri yüklemek için komut tablosu şu şekildedir:</span><span class="sxs-lookup"><span data-stu-id="c95c2-112">Here is a table of the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="c95c2-113">Distribution(s)</span><span class="sxs-lookup"><span data-stu-id="c95c2-113">Distribution(s)</span></span>|<span data-ttu-id="c95c2-114">Kararlı komutu</span><span class="sxs-lookup"><span data-stu-id="c95c2-114">Stable Command</span></span> | <span data-ttu-id="c95c2-115">Önizleme komutu</span><span class="sxs-lookup"><span data-stu-id="c95c2-115">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="c95c2-116">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="c95c2-116">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="c95c2-117">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="c95c2-117">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="c95c2-118">Fedora</span><span class="sxs-lookup"><span data-stu-id="c95c2-118">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a><span data-ttu-id="c95c2-119">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="c95c2-119">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="c95c2-120">Paket Deposu - Ubuntu 14.04 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="c95c2-120">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="c95c2-121">Linux için PowerShell Core, paket depolarınızın kolay yükleme (ve güncelleştirmeleri) için yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="c95c2-121">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="c95c2-122">Bu tercih edilen yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="c95c2-122">This is the preferred method.</span></span>

```sh
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/14.04/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="c95c2-123">Süper kullanıcı Microsoft depoya kaydedin.</span><span class="sxs-lookup"><span data-stu-id="c95c2-123">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="c95c2-124">Daha sonra kullanmanız yeterlidir `sudo apt-get upgrade powershell` yüklemesini güncelleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="c95c2-124">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="c95c2-125">Doğrudan indirme - Ubuntu 14.04 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="c95c2-125">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="c95c2-126">Debian paketi indirin `powershell_6.1.0-1.ubuntu.14.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="c95c2-126">Download the Debian package `powershell_6.1.0-1.ubuntu.14.04_amd64.deb`</span></span>
<span data-ttu-id="c95c2-127">gelen [sürümleri][] Ubuntu makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="c95c2-127">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="c95c2-128">Ardından aşağıdakileri terminalde yürütün:</span><span class="sxs-lookup"><span data-stu-id="c95c2-128">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="c95c2-129">`dpkg -i` Komutu karşılaşılmamış bağımlılıklarıyla birlikte başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="c95c2-129">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="c95c2-130">Sonraki komut `apt-get install -f` PowerShell paketi Yapılandırma tamamlandıktan sonra bu sorunları giderir.</span><span class="sxs-lookup"><span data-stu-id="c95c2-130">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="c95c2-131">Kaldırma - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="c95c2-131">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="c95c2-132">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="c95c2-132">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="c95c2-133">Paket Deposu - Ubuntu 16.04 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="c95c2-133">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="c95c2-134">Linux için PowerShell Core, paket depolarınızın kolay yükleme (ve güncelleştirmeleri) için yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="c95c2-134">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="c95c2-135">Bu tercih edilen yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="c95c2-135">This is the preferred method.</span></span>

```sh
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="c95c2-136">Microsoft depo süper kullanıcı bir kez kaydolduktan sonra daha sonra kullanmanız yeterlidir `sudo apt-get upgrade powershell` güncelleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="c95c2-136">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="c95c2-137">Doğrudan indirme - Ubuntu 16.04 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="c95c2-137">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="c95c2-138">Debian paketi indirin `powershell_6.1.0-1.ubuntu.16.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="c95c2-138">Download the Debian package `powershell_6.1.0-1.ubuntu.16.04_amd64.deb`</span></span>
<span data-ttu-id="c95c2-139">gelen [sürümleri][] Ubuntu makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="c95c2-139">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="c95c2-140">Ardından aşağıdakileri terminalde yürütün:</span><span class="sxs-lookup"><span data-stu-id="c95c2-140">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="c95c2-141">`dpkg -i` Komutu karşılaşılmamış bağımlılıklarıyla birlikte başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="c95c2-141">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="c95c2-142">Sonraki komut `apt-get install -f` PowerShell paketi Yapılandırma tamamlandıktan sonra bu sorunları giderir.</span><span class="sxs-lookup"><span data-stu-id="c95c2-142">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="c95c2-143">Kaldırma - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="c95c2-143">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="c95c2-144">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="c95c2-144">Ubuntu 18.04</span></span>

> [!NOTE]
> <span data-ttu-id="c95c2-145">Sonra Ubuntu 18.04 desteği eklendi `6.1.0-preview.2`</span><span class="sxs-lookup"><span data-stu-id="c95c2-145">Support for Ubuntu 18.04 was added after `6.1.0-preview.2`</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="c95c2-146">Paket Deposu - Ubuntu 18.04 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="c95c2-146">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="c95c2-147">Linux için PowerShell Core, paket depolarınızın kolay yükleme (ve güncelleştirmeleri) için yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="c95c2-147">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="c95c2-148">Bu tercih edilen yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="c95c2-148">This is the preferred method.</span></span>

```sh
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="c95c2-149">Microsoft depo süper kullanıcı bir kez kaydolduktan sonra daha sonra kullanmanız yeterlidir `sudo apt-get upgrade powershell` güncelleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="c95c2-149">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="c95c2-150">Doğrudan indirme - Ubuntu 18.04 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="c95c2-150">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="c95c2-151">Debian paketi indirin `powershell_6.1.0-1.ubuntu.18.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="c95c2-151">Download the Debian package `powershell_6.1.0-1.ubuntu.18.04_amd64.deb`</span></span>
<span data-ttu-id="c95c2-152">gelen [sürümleri][] Ubuntu makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="c95c2-152">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="c95c2-153">Ardından aşağıdakileri terminalde yürütün:</span><span class="sxs-lookup"><span data-stu-id="c95c2-153">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="c95c2-154">`dpkg -i` Komutu karşılaşılmamış bağımlılıklarıyla birlikte başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="c95c2-154">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="c95c2-155">Sonraki komut `apt-get install -f` PowerShell paketi Yapılandırma tamamlandıktan sonra bu sorunları giderir.</span><span class="sxs-lookup"><span data-stu-id="c95c2-155">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="c95c2-156">Kaldırma - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="c95c2-156">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="c95c2-157">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="c95c2-157">Ubuntu 18.10</span></span>

> [!NOTE]
> <span data-ttu-id="c95c2-158">Ubuntu 18.10 desteği sonra eklenen `6.1.0-preview.3`.</span><span class="sxs-lookup"><span data-stu-id="c95c2-158">Support for Ubuntu 18.10 was added after `6.1.0-preview.3`.</span></span>
> <span data-ttu-id="c95c2-159">18.10 günlük bir derleme olduğundan, yalnızca desteklenen topluluk var.</span><span class="sxs-lookup"><span data-stu-id="c95c2-159">As 18.10 is a daily build, it is only community supported.</span></span>

<span data-ttu-id="c95c2-160">Üzerinde 18.10 yükleme aracılığıyla desteklenir `snapd`.</span><span class="sxs-lookup"><span data-stu-id="c95c2-160">Installing on 18.10 is supported via `snapd`.</span></span> <span data-ttu-id="c95c2-161">Bkz: [Yasla paket] [ snap] için tam yönergeler;</span><span class="sxs-lookup"><span data-stu-id="c95c2-161">See [Snap Package][snap] for full instructions;</span></span>

## <a name="debian-8"></a><span data-ttu-id="c95c2-162">Debian 8</span><span class="sxs-lookup"><span data-stu-id="c95c2-162">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="c95c2-163">Paket Deposu - Debian 8 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="c95c2-163">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="c95c2-164">Linux için PowerShell Core, paket depolarınızın kolay yükleme (ve güncelleştirmeleri) için yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="c95c2-164">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="c95c2-165">Bu tercih edilen yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="c95c2-165">This is the preferred method.</span></span>

```sh
# Install system components
sudo apt-get update
sudo apt-get install curl apt-transport-https

# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Product feed
sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-jessie-prod jessie main" > /etc/apt/sources.list.d/microsoft.list'

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="c95c2-166">Microsoft depo süper kullanıcı bir kez kaydolduktan sonra daha sonra kullanmanız yeterlidir `sudo apt-get upgrade powershell` güncelleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="c95c2-166">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="c95c2-167">Doğrudan indirme - Debian 8 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="c95c2-167">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="c95c2-168">Debian paketi indirin `powershell_6.1.0-1.debian.8_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="c95c2-168">Download the Debian package `powershell_6.1.0-1.debian.8_amd64.deb`</span></span>
<span data-ttu-id="c95c2-169">gelen [sürümleri][] Debian makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="c95c2-169">from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="c95c2-170">Ardından aşağıdakileri terminalde yürütün:</span><span class="sxs-lookup"><span data-stu-id="c95c2-170">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="c95c2-171">`dpkg -i` Komutu karşılaşılmamış bağımlılıklarıyla birlikte başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="c95c2-171">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="c95c2-172">Sonraki komut `apt-get install -f` PowerShell paketi Yapılandırma tamamlandıktan sonra bu sorunları giderir.</span><span class="sxs-lookup"><span data-stu-id="c95c2-172">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="c95c2-173">Kaldırma - Debian 8</span><span class="sxs-lookup"><span data-stu-id="c95c2-173">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="c95c2-174">Debian 9</span><span class="sxs-lookup"><span data-stu-id="c95c2-174">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="c95c2-175">Paket Deposu - Debian 9 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="c95c2-175">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="c95c2-176">Linux için PowerShell Core, paket depolarınızın kolay yükleme (ve güncelleştirmeleri) için yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="c95c2-176">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="c95c2-177">Bu tercih edilen yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="c95c2-177">This is the preferred method.</span></span>

```sh
# Install system components
sudo apt-get update
sudo apt-get install curl gnupg apt-transport-https

# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Product feed
sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch main" > /etc/apt/sources.list.d/microsoft.list'

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="c95c2-178">Microsoft depo süper kullanıcı bir kez kaydolduktan sonra daha sonra kullanmanız yeterlidir `sudo apt-get upgrade powershell` güncelleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="c95c2-178">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="c95c2-179">Doğrudan indirme - Debian 9 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="c95c2-179">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="c95c2-180">Debian paketi indirin `powershell_6.1.0-1.debian.9_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="c95c2-180">Download the Debian package `powershell_6.1.0-1.debian.9_amd64.deb`</span></span>
<span data-ttu-id="c95c2-181">gelen [sürümleri][] Debian makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="c95c2-181">from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="c95c2-182">Ardından aşağıdakileri terminalde yürütün:</span><span class="sxs-lookup"><span data-stu-id="c95c2-182">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="c95c2-183">Kaldırma - Debian 9</span><span class="sxs-lookup"><span data-stu-id="c95c2-183">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="c95c2-184">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="c95c2-184">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="c95c2-185">Bu paket, Oracle Linux 7'de de çalışır.</span><span class="sxs-lookup"><span data-stu-id="c95c2-185">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="c95c2-186">Paket (tercih edilir) - deposu CentOS 7 ile yükleme</span><span class="sxs-lookup"><span data-stu-id="c95c2-186">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="c95c2-187">Linux için PowerShell Core, resmi Microsoft depolara kolay yükleme (ve güncelleştirmeleri) için yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="c95c2-187">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="c95c2-188">Microsoft depo süper kullanıcı bir kez kaydolduktan sonra kullanmak yeterlidir `sudo yum update powershell` PowerShell güncelleştirilecek.</span><span class="sxs-lookup"><span data-stu-id="c95c2-188">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="c95c2-189">Doğrudan indirme - CentOS 7 ile yükleme</span><span class="sxs-lookup"><span data-stu-id="c95c2-189">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="c95c2-190">Kullanarak [CentOS 7][], RPM paketini indirme `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="c95c2-190">Using [CentOS 7][], download the RPM package `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="c95c2-191">gelen [sürümleri][] CentOS makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="c95c2-191">from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="c95c2-192">Ardından aşağıdakileri terminalde yürütün:</span><span class="sxs-lookup"><span data-stu-id="c95c2-192">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="c95c2-193">RPM karşıdan ara adım olmadan da yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c95c2-193">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="c95c2-194">Kaldırma - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="c95c2-194">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="c95c2-196">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="c95c2-196">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="c95c2-197">Paket (tercih edilir) - deposu Red Hat Enterprise Linux (RHEL) 7 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="c95c2-197">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="c95c2-198">Linux için PowerShell Core, resmi Microsoft depolara kolay yükleme (ve güncelleştirmeleri) için yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="c95c2-198">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="c95c2-199">Microsoft depo süper kullanıcı bir kez kaydolduktan sonra kullanmak yeterlidir `sudo yum update powershell` PowerShell güncelleştirilecek.</span><span class="sxs-lookup"><span data-stu-id="c95c2-199">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="c95c2-200">Doğrudan indirme - Red Hat Enterprise Linux (RHEL) 7 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="c95c2-200">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="c95c2-201">RPM paketini indirme `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="c95c2-201">Download the RPM package `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="c95c2-202">gelen [sürümleri][] Red Hat Enterprise Linux makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="c95c2-202">from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="c95c2-203">Ardından aşağıdakileri terminalde yürütün:</span><span class="sxs-lookup"><span data-stu-id="c95c2-203">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="c95c2-204">RPM karşıdan ara adım olmadan da yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c95c2-204">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="c95c2-205">Kaldırma - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="c95c2-205">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="c95c2-206">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="c95c2-206">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="c95c2-207">Yükleme - openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="c95c2-207">Installation - openSUSE 42.3</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar libicu52_1

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/6.1.0

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.1.0

# Set execute permissions
chmod +x /opt/microsoft/powershell/6.1.0/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/6.1.0/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="c95c2-208">Yükleme - openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="c95c2-208">Installation - openSUSE Leap 15</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar gzip libopenssl1_0_0 libicu60_2

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/6.1.0

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.1.0

# Set execute permissions
chmod +x /opt/microsoft/powershell/6.1.0/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/6.1.0/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="c95c2-209">Kaldırma - openSUSE 42.3, openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="c95c2-209">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="c95c2-210">Fedora</span><span class="sxs-lookup"><span data-stu-id="c95c2-210">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="c95c2-211">28 fedora yalnızca PowerShell Core 6.1 ve üzeri sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="c95c2-211">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="c95c2-212">Paket (tercih edilir) - deposu Fedora 27 Fedora 28 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="c95c2-212">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="c95c2-213">Linux için PowerShell Core, resmi Microsoft depolara kolay yükleme (ve güncelleştirmeleri) için yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="c95c2-213">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Update the list of products
sudo dnf update

# Install a system component
sudo dnf install compat-openssl10

# Install PowerShell
sudo dnf install -y powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="c95c2-214">Doğrudan indirme - 27 Fedora, Fedora 28 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="c95c2-214">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="c95c2-215">RPM paketini indirme `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="c95c2-215">Download the RPM package `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="c95c2-216">gelen [sürümleri][] Fedora makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="c95c2-216">from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="c95c2-217">Ardından aşağıdakileri terminalde yürütün:</span><span class="sxs-lookup"><span data-stu-id="c95c2-217">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="c95c2-218">RPM karşıdan ara adım olmadan da yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c95c2-218">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="c95c2-219">Kaldırma - 27, Fedora Fedora 28</span><span class="sxs-lookup"><span data-stu-id="c95c2-219">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="c95c2-220">Linux arch</span><span class="sxs-lookup"><span data-stu-id="c95c2-220">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="c95c2-221">Deneysel yay desteği.</span><span class="sxs-lookup"><span data-stu-id="c95c2-221">Arch support is experimental.</span></span>

<span data-ttu-id="c95c2-222">PowerShell kullanılabilir [Arch Linux][] kullanıcı deposu (AUR).</span><span class="sxs-lookup"><span data-stu-id="c95c2-222">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="c95c2-223">İle derlenebilir [en son sürümü etiketlendi][arch-release]</span><span class="sxs-lookup"><span data-stu-id="c95c2-223">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="c95c2-224">Gelen derlenebilir [ana son kaydetme][arch-git]</span><span class="sxs-lookup"><span data-stu-id="c95c2-224">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="c95c2-225">Kullanılarak yüklenebilir [ikili en son sürüm][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="c95c2-225">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="c95c2-226">AUR paketlerinde saklanır topluluk - resmi desteği yoktur.</span><span class="sxs-lookup"><span data-stu-id="c95c2-226">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="c95c2-227">AUR paketlerini yükleme hakkında daha fazla bilgi için bkz: [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) veya topluluk [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="c95c2-227">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="c95c2-229">Paket Yasla</span><span class="sxs-lookup"><span data-stu-id="c95c2-229">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="c95c2-230">Snapd alma</span><span class="sxs-lookup"><span data-stu-id="c95c2-230">Getting snapd</span></span>

<span data-ttu-id="c95c2-231">`snapd` yaslar çalıştırmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c95c2-231">`snapd` is required to run snaps.</span></span>
<span data-ttu-id="c95c2-232">Kullanım [bu yönergeleri](https://docs.snapcraft.io/core/install) sahip olduğunuzdan emin olmak için `snapd` yüklü.</span><span class="sxs-lookup"><span data-stu-id="c95c2-232">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="c95c2-233">Ek bileşeni aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="c95c2-233">Installation via Snap</span></span>

<span data-ttu-id="c95c2-234">Linux için PowerShell Core yayımlanmıştır [ek depolama](https://snapcraft.io/store) kolay yükleme (ve güncelleştirmeleri).</span><span class="sxs-lookup"><span data-stu-id="c95c2-234">PowerShell Core, for Linux, is published to the [Snap store](https://snapcraft.io/store) for easy installation (and updates).</span></span>
<span data-ttu-id="c95c2-235">Bu tercih edilen yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="c95c2-235">This is the preferred method.</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="c95c2-236">Önizleme sürümünü yüklemek istiyorsanız, yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="c95c2-236">If you want to install preview version, use following method.</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="c95c2-237">Sonra ek yükleme otomatik olarak yükseltecek, ancak bir yükseltme kullanarak tetikleyebilirsiniz `sudo snap refresh powershell` veya `sudo snap refresh powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="c95c2-237">After installing Snap will automatically upgrade, but you can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="c95c2-238">Kaldırma</span><span class="sxs-lookup"><span data-stu-id="c95c2-238">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="c95c2-239">veya</span><span class="sxs-lookup"><span data-stu-id="c95c2-239">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="c95c2-240">Kali</span><span class="sxs-lookup"><span data-stu-id="c95c2-240">Kali</span></span>

### <a name="installation---kali"></a><span data-ttu-id="c95c2-241">Yükleme - Kali</span><span class="sxs-lookup"><span data-stu-id="c95c2-241">Installation - Kali</span></span>

```sh
# Download & Install prerequisites
wget http://ftp.us.debian.org/debian/pool/main/i/icu/libicu57_57.1-9_amd64.deb
dpkg -i libicu57_57.1-9_amd64.deb
apt-get update && apt-get install -y curl gnupg apt-transport-https

# Add Microsoft public repository key to APT
curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -

# Add Microsoft package repository to the source list
echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch main" | tee /etc/apt/sources.list.d/powershell.list

# Install PowerShell package
apt-get update && apt-get install -y powershell

# Start PowerShell
pwsh
```

### <a name="uninstallation---kali"></a><span data-ttu-id="c95c2-242">Kaldırma - Kali</span><span class="sxs-lookup"><span data-stu-id="c95c2-242">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt-get remove -y powershell
```

## <a name="raspbian"></a><span data-ttu-id="c95c2-243">Raspbian</span><span class="sxs-lookup"><span data-stu-id="c95c2-243">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="c95c2-244">Deneysel Raspbian desteği.</span><span class="sxs-lookup"><span data-stu-id="c95c2-244">Raspbian support is experimental.</span></span>

<span data-ttu-id="c95c2-245">Şu anda PowerShell yalnızca Raspbian Esnetme üzerinde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="c95c2-245">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="c95c2-246">Ayrıca CoreCLR (ve bu nedenle PowerShell Core) yalnızca Pi 2 ve Pi 3 cihazlarında diğer cihazlar gibi çalışır [Pi sıfır](https://github.com/dotnet/coreclr/issues/10605), desteklenmeyen bir işlemciye sahip.</span><span class="sxs-lookup"><span data-stu-id="c95c2-246">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="c95c2-247">İndirme [Raspbian Esnetme](https://www.raspberrypi.org/downloads/raspbian/) izleyin [yükleme yönergeleri](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) Pi'yi almak için.</span><span class="sxs-lookup"><span data-stu-id="c95c2-247">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="c95c2-248">Yükleme - Raspbian</span><span class="sxs-lookup"><span data-stu-id="c95c2-248">Installation - Raspbian</span></span>

```sh
# Install prerequisites
sudo apt-get install libunwind8

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.1.0-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

<span data-ttu-id="c95c2-249">İsteğe bağlı olarak PowerShell "pwsh" ikili yol belirtmeden başlatabilmeniz için bir sembolik bağlantı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c95c2-249">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="c95c2-250">Kaldırma - Raspbian</span><span class="sxs-lookup"><span data-stu-id="c95c2-250">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="c95c2-251">İkili Arşivi</span><span class="sxs-lookup"><span data-stu-id="c95c2-251">Binary Archives</span></span>

<span data-ttu-id="c95c2-252">PowerShell ikili `tar.gz` arşivleri gelişmiş dağıtım senaryoları etkinleştirmek Linux platformlar için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="c95c2-252">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="c95c2-253">Bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="c95c2-253">Dependencies</span></span>

<span data-ttu-id="c95c2-254">PowerShell tüm Linux dağıtımları için taşınabilir ikili dosyaları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c95c2-254">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="c95c2-255">Ancak farklı bağımlılıklara farklı dağıtımlar üzerinde .NET Core çalışma zamanı gerektirir ve bu nedenle aynı PowerShell yapar.</span><span class="sxs-lookup"><span data-stu-id="c95c2-255">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="c95c2-256">Aşağıdaki tabloda farklı Linux dağıtımlarında resmi olarak desteklenen .NET Core 2.0 bağımlılıkları gösterir.</span><span class="sxs-lookup"><span data-stu-id="c95c2-256">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="c95c2-257">İşletim sistemi</span><span class="sxs-lookup"><span data-stu-id="c95c2-257">OS</span></span>                 | <span data-ttu-id="c95c2-258">Bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="c95c2-258">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="c95c2-259">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="c95c2-259">Ubuntu 14.04</span></span>       | <span data-ttu-id="c95c2-260">libc6, libgcc1, libgssapi-krb5-2 liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="c95c2-260">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="c95c2-261">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="c95c2-261">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="c95c2-262">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="c95c2-262">Ubuntu 16.04</span></span>       | <span data-ttu-id="c95c2-263">libc6, libgcc1, libgssapi-krb5-2 liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="c95c2-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="c95c2-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="c95c2-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="c95c2-265">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="c95c2-265">Ubuntu 17.10</span></span>       | <span data-ttu-id="c95c2-266">libc6, libgcc1, libgssapi-krb5-2 liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="c95c2-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="c95c2-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="c95c2-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="c95c2-268">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="c95c2-268">Ubuntu 18.04</span></span>       | <span data-ttu-id="c95c2-269">libc6, libgcc1, libgssapi-krb5-2 liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="c95c2-269">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="c95c2-270">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="c95c2-270">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="c95c2-271">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="c95c2-271">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="c95c2-272">libc6, libgcc1, libgssapi-krb5-2 liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="c95c2-272">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="c95c2-273">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="c95c2-273">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="c95c2-274">Debian 9 (Esnetme)</span><span class="sxs-lookup"><span data-stu-id="c95c2-274">Debian 9 (Stretch)</span></span> | <span data-ttu-id="c95c2-275">libc6, libgcc1, libgssapi-krb5-2 liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="c95c2-275">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="c95c2-276">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="c95c2-276">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="c95c2-277">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="c95c2-277">CentOS 7</span></span> <br> <span data-ttu-id="c95c2-278">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="c95c2-278">Oracle Linux 7</span></span> <br> <span data-ttu-id="c95c2-279">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="c95c2-279">RHEL 7</span></span> | <span data-ttu-id="c95c2-280">libunwind, libcurl, openssl kitaplıkları, libicu</span><span class="sxs-lookup"><span data-stu-id="c95c2-280">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="c95c2-281">OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="c95c2-281">openSUSE 42.3</span></span> | <span data-ttu-id="c95c2-282">libcurl4, libopenssl1_0_0, libicu52_1</span><span class="sxs-lookup"><span data-stu-id="c95c2-282">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="c95c2-283">openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="c95c2-283">openSUSE Leap 15</span></span> | <span data-ttu-id="c95c2-284">libcurl4, libopenssl1_0_0, libicu60_2</span><span class="sxs-lookup"><span data-stu-id="c95c2-284">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="c95c2-285">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="c95c2-285">Fedora 27</span></span> <br> <span data-ttu-id="c95c2-286">28 fedora</span><span class="sxs-lookup"><span data-stu-id="c95c2-286">Fedora 28</span></span> | <span data-ttu-id="c95c2-287">libunwind, libcurl, openssl kitaplıkları, libicu, compat openssl10</span><span class="sxs-lookup"><span data-stu-id="c95c2-287">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="c95c2-288">Resmi olarak desteklenmez Linux dağıtımlarında PowerShell ikili dosyaları dağıtmak için ayrı adımları hedef işletim sistemi için gerekli bağımlılıkları yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c95c2-288">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="c95c2-289">Örneğin, bizim [Amazon Linux dockerfile] [ amazon-dockerfile] ilk bağımlılıkları yükler ve ardından Linux ayıklar `tar.gz` arşiv.</span><span class="sxs-lookup"><span data-stu-id="c95c2-289">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="c95c2-290">Yükleme - ikili Arşivi</span><span class="sxs-lookup"><span data-stu-id="c95c2-290">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="c95c2-291">Linux</span><span class="sxs-lookup"><span data-stu-id="c95c2-291">Linux</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/6.1.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.1.0

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/6.1.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/6.1.0/pwsh /usr/bin/pwsh
```

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="c95c2-292">Kaldırma ikili Arşivi</span><span class="sxs-lookup"><span data-stu-id="c95c2-292">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="c95c2-293">Yollar</span><span class="sxs-lookup"><span data-stu-id="c95c2-293">Paths</span></span>

* <span data-ttu-id="c95c2-294">`$PSHOME` olduğu `/opt/microsoft/powershell/6.1.0/`</span><span class="sxs-lookup"><span data-stu-id="c95c2-294">`$PSHOME` is `/opt/microsoft/powershell/6.1.0/`</span></span>
* <span data-ttu-id="c95c2-295">Kullanıcı profillerini okuyabilir `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="c95c2-295">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="c95c2-296">Varsayılan profiller okuyabilir `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="c95c2-296">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="c95c2-297">Kullanıcı modülleri okuyabilir `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="c95c2-297">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="c95c2-298">Paylaşılan modülleri okuyabilir `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="c95c2-298">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="c95c2-299">Varsayılan modülleri okuyabilir `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="c95c2-299">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="c95c2-300">PSReadline geçmişi için kaydedilir `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="c95c2-300">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="c95c2-301">Varsayılan konak özel profilleri var Bu nedenle, PowerShell'in konak başına yapılandırma profilleri dikkate `Microsoft.PowerShell_profile.ps1` aynı konumlarda.</span><span class="sxs-lookup"><span data-stu-id="c95c2-301">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="c95c2-302">PowerShell uyar [XDG temel dizin belirtimi] [ xdg-bds] Linux üzerinde.</span><span class="sxs-lookup"><span data-stu-id="c95c2-302">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[sürümleri]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
