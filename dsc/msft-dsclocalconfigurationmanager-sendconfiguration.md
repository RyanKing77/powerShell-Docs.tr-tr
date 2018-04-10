---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, yapılandırma, Kur
title: MSFT_DSCLocalConfigurationManager sınıfının SendConfiguration yöntemi
ms.openlocfilehash: 07ae48dd456e68be4ad0b09127ba9801359fd101
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="sendconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="2493f-103">MSFT_DSCLocalConfigurationManager sınıfının SendConfiguration yöntemi</span><span class="sxs-lookup"><span data-stu-id="2493f-103">SendConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="2493f-104">Yönetilen düğüme yapılandırma belgesini gönderir ve bekleyen bir değişiklik kaydeder.</span><span class="sxs-lookup"><span data-stu-id="2493f-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

<a name="syntax"></a><span data-ttu-id="2493f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2493f-105">Syntax</span></span>
------

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="2493f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2493f-106">Parameters</span></span>
----------

<span data-ttu-id="2493f-107">*ConfigurationData* \[içinde\] yapılandırması için ortam verilerini.</span><span class="sxs-lookup"><span data-stu-id="2493f-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="2493f-108">*zorla* \[içinde\] **true** durdurmak için yapılandırmayı zorla uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="2493f-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="2493f-109">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="2493f-109">Return value</span></span>
------------

<span data-ttu-id="2493f-110">Başarı sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="2493f-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="2493f-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2493f-111">Remarks</span></span>

<span data-ttu-id="2493f-112">Bu statik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="2493f-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="2493f-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2493f-113">Requirements</span></span>
------------
><span data-ttu-id="2493f-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="2493f-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="2493f-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="2493f-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="2493f-116">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="2493f-116">See also</span></span>


[<span data-ttu-id="2493f-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="2493f-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)