---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC WaitForAny kaynak
ms.openlocfilehash: 55869f665837b422c006f4cfb3e91366fac60362
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076842"
---
# <a name="dsc-waitforany-resource"></a><span data-ttu-id="bab86-103">DSC WaitForAny kaynak</span><span class="sxs-lookup"><span data-stu-id="bab86-103">DSC WaitForAny Resource</span></span>

> <span data-ttu-id="bab86-104">Uygulama hedefi: Windows PowerShell 5.1 ve üzeri</span><span class="sxs-lookup"><span data-stu-id="bab86-104">Applies To: Windows PowerShell 5.1 and later</span></span>

<span data-ttu-id="bab86-105">**WaitForAny** Desired State Configuration ' nı (DSC) kaynak, bir düğüm bloğunda içinde kullanılabilir bir [DSC Yapılandırması](../../../configurations/configurations.md) diğer düğümlerde yapılandırmalarında bağımlılıklarını belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="bab86-105">The **WaitForAny** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](../../../configurations/configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="bab86-106">Bu kaynak tarafından belirtilen kaynağı, başarılı **ResourceName** özelliği içinde tanımlanan tüm hedef düğümler üzerinde istenen durumda **NodeName** özelliği.</span><span class="sxs-lookup"><span data-stu-id="bab86-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on any target nodes defined in the **NodeName** property.</span></span>


## <a name="syntax"></a><span data-ttu-id="bab86-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bab86-107">Syntax</span></span>

```
WaitForAny [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    [ RetryIntervalSec = [Uint64] ]
    [ RetryCount = [Uint32] ]
    [ ThrottleLimit = [Uint32]]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="bab86-108">Özellikler</span><span class="sxs-lookup"><span data-stu-id="bab86-108">Properties</span></span>

|  <span data-ttu-id="bab86-109">Özellik</span><span class="sxs-lookup"><span data-stu-id="bab86-109">Property</span></span>  |  <span data-ttu-id="bab86-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bab86-110">Description</span></span>   |
|---|---|
| <span data-ttu-id="bab86-111">resourceName</span><span class="sxs-lookup"><span data-stu-id="bab86-111">ResourceName</span></span>| <span data-ttu-id="bab86-112">Bağımlı kaynak adı.</span><span class="sxs-lookup"><span data-stu-id="bab86-112">The resource name to depend on.</span></span> <span data-ttu-id="bab86-113">Bu kaynak farklı bir yapılandırmaya aitse, adı olarak Biçimlendir "[__ResourceType__]__ResourceName__:: [__ConfigurationName__]:: [ __ConfigurationName__] "</span><span class="sxs-lookup"><span data-stu-id="bab86-113">If this resource belongs to a different configuration, format the name as "[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]"</span></span>|
| <span data-ttu-id="bab86-114">nodeName</span><span class="sxs-lookup"><span data-stu-id="bab86-114">NodeName</span></span>| <span data-ttu-id="bab86-115">Hedef düğümleri kaynak bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="bab86-115">The target nodes of the resource to depend on.</span></span>|
| <span data-ttu-id="bab86-116">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="bab86-116">RetryIntervalSec</span></span>| <span data-ttu-id="bab86-117">Yeniden denemeden önce saniye sayısı.</span><span class="sxs-lookup"><span data-stu-id="bab86-117">The number of seconds before retrying.</span></span> <span data-ttu-id="bab86-118">Minimum is 1.</span><span class="sxs-lookup"><span data-stu-id="bab86-118">Minimum is 1.</span></span>|
| <span data-ttu-id="bab86-119">RetryCount</span><span class="sxs-lookup"><span data-stu-id="bab86-119">RetryCount</span></span>| <span data-ttu-id="bab86-120">Yeniden deneme sayısı.</span><span class="sxs-lookup"><span data-stu-id="bab86-120">The maximum number of times to retry.</span></span>|
| <span data-ttu-id="bab86-121">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="bab86-121">ThrottleLimit</span></span>| <span data-ttu-id="bab86-122">Aynı anda bağlanmak makineleri sayısı.</span><span class="sxs-lookup"><span data-stu-id="bab86-122">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="bab86-123">Yeni-cimsession varsayılan varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="bab86-123">Default is new-cimsession default.</span></span>|
| <span data-ttu-id="bab86-124">dependsOn</span><span class="sxs-lookup"><span data-stu-id="bab86-124">DependsOn</span></span> | <span data-ttu-id="bab86-125">Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="bab86-125">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="bab86-126">Örneğin, kaynak yapılandırmasının Kimliğini çalıştırmak istediğiniz bir blok betik ilk ise __ResourceName__ ve kendi türünün __ResourceType__, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="bab86-126">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="bab86-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="bab86-127">Example</span></span>

<span data-ttu-id="bab86-128">Bu kaynağı kullanmaya ilişkin bir örnek için bkz: [çapraz düğüm bağımlılıklarını belirtme](../../../configurations/crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="bab86-128">For an example of how to use this resource, see [Specifying cross-node dependencies](../../../configurations/crossNodeDependencies.md)</span></span>
