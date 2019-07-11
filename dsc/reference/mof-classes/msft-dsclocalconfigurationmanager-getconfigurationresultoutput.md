---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: GetConfigurationResultOutput yöntemi
ms.openlocfilehash: 480e710ce1a208253f0e664474c3e9bab296066a
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727122"
---
# <a name="getconfigurationresultoutput-method"></a><span data-ttu-id="f786f-103">GetConfigurationResultOutput yöntemi</span><span class="sxs-lookup"><span data-stu-id="f786f-103">GetConfigurationResultOutput method</span></span>

<span data-ttu-id="f786f-104">Belirli bir işi ile ilişkili yapılandırma aracı çıkış alır.</span><span class="sxs-lookup"><span data-stu-id="f786f-104">Gets the Configuration Agent output associated with a specific job.</span></span>

## <a name="syntax"></a><span data-ttu-id="f786f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f786f-105">Syntax</span></span>

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

## <a name="parameters"></a><span data-ttu-id="f786f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f786f-106">Parameters</span></span>

<span data-ttu-id="f786f-107">*JobId* \[içinde\] iş için çıktı verilerini almak için kimliği.</span><span class="sxs-lookup"><span data-stu-id="f786f-107">*jobId* \[in\] The ID of the job for which to get output data.</span></span>

<span data-ttu-id="f786f-108">*resumeOutputBookmark* \[içinde\] çıkış bir önceki yer işareti gelen bir devamlılık olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f786f-108">*resumeOutputBookmark* \[in\] Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="f786f-109">*Çıkış* \[kullanıma\] belirtilen işin çıktısı.</span><span class="sxs-lookup"><span data-stu-id="f786f-109">*output* \[out\] The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="f786f-110">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="f786f-110">Return value</span></span>

<span data-ttu-id="f786f-111">Başarılıysa sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="f786f-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="f786f-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f786f-112">Remarks</span></span>

<span data-ttu-id="f786f-113">Statik bir yöntem budur.</span><span class="sxs-lookup"><span data-stu-id="f786f-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="f786f-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f786f-114">Requirements</span></span>

<span data-ttu-id="f786f-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="f786f-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="f786f-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="f786f-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="f786f-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f786f-117">See also</span></span>

[<span data-ttu-id="f786f-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="f786f-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
