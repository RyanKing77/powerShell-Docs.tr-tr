---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC için Linux nxPackage kaynağı
ms.openlocfilehash: 64bb89a95bd6cbaea4e74b8a9979de52428fef3f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077883"
---
# <a name="dsc-for-linux-nxpackage-resource"></a><span data-ttu-id="8b00a-103">DSC için Linux nxPackage kaynağı</span><span class="sxs-lookup"><span data-stu-id="8b00a-103">DSC for Linux nxPackage Resource</span></span>

<span data-ttu-id="8b00a-104">**NxPackage** kaynak içinde PowerShell Desired State Configuration (DSC), bir Linux düğümde paketlerini yönetmek için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b00a-104">The **nxPackage** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage packages on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="8b00a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8b00a-105">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="8b00a-106">Özellikler</span><span class="sxs-lookup"><span data-stu-id="8b00a-106">Properties</span></span>

|  <span data-ttu-id="8b00a-107">Özellik</span><span class="sxs-lookup"><span data-stu-id="8b00a-107">Property</span></span> |  <span data-ttu-id="8b00a-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8b00a-108">Description</span></span> |
|---|---|
| <span data-ttu-id="8b00a-109">Adı</span><span class="sxs-lookup"><span data-stu-id="8b00a-109">Name</span></span>| <span data-ttu-id="8b00a-110">Belirli bir durumu sağlamak istediğiniz paketin adı.</span><span class="sxs-lookup"><span data-stu-id="8b00a-110">The name of the package for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="8b00a-111">Emin olun</span><span class="sxs-lookup"><span data-stu-id="8b00a-111">Ensure</span></span>| <span data-ttu-id="8b00a-112">Paket mevcut olup olmadığını denetleyin belirler.</span><span class="sxs-lookup"><span data-stu-id="8b00a-112">Determines whether to check if the package exists.</span></span> <span data-ttu-id="8b00a-113">"Var" Paket var. olmak için bu özelliği ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="8b00a-113">Set this property to "Present" to ensure the package exists.</span></span> <span data-ttu-id="8b00a-114">Kümesi "Yok" Paket sağlamak için mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="8b00a-114">Set it to "Absent" to ensure the package does not exist.</span></span> <span data-ttu-id="8b00a-115">"Var" varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="8b00a-115">The default value is "Present".</span></span>|
| <span data-ttu-id="8b00a-116">PackageManager</span><span class="sxs-lookup"><span data-stu-id="8b00a-116">PackageManager</span></span>| <span data-ttu-id="8b00a-117">Desteklenen değerler şunlardır: "yum", "apt" ve "zypper".</span><span class="sxs-lookup"><span data-stu-id="8b00a-117">Supported values are "yum", "apt", and "zypper".</span></span> <span data-ttu-id="8b00a-118">Paket Yöneticisi paketleri yüklerken kullanılacak belirtir.</span><span class="sxs-lookup"><span data-stu-id="8b00a-118">Specifies the package manager to use when installing packages.</span></span> <span data-ttu-id="8b00a-119">Varsa **FilePath** belirtilirse, sağlanan yol, paketi yüklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8b00a-119">If **FilePath** is specified, the provided path will be used to install the package.</span></span> <span data-ttu-id="8b00a-120">Aksi takdirde, bir paket Yöneticisi, önceden yapılandırılmış bir depodan paketini yüklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8b00a-120">Otherwise, a Package Manager will be used to install the package from a pre-configured repository.</span></span> <span data-ttu-id="8b00a-121">Kullanılmazsa **PackageManager** ya da **FilePath** sağlanır, varsayılan Paket Yöneticisi için sistem kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8b00a-121">If neither **PackageManager** nor **FilePath** are provided, the default package manager for the system will be used.</span></span>|
| <span data-ttu-id="8b00a-122">FilePath</span><span class="sxs-lookup"><span data-stu-id="8b00a-122">FilePath</span></span>| <span data-ttu-id="8b00a-123">Paketin bulunduğu dosya yolu</span><span class="sxs-lookup"><span data-stu-id="8b00a-123">The file path where the package resides</span></span>|
| <span data-ttu-id="8b00a-124">PackageGroup</span><span class="sxs-lookup"><span data-stu-id="8b00a-124">PackageGroup</span></span>| <span data-ttu-id="8b00a-125">Varsa **$true**, **adı** ile kullanmak için bir paket grubu adını olması beklenen bir **PackageManager**.</span><span class="sxs-lookup"><span data-stu-id="8b00a-125">If **$true**, the **Name** is expected to be the name of a package group for use with a **PackageManager**.</span></span> <span data-ttu-id="8b00a-126">**PacakgeGroup** sağlanırken geçersiz bir **FilePath**.</span><span class="sxs-lookup"><span data-stu-id="8b00a-126">**PacakgeGroup** is not valid when providing a **FilePath**.</span></span>|
| <span data-ttu-id="8b00a-127">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="8b00a-127">Arguments</span></span>| <span data-ttu-id="8b00a-128">Paketi tam olarak sağlanan şekilde geçirilecek bağımsız değişken bir dize.</span><span class="sxs-lookup"><span data-stu-id="8b00a-128">A string of arguments that will be passed to the package exactly as provided.</span></span>|
| <span data-ttu-id="8b00a-129">ReturnCode</span><span class="sxs-lookup"><span data-stu-id="8b00a-129">ReturnCode</span></span>| <span data-ttu-id="8b00a-130">Beklenen dönüş kodu.</span><span class="sxs-lookup"><span data-stu-id="8b00a-130">The expected return code.</span></span> <span data-ttu-id="8b00a-131">Gerçek kodu döndürmesi durumunda beklenen değer, burada, yapılandırma, bir hata döndürür sağlanan eşleşmiyor.</span><span class="sxs-lookup"><span data-stu-id="8b00a-131">If the actual return code does not match the expected value provided here, the configuration will return an error.</span></span>|
| <span data-ttu-id="8b00a-132">dependsOn</span><span class="sxs-lookup"><span data-stu-id="8b00a-132">DependsOn</span></span> | <span data-ttu-id="8b00a-133">Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="8b00a-133">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="8b00a-134">Örneğin, varsa **kimliği** kaynağın çalıştırmak istediğiniz yapılandırma komut dosyası bloğu ilk. **ResourceName** ve türünü **ResourceType**, bunu kullanarak söz dizimi özellik `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="8b00a-134">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="8b00a-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="8b00a-135">Example</span></span>

<span data-ttu-id="8b00a-136">Aşağıdaki örnek, "httpd" adlı bir paket "ı Yum" Paket Yöneticisi'ni kullanarak bir Linux bilgisayara yüklendiğini sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b00a-136">The following example ensures that the package named "httpd" is installed on a Linux computer, using the “Yum” package manager.</span></span>

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