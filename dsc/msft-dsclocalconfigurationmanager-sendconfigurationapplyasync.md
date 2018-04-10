---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, yapılandırma, Kur
title: MSFT_DSCLocalConfigurationManager sınıfının SendConfigurationApplyAsync yöntemi
ms.openlocfilehash: 7ff821a277a548869862741551ee9897e417ea45
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="sendconfigurationapplyasync-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="36e59-103">MSFT_DSCLocalConfigurationManager sınıfının SendConfigurationApplyAsync yöntemi</span><span class="sxs-lookup"><span data-stu-id="36e59-103">SendConfigurationApplyAsync method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="36e59-104">Yönetilen düğüme yapılandırma belgesini zaman uyumsuz olarak gönderir ve yapılandırmayı uygulamak için yapılandırma aracısı kullanır.</span><span class="sxs-lookup"><span data-stu-id="36e59-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="36e59-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="36e59-105">Syntax</span></span>
------

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

<a name="parameters"></a><span data-ttu-id="36e59-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="36e59-106">Parameters</span></span>
----------

<span data-ttu-id="36e59-107">*ConfigurationData* \[içinde\] yapılandırması için ortam verilerini.</span><span class="sxs-lookup"><span data-stu-id="36e59-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="36e59-108">*zorla* \[içinde\] **true** durdurmak için yapılandırmayı zorla uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="36e59-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

<span data-ttu-id="36e59-109">*JobId* \[içinde\] yapılandırma göndermek işin kimliği.</span><span class="sxs-lookup"><span data-stu-id="36e59-109">*jobId* \[in\] The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="36e59-110">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="36e59-110">Return value</span></span>
------------

<span data-ttu-id="36e59-111">Başarı sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="36e59-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="36e59-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="36e59-112">Remarks</span></span>

<span data-ttu-id="36e59-113">Bu statik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="36e59-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="36e59-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="36e59-114">Requirements</span></span>
------------
><span data-ttu-id="36e59-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="36e59-115">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="36e59-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="36e59-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="36e59-117">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="36e59-117">See also</span></span>


[<span data-ttu-id="36e59-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="36e59-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)