---
ms.date: 12/12/2018
keywords: DSC, powershell, yapılandırma, Kurulum
title: Çapraz düğüm bağımlılıklarını belirtme
ms.openlocfilehash: 62e553d894897ae1908745c2788b7b7b9cbe50ff
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734677"
---
# <a name="specifying-cross-node-dependencies"></a><span data-ttu-id="6be3f-103">Çapraz düğüm bağımlılıklarını belirtme</span><span class="sxs-lookup"><span data-stu-id="6be3f-103">Specifying cross-node dependencies</span></span>

> <span data-ttu-id="6be3f-104">Şunun için geçerlidir: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="6be3f-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="6be3f-105">DSC özel kaynaklar sağlayan **WaitForAll**, **WaitForAny**, ve **WaitForSome** kullanılabilecek yapılandırmalarında diğer yapılandırmaları bağımlılıklarını belirtmek için düğümleri.</span><span class="sxs-lookup"><span data-stu-id="6be3f-105">DSC provides special resources, **WaitForAll**, **WaitForAny**, and **WaitForSome** that can be used in configurations to specify dependencies on configurations on other nodes.</span></span> <span data-ttu-id="6be3f-106">Bu kaynakların davranış aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="6be3f-106">The behavior of these resources is as follows:</span></span>

- <span data-ttu-id="6be3f-107">**WaitForAll**: Belirtilen kaynak tanımlanan tüm hedef düğümler üzerinde istenen durumda ise başarılı **NodeName** özelliği.</span><span class="sxs-lookup"><span data-stu-id="6be3f-107">**WaitForAll**: Succeeds if the specified resource is in the desired state on all target nodes defined in the **NodeName** property.</span></span>
- <span data-ttu-id="6be3f-108">**WaitForAny**: Belirtilen kaynak en az bir tanımlanmış hedef düğümler üzerinde istenen durumda ise başarılı **NodeName** özelliği.</span><span class="sxs-lookup"><span data-stu-id="6be3f-108">**WaitForAny**: Succeeds if the specified resource is in the desired state on at least one of the target nodes defined in the **NodeName** property.</span></span>
- <span data-ttu-id="6be3f-109">**WaitForSome**: Belirtir bir **NodeCount** özelliğine ek olarak bir **NodeName** özelliği.</span><span class="sxs-lookup"><span data-stu-id="6be3f-109">**WaitForSome**: Specifies a **NodeCount** property in addition to a **NodeName** property.</span></span> <span data-ttu-id="6be3f-110">Kaynak düğüm sayısı alt sınırı üzerinde istenen durumda ise kaynak başarılı (tarafından belirtilen **NodeCount**) tarafından tanımlanan **NodeName** özelliği.</span><span class="sxs-lookup"><span data-stu-id="6be3f-110">The resource succeeds if the resource is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span>

## <a name="syntax"></a><span data-ttu-id="6be3f-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6be3f-111">Syntax</span></span>

<span data-ttu-id="6be3f-112">**WaitForAll** ve **WaitForAny** aynı sözdizimini kaynakları paylaşır.</span><span class="sxs-lookup"><span data-stu-id="6be3f-112">The **WaitForAll** and **WaitForAny** resources share the same syntax.</span></span> <span data-ttu-id="6be3f-113">Değiştirin \<ResourceType\> aşağıdaki örnekte ya da ile **WaitForAny** veya **WaitForAll**.</span><span class="sxs-lookup"><span data-stu-id="6be3f-113">Replace \<ResourceType\> in the example below with either **WaitForAny** or **WaitForAll**.</span></span>
<span data-ttu-id="6be3f-114">Gibi **DependsOn** anahtar sözcüğü, adı "[ResourceType] ResourceName" olarak biçimlendirmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="6be3f-114">Like the **DependsOn** keyword, you will need to format the name as "[ResourceType]ResourceName".</span></span> <span data-ttu-id="6be3f-115">Kaynak için ayrı bir aitse [yapılandırma](configurations.md), dahil **ConfigurationName** biçimlendirilen dizesinde "[ResourceType] ResourceName:: [ConfigurationName]:: [ConfigurationName]".</span><span class="sxs-lookup"><span data-stu-id="6be3f-115">If the resource belongs to a separate [Configuration](configurations.md), include the **ConfigurationName** in the formatted string "[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]".</span></span> <span data-ttu-id="6be3f-116">**NodeName** bilgisayar veya üzerinde geçerli kaynak beklemesi gereken düğümü.</span><span class="sxs-lookup"><span data-stu-id="6be3f-116">The **NodeName** is the computer, or Node, on which the current resource should wait.</span></span>

```
<ResourceType> [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential]]
    [ RetryCount = [Uint32] ]
    [ RetryIntervalSec = [Uint64] ]
    [ ThrottleLimit = [Uint32]]
}
```

<span data-ttu-id="6be3f-117">**WaitForSome** kaynak yukarıdaki örneğe benzer bir sözdizimi vardır, ancak ekler **NodeCount** anahtarı.</span><span class="sxs-lookup"><span data-stu-id="6be3f-117">The **WaitForSome** resource has a similar syntax to the example above, but adds the **NodeCount** key.</span></span> <span data-ttu-id="6be3f-118">**NodeCount** kaç düğümleri geçerli kaynak beklemesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="6be3f-118">The **NodeCount** indicates how many Nodes the current resource should wait on.</span></span>

```
WaitForSome [String] #ResourceName
{
    NodeCount = [UInt32]
    NodeName = [string[]]
    ResourceName = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
    [RetryCount = [UInt32]]
    [RetryIntervalSec = [UInt64]]
    [ThrottleLimit = [UInt32]]
}
```

<span data-ttu-id="6be3f-119">Tüm **WaitForXXXX** aşağıdaki söz dizimini anahtarlarını paylaşın.</span><span class="sxs-lookup"><span data-stu-id="6be3f-119">All **WaitForXXXX** share the following syntax keys.</span></span>

|<span data-ttu-id="6be3f-120">Özellik</span><span class="sxs-lookup"><span data-stu-id="6be3f-120">Property</span></span>|  <span data-ttu-id="6be3f-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6be3f-121">Description</span></span>   |
|---------|---------------------|
| <span data-ttu-id="6be3f-122">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="6be3f-122">RetryIntervalSec</span></span>| <span data-ttu-id="6be3f-123">Yeniden denemeden önce saniye sayısı.</span><span class="sxs-lookup"><span data-stu-id="6be3f-123">The number of seconds before retrying.</span></span> <span data-ttu-id="6be3f-124">Minimum is 1.</span><span class="sxs-lookup"><span data-stu-id="6be3f-124">Minimum is 1.</span></span>|
| <span data-ttu-id="6be3f-125">RetryCount</span><span class="sxs-lookup"><span data-stu-id="6be3f-125">RetryCount</span></span>| <span data-ttu-id="6be3f-126">Yeniden deneme sayısı.</span><span class="sxs-lookup"><span data-stu-id="6be3f-126">The maximum number of times to retry.</span></span>|
| <span data-ttu-id="6be3f-127">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="6be3f-127">ThrottleLimit</span></span>| <span data-ttu-id="6be3f-128">Aynı anda bağlanmak makineleri sayısı.</span><span class="sxs-lookup"><span data-stu-id="6be3f-128">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="6be3f-129">Varsayılan değer `New-CimSession` varsayılan.</span><span class="sxs-lookup"><span data-stu-id="6be3f-129">Default is `New-CimSession` default.</span></span>|
| <span data-ttu-id="6be3f-130">dependsOn</span><span class="sxs-lookup"><span data-stu-id="6be3f-130">DependsOn</span></span> | <span data-ttu-id="6be3f-131">Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="6be3f-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="6be3f-132">Daha fazla bilgi için [DependsOn](resource-depends-on.md)</span><span class="sxs-lookup"><span data-stu-id="6be3f-132">For more information, see [DependsOn](resource-depends-on.md)</span></span>|
| <span data-ttu-id="6be3f-133">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="6be3f-133">PsDscRunAsCredential</span></span> | <span data-ttu-id="6be3f-134">Bkz: [kullanıcı kimlik bilgileriyle DSC kullanma](./runAsUser.md)</span><span class="sxs-lookup"><span data-stu-id="6be3f-134">See [Using DSC with User Credentials](./runAsUser.md)</span></span> |

## <a name="using-waitforxxxx-resources"></a><span data-ttu-id="6be3f-135">WaitForXXXX kaynakları kullanma</span><span class="sxs-lookup"><span data-stu-id="6be3f-135">Using WaitForXXXX resources</span></span>

<span data-ttu-id="6be3f-136">Her **WaitForXXXX** belirtilen düğümde tamamlamak belirtilen kaynaklar için kaynak bekler.</span><span class="sxs-lookup"><span data-stu-id="6be3f-136">Each **WaitForXXXX** resource waits for the specified resources to complete on the specified Node.</span></span>
<span data-ttu-id="6be3f-137">Diğer kaynakları aynı yapılandırmayı, böylece *bağımlı* **WaitForXXXX** kaynak kullanarak **DependsOn** anahtarı.</span><span class="sxs-lookup"><span data-stu-id="6be3f-137">Other resources in the same Configuration can then *depend on* the **WaitForXXXX** resource using the **DependsOn** key.</span></span>

<span data-ttu-id="6be3f-138">Örneğin, aşağıdaki yapılandırmasında, hedef düğüm bekliyor **xADDomain** bitmesi için kaynak **MyDC** düğüm sayısı 30 ile yeniden deneme sayısı, 15 saniyelik aralıklarla önce Hedef düğüm, etki alanına katılmasını sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6be3f-138">For example, in the following configuration, the target node is waiting for the **xADDomain** resource to finish on the **MyDC** node with maximum number of 30 retries, at 15-second intervals, before the target node can join the domain.</span></span>

<span data-ttu-id="6be3f-139">Varsayılan olarak **WaitForXXX** kaynakları bir kez deneyin ve sonra başarısız.</span><span class="sxs-lookup"><span data-stu-id="6be3f-139">By default the **WaitForXXX** resources try one time and then fail.</span></span> <span data-ttu-id="6be3f-140">Gerekli olmamasına karşın, genellikle belirtmek istersiniz bir **RetryCount** ve **RetryIntervalSec**.</span><span class="sxs-lookup"><span data-stu-id="6be3f-140">Although it is not required, you will typically want to specify a **RetryCount** and **RetryIntervalSec**.</span></span>

```powershell
Configuration JoinDomain
{
    Import-DscResource -Module xComputerManagement, xActiveDirectory

    Node myDC
    {
        WindowsFeature InstallAD
        {
            Ensure = 'Present'
            Name = 'AD-Domain-Services'
        }

        xADDomain NewDomain
        {
            DomainName = 'Contoso.com'
            DomainAdministratorCredential = (Get-Credential)
            SafemodeAdministratorPassword = (Get-Credential)
            DatabasePath = "C:\Windows\NTDS"
            LogPath = "C:\Windows\NTDS"
            SysvolPath = "C:\Windows\Sysvol"
        }
    }

    Node myDomainJoinedServer
    {
        WaitForAll DC
        {
            ResourceName      = '[xADDomain]NewDomain'
            NodeName          = 'MyDC'
            RetryIntervalSec  = 15
            RetryCount        = 30
        }

        xComputer JoinDomain
        {
            Name             = 'myPC'
            DomainName       = 'Contoso.com'
            Credential       = (Get-Credential)
            DependsOn        ='[WaitForAll]DC'
        }
    }
}
```

<span data-ttu-id="6be3f-141">Yapılandırmayı derlemek, iki ".mof" dosya üretilir.</span><span class="sxs-lookup"><span data-stu-id="6be3f-141">When you compile the Configuration, two ".mof" files are generated.</span></span> <span data-ttu-id="6be3f-142">Kullanarak hedef düğümler için her iki ".mof" dosyalara [Başlat-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet'i</span><span class="sxs-lookup"><span data-stu-id="6be3f-142">Apply both ".mof" files to the target Nodes using the [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet</span></span>

> [!NOTE]
> <span data-ttu-id="6be3f-143">**WaitForXXX** kaynakları diğer düğümlerinin durumunu denetlemek için Windows Uzaktan Yönetimi kullanın.</span><span class="sxs-lookup"><span data-stu-id="6be3f-143">**WaitForXXX** resources use Windows Remote Management to check the state of other Nodes.</span></span>
> <span data-ttu-id="6be3f-144">WinRM bağlantı noktası ve güvenlik gereksinimleri hakkında daha fazla bilgi için bkz. [PowerShell uzaktan iletişim güvenlik konuları](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="6be3f-144">For more information about port and security requirements for WinRM, see [PowerShell Remoting Security Considerations](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span></span>

## <a name="see-also"></a><span data-ttu-id="6be3f-145">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="6be3f-145">See Also</span></span>

- [<span data-ttu-id="6be3f-146">DSC yapılandırmaları</span><span class="sxs-lookup"><span data-stu-id="6be3f-146">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="6be3f-147">Kaynak bağımlılıkları kullanın</span><span class="sxs-lookup"><span data-stu-id="6be3f-147">Use Resource Dependencies</span></span>](resource-depends-on.md)
- [<span data-ttu-id="6be3f-148">DSC kaynakları</span><span class="sxs-lookup"><span data-stu-id="6be3f-148">DSC Resources</span></span>](../resources/resources.md)
- [<span data-ttu-id="6be3f-149">Yerel Configuration Manager'ı yapılandırma</span><span class="sxs-lookup"><span data-stu-id="6be3f-149">Configuring The Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)
