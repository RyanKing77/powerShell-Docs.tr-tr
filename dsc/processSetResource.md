---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "DSC ProcessSet kaynağı"
ms.openlocfilehash: b713d1a9c34eab6966de4f342991ead32c19df5d
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-windowsprocess-resource"></a><span data-ttu-id="c1f9f-103">DSC WindowsProcess kaynağı</span><span class="sxs-lookup"><span data-stu-id="c1f9f-103">DSC WindowsProcess Resource</span></span>

> <span data-ttu-id="c1f9f-104">İçin geçerlidir: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="c1f9f-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="c1f9f-105">**ProcessSet** kaynağı içinde Windows PowerShell istenen durum yapılandırması (DSC), bir hedef düğümde işlemlerini yapılandırmak için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="c1f9f-105">The **ProcessSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to configure processes on a target node.</span></span> <span data-ttu-id="c1f9f-106">Bu kaynak olmadığı bir [bileşik kaynak](authoringResourceComposite.md) çağrısı [WindowsProcess kaynak](windowsProcessResource.md) belirtilen her grup için `GroupName` parametresi.</span><span class="sxs-lookup"><span data-stu-id="c1f9f-106">This resource is a [composite resource](authoringResourceComposite.md) that calls the [WindowsProcess resource](windowsProcessResource.md) for each group specified in the `GroupName` parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="c1f9f-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c1f9f-107">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="c1f9f-108">Özellikler</span><span class="sxs-lookup"><span data-stu-id="c1f9f-108">Properties</span></span>
|  <span data-ttu-id="c1f9f-109">Özellik</span><span class="sxs-lookup"><span data-stu-id="c1f9f-109">Property</span></span>  |  <span data-ttu-id="c1f9f-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c1f9f-110">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="c1f9f-111">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="c1f9f-111">Arguments</span></span>| <span data-ttu-id="c1f9f-112">İşlem olarak geçirilecek bağımsız değişkenleri içeren bir dize-değil.</span><span class="sxs-lookup"><span data-stu-id="c1f9f-112">A string that contains arguments to pass to the process as-is.</span></span> <span data-ttu-id="c1f9f-113">Birden fazla bağımsız değişken geçirmek gerekiyorsa, bunları bu dize tüm yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="c1f9f-113">If you need to pass several arguments, put them all in this string.</span></span>| 
| <span data-ttu-id="c1f9f-114">Yol</span><span class="sxs-lookup"><span data-stu-id="c1f9f-114">Path</span></span>| <span data-ttu-id="c1f9f-115">İşlem yürütülebilir dosya yolları.</span><span class="sxs-lookup"><span data-stu-id="c1f9f-115">The paths to the process executables.</span></span> <span data-ttu-id="c1f9f-116">Bunlar yürütülebilir dosyaları (tam olarak nitelenmiş yollar) adlarını varsa, DSC kaynağı ortam arama **yolu** değişkeni (`$env:Path`) dosyaları bulmak için.</span><span class="sxs-lookup"><span data-stu-id="c1f9f-116">If these are the names of the executable files (not fully qualified paths), the DSC resource will search the environment **Path** variable (`$env:Path`) to find the files.</span></span> <span data-ttu-id="c1f9f-117">Bu özelliğin değerleri, tam yol varsa, DSC kullanmaz **yolu** dosyaları bulmak için ortam değişkeni ve yolların yoksa bir hata özel durum oluşturacak.</span><span class="sxs-lookup"><span data-stu-id="c1f9f-117">If the values of this property are fully qualified paths, DSC will not use the **Path** environment variable to find the files, and will throw an error if any of the paths do not exist.</span></span> <span data-ttu-id="c1f9f-118">Göreli yollar izin verilmiyor.</span><span class="sxs-lookup"><span data-stu-id="c1f9f-118">Relative paths are not allowed.</span></span>| 
| <span data-ttu-id="c1f9f-119">kimlik bilgisi</span><span class="sxs-lookup"><span data-stu-id="c1f9f-119">Credential</span></span>| <span data-ttu-id="c1f9f-120">İşlemi başlatmak için kimlik bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c1f9f-120">Indicates the credentials for starting the process.</span></span>| 
| <span data-ttu-id="c1f9f-121">Emin olun</span><span class="sxs-lookup"><span data-stu-id="c1f9f-121">Ensure</span></span>| <span data-ttu-id="c1f9f-122">İşlemler var olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c1f9f-122">Specifies whether the processes exists.</span></span> <span data-ttu-id="c1f9f-123">Bu özelliği işlemi var olduğundan emin olmak için "var" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c1f9f-123">Set this property to "Present" to ensure that the process exists.</span></span> <span data-ttu-id="c1f9f-124">Aksi takdirde, "Yok" ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c1f9f-124">Otherwise, set it to "Absent".</span></span> <span data-ttu-id="c1f9f-125">"Var" varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="c1f9f-125">The default is "Present".</span></span>| 
| <span data-ttu-id="c1f9f-126">StandardErrorPath</span><span class="sxs-lookup"><span data-stu-id="c1f9f-126">StandardErrorPath</span></span>| <span data-ttu-id="c1f9f-127">İşlemler yazma standart hatası yolu.</span><span class="sxs-lookup"><span data-stu-id="c1f9f-127">The path to which the processes write standard error.</span></span> <span data-ttu-id="c1f9f-128">Var. Varolan dosyanın üzerine yazılır.</span><span class="sxs-lookup"><span data-stu-id="c1f9f-128">Any existing file there will be overwritten.</span></span>| 
| <span data-ttu-id="c1f9f-129">StandardInputPath</span><span class="sxs-lookup"><span data-stu-id="c1f9f-129">StandardInputPath</span></span>| <span data-ttu-id="c1f9f-130">İşlem standart giriş aldığı akış.</span><span class="sxs-lookup"><span data-stu-id="c1f9f-130">The stream from which the process receives standard input.</span></span>| 
| <span data-ttu-id="c1f9f-131">StandardOutputPath</span><span class="sxs-lookup"><span data-stu-id="c1f9f-131">StandardOutputPath</span></span>| <span data-ttu-id="c1f9f-132">Standart çıktı yazma işlemleri için dosyanın yolu.</span><span class="sxs-lookup"><span data-stu-id="c1f9f-132">The path of the file to which the processes write standard output.</span></span> <span data-ttu-id="c1f9f-133">Var. Varolan dosyanın üzerine yazılır.</span><span class="sxs-lookup"><span data-stu-id="c1f9f-133">Any existing file there will be overwritten.</span></span>| 
| <span data-ttu-id="c1f9f-134">WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="c1f9f-134">WorkingDirectory</span></span>| <span data-ttu-id="c1f9f-135">Geçerli çalışma dizini olarak işlemleri için kullanılan konumu.</span><span class="sxs-lookup"><span data-stu-id="c1f9f-135">The location used as the current working directory for the processes.</span></span>| 
| <span data-ttu-id="c1f9f-136">dependsOn</span><span class="sxs-lookup"><span data-stu-id="c1f9f-136">DependsOn</span></span> | <span data-ttu-id="c1f9f-137">Bu kaynak yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmalısınız gösterir.</span><span class="sxs-lookup"><span data-stu-id="c1f9f-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="c1f9f-138">Örneğin, kaynak yapılandırması Kimliğini komut dosyası çalıştırmak istediğiniz bloğu ilk ise **ResourceName** ve türünü **_ResourceType**, bu özelliği kullanmak için sözdizimi ' DependsOn = "[ ResourceType] KaynakAdı"''.</span><span class="sxs-lookup"><span data-stu-id="c1f9f-138">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **_ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`\` .</span></span>| 

