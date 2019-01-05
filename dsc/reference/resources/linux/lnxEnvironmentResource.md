---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC için Linux nxEnvironment kaynağı
ms.openlocfilehash: 763ec560faa6adaf42aef3c21c9045be95f780bc
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048854"
---
# <a name="dsc-for-linux-nxenvironment-resource"></a><span data-ttu-id="bda67-103">DSC için Linux nxEnvironment kaynağı</span><span class="sxs-lookup"><span data-stu-id="bda67-103">DSC for Linux nxEnvironment Resource</span></span>

<span data-ttu-id="bda67-104">**NxEnvironment** kaynak içinde PowerShell Desired State Configuration (DSC), sistem ortam değişkenlerini Linux düğümde yönetmek için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="bda67-104">The **nxEnvironment** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage system environment variables on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="bda67-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bda67-105">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="bda67-106">Özellikler</span><span class="sxs-lookup"><span data-stu-id="bda67-106">Properties</span></span>

|  <span data-ttu-id="bda67-107">Özellik</span><span class="sxs-lookup"><span data-stu-id="bda67-107">Property</span></span> |  <span data-ttu-id="bda67-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bda67-108">Description</span></span> |
|---|---|
| <span data-ttu-id="bda67-109">Ad</span><span class="sxs-lookup"><span data-stu-id="bda67-109">Name</span></span>| <span data-ttu-id="bda67-110">Belirli bir durumu sağlamak istediğiniz ortam değişkeninin adı gösterir.</span><span class="sxs-lookup"><span data-stu-id="bda67-110">Indicates the name of the environment variable for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="bda67-111">Değer</span><span class="sxs-lookup"><span data-stu-id="bda67-111">Value</span></span>| <span data-ttu-id="bda67-112">Ortam değişkenine atanacak değer.</span><span class="sxs-lookup"><span data-stu-id="bda67-112">The value to assign to the environment variable.</span></span>|
| <span data-ttu-id="bda67-113">Emin olun</span><span class="sxs-lookup"><span data-stu-id="bda67-113">Ensure</span></span>| <span data-ttu-id="bda67-114">Değişkeni mevcut olup olmadığını denetleyin belirler.</span><span class="sxs-lookup"><span data-stu-id="bda67-114">Determines whether to check if the variable exists.</span></span> <span data-ttu-id="bda67-115">Bu özelliği değişkeni var. olmak için "var" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="bda67-115">Set this property to "Present" to ensure the variable exists.</span></span> <span data-ttu-id="bda67-116">Kümesi "Yok" değişken sağlamak için mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="bda67-116">Set it to "Absent" to ensure the variable does not exist.</span></span> <span data-ttu-id="bda67-117">"Var" varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="bda67-117">The default value is "Present".</span></span>|
| <span data-ttu-id="bda67-118">Yol</span><span class="sxs-lookup"><span data-stu-id="bda67-118">Path</span></span>| <span data-ttu-id="bda67-119">Yapılandırılan ortam değişkenini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bda67-119">Defines the environment variable that is being configured.</span></span> <span data-ttu-id="bda67-120">Bu özellik kümesine **$true** değişken ise **yolu** değişken; Aksi takdirde ayarlayın **$false**.</span><span class="sxs-lookup"><span data-stu-id="bda67-120">Set this property to **$true** if the variable is the **Path** variable; otherwise, set it to **$false**.</span></span> <span data-ttu-id="bda67-121">Varsayılan değer **$false**.</span><span class="sxs-lookup"><span data-stu-id="bda67-121">The default is **$false**.</span></span> <span data-ttu-id="bda67-122">Yapılandırılan değişken ise **yolu** değişkeni aracılığıyla belirtilen değer **değer** özelliği için mevcut değeri eklenir.</span><span class="sxs-lookup"><span data-stu-id="bda67-122">If the variable being configured is the **Path** variable, the value provided through the **Value** property will be appended to the existing value.</span></span>|
| <span data-ttu-id="bda67-123">DependsOn</span><span class="sxs-lookup"><span data-stu-id="bda67-123">DependsOn</span></span> | <span data-ttu-id="bda67-124">Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="bda67-124">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="bda67-125">Örneğin, varsa **kimliği** kaynağın çalıştırmak istediğiniz yapılandırma komut dosyası bloğu ilk. **ResourceName** ve türünü **ResourceType**, bunu kullanarak söz dizimi özellik `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="bda67-125">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="additional-information"></a><span data-ttu-id="bda67-126">Ek Bilgi</span><span class="sxs-lookup"><span data-stu-id="bda67-126">Additional Information</span></span>

* <span data-ttu-id="bda67-127">Varsa **yolu** yok veya kümesine **$false**, ortam değişkenleri yönetilen `/etc/environment`.</span><span class="sxs-lookup"><span data-stu-id="bda67-127">If **Path** is absent or set to **$false**, environment variables are managed in `/etc/environment`.</span></span> <span data-ttu-id="bda67-128">Programlar veya betiklerde kaynak yapılandırma gerektirebilir `/etc/environment` yönetilen ortam değişkenlerine erişmek için dosya.</span><span class="sxs-lookup"><span data-stu-id="bda67-128">Your programs or scripts may require configuration to source the `/etc/environment` file to access the managed environment variables.</span></span>
* <span data-ttu-id="bda67-129">Varsa **yolu** ayarlanır **$true**, ortam değişkeni dosyasında yönetilen `/etc/profile.d/DSCenvironment.sh`.</span><span class="sxs-lookup"><span data-stu-id="bda67-129">If **Path** is set to **$true**, the environment variable is managed in the file `/etc/profile.d/DSCenvironment.sh`.</span></span> <span data-ttu-id="bda67-130">Bu dosya yoksa, oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="bda67-130">This file will be created if it does not exist.</span></span> <span data-ttu-id="bda67-131">Varsa **emin olun** ayarlanmış "Yok" için ve **yolu** ayarlanır **$true**, var olan bir ortam değişkeni yalnızca kaldırılacak. `/etc/profile.d/DSCenvironment.sh` ve diğer dosyalardan.</span><span class="sxs-lookup"><span data-stu-id="bda67-131">If **Ensure** is set to "Absent" and **Path** is set to **$true**, an existing environment variable will only be removed from `/etc/profile.d/DSCenvironment.sh` and not from other files.</span></span>

## <a name="example"></a><span data-ttu-id="bda67-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="bda67-132">Example</span></span>

<span data-ttu-id="bda67-133">Aşağıdaki örnek nasıl kullanılacağını gösterir **nxEnvironment** emin olmak için kaynak **TestEnvironmentVariable** mevcut olduğundan ve "Test-Value" değerine sahip.</span><span class="sxs-lookup"><span data-stu-id="bda67-133">The following example shows how to use the **nxEnvironment** resource to ensure that **TestEnvironmentVariable** is present and has the value "Test-Value".</span></span> <span data-ttu-id="bda67-134">Varsa **TestEnvironmentVariable** olduğunu yoksa oluşturulacaktır.</span><span class="sxs-lookup"><span data-stu-id="bda67-134">If **TestEnvironmentVariable** is not present, it will be created.</span></span>

```
Import-DSCResource -Module nx


nxEnvironment EnvironmentExample
{
    Ensure = “Present”
    Name = “TestEnvironmentVariable”
    Value = “TestValue”
}
```