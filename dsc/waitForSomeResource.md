---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "DSC WaitForSome kaynağı"
ms.openlocfilehash: 8b0ad0dbd31816cc673c7f77945927987e90e08b
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2018
---
# <a name="dsc-waitforsome-resource"></a><span data-ttu-id="67a16-103">DSC WaitForSome kaynağı</span><span class="sxs-lookup"><span data-stu-id="67a16-103">DSC WaitForSome Resource</span></span>

> <span data-ttu-id="67a16-104">İçin geçerlidir: Windows PowerShell 5.0 ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="67a16-104">Applies To: Windows PowerShell 5.0 and later</span></span>

<span data-ttu-id="67a16-105">**WaitForAny** istenen durum Yapılandırması'nı (DSC) kaynak, bir düğüm bloğu içinde kullanılabilir bir [DSC Yapılandırması](configurations.md) diğer düğümlerde yapılandırmalarında bağımlılıklarını belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="67a16-105">The **WaitForAny** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="67a16-106">Kaynak tarafından belirtilmişse bu kaynak başarılı **ResourceName** özelliktir istenilen durumda düğüm sayısı alt sınırı (tarafından belirtilen **NodeCount**) tarafından tanımlanan **NodeName**  özelliği.</span><span class="sxs-lookup"><span data-stu-id="67a16-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span> 


## <a name="syntax"></a><span data-ttu-id="67a16-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="67a16-107">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="67a16-108">Özellikler</span><span class="sxs-lookup"><span data-stu-id="67a16-108">Properties</span></span>

|  <span data-ttu-id="67a16-109">Özellik</span><span class="sxs-lookup"><span data-stu-id="67a16-109">Property</span></span>  |  <span data-ttu-id="67a16-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="67a16-110">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="67a16-111">NodeCount</span><span class="sxs-lookup"><span data-stu-id="67a16-111">NodeCount</span></span>| <span data-ttu-id="67a16-112">Düğüm sayısı alt sınırı başarılı olması bu kaynak için istenen durumunda olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="67a16-112">The minimum number of nodes that must be in the desired state for this resource to succeed.</span></span>|
| <span data-ttu-id="67a16-113">nodeName</span><span class="sxs-lookup"><span data-stu-id="67a16-113">NodeName</span></span>| <span data-ttu-id="67a16-114">Hedef düğümleri kaynağın bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="67a16-114">The target nodes of the resource to depend on.</span></span>| 
| <span data-ttu-id="67a16-115">resourceName</span><span class="sxs-lookup"><span data-stu-id="67a16-115">ResourceName</span></span>| <span data-ttu-id="67a16-116">Bağımlı kaynak adı.</span><span class="sxs-lookup"><span data-stu-id="67a16-116">The resource name to depend on.</span></span> <span data-ttu-id="67a16-117">Bu kaynak için farklı bir yapılandırma aitse, adı olarak biçim "[__ResourceType__]__ResourceName__:: [__ConfigurationName__]:: [ __ConfigurationName__] "</span><span class="sxs-lookup"><span data-stu-id="67a16-117">If this resource belongs to a different configuration, format the name as "[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]"</span></span>| 
| <span data-ttu-id="67a16-118">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="67a16-118">RetryIntervalSec</span></span>| <span data-ttu-id="67a16-119">Yeniden denemeden önce saniye sayısı.</span><span class="sxs-lookup"><span data-stu-id="67a16-119">The number of seconds before retrying.</span></span> <span data-ttu-id="67a16-120">Minimum is 1.</span><span class="sxs-lookup"><span data-stu-id="67a16-120">Minimum is 1.</span></span>| 
| <span data-ttu-id="67a16-121">retryCount</span><span class="sxs-lookup"><span data-stu-id="67a16-121">RetryCount</span></span>| <span data-ttu-id="67a16-122">Yeniden deneneceğini maksimum sayısı.</span><span class="sxs-lookup"><span data-stu-id="67a16-122">The maximum number of times to retry.</span></span>| 
| <span data-ttu-id="67a16-123">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="67a16-123">ThrottleLimit</span></span>| <span data-ttu-id="67a16-124">Makinelerin aynı anda bağlanmasına sayısı.</span><span class="sxs-lookup"><span data-stu-id="67a16-124">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="67a16-125">Varsayılan yeni-cimsession varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="67a16-125">Default is new-cimsession default.</span></span>| 
| <span data-ttu-id="67a16-126">dependsOn</span><span class="sxs-lookup"><span data-stu-id="67a16-126">DependsOn</span></span> | <span data-ttu-id="67a16-127">Bu kaynak yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmalısınız gösterir.</span><span class="sxs-lookup"><span data-stu-id="67a16-127">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="67a16-128">Örneğin, kaynak yapılandırması Kimliğini komut dosyası çalıştırmak istediğiniz bloğu ilk ise __ResourceName__ ve türünü __ResourceType__, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="67a16-128">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="67a16-129">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="67a16-129">PsDscRunAsCredential</span></span> | <span data-ttu-id="67a16-130">Bkz: [kullanıcı kimlik bilgileriyle DSC kullanma](https://docs.microsoft.com/powershell/dsc/runasuser)</span><span class="sxs-lookup"><span data-stu-id="67a16-130">See [Using DSC with User Credentials](https://docs.microsoft.com/powershell/dsc/runasuser)</span></span> |


## <a name="example"></a><span data-ttu-id="67a16-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="67a16-131">Example</span></span>

<span data-ttu-id="67a16-132">Bu kaynak kullanma örneği için bkz: [arası düğümlü bağımlılıkları belirtme](crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="67a16-132">For an example of how to use this resource, see [Specifying cross-node dependencies](crossNodeDependencies.md)</span></span>

