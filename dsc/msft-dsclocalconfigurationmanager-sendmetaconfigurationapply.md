---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "MSFT_DSCLocalConfigurationManager sınıfının SendMetaConfigurationApply yöntemi"
ms.openlocfilehash: 350555220757b1939b1de34ab423e963635eb53c
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="d6415-103">MSFT_DSCLocalConfigurationManager sınıfının SendMetaConfigurationApply yöntemi</span><span class="sxs-lookup"><span data-stu-id="d6415-103">SendMetaConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="d6415-104">Yapılandırma aracısı denetlemek için kullanılan yerel Configuration Manager ayarlarını belirler.</span><span class="sxs-lookup"><span data-stu-id="d6415-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="d6415-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d6415-105">Syntax</span></span>
------

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="d6415-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d6415-106">Parameters</span></span>
----------

<span data-ttu-id="d6415-107">*ConfigurationData* \[içinde\]</span><span class="sxs-lookup"><span data-stu-id="d6415-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="d6415-108">Ortam verilerini yapılandırması için.</span><span class="sxs-lookup"><span data-stu-id="d6415-108">The environment data for the configuration.</span></span>

<span data-ttu-id="d6415-109">*zorla* \[içinde\]</span><span class="sxs-lookup"><span data-stu-id="d6415-109">*force* \[in\]</span></span>  
<span data-ttu-id="d6415-110">**doğru** durdurmak için yapılandırmayı zorla uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="d6415-110">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="d6415-111">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="d6415-111">Return value</span></span>
------------

<span data-ttu-id="d6415-112">Başarı sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="d6415-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="d6415-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d6415-113">Remarks</span></span>

<span data-ttu-id="d6415-114">Bu statik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="d6415-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d6415-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d6415-115">Requirements</span></span>
------------
><span data-ttu-id="d6415-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="d6415-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="d6415-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="d6415-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="d6415-118">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="d6415-118">See also</span></span>


[<span data-ttu-id="d6415-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="d6415-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



