---
ms.date: 06/12/2017
keywords: jea, powershell, güvenlik
title: JEA yapılandırmaları kaydediliyor
ms.openlocfilehash: 160aa95283da57a10aad5fdd4043adb1354a5db5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55689067"
---
# <a name="registering-jea-configurations"></a><span data-ttu-id="16dbb-103">JEA yapılandırmaları kaydediliyor</span><span class="sxs-lookup"><span data-stu-id="16dbb-103">Registering JEA Configurations</span></span>

> <span data-ttu-id="16dbb-104">Şunun için geçerlidir: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="16dbb-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="16dbb-105">Sonra [rol işlevleri](role-capabilities.md) ve [oturum yapılandırma dosyası](session-configurations.md) , son adım JEA kullanabilmeniz için önce JEA uç noktasını kaydetmek için oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="16dbb-105">Once you have your [role capabilities](role-capabilities.md) and [session configuration file](session-configurations.md) created, the last step before you can use JEA is to register the JEA endpoint.</span></span>
<span data-ttu-id="16dbb-106">Sistemiyle JEA uç noktası kaydediliyor uç nokta kullanıcılar ve Otomasyon motoru tarafından kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="16dbb-106">Registering the JEA endpoint with the system makes the endpoint available for use by users and automation engines.</span></span>

## <a name="single-machine-configuration"></a><span data-ttu-id="16dbb-107">Tek makine yapılandırması</span><span class="sxs-lookup"><span data-stu-id="16dbb-107">Single machine configuration</span></span>

<span data-ttu-id="16dbb-108">Küçük ortamlarda oturum yapılandırma dosyası kullanarak kaydederek JEA dağıtabilirsiniz [Register-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/register-pssessionconfiguration) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="16dbb-108">For small environments, you can deploy JEA by registering the session configuration file using the [Register-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/register-pssessionconfiguration) cmdlet.</span></span>

<span data-ttu-id="16dbb-109">Başlamadan önce aşağıdaki önkoşulları karşıladığınızdan emin olun:</span><span class="sxs-lookup"><span data-stu-id="16dbb-109">Before you begin, ensure that the following prerequisites have been met:</span></span>
- <span data-ttu-id="16dbb-110">Bir veya daha fazla rol oluşturuldu ve geçerli bir PowerShell Modülü 'RoleCapabilities' klasörüne yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="16dbb-110">One or more roles has been created and placed in the 'RoleCapabilities' folder of a valid PowerShell module.</span></span>
- <span data-ttu-id="16dbb-111">Bir oturum yapılandırma dosyası oluşturulur ve test.</span><span class="sxs-lookup"><span data-stu-id="16dbb-111">A session configuration file has been created and tested.</span></span>
- <span data-ttu-id="16dbb-112">Jea'yı yapılandırma kaydetme kullanıcı sistemleri üzerinde yönetici haklarına sahip.</span><span class="sxs-lookup"><span data-stu-id="16dbb-112">The user registering the JEA configuration has administrator rights on the system(s).</span></span>

<span data-ttu-id="16dbb-113">Ayrıca JEA uç noktanız için bir ad seçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="16dbb-113">You also need to select a name for your JEA endpoint.</span></span>
<span data-ttu-id="16dbb-114">Jea'yı kullanarak sisteme bağlanmak kullanıcıların istediğinizde JEA uç nokta adı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="16dbb-114">The name of the JEA endpoint is required when users want to connect to the system using JEA.</span></span>
<span data-ttu-id="16dbb-115">Kullanabileceğiniz [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet'ini sistemde mevcut uç nokta adları denetleyin.</span><span class="sxs-lookup"><span data-stu-id="16dbb-115">You can use the [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet to check the names of existing endpoints on the system.</span></span>
<span data-ttu-id="16dbb-116">'Microsoft' ile başlayan uç noktaları, genellikle Windows ile gönderilir.</span><span class="sxs-lookup"><span data-stu-id="16dbb-116">Endpoints that start with 'microsoft' are typically shipped with Windows.</span></span>
<span data-ttu-id="16dbb-117">'Microsoft.powershell' uç noktası bir uzak PowerShell uç noktasına bağlanırken kullanılan varsayılan uç noktadır.</span><span class="sxs-lookup"><span data-stu-id="16dbb-117">The 'microsoft.powershell' endpoint is the default endpoint used when connecting to a remote PowerShell endpoint.</span></span>

```powershell
PS C:\> Get-PSSessionConfiguration | Select-Object Name

Name
----
microsoft.powershell
microsoft.powershell.workflow
microsoft.powershell32
```

<span data-ttu-id="16dbb-118">JEA uç noktanız için uygun bir ad belirlediğinizde uç noktasını kaydetmek için aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="16dbb-118">When you have determined an appropriate name for your JEA endpoint, run the following command to register the endpoint.</span></span>

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="16dbb-119">Yukarıdaki komut, sistem üzerindeki WinRM hizmetini yeniden başlatır.</span><span class="sxs-lookup"><span data-stu-id="16dbb-119">The above command restarts the WinRM service on the system.</span></span>
> <span data-ttu-id="16dbb-120">Bu, devam eden herhangi bir DSC yapılandırması yanı sıra tüm PowerShell uzaktan iletişimini oturumlarını sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="16dbb-120">This terminates all PowerShell remoting sessions as well as any ongoing DSC configurations.</span></span>
> <span data-ttu-id="16dbb-121">İşle ilgili işlemlerin kesintiye önlemek için komutu çalıştırmadan önce tüm üretim makinelerinden çevrimdışı olması önerilir.</span><span class="sxs-lookup"><span data-stu-id="16dbb-121">It is recommended that you take any production machines offline before running the command to avoid disrupting business operations.</span></span>

<span data-ttu-id="16dbb-122">Kayıt başarılı olursa, hazır olduğunuz [JEA kullanın](using-jea.md).</span><span class="sxs-lookup"><span data-stu-id="16dbb-122">If registration is successful, you are ready to [use JEA](using-jea.md).</span></span>
<span data-ttu-id="16dbb-123">Dilediğiniz zaman oturum yapılandırma dosyasını silebilir; Kayıt uç noktasının sonrasında kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="16dbb-123">You may delete the session configuration file at any time; it is not used after registration of the end point.</span></span>

## <a name="multi-machine-configuration-with-dsc"></a><span data-ttu-id="16dbb-124">DSC ile çok makineli yapılandırma</span><span class="sxs-lookup"><span data-stu-id="16dbb-124">Multi-machine configuration with DSC</span></span>

<span data-ttu-id="16dbb-125">Birden fazla makinede JEA dağıtıyorsanız, en basit dağıtım modeli JEA kullanmaktır [Desired State Configuration](https://msdn.microsoft.com/powershell/dsc/overview) hızlı ve tutarlı bir şekilde JEA her makineye dağıtmak için kaynak.</span><span class="sxs-lookup"><span data-stu-id="16dbb-125">If you are deploying JEA on multiple machines, the simplest deployment model is to use the JEA [Desired State Configuration](https://msdn.microsoft.com/powershell/dsc/overview) resource to quickly and consistently deploy JEA on each machine.</span></span>

<span data-ttu-id="16dbb-126">JEA DSC ile dağıtmak için aşağıdaki önkoşulların karşılandığından emin olmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="16dbb-126">To deploy JEA with DSC, you need to ensure the following prerequisites are met:</span></span>
- <span data-ttu-id="16dbb-127">Bir veya daha fazla rol işlevleri yazılan ve geçerli bir PowerShell modülüne eklendi.</span><span class="sxs-lookup"><span data-stu-id="16dbb-127">One or more role capabilities have been authored and added to a valid PowerShell module.</span></span>
- <span data-ttu-id="16dbb-128">Rolleri içeren PowerShell modülünü (salt okunur) erişilebilen bir dosya paylaşımı her makine tarafından depolanır.</span><span class="sxs-lookup"><span data-stu-id="16dbb-128">The PowerShell module containing the roles is stored on a (read-only) file share accessible by each machine.</span></span>
- <span data-ttu-id="16dbb-129">Oturum yapılandırması ayarlarını belirlediniz.</span><span class="sxs-lookup"><span data-stu-id="16dbb-129">Settings for the session configuration have been determined.</span></span> <span data-ttu-id="16dbb-130">JEA DSC kaynağı kullanan bir oturum yapılandırma dosyası oluşturduğunuzda gerekmez.</span><span class="sxs-lookup"><span data-stu-id="16dbb-130">You do not need to create a session configuration file when using the JEA DSC resource.</span></span>
- <span data-ttu-id="16dbb-131">Her makine üzerinde yönetimsel Eylemler gerçekleştirmenize olanak sağlayan kimlik bilgilerine sahip olması veya makineleri yönetmek için kullanılan bir DSC çekme sunucusuna erişimi vardır.</span><span class="sxs-lookup"><span data-stu-id="16dbb-131">You have credentials that allow you to perform administrative actions on each machine, or have access to a DSC pull server used to manage the machines.</span></span>
- <span data-ttu-id="16dbb-132">Yüklediğiniz [JEA DSC kaynağı](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource)</span><span class="sxs-lookup"><span data-stu-id="16dbb-132">You have downloaded the [JEA DSC resource](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource)</span></span>

<span data-ttu-id="16dbb-133">Bir hedef makine (veya çekme sunucusu birini kullanıyorsanız), bir JEA uç noktanız için DSC yapılandırması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="16dbb-133">On a target machine (or pull server, if you are using one), create a DSC configuration for your JEA endpoint.</span></span>
<span data-ttu-id="16dbb-134">Bu yapılandırmada JustEnoughAdministration DSC kaynağı oturum yapılandırma dosyası oluşturma ve rol işlevleri dosya paylaşımı kopyalamak için dosya kaynağı kullanın.</span><span class="sxs-lookup"><span data-stu-id="16dbb-134">In this configuration, you use the JustEnoughAdministration DSC resource to set up the session configuration file and the File resource to copy over the role capabilities from the file share.</span></span>

<span data-ttu-id="16dbb-135">Aşağıdaki özellikler DSC kaynağı kullanılarak yapılandırılabilir:</span><span class="sxs-lookup"><span data-stu-id="16dbb-135">The following properties are configurable using the DSC resource:</span></span>
- <span data-ttu-id="16dbb-136">Rol tanımları</span><span class="sxs-lookup"><span data-stu-id="16dbb-136">Role Definitions</span></span>
- <span data-ttu-id="16dbb-137">Sanal hesap grupları</span><span class="sxs-lookup"><span data-stu-id="16dbb-137">Virtual Account groups</span></span>
- <span data-ttu-id="16dbb-138">Grup yönetilen hizmet hesabı adı</span><span class="sxs-lookup"><span data-stu-id="16dbb-138">Group Managed Service Account name</span></span>
- <span data-ttu-id="16dbb-139">Transkript dizini</span><span class="sxs-lookup"><span data-stu-id="16dbb-139">Transcript directory</span></span>
- <span data-ttu-id="16dbb-140">Kullanıcı sürücü</span><span class="sxs-lookup"><span data-stu-id="16dbb-140">User drive</span></span>
- <span data-ttu-id="16dbb-141">Koşullu erişim kuralları</span><span class="sxs-lookup"><span data-stu-id="16dbb-141">Conditional access rules</span></span>
- <span data-ttu-id="16dbb-142">JEA oturumu için başlangıç betikleri</span><span class="sxs-lookup"><span data-stu-id="16dbb-142">Startup scripts for the JEA session</span></span>

<span data-ttu-id="16dbb-143">DSC yapılandırması bu özelliklerden her biri için söz dizimi PowerShell oturumu yapılandırma dosyası ile tutarlıdır.</span><span class="sxs-lookup"><span data-stu-id="16dbb-143">The syntax for each of these properties in a DSC configuration is consistent with the PowerShell session configuration file.</span></span>

<span data-ttu-id="16dbb-144">Genel sunucu bakım modülü için örnek DSC yapılandırması aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="16dbb-144">Below is a sample DSC configuration for a general server maintenance module.</span></span>

<span data-ttu-id="16dbb-145">Rol işlevleri bir 'RoleCapabilities' alt içeren geçerli bir PowerShell modülü bulunan varsayar '\\\\myfileshare\\JEA' dosya paylaşımı.</span><span class="sxs-lookup"><span data-stu-id="16dbb-145">It assumes that a valid PowerShell module containing role capabilities in a 'RoleCapabilities' subfolder is located on the '\\\\myfileshare\\JEA' file share.</span></span>


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

<span data-ttu-id="16dbb-146">Bu yapılandırma tarafından bir sistemde sonra uygulanabilir [doğrudan yerel Configuration Manager'ı çağırma](https://msdn.microsoft.com/powershell/dsc/metaconfig) veya güncelleştirme [çekme sunucusu yapılandırmasını](https://msdn.microsoft.com/powershell/dsc/pullserver).</span><span class="sxs-lookup"><span data-stu-id="16dbb-146">This configuration can then be applied on a system by [directly invoking the Local Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig) or updating the [pull server configuration](https://msdn.microsoft.com/powershell/dsc/pullserver).</span></span>

<span data-ttu-id="16dbb-147">DSC kaynağı da varsayılan Microsoft.PowerShell uzak uç nokta çoğaltmanıza imkan tanır.</span><span class="sxs-lookup"><span data-stu-id="16dbb-147">The DSC resource also allows you to replace the default Microsoft.PowerShell remoting endpoint.</span></span>
<span data-ttu-id="16dbb-148">Bunu yaparsanız, kaynak, "WinRM (Uzak Yönetim kullanıcıları ve yerel Yöneticiler grup üyelerine erişim verme) ACL varsayılan olan Microsoft.PowerShell.Restricted" adlı bir yedekleme unconstrainted uç noktası otomatik olarak kaydeder.</span><span class="sxs-lookup"><span data-stu-id="16dbb-148">If you do this, the resource automatically registers a backup unconstrainted endpoint named "Microsoft.PowerShell.Restricted" which has the default WinRM ACL (allowing Remote Management Users and local Administrators group members to access it).</span></span>

## <a name="unregistering-jea-configurations"></a><span data-ttu-id="16dbb-149">JEA yapılandırmaları kaydı siliniyor</span><span class="sxs-lookup"><span data-stu-id="16dbb-149">Unregistering JEA configurations</span></span>

<span data-ttu-id="16dbb-150">Bir JEA uç noktası bir sistemde kaldırmak için [Unregister-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="16dbb-150">To remove a JEA endpoint on a system, use the [Unregister-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet.</span></span>
<span data-ttu-id="16dbb-151">Bir JEA uç noktası kaydı, yeni kullanıcıların sistemde yeni JEA oturumları oluşturmasını engeller.</span><span class="sxs-lookup"><span data-stu-id="16dbb-151">Unregistering a JEA endpoint prevents new users from creating new JEA sessions on the system.</span></span>
<span data-ttu-id="16dbb-152">Ayrıca, aynı uç nokta adı kullanarak güncelleştirilmiş oturum yapılandırma dosyası yeniden kaydederek bir JEA yapılandırmasını güncelleştirmek sağlar.</span><span class="sxs-lookup"><span data-stu-id="16dbb-152">It also allows you to update a JEA configuration by re-registering an updated session configuration file using the same endpoint name.</span></span>

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="16dbb-153">Bir JEA kaydını yeniden başlatmak WinRM Hizmeti uç noktası neden olur.</span><span class="sxs-lookup"><span data-stu-id="16dbb-153">Unregistering a JEA endpoint causes the WinRM service to restart.</span></span>
> <span data-ttu-id="16dbb-154">Bu, devam eden diğer PowerShell oturumları, WMI çağrıları ve bazı yönetim araçları dahil olmak üzere, en uzak yönetim işlemlerini kesintiye uğratır.</span><span class="sxs-lookup"><span data-stu-id="16dbb-154">This interrupts most remote management operations in progress, including other PowerShell sessions, WMI invocations, and some management tools.</span></span>
> <span data-ttu-id="16dbb-155">Yalnızca PowerShell uç noktaları, planlı bakım pencereleri sırasında kaydını silin.</span><span class="sxs-lookup"><span data-stu-id="16dbb-155">Only unregister PowerShell endpoints during planned maintenance windows.</span></span>

## <a name="next-steps"></a><span data-ttu-id="16dbb-156">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="16dbb-156">Next steps</span></span>

- [<span data-ttu-id="16dbb-157">JEA uç test etme</span><span class="sxs-lookup"><span data-stu-id="16dbb-157">Test the JEA endpoint</span></span>](using-jea.md)
