---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, yapılandırma, Kur
title: DSC WaitForSome kaynağı
ms.openlocfilehash: 8132b584fad350530f6fc80175980881a399ac2e
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-waitforsome-resource"></a><span data-ttu-id="a6392-103">DSC WaitForSome kaynağı</span><span class="sxs-lookup"><span data-stu-id="a6392-103">DSC WaitForSome Resource</span></span>

> <span data-ttu-id="a6392-104">İçin geçerlidir: Windows PowerShell 5.0 ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="a6392-104">Applies To: Windows PowerShell 5.0 and later</span></span>

<span data-ttu-id="a6392-105">**WaitForAny** istenen durum Yapılandırması'nı (DSC) kaynak, bir düğüm bloğu içinde kullanılabilir bir [DSC Yapılandırması](configurations.md) diğer düğümlerde yapılandırmalarında bağımlılıklarını belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="a6392-105">The **WaitForAny** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="a6392-106">Kaynak tarafından belirtilmişse bu kaynak başarılı **ResourceName** özelliktir istenilen durumda düğüm sayısı alt sınırı (tarafından belirtilen **NodeCount**) tarafından tanımlanan **NodeName**  özelliği.</span><span class="sxs-lookup"><span data-stu-id="a6392-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span>


## <a name="syntax"></a><span data-ttu-id="a6392-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a6392-107">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="a6392-108">Özellikler</span><span class="sxs-lookup"><span data-stu-id="a6392-108">Properties</span></span>

|  <span data-ttu-id="a6392-109">Özellik</span><span class="sxs-lookup"><span data-stu-id="a6392-109">Property</span></span>  |  <span data-ttu-id="a6392-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a6392-110">Description</span></span>   |
|---|---|
| <span data-ttu-id="a6392-111">NodeCount</span><span class="sxs-lookup"><span data-stu-id="a6392-111">NodeCount</span></span>| <span data-ttu-id="a6392-112">Düğüm sayısı alt sınırı başarılı olması bu kaynak için istenen durumunda olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a6392-112">The minimum number of nodes that must be in the desired state for this resource to succeed.</span></span>|
| <span data-ttu-id="a6392-113">nodeName</span><span class="sxs-lookup"><span data-stu-id="a6392-113">NodeName</span></span>| <span data-ttu-id="a6392-114">Hedef düğümleri kaynağın bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="a6392-114">The target nodes of the resource to depend on.</span></span>|
| <span data-ttu-id="a6392-115">resourceName</span><span class="sxs-lookup"><span data-stu-id="a6392-115">ResourceName</span></span>| <span data-ttu-id="a6392-116">Bağımlı kaynak adı.</span><span class="sxs-lookup"><span data-stu-id="a6392-116">The resource name to depend on.</span></span> <span data-ttu-id="a6392-117">Bu kaynak için farklı bir yapılandırma aitse, adı olarak biçim "[__ResourceType__]__ResourceName__:: [__ConfigurationName__]:: [ __ConfigurationName__] "</span><span class="sxs-lookup"><span data-stu-id="a6392-117">If this resource belongs to a different configuration, format the name as "[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]"</span></span>|
| <span data-ttu-id="a6392-118">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="a6392-118">RetryIntervalSec</span></span>| <span data-ttu-id="a6392-119">Yeniden denemeden önce saniye sayısı.</span><span class="sxs-lookup"><span data-stu-id="a6392-119">The number of seconds before retrying.</span></span> <span data-ttu-id="a6392-120">Minimum is 1.</span><span class="sxs-lookup"><span data-stu-id="a6392-120">Minimum is 1.</span></span>|
| <span data-ttu-id="a6392-121">retryCount</span><span class="sxs-lookup"><span data-stu-id="a6392-121">RetryCount</span></span>| <span data-ttu-id="a6392-122">Yeniden deneneceğini maksimum sayısı.</span><span class="sxs-lookup"><span data-stu-id="a6392-122">The maximum number of times to retry.</span></span>|
| <span data-ttu-id="a6392-123">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="a6392-123">ThrottleLimit</span></span>| <span data-ttu-id="a6392-124">Makinelerin aynı anda bağlanmasına sayısı.</span><span class="sxs-lookup"><span data-stu-id="a6392-124">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="a6392-125">Varsayılan yeni-cimsession varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="a6392-125">Default is new-cimsession default.</span></span>|
| <span data-ttu-id="a6392-126">dependsOn</span><span class="sxs-lookup"><span data-stu-id="a6392-126">DependsOn</span></span> | <span data-ttu-id="a6392-127">Bu kaynak yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmalısınız gösterir.</span><span class="sxs-lookup"><span data-stu-id="a6392-127">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="a6392-128">Örneğin, kaynak yapılandırması Kimliğini komut dosyası çalıştırmak istediğiniz bloğu ilk ise __ResourceName__ ve türünü __ResourceType__, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="a6392-128">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="a6392-129">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="a6392-129">PsDscRunAsCredential</span></span> | <span data-ttu-id="a6392-130">Bkz: [kullanıcı kimlik bilgileriyle DSC kullanma](https://docs.microsoft.com/powershell/dsc/runasuser)</span><span class="sxs-lookup"><span data-stu-id="a6392-130">See [Using DSC with User Credentials](https://docs.microsoft.com/powershell/dsc/runasuser)</span></span> |


## <a name="example"></a><span data-ttu-id="a6392-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="a6392-131">Example</span></span>

<span data-ttu-id="a6392-132">Bu kaynak kullanma örneği için bkz: [arası düğümlü bağımlılıkları belirtme](crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="a6392-132">For an example of how to use this resource, see [Specifying cross-node dependencies](crossNodeDependencies.md)</span></span>