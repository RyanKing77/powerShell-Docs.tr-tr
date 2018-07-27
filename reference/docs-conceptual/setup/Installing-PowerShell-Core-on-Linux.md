# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="fccc1-101">Linux’ta PowerShell Core yükleme</span><span class="sxs-lookup"><span data-stu-id="fccc1-101">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="fccc1-102">Destekler [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.10] [ u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7] [ cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.3][opensuse], [Fedora 27 ] [ fedora], [Fedora 28][fedora], ve [Arch Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="fccc1-102">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.10][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.3][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="fccc1-103">Değil resmi olarak desteklenen Linux dağıtımları için kullanmayı deneyebilirsiniz [PowerShell AppImage][lai].</span><span class="sxs-lookup"><span data-stu-id="fccc1-103">For Linux distributions that are not officially supported, you can try using the [PowerShell AppImage][lai].</span></span>
<span data-ttu-id="fccc1-104">Linux kullanarak doğrudan PowerShell ikili dosyaları dağıtmaya de deneyebilirsiniz [ `tar.gz` arşiv][tar], ancak gerekli bağımlılıkları işletim sisteminde ayrı adımları göre ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fccc1-104">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="fccc1-105">Tüm paketleri bizim Github'da kullanılabilir [sürümleri][] sayfası.</span><span class="sxs-lookup"><span data-stu-id="fccc1-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="fccc1-106">Paket yüklendikten sonra Çalıştır `pwsh` bir terminalden.</span><span class="sxs-lookup"><span data-stu-id="fccc1-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u17]: #ubuntu-1710
[u18]: #ubuntu-1804
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse-423
[fedora]: #fedora
[arch]: #arch-linux
[lai]: #linux-appimage
[tar]: #binary-archives

## <a name="installing-preview-releases"></a><span data-ttu-id="fccc1-107">Önizleme sürümleri yükleme</span><span class="sxs-lookup"><span data-stu-id="fccc1-107">Installing Preview Releases</span></span>

<span data-ttu-id="fccc1-108">PowerShell Core Önizleme sürümü için Paket Deposu aracılığıyla Linux yüklerken, paket adı değişiklikleri `powershell` için `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="fccc1-108">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="fccc1-109">Doğrudan indirme ile yükleme, dosya adı dışında değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="fccc1-109">Installing via direct download does not change, other than the file name.</span></span>

<span data-ttu-id="fccc1-110">Çeşitli paket yöneticilerini kullanarak kararlı ve önizleme paketleri yüklemek için komut tablosu şu şekildedir:</span><span class="sxs-lookup"><span data-stu-id="fccc1-110">Here is a table of the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="fccc1-111">Distribution(s)</span><span class="sxs-lookup"><span data-stu-id="fccc1-111">Distribution(s)</span></span>|<span data-ttu-id="fccc1-112">Kararlı komutu</span><span class="sxs-lookup"><span data-stu-id="fccc1-112">Stable Command</span></span> | <span data-ttu-id="fccc1-113">Önizleme komutu</span><span class="sxs-lookup"><span data-stu-id="fccc1-113">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="fccc1-114">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="fccc1-114">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="fccc1-115">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="fccc1-115">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="fccc1-116">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="fccc1-116">OpenSUSE</span></span> |`sudo zypper install powershell` | `sudo zypper install powershell-preview`|
| <span data-ttu-id="fccc1-117">Fedora</span><span class="sxs-lookup"><span data-stu-id="fccc1-117">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a><span data-ttu-id="fccc1-118">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="fccc1-118">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="fccc1-119">Paket Deposu - Ubuntu 14.04 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="fccc1-119">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="fccc1-120">Linux için PowerShell Core, paket depolarınızın kolay yükleme (ve güncelleştirmeleri) için yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="fccc1-120">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="fccc1-121">Bu tercih edilen yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="fccc1-121">This is the preferred method.</span></span>

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

<span data-ttu-id="fccc1-122">Süper kullanıcı Microsoft depoya kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fccc1-122">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="fccc1-123">Daha sonra kullanmanız yeterlidir `sudo apt-get upgrade powershell` yüklemesini güncelleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="fccc1-123">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="fccc1-124">Doğrudan indirme - Ubuntu 14.04 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="fccc1-124">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="fccc1-125">Debian paketi indirme `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` gelen [sürümleri][] Ubuntu makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="fccc1-125">Download the Debian package `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="fccc1-126">Ardından aşağıdakileri terminalde yürütün:</span><span class="sxs-lookup"><span data-stu-id="fccc1-126">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="fccc1-127">`dpkg -i` Komutu karşılaşılmamış bağımlılıklarıyla birlikte başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="fccc1-127">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="fccc1-128">Sonraki komut `apt-get install -f` PowerShell paketi Yapılandırma tamamlandıktan sonra bu sorunları giderir.</span><span class="sxs-lookup"><span data-stu-id="fccc1-128">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="fccc1-129">Kaldırma - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="fccc1-129">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="fccc1-130">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="fccc1-130">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="fccc1-131">Paket Deposu - Ubuntu 16.04 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="fccc1-131">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="fccc1-132">Linux için PowerShell Core, paket depolarınızın kolay yükleme (ve güncelleştirmeleri) için yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="fccc1-132">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="fccc1-133">Bu tercih edilen yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="fccc1-133">This is the preferred method.</span></span>

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

<span data-ttu-id="fccc1-134">Microsoft depo süper kullanıcı bir kez kaydolduktan sonra daha sonra kullanmanız yeterlidir `sudo apt-get upgrade powershell` güncelleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="fccc1-134">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="fccc1-135">Doğrudan indirme - Ubuntu 16.04 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="fccc1-135">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="fccc1-136">Debian paketi indirme `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` gelen [sürümleri][] Ubuntu makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="fccc1-136">Download the Debian package `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="fccc1-137">Ardından aşağıdakileri terminalde yürütün:</span><span class="sxs-lookup"><span data-stu-id="fccc1-137">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="fccc1-138">`dpkg -i` Komutu karşılaşılmamış bağımlılıklarıyla birlikte başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="fccc1-138">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="fccc1-139">Sonraki komut `apt-get install -f` PowerShell paketi Yapılandırma tamamlandıktan sonra bu sorunları giderir.</span><span class="sxs-lookup"><span data-stu-id="fccc1-139">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="fccc1-140">Kaldırma - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="fccc1-140">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1710"></a><span data-ttu-id="fccc1-141">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="fccc1-141">Ubuntu 17.10</span></span>

> [!NOTE]
> <span data-ttu-id="fccc1-142">Sonra Ubuntu 17.04 desteği eklendi `6.1.0-preview.2`</span><span class="sxs-lookup"><span data-stu-id="fccc1-142">Support for Ubuntu 17.04 was added after `6.1.0-preview.2`</span></span>

### <a name="installation-via-package-repository---ubuntu-1710"></a><span data-ttu-id="fccc1-143">Paket Deposu - Ubuntu 17.10 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="fccc1-143">Installation via Package Repository - Ubuntu 17.10</span></span>

<span data-ttu-id="fccc1-144">Linux için PowerShell Core, paket depolarınızın kolay yükleme (ve güncelleştirmeleri) için yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="fccc1-144">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="fccc1-145">Bu tercih edilen yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="fccc1-145">This is the preferred method.</span></span>

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

<span data-ttu-id="fccc1-146">Microsoft depo süper kullanıcı bir kez kaydolduktan sonra daha sonra kullanmanız yeterlidir `sudo apt-get upgrade powershell` güncelleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="fccc1-146">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1710"></a><span data-ttu-id="fccc1-147">Doğrudan indirme - Ubuntu 17.10 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="fccc1-147">Installation via Direct Download - Ubuntu 17.10</span></span>

<span data-ttu-id="fccc1-148">Debian paketi indirme `powershell_6.0.2-1.ubuntu.17.10_amd64.deb` gelen [sürümleri][] Ubuntu makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="fccc1-148">Download the Debian package `powershell_6.0.2-1.ubuntu.17.10_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="fccc1-149">Ardından aşağıdakileri terminalde yürütün:</span><span class="sxs-lookup"><span data-stu-id="fccc1-149">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.17.10_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="fccc1-150">`dpkg -i` Komutu karşılaşılmamış bağımlılıklarıyla birlikte başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="fccc1-150">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="fccc1-151">Sonraki komut `apt-get install -f` PowerShell paketi Yapılandırma tamamlandıktan sonra bu sorunları giderir.</span><span class="sxs-lookup"><span data-stu-id="fccc1-151">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1710"></a><span data-ttu-id="fccc1-152">Kaldırma - Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="fccc1-152">Uninstallation - Ubuntu 17.10</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="fccc1-153">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="fccc1-153">Ubuntu 18.04</span></span>

> [!NOTE]
> <span data-ttu-id="fccc1-154">Sonra Ubuntu 18.04 desteği eklendi `6.1.0-preview.2`</span><span class="sxs-lookup"><span data-stu-id="fccc1-154">Support for Ubuntu 18.04 was added after `6.1.0-preview.2`</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="fccc1-155">Paket Deposu - Ubuntu 18.04 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="fccc1-155">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="fccc1-156">Linux için PowerShell Core, paket depolarınızın kolay yükleme (ve güncelleştirmeleri) için yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="fccc1-156">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="fccc1-157">Bu tercih edilen yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="fccc1-157">This is the preferred method.</span></span>

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

<span data-ttu-id="fccc1-158">Microsoft depo süper kullanıcı bir kez kaydolduktan sonra daha sonra kullanmanız yeterlidir `sudo apt-get upgrade powershell` güncelleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="fccc1-158">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="fccc1-159">Doğrudan indirme - Ubuntu 18.04 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="fccc1-159">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="fccc1-160">Debian paketi indirme `powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb` gelen [sürümleri][] Ubuntu makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="fccc1-160">Download the Debian package `powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="fccc1-161">Ardından aşağıdakileri terminalde yürütün:</span><span class="sxs-lookup"><span data-stu-id="fccc1-161">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="fccc1-162">`dpkg -i` Komutu karşılaşılmamış bağımlılıklarıyla birlikte başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="fccc1-162">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="fccc1-163">Sonraki komut `apt-get install -f` PowerShell paketi Yapılandırma tamamlandıktan sonra bu sorunları giderir.</span><span class="sxs-lookup"><span data-stu-id="fccc1-163">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="fccc1-164">Kaldırma - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="fccc1-164">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-8"></a><span data-ttu-id="fccc1-165">Debian 8</span><span class="sxs-lookup"><span data-stu-id="fccc1-165">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="fccc1-166">Paket Deposu - Debian 8 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="fccc1-166">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="fccc1-167">Linux için PowerShell Core, paket depolarınızın kolay yükleme (ve güncelleştirmeleri) için yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="fccc1-167">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="fccc1-168">Bu tercih edilen yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="fccc1-168">This is the preferred method.</span></span>

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

<span data-ttu-id="fccc1-169">Microsoft depo süper kullanıcı bir kez kaydolduktan sonra daha sonra kullanmanız yeterlidir `sudo apt-get upgrade powershell` güncelleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="fccc1-169">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="fccc1-170">Doğrudan indirme - Debian 8 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="fccc1-170">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="fccc1-171">Debian paketi indirme `powershell_6.0.2-1.debian.8_amd64.deb` gelen [sürümleri][] Debian makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="fccc1-171">Download the Debian package `powershell_6.0.2-1.debian.8_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="fccc1-172">Ardından aşağıdakileri terminalde yürütün:</span><span class="sxs-lookup"><span data-stu-id="fccc1-172">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="fccc1-173">`dpkg -i` Komutu karşılaşılmamış bağımlılıklarıyla birlikte başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="fccc1-173">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="fccc1-174">Sonraki komut `apt-get install -f` PowerShell paketi Yapılandırma tamamlandıktan sonra bu sorunları giderir.</span><span class="sxs-lookup"><span data-stu-id="fccc1-174">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="fccc1-175">Kaldırma - Debian 8</span><span class="sxs-lookup"><span data-stu-id="fccc1-175">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="fccc1-176">Debian 9</span><span class="sxs-lookup"><span data-stu-id="fccc1-176">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="fccc1-177">Paket Deposu - Debian 9 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="fccc1-177">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="fccc1-178">Linux için PowerShell Core, paket depolarınızın kolay yükleme (ve güncelleştirmeleri) için yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="fccc1-178">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="fccc1-179">Bu tercih edilen yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="fccc1-179">This is the preferred method.</span></span>

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

<span data-ttu-id="fccc1-180">Microsoft depo süper kullanıcı bir kez kaydolduktan sonra daha sonra kullanmanız yeterlidir `sudo apt-get upgrade powershell` güncelleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="fccc1-180">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="fccc1-181">Doğrudan indirme - Debian 9 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="fccc1-181">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="fccc1-182">Debian paketi indirme `powershell_6.0.2-1.debian.9_amd64.deb` gelen [sürümleri][] Debian makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="fccc1-182">Download the Debian package `powershell_6.0.2-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="fccc1-183">Ardından aşağıdakileri terminalde yürütün:</span><span class="sxs-lookup"><span data-stu-id="fccc1-183">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="fccc1-184">Kaldırma - Debian 9</span><span class="sxs-lookup"><span data-stu-id="fccc1-184">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="fccc1-185">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="fccc1-185">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="fccc1-186">Bu paket, Oracle Linux 7'de de çalışır.</span><span class="sxs-lookup"><span data-stu-id="fccc1-186">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="fccc1-187">Paket (tercih edilir) - deposu CentOS 7 ile yükleme</span><span class="sxs-lookup"><span data-stu-id="fccc1-187">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="fccc1-188">Linux için PowerShell Core, resmi Microsoft depolara kolay yükleme (ve güncelleştirmeleri) için yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="fccc1-188">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="fccc1-189">Microsoft depo süper kullanıcı bir kez kaydolduktan sonra kullanmak yeterlidir `sudo yum update powershell` PowerShell güncelleştirilecek.</span><span class="sxs-lookup"><span data-stu-id="fccc1-189">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="fccc1-190">Doğrudan indirme - CentOS 7 ile yükleme</span><span class="sxs-lookup"><span data-stu-id="fccc1-190">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="fccc1-191">Kullanarak [CentOS 7][], RPM paketini indirme `powershell-6.0.2-1.rhel.7.x86_64.rpm` gelen [sürümleri][] CentOS makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="fccc1-191">Using [CentOS 7][], download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="fccc1-192">Ardından aşağıdakileri terminalde yürütün:</span><span class="sxs-lookup"><span data-stu-id="fccc1-192">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="fccc1-193">RPM karşıdan ara adım olmadan da yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="fccc1-193">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="fccc1-194">Kaldırma - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="fccc1-194">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="fccc1-196">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="fccc1-196">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="fccc1-197">Paket (tercih edilir) - deposu Red Hat Enterprise Linux (RHEL) 7 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="fccc1-197">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="fccc1-198">Linux için PowerShell Core, resmi Microsoft depolara kolay yükleme (ve güncelleştirmeleri) için yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="fccc1-198">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="fccc1-199">Microsoft depo süper kullanıcı bir kez kaydolduktan sonra kullanmak yeterlidir `sudo yum update powershell` PowerShell güncelleştirilecek.</span><span class="sxs-lookup"><span data-stu-id="fccc1-199">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="fccc1-200">Doğrudan indirme - Red Hat Enterprise Linux (RHEL) 7 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="fccc1-200">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="fccc1-201">RPM paketini indirme `powershell-6.0.2-1.rhel.7.x86_64.rpm` gelen [sürümleri][] Red Hat Enterprise Linux makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="fccc1-201">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="fccc1-202">Ardından aşağıdakileri terminalde yürütün:</span><span class="sxs-lookup"><span data-stu-id="fccc1-202">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="fccc1-203">RPM karşıdan ara adım olmadan da yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="fccc1-203">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="fccc1-204">Kaldırma - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="fccc1-204">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse-423"></a><span data-ttu-id="fccc1-205">OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="fccc1-205">OpenSUSE 42.3</span></span>

<span data-ttu-id="fccc1-206">PowerShell Core yükleme sırasında `zypper` şu hatayı bildirin:</span><span class="sxs-lookup"><span data-stu-id="fccc1-206">When installing PowerShell Core, `zypper` may report the following error:</span></span>

```Output
Problem: nothing provides libcurl needed by powershell-6.0.1-1.rhel.7.x86_64
 Solution 1: do not install powershell-6.0.1-1.rhel.7.x86_64
 Solution 2: break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies
```

<span data-ttu-id="fccc1-207">Bu durumda, doğrulayın bir uyumlu `libcurl` kitaplığı varsa aşağıdaki gösterir komut denetleyerek `libcurl4` paketini yüklü olarak:</span><span class="sxs-lookup"><span data-stu-id="fccc1-207">In this case, verify that a compatible `libcurl` library is present by checking that the following command shows the `libcurl4` package as installed:</span></span>

```sh
zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
```

<span data-ttu-id="fccc1-208">Ardından `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` PowerShell paketi yüklerken bir çözüm.</span><span class="sxs-lookup"><span data-stu-id="fccc1-208">Then choose the `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` solution when installing the PowerShell package.</span></span>

### <a name="installation-via-package-repository-preferred---opensuse-423"></a><span data-ttu-id="fccc1-209">Paket (tercih edilir) - deposu OpenSUSE 42.3 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="fccc1-209">Installation via Package Repository (preferred) - OpenSUSE 42.3</span></span>

<span data-ttu-id="fccc1-210">Linux için PowerShell Core, resmi Microsoft depolara kolay yükleme (ve güncelleştirmeleri) için yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="fccc1-210">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---opensuse-423"></a><span data-ttu-id="fccc1-211">Doğrudan indirme - OpenSUSE 42.3 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="fccc1-211">Installation via Direct Download - OpenSUSE 42.3</span></span>

<span data-ttu-id="fccc1-212">RPM paketini indirme `powershell-6.0.2-1.rhel.7.x86_64.rpm` gelen [sürümleri][] OpenSUSE makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="fccc1-212">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the OpenSUSE machine.</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="fccc1-213">RPM karşıdan ara adım olmadan da yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="fccc1-213">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-423"></a><span data-ttu-id="fccc1-214">Kaldırma - OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="fccc1-214">Uninstallation - OpenSUSE 42.3</span></span>

```sh
sudo zypper remove powershell
```

## <a name="fedora"></a><span data-ttu-id="fccc1-215">Fedora</span><span class="sxs-lookup"><span data-stu-id="fccc1-215">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="fccc1-216">28 fedora yalnızca PowerShell Core 6.1 ve üzeri sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="fccc1-216">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="fccc1-217">Paket (tercih edilir) - deposu Fedora 27 Fedora 28 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="fccc1-217">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="fccc1-218">Linux için PowerShell Core, resmi Microsoft depolara kolay yükleme (ve güncelleştirmeleri) için yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="fccc1-218">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="fccc1-219">Doğrudan indirme - 27 Fedora, Fedora 28 aracılığıyla yükleme</span><span class="sxs-lookup"><span data-stu-id="fccc1-219">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="fccc1-220">RPM paketini indirme `powershell-6.0.2-1.rhel.7.x86_64.rpm` gelen [sürümleri][] Fedora makine sayfaya.</span><span class="sxs-lookup"><span data-stu-id="fccc1-220">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="fccc1-221">Ardından aşağıdakileri terminalde yürütün:</span><span class="sxs-lookup"><span data-stu-id="fccc1-221">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="fccc1-222">RPM karşıdan ara adım olmadan da yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="fccc1-222">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="fccc1-223">Kaldırma - 27, Fedora Fedora 28</span><span class="sxs-lookup"><span data-stu-id="fccc1-223">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="fccc1-224">Linux arch</span><span class="sxs-lookup"><span data-stu-id="fccc1-224">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="fccc1-225">Deneysel yay desteği.</span><span class="sxs-lookup"><span data-stu-id="fccc1-225">Arch support is experimental.</span></span>

<span data-ttu-id="fccc1-226">PowerShell kullanılabilir [Linux arch][] kullanıcı deposu (AUR).</span><span class="sxs-lookup"><span data-stu-id="fccc1-226">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="fccc1-227">İle derlenebilir [en son sürümü etiketlendi][arch-release]</span><span class="sxs-lookup"><span data-stu-id="fccc1-227">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="fccc1-228">Gelen derlenebilir [ana son kaydetme][arch-git]</span><span class="sxs-lookup"><span data-stu-id="fccc1-228">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="fccc1-229">Kullanılarak yüklenebilir [ikili en son sürüm][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="fccc1-229">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="fccc1-230">AUR paketlerinde saklanır topluluk - resmi desteği yoktur.</span><span class="sxs-lookup"><span data-stu-id="fccc1-230">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="fccc1-231">AUR paketlerini yükleme hakkında daha fazla bilgi için bkz: [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) veya topluluk [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="fccc1-231">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Linux arch]: https://www.archlinux.org/download/
[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="linux-appimage"></a><span data-ttu-id="fccc1-233">Linux AppImage</span><span class="sxs-lookup"><span data-stu-id="fccc1-233">Linux AppImage</span></span>

> [!NOTE]
> <span data-ttu-id="fccc1-234">Deneysel AppImage desteği</span><span class="sxs-lookup"><span data-stu-id="fccc1-234">AppImage support is experimental</span></span>

<span data-ttu-id="fccc1-235">Son bir Linux dağıtımını kullanarak indirme AppImage `powershell-6.0.1-x86_64.AppImage` gelen [sürümleri][] Linux makinesi sayfaya.</span><span class="sxs-lookup"><span data-stu-id="fccc1-235">Using a recent Linux distribution, download the AppImage `powershell-6.0.1-x86_64.AppImage` from the [releases][] page onto the Linux machine.</span></span>

<span data-ttu-id="fccc1-236">Ardından aşağıdakileri terminalde yürütün:</span><span class="sxs-lookup"><span data-stu-id="fccc1-236">Then execute the following in the terminal:</span></span>

```bash
chmod a+x powershell-6.0.1-x86_64.AppImage
./powershell-6.0.1-x86_64.AppImage
```

<span data-ttu-id="fccc1-237">[AppImage][] , PowerShell yüklemeden çalıştırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="fccc1-237">The [AppImage][] lets you run PowerShell without installing it.</span></span>
<span data-ttu-id="fccc1-238">PowerShell ve bağımlılıklarını (.NET Core'nın sistem bağımlılıklar dahil olmak üzere) cohesive tek bir pakette toplamıştır taşınabilir bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="fccc1-238">It is a portable application that bundles PowerShell and its dependencies (including .NET Core's system dependencies) into one cohesive package.</span></span>
<span data-ttu-id="fccc1-239">Bu paket, kullanıcının Linux dağıtım bağımsız olarak çalışan tek bir ikili dosyadır.</span><span class="sxs-lookup"><span data-stu-id="fccc1-239">This package is a single binary that works independently of the user's Linux distribution.</span></span>

[appimage]: http://appimage.org/

## <a name="kali"></a><span data-ttu-id="fccc1-241">Kali</span><span class="sxs-lookup"><span data-stu-id="fccc1-241">Kali</span></span>

> [!NOTE]
> <span data-ttu-id="fccc1-242">Deneysel Kali desteği.</span><span class="sxs-lookup"><span data-stu-id="fccc1-242">Kali support is experimental.</span></span>

### <a name="installation"></a><span data-ttu-id="fccc1-243">Yükleme</span><span class="sxs-lookup"><span data-stu-id="fccc1-243">Installation</span></span>

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

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a><span data-ttu-id="fccc1-244">PowerShell yüklemeden son Kali içinde (GNU/Linux Kali çalışırken) çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="fccc1-244">Run PowerShell in latest Kali (Kali GNU/Linux Rolling) without installing it</span></span>

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.2-x86_64.AppImage

# Start PowerShell
./powershell-6.0.2-x86_64.AppImage
```

### <a name="uninstallation---kali"></a><span data-ttu-id="fccc1-245">Kaldırma - Kali</span><span class="sxs-lookup"><span data-stu-id="fccc1-245">Uninstallation - Kali</span></span>

```sh
sudo dpkg -r powershell_6.0.2-1.ubuntu.16.04_amd64.deb
```

## <a name="raspbian"></a><span data-ttu-id="fccc1-246">Raspbian</span><span class="sxs-lookup"><span data-stu-id="fccc1-246">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="fccc1-247">Deneysel Raspbian desteği.</span><span class="sxs-lookup"><span data-stu-id="fccc1-247">Raspbian support is experimental.</span></span>

<span data-ttu-id="fccc1-248">Şu anda PowerShell yalnızca Raspbian Esnetme üzerinde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="fccc1-248">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="fccc1-249">Ayrıca CoreCLR (ve bu nedenle PowerShell Core) yalnızca Pi 2 ve Pi 3 cihazlarında diğer cihazlar gibi çalışır [Pi sıfır](https://github.com/dotnet/coreclr/issues/10605), desteklenmeyen bir işlemciye sahip.</span><span class="sxs-lookup"><span data-stu-id="fccc1-249">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="fccc1-250">İndirme [Raspbian Esnetme](https://www.raspberrypi.org/downloads/raspbian/) izleyin [yükleme yönergeleri](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) Pi'yi almak için.</span><span class="sxs-lookup"><span data-stu-id="fccc1-250">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation"></a><span data-ttu-id="fccc1-251">Yükleme</span><span class="sxs-lookup"><span data-stu-id="fccc1-251">Installation</span></span>

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

<span data-ttu-id="fccc1-252">İsteğe bağlı olarak PowerShell "pwsh" ikili yol belirtmeden başlatabilmeniz için bir sembolik bağlantı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fccc1-252">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="fccc1-253">Kaldırma - Raspbian</span><span class="sxs-lookup"><span data-stu-id="fccc1-253">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="fccc1-254">İkili Arşivi</span><span class="sxs-lookup"><span data-stu-id="fccc1-254">Binary Archives</span></span>

<span data-ttu-id="fccc1-255">PowerShell ikili `tar.gz` arşivleri gelişmiş dağıtım senaryoları etkinleştirmek Linux platformlar için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="fccc1-255">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="fccc1-256">Bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="fccc1-256">Dependencies</span></span>

<span data-ttu-id="fccc1-257">PowerShell tüm Linux dağıtımları için taşınabilir ikili dosyaları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fccc1-257">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="fccc1-258">Ancak farklı bağımlılıklara farklı dağıtımlar üzerinde .NET Core çalışma zamanı gerektirir ve bu nedenle aynı PowerShell yapar.</span><span class="sxs-lookup"><span data-stu-id="fccc1-258">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="fccc1-259">Aşağıdaki tabloda farklı Linux dağıtımlarında resmi olarak desteklenen .NET Core 2.0 bağımlılıkları gösterir.</span><span class="sxs-lookup"><span data-stu-id="fccc1-259">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="fccc1-260">İşletim sistemi</span><span class="sxs-lookup"><span data-stu-id="fccc1-260">OS</span></span>                 | <span data-ttu-id="fccc1-261">Bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="fccc1-261">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="fccc1-262">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="fccc1-262">Ubuntu 14.04</span></span>       | <span data-ttu-id="fccc1-263">libc6, libgcc1, libgssapi-krb5-2 liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="fccc1-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="fccc1-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="fccc1-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="fccc1-265">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="fccc1-265">Ubuntu 16.04</span></span>       | <span data-ttu-id="fccc1-266">libc6, libgcc1, libgssapi-krb5-2 liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="fccc1-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="fccc1-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="fccc1-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="fccc1-268">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="fccc1-268">Ubuntu 17.10</span></span>       | <span data-ttu-id="fccc1-269">libc6, libgcc1, libgssapi-krb5-2 liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="fccc1-269">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="fccc1-270">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="fccc1-270">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="fccc1-271">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="fccc1-271">Ubuntu 18.04</span></span>       | <span data-ttu-id="fccc1-272">libc6, libgcc1, libgssapi-krb5-2 liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="fccc1-272">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="fccc1-273">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="fccc1-273">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="fccc1-274">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="fccc1-274">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="fccc1-275">libc6, libgcc1, libgssapi-krb5-2 liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="fccc1-275">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="fccc1-276">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="fccc1-276">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="fccc1-277">Debian 9 (Esnetme)</span><span class="sxs-lookup"><span data-stu-id="fccc1-277">Debian 9 (Stretch)</span></span> | <span data-ttu-id="fccc1-278">libc6, libgcc1, libgssapi-krb5-2 liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="fccc1-278">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="fccc1-279">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="fccc1-279">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="fccc1-280">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="fccc1-280">CentOS 7</span></span> <br> <span data-ttu-id="fccc1-281">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="fccc1-281">Oracle Linux 7</span></span> <br> <span data-ttu-id="fccc1-282">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="fccc1-282">RHEL 7</span></span> <br> <span data-ttu-id="fccc1-283">OpenSUSE OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="fccc1-283">OpenSUSE OpenSUSE 42.3</span></span> | <span data-ttu-id="fccc1-284">libunwind, libcurl, openssl kitaplıkları, libicu</span><span class="sxs-lookup"><span data-stu-id="fccc1-284">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="fccc1-285">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="fccc1-285">Fedora 27</span></span> <br> <span data-ttu-id="fccc1-286">28 fedora</span><span class="sxs-lookup"><span data-stu-id="fccc1-286">Fedora 28</span></span> | <span data-ttu-id="fccc1-287">libunwind, libcurl, openssl kitaplıkları, libicu, compat openssl10</span><span class="sxs-lookup"><span data-stu-id="fccc1-287">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="fccc1-288">Resmi olarak desteklenmez Linux dağıtımlarında PowerShell ikili dosyaları dağıtmak için ayrı adımları hedef işletim sistemi için gerekli bağımlılıkları yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="fccc1-288">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="fccc1-289">Örneğin, bizim [Amazon Linux dockerfile] [ amazon-dockerfile] ilk bağımlılıkları yükler ve ardından Linux ayıklar `tar.gz` arşiv.</span><span class="sxs-lookup"><span data-stu-id="fccc1-289">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="fccc1-290">Yükleme - ikili Arşivi</span><span class="sxs-lookup"><span data-stu-id="fccc1-290">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="fccc1-291">Linux</span><span class="sxs-lookup"><span data-stu-id="fccc1-291">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="fccc1-292">Kaldırma ikili Arşivi</span><span class="sxs-lookup"><span data-stu-id="fccc1-292">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="fccc1-293">Yollar</span><span class="sxs-lookup"><span data-stu-id="fccc1-293">Paths</span></span>

* <span data-ttu-id="fccc1-294">`$PSHOME` olduğu `/opt/microsoft/powershell/6.0.2/`</span><span class="sxs-lookup"><span data-stu-id="fccc1-294">`$PSHOME` is `/opt/microsoft/powershell/6.0.2/`</span></span>
* <span data-ttu-id="fccc1-295">Kullanıcı profillerini okuyabilir `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="fccc1-295">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="fccc1-296">Varsayılan profiller okuyabilir `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="fccc1-296">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="fccc1-297">Kullanıcı modülleri okuyabilir `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="fccc1-297">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="fccc1-298">Paylaşılan modülleri okuyabilir `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="fccc1-298">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="fccc1-299">Varsayılan modülleri okuyabilir `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="fccc1-299">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="fccc1-300">PSReadline geçmişi için kaydedilir `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="fccc1-300">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="fccc1-301">Varsayılan konak özel profilleri var Bu nedenle, PowerShell'in konak başına yapılandırma profilleri dikkate `Microsoft.PowerShell_profile.ps1` aynı konumlarda.</span><span class="sxs-lookup"><span data-stu-id="fccc1-301">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="fccc1-302">PowerShell uyar [XDG temel dizin belirtimi] [ xdg-bds] Linux üzerinde.</span><span class="sxs-lookup"><span data-stu-id="fccc1-302">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[sürümleri]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
