---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: Yapılandırma verilerini seçeneklerinde kimlik bilgileri
ms.openlocfilehash: 2a326e45bbbad7bd2362b66b88bf61b98df7b02e
ms.sourcegitcommit: 6ae5b50a4b3ffcd649de1525c3ce6f15d3669082
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/18/2019
ms.locfileid: "55686379"
---
# <a name="credentials-options-in-configuration-data"></a>Yapılandırma verilerini seçeneklerinde kimlik bilgileri

>Şunun için geçerlidir: Windows PowerShell 5.0

## <a name="plain-text-passwords-and-domain-users"></a>Düz metin parola ve etki alanı kullanıcıları

DSC yapılandırmaları şifreleme olmadan kimlik bilgisi içeren düz metin parolalarını ilgili bir hata iletisi oluşturur.
Ayrıca, DSC etki alanı kimlik bilgileri kullanırken bir uyarı oluşturur.
Gizlemek için bu hata ve uyarı iletileri DSC yapılandırma verileri anahtar sözcükler kullanın:

- **PsDscAllowPlainTextPassword**
- **PsDscAllowDomainUser**

> [!NOTE]
> Depolama/iletmek düz metin parolalarını şifrelenmemiş genellikle güvenli değildir. Bu konuda açıklanan teknikleri kullanarak kimlik bilgilerini güvenli hale getirme önerilir.
> Azure Otomasyonu DSC hizmet yapılandırmalarında derlenmiş ve güvenli şekilde depolanan kimlik bilgileri merkezi olarak yönetmenizi sağlar.
> Bilgi için bkz: [DSC yapılandırmaları derleme / kimlik bilgisi varlıkları](/azure/automation/automation-dsc-compile#credential-assets)

## <a name="handling-credentials-in-dsc"></a>DSC kimlik bilgilerini işleme

DSC yapılandırması kaynakları Farklı Çalıştır `Local System` varsayılan olarak.
Ancak, bazı kaynaklar bir kimlik bilgileri, örneğin gerektiğinde `Package` kaynak belirli bir kullanıcı hesabı altında yazılımı yüklemeniz gerekir.

Önceki kaynakların kullanılan bir sabit kodlanmış `Credential` bu durumu çözmek için özellik adı.
WMF 5.0 eklenen otomatik `PsDscRunAsCredential` tüm kaynaklar için özellik.
Kullanma hakkında bilgi için `PsDscRunAsCredential`, bkz: [çalıştıran DSC kullanıcı kimlik bilgileriyle](runAsUser.md).
Daha yeni kaynakları ve özel kaynakları için kimlik bilgilerini kendi özelliği oluşturmak yerine bu otomatik özelliğini kullanabilirsiniz.

> [!NOTE]
> Bazı kaynaklar tasarımını olan belirli bir nedenle birden çok kimlik bilgilerini kullanmayı ve kendi kimlik özelliklerine sahip olur.

Kullanılabilir kimlik bilgisi bulmak için bir kaynak özelliklerini kullanın ya da `Get-DscResource -Name ResourceName -Syntax` veya işe IntelliSense (`CTRL+SPACE`).

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

Bu örnekte bir [grup](../resources/resources.md) kaynaktan `PSDesiredStateConfiguration` yerleşik DSC kaynakları modülü.
Onu yerel gruplar oluşturabilir ve ekleyebilir veya üyeleri kaldırın.
Her ikisini de kabul `Credential` özelliği ve otomatik `PsDscRunAsCredential` özelliği.
Ancak, kaynak yalnızca kullanır `Credential` özelliği.

Hakkında daha fazla bilgi için `PsDscRunAsCredential` özelliği, bkz: [çalıştıran DSC kullanıcı kimlik bilgileriyle](runAsUser.md).

## <a name="example-the-group-resource-credential-property"></a>Örnek: Grup Kaynak kimlik bilgisi özelliği

DSC çalıştıran altında `Local System`, yerel kullanıcılar ve gruplar değiştirme izni zaten sahiptir.
Yerel bir hesap eklenen üyesi ise, hiçbir kimlik bilgisi gereklidir.
Varsa `Group` kaynak etki alanı hesabı yerel grubuna ekler, sonra bir kimlik bilgisi gereklidir.

Active Directory anonim sorgularına izin verilmiyor.
`Credential` Özelliği `Group` kaynak Active Directory'yi sorgulamak için kullanılan etki alanı hesabıdır.
Çoğu amaç için varsayılan olarak kullanıcılar şunları yapabilir Bunun nedeni bir genel kullanıcı hesabı olabilir *okuma* Active Directory içindeki nesneleri çoğu.

## <a name="example-configuration"></a>Örnek yapılandırma

Aşağıdaki kod örneği, bir etki alanı kullanıcısı ile yerel bir grup doldurmak için DSC kullanır:

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

Bu örnek iki sorunları vardır:

1. Düz metin parolalarını önerilmez hata açıklar
2. Bir uyarı etki alanı kimlik bilgilerini kullanarak karşı öneren

Bayrakları **PSDSCAllowPlainTextPassword** ve **PSDSCAllowDomainUser** hata ve söz konusu riski kullanıcı bildiren uyarı gösterme.

## <a name="psdscallowplaintextpassword"></a>PSDSCAllowPlainTextPassword

İlk hata iletisi belgelerine bir URL'ye sahip.
Bu bağlantıyı kullanarak parolaları şifrelemek açıklanmaktadır bir [ConfigurationData](./configData.md) yapısı ve bir sertifika.
Sertifikalar ve DSC hakkında daha fazla bilgi için [bu gönderisini okuduğunuzu](http://aka.ms/certs4dsc).

Düz metinli bir parola zorlamak için kaynak gerektiriyor `PsDscAllowPlainTextPassword` yapılandırma verilerinde anahtar sözcüğü bölümünde aşağıdaki gibi:

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

**PSDSCAllowPlainTextPassword** bayrağı gerektiren kullanıcı MOF dosyasında düz metin parolalarını depolama riskini kabul. Oluşturulan MOF dosyasındaki olsa bile bir **PSCredential** nesnesini içeren bir **SecureString** , parolaları düz metin olarak görünmeye kullanıldı. Bu kimlik bilgilerinin gösterildiği yalnızca bir kez gösterilecektir. Herkes yönetici hesabına bu MOF dosyası erişmenizi erişimini.

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

### <a name="credentials-in-transit-and-at-rest"></a>Kimlik aktarım ve REST

- **PSDscAllowPlainTextPassword** bayrağı şifresiz parolalar içeren MOF dosyaları derlenmesini sağlar.
  Şifresiz parolalar içeren MOF dosyaları depolarken önlemleri alın.
- Ne zaman MOF dosyası teslim edilirse bir düğüme **anında** modu, WinRM şifreler varsayılan geçersiz kılma sürece düz metin parolası korumak için iletişim **AllowUnencrypted** parametresi.
  - Bir düğüme uygulanan önce bir sertifika ile MOF şifreleme REST MOF dosyası korur.
- İçinde **çekme** modu, Internet Information Server'ın belirtilen protokolünü kullanarak trafiği şifrelemek için HTTPS kullanmak üzere Windows çekme sunucusunu yapılandırabilirsiniz. Daha fazla bilgi için makalelere bakın [bir DSC çekme istemcisi kurarken](../pull-server/pullclient.md) ve [sertifikalar ile güvenli hale getirme MOF dosyaları](../pull-server/secureMOF.md).
  - İçinde [Azure Otomasyon durum Yapılandırması](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview) hizmeti, çekme trafiği her zaman şifrelenir.
- Düğümde, MOF dosyalarını bekleyen şifrelenir PowerShell 5. 0'den itibaren.
  - Gönderilen veya düğüme çekilen bir sertifikayla şifrelenmiş sürece PowerShell 4.0 MOF dosyaları bekleyen şifrelenmemiş.

**Düz metin parolalarını önemli güvenlik riski nedeniyle önlemek için Microsoft önerir.**

## <a name="domain-credentials"></a>Etki alanı kimlik bilgileri

Örnek yapılandırma betiği yeniden (ile veya şifreleme olmadan) çalıştıran bir etki alanı hesabı bir kimlik bilgisi için önerilmez uyarı hala oluşturur.
Yerel bir hesap kullanarak diğer sunucularda kullanılabilir etki alanı kimlik bilgileri olası riskini ortadan kaldırır.

**Kimlik bilgileri ile DSC kaynakları kullanılırken, yerel bir hesap bir etki alanı hesabı mümkün olduğunda tercih edilir.**

Varsa bir '\\'veya'\@' ın `Username` özelliği kimlik bilgisi, daha sonra DSC işlemek, bir etki alanı hesabı olarak.
"Localhost", "127.0.0.1" için bir özel durum yoktur ve ":: 1" kullanıcı adı etki alanı kısmının.

## <a name="psdscallowdomainuser"></a>PSDscAllowDomainUser

DSC içinde `Group` yukarıda, bir Active Directory etki alanı sorgulama kaynak örnek *gerektirir* bir etki alanı hesabı.
Bu durumda eklemek `PSDscAllowDomainUser` özelliğine `ConfigurationData` gibi engelle:

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

Artık yapılandırma komut dosyası hata veya uyarı ile MOF dosyası oluşturur.
