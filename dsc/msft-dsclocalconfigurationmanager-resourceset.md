---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "MSFT_DSCLocalConfigurationManager sınıfının ResourceSet yöntemi"
ms.openlocfilehash: 3486ef559102929f8d05994a4bf6e45d49a0c140
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2018
---
# <a name="resourceset-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="bf44f-103">MSFT_DSCLocalConfigurationManager sınıfının ResourceSet yöntemi</span><span class="sxs-lookup"><span data-stu-id="bf44f-103">ResourceSet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="bf44f-104">Doğrudan çağıran **ayarlamak** DSC kaynağı yöntemi.</span><span class="sxs-lookup"><span data-stu-id="bf44f-104">Directly calls the **Set** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="bf44f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bf44f-105">Syntax</span></span>
------

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
);
```

<a name="parameters"></a><span data-ttu-id="bf44f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bf44f-106">Parameters</span></span>
----------

<span data-ttu-id="bf44f-107">*ResourceType* \[in\]</span><span class="sxs-lookup"><span data-stu-id="bf44f-107">*ResourceType* \[in\]</span></span>  
<span data-ttu-id="bf44f-108">Çağrılacak kaynağının adı.</span><span class="sxs-lookup"><span data-stu-id="bf44f-108">The name of the resource to call.</span></span>

<span data-ttu-id="bf44f-109">*ModuleName* \[in\]</span><span class="sxs-lookup"><span data-stu-id="bf44f-109">*ModuleName* \[in\]</span></span>  
<span data-ttu-id="bf44f-110">Aranacak kaynak içeren modülü adı.</span><span class="sxs-lookup"><span data-stu-id="bf44f-110">The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="bf44f-111">*resourceProperty* \[in\]</span><span class="sxs-lookup"><span data-stu-id="bf44f-111">*resourceProperty* \[in\]</span></span>  
<span data-ttu-id="bf44f-112">Kaynak özelliği adını ve değerini bir karma tablosunda anahtar ve değer sırasıyla belirtir.</span><span class="sxs-lookup"><span data-stu-id="bf44f-112">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="bf44f-113">Kullanım [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) kaynak özelliklerini ve bunların türlerini bulmak için cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bf44f-113">Use the [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="bf44f-114">*RebootRequired* \[çıkışı\]</span><span class="sxs-lookup"><span data-stu-id="bf44f-114">*RebootRequired* \[out\]</span></span>  
<span data-ttu-id="bf44f-115">Getirisi, bu özelliği ayarlamak **true** hedef düğümün yeniden başlatılması gerekiyorsa.</span><span class="sxs-lookup"><span data-stu-id="bf44f-115">On return, this property is set to **true** if the target node needs to be rebooted.</span></span>

## <a name="return-value"></a><span data-ttu-id="bf44f-116">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="bf44f-116">Return value</span></span>
------------

<span data-ttu-id="bf44f-117">Başarı sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="bf44f-117">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="bf44f-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bf44f-118">Remarks</span></span>

<span data-ttu-id="bf44f-119">Bu statik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="bf44f-119">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="bf44f-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bf44f-120">Requirements</span></span>
------------
><span data-ttu-id="bf44f-121">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="bf44f-121">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="bf44f-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="bf44f-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="bf44f-123">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="bf44f-123">See also</span></span>


[<span data-ttu-id="bf44f-124">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="bf44f-124">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

 

 



