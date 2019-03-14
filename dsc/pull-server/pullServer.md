---
ms.date: 03/04/2019
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC Çekme Hizmeti
ms.openlocfilehash: 27effe0cd3b9d90dcfaaf1bd4e38edf3c04c9cfb
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794731"
---
# <a name="desired-state-configuration-pull-service"></a><span data-ttu-id="44806-103">Desired State Configuration çekme hizmeti</span><span class="sxs-lookup"><span data-stu-id="44806-103">Desired State Configuration Pull Service</span></span>

> [!IMPORTANT]
> <span data-ttu-id="44806-104">Çekme sunucusu (Windows özelliği *DSC hizmet*) ancak desteklenen bir bileşen Windows Server'ın yeni özellikler veya yetenekler sunmak için herhangi bir plan vardır.</span><span class="sxs-lookup"><span data-stu-id="44806-104">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="44806-105">Geçişi başlıyor önerilir yönetilen istemcilere [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (Windows Server çekme sunucusunda dışında özellikler dahildir) veya topluluk çözümlerden birini listelenen [burada](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="44806-105">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="44806-106">Yerel Configuration Manager, bir çekme hizmetini çözümü tarafından merkezi olarak yönetilebilir.</span><span class="sxs-lookup"><span data-stu-id="44806-106">Local Configuration Manager can be centrally managed by a Pull Service solution.</span></span>
<span data-ttu-id="44806-107">Bu yaklaşımı kullanarak, yönetilen düğüme bir hizmete kayıtlı ve LCM ayarları yapılandırmasında atanan.</span><span class="sxs-lookup"><span data-stu-id="44806-107">When using this approach, the node that is being managed is registered with a service and assigned a configuration in LCM settings.</span></span>
<span data-ttu-id="44806-108">Yapılandırması ve yapılandırma için bağımlılık olarak gerekli olan tüm DSC kaynaklarını makineye indirilir ve yapılandırmasını yönetmek için LCM tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="44806-108">The configuration and all DSC resources needed as dependencies for the configuration are downloaded to the machine and used by LCM to manage the configuration.</span></span>
<span data-ttu-id="44806-109">Yönetilen makinenin durumu hakkında bilgi, hizmet raporlama için yüklenir.</span><span class="sxs-lookup"><span data-stu-id="44806-109">Information about the state of the machine being managed is uploaded to the service for reporting.</span></span>
<span data-ttu-id="44806-110">Bu kavramı "çekme hizmeti." olarak adlandırılır</span><span class="sxs-lookup"><span data-stu-id="44806-110">This concept is referred to as "pull service."</span></span>

<span data-ttu-id="44806-111">Çekme Hizmeti için geçerli seçenekler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="44806-111">The current options for pull service include:</span></span>

- <span data-ttu-id="44806-112">Azure Otomasyonu Desired State Configuration hizmeti</span><span class="sxs-lookup"><span data-stu-id="44806-112">Azure Automation Desired State Configuration service</span></span>
- <span data-ttu-id="44806-113">Windows Server üzerinde çalışan bir çekme hizmeti</span><span class="sxs-lookup"><span data-stu-id="44806-113">A pull service running on Windows Server</span></span>
- <span data-ttu-id="44806-114">Açık kaynak çözümleri tutulan topluluk</span><span class="sxs-lookup"><span data-stu-id="44806-114">Community maintained open-source solutions</span></span>
- <span data-ttu-id="44806-115">SMB paylaşımı</span><span class="sxs-lookup"><span data-stu-id="44806-115">An SMB share</span></span>

<span data-ttu-id="44806-116">**Önerilen Çözüm**, ve en çok kullanılabilir olan özellikleri seçeneğiyle [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span><span class="sxs-lookup"><span data-stu-id="44806-116">**The recommended solution**, and the option with the most features available, is [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span></span>

<span data-ttu-id="44806-117">Azure hizmet düğümleri şirket içi özel veri merkezinde veya genel bulutlarda Azure ve AWS gibi yönetebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44806-117">The Azure service can manage nodes on-premises in private datacenters, or in public clouds such as Azure and AWS.</span></span>
<span data-ttu-id="44806-118">Yalnızca yayımlanan Azure IP aralığına giden trafiği sınırlamak burada sunucuları doğrudan bağlanamaz Internet'e özel ortamları için göz önünde bulundurun (bkz [Azure veri merkezi IP aralıkları](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).</span><span class="sxs-lookup"><span data-stu-id="44806-118">For private environments where servers cannot directly connect to the Internet, consider limiting outbound traffic to only the published Azure IP range (see [Azure Datacenter IP Ranges](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).</span></span>

<span data-ttu-id="44806-119">Çevrimiçi hizmet çekme hizmetini Windows Server üzerinde şu anda kullanılabilir olmayan özellikler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="44806-119">Features of the online service that are not currently available in the pull service on Windows Server include:</span></span>

- <span data-ttu-id="44806-120">Tüm veriler aktarımda ve bekleme sırasında şifrelenir</span><span class="sxs-lookup"><span data-stu-id="44806-120">All data is encrypted in transit and at rest</span></span>
- <span data-ttu-id="44806-121">İstemci sertifikaları oluşturulur ve otomatik olarak yönetilir</span><span class="sxs-lookup"><span data-stu-id="44806-121">Client certificates are created and managed automatically</span></span>
- <span data-ttu-id="44806-122">Gizli dizileri depolamak merkezi olarak yönetmek için [parolaları/kimlik bilgilerinin](/azure/automation/automation-credentials), veya [değişkenleri](/azure/automation/automation-variables) sunucu adları veya bağlantı dizeleri gibi</span><span class="sxs-lookup"><span data-stu-id="44806-122">Secrets store for centrally managing [passwords/credentials](/azure/automation/automation-credentials), or [variables](/azure/automation/automation-variables) such as server names or connection strings</span></span>
- <span data-ttu-id="44806-123">Düğüm merkezi olarak yönetin [LCM yapılandırma](../managing-nodes/metaConfig.md#basic-settings)</span><span class="sxs-lookup"><span data-stu-id="44806-123">Centrally manage node [LCM configuration](../managing-nodes/metaConfig.md#basic-settings)</span></span>
- <span data-ttu-id="44806-124">Merkezi olarak istemci düğüm yapılandırmaları Ata</span><span class="sxs-lookup"><span data-stu-id="44806-124">Centrally assign configurations to client nodes</span></span>
- <span data-ttu-id="44806-125">Üretim ulaşmadan önce test etmek için "kanarya gruplarına" yayın yapılandırması değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="44806-125">Release configuration changes to "canary groups" for testing before reaching production</span></span>
- <span data-ttu-id="44806-126">Grafik raporlama</span><span class="sxs-lookup"><span data-stu-id="44806-126">Graphical reporting</span></span>
  - <span data-ttu-id="44806-127">DSC kaynak düzeyinde ayrıntı durumu ayrıntısı</span><span class="sxs-lookup"><span data-stu-id="44806-127">Status detail at the DSC resource level of granularity</span></span>
  - <span data-ttu-id="44806-128">Sorun giderme için istemci makinelerden ayrıntılı hata iletileri</span><span class="sxs-lookup"><span data-stu-id="44806-128">Verbose error messages from client machines for troubleshooting</span></span>
- <span data-ttu-id="44806-129">[Azure Log Analytics ile tümleştirme](/azure/automation/automation-dsc-diagnostics) uyarı verme, otomatik görevler, raporlama ve uyarı Android/iOS uygulaması</span><span class="sxs-lookup"><span data-stu-id="44806-129">[Integration with Azure Log Analytics](/azure/automation/automation-dsc-diagnostics) for alerting, automated tasks, Android/iOS app for reporting and alerting</span></span>

## <a name="dsc-pull-service-in-windows-server"></a><span data-ttu-id="44806-130">Windows Server'da DSC çekme hizmeti</span><span class="sxs-lookup"><span data-stu-id="44806-130">DSC pull service in Windows Server</span></span>

<span data-ttu-id="44806-131">Windows Server üzerinde çalıştırmak için bir çekme hizmetini yapılandırmak için mümkündür.</span><span class="sxs-lookup"><span data-stu-id="44806-131">It is possible to configuring a pull service to run on Windows Server.</span></span>
<span data-ttu-id="44806-132">Windows Server'a dahil çekme hizmet çözümü yapılandırmaları/modules indirmek için depolama ve veritabanı için rapor verilerini yakalama yalnızca özellikleri içerdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="44806-132">Be advised that the pull service solution included in Windows Server includes only capabilities of storing configurations/modules for download and capturing report data in to database.</span></span>
<span data-ttu-id="44806-133">Çoğu Azure hizmeti tarafından sunulan içermez ve bu nedenle nasıl hizmet kullanılan değerlendirmek için iyi bir aracı değildir.</span><span class="sxs-lookup"><span data-stu-id="44806-133">It does not include many of the capabilities offered by the service in Azure and so is not a good tool for evaluating how the service would be used.</span></span>

<span data-ttu-id="44806-134">Windows Server'da sunulan çekme hizmetini bir düğümleri için isteyin, DSC yapılandırma dosyalarını hedef düğümler için kullanılabilir hale getirmek için bir OData arabirimini kullanan bir IIS web hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="44806-134">The pull service offered in Windows Server is a web service in IIS that uses an OData interface to make DSC configuration files available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="44806-135">Bir çekme sunucusu kullanmak için gereksinimler:</span><span class="sxs-lookup"><span data-stu-id="44806-135">Requirements for using a pull server:</span></span>

- <span data-ttu-id="44806-136">Çalıştıran bir sunucu:</span><span class="sxs-lookup"><span data-stu-id="44806-136">A server running:</span></span>
  - <span data-ttu-id="44806-137">WMF/PowerShell 4.0 veya üzeri</span><span class="sxs-lookup"><span data-stu-id="44806-137">WMF/PowerShell 4.0 or greater</span></span>
  - <span data-ttu-id="44806-138">IIS sunucu rolü</span><span class="sxs-lookup"><span data-stu-id="44806-138">IIS server role</span></span>
  - <span data-ttu-id="44806-139">DSC hizmeti</span><span class="sxs-lookup"><span data-stu-id="44806-139">DSC Service</span></span>
- <span data-ttu-id="44806-140">İdeal olarak, bazı anlamına gelir bir sertifika oluşturma hedef düğümlerde yerel Configuration Manager (LCM) geçirilen kimlik bilgilerini güvenli hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="44806-140">Ideally, some means of generating a certificate, to secure credentials passed to the Local Configuration Manager (LCM) on target nodes</span></span>

<span data-ttu-id="44806-141">Windows Server için konak çekme hizmetini yapılandırmak için en iyi yolu, bir DSC yapılandırması kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="44806-141">The best way to configure Windows Server to host pull service is to use a DSC configuration.</span></span>
<span data-ttu-id="44806-142">Bir örnek betiği aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="44806-142">An example script is provided below.</span></span>

### <a name="supported-database-systems"></a><span data-ttu-id="44806-143">Desteklenen veritabanı sistemleri</span><span class="sxs-lookup"><span data-stu-id="44806-143">Supported database systems</span></span>

|<span data-ttu-id="44806-144">WMF 4.0</span><span class="sxs-lookup"><span data-stu-id="44806-144">WMF 4.0</span></span>   |<span data-ttu-id="44806-145">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="44806-145">WMF 5.0</span></span>  |<span data-ttu-id="44806-146">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="44806-146">WMF 5.1</span></span> |<span data-ttu-id="44806-147">WMF 5.1 (Windows Server Insider Önizleme 17090)</span><span class="sxs-lookup"><span data-stu-id="44806-147">WMF 5.1 (Windows Server Insider Preview 17090)</span></span>|
|---------|---------|---------|---------|
|<span data-ttu-id="44806-148">MDB</span><span class="sxs-lookup"><span data-stu-id="44806-148">MDB</span></span>     |<span data-ttu-id="44806-149">ESENT (varsayılan), MDB</span><span class="sxs-lookup"><span data-stu-id="44806-149">ESENT (Default), MDB</span></span> |<span data-ttu-id="44806-150">ESENT (varsayılan), MDB</span><span class="sxs-lookup"><span data-stu-id="44806-150">ESENT (Default), MDB</span></span>|<span data-ttu-id="44806-151">ESENT (varsayılan), SQL Server'ı MDB</span><span class="sxs-lookup"><span data-stu-id="44806-151">ESENT (Default), SQL Server, MDB</span></span>

<span data-ttu-id="44806-152">İtibariyle, 17090 yayın [Windows Server Insider Preview](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewserver), SQL Server, çekme hizmeti için desteklenen bir seçenektir (Windows özelliği *DSC hizmet*).</span><span class="sxs-lookup"><span data-stu-id="44806-152">Starting in release 17090 of [Windows Server Insider Preview](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewserver), SQL Server is a supported option for the Pull Service (Windows Feature *DSC-Service*).</span></span> <span data-ttu-id="44806-153">Bunun için geçmemiş büyük DSC ortamlarda ölçeklendirmeye yönelik yeni bir seçenek sağlar [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span><span class="sxs-lookup"><span data-stu-id="44806-153">This provides a new option for scaling large DSC environments that have not migrated to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span></span>

> <span data-ttu-id="44806-154">**Not**: SQL Server desteği, önceki sürümler için WMF 5.1 (veya öncesi) eklenmez ve yalnızca Windows Server sürümlerinde büyüktür veya eşittir 17090 için kullanılabilir olacak.</span><span class="sxs-lookup"><span data-stu-id="44806-154">**Note**: SQL Server support will not be added to previous versions of WMF 5.1 (or earlier) and will only be available on Windows Server versions greater than or equal to 17090.</span></span>

<span data-ttu-id="44806-155">Çekme sunucusunu SQL Server'ı kullanacak şekilde yapılandırmak için **SqlProvider** için `$true` ve **SqlConnectionString** için geçerli bir SQL Server bağlantı dizesi.</span><span class="sxs-lookup"><span data-stu-id="44806-155">To configure the pull server to use SQL Server, set **SqlProvider** to `$true` and **SqlConnectionString** to a valid SQL Server Connection String.</span></span> <span data-ttu-id="44806-156">Daha fazla bilgi için [SqlClient bağlantı dizeleri](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings).</span><span class="sxs-lookup"><span data-stu-id="44806-156">For more information, see [SqlClient Connection Strings](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings).</span></span>
<span data-ttu-id="44806-157">Bir örnek ile SQL Server yapılandırmasının **xDscWebService**, öncelikle [xDscWebService kaynak kullanarak](#using-the-xdscwebservice-resource) ve daha sonra gözden [Sample_xDscWebServiceRegistration_ GitHub üzerinde UseSQLProvider.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1).</span><span class="sxs-lookup"><span data-stu-id="44806-157">For an example of SQL Server configuration with **xDscWebService**, first read [Using the xDscWebService resource](#using-the-xdscwebservice-resource) and then review [Sample_xDscWebServiceRegistration_UseSQLProvider.ps1 on GitHub](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1).</span></span>

### <a name="using-the-xdscwebservice-resource"></a><span data-ttu-id="44806-158">XDscWebService kaynağı kullanma</span><span class="sxs-lookup"><span data-stu-id="44806-158">Using the xDscWebService resource</span></span>

<span data-ttu-id="44806-159">Web çekme sunucusu kurmak için en kolay yolu kullanmaktır **xDscWebService** dahil kaynak **xPSDesiredStateConfiguration** modülü.</span><span class="sxs-lookup"><span data-stu-id="44806-159">The easiest way to set up a web pull server is to use the **xDscWebService** resource, included in the **xPSDesiredStateConfiguration** module.</span></span>
<span data-ttu-id="44806-160">Aşağıdaki adımlarda, kaynak web hizmeti oluşturmaya ayarlar bir yapılandırmada kullanmak açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="44806-160">The following steps explain how to use the resource in a configuration that sets up the web service.</span></span>

1. <span data-ttu-id="44806-161">Çağrı [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet'ine **xPSDesiredStateConfiguration** modülü.</span><span class="sxs-lookup"><span data-stu-id="44806-161">Call the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to install the **xPSDesiredStateConfiguration** module.</span></span>
   > [!NOTE]
   > <span data-ttu-id="44806-162">**Install-Module** dahil **PowerShellGet** modülü, PowerShell 5. 0'da dahildir.</span><span class="sxs-lookup"><span data-stu-id="44806-162">**Install-Module** is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="44806-163">İndirebileceğiniz **PowerShellGet** modülü PowerShell 3.0 ve 4.0, [PackageManagement PowerShell modülleri Önizleme](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span><span class="sxs-lookup"><span data-stu-id="44806-163">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span>
2. <span data-ttu-id="44806-164">Bir SSL sertifikası güvenilen bir sertifika yetkilisi, kuruluşunuz veya bir ortak yetkilisi ya da DSC çekme sunucusu alın.</span><span class="sxs-lookup"><span data-stu-id="44806-164">Get an SSL certificate for the DSC Pull server from a trusted Certificate Authority, either within your organization or a public authority.</span></span> <span data-ttu-id="44806-165">Genellikle yetkilisinden alınan sertifika PFX biçimi ' dir.</span><span class="sxs-lookup"><span data-stu-id="44806-165">The certificate received from the authority is usually in the PFX format.</span></span>
3. <span data-ttu-id="44806-166">DSC çekme sunucusu olmalıdır varsayılan konumda olacak düğüme sertifikayı yükleme `CERT:\LocalMachine\My`.</span><span class="sxs-lookup"><span data-stu-id="44806-166">Install the certificate on the node that will become the DSC Pull server in the default location, which should be `CERT:\LocalMachine\My`.</span></span>
   - <span data-ttu-id="44806-167">Sertifika parmak izini not edin.</span><span class="sxs-lookup"><span data-stu-id="44806-167">Make a note of the certificate thumbprint.</span></span>
4. <span data-ttu-id="44806-168">Kayıt anahtarı kullanılacak bir GUID seçin.</span><span class="sxs-lookup"><span data-stu-id="44806-168">Select a GUID to be used as the Registration Key.</span></span> <span data-ttu-id="44806-169">İçin bir PowerShell kullanarak, PS istemine aşağıdakileri girin ve enter tuşuna basın: `[guid]::newGuid()` veya `New-Guid`.</span><span class="sxs-lookup"><span data-stu-id="44806-169">To generate one using PowerShell enter the following at the PS prompt and press enter: `[guid]::newGuid()` or `New-Guid`.</span></span> <span data-ttu-id="44806-170">Bu anahtar tarafından istemci düğümleri kayıt sırasında kimlik doğrulaması için paylaşılan bir anahtar olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="44806-170">This key will be used by client nodes as a shared key to authenticate during registration.</span></span> <span data-ttu-id="44806-171">Daha fazla bilgi için kayıt anahtarı bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="44806-171">For more information, see the Registration Key section below.</span></span>
5. <span data-ttu-id="44806-172">PowerShell ISE'de (F5) aşağıdaki yapılandırma betiğini Başlat (örnekler klasöründe bulunan **xPSDesiredStateConfiguration** modül olarak `Sample_xDscWebServiceRegistration.ps1`).</span><span class="sxs-lookup"><span data-stu-id="44806-172">In the PowerShell ISE, start (F5) the following configuration script (included in the Examples folder of the **xPSDesiredStateConfiguration** module as `Sample_xDscWebServiceRegistration.ps1`).</span></span> <span data-ttu-id="44806-173">Bu betik, çekme sunucusu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="44806-173">This script sets up the pull server.</span></span>

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

        Import-DSCResource -ModuleName PSDesiredStateConfiguration
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
                UseSecurityBestPractices     = $true
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

6. <span data-ttu-id="44806-174">Çalıştırma SSL sertifikası parmak izi geçirme yapılandırmasını **certificateThumbPrint** parametre ve bir GUID kayıt anahtarı olarak **RegistrationKey** parametresi:</span><span class="sxs-lookup"><span data-stu-id="44806-174">Run the configuration, passing the thumbprint of the SSL certificate as the **certificateThumbPrint** parameter and a GUID registration key as the **RegistrationKey** parameter:</span></span>

    ```powershell
    # To find the Thumbprint for an installed SSL certificate for use with the pull server list all certificates in your local store
    # and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
    dir Cert:\LocalMachine\my

    # Then include this thumbprint when running the configuration
    Sample_xDscWebServiceRegistration -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutputPath c:\Configs\PullServer

    # Run the compiled configuration to make the target node a DSC Pull Server
    Start-DscConfiguration -Path c:\Configs\PullServer -Wait -Verbose
    ```

#### <a name="registration-key"></a><span data-ttu-id="44806-175">Kayıt anahtarı</span><span class="sxs-lookup"><span data-stu-id="44806-175">Registration Key</span></span>

<span data-ttu-id="44806-176">İstemci yapılandırma adları yerine bir yapılandırma kimliği kullanabilmeniz sunucusu ile kayıt düğümleri izin vermek için yukarıdaki yapılandırma tarafından oluşturulan bir kayıt anahtarı adlı bir dosyaya kaydedilir `RegistrationKeys.txt` içinde `C:\Program Files\WindowsPowerShell\DscService`.</span><span class="sxs-lookup"><span data-stu-id="44806-176">To allow client nodes to register with the server so that they can use configuration names instead of a configuration ID, a registration key that was created by the above configuration is saved in a file named `RegistrationKeys.txt` in `C:\Program Files\WindowsPowerShell\DscService`.</span></span> <span data-ttu-id="44806-177">Kayıt anahtarı, ilk kayıt sırasında çekme sunucusu ile istemci tarafından kullanılan paylaşılan gizlilik işlevini görür.</span><span class="sxs-lookup"><span data-stu-id="44806-177">The registration key functions as a shared secret used during the initial registration by the client with the pull server.</span></span> <span data-ttu-id="44806-178">İstemci kayıt başarıyla tamamlandıktan sonra çekme sunucusuna benzersiz kimliğini doğrulamak için kullanılan otomatik olarak imzalanan bir sertifika oluşturur.</span><span class="sxs-lookup"><span data-stu-id="44806-178">The client will generate a self-signed certificate that is used to uniquely authenticate to the pull server once registration is successfully completed.</span></span> <span data-ttu-id="44806-179">Bu sertifikanın parmak izini yerel olarak depolanan ve çekme sunucusu URL'si ile ilişkili.</span><span class="sxs-lookup"><span data-stu-id="44806-179">The thumbprint of this certificate is stored locally and associated with the URL of the pull server.</span></span>

> [!NOTE]
> <span data-ttu-id="44806-180">PowerShell 4. 0'kayıt anahtarları desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="44806-180">Registration keys are not supported in PowerShell 4.0.</span></span>

<span data-ttu-id="44806-181">Çekme sunucusu ile kimlik doğrulaması için bir düğüm yapılandırmak için kayıt anahtarını metaconfiguration bu çekme sunucusu ile kayıt herhangi bir hedef düğüm için yer alması gerekir.</span><span class="sxs-lookup"><span data-stu-id="44806-181">In order to configure a node to authenticate with the pull server, the registration key needs to be in the metaconfiguration for any target node that will be registering with this pull server.</span></span> <span data-ttu-id="44806-182">Unutmayın **RegistrationKey** aşağıdaki metaconfiguration hedef makine'nın başarıyla kaydolduğunu ve değer saklanan değerle eşleşmelidir sonra kaldırılır `RegistrationKeys.txt` çekme sunucusunda dosyasını (' 140a952b-b9d6-406b-b416-e0f759c9c0e4' Bu örnek için).</span><span class="sxs-lookup"><span data-stu-id="44806-182">Note that the **RegistrationKey** in the metaconfiguration below is removed after the target machine has successfully registered, and that the value must match the value stored in the `RegistrationKeys.txt` file on the pull server ('140a952b-b9d6-406b-b416-e0f759c9c0e4' for this example).</span></span> <span data-ttu-id="44806-183">Her zaman farkında çekme sunucusu ile kayıt herhangi bir hedef makine izin verdiğinden kayıt anahtar değeri güvenli bir şekilde, kabul eder.</span><span class="sxs-lookup"><span data-stu-id="44806-183">Always treat the registration key value securely, because knowing it allows any target machine to register with the pull server.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration Sample_MetaConfigurationToRegisterWithLessSecurePullServer
{
    param
    (
        [ValidateNotNullOrEmpty()]
        [string] $NodeName = 'localhost',

        [ValidateNotNullOrEmpty()]
        [string] $RegistrationKey, #same as the one used to set up pull server in previous configuration

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

> [!NOTE]
> <span data-ttu-id="44806-184">**ReportServerWeb** bölümü raporlama verilerini çekme sunucusuna gönderilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="44806-184">The **ReportServerWeb** section allows reporting data to be sent to the pull server.</span></span>

<span data-ttu-id="44806-185">Eksikliği **ConfigurationID** metaconfiguration dosyasındaki özellik örtük olarak anlamına gelir, çekme sunucusu bir ilk kaydı gerekli olacak şekilde çekme sunucusu protokolü V2 sürümünü destekleme.</span><span class="sxs-lookup"><span data-stu-id="44806-185">The lack of the **ConfigurationID** property in the metaconfiguration file implicitly means that pull server is supporting the V2 version of the pull server protocol so an initial registration is required.</span></span>
<span data-ttu-id="44806-186">Buna karşılık, varlığı bir **ConfigurationID** çekme sunucusu protokolü V1 sürümü kullanılır ve hiçbir kayıt işleme yoktur anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="44806-186">Conversely, the presence of a **ConfigurationID** means that the V1 version of the pull server protocol is used and there is no registration processing.</span></span>

> [!NOTE]
> <span data-ttu-id="44806-187">Bir anında İLETME senaryosunda, hiçbir zaman bir çekme sunucusuna kaydettirdiyseniz düğümleri metaconfiguration dosyasında ConfigurationID özelliği tanımlamak gerekli kılan geçerli sürümde olan bir hata var.</span><span class="sxs-lookup"><span data-stu-id="44806-187">In a PUSH scenario, a bug exists in the current release that makes it necessary to define a ConfigurationID property in the metaconfiguration file for nodes that have never registered with a pull server.</span></span> <span data-ttu-id="44806-188">V1 çekme sunucusu protokolü zorlamak ve kayıt hata iletileri kaçının.</span><span class="sxs-lookup"><span data-stu-id="44806-188">This will force the V1 Pull Server protocol and avoid registration failure messages.</span></span>

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="44806-189">Yapılandırmaları ve kaynakları yerleştirme</span><span class="sxs-lookup"><span data-stu-id="44806-189">Placing configurations and resources</span></span>

<span data-ttu-id="44806-190">Sonra çekme Sunucusu Kurulumu tamamlandığında, tarafından tanımlanan klasörleri **Yapılandırmayolu** ve **ModulePath** çekme sunucusu yapılandırma özelliklerinde olan modülleri ve yapılandırmaları koyacağı Hedef düğümleri çekmek kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="44806-190">After the pull server setup completes, the folders defined by the **ConfigurationPath** and **ModulePath** properties in the pull server configuration are where you will place modules and configurations that will be available for target nodes to pull.</span></span>
<span data-ttu-id="44806-191">Bu dosyalar çekme sunucusunun doğru şekilde işlemek sırada belirli bir biçimde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="44806-191">These files need to be in a specific format in order for the pull server to correctly process them.</span></span>

### <a name="dsc-resource-module-package-format"></a><span data-ttu-id="44806-192">DSC kaynak modülü paket biçimi</span><span class="sxs-lookup"><span data-stu-id="44806-192">DSC resource module package format</span></span>

<span data-ttu-id="44806-193">Her kaynak modülü sıkıştırılmasını ve aşağıdaki modele göre adında gereken `{Module Name}_{Module Version}.zip`.</span><span class="sxs-lookup"><span data-stu-id="44806-193">Each resource module needs to be zipped and named according to the following pattern `{Module Name}_{Module Version}.zip`.</span></span>

<span data-ttu-id="44806-194">Örneğin, bir modül sürümüyle 3.1.2.0 xWebAdminstration adlı bir modül adlı `xWebAdministration_3.2.1.0.zip`.</span><span class="sxs-lookup"><span data-stu-id="44806-194">For example, a module named xWebAdminstration with a module version of 3.1.2.0 would be named `xWebAdministration_3.2.1.0.zip`.</span></span>
<span data-ttu-id="44806-195">Her bir modül sürümü tek zip dosyasında yer almalıdır.</span><span class="sxs-lookup"><span data-stu-id="44806-195">Each version of a module must be contained in a single zip file.</span></span>
<span data-ttu-id="44806-196">Bir kaynağın her zip dosyası yalnızca tek bir sürüm olduğundan, WMF 5. 0'ile tek bir dizinde birden çok modül sürümleri için destek eklendi modül biçimi desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="44806-196">Since there is only a single version of a resource in each zip file, the module format added in WMF 5.0 with support for multiple module versions in a single directory is not supported.</span></span>
<span data-ttu-id="44806-197">Bu DSC çekme server ile kullanmak için kaynak modülleri'kurmak paketleme önce küçük bir değişiklik yapmak için dizin yapısını gerektiğini anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="44806-197">This means that before packaging up DSC resource modules for use with pull server you will need to make a small change to the directory structure.</span></span>
<span data-ttu-id="44806-198">WMF 5.0 DSC kaynağı içeren modüllerin varsayılan biçimi `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.</span><span class="sxs-lookup"><span data-stu-id="44806-198">The default format of modules containing DSC resource in WMF 5.0 is `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.</span></span>
<span data-ttu-id="44806-199">Çekme sunucusu için paketleme önce kaldırmak **{Modül sürümü}** klasör yolu olacak şekilde `{Module Folder}\DscResources\{DSC Resource Folder}\`.</span><span class="sxs-lookup"><span data-stu-id="44806-199">Before packaging up for the pull server, remove the **{Module version}** folder so the path becomes `{Module Folder}\DscResources\{DSC Resource Folder}\`.</span></span>
<span data-ttu-id="44806-200">Bu değişiklik, yukarıda açıklandığı gibi klasör zip ve bu zip dosyalarını **ModulePath** klasör.</span><span class="sxs-lookup"><span data-stu-id="44806-200">With this change, zip the folder as described above and place these zip files in the **ModulePath** folder.</span></span>

<span data-ttu-id="44806-201">Kullanım `New-DscChecksum {module zip file}` yeni eklenen modülün bir sağlama toplamı dosyası oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="44806-201">Use `New-DscChecksum {module zip file}` to create a checksum file for the newly added module.</span></span>

### <a name="configuration-mof-format"></a><span data-ttu-id="44806-202">Yapılandırma MOF biçimi</span><span class="sxs-lookup"><span data-stu-id="44806-202">Configuration MOF format</span></span>

<span data-ttu-id="44806-203">Yapılandırma MOF dosyasının yapılandırmasını hedef düğümde bir LCM doğrulayabilmesi bir sağlama toplamı dosyasına ile eşleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="44806-203">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span>
<span data-ttu-id="44806-204">Bir sağlama toplamı oluşturmak için arama [yeni DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DscChecksum) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="44806-204">To create a checksum, call the [New-DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DscChecksum) cmdlet.</span></span>
<span data-ttu-id="44806-205">Cmdlet alır bir **yolu** parametresi yapılandırma MOF bulunduğu klasörü belirtir.</span><span class="sxs-lookup"><span data-stu-id="44806-205">The cmdlet takes a **Path** parameter that specifies the folder where the configuration MOF is located.</span></span>
<span data-ttu-id="44806-206">Adlı bir sağlama toplamı dosyasına cmdlet oluşturur `ConfigurationMOFName.mof.checksum`burada `ConfigurationMOFName` yapılandırma mof dosyasının adıdır.</span><span class="sxs-lookup"><span data-stu-id="44806-206">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span>
<span data-ttu-id="44806-207">Belirtilen klasörde MOF dosyaları birden fazla yapılandırması varsa, klasördeki her bir yapılandırma için bir sağlama toplamı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="44806-207">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span>
<span data-ttu-id="44806-208">MOF dosyaları ve bunların ilişkili sağlama toplamı dosyalarında yerleştirmek **Yapılandırmayolu** klasör.</span><span class="sxs-lookup"><span data-stu-id="44806-208">Place the MOF files and their associated checksum files in the **ConfigurationPath** folder.</span></span>

> [!NOTE]
> <span data-ttu-id="44806-209">Yapılandırma MOF dosyasının herhangi bir şekilde değiştirirseniz, sağlama toplamı dosyasına yeniden oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="44806-209">If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

### <a name="tooling"></a><span data-ttu-id="44806-210">Araç kullanımı</span><span class="sxs-lookup"><span data-stu-id="44806-210">Tooling</span></span>

<span data-ttu-id="44806-211">Ayarı yapmak için doğrulama ve daha kolay, çekme sunucusu yönetme aşağıdaki araçları xPSDesiredStateConfiguration modülünün en son sürümünü örneklerde olarak dahil edilir:</span><span class="sxs-lookup"><span data-stu-id="44806-211">In order to make setting up, validating and managing the pull server easier, the following tools are included as examples in the latest version of the xPSDesiredStateConfiguration module:</span></span>

1. <span data-ttu-id="44806-212">DSC kaynak modülleri ve çekme sunucusu kullanmak için yapılandırma dosyalarını paketleme ile yardımcı olacak bir modül.</span><span class="sxs-lookup"><span data-stu-id="44806-212">A module that will help with packaging DSC resource modules and configuration files for use on the pull server.</span></span>
   <span data-ttu-id="44806-213">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span><span class="sxs-lookup"><span data-stu-id="44806-213">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span></span>
   <span data-ttu-id="44806-214">Aşağıdaki örnekler:</span><span class="sxs-lookup"><span data-stu-id="44806-214">Examples below:</span></span>

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @('xWebAdministration', 'xPhp')
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. <span data-ttu-id="44806-215">Çekme sunucusu doğrulayan bir betik doğru şekilde yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="44806-215">A script that validates the pull server is configured correctly.</span></span> <span data-ttu-id="44806-216">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span><span class="sxs-lookup"><span data-stu-id="44806-216">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span></span>

## <a name="community-solutions-for-pull-service"></a><span data-ttu-id="44806-217">Topluluk çözümleriyle çekme hizmeti</span><span class="sxs-lookup"><span data-stu-id="44806-217">Community Solutions for Pull Service</span></span>

<span data-ttu-id="44806-218">Topluluk DSC çekme hizmeti Protokolü uygulamak için birden çok çözümü yazan.</span><span class="sxs-lookup"><span data-stu-id="44806-218">The DSC community has authored multiple solutions to implement the pull service protocol.</span></span>
<span data-ttu-id="44806-219">Şirket içi ortamlar için bu çekme hizmet özellikleri ve geri artımlı iyileştirmeleri topluluğa katkıda fırsatı sunar.</span><span class="sxs-lookup"><span data-stu-id="44806-219">For on-premises environments, these offer pull service capabilities and an opportunity to contribute back to the community with incremental enhancements.</span></span>

- [<span data-ttu-id="44806-220">Arasında bir güç çekişmesi</span><span class="sxs-lookup"><span data-stu-id="44806-220">Tug</span></span>](https://github.com/powershellorg/tug)
- [<span data-ttu-id="44806-221">DSC-TRÆK</span><span class="sxs-lookup"><span data-stu-id="44806-221">DSC-TRÆK</span></span>](https://github.com/powershellorg/dsc-traek)

## <a name="pull-client-configuration"></a><span data-ttu-id="44806-222">Çekme istemcisi yapılandırması</span><span class="sxs-lookup"><span data-stu-id="44806-222">Pull client configuration</span></span>

<span data-ttu-id="44806-223">Aşağıdaki konularda ayrıntılı çekme istemciler ayarlama açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="44806-223">The following topics describe setting up pull clients in detail:</span></span>

- [<span data-ttu-id="44806-224">Yapılandırma Kimliğini kullanarak bir DSC çekme istemcisi ayarlama</span><span class="sxs-lookup"><span data-stu-id="44806-224">Set up a DSC pull client using a configuration ID</span></span>](pullClientConfigID.md)
- [<span data-ttu-id="44806-225">Yapılandırma adlarını kullanarak bir DSC çekme istemcisi ayarlama</span><span class="sxs-lookup"><span data-stu-id="44806-225">Set up a DSC pull client using configuration names</span></span>](pullClientConfigNames.md)
- [<span data-ttu-id="44806-226">Kısmi yapılandırmalar</span><span class="sxs-lookup"><span data-stu-id="44806-226">Partial configurations</span></span>](partialConfigs.md)

## <a name="see-also"></a><span data-ttu-id="44806-227">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="44806-227">See also</span></span>

- [<span data-ttu-id="44806-228">Windows PowerShell Desired State Configuration ' ne genel bakış</span><span class="sxs-lookup"><span data-stu-id="44806-228">Windows PowerShell Desired State Configuration Overview</span></span>](../overview/overview.md)
- [<span data-ttu-id="44806-229">Yapılandırmaları Kabul Etme</span><span class="sxs-lookup"><span data-stu-id="44806-229">Enacting configurations</span></span>](enactingConfigurations.md)
- [<span data-ttu-id="44806-230">DSC rapor sunucusu kullanma</span><span class="sxs-lookup"><span data-stu-id="44806-230">Using a DSC report server</span></span>](reportServer.md)
- <span data-ttu-id="44806-231">[[MS-DSCPM]: Çekme modeli Protokolü Desired State Configuration](https://msdn.microsoft.com/library/dn393548.aspx)</span><span class="sxs-lookup"><span data-stu-id="44806-231">[[MS-DSCPM]: Desired State Configuration Pull Model Protocol](https://msdn.microsoft.com/library/dn393548.aspx)</span></span>
- <span data-ttu-id="44806-232">[[MS-DSCPM]: Çekme modeli Protokolü Errata Desired State Configuration](https://msdn.microsoft.com/library/mt612824.aspx)</span><span class="sxs-lookup"><span data-stu-id="44806-232">[[MS-DSCPM]: Desired State Configuration Pull Model Protocol Errata](https://msdn.microsoft.com/library/mt612824.aspx)</span></span>
