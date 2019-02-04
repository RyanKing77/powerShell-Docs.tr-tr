---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: MSFT_DSCLocalConfigurationManager sınıfının StopConfiguration yöntemi
ms.openlocfilehash: 1cd887d205967c3d282143df4e6199027639230e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687758"
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="5c849-103">MSFT_DSCLocalConfigurationManager sınıfının StopConfiguration yöntemi</span><span class="sxs-lookup"><span data-stu-id="5c849-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="5c849-104">Devam eden yapılandırma değişikliğini durdurur.</span><span class="sxs-lookup"><span data-stu-id="5c849-104">Stops the configuration change that is in progress.</span></span>

## <a name="syntax"></a><span data-ttu-id="5c849-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5c849-105">Syntax</span></span>

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="5c849-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5c849-106">Parameters</span></span>

<span data-ttu-id="5c849-107">*zorla* \[içinde\] **true** durdurmak için yapılandırmayı zorla uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="5c849-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="5c849-108">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="5c849-108">Return value</span></span>

<span data-ttu-id="5c849-109">Başarılıysa sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="5c849-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="5c849-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5c849-110">Remarks</span></span>

<span data-ttu-id="5c849-111">Statik bir yöntem budur.</span><span class="sxs-lookup"><span data-stu-id="5c849-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="5c849-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5c849-112">Requirements</span></span>

<span data-ttu-id="5c849-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="5c849-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="5c849-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="5c849-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="5c849-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5c849-115">See also</span></span>

[<span data-ttu-id="5c849-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="5c849-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)