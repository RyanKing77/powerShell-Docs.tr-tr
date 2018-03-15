---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "MSFT_DSCLocalConfigurationManager sınıfının ResourceGet yöntemi"
ms.openlocfilehash: 2c055b3fab468f85c9e2f91cf1eaf1a4353b4660
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2018
---
# <a name="resourceget-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="fc354-103">MSFT_DSCLocalConfigurationManager sınıfının ResourceGet yöntemi</span><span class="sxs-lookup"><span data-stu-id="fc354-103">ResourceGet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="fc354-104">Doğrudan çağıran **almak** DSC kaynağı yöntemi.</span><span class="sxs-lookup"><span data-stu-id="fc354-104">Directly calls the **Get** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="fc354-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fc354-105">Syntax</span></span>
------

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

<a name="parameters"></a><span data-ttu-id="fc354-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fc354-106">Parameters</span></span>
----------

<span data-ttu-id="fc354-107">*ResourceType* \[in\]</span><span class="sxs-lookup"><span data-stu-id="fc354-107">*ResourceType* \[in\]</span></span>  
<span data-ttu-id="fc354-108">Çağrılacak kaynağının adı.</span><span class="sxs-lookup"><span data-stu-id="fc354-108">The name of the resource to call.</span></span>

<span data-ttu-id="fc354-109">*ModuleName* \[in\]</span><span class="sxs-lookup"><span data-stu-id="fc354-109">*ModuleName* \[in\]</span></span>  
<span data-ttu-id="fc354-110">Aranacak kaynak içeren modülü adı.</span><span class="sxs-lookup"><span data-stu-id="fc354-110">The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="fc354-111">*resourceProperty* \[in\]</span><span class="sxs-lookup"><span data-stu-id="fc354-111">*resourceProperty* \[in\]</span></span>  
<span data-ttu-id="fc354-112">Kaynak özelliği adını ve değerini bir karma tablosunda anahtar ve değer sırasıyla belirtir.</span><span class="sxs-lookup"><span data-stu-id="fc354-112">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="fc354-113">Kullanım [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) kaynak özelliklerini ve bunların türlerini bulmak için cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fc354-113">Use the [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="fc354-114">*yapılandırmaları* \[çıkışı\]</span><span class="sxs-lookup"><span data-stu-id="fc354-114">*configurations* \[out\]</span></span>  
<span data-ttu-id="fc354-115">Getirisi, katıştırılmış yapılandırmaları örneğini içerir.</span><span class="sxs-lookup"><span data-stu-id="fc354-115">On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="fc354-116">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="fc354-116">Return value</span></span>
------------

<span data-ttu-id="fc354-117">Başarı sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="fc354-117">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="fc354-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fc354-118">Remarks</span></span>

<span data-ttu-id="fc354-119">Bu statik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="fc354-119">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="fc354-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fc354-120">Requirements</span></span>
------------
><span data-ttu-id="fc354-121">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="fc354-121">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="fc354-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="fc354-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="fc354-123">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="fc354-123">See also</span></span>


[<span data-ttu-id="fc354-124">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="fc354-124">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



