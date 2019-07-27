---
title: Linux’ta PowerShell Core yükleme
description: Çeşitli Linux dağıtımlarına PowerShell Core yükleme hakkında bilgi
ms.date: 07/19/2019
ms.openlocfilehash: 929b153ef784f3203cd31a0e2fc52e744a07532f
ms.sourcegitcommit: 118eb294d5a84a772e6449d42a9d9324e18ef6b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68372187"
---
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="3e52d-103">Linux’ta PowerShell Core yükleme</span><span class="sxs-lookup"><span data-stu-id="3e52d-103">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="3e52d-104">[Ubuntu 16,04][u16], [ubuntu 18,04][u1804], [Ubuntu 18,10][u1810], [de, 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42,3][opensuse], [openSUSE artık 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [mimari Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="3e52d-104">Supports [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="3e52d-105">Resmi olarak desteklenen Linux dağıtımları için PowerShell [Snap paketini][snap]kullanarak PowerShell 'i yüklemeyi deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e52d-105">For Linux distributions that aren't officially supported, you can try to install PowerShell using the [PowerShell Snap Package][snap].</span></span> <span data-ttu-id="3e52d-106">Ayrıca, Linux [ `tar.gz` Arşivi][tar]kullanarak PowerShell ikililerini doğrudan dağıtmaya da deneyebilirsiniz, ancak işletim sistemini ayrı adımlarda temel alarak gerekli bağımlılıkları ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3e52d-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="3e52d-107">Tüm paketleri GitHub [yayınları][] sayfamızda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e52d-107">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="3e52d-108">Paket yüklendikten sonra bir terminalden çalıştırın `pwsh` .</span><span class="sxs-lookup"><span data-stu-id="3e52d-108">After the package is installed, run `pwsh` from a terminal.</span></span>

[u16]: #ubuntu-1604
[u1804]: #ubuntu-1804
[u1810]: #ubuntu-1810
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse
[fedora]: #fedora
[arch]: #arch-linux
[snap]: #snap-package
[tar]: #binary-archives

## <a name="installing-preview-releases"></a><span data-ttu-id="3e52d-109">Önizleme sürümleri yükleniyor</span><span class="sxs-lookup"><span data-stu-id="3e52d-109">Installing Preview Releases</span></span>

<span data-ttu-id="3e52d-110">Bir paket deposu aracılığıyla Linux için bir PowerShell Core Preview sürümü yüklerken, paket adı ' dan `powershell` `powershell-preview`' a değişir.</span><span class="sxs-lookup"><span data-stu-id="3e52d-110">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="3e52d-111">Doğrudan indirme aracılığıyla yükleme, dosya adından başka bir değişiklik yapmaz.</span><span class="sxs-lookup"><span data-stu-id="3e52d-111">Installing via direct download doesn't change, other than the file name.</span></span>

<span data-ttu-id="3e52d-112">Aşağıdaki tabloda, çeşitli paket yöneticilerini kullanarak kararlı ve önizleme paketlerini yüklemeye yönelik komutlar yer almaktadır:</span><span class="sxs-lookup"><span data-stu-id="3e52d-112">The following table contains the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="3e52d-113">Dağıtım (ler)</span><span class="sxs-lookup"><span data-stu-id="3e52d-113">Distribution(s)</span></span>|<span data-ttu-id="3e52d-114">Stable komutu</span><span class="sxs-lookup"><span data-stu-id="3e52d-114">Stable Command</span></span> | <span data-ttu-id="3e52d-115">Önizleme komutu</span><span class="sxs-lookup"><span data-stu-id="3e52d-115">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="3e52d-116">Ubuntu, dene</span><span class="sxs-lookup"><span data-stu-id="3e52d-116">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="3e52d-117">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="3e52d-117">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="3e52d-118">Fedora</span><span class="sxs-lookup"><span data-stu-id="3e52d-118">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1604"></a><span data-ttu-id="3e52d-119">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="3e52d-119">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="3e52d-120">Paket deposu aracılığıyla yükleme-Ubuntu 16,04</span><span class="sxs-lookup"><span data-stu-id="3e52d-120">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="3e52d-121">Linux için PowerShell Core, kolay yükleme ve güncelleştirmeler için paket depolarında yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="3e52d-121">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="3e52d-122">Tercih edilen yöntem aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="3e52d-122">The preferred method is as follows:</span></span>

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

<span data-ttu-id="3e52d-123">Süper Kullanıcı olarak Microsoft Repository 'yi bir kez kaydettirin.</span><span class="sxs-lookup"><span data-stu-id="3e52d-123">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="3e52d-124">Kayıttan sonra PowerShell 'i ile `sudo apt-get upgrade powershell`güncelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e52d-124">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="3e52d-125">Doğrudan Download-Ubuntu 16,04 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="3e52d-125">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="3e52d-126">[yayınları][] sayfasından Ubuntu `powershell_6.2.0-1.ubuntu.16.04_amd64.deb` makinesine deleyi paketini indirin.</span><span class="sxs-lookup"><span data-stu-id="3e52d-126">Download the Debian package `powershell_6.2.0-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="3e52d-127">Ardından, terminalde aşağıdaki komutları yürütün:</span><span class="sxs-lookup"><span data-stu-id="3e52d-127">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="3e52d-128">`dpkg -i` Komut karşılanmamış bağımlılıklarla başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="3e52d-128">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="3e52d-129">Sonraki komut, `apt-get install -f` bu sorunları çözer ve PowerShell paketini yapılandırmayı tamamlar.</span><span class="sxs-lookup"><span data-stu-id="3e52d-129">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="3e52d-130">Kaldırma-Ubuntu 16,04</span><span class="sxs-lookup"><span data-stu-id="3e52d-130">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="3e52d-131">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="3e52d-131">Ubuntu 18.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="3e52d-132">Paket deposu aracılığıyla yükleme-Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="3e52d-132">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="3e52d-133">Linux için PowerShell Core, kolay yükleme ve güncelleştirmeler için paket depolarında yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="3e52d-133">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="3e52d-134">Tercih edilen yöntem aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="3e52d-134">The preferred method is as follows:</span></span>

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

<span data-ttu-id="3e52d-135">Süper Kullanıcı olarak Microsoft Repository 'yi bir kez kaydettirin.</span><span class="sxs-lookup"><span data-stu-id="3e52d-135">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="3e52d-136">Kayıttan sonra PowerShell 'i ile `sudo apt-get upgrade powershell`güncelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e52d-136">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="3e52d-137">Doğrudan Download-Ubuntu 18,04 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="3e52d-137">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="3e52d-138">[yayınları][] sayfasından Ubuntu `powershell_6.2.0-1.ubuntu.18.04_amd64.deb` makinesine deleyi paketini indirin.</span><span class="sxs-lookup"><span data-stu-id="3e52d-138">Download the Debian package `powershell_6.2.0-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="3e52d-139">Ardından, terminalde aşağıdaki komutları yürütün:</span><span class="sxs-lookup"><span data-stu-id="3e52d-139">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="3e52d-140">`dpkg -i` Komut karşılanmamış bağımlılıklarla başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="3e52d-140">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="3e52d-141">Sonraki komut, `apt-get install -f` bu sorunları çözer ve PowerShell paketini yapılandırmayı tamamlar.</span><span class="sxs-lookup"><span data-stu-id="3e52d-141">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="3e52d-142">Kaldırma-Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="3e52d-142">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="3e52d-143">Ubuntu 18,10</span><span class="sxs-lookup"><span data-stu-id="3e52d-143">Ubuntu 18.10</span></span>

> [!NOTE]
> <span data-ttu-id="3e52d-144">18,10, geçici bir [Sürüm](https://www.ubuntu.com/about/release-cycle)olduğundan yalnızca [topluluk desteklenir](https://docs.microsoft.com/en-us/powershell/scripting/powershell-support-lifecycle?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="3e52d-144">As 18.10 is an [interim release](https://www.ubuntu.com/about/release-cycle), it is only [community supported](https://docs.microsoft.com/en-us/powershell/scripting/powershell-support-lifecycle?view=powershell-6).</span></span>

<span data-ttu-id="3e52d-145">18,10 üzerine yükleme, aracılığıyla `snapd`desteklenir.</span><span class="sxs-lookup"><span data-stu-id="3e52d-145">Installing on 18.10 is supported via `snapd`.</span></span> <span data-ttu-id="3e52d-146">Bkz. tam yönergeler için [yaslama paketi][snap] ;</span><span class="sxs-lookup"><span data-stu-id="3e52d-146">See [Snap Package][snap] for full instructions;</span></span>

## <a name="debian-8"></a><span data-ttu-id="3e52d-147">Debian 8</span><span class="sxs-lookup"><span data-stu-id="3e52d-147">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="3e52d-148">Paket deposu aracılığıyla yükleme-detem 8</span><span class="sxs-lookup"><span data-stu-id="3e52d-148">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="3e52d-149">Linux için PowerShell Core, kolay yükleme ve güncelleştirmeler için paket depolarında yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="3e52d-149">PowerShell Core, for Linux, is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="3e52d-150">Tercih edilen yöntem aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="3e52d-150">The preferred method is as follows:</span></span>

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

<span data-ttu-id="3e52d-151">Süper Kullanıcı olarak Microsoft Repository 'yi bir kez kaydettirin.</span><span class="sxs-lookup"><span data-stu-id="3e52d-151">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="3e52d-152">Kayıttan sonra PowerShell 'i ile `sudo apt-get upgrade powershell`güncelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e52d-152">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

## <a name="debian-9"></a><span data-ttu-id="3e52d-153">Debian 9</span><span class="sxs-lookup"><span data-stu-id="3e52d-153">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="3e52d-154">Paket deposu aracılığıyla yükleme-detem 9</span><span class="sxs-lookup"><span data-stu-id="3e52d-154">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="3e52d-155">Linux için PowerShell Core, kolay yükleme ve güncelleştirmeler için paket depolarında yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="3e52d-155">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="3e52d-156">Tercih edilen yöntem aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="3e52d-156">The preferred method is as follows:</span></span>

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

<span data-ttu-id="3e52d-157">Süper Kullanıcı olarak Microsoft Repository 'yi bir kez kaydettirin.</span><span class="sxs-lookup"><span data-stu-id="3e52d-157">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="3e52d-158">Kayıttan sonra PowerShell 'i ile `sudo apt-get upgrade powershell`güncelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e52d-158">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="3e52d-159">Doğrudan Indirme ile yükleme-detem 9</span><span class="sxs-lookup"><span data-stu-id="3e52d-159">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="3e52d-160">[yayınları][] sayfasından debir makineye `powershell_6.2.0-1.debian.9_amd64.deb` olan deleyi paketini indirin.</span><span class="sxs-lookup"><span data-stu-id="3e52d-160">Download the Debian package `powershell_6.2.0-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="3e52d-161">Ardından, terminalde aşağıdaki komutları yürütün:</span><span class="sxs-lookup"><span data-stu-id="3e52d-161">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="3e52d-162">Kaldırma-kaldırıcı 9</span><span class="sxs-lookup"><span data-stu-id="3e52d-162">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="3e52d-163">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="3e52d-163">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="3e52d-164">Bu paket Oracle Linux 7 ' de çalışmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3e52d-164">This package works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="3e52d-165">Paket deposu aracılığıyla yükleme (tercih edilen)-CentOS 7</span><span class="sxs-lookup"><span data-stu-id="3e52d-165">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="3e52d-166">Linux için PowerShell Core, kolay yükleme ve güncelleştirmeler için resmi Microsoft depolarında yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="3e52d-166">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="3e52d-167">Süper Kullanıcı olarak Microsoft Repository 'yi bir kez kaydettirin.</span><span class="sxs-lookup"><span data-stu-id="3e52d-167">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="3e52d-168">Kayıttan sonra PowerShell 'i ile `sudo yum update powershell`güncelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e52d-168">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="3e52d-169">Doğrudan Indirme ile yükleme-CentOS 7</span><span class="sxs-lookup"><span data-stu-id="3e52d-169">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="3e52d-170">[CentOS 7][]' yi kullanarak, [yayınları][] sayfasından `powershell-6.2.0-1.rhel.7.x86_64.rpm` CentOS makinesine RPM paketini indirin.</span><span class="sxs-lookup"><span data-stu-id="3e52d-170">Using [CentOS 7][], download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="3e52d-171">Ardından, terminalde aşağıdaki komutları yürütün:</span><span class="sxs-lookup"><span data-stu-id="3e52d-171">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="3e52d-172">Yükleme işlemi için ara adım olmadan RPM 'yi yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3e52d-172">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="3e52d-173">Kaldırma-CentOS 7</span><span class="sxs-lookup"><span data-stu-id="3e52d-173">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="3e52d-175">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="3e52d-175">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="3e52d-176">Paket deposu aracılığıyla yükleme (tercih edilen)-Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="3e52d-176">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="3e52d-177">Linux için PowerShell Core, kolay yükleme ve güncelleştirmeler için resmi Microsoft depolarında yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="3e52d-177">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="3e52d-178">Süper Kullanıcı olarak Microsoft Repository 'yi bir kez kaydettirin.</span><span class="sxs-lookup"><span data-stu-id="3e52d-178">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="3e52d-179">Kayıttan sonra PowerShell 'i ile `sudo yum update powershell`güncelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e52d-179">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="3e52d-180">Doğrudan Indirme ile yükleme-Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="3e52d-180">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="3e52d-181">Sürümler sayfasından Red Hat Enterprise Linux makineye `powershell-6.2.0-1.rhel.7.x86_64.rpm` RPM paketini [yayınları][].</span><span class="sxs-lookup"><span data-stu-id="3e52d-181">Download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="3e52d-182">Ardından, terminalde aşağıdaki komutları yürütün:</span><span class="sxs-lookup"><span data-stu-id="3e52d-182">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="3e52d-183">Yükleme işlemi için ara adım olmadan RPM 'yi yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3e52d-183">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="3e52d-184">Kaldırma-Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="3e52d-184">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="3e52d-185">openSUSE</span><span class="sxs-lookup"><span data-stu-id="3e52d-185">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="3e52d-186">Yükleme-openSUSE 42,3</span><span class="sxs-lookup"><span data-stu-id="3e52d-186">Installation - openSUSE 42.3</span></span>

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

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="3e52d-187">Yükleme-openSUSE artık 15</span><span class="sxs-lookup"><span data-stu-id="3e52d-187">Installation - openSUSE Leap 15</span></span>

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

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="3e52d-188">Kaldırma-openSUSE 42,3, openSUSE artık 15</span><span class="sxs-lookup"><span data-stu-id="3e52d-188">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="3e52d-189">Fedora</span><span class="sxs-lookup"><span data-stu-id="3e52d-189">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="3e52d-190">Fedora 28 yalnızca PowerShell Core 6,1 ve daha yeni sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="3e52d-190">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="3e52d-191">Paket deposu aracılığıyla yükleme (tercih edilen)-Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="3e52d-191">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="3e52d-192">Linux için PowerShell Core, kolay yükleme ve güncelleştirmeler için resmi Microsoft depolarında yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="3e52d-192">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="3e52d-193">Doğrudan Indirme ile yükleme-Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="3e52d-193">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="3e52d-194">`powershell-6.2.0-1.rhel.7.x86_64.rpm` [yayınları][] sayfasından Fedora makinesine RPM paketini indirin.</span><span class="sxs-lookup"><span data-stu-id="3e52d-194">Download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="3e52d-195">Ardından, terminalde aşağıdaki komutları yürütün:</span><span class="sxs-lookup"><span data-stu-id="3e52d-195">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="3e52d-196">Yükleme işlemi için ara adım olmadan RPM 'yi yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3e52d-196">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="3e52d-197">Kaldırma-Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="3e52d-197">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="3e52d-198">Mimari Linux</span><span class="sxs-lookup"><span data-stu-id="3e52d-198">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="3e52d-199">Mimari desteği deneysel.</span><span class="sxs-lookup"><span data-stu-id="3e52d-199">Arch support is experimental.</span></span>

<span data-ttu-id="3e52d-200">PowerShell, [mimari Linux][] kullanıcı deposundan (AUR) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3e52d-200">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="3e52d-201">[En son etiketli sürümle][arch-release] derlenebilir</span><span class="sxs-lookup"><span data-stu-id="3e52d-201">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="3e52d-202">[En son işlemeden ana şablona][arch-git] derlenebilir</span><span class="sxs-lookup"><span data-stu-id="3e52d-202">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="3e52d-203">[En son sürüm ikilisi][arch-bin] kullanılarak yüklenebilir</span><span class="sxs-lookup"><span data-stu-id="3e52d-203">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="3e52d-204">AUR 'teki paketler topluluk tarafından korunur; resmi olmayan destek yoktur.</span><span class="sxs-lookup"><span data-stu-id="3e52d-204">Packages in the AUR are community maintained; there's no official support.</span></span>

<span data-ttu-id="3e52d-205">AUR 'ten paket yükleme hakkında daha fazla bilgi için bkz. [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) veya Community [dockerfile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="3e52d-205">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Mimari Linux]: https://www.archlinux.org/download/
[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="3e52d-207">Yaslama paketi</span><span class="sxs-lookup"><span data-stu-id="3e52d-207">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="3e52d-208">Anlık görüntü alınıyor</span><span class="sxs-lookup"><span data-stu-id="3e52d-208">Getting snapd</span></span>

<span data-ttu-id="3e52d-209">`snapd`yapış çalıştırmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="3e52d-209">`snapd` is required to run snaps.</span></span> <span data-ttu-id="3e52d-210">Yüklediğinizden emin `snapd` olmak için [Bu yönergeleri](https://docs.snapcraft.io/core/install) kullanın.</span><span class="sxs-lookup"><span data-stu-id="3e52d-210">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="3e52d-211">Yaslama aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="3e52d-211">Installation via Snap</span></span>

<span data-ttu-id="3e52d-212">Linux için PowerShell Core, kolay yükleme ve güncelleştirmeler için [Snap deposunda](https://snapcraft.io/store) yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="3e52d-212">PowerShell Core for Linux is published to the [Snap store](https://snapcraft.io/store) for easy installation and updates.</span></span>

<span data-ttu-id="3e52d-213">Tercih edilen yöntem aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="3e52d-213">The preferred method is as follows:</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="3e52d-214">Önizleme sürümünü yüklemek için aşağıdaki yöntemi kullanın:</span><span class="sxs-lookup"><span data-stu-id="3e52d-214">To install a preview version, use the following method:</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="3e52d-215">Yükleme sonrasında, yaslama otomatik olarak yükseltilir.</span><span class="sxs-lookup"><span data-stu-id="3e52d-215">After installation, Snap will automatically upgrade.</span></span> <span data-ttu-id="3e52d-216">`sudo snap refresh powershell` Veya`sudo snap refresh powershell-preview`kullanarak bir yükseltmeyi tetikleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e52d-216">You can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="3e52d-217">CP</span><span class="sxs-lookup"><span data-stu-id="3e52d-217">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="3e52d-218">veya</span><span class="sxs-lookup"><span data-stu-id="3e52d-218">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="3e52d-219">Kalı</span><span class="sxs-lookup"><span data-stu-id="3e52d-219">Kali</span></span>

### <a name="installation---kali"></a><span data-ttu-id="3e52d-220">Yükleme-kalı</span><span class="sxs-lookup"><span data-stu-id="3e52d-220">Installation - Kali</span></span>

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

### <a name="uninstallation---kali"></a><span data-ttu-id="3e52d-221">Kaldırma-kalı</span><span class="sxs-lookup"><span data-stu-id="3e52d-221">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt-get remove -y powershell
```

## <a name="raspbian"></a><span data-ttu-id="3e52d-222">Raspbian</span><span class="sxs-lookup"><span data-stu-id="3e52d-222">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="3e52d-223">Raspbian desteği deneysel.</span><span class="sxs-lookup"><span data-stu-id="3e52d-223">Raspbian support is experimental.</span></span>

<span data-ttu-id="3e52d-224">Şu anda PowerShell yalnızca Raspbian Esnette destekleniyor.</span><span class="sxs-lookup"><span data-stu-id="3e52d-224">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="3e52d-225">CoreCLR ve PowerShell Core yalnızca PI 2 ve PI 3 cihazlarda, [PI sıfır](https://github.com/dotnet/coreclr/issues/10605)gibi diğer cihazlar için de çalışır ve desteklenmeyen bir işlemciye sahip olur.</span><span class="sxs-lookup"><span data-stu-id="3e52d-225">CoreCLR and PowerShell Core will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="3e52d-226">[Raspbian Esnetme](https://www.raspberrypi.org/downloads/raspbian/) Indirin ve PI 'larınızın üzerine ulaşmak için [yükleme yönergelerini](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) izleyin.</span><span class="sxs-lookup"><span data-stu-id="3e52d-226">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="3e52d-227">Yükleme-Raspbian</span><span class="sxs-lookup"><span data-stu-id="3e52d-227">Installation - Raspbian</span></span>

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

<span data-ttu-id="3e52d-228">İsteğe bağlı olarak, `pwsh` ikili dosyanın yolunu belirtmeden PowerShell 'i başlatmak için bir sembolik bağlantı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e52d-228">Optionally, you can create a symbolic link to start PowerShell without specifying the path to the `pwsh` binary.</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="3e52d-229">Kaldırma-Raspbian</span><span class="sxs-lookup"><span data-stu-id="3e52d-229">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="3e52d-230">İkili Arşivler</span><span class="sxs-lookup"><span data-stu-id="3e52d-230">Binary Archives</span></span>

<span data-ttu-id="3e52d-231">PowerShell ikili `tar.gz` arşivleri, Linux platformları için gelişmiş dağıtım senaryolarını etkinleştirmek üzere sağlanır.</span><span class="sxs-lookup"><span data-stu-id="3e52d-231">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="3e52d-232">Bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="3e52d-232">Dependencies</span></span>

<span data-ttu-id="3e52d-233">PowerShell, tüm Linux dağıtımları için taşınabilir ikili dosyalar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3e52d-233">PowerShell builds portable binaries for all Linux distributions.</span></span> <span data-ttu-id="3e52d-234">Ancak, .NET Core çalışma zamanı farklı dağıtımlarda farklı bağımlılıklar gerektirir ve PowerShell de çok fazla yapılır.</span><span class="sxs-lookup"><span data-stu-id="3e52d-234">But, .NET Core runtime requires different dependencies on different distributions, and PowerShell does too.</span></span>

<span data-ttu-id="3e52d-235">Aşağıdaki grafikte, farklı Linux dağıtımları üzerinde resmi olarak desteklenen .NET Core 2,0 bağımlılıkları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3e52d-235">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="3e52d-236">İşletim sistemi</span><span class="sxs-lookup"><span data-stu-id="3e52d-236">OS</span></span>                 | <span data-ttu-id="3e52d-237">Bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="3e52d-237">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="3e52d-238">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="3e52d-238">Ubuntu 16.04</span></span>       | <span data-ttu-id="3e52d-239">libc6, libgcc1, libgssapı-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="3e52d-239">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="3e52d-240">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="3e52d-240">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="3e52d-241">Ubuntu 17,10</span><span class="sxs-lookup"><span data-stu-id="3e52d-241">Ubuntu 17.10</span></span>       | <span data-ttu-id="3e52d-242">libc6, libgcc1, libgssapı-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="3e52d-242">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="3e52d-243">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="3e52d-243">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="3e52d-244">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="3e52d-244">Ubuntu 18.04</span></span>       | <span data-ttu-id="3e52d-245">libc6, libgcc1, libgssapı-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="3e52d-245">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="3e52d-246">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="3e52d-246">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="3e52d-247">Desek8 (Jese)</span><span class="sxs-lookup"><span data-stu-id="3e52d-247">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="3e52d-248">libc6, libgcc1, libgssapı-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="3e52d-248">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="3e52d-249">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="3e52d-249">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="3e52d-250">Deda 9 (uzat)</span><span class="sxs-lookup"><span data-stu-id="3e52d-250">Debian 9 (Stretch)</span></span> | <span data-ttu-id="3e52d-251">libc6, libgcc1, libgssapı-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="3e52d-251">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="3e52d-252">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="3e52d-252">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="3e52d-253">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="3e52d-253">CentOS 7</span></span> <br> <span data-ttu-id="3e52d-254">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="3e52d-254">Oracle Linux 7</span></span> <br> <span data-ttu-id="3e52d-255">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="3e52d-255">RHEL 7</span></span> | <span data-ttu-id="3e52d-256">librüzgar, Libya, OpenSSL-libs, libıu</span><span class="sxs-lookup"><span data-stu-id="3e52d-256">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="3e52d-257">openSUSE 42,3</span><span class="sxs-lookup"><span data-stu-id="3e52d-257">openSUSE 42.3</span></span> | <span data-ttu-id="3e52d-258">libcurl4, libopenssl1_0_0, libicu52_1</span><span class="sxs-lookup"><span data-stu-id="3e52d-258">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="3e52d-259">openSUSE artık 15</span><span class="sxs-lookup"><span data-stu-id="3e52d-259">openSUSE Leap 15</span></span> | <span data-ttu-id="3e52d-260">libcurl4, libopenssl1_0_0, libicu60_2</span><span class="sxs-lookup"><span data-stu-id="3e52d-260">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="3e52d-261">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="3e52d-261">Fedora 27</span></span> <br> <span data-ttu-id="3e52d-262">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="3e52d-262">Fedora 28</span></span> | <span data-ttu-id="3e52d-263">libıwind, libkıvrık, OpenSSL-libs, libıu, COMPAT-openssl10</span><span class="sxs-lookup"><span data-stu-id="3e52d-263">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="3e52d-264">Resmi olarak desteklenmeyen Linux dağıtımlarına PowerShell ikilileri dağıtmak için, hedef işletim sistemi için gerekli bağımlılıkları ayrı adımlarda yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3e52d-264">To deploy PowerShell binaries on Linux distributions that aren't officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span> <span data-ttu-id="3e52d-265">Örneğin, [Amazon Linux dockerfile][amazon-dockerfile] , önce bağımlılıkları yüklüyor ve ardından Linux `tar.gz` arşivini ayıklar.</span><span class="sxs-lookup"><span data-stu-id="3e52d-265">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="3e52d-266">Yükleme-Ikili arşivleri</span><span class="sxs-lookup"><span data-stu-id="3e52d-266">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="3e52d-267">Linux</span><span class="sxs-lookup"><span data-stu-id="3e52d-267">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="3e52d-268">İkili arşivleri kaldırma</span><span class="sxs-lookup"><span data-stu-id="3e52d-268">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="3e52d-269">Yollar</span><span class="sxs-lookup"><span data-stu-id="3e52d-269">Paths</span></span>

* <span data-ttu-id="3e52d-270">`$PSHOME`eklenir`/opt/microsoft/powershell/6.2.0/`</span><span class="sxs-lookup"><span data-stu-id="3e52d-270">`$PSHOME` is `/opt/microsoft/powershell/6.2.0/`</span></span>
* <span data-ttu-id="3e52d-271">Kullanıcı profilleri şuradan okunacaktır`~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="3e52d-271">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="3e52d-272">Varsayılan profiller buradan okunacaktır`$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="3e52d-272">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="3e52d-273">Kullanıcı modülleri okunacaktır`~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="3e52d-273">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="3e52d-274">Paylaşılan modüller buradan okunacaktır`/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="3e52d-274">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="3e52d-275">Varsayılan modüller okunacaktır`$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="3e52d-275">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="3e52d-276">PSReadline geçmişi şu şekilde kaydedilecek`~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="3e52d-276">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="3e52d-277">Profiller, PowerShell 'in konak başına yapılandırmasını kabul eder; bu nedenle, varsayılan konağa özgü profiller aynı konumlarda `Microsoft.PowerShell_profile.ps1` bulunur.</span><span class="sxs-lookup"><span data-stu-id="3e52d-277">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="3e52d-278">PowerShell, Linux üzerinde [xdg taban dizini belirtimine][xdg-bds] uyar.</span><span class="sxs-lookup"><span data-stu-id="3e52d-278">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[yayınları]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
