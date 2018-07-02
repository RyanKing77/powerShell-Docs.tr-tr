# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="e8509-101">Linux’ta PowerShell Core yükleme</span><span class="sxs-lookup"><span data-stu-id="e8509-101">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="e8509-102">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.10][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="e8509-102">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.10][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="e8509-103">Resmi olarak desteklenmez Linux dağıtımları için kullanmayı deneyebilirsiniz [PowerShell AppImage][lai].</span><span class="sxs-lookup"><span data-stu-id="e8509-103">For Linux distributions that are not officially supported, you can try using the [PowerShell AppImage][lai].</span></span>
<span data-ttu-id="e8509-104">Ayrıca Linux kullanarak doğrudan PowerShell ikili dosyaları dağıtma deneyebilirsiniz [ `tar.gz` arşiv][tar], ancak işletim sisteminde ayrı adımlar göre gerekli bağımlılıkları ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e8509-104">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="e8509-105">Tüm paketler bizim Github'da bulunan [serbest][] sayfası.</span><span class="sxs-lookup"><span data-stu-id="e8509-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="e8509-106">Paket yüklendikten sonra çalıştırmak `pwsh` bir terminal gelen.</span><span class="sxs-lookup"><span data-stu-id="e8509-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

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

## <a name="installing-preview-releases"></a><span data-ttu-id="e8509-107">Önizleme sürümleri yükleme</span><span class="sxs-lookup"><span data-stu-id="e8509-107">Installing Preview Releases</span></span>

<span data-ttu-id="e8509-108">PowerShell çekirdek Önizleme sürümü için bir paket deposu aracılığıyla Linux yüklerken, paket adı değişiklikleri `powershell` için `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="e8509-108">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="e8509-109">Doğrudan indirme yükleme, dosya adı dışında değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="e8509-109">Installing via direct download does not change, other than the file name.</span></span>

<span data-ttu-id="e8509-110">Çeşitli paket yöneticileri kullanarak kararlı ve önizleme paketleri yüklemek için komutları tablosu aşağıdadır:</span><span class="sxs-lookup"><span data-stu-id="e8509-110">Here is a table of the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="e8509-111">Distrobution(s)</span><span class="sxs-lookup"><span data-stu-id="e8509-111">Distrobution(s)</span></span>|<span data-ttu-id="e8509-112">Kararlı komutu</span><span class="sxs-lookup"><span data-stu-id="e8509-112">Stable Command</span></span> | <span data-ttu-id="e8509-113">Önizleme komutu</span><span class="sxs-lookup"><span data-stu-id="e8509-113">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="e8509-114">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="e8509-114">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="e8509-115">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="e8509-115">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="e8509-116">openSUSE</span><span class="sxs-lookup"><span data-stu-id="e8509-116">OpenSUSE</span></span> |`sudo zypper install powershell` | `sudo zypper install powershell-preview`|
| <span data-ttu-id="e8509-117">Fedora</span><span class="sxs-lookup"><span data-stu-id="e8509-117">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a><span data-ttu-id="e8509-118">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="e8509-118">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="e8509-119">Paket Deposu - Ubuntu 14.04 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="e8509-119">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="e8509-120">Linux için PowerShell çekirdek paket depoları kolay yükleme (ve güncelleştirmeleri) için yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="e8509-120">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="e8509-121">Bu tercih edilen yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="e8509-121">This is the preferred method.</span></span>

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

<span data-ttu-id="e8509-122">Süper kullanıcı Microsoft depoya kaydedin.</span><span class="sxs-lookup"><span data-stu-id="e8509-122">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="e8509-123">Daha sonra kullanmak yeterlidir `sudo apt-get upgrade powershell` yüklemeyi güncelleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="e8509-123">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="e8509-124">Doğrudan indirme - Ubuntu 14.04 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="e8509-124">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="e8509-125">Debian paketi Yükle `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` gelen [serbest][] Ubuntu makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="e8509-125">Download the Debian package `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="e8509-126">Ardından aşağıdaki terminale yürütün:</span><span class="sxs-lookup"><span data-stu-id="e8509-126">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="e8509-127">`dpkg -i` Komut unmet bağımlılıkları ile başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="e8509-127">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="e8509-128">Sonraki komutu `apt-get install -f` PowerShell paketi Yapılandırma tamamlandıktan sonra bu sorunları giderir.</span><span class="sxs-lookup"><span data-stu-id="e8509-128">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="e8509-129">Kaldırma - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="e8509-129">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="e8509-130">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="e8509-130">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="e8509-131">Paket Deposu - Ubuntu 16.04 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="e8509-131">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="e8509-132">Linux için PowerShell çekirdek paket depoları kolay yükleme (ve güncelleştirmeleri) için yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="e8509-132">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="e8509-133">Bu tercih edilen yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="e8509-133">This is the preferred method.</span></span>

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

<span data-ttu-id="e8509-134">Microsoft depo süper kullanıcı bir kez kaydolduktan sonra daha sonra kullanmak yeterlidir `sudo apt-get upgrade powershell` güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="e8509-134">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="e8509-135">Doğrudan indirme - Ubuntu 16.04 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="e8509-135">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="e8509-136">Debian paketi Yükle `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` gelen [serbest][] Ubuntu makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="e8509-136">Download the Debian package `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="e8509-137">Ardından aşağıdaki terminale yürütün:</span><span class="sxs-lookup"><span data-stu-id="e8509-137">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="e8509-138">`dpkg -i` Komut unmet bağımlılıkları ile başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="e8509-138">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="e8509-139">Sonraki komutu `apt-get install -f` PowerShell paketi Yapılandırma tamamlandıktan sonra bu sorunları giderir.</span><span class="sxs-lookup"><span data-stu-id="e8509-139">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="e8509-140">Kaldırma - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="e8509-140">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1710"></a><span data-ttu-id="e8509-141">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="e8509-141">Ubuntu 17.10</span></span>

> [!NOTE]
> <span data-ttu-id="e8509-142">Sonra Ubuntu 17.04 desteği eklendi `6.1.0-preview.2`</span><span class="sxs-lookup"><span data-stu-id="e8509-142">Support for Ubuntu 17.04 was added after `6.1.0-preview.2`</span></span>

### <a name="installation-via-package-repository---ubuntu-1710"></a><span data-ttu-id="e8509-143">Paket Deposu - Ubuntu 17.10 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="e8509-143">Installation via Package Repository - Ubuntu 17.10</span></span>

<span data-ttu-id="e8509-144">Linux için PowerShell çekirdek paket depoları kolay yükleme (ve güncelleştirmeleri) için yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="e8509-144">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="e8509-145">Bu tercih edilen yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="e8509-145">This is the preferred method.</span></span>

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

<span data-ttu-id="e8509-146">Microsoft depo süper kullanıcı bir kez kaydolduktan sonra daha sonra kullanmak yeterlidir `sudo apt-get upgrade powershell` güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="e8509-146">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1710"></a><span data-ttu-id="e8509-147">Doğrudan indirme - Ubuntu 17.10 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="e8509-147">Installation via Direct Download - Ubuntu 17.10</span></span>

<span data-ttu-id="e8509-148">Debian paketi Yükle `powershell_6.0.2-1.ubuntu.17.10_amd64.deb` gelen [serbest][] Ubuntu makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="e8509-148">Download the Debian package `powershell_6.0.2-1.ubuntu.17.10_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="e8509-149">Ardından aşağıdaki terminale yürütün:</span><span class="sxs-lookup"><span data-stu-id="e8509-149">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.17.10_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="e8509-150">`dpkg -i` Komut unmet bağımlılıkları ile başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="e8509-150">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="e8509-151">Sonraki komutu `apt-get install -f` PowerShell paketi Yapılandırma tamamlandıktan sonra bu sorunları giderir.</span><span class="sxs-lookup"><span data-stu-id="e8509-151">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1710"></a><span data-ttu-id="e8509-152">Kaldırma - Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="e8509-152">Uninstallation - Ubuntu 17.10</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="e8509-153">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="e8509-153">Ubuntu 18.04</span></span>

> [!NOTE]
> <span data-ttu-id="e8509-154">Sonra Ubuntu 18.04 desteği eklendi `6.1.0-preview.2`</span><span class="sxs-lookup"><span data-stu-id="e8509-154">Support for Ubuntu 18.04 was added after `6.1.0-preview.2`</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="e8509-155">Paket Deposu - Ubuntu 18.04 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="e8509-155">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="e8509-156">Linux için PowerShell çekirdek paket depoları kolay yükleme (ve güncelleştirmeleri) için yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="e8509-156">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="e8509-157">Bu tercih edilen yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="e8509-157">This is the preferred method.</span></span>

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

<span data-ttu-id="e8509-158">Microsoft depo süper kullanıcı bir kez kaydolduktan sonra daha sonra kullanmak yeterlidir `sudo apt-get upgrade powershell` güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="e8509-158">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="e8509-159">Doğrudan indirme - Ubuntu 18.04 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="e8509-159">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="e8509-160">Debian paketi Yükle `powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb` gelen [serbest][] Ubuntu makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="e8509-160">Download the Debian package `powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="e8509-161">Ardından aşağıdaki terminale yürütün:</span><span class="sxs-lookup"><span data-stu-id="e8509-161">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="e8509-162">`dpkg -i` Komut unmet bağımlılıkları ile başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="e8509-162">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="e8509-163">Sonraki komutu `apt-get install -f` PowerShell paketi Yapılandırma tamamlandıktan sonra bu sorunları giderir.</span><span class="sxs-lookup"><span data-stu-id="e8509-163">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1710"></a><span data-ttu-id="e8509-164">Kaldırma - Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="e8509-164">Uninstallation - Ubuntu 17.10</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-8"></a><span data-ttu-id="e8509-165">Debian 8</span><span class="sxs-lookup"><span data-stu-id="e8509-165">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="e8509-166">Paket Deposu - Debian 8 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="e8509-166">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="e8509-167">Linux için PowerShell çekirdek paket depoları kolay yükleme (ve güncelleştirmeleri) için yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="e8509-167">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="e8509-168">Bu tercih edilen yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="e8509-168">This is the preferred method.</span></span>

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

<span data-ttu-id="e8509-169">Microsoft depo süper kullanıcı bir kez kaydolduktan sonra daha sonra kullanmak yeterlidir `sudo apt-get upgrade powershell` güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="e8509-169">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="e8509-170">Aracılığıyla doğrudan indirme - Debian 8 yükleme</span><span class="sxs-lookup"><span data-stu-id="e8509-170">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="e8509-171">Debian paketi Yükle `powershell_6.0.2-1.debian.8_amd64.deb` gelen [serbest][] Debian makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="e8509-171">Download the Debian package `powershell_6.0.2-1.debian.8_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="e8509-172">Ardından aşağıdaki terminale yürütün:</span><span class="sxs-lookup"><span data-stu-id="e8509-172">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="e8509-173">`dpkg -i` Komut unmet bağımlılıkları ile başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="e8509-173">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="e8509-174">Sonraki komutu `apt-get install -f` PowerShell paketi Yapılandırma tamamlandıktan sonra bu sorunları giderir.</span><span class="sxs-lookup"><span data-stu-id="e8509-174">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="e8509-175">Kaldırma - Debian 8</span><span class="sxs-lookup"><span data-stu-id="e8509-175">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="e8509-176">Debian 9</span><span class="sxs-lookup"><span data-stu-id="e8509-176">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="e8509-177">Paket Deposu - Debian 9 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="e8509-177">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="e8509-178">Linux için PowerShell çekirdek paket depoları kolay yükleme (ve güncelleştirmeleri) için yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="e8509-178">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="e8509-179">Bu tercih edilen yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="e8509-179">This is the preferred method.</span></span>

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

<span data-ttu-id="e8509-180">Microsoft depo süper kullanıcı bir kez kaydolduktan sonra daha sonra kullanmak yeterlidir `sudo apt-get upgrade powershell` güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="e8509-180">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="e8509-181">Doğrudan indirme - Debian 9 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="e8509-181">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="e8509-182">Debian paketi Yükle `powershell_6.0.2-1.debian.9_amd64.deb` gelen [serbest][] Debian makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="e8509-182">Download the Debian package `powershell_6.0.2-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="e8509-183">Ardından aşağıdaki terminale yürütün:</span><span class="sxs-lookup"><span data-stu-id="e8509-183">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="e8509-184">Kaldırma - Debian 9</span><span class="sxs-lookup"><span data-stu-id="e8509-184">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="e8509-185">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="e8509-185">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="e8509-186">Bu paket, Oracle Linux 7'de de çalışır.</span><span class="sxs-lookup"><span data-stu-id="e8509-186">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="e8509-187">Paket (önerilen) - deposu CentOS 7 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="e8509-187">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="e8509-188">Linux için PowerShell çekirdek kolay yükleme (ve güncelleştirmeleri) için resmi Microsoft depoları yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="e8509-188">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="e8509-189">Microsoft depo süper kullanıcı bir kez kaydolduktan sonra kullanmak yeterlidir `sudo yum update powershell` PowerShell güncelleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="e8509-189">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="e8509-190">Doğrudan indirme - CentOS 7 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="e8509-190">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="e8509-191">Kullanarak [CentOS 7][], RPM paketi Yükle `powershell-6.0.2-1.rhel.7.x86_64.rpm` gelen [serbest][] CentOS makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="e8509-191">Using [CentOS 7][], download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="e8509-192">Ardından aşağıdaki terminale yürütün:</span><span class="sxs-lookup"><span data-stu-id="e8509-192">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="e8509-193">Ayrıca, indirilmesi ara adım olmadan RPM yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e8509-193">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="e8509-194">Kaldırma - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="e8509-194">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="e8509-196">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="e8509-196">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="e8509-197">Paket (önerilen) - deposu Red Hat Enterprise Linux (RHEL) 7 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="e8509-197">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="e8509-198">Linux için PowerShell çekirdek kolay yükleme (ve güncelleştirmeleri) için resmi Microsoft depoları yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="e8509-198">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="e8509-199">Microsoft depo süper kullanıcı bir kez kaydolduktan sonra kullanmak yeterlidir `sudo yum update powershell` PowerShell güncelleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="e8509-199">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="e8509-200">Doğrudan indirme - Red Hat Enterprise Linux (RHEL) 7 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="e8509-200">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="e8509-201">RPM paketi Yükle `powershell-6.0.2-1.rhel.7.x86_64.rpm` gelen [serbest][] Red Hat Enterprise Linux makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="e8509-201">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="e8509-202">Ardından aşağıdaki terminale yürütün:</span><span class="sxs-lookup"><span data-stu-id="e8509-202">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="e8509-203">Ayrıca, indirilmesi ara adım olmadan RPM yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e8509-203">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="e8509-204">Kaldırma - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="e8509-204">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse-422"></a><span data-ttu-id="e8509-205">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="e8509-205">OpenSUSE 42.2</span></span>

<span data-ttu-id="e8509-206">PowerShell çekirdek yüklerken `zypper` şu hata rapor edebilir:</span><span class="sxs-lookup"><span data-stu-id="e8509-206">When installing PowerShell Core, `zypper` may report the following error:</span></span>

```Output
Problem: nothing provides libcurl needed by powershell-6.0.1-1.rhel.7.x86_64
 Solution 1: do not install powershell-6.0.1-1.rhel.7.x86_64
 Solution 2: break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies
```

<span data-ttu-id="e8509-207">Bu durumda, doğrulayın uyumlu bir `libcurl` kitaplığı varsa aşağıdaki gösterir komutu denetleyerek `libcurl4` paketini yüklü olarak:</span><span class="sxs-lookup"><span data-stu-id="e8509-207">In this case, verify that a compatible `libcurl` library is present by checking that the following command shows the `libcurl4` package as installed:</span></span>

```sh
zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
```

<span data-ttu-id="e8509-208">Ardından `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` PowerShell paket yüklerken çözümü.</span><span class="sxs-lookup"><span data-stu-id="e8509-208">Then choose the `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` solution when installing the PowerShell package.</span></span>

### <a name="installation-via-package-repository-preferred---opensuse-422"></a><span data-ttu-id="e8509-209">Paket (önerilen) - deposu OpenSUSE 42.2 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="e8509-209">Installation via Package Repository (preferred) - OpenSUSE 42.2</span></span>

<span data-ttu-id="e8509-210">Linux için PowerShell çekirdek kolay yükleme (ve güncelleştirmeleri) için resmi Microsoft depoları yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="e8509-210">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---opensuse-422"></a><span data-ttu-id="e8509-211">Doğrudan indirme - OpenSUSE 42.2 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="e8509-211">Installation via Direct Download - OpenSUSE 42.2</span></span>

<span data-ttu-id="e8509-212">RPM paketi Yükle `powershell-6.0.2-1.rhel.7.x86_64.rpm` gelen [serbest][] OpenSUSE makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="e8509-212">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the OpenSUSE machine.</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="e8509-213">Ayrıca, indirilmesi ara adım olmadan RPM yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e8509-213">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-422"></a><span data-ttu-id="e8509-214">Kaldırma - OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="e8509-214">Uninstallation - OpenSUSE 42.2</span></span>

```sh
sudo zypper remove powershell
```

## <a name="fedora"></a><span data-ttu-id="e8509-215">Fedora</span><span class="sxs-lookup"><span data-stu-id="e8509-215">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="e8509-216">Fedora 28 yalnızca PowerShell çekirdek 6.1 ve sonraki sürümleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="e8509-216">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="e8509-217">Paket (önerilen) - deposu Fedora 27 Fedora 28 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="e8509-217">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="e8509-218">Linux için PowerShell çekirdek kolay yükleme (ve güncelleştirmeleri) için resmi Microsoft depoları yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="e8509-218">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="e8509-219">Doğrudan indirme - Fedora 27, Fedora 28 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="e8509-219">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="e8509-220">RPM paketi Yükle `powershell-6.0.2-1.rhel.7.x86_64.rpm` gelen [serbest][] Fedora makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="e8509-220">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="e8509-221">Ardından aşağıdaki terminale yürütün:</span><span class="sxs-lookup"><span data-stu-id="e8509-221">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="e8509-222">Ayrıca, indirilmesi ara adım olmadan RPM yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e8509-222">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="e8509-223">Kaldırma - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="e8509-223">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="e8509-224">Linux arch</span><span class="sxs-lookup"><span data-stu-id="e8509-224">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="e8509-225">Yay Deneysel desteğidir.</span><span class="sxs-lookup"><span data-stu-id="e8509-225">Arch support is experimental.</span></span>

<span data-ttu-id="e8509-226">PowerShell edinilebilir [Arch Linux][] kullanıcı deposu (AUR).</span><span class="sxs-lookup"><span data-stu-id="e8509-226">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="e8509-227">İle derlenebilir [en son sürüm etiketli][arch-release]</span><span class="sxs-lookup"><span data-stu-id="e8509-227">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="e8509-228">Nden derlenebilir [ana son yürütme][arch-git]</span><span class="sxs-lookup"><span data-stu-id="e8509-228">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="e8509-229">Kullanılarak yüklenebilir [ikili en son sürüm][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="e8509-229">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="e8509-230">AUR paketlerinde saklanır topluluk - resmi desteği yoktur.</span><span class="sxs-lookup"><span data-stu-id="e8509-230">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="e8509-231">AUR paketleri yükleme hakkında daha fazla bilgi için bkz: [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) veya topluluk [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="e8509-231">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="linux-appimage"></a><span data-ttu-id="e8509-233">Linux AppImage</span><span class="sxs-lookup"><span data-stu-id="e8509-233">Linux AppImage</span></span>

> [!NOTE]
> <span data-ttu-id="e8509-234">Deneysel AppImage desteği</span><span class="sxs-lookup"><span data-stu-id="e8509-234">AppImage support is experimental</span></span>

<span data-ttu-id="e8509-235">Son Linux dağıtım kullanarak karşıdan AppImage `powershell-6.0.1-x86_64.AppImage` gelen [serbest][] Linux makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="e8509-235">Using a recent Linux distribution, download the AppImage `powershell-6.0.1-x86_64.AppImage` from the [releases][] page onto the Linux machine.</span></span>

<span data-ttu-id="e8509-236">Ardından aşağıdaki terminale yürütün:</span><span class="sxs-lookup"><span data-stu-id="e8509-236">Then execute the following in the terminal:</span></span>

```bash
chmod a+x powershell-6.0.1-x86_64.AppImage
./powershell-6.0.1-x86_64.AppImage
```

<span data-ttu-id="e8509-237">[AppImage][] yüklemeden PowerShell çalıştırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="e8509-237">The [AppImage][] lets you run PowerShell without installing it.</span></span>
<span data-ttu-id="e8509-238">PowerShell ve bağımlılıklarını (.NET Core'nın sistem bağımlılıklar dahil olmak üzere) bağlı bir pakete sunmaktadır taşınabilir bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="e8509-238">It is a portable application that bundles PowerShell and its dependencies (including .NET Core's system dependencies) into one cohesive package.</span></span>
<span data-ttu-id="e8509-239">Kullanıcının Linux dağıtım bağımsız olarak çalışır, tek bir ikili paketidir.</span><span class="sxs-lookup"><span data-stu-id="e8509-239">This package  is a single binary that works independently of the user's Linux distribution.</span></span>

[appimage]: http://appimage.org/

## <a name="kali"></a><span data-ttu-id="e8509-241">Kali</span><span class="sxs-lookup"><span data-stu-id="e8509-241">Kali</span></span>

> [!NOTE]
> <span data-ttu-id="e8509-242">Kali desteği Deneysel değil.</span><span class="sxs-lookup"><span data-stu-id="e8509-242">Kali support is experimental.</span></span>

### <a name="installation"></a><span data-ttu-id="e8509-243">Yükleme</span><span class="sxs-lookup"><span data-stu-id="e8509-243">Installation</span></span>

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

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a><span data-ttu-id="e8509-244">PowerShell yüklemeden son Kali içinde (GNU/Linux Kali çalışırken) çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e8509-244">Run PowerShell in latest Kali (Kali GNU/Linux Rolling) without installing it</span></span>

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.2-x86_64.AppImage

# Start PowerShell
./powershell-6.0.2-x86_64.AppImage
```

### <a name="uninstallation---kali"></a><span data-ttu-id="e8509-245">Kaldırma - Kali</span><span class="sxs-lookup"><span data-stu-id="e8509-245">Uninstallation - Kali</span></span>

```sh
sudo dpkg -r powershell_6.0.2-1.ubuntu.16.04_amd64.deb
```

## <a name="raspbian"></a><span data-ttu-id="e8509-246">Raspbian</span><span class="sxs-lookup"><span data-stu-id="e8509-246">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="e8509-247">Raspbian desteği Deneysel değil.</span><span class="sxs-lookup"><span data-stu-id="e8509-247">Raspbian support is experimental.</span></span>

<span data-ttu-id="e8509-248">Şu anda, PowerShell yalnızca Raspbian Esnetme üzerinde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="e8509-248">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="e8509-249">Ayrıca CoreCLR (ve bu nedenle PowerShell çekirdeği) yalnızca Pi 2 ve 3 PI cihazlarda diğer cihazlar olarak gibi çalışır [Pi sıfır](https://github.com/dotnet/coreclr/issues/10605), desteklenmeyen bir işlemciye sahip.</span><span class="sxs-lookup"><span data-stu-id="e8509-249">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="e8509-250">Karşıdan [Raspbian Esnetme](https://www.raspberrypi.org/downloads/raspbian/) ve izleyin [yükleme yönergeleri](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) , Pi almak için.</span><span class="sxs-lookup"><span data-stu-id="e8509-250">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation"></a><span data-ttu-id="e8509-251">Yükleme</span><span class="sxs-lookup"><span data-stu-id="e8509-251">Installation</span></span>

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

<span data-ttu-id="e8509-252">İsteğe bağlı olarak, PowerShell "pwsh" ikili yoluna belirtmeden başlatabilmek için sembolik bağlantı oluşturabilirsiniz</span><span class="sxs-lookup"><span data-stu-id="e8509-252">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="e8509-253">Kaldırma - Raspbian</span><span class="sxs-lookup"><span data-stu-id="e8509-253">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="e8509-254">İkili arşivler</span><span class="sxs-lookup"><span data-stu-id="e8509-254">Binary Archives</span></span>

<span data-ttu-id="e8509-255">PowerShell ikili `tar.gz` arşivler gelişmiş dağıtım senaryoları etkinleştirmek Linux platformlar için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="e8509-255">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="e8509-256">Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="e8509-256">Dependencies</span></span>

<span data-ttu-id="e8509-257">PowerShell tüm Linux dağıtımları için taşınabilir ikili dosyalarını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e8509-257">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="e8509-258">Ancak farklı dağıtımların farklı bağımlılıkları .NET çekirdeği çalışma zamanı gerektirir ve bu nedenle PowerShell aynı değil.</span><span class="sxs-lookup"><span data-stu-id="e8509-258">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="e8509-259">Aşağıdaki grafikte farklı Linux dağıtımları üzerinde resmi olarak desteklenen .NET Core 2.0 bağımlılıkları gösterir.</span><span class="sxs-lookup"><span data-stu-id="e8509-259">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="e8509-260">İşletim sistemi</span><span class="sxs-lookup"><span data-stu-id="e8509-260">OS</span></span>                 | <span data-ttu-id="e8509-261">Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="e8509-261">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="e8509-262">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="e8509-262">Ubuntu 14.04</span></span>       | <span data-ttu-id="e8509-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="e8509-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e8509-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="e8509-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="e8509-265">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="e8509-265">Ubuntu 16.04</span></span>       | <span data-ttu-id="e8509-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="e8509-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e8509-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="e8509-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="e8509-268">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="e8509-268">Ubuntu 17.10</span></span>       | <span data-ttu-id="e8509-269">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="e8509-269">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e8509-270">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="e8509-270">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="e8509-271">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="e8509-271">Ubuntu 18.04</span></span>       | <span data-ttu-id="e8509-272">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="e8509-272">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e8509-273">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="e8509-273">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="e8509-274">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="e8509-274">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="e8509-275">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="e8509-275">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e8509-276">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="e8509-276">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="e8509-277">Debian 9 (Esnetme)</span><span class="sxs-lookup"><span data-stu-id="e8509-277">Debian 9 (Stretch)</span></span> | <span data-ttu-id="e8509-278">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="e8509-278">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e8509-279">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="e8509-279">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="e8509-280">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="e8509-280">CentOS 7</span></span> <br> <span data-ttu-id="e8509-281">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="e8509-281">Oracle Linux 7</span></span> <br> <span data-ttu-id="e8509-282">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="e8509-282">RHEL 7</span></span> <br> <span data-ttu-id="e8509-283">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="e8509-283">OpenSUSE 42.2</span></span> | <span data-ttu-id="e8509-284">libunwind, libcurl, openssl kitaplıklar, libicu</span><span class="sxs-lookup"><span data-stu-id="e8509-284">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="e8509-285">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="e8509-285">Fedora 27</span></span> <br> <span data-ttu-id="e8509-286">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="e8509-286">Fedora 28</span></span> | <span data-ttu-id="e8509-287">libunwind, libcurl, openssl kitaplıklar, libicu, compat openssl10</span><span class="sxs-lookup"><span data-stu-id="e8509-287">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="e8509-288">Resmi olarak desteklenmez Linux dağıtımları PowerShell ikili dosyaları dağıtmak için hedef işletim sistemi için gerekli bağımlılıkları ayrı adımlarda yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e8509-288">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="e8509-289">Örneğin, bizim [Amazon Linux dockerfile] [ amazon-dockerfile] bağımlılıkları ilk yükler ve Linux ayıklar `tar.gz` arşiv.</span><span class="sxs-lookup"><span data-stu-id="e8509-289">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="e8509-290">Yükleme - ikili arşivler</span><span class="sxs-lookup"><span data-stu-id="e8509-290">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="e8509-291">Linux</span><span class="sxs-lookup"><span data-stu-id="e8509-291">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="e8509-292">Kaldırma ikili arşivler</span><span class="sxs-lookup"><span data-stu-id="e8509-292">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="e8509-293">Yollar</span><span class="sxs-lookup"><span data-stu-id="e8509-293">Paths</span></span>

* <span data-ttu-id="e8509-294">`$PSHOME` değil `/opt/microsoft/powershell/6.0.2/`</span><span class="sxs-lookup"><span data-stu-id="e8509-294">`$PSHOME` is `/opt/microsoft/powershell/6.0.2/`</span></span>
* <span data-ttu-id="e8509-295">Kullanıcı profillerini okuma `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="e8509-295">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="e8509-296">Varsayılan profiller okuma `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="e8509-296">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="e8509-297">Kullanıcı modülleri okuma `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="e8509-297">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="e8509-298">Paylaşılan modülleri okuma `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="e8509-298">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="e8509-299">Varsayılan modülleri okuma `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="e8509-299">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="e8509-300">PSReadline geçmişi için kaydedilen `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="e8509-300">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="e8509-301">Varsayılan ana bilgisayar özel profiller var böylece profilleri PowerShell'in başına ana bilgisayar yapılandırması saygı `Microsoft.PowerShell_profile.ps1` aynı konumlarda.</span><span class="sxs-lookup"><span data-stu-id="e8509-301">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="e8509-302">PowerShell uyar [XDG temel dizin belirtimi] [ xdg-bds] Linux üzerinde.</span><span class="sxs-lookup"><span data-stu-id="e8509-302">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[serbest]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
