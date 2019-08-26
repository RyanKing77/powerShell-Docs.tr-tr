---
ms.date: 07/10/2019
keywords: Jea, PowerShell, güvenlik
title: JEA yapılandırmalarının kaydı yapılıyor
ms.openlocfilehash: c85eddea2196e4db4bbeea54bde11074f3d1c927
ms.sourcegitcommit: e894ed833cef57967cdaf002f8c883f66864e836
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2019
ms.locfileid: "70017870"
---
# <a name="registering-jea-configurations"></a><span data-ttu-id="51a8c-103">JEA yapılandırmalarının kaydı yapılıyor</span><span class="sxs-lookup"><span data-stu-id="51a8c-103">Registering JEA Configurations</span></span>

<span data-ttu-id="51a8c-104">[Rol olanaklarınız](role-capabilities.md) ve [oturum yapılandırma dosyanız](session-configurations.md) oluşturulduktan sonra, son adım Jea uç noktasını kaydetmek olur.</span><span class="sxs-lookup"><span data-stu-id="51a8c-104">Once you have your [role capabilities](role-capabilities.md) and [session configuration file](session-configurations.md) created, the last step is to register the JEA endpoint.</span></span> <span data-ttu-id="51a8c-105">JEA uç noktasının sistemle kaydı, uç noktanın kullanıcılar ve otomasyon motorları tarafından kullanılabilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="51a8c-105">Registering the JEA endpoint with the system makes the endpoint available for use by users and automation engines.</span></span>

## <a name="single-machine-configuration"></a><span data-ttu-id="51a8c-106">Tek makineli yapılandırma</span><span class="sxs-lookup"><span data-stu-id="51a8c-106">Single machine configuration</span></span>

<span data-ttu-id="51a8c-107">Küçük ortamlarda, oturum yapılandırma dosyasını [register-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/register-pssessionconfiguration) cmdlet 'ini kullanarak kaydederek Jea 'yı dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="51a8c-107">For small environments, you can deploy JEA by registering the session configuration file using the [Register-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/register-pssessionconfiguration) cmdlet.</span></span>

<span data-ttu-id="51a8c-108">Başlamadan önce, aşağıdaki önkoşulların karşılandığından emin olun:</span><span class="sxs-lookup"><span data-stu-id="51a8c-108">Before you begin, ensure that the following prerequisites have been met:</span></span>

- <span data-ttu-id="51a8c-109">Bir veya daha fazla rol oluşturulup bir PowerShell modülünün **Rolecapabilities** klasörüne yerleştirildi.</span><span class="sxs-lookup"><span data-stu-id="51a8c-109">One or more roles has been created and placed in the **RoleCapabilities** folder of a PowerShell module.</span></span>
- <span data-ttu-id="51a8c-110">Bir oturum yapılandırma dosyası oluşturuldu ve test edildi.</span><span class="sxs-lookup"><span data-stu-id="51a8c-110">A session configuration file has been created and tested.</span></span>
- <span data-ttu-id="51a8c-111">JEA yapılandırmasını kaydeden Kullanıcı sistemde yönetici haklarına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="51a8c-111">The user registering the JEA configuration has administrator rights on the system.</span></span>
- <span data-ttu-id="51a8c-112">JEA uç noktanız için bir ad seçtiniz.</span><span class="sxs-lookup"><span data-stu-id="51a8c-112">You've selected a name for your JEA endpoint.</span></span>

<span data-ttu-id="51a8c-113">Kullanıcılar JEA kullanarak sisteme bağlandıklarında JEA uç noktasının adı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="51a8c-113">The name of the JEA endpoint is required when users connect to the system using JEA.</span></span> <span data-ttu-id="51a8c-114">[Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet 'i bir sistemdeki uç noktaların adlarını listeler.</span><span class="sxs-lookup"><span data-stu-id="51a8c-114">The [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet lists the names of the endpoints on a system.</span></span> <span data-ttu-id="51a8c-115">İle `microsoft` başlayan uç noktalar genellikle Windows ile birlikte gönderilir.</span><span class="sxs-lookup"><span data-stu-id="51a8c-115">Endpoints that start with `microsoft` are typically shipped with Windows.</span></span> <span data-ttu-id="51a8c-116">`microsoft.powershell` Uç nokta, uzak bir PowerShell uç noktasına bağlanırken kullanılan varsayılan uç noktadır.</span><span class="sxs-lookup"><span data-stu-id="51a8c-116">The `microsoft.powershell` endpoint is the default endpoint used when connecting to a remote PowerShell endpoint.</span></span>

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

<span data-ttu-id="51a8c-117">Uç noktasını kaydetmek için aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="51a8c-117">Run the following command to register the endpoint.</span></span>

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="51a8c-118">Önceki komut, sistem üzerindeki WinRM hizmetini yeniden başlatır.</span><span class="sxs-lookup"><span data-stu-id="51a8c-118">The previous command restarts the WinRM service on the system.</span></span> <span data-ttu-id="51a8c-119">Bu, tüm PowerShell uzaktan iletişim oturumlarını ve devam eden DSC yapılandırmasını sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="51a8c-119">This terminates all PowerShell remoting sessions and any ongoing DSC configurations.</span></span> <span data-ttu-id="51a8c-120">İş operasyonlarının kesintiye uğramaması için komutunu çalıştırmadan önce üretim makinelerinizi çevrimdışına almanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="51a8c-120">We recommended you take production machines offline before running the command to avoid disrupting business operations.</span></span>

<span data-ttu-id="51a8c-121">Kayıttan sonra, [JEA kullanmaya](using-jea.md)hazırsınız demektir.</span><span class="sxs-lookup"><span data-stu-id="51a8c-121">After registration, you're ready to [use JEA](using-jea.md).</span></span> <span data-ttu-id="51a8c-122">Oturum yapılandırma dosyasını dilediğiniz zaman silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="51a8c-122">You may delete the session configuration file at any time.</span></span> <span data-ttu-id="51a8c-123">Yapılandırma dosyası uç nokta kaydettirildikten sonra kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="51a8c-123">The configuration file isn't used after registration of the endpoint.</span></span>

## <a name="multi-machine-configuration-with-dsc"></a><span data-ttu-id="51a8c-124">DSC ile çok makineli yapılandırma</span><span class="sxs-lookup"><span data-stu-id="51a8c-124">Multi-machine configuration with DSC</span></span>

<span data-ttu-id="51a8c-125">JEA 'yı birden çok makineye dağıtırken, en basit dağıtım modeli JEA [Istenen durum yapılandırması (DSC)](/powershell/dsc/overview) kaynağını her makinede hızlı ve tutarlı bir şekilde dağıtmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="51a8c-125">When deploying JEA on multiple machines, the simplest deployment model uses the JEA [Desired State Configuration (DSC)](/powershell/dsc/overview) resource to quickly and consistently deploy JEA on each machine.</span></span>

<span data-ttu-id="51a8c-126">JEA 'yı DSC ile dağıtmak için aşağıdaki önkoşulların karşılandığından emin olun:</span><span class="sxs-lookup"><span data-stu-id="51a8c-126">To deploy JEA with DSC, ensure the following prerequisites are met:</span></span>

- <span data-ttu-id="51a8c-127">Bir veya daha fazla rol özelliği yazıldı ve bir PowerShell modülüne eklendi.</span><span class="sxs-lookup"><span data-stu-id="51a8c-127">One or more role capabilities have been authored and added to a PowerShell module.</span></span>
- <span data-ttu-id="51a8c-128">Rolleri içeren PowerShell modülü, her makine tarafından erişilebilen bir (salt okunurdur) dosya paylaşımında depolanır.</span><span class="sxs-lookup"><span data-stu-id="51a8c-128">The PowerShell module containing the roles is stored on a (read-only) file share accessible by each machine.</span></span>
- <span data-ttu-id="51a8c-129">Oturum yapılandırması ayarları belirlendi.</span><span class="sxs-lookup"><span data-stu-id="51a8c-129">Settings for the session configuration have been determined.</span></span> <span data-ttu-id="51a8c-130">JEA DSC kaynağını kullanırken bir oturum yapılandırma dosyası oluşturmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="51a8c-130">You don't need to create a session configuration file when using the JEA DSC resource.</span></span>
- <span data-ttu-id="51a8c-131">Her makinede yönetim eylemlerine izin veren veya makineleri yönetmek için kullanılan DSC çekme sunucusuna erişim sağlayan kimlik bilgileri vardır.</span><span class="sxs-lookup"><span data-stu-id="51a8c-131">You have credentials that allow administrative actions on each machine or access to the DSC pull server used to manage the machines.</span></span>
- <span data-ttu-id="51a8c-132">[Jea DSC kaynağını](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource)indirdiniz.</span><span class="sxs-lookup"><span data-stu-id="51a8c-132">You've downloaded the [JEA DSC resource](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource).</span></span>

<span data-ttu-id="51a8c-133">Hedef makinede veya çekme sunucusunda JEA uç noktanız için bir DSC yapılandırması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="51a8c-133">Create a DSC configuration for your JEA endpoint on a target machine or pull server.</span></span> <span data-ttu-id="51a8c-134">Bu yapılandırmada, **Ditenoughadministration** DSC kaynağı, oturum yapılandırma dosyasını tanımlar ve **Dosya** kaynağı rol yeteneklerini dosya paylaşımından kopyalar.</span><span class="sxs-lookup"><span data-stu-id="51a8c-134">In this configuration, the **JustEnoughAdministration** DSC resource defines the session configuration file and the **File** resource copies the role capabilities from the file share.</span></span>

<span data-ttu-id="51a8c-135">Aşağıdaki özellikler DSC kaynağı kullanılarak yapılandırılabilir:</span><span class="sxs-lookup"><span data-stu-id="51a8c-135">The following properties are configurable using the DSC resource:</span></span>

- <span data-ttu-id="51a8c-136">Rol tanımları</span><span class="sxs-lookup"><span data-stu-id="51a8c-136">Role Definitions</span></span>
- <span data-ttu-id="51a8c-137">Sanal hesap grupları</span><span class="sxs-lookup"><span data-stu-id="51a8c-137">Virtual account groups</span></span>
- <span data-ttu-id="51a8c-138">Grup tarafından yönetilen hizmet hesabı adı</span><span class="sxs-lookup"><span data-stu-id="51a8c-138">Group-managed service account name</span></span>
- <span data-ttu-id="51a8c-139">Döküm dizini</span><span class="sxs-lookup"><span data-stu-id="51a8c-139">Transcript directory</span></span>
- <span data-ttu-id="51a8c-140">Kullanıcı sürücüsü</span><span class="sxs-lookup"><span data-stu-id="51a8c-140">User drive</span></span>
- <span data-ttu-id="51a8c-141">Koşullu erişim kuralları</span><span class="sxs-lookup"><span data-stu-id="51a8c-141">Conditional access rules</span></span>
- <span data-ttu-id="51a8c-142">JEA oturumu için başlatma betikleri</span><span class="sxs-lookup"><span data-stu-id="51a8c-142">Startup scripts for the JEA session</span></span>

<span data-ttu-id="51a8c-143">Bir DSC yapılandırmasındaki bu özelliklerin her biri için sözdizimi, PowerShell oturum yapılandırma dosyası ile tutarlıdır.</span><span class="sxs-lookup"><span data-stu-id="51a8c-143">The syntax for each of these properties in a DSC configuration is consistent with the PowerShell session configuration file.</span></span>

<span data-ttu-id="51a8c-144">Genel sunucu bakım modülünün örnek DSC yapılandırması aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="51a8c-144">Below is a sample DSC configuration for a general server maintenance module.</span></span> <span data-ttu-id="51a8c-145">Rol özelliklerini `\\myfileshare\JEA` içeren geçerli bir PowerShell modülünün dosya paylaşımında bulunduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="51a8c-145">It assumes that a valid PowerShell module containing role capabilities is located on the `\\myfileshare\JEA` file share.</span></span>

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

<span data-ttu-id="51a8c-146">Daha sonra, yapılandırma doğrudan [yerel Configuration Manager](/powershell/dsc/managing-nodes/metaConfig) çağırarak veya [çekme sunucusu yapılandırması](/powershell/dsc/pull-server/pullServer)güncelleştirilerek bir sisteme uygulanır.</span><span class="sxs-lookup"><span data-stu-id="51a8c-146">Next, the configuration is applied on a system by directly invoking the [Local Configuration Manager](/powershell/dsc/managing-nodes/metaConfig) or updating the [pull server configuration](/powershell/dsc/pull-server/pullServer).</span></span>

<span data-ttu-id="51a8c-147">DSC kaynağı, varsayılan **Microsoft. PowerShell** uç noktasını değiştirmenize de olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="51a8c-147">The DSC resource also allows you to replace the default **Microsoft.PowerShell** endpoint.</span></span> <span data-ttu-id="51a8c-148">Değiştirildiğinde kaynak, **Microsoft. PowerShell. Restricted**adlı bir yedekleme uç noktasını otomatik olarak kaydeder.</span><span class="sxs-lookup"><span data-stu-id="51a8c-148">When replaced, the resource automatically registers a backup endpoint named **Microsoft.PowerShell.Restricted**.</span></span> <span data-ttu-id="51a8c-149">Yedekleme uç noktası, uzaktan yönetim kullanıcılarına ve yerel Yöneticiler grubu üyelerine erişmesine izin veren varsayılan WinRM ACL 'sine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="51a8c-149">The backup endpoint has the default WinRM ACL that allows Remote Management Users and local Administrators group members to access it.</span></span>

## <a name="unregistering-jea-configurations"></a><span data-ttu-id="51a8c-150">JEA yapılandırmalarının kaydı siliniyor</span><span class="sxs-lookup"><span data-stu-id="51a8c-150">Unregistering JEA configurations</span></span>

<span data-ttu-id="51a8c-151">[Unregister-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet 'ı BIR Jea uç noktasını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="51a8c-151">The [Unregister-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet removes a JEA endpoint.</span></span> <span data-ttu-id="51a8c-152">JEA uç noktasının kaydını silme, yeni kullanıcıların sistemde yeni JEA oturumları oluşturmasını engeller.</span><span class="sxs-lookup"><span data-stu-id="51a8c-152">Unregistering a JEA endpoint prevents new users from creating new JEA sessions on the system.</span></span> <span data-ttu-id="51a8c-153">Aynı zamanda aynı uç nokta adını kullanarak güncelleştirilmiş bir oturum yapılandırma dosyasını yeniden kaydederek bir JEA yapılandırmasını güncelleştirmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="51a8c-153">It also allows you to update a JEA configuration by re-registering an updated session configuration file using the same endpoint name.</span></span>

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="51a8c-154">JEA uç noktasının kaydının kaydı, WinRM hizmetinin yeniden başlatılmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="51a8c-154">Unregistering a JEA endpoint causes the WinRM service to restart.</span></span> <span data-ttu-id="51a8c-155">Bu, diğer PowerShell oturumları, WMI etkinleştirmeleri ve bazı yönetim araçları da dahil olmak üzere birçok uzaktan yönetim işlemini keser.</span><span class="sxs-lookup"><span data-stu-id="51a8c-155">This interrupts most remote management operations in progress, including other PowerShell sessions, WMI invocations, and some management tools.</span></span> <span data-ttu-id="51a8c-156">Yalnızca planlanan bakım pencereleri sırasında PowerShell uç noktalarının kaydını silin.</span><span class="sxs-lookup"><span data-stu-id="51a8c-156">Only unregister PowerShell endpoints during planned maintenance windows.</span></span>

## <a name="next-steps"></a><span data-ttu-id="51a8c-157">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="51a8c-157">Next steps</span></span>

[<span data-ttu-id="51a8c-158">JEA uç noktasını test etme</span><span class="sxs-lookup"><span data-stu-id="51a8c-158">Test the JEA endpoint</span></span>](using-jea.md)
