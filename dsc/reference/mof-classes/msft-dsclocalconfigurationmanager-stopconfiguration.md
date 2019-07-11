---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: StopConfiguration yöntemi
ms.openlocfilehash: e1de175032a3bddf11af218bc4a15bdbe554a9d5
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726993"
---
# <a name="stopconfiguration-method"></a><span data-ttu-id="449eb-103">StopConfiguration yöntemi</span><span class="sxs-lookup"><span data-stu-id="449eb-103">StopConfiguration method</span></span>

<span data-ttu-id="449eb-104">Devam eden yapılandırma değişikliğini durdurur.</span><span class="sxs-lookup"><span data-stu-id="449eb-104">Stops the configuration change that is in progress.</span></span>

## <a name="syntax"></a><span data-ttu-id="449eb-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="449eb-105">Syntax</span></span>

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="449eb-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="449eb-106">Parameters</span></span>

<span data-ttu-id="449eb-107">*zorla* \[içinde\] **true** durdurmak için yapılandırmayı zorla uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="449eb-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="449eb-108">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="449eb-108">Return value</span></span>

<span data-ttu-id="449eb-109">Başarılıysa sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="449eb-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="449eb-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="449eb-110">Remarks</span></span>

<span data-ttu-id="449eb-111">Statik bir yöntem budur.</span><span class="sxs-lookup"><span data-stu-id="449eb-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="449eb-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="449eb-112">Requirements</span></span>

<span data-ttu-id="449eb-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="449eb-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="449eb-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="449eb-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="449eb-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="449eb-115">See also</span></span>

[<span data-ttu-id="449eb-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="449eb-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
