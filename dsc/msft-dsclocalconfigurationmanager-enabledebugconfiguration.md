---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "MSFT_DSCLocalConfigurationManager sınıfının EnableDebugConfiguration yöntemi"
ms.openlocfilehash: fa34a583af7c3fd46d99307d582973410e4c0e31
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="76528-103">MSFT_DSCLocalConfigurationManager sınıfının EnableDebugConfiguration yöntemi</span><span class="sxs-lookup"><span data-stu-id="76528-103">EnableDebugConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="76528-104">DSC kaynak hata ayıklamasını etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="76528-104">Enables DSC resource debugging.</span></span>

<a name="syntax"></a><span data-ttu-id="76528-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="76528-105">Syntax</span></span>
------

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

<a name="parameters"></a><span data-ttu-id="76528-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="76528-106">Parameters</span></span>
----------

<span data-ttu-id="76528-107">*BreakAll* \[içinde\]</span><span class="sxs-lookup"><span data-stu-id="76528-107">*BreakAll* \[in\]</span></span>  
<span data-ttu-id="76528-108">Her kaynak komut satırında bir kesme noktası ayarlar.</span><span class="sxs-lookup"><span data-stu-id="76528-108">Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="76528-109">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="76528-109">Return value</span></span>
------------

<span data-ttu-id="76528-110">Başarı sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="76528-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="76528-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="76528-111">Remarks</span></span>

<span data-ttu-id="76528-112">Bu statik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="76528-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="76528-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="76528-113">Requirements</span></span>
------------
><span data-ttu-id="76528-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="76528-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="76528-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="76528-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="76528-116">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="76528-116">See also</span></span>


[<span data-ttu-id="76528-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="76528-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
 

 



