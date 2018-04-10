---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, yapılandırma, Kur
title: MSFT_DSCLocalConfigurationManager sınıfının ApplyConfiguration yöntemi
ms.openlocfilehash: 2844e354e0d054b13b92267ce314536d88a1c33e
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="4ef57-103">MSFT_DSCLocalConfigurationManager sınıfının ApplyConfiguration yöntemi</span><span class="sxs-lookup"><span data-stu-id="4ef57-103">ApplyConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="4ef57-104">Bekleyen yapılandırmayı uygulamak için yapılandırma Aracısı'nı kullanır.</span><span class="sxs-lookup"><span data-stu-id="4ef57-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span>

<span data-ttu-id="4ef57-105">Bekleyen yapılandırma yoksa, bu yöntem geçerli yapılandırmasını yeniden uygular.</span><span class="sxs-lookup"><span data-stu-id="4ef57-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>


## <a name="syntax"></a><span data-ttu-id="4ef57-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4ef57-106">Syntax</span></span>
------

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="4ef57-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4ef57-107">Parameters</span></span>
----------

<span data-ttu-id="4ef57-108">*zorla* \[içinde\] bu ise **doğru**, bekleyen bir yapılandırma olsa bile geçerli yapılandırmasını yeniden.</span><span class="sxs-lookup"><span data-stu-id="4ef57-108">*force* \[in\] If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="4ef57-109">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="4ef57-109">Return value</span></span>
------------

<span data-ttu-id="4ef57-110">Başarı sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="4ef57-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="4ef57-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4ef57-111">Remarks</span></span>

<span data-ttu-id="4ef57-112">Bu statik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="4ef57-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="4ef57-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4ef57-113">Requirements</span></span>
------------
><span data-ttu-id="4ef57-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="4ef57-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="4ef57-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="4ef57-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="4ef57-116">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="4ef57-116">See also</span></span>


[<span data-ttu-id="4ef57-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="4ef57-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)