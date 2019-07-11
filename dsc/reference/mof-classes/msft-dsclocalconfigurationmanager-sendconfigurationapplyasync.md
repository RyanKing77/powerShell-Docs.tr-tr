---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: SendConfigurationApplyAsync yöntemi
ms.openlocfilehash: c0e6dc9418757ee719e848fa8e7006dd73d91ad8
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734310"
---
# <a name="sendconfigurationapplyasync-method"></a><span data-ttu-id="68b82-103">SendConfigurationApplyAsync yöntemi</span><span class="sxs-lookup"><span data-stu-id="68b82-103">SendConfigurationApplyAsync method</span></span>

<span data-ttu-id="68b82-104">Yapılandırma belgelerini yönetilen düğüme zaman uyumsuz olarak gönderir ve yapılandırmayı uygulamak için yapılandırma aracısı kullanır.</span><span class="sxs-lookup"><span data-stu-id="68b82-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="68b82-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="68b82-105">Syntax</span></span>

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

## <a name="parameters"></a><span data-ttu-id="68b82-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="68b82-106">Parameters</span></span>

<span data-ttu-id="68b82-107">*ConfigurationData* \[içinde\] ortam verilerini.</span><span class="sxs-lookup"><span data-stu-id="68b82-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="68b82-108">*zorla* \[içinde\] **true** durdurmak için yapılandırmayı zorla uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="68b82-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

<span data-ttu-id="68b82-109">*JobId* \[içinde\] yapılandırma göndermek istediğiniz işin kimliği.</span><span class="sxs-lookup"><span data-stu-id="68b82-109">*jobId* \[in\] The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="68b82-110">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="68b82-110">Return value</span></span>

<span data-ttu-id="68b82-111">Başarılıysa sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="68b82-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="68b82-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="68b82-112">Remarks</span></span>

<span data-ttu-id="68b82-113">Statik bir yöntem budur.</span><span class="sxs-lookup"><span data-stu-id="68b82-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="68b82-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="68b82-114">Requirements</span></span>

<span data-ttu-id="68b82-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="68b82-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="68b82-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="68b82-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="68b82-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="68b82-117">See also</span></span>

[<span data-ttu-id="68b82-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="68b82-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
