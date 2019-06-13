---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: ISEAddOnToolCollection Nesnesi
ms.openlocfilehash: 28ab9747e573b7a76ee655289b341870b1728bc2
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030631"
---
# <a name="the-iseaddontoolcollection-object"></a><span data-ttu-id="c6527-103">ISEAddOnToolCollection Nesnesi</span><span class="sxs-lookup"><span data-stu-id="c6527-103">The ISEAddOnToolCollection Object</span></span>

<span data-ttu-id="c6527-104">**Iseaddontoolcollection** nesnedir koleksiyonu **Iseaddontool** nesneleri.</span><span class="sxs-lookup"><span data-stu-id="c6527-104">The **ISEAddOnToolCollection** object is a collection of **ISEAddOnTool** objects.</span></span> <span data-ttu-id="c6527-105">Bir örnek **$psISE.CurrentPowerShellTab.VerticalAddOnTools** nesne.</span><span class="sxs-lookup"><span data-stu-id="c6527-105">An example is the **$psISE.CurrentPowerShellTab.VerticalAddOnTools** object.</span></span>

## <a name="methods"></a><span data-ttu-id="c6527-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c6527-106">Methods</span></span>

### <a name="add-name-controltype-isvisible-"></a><span data-ttu-id="c6527-107">Ekleme\( adı, ControlType, \[IsVisible\] \)</span><span class="sxs-lookup"><span data-stu-id="c6527-107">Add\( Name, ControlType, \[IsVisible\] \)</span></span>

<span data-ttu-id="c6527-108">Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="c6527-108">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="c6527-109">Yeni bir eklenti aracı koleksiyon ekler.</span><span class="sxs-lookup"><span data-stu-id="c6527-109">Adds a new add-on tool to the collection.</span></span> <span data-ttu-id="c6527-110">Yeni eklenen eklenti aracını döndürür.</span><span class="sxs-lookup"><span data-stu-id="c6527-110">It returns the newly added add-on tool.</span></span> <span data-ttu-id="c6527-111">Bu komutu çalıştırmadan önce yerel bilgisayarda eklenti aracını yükleyin ve derlemesi yüklenemiyor.</span><span class="sxs-lookup"><span data-stu-id="c6527-111">Before you run this command, you must install the add-on tool on the local computer and load the assembly.</span></span>

<span data-ttu-id="c6527-112">**Ad** -dize Windows PowerShell ISE'ye eklenen eklenti aracını görünen adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c6527-112">**Name** - String Specifies the display name of the add-on tool that is added to Windows PowerShell ISE.</span></span>

<span data-ttu-id="c6527-113">**ControlType** -eklenen denetim türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="c6527-113">**ControlType** -Type Specifies the control that is added.</span></span>

<span data-ttu-id="c6527-114">**\[IsVisible\]**  -isteğe bağlı Boolean ayarlayın **$true**, eklenti aracını hemen ilişkili araç bölmesinde görünür.</span><span class="sxs-lookup"><span data-stu-id="c6527-114">**\[IsVisible\]** - optional Boolean If set to **$true**, the add-on tool is immediately visible in the associated tool pane.</span></span>

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="remove-item-"></a><span data-ttu-id="c6527-115">Kaldırma\( öğesi \)</span><span class="sxs-lookup"><span data-stu-id="c6527-115">Remove\( Item \)</span></span>

<span data-ttu-id="c6527-116">Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="c6527-116">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="c6527-117">Belirtilen eklenti aracını koleksiyondan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="c6527-117">Removes the specified add-on tool from the collection.</span></span>

<span data-ttu-id="c6527-118">**Öğe** -Microsoft.PowerShell.Host.ISE.ISEAddOnTool Windows PowerShell ISE'den kaldırılacak nesne belirtir.</span><span class="sxs-lookup"><span data-stu-id="c6527-118">**Item** - Microsoft.PowerShell.Host.ISE.ISEAddOnTool Specifies the object to be removed from Windows PowerShell ISE.</span></span>

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="setselectedpowershelltab-pstab-"></a><span data-ttu-id="c6527-119">SetSelectedPowerShellTab\( psTab \)</span><span class="sxs-lookup"><span data-stu-id="c6527-119">SetSelectedPowerShellTab\( psTab \)</span></span>

<span data-ttu-id="c6527-120">Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="c6527-120">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="c6527-121">PowerShell'i seçer sekmesinde **psTab** parametre belirtir.</span><span class="sxs-lookup"><span data-stu-id="c6527-121">Selects the PowerShell tab that the **psTab** parameter specifies.</span></span>

<span data-ttu-id="c6527-122">**psTab** -Microsoft.PowerShell.Host.ISE.PowerShellTab PowerShell sekmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="c6527-122">**psTab** - Microsoft.PowerShell.Host.ISE.PowerShellTab The PowerShell tab to select.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="remove-pstab-"></a><span data-ttu-id="c6527-123">Kaldırma\( psTab \)</span><span class="sxs-lookup"><span data-stu-id="c6527-123">Remove\( psTab \)</span></span>

<span data-ttu-id="c6527-124">Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="c6527-124">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="c6527-125">PowerShell kaldırır sekmesinde **psTab** parametre belirtir.</span><span class="sxs-lookup"><span data-stu-id="c6527-125">Removes the PowerShell tab that the **psTab** parameter specifies.</span></span>

<span data-ttu-id="c6527-126">**psTab** -kaldırmak için sekmesinde Microsoft.PowerShell.Host.ISE.PowerShellTab PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c6527-126">**psTab** - Microsoft.PowerShell.Host.ISE.PowerShellTab The PowerShell tab to remove.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

## <a name="see-also"></a><span data-ttu-id="c6527-127">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="c6527-127">See Also</span></span>

- [<span data-ttu-id="c6527-128">PowerShellTab nesnesi</span><span class="sxs-lookup"><span data-stu-id="c6527-128">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md)
- [<span data-ttu-id="c6527-129">Windows PowerShell ISE betik oluşturma nesne modelinin amacı</span><span class="sxs-lookup"><span data-stu-id="c6527-129">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="c6527-130">ISE Nesne Modeli Hiyerarşisi</span><span class="sxs-lookup"><span data-stu-id="c6527-130">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
