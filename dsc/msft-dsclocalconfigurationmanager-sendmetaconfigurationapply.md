---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "MSFT_DSCLocalConfigurationManager sınıfının SendMetaConfigurationApply yöntemi"
ms.openlocfilehash: d8ddc9d99f0d74ad907a6e39ae0e8ac14159be16
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="52c6a-103">MSFT_DSCLocalConfigurationManager sınıfının SendMetaConfigurationApply yöntemi</span><span class="sxs-lookup"><span data-stu-id="52c6a-103">SendMetaConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="52c6a-104">Yapılandırma aracısı denetlemek için kullanılan yerel Configuration Manager ayarlarını belirler.</span><span class="sxs-lookup"><span data-stu-id="52c6a-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="52c6a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="52c6a-105">Syntax</span></span>
------

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="52c6a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="52c6a-106">Parameters</span></span>
----------

<span data-ttu-id="52c6a-107">*ConfigurationData* \[içinde\]</span><span class="sxs-lookup"><span data-stu-id="52c6a-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="52c6a-108">Ortam verilerini yapılandırması için.</span><span class="sxs-lookup"><span data-stu-id="52c6a-108">The environment data for the configuration.</span></span>

<span data-ttu-id="52c6a-109">*zorla* \[içinde\]</span><span class="sxs-lookup"><span data-stu-id="52c6a-109">*force* \[in\]</span></span>  
<span data-ttu-id="52c6a-110">**doğru** durdurmak için yapılandırmayı zorla uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="52c6a-110">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="52c6a-111">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="52c6a-111">Return value</span></span>
------------

<span data-ttu-id="52c6a-112">Başarı sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="52c6a-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="52c6a-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="52c6a-113">Remarks</span></span>

<span data-ttu-id="52c6a-114">Bu statik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="52c6a-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="52c6a-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="52c6a-115">Requirements</span></span>
------------
><span data-ttu-id="52c6a-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="52c6a-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="52c6a-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="52c6a-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="52c6a-118">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="52c6a-118">See also</span></span>


[<span data-ttu-id="52c6a-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="52c6a-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



