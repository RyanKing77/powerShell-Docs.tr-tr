---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: DSC ProcessSet kaynağı
ms.openlocfilehash: 412cf1076996126f0d9b7a9a8ebbc9bdb7ecf377
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189933"
---
# <a name="dsc-windowsprocess-resource"></a><span data-ttu-id="a0286-103">DSC WindowsProcess kaynağı</span><span class="sxs-lookup"><span data-stu-id="a0286-103">DSC WindowsProcess Resource</span></span>

> <span data-ttu-id="a0286-104">İçin geçerlidir: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="a0286-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="a0286-105">**ProcessSet** kaynağı içinde Windows PowerShell istenen durum yapılandırması (DSC), bir hedef düğümde işlemlerini yapılandırmak için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="a0286-105">The **ProcessSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to configure processes on a target node.</span></span> <span data-ttu-id="a0286-106">Bu kaynak olmadığı bir [bileşik kaynak](authoringResourceComposite.md) çağrısı [WindowsProcess kaynak](windowsProcessResource.md) belirtilen her grup için `GroupName` parametresi.</span><span class="sxs-lookup"><span data-stu-id="a0286-106">This resource is a [composite resource](authoringResourceComposite.md) that calls the [WindowsProcess resource](windowsProcessResource.md) for each group specified in the `GroupName` parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="a0286-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a0286-107">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="a0286-108">Özellikler</span><span class="sxs-lookup"><span data-stu-id="a0286-108">Properties</span></span>
|  <span data-ttu-id="a0286-109">Özellik</span><span class="sxs-lookup"><span data-stu-id="a0286-109">Property</span></span>  |  <span data-ttu-id="a0286-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a0286-110">Description</span></span>   |
|---|---|
| <span data-ttu-id="a0286-111">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="a0286-111">Arguments</span></span>| <span data-ttu-id="a0286-112">İşlem olarak geçirilecek bağımsız değişkenleri içeren bir dize-değil.</span><span class="sxs-lookup"><span data-stu-id="a0286-112">A string that contains arguments to pass to the process as-is.</span></span> <span data-ttu-id="a0286-113">Birden fazla bağımsız değişken geçirmek gerekiyorsa, bunları bu dize tüm yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="a0286-113">If you need to pass several arguments, put them all in this string.</span></span>|
| <span data-ttu-id="a0286-114">Yol</span><span class="sxs-lookup"><span data-stu-id="a0286-114">Path</span></span>| <span data-ttu-id="a0286-115">İşlem yürütülebilir dosya yolları.</span><span class="sxs-lookup"><span data-stu-id="a0286-115">The paths to the process executables.</span></span> <span data-ttu-id="a0286-116">Bunlar yürütülebilir dosyaları (tam olarak nitelenmiş yollar) adlarını varsa, DSC kaynağı ortam arama **yolu** değişkeni (`$env:Path`) dosyaları bulmak için.</span><span class="sxs-lookup"><span data-stu-id="a0286-116">If these are the names of the executable files (not fully qualified paths), the DSC resource will search the environment **Path** variable (`$env:Path`) to find the files.</span></span> <span data-ttu-id="a0286-117">Bu özelliğin değerleri, tam yol varsa, DSC kullanmaz **yolu** dosyaları bulmak için ortam değişkeni ve yolların yoksa bir hata özel durum oluşturacak.</span><span class="sxs-lookup"><span data-stu-id="a0286-117">If the values of this property are fully qualified paths, DSC will not use the **Path** environment variable to find the files, and will throw an error if any of the paths do not exist.</span></span> <span data-ttu-id="a0286-118">Göreli yollar izin verilmiyor.</span><span class="sxs-lookup"><span data-stu-id="a0286-118">Relative paths are not allowed.</span></span>|
| <span data-ttu-id="a0286-119">kimlik bilgisi</span><span class="sxs-lookup"><span data-stu-id="a0286-119">Credential</span></span>| <span data-ttu-id="a0286-120">İşlemi başlatmak için kimlik bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a0286-120">Indicates the credentials for starting the process.</span></span>|
| <span data-ttu-id="a0286-121">Emin olun</span><span class="sxs-lookup"><span data-stu-id="a0286-121">Ensure</span></span>| <span data-ttu-id="a0286-122">İşlemler var olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a0286-122">Specifies whether the processes exists.</span></span> <span data-ttu-id="a0286-123">Bu özelliği işlemi var olduğundan emin olmak için "var" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a0286-123">Set this property to "Present" to ensure that the process exists.</span></span> <span data-ttu-id="a0286-124">Aksi takdirde, "Yok" ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a0286-124">Otherwise, set it to "Absent".</span></span> <span data-ttu-id="a0286-125">"Var" varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="a0286-125">The default is "Present".</span></span>|
| <span data-ttu-id="a0286-126">StandardErrorPath</span><span class="sxs-lookup"><span data-stu-id="a0286-126">StandardErrorPath</span></span>| <span data-ttu-id="a0286-127">İşlemler yazma standart hatası yolu.</span><span class="sxs-lookup"><span data-stu-id="a0286-127">The path to which the processes write standard error.</span></span> <span data-ttu-id="a0286-128">Var. Varolan dosyanın üzerine yazılır.</span><span class="sxs-lookup"><span data-stu-id="a0286-128">Any existing file there will be overwritten.</span></span>|
| <span data-ttu-id="a0286-129">StandardInputPath</span><span class="sxs-lookup"><span data-stu-id="a0286-129">StandardInputPath</span></span>| <span data-ttu-id="a0286-130">İşlem standart giriş aldığı akış.</span><span class="sxs-lookup"><span data-stu-id="a0286-130">The stream from which the process receives standard input.</span></span>|
| <span data-ttu-id="a0286-131">StandardOutputPath</span><span class="sxs-lookup"><span data-stu-id="a0286-131">StandardOutputPath</span></span>| <span data-ttu-id="a0286-132">Standart çıktı yazma işlemleri için dosyanın yolu.</span><span class="sxs-lookup"><span data-stu-id="a0286-132">The path of the file to which the processes write standard output.</span></span> <span data-ttu-id="a0286-133">Var. Varolan dosyanın üzerine yazılır.</span><span class="sxs-lookup"><span data-stu-id="a0286-133">Any existing file there will be overwritten.</span></span>|
| <span data-ttu-id="a0286-134">WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="a0286-134">WorkingDirectory</span></span>| <span data-ttu-id="a0286-135">Geçerli çalışma dizini olarak işlemleri için kullanılan konumu.</span><span class="sxs-lookup"><span data-stu-id="a0286-135">The location used as the current working directory for the processes.</span></span>|
| <span data-ttu-id="a0286-136">dependsOn</span><span class="sxs-lookup"><span data-stu-id="a0286-136">DependsOn</span></span> | <span data-ttu-id="a0286-137">Bu kaynak yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmalısınız gösterir.</span><span class="sxs-lookup"><span data-stu-id="a0286-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="a0286-138">Örneğin, kaynak yapılandırması Kimliğini komut dosyası çalıştırmak istediğiniz bloğu ilk ise **ResourceName** ve türünü **_ResourceType**, bu özelliği kullanmak için sözdizimi ' DependsOn = "[ ResourceType] KaynakAdı"''.</span><span class="sxs-lookup"><span data-stu-id="a0286-138">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **_ResourceType**, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\` .</span></span>|