---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: MSFT_DSCLocalConfigurationManager sınıfının SendConfigurationApplyAsync yöntemi
ms.openlocfilehash: b028079cf826719967858f50e357b441ba8f9d79
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688836"
---
# <a name="sendconfigurationapplyasync-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="9d1de-103">MSFT_DSCLocalConfigurationManager sınıfının SendConfigurationApplyAsync yöntemi</span><span class="sxs-lookup"><span data-stu-id="9d1de-103">SendConfigurationApplyAsync method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="9d1de-104">Yapılandırma belgelerini yönetilen düğüme zaman uyumsuz olarak gönderir ve yapılandırmayı uygulamak için yapılandırma aracısı kullanır.</span><span class="sxs-lookup"><span data-stu-id="9d1de-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="9d1de-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9d1de-105">Syntax</span></span>

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

## <a name="parameters"></a><span data-ttu-id="9d1de-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9d1de-106">Parameters</span></span>

<span data-ttu-id="9d1de-107">*ConfigurationData* \[içinde\] ortam verilerini.</span><span class="sxs-lookup"><span data-stu-id="9d1de-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="9d1de-108">*zorla* \[içinde\] **true** durdurmak için yapılandırmayı zorla uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="9d1de-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

<span data-ttu-id="9d1de-109">*JobId* \[içinde\] yapılandırma göndermek istediğiniz işin kimliği.</span><span class="sxs-lookup"><span data-stu-id="9d1de-109">*jobId* \[in\] The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="9d1de-110">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="9d1de-110">Return value</span></span>

<span data-ttu-id="9d1de-111">Başarılıysa sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="9d1de-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="9d1de-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9d1de-112">Remarks</span></span>

<span data-ttu-id="9d1de-113">Statik bir yöntem budur.</span><span class="sxs-lookup"><span data-stu-id="9d1de-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="9d1de-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9d1de-114">Requirements</span></span>

<span data-ttu-id="9d1de-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="9d1de-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="9d1de-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="9d1de-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="9d1de-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9d1de-117">See also</span></span>

[<span data-ttu-id="9d1de-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="9d1de-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)