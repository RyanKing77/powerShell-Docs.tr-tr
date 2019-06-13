---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: ISESnippet Nesnesi
ms.openlocfilehash: 62d470569deb051fca80005235d4c492319cf5ec
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67028893"
---
# <a name="the-isesnippetobject"></a><span data-ttu-id="c6758-103">ISESnippet Nesnesi</span><span class="sxs-lookup"><span data-stu-id="c6758-103">The ISESnippetObject</span></span>

<span data-ttu-id="c6758-104">Bir **ISESnippet** nesnedir Microsoft.PowerShell.Host.ISE.ISESnippet sınıfının örneği.</span><span class="sxs-lookup"><span data-stu-id="c6758-104">An **ISESnippet** object is an instance of the Microsoft.PowerShell.Host.ISE.ISESnippet class.</span></span> <span data-ttu-id="c6758-105">Üyeleri **$psISE.CurrentPowerShellTab.Snippets** koleksiyonu olan tüm örnekleri **ISESnippet** nesneleri.</span><span class="sxs-lookup"><span data-stu-id="c6758-105">The members of the **$psISE.CurrentPowerShellTab.Snippets** collection are all examples of **ISESnippet** objects.</span></span> <span data-ttu-id="c6758-106">Bir kod parçacığı oluşturmak için en kolay yolu kullanmaktır [yeni IseSnippet&#91;PSITPro5_ISE&#93; ](https://technet.microsoft.com/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="c6758-106">The easiest way to create a snippet is to use the [New-IseSnippet&#91;PSITPro5_ISE&#93;](https://technet.microsoft.com/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) cmdlet.</span></span>

## <a name="properties"></a><span data-ttu-id="c6758-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="c6758-107">Properties</span></span>

### <a name="author"></a><span data-ttu-id="c6758-108">Yazar</span><span class="sxs-lookup"><span data-stu-id="c6758-108">Author</span></span>

<span data-ttu-id="c6758-109">Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="c6758-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="c6758-110">Kod parçacığı yazarının adını alan salt okunur özelliği.</span><span class="sxs-lookup"><span data-stu-id="c6758-110">The read-only property that gets the name of the author of the snippet.</span></span>

```powershell
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author
```

### <a name="codefragment"></a><span data-ttu-id="c6758-111">CodeFragment</span><span class="sxs-lookup"><span data-stu-id="c6758-111">CodeFragment</span></span>

<span data-ttu-id="c6758-112">Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="c6758-112">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="c6758-113">Düzenleyiciye eklenmesi için kod parçasını alan salt okunur özelliği.</span><span class="sxs-lookup"><span data-stu-id="c6758-113">The read-only property that gets the code fragment to be inserted into the editor.</span></span>

```powershell
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment
```

### <a name="shortcut"></a><span data-ttu-id="c6758-114">Kısayol</span><span class="sxs-lookup"><span data-stu-id="c6758-114">Shortcut</span></span>

<span data-ttu-id="c6758-115">Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="c6758-115">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="c6758-116">Klavye kısayol menü öğesi için Windows salt okunur özelliği.</span><span class="sxs-lookup"><span data-stu-id="c6758-116">The read-only property that gets the Windows keyboard shortcut for the menu item.</span></span>

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## <a name="see-also"></a><span data-ttu-id="c6758-117">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="c6758-117">See Also</span></span>

- [<span data-ttu-id="c6758-118">Isesnippetcollection nesnesi</span><span class="sxs-lookup"><span data-stu-id="c6758-118">The ISESnippetCollection Object</span></span>](The-ISESnippetCollection-Object.md)
- [<span data-ttu-id="c6758-119">Windows PowerShell ISE betik oluşturma nesne modelinin amacı</span><span class="sxs-lookup"><span data-stu-id="c6758-119">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](purpose-of-the-windows-powershell-ise-scripting-object-model.md)
- [<span data-ttu-id="c6758-120">ISE Nesne Modeli Hiyerarşisi</span><span class="sxs-lookup"><span data-stu-id="c6758-120">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
