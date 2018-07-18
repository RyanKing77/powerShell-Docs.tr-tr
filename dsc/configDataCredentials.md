---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: Yapılandırma verilerinde kimlik bilgisi seçeneklerinden
ms.openlocfilehash: 12bb8d8ce5fc4685e583e74d411b098320ac4fd4
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093686"
---
# <a name="credentials-options-in-configuration-data"></a><span data-ttu-id="a6d51-103">Yapılandırma verilerinde kimlik bilgisi seçeneklerinden</span><span class="sxs-lookup"><span data-stu-id="a6d51-103">Credentials Options in Configuration Data</span></span>
><span data-ttu-id="a6d51-104">Uygulama hedefi: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="a6d51-104">Applies To: Windows PowerShell 5.0</span></span>

## <a name="plain-text-passwords-and-domain-users"></a><span data-ttu-id="a6d51-105">Düz metin şifreleri ve etki alanı kullanıcıları</span><span class="sxs-lookup"><span data-stu-id="a6d51-105">Plain Text Passwords and Domain Users</span></span>

<span data-ttu-id="a6d51-106">DSC yapılandırmaları içeren bir kimlik bilgisi şifreleme olmadan düz metin parolalar ilgili bir hata iletisi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a6d51-106">DSC configurations containing a credential without encryption will generate an error message about plain text passwords.</span></span>
<span data-ttu-id="a6d51-107">Ayrıca, DSC etki alanı kimlik bilgilerini kullanarak bir uyarı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a6d51-107">Also, DSC will generate a warning when using domain credentials.</span></span>
<span data-ttu-id="a6d51-108">Engellemek için bu hata ve uyarı iletilerini DSC yapılandırma verileri anahtar sözcükleri kullanın:</span><span class="sxs-lookup"><span data-stu-id="a6d51-108">To suppress these error and warning messages use the DSC configuration data keywords:</span></span>
* <span data-ttu-id="a6d51-109">**PsDscAllowPlainTextPassword**</span><span class="sxs-lookup"><span data-stu-id="a6d51-109">**PsDscAllowPlainTextPassword**</span></span>
* <span data-ttu-id="a6d51-110">**PsDscAllowDomainUser**</span><span class="sxs-lookup"><span data-stu-id="a6d51-110">**PsDscAllowDomainUser**</span></span>

> [!NOTE]
> <span data-ttu-id="a6d51-111">Düz metin parolalar şifrelenmemiş depolayarak/iletme genellikle güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="a6d51-111">Storing/transmitting plaintext passwords unencrypted is generally not secure.</span></span> <span data-ttu-id="a6d51-112">Bu konuda açıklanan teknikleri kullanarak kimlik bilgilerini güvenli hale getirme önerilir.</span><span class="sxs-lookup"><span data-stu-id="a6d51-112">Securing credentials by using the techniques covered later in this topic is recommended.</span></span>
> <span data-ttu-id="a6d51-113">Azure Otomasyonu DSC hizmet yapılandırmasında derlenmiş olmaya ve güvenli şekilde depolanan kimlik bilgileri merkezi olarak yönetmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="a6d51-113">The Azure Automation DSC service allows you to centrally manage credentials to be compiled in configurations and stored securely.</span></span>
> <span data-ttu-id="a6d51-114">Bilgi için bkz: [DSC yapılandırmaları derleme / kimlik bilgisi varlıkları](/azure/automation/automation-dsc-compile#credential-assets)</span><span class="sxs-lookup"><span data-stu-id="a6d51-114">For information, see: [Compiling DSC Configurations / Credential Assets](/azure/automation/automation-dsc-compile#credential-assets)</span></span>

<span data-ttu-id="a6d51-115">Düz metin kimlik bilgilerini geçirerek bir örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="a6d51-115">The following is an example of passing plain text credentials:</span></span>

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

## <a name="handling-credentials-in-dsc"></a><span data-ttu-id="a6d51-116">DSC kimlik bilgilerini işleme</span><span class="sxs-lookup"><span data-stu-id="a6d51-116">Handling Credentials in DSC</span></span>

<span data-ttu-id="a6d51-117">DSC yapılandırma kaynaklarını Çalıştır `Local System` varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="a6d51-117">DSC configuration resources run as `Local System` by default.</span></span>
<span data-ttu-id="a6d51-118">Ancak, bazı kaynaklar bir kimlik bilgisi, örneğin gerektiğinde `Package` kaynak belirli bir kullanıcı hesabı altında yazılımı yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a6d51-118">However, some resources need a credential, for example when the `Package` resource needs to install software under a specific user account.</span></span>

<span data-ttu-id="a6d51-119">Önceki kaynakları kullanılan sabit olarak kodlanmış `Credential` bu durumu çözmek için özellik adı.</span><span class="sxs-lookup"><span data-stu-id="a6d51-119">Earlier resources used a hard-coded `Credential` property name to handle this.</span></span>
<span data-ttu-id="a6d51-120">WMF 5.0 otomatik eklenen `PsDscRunAsCredential` tüm kaynaklar için özellik.</span><span class="sxs-lookup"><span data-stu-id="a6d51-120">WMF 5.0 added an automatic `PsDscRunAsCredential` property for all resources.</span></span>
<span data-ttu-id="a6d51-121">Kullanma hakkında bilgi için `PsDscRunAsCredential`, bkz: [DSC çalıştıran kullanıcı kimlik bilgileriyle](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="a6d51-121">For information about using `PsDscRunAsCredential`, see [Running DSC with user credentials](runAsUser.md).</span></span>
<span data-ttu-id="a6d51-122">Yeni kaynaklar ve özel kaynakların otomatik bu özelliği kendi kimlik bilgilerini özelliği oluşturmak yerine kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a6d51-122">Newer resources and custom resources can use this automatic property instead of creating their own property for credentials.</span></span>

> [!NOTE]
> <span data-ttu-id="a6d51-123">Bazı kaynaklar tasarımını olan belirli bir nedenle birden çok kimlik bilgilerini kullanmayı ve kendi kimlik bilgisi özelliklerine sahip.</span><span class="sxs-lookup"><span data-stu-id="a6d51-123">The design of some resources are to use multiple credentials for a specific reason, and they will have their own credential properties.</span></span>

<span data-ttu-id="a6d51-124">Kullanılabilir kimlik bilgileri bulmak için bir kaynak özelliklerini kullanın `Get-DscResource -Name ResourceName -Syntax` veya işe IntelliSense (`CTRL+SPACE`).</span><span class="sxs-lookup"><span data-stu-id="a6d51-124">To find the available credential properties on a resource use either `Get-DscResource -Name ResourceName -Syntax` or the Intellisense in the ISE (`CTRL+SPACE`).</span></span>

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

<span data-ttu-id="a6d51-125">Bu örnekte bir [grubu](https://msdn.microsoft.com/powershell/dsc/groupresource) kaynaktan `PSDesiredStateConfiguration` yerleşik DSC kaynak modülü.</span><span class="sxs-lookup"><span data-stu-id="a6d51-125">This example uses a [Group](https://msdn.microsoft.com/powershell/dsc/groupresource) resource from the `PSDesiredStateConfiguration` built-in DSC resource module.</span></span>
<span data-ttu-id="a6d51-126">Bu yerel gruplarını oluşturun ve ekleyebilir veya üyeleri kaldırın.</span><span class="sxs-lookup"><span data-stu-id="a6d51-126">It can create local groups and add or remove members.</span></span>
<span data-ttu-id="a6d51-127">Hem kabul ettiği `Credential` özelliği ve otomatik `PsDscRunAsCredential` özelliği.</span><span class="sxs-lookup"><span data-stu-id="a6d51-127">It accepts both the `Credential` property and the automatic `PsDscRunAsCredential` property.</span></span>
<span data-ttu-id="a6d51-128">Ancak, yalnızca kaynak kullanan `Credential` özelliği.</span><span class="sxs-lookup"><span data-stu-id="a6d51-128">However, the resource only uses the `Credential` property.</span></span>

<span data-ttu-id="a6d51-129">Hakkında daha fazla bilgi için `PsDscRunAsCredential` özelliğine bakın [DSC çalıştıran kullanıcı kimlik bilgileriyle](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="a6d51-129">For more information about the `PsDscRunAsCredential` property, see [Running DSC with user credentials](runAsUser.md).</span></span>

## <a name="example-the-group-resource-credential-property"></a><span data-ttu-id="a6d51-130">Örnek: Grubu kaynağının Credential özelliği</span><span class="sxs-lookup"><span data-stu-id="a6d51-130">Example: The Group resource Credential property</span></span>

<span data-ttu-id="a6d51-131">DSC çalıştıran altında `Local System`, yerel kullanıcılar ve gruplar değiştirmek için izinlere zaten sahip.</span><span class="sxs-lookup"><span data-stu-id="a6d51-131">DSC runs under `Local System`, so it already has permissions to change local users and groups.</span></span>
<span data-ttu-id="a6d51-132">Eklenen üye bir yerel hesapsa, hiçbir kimlik bilgisi gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a6d51-132">If the member added is a local account, then no credential is necessary.</span></span>
<span data-ttu-id="a6d51-133">Varsa `Group` kaynak, yerel gruba bir etki alanı hesabı ekler ve ardından bir kimlik bilgisi gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a6d51-133">If the `Group` resource adds a domain account to the local group, then a credential is necessary.</span></span>

<span data-ttu-id="a6d51-134">Active Directory anonim sorgulara izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="a6d51-134">Anonymous queries to Active Directory are not allowed.</span></span>
<span data-ttu-id="a6d51-135">`Credential` Özelliği `Group` kullanılan sorgu için Active Directory etki alanı hesabı bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="a6d51-135">The `Credential` property of the `Group` resource is the domain account used to query Active Directory.</span></span>
<span data-ttu-id="a6d51-136">Birçok amaç için bunun nedeni, varsayılan olarak, kullanıcıların yükleyebileceği bir genel kullanıcı hesabı olabilir *okuma* Active Directory içindeki nesneleri çoğu.</span><span class="sxs-lookup"><span data-stu-id="a6d51-136">For most purposes this could be a generic user account, because by default users can *read* most of the objects in Active Directory.</span></span>

## <a name="example-configuration"></a><span data-ttu-id="a6d51-137">Örnek yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a6d51-137">Example Configuration</span></span>

<span data-ttu-id="a6d51-138">Aşağıdaki kod örneği, bir yerel Grup bir etki alanı kullanıcısı ile doldurmak için DSC kullanır:</span><span class="sxs-lookup"><span data-stu-id="a6d51-138">The following example code uses DSC to populate a local group with a domain user:</span></span>

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

<span data-ttu-id="a6d51-139">Bu kod, bir hata ve uyarı iletisi oluşturur:</span><span class="sxs-lookup"><span data-stu-id="a6d51-139">This code generates both an error and warning message:</span></span>

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

<span data-ttu-id="a6d51-140">Bu örnekte, iki sorun vardır:</span><span class="sxs-lookup"><span data-stu-id="a6d51-140">This example has two issues:</span></span>
1. <span data-ttu-id="a6d51-141">Bir hata düz metin parolalar önerilmez açıklar.</span><span class="sxs-lookup"><span data-stu-id="a6d51-141">An error explains that plain text passwords are not recommended</span></span>
2. <span data-ttu-id="a6d51-142">Bir uyarı bir etki alanı kimlik bilgisi kullanılmamasını önerir.</span><span class="sxs-lookup"><span data-stu-id="a6d51-142">A warning advises against using a domain credential</span></span>

## <a name="psdscallowplaintextpassword"></a><span data-ttu-id="a6d51-143">PsDscAllowPlainTextPassword</span><span class="sxs-lookup"><span data-stu-id="a6d51-143">PsDscAllowPlainTextPassword</span></span>

<span data-ttu-id="a6d51-144">İlk hata iletisi, belgeleri bir URL vardır.</span><span class="sxs-lookup"><span data-stu-id="a6d51-144">The first error message has a URL with documentation.</span></span>
<span data-ttu-id="a6d51-145">Bu bağlantıyı kullanarak parolaları şifrelemek açıklanmaktadır bir [ConfigurationData](https://msdn.microsoft.com/powershell/dsc/configdata) yapısı ve bir sertifika.</span><span class="sxs-lookup"><span data-stu-id="a6d51-145">This link explains how to encrypt passwords using a [ConfigurationData](https://msdn.microsoft.com/powershell/dsc/configdata) structure and a certificate.</span></span>
<span data-ttu-id="a6d51-146">Sertifikaları ve DSC hakkında daha fazla bilgi için [Bu gönderiyi okuyun](http://aka.ms/certs4dsc).</span><span class="sxs-lookup"><span data-stu-id="a6d51-146">For more information on certificates and DSC [read this post](http://aka.ms/certs4dsc).</span></span>

<span data-ttu-id="a6d51-147">Düz metin parola zorlamak için kaynak gerektiren `PsDscAllowPlainTextPassword` yapılandırma verilerini bir anahtar sözcük bölümünde şu şekilde:</span><span class="sxs-lookup"><span data-stu-id="a6d51-147">To force a plain text password, the resource requires the `PsDscAllowPlainTextPassword` keyword in the configuration data section as follows:</span></span>

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
> <span data-ttu-id="a6d51-148">`NodeName` yıldız işareti, belirli bir düğümün adı zorunludur eşit olamaz.</span><span class="sxs-lookup"><span data-stu-id="a6d51-148">`NodeName` cannot equal asterisk, a specific node name is mandatory.</span></span>

<span data-ttu-id="a6d51-149">**Önemli güvenlik riski nedeniyle düz metin parolalar önlemek için Microsoft önerir.**</span><span class="sxs-lookup"><span data-stu-id="a6d51-149">**Microsoft advises to avoid plain text passwords due to the significant security risk.**</span></span>

## <a name="domain-credentials"></a><span data-ttu-id="a6d51-150">Etki alanı kimlik bilgileri</span><span class="sxs-lookup"><span data-stu-id="a6d51-150">Domain Credentials</span></span>

<span data-ttu-id="a6d51-151">(İle veya şifreleme olmadan), yeniden örnekte yapılandırma betiği çalıştıran bir etki alanı kullanarak bir kimlik bilgisi hesabı önerilmez uyarı hala oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a6d51-151">Running the example configuration script again (with or without encryption), still generates the warning that using a domain account for a credential is not recommended.</span></span>
<span data-ttu-id="a6d51-152">Yerel bir hesap kullanarak, diğer tüm sunucularda kullanılabilir etki alanı kimlik bilgilerini olası riskini ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="a6d51-152">Using a local account eliminates potential exposure of domain credentials that could be used on other servers.</span></span>

<span data-ttu-id="a6d51-153">**DSC kaynakları ile kimlik bilgilerini kullanarak, yerel bir hesap bir etki alanı hesabı mümkün olduğunda tercih edin.**</span><span class="sxs-lookup"><span data-stu-id="a6d51-153">**When using credentials with DSC resources, prefer a local account over a domain account when possible.**</span></span>

<span data-ttu-id="a6d51-154">Varsa bir '\' veya '\@' ın `Username` özelliği kimlik bilgisi, daha sonra DSC işlemek, bir etki alanı hesabı olarak.</span><span class="sxs-lookup"><span data-stu-id="a6d51-154">If there is a '\' or '@' in the `Username` property of the credential, then DSC will treat it as a domain account.</span></span>
<span data-ttu-id="a6d51-155">Bir özel durum için "localhost", "127.0.0.1" ve ":: 1" kullanıcı adının etki alanı bölümü içinde.</span><span class="sxs-lookup"><span data-stu-id="a6d51-155">There is an exception for "localhost", "127.0.0.1", and "::1" in the domain portion of the user name.</span></span>

## <a name="psdscallowdomainuser"></a><span data-ttu-id="a6d51-156">PSDscAllowDomainUser</span><span class="sxs-lookup"><span data-stu-id="a6d51-156">PSDscAllowDomainUser</span></span>

<span data-ttu-id="a6d51-157">DSC, `Group` yukarıda bir Active Directory etki alanı sorgulanıyor kaynak örnek *gerektirir* bir etki alanı hesabı.</span><span class="sxs-lookup"><span data-stu-id="a6d51-157">In the DSC `Group` resource example above, querying an Active Directory domain *requires* a domain account.</span></span>
<span data-ttu-id="a6d51-158">Bu durumda ekleme `PSDscAllowDomainUser` özelliğini `ConfigurationData` bloğunu şu şekilde:</span><span class="sxs-lookup"><span data-stu-id="a6d51-158">In this case add the `PSDscAllowDomainUser` property to the `ConfigurationData` block as follows:</span></span>

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

<span data-ttu-id="a6d51-159">Artık yapılandırma betiği ile bir hata veya uyarı MOF dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a6d51-159">Now the configuration script will generate the MOF file with no errors or warnings.</span></span>
