---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: MSFT_DSCLocalConfigurationManager sınıfının SendMetaConfigurationApply yöntemi
ms.openlocfilehash: b372a6c0ab9d4561dcf67026275e7d3ca6aa2584
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892966"
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="fcafc-103">MSFT_DSCLocalConfigurationManager sınıfının SendMetaConfigurationApply yöntemi</span><span class="sxs-lookup"><span data-stu-id="fcafc-103">SendMetaConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="fcafc-104">Yapılandırma Aracı denetlemek için kullanılan yerel Configuration Manager ayarlarını belirler.</span><span class="sxs-lookup"><span data-stu-id="fcafc-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="fcafc-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fcafc-105">Syntax</span></span>

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="fcafc-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fcafc-106">Parameters</span></span>

<span data-ttu-id="fcafc-107">*ConfigurationData* \[içinde\] ortam verilerini.</span><span class="sxs-lookup"><span data-stu-id="fcafc-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="fcafc-108">*zorla* \[içinde\] **true** durdurmak için yapılandırmayı zorla uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="fcafc-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="fcafc-109">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="fcafc-109">Return value</span></span>

<span data-ttu-id="fcafc-110">Başarılıysa sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="fcafc-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="fcafc-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fcafc-111">Remarks</span></span>

<span data-ttu-id="fcafc-112">Statik bir yöntem budur.</span><span class="sxs-lookup"><span data-stu-id="fcafc-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="fcafc-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fcafc-113">Requirements</span></span>

<span data-ttu-id="fcafc-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="fcafc-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="fcafc-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="fcafc-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="fcafc-116">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="fcafc-116">See also</span></span>

[<span data-ttu-id="fcafc-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="fcafc-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)