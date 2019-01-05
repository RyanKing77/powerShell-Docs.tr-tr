---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: MSFT_DSCLocalConfigurationManager sınıfının SendMetaConfigurationApply yöntemi
ms.openlocfilehash: b372a6c0ab9d4561dcf67026275e7d3ca6aa2584
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048797"
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="12aee-103">MSFT_DSCLocalConfigurationManager sınıfının SendMetaConfigurationApply yöntemi</span><span class="sxs-lookup"><span data-stu-id="12aee-103">SendMetaConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="12aee-104">Yapılandırma Aracı denetlemek için kullanılan yerel Configuration Manager ayarlarını belirler.</span><span class="sxs-lookup"><span data-stu-id="12aee-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="12aee-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="12aee-105">Syntax</span></span>

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="12aee-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="12aee-106">Parameters</span></span>

<span data-ttu-id="12aee-107">*ConfigurationData* \[içinde\] ortam verilerini.</span><span class="sxs-lookup"><span data-stu-id="12aee-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="12aee-108">*zorla* \[içinde\] **true** durdurmak için yapılandırmayı zorla uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="12aee-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="12aee-109">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="12aee-109">Return value</span></span>

<span data-ttu-id="12aee-110">Başarılıysa sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="12aee-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="12aee-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="12aee-111">Remarks</span></span>

<span data-ttu-id="12aee-112">Statik bir yöntem budur.</span><span class="sxs-lookup"><span data-stu-id="12aee-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="12aee-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="12aee-113">Requirements</span></span>

<span data-ttu-id="12aee-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="12aee-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="12aee-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="12aee-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="12aee-116">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="12aee-116">See also</span></span>

[<span data-ttu-id="12aee-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="12aee-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)