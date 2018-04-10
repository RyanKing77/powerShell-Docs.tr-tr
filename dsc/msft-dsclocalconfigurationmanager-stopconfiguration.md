---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, yapılandırma, Kur
title: MSFT_DSCLocalConfigurationManager sınıfının StopConfiguration yöntemi
ms.openlocfilehash: dadb6912af2e4450381958ed465799056da49946
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="72497-103">MSFT_DSCLocalConfigurationManager sınıfının StopConfiguration yöntemi</span><span class="sxs-lookup"><span data-stu-id="72497-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="72497-104">Devam ediyor yapılandırma değişikliği durdurur.</span><span class="sxs-lookup"><span data-stu-id="72497-104">Stops the configuration change that is in progress.</span></span>

<a name="syntax"></a><span data-ttu-id="72497-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="72497-105">Syntax</span></span>
------

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="72497-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="72497-106">Parameters</span></span>
----------

<span data-ttu-id="72497-107">*zorla* \[içinde\] **true** durdurmak için yapılandırmayı zorla uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="72497-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="72497-108">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="72497-108">Return value</span></span>
------------

<span data-ttu-id="72497-109">Başarı sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="72497-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="72497-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="72497-110">Remarks</span></span>

<span data-ttu-id="72497-111">Bu statik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="72497-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="72497-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="72497-112">Requirements</span></span>
------------
><span data-ttu-id="72497-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="72497-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="72497-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="72497-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="72497-115">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="72497-115">See also</span></span>


[<span data-ttu-id="72497-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="72497-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)