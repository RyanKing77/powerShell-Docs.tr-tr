---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: MSFT_DSCLocalConfigurationManager sınıfının SendMetaConfigurationApply yöntemi
ms.openlocfilehash: 46acd86ac52b7b6b39f06fc65af2498b4f5348ed
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218850"
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="3cf4d-103">MSFT_DSCLocalConfigurationManager sınıfının SendMetaConfigurationApply yöntemi</span><span class="sxs-lookup"><span data-stu-id="3cf4d-103">SendMetaConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="3cf4d-104">Yapılandırma aracısı denetlemek için kullanılan yerel Configuration Manager ayarlarını belirler.</span><span class="sxs-lookup"><span data-stu-id="3cf4d-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="3cf4d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3cf4d-105">Syntax</span></span>
------

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="3cf4d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3cf4d-106">Parameters</span></span>
----------

<span data-ttu-id="3cf4d-107">*ConfigurationData* \[içinde\] yapılandırması için ortam verilerini.</span><span class="sxs-lookup"><span data-stu-id="3cf4d-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="3cf4d-108">*zorla* \[içinde\] **true** durdurmak için yapılandırmayı zorla uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="3cf4d-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="3cf4d-109">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="3cf4d-109">Return value</span></span>
------------

<span data-ttu-id="3cf4d-110">Başarı sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="3cf4d-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="3cf4d-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3cf4d-111">Remarks</span></span>

<span data-ttu-id="3cf4d-112">Bu statik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="3cf4d-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="3cf4d-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3cf4d-113">Requirements</span></span>
------------
><span data-ttu-id="3cf4d-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="3cf4d-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="3cf4d-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="3cf4d-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="3cf4d-116">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="3cf4d-116">See also</span></span>


[<span data-ttu-id="3cf4d-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="3cf4d-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)