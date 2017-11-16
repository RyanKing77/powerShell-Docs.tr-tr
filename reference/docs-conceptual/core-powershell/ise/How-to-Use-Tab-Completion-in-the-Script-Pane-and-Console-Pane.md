---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: "Sekme tamamlama betik bölmesine ve konsol bölmesinde kullanma"
ms.assetid: 3b752c3c-0bd0-4eca-a2d3-2d5a37fd9d84
ms.openlocfilehash: ba8d0af7e7fc0f1df9f65116be899097b0a97a3c
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2017
---
# <a name="how-to-use-tab-completion-in-the-script-pane-and-console-pane"></a><span data-ttu-id="078bb-103">Sekme tamamlama betik bölmesine ve konsol bölmesinde kullanma</span><span class="sxs-lookup"><span data-stu-id="078bb-103">How to Use Tab Completion in the Script Pane and Console Pane</span></span>
<span data-ttu-id="078bb-104">Betik bölmesine ya da komut bölmesinde yazarken sekme tamamlama otomatik Yardım sağlar.</span><span class="sxs-lookup"><span data-stu-id="078bb-104">Tab completion provides automatic help when you are typing in the Script Pane or in the Command Pane.</span></span> <span data-ttu-id="078bb-105">Bu özelliğin avantajlarından yararlanmak için aşağıdaki adımları kullanın:</span><span class="sxs-lookup"><span data-stu-id="078bb-105">Use the following steps to take advantage of this feature:</span></span>

## <a name="to-automatically-complete-a-command-entry"></a><span data-ttu-id="078bb-106">Bir komut girişi otomatik olarak tamamlamak için</span><span class="sxs-lookup"><span data-stu-id="078bb-106">To automatically complete a command entry</span></span>
<span data-ttu-id="078bb-107">Komut bölmesinde veya komut dosyası bölmesi, birkaç karakterini bir komut yazın ve istenen tamamlama metni seçmek için SEKME tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="078bb-107">In the Command Pane or Script Pane, type a few characters of a command and then press TAB to select the desired completion text.</span></span> <span data-ttu-id="078bb-108">Birden çok öğe başlangıçta yazdığınız metni ile başlarsa, ardından istediğiniz öğeyi görünene kadar SEKME tuşuna basarak devam edin.</span><span class="sxs-lookup"><span data-stu-id="078bb-108">If multiple items begin with the text that you initially typed, then continue pressing Tab until the item you want appears.</span></span> <span data-ttu-id="078bb-109">Sekme tamamlama, bir cmdlet adı, parametre adı, değişken adı, nesne özellik adı veya bir dosya yolu yazarak ile yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="078bb-109">Tab completion can help with typing a cmdlet name, parameter name, variable name, object property name, or a file path.</span></span>

> [!NOTE]
> <span data-ttu-id="078bb-110">Yalnızca .ps1, .psd1 veya .psm1 dosyaları düzenlerken betik bölmesinde SEKME tuşuna basarak otomatik olarak bir komut işlemini tamamlar.</span><span class="sxs-lookup"><span data-stu-id="078bb-110">In the Script Pane, pressing TAB will automatically complete a command only when you are editing .ps1, .psd1, or .psm1 files.</span></span> <span data-ttu-id="078bb-111">Sekme tamamlama zaman komut bölmesinde yazarak dilediğiniz zaman çalışır.</span><span class="sxs-lookup"><span data-stu-id="078bb-111">Tab completion works any time when you are typing in the Command Pane.</span></span>

## <a name="to-automatically-complete-a-cmdlet-parameter-entry"></a><span data-ttu-id="078bb-112">Bir cmdlet parametresi girişi otomatik olarak tamamlamak için</span><span class="sxs-lookup"><span data-stu-id="078bb-112">To automatically complete a cmdlet parameter entry</span></span>
<span data-ttu-id="078bb-113">Komut bölmesi veya betik bölmesinde kısa çizgi ve ardından cmdlet'i yazın ve sonra SEKME tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="078bb-113">In the Command Pane or Script pane, type a cmdlet followed by a dash, and then press TAB.</span></span>

<span data-ttu-id="078bb-114">Örneğin, `Get-Process -` sekme her cmdlet parametrelerinin sırayla görüntülemek için birden çok kez basın.</span><span class="sxs-lookup"><span data-stu-id="078bb-114">For example, type `Get-Process -` and then press TAB multiple times to display each of the parameters for the cmdlet in turn.</span></span>

## <a name="see-also"></a><span data-ttu-id="078bb-115">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="078bb-115">See Also</span></span>
- [<span data-ttu-id="078bb-116">Windows PowerShell ISE kullanma</span><span class="sxs-lookup"><span data-stu-id="078bb-116">Using Windows PowerShell ISE</span></span>](using-the-windows-powershell-ise.md)
- [<span data-ttu-id="078bb-117">Bir PowerShell sekme oluşturma</span><span class="sxs-lookup"><span data-stu-id="078bb-117">How to Create a PowerShell Tab</span></span>](How-to-Create-a-PowerShell-Tab-in-Windows-PowerShell-ISE.md)

