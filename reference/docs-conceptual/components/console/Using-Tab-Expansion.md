---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Sekme Genişletmeyi Kullanma
ms.openlocfilehash: d96cbf848f464aff29a7bed9b70d0b6a000aa808
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67031015"
---
# <a name="using-tab-expansion"></a><span data-ttu-id="0ff13-103">Sekme Genişletmeyi Kullanma</span><span class="sxs-lookup"><span data-stu-id="0ff13-103">Using Tab Expansion</span></span>

<span data-ttu-id="0ff13-104">Komut satırı Kabuk komut girişini hızlandırmak ve ipuçları sağlayan genellikle uzun dosyalarını veya komutları adlarını otomatik olarak tamamlamak için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="0ff13-104">Command-line shells often provide a way to complete the names of long files or commands automatically, speeding up command entry and providing hints.</span></span> <span data-ttu-id="0ff13-105">PowerShell sayesinde dosya adları ve cmdlet adları tuşlarına basarak doldurun <kbd>sekmesini</kbd> anahtarı.</span><span class="sxs-lookup"><span data-stu-id="0ff13-105">PowerShell allows you to fill in file names and cmdlet names by pressing the <kbd>Tab</kbd> key.</span></span>

> [!NOTE]
> <span data-ttu-id="0ff13-106">Sekme genişletmeyi iç işlev TabExpansion veya TabExpansion2 tarafından denetlenir.</span><span class="sxs-lookup"><span data-stu-id="0ff13-106">Tab expansion is controlled by the internal function TabExpansion or TabExpansion2.</span></span> <span data-ttu-id="0ff13-107">Bu işlev değiştirilmiş veya geçersiz olduğundan, bu tartışma için varsayılan PowerShell yapılandırması davranışını kılavuzudur.</span><span class="sxs-lookup"><span data-stu-id="0ff13-107">Since this function can be modified or overridden, this discussion is a guide to the behavior of the default PowerShell configuration.</span></span>

<span data-ttu-id="0ff13-108">Bir dosya adı veya yolu kullanılabilir seçeneklerden otomatik doldurma, tuşuna basın ve ad bölümünü yazın <kbd>sekmesini</kbd> anahtarı.</span><span class="sxs-lookup"><span data-stu-id="0ff13-108">To fill in a filename or path from the available choices automatically, type part of the name and press the <kbd>Tab</kbd> key.</span></span> <span data-ttu-id="0ff13-109">PowerShell, bulduğu ilk eşleşmeyi adı otomatik olarak genişletilecektir.</span><span class="sxs-lookup"><span data-stu-id="0ff13-109">PowerShell will automatically expand the name to the first match that it finds.</span></span> <span data-ttu-id="0ff13-110">Tuşuna basarak <kbd>sekmesini</kbd> anahtar art arda geçiş tüm kullanılabilir seçenekleri.</span><span class="sxs-lookup"><span data-stu-id="0ff13-110">Pressing the <kbd>Tab</kbd> key repeatedly will cycle through all of the available choices.</span></span>

<span data-ttu-id="0ff13-111">Sekme genişletmeyi cmdlet adları, biraz farklıdır.</span><span class="sxs-lookup"><span data-stu-id="0ff13-111">The tab expansion of cmdlet names is slightly different.</span></span> <span data-ttu-id="0ff13-112">Sekme genişletmeyi bir cmdlet adı kullanmak için ' % s'adı (Fiili) ve izleyen tire tüm ilk bölümünü yazın.</span><span class="sxs-lookup"><span data-stu-id="0ff13-112">To use tab expansion on a cmdlet name, type the entire first part of the name (the verb) and the hyphen that follows it.</span></span> <span data-ttu-id="0ff13-113">Daha fazla kısmi bir eşleşme için bir ad doldurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ff13-113">You can fill in more of the name for a partial match.</span></span> <span data-ttu-id="0ff13-114">Örneğin, `get-co` ve tuşuna <kbd>sekmesini</kbd> anahtar, PowerShell otomatik olarak bu genişleyecek `Get-Command` cmdlet (, ayrıca standart formlarına büyük/küçük harf değiştiğine dikkat edin).</span><span class="sxs-lookup"><span data-stu-id="0ff13-114">For example, if you type `get-co` and then press the <kbd>Tab</kbd> key, PowerShell will automatically expand this to the `Get-Command` cmdlet (notice that it also changes the case of letters to their standard form).</span></span> <span data-ttu-id="0ff13-115">Basarsanız <kbd>sekmesini</kbd> anahtar yeniden PowerShell Bu yalnızca diğer eşleşen cmdlet'i adla değiştirir `Get-Content`.</span><span class="sxs-lookup"><span data-stu-id="0ff13-115">If you press <kbd>Tab</kbd> key again, PowerShell replaces this with the only other matching cmdlet name, `Get-Content`.</span></span>

<span data-ttu-id="0ff13-116">Sekme genişletmeyi aynı satırda tekrar tekrar kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ff13-116">You can use tab expansion repeatedly on the same line.</span></span> <span data-ttu-id="0ff13-117">Sekme genişletmeyi adına gibi kullanabileceğiniz `Get-Content` cmdlet'ini girerek:</span><span class="sxs-lookup"><span data-stu-id="0ff13-117">For example, you can use tab expansion on the name of the `Get-Content` cmdlet by entering:</span></span>

```
PS> Get-Con<Tab>
```

<span data-ttu-id="0ff13-118">Bastığınızda <kbd>sekmesini</kbd> anahtar, komut genişletir:</span><span class="sxs-lookup"><span data-stu-id="0ff13-118">When you press the <kbd>Tab</kbd> key, the command expands to:</span></span>

```
PS> Get-Content
```

<span data-ttu-id="0ff13-119">Sonra kısmen Active Kurulum günlük dosyası yolunu belirtin ve yeniden sekme genişletmeyi kullanma:</span><span class="sxs-lookup"><span data-stu-id="0ff13-119">You can then partially specify the path to the Active Setup log file and use tab expansion again:</span></span>

```
PS> Get-Content c:\windows\acts<Tab>
```

<span data-ttu-id="0ff13-120">Bastığınızda <kbd>sekmesini</kbd> anahtar, komut genişletir:</span><span class="sxs-lookup"><span data-stu-id="0ff13-120">When you press the <kbd>Tab</kbd> key, the command expands to:</span></span>

```
PS> Get-Content C:\windows\actsetup.log
```

> [!NOTE]
> <span data-ttu-id="0ff13-121">Bir sekme genişletme işlemi sekmelerin her zaman bir sözcük tamamlama girişiminde yorumlanır sınırlamasıdır.</span><span class="sxs-lookup"><span data-stu-id="0ff13-121">One limitation of the tab expansion process is that tabs are always interpreted as attempts to complete a word.</span></span> <span data-ttu-id="0ff13-122">Bir PowerShell konsolunda komut örnekleri kopyalayıp, örnek sekmeleri içermediğinden emin emin olun; aşması durumunda sonuçları tahmin edilemez ve istediğiniz neredeyse kesindir olmayacak.</span><span class="sxs-lookup"><span data-stu-id="0ff13-122">If you copy and paste command examples into a PowerShell console, make sure that the sample does not contain tabs; if it does, the results will be unpredictable and will almost certainly not be what you intended.</span></span>
