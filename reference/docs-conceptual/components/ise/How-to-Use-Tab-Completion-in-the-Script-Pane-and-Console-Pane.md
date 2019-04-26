---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Betik Bölmesi ve Konsol Bölmesinde Sekme Tamamlamayı Kullanma
ms.assetid: 3b752c3c-0bd0-4eca-a2d3-2d5a37fd9d84
ms.openlocfilehash: 24a3f00987ff5ca4bf82d1a3206857ec3c4b3f09
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086893"
---
# <a name="how-to-use-tab-completion-in-the-script-pane-and-console-pane"></a><span data-ttu-id="54658-103">Betik Bölmesi ve Konsol Bölmesinde Sekme Tamamlamayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="54658-103">How to Use Tab Completion in the Script Pane and Console Pane</span></span>

<span data-ttu-id="54658-104">Sekme tamamlama, betik bölmesine ya da komut bölmesinde yazarken otomatik Yardım sağlar.</span><span class="sxs-lookup"><span data-stu-id="54658-104">Tab completion provides automatic help when you are typing in the Script Pane or in the Command Pane.</span></span> <span data-ttu-id="54658-105">Bu özelliğin avantajlarından yararlanmak için aşağıdaki adımları kullanın:</span><span class="sxs-lookup"><span data-stu-id="54658-105">Use the following steps to take advantage of this feature:</span></span>

## <a name="to-automatically-complete-a-command-entry"></a><span data-ttu-id="54658-106">Bir komut girişi otomatik olarak tamamlamak için</span><span class="sxs-lookup"><span data-stu-id="54658-106">To automatically complete a command entry</span></span>

<span data-ttu-id="54658-107">Bölmesinde komutu veya betik bölmesi, birkaç karakter, bir komut yazın ve istenen tamamlama metni seçmek için SEKME tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="54658-107">In the Command Pane or Script Pane, type a few characters of a command and then press TAB to select the desired completion text.</span></span> <span data-ttu-id="54658-108">Birden çok öğe, başlangıçta yazdığınız metni ile başlarsa, ardından istediğiniz öğeyi görünene kadar SEKME tuşuna basarak devam edin.</span><span class="sxs-lookup"><span data-stu-id="54658-108">If multiple items begin with the text that you initially typed, then continue pressing Tab until the item you want appears.</span></span> <span data-ttu-id="54658-109">Sekme tamamlama, bir cmdlet adı, parametre adı, değişken adı, nesne özelliği adı veya bir dosya yolu yazmaya yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="54658-109">Tab completion can help with typing a cmdlet name, parameter name, variable name, object property name, or a file path.</span></span>

> [!NOTE]
> <span data-ttu-id="54658-110">Yalnızca, .ps1, .psd1 veya .psm1 dosyaları düzenlerken betik bölmesinde SEKME tuşuna basarak otomatik olarak bir komut tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="54658-110">In the Script Pane, pressing TAB will automatically complete a command only when you are editing .ps1, .psd1, or .psm1 files.</span></span> <span data-ttu-id="54658-111">Sekme tamamlama, ne zaman komut bölmesinde yazarak dilediğiniz zaman çalışır.</span><span class="sxs-lookup"><span data-stu-id="54658-111">Tab completion works any time when you are typing in the Command Pane.</span></span>

## <a name="to-automatically-complete-a-cmdlet-parameter-entry"></a><span data-ttu-id="54658-112">Bir cmdlet parametresi girişi otomatik olarak tamamlamak için</span><span class="sxs-lookup"><span data-stu-id="54658-112">To automatically complete a cmdlet parameter entry</span></span>

<span data-ttu-id="54658-113">Komut bölmesinde veya betik bölmesinde bir kısa çizgi ve bir cmdlet'i yazın ve sonra SEKME tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="54658-113">In the Command Pane or Script pane, type a cmdlet followed by a dash and then press TAB.</span></span>

<span data-ttu-id="54658-114">Örneğin `Get-Process -` ve ardından birden çok kez sırayla her cmdlet parametreleri görüntülemek için SEKME tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="54658-114">For example, type `Get-Process -` and then press TAB multiple times to display each of the parameters for the cmdlet in turn.</span></span>

## <a name="see-also"></a><span data-ttu-id="54658-115">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="54658-115">See Also</span></span>

- [<span data-ttu-id="54658-116">Windows PowerShell ISE Tanıtımı</span><span class="sxs-lookup"><span data-stu-id="54658-116">Introducing the Windows PowerShell ISE</span></span>](Introducing-the-Windows-PowerShell-ISE.md)
- [<span data-ttu-id="54658-117">Bir PowerShell sekmesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="54658-117">How to Create a PowerShell Tab</span></span>](How-to-Create-a-PowerShell-Tab-in-Windows-PowerShell-ISE.md)
