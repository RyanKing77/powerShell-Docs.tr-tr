---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: SendConfigurationApply yöntemi
ms.openlocfilehash: 11b9d435bbaac1600d25ff074b6c55b236a8378b
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727006"
---
# <a name="sendconfigurationapply-method"></a><span data-ttu-id="61b50-103">SendConfigurationApply yöntemi</span><span class="sxs-lookup"><span data-stu-id="61b50-103">SendConfigurationApply method</span></span>

<span data-ttu-id="61b50-104">Yapılandırma belgelerini yönetilen düğüme gönderir ve yapılandırmayı uygulamak için yapılandırma aracısı kullanır.</span><span class="sxs-lookup"><span data-stu-id="61b50-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="61b50-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="61b50-105">Syntax</span></span>

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="61b50-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="61b50-106">Parameters</span></span>

<span data-ttu-id="61b50-107">*ConfigurationData* \[içinde\] ortam verilerini.</span><span class="sxs-lookup"><span data-stu-id="61b50-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="61b50-108">*zorla* \[içinde\] **true** durdurmak için yapılandırmayı zorla uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="61b50-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="61b50-109">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="61b50-109">Return value</span></span>

<span data-ttu-id="61b50-110">Başarılıysa sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="61b50-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="61b50-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="61b50-111">Remarks</span></span>

<span data-ttu-id="61b50-112">Statik bir yöntem budur.</span><span class="sxs-lookup"><span data-stu-id="61b50-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="61b50-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="61b50-113">Requirements</span></span>

<span data-ttu-id="61b50-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="61b50-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="61b50-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="61b50-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="61b50-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="61b50-116">See also</span></span>

[<span data-ttu-id="61b50-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="61b50-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
