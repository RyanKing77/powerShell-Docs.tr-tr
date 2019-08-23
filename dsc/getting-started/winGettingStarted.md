---
ms.date: 08/15/2019
keywords: DSC, PowerShell, yapılandırma, kurulum
title: Windows için Istenen durum yapılandırması (DSC) ile çalışmaya başlama
ms.openlocfilehash: a4f9db481afda65fc4ac5e553230dbba3037ac9a
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988931"
---
# <a name="get-started-with-desired-state-configuration-dsc-for-windows"></a><span data-ttu-id="5624f-103">Windows için Istenen durum yapılandırması (DSC) ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="5624f-103">Get started with Desired State Configuration (DSC) for Windows</span></span>

<span data-ttu-id="5624f-104">Bu konuda, Windows için PowerShell Istenen durum yapılandırması (DSC) ile çalışmaya başlama açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5624f-104">This topic explains how to get started using PowerShell Desired State Configuration (DSC) for Windows.</span></span>
<span data-ttu-id="5624f-105">DSC hakkında genel bilgi için bkz. [Windows PowerShell Istenen durum yapılandırmasını kullanmaya başlama](../overview/overview.md).</span><span class="sxs-lookup"><span data-stu-id="5624f-105">For general information about DSC, see [Get Started with Windows PowerShell Desired State Configuration](../overview/overview.md).</span></span>

## <a name="supported-windows-operation-system-versions"></a><span data-ttu-id="5624f-106">Desteklenen Windows işletim sistemi sürümleri</span><span class="sxs-lookup"><span data-stu-id="5624f-106">Supported Windows operation system versions</span></span>

<span data-ttu-id="5624f-107">Aşağıdaki sürümler desteklenir:</span><span class="sxs-lookup"><span data-stu-id="5624f-107">The following versions are supported:</span></span>

- <span data-ttu-id="5624f-108">Windows Server 2019</span><span class="sxs-lookup"><span data-stu-id="5624f-108">Windows Server 2019</span></span>
- <span data-ttu-id="5624f-109">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="5624f-109">Windows Server 2016</span></span>
- <span data-ttu-id="5624f-110">Windows Server 2012R2</span><span class="sxs-lookup"><span data-stu-id="5624f-110">Windows Server 2012R2</span></span>
- <span data-ttu-id="5624f-111">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="5624f-111">Windows Server 2012</span></span>
- <span data-ttu-id="5624f-112">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="5624f-112">Windows Server 2008 R2 SP1</span></span>
- <span data-ttu-id="5624f-113">Windows 10</span><span class="sxs-lookup"><span data-stu-id="5624f-113">Windows 10</span></span>
- <span data-ttu-id="5624f-114">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="5624f-114">Windows 8.1</span></span>
- <span data-ttu-id="5624f-115">Windows 7</span><span class="sxs-lookup"><span data-stu-id="5624f-115">Windows 7</span></span>

<span data-ttu-id="5624f-116">[Microsoft Hyper-V Server](/windows-server/virtualization/hyper-v/hyper-v-server-2016) tek başına Ürün SKU 'Su istenen durum yapılandırmasına sahip değil, bu nedenle PowerShell DSC veya Azure Otomasyonu durum yapılandırması tarafından yönetilemez.</span><span class="sxs-lookup"><span data-stu-id="5624f-116">The [Microsoft Hyper-V Server](/windows-server/virtualization/hyper-v/hyper-v-server-2016) standalone product sku does not contain an implementation of Desired State Configuraion so it cannot be managed by PowerShell DSC or Azure Automation State Configuration.</span></span>

## <a name="installing-dsc"></a><span data-ttu-id="5624f-117">DSC yükleme</span><span class="sxs-lookup"><span data-stu-id="5624f-117">Installing DSC</span></span>

<span data-ttu-id="5624f-118">PowerShell Istenen durum Yapılandırması Windows 'a dahil edilmiştir ve Windows Management Framework aracılığıyla güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="5624f-118">PowerShell Desired State Configuration is included in Windows and updated through Windows Management Framework.</span></span>
<span data-ttu-id="5624f-119">En son sürüm [Windows Management Framework 5,1](https://www.microsoft.com/en-us/download/details.aspx?id=54616)' dir.</span><span class="sxs-lookup"><span data-stu-id="5624f-119">The latest version is [Windows Management Framework 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616).</span></span>

> [!NOTE]
> <span data-ttu-id="5624f-120">DSC kullanarak bir makineyi yönetmek için ' DSC-Service ' Windows Server özelliğini etkinleştirmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="5624f-120">You do not need to enable the Windows Server feature 'DSC-Service' to manage a machine using DSC.</span></span>
> <span data-ttu-id="5624f-121">Bu özellik yalnızca bir Windows çekme sunucusu örneği oluşturulurken gereklidir.</span><span class="sxs-lookup"><span data-stu-id="5624f-121">That feature is only needed when building a Windows Pull Server instance.</span></span>

## <a name="using-dsc-for-windows"></a><span data-ttu-id="5624f-122">Windows için DSC kullanma</span><span class="sxs-lookup"><span data-stu-id="5624f-122">Using DSC for Windows</span></span>

<span data-ttu-id="5624f-123">Aşağıdaki bölümlerde Windows bilgisayarlarda DSC yapılandırmalarının nasıl oluşturulacağı ve çalıştırılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5624f-123">The following sections explain how to create and run DSC configurations on Windows computers.</span></span>

### <a name="creating-a-configuration-mof-document"></a><span data-ttu-id="5624f-124">Yapılandırma MOF belgesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="5624f-124">Creating a configuration MOF document</span></span>

<span data-ttu-id="5624f-125">Windows PowerShell yapılandırma anahtar sözcüğü, bir yapılandırma oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5624f-125">The Windows PowerShell Configuration keyword is used to create a configuration.</span></span>
<span data-ttu-id="5624f-126">Aşağıdaki adımlarda, Windows PowerShell kullanılarak bir yapılandırma belgesi oluşturma açıklanır.</span><span class="sxs-lookup"><span data-stu-id="5624f-126">The following steps describe the creation of a configuration document using Windows PowerShell.</span></span>

#### <a name="define-a-configuration-and-generate-the-configuration-document"></a><span data-ttu-id="5624f-127">Bir yapılandırma tanımlayın ve yapılandırma belgesini oluşturun:</span><span class="sxs-lookup"><span data-stu-id="5624f-127">Define a configuration and generate the configuration document:</span></span>

```powershell
Configuration EnvironmentVariable_Path
{
    param ()

    Import-DscResource -ModuleName 'PSDscResources'

    Node localhost
    {
        Environment CreatePathEnvironmentVariable
        {
            Name = 'TestPathEnvironmentVariable'
            Value = 'TestValue'
            Ensure = 'Present'
            Path = $true
            Target = @('Process', 'Machine')
        }
    }
}

EnvironmentVariable_Path -OutputPath:"C:\EnvironmentVariable_Path"
```
#### <a name="install-a-module-containing-dsc-resources"></a><span data-ttu-id="5624f-128">DSC kaynaklarını içeren bir modül yükler</span><span class="sxs-lookup"><span data-stu-id="5624f-128">Install a module containing DSC resources</span></span>

<span data-ttu-id="5624f-129">Windows PowerShell Istenen durum yapılandırması, DSC kaynaklarını içeren yerleşik modüller içerir.</span><span class="sxs-lookup"><span data-stu-id="5624f-129">Windows PowerShell Desired State Configuration includes built-in modules containing DSC resources.</span></span>
<span data-ttu-id="5624f-130">PowerShellGet cmdlet 'lerini kullanarak, PowerShell Galerisi gibi dış kaynaklardan modüller de yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5624f-130">You can also load modules from external sources such as the PowerShell Gallery, using the PowerShellGet cmdlets.</span></span>

`Install-Module 'PSDscResources' -Verbose`

#### <a name="apply-the-configuration-to-the-machine"></a><span data-ttu-id="5624f-131">Yapılandırmayı makineye Uygula</span><span class="sxs-lookup"><span data-stu-id="5624f-131">Apply the configuration to the machine</span></span>

<span data-ttu-id="5624f-132">Yapılandırma belgeleri (MOF dosyaları), [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet 'i kullanılarak makineye uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="5624f-132">Configuration documents (MOF files) can be applied to the machine using the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

`Start-DscConfiguration -Path 'C:\EnvironmentVariable_Path' -Wait -Verbose`

#### <a name="get-the-current-state-of-the-configuration"></a><span data-ttu-id="5624f-133">Yapılandırmanın geçerli durumunu al</span><span class="sxs-lookup"><span data-stu-id="5624f-133">Get the current state of the configuration</span></span>

<span data-ttu-id="5624f-134">[Get-DscConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet 'i makinenin geçerli durumunu sorgular ve yapılandırmanın geçerli değerlerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="5624f-134">The [Get-DscConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet queries the current status of the machine and returns the current values for the configuration.</span></span>

`Get-DscConfiguration`

<span data-ttu-id="5624f-135">[Get-DscLocalConfigurationManager](/powershell/module/psdesiredstateconfiguration/get-dscLocalConfigurationManager) cmdlet 'i, makineye uygulanan geçerli meta yapılandırmayı döndürür.</span><span class="sxs-lookup"><span data-stu-id="5624f-135">The [Get-DscLocalConfigurationManager](/powershell/module/psdesiredstateconfiguration/get-dscLocalConfigurationManager) cmdlet returns the current meta-configuration applied to the machine.</span></span>

`Get-DscLocalConfigurationManager`

#### <a name="remove-the-current-configuration-from-a-machine"></a><span data-ttu-id="5624f-136">Geçerli yapılandırmayı bir makineden kaldır</span><span class="sxs-lookup"><span data-stu-id="5624f-136">Remove the current configuration from a machine</span></span>

<span data-ttu-id="5624f-137">[Remove-DscConfigurationDocument](/powershell/module/psdesiredstateconfiguration/remove-dscconfigurationdocument)</span><span class="sxs-lookup"><span data-stu-id="5624f-137">The [Remove-DscConfigurationDocument](/powershell/module/psdesiredstateconfiguration/remove-dscconfigurationdocument)</span></span>

`Remove-DscConfigurationDocument -Stage Current -Verbose`

#### <a name="configure-settings-in-local-configuration-manager"></a><span data-ttu-id="5624f-138">Yerel Configuration Manager Ayarları Yapılandır</span><span class="sxs-lookup"><span data-stu-id="5624f-138">Configure settings in Local Configuration Manager</span></span>

<span data-ttu-id="5624f-139">[Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) cmdlet 'ini kullanarak makineye meta yapılandırma MOF dosyası uygulayın.</span><span class="sxs-lookup"><span data-stu-id="5624f-139">Apply a Meta Configuration MOF file to the machine using the [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) cmdlet.</span></span>
<span data-ttu-id="5624f-140">Meta yapılandırma MOF 'nin yolunu gerektirir.</span><span class="sxs-lookup"><span data-stu-id="5624f-140">Requires the path to the Meta Configuration MOF.</span></span>

`Set-DSCLocalConfigurationManager -Path 'c:\metaconfig\localhost.meta.mof' -Verbose`

## <a name="windows-powershell-desired-state-configuration-log-files"></a><span data-ttu-id="5624f-141">Windows PowerShell Istenen durum yapılandırması günlük dosyaları</span><span class="sxs-lookup"><span data-stu-id="5624f-141">Windows PowerShell Desired State Configuration log files</span></span>

<span data-ttu-id="5624f-142">DSC günlükleri yoldaki `Microsoft-Windows-Dsc/Operational`Windows olay günlüğü 'ne yazılır.</span><span class="sxs-lookup"><span data-stu-id="5624f-142">Logs for DSC are written to Windows Event Log in the path `Microsoft-Windows-Dsc/Operational`.</span></span>
<span data-ttu-id="5624f-143">Hata ayıklama amacıyla ek Günlükler, içinde [DSC olay günlüklerinin bulunduğu](/powershell/dsc/troubleshooting/troubleshooting#where-are-dsc-event-logs)adımlarda etkinleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="5624f-143">Additional logs for debugging purposes can be enabled following the steps in [Where Are DSC Event Logs](/powershell/dsc/troubleshooting/troubleshooting#where-are-dsc-event-logs).</span></span>
