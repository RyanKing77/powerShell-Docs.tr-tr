# <a name="installing-powershell-core-on-macos-and-linux"></a><span data-ttu-id="0481b-101">PowerShell çekirdek yüklemek macOS ve Linux</span><span class="sxs-lookup"><span data-stu-id="0481b-101">Installing PowerShell Core on macOS and Linux</span></span>

<span data-ttu-id="0481b-102">Destekler [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.04] [ u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7] [ cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 25 ] [ fed25], [Fedora 26][fed26], [Arch Linux][arch]ve [macOS 10,12][mac].</span><span class="sxs-lookup"><span data-stu-id="0481b-102">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.04][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 25][fed25], [Fedora 26][fed26], [Arch Linux][arch], and [macOS 10.12][mac].</span></span>

<span data-ttu-id="0481b-103">Resmi olarak desteklenmez Linux dağıtımları için kullanmayı deneyebilirsiniz [PowerShell AppImage][lai].</span><span class="sxs-lookup"><span data-stu-id="0481b-103">For Linux distributions that are not officially supported, you can try using the [PowerShell AppImage][lai].</span></span>
<span data-ttu-id="0481b-104">Ayrıca Linux kullanarak doğrudan PowerShell ikili dosyaları dağıtma deneyebilirsiniz [ `tar.gz` arşiv][tar], ancak işletim sisteminde ayrı adımlar göre gerekli bağımlılıkları ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0481b-104">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="0481b-105">Tüm paketler bizim Github'da bulunan [serbest][] sayfası.</span><span class="sxs-lookup"><span data-stu-id="0481b-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="0481b-106">Paket yüklendikten sonra çalıştırmak `pwsh` bir terminal gelen.</span><span class="sxs-lookup"><span data-stu-id="0481b-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u17]: #ubuntu-1704
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse-422
[fed25]: #fedora-25
[fed26]: #fedora-26
[arch]: #arch-linux
[lai]: #linux-appimage
[mac]: #macos-1012
[tar]: #binary-archives

## <a name="ubuntu-1404"></a><span data-ttu-id="0481b-107">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="0481b-107">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="0481b-108">Paket Deposu - Ubuntu 14.04 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="0481b-108">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="0481b-109">Linux için PowerShell çekirdek paket depoları kolay yükleme (ve güncelleştirmeleri) için yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="0481b-109">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="0481b-110">Bu tercih edilen yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="0481b-110">This is the preferred method.</span></span>

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

<span data-ttu-id="0481b-111">Microsoft depo süper kullanıcı bir kez kaydolduktan sonra daha sonra kullanmak yeterlidir `sudo apt-get upgrade powershell` güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="0481b-111">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="0481b-112">Doğrudan indirme - Ubuntu 14.04 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="0481b-112">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="0481b-113">Debian paketi Yükle `powershell_6.0.0-rc-1.ubuntu.14.04_amd64.deb` gelen [serbest][] Ubuntu makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="0481b-113">Download the Debian package `powershell_6.0.0-rc-1.ubuntu.14.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="0481b-114">Ardından aşağıdaki terminale yürütün:</span><span class="sxs-lookup"><span data-stu-id="0481b-114">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-rc-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="0481b-115">Lütfen unutmayın `dpkg -i` başarısız unmet bağımlılıkları; sonraki komut `apt-get install -f` Bu çözümler ve daha sonra PowerShell paketi yapılandırma tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="0481b-115">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="0481b-116">Kaldırma - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="0481b-116">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="0481b-117">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="0481b-117">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="0481b-118">Paket Deposu - Ubuntu 16.04 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="0481b-118">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="0481b-119">Linux için PowerShell çekirdek paket depoları kolay yükleme (ve güncelleştirmeleri) için yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="0481b-119">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="0481b-120">Bu tercih edilen yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="0481b-120">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list | sudo tee /etc/apt/sources.list.d/microsoft.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="0481b-121">Microsoft depo süper kullanıcı bir kez kaydolduktan sonra daha sonra kullanmak yeterlidir `sudo apt-get upgrade powershell` güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="0481b-121">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="0481b-122">Doğrudan indirme - Ubuntu 16.04 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="0481b-122">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="0481b-123">Debian paketi Yükle `powershell_6.0.0-rc-1.ubuntu.16.04_amd64.deb` gelen [serbest][] Ubuntu makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="0481b-123">Download the Debian package `powershell_6.0.0-rc-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="0481b-124">Ardından aşağıdaki terminale yürütün:</span><span class="sxs-lookup"><span data-stu-id="0481b-124">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-rc-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="0481b-125">Lütfen unutmayın `dpkg -i` başarısız unmet bağımlılıkları; sonraki komut `apt-get install -f` Bu çözümler ve daha sonra PowerShell paketi yapılandırma tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="0481b-125">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="0481b-126">Kaldırma - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="0481b-126">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1704"></a><span data-ttu-id="0481b-127">Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="0481b-127">Ubuntu 17.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1704"></a><span data-ttu-id="0481b-128">Paket Deposu - Ubuntu 17.04 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="0481b-128">Installation via Package Repository - Ubuntu 17.04</span></span>

<span data-ttu-id="0481b-129">Linux için PowerShell çekirdek paket depoları kolay yükleme (ve güncelleştirmeleri) için yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="0481b-129">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="0481b-130">Bu tercih edilen yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="0481b-130">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
curl https://packages.microsoft.com/config/ubuntu/17.04/prod.list | sudo tee /etc/apt/sources.list.d/microsoft.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="0481b-131">Microsoft depo süper kullanıcı bir kez kaydolduktan sonra daha sonra kullanmak yeterlidir `sudo apt-get upgrade powershell` güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="0481b-131">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1704"></a><span data-ttu-id="0481b-132">Doğrudan indirme - Ubuntu 17.04 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="0481b-132">Installation via Direct Download - Ubuntu 17.04</span></span>

<span data-ttu-id="0481b-133">Debian paketi Yükle `powershell_6.0.0-rc-1.ubuntu.17.04_amd64.deb` gelen [serbest][] Ubuntu makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="0481b-133">Download the Debian package `powershell_6.0.0-rc-1.ubuntu.17.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="0481b-134">Ardından aşağıdaki terminale yürütün:</span><span class="sxs-lookup"><span data-stu-id="0481b-134">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-rc-1.ubuntu.17.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="0481b-135">Lütfen unutmayın `dpkg -i` başarısız unmet bağımlılıkları; sonraki komut `apt-get install -f` Bu çözümler ve daha sonra PowerShell paketi yapılandırma tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="0481b-135">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1704"></a><span data-ttu-id="0481b-136">Kaldırma - Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="0481b-136">Uninstallation - Ubuntu 17.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-8"></a><span data-ttu-id="0481b-137">Debian 8</span><span class="sxs-lookup"><span data-stu-id="0481b-137">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="0481b-138">Paket Deposu - Debian 8 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="0481b-138">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="0481b-139">Linux için PowerShell çekirdek paket depoları kolay yükleme (ve güncelleştirmeleri) için yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="0481b-139">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="0481b-140">Bu tercih edilen yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="0481b-140">This is the preferred method.</span></span>

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

<span data-ttu-id="0481b-141">Microsoft depo süper kullanıcı bir kez kaydolduktan sonra daha sonra kullanmak yeterlidir `sudo apt-get upgrade powershell` güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="0481b-141">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="0481b-142">Aracılığıyla doğrudan indirme - Debian 8 yükleme</span><span class="sxs-lookup"><span data-stu-id="0481b-142">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="0481b-143">Debian paketi Yükle `powershell_6.0.0-rc-1.debian.8_amd64.deb` gelen [serbest][] Debian makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="0481b-143">Download the Debian package `powershell_6.0.0-rc-1.debian.8_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="0481b-144">Ardından aşağıdaki terminale yürütün:</span><span class="sxs-lookup"><span data-stu-id="0481b-144">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-rc-1.debian.8_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="0481b-145">Lütfen unutmayın `dpkg -i` başarısız unmet bağımlılıkları; sonraki komut `apt-get install -f` Bu çözümler ve daha sonra PowerShell paketi yapılandırma tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="0481b-145">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="0481b-146">Kaldırma - Debian 8</span><span class="sxs-lookup"><span data-stu-id="0481b-146">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="0481b-147">Debian 9</span><span class="sxs-lookup"><span data-stu-id="0481b-147">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="0481b-148">Paket Deposu - Debian 9 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="0481b-148">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="0481b-149">Linux için PowerShell çekirdek paket depoları kolay yükleme (ve güncelleştirmeleri) için yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="0481b-149">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="0481b-150">Bu tercih edilen yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="0481b-150">This is the preferred method.</span></span>

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

<span data-ttu-id="0481b-151">Microsoft depo süper kullanıcı bir kez kaydolduktan sonra daha sonra kullanmak yeterlidir `sudo apt-get upgrade powershell` güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="0481b-151">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="0481b-152">Doğrudan indirme - Debian 9 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="0481b-152">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="0481b-153">Debian paketi Yükle `powershell_6.0.0-rc-1.debian.9_amd64.deb` gelen [serbest][] Debian makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="0481b-153">Download the Debian package `powershell_6.0.0-rc-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="0481b-154">Ardından aşağıdaki terminale yürütün:</span><span class="sxs-lookup"><span data-stu-id="0481b-154">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-rc-1.debian.9_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="0481b-155">Lütfen unutmayın `dpkg -i` başarısız unmet bağımlılıkları; sonraki komut `apt-get install -f` Bu çözümler ve daha sonra PowerShell paketi yapılandırma tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="0481b-155">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-9"></a><span data-ttu-id="0481b-156">Kaldırma - Debian 9</span><span class="sxs-lookup"><span data-stu-id="0481b-156">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="0481b-157">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="0481b-157">CentOS 7</span></span>

> <span data-ttu-id="0481b-158">Bu paket, Oracle Linux 7'de de çalışır.</span><span class="sxs-lookup"><span data-stu-id="0481b-158">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="0481b-159">Paket (önerilen) - deposu CentOS 7 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="0481b-159">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="0481b-160">Linux için PowerShell çekirdek kolay yükleme (ve güncelleştirmeleri) için resmi Microsoft depoları yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="0481b-160">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="0481b-161">Microsoft depo süper kullanıcı bir kez kaydolduktan sonra kullanmak yeterlidir `sudo yum update powershell` PowerShell güncelleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="0481b-161">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="0481b-162">Doğrudan indirme - CentOS 7 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="0481b-162">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="0481b-163">Kullanarak [CentOS 7][], RPM paketi Yükle `powershell-6.0.0_rc-1.rhel.7.x86_64.rpm` gelen [serbest][] CentOS makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="0481b-163">Using [CentOS 7][], download the RPM package `powershell-6.0.0_rc-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="0481b-164">Ardından aşağıdaki terminale yürütün:</span><span class="sxs-lookup"><span data-stu-id="0481b-164">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="0481b-165">Ayrıca, indirilmesi ara adım olmadan RPM yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0481b-165">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-rc/powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="0481b-166">Kaldırma - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="0481b-166">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="0481b-168">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="0481b-168">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="0481b-169">Paket (önerilen) - deposu Red Hat Enterprise Linux (RHEL) 7 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="0481b-169">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="0481b-170">Linux için PowerShell çekirdek kolay yükleme (ve güncelleştirmeleri) için resmi Microsoft depoları yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="0481b-170">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="0481b-171">Microsoft depo süper kullanıcı bir kez kaydolduktan sonra kullanmak yeterlidir `sudo yum update powershell` PowerShell güncelleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="0481b-171">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="0481b-172">Doğrudan indirme - Red Hat Enterprise Linux (RHEL) 7 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="0481b-172">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="0481b-173">RPM paketi Yükle `powershell-6.0.0_rc-1.rhel.7.x86_64.rpm` gelen [serbest][] Red Hat Enterprise Linux makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="0481b-173">Download the RPM package `powershell-6.0.0_rc-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="0481b-174">Ardından aşağıdaki terminale yürütün:</span><span class="sxs-lookup"><span data-stu-id="0481b-174">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="0481b-175">Ayrıca, indirilmesi ara adım olmadan RPM yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0481b-175">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-rc/powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="0481b-176">Kaldırma - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="0481b-176">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse-422"></a><span data-ttu-id="0481b-177">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="0481b-177">OpenSUSE 42.2</span></span>

> <span data-ttu-id="0481b-178">**Not:** PowerShell çekirdek yüklerken OpenSUSE hiçbir şey sağladığını bildirebilir `libcurl`.</span><span class="sxs-lookup"><span data-stu-id="0481b-178">**Note:** When installing PowerShell Core, OpenSUSE may report that nothing provides `libcurl`.</span></span>
<span data-ttu-id="0481b-179">`libcurl`OpenSUSE desteklenen sürümleri önceden yüklenmiş olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0481b-179">`libcurl` should already be installed on supported versions of OpenSUSE.</span></span>
<span data-ttu-id="0481b-180">Çalıştırma `zypper search libcurl` onaylamak için.</span><span class="sxs-lookup"><span data-stu-id="0481b-180">Run `zypper search libcurl` to confirm.</span></span>
<span data-ttu-id="0481b-181">Hata 2 'çözümleri' sunacaktır.</span><span class="sxs-lookup"><span data-stu-id="0481b-181">The error will present 2 'solutions'.</span></span> <span data-ttu-id="0481b-182">'Çözüm PowerShell çekirdek yüklemeye devam etmek için 2' i seçin.</span><span class="sxs-lookup"><span data-stu-id="0481b-182">Choose 'Solution 2' to continue installing PowerShell Core.</span></span>

### <a name="installation-via-package-repository-preferred---opensuse-422"></a><span data-ttu-id="0481b-183">Paket (önerilen) - deposu OpenSUSE 42.2 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="0481b-183">Installation via Package Repository (preferred) - OpenSUSE 42.2</span></span>

<span data-ttu-id="0481b-184">Linux için PowerShell çekirdek kolay yükleme (ve güncelleştirmeleri) için resmi Microsoft depoları yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="0481b-184">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Add the Microsoft Product feed
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/zypp/repos.d/microsoft.repo

# Update the list of products
sudo zypper update

# Install PowerShell
sudo zypper install powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---opensuse-422"></a><span data-ttu-id="0481b-185">Doğrudan indirme - OpenSUSE 42.2 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="0481b-185">Installation via Direct Download - OpenSUSE 42.2</span></span>

<span data-ttu-id="0481b-186">RPM paketi Yükle `powershell-6.0.0_rc-1.rhel.7.x86_64.rpm` gelen [serbest][] OpenSUSE makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="0481b-186">Download the RPM package `powershell-6.0.0_rc-1.rhel.7.x86_64.rpm` from the [releases][] page onto the OpenSUSE machine.</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="0481b-187">Ayrıca, indirilmesi ara adım olmadan RPM yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0481b-187">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-rc/powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-422"></a><span data-ttu-id="0481b-188">Kaldırma - OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="0481b-188">Uninstallation - OpenSUSE 42.2</span></span>

```sh
sudo zypper remove powershell
```

## <a name="fedora-25"></a><span data-ttu-id="0481b-189">Fedora 25</span><span class="sxs-lookup"><span data-stu-id="0481b-189">Fedora 25</span></span>

### <a name="installation-via-package-repository-preferred---fedora-25"></a><span data-ttu-id="0481b-190">Paket (önerilen) - deposu Fedora 25 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="0481b-190">Installation via Package Repository (preferred) - Fedora 25</span></span>

<span data-ttu-id="0481b-191">Linux için PowerShell çekirdek kolay yükleme (ve güncelleştirmeleri) için resmi Microsoft depoları yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="0481b-191">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Update the list of products
sudo dnf update

# Install PowerShell
sudo dnf install -y powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---fedora-25"></a><span data-ttu-id="0481b-192">Doğrudan indirme - Fedora 25 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="0481b-192">Installation via Direct Download - Fedora 25</span></span>

<span data-ttu-id="0481b-193">RPM paketi Yükle `powershell-6.0.0_rc-1.rhel.7.x86_64.rpm` gelen [serbest][] Fedora makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="0481b-193">Download the RPM package `powershell-6.0.0_rc-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="0481b-194">Ardından aşağıdaki terminale yürütün:</span><span class="sxs-lookup"><span data-stu-id="0481b-194">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="0481b-195">Ayrıca, indirilmesi ara adım olmadan RPM yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0481b-195">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-rc/powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-25"></a><span data-ttu-id="0481b-196">Kaldırma - Fedora 25</span><span class="sxs-lookup"><span data-stu-id="0481b-196">Uninstallation - Fedora 25</span></span>

```sh
sudo dnf remove powershell
```

## <a name="fedora-26"></a><span data-ttu-id="0481b-197">Fedora 26</span><span class="sxs-lookup"><span data-stu-id="0481b-197">Fedora 26</span></span>

### <a name="installation-via-package-repository-preferred---fedora-26"></a><span data-ttu-id="0481b-198">Paket (önerilen) - deposu Fedora 26 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="0481b-198">Installation via Package Repository (preferred) - Fedora 26</span></span>

<span data-ttu-id="0481b-199">Linux için PowerShell çekirdek kolay yükleme (ve güncelleştirmeleri) için resmi Microsoft depoları yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="0481b-199">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-26"></a><span data-ttu-id="0481b-200">Doğrudan indirme - Fedora 26 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="0481b-200">Installation via Direct Download - Fedora 26</span></span>

<span data-ttu-id="0481b-201">RPM paketi Yükle `powershell-6.0.0_rc-1.rhel.7.x86_64.rpm` gelen [serbest][] Fedora makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="0481b-201">Download the RPM package `powershell-6.0.0_rc-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="0481b-202">Ardından aşağıdaki terminale yürütün:</span><span class="sxs-lookup"><span data-stu-id="0481b-202">Then execute the following in the terminal:</span></span>

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="0481b-203">Ayrıca, indirilmesi ara adım olmadan RPM yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0481b-203">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-rc/powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-26"></a><span data-ttu-id="0481b-204">Kaldırma - Fedora 26</span><span class="sxs-lookup"><span data-stu-id="0481b-204">Uninstallation - Fedora 26</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="0481b-205">Linux arch</span><span class="sxs-lookup"><span data-stu-id="0481b-205">Arch Linux</span></span>

<span data-ttu-id="0481b-206">PowerShell edinilebilir [Arch Linux][] kullanıcı deposu (AUR).</span><span class="sxs-lookup"><span data-stu-id="0481b-206">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="0481b-207">İle derlenebilir [en son sürüm etiketli][arch-release]</span><span class="sxs-lookup"><span data-stu-id="0481b-207">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="0481b-208">Nden derlenebilir [ana son yürütme][arch-git]</span><span class="sxs-lookup"><span data-stu-id="0481b-208">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="0481b-209">Kullanılarak yüklenebilir [ikili en son sürüm][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="0481b-209">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="0481b-210">AUR paketlerinde saklanır topluluk - resmi desteği yoktur.</span><span class="sxs-lookup"><span data-stu-id="0481b-210">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="0481b-211">AUR paketleri yükleme hakkında daha fazla bilgi için bkz: [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) veya topluluk [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="0481b-211">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="linux-appimage"></a><span data-ttu-id="0481b-213">Linux AppImage</span><span class="sxs-lookup"><span data-stu-id="0481b-213">Linux AppImage</span></span>

<span data-ttu-id="0481b-214">Son Linux dağıtım kullanarak karşıdan AppImage `powershell-6.0.0-rc-x86_64.AppImage` gelen [serbest][] Linux makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="0481b-214">Using a recent Linux distribution, download the AppImage `powershell-6.0.0-rc-x86_64.AppImage` from the [releases][] page onto the Linux machine.</span></span>

<span data-ttu-id="0481b-215">Ardından aşağıdaki terminale yürütün:</span><span class="sxs-lookup"><span data-stu-id="0481b-215">Then execute the following in the terminal:</span></span>

```bash
chmod a+x powershell-6.0.0-rc-x86_64.AppImage
./powershell-6.0.0-rc-x86_64.AppImage
```

<span data-ttu-id="0481b-216">[AppImage][] yüklemeden PowerShell çalıştırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="0481b-216">The [AppImage][] lets you run PowerShell without installing it.</span></span>
<span data-ttu-id="0481b-217">PowerShell ve bağımlılıklarını (.NET Core'nın sistem bağımlılıklar dahil olmak üzere) bağlı bir pakete sunmaktadır taşınabilir bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="0481b-217">It is a portable application that bundles PowerShell and its dependencies (including .NET Core's system dependencies) into one cohesive package.</span></span>
<span data-ttu-id="0481b-218">Bu paket, kullanıcının Linux dağıtım bağımsız olarak çalışır ve tek bir ikili dosyadır.</span><span class="sxs-lookup"><span data-stu-id="0481b-218">This package works independently of the user's Linux distribution, and is a single binary.</span></span>

[appimage]: http://appimage.org/

## <a name="macos-1012"></a><span data-ttu-id="0481b-220">macOS 10,12</span><span class="sxs-lookup"><span data-stu-id="0481b-220">macOS 10.12</span></span>

### <a name="installation-via-homebrew-preferred---macos-1012"></a><span data-ttu-id="0481b-221">(Önerilen) - Homebrew macOS 10,12 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="0481b-221">Installation via Homebrew (preferred) - macOS 10.12</span></span>

<span data-ttu-id="0481b-222">[Homebrew] [ brew] macOS için eksik Paket Yöneticisi.</span><span class="sxs-lookup"><span data-stu-id="0481b-222">[Homebrew][brew] is the missing package manager for macOS.</span></span>
<span data-ttu-id="0481b-223">Varsa `brew` komutu bulunamadı, Homebrew aşağıdaki yüklemenize gerek [kendi yönergeleri][brew].</span><span class="sxs-lookup"><span data-stu-id="0481b-223">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

<span data-ttu-id="0481b-224">Homebrew yükledikten sonra PowerShell yükleme kolaydır.</span><span class="sxs-lookup"><span data-stu-id="0481b-224">Once you've installed Homebrew, installing PowerShell is easy.</span></span>
<span data-ttu-id="0481b-225">İlk olarak, yükleme [Homebrew Cask][cask], daha fazla paket yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0481b-225">First, install [Homebrew-Cask][cask], so you can install more packages:</span></span>

```sh
brew tap caskroom/cask
```

<span data-ttu-id="0481b-226">Şimdi, PowerShell yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0481b-226">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="0481b-227">PowerShell yeni sürümleri yayımlandığında, yalnızca Homebrew'ın formül güncelleştirin ve PowerShell yükseltme:</span><span class="sxs-lookup"><span data-stu-id="0481b-227">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask reinstall powershell
```

> <span data-ttu-id="0481b-228">Not: nedeniyle, [Cask bu sorunu](https://github.com/caskroom/homebrew-cask/issues/29301), şu anda yükseltmek için bir yeniden yükleme yapmak zorunda.</span><span class="sxs-lookup"><span data-stu-id="0481b-228">Note: because of [this issue in Cask](https://github.com/caskroom/homebrew-cask/issues/29301), you currently have to do a reinstall to upgrade.</span></span>

[brew]: http://brew.sh/
[cask]: https://caskroom.github.io/

### <a name="installation-via-direct-download---macos-1012"></a><span data-ttu-id="0481b-229">Doğrudan indirme - macOS 10,12 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="0481b-229">Installation via Direct Download - macOS 10.12</span></span>

<span data-ttu-id="0481b-230">MacOS 10,12 kullanarak PKG paketini indirin `powershell-6.0.0-rc-osx.10.12-x64.pkg` gelen [serbest][] macOS makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="0481b-230">Using macOS 10.12, download the PKG package `powershell-6.0.0-rc-osx.10.12-x64.pkg` from the [releases][] page onto the macOS machine.</span></span>

<span data-ttu-id="0481b-231">Dosyaya çift tıklayın ve yönergeleri izleyin veya terminal durumundan yükleyin:</span><span class="sxs-lookup"><span data-stu-id="0481b-231">Either double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.0.0-rc-osx.10.12-x64.pkg -target /
```

### <a name="uninstallation---macos-1012"></a><span data-ttu-id="0481b-232">Kaldırma - macOS 10,12</span><span class="sxs-lookup"><span data-stu-id="0481b-232">Uninstallation - macOS 10.12</span></span>

<span data-ttu-id="0481b-233">PowerShell ile Homebrew yüklediyseniz, kaldırma işlemi kolaydır:</span><span class="sxs-lookup"><span data-stu-id="0481b-233">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="0481b-234">PowerShell doğrudan indirme yüklediyseniz, PowerShell el ile kaldırılması gerekir:</span><span class="sxs-lookup"><span data-stu-id="0481b-234">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="0481b-235">Ek PowerShell yolları (örneğin, kullanıcı profili yolu) kaldırmak için lütfen bkz [yolları] [ paths] bu belgede bölüm aşağıda ve istenen kaldırma ile yolları `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="0481b-235">To uninstall the additional PowerShell paths (such as the user profile path) please see the [paths][paths] section below in this document and remove the desired the paths with `sudo rm`.</span></span>
<span data-ttu-id="0481b-236">(Not: Bu ile Homebrew yüklediyseniz gerekli değildir.)</span><span class="sxs-lookup"><span data-stu-id="0481b-236">(Note: this is not necessary if you installed with Homebrew.)</span></span>

[paths]:#paths

## <a name="kali"></a><span data-ttu-id="0481b-237">Kali</span><span class="sxs-lookup"><span data-stu-id="0481b-237">Kali</span></span>

### <a name="installation"></a><span data-ttu-id="0481b-238">Yükleme</span><span class="sxs-lookup"><span data-stu-id="0481b-238">Installation</span></span>

```sh
# Install prerequisites
apt-get install libunwind8 libicu55
wget http://security.debian.org/debian-security/pool/updates/main/o/openssl/libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb
dpkg -i libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb

# Install PowerShell
dpkg -i powershell_6.0.0-rc-1.ubuntu.16.04_amd64.deb

# Start PowerShell
pwsh
```

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a><span data-ttu-id="0481b-239">PowerShell yüklemeden son Kali içinde (GNU/Linux Kali çalışırken) çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0481b-239">Run PowerShell in latest Kali (Kali GNU/Linux Rolling) without installing it</span></span>

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-rc/powershell-6.0.0-rc-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.0-rc-x86_64.AppImage

# Start PowerShell
./powershell-6.0.0-rc-x86_64.AppImage
```

### <a name="uninstallation---kali"></a><span data-ttu-id="0481b-240">Kaldırma - Kali</span><span class="sxs-lookup"><span data-stu-id="0481b-240">Uninstallation - Kali</span></span>

```sh
dpkg -r powershell_6.0.0-rc-1.ubuntu.16.04_amd64.deb
```

## <a name="raspbian"></a><span data-ttu-id="0481b-241">Raspbian</span><span class="sxs-lookup"><span data-stu-id="0481b-241">Raspbian</span></span>

<span data-ttu-id="0481b-242">Şu anda, PowerShell yalnızca Raspbian Esnetme üzerinde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="0481b-242">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

### <a name="installation"></a><span data-ttu-id="0481b-243">Yükleme</span><span class="sxs-lookup"><span data-stu-id="0481b-243">Installation</span></span>

```sh
# Install prerequisites
sudo apt-get install libunwind8

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-rc/powershell-6.0.0-rc-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.0.0-rc-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="0481b-244">Kaldırma - Raspbian</span><span class="sxs-lookup"><span data-stu-id="0481b-244">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="0481b-245">İkili arşivler</span><span class="sxs-lookup"><span data-stu-id="0481b-245">Binary Archives</span></span>

<span data-ttu-id="0481b-246">PowerShell ikili `tar.gz` arşivler macOS ve gelişmiş dağıtım senaryoları etkinleştirmek için Linux platformlar için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="0481b-246">PowerShell binary `tar.gz` archives are provided for macOS and Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="0481b-247">Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="0481b-247">Dependencies</span></span>

<span data-ttu-id="0481b-248">Linux için PowerShell tüm Linux dağıtımları için taşınabilir ikili dosyalarını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0481b-248">For Linux, PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="0481b-249">Ancak farklı dağıtımların farklı bağımlılıkları .NET çekirdeği çalışma zamanı gerektirir ve bu nedenle PowerShell aynı değil.</span><span class="sxs-lookup"><span data-stu-id="0481b-249">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="0481b-250">Aşağıdaki grafikte .NET Core 2.0 bağımlılıkları resmi olarak desteklenen farklı Linux dağıtımları üzerinde gösterir.</span><span class="sxs-lookup"><span data-stu-id="0481b-250">The following chart shows the .NET Core 2.0 dependencies on different Linux distributions that are officially supported.</span></span>

| <span data-ttu-id="0481b-251">İşletim sistemi</span><span class="sxs-lookup"><span data-stu-id="0481b-251">OS</span></span>                 | <span data-ttu-id="0481b-252">Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="0481b-252">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="0481b-253">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="0481b-253">Ubuntu 14.04</span></span>       | <span data-ttu-id="0481b-254">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="0481b-254">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="0481b-255">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="0481b-255">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="0481b-256">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="0481b-256">Ubuntu 16.04</span></span>       | <span data-ttu-id="0481b-257">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="0481b-257">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="0481b-258">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="0481b-258">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="0481b-259">Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="0481b-259">Ubuntu 17.04</span></span>       | <span data-ttu-id="0481b-260">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="0481b-260">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="0481b-261">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="0481b-261">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="0481b-262">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="0481b-262">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="0481b-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="0481b-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="0481b-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="0481b-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="0481b-265">Debian 9 (Esnetme)</span><span class="sxs-lookup"><span data-stu-id="0481b-265">Debian 9 (Stretch)</span></span> | <span data-ttu-id="0481b-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="0481b-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="0481b-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="0481b-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="0481b-268">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="0481b-268">CentOS 7</span></span> <br> <span data-ttu-id="0481b-269">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="0481b-269">Oracle Linux 7</span></span> <br> <span data-ttu-id="0481b-270">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="0481b-270">RHEL 7</span></span> <br> <span data-ttu-id="0481b-271">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="0481b-271">OpenSUSE 42.2</span></span> <br> <span data-ttu-id="0481b-272">Fedora 25</span><span class="sxs-lookup"><span data-stu-id="0481b-272">Fedora 25</span></span> | <span data-ttu-id="0481b-273">libunwind, libcurl, openssl kitaplıklar, libicu</span><span class="sxs-lookup"><span data-stu-id="0481b-273">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="0481b-274">Fedora 26</span><span class="sxs-lookup"><span data-stu-id="0481b-274">Fedora 26</span></span>          | <span data-ttu-id="0481b-275">libunwind, libcurl, openssl kitaplıklar, libicu, compat openssl10</span><span class="sxs-lookup"><span data-stu-id="0481b-275">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="0481b-276">Resmi olarak desteklenmez Linux dağıtımları PowerShell ikili dosyaları dağıtmak için hedef işletim sistemi için gerekli bağımlılıkları ayrı adımlarda yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="0481b-276">In order to deploy PowerShell binaries on Linux distributions that are not officially supported, you would need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="0481b-277">Örneğin, bizim [Amazon Linux dockerfile] [ amazon-dockerfile] bağımlılıkları ilk yükler ve Linux ayıklar `tar.gz` arşiv.</span><span class="sxs-lookup"><span data-stu-id="0481b-277">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="0481b-278">Yükleme - ikili arşivler</span><span class="sxs-lookup"><span data-stu-id="0481b-278">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="0481b-279">Linux</span><span class="sxs-lookup"><span data-stu-id="0481b-279">Linux</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-rc/powershell-6.0.0-rc-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/6.0.0-rc

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.0.0-rc

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.0.0-rc/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/6.0.0-rc/pwsh /usr/bin/pwsh
```

#### <a name="macos"></a><span data-ttu-id="0481b-280">MacOS</span><span class="sxs-lookup"><span data-stu-id="0481b-280">macOS</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-rc/powershell-6.0.0-rc-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.0.0-rc

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.0.0-rc

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.0.0-rc/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.0.0-rc/pwsh /usr/local/bin/pwsh
```

### <a name="uninstallation---binary-archives"></a><span data-ttu-id="0481b-281">Kaldırma - ikili arşivler</span><span class="sxs-lookup"><span data-stu-id="0481b-281">Uninstallation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="0481b-282">Linux</span><span class="sxs-lookup"><span data-stu-id="0481b-282">Linux</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

#### <a name="macos"></a><span data-ttu-id="0481b-283">MacOS</span><span class="sxs-lookup"><span data-stu-id="0481b-283">macOS</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="0481b-284">Yollar</span><span class="sxs-lookup"><span data-stu-id="0481b-284">Paths</span></span>

* <span data-ttu-id="0481b-285">`$PSHOME`değil`/opt/microsoft/powershell/6.0.0-rc/`</span><span class="sxs-lookup"><span data-stu-id="0481b-285">`$PSHOME` is `/opt/microsoft/powershell/6.0.0-rc/`</span></span>
* <span data-ttu-id="0481b-286">Kullanıcı profillerini okuma`~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="0481b-286">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="0481b-287">Varsayılan profiller okuma`$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="0481b-287">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="0481b-288">Kullanıcı modülleri okuma`~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="0481b-288">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="0481b-289">Paylaşılan modülleri okuma`/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="0481b-289">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="0481b-290">Varsayılan modülleri okuma`$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="0481b-290">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="0481b-291">PSReadline geçmişi için kaydedilen`~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="0481b-291">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="0481b-292">Varsayılan ana bilgisayar özel profiller var böylece profilleri PowerShell'in başına ana bilgisayar yapılandırması saygı `Microsoft.PowerShell_profile.ps1` aynı konumlarda.</span><span class="sxs-lookup"><span data-stu-id="0481b-292">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="0481b-293">Linux ve macOS, [XDG temel dizin belirtimi] [ xdg-bds] dikkate.</span><span class="sxs-lookup"><span data-stu-id="0481b-293">On Linux and macOS, the [XDG Base Directory Specification][xdg-bds] is respected.</span></span>

<span data-ttu-id="0481b-294">MacOS yerine bir türevi BSD, çünkü unutmayın `/opt`, kullanılan öneki `/usr/local`.</span><span class="sxs-lookup"><span data-stu-id="0481b-294">Note that because macOS is a derivation of BSD, instead of `/opt`, the prefix used is `/usr/local`.</span></span>
<span data-ttu-id="0481b-295">Bu nedenle, `$PSHOME` olan `/usr/local/microsoft/powershell/6.0.0-rc/`, ve simgesel yerleştirilmiş olması `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="0481b-295">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.0.0-rc/`, and the symlink is placed at `/usr/local/bin/pwsh`.</span></span>

[serbest]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
