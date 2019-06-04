---
ms.date: 01/17/2019
keywords: DSC, powershell, yapılandırma, Kurulum
title: Düğümü yeniden başlatma
ms.openlocfilehash: 106fa1e7b0e3aaf3070ec05548d51140fe9a7725
ms.sourcegitcommit: bc42c9166857147a1ecf9924b718d4a48eb901e3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/03/2019
ms.locfileid: "66470753"
---
# <a name="reboot-a-node"></a><span data-ttu-id="5f277-103">Düğümü yeniden başlatma</span><span class="sxs-lookup"><span data-stu-id="5f277-103">Reboot a Node</span></span>

> [!NOTE]
> <span data-ttu-id="5f277-104">Bu konuda, bir düğümü yeniden başlatma hakkında konuşuyor.</span><span class="sxs-lookup"><span data-stu-id="5f277-104">This topic talks about how to reboot a Node.</span></span> <span data-ttu-id="5f277-105">Başarılı olması için yeniden başlatma için sırayla **ActionAfterReboot** ve **RebootNodeIfNeeded** LCM ayarları doğru şekilde yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5f277-105">In order for the reboot to be successful the **ActionAfterReboot** and **RebootNodeIfNeeded** LCM settings need to be configured properly.</span></span>
> <span data-ttu-id="5f277-106">Yerel Configuration Manager ayarları hakkında bilgi için bkz [yerel Configuration Manager Yapılandırma](../managing-nodes/metaConfig.md), veya [yerel Configuration Manager'ı (v4) yapılandırma](../managing-nodes/metaConfig4.md).</span><span class="sxs-lookup"><span data-stu-id="5f277-106">To read about Local Configuration Manager settings, see [Configure the Local Configuration Manager](../managing-nodes/metaConfig.md), or [Configure the Local Configuration Manager (v4)](../managing-nodes/metaConfig4.md).</span></span>

<span data-ttu-id="5f277-107">Düğümler yeniden başlatılması gelen bir kaynak içinde kullanarak `$global:DSCMachineStatus` bayrağı.</span><span class="sxs-lookup"><span data-stu-id="5f277-107">Nodes can be rebooted from within a resource, by using the `$global:DSCMachineStatus` flag.</span></span> <span data-ttu-id="5f277-108">Bu bayrak ayarlayarak `1` içinde `Set-TargetResource` işlevi zorlar düğümü doğrudan sonra yeniden başlatma için LCM'yi **ayarlayın** geçerli kaynak yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5f277-108">Setting this flag to `1` in the `Set-TargetResource` function forces the LCM to reboot the Node directly after the **Set** method of the current resource.</span></span> <span data-ttu-id="5f277-109">Bu bayrağı kullanarak **xPendingReboot** kaynak algılar bir yeniden başlatmanın bekletilip bekletilmediği DSC dışında.</span><span class="sxs-lookup"><span data-stu-id="5f277-109">Using this flag, the **xPendingReboot** resource detects if a reboot is pending outside of DSC.</span></span>

<span data-ttu-id="5f277-110">[Yapılandırmaları](configurations.md) düğümü yeniden başlatmak gerekli adımları gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="5f277-110">Your [configurations](configurations.md) may perform steps that require the Node to reboot.</span></span> <span data-ttu-id="5f277-111">Bu gibi şeyler içerebilir:</span><span class="sxs-lookup"><span data-stu-id="5f277-111">This could include things such as:</span></span>

- <span data-ttu-id="5f277-112">Windows güncelleştirmeleri</span><span class="sxs-lookup"><span data-stu-id="5f277-112">Windows updates</span></span>
- <span data-ttu-id="5f277-113">Yazılım yükleme</span><span class="sxs-lookup"><span data-stu-id="5f277-113">Software install</span></span>
- <span data-ttu-id="5f277-114">Dosyayı yeniden adlandırır</span><span class="sxs-lookup"><span data-stu-id="5f277-114">File renames</span></span>
- <span data-ttu-id="5f277-115">Bilgisayarı yeniden adlandırma</span><span class="sxs-lookup"><span data-stu-id="5f277-115">Computer rename</span></span>

<span data-ttu-id="5f277-116">**XPendingReboot** kaynak bir yeniden başlatmanın bekletilip bekletilmediği belirlemek için belirli bir bilgisayar konumları denetler.</span><span class="sxs-lookup"><span data-stu-id="5f277-116">The **xPendingReboot** resource checks specific computer locations to determine if a reboot is pending.</span></span> <span data-ttu-id="5f277-117">Düğüm, DSC dışında yeniden başlatma gerektiriyorsa **xPendingReboot** kaynak kümeleri `$global:DSCMachineStatus` bayrak `1` bekleyen durumu çözümlemek ve bir yeniden başlatmaya zorlanıyor.</span><span class="sxs-lookup"><span data-stu-id="5f277-117">If the Node requires a reboot outside of DSC, the **xPendingReboot** resource sets the `$global:DSCMachineStatus` flag to `1` forcing a reboot and resolving the pending condition.</span></span>

> [!NOTE]
> <span data-ttu-id="5f277-118">Bu bayrak ayarlayarak düğümü yeniden başlatma için LCM'yi herhangi bir DSC kaynağı bildirebilirsiniz `Set-TargetResource` işlevi.</span><span class="sxs-lookup"><span data-stu-id="5f277-118">Any DSC resource can instruct the LCM to reboot the node by setting this flag in the `Set-TargetResource` function.</span></span> <span data-ttu-id="5f277-119">Daha fazla bilgi için [MOF ile özel bir DSC kaynağı yazma](../resources/authoringResourceMOF.md).</span><span class="sxs-lookup"><span data-stu-id="5f277-119">For more information, see [Writing a custom DSC resource with MOF](../resources/authoringResourceMOF.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="5f277-120">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5f277-120">Syntax</span></span>

```
xPendingReboot [String] #ResourceName
{
    Name = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
    [SkipCcmClientSDK = [bool]]
    [SkipComponentBasedServicing = [bool]]
    [SkipPendingComputerRename = [bool]]
    [SkipPendingFileRename = [bool]]
    [SkipWindowsUpdate = [bool]]
}
```

## <a name="properties"></a><span data-ttu-id="5f277-121">Özellikler</span><span class="sxs-lookup"><span data-stu-id="5f277-121">Properties</span></span>

| <span data-ttu-id="5f277-122">Özellik</span><span class="sxs-lookup"><span data-stu-id="5f277-122">Property</span></span> | <span data-ttu-id="5f277-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5f277-123">Description</span></span> |
| --- | --- |
| <span data-ttu-id="5f277-124">Adı</span><span class="sxs-lookup"><span data-stu-id="5f277-124">Name</span></span>| <span data-ttu-id="5f277-125">Kaynak yapılandırması içindeki örnek başına benzersiz olmalıdır, gerekli parametre.</span><span class="sxs-lookup"><span data-stu-id="5f277-125">Required parameter that must be unique per instance of the resource within a configuration.</span></span>|
| <span data-ttu-id="5f277-126">SkipComponentBasedServicing</span><span class="sxs-lookup"><span data-stu-id="5f277-126">SkipComponentBasedServicing</span></span> | <span data-ttu-id="5f277-127">Skip yeniden başlatmalar bileşen tabanlı hizmet bileşeni tarafından tetiklendi.</span><span class="sxs-lookup"><span data-stu-id="5f277-127">Skip reboots triggered by the Component-Based Servicing component.</span></span> |
| <span data-ttu-id="5f277-128">SkipWindowsUpdate</span><span class="sxs-lookup"><span data-stu-id="5f277-128">SkipWindowsUpdate</span></span> | <span data-ttu-id="5f277-129">Skip yeniden başlatmalar Windows Update tarafından tetiklendi.</span><span class="sxs-lookup"><span data-stu-id="5f277-129">Skip reboots triggered by Windows Update.</span></span>|
| <span data-ttu-id="5f277-130">SkipPendingFileRename</span><span class="sxs-lookup"><span data-stu-id="5f277-130">SkipPendingFileRename</span></span> | <span data-ttu-id="5f277-131">Bekleyen dosya yeniden adlandırma yeniden başlatmalar atlayın.</span><span class="sxs-lookup"><span data-stu-id="5f277-131">Skip pending file rename reboots.</span></span> |
| <span data-ttu-id="5f277-132">SkipCcmClientSDK</span><span class="sxs-lookup"><span data-stu-id="5f277-132">SkipCcmClientSDK</span></span> | <span data-ttu-id="5f277-133">Skip yeniden başlatmalar ConfigMgr istemci tarafından tetiklendi.</span><span class="sxs-lookup"><span data-stu-id="5f277-133">Skip reboots triggered by the ConfigMgr client.</span></span> |
| <span data-ttu-id="5f277-134">SkipComputerRename</span><span class="sxs-lookup"><span data-stu-id="5f277-134">SkipComputerRename</span></span> | <span data-ttu-id="5f277-135">Bilgisayar tarafından tetiklenen Atla yeniden adlandırır.</span><span class="sxs-lookup"><span data-stu-id="5f277-135">Skip reboots triggered by Computer renames.</span></span> |
| <span data-ttu-id="5f277-136">PSDSCRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="5f277-136">PSDSCRunAsCredential</span></span> | <span data-ttu-id="5f277-137">V5 desteklenir.</span><span class="sxs-lookup"><span data-stu-id="5f277-137">Supported in v5.</span></span> <span data-ttu-id="5f277-138">Kaynak, belirtilen kullanıcı olarak yürütür.</span><span class="sxs-lookup"><span data-stu-id="5f277-138">Executes the resource as the specified user.</span></span> |
| <span data-ttu-id="5f277-139">dependsOn</span><span class="sxs-lookup"><span data-stu-id="5f277-139">DependsOn</span></span> | <span data-ttu-id="5f277-140">Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5f277-140">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="5f277-141">Örneğin, kaynak yapılandırmasının Kimliğini çalıştırmak istediğiniz bir blok betik ilk ise **ResourceName** ve kendi türünün **ResourceType**, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="5f277-141">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> <span data-ttu-id="5f277-142">Daha fazla bilgi için [DependsOn kullanma](resource-depends-on.md)</span><span class="sxs-lookup"><span data-stu-id="5f277-142">For more information, see [Using DependsOn](resource-depends-on.md)</span></span>|

## <a name="example"></a><span data-ttu-id="5f277-143">Örnek</span><span class="sxs-lookup"><span data-stu-id="5f277-143">Example</span></span>

<span data-ttu-id="5f277-144">Aşağıdaki örnek, Microsoft Exchange kullanarak yükler [xExchange](https://github.com/PowerShell/xExchange) kaynak.</span><span class="sxs-lookup"><span data-stu-id="5f277-144">The following example installs Microsoft Exchange using the [xExchange](https://github.com/PowerShell/xExchange) resource.</span></span>
<span data-ttu-id="5f277-145">Yükleme boyunca **xPendingReboot** kaynak düğümü yeniden başlatma için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5f277-145">Throughout the install, the **xPendingReboot** resource is used to reboot the Node.</span></span>

> [!NOTE]
> <span data-ttu-id="5f277-146">Bu örnek, bir Exchange sunucusunun ormana eklemek için haklarına sahip bir hesabın kimlik gerektirir.</span><span class="sxs-lookup"><span data-stu-id="5f277-146">This example requires the credential of an account that has rights to add an Exchange server to the forest.</span></span> <span data-ttu-id="5f277-147">DSC kimlik bilgilerini kullanarak daha fazla bilgi için bkz: [DSC kimlik bilgilerini işleme](../configurations/configDataCredentials.md)</span><span class="sxs-lookup"><span data-stu-id="5f277-147">For more information on using credentials in DSC, see [Handling Credentials in DSC](../configurations/configDataCredentials.md)</span></span>

```powershell
$ConfigurationData = @{
    AllNodes = @(
        @{
            NodeName                    = '*'
            PSDSCAllowPlainTextPassword = $true
        },
        @{
            NodeName = 'DSCPULL-1'
        }
    )
}

Configuration Example
{
    param
    (
        [Parameter(Mandatory = $true)]
        [System.Management.Automation.PSCredential]
        $ExchangeAdminCredential
    )

    Import-DscResource -Module xExchange
    Import-DscResource -Module xPendingReboot

    Node $AllNodes.NodeName
    {
        # Copy the Exchange setup files locally
        File ExchangeBinaries
        {
            Ensure          = 'Present'
            Type            = 'Directory'
            Recurse         = $true
            SourcePath      = '\\rras-1\Binaries\E15CU6'
            DestinationPath = 'C:\Binaries\E15CU6'
        }

        # Check if a reboot is needed before installing Exchange
        xPendingReboot BeforeExchangeInstall
        {
            Name       = 'BeforeExchangeInstall'
            DependsOn  = '[File]ExchangeBinaries'
        }

        # Do the Exchange install
        xExchInstall InstallExchange
        {
            Path       = 'C:\Binaries\E15CU6\Setup.exe'
            Arguments  = '/mode:Install /role:Mailbox /Iacceptexchangeserverlicenseterms'
            Credential = $ExchangeAdminCredential
            DependsOn  = '[xPendingReboot]BeforeExchangeInstall'
        }

        # See if a reboot is required after installing Exchange
        xPendingReboot AfterExchangeInstall
        {
            Name      = 'AfterExchangeInstall'
            DependsOn = '[xExchInstall]InstallExchange'
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="5f277-148">Bu örnekte, yeniden başlatmalar izin vermek ve bir yeniden başlatma işleminden sonra yapılandırmasına devam etmek için yerel Configuration Manager yapılandırmış olduğunuz varsayılır.</span><span class="sxs-lookup"><span data-stu-id="5f277-148">This example assumes that you have configured your Local Configuration Manager to allow reboots and continue the configuration after a reboot.</span></span>

## <a name="where-to-download"></a><span data-ttu-id="5f277-149">Karşıdan yükleme konumu</span><span class="sxs-lookup"><span data-stu-id="5f277-149">Where to Download</span></span>

<span data-ttu-id="5f277-150">Bu konuda aşağıdaki konumlarda ya da PowerShell Galerisi kullanılarak tarafından kullanılan kaynakları indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5f277-150">You can download the resources used in this topic at the following locations, or by using the PowerShell gallery.</span></span>

- [<span data-ttu-id="5f277-151">xPendingReboot</span><span class="sxs-lookup"><span data-stu-id="5f277-151">xPendingReboot</span></span>](https://github.com/PowerShell/xPendingReboot)
- [<span data-ttu-id="5f277-152">xExchange</span><span class="sxs-lookup"><span data-stu-id="5f277-152">xExchange</span></span>](https://github.com/PowerShell/xExchange)
