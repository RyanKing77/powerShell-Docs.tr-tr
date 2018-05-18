---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: MSFT_DSCLocalConfigurationManager sınıfının GetConfigurationResultOutput yöntemi
ms.openlocfilehash: 73d10a8b44e5056e3fce1598518630a84aff6ceb
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="edf85-103">MSFT_DSCLocalConfigurationManager sınıfının GetConfigurationResultOutput yöntemi</span><span class="sxs-lookup"><span data-stu-id="edf85-103">GetConfigurationResultOutput method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="edf85-104">Belirli bir iş ile ilgili yapılandırma aracısı çıktısını alır.</span><span class="sxs-lookup"><span data-stu-id="edf85-104">Gets the Configuration Agent output associated with a specific job.</span></span>

<a name="syntax"></a><span data-ttu-id="edf85-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="edf85-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

<a name="parameters"></a><span data-ttu-id="edf85-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="edf85-106">Parameters</span></span>
----------

<span data-ttu-id="edf85-107">*JobId* \[içinde\] , çıktı verilerini almak iş kimliği.</span><span class="sxs-lookup"><span data-stu-id="edf85-107">*jobId* \[in\] The ID of the job for which to get output data.</span></span>

<span data-ttu-id="edf85-108">*resumeOutputBookmark* \[içinde\] çıkış devamlılığı önceki yer işareti gelen olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="edf85-108">*resumeOutputBookmark* \[in\] Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="edf85-109">*Çıktı* \[çıkışı\] belirtilen iş için çıktı.</span><span class="sxs-lookup"><span data-stu-id="edf85-109">*output* \[out\] The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="edf85-110">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="edf85-110">Return value</span></span>
------------

<span data-ttu-id="edf85-111">Başarı sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="edf85-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="edf85-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="edf85-112">Remarks</span></span>

<span data-ttu-id="edf85-113">Bu statik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="edf85-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="edf85-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="edf85-114">Requirements</span></span>
------------
><span data-ttu-id="edf85-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="edf85-115">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="edf85-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="edf85-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="edf85-117">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="edf85-117">See also</span></span>


[<span data-ttu-id="edf85-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="edf85-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)