---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, yapılandırma, Kur
title: DSC Linux nxService kaynak için
ms.openlocfilehash: b02fb1153570f628682533cb57a7d429e5cc8762
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-for-linux-nxservice-resource"></a><span data-ttu-id="404e1-103">DSC Linux nxService kaynak için</span><span class="sxs-lookup"><span data-stu-id="404e1-103">DSC for Linux nxService Resource</span></span>

<span data-ttu-id="404e1-104">**NxService** kaynağı içinde PowerShell istenen durum yapılandırması (DSC), bir Linux düğümü hizmetleri yönetmek için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="404e1-104">The **nxService** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="404e1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="404e1-105">Syntax</span></span>

```
nxService <string> #ResourceName
{
    Name = <string>
    [ Controller = <string> { init | upstart | systemd }  ]
    [ Enabled = <bool> ]
    [ State = <string> { Running | Stopped } ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="404e1-106">Özellikler</span><span class="sxs-lookup"><span data-stu-id="404e1-106">Properties</span></span>
|  <span data-ttu-id="404e1-107">Özellik</span><span class="sxs-lookup"><span data-stu-id="404e1-107">Property</span></span> |  <span data-ttu-id="404e1-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="404e1-108">Description</span></span> |
|---|---|
| <span data-ttu-id="404e1-109">Ad</span><span class="sxs-lookup"><span data-stu-id="404e1-109">Name</span></span>| <span data-ttu-id="404e1-110">Hizmeti/yapılandırmak için arka plan programı adı.</span><span class="sxs-lookup"><span data-stu-id="404e1-110">The name of the service/daemon to configure.</span></span>|
| <span data-ttu-id="404e1-111">Denetleyici</span><span class="sxs-lookup"><span data-stu-id="404e1-111">Controller</span></span>| <span data-ttu-id="404e1-112">Hizmet yapılandırırken kullanmak için hizmet denetleyicisi türü.</span><span class="sxs-lookup"><span data-stu-id="404e1-112">The type of service controller to use when configuring the service.</span></span>|
| <span data-ttu-id="404e1-113">Etkin</span><span class="sxs-lookup"><span data-stu-id="404e1-113">Enabled</span></span>| <span data-ttu-id="404e1-114">Hizmet önyükleme başlayıp başlamadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="404e1-114">Indicates whether the service starts on boot.</span></span>|
| <span data-ttu-id="404e1-115">Durum</span><span class="sxs-lookup"><span data-stu-id="404e1-115">State</span></span>| <span data-ttu-id="404e1-116">Hizmetin çalışıp çalışmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="404e1-116">Indicates whether the service is running.</span></span> <span data-ttu-id="404e1-117">Bu özelliği hizmeti çalışmadığından emin olmak için "durduruldu" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="404e1-117">Set this property to "Stopped" to ensure that the service is not running.</span></span> <span data-ttu-id="404e1-118">"Hizmet çalışmıyor emin olmak için çalışıyor" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="404e1-118">Set it to "Running" to ensure that the service is not running.</span></span>|
| <span data-ttu-id="404e1-119">dependsOn</span><span class="sxs-lookup"><span data-stu-id="404e1-119">DependsOn</span></span> | <span data-ttu-id="404e1-120">Bu kaynak yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmalısınız gösterir.</span><span class="sxs-lookup"><span data-stu-id="404e1-120">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="404e1-121">Örneğin, varsa **kimliği** çalıştırmak istediğiniz yapılandırma betik bloğu ilk kaynaktır **ResourceName** ve türünü **ResourceType**, bunu kullanarak söz dizimi özellik `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="404e1-121">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|


## <a name="additional-information"></a><span data-ttu-id="404e1-122">Ek Bilgi</span><span class="sxs-lookup"><span data-stu-id="404e1-122">Additional Information</span></span>

<span data-ttu-id="404e1-123">**NxService** kaynak değil oluşturacak bir hizmet tanımı veya hizmet için komut dosyası henüz yoksa.</span><span class="sxs-lookup"><span data-stu-id="404e1-123">The **nxService** resource will not create a service definition or script for the service if it does not exist.</span></span> <span data-ttu-id="404e1-124">PowerShell istenen durum yapılandırması kullanabilirsiniz **nxFile** varlığı ya da hizmet tanımı dosyası veya komut dosyası içeriğini yönetmek için kaynak kaynak.</span><span class="sxs-lookup"><span data-stu-id="404e1-124">You can use the PowerShell Desired State Configuration **nxFile** Resource resource to manage the existence or contents of the service definition file or script.</span></span>

## <a name="example"></a><span data-ttu-id="404e1-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="404e1-125">Example</span></span>

<span data-ttu-id="404e1-126">Aşağıdaki örnek, kayıtlı yapılandırma (için Apache HTTP Server), "httpd" hizmetinin gösterir **SystemD** hizmet denetleyicisi.</span><span class="sxs-lookup"><span data-stu-id="404e1-126">The following example shows configuration of the “httpd” service (for Apache HTTP Server), registered with the **SystemD** service controller.</span></span>

```
Import-DSCResource -Module nx

Node $node {
#Apache Service
nxService ApacheService
{
Name = "httpd"
State = "running"
Enabled = $true
Controller = "systemd"
}
}
```