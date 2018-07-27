---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC ProcessSet kaynağı
ms.openlocfilehash: 33000786a9e17e11168b5e08c3bcfcacf3af2611
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/26/2018
ms.locfileid: "39268026"
---
# <a name="dsc-windowsprocess-resource"></a><span data-ttu-id="703eb-103">DSC WindowsProcess kaynağı</span><span class="sxs-lookup"><span data-stu-id="703eb-103">DSC WindowsProcess Resource</span></span>

<span data-ttu-id="703eb-104">_Uygulama hedefi: Windows PowerShell 5.0_</span><span class="sxs-lookup"><span data-stu-id="703eb-104">_Applies To: Windows PowerShell 5.0_</span></span>

<span data-ttu-id="703eb-105">**ProcessSet** kaynak içinde Windows PowerShell Desired State Configuration (DSC), bir hedef düğümde işlemlerini yapılandırmak için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="703eb-105">The **ProcessSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to configure processes on a target node.</span></span> <span data-ttu-id="703eb-106">Bu kaynak bir [bileşik kaynak](authoringResourceComposite.md) çağrılarının [WindowsProcess kaynağı](windowsProcessResource.md) belirtilen her grup için `GroupName` parametresi.</span><span class="sxs-lookup"><span data-stu-id="703eb-106">This resource is a [composite resource](authoringResourceComposite.md) that calls the [WindowsProcess resource](windowsProcessResource.md) for each group specified in the `GroupName` parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="703eb-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="703eb-107">Syntax</span></span>

```
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ StandardOutputPath = [string] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ WorkingDirectory = [string] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="703eb-108">Özellikler</span><span class="sxs-lookup"><span data-stu-id="703eb-108">Properties</span></span>

| <span data-ttu-id="703eb-109">Özellik</span><span class="sxs-lookup"><span data-stu-id="703eb-109">Property</span></span> | <span data-ttu-id="703eb-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="703eb-110">Description</span></span> |
| --- | --- |
| <span data-ttu-id="703eb-111">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="703eb-111">Arguments</span></span>| <span data-ttu-id="703eb-112">İşlem olarak geçirilecek bağımsız değişkenleri içeren bir dize-olduğu.</span><span class="sxs-lookup"><span data-stu-id="703eb-112">A string that contains arguments to pass to the process as-is.</span></span> <span data-ttu-id="703eb-113">Birden çok bağımsız değişkenleri geçirmek gerekiyorsa, bunları bu dize tüm yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="703eb-113">If you need to pass several arguments, put them all in this string.</span></span>|
| <span data-ttu-id="703eb-114">Yol</span><span class="sxs-lookup"><span data-stu-id="703eb-114">Path</span></span>| <span data-ttu-id="703eb-115">İşlem yürütülebilir dosya yolları.</span><span class="sxs-lookup"><span data-stu-id="703eb-115">The paths to the process executables.</span></span> <span data-ttu-id="703eb-116">Bunlar yürütülebilir dosyaları (tam olarak nitelenmiş yollar) adlarıdır, DSC kaynak ortam arar **yolu** değişkeni (`$env:Path`) dosyaları bulmak için.</span><span class="sxs-lookup"><span data-stu-id="703eb-116">If these are the names of the executable files (not fully qualified paths), the DSC resource will search the environment **Path** variable (`$env:Path`) to find the files.</span></span> <span data-ttu-id="703eb-117">Bu özellik değerlerini tam olarak nitelenmiş yollar, DSC kullanmaz **yolu** dosyaları bulmak için ortam değişkeni ve yoksa yolların herhangi bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="703eb-117">If the values of this property are fully qualified paths, DSC will not use the **Path** environment variable to find the files, and will throw an error if any of the paths do not exist.</span></span> <span data-ttu-id="703eb-118">Göreli yollar izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="703eb-118">Relative paths are not allowed.</span></span>|
| <span data-ttu-id="703eb-119">Kimlik bilgisi</span><span class="sxs-lookup"><span data-stu-id="703eb-119">Credential</span></span>| <span data-ttu-id="703eb-120">İşlemi başlatmak için kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="703eb-120">Indicates the credentials for starting the process.</span></span>|
| <span data-ttu-id="703eb-121">Emin olun</span><span class="sxs-lookup"><span data-stu-id="703eb-121">Ensure</span></span>| <span data-ttu-id="703eb-122">İşlemler var olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="703eb-122">Specifies whether the processes exists.</span></span> <span data-ttu-id="703eb-123">Bu işlem var olduğundan emin olmak için "var" özelliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="703eb-123">Set this property to "Present" to ensure that the process exists.</span></span> <span data-ttu-id="703eb-124">Aksi takdirde, "Yok" ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="703eb-124">Otherwise, set it to "Absent".</span></span> <span data-ttu-id="703eb-125">"Var" varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="703eb-125">The default is "Present".</span></span>|
| <span data-ttu-id="703eb-126">StandardErrorPath</span><span class="sxs-lookup"><span data-stu-id="703eb-126">StandardErrorPath</span></span>| <span data-ttu-id="703eb-127">Standart hata yazma işlemleri için yolu.</span><span class="sxs-lookup"><span data-stu-id="703eb-127">The path to which the processes write standard error.</span></span> <span data-ttu-id="703eb-128">Var. Varolan dosyanın üzerine yazılır.</span><span class="sxs-lookup"><span data-stu-id="703eb-128">Any existing file there will be overwritten.</span></span>|
| <span data-ttu-id="703eb-129">StandardInputPath</span><span class="sxs-lookup"><span data-stu-id="703eb-129">StandardInputPath</span></span>| <span data-ttu-id="703eb-130">İşlem standart giriş aldığı akış.</span><span class="sxs-lookup"><span data-stu-id="703eb-130">The stream from which the process receives standard input.</span></span>|
| <span data-ttu-id="703eb-131">StandardOutputPath</span><span class="sxs-lookup"><span data-stu-id="703eb-131">StandardOutputPath</span></span>| <span data-ttu-id="703eb-132">Standart çıkış yazma işlemleri için dosyanın yolu.</span><span class="sxs-lookup"><span data-stu-id="703eb-132">The path of the file to which the processes write standard output.</span></span> <span data-ttu-id="703eb-133">Var. Varolan dosyanın üzerine yazılır.</span><span class="sxs-lookup"><span data-stu-id="703eb-133">Any existing file there will be overwritten.</span></span>|
| <span data-ttu-id="703eb-134">WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="703eb-134">WorkingDirectory</span></span>| <span data-ttu-id="703eb-135">Geçerli çalışma dizini işlemleri için kullanılan konum.</span><span class="sxs-lookup"><span data-stu-id="703eb-135">The location used as the current working directory for the processes.</span></span>|
| <span data-ttu-id="703eb-136">DependsOn</span><span class="sxs-lookup"><span data-stu-id="703eb-136">DependsOn</span></span> | <span data-ttu-id="703eb-137">Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="703eb-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="703eb-138">Örneğin, kaynak yapılandırmasının Kimliğini çalıştırmak istediğiniz bir blok betik ilk ise **ResourceName** ve kendi türünün **_ResourceType**, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="703eb-138">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **_ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"` .</span></span>|