---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: WMF 5.1 DSC geliştirmeleri
ms.openlocfilehash: e7f20bfa865777aeac8f083959782317cfdf6cde
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856234"
---
# <a name="improvements-in-desired-state-configuration-dsc-in-wmf-51"></a><span data-ttu-id="4156c-103">WMF 5.1 içinde Desired State Configuration (DSC) iyileştirmeleri</span><span class="sxs-lookup"><span data-stu-id="4156c-103">Improvements in Desired State Configuration (DSC) in WMF 5.1</span></span>

## <a name="dsc-class-resource-improvements"></a><span data-ttu-id="4156c-104">DSC sınıf kaynak geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="4156c-104">DSC class resource improvements</span></span>

<span data-ttu-id="4156c-105">WMF 5.1, aşağıdaki bilinen sorunlar düzelttik:</span><span class="sxs-lookup"><span data-stu-id="4156c-105">In WMF 5.1, we have fixed the following known issues:</span></span>

- <span data-ttu-id="4156c-106">Karmaşık/karma tablo türünde bir sınıf tabanlı DSC kaynağı Get() işlevi tarafından döndürülen, get-DscConfiguration boş değerler (null) ya da hataları döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="4156c-106">Get-DscConfiguration may return empty values (null) or errors if a complex/hash table type is returned by Get() function of a class-based DSC resource.</span></span>
- <span data-ttu-id="4156c-107">DSC yapılandırması RunAs kimlik bilgileri kullanılıyorsa, get-DscConfiguration hata döndürür.</span><span class="sxs-lookup"><span data-stu-id="4156c-107">Get-DscConfiguration returns error if RunAs credential is used in DSC configuration.</span></span>
- <span data-ttu-id="4156c-108">Kaynak sınıf tabanlı bileşik bir yapılandırmada kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="4156c-108">Class-based resource cannot be used in a composite configuration.</span></span>
- <span data-ttu-id="4156c-109">Kaynak sınıf tabanlı kendi türünün bir özelliği varsa Başlat-DscConfiguration yanıt vermemeye başlıyor.</span><span class="sxs-lookup"><span data-stu-id="4156c-109">Start-DscConfiguration hangs if class-based resource has a property of its own type.</span></span>
- <span data-ttu-id="4156c-110">Kaynak sınıf tabanlı özel bir kaynak kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="4156c-110">Class-based resource cannot be used as an exclusive resource.</span></span>

## <a name="dsc-resource-debugging-improvements"></a><span data-ttu-id="4156c-111">DSC kaynak hata ayıklama iyileştirmeleri</span><span class="sxs-lookup"><span data-stu-id="4156c-111">DSC resource debugging improvements</span></span>

<span data-ttu-id="4156c-112">WMF 5. 0'da, PowerShell hata ayıklayıcı kaynak sınıf tabanlı yöntemini (Get/Set/Test) doğrudan durdurulmadı.</span><span class="sxs-lookup"><span data-stu-id="4156c-112">In WMF 5.0, the PowerShell debugger did not stop at the class-based resource method (Get/Set/Test) directly.</span></span> <span data-ttu-id="4156c-113">WMF 5.1 MOF temelli kaynak yöntemleri olduğu gibi sınıf tabanlı kaynak yöntem hata ayıklayıcıyı durdurur.</span><span class="sxs-lookup"><span data-stu-id="4156c-113">In WMF 5.1, the debugger stops at the class-based resource method in the same way as for MOF-based resources methods.</span></span>

## <a name="dsc-pull-client-supports-tls-11-and-tls-12"></a><span data-ttu-id="4156c-114">DSC çekme istemcisi, TLS 1.1 ve TLS 1.2 destekler.</span><span class="sxs-lookup"><span data-stu-id="4156c-114">DSC pull client supports TLS 1.1 and TLS 1.2</span></span>

<span data-ttu-id="4156c-115">Daha önce DSC çekme istemcisi yalnızca SSL3.0 ve TLS1.0 HTTPS bağlantılarında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="4156c-115">Previously, the DSC pull client only supported SSL3.0 and TLS1.0 over HTTPS connections.</span></span> <span data-ttu-id="4156c-116">Daha güvenli protokollerini kullanacak şekilde zorlandığında, çekme istemcisi çalışmamaya.</span><span class="sxs-lookup"><span data-stu-id="4156c-116">When forced to use more secure protocols, the pull client would stop functioning.</span></span> <span data-ttu-id="4156c-117">WMF 5.1 DSC çekme istemcisi artık SSL 3.0 destekler ve daha güvenli TLS 1.1 ve TLS 1.2 protokolleri için destek ekler.</span><span class="sxs-lookup"><span data-stu-id="4156c-117">In WMF 5.1, the DSC pull client no longer supports SSL 3.0 and adds support for the more secure TLS 1.1 and TLS 1.2 protocols.</span></span>

## <a name="improved-pull-server-registration"></a><span data-ttu-id="4156c-118">Geliştirilmiş çekme sunucusu kaydı</span><span class="sxs-lookup"><span data-stu-id="4156c-118">Improved pull server registration</span></span>

<span data-ttu-id="4156c-119">WMF önceki sürümlerinde eşzamanlı kayıtları/reporting istekleri ESENT veritabanını kullanırken bir DSC çekme sunucusuna kaydedin ve/veya raporu yüklerken LCM için yol açar.</span><span class="sxs-lookup"><span data-stu-id="4156c-119">In the earlier versions of WMF, simultaneous registrations/reporting requests to a DSC pull server while using the ESENT database would lead to LCM failing to register and/or report.</span></span> <span data-ttu-id="4156c-120">Bu gibi durumlarda, olay günlüklerini çekme sunucusunda sahip hata "Örnek adı zaten kullanımda."</span><span class="sxs-lookup"><span data-stu-id="4156c-120">In such cases, the event logs on the pull server has the error "Instance Name already in use."</span></span> <span data-ttu-id="4156c-121">Bu, hatalı bir çok iş parçacıklı senaryosunda ESENT veritabanına erişmek için kullanılan desen tarafından neden oldu.</span><span class="sxs-lookup"><span data-stu-id="4156c-121">This was caused by an incorrect pattern being used to access the ESENT database in a multi-threaded scenario.</span></span> <span data-ttu-id="4156c-122">WMF 5.1, bu sorun düzeltilmiştir.</span><span class="sxs-lookup"><span data-stu-id="4156c-122">In WMF 5.1, this issue has been fixed.</span></span> <span data-ttu-id="4156c-123">Eşzamanlı kaydı veya (ESENT veritabanını içeren) raporlama WMF 5.1 düzgün çalışır.</span><span class="sxs-lookup"><span data-stu-id="4156c-123">Concurrent registrations or reporting (involving ESENT database) works fine in WMF 5.1.</span></span> <span data-ttu-id="4156c-124">Bu sorun yalnızca ESENT veritabanı için geçerlidir ve OLEDB veritabanı için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="4156c-124">This issue is applicable only to the ESENT database and does not apply to the OLEDB database.</span></span>

## <a name="enable-circular-log-on-esent-database-instance"></a><span data-ttu-id="4156c-125">ESENT veritabanı örneğinde dairesel günlüğünü etkinleştir</span><span class="sxs-lookup"><span data-stu-id="4156c-125">Enable Circular log on ESENT database instance</span></span>

<span data-ttu-id="4156c-126">DSC PullServer eariler sürümünde, döngüsel günlüğü olmadan veritabanı örneği oluşturulurken pullserver becouse, disk alanı ESENT veritabanı günlük dosyalarını doldurma.</span><span class="sxs-lookup"><span data-stu-id="4156c-126">In eariler version of DSC-PullServer, the ESENT database log files were filling up the disk space of the pullserver becouse the database instance was being created without circular logging.</span></span> <span data-ttu-id="4156c-127">Bu sürümde, web.config dosyasının pullserver kullanarak örneğini döngüsel günlüğü davranışını denetlemek için seçeneğiniz vardır.</span><span class="sxs-lookup"><span data-stu-id="4156c-127">In this release, you have the option to control the circular logging behavior of the instance using the web.config of the pullserver.</span></span> <span data-ttu-id="4156c-128">Varsayılan olarak CircularLogging TRUE olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="4156c-128">By default CircularLogging is set to TRUE.</span></span>

```xml
<appSettings>
    <add key="dbprovider" value="ESENT" />
    <add key="dbconnectionstr" value="C:\Program Files\WindowsPowerShell\DscService\Devices.edb" />
    <add key="CheckpointDepthMaxKB" value="512" />
    <add key="UseCircularESENTLogs" value="TRUE" />
  </appSettings>
```

## <a name="wow64-support-for-configuration-keyword"></a><span data-ttu-id="4156c-129">Yapılandırma anahtar sözcüğü için WOW64 desteği</span><span class="sxs-lookup"><span data-stu-id="4156c-129">WOW64 support for Configuration Keyword</span></span>

<span data-ttu-id="4156c-130">`Configuration` Anahtar sözcüğü bir 64 bit bilgisayarda WOW64 artık desteklenmektedir.</span><span class="sxs-lookup"><span data-stu-id="4156c-130">The `Configuration` keyword is now supported in WOW64 on a 64-bit computer.</span></span> <span data-ttu-id="4156c-131">Bu, bir DSC yapılandırması tanımlanabilir ve 64 bit bilgisayarda çalışan bir 32-bit işlem içinde Windows PowerShell ISE gibi (x 86) derlenmiş, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="4156c-131">This means that a DSC configuration can be defined and compiled within a 32-bit process such as Windows PowerShell ISE (x86) running on a 64-bit computer.</span></span>

## <a name="pull-partial-configuration-naming-convention"></a><span data-ttu-id="4156c-132">Kısmi yapılandırma adlandırma kuralı çekme</span><span class="sxs-lookup"><span data-stu-id="4156c-132">Pull partial configuration naming convention</span></span>

<span data-ttu-id="4156c-133">Önceki bir sürümde çekme Sunucusu/hizmetinde MOF dosyası adı belirtilen sırayla eşleşmelidir yerel configuration manager ayarlarında kısmi yapılandırma adıyla eşleşmelidir kısmi bir yapılandırma için adlandırma kuralı oluştu. Yapılandırma adı MOF dosyası içinde gömülü.</span><span class="sxs-lookup"><span data-stu-id="4156c-133">In the previous release, the naming convention for a partial configuration was that the MOF file name in the pull server/service should match the partial configuration name specified in the local configuration manager settings that in turn must match the configuration name embedded in the MOF file.</span></span>

<span data-ttu-id="4156c-134">Aşağıdaki anlık görüntüleri bakın:</span><span class="sxs-lookup"><span data-stu-id="4156c-134">See the snapshots below:</span></span>

- <span data-ttu-id="4156c-135">Bir düğüm alma izni olan bir kısmi yapılandırmasını tanımlayan yerel yapılandırma ayarları.</span><span class="sxs-lookup"><span data-stu-id="4156c-135">Local configuration settings which defines a partial configuration that a node is allowed to receive.</span></span>

  ![Örnek metaconfiguration](../images/MetaConfigPartialOne.png)

- <span data-ttu-id="4156c-137">Örnek kısmi yapılandırma tanımı</span><span class="sxs-lookup"><span data-stu-id="4156c-137">Sample partial configuration definition</span></span>

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

- <span data-ttu-id="4156c-138">Oluşturulan MOF dosyasında ekli ConfigurationName'.</span><span class="sxs-lookup"><span data-stu-id="4156c-138">'ConfigurationName' embedded in the generated MOF file.</span></span>

  ![Örnek oluşturulan mof dosyası](../images/PartialGeneratedMof.png)

- <span data-ttu-id="4156c-140">Çekme yapılandırma deposundaki dosya adı</span><span class="sxs-lookup"><span data-stu-id="4156c-140">FileName in the pull configuration repository</span></span>

  ![Yapılandırma deposundaki dosya adı](../images/PartialInConfigRepository.png)

  <span data-ttu-id="4156c-142">Azure Otomasyonu hizmeti adı MOF dosyaları olarak oluşturulan `<ConfigurationName>.<NodeName>.mof`.</span><span class="sxs-lookup"><span data-stu-id="4156c-142">Azure Automation service name generated MOF files as `<ConfigurationName>.<NodeName>.mof`.</span></span> <span data-ttu-id="4156c-143">Bu nedenle aşağıdaki yapılandırmayı PartialOne.localhost.mof için derler.</span><span class="sxs-lookup"><span data-stu-id="4156c-143">So the configuration below compiles to PartialOne.localhost.mof.</span></span>

  <span data-ttu-id="4156c-144">Bunu mümkün olmayan çekme kısmi yapılandırmanızın bir Azure Otomasyonu hizmetinden yapılan.</span><span class="sxs-lookup"><span data-stu-id="4156c-144">This made it impossible to pull one of your partial configuration from Azure Automation service.</span></span>

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

  <span data-ttu-id="4156c-145">WMF 5.1, kısmi bir çekme sunucusu/hizmet yapılandırmasında olarak adlandırılabilir `<ConfigurationName>.<NodeName>.mof`.</span><span class="sxs-lookup"><span data-stu-id="4156c-145">In WMF 5.1, a partial configuration in the pull server/service can be named as `<ConfigurationName>.<NodeName>.mof`.</span></span> <span data-ttu-id="4156c-146">Ayrıca, bir makine bir tek bir çekme yapılandırmasından çekiyor, sunucu/hizmet yapılandırma dosyasını ardından çekme sunucusu yapılandırma deposu üzerindeki herhangi bir dosya adı olabilir.</span><span class="sxs-lookup"><span data-stu-id="4156c-146">Moreover, if a machine is pulling a single configuration from a pull server/service then the configuration file on the pull server configuration repository can have any file name.</span></span> <span data-ttu-id="4156c-147">Bu adlandırma esneklik düğümü için bazı yapılandırmalar Azure Automation DSC ve yerel olarak yönettiğiniz kısmi bir yapılandırma ile nereden geldiğini düğümlerinizi kısmen Azure Otomasyonu hizmeti tarafından yönetmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="4156c-147">This naming flexibility allows you to manage your nodes partially by Azure Automation service, where some configuration for your node is coming from Azure Automation DSC and with a partial configuration that you manage locally.</span></span>

  <span data-ttu-id="4156c-148">Bir düğüm olacak şekilde ayarlar aşağıda metaconfiguration hem de yönetilen yerel olarak hem de Azure Otomasyonu tarafından hizmet.</span><span class="sxs-lookup"><span data-stu-id="4156c-148">The metaconfiguration below sets up a node to be managed both locally as well as by Azure Automation service.</span></span>

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

## <a name="using-psdscrunascredential-with-dsc-composite-resources"></a><span data-ttu-id="4156c-149">DSC bileşik kaynaklarla PsDscRunAsCredential kullanma</span><span class="sxs-lookup"><span data-stu-id="4156c-149">Using PsDscRunAsCredential with DSC composite resources</span></span>

<span data-ttu-id="4156c-150">Kullanma desteği ekledik [PsDscRunAsCredential](/powershell/dsc/configurations/runAsUser) DSC ile [bileşik](https://msdn.microsoft.com/powershell/dsc/authoringresourcecomposite) kaynakları.</span><span class="sxs-lookup"><span data-stu-id="4156c-150">We have added support for using [PsDscRunAsCredential](/powershell/dsc/configurations/runAsUser) with DSC [Composite](https://msdn.microsoft.com/powershell/dsc/authoringresourcecomposite) resources.</span></span>

<span data-ttu-id="4156c-151">Artık için bir değer belirtebilirsiniz **PsDscRunAsCredential** yapılandırmaları içinde bileşik kaynakları kullanırken.</span><span class="sxs-lookup"><span data-stu-id="4156c-151">You can now specify a value for **PsDscRunAsCredential** when using composite resources inside configurations.</span></span> <span data-ttu-id="4156c-152">Belirtildiğinde, tüm kaynaklar bir bileşik kaynak içinde bir RunAs kullanıcı olarak çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="4156c-152">When specified, all resources run inside a composite resource as a RunAs user.</span></span> <span data-ttu-id="4156c-153">Bileşik kaynak başka bir bileşik kaynak çağırırsa, tüm bu kaynakları da RunAs kullanıcı olarak yürütülür.</span><span class="sxs-lookup"><span data-stu-id="4156c-153">If a composite resource calls another composite resource, all those resources are also executed as RunAs user.</span></span> <span data-ttu-id="4156c-154">RunAs kimlik Bilgileri'ni bileşik kaynak hiyerarşi düzeyine yayılır.</span><span class="sxs-lookup"><span data-stu-id="4156c-154">RunAs credentials are propagated to any level of the composite resource hierarchy.</span></span> <span data-ttu-id="4156c-155">Bileşik kaynak içinde herhangi bir kaynak için kendi değerine belirtirse **PsDscRunAsCredential**, yapılandırma derleme sırasında bir birleştirme hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="4156c-155">If any resource inside a composite resource specifies its own value for **PsDscRunAsCredential**, a merge error results during configuration compilation.</span></span>

<span data-ttu-id="4156c-156">Bu örnek, kullanımını gösterir. [WindowsFeatureSet](/powershell/dsc/reference/resources/windows/windowsfeaturesetresource) da PSDesiredStateConfiguration modülüne dahil edilen bileşik kaynak.</span><span class="sxs-lookup"><span data-stu-id="4156c-156">This example shows usage with the [WindowsFeatureSet](/powershell/dsc/reference/resources/windows/windowsfeaturesetresource) composite resource included in PSDesiredStateConfiguration module.</span></span>

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

## <a name="allowing-for-identical-duplicate-resources-in-a-configuration"></a><span data-ttu-id="4156c-157">Bir yapılandırmada aynı kaynağa izin verme</span><span class="sxs-lookup"><span data-stu-id="4156c-157">Allowing for Identical Duplicate Resources in a Configuration</span></span>

<span data-ttu-id="4156c-158">DSC izin ver veya yapılandırması içindeki çakışan kaynak tanımlarını işlemek desteklemez.</span><span class="sxs-lookup"><span data-stu-id="4156c-158">DSC does not allow or handle conflicting resource definitions within a configuration.</span></span> <span data-ttu-id="4156c-159">Çakışmayı çözmek çalışmak yerine, basitçe başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="4156c-159">Instead of trying to resolve the conflict, it simply fails.</span></span> <span data-ttu-id="4156c-160">Yapılandırma yeniden daha bileşik kaynaklarında kullanılan haline gelir gibi vb. çakışmaları daha sık meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="4156c-160">As configuration reuse becomes more utilized through composite resources, etc. conflicts will occur more often.</span></span> <span data-ttu-id="4156c-161">Çakışan kaynak tanımları aynı olduğunda, DSC Akıllı ve buna izin gerekir.</span><span class="sxs-lookup"><span data-stu-id="4156c-161">When conflicting resource definitions are identical, DSC should be smart and allow this.</span></span> <span data-ttu-id="4156c-162">Bu sürümle birlikte, aynı tanımlara sahip birden çok kaynak örneğini sahip destekliyoruz:</span><span class="sxs-lookup"><span data-stu-id="4156c-162">With this release, we support having multiple resource instances that have identical definitions:</span></span>

```powershell
Configuration IIS_FrontEnd
{
    WindowsFeature FE_IIS         #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature FTP
    {
        Ensure = 'Present'
        Name = 'Web-FTP-Server'
    }
}

Configuration IIS_Worker
{
    WindowsFeature Worker_IIS      #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature ASP
    {
        Ensure = 'Present'
        Name = 'Web-ASP-Net45'
    }
}

Configuration WebApplication
{
    IIS_Frontend Web {}

    IIS_Worker ASP {}
}
```

<span data-ttu-id="4156c-163">Önceki sürümlerde, sonuç WindowsFeature FE_IIS ve 'Web-Server' rolü emin olmak çalışırken WindowsFeature Worker_IIS örnekleri arasında bir çakışma nedeniyle başarısız bir derleme yüklü olacaktır.</span><span class="sxs-lookup"><span data-stu-id="4156c-163">In previous releases, the result would be a failed compilation due to a conflict between the WindowsFeature FE_IIS and WindowsFeature Worker_IIS instances trying to ensure the 'Web-Server' role is installed.</span></span> <span data-ttu-id="4156c-164">Dikkat *tüm* bu iki yapılandırmada yapılandırılmış olan özellikleri aynıdır.</span><span class="sxs-lookup"><span data-stu-id="4156c-164">Notice that *all* of the properties that are being configured are identical in these two configurations.</span></span> <span data-ttu-id="4156c-165">Bu yana *tüm* bu iki özellik kaynakların aynı olduğundan, bu artık başarılı bir derleme içinde neden olur.</span><span class="sxs-lookup"><span data-stu-id="4156c-165">Since *all* of the properties in these two resources are identical, this will result in a successful compilation now.</span></span>

<span data-ttu-id="4156c-166">Özelliklerinden herhangi birini iki kaynakları arasında farklıysa, bunlar aynı kabul edilmez ve derleme başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="4156c-166">If any of the properties are different between the two resources, they will not be considered identical and compilation will fail.</span></span>

## <a name="dsc-module-and-configuration-signing-validations"></a><span data-ttu-id="4156c-167">DSC modülünü ve doğrulamaları imzalama yapılandırma</span><span class="sxs-lookup"><span data-stu-id="4156c-167">DSC module and configuration signing validations</span></span>

<span data-ttu-id="4156c-168">DSC yapılandırmaları ve modülleri çekme sunucusundan yönetilen bilgisayarlara dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="4156c-168">In DSC, configurations and modules are distributed to managed computers from the pull server.</span></span> <span data-ttu-id="4156c-169">Çekme sunucusu ele geçirilirse saldırgan büyük olasılıkla çekme sunucusunda modülleri ve yapılandırmaları değiştirebilir ve tüm yönetilen düğümlere dağıtılmış olması.</span><span class="sxs-lookup"><span data-stu-id="4156c-169">If the pull server is compromised, an attacker can potentially modify the configurations and modules on the pull server and have it distributed to all managed nodes.</span></span>

<span data-ttu-id="4156c-170">WMF 5.1 DSC destekler katalog ve yapılandırmasına dijital imzalarını doğrulama (. MOF) dosyası.</span><span class="sxs-lookup"><span data-stu-id="4156c-170">In WMF 5.1, DSC supports validating the digital signatures on catalog and configuration (.MOF) files.</span></span> <span data-ttu-id="4156c-171">Bu özellik, düğüm yapılandırmaları veya güvenilen bir imzalayan tarafından imzalanmamış veya güvenilen imzalayan tarafından imzalanmış sonra kurcalanmış Modülü dosyaları yürütülmesini engeller.</span><span class="sxs-lookup"><span data-stu-id="4156c-171">This feature prevents nodes from executing configurations or module files which are not signed by a trusted signer or which have been tampered with after they have been signed by trusted signer.</span></span>

### <a name="how-to-sign-configuration-and-module"></a><span data-ttu-id="4156c-172">Yapılandırma ve modül oturum açma</span><span class="sxs-lookup"><span data-stu-id="4156c-172">How to sign configuration and module</span></span>

- <span data-ttu-id="4156c-173">Yapılandırma dosyaları (. MOF'lar): Mevcut PowerShell cmdlet'i [kümesi AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) MOF dosyaları imzalama destekleyecek şekilde genişletilmiştir.</span><span class="sxs-lookup"><span data-stu-id="4156c-173">Configuration Files (.MOFs): The existing PowerShell cmdlet [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) is extended to support signing of MOF files.</span></span>
- <span data-ttu-id="4156c-174">Modüller: Aşağıdaki adımları kullanarak karşılık gelen modülü Kataloğu açarak modüllerini imzalama gerçekleştirilir:</span><span class="sxs-lookup"><span data-stu-id="4156c-174">Modules: Signing of modules is done by signing the corresponding module catalog using the following steps:</span></span>
  1. <span data-ttu-id="4156c-175">Bir katalog dosyası oluşturun: Bir katalog dosyası şifreleme karmalarını ya da parmak izleri koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="4156c-175">Create a catalog file: A catalog file contains a collection of cryptographic hashes or thumbprints.</span></span> <span data-ttu-id="4156c-176">Her bir parmak izi modülüne dahil edilen bir dosyaya karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="4156c-176">Each thumbprint corresponds to a file that is included in the module.</span></span> <span data-ttu-id="4156c-177">Yeni cmdlet [yeni FileCatalog](/powershell/module/microsoft.powershell.security/new-filecatalog), kendi modül için bir katalog dosyası oluşturmak için kullanıcıları etkinleştirmek üzere eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="4156c-177">The new cmdlet [New-FileCatalog](/powershell/module/microsoft.powershell.security/new-filecatalog), has been added to enable users to create a catalog file for their module.</span></span>
  2. <span data-ttu-id="4156c-178">Katalog dosyasını imzalayın: Kullanım [kümesi AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) katalog dosyasını imzalamak için.</span><span class="sxs-lookup"><span data-stu-id="4156c-178">Sign the catalog file: Use [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) to sign the catalog file.</span></span>
  3. <span data-ttu-id="4156c-179">Katalog dosyası modülü klasörün içine yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="4156c-179">Place the catalog file inside the module folder.</span></span> <span data-ttu-id="4156c-180">Kural gereği, modül olarak aynı ada sahip modülü klasörü altında modülü katalog dosyası yerleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="4156c-180">By convention, module catalog file should be placed under the module folder with the same name as the module.</span></span>

### <a name="localconfigurationmanager-settings-to-enable-signing-validations"></a><span data-ttu-id="4156c-181">İmzalama doğrulamaları etkinleştirmek için LocalConfigurationManager ayarları</span><span class="sxs-lookup"><span data-stu-id="4156c-181">LocalConfigurationManager settings to enable signing validations</span></span>

#### <a name="pull"></a><span data-ttu-id="4156c-182">Çekme</span><span class="sxs-lookup"><span data-stu-id="4156c-182">Pull</span></span>

<span data-ttu-id="4156c-183">Bir düğümün LocalConfigurationManager modülleri ve yapılandırmaları, geçerli ayarları temel alarak imza doğrulaması gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="4156c-183">The LocalConfigurationManager of a node performs signing validation of modules and configurations based on its current settings.</span></span> <span data-ttu-id="4156c-184">Varsayılan olarak, imza doğrulaması devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="4156c-184">By default, signature validation is disabled.</span></span> <span data-ttu-id="4156c-185">İmza doğrulama düğümü gösterildiği meta-yapılandırma tanımını 'SignatureValidation' bloğu ekleyerek etkinleştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="4156c-185">Signature validation can enabled by adding the ‘SignatureValidation’ block to the meta-configuration definition of the node as shown below:</span></span>

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

<span data-ttu-id="4156c-186">Bir düğümde yukarıdaki metaconfiguration ayarlamak, indirilen yapılandırmaları ve modülleri İmza doğrulamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="4156c-186">Setting the above metaconfiguration on a node enables signature validation on downloaded configurations and modules.</span></span> <span data-ttu-id="4156c-187">Yerel Configuration Manager dijital imzaları doğrulamak için aşağıdaki adımları gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="4156c-187">The Local Configuration Manager performs the following steps to verify the digital signatures.</span></span>

1. <span data-ttu-id="4156c-188">Bir yapılandırma dosyası üzerinde imzasını (. MOF), geçerli kullanarak `Get-AuthenticodeSignature` cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="4156c-188">Verify the signature on a configuration file (.MOF) is valid using the `Get-AuthenticodeSignature` cmdlet.</span></span>
2. <span data-ttu-id="4156c-189">Yetkili imzalayan sertifika yetkilisi güvenildiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="4156c-189">Verify the certificate authority that authorized the signer is trusted.</span></span>
3. <span data-ttu-id="4156c-190">Modül/kaynak bağımlılıkları yapılandırmasının geçici bir konuma indirin.</span><span class="sxs-lookup"><span data-stu-id="4156c-190">Download module/resource dependencies of the configuration to a temp location.</span></span>
4. <span data-ttu-id="4156c-191">İçinde modülüne dahil edilen Kataloğu imzasını doğrular.</span><span class="sxs-lookup"><span data-stu-id="4156c-191">Verify the signature of the catalog included inside the module.</span></span>
   - <span data-ttu-id="4156c-192">Bulma bir `<moduleName>.cat` dosya ve imza kullanarak doğrulama `Get-AuthenticodeSignature`.</span><span class="sxs-lookup"><span data-stu-id="4156c-192">Find a `<moduleName>.cat` file and verify its signature using `Get-AuthenticodeSignature`.</span></span>
   - <span data-ttu-id="4156c-193">İmzalayan kimlik doğrulaması sertifika yetkilisi güvenildiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="4156c-193">Verify the certification authority that authenticated the signer is trusted.</span></span>
   - <span data-ttu-id="4156c-194">Modüller içeriğini değil kurcalanıp yeni cmdlet'ini kullanarak doğrulama `Test-FileCatalog`.</span><span class="sxs-lookup"><span data-stu-id="4156c-194">Verify the content of the modules has not been tampered using the new cmdlet `Test-FileCatalog`.</span></span>
5. <span data-ttu-id="4156c-195">`Install-Module` Hedef `$env:ProgramFiles\WindowsPowerShell\Modules\`</span><span class="sxs-lookup"><span data-stu-id="4156c-195">`Install-Module` to `$env:ProgramFiles\WindowsPowerShell\Modules\`</span></span>
6. <span data-ttu-id="4156c-196">İşlem Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="4156c-196">Process configuration</span></span>

> [!NOTE]
> <span data-ttu-id="4156c-197">Yapılandırmayı ilk kez veya modül indirilir ve yüklenir, sisteme uygulandığında imzası doğrulama modülü katalog ve yapılandırmasına yalnızca gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="4156c-197">Signature validation on module-catalog and configuration is only performed when the configuration is applied to the system for the first time or when the module is downloaded and installed.</span></span>
> <span data-ttu-id="4156c-198">Tutarlılık çalıştırmaları Current.mof veya modül bağımlılıklarını imzasını doğrulamaz.</span><span class="sxs-lookup"><span data-stu-id="4156c-198">Consistency runs do not validate the signature of Current.mof or its module dependencies.</span></span> <span data-ttu-id="4156c-199">Herhangi bir aşamasında doğrulama başarısız olursa, örneği için yapılandırmayı çekilen, çekme sunucusu imzalanmamış, ardından yapılandırmanın işleme aşağıda gösterilen hata ile sona erer ve tüm geçici dosyalar silinir.</span><span class="sxs-lookup"><span data-stu-id="4156c-199">If verification has failed at any stage, for instance, if the configuration pulled from the pull server is unsigned, then processing of the configuration terminates with the error shown below and all temporary files are deleted.</span></span>

![Örnek hata çıkış yapılandırması](../images/PullUnsignedConfigFail.png)

<span data-ttu-id="4156c-201">Benzer şekilde, katalog değil bir modül çekme şu hata sonuçlarında imzalı:</span><span class="sxs-lookup"><span data-stu-id="4156c-201">Similarly, pulling a module whose catalog is not signed results in the following error:</span></span>

![Örnek hata çıkış modülü](../images/PullUnisgnedCatalog.png)

#### <a name="push"></a><span data-ttu-id="4156c-203">anında iletme</span><span class="sxs-lookup"><span data-stu-id="4156c-203">Push</span></span>

<span data-ttu-id="4156c-204">Düğüme teslim önce yükleme kullanılarak teslim edilen yapılandırma, kaynakta değiştirilmiş.</span><span class="sxs-lookup"><span data-stu-id="4156c-204">A configuration delivered by using push might be tampered with at its source before it delivered to the node.</span></span> <span data-ttu-id="4156c-205">Yerel Configuration Manager için gönderildi veya yayımlanmış yapılandırmaları benzer imzası doğrulama adımları gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="4156c-205">The Local Configuration Manager performs similar signature validation steps for pushed or published configuration(s).</span></span> <span data-ttu-id="4156c-206">Gönderim için imza doğrulaması için tam bir örnek aşağıdadır.</span><span class="sxs-lookup"><span data-stu-id="4156c-206">Below is a complete example of signature validation for push.</span></span>

- <span data-ttu-id="4156c-207">İmza doğrulaması düğüm üzerinde etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="4156c-207">Enable signature validation on the node.</span></span>

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

- <span data-ttu-id="4156c-208">Örnek bir yapılandırma dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="4156c-208">Create a sample configuration file.</span></span>

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

- <span data-ttu-id="4156c-209">İşaretsiz bir yapılandırma dosyası düğüme gönderme deneyin.</span><span class="sxs-lookup"><span data-stu-id="4156c-209">Try pushing the unsigned configuration file in to the node.</span></span>

  ```powershell
  Start-DscConfiguration -Path .\Test -Wait -Verbose -Force
  ```

  ![ErrorUnsignedMofPushed](../images/PushUnsignedMof.png)

- <span data-ttu-id="4156c-211">Yapılandırma dosyası, kod imzalama sertifikası kullanarak oturum açın.</span><span class="sxs-lookup"><span data-stu-id="4156c-211">Sign the configuration file using code-signing certificate.</span></span>

  ![SignMofFile](../images/SignMofFile.png)

- <span data-ttu-id="4156c-213">İmzalı MOF dosyası göndermek deneyin.</span><span class="sxs-lookup"><span data-stu-id="4156c-213">Try pushing the signed MOF file.</span></span>

  ![SignMofFile](../images/PushSignedMof.png)
