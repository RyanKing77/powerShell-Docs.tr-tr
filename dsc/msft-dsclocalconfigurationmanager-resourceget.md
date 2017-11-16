---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "MSFT_DSCLocalConfigurationManager sınıfının ResourceGet yöntemi"
ms.openlocfilehash: 7d8b185c49778253dcb4e983ad948775c4cb0842
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="resourceget-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="84e25-103">MSFT_DSCLocalConfigurationManager sınıfının ResourceGet yöntemi</span><span class="sxs-lookup"><span data-stu-id="84e25-103">ResourceGet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="84e25-104">Doğrudan çağıran **almak** DSC kaynağı yöntemi.</span><span class="sxs-lookup"><span data-stu-id="84e25-104">Directly calls the **Get** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="84e25-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="84e25-105">Syntax</span></span>
------

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

<a name="parameters"></a><span data-ttu-id="84e25-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="84e25-106">Parameters</span></span>
----------

<span data-ttu-id="84e25-107">*ResourceType* \[içinde\]</span><span class="sxs-lookup"><span data-stu-id="84e25-107">*ResourceType* \[in\]</span></span>  
<span data-ttu-id="84e25-108">Çağrılacak kaynağının adı.</span><span class="sxs-lookup"><span data-stu-id="84e25-108">The name of the resource to call.</span></span>

<span data-ttu-id="84e25-109">*ModuleName* \[içinde\]</span><span class="sxs-lookup"><span data-stu-id="84e25-109">*ModuleName* \[in\]</span></span>  
<span data-ttu-id="84e25-110">Aranacak kaynak içeren modülü adı.</span><span class="sxs-lookup"><span data-stu-id="84e25-110">The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="84e25-111">*resourceProperty* \[içinde\]</span><span class="sxs-lookup"><span data-stu-id="84e25-111">*resourceProperty* \[in\]</span></span>  
<span data-ttu-id="84e25-112">Kaynak özelliği adını ve değerini bir karma tablosunda anahtar ve değer sırasıyla belirtir.</span><span class="sxs-lookup"><span data-stu-id="84e25-112">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="84e25-113">Kullanım [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) kaynak özelliklerini ve bunların türlerini bulmak için cmdlet.</span><span class="sxs-lookup"><span data-stu-id="84e25-113">Use the [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="84e25-114">*yapılandırmaları* \[çıkışı\]</span><span class="sxs-lookup"><span data-stu-id="84e25-114">*configurations* \[out\]</span></span>  
<span data-ttu-id="84e25-115">Getirisi, katıştırılmış yapılandırmaları örneğini içerir.</span><span class="sxs-lookup"><span data-stu-id="84e25-115">On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="84e25-116">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="84e25-116">Return value</span></span>
------------

<span data-ttu-id="84e25-117">Başarı sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="84e25-117">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="84e25-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="84e25-118">Remarks</span></span>

<span data-ttu-id="84e25-119">Bu statik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="84e25-119">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="84e25-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="84e25-120">Requirements</span></span>
------------
><span data-ttu-id="84e25-121">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="84e25-121">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="84e25-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="84e25-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="84e25-123">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="84e25-123">See also</span></span>


[<span data-ttu-id="84e25-124">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="84e25-124">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



