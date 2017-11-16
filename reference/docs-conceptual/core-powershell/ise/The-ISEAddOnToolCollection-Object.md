---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: ISEAddOnToolCollection nesnesi
ms.assetid: 634eab89-0845-4016-974b-361b09bb8f7b
ms.openlocfilehash: ba8b4e0e3952226407f00dea8b32785633256089
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2017
---
# <a name="the-iseaddontoolcollection-object"></a><span data-ttu-id="ff8c8-103">ISEAddOnToolCollection nesnesi</span><span class="sxs-lookup"><span data-stu-id="ff8c8-103">The ISEAddOnToolCollection Object</span></span>
  <span data-ttu-id="ff8c8-104">**ISEAddOnToolCollection** nesnesidir koleksiyonu **ISEAddOnTool** nesneleri.</span><span class="sxs-lookup"><span data-stu-id="ff8c8-104">The **ISEAddOnToolCollection** object is a collection of **ISEAddOnTool** objects.</span></span> <span data-ttu-id="ff8c8-105">Örnek **$psISE.CurrentPowerShellTab.VerticalAddOnTools** nesnesi.</span><span class="sxs-lookup"><span data-stu-id="ff8c8-105">An example is the **$psISE.CurrentPowerShellTab.VerticalAddOnTools** object.</span></span>

## <a name="methods"></a><span data-ttu-id="ff8c8-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ff8c8-106">Methods</span></span>

### <a name="add-name-controltype-isvisible-"></a><span data-ttu-id="ff8c8-107">Ekleme\( adı, ControlType, \[IsVisible\]\)</span><span class="sxs-lookup"><span data-stu-id="ff8c8-107">Add\( Name, ControlType, \[IsVisible\] \)</span></span>
  <span data-ttu-id="ff8c8-108">Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="ff8c8-108">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="ff8c8-109">Yeni bir eklenti aracı koleksiyona ekler.</span><span class="sxs-lookup"><span data-stu-id="ff8c8-109">Adds a new add-on tool to the collection.</span></span> <span data-ttu-id="ff8c8-110">Yeni eklenen eklenti aracı döndürür.</span><span class="sxs-lookup"><span data-stu-id="ff8c8-110">It returns the newly added add-on tool.</span></span> <span data-ttu-id="ff8c8-111">Bu komutu çalıştırmadan önce yerel bilgisayarda eklenti aracını yükleyin ve derleme yükleme.</span><span class="sxs-lookup"><span data-stu-id="ff8c8-111">Before you run this command, you must install the add-on tool on the local computer and load the assembly.</span></span>

 <span data-ttu-id="ff8c8-112">**Ad** -dize için Windows PowerShell ISE eklenen eklenti aracı görünen adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ff8c8-112">**Name** - String Specifies the display name of the add-on tool that is added to Windows PowerShell ISE.</span></span>

 <span data-ttu-id="ff8c8-113">**ControlType** -eklenen denetim türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="ff8c8-113">**ControlType** -Type Specifies the control that is added.</span></span>

 <span data-ttu-id="ff8c8-114">**\[IsVisible\]**  -isteğe bağlı Boole ayarlayın **$true**, eklenti araçtır hemen ilişkili araç bölmesinde görünür.</span><span class="sxs-lookup"><span data-stu-id="ff8c8-114">**\[IsVisible\]** - optional Boolean If set to **$true**, the add-on tool is immediately visible in the associated tool pane.</span></span>

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="remove-item-"></a><span data-ttu-id="ff8c8-115">Kaldırma\( öğesi\)</span><span class="sxs-lookup"><span data-stu-id="ff8c8-115">Remove\( Item \)</span></span>
  <span data-ttu-id="ff8c8-116">Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="ff8c8-116">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="ff8c8-117">Belirtilen eklenti aracı koleksiyondan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ff8c8-117">Removes the specified add-on tool from the collection.</span></span>

 <span data-ttu-id="ff8c8-118">**Öğe** -Microsoft.PowerShell.Host.ISE.ISEAddOnTool Windows PowerShell ISE kaldırılacak nesne belirtir.</span><span class="sxs-lookup"><span data-stu-id="ff8c8-118">**Item** - Microsoft.PowerShell.Host.ISE.ISEAddOnTool Specifies the object to be removed from Windows PowerShell ISE.</span></span>

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="setselectedpowershelltab-pstab-"></a><span data-ttu-id="ff8c8-119">SetSelectedPowerShellTab\( psTab\)</span><span class="sxs-lookup"><span data-stu-id="ff8c8-119">SetSelectedPowerShellTab\( psTab \)</span></span>
  <span data-ttu-id="ff8c8-120">Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="ff8c8-120">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="ff8c8-121">Seçer PowerShell sekmesinde **psTab** parametresi belirtir.</span><span class="sxs-lookup"><span data-stu-id="ff8c8-121">Selects the PowerShell tab that the **psTab** parameter specifies.</span></span>

 <span data-ttu-id="ff8c8-122">**psTab** -Microsoft.PowerShell.Host.ISE.PowerShellTab PowerShell sekmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="ff8c8-122">**psTab** - Microsoft.PowerShell.Host.ISE.PowerShellTab The PowerShell tab to select.</span></span>

```powershell
      $newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="Brand New Tab"
```

### <a name="remove-pstab-"></a><span data-ttu-id="ff8c8-123">Kaldırma\( psTab\)</span><span class="sxs-lookup"><span data-stu-id="ff8c8-123">Remove\( psTab \)</span></span>
  <span data-ttu-id="ff8c8-124">Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="ff8c8-124">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="ff8c8-125">Kaldırır PowerShell sekmesinde **psTab** parametresi belirtir.</span><span class="sxs-lookup"><span data-stu-id="ff8c8-125">Removes the PowerShell tab that the **psTab** parameter specifies.</span></span>

 <span data-ttu-id="ff8c8-126">**psTab** -Microsoft.PowerShell.Host.ISE.PowerShellTab PowerShell sekmesini kaldırmak için.</span><span class="sxs-lookup"><span data-stu-id="ff8c8-126">**psTab** - Microsoft.PowerShell.Host.ISE.PowerShellTab The PowerShell tab to remove.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="This tab will go away in 5 seconds" 
sleep 5 
$psISE.PowerShellTabs.Remove($newTab)
```

## <a name="see-also"></a><span data-ttu-id="ff8c8-127">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="ff8c8-127">See Also</span></span>
- [<span data-ttu-id="ff8c8-128">PowerShellTab nesnesi</span><span class="sxs-lookup"><span data-stu-id="ff8c8-128">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md) 
- [<span data-ttu-id="ff8c8-129">Windows PowerShell ISE nesne modeli komut dosyası oluşturma</span><span class="sxs-lookup"><span data-stu-id="ff8c8-129">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="ff8c8-130">Windows PowerShell ISE nesne modeli başvurusu</span><span class="sxs-lookup"><span data-stu-id="ff8c8-130">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="ff8c8-131">ISE nesne modeli hiyerarşisi</span><span class="sxs-lookup"><span data-stu-id="ff8c8-131">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

  
