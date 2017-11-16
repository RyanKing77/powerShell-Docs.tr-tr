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
# <a name="setting-up-a-dsc-web-pull-server"></a>DSC çekme sunucusuna ayarlama

> İçin geçerlidir: Windows PowerShell 5.0

DSC çekme sunucusuna düğümleri için söylediğinizde DSC yapılandırma dosyalarını hedef düğümleri kullanılabilir hale getirmek için bir OData arabirimi kullanır IIS'de bir web hizmetidir.

Bir çekme sunucusuna kullanmak için gereksinimler:

* Çalıştıran bir sunucuda:
  - WMF/PowerShell 5.0 veya daha büyük
  - IIS sunucu rolü
  - DSC hizmeti
* İdeal olarak, bazı anlamına gelir bir sertifika oluşturma hedef düğümlerine yerel Configuration Manager (LCM'yi) için geçirilen kimlik bilgileri güvenli hale getirmek için

Rol ve Özellik Ekle Sihirbazı'nı kullanarak Sunucu Yöneticisi'nde veya PowerShell kullanarak IIS sunucusu rolü ve DSC hizmet ekleyebilirsiniz. Bu konuda bulunan örnek komut dosyaları bu iki adım sizin için de işleyecek.

## <a name="using-the-xdscwebservice-resource"></a>XDSCWebService kaynak kullanma
Bir web çekme sunucusu kurmak için en kolay yolu xPSDesiredStateConfiguration modülünde yer alan xWebService kaynak kullanmaktır. Aşağıdaki adımları, kaynak web hizmeti oluşturan ayarlar bir yapılandırmada kullanmak açıklanmaktadır.

1. Çağrı [yükleme-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) yüklemek için cmdlet'i **xPSDesiredStateConfiguration** modülü. **Not**: **yükleme-Module** dahil **PowerShellGet** PowerShell 5. 0 ' dahil modülü. İndirebilirsiniz **PowerShellGet** için modülü PowerShell 3.0 ve 4.0 en [PackageManagement PowerShell modülleri Önizleme](https://www.microsoft.com/en-us/download/details.aspx?id=49186). 
1. Bir güvenilen sertifika yetkilisi, kuruluşunuz ya da bir ortak yetkilisinden içinde ya da DSC çekme sunucusu için bir SSL sertifikası alın. Yetkilisinden alınan sertifika genellikle PFX biçimindedir. DSC çekme sunucusuna CERT: \LocalMachine\My olması gereken varsayılan konumda olacak düğüm üzerinde sertifikayı yükleyin. Sertifika parmak izini not edin.
1. Kayıt anahtarı olarak kullanılacak bir GUID seçin. Bir oluşturmak için PowerShell kullanarak PS istemine aşağıdakileri girin ve ENTER tuşuna basın: '``` [guid]::newGuid()```'veya'```New-Guid```'. Bu anahtar istemci düğümleri tarafından kayıt sırasında kimlik doğrulaması için paylaşılan bir anahtar olarak kullanılır. Daha fazla bilgi için aşağıdaki kayıt anahtarı bölümüne bakın.
1. PowerShell ISE aşağıdaki yapılandırma komut dosyası (F5) başlatın (örneğin klasöründe bulunan **xPSDesiredStateConfiguration** modülü Sample_xDscWebService.ps1 olarak). Bu komut çekme sunucusunda ayarlar.
  
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

## <a name="registration-key"></a>Kayıt anahtarı
İstemci yapılandırması kimliği yerine yapılandırma adları kullanabilmeleri sunucusu ile kayıt düğümleri izin vermek için yukarıdaki yapılandırması tarafından oluşturulan bir kayıt anahtarı adlı bir dosyaya kaydedilir `RegistrationKeys.txt` içinde `C:\Program Files\WindowsPowerShell\DscService`. Kayıt anahtarını ilk kaydı sırasında çekme sunucu ile istemci tarafından kullanılan bir paylaşılan gizlilik olarak çalışır. İstemci kayıt başarıyla tamamlandıktan sonra çekme sunucusuna benzersiz olarak kimlik doğrulaması için kullanılan kendinden imzalı bir sertifika oluşturur. Bu sertifikanın parmak izini yerel olarak depolanır ve çekme sunucu URL'si ile ilişkili.
> **Not**: Kayıt anahtarlarını PowerShell 4. 0'desteklenmiyor. 

Çekme sunucunun kayıt kimliğini doğrulamak için bir düğüm yapılandırmak için anahtarı'nı bu çekme Server'a kaydettirirken herhangi bir hedef düğümün meta yapılandırmasını olması gerekir. Unutmayın **RegistrationKey** meta yapılandırmasını içinde aşağıdaki hedef makine başarılı bir şekilde kaydettirildi ve '140a952b-b9d6-406b-b416-e0f759c9c0e4' değeri depolanan değeriyle eşleşmelidir sonra kaldırılır. Çekme sunucusunda RegistrationKeys.txt dosyası. Her zaman farkında çekme sunucusu ile kayıt herhangi bir hedef makine verdiğinden kayıt anahtarı değeri güvenli kabul eder.

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
> **Not**: **ReportServerWeb** bölümü çekme sunucusuna gönderilecek verileri raporlama sağlar. 

Eksikliği **ConfigurationID** meta yapılandırmasını dosyasında özellik örtük olarak anlamına gelir, çekme sunucu bir ilk kaydı gerekli olacak şekilde çekme sunucusu protokolü V2 sürümünü destekliyor. Buna karşılık, varlığını bir **ConfigurationID** çekme sunucusu protokolü V1 sürümünü kullanılır ve da bir kayıt işleme anlamına gelir.

>**Not**: hiçbir zaman bir çekme sunucusuna kaydettirdiyseniz düğümleri için meta yapılandırmasını dosyasındaki bir ConfigurationID özellik tanımlamak için gerekli kılan geçerli relase içinde bir anında İLETME senaryosu, bir hata bulunmaktadır. V1 çekme sunucu protokolü zorlamak ve kayıt hata iletileri kaçının.

## <a name="placing-configurations-and-resources"></a>Yapılandırmaları ve kaynakları yerleştirme

Çekme sonra sunucu Kurulum tamamlandıktan, tarafından tanımlanan klasörleri **ConfigurationPath** ve **ModulePath** çekme sunucu yapılandırması özelliklerinde olan modülleri ve yapılandırmaları olduğu yerleştirir Hedef düğümleri çıkarmak kullanılabilir. Bu dosyalar çekme sunucusunun doğru şekilde işlemek sırayla belirli bir biçimde olması gerekir. 

### <a name="dsc-resource-module-package-format"></a>DSC kaynağı modülü paket biçimi

Her kaynak modül sıkıştırılmış ve aşağıdaki düzeni according adlı gerekiyor `{Module Name}_{Module Version}.zip`. Örneğin, 3.1.2.0 Modül sürümü xWebAdminstration adlı bir modül 'xWebAdministration_3.2.1.0.zip' adlı. Her bir modül sürümü tek zip dosyasında yer almalıdır. Yalnızca tek bir sürümünü modül biçimi WMF 5.0 ile eklenen her zip dosyasında bir kaynak olduğundan, tek bir dizin içinde birden çok modül sürümleri için destek desteklenmiyor. Bu, paketleme yukarı DSC kaynakları modüllerinin çekme server ile kullanmak için önce dizin yapısını küçük değişiklik gerektiğini anlamına gelir. WMF 5.0 DSC kaynağı içeren modüller varsayılan biçimi ' {modül klasörü}\{Modül sürümü} \DscResources\{DSC kaynak klasörünü}\'. Paketleme çekme sunucu için önce yalnızca kaldırmak **{Modül sürümü}** yolu olacak şekilde klasörü ' {modül klasörü} \DscResources\{DSC kaynak klasörünü}\'. Bu değişiklikle, yukarıda açıklandığı gibi klasör zip ve bu ZIP dosyaları yerleştirmek **ModulePath** klasör.

Kullanım `new-dscchecksum {module zip file}` yeni eklenen modülü için sağlama toplamı dosya oluşturulamadı.

### <a name="configuration-mof-format"></a>Yapılandırma MOF biçimi 
Bir yapılandırma MOF dosyası yapılandırmasını hedef düğümde bir LCM'yi doğrulayabilmesi bir sağlama toplamı dosyasıyla eşleştirilmiş gerekir. Bir sağlama toplamı oluşturmak için arama [yeni DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx) cmdlet'i. Cmdlet geçen bir **yolu** MOF yapılandırma bulunduğu klasörü belirten parametre. Cmdlet adlı bir sağlama toplamı dosyası oluşturur `ConfigurationMOFName.mof.checksum`, burada `ConfigurationMOFName` yapılandırma mof dosyasının adıdır. Belirtilen klasörde MOF dosyaları birden fazla yapılandırma varsa, her yapılandırma klasörü için bir sağlama toplamı oluşturulur. MOF dosyaları ve ilişkili sağlama toplamı dosyalarına yerleştirmek **ConfigurationPath** klasör.

>**Not**: herhangi bir şekilde yapılandırma MOF dosyasını değiştirirseniz, sağlama toplamı dosyasını da yeniden oluşturmanız gerekir.

## <a name="tooling"></a>Araçları
Ayar oluşturan için doğrulama ve daha kolay, çekme sunucusunu yönetme aşağıdaki araçları xPSDesiredStateConfiguration modülü en son sürümünü örneklerde olarak eklenir:
1. DSC kaynağı modülleri ve çekme sunucusunda kullanmak üzere yapılandırma dosyalarını paketleme ile yardımcı olacak bir modül. [PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1). Aşağıdaki örnekler:

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @("xWebAdministration", "xPhp") 
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList 

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. Çekme sunucunun doğrulayan bir komut dosyası doğru yapılandırılmamış. [PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).


## <a name="pull-client-configuration"></a>Çekme istemci yapılandırması 
Aşağıdaki konularda ayrıntılı çekme istemcileri ayarlama açıklanmaktadır:

* [Bir yapılandırma kimliği kullanan bir DSC çekme istemci ayarlama](pullClientConfigID.md)
* [Yapılandırma adları kullanarak bir DSC çekme istemcisi ayarlama](pullClientConfigNames.md)
* [Kısmi yapılandırmaları](partialConfigs.md)


## <a name="see-also"></a>Ayrıca bkz:
* [Windows PowerShell istenen durum yapılandırması genel bakış](overview.md)
* [Yapılandırmaları ederek ilerlemesini kabul ederek](enactingConfigurations.md)
* [DSC rapor sunucusu kullanma](reportServer.md)

