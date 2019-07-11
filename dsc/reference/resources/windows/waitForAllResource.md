---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC WaitForAll kaynak
ms.openlocfilehash: c1125b7c5b68b9b520ed052800b6a2abf4e53b85
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726870"
---
# <a name="dsc-waitforall-resource"></a><span data-ttu-id="1b385-103">DSC WaitForAll kaynak</span><span class="sxs-lookup"><span data-stu-id="1b385-103">DSC WaitForAll Resource</span></span>

> <span data-ttu-id="1b385-104">Şunun için geçerlidir: Windows PowerShell 5.0 ve üzeri</span><span class="sxs-lookup"><span data-stu-id="1b385-104">Applies To: Windows PowerShell 5.0 and later</span></span>

<span data-ttu-id="1b385-105">**WaitForAll** Desired State Configuration ' nı (DSC) kaynak, bir düğüm bloğunda içinde kullanılabilir bir [DSC Yapılandırması](../../../configurations/configurations.md) diğer düğümlerde yapılandırmalarında bağımlılıklarını belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="1b385-105">The **WaitForAll** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](../../../configurations/configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="1b385-106">Bu kaynak tarafından belirtilen kaynağı, başarılı **ResourceName** özelliği içinde tanımlanan tüm hedef düğümler üzerinde istenen durumda **NodeName** özelliği.</span><span class="sxs-lookup"><span data-stu-id="1b385-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on all target nodes defined in the **NodeName** property.</span></span>

> [!NOTE]
> <span data-ttu-id="1b385-107">**WaitForAll** kaynak diğer düğümlerinin durumunu denetlemek için Windows Uzaktan Yönetimi kullanır.</span><span class="sxs-lookup"><span data-stu-id="1b385-107">**WaitForAll** resource uses Windows Remote Management to check the state of other Nodes.</span></span>
> <span data-ttu-id="1b385-108">WinRM bağlantı noktası ve güvenlik gereksinimleri hakkında daha fazla bilgi için bkz. [PowerShell uzaktan iletişim güvenlik konuları](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="1b385-108">For more information about port and security requirements for WinRM, see [PowerShell Remoting Security Considerations](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span></span>

## <a name="syntax"></a><span data-ttu-id="1b385-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1b385-109">Syntax</span></span>

```
WaitForAll [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    [ RetryIntervalSec = [Uint64] ]
    [ RetryCount = [Uint32] ]
    [ ThrottleLimit = [Uint32]]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="1b385-110">Özellikler</span><span class="sxs-lookup"><span data-stu-id="1b385-110">Properties</span></span>

|  <span data-ttu-id="1b385-111">Özellik</span><span class="sxs-lookup"><span data-stu-id="1b385-111">Property</span></span>  |  <span data-ttu-id="1b385-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1b385-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="1b385-113">resourceName</span><span class="sxs-lookup"><span data-stu-id="1b385-113">ResourceName</span></span>| <span data-ttu-id="1b385-114">Bağımlı kaynak adı.</span><span class="sxs-lookup"><span data-stu-id="1b385-114">The resource name to depend on.</span></span> <span data-ttu-id="1b385-115">Bu kaynak farklı bir yapılandırmaya aitse, adı olarak Biçimlendir "[__ResourceType__]__ResourceName__:: [__ConfigurationName__]:: [ __ConfigurationName__] "</span><span class="sxs-lookup"><span data-stu-id="1b385-115">If this resource belongs to a different configuration, format the name as "[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]"</span></span>|
| <span data-ttu-id="1b385-116">nodeName</span><span class="sxs-lookup"><span data-stu-id="1b385-116">NodeName</span></span>| <span data-ttu-id="1b385-117">Hedef düğümleri kaynak bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="1b385-117">The target nodes of the resource to depend on.</span></span>|
| <span data-ttu-id="1b385-118">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="1b385-118">RetryIntervalSec</span></span>| <span data-ttu-id="1b385-119">Yeniden denemeden önce saniye sayısı.</span><span class="sxs-lookup"><span data-stu-id="1b385-119">The number of seconds before retrying.</span></span> <span data-ttu-id="1b385-120">Minimum is 1.</span><span class="sxs-lookup"><span data-stu-id="1b385-120">Minimum is 1.</span></span>|
| <span data-ttu-id="1b385-121">RetryCount</span><span class="sxs-lookup"><span data-stu-id="1b385-121">RetryCount</span></span>| <span data-ttu-id="1b385-122">Yeniden deneme sayısı.</span><span class="sxs-lookup"><span data-stu-id="1b385-122">The maximum number of times to retry.</span></span>|
| <span data-ttu-id="1b385-123">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="1b385-123">ThrottleLimit</span></span>| <span data-ttu-id="1b385-124">Aynı anda bağlanmak makineleri sayısı.</span><span class="sxs-lookup"><span data-stu-id="1b385-124">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="1b385-125">Yeni-cimsession varsayılan varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="1b385-125">Default is new-cimsession default.</span></span>|
| <span data-ttu-id="1b385-126">dependsOn</span><span class="sxs-lookup"><span data-stu-id="1b385-126">DependsOn</span></span> | <span data-ttu-id="1b385-127">Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="1b385-127">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="1b385-128">Örneğin, kaynak yapılandırmasının Kimliğini çalıştırmak istediğiniz bir blok betik ilk ise __ResourceName__ ve kendi türünün __ResourceType__, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="1b385-128">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="1b385-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="1b385-129">Example</span></span>

<span data-ttu-id="1b385-130">Bu kaynağı kullanmaya ilişkin bir örnek için bkz: [çapraz düğüm bağımlılıklarını belirtme](../../../configurations/crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="1b385-130">For an example of how to use this resource, see [Specifying cross-node dependencies](../../../configurations/crossNodeDependencies.md)</span></span>
