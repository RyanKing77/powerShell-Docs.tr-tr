---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "DSC çekme sunucusuna ayarlama"
ms.openlocfilehash: 03d4d148c87854b146091aa0e8d815b8c35def72
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2017
---
# <a name="setting-up-a-dsc-web-pull-server"></a><span data-ttu-id="dc4d1-103">DSC çekme sunucusuna ayarlama</span><span class="sxs-lookup"><span data-stu-id="dc4d1-103">Setting up a DSC web pull server</span></span>

> <span data-ttu-id="dc4d1-104">İçin geçerlidir: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="dc4d1-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="dc4d1-105">DSC çekme sunucusuna düğümleri için söylediğinizde DSC yapılandırma dosyalarını hedef düğümleri kullanılabilir hale getirmek için bir OData arabirimi kullanır IIS'de bir web hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="dc4d1-105">A DSC web pull server is a web service in IIS that uses an OData interface to make DSC configuration files available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="dc4d1-106">Bir çekme sunucusuna kullanmak için gereksinimler:</span><span class="sxs-lookup"><span data-stu-id="dc4d1-106">Requirements for using a pull server:</span></span>

* <span data-ttu-id="dc4d1-107">Çalıştıran bir sunucuda:</span><span class="sxs-lookup"><span data-stu-id="dc4d1-107">A server running:</span></span>
  - <span data-ttu-id="dc4d1-108">WMF/PowerShell 5.0 veya daha büyük</span><span class="sxs-lookup"><span data-stu-id="dc4d1-108">WMF/PowerShell 5.0 or greater</span></span>
  - <span data-ttu-id="dc4d1-109">IIS sunucu rolü</span><span class="sxs-lookup"><span data-stu-id="dc4d1-109">IIS server role</span></span>
  - <span data-ttu-id="dc4d1-110">DSC hizmeti</span><span class="sxs-lookup"><span data-stu-id="dc4d1-110">DSC Service</span></span>
* <span data-ttu-id="dc4d1-111">İdeal olarak, bazı anlamına gelir bir sertifika oluşturma hedef düğümlerine yerel Configuration Manager (LCM'yi) için geçirilen kimlik bilgileri güvenli hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="dc4d1-111">Ideally, some means of generating a certificate, to secure credentials passed to the Local Configuration Manager (LCM) on target nodes</span></span>

<span data-ttu-id="dc4d1-112">Rol ve Özellik Ekle Sihirbazı'nı kullanarak Sunucu Yöneticisi'nde veya PowerShell kullanarak IIS sunucusu rolü ve DSC hizmet ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dc4d1-112">You can add the IIS server role and DSC Service with the Add Roles and Features wizard in Server Manager, or by using PowerShell.</span></span> <span data-ttu-id="dc4d1-113">Bu konuda bulunan örnek komut dosyaları bu iki adım sizin için de işleyecek.</span><span class="sxs-lookup"><span data-stu-id="dc4d1-113">The sample scripts included in this topic will handle both of these steps for you as well.</span></span>

## <a name="using-the-xdscwebservice-resource"></a><span data-ttu-id="dc4d1-114">XDSCWebService kaynak kullanma</span><span class="sxs-lookup"><span data-stu-id="dc4d1-114">Using the xDSCWebService resource</span></span>
<span data-ttu-id="dc4d1-115">Bir web çekme sunucusu kurmak için en kolay yolu xPSDesiredStateConfiguration modülünde yer alan xWebService kaynak kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="dc4d1-115">The easiest way to set up a web pull server is to use the xWebService resource, included in the xPSDesiredStateConfiguration module.</span></span> <span data-ttu-id="dc4d1-116">Aşağıdaki adımları, kaynak web hizmeti oluşturan ayarlar bir yapılandırmada kullanmak açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="dc4d1-116">The following steps explain how to use the resource in a configuration that sets up the web service.</span></span>

1. <span data-ttu-id="dc4d1-117">Çağrı [yükleme-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) yüklemek için cmdlet'i **xPSDesiredStateConfiguration** modülü.</span><span class="sxs-lookup"><span data-stu-id="dc4d1-117">Call the [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) cmdlet to install the **xPSDesiredStateConfiguration** module.</span></span> <span data-ttu-id="dc4d1-118">**Not**: **yükleme-Module** dahil **PowerShellGet** PowerShell 5. 0 ' dahil modülü.</span><span class="sxs-lookup"><span data-stu-id="dc4d1-118">**Note**: **Install-Module** is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="dc4d1-119">İndirebilirsiniz **PowerShellGet** için modülü PowerShell 3.0 ve 4.0 en [PackageManagement PowerShell modülleri Önizleme](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span><span class="sxs-lookup"><span data-stu-id="dc4d1-119">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span> 
1. <span data-ttu-id="dc4d1-120">Bir güvenilen sertifika yetkilisi, kuruluşunuz ya da bir ortak yetkilisinden içinde ya da DSC çekme sunucusu için bir SSL sertifikası alın.</span><span class="sxs-lookup"><span data-stu-id="dc4d1-120">Get an SSL certificate for the DSC Pull server from a trusted Certificate Authority, either within your organization or a public authority.</span></span> <span data-ttu-id="dc4d1-121">Yetkilisinden alınan sertifika genellikle PFX biçimindedir.</span><span class="sxs-lookup"><span data-stu-id="dc4d1-121">The certificate received from the authority is usually in the PFX format.</span></span> <span data-ttu-id="dc4d1-122">DSC çekme sunucusuna CERT: \LocalMachine\My olması gereken varsayılan konumda olacak düğüm üzerinde sertifikayı yükleyin.</span><span class="sxs-lookup"><span data-stu-id="dc4d1-122">Install the certificate on the node that will become the DSC Pull server in the default location which should be CERT:\LocalMachine\My.</span></span> <span data-ttu-id="dc4d1-123">Sertifika parmak izini not edin.</span><span class="sxs-lookup"><span data-stu-id="dc4d1-123">Make a note of the certificate thumbprint.</span></span>
1. <span data-ttu-id="dc4d1-124">Kayıt anahtarı olarak kullanılacak bir GUID seçin.</span><span class="sxs-lookup"><span data-stu-id="dc4d1-124">Select a GUID to be used as the Registration Key.</span></span> <span data-ttu-id="dc4d1-125">Bir oluşturmak için PowerShell kullanarak PS istemine aşağıdakileri girin ve ENTER tuşuna basın: '``` [guid]::newGuid()```'veya'```New-Guid```'.</span><span class="sxs-lookup"><span data-stu-id="dc4d1-125">To generate one using PowerShell enter the following at the PS prompt and press enter: '``` [guid]::newGuid()```' or '```New-Guid```'.</span></span> <span data-ttu-id="dc4d1-126">Bu anahtar istemci düğümleri tarafından kayıt sırasında kimlik doğrulaması için paylaşılan bir anahtar olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dc4d1-126">This key will be used by client nodes as a shared key to authenticate during registration.</span></span> <span data-ttu-id="dc4d1-127">Daha fazla bilgi için aşağıdaki kayıt anahtarı bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="dc4d1-127">For more information see the Registration Key section below.</span></span>
1. <span data-ttu-id="dc4d1-128">PowerShell ISE aşağıdaki yapılandırma komut dosyası (F5) başlatın (örneğin klasöründe bulunan **xPSDesiredStateConfiguration** modülü Sample_xDscWebService.ps1 olarak).</span><span class="sxs-lookup"><span data-stu-id="dc4d1-128">In the PowerShell ISE, start (F5) the following configuration script (included in the Example folder of the  **xPSDesiredStateConfiguration** module as Sample_xDscWebService.ps1).</span></span> <span data-ttu-id="dc4d1-129">Bu komut çekme sunucusunda ayarlar.</span><span class="sxs-lookup"><span data-stu-id="dc4d1-129">This script sets up the pull server.</span></span>
  
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

1. <span data-ttu-id="dc4d1-130">Sertifikanın parmak izi SSL geçirme yapılandırmayı çalıştırın **certificateThumbPrint** parametre ve bir GUID kayıt anahtarı olarak **RegistrationKey** parametre:</span><span class="sxs-lookup"><span data-stu-id="dc4d1-130">Run the configuration, passing the thumbprint of the SSL certificate as the **certificateThumbPrint** parameter and a GUID registration key as the **RegistrationKey** parameter:</span></span>

    ```powershell
    # To find the Thumbprint for an installed SSL certificate for use with the pull server list all certificates in your local store 
    # and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
    dir Cert:\LocalMachine\my

    # Then include this thumbprint when running the configuration
    Sample_xDSCPullServer -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutputPath c:\Configs\PullServer

    # Run the compiled configuration to make the target node a DSC Pull Server
    Start-DscConfiguration -Path c:\Configs\PullServer -Wait -Verbose
    ```

## <a name="registration-key"></a><span data-ttu-id="dc4d1-131">Kayıt anahtarı</span><span class="sxs-lookup"><span data-stu-id="dc4d1-131">Registration Key</span></span>
<span data-ttu-id="dc4d1-132">İstemci yapılandırması kimliği yerine yapılandırma adları kullanabilmeleri sunucusu ile kayıt düğümleri izin vermek için yukarıdaki yapılandırması tarafından oluşturulan bir kayıt anahtarı adlı bir dosyaya kaydedilir `RegistrationKeys.txt` içinde `C:\Program Files\WindowsPowerShell\DscService`.</span><span class="sxs-lookup"><span data-stu-id="dc4d1-132">To allow client nodes to register with the server so that they can use configuration names instead of a configuration ID, a registration key which was created by the above configuration is saved in a file named `RegistrationKeys.txt` in `C:\Program Files\WindowsPowerShell\DscService`.</span></span> <span data-ttu-id="dc4d1-133">Kayıt anahtarını ilk kaydı sırasında çekme sunucu ile istemci tarafından kullanılan bir paylaşılan gizlilik olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="dc4d1-133">The registration key functions as a shared secret used during the initial registration by the client with the pull server.</span></span> <span data-ttu-id="dc4d1-134">İstemci kayıt başarıyla tamamlandıktan sonra çekme sunucusuna benzersiz olarak kimlik doğrulaması için kullanılan kendinden imzalı bir sertifika oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dc4d1-134">The client will generate a self-signed certificate which is used to uniquely authenticate to the pull server once registration is successfully completed.</span></span> <span data-ttu-id="dc4d1-135">Bu sertifikanın parmak izini yerel olarak depolanır ve çekme sunucu URL'si ile ilişkili.</span><span class="sxs-lookup"><span data-stu-id="dc4d1-135">The thumbprint of this certificate is stored locally and associated with the URL of the pull server.</span></span>
> <span data-ttu-id="dc4d1-136">**Not**: Kayıt anahtarlarını PowerShell 4. 0'desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="dc4d1-136">**Note**: Registration keys are not supported in PowerShell 4.0.</span></span> 

<span data-ttu-id="dc4d1-137">Çekme sunucunun kayıt kimliğini doğrulamak için bir düğüm yapılandırmak için anahtarı'nı bu çekme Server'a kaydettirirken herhangi bir hedef düğümün meta yapılandırmasını olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="dc4d1-137">In order to configure a node to authenticate with the pull server the registration key needs to be in the metaconfiguration for any target node that will be registering with this pull server.</span></span> <span data-ttu-id="dc4d1-138">Unutmayın **RegistrationKey** meta yapılandırmasını içinde aşağıdaki hedef makine başarılı bir şekilde kaydettirildi ve '140a952b-b9d6-406b-b416-e0f759c9c0e4' değeri depolanan değeriyle eşleşmelidir sonra kaldırılır. Çekme sunucusunda RegistrationKeys.txt dosyası.</span><span class="sxs-lookup"><span data-stu-id="dc4d1-138">Note that the **RegistrationKey** in the metaconfiguration below is removed after the target machine has successfully registered, and that the value '140a952b-b9d6-406b-b416-e0f759c9c0e4' must match the value stored in the RegistrationKeys.txt file on the pull server.</span></span> <span data-ttu-id="dc4d1-139">Her zaman farkında çekme sunucusu ile kayıt herhangi bir hedef makine verdiğinden kayıt anahtarı değeri güvenli kabul eder.</span><span class="sxs-lookup"><span data-stu-id="dc4d1-139">Always treat the registration key value securely, because knowing it allows any target machine to register with the pull server.</span></span>

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
> <span data-ttu-id="dc4d1-140">**Not**: **ReportServerWeb** bölümü çekme sunucusuna gönderilecek verileri raporlama sağlar.</span><span class="sxs-lookup"><span data-stu-id="dc4d1-140">**Note**: The **ReportServerWeb** section allows reporting data to be sent to the pull server.</span></span> 

<span data-ttu-id="dc4d1-141">Eksikliği **ConfigurationID** meta yapılandırmasını dosyasında özellik örtük olarak anlamına gelir, çekme sunucu bir ilk kaydı gerekli olacak şekilde çekme sunucusu protokolü V2 sürümünü destekliyor.</span><span class="sxs-lookup"><span data-stu-id="dc4d1-141">The lack of the **ConfigurationID** property in the metaconfiguration file implicitly means that pull server is supporting the V2 version of the pull server protocol so an initial registration is required.</span></span> <span data-ttu-id="dc4d1-142">Buna karşılık, varlığını bir **ConfigurationID** çekme sunucusu protokolü V1 sürümünü kullanılır ve da bir kayıt işleme anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="dc4d1-142">Conversely, the presence of a **ConfigurationID** means that the V1 version of the pull server protocol is used and there is no registration processing.</span></span>

><span data-ttu-id="dc4d1-143">**Not**: hiçbir zaman bir çekme sunucusuna kaydettirdiyseniz düğümleri için meta yapılandırmasını dosyasındaki bir ConfigurationID özellik tanımlamak için gerekli kılan geçerli relase içinde bir anında İLETME senaryosu, bir hata bulunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="dc4d1-143">**Note**: In a PUSH scenario, a bug exists in the current relase that makes it necessary to define a ConfigurationID property in the metaconfiguration file for nodes that have never registered with a pull server.</span></span> <span data-ttu-id="dc4d1-144">V1 çekme sunucu protokolü zorlamak ve kayıt hata iletileri kaçının.</span><span class="sxs-lookup"><span data-stu-id="dc4d1-144">This will force the V1 Pull Server protocol and avoid registration failure messages.</span></span>

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="dc4d1-145">Yapılandırmaları ve kaynakları yerleştirme</span><span class="sxs-lookup"><span data-stu-id="dc4d1-145">Placing configurations and resources</span></span>

<span data-ttu-id="dc4d1-146">Çekme sonra sunucu Kurulum tamamlandıktan, tarafından tanımlanan klasörleri **ConfigurationPath** ve **ModulePath** çekme sunucu yapılandırması özelliklerinde olan modülleri ve yapılandırmaları olduğu yerleştirir Hedef düğümleri çıkarmak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dc4d1-146">After the pull server setup completes, the folders defined by the **ConfigurationPath** and **ModulePath** properties in the pull server configuration are where you will place modules and configurations that will be available for target nodes to pull.</span></span> <span data-ttu-id="dc4d1-147">Bu dosyalar çekme sunucusunun doğru şekilde işlemek sırayla belirli bir biçimde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="dc4d1-147">These files need to be in a specific format in order for the pull server to correctly process them.</span></span> 

### <a name="dsc-resource-module-package-format"></a><span data-ttu-id="dc4d1-148">DSC kaynağı modülü paket biçimi</span><span class="sxs-lookup"><span data-stu-id="dc4d1-148">DSC resource module package format</span></span>

<span data-ttu-id="dc4d1-149">Her kaynak modül sıkıştırılmış ve aşağıdaki düzeni according adlı gerekiyor `{Module Name}_{Module Version}.zip`.</span><span class="sxs-lookup"><span data-stu-id="dc4d1-149">Each resource module needs to be zipped and named according the following pattern `{Module Name}_{Module Version}.zip`.</span></span> <span data-ttu-id="dc4d1-150">Örneğin, 3.1.2.0 Modül sürümü xWebAdminstration adlı bir modül 'xWebAdministration_3.2.1.0.zip' adlı.</span><span class="sxs-lookup"><span data-stu-id="dc4d1-150">For example, a module named xWebAdminstration with a module version of 3.1.2.0 would be named 'xWebAdministration_3.2.1.0.zip'.</span></span> <span data-ttu-id="dc4d1-151">Her bir modül sürümü tek zip dosyasında yer almalıdır.</span><span class="sxs-lookup"><span data-stu-id="dc4d1-151">Each version of a module must be contained in a single zip file.</span></span> <span data-ttu-id="dc4d1-152">Yalnızca tek bir sürümünü modül biçimi WMF 5.0 ile eklenen her zip dosyasında bir kaynak olduğundan, tek bir dizin içinde birden çok modül sürümleri için destek desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="dc4d1-152">Since there is only a single version of a resource in each zip file the module format added in WMF 5.0 with support for multiple module versions in a single directory is not supported.</span></span> <span data-ttu-id="dc4d1-153">Bu, paketleme yukarı DSC kaynakları modüllerinin çekme server ile kullanmak için önce dizin yapısını küçük değişiklik gerektiğini anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="dc4d1-153">This means that before packaging up DSC resource modules for use with pull server you will need to make a small change to the directory structure.</span></span> <span data-ttu-id="dc4d1-154">WMF 5.0 DSC kaynağı içeren modüller varsayılan biçimi ' {modül klasörü}\{Modül sürümü} \DscResources\{DSC kaynak klasörünü}\'.</span><span class="sxs-lookup"><span data-stu-id="dc4d1-154">The default format of modules containing DSC resource in WMF 5.0 is '{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\'.</span></span> <span data-ttu-id="dc4d1-155">Paketleme çekme sunucu için önce yalnızca kaldırmak **{Modül sürümü}** yolu olacak şekilde klasörü ' {modül klasörü} \DscResources\{DSC kaynak klasörünü}\'.</span><span class="sxs-lookup"><span data-stu-id="dc4d1-155">Before packaging up for the pull server simply remove the **{Module version}** folder so the path becomes '{Module Folder}\DscResources\{DSC Resource Folder}\'.</span></span> <span data-ttu-id="dc4d1-156">Bu değişiklikle, yukarıda açıklandığı gibi klasör zip ve bu ZIP dosyaları yerleştirmek **ModulePath** klasör.</span><span class="sxs-lookup"><span data-stu-id="dc4d1-156">With this change, zip the folder as described above and place these zip files in the **ModulePath** folder.</span></span>

<span data-ttu-id="dc4d1-157">Kullanım `new-dscchecksum {module zip file}` yeni eklenen modülü için sağlama toplamı dosya oluşturulamadı.</span><span class="sxs-lookup"><span data-stu-id="dc4d1-157">Use `new-dscchecksum {module zip file}` to create a checksum file for the newly-added module.</span></span>

### <a name="configuration-mof-format"></a><span data-ttu-id="dc4d1-158">Yapılandırma MOF biçimi</span><span class="sxs-lookup"><span data-stu-id="dc4d1-158">Configuration MOF format</span></span> 
<span data-ttu-id="dc4d1-159">Bir yapılandırma MOF dosyası yapılandırmasını hedef düğümde bir LCM'yi doğrulayabilmesi bir sağlama toplamı dosyasıyla eşleştirilmiş gerekir.</span><span class="sxs-lookup"><span data-stu-id="dc4d1-159">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span> <span data-ttu-id="dc4d1-160">Bir sağlama toplamı oluşturmak için arama [yeni DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="dc4d1-160">To create a checksum, call the [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx) cmdlet.</span></span> <span data-ttu-id="dc4d1-161">Cmdlet geçen bir **yolu** MOF yapılandırma bulunduğu klasörü belirten parametre.</span><span class="sxs-lookup"><span data-stu-id="dc4d1-161">The cmdlet takes a **Path** parameter that specifies the folder where the configuration MOF is located.</span></span> <span data-ttu-id="dc4d1-162">Cmdlet adlı bir sağlama toplamı dosyası oluşturur `ConfigurationMOFName.mof.checksum`, burada `ConfigurationMOFName` yapılandırma mof dosyasının adıdır.</span><span class="sxs-lookup"><span data-stu-id="dc4d1-162">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span> <span data-ttu-id="dc4d1-163">Belirtilen klasörde MOF dosyaları birden fazla yapılandırma varsa, her yapılandırma klasörü için bir sağlama toplamı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="dc4d1-163">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span> <span data-ttu-id="dc4d1-164">MOF dosyaları ve ilişkili sağlama toplamı dosyalarına yerleştirmek **ConfigurationPath** klasör.</span><span class="sxs-lookup"><span data-stu-id="dc4d1-164">Place the MOF files and their associated checksum files in the the **ConfigurationPath** folder.</span></span>

><span data-ttu-id="dc4d1-165">**Not**: herhangi bir şekilde yapılandırma MOF dosyasını değiştirirseniz, sağlama toplamı dosyasını da yeniden oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="dc4d1-165">**Note**: If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

## <a name="tooling"></a><span data-ttu-id="dc4d1-166">Araçları</span><span class="sxs-lookup"><span data-stu-id="dc4d1-166">Tooling</span></span>
<span data-ttu-id="dc4d1-167">Ayar oluşturan için doğrulama ve daha kolay, çekme sunucusunu yönetme aşağıdaki araçları xPSDesiredStateConfiguration modülü en son sürümünü örneklerde olarak eklenir:</span><span class="sxs-lookup"><span data-stu-id="dc4d1-167">In order to make setting up, validating and managing the pull server easier, the following tools are included as examples in the latest version of the xPSDesiredStateConfiguration module:</span></span>
1. <span data-ttu-id="dc4d1-168">DSC kaynağı modülleri ve çekme sunucusunda kullanmak üzere yapılandırma dosyalarını paketleme ile yardımcı olacak bir modül.</span><span class="sxs-lookup"><span data-stu-id="dc4d1-168">A module that will help with packaging DSC resource modules and configuration files for use on the pull server.</span></span> <span data-ttu-id="dc4d1-169">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span><span class="sxs-lookup"><span data-stu-id="dc4d1-169">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span></span> <span data-ttu-id="dc4d1-170">Aşağıdaki örnekler:</span><span class="sxs-lookup"><span data-stu-id="dc4d1-170">Examples below:</span></span>

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @("xWebAdministration", "xPhp") 
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList 

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. <span data-ttu-id="dc4d1-171">Çekme sunucunun doğrulayan bir komut dosyası doğru yapılandırılmamış.</span><span class="sxs-lookup"><span data-stu-id="dc4d1-171">A script that validates the pull server is configured correctly.</span></span> <span data-ttu-id="dc4d1-172">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span><span class="sxs-lookup"><span data-stu-id="dc4d1-172">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span></span>


## <a name="pull-client-configuration"></a><span data-ttu-id="dc4d1-173">Çekme istemci yapılandırması</span><span class="sxs-lookup"><span data-stu-id="dc4d1-173">Pull client configuration</span></span> 
<span data-ttu-id="dc4d1-174">Aşağıdaki konularda ayrıntılı çekme istemcileri ayarlama açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="dc4d1-174">The following topics describe setting up pull clients in detail:</span></span>

* [<span data-ttu-id="dc4d1-175">Bir yapılandırma kimliği kullanan bir DSC çekme istemci ayarlama</span><span class="sxs-lookup"><span data-stu-id="dc4d1-175">Setting up a DSC pull client using a configuration ID</span></span>](pullClientConfigID.md)
* [<span data-ttu-id="dc4d1-176">Yapılandırma adları kullanarak bir DSC çekme istemcisi ayarlama</span><span class="sxs-lookup"><span data-stu-id="dc4d1-176">Setting up a DSC pull client using configuration names</span></span>](pullClientConfigNames.md)
* [<span data-ttu-id="dc4d1-177">Kısmi yapılandırmaları</span><span class="sxs-lookup"><span data-stu-id="dc4d1-177">Partial configurations</span></span>](partialConfigs.md)


## <a name="see-also"></a><span data-ttu-id="dc4d1-178">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="dc4d1-178">See also</span></span>
* [<span data-ttu-id="dc4d1-179">Windows PowerShell istenen durum yapılandırması genel bakış</span><span class="sxs-lookup"><span data-stu-id="dc4d1-179">Windows PowerShell Desired State Configuration Overview</span></span>](overview.md)
* [<span data-ttu-id="dc4d1-180">Yapılandırmaları ederek ilerlemesini kabul ederek</span><span class="sxs-lookup"><span data-stu-id="dc4d1-180">Enacting configurations</span></span>](enactingConfigurations.md)
* [<span data-ttu-id="dc4d1-181">DSC rapor sunucusu kullanma</span><span class="sxs-lookup"><span data-stu-id="dc4d1-181">Using a DSC report server</span></span>](reportServer.md)

