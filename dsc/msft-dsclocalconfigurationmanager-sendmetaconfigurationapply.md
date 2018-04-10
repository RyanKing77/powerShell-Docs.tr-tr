---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, yapılandırma, Kur
title: MSFT_DSCLocalConfigurationManager sınıfının SendMetaConfigurationApply yöntemi
ms.openlocfilehash: ab82b239ddfdb4075d9440cd66343266b3c08eda
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="ea5a6-103">MSFT_DSCLocalConfigurationManager sınıfının SendMetaConfigurationApply yöntemi</span><span class="sxs-lookup"><span data-stu-id="ea5a6-103">SendMetaConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="ea5a6-104">Yapılandırma aracısı denetlemek için kullanılan yerel Configuration Manager ayarlarını belirler.</span><span class="sxs-lookup"><span data-stu-id="ea5a6-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="ea5a6-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ea5a6-105">Syntax</span></span>
------

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="ea5a6-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ea5a6-106">Parameters</span></span>
----------

<span data-ttu-id="ea5a6-107">*ConfigurationData* \[içinde\] yapılandırması için ortam verilerini.</span><span class="sxs-lookup"><span data-stu-id="ea5a6-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="ea5a6-108">*zorla* \[içinde\] **true** durdurmak için yapılandırmayı zorla uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="ea5a6-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="ea5a6-109">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="ea5a6-109">Return value</span></span>
------------

<span data-ttu-id="ea5a6-110">Başarı sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="ea5a6-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="ea5a6-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ea5a6-111">Remarks</span></span>

<span data-ttu-id="ea5a6-112">Bu statik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="ea5a6-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="ea5a6-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ea5a6-113">Requirements</span></span>
------------
><span data-ttu-id="ea5a6-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="ea5a6-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="ea5a6-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="ea5a6-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="ea5a6-116">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="ea5a6-116">See also</span></span>


[<span data-ttu-id="ea5a6-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="ea5a6-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)