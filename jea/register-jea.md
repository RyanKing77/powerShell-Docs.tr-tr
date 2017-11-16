---
ms.date: 2017-06-12
author: rpsqrd
ms.topic: conceptual
keywords: "jea, powershell, güvenlik"
title: "JEA yapılandırmaları kaydetme"
ms.openlocfilehash: 0684a1c7acffbccbedab9dba4689611a24c8ae25
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="registering-jea-configurations"></a><span data-ttu-id="1bdaf-103">JEA yapılandırmaları kaydetme</span><span class="sxs-lookup"><span data-stu-id="1bdaf-103">Registering JEA Configurations</span></span>

> <span data-ttu-id="1bdaf-104">Uygulandığı öğe: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="1bdaf-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="1bdaf-105">Son adım bulduktan sonra JEA kullanmadan önce [rol özellikleri](role-capabilities.md) ve [oturum yapılandırma dosyası](session-configurations.md) JEA uç noktasını kaydetmek için oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="1bdaf-105">The last step before you can use JEA once you have your [role capabilities](role-capabilities.md) and [session configuration file](session-configurations.md) created is to register the JEA endpoint.</span></span>
<span data-ttu-id="1bdaf-106">Bu işlem için sistem oturum yapılandırma bilgilerini uygular ve uç nokta kullanıcıları ve Otomasyon motorları tarafından kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="1bdaf-106">This process applies the session configuration information to the system and makes the endpoint available for use by users and automation engines.</span></span>

## <a name="single-machine-configuration"></a><span data-ttu-id="1bdaf-107">Tek makine yapılandırması</span><span class="sxs-lookup"><span data-stu-id="1bdaf-107">Single machine configuration</span></span>

<span data-ttu-id="1bdaf-108">Küçük ortamlarda oturum yapılandırma dosyası kullanarak kaydederek JEA dağıtabilirsiniz [Register-PSSessionConfiguration](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/register-pssessionconfiguration) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="1bdaf-108">For small environments, you can deploy JEA by registering the session configuration file using the [Register-PSSessionConfiguration](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/register-pssessionconfiguration) cmdlet.</span></span>

<span data-ttu-id="1bdaf-109">Başlamadan önce aşağıdaki önkoşulların karşılandığından emin olun:</span><span class="sxs-lookup"><span data-stu-id="1bdaf-109">Before you begin, ensure that the following prerequisites have been met:</span></span>
- <span data-ttu-id="1bdaf-110">Bir veya daha fazla rol oluşturulur ve geçerli bir PowerShell Modülü 'RoleCapabilities' klasörüne yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="1bdaf-110">One or more roles has been created and placed in the 'RoleCapabilities' folder of a valid PowerShell module.</span></span>
- <span data-ttu-id="1bdaf-111">Bir oturum yapılandırma dosyası oluşturulur ve test.</span><span class="sxs-lookup"><span data-stu-id="1bdaf-111">A session configuration file has been created and tested.</span></span>
- <span data-ttu-id="1bdaf-112">JEA yapılandırması kaydediliyor kullanıcının sistemleri üzerinde yönetici haklarına sahip.</span><span class="sxs-lookup"><span data-stu-id="1bdaf-112">The user registering the JEA configuration has administrator rights on the system(s).</span></span>

<span data-ttu-id="1bdaf-113">JEA uç noktanız için bir ad seçmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="1bdaf-113">You will also need to select a name for your JEA endpoint.</span></span>
<span data-ttu-id="1bdaf-114">Kullanıcıların JEA kullanarak sisteme bağlanmak istediğinizde JEA uç noktanın adı gerekli olacaktır.</span><span class="sxs-lookup"><span data-stu-id="1bdaf-114">The name of the JEA endpoint will be required when users want to connect to the system using JEA.</span></span>
<span data-ttu-id="1bdaf-115">Kullanabileceğiniz [Get-PSSessionConfiguration](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet'ini sistemde mevcut uç nokta adlarını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="1bdaf-115">You can use the [Get-PSSessionConfiguration](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet to check the names of existing endpoints on the system.</span></span>
<span data-ttu-id="1bdaf-116">'Microsoft' ile başlayan uç noktaları genellikle Windows ile birlikte gönderilir.</span><span class="sxs-lookup"><span data-stu-id="1bdaf-116">Endpoints that start with 'microsoft' are typically shipped with Windows.</span></span>
<span data-ttu-id="1bdaf-117">'Microsoft.powershell' uç noktası bir uzak PowerShell bitiş noktasına bağlanırken kullanılan varsayılan uç noktadır.</span><span class="sxs-lookup"><span data-stu-id="1bdaf-117">The 'microsoft.powershell' endpoint is the default endpoint used when connecting to a remote PowerShell endpoint.</span></span>

```powershell
PS C:\> Get-PSSessionConfiguration | Select-Object Name

Name
----
microsoft.powershell
microsoft.powershell.workflow
microsoft.powershell32
```

<span data-ttu-id="1bdaf-118">JEA uç noktanız için uygun bir ad belirlediğinizde uç noktasını kaydetmek için aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1bdaf-118">When you have determined an appropriate name for your JEA endpoint, run the following command to register the endpoint.</span></span>

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="1bdaf-119">Yukarıdaki komut sistem üzerindeki WinRM hizmeti yeniden başlatılır.</span><span class="sxs-lookup"><span data-stu-id="1bdaf-119">The above command will restart the WinRM service on the system.</span></span>
> <span data-ttu-id="1bdaf-120">Bu, devam eden tüm DSC yapılandırmaları yanı sıra tüm PowerShell uzaktan iletişim oturumları sonlandırılacak.</span><span class="sxs-lookup"><span data-stu-id="1bdaf-120">This will terminate all PowerShell remoting sessions as well as any ongoing DSC configurations.</span></span>
> <span data-ttu-id="1bdaf-121">İş işlemlerini kesintiye önlemek için komutu çalıştırmadan önce tüm üretim makinelerinin çevrimdışı olması önerilir.</span><span class="sxs-lookup"><span data-stu-id="1bdaf-121">It is recommended that you take any production machines offline before running the command to avoid disrupting business operations.</span></span>

<span data-ttu-id="1bdaf-122">Kayıt başarılı olursa hazırsınız [JEA kullanmak](using-jea.md).</span><span class="sxs-lookup"><span data-stu-id="1bdaf-122">If registration was successful, you are ready to [use JEA](using-jea.md).</span></span>
<span data-ttu-id="1bdaf-123">Oturum yapılandırma dosyası herhangi bir anda silebilir; kayıttan sonra kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="1bdaf-123">You may delete the session configuration file at any time; it is not used after registration.</span></span>

## <a name="multi-machine-configuration-with-dsc"></a><span data-ttu-id="1bdaf-124">DSC ile çoklu makine yapılandırması</span><span class="sxs-lookup"><span data-stu-id="1bdaf-124">Multi-machine configuration with DSC</span></span>

<span data-ttu-id="1bdaf-125">Birden çok makineye JEA dağıtıyorsanız, basit dağıtım modeli JEA kullanmaktır [istenen durum Yapılandırması](https://msdn.microsoft.com/en-us/powershell/dsc/overview) hızlı ve tutarlı bir şekilde JEA her makine dağıtmak için kaynak.</span><span class="sxs-lookup"><span data-stu-id="1bdaf-125">If you are deploying JEA on multiple machines, the simplest deployment model is to use the JEA [Desired State Configuration](https://msdn.microsoft.com/en-us/powershell/dsc/overview) resource to quickly and consistently deploy JEA on each machine.</span></span>

<span data-ttu-id="1bdaf-126">JEA DSC ile dağıtmak için aşağıdaki önkoşulların karşılandığından emin olmak gerekir:</span><span class="sxs-lookup"><span data-stu-id="1bdaf-126">To deploy JEA with DSC, you will need to ensure the following prerequisites are met:</span></span>
- <span data-ttu-id="1bdaf-127">Bir veya daha fazla rol özellikleri yazılan ve geçerli bir PowerShell modülü eklenir.</span><span class="sxs-lookup"><span data-stu-id="1bdaf-127">One or more role capabilities have been authored and added to a valid PowerShell module.</span></span>
- <span data-ttu-id="1bdaf-128">Rolleri içeren PowerShell Modülü (salt okunur) erişilebilen bir dosya paylaşımı her makine tarafından depolanır.</span><span class="sxs-lookup"><span data-stu-id="1bdaf-128">The PowerShell module containing the roles is stored on a (read-only) file share accessible by each machine.</span></span>
- <span data-ttu-id="1bdaf-129">Oturum yapılandırması ayarlarını belirlediniz.</span><span class="sxs-lookup"><span data-stu-id="1bdaf-129">Settings for the session configuration have been determined.</span></span> <span data-ttu-id="1bdaf-130">JEA DSC kaynağı kullanırken oturum yapılandırma dosyası oluşturmak gerekmez.</span><span class="sxs-lookup"><span data-stu-id="1bdaf-130">You do not need to create a session configuration file when using the JEA DSC resource.</span></span>
- <span data-ttu-id="1bdaf-131">Her makinede yönetici eylemleri gerçekleştirmenize izin veren veya makineleri yönetmek için kullanılan bir DSC çekme sunucusuna erişimi olan kimlik bilgilerine sahip.</span><span class="sxs-lookup"><span data-stu-id="1bdaf-131">You have credentials that will allow you to perform administrative actions on each machine, or have access to a DSC pull server used to manage the machines.</span></span>
- <span data-ttu-id="1bdaf-132">Yüklediğiniz [JEA DSC kaynağı](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource)</span><span class="sxs-lookup"><span data-stu-id="1bdaf-132">You have downloaded the [JEA DSC resource](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource)</span></span>

<span data-ttu-id="1bdaf-133">Bir hedef makine (veya çekme sunucu birini kullanıyorsanız), JEA uç noktanız için bir DSC yapılandırmasını oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1bdaf-133">On a target machine (or pull server, if you are using one), create a DSC configuration for your JEA endpoint.</span></span>
<span data-ttu-id="1bdaf-134">Bu yapılandırmada, oturum yapılandırma dosyasını ayarlamaya JustEnoughAdministration DSC kaynağı ve rol yetenekler dosya paylaşımından kopyalamak için dosya kaynağı kullanır.</span><span class="sxs-lookup"><span data-stu-id="1bdaf-134">In this configuration, you will use the JustEnoughAdministration DSC resource to set up the session configuration file and the File resource to copy over the role capabilities from the file share.</span></span>

<span data-ttu-id="1bdaf-135">Aşağıdaki özellikler DSC kaynağı kullanılarak yapılandırılabilir:</span><span class="sxs-lookup"><span data-stu-id="1bdaf-135">The following properties are configurable using the DSC resource:</span></span>
- <span data-ttu-id="1bdaf-136">Rol tanımları</span><span class="sxs-lookup"><span data-stu-id="1bdaf-136">Role Definitions</span></span>
- <span data-ttu-id="1bdaf-137">Sanal hesap grupları</span><span class="sxs-lookup"><span data-stu-id="1bdaf-137">Virtual Account groups</span></span>
- <span data-ttu-id="1bdaf-138">Grup yönetilen hizmet hesabı adı</span><span class="sxs-lookup"><span data-stu-id="1bdaf-138">Group Managed Service Account name</span></span>
- <span data-ttu-id="1bdaf-139">Dökümü dizini</span><span class="sxs-lookup"><span data-stu-id="1bdaf-139">Transcript directory</span></span>
- <span data-ttu-id="1bdaf-140">Kullanıcı sürücü</span><span class="sxs-lookup"><span data-stu-id="1bdaf-140">User drive</span></span>
- <span data-ttu-id="1bdaf-141">Koşullu erişim kuralları</span><span class="sxs-lookup"><span data-stu-id="1bdaf-141">Conditional access rules</span></span>
- <span data-ttu-id="1bdaf-142">JEA oturumu için başlangıç betiklerini</span><span class="sxs-lookup"><span data-stu-id="1bdaf-142">Startup scripts for the JEA session</span></span>

<span data-ttu-id="1bdaf-143">DSC yapılandırması bu özelliklerin her biri için söz dizimi PowerShell oturumu yapılandırma dosyası ile tutarlıdır.</span><span class="sxs-lookup"><span data-stu-id="1bdaf-143">The syntax for each of these properties in a DSC configuration is consistent with the PowerShell session configuration file.</span></span>

<span data-ttu-id="1bdaf-144">Genel sunucu bakım modülü için örnek bir DSC yapılandırma aşağıdadır.</span><span class="sxs-lookup"><span data-stu-id="1bdaf-144">Below is a sample DSC configuration for a general server maintenance module.</span></span>

<span data-ttu-id="1bdaf-145">Rol özellikleri 'RoleCapabilities' bir alt klasör içeren geçerli bir PowerShell modülü bulunan varsayar '\\\\myfileshare\\JEA' dosya paylaşımı.</span><span class="sxs-lookup"><span data-stu-id="1bdaf-145">It assumes that a valid PowerShell module containing role capabilities in a 'RoleCapabilities' subfolder is located on the '\\\\myfileshare\\JEA' file share.</span></span>


```powershell
Configuration JEAMaintenance
{
    Import-DscResource -Module JustEnoughAdministration, PSDesiredStateConfiguration

    File MaintenanceModule
    {
        SourcePath = "\\myfileshare\JEA\ContosoMaintenance"
        DestinationPath = "C:\Program Files\WindowsPowerShell\Modules\ContosoMaintenance"
        Checksum = "SHA-256"
        Ensure = "Present"
        Type = "Directory"
        Recurse = $true
    }

    JeaEndpoint JEAMaintenanceEndpoint
    {
        EndpointName = "JEAMaintenance"
        RoleDefinitions = "@{ 'CONTOSO\JEAMaintenanceAuditors' = @{ RoleCapabilities = 'GeneralServerMaintenance-Audit' }; 'CONTOSO\JEAMaintenanceAdmins' = @{ RoleCapabilities = 'GeneralServerMaintenance-Audit', 'GeneralServerMaintenance-Admin' } }"
        TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
        DependsOn = '[File]MaintenanceModule'
    }
}
```

<span data-ttu-id="1bdaf-146">Bu yapılandırmayı daha sonra bir sistemde tarafından uygulanabilir [yerel Configuration Manager doğrudan çağırma](https://msdn.microsoft.com/en-us/powershell/dsc/metaconfig) veya güncelleştirme [çekme sunucu yapılandırması](https://msdn.microsoft.com/en-us/powershell/dsc/pullserver).</span><span class="sxs-lookup"><span data-stu-id="1bdaf-146">This configuration can then be applied on a system by [directly invoking the Local Configuration Manager](https://msdn.microsoft.com/en-us/powershell/dsc/metaconfig) or updating the [pull server configuration](https://msdn.microsoft.com/en-us/powershell/dsc/pullserver).</span></span>

<span data-ttu-id="1bdaf-147">DSC kaynağı varsayılan Microsoft.PowerShell uzak uç değiştirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="1bdaf-147">The DSC resource also allows you to replace the default Microsoft.PowerShell remoting endpoint.</span></span>
<span data-ttu-id="1bdaf-148">Bunu yaparsanız, kaynak "WinRM (Uzak Yönetim kullanıcıları ve yerel Yöneticiler grubu üyeleri erişmek izin vererek) ACL varsayılan olan Microsoft.PowerShell.Restricted" adlı bir yedekleme unconstrainted uç noktası otomatik olarak kaydeder.</span><span class="sxs-lookup"><span data-stu-id="1bdaf-148">If you do this, the resource will automatically register a backup unconstrainted endpoint named "Microsoft.PowerShell.Restricted" which has the default WinRM ACL (allowing Remote Management Users and local Administrators group members to access it).</span></span>

## <a name="unregistering-jea-configurations"></a><span data-ttu-id="1bdaf-149">Kaydı siliniyor JEA yapılandırmaları</span><span class="sxs-lookup"><span data-stu-id="1bdaf-149">Unregistering JEA configurations</span></span>

<span data-ttu-id="1bdaf-150">Bir sistem JEA noktadaki kaldırmak için kullanın [Unregister-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="1bdaf-150">To remove a JEA endpoint on a system, use the [Unregister-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet.</span></span>
<span data-ttu-id="1bdaf-151">JEA endpoint kaydını yeni kullanıcıların sistemde yeni JEA oturumlar oluşturmaktan engel olur.</span><span class="sxs-lookup"><span data-stu-id="1bdaf-151">Unregistering a JEA endpoint will prevent new users from creating new JEA sessions on the system.</span></span>
<span data-ttu-id="1bdaf-152">Ayrıca, aynı uç nokta adı kullanarak güncelleştirilmiş oturum yapılandırma dosyası yeniden kaydederek JEA yapılandırmasını güncelleştirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="1bdaf-152">It also allows you to update a JEA configuration by re-registering an updated session configuration file using the same endpoint name.</span></span>

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="1bdaf-153">Bir JEA kaydını yeniden başlatmak WinRM Hizmeti uç noktası neden olur.</span><span class="sxs-lookup"><span data-stu-id="1bdaf-153">Unregistering a JEA endpoint will cause the WinRM service to restart.</span></span>
> <span data-ttu-id="1bdaf-154">Bu, devam eden diğer PowerShell oturumları, WMI çağrılarını ve bazı yönetim araçları dahil olmak üzere, çoğu uzak yönetim işlemlerini kesintiye uğratır.</span><span class="sxs-lookup"><span data-stu-id="1bdaf-154">This will interrupt most remote management operations in progress, including other PowerShell sessions, WMI invocations, and some management tools.</span></span>
> <span data-ttu-id="1bdaf-155">Yalnızca PowerShell uç noktaları planlı bakım pencerelerini kaydını silin.</span><span class="sxs-lookup"><span data-stu-id="1bdaf-155">Only unregister PowerShell endpoints during planned maintenance windows.</span></span>

## <a name="next-steps"></a><span data-ttu-id="1bdaf-156">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="1bdaf-156">Next steps</span></span>

- [<span data-ttu-id="1bdaf-157">JEA endpoint test</span><span class="sxs-lookup"><span data-stu-id="1bdaf-157">Test the JEA endpoint</span></span>](using-jea.md)

