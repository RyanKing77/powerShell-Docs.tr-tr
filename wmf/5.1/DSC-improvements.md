---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: WMF 5.1 DSC yenilikleri
ms.openlocfilehash: 76cfb1a1e8908fbb751562c1d5081c116368a8f6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
---
# <a name="improvements-in-desired-state-configuration-dsc-in-wmf-51"></a>İstenen durum yapılandırması (DSC) WMF 5.1'yenilikleri

## <a name="dsc-class-resource-improvements"></a>DSC sınıfı kaynak geliştirmeleri

WMF 5.1, biz aşağıdaki bilinen sorunlar düzeltildi:
* Karmaşık/karma tablo türü bir sınıf tabanlı DSC kaynağı Get() işlevi tarafından döndürülürse, get-DscConfiguration boş değerler (boş) veya hatalar döndürebilir.
* DSC yapılandırması RunAs kimlik bilgileri kullanılıyorsa, get-DscConfiguration hata döndürür.
* Kaynak sınıf tabanlı bileşik bir yapılandırmada kullanılamaz.
* Kaynak sınıf tabanlı kendi türünde bir özellik varsa Başlangıç DscConfiguration askıda kalır.
* Kaynak sınıf tabanlı özel bir kaynak kullanılamaz.


## <a name="dsc-resource-debugging-improvements"></a>DSC kaynağı geliştirmeleri hata ayıklama
WMF 5. 0'da, PowerShell hata ayıklayıcı kaynak sınıf tabanlı bir yöntem (Get/Set/Test) doğrudan durdurulmadı.
WMF 5.1, hata ayıklayıcı MOF tabanlı kaynaklara yöntemleri için olduğu gibi aynı şekilde at sınıf tabanlı kaynak yöntemi durdurur.

## <a name="dsc-pull-client-supports-tls-11-and-tls-12"></a>TLS 1.1 ve TLS 1.2 DSC çekme istemci destekler
Daha önce DSC çekme istemci yalnızca SSL3.0 ve TLS1.0 HTTPS bağlantıları üzerinden desteklenir.
Daha güvenli protokolleri kullanmak üzere zorlandığında, çekme istemci çalışmayı durdurmasına.
WMF 5.1 DSC çekme istemci artık SSL 3.0 destekler ve daha güvenli TLS 1.1 ve TLS 1.2 protokolleri için destek ekler.

## <a name="improved-pull-server-registration"></a>Geliştirilmiş çekme sunucu kaydı ##

WMF önceki sürümlerinde, eşzamanlı kayıtlar/raporlama istekleri ESENT veritabanı kullanılırken bir DSC çekme sunucusuna kaydetmek ve/veya rapor başarısız LCM'yi sunulmasını sağlar.
Böyle durumlarda, olay günlükleri çekme sunucusunda şunlardır hata "Örnek adı zaten kullanımda."
Çok iş parçacıklı senaryoda ESENT veritabanına erişmek için kullanılan hatalı desen nedeniyle, bu.
WMF 5.1, bu sorun düzeltilmiştir.
Eşzamanlı kayıtlar veya (ESENT veritabanını içeren) raporlama WMF 5.1 düzgün çalışır.
Bu sorun yalnızca ESENT veritabanı için geçerlidir ve OLEDB veritabanı için geçerli değil.

## <a name="enable-circular-log-on-esent-database-instance"></a>ESENT veritabanı örneğinde döngüsel günlüğü etkinleştir
DSC PullServer eariler sürümünde veritabanı örneği olmadan döngüsel günlüğü oluşturulurken pullserver becouse disk alan ESENT veritabanı günlük dosyalarını doldurma. Bu sürümde, web.config dosyasının pullserver kullanarak örneğini döngüsel günlüğü davranışını denetlemek için seçeneğiniz vardır. Varsayılan olarak CircularLogging TRUE olarak ayarlanır.
```
<appSettings>
    <add key="dbprovider" value="ESENT" />
    <add key="dbconnectionstr" value="C:\Program Files\WindowsPowerShell\DscService\Devices.edb" />
    <add key="CheckpointDepthMaxKB" value="512" />
    <add key="UseCircularESENTLogs" value="TRUE" />
  </appSettings>
```
## <a name="pull-partial-configuration-naming-convention"></a>Kısmi yapılandırma adlandırma kuralı isteme
MOF dosya adı çekme Sunucu/hizmetinde sırayla eşleşmelidir yerel configuration manager ayarlarında belirtilen kısmi yapılandırma adı eşleşmelidir önceki sürümde, kısmi bir yapılandırma için adlandırma kuralı edildi Yapılandırma adı MOF dosyasında katıştırılmış.

Aşağıdaki anlık görüntüleri bakın:

Bir düğüm alma izni olan bir kısmi yapılandırmasını tanımlayan • yerel yapılandırma ayarları.

![Örnek meta yapılandırmasını](../images/MetaConfigPartialOne.png)

• Örnek kısmi yapılandırma tanımı

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

• 'ConfigurationName' oluşturulan MOF dosyasında katıştırılmış.

![Örnek oluşturulan mof dosyası](../images/PartialGeneratedMof.png)

• Çekme yapılandırma deposundaki FileName

![Yapılandırma deposundaki FileName](../images/PartialInConfigRepository.png)

Azure Otomasyonu hizmet adı MOF dosyaları olarak oluşturulan `<ConfigurationName>.<NodeName>.mof`.
Bu nedenle yapılandırma PartialOne.localhost.mof için derler.

Bu olanaksız çekme kısmi yapılandırmanızın bir Azure Otomasyonu hizmetinden kılan.

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

WMF 5.1, kısmi bir çekme sunucu/hizmet yapılandırmasında olarak adlandırılabilir `<ConfigurationName>.<NodeName>.mof`.
Ayrıca, bir makine çekme tek yapılandırmasından çekiyor, sunucu/hizmet ardından çekme sunucusu yapılandırma deposu yapılandırma dosyası herhangi bir dosya adı olabilir.
Bu adlandırma esneklik düğümünüz için bazı yapılandırma Azure Automation DSC'de bulunan ve yerel olarak yönetme kısmi bir yapılandırmaya sahip olduğu gelen düğümleriniz Azure Otomasyon hizmeti tarafından kısmen yönetmenizi sağlar.

Bir düğüm olarak ayarlar aşağıda meta yapılandırmasını hem de yönetilen yerel olarak yanı sıra Azure Otomasyonu hizmet.

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

# <a name="using-psdscrunascredential-with-dsc-composite-resources"></a>DSC bileşik kaynaklarla PsDscRunAsCredential kullanma

Kullanma desteği ekledik [ *PsDscRunAsCredential* ](https://msdn.microsoft.com/cs-cz/powershell/dsc/runasuser) DSC ile [bileşik](https://msdn.microsoft.com/en-us/powershell/dsc/authoringresourcecomposite) kaynakları.

Yapılandırmaları içindeki bileşik kaynakların kullanırken, şimdi PsDscRunAsCredential için bir değer belirtebilirsiniz.
Belirtildiğinde, tüm kaynakları bileşik bir kaynak içinde bir RunAs kullanıcı olarak çalıştırın.
Bileşik bir kaynağı başka bir bileşik kaynak çağırırsa, kaynaklarının tümü de RunAs kullanıcı olarak çalıştırılır.
RunAs kimlik bilgileri bileşik kaynak hiyerarşi herhangi bir düzeyde yayılır.
Bileşik bir kaynak içinde herhangi bir kaynak için PsDscRunAsCredential kendi değerini belirtiyorsa, birleştirme hata yapılandırma derleme sırasında oluşur.

Bu örnek ile kullanımını gösterir [WindowsFeatureSet](https://msdn.microsoft.com/en-us/powershell/wmf/dsc_newresources) bileşik kaynağı da PSDesiredStateConfiguration modülünde yer alan.



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

##<a name="dsc-module-and-configuration-signing-validations"></a>DSC modülü ve doğrulamaları imzalama yapılandırma
DSC yapılandırmaları ve modülleri yönetilen bilgisayarlar için istek sunucusundan dağıtılır.
Çekme sunucunun aşılırsa, bir saldırganın olası çekme sunucusunda modülleri ve yapılandırmaları değiştirebilir ve tüm yönetilen düğümlere dağıtılan hepsinde tehlikeye olması.

 WMF 5.1, DSC destekleyen katalog ve yapılandırma dijital imzaları doğrulama (. MOF) dosyası.
Bu özellik, yapılandırmalar veya güvenilen bir imzalayan tarafından imzalanmamış veya güvenilen imzalayan tarafından imzalanmış sonra hangi oynanmış modül dosyaları yürütülmesini düğümleri engeller.



###<a name="how-to-sign-configuration-and-module"></a>Oturum yapılandırması ve modülü
***
* Yapılandırma dosyaları (. MOF dosyalarından): Varolan PowerShell cmdlet'ini [kümesi AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) MOF dosyaları imzalama destekleyecek şekilde genişletilmiştir.
* Modüller: modüller imzalama, aşağıdaki adımları kullanarak karşılık gelen modülü katalog imzalayarak gerçekleştirilir:
    1. Bir katalog dosyası oluşturun: bir katalog dosyası şifreleme karmalarını ya da parmak izleri koleksiyonunu içerir.
       Her parmak izi modülünde yer alan bir dosyaya karşılık gelir.
       Yeni cmdlet [yeni FileCatalog](https://technet.microsoft.com/library/cc732148.aspx), kullanıcıların kendi modül için bir katalog dosyası oluşturmak eklendi.
    2. Katalog dosyası oturum: kullanım [kümesi AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) katalog dosyasını imzalamak için.
    3. Katalog dosyası modülü klasöre yerleştirin.
Kurala göre modül katalog dosyası modülü aynı ada sahip modülü klasörü altında yerleştirilmelidir.

###<a name="localconfigurationmanager-settings-to-enable-signing-validations"></a>İmza doğrulama etkinleştirmek için LocalConfigurationManager ayarları

####<a name="pull"></a>Çekme
Bir düğümün LocalConfigurationManager modülleri ve yapılandırmaları geçerli ayarlarına bağlı imza doğrulaması gerçekleştirir.
Varsayılan olarak, imza doğrulaması devre dışı bırakıldı.
İmza doğrulaması etkin düğüm gösterildiği gibi meta yapılandırma tanımını 'SignatureValidation' blok ekleyerek:

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
        # By default, LCM uses the default Windows trusted publisher store to validate the certificate chain. If TrustedStorePath property is specified, LCM uses this custom store for retrieving the trusted publishers to validate the content.
        TrustedStorePath = 'Cert:\LocalMachine\DSCStore'
        SignedItemType = 'Configuration','Module'         # This is a list of DSC artifacts, for which LCM need to verify their digital signature before executing them on the node.
    }

}
EnableSignatureValidation
Set-DscLocalConfigurationManager -Path .\EnableSignatureValidation -Verbose
 ```

Bir düğümde yukarıdaki meta yapılandırmasını ayarlama indirilen yapılandırmaları ve modülleri İmza doğrulamasını sağlar.
Yerel Configuration Manager dijital imzaları doğrulamak için aşağıdaki adımları gerçekleştirir.

1. Bir yapılandırma dosyası imzayı doğrulamak (. MOF) geçerli değil.
   PowerShell cmdlet kullanır [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx), 5.1 MOF imza doğrulaması desteklemek için genişletilmiş.
2. İmzalayan yetkili sertifika yetkilisi güvenilir olduğunu doğrulayın.
3. Modül/kaynak bağımlılıkları yapılandırmasının geçici bir konuma indirin.
4. Modülün dahil katalog imzasını doğrular.
    * Bulma bir `<moduleName>.cat` dosyası ve cmdlet kullanılarak imzası doğrulayın [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx).
    * İmzalayan kimlik doğrulaması sertifika yetkilisi güvenilir olduğunu doğrulayın.
    * Modülleri içeriğini yok değiştirilmediğini yeni cmdlet'ini kullanarak doğrulama [Test FileCatalog](https://technet.microsoft.com/library/cc732148.aspx).
5. Install-modülüne $env: ProgramFiles\WindowsPowerShell\Modules\
6. İşlem Yapılandırması

> Not: yapılandırma sisteme ilk kez veya modül karşıdan yüklenip uygulandığında imza doğrulama modülü katalog ve yapılandırma yalnızca gerçekleştirilir.
Tutarlılık çalışır Current.mof veya modülü bağımlılıklarını imzasını doğrulamaz.
Herhangi bir aşamada doğrulama başarısız olursa, örneği için yapılandırma öğesinden çekilen varsa çekme sunucunun imzalanmamış, ardından yapılandırmanın işlenmesi aşağıda gösterilen hata ile sona erer ve tüm geçici dosyalar silinir.

![Örnek hata çıkış yapılandırması](../images/PullUnsignedConfigFail.png)

Benzer şekilde, katalog olmayan bir modül çekme aşağıdaki hata sonuçlarında imzalı:

![Örnek hata çıkış modülü](../images/PullUnisgnedCatalog.png)

####<a name="push"></a>Anında iletme
Düğüme teslim önce teslim gönderme yöntemini kullanarak bir yapılandırma kendi kaynakta değiştirilmiş.
Yerel Configuration Manager basılmış veya yayımlanmış yapılandırmalar için benzer imza doğrulama adımları gerçekleştirir.
İmza doğrulaması anında iletme için tam örnek aşağıdadır.

* İmza doğrulaması düğüm üzerinde etkinleştirin.

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
* Örnek bir yapılandırma dosyası oluşturun.

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

* İmzasız yapılandırma dosyası düğüme Ftp'den deneyin.

```powershell
Start-DscConfiguration -Path .\Test -Wait -Verbose -Force
```
![ErrorUnsignedMofPushed](../images/PushUnsignedMof.png)

* Kod imzalama sertifikası kullanarak yapılandırma dosyasını imzalayın.

![SignMofFile](../images/SignMofFile.png)

* İmzalı MOF dosyası Ftp'den deneyin.

![SignMofFile](../images/PushSignedMof.png)
