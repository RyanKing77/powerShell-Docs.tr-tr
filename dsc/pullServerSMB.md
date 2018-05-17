---
ms.date: 04/11/2018
keywords: DSC, powershell, yapılandırma, Kur
title: DSC SMB çekme sunucusu ayarlama
ms.openlocfilehash: 92c03c99afd612fa2b5475e8c26991ff080584e9
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
---
# <a name="setting-up-a-dsc-smb-pull-server"></a>DSC SMB çekme sunucusu ayarlama

>İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0

> [!IMPORTANT]
> Çekme sunucusuna (Windows özelliği *DSC hizmet*) vardır ancak desteklenen bir bileşen Windows Server'ın yeni özellikleri veya yetenekleri sunmak için herhangi bir plan vardır. Geçiş başlamak için önerilen yönetilen istemcilere [Azure Otomasyonu DSC](/azure/automation/automation-dsc-getting-started) (Windows Server çekme sunucusunda ötesinde özellikler içerir) veya topluluk çözümlerden birini listelenen [burada](pullserver.md#community-solutions-for-pull-service).

Bir DSC [SMB](https://technet.microsoft.com/library/hh831795.aspx) çekme sunucu, bu düğümler için söylediğinizde DSC yapılandırma dosyalarını ve DSC kaynakları, hedef düğümleri kullanılabilmesini SMB dosya paylaşımlarını barındıran bir bilgisayardır.

DSC için bir SMB çekme sunucusunu kullanmak üzere için gerekenler:
- PowerShell 4.0 veya üstünü çalıştıran bir sunucuda bir SMB dosya paylaşımı ayarlama
- Bu SMB paylaşımından çıkarmak için PowerShell 4.0 veya sonraki sürümlerini çalıştıran istemci yapılandırma

## <a name="using-the-xsmbshare-resource-to-create-an-smb-file-share"></a>XSmbShare kaynağı kullanarak bir SMB dosya paylaşımı oluşturmak için

Bir SMB dosya paylaşımı ayarlama, ancak nasıl DSC kullanarak bunu yapabilirsiniz bakalım yolları vardır.

### <a name="install-the-xsmbshare-resource"></a>XSmbShare kaynak yükleyin

Çağrı [yükleme-Module](https://technet.microsoft.com/library/dn807162.aspx) yüklemek için cmdlet'i **xSmbShare** modülü.
>**Not**: **yükleme-Module** dahil **PowerShellGet** PowerShell 5. 0 ' dahil modülü. İndirebilirsiniz **PowerShellGet** için modülü PowerShell 3.0 ve 4.0 en [PackageManagement PowerShell modülleri Önizleme](https://www.microsoft.com/en-us/download/details.aspx?id=49186). **XSmbShare** DSC kaynağı içeren **xSmbShare**, bir SMB dosya paylaşımı oluşturmak için kullanılabilir.

### <a name="create-the-directory-and-file-share"></a>Dizin ve dosya paylaşımı oluşturma

Aşağıdaki yapılandırmayı kullanan [dosya](fileResource.md) paylaşımı dizinini oluşturmak için kaynak ve **xSmbShare** SMB Paylaşımı kurmak için kaynak:

```powershell
Configuration SmbShare {

Import-DscResource -ModuleName PSDesiredStateConfiguration
Import-DscResource -ModuleName xSmbShare

    Node localhost {

        File CreateFolder {

            DestinationPath = 'C:\DscSmbShare'
            Type = 'Directory'
            Ensure = 'Present'

        }

        xSMBShare CreateShare {

            Name = 'DscSmbShare'
            Path = 'C:\DscSmbShare'
            FullAccess = 'admininstrator'
            ReadAccess = 'myDomain\Contoso-Server$'
            FolderEnumerationMode = 'AccessBased'
            Ensure = 'Present'
            DependsOn = '[File]CreateFolder'

        }

    }

}
```

Yapılandırma dizini `C:\DscSmbShare` zaten seçili değilse var ve daha sonra bu dizine bir SMB dosya paylaşımı kullanır. **FullAccess** yazmak veya dosya paylaşımından silmek için gereken herhangi bir hesabı verilecek ve **okuma erişimi** yapılandırmaları ve/veya DSC kaynakları (Bunun nedeni paylaşımından alma tüm istemci düğümlere verilmelidir Bilgisayar paylaşımına erişim iznine sahip olması gerekir DSC sistem hesabı olarak varsayılan olarak çalışır, böylece).


### <a name="give-file-system-access-to-the-pull-client"></a>Çekme istemciye dosya sistemi erişimi verin

Vermiş **okuma erişimi** istemciye düğümü, SMB paylaşımı erişim, ancak dosyalar veya klasörler, içinde paylaşmak için o düğüm sağlar. Açıkça istemci SMB paylaşımı klasörü ve alt klasörler için düğümleri erişim vermeniz gerekir. Bu DSC ile kullanarak ekleyerek yapabiliriz **cNtfsPermissionEntry** bulunan kaynak [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0) modülü. Aşağıdaki yapılandırma ekler bir **cNtfsPermissionEntry** çekme istemciye ReadAndExecute erişim verir engelle:

```powershell
Configuration DSCSMB {

Import-DscResource -ModuleName PSDesiredStateConfiguration
Import-DscResource -ModuleName xSmbShare
Import-DscResource -ModuleName cNtfsAccessControl

    Node localhost {

        File CreateFolder {

            DestinationPath = 'DscSmbShare'
            Type = 'Directory'
            Ensure = 'Present'

        }

        xSMBShare CreateShare {

            Name = 'DscSmbShare'
            Path = 'DscSmbShare'
            FullAccess = 'administrator'
            ReadAccess = 'myDomain\Contoso-Server$'
            FolderEnumerationMode = 'AccessBased'
            Ensure = 'Present'
            DependsOn = '[File]CreateFolder'

        }

        cNtfsPermissionEntry PermissionSet1 {

        Ensure = 'Present'
        Path = 'C:\DSCSMB'
        Principal = 'myDomain\Contoso-Server$'
        AccessControlInformation = @(
            cNtfsAccessControlInformation
            {
                AccessControlType = 'Allow'
                FileSystemRights = 'ReadAndExecute'
                Inheritance = 'ThisFolderSubfoldersAndFiles'
                NoPropagateInherit = $false
            }
        )
        DependsOn = '[File]CreateFolder'

        }


    }

}
```

## <a name="placing-configurations-and-resources"></a>Yapılandırmaları ve kaynakları yerleştirme

Herhangi bir yapılandırma MOF dosyaları ve/veya istemci düğümleri SMB paylaşımı klasöründe çekmek için istediğiniz DSC kaynakları kaydedin.

Tüm yapılandırma MOF dosyası olarak adlandırılmalıdır _ConfigurationID_.mof, burada _ConfigurationID_ değeri **ConfigurationID** hedef düğümün LCM'yi özelliği. Çekme istemcileri ayarlama hakkında daha fazla bilgi için bkz: [yapılandırma Kimliğini kullanarak bir çekme istemcisi kurarken](pullClientConfigID.md).

>**Not:** bir SMB çekme sunucusu kullanıyorsanız, yapılandırma kimlikleri kullanmanız gerekir. Yapılandırma adları için SMB desteklenmez.

Her kaynak modül sıkıştırılmış ve according adlı gerekiyor şu deseni `{Module Name}_{Module Version}.zip`. Örneğin, 3.1.2.0 Modül sürümü xWebAdminstration adlı bir modül 'xWebAdministration_3.2.1.0.zip' adlı. Her bir modül sürümü tek zip dosyasında yer almalıdır. Yalnızca tek bir sürümünü modül biçimi WMF 5.0 ile eklenen her zip dosyasında bir kaynak olduğundan, tek bir dizin içinde birden çok modül sürümleri için destek desteklenmiyor. Bu paketleme yukarı DSC kaynakları modüllerinin çekme server ile kullanmak için önce dizin yapısını küçük değişiklikler yapmak gerektiği anlamına gelir. WMF 5.0 DSC kaynağı içeren modüller varsayılan biçimi ' {modül klasörü}\{Modül sürümü} \DscResources\{DSC kaynak klasörünü}\'. Paketleme çekme sunucu için önce yalnızca kaldırmak **{Modül sürümü}** yolu olacak şekilde klasörü ' {modül klasörü} \DscResources\{DSC kaynak klasörünü}\'. Bu değişiklik, yukarıda açıklandığı gibi klasör zip ve bu ZIP dosyaları SMB paylaşımı klasörüne yerleştirin.

## <a name="creating-the-mof-checksum"></a>MOF sağlama toplamı oluşturma
Bir yapılandırma MOF dosyası yapılandırmasını hedef düğümde bir LCM'yi doğrulayabilmesi bir sağlama toplamı dosyasıyla eşleştirilmiş gerekir.
Bir sağlama toplamı oluşturmak için arama [yeni DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx) cmdlet'i. Cmdlet geçen bir **yolu** MOF yapılandırma bulunduğu klasörü belirten parametre. Cmdlet adlı bir sağlama toplamı dosyası oluşturur `ConfigurationMOFName.mof.checksum`, burada `ConfigurationMOFName` yapılandırma mof dosyasının adıdır.
Belirtilen klasörde MOF dosyaları birden fazla yapılandırma varsa, her yapılandırma klasörü için bir sağlama toplamı oluşturulur.

Sağlama toplamı dosya yapılandırma MOF dosyası ile aynı dizinde mevcut olması gerekir (`$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration` varsayılan olarak), ve aynı ada sahip olan `.checksum` uzantısı eklenmiş.

>**Not**: herhangi bir şekilde yapılandırma MOF dosyasını değiştirirseniz, sağlama toplamı dosyasını da yeniden oluşturmanız gerekir.

## <a name="setting-up-a-pull-client-for-smb"></a>Bir çekme istemci SMB için ayarlama

İle istemcinin yerel Configuration Manager (LCM'yi) yapılandırdığınız yapılandırmaları ve/veya bir SMB paylaşımına kaynaklardan çeken bir istemci ayarlamak için **ConfigurationRepositoryShare** ve **ResourceRepositoryShare** , yapılandırmaları ve DSC kaynakları çekmesini paylaşımından belirtin engeller.

LCM'yi yapılandırma hakkında daha fazla bilgi için bkz: [yapılandırma Kimliğini kullanarak bir çekme istemcisi kurarken](pullClientConfigID.md).

>**Not:** kolaylık sağlamak için bu örnekte **PSDscAllowPlainTextPassword** bir düz metin parola geçirerek izin vermek için **kimlik bilgisi** parametresi. Kimlik bilgileri daha güvenli bir şekilde geçirme hakkında daha fazla bilgi için bkz: [kimlik bilgileri seçenekleri yapılandırma verilerinde](configDataCredentials.md).

>**Not:** belirtmeniz gerekir bir **ConfigurationID** içinde **ayarları** bir kaynaklar yalnızca çekme olsa bile SMB çekme sunucusu için bir meta yapılandırmasını bloğu.

```powershell
$secpasswd = ConvertTo-SecureString “Pass1Word” -AsPlainText -Force
$mycreds = New-Object System.Management.Automation.PSCredential (“TestUser”, $secpasswd)

[DSCLocalConfigurationManager()]
configuration SmbCredTest
{
    Node $AllNodes.NodeName
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
            ConfigurationID    = '16db7357-9083-4806-a80c-ebbaf4acd6c1'
        }

         ConfigurationRepositoryShare SmbConfigShare
        {
            SourcePath = '\\WIN-E0TRU6U11B1\DscSmbShare'
            Credential = $mycreds
        }

        ResourceRepositoryShare SmbResourceShare
        {
            SourcePath = '\\WIN-E0TRU6U11B1\DscSmbShare'
            Credential = $mycreds

        }
    }
}

$ConfigurationData = @{

    AllNodes = @(

        @{

            #the "*" means "all nodes named in ConfigData" so we don't have to repeat ourselves

            NodeName="localhost"

            PSDscAllowPlainTextPassword = $true

        })



}
```

## <a name="acknowledgements"></a>Bildirimler

Özel aşağıdaki sayesinde:

- Bu konudaki içeriğin bildirmek için DSC SMB kullanma, postaları Yardım CAN F'ye Robbins. Kendi blogu [CAN F Robbins](http://mikefrobbins.com/).
- Kimin yazılan serge Nikalaichyk **cNtfsAccessControl** modülü. Bu modül için bir kaynak altındadır https://github.com/SNikalaichyk/cNtfsAccessControl.

## <a name="see-also"></a>Ayrıca bkz:
- [Windows PowerShell istenen durum yapılandırması genel bakış](overview.md)
- [Yapılandırmaları Kabul Etme](enactingConfigurations.md)
- [Yapılandırma kimliğini kullanarak çekme istemcisi ayarlama](pullClientConfigID.md)