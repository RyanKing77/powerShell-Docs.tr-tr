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
# <a name="setting-up-a-dsc-smb-pull-server"></a><span data-ttu-id="a57ec-103">DSC SMB çekme sunucusu ayarlama</span><span class="sxs-lookup"><span data-stu-id="a57ec-103">Setting up a DSC SMB pull server</span></span>

><span data-ttu-id="a57ec-104">İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="a57ec-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a57ec-105">Çekme sunucusuna (Windows özelliği *DSC hizmet*) vardır ancak desteklenen bir bileşen Windows Server'ın yeni özellikleri veya yetenekleri sunmak için herhangi bir plan vardır.</span><span class="sxs-lookup"><span data-stu-id="a57ec-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="a57ec-106">Geçiş başlamak için önerilen yönetilen istemcilere [Azure Otomasyonu DSC](/azure/automation/automation-dsc-getting-started) (Windows Server çekme sunucusunda ötesinde özellikler içerir) veya topluluk çözümlerden birini listelenen [burada](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="a57ec-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="a57ec-107">Bir DSC [SMB](https://technet.microsoft.com/library/hh831795.aspx) çekme sunucu, bu düğümler için söylediğinizde DSC yapılandırma dosyalarını ve DSC kaynakları, hedef düğümleri kullanılabilmesini SMB dosya paylaşımlarını barındıran bir bilgisayardır.</span><span class="sxs-lookup"><span data-stu-id="a57ec-107">A DSC [SMB](https://technet.microsoft.com/library/hh831795.aspx) pull server is a computer hosting SMB file shares that make DSC configuration files and DSC resources available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="a57ec-108">DSC için bir SMB çekme sunucusunu kullanmak üzere için gerekenler:</span><span class="sxs-lookup"><span data-stu-id="a57ec-108">To use an SMB pull server for DSC, you have to:</span></span>
- <span data-ttu-id="a57ec-109">PowerShell 4.0 veya üstünü çalıştıran bir sunucuda bir SMB dosya paylaşımı ayarlama</span><span class="sxs-lookup"><span data-stu-id="a57ec-109">Set up an SMB file share on a server running PowerShell 4.0 or higher</span></span>
- <span data-ttu-id="a57ec-110">Bu SMB paylaşımından çıkarmak için PowerShell 4.0 veya sonraki sürümlerini çalıştıran istemci yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a57ec-110">Configure a client running PowerShell 4.0 or higher to pull from that SMB share</span></span>

## <a name="using-the-xsmbshare-resource-to-create-an-smb-file-share"></a><span data-ttu-id="a57ec-111">XSmbShare kaynağı kullanarak bir SMB dosya paylaşımı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="a57ec-111">Using the xSmbShare resource to create an SMB file share</span></span>

<span data-ttu-id="a57ec-112">Bir SMB dosya paylaşımı ayarlama, ancak nasıl DSC kullanarak bunu yapabilirsiniz bakalım yolları vardır.</span><span class="sxs-lookup"><span data-stu-id="a57ec-112">There are a number of ways to set up an SMB file share, but let's look at how you can do this by using DSC.</span></span>

### <a name="install-the-xsmbshare-resource"></a><span data-ttu-id="a57ec-113">XSmbShare kaynak yükleyin</span><span class="sxs-lookup"><span data-stu-id="a57ec-113">Install the xSmbShare resource</span></span>

<span data-ttu-id="a57ec-114">Çağrı [yükleme-Module](https://technet.microsoft.com/library/dn807162.aspx) yüklemek için cmdlet'i **xSmbShare** modülü.</span><span class="sxs-lookup"><span data-stu-id="a57ec-114">Call the [Install-Module](https://technet.microsoft.com/library/dn807162.aspx) cmdlet to install the **xSmbShare** module.</span></span>
><span data-ttu-id="a57ec-115">**Not**: **yükleme-Module** dahil **PowerShellGet** PowerShell 5. 0 ' dahil modülü.</span><span class="sxs-lookup"><span data-stu-id="a57ec-115">**Note**: **Install-Module** is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="a57ec-116">İndirebilirsiniz **PowerShellGet** için modülü PowerShell 3.0 ve 4.0 en [PackageManagement PowerShell modülleri Önizleme](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span><span class="sxs-lookup"><span data-stu-id="a57ec-116">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span> <span data-ttu-id="a57ec-117">**XSmbShare** DSC kaynağı içeren **xSmbShare**, bir SMB dosya paylaşımı oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a57ec-117">The **xSmbShare** contains the DSC resource **xSmbShare**, which can be used to create an SMB file share.</span></span>

### <a name="create-the-directory-and-file-share"></a><span data-ttu-id="a57ec-118">Dizin ve dosya paylaşımı oluşturma</span><span class="sxs-lookup"><span data-stu-id="a57ec-118">Create the directory and file share</span></span>

<span data-ttu-id="a57ec-119">Aşağıdaki yapılandırmayı kullanan [dosya](fileResource.md) paylaşımı dizinini oluşturmak için kaynak ve **xSmbShare** SMB Paylaşımı kurmak için kaynak:</span><span class="sxs-lookup"><span data-stu-id="a57ec-119">The following configuration uses the [File](fileResource.md) resource to create the directory for the share and the **xSmbShare** resource to set up the SMB share:</span></span>

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

<span data-ttu-id="a57ec-120">Yapılandırma dizini `C:\DscSmbShare` zaten seçili değilse var ve daha sonra bu dizine bir SMB dosya paylaşımı kullanır.</span><span class="sxs-lookup"><span data-stu-id="a57ec-120">The configuration creates the directory `C:\DscSmbShare` if it doesn't already exists, and then uses that directory as an SMB file share.</span></span> <span data-ttu-id="a57ec-121">**FullAccess** yazmak veya dosya paylaşımından silmek için gereken herhangi bir hesabı verilecek ve **okuma erişimi** yapılandırmaları ve/veya DSC kaynakları (Bunun nedeni paylaşımından alma tüm istemci düğümlere verilmelidir Bilgisayar paylaşımına erişim iznine sahip olması gerekir DSC sistem hesabı olarak varsayılan olarak çalışır, böylece).</span><span class="sxs-lookup"><span data-stu-id="a57ec-121">**FullAccess** should be given to any account that needs to write to or delete from the file share, and **ReadAccess** must be given to any client nodes that get configurations and/or DSC resources from the share ( this is because DSC runs as the system account by default, so the computer itself has to have access to the share).</span></span>


### <a name="give-file-system-access-to-the-pull-client"></a><span data-ttu-id="a57ec-122">Çekme istemciye dosya sistemi erişimi verin</span><span class="sxs-lookup"><span data-stu-id="a57ec-122">Give file system access to the pull client</span></span>

<span data-ttu-id="a57ec-123">Vermiş **okuma erişimi** istemciye düğümü, SMB paylaşımı erişim, ancak dosyalar veya klasörler, içinde paylaşmak için o düğüm sağlar.</span><span class="sxs-lookup"><span data-stu-id="a57ec-123">Giving **ReadAccess** to a client node allows that node to access the SMB share, but not to files or folders within that share.</span></span> <span data-ttu-id="a57ec-124">Açıkça istemci SMB paylaşımı klasörü ve alt klasörler için düğümleri erişim vermeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a57ec-124">You have to explicitly grant client nodes access to the SMB share folder and sub-folders.</span></span> <span data-ttu-id="a57ec-125">Bu DSC ile kullanarak ekleyerek yapabiliriz **cNtfsPermissionEntry** bulunan kaynak [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0) modülü.</span><span class="sxs-lookup"><span data-stu-id="a57ec-125">We can do this with DSC by adding using the **cNtfsPermissionEntry** resource, which is contained in the [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0) module.</span></span> <span data-ttu-id="a57ec-126">Aşağıdaki yapılandırma ekler bir **cNtfsPermissionEntry** çekme istemciye ReadAndExecute erişim verir engelle:</span><span class="sxs-lookup"><span data-stu-id="a57ec-126">The following configuration adds a **cNtfsPermissionEntry** block that grants ReadAndExecute access to the pull client:</span></span>

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

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="a57ec-127">Yapılandırmaları ve kaynakları yerleştirme</span><span class="sxs-lookup"><span data-stu-id="a57ec-127">Placing configurations and resources</span></span>

<span data-ttu-id="a57ec-128">Herhangi bir yapılandırma MOF dosyaları ve/veya istemci düğümleri SMB paylaşımı klasöründe çekmek için istediğiniz DSC kaynakları kaydedin.</span><span class="sxs-lookup"><span data-stu-id="a57ec-128">Save any configuration MOF files and/or DSC resources that you want client nodes to pull in the SMB share folder.</span></span>

<span data-ttu-id="a57ec-129">Tüm yapılandırma MOF dosyası olarak adlandırılmalıdır _ConfigurationID_.mof, burada _ConfigurationID_ değeri **ConfigurationID** hedef düğümün LCM'yi özelliği.</span><span class="sxs-lookup"><span data-stu-id="a57ec-129">Any configuration MOF file must be named _ConfigurationID_.mof, where _ConfigurationID_ is the value of the **ConfigurationID** property of the target node's LCM.</span></span> <span data-ttu-id="a57ec-130">Çekme istemcileri ayarlama hakkında daha fazla bilgi için bkz: [yapılandırma Kimliğini kullanarak bir çekme istemcisi kurarken](pullClientConfigID.md).</span><span class="sxs-lookup"><span data-stu-id="a57ec-130">For more information about setting up pull clients, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

><span data-ttu-id="a57ec-131">**Not:** bir SMB çekme sunucusu kullanıyorsanız, yapılandırma kimlikleri kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a57ec-131">**Note:** You must use configuration IDs if you are using an SMB pull server.</span></span> <span data-ttu-id="a57ec-132">Yapılandırma adları için SMB desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="a57ec-132">Configuration names are not supported for SMB.</span></span>

<span data-ttu-id="a57ec-133">Her kaynak modül sıkıştırılmış ve according adlı gerekiyor şu deseni `{Module Name}_{Module Version}.zip`.</span><span class="sxs-lookup"><span data-stu-id="a57ec-133">Each resource module needs to be zipped and named according the the following pattern `{Module Name}_{Module Version}.zip`.</span></span> <span data-ttu-id="a57ec-134">Örneğin, 3.1.2.0 Modül sürümü xWebAdminstration adlı bir modül 'xWebAdministration_3.2.1.0.zip' adlı.</span><span class="sxs-lookup"><span data-stu-id="a57ec-134">For example, a module named xWebAdminstration with a module version of 3.1.2.0 would be named 'xWebAdministration_3.2.1.0.zip'.</span></span> <span data-ttu-id="a57ec-135">Her bir modül sürümü tek zip dosyasında yer almalıdır.</span><span class="sxs-lookup"><span data-stu-id="a57ec-135">Each version of a module must be contained in a single zip file.</span></span> <span data-ttu-id="a57ec-136">Yalnızca tek bir sürümünü modül biçimi WMF 5.0 ile eklenen her zip dosyasında bir kaynak olduğundan, tek bir dizin içinde birden çok modül sürümleri için destek desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="a57ec-136">Since there is only a single version of a resource in each zip file the module format added in WMF 5.0 with support for multiple module versions in a single directory is not supported.</span></span> <span data-ttu-id="a57ec-137">Bu paketleme yukarı DSC kaynakları modüllerinin çekme server ile kullanmak için önce dizin yapısını küçük değişiklikler yapmak gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a57ec-137">This means that before packaging up DSC resource modules for use with pull server you need to make a small change to the directory structure.</span></span> <span data-ttu-id="a57ec-138">WMF 5.0 DSC kaynağı içeren modüller varsayılan biçimi ' {modül klasörü}\{Modül sürümü} \DscResources\{DSC kaynak klasörünü}\'.</span><span class="sxs-lookup"><span data-stu-id="a57ec-138">The default format of modules containing DSC resource in WMF 5.0 is '{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\'.</span></span> <span data-ttu-id="a57ec-139">Paketleme çekme sunucu için önce yalnızca kaldırmak **{Modül sürümü}** yolu olacak şekilde klasörü ' {modül klasörü} \DscResources\{DSC kaynak klasörünü}\'.</span><span class="sxs-lookup"><span data-stu-id="a57ec-139">Before packaging up for the pull server simply remove the **{Module version}** folder so the path becomes '{Module Folder}\DscResources\{DSC Resource Folder}\'.</span></span> <span data-ttu-id="a57ec-140">Bu değişiklik, yukarıda açıklandığı gibi klasör zip ve bu ZIP dosyaları SMB paylaşımı klasörüne yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="a57ec-140">With this change, zip the folder as described above and place these zip files in the SMB share folder.</span></span>

## <a name="creating-the-mof-checksum"></a><span data-ttu-id="a57ec-141">MOF sağlama toplamı oluşturma</span><span class="sxs-lookup"><span data-stu-id="a57ec-141">Creating the MOF checksum</span></span>
<span data-ttu-id="a57ec-142">Bir yapılandırma MOF dosyası yapılandırmasını hedef düğümde bir LCM'yi doğrulayabilmesi bir sağlama toplamı dosyasıyla eşleştirilmiş gerekir.</span><span class="sxs-lookup"><span data-stu-id="a57ec-142">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span>
<span data-ttu-id="a57ec-143">Bir sağlama toplamı oluşturmak için arama [yeni DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="a57ec-143">To create a checksum, call the [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx) cmdlet.</span></span> <span data-ttu-id="a57ec-144">Cmdlet geçen bir **yolu** MOF yapılandırma bulunduğu klasörü belirten parametre.</span><span class="sxs-lookup"><span data-stu-id="a57ec-144">The cmdlet takes a **Path** parameter that specifies the folder where the configuration MOF is located.</span></span> <span data-ttu-id="a57ec-145">Cmdlet adlı bir sağlama toplamı dosyası oluşturur `ConfigurationMOFName.mof.checksum`, burada `ConfigurationMOFName` yapılandırma mof dosyasının adıdır.</span><span class="sxs-lookup"><span data-stu-id="a57ec-145">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span>
<span data-ttu-id="a57ec-146">Belirtilen klasörde MOF dosyaları birden fazla yapılandırma varsa, her yapılandırma klasörü için bir sağlama toplamı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a57ec-146">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span>

<span data-ttu-id="a57ec-147">Sağlama toplamı dosya yapılandırma MOF dosyası ile aynı dizinde mevcut olması gerekir (`$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration` varsayılan olarak), ve aynı ada sahip olan `.checksum` uzantısı eklenmiş.</span><span class="sxs-lookup"><span data-stu-id="a57ec-147">The checksum file must be present in the same directory as the configuration MOF file (`$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration` by default), and have the same name with the `.checksum` extension appended.</span></span>

><span data-ttu-id="a57ec-148">**Not**: herhangi bir şekilde yapılandırma MOF dosyasını değiştirirseniz, sağlama toplamı dosyasını da yeniden oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a57ec-148">**Note**: If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

## <a name="setting-up-a-pull-client-for-smb"></a><span data-ttu-id="a57ec-149">Bir çekme istemci SMB için ayarlama</span><span class="sxs-lookup"><span data-stu-id="a57ec-149">Setting up a pull client for SMB</span></span>

<span data-ttu-id="a57ec-150">İle istemcinin yerel Configuration Manager (LCM'yi) yapılandırdığınız yapılandırmaları ve/veya bir SMB paylaşımına kaynaklardan çeken bir istemci ayarlamak için **ConfigurationRepositoryShare** ve **ResourceRepositoryShare** , yapılandırmaları ve DSC kaynakları çekmesini paylaşımından belirtin engeller.</span><span class="sxs-lookup"><span data-stu-id="a57ec-150">To set up a client that pulls configurations and/or resources from an SMB share, you configure the client's Local Configuration Manager (LCM) with **ConfigurationRepositoryShare** and **ResourceRepositoryShare** blocks that specify the share from which to pull configurations and DSC resources.</span></span>

<span data-ttu-id="a57ec-151">LCM'yi yapılandırma hakkında daha fazla bilgi için bkz: [yapılandırma Kimliğini kullanarak bir çekme istemcisi kurarken](pullClientConfigID.md).</span><span class="sxs-lookup"><span data-stu-id="a57ec-151">For more information about configuring the LCM, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

><span data-ttu-id="a57ec-152">**Not:** kolaylık sağlamak için bu örnekte **PSDscAllowPlainTextPassword** bir düz metin parola geçirerek izin vermek için **kimlik bilgisi** parametresi.</span><span class="sxs-lookup"><span data-stu-id="a57ec-152">**Note:** For simplicity, this example uses the **PSDscAllowPlainTextPassword** to allow passing a plaintext password to the **Credential** parameter.</span></span> <span data-ttu-id="a57ec-153">Kimlik bilgileri daha güvenli bir şekilde geçirme hakkında daha fazla bilgi için bkz: [kimlik bilgileri seçenekleri yapılandırma verilerinde](configDataCredentials.md).</span><span class="sxs-lookup"><span data-stu-id="a57ec-153">For information about passing credentials more securely, see [Credentials Options in Configuration Data](configDataCredentials.md).</span></span>

><span data-ttu-id="a57ec-154">**Not:** belirtmeniz gerekir bir **ConfigurationID** içinde **ayarları** bir kaynaklar yalnızca çekme olsa bile SMB çekme sunucusu için bir meta yapılandırmasını bloğu.</span><span class="sxs-lookup"><span data-stu-id="a57ec-154">**Note:** You must specify a **ConfigurationID** in the **Settings** block of a metaconfiguration for an SMB pull server, even if you are only pulling resources.</span></span>

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

## <a name="acknowledgements"></a><span data-ttu-id="a57ec-155">Bildirimler</span><span class="sxs-lookup"><span data-stu-id="a57ec-155">Acknowledgements</span></span>

<span data-ttu-id="a57ec-156">Özel aşağıdaki sayesinde:</span><span class="sxs-lookup"><span data-stu-id="a57ec-156">Special thanks to the following:</span></span>

- <span data-ttu-id="a57ec-157">Bu konudaki içeriğin bildirmek için DSC SMB kullanma, postaları Yardım CAN F'ye Robbins.</span><span class="sxs-lookup"><span data-stu-id="a57ec-157">Mike F. Robbins, whose posts on using SMB for DSC helped inform the content in this topic.</span></span> <span data-ttu-id="a57ec-158">Kendi blogu [CAN F Robbins](http://mikefrobbins.com/).</span><span class="sxs-lookup"><span data-stu-id="a57ec-158">His blog is at [Mike F Robbins](http://mikefrobbins.com/).</span></span>
- <span data-ttu-id="a57ec-159">Kimin yazılan serge Nikalaichyk **cNtfsAccessControl** modülü.</span><span class="sxs-lookup"><span data-stu-id="a57ec-159">Serge Nikalaichyk, who authored the **cNtfsAccessControl** module.</span></span> <span data-ttu-id="a57ec-160">Bu modül için bir kaynak altındadır https://github.com/SNikalaichyk/cNtfsAccessControl.</span><span class="sxs-lookup"><span data-stu-id="a57ec-160">The source for this module is at https://github.com/SNikalaichyk/cNtfsAccessControl.</span></span>

## <a name="see-also"></a><span data-ttu-id="a57ec-161">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="a57ec-161">See also</span></span>
- [<span data-ttu-id="a57ec-162">Windows PowerShell istenen durum yapılandırması genel bakış</span><span class="sxs-lookup"><span data-stu-id="a57ec-162">Windows PowerShell Desired State Configuration Overview</span></span>](overview.md)
- [<span data-ttu-id="a57ec-163">Yapılandırmaları Kabul Etme</span><span class="sxs-lookup"><span data-stu-id="a57ec-163">Enacting configurations</span></span>](enactingConfigurations.md)
- [<span data-ttu-id="a57ec-164">Yapılandırma kimliğini kullanarak çekme istemcisi ayarlama</span><span class="sxs-lookup"><span data-stu-id="a57ec-164">Setting up a pull client using configuration ID</span></span>](pullClientConfigID.md)