---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: SendConfiguration yöntemi
ms.openlocfilehash: 4feba090bc58844659c2329a304dd9805255564f
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734314"
---
# <a name="sendconfiguration-method"></a><span data-ttu-id="66540-103">SendConfiguration yöntemi</span><span class="sxs-lookup"><span data-stu-id="66540-103">SendConfiguration method</span></span>

<span data-ttu-id="66540-104">Yapılandırma belgelerini yönetilen düğüme gönderir ve bir bekleyen değişiklik olarak kaydeder.</span><span class="sxs-lookup"><span data-stu-id="66540-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

## <a name="syntax"></a><span data-ttu-id="66540-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="66540-105">Syntax</span></span>

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="66540-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="66540-106">Parameters</span></span>

<span data-ttu-id="66540-107">*ConfigurationData* \[içinde\] ortam verilerini.</span><span class="sxs-lookup"><span data-stu-id="66540-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="66540-108">*zorla* \[içinde\] **true** durdurmak için yapılandırmayı zorla uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="66540-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="66540-109">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="66540-109">Return value</span></span>

<span data-ttu-id="66540-110">Başarılıysa sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="66540-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="66540-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="66540-111">Remarks</span></span>

<span data-ttu-id="66540-112">Statik bir yöntem budur.</span><span class="sxs-lookup"><span data-stu-id="66540-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="66540-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="66540-113">Requirements</span></span>

<span data-ttu-id="66540-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="66540-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="66540-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="66540-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="66540-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="66540-116">See also</span></span>

[<span data-ttu-id="66540-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="66540-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
