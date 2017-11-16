---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "DSC ortamı kaynak"
ms.openlocfilehash: 7c98798fa0e8fc865798ea30530e41ac87b2dadc
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-environment-resource"></a><span data-ttu-id="976b7-103">DSC ortamı kaynak</span><span class="sxs-lookup"><span data-stu-id="976b7-103">DSC Environment Resource</span></span>

> <span data-ttu-id="976b7-104">İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="976b7-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="976b7-105">__Ortam__ kaynağı içinde Windows PowerShell istenen durum yapılandırması (DSC), sistem ortam değişkenlerini yönetmek için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="976b7-105">The __Environment__ resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage system environment variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="976b7-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="976b7-106">Syntax</span></span>
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

## <a name="properties"></a><span data-ttu-id="976b7-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="976b7-107">Properties</span></span>

|  <span data-ttu-id="976b7-108">Özellik</span><span class="sxs-lookup"><span data-stu-id="976b7-108">Property</span></span>  |  <span data-ttu-id="976b7-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="976b7-109">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="976b7-110">Ad</span><span class="sxs-lookup"><span data-stu-id="976b7-110">Name</span></span>| <span data-ttu-id="976b7-111">Belirli bir durumu sağlamak istediğiniz ortam değişkeninin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="976b7-111">Indicates the name of the environment variable for which you want to ensure a specific state.</span></span>| 
| <span data-ttu-id="976b7-112">Emin olun</span><span class="sxs-lookup"><span data-stu-id="976b7-112">Ensure</span></span>| <span data-ttu-id="976b7-113">Bir değişken var olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="976b7-113">Indicates if a variable exists.</span></span> <span data-ttu-id="976b7-114">Bu özelliği ayarlamak __mevcut__ henüz yoksa ortam değişkeni oluşturmak veya değerini aracılığıyla sunulan uyduğundan emin olmak için __değeri__ değişkeni zaten varsa, özelliği.</span><span class="sxs-lookup"><span data-stu-id="976b7-114">Set this property to __Present__ to create the environment variable if it does not exist or to ensure that its value matches what is provided through the __Value__ property if the variable already exists.</span></span> <span data-ttu-id="976b7-115">Ayarlamak __etmeksizin__ varsa değişkeni silmek için.</span><span class="sxs-lookup"><span data-stu-id="976b7-115">Set it to __Absent__ to delete the variable if it exists.</span></span>| 
| <span data-ttu-id="976b7-116">Yol</span><span class="sxs-lookup"><span data-stu-id="976b7-116">Path</span></span>| <span data-ttu-id="976b7-117">Yapılandırılmakta olan ortam değişkeni tanımlar.</span><span class="sxs-lookup"><span data-stu-id="976b7-117">Defines the environment variable that is being configured.</span></span> <span data-ttu-id="976b7-118">Bu özelliği ayarlamak __$true__ değişken ise __yolu__ değişken, aksi takdirde ayarlamak __$false__.</span><span class="sxs-lookup"><span data-stu-id="976b7-118">Set this property to __$true__ if the variable is the __Path__ variable; otherwise, set it to __$false__.</span></span> <span data-ttu-id="976b7-119">Varsayılan değer __$false__.</span><span class="sxs-lookup"><span data-stu-id="976b7-119">The default is __$false__.</span></span> <span data-ttu-id="976b7-120">Yapılandırılmakta değişken ise __yolu__ değişken değeri sağlanan __değeri__ özelliği, var olan değerin eklenir.</span><span class="sxs-lookup"><span data-stu-id="976b7-120">If the variable being configured is the __Path__ variable, the value provided through the __Value__ property will be appended to the existing value.</span></span>| 
| <span data-ttu-id="976b7-121">dependsOn</span><span class="sxs-lookup"><span data-stu-id="976b7-121">DependsOn</span></span> | <span data-ttu-id="976b7-122">Bu kaynak yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmalısınız gösterir.</span><span class="sxs-lookup"><span data-stu-id="976b7-122">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="976b7-123">Örneğin, kaynak yapılandırması Kimliğini komut dosyası çalıştırmak istediğiniz bloğu ilk ise __ResourceName__ ve türünü __ResourceType__, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="976b7-123">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 
| <span data-ttu-id="976b7-124">Değer</span><span class="sxs-lookup"><span data-stu-id="976b7-124">Value</span></span>| <span data-ttu-id="976b7-125">Ortam değişkenine atanacak değer.</span><span class="sxs-lookup"><span data-stu-id="976b7-125">The value to assign to the environment variable.</span></span>| 

## <a name="example"></a><span data-ttu-id="976b7-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="976b7-126">Example</span></span>

<span data-ttu-id="976b7-127">Aşağıdaki örnek sağlar __TestEnvironmentVariable__ bulunduğundan ve değerine sahip __TestValue__.</span><span class="sxs-lookup"><span data-stu-id="976b7-127">The following example ensures that __TestEnvironmentVariable__ is present and it has the value __TestValue__.</span></span> <span data-ttu-id="976b7-128">Mevcut değilse, onu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="976b7-128">If it is not present, it creates it.</span></span>

```powershell
Environment EnvironmentExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```

