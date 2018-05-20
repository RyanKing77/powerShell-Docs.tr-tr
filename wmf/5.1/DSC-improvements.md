---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: WMF 5.1 DSC yenilikleri
ms.openlocfilehash: 32bdde6d43d17cc76c454fe10b00097753a9eebe
ms.sourcegitcommit: 2d9cf1ccb9a653db7726a408ebcb65530dcb1522
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2018
---
# <a name="improvements-in-desired-state-configuration-dsc-in-wmf-51"></a><span data-ttu-id="9fbce-103">İstenen durum yapılandırması (DSC) WMF 5.1'yenilikleri</span><span class="sxs-lookup"><span data-stu-id="9fbce-103">Improvements in Desired State Configuration (DSC) in WMF 5.1</span></span>

## <a name="dsc-class-resource-improvements"></a><span data-ttu-id="9fbce-104">DSC sınıfı kaynak geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="9fbce-104">DSC class resource improvements</span></span>

<span data-ttu-id="9fbce-105">WMF 5.1, biz aşağıdaki bilinen sorunlar düzeltildi:</span><span class="sxs-lookup"><span data-stu-id="9fbce-105">In WMF 5.1, we have fixed the following known issues:</span></span>

- <span data-ttu-id="9fbce-106">Karmaşık/karma tablo türü bir sınıf tabanlı DSC kaynağı Get() işlevi tarafından döndürülürse, get-DscConfiguration boş değerler (boş) veya hatalar döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="9fbce-106">Get-DscConfiguration may return empty values (null) or errors if a complex/hash table type is returned by Get() function of a class-based DSC resource.</span></span>
- <span data-ttu-id="9fbce-107">DSC yapılandırması RunAs kimlik bilgileri kullanılıyorsa, get-DscConfiguration hata döndürür.</span><span class="sxs-lookup"><span data-stu-id="9fbce-107">Get-DscConfiguration returns error if RunAs credential is used in DSC configuration.</span></span>
- <span data-ttu-id="9fbce-108">Kaynak sınıf tabanlı bileşik bir yapılandırmada kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="9fbce-108">Class-based resource cannot be used in a composite configuration.</span></span>
- <span data-ttu-id="9fbce-109">Kaynak sınıf tabanlı kendi türünde bir özellik varsa Başlangıç DscConfiguration askıda kalır.</span><span class="sxs-lookup"><span data-stu-id="9fbce-109">Start-DscConfiguration hangs if class-based resource has a property of its own type.</span></span>
- <span data-ttu-id="9fbce-110">Kaynak sınıf tabanlı özel bir kaynak kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="9fbce-110">Class-based resource cannot be used as an exclusive resource.</span></span>

## <a name="dsc-resource-debugging-improvements"></a><span data-ttu-id="9fbce-111">DSC kaynağı geliştirmeleri hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="9fbce-111">DSC resource debugging improvements</span></span>

<span data-ttu-id="9fbce-112">WMF 5. 0'da, PowerShell hata ayıklayıcı kaynak sınıf tabanlı bir yöntem (Get/Set/Test) doğrudan durdurulmadı.</span><span class="sxs-lookup"><span data-stu-id="9fbce-112">In WMF 5.0, the PowerShell debugger did not stop at the class-based resource method (Get/Set/Test) directly.</span></span>
<span data-ttu-id="9fbce-113">WMF 5.1, hata ayıklayıcı MOF tabanlı kaynaklara yöntemleri için olduğu gibi aynı şekilde at sınıf tabanlı kaynak yöntemi durdurur.</span><span class="sxs-lookup"><span data-stu-id="9fbce-113">In WMF 5.1, the debugger stops at the class-based resource method in the same way as for MOF-based resources methods.</span></span>

## <a name="dsc-pull-client-supports-tls-11-and-tls-12"></a><span data-ttu-id="9fbce-114">TLS 1.1 ve TLS 1.2 DSC çekme istemci destekler</span><span class="sxs-lookup"><span data-stu-id="9fbce-114">DSC pull client supports TLS 1.1 and TLS 1.2</span></span>

<span data-ttu-id="9fbce-115">Daha önce DSC çekme istemci yalnızca SSL3.0 ve TLS1.0 HTTPS bağlantıları üzerinden desteklenir.</span><span class="sxs-lookup"><span data-stu-id="9fbce-115">Previously, the DSC pull client only supported SSL3.0 and TLS1.0 over HTTPS connections.</span></span>
<span data-ttu-id="9fbce-116">Daha güvenli protokolleri kullanmak üzere zorlandığında, çekme istemci çalışmayı durdurmasına.</span><span class="sxs-lookup"><span data-stu-id="9fbce-116">When forced to use more secure protocols, the pull client would stop functioning.</span></span>
<span data-ttu-id="9fbce-117">WMF 5.1 DSC çekme istemci artık SSL 3.0 destekler ve daha güvenli TLS 1.1 ve TLS 1.2 protokolleri için destek ekler.</span><span class="sxs-lookup"><span data-stu-id="9fbce-117">In WMF 5.1, the DSC pull client no longer supports SSL 3.0 and adds support for the more secure TLS 1.1 and TLS 1.2 protocols.</span></span>

## <a name="improved-pull-server-registration"></a><span data-ttu-id="9fbce-118">Geliştirilmiş çekme sunucu kaydı</span><span class="sxs-lookup"><span data-stu-id="9fbce-118">Improved pull server registration</span></span>

<span data-ttu-id="9fbce-119">WMF önceki sürümlerinde, eşzamanlı kayıtlar/raporlama istekleri ESENT veritabanı kullanılırken bir DSC çekme sunucusuna kaydetmek ve/veya rapor başarısız LCM'yi sunulmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="9fbce-119">In the earlier versions of WMF, simultaneous registrations/reporting requests to a DSC pull server while using the ESENT database would lead to LCM failing to register and/or report.</span></span>
<span data-ttu-id="9fbce-120">Böyle durumlarda, olay günlükleri çekme sunucusunda şunlardır hata "Örnek adı zaten kullanımda."</span><span class="sxs-lookup"><span data-stu-id="9fbce-120">In such cases, the event logs on the pull server has the error "Instance Name already in use."</span></span>
<span data-ttu-id="9fbce-121">Çok iş parçacıklı senaryoda ESENT veritabanına erişmek için kullanılan hatalı desen nedeniyle, bu.</span><span class="sxs-lookup"><span data-stu-id="9fbce-121">This was due to an incorrect pattern being used to access the ESENT database in a multi-threaded scenario.</span></span>
<span data-ttu-id="9fbce-122">WMF 5.1, bu sorun düzeltilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9fbce-122">In WMF 5.1, this issue has been fixed.</span></span>
<span data-ttu-id="9fbce-123">Eşzamanlı kayıtlar veya (ESENT veritabanını içeren) raporlama WMF 5.1 düzgün çalışır.</span><span class="sxs-lookup"><span data-stu-id="9fbce-123">Concurrent registrations or reporting (involving ESENT database) works fine in WMF 5.1.</span></span>
<span data-ttu-id="9fbce-124">Bu sorun yalnızca ESENT veritabanı için geçerlidir ve OLEDB veritabanı için geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="9fbce-124">This issue is applicable only to the ESENT database and does not apply to the OLEDB database.</span></span>

## <a name="enable-circular-log-on-esent-database-instance"></a><span data-ttu-id="9fbce-125">ESENT veritabanı örneğinde döngüsel günlüğü etkinleştir</span><span class="sxs-lookup"><span data-stu-id="9fbce-125">Enable Circular log on ESENT database instance</span></span>

<span data-ttu-id="9fbce-126">DSC PullServer eariler sürümünde veritabanı örneği olmadan döngüsel günlüğü oluşturulurken pullserver becouse disk alan ESENT veritabanı günlük dosyalarını doldurma.</span><span class="sxs-lookup"><span data-stu-id="9fbce-126">In eariler version of DSC-PullServer, the ESENT database log files were filling up the disk space of the pullserver becouse the database instance was being created without circular logging.</span></span> <span data-ttu-id="9fbce-127">Bu sürümde, web.config dosyasının pullserver kullanarak örneğini döngüsel günlüğü davranışını denetlemek için seçeneğiniz vardır.</span><span class="sxs-lookup"><span data-stu-id="9fbce-127">In this release, you have the option to control the circular logging behavior of the instance using the web.config of the pullserver.</span></span> <span data-ttu-id="9fbce-128">Varsayılan olarak CircularLogging TRUE olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="9fbce-128">By default CircularLogging is set to TRUE.</span></span>

```
<appSettings>
    <add key="dbprovider" value="ESENT" />
    <add key="dbconnectionstr" value="C:\Program Files\WindowsPowerShell\DscService\Devices.edb" />
    <add key="CheckpointDepthMaxKB" value="512" />
    <add key="UseCircularESENTLogs" value="TRUE" />
  </appSettings>
```

## <a name="pull-partial-configuration-naming-convention"></a><span data-ttu-id="9fbce-129">Kısmi yapılandırma adlandırma kuralı isteme</span><span class="sxs-lookup"><span data-stu-id="9fbce-129">Pull partial configuration naming convention</span></span>

<span data-ttu-id="9fbce-130">MOF dosya adı çekme Sunucu/hizmetinde sırayla eşleşmelidir yerel configuration manager ayarlarında belirtilen kısmi yapılandırma adı eşleşmelidir önceki sürümde, kısmi bir yapılandırma için adlandırma kuralı edildi Yapılandırma adı MOF dosyasında katıştırılmış.</span><span class="sxs-lookup"><span data-stu-id="9fbce-130">In the previous release, the naming convention for a partial configuration was that the MOF file name in the pull server/service should match the partial configuration name specified in the local configuration manager settings that in turn must match the configuration name embedded in the MOF file.</span></span>

<span data-ttu-id="9fbce-131">Aşağıdaki anlık görüntüleri bakın:</span><span class="sxs-lookup"><span data-stu-id="9fbce-131">See the snapshots below:</span></span>

- <span data-ttu-id="9fbce-132">Bir düğüm alma izni olan bir kısmi yapılandırmasını tanımlayan yerel yapılandırma ayarları.</span><span class="sxs-lookup"><span data-stu-id="9fbce-132">Local configuration settings which defines a partial configuration that a node is allowed to receive.</span></span>

![Örnek meta yapılandırmasını](../images/MetaConfigPartialOne.png)

- <span data-ttu-id="9fbce-134">Örnek kısmi yapılandırma tanımı</span><span class="sxs-lookup"><span data-stu-id="9fbce-134">Sample partial configuration definition</span></span>

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

- <span data-ttu-id="9fbce-135">'ConfigurationName' oluşturulan MOF dosyasında katıştırılmış.</span><span class="sxs-lookup"><span data-stu-id="9fbce-135">'ConfigurationName' embedded in the generated MOF file.</span></span>

![Örnek oluşturulan mof dosyası](../images/PartialGeneratedMof.png)

- <span data-ttu-id="9fbce-137">Çekme yapılandırma deposundaki FileName</span><span class="sxs-lookup"><span data-stu-id="9fbce-137">FileName in the pull configuration repository</span></span>

![Yapılandırma deposundaki FileName](../images/PartialInConfigRepository.png)

<span data-ttu-id="9fbce-139">Azure Otomasyonu hizmet adı MOF dosyaları olarak oluşturulan `<ConfigurationName>.<NodeName>.mof`.</span><span class="sxs-lookup"><span data-stu-id="9fbce-139">Azure Automation service name generated MOF files as `<ConfigurationName>.<NodeName>.mof`.</span></span>
<span data-ttu-id="9fbce-140">Bu nedenle yapılandırma PartialOne.localhost.mof için derler.</span><span class="sxs-lookup"><span data-stu-id="9fbce-140">So the configuration below compiles to PartialOne.localhost.mof.</span></span>

<span data-ttu-id="9fbce-141">Bu olanaksız çekme kısmi yapılandırmanızın bir Azure Otomasyonu hizmetinden kılan.</span><span class="sxs-lookup"><span data-stu-id="9fbce-141">This made it impossible to pull one of your partial configuration from Azure Automation service.</span></span>

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

<span data-ttu-id="9fbce-142">WMF 5.1, kısmi bir çekme sunucu/hizmet yapılandırmasında olarak adlandırılabilir `<ConfigurationName>.<NodeName>.mof`.</span><span class="sxs-lookup"><span data-stu-id="9fbce-142">In WMF 5.1, a partial configuration in the pull server/service can be named as `<ConfigurationName>.<NodeName>.mof`.</span></span>
<span data-ttu-id="9fbce-143">Ayrıca, bir makine çekme tek yapılandırmasından çekiyor, sunucu/hizmet ardından çekme sunucusu yapılandırma deposu yapılandırma dosyası herhangi bir dosya adı olabilir.</span><span class="sxs-lookup"><span data-stu-id="9fbce-143">Moreover, if a machine is pulling a single configuration from a pull server/service then the configuration file on the pull server configuration repository can have any file name.</span></span>
<span data-ttu-id="9fbce-144">Bu adlandırma esneklik düğümünüz için bazı yapılandırma Azure Automation DSC'de bulunan ve yerel olarak yönetme kısmi bir yapılandırmaya sahip olduğu gelen düğümleriniz Azure Otomasyon hizmeti tarafından kısmen yönetmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="9fbce-144">This naming flexibility allows you to manage your nodes partially by Azure Automation service, where some configuration for your node is coming from Azure Automation DSC and with a partial configuration that you manage locally.</span></span>

<span data-ttu-id="9fbce-145">Bir düğüm olarak ayarlar aşağıda meta yapılandırmasını hem de yönetilen yerel olarak yanı sıra Azure Otomasyonu hizmet.</span><span class="sxs-lookup"><span data-stu-id="9fbce-145">The metaconfiguration below sets up a node to be managed both locally as well as by Azure Automation service.</span></span>

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

## <a name="using-psdscrunascredential-with-dsc-composite-resources"></a><span data-ttu-id="9fbce-146">DSC bileşik kaynaklarla PsDscRunAsCredential kullanma</span><span class="sxs-lookup"><span data-stu-id="9fbce-146">Using PsDscRunAsCredential with DSC composite resources</span></span>

<span data-ttu-id="9fbce-147">Kullanma desteği ekledik [ *PsDscRunAsCredential* ](https://msdn.microsoft.com/cs-cz/powershell/dsc/runasuser) DSC ile [bileşik](https://msdn.microsoft.com/en-us/powershell/dsc/authoringresourcecomposite) kaynakları.</span><span class="sxs-lookup"><span data-stu-id="9fbce-147">We have added support for using [*PsDscRunAsCredential*](https://msdn.microsoft.com/cs-cz/powershell/dsc/runasuser) with DSC [Composite](https://msdn.microsoft.com/en-us/powershell/dsc/authoringresourcecomposite) resources.</span></span>

<span data-ttu-id="9fbce-148">Yapılandırmaları içindeki bileşik kaynakların kullanırken, şimdi PsDscRunAsCredential için bir değer belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9fbce-148">You can now specify a value for PsDscRunAsCredential when using composite resources inside configurations.</span></span>
<span data-ttu-id="9fbce-149">Belirtildiğinde, tüm kaynakları bileşik bir kaynak içinde bir RunAs kullanıcı olarak çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9fbce-149">When specified, all resources run inside a composite resource as a RunAs user.</span></span>
<span data-ttu-id="9fbce-150">Bileşik bir kaynağı başka bir bileşik kaynak çağırırsa, kaynaklarının tümü de RunAs kullanıcı olarak çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="9fbce-150">If a composite resource calls another composite resource, all of its resources are also executed as RunAs user.</span></span>
<span data-ttu-id="9fbce-151">RunAs kimlik bilgileri bileşik kaynak hiyerarşi herhangi bir düzeyde yayılır.</span><span class="sxs-lookup"><span data-stu-id="9fbce-151">RunAs credentials are propagated to any level of the composite resource hierarchy.</span></span>
<span data-ttu-id="9fbce-152">Bileşik bir kaynak içinde herhangi bir kaynak için PsDscRunAsCredential kendi değerini belirtiyorsa, birleştirme hata yapılandırma derleme sırasında oluşur.</span><span class="sxs-lookup"><span data-stu-id="9fbce-152">If any resource inside a composite resource specifies its own value for PsDscRunAsCredential, a merge error results during configuration compilation.</span></span>

<span data-ttu-id="9fbce-153">Bu örnek ile kullanımını gösterir [WindowsFeatureSet](https://msdn.microsoft.com/en-us/powershell/wmf/dsc_newresources) bileşik kaynağı da PSDesiredStateConfiguration modülünde yer alan.</span><span class="sxs-lookup"><span data-stu-id="9fbce-153">This example shows usage with [WindowsFeatureSet](https://msdn.microsoft.com/en-us/powershell/wmf/dsc_newresources) composite resource included in PSDesiredStateConfiguration module.</span></span>

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

## <a name="dsc-module-and-configuration-signing-validations"></a><span data-ttu-id="9fbce-154">DSC modülü ve doğrulamaları imzalama yapılandırma</span><span class="sxs-lookup"><span data-stu-id="9fbce-154">DSC module and configuration signing validations</span></span>

<span data-ttu-id="9fbce-155">DSC yapılandırmaları ve modülleri yönetilen bilgisayarlar için istek sunucusundan dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="9fbce-155">In DSC, configurations and modules are distributed to managed computers from the pull server.</span></span>
<span data-ttu-id="9fbce-156">Çekme sunucunun aşılırsa, bir saldırganın olası çekme sunucusunda modülleri ve yapılandırmaları değiştirebilir ve tüm yönetilen düğümlere dağıtılan hepsinde tehlikeye olması.</span><span class="sxs-lookup"><span data-stu-id="9fbce-156">If the pull server is compromised, an attacker can potentially modify the configurations and modules on the pull server and have it distributed to all managed nodes, compromising all of them.</span></span>

<span data-ttu-id="9fbce-157">WMF 5.1, DSC destekleyen katalog ve yapılandırma dijital imzaları doğrulama (. MOF) dosyası.</span><span class="sxs-lookup"><span data-stu-id="9fbce-157">In WMF 5.1, DSC supports validating the digital signatures on catalog and configuration (.MOF) files.</span></span>
<span data-ttu-id="9fbce-158">Bu özellik, yapılandırmalar veya güvenilen bir imzalayan tarafından imzalanmamış veya güvenilen imzalayan tarafından imzalanmış sonra hangi oynanmış modül dosyaları yürütülmesini düğümleri engeller.</span><span class="sxs-lookup"><span data-stu-id="9fbce-158">This feature prevents nodes from executing configurations or module files which are not signed by a trusted signer or which have been tampered with after they have been signed by trusted signer.</span></span>

### <a name="how-to-sign-configuration-and-module"></a><span data-ttu-id="9fbce-159">Oturum yapılandırması ve modülü</span><span class="sxs-lookup"><span data-stu-id="9fbce-159">How to sign configuration and module</span></span>

***
* <span data-ttu-id="9fbce-160">Yapılandırma dosyaları (. MOF dosyalarından): Varolan PowerShell cmdlet'ini [kümesi AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) MOF dosyaları imzalama destekleyecek şekilde genişletilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9fbce-160">Configuration Files (.MOFs): The existing PowerShell cmdlet [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) is extended to support signing of MOF files.</span></span>
* <span data-ttu-id="9fbce-161">Modüller: modüller imzalama, aşağıdaki adımları kullanarak karşılık gelen modülü katalog imzalayarak gerçekleştirilir:</span><span class="sxs-lookup"><span data-stu-id="9fbce-161">Modules: Signing of modules is done by signing the corresponding module catalog using the following steps:</span></span>
    1. <span data-ttu-id="9fbce-162">Bir katalog dosyası oluşturun: bir katalog dosyası şifreleme karmalarını ya da parmak izleri koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="9fbce-162">Create a catalog file: A catalog file contains a collection of cryptographic hashes or thumbprints.</span></span>
       <span data-ttu-id="9fbce-163">Her parmak izi modülünde yer alan bir dosyaya karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="9fbce-163">Each thumbprint corresponds to a file that is included in the module.</span></span>
       <span data-ttu-id="9fbce-164">Yeni cmdlet [yeni FileCatalog](https://technet.microsoft.com/library/cc732148.aspx), kullanıcıların kendi modül için bir katalog dosyası oluşturmak eklendi.</span><span class="sxs-lookup"><span data-stu-id="9fbce-164">The new cmdlet [New-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx), has been added to enable users to create a catalog file for their module.</span></span>
    2. <span data-ttu-id="9fbce-165">Katalog dosyası oturum: kullanım [kümesi AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) katalog dosyasını imzalamak için.</span><span class="sxs-lookup"><span data-stu-id="9fbce-165">Sign the catalog file: Use [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) to sign the catalog file.</span></span>
    3. <span data-ttu-id="9fbce-166">Katalog dosyası modülü klasöre yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="9fbce-166">Place the catalog file inside the module folder.</span></span>
<span data-ttu-id="9fbce-167">Kurala göre modül katalog dosyası modülü aynı ada sahip modülü klasörü altında yerleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="9fbce-167">By convention, module catalog file should be placed under the module folder with the same name as the module.</span></span>

### <a name="localconfigurationmanager-settings-to-enable-signing-validations"></a><span data-ttu-id="9fbce-168">İmza doğrulama etkinleştirmek için LocalConfigurationManager ayarları</span><span class="sxs-lookup"><span data-stu-id="9fbce-168">LocalConfigurationManager settings to enable signing validations</span></span>

#### <a name="pull"></a><span data-ttu-id="9fbce-169">Çekme</span><span class="sxs-lookup"><span data-stu-id="9fbce-169">Pull</span></span>

<span data-ttu-id="9fbce-170">Bir düğümün LocalConfigurationManager modülleri ve yapılandırmaları geçerli ayarlarına bağlı imza doğrulaması gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="9fbce-170">The LocalConfigurationManager of a node performs signing validation of modules and configurations based on its current settings.</span></span>
<span data-ttu-id="9fbce-171">Varsayılan olarak, imza doğrulaması devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="9fbce-171">By default, signature validation is disabled.</span></span>
<span data-ttu-id="9fbce-172">İmza doğrulaması etkin düğüm gösterildiği gibi meta yapılandırma tanımını 'SignatureValidation' blok ekleyerek:</span><span class="sxs-lookup"><span data-stu-id="9fbce-172">Signature validation can enabled by adding the ‘SignatureValidation’ block to the meta-configuration definition of the node as shown below:</span></span>

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

<span data-ttu-id="9fbce-173">Bir düğümde yukarıdaki meta yapılandırmasını ayarlama indirilen yapılandırmaları ve modülleri İmza doğrulamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="9fbce-173">Setting the above metaconfiguration on a node enables signature validation on downloaded configurations and modules.</span></span>
<span data-ttu-id="9fbce-174">Yerel Configuration Manager dijital imzaları doğrulamak için aşağıdaki adımları gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="9fbce-174">The Local Configuration Manager performs the following steps to verify the digital signatures.</span></span>

1. <span data-ttu-id="9fbce-175">Bir yapılandırma dosyası imzayı doğrulamak (. MOF) geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="9fbce-175">Verify the signature on a configuration file (.MOF) is valid.</span></span>
   <span data-ttu-id="9fbce-176">PowerShell cmdlet kullanır [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx), 5.1 MOF imza doğrulaması desteklemek için genişletilmiş.</span><span class="sxs-lookup"><span data-stu-id="9fbce-176">It uses the PowerShell cmdlet [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx), which is extended in 5.1 to support MOF signature validation.</span></span>
2. <span data-ttu-id="9fbce-177">İmzalayan yetkili sertifika yetkilisi güvenilir olduğunu doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="9fbce-177">Verify the certificate authority that authorized the signer is trusted.</span></span>
3. <span data-ttu-id="9fbce-178">Modül/kaynak bağımlılıkları yapılandırmasının geçici bir konuma indirin.</span><span class="sxs-lookup"><span data-stu-id="9fbce-178">Download module/resource dependencies of the configuration to a temp location.</span></span>
4. <span data-ttu-id="9fbce-179">Modülün dahil katalog imzasını doğrular.</span><span class="sxs-lookup"><span data-stu-id="9fbce-179">Verify the signature of the catalog included inside the module.</span></span>
    * <span data-ttu-id="9fbce-180">Bulma bir `<moduleName>.cat` dosyası ve cmdlet kullanılarak imzası doğrulayın [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx).</span><span class="sxs-lookup"><span data-stu-id="9fbce-180">Find a `<moduleName>.cat` file and verify its signature using the cmdlet  [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx).</span></span>
    * <span data-ttu-id="9fbce-181">İmzalayan kimlik doğrulaması sertifika yetkilisi güvenilir olduğunu doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="9fbce-181">Verify the certification authority that authenticated the signer is trusted.</span></span>
    * <span data-ttu-id="9fbce-182">Modülleri içeriğini yok değiştirilmediğini yeni cmdlet'ini kullanarak doğrulama [Test FileCatalog](https://technet.microsoft.com/library/cc732148.aspx).</span><span class="sxs-lookup"><span data-stu-id="9fbce-182">Verify the content of the modules has not been tampered using the new cmdlet [Test-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx).</span></span>
5. <span data-ttu-id="9fbce-183">Install-modülüne $env: ProgramFiles\WindowsPowerShell\Modules\\</span><span class="sxs-lookup"><span data-stu-id="9fbce-183">Install-Module to $env:ProgramFiles\WindowsPowerShell\Modules\\</span></span>
6. <span data-ttu-id="9fbce-184">İşlem Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="9fbce-184">Process configuration</span></span>

> <span data-ttu-id="9fbce-185">Not: yapılandırma sisteme ilk kez veya modül karşıdan yüklenip uygulandığında imza doğrulama modülü katalog ve yapılandırma yalnızca gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="9fbce-185">Note: Signature validation on module-catalog and configuration is only performed when the configuration is applied to the system for the first time or when the module is downloaded and installed.</span></span>
<span data-ttu-id="9fbce-186">Tutarlılık çalışır Current.mof veya modülü bağımlılıklarını imzasını doğrulamaz.</span><span class="sxs-lookup"><span data-stu-id="9fbce-186">Consistency runs do not validate the signature of Current.mof or its module dependencies.</span></span>
<span data-ttu-id="9fbce-187">Herhangi bir aşamada doğrulama başarısız olursa, örneği için yapılandırma öğesinden çekilen varsa çekme sunucunun imzalanmamış, ardından yapılandırmanın işlenmesi aşağıda gösterilen hata ile sona erer ve tüm geçici dosyalar silinir.</span><span class="sxs-lookup"><span data-stu-id="9fbce-187">If verification has failed at any stage, for instance, if the configuration pulled from the pull server is unsigned, then processing of the configuration terminates with the error shown below and all temporary files are deleted.</span></span>

![Örnek hata çıkış yapılandırması](../images/PullUnsignedConfigFail.png)

<span data-ttu-id="9fbce-189">Benzer şekilde, katalog olmayan bir modül çekme aşağıdaki hata sonuçlarında imzalı:</span><span class="sxs-lookup"><span data-stu-id="9fbce-189">Similarly, pulling a module whose catalog is not signed results in the following error:</span></span>

![Örnek hata çıkış modülü](../images/PullUnisgnedCatalog.png)

#### <a name="push"></a><span data-ttu-id="9fbce-191">Anında iletme</span><span class="sxs-lookup"><span data-stu-id="9fbce-191">Push</span></span>

<span data-ttu-id="9fbce-192">Düğüme teslim önce teslim gönderme yöntemini kullanarak bir yapılandırma kendi kaynakta değiştirilmiş.</span><span class="sxs-lookup"><span data-stu-id="9fbce-192">A configuration delivered by using push might be tampered with at its source before it delivered to the node.</span></span>
<span data-ttu-id="9fbce-193">Yerel Configuration Manager basılmış veya yayımlanmış yapılandırmalar için benzer imza doğrulama adımları gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="9fbce-193">The Local Configuration Manager performs similar signature validation steps for pushed or published configuration(s).</span></span>
<span data-ttu-id="9fbce-194">İmza doğrulaması anında iletme için tam örnek aşağıdadır.</span><span class="sxs-lookup"><span data-stu-id="9fbce-194">Below is a complete example of signature validation for push.</span></span>

- <span data-ttu-id="9fbce-195">İmza doğrulaması düğüm üzerinde etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="9fbce-195">Enable signature validation on the node.</span></span>

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

- <span data-ttu-id="9fbce-196">Örnek bir yapılandırma dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9fbce-196">Create a sample configuration file.</span></span>

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

- <span data-ttu-id="9fbce-197">İmzasız yapılandırma dosyası düğüme Ftp'den deneyin.</span><span class="sxs-lookup"><span data-stu-id="9fbce-197">Try pushing the unsigned configuration file in to the node.</span></span>

```powershell
Start-DscConfiguration -Path .\Test -Wait -Verbose -Force
```

![ErrorUnsignedMofPushed](../images/PushUnsignedMof.png)

- <span data-ttu-id="9fbce-199">Kod imzalama sertifikası kullanarak yapılandırma dosyasını imzalayın.</span><span class="sxs-lookup"><span data-stu-id="9fbce-199">Sign the configuration file using code-signing certificate.</span></span>

![SignMofFile](../images/SignMofFile.png)

- <span data-ttu-id="9fbce-201">İmzalı MOF dosyası Ftp'den deneyin.</span><span class="sxs-lookup"><span data-stu-id="9fbce-201">Try pushing the signed MOF file.</span></span>

![SignMofFile](../images/PushSignedMof.png)
