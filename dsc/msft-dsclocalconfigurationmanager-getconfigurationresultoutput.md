---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "MSFT_DSCLocalConfigurationManager sınıfının GetConfigurationResultOutput yöntemi"
ms.openlocfilehash: f6106bb28dc20004b5bbb6df2d8e719cf0c453f0
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="5d6f1-103">MSFT_DSCLocalConfigurationManager sınıfının GetConfigurationResultOutput yöntemi</span><span class="sxs-lookup"><span data-stu-id="5d6f1-103">GetConfigurationResultOutput method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="5d6f1-104">Belirli bir iş ile ilgili yapılandırma aracısı çıktısını alır.</span><span class="sxs-lookup"><span data-stu-id="5d6f1-104">Gets the Configuration Agent output associated with a specific job.</span></span>

<a name="syntax"></a><span data-ttu-id="5d6f1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5d6f1-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

<a name="parameters"></a><span data-ttu-id="5d6f1-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5d6f1-106">Parameters</span></span>
----------

<span data-ttu-id="5d6f1-107">*jobId* \[in\]</span><span class="sxs-lookup"><span data-stu-id="5d6f1-107">*jobId* \[in\]</span></span>  
<span data-ttu-id="5d6f1-108">Proje çıktı verileri almak istediğiniz için kimliği.</span><span class="sxs-lookup"><span data-stu-id="5d6f1-108">The ID of the job for which to get output data.</span></span>

<span data-ttu-id="5d6f1-109">*resumeOutputBookmark* \[in\]</span><span class="sxs-lookup"><span data-stu-id="5d6f1-109">*resumeOutputBookmark* \[in\]</span></span>  
<span data-ttu-id="5d6f1-110">Çıktı devamlılığı önceki yer işareti gelen olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5d6f1-110">Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="5d6f1-111">*Çıktı* \[çıkışı\]</span><span class="sxs-lookup"><span data-stu-id="5d6f1-111">*output* \[out\]</span></span>  
<span data-ttu-id="5d6f1-112">Belirtilen iş için çıktı.</span><span class="sxs-lookup"><span data-stu-id="5d6f1-112">The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="5d6f1-113">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="5d6f1-113">Return value</span></span>
------------

<span data-ttu-id="5d6f1-114">Başarı sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="5d6f1-114">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="5d6f1-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5d6f1-115">Remarks</span></span>

<span data-ttu-id="5d6f1-116">Bu statik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="5d6f1-116">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="5d6f1-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5d6f1-117">Requirements</span></span>
------------
><span data-ttu-id="5d6f1-118">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="5d6f1-118">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="5d6f1-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="5d6f1-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="5d6f1-120">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="5d6f1-120">See also</span></span>


[<span data-ttu-id="5d6f1-121">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="5d6f1-121">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

 

 



