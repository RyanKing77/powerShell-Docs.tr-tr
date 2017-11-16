---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: PowerShellTabCollection nesnesi
ms.assetid: 81f4bf4a-83bf-415e-8378-1703792fbb58
ms.openlocfilehash: dcdc16ae126453b6ade64917ac4950cc05e5f8ad
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2017
---
# <a name="the-powershelltabcollection-object"></a><span data-ttu-id="38a67-103">PowerShellTabCollection nesnesi</span><span class="sxs-lookup"><span data-stu-id="38a67-103">The PowerShellTabCollection Object</span></span>
  <span data-ttu-id="38a67-104">**PowerShellTab** koleksiyon nesnesi koleksiyonudur **PowerShellTab** nesneleri.</span><span class="sxs-lookup"><span data-stu-id="38a67-104">The **PowerShellTab** collection object is a collection of **PowerShellTab** objects.</span></span> <span data-ttu-id="38a67-105">Her **PowerShellTab** nesne ayrı bir çalışma zamanı ortamı olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="38a67-105">Each **PowerShellTab** object functions as a separate runtime environment.</span></span> <span data-ttu-id="38a67-106">Microsoft.PowerShell.Host.ISE.PowerShellTabs sınıfının bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="38a67-106">It is an instance of Microsoft.PowerShell.Host.ISE.PowerShellTabs class.</span></span> <span data-ttu-id="38a67-107">Örnek **$psISE.PowerShellTabs** nesnesi.</span><span class="sxs-lookup"><span data-stu-id="38a67-107">An example is the **$psISE.PowerShellTabs** object.</span></span>

## <a name="methods"></a><span data-ttu-id="38a67-108">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="38a67-108">Methods</span></span>

### <a name="add"></a><span data-ttu-id="38a67-109">Ekleme\(\)</span><span class="sxs-lookup"><span data-stu-id="38a67-109">Add\(\)</span></span>
  <span data-ttu-id="38a67-110">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="38a67-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="38a67-111">Yeni bir PowerShell sekmesi koleksiyona ekler.</span><span class="sxs-lookup"><span data-stu-id="38a67-111">Adds a new PowerShell tab to the collection.</span></span> <span data-ttu-id="38a67-112">Yeni eklenen sekmesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="38a67-112">It returns the newly added tab.</span></span>

```
$NewTab=$psISE.PowerShellTabs.Add()
$newTab.DisplayName="Brand New Tab"
```

### <a name="removemicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="38a67-113">Kaldırma\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="38a67-113">Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>
  <span data-ttu-id="38a67-114">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="38a67-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="38a67-115">Tarafından belirtilen sekmesini kaldırır **psTab** parametresi.</span><span class="sxs-lookup"><span data-stu-id="38a67-115">Removes the tab that is specified by the **psTab** parameter.</span></span>

 <span data-ttu-id="38a67-116">**psTab** kaldırmak için PowerShell sekmesi.</span><span class="sxs-lookup"><span data-stu-id="38a67-116">**psTab** The PowerShell tab to remove.</span></span>

```

$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="This tab will go away in 5 seconds" 
sleep 5 
$psISE.PowerShellTabs.Remove($newTab)
```

### <a name="setselectedpowershelltabmicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="38a67-117">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="38a67-117">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>
  <span data-ttu-id="38a67-118">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="38a67-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="38a67-119">Tarafından belirtilen PowerShell sekmesinde seçer **psTab** parametresi şu anda etkin PowerShell sekmesinde yapın.</span><span class="sxs-lookup"><span data-stu-id="38a67-119">Selects the PowerShell tab that is specified by the **psTab** parameter to make it the currently active PowerShell tab.</span></span>

 <span data-ttu-id="38a67-120">**psTab** PowerShell sekmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="38a67-120">**psTab** The PowerShell tab to select.</span></span>

```
# Save the current tab in a variable and rename it
$OldTab = $psISE.CurrentPowerShellTab
$psISE.CurrentPowerShellTab.DisplayName="Old Tab"
# Create a new tab and give it a new display name
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName="Brand New Tab" 
# Switch back to the original tab
$psISE.PowerShellTabs.SelectedPowerShellTab=$oldtab
```

## <a name="see-also"></a><span data-ttu-id="38a67-121">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="38a67-121">See Also</span></span>
- [<span data-ttu-id="38a67-122">PowerShellTab nesnesi</span><span class="sxs-lookup"><span data-stu-id="38a67-122">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md) 
- [<span data-ttu-id="38a67-123">Windows PowerShell ISE nesne modeli komut dosyası oluşturma</span><span class="sxs-lookup"><span data-stu-id="38a67-123">The Windows PowerShell ISE Scripting Object Model</span></span>](../ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="38a67-124">Windows PowerShell ISE nesne modeli başvurusu</span><span class="sxs-lookup"><span data-stu-id="38a67-124">Windows PowerShell ISE Object Model Reference</span></span>](../ise/Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="38a67-125">ISE nesne modeli hiyerarşisi</span><span class="sxs-lookup"><span data-stu-id="38a67-125">The ISE Object Model Hierarchy</span></span>](../ise/The-ISE-Object-Model-Hierarchy.md)

  
