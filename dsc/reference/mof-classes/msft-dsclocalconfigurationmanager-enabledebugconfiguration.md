---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: EnableDebugConfiguration yöntemi
ms.openlocfilehash: f1290e4d898332361850ffc85aa0a8d79863c8f7
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727140"
---
# <a name="enabledebugconfiguration-method"></a><span data-ttu-id="2ba56-103">EnableDebugConfiguration yöntemi</span><span class="sxs-lookup"><span data-stu-id="2ba56-103">EnableDebugConfiguration method</span></span>

<span data-ttu-id="2ba56-104">DSC kaynak hata ayıklamasını etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="2ba56-104">Enables DSC resource debugging.</span></span>

## <a name="syntax"></a><span data-ttu-id="2ba56-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2ba56-105">Syntax</span></span>

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

## <a name="parameters"></a><span data-ttu-id="2ba56-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2ba56-106">Parameters</span></span>

<span data-ttu-id="2ba56-107">*BreakAll* \[içinde\] kaynak betiği her satırında bir kesme noktası ayarlar.</span><span class="sxs-lookup"><span data-stu-id="2ba56-107">*BreakAll* \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="2ba56-108">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="2ba56-108">Return value</span></span>

<span data-ttu-id="2ba56-109">Başarılıysa sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="2ba56-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="2ba56-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2ba56-110">Remarks</span></span>

<span data-ttu-id="2ba56-111">Statik bir yöntem budur.</span><span class="sxs-lookup"><span data-stu-id="2ba56-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="2ba56-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2ba56-112">Requirements</span></span>

<span data-ttu-id="2ba56-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="2ba56-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="2ba56-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="2ba56-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="2ba56-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2ba56-115">See also</span></span>

[<span data-ttu-id="2ba56-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="2ba56-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
