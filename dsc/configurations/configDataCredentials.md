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
# <a name="credentials-options-in-configuration-data"></a><span data-ttu-id="8060f-103">Yapılandırma verilerinde kimlik bilgisi seçeneklerinden</span><span class="sxs-lookup"><span data-stu-id="8060f-103">Credentials Options in Configuration Data</span></span>

><span data-ttu-id="8060f-104">Şunun için geçerlidir: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="8060f-104">Applies To: Windows PowerShell 5.0</span></span>

## <a name="plain-text-passwords-and-domain-users"></a><span data-ttu-id="8060f-105">Düz metin şifreleri ve etki alanı kullanıcıları</span><span class="sxs-lookup"><span data-stu-id="8060f-105">Plain Text Passwords and Domain Users</span></span>

<span data-ttu-id="8060f-106">DSC yapılandırmaları içeren bir kimlik bilgisi şifreleme olmadan düz metin parolalar ilgili bir hata iletisi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8060f-106">DSC configurations containing a credential without encryption will generate an error message about plain text passwords.</span></span>
<span data-ttu-id="8060f-107">Ayrıca, DSC etki alanı kimlik bilgilerini kullanarak bir uyarı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8060f-107">Also, DSC will generate a warning when using domain credentials.</span></span>
<span data-ttu-id="8060f-108">Engellemek için bu hata ve uyarı iletilerini DSC yapılandırma verileri anahtar sözcükleri kullanın:</span><span class="sxs-lookup"><span data-stu-id="8060f-108">To suppress these error and warning messages use the DSC configuration data keywords:</span></span>

- <span data-ttu-id="8060f-109">**PsDscAllowPlainTextPassword**</span><span class="sxs-lookup"><span data-stu-id="8060f-109">**PsDscAllowPlainTextPassword**</span></span>
- <span data-ttu-id="8060f-110">**PsDscAllowDomainUser**</span><span class="sxs-lookup"><span data-stu-id="8060f-110">**PsDscAllowDomainUser**</span></span>

> [!NOTE]
> <span data-ttu-id="8060f-111">Düz metin parolalar şifrelenmemiş depolayarak/iletme genellikle güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="8060f-111">Storing/transmitting plaintext passwords unencrypted is generally not secure.</span></span> <span data-ttu-id="8060f-112">Bu konuda açıklanan teknikleri kullanarak kimlik bilgilerini güvenli hale getirme önerilir.</span><span class="sxs-lookup"><span data-stu-id="8060f-112">Securing credentials by using the techniques covered later in this topic is recommended.</span></span>
> <span data-ttu-id="8060f-113">Azure Otomasyonu DSC hizmet yapılandırmasında derlenmiş olmaya ve güvenli şekilde depolanan kimlik bilgileri merkezi olarak yönetmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="8060f-113">The Azure Automation DSC service allows you to centrally manage credentials to be compiled in configurations and stored securely.</span></span>
> <span data-ttu-id="8060f-114">Bilgi için bkz: [DSC yapılandırmaları derleme / kimlik bilgisi varlıkları](/azure/automation/automation-dsc-compile#credential-assets)</span><span class="sxs-lookup"><span data-stu-id="8060f-114">For information, see: [Compiling DSC Configurations / Credential Assets](/azure/automation/automation-dsc-compile#credential-assets)</span></span>

## <a name="handling-credentials-in-dsc"></a><span data-ttu-id="8060f-115">DSC kimlik bilgilerini işleme</span><span class="sxs-lookup"><span data-stu-id="8060f-115">Handling Credentials in DSC</span></span>

<span data-ttu-id="8060f-116">DSC yapılandırma kaynaklarını Çalıştır `Local System` varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="8060f-116">DSC configuration resources run as `Local System` by default.</span></span>
<span data-ttu-id="8060f-117">Ancak, bazı kaynaklar bir kimlik bilgisi, örneğin gerektiğinde `Package` kaynak belirli bir kullanıcı hesabı altında yazılımı yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8060f-117">However, some resources need a credential, for example when the `Package` resource needs to install software under a specific user account.</span></span>

<span data-ttu-id="8060f-118">Önceki kaynakları kullanılan sabit olarak kodlanmış `Credential` bu durumu çözmek için özellik adı.</span><span class="sxs-lookup"><span data-stu-id="8060f-118">Earlier resources used a hard-coded `Credential` property name to handle this.</span></span>
<span data-ttu-id="8060f-119">WMF 5.0 otomatik eklenen `PsDscRunAsCredential` tüm kaynaklar için özellik.</span><span class="sxs-lookup"><span data-stu-id="8060f-119">WMF 5.0 added an automatic `PsDscRunAsCredential` property for all resources.</span></span>
<span data-ttu-id="8060f-120">Kullanma hakkında bilgi için `PsDscRunAsCredential`, bkz: [DSC çalıştıran kullanıcı kimlik bilgileriyle](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="8060f-120">For information about using `PsDscRunAsCredential`, see [Running DSC with user credentials](runAsUser.md).</span></span>
<span data-ttu-id="8060f-121">Yeni kaynaklar ve özel kaynakların otomatik bu özelliği kendi kimlik bilgilerini özelliği oluşturmak yerine kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8060f-121">Newer resources and custom resources can use this automatic property instead of creating their own property for credentials.</span></span>

> [!NOTE]
> <span data-ttu-id="8060f-122">Bazı kaynaklar tasarımını olan belirli bir nedenle birden çok kimlik bilgilerini kullanmayı ve kendi kimlik bilgisi özelliklerine sahip.</span><span class="sxs-lookup"><span data-stu-id="8060f-122">The design of some resources are to use multiple credentials for a specific reason, and they will have their own credential properties.</span></span>

<span data-ttu-id="8060f-123">Kullanılabilir kimlik bilgileri bulmak için bir kaynak özelliklerini kullanın `Get-DscResource -Name ResourceName -Syntax` veya işe IntelliSense (`CTRL+SPACE`).</span><span class="sxs-lookup"><span data-stu-id="8060f-123">To find the available credential properties on a resource use either `Get-DscResource -Name ResourceName -Syntax` or the Intellisense in the ISE (`CTRL+SPACE`).</span></span>

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

<span data-ttu-id="8060f-124">Bu örnekte bir [grubu](../resources/resources.md) kaynaktan `PSDesiredStateConfiguration` yerleşik DSC kaynak modülü.</span><span class="sxs-lookup"><span data-stu-id="8060f-124">This example uses a [Group](../resources/resources.md) resource from the `PSDesiredStateConfiguration` built-in DSC resource module.</span></span>
<span data-ttu-id="8060f-125">Bu yerel gruplarını oluşturun ve ekleyebilir veya üyeleri kaldırın.</span><span class="sxs-lookup"><span data-stu-id="8060f-125">It can create local groups and add or remove members.</span></span>
<span data-ttu-id="8060f-126">Hem kabul ettiği `Credential` özelliği ve otomatik `PsDscRunAsCredential` özelliği.</span><span class="sxs-lookup"><span data-stu-id="8060f-126">It accepts both the `Credential` property and the automatic `PsDscRunAsCredential` property.</span></span>
<span data-ttu-id="8060f-127">Ancak, yalnızca kaynak kullanan `Credential` özelliği.</span><span class="sxs-lookup"><span data-stu-id="8060f-127">However, the resource only uses the `Credential` property.</span></span>

<span data-ttu-id="8060f-128">Hakkında daha fazla bilgi için `PsDscRunAsCredential` özelliğine bakın [DSC çalıştıran kullanıcı kimlik bilgileriyle](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="8060f-128">For more information about the `PsDscRunAsCredential` property, see [Running DSC with user credentials](runAsUser.md).</span></span>

## <a name="example-the-group-resource-credential-property"></a><span data-ttu-id="8060f-129">Örnek: Grubu kaynağının Credential özelliği</span><span class="sxs-lookup"><span data-stu-id="8060f-129">Example: The Group resource Credential property</span></span>

<span data-ttu-id="8060f-130">DSC çalıştıran altında `Local System`, yerel kullanıcılar ve gruplar değiştirmek için izinlere zaten sahip.</span><span class="sxs-lookup"><span data-stu-id="8060f-130">DSC runs under `Local System`, so it already has permissions to change local users and groups.</span></span>
<span data-ttu-id="8060f-131">Eklenen üye bir yerel hesapsa, hiçbir kimlik bilgisi gereklidir.</span><span class="sxs-lookup"><span data-stu-id="8060f-131">If the member added is a local account, then no credential is necessary.</span></span>
<span data-ttu-id="8060f-132">Varsa `Group` kaynak, yerel gruba bir etki alanı hesabı ekler ve ardından bir kimlik bilgisi gereklidir.</span><span class="sxs-lookup"><span data-stu-id="8060f-132">If the `Group` resource adds a domain account to the local group, then a credential is necessary.</span></span>

<span data-ttu-id="8060f-133">Active Directory anonim sorgulara izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="8060f-133">Anonymous queries to Active Directory are not allowed.</span></span>
<span data-ttu-id="8060f-134">`Credential` Özelliği `Group` kullanılan sorgu için Active Directory etki alanı hesabı bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="8060f-134">The `Credential` property of the `Group` resource is the domain account used to query Active Directory.</span></span>
<span data-ttu-id="8060f-135">Birçok amaç için bunun nedeni, varsayılan olarak, kullanıcıların yükleyebileceği bir genel kullanıcı hesabı olabilir *okuma* Active Directory içindeki nesneleri çoğu.</span><span class="sxs-lookup"><span data-stu-id="8060f-135">For most purposes this could be a generic user account, because by default users can *read* most of the objects in Active Directory.</span></span>

## <a name="example-configuration"></a><span data-ttu-id="8060f-136">Örnek yapılandırma</span><span class="sxs-lookup"><span data-stu-id="8060f-136">Example Configuration</span></span>

<span data-ttu-id="8060f-137">Aşağıdaki kod örneği, bir yerel Grup bir etki alanı kullanıcısı ile doldurmak için DSC kullanır:</span><span class="sxs-lookup"><span data-stu-id="8060f-137">The following example code uses DSC to populate a local group with a domain user:</span></span>

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

<span data-ttu-id="8060f-138">Bu kod, bir hata ve uyarı iletisi oluşturur:</span><span class="sxs-lookup"><span data-stu-id="8060f-138">This code generates both an error and warning message:</span></span>

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

<span data-ttu-id="8060f-139">Bu örnekte, iki sorun vardır:</span><span class="sxs-lookup"><span data-stu-id="8060f-139">This example has two issues:</span></span>

1. <span data-ttu-id="8060f-140">Bir hata düz metin parolalar önerilmez açıklar.</span><span class="sxs-lookup"><span data-stu-id="8060f-140">An error explains that plain text passwords are not recommended</span></span>
2. <span data-ttu-id="8060f-141">Bir uyarı bir etki alanı kimlik bilgisi kullanılmamasını önerir.</span><span class="sxs-lookup"><span data-stu-id="8060f-141">A warning advises against using a domain credential</span></span>

<span data-ttu-id="8060f-142">Bayrakları **PSDSCAllowPlainTextPassword** ve **PSDSCAllowDomainUser** hata ve söz konusu riski kullanıcısı bildiren bir uyarı bastırır.</span><span class="sxs-lookup"><span data-stu-id="8060f-142">The flags **PSDSCAllowPlainTextPassword** and **PSDSCAllowDomainUser** suppress the error and warning informing the user of the risk involved.</span></span>

## <a name="psdscallowplaintextpassword"></a><span data-ttu-id="8060f-143">PSDSCAllowPlainTextPassword</span><span class="sxs-lookup"><span data-stu-id="8060f-143">PSDSCAllowPlainTextPassword</span></span>

<span data-ttu-id="8060f-144">İlk hata iletisi, belgeleri bir URL vardır.</span><span class="sxs-lookup"><span data-stu-id="8060f-144">The first error message has a URL with documentation.</span></span>
<span data-ttu-id="8060f-145">Bu bağlantıyı kullanarak parolaları şifrelemek açıklanmaktadır bir [ConfigurationData](./configData.md) yapısı ve bir sertifika.</span><span class="sxs-lookup"><span data-stu-id="8060f-145">This link explains how to encrypt passwords using a [ConfigurationData](./configData.md) structure and a certificate.</span></span>
<span data-ttu-id="8060f-146">Sertifikaları ve DSC hakkında daha fazla bilgi için [Bu gönderiyi okuyun](http://aka.ms/certs4dsc).</span><span class="sxs-lookup"><span data-stu-id="8060f-146">For more information on certificates and DSC [read this post](http://aka.ms/certs4dsc).</span></span>

<span data-ttu-id="8060f-147">Düz metin parola zorlamak için kaynak gerektiren `PsDscAllowPlainTextPassword` yapılandırma verilerini bir anahtar sözcük bölümünde şu şekilde:</span><span class="sxs-lookup"><span data-stu-id="8060f-147">To force a plain text password, the resource requires the `PsDscAllowPlainTextPassword` keyword in the configuration data section as follows:</span></span>

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

### <a name="localhostmof"></a><span data-ttu-id="8060f-148">localhost.mof</span><span class="sxs-lookup"><span data-stu-id="8060f-148">localhost.mof</span></span>

<span data-ttu-id="8060f-149">**PSDSCAllowPlainTextPassword** bayrağı gerektiren kullanıcı MOF dosyasında düz metin parolaların saklanması riskini kabul etme.</span><span class="sxs-lookup"><span data-stu-id="8060f-149">The **PSDSCAllowPlainTextPassword** flag requires that the user acknowledge the risk of storing plain text passwords in a MOF file.</span></span> <span data-ttu-id="8060f-150">Oluşturulan MOF dosyasındaki olsa bile bir **PSCredential** nesne içeren bir **SecureString** kullanılan, parolaları düz metin olarak görünmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="8060f-150">In the generated MOF file, even though a **PSCredential** object containing a **SecureString** was used, the passwords still appear as plain text.</span></span> <span data-ttu-id="8060f-151">Kimlik bilgilerinin ifşa edildiği yalnızca bir kez budur.</span><span class="sxs-lookup"><span data-stu-id="8060f-151">This is the only time the credentials are exposed.</span></span> <span data-ttu-id="8060f-152">Herkes yönetici hesabına bu MOF dosyası erişmenizi erişmesini.</span><span class="sxs-lookup"><span data-stu-id="8060f-152">Gaining access to this MOF file gives anyone access to the Administrator account.</span></span>

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

### <a name="credentials-in-transit-and-at-rest"></a><span data-ttu-id="8060f-153">Aktarımda ve bekleme sırasında kimlik bilgileri</span><span class="sxs-lookup"><span data-stu-id="8060f-153">Credentials in transit and at rest</span></span>

- <span data-ttu-id="8060f-154">**PSDscAllowPlainTextPassword** bayrağı, düz metin parolalar içeren MOF dosyaları derlenmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="8060f-154">The **PSDscAllowPlainTextPassword** flag allows the compilation of MOF files that contain passwords in clear text.</span></span>
  <span data-ttu-id="8060f-155">Düz metin parolalar içeren MOF dosyaları depolarken önlemleri alın.</span><span class="sxs-lookup"><span data-stu-id="8060f-155">Take precautions when storing MOF files containing clear text passwords.</span></span>
- <span data-ttu-id="8060f-156">Ne zaman MOF dosyasını girmediklerinden bir düğüme **anında iletme** modu, WinRM şifreler varsayılan yazmadığınız sürece düz metin parolası korumak için iletişim **AllowUnencrypted** parametresi.</span><span class="sxs-lookup"><span data-stu-id="8060f-156">When the MOF file is delivered to a Node in **Push** mode, WinRM encrypts the communication to protect the clear text password unless you override the default with the **AllowUnencrypted** parameter.</span></span>
  - <span data-ttu-id="8060f-157">Bir sertifika ile MOF şifreleme, bir düğüme uygulanan önce bekleyen MOF dosyasını korur.</span><span class="sxs-lookup"><span data-stu-id="8060f-157">Encrypting the MOF with a certificate protects the MOF file at rest before it has been applied to a node.</span></span>
- <span data-ttu-id="8060f-158">İçinde **çekme** modu, Internet Information Server'ın belirtilen protokolünü kullanarak trafiği şifrelemek için HTTPS kullanmak üzere Windows çekme sunucusu yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8060f-158">In **Pull** mode, you can configure Windows pull server to use HTTPS to encrypt traffic using the protocol specified in Internet Information Server.</span></span> <span data-ttu-id="8060f-159">Daha fazla bilgi için makalelere bakın [DSC çekme istemcisi ayarlama](../pull-server/pullclient.md) ve [sertifikalar ile güvenli hale getirme MOF dosyaları](../pull-server/secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="8060f-159">For more information, see the articles [Setting up a DSC pull client](../pull-server/pullclient.md) and [Securing MOF files with Certificates](../pull-server/secureMOF.md).</span></span>
  - <span data-ttu-id="8060f-160">İçinde [Azure Otomasyon durum Yapılandırması](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview) hizmeti, çekme trafik her zaman şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="8060f-160">In the [Azure Automation State Configuration](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview) service, Pull traffic is always encrypted.</span></span>
- <span data-ttu-id="8060f-161">Düğümde, MOF dosyaları bekleme sırasında şifrelenir PowerShell 5. 0'den itibaren.</span><span class="sxs-lookup"><span data-stu-id="8060f-161">On the Node, MOF files are encrypted at rest Beginning in PowerShell 5.0.</span></span>
  - <span data-ttu-id="8060f-162">Gönderilen veya düğüme çekilen bir sertifika ile şifrelenir sürece içinde PowerShell 4.0 MOF dosyaları bekleme sırasında şifrelenmemiş olarak.</span><span class="sxs-lookup"><span data-stu-id="8060f-162">In PowerShell 4.0 MOF files are unencrypted at rest unless they are encrypted with a certificate when they pushed or pulled to the Node.</span></span>

<span data-ttu-id="8060f-163">**Önemli güvenlik riski nedeniyle düz metin parolalar önlemek için Microsoft önerir.**</span><span class="sxs-lookup"><span data-stu-id="8060f-163">**Microsoft advises to avoid plain text passwords due to the significant security risk.**</span></span>

## <a name="domain-credentials"></a><span data-ttu-id="8060f-164">Etki alanı kimlik bilgileri</span><span class="sxs-lookup"><span data-stu-id="8060f-164">Domain Credentials</span></span>

<span data-ttu-id="8060f-165">(İle veya şifreleme olmadan), yeniden örnekte yapılandırma betiği çalıştıran bir etki alanı kullanarak bir kimlik bilgisi hesabı önerilmez uyarı hala oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8060f-165">Running the example configuration script again (with or without encryption), still generates the warning that using a domain account for a credential is not recommended.</span></span>
<span data-ttu-id="8060f-166">Yerel bir hesap kullanarak, diğer tüm sunucularda kullanılabilir etki alanı kimlik bilgilerini olası riskini ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="8060f-166">Using a local account eliminates potential exposure of domain credentials that could be used on other servers.</span></span>

<span data-ttu-id="8060f-167">**DSC kaynakları ile kimlik bilgilerini kullanarak, yerel bir hesap bir etki alanı hesabı mümkün olduğunda tercih edin.**</span><span class="sxs-lookup"><span data-stu-id="8060f-167">**When using credentials with DSC resources, prefer a local account over a domain account when possible.**</span></span>

<span data-ttu-id="8060f-168">Varsa bir '\\'veya'\@' nda `Username` özelliği kimlik bilgisi, daha sonra DSC işlemek, bir etki alanı hesabı olarak.</span><span class="sxs-lookup"><span data-stu-id="8060f-168">If there is a '\\' or '\@' in the `Username` property of the credential, then DSC will treat it as a domain account.</span></span>
<span data-ttu-id="8060f-169">Bir özel durum için "localhost", "127.0.0.1" ve ":: 1" kullanıcı adının etki alanı bölümü içinde.</span><span class="sxs-lookup"><span data-stu-id="8060f-169">There is an exception for "localhost", "127.0.0.1", and "::1" in the domain portion of the user name.</span></span>

## <a name="psdscallowdomainuser"></a><span data-ttu-id="8060f-170">PSDscAllowDomainUser</span><span class="sxs-lookup"><span data-stu-id="8060f-170">PSDscAllowDomainUser</span></span>

<span data-ttu-id="8060f-171">DSC, `Group` yukarıda bir Active Directory etki alanı sorgulanıyor kaynak örnek *gerektirir* bir etki alanı hesabı.</span><span class="sxs-lookup"><span data-stu-id="8060f-171">In the DSC `Group` resource example above, querying an Active Directory domain *requires* a domain account.</span></span>
<span data-ttu-id="8060f-172">Bu durumda ekleme `PSDscAllowDomainUser` özelliğini `ConfigurationData` bloğunu şu şekilde:</span><span class="sxs-lookup"><span data-stu-id="8060f-172">In this case add the `PSDscAllowDomainUser` property to the `ConfigurationData` block as follows:</span></span>

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

<span data-ttu-id="8060f-173">Artık yapılandırma betiği ile bir hata veya uyarı MOF dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8060f-173">Now the configuration script will generate the MOF file with no errors or warnings.</span></span>
