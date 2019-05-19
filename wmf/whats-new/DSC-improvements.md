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
# <a name="improvements-in-desired-state-configuration-dsc-in-wmf-51"></a>WMF 5.1 içinde Desired State Configuration (DSC) iyileştirmeleri

## <a name="dsc-class-resource-improvements"></a>DSC sınıf kaynak geliştirmeleri

WMF 5.1, aşağıdaki bilinen sorunlar düzelttik:

- Karmaşık/karma tablo türünde bir sınıf tabanlı DSC kaynağı Get() işlevi tarafından döndürülen, get-DscConfiguration boş değerler (null) ya da hataları döndürebilir.
- DSC yapılandırması RunAs kimlik bilgileri kullanılıyorsa, get-DscConfiguration hata döndürür.
- Kaynak sınıf tabanlı bileşik bir yapılandırmada kullanılamaz.
- Kaynak sınıf tabanlı kendi türünün bir özelliği varsa Başlat-DscConfiguration yanıt vermemeye başlıyor.
- Kaynak sınıf tabanlı özel bir kaynak kullanılamaz.

## <a name="dsc-resource-debugging-improvements"></a>DSC kaynak hata ayıklama iyileştirmeleri

WMF 5. 0'da, PowerShell hata ayıklayıcı kaynak sınıf tabanlı yöntemini (Get/Set/Test) doğrudan durdurulmadı. WMF 5.1 MOF temelli kaynak yöntemleri olduğu gibi sınıf tabanlı kaynak yöntem hata ayıklayıcıyı durdurur.

## <a name="dsc-pull-client-supports-tls-11-and-tls-12"></a>DSC çekme istemcisi, TLS 1.1 ve TLS 1.2 destekler.

Daha önce DSC çekme istemcisi yalnızca SSL3.0 ve TLS1.0 HTTPS bağlantılarında desteklenir. Daha güvenli protokollerini kullanacak şekilde zorlandığında, çekme istemcisi çalışmamaya. WMF 5.1 DSC çekme istemcisi artık SSL 3.0 destekler ve daha güvenli TLS 1.1 ve TLS 1.2 protokolleri için destek ekler.

## <a name="improved-pull-server-registration"></a>Geliştirilmiş çekme sunucusu kaydı

WMF önceki sürümlerinde eşzamanlı kayıtları/reporting istekleri ESENT veritabanını kullanırken bir DSC çekme sunucusuna kaydedin ve/veya raporu yüklerken LCM için yol açar. Bu gibi durumlarda, olay günlüklerini çekme sunucusunda sahip hata "Örnek adı zaten kullanımda." Bu, hatalı bir çok iş parçacıklı senaryosunda ESENT veritabanına erişmek için kullanılan desen tarafından neden oldu. WMF 5.1, bu sorun düzeltilmiştir. Eşzamanlı kaydı veya (ESENT veritabanını içeren) raporlama WMF 5.1 düzgün çalışır. Bu sorun yalnızca ESENT veritabanı için geçerlidir ve OLEDB veritabanı için geçerli değildir.

## <a name="enable-circular-log-on-esent-database-instance"></a>ESENT veritabanı örneğinde dairesel günlüğünü etkinleştir

DSC PullServer eariler sürümünde, döngüsel günlüğü olmadan veritabanı örneği oluşturulurken pullserver becouse, disk alanı ESENT veritabanı günlük dosyalarını doldurma. Bu sürümde, web.config dosyasının pullserver kullanarak örneğini döngüsel günlüğü davranışını denetlemek için seçeneğiniz vardır. Varsayılan olarak CircularLogging TRUE olarak ayarlanır.

```xml
<appSettings>
    <add key="dbprovider" value="ESENT" />
    <add key="dbconnectionstr" value="C:\Program Files\WindowsPowerShell\DscService\Devices.edb" />
    <add key="CheckpointDepthMaxKB" value="512" />
    <add key="UseCircularESENTLogs" value="TRUE" />
  </appSettings>
```

## <a name="wow64-support-for-configuration-keyword"></a>Yapılandırma anahtar sözcüğü için WOW64 desteği

`Configuration` Anahtar sözcüğü bir 64 bit bilgisayarda WOW64 artık desteklenmektedir. Bu, bir DSC yapılandırması tanımlanabilir ve 64 bit bilgisayarda çalışan bir 32-bit işlem içinde Windows PowerShell ISE gibi (x 86) derlenmiş, anlamına gelir.

## <a name="pull-partial-configuration-naming-convention"></a>Kısmi yapılandırma adlandırma kuralı çekme

Önceki bir sürümde çekme Sunucusu/hizmetinde MOF dosyası adı belirtilen sırayla eşleşmelidir yerel configuration manager ayarlarında kısmi yapılandırma adıyla eşleşmelidir kısmi bir yapılandırma için adlandırma kuralı oluştu. Yapılandırma adı MOF dosyası içinde gömülü.

Aşağıdaki anlık görüntüleri bakın:

- Bir düğüm alma izni olan bir kısmi yapılandırmasını tanımlayan yerel yapılandırma ayarları.

  ![Örnek metaconfiguration](../images/MetaConfigPartialOne.png)

- Örnek kısmi yapılandırma tanımı

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

- Oluşturulan MOF dosyasında ekli ConfigurationName'.

  ![Örnek oluşturulan mof dosyası](../images/PartialGeneratedMof.png)

- Çekme yapılandırma deposundaki dosya adı

  ![Yapılandırma deposundaki dosya adı](../images/PartialInConfigRepository.png)

  Azure Otomasyonu hizmeti adı MOF dosyaları olarak oluşturulan `<ConfigurationName>.<NodeName>.mof`. Bu nedenle aşağıdaki yapılandırmayı PartialOne.localhost.mof için derler.

  Bunu mümkün olmayan çekme kısmi yapılandırmanızın bir Azure Otomasyonu hizmetinden yapılan.

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

  WMF 5.1, kısmi bir çekme sunucusu/hizmet yapılandırmasında olarak adlandırılabilir `<ConfigurationName>.<NodeName>.mof`. Ayrıca, bir makine bir tek bir çekme yapılandırmasından çekiyor, sunucu/hizmet yapılandırma dosyasını ardından çekme sunucusu yapılandırma deposu üzerindeki herhangi bir dosya adı olabilir. Bu adlandırma esneklik düğümü için bazı yapılandırmalar Azure Automation DSC ve yerel olarak yönettiğiniz kısmi bir yapılandırma ile nereden geldiğini düğümlerinizi kısmen Azure Otomasyonu hizmeti tarafından yönetmenize olanak sağlar.

  Bir düğüm olacak şekilde ayarlar aşağıda metaconfiguration hem de yönetilen yerel olarak hem de Azure Otomasyonu tarafından hizmet.

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

## <a name="using-psdscrunascredential-with-dsc-composite-resources"></a>DSC bileşik kaynaklarla PsDscRunAsCredential kullanma

Kullanma desteği ekledik [PsDscRunAsCredential](/powershell/dsc/configurations/runAsUser) DSC ile [bileşik](https://msdn.microsoft.com/powershell/dsc/authoringresourcecomposite) kaynakları.

Artık için bir değer belirtebilirsiniz **PsDscRunAsCredential** yapılandırmaları içinde bileşik kaynakları kullanırken. Belirtildiğinde, tüm kaynaklar bir bileşik kaynak içinde bir RunAs kullanıcı olarak çalıştırın. Bileşik kaynak başka bir bileşik kaynak çağırırsa, tüm bu kaynakları da RunAs kullanıcı olarak yürütülür. RunAs kimlik Bilgileri'ni bileşik kaynak hiyerarşi düzeyine yayılır. Bileşik kaynak içinde herhangi bir kaynak için kendi değerine belirtirse **PsDscRunAsCredential**, yapılandırma derleme sırasında bir birleştirme hatası oluşur.

Bu örnek, kullanımını gösterir. [WindowsFeatureSet](/powershell/dsc/reference/resources/windows/windowsfeaturesetresource) da PSDesiredStateConfiguration modülüne dahil edilen bileşik kaynak.

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

## <a name="allowing-for-identical-duplicate-resources-in-a-configuration"></a>Bir yapılandırmada aynı kaynağa izin verme

DSC izin ver veya yapılandırması içindeki çakışan kaynak tanımlarını işlemek desteklemez. Çakışmayı çözmek çalışmak yerine, basitçe başarısız olur. Yapılandırma yeniden daha bileşik kaynaklarında kullanılan haline gelir gibi vb. çakışmaları daha sık meydana gelir. Çakışan kaynak tanımları aynı olduğunda, DSC Akıllı ve buna izin gerekir. Bu sürümle birlikte, aynı tanımlara sahip birden çok kaynak örneğini sahip destekliyoruz:

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

Önceki sürümlerde, sonuç WindowsFeature FE_IIS ve 'Web-Server' rolü emin olmak çalışırken WindowsFeature Worker_IIS örnekleri arasında bir çakışma nedeniyle başarısız bir derleme yüklü olacaktır. Dikkat *tüm* bu iki yapılandırmada yapılandırılmış olan özellikleri aynıdır. Bu yana *tüm* bu iki özellik kaynakların aynı olduğundan, bu artık başarılı bir derleme içinde neden olur.

Özelliklerinden herhangi birini iki kaynakları arasında farklıysa, bunlar aynı kabul edilmez ve derleme başarısız olur.

## <a name="dsc-module-and-configuration-signing-validations"></a>DSC modülünü ve doğrulamaları imzalama yapılandırma

DSC yapılandırmaları ve modülleri çekme sunucusundan yönetilen bilgisayarlara dağıtılır. Çekme sunucusu ele geçirilirse saldırgan büyük olasılıkla çekme sunucusunda modülleri ve yapılandırmaları değiştirebilir ve tüm yönetilen düğümlere dağıtılmış olması.

WMF 5.1 DSC destekler katalog ve yapılandırmasına dijital imzalarını doğrulama (. MOF) dosyası. Bu özellik, düğüm yapılandırmaları veya güvenilen bir imzalayan tarafından imzalanmamış veya güvenilen imzalayan tarafından imzalanmış sonra kurcalanmış Modülü dosyaları yürütülmesini engeller.

### <a name="how-to-sign-configuration-and-module"></a>Yapılandırma ve modül oturum açma

- Yapılandırma dosyaları (. MOF'lar): Mevcut PowerShell cmdlet'i [kümesi AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) MOF dosyaları imzalama destekleyecek şekilde genişletilmiştir.
- Modüller: Aşağıdaki adımları kullanarak karşılık gelen modülü Kataloğu açarak modüllerini imzalama gerçekleştirilir:
  1. Bir katalog dosyası oluşturun: Bir katalog dosyası şifreleme karmalarını ya da parmak izleri koleksiyonunu içerir. Her bir parmak izi modülüne dahil edilen bir dosyaya karşılık gelir. Yeni cmdlet [yeni FileCatalog](/powershell/module/microsoft.powershell.security/new-filecatalog), kendi modül için bir katalog dosyası oluşturmak için kullanıcıları etkinleştirmek üzere eklenmiştir.
  2. Katalog dosyasını imzalayın: Kullanım [kümesi AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) katalog dosyasını imzalamak için.
  3. Katalog dosyası modülü klasörün içine yerleştirin. Kural gereği, modül olarak aynı ada sahip modülü klasörü altında modülü katalog dosyası yerleştirilmelidir.

### <a name="localconfigurationmanager-settings-to-enable-signing-validations"></a>İmzalama doğrulamaları etkinleştirmek için LocalConfigurationManager ayarları

#### <a name="pull"></a>Çekme

Bir düğümün LocalConfigurationManager modülleri ve yapılandırmaları, geçerli ayarları temel alarak imza doğrulaması gerçekleştirir. Varsayılan olarak, imza doğrulaması devre dışı bırakıldı. İmza doğrulama düğümü gösterildiği meta-yapılandırma tanımını 'SignatureValidation' bloğu ekleyerek etkinleştirebilirsiniz:

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

Bir düğümde yukarıdaki metaconfiguration ayarlamak, indirilen yapılandırmaları ve modülleri İmza doğrulamasını sağlar. Yerel Configuration Manager dijital imzaları doğrulamak için aşağıdaki adımları gerçekleştirir.

1. Bir yapılandırma dosyası üzerinde imzasını (. MOF), geçerli kullanarak `Get-AuthenticodeSignature` cmdlet'i.
2. Yetkili imzalayan sertifika yetkilisi güvenildiğinden emin olun.
3. Modül/kaynak bağımlılıkları yapılandırmasının geçici bir konuma indirin.
4. İçinde modülüne dahil edilen Kataloğu imzasını doğrular.
   - Bulma bir `<moduleName>.cat` dosya ve imza kullanarak doğrulama `Get-AuthenticodeSignature`.
   - İmzalayan kimlik doğrulaması sertifika yetkilisi güvenildiğinden emin olun.
   - Modüller içeriğini değil kurcalanıp yeni cmdlet'ini kullanarak doğrulama `Test-FileCatalog`.
5. `Install-Module` Hedef `$env:ProgramFiles\WindowsPowerShell\Modules\`
6. İşlem Yapılandırması

> [!NOTE]
> Yapılandırmayı ilk kez veya modül indirilir ve yüklenir, sisteme uygulandığında imzası doğrulama modülü katalog ve yapılandırmasına yalnızca gerçekleştirilir.
> Tutarlılık çalıştırmaları Current.mof veya modül bağımlılıklarını imzasını doğrulamaz. Herhangi bir aşamasında doğrulama başarısız olursa, örneği için yapılandırmayı çekilen, çekme sunucusu imzalanmamış, ardından yapılandırmanın işleme aşağıda gösterilen hata ile sona erer ve tüm geçici dosyalar silinir.

![Örnek hata çıkış yapılandırması](../images/PullUnsignedConfigFail.png)

Benzer şekilde, katalog değil bir modül çekme şu hata sonuçlarında imzalı:

![Örnek hata çıkış modülü](../images/PullUnisgnedCatalog.png)

#### <a name="push"></a>anında iletme

Düğüme teslim önce yükleme kullanılarak teslim edilen yapılandırma, kaynakta değiştirilmiş. Yerel Configuration Manager için gönderildi veya yayımlanmış yapılandırmaları benzer imzası doğrulama adımları gerçekleştirir. Gönderim için imza doğrulaması için tam bir örnek aşağıdadır.

- İmza doğrulaması düğüm üzerinde etkinleştirin.

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

- Örnek bir yapılandırma dosyası oluşturun.

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

- İşaretsiz bir yapılandırma dosyası düğüme gönderme deneyin.

  ```powershell
  Start-DscConfiguration -Path .\Test -Wait -Verbose -Force
  ```

  ![ErrorUnsignedMofPushed](../images/PushUnsignedMof.png)

- Yapılandırma dosyası, kod imzalama sertifikası kullanarak oturum açın.

  ![SignMofFile](../images/SignMofFile.png)

- İmzalı MOF dosyası göndermek deneyin.

  ![SignMofFile](../images/PushSignedMof.png)
