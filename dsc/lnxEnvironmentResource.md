---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, yapılandırma, Kur
title: DSC Linux nxEnvironment kaynak için
ms.openlocfilehash: 6d1d5e578e9a7ddda0e70063f86867de2e87a52e
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-for-linux-nxenvironment-resource"></a><span data-ttu-id="9d2da-103">DSC Linux nxEnvironment kaynak için</span><span class="sxs-lookup"><span data-stu-id="9d2da-103">DSC for Linux nxEnvironment Resource</span></span>

<span data-ttu-id="9d2da-104">**NxEnvironment** kaynağı içinde PowerShell istenen durum yapılandırması (DSC), sistem ortam değişkenlerini Linux düğümde yönetmek için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="9d2da-104">The **nxEnvironment** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to to manage system environment variables on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="9d2da-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9d2da-105">Syntax</span></span>

```
nxEnvironment <string> #ResourceName
{
    Name = <string>
    [ Value = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Path = <bool> }
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="9d2da-106">Özellikler</span><span class="sxs-lookup"><span data-stu-id="9d2da-106">Properties</span></span>

|  <span data-ttu-id="9d2da-107">Özellik</span><span class="sxs-lookup"><span data-stu-id="9d2da-107">Property</span></span> |  <span data-ttu-id="9d2da-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9d2da-108">Description</span></span> |
|---|---|
| <span data-ttu-id="9d2da-109">Ad</span><span class="sxs-lookup"><span data-stu-id="9d2da-109">Name</span></span>| <span data-ttu-id="9d2da-110">Belirli bir durumu sağlamak istediğiniz ortam değişkeninin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9d2da-110">Indicates the name of the environment variable for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="9d2da-111">Değer</span><span class="sxs-lookup"><span data-stu-id="9d2da-111">Value</span></span>| <span data-ttu-id="9d2da-112">Ortam değişkenine atanacak değer.</span><span class="sxs-lookup"><span data-stu-id="9d2da-112">The value to assign to the environment variable.</span></span>|
| <span data-ttu-id="9d2da-113">Emin olun</span><span class="sxs-lookup"><span data-stu-id="9d2da-113">Ensure</span></span>| <span data-ttu-id="9d2da-114">Değişkeni var olup olmadığını denetlemek belirler.</span><span class="sxs-lookup"><span data-stu-id="9d2da-114">Determines whether to check if the variable exists.</span></span> <span data-ttu-id="9d2da-115">Bu özelliği değişkeni mevcut emin olmak için "var" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="9d2da-115">Set this property to "Present" to ensure the variable exists.</span></span> <span data-ttu-id="9d2da-116">"Mevcut için" değişkeni var olmadığından emin olmak için ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="9d2da-116">Set it to "Absent" to ensure the variable does not exist.</span></span> <span data-ttu-id="9d2da-117">"Var" varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="9d2da-117">The default value is "Present".</span></span>|
| <span data-ttu-id="9d2da-118">Yol</span><span class="sxs-lookup"><span data-stu-id="9d2da-118">Path</span></span>| <span data-ttu-id="9d2da-119">Yapılandırılmakta olan ortam değişkeni tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9d2da-119">Defines the environment variable that is being configured.</span></span> <span data-ttu-id="9d2da-120">Bu özelliği ayarlamak **$true** değişken ise **yolu** değişken, aksi takdirde ayarlamak **$false**.</span><span class="sxs-lookup"><span data-stu-id="9d2da-120">Set this property to **$true** if the variable is the **Path** variable; otherwise, set it to **$false**.</span></span> <span data-ttu-id="9d2da-121">Varsayılan değer **$false**.</span><span class="sxs-lookup"><span data-stu-id="9d2da-121">The default is **$false**.</span></span> <span data-ttu-id="9d2da-122">Yapılandırılmakta değişken ise **yolu** değişken değeri sağlanan **değeri** özelliği, var olan değerin eklenir.</span><span class="sxs-lookup"><span data-stu-id="9d2da-122">If the variable being configured is the **Path** variable, the value provided through the **Value** property will be appended to the existing value.</span></span>|
| <span data-ttu-id="9d2da-123">dependsOn</span><span class="sxs-lookup"><span data-stu-id="9d2da-123">DependsOn</span></span> | <span data-ttu-id="9d2da-124">Bu kaynak yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmalısınız gösterir.</span><span class="sxs-lookup"><span data-stu-id="9d2da-124">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="9d2da-125">Örneğin, varsa **kimliği** çalıştırmak istediğiniz yapılandırma betik bloğu ilk kaynaktır **ResourceName** ve türünü **ResourceType**, bunu kullanarak söz dizimi özellik `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="9d2da-125">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="additional-information"></a><span data-ttu-id="9d2da-126">Ek Bilgi</span><span class="sxs-lookup"><span data-stu-id="9d2da-126">Additional Information</span></span>

* <span data-ttu-id="9d2da-127">Varsa **yolu** yok veya kümesine **$false**, ortam değişkenleri yönetilen `/etc/environment`.</span><span class="sxs-lookup"><span data-stu-id="9d2da-127">If **Path** is absent or set to **$false**, environment variables are managed in `/etc/environment`.</span></span> <span data-ttu-id="9d2da-128">Programları veya komut dosyalarını kaynağı için yapılandırma gerekebilir `/etc/environment` yönetilen ortam değişkenleri erişmek için dosya.</span><span class="sxs-lookup"><span data-stu-id="9d2da-128">Your programs or scripts may require configuration to source the `/etc/environment` file to access the managed environment variables.</span></span>
* <span data-ttu-id="9d2da-129">Varsa **yolu** ayarlanır **$true**, ortam değişkeni dosyasında yönetilen `/etc/profile.d/DSCenvironment.sh`.</span><span class="sxs-lookup"><span data-stu-id="9d2da-129">If **Path** is set to **$true**, the environment variable is managed in the file `/etc/profile.d/DSCenvironment.sh`.</span></span> <span data-ttu-id="9d2da-130">Bu dosya, henüz yoksa oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9d2da-130">This file will be created if it does not exist.</span></span> <span data-ttu-id="9d2da-131">Varsa **emin olun** ayarlanır "Yok" için ve **yolu** ayarlanır **$true**, varolan bir ortam değişkeni yalnızca konumundan kaldırılacak `/etc/profile.d/DSCenvironment.sh` ve diğer dosyalarından.</span><span class="sxs-lookup"><span data-stu-id="9d2da-131">If **Ensure** is set to "Absent" and **Path** is set to **$true**, an existing environment variable will only be removed from `/etc/profile.d/DSCenvironment.sh` and not from other files.</span></span>

## <a name="example"></a><span data-ttu-id="9d2da-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="9d2da-132">Example</span></span>

<span data-ttu-id="9d2da-133">Aşağıdaki örnekte nasıl kullanılacağını gösterir **nxEnvironment** emin olmak için kaynak **TestEnvironmentVariable** var ve "Test-Value" değerine sahip.</span><span class="sxs-lookup"><span data-stu-id="9d2da-133">The following example shows how to use the **nxEnvironment** resource to ensure that **TestEnvironmentVariable** is present and has the value "Test-Value".</span></span> <span data-ttu-id="9d2da-134">Varsa **TestEnvironmentVariable** olan yoksa, oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9d2da-134">If **TestEnvironmentVariable** is not present, it will be created.</span></span>

```
Import-DSCResource -Module nx


nxEnvironment EnvironmentExample
{
    Ensure = “Present”
    Name = “TestEnvironmentVariable”
    Value = “TestValue”
}
```