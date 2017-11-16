---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "DSC WindowsProcess kaynağı"
ms.openlocfilehash: c34d3cb1d4d9b899b45fba7b4b148a7c977f5365
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-windowsprocess-resource"></a><span data-ttu-id="ead6e-103">DSC WindowsProcess kaynağı</span><span class="sxs-lookup"><span data-stu-id="ead6e-103">DSC WindowsProcess Resource</span></span>

> <span data-ttu-id="ead6e-104">İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="ead6e-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="ead6e-105">**WindowsProcess** kaynağı içinde Windows PowerShell istenen durum yapılandırması (DSC), bir hedef düğümde işlemlerini yapılandırmak için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="ead6e-105">The **WindowsProcess** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to configure processes on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="ead6e-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ead6e-106">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="ead6e-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="ead6e-107">Properties</span></span>
|  <span data-ttu-id="ead6e-108">Özellik</span><span class="sxs-lookup"><span data-stu-id="ead6e-108">Property</span></span>  |  <span data-ttu-id="ead6e-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ead6e-109">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="ead6e-110">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="ead6e-110">Arguments</span></span>| <span data-ttu-id="ead6e-111">Bir işlem olarak geçirilecek bağımsız değişkenleri dizisini gösterir-değil.</span><span class="sxs-lookup"><span data-stu-id="ead6e-111">Indicates a string of arguments to pass to the process as-is.</span></span> <span data-ttu-id="ead6e-112">Birden fazla bağımsız değişken geçirmek gerekiyorsa, bunları bu dize tüm yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="ead6e-112">If you need to pass several arguments, put them all in this string.</span></span>| 
| <span data-ttu-id="ead6e-113">Yol</span><span class="sxs-lookup"><span data-stu-id="ead6e-113">Path</span></span>| <span data-ttu-id="ead6e-114">İşlem yürütülebilir dosyası yolu.</span><span class="sxs-lookup"><span data-stu-id="ead6e-114">The path to the process executable.</span></span> <span data-ttu-id="ead6e-115">Bu ortam çalıştırılabilir dosyanın (olmayan tam yolunu), DSC kaynağı dosya adını arayacaktır **yolu** değişkeni (`$env:Path`) yürütülebilir dosyası bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="ead6e-115">If this the file name of the executable (not the fully qualified path), the DSC resource will search the environment **Path** variable (`$env:Path`) to find the executable file.</span></span> <span data-ttu-id="ead6e-116">Bu özelliğin değeri tam bir yol ise, DSC kullanmaz **yolu** dosyayı bulmak için ortam değişkeni ve yol yoksa, bir hata özel durum oluşturacak.</span><span class="sxs-lookup"><span data-stu-id="ead6e-116">If the value of this property is a fully qualified path, DSC will not use the **Path** environment variable to find the file, and will throw an error if the path does not exist.</span></span> <span data-ttu-id="ead6e-117">Göreli yollar izin verilmiyor.</span><span class="sxs-lookup"><span data-stu-id="ead6e-117">Relative paths are not allowed.</span></span>| 
| <span data-ttu-id="ead6e-118">kimlik bilgisi</span><span class="sxs-lookup"><span data-stu-id="ead6e-118">Credential</span></span>| <span data-ttu-id="ead6e-119">İşlemi başlatmak için kimlik bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ead6e-119">Indicates the credentials for starting the process.</span></span>| 
| <span data-ttu-id="ead6e-120">Emin olun</span><span class="sxs-lookup"><span data-stu-id="ead6e-120">Ensure</span></span>| <span data-ttu-id="ead6e-121">İşlem var olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ead6e-121">Indicates if the process exists.</span></span> <span data-ttu-id="ead6e-122">Bu özelliği işlemi var olduğundan emin olmak için "var" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ead6e-122">Set this property to "Present" to ensure that the process exists.</span></span> <span data-ttu-id="ead6e-123">Aksi takdirde, "Yok" ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ead6e-123">Otherwise, set it to "Absent".</span></span> <span data-ttu-id="ead6e-124">"Var" varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="ead6e-124">The default is "Present".</span></span>| 
| <span data-ttu-id="ead6e-125">dependsOn</span><span class="sxs-lookup"><span data-stu-id="ead6e-125">DependsOn</span></span> | <span data-ttu-id="ead6e-126">Bu kaynak yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmalısınız gösterir.</span><span class="sxs-lookup"><span data-stu-id="ead6e-126">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="ead6e-127">Örneğin, kaynak yapılandırması Kimliğini komut dosyası çalıştırmak istediğiniz bloğu ilk ise __ResourceName__ ve türünü __ResourceType__, bu özelliği kullanmak için sözdizimi ' DependsOn = "[ ResourceType] KaynakAdı"''.</span><span class="sxs-lookup"><span data-stu-id="ead6e-127">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`\` .</span></span>| 
| <span data-ttu-id="ead6e-128">StandardErrorPath</span><span class="sxs-lookup"><span data-stu-id="ead6e-128">StandardErrorPath</span></span>| <span data-ttu-id="ead6e-129">Standart hatayı yazmak için dizin yolu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ead6e-129">Indicates the directory path to write the standard error.</span></span> <span data-ttu-id="ead6e-130">Var. Varolan dosyanın üzerine yazılır.</span><span class="sxs-lookup"><span data-stu-id="ead6e-130">Any existing file there will be overwritten.</span></span>| 
| <span data-ttu-id="ead6e-131">StandardInputPath</span><span class="sxs-lookup"><span data-stu-id="ead6e-131">StandardInputPath</span></span>| <span data-ttu-id="ead6e-132">Standart giriş konumu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ead6e-132">Indicates the standard input location.</span></span>| 
| <span data-ttu-id="ead6e-133">StandardOutputPath</span><span class="sxs-lookup"><span data-stu-id="ead6e-133">StandardOutputPath</span></span>| <span data-ttu-id="ead6e-134">Standart çıktı yazmak için konumu belirtir.</span><span class="sxs-lookup"><span data-stu-id="ead6e-134">Indicates the location to write the standard output.</span></span> <span data-ttu-id="ead6e-135">Var. Varolan dosyanın üzerine yazılır.</span><span class="sxs-lookup"><span data-stu-id="ead6e-135">Any existing file there will be overwritten.</span></span>| 
| <span data-ttu-id="ead6e-136">WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="ead6e-136">WorkingDirectory</span></span>| <span data-ttu-id="ead6e-137">Geçerli çalışma dizini olarak işlemi için kullanılacak konumu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ead6e-137">Indicates the location that will be used as the current working directory for the process.</span></span>| 

