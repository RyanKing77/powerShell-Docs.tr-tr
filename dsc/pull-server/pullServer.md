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
# <a name="desired-state-configuration-pull-service"></a>İstenen durum yapılandırması çekme hizmeti

> [!IMPORTANT]
> Çekme sunucusu (Windows özelliği *DSC-Service*) Windows Server 'ın desteklenen bir bileşenidir, ancak yeni özellikler veya yetenekler sunmaya yönelik bir plan yoktur. Yönetilen istemcileri [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) geçirmeyi (Windows Server 'Da çekme sunucusunun ötesindeki özellikleri içerir) veya [burada](pullserver.md#community-solutions-for-pull-service)listelenen topluluk çözümlerinin birini kullanmaya başlamanız önerilir.

Yerel Configuration Manager, bir çekme hizmeti çözümü tarafından merkezi olarak yönetilebilir.
Bu yaklaşımı kullanırken, yönetilmekte olan düğüm bir hizmete kaydedilir ve LCM ayarlarında bir yapılandırma atanır.
Yapılandırma bağımlılıkları olarak gereken yapılandırma ve tüm DSC kaynakları makineye indirilir ve bu yapılandırmayı yönetmek için LCM tarafından kullanılır.
Yönetilmekte olan makinenin durumu hakkında bilgi, raporlama için hizmete yüklenir.
Bu kavram "çekme hizmeti" olarak anılacaktır.

Çekme hizmeti için geçerli seçenekler şunları içerir:

- Azure Otomasyonu Istenen durum yapılandırma hizmeti
- Windows Server üzerinde çalışan bir çekme hizmeti
- Topluluk tarafından tutulan açık kaynaklı çözümler
- Bir SMB paylaşma

**Önerilen çözüm**ve en fazla özelliklerle sunulan seçenek [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).

Azure hizmeti, şirket içi düğümleri özel veri merkezlerinde veya Azure ve AWS gibi genel bulutlarda yönetebilir.
Sunucularının Internet 'e doğrudan bağlanamamakta olduğu özel ortamlar için, giden trafiği yalnızca yayımlanan Azure IP aralığıyla sınırlamayı düşünün (bkz. [Azure veri MERKEZI IP aralıkları](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).

Windows Server 'da çekme hizmetinde şu anda kullanılamayan çevrimiçi hizmetin özellikleri şunlardır:

- Tüm veriler aktarım sırasında ve bekleyen saatinde şifrelenir
- İstemci sertifikaları otomatik olarak oluşturulur ve yönetilir
- [Parolaları/kimlik bilgilerini](/azure/automation/automation-credentials)ya da sunucu adları veya bağlantı dizeleri gibi [değişkenleri](/azure/automation/automation-variables) merkezi olarak yönetmek için gizli dizileri depolar
- Düğüm [LCM yapılandırmasını](../managing-nodes/metaConfig.md#basic-settings) merkezi olarak Yönet
- İstemci düğümlerine yapılandırma merkezi olarak atama
- Üretime ulaşmadan önce test için "Canary gruplarında" yayın yapılandırması değişiklikleri
- Grafik raporlama
  - Ayrıntı düzeyi DSC kaynak düzeyinde durum ayrıntısı
  - Sorun giderme için istemci makinelerden ayrıntılı hata iletileri
- Raporlama ve uyarı için Azure Log Analytics uyarı, otomatikleştirilmiş görevler, Android/iOS uygulaması [Ile tümleştirme](/azure/automation/automation-dsc-diagnostics)

## <a name="dsc-pull-service-in-windows-server"></a>Windows Server 'da DSC çekme hizmeti

Bir çekme hizmetini Windows Server 'da çalışacak şekilde yapılandırmak mümkündür.
Windows Server 'a dahil olan çekme hizmeti çözümünün yalnızca yapılandırma ve rapor verilerini veritabanına yükleme için depolama yeteneklerini içermesi önerilir.
Azure 'da hizmetin sunduğu birçok özelliği içermez ve bu nedenle hizmetin nasıl kullanılacağını değerlendirmek için iyi bir araç değildir.

Windows Server 'da sunulan çekme hizmeti, bir OData arabirimi kullanan bir Web hizmetidir ve bu düğümler, bu düğümleri isteyenler için DSC yapılandırma dosyalarını hedef düğümlere kullanılabilir hale getirir.

Çekme sunucusu kullanma gereksinimleri:

- Çalıştıran bir sunucu:
  - WMF/PowerShell 4,0 veya üzeri
  - IIS sunucu rolü
  - DSC hizmeti
- Hedef düğümlerde yerel Configuration Manager (LCM) geçirilen kimlik bilgilerinin güvenliğini sağlamak için bir sertifika oluşturmanın bazı yolları idealdir.

Windows Server 'ı çekme hizmetini barındıracak şekilde yapılandırmanın en iyi yolu DSC yapılandırması kullanmaktır.
Aşağıda örnek bir komut dosyası verilmiştir.

### <a name="supported-database-systems"></a>Desteklenen veritabanı sistemleri

|WMF 4,0   |WMF 5.0  |WMF 5.1 |WMF 5,1 (Windows Server Insider Preview 17090)|
|---------|---------|---------|---------|
|TATIL     |ESENT (varsayılan), MDB |ESENT (varsayılan), MDB|ESENT (varsayılan), SQL Server, MDB

[Windows Server Insider Preview](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewserver)sürüm 17090 ' den başlayarak, çekme hizmeti (Windows özelliği *DSC-Service*) için desteklenen bir seçenektir SQL Server. Bu, [Azure Automation DSC](/azure/automation/automation-dsc-getting-started)'e geçirilmeyen büyük DSC ortamlarını ölçeklendirmek için yeni bir seçenek sağlar.

> [!NOTE]
> SQL Server desteği, WMF 5,1 (veya önceki bir sürümü) önceki sürümlerine eklenmez ve yalnızca 17090 ' den büyük veya buna eşit olan Windows Server sürümlerinde kullanılabilir.

Çekme sunucusunu SQL Server kullanacak şekilde yapılandırmak için, **SqlProvider** `$true` ' ı ve **sqlConnectionString** ' i geçerli bir SQL Server bağlantı dizesine ayarlayın. Daha fazla bilgi için bkz. [SqlClient bağlantı dizeleri](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings).
**Xdscwebservice**ile SQL Server yapılandırmasına bir örnek için Ilk olarak [xdscwebservice kaynağını kullanarak](#using-the-xdscwebservice-resource) okuyun ve ardından [GitHub 'da Sample_xDscWebServiceRegistration_UseSQLProvider. ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1)' yi inceleyin.

### <a name="using-the-xdscwebservice-resource"></a>XDscWebService kaynağını kullanma

Bir Web çekme sunucusu ayarlamanın en kolay yolu, **Xpsdesiredstateconfiguration** modülüne dahil edilen **xdscwebservice** kaynağını kullanmaktır.
Aşağıdaki adımlarda, kaynağı Web hizmetini ayarlayan bir yapılandırmada kullanma açıklanmaktadır.

1. **Xpsdesiredstateconfiguration** modülünü yüklemek için [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet 'ini çağırın.
   > [!NOTE]
   > **Install-Module** , PowerShell 5,0 ' de bulunan **PowerShellGet** modülüne dahildir. PowerShell 3,0 ve 4,0 için **PowerShellGet** modülünü [PackageManagement PowerShell modülleri önizlemesine](https://www.microsoft.com/en-us/download/details.aspx?id=49186)indirebilirsiniz.
2. Kuruluşunuzun içinde veya genel yetkilinizden, güvenilir bir sertifika yetkilisinden DSC çekme sunucusu için bir SSL sertifikası alın. Yetkilinden alınan sertifika genellikle PFX biçimindedir.
3. Varsayılan konumda `CERT:\LocalMachine\My`DSC çekme sunucusu olacak olan düğüme sertifikayı yükler.
   - Sertifika parmak izini bir yere getirin.
4. Kayıt anahtarı olarak kullanılacak bir GUID seçin. PowerShell kullanarak bir tane oluşturmak için PS isteminde aşağıdakini girin ve ENTER tuşuna basın: `[guid]::newGuid()` veya. `New-Guid` Bu anahtar, kayıt sırasında kimlik doğrulaması için paylaşılan anahtar olarak istemci düğümleri tarafından kullanılacaktır. Daha fazla bilgi için aşağıdaki kayıt anahtarı bölümüne bakın.
5. PowerShell ıSE 'de, aşağıdaki yapılandırma betiğini (F5) başlatın ( **Xpsdesiredstateconfiguration** modülünün `Sample_xDscWebServiceRegistration.ps1`örnekler klasörüne dahil). Bu betik, çekme sunucusunu ayarlar.

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

6. SSL sertifikasının parmak izini **certificateThumbPrint** parametresi olarak ve bir GUID kayıt anahtarını **registrationkey** parametresi olarak geçirerek yapılandırmayı çalıştırın:

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

İstemci düğümlerinin bir yapılandırma kimliği yerine yapılandırma adlarını kullanabilmesi için sunucuya kaydedilmesine izin vermek üzere, yukarıdaki yapılandırma tarafından oluşturulan bir kayıt anahtarı içinde `RegistrationKeys.txt` `C:\Program Files\WindowsPowerShell\DscService`adlı bir dosyaya kaydedilir. Kayıt anahtarı, istemci tarafından çekme sunucusuna ilk kayıt sırasında kullanılan bir paylaşılan gizli dizi olarak çalışır. İstemci, kayıt başarıyla tamamlandıktan sonra çekme sunucusuna benzersiz olarak kimlik doğrulaması yapmak için kullanılan otomatik olarak imzalanan bir sertifika oluşturur. Bu sertifikanın parmak izi yerel olarak depolanır ve çekme sunucusunun URL 'SI ile ilişkilendirilir.

> [!NOTE]
> Kayıt anahtarları PowerShell 4,0 ' de desteklenmez.

Bir düğümü, çekme sunucusunda kimlik doğrulaması yapacak şekilde yapılandırmak için, kayıt anahtarının bu çekme sunucusuna kaydedilecek herhangi bir hedef düğüm için metaconfiguration içinde olması gerekir. Aşağıdaki metaconfiguration içindeki **registrationkey** 'in, hedef makine başarıyla kaydedildikten sonra kaldırıldığını ve değerin çekme sunucusundaki `RegistrationKeys.txt` dosyasında depolanan değerle eşleşmesi gerektiğini unutmayın (' 140a952b-b9d6-406b-B416-e0f759c9c0e4 ' Bu örnek için). Her zaman, tüm hedef makinelerin çekme sunucusuna kaydedilmesine izin verdiğini bilerek, kayıt anahtarı değerini güvenli şekilde değerlendirin.

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
> **Reportserverweb** bölümü raporlama verilerinin çekme sunucusuna gönderilmesine izin verir.

Metaconfiguration dosyasındaki **ConfigurationId** özelliğinin olmaması, çekme sunucusunun, çekme sunucusu protokolünün v2 sürümünü, bu nedenle bir ilk kaydın gerekli olduğu anlamına gelir.
Buna karşılık, bir **ConfigurationId** varlığı, çekme sunucusu protokolünün v1 sürümünün kullanıldığı ve kayıt işlemenin bulunmadığı anlamına gelir.

> [!NOTE]
> Bir gönderme senaryosunda, geçerli yayında bir hata var ve bu, bir çekme sunucusuna hiç kaydedilmemiş düğümler için metaconfiguration dosyasında bir ConfigurationId özelliği tanımlamanızı sağlar. Bu, v1 çekme sunucusu protokolünü zorlar ve kayıt hatası iletilerini önler.

## <a name="placing-configurations-and-resources"></a>Yapılandırma ve kaynakları yerleştirme

Çekme sunucusu kurulumu tamamlandıktan sonra, çekme sunucusu yapılandırmasındaki **ConfigurationPath** ve **ModulePath** özellikleri tarafından tanımlanan klasörler, hedef düğümlerin çekmesini sağlamak için kullanılabilecek modülleri ve yapılandırmaları yerleştireceğiniz yerdir.
Bu dosyaların, çekme sunucusunun düzgün şekilde işlemesi için belirli bir biçimde olması gerekir.

### <a name="dsc-resource-module-package-format"></a>DSC kaynak modülü paket biçimi

Her kaynak modülünün sıkıştırılmış ve aşağıdaki modele `{Module Name}_{Module Version}.zip`göre adlandırılmış olması gerekir.

Örneğin, xWebAdminstration adlı bir modülün Modül sürümü 3.1.2.0 olarak adlandırılır `xWebAdministration_3.1.2.0.zip`.
Modülün her sürümü tek bir ZIP dosyasında bulunmalıdır.
Her ZIP dosyasında bir kaynağın yalnızca tek bir sürümü olduğundan, WMF 5,0 ' de tek bir dizinde birden çok modül sürümü desteğiyle eklenen modül biçimi desteklenmez.
Diğer bir deyişle, çekme sunucusu ile kullanım için DSC kaynak modüllerini paketlemeden önce dizin yapısında küçük bir değişiklik yapmanız gerekir.
WMF 5,0 ' de DSC kaynağını içeren modüllerin varsayılan biçimi vardır `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.
Çekme sunucusuna paketlemeden önce, yol haline `{Module Folder}\DscResources\{DSC Resource Folder}\`gelmesi için **{module sürümü}** klasörünü kaldırın.
Bu değişiklik ile, yukarıda açıklandığı gibi klasörü zip halinde ve bu ZIP dosyalarını **ModulePath** klasörüne yerleştirin.

Yeni `New-DscChecksum {module zip file}` eklenen modül için bir sağlama toplamı dosyası oluşturmak için kullanın.

### <a name="configuration-mof-format"></a>Yapılandırma MOF biçimi

Bir hedef düğümdeki LCM 'nin yapılandırmayı doğrulayabilmesi için bir yapılandırma MOF dosyasının bir sağlama toplamı dosyasıyla eşleştirilmesi gerekir.
Sağlama toplamı oluşturmak için [New-DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DscChecksum) cmdlet 'ini çağırın.
Cmdlet 'i, yapılandırma MOF 'nin bulunduğu klasörü belirten bir **yol** parametresi alır.
Cmdlet 'i adlı `ConfigurationMOFName.mof.checksum`bir sağlama toplamı dosyası oluşturur, `ConfigurationMOFName` burada yapılandırma mof dosyasının adıdır.
Belirtilen klasörde birden fazla yapılandırma MOF dosyası varsa, klasördeki her bir yapılandırma için bir sağlama toplamı oluşturulur.
MOF dosyalarını ve ilgili sağlama toplamı dosyalarını **ConfigurationPath** klasörüne yerleştirin.

> [!NOTE]
> Yapılandırma MOF dosyasını herhangi bir şekilde değiştirirseniz, sağlama toplamı dosyasını da yeniden oluşturmanız gerekir.

### <a name="tooling"></a>Araçları

İstek sunucusunu ayarlamayı, doğrulamayı ve yönetmeyi kolaylaştırmak için aşağıdaki araçlar xPSDesiredStateConfiguration modülünün en son sürümüne örnek olarak dahil edilir:

1. Çekme sunucusunda kullanılmak üzere DSC kaynak modüllerinin ve yapılandırma dosyalarının paketlenmesi için yardımcı olacak bir modül.
   [PublishModulesAndMofsToPullServer. psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).
   Aşağıdaki örnekler:

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @('xWebAdministration', 'xPhp')
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. Çekme sunucusunu doğrulayan bir betik doğru şekilde yapılandırılır. [Pullserversetuptests. ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).

## <a name="community-solutions-for-pull-service"></a>Çekme hizmeti için topluluk çözümleri

DSC topluluğu, çekme hizmeti protokolünü uygulamak için birden çok çözüm yazdı.
Şirket içi ortamlar için, bu teklif çekme hizmeti özellikleri ve artımlı geliştirmeler sayesinde topluluğa katkıda bulunmak için bir fırsat sunar.

- [Tug](https://github.com/powershellorg/tug)
- [DSC-TRÆK](https://github.com/powershellorg/dsc-traek)

## <a name="pull-client-configuration"></a>İstek temelli istemci yapılandırması

Aşağıdaki konularda, çekme istemcilerinin ayrıntılı olarak ayarlanması açıklanır:

- [Bir DSC çekme istemcisini yapılandırma KIMLIĞI kullanarak ayarlama](pullClientConfigID.md)
- [Yapılandırma adlarını kullanarak DSC çekme istemcisini ayarlama](pullClientConfigNames.md)
- [Kısmi yapılandırma](partialConfigs.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Windows PowerShell Istenen durum yapılandırmasına genel bakış](../overview/overview.md)
- [Yapılandırmaları Kabul Etme](enactingConfigurations.md)
- [DSC rapor sunucusu kullanma](reportServer.md)
- [[MS-DSCPM]: İstenen durum yapılandırması Istek modeli Protokolü](https://msdn.microsoft.com/library/dn393548.aspx)
- [[MS-DSCPM]: İstenen durum yapılandırması Istek modeli protokol Eroytası](https://msdn.microsoft.com/library/mt612824.aspx)
