---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: MSFT_DSCLocalConfigurationManager sınıfının GetConfigurationResultOutput yöntemi
ms.openlocfilehash: ea572a4a66befd4e4b8d83e2957632b1b5ed7d93
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078662"
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="7f60a-103">MSFT_DSCLocalConfigurationManager sınıfının GetConfigurationResultOutput yöntemi</span><span class="sxs-lookup"><span data-stu-id="7f60a-103">GetConfigurationResultOutput method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="7f60a-104">Belirli bir işi ile ilişkili yapılandırma aracı çıkış alır.</span><span class="sxs-lookup"><span data-stu-id="7f60a-104">Gets the Configuration Agent output associated with a specific job.</span></span>

## <a name="syntax"></a><span data-ttu-id="7f60a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7f60a-105">Syntax</span></span>

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

## <a name="parameters"></a><span data-ttu-id="7f60a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7f60a-106">Parameters</span></span>

<span data-ttu-id="7f60a-107">*JobId* \[içinde\] iş için çıktı verilerini almak için kimliği.</span><span class="sxs-lookup"><span data-stu-id="7f60a-107">*jobId* \[in\] The ID of the job for which to get output data.</span></span>

<span data-ttu-id="7f60a-108">*resumeOutputBookmark* \[içinde\] çıkış bir önceki yer işareti gelen bir devamlılık olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7f60a-108">*resumeOutputBookmark* \[in\] Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="7f60a-109">*Çıkış* \[kullanıma\] belirtilen işin çıktısı.</span><span class="sxs-lookup"><span data-stu-id="7f60a-109">*output* \[out\] The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="7f60a-110">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="7f60a-110">Return value</span></span>

<span data-ttu-id="7f60a-111">Başarılıysa sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="7f60a-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="7f60a-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7f60a-112">Remarks</span></span>

<span data-ttu-id="7f60a-113">Statik bir yöntem budur.</span><span class="sxs-lookup"><span data-stu-id="7f60a-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="7f60a-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7f60a-114">Requirements</span></span>

<span data-ttu-id="7f60a-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="7f60a-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="7f60a-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="7f60a-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="7f60a-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7f60a-117">See also</span></span>

[<span data-ttu-id="7f60a-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="7f60a-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)