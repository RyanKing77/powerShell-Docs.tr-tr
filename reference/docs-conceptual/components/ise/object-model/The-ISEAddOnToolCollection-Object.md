---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: ISEAddOnToolCollection Nesnesi
ms.assetid: 634eab89-0845-4016-974b-361b09bb8f7b
ms.openlocfilehash: ff4f19d1a85a592f2f4f09c62caa0971751bdff7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057412"
---
# <a name="the-iseaddontoolcollection-object"></a><span data-ttu-id="012c3-103">ISEAddOnToolCollection Nesnesi</span><span class="sxs-lookup"><span data-stu-id="012c3-103">The ISEAddOnToolCollection Object</span></span>

<span data-ttu-id="012c3-104">**Iseaddontoolcollection** nesnedir koleksiyonu **Iseaddontool** nesneleri.</span><span class="sxs-lookup"><span data-stu-id="012c3-104">The **ISEAddOnToolCollection** object is a collection of **ISEAddOnTool** objects.</span></span> <span data-ttu-id="012c3-105">Bir örnek **$psISE.CurrentPowerShellTab.VerticalAddOnTools** nesne.</span><span class="sxs-lookup"><span data-stu-id="012c3-105">An example is the **$psISE.CurrentPowerShellTab.VerticalAddOnTools** object.</span></span>

## <a name="methods"></a><span data-ttu-id="012c3-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="012c3-106">Methods</span></span>

### <a name="add-name-controltype-isvisible-"></a><span data-ttu-id="012c3-107">Ekleme\( adı, ControlType, \[IsVisible\] \)</span><span class="sxs-lookup"><span data-stu-id="012c3-107">Add\( Name, ControlType, \[IsVisible\] \)</span></span>

<span data-ttu-id="012c3-108">Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="012c3-108">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="012c3-109">Yeni bir eklenti aracı koleksiyon ekler.</span><span class="sxs-lookup"><span data-stu-id="012c3-109">Adds a new add-on tool to the collection.</span></span> <span data-ttu-id="012c3-110">Yeni eklenen eklenti aracını döndürür.</span><span class="sxs-lookup"><span data-stu-id="012c3-110">It returns the newly added add-on tool.</span></span> <span data-ttu-id="012c3-111">Bu komutu çalıştırmadan önce yerel bilgisayarda eklenti aracını yükleyin ve derlemesi yüklenemiyor.</span><span class="sxs-lookup"><span data-stu-id="012c3-111">Before you run this command, you must install the add-on tool on the local computer and load the assembly.</span></span>

<span data-ttu-id="012c3-112">**Ad** -dize Windows PowerShell ISE'ye eklenen eklenti aracını görünen adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="012c3-112">**Name** - String Specifies the display name of the add-on tool that is added to Windows PowerShell ISE.</span></span>

<span data-ttu-id="012c3-113">**ControlType** -eklenen denetim türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="012c3-113">**ControlType** -Type Specifies the control that is added.</span></span>

<span data-ttu-id="012c3-114">**\[IsVisible\]**  -isteğe bağlı Boolean ayarlayın **$true**, eklenti aracını hemen ilişkili araç bölmesinde görünür.</span><span class="sxs-lookup"><span data-stu-id="012c3-114">**\[IsVisible\]** - optional Boolean If set to **$true**, the add-on tool is immediately visible in the associated tool pane.</span></span>

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="remove-item-"></a><span data-ttu-id="012c3-115">Kaldırma\( öğesi \)</span><span class="sxs-lookup"><span data-stu-id="012c3-115">Remove\( Item \)</span></span>

<span data-ttu-id="012c3-116">Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="012c3-116">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="012c3-117">Belirtilen eklenti aracını koleksiyondan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="012c3-117">Removes the specified add-on tool from the collection.</span></span>

<span data-ttu-id="012c3-118">**Öğe** -Microsoft.PowerShell.Host.ISE.ISEAddOnTool Windows PowerShell ISE'den kaldırılacak nesne belirtir.</span><span class="sxs-lookup"><span data-stu-id="012c3-118">**Item** - Microsoft.PowerShell.Host.ISE.ISEAddOnTool Specifies the object to be removed from Windows PowerShell ISE.</span></span>

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="setselectedpowershelltab-pstab-"></a><span data-ttu-id="012c3-119">SetSelectedPowerShellTab\( psTab \)</span><span class="sxs-lookup"><span data-stu-id="012c3-119">SetSelectedPowerShellTab\( psTab \)</span></span>

<span data-ttu-id="012c3-120">Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="012c3-120">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="012c3-121">PowerShell'i seçer sekmesinde **psTab** parametre belirtir.</span><span class="sxs-lookup"><span data-stu-id="012c3-121">Selects the PowerShell tab that the **psTab** parameter specifies.</span></span>

<span data-ttu-id="012c3-122">**psTab** -Microsoft.PowerShell.Host.ISE.PowerShellTab PowerShell sekmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="012c3-122">**psTab** - Microsoft.PowerShell.Host.ISE.PowerShellTab The PowerShell tab to select.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="remove-pstab-"></a><span data-ttu-id="012c3-123">Kaldırma\( psTab \)</span><span class="sxs-lookup"><span data-stu-id="012c3-123">Remove\( psTab \)</span></span>

<span data-ttu-id="012c3-124">Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="012c3-124">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="012c3-125">PowerShell kaldırır sekmesinde **psTab** parametre belirtir.</span><span class="sxs-lookup"><span data-stu-id="012c3-125">Removes the PowerShell tab that the **psTab** parameter specifies.</span></span>

<span data-ttu-id="012c3-126">**psTab** -kaldırmak için sekmesinde Microsoft.PowerShell.Host.ISE.PowerShellTab PowerShell.</span><span class="sxs-lookup"><span data-stu-id="012c3-126">**psTab** - Microsoft.PowerShell.Host.ISE.PowerShellTab The PowerShell tab to remove.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

## <a name="see-also"></a><span data-ttu-id="012c3-127">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="012c3-127">See Also</span></span>

- [<span data-ttu-id="012c3-128">PowerShellTab nesnesi</span><span class="sxs-lookup"><span data-stu-id="012c3-128">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md)
- [<span data-ttu-id="012c3-129">Windows PowerShell ISE betik oluşturma nesne modelinin amacı</span><span class="sxs-lookup"><span data-stu-id="012c3-129">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="012c3-130">ISE Nesne Modeli Hiyerarşisi</span><span class="sxs-lookup"><span data-stu-id="012c3-130">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)