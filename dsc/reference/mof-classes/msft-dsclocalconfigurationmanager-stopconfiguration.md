---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: MSFT_DSCLocalConfigurationManager sınıfının StopConfiguration yöntemi
ms.openlocfilehash: 1cd887d205967c3d282143df4e6199027639230e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078258"
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="4ba49-103">MSFT_DSCLocalConfigurationManager sınıfının StopConfiguration yöntemi</span><span class="sxs-lookup"><span data-stu-id="4ba49-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="4ba49-104">Devam eden yapılandırma değişikliğini durdurur.</span><span class="sxs-lookup"><span data-stu-id="4ba49-104">Stops the configuration change that is in progress.</span></span>

## <a name="syntax"></a><span data-ttu-id="4ba49-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4ba49-105">Syntax</span></span>

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="4ba49-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4ba49-106">Parameters</span></span>

<span data-ttu-id="4ba49-107">*zorla* \[içinde\] **true** durdurmak için yapılandırmayı zorla uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="4ba49-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="4ba49-108">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="4ba49-108">Return value</span></span>

<span data-ttu-id="4ba49-109">Başarılıysa sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="4ba49-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="4ba49-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4ba49-110">Remarks</span></span>

<span data-ttu-id="4ba49-111">Statik bir yöntem budur.</span><span class="sxs-lookup"><span data-stu-id="4ba49-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="4ba49-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4ba49-112">Requirements</span></span>

<span data-ttu-id="4ba49-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="4ba49-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="4ba49-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="4ba49-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="4ba49-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4ba49-115">See also</span></span>

[<span data-ttu-id="4ba49-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="4ba49-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)