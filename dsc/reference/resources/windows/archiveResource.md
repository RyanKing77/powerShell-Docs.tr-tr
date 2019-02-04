---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC Archive kaynağı
ms.openlocfilehash: d5ccd242d000a0907c6768f30923764be6bf20a3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688409"
---
# <a name="dsc-archive-resource"></a><span data-ttu-id="69a07-103">DSC Archive kaynağı</span><span class="sxs-lookup"><span data-stu-id="69a07-103">DSC Archive Resource</span></span>

> <span data-ttu-id="69a07-104">Şunun için geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="69a07-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="69a07-105">Archive kaynağı, Windows PowerShell Desired State Configuration (DSC), belirli bir yola arşiv (.zip) dosyalarını açmak için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="69a07-105">The Archive resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to unpack archive (.zip) files at a specific path.</span></span>

## <a name="syntax"></a><span data-ttu-id="69a07-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="69a07-106">Syntax</span></span>
```MOF
Archive [string] #ResourceName
{
    Destination = [string]
    Path = [string]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Force = [bool] ]
    [ Validate = [bool] ]
}
```

## <a name="properties"></a><span data-ttu-id="69a07-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="69a07-107">Properties</span></span>

|  <span data-ttu-id="69a07-108">Özellik</span><span class="sxs-lookup"><span data-stu-id="69a07-108">Property</span></span>  |  <span data-ttu-id="69a07-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="69a07-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="69a07-110">Hedef</span><span class="sxs-lookup"><span data-stu-id="69a07-110">Destination</span></span>| <span data-ttu-id="69a07-111">Arşiv içeriğini ayıklanan sağlamak istediğiniz konumu belirtir.</span><span class="sxs-lookup"><span data-stu-id="69a07-111">Specifies the location where you want to ensure the archive contents are extracted.</span></span>|
| <span data-ttu-id="69a07-112">Yol</span><span class="sxs-lookup"><span data-stu-id="69a07-112">Path</span></span>| <span data-ttu-id="69a07-113">Arşiv dosyasının kaynak yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="69a07-113">Specifies the source path of the archive file.</span></span>|
| <span data-ttu-id="69a07-114">__Sağlama toplamı__</span><span class="sxs-lookup"><span data-stu-id="69a07-114">__Checksum__</span></span>| <span data-ttu-id="69a07-115">İki dosya aynı olup olmadığını belirlerken kullanılacak türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="69a07-115">Defines the type to use when determining whether two files are the same.</span></span> <span data-ttu-id="69a07-116">Varsa __sağlama toplamı__ belirtilmezse, yalnızca dosya veya dizin adı, karşılaştırma için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="69a07-116">If __Checksum__ is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="69a07-117">Geçerli değerler şunlardır: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate, Hiçbiri (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="69a07-117">Valid values include: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate, none (default).</span></span> <span data-ttu-id="69a07-118">Belirtirseniz __sağlama toplamı__ olmadan __doğrulama__, yapılandırmanız başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="69a07-118">If you specify __Checksum__ without __Validate__, the configuration will fail.</span></span>|
| <span data-ttu-id="69a07-119">Emin olun</span><span class="sxs-lookup"><span data-stu-id="69a07-119">Ensure</span></span>| <span data-ttu-id="69a07-120">Arşiv içeriğini, mevcut olup olmadığını denetleyin belirler __hedef__.</span><span class="sxs-lookup"><span data-stu-id="69a07-120">Determines whether to check if the content of the archive exists at the __Destination__.</span></span> <span data-ttu-id="69a07-121">Bu özellik kümesine __mevcut__ içeriği mevcut emin olmak için.</span><span class="sxs-lookup"><span data-stu-id="69a07-121">Set this property to __Present__ to ensure the contents exist.</span></span> <span data-ttu-id="69a07-122">Ayarlayın __devamsızlık__ mevcut emin olmak için.</span><span class="sxs-lookup"><span data-stu-id="69a07-122">Set it to __Absent__ to ensure they do not exist.</span></span> <span data-ttu-id="69a07-123">Varsayılan değer __mevcut__.</span><span class="sxs-lookup"><span data-stu-id="69a07-123">The default value is __Present__.</span></span>|
| <span data-ttu-id="69a07-124">DependsOn</span><span class="sxs-lookup"><span data-stu-id="69a07-124">DependsOn</span></span> | <span data-ttu-id="69a07-125">Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="69a07-125">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="69a07-126">Örneğin, çalıştırmak istediğiniz kaynak yapılandırma komut dosyası bloğu Kimliğini ilk ResourceName ve onun türü ise __ResourceType__, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="69a07-126">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="69a07-127">Doğrulama</span><span class="sxs-lookup"><span data-stu-id="69a07-127">Validate</span></span>| <span data-ttu-id="69a07-128">Arşiv imza eşleşip eşleşmediğini belirlemek için sağlama toplamı özelliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="69a07-128">Uses the Checksum property to determine if the archive matches the signature.</span></span> <span data-ttu-id="69a07-129">Sağlama toplamı doğrulama olmadan belirtirseniz, yapılandırma başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="69a07-129">If you specify Checksum without Validate, the configuration will fail.</span></span> <span data-ttu-id="69a07-130">SHA-256'yı sağlama toplamı, olmadan sağlama toplamı doğrulama belirtirseniz, varsayılan olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="69a07-130">If you specify Validate without Checksum, a SHA-256 checksum is used by default.</span></span>|
| <span data-ttu-id="69a07-131">Force</span><span class="sxs-lookup"><span data-stu-id="69a07-131">Force</span></span>| <span data-ttu-id="69a07-132">Belirli dosya işlemleri (örneğin, bir dosyanın üzerine veya boş olmayan bir dizini silme) bir hataya neden olur.</span><span class="sxs-lookup"><span data-stu-id="69a07-132">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="69a07-133">Zorla özelliğini kullanarak bu tür hatalar geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="69a07-133">Using the Force property overrides such errors.</span></span> <span data-ttu-id="69a07-134">Varsayılan değer False olur.</span><span class="sxs-lookup"><span data-stu-id="69a07-134">The default value is False.</span></span>|

## <a name="example"></a><span data-ttu-id="69a07-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="69a07-135">Example</span></span>

<span data-ttu-id="69a07-136">Aşağıdaki örnek Archive kaynağı Test.zip adlı bir arşiv dosyasının içeriğini mevcut ve belirli bir hedefe ayıklanan emin olmak için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="69a07-136">The following example shows how to use the Archive resource to ensure that the contents of an archive file called Test.zip exist and are extracted at a given destination.</span></span>

```
Archive ArchiveExample {
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Path = "C:\Users\Public\Documents\Test.zip"
    Destination = "C:\Users\Public\Documents\ExtractionPath"
}
```