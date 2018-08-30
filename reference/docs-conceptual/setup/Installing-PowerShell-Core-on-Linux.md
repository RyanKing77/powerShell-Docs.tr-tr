---
title: Linux’ta PowerShell Core yükleme
description: PowerShell Core yükleme üzerinde çeşitli Linux dağıtımları hakkında bilgi
ms.date: 08/06/2018
ms.openlocfilehash: 0a1f30ef75a0feeb97df9a35a08d6b0d3edaeccf
ms.sourcegitcommit: 56b9be8503a5a1342c0b85b36f5ba6f57c281b63
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2018
ms.locfileid: "43133825"
---
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="b3197-103">Linux’ta PowerShell Core yükleme</span><span class="sxs-lookup"><span data-stu-id="b3197-103">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="b3197-104">Destekler [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.10] [ u18], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7] [ cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.3][opensuse], [Fedora 27 ] [ fedora], [Fedora 28][fedora], ve [Arch Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="b3197-104">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.10][u18], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.3][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="b3197-105">Değil resmi olarak desteklenen Linux dağıtımları için kullanmayı deneyebilirsiniz [PowerShell Yasla paket][snap].</span><span class="sxs-lookup"><span data-stu-id="b3197-105">For Linux distributions that are not officially supported, you can try using the [PowerShell Snap Package][snap].</span></span>
<span data-ttu-id="b3197-106">Linux kullanarak doğrudan PowerShell ikili dosyaları dağıtmaya de deneyebilirsiniz [ `tar.gz` arşiv][tar], ancak gerekli bağımlılıkları işletim sisteminde ayrı adımları göre ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b3197-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="b3197-107">Tüm paketleri bizim Github'da kullanılabilir [sürümleri][] sayfası.</span><span class="sxs-lookup"><span data-stu-id="b3197-107">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="b3197-108">Paket yüklendikten sonra Çalıştır `pwsh` bir terminalden.</span><span class="sxs-lookup"><span data-stu-id="b3197-108">Once the package is installed, run `pwsh` from a terminal.</span></span>

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

## <a name="installing-preview-releases"></a><span data-ttu-id="b3197-109">Önizleme sürümleri yükleme</span><span class="sxs-lookup"><span data-stu-id="b3197-109">Installing Preview Releases</span></span>

<span data-ttu-id="b3197-110">PowerShell Core Önizleme sürümü için Paket Deposu aracılığıyla Linux yüklerken, paket adı değişiklikleri `powershell` için `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="b3197-110">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="b3197-111">Doğrudan indirme ile yükleme, dosya adı dışında değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="b3197-111">Installing via direct download does not change, other than the file name.</span></span>

<span data-ttu-id="b3197-112">Çeşitli paket yöneticilerini kullanarak kararlı ve önizleme paketleri yüklemek için komut tablosu şu şekildedir:</span><span class="sxs-lookup"><span data-stu-id="b3197-112">Here is a table of the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="b3197-113">Distribution(s)</span><span class="sxs-lookup"><span data-stu-id="b3197-113">Distribution(s)</span></span>|<span data-ttu-id="b3197-114">Kararlı komutu</span><span class="sxs-lookup"><span data-stu-id="b3197-114">Stable Command</span></span> | <span data-ttu-id="b3197-115">Önizleme komutu</span><span class="sxs-lookup"><span data-stu-id="b3197-115">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="b3197-116">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="b3197-116">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="b3197-117">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="b3197-117">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="b3197-118">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="b3197-118">OpenSUSE</span></span> |`sudo zypper install powershell` | `sudo zypper install powershell-preview`|
| <span data-ttu-id="b3197-119">Fedora</span><span class="sxs-lookup"><span data-stu-id="b3197-119">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a><span data-ttu-id="b3197-120">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="b3197-120">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="b3197-121">Paket Deposu - Ubuntu 14.04 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="b3197-121">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="b3197-122">Linux için PowerShell Core, paket depolarınızın kolay yükleme (ve güncelleştirmeleri) için yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="b3197-122">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="b3197-123">Bu tercih edilen yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="b3197-123">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
curl https://packages.microsoft.com/config/ubuntu/14.04/prod.list | sudo tee /etc/apt/sources.list.d/microsoft.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="b3197-124">Süper kullanıcı Microsoft depoya kaydedin.</span><span class="sxs-lookup"><span data-stu-id="b3197-124">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="b3197-125">Daha sonra kullanmanız yeterlidir `sudo apt-get upgrade powershell` yüklemesini güncelleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="b3197-125">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="b3197-126">Doğrudan indirme - Ubuntu 14.04 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="b3197-126">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="b3197-127">Debian paketi indirin `powershell_6.0.3-1.ubuntu.14.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="b3197-127">Download the Debian package `powershell_6.0.3-1.ubuntu.14.04_amd64.deb`</span></span>
<span data-ttu-id="b3197-128">gelen [sürümleri][] Ubuntu makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="b3197-128">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="b3197-129">Ardından aşağıdakileri terminalde yürütün:</span><span class="sxs-lookup"><span data-stu-id="b3197-129">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.3-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="b3197-130">`dpkg -i` Komutu karşılaşılmamış bağımlılıklarıyla birlikte başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="b3197-130">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="b3197-131">Sonraki komut `apt-get install -f` PowerShell paketi Yapılandırma tamamlandıktan sonra bu sorunları giderir.</span><span class="sxs-lookup"><span data-stu-id="b3197-131">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="b3197-132">Kaldırma - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="b3197-132">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="b3197-133">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="b3197-133">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="b3197-134">Paket Deposu - Ubuntu 16.04 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="b3197-134">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="b3197-135">Linux için PowerShell Core, paket depolarınızın kolay yükleme (ve güncelleştirmeleri) için yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="b3197-135">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="b3197-136">Bu tercih edilen yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="b3197-136">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/16.04/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="b3197-137">Microsoft depo süper kullanıcı bir kez kaydolduktan sonra daha sonra kullanmanız yeterlidir `sudo apt-get upgrade powershell` güncelleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="b3197-137">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="b3197-138">Doğrudan indirme - Ubuntu 16.04 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="b3197-138">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="b3197-139">Debian paketi indirin `powershell_6.0.3-1.ubuntu.16.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="b3197-139">Download the Debian package `powershell_6.0.3-1.ubuntu.16.04_amd64.deb`</span></span>
<span data-ttu-id="b3197-140">gelen [sürümleri][] Ubuntu makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="b3197-140">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="b3197-141">Ardından aşağıdakileri terminalde yürütün:</span><span class="sxs-lookup"><span data-stu-id="b3197-141">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.3-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="b3197-142">`dpkg -i` Komutu karşılaşılmamış bağımlılıklarıyla birlikte başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="b3197-142">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="b3197-143">Sonraki komut `apt-get install -f` PowerShell paketi Yapılandırma tamamlandıktan sonra bu sorunları giderir.</span><span class="sxs-lookup"><span data-stu-id="b3197-143">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="b3197-144">Kaldırma - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="b3197-144">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="b3197-145">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="b3197-145">Ubuntu 18.04</span></span>

> [!NOTE]
> <span data-ttu-id="b3197-146">Sonra Ubuntu 18.04 desteği eklendi `6.1.0-preview.2`</span><span class="sxs-lookup"><span data-stu-id="b3197-146">Support for Ubuntu 18.04 was added after `6.1.0-preview.2`</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="b3197-147">Paket Deposu - Ubuntu 18.04 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="b3197-147">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="b3197-148">Linux için PowerShell Core, paket depolarınızın kolay yükleme (ve güncelleştirmeleri) için yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="b3197-148">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="b3197-149">Bu tercih edilen yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="b3197-149">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/18.04/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell-preview

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="b3197-150">Microsoft depo süper kullanıcı bir kez kaydolduktan sonra daha sonra kullanmanız yeterlidir `sudo apt-get upgrade powershell` güncelleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="b3197-150">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="b3197-151">Doğrudan indirme - Ubuntu 18.04 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="b3197-151">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="b3197-152">Debian paketi indirin `powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="b3197-152">Download the Debian package `powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb`</span></span>
<span data-ttu-id="b3197-153">gelen [sürümleri][] Ubuntu makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="b3197-153">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="b3197-154">Ardından aşağıdakileri terminalde yürütün:</span><span class="sxs-lookup"><span data-stu-id="b3197-154">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="b3197-155">`dpkg -i` Komutu karşılaşılmamış bağımlılıklarıyla birlikte başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="b3197-155">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="b3197-156">Sonraki komut `apt-get install -f` PowerShell paketi Yapılandırma tamamlandıktan sonra bu sorunları giderir.</span><span class="sxs-lookup"><span data-stu-id="b3197-156">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="b3197-157">Kaldırma - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="b3197-157">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="b3197-158">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="b3197-158">Ubuntu 18.10</span></span>

> [!NOTE]
> <span data-ttu-id="b3197-159">Ubuntu 18.10 desteği sonra eklenen `6.1.0-preview.3`.</span><span class="sxs-lookup"><span data-stu-id="b3197-159">Support for Ubuntu 18.10 was added after `6.1.0-preview.3`.</span></span>
> <span data-ttu-id="b3197-160">18.10 günlük bir derleme olduğundan, yalnızca desteklenen topluluk var.</span><span class="sxs-lookup"><span data-stu-id="b3197-160">As 18.10 is a daily build, it is only community supported.</span></span>

<span data-ttu-id="b3197-161">Üzerinde 18.10 yükleme aracılığıyla desteklenir `snapd`.</span><span class="sxs-lookup"><span data-stu-id="b3197-161">Installing on 18.10 is supported via `snapd`.</span></span> <span data-ttu-id="b3197-162">Bkz: [Yasla paket] [ snap] için tam yönergeler;</span><span class="sxs-lookup"><span data-stu-id="b3197-162">See [Snap Package][snap] for full instructions;</span></span>

## <a name="debian-8"></a><span data-ttu-id="b3197-163">Debian 8</span><span class="sxs-lookup"><span data-stu-id="b3197-163">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="b3197-164">Paket Deposu - Debian 8 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="b3197-164">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="b3197-165">Linux için PowerShell Core, paket depolarınızın kolay yükleme (ve güncelleştirmeleri) için yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="b3197-165">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="b3197-166">Bu tercih edilen yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="b3197-166">This is the preferred method.</span></span>

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

<span data-ttu-id="b3197-167">Microsoft depo süper kullanıcı bir kez kaydolduktan sonra daha sonra kullanmanız yeterlidir `sudo apt-get upgrade powershell` güncelleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="b3197-167">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="b3197-168">Doğrudan indirme - Debian 8 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="b3197-168">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="b3197-169">Debian paketi indirin `powershell_6.0.3-1.debian.8_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="b3197-169">Download the Debian package `powershell_6.0.3-1.debian.8_amd64.deb`</span></span>
<span data-ttu-id="b3197-170">gelen [sürümleri][] Debian makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="b3197-170">from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="b3197-171">Ardından aşağıdakileri terminalde yürütün:</span><span class="sxs-lookup"><span data-stu-id="b3197-171">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.3-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="b3197-172">`dpkg -i` Komutu karşılaşılmamış bağımlılıklarıyla birlikte başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="b3197-172">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="b3197-173">Sonraki komut `apt-get install -f` PowerShell paketi Yapılandırma tamamlandıktan sonra bu sorunları giderir.</span><span class="sxs-lookup"><span data-stu-id="b3197-173">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="b3197-174">Kaldırma - Debian 8</span><span class="sxs-lookup"><span data-stu-id="b3197-174">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="b3197-175">Debian 9</span><span class="sxs-lookup"><span data-stu-id="b3197-175">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="b3197-176">Paket Deposu - Debian 9 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="b3197-176">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="b3197-177">Linux için PowerShell Core, paket depolarınızın kolay yükleme (ve güncelleştirmeleri) için yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="b3197-177">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="b3197-178">Bu tercih edilen yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="b3197-178">This is the preferred method.</span></span>

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

<span data-ttu-id="b3197-179">Microsoft depo süper kullanıcı bir kez kaydolduktan sonra daha sonra kullanmanız yeterlidir `sudo apt-get upgrade powershell` güncelleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="b3197-179">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="b3197-180">Doğrudan indirme - Debian 9 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="b3197-180">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="b3197-181">Debian paketi indirin `powershell_6.0.3-1.debian.9_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="b3197-181">Download the Debian package `powershell_6.0.3-1.debian.9_amd64.deb`</span></span>
<span data-ttu-id="b3197-182">gelen [sürümleri][] Debian makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="b3197-182">from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="b3197-183">Ardından aşağıdakileri terminalde yürütün:</span><span class="sxs-lookup"><span data-stu-id="b3197-183">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.3-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="b3197-184">Kaldırma - Debian 9</span><span class="sxs-lookup"><span data-stu-id="b3197-184">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="b3197-185">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="b3197-185">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="b3197-186">Bu paket, Oracle Linux 7'de de çalışır.</span><span class="sxs-lookup"><span data-stu-id="b3197-186">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="b3197-187">Paket (tercih edilir) - deposu CentOS 7 ile yükleme</span><span class="sxs-lookup"><span data-stu-id="b3197-187">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="b3197-188">Linux için PowerShell Core, resmi Microsoft depolara kolay yükleme (ve güncelleştirmeleri) için yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="b3197-188">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="b3197-189">Microsoft depo süper kullanıcı bir kez kaydolduktan sonra kullanmak yeterlidir `sudo yum update powershell` PowerShell güncelleştirilecek.</span><span class="sxs-lookup"><span data-stu-id="b3197-189">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="b3197-190">Doğrudan indirme - CentOS 7 ile yükleme</span><span class="sxs-lookup"><span data-stu-id="b3197-190">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="b3197-191">Kullanarak [CentOS 7][], RPM paketini indirme `powershell-6.0.3-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="b3197-191">Using [CentOS 7][], download the RPM package `powershell-6.0.3-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="b3197-192">gelen [sürümleri][] CentOS makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="b3197-192">from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="b3197-193">Ardından aşağıdakileri terminalde yürütün:</span><span class="sxs-lookup"><span data-stu-id="b3197-193">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.3-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="b3197-194">RPM karşıdan ara adım olmadan da yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b3197-194">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.3/powershell-6.0.3-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="b3197-195">Kaldırma - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="b3197-195">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="b3197-197">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="b3197-197">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="b3197-198">Paket (tercih edilir) - deposu Red Hat Enterprise Linux (RHEL) 7 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="b3197-198">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="b3197-199">Linux için PowerShell Core, resmi Microsoft depolara kolay yükleme (ve güncelleştirmeleri) için yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="b3197-199">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="b3197-200">Microsoft depo süper kullanıcı bir kez kaydolduktan sonra kullanmak yeterlidir `sudo yum update powershell` PowerShell güncelleştirilecek.</span><span class="sxs-lookup"><span data-stu-id="b3197-200">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="b3197-201">Doğrudan indirme - Red Hat Enterprise Linux (RHEL) 7 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="b3197-201">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="b3197-202">RPM paketini indirme `powershell-6.0.3-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="b3197-202">Download the RPM package `powershell-6.0.3-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="b3197-203">gelen [sürümleri][] Red Hat Enterprise Linux makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="b3197-203">from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="b3197-204">Ardından aşağıdakileri terminalde yürütün:</span><span class="sxs-lookup"><span data-stu-id="b3197-204">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.3-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="b3197-205">RPM karşıdan ara adım olmadan da yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b3197-205">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.3/powershell-6.0.3-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="b3197-206">Kaldırma - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="b3197-206">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse-423"></a><span data-ttu-id="b3197-207">OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="b3197-207">OpenSUSE 42.3</span></span>

<span data-ttu-id="b3197-208">PowerShell Core yükleme sırasında `zypper` şu hatayı bildirin:</span><span class="sxs-lookup"><span data-stu-id="b3197-208">When installing PowerShell Core, `zypper` may report the following error:</span></span>

```Output
Problem: nothing provides libcurl needed by powershell-6.0.1-1.rhel.7.x86_64
 Solution 1: do not install powershell-6.0.1-1.rhel.7.x86_64
 Solution 2: break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies
```

<span data-ttu-id="b3197-209">Bu durumda, doğrulayın bir uyumlu `libcurl` kitaplığı varsa aşağıdaki gösterir komut denetleyerek `libcurl4` paketini yüklü olarak:</span><span class="sxs-lookup"><span data-stu-id="b3197-209">In this case, verify that a compatible `libcurl` library is present by checking that the following command shows the `libcurl4` package as installed:</span></span>

```sh
zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
```

<span data-ttu-id="b3197-210">Ardından `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` PowerShell paketi yüklerken bir çözüm.</span><span class="sxs-lookup"><span data-stu-id="b3197-210">Then choose the `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` solution when installing the PowerShell package.</span></span>

### <a name="installation-via-package-repository-preferred---opensuse-423"></a><span data-ttu-id="b3197-211">Paket (tercih edilir) - deposu OpenSUSE 42.3 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="b3197-211">Installation via Package Repository (preferred) - OpenSUSE 42.3</span></span>

<span data-ttu-id="b3197-212">Linux için PowerShell Core, resmi Microsoft depolara kolay yükleme (ve güncelleştirmeleri) için yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="b3197-212">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---opensuse-423"></a><span data-ttu-id="b3197-213">Doğrudan indirme - OpenSUSE 42.3 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="b3197-213">Installation via Direct Download - OpenSUSE 42.3</span></span>

<span data-ttu-id="b3197-214">RPM paketini indirme `powershell-6.0.3-1.rhel.7.x86_64.rpm` gelen [sürümleri][] OpenSUSE makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="b3197-214">Download the RPM package `powershell-6.0.3-1.rhel.7.x86_64.rpm` from the [releases][] page onto the OpenSUSE machine.</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.3-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="b3197-215">RPM karşıdan ara adım olmadan da yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b3197-215">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.3/powershell-6.0.3-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-423"></a><span data-ttu-id="b3197-216">Kaldırma - OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="b3197-216">Uninstallation - OpenSUSE 42.3</span></span>

```sh
sudo zypper remove powershell
```

## <a name="fedora"></a><span data-ttu-id="b3197-217">Fedora</span><span class="sxs-lookup"><span data-stu-id="b3197-217">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="b3197-218">28 fedora yalnızca PowerShell Core 6.1 ve üzeri sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="b3197-218">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="b3197-219">Paket (tercih edilir) - deposu Fedora 27 Fedora 28 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="b3197-219">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="b3197-220">Linux için PowerShell Core, resmi Microsoft depolara kolay yükleme (ve güncelleştirmeleri) için yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="b3197-220">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="b3197-221">Doğrudan indirme - 27 Fedora, Fedora 28 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="b3197-221">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="b3197-222">RPM paketini indirme `powershell-6.0.3-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="b3197-222">Download the RPM package `powershell-6.0.3-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="b3197-223">gelen [sürümleri][] Fedora makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="b3197-223">from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="b3197-224">Ardından aşağıdakileri terminalde yürütün:</span><span class="sxs-lookup"><span data-stu-id="b3197-224">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.3-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="b3197-225">RPM karşıdan ara adım olmadan da yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b3197-225">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="b3197-226">Kaldırma - 27, Fedora Fedora 28</span><span class="sxs-lookup"><span data-stu-id="b3197-226">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="b3197-227">Linux arch</span><span class="sxs-lookup"><span data-stu-id="b3197-227">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="b3197-228">Deneysel yay desteği.</span><span class="sxs-lookup"><span data-stu-id="b3197-228">Arch support is experimental.</span></span>

<span data-ttu-id="b3197-229">PowerShell kullanılabilir [Linux arch][] kullanıcı deposu (AUR).</span><span class="sxs-lookup"><span data-stu-id="b3197-229">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="b3197-230">İle derlenebilir [en son sürümü etiketlendi][arch-release]</span><span class="sxs-lookup"><span data-stu-id="b3197-230">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="b3197-231">Gelen derlenebilir [ana son kaydetme][arch-git]</span><span class="sxs-lookup"><span data-stu-id="b3197-231">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="b3197-232">Kullanılarak yüklenebilir [ikili en son sürüm][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="b3197-232">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="b3197-233">AUR paketlerinde saklanır topluluk - resmi desteği yoktur.</span><span class="sxs-lookup"><span data-stu-id="b3197-233">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="b3197-234">AUR paketlerini yükleme hakkında daha fazla bilgi için bkz: [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) veya topluluk [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="b3197-234">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Linux arch]: https://www.archlinux.org/download/
[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="b3197-236">Paket Yasla</span><span class="sxs-lookup"><span data-stu-id="b3197-236">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="b3197-237">Snapd alma</span><span class="sxs-lookup"><span data-stu-id="b3197-237">Getting snapd</span></span>

<span data-ttu-id="b3197-238">`snapd` yaslar çalıştırmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b3197-238">`snapd` is required to run snaps.</span></span>  <span data-ttu-id="b3197-239">Kullanım [bu yönergeleri](https://docs.snapcraft.io/core/install) sahip olduğunuzdan emin olmak için `snapd` yüklü.</span><span class="sxs-lookup"><span data-stu-id="b3197-239">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="b3197-240">Ek bileşeni aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="b3197-240">Installation via Snap</span></span>

<span data-ttu-id="b3197-241">Linux için PowerShell Core yayımlanmıştır [ek depolama](https://snapcraft.io/store) kolay yükleme (ve güncelleştirmeleri).</span><span class="sxs-lookup"><span data-stu-id="b3197-241">PowerShell Core, for Linux, is published to the [Snap store](https://snapcraft.io/store) for easy installation (and updates).</span></span>
<span data-ttu-id="b3197-242">Bu tercih edilen yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="b3197-242">This is the preferred method.</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="b3197-243">Sonra ek yükleme otomatik olarak yükseltecek, ancak bir yükseltme kullanarak tetikleyebilirsiniz `sudo snap refresh powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="b3197-243">After installing Snap will automatically upgrade, but you can trigger an upgrade using `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="b3197-244">Kaldırma</span><span class="sxs-lookup"><span data-stu-id="b3197-244">Uninstallation</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="linux-appimage"></a><span data-ttu-id="b3197-245">Linux AppImage</span><span class="sxs-lookup"><span data-stu-id="b3197-245">Linux AppImage</span></span>

> [!NOTE]
> <span data-ttu-id="b3197-246">Deneysel AppImage desteği</span><span class="sxs-lookup"><span data-stu-id="b3197-246">AppImage support is experimental</span></span>

<span data-ttu-id="b3197-247">Son bir Linux dağıtımını kullanarak indirme AppImage `powershell-6.0.1-x86_64.AppImage` gelen [sürümleri][] Linux makinesi sayfaya.</span><span class="sxs-lookup"><span data-stu-id="b3197-247">Using a recent Linux distribution, download the AppImage `powershell-6.0.1-x86_64.AppImage` from the [releases][] page onto the Linux machine.</span></span>

<span data-ttu-id="b3197-248">Ardından aşağıdakileri terminalde yürütün:</span><span class="sxs-lookup"><span data-stu-id="b3197-248">Then execute the following in the terminal:</span></span>

```bash
chmod a+x powershell-6.0.1-x86_64.AppImage
./powershell-6.0.1-x86_64.AppImage
```

<span data-ttu-id="b3197-249">[AppImage][] , PowerShell yüklemeden çalıştırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="b3197-249">The [AppImage][] lets you run PowerShell without installing it.</span></span>
<span data-ttu-id="b3197-250">PowerShell ve bağımlılıklarını (.NET Core'nın sistem bağımlılıklar dahil olmak üzere) cohesive tek bir pakette toplamıştır taşınabilir bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="b3197-250">It is a portable application that bundles PowerShell and its dependencies (including .NET Core's system dependencies) into one cohesive package.</span></span>
<span data-ttu-id="b3197-251">Bu paket, kullanıcının Linux dağıtım bağımsız olarak çalışan tek bir ikili dosyadır.</span><span class="sxs-lookup"><span data-stu-id="b3197-251">This package is a single binary that works independently of the user's Linux distribution.</span></span>

[appimage]: http://appimage.org/

## <a name="kali"></a><span data-ttu-id="b3197-253">Kali</span><span class="sxs-lookup"><span data-stu-id="b3197-253">Kali</span></span>

> [!NOTE]
> <span data-ttu-id="b3197-254">Deneysel Kali desteği.</span><span class="sxs-lookup"><span data-stu-id="b3197-254">Kali support is experimental.</span></span>

### <a name="installation"></a><span data-ttu-id="b3197-255">Yükleme</span><span class="sxs-lookup"><span data-stu-id="b3197-255">Installation</span></span>

```sh
# Download & Install prerequisites
sudo apt-get install libunwind8 libicu55
wget http://security.debian.org/debian-security/pool/updates/main/o/openssl/libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb
sudo dpkg -i libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb

# Install PowerShell
sudo dpkg -i powershell_6.0.3-1.ubuntu.16.04_amd64.deb

# Start PowerShell
pwsh
```

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a><span data-ttu-id="b3197-256">PowerShell yüklemeden son Kali içinde (GNU/Linux Kali çalışırken) çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b3197-256">Run PowerShell in latest Kali (Kali GNU/Linux Rolling) without installing it</span></span>

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.2-x86_64.AppImage

# Start PowerShell
./powershell-6.0.2-x86_64.AppImage
```

### <a name="uninstallation---kali"></a><span data-ttu-id="b3197-257">Kaldırma - Kali</span><span class="sxs-lookup"><span data-stu-id="b3197-257">Uninstallation - Kali</span></span>

```sh
sudo dpkg -r powershell_6.0.2-1.ubuntu.16.04_amd64.deb
```

## <a name="raspbian"></a><span data-ttu-id="b3197-258">Raspbian</span><span class="sxs-lookup"><span data-stu-id="b3197-258">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="b3197-259">Deneysel Raspbian desteği.</span><span class="sxs-lookup"><span data-stu-id="b3197-259">Raspbian support is experimental.</span></span>

<span data-ttu-id="b3197-260">Şu anda PowerShell yalnızca Raspbian Esnetme üzerinde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="b3197-260">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="b3197-261">Ayrıca CoreCLR (ve bu nedenle PowerShell Core) yalnızca Pi 2 ve Pi 3 cihazlarında diğer cihazlar gibi çalışır [Pi sıfır](https://github.com/dotnet/coreclr/issues/10605), desteklenmeyen bir işlemciye sahip.</span><span class="sxs-lookup"><span data-stu-id="b3197-261">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="b3197-262">İndirme [Raspbian Esnetme](https://www.raspberrypi.org/downloads/raspbian/) izleyin [yükleme yönergeleri](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) Pi'yi almak için.</span><span class="sxs-lookup"><span data-stu-id="b3197-262">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation"></a><span data-ttu-id="b3197-263">Yükleme</span><span class="sxs-lookup"><span data-stu-id="b3197-263">Installation</span></span>

```sh
# Install prerequisites
sudo apt-get install libunwind8

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.3/powershell-6.0.3-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.0.3-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

<span data-ttu-id="b3197-264">İsteğe bağlı olarak PowerShell "pwsh" ikili yol belirtmeden başlatabilmeniz için bir sembolik bağlantı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b3197-264">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="b3197-265">Kaldırma - Raspbian</span><span class="sxs-lookup"><span data-stu-id="b3197-265">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="b3197-266">İkili Arşivi</span><span class="sxs-lookup"><span data-stu-id="b3197-266">Binary Archives</span></span>

<span data-ttu-id="b3197-267">PowerShell ikili `tar.gz` arşivleri gelişmiş dağıtım senaryoları etkinleştirmek Linux platformlar için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="b3197-267">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="b3197-268">Bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="b3197-268">Dependencies</span></span>

<span data-ttu-id="b3197-269">PowerShell tüm Linux dağıtımları için taşınabilir ikili dosyaları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b3197-269">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="b3197-270">Ancak farklı bağımlılıklara farklı dağıtımlar üzerinde .NET Core çalışma zamanı gerektirir ve bu nedenle aynı PowerShell yapar.</span><span class="sxs-lookup"><span data-stu-id="b3197-270">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="b3197-271">Aşağıdaki tabloda farklı Linux dağıtımlarında resmi olarak desteklenen .NET Core 2.0 bağımlılıkları gösterir.</span><span class="sxs-lookup"><span data-stu-id="b3197-271">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="b3197-272">İşletim sistemi</span><span class="sxs-lookup"><span data-stu-id="b3197-272">OS</span></span>                 | <span data-ttu-id="b3197-273">Bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="b3197-273">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="b3197-274">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="b3197-274">Ubuntu 14.04</span></span>       | <span data-ttu-id="b3197-275">libc6, libgcc1, libgssapi-krb5-2 liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="b3197-275">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="b3197-276">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="b3197-276">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="b3197-277">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="b3197-277">Ubuntu 16.04</span></span>       | <span data-ttu-id="b3197-278">libc6, libgcc1, libgssapi-krb5-2 liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="b3197-278">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="b3197-279">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="b3197-279">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="b3197-280">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="b3197-280">Ubuntu 17.10</span></span>       | <span data-ttu-id="b3197-281">libc6, libgcc1, libgssapi-krb5-2 liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="b3197-281">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="b3197-282">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="b3197-282">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="b3197-283">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="b3197-283">Ubuntu 18.04</span></span>       | <span data-ttu-id="b3197-284">libc6, libgcc1, libgssapi-krb5-2 liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="b3197-284">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="b3197-285">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="b3197-285">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="b3197-286">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="b3197-286">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="b3197-287">libc6, libgcc1, libgssapi-krb5-2 liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="b3197-287">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="b3197-288">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="b3197-288">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="b3197-289">Debian 9 (Esnetme)</span><span class="sxs-lookup"><span data-stu-id="b3197-289">Debian 9 (Stretch)</span></span> | <span data-ttu-id="b3197-290">libc6, libgcc1, libgssapi-krb5-2 liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="b3197-290">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="b3197-291">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="b3197-291">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="b3197-292">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="b3197-292">CentOS 7</span></span> <br> <span data-ttu-id="b3197-293">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="b3197-293">Oracle Linux 7</span></span> <br> <span data-ttu-id="b3197-294">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="b3197-294">RHEL 7</span></span> <br> <span data-ttu-id="b3197-295">OpenSUSE OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="b3197-295">OpenSUSE OpenSUSE 42.3</span></span> | <span data-ttu-id="b3197-296">libunwind, libcurl, openssl kitaplıkları, libicu</span><span class="sxs-lookup"><span data-stu-id="b3197-296">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="b3197-297">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="b3197-297">Fedora 27</span></span> <br> <span data-ttu-id="b3197-298">28 fedora</span><span class="sxs-lookup"><span data-stu-id="b3197-298">Fedora 28</span></span> | <span data-ttu-id="b3197-299">libunwind, libcurl, openssl kitaplıkları, libicu, compat openssl10</span><span class="sxs-lookup"><span data-stu-id="b3197-299">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="b3197-300">Resmi olarak desteklenmez Linux dağıtımlarında PowerShell ikili dosyaları dağıtmak için ayrı adımları hedef işletim sistemi için gerekli bağımlılıkları yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b3197-300">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="b3197-301">Örneğin, bizim [Amazon Linux dockerfile] [ amazon-dockerfile] ilk bağımlılıkları yükler ve ardından Linux ayıklar `tar.gz` arşiv.</span><span class="sxs-lookup"><span data-stu-id="b3197-301">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="b3197-302">Yükleme - ikili Arşivi</span><span class="sxs-lookup"><span data-stu-id="b3197-302">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="b3197-303">Linux</span><span class="sxs-lookup"><span data-stu-id="b3197-303">Linux</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/6.0.2

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.0.2

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/6.0.2/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/6.0.2/pwsh /usr/bin/pwsh
```

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="b3197-304">Kaldırma ikili Arşivi</span><span class="sxs-lookup"><span data-stu-id="b3197-304">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="b3197-305">Yollar</span><span class="sxs-lookup"><span data-stu-id="b3197-305">Paths</span></span>

* <span data-ttu-id="b3197-306">`$PSHOME` olduğu `/opt/microsoft/powershell/6.0.3/`</span><span class="sxs-lookup"><span data-stu-id="b3197-306">`$PSHOME` is `/opt/microsoft/powershell/6.0.3/`</span></span>
* <span data-ttu-id="b3197-307">Kullanıcı profillerini okuyabilir `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="b3197-307">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="b3197-308">Varsayılan profiller okuyabilir `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="b3197-308">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="b3197-309">Kullanıcı modülleri okuyabilir `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="b3197-309">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="b3197-310">Paylaşılan modülleri okuyabilir `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="b3197-310">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="b3197-311">Varsayılan modülleri okuyabilir `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="b3197-311">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="b3197-312">PSReadline geçmişi için kaydedilir `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="b3197-312">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="b3197-313">Varsayılan konak özel profilleri var Bu nedenle, PowerShell'in konak başına yapılandırma profilleri dikkate `Microsoft.PowerShell_profile.ps1` aynı konumlarda.</span><span class="sxs-lookup"><span data-stu-id="b3197-313">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="b3197-314">PowerShell uyar [XDG temel dizin belirtimi] [ xdg-bds] Linux üzerinde.</span><span class="sxs-lookup"><span data-stu-id="b3197-314">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[sürümleri]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
