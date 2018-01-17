---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "MSFT_DSCLocalConfigurationManager sınıfının SendConfigurationApplyAsync yöntemi"
ms.openlocfilehash: e680d510aaac097f4f0de80660274230e028ed45
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="sendconfigurationapplyasync-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="a9447-103">MSFT_DSCLocalConfigurationManager sınıfının SendConfigurationApplyAsync yöntemi</span><span class="sxs-lookup"><span data-stu-id="a9447-103">SendConfigurationApplyAsync method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="a9447-104">Yönetilen düğüme yapılandırma belgesini zaman uyumsuz olarak gönderir ve yapılandırmayı uygulamak için yapılandırma aracısı kullanır.</span><span class="sxs-lookup"><span data-stu-id="a9447-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="a9447-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a9447-105">Syntax</span></span>
------

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

<a name="parameters"></a><span data-ttu-id="a9447-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a9447-106">Parameters</span></span>
----------

<span data-ttu-id="a9447-107">*ConfigurationData* \[içinde\]</span><span class="sxs-lookup"><span data-stu-id="a9447-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="a9447-108">Ortam verilerini yapılandırması için.</span><span class="sxs-lookup"><span data-stu-id="a9447-108">The environment data for the configuration.</span></span>

<span data-ttu-id="a9447-109">*zorla* \[içinde\]</span><span class="sxs-lookup"><span data-stu-id="a9447-109">*force* \[in\]</span></span>  
<span data-ttu-id="a9447-110">**doğru** durdurmak için yapılandırmayı zorla uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="a9447-110">**true** to force the configuration to stop.</span></span>

<span data-ttu-id="a9447-111">*jobId* \[in\]</span><span class="sxs-lookup"><span data-stu-id="a9447-111">*jobId* \[in\]</span></span>  
<span data-ttu-id="a9447-112">İş için yapılandırma gönderileceği kimliği.</span><span class="sxs-lookup"><span data-stu-id="a9447-112">The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="a9447-113">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="a9447-113">Return value</span></span>
------------

<span data-ttu-id="a9447-114">Başarı sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="a9447-114">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="a9447-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a9447-115">Remarks</span></span>

<span data-ttu-id="a9447-116">Bu statik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="a9447-116">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="a9447-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a9447-117">Requirements</span></span>
------------
><span data-ttu-id="a9447-118">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="a9447-118">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="a9447-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="a9447-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="a9447-120">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="a9447-120">See also</span></span>


[<span data-ttu-id="a9447-121">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="a9447-121">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



