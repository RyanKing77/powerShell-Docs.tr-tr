---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "MSFT_DSCLocalConfigurationManager sınıfının SendConfigurationApply yöntemi"
ms.openlocfilehash: 20f732d35860cccde4e507dc6916e27d0cf8c5f6
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="sendconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="a9ee7-103">MSFT_DSCLocalConfigurationManager sınıfının SendConfigurationApply yöntemi</span><span class="sxs-lookup"><span data-stu-id="a9ee7-103">SendConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="a9ee7-104">Yönetilen düğüme yapılandırma belgesini gönderir ve yapılandırmayı uygulamak için yapılandırma Aracısı'nı kullanır.</span><span class="sxs-lookup"><span data-stu-id="a9ee7-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="a9ee7-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a9ee7-105">Syntax</span></span>
------

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="a9ee7-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a9ee7-106">Parameters</span></span>
----------

<span data-ttu-id="a9ee7-107">*ConfigurationData* \[içinde\]</span><span class="sxs-lookup"><span data-stu-id="a9ee7-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="a9ee7-108">Ortam verilerini yapılandırması için.</span><span class="sxs-lookup"><span data-stu-id="a9ee7-108">The environment data for the configuration.</span></span>

<span data-ttu-id="a9ee7-109">*zorla* \[içinde\]</span><span class="sxs-lookup"><span data-stu-id="a9ee7-109">*force* \[in\]</span></span>  
<span data-ttu-id="a9ee7-110">**doğru** durdurmak için yapılandırmayı zorla uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="a9ee7-110">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="a9ee7-111">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="a9ee7-111">Return value</span></span>
------------

<span data-ttu-id="a9ee7-112">Başarı sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="a9ee7-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="a9ee7-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a9ee7-113">Remarks</span></span>

<span data-ttu-id="a9ee7-114">Bu statik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="a9ee7-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="a9ee7-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a9ee7-115">Requirements</span></span>
------------
><span data-ttu-id="a9ee7-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="a9ee7-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="a9ee7-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="a9ee7-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="a9ee7-118">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="a9ee7-118">See also</span></span>


[<span data-ttu-id="a9ee7-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="a9ee7-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



