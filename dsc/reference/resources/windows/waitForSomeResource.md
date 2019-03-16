---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC WaitForSome kaynak
ms.openlocfilehash: 888da1810f0a9233579bad5eef8d5dd556947c61
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059465"
---
# <a name="dsc-waitforsome-resource"></a><span data-ttu-id="2238d-103">DSC WaitForSome kaynak</span><span class="sxs-lookup"><span data-stu-id="2238d-103">DSC WaitForSome Resource</span></span>

> <span data-ttu-id="2238d-104">Şunun için geçerlidir: Windows PowerShell 5.0 ve üzeri</span><span class="sxs-lookup"><span data-stu-id="2238d-104">Applies To: Windows PowerShell 5.0 and later</span></span>

<span data-ttu-id="2238d-105">**WaitForSome** Desired State Configuration ' nı (DSC) kaynak, bir düğüm bloğunda içinde kullanılabilir bir [DSC Yapılandırması](../../../configurations/configurations.md) diğer düğümlerde yapılandırmalarında bağımlılıklarını belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="2238d-105">The **WaitForSome** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](../../../configurations/configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="2238d-106">Bu kaynak tarafından belirtilen kaynağı, başarılı **ResourceName** özelliktir istenen durumda düğüm sayısı alt sınırı (tarafından belirtilen **NodeCount**) tarafından tanımlanan **NodeName**  özelliği.</span><span class="sxs-lookup"><span data-stu-id="2238d-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span>


## <a name="syntax"></a><span data-ttu-id="2238d-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2238d-107">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="2238d-108">Özellikler</span><span class="sxs-lookup"><span data-stu-id="2238d-108">Properties</span></span>

|  <span data-ttu-id="2238d-109">Özellik</span><span class="sxs-lookup"><span data-stu-id="2238d-109">Property</span></span>  |  <span data-ttu-id="2238d-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2238d-110">Description</span></span>   |
|---|---|
| <span data-ttu-id="2238d-111">NodeCount</span><span class="sxs-lookup"><span data-stu-id="2238d-111">NodeCount</span></span>| <span data-ttu-id="2238d-112">Başarılı olması bu kaynak için istenen durumda olması gereken düğüm sayısı alt sınırı.</span><span class="sxs-lookup"><span data-stu-id="2238d-112">The minimum number of nodes that must be in the desired state for this resource to succeed.</span></span>|
| <span data-ttu-id="2238d-113">nodeName</span><span class="sxs-lookup"><span data-stu-id="2238d-113">NodeName</span></span>| <span data-ttu-id="2238d-114">Hedef düğümleri kaynak bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="2238d-114">The target nodes of the resource to depend on.</span></span>|
| <span data-ttu-id="2238d-115">resourceName</span><span class="sxs-lookup"><span data-stu-id="2238d-115">ResourceName</span></span>| <span data-ttu-id="2238d-116">Bağımlı kaynak adı.</span><span class="sxs-lookup"><span data-stu-id="2238d-116">The resource name to depend on.</span></span> <span data-ttu-id="2238d-117">Bu kaynak farklı bir yapılandırmaya aitse, adı olarak Biçimlendir "[__ResourceType__]__ResourceName__:: [__ConfigurationName__]:: [ __ConfigurationName__] "</span><span class="sxs-lookup"><span data-stu-id="2238d-117">If this resource belongs to a different configuration, format the name as "[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]"</span></span>|
| <span data-ttu-id="2238d-118">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="2238d-118">RetryIntervalSec</span></span>| <span data-ttu-id="2238d-119">Yeniden denemeden önce saniye sayısı.</span><span class="sxs-lookup"><span data-stu-id="2238d-119">The number of seconds before retrying.</span></span> <span data-ttu-id="2238d-120">Minimum is 1.</span><span class="sxs-lookup"><span data-stu-id="2238d-120">Minimum is 1.</span></span>|
| <span data-ttu-id="2238d-121">RetryCount</span><span class="sxs-lookup"><span data-stu-id="2238d-121">RetryCount</span></span>| <span data-ttu-id="2238d-122">Yeniden deneme sayısı.</span><span class="sxs-lookup"><span data-stu-id="2238d-122">The maximum number of times to retry.</span></span>|
| <span data-ttu-id="2238d-123">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="2238d-123">ThrottleLimit</span></span>| <span data-ttu-id="2238d-124">Aynı anda bağlanmak makineleri sayısı.</span><span class="sxs-lookup"><span data-stu-id="2238d-124">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="2238d-125">Yeni-cimsession varsayılan varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="2238d-125">Default is new-cimsession default.</span></span>|
| <span data-ttu-id="2238d-126">dependsOn</span><span class="sxs-lookup"><span data-stu-id="2238d-126">DependsOn</span></span> | <span data-ttu-id="2238d-127">Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="2238d-127">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="2238d-128">Örneğin, kaynak yapılandırmasının Kimliğini çalıştırmak istediğiniz bir blok betik ilk ise __ResourceName__ ve kendi türünün __ResourceType__, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="2238d-128">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="2238d-129">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="2238d-129">PsDscRunAsCredential</span></span> | <span data-ttu-id="2238d-130">Bkz: [kullanıcı kimlik bilgileriyle DSC kullanma](https://docs.microsoft.com/powershell/dsc/runasuser)</span><span class="sxs-lookup"><span data-stu-id="2238d-130">See [Using DSC with User Credentials](https://docs.microsoft.com/powershell/dsc/runasuser)</span></span> |

## <a name="example"></a><span data-ttu-id="2238d-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="2238d-131">Example</span></span>

<span data-ttu-id="2238d-132">Bu kaynağı kullanmaya ilişkin bir örnek için bkz: [çapraz düğüm bağımlılıklarını belirtme](../../../configurations/crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="2238d-132">For an example of how to use this resource, see [Specifying cross-node dependencies](../../../configurations/crossNodeDependencies.md)</span></span>
