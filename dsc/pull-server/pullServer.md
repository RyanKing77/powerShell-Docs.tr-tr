---
ms.date: 03/04/2019
keywords: DSC, PowerShell, yapılandırma, kurulum
title: DSC Çekme Hizmeti
ms.openlocfilehash: 865eae5813e0c7b656a4158f0b1350e60f1e3291
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986533"
---
# <a name="desired-state-configuration-pull-service"></a><span data-ttu-id="48e50-103">İstenen durum yapılandırması çekme hizmeti</span><span class="sxs-lookup"><span data-stu-id="48e50-103">Desired State Configuration Pull Service</span></span>

> [!IMPORTANT]
> <span data-ttu-id="48e50-104">Çekme sunucusu (Windows özelliği *DSC-Service*) Windows Server 'ın desteklenen bir bileşenidir, ancak yeni özellikler veya yetenekler sunmaya yönelik bir plan yoktur.</span><span class="sxs-lookup"><span data-stu-id="48e50-104">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="48e50-105">Yönetilen istemcileri [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) geçirmeyi (Windows Server 'Da çekme sunucusunun ötesindeki özellikleri içerir) veya [burada](pullserver.md#community-solutions-for-pull-service)listelenen topluluk çözümlerinin birini kullanmaya başlamanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="48e50-105">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="48e50-106">Yerel Configuration Manager, bir çekme hizmeti çözümü tarafından merkezi olarak yönetilebilir.</span><span class="sxs-lookup"><span data-stu-id="48e50-106">Local Configuration Manager can be centrally managed by a Pull Service solution.</span></span>
<span data-ttu-id="48e50-107">Bu yaklaşımı kullanırken, yönetilmekte olan düğüm bir hizmete kaydedilir ve LCM ayarlarında bir yapılandırma atanır.</span><span class="sxs-lookup"><span data-stu-id="48e50-107">When using this approach, the node that is being managed is registered with a service and assigned a configuration in LCM settings.</span></span>
<span data-ttu-id="48e50-108">Yapılandırma bağımlılıkları olarak gereken yapılandırma ve tüm DSC kaynakları makineye indirilir ve bu yapılandırmayı yönetmek için LCM tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="48e50-108">The configuration and all DSC resources needed as dependencies for the configuration are downloaded to the machine and used by LCM to manage the configuration.</span></span>
<span data-ttu-id="48e50-109">Yönetilmekte olan makinenin durumu hakkında bilgi, raporlama için hizmete yüklenir.</span><span class="sxs-lookup"><span data-stu-id="48e50-109">Information about the state of the machine being managed is uploaded to the service for reporting.</span></span>
<span data-ttu-id="48e50-110">Bu kavram "çekme hizmeti" olarak anılacaktır.</span><span class="sxs-lookup"><span data-stu-id="48e50-110">This concept is referred to as "pull service."</span></span>

<span data-ttu-id="48e50-111">Çekme hizmeti için geçerli seçenekler şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="48e50-111">The current options for pull service include:</span></span>

- <span data-ttu-id="48e50-112">Azure Otomasyonu Istenen durum yapılandırma hizmeti</span><span class="sxs-lookup"><span data-stu-id="48e50-112">Azure Automation Desired State Configuration service</span></span>
- <span data-ttu-id="48e50-113">Windows Server üzerinde çalışan bir çekme hizmeti</span><span class="sxs-lookup"><span data-stu-id="48e50-113">A pull service running on Windows Server</span></span>
- <span data-ttu-id="48e50-114">Topluluk tarafından tutulan açık kaynaklı çözümler</span><span class="sxs-lookup"><span data-stu-id="48e50-114">Community maintained open-source solutions</span></span>
- <span data-ttu-id="48e50-115">Bir SMB paylaşma</span><span class="sxs-lookup"><span data-stu-id="48e50-115">An SMB share</span></span>

<span data-ttu-id="48e50-116">**Önerilen çözüm**ve en fazla özelliklerle sunulan seçenek [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span><span class="sxs-lookup"><span data-stu-id="48e50-116">**The recommended solution**, and the option with the most features available, is [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span></span>

<span data-ttu-id="48e50-117">Azure hizmeti, şirket içi düğümleri özel veri merkezlerinde veya Azure ve AWS gibi genel bulutlarda yönetebilir.</span><span class="sxs-lookup"><span data-stu-id="48e50-117">The Azure service can manage nodes on-premises in private datacenters, or in public clouds such as Azure and AWS.</span></span>
<span data-ttu-id="48e50-118">Sunucularının Internet 'e doğrudan bağlanamamakta olduğu özel ortamlar için, giden trafiği yalnızca yayımlanan Azure IP aralığıyla sınırlamayı düşünün (bkz. [Azure veri MERKEZI IP aralıkları](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).</span><span class="sxs-lookup"><span data-stu-id="48e50-118">For private environments where servers cannot directly connect to the Internet, consider limiting outbound traffic to only the published Azure IP range (see [Azure Datacenter IP Ranges](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).</span></span>

<span data-ttu-id="48e50-119">Windows Server 'da çekme hizmetinde şu anda kullanılamayan çevrimiçi hizmetin özellikleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="48e50-119">Features of the online service that are not currently available in the pull service on Windows Server include:</span></span>

- <span data-ttu-id="48e50-120">Tüm veriler aktarım sırasında ve bekleyen saatinde şifrelenir</span><span class="sxs-lookup"><span data-stu-id="48e50-120">All data is encrypted in transit and at rest</span></span>
- <span data-ttu-id="48e50-121">İstemci sertifikaları otomatik olarak oluşturulur ve yönetilir</span><span class="sxs-lookup"><span data-stu-id="48e50-121">Client certificates are created and managed automatically</span></span>
- <span data-ttu-id="48e50-122">[Parolaları/kimlik bilgilerini](/azure/automation/automation-credentials)ya da sunucu adları veya bağlantı dizeleri gibi [değişkenleri](/azure/automation/automation-variables) merkezi olarak yönetmek için gizli dizileri depolar</span><span class="sxs-lookup"><span data-stu-id="48e50-122">Secrets store for centrally managing [passwords/credentials](/azure/automation/automation-credentials), or [variables](/azure/automation/automation-variables) such as server names or connection strings</span></span>
- <span data-ttu-id="48e50-123">Düğüm [LCM yapılandırmasını](../managing-nodes/metaConfig.md#basic-settings) merkezi olarak Yönet</span><span class="sxs-lookup"><span data-stu-id="48e50-123">Centrally manage node [LCM configuration](../managing-nodes/metaConfig.md#basic-settings)</span></span>
- <span data-ttu-id="48e50-124">İstemci düğümlerine yapılandırma merkezi olarak atama</span><span class="sxs-lookup"><span data-stu-id="48e50-124">Centrally assign configurations to client nodes</span></span>
- <span data-ttu-id="48e50-125">Üretime ulaşmadan önce test için "Canary gruplarında" yayın yapılandırması değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="48e50-125">Release configuration changes to "canary groups" for testing before reaching production</span></span>
- <span data-ttu-id="48e50-126">Grafik raporlama</span><span class="sxs-lookup"><span data-stu-id="48e50-126">Graphical reporting</span></span>
  - <span data-ttu-id="48e50-127">Ayrıntı düzeyi DSC kaynak düzeyinde durum ayrıntısı</span><span class="sxs-lookup"><span data-stu-id="48e50-127">Status detail at the DSC resource level of granularity</span></span>
  - <span data-ttu-id="48e50-128">Sorun giderme için istemci makinelerden ayrıntılı hata iletileri</span><span class="sxs-lookup"><span data-stu-id="48e50-128">Verbose error messages from client machines for troubleshooting</span></span>
- <span data-ttu-id="48e50-129">Raporlama ve uyarı için Azure Log Analytics uyarı, otomatikleştirilmiş görevler, Android/iOS uygulaması [Ile tümleştirme](/azure/automation/automation-dsc-diagnostics)</span><span class="sxs-lookup"><span data-stu-id="48e50-129">[Integration with Azure Log Analytics](/azure/automation/automation-dsc-diagnostics) for alerting, automated tasks, Android/iOS app for reporting and alerting</span></span>

## <a name="dsc-pull-service-in-windows-server"></a><span data-ttu-id="48e50-130">Windows Server 'da DSC çekme hizmeti</span><span class="sxs-lookup"><span data-stu-id="48e50-130">DSC pull service in Windows Server</span></span>

<span data-ttu-id="48e50-131">Bir çekme hizmetini Windows Server 'da çalışacak şekilde yapılandırmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="48e50-131">It is possible to configure a pull service to run on Windows Server.</span></span>
<span data-ttu-id="48e50-132">Windows Server 'a dahil olan çekme hizmeti çözümünün yalnızca yapılandırma ve rapor verilerini veritabanına yükleme için depolama yeteneklerini içermesi önerilir.</span><span class="sxs-lookup"><span data-stu-id="48e50-132">Be advised that the pull service solution included in Windows Server includes only capabilities of storing configurations/modules for download and capturing report data in to database.</span></span>
<span data-ttu-id="48e50-133">Azure 'da hizmetin sunduğu birçok özelliği içermez ve bu nedenle hizmetin nasıl kullanılacağını değerlendirmek için iyi bir araç değildir.</span><span class="sxs-lookup"><span data-stu-id="48e50-133">It does not include many of the capabilities offered by the service in Azure and so is not a good tool for evaluating how the service would be used.</span></span>

<span data-ttu-id="48e50-134">Windows Server 'da sunulan çekme hizmeti, bir OData arabirimi kullanan bir Web hizmetidir ve bu düğümler, bu düğümleri isteyenler için DSC yapılandırma dosyalarını hedef düğümlere kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="48e50-134">The pull service offered in Windows Server is a web service in IIS that uses an OData interface to make DSC configuration files available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="48e50-135">Çekme sunucusu kullanma gereksinimleri:</span><span class="sxs-lookup"><span data-stu-id="48e50-135">Requirements for using a pull server:</span></span>

- <span data-ttu-id="48e50-136">Çalıştıran bir sunucu:</span><span class="sxs-lookup"><span data-stu-id="48e50-136">A server running:</span></span>
  - <span data-ttu-id="48e50-137">WMF/PowerShell 4,0 veya üzeri</span><span class="sxs-lookup"><span data-stu-id="48e50-137">WMF/PowerShell 4.0 or greater</span></span>
  - <span data-ttu-id="48e50-138">IIS sunucu rolü</span><span class="sxs-lookup"><span data-stu-id="48e50-138">IIS server role</span></span>
  - <span data-ttu-id="48e50-139">DSC hizmeti</span><span class="sxs-lookup"><span data-stu-id="48e50-139">DSC Service</span></span>
- <span data-ttu-id="48e50-140">Hedef düğümlerde yerel Configuration Manager (LCM) geçirilen kimlik bilgilerinin güvenliğini sağlamak için bir sertifika oluşturmanın bazı yolları idealdir.</span><span class="sxs-lookup"><span data-stu-id="48e50-140">Ideally, some means of generating a certificate, to secure credentials passed to the Local Configuration Manager (LCM) on target nodes</span></span>

<span data-ttu-id="48e50-141">Windows Server 'ı çekme hizmetini barındıracak şekilde yapılandırmanın en iyi yolu DSC yapılandırması kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="48e50-141">The best way to configure Windows Server to host pull service is to use a DSC configuration.</span></span>
<span data-ttu-id="48e50-142">Aşağıda örnek bir komut dosyası verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="48e50-142">An example script is provided below.</span></span>

### <a name="supported-database-systems"></a><span data-ttu-id="48e50-143">Desteklenen veritabanı sistemleri</span><span class="sxs-lookup"><span data-stu-id="48e50-143">Supported database systems</span></span>

|<span data-ttu-id="48e50-144">WMF 4,0</span><span class="sxs-lookup"><span data-stu-id="48e50-144">WMF 4.0</span></span>   |<span data-ttu-id="48e50-145">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="48e50-145">WMF 5.0</span></span>  |<span data-ttu-id="48e50-146">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="48e50-146">WMF 5.1</span></span> |<span data-ttu-id="48e50-147">WMF 5,1 (Windows Server Insider Preview 17090)</span><span class="sxs-lookup"><span data-stu-id="48e50-147">WMF 5.1 (Windows Server Insider Preview 17090)</span></span>|
|---------|---------|---------|---------|
|<span data-ttu-id="48e50-148">TATIL</span><span class="sxs-lookup"><span data-stu-id="48e50-148">MDB</span></span>     |<span data-ttu-id="48e50-149">ESENT (varsayılan), MDB</span><span class="sxs-lookup"><span data-stu-id="48e50-149">ESENT (Default), MDB</span></span> |<span data-ttu-id="48e50-150">ESENT (varsayılan), MDB</span><span class="sxs-lookup"><span data-stu-id="48e50-150">ESENT (Default), MDB</span></span>|<span data-ttu-id="48e50-151">ESENT (varsayılan), SQL Server, MDB</span><span class="sxs-lookup"><span data-stu-id="48e50-151">ESENT (Default), SQL Server, MDB</span></span>

<span data-ttu-id="48e50-152">[Windows Server Insider Preview](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewserver)sürüm 17090 ' den başlayarak, çekme hizmeti (Windows özelliği *DSC-Service*) için desteklenen bir seçenektir SQL Server.</span><span class="sxs-lookup"><span data-stu-id="48e50-152">Starting in release 17090 of [Windows Server Insider Preview](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewserver), SQL Server is a supported option for the Pull Service (Windows Feature *DSC-Service*).</span></span> <span data-ttu-id="48e50-153">Bu, [Azure Automation DSC](/azure/automation/automation-dsc-getting-started)'e geçirilmeyen büyük DSC ortamlarını ölçeklendirmek için yeni bir seçenek sağlar.</span><span class="sxs-lookup"><span data-stu-id="48e50-153">This provides a new option for scaling large DSC environments that have not migrated to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span></span>

> [!NOTE]
> <span data-ttu-id="48e50-154">SQL Server desteği, WMF 5,1 (veya önceki bir sürümü) önceki sürümlerine eklenmez ve yalnızca 17090 ' den büyük veya buna eşit olan Windows Server sürümlerinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="48e50-154">SQL Server support will not be added to previous versions of WMF 5.1 (or earlier) and will only be available on Windows Server versions greater than or equal to 17090.</span></span>

<span data-ttu-id="48e50-155">Çekme sunucusunu SQL Server kullanacak şekilde yapılandırmak için, **SqlProvider** `$true` ' ı ve **sqlConnectionString** ' i geçerli bir SQL Server bağlantı dizesine ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="48e50-155">To configure the pull server to use SQL Server, set **SqlProvider** to `$true` and **SqlConnectionString** to a valid SQL Server Connection String.</span></span> <span data-ttu-id="48e50-156">Daha fazla bilgi için bkz. [SqlClient bağlantı dizeleri](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings).</span><span class="sxs-lookup"><span data-stu-id="48e50-156">For more information, see [SqlClient Connection Strings](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings).</span></span>
<span data-ttu-id="48e50-157">**Xdscwebservice**ile SQL Server yapılandırmasına bir örnek için Ilk olarak [xdscwebservice kaynağını kullanarak](#using-the-xdscwebservice-resource) okuyun ve ardından [GitHub 'da Sample_xDscWebServiceRegistration_UseSQLProvider. ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1)' yi inceleyin.</span><span class="sxs-lookup"><span data-stu-id="48e50-157">For an example of SQL Server configuration with **xDscWebService**, first read [Using the xDscWebService resource](#using-the-xdscwebservice-resource) and then review [Sample_xDscWebServiceRegistration_UseSQLProvider.ps1 on GitHub](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1).</span></span>

### <a name="using-the-xdscwebservice-resource"></a><span data-ttu-id="48e50-158">XDscWebService kaynağını kullanma</span><span class="sxs-lookup"><span data-stu-id="48e50-158">Using the xDscWebService resource</span></span>

<span data-ttu-id="48e50-159">Bir Web çekme sunucusu ayarlamanın en kolay yolu, **Xpsdesiredstateconfiguration** modülüne dahil edilen **xdscwebservice** kaynağını kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="48e50-159">The easiest way to set up a web pull server is to use the **xDscWebService** resource, included in the **xPSDesiredStateConfiguration** module.</span></span>
<span data-ttu-id="48e50-160">Aşağıdaki adımlarda, kaynağı Web hizmetini ayarlayan bir yapılandırmada kullanma açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="48e50-160">The following steps explain how to use the resource in a configuration that sets up the web service.</span></span>

1. <span data-ttu-id="48e50-161">**Xpsdesiredstateconfiguration** modülünü yüklemek için [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet 'ini çağırın.</span><span class="sxs-lookup"><span data-stu-id="48e50-161">Call the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to install the **xPSDesiredStateConfiguration** module.</span></span>
   > [!NOTE]
   > <span data-ttu-id="48e50-162">**Install-Module** , PowerShell 5,0 ' de bulunan **PowerShellGet** modülüne dahildir.</span><span class="sxs-lookup"><span data-stu-id="48e50-162">**Install-Module** is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="48e50-163">PowerShell 3,0 ve 4,0 için **PowerShellGet** modülünü [PackageManagement PowerShell modülleri önizlemesine](https://www.microsoft.com/en-us/download/details.aspx?id=49186)indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="48e50-163">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span>
2. <span data-ttu-id="48e50-164">Kuruluşunuzun içinde veya genel yetkilinizden, güvenilir bir sertifika yetkilisinden DSC çekme sunucusu için bir SSL sertifikası alın.</span><span class="sxs-lookup"><span data-stu-id="48e50-164">Get an SSL certificate for the DSC Pull server from a trusted Certificate Authority, either within your organization or a public authority.</span></span> <span data-ttu-id="48e50-165">Yetkilinden alınan sertifika genellikle PFX biçimindedir.</span><span class="sxs-lookup"><span data-stu-id="48e50-165">The certificate received from the authority is usually in the PFX format.</span></span>
3. <span data-ttu-id="48e50-166">Varsayılan konumda `CERT:\LocalMachine\My`DSC çekme sunucusu olacak olan düğüme sertifikayı yükler.</span><span class="sxs-lookup"><span data-stu-id="48e50-166">Install the certificate on the node that will become the DSC Pull server in the default location, which should be `CERT:\LocalMachine\My`.</span></span>
   - <span data-ttu-id="48e50-167">Sertifika parmak izini bir yere getirin.</span><span class="sxs-lookup"><span data-stu-id="48e50-167">Make a note of the certificate thumbprint.</span></span>
4. <span data-ttu-id="48e50-168">Kayıt anahtarı olarak kullanılacak bir GUID seçin.</span><span class="sxs-lookup"><span data-stu-id="48e50-168">Select a GUID to be used as the Registration Key.</span></span> <span data-ttu-id="48e50-169">PowerShell kullanarak bir tane oluşturmak için PS isteminde aşağıdakini girin ve ENTER tuşuna basın: `[guid]::newGuid()` veya. `New-Guid`</span><span class="sxs-lookup"><span data-stu-id="48e50-169">To generate one using PowerShell enter the following at the PS prompt and press enter: `[guid]::newGuid()` or `New-Guid`.</span></span> <span data-ttu-id="48e50-170">Bu anahtar, kayıt sırasında kimlik doğrulaması için paylaşılan anahtar olarak istemci düğümleri tarafından kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="48e50-170">This key will be used by client nodes as a shared key to authenticate during registration.</span></span> <span data-ttu-id="48e50-171">Daha fazla bilgi için aşağıdaki kayıt anahtarı bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="48e50-171">For more information, see the Registration Key section below.</span></span>
5. <span data-ttu-id="48e50-172">PowerShell ıSE 'de, aşağıdaki yapılandırma betiğini (F5) başlatın ( **Xpsdesiredstateconfiguration** modülünün `Sample_xDscWebServiceRegistration.ps1`örnekler klasörüne dahil).</span><span class="sxs-lookup"><span data-stu-id="48e50-172">In the PowerShell ISE, start (F5) the following configuration script (included in the Examples folder of the **xPSDesiredStateConfiguration** module as `Sample_xDscWebServiceRegistration.ps1`).</span></span> <span data-ttu-id="48e50-173">Bu betik, çekme sunucusunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="48e50-173">This script sets up the pull server.</span></span>

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

6. <span data-ttu-id="48e50-174">SSL sertifikasının parmak izini **certificateThumbPrint** parametresi olarak ve bir GUID kayıt anahtarını **registrationkey** parametresi olarak geçirerek yapılandırmayı çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="48e50-174">Run the configuration, passing the thumbprint of the SSL certificate as the **certificateThumbPrint** parameter and a GUID registration key as the **RegistrationKey** parameter:</span></span>

    ```powershell
    # To find the Thumbprint for an installed SSL certificate for use with the pull server list all certificates in your local store
    # and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
    dir Cert:\LocalMachine\my

    # Then include this thumbprint when running the configuration
    Sample_xDscWebServiceRegistration -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutputPath c:\Configs\PullServer

    # Run the compiled configuration to make the target node a DSC Pull Server
    Start-DscConfiguration -Path c:\Configs\PullServer -Wait -Verbose
    ```

#### <a name="registration-key"></a><span data-ttu-id="48e50-175">Kayıt anahtarı</span><span class="sxs-lookup"><span data-stu-id="48e50-175">Registration Key</span></span>

<span data-ttu-id="48e50-176">İstemci düğümlerinin bir yapılandırma kimliği yerine yapılandırma adlarını kullanabilmesi için sunucuya kaydedilmesine izin vermek üzere, yukarıdaki yapılandırma tarafından oluşturulan bir kayıt anahtarı içinde `RegistrationKeys.txt` `C:\Program Files\WindowsPowerShell\DscService`adlı bir dosyaya kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="48e50-176">To allow client nodes to register with the server so that they can use configuration names instead of a configuration ID, a registration key that was created by the above configuration is saved in a file named `RegistrationKeys.txt` in `C:\Program Files\WindowsPowerShell\DscService`.</span></span> <span data-ttu-id="48e50-177">Kayıt anahtarı, istemci tarafından çekme sunucusuna ilk kayıt sırasında kullanılan bir paylaşılan gizli dizi olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="48e50-177">The registration key functions as a shared secret used during the initial registration by the client with the pull server.</span></span> <span data-ttu-id="48e50-178">İstemci, kayıt başarıyla tamamlandıktan sonra çekme sunucusuna benzersiz olarak kimlik doğrulaması yapmak için kullanılan otomatik olarak imzalanan bir sertifika oluşturur.</span><span class="sxs-lookup"><span data-stu-id="48e50-178">The client will generate a self-signed certificate that is used to uniquely authenticate to the pull server once registration is successfully completed.</span></span> <span data-ttu-id="48e50-179">Bu sertifikanın parmak izi yerel olarak depolanır ve çekme sunucusunun URL 'SI ile ilişkilendirilir.</span><span class="sxs-lookup"><span data-stu-id="48e50-179">The thumbprint of this certificate is stored locally and associated with the URL of the pull server.</span></span>

> [!NOTE]
> <span data-ttu-id="48e50-180">Kayıt anahtarları PowerShell 4,0 ' de desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="48e50-180">Registration keys are not supported in PowerShell 4.0.</span></span>

<span data-ttu-id="48e50-181">Bir düğümü, çekme sunucusunda kimlik doğrulaması yapacak şekilde yapılandırmak için, kayıt anahtarının bu çekme sunucusuna kaydedilecek herhangi bir hedef düğüm için metaconfiguration içinde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="48e50-181">In order to configure a node to authenticate with the pull server, the registration key needs to be in the metaconfiguration for any target node that will be registering with this pull server.</span></span> <span data-ttu-id="48e50-182">Aşağıdaki metaconfiguration içindeki **registrationkey** 'in, hedef makine başarıyla kaydedildikten sonra kaldırıldığını ve değerin çekme sunucusundaki `RegistrationKeys.txt` dosyasında depolanan değerle eşleşmesi gerektiğini unutmayın (' 140a952b-b9d6-406b-B416-e0f759c9c0e4 ' Bu örnek için).</span><span class="sxs-lookup"><span data-stu-id="48e50-182">Note that the **RegistrationKey** in the metaconfiguration below is removed after the target machine has successfully registered, and that the value must match the value stored in the `RegistrationKeys.txt` file on the pull server ('140a952b-b9d6-406b-b416-e0f759c9c0e4' for this example).</span></span> <span data-ttu-id="48e50-183">Her zaman, tüm hedef makinelerin çekme sunucusuna kaydedilmesine izin verdiğini bilerek, kayıt anahtarı değerini güvenli şekilde değerlendirin.</span><span class="sxs-lookup"><span data-stu-id="48e50-183">Always treat the registration key value securely, because knowing it allows any target machine to register with the pull server.</span></span>

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
> <span data-ttu-id="48e50-184">**Reportserverweb** bölümü raporlama verilerinin çekme sunucusuna gönderilmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="48e50-184">The **ReportServerWeb** section allows reporting data to be sent to the pull server.</span></span>

<span data-ttu-id="48e50-185">Metaconfiguration dosyasındaki **ConfigurationId** özelliğinin olmaması, çekme sunucusunun, çekme sunucusu protokolünün v2 sürümünü, bu nedenle bir ilk kaydın gerekli olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="48e50-185">The lack of the **ConfigurationID** property in the metaconfiguration file implicitly means that pull server is supporting the V2 version of the pull server protocol so an initial registration is required.</span></span>
<span data-ttu-id="48e50-186">Buna karşılık, bir **ConfigurationId** varlığı, çekme sunucusu protokolünün v1 sürümünün kullanıldığı ve kayıt işlemenin bulunmadığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="48e50-186">Conversely, the presence of a **ConfigurationID** means that the V1 version of the pull server protocol is used and there is no registration processing.</span></span>

> [!NOTE]
> <span data-ttu-id="48e50-187">Bir gönderme senaryosunda, geçerli yayında bir hata var ve bu, bir çekme sunucusuna hiç kaydedilmemiş düğümler için metaconfiguration dosyasında bir ConfigurationId özelliği tanımlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="48e50-187">In a PUSH scenario, a bug exists in the current release that makes it necessary to define a ConfigurationID property in the metaconfiguration file for nodes that have never registered with a pull server.</span></span> <span data-ttu-id="48e50-188">Bu, v1 çekme sunucusu protokolünü zorlar ve kayıt hatası iletilerini önler.</span><span class="sxs-lookup"><span data-stu-id="48e50-188">This will force the V1 Pull Server protocol and avoid registration failure messages.</span></span>

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="48e50-189">Yapılandırma ve kaynakları yerleştirme</span><span class="sxs-lookup"><span data-stu-id="48e50-189">Placing configurations and resources</span></span>

<span data-ttu-id="48e50-190">Çekme sunucusu kurulumu tamamlandıktan sonra, çekme sunucusu yapılandırmasındaki **ConfigurationPath** ve **ModulePath** özellikleri tarafından tanımlanan klasörler, hedef düğümlerin çekmesini sağlamak için kullanılabilecek modülleri ve yapılandırmaları yerleştireceğiniz yerdir.</span><span class="sxs-lookup"><span data-stu-id="48e50-190">After the pull server setup completes, the folders defined by the **ConfigurationPath** and **ModulePath** properties in the pull server configuration are where you will place modules and configurations that will be available for target nodes to pull.</span></span>
<span data-ttu-id="48e50-191">Bu dosyaların, çekme sunucusunun düzgün şekilde işlemesi için belirli bir biçimde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="48e50-191">These files need to be in a specific format in order for the pull server to correctly process them.</span></span>

### <a name="dsc-resource-module-package-format"></a><span data-ttu-id="48e50-192">DSC kaynak modülü paket biçimi</span><span class="sxs-lookup"><span data-stu-id="48e50-192">DSC resource module package format</span></span>

<span data-ttu-id="48e50-193">Her kaynak modülünün sıkıştırılmış ve aşağıdaki modele `{Module Name}_{Module Version}.zip`göre adlandırılmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="48e50-193">Each resource module needs to be zipped and named according to the following pattern `{Module Name}_{Module Version}.zip`.</span></span>

<span data-ttu-id="48e50-194">Örneğin, xWebAdminstration adlı bir modülün Modül sürümü 3.1.2.0 olarak adlandırılır `xWebAdministration_3.1.2.0.zip`.</span><span class="sxs-lookup"><span data-stu-id="48e50-194">For example, a module named xWebAdminstration with a module version of 3.1.2.0 would be named `xWebAdministration_3.1.2.0.zip`.</span></span>
<span data-ttu-id="48e50-195">Modülün her sürümü tek bir ZIP dosyasında bulunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="48e50-195">Each version of a module must be contained in a single zip file.</span></span>
<span data-ttu-id="48e50-196">Her ZIP dosyasında bir kaynağın yalnızca tek bir sürümü olduğundan, WMF 5,0 ' de tek bir dizinde birden çok modül sürümü desteğiyle eklenen modül biçimi desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="48e50-196">Since there is only a single version of a resource in each zip file, the module format added in WMF 5.0 with support for multiple module versions in a single directory is not supported.</span></span>
<span data-ttu-id="48e50-197">Diğer bir deyişle, çekme sunucusu ile kullanım için DSC kaynak modüllerini paketlemeden önce dizin yapısında küçük bir değişiklik yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="48e50-197">This means that before packaging up DSC resource modules for use with pull server you will need to make a small change to the directory structure.</span></span>
<span data-ttu-id="48e50-198">WMF 5,0 ' de DSC kaynağını içeren modüllerin varsayılan biçimi vardır `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.</span><span class="sxs-lookup"><span data-stu-id="48e50-198">The default format of modules containing DSC resource in WMF 5.0 is `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.</span></span>
<span data-ttu-id="48e50-199">Çekme sunucusuna paketlemeden önce, yol haline `{Module Folder}\DscResources\{DSC Resource Folder}\`gelmesi için **{module sürümü}** klasörünü kaldırın.</span><span class="sxs-lookup"><span data-stu-id="48e50-199">Before packaging up for the pull server, remove the **{Module version}** folder so the path becomes `{Module Folder}\DscResources\{DSC Resource Folder}\`.</span></span>
<span data-ttu-id="48e50-200">Bu değişiklik ile, yukarıda açıklandığı gibi klasörü zip halinde ve bu ZIP dosyalarını **ModulePath** klasörüne yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="48e50-200">With this change, zip the folder as described above and place these zip files in the **ModulePath** folder.</span></span>

<span data-ttu-id="48e50-201">Yeni `New-DscChecksum {module zip file}` eklenen modül için bir sağlama toplamı dosyası oluşturmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="48e50-201">Use `New-DscChecksum {module zip file}` to create a checksum file for the newly added module.</span></span>

### <a name="configuration-mof-format"></a><span data-ttu-id="48e50-202">Yapılandırma MOF biçimi</span><span class="sxs-lookup"><span data-stu-id="48e50-202">Configuration MOF format</span></span>

<span data-ttu-id="48e50-203">Bir hedef düğümdeki LCM 'nin yapılandırmayı doğrulayabilmesi için bir yapılandırma MOF dosyasının bir sağlama toplamı dosyasıyla eşleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="48e50-203">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span>
<span data-ttu-id="48e50-204">Sağlama toplamı oluşturmak için [New-DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DscChecksum) cmdlet 'ini çağırın.</span><span class="sxs-lookup"><span data-stu-id="48e50-204">To create a checksum, call the [New-DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DscChecksum) cmdlet.</span></span>
<span data-ttu-id="48e50-205">Cmdlet 'i, yapılandırma MOF 'nin bulunduğu klasörü belirten bir **yol** parametresi alır.</span><span class="sxs-lookup"><span data-stu-id="48e50-205">The cmdlet takes a **Path** parameter that specifies the folder where the configuration MOF is located.</span></span>
<span data-ttu-id="48e50-206">Cmdlet 'i adlı `ConfigurationMOFName.mof.checksum`bir sağlama toplamı dosyası oluşturur, `ConfigurationMOFName` burada yapılandırma mof dosyasının adıdır.</span><span class="sxs-lookup"><span data-stu-id="48e50-206">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span>
<span data-ttu-id="48e50-207">Belirtilen klasörde birden fazla yapılandırma MOF dosyası varsa, klasördeki her bir yapılandırma için bir sağlama toplamı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="48e50-207">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span>
<span data-ttu-id="48e50-208">MOF dosyalarını ve ilgili sağlama toplamı dosyalarını **ConfigurationPath** klasörüne yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="48e50-208">Place the MOF files and their associated checksum files in the **ConfigurationPath** folder.</span></span>

> [!NOTE]
> <span data-ttu-id="48e50-209">Yapılandırma MOF dosyasını herhangi bir şekilde değiştirirseniz, sağlama toplamı dosyasını da yeniden oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="48e50-209">If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

### <a name="tooling"></a><span data-ttu-id="48e50-210">Araçları</span><span class="sxs-lookup"><span data-stu-id="48e50-210">Tooling</span></span>

<span data-ttu-id="48e50-211">İstek sunucusunu ayarlamayı, doğrulamayı ve yönetmeyi kolaylaştırmak için aşağıdaki araçlar xPSDesiredStateConfiguration modülünün en son sürümüne örnek olarak dahil edilir:</span><span class="sxs-lookup"><span data-stu-id="48e50-211">In order to make setting up, validating and managing the pull server easier, the following tools are included as examples in the latest version of the xPSDesiredStateConfiguration module:</span></span>

1. <span data-ttu-id="48e50-212">Çekme sunucusunda kullanılmak üzere DSC kaynak modüllerinin ve yapılandırma dosyalarının paketlenmesi için yardımcı olacak bir modül.</span><span class="sxs-lookup"><span data-stu-id="48e50-212">A module that will help with packaging DSC resource modules and configuration files for use on the pull server.</span></span>
   <span data-ttu-id="48e50-213">[PublishModulesAndMofsToPullServer. psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span><span class="sxs-lookup"><span data-stu-id="48e50-213">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span></span>
   <span data-ttu-id="48e50-214">Aşağıdaki örnekler:</span><span class="sxs-lookup"><span data-stu-id="48e50-214">Examples below:</span></span>

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @('xWebAdministration', 'xPhp')
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. <span data-ttu-id="48e50-215">Çekme sunucusunu doğrulayan bir betik doğru şekilde yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="48e50-215">A script that validates the pull server is configured correctly.</span></span> <span data-ttu-id="48e50-216">[Pullserversetuptests. ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span><span class="sxs-lookup"><span data-stu-id="48e50-216">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span></span>

## <a name="community-solutions-for-pull-service"></a><span data-ttu-id="48e50-217">Çekme hizmeti için topluluk çözümleri</span><span class="sxs-lookup"><span data-stu-id="48e50-217">Community Solutions for Pull Service</span></span>

<span data-ttu-id="48e50-218">DSC topluluğu, çekme hizmeti protokolünü uygulamak için birden çok çözüm yazdı.</span><span class="sxs-lookup"><span data-stu-id="48e50-218">The DSC community has authored multiple solutions to implement the pull service protocol.</span></span>
<span data-ttu-id="48e50-219">Şirket içi ortamlar için, bu teklif çekme hizmeti özellikleri ve artımlı geliştirmeler sayesinde topluluğa katkıda bulunmak için bir fırsat sunar.</span><span class="sxs-lookup"><span data-stu-id="48e50-219">For on-premises environments, these offer pull service capabilities and an opportunity to contribute back to the community with incremental enhancements.</span></span>

- [<span data-ttu-id="48e50-220">Tug</span><span class="sxs-lookup"><span data-stu-id="48e50-220">Tug</span></span>](https://github.com/powershellorg/tug)
- [<span data-ttu-id="48e50-221">DSC-TRÆK</span><span class="sxs-lookup"><span data-stu-id="48e50-221">DSC-TRÆK</span></span>](https://github.com/powershellorg/dsc-traek)

## <a name="pull-client-configuration"></a><span data-ttu-id="48e50-222">İstek temelli istemci yapılandırması</span><span class="sxs-lookup"><span data-stu-id="48e50-222">Pull client configuration</span></span>

<span data-ttu-id="48e50-223">Aşağıdaki konularda, çekme istemcilerinin ayrıntılı olarak ayarlanması açıklanır:</span><span class="sxs-lookup"><span data-stu-id="48e50-223">The following topics describe setting up pull clients in detail:</span></span>

- [<span data-ttu-id="48e50-224">Bir DSC çekme istemcisini yapılandırma KIMLIĞI kullanarak ayarlama</span><span class="sxs-lookup"><span data-stu-id="48e50-224">Set up a DSC pull client using a configuration ID</span></span>](pullClientConfigID.md)
- [<span data-ttu-id="48e50-225">Yapılandırma adlarını kullanarak DSC çekme istemcisini ayarlama</span><span class="sxs-lookup"><span data-stu-id="48e50-225">Set up a DSC pull client using configuration names</span></span>](pullClientConfigNames.md)
- [<span data-ttu-id="48e50-226">Kısmi yapılandırma</span><span class="sxs-lookup"><span data-stu-id="48e50-226">Partial configurations</span></span>](partialConfigs.md)

## <a name="see-also"></a><span data-ttu-id="48e50-227">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="48e50-227">See also</span></span>

- [<span data-ttu-id="48e50-228">Windows PowerShell Istenen durum yapılandırmasına genel bakış</span><span class="sxs-lookup"><span data-stu-id="48e50-228">Windows PowerShell Desired State Configuration Overview</span></span>](../overview/overview.md)
- [<span data-ttu-id="48e50-229">Yapılandırmaları Kabul Etme</span><span class="sxs-lookup"><span data-stu-id="48e50-229">Enacting configurations</span></span>](enactingConfigurations.md)
- [<span data-ttu-id="48e50-230">DSC rapor sunucusu kullanma</span><span class="sxs-lookup"><span data-stu-id="48e50-230">Using a DSC report server</span></span>](reportServer.md)
- <span data-ttu-id="48e50-231">[[MS-DSCPM]: İstenen durum yapılandırması Istek modeli Protokolü](https://msdn.microsoft.com/library/dn393548.aspx)</span><span class="sxs-lookup"><span data-stu-id="48e50-231">[[MS-DSCPM]: Desired State Configuration Pull Model Protocol](https://msdn.microsoft.com/library/dn393548.aspx)</span></span>
- <span data-ttu-id="48e50-232">[[MS-DSCPM]: İstenen durum yapılandırması Istek modeli protokol Eroytası](https://msdn.microsoft.com/library/mt612824.aspx)</span><span class="sxs-lookup"><span data-stu-id="48e50-232">[[MS-DSCPM]: Desired State Configuration Pull Model Protocol Errata](https://msdn.microsoft.com/library/mt612824.aspx)</span></span>
