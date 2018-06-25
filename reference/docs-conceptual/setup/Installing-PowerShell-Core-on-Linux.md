# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="e557c-101">Linux’ta PowerShell Core yükleme</span><span class="sxs-lookup"><span data-stu-id="e557c-101">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="e557c-102">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.10][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="e557c-102">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.10][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="e557c-103">Resmi olarak desteklenmez Linux dağıtımları için kullanmayı deneyebilirsiniz [PowerShell AppImage][lai].</span><span class="sxs-lookup"><span data-stu-id="e557c-103">For Linux distributions that are not officially supported, you can try using the [PowerShell AppImage][lai].</span></span>
<span data-ttu-id="e557c-104">Ayrıca Linux kullanarak doğrudan PowerShell ikili dosyaları dağıtma deneyebilirsiniz [ `tar.gz` arşiv][tar], ancak işletim sisteminde ayrı adımlar göre gerekli bağımlılıkları ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e557c-104">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="e557c-105">Tüm paketler bizim Github'da bulunan [serbest][] sayfası.</span><span class="sxs-lookup"><span data-stu-id="e557c-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="e557c-106">Paket yüklendikten sonra çalıştırmak `pwsh` bir terminal gelen.</span><span class="sxs-lookup"><span data-stu-id="e557c-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u17]: #ubuntu-1710
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse-422
[fedora]: #fedora
[arch]: #arch-linux
[lai]: #linux-appimage
[tar]: #binary-archives

## <a name="ubuntu-1404"></a><span data-ttu-id="e557c-107">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="e557c-107">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="e557c-108">Paket Deposu - Ubuntu 14.04 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="e557c-108">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="e557c-109">Linux için PowerShell çekirdek paket depoları kolay yükleme (ve güncelleştirmeleri) için yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="e557c-109">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="e557c-110">Bu tercih edilen yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="e557c-110">This is the preferred method.</span></span>

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

<span data-ttu-id="e557c-111">Süper kullanıcı Microsoft depoya kaydedin.</span><span class="sxs-lookup"><span data-stu-id="e557c-111">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="e557c-112">Daha sonra kullanmak yeterlidir `sudo apt-get upgrade powershell` yüklemeyi güncelleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="e557c-112">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="e557c-113">Doğrudan indirme - Ubuntu 14.04 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="e557c-113">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="e557c-114">Debian paketi Yükle `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` gelen [serbest][] Ubuntu makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="e557c-114">Download the Debian package `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="e557c-115">Ardından aşağıdaki terminale yürütün:</span><span class="sxs-lookup"><span data-stu-id="e557c-115">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="e557c-116">Lütfen unutmayın `dpkg -i` başarısız unmet bağımlılıkları; sonraki komut `apt-get install -f` Bu çözümler ve daha sonra PowerShell paketi yapılandırma tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="e557c-116">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="e557c-117">Kaldırma - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="e557c-117">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="e557c-118">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="e557c-118">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="e557c-119">Paket Deposu - Ubuntu 16.04 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="e557c-119">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="e557c-120">Linux için PowerShell çekirdek paket depoları kolay yükleme (ve güncelleştirmeleri) için yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="e557c-120">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="e557c-121">Bu tercih edilen yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="e557c-121">This is the preferred method.</span></span>

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

<span data-ttu-id="e557c-122">Microsoft depo süper kullanıcı bir kez kaydolduktan sonra daha sonra kullanmak yeterlidir `sudo apt-get upgrade powershell` güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="e557c-122">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="e557c-123">Doğrudan indirme - Ubuntu 16.04 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="e557c-123">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="e557c-124">Debian paketi Yükle `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` gelen [serbest][] Ubuntu makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="e557c-124">Download the Debian package `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="e557c-125">Ardından aşağıdaki terminale yürütün:</span><span class="sxs-lookup"><span data-stu-id="e557c-125">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="e557c-126">Lütfen unutmayın `dpkg -i` başarısız unmet bağımlılıkları; sonraki komut `apt-get install -f` Bu çözümler ve daha sonra PowerShell paketi yapılandırma tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="e557c-126">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="e557c-127">Kaldırma - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="e557c-127">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1710"></a><span data-ttu-id="e557c-128">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="e557c-128">Ubuntu 17.10</span></span>

> <span data-ttu-id="e557c-129">Not: Sonra Ubuntu 18.04 desteği eklendi `6.1.0-preview.2`</span><span class="sxs-lookup"><span data-stu-id="e557c-129">Note: Support for Ubuntu 18.04 was added after `6.1.0-preview.2`</span></span>

### <a name="installation-via-package-repository---ubuntu-1710"></a><span data-ttu-id="e557c-130">Paket Deposu - Ubuntu 17.10 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="e557c-130">Installation via Package Repository - Ubuntu 17.10</span></span>

<span data-ttu-id="e557c-131">Linux için PowerShell çekirdek paket depoları kolay yükleme (ve güncelleştirmeleri) için yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="e557c-131">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="e557c-132">Bu tercih edilen yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="e557c-132">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/17.10/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="e557c-133">Microsoft depo süper kullanıcı bir kez kaydolduktan sonra daha sonra kullanmak yeterlidir `sudo apt-get upgrade powershell` güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="e557c-133">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1710"></a><span data-ttu-id="e557c-134">Doğrudan indirme - Ubuntu 17.10 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="e557c-134">Installation via Direct Download - Ubuntu 17.10</span></span>

<span data-ttu-id="e557c-135">Debian paketi Yükle `powershell_6.0.2-1.ubuntu.17.10_amd64.deb` gelen [serbest][] Ubuntu makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="e557c-135">Download the Debian package `powershell_6.0.2-1.ubuntu.17.10_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="e557c-136">Ardından aşağıdaki terminale yürütün:</span><span class="sxs-lookup"><span data-stu-id="e557c-136">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.17.10_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="e557c-137">Lütfen unutmayın `dpkg -i` başarısız unmet bağımlılıkları; sonraki komut `apt-get install -f` Bu çözümler ve daha sonra PowerShell paketi yapılandırma tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="e557c-137">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1710"></a><span data-ttu-id="e557c-138">Kaldırma - Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="e557c-138">Uninstallation - Ubuntu 17.10</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="e557c-139">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="e557c-139">Ubuntu 18.04</span></span>

> <span data-ttu-id="e557c-140">Not: Sonra Ubuntu 18.04 desteği eklendi `6.1.0-preview.2`</span><span class="sxs-lookup"><span data-stu-id="e557c-140">Note: Support for Ubuntu 18.04 was added after `6.1.0-preview.2`</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="e557c-141">Paket Deposu - Ubuntu 18.04 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="e557c-141">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="e557c-142">Linux için PowerShell çekirdek paket depoları kolay yükleme (ve güncelleştirmeleri) için yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="e557c-142">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="e557c-143">Bu tercih edilen yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="e557c-143">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/18.04/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="e557c-144">Microsoft depo süper kullanıcı bir kez kaydolduktan sonra daha sonra kullanmak yeterlidir `sudo apt-get upgrade powershell` güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="e557c-144">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="e557c-145">Doğrudan indirme - Ubuntu 18.04 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="e557c-145">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="e557c-146">Debian paketi Yükle `powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb` gelen [serbest][] Ubuntu makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="e557c-146">Download the Debian package `powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="e557c-147">Ardından aşağıdaki terminale yürütün:</span><span class="sxs-lookup"><span data-stu-id="e557c-147">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="e557c-148">Lütfen unutmayın `dpkg -i` başarısız unmet bağımlılıkları; sonraki komut `apt-get install -f` Bu çözümler ve daha sonra PowerShell paketi yapılandırma tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="e557c-148">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1710"></a><span data-ttu-id="e557c-149">Kaldırma - Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="e557c-149">Uninstallation - Ubuntu 17.10</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-8"></a><span data-ttu-id="e557c-150">Debian 8</span><span class="sxs-lookup"><span data-stu-id="e557c-150">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="e557c-151">Paket Deposu - Debian 8 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="e557c-151">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="e557c-152">Linux için PowerShell çekirdek paket depoları kolay yükleme (ve güncelleştirmeleri) için yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="e557c-152">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="e557c-153">Bu tercih edilen yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="e557c-153">This is the preferred method.</span></span>

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

<span data-ttu-id="e557c-154">Microsoft depo süper kullanıcı bir kez kaydolduktan sonra daha sonra kullanmak yeterlidir `sudo apt-get upgrade powershell` güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="e557c-154">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="e557c-155">Aracılığıyla doğrudan indirme - Debian 8 yükleme</span><span class="sxs-lookup"><span data-stu-id="e557c-155">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="e557c-156">Debian paketi Yükle `powershell_6.0.2-1.debian.8_amd64.deb` gelen [serbest][] Debian makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="e557c-156">Download the Debian package `powershell_6.0.2-1.debian.8_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="e557c-157">Ardından aşağıdaki terminale yürütün:</span><span class="sxs-lookup"><span data-stu-id="e557c-157">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="e557c-158">Lütfen unutmayın `dpkg -i` unmet bağımlılıkları ile başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="e557c-158">Please note that `dpkg -i` will fail with unmet dependencies.</span></span>
> <span data-ttu-id="e557c-159">Sonraki komutu `apt-get install -f` Bu çözümler ve daha sonra PowerShell paketi yapılandırma tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="e557c-159">The next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="e557c-160">Kaldırma - Debian 8</span><span class="sxs-lookup"><span data-stu-id="e557c-160">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="e557c-161">Debian 9</span><span class="sxs-lookup"><span data-stu-id="e557c-161">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="e557c-162">Paket Deposu - Debian 9 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="e557c-162">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="e557c-163">Linux için PowerShell çekirdek paket depoları kolay yükleme (ve güncelleştirmeleri) için yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="e557c-163">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="e557c-164">Bu tercih edilen yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="e557c-164">This is the preferred method.</span></span>

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

<span data-ttu-id="e557c-165">Microsoft depo süper kullanıcı bir kez kaydolduktan sonra daha sonra kullanmak yeterlidir `sudo apt-get upgrade powershell` güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="e557c-165">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="e557c-166">Doğrudan indirme - Debian 9 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="e557c-166">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="e557c-167">Debian paketi Yükle `powershell_6.0.2-1.debian.9_amd64.deb` gelen [serbest][] Debian makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="e557c-167">Download the Debian package `powershell_6.0.2-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="e557c-168">Ardından aşağıdaki terminale yürütün:</span><span class="sxs-lookup"><span data-stu-id="e557c-168">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.9_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="e557c-169">Lütfen unutmayın `dpkg -i` unmet bağımlılıkları ile başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="e557c-169">Please note that `dpkg -i` will fail with unmet dependencies.</span></span>
> <span data-ttu-id="e557c-170">Sonraki komutu `apt-get install -f` Bu çözümler ve daha sonra PowerShell paketi yapılandırma tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="e557c-170">The next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-9"></a><span data-ttu-id="e557c-171">Kaldırma - Debian 9</span><span class="sxs-lookup"><span data-stu-id="e557c-171">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="e557c-172">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="e557c-172">CentOS 7</span></span>

> <span data-ttu-id="e557c-173">Bu paket, Oracle Linux 7'de de çalışır.</span><span class="sxs-lookup"><span data-stu-id="e557c-173">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="e557c-174">Paket (önerilen) - deposu CentOS 7 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="e557c-174">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="e557c-175">Linux için PowerShell çekirdek kolay yükleme (ve güncelleştirmeleri) için resmi Microsoft depoları yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="e557c-175">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="e557c-176">Microsoft depo süper kullanıcı bir kez kaydolduktan sonra kullanmak yeterlidir `sudo yum update powershell` PowerShell güncelleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="e557c-176">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="e557c-177">Doğrudan indirme - CentOS 7 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="e557c-177">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="e557c-178">Kullanarak [CentOS 7][], RPM paketi Yükle `powershell-6.0.2-1.rhel.7.x86_64.rpm` gelen [serbest][] CentOS makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="e557c-178">Using [CentOS 7][], download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="e557c-179">Ardından aşağıdaki terminale yürütün:</span><span class="sxs-lookup"><span data-stu-id="e557c-179">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="e557c-180">Ayrıca, indirilmesi ara adım olmadan RPM yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e557c-180">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="e557c-181">Kaldırma - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="e557c-181">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="e557c-183">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="e557c-183">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="e557c-184">Paket (önerilen) - deposu Red Hat Enterprise Linux (RHEL) 7 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="e557c-184">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="e557c-185">Linux için PowerShell çekirdek kolay yükleme (ve güncelleştirmeleri) için resmi Microsoft depoları yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="e557c-185">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="e557c-186">Microsoft depo süper kullanıcı bir kez kaydolduktan sonra kullanmak yeterlidir `sudo yum update powershell` PowerShell güncelleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="e557c-186">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="e557c-187">Doğrudan indirme - Red Hat Enterprise Linux (RHEL) 7 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="e557c-187">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="e557c-188">RPM paketi Yükle `powershell-6.0.2-1.rhel.7.x86_64.rpm` gelen [serbest][] Red Hat Enterprise Linux makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="e557c-188">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="e557c-189">Ardından aşağıdaki terminale yürütün:</span><span class="sxs-lookup"><span data-stu-id="e557c-189">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="e557c-190">Ayrıca, indirilmesi ara adım olmadan RPM yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e557c-190">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="e557c-191">Kaldırma - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="e557c-191">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse-422"></a><span data-ttu-id="e557c-192">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="e557c-192">OpenSUSE 42.2</span></span>

> [!NOTE]
> <span data-ttu-id="e557c-193">PowerShell çekirdek yüklerken `zypper` şu hata rapor edebilir:</span><span class="sxs-lookup"><span data-stu-id="e557c-193">When installing PowerShell Core, `zypper` may report the following error:</span></span>
>
> ```Output
> Problem: nothing provides libcurl needed by powershell-6.0.1-1.rhel.7.x86_64
>  Solution 1: do not install powershell-6.0.1-1.rhel.7.x86_64
>  Solution 2: break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies
> ```
>
> <span data-ttu-id="e557c-194">Bu durumda, doğrulayın uyumlu bir `libcurl` kitaplığı varsa aşağıdaki gösterir komutu denetleyerek `libcurl4` paketini yüklü olarak:</span><span class="sxs-lookup"><span data-stu-id="e557c-194">In this case, verify that a compatible `libcurl` library is present by checking that the following command shows the `libcurl4` package as installed:</span></span>
>
> ```sh
> zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
> ```
>
> <span data-ttu-id="e557c-195">Ardından `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` PowerShell paket yüklerken çözümü.</span><span class="sxs-lookup"><span data-stu-id="e557c-195">Then choose the `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` solution when installing the PowerShell package.</span></span>

### <a name="installation-via-package-repository-preferred---opensuse-422"></a><span data-ttu-id="e557c-196">Paket (önerilen) - deposu OpenSUSE 42.2 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="e557c-196">Installation via Package Repository (preferred) - OpenSUSE 42.2</span></span>

<span data-ttu-id="e557c-197">Linux için PowerShell çekirdek kolay yükleme (ve güncelleştirmeleri) için resmi Microsoft depoları yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="e557c-197">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---opensuse-422"></a><span data-ttu-id="e557c-198">Doğrudan indirme - OpenSUSE 42.2 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="e557c-198">Installation via Direct Download - OpenSUSE 42.2</span></span>

<span data-ttu-id="e557c-199">RPM paketi Yükle `powershell-6.0.2-1.rhel.7.x86_64.rpm` gelen [serbest][] OpenSUSE makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="e557c-199">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the OpenSUSE machine.</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="e557c-200">Ayrıca, indirilmesi ara adım olmadan RPM yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e557c-200">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-422"></a><span data-ttu-id="e557c-201">Kaldırma - OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="e557c-201">Uninstallation - OpenSUSE 42.2</span></span>

```sh
sudo zypper remove powershell
```

## <a name="fedora"></a><span data-ttu-id="e557c-202">Fedora</span><span class="sxs-lookup"><span data-stu-id="e557c-202">Fedora</span></span>

> <span data-ttu-id="e557c-203">Lütfen unutmayın, Fedora 28 yalnızca PowerShell çekirdek 6.1 ve sonraki sürümleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="e557c-203">Please note, Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="e557c-204">Paket (önerilen) - deposu Fedora 27 Fedora 28 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="e557c-204">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="e557c-205">Linux için PowerShell çekirdek kolay yükleme (ve güncelleştirmeleri) için resmi Microsoft depoları yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="e557c-205">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="e557c-206">Doğrudan indirme - Fedora 27, Fedora 28 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="e557c-206">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="e557c-207">RPM paketi Yükle `powershell-6.0.2-1.rhel.7.x86_64.rpm` gelen [serbest][] Fedora makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="e557c-207">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="e557c-208">Ardından aşağıdaki terminale yürütün:</span><span class="sxs-lookup"><span data-stu-id="e557c-208">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="e557c-209">Ayrıca, indirilmesi ara adım olmadan RPM yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e557c-209">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="e557c-210">Kaldırma - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="e557c-210">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="e557c-211">Linux arch</span><span class="sxs-lookup"><span data-stu-id="e557c-211">Arch Linux</span></span>

<span data-ttu-id="e557c-212">PowerShell edinilebilir [Linux arch][] kullanıcı deposu (AUR).</span><span class="sxs-lookup"><span data-stu-id="e557c-212">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="e557c-213">İle derlenebilir [en son sürüm etiketli][arch-release]</span><span class="sxs-lookup"><span data-stu-id="e557c-213">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="e557c-214">Nden derlenebilir [ana son yürütme][arch-git]</span><span class="sxs-lookup"><span data-stu-id="e557c-214">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="e557c-215">Kullanılarak yüklenebilir [ikili en son sürüm][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="e557c-215">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="e557c-216">AUR paketlerinde saklanır topluluk - resmi desteği yoktur.</span><span class="sxs-lookup"><span data-stu-id="e557c-216">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="e557c-217">AUR paketleri yükleme hakkında daha fazla bilgi için bkz: [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) veya topluluk [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="e557c-217">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Linux arch]: https://www.archlinux.org/download/
[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="linux-appimage"></a><span data-ttu-id="e557c-219">Linux AppImage</span><span class="sxs-lookup"><span data-stu-id="e557c-219">Linux AppImage</span></span>

<span data-ttu-id="e557c-220">Son Linux dağıtım kullanarak karşıdan AppImage `powershell-6.0.1-x86_64.AppImage` gelen [serbest][] Linux makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="e557c-220">Using a recent Linux distribution, download the AppImage `powershell-6.0.1-x86_64.AppImage` from the [releases][] page onto the Linux machine.</span></span>

<span data-ttu-id="e557c-221">Ardından aşağıdaki terminale yürütün:</span><span class="sxs-lookup"><span data-stu-id="e557c-221">Then execute the following in the terminal:</span></span>

```bash
chmod a+x powershell-6.0.1-x86_64.AppImage
./powershell-6.0.1-x86_64.AppImage
```

<span data-ttu-id="e557c-222">[AppImage][] yüklemeden PowerShell çalıştırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="e557c-222">The [AppImage][] lets you run PowerShell without installing it.</span></span>
<span data-ttu-id="e557c-223">PowerShell ve bağımlılıklarını (.NET Core'nın sistem bağımlılıklar dahil olmak üzere) bağlı bir pakete sunmaktadır taşınabilir bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="e557c-223">It is a portable application that bundles PowerShell and its dependencies (including .NET Core's system dependencies) into one cohesive package.</span></span>
<span data-ttu-id="e557c-224">Kullanıcının Linux dağıtım bağımsız olarak çalışır, tek bir ikili paketidir.</span><span class="sxs-lookup"><span data-stu-id="e557c-224">This package  is a single binary that works independently of the user's Linux distribution.</span></span>

[appimage]: http://appimage.org/

## <a name="kali"></a><span data-ttu-id="e557c-226">Kali</span><span class="sxs-lookup"><span data-stu-id="e557c-226">Kali</span></span>

### <a name="installation"></a><span data-ttu-id="e557c-227">Yükleme</span><span class="sxs-lookup"><span data-stu-id="e557c-227">Installation</span></span>

```sh
# Download & Install prerequisites
sudo apt-get install libunwind8 libicu55
wget http://security.debian.org/debian-security/pool/updates/main/o/openssl/libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb
sudo dpkg -i libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb

# Install PowerShell
sudo dpkg -i powershell_6.0.2-1.ubuntu.16.04_amd64.deb

# Start PowerShell
pwsh
```

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a><span data-ttu-id="e557c-228">PowerShell yüklemeden son Kali içinde (GNU/Linux Kali çalışırken) çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e557c-228">Run PowerShell in latest Kali (Kali GNU/Linux Rolling) without installing it</span></span>

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.2-x86_64.AppImage

# Start PowerShell
./powershell-6.0.2-x86_64.AppImage
```

### <a name="uninstallation---kali"></a><span data-ttu-id="e557c-229">Kaldırma - Kali</span><span class="sxs-lookup"><span data-stu-id="e557c-229">Uninstallation - Kali</span></span>

```sh
sudo dpkg -r powershell_6.0.2-1.ubuntu.16.04_amd64.deb
```

## <a name="raspbian"></a><span data-ttu-id="e557c-230">Raspbian</span><span class="sxs-lookup"><span data-stu-id="e557c-230">Raspbian</span></span>

<span data-ttu-id="e557c-231">Şu anda, PowerShell yalnızca Raspbian Esnetme üzerinde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="e557c-231">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="e557c-232">Ayrıca CoreCLR (ve bu nedenle PowerShell çekirdeği) yalnızca Pi 2 ve 3 PI cihazlarda diğer cihazlar olarak gibi çalışır [Pi sıfır](https://github.com/dotnet/coreclr/issues/10605), desteklenmeyen bir işlemciye sahip.</span><span class="sxs-lookup"><span data-stu-id="e557c-232">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="e557c-233">Karşıdan [Raspbian Esnetme](https://www.raspberrypi.org/downloads/raspbian/) ve izleyin [yükleme yönergeleri](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) , Pi almak için.</span><span class="sxs-lookup"><span data-stu-id="e557c-233">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation"></a><span data-ttu-id="e557c-234">Yükleme</span><span class="sxs-lookup"><span data-stu-id="e557c-234">Installation</span></span>

```sh
# Install prerequisites
sudo apt-get install libunwind8

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.0.2-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

<span data-ttu-id="e557c-235">İsteğe bağlı olarak, PowerShell "pwsh" ikili yoluna belirtmeden başlatabilmek için sembolik bağlantı oluşturabilirsiniz</span><span class="sxs-lookup"><span data-stu-id="e557c-235">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="e557c-236">Kaldırma - Raspbian</span><span class="sxs-lookup"><span data-stu-id="e557c-236">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="e557c-237">İkili arşivler</span><span class="sxs-lookup"><span data-stu-id="e557c-237">Binary Archives</span></span>

<span data-ttu-id="e557c-238">PowerShell ikili `tar.gz` arşivler gelişmiş dağıtım senaryoları etkinleştirmek Linux platformlar için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="e557c-238">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="e557c-239">Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="e557c-239">Dependencies</span></span>

<span data-ttu-id="e557c-240">PowerShell tüm Linux dağıtımları için taşınabilir ikili dosyalarını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e557c-240">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="e557c-241">Ancak farklı dağıtımların farklı bağımlılıkları .NET çekirdeği çalışma zamanı gerektirir ve bu nedenle PowerShell aynı değil.</span><span class="sxs-lookup"><span data-stu-id="e557c-241">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="e557c-242">Aşağıdaki grafikte farklı Linux dağıtımları üzerinde resmi olarak desteklenen .NET Core 2.0 bağımlılıkları gösterir.</span><span class="sxs-lookup"><span data-stu-id="e557c-242">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="e557c-243">İşletim sistemi</span><span class="sxs-lookup"><span data-stu-id="e557c-243">OS</span></span>                 | <span data-ttu-id="e557c-244">Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="e557c-244">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="e557c-245">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="e557c-245">Ubuntu 14.04</span></span>       | <span data-ttu-id="e557c-246">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="e557c-246">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e557c-247">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="e557c-247">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="e557c-248">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="e557c-248">Ubuntu 16.04</span></span>       | <span data-ttu-id="e557c-249">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="e557c-249">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e557c-250">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="e557c-250">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="e557c-251">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="e557c-251">Ubuntu 17.10</span></span>       | <span data-ttu-id="e557c-252">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="e557c-252">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e557c-253">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="e557c-253">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="e557c-254">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="e557c-254">Ubuntu 18.04</span></span>       | <span data-ttu-id="e557c-255">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="e557c-255">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e557c-256">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="e557c-256">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="e557c-257">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="e557c-257">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="e557c-258">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="e557c-258">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e557c-259">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="e557c-259">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="e557c-260">Debian 9 (Esnetme)</span><span class="sxs-lookup"><span data-stu-id="e557c-260">Debian 9 (Stretch)</span></span> | <span data-ttu-id="e557c-261">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="e557c-261">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e557c-262">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="e557c-262">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="e557c-263">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="e557c-263">CentOS 7</span></span> <br> <span data-ttu-id="e557c-264">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="e557c-264">Oracle Linux 7</span></span> <br> <span data-ttu-id="e557c-265">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="e557c-265">RHEL 7</span></span> <br> <span data-ttu-id="e557c-266">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="e557c-266">OpenSUSE 42.2</span></span> | <span data-ttu-id="e557c-267">libunwind, libcurl, openssl kitaplıklar, libicu</span><span class="sxs-lookup"><span data-stu-id="e557c-267">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="e557c-268">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="e557c-268">Fedora 27</span></span> <br> <span data-ttu-id="e557c-269">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="e557c-269">Fedora 28</span></span> | <span data-ttu-id="e557c-270">libunwind, libcurl, openssl kitaplıklar, libicu, compat openssl10</span><span class="sxs-lookup"><span data-stu-id="e557c-270">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="e557c-271">Resmi olarak desteklenmez Linux dağıtımları PowerShell ikili dosyaları dağıtmak için hedef işletim sistemi için gerekli bağımlılıkları ayrı adımlarda yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e557c-271">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="e557c-272">Örneğin, bizim [Amazon Linux dockerfile] [ amazon-dockerfile] bağımlılıkları ilk yükler ve Linux ayıklar `tar.gz` arşiv.</span><span class="sxs-lookup"><span data-stu-id="e557c-272">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="e557c-273">Yükleme - ikili arşivler</span><span class="sxs-lookup"><span data-stu-id="e557c-273">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="e557c-274">Linux</span><span class="sxs-lookup"><span data-stu-id="e557c-274">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="e557c-275">Kaldırma ikili arşivler</span><span class="sxs-lookup"><span data-stu-id="e557c-275">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="e557c-276">Yollar</span><span class="sxs-lookup"><span data-stu-id="e557c-276">Paths</span></span>

* <span data-ttu-id="e557c-277">`$PSHOME` değil `/opt/microsoft/powershell/6.0.2/`</span><span class="sxs-lookup"><span data-stu-id="e557c-277">`$PSHOME` is `/opt/microsoft/powershell/6.0.2/`</span></span>
* <span data-ttu-id="e557c-278">Kullanıcı profillerini okuma `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="e557c-278">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="e557c-279">Varsayılan profiller okuma `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="e557c-279">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="e557c-280">Kullanıcı modülleri okuma `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="e557c-280">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="e557c-281">Paylaşılan modülleri okuma `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="e557c-281">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="e557c-282">Varsayılan modülleri okuma `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="e557c-282">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="e557c-283">PSReadline geçmişi için kaydedilen `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="e557c-283">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="e557c-284">Varsayılan ana bilgisayar özel profiller var böylece profilleri PowerShell'in başına ana bilgisayar yapılandırması saygı `Microsoft.PowerShell_profile.ps1` aynı konumlarda.</span><span class="sxs-lookup"><span data-stu-id="e557c-284">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="e557c-285">PowerShell uyar [XDG temel dizin belirtimi] [ xdg-bds] Linux üzerinde.</span><span class="sxs-lookup"><span data-stu-id="e557c-285">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[serbest]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
