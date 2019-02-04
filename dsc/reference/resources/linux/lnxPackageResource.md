---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC için Linux nxPackage kaynağı
ms.openlocfilehash: 64bb89a95bd6cbaea4e74b8a9979de52428fef3f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685686"
---
# <a name="dsc-for-linux-nxpackage-resource"></a><span data-ttu-id="694e0-103">DSC için Linux nxPackage kaynağı</span><span class="sxs-lookup"><span data-stu-id="694e0-103">DSC for Linux nxPackage Resource</span></span>

<span data-ttu-id="694e0-104">**NxPackage** kaynak içinde PowerShell Desired State Configuration (DSC), bir Linux düğümde paketlerini yönetmek için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="694e0-104">The **nxPackage** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage packages on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="694e0-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="694e0-105">Syntax</span></span>

```
nxPackage <string> #ResourceName
{
    Name = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ PackageManager = <string> { Yum | Apt | Zypper } ]
    [ PackageGroup = <bool>]
    [ Arguments = <string> ]
    [ ReturnCode = <uint32> ]
    [ LogPath = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="694e0-106">Özellikler</span><span class="sxs-lookup"><span data-stu-id="694e0-106">Properties</span></span>

|  <span data-ttu-id="694e0-107">Özellik</span><span class="sxs-lookup"><span data-stu-id="694e0-107">Property</span></span> |  <span data-ttu-id="694e0-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="694e0-108">Description</span></span> |
|---|---|
| <span data-ttu-id="694e0-109">Adı</span><span class="sxs-lookup"><span data-stu-id="694e0-109">Name</span></span>| <span data-ttu-id="694e0-110">Belirli bir durumu sağlamak istediğiniz paketin adı.</span><span class="sxs-lookup"><span data-stu-id="694e0-110">The name of the package for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="694e0-111">Emin olun</span><span class="sxs-lookup"><span data-stu-id="694e0-111">Ensure</span></span>| <span data-ttu-id="694e0-112">Paket mevcut olup olmadığını denetleyin belirler.</span><span class="sxs-lookup"><span data-stu-id="694e0-112">Determines whether to check if the package exists.</span></span> <span data-ttu-id="694e0-113">"Var" Paket var. olmak için bu özelliği ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="694e0-113">Set this property to "Present" to ensure the package exists.</span></span> <span data-ttu-id="694e0-114">Kümesi "Yok" Paket sağlamak için mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="694e0-114">Set it to "Absent" to ensure the package does not exist.</span></span> <span data-ttu-id="694e0-115">"Var" varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="694e0-115">The default value is "Present".</span></span>|
| <span data-ttu-id="694e0-116">PackageManager</span><span class="sxs-lookup"><span data-stu-id="694e0-116">PackageManager</span></span>| <span data-ttu-id="694e0-117">Desteklenen değerler şunlardır: "yum", "apt" ve "zypper".</span><span class="sxs-lookup"><span data-stu-id="694e0-117">Supported values are "yum", "apt", and "zypper".</span></span> <span data-ttu-id="694e0-118">Paket Yöneticisi paketleri yüklerken kullanılacak belirtir.</span><span class="sxs-lookup"><span data-stu-id="694e0-118">Specifies the package manager to use when installing packages.</span></span> <span data-ttu-id="694e0-119">Varsa **FilePath** belirtilirse, sağlanan yol, paketi yüklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="694e0-119">If **FilePath** is specified, the provided path will be used to install the package.</span></span> <span data-ttu-id="694e0-120">Aksi takdirde, bir paket Yöneticisi, önceden yapılandırılmış bir depodan paketini yüklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="694e0-120">Otherwise, a Package Manager will be used to install the package from a pre-configured repository.</span></span> <span data-ttu-id="694e0-121">Kullanılmazsa **PackageManager** ya da **FilePath** sağlanır, varsayılan Paket Yöneticisi için sistem kullanılır.</span><span class="sxs-lookup"><span data-stu-id="694e0-121">If neither **PackageManager** nor **FilePath** are provided, the default package manager for the system will be used.</span></span>|
| <span data-ttu-id="694e0-122">Dosya yolu</span><span class="sxs-lookup"><span data-stu-id="694e0-122">FilePath</span></span>| <span data-ttu-id="694e0-123">Paketin bulunduğu dosya yolu</span><span class="sxs-lookup"><span data-stu-id="694e0-123">The file path where the package resides</span></span>|
| <span data-ttu-id="694e0-124">PackageGroup</span><span class="sxs-lookup"><span data-stu-id="694e0-124">PackageGroup</span></span>| <span data-ttu-id="694e0-125">Varsa **$true**, **adı** ile kullanmak için bir paket grubu adını olması beklenen bir **PackageManager**.</span><span class="sxs-lookup"><span data-stu-id="694e0-125">If **$true**, the **Name** is expected to be the name of a package group for use with a **PackageManager**.</span></span> <span data-ttu-id="694e0-126">**PacakgeGroup** sağlanırken geçersiz bir **FilePath**.</span><span class="sxs-lookup"><span data-stu-id="694e0-126">**PacakgeGroup** is not valid when providing a **FilePath**.</span></span>|
| <span data-ttu-id="694e0-127">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="694e0-127">Arguments</span></span>| <span data-ttu-id="694e0-128">Paketi tam olarak sağlanan şekilde geçirilecek bağımsız değişken bir dize.</span><span class="sxs-lookup"><span data-stu-id="694e0-128">A string of arguments that will be passed to the package exactly as provided.</span></span>|
| <span data-ttu-id="694e0-129">ReturnCode</span><span class="sxs-lookup"><span data-stu-id="694e0-129">ReturnCode</span></span>| <span data-ttu-id="694e0-130">Beklenen dönüş kodu.</span><span class="sxs-lookup"><span data-stu-id="694e0-130">The expected return code.</span></span> <span data-ttu-id="694e0-131">Gerçek kodu döndürmesi durumunda beklenen değer, burada, yapılandırma, bir hata döndürür sağlanan eşleşmiyor.</span><span class="sxs-lookup"><span data-stu-id="694e0-131">If the actual return code does not match the expected value provided here, the configuration will return an error.</span></span>|
| <span data-ttu-id="694e0-132">DependsOn</span><span class="sxs-lookup"><span data-stu-id="694e0-132">DependsOn</span></span> | <span data-ttu-id="694e0-133">Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="694e0-133">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="694e0-134">Örneğin, varsa **kimliği** kaynağın çalıştırmak istediğiniz yapılandırma komut dosyası bloğu ilk. **ResourceName** ve türünü **ResourceType**, bunu kullanarak söz dizimi özellik `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="694e0-134">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="694e0-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="694e0-135">Example</span></span>

<span data-ttu-id="694e0-136">Aşağıdaki örnek, "httpd" adlı bir paket "ı Yum" Paket Yöneticisi'ni kullanarak bir Linux bilgisayara yüklendiğini sağlar.</span><span class="sxs-lookup"><span data-stu-id="694e0-136">The following example ensures that the package named "httpd" is installed on a Linux computer, using the “Yum” package manager.</span></span>

```
Import-DSCResource -Module nx

Node $node {
nxPackage httpd
{
    Name = "httpd"
    Ensure = "Present"
    PackageManager = "Yum"
}
}
```