---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: WMF 5.1 DSC geliştirmeleri
ms.openlocfilehash: 92f82d62550e105a187fd7c0c58b49367c646a7e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55683803"
---
# <a name="improvements-in-desired-state-configuration-dsc-in-wmf-51"></a><span data-ttu-id="3cc49-103">WMF 5.1 içinde Desired State Configuration (DSC) iyileştirmeleri</span><span class="sxs-lookup"><span data-stu-id="3cc49-103">Improvements in Desired State Configuration (DSC) in WMF 5.1</span></span>

## <a name="dsc-class-resource-improvements"></a><span data-ttu-id="3cc49-104">DSC sınıf kaynak geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="3cc49-104">DSC class resource improvements</span></span>

<span data-ttu-id="3cc49-105">WMF 5.1, aşağıdaki bilinen sorunlar düzelttik:</span><span class="sxs-lookup"><span data-stu-id="3cc49-105">In WMF 5.1, we have fixed the following known issues:</span></span>

- <span data-ttu-id="3cc49-106">Karmaşık/karma tablo türünde bir sınıf tabanlı DSC kaynağı Get() işlevi tarafından döndürülen, get-DscConfiguration boş değerler (null) ya da hataları döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="3cc49-106">Get-DscConfiguration may return empty values (null) or errors if a complex/hash table type is returned by Get() function of a class-based DSC resource.</span></span>
- <span data-ttu-id="3cc49-107">DSC yapılandırması RunAs kimlik bilgileri kullanılıyorsa, get-DscConfiguration hata döndürür.</span><span class="sxs-lookup"><span data-stu-id="3cc49-107">Get-DscConfiguration returns error if RunAs credential is used in DSC configuration.</span></span>
- <span data-ttu-id="3cc49-108">Kaynak sınıf tabanlı bileşik bir yapılandırmada kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="3cc49-108">Class-based resource cannot be used in a composite configuration.</span></span>
- <span data-ttu-id="3cc49-109">Kaynak sınıf tabanlı kendi türünün bir özelliği varsa Başlat-DscConfiguration yanıt vermemeye başlıyor.</span><span class="sxs-lookup"><span data-stu-id="3cc49-109">Start-DscConfiguration hangs if class-based resource has a property of its own type.</span></span>
- <span data-ttu-id="3cc49-110">Kaynak sınıf tabanlı özel bir kaynak kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="3cc49-110">Class-based resource cannot be used as an exclusive resource.</span></span>

## <a name="dsc-resource-debugging-improvements"></a><span data-ttu-id="3cc49-111">DSC kaynak hata ayıklama iyileştirmeleri</span><span class="sxs-lookup"><span data-stu-id="3cc49-111">DSC resource debugging improvements</span></span>

<span data-ttu-id="3cc49-112">WMF 5. 0'da, PowerShell hata ayıklayıcı kaynak sınıf tabanlı yöntemini (Get/Set/Test) doğrudan durdurulmadı.</span><span class="sxs-lookup"><span data-stu-id="3cc49-112">In WMF 5.0, the PowerShell debugger did not stop at the class-based resource method (Get/Set/Test) directly.</span></span>
<span data-ttu-id="3cc49-113">WMF 5.1 MOF temelli kaynak yöntemleri olduğu gibi sınıf tabanlı kaynak yöntem hata ayıklayıcıyı durdurur.</span><span class="sxs-lookup"><span data-stu-id="3cc49-113">In WMF 5.1, the debugger stops at the class-based resource method in the same way as for MOF-based resources methods.</span></span>

## <a name="dsc-pull-client-supports-tls-11-and-tls-12"></a><span data-ttu-id="3cc49-114">DSC çekme istemcisi, TLS 1.1 ve TLS 1.2 destekler.</span><span class="sxs-lookup"><span data-stu-id="3cc49-114">DSC pull client supports TLS 1.1 and TLS 1.2</span></span>

<span data-ttu-id="3cc49-115">Daha önce DSC çekme istemcisi yalnızca SSL3.0 ve TLS1.0 HTTPS bağlantılarında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="3cc49-115">Previously, the DSC pull client only supported SSL3.0 and TLS1.0 over HTTPS connections.</span></span>
<span data-ttu-id="3cc49-116">Daha güvenli protokollerini kullanacak şekilde zorlandığında, çekme istemcisi çalışmamaya.</span><span class="sxs-lookup"><span data-stu-id="3cc49-116">When forced to use more secure protocols, the pull client would stop functioning.</span></span>
<span data-ttu-id="3cc49-117">WMF 5.1 DSC çekme istemcisi artık SSL 3.0 destekler ve daha güvenli TLS 1.1 ve TLS 1.2 protokolleri için destek ekler.</span><span class="sxs-lookup"><span data-stu-id="3cc49-117">In WMF 5.1, the DSC pull client no longer supports SSL 3.0 and adds support for the more secure TLS 1.1 and TLS 1.2 protocols.</span></span>

## <a name="improved-pull-server-registration"></a><span data-ttu-id="3cc49-118">Geliştirilmiş çekme sunucusu kaydı</span><span class="sxs-lookup"><span data-stu-id="3cc49-118">Improved pull server registration</span></span>

<span data-ttu-id="3cc49-119">WMF önceki sürümlerinde eşzamanlı kayıtları/reporting istekleri ESENT veritabanını kullanırken bir DSC çekme sunucusuna kaydedin ve/veya raporu yüklerken LCM için yol açar.</span><span class="sxs-lookup"><span data-stu-id="3cc49-119">In the earlier versions of WMF, simultaneous registrations/reporting requests to a DSC pull server while using the ESENT database would lead to LCM failing to register and/or report.</span></span>
<span data-ttu-id="3cc49-120">Bu gibi durumlarda, olay günlüklerini çekme sunucusunda sahip hata "Örnek adı zaten kullanımda."</span><span class="sxs-lookup"><span data-stu-id="3cc49-120">In such cases, the event logs on the pull server has the error "Instance Name already in use."</span></span>
<span data-ttu-id="3cc49-121">Bu, hatalı bir çok iş parçacıklı senaryosunda ESENT veritabanına erişmek için kullanılan desen nedeniyle oluştu.</span><span class="sxs-lookup"><span data-stu-id="3cc49-121">This was due to an incorrect pattern being used to access the ESENT database in a multi-threaded scenario.</span></span>
<span data-ttu-id="3cc49-122">WMF 5.1, bu sorun düzeltilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3cc49-122">In WMF 5.1, this issue has been fixed.</span></span>
<span data-ttu-id="3cc49-123">Eşzamanlı kaydı veya (ESENT veritabanını içeren) raporlama WMF 5.1 düzgün çalışır.</span><span class="sxs-lookup"><span data-stu-id="3cc49-123">Concurrent registrations or reporting (involving ESENT database) works fine in WMF 5.1.</span></span>
<span data-ttu-id="3cc49-124">Bu sorun yalnızca ESENT veritabanı için geçerlidir ve OLEDB veritabanı için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="3cc49-124">This issue is applicable only to the ESENT database and does not apply to the OLEDB database.</span></span>

## <a name="enable-circular-log-on-esent-database-instance"></a><span data-ttu-id="3cc49-125">ESENT veritabanı örneğinde dairesel günlüğünü etkinleştir</span><span class="sxs-lookup"><span data-stu-id="3cc49-125">Enable Circular log on ESENT database instance</span></span>

<span data-ttu-id="3cc49-126">DSC PullServer eariler sürümünde, döngüsel günlüğü olmadan veritabanı örneği oluşturulurken pullserver becouse, disk alanı ESENT veritabanı günlük dosyalarını doldurma.</span><span class="sxs-lookup"><span data-stu-id="3cc49-126">In eariler version of DSC-PullServer, the ESENT database log files were filling up the disk space of the pullserver becouse the database instance was being created without circular logging.</span></span> <span data-ttu-id="3cc49-127">Bu sürümde, web.config dosyasının pullserver kullanarak örneğini döngüsel günlüğü davranışını denetlemek için seçeneğiniz vardır.</span><span class="sxs-lookup"><span data-stu-id="3cc49-127">In this release, you have the option to control the circular logging behavior of the instance using the web.config of the pullserver.</span></span> <span data-ttu-id="3cc49-128">Varsayılan olarak CircularLogging TRUE olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="3cc49-128">By default CircularLogging is set to TRUE.</span></span>

```
<appSettings>
    <add key="dbprovider" value="ESENT" />
    <add key="dbconnectionstr" value="C:\Program Files\WindowsPowerShell\DscService\Devices.edb" />
    <add key="CheckpointDepthMaxKB" value="512" />
    <add key="UseCircularESENTLogs" value="TRUE" />
  </appSettings>
```

## <a name="pull-partial-configuration-naming-convention"></a><span data-ttu-id="3cc49-129">Kısmi yapılandırma adlandırma kuralı çekme</span><span class="sxs-lookup"><span data-stu-id="3cc49-129">Pull partial configuration naming convention</span></span>

<span data-ttu-id="3cc49-130">Önceki bir sürümde çekme Sunucusu/hizmetinde MOF dosyası adı belirtilen sırayla eşleşmelidir yerel configuration manager ayarlarında kısmi yapılandırma adıyla eşleşmelidir kısmi bir yapılandırma için adlandırma kuralı oluştu. Yapılandırma adı MOF dosyası içinde gömülü.</span><span class="sxs-lookup"><span data-stu-id="3cc49-130">In the previous release, the naming convention for a partial configuration was that the MOF file name in the pull server/service should match the partial configuration name specified in the local configuration manager settings that in turn must match the configuration name embedded in the MOF file.</span></span>

<span data-ttu-id="3cc49-131">Aşağıdaki anlık görüntüleri bakın:</span><span class="sxs-lookup"><span data-stu-id="3cc49-131">See the snapshots below:</span></span>

- <span data-ttu-id="3cc49-132">Bir düğüm alma izni olan bir kısmi yapılandırmasını tanımlayan yerel yapılandırma ayarları.</span><span class="sxs-lookup"><span data-stu-id="3cc49-132">Local configuration settings which defines a partial configuration that a node is allowed to receive.</span></span>

![Örnek metaconfiguration](../images/MetaConfigPartialOne.png)

- <span data-ttu-id="3cc49-134">Örnek kısmi yapılandırma tanımı</span><span class="sxs-lookup"><span data-stu-id="3cc49-134">Sample partial configuration definition</span></span>

```powershell
Configuration PartialOne
{
    Node('localhost')
    {
        File test
        {
            DestinationPath = "$env:TEMP\partialconfigexample.txt"
            Contents = 'Partial Config Example'
        }
    }
}
PartialOne
```

- <span data-ttu-id="3cc49-135">Oluşturulan MOF dosyasında ekli ConfigurationName'.</span><span class="sxs-lookup"><span data-stu-id="3cc49-135">'ConfigurationName' embedded in the generated MOF file.</span></span>

![Örnek oluşturulan mof dosyası](../images/PartialGeneratedMof.png)

- <span data-ttu-id="3cc49-137">Çekme yapılandırma deposundaki dosya adı</span><span class="sxs-lookup"><span data-stu-id="3cc49-137">FileName in the pull configuration repository</span></span>

![Yapılandırma deposundaki dosya adı](../images/PartialInConfigRepository.png)

<span data-ttu-id="3cc49-139">Azure Otomasyonu hizmeti adı MOF dosyaları olarak oluşturulan `<ConfigurationName>.<NodeName>.mof`.</span><span class="sxs-lookup"><span data-stu-id="3cc49-139">Azure Automation service name generated MOF files as `<ConfigurationName>.<NodeName>.mof`.</span></span>
<span data-ttu-id="3cc49-140">Bu nedenle aşağıdaki yapılandırmayı PartialOne.localhost.mof için derler.</span><span class="sxs-lookup"><span data-stu-id="3cc49-140">So the configuration below compiles to PartialOne.localhost.mof.</span></span>

<span data-ttu-id="3cc49-141">Bunu mümkün olmayan çekme kısmi yapılandırmanızın bir Azure Otomasyonu hizmetinden yapılan.</span><span class="sxs-lookup"><span data-stu-id="3cc49-141">This made it impossible to pull one of your partial configuration from Azure Automation service.</span></span>

```powershell
Configuration PartialOne
{
    Node('localhost')
    {
        File test
        {
            DestinationPath = "$env:TEMP\partialconfigexample.txt"
            Contents = 'Partial Config Example'
        }
    }
}
PartialOne
```

<span data-ttu-id="3cc49-142">WMF 5.1, kısmi bir çekme sunucusu/hizmet yapılandırmasında olarak adlandırılabilir `<ConfigurationName>.<NodeName>.mof`.</span><span class="sxs-lookup"><span data-stu-id="3cc49-142">In WMF 5.1, a partial configuration in the pull server/service can be named as `<ConfigurationName>.<NodeName>.mof`.</span></span>
<span data-ttu-id="3cc49-143">Ayrıca, bir makine bir tek bir çekme yapılandırmasından çekiyor, sunucu/hizmet yapılandırma dosyasını ardından çekme sunucusu yapılandırma deposu üzerindeki herhangi bir dosya adı olabilir.</span><span class="sxs-lookup"><span data-stu-id="3cc49-143">Moreover, if a machine is pulling a single configuration from a pull server/service then the configuration file on the pull server configuration repository can have any file name.</span></span>
<span data-ttu-id="3cc49-144">Bu adlandırma esneklik düğümü için bazı yapılandırmalar Azure Automation DSC ve yerel olarak yönettiğiniz kısmi bir yapılandırma ile nereden geldiğini düğümlerinizi kısmen Azure Otomasyonu hizmeti tarafından yönetmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="3cc49-144">This naming flexibility allows you to manage your nodes partially by Azure Automation service, where some configuration for your node is coming from Azure Automation DSC and with a partial configuration that you manage locally.</span></span>

<span data-ttu-id="3cc49-145">Bir düğüm olacak şekilde ayarlar aşağıda metaconfiguration hem de yönetilen yerel olarak hem de Azure Otomasyonu tarafından hizmet.</span><span class="sxs-lookup"><span data-stu-id="3cc49-145">The metaconfiguration below sets up a node to be managed both locally as well as by Azure Automation service.</span></span>

```powershell
[DscLocalConfigurationManager()]
Configuration RegistrationMetaConfig
{
    Settings
    {
        RefreshFrequencyMins = 30
        RefreshMode = "PULL"
    }

    ConfigurationRepositoryWeb web
    {
        ServerURL =  $endPoint
        RegistrationKey = $registrationKey
        ConfigurationNames = $configurationName
    }

    # Partial configuration managed by Azure Automation service.
    PartialConfiguration PartialConfigurationManagedByAzureAutomation
    {
        ConfigurationSource = "[ConfigurationRepositoryWeb]Web"
    }

    # This partial configuration is managed locally.
    PartialConfiguration OnPremisesConfig
    {
        RefreshMode = "PUSH"
        ExclusiveResources = @("Script")
    }

}

RegistrationMetaConfig
Set-DscLocalConfigurationManager -Path .\RegistrationMetaConfig -Verbose
```

## <a name="using-psdscrunascredential-with-dsc-composite-resources"></a><span data-ttu-id="3cc49-146">DSC bileşik kaynaklarla PsDscRunAsCredential kullanma</span><span class="sxs-lookup"><span data-stu-id="3cc49-146">Using PsDscRunAsCredential with DSC composite resources</span></span>

<span data-ttu-id="3cc49-147">Kullanma desteği ekledik [ *PsDscRunAsCredential* ](https://msdn.microsoft.com/cs-cz/powershell/dsc/runasuser) DSC ile [bileşik](https://msdn.microsoft.com/powershell/dsc/authoringresourcecomposite) kaynakları.</span><span class="sxs-lookup"><span data-stu-id="3cc49-147">We have added support for using [*PsDscRunAsCredential*](https://msdn.microsoft.com/cs-cz/powershell/dsc/runasuser) with DSC [Composite](https://msdn.microsoft.com/powershell/dsc/authoringresourcecomposite) resources.</span></span>

<span data-ttu-id="3cc49-148">Bileşik kaynaklar içinde yapılandırmaları kullanırken, artık PsDscRunAsCredential için bir değer belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3cc49-148">You can now specify a value for PsDscRunAsCredential when using composite resources inside configurations.</span></span>
<span data-ttu-id="3cc49-149">Belirtildiğinde, tüm kaynaklar bir bileşik kaynak içinde bir RunAs kullanıcı olarak çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="3cc49-149">When specified, all resources run inside a composite resource as a RunAs user.</span></span>
<span data-ttu-id="3cc49-150">Bileşik kaynak başka bir bileşik kaynak çağırırsa, tüm kaynaklarını RunAs kullanıcı olarak yürütülür.</span><span class="sxs-lookup"><span data-stu-id="3cc49-150">If a composite resource calls another composite resource, all of its resources are also executed as RunAs user.</span></span>
<span data-ttu-id="3cc49-151">RunAs kimlik Bilgileri'ni bileşik kaynak hiyerarşi düzeyine yayılır.</span><span class="sxs-lookup"><span data-stu-id="3cc49-151">RunAs credentials are propagated to any level of the composite resource hierarchy.</span></span>
<span data-ttu-id="3cc49-152">Bileşik kaynak içinde herhangi bir kaynak için PsDscRunAsCredential kendi değeri belirtiyorsa, yapılandırma derleme sırasında bir birleştirme hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="3cc49-152">If any resource inside a composite resource specifies its own value for PsDscRunAsCredential, a merge error results during configuration compilation.</span></span>

<span data-ttu-id="3cc49-153">Bu örnek, kullanımını gösterir. [WindowsFeatureSet](https://msdn.microsoft.com/powershell/wmf/dsc_newresources) da PSDesiredStateConfiguration modülüne dahil edilen bileşik kaynak.</span><span class="sxs-lookup"><span data-stu-id="3cc49-153">This example shows usage with [WindowsFeatureSet](https://msdn.microsoft.com/powershell/wmf/dsc_newresources) composite resource included in PSDesiredStateConfiguration module.</span></span>

```powershell
Configuration InstallWindowsFeature
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node $AllNodes.NodeName
    {
        WindowsFeatureSet features
        {
            Name = @("Telnet-Client","SNMP-Service")
            Ensure = "Present"
            IncludeAllSubFeature = $true
            PsDscRunAsCredential = Get-Credential
        }
    }
}

$configData = @{
    AllNodes = @(
        @{
            NodeName             = 'localhost'
            PSDscAllowDomainUser = $true
            CertificateFile      = 'C:\publicKeys\targetNode.cer'
            Thumbprint           = '7ee7f09d-4be0-41aa-a47f-96b9e3bdec25'
        }
    )
}

InstallWindowsFeature -ConfigurationData $configData
```

## <a name="dsc-module-and-configuration-signing-validations"></a><span data-ttu-id="3cc49-154">DSC modülünü ve doğrulamaları imzalama yapılandırma</span><span class="sxs-lookup"><span data-stu-id="3cc49-154">DSC module and configuration signing validations</span></span>

<span data-ttu-id="3cc49-155">DSC yapılandırmaları ve modülleri çekme sunucusundan yönetilen bilgisayarlara dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="3cc49-155">In DSC, configurations and modules are distributed to managed computers from the pull server.</span></span>
<span data-ttu-id="3cc49-156">Çekme sunucusu ele geçirilirse saldırgan potansiyel olarak çekme sunucusunda modülleri ve yapılandırmaları değiştirmek ve tüm yönetilen düğümlere dağıtılmış tümünün ödün sahip.</span><span class="sxs-lookup"><span data-stu-id="3cc49-156">If the pull server is compromised, an attacker can potentially modify the configurations and modules on the pull server and have it distributed to all managed nodes, compromising all of them.</span></span>

<span data-ttu-id="3cc49-157">WMF 5.1 DSC destekler katalog ve yapılandırmasına dijital imzalarını doğrulama (. MOF) dosyası.</span><span class="sxs-lookup"><span data-stu-id="3cc49-157">In WMF 5.1, DSC supports validating the digital signatures on catalog and configuration (.MOF) files.</span></span>
<span data-ttu-id="3cc49-158">Bu özellik, düğüm yapılandırmaları veya güvenilen bir imzalayan tarafından imzalanmamış veya güvenilen imzalayan tarafından imzalanmış sonra kurcalanmış Modülü dosyaları yürütülmesini engeller.</span><span class="sxs-lookup"><span data-stu-id="3cc49-158">This feature prevents nodes from executing configurations or module files which are not signed by a trusted signer or which have been tampered with after they have been signed by trusted signer.</span></span>

### <a name="how-to-sign-configuration-and-module"></a><span data-ttu-id="3cc49-159">Yapılandırma ve modül oturum açma</span><span class="sxs-lookup"><span data-stu-id="3cc49-159">How to sign configuration and module</span></span>

***
* <span data-ttu-id="3cc49-160">Yapılandırma dosyaları (. MOF'lar): Mevcut PowerShell cmdlet'i [kümesi AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) MOF dosyaları imzalama destekleyecek şekilde genişletilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3cc49-160">Configuration Files (.MOFs): The existing PowerShell cmdlet [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) is extended to support signing of MOF files.</span></span>
* <span data-ttu-id="3cc49-161">Modüller: Aşağıdaki adımları kullanarak karşılık gelen modülü Kataloğu açarak modüllerini imzalama gerçekleştirilir:</span><span class="sxs-lookup"><span data-stu-id="3cc49-161">Modules: Signing of modules is done by signing the corresponding module catalog using the following steps:</span></span>
    1. <span data-ttu-id="3cc49-162">Bir katalog dosyası oluşturun: Bir katalog dosyası şifreleme karmalarını ya da parmak izleri koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="3cc49-162">Create a catalog file: A catalog file contains a collection of cryptographic hashes or thumbprints.</span></span>
       <span data-ttu-id="3cc49-163">Her bir parmak izi modülüne dahil edilen bir dosyaya karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="3cc49-163">Each thumbprint corresponds to a file that is included in the module.</span></span>
       <span data-ttu-id="3cc49-164">Yeni cmdlet [yeni FileCatalog](https://technet.microsoft.com/library/cc732148.aspx), kendi modül için bir katalog dosyası oluşturmak için kullanıcıları etkinleştirmek üzere eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="3cc49-164">The new cmdlet [New-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx), has been added to enable users to create a catalog file for their module.</span></span>
    2. <span data-ttu-id="3cc49-165">Katalog dosyasını imzalayın: Kullanım [kümesi AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) katalog dosyasını imzalamak için.</span><span class="sxs-lookup"><span data-stu-id="3cc49-165">Sign the catalog file: Use [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) to sign the catalog file.</span></span>
    3. <span data-ttu-id="3cc49-166">Katalog dosyası modülü klasörün içine yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="3cc49-166">Place the catalog file inside the module folder.</span></span>
<span data-ttu-id="3cc49-167">Kural gereği, modül olarak aynı ada sahip modülü klasörü altında modülü katalog dosyası yerleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="3cc49-167">By convention, module catalog file should be placed under the module folder with the same name as the module.</span></span>

### <a name="localconfigurationmanager-settings-to-enable-signing-validations"></a><span data-ttu-id="3cc49-168">İmzalama doğrulamaları etkinleştirmek için LocalConfigurationManager ayarları</span><span class="sxs-lookup"><span data-stu-id="3cc49-168">LocalConfigurationManager settings to enable signing validations</span></span>

#### <a name="pull"></a><span data-ttu-id="3cc49-169">Çekme</span><span class="sxs-lookup"><span data-stu-id="3cc49-169">Pull</span></span>

<span data-ttu-id="3cc49-170">Bir düğümün LocalConfigurationManager modülleri ve yapılandırmaları, geçerli ayarları temel alarak imza doğrulaması gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="3cc49-170">The LocalConfigurationManager of a node performs signing validation of modules and configurations based on its current settings.</span></span>
<span data-ttu-id="3cc49-171">Varsayılan olarak, imza doğrulaması devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="3cc49-171">By default, signature validation is disabled.</span></span>
<span data-ttu-id="3cc49-172">İmza doğrulama düğümü gösterildiği meta-yapılandırma tanımını 'SignatureValidation' bloğu ekleyerek etkinleştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3cc49-172">Signature validation can enabled by adding the ‘SignatureValidation’ block to the meta-configuration definition of the node as shown below:</span></span>

```powershell
[DSCLocalConfigurationManager()]
Configuration EnableSignatureValidation
{
    Settings
    {
        RefreshMode = 'PULL'
    }

    ConfigurationRepositoryWeb pullserver{
      ConfigurationNames = 'sql'
      ServerURL = 'http://localhost:8080/PSDSCPullServer/PSDSCPullServer.svc'
      AllowUnsecureConnection = $true
      RegistrationKey = 'd6750ff1-d8dd-49f7-8caf-7471ea9793fc' # Replace this with correct registration key.
    }
    SignatureValidation validations{
        # If the TrustedStorePath property is provided then LCM will use the custom path. Otherwise, the LCM will use default trusted store path (Cert:\LocalMachine\DSCStore) to find the signing certificate.
        TrustedStorePath = 'Cert:\LocalMachine\DSCStore'
        SignedItemType = 'Configuration','Module'         # This is a list of DSC artifacts, for which LCM need to verify their digital signature before executing them on the node.
    }

}
EnableSignatureValidation
Set-DscLocalConfigurationManager -Path .\EnableSignatureValidation -Verbose
```

<span data-ttu-id="3cc49-173">Bir düğümde yukarıdaki metaconfiguration ayarlamak, indirilen yapılandırmaları ve modülleri İmza doğrulamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="3cc49-173">Setting the above metaconfiguration on a node enables signature validation on downloaded configurations and modules.</span></span>
<span data-ttu-id="3cc49-174">Yerel Configuration Manager dijital imzaları doğrulamak için aşağıdaki adımları gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="3cc49-174">The Local Configuration Manager performs the following steps to verify the digital signatures.</span></span>

1. <span data-ttu-id="3cc49-175">Bir yapılandırma dosyası üzerinde imzasını (. MOF) geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="3cc49-175">Verify the signature on a configuration file (.MOF) is valid.</span></span>
   <span data-ttu-id="3cc49-176">PowerShell cmdlet'ini kullanır [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx), 5.1 MOF imza doğrulaması destekleyecek şekilde genişletilmiş.</span><span class="sxs-lookup"><span data-stu-id="3cc49-176">It uses the PowerShell cmdlet [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx), which is extended in 5.1 to support MOF signature validation.</span></span>
2. <span data-ttu-id="3cc49-177">Yetkili imzalayan sertifika yetkilisi güvenildiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="3cc49-177">Verify the certificate authority that authorized the signer is trusted.</span></span>
3. <span data-ttu-id="3cc49-178">Modül/kaynak bağımlılıkları yapılandırmasının geçici bir konuma indirin.</span><span class="sxs-lookup"><span data-stu-id="3cc49-178">Download module/resource dependencies of the configuration to a temp location.</span></span>
4. <span data-ttu-id="3cc49-179">İçinde modülüne dahil edilen Kataloğu imzasını doğrular.</span><span class="sxs-lookup"><span data-stu-id="3cc49-179">Verify the signature of the catalog included inside the module.</span></span>
    * <span data-ttu-id="3cc49-180">Bulma bir `<moduleName>.cat` dosyası ve cmdlet kullanarak kendi imzasını [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx).</span><span class="sxs-lookup"><span data-stu-id="3cc49-180">Find a `<moduleName>.cat` file and verify its signature using the cmdlet  [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx).</span></span>
    * <span data-ttu-id="3cc49-181">İmzalayan kimlik doğrulaması sertifika yetkilisi güvenildiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="3cc49-181">Verify the certification authority that authenticated the signer is trusted.</span></span>
    * <span data-ttu-id="3cc49-182">Modüller içeriğini değil kurcalanıp yeni cmdlet'ini kullanarak doğrulama [Test FileCatalog](https://technet.microsoft.com/library/cc732148.aspx).</span><span class="sxs-lookup"><span data-stu-id="3cc49-182">Verify the content of the modules has not been tampered using the new cmdlet [Test-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx).</span></span>
5. <span data-ttu-id="3cc49-183">Install-Module $env: ProgramFiles\WindowsPowerShell\Modules\\</span><span class="sxs-lookup"><span data-stu-id="3cc49-183">Install-Module to $env:ProgramFiles\WindowsPowerShell\Modules\\</span></span>
6. <span data-ttu-id="3cc49-184">İşlem Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="3cc49-184">Process configuration</span></span>

> <span data-ttu-id="3cc49-185">Not: Yapılandırmayı ilk kez veya modül indirilir ve yüklenir, sisteme uygulandığında imzası doğrulama modülü katalog ve yapılandırmasına yalnızca gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="3cc49-185">Note: Signature validation on module-catalog and configuration is only performed when the configuration is applied to the system for the first time or when the module is downloaded and installed.</span></span>
<span data-ttu-id="3cc49-186">Tutarlılık çalıştırmaları Current.mof veya modül bağımlılıklarını imzasını doğrulamaz.</span><span class="sxs-lookup"><span data-stu-id="3cc49-186">Consistency runs do not validate the signature of Current.mof or its module dependencies.</span></span>
<span data-ttu-id="3cc49-187">Herhangi bir aşamasında doğrulama başarısız olursa, örneği için yapılandırmayı çekilen, çekme sunucusu imzalanmamış, ardından yapılandırmanın işleme aşağıda gösterilen hata ile sona erer ve tüm geçici dosyalar silinir.</span><span class="sxs-lookup"><span data-stu-id="3cc49-187">If verification has failed at any stage, for instance, if the configuration pulled from the pull server is unsigned, then processing of the configuration terminates with the error shown below and all temporary files are deleted.</span></span>

![Örnek hata çıkış yapılandırması](../images/PullUnsignedConfigFail.png)

<span data-ttu-id="3cc49-189">Benzer şekilde, katalog değil bir modül çekme şu hata sonuçlarında imzalı:</span><span class="sxs-lookup"><span data-stu-id="3cc49-189">Similarly, pulling a module whose catalog is not signed results in the following error:</span></span>

![Örnek hata çıkış modülü](../images/PullUnisgnedCatalog.png)

#### <a name="push"></a><span data-ttu-id="3cc49-191">anında iletme</span><span class="sxs-lookup"><span data-stu-id="3cc49-191">Push</span></span>

<span data-ttu-id="3cc49-192">Düğüme teslim önce yükleme kullanılarak teslim edilen yapılandırma, kaynakta değiştirilmiş.</span><span class="sxs-lookup"><span data-stu-id="3cc49-192">A configuration delivered by using push might be tampered with at its source before it delivered to the node.</span></span>
<span data-ttu-id="3cc49-193">Yerel Configuration Manager için gönderildi veya yayımlanmış yapılandırmaları benzer imzası doğrulama adımları gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="3cc49-193">The Local Configuration Manager performs similar signature validation steps for pushed or published configuration(s).</span></span>
<span data-ttu-id="3cc49-194">Gönderim için imza doğrulaması için tam bir örnek aşağıdadır.</span><span class="sxs-lookup"><span data-stu-id="3cc49-194">Below is a complete example of signature validation for push.</span></span>

- <span data-ttu-id="3cc49-195">İmza doğrulaması düğüm üzerinde etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="3cc49-195">Enable signature validation on the node.</span></span>

```powershell
[DSCLocalConfigurationManager()]
Configuration EnableSignatureValidation
{
    Settings
    {
        RefreshMode = 'PUSH'
    }
    SignatureValidation validations{
        TrustedStorePath = 'Cert:\LocalMachine\DSCStore'
        SignedItemType =  'Configuration','Module'
    }

}
EnableSignatureValidation
Set-DscLocalConfigurationManager -Path .\EnableSignatureValidation -Verbose
```

- <span data-ttu-id="3cc49-196">Örnek bir yapılandırma dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3cc49-196">Create a sample configuration file.</span></span>

```powershell
# Sample configuration
Configuration Test
{

    File foo
    {
        DestinationPath =  "$env:TEMP\signingTest.txt"
        Contents = "ABC"
    }
}
Test
```

- <span data-ttu-id="3cc49-197">İşaretsiz bir yapılandırma dosyası düğüme gönderme deneyin.</span><span class="sxs-lookup"><span data-stu-id="3cc49-197">Try pushing the unsigned configuration file in to the node.</span></span>

```powershell
Start-DscConfiguration -Path .\Test -Wait -Verbose -Force
```

![ErrorUnsignedMofPushed](../images/PushUnsignedMof.png)

- <span data-ttu-id="3cc49-199">Yapılandırma dosyası, kod imzalama sertifikası kullanarak oturum açın.</span><span class="sxs-lookup"><span data-stu-id="3cc49-199">Sign the configuration file using code-signing certificate.</span></span>

![SignMofFile](../images/SignMofFile.png)

- <span data-ttu-id="3cc49-201">İmzalı MOF dosyası göndermek deneyin.</span><span class="sxs-lookup"><span data-stu-id="3cc49-201">Try pushing the signed MOF file.</span></span>

![SignMofFile](../images/PushSignedMof.png)
