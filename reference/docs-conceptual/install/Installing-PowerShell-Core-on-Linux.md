---
title: Linux’ta PowerShell Core yükleme
description: Çeşitli Linux dağıtımlarına PowerShell Core yükleme hakkında bilgi
ms.date: 07/19/2019
ms.openlocfilehash: 7d7c9a9f915f0a6e735a7baec1ec56e9c205a155
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848190"
---
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="ec00a-103">Linux’ta PowerShell Core yükleme</span><span class="sxs-lookup"><span data-stu-id="ec00a-103">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="ec00a-104">[Ubuntu 16,04][u16], [ubuntu 18,04][u1804], [Ubuntu 18,10][u1810], [Ubuntu 19,04][u1904], [de, 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42,3][opensuse], [openSUSE, 15][opensuse], [Fedora 27 ' yi destekler ][fedora], [Fedora 28][fedora]ve [mimari Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="ec00a-104">Supports [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810], [Ubuntu 19.04][u1904], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="ec00a-105">Resmi olarak desteklenen Linux dağıtımları için PowerShell [Snap paketini][snap]kullanarak PowerShell 'i yüklemeyi deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec00a-105">For Linux distributions that aren't officially supported, you can try to install PowerShell using the [PowerShell Snap Package][snap].</span></span> <span data-ttu-id="ec00a-106">Ayrıca, Linux [ `tar.gz` Arşivi][tar]kullanarak PowerShell ikililerini doğrudan dağıtmaya da deneyebilirsiniz, ancak işletim sistemini ayrı adımlarda temel alarak gerekli bağımlılıkları ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ec00a-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="ec00a-107">Tüm paketleri GitHub [yayınları][] sayfamızda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec00a-107">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="ec00a-108">Paket yüklendikten sonra bir terminalden çalıştırın `pwsh` .</span><span class="sxs-lookup"><span data-stu-id="ec00a-108">After the package is installed, run `pwsh` from a terminal.</span></span>

[u16]: #ubuntu-1604
[u1804]: #ubuntu-1804
[u1810]: #ubuntu-1810
[u1904]: #ubuntu-1904
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse
[fedora]: #fedora
[arch]: #arch-linux
[snap]: #snap-package
[tar]: #binary-archives

## <a name="installing-preview-releases"></a><span data-ttu-id="ec00a-109">Önizleme sürümleri yükleniyor</span><span class="sxs-lookup"><span data-stu-id="ec00a-109">Installing Preview Releases</span></span>

<span data-ttu-id="ec00a-110">Bir paket deposu aracılığıyla Linux için bir PowerShell Core Preview sürümü yüklerken, paket adı ' dan `powershell` `powershell-preview`' a değişir.</span><span class="sxs-lookup"><span data-stu-id="ec00a-110">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="ec00a-111">Doğrudan indirme aracılığıyla yükleme, dosya adından başka bir değişiklik yapmaz.</span><span class="sxs-lookup"><span data-stu-id="ec00a-111">Installing via direct download doesn't change, other than the file name.</span></span>

<span data-ttu-id="ec00a-112">Aşağıdaki tabloda, çeşitli paket yöneticilerini kullanarak kararlı ve önizleme paketlerini yüklemeye yönelik komutlar yer almaktadır:</span><span class="sxs-lookup"><span data-stu-id="ec00a-112">The following table contains the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="ec00a-113">Dağıtım (ler)</span><span class="sxs-lookup"><span data-stu-id="ec00a-113">Distribution(s)</span></span>|<span data-ttu-id="ec00a-114">Stable komutu</span><span class="sxs-lookup"><span data-stu-id="ec00a-114">Stable Command</span></span> | <span data-ttu-id="ec00a-115">Önizleme komutu</span><span class="sxs-lookup"><span data-stu-id="ec00a-115">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="ec00a-116">Ubuntu, dene</span><span class="sxs-lookup"><span data-stu-id="ec00a-116">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="ec00a-117">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="ec00a-117">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="ec00a-118">Fedora</span><span class="sxs-lookup"><span data-stu-id="ec00a-118">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1604"></a><span data-ttu-id="ec00a-119">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="ec00a-119">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="ec00a-120">Paket deposu aracılığıyla yükleme-Ubuntu 16,04</span><span class="sxs-lookup"><span data-stu-id="ec00a-120">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="ec00a-121">Linux için PowerShell Core, kolay yükleme ve güncelleştirmeler için paket depolarında yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="ec00a-121">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="ec00a-122">Tercih edilen yöntem aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="ec00a-122">The preferred method is as follows:</span></span>

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

<span data-ttu-id="ec00a-123">Süper Kullanıcı olarak Microsoft Repository 'yi bir kez kaydettirin.</span><span class="sxs-lookup"><span data-stu-id="ec00a-123">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="ec00a-124">Kayıttan sonra PowerShell 'i ile `sudo apt-get upgrade powershell`güncelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec00a-124">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="ec00a-125">Doğrudan Download-Ubuntu 16,04 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="ec00a-125">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="ec00a-126">[yayınları][] sayfasından Ubuntu `powershell_6.2.0-1.ubuntu.16.04_amd64.deb` makinesine deleyi paketini indirin.</span><span class="sxs-lookup"><span data-stu-id="ec00a-126">Download the Debian package `powershell_6.2.0-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="ec00a-127">Ardından, terminalde aşağıdaki komutları yürütün:</span><span class="sxs-lookup"><span data-stu-id="ec00a-127">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="ec00a-128">`dpkg -i` Komut karşılanmamış bağımlılıklarla başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="ec00a-128">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="ec00a-129">Sonraki komut, `apt-get install -f` bu sorunları çözer ve PowerShell paketini yapılandırmayı tamamlar.</span><span class="sxs-lookup"><span data-stu-id="ec00a-129">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="ec00a-130">Kaldırma-Ubuntu 16,04</span><span class="sxs-lookup"><span data-stu-id="ec00a-130">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="ec00a-131">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="ec00a-131">Ubuntu 18.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="ec00a-132">Paket deposu aracılığıyla yükleme-Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="ec00a-132">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="ec00a-133">Linux için PowerShell Core, kolay yükleme ve güncelleştirmeler için paket depolarında yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="ec00a-133">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="ec00a-134">Tercih edilen yöntem aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="ec00a-134">The preferred method is as follows:</span></span>

```sh
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Enable the "universe" repositories
sudo add-apt-repository universe

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="ec00a-135">Süper Kullanıcı olarak Microsoft Repository 'yi bir kez kaydettirin.</span><span class="sxs-lookup"><span data-stu-id="ec00a-135">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="ec00a-136">Kayıttan sonra PowerShell 'i ile `sudo apt-get upgrade powershell`güncelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec00a-136">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="ec00a-137">Doğrudan Download-Ubuntu 18,04 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="ec00a-137">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="ec00a-138">[yayınları][] sayfasından Ubuntu `powershell_6.2.0-1.ubuntu.18.04_amd64.deb` makinesine deleyi paketini indirin.</span><span class="sxs-lookup"><span data-stu-id="ec00a-138">Download the Debian package `powershell_6.2.0-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="ec00a-139">Ardından, terminalde aşağıdaki komutları yürütün:</span><span class="sxs-lookup"><span data-stu-id="ec00a-139">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="ec00a-140">`dpkg -i` Komut karşılanmamış bağımlılıklarla başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="ec00a-140">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="ec00a-141">Sonraki komut, `apt-get install -f` bu sorunları çözer ve PowerShell paketini yapılandırmayı tamamlar.</span><span class="sxs-lookup"><span data-stu-id="ec00a-141">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="ec00a-142">Kaldırma-Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="ec00a-142">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="ec00a-143">Ubuntu 18,10</span><span class="sxs-lookup"><span data-stu-id="ec00a-143">Ubuntu 18.10</span></span>

<span data-ttu-id="ec00a-144">Yüklemesi aracılığıyla `snapd`desteklenir.</span><span class="sxs-lookup"><span data-stu-id="ec00a-144">Installation is supported via `snapd`.</span></span> <span data-ttu-id="ec00a-145">Yönergeler için bkz. [yaslama paketi][snap].</span><span class="sxs-lookup"><span data-stu-id="ec00a-145">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="ec00a-146">Ubuntu 18,10, [topluluk tarafından desteklenen](../powershell-support-lifecycle.md)bir [Ara sürümdür](https://www.ubuntu.com/about/release-cycle) .</span><span class="sxs-lookup"><span data-stu-id="ec00a-146">Ubuntu 18.10 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="ubuntu-1904"></a><span data-ttu-id="ec00a-147">Ubuntu 19,04</span><span class="sxs-lookup"><span data-stu-id="ec00a-147">Ubuntu 19.04</span></span>

<span data-ttu-id="ec00a-148">Yüklemesi aracılığıyla `snapd`desteklenir.</span><span class="sxs-lookup"><span data-stu-id="ec00a-148">Installation is supported via `snapd`.</span></span> <span data-ttu-id="ec00a-149">Yönergeler için bkz. [yaslama paketi][snap].</span><span class="sxs-lookup"><span data-stu-id="ec00a-149">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="ec00a-150">Ubuntu 19,04, [topluluk tarafından desteklenen](../powershell-support-lifecycle.md)bir [Ara sürümdür](https://www.ubuntu.com/about/release-cycle) .</span><span class="sxs-lookup"><span data-stu-id="ec00a-150">Ubuntu 19.04 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="debian-8"></a><span data-ttu-id="ec00a-151">Debian 8</span><span class="sxs-lookup"><span data-stu-id="ec00a-151">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="ec00a-152">Paket deposu aracılığıyla yükleme-detem 8</span><span class="sxs-lookup"><span data-stu-id="ec00a-152">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="ec00a-153">Linux için PowerShell Core, kolay yükleme ve güncelleştirmeler için paket depolarında yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="ec00a-153">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="ec00a-154">Tercih edilen yöntem aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="ec00a-154">The preferred method is as follows:</span></span>

```sh
# Install system components
sudo apt-get update
sudo apt-get install -y curl apt-transport-https

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

<span data-ttu-id="ec00a-155">Süper Kullanıcı olarak Microsoft Repository 'yi bir kez kaydettirin.</span><span class="sxs-lookup"><span data-stu-id="ec00a-155">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="ec00a-156">Kayıttan sonra PowerShell 'i ile `sudo apt-get upgrade powershell`güncelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec00a-156">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

## <a name="debian-9"></a><span data-ttu-id="ec00a-157">Debian 9</span><span class="sxs-lookup"><span data-stu-id="ec00a-157">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="ec00a-158">Paket deposu aracılığıyla yükleme-detem 9</span><span class="sxs-lookup"><span data-stu-id="ec00a-158">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="ec00a-159">Linux için PowerShell Core, kolay yükleme ve güncelleştirmeler için paket depolarında yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="ec00a-159">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="ec00a-160">Tercih edilen yöntem aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="ec00a-160">The preferred method is as follows:</span></span>

```sh
# Install system components
sudo apt-get update
sudo apt-get install -y curl gnupg apt-transport-https

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

<span data-ttu-id="ec00a-161">Süper Kullanıcı olarak Microsoft Repository 'yi bir kez kaydettirin.</span><span class="sxs-lookup"><span data-stu-id="ec00a-161">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="ec00a-162">Kayıttan sonra PowerShell 'i ile `sudo apt-get upgrade powershell`güncelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec00a-162">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="ec00a-163">Doğrudan Indirme ile yükleme-detem 9</span><span class="sxs-lookup"><span data-stu-id="ec00a-163">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="ec00a-164">[yayınları][] sayfasından debir makineye `powershell_6.2.0-1.debian.9_amd64.deb` olan deleyi paketini indirin.</span><span class="sxs-lookup"><span data-stu-id="ec00a-164">Download the Debian package `powershell_6.2.0-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="ec00a-165">Ardından, terminalde aşağıdaki komutları yürütün:</span><span class="sxs-lookup"><span data-stu-id="ec00a-165">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="ec00a-166">Kaldırma-kaldırıcı 9</span><span class="sxs-lookup"><span data-stu-id="ec00a-166">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="ec00a-167">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="ec00a-167">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="ec00a-168">Bu paket Oracle Linux 7 ' de çalışmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ec00a-168">This package works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="ec00a-169">Paket deposu aracılığıyla yükleme (tercih edilen)-CentOS 7</span><span class="sxs-lookup"><span data-stu-id="ec00a-169">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="ec00a-170">Linux için PowerShell Core, kolay yükleme ve güncelleştirmeler için resmi Microsoft depolarında yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="ec00a-170">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="ec00a-171">Süper Kullanıcı olarak Microsoft Repository 'yi bir kez kaydettirin.</span><span class="sxs-lookup"><span data-stu-id="ec00a-171">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="ec00a-172">Kayıttan sonra PowerShell 'i ile `sudo yum update powershell`güncelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec00a-172">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="ec00a-173">Doğrudan Indirme ile yükleme-CentOS 7</span><span class="sxs-lookup"><span data-stu-id="ec00a-173">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="ec00a-174">[CentOS 7][]' yi kullanarak, [yayınları][] sayfasından `powershell-6.2.0-1.rhel.7.x86_64.rpm` CentOS makinesine RPM paketini indirin.</span><span class="sxs-lookup"><span data-stu-id="ec00a-174">Using [CentOS 7][], download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="ec00a-175">Ardından, terminalde aşağıdaki komutları yürütün:</span><span class="sxs-lookup"><span data-stu-id="ec00a-175">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="ec00a-176">Yükleme işlemi için ara adım olmadan RPM 'yi yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ec00a-176">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="ec00a-177">Kaldırma-CentOS 7</span><span class="sxs-lookup"><span data-stu-id="ec00a-177">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="ec00a-179">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="ec00a-179">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="ec00a-180">Paket deposu aracılığıyla yükleme (tercih edilen)-Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="ec00a-180">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="ec00a-181">Linux için PowerShell Core, kolay yükleme ve güncelleştirmeler için resmi Microsoft depolarında yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="ec00a-181">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="ec00a-182">Süper Kullanıcı olarak Microsoft Repository 'yi bir kez kaydettirin.</span><span class="sxs-lookup"><span data-stu-id="ec00a-182">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="ec00a-183">Kayıttan sonra PowerShell 'i ile `sudo yum update powershell`güncelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec00a-183">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="ec00a-184">Doğrudan Indirme ile yükleme-Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="ec00a-184">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="ec00a-185">Sürümler sayfasından Red Hat Enterprise Linux makineye `powershell-6.2.0-1.rhel.7.x86_64.rpm` RPM paketini [yayınları][].</span><span class="sxs-lookup"><span data-stu-id="ec00a-185">Download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="ec00a-186">Ardından, terminalde aşağıdaki komutları yürütün:</span><span class="sxs-lookup"><span data-stu-id="ec00a-186">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="ec00a-187">Yükleme işlemi için ara adım olmadan RPM 'yi yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ec00a-187">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="ec00a-188">Kaldırma-Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="ec00a-188">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="ec00a-189">openSUSE</span><span class="sxs-lookup"><span data-stu-id="ec00a-189">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="ec00a-190">Yükleme-openSUSE 42,3</span><span class="sxs-lookup"><span data-stu-id="ec00a-190">Installation - openSUSE 42.3</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar libicu52_1

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/6.2.0

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.2.0

# Set execute permissions
chmod +x /opt/microsoft/powershell/6.2.0/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/6.2.0/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="ec00a-191">Yükleme-openSUSE artık 15</span><span class="sxs-lookup"><span data-stu-id="ec00a-191">Installation - openSUSE Leap 15</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar gzip libopenssl1_0_0 libicu60_2

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/6.2.0

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.2.0

# Set execute permissions
chmod +x /opt/microsoft/powershell/6.2.0/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/6.2.0/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="ec00a-192">Kaldırma-openSUSE 42,3, openSUSE artık 15</span><span class="sxs-lookup"><span data-stu-id="ec00a-192">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="ec00a-193">Fedora</span><span class="sxs-lookup"><span data-stu-id="ec00a-193">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="ec00a-194">Fedora 28 yalnızca PowerShell Core 6,1 ve daha yeni sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="ec00a-194">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="ec00a-195">Paket deposu aracılığıyla yükleme (tercih edilen)-Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="ec00a-195">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="ec00a-196">Linux için PowerShell Core, kolay yükleme ve güncelleştirmeler için resmi Microsoft depolarında yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="ec00a-196">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="ec00a-197">Doğrudan Indirme ile yükleme-Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="ec00a-197">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="ec00a-198">`powershell-6.2.0-1.rhel.7.x86_64.rpm` [yayınları][] sayfasından Fedora makinesine RPM paketini indirin.</span><span class="sxs-lookup"><span data-stu-id="ec00a-198">Download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="ec00a-199">Ardından, terminalde aşağıdaki komutları yürütün:</span><span class="sxs-lookup"><span data-stu-id="ec00a-199">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="ec00a-200">Yükleme işlemi için ara adım olmadan RPM 'yi yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ec00a-200">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="ec00a-201">Kaldırma-Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="ec00a-201">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="ec00a-202">Mimari Linux</span><span class="sxs-lookup"><span data-stu-id="ec00a-202">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="ec00a-203">Mimari desteği deneysel.</span><span class="sxs-lookup"><span data-stu-id="ec00a-203">Arch support is experimental.</span></span>

<span data-ttu-id="ec00a-204">PowerShell, [mimari Linux][] kullanıcı deposundan (AUR) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ec00a-204">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="ec00a-205">[En son etiketli sürümle][arch-release] derlenebilir</span><span class="sxs-lookup"><span data-stu-id="ec00a-205">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="ec00a-206">[En son işlemeden ana şablona][arch-git] derlenebilir</span><span class="sxs-lookup"><span data-stu-id="ec00a-206">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="ec00a-207">[En son sürüm ikilisi][arch-bin] kullanılarak yüklenebilir</span><span class="sxs-lookup"><span data-stu-id="ec00a-207">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="ec00a-208">AUR 'teki paketler topluluk tarafından korunur; resmi olmayan destek yoktur.</span><span class="sxs-lookup"><span data-stu-id="ec00a-208">Packages in the AUR are community maintained; there's no official support.</span></span>

<span data-ttu-id="ec00a-209">AUR 'ten paket yükleme hakkında daha fazla bilgi için bkz. [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) veya Community [dockerfile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="ec00a-209">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Mimari Linux]: https://www.archlinux.org/download/
[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="ec00a-211">Yaslama paketi</span><span class="sxs-lookup"><span data-stu-id="ec00a-211">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="ec00a-212">Anlık görüntü alınıyor</span><span class="sxs-lookup"><span data-stu-id="ec00a-212">Getting snapd</span></span>

<span data-ttu-id="ec00a-213">`snapd`yapış çalıştırmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ec00a-213">`snapd` is required to run snaps.</span></span> <span data-ttu-id="ec00a-214">Yüklediğinizden emin `snapd` olmak için [Bu yönergeleri](https://docs.snapcraft.io/core/install) kullanın.</span><span class="sxs-lookup"><span data-stu-id="ec00a-214">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="ec00a-215">Yaslama aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="ec00a-215">Installation via Snap</span></span>

<span data-ttu-id="ec00a-216">Linux için PowerShell Core, kolay yükleme ve güncelleştirmeler için [Snap deposunda](https://snapcraft.io/store) yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="ec00a-216">PowerShell Core for Linux is published to the [Snap store](https://snapcraft.io/store) for easy installation and updates.</span></span>

<span data-ttu-id="ec00a-217">Tercih edilen yöntem aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="ec00a-217">The preferred method is as follows:</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="ec00a-218">Önizleme sürümünü yüklemek için aşağıdaki yöntemi kullanın:</span><span class="sxs-lookup"><span data-stu-id="ec00a-218">To install a preview version, use the following method:</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="ec00a-219">Yükleme sonrasında, yaslama otomatik olarak yükseltilir.</span><span class="sxs-lookup"><span data-stu-id="ec00a-219">After installation, Snap will automatically upgrade.</span></span> <span data-ttu-id="ec00a-220">`sudo snap refresh powershell` Veya`sudo snap refresh powershell-preview`kullanarak bir yükseltmeyi tetikleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec00a-220">You can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="ec00a-221">CP</span><span class="sxs-lookup"><span data-stu-id="ec00a-221">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="ec00a-222">veya</span><span class="sxs-lookup"><span data-stu-id="ec00a-222">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="ec00a-223">Kalı</span><span class="sxs-lookup"><span data-stu-id="ec00a-223">Kali</span></span>

### <a name="installation---kali"></a><span data-ttu-id="ec00a-224">Yükleme-kalı</span><span class="sxs-lookup"><span data-stu-id="ec00a-224">Installation - Kali</span></span>

```sh
# Download & Install prerequisites
wget http://ftp.us.debian.org/debian/pool/main/i/icu/libicu57_57.1-6+deb9u2_amd64.deb
dpkg -i libicu57_57.1-6+deb9u2_amd64.deb
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

### <a name="uninstallation---kali"></a><span data-ttu-id="ec00a-225">Kaldırma-kalı</span><span class="sxs-lookup"><span data-stu-id="ec00a-225">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt-get remove -y powershell
```

## <a name="raspbian"></a><span data-ttu-id="ec00a-226">Raspbian</span><span class="sxs-lookup"><span data-stu-id="ec00a-226">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="ec00a-227">Raspbian desteği deneysel.</span><span class="sxs-lookup"><span data-stu-id="ec00a-227">Raspbian support is experimental.</span></span>

<span data-ttu-id="ec00a-228">Şu anda PowerShell yalnızca Raspbian Esnette destekleniyor.</span><span class="sxs-lookup"><span data-stu-id="ec00a-228">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="ec00a-229">CoreCLR ve PowerShell Core yalnızca PI 2 ve PI 3 cihazlarda, [PI sıfır](https://github.com/dotnet/coreclr/issues/10605)gibi diğer cihazlar için de çalışır ve desteklenmeyen bir işlemciye sahip olur.</span><span class="sxs-lookup"><span data-stu-id="ec00a-229">CoreCLR and PowerShell Core will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="ec00a-230">[Raspbian Esnetme](https://www.raspberrypi.org/downloads/raspbian/) Indirin ve PI 'larınızın üzerine ulaşmak için [yükleme yönergelerini](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) izleyin.</span><span class="sxs-lookup"><span data-stu-id="ec00a-230">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="ec00a-231">Yükleme-Raspbian</span><span class="sxs-lookup"><span data-stu-id="ec00a-231">Installation - Raspbian</span></span>

```sh
###################################
# Prerequisites

# Update package lists
sudo apt-get update

# Install libunwind8 and libssl1.0
# Regex is used to ensure that we do not install libssl1.0-dev, as it is a variant that is not required
sudo apt-get install '^libssl1.0.[0-9]$' libunwind8 -y

###################################
# Download and extract PowerShell

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.2.0-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

<span data-ttu-id="ec00a-232">İsteğe bağlı olarak, `pwsh` ikili dosyanın yolunu belirtmeden PowerShell 'i başlatmak için bir sembolik bağlantı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec00a-232">Optionally, you can create a symbolic link to start PowerShell without specifying the path to the `pwsh` binary.</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="ec00a-233">Kaldırma-Raspbian</span><span class="sxs-lookup"><span data-stu-id="ec00a-233">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="ec00a-234">İkili Arşivler</span><span class="sxs-lookup"><span data-stu-id="ec00a-234">Binary Archives</span></span>

<span data-ttu-id="ec00a-235">PowerShell ikili `tar.gz` arşivleri, Linux platformları için gelişmiş dağıtım senaryolarını etkinleştirmek üzere sağlanır.</span><span class="sxs-lookup"><span data-stu-id="ec00a-235">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="ec00a-236">Bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="ec00a-236">Dependencies</span></span>

<span data-ttu-id="ec00a-237">PowerShell, tüm Linux dağıtımları için taşınabilir ikili dosyalar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ec00a-237">PowerShell builds portable binaries for all Linux distributions.</span></span> <span data-ttu-id="ec00a-238">Ancak, .NET Core çalışma zamanı farklı dağıtımlarda farklı bağımlılıklar gerektirir ve PowerShell de çok fazla yapılır.</span><span class="sxs-lookup"><span data-stu-id="ec00a-238">But, .NET Core runtime requires different dependencies on different distributions, and PowerShell does too.</span></span>

<span data-ttu-id="ec00a-239">Aşağıdaki grafikte, farklı Linux dağıtımları üzerinde resmi olarak desteklenen .NET Core 2,0 bağımlılıkları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ec00a-239">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="ec00a-240">İşletim sistemi</span><span class="sxs-lookup"><span data-stu-id="ec00a-240">OS</span></span>                 | <span data-ttu-id="ec00a-241">Bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="ec00a-241">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="ec00a-242">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="ec00a-242">Ubuntu 16.04</span></span>       | <span data-ttu-id="ec00a-243">libc6, libgcc1, libgssapı-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="ec00a-243">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="ec00a-244">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="ec00a-244">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="ec00a-245">Ubuntu 17,10</span><span class="sxs-lookup"><span data-stu-id="ec00a-245">Ubuntu 17.10</span></span>       | <span data-ttu-id="ec00a-246">libc6, libgcc1, libgssapı-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="ec00a-246">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="ec00a-247">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="ec00a-247">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="ec00a-248">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="ec00a-248">Ubuntu 18.04</span></span>       | <span data-ttu-id="ec00a-249">libc6, libgcc1, libgssapı-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="ec00a-249">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="ec00a-250">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="ec00a-250">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="ec00a-251">Desek8 (Jese)</span><span class="sxs-lookup"><span data-stu-id="ec00a-251">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="ec00a-252">libc6, libgcc1, libgssapı-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="ec00a-252">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="ec00a-253">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="ec00a-253">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="ec00a-254">Deda 9 (uzat)</span><span class="sxs-lookup"><span data-stu-id="ec00a-254">Debian 9 (Stretch)</span></span> | <span data-ttu-id="ec00a-255">libc6, libgcc1, libgssapı-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="ec00a-255">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="ec00a-256">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="ec00a-256">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="ec00a-257">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="ec00a-257">CentOS 7</span></span> <br> <span data-ttu-id="ec00a-258">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="ec00a-258">Oracle Linux 7</span></span> <br> <span data-ttu-id="ec00a-259">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="ec00a-259">RHEL 7</span></span> | <span data-ttu-id="ec00a-260">librüzgar, Libya, OpenSSL-libs, libıu</span><span class="sxs-lookup"><span data-stu-id="ec00a-260">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="ec00a-261">openSUSE 42,3</span><span class="sxs-lookup"><span data-stu-id="ec00a-261">openSUSE 42.3</span></span> | <span data-ttu-id="ec00a-262">libcurl4, libopenssl1_0_0, libicu52_1</span><span class="sxs-lookup"><span data-stu-id="ec00a-262">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="ec00a-263">openSUSE artık 15</span><span class="sxs-lookup"><span data-stu-id="ec00a-263">openSUSE Leap 15</span></span> | <span data-ttu-id="ec00a-264">libcurl4, libopenssl1_0_0, libicu60_2</span><span class="sxs-lookup"><span data-stu-id="ec00a-264">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="ec00a-265">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="ec00a-265">Fedora 27</span></span> <br> <span data-ttu-id="ec00a-266">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="ec00a-266">Fedora 28</span></span> | <span data-ttu-id="ec00a-267">libıwind, libkıvrık, OpenSSL-libs, libıu, COMPAT-openssl10</span><span class="sxs-lookup"><span data-stu-id="ec00a-267">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="ec00a-268">Resmi olarak desteklenmeyen Linux dağıtımlarına PowerShell ikilileri dağıtmak için, hedef işletim sistemi için gerekli bağımlılıkları ayrı adımlarda yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ec00a-268">To deploy PowerShell binaries on Linux distributions that aren't officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span> <span data-ttu-id="ec00a-269">Örneğin, [Amazon Linux dockerfile][amazon-dockerfile] , önce bağımlılıkları yüklüyor ve ardından Linux `tar.gz` arşivini ayıklar.</span><span class="sxs-lookup"><span data-stu-id="ec00a-269">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="ec00a-270">Yükleme-Ikili arşivleri</span><span class="sxs-lookup"><span data-stu-id="ec00a-270">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="ec00a-271">Linux</span><span class="sxs-lookup"><span data-stu-id="ec00a-271">Linux</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/6.2.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.2.0

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/6.2.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/6.2.0/pwsh /usr/bin/pwsh
```

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="ec00a-272">İkili arşivleri kaldırma</span><span class="sxs-lookup"><span data-stu-id="ec00a-272">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="ec00a-273">Yollar</span><span class="sxs-lookup"><span data-stu-id="ec00a-273">Paths</span></span>

* <span data-ttu-id="ec00a-274">`$PSHOME`eklenir`/opt/microsoft/powershell/6.2.0/`</span><span class="sxs-lookup"><span data-stu-id="ec00a-274">`$PSHOME` is `/opt/microsoft/powershell/6.2.0/`</span></span>
* <span data-ttu-id="ec00a-275">Kullanıcı profilleri şuradan okunacaktır`~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="ec00a-275">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="ec00a-276">Varsayılan profiller buradan okunacaktır`$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="ec00a-276">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="ec00a-277">Kullanıcı modülleri okunacaktır`~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="ec00a-277">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="ec00a-278">Paylaşılan modüller buradan okunacaktır`/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="ec00a-278">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="ec00a-279">Varsayılan modüller okunacaktır`$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="ec00a-279">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="ec00a-280">PSReadline geçmişi şu şekilde kaydedilecek`~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="ec00a-280">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="ec00a-281">Profiller, PowerShell 'in konak başına yapılandırmasını kabul eder; bu nedenle, varsayılan konağa özgü profiller aynı konumlarda `Microsoft.PowerShell_profile.ps1` bulunur.</span><span class="sxs-lookup"><span data-stu-id="ec00a-281">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="ec00a-282">PowerShell, Linux üzerinde [xdg taban dizini belirtimine][xdg-bds] uyar.</span><span class="sxs-lookup"><span data-stu-id="ec00a-282">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[yayınları]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
