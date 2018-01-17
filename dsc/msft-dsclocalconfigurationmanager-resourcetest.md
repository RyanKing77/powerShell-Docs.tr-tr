---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "MSFT_DSCLocalConfigurationManager sınıfının ResourceTest yöntemi"
ms.openlocfilehash: 3c88f74c5f623502e8cbe0d7aa7390fca75569a9
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="resourcetest-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="573cd-103">MSFT_DSCLocalConfigurationManager sınıfının ResourceTest yöntemi</span><span class="sxs-lookup"><span data-stu-id="573cd-103">ResourceTest method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="573cd-104">Doğrudan çağıran **Test** DSC kaynağı yöntemi.</span><span class="sxs-lookup"><span data-stu-id="573cd-104">Directly calls the **Test** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="573cd-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="573cd-105">Syntax</span></span>
------

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

<a name="parameters"></a><span data-ttu-id="573cd-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="573cd-106">Parameters</span></span>
----------

<span data-ttu-id="573cd-107">*ResourceType* \[in\]</span><span class="sxs-lookup"><span data-stu-id="573cd-107">*ResourceType* \[in\]</span></span>  
<span data-ttu-id="573cd-108">Çağrılacak kaynağının adı.</span><span class="sxs-lookup"><span data-stu-id="573cd-108">The name of the resource to call.</span></span>

<span data-ttu-id="573cd-109">*ModuleName* \[in\]</span><span class="sxs-lookup"><span data-stu-id="573cd-109">*ModuleName* \[in\]</span></span>  
<span data-ttu-id="573cd-110">Aranacak kaynak içeren modülü adı.</span><span class="sxs-lookup"><span data-stu-id="573cd-110">The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="573cd-111">*resourceProperty* \[in\]</span><span class="sxs-lookup"><span data-stu-id="573cd-111">*resourceProperty* \[in\]</span></span>  
<span data-ttu-id="573cd-112">Kaynak özelliği adını ve değerini bir karma tablosunda anahtar ve değer sırasıyla belirtir.</span><span class="sxs-lookup"><span data-stu-id="573cd-112">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="573cd-113">Kullanım [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) kaynak özelliklerini ve bunların türlerini bulmak için cmdlet.</span><span class="sxs-lookup"><span data-stu-id="573cd-113">Use the [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="573cd-114">*InDesiredState* \[çıkışı\]</span><span class="sxs-lookup"><span data-stu-id="573cd-114">*InDesiredState* \[out\]</span></span>  
<span data-ttu-id="573cd-115">Getirisi, bu özelliği ayarlamak **true** hedef düğüm istenen durumdaysa.</span><span class="sxs-lookup"><span data-stu-id="573cd-115">On return, this property is set to **true** if the target node is in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="573cd-116">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="573cd-116">Return value</span></span>
------------

<span data-ttu-id="573cd-117">Başarı sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="573cd-117">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="573cd-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="573cd-118">Remarks</span></span>

<span data-ttu-id="573cd-119">Bu statik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="573cd-119">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="573cd-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="573cd-120">Requirements</span></span>
------------
><span data-ttu-id="573cd-121">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="573cd-121">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="573cd-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="573cd-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="573cd-123">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="573cd-123">See also</span></span>


[<span data-ttu-id="573cd-124">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="573cd-124">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



