---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: MSFT_DSCLocalConfigurationManager sınıfının RollBack yöntemi
ms.openlocfilehash: d2f9b7025d611912e119800408e25fcb66bc0228
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219887"
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="41484-103">MSFT_DSCLocalConfigurationManager sınıfının RollBack yöntemi</span><span class="sxs-lookup"><span data-stu-id="41484-103">RollBack method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="41484-104">Geri önceki bir sürüm olarak yapılandırma yapar.</span><span class="sxs-lookup"><span data-stu-id="41484-104">Rolls back the configuration to a previous version.</span></span>

<a name="syntax"></a><span data-ttu-id="41484-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="41484-105">Syntax</span></span>
------

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

<a name="parameters"></a><span data-ttu-id="41484-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="41484-106">Parameters</span></span>
----------

<span data-ttu-id="41484-107">*configurationNumber* \[içinde\] istenen yapılandırma belirtir.</span><span class="sxs-lookup"><span data-stu-id="41484-107">*configurationNumber* \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="41484-108">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="41484-108">Return value</span></span>
------------

<span data-ttu-id="41484-109">Başarı sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="41484-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="41484-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="41484-110">Remarks</span></span>

<span data-ttu-id="41484-111">Bu statik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="41484-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="41484-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="41484-112">Requirements</span></span>
------------
><span data-ttu-id="41484-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="41484-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="41484-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="41484-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="41484-115">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="41484-115">See also</span></span>


[<span data-ttu-id="41484-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="41484-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)