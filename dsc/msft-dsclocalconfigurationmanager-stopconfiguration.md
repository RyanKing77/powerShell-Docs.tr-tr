---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: MSFT_DSCLocalConfigurationManager sınıfının StopConfiguration yöntemi
ms.openlocfilehash: 1cd887d205967c3d282143df4e6199027639230e
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893884"
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="f19fd-103">MSFT_DSCLocalConfigurationManager sınıfının StopConfiguration yöntemi</span><span class="sxs-lookup"><span data-stu-id="f19fd-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="f19fd-104">Devam eden yapılandırma değişikliğini durdurur.</span><span class="sxs-lookup"><span data-stu-id="f19fd-104">Stops the configuration change that is in progress.</span></span>

## <a name="syntax"></a><span data-ttu-id="f19fd-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f19fd-105">Syntax</span></span>

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="f19fd-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f19fd-106">Parameters</span></span>

<span data-ttu-id="f19fd-107">*zorla* \[içinde\] **true** durdurmak için yapılandırmayı zorla uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="f19fd-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="f19fd-108">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="f19fd-108">Return value</span></span>

<span data-ttu-id="f19fd-109">Başarılıysa sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="f19fd-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="f19fd-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f19fd-110">Remarks</span></span>

<span data-ttu-id="f19fd-111">Statik bir yöntem budur.</span><span class="sxs-lookup"><span data-stu-id="f19fd-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="f19fd-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f19fd-112">Requirements</span></span>

<span data-ttu-id="f19fd-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="f19fd-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="f19fd-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="f19fd-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="f19fd-115">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="f19fd-115">See also</span></span>

[<span data-ttu-id="f19fd-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="f19fd-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)