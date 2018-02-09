---
ms.date: 2018-02-02
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: DSC Pull Service
ms.openlocfilehash: d5e24dcc093c73d8ebbaa618517193dacc4f2aaf
ms.sourcegitcommit: 755d7bc0740573d73613cedcf79981ca3dc81c5e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2018
---
# <a name="desired-state-configuration-pull-service"></a><span data-ttu-id="9ba2c-103">İstenen durum yapılandırma çekme hizmeti</span><span class="sxs-lookup"><span data-stu-id="9ba2c-103">Desired State Configuration Pull Service</span></span>

> <span data-ttu-id="9ba2c-104">İçin geçerlidir: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="9ba2c-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="9ba2c-105">Yerel Configuration Manager, bir çekme hizmet çözümü tarafından merkezi olarak yönetilebilir.</span><span class="sxs-lookup"><span data-stu-id="9ba2c-105">Local Configuration Manager can be centrally managed by a Pull Service solution.</span></span>
<span data-ttu-id="9ba2c-106">Bu yaklaşımı kullanarak, yönetilmekte olan düğüm bir hizmete kayıtlı ve yapılandırma LCM'yi ayarlarında atanmış.</span><span class="sxs-lookup"><span data-stu-id="9ba2c-106">When using this approach, the node that is being managed is registered with a service and assigned a configuration in LCM settings.</span></span>
<span data-ttu-id="9ba2c-107">Yapılandırma ve bağımlılık yapılandırması için gereken tüm DSC kaynakları makineye indirilir ve yapılandırmasını yönetmek için LCM'yi tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9ba2c-107">The configuration and all DSC resources needed as dependencies for the configuration are downloaded to the machine and used by LCM to manage the configuration.</span></span>
<span data-ttu-id="9ba2c-108">Yönetilen makinenin durumu hakkında bilgi, hizmet raporlama için yüklenir.</span><span class="sxs-lookup"><span data-stu-id="9ba2c-108">Information about the state of the machine being managed is uploaded to the service for reporting.</span></span>
<span data-ttu-id="9ba2c-109">Bu kavram "çekme hizmeti" olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="9ba2c-109">This concept is referred to as "pull service".</span></span>

<span data-ttu-id="9ba2c-110">Çekme Hizmeti için geçerli seçenekler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="9ba2c-110">The current options for pull service include:</span></span>

- <span data-ttu-id="9ba2c-111">Azure Otomasyonu istenen durum Yapılandırma hizmeti</span><span class="sxs-lookup"><span data-stu-id="9ba2c-111">Azure Automation Desired State Configuration service</span></span>
- <span data-ttu-id="9ba2c-112">Windows Server'da çalışan bir çekme hizmeti</span><span class="sxs-lookup"><span data-stu-id="9ba2c-112">A pull service running on Windows Server</span></span>
- <span data-ttu-id="9ba2c-113">Açık kaynak çözümleri tutulan topluluk</span><span class="sxs-lookup"><span data-stu-id="9ba2c-113">Community maintained open source solutions</span></span>
- <span data-ttu-id="9ba2c-114">SMB paylaşımı</span><span class="sxs-lookup"><span data-stu-id="9ba2c-114">An SMB share</span></span>

<span data-ttu-id="9ba2c-115">**Önerilen Çözüm**, ve en çok kullanılabilir olan özellikleri seçeneğiyle [Azure Otomasyonu DSC](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-getting-started).</span><span class="sxs-lookup"><span data-stu-id="9ba2c-115">**The recommended solution**, and the option with the most features available, is [Azure Automation DSC](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-getting-started).</span></span>

<span data-ttu-id="9ba2c-116">Azure hizmet düğümleri şirket içi özel veri merkezleri veya genel Bulutlar Azure ve AWS gibi yönetebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9ba2c-116">The Azure service can manage nodes on-premises in private datacenters, or in public clouds such as Azure and AWS.</span></span>
<span data-ttu-id="9ba2c-117">Burada sunucuları doğrudan bağlanamıyor Internet'e özel ortamları için yalnızca yayımlanan Azure IP aralığına giden trafiği kullanabilirsiniz (bkz [Azure veri merkezi IP aralıkları](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).</span><span class="sxs-lookup"><span data-stu-id="9ba2c-117">For private environments where servers cannot directly connect to the Internet, consider limiting outbound traffic to only the published Azure IP range (see [Azure Datacenter IP Ranges](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).</span></span>

<span data-ttu-id="9ba2c-118">Şu anda Windows Server'da çekme Hizmet kullanılamıyor çevrimiçi hizmet özelliklerini içerir:</span><span class="sxs-lookup"><span data-stu-id="9ba2c-118">Features of the online service that are not currently available in the pull service on Windows Server include:</span></span>
- <span data-ttu-id="9ba2c-119">Yoldaki ve bekleyen tüm veriler şifrelenir</span><span class="sxs-lookup"><span data-stu-id="9ba2c-119">All data is encrypted in transit and at rest</span></span>
- <span data-ttu-id="9ba2c-120">İstemci sertifikalarını oluşturulur ve otomatik olarak yönetilir</span><span class="sxs-lookup"><span data-stu-id="9ba2c-120">Client certificates are created and managed automatically</span></span>
- <span data-ttu-id="9ba2c-121">Parolaları depolamak merkezi olarak yönetmek için [parolaları/kimlik bilgilerinin](https://docs.microsoft.com/en-us/azure/automation/automation-credentials), veya [değişkenleri](https://docs.microsoft.com/en-us/azure/automation/automation-variables) sunucu adlarını veya bağlantı dizeleri gibi</span><span class="sxs-lookup"><span data-stu-id="9ba2c-121">Secrets store for centrally managing [passwords/credentials](https://docs.microsoft.com/en-us/azure/automation/automation-credentials), or [variables](https://docs.microsoft.com/en-us/azure/automation/automation-variables) such as server names or connection strings</span></span>
- <span data-ttu-id="9ba2c-122">Düğüm merkezi olarak yönetmenize [LCM'yi yapılandırma](metaConfig.md#basic-settings)</span><span class="sxs-lookup"><span data-stu-id="9ba2c-122">Centrally manage node [LCM configuration](metaConfig.md#basic-settings)</span></span>
- <span data-ttu-id="9ba2c-123">Merkezi olarak istemci düğümlerine yapılandırmalar atama</span><span class="sxs-lookup"><span data-stu-id="9ba2c-123">Centrally assign configurations to client nodes</span></span>
- <span data-ttu-id="9ba2c-124">Üretim ulaşmadan önce test etmek için "yalancı gruplarına" yayın yapılandırma değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="9ba2c-124">Release configuration changes to "canary groups" for testing before reaching production</span></span>
- <span data-ttu-id="9ba2c-125">Grafik raporlama</span><span class="sxs-lookup"><span data-stu-id="9ba2c-125">Graphical reporting</span></span>
  - <span data-ttu-id="9ba2c-126">Ayrıntı düzeyi DSC kaynağı düzeyinde durumu ayrıntısı</span><span class="sxs-lookup"><span data-stu-id="9ba2c-126">Status detail at the DSC resource level of granularity</span></span>
  - <span data-ttu-id="9ba2c-127">Sorun giderme için istemci makinelerden ayrıntılı hata iletileri</span><span class="sxs-lookup"><span data-stu-id="9ba2c-127">Verbose error messages from client machines for troubleshooting</span></span>
- <span data-ttu-id="9ba2c-128">[Azure günlük analizi ile tümleştirme](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-diagnostics) , otomatik görevler, raporlama ve Uyarılar için Android/iOS uygulaması uyarı verme</span><span class="sxs-lookup"><span data-stu-id="9ba2c-128">[Integration with Azure Log Analytics](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-diagnostics) for alerting, automated tasks, Android/iOS app for reporting and alerting</span></span>

## <a name="dsc-pull-service-in-windows-server"></a><span data-ttu-id="9ba2c-129">Windows Server'daki DSC çekme hizmeti</span><span class="sxs-lookup"><span data-stu-id="9ba2c-129">DSC pull service in Windows Server</span></span>

<span data-ttu-id="9ba2c-130">Bir çekme hizmetini Windows Server üzerinde çalışacak şekilde yapılandırmak için mümkündür.</span><span class="sxs-lookup"><span data-stu-id="9ba2c-130">It is possible to configuring a pull service to run on Windows Server.</span></span>
<span data-ttu-id="9ba2c-131">Lütfen Windows Server'da bulunan çekme hizmet çözümünü yapılandırmaları/modüllerini yüklemek için depolama ve veritabanı için rapor verileri yakalama yalnızca yetenekleri içerir dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="9ba2c-131">Please be advised that the pull service solution included in Windows Server includes only capabilities of storing configurations/modules for download and capturing report data in to database.</span></span>
<span data-ttu-id="9ba2c-132">Çoğu Azure hizmeti tarafından sunulan yetenekleri içermez ve bu nedenle nasıl hizmeti kullanılan değerlendirmek için iyi bir aracı değildir.</span><span class="sxs-lookup"><span data-stu-id="9ba2c-132">It does not include many of the capabilities offered by the service in Azure and so is not a good tool for evaluating how the service would be used.</span></span>

<span data-ttu-id="9ba2c-133">Windows Server'da sunulan çekme hizmeti düğümleri için söylediğinizde DSC yapılandırma dosyalarını hedef düğümleri kullanılabilir hale getirmek için bir OData arabirimi kullanır IIS'de bir web hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="9ba2c-133">The pull service offered in Windows Server is a web service in IIS that uses an OData interface to make DSC configuration files available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="9ba2c-134">Bir çekme sunucusuna kullanmak için gereksinimler:</span><span class="sxs-lookup"><span data-stu-id="9ba2c-134">Requirements for using a pull server:</span></span>

- <span data-ttu-id="9ba2c-135">Çalıştıran bir sunucuda:</span><span class="sxs-lookup"><span data-stu-id="9ba2c-135">A server running:</span></span>
  - <span data-ttu-id="9ba2c-136">WMF/PowerShell 5.0 veya daha büyük</span><span class="sxs-lookup"><span data-stu-id="9ba2c-136">WMF/PowerShell 5.0 or greater</span></span>
  - <span data-ttu-id="9ba2c-137">IIS sunucu rolü</span><span class="sxs-lookup"><span data-stu-id="9ba2c-137">IIS server role</span></span>
  - <span data-ttu-id="9ba2c-138">DSC hizmeti</span><span class="sxs-lookup"><span data-stu-id="9ba2c-138">DSC Service</span></span>
- <span data-ttu-id="9ba2c-139">İdeal olarak, bazı anlamına gelir bir sertifika oluşturma hedef düğümlerine yerel Configuration Manager (LCM'yi) için geçirilen kimlik bilgileri güvenli hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="9ba2c-139">Ideally, some means of generating a certificate, to secure credentials passed to the Local Configuration Manager (LCM) on target nodes</span></span>

<span data-ttu-id="9ba2c-140">Windows Server ana bilgisayar çekme hizmetini yapılandırmak için en iyi yolu, DSC yapılandırması kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="9ba2c-140">The best way to configure Windows Server to host pull service is to use a DSC configuration.</span></span>
<span data-ttu-id="9ba2c-141">Bir örnek komut dosyası aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9ba2c-141">An example script is provided below.</span></span>

### <a name="using-the-xdscwebservice-resource"></a><span data-ttu-id="9ba2c-142">XDSCWebService kaynak kullanma</span><span class="sxs-lookup"><span data-stu-id="9ba2c-142">Using the xDSCWebService resource</span></span>

<span data-ttu-id="9ba2c-143">Bir web çekme sunucusu kurmak için en kolay yolu xPSDesiredStateConfiguration modülünde yer alan xWebService kaynak kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="9ba2c-143">The easiest way to set up a web pull server is to use the xWebService resource, included in the xPSDesiredStateConfiguration module.</span></span>
<span data-ttu-id="9ba2c-144">Aşağıdaki adımları, kaynak web hizmeti oluşturan ayarlar bir yapılandırmada kullanmak açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9ba2c-144">The following steps explain how to use the resource in a configuration that sets up the web service.</span></span>

1. <span data-ttu-id="9ba2c-145">Çağrı [yükleme-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) yüklemek için cmdlet'i **xPSDesiredStateConfiguration** modülü.</span><span class="sxs-lookup"><span data-stu-id="9ba2c-145">Call the [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) cmdlet to install the **xPSDesiredStateConfiguration** module.</span></span> <span data-ttu-id="9ba2c-146">**Not**: **yükleme-Module** dahil **PowerShellGet** PowerShell 5. 0 ' dahil modülü.</span><span class="sxs-lookup"><span data-stu-id="9ba2c-146">**Note**: **Install-Module** is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="9ba2c-147">İndirebilirsiniz **PowerShellGet** için modülü PowerShell 3.0 ve 4.0 en [PackageManagement PowerShell modülleri Önizleme](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span><span class="sxs-lookup"><span data-stu-id="9ba2c-147">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span> 
1. <span data-ttu-id="9ba2c-148">Bir güvenilen sertifika yetkilisi, kuruluşunuz ya da bir ortak yetkilisinden içinde ya da DSC çekme sunucusu için bir SSL sertifikası alın.</span><span class="sxs-lookup"><span data-stu-id="9ba2c-148">Get an SSL certificate for the DSC Pull server from a trusted Certificate Authority, either within your organization or a public authority.</span></span> <span data-ttu-id="9ba2c-149">Yetkilisinden alınan sertifika genellikle PFX biçimindedir.</span><span class="sxs-lookup"><span data-stu-id="9ba2c-149">The certificate received from the authority is usually in the PFX format.</span></span> <span data-ttu-id="9ba2c-150">DSC çekme sunucusuna CERT: \LocalMachine\My olması gereken varsayılan konumda olacak düğüm üzerinde sertifikayı yükleyin.</span><span class="sxs-lookup"><span data-stu-id="9ba2c-150">Install the certificate on the node that will become the DSC Pull server in the default location which should be CERT:\LocalMachine\My.</span></span> <span data-ttu-id="9ba2c-151">Sertifika parmak izini not edin.</span><span class="sxs-lookup"><span data-stu-id="9ba2c-151">Make a note of the certificate thumbprint.</span></span>
1. <span data-ttu-id="9ba2c-152">Kayıt anahtarı olarak kullanılacak bir GUID seçin.</span><span class="sxs-lookup"><span data-stu-id="9ba2c-152">Select a GUID to be used as the Registration Key.</span></span> <span data-ttu-id="9ba2c-153">Bir oluşturmak için PowerShell kullanarak PS istemine aşağıdakileri girin ve ENTER tuşuna basın: '``` [guid]::newGuid()```'veya'```New-Guid```'.</span><span class="sxs-lookup"><span data-stu-id="9ba2c-153">To generate one using PowerShell enter the following at the PS prompt and press enter: '``` [guid]::newGuid()```' or '```New-Guid```'.</span></span> <span data-ttu-id="9ba2c-154">Bu anahtar istemci düğümleri tarafından kayıt sırasında kimlik doğrulaması için paylaşılan bir anahtar olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9ba2c-154">This key will be used by client nodes as a shared key to authenticate during registration.</span></span> <span data-ttu-id="9ba2c-155">Daha fazla bilgi için aşağıdaki kayıt anahtarı bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="9ba2c-155">For more information see the Registration Key section below.</span></span>
1. <span data-ttu-id="9ba2c-156">PowerShell ISE aşağıdaki yapılandırma komut dosyası (F5) başlatın (örneğin klasöründe bulunan **xPSDesiredStateConfiguration** modülü Sample_xDscWebService.ps1 olarak).</span><span class="sxs-lookup"><span data-stu-id="9ba2c-156">In the PowerShell ISE, start (F5) the following configuration script (included in the Example folder of the  **xPSDesiredStateConfiguration** module as Sample_xDscWebService.ps1).</span></span> <span data-ttu-id="9ba2c-157">Bu komut çekme sunucusunda ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9ba2c-157">This script sets up the pull server.</span></span>

```powershell
    configuration Sample_xDscPullServer
    {
        param
        (
                [string[]]$NodeName = 'localhost',

                [ValidateNotNullOrEmpty()]
                [string] $certificateThumbPrint,

                [Parameter(Mandatory)]
                [ValidateNotNullOrEmpty()]
                [string] $RegistrationKey
         )

         Import-DSCResource -ModuleName xPSDesiredStateConfiguration
         Import-DSCResource –ModuleName PSDesiredStateConfiguration

         Node $NodeName
         {
             WindowsFeature DSCServiceFeature
             {
                 Ensure = 'Present'
                 Name   = 'DSC-Service'
             }

             xDscWebService PSDSCPullServer
             {
                 Ensure                   = 'Present'
                 EndpointName             = 'PSDSCPullServer'
                 Port                     = 8080
                 PhysicalPath             = "$env:SystemDrive\inetpub\PSDSCPullServer"
                 CertificateThumbPrint    = $certificateThumbPrint
                 ModulePath               = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
                 ConfigurationPath        = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
                 State                    = 'Started'
                 DependsOn                = '[WindowsFeature]DSCServiceFeature'
                 UseSecurityBestPractices = $false
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

1. <span data-ttu-id="9ba2c-158">Sertifikanın parmak izi SSL geçirme yapılandırmayı çalıştırın **certificateThumbPrint** parametre ve bir GUID kayıt anahtarı olarak **RegistrationKey** parametre:</span><span class="sxs-lookup"><span data-stu-id="9ba2c-158">Run the configuration, passing the thumbprint of the SSL certificate as the **certificateThumbPrint** parameter and a GUID registration key as the **RegistrationKey** parameter:</span></span>

```powershell
    # To find the Thumbprint for an installed SSL certificate for use with the pull server list all certificates in your local store 
    # and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
    dir Cert:\LocalMachine\my

    # Then include this thumbprint when running the configuration
    Sample_xDSCPullServer -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutputPath c:\Configs\PullServer

    # Run the compiled configuration to make the target node a DSC Pull Server
    Start-DscConfiguration -Path c:\Configs\PullServer -Wait -Verbose

```

#### <a name="registration-key"></a><span data-ttu-id="9ba2c-159">Kayıt anahtarı</span><span class="sxs-lookup"><span data-stu-id="9ba2c-159">Registration Key</span></span>

<span data-ttu-id="9ba2c-160">İstemci yapılandırması kimliği yerine yapılandırma adları kullanabilmeleri sunucusu ile kayıt düğümleri izin vermek için yukarıdaki yapılandırması tarafından oluşturulan bir kayıt anahtarı adlı bir dosyaya kaydedilir `RegistrationKeys.txt` içinde `C:\Program Files\WindowsPowerShell\DscService`.</span><span class="sxs-lookup"><span data-stu-id="9ba2c-160">To allow client nodes to register with the server so that they can use configuration names instead of a configuration ID, a registration key which was created by the above configuration is saved in a file named `RegistrationKeys.txt` in `C:\Program Files\WindowsPowerShell\DscService`.</span></span> <span data-ttu-id="9ba2c-161">Kayıt anahtarını ilk kaydı sırasında çekme sunucu ile istemci tarafından kullanılan bir paylaşılan gizlilik olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="9ba2c-161">The registration key functions as a shared secret used during the initial registration by the client with the pull server.</span></span> <span data-ttu-id="9ba2c-162">İstemci kayıt başarıyla tamamlandıktan sonra çekme sunucusuna benzersiz olarak kimlik doğrulaması için kullanılan kendinden imzalı bir sertifika oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9ba2c-162">The client will generate a self-signed certificate which is used to uniquely authenticate to the pull server once registration is successfully completed.</span></span> <span data-ttu-id="9ba2c-163">Bu sertifikanın parmak izini yerel olarak depolanır ve çekme sunucu URL'si ile ilişkili.</span><span class="sxs-lookup"><span data-stu-id="9ba2c-163">The thumbprint of this certificate is stored locally and associated with the URL of the pull server.</span></span>
> <span data-ttu-id="9ba2c-164">**Not**: Kayıt anahtarlarını PowerShell 4. 0'desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="9ba2c-164">**Note**: Registration keys are not supported in PowerShell 4.0.</span></span> 

<span data-ttu-id="9ba2c-165">Çekme sunucunun kayıt kimliğini doğrulamak için bir düğüm yapılandırmak için anahtarı'nı bu çekme Server'a kaydettirirken herhangi bir hedef düğümün meta yapılandırmasını olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9ba2c-165">In order to configure a node to authenticate with the pull server the registration key needs to be in the metaconfiguration for any target node that will be registering with this pull server.</span></span> <span data-ttu-id="9ba2c-166">Unutmayın **RegistrationKey** meta yapılandırmasını içinde aşağıdaki hedef makine başarılı bir şekilde kaydettirildi ve '140a952b-b9d6-406b-b416-e0f759c9c0e4' değeri depolanan değeriyle eşleşmelidir sonra kaldırılır. Çekme sunucusunda RegistrationKeys.txt dosyası.</span><span class="sxs-lookup"><span data-stu-id="9ba2c-166">Note that the **RegistrationKey** in the metaconfiguration below is removed after the target machine has successfully registered, and that the value '140a952b-b9d6-406b-b416-e0f759c9c0e4' must match the value stored in the RegistrationKeys.txt file on the pull server.</span></span> <span data-ttu-id="9ba2c-167">Her zaman farkında çekme sunucusu ile kayıt herhangi bir hedef makine verdiğinden kayıt anahtarı değeri güvenli kabul eder.</span><span class="sxs-lookup"><span data-stu-id="9ba2c-167">Always treat the registration key value securely, because knowing it allows any target machine to register with the pull server.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode          = 'Pull'
            RefreshFrequencyMins = 30 
            RebootNodeIfNeeded   = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL          = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey    = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('ClientConfig')
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
        }
    }
}

PullClientConfigID -OutputPath c:\Configs\TargetNodes


```

> <span data-ttu-id="9ba2c-168">**Not**: **ReportServerWeb** bölümü çekme sunucusuna gönderilecek verileri raporlama sağlar.</span><span class="sxs-lookup"><span data-stu-id="9ba2c-168">**Note**: The **ReportServerWeb** section allows reporting data to be sent to the pull server.</span></span>

<span data-ttu-id="9ba2c-169">Eksikliği **ConfigurationID** meta yapılandırmasını dosyasında özellik örtük olarak anlamına gelir, çekme sunucu bir ilk kaydı gerekli olacak şekilde çekme sunucusu protokolü V2 sürümünü destekliyor.</span><span class="sxs-lookup"><span data-stu-id="9ba2c-169">The lack of the **ConfigurationID** property in the metaconfiguration file implicitly means that pull server is supporting the V2 version of the pull server protocol so an initial registration is required.</span></span>
<span data-ttu-id="9ba2c-170">Buna karşılık, varlığını bir **ConfigurationID** çekme sunucusu protokolü V1 sürümünü kullanılır ve da bir kayıt işleme anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="9ba2c-170">Conversely, the presence of a **ConfigurationID** means that the V1 version of the pull server protocol is used and there is no registration processing.</span></span>

><span data-ttu-id="9ba2c-171">**Not**: hiçbir zaman bir çekme sunucusuna kaydettirdiyseniz düğümleri için meta yapılandırmasını dosyasındaki bir ConfigurationID özellik tanımlamak için gerekli kılan geçerli relase içinde bir anında İLETME senaryosu, bir hata bulunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9ba2c-171">**Note**: In a PUSH scenario, a bug exists in the current relase that makes it necessary to define a ConfigurationID property in the metaconfiguration file for nodes that have never registered with a pull server.</span></span> <span data-ttu-id="9ba2c-172">V1 çekme sunucu protokolü zorlamak ve kayıt hata iletileri kaçının.</span><span class="sxs-lookup"><span data-stu-id="9ba2c-172">This will force the V1 Pull Server protocol and avoid registration failure messages.</span></span>

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="9ba2c-173">Yapılandırmaları ve kaynakları yerleştirme</span><span class="sxs-lookup"><span data-stu-id="9ba2c-173">Placing configurations and resources</span></span>

<span data-ttu-id="9ba2c-174">Çekme sonra sunucu Kurulum tamamlandıktan, tarafından tanımlanan klasörleri **ConfigurationPath** ve **ModulePath** çekme sunucu yapılandırması özelliklerinde olan modülleri ve yapılandırmaları olduğu yerleştirir Hedef düğümleri çıkarmak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9ba2c-174">After the pull server setup completes, the folders defined by the **ConfigurationPath** and **ModulePath** properties in the pull server configuration are where you will place modules and configurations that will be available for target nodes to pull.</span></span>
<span data-ttu-id="9ba2c-175">Bu dosyalar çekme sunucusunun doğru şekilde işlemek sırayla belirli bir biçimde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9ba2c-175">These files need to be in a specific format in order for the pull server to correctly process them.</span></span>

### <a name="dsc-resource-module-package-format"></a><span data-ttu-id="9ba2c-176">DSC kaynağı modülü paket biçimi</span><span class="sxs-lookup"><span data-stu-id="9ba2c-176">DSC resource module package format</span></span>

<span data-ttu-id="9ba2c-177">Her kaynak modül sıkıştırılmış ve aşağıdaki düzeni according adlı gerekiyor `{Module Name}_{Module Version}.zip`.</span><span class="sxs-lookup"><span data-stu-id="9ba2c-177">Each resource module needs to be zipped and named according the following pattern `{Module Name}_{Module Version}.zip`.</span></span>
<span data-ttu-id="9ba2c-178">Örneğin, 3.1.2.0 Modül sürümü xWebAdminstration adlı bir modül 'xWebAdministration_3.2.1.0.zip' adlı.</span><span class="sxs-lookup"><span data-stu-id="9ba2c-178">For example, a module named xWebAdminstration with a module version of 3.1.2.0 would be named 'xWebAdministration_3.2.1.0.zip'.</span></span>
<span data-ttu-id="9ba2c-179">Her bir modül sürümü tek zip dosyasında yer almalıdır.</span><span class="sxs-lookup"><span data-stu-id="9ba2c-179">Each version of a module must be contained in a single zip file.</span></span>
<span data-ttu-id="9ba2c-180">Yalnızca tek bir sürümünü modül biçimi WMF 5.0 ile eklenen her zip dosyasında bir kaynak olduğundan, tek bir dizin içinde birden çok modül sürümleri için destek desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="9ba2c-180">Since there is only a single version of a resource in each zip file the module format added in WMF 5.0 with support for multiple module versions in a single directory is not supported.</span></span>
<span data-ttu-id="9ba2c-181">Bu, paketleme yukarı DSC kaynakları modüllerinin çekme server ile kullanmak için önce dizin yapısını küçük değişiklik gerektiğini anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="9ba2c-181">This means that before packaging up DSC resource modules for use with pull server you will need to make a small change to the directory structure.</span></span>
<span data-ttu-id="9ba2c-182">WMF 5.0 DSC kaynağı içeren modüller varsayılan biçimi ' {modül klasörü}\{Modül sürümü} \DscResources\{DSC kaynak klasörünü}\'.</span><span class="sxs-lookup"><span data-stu-id="9ba2c-182">The default format of modules containing DSC resource in WMF 5.0 is '{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\'.</span></span>
<span data-ttu-id="9ba2c-183">Paketleme çekme sunucu için önce yalnızca kaldırmak **{Modül sürümü}** yolu olacak şekilde klasörü ' {modül klasörü} \DscResources\{DSC kaynak klasörünü}\'.</span><span class="sxs-lookup"><span data-stu-id="9ba2c-183">Before packaging up for the pull server simply remove the **{Module version}** folder so the path becomes '{Module Folder}\DscResources\{DSC Resource Folder}\'.</span></span>
<span data-ttu-id="9ba2c-184">Bu değişiklikle, yukarıda açıklandığı gibi klasör zip ve bu ZIP dosyaları yerleştirmek **ModulePath** klasör.</span><span class="sxs-lookup"><span data-stu-id="9ba2c-184">With this change, zip the folder as described above and place these zip files in the **ModulePath** folder.</span></span>

<span data-ttu-id="9ba2c-185">Kullanım `new-dscchecksum {module zip file}` yeni eklenen modülü için sağlama toplamı dosya oluşturulamadı.</span><span class="sxs-lookup"><span data-stu-id="9ba2c-185">Use `new-dscchecksum {module zip file}` to create a checksum file for the newly-added module.</span></span>

### <a name="configuration-mof-format"></a><span data-ttu-id="9ba2c-186">Yapılandırma MOF biçimi</span><span class="sxs-lookup"><span data-stu-id="9ba2c-186">Configuration MOF format</span></span>

<span data-ttu-id="9ba2c-187">Bir yapılandırma MOF dosyası yapılandırmasını hedef düğümde bir LCM'yi doğrulayabilmesi bir sağlama toplamı dosyasıyla eşleştirilmiş gerekir.</span><span class="sxs-lookup"><span data-stu-id="9ba2c-187">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span>
<span data-ttu-id="9ba2c-188">Bir sağlama toplamı oluşturmak için arama [yeni DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="9ba2c-188">To create a checksum, call the [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx) cmdlet.</span></span>
<span data-ttu-id="9ba2c-189">Cmdlet geçen bir **yolu** MOF yapılandırma bulunduğu klasörü belirten parametre.</span><span class="sxs-lookup"><span data-stu-id="9ba2c-189">The cmdlet takes a **Path** parameter that specifies the folder where the configuration MOF is located.</span></span>
<span data-ttu-id="9ba2c-190">Cmdlet adlı bir sağlama toplamı dosyası oluşturur `ConfigurationMOFName.mof.checksum`, burada `ConfigurationMOFName` yapılandırma mof dosyasının adıdır.</span><span class="sxs-lookup"><span data-stu-id="9ba2c-190">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span>
<span data-ttu-id="9ba2c-191">Belirtilen klasörde MOF dosyaları birden fazla yapılandırma varsa, her yapılandırma klasörü için bir sağlama toplamı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9ba2c-191">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span>
<span data-ttu-id="9ba2c-192">MOF dosyaları ve ilişkili sağlama toplamı dosyalarına yerleştirmek **ConfigurationPath** klasör.</span><span class="sxs-lookup"><span data-stu-id="9ba2c-192">Place the MOF files and their associated checksum files in the **ConfigurationPath** folder.</span></span>

><span data-ttu-id="9ba2c-193">**Not**: herhangi bir şekilde yapılandırma MOF dosyasını değiştirirseniz, sağlama toplamı dosyasını da yeniden oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9ba2c-193">**Note**: If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

### <a name="tooling"></a><span data-ttu-id="9ba2c-194">Araçları</span><span class="sxs-lookup"><span data-stu-id="9ba2c-194">Tooling</span></span>

<span data-ttu-id="9ba2c-195">Ayar oluşturan için doğrulama ve daha kolay, çekme sunucusunu yönetme aşağıdaki araçları xPSDesiredStateConfiguration modülü en son sürümünü örneklerde olarak eklenir:</span><span class="sxs-lookup"><span data-stu-id="9ba2c-195">In order to make setting up, validating and managing the pull server easier, the following tools are included as examples in the latest version of the xPSDesiredStateConfiguration module:</span></span>

1. <span data-ttu-id="9ba2c-196">DSC kaynağı modülleri ve çekme sunucusunda kullanmak üzere yapılandırma dosyalarını paketleme ile yardımcı olacak bir modül.</span><span class="sxs-lookup"><span data-stu-id="9ba2c-196">A module that will help with packaging DSC resource modules and configuration files for use on the pull server.</span></span> <span data-ttu-id="9ba2c-197">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span><span class="sxs-lookup"><span data-stu-id="9ba2c-197">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span></span> <span data-ttu-id="9ba2c-198">Aşağıdaki örnekler:</span><span class="sxs-lookup"><span data-stu-id="9ba2c-198">Examples below:</span></span>

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @("xWebAdministration", "xPhp") 
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList 

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. <span data-ttu-id="9ba2c-199">Çekme sunucunun doğrulayan bir komut dosyası doğru yapılandırılmamış.</span><span class="sxs-lookup"><span data-stu-id="9ba2c-199">A script that validates the pull server is configured correctly.</span></span> <span data-ttu-id="9ba2c-200">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span><span class="sxs-lookup"><span data-stu-id="9ba2c-200">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span></span>

## <a name="community-solutions-for-pull-service"></a><span data-ttu-id="9ba2c-201">Çekme Hizmeti için topluluk çözümleri</span><span class="sxs-lookup"><span data-stu-id="9ba2c-201">Community Solutions for Pull Service</span></span>

<span data-ttu-id="9ba2c-202">DSC topluluk çekme hizmet protokolü uygulamak için birden çok çözümleri yazılan.</span><span class="sxs-lookup"><span data-stu-id="9ba2c-202">The DSC community has authored multiple solutions to implement the pull service protocol.</span></span>
<span data-ttu-id="9ba2c-203">Şirket içi artımlı iyileştirmeleri toplulukla bu çekme hizmet özellikleri ve katkıda fırsatı sunar ortamları dön.</span><span class="sxs-lookup"><span data-stu-id="9ba2c-203">For on-premises environments these offer pull service capabilities and an opportunity to contribute back to the community with incremental enhancements.</span></span>

- [<span data-ttu-id="9ba2c-204">Tug</span><span class="sxs-lookup"><span data-stu-id="9ba2c-204">Tug</span></span>](https://github.com/powershellorg/tug)
- [<span data-ttu-id="9ba2c-205">DSC-TRÆK</span><span class="sxs-lookup"><span data-stu-id="9ba2c-205">DSC-TRÆK</span></span>](https://github.com/powershellorg/dsc-traek)

## <a name="pull-client-configuration"></a><span data-ttu-id="9ba2c-206">Çekme istemci yapılandırması</span><span class="sxs-lookup"><span data-stu-id="9ba2c-206">Pull client configuration</span></span>

<span data-ttu-id="9ba2c-207">Aşağıdaki konularda ayrıntılı çekme istemcileri ayarlama açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="9ba2c-207">The following topics describe setting up pull clients in detail:</span></span>

- [<span data-ttu-id="9ba2c-208">Bir yapılandırma kimliği kullanan bir DSC çekme istemci ayarlama</span><span class="sxs-lookup"><span data-stu-id="9ba2c-208">Setting up a DSC pull client using a configuration ID</span></span>](pullClientConfigID.md)
- [<span data-ttu-id="9ba2c-209">Yapılandırma adları kullanarak bir DSC çekme istemcisi ayarlama</span><span class="sxs-lookup"><span data-stu-id="9ba2c-209">Setting up a DSC pull client using configuration names</span></span>](pullClientConfigNames.md)
- [<span data-ttu-id="9ba2c-210">Kısmi yapılandırmaları</span><span class="sxs-lookup"><span data-stu-id="9ba2c-210">Partial configurations</span></span>](partialConfigs.md)

## <a name="see-also"></a><span data-ttu-id="9ba2c-211">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="9ba2c-211">See also</span></span>

- [<span data-ttu-id="9ba2c-212">Windows PowerShell istenen durum yapılandırması genel bakış</span><span class="sxs-lookup"><span data-stu-id="9ba2c-212">Windows PowerShell Desired State Configuration Overview</span></span>](overview.md)
- [<span data-ttu-id="9ba2c-213">Yapılandırmaları Kabul Etme</span><span class="sxs-lookup"><span data-stu-id="9ba2c-213">Enacting configurations</span></span>](enactingConfigurations.md)
- [<span data-ttu-id="9ba2c-214">DSC rapor sunucusu kullanma</span><span class="sxs-lookup"><span data-stu-id="9ba2c-214">Using a DSC report server</span></span>](reportServer.md)
