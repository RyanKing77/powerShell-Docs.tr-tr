---
ms.date: 04/11/2018
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC Çekme Hizmeti
ms.openlocfilehash: 659a8f8b2ce7d34058e789c5de336dc1f1f2abb2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687800"
---
# <a name="desired-state-configuration-pull-service"></a>Desired State Configuration çekme hizmeti

> Şunun için geçerlidir: Windows PowerShell 5.0

> [!IMPORTANT]
> Çekme sunucusu (Windows özelliği *DSC hizmet*) ancak desteklenen bir bileşen Windows Server'ın yeni özellikler veya yetenekler sunmak için herhangi bir plan vardır. Geçişi başlıyor önerilir yönetilen istemcilere [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (Windows Server çekme sunucusunda dışında özellikler dahildir) veya topluluk çözümlerden birini listelenen [burada](pullserver.md#community-solutions-for-pull-service).

Yerel Configuration Manager, bir çekme hizmetini çözümü tarafından merkezi olarak yönetilebilir.
Bu yaklaşımı kullanarak, yönetilen düğüme bir hizmete kayıtlı ve LCM ayarları yapılandırmasında atanan.
Yapılandırması ve yapılandırma için bağımlılık olarak gerekli olan tüm DSC kaynaklarını makineye indirilir ve yapılandırmasını yönetmek için LCM tarafından kullanılır.
Yönetilen makinenin durumu hakkında bilgi, hizmet raporlama için yüklenir.
Bu kavramı "çekme hizmeti." olarak adlandırılır

Çekme Hizmeti için geçerli seçenekler şunlardır:

- Azure Otomasyonu Desired State Configuration hizmeti
- Windows Server üzerinde çalışan bir çekme hizmeti
- Açık kaynak çözümleri tutulan topluluk
- SMB paylaşımı

**Önerilen Çözüm**, ve en çok kullanılabilir olan özellikleri seçeneğiyle [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).

Azure hizmet düğümleri şirket içi özel veri merkezinde veya genel bulutlarda Azure ve AWS gibi yönetebilirsiniz.
Yalnızca yayımlanan Azure IP aralığına giden trafiği sınırlamak burada sunucuları doğrudan bağlanamaz Internet'e özel ortamları için göz önünde bulundurun (bkz [Azure veri merkezi IP aralıkları](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).

Çevrimiçi hizmet çekme hizmetini Windows Server üzerinde şu anda kullanılabilir olmayan özellikler şunlardır:
- Tüm veriler aktarımda ve bekleme sırasında şifrelenir
- İstemci sertifikaları oluşturulur ve otomatik olarak yönetilir
- Gizli dizileri depolamak merkezi olarak yönetmek için [parolaları/kimlik bilgilerinin](/azure/automation/automation-credentials), veya [değişkenleri](/azure/automation/automation-variables) sunucu adları veya bağlantı dizeleri gibi
- Düğüm merkezi olarak yönetin [LCM yapılandırma](../managing-nodes/metaConfig.md#basic-settings)
- Merkezi olarak istemci düğüm yapılandırmaları Ata
- Üretim ulaşmadan önce test etmek için "kanarya gruplarına" yayın yapılandırması değişiklikleri
- Grafik raporlama
  - DSC kaynak düzeyinde ayrıntı durumu ayrıntısı
  - Sorun giderme için istemci makinelerden ayrıntılı hata iletileri
- [Azure Log Analytics ile tümleştirme](/azure/automation/automation-dsc-diagnostics) uyarı verme, otomatik görevler, raporlama ve uyarı Android/iOS uygulaması

## <a name="dsc-pull-service-in-windows-server"></a>Windows Server'da DSC çekme hizmeti

Windows Server üzerinde çalıştırmak için bir çekme hizmetini yapılandırmak için mümkündür.
Windows Server'a dahil çekme hizmet çözümü yapılandırmaları/modules indirmek için depolama ve veritabanı için rapor verilerini yakalama yalnızca özellikleri içerdiğinden emin olun.
Çoğu Azure hizmeti tarafından sunulan içermez ve bu nedenle nasıl hizmet kullanılan değerlendirmek için iyi bir aracı değildir.

Windows Server'da sunulan çekme hizmetini bir düğümleri için isteyin, DSC yapılandırma dosyalarını hedef düğümler için kullanılabilir hale getirmek için bir OData arabirimini kullanan bir IIS web hizmetidir.

Bir çekme sunucusu kullanmak için gereksinimler:

- Çalıştıran bir sunucu:
  - WMF/PowerShell 5.0 veya üzeri
  - IIS sunucu rolü
  - DSC hizmeti
- İdeal olarak, bazı anlamına gelir bir sertifika oluşturma hedef düğümlerde yerel Configuration Manager (LCM) geçirilen kimlik bilgilerini güvenli hale getirmek için

Windows Server için konak çekme hizmetini yapılandırmak için en iyi yolu, bir DSC yapılandırması kullanmaktır.
Bir örnek betiği aşağıda verilmiştir.

### <a name="supported-database-systems"></a>Desteklenen veritabanı sistemleri

|WMF 4.0   |WMF 5.0  |WMF 5.1 |WMF 5.1 (Windows Server Insider Önizleme 17090)|
|---------|---------|---------|---------|
|MDB     |ESENT (varsayılan), MDB |ESENT (varsayılan), MDB|ESENT (varsayılan), SQL Server'ı MDB

İtibariyle, 17090 yayın [Windows Server Insider Preview](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewserver), SQL Server, çekme hizmeti için desteklenen bir seçenektir (Windows özelliği *DSC hizmet*).  Bunun için geçmemiş büyük DSC ortamlarda ölçeklendirmeye yönelik yeni bir seçenek sağlar [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).

> **Not**: SQL Server desteği, önceki sürümler için WMF 5.1 (veya öncesi) eklenmez ve yalnızca Windows Server sürümlerinde büyüktür veya eşittir 17090 için kullanılabilir olacak.

Çekme sunucusunu SQL Server'ı kullanacak şekilde yapılandırmak için **SqlProvider** için `$true` ve **SqlConnectionString** için geçerli bir SQL Server bağlantı dizesi.  Daha fazla bilgi için [SqlClient bağlantı dizeleri](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings).
Bir örnek ile SQL Server yapılandırmasının **xDscWebService**, öncelikle [xDscWebService kaynak kullanarak](#using-the-xdscwebservice-resource) ve daha sonra gözden [Sample_xDscWebServiceRegistration_ GitHub üzerinde UseSQLProvider.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1).

### <a name="using-the-xdscwebservice-resource"></a>XDscWebService kaynağı kullanma

Web çekme sunucusu kurmak için en kolay yolu kullanmaktır **xDscWebService** dahil kaynak **xPSDesiredStateConfiguration** modülü.
Aşağıdaki adımlarda, kaynak web hizmeti oluşturmaya ayarlar bir yapılandırmada kullanmak açıklanmaktadır.

1. Çağrı [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet'ine **xPSDesiredStateConfiguration** modülü. **Not**: **Install-Module** dahil **PowerShellGet** modülü, PowerShell 5. 0'da dahildir. İndirebileceğiniz **PowerShellGet** modülü PowerShell 3.0 ve 4.0, [PackageManagement PowerShell modülleri Önizleme](https://www.microsoft.com/en-us/download/details.aspx?id=49186).
1. Bir SSL sertifikası güvenilen bir sertifika yetkilisi, kuruluşunuz veya bir ortak yetkilisi ya da DSC çekme sunucusu alın. Genellikle yetkilisinden alınan sertifika PFX biçimi ' dir. DSC çekme sunucusu CERT: \LocalMachine\My olmalıdır varsayılan konumda olacak düğüme sertifikayı yükleyin. Sertifika parmak izini not edin.
1. Kayıt anahtarı kullanılacak bir GUID seçin. İçin bir PowerShell kullanarak, PS istemine aşağıdakileri girin ve enter tuşuna basın: '``` [guid]::newGuid()```'veya'```New-Guid```'. Bu anahtar tarafından istemci düğümleri kayıt sırasında kimlik doğrulaması için paylaşılan bir anahtar olarak kullanılır. Daha fazla bilgi için kayıt anahtarı bölümüne bakın.
1. PowerShell ISE'de (F5) aşağıdaki yapılandırma betiğini Başlat (örnekler klasöründe bulunan **xPSDesiredStateConfiguration** modül Sample_xDscWebServiceRegistration.ps1 olarak). Bu betik, çekme sunucusu ayarlar.

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

1. Çalıştırma SSL sertifikası parmak izi geçirme yapılandırmasını **certificateThumbPrint** parametre ve bir GUID kayıt anahtarı olarak **RegistrationKey** parametresi:

    ```powershell
    # To find the Thumbprint for an installed SSL certificate for use with the pull server list all certificates in your local store
    # and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
    dir Cert:\LocalMachine\my

    # Then include this thumbprint when running the configuration
    Sample_xDscWebServiceRegistration -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutputPath c:\Configs\PullServer

    # Run the compiled configuration to make the target node a DSC Pull Server
    Start-DscConfiguration -Path c:\Configs\PullServer -Wait -Verbose
    ```

#### <a name="registration-key"></a>Kayıt anahtarı

İstemci yapılandırma adları yerine bir yapılandırma kimliği kullanabilmeniz sunucusu ile kayıt düğümleri izin vermek için yukarıdaki yapılandırma tarafından oluşturulan bir kayıt anahtarı adlı bir dosyaya kaydedilir `RegistrationKeys.txt` içinde `C:\Program Files\WindowsPowerShell\DscService`. Kayıt anahtarı, ilk kayıt sırasında çekme sunucusu ile istemci tarafından kullanılan paylaşılan gizlilik işlevini görür. İstemci kayıt başarıyla tamamlandıktan sonra çekme sunucusuna benzersiz kimliğini doğrulamak için kullanılan otomatik olarak imzalanan bir sertifika oluşturur. Bu sertifikanın parmak izini yerel olarak depolanan ve çekme sunucusu URL'si ile ilişkili.
> **Not**: PowerShell 4. 0'kayıt anahtarları desteklenmiyor.

Çekme sunucusu ile kimlik doğrulaması için bir düğüm yapılandırmak için kayıt anahtarını metaconfiguration bu çekme sunucusu ile kayıt herhangi bir hedef düğüm için yer alması gerekir. Unutmayın **RegistrationKey** aşağıdaki metaconfiguration hedef makine başarıyla kaydolduğunu ve ' % s'değeri '140a952b-b9d6-406b-b416-e0f759c9c0e4' içinde depolanan değeri ile eşleşen sonra kaldırılır. Çekme sunucusunda RegistrationKeys.txt dosya. Her zaman farkında çekme sunucusu ile kayıt herhangi bir hedef makine izin verdiğinden kayıt anahtar değeri güvenli bir şekilde, kabul eder.

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

> **Not**: **ReportServerWeb** bölümü raporlama verilerini çekme sunucusuna gönderilmesini sağlar.

Eksikliği **ConfigurationID** metaconfiguration dosyasındaki özellik örtük olarak anlamına gelir, çekme sunucusu bir ilk kaydı gerekli olacak şekilde çekme sunucusu protokolü V2 sürümünü destekleme.
Buna karşılık, varlığı bir **ConfigurationID** çekme sunucusu protokolü V1 sürümü kullanılır ve hiçbir kayıt işleme yoktur anlamına gelir.

>**Not**: Bir anında İLETME senaryosunda, hiçbir zaman bir çekme sunucusuna kaydettirdiyseniz düğümleri metaconfiguration dosyasında ConfigurationID özelliği tanımlamak gerekli kılan geçerli sürümde olan bir hata var. V1 çekme sunucusu protokolü zorlamak ve kayıt hata iletileri kaçının.

## <a name="placing-configurations-and-resources"></a>Yapılandırmaları ve kaynakları yerleştirme

Sonra çekme Sunucusu Kurulumu tamamlandığında, tarafından tanımlanan klasörleri **Yapılandırmayolu** ve **ModulePath** çekme sunucusu yapılandırma özelliklerinde olan modülleri ve yapılandırmaları koyacağı Hedef düğümleri çekmek kullanılabilir.
Bu dosyalar çekme sunucusunun doğru şekilde işlemek sırada belirli bir biçimde olması gerekir.

### <a name="dsc-resource-module-package-format"></a>DSC kaynak modülü paket biçimi

Her kaynak modülü sıkıştırılmasını ve aşağıdaki modele göre adında gereken `{Module Name}_{Module Version}.zip`.
Örneğin, xWebAdminstration 3.1.2.0 modülü sürümü ile adlı bir modül 'xWebAdministration_3.2.1.0.zip' adlı.
Her bir modül sürümü tek zip dosyasında yer almalıdır.
Bir kaynağın her zip dosyası yalnızca tek bir sürüm olduğundan, WMF 5. 0'ile tek bir dizinde birden çok modül sürümleri için destek eklendi modül biçimi desteklenmiyor.
Bu DSC çekme server ile kullanmak için kaynak modülleri'kurmak paketleme önce küçük bir değişiklik yapmak için dizin yapısını gerektiğini anlamına gelir.
WMF 5.0 DSC kaynağı içeren modüllerin varsayılan biçimi ' {modülü Folder}\{Modül sürümü} \DscResources\{DSC kaynak klasörünü}\'.
Çekme sunucusu için paketleme önce kaldırmak **{Modül sürümü}** yolu olacak şekilde klasör ' {modülü Folder} \DscResources\{DSC kaynak klasörünü}\'.
Bu değişiklik, yukarıda açıklandığı gibi klasör zip ve bu zip dosyalarını **ModulePath** klasör.

Kullanım `New-DscChecksum {module zip file}` yeni eklenen modülün bir sağlama toplamı dosyası oluşturmak için.

### <a name="configuration-mof-format"></a>Yapılandırma MOF biçimi

Yapılandırma MOF dosyasının yapılandırmasını hedef düğümde bir LCM doğrulayabilmesi bir sağlama toplamı dosyasına ile eşleştirilmesi gerekir.
Bir sağlama toplamı oluşturmak için arama [yeni DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DscChecksum) cmdlet'i.
Cmdlet alır bir **yolu** parametresi yapılandırma MOF bulunduğu klasörü belirtir.
Adlı bir sağlama toplamı dosyasına cmdlet oluşturur `ConfigurationMOFName.mof.checksum`burada `ConfigurationMOFName` yapılandırma mof dosyasının adıdır.
Belirtilen klasörde MOF dosyaları birden fazla yapılandırması varsa, klasördeki her bir yapılandırma için bir sağlama toplamı oluşturulur.
MOF dosyaları ve bunların ilişkili sağlama toplamı dosyalarında yerleştirmek **Yapılandırmayolu** klasör.

>**Not**: Yapılandırma MOF dosyasının herhangi bir şekilde değiştirirseniz, sağlama toplamı dosyasına yeniden oluşturmanız gerekir.

### <a name="tooling"></a>Araç kullanımı

Ayarı yapmak için doğrulama ve daha kolay, çekme sunucusu yönetme aşağıdaki araçları xPSDesiredStateConfiguration modülünün en son sürümünü örneklerde olarak dahil edilir:

1. DSC kaynak modülleri ve çekme sunucusu kullanmak için yapılandırma dosyalarını paketleme ile yardımcı olacak bir modül. [PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1). Aşağıdaki örnekler:

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @('xWebAdministration', 'xPhp')
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. Çekme sunucusu doğrulayan bir betik doğru şekilde yapılandırılır. [PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).

## <a name="community-solutions-for-pull-service"></a>Topluluk çözümleriyle çekme hizmeti

Topluluk DSC çekme hizmeti Protokolü uygulamak için birden çok çözümü yazan.
Şirket içi ortamlar için bu çekme hizmet özellikleri ve geri artımlı iyileştirmeleri topluluğa katkıda fırsatı sunar.

- [Arasında bir güç çekişmesi](https://github.com/powershellorg/tug)
- [DSC TRÆK](https://github.com/powershellorg/dsc-traek)

## <a name="pull-client-configuration"></a>Çekme istemcisi yapılandırması

Aşağıdaki konularda ayrıntılı çekme istemciler ayarlama açıklanmaktadır:

- [Yapılandırma Kimliğini kullanarak bir DSC çekme istemcisi ayarlama](pullClientConfigID.md)
- [Yapılandırma adlarını kullanarak bir DSC çekme istemcisi ayarlama](pullClientConfigNames.md)
- [Kısmi yapılandırmalar](partialConfigs.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Windows PowerShell Desired State Configuration ' ne genel bakış](../overview/overview.md)
- [Yapılandırmaları Kabul Etme](enactingConfigurations.md)
- [DSC rapor sunucusu kullanma](reportServer.md)
- [[MS-DSCPM]: Çekme modeli Protokolü Desired State Configuration](https://msdn.microsoft.com/library/dn393548.aspx)
- [[MS-DSCPM]: Çekme modeli Protokolü Errata Desired State Configuration](https://msdn.microsoft.com/library/mt612824.aspx)
