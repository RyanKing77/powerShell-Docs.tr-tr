---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: Yapılandırma verilerinde kimlik bilgisi seçeneklerinden
ms.openlocfilehash: 2a326e45bbbad7bd2362b66b88bf61b98df7b02e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686379"
---
# <a name="credentials-options-in-configuration-data"></a>Yapılandırma verilerinde kimlik bilgisi seçeneklerinden

>Şunun için geçerlidir: Windows PowerShell 5.0

## <a name="plain-text-passwords-and-domain-users"></a>Düz metin şifreleri ve etki alanı kullanıcıları

DSC yapılandırmaları içeren bir kimlik bilgisi şifreleme olmadan düz metin parolalar ilgili bir hata iletisi oluşturur.
Ayrıca, DSC etki alanı kimlik bilgilerini kullanarak bir uyarı oluşturur.
Engellemek için bu hata ve uyarı iletilerini DSC yapılandırma verileri anahtar sözcükleri kullanın:

- **PsDscAllowPlainTextPassword**
- **PsDscAllowDomainUser**

> [!NOTE]
> Düz metin parolalar şifrelenmemiş depolayarak/iletme genellikle güvenli değildir. Bu konuda açıklanan teknikleri kullanarak kimlik bilgilerini güvenli hale getirme önerilir.
> Azure Otomasyonu DSC hizmet yapılandırmasında derlenmiş olmaya ve güvenli şekilde depolanan kimlik bilgileri merkezi olarak yönetmenizi sağlar.
> Bilgi için bkz: [DSC yapılandırmaları derleme / kimlik bilgisi varlıkları](/azure/automation/automation-dsc-compile#credential-assets)

## <a name="handling-credentials-in-dsc"></a>DSC kimlik bilgilerini işleme

DSC yapılandırma kaynaklarını Çalıştır `Local System` varsayılan olarak.
Ancak, bazı kaynaklar bir kimlik bilgisi, örneğin gerektiğinde `Package` kaynak belirli bir kullanıcı hesabı altında yazılımı yüklemeniz gerekir.

Önceki kaynakları kullanılan sabit olarak kodlanmış `Credential` bu durumu çözmek için özellik adı.
WMF 5.0 otomatik eklenen `PsDscRunAsCredential` tüm kaynaklar için özellik.
Kullanma hakkında bilgi için `PsDscRunAsCredential`, bkz: [DSC çalıştıran kullanıcı kimlik bilgileriyle](runAsUser.md).
Yeni kaynaklar ve özel kaynakların otomatik bu özelliği kendi kimlik bilgilerini özelliği oluşturmak yerine kullanabilirsiniz.

> [!NOTE]
> Bazı kaynaklar tasarımını olan belirli bir nedenle birden çok kimlik bilgilerini kullanmayı ve kendi kimlik bilgisi özelliklerine sahip.

Kullanılabilir kimlik bilgileri bulmak için bir kaynak özelliklerini kullanın `Get-DscResource -Name ResourceName -Syntax` veya işe IntelliSense (`CTRL+SPACE`).

```powershell
PS C:\> Get-DscResource -Name Group -Syntax
Group [String] #ResourceName
{
    GroupName = [string]
    [Credential = [PSCredential]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Members = [string[]]]
    [MembersToExclude = [string[]]]
    [MembersToInclude = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
}
```

Bu örnekte bir [grubu](../resources/resources.md) kaynaktan `PSDesiredStateConfiguration` yerleşik DSC kaynak modülü.
Bu yerel gruplarını oluşturun ve ekleyebilir veya üyeleri kaldırın.
Hem kabul ettiği `Credential` özelliği ve otomatik `PsDscRunAsCredential` özelliği.
Ancak, yalnızca kaynak kullanan `Credential` özelliği.

Hakkında daha fazla bilgi için `PsDscRunAsCredential` özelliğine bakın [DSC çalıştıran kullanıcı kimlik bilgileriyle](runAsUser.md).

## <a name="example-the-group-resource-credential-property"></a>Örnek: Grubu kaynağının Credential özelliği

DSC çalıştıran altında `Local System`, yerel kullanıcılar ve gruplar değiştirmek için izinlere zaten sahip.
Eklenen üye bir yerel hesapsa, hiçbir kimlik bilgisi gereklidir.
Varsa `Group` kaynak, yerel gruba bir etki alanı hesabı ekler ve ardından bir kimlik bilgisi gereklidir.

Active Directory anonim sorgulara izin verilmez.
`Credential` Özelliği `Group` kullanılan sorgu için Active Directory etki alanı hesabı bir kaynaktır.
Birçok amaç için bunun nedeni, varsayılan olarak, kullanıcıların yükleyebileceği bir genel kullanıcı hesabı olabilir *okuma* Active Directory içindeki nesneleri çoğu.

## <a name="example-configuration"></a>Örnek yapılandırma

Aşağıdaki kod örneği, bir yerel Grup bir etki alanı kullanıcısı ile doldurmak için DSC kullanır:

```powershell
Configuration DomainCredentialExample
{
    param
    (
        [PSCredential] $DomainCredential
    )
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    node localhost
    {
        Group DomainUserToLocalGroup
        {
            GroupName        = 'ApplicationAdmins'
            MembersToInclude = 'contoso\alice'
            Credential       = $DomainCredential
        }
    }
}

$cred = Get-Credential -UserName contoso\genericuser -Message "Password please"
DomainCredentialExample -DomainCredential $cred
```

Bu kod, bir hata ve uyarı iletisi oluşturur:

```
ConvertTo-MOFInstance : System.InvalidOperationException error processing property 'Credential' OF
TYPE 'Group': Converting and storing encrypted passwords as plain text is not recommended.
For more information on securing credentials in MOF file, please refer to MSDN blog:
https://go.microsoft.com/fwlink/?LinkId=393729

At line:11 char:9
+   Group
At line:341 char:16
+     $aliasId = ConvertTo-MOFInstance $keywordName $canonicalizedValue
+                ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Write-Error], InvalidOperationException
    + FullyQualifiedErrorId : FailToProcessProperty,ConvertTo-MOFInstance
WARNING: It is not recommended to use domain credential for node 'localhost'. In order to suppress
the warning, you can add a property named 'PSDscAllowDomainUser' with a value of $true to your DSC
configuration data for node 'localhost'.

Compilation errors occurred while processing configuration
'DomainCredentialExample'. Please review the errors reported in error stream and modify your
configuration code appropriately.
At C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:3917 char:5
+     throw $ErrorRecord
+     ~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (DomainCredentialExample:String) [], InvalidOperationException
    + FullyQualifiedErrorId : FailToProcessConfiguration
```

Bu örnekte, iki sorun vardır:

1. Bir hata düz metin parolalar önerilmez açıklar.
2. Bir uyarı bir etki alanı kimlik bilgisi kullanılmamasını önerir.

Bayrakları **PSDSCAllowPlainTextPassword** ve **PSDSCAllowDomainUser** hata ve söz konusu riski kullanıcısı bildiren bir uyarı bastırır.

## <a name="psdscallowplaintextpassword"></a>PSDSCAllowPlainTextPassword

İlk hata iletisi, belgeleri bir URL vardır.
Bu bağlantıyı kullanarak parolaları şifrelemek açıklanmaktadır bir [ConfigurationData](./configData.md) yapısı ve bir sertifika.
Sertifikaları ve DSC hakkında daha fazla bilgi için [Bu gönderiyi okuyun](http://aka.ms/certs4dsc).

Düz metin parola zorlamak için kaynak gerektiren `PsDscAllowPlainTextPassword` yapılandırma verilerini bir anahtar sözcük bölümünde şu şekilde:

```powershell
$password = "ThisIsAPlaintextPassword" | ConvertTo-SecureString -asPlainText -Force
$username = "contoso\Administrator"
[PSCredential] $credential = New-Object System.Management.Automation.PSCredential($username,$password)

Configuration DomainCredentialExample
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    node localhost
    {
        Group DomainUserToLocalGroup
        {
            GroupName        = 'ApplicationAdmins'
            MembersToInclude = 'contoso\alice'
            Credential       = $credential
        }
    }
}

$cd = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            PSDscAllowPlainTextPassword = $true
        }
    )
}

DomainCredentialExample -ConfigurationData $cd
```

### <a name="localhostmof"></a>localhost.mof

**PSDSCAllowPlainTextPassword** bayrağı gerektiren kullanıcı MOF dosyasında düz metin parolaların saklanması riskini kabul etme. Oluşturulan MOF dosyasındaki olsa bile bir **PSCredential** nesne içeren bir **SecureString** kullanılan, parolaları düz metin olarak görünmeye devam eder. Kimlik bilgilerinin ifşa edildiği yalnızca bir kez budur. Herkes yönetici hesabına bu MOF dosyası erişmenizi erişmesini.

```
/*
@TargetNode='localhost'
@GeneratedBy=Administrator
@GenerationDate=01/31/2019 06:43:13
@GenerationHost=Server01
*/

instance of MSFT_Credential as $MSFT_Credential1ref
{
Password = "ThisIsAPlaintextPassword";
 UserName = "Administrator";

};

instance of MSFT_GroupResource as $MSFT_GroupResource1ref
{
ResourceID = "[Group]DomainUserToLocalGroup";
 MembersToInclude = {
    "contoso\\alice"
};
 Credential = $MSFT_Credential1ref;
 SourceInfo = "::11::9::Group";
 GroupName = "ApplicationAdmins";
 ModuleName = "PSDesiredStateConfiguration";

ModuleVersion = "1.0";

 ConfigurationName = "DomainCredentialExample";

};
```

### <a name="credentials-in-transit-and-at-rest"></a>Aktarımda ve bekleme sırasında kimlik bilgileri

- **PSDscAllowPlainTextPassword** bayrağı, düz metin parolalar içeren MOF dosyaları derlenmesini sağlar.
  Düz metin parolalar içeren MOF dosyaları depolarken önlemleri alın.
- Ne zaman MOF dosyasını girmediklerinden bir düğüme **anında iletme** modu, WinRM şifreler varsayılan yazmadığınız sürece düz metin parolası korumak için iletişim **AllowUnencrypted** parametresi.
  - Bir sertifika ile MOF şifreleme, bir düğüme uygulanan önce bekleyen MOF dosyasını korur.
- İçinde **çekme** modu, Internet Information Server'ın belirtilen protokolünü kullanarak trafiği şifrelemek için HTTPS kullanmak üzere Windows çekme sunucusu yapılandırabilirsiniz. Daha fazla bilgi için makalelere bakın [DSC çekme istemcisi ayarlama](../pull-server/pullclient.md) ve [sertifikalar ile güvenli hale getirme MOF dosyaları](../pull-server/secureMOF.md).
  - İçinde [Azure Otomasyon durum Yapılandırması](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview) hizmeti, çekme trafik her zaman şifrelenir.
- Düğümde, MOF dosyaları bekleme sırasında şifrelenir PowerShell 5. 0'den itibaren.
  - Gönderilen veya düğüme çekilen bir sertifika ile şifrelenir sürece içinde PowerShell 4.0 MOF dosyaları bekleme sırasında şifrelenmemiş olarak.

**Önemli güvenlik riski nedeniyle düz metin parolalar önlemek için Microsoft önerir.**

## <a name="domain-credentials"></a>Etki alanı kimlik bilgileri

(İle veya şifreleme olmadan), yeniden örnekte yapılandırma betiği çalıştıran bir etki alanı kullanarak bir kimlik bilgisi hesabı önerilmez uyarı hala oluşturur.
Yerel bir hesap kullanarak, diğer tüm sunucularda kullanılabilir etki alanı kimlik bilgilerini olası riskini ortadan kaldırır.

**DSC kaynakları ile kimlik bilgilerini kullanarak, yerel bir hesap bir etki alanı hesabı mümkün olduğunda tercih edin.**

Varsa bir '\\'veya'\@' nda `Username` özelliği kimlik bilgisi, daha sonra DSC işlemek, bir etki alanı hesabı olarak.
Bir özel durum için "localhost", "127.0.0.1" ve ":: 1" kullanıcı adının etki alanı bölümü içinde.

## <a name="psdscallowdomainuser"></a>PSDscAllowDomainUser

DSC, `Group` yukarıda bir Active Directory etki alanı sorgulanıyor kaynak örnek *gerektirir* bir etki alanı hesabı.
Bu durumda ekleme `PSDscAllowDomainUser` özelliğini `ConfigurationData` bloğunu şu şekilde:

```powershell
$password = "ThisIsAPlaintextPassword" | ConvertTo-SecureString -asPlainText -Force
$username = "contoso\Administrator"
[PSCredential] $credential = New-Object System.Management.Automation.PSCredential($username,$password)

Configuration DomainCredentialExample
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    node localhost
    {
        Group DomainUserToLocalGroup
        {
            GroupName        = 'ApplicationAdmins'
            MembersToInclude = 'contoso\alice'
            Credential       = $credential
        }
    }
}

$cd = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            PSDscAllowDomainUser = $true
            PSDscAllowPlainTextPassword = $true
        }
    )
}

DomainCredentialExample -ConfigurationData $cd
```

Artık yapılandırma betiği ile bir hata veya uyarı MOF dosyası oluşturur.
