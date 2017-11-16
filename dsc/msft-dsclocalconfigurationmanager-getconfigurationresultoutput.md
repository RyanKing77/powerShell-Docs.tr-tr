---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "MSFT_DSCLocalConfigurationManager sınıfının GetConfigurationResultOutput yöntemi"
ms.openlocfilehash: 09862fd3c19e1e517c9bf5df878113ba3f10d8a6
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="d078d-103">MSFT_DSCLocalConfigurationManager sınıfının GetConfigurationResultOutput yöntemi</span><span class="sxs-lookup"><span data-stu-id="d078d-103">GetConfigurationResultOutput method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="d078d-104">Belirli bir iş ile ilgili yapılandırma aracısı çıktısını alır.</span><span class="sxs-lookup"><span data-stu-id="d078d-104">Gets the Configuration Agent output associated with a specific job.</span></span>

<a name="syntax"></a><span data-ttu-id="d078d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d078d-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

<a name="parameters"></a><span data-ttu-id="d078d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d078d-106">Parameters</span></span>
----------

<span data-ttu-id="d078d-107">*JobId* \[içinde\]</span><span class="sxs-lookup"><span data-stu-id="d078d-107">*jobId* \[in\]</span></span>  
<span data-ttu-id="d078d-108">Proje çıktı verileri almak istediğiniz için kimliği.</span><span class="sxs-lookup"><span data-stu-id="d078d-108">The ID of the job for which to get output data.</span></span>

<span data-ttu-id="d078d-109">*resumeOutputBookmark* \[içinde\]</span><span class="sxs-lookup"><span data-stu-id="d078d-109">*resumeOutputBookmark* \[in\]</span></span>  
<span data-ttu-id="d078d-110">Çıktı devamlılığı önceki yer işareti gelen olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d078d-110">Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="d078d-111">*Çıktı* \[çıkışı\]</span><span class="sxs-lookup"><span data-stu-id="d078d-111">*output* \[out\]</span></span>  
<span data-ttu-id="d078d-112">Belirtilen iş için çıktı.</span><span class="sxs-lookup"><span data-stu-id="d078d-112">The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="d078d-113">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="d078d-113">Return value</span></span>
------------

<span data-ttu-id="d078d-114">Başarı sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="d078d-114">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="d078d-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d078d-115">Remarks</span></span>

<span data-ttu-id="d078d-116">Bu statik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="d078d-116">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d078d-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d078d-117">Requirements</span></span>
------------
><span data-ttu-id="d078d-118">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="d078d-118">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="d078d-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="d078d-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="d078d-120">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="d078d-120">See also</span></span>


[<span data-ttu-id="d078d-121">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="d078d-121">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

 

 



