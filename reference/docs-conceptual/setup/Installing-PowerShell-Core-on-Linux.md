---
title: Linux’ta PowerShell Core yükleme
description: PowerShell Core yükleme üzerinde çeşitli Linux dağıtımları hakkında bilgi
ms.date: 08/06/2018
ms.openlocfilehash: 9abe7d9afda42478159b55f90f4de654f215682d
ms.sourcegitcommit: b235c58b34d23317076540631f5cf83f1f309c0d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45557223"
---
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="0f01a-103">Linux’ta PowerShell Core yükleme</span><span class="sxs-lookup"><span data-stu-id="0f01a-103">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="0f01a-104">Destekler [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.10] [ u18], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7] [ cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.3][opensuse], [Fedora 27 ] [ fedora], [Fedora 28][fedora], ve [Arch Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="0f01a-104">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.10][u18], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.3][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="0f01a-105">Değil resmi olarak desteklenen Linux dağıtımları için kullanmayı deneyebilirsiniz [PowerShell Yasla paket][snap].</span><span class="sxs-lookup"><span data-stu-id="0f01a-105">For Linux distributions that are not officially supported, you can try using the [PowerShell Snap Package][snap].</span></span>
<span data-ttu-id="0f01a-106">Linux kullanarak doğrudan PowerShell ikili dosyaları dağıtmaya de deneyebilirsiniz [ `tar.gz` arşiv][tar], ancak gerekli bağımlılıkları işletim sisteminde ayrı adımları göre ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0f01a-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="0f01a-107">Tüm paketleri bizim Github'da kullanılabilir [sürümleri][] sayfası.</span><span class="sxs-lookup"><span data-stu-id="0f01a-107">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="0f01a-108">Paket yüklendikten sonra Çalıştır `pwsh` bir terminalden.</span><span class="sxs-lookup"><span data-stu-id="0f01a-108">Once the package is installed, run `pwsh` from a terminal.</span></span>

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u18]: #ubuntu-1810
[u18]: #ubuntu-1804
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse-423
[fedora]: #fedora
[arch]: #arch-linux
[snap]: #snap-package
[tar]: #binary-archives

## <a name="installing-preview-releases"></a><span data-ttu-id="0f01a-109">Önizleme sürümleri yükleme</span><span class="sxs-lookup"><span data-stu-id="0f01a-109">Installing Preview Releases</span></span>

<span data-ttu-id="0f01a-110">PowerShell Core Önizleme sürümü için Paket Deposu aracılığıyla Linux yüklerken, paket adı değişiklikleri `powershell` için `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="0f01a-110">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="0f01a-111">Doğrudan indirme ile yükleme, dosya adı dışında değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="0f01a-111">Installing via direct download does not change, other than the file name.</span></span>

<span data-ttu-id="0f01a-112">Çeşitli paket yöneticilerini kullanarak kararlı ve önizleme paketleri yüklemek için komut tablosu şu şekildedir:</span><span class="sxs-lookup"><span data-stu-id="0f01a-112">Here is a table of the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="0f01a-113">Distribution(s)</span><span class="sxs-lookup"><span data-stu-id="0f01a-113">Distribution(s)</span></span>|<span data-ttu-id="0f01a-114">Kararlı komutu</span><span class="sxs-lookup"><span data-stu-id="0f01a-114">Stable Command</span></span> | <span data-ttu-id="0f01a-115">Önizleme komutu</span><span class="sxs-lookup"><span data-stu-id="0f01a-115">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="0f01a-116">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="0f01a-116">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="0f01a-117">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="0f01a-117">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="0f01a-118">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="0f01a-118">OpenSUSE</span></span> |`sudo zypper install powershell` | `sudo zypper install powershell-preview`|
| <span data-ttu-id="0f01a-119">Fedora</span><span class="sxs-lookup"><span data-stu-id="0f01a-119">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a><span data-ttu-id="0f01a-120">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="0f01a-120">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="0f01a-121">Paket Deposu - Ubuntu 14.04 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="0f01a-121">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="0f01a-122">Linux için PowerShell Core, paket depolarınızın kolay yükleme (ve güncelleştirmeleri) için yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="0f01a-122">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="0f01a-123">Bu tercih edilen yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="0f01a-123">This is the preferred method.</span></span>

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

<span data-ttu-id="0f01a-124">Süper kullanıcı Microsoft depoya kaydedin.</span><span class="sxs-lookup"><span data-stu-id="0f01a-124">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="0f01a-125">Daha sonra kullanmanız yeterlidir `sudo apt-get upgrade powershell` yüklemesini güncelleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="0f01a-125">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="0f01a-126">Doğrudan indirme - Ubuntu 14.04 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="0f01a-126">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="0f01a-127">Debian paketi indirin `powershell_6.1.0-1.ubuntu.14.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="0f01a-127">Download the Debian package `powershell_6.1.0-1.ubuntu.14.04_amd64.deb`</span></span>
<span data-ttu-id="0f01a-128">gelen [sürümleri][] Ubuntu makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="0f01a-128">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="0f01a-129">Ardından aşağıdakileri terminalde yürütün:</span><span class="sxs-lookup"><span data-stu-id="0f01a-129">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="0f01a-130">`dpkg -i` Komutu karşılaşılmamış bağımlılıklarıyla birlikte başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="0f01a-130">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="0f01a-131">Sonraki komut `apt-get install -f` PowerShell paketi Yapılandırma tamamlandıktan sonra bu sorunları giderir.</span><span class="sxs-lookup"><span data-stu-id="0f01a-131">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="0f01a-132">Kaldırma - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="0f01a-132">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="0f01a-133">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="0f01a-133">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="0f01a-134">Paket Deposu - Ubuntu 16.04 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="0f01a-134">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="0f01a-135">Linux için PowerShell Core, paket depolarınızın kolay yükleme (ve güncelleştirmeleri) için yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="0f01a-135">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="0f01a-136">Bu tercih edilen yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="0f01a-136">This is the preferred method.</span></span>

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

<span data-ttu-id="0f01a-137">Microsoft depo süper kullanıcı bir kez kaydolduktan sonra daha sonra kullanmanız yeterlidir `sudo apt-get upgrade powershell` güncelleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="0f01a-137">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="0f01a-138">Doğrudan indirme - Ubuntu 16.04 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="0f01a-138">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="0f01a-139">Debian paketi indirin `powershell_6.1.0-1.ubuntu.16.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="0f01a-139">Download the Debian package `powershell_6.1.0-1.ubuntu.16.04_amd64.deb`</span></span>
<span data-ttu-id="0f01a-140">gelen [sürümleri][] Ubuntu makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="0f01a-140">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="0f01a-141">Ardından aşağıdakileri terminalde yürütün:</span><span class="sxs-lookup"><span data-stu-id="0f01a-141">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="0f01a-142">`dpkg -i` Komutu karşılaşılmamış bağımlılıklarıyla birlikte başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="0f01a-142">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="0f01a-143">Sonraki komut `apt-get install -f` PowerShell paketi Yapılandırma tamamlandıktan sonra bu sorunları giderir.</span><span class="sxs-lookup"><span data-stu-id="0f01a-143">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="0f01a-144">Kaldırma - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="0f01a-144">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="0f01a-145">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="0f01a-145">Ubuntu 18.04</span></span>

> [!NOTE]
> <span data-ttu-id="0f01a-146">Sonra Ubuntu 18.04 desteği eklendi `6.1.0-preview.2`</span><span class="sxs-lookup"><span data-stu-id="0f01a-146">Support for Ubuntu 18.04 was added after `6.1.0-preview.2`</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="0f01a-147">Paket Deposu - Ubuntu 18.04 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="0f01a-147">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="0f01a-148">Linux için PowerShell Core, paket depolarınızın kolay yükleme (ve güncelleştirmeleri) için yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="0f01a-148">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="0f01a-149">Bu tercih edilen yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="0f01a-149">This is the preferred method.</span></span>

```sh
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell-preview

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="0f01a-150">Microsoft depo süper kullanıcı bir kez kaydolduktan sonra daha sonra kullanmanız yeterlidir `sudo apt-get upgrade powershell` güncelleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="0f01a-150">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="0f01a-151">Doğrudan indirme - Ubuntu 18.04 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="0f01a-151">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="0f01a-152">Debian paketi indirin `powershell_6.1.0-1.ubuntu.18.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="0f01a-152">Download the Debian package `powershell_6.1.0-1.ubuntu.18.04_amd64.deb`</span></span>
<span data-ttu-id="0f01a-153">gelen [sürümleri][] Ubuntu makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="0f01a-153">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="0f01a-154">Ardından aşağıdakileri terminalde yürütün:</span><span class="sxs-lookup"><span data-stu-id="0f01a-154">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="0f01a-155">`dpkg -i` Komutu karşılaşılmamış bağımlılıklarıyla birlikte başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="0f01a-155">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="0f01a-156">Sonraki komut `apt-get install -f` PowerShell paketi Yapılandırma tamamlandıktan sonra bu sorunları giderir.</span><span class="sxs-lookup"><span data-stu-id="0f01a-156">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="0f01a-157">Kaldırma - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="0f01a-157">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="0f01a-158">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="0f01a-158">Ubuntu 18.10</span></span>

> [!NOTE]
> <span data-ttu-id="0f01a-159">Ubuntu 18.10 desteği sonra eklenen `6.1.0-preview.3`.</span><span class="sxs-lookup"><span data-stu-id="0f01a-159">Support for Ubuntu 18.10 was added after `6.1.0-preview.3`.</span></span>
> <span data-ttu-id="0f01a-160">18.10 günlük bir derleme olduğundan, yalnızca desteklenen topluluk var.</span><span class="sxs-lookup"><span data-stu-id="0f01a-160">As 18.10 is a daily build, it is only community supported.</span></span>

<span data-ttu-id="0f01a-161">Üzerinde 18.10 yükleme aracılığıyla desteklenir `snapd`.</span><span class="sxs-lookup"><span data-stu-id="0f01a-161">Installing on 18.10 is supported via `snapd`.</span></span> <span data-ttu-id="0f01a-162">Bkz: [Yasla paket] [ snap] için tam yönergeler;</span><span class="sxs-lookup"><span data-stu-id="0f01a-162">See [Snap Package][snap] for full instructions;</span></span>

## <a name="debian-8"></a><span data-ttu-id="0f01a-163">Debian 8</span><span class="sxs-lookup"><span data-stu-id="0f01a-163">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="0f01a-164">Paket Deposu - Debian 8 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="0f01a-164">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="0f01a-165">Linux için PowerShell Core, paket depolarınızın kolay yükleme (ve güncelleştirmeleri) için yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="0f01a-165">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="0f01a-166">Bu tercih edilen yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="0f01a-166">This is the preferred method.</span></span>

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

<span data-ttu-id="0f01a-167">Microsoft depo süper kullanıcı bir kez kaydolduktan sonra daha sonra kullanmanız yeterlidir `sudo apt-get upgrade powershell` güncelleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="0f01a-167">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="0f01a-168">Doğrudan indirme - Debian 8 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="0f01a-168">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="0f01a-169">Debian paketi indirin `powershell_6.1.0-1.debian.8_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="0f01a-169">Download the Debian package `powershell_6.1.0-1.debian.8_amd64.deb`</span></span>
<span data-ttu-id="0f01a-170">gelen [sürümleri][] Debian makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="0f01a-170">from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="0f01a-171">Ardından aşağıdakileri terminalde yürütün:</span><span class="sxs-lookup"><span data-stu-id="0f01a-171">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="0f01a-172">`dpkg -i` Komutu karşılaşılmamış bağımlılıklarıyla birlikte başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="0f01a-172">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="0f01a-173">Sonraki komut `apt-get install -f` PowerShell paketi Yapılandırma tamamlandıktan sonra bu sorunları giderir.</span><span class="sxs-lookup"><span data-stu-id="0f01a-173">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="0f01a-174">Kaldırma - Debian 8</span><span class="sxs-lookup"><span data-stu-id="0f01a-174">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="0f01a-175">Debian 9</span><span class="sxs-lookup"><span data-stu-id="0f01a-175">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="0f01a-176">Paket Deposu - Debian 9 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="0f01a-176">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="0f01a-177">Linux için PowerShell Core, paket depolarınızın kolay yükleme (ve güncelleştirmeleri) için yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="0f01a-177">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="0f01a-178">Bu tercih edilen yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="0f01a-178">This is the preferred method.</span></span>

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

<span data-ttu-id="0f01a-179">Microsoft depo süper kullanıcı bir kez kaydolduktan sonra daha sonra kullanmanız yeterlidir `sudo apt-get upgrade powershell` güncelleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="0f01a-179">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="0f01a-180">Doğrudan indirme - Debian 9 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="0f01a-180">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="0f01a-181">Debian paketi indirin `powershell_6.1.0-1.debian.9_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="0f01a-181">Download the Debian package `powershell_6.1.0-1.debian.9_amd64.deb`</span></span>
<span data-ttu-id="0f01a-182">gelen [sürümleri][] Debian makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="0f01a-182">from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="0f01a-183">Ardından aşağıdakileri terminalde yürütün:</span><span class="sxs-lookup"><span data-stu-id="0f01a-183">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="0f01a-184">Kaldırma - Debian 9</span><span class="sxs-lookup"><span data-stu-id="0f01a-184">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="0f01a-185">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="0f01a-185">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="0f01a-186">Bu paket, Oracle Linux 7'de de çalışır.</span><span class="sxs-lookup"><span data-stu-id="0f01a-186">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="0f01a-187">Paket (tercih edilir) - deposu CentOS 7 ile yükleme</span><span class="sxs-lookup"><span data-stu-id="0f01a-187">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="0f01a-188">Linux için PowerShell Core, resmi Microsoft depolara kolay yükleme (ve güncelleştirmeleri) için yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="0f01a-188">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="0f01a-189">Microsoft depo süper kullanıcı bir kez kaydolduktan sonra kullanmak yeterlidir `sudo yum update powershell` PowerShell güncelleştirilecek.</span><span class="sxs-lookup"><span data-stu-id="0f01a-189">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="0f01a-190">Doğrudan indirme - CentOS 7 ile yükleme</span><span class="sxs-lookup"><span data-stu-id="0f01a-190">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="0f01a-191">Kullanarak [CentOS 7][], RPM paketini indirme `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="0f01a-191">Using [CentOS 7][], download the RPM package `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="0f01a-192">gelen [sürümleri][] CentOS makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="0f01a-192">from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="0f01a-193">Ardından aşağıdakileri terminalde yürütün:</span><span class="sxs-lookup"><span data-stu-id="0f01a-193">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="0f01a-194">RPM karşıdan ara adım olmadan da yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0f01a-194">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="0f01a-195">Kaldırma - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="0f01a-195">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="0f01a-197">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="0f01a-197">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="0f01a-198">Paket (tercih edilir) - deposu Red Hat Enterprise Linux (RHEL) 7 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="0f01a-198">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="0f01a-199">Linux için PowerShell Core, resmi Microsoft depolara kolay yükleme (ve güncelleştirmeleri) için yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="0f01a-199">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="0f01a-200">Microsoft depo süper kullanıcı bir kez kaydolduktan sonra kullanmak yeterlidir `sudo yum update powershell` PowerShell güncelleştirilecek.</span><span class="sxs-lookup"><span data-stu-id="0f01a-200">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="0f01a-201">Doğrudan indirme - Red Hat Enterprise Linux (RHEL) 7 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="0f01a-201">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="0f01a-202">RPM paketini indirme `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="0f01a-202">Download the RPM package `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="0f01a-203">gelen [sürümleri][] Red Hat Enterprise Linux makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="0f01a-203">from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="0f01a-204">Ardından aşağıdakileri terminalde yürütün:</span><span class="sxs-lookup"><span data-stu-id="0f01a-204">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="0f01a-205">RPM karşıdan ara adım olmadan da yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0f01a-205">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="0f01a-206">Kaldırma - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="0f01a-206">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse-423"></a><span data-ttu-id="0f01a-207">OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="0f01a-207">OpenSUSE 42.3</span></span>

<span data-ttu-id="0f01a-208">PowerShell Core yükleme sırasında `zypper` şu hatayı bildirin:</span><span class="sxs-lookup"><span data-stu-id="0f01a-208">When installing PowerShell Core, `zypper` may report the following error:</span></span>

```Output
Problem: nothing provides libcurl needed by powershell-6.1.0-1.rhel.7.x86_64
 Solution 1: do not install powershell-6.1.0-1.rhel.7.x86_64
 Solution 2: break powershell-6.1.0-1.rhel.7.x86_64 by ignoring some of its dependencies
```

<span data-ttu-id="0f01a-209">Bu durumda, doğrulayın bir uyumlu `libcurl` kitaplığı varsa aşağıdaki gösterir komut denetleyerek `libcurl4` paketini yüklü olarak:</span><span class="sxs-lookup"><span data-stu-id="0f01a-209">In this case, verify that a compatible `libcurl` library is present by checking that the following command shows the `libcurl4` package as installed:</span></span>

```sh
zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
```

<span data-ttu-id="0f01a-210">Ardından `break powershell-6.1.0-1.rhel.7.x86_64 by ignoring some of its dependencies` PowerShell paketi yüklerken bir çözüm.</span><span class="sxs-lookup"><span data-stu-id="0f01a-210">Then choose the `break powershell-6.1.0-1.rhel.7.x86_64 by ignoring some of its dependencies` solution when installing the PowerShell package.</span></span>

### <a name="installation-via-package-repository-preferred---opensuse-423"></a><span data-ttu-id="0f01a-211">Paket (tercih edilir) - deposu OpenSUSE 42.3 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="0f01a-211">Installation via Package Repository (preferred) - OpenSUSE 42.3</span></span>

<span data-ttu-id="0f01a-212">Linux için PowerShell Core, resmi Microsoft depolara kolay yükleme (ve güncelleştirmeleri) için yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="0f01a-212">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Add the Microsoft Repository
zypper ar https://packages.microsoft.com/rhel/7/prod/

# Update the list of products
sudo zypper update

# Install PowerShell
sudo zypper install powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---opensuse-423"></a><span data-ttu-id="0f01a-213">Doğrudan indirme - OpenSUSE 42.3 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="0f01a-213">Installation via Direct Download - OpenSUSE 42.3</span></span>

<span data-ttu-id="0f01a-214">RPM paketini indirme `powershell-6.1.0-1.rhel.7.x86_64.rpm` gelen [sürümleri][] OpenSUSE makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="0f01a-214">Download the RPM package `powershell-6.1.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the OpenSUSE machine.</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="0f01a-215">RPM karşıdan ara adım olmadan da yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0f01a-215">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-423"></a><span data-ttu-id="0f01a-216">Kaldırma - OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="0f01a-216">Uninstallation - OpenSUSE 42.3</span></span>

```sh
sudo zypper remove powershell
```

## <a name="fedora"></a><span data-ttu-id="0f01a-217">Fedora</span><span class="sxs-lookup"><span data-stu-id="0f01a-217">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="0f01a-218">28 fedora yalnızca PowerShell Core 6.1 ve üzeri sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="0f01a-218">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="0f01a-219">Paket (tercih edilir) - deposu Fedora 27 Fedora 28 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="0f01a-219">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="0f01a-220">Linux için PowerShell Core, resmi Microsoft depolara kolay yükleme (ve güncelleştirmeleri) için yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="0f01a-220">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="0f01a-221">Doğrudan indirme - 27 Fedora, Fedora 28 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="0f01a-221">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="0f01a-222">RPM paketini indirme `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="0f01a-222">Download the RPM package `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="0f01a-223">gelen [sürümleri][] Fedora makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="0f01a-223">from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="0f01a-224">Ardından aşağıdakileri terminalde yürütün:</span><span class="sxs-lookup"><span data-stu-id="0f01a-224">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="0f01a-225">RPM karşıdan ara adım olmadan da yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0f01a-225">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="0f01a-226">Kaldırma - 27, Fedora Fedora 28</span><span class="sxs-lookup"><span data-stu-id="0f01a-226">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="0f01a-227">Linux arch</span><span class="sxs-lookup"><span data-stu-id="0f01a-227">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="0f01a-228">Deneysel yay desteği.</span><span class="sxs-lookup"><span data-stu-id="0f01a-228">Arch support is experimental.</span></span>

<span data-ttu-id="0f01a-229">PowerShell kullanılabilir [Linux arch][] kullanıcı deposu (AUR).</span><span class="sxs-lookup"><span data-stu-id="0f01a-229">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="0f01a-230">İle derlenebilir [en son sürümü etiketlendi][arch-release]</span><span class="sxs-lookup"><span data-stu-id="0f01a-230">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="0f01a-231">Gelen derlenebilir [ana son kaydetme][arch-git]</span><span class="sxs-lookup"><span data-stu-id="0f01a-231">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="0f01a-232">Kullanılarak yüklenebilir [ikili en son sürüm][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="0f01a-232">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="0f01a-233">AUR paketlerinde saklanır topluluk - resmi desteği yoktur.</span><span class="sxs-lookup"><span data-stu-id="0f01a-233">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="0f01a-234">AUR paketlerini yükleme hakkında daha fazla bilgi için bkz: [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) veya topluluk [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="0f01a-234">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Linux arch]: https://www.archlinux.org/download/
[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="0f01a-236">Paket Yasla</span><span class="sxs-lookup"><span data-stu-id="0f01a-236">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="0f01a-237">Snapd alma</span><span class="sxs-lookup"><span data-stu-id="0f01a-237">Getting snapd</span></span>

<span data-ttu-id="0f01a-238">`snapd` yaslar çalıştırmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="0f01a-238">`snapd` is required to run snaps.</span></span>
<span data-ttu-id="0f01a-239">Kullanım [bu yönergeleri](https://docs.snapcraft.io/core/install) sahip olduğunuzdan emin olmak için `snapd` yüklü.</span><span class="sxs-lookup"><span data-stu-id="0f01a-239">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="0f01a-240">Ek bileşeni aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="0f01a-240">Installation via Snap</span></span>

<span data-ttu-id="0f01a-241">Linux için PowerShell Core yayımlanmıştır [ek depolama](https://snapcraft.io/store) kolay yükleme (ve güncelleştirmeleri).</span><span class="sxs-lookup"><span data-stu-id="0f01a-241">PowerShell Core, for Linux, is published to the [Snap store](https://snapcraft.io/store) for easy installation (and updates).</span></span>
<span data-ttu-id="0f01a-242">Bu tercih edilen yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="0f01a-242">This is the preferred method.</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="0f01a-243">Sonra ek yükleme otomatik olarak yükseltecek, ancak bir yükseltme kullanarak tetikleyebilirsiniz `sudo snap refresh powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="0f01a-243">After installing Snap will automatically upgrade, but you can trigger an upgrade using `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="0f01a-244">Kaldırma</span><span class="sxs-lookup"><span data-stu-id="0f01a-244">Uninstallation</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="0f01a-245">Kali</span><span class="sxs-lookup"><span data-stu-id="0f01a-245">Kali</span></span>

> [!NOTE]
> <span data-ttu-id="0f01a-246">Kali desteği şu anda çalışmıyor.</span><span class="sxs-lookup"><span data-stu-id="0f01a-246">Kali support is not currently working.</span></span> <span data-ttu-id="0f01a-247">Lütfen kullanın [ek paket] [ snap] yerine.</span><span class="sxs-lookup"><span data-stu-id="0f01a-247">Please use the [Snap package][snap] instead.</span></span>

### <a name="installation"></a><span data-ttu-id="0f01a-248">Yükleme</span><span class="sxs-lookup"><span data-stu-id="0f01a-248">Installation</span></span>

```sh
# Download & Install prerequisites
sudo apt-get install libunwind8 libicu55
wget http://security.debian.org/debian-security/pool/updates/main/o/openssl/libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb
sudo dpkg -i libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb

# Install PowerShell
sudo dpkg -i powershell_6.1.0-1.ubuntu.16.04_amd64.deb

# Start PowerShell
pwsh
```

### <a name="uninstallation---kali"></a><span data-ttu-id="0f01a-249">Kaldırma - Kali</span><span class="sxs-lookup"><span data-stu-id="0f01a-249">Uninstallation - Kali</span></span>

```sh
sudo dpkg -r powershell_6.0.2-1.ubuntu.16.04_amd64.deb
```

## <a name="raspbian"></a><span data-ttu-id="0f01a-250">Raspbian</span><span class="sxs-lookup"><span data-stu-id="0f01a-250">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="0f01a-251">Deneysel Raspbian desteği.</span><span class="sxs-lookup"><span data-stu-id="0f01a-251">Raspbian support is experimental.</span></span>

<span data-ttu-id="0f01a-252">Şu anda PowerShell yalnızca Raspbian Esnetme üzerinde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="0f01a-252">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="0f01a-253">Ayrıca CoreCLR (ve bu nedenle PowerShell Core) yalnızca Pi 2 ve Pi 3 cihazlarında diğer cihazlar gibi çalışır [Pi sıfır](https://github.com/dotnet/coreclr/issues/10605), desteklenmeyen bir işlemciye sahip.</span><span class="sxs-lookup"><span data-stu-id="0f01a-253">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="0f01a-254">İndirme [Raspbian Esnetme](https://www.raspberrypi.org/downloads/raspbian/) izleyin [yükleme yönergeleri](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) Pi'yi almak için.</span><span class="sxs-lookup"><span data-stu-id="0f01a-254">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation"></a><span data-ttu-id="0f01a-255">Yükleme</span><span class="sxs-lookup"><span data-stu-id="0f01a-255">Installation</span></span>

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

<span data-ttu-id="0f01a-256">İsteğe bağlı olarak PowerShell "pwsh" ikili yol belirtmeden başlatabilmeniz için bir sembolik bağlantı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0f01a-256">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="0f01a-257">Kaldırma - Raspbian</span><span class="sxs-lookup"><span data-stu-id="0f01a-257">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="0f01a-258">İkili Arşivi</span><span class="sxs-lookup"><span data-stu-id="0f01a-258">Binary Archives</span></span>

<span data-ttu-id="0f01a-259">PowerShell ikili `tar.gz` arşivleri gelişmiş dağıtım senaryoları etkinleştirmek Linux platformlar için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="0f01a-259">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="0f01a-260">Bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="0f01a-260">Dependencies</span></span>

<span data-ttu-id="0f01a-261">PowerShell tüm Linux dağıtımları için taşınabilir ikili dosyaları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0f01a-261">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="0f01a-262">Ancak farklı bağımlılıklara farklı dağıtımlar üzerinde .NET Core çalışma zamanı gerektirir ve bu nedenle aynı PowerShell yapar.</span><span class="sxs-lookup"><span data-stu-id="0f01a-262">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="0f01a-263">Aşağıdaki tabloda farklı Linux dağıtımlarında resmi olarak desteklenen .NET Core 2.0 bağımlılıkları gösterir.</span><span class="sxs-lookup"><span data-stu-id="0f01a-263">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="0f01a-264">İşletim sistemi</span><span class="sxs-lookup"><span data-stu-id="0f01a-264">OS</span></span>                 | <span data-ttu-id="0f01a-265">Bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="0f01a-265">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="0f01a-266">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="0f01a-266">Ubuntu 14.04</span></span>       | <span data-ttu-id="0f01a-267">libc6, libgcc1, libgssapi-krb5-2 liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="0f01a-267">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="0f01a-268">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="0f01a-268">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="0f01a-269">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="0f01a-269">Ubuntu 16.04</span></span>       | <span data-ttu-id="0f01a-270">libc6, libgcc1, libgssapi-krb5-2 liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="0f01a-270">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="0f01a-271">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="0f01a-271">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="0f01a-272">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="0f01a-272">Ubuntu 17.10</span></span>       | <span data-ttu-id="0f01a-273">libc6, libgcc1, libgssapi-krb5-2 liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="0f01a-273">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="0f01a-274">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="0f01a-274">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="0f01a-275">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="0f01a-275">Ubuntu 18.04</span></span>       | <span data-ttu-id="0f01a-276">libc6, libgcc1, libgssapi-krb5-2 liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="0f01a-276">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="0f01a-277">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="0f01a-277">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="0f01a-278">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="0f01a-278">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="0f01a-279">libc6, libgcc1, libgssapi-krb5-2 liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="0f01a-279">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="0f01a-280">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="0f01a-280">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="0f01a-281">Debian 9 (Esnetme)</span><span class="sxs-lookup"><span data-stu-id="0f01a-281">Debian 9 (Stretch)</span></span> | <span data-ttu-id="0f01a-282">libc6, libgcc1, libgssapi-krb5-2 liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="0f01a-282">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="0f01a-283">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="0f01a-283">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="0f01a-284">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="0f01a-284">CentOS 7</span></span> <br> <span data-ttu-id="0f01a-285">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="0f01a-285">Oracle Linux 7</span></span> <br> <span data-ttu-id="0f01a-286">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="0f01a-286">RHEL 7</span></span> <br> <span data-ttu-id="0f01a-287">OpenSUSE OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="0f01a-287">OpenSUSE OpenSUSE 42.3</span></span> | <span data-ttu-id="0f01a-288">libunwind, libcurl, openssl kitaplıkları, libicu</span><span class="sxs-lookup"><span data-stu-id="0f01a-288">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="0f01a-289">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="0f01a-289">Fedora 27</span></span> <br> <span data-ttu-id="0f01a-290">28 fedora</span><span class="sxs-lookup"><span data-stu-id="0f01a-290">Fedora 28</span></span> | <span data-ttu-id="0f01a-291">libunwind, libcurl, openssl kitaplıkları, libicu, compat openssl10</span><span class="sxs-lookup"><span data-stu-id="0f01a-291">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="0f01a-292">Resmi olarak desteklenmez Linux dağıtımlarında PowerShell ikili dosyaları dağıtmak için ayrı adımları hedef işletim sistemi için gerekli bağımlılıkları yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="0f01a-292">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="0f01a-293">Örneğin, bizim [Amazon Linux dockerfile] [ amazon-dockerfile] ilk bağımlılıkları yükler ve ardından Linux ayıklar `tar.gz` arşiv.</span><span class="sxs-lookup"><span data-stu-id="0f01a-293">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="0f01a-294">Yükleme - ikili Arşivi</span><span class="sxs-lookup"><span data-stu-id="0f01a-294">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="0f01a-295">Linux</span><span class="sxs-lookup"><span data-stu-id="0f01a-295">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="0f01a-296">Kaldırma ikili Arşivi</span><span class="sxs-lookup"><span data-stu-id="0f01a-296">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="0f01a-297">Yollar</span><span class="sxs-lookup"><span data-stu-id="0f01a-297">Paths</span></span>

* <span data-ttu-id="0f01a-298">`$PSHOME` olduğu `/opt/microsoft/powershell/6.1.0/`</span><span class="sxs-lookup"><span data-stu-id="0f01a-298">`$PSHOME` is `/opt/microsoft/powershell/6.1.0/`</span></span>
* <span data-ttu-id="0f01a-299">Kullanıcı profillerini okuyabilir `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="0f01a-299">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="0f01a-300">Varsayılan profiller okuyabilir `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="0f01a-300">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="0f01a-301">Kullanıcı modülleri okuyabilir `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="0f01a-301">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="0f01a-302">Paylaşılan modülleri okuyabilir `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="0f01a-302">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="0f01a-303">Varsayılan modülleri okuyabilir `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="0f01a-303">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="0f01a-304">PSReadline geçmişi için kaydedilir `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="0f01a-304">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="0f01a-305">Varsayılan konak özel profilleri var Bu nedenle, PowerShell'in konak başına yapılandırma profilleri dikkate `Microsoft.PowerShell_profile.ps1` aynı konumlarda.</span><span class="sxs-lookup"><span data-stu-id="0f01a-305">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="0f01a-306">PowerShell uyar [XDG temel dizin belirtimi] [ xdg-bds] Linux üzerinde.</span><span class="sxs-lookup"><span data-stu-id="0f01a-306">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[sürümleri]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
