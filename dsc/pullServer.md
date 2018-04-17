---
ms.date: 04/11/2018
ms.topic: conceptual
keywords: DSC, powershell, yapılandırma, Kur
title: DSC Çekme Hizmeti
ms.openlocfilehash: 61b4c0e9cfe1d1d7539cd32da35d2fe50da4b0e3
ms.sourcegitcommit: ece1794c94be4880a2af5a2605ed4721593643b6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
---
# <a name="desired-state-configuration-pull-service"></a><span data-ttu-id="7650d-103">İstenen durum yapılandırma çekme hizmeti</span><span class="sxs-lookup"><span data-stu-id="7650d-103">Desired State Configuration Pull Service</span></span>

> <span data-ttu-id="7650d-104">İçin geçerlidir: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="7650d-104">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7650d-105">Çekme sunucusuna (Windows özelliği *DSC hizmet*) vardır ancak desteklenen bir bileşen Windows Server'ın yeni özellikleri veya yetenekleri sunmak için herhangi bir plan vardır.</span><span class="sxs-lookup"><span data-stu-id="7650d-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="7650d-106">Geçiş başlamak için önerilen yönetilen istemcilere [Azure Otomasyonu DSC](/azure/automation/automation-dsc-getting-started) (Windows Server çekme sunucusunda ötesinde özellikler içerir) veya topluluk çözümlerden birini listelenen [burada](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="7650d-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="7650d-107">Yerel Configuration Manager, bir çekme hizmet çözümü tarafından merkezi olarak yönetilebilir.</span><span class="sxs-lookup"><span data-stu-id="7650d-107">Local Configuration Manager can be centrally managed by a Pull Service solution.</span></span>
<span data-ttu-id="7650d-108">Bu yaklaşımı kullanarak, yönetilmekte olan düğüm bir hizmete kayıtlı ve yapılandırma LCM'yi ayarlarında atanmış.</span><span class="sxs-lookup"><span data-stu-id="7650d-108">When using this approach, the node that is being managed is registered with a service and assigned a configuration in LCM settings.</span></span>
<span data-ttu-id="7650d-109">Yapılandırma ve bağımlılık yapılandırması için gereken tüm DSC kaynakları makineye indirilir ve yapılandırmasını yönetmek için LCM'yi tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7650d-109">The configuration and all DSC resources needed as dependencies for the configuration are downloaded to the machine and used by LCM to manage the configuration.</span></span>
<span data-ttu-id="7650d-110">Yönetilen makinenin durumu hakkında bilgi, hizmet raporlama için yüklenir.</span><span class="sxs-lookup"><span data-stu-id="7650d-110">Information about the state of the machine being managed is uploaded to the service for reporting.</span></span>
<span data-ttu-id="7650d-111">Bu kavram "çekme hizmeti." olarak adlandırılır</span><span class="sxs-lookup"><span data-stu-id="7650d-111">This concept is referred to as "pull service."</span></span>

<span data-ttu-id="7650d-112">Çekme Hizmeti için geçerli seçenekler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="7650d-112">The current options for pull service include:</span></span>

- <span data-ttu-id="7650d-113">Azure Otomasyonu istenen durum Yapılandırma hizmeti</span><span class="sxs-lookup"><span data-stu-id="7650d-113">Azure Automation Desired State Configuration service</span></span>
- <span data-ttu-id="7650d-114">Windows Server'da çalışan bir çekme hizmeti</span><span class="sxs-lookup"><span data-stu-id="7650d-114">A pull service running on Windows Server</span></span>
- <span data-ttu-id="7650d-115">Açık kaynak çözümleri tutulan topluluk</span><span class="sxs-lookup"><span data-stu-id="7650d-115">Community maintained open-source solutions</span></span>
- <span data-ttu-id="7650d-116">SMB paylaşımı</span><span class="sxs-lookup"><span data-stu-id="7650d-116">An SMB share</span></span>

<span data-ttu-id="7650d-117">**Önerilen Çözüm**, ve en çok kullanılabilir olan özellikleri seçeneğiyle [Azure Otomasyonu DSC](/azure/automation/automation-dsc-getting-started).</span><span class="sxs-lookup"><span data-stu-id="7650d-117">**The recommended solution**, and the option with the most features available, is [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span></span>

<span data-ttu-id="7650d-118">Azure hizmet düğümleri şirket içi özel veri merkezleri veya genel Bulutlar Azure ve AWS gibi yönetebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7650d-118">The Azure service can manage nodes on-premises in private datacenters, or in public clouds such as Azure and AWS.</span></span>
<span data-ttu-id="7650d-119">Burada sunucuları doğrudan bağlanamıyor Internet'e özel ortamları için yalnızca yayımlanan Azure IP aralığına giden trafiği kullanabilirsiniz (bkz [Azure veri merkezi IP aralıkları](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).</span><span class="sxs-lookup"><span data-stu-id="7650d-119">For private environments where servers cannot directly connect to the Internet, consider limiting outbound traffic to only the published Azure IP range (see [Azure Datacenter IP Ranges](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).</span></span>

<span data-ttu-id="7650d-120">Şu anda Windows Server'da çekme Hizmet kullanılamıyor çevrimiçi hizmet özelliklerini içerir:</span><span class="sxs-lookup"><span data-stu-id="7650d-120">Features of the online service that are not currently available in the pull service on Windows Server include:</span></span>
- <span data-ttu-id="7650d-121">Yoldaki ve bekleyen tüm veriler şifrelenir</span><span class="sxs-lookup"><span data-stu-id="7650d-121">All data is encrypted in transit and at rest</span></span>
- <span data-ttu-id="7650d-122">İstemci sertifikalarını oluşturulur ve otomatik olarak yönetilir</span><span class="sxs-lookup"><span data-stu-id="7650d-122">Client certificates are created and managed automatically</span></span>
- <span data-ttu-id="7650d-123">Parolaları depolamak merkezi olarak yönetmek için [parolaları/kimlik bilgilerinin](/azure/automation/automation-credentials), veya [değişkenleri](/azure/automation/automation-variables) sunucu adlarını veya bağlantı dizeleri gibi</span><span class="sxs-lookup"><span data-stu-id="7650d-123">Secrets store for centrally managing [passwords/credentials](/azure/automation/automation-credentials), or [variables](/azure/automation/automation-variables) such as server names or connection strings</span></span>
- <span data-ttu-id="7650d-124">Düğüm merkezi olarak yönetmenize [LCM'yi yapılandırma](metaConfig.md#basic-settings)</span><span class="sxs-lookup"><span data-stu-id="7650d-124">Centrally manage node [LCM configuration](metaConfig.md#basic-settings)</span></span>
- <span data-ttu-id="7650d-125">Merkezi olarak istemci düğümlerine yapılandırmalar atama</span><span class="sxs-lookup"><span data-stu-id="7650d-125">Centrally assign configurations to client nodes</span></span>
- <span data-ttu-id="7650d-126">Üretim ulaşmadan önce test etmek için "yalancı gruplarına" yayın yapılandırma değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="7650d-126">Release configuration changes to "canary groups" for testing before reaching production</span></span>
- <span data-ttu-id="7650d-127">Grafik raporlama</span><span class="sxs-lookup"><span data-stu-id="7650d-127">Graphical reporting</span></span>
  - <span data-ttu-id="7650d-128">Ayrıntı düzeyi DSC kaynağı düzeyinde durumu ayrıntısı</span><span class="sxs-lookup"><span data-stu-id="7650d-128">Status detail at the DSC resource level of granularity</span></span>
  - <span data-ttu-id="7650d-129">Sorun giderme için istemci makinelerden ayrıntılı hata iletileri</span><span class="sxs-lookup"><span data-stu-id="7650d-129">Verbose error messages from client machines for troubleshooting</span></span>
- <span data-ttu-id="7650d-130">[Azure günlük analizi ile tümleştirme](/azure/automation/automation-dsc-diagnostics) , otomatik görevler, raporlama ve Uyarılar için Android/iOS uygulaması uyarı verme</span><span class="sxs-lookup"><span data-stu-id="7650d-130">[Integration with Azure Log Analytics](/azure/automation/automation-dsc-diagnostics) for alerting, automated tasks, Android/iOS app for reporting and alerting</span></span>

## <a name="dsc-pull-service-in-windows-server"></a><span data-ttu-id="7650d-131">Windows Server'daki DSC çekme hizmeti</span><span class="sxs-lookup"><span data-stu-id="7650d-131">DSC pull service in Windows Server</span></span>

<span data-ttu-id="7650d-132">Bir çekme hizmetini Windows Server üzerinde çalışacak şekilde yapılandırmak için mümkündür.</span><span class="sxs-lookup"><span data-stu-id="7650d-132">It is possible to configuring a pull service to run on Windows Server.</span></span>
<span data-ttu-id="7650d-133">Windows Server'da bulunan çekme hizmet çözümünü yapılandırmaları/modüllerini yüklemek için depolama ve veritabanı için rapor verileri yakalama yalnızca yetenekleri içerir dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="7650d-133">Be advised that the pull service solution included in Windows Server includes only capabilities of storing configurations/modules for download and capturing report data in to database.</span></span>
<span data-ttu-id="7650d-134">Çoğu Azure hizmeti tarafından sunulan yetenekleri içermez ve bu nedenle nasıl hizmeti kullanılan değerlendirmek için iyi bir aracı değildir.</span><span class="sxs-lookup"><span data-stu-id="7650d-134">It does not include many of the capabilities offered by the service in Azure and so is not a good tool for evaluating how the service would be used.</span></span>

<span data-ttu-id="7650d-135">Windows Server'da sunulan çekme hizmeti düğümleri için söylediğinizde DSC yapılandırma dosyalarını hedef düğümleri kullanılabilir hale getirmek için bir OData arabirimi kullanır IIS'de bir web hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="7650d-135">The pull service offered in Windows Server is a web service in IIS that uses an OData interface to make DSC configuration files available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="7650d-136">Bir çekme sunucusuna kullanmak için gereksinimler:</span><span class="sxs-lookup"><span data-stu-id="7650d-136">Requirements for using a pull server:</span></span>

- <span data-ttu-id="7650d-137">Çalıştıran bir sunucuda:</span><span class="sxs-lookup"><span data-stu-id="7650d-137">A server running:</span></span>
  - <span data-ttu-id="7650d-138">WMF/PowerShell 5.0 veya daha büyük</span><span class="sxs-lookup"><span data-stu-id="7650d-138">WMF/PowerShell 5.0 or greater</span></span>
  - <span data-ttu-id="7650d-139">IIS sunucu rolü</span><span class="sxs-lookup"><span data-stu-id="7650d-139">IIS server role</span></span>
  - <span data-ttu-id="7650d-140">DSC hizmeti</span><span class="sxs-lookup"><span data-stu-id="7650d-140">DSC Service</span></span>
- <span data-ttu-id="7650d-141">İdeal olarak, bazı anlamına gelir bir sertifika oluşturma hedef düğümlerine yerel Configuration Manager (LCM'yi) için geçirilen kimlik bilgileri güvenli hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="7650d-141">Ideally, some means of generating a certificate, to secure credentials passed to the Local Configuration Manager (LCM) on target nodes</span></span>

<span data-ttu-id="7650d-142">Windows Server ana bilgisayar çekme hizmetini yapılandırmak için en iyi yolu, DSC yapılandırması kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="7650d-142">The best way to configure Windows Server to host pull service is to use a DSC configuration.</span></span>
<span data-ttu-id="7650d-143">Bir örnek komut dosyası aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7650d-143">An example script is provided below.</span></span>

### <a name="supported-database-systems"></a><span data-ttu-id="7650d-144">Desteklenen veritabanı sistemleri</span><span class="sxs-lookup"><span data-stu-id="7650d-144">Supported database systems</span></span>

|<span data-ttu-id="7650d-145">WMF 4.0</span><span class="sxs-lookup"><span data-stu-id="7650d-145">WMF 4.0</span></span>   |<span data-ttu-id="7650d-146">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="7650d-146">WMF 5.0</span></span>  |<span data-ttu-id="7650d-147">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="7650d-147">WMF 5.1</span></span> |<span data-ttu-id="7650d-148">WMF 5.1 (Windows Server Insider Önizleme 17090)</span><span class="sxs-lookup"><span data-stu-id="7650d-148">WMF 5.1 (Windows Server Insider Preview 17090)</span></span>|
|---------|---------|---------|---------|
|<span data-ttu-id="7650d-149">MDB</span><span class="sxs-lookup"><span data-stu-id="7650d-149">MDB</span></span>     |<span data-ttu-id="7650d-150">ESENT (varsayılan), MDB</span><span class="sxs-lookup"><span data-stu-id="7650d-150">ESENT (Default), MDB</span></span> |<span data-ttu-id="7650d-151">ESENT (varsayılan), MDB</span><span class="sxs-lookup"><span data-stu-id="7650d-151">ESENT (Default), MDB</span></span>|<span data-ttu-id="7650d-152">ESENT (varsayılan), SQL Server'ı MDB</span><span class="sxs-lookup"><span data-stu-id="7650d-152">ESENT (Default), SQL Server, MDB</span></span>

<span data-ttu-id="7650d-153">İtibariyle, 17090 sürüm [Windows Server Insider Önizleme](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewserver), SQL Server, çekme hizmeti için desteklenen bir seçenek (Windows özelliği *DSC hizmet*).</span><span class="sxs-lookup"><span data-stu-id="7650d-153">Starting in release 17090 of [Windows Server Insider Preview](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewserver), SQL Server is a supported option for the Pull Service (Windows Feature *DSC-Service*).</span></span>  <span data-ttu-id="7650d-154">Bunun için geçirilen değil büyük DSC ortamları ölçeklendirmeye yönelik yeni bir seçenek sağlar [Azure Otomasyonu DSC](/azure/automation/automation-dsc-getting-started).</span><span class="sxs-lookup"><span data-stu-id="7650d-154">This provides a new option for scaling large DSC environments that have not migrated to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span></span>

> <span data-ttu-id="7650d-155">**Not**: SQL Server desteği önceki sürümler için WMF 5.1 (veya öncesi) eklenmez ve yalnızca Windows Server sürümlerinde büyük veya ona eşit 17090 için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7650d-155">**Note**: SQL Server support will not be added to previous versions of WMF 5.1 (or earlier) and will only be available on Windows Server versions greater than or equal to 17090.</span></span>

<span data-ttu-id="7650d-156">Çekme sunucusunu SQL Server kullanacak biçimde yapılandırmak için ayarlayın **SqlProvider** için `$true` ve **SqlConnectionString** geçerli bir SQL Server bağlantı dizesi.</span><span class="sxs-lookup"><span data-stu-id="7650d-156">To configure the pull server to use SQL Server, set **SqlProvider** to `$true` and **SqlConnectionString** to a valid SQL Server Connection String.</span></span>  <span data-ttu-id="7650d-157">Daha fazla bilgi için bkz: [SqlClient bağlantı dizeleri](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings).</span><span class="sxs-lookup"><span data-stu-id="7650d-157">For more information, see [SqlClient Connection Strings](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings).</span></span>
<span data-ttu-id="7650d-158">Bir örnek için SQL Server yapılandırma ile **xDscWebService**, öncelikle [xDscWebService kaynağı kullanan](#using-the-xdscwebservice-resource) ve daha sonra gözden [Sample_xDscWebServiceRegistration_ Github'da UseSQLProvider.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1).</span><span class="sxs-lookup"><span data-stu-id="7650d-158">For an example of SQL Server configuration with **xDscWebService**, first read [Using the xDscWebService resource](#using-the-xdscwebservice-resource) and then review [Sample_xDscWebServiceRegistration_UseSQLProvider.ps1 on GitHub](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1).</span></span>

### <a name="using-the-xdscwebservice-resource"></a><span data-ttu-id="7650d-159">XDscWebService kaynak kullanma</span><span class="sxs-lookup"><span data-stu-id="7650d-159">Using the xDscWebService resource</span></span>

<span data-ttu-id="7650d-160">Bir web çekme sunucusu kurmak için en kolay yolu kullanmaktır **xDscWebService** dahil kaynak **xPSDesiredStateConfiguration** modülü.</span><span class="sxs-lookup"><span data-stu-id="7650d-160">The easiest way to set up a web pull server is to use the **xDscWebService** resource, included in the **xPSDesiredStateConfiguration** module.</span></span>
<span data-ttu-id="7650d-161">Aşağıdaki adımları, kaynak web hizmeti oluşturan ayarlar bir yapılandırmada kullanmak açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7650d-161">The following steps explain how to use the resource in a configuration that sets up the web service.</span></span>

1. <span data-ttu-id="7650d-162">Çağrı [yükleme-Module](/powershell/module/PowershellGet/Install-Module) yüklemek için cmdlet'i **xPSDesiredStateConfiguration** modülü.</span><span class="sxs-lookup"><span data-stu-id="7650d-162">Call the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to install the **xPSDesiredStateConfiguration** module.</span></span> <span data-ttu-id="7650d-163">**Not**: **yükleme-Module** dahil **PowerShellGet** PowerShell 5. 0 ' dahil modülü.</span><span class="sxs-lookup"><span data-stu-id="7650d-163">**Note**: **Install-Module** is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="7650d-164">İndirebilirsiniz **PowerShellGet** için modülü PowerShell 3.0 ve 4.0 en [PackageManagement PowerShell modülleri Önizleme](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span><span class="sxs-lookup"><span data-stu-id="7650d-164">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span>
1. <span data-ttu-id="7650d-165">Bir güvenilen sertifika yetkilisi, kuruluşunuz ya da bir ortak yetkilisinden içinde ya da DSC çekme sunucusu için bir SSL sertifikası alın.</span><span class="sxs-lookup"><span data-stu-id="7650d-165">Get an SSL certificate for the DSC Pull server from a trusted Certificate Authority, either within your organization or a public authority.</span></span> <span data-ttu-id="7650d-166">Yetkilisinden alınan sertifika genellikle PFX biçimindedir.</span><span class="sxs-lookup"><span data-stu-id="7650d-166">The certificate received from the authority is usually in the PFX format.</span></span> <span data-ttu-id="7650d-167">DSC çekme sunucusuna CERT: \LocalMachine\My olmalıdır varsayılan konumda olacak düğüm üzerinde sertifikayı yükleyin.</span><span class="sxs-lookup"><span data-stu-id="7650d-167">Install the certificate on the node that will become the DSC Pull server in the default location, which should be CERT:\LocalMachine\My.</span></span> <span data-ttu-id="7650d-168">Sertifika parmak izini not edin.</span><span class="sxs-lookup"><span data-stu-id="7650d-168">Make a note of the certificate thumbprint.</span></span>
1. <span data-ttu-id="7650d-169">Kayıt anahtarı olarak kullanılacak bir GUID seçin.</span><span class="sxs-lookup"><span data-stu-id="7650d-169">Select a GUID to be used as the Registration Key.</span></span> <span data-ttu-id="7650d-170">Bir oluşturmak için PowerShell kullanarak PS istemine aşağıdakileri girin ve ENTER tuşuna basın: '``` [guid]::newGuid()```'veya'```New-Guid```'.</span><span class="sxs-lookup"><span data-stu-id="7650d-170">To generate one using PowerShell enter the following at the PS prompt and press enter: '``` [guid]::newGuid()```' or '```New-Guid```'.</span></span> <span data-ttu-id="7650d-171">Bu anahtar istemci düğümleri tarafından kayıt sırasında kimlik doğrulaması için paylaşılan bir anahtar olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7650d-171">This key will be used by client nodes as a shared key to authenticate during registration.</span></span> <span data-ttu-id="7650d-172">Daha fazla bilgi için aşağıdaki kayıt anahtarı bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="7650d-172">For more information, see the Registration Key section below.</span></span>
1. <span data-ttu-id="7650d-173">PowerShell ISE aşağıdaki yapılandırma komut dosyası (F5) başlatın (örnekler klasöründe bulunan **xPSDesiredStateConfiguration** modülü Sample_xDscWebServiceRegistration.ps1 olarak).</span><span class="sxs-lookup"><span data-stu-id="7650d-173">In the PowerShell ISE, start (F5) the following configuration script (included in the Examples folder of the  **xPSDesiredStateConfiguration** module as Sample_xDscWebServiceRegistration.ps1).</span></span> <span data-ttu-id="7650d-174">Bu komut çekme sunucusunda ayarlar.</span><span class="sxs-lookup"><span data-stu-id="7650d-174">This script sets up the pull server.</span></span>

```powershell
configuration Sample_xDscWebServiceRegistration
{
    param
    (
        [string[]]$NodeName = 'localhost',

        [ValidateNotNullOrEmpty()]
        [string] $certificateThumbPrint,

        [Parameter(HelpMessage='This should be a string with enough entropy (randomness) to protect the registration of clients to the pull server.  We will use new GUID by default.')]
        [ValidateNotNullOrEmpty()]
        [string] $RegistrationKey   # A guid that clients use to initiate conversation with pull server
    )

    Import-DSCResource -ModuleName xPSDesiredStateConfiguration

    Node $NodeName
    {
        WindowsFeature DSCServiceFeature
        {
            Ensure = "Present"
            Name   = "DSC-Service"
        }

        xDscWebService PSDSCPullServer
        {
            Ensure                  = "Present"
            EndpointName            = "PSDSCPullServer"
            Port                    = 8080
            PhysicalPath            = "$env:SystemDrive\inetpub\PSDSCPullServer"
            CertificateThumbPrint   = $certificateThumbPrint
            ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
            ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
            State                   = "Started"
            DependsOn               = "[WindowsFeature]DSCServiceFeature"
            RegistrationKeyPath     = "$env:PROGRAMFILES\WindowsPowerShell\DscService"
            AcceptSelfSignedCertificates = $true
            Enable32BitAppOnWin64   = $false
        }

        File RegistrationKeyFile
        {
            Ensure          = 'Present'
            Type            = 'File'
            DestinationPath = "$env:ProgramFiles\WindowsPowerShell\DscService\RegistrationKeys.txt"
            Contents        = $RegistrationKey
        }
    }
}
```

1. <span data-ttu-id="7650d-175">Sertifikanın parmak izi SSL geçirme yapılandırmayı çalıştırın **certificateThumbPrint** parametre ve bir GUID kayıt anahtarı olarak **RegistrationKey** parametre:</span><span class="sxs-lookup"><span data-stu-id="7650d-175">Run the configuration, passing the thumbprint of the SSL certificate as the **certificateThumbPrint** parameter and a GUID registration key as the **RegistrationKey** parameter:</span></span>

```powershell
# To find the Thumbprint for an installed SSL certificate for use with the pull server list all certificates in your local store
# and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
dir Cert:\LocalMachine\my

# Then include this thumbprint when running the configuration
Sample_xDSCPullServer -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutputPath c:\Configs\PullServer

# Run the compiled configuration to make the target node a DSC Pull Server
Start-DscConfiguration -Path c:\Configs\PullServer -Wait -Verbose
```

#### <a name="registration-key"></a><span data-ttu-id="7650d-176">Kayıt anahtarı</span><span class="sxs-lookup"><span data-stu-id="7650d-176">Registration Key</span></span>

<span data-ttu-id="7650d-177">İstemci yapılandırması kimliği yerine yapılandırma adları kullanabilmeleri sunucusu ile kayıt düğümleri izin vermek için yukarıdaki yapılandırması tarafından oluşturulan bir kayıt anahtarı adlı bir dosyaya kaydedilir `RegistrationKeys.txt` içinde `C:\Program Files\WindowsPowerShell\DscService`.</span><span class="sxs-lookup"><span data-stu-id="7650d-177">To allow client nodes to register with the server so that they can use configuration names instead of a configuration ID, a registration key that was created by the above configuration is saved in a file named `RegistrationKeys.txt` in `C:\Program Files\WindowsPowerShell\DscService`.</span></span> <span data-ttu-id="7650d-178">Kayıt anahtarını ilk kaydı sırasında çekme sunucu ile istemci tarafından kullanılan bir paylaşılan gizlilik olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="7650d-178">The registration key functions as a shared secret used during the initial registration by the client with the pull server.</span></span> <span data-ttu-id="7650d-179">İstemci kayıt başarıyla tamamlandıktan sonra çekme sunucusuna benzersiz kimliğini doğrulamak için kullanılan otomatik olarak imzalanan bir sertifika oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7650d-179">The client will generate a self-signed certificate that is used to uniquely authenticate to the pull server once registration is successfully completed.</span></span> <span data-ttu-id="7650d-180">Bu sertifikanın parmak izini yerel olarak depolanır ve çekme sunucu URL'si ile ilişkili.</span><span class="sxs-lookup"><span data-stu-id="7650d-180">The thumbprint of this certificate is stored locally and associated with the URL of the pull server.</span></span>
> <span data-ttu-id="7650d-181">**Not**: Kayıt anahtarlarını PowerShell 4. 0'desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="7650d-181">**Note**: Registration keys are not supported in PowerShell 4.0.</span></span>

<span data-ttu-id="7650d-182">Çekme sunucunun kimliğini doğrulamak için bir düğümü yapılandırmak için kayıt anahtarını bu çekme Server'a kaydettirirken herhangi bir hedef düğümün meta yapılandırmasını olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="7650d-182">In order to configure a node to authenticate with the pull server, the registration key needs to be in the metaconfiguration for any target node that will be registering with this pull server.</span></span> <span data-ttu-id="7650d-183">Unutmayın **RegistrationKey** meta yapılandırmasını içinde aşağıdaki hedef makine başarılı bir şekilde kaydettirildi ve '140a952b-b9d6-406b-b416-e0f759c9c0e4' değeri depolanan değeriyle eşleşmelidir sonra kaldırılır. Çekme sunucusunda RegistrationKeys.txt dosyası.</span><span class="sxs-lookup"><span data-stu-id="7650d-183">Note that the **RegistrationKey** in the metaconfiguration below is removed after the target machine has successfully registered, and that the value '140a952b-b9d6-406b-b416-e0f759c9c0e4' must match the value stored in the RegistrationKeys.txt file on the pull server.</span></span> <span data-ttu-id="7650d-184">Her zaman farkında çekme sunucusu ile kayıt herhangi bir hedef makine verdiğinden kayıt anahtarı değeri güvenli kabul eder.</span><span class="sxs-lookup"><span data-stu-id="7650d-184">Always treat the registration key value securely, because knowing it allows any target machine to register with the pull server.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration Sample_MetaConfigurationToRegisterWithLessSecurePullServer
{
    param
    (
        [ValidateNotNullOrEmpty()]
        [string] $NodeName = 'localhost',

        [ValidateNotNullOrEmpty()]
        [string] $RegistrationKey, #same as the one used to setup pull server in previous configuration

        [ValidateNotNullOrEmpty()]
        [string] $ServerName = 'localhost' #node name of the pull server, same as $NodeName used in previous configuration
    )

    Node $NodeName
    {
        Settings
        {
            RefreshMode        = 'Pull'
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL          = "https://$ServerName`:8080/PSDSCPullServer.svc" # notice it is https
            RegistrationKey    = $RegistrationKey
            ConfigurationNames = @('ClientConfig')
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL       = "https://$ServerName`:8080/PSDSCPullServer.svc" # notice it is https
            RegistrationKey = $RegistrationKey
        }
    }
}

Sample_MetaConfigurationToRegisterWithLessSecurePullServer -RegistrationKey $RegistrationKey -OutputPath c:\Configs\TargetNodes
```

> <span data-ttu-id="7650d-185">**Not**: **ReportServerWeb** bölümü çekme sunucusuna gönderilecek verileri raporlama sağlar.</span><span class="sxs-lookup"><span data-stu-id="7650d-185">**Note**: The **ReportServerWeb** section allows reporting data to be sent to the pull server.</span></span>

<span data-ttu-id="7650d-186">Eksikliği **ConfigurationID** meta yapılandırmasını dosyasında özellik örtük olarak anlamına gelir, çekme sunucu bir ilk kaydı gerekli olacak şekilde çekme sunucusu protokolü V2 sürümünü destekliyor.</span><span class="sxs-lookup"><span data-stu-id="7650d-186">The lack of the **ConfigurationID** property in the metaconfiguration file implicitly means that pull server is supporting the V2 version of the pull server protocol so an initial registration is required.</span></span>
<span data-ttu-id="7650d-187">Buna karşılık, varlığını bir **ConfigurationID** çekme sunucusu protokolü V1 sürümünü kullanılır ve da bir kayıt işleme anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="7650d-187">Conversely, the presence of a **ConfigurationID** means that the V1 version of the pull server protocol is used and there is no registration processing.</span></span>

><span data-ttu-id="7650d-188">**Not**: içinde bir anında İLETME senaryosu, bir hata var. geçerli sürümde hiçbir zaman bir çekme sunucusuna kaydettirdiyseniz düğümleri için meta yapılandırmasını dosyasındaki bir ConfigurationID özellik tanımlamak için gerekli hale getirir.</span><span class="sxs-lookup"><span data-stu-id="7650d-188">**Note**: In a PUSH scenario, a bug exists in the current release that makes it necessary to define a ConfigurationID property in the metaconfiguration file for nodes that have never registered with a pull server.</span></span> <span data-ttu-id="7650d-189">V1 çekme sunucu protokolü zorlamak ve kayıt hata iletileri kaçının.</span><span class="sxs-lookup"><span data-stu-id="7650d-189">This will force the V1 Pull Server protocol and avoid registration failure messages.</span></span>

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="7650d-190">Yapılandırmaları ve kaynakları yerleştirme</span><span class="sxs-lookup"><span data-stu-id="7650d-190">Placing configurations and resources</span></span>

<span data-ttu-id="7650d-191">Çekme sonra sunucu Kurulum tamamlandıktan, tarafından tanımlanan klasörleri **ConfigurationPath** ve **ModulePath** çekme sunucu yapılandırması özelliklerinde olan modülleri ve yapılandırmaları olduğu yerleştirir Hedef düğümleri çıkarmak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7650d-191">After the pull server setup completes, the folders defined by the **ConfigurationPath** and **ModulePath** properties in the pull server configuration are where you will place modules and configurations that will be available for target nodes to pull.</span></span>
<span data-ttu-id="7650d-192">Bu dosyalar çekme sunucusunun doğru şekilde işlemek sırayla belirli bir biçimde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="7650d-192">These files need to be in a specific format in order for the pull server to correctly process them.</span></span>

### <a name="dsc-resource-module-package-format"></a><span data-ttu-id="7650d-193">DSC kaynağı modülü paket biçimi</span><span class="sxs-lookup"><span data-stu-id="7650d-193">DSC resource module package format</span></span>

<span data-ttu-id="7650d-194">Her kaynak modül sıkıştırılmış ve göre aşağıdaki düzeni adlı gerekiyor `{Module Name}_{Module Version}.zip`.</span><span class="sxs-lookup"><span data-stu-id="7650d-194">Each resource module needs to be zipped and named according to the following pattern `{Module Name}_{Module Version}.zip`.</span></span>
<span data-ttu-id="7650d-195">Örneğin, 3.1.2.0 Modül sürümü xWebAdminstration adlı bir modül 'xWebAdministration_3.2.1.0.zip' adlı.</span><span class="sxs-lookup"><span data-stu-id="7650d-195">For example, a module named xWebAdminstration with a module version of 3.1.2.0 would be named 'xWebAdministration_3.2.1.0.zip'.</span></span>
<span data-ttu-id="7650d-196">Her bir modül sürümü tek zip dosyasında yer almalıdır.</span><span class="sxs-lookup"><span data-stu-id="7650d-196">Each version of a module must be contained in a single zip file.</span></span>
<span data-ttu-id="7650d-197">Yalnızca tek bir sürümünü her zip dosyasında bir kaynak olduğundan, WMF 5.0 ile tek bir dizin içinde birden çok modül sürümleri için destek eklendi modül biçimi desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="7650d-197">Since there is only a single version of a resource in each zip file, the module format added in WMF 5.0 with support for multiple module versions in a single directory is not supported.</span></span>
<span data-ttu-id="7650d-198">Bu, paketleme yukarı DSC kaynakları modüllerinin çekme server ile kullanmak için önce dizin yapısını küçük değişiklik gerektiğini anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="7650d-198">This means that before packaging up DSC resource modules for use with pull server you will need to make a small change to the directory structure.</span></span>
<span data-ttu-id="7650d-199">WMF 5.0 DSC kaynağı içeren modüller varsayılan biçimi ' {modül klasörü}\{Modül sürümü} \DscResources\{DSC kaynak klasörünü}\'.</span><span class="sxs-lookup"><span data-stu-id="7650d-199">The default format of modules containing DSC resource in WMF 5.0 is '{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\'.</span></span>
<span data-ttu-id="7650d-200">Çekme sunucunun kaydınızı paketleme önce kaldırmak **{Modül sürümü}** yolu olacak şekilde klasörü ' {modül klasörü} \DscResources\{DSC kaynak klasörünü}\'.</span><span class="sxs-lookup"><span data-stu-id="7650d-200">Before packaging up for the pull server, remove the **{Module version}** folder so the path becomes '{Module Folder}\DscResources\{DSC Resource Folder}\'.</span></span>
<span data-ttu-id="7650d-201">Bu değişiklikle, yukarıda açıklandığı gibi klasör zip ve bu ZIP dosyaları yerleştirmek **ModulePath** klasör.</span><span class="sxs-lookup"><span data-stu-id="7650d-201">With this change, zip the folder as described above and place these zip files in the **ModulePath** folder.</span></span>

<span data-ttu-id="7650d-202">Kullanım `New-DscChecksum {module zip file}` yeni eklenen modülü için sağlama toplamı dosya oluşturulamadı.</span><span class="sxs-lookup"><span data-stu-id="7650d-202">Use `New-DscChecksum {module zip file}` to create a checksum file for the newly added module.</span></span>

### <a name="configuration-mof-format"></a><span data-ttu-id="7650d-203">Yapılandırma MOF biçimi</span><span class="sxs-lookup"><span data-stu-id="7650d-203">Configuration MOF format</span></span>

<span data-ttu-id="7650d-204">Bir yapılandırma MOF dosyası yapılandırmasını hedef düğümde bir LCM'yi doğrulayabilmesi bir sağlama toplamı dosyasıyla eşleştirilmiş gerekir.</span><span class="sxs-lookup"><span data-stu-id="7650d-204">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span>
<span data-ttu-id="7650d-205">Bir sağlama toplamı oluşturmak için arama [yeni DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DscChecksum) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="7650d-205">To create a checksum, call the [New-DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DscChecksum) cmdlet.</span></span>
<span data-ttu-id="7650d-206">Cmdlet geçen bir **yolu** MOF yapılandırma bulunduğu klasörü belirten parametre.</span><span class="sxs-lookup"><span data-stu-id="7650d-206">The cmdlet takes a **Path** parameter that specifies the folder where the configuration MOF is located.</span></span>
<span data-ttu-id="7650d-207">Cmdlet adlı bir sağlama toplamı dosyası oluşturur `ConfigurationMOFName.mof.checksum`, burada `ConfigurationMOFName` yapılandırma mof dosyasının adıdır.</span><span class="sxs-lookup"><span data-stu-id="7650d-207">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span>
<span data-ttu-id="7650d-208">Belirtilen klasörde MOF dosyaları birden fazla yapılandırma varsa, her yapılandırma klasörü için bir sağlama toplamı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="7650d-208">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span>
<span data-ttu-id="7650d-209">MOF dosyaları ve ilişkili sağlama toplamı dosyalarına yerleştirmek **ConfigurationPath** klasör.</span><span class="sxs-lookup"><span data-stu-id="7650d-209">Place the MOF files and their associated checksum files in the **ConfigurationPath** folder.</span></span>

><span data-ttu-id="7650d-210">**Not**: herhangi bir şekilde yapılandırma MOF dosyasını değiştirirseniz, sağlama toplamı dosyasını da yeniden oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7650d-210">**Note**: If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

### <a name="tooling"></a><span data-ttu-id="7650d-211">Araçları</span><span class="sxs-lookup"><span data-stu-id="7650d-211">Tooling</span></span>

<span data-ttu-id="7650d-212">Ayar oluşturan için doğrulama ve daha kolay, çekme sunucusunu yönetme aşağıdaki araçları xPSDesiredStateConfiguration modülü en son sürümünü örneklerde olarak eklenir:</span><span class="sxs-lookup"><span data-stu-id="7650d-212">In order to make setting up, validating and managing the pull server easier, the following tools are included as examples in the latest version of the xPSDesiredStateConfiguration module:</span></span>

1. <span data-ttu-id="7650d-213">DSC kaynağı modülleri ve çekme sunucusunda kullanmak üzere yapılandırma dosyalarını paketleme ile yardımcı olacak bir modül.</span><span class="sxs-lookup"><span data-stu-id="7650d-213">A module that will help with packaging DSC resource modules and configuration files for use on the pull server.</span></span> <span data-ttu-id="7650d-214">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span><span class="sxs-lookup"><span data-stu-id="7650d-214">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span></span> <span data-ttu-id="7650d-215">Aşağıdaki örnekler:</span><span class="sxs-lookup"><span data-stu-id="7650d-215">Examples below:</span></span>

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @('xWebAdministration', 'xPhp')
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. <span data-ttu-id="7650d-216">Çekme sunucunun doğrulayan bir komut dosyası doğru yapılandırılmamış.</span><span class="sxs-lookup"><span data-stu-id="7650d-216">A script that validates the pull server is configured correctly.</span></span> <span data-ttu-id="7650d-217">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span><span class="sxs-lookup"><span data-stu-id="7650d-217">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span></span>

## <a name="community-solutions-for-pull-service"></a><span data-ttu-id="7650d-218">Çekme Hizmeti için topluluk çözümleri</span><span class="sxs-lookup"><span data-stu-id="7650d-218">Community Solutions for Pull Service</span></span>

<span data-ttu-id="7650d-219">DSC topluluk çekme hizmet protokolü uygulamak için birden çok çözümleri yazılan.</span><span class="sxs-lookup"><span data-stu-id="7650d-219">The DSC community has authored multiple solutions to implement the pull service protocol.</span></span>
<span data-ttu-id="7650d-220">Şirket içi ortamları için bu çekme hizmet özellikleri ve geri artımlı iyileştirmeleri topluluğa katkıda fırsatı sunar.</span><span class="sxs-lookup"><span data-stu-id="7650d-220">For on-premises environments, these offer pull service capabilities and an opportunity to contribute back to the community with incremental enhancements.</span></span>

- [<span data-ttu-id="7650d-221">Tug</span><span class="sxs-lookup"><span data-stu-id="7650d-221">Tug</span></span>](https://github.com/powershellorg/tug)
- [<span data-ttu-id="7650d-222">DSC TRÆK</span><span class="sxs-lookup"><span data-stu-id="7650d-222">DSC-TRÆK</span></span>](https://github.com/powershellorg/dsc-traek)

## <a name="pull-client-configuration"></a><span data-ttu-id="7650d-223">Çekme istemci yapılandırması</span><span class="sxs-lookup"><span data-stu-id="7650d-223">Pull client configuration</span></span>

<span data-ttu-id="7650d-224">Aşağıdaki konularda ayrıntılı çekme istemcileri ayarlama açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="7650d-224">The following topics describe setting up pull clients in detail:</span></span>

- [<span data-ttu-id="7650d-225">Bir yapılandırma kimliği kullanan bir DSC çekme istemci ayarlama</span><span class="sxs-lookup"><span data-stu-id="7650d-225">Setting up a DSC pull client using a configuration ID</span></span>](pullClientConfigID.md)
- [<span data-ttu-id="7650d-226">Yapılandırma adları kullanarak bir DSC çekme istemcisi ayarlama</span><span class="sxs-lookup"><span data-stu-id="7650d-226">Setting up a DSC pull client using configuration names</span></span>](pullClientConfigNames.md)
- [<span data-ttu-id="7650d-227">Kısmi yapılandırmaları</span><span class="sxs-lookup"><span data-stu-id="7650d-227">Partial configurations</span></span>](partialConfigs.md)

## <a name="see-also"></a><span data-ttu-id="7650d-228">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="7650d-228">See also</span></span>

- [<span data-ttu-id="7650d-229">Windows PowerShell istenen durum yapılandırması genel bakış</span><span class="sxs-lookup"><span data-stu-id="7650d-229">Windows PowerShell Desired State Configuration Overview</span></span>](overview.md)
- [<span data-ttu-id="7650d-230">Yapılandırmaları Kabul Etme</span><span class="sxs-lookup"><span data-stu-id="7650d-230">Enacting configurations</span></span>](enactingConfigurations.md)
- [<span data-ttu-id="7650d-231">DSC rapor sunucusu kullanma</span><span class="sxs-lookup"><span data-stu-id="7650d-231">Using a DSC report server</span></span>](reportServer.md)