---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC için Linux nxService kaynağı
ms.openlocfilehash: fe8043995205649378725f2ab0a78e19313739c9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684251"
---
# <a name="dsc-for-linux-nxservice-resource"></a><span data-ttu-id="bdfd5-103">DSC için Linux nxService kaynağı</span><span class="sxs-lookup"><span data-stu-id="bdfd5-103">DSC for Linux nxService Resource</span></span>

<span data-ttu-id="bdfd5-104">**NxService** kaynak içinde PowerShell Desired State Configuration (DSC), bir Linux düğümdeki hizmetleri yönetmek için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="bdfd5-104">The **nxService** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="bdfd5-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bdfd5-105">Syntax</span></span>

```
nxService <string> #ResourceName
{
    Name = <string>
    [ Controller = <string> { init | upstart | systemd } ]
    [ Enabled = <bool> ]
    [ State = <string> { Running | Stopped } ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a><span data-ttu-id="bdfd5-106">Özellikler</span><span class="sxs-lookup"><span data-stu-id="bdfd5-106">Properties</span></span>

| <span data-ttu-id="bdfd5-107">Özellik</span><span class="sxs-lookup"><span data-stu-id="bdfd5-107">Property</span></span> | <span data-ttu-id="bdfd5-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bdfd5-108">Description</span></span> |
|---|---|
| <span data-ttu-id="bdfd5-109">Adı</span><span class="sxs-lookup"><span data-stu-id="bdfd5-109">Name</span></span>| <span data-ttu-id="bdfd5-110">Yapılandırmak için hizmetin/daemon adı.</span><span class="sxs-lookup"><span data-stu-id="bdfd5-110">The name of the service/daemon to configure.</span></span>|
| <span data-ttu-id="bdfd5-111">Denetleyici</span><span class="sxs-lookup"><span data-stu-id="bdfd5-111">Controller</span></span>| <span data-ttu-id="bdfd5-112">Hizmeti yapılandırırken kullanılacak hizmet denetleyicisi türü.</span><span class="sxs-lookup"><span data-stu-id="bdfd5-112">The type of service controller to use when configuring the service.</span></span>|
| <span data-ttu-id="bdfd5-113">Etkin</span><span class="sxs-lookup"><span data-stu-id="bdfd5-113">Enabled</span></span>| <span data-ttu-id="bdfd5-114">Hizmet önyükleme başlayıp başlamadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="bdfd5-114">Indicates whether the service starts on boot.</span></span>|
| <span data-ttu-id="bdfd5-115">Durum</span><span class="sxs-lookup"><span data-stu-id="bdfd5-115">State</span></span>| <span data-ttu-id="bdfd5-116">Hizmetin çalışıp çalışmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="bdfd5-116">Indicates whether the service is running.</span></span> <span data-ttu-id="bdfd5-117">Bu özelliği hizmet çalışmadığından emin olmak için "Stopped" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="bdfd5-117">Set this property to "Stopped" to ensure that the service is not running.</span></span> <span data-ttu-id="bdfd5-118">"Hizmet çalışmadığından emin olmak için çalışıyor" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="bdfd5-118">Set it to "Running" to ensure that the service is not running.</span></span>|
| <span data-ttu-id="bdfd5-119">DependsOn</span><span class="sxs-lookup"><span data-stu-id="bdfd5-119">DependsOn</span></span> | <span data-ttu-id="bdfd5-120">Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="bdfd5-120">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="bdfd5-121">Örneğin, varsa **kimliği** kaynağın çalıştırmak istediğiniz yapılandırma komut dosyası bloğu ilk. **ResourceName** ve türünü **ResourceType**, bunu kullanarak söz dizimi özellik `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="bdfd5-121">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="additional-information"></a><span data-ttu-id="bdfd5-122">Ek Bilgi</span><span class="sxs-lookup"><span data-stu-id="bdfd5-122">Additional Information</span></span>

<span data-ttu-id="bdfd5-123">**NxService** kaynak değil oluşturur bir hizmet tanımı veya hizmet için betik yok.</span><span class="sxs-lookup"><span data-stu-id="bdfd5-123">The **nxService** resource will not create a service definition or script for the service if it does not exist.</span></span> <span data-ttu-id="bdfd5-124">PowerShell Desired State Configuration kullanabileceğiniz **nxFile** varlığını veya Hizmet tanım dosyası veya komut dosyasının içeriğini yönetmek için kaynak kaynak.</span><span class="sxs-lookup"><span data-stu-id="bdfd5-124">You can use the PowerShell Desired State Configuration **nxFile** Resource resource to manage the existence or contents of the service definition file or script.</span></span>

## <a name="example"></a><span data-ttu-id="bdfd5-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="bdfd5-125">Example</span></span>

<span data-ttu-id="bdfd5-126">Aşağıdaki örnek, kayıtlı (için Apache HTTP Server), 'httpd' hizmetinin yapılandırmasını gösterir. **SystemD** hizmet denetleyicisi.</span><span class="sxs-lookup"><span data-stu-id="bdfd5-126">The following example shows configuration of the 'httpd' service (for Apache HTTP Server), registered with the **SystemD** service controller.</span></span>

```powershell
Import-DSCResource -Module nx

Node $node {
    #Apache Service
    nxService ApacheService {
        Name = 'httpd'
        State = 'running'
        Enabled = $true
        Controller = 'systemd'
    }
}
```