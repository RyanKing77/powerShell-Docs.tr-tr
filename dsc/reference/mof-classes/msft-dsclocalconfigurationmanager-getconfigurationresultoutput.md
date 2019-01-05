---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: MSFT_DSCLocalConfigurationManager sınıfının GetConfigurationResultOutput yöntemi
ms.openlocfilehash: ea572a4a66befd4e4b8d83e2957632b1b5ed7d93
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048651"
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="bc794-103">MSFT_DSCLocalConfigurationManager sınıfının GetConfigurationResultOutput yöntemi</span><span class="sxs-lookup"><span data-stu-id="bc794-103">GetConfigurationResultOutput method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="bc794-104">Belirli bir işi ile ilişkili yapılandırma aracı çıkış alır.</span><span class="sxs-lookup"><span data-stu-id="bc794-104">Gets the Configuration Agent output associated with a specific job.</span></span>

## <a name="syntax"></a><span data-ttu-id="bc794-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bc794-105">Syntax</span></span>

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

## <a name="parameters"></a><span data-ttu-id="bc794-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bc794-106">Parameters</span></span>

<span data-ttu-id="bc794-107">*JobId* \[içinde\] iş için çıktı verilerini almak için kimliği.</span><span class="sxs-lookup"><span data-stu-id="bc794-107">*jobId* \[in\] The ID of the job for which to get output data.</span></span>

<span data-ttu-id="bc794-108">*resumeOutputBookmark* \[içinde\] çıkış bir önceki yer işareti gelen bir devamlılık olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="bc794-108">*resumeOutputBookmark* \[in\] Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="bc794-109">*Çıkış* \[kullanıma\] belirtilen işin çıktısı.</span><span class="sxs-lookup"><span data-stu-id="bc794-109">*output* \[out\] The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="bc794-110">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="bc794-110">Return value</span></span>

<span data-ttu-id="bc794-111">Başarılıysa sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="bc794-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="bc794-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bc794-112">Remarks</span></span>

<span data-ttu-id="bc794-113">Statik bir yöntem budur.</span><span class="sxs-lookup"><span data-stu-id="bc794-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="bc794-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bc794-114">Requirements</span></span>

<span data-ttu-id="bc794-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="bc794-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="bc794-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="bc794-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="bc794-117">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="bc794-117">See also</span></span>

[<span data-ttu-id="bc794-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="bc794-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)