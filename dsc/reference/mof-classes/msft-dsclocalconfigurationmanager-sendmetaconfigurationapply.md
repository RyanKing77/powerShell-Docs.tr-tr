---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: SendMetaConfigurationApply yöntemi
ms.openlocfilehash: b2e420bafb8ea22aea43800f6e429d3ed785d1e8
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727051"
---
# <a name="sendmetaconfigurationapply-method"></a><span data-ttu-id="e0060-103">SendMetaConfigurationApply yöntemi</span><span class="sxs-lookup"><span data-stu-id="e0060-103">SendMetaConfigurationApply method</span></span>

<span data-ttu-id="e0060-104">Yapılandırma Aracı denetlemek için kullanılan yerel Configuration Manager ayarlarını belirler.</span><span class="sxs-lookup"><span data-stu-id="e0060-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="e0060-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e0060-105">Syntax</span></span>

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="e0060-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e0060-106">Parameters</span></span>

<span data-ttu-id="e0060-107">*ConfigurationData* \[içinde\] ortam verilerini.</span><span class="sxs-lookup"><span data-stu-id="e0060-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="e0060-108">*zorla* \[içinde\] **true** durdurmak için yapılandırmayı zorla uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="e0060-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="e0060-109">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="e0060-109">Return value</span></span>

<span data-ttu-id="e0060-110">Başarılıysa sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="e0060-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="e0060-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e0060-111">Remarks</span></span>

<span data-ttu-id="e0060-112">Statik bir yöntem budur.</span><span class="sxs-lookup"><span data-stu-id="e0060-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e0060-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e0060-113">Requirements</span></span>

<span data-ttu-id="e0060-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="e0060-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="e0060-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="e0060-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="e0060-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e0060-116">See also</span></span>

[<span data-ttu-id="e0060-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="e0060-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
