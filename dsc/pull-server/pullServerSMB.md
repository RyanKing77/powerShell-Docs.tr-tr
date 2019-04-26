---
ms.date: 04/11/2018
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC SMB çekme sunucusu ayarlama
ms.openlocfilehash: 9d087a08861b2f4683e81efd1e25f857b8b75e07
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079294"
---
# <a name="setting-up-a-dsc-smb-pull-server"></a><span data-ttu-id="8ef8e-103">DSC SMB çekme sunucusu ayarlama</span><span class="sxs-lookup"><span data-stu-id="8ef8e-103">Setting up a DSC SMB pull server</span></span>

<span data-ttu-id="8ef8e-104">Uygulama hedefi: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="8ef8e-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8ef8e-105">Çekme sunucusu (Windows özelliği *DSC hizmet*) ancak desteklenen bir bileşen Windows Server'ın yeni özellikler veya yetenekler sunmak için herhangi bir plan vardır.</span><span class="sxs-lookup"><span data-stu-id="8ef8e-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="8ef8e-106">Geçişi başlıyor önerilir yönetilen istemcilere [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (Windows Server çekme sunucusunda dışında özellikler dahildir) veya topluluk çözümlerden birini listelenen [burada](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="8ef8e-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="8ef8e-107">Bir DSC [SMB](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831795(v=ws.11)) çekme sunucusu, bu düğümler için isteyin, DSC yapılandırma dosyalarını ve DSC kaynakları hedef düğümler için kullanılabilir hale getiren bir SMB dosya paylaşımları barındıran bir bilgisayardır.</span><span class="sxs-lookup"><span data-stu-id="8ef8e-107">A DSC [SMB](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831795(v=ws.11)) pull server is a computer hosting SMB file shares that make DSC configuration files and DSC resources available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="8ef8e-108">İçin DSC SMB çekme sunucusu kullanmak için için gerekenler:</span><span class="sxs-lookup"><span data-stu-id="8ef8e-108">To use an SMB pull server for DSC, you have to:</span></span>

- <span data-ttu-id="8ef8e-109">PowerShell 4.0 veya üzerini çalıştıran bir sunucuda bir SMB dosya paylaşımı ayarlama</span><span class="sxs-lookup"><span data-stu-id="8ef8e-109">Set up an SMB file share on a server running PowerShell 4.0 or higher</span></span>
- <span data-ttu-id="8ef8e-110">Bu SMB paylaşımından çekmek için PowerShell 4.0 veya sonraki sürümlerini çalıştıran istemci yapılandırma</span><span class="sxs-lookup"><span data-stu-id="8ef8e-110">Configure a client running PowerShell 4.0 or higher to pull from that SMB share</span></span>

## <a name="using-the-xsmbshare-resource-to-create-an-smb-file-share"></a><span data-ttu-id="8ef8e-111">Bir SMB dosya paylaşımı oluşturmak için xSmbShare kaynak'ı kullanma</span><span class="sxs-lookup"><span data-stu-id="8ef8e-111">Using the xSmbShare resource to create an SMB file share</span></span>

<span data-ttu-id="8ef8e-112">Bir SMB dosya paylaşımı ayarlama, ancak bakalım nasıl DSC kullanarak bunu yapabilirsiniz çeşitli yollarla vardır.</span><span class="sxs-lookup"><span data-stu-id="8ef8e-112">There are a number of ways to set up an SMB file share, but let's look at how you can do this by using DSC.</span></span>

### <a name="install-the-xsmbshare-resource"></a><span data-ttu-id="8ef8e-113">XSmbShare kaynak yükleyin</span><span class="sxs-lookup"><span data-stu-id="8ef8e-113">Install the xSmbShare resource</span></span>

<span data-ttu-id="8ef8e-114">Çağrı [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet'ine **xSmbShare** modülü.</span><span class="sxs-lookup"><span data-stu-id="8ef8e-114">Call the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to install the **xSmbShare** module.</span></span>

> [!NOTE]
> <span data-ttu-id="8ef8e-115">`Install-Module` yer aldığı **PowerShellGet** modülü, PowerShell 5. 0'da dahildir.</span><span class="sxs-lookup"><span data-stu-id="8ef8e-115">`Install-Module` is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="8ef8e-116">İndirebileceğiniz **PowerShellGet** modülü PowerShell 3.0 ve 4.0, [PackageManagement PowerShell modülleri Önizleme](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span><span class="sxs-lookup"><span data-stu-id="8ef8e-116">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span>
> <span data-ttu-id="8ef8e-117">**XSmbShare** DSC kaynağı içeren **xSmbShare**, SMB dosya paylaşımı oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8ef8e-117">The **xSmbShare** contains the DSC resource **xSmbShare**, which can be used to create an SMB file share.</span></span>

### <a name="create-the-directory-and-file-share"></a><span data-ttu-id="8ef8e-118">Dizin ve dosya paylaşımı oluşturma</span><span class="sxs-lookup"><span data-stu-id="8ef8e-118">Create the directory and file share</span></span>

<span data-ttu-id="8ef8e-119">Aşağıdaki yapılandırmayı kullanır **dosya** paylaşımı için bir dizin oluşturmak için kaynak ve **xSmbShare** SMB Paylaşımı'kurmak için kaynak:</span><span class="sxs-lookup"><span data-stu-id="8ef8e-119">The following configuration uses the **File** resource to create the directory for the share and the **xSmbShare** resource to set up the SMB share:</span></span>

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

<span data-ttu-id="8ef8e-120">Yapılandırma dizini `C:\DscSmbShare`, zaten mevcut değil ve daha sonra bu dizine bir SMB dosya paylaşımı kullanır.</span><span class="sxs-lookup"><span data-stu-id="8ef8e-120">The configuration creates the directory `C:\DscSmbShare`, if it doesn't already exist, and then uses that directory as an SMB file share.</span></span> <span data-ttu-id="8ef8e-121">**FullAccess** yazmak veya dosya paylaşımından silmek için gereken herhangi bir hesaba verilmelidir.</span><span class="sxs-lookup"><span data-stu-id="8ef8e-121">**FullAccess** should be given to any account that needs to write to or delete from the file share.</span></span> <span data-ttu-id="8ef8e-122">**Okuma erişimi** yapılandırmaları ve/veya DSC kaynakları paylaşımından hale herhangi bir istemci düğümlere verilmelidir.</span><span class="sxs-lookup"><span data-stu-id="8ef8e-122">**ReadAccess** must be given to any client nodes that get configurations and/or DSC resources from the share.</span></span>

> [!NOTE]
> <span data-ttu-id="8ef8e-123">DSC, sistem hesabı olarak varsayılan olarak çalışır, böylece bilgisayar paylaşımına erişimi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8ef8e-123">DSC runs as the system account by default, so the computer itself must have access to the share.</span></span>

### <a name="give-file-system-access-to-the-pull-client"></a><span data-ttu-id="8ef8e-124">Çekme istemcisi için dosya sistemi erişimi verin</span><span class="sxs-lookup"><span data-stu-id="8ef8e-124">Give file system access to the pull client</span></span>

<span data-ttu-id="8ef8e-125">Verme **okuma erişimi** istemciye düğümü, SMB paylaşımı erişecek ancak dosyaları veya klasörleri içindeki paylaşmak için bu düğümü sağlar.</span><span class="sxs-lookup"><span data-stu-id="8ef8e-125">Giving **ReadAccess** to a client node allows that node to access the SMB share, but not to files or folders within that share.</span></span> <span data-ttu-id="8ef8e-126">Açıkça istemci SMB paylaşımı klasörü ve alt düğümleri erişim izni gerekir.</span><span class="sxs-lookup"><span data-stu-id="8ef8e-126">You have to explicitly grant client nodes access to the SMB share folder and subfolders.</span></span> <span data-ttu-id="8ef8e-127">Bu DSC ile kullanarak ekleyerek yapabiliriz **cNtfsPermissionEntry** bulunan kaynak [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0) modülü.</span><span class="sxs-lookup"><span data-stu-id="8ef8e-127">We can do this with DSC by adding using the **cNtfsPermissionEntry** resource, which is contained in the [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0) module.</span></span> <span data-ttu-id="8ef8e-128">Aşağıdaki yapılandırmayı ekler bir **cNtfsPermissionEntry** çekme istemciye ReadAndExecute erişim veren engelle:</span><span class="sxs-lookup"><span data-stu-id="8ef8e-128">The following configuration adds a **cNtfsPermissionEntry** block that grants ReadAndExecute access to the pull client:</span></span>

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

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="8ef8e-129">Yapılandırmaları ve kaynakları yerleştirme</span><span class="sxs-lookup"><span data-stu-id="8ef8e-129">Placing configurations and resources</span></span>

<span data-ttu-id="8ef8e-130">Herhangi bir yapılandırma MOF dosyaları ve/veya istemci düğümleri SMB paylaşımı klasöründe çekmek için istediğiniz DSC kaynakları kaydedin.</span><span class="sxs-lookup"><span data-stu-id="8ef8e-130">Save any configuration MOF files and/or DSC resources that you want client nodes to pull in the SMB share folder.</span></span>

<span data-ttu-id="8ef8e-131">Tüm yapılandırma MOF dosyasının adlandırılmalıdır *ConfigurationID*.mof, burada *ConfigurationID* değeri **ConfigurationID** hedef düğümün LCM özelliği.</span><span class="sxs-lookup"><span data-stu-id="8ef8e-131">Any configuration MOF file must be named *ConfigurationID*.mof, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span> <span data-ttu-id="8ef8e-132">Çekme istemciler ayarlama hakkında daha fazla bilgi için bkz. [yapılandırma Kimliğini kullanarak çekme istemcisi ayarlama](pullClientConfigID.md).</span><span class="sxs-lookup"><span data-stu-id="8ef8e-132">For more information about setting up pull clients, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

> [!NOTE]
> <span data-ttu-id="8ef8e-133">Bir SMB çekme sunucusu kullanıyorsanız, yapılandırma kimliklerinin kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8ef8e-133">You must use configuration IDs if you are using an SMB pull server.</span></span> <span data-ttu-id="8ef8e-134">Yapılandırma adları, SMB için desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="8ef8e-134">Configuration names are not supported for SMB.</span></span>

<span data-ttu-id="8ef8e-135">Her kaynak modülü sıkıştırılmasını ve aşağıdaki modele göre adında gereken `{Module Name}_{Module Version}.zip`.</span><span class="sxs-lookup"><span data-stu-id="8ef8e-135">Each resource module needs to be zipped and named according to the following pattern `{Module Name}_{Module Version}.zip`.</span></span> <span data-ttu-id="8ef8e-136">Örneğin, xWebAdminstration 3.1.2.0 modülü sürümü ile adlı bir modül 'xWebAdministration_3.2.1.0.zip' adlı.</span><span class="sxs-lookup"><span data-stu-id="8ef8e-136">For example, a module named xWebAdminstration with a module version of 3.1.2.0 would be named 'xWebAdministration_3.2.1.0.zip'.</span></span> <span data-ttu-id="8ef8e-137">Her bir modül sürümü tek zip dosyasında yer almalıdır.</span><span class="sxs-lookup"><span data-stu-id="8ef8e-137">Each version of a module must be contained in a single zip file.</span></span> <span data-ttu-id="8ef8e-138">Modül zip dosyası içinde ayrı sürümleri desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="8ef8e-138">Separate versions of a module in a zip file are not supported.</span></span> <span data-ttu-id="8ef8e-139">DSC çekme server ile kullanmak için kaynak modülleri'kurmak paketleme önce dizin yapısı için küçük bir değişiklik yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8ef8e-139">Before packaging up DSC resource modules for use with pull server, you need to make a small change to the directory structure.</span></span>

<span data-ttu-id="8ef8e-140">WMF 5.0 DSC kaynağı içeren modüllerin varsayılan biçimi `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.</span><span class="sxs-lookup"><span data-stu-id="8ef8e-140">The default format of modules containing DSC resource in WMF 5.0 is `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.</span></span>

<span data-ttu-id="8ef8e-141">Çekme sunucusu için paketleme önce kaldırmanız `{Module version}` klasör yolu olacak şekilde `{Module Folder}\DscResources\{DSC Resource Folder}\`.</span><span class="sxs-lookup"><span data-stu-id="8ef8e-141">Before packaging up for the pull server simply remove the `{Module version}` folder so the path becomes `{Module Folder}\DscResources\{DSC Resource Folder}\`.</span></span> <span data-ttu-id="8ef8e-142">Bu değişiklik, yukarıda açıklandığı gibi klasör zip ve bu zip dosyaları SMB paylaşımı klasörüne yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="8ef8e-142">With this change, zip the folder as described above and place these zip files in the SMB share folder.</span></span>

## <a name="creating-the-mof-checksum"></a><span data-ttu-id="8ef8e-143">MOF sağlama toplamı oluşturma</span><span class="sxs-lookup"><span data-stu-id="8ef8e-143">Creating the MOF checksum</span></span>

<span data-ttu-id="8ef8e-144">Yapılandırma MOF dosyasının yapılandırmasını hedef düğümde bir LCM doğrulayabilmesi bir sağlama toplamı dosyasına ile eşleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="8ef8e-144">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span>
<span data-ttu-id="8ef8e-145">Bir sağlama toplamı oluşturmak için arama [yeni DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="8ef8e-145">To create a checksum, call the [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet.</span></span> <span data-ttu-id="8ef8e-146">Cmdlet alır bir `Path` parametresi yapılandırma MOF bulunduğu klasörü belirtir.</span><span class="sxs-lookup"><span data-stu-id="8ef8e-146">The cmdlet takes a `Path` parameter that specifies the folder where the configuration MOF is located.</span></span> <span data-ttu-id="8ef8e-147">Adlı bir sağlama toplamı dosyasına cmdlet oluşturur `ConfigurationMOFName.mof.checksum`burada `ConfigurationMOFName` yapılandırma mof dosyasının adıdır.</span><span class="sxs-lookup"><span data-stu-id="8ef8e-147">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span>
<span data-ttu-id="8ef8e-148">Belirtilen klasörde MOF dosyaları birden fazla yapılandırması varsa, klasördeki her bir yapılandırma için bir sağlama toplamı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="8ef8e-148">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span>

<span data-ttu-id="8ef8e-149">Sağlama toplamı dosyasına yapılandırma MOF dosyasının aynı dizinde bulunmalıdır (`$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration` varsayılan olarak), ve aynı ada sahip `.checksum` uzantısı eklenmiş.</span><span class="sxs-lookup"><span data-stu-id="8ef8e-149">The checksum file must be present in the same directory as the configuration MOF file (`$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration` by default), and have the same name with the `.checksum` extension appended.</span></span>

> [!NOTE]
> <span data-ttu-id="8ef8e-150">Yapılandırma MOF dosyasının herhangi bir şekilde değiştirirseniz, sağlama toplamı dosyasına yeniden oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8ef8e-150">If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

## <a name="setting-up-a-pull-client-for-smb"></a><span data-ttu-id="8ef8e-151">SMB için çekme istemcisi ayarlama</span><span class="sxs-lookup"><span data-stu-id="8ef8e-151">Setting up a pull client for SMB</span></span>

<span data-ttu-id="8ef8e-152">Bir istemci yapılandırmaları ve/veya bir SMB paylaşımından kaynaklar çeker ayarlamak için ile istemcinin yerel Configuration Manager (LCM) yapılandırma **ConfigurationRepositoryShare** ve **ResourceRepositoryShare** blokları yapılandırmaları ve DSC kaynakları çekmek paylaşımını belirtin.</span><span class="sxs-lookup"><span data-stu-id="8ef8e-152">To set up a client that pulls configurations and/or resources from an SMB share, you configure the client's Local Configuration Manager (LCM) with **ConfigurationRepositoryShare** and **ResourceRepositoryShare** blocks that specify the share from which to pull configurations and DSC resources.</span></span>

<span data-ttu-id="8ef8e-153">LCM yapılandırma hakkında daha fazla bilgi için bkz. [yapılandırma Kimliğini kullanarak çekme istemcisi ayarlama](pullClientConfigID.md).</span><span class="sxs-lookup"><span data-stu-id="8ef8e-153">For more information about configuring the LCM, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

> [!NOTE]
> <span data-ttu-id="8ef8e-154">Kolaylık olması için bu örnekte **PSDscAllowPlainTextPassword** bir düz metin parolayı geçirme izin vermek için **kimlik bilgisi** parametresi.</span><span class="sxs-lookup"><span data-stu-id="8ef8e-154">For simplicity, this example uses the **PSDscAllowPlainTextPassword** to allow passing a plaintext password to the **Credential** parameter.</span></span> <span data-ttu-id="8ef8e-155">Kimlik bilgileri daha güvenli bir şekilde geçirme hakkında daha fazla bilgi için bkz: [yapılandırma verilerinde kimlik bilgisi seçeneklerinden](../configurations/configDataCredentials.md).</span><span class="sxs-lookup"><span data-stu-id="8ef8e-155">For information about passing credentials more securely, see [Credentials Options in Configuration Data](../configurations/configDataCredentials.md).</span></span>
>
> <span data-ttu-id="8ef8e-156">**Gerekir** belirtin bir **ConfigurationID** içinde **ayarları** kaynakları yalnızca çeken olsa bile bir SMB çekme sunucusu, bir metaconfiguration bloğu.</span><span class="sxs-lookup"><span data-stu-id="8ef8e-156">You **MUST** specify a **ConfigurationID** in the **Settings** block of a metaconfiguration for an SMB pull server, even if you are only pulling resources.</span></span>

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

## <a name="acknowledgements"></a><span data-ttu-id="8ef8e-157">Bildirimler</span><span class="sxs-lookup"><span data-stu-id="8ef8e-157">Acknowledgements</span></span>

<span data-ttu-id="8ef8e-158">Özel sayesinde aşağıdaki kişiler:</span><span class="sxs-lookup"><span data-stu-id="8ef8e-158">Special thanks to the following individuals:</span></span>

- <span data-ttu-id="8ef8e-159">Bu konudaki içeriğin bildirmek için DSC SMB kullanarak, gönderiler Yardım Mike F. Robbins.</span><span class="sxs-lookup"><span data-stu-id="8ef8e-159">Mike F. Robbins, whose posts on using SMB for DSC helped inform the content in this topic.</span></span> <span data-ttu-id="8ef8e-160">Blog altındadır [Mike F Robbins](http://mikefrobbins.com/).</span><span class="sxs-lookup"><span data-stu-id="8ef8e-160">His blog is at [Mike F Robbins](http://mikefrobbins.com/).</span></span>
- <span data-ttu-id="8ef8e-161">Kimin yazılan serge Nikalaichyk **cNtfsAccessControl** modülü.</span><span class="sxs-lookup"><span data-stu-id="8ef8e-161">Serge Nikalaichyk, who authored the **cNtfsAccessControl** module.</span></span> <span data-ttu-id="8ef8e-162">Bu modülü için kaynak altındadır [cNtfsAccessControl](https://github.com/SNikalaichyk/cNtfsAccessControl).</span><span class="sxs-lookup"><span data-stu-id="8ef8e-162">The source for this module is at [cNtfsAccessControl](https://github.com/SNikalaichyk/cNtfsAccessControl).</span></span>

## <a name="see-also"></a><span data-ttu-id="8ef8e-163">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8ef8e-163">See also</span></span>

[<span data-ttu-id="8ef8e-164">Windows PowerShell Desired State Configuration ' ne genel bakış</span><span class="sxs-lookup"><span data-stu-id="8ef8e-164">Windows PowerShell Desired State Configuration Overview</span></span>](../overview/overview.md)

[<span data-ttu-id="8ef8e-165">Yapılandırmaları Kabul Etme</span><span class="sxs-lookup"><span data-stu-id="8ef8e-165">Enacting configurations</span></span>](enactingConfigurations.md)

[<span data-ttu-id="8ef8e-166">Yapılandırma kimliğini kullanarak çekme istemcisi ayarlama</span><span class="sxs-lookup"><span data-stu-id="8ef8e-166">Setting up a pull client using configuration ID</span></span>](pullClientConfigID.md)
