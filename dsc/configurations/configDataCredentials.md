---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: Yapılandırma verilerinde kimlik bilgisi seçeneklerinden
ms.openlocfilehash: c4057457bf6beb2c5fc9dffef9122cd488ccdcd7
ms.sourcegitcommit: 9df29dfc637191b62ca591893c251c1e02d4eb4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54012441"
---
# <a name="credentials-options-in-configuration-data"></a>Yapılandırma verilerinde kimlik bilgisi seçeneklerinden
>Şunun için geçerlidir: Windows PowerShell 5.0

## <a name="plain-text-passwords-and-domain-users"></a>Düz metin şifreleri ve etki alanı kullanıcıları

DSC yapılandırmaları içeren bir kimlik bilgisi şifreleme olmadan düz metin parolalar ilgili bir hata iletisi oluşturur.
Ayrıca, DSC etki alanı kimlik bilgilerini kullanarak bir uyarı oluşturur.
Engellemek için bu hata ve uyarı iletilerini DSC yapılandırma verileri anahtar sözcükleri kullanın:
* **PsDscAllowPlainTextPassword**
* **PsDscAllowDomainUser**

> [!NOTE]
> Düz metin parolalar şifrelenmemiş depolayarak/iletme genellikle güvenli değildir. Bu konuda açıklanan teknikleri kullanarak kimlik bilgilerini güvenli hale getirme önerilir.
> Azure Otomasyonu DSC hizmet yapılandırmasında derlenmiş olmaya ve güvenli şekilde depolanan kimlik bilgileri merkezi olarak yönetmenizi sağlar.
> Bilgi için bkz: [DSC yapılandırmaları derleme / kimlik bilgisi varlıkları](/azure/automation/automation-dsc-compile#credential-assets)

Düz metin kimlik bilgilerini geçirerek bir örnek verilmiştir:

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
        $password = $Node.LocalPassword | ConvertTo-SecureString -asPlainText -Force
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
            Credential = $promptedCreds
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

"TestMachine1" yapılandırması tarafından oluşturulan ".mof" dosyasından bir alıntı budur. `System.Security.SecureString` Kullanılan yapılandırma düz metne dönüştürülür ve ".mof" dosyası olarak depolanan bir `MSF_Credential`. A `SecureString` geçerli bir kullanıcı profili ile şifrelenir. Bu da PowerShell uzaktan yönetiminin tüm formları ile çalışır. Bir ".mof" dosyası, bir tek başına yapılandırma mekanizması olacak şekilde tasarlanmıştır. PowerShell 5. 0'den itibaren bekleyen, ancak geçiş düğüme bir düğüm üzerindeki ".mof" dosyalar şifrelenir. Bu, bir düğüme uyguladığınızda ".mof" dosyasında parolaları düz metin ifşa anlamına gelir. Kullanmak istediğiniz kimlik bilgilerini şifrelemek için bir **çekme sunucusu**. Daha fazla bilgi için [sertifikalar ile güvenli hale getirme MOF dosyaları](./pull-server/secureMOF.md).

```syntax
instance of MSFT_Credential as $MSFT_Credential1ref
{
Password = "ThisIsYetAnotherPlaintextPassword";
 UserName = "User2";

};

instance of MSFT_UserResource as $MSFT_UserResource1ref
{
ResourceID = "[User]User2";
 Description = "local account";
 UserName = "User2";
 Ensure = "Present";
 Password = $MSFT_Credential1ref;
 Disabled = False;
 SourceInfo = "::66::9::User";
 PasswordNeverExpires = True;
 ModuleName = "PsDesiredStateConfiguration";
 PasswordChangeRequired = False;

ModuleVersion = "1.0";

 ConfigurationName = "unencryptedPasswordDemo";

};
```

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

Bu örnekte, iki sorun vardır:
1. Bir hata düz metin parolalar önerilmez açıklar.
2. Bir uyarı bir etki alanı kimlik bilgisi kullanılmamasını önerir.

## <a name="psdscallowplaintextpassword"></a>PsDscAllowPlainTextPassword

İlk hata iletisi, belgeleri bir URL vardır.
Bu bağlantıyı kullanarak parolaları şifrelemek açıklanmaktadır bir [ConfigurationData](./configData.md) yapısı ve bir sertifika.
Sertifikaları ve DSC hakkında daha fazla bilgi için [Bu gönderiyi okuyun](http://aka.ms/certs4dsc).

Düz metin parola zorlamak için kaynak gerektiren `PsDscAllowPlainTextPassword` yapılandırma verilerini bir anahtar sözcük bölümünde şu şekilde:

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

> [!NOTE]
> `NodeName` yıldız işareti, belirli bir düğümün adı zorunludur eşit olamaz.

**Önemli güvenlik riski nedeniyle düz metin parolalar önlemek için Microsoft önerir.**

## <a name="domain-credentials"></a>Etki alanı kimlik bilgileri

(İle veya şifreleme olmadan), yeniden örnekte yapılandırma betiği çalıştıran bir etki alanı kullanarak bir kimlik bilgisi hesabı önerilmez uyarı hala oluşturur.
Yerel bir hesap kullanarak, diğer tüm sunucularda kullanılabilir etki alanı kimlik bilgilerini olası riskini ortadan kaldırır.

**DSC kaynakları ile kimlik bilgilerini kullanarak, yerel bir hesap bir etki alanı hesabı mümkün olduğunda tercih edin.**

Varsa bir '\' veya '\@' ın `Username` özelliği kimlik bilgisi, daha sonra DSC işlemek, bir etki alanı hesabı olarak.
Bir özel durum için "localhost", "127.0.0.1" ve ":: 1" kullanıcı adının etki alanı bölümü içinde.

## <a name="psdscallowdomainuser"></a>PSDscAllowDomainUser

DSC, `Group` yukarıda bir Active Directory etki alanı sorgulanıyor kaynak örnek *gerektirir* bir etki alanı hesabı.
Bu durumda ekleme `PSDscAllowDomainUser` özelliğini `ConfigurationData` bloğunu şu şekilde:

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

Artık yapılandırma betiği ile bir hata veya uyarı MOF dosyası oluşturur.
