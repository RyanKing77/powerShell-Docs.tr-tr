---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: MSFT_DSCLocalConfigurationManager sınıfının SendConfigurationApply yöntemi
ms.openlocfilehash: da3a08307122ab38ee4a6fd5d4a9b97579a988f7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685392"
---
# <a name="sendconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="543fc-103">MSFT_DSCLocalConfigurationManager sınıfının SendConfigurationApply yöntemi</span><span class="sxs-lookup"><span data-stu-id="543fc-103">SendConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="543fc-104">Yapılandırma belgelerini yönetilen düğüme gönderir ve yapılandırmayı uygulamak için yapılandırma aracısı kullanır.</span><span class="sxs-lookup"><span data-stu-id="543fc-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="543fc-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="543fc-105">Syntax</span></span>

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="543fc-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="543fc-106">Parameters</span></span>

<span data-ttu-id="543fc-107">*ConfigurationData* \[içinde\] ortam verilerini.</span><span class="sxs-lookup"><span data-stu-id="543fc-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="543fc-108">*zorla* \[içinde\] **true** durdurmak için yapılandırmayı zorla uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="543fc-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="543fc-109">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="543fc-109">Return value</span></span>

<span data-ttu-id="543fc-110">Başarılıysa sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="543fc-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="543fc-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="543fc-111">Remarks</span></span>

<span data-ttu-id="543fc-112">Statik bir yöntem budur.</span><span class="sxs-lookup"><span data-stu-id="543fc-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="543fc-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="543fc-113">Requirements</span></span>

<span data-ttu-id="543fc-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="543fc-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="543fc-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="543fc-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="543fc-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="543fc-116">See also</span></span>

[<span data-ttu-id="543fc-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="543fc-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)