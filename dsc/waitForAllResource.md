---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "DSC WaitForAll kaynağı"
ms.openlocfilehash: 2b6d9e11acd429eecb30926316d1033331524edc
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2018
---
# <a name="dsc-waitforall-resource"></a><span data-ttu-id="1ccda-103">DSC WaitForAll kaynağı</span><span class="sxs-lookup"><span data-stu-id="1ccda-103">DSC WaitForAll Resource</span></span>

> <span data-ttu-id="1ccda-104">İçin geçerlidir: Windows PowerShell 5.0 ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="1ccda-104">Applies To: Windows PowerShell 5.0 and later</span></span>

<span data-ttu-id="1ccda-105">**WaitForAll** istenen durum Yapılandırması'nı (DSC) kaynak, bir düğüm bloğu içinde kullanılabilir bir [DSC Yapılandırması](configurations.md) diğer düğümlerde yapılandırmalarında bağımlılıklarını belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="1ccda-105">The **WaitForAll** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="1ccda-106">Bu kaynak, başarılı kaynak tarafından belirtilmişse **ResourceName** özelliktir tanımlanan tüm hedef düğümleri üzerinde istenen durumda **NodeName** özelliği.</span><span class="sxs-lookup"><span data-stu-id="1ccda-106">This resource succeeds if if the resource specified by the **ResourceName** property is in the desired state on all target nodes defined in the **NodeName** property.</span></span>


## <a name="syntax"></a><span data-ttu-id="1ccda-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1ccda-107">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="1ccda-108">Özellikler</span><span class="sxs-lookup"><span data-stu-id="1ccda-108">Properties</span></span>

|  <span data-ttu-id="1ccda-109">Özellik</span><span class="sxs-lookup"><span data-stu-id="1ccda-109">Property</span></span>  |  <span data-ttu-id="1ccda-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1ccda-110">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="1ccda-111">resourceName</span><span class="sxs-lookup"><span data-stu-id="1ccda-111">ResourceName</span></span>| <span data-ttu-id="1ccda-112">Bağımlı kaynak adı.</span><span class="sxs-lookup"><span data-stu-id="1ccda-112">The resource name to depend on.</span></span> <span data-ttu-id="1ccda-113">Bu kaynak için farklı bir yapılandırma aitse, adı olarak biçim "[__ResourceType__]__ResourceName__:: [__ConfigurationName__]:: [ __ConfigurationName__] "</span><span class="sxs-lookup"><span data-stu-id="1ccda-113">If this resource belongs to a different configuration, format the name as "[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]"</span></span>| 
| <span data-ttu-id="1ccda-114">nodeName</span><span class="sxs-lookup"><span data-stu-id="1ccda-114">NodeName</span></span>| <span data-ttu-id="1ccda-115">Hedef düğümleri kaynağın bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="1ccda-115">The target nodes of the resource to depend on.</span></span>| 
| <span data-ttu-id="1ccda-116">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="1ccda-116">RetryIntervalSec</span></span>| <span data-ttu-id="1ccda-117">Yeniden denemeden önce saniye sayısı.</span><span class="sxs-lookup"><span data-stu-id="1ccda-117">The number of seconds before retrying.</span></span> <span data-ttu-id="1ccda-118">Minimum is 1.</span><span class="sxs-lookup"><span data-stu-id="1ccda-118">Minimum is 1.</span></span>| 
| <span data-ttu-id="1ccda-119">retryCount</span><span class="sxs-lookup"><span data-stu-id="1ccda-119">RetryCount</span></span>| <span data-ttu-id="1ccda-120">Yeniden deneneceğini maksimum sayısı.</span><span class="sxs-lookup"><span data-stu-id="1ccda-120">The maximum number of times to retry.</span></span>| 
| <span data-ttu-id="1ccda-121">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="1ccda-121">ThrottleLimit</span></span>| <span data-ttu-id="1ccda-122">Makinelerin aynı anda bağlanmasına sayısı.</span><span class="sxs-lookup"><span data-stu-id="1ccda-122">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="1ccda-123">Varsayılan yeni-cimsession varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="1ccda-123">Default is new-cimsession default.</span></span>| 
| <span data-ttu-id="1ccda-124">dependsOn</span><span class="sxs-lookup"><span data-stu-id="1ccda-124">DependsOn</span></span> | <span data-ttu-id="1ccda-125">Bu kaynak yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmalısınız gösterir.</span><span class="sxs-lookup"><span data-stu-id="1ccda-125">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="1ccda-126">Örneğin, kaynak yapılandırması Kimliğini komut dosyası çalıştırmak istediğiniz bloğu ilk ise __ResourceName__ ve türünü __ResourceType__, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="1ccda-126">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|


## <a name="example"></a><span data-ttu-id="1ccda-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="1ccda-127">Example</span></span>

<span data-ttu-id="1ccda-128">Bu kaynak kullanma örneği için bkz: [arası düğümlü bağımlılıkları belirtme](crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="1ccda-128">For an example of how to use this resource, see [Specifying cross-node dependencies](crossNodeDependencies.md)</span></span>

