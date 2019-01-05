---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: MSFT_DSCLocalConfigurationManager sınıfının SendConfiguration yöntemi
ms.openlocfilehash: 3529bc56ecba19ed0fbbf070a4e86d0692824d39
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048639"
---
# <a name="sendconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="e8609-103">MSFT_DSCLocalConfigurationManager sınıfının SendConfiguration yöntemi</span><span class="sxs-lookup"><span data-stu-id="e8609-103">SendConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="e8609-104">Yapılandırma belgelerini yönetilen düğüme gönderir ve bir bekleyen değişiklik olarak kaydeder.</span><span class="sxs-lookup"><span data-stu-id="e8609-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

## <a name="syntax"></a><span data-ttu-id="e8609-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e8609-105">Syntax</span></span>

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="e8609-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e8609-106">Parameters</span></span>

<span data-ttu-id="e8609-107">*ConfigurationData* \[içinde\] ortam verilerini.</span><span class="sxs-lookup"><span data-stu-id="e8609-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="e8609-108">*zorla* \[içinde\] **true** durdurmak için yapılandırmayı zorla uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="e8609-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="e8609-109">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="e8609-109">Return value</span></span>

<span data-ttu-id="e8609-110">Başarılıysa sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="e8609-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="e8609-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e8609-111">Remarks</span></span>

<span data-ttu-id="e8609-112">Statik bir yöntem budur.</span><span class="sxs-lookup"><span data-stu-id="e8609-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e8609-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e8609-113">Requirements</span></span>

<span data-ttu-id="e8609-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="e8609-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="e8609-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="e8609-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="e8609-116">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="e8609-116">See also</span></span>

[<span data-ttu-id="e8609-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="e8609-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)