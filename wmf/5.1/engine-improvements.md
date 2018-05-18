---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: WMF 5.1 PowerShell altyapısı yenilikleri
ms.openlocfilehash: 98095904157a675bbe84616b1d9cbb22689cd059
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
---
#<a name="powershell-engine-improvements"></a><span data-ttu-id="13600-103">PowerShell altyapısı geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="13600-103">PowerShell Engine Improvements</span></span>

<span data-ttu-id="13600-104">WMF 5.1, çekirdek PowerShell altyapısı aşağıdaki iyileştirmeleri uygulanmıştır:</span><span class="sxs-lookup"><span data-stu-id="13600-104">The following improvements to the core PowerShell engine have been implemented in WMF 5.1:</span></span>


## <a name="performance"></a><span data-ttu-id="13600-105">Performans</span><span class="sxs-lookup"><span data-stu-id="13600-105">Performance</span></span> ##

<span data-ttu-id="13600-106">Performans bazı önemli alanlarında geliştirilmiştir:</span><span class="sxs-lookup"><span data-stu-id="13600-106">Performance has improved in some important areas:</span></span>

- <span data-ttu-id="13600-107">Başlatma</span><span class="sxs-lookup"><span data-stu-id="13600-107">Startup</span></span>
- <span data-ttu-id="13600-108">ForEach-Object ve Where-Object gibi cmdlet öğelerini ardışık düzen yaklaşık % 50 daha hızlı'dir</span><span class="sxs-lookup"><span data-stu-id="13600-108">Pipelining to cmdlets like ForEach-Object and Where-Object is approximately 50% faster</span></span>

<span data-ttu-id="13600-109">Bazı örnek iyileştirmeleri (sonuçlarınızı donanımınıza bağlı olarak değişebilir):</span><span class="sxs-lookup"><span data-stu-id="13600-109">Some example improvements (your results may vary depending on your hardware):</span></span>

| <span data-ttu-id="13600-110">Senaryo</span><span class="sxs-lookup"><span data-stu-id="13600-110">Scenario</span></span> | <span data-ttu-id="13600-111">5.0 süresi (ms)</span><span class="sxs-lookup"><span data-stu-id="13600-111">5.0 Time (ms)</span></span> | <span data-ttu-id="13600-112">5.1 süresi (ms)</span><span class="sxs-lookup"><span data-stu-id="13600-112">5.1 Time (ms)</span></span> |
| -------- | :---------------: | :---------------: |
| `powershell -command "echo 1"` | <span data-ttu-id="13600-113">900</span><span class="sxs-lookup"><span data-stu-id="13600-113">900</span></span> | <span data-ttu-id="13600-114">250</span><span class="sxs-lookup"><span data-stu-id="13600-114">250</span></span> |
| <span data-ttu-id="13600-115">PowerShell çalıştırma ilk hiç: `powershell -command "Unknown-Command"`</span><span class="sxs-lookup"><span data-stu-id="13600-115">First ever PowerShell run: `powershell -command "Unknown-Command"`</span></span> | <span data-ttu-id="13600-116">30000</span><span class="sxs-lookup"><span data-stu-id="13600-116">30000</span></span> | <span data-ttu-id="13600-117">13000</span><span class="sxs-lookup"><span data-stu-id="13600-117">13000</span></span> |
| <span data-ttu-id="13600-118">Yerleşik komutu analiz önbellek: `powershell -command "Unknown-Command"`</span><span class="sxs-lookup"><span data-stu-id="13600-118">Command analysis cache built: `powershell -command "Unknown-Command"`</span></span> | <span data-ttu-id="13600-119">7000</span><span class="sxs-lookup"><span data-stu-id="13600-119">7000</span></span> | <span data-ttu-id="13600-120">520</span><span class="sxs-lookup"><span data-stu-id="13600-120">520</span></span> |
| <code>1..1000000 &#124; % { }</code> | <span data-ttu-id="13600-121">1400</span><span class="sxs-lookup"><span data-stu-id="13600-121">1400</span></span> | <span data-ttu-id="13600-122">750</span><span class="sxs-lookup"><span data-stu-id="13600-122">750</span></span> |

> <span data-ttu-id="13600-123">Bir değişiklik için başlatma ilgili bazı etkileyebilecek Not senaryoları desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="13600-123">Note One change related to startup might impact some unsupported scenarios.</span></span>
> <span data-ttu-id="13600-124">PowerShell artık dosyaları okur `$pshome\*.ps1xml` --bu dosyaları bazı dosya önlemek için C# için olarak dönüştürülen ve XML işlem yükünü CPU dosyaları.</span><span class="sxs-lookup"><span data-stu-id="13600-124">PowerShell no longer reads the files `$pshome\*.ps1xml` -- these files have been converted to C# to avoid some file and CPU overhead of processing the XML files.</span></span>
<span data-ttu-id="13600-125">Dosya içeriğini değiştirirseniz, bu V5, yalnızca V2 için herhangi bir etkisi kalmaması dosyaları yan yana destek V2 hala mevcut.</span><span class="sxs-lookup"><span data-stu-id="13600-125">The files still exist to support V2 side-by-side, so if you change the file contents, it will not have any effect to V5, only V2.</span></span>
<span data-ttu-id="13600-126">Bu dosyaların içeriğini değiştirme, desteklenen bir senaryo asla olup olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="13600-126">Note that changing the contents of these files was never a supported scenario.</span></span>

<span data-ttu-id="13600-127">Başka bir görünür PowerShell dışarı aktarılan komutlar ve diğer bilgileri bir sistemde yüklü modülleri için nasıl önbelleğe alınacağını değişikliktir.</span><span class="sxs-lookup"><span data-stu-id="13600-127">Another visible change is how PowerShell caches the exported commands and other information for modules that are installed on a system.</span></span>
<span data-ttu-id="13600-128">Bu önbellek dizinde depolanan daha önce `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis`.</span><span class="sxs-lookup"><span data-stu-id="13600-128">Previously, this cache was stored in the directory `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis`.</span></span>
<span data-ttu-id="13600-129">WMF 5.1, tek bir dosya önbelleğidir `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span><span class="sxs-lookup"><span data-stu-id="13600-129">In WMF 5.1, the cache is a single file `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span></span>
<span data-ttu-id="13600-130">Bkz: [modülü analiz önbellek](scenarios-features.md#module-analysis-cache) daha fazla ayrıntı için.</span><span class="sxs-lookup"><span data-stu-id="13600-130">See [Module Analysis Cache](scenarios-features.md#module-analysis-cache) for more details.</span></span>
