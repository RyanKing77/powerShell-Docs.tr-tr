---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "DSC arşiv kaynak"
ms.openlocfilehash: 035f7cc1b7f21f7a0df2d72db0ba83bc0688356c
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-archive-resource"></a><span data-ttu-id="1e97b-103">DSC arşiv kaynak</span><span class="sxs-lookup"><span data-stu-id="1e97b-103">DSC Archive Resource</span></span>

> <span data-ttu-id="1e97b-104">İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="1e97b-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="1e97b-105">Arşiv kaynak olarak Windows PowerShell istenen durum yapılandırması (DSC) belirli bir yola arşiv (.zip) dosyalarını açmak için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="1e97b-105">The Archive resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to unpack archive (.zip) files at a specific path.</span></span>

## <a name="syntax"></a><span data-ttu-id="1e97b-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1e97b-106">Syntax</span></span> 
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

## <a name="properties"></a><span data-ttu-id="1e97b-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="1e97b-107">Properties</span></span>

|  <span data-ttu-id="1e97b-108">Özellik</span><span class="sxs-lookup"><span data-stu-id="1e97b-108">Property</span></span>  |  <span data-ttu-id="1e97b-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1e97b-109">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="1e97b-110">Hedef</span><span class="sxs-lookup"><span data-stu-id="1e97b-110">Destination</span></span>| <span data-ttu-id="1e97b-111">Arşiv içeriği ayıklanır sağlamak istediğiniz konumu belirtir.</span><span class="sxs-lookup"><span data-stu-id="1e97b-111">Specifies the location where you want to ensure the archive contents are extracted.</span></span>| 
| <span data-ttu-id="1e97b-112">Yol</span><span class="sxs-lookup"><span data-stu-id="1e97b-112">Path</span></span>| <span data-ttu-id="1e97b-113">Arşiv dosyasını kaynak yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="1e97b-113">Specifies the source path of the archive file.</span></span>| 
| <span data-ttu-id="1e97b-114">__Sağlama toplamı__</span><span class="sxs-lookup"><span data-stu-id="1e97b-114">__Checksum__</span></span>| <span data-ttu-id="1e97b-115">İki dosya aynı olup olmadığını belirlerken kullanılacak türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1e97b-115">Defines the type to use when determining whether two files are the same.</span></span> <span data-ttu-id="1e97b-116">Varsa __sağlama toplamı__ belirtilmezse, yalnızca dosya veya dizin adı karşılaştırma için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1e97b-116">If __Checksum__ is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="1e97b-117">Geçerli değerler şunlardır: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate, none (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="1e97b-117">Valid values include: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate, none (default).</span></span> <span data-ttu-id="1e97b-118">Belirtirseniz __sağlama toplamı__ olmadan __doğrulama__, yapılandırma başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="1e97b-118">If you specify __Checksum__ without __Validate__, the configuration will fail.</span></span>| 
| <span data-ttu-id="1e97b-119">Emin olun</span><span class="sxs-lookup"><span data-stu-id="1e97b-119">Ensure</span></span>| <span data-ttu-id="1e97b-120">Arşiv içeriğini adresindeki var olup olmadığını denetlemek belirler __hedef__.</span><span class="sxs-lookup"><span data-stu-id="1e97b-120">Determines whether to check if the content of the archive exists at the __Destination__.</span></span> <span data-ttu-id="1e97b-121">Bu özelliği ayarlamak __mevcut__ içeriği mevcut emin olmak için.</span><span class="sxs-lookup"><span data-stu-id="1e97b-121">Set this property to __Present__ to ensure the contents exist.</span></span> <span data-ttu-id="1e97b-122">Ayarlamak __etmeksizin__ mevcut emin olmak için.</span><span class="sxs-lookup"><span data-stu-id="1e97b-122">Set it to __Absent__ to ensure they do not exist.</span></span> <span data-ttu-id="1e97b-123">Varsayılan değer __mevcut__.</span><span class="sxs-lookup"><span data-stu-id="1e97b-123">The default value is __Present__.</span></span>| 
| <span data-ttu-id="1e97b-124">dependsOn</span><span class="sxs-lookup"><span data-stu-id="1e97b-124">DependsOn</span></span> | <span data-ttu-id="1e97b-125">Bu kaynak yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmalısınız gösterir.</span><span class="sxs-lookup"><span data-stu-id="1e97b-125">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="1e97b-126">Örneğin, çalıştırmak istediğiniz kaynak yapılandırma komut dosyası bloğunda Kimliğini ilk KaynakAdı ve onun türü ise __ResourceType__, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="1e97b-126">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 
| <span data-ttu-id="1e97b-127">Doğrula</span><span class="sxs-lookup"><span data-stu-id="1e97b-127">Validate</span></span>| <span data-ttu-id="1e97b-128">Arşiv imza eşleşip eşleşmediğini belirlemek için sağlama özelliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="1e97b-128">Uses the Checksum property to determine if the archive matches the signature.</span></span> <span data-ttu-id="1e97b-129">Sağlama toplamı doğrulama olmadan belirtirseniz, yapılandırma başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="1e97b-129">If you specify Checksum without Validate, the configuration will fail.</span></span> <span data-ttu-id="1e97b-130">SHA-256 sağlama toplamı doğrulama sağlama toplamı olmadan belirtirseniz, varsayılan olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1e97b-130">If you specify Validate without Checksum, a SHA-256 checksum is used by default.</span></span>| 
| <span data-ttu-id="1e97b-131">Force</span><span class="sxs-lookup"><span data-stu-id="1e97b-131">Force</span></span>| <span data-ttu-id="1e97b-132">Belirli dosya işlemleri (örneğin, bir dosyanın üzerine veya boş olmayan bir dizin silme) bir hatayla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="1e97b-132">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="1e97b-133">Zorla özelliğini kullanarak bu tür hatalar geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="1e97b-133">Using the Force property overrides such errors.</span></span> <span data-ttu-id="1e97b-134">Varsayılan değer False olur.</span><span class="sxs-lookup"><span data-stu-id="1e97b-134">The default value is False.</span></span>| 

## <a name="example"></a><span data-ttu-id="1e97b-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="1e97b-135">Example</span></span>

<span data-ttu-id="1e97b-136">Aşağıdaki örnek, arşiv kaynak Test.zip adlı bir arşiv dosyasının içeriğini mevcut ve belirli bir hedefe ayıklanır emin olmak için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1e97b-136">The following example shows how to use the Archive resource to ensure that the contents of an archive file called Test.zip exist and are extracted at a given destination.</span></span>

```
Archive ArchiveExample {
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Path = "C:\Users\Public\Documents\Test.zip"
    Destination = "C:\Users\Public\Documents\ExtractionPath"
} 
```

