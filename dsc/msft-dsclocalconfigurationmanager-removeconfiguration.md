---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "MSFT_DSCLocalConfigurationManager sınıfının RemoveConfiguration yöntemi"
ms.openlocfilehash: fed45836293adedbce18f01cfe53cdfa1a474975
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="67924-103">MSFT_DSCLocalConfigurationManager sınıfının RemoveConfiguration yöntemi</span><span class="sxs-lookup"><span data-stu-id="67924-103">RemoveConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="67924-104">Yapılandırma dosyalarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="67924-104">Removes the configuration files.</span></span>

<a name="syntax"></a><span data-ttu-id="67924-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="67924-105">Syntax</span></span>
------

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

<a name="parameters"></a><span data-ttu-id="67924-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="67924-106">Parameters</span></span>
----------

<span data-ttu-id="67924-107">*Aşama* \[içinde\]</span><span class="sxs-lookup"><span data-stu-id="67924-107">*Stage* \[in\]</span></span>  
<span data-ttu-id="67924-108">Kaldırmak için hangi yapılandırma belgesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="67924-108">Specifies which configuration document to remove.</span></span> <span data-ttu-id="67924-109">Aşağıdaki değerler geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="67924-109">The following values are valid:</span></span>

|<span data-ttu-id="67924-110">Değer</span><span class="sxs-lookup"><span data-stu-id="67924-110">Value</span></span> |<span data-ttu-id="67924-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="67924-111">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="67924-112">**1**</span><span class="sxs-lookup"><span data-stu-id="67924-112">**1**</span></span> | <span data-ttu-id="67924-113">**Geçerli** yapılandırma belgesi (current.mof).</span><span class="sxs-lookup"><span data-stu-id="67924-113">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="67924-114">**2**</span><span class="sxs-lookup"><span data-stu-id="67924-114">**2**</span></span> | <span data-ttu-id="67924-115">**Bekleyen** yapılandırma belgesi (pending.mof).</span><span class="sxs-lookup"><span data-stu-id="67924-115">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="67924-116">**4**</span><span class="sxs-lookup"><span data-stu-id="67924-116">**4**</span></span> | <span data-ttu-id="67924-117">**Önceki** yapılandırma belgesi (previous.mof).</span><span class="sxs-lookup"><span data-stu-id="67924-117">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="67924-118">*Zorla* \[içinde\]</span><span class="sxs-lookup"><span data-stu-id="67924-118">*Force* \[in\]</span></span>  
<span data-ttu-id="67924-119">**doğru** yapılandırma kaldırılmasını zorla için.</span><span class="sxs-lookup"><span data-stu-id="67924-119">**true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="67924-120">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="67924-120">Return value</span></span>
------------

<span data-ttu-id="67924-121">Başarı sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="67924-121">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="67924-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="67924-122">Remarks</span></span>

<span data-ttu-id="67924-123">Bu statik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="67924-123">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="67924-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="67924-124">Requirements</span></span>
------------
><span data-ttu-id="67924-125">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="67924-125">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="67924-126">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="67924-126">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="67924-127">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="67924-127">See also</span></span>


[<span data-ttu-id="67924-128">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="67924-128">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



