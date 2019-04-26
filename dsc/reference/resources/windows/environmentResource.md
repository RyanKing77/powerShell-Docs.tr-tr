---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC Environment kaynağı
ms.openlocfilehash: 2bc1600a9df32538d59efa712569b12fa9e3beee
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077543"
---
# <a name="dsc-environment-resource"></a><span data-ttu-id="cd5e3-103">DSC Environment kaynağı</span><span class="sxs-lookup"><span data-stu-id="cd5e3-103">DSC Environment Resource</span></span>

> <span data-ttu-id="cd5e3-104">Uygulama hedefi: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="cd5e3-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="cd5e3-105">__Ortam__ kaynak olarak Windows PowerShell Desired State Configuration (DSC), sistem ortam değişkenlerini yönetmek için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="cd5e3-105">The __Environment__ resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage system environment variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="cd5e3-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cd5e3-106">Syntax</span></span>
``` mof
Environment [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ Path = [bool] ]
    [ DependsOn = [string[]] ]
    [ Value = [string] ]
}
```

## <a name="properties"></a><span data-ttu-id="cd5e3-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="cd5e3-107">Properties</span></span>

|  <span data-ttu-id="cd5e3-108">Özellik</span><span class="sxs-lookup"><span data-stu-id="cd5e3-108">Property</span></span>  |  <span data-ttu-id="cd5e3-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cd5e3-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="cd5e3-110">Adı</span><span class="sxs-lookup"><span data-stu-id="cd5e3-110">Name</span></span>| <span data-ttu-id="cd5e3-111">Belirli bir durumu sağlamak istediğiniz ortam değişkeninin adı gösterir.</span><span class="sxs-lookup"><span data-stu-id="cd5e3-111">Indicates the name of the environment variable for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="cd5e3-112">Emin olun</span><span class="sxs-lookup"><span data-stu-id="cd5e3-112">Ensure</span></span>| <span data-ttu-id="cd5e3-113">Bir değişkenin olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="cd5e3-113">Indicates if a variable exists.</span></span> <span data-ttu-id="cd5e3-114">Bu özellik kümesine __mevcut__ henüz yoksa ortam değişkenini oluşturmak veya değerini aracılığıyla sağlanan eşleştiğinden emin olmak için __değer__ değişkeni zaten varsa, özelliği.</span><span class="sxs-lookup"><span data-stu-id="cd5e3-114">Set this property to __Present__ to create the environment variable if it does not exist or to ensure that its value matches what is provided through the __Value__ property if the variable already exists.</span></span> <span data-ttu-id="cd5e3-115">Ayarlayın __devamsızlık__ varsa değişken silinemedi.</span><span class="sxs-lookup"><span data-stu-id="cd5e3-115">Set it to __Absent__ to delete the variable if it exists.</span></span>|
| <span data-ttu-id="cd5e3-116">Yol</span><span class="sxs-lookup"><span data-stu-id="cd5e3-116">Path</span></span>| <span data-ttu-id="cd5e3-117">Yapılandırılan ortam değişkenini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="cd5e3-117">Defines the environment variable that is being configured.</span></span> <span data-ttu-id="cd5e3-118">Bu özellik kümesine __$true__ değişken ise __yolu__ değişken; Aksi takdirde ayarlayın __$false__.</span><span class="sxs-lookup"><span data-stu-id="cd5e3-118">Set this property to __$true__ if the variable is the __Path__ variable; otherwise, set it to __$false__.</span></span> <span data-ttu-id="cd5e3-119">Varsayılan değer __$false__.</span><span class="sxs-lookup"><span data-stu-id="cd5e3-119">The default is __$false__.</span></span> <span data-ttu-id="cd5e3-120">Yapılandırılan değişken ise __yolu__ değişkeni aracılığıyla belirtilen değer __değer__ özelliği için mevcut değeri eklenir.</span><span class="sxs-lookup"><span data-stu-id="cd5e3-120">If the variable being configured is the __Path__ variable, the value provided through the __Value__ property will be appended to the existing value.</span></span>|
| <span data-ttu-id="cd5e3-121">dependsOn</span><span class="sxs-lookup"><span data-stu-id="cd5e3-121">DependsOn</span></span> | <span data-ttu-id="cd5e3-122">Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="cd5e3-122">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="cd5e3-123">Örneğin, kaynak yapılandırmasının Kimliğini çalıştırmak istediğiniz bir blok betik ilk ise __ResourceName__ ve kendi türünün __ResourceType__, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="cd5e3-123">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="cd5e3-124">Değer</span><span class="sxs-lookup"><span data-stu-id="cd5e3-124">Value</span></span>| <span data-ttu-id="cd5e3-125">Ortam değişkenine atanacak değer.</span><span class="sxs-lookup"><span data-stu-id="cd5e3-125">The value to assign to the environment variable.</span></span>|

## <a name="example"></a><span data-ttu-id="cd5e3-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="cd5e3-126">Example</span></span>

<span data-ttu-id="cd5e3-127">Aşağıdaki örnek, sağlar __TestEnvironmentVariable__ mevcut olduğundan ve değere sahip __TestValue__.</span><span class="sxs-lookup"><span data-stu-id="cd5e3-127">The following example ensures that __TestEnvironmentVariable__ is present and it has the value __TestValue__.</span></span> <span data-ttu-id="cd5e3-128">Mevcut değilse, onu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cd5e3-128">If it is not present, it creates it.</span></span>

```powershell
Environment EnvironmentExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```