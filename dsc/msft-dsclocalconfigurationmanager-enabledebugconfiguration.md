---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "MSFT_DSCLocalConfigurationManager sınıfının EnableDebugConfiguration yöntemi"
ms.openlocfilehash: 7220c972b3f43b4697cf71df54d2d43881938367
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="fc393-103">MSFT_DSCLocalConfigurationManager sınıfının EnableDebugConfiguration yöntemi</span><span class="sxs-lookup"><span data-stu-id="fc393-103">EnableDebugConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="fc393-104">DSC kaynak hata ayıklamasını etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="fc393-104">Enables DSC resource debugging.</span></span>

<a name="syntax"></a><span data-ttu-id="fc393-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fc393-105">Syntax</span></span>
------

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

<a name="parameters"></a><span data-ttu-id="fc393-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fc393-106">Parameters</span></span>
----------

<span data-ttu-id="fc393-107">*BreakAll* \[içinde\]</span><span class="sxs-lookup"><span data-stu-id="fc393-107">*BreakAll* \[in\]</span></span>  
<span data-ttu-id="fc393-108">Her kaynak komut satırında bir kesme noktası ayarlar.</span><span class="sxs-lookup"><span data-stu-id="fc393-108">Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="fc393-109">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="fc393-109">Return value</span></span>
------------

<span data-ttu-id="fc393-110">Başarı sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="fc393-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="fc393-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fc393-111">Remarks</span></span>

<span data-ttu-id="fc393-112">Bu statik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="fc393-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="fc393-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fc393-113">Requirements</span></span>
------------
><span data-ttu-id="fc393-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="fc393-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="fc393-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="fc393-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="fc393-116">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="fc393-116">See also</span></span>


[<span data-ttu-id="fc393-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="fc393-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
 

 



