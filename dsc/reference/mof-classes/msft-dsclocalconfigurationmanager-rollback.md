---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: MSFT_DSCLocalConfigurationManager sınıfının RollBack yöntemi
ms.openlocfilehash: 4956900ecd2c9cb7f2e2b5bcab94616f9f5d5565
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688584"
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="74575-103">MSFT_DSCLocalConfigurationManager sınıfının RollBack yöntemi</span><span class="sxs-lookup"><span data-stu-id="74575-103">RollBack method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="74575-104">Yeniden yapılandırma, önceki bir sürüme yapar.</span><span class="sxs-lookup"><span data-stu-id="74575-104">Rolls back the configuration to a previous version.</span></span>

## <a name="syntax"></a><span data-ttu-id="74575-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="74575-105">Syntax</span></span>

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

## <a name="parameters"></a><span data-ttu-id="74575-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="74575-106">Parameters</span></span>

<span data-ttu-id="74575-107">*configurationNumber* \[içinde\] istenen yapılandırmanın belirtir.</span><span class="sxs-lookup"><span data-stu-id="74575-107">*configurationNumber* \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="74575-108">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="74575-108">Return value</span></span>

<span data-ttu-id="74575-109">Başarılıysa sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="74575-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="74575-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="74575-110">Remarks</span></span>

<span data-ttu-id="74575-111">Statik bir yöntem budur.</span><span class="sxs-lookup"><span data-stu-id="74575-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="74575-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="74575-112">Requirements</span></span>

<span data-ttu-id="74575-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="74575-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="74575-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="74575-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="74575-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="74575-115">See also</span></span>

[<span data-ttu-id="74575-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="74575-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)