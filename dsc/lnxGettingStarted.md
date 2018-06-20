---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: Linux için istenen durum yapılandırması (DSC) ile çalışmaya başlama
ms.openlocfilehash: 0534cede979eb2917adb608dba622539fe4bdc45
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189440"
---
# <a name="get-started-with-desired-state-configuration-dsc-for-linux"></a><span data-ttu-id="d0708-103">Linux için istenen durum yapılandırması (DSC) ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="d0708-103">Get started with Desired State Configuration (DSC) for Linux</span></span>

<span data-ttu-id="d0708-104">Bu konuda Linux için PowerShell istenen durum yapılandırması (DSC) ile çalışmaya başlamak açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d0708-104">This topic explains how to get started using PowerShell Desired State Configuration (DSC) for Linux.</span></span> <span data-ttu-id="d0708-105">DSC hakkında genel bilgi için bkz: [Windows PowerShell istenen durum yapılandırması ile çalışmaya başlama](overview.md).</span><span class="sxs-lookup"><span data-stu-id="d0708-105">For general information about DSC, see [Get Started with Windows PowerShell Desired State Configuration](overview.md).</span></span>

## <a name="supported-linux-operation-system-versions"></a><span data-ttu-id="d0708-106">Desteklenen Linux işlemi sistemi sürümleri</span><span class="sxs-lookup"><span data-stu-id="d0708-106">Supported Linux operation system versions</span></span>

<span data-ttu-id="d0708-107">Aşağıdaki Linux işletim sistemi sürümleri için DSC Linux için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="d0708-107">The following Linux operating system versions are supported for DSC for Linux.</span></span>
- <span data-ttu-id="d0708-108">CentOS 5, 6 ve 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="d0708-108">CentOS 5, 6, and 7 (x86/x64)</span></span>
- <span data-ttu-id="d0708-109">Debian GNU/Linux 6, 7 ve 8 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="d0708-109">Debian GNU/Linux 6, 7 and 8 (x86/x64)</span></span>
- <span data-ttu-id="d0708-110">Oracle Linux 5, 6 ve 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="d0708-110">Oracle Linux 5, 6 and 7 (x86/x64)</span></span>
- <span data-ttu-id="d0708-111">Red Hat Enterprise Linux Server 5, 6 ve 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="d0708-111">Red Hat Enterprise Linux Server 5, 6 and 7 (x86/x64)</span></span>
- <span data-ttu-id="d0708-112">SUSE Linux Enterprise Server 10, 11 ve 12 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="d0708-112">SUSE Linux Enterprise Server 10, 11 and 12 (x86/x64)</span></span>
- <span data-ttu-id="d0708-113">Ubuntu Server 12.04 LTS, 14.04 LTS ve 16.04 LTS (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="d0708-113">Ubuntu Server 12.04 LTS, 14.04 LTS and 16.04 LTS (x86/x64)</span></span>

<span data-ttu-id="d0708-114">Aşağıdaki tabloda, Linux için DSC için gerekli paket bağımlılıkları açıklar.</span><span class="sxs-lookup"><span data-stu-id="d0708-114">The following table describes the required package dependencies for DSC for Linux.</span></span>

|  <span data-ttu-id="d0708-115">Gerekli paket</span><span class="sxs-lookup"><span data-stu-id="d0708-115">Required package</span></span> |  <span data-ttu-id="d0708-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d0708-116">Description</span></span> |  <span data-ttu-id="d0708-117">En düşük sürüm</span><span class="sxs-lookup"><span data-stu-id="d0708-117">Minimum version</span></span> |
|---|---|---|
| <span data-ttu-id="d0708-118">Glibc</span><span class="sxs-lookup"><span data-stu-id="d0708-118">glibc</span></span>| <span data-ttu-id="d0708-119">GNU Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="d0708-119">GNU Library</span></span>| <span data-ttu-id="d0708-120">2... 4 – 31.30</span><span class="sxs-lookup"><span data-stu-id="d0708-120">2…4 – 31.30</span></span>|
| <span data-ttu-id="d0708-121">Python</span><span class="sxs-lookup"><span data-stu-id="d0708-121">python</span></span>| <span data-ttu-id="d0708-122">Python</span><span class="sxs-lookup"><span data-stu-id="d0708-122">Python</span></span>| <span data-ttu-id="d0708-123">2.4 – 3.4</span><span class="sxs-lookup"><span data-stu-id="d0708-123">2.4 – 3.4</span></span>|
| <span data-ttu-id="d0708-124">omiserver</span><span class="sxs-lookup"><span data-stu-id="d0708-124">omiserver</span></span>| <span data-ttu-id="d0708-125">Açık Yönetim Altyapısı</span><span class="sxs-lookup"><span data-stu-id="d0708-125">Open Management Infrastructure</span></span>| <span data-ttu-id="d0708-126">1.0.8.1</span><span class="sxs-lookup"><span data-stu-id="d0708-126">1.0.8.1</span></span>|
| <span data-ttu-id="d0708-127">Openssl</span><span class="sxs-lookup"><span data-stu-id="d0708-127">openssl</span></span>| <span data-ttu-id="d0708-128">OpenSSL kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="d0708-128">OpenSSL Libraries</span></span>| <span data-ttu-id="d0708-129">0.9.8 veya 1.0</span><span class="sxs-lookup"><span data-stu-id="d0708-129">0.9.8 or 1.0</span></span>|
| <span data-ttu-id="d0708-130">ctypes</span><span class="sxs-lookup"><span data-stu-id="d0708-130">ctypes</span></span>| <span data-ttu-id="d0708-131">Python CTypes kitaplığı</span><span class="sxs-lookup"><span data-stu-id="d0708-131">Python CTypes library</span></span>| <span data-ttu-id="d0708-132">Python sürümü aynı olmalıdır</span><span class="sxs-lookup"><span data-stu-id="d0708-132">Must match Python version</span></span>|
| <span data-ttu-id="d0708-133">libcurl</span><span class="sxs-lookup"><span data-stu-id="d0708-133">libcurl</span></span>| <span data-ttu-id="d0708-134">cURL http istemci kitaplığı</span><span class="sxs-lookup"><span data-stu-id="d0708-134">cURL http client library</span></span>| <span data-ttu-id="d0708-135">7.15.1</span><span class="sxs-lookup"><span data-stu-id="d0708-135">7.15.1</span></span>|

## <a name="installing-dsc-for-linux"></a><span data-ttu-id="d0708-136">Linux için DSC yükleme</span><span class="sxs-lookup"><span data-stu-id="d0708-136">Installing DSC for Linux</span></span>

<span data-ttu-id="d0708-137">Yüklemelisiniz [açık Yönetim Altyapısı (OMI)](https://github.com/Microsoft/omi) Linux için DSC yüklemeden önce.</span><span class="sxs-lookup"><span data-stu-id="d0708-137">You must install the [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi) before installing DSC for Linux.</span></span>

### <a name="installing-omi"></a><span data-ttu-id="d0708-138">OMI yükleme</span><span class="sxs-lookup"><span data-stu-id="d0708-138">Installing OMI</span></span>

<span data-ttu-id="d0708-139">İstenen durum yapılandırması sürümü 1.0.8.1 açık Yönetim Altyapısı (OMI) CIM sunucusu Linux gerektirir veya sonraki bir sürümü.</span><span class="sxs-lookup"><span data-stu-id="d0708-139">Desired State Configuration for Linux requires the Open Management Infrastructure (OMI) CIM server, version 1.0.8.1 or later.</span></span> <span data-ttu-id="d0708-140">OMI açık grubundan indirilebilir: [açık Yönetim Altyapısı (OMI)](https://github.com/Microsoft/omi).</span><span class="sxs-lookup"><span data-stu-id="d0708-140">OMI can be downloaded from The Open Group: [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi).</span></span>

<span data-ttu-id="d0708-141">OMI yüklemek için Linux sistemine (.rpm veya .deb) ve OpenSSL sürümü (ssl_098 veya ssl_100) ve mimari (x64/x86) uygun paketini yükleyin.</span><span class="sxs-lookup"><span data-stu-id="d0708-141">To install OMI, install the package that is appropriate for your Linux system (.rpm or .deb) and OpenSSL version (ssl_098 or ssl_100), and architecture (x64/x86).</span></span> <span data-ttu-id="d0708-142">RPM paketleri, CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server ve Oracle Linux için uygundur.</span><span class="sxs-lookup"><span data-stu-id="d0708-142">RPM packages are appropriate for CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server, and Oracle Linux.</span></span> <span data-ttu-id="d0708-143">DEB paketleri Debian GNU/Linux ve Ubuntu Server için uygundur.</span><span class="sxs-lookup"><span data-stu-id="d0708-143">DEB packages are appropriate for Debian GNU/Linux and Ubuntu Server.</span></span> <span data-ttu-id="d0708-144">Ssl_098 paketleri OpenSSL 0.9.8 ssl_100 paketleri OpenSSL 1.0 yüklü bilgisayarlar için uygun durumdayken yüklü olan bilgisayarlar için uygundur.</span><span class="sxs-lookup"><span data-stu-id="d0708-144">The ssl_098 packages are appropriate for computers with OpenSSL 0.9.8 installed while the ssl_100 packages are appropriate for computers with OpenSSL 1.0 installed.</span></span>

> <span data-ttu-id="d0708-145">**Not**: yüklü olan bir OpenSSL sürümü belirlemek için komutu çalıştırmak `openssl version`.</span><span class="sxs-lookup"><span data-stu-id="d0708-145">**Note**: To determine the installed OpenSSL version, run the command `openssl version`.</span></span>

<span data-ttu-id="d0708-146">OMI CentOS 7 x64 sisteme yüklemek için aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d0708-146">Run the following command to install OMI on a CentOS 7 x64 system.</span></span>

`# sudo rpm -Uvh omiserver-1.0.8.ssl_100.rpm`

### <a name="installing-dsc"></a><span data-ttu-id="d0708-147">DSC yükleme</span><span class="sxs-lookup"><span data-stu-id="d0708-147">Installing DSC</span></span>

<span data-ttu-id="d0708-148">Linux için DSC indirilebilir [burada](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/latest).</span><span class="sxs-lookup"><span data-stu-id="d0708-148">DSC for Linux is available for download [here](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/latest).</span></span>

<span data-ttu-id="d0708-149">DSC yüklemek için Linux sistemine (.rpm veya .deb) ve OpenSSL sürümü (ssl_098 veya ssl_100) ve mimari (x64/x86) uygun paketini yükleyin.</span><span class="sxs-lookup"><span data-stu-id="d0708-149">To install DSC, install the package that is appropriate for your Linux system (.rpm or .deb) and OpenSSL version (ssl_098 or ssl_100), and architecture (x64/x86).</span></span> <span data-ttu-id="d0708-150">RPM paketleri, CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server ve Oracle Linux için uygundur.</span><span class="sxs-lookup"><span data-stu-id="d0708-150">RPM packages are appropriate for CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server, and Oracle Linux.</span></span> <span data-ttu-id="d0708-151">DEB paketleri Debian GNU/Linux ve Ubuntu Server için uygundur.</span><span class="sxs-lookup"><span data-stu-id="d0708-151">DEB packages are appropriate for Debian GNU/Linux and Ubuntu Server.</span></span> <span data-ttu-id="d0708-152">Ssl_098 paketleri OpenSSL 0.9.8 ssl_100 paketleri OpenSSL 1.0 yüklü bilgisayarlar için uygun durumdayken yüklü olan bilgisayarlar için uygundur.</span><span class="sxs-lookup"><span data-stu-id="d0708-152">The ssl_098 packages are appropriate for computers with OpenSSL 0.9.8 installed while the ssl_100 packages are appropriate for computers with OpenSSL 1.0 installed.</span></span>

> <span data-ttu-id="d0708-153">**Not**: yüklü olan bir OpenSSL sürümü belirlemek için komut openssl sürümü çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d0708-153">**Note**: To determine the installed OpenSSL version, run the command openssl version.</span></span>

<span data-ttu-id="d0708-154">DSC CentOS 7 x64 sisteme yüklemek için aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d0708-154">Run the following command to install DSC on a CentOS 7 x64 system.</span></span>

`# sudo rpm -Uvh dsc-1.0.0-254.ssl_100.x64.rpm`


## <a name="using-dsc-for-linux"></a><span data-ttu-id="d0708-155">Linux için DSC kullanma</span><span class="sxs-lookup"><span data-stu-id="d0708-155">Using DSC for Linux</span></span>

<span data-ttu-id="d0708-156">Aşağıdaki bölümlerde, oluşturma ve Linux bilgisayarlarda DSC yapılandırmaları çalıştırma açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d0708-156">The following sections explain how to create and run DSC configurations on Linux computers.</span></span>

### <a name="creating-a-configuration-mof-document"></a><span data-ttu-id="d0708-157">Bir yapılandırma MOF belge oluşturma</span><span class="sxs-lookup"><span data-stu-id="d0708-157">Creating a configuration MOF document</span></span>

<span data-ttu-id="d0708-158">Windows PowerShell yapılandırması anahtar sözcüğü, Windows bilgisayarları için olduğu gibi Linux bilgisayarlar için bir yapılandırma oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d0708-158">The Windows PowerShell Configuration keyword is used to create a configuration for Linux computers, just like for Windows computers.</span></span> <span data-ttu-id="d0708-159">Aşağıdaki adımlar, Windows PowerShell kullanarak bir Linux bilgisayar için bir yapılandırma belge oluşturulmasını açıklar.</span><span class="sxs-lookup"><span data-stu-id="d0708-159">The following steps describe the creation of a configuration document for a Linux computer using Windows PowerShell.</span></span>

1. <span data-ttu-id="d0708-160">Nx modülünü içeri aktarın.</span><span class="sxs-lookup"><span data-stu-id="d0708-160">Import the nx module.</span></span> <span data-ttu-id="d0708-161">Nx Windows PowerShell modülü yerleşik kaynaklar için şema DSC için Linux için içerir ve yerel bilgisayarınıza yüklenmeli ve yapılandırmada içeri aktarıldı.</span><span class="sxs-lookup"><span data-stu-id="d0708-161">The nx Windows PowerShell module contains the schema for Built-In resources for DSC for Linux, and must be installed to your local computer and imported in the configuration.</span></span>

    <span data-ttu-id="d0708-162">-Nx modülünü yüklemek için nx modülü dizini ya da kopyalama `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` veya `$PSHOME\Modules`.</span><span class="sxs-lookup"><span data-stu-id="d0708-162">-To install the nx module, copy the nx module directory to either `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` or `$PSHOME\Modules`.</span></span> <span data-ttu-id="d0708-163">Nx modülü DSC Linux yükleme paketinin (MSI) dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="d0708-163">The nx module is included in the DSC for Linux installation package (MSI).</span></span> <span data-ttu-id="d0708-164">Yapılandırmanızda nx modülü içeri aktarmak için kullanın __alma DSCResource__ komutu:</span><span class="sxs-lookup"><span data-stu-id="d0708-164">To import the nx module in your configuration, use the __Import-DSCResource__ command:</span></span>

```powershell
Configuration ExampleConfiguration{

    Import-DSCResource -Module nx

}
```
2. <span data-ttu-id="d0708-165">Yapılandırma belge oluşturmak ve bir yapılandırma tanımlayın:</span><span class="sxs-lookup"><span data-stu-id="d0708-165">Define a configuration and generate the configuration document:</span></span>

```powershell
Configuration ExampleConfiguration{

    Import-DscResource -Module nx

    Node  "linuxhost.contoso.com"{
    nxFile ExampleFile {

        DestinationPath = "/tmp/example"
        Contents = "hello world `n"
        Ensure = "Present"
        Type = "File"
    }

    }
}
ExampleConfiguration -OutputPath:"C:\temp"
```

### <a name="push-the-configuration-to-the-linux-computer"></a><span data-ttu-id="d0708-166">Linux bilgisayara yapılandırma bildirme</span><span class="sxs-lookup"><span data-stu-id="d0708-166">Push the configuration to the Linux computer</span></span>

<span data-ttu-id="d0708-167">Yapılandırma belgeleri (MOF dosyaları) gönderilen Linux kullanarak bilgisayar [başlangıç DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="d0708-167">Configuration documents (MOF files) can be pushed to the Linux computer using the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet.</span></span> <span data-ttu-id="d0708-168">Bu cmdlet ile birlikte kullanmak için [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379.aspx), veya [Test DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlet'leri, uzaktan Linux bilgisayara bir CIMSession kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d0708-168">In order to use this cmdlet, along with the [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379.aspx), or [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlets, remotely to a Linux computer, you must use a CIMSession.</span></span> <span data-ttu-id="d0708-169">[New-CimSession](http://go.microsoft.com/fwlink/?LinkId=227967) cmdlet CIMSession Linux bilgisayara oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d0708-169">The [New-CimSession](http://go.microsoft.com/fwlink/?LinkId=227967) cmdlet is used to create a CIMSession to the Linux computer.</span></span>

<span data-ttu-id="d0708-170">Aşağıdaki kod bir CIMSession DSC için Linux için oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d0708-170">The following code shows how to create a CIMSession for DSC for Linux.</span></span>

```powershell
$Node = "ostc-dsc-01"
$Credential = Get-Credential -UserName:"root" -Message:"Enter Password:"

#Ignore SSL certificate validation
#$opt = New-CimSessionOption -UseSsl:$true -SkipCACheck:$true -SkipCNCheck:$true -SkipRevocationCheck:$true

#Options for a trusted SSL certificate
$opt = New-CimSessionOption -UseSsl:$true
$Sess=New-CimSession -Credential:$credential -ComputerName:$Node -Port:5986 -Authentication:basic -SessionOption:$opt -OperationTimeoutSec:90
```

> <span data-ttu-id="d0708-171">**Not**:</span><span class="sxs-lookup"><span data-stu-id="d0708-171">**Note**:</span></span>
* <span data-ttu-id="d0708-172">"Gönderme" modu için kullanıcı kimlik bilgileri Linux bilgisayardaki kök kullanıcı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d0708-172">For “Push” mode, the user credential must be the root user on the Linux computer.</span></span>
* <span data-ttu-id="d0708-173">Linux, New-CimSession – UseSSL parametresi $true olarak ayarlanmış kullanılmalıdır yalnızca SSL/TLS bağlantılarını DSC için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="d0708-173">Only SSL/TLS connections are supported for DSC for Linux, the New-CimSession must be used with the –UseSSL parameter set to $true.</span></span>
* <span data-ttu-id="d0708-174">(DSC için) OMI tarafından kullanılan SSL sertifikasını dosyasında belirtilen: `/opt/omi/etc/omiserver.conf` özelliklere sahip: pemfile ve keyfile.</span><span class="sxs-lookup"><span data-stu-id="d0708-174">The SSL certificate used by OMI (for DSC) is specified in the file: `/opt/omi/etc/omiserver.conf` with the properties: pemfile and keyfile.</span></span>
<span data-ttu-id="d0708-175">Bu sertifika çalıştırmakta olduğunuz Windows bilgisayar tarafından güvenilir değilse [New-CimSession](http://go.microsoft.com/fwlink/?LinkId=227967) cmdlet'ini, sertifika doğrulama CIMSession seçeneklerle yoksay seçebilirsiniz: `-SkipCACheck:$true -SkipCNCheck:$true -SkipRevocationCheck:$true`</span><span class="sxs-lookup"><span data-stu-id="d0708-175">If this certificate is not trusted by the Windows computer that you are running the [New-CimSession](http://go.microsoft.com/fwlink/?LinkId=227967) cmdlet on, you can choose to ignore certificate validation with the CIMSession Options: `-SkipCACheck:$true -SkipCNCheck:$true -SkipRevocationCheck:$true`</span></span>

<span data-ttu-id="d0708-176">DSC yapılandırması Linux düğüme göndermek için aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d0708-176">Run the following command to push the DSC configuration to the Linux node.</span></span>

`Start-DscConfiguration -Path:"C:\temp" -CimSession:$Sess -Wait -Verbose`

### <a name="distribute-the-configuration-with-a-pull-server"></a><span data-ttu-id="d0708-177">Bir çekme sunucu yapılandırmasıyla Dağıt</span><span class="sxs-lookup"><span data-stu-id="d0708-177">Distribute the configuration with a pull server</span></span>

<span data-ttu-id="d0708-178">Yapılandırmaları bir çekme sunucusuyla Linux bilgisayara gibi Windows bilgisayarları için dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="d0708-178">Configurations can be distributed to a Linux computer with a pull server, just like for Windows computers.</span></span> <span data-ttu-id="d0708-179">Bir çekme sunucusuna kullanma ile ilgili yönergeler için bkz: [Windows PowerShell istenen durum yapılandırma çekme sunucularına](pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="d0708-179">For guidance on using a pull server, see [Windows PowerShell Desired State Configuration Pull Servers](pullServer.md).</span></span> <span data-ttu-id="d0708-180">Ek bilgi ve Linux bilgisayarları bir çekme sunucusuyla kullanmaya ilişkin sınırlamalar, sürüm notları Linux için istenen durum yapılandırması için bkz.</span><span class="sxs-lookup"><span data-stu-id="d0708-180">For additional information and limitations related to using Linux computers with a pull server, see the Release Notes for Desired State Configuration for Linux.</span></span>

### <a name="working-with-configurations-locally"></a><span data-ttu-id="d0708-181">Yerel olarak yapılandırmaları ile çalışma</span><span class="sxs-lookup"><span data-stu-id="d0708-181">Working with configurations locally</span></span>

<span data-ttu-id="d0708-182">Linux için DSC yapılandırma yerel Linux bilgisayardan çalışmak için komut dosyalarını içerir.</span><span class="sxs-lookup"><span data-stu-id="d0708-182">DSC for Linux includes scripts to work with configuration from the local Linux computer.</span></span> <span data-ttu-id="d0708-183">Bu komut dosyalarını bulun `/opt/microsoft/dsc/Scripts` ve şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="d0708-183">These scripts are locate in `/opt/microsoft/dsc/Scripts` and include the following:</span></span>
* <span data-ttu-id="d0708-184">GetDscConfiguration.py</span><span class="sxs-lookup"><span data-stu-id="d0708-184">GetDscConfiguration.py</span></span>

 <span data-ttu-id="d0708-185">Bilgisayara uygulanan geçerli yapılandırmasını döndürür.</span><span class="sxs-lookup"><span data-stu-id="d0708-185">Returns the current configuration applied to the computer.</span></span> <span data-ttu-id="d0708-186">Windows PowerShell cmdlet Get-DscConfiguration cmdlet'i benzer.</span><span class="sxs-lookup"><span data-stu-id="d0708-186">Similar to the Windows PowerShell cmdlet Get-DscConfiguration cmdlet.</span></span>

`# sudo ./GetDscConfiguration.py`

* <span data-ttu-id="d0708-187">GetDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="d0708-187">GetDscLocalConfigurationManager.py</span></span>

 <span data-ttu-id="d0708-188">Bilgisayara uygulanan geçerli meta yapılandırmasını döndürür.</span><span class="sxs-lookup"><span data-stu-id="d0708-188">Returns the current meta-configuration applied to the computer.</span></span> <span data-ttu-id="d0708-189">Cmdlet benzer [Get-DSCLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="d0708-189">Similar to the cmdlet [Get-DSCLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx) cmdlet.</span></span>

`# sudo ./GetDscLocalConfigurationManager.py`

* <span data-ttu-id="d0708-190">InstallModule.py</span><span class="sxs-lookup"><span data-stu-id="d0708-190">InstallModule.py</span></span>

 <span data-ttu-id="d0708-191">Özel bir DSC kaynağı modülünü yükler.</span><span class="sxs-lookup"><span data-stu-id="d0708-191">Installs a custom DSC resource module.</span></span> <span data-ttu-id="d0708-192">Modül paylaşılan nesne kitaplığını içeren bir .zip dosyası ve şema MOF dosyaları yolunu gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d0708-192">Requires the path to a .zip file containing the module shared object library and schema MOF files.</span></span>

`# sudo ./InstallModule.py /tmp/cnx_Resource.zip`

* <span data-ttu-id="d0708-193">RemoveModule.py</span><span class="sxs-lookup"><span data-stu-id="d0708-193">RemoveModule.py</span></span>

 <span data-ttu-id="d0708-194">Özel bir DSC kaynağı modülü kaldırır.</span><span class="sxs-lookup"><span data-stu-id="d0708-194">Removes a custom DSC resource module.</span></span> <span data-ttu-id="d0708-195">Kaldırılacak modülün adı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d0708-195">Requires the name of the module to remove.</span></span>

`# sudo ./RemoveModule.py cnx_Resource`

* <span data-ttu-id="d0708-196">StartDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="d0708-196">StartDscLocalConfigurationManager.py</span></span>

 <span data-ttu-id="d0708-197">Bir yapılandırma MOF dosyası bilgisayara uygulanır.</span><span class="sxs-lookup"><span data-stu-id="d0708-197">Applies a configuration MOF file to the computer.</span></span> <span data-ttu-id="d0708-198">Benzer şekilde [başlangıç DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="d0708-198">Similar to the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet.</span></span> <span data-ttu-id="d0708-199">Yapılandırmayı uygulamak için MOF yolu gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d0708-199">Requires the path to the configuration MOF to apply.</span></span>

`# sudo ./StartDscLocalConfigurationManager.py –configurationmof /tmp/localhost.mof`

* <span data-ttu-id="d0708-200">SetDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="d0708-200">SetDscLocalConfigurationManager.py</span></span>

 <span data-ttu-id="d0708-201">Bir Meta yapılandırma MOF dosyası bilgisayara uygulanır.</span><span class="sxs-lookup"><span data-stu-id="d0708-201">Applies a Meta Configuration MOF file to the computer.</span></span> <span data-ttu-id="d0708-202">Benzer şekilde [kümesi DSCLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621.aspx) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="d0708-202">Similar to the [Set-DSCLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621.aspx) cmdlet.</span></span> <span data-ttu-id="d0708-203">Uygulanacak Meta yapılandırma MOF yolu gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d0708-203">Requires the path to the Meta Configuration MOF to apply.</span></span>

`# sudo ./SetDscLocalConfigurationManager.py –configurationmof /tmp/localhost.meta.mof`

## <a name="powershell-desired-state-configuration-for-linux-log-files"></a><span data-ttu-id="d0708-204">PowerShell istenen durum yapılandırması Linux günlük dosyaları için</span><span class="sxs-lookup"><span data-stu-id="d0708-204">PowerShell Desired State Configuration for Linux Log Files</span></span>

<span data-ttu-id="d0708-205">Aşağıdaki günlük dosyalarına DSC için Linux iletiler için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d0708-205">The following log files are generated for DSC for Linux messages.</span></span>

|<span data-ttu-id="d0708-206">Günlük dosyası</span><span class="sxs-lookup"><span data-stu-id="d0708-206">Log file</span></span>|<span data-ttu-id="d0708-207">Dizin</span><span class="sxs-lookup"><span data-stu-id="d0708-207">Directory</span></span>|<span data-ttu-id="d0708-208">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d0708-208">Description</span></span>|
|---|---|---|
|<span data-ttu-id="d0708-209">omiserver.log</span><span class="sxs-lookup"><span data-stu-id="d0708-209">omiserver.log</span></span>|<span data-ttu-id="d0708-210">/var/OPT/omi/log</span><span class="sxs-lookup"><span data-stu-id="d0708-210">/var/opt/omi/log</span></span>|<span data-ttu-id="d0708-211">OMI CIM sunucusu işlemi için ilgili iletileri.</span><span class="sxs-lookup"><span data-stu-id="d0708-211">Messages relating to the operation of the OMI CIM server.</span></span>|
|<span data-ttu-id="d0708-212">DSC.log</span><span class="sxs-lookup"><span data-stu-id="d0708-212">dsc.log</span></span>|<span data-ttu-id="d0708-213">/var/OPT/omi/log</span><span class="sxs-lookup"><span data-stu-id="d0708-213">/var/opt/omi/log</span></span>|<span data-ttu-id="d0708-214">Yerel Configuration Manager (LCM'yi) ve DSC kaynak işlemlerinin işlemi için ilgili iletileri.</span><span class="sxs-lookup"><span data-stu-id="d0708-214">Messages relating to the operation of the Local Configuration Manager (LCM) and DSC resource operations.</span></span>|