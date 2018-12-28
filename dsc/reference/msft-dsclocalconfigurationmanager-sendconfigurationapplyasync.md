---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: MSFT_DSCLocalConfigurationManager sınıfının SendConfigurationApplyAsync yöntemi
ms.openlocfilehash: b028079cf826719967858f50e357b441ba8f9d79
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405674"
---
# <a name="sendconfigurationapplyasync-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="e8ff8-103">MSFT_DSCLocalConfigurationManager sınıfının SendConfigurationApplyAsync yöntemi</span><span class="sxs-lookup"><span data-stu-id="e8ff8-103">SendConfigurationApplyAsync method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="e8ff8-104">Yapılandırma belgelerini yönetilen düğüme zaman uyumsuz olarak gönderir ve yapılandırmayı uygulamak için yapılandırma aracısı kullanır.</span><span class="sxs-lookup"><span data-stu-id="e8ff8-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="e8ff8-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e8ff8-105">Syntax</span></span>

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

## <a name="parameters"></a><span data-ttu-id="e8ff8-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e8ff8-106">Parameters</span></span>

<span data-ttu-id="e8ff8-107">*ConfigurationData* \[içinde\] ortam verilerini.</span><span class="sxs-lookup"><span data-stu-id="e8ff8-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="e8ff8-108">*zorla* \[içinde\] **true** durdurmak için yapılandırmayı zorla uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="e8ff8-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

<span data-ttu-id="e8ff8-109">*JobId* \[içinde\] yapılandırma göndermek istediğiniz işin kimliği.</span><span class="sxs-lookup"><span data-stu-id="e8ff8-109">*jobId* \[in\] The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="e8ff8-110">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="e8ff8-110">Return value</span></span>

<span data-ttu-id="e8ff8-111">Başarılıysa sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="e8ff8-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="e8ff8-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e8ff8-112">Remarks</span></span>

<span data-ttu-id="e8ff8-113">Statik bir yöntem budur.</span><span class="sxs-lookup"><span data-stu-id="e8ff8-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e8ff8-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e8ff8-114">Requirements</span></span>

<span data-ttu-id="e8ff8-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="e8ff8-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="e8ff8-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="e8ff8-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="e8ff8-117">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="e8ff8-117">See also</span></span>

[<span data-ttu-id="e8ff8-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="e8ff8-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)