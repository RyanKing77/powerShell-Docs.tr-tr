---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, yapılandırma, Kur
title: MSFT_DSCLocalConfigurationManager sınıfının RemoveConfiguration yöntemi
ms.openlocfilehash: e0ae8a50212b70841d210d7b2d666a2855218d1a
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="193a8-103">MSFT_DSCLocalConfigurationManager sınıfının RemoveConfiguration yöntemi</span><span class="sxs-lookup"><span data-stu-id="193a8-103">RemoveConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="193a8-104">Yapılandırma dosyalarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="193a8-104">Removes the configuration files.</span></span>

<a name="syntax"></a><span data-ttu-id="193a8-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="193a8-105">Syntax</span></span>
------

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

<a name="parameters"></a><span data-ttu-id="193a8-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="193a8-106">Parameters</span></span>
----------

<span data-ttu-id="193a8-107">*Aşama* \[içinde\] kaldırmak için hangi yapılandırma belgesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="193a8-107">*Stage* \[in\] Specifies which configuration document to remove.</span></span> <span data-ttu-id="193a8-108">Aşağıdaki değerler geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="193a8-108">The following values are valid:</span></span>

|<span data-ttu-id="193a8-109">Değer</span><span class="sxs-lookup"><span data-stu-id="193a8-109">Value</span></span> |<span data-ttu-id="193a8-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="193a8-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="193a8-111">**1**</span><span class="sxs-lookup"><span data-stu-id="193a8-111">**1**</span></span> | <span data-ttu-id="193a8-112">**Geçerli** yapılandırma belgesi (current.mof).</span><span class="sxs-lookup"><span data-stu-id="193a8-112">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="193a8-113">**2**</span><span class="sxs-lookup"><span data-stu-id="193a8-113">**2**</span></span> | <span data-ttu-id="193a8-114">**Bekleyen** yapılandırma belgesi (pending.mof).</span><span class="sxs-lookup"><span data-stu-id="193a8-114">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="193a8-115">**4**</span><span class="sxs-lookup"><span data-stu-id="193a8-115">**4**</span></span> | <span data-ttu-id="193a8-116">**Önceki** yapılandırma belgesi (previous.mof).</span><span class="sxs-lookup"><span data-stu-id="193a8-116">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="193a8-117">*Zorla* \[içinde\] **true** yapılandırma kaldırılmasını zorla için.</span><span class="sxs-lookup"><span data-stu-id="193a8-117">*Force* \[in\] **true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="193a8-118">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="193a8-118">Return value</span></span>
------------

<span data-ttu-id="193a8-119">Başarı sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="193a8-119">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="193a8-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="193a8-120">Remarks</span></span>

<span data-ttu-id="193a8-121">Bu statik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="193a8-121">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="193a8-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="193a8-122">Requirements</span></span>
------------
><span data-ttu-id="193a8-123">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="193a8-123">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="193a8-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="193a8-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="193a8-125">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="193a8-125">See also</span></span>


[<span data-ttu-id="193a8-126">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="193a8-126">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)