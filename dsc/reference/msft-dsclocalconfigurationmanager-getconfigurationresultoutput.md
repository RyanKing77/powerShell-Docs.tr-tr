---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: MSFT_DSCLocalConfigurationManager sınıfının GetConfigurationResultOutput yöntemi
ms.openlocfilehash: ea572a4a66befd4e4b8d83e2957632b1b5ed7d93
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405829"
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="98b99-103">MSFT_DSCLocalConfigurationManager sınıfının GetConfigurationResultOutput yöntemi</span><span class="sxs-lookup"><span data-stu-id="98b99-103">GetConfigurationResultOutput method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="98b99-104">Belirli bir işi ile ilişkili yapılandırma aracı çıkış alır.</span><span class="sxs-lookup"><span data-stu-id="98b99-104">Gets the Configuration Agent output associated with a specific job.</span></span>

## <a name="syntax"></a><span data-ttu-id="98b99-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="98b99-105">Syntax</span></span>

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

## <a name="parameters"></a><span data-ttu-id="98b99-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="98b99-106">Parameters</span></span>

<span data-ttu-id="98b99-107">*JobId* \[içinde\] iş için çıktı verilerini almak için kimliği.</span><span class="sxs-lookup"><span data-stu-id="98b99-107">*jobId* \[in\] The ID of the job for which to get output data.</span></span>

<span data-ttu-id="98b99-108">*resumeOutputBookmark* \[içinde\] çıkış bir önceki yer işareti gelen bir devamlılık olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="98b99-108">*resumeOutputBookmark* \[in\] Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="98b99-109">*Çıkış* \[kullanıma\] belirtilen işin çıktısı.</span><span class="sxs-lookup"><span data-stu-id="98b99-109">*output* \[out\] The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="98b99-110">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="98b99-110">Return value</span></span>

<span data-ttu-id="98b99-111">Başarılıysa sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="98b99-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="98b99-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="98b99-112">Remarks</span></span>

<span data-ttu-id="98b99-113">Statik bir yöntem budur.</span><span class="sxs-lookup"><span data-stu-id="98b99-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="98b99-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="98b99-114">Requirements</span></span>

<span data-ttu-id="98b99-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="98b99-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="98b99-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="98b99-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="98b99-117">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="98b99-117">See also</span></span>

[<span data-ttu-id="98b99-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="98b99-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)