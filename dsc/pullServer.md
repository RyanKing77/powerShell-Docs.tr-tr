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
# <a name="desired-state-configuration-pull-service"></a>İstenen durum yapılandırma çekme hizmeti

> İçin geçerlidir: Windows PowerShell 5.0

> [!IMPORTANT]
> Çekme sunucusuna (Windows özelliği *DSC hizmet*) vardır ancak desteklenen bir bileşen Windows Server'ın yeni özellikleri veya yetenekleri sunmak için herhangi bir plan vardır. Geçiş başlamak için önerilen yönetilen istemcilere [Azure Otomasyonu DSC](/azure/automation/automation-dsc-getting-started) (Windows Server çekme sunucusunda ötesinde özellikler içerir) veya topluluk çözümlerden birini listelenen [burada](pullserver.md#community-solutions-for-pull-service).

Yerel Configuration Manager, bir çekme hizmet çözümü tarafından merkezi olarak yönetilebilir.
Bu yaklaşımı kullanarak, yönetilmekte olan düğüm bir hizmete kayıtlı ve yapılandırma LCM'yi ayarlarında atanmış.
Yapılandırma ve bağımlılık yapılandırması için gereken tüm DSC kaynakları makineye indirilir ve yapılandırmasını yönetmek için LCM'yi tarafından kullanılır.
Yönetilen makinenin durumu hakkında bilgi, hizmet raporlama için yüklenir.
Bu kavram "çekme hizmeti." olarak adlandırılır

Çekme Hizmeti için geçerli seçenekler şunlardır:

- Azure Otomasyonu istenen durum Yapılandırma hizmeti
- Windows Server'da çalışan bir çekme hizmeti
- Açık kaynak çözümleri tutulan topluluk
- SMB paylaşımı

**Önerilen Çözüm**, ve en çok kullanılabilir olan özellikleri seçeneğiyle [Azure Otomasyonu DSC](/azure/automation/automation-dsc-getting-started).

Azure hizmet düğümleri şirket içi özel veri merkezleri veya genel Bulutlar Azure ve AWS gibi yönetebilirsiniz.
Burada sunucuları doğrudan bağlanamıyor Internet'e özel ortamları için yalnızca yayımlanan Azure IP aralığına giden trafiği kullanabilirsiniz (bkz [Azure veri merkezi IP aralıkları](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).

Şu anda Windows Server'da çekme Hizmet kullanılamıyor çevrimiçi hizmet özelliklerini içerir:
- Yoldaki ve bekleyen tüm veriler şifrelenir
- İstemci sertifikalarını oluşturulur ve otomatik olarak yönetilir
- Parolaları depolamak merkezi olarak yönetmek için [parolaları/kimlik bilgilerinin](/azure/automation/automation-credentials), veya [değişkenleri](/azure/automation/automation-variables) sunucu adlarını veya bağlantı dizeleri gibi
- Düğüm merkezi olarak yönetmenize [LCM'yi yapılandırma](metaConfig.md#basic-settings)
- Merkezi olarak istemci düğümlerine yapılandırmalar atama
- Üretim ulaşmadan önce test etmek için "yalancı gruplarına" yayın yapılandırma değişiklikleri
- Grafik raporlama
  - Ayrıntı düzeyi DSC kaynağı düzeyinde durumu ayrıntısı
  - Sorun giderme için istemci makinelerden ayrıntılı hata iletileri
- [Azure günlük analizi ile tümleştirme](/azure/automation/automation-dsc-diagnostics) , otomatik görevler, raporlama ve Uyarılar için Android/iOS uygulaması uyarı verme

## <a name="dsc-pull-service-in-windows-server"></a>Windows Server'daki DSC çekme hizmeti

Bir çekme hizmetini Windows Server üzerinde çalışacak şekilde yapılandırmak için mümkündür.
Windows Server'da bulunan çekme hizmet çözümünü yapılandırmaları/modüllerini yüklemek için depolama ve veritabanı için rapor verileri yakalama yalnızca yetenekleri içerir dikkat edin.
Çoğu Azure hizmeti tarafından sunulan yetenekleri içermez ve bu nedenle nasıl hizmeti kullanılan değerlendirmek için iyi bir aracı değildir.

Windows Server'da sunulan çekme hizmeti düğümleri için söylediğinizde DSC yapılandırma dosyalarını hedef düğümleri kullanılabilir hale getirmek için bir OData arabirimi kullanır IIS'de bir web hizmetidir.

Bir çekme sunucusuna kullanmak için gereksinimler:

- Çalıştıran bir sunucuda:
  - WMF/PowerShell 5.0 veya daha büyük
  - IIS sunucu rolü
  - DSC hizmeti
- İdeal olarak, bazı anlamına gelir bir sertifika oluşturma hedef düğümlerine yerel Configuration Manager (LCM'yi) için geçirilen kimlik bilgileri güvenli hale getirmek için

Windows Server ana bilgisayar çekme hizmetini yapılandırmak için en iyi yolu, DSC yapılandırması kullanmaktır.
Bir örnek komut dosyası aşağıda verilmiştir.

### <a name="supported-database-systems"></a>Desteklenen veritabanı sistemleri

|WMF 4.0   |WMF 5.0  |WMF 5.1 |WMF 5.1 (Windows Server Insider Önizleme 17090)|
|---------|---------|---------|---------|
|MDB     |ESENT (varsayılan), MDB |ESENT (varsayılan), MDB|ESENT (varsayılan), SQL Server'ı MDB

İtibariyle, 17090 sürüm [Windows Server Insider Önizleme](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewserver), SQL Server, çekme hizmeti için desteklenen bir seçenek (Windows özelliği *DSC hizmet*).  Bunun için geçirilen değil büyük DSC ortamları ölçeklendirmeye yönelik yeni bir seçenek sağlar [Azure Otomasyonu DSC](/azure/automation/automation-dsc-getting-started).

> **Not**: SQL Server desteği önceki sürümler için WMF 5.1 (veya öncesi) eklenmez ve yalnızca Windows Server sürümlerinde büyük veya ona eşit 17090 için kullanılabilir.

Çekme sunucusunu SQL Server kullanacak biçimde yapılandırmak için ayarlayın **SqlProvider** için `$true` ve **SqlConnectionString** geçerli bir SQL Server bağlantı dizesi.  Daha fazla bilgi için bkz: [SqlClient bağlantı dizeleri](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings).
Bir örnek için SQL Server yapılandırma ile **xDscWebService**, öncelikle [xDscWebService kaynağı kullanan](#using-the-xdscwebservice-resource) ve daha sonra gözden [Sample_xDscWebServiceRegistration_ Github'da UseSQLProvider.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1).

### <a name="using-the-xdscwebservice-resource"></a>XDscWebService kaynak kullanma

Bir web çekme sunucusu kurmak için en kolay yolu kullanmaktır **xDscWebService** dahil kaynak **xPSDesiredStateConfiguration** modülü.
Aşağıdaki adımları, kaynak web hizmeti oluşturan ayarlar bir yapılandırmada kullanmak açıklanmaktadır.

1. Çağrı [yükleme-Module](/powershell/module/PowershellGet/Install-Module) yüklemek için cmdlet'i **xPSDesiredStateConfiguration** modülü. **Not**: **yükleme-Module** dahil **PowerShellGet** PowerShell 5. 0 ' dahil modülü. İndirebilirsiniz **PowerShellGet** için modülü PowerShell 3.0 ve 4.0 en [PackageManagement PowerShell modülleri Önizleme](https://www.microsoft.com/en-us/download/details.aspx?id=49186).
1. Bir güvenilen sertifika yetkilisi, kuruluşunuz ya da bir ortak yetkilisinden içinde ya da DSC çekme sunucusu için bir SSL sertifikası alın. Yetkilisinden alınan sertifika genellikle PFX biçimindedir. DSC çekme sunucusuna CERT: \LocalMachine\My olmalıdır varsayılan konumda olacak düğüm üzerinde sertifikayı yükleyin. Sertifika parmak izini not edin.
1. Kayıt anahtarı olarak kullanılacak bir GUID seçin. Bir oluşturmak için PowerShell kullanarak PS istemine aşağıdakileri girin ve ENTER tuşuna basın: '``` [guid]::newGuid()```'veya'```New-Guid```'. Bu anahtar istemci düğümleri tarafından kayıt sırasında kimlik doğrulaması için paylaşılan bir anahtar olarak kullanılır. Daha fazla bilgi için aşağıdaki kayıt anahtarı bölümüne bakın.
1. PowerShell ISE aşağıdaki yapılandırma komut dosyası (F5) başlatın (örnekler klasöründe bulunan **xPSDesiredStateConfiguration** modülü Sample_xDscWebServiceRegistration.ps1 olarak). Bu komut çekme sunucusunda ayarlar.

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

1. Sertifikanın parmak izi SSL geçirme yapılandırmayı çalıştırın **certificateThumbPrint** parametre ve bir GUID kayıt anahtarı olarak **RegistrationKey** parametre:

```powershell
# To find the Thumbprint for an installed SSL certificate for use with the pull server list all certificates in your local store
# and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
dir Cert:\LocalMachine\my

# Then include this thumbprint when running the configuration
Sample_xDSCPullServer -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutputPath c:\Configs\PullServer

# Run the compiled configuration to make the target node a DSC Pull Server
Start-DscConfiguration -Path c:\Configs\PullServer -Wait -Verbose
```

#### <a name="registration-key"></a>Kayıt anahtarı

İstemci yapılandırması kimliği yerine yapılandırma adları kullanabilmeleri sunucusu ile kayıt düğümleri izin vermek için yukarıdaki yapılandırması tarafından oluşturulan bir kayıt anahtarı adlı bir dosyaya kaydedilir `RegistrationKeys.txt` içinde `C:\Program Files\WindowsPowerShell\DscService`. Kayıt anahtarını ilk kaydı sırasında çekme sunucu ile istemci tarafından kullanılan bir paylaşılan gizlilik olarak çalışır. İstemci kayıt başarıyla tamamlandıktan sonra çekme sunucusuna benzersiz kimliğini doğrulamak için kullanılan otomatik olarak imzalanan bir sertifika oluşturur. Bu sertifikanın parmak izini yerel olarak depolanır ve çekme sunucu URL'si ile ilişkili.
> **Not**: Kayıt anahtarlarını PowerShell 4. 0'desteklenmiyor.

Çekme sunucunun kimliğini doğrulamak için bir düğümü yapılandırmak için kayıt anahtarını bu çekme Server'a kaydettirirken herhangi bir hedef düğümün meta yapılandırmasını olması gerekir. Unutmayın **RegistrationKey** meta yapılandırmasını içinde aşağıdaki hedef makine başarılı bir şekilde kaydettirildi ve '140a952b-b9d6-406b-b416-e0f759c9c0e4' değeri depolanan değeriyle eşleşmelidir sonra kaldırılır. Çekme sunucusunda RegistrationKeys.txt dosyası. Her zaman farkında çekme sunucusu ile kayıt herhangi bir hedef makine verdiğinden kayıt anahtarı değeri güvenli kabul eder.

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

> **Not**: **ReportServerWeb** bölümü çekme sunucusuna gönderilecek verileri raporlama sağlar.

Eksikliği **ConfigurationID** meta yapılandırmasını dosyasında özellik örtük olarak anlamına gelir, çekme sunucu bir ilk kaydı gerekli olacak şekilde çekme sunucusu protokolü V2 sürümünü destekliyor.
Buna karşılık, varlığını bir **ConfigurationID** çekme sunucusu protokolü V1 sürümünü kullanılır ve da bir kayıt işleme anlamına gelir.

>**Not**: içinde bir anında İLETME senaryosu, bir hata var. geçerli sürümde hiçbir zaman bir çekme sunucusuna kaydettirdiyseniz düğümleri için meta yapılandırmasını dosyasındaki bir ConfigurationID özellik tanımlamak için gerekli hale getirir. V1 çekme sunucu protokolü zorlamak ve kayıt hata iletileri kaçının.

## <a name="placing-configurations-and-resources"></a>Yapılandırmaları ve kaynakları yerleştirme

Çekme sonra sunucu Kurulum tamamlandıktan, tarafından tanımlanan klasörleri **ConfigurationPath** ve **ModulePath** çekme sunucu yapılandırması özelliklerinde olan modülleri ve yapılandırmaları olduğu yerleştirir Hedef düğümleri çıkarmak kullanılabilir.
Bu dosyalar çekme sunucusunun doğru şekilde işlemek sırayla belirli bir biçimde olması gerekir.

### <a name="dsc-resource-module-package-format"></a>DSC kaynağı modülü paket biçimi

Her kaynak modül sıkıştırılmış ve göre aşağıdaki düzeni adlı gerekiyor `{Module Name}_{Module Version}.zip`.
Örneğin, 3.1.2.0 Modül sürümü xWebAdminstration adlı bir modül 'xWebAdministration_3.2.1.0.zip' adlı.
Her bir modül sürümü tek zip dosyasında yer almalıdır.
Yalnızca tek bir sürümünü her zip dosyasında bir kaynak olduğundan, WMF 5.0 ile tek bir dizin içinde birden çok modül sürümleri için destek eklendi modül biçimi desteklenmiyor.
Bu, paketleme yukarı DSC kaynakları modüllerinin çekme server ile kullanmak için önce dizin yapısını küçük değişiklik gerektiğini anlamına gelir.
WMF 5.0 DSC kaynağı içeren modüller varsayılan biçimi ' {modül klasörü}\{Modül sürümü} \DscResources\{DSC kaynak klasörünü}\'.
Çekme sunucunun kaydınızı paketleme önce kaldırmak **{Modül sürümü}** yolu olacak şekilde klasörü ' {modül klasörü} \DscResources\{DSC kaynak klasörünü}\'.
Bu değişiklikle, yukarıda açıklandığı gibi klasör zip ve bu ZIP dosyaları yerleştirmek **ModulePath** klasör.

Kullanım `New-DscChecksum {module zip file}` yeni eklenen modülü için sağlama toplamı dosya oluşturulamadı.

### <a name="configuration-mof-format"></a>Yapılandırma MOF biçimi

Bir yapılandırma MOF dosyası yapılandırmasını hedef düğümde bir LCM'yi doğrulayabilmesi bir sağlama toplamı dosyasıyla eşleştirilmiş gerekir.
Bir sağlama toplamı oluşturmak için arama [yeni DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DscChecksum) cmdlet'i.
Cmdlet geçen bir **yolu** MOF yapılandırma bulunduğu klasörü belirten parametre.
Cmdlet adlı bir sağlama toplamı dosyası oluşturur `ConfigurationMOFName.mof.checksum`, burada `ConfigurationMOFName` yapılandırma mof dosyasının adıdır.
Belirtilen klasörde MOF dosyaları birden fazla yapılandırma varsa, her yapılandırma klasörü için bir sağlama toplamı oluşturulur.
MOF dosyaları ve ilişkili sağlama toplamı dosyalarına yerleştirmek **ConfigurationPath** klasör.

>**Not**: herhangi bir şekilde yapılandırma MOF dosyasını değiştirirseniz, sağlama toplamı dosyasını da yeniden oluşturmanız gerekir.

### <a name="tooling"></a>Araçları

Ayar oluşturan için doğrulama ve daha kolay, çekme sunucusunu yönetme aşağıdaki araçları xPSDesiredStateConfiguration modülü en son sürümünü örneklerde olarak eklenir:

1. DSC kaynağı modülleri ve çekme sunucusunda kullanmak üzere yapılandırma dosyalarını paketleme ile yardımcı olacak bir modül. [PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1). Aşağıdaki örnekler:

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @('xWebAdministration', 'xPhp')
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. Çekme sunucunun doğrulayan bir komut dosyası doğru yapılandırılmamış. [PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).

## <a name="community-solutions-for-pull-service"></a>Çekme Hizmeti için topluluk çözümleri

DSC topluluk çekme hizmet protokolü uygulamak için birden çok çözümleri yazılan.
Şirket içi ortamları için bu çekme hizmet özellikleri ve geri artımlı iyileştirmeleri topluluğa katkıda fırsatı sunar.

- [Tug](https://github.com/powershellorg/tug)
- [DSC TRÆK](https://github.com/powershellorg/dsc-traek)

## <a name="pull-client-configuration"></a>Çekme istemci yapılandırması

Aşağıdaki konularda ayrıntılı çekme istemcileri ayarlama açıklanmaktadır:

- [Bir yapılandırma kimliği kullanan bir DSC çekme istemci ayarlama](pullClientConfigID.md)
- [Yapılandırma adları kullanarak bir DSC çekme istemcisi ayarlama](pullClientConfigNames.md)
- [Kısmi yapılandırmaları](partialConfigs.md)

## <a name="see-also"></a>Ayrıca bkz:

- [Windows PowerShell istenen durum yapılandırması genel bakış](overview.md)
- [Yapılandırmaları Kabul Etme](enactingConfigurations.md)
- [DSC rapor sunucusu kullanma](reportServer.md)