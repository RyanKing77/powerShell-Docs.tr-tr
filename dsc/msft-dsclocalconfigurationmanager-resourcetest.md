---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, yapılandırma, Kur
title: MSFT_DSCLocalConfigurationManager sınıfının ResourceTest yöntemi
ms.openlocfilehash: f03a034329a9cde5cd44dbaf42ba1789c2b8f4f9
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="resourcetest-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="e2099-103">MSFT_DSCLocalConfigurationManager sınıfının ResourceTest yöntemi</span><span class="sxs-lookup"><span data-stu-id="e2099-103">ResourceTest method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="e2099-104">Doğrudan çağıran **Test** DSC kaynağı yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e2099-104">Directly calls the **Test** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="e2099-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e2099-105">Syntax</span></span>
------

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

<a name="parameters"></a><span data-ttu-id="e2099-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e2099-106">Parameters</span></span>
----------

<span data-ttu-id="e2099-107">*ResourceType* \[içinde\] çağırmak için kaynağın adı.</span><span class="sxs-lookup"><span data-stu-id="e2099-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="e2099-108">*ModuleName* \[içinde\] çağırmak için kaynak içeren modülü adı.</span><span class="sxs-lookup"><span data-stu-id="e2099-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="e2099-109">*resourceProperty* \[içinde\] kaynak özellik adını ve değerini bir karma tablosunda anahtar ve değer sırasıyla belirtir.</span><span class="sxs-lookup"><span data-stu-id="e2099-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="e2099-110">Kullanım [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) kaynak özelliklerini ve bunların türlerini bulmak için cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e2099-110">Use the [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="e2099-111">*InDesiredState* \[çıkışı\] getirisi, bu özelliği ayarlamak **true** hedef düğüm istenen durumdaysa.</span><span class="sxs-lookup"><span data-stu-id="e2099-111">*InDesiredState* \[out\] On return, this property is set to **true** if the target node is in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="e2099-112">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="e2099-112">Return value</span></span>
------------

<span data-ttu-id="e2099-113">Başarı sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="e2099-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="e2099-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e2099-114">Remarks</span></span>

<span data-ttu-id="e2099-115">Bu statik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="e2099-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e2099-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e2099-116">Requirements</span></span>
------------
><span data-ttu-id="e2099-117">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="e2099-117">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="e2099-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="e2099-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="e2099-119">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="e2099-119">See also</span></span>


[<span data-ttu-id="e2099-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="e2099-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)