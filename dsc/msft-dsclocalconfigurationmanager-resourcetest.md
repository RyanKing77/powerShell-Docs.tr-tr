---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: MSFT_DSCLocalConfigurationManager sınıfının ResourceTest yöntemi
ms.openlocfilehash: 714bbb286ebbe4ed0f1faa15e03ac4b51a3ee87f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
---
# <a name="resourcetest-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="bb682-103">MSFT_DSCLocalConfigurationManager sınıfının ResourceTest yöntemi</span><span class="sxs-lookup"><span data-stu-id="bb682-103">ResourceTest method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="bb682-104">Doğrudan çağıran **Test** DSC kaynağı yöntemi.</span><span class="sxs-lookup"><span data-stu-id="bb682-104">Directly calls the **Test** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="bb682-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bb682-105">Syntax</span></span>
------

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

<a name="parameters"></a><span data-ttu-id="bb682-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bb682-106">Parameters</span></span>
----------

<span data-ttu-id="bb682-107">*ResourceType* \[içinde\] çağırmak için kaynağın adı.</span><span class="sxs-lookup"><span data-stu-id="bb682-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="bb682-108">*ModuleName* \[içinde\] çağırmak için kaynak içeren modülü adı.</span><span class="sxs-lookup"><span data-stu-id="bb682-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="bb682-109">*resourceProperty* \[içinde\] kaynak özellik adını ve değerini bir karma tablosunda anahtar ve değer sırasıyla belirtir.</span><span class="sxs-lookup"><span data-stu-id="bb682-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="bb682-110">Kullanım [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) kaynak özelliklerini ve bunların türlerini bulmak için cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bb682-110">Use the [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="bb682-111">*InDesiredState* \[çıkışı\] getirisi, bu özelliği ayarlamak **true** hedef düğüm istenen durumdaysa.</span><span class="sxs-lookup"><span data-stu-id="bb682-111">*InDesiredState* \[out\] On return, this property is set to **true** if the target node is in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="bb682-112">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="bb682-112">Return value</span></span>
------------

<span data-ttu-id="bb682-113">Başarı sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="bb682-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="bb682-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bb682-114">Remarks</span></span>

<span data-ttu-id="bb682-115">Bu statik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="bb682-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="bb682-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bb682-116">Requirements</span></span>
------------
><span data-ttu-id="bb682-117">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="bb682-117">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="bb682-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="bb682-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="bb682-119">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="bb682-119">See also</span></span>


[<span data-ttu-id="bb682-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="bb682-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)