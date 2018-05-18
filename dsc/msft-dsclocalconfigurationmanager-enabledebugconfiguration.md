---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: MSFT_DSCLocalConfigurationManager sınıfının EnableDebugConfiguration yöntemi
ms.openlocfilehash: 9e2a978f9d16abaed959be022229db4da5fd65bd
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="9ebc3-103">MSFT_DSCLocalConfigurationManager sınıfının EnableDebugConfiguration yöntemi</span><span class="sxs-lookup"><span data-stu-id="9ebc3-103">EnableDebugConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="9ebc3-104">DSC kaynak hata ayıklamasını etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="9ebc3-104">Enables DSC resource debugging.</span></span>

<a name="syntax"></a><span data-ttu-id="9ebc3-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9ebc3-105">Syntax</span></span>
------

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

<a name="parameters"></a><span data-ttu-id="9ebc3-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9ebc3-106">Parameters</span></span>
----------

<span data-ttu-id="9ebc3-107">*BreakAll* \[içinde\] her kaynak komut satırında bir kesme noktası ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9ebc3-107">*BreakAll* \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="9ebc3-108">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="9ebc3-108">Return value</span></span>
------------

<span data-ttu-id="9ebc3-109">Başarı sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="9ebc3-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="9ebc3-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9ebc3-110">Remarks</span></span>

<span data-ttu-id="9ebc3-111">Bu statik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="9ebc3-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="9ebc3-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9ebc3-112">Requirements</span></span>
------------
><span data-ttu-id="9ebc3-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="9ebc3-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="9ebc3-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="9ebc3-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="9ebc3-115">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="9ebc3-115">See also</span></span>


[<span data-ttu-id="9ebc3-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="9ebc3-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)