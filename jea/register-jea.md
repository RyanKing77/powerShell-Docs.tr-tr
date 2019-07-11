---
ms.date: 07/10/2019
keywords: jea, powershell, güvenlik
title: JEA yapılandırmaları kaydediliyor
ms.openlocfilehash: c85eddea2196e4db4bbeea54bde11074f3d1c927
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726617"
---
# <a name="registering-jea-configurations"></a><span data-ttu-id="6b497-103">JEA yapılandırmaları kaydediliyor</span><span class="sxs-lookup"><span data-stu-id="6b497-103">Registering JEA Configurations</span></span>

<span data-ttu-id="6b497-104">Sonra [rol işlevleri](role-capabilities.md) ve [oturum yapılandırma dosyası](session-configurations.md) , son adım JEA uç noktasını kaydetmek için oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="6b497-104">Once you have your [role capabilities](role-capabilities.md) and [session configuration file](session-configurations.md) created, the last step is to register the JEA endpoint.</span></span> <span data-ttu-id="6b497-105">Sistemiyle JEA uç noktası kaydediliyor uç nokta kullanıcılar ve Otomasyon motoru tarafından kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="6b497-105">Registering the JEA endpoint with the system makes the endpoint available for use by users and automation engines.</span></span>

## <a name="single-machine-configuration"></a><span data-ttu-id="6b497-106">Tek makine yapılandırması</span><span class="sxs-lookup"><span data-stu-id="6b497-106">Single machine configuration</span></span>

<span data-ttu-id="6b497-107">Küçük ortamlarda oturum yapılandırma dosyası kullanarak kaydederek JEA dağıtabilirsiniz [Register-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/register-pssessionconfiguration) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="6b497-107">For small environments, you can deploy JEA by registering the session configuration file using the [Register-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/register-pssessionconfiguration) cmdlet.</span></span>

<span data-ttu-id="6b497-108">Başlamadan önce aşağıdaki önkoşulları karşıladığınızdan emin olun:</span><span class="sxs-lookup"><span data-stu-id="6b497-108">Before you begin, ensure that the following prerequisites have been met:</span></span>

- <span data-ttu-id="6b497-109">Bir veya daha fazla rol oluşturuldu ve bulundukları **RoleCapabilities** bir PowerShell modülü klasörü.</span><span class="sxs-lookup"><span data-stu-id="6b497-109">One or more roles has been created and placed in the **RoleCapabilities** folder of a PowerShell module.</span></span>
- <span data-ttu-id="6b497-110">Bir oturum yapılandırma dosyası oluşturulur ve test.</span><span class="sxs-lookup"><span data-stu-id="6b497-110">A session configuration file has been created and tested.</span></span>
- <span data-ttu-id="6b497-111">Jea'yı yapılandırma kaydetme kullanıcı sistem üzerinde yönetici haklarına sahip.</span><span class="sxs-lookup"><span data-stu-id="6b497-111">The user registering the JEA configuration has administrator rights on the system.</span></span>
- <span data-ttu-id="6b497-112">JEA uç noktanız için bir ad seçtiniz.</span><span class="sxs-lookup"><span data-stu-id="6b497-112">You've selected a name for your JEA endpoint.</span></span>

<span data-ttu-id="6b497-113">Kullanıcılar JEA kullanarak sisteme bağlanmak için JEA uç nokta adı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="6b497-113">The name of the JEA endpoint is required when users connect to the system using JEA.</span></span> <span data-ttu-id="6b497-114">[Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet'i uç noktaları bir sistemde adlarını listeler.</span><span class="sxs-lookup"><span data-stu-id="6b497-114">The [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet lists the names of the endpoints on a system.</span></span> <span data-ttu-id="6b497-115">İle başlayan uç noktaları `microsoft` genellikle Windows ile gönderilir.</span><span class="sxs-lookup"><span data-stu-id="6b497-115">Endpoints that start with `microsoft` are typically shipped with Windows.</span></span> <span data-ttu-id="6b497-116">`microsoft.powershell` Uç noktası olan bir uzak PowerShell uç noktasına bağlanırken kullanılan varsayılan uç nokta.</span><span class="sxs-lookup"><span data-stu-id="6b497-116">The `microsoft.powershell` endpoint is the default endpoint used when connecting to a remote PowerShell endpoint.</span></span>

```powershell
Get-PSSessionConfiguration | Select-Object Name
```

```Output
Name
----
microsoft.powershell
microsoft.powershell.workflow
microsoft.powershell32
```

<span data-ttu-id="6b497-117">Uç nokta kaydetmek için aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="6b497-117">Run the following command to register the endpoint.</span></span>

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="6b497-118">Önceki komut, sistem üzerindeki WinRM hizmetini yeniden başlatır.</span><span class="sxs-lookup"><span data-stu-id="6b497-118">The previous command restarts the WinRM service on the system.</span></span> <span data-ttu-id="6b497-119">Bu, tüm PowerShell uzaktan iletişimini oturumları ve devam eden herhangi bir DSC yapılandırması sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="6b497-119">This terminates all PowerShell remoting sessions and any ongoing DSC configurations.</span></span> <span data-ttu-id="6b497-120">İşle ilgili işlemlerin kesintiye önlemek için komutu çalıştırmadan önce üretim makineleri çevrimdışına almanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="6b497-120">We recommended you take production machines offline before running the command to avoid disrupting business operations.</span></span>

<span data-ttu-id="6b497-121">Kayıt sonrasında hazır [JEA kullanın](using-jea.md).</span><span class="sxs-lookup"><span data-stu-id="6b497-121">After registration, you're ready to [use JEA](using-jea.md).</span></span> <span data-ttu-id="6b497-122">Dilediğiniz zaman oturum yapılandırma dosyasını silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6b497-122">You may delete the session configuration file at any time.</span></span> <span data-ttu-id="6b497-123">Yapılandırma dosyası, uç nokta kayıt sonrasında kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="6b497-123">The configuration file isn't used after registration of the endpoint.</span></span>

## <a name="multi-machine-configuration-with-dsc"></a><span data-ttu-id="6b497-124">DSC ile çok makineli yapılandırma</span><span class="sxs-lookup"><span data-stu-id="6b497-124">Multi-machine configuration with DSC</span></span>

<span data-ttu-id="6b497-125">JEA birden fazla makinede dağıtım yaparken, JEA en basit dağıtım modelini kullanan [Desired State Configuration ' nı (DSC)](/powershell/dsc/overview) hızlı ve tutarlı bir şekilde JEA her makineye dağıtmak için kaynak.</span><span class="sxs-lookup"><span data-stu-id="6b497-125">When deploying JEA on multiple machines, the simplest deployment model uses the JEA [Desired State Configuration (DSC)](/powershell/dsc/overview) resource to quickly and consistently deploy JEA on each machine.</span></span>

<span data-ttu-id="6b497-126">JEA DSC ile dağıtmak için aşağıdaki önkoşulların karşılandığından emin olun:</span><span class="sxs-lookup"><span data-stu-id="6b497-126">To deploy JEA with DSC, ensure the following prerequisites are met:</span></span>

- <span data-ttu-id="6b497-127">Bir veya daha fazla rol işlevleri yazılmış ve bir PowerShell modülüne eklendi.</span><span class="sxs-lookup"><span data-stu-id="6b497-127">One or more role capabilities have been authored and added to a PowerShell module.</span></span>
- <span data-ttu-id="6b497-128">Rolleri içeren PowerShell modülünü (salt okunur) erişilebilen bir dosya paylaşımı her makine tarafından depolanır.</span><span class="sxs-lookup"><span data-stu-id="6b497-128">The PowerShell module containing the roles is stored on a (read-only) file share accessible by each machine.</span></span>
- <span data-ttu-id="6b497-129">Oturum yapılandırması ayarlarını belirlediniz.</span><span class="sxs-lookup"><span data-stu-id="6b497-129">Settings for the session configuration have been determined.</span></span> <span data-ttu-id="6b497-130">JEA DSC kaynağı kullanılırken bir oturum yapılandırma dosyası oluşturmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="6b497-130">You don't need to create a session configuration file when using the JEA DSC resource.</span></span>
- <span data-ttu-id="6b497-131">Yönetim eylemlerini her makinede veya makineleri yönetmek için kullanılan DSC çekme sunucusuna erişim sağlayan kimlik bilgileri var.</span><span class="sxs-lookup"><span data-stu-id="6b497-131">You have credentials that allow administrative actions on each machine or access to the DSC pull server used to manage the machines.</span></span>
- <span data-ttu-id="6b497-132">İndirdiğiniz [JEA DSC kaynak](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource).</span><span class="sxs-lookup"><span data-stu-id="6b497-132">You've downloaded the [JEA DSC resource](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource).</span></span>

<span data-ttu-id="6b497-133">Bir hedef makine ya da çekme sunucusunda JEA uç noktanız için bir DSC yapılandırması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6b497-133">Create a DSC configuration for your JEA endpoint on a target machine or pull server.</span></span> <span data-ttu-id="6b497-134">Bu yapılandırmada, **JustEnoughAdministration** DSC kaynağı oturum yapılandırma dosyasını tanımlar ve **dosya** kaynak dosya paylaşımından rol özellikleri kopyalar.</span><span class="sxs-lookup"><span data-stu-id="6b497-134">In this configuration, the **JustEnoughAdministration** DSC resource defines the session configuration file and the **File** resource copies the role capabilities from the file share.</span></span>

<span data-ttu-id="6b497-135">Aşağıdaki özellikler DSC kaynağı kullanılarak yapılandırılabilir:</span><span class="sxs-lookup"><span data-stu-id="6b497-135">The following properties are configurable using the DSC resource:</span></span>

- <span data-ttu-id="6b497-136">Rol tanımları</span><span class="sxs-lookup"><span data-stu-id="6b497-136">Role Definitions</span></span>
- <span data-ttu-id="6b497-137">Sanal hesap grupları</span><span class="sxs-lookup"><span data-stu-id="6b497-137">Virtual account groups</span></span>
- <span data-ttu-id="6b497-138">Grup yönetilen hizmet hesabı adı</span><span class="sxs-lookup"><span data-stu-id="6b497-138">Group-managed service account name</span></span>
- <span data-ttu-id="6b497-139">Transkript dizini</span><span class="sxs-lookup"><span data-stu-id="6b497-139">Transcript directory</span></span>
- <span data-ttu-id="6b497-140">Kullanıcı sürücü</span><span class="sxs-lookup"><span data-stu-id="6b497-140">User drive</span></span>
- <span data-ttu-id="6b497-141">Koşullu erişim kuralları</span><span class="sxs-lookup"><span data-stu-id="6b497-141">Conditional access rules</span></span>
- <span data-ttu-id="6b497-142">JEA oturumu için başlangıç betikleri</span><span class="sxs-lookup"><span data-stu-id="6b497-142">Startup scripts for the JEA session</span></span>

<span data-ttu-id="6b497-143">DSC yapılandırması bu özelliklerden her biri için söz dizimi PowerShell oturumu yapılandırma dosyası ile tutarlıdır.</span><span class="sxs-lookup"><span data-stu-id="6b497-143">The syntax for each of these properties in a DSC configuration is consistent with the PowerShell session configuration file.</span></span>

<span data-ttu-id="6b497-144">Genel sunucu bakım modülü için örnek DSC yapılandırması aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6b497-144">Below is a sample DSC configuration for a general server maintenance module.</span></span> <span data-ttu-id="6b497-145">Rol işlevleri içeren geçerli bir PowerShell modülü bulunan varsayar `\\myfileshare\JEA` dosya paylaşımı.</span><span class="sxs-lookup"><span data-stu-id="6b497-145">It assumes that a valid PowerShell module containing role capabilities is located on the `\\myfileshare\JEA` file share.</span></span>

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

<span data-ttu-id="6b497-146">Ardından, yapılandırmanın bir sistemde doğrudan çağırarak uygulanması [yerel Configuration Manager](/powershell/dsc/managing-nodes/metaConfig) veya güncelleştirme [çekme sunucusu yapılandırmasını](/powershell/dsc/pull-server/pullServer).</span><span class="sxs-lookup"><span data-stu-id="6b497-146">Next, the configuration is applied on a system by directly invoking the [Local Configuration Manager](/powershell/dsc/managing-nodes/metaConfig) or updating the [pull server configuration](/powershell/dsc/pull-server/pullServer).</span></span>

<span data-ttu-id="6b497-147">DSC kaynağı da varsayılan çoğaltmanıza imkan tanır **Microsoft.PowerShell** uç noktası.</span><span class="sxs-lookup"><span data-stu-id="6b497-147">The DSC resource also allows you to replace the default **Microsoft.PowerShell** endpoint.</span></span> <span data-ttu-id="6b497-148">Değiştirildiğinde, kaynak adlı bir yedekleme uç noktası otomatik olarak kaydeder. **Microsoft.PowerShell.Restricted**.</span><span class="sxs-lookup"><span data-stu-id="6b497-148">When replaced, the resource automatically registers a backup endpoint named **Microsoft.PowerShell.Restricted**.</span></span> <span data-ttu-id="6b497-149">WinRM ACL, uzak yönetim kullanıcıları ve yerel Yöneticiler grup üyelerine erişim sağlar. varsayılan yedekleme uç nokta vardır.</span><span class="sxs-lookup"><span data-stu-id="6b497-149">The backup endpoint has the default WinRM ACL that allows Remote Management Users and local Administrators group members to access it.</span></span>

## <a name="unregistering-jea-configurations"></a><span data-ttu-id="6b497-150">JEA yapılandırmaları kaydı siliniyor</span><span class="sxs-lookup"><span data-stu-id="6b497-150">Unregistering JEA configurations</span></span>

<span data-ttu-id="6b497-151">[Unregister-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet'i bir JEA uç noktası kaldırır.</span><span class="sxs-lookup"><span data-stu-id="6b497-151">The [Unregister-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet removes a JEA endpoint.</span></span> <span data-ttu-id="6b497-152">Bir JEA uç noktası kaydı, yeni kullanıcıların sistemde yeni JEA oturumları oluşturmasını engeller.</span><span class="sxs-lookup"><span data-stu-id="6b497-152">Unregistering a JEA endpoint prevents new users from creating new JEA sessions on the system.</span></span> <span data-ttu-id="6b497-153">Ayrıca, aynı uç nokta adı kullanarak güncelleştirilmiş oturum yapılandırma dosyası yeniden kaydederek bir JEA yapılandırmasını güncelleştirmek sağlar.</span><span class="sxs-lookup"><span data-stu-id="6b497-153">It also allows you to update a JEA configuration by re-registering an updated session configuration file using the same endpoint name.</span></span>

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="6b497-154">Bir JEA kaydını yeniden başlatmak WinRM Hizmeti uç noktası neden olur.</span><span class="sxs-lookup"><span data-stu-id="6b497-154">Unregistering a JEA endpoint causes the WinRM service to restart.</span></span> <span data-ttu-id="6b497-155">Bu, devam eden diğer PowerShell oturumları, WMI çağrıları ve bazı yönetim araçları dahil olmak üzere, en uzak yönetim işlemlerini kesintiye uğratır.</span><span class="sxs-lookup"><span data-stu-id="6b497-155">This interrupts most remote management operations in progress, including other PowerShell sessions, WMI invocations, and some management tools.</span></span> <span data-ttu-id="6b497-156">Yalnızca PowerShell uç noktaları, planlı bakım pencereleri sırasında kaydını silin.</span><span class="sxs-lookup"><span data-stu-id="6b497-156">Only unregister PowerShell endpoints during planned maintenance windows.</span></span>

## <a name="next-steps"></a><span data-ttu-id="6b497-157">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="6b497-157">Next steps</span></span>

[<span data-ttu-id="6b497-158">JEA uç test etme</span><span class="sxs-lookup"><span data-stu-id="6b497-158">Test the JEA endpoint</span></span>](using-jea.md)
