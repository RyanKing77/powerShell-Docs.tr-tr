---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "MSFT_DSCLocalConfigurationManager sınıfının ResourceSet yöntemi"
ms.openlocfilehash: 7291641098578226449f8cbd360da0a3f9842598
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="resourceset-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="954a4-103">MSFT_DSCLocalConfigurationManager sınıfının ResourceSet yöntemi</span><span class="sxs-lookup"><span data-stu-id="954a4-103">ResourceSet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="954a4-104">Doğrudan çağıran **ayarlamak** DSC kaynağı yöntemi.</span><span class="sxs-lookup"><span data-stu-id="954a4-104">Directly calls the **Set** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="954a4-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="954a4-105">Syntax</span></span>
------

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
);
```

<a name="parameters"></a><span data-ttu-id="954a4-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="954a4-106">Parameters</span></span>
----------

<span data-ttu-id="954a4-107">*ResourceType* \[in\]</span><span class="sxs-lookup"><span data-stu-id="954a4-107">*ResourceType* \[in\]</span></span>  
<span data-ttu-id="954a4-108">Çağrılacak kaynağının adı.</span><span class="sxs-lookup"><span data-stu-id="954a4-108">The name of the resource to call.</span></span>

<span data-ttu-id="954a4-109">*ModuleName* \[in\]</span><span class="sxs-lookup"><span data-stu-id="954a4-109">*ModuleName* \[in\]</span></span>  
<span data-ttu-id="954a4-110">Aranacak kaynak içeren modülü adı.</span><span class="sxs-lookup"><span data-stu-id="954a4-110">The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="954a4-111">*resourceProperty* \[in\]</span><span class="sxs-lookup"><span data-stu-id="954a4-111">*resourceProperty* \[in\]</span></span>  
<span data-ttu-id="954a4-112">Kaynak özelliği adını ve değerini bir karma tablosunda anahtar ve değer sırasıyla belirtir.</span><span class="sxs-lookup"><span data-stu-id="954a4-112">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="954a4-113">Kullanım [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) kaynak özelliklerini ve bunların türlerini bulmak için cmdlet.</span><span class="sxs-lookup"><span data-stu-id="954a4-113">Use the [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="954a4-114">*RebootRequired* \[çıkışı\]</span><span class="sxs-lookup"><span data-stu-id="954a4-114">*RebootRequired* \[out\]</span></span>  
<span data-ttu-id="954a4-115">Getirisi, bu özelliği ayarlamak **true** hedef düğümün yeniden başlatılması gerekiyorsa.</span><span class="sxs-lookup"><span data-stu-id="954a4-115">On return, this property is set to **true** if the target node needs to be rebooted.</span></span>

## <a name="return-value"></a><span data-ttu-id="954a4-116">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="954a4-116">Return value</span></span>
------------

<span data-ttu-id="954a4-117">Başarı sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="954a4-117">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="954a4-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="954a4-118">Remarks</span></span>

<span data-ttu-id="954a4-119">Bu statik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="954a4-119">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="954a4-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="954a4-120">Requirements</span></span>
------------
><span data-ttu-id="954a4-121">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="954a4-121">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="954a4-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="954a4-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="954a4-123">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="954a4-123">See also</span></span>


[<span data-ttu-id="954a4-124">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="954a4-124">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

 

 



