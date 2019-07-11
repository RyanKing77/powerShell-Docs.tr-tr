---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: ApplyConfiguration yöntemi
ms.openlocfilehash: 0425b9a7db37e421830ba37da8f5c0a4877a1b72
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727186"
---
# <a name="applyconfiguration-method"></a><span data-ttu-id="9540a-103">ApplyConfiguration yöntemi</span><span class="sxs-lookup"><span data-stu-id="9540a-103">ApplyConfiguration method</span></span>

<span data-ttu-id="9540a-104">Yapılandırma Aracı, bekleyen yapılandırmayı uygulamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="9540a-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span>

<span data-ttu-id="9540a-105">Bekleyen herhangi bir yapılandırma varsa, bu yöntem geçerli yapılandırmasını yeniden uygular.</span><span class="sxs-lookup"><span data-stu-id="9540a-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="9540a-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9540a-106">Syntax</span></span>

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="9540a-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9540a-107">Parameters</span></span>

<span data-ttu-id="9540a-108">*zorla* \[içinde\] buysa **true**, bekleyen bir yapılandırma olsa bile geçerli yapılandırmasını yeniden uygulanır.</span><span class="sxs-lookup"><span data-stu-id="9540a-108">*force* \[in\] If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="9540a-109">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="9540a-109">Return value</span></span>

<span data-ttu-id="9540a-110">Başarılıysa sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="9540a-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="9540a-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9540a-111">Remarks</span></span>

<span data-ttu-id="9540a-112">Statik bir yöntem budur.</span><span class="sxs-lookup"><span data-stu-id="9540a-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="9540a-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9540a-113">Requirements</span></span>

<span data-ttu-id="9540a-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="9540a-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="9540a-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="9540a-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="9540a-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9540a-116">See also</span></span>

[<span data-ttu-id="9540a-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="9540a-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
