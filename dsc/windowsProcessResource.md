---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC WindowsProcess kaynağı
ms.openlocfilehash: 3c4e6d8377c3dcbf4f1db87a603d5483b8caafb8
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093744"
---
# <a name="dsc-windowsprocess-resource"></a><span data-ttu-id="ce8c2-103">DSC WindowsProcess kaynağı</span><span class="sxs-lookup"><span data-stu-id="ce8c2-103">DSC WindowsProcess Resource</span></span>

> <span data-ttu-id="ce8c2-104">Uygulama hedefi: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="ce8c2-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="ce8c2-105">**WindowsProcess** kaynak içinde Windows PowerShell Desired State Configuration (DSC), bir hedef düğümde işlemlerini yapılandırmak için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="ce8c2-105">The **WindowsProcess** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to configure processes on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="ce8c2-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ce8c2-106">Syntax</span></span>

```
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ DependsOn = [string[]] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ StandardOutputPath = [string] ]
    [ WorkingDirectory = [string] ]
}
```

## <a name="properties"></a><span data-ttu-id="ce8c2-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="ce8c2-107">Properties</span></span>

|  <span data-ttu-id="ce8c2-108">Özellik</span><span class="sxs-lookup"><span data-stu-id="ce8c2-108">Property</span></span>  |  <span data-ttu-id="ce8c2-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ce8c2-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="ce8c2-110">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="ce8c2-110">Arguments</span></span>| <span data-ttu-id="ce8c2-111">Bir işlem olarak geçirilecek bağımsız değişkenleri dizisini gösterir-olduğu.</span><span class="sxs-lookup"><span data-stu-id="ce8c2-111">Indicates a string of arguments to pass to the process as-is.</span></span> <span data-ttu-id="ce8c2-112">Birden çok bağımsız değişkenleri geçirmek gerekiyorsa, bunları bu dize tüm yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="ce8c2-112">If you need to pass several arguments, put them all in this string.</span></span>|
| <span data-ttu-id="ce8c2-113">Yol</span><span class="sxs-lookup"><span data-stu-id="ce8c2-113">Path</span></span>| <span data-ttu-id="ce8c2-114">İşlem yürütülebilir dosyası yolu.</span><span class="sxs-lookup"><span data-stu-id="ce8c2-114">The path to the process executable.</span></span> <span data-ttu-id="ce8c2-115">Bu ortamı yürütülebilir dosya (tam olarak nitelenmiş yolu değil) DSC kaynak dosya adını arayacaktır **yolu** değişkeni (`$env:Path`) yürütülebilir dosyası bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="ce8c2-115">If this the file name of the executable (not the fully qualified path), the DSC resource will search the environment **Path** variable (`$env:Path`) to find the executable file.</span></span> <span data-ttu-id="ce8c2-116">Bu özelliğin değeri tam bir yolu ise, DSC kullanmaz **yolu** dosyayı bulmak için ortam değişkeni ve yol mevcut değilse bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ce8c2-116">If the value of this property is a fully qualified path, DSC will not use the **Path** environment variable to find the file, and will throw an error if the path does not exist.</span></span> <span data-ttu-id="ce8c2-117">Göreli yollar izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="ce8c2-117">Relative paths are not allowed.</span></span>|
| <span data-ttu-id="ce8c2-118">Kimlik bilgisi</span><span class="sxs-lookup"><span data-stu-id="ce8c2-118">Credential</span></span>| <span data-ttu-id="ce8c2-119">İşlemi başlatmak için kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ce8c2-119">Indicates the credentials for starting the process.</span></span>|
| <span data-ttu-id="ce8c2-120">Emin olun</span><span class="sxs-lookup"><span data-stu-id="ce8c2-120">Ensure</span></span>| <span data-ttu-id="ce8c2-121">Bir işlem olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ce8c2-121">Indicates if the process exists.</span></span> <span data-ttu-id="ce8c2-122">Bu işlem var olduğundan emin olmak için "var" özelliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ce8c2-122">Set this property to "Present" to ensure that the process exists.</span></span> <span data-ttu-id="ce8c2-123">Aksi takdirde, "Yok" ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ce8c2-123">Otherwise, set it to "Absent".</span></span> <span data-ttu-id="ce8c2-124">"Var" varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="ce8c2-124">The default is "Present".</span></span>|
| <span data-ttu-id="ce8c2-125">DependsOn</span><span class="sxs-lookup"><span data-stu-id="ce8c2-125">DependsOn</span></span> | <span data-ttu-id="ce8c2-126">Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ce8c2-126">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="ce8c2-127">Örneğin, kaynak yapılandırmasının Kimliğini çalıştırmak istediğiniz bir blok betik ilk ise **ResourceName** ve kendi türünün **ResourceType**, bu özelliği kullanmak için söz dizimi ' DependsOn "[= ResourceType] ResourceName"''.</span><span class="sxs-lookup"><span data-stu-id="ce8c2-127">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\` .</span></span>|
| <span data-ttu-id="ce8c2-128">StandardErrorPath</span><span class="sxs-lookup"><span data-stu-id="ce8c2-128">StandardErrorPath</span></span>| <span data-ttu-id="ce8c2-129">Standart hatayı yazmak için dizin yolu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ce8c2-129">Indicates the directory path to write the standard error.</span></span> <span data-ttu-id="ce8c2-130">Var. Varolan dosyanın üzerine yazılır.</span><span class="sxs-lookup"><span data-stu-id="ce8c2-130">Any existing file there will be overwritten.</span></span>|
| <span data-ttu-id="ce8c2-131">StandardInputPath</span><span class="sxs-lookup"><span data-stu-id="ce8c2-131">StandardInputPath</span></span>| <span data-ttu-id="ce8c2-132">Standart giriş konumu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ce8c2-132">Indicates the standard input location.</span></span>|
| <span data-ttu-id="ce8c2-133">StandardOutputPath</span><span class="sxs-lookup"><span data-stu-id="ce8c2-133">StandardOutputPath</span></span>| <span data-ttu-id="ce8c2-134">Standart çıkışını yazmak için konumu belirtir.</span><span class="sxs-lookup"><span data-stu-id="ce8c2-134">Indicates the location to write the standard output.</span></span> <span data-ttu-id="ce8c2-135">Var. Varolan dosyanın üzerine yazılır.</span><span class="sxs-lookup"><span data-stu-id="ce8c2-135">Any existing file there will be overwritten.</span></span>|
| <span data-ttu-id="ce8c2-136">WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="ce8c2-136">WorkingDirectory</span></span>| <span data-ttu-id="ce8c2-137">İşlem için geçerli çalışma dizini kullanılacak konumu belirtir.</span><span class="sxs-lookup"><span data-stu-id="ce8c2-137">Indicates the location that will be used as the current working directory for the process.</span></span>|