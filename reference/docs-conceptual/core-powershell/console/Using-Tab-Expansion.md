---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Sekme Genişletmeyi Kullanma
ms.assetid: c8730471-bf6a-43b8-ab1d-f9ef5a74f04e
ms.openlocfilehash: 3d047bf0691c8a304d7637aa50fba6ae99709a82
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="using-tab-expansion"></a><span data-ttu-id="a3305-103">Sekme Genişletmeyi Kullanma</span><span class="sxs-lookup"><span data-stu-id="a3305-103">Using Tab Expansion</span></span>

<span data-ttu-id="a3305-104">Komut satırı Kabukları komut girişini hızlandırmak ve sağlama genellikle uzun dosyalarını veya komutları adlarını otomatik olarak tamamlamak için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="a3305-104">Command-line shells often provide a way to complete the names of long files or commands automatically, speeding up command entry and providing .</span></span> <span data-ttu-id="a3305-105">Windows PowerShell tuşlarına basarak dosya adlarını ve cmdlet adları doldurmanıza olanak sağlar **sekmesini** anahtarı.</span><span class="sxs-lookup"><span data-stu-id="a3305-105">Windows PowerShell allows you to fill in file names and cmdlet names by pressing the **Tab** key.</span></span>

> [!NOTE]
> <span data-ttu-id="a3305-106">Sekme genişletme iç işlev TabExpansion veya TabExpansion2 tarafından denetlenir.</span><span class="sxs-lookup"><span data-stu-id="a3305-106">Tab expansion is controlled by the internal function TabExpansion or TabExpansion2.</span></span> <span data-ttu-id="a3305-107">Bu işlev değiştirilmiş veya geçersiz olduğundan, bu tartışma varsayılan PowerShell yapılandırması davranışını Kılavuzu kalır.</span><span class="sxs-lookup"><span data-stu-id="a3305-107">Since this function can be modified or overridden, this discussion is a guide to the behavior of the default PowerShell configuration.</span></span>

<span data-ttu-id="a3305-108">Bir dosya adı veya yolu kullanılabilir seçeneklerden otomatik olarak doldurun, kısmını basın ve adını yazın **sekmesini** anahtarı.</span><span class="sxs-lookup"><span data-stu-id="a3305-108">To fill in a filename or path from the available choices automatically, type part of the name and press the **Tab** key.</span></span> <span data-ttu-id="a3305-109">PowerShell, bulduğu ilk eşleşmeye adı otomatik olarak genişletilir.</span><span class="sxs-lookup"><span data-stu-id="a3305-109">PowerShell will automatically expand the name to the first match that it finds.</span></span> <span data-ttu-id="a3305-110">Tuşuna basarak **sekmesini** anahtar art arda geçiş tüm kullanılabilir seçenekleri.</span><span class="sxs-lookup"><span data-stu-id="a3305-110">Pressing the **Tab** key repeatedly will cycle through all of the available choices.</span></span>

<span data-ttu-id="a3305-111">Cmdlet adları sekmesini genişlemesi biraz farklıdır.</span><span class="sxs-lookup"><span data-stu-id="a3305-111">The tab expansion of cmdlet names is slightly different.</span></span> <span data-ttu-id="a3305-112">Bir cmdlet adı sekmesini genişletme kullanmak için (fiil) adı ve izleyen tire tüm ilk bölümünü yazın.</span><span class="sxs-lookup"><span data-stu-id="a3305-112">To use tab expansion on a cmdlet name, type the entire first part of the name (the verb) and the hyphen that follows it.</span></span> <span data-ttu-id="a3305-113">Daha fazla kısmi eşleşme için ad doldurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a3305-113">You can fill in more of the name for a partial match.</span></span> <span data-ttu-id="a3305-114">Örneğin, **get-co** ve tuşuna basın **sekmesini** anahtar, PowerShell otomatik olarak bu genişletecek **Get-Command** cmdlet (bildirim, ayrıca durum değiştirir harfini standart formlarına).</span><span class="sxs-lookup"><span data-stu-id="a3305-114">For example, if you type **get-co** and then press the **Tab** key, PowerShell will automatically expand this to the **Get-Command** cmdlet (notice that it also changes the case of letters to their standard form).</span></span> <span data-ttu-id="a3305-115">Basarsanız **sekmesini** anahtar yeniden PowerShell Bu yalnızca diğer eşleşen cmdlet adla değiştirir **Get-Content**.</span><span class="sxs-lookup"><span data-stu-id="a3305-115">If you press **Tab** key again, PowerShell replaces this with the only other matching cmdlet name, **Get-Content**.</span></span>

<span data-ttu-id="a3305-116">Sekme genişletme aynı çizgi üzerinde tekrar tekrar kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a3305-116">You can use tab expansion repeatedly on the same line.</span></span> <span data-ttu-id="a3305-117">Örneğin, adına sekmesini genişletme kullanabilirsiniz **Get-Content** girerek cmdlet:</span><span class="sxs-lookup"><span data-stu-id="a3305-117">For example, you can use tab expansion on the name of the **Get-Content** cmdlet by entering:</span></span>

```
PS> Get-Con<Tab>
```

<span data-ttu-id="a3305-118">Bastığınızda **sekmesini** için anahtar, komut genişletir:</span><span class="sxs-lookup"><span data-stu-id="a3305-118">When you press the **Tab** key, the command expands to:</span></span>

```
PS> Get-Content
```

<span data-ttu-id="a3305-119">Daha sonra kısmen Active Kurulum günlük dosyası yolunu belirtin ve yeniden sekmesini genişletme kullanın:</span><span class="sxs-lookup"><span data-stu-id="a3305-119">You can then partially specify the path to the Active Setup log file and use tab expansion again:</span></span>

```
PS> Get-Content c:\windows\acts<Tab>
```

<span data-ttu-id="a3305-120">Bastığınızda **sekmesini** için anahtar, komut genişletir:</span><span class="sxs-lookup"><span data-stu-id="a3305-120">When you press the **Tab** key, the command expands to:</span></span>

```
PS> Get-Content C:\windows\actsetup.log
```

> [!NOTE]
> <span data-ttu-id="a3305-121">Bir sekme genişletme işlemi sekmelerin her zaman tam bir sözcük girişimleri yorumlanır kısıtlamasıdır.</span><span class="sxs-lookup"><span data-stu-id="a3305-121">One limitation of the tab expansion process is that tabs are always interpreted as attempts to complete a word.</span></span> <span data-ttu-id="a3305-122">Bir PowerShell konsolunda komut örnekleri kopyalayıp, örnek sekmeleri içermiyor emin olun; varsa, sonuçlar öngörülemez olacaktır ve istediğiniz neredeyse kesinlikle olmaz.</span><span class="sxs-lookup"><span data-stu-id="a3305-122">If you copy and paste command examples into a PowerShell console, make sure that the sample does not contain tabs; if it does, the results will be unpredictable and will almost certainly not be what you intended.</span></span>