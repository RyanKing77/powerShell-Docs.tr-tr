---
ms.date: 04/11/2018
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC SMB çekme sunucusu ayarlama
ms.openlocfilehash: 9d087a08861b2f4683e81efd1e25f857b8b75e07
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057765"
---
# <a name="setting-up-a-dsc-smb-pull-server"></a>DSC SMB çekme sunucusu ayarlama

Şunun için geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0

> [!IMPORTANT]
> Çekme sunucusu (Windows özelliği *DSC hizmet*) ancak desteklenen bir bileşen Windows Server'ın yeni özellikler veya yetenekler sunmak için herhangi bir plan vardır. Geçişi başlıyor önerilir yönetilen istemcilere [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (Windows Server çekme sunucusunda dışında özellikler dahildir) veya topluluk çözümlerden birini listelenen [burada](pullserver.md#community-solutions-for-pull-service).

Bir DSC [SMB](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831795(v=ws.11)) çekme sunucusu, bu düğümler için isteyin, DSC yapılandırma dosyalarını ve DSC kaynakları hedef düğümler için kullanılabilir hale getiren bir SMB dosya paylaşımları barındıran bir bilgisayardır.

İçin DSC SMB çekme sunucusu kullanmak için için gerekenler:

- PowerShell 4.0 veya üzerini çalıştıran bir sunucuda bir SMB dosya paylaşımı ayarlama
- Bu SMB paylaşımından çekmek için PowerShell 4.0 veya sonraki sürümlerini çalıştıran istemci yapılandırma

## <a name="using-the-xsmbshare-resource-to-create-an-smb-file-share"></a>Bir SMB dosya paylaşımı oluşturmak için xSmbShare kaynak'ı kullanma

Bir SMB dosya paylaşımı ayarlama, ancak bakalım nasıl DSC kullanarak bunu yapabilirsiniz çeşitli yollarla vardır.

### <a name="install-the-xsmbshare-resource"></a>XSmbShare kaynak yükleyin

Çağrı [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet'ine **xSmbShare** modülü.

> [!NOTE]
> `Install-Module` yer aldığı **PowerShellGet** modülü, PowerShell 5. 0'da dahildir. İndirebileceğiniz **PowerShellGet** modülü PowerShell 3.0 ve 4.0, [PackageManagement PowerShell modülleri Önizleme](https://www.microsoft.com/en-us/download/details.aspx?id=49186).
> **XSmbShare** DSC kaynağı içeren **xSmbShare**, SMB dosya paylaşımı oluşturmak için kullanılabilir.

### <a name="create-the-directory-and-file-share"></a>Dizin ve dosya paylaşımı oluşturma

Aşağıdaki yapılandırmayı kullanır **dosya** paylaşımı için bir dizin oluşturmak için kaynak ve **xSmbShare** SMB Paylaşımı'kurmak için kaynak:

```powershell
Configuration SmbShare
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Import-DscResource -ModuleName xSmbShare

    Node localhost
    {

        File CreateFolder
        {
            DestinationPath = 'C:\DscSmbShare'
            Type = 'Directory'
            Ensure = 'Present'
        }

        xSMBShare CreateShare
        {
            Name = 'DscSmbShare'
            Path = 'C:\DscSmbShare'
            FullAccess = 'administrator'
            ReadAccess = 'myDomain\Contoso-Server$'
            FolderEnumerationMode = 'AccessBased'
            Ensure = 'Present'
            DependsOn = '[File]CreateFolder'
        }
    }
}
```

Yapılandırma dizini `C:\DscSmbShare`, zaten mevcut değil ve daha sonra bu dizine bir SMB dosya paylaşımı kullanır. **FullAccess** yazmak veya dosya paylaşımından silmek için gereken herhangi bir hesaba verilmelidir. **Okuma erişimi** yapılandırmaları ve/veya DSC kaynakları paylaşımından hale herhangi bir istemci düğümlere verilmelidir.

> [!NOTE]
> DSC, sistem hesabı olarak varsayılan olarak çalışır, böylece bilgisayar paylaşımına erişimi olması gerekir.

### <a name="give-file-system-access-to-the-pull-client"></a>Çekme istemcisi için dosya sistemi erişimi verin

Verme **okuma erişimi** istemciye düğümü, SMB paylaşımı erişecek ancak dosyaları veya klasörleri içindeki paylaşmak için bu düğümü sağlar. Açıkça istemci SMB paylaşımı klasörü ve alt düğümleri erişim izni gerekir. Bu DSC ile kullanarak ekleyerek yapabiliriz **cNtfsPermissionEntry** bulunan kaynak [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0) modülü. Aşağıdaki yapılandırmayı ekler bir **cNtfsPermissionEntry** çekme istemciye ReadAndExecute erişim veren engelle:

```powershell
Configuration DSCSMB
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Import-DscResource -ModuleName xSmbShare
    Import-DscResource -ModuleName cNtfsAccessControl

    Node localhost
    {

        File CreateFolder
        {
            DestinationPath = 'C:\DscSmbShare'
            Type = 'Directory'
            Ensure = 'Present'
        }

        xSMBShare CreateShare
        {
            Name = 'DscSmbShare'
            Path = 'C:\DscSmbShare'
            FullAccess = 'administrator'
            ReadAccess = 'myDomain\Contoso-Server$'
            FolderEnumerationMode = 'AccessBased'
            Ensure = 'Present'
            DependsOn = '[File]CreateFolder'
        }

        cNtfsPermissionEntry PermissionSet1
        {
            Ensure = 'Present'
            Path = 'C:\DscSmbShare'
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

Tüm yapılandırma MOF dosyasının adlandırılmalıdır *ConfigurationID*.mof, burada *ConfigurationID* değeri **ConfigurationID** hedef düğümün LCM özelliği. Çekme istemciler ayarlama hakkında daha fazla bilgi için bkz. [yapılandırma Kimliğini kullanarak çekme istemcisi ayarlama](pullClientConfigID.md).

> [!NOTE]
> Bir SMB çekme sunucusu kullanıyorsanız, yapılandırma kimliklerinin kullanmanız gerekir. Yapılandırma adları, SMB için desteklenmez.

Her kaynak modülü sıkıştırılmasını ve aşağıdaki modele göre adında gereken `{Module Name}_{Module Version}.zip`. Örneğin, xWebAdminstration 3.1.2.0 modülü sürümü ile adlı bir modül 'xWebAdministration_3.2.1.0.zip' adlı. Her bir modül sürümü tek zip dosyasında yer almalıdır. Modül zip dosyası içinde ayrı sürümleri desteklenmez. DSC çekme server ile kullanmak için kaynak modülleri'kurmak paketleme önce dizin yapısı için küçük bir değişiklik yapmanız gerekir.

WMF 5.0 DSC kaynağı içeren modüllerin varsayılan biçimi `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.

Çekme sunucusu için paketleme önce kaldırmanız `{Module version}` klasör yolu olacak şekilde `{Module Folder}\DscResources\{DSC Resource Folder}\`. Bu değişiklik, yukarıda açıklandığı gibi klasör zip ve bu zip dosyaları SMB paylaşımı klasörüne yerleştirin.

## <a name="creating-the-mof-checksum"></a>MOF sağlama toplamı oluşturma

Yapılandırma MOF dosyasının yapılandırmasını hedef düğümde bir LCM doğrulayabilmesi bir sağlama toplamı dosyasına ile eşleştirilmesi gerekir.
Bir sağlama toplamı oluşturmak için arama [yeni DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet'i. Cmdlet alır bir `Path` parametresi yapılandırma MOF bulunduğu klasörü belirtir. Adlı bir sağlama toplamı dosyasına cmdlet oluşturur `ConfigurationMOFName.mof.checksum`burada `ConfigurationMOFName` yapılandırma mof dosyasının adıdır.
Belirtilen klasörde MOF dosyaları birden fazla yapılandırması varsa, klasördeki her bir yapılandırma için bir sağlama toplamı oluşturulur.

Sağlama toplamı dosyasına yapılandırma MOF dosyasının aynı dizinde bulunmalıdır (`$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration` varsayılan olarak), ve aynı ada sahip `.checksum` uzantısı eklenmiş.

> [!NOTE]
> Yapılandırma MOF dosyasının herhangi bir şekilde değiştirirseniz, sağlama toplamı dosyasına yeniden oluşturmanız gerekir.

## <a name="setting-up-a-pull-client-for-smb"></a>SMB için çekme istemcisi ayarlama

Bir istemci yapılandırmaları ve/veya bir SMB paylaşımından kaynaklar çeker ayarlamak için ile istemcinin yerel Configuration Manager (LCM) yapılandırma **ConfigurationRepositoryShare** ve **ResourceRepositoryShare** blokları yapılandırmaları ve DSC kaynakları çekmek paylaşımını belirtin.

LCM yapılandırma hakkında daha fazla bilgi için bkz. [yapılandırma Kimliğini kullanarak çekme istemcisi ayarlama](pullClientConfigID.md).

> [!NOTE]
> Kolaylık olması için bu örnekte **PSDscAllowPlainTextPassword** bir düz metin parolayı geçirme izin vermek için **kimlik bilgisi** parametresi. Kimlik bilgileri daha güvenli bir şekilde geçirme hakkında daha fazla bilgi için bkz: [yapılandırma verilerinde kimlik bilgisi seçeneklerinden](../configurations/configDataCredentials.md).
>
> **Gerekir** belirtin bir **ConfigurationID** içinde **ayarları** kaynakları yalnızca çeken olsa bile bir SMB çekme sunucusu, bir metaconfiguration bloğu.

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

Özel sayesinde aşağıdaki kişiler:

- Bu konudaki içeriğin bildirmek için DSC SMB kullanarak, gönderiler Yardım Mike F. Robbins. Blog altındadır [Mike F Robbins](http://mikefrobbins.com/).
- Kimin yazılan serge Nikalaichyk **cNtfsAccessControl** modülü. Bu modülü için kaynak altındadır [cNtfsAccessControl](https://github.com/SNikalaichyk/cNtfsAccessControl).

## <a name="see-also"></a>Ayrıca bkz.

[Windows PowerShell Desired State Configuration ' ne genel bakış](../overview/overview.md)

[Yapılandırmaları Kabul Etme](enactingConfigurations.md)

[Yapılandırma kimliğini kullanarak çekme istemcisi ayarlama](pullClientConfigID.md)
