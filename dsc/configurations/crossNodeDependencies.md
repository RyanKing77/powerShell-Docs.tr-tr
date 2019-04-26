---
ms.date: 12/12/2018
keywords: DSC, powershell, yapılandırma, Kurulum
title: Çapraz düğüm bağımlılıklarını belirtme
ms.openlocfilehash: 1bdfbd9f8a94809d6bf410eff525e1c877fb6aad
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080212"
---
# <a name="specifying-cross-node-dependencies"></a><span data-ttu-id="71bdb-103">Çapraz düğüm bağımlılıklarını belirtme</span><span class="sxs-lookup"><span data-stu-id="71bdb-103">Specifying cross-node dependencies</span></span>

> <span data-ttu-id="71bdb-104">Uygulama hedefi: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="71bdb-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="71bdb-105">DSC özel kaynaklar sağlayan **WaitForAll**, **WaitForAny**, ve **WaitForSome** kullanılabilecek yapılandırmalarında diğer yapılandırmaları bağımlılıklarını belirtmek için düğümleri.</span><span class="sxs-lookup"><span data-stu-id="71bdb-105">DSC provides special resources, **WaitForAll**, **WaitForAny**, and **WaitForSome** that can be used in configurations to specify dependencies on configurations on other nodes.</span></span> <span data-ttu-id="71bdb-106">Bu kaynakların davranış aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="71bdb-106">The behavior of these resources is as follows:</span></span>

- <span data-ttu-id="71bdb-107">**WaitForAll**: Belirtilen kaynak tanımlanan tüm hedef düğümler üzerinde istenen durumda ise başarılı **NodeName** özelliği.</span><span class="sxs-lookup"><span data-stu-id="71bdb-107">**WaitForAll**: Succeeds if the specified resource is in the desired state on all target nodes defined in the **NodeName** property.</span></span>
- <span data-ttu-id="71bdb-108">**WaitForAny**: Belirtilen kaynak en az bir tanımlanmış hedef düğümler üzerinde istenen durumda ise başarılı **NodeName** özelliği.</span><span class="sxs-lookup"><span data-stu-id="71bdb-108">**WaitForAny**: Succeeds if the specified resource is in the desired state on at least one of the target nodes defined in the **NodeName** property.</span></span>
- <span data-ttu-id="71bdb-109">**WaitForSome**: Belirtir bir **NodeCount** özelliğine ek olarak bir **NodeName** özelliği.</span><span class="sxs-lookup"><span data-stu-id="71bdb-109">**WaitForSome**: Specifies a **NodeCount** property in addition to a **NodeName** property.</span></span> <span data-ttu-id="71bdb-110">Kaynak düğüm sayısı alt sınırı üzerinde istenen durumda ise kaynak başarılı (tarafından belirtilen **NodeCount**) tarafından tanımlanan **NodeName** özelliği.</span><span class="sxs-lookup"><span data-stu-id="71bdb-110">The resource succeeds if the resource is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span>

## <a name="syntax"></a><span data-ttu-id="71bdb-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="71bdb-111">Syntax</span></span>

<span data-ttu-id="71bdb-112">**WaitForAll** ve **WaitForAny** aynı sözdizimini kaynakları paylaşır.</span><span class="sxs-lookup"><span data-stu-id="71bdb-112">The **WaitForAll** and **WaitForAny** resources share the same syntax.</span></span> <span data-ttu-id="71bdb-113">Değiştirin \<ResourceType\> aşağıdaki örnekte ya da ile **WaitForAny** veya **WaitForAll**.</span><span class="sxs-lookup"><span data-stu-id="71bdb-113">Replace \<ResourceType\> in the example below with either **WaitForAny** or **WaitForAll**.</span></span>
<span data-ttu-id="71bdb-114">Gibi **DependsOn** anahtar sözcüğü, adı "[ResourceType] ResourceName" olarak biçimlendirmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="71bdb-114">Like the **DependsOn** keyword, you will need to format the name as "[ResourceType]ResourceName".</span></span> <span data-ttu-id="71bdb-115">Kaynak için ayrı bir aitse [yapılandırma](configurations.md), dahil **ConfigurationName** biçimlendirilen dizesinde "[ResourceType] ResourceName:: [ConfigurationName]:: [ConfigurationName]".</span><span class="sxs-lookup"><span data-stu-id="71bdb-115">If the resource belongs to a separate [Configuration](configurations.md), include the **ConfigurationName** in the formatted string "[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]".</span></span> <span data-ttu-id="71bdb-116">**NodeName** bilgisayar veya üzerinde geçerli kaynak beklemesi gereken düğümü.</span><span class="sxs-lookup"><span data-stu-id="71bdb-116">The **NodeName** is the computer, or Node, on which the current resource should wait.</span></span>

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

<span data-ttu-id="71bdb-117">**WaitForSome** kaynak yukarıdaki örneğe benzer bir sözdizimi vardır, ancak ekler **NodeCount** anahtarı.</span><span class="sxs-lookup"><span data-stu-id="71bdb-117">The **WaitForSome** resource has a similar syntax to the example above, but adds the **NodeCount** key.</span></span> <span data-ttu-id="71bdb-118">**NodeCount** kaç düğümleri geçerli kaynak beklemesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="71bdb-118">The **NodeCount** indicates how many Nodes the current resource should wait on.</span></span>

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

<span data-ttu-id="71bdb-119">Tüm **WaitForXXXX** aşağıdaki söz dizimini anahtarlarını paylaşın.</span><span class="sxs-lookup"><span data-stu-id="71bdb-119">All **WaitForXXXX** share the following syntax keys.</span></span>

<span data-ttu-id="71bdb-120">|  Özellik |  Açıklama || RetryIntervalSec | Yeniden denemeden önce saniye sayısı.</span><span class="sxs-lookup"><span data-stu-id="71bdb-120">|  Property  |  Description   | | RetryIntervalSec| The number of seconds before retrying.</span></span> <span data-ttu-id="71bdb-121">En az 1 olmalıdır. | | RetryCount | Yeniden deneme sayısı. | | ThrottleLimit | Aynı anda bağlanmak makineleri sayısı.</span><span class="sxs-lookup"><span data-stu-id="71bdb-121">Minimum is 1.| | RetryCount| The maximum number of times to retry.| | ThrottleLimit| Number of machines to connect simultaneously.</span></span> <span data-ttu-id="71bdb-122">Varsayılan değer `New-CimSession` varsayılan. | | DependsOn | Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="71bdb-122">Default is `New-CimSession` default.| | DependsOn | Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="71bdb-123">Daha fazla bilgi için [DependsOn](resource-depends-on.md)|| PsDscRunAsCredential | Bkz: [kullanıcı kimlik bilgileriyle DSC kullanma](./runAsUser.md) |</span><span class="sxs-lookup"><span data-stu-id="71bdb-123">For more information, see [DependsOn](resource-depends-on.md)| | PsDscRunAsCredential | See [Using DSC with User Credentials](./runAsUser.md) |</span></span>


## <a name="using-waitforxxxx-resources"></a><span data-ttu-id="71bdb-124">WaitForXXXX kaynakları kullanma</span><span class="sxs-lookup"><span data-stu-id="71bdb-124">Using WaitForXXXX resources</span></span>

<span data-ttu-id="71bdb-125">Her **WaitForXXXX** belirtilen düğümde tamamlamak belirtilen kaynaklar için kaynak bekler.</span><span class="sxs-lookup"><span data-stu-id="71bdb-125">Each **WaitForXXXX** resource waits for the specified resources to complete on the specified Node.</span></span> <span data-ttu-id="71bdb-126">Diğer kaynakları aynı yapılandırmayı, böylece *bağımlı* **WaitForXXXX** kaynak kullanarak **DependsOn** anahtarı.</span><span class="sxs-lookup"><span data-stu-id="71bdb-126">Other resources in the same Configuration can then *depend on* the **WaitForXXXX** resource using the **DependsOn** key.</span></span>

<span data-ttu-id="71bdb-127">Örneğin, aşağıdaki yapılandırmasında, hedef düğüm bekliyor **xADDomain** bitmesi için kaynak **MyDC** düğüm sayısı 30 ile yeniden deneme sayısı, 15 saniyelik aralıklarla önce Hedef düğüm, etki alanına katılmasını sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="71bdb-127">For example, in the following configuration, the target node is waiting for the **xADDomain** resource to finish on the **MyDC** node with maximum number of 30 retries, at 15-second intervals, before the target node can join the domain.</span></span>

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

<span data-ttu-id="71bdb-128">Yapılandırmayı derlemek, iki ".mof" dosya üretilir.</span><span class="sxs-lookup"><span data-stu-id="71bdb-128">When you compile the Configuration, two ".mof" files are generated.</span></span> <span data-ttu-id="71bdb-129">Kullanarak hedef düğümler için her iki ".mof" dosyalara [Başlat-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet'i</span><span class="sxs-lookup"><span data-stu-id="71bdb-129">Apply both ".mof" files to the target Nodes using the [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet</span></span>

><span data-ttu-id="71bdb-130">**Not:** Varsayılan WaitForXXX kaynakları bir kez deneyin ve sonra başarısız.</span><span class="sxs-lookup"><span data-stu-id="71bdb-130">**Note:** By default the WaitForXXX resources try one time and then fail.</span></span> <span data-ttu-id="71bdb-131">Gerekli olmamasına karşın, genellikle belirtmek istersiniz bir **RetryCount** ve **RetryIntervalSec**.</span><span class="sxs-lookup"><span data-stu-id="71bdb-131">Although it is not required, you will typically want to specify a **RetryCount** and **RetryIntervalSec**.</span></span>

## <a name="see-also"></a><span data-ttu-id="71bdb-132">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="71bdb-132">See Also</span></span>

- [<span data-ttu-id="71bdb-133">DSC yapılandırmaları</span><span class="sxs-lookup"><span data-stu-id="71bdb-133">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="71bdb-134">Kaynak bağımlılıkları kullanın</span><span class="sxs-lookup"><span data-stu-id="71bdb-134">Use Resource Dependencies</span></span>](resource-depends-on.md)
- [<span data-ttu-id="71bdb-135">DSC kaynakları</span><span class="sxs-lookup"><span data-stu-id="71bdb-135">DSC Resources</span></span>](../resources/resources.md)
- [<span data-ttu-id="71bdb-136">Yerel Configuration Manager'ı yapılandırma</span><span class="sxs-lookup"><span data-stu-id="71bdb-136">Configuring The Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)
