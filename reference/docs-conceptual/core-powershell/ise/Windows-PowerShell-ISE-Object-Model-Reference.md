---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: "Windows PowerShell ISE Nesne Modeli Başvurusu"
ms.assetid: e1a9e7d1-0fd5-47de-8d9b-f1be1ed13b0c
ms.openlocfilehash: 624ddca3895ba3e24bf52a27babdb07e8714baae
ms.sourcegitcommit: 18e3bfae83ffe282d3fd1a45f5386f3b7250f0c0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2018
---
# <a name="windows-powershell-ise-object-model-reference"></a><span data-ttu-id="7f3be-103">Windows PowerShell ISE Nesne Modeli Başvurusu</span><span class="sxs-lookup"><span data-stu-id="7f3be-103">Windows PowerShell ISE Object Model Reference</span></span>
  
## <a name="object-model-reference"></a><span data-ttu-id="7f3be-104">Nesne Modeli Başvurusu</span><span class="sxs-lookup"><span data-stu-id="7f3be-104">Object Model Reference</span></span>
 <span data-ttu-id="7f3be-105">Bu bölüm, çeşitli nesneleri inWindows PowerShell® Tümleşik komut dosyası ortamı (ISE) tanımlayan temel sınıflar üzerinde bir başvuru sağlar.</span><span class="sxs-lookup"><span data-stu-id="7f3be-105">This section provides a reference on the underlying classes that define the various objects inWindows PowerShell® Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="7f3be-106">Kendi hiyerarşilerinde düzenlenmiş nesneleri görmek için bkz: [işe nesne modeli hiyerarşisi](The-ISE-Object-Model-Hierarchy.md).</span><span class="sxs-lookup"><span data-stu-id="7f3be-106">To see the objects organized in their hierarchy, see [The ISE Object Model Hierarchy](The-ISE-Object-Model-Hierarchy.md).</span></span>

 <span data-ttu-id="7f3be-107">[ISEAddOnTool nesne](The-ISEAddOnTool-Object.md) örnekler: $psISE.CurrentVisibleHorizontalTool, $psISE.CurrentVisibleVerticalTool.</span><span class="sxs-lookup"><span data-stu-id="7f3be-107">[The ISEAddOnTool Object](The-ISEAddOnTool-Object.md) Examples: $psISE.CurrentVisibleHorizontalTool, $psISE.CurrentVisibleVerticalTool.</span></span>

 <span data-ttu-id="7f3be-108">[ISEAddOnTool nesne](The-ISEAddOnTool-Object.md) [ISEEditor nesne](The-ISEEditor-Object.md) örnekler: $psISE.CurrentFile.Editor, $psISE.CurrentPowerShellTab.Output, $psISE.CurrentPowerShellTab.CommandPane.</span><span class="sxs-lookup"><span data-stu-id="7f3be-108">[The ISEAddOnTool Object](The-ISEAddOnTool-Object.md) [The ISEEditor Object](The-ISEEditor-Object.md) Examples: $psISE.CurrentFile.Editor, $psISE.CurrentPowerShellTab.Output, $psISE.CurrentPowerShellTab.CommandPane.</span></span>

 <span data-ttu-id="7f3be-109">[ISEFile nesne](The-ISEFile-Object.md) örnekler: $psISE.CurrentFile, $psISE.PowerShellTabs.Files\[0\].</span><span class="sxs-lookup"><span data-stu-id="7f3be-109">[The ISEFile Object](The-ISEFile-Object.md) Examples: $psISE.CurrentFile, $psISE.PowerShellTabs.Files\[0\].</span></span>

 <span data-ttu-id="7f3be-110">[ISEFileCollection nesne](The-ISEFileCollection-Object.md) örnekler: $psISE.PowerShellTabs.Files.</span><span class="sxs-lookup"><span data-stu-id="7f3be-110">[The ISEFileCollection Object](The-ISEFileCollection-Object.md) Examples: $psISE.PowerShellTabs.Files.</span></span>

 <span data-ttu-id="7f3be-111">[ISEMenuItem nesne](The-ISEMenuItem-Object.md) örnekler: $psISE.CurrentPowerShellTab.AddOnsMenu, $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus\[0\].</span><span class="sxs-lookup"><span data-stu-id="7f3be-111">[The ISEMenuItem Object](The-ISEMenuItem-Object.md) Examples: $psISE.CurrentPowerShellTab.AddOnsMenu , $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus\[0\].</span></span>

 <span data-ttu-id="7f3be-112">[ISEMenuItemCollection nesne](The-ISEMenuItemCollection-Object.md) örnek: $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.</span><span class="sxs-lookup"><span data-stu-id="7f3be-112">[The ISEMenuItemCollection Object](The-ISEMenuItemCollection-Object.md) Example: $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.</span></span>

 <span data-ttu-id="7f3be-113">[ISEOptions nesne](The-ISEOptions-Object.md) örnekler: $psISE.Options, $psISE.Options.DefaultOptions.</span><span class="sxs-lookup"><span data-stu-id="7f3be-113">[The ISEOptions Object](The-ISEOptions-Object.md) Examples: $psISE.Options, $psISE.Options.DefaultOptions.</span></span>

 <span data-ttu-id="7f3be-114">[ObjectModelRoot nesne](The-ObjectModelRoot-Object.md) örnek: kök $psISE nesnesi.</span><span class="sxs-lookup"><span data-stu-id="7f3be-114">[The ObjectModelRoot Object](The-ObjectModelRoot-Object.md) Example: The root $psISE object.</span></span>

 <span data-ttu-id="7f3be-115">[PowerShellTab nesne](The-PowerShellTab-Object.md) örnekler: $psISE.CurrentPowerShellTab, $psISE.PowerShellTabs\[0\].</span><span class="sxs-lookup"><span data-stu-id="7f3be-115">[The PowerShellTab Object](The-PowerShellTab-Object.md) Examples: $psISE.CurrentPowerShellTab, $psISE.PowerShellTabs\[0\].</span></span>

 <span data-ttu-id="7f3be-116">[PowerShellTabCollection nesne](The-PowerShellTabCollection-Object.md) örnek: $psISE.PowerShellTabs.</span><span class="sxs-lookup"><span data-stu-id="7f3be-116">[The PowerShellTabCollection Object](The-PowerShellTabCollection-Object.md) Example: $psISE.PowerShellTabs.</span></span>

## <a name="see-also"></a><span data-ttu-id="7f3be-117">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="7f3be-117">See Also</span></span>
- [<span data-ttu-id="7f3be-118">Windows PowerShell ISE nesne modeli komut dosyası oluşturma</span><span class="sxs-lookup"><span data-stu-id="7f3be-118">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
