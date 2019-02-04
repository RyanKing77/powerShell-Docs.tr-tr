---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC Environment kaynağı
ms.openlocfilehash: 2bc1600a9df32538d59efa712569b12fa9e3beee
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685987"
---
# <a name="dsc-environment-resource"></a><span data-ttu-id="48cea-103">DSC Environment kaynağı</span><span class="sxs-lookup"><span data-stu-id="48cea-103">DSC Environment Resource</span></span>

> <span data-ttu-id="48cea-104">Şunun için geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="48cea-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="48cea-105">__Ortam__ kaynak olarak Windows PowerShell Desired State Configuration (DSC), sistem ortam değişkenlerini yönetmek için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="48cea-105">The __Environment__ resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage system environment variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="48cea-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="48cea-106">Syntax</span></span>
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

## <a name="properties"></a><span data-ttu-id="48cea-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="48cea-107">Properties</span></span>

|  <span data-ttu-id="48cea-108">Özellik</span><span class="sxs-lookup"><span data-stu-id="48cea-108">Property</span></span>  |  <span data-ttu-id="48cea-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="48cea-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="48cea-110">Adı</span><span class="sxs-lookup"><span data-stu-id="48cea-110">Name</span></span>| <span data-ttu-id="48cea-111">Belirli bir durumu sağlamak istediğiniz ortam değişkeninin adı gösterir.</span><span class="sxs-lookup"><span data-stu-id="48cea-111">Indicates the name of the environment variable for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="48cea-112">Emin olun</span><span class="sxs-lookup"><span data-stu-id="48cea-112">Ensure</span></span>| <span data-ttu-id="48cea-113">Bir değişkenin olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="48cea-113">Indicates if a variable exists.</span></span> <span data-ttu-id="48cea-114">Bu özellik kümesine __mevcut__ henüz yoksa ortam değişkenini oluşturmak veya değerini aracılığıyla sağlanan eşleştiğinden emin olmak için __değer__ değişkeni zaten varsa, özelliği.</span><span class="sxs-lookup"><span data-stu-id="48cea-114">Set this property to __Present__ to create the environment variable if it does not exist or to ensure that its value matches what is provided through the __Value__ property if the variable already exists.</span></span> <span data-ttu-id="48cea-115">Ayarlayın __devamsızlık__ varsa değişken silinemedi.</span><span class="sxs-lookup"><span data-stu-id="48cea-115">Set it to __Absent__ to delete the variable if it exists.</span></span>|
| <span data-ttu-id="48cea-116">Yol</span><span class="sxs-lookup"><span data-stu-id="48cea-116">Path</span></span>| <span data-ttu-id="48cea-117">Yapılandırılan ortam değişkenini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="48cea-117">Defines the environment variable that is being configured.</span></span> <span data-ttu-id="48cea-118">Bu özellik kümesine __$true__ değişken ise __yolu__ değişken; Aksi takdirde ayarlayın __$false__.</span><span class="sxs-lookup"><span data-stu-id="48cea-118">Set this property to __$true__ if the variable is the __Path__ variable; otherwise, set it to __$false__.</span></span> <span data-ttu-id="48cea-119">Varsayılan değer __$false__.</span><span class="sxs-lookup"><span data-stu-id="48cea-119">The default is __$false__.</span></span> <span data-ttu-id="48cea-120">Yapılandırılan değişken ise __yolu__ değişkeni aracılığıyla belirtilen değer __değer__ özelliği için mevcut değeri eklenir.</span><span class="sxs-lookup"><span data-stu-id="48cea-120">If the variable being configured is the __Path__ variable, the value provided through the __Value__ property will be appended to the existing value.</span></span>|
| <span data-ttu-id="48cea-121">DependsOn</span><span class="sxs-lookup"><span data-stu-id="48cea-121">DependsOn</span></span> | <span data-ttu-id="48cea-122">Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="48cea-122">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="48cea-123">Örneğin, kaynak yapılandırmasının Kimliğini çalıştırmak istediğiniz bir blok betik ilk ise __ResourceName__ ve kendi türünün __ResourceType__, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="48cea-123">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="48cea-124">Değer</span><span class="sxs-lookup"><span data-stu-id="48cea-124">Value</span></span>| <span data-ttu-id="48cea-125">Ortam değişkenine atanacak değer.</span><span class="sxs-lookup"><span data-stu-id="48cea-125">The value to assign to the environment variable.</span></span>|

## <a name="example"></a><span data-ttu-id="48cea-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="48cea-126">Example</span></span>

<span data-ttu-id="48cea-127">Aşağıdaki örnek, sağlar __TestEnvironmentVariable__ mevcut olduğundan ve değere sahip __TestValue__.</span><span class="sxs-lookup"><span data-stu-id="48cea-127">The following example ensures that __TestEnvironmentVariable__ is present and it has the value __TestValue__.</span></span> <span data-ttu-id="48cea-128">Mevcut değilse, onu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="48cea-128">If it is not present, it creates it.</span></span>

```powershell
Environment EnvironmentExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```