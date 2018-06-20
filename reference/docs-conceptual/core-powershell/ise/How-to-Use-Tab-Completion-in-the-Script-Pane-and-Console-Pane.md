---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Betik Bölmesi ve Konsol Bölmesinde Sekme Tamamlamayı Kullanma
ms.assetid: 3b752c3c-0bd0-4eca-a2d3-2d5a37fd9d84
ms.openlocfilehash: e1f8146b6113a82fd3d857c98550ec2e459715a4
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30954934"
---
# <a name="how-to-use-tab-completion-in-the-script-pane-and-console-pane"></a><span data-ttu-id="423ca-103">Betik Bölmesi ve Konsol Bölmesinde Sekme Tamamlamayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="423ca-103">How to Use Tab Completion in the Script Pane and Console Pane</span></span>

<span data-ttu-id="423ca-104">Betik bölmesine ya da komut bölmesinde yazarken sekme tamamlama otomatik Yardım sağlar.</span><span class="sxs-lookup"><span data-stu-id="423ca-104">Tab completion provides automatic help when you are typing in the Script Pane or in the Command Pane.</span></span> <span data-ttu-id="423ca-105">Bu özelliğin avantajlarından yararlanmak için aşağıdaki adımları kullanın:</span><span class="sxs-lookup"><span data-stu-id="423ca-105">Use the following steps to take advantage of this feature:</span></span>

## <a name="to-automatically-complete-a-command-entry"></a><span data-ttu-id="423ca-106">Bir komut girişi otomatik olarak tamamlamak için</span><span class="sxs-lookup"><span data-stu-id="423ca-106">To automatically complete a command entry</span></span>

<span data-ttu-id="423ca-107">Komut bölmesinde veya komut dosyası bölmesi, birkaç karakterini bir komut yazın ve istenen tamamlama metni seçmek için SEKME tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="423ca-107">In the Command Pane or Script Pane, type a few characters of a command and then press TAB to select the desired completion text.</span></span> <span data-ttu-id="423ca-108">Birden çok öğe başlangıçta yazdığınız metni ile başlarsa, ardından istediğiniz öğeyi görünene kadar SEKME tuşuna basarak devam edin.</span><span class="sxs-lookup"><span data-stu-id="423ca-108">If multiple items begin with the text that you initially typed, then continue pressing Tab until the item you want appears.</span></span> <span data-ttu-id="423ca-109">Sekme tamamlama, bir cmdlet adı, parametre adı, değişken adı, nesne özellik adı veya bir dosya yolu yazarak ile yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="423ca-109">Tab completion can help with typing a cmdlet name, parameter name, variable name, object property name, or a file path.</span></span>

> [!NOTE]
> <span data-ttu-id="423ca-110">Yalnızca .ps1, .psd1 veya .psm1 dosyaları düzenlerken betik bölmesinde SEKME tuşuna basarak otomatik olarak bir komut işlemini tamamlar.</span><span class="sxs-lookup"><span data-stu-id="423ca-110">In the Script Pane, pressing TAB will automatically complete a command only when you are editing .ps1, .psd1, or .psm1 files.</span></span> <span data-ttu-id="423ca-111">Sekme tamamlama zaman komut bölmesinde yazarak dilediğiniz zaman çalışır.</span><span class="sxs-lookup"><span data-stu-id="423ca-111">Tab completion works any time when you are typing in the Command Pane.</span></span>

## <a name="to-automatically-complete-a-cmdlet-parameter-entry"></a><span data-ttu-id="423ca-112">Bir cmdlet parametresi girişi otomatik olarak tamamlamak için</span><span class="sxs-lookup"><span data-stu-id="423ca-112">To automatically complete a cmdlet parameter entry</span></span>

<span data-ttu-id="423ca-113">Komut bölmesi veya betik bölmesinde kısa çizgi ve ardından cmdlet'i yazın ve sonra SEKME tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="423ca-113">In the Command Pane or Script pane, type a cmdlet followed by a dash, and then press TAB.</span></span>

<span data-ttu-id="423ca-114">Örneğin, `Get-Process -` sekme her cmdlet parametrelerinin sırayla görüntülemek için birden çok kez basın.</span><span class="sxs-lookup"><span data-stu-id="423ca-114">For example, type `Get-Process -` and then press TAB multiple times to display each of the parameters for the cmdlet in turn.</span></span>

## <a name="see-also"></a><span data-ttu-id="423ca-115">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="423ca-115">See Also</span></span>

- [<span data-ttu-id="423ca-116">Windows PowerShell ISE Tanıtımı</span><span class="sxs-lookup"><span data-stu-id="423ca-116">Introducing the Windows PowerShell ISE</span></span>](Introducing-the-Windows-PowerShell-ISE.md)
- [<span data-ttu-id="423ca-117">Bir PowerShell sekme oluşturma</span><span class="sxs-lookup"><span data-stu-id="423ca-117">How to Create a PowerShell Tab</span></span>](How-to-Create-a-PowerShell-Tab-in-Windows-PowerShell-ISE.md)