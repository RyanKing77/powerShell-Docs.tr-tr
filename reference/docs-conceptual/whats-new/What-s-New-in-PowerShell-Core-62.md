---
title: PowerShell Core 6.2 yenilikler nelerdir?
description: Yeni özellikler ve PowerShell Core 6.2 yayımlanan değişiklikleri
ms.date: 03/28/2019
ms.openlocfilehash: 2224d23a244175059a705c07001e8ad8d6ab3aa0
ms.sourcegitcommit: 8dd4394cf867005a8b9ef0bb74b744c964fbc332
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/30/2019
ms.locfileid: "58750039"
---
# <a name="whats-new-in-powershell-core-62"></a><span data-ttu-id="e1382-103">PowerShell Core 6.2 yenilikler nelerdir?</span><span class="sxs-lookup"><span data-stu-id="e1382-103">What's New in PowerShell Core 6.2</span></span>

<span data-ttu-id="e1382-104">Seçimi önemli yeni özellikler ve PowerShell Core 6.2 ' sunulan değişiklikler bazıları aşağıdadır.</span><span class="sxs-lookup"><span data-stu-id="e1382-104">Below is a selection of some of the major new features and changes that have been introduced in PowerShell Core 6.2.</span></span>

<span data-ttu-id="e1382-105">Ayrıca **ton** boyunca "daha hızlı ve daha kararlı (Ayrıca, birçok ve çok sayıda hata düzeltmesi) PowerShell olun bence olarak"!</span><span class="sxs-lookup"><span data-stu-id="e1382-105">There's also **tons** of "boring stuff" that make PowerShell faster and more stable (plus lots and lots of bug fixes)!</span></span>
<span data-ttu-id="e1382-106">Değişikliklerin tam listesi için kullanıma sunduğumuz [github'da changelog](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).</span><span class="sxs-lookup"><span data-stu-id="e1382-106">For a full list of changes, check out our [changelog on GitHub](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).</span></span>

<span data-ttu-id="e1382-107">Ve bazı adları diyoruz sırasında kullandığınız için teşekkür ederiz [tüm topluluğa katkıda bulunanlar](https://github.com/PowerShell/PowerShell/graphs/contributors) yapılması bu sürümde mümkün.</span><span class="sxs-lookup"><span data-stu-id="e1382-107">And while we call out some names below, thank you to [all of the community contributors](https://github.com/PowerShell/PowerShell/graphs/contributors) that made this release possible.</span></span>

## <a name="engine-updates-and-fixes"></a><span data-ttu-id="e1382-108">Altyapı güncelleştirmeleri ve düzeltmeleri</span><span class="sxs-lookup"><span data-stu-id="e1382-108">Engine Updates and Fixes</span></span>

- <span data-ttu-id="e1382-109">PowerShell uzaktan iletişimini etkinleştirme/devre dışı cmdlet'i uyarı iletilerini ekleyin ([#9203][])</span><span class="sxs-lookup"><span data-stu-id="e1382-109">Add PowerShell remoting enable/disable cmdlet warning messages ([#9203][])</span></span>
- <span data-ttu-id="e1382-110">Düzeltme `FormatTable` uzak seri durumundan çıkarma regresyon ([#9116][])</span><span class="sxs-lookup"><span data-stu-id="e1382-110">Fix for `FormatTable` remote deserialization regression ([#9116][])</span></span>
- <span data-ttu-id="e1382-111">Görev-tabanlı güncelleştirme `async` API'lerini doğrudan bir görev nesnesi döndürmek için PowerShell eklendi ([#9079][])</span><span class="sxs-lookup"><span data-stu-id="e1382-111">Update the task-based `async` APIs added to PowerShell to return a Task object directly ([#9079][])</span></span>
- <span data-ttu-id="e1382-112">5 ekleyin `InvokeAsync` aşırı yüklemeler ve `StopAsync` için `PowerShell` türü ([#8056][]) (teşekkürler @KirkMunro!)</span><span class="sxs-lookup"><span data-stu-id="e1382-112">Add 5 `InvokeAsync` overloads and `StopAsync` to the `PowerShell` type ([#8056][]) (Thanks @KirkMunro!)</span></span>

## <a name="general-cmdlet-updates-and-fixes"></a><span data-ttu-id="e1382-113">Genel Cmdlet güncelleştirmeleri ve düzeltmeleri</span><span class="sxs-lookup"><span data-stu-id="e1382-113">General Cmdlet Updates and Fixes</span></span>

- <span data-ttu-id="e1382-114">Etkinleştirme `SecureString` cmdlet'leri için Windows olmayan düz metin depolayarak ([#9199][])</span><span class="sxs-lookup"><span data-stu-id="e1382-114">Enable `SecureString` cmdlets for non-Windows by storing the plain text ([#9199][])</span></span>
- <span data-ttu-id="e1382-115">Geçersiz ileti Ekle `Send-MailMessage` ([#9178][])</span><span class="sxs-lookup"><span data-stu-id="e1382-115">Add Obsolete message to `Send-MailMessage` ([#9178][])</span></span>
- <span data-ttu-id="e1382-116">Düzeltme `Restart-Computer` üzerinde çalışılacak `localhost` WinRM olmadığında mevcut ([#9160][])</span><span class="sxs-lookup"><span data-stu-id="e1382-116">Fix `Restart-Computer` to work on `localhost` when WinRM is not present ([#9160][])</span></span>
- <span data-ttu-id="e1382-117">Olun `Start-Job` PowerShell barındırıldığında sonlandırma hatası throw ([#9128][])</span><span class="sxs-lookup"><span data-stu-id="e1382-117">Make `Start-Job` throw terminating error when PowerShell is being hosted ([#9128][])</span></span>
- <span data-ttu-id="e1382-118">İçin güncelleştirme sürüm `PowerShell.Native` ve testleri barındırma ([#8983][])</span><span class="sxs-lookup"><span data-stu-id="e1382-118">Update version for `PowerShell.Native` and hosting tests ([#8983][])</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="e1382-119">Hataya Neden Olan Değişiklikler</span><span class="sxs-lookup"><span data-stu-id="e1382-119">Breaking Changes</span></span>

<span data-ttu-id="e1382-120">Windows PowerShell ile tutarlı olmasını Write-Output içinde - NoEnumerate davranışı düzeltmek ([#9069][]) (teşekkürler @vexx32!)</span><span class="sxs-lookup"><span data-stu-id="e1382-120">Fix -NoEnumerate behavior in Write-Output to be consistent with Windows PowerShell ([#9069][]) (Thanks @vexx32!)</span></span>

<!-- Link references -->
[#8056]: https://github.com/PowerShell/PowerShell/pull/8056
[#8983]: https://github.com/PowerShell/PowerShell/pull/8983
[#9069]: https://github.com/PowerShell/PowerShell/pull/9069
[#9079]: https://github.com/PowerShell/PowerShell/pull/9079
[#9116]: https://github.com/PowerShell/PowerShell/pull/9116
[#9128]: https://github.com/PowerShell/PowerShell/pull/9128
[#9160]: https://github.com/PowerShell/PowerShell/pull/9160
[#9178]: https://github.com/PowerShell/PowerShell/pull/9178
[#9199]: https://github.com/PowerShell/PowerShell/pull/9199
[#9203]: https://github.com/PowerShell/PowerShell/pull/9203
