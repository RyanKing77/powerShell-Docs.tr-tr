---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: PowerShellTabCollection Nesnesi
ms.assetid: 81f4bf4a-83bf-415e-8378-1703792fbb58
ms.openlocfilehash: d9088b26de35360b8258d3f15924b3010a986d15
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405920"
---
# <a name="the-powershelltabcollection-object"></a><span data-ttu-id="ab864-103">PowerShellTabCollection Nesnesi</span><span class="sxs-lookup"><span data-stu-id="ab864-103">The PowerShellTabCollection Object</span></span>

<span data-ttu-id="ab864-104">**PowerShellTab** koleksiyon nesnesi, koleksiyonudur **PowerShellTab** nesneleri.</span><span class="sxs-lookup"><span data-stu-id="ab864-104">The **PowerShellTab** collection object is a collection of **PowerShellTab** objects.</span></span> <span data-ttu-id="ab864-105">Her **PowerShellTab** nesne ayrı bir çalışma zamanı ortamı olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="ab864-105">Each **PowerShellTab** object functions as a separate runtime environment.</span></span> <span data-ttu-id="ab864-106">Microsoft.PowerShell.Host.ISE.PowerShellTabs sınıfının bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="ab864-106">It is an instance of Microsoft.PowerShell.Host.ISE.PowerShellTabs class.</span></span> <span data-ttu-id="ab864-107">Bir örnek **$psISE.PowerShellTabs** nesne.</span><span class="sxs-lookup"><span data-stu-id="ab864-107">An example is the **$psISE.PowerShellTabs** object.</span></span>

## <a name="methods"></a><span data-ttu-id="ab864-108">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ab864-108">Methods</span></span>

### <a name="add"></a><span data-ttu-id="ab864-109">ekleme\(\)</span><span class="sxs-lookup"><span data-stu-id="ab864-109">Add\(\)</span></span>

<span data-ttu-id="ab864-110">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="ab864-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="ab864-111">Yeni bir PowerShell sekmesi koleksiyona ekler.</span><span class="sxs-lookup"><span data-stu-id="ab864-111">Adds a new PowerShell tab to the collection.</span></span> <span data-ttu-id="ab864-112">Yeni eklenen sekmesine döndürür.</span><span class="sxs-lookup"><span data-stu-id="ab864-112">It returns the newly added tab.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="removemicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="ab864-113">Kaldırma\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="ab864-113">Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>

<span data-ttu-id="ab864-114">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="ab864-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="ab864-115">Tarafından belirtilen sekmesini kaldırır **psTab** parametresi.</span><span class="sxs-lookup"><span data-stu-id="ab864-115">Removes the tab that is specified by the **psTab** parameter.</span></span>

<span data-ttu-id="ab864-116">**psTab** kaldırmak için bir PowerShell sekmesi.</span><span class="sxs-lookup"><span data-stu-id="ab864-116">**psTab** The PowerShell tab to remove.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

### <a name="setselectedpowershelltabmicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="ab864-117">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="ab864-117">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>

<span data-ttu-id="ab864-118">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="ab864-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="ab864-119">Tarafından belirtilen PowerShell sekme seçer **psTab** şu anda etkin PowerShell sekme yapmak için parametre.</span><span class="sxs-lookup"><span data-stu-id="ab864-119">Selects the PowerShell tab that is specified by the **psTab** parameter to make it the currently active PowerShell tab.</span></span>

<span data-ttu-id="ab864-120">**psTab** PowerShell sekmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="ab864-120">**psTab** The PowerShell tab to select.</span></span>

```powershell
# Save the current tab in a variable and rename it
$oldTab = $psISE.CurrentPowerShellTab
$psISE.CurrentPowerShellTab.DisplayName = 'Old Tab'
# Create a new tab and give it a new display name
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
# Switch back to the original tab
$psISE.PowerShellTabs.SelectedPowerShellTab = $oldTab
```

## <a name="see-also"></a><span data-ttu-id="ab864-121">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="ab864-121">See Also</span></span>

- [<span data-ttu-id="ab864-122">PowerShellTab nesnesi</span><span class="sxs-lookup"><span data-stu-id="ab864-122">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md)
- [<span data-ttu-id="ab864-123">Windows PowerShell ISE betik oluşturma nesne modelinin amacı</span><span class="sxs-lookup"><span data-stu-id="ab864-123">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="ab864-124">ISE Nesne Modeli Hiyerarşisi</span><span class="sxs-lookup"><span data-stu-id="ab864-124">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)