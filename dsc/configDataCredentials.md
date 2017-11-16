---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "Yapılandırma verilerini seçeneklerinde kimlik bilgileri"
ms.openlocfilehash: 94ff541fc517254ef2876c424307513eaf1d362a
ms.sourcegitcommit: 28e71b0ae868014523631fec3f5417de751944f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2017
---
# <a name="credentials-options-in-configuration-data"></a>Yapılandırma verilerini seçeneklerinde kimlik bilgileri
>İçin geçerlidir: Windows PowerShell 5.0

## <a name="plain-text-passwords-and-domain-users"></a>Düz metin parola ve etki alanı kullanıcıları

DSC yapılandırmaları şifreleme olmadan kimlik bilgisi içeren düz metin parolalarını ilgili bir hata iletisi oluşturur.
Ayrıca, DSC etki alanı kimlik bilgileri kullanırken bir uyarı oluşturur.
Gizlemek için bu hata ve uyarı iletileri DSC yapılandırma verileri anahtar sözcükler kullanın:
* **PsDscAllowPlainTextPassword**
* **PsDscAllowDomainUser**

>**Notlar:** <p>Depolama/iletmek düz metin parolalarını şifrelenmemiş genellikle güvenli değildir. Bu konuda açıklanan teknikleri kullanarak kimlik bilgilerini güvenli hale getirme önerilir.</p> <p>Azure Otomasyonu DSC hizmet yapılandırmalarında derlenmiş ve güvenli şekilde depolanan kimlik bilgileri merkezi olarak yönetmenizi sağlar.  Bilgi için bkz: [derleme DSC yapılandırmaları / kimlik bilgisi varlıkları](https://docs.microsoft.com/en-in/azure/automation/automation-dsc-compile#credential-assets)</p>

Düz metin kimlik bilgileri geçirme bir örnek verilmiştir:

```powershell
#Prompt user for their credentials
#credentials will be unencrypted in the MOF
$promptedCreds = get-credential -Message "Please enter your credentials to generate a DSC MOF:"

# Store passwords in plaintext, in the document itself
# will also be stored in plaintext in the mof
$password = "ThisIsAPlaintextPassword" | ConvertTo-SecureString -asPlainText -Force
$username = "User1"
[PSCredential] $credential = New-Object System.Management.Automation.PSCredential($username,$password)

# DSC requires explicit confirmation before storing passwords insecurely
$ConfigurationData = @{
    AllNodes = @(
        @{
            # The "*" means "all nodes named in ConfigData" so we don't have to repeat ourselves
            NodeName="*"
            PSDscAllowPlainTextPassword = $true
        },
        #however, each node still needs to be explicitly defined for "*" to have meaning
        @{
            NodeName = "TestMachine1"
        },
        #we can also use a property to define node-specific passwords, although this is no more secure
        @{
            NodeName = "TestMachine2";
            UserName = "User2"
            LocalPassword = "ThisIsYetAnotherPlaintextPassword"
        }
        )
}
configuration unencryptedPasswordDemo
{
    Node "TestMachine1"
    {
        # We use the plaintext password to generate a new account
        User User1
        {
            UserName = $username
            Password = $credential
            Description = "local account"
            Ensure = "Present"
            Disabled = $false
            PasswordNeverExpires = $true
            PasswordChangeRequired = $false
        }
        # We use the prompted password to add this account to the local admins group
        Group addToAdmin
        {
            # Ensure the user exists before we add the user to a group
            DependsOn = "[User]User1"
            Credential = $promptedCreds
            GroupName = "Administrators"
            Ensure = "Present"
            MembersToInclude = "User1"
        }
    }

    Node "TestMachine2"
    {
        # Now we'll use a node-specific password to this machine
        $password = $Node.LocalPass | ConvertTo-SecureString -asPlainText -Force
        $username = $node.UserName
        [PSCredential] $nodeCred = New-Object System.Management.Automation.PSCredential($username,$password)

        User User2
        {
            UserName = $username
            Password = $nodeCred
            Description = "local account"
            Ensure = "Present"
            Disabled = $false
            PasswordNeverExpires = $true
            PasswordChangeRequired = $false
        }

        Group addToAdmin
        {
            Credential = $domain
            GroupName = "Administrators"
            DependsOn = "[User]User2"
            Ensure = "Present"
            MembersToInclude = "User2"
        }
    }

}
# We declared the ConfigurationData in a local variable, but we need to pass it in to our configuration function
# We need to invoke the configuration function we created to generate a MOF
unencryptedPasswordDemo -ConfigurationData $ConfigurationData
# We need to pass the MOF to the machines we named.
#-wait: doesn't use jobs so we get blocked at the prompt until the configuration is done
#-verbose: so we can see what's going on and catch any errors
#-force: for testing purposes, I run start-dscconfiguration frequently + want to make sure i'm
#        not blocked by previous configurations that are still running
Start-DscConfiguration ./unencryptedPasswordDemo -verbose -wait -force
```

## <a name="handling-credentials-in-dsc"></a>DSC kimlik bilgilerini işleme

DSC yapılandırması kaynakları Farklı Çalıştır `Local System` varsayılan olarak.
Ancak, bazı kaynaklar bir kimlik bilgileri, örneğin gerektiğinde `Package` kaynak belirli bir kullanıcı hesabı altında yazılımı yüklemeniz gerekir.

Önceki kaynakların kullanılan bir sabit kodlanmış `Credential` bu durumu çözmek için özellik adı.
WMF 5.0 eklenen otomatik `PsDscRunAsCredential` tüm kaynaklar için özellik.
Kullanma hakkında bilgi için `PsDscRunAsCredential`, bkz: [çalıştıran DSC kullanıcı kimlik bilgileriyle](runAsUser.md).
Daha yeni kaynakları ve özel kaynakları için kimlik bilgilerini kendi özelliği oluşturmak yerine bu otomatik özelliğini kullanabilirsiniz.

>**Not:** bazı kaynaklar tasarımını olan belirli bir nedenle birden çok kimlik bilgilerini kullanmayı ve kendi kimlik özelliklerine sahip olur.

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

Bu örnekte bir [grup](https://msdn.microsoft.com/en-us/powershell/dsc/groupresource) kaynaktan `PSDesiredStateConfiguration` yerleşik DSC kaynakları modülü.
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
ConvertTo-MOFInstance : System.InvalidOperationException error processing
property 'Credential' OF TYPE 'Group': Converting and storing encrypted
passwords as plain text is not recommended. For more information on securing
credentials in MOF file, please refer to MSDN blog:
http://go.microsoft.com/fwlink/?LinkId=393729

At line:11 char:9
+   Group
At line:297 char:16
+     $aliasId = ConvertTo-MOFInstance $keywordName $canonicalizedValue
+                ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Write-Error], InvalidOperationException
    + FullyQualifiedErrorId : FailToProcessProperty,ConvertTo-MOFInstance

WARNING: It is not recommended to use domain credential for node 'localhost'.
In order to suppress the warning, you can add a property named
'PSDscAllowDomainUser' with a value of $true to your DSC configuration data
for node 'localhost'.
```

Bu örnek iki sorunları vardır:
1.  Düz metin parolalarını önerilmez hata açıklar
2.  Bir uyarı etki alanı kimlik bilgilerini kullanarak karşı öneren

## <a name="psdscallowplaintextpassword"></a>PsDscAllowPlainTextPassword

İlk hata iletisi belgelerine bir URL'ye sahip.
Bu bağlantıyı kullanarak parolaları şifrelemek açıklanmaktadır bir [ConfigurationData](https://msdn.microsoft.com/en-us/powershell/dsc/configdata) yapısı ve bir sertifika.
Sertifikalar ve DSC hakkında daha fazla bilgi için [bu gönderisini okuduğunuzu](http://aka.ms/certs4dsc).

Düz metinli bir parola zorlamak için kaynak gerektiriyor `PsDscAllowPlainTextPassword` yapılandırma verilerinde anahtar sözcüğü bölümünde aşağıdaki gibi:

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

$cd = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            PSDscAllowPlainTextPassword = $true
        }
    )
}

$cred = Get-Credential -UserName contoso\genericuser -Message "Password please"
DomainCredentialExample -DomainCredential $cred -ConfigurationData $cd
```

>**Not:** `NodeName` yıldız işareti, belirli düğüm adı zorunludur eşit olamaz.

**Düz metin parolalarını önemli güvenlik riski nedeniyle önlemek için Microsoft önerir.**
Yalnızca (aktarımda, hizmet REST ve düğüm üzerinde bekleyen) şifreli her zaman verilerin depolandığı için bir özel durum Azure Otomasyonu DSC hizmetini kullanırken olacaktır.

## <a name="domain-credentials"></a>Etki alanı kimlik bilgileri

Örnek yapılandırma betiği yeniden (ile veya şifreleme olmadan) çalıştıran bir etki alanı hesabı bir kimlik bilgisi için önerilmez uyarı hala oluşturur.
Yerel bir hesap kullanarak diğer sunucularda kullanılabilir etki alanı kimlik bilgileri olası riskini ortadan kaldırır.

**Kimlik bilgileri ile DSC kaynakları kullanılırken, yerel bir hesap bir etki alanı hesabı mümkün olduğunda tercih edilir.**

Varsa bir '\' veya ' @' ın `Username` özelliği kimlik bilgisi, daha sonra DSC işlemek, bir etki alanı hesabı olarak.
"Localhost", "127.0.0.1" için bir özel durum yoktur ve ":: 1" kullanıcı adı etki alanı kısmının.

## <a name="psdscallowdomainuser"></a>PSDscAllowDomainUser

DSC içinde `Group` yukarıda, bir Active Directory etki alanı sorgulama kaynak örnek *gerektirir* bir etki alanı hesabı.
Bu durumda eklemek `PSDscAllowDomainUser` özelliğine `ConfigurationData` gibi engelle:

```powershell
$cd = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            PSDscAllowDomainUser = $true
            # PSDscAllowPlainTextPassword = $true
            CertificateFile = "C:\PublicKeys\server1.cer"
        }
    )
}
```

Artık yapılandırma komut dosyası hata veya uyarı ile MOF dosyası oluşturur.
