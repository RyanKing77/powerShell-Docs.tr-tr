---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: Linux için Desired State Configuration (DSC) ile çalışmaya başlama
ms.openlocfilehash: d5a4a17fbcffbbbd6df3dd902dbd104769b7d17e
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893605"
---
# <a name="get-started-with-desired-state-configuration-dsc-for-linux"></a><span data-ttu-id="d698d-103">Linux için Desired State Configuration (DSC) ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="d698d-103">Get started with Desired State Configuration (DSC) for Linux</span></span>

<span data-ttu-id="d698d-104">Bu konuda, Linux için PowerShell Desired State Configuration (DSC) ile çalışmaya başlamak açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d698d-104">This topic explains how to get started using PowerShell Desired State Configuration (DSC) for Linux.</span></span> <span data-ttu-id="d698d-105">DSC hakkında genel bilgi için bkz: [Windows PowerShell Desired State Configuration ile'çalışmaya başlama](overview.md).</span><span class="sxs-lookup"><span data-stu-id="d698d-105">For general information about DSC, see [Get Started with Windows PowerShell Desired State Configuration](overview.md).</span></span>

## <a name="supported-linux-operation-system-versions"></a><span data-ttu-id="d698d-106">Desteklenen Linux işlemi sistemi sürümleri</span><span class="sxs-lookup"><span data-stu-id="d698d-106">Supported Linux operation system versions</span></span>

<span data-ttu-id="d698d-107">Aşağıdaki Linux işletim sistemi sürümleri için DSC Linux için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="d698d-107">The following Linux operating system versions are supported for DSC for Linux.</span></span>

- <span data-ttu-id="d698d-108">CentOS 5, 6 ve 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="d698d-108">CentOS 5, 6, and 7 (x86/x64)</span></span>
- <span data-ttu-id="d698d-109">Debian GNU/Linux 6, 7 ve 8 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="d698d-109">Debian GNU/Linux 6, 7 and 8 (x86/x64)</span></span>
- <span data-ttu-id="d698d-110">Oracle Linux 5, 6 ve 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="d698d-110">Oracle Linux 5, 6 and 7 (x86/x64)</span></span>
- <span data-ttu-id="d698d-111">Red Hat Enterprise Linux Server 5, 6 ve 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="d698d-111">Red Hat Enterprise Linux Server 5, 6 and 7 (x86/x64)</span></span>
- <span data-ttu-id="d698d-112">SUSE Linux Enterprise Server 10, 11 ve 12 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="d698d-112">SUSE Linux Enterprise Server 10, 11 and 12 (x86/x64)</span></span>
- <span data-ttu-id="d698d-113">Ubuntu Server 12.04 LTS, 14.04 LTS ve 16.04 LTS (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="d698d-113">Ubuntu Server 12.04 LTS, 14.04 LTS and 16.04 LTS (x86/x64)</span></span>

<span data-ttu-id="d698d-114">Aşağıdaki tabloda, Linux için DSC için gerekli Paket bağımlılıklarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="d698d-114">The following table describes the required package dependencies for DSC for Linux.</span></span>

|  <span data-ttu-id="d698d-115">Gerekli paket</span><span class="sxs-lookup"><span data-stu-id="d698d-115">Required package</span></span> |  <span data-ttu-id="d698d-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d698d-116">Description</span></span> |  <span data-ttu-id="d698d-117">En düşük sürüm</span><span class="sxs-lookup"><span data-stu-id="d698d-117">Minimum version</span></span> |
|---|---|---|
| <span data-ttu-id="d698d-118">glibc</span><span class="sxs-lookup"><span data-stu-id="d698d-118">glibc</span></span>| <span data-ttu-id="d698d-119">GNU Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="d698d-119">GNU Library</span></span>| <span data-ttu-id="d698d-120">2... 4 – 31.30</span><span class="sxs-lookup"><span data-stu-id="d698d-120">2…4 – 31.30</span></span>|
| <span data-ttu-id="d698d-121">Python</span><span class="sxs-lookup"><span data-stu-id="d698d-121">python</span></span>| <span data-ttu-id="d698d-122">Python</span><span class="sxs-lookup"><span data-stu-id="d698d-122">Python</span></span>| <span data-ttu-id="d698d-123">2.4-3.4</span><span class="sxs-lookup"><span data-stu-id="d698d-123">2.4 – 3.4</span></span>|
| <span data-ttu-id="d698d-124">omiserver</span><span class="sxs-lookup"><span data-stu-id="d698d-124">omiserver</span></span>| <span data-ttu-id="d698d-125">Açık Yönetim Altyapısı</span><span class="sxs-lookup"><span data-stu-id="d698d-125">Open Management Infrastructure</span></span>| <span data-ttu-id="d698d-126">1.0.8.1</span><span class="sxs-lookup"><span data-stu-id="d698d-126">1.0.8.1</span></span>|
| <span data-ttu-id="d698d-127">openssl</span><span class="sxs-lookup"><span data-stu-id="d698d-127">openssl</span></span>| <span data-ttu-id="d698d-128">OpenSSL kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="d698d-128">OpenSSL Libraries</span></span>| <span data-ttu-id="d698d-129">0.9.8 veya 1.0</span><span class="sxs-lookup"><span data-stu-id="d698d-129">0.9.8 or 1.0</span></span>|
| <span data-ttu-id="d698d-130">ctypes</span><span class="sxs-lookup"><span data-stu-id="d698d-130">ctypes</span></span>| <span data-ttu-id="d698d-131">Python CTypes kitaplığı</span><span class="sxs-lookup"><span data-stu-id="d698d-131">Python CTypes library</span></span>| <span data-ttu-id="d698d-132">Python sürümü ile eşleşmelidir</span><span class="sxs-lookup"><span data-stu-id="d698d-132">Must match Python version</span></span>|
| <span data-ttu-id="d698d-133">libcurl</span><span class="sxs-lookup"><span data-stu-id="d698d-133">libcurl</span></span>| <span data-ttu-id="d698d-134">cURL, http istemci kitaplığı</span><span class="sxs-lookup"><span data-stu-id="d698d-134">cURL http client library</span></span>| <span data-ttu-id="d698d-135">7.15.1</span><span class="sxs-lookup"><span data-stu-id="d698d-135">7.15.1</span></span>|

## <a name="installing-dsc-for-linux"></a><span data-ttu-id="d698d-136">Linux için DSC yükleme</span><span class="sxs-lookup"><span data-stu-id="d698d-136">Installing DSC for Linux</span></span>

<span data-ttu-id="d698d-137">Yüklemelisiniz [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi) Linux için DSC yüklemeden önce.</span><span class="sxs-lookup"><span data-stu-id="d698d-137">You must install the [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi) before installing DSC for Linux.</span></span>

### <a name="installing-omi"></a><span data-ttu-id="d698d-138">OMI yükleme</span><span class="sxs-lookup"><span data-stu-id="d698d-138">Installing OMI</span></span>

<span data-ttu-id="d698d-139">Sürüm 1.0.8.1 Open Management Infrastructure (OMI) CIM sunucusu Linux gerektirir Desired State Configuration veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="d698d-139">Desired State Configuration for Linux requires the Open Management Infrastructure (OMI) CIM server, version 1.0.8.1 or later.</span></span> <span data-ttu-id="d698d-140">OMI açık grubundan indirilebilir: [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi).</span><span class="sxs-lookup"><span data-stu-id="d698d-140">OMI can be downloaded from The Open Group: [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi).</span></span>

<span data-ttu-id="d698d-141">OMI yüklemek için Linux sistemine (.rpm veya .deb) ve OpenSSL sürümü (ssl_098 veya ssl_100) ve mimari (x64/x86) için uygun olan paketi yükleyin.</span><span class="sxs-lookup"><span data-stu-id="d698d-141">To install OMI, install the package that is appropriate for your Linux system (.rpm or .deb) and OpenSSL version (ssl_098 or ssl_100), and architecture (x64/x86).</span></span> <span data-ttu-id="d698d-142">RPM paketleri, CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server ve Oracle Linux için uygundur.</span><span class="sxs-lookup"><span data-stu-id="d698d-142">RPM packages are appropriate for CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server, and Oracle Linux.</span></span> <span data-ttu-id="d698d-143">DEB paketleri, Debian GNU/Linux ve Ubuntu Server için uygundur.</span><span class="sxs-lookup"><span data-stu-id="d698d-143">DEB packages are appropriate for Debian GNU/Linux and Ubuntu Server.</span></span> <span data-ttu-id="d698d-144">Ssl_098 paketleri OpenSSL 0.9.8 ssl_100 paketleri OpenSSL 1.0 yüklü bilgisayarlar için uygun olsa da yüklü olan bilgisayarlar için uygundur.</span><span class="sxs-lookup"><span data-stu-id="d698d-144">The ssl_098 packages are appropriate for computers with OpenSSL 0.9.8 installed while the ssl_100 packages are appropriate for computers with OpenSSL 1.0 installed.</span></span>

> [!NOTE]
> <span data-ttu-id="d698d-145">Yüklü olan bir OpenSSL sürümü belirlemek için komutu çalıştırmak `openssl version`.</span><span class="sxs-lookup"><span data-stu-id="d698d-145">To determine the installed OpenSSL version, run the command `openssl version`.</span></span>

<span data-ttu-id="d698d-146">OMI, bir CentOS 7 x64 sisteme yüklemek için aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d698d-146">Run the following command to install OMI on a CentOS 7 x64 system.</span></span>

`# sudo rpm -Uvh omiserver-1.0.8.ssl_100.rpm`

### <a name="installing-dsc"></a><span data-ttu-id="d698d-147">DSC yükleme</span><span class="sxs-lookup"><span data-stu-id="d698d-147">Installing DSC</span></span>

<span data-ttu-id="d698d-148">Linux için DSC indirilebilir [burada](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/tag/v1.1.1-294).</span><span class="sxs-lookup"><span data-stu-id="d698d-148">DSC for Linux is available for download [here](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/tag/v1.1.1-294).</span></span>

<span data-ttu-id="d698d-149">DSC yüklemek için Linux sistemine (.rpm veya .deb) ve OpenSSL sürümü (ssl_098 veya ssl_100) ve mimari (x64/x86) için uygun olan paketi yükleyin.</span><span class="sxs-lookup"><span data-stu-id="d698d-149">To install DSC, install the package that is appropriate for your Linux system (.rpm or .deb) and OpenSSL version (ssl_098 or ssl_100), and architecture (x64/x86).</span></span> <span data-ttu-id="d698d-150">RPM paketleri, CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server ve Oracle Linux için uygundur.</span><span class="sxs-lookup"><span data-stu-id="d698d-150">RPM packages are appropriate for CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server, and Oracle Linux.</span></span> <span data-ttu-id="d698d-151">DEB paketleri, Debian GNU/Linux ve Ubuntu Server için uygundur.</span><span class="sxs-lookup"><span data-stu-id="d698d-151">DEB packages are appropriate for Debian GNU/Linux and Ubuntu Server.</span></span> <span data-ttu-id="d698d-152">Ssl_098 paketleri OpenSSL 0.9.8 ssl_100 paketleri OpenSSL 1.0 yüklü bilgisayarlar için uygun olsa da yüklü olan bilgisayarlar için uygundur.</span><span class="sxs-lookup"><span data-stu-id="d698d-152">The ssl_098 packages are appropriate for computers with OpenSSL 0.9.8 installed while the ssl_100 packages are appropriate for computers with OpenSSL 1.0 installed.</span></span>

> [!NOTE]
> <span data-ttu-id="d698d-153">Yüklü olan bir OpenSSL sürümü belirlemek için komut openssl sürümü çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d698d-153">To determine the installed OpenSSL version, run the command openssl version.</span></span>

<span data-ttu-id="d698d-154">DSC, bir CentOS 7 x64 sisteme yüklemek için aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d698d-154">Run the following command to install DSC on a CentOS 7 x64 system.</span></span>

`# sudo rpm -Uvh dsc-1.0.0-254.ssl_100.x64.rpm`

## <a name="using-dsc-for-linux"></a><span data-ttu-id="d698d-155">Linux için DSC kullanma</span><span class="sxs-lookup"><span data-stu-id="d698d-155">Using DSC for Linux</span></span>

<span data-ttu-id="d698d-156">Aşağıdaki bölümlerde, oluşturma ve Linux bilgisayarlarda DSC yapılandırmaları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d698d-156">The following sections explain how to create and run DSC configurations on Linux computers.</span></span>

### <a name="creating-a-configuration-mof-document"></a><span data-ttu-id="d698d-157">Yapılandırma MOF belgesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="d698d-157">Creating a configuration MOF document</span></span>

<span data-ttu-id="d698d-158">Windows PowerShell yapılandırma anahtar sözcüğü, tıpkı Windows bilgisayarlar için Linux bilgisayarlar için bir yapılandırma oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d698d-158">The Windows PowerShell Configuration keyword is used to create a configuration for Linux computers, just like for Windows computers.</span></span> <span data-ttu-id="d698d-159">Aşağıdaki adımlar, Windows PowerShell kullanarak bir Linux bilgisayar için bir yapılandırma belgesi oluşturulmasını açıklar.</span><span class="sxs-lookup"><span data-stu-id="d698d-159">The following steps describe the creation of a configuration document for a Linux computer using Windows PowerShell.</span></span>

1. <span data-ttu-id="d698d-160">Nx modülünü içeri aktarın.</span><span class="sxs-lookup"><span data-stu-id="d698d-160">Import the nx module.</span></span> <span data-ttu-id="d698d-161">Nx Windows PowerShell modülünü şeması için yerleşik kaynaklar için DSC Linux için içerir ve yerel bilgisayarınıza yüklenmeli ve yapılandırmada içeri aktarıldı.</span><span class="sxs-lookup"><span data-stu-id="d698d-161">The nx Windows PowerShell module contains the schema for Built-In resources for DSC for Linux, and must be installed to your local computer and imported in the configuration.</span></span>

   - <span data-ttu-id="d698d-162">Nx modülünü yüklemek için nx modülü dizini ya da kopyalama `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` veya `$PSHOME\Modules`.</span><span class="sxs-lookup"><span data-stu-id="d698d-162">To install the nx module, copy the nx module directory to either `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` or `$PSHOME\Modules`.</span></span> <span data-ttu-id="d698d-163">Nx modülü DSC Linux yükleme paketinin (MSI) dahildir.</span><span class="sxs-lookup"><span data-stu-id="d698d-163">The nx module is included in the DSC for Linux installation package (MSI).</span></span> <span data-ttu-id="d698d-164">Yapılandırmanızda nx modülü içeri aktarmak için kullanın `Import-DSCResource` komutu:</span><span class="sxs-lookup"><span data-stu-id="d698d-164">To import the nx module in your configuration, use the `Import-DSCResource` command:</span></span>

   ```powershell
   Configuration ExampleConfiguration{

    Import-DSCResource -Module nx

   }
   ```

2. <span data-ttu-id="d698d-165">Bir yapılandırma tanımlama ve yapılandırma belgesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="d698d-165">Define a configuration and generate the configuration document:</span></span>

   ```powershell
   Configuration ExampleConfiguration
   {
        Import-DscResource -Module nx

        Node  "linuxhost.contoso.com"
        {
            nxFile ExampleFile 
            {
                DestinationPath = "/tmp/example"
                Contents = "hello world `n"
                Ensure = "Present"
                Type = "File"
            }
        }
   }

   ExampleConfiguration -OutputPath:"C:\temp"
   ```

### <a name="push-the-configuration-to-the-linux-computer"></a><span data-ttu-id="d698d-166">Yapılandırma Linux bilgisayar anında iletme</span><span class="sxs-lookup"><span data-stu-id="d698d-166">Push the configuration to the Linux computer</span></span>

<span data-ttu-id="d698d-167">Yapılandırma belgelerini (MOF dosyaları) gönderilen Linux bilgisayar kullanarak [Başlat-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Start-DscConfiguration) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="d698d-167">Configuration documents (MOF files) can be pushed to the Linux computer using the [Start-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Start-DscConfiguration) cmdlet.</span></span> <span data-ttu-id="d698d-168">Bu cmdlet ile birlikte kullanmak için [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration), veya [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) cmdlet'leri, uzaktan Linux bilgisayara bir CIMSession kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d698d-168">In order to use this cmdlet, along with the [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration), or [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) cmdlets, remotely to a Linux computer, you must use a CIMSession.</span></span> <span data-ttu-id="d698d-169">[New-CimSession](http://go.microsoft.com/fwlink/?LinkId=227967) cmdlet'i bir CIMSession Linux bilgisayarda oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d698d-169">The [New-CimSession](http://go.microsoft.com/fwlink/?LinkId=227967) cmdlet is used to create a CIMSession to the Linux computer.</span></span>

<span data-ttu-id="d698d-170">Aşağıdaki kod bir CIMSession DSC için Linux için oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d698d-170">The following code shows how to create a CIMSession for DSC for Linux.</span></span>

```powershell
$Node = "ostc-dsc-01"
$Credential = Get-Credential -UserName:"root" -Message:"Enter Password:"

#Ignore SSL certificate validation
#$opt = New-CimSessionOption -UseSsl:$true -SkipCACheck:$true -SkipCNCheck:$true -SkipRevocationCheck:$true

#Options for a trusted SSL certificate
$opt = New-CimSessionOption -UseSsl:$true
$Sess=New-CimSession -Credential:$credential -ComputerName:$Node -Port:5986 -Authentication:basic -SessionOption:$opt -OperationTimeoutSec:90
```

> [!NOTE]
> <span data-ttu-id="d698d-171">"Gönderme" modu için kullanıcı kimlik bilgilerini Linux bilgisayarında kök kullanıcı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d698d-171">For “Push” mode, the user credential must be the root user on the Linux computer.</span></span>
> <span data-ttu-id="d698d-172">Yalnızca SSL/TLS bağlantılarını DSC için Linux için desteklenen `New-CimSession` $true olarak ayarlayın: UseSSL parametresi ile birlikte kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d698d-172">Only SSL/TLS connections are supported for DSC for Linux, the `New-CimSession` must be used with the –UseSSL parameter set to $true.</span></span>
> <span data-ttu-id="d698d-173">(DSC için) OMI tarafından kullanılan SSL sertifikasını dosyasında belirtilen: `/opt/omi/etc/omiserver.conf` özelliklere sahip: pemfile ve keyfile.</span><span class="sxs-lookup"><span data-stu-id="d698d-173">The SSL certificate used by OMI (for DSC) is specified in the file: `/opt/omi/etc/omiserver.conf` with the properties: pemfile and keyfile.</span></span>
> <span data-ttu-id="d698d-174">Bu sertifika, çalıştırmakta olduğunuz Windows bilgisayar tarafından güvenilir değilse [New-CimSession](http://go.microsoft.com/fwlink/?LinkId=227967) cmdlet'i üzerinde tercih edebilirsiniz sertifika doğrulama CIMSession seçeneklerle yoksay: `-SkipCACheck:$true -SkipCNCheck:$true -SkipRevocationCheck:$true`</span><span class="sxs-lookup"><span data-stu-id="d698d-174">If this certificate is not trusted by the Windows computer that you are running the [New-CimSession](http://go.microsoft.com/fwlink/?LinkId=227967) cmdlet on, you can choose to ignore certificate validation with the CIMSession Options: `-SkipCACheck:$true -SkipCNCheck:$true -SkipRevocationCheck:$true`</span></span>

<span data-ttu-id="d698d-175">DSC yapılandırması Linux düğüme göndermek için aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d698d-175">Run the following command to push the DSC configuration to the Linux node.</span></span>

`Start-DscConfiguration -Path:"C:\temp" -CimSession:$Sess -Wait -Verbose`

### <a name="distribute-the-configuration-with-a-pull-server"></a><span data-ttu-id="d698d-176">Bir çekme sunucusu yapılandırmasıyla dağıtın</span><span class="sxs-lookup"><span data-stu-id="d698d-176">Distribute the configuration with a pull server</span></span>

<span data-ttu-id="d698d-177">Yapılandırmaları bir çekme sunucusu ile bir Linux bilgisayar gibi Windows bilgisayarlar için dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="d698d-177">Configurations can be distributed to a Linux computer with a pull server, just like for Windows computers.</span></span> <span data-ttu-id="d698d-178">Bir çekme sunucusu kullanma ile ilgili yönergeler için bkz [Windows PowerShell Desired State Configuration çekme sunucuları](pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="d698d-178">For guidance on using a pull server, see [Windows PowerShell Desired State Configuration Pull Servers](pullServer.md).</span></span> <span data-ttu-id="d698d-179">Ek bilgi ve Linux bilgisayarları bir çekme sunucusu kullanmaya ilişkin sınırlamalar için sürüm notları için Linux Desired State Configuration ' için bkz.</span><span class="sxs-lookup"><span data-stu-id="d698d-179">For additional information and limitations related to using Linux computers with a pull server, see the Release Notes for Desired State Configuration for Linux.</span></span>

### <a name="working-with-configurations-locally"></a><span data-ttu-id="d698d-180">Yerel olarak yapılandırmaları ile çalışma</span><span class="sxs-lookup"><span data-stu-id="d698d-180">Working with configurations locally</span></span>

<span data-ttu-id="d698d-181">Linux için DSC yapılandırması yerel Linux bilgisayardan çalışmak için komut dosyalarını içerir.</span><span class="sxs-lookup"><span data-stu-id="d698d-181">DSC for Linux includes scripts to work with configuration from the local Linux computer.</span></span> <span data-ttu-id="d698d-182">Olan bu betikler bulun `/opt/microsoft/dsc/Scripts` ve şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="d698d-182">These scripts are locate in `/opt/microsoft/dsc/Scripts` and include the following:</span></span>

- <span data-ttu-id="d698d-183">GetDscConfiguration.py</span><span class="sxs-lookup"><span data-stu-id="d698d-183">GetDscConfiguration.py</span></span>

<span data-ttu-id="d698d-184">Bilgisayara uygulanan geçerli yapılandırmasını döndürür.</span><span class="sxs-lookup"><span data-stu-id="d698d-184">Returns the current configuration applied to the computer.</span></span> <span data-ttu-id="d698d-185">Windows PowerShell cmdlet'i için benzer `Get-DscConfiguration` cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="d698d-185">Similar to the Windows PowerShell cmdlet `Get-DscConfiguration` cmdlet.</span></span>

`# sudo ./GetDscConfiguration.py`

- <span data-ttu-id="d698d-186">GetDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="d698d-186">GetDscLocalConfigurationManager.py</span></span>

<span data-ttu-id="d698d-187">Bilgisayara uygulanan geçerli meta yapılandırmasını döndürür.</span><span class="sxs-lookup"><span data-stu-id="d698d-187">Returns the current meta-configuration applied to the computer.</span></span> <span data-ttu-id="d698d-188">Cmdlet'e benzer [Get-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="d698d-188">Similar to the cmdlet [Get-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) cmdlet.</span></span>

`# sudo ./GetDscLocalConfigurationManager.py`

- <span data-ttu-id="d698d-189">InstallModule.py</span><span class="sxs-lookup"><span data-stu-id="d698d-189">InstallModule.py</span></span>

<span data-ttu-id="d698d-190">Özel bir DSC kaynağı modülünü yükler.</span><span class="sxs-lookup"><span data-stu-id="d698d-190">Installs a custom DSC resource module.</span></span> <span data-ttu-id="d698d-191">Modül paylaşılan nesne kitaplığı içeren bir .zip dosyası ve şema MOF dosya yolunu gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d698d-191">Requires the path to a .zip file containing the module shared object library and schema MOF files.</span></span>

`# sudo ./InstallModule.py /tmp/cnx_Resource.zip`

- <span data-ttu-id="d698d-192">RemoveModule.py</span><span class="sxs-lookup"><span data-stu-id="d698d-192">RemoveModule.py</span></span>

<span data-ttu-id="d698d-193">Özel bir DSC kaynak modülü kaldırır.</span><span class="sxs-lookup"><span data-stu-id="d698d-193">Removes a custom DSC resource module.</span></span> <span data-ttu-id="d698d-194">Kaldırmak için modülünün adı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d698d-194">Requires the name of the module to remove.</span></span>

`# sudo ./RemoveModule.py cnx_Resource`

- <span data-ttu-id="d698d-195">StartDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="d698d-195">StartDscLocalConfigurationManager.py</span></span>

<span data-ttu-id="d698d-196">Yapılandırma MOF dosyasının bilgisayara uygulanır.</span><span class="sxs-lookup"><span data-stu-id="d698d-196">Applies a configuration MOF file to the computer.</span></span> <span data-ttu-id="d698d-197">Benzer şekilde [Başlat-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Start-DscConfiguration) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="d698d-197">Similar to the [Start-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Start-DscConfiguration) cmdlet.</span></span> <span data-ttu-id="d698d-198">' % S'yapılandırması uygulamak için MOF yolu gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d698d-198">Requires the path to the configuration MOF to apply.</span></span>

`# sudo ./StartDscLocalConfigurationManager.py –configurationmof /tmp/localhost.mof`

- <span data-ttu-id="d698d-199">SetDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="d698d-199">SetDscLocalConfigurationManager.py</span></span>

<span data-ttu-id="d698d-200">Bir Meta yapılandırma MOF dosyasının bilgisayara uygulanır.</span><span class="sxs-lookup"><span data-stu-id="d698d-200">Applies a Meta Configuration MOF file to the computer.</span></span> <span data-ttu-id="d698d-201">Benzer şekilde [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="d698d-201">Similar to the [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) cmdlet.</span></span> <span data-ttu-id="d698d-202">Uygulanacak Meta yapılandırma MOF yolu gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d698d-202">Requires the path to the Meta Configuration MOF to apply.</span></span>

`# sudo ./SetDscLocalConfigurationManager.py –configurationmof /tmp/localhost.meta.mof`

## <a name="powershell-desired-state-configuration-for-linux-log-files"></a><span data-ttu-id="d698d-203">Linux günlük dosyaları için PowerShell Desired State Configuration</span><span class="sxs-lookup"><span data-stu-id="d698d-203">PowerShell Desired State Configuration for Linux Log Files</span></span>

<span data-ttu-id="d698d-204">Aşağıdaki günlük dosyaları için DSC Linux iletileri üretilir.</span><span class="sxs-lookup"><span data-stu-id="d698d-204">The following log files are generated for DSC for Linux messages.</span></span>

|<span data-ttu-id="d698d-205">Günlük dosyası</span><span class="sxs-lookup"><span data-stu-id="d698d-205">Log file</span></span>|<span data-ttu-id="d698d-206">Dizin</span><span class="sxs-lookup"><span data-stu-id="d698d-206">Directory</span></span>|<span data-ttu-id="d698d-207">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d698d-207">Description</span></span>|
|---|---|---|
|<span data-ttu-id="d698d-208">**omiserver.log**</span><span class="sxs-lookup"><span data-stu-id="d698d-208">**omiserver.log**</span></span>|`/var/opt/omi/log`|<span data-ttu-id="d698d-209">OMI CIM sunucusu işlemi için ilgili iletiler.</span><span class="sxs-lookup"><span data-stu-id="d698d-209">Messages relating to the operation of the OMI CIM server.</span></span>|
|<span data-ttu-id="d698d-210">**DSC.log**</span><span class="sxs-lookup"><span data-stu-id="d698d-210">**dsc.log**</span></span>|`/var/opt/omi/log`|<span data-ttu-id="d698d-211">Yerel Configuration Manager'ı (LCM) ve DSC kaynak işlemleri çalışması için ilgili iletiler.</span><span class="sxs-lookup"><span data-stu-id="d698d-211">Messages relating to the operation of the Local Configuration Manager (LCM) and DSC resource operations.</span></span>|