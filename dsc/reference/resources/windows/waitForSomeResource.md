---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC WaitForSome kaynak
ms.openlocfilehash: 2260f37002171154a6f2c3996b2af1bd9120039d
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726776"
---
# <a name="dsc-waitforsome-resource"></a><span data-ttu-id="ab27a-103">DSC WaitForSome kaynak</span><span class="sxs-lookup"><span data-stu-id="ab27a-103">DSC WaitForSome Resource</span></span>

> <span data-ttu-id="ab27a-104">Şunun için geçerlidir: Windows PowerShell 5.0 ve üzeri</span><span class="sxs-lookup"><span data-stu-id="ab27a-104">Applies To: Windows PowerShell 5.0 and later</span></span>

<span data-ttu-id="ab27a-105">**WaitForSome** Desired State Configuration ' nı (DSC) kaynak, bir düğüm bloğunda içinde kullanılabilir bir [DSC Yapılandırması](../../../configurations/configurations.md) diğer düğümlerde yapılandırmalarında bağımlılıklarını belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="ab27a-105">The **WaitForSome** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](../../../configurations/configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="ab27a-106">Bu kaynak tarafından belirtilen kaynağı, başarılı **ResourceName** özelliktir istenen durumda düğüm sayısı alt sınırı (tarafından belirtilen **NodeCount**) tarafından tanımlanan **NodeName**  özelliği.</span><span class="sxs-lookup"><span data-stu-id="ab27a-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span>

> [!NOTE]
> <span data-ttu-id="ab27a-107">**WaitForSome** kaynak diğer düğümlerinin durumunu denetlemek için Windows Uzaktan Yönetimi kullanır.</span><span class="sxs-lookup"><span data-stu-id="ab27a-107">**WaitForSome** resource uses Windows Remote Management to check the state of other Nodes.</span></span>
> <span data-ttu-id="ab27a-108">WinRM bağlantı noktası ve güvenlik gereksinimleri hakkında daha fazla bilgi için bkz. [PowerShell uzaktan iletişim güvenlik konuları](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="ab27a-108">For more information about port and security requirements for WinRM, see [PowerShell Remoting Security Considerations](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span></span>

## <a name="syntax"></a><span data-ttu-id="ab27a-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ab27a-109">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="ab27a-110">Özellikler</span><span class="sxs-lookup"><span data-stu-id="ab27a-110">Properties</span></span>

|  <span data-ttu-id="ab27a-111">Özellik</span><span class="sxs-lookup"><span data-stu-id="ab27a-111">Property</span></span>  |  <span data-ttu-id="ab27a-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ab27a-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="ab27a-113">NodeCount</span><span class="sxs-lookup"><span data-stu-id="ab27a-113">NodeCount</span></span>| <span data-ttu-id="ab27a-114">Başarılı olması bu kaynak için istenen durumda olması gereken düğüm sayısı alt sınırı.</span><span class="sxs-lookup"><span data-stu-id="ab27a-114">The minimum number of nodes that must be in the desired state for this resource to succeed.</span></span>|
| <span data-ttu-id="ab27a-115">nodeName</span><span class="sxs-lookup"><span data-stu-id="ab27a-115">NodeName</span></span>| <span data-ttu-id="ab27a-116">Hedef düğümleri kaynak bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="ab27a-116">The target nodes of the resource to depend on.</span></span>|
| <span data-ttu-id="ab27a-117">resourceName</span><span class="sxs-lookup"><span data-stu-id="ab27a-117">ResourceName</span></span>| <span data-ttu-id="ab27a-118">Bağımlı kaynak adı.</span><span class="sxs-lookup"><span data-stu-id="ab27a-118">The resource name to depend on.</span></span> <span data-ttu-id="ab27a-119">Bu kaynak farklı bir yapılandırmaya aitse, adı olarak Biçimlendir "[__ResourceType__]__ResourceName__:: [__ConfigurationName__]:: [ __ConfigurationName__] "</span><span class="sxs-lookup"><span data-stu-id="ab27a-119">If this resource belongs to a different configuration, format the name as "[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]"</span></span>|
| <span data-ttu-id="ab27a-120">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="ab27a-120">RetryIntervalSec</span></span>| <span data-ttu-id="ab27a-121">Yeniden denemeden önce saniye sayısı.</span><span class="sxs-lookup"><span data-stu-id="ab27a-121">The number of seconds before retrying.</span></span> <span data-ttu-id="ab27a-122">Minimum is 1.</span><span class="sxs-lookup"><span data-stu-id="ab27a-122">Minimum is 1.</span></span>|
| <span data-ttu-id="ab27a-123">RetryCount</span><span class="sxs-lookup"><span data-stu-id="ab27a-123">RetryCount</span></span>| <span data-ttu-id="ab27a-124">Yeniden deneme sayısı.</span><span class="sxs-lookup"><span data-stu-id="ab27a-124">The maximum number of times to retry.</span></span>|
| <span data-ttu-id="ab27a-125">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="ab27a-125">ThrottleLimit</span></span>| <span data-ttu-id="ab27a-126">Aynı anda bağlanmak makineleri sayısı.</span><span class="sxs-lookup"><span data-stu-id="ab27a-126">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="ab27a-127">Yeni-cimsession varsayılan varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="ab27a-127">Default is new-cimsession default.</span></span>|
| <span data-ttu-id="ab27a-128">dependsOn</span><span class="sxs-lookup"><span data-stu-id="ab27a-128">DependsOn</span></span> | <span data-ttu-id="ab27a-129">Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ab27a-129">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="ab27a-130">Örneğin, kaynak yapılandırmasının Kimliğini çalıştırmak istediğiniz bir blok betik ilk ise __ResourceName__ ve kendi türünün __ResourceType__, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="ab27a-130">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="ab27a-131">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="ab27a-131">PsDscRunAsCredential</span></span> | <span data-ttu-id="ab27a-132">Bkz: [kullanıcı kimlik bilgileriyle DSC kullanma](https://docs.microsoft.com/powershell/dsc/runasuser)</span><span class="sxs-lookup"><span data-stu-id="ab27a-132">See [Using DSC with User Credentials](https://docs.microsoft.com/powershell/dsc/runasuser)</span></span> |

## <a name="example"></a><span data-ttu-id="ab27a-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="ab27a-133">Example</span></span>

<span data-ttu-id="ab27a-134">Bu kaynağı kullanmaya ilişkin bir örnek için bkz: [çapraz düğüm bağımlılıklarını belirtme](../../../configurations/crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="ab27a-134">For an example of how to use this resource, see [Specifying cross-node dependencies](../../../configurations/crossNodeDependencies.md)</span></span>
