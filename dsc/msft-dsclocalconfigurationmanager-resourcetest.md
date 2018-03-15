---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "MSFT_DSCLocalConfigurationManager sınıfının ResourceTest yöntemi"
ms.openlocfilehash: 799b1cd91dfacf25c0e5e734ca96d20a776103f0
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2018
---
# <a name="resourcetest-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="daf03-103">MSFT_DSCLocalConfigurationManager sınıfının ResourceTest yöntemi</span><span class="sxs-lookup"><span data-stu-id="daf03-103">ResourceTest method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="daf03-104">Doğrudan çağıran **Test** DSC kaynağı yöntemi.</span><span class="sxs-lookup"><span data-stu-id="daf03-104">Directly calls the **Test** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="daf03-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="daf03-105">Syntax</span></span>
------

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

<a name="parameters"></a><span data-ttu-id="daf03-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="daf03-106">Parameters</span></span>
----------

<span data-ttu-id="daf03-107">*ResourceType* \[in\]</span><span class="sxs-lookup"><span data-stu-id="daf03-107">*ResourceType* \[in\]</span></span>  
<span data-ttu-id="daf03-108">Çağrılacak kaynağının adı.</span><span class="sxs-lookup"><span data-stu-id="daf03-108">The name of the resource to call.</span></span>

<span data-ttu-id="daf03-109">*ModuleName* \[in\]</span><span class="sxs-lookup"><span data-stu-id="daf03-109">*ModuleName* \[in\]</span></span>  
<span data-ttu-id="daf03-110">Aranacak kaynak içeren modülü adı.</span><span class="sxs-lookup"><span data-stu-id="daf03-110">The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="daf03-111">*resourceProperty* \[in\]</span><span class="sxs-lookup"><span data-stu-id="daf03-111">*resourceProperty* \[in\]</span></span>  
<span data-ttu-id="daf03-112">Kaynak özelliği adını ve değerini bir karma tablosunda anahtar ve değer sırasıyla belirtir.</span><span class="sxs-lookup"><span data-stu-id="daf03-112">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="daf03-113">Kullanım [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) kaynak özelliklerini ve bunların türlerini bulmak için cmdlet.</span><span class="sxs-lookup"><span data-stu-id="daf03-113">Use the [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="daf03-114">*InDesiredState* \[çıkışı\]</span><span class="sxs-lookup"><span data-stu-id="daf03-114">*InDesiredState* \[out\]</span></span>  
<span data-ttu-id="daf03-115">Getirisi, bu özelliği ayarlamak **true** hedef düğüm istenen durumdaysa.</span><span class="sxs-lookup"><span data-stu-id="daf03-115">On return, this property is set to **true** if the target node is in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="daf03-116">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="daf03-116">Return value</span></span>
------------

<span data-ttu-id="daf03-117">Başarı sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="daf03-117">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="daf03-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="daf03-118">Remarks</span></span>

<span data-ttu-id="daf03-119">Bu statik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="daf03-119">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="daf03-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="daf03-120">Requirements</span></span>
------------
><span data-ttu-id="daf03-121">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="daf03-121">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="daf03-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="daf03-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="daf03-123">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="daf03-123">See also</span></span>


[<span data-ttu-id="daf03-124">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="daf03-124">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



