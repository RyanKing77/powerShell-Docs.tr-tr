---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: Geri alma yöntemi
ms.openlocfilehash: 6452bdffd5160d9956576fb59c98e2f9ff7ddbbb
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727030"
---
# <a name="rollback-method"></a><span data-ttu-id="d0fd6-103">Geri alma yöntemi</span><span class="sxs-lookup"><span data-stu-id="d0fd6-103">RollBack method</span></span>

<span data-ttu-id="d0fd6-104">Yeniden yapılandırma, önceki bir sürüme yapar.</span><span class="sxs-lookup"><span data-stu-id="d0fd6-104">Rolls back the configuration to a previous version.</span></span>

## <a name="syntax"></a><span data-ttu-id="d0fd6-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d0fd6-105">Syntax</span></span>

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

## <a name="parameters"></a><span data-ttu-id="d0fd6-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d0fd6-106">Parameters</span></span>

<span data-ttu-id="d0fd6-107">*configurationNumber* \[içinde\] istenen yapılandırmanın belirtir.</span><span class="sxs-lookup"><span data-stu-id="d0fd6-107">*configurationNumber* \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="d0fd6-108">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="d0fd6-108">Return value</span></span>

<span data-ttu-id="d0fd6-109">Başarılıysa sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="d0fd6-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="d0fd6-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d0fd6-110">Remarks</span></span>

<span data-ttu-id="d0fd6-111">Statik bir yöntem budur.</span><span class="sxs-lookup"><span data-stu-id="d0fd6-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d0fd6-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d0fd6-112">Requirements</span></span>

<span data-ttu-id="d0fd6-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="d0fd6-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="d0fd6-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="d0fd6-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="d0fd6-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0fd6-115">See also</span></span>

[<span data-ttu-id="d0fd6-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="d0fd6-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
