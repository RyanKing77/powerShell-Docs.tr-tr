---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: WMF 5.1 PowerShell altyapısı iyileştirmeleri
ms.openlocfilehash: 738f72b910de7d44f48309013237d523d0dd40a4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687450"
---
# <a name="powershell-engine-improvements"></a><span data-ttu-id="26d91-103">PowerShell altyapısı iyileştirmeleri</span><span class="sxs-lookup"><span data-stu-id="26d91-103">PowerShell Engine Improvements</span></span>

<span data-ttu-id="26d91-104">WMF 5.1 aşağıdaki çekirdek PowerShell altyapısı iyileştirmeleri uygulanmıştır:</span><span class="sxs-lookup"><span data-stu-id="26d91-104">The following improvements to the core PowerShell engine have been implemented in WMF 5.1:</span></span>

## <a name="performance"></a><span data-ttu-id="26d91-105">Performans</span><span class="sxs-lookup"><span data-stu-id="26d91-105">Performance</span></span>

<span data-ttu-id="26d91-106">Bazı önemli alanda performans geliştirilmiştir:</span><span class="sxs-lookup"><span data-stu-id="26d91-106">Performance has improved in some important areas:</span></span>

- <span data-ttu-id="26d91-107">Başlatma</span><span class="sxs-lookup"><span data-stu-id="26d91-107">Startup</span></span>
- <span data-ttu-id="26d91-108">Gibi cmdlet'leri için ardışık düzen `ForEach-Object` ve `Where-Object` yaklaşık % 50 daha hızlıdır</span><span class="sxs-lookup"><span data-stu-id="26d91-108">Pipelining to cmdlets like `ForEach-Object` and `Where-Object` is approximately 50% faster</span></span>

<span data-ttu-id="26d91-109">Bazı örnek iyileştirmeleri (sonuçlarınızı donanımınıza bağlı olarak farklılık gösterebilir):</span><span class="sxs-lookup"><span data-stu-id="26d91-109">Some example improvements (your results may vary depending on your hardware):</span></span>

| <span data-ttu-id="26d91-110">Senaryo</span><span class="sxs-lookup"><span data-stu-id="26d91-110">Scenario</span></span> | <span data-ttu-id="26d91-111">5.0 süresi (ms)</span><span class="sxs-lookup"><span data-stu-id="26d91-111">5.0 Time (ms)</span></span> | <span data-ttu-id="26d91-112">5.1 süresi (ms)</span><span class="sxs-lookup"><span data-stu-id="26d91-112">5.1 Time (ms)</span></span> |
| -------- | :---------------: | :---------------: |
| `powershell -command "echo 1"` | <span data-ttu-id="26d91-113">900</span><span class="sxs-lookup"><span data-stu-id="26d91-113">900</span></span> | <span data-ttu-id="26d91-114">250</span><span class="sxs-lookup"><span data-stu-id="26d91-114">250</span></span> |
| <span data-ttu-id="26d91-115">PowerShell'i çalıştırmak ilk hiç olmadığı kadar: `powershell -command "Unknown-Command"`</span><span class="sxs-lookup"><span data-stu-id="26d91-115">First ever PowerShell run: `powershell -command "Unknown-Command"`</span></span> | <span data-ttu-id="26d91-116">30000</span><span class="sxs-lookup"><span data-stu-id="26d91-116">30000</span></span> | <span data-ttu-id="26d91-117">13000</span><span class="sxs-lookup"><span data-stu-id="26d91-117">13000</span></span> |
| <span data-ttu-id="26d91-118">Yerleşik komut analiz önbellek: `powershell -command "Unknown-Command"`</span><span class="sxs-lookup"><span data-stu-id="26d91-118">Command analysis cache built: `powershell -command "Unknown-Command"`</span></span> | <span data-ttu-id="26d91-119">7000</span><span class="sxs-lookup"><span data-stu-id="26d91-119">7000</span></span> | <span data-ttu-id="26d91-120">520</span><span class="sxs-lookup"><span data-stu-id="26d91-120">520</span></span> |
| <code>1..1000000 &#124; % { }</code> | <span data-ttu-id="26d91-121">1400</span><span class="sxs-lookup"><span data-stu-id="26d91-121">1400</span></span> | <span data-ttu-id="26d91-122">750</span><span class="sxs-lookup"><span data-stu-id="26d91-122">750</span></span> |

> [!Note]
> <span data-ttu-id="26d91-123">Desteklenmeyen bazı senaryolar için başlatma ilgili bir değişiklik etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="26d91-123">One change related to startup might impact some unsupported scenarios.</span></span>
> <span data-ttu-id="26d91-124">PowerShell artık, dosyaları okur `$pshome\*.ps1xml` --bu dosyaları bazı dosya önlemek için C# için olarak dönüştürüldü ve XML işlem yükünü CPU dosyaları.</span><span class="sxs-lookup"><span data-stu-id="26d91-124">PowerShell no longer reads the files `$pshome\*.ps1xml` -- these files have been converted to C# to avoid some file and CPU overhead of processing the XML files.</span></span>
> <span data-ttu-id="26d91-125">Dosya içeriğini değiştirirseniz V5, yalnızca V2 için herhangi bir etkisi olmaz şekilde dosyaları yan yana V2 desteklemek için hala mevcut.</span><span class="sxs-lookup"><span data-stu-id="26d91-125">The files still exist to support V2 side-by-side, so if you change the file contents, it will not have any effect to V5, only V2.</span></span>
> <span data-ttu-id="26d91-126">Bu dosyaların içeriğini değiştirme, desteklenen bir senaryo asla olup olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="26d91-126">Note that changing the contents of these files was never a supported scenario.</span></span>

<span data-ttu-id="26d91-127">Başka bir görünür bir değişiklik, dışarı aktarılan komutlar ve diğer bilgileri sistemde yüklü modüller için PowerShell'i nasıl önbelleğe aldığını ' dir.</span><span class="sxs-lookup"><span data-stu-id="26d91-127">Another visible change is how PowerShell caches the exported commands and other information for modules that are installed on a system.</span></span>
<span data-ttu-id="26d91-128">Daha önce bu önbellek dizinde depolanan `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis`.</span><span class="sxs-lookup"><span data-stu-id="26d91-128">Previously, this cache was stored in the directory `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis`.</span></span>
<span data-ttu-id="26d91-129">WMF 5.1, tek bir dosyayı bir önbellektir `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span><span class="sxs-lookup"><span data-stu-id="26d91-129">In WMF 5.1, the cache is a single file `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span></span>
<span data-ttu-id="26d91-130">Bkz: [modül çözümleme önbellek](scenarios-features.md#module-analysis-cache) daha fazla ayrıntı için.</span><span class="sxs-lookup"><span data-stu-id="26d91-130">See [Module Analysis Cache](scenarios-features.md#module-analysis-cache) for more details.</span></span>