---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: MSFT_DSCLocalConfigurationManager sınıfının SendConfiguration yöntemi
ms.openlocfilehash: 3529bc56ecba19ed0fbbf070a4e86d0692824d39
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405671"
---
# <a name="sendconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="da70a-103">MSFT_DSCLocalConfigurationManager sınıfının SendConfiguration yöntemi</span><span class="sxs-lookup"><span data-stu-id="da70a-103">SendConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="da70a-104">Yapılandırma belgelerini yönetilen düğüme gönderir ve bir bekleyen değişiklik olarak kaydeder.</span><span class="sxs-lookup"><span data-stu-id="da70a-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

## <a name="syntax"></a><span data-ttu-id="da70a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="da70a-105">Syntax</span></span>

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="da70a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="da70a-106">Parameters</span></span>

<span data-ttu-id="da70a-107">*ConfigurationData* \[içinde\] ortam verilerini.</span><span class="sxs-lookup"><span data-stu-id="da70a-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="da70a-108">*zorla* \[içinde\] **true** durdurmak için yapılandırmayı zorla uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="da70a-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="da70a-109">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="da70a-109">Return value</span></span>

<span data-ttu-id="da70a-110">Başarılıysa sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="da70a-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="da70a-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="da70a-111">Remarks</span></span>

<span data-ttu-id="da70a-112">Statik bir yöntem budur.</span><span class="sxs-lookup"><span data-stu-id="da70a-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="da70a-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="da70a-113">Requirements</span></span>

<span data-ttu-id="da70a-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="da70a-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="da70a-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="da70a-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="da70a-116">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="da70a-116">See also</span></span>

[<span data-ttu-id="da70a-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="da70a-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)