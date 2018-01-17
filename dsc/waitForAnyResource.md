---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "DSC WaitForAny kaynağı"
ms.openlocfilehash: 795c005c67c196ef9afb08af790fe2a1695392ec
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-waitforany-resource"></a><span data-ttu-id="3b72a-103">DSC WaitForAny kaynağı</span><span class="sxs-lookup"><span data-stu-id="3b72a-103">DSC WaitForAny Resource</span></span>

> <span data-ttu-id="3b72a-104">İçin geçerlidir: Windows PowerShell 5.1 ve sonrası</span><span class="sxs-lookup"><span data-stu-id="3b72a-104">Applies To: Windows PowerShell 5.1 and later</span></span>

<span data-ttu-id="3b72a-105">**WaitForSome** istenen durum Yapılandırması'nı (DSC) kaynak, bir düğüm bloğu içinde kullanılabilir bir [DSC Yapılandırması](configurations.md) diğer düğümlerde yapılandırmalarında bağımlılıklarını belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="3b72a-105">The **WaitForSome** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="3b72a-106">Bu kaynak, başarılı kaynak tarafından belirtilmişse **ResourceName** özelliktir tanımlanan tüm hedef düğümleri üzerinde istenen durumda **NodeName** özelliği.</span><span class="sxs-lookup"><span data-stu-id="3b72a-106">This resource succeeds if if the resource specified by the **ResourceName** property is in the desired state on any target nodes defined in the **NodeName** property.</span></span>


## <a name="syntax"></a><span data-ttu-id="3b72a-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3b72a-107">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="3b72a-108">Özellikler</span><span class="sxs-lookup"><span data-stu-id="3b72a-108">Properties</span></span>

|  <span data-ttu-id="3b72a-109">Özellik</span><span class="sxs-lookup"><span data-stu-id="3b72a-109">Property</span></span>  |  <span data-ttu-id="3b72a-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3b72a-110">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="3b72a-111">resourceName</span><span class="sxs-lookup"><span data-stu-id="3b72a-111">ResourceName</span></span>| <span data-ttu-id="3b72a-112">Bağımlı kaynak adı.</span><span class="sxs-lookup"><span data-stu-id="3b72a-112">The resource name to depend on.</span></span>| 
| <span data-ttu-id="3b72a-113">nodeName</span><span class="sxs-lookup"><span data-stu-id="3b72a-113">NodeName</span></span>| <span data-ttu-id="3b72a-114">Hedef düğümleri kaynağın bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="3b72a-114">The target nodes of the resource to depend on.</span></span>| 
| <span data-ttu-id="3b72a-115">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="3b72a-115">RetryIntervalSec</span></span>| <span data-ttu-id="3b72a-116">Yeniden denemeden önce saniye sayısı.</span><span class="sxs-lookup"><span data-stu-id="3b72a-116">The number of seconds before retrying.</span></span> <span data-ttu-id="3b72a-117">Minimum is 1.</span><span class="sxs-lookup"><span data-stu-id="3b72a-117">Minimum is 1.</span></span>| 
| <span data-ttu-id="3b72a-118">retryCount</span><span class="sxs-lookup"><span data-stu-id="3b72a-118">RetryCount</span></span>| <span data-ttu-id="3b72a-119">Yeniden deneneceğini maksimum sayısı.</span><span class="sxs-lookup"><span data-stu-id="3b72a-119">The maximum number of times to retry.</span></span>| 
| <span data-ttu-id="3b72a-120">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="3b72a-120">ThrottleLimit</span></span>| <span data-ttu-id="3b72a-121">Makinelerin aynı anda bağlanmasına sayısı.</span><span class="sxs-lookup"><span data-stu-id="3b72a-121">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="3b72a-122">Varsayılan yeni-cimsession varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="3b72a-122">Default is new-cimsession default.</span></span>| 
| <span data-ttu-id="3b72a-123">dependsOn</span><span class="sxs-lookup"><span data-stu-id="3b72a-123">DependsOn</span></span> | <span data-ttu-id="3b72a-124">Bu kaynak yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmalısınız gösterir.</span><span class="sxs-lookup"><span data-stu-id="3b72a-124">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="3b72a-125">Örneğin, kaynak yapılandırması Kimliğini komut dosyası çalıştırmak istediğiniz bloğu ilk ise __ResourceName__ ve türünü __ResourceType__, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="3b72a-125">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|


## <a name="example"></a><span data-ttu-id="3b72a-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="3b72a-126">Example</span></span>

<span data-ttu-id="3b72a-127">Bu kaynak kullanma örneği için bkz: [arası düğümlü bağımlılıkları belirtme](crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="3b72a-127">For an example of how to use this resource, see [Specifying cross-node dependencies](crossNodeDependencies.md)</span></span>

