---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: ISESnippetObject
ms.assetid: 98bc8113-c3cd-4201-bdb9-9d9bdb7e266c
ms.openlocfilehash: 6112f5252d2d1e868092da4a6cd04feb1875b597
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2017
---
# <a name="the-isesnippetobject"></a><span data-ttu-id="d73e7-103">ISESnippetObject</span><span class="sxs-lookup"><span data-stu-id="d73e7-103">The ISESnippetObject</span></span>
  <span data-ttu-id="d73e7-104">Bir **ISESnippet** nesnesidir Microsoft.PowerShell.Host.ISE.ISESnippet sınıfının bir örneği.</span><span class="sxs-lookup"><span data-stu-id="d73e7-104">An **ISESnippet** object is an instance of the Microsoft.PowerShell.Host.ISE.ISESnippet class.</span></span> <span data-ttu-id="d73e7-105">Üyeleri **$psISE.CurrentPowerShellTab.Snippets** koleksiyonu olan tüm örnekleri **ISESnippet** nesneleri.</span><span class="sxs-lookup"><span data-stu-id="d73e7-105">The members of the **$psISE.CurrentPowerShellTab.Snippets** collection are all examples of **ISESnippet** objects.</span></span> <span data-ttu-id="d73e7-106">Parçacık oluşturmanın en kolay yolu kullanmaktır [yeni IseSnippet &#91; PSITPro5_ISE &#93; ](https://technet.microsoft.com/en-us/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="d73e7-106">The easiest way to create a snippet is to use the [New-IseSnippet&#91;PSITPro5_ISE&#93;](https://technet.microsoft.com/en-us/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) cmdlet.</span></span>

## <a name="properties"></a><span data-ttu-id="d73e7-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="d73e7-107">Properties</span></span>

### <a name="author"></a><span data-ttu-id="d73e7-108">Yazar</span><span class="sxs-lookup"><span data-stu-id="d73e7-108">Author</span></span>
  <span data-ttu-id="d73e7-109">Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="d73e7-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="d73e7-110">Kod parçacığını yazarının adını alır salt okunur özellik.</span><span class="sxs-lookup"><span data-stu-id="d73e7-110">The read-only property that gets the name of the author of the snippet.</span></span>

```
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author

```

### <a name="codefragment"></a><span data-ttu-id="d73e7-111">CodeFragment</span><span class="sxs-lookup"><span data-stu-id="d73e7-111">CodeFragment</span></span>
  <span data-ttu-id="d73e7-112">Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="d73e7-112">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="d73e7-113">Düzenleyiciye eklenecek kod parçası alır salt okunur özellik.</span><span class="sxs-lookup"><span data-stu-id="d73e7-113">The read-only property that gets the code fragment to be inserted into the editor.</span></span>

```
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment

```

### <a name="shortcut"></a><span data-ttu-id="d73e7-114">Kısayol</span><span class="sxs-lookup"><span data-stu-id="d73e7-114">Shortcut</span></span>
  <span data-ttu-id="d73e7-115">Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="d73e7-115">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="d73e7-116">Klavye kısayol menü öğesi için Windows alır salt okunur özellik.</span><span class="sxs-lookup"><span data-stu-id="d73e7-116">The read-only property that gets the Windows keyboard shortcut for the menu item.</span></span>

```
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## <a name="see-also"></a><span data-ttu-id="d73e7-117">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="d73e7-117">See Also</span></span>
- [<span data-ttu-id="d73e7-118">ISESnippetCollection nesnesi</span><span class="sxs-lookup"><span data-stu-id="d73e7-118">The ISESnippetCollection Object</span></span>](The-ISESnippetCollection-Object.md) 
- [<span data-ttu-id="d73e7-119">Windows PowerShell ISE nesne modeli komut dosyası oluşturma</span><span class="sxs-lookup"><span data-stu-id="d73e7-119">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="d73e7-120">Windows PowerShell ISE nesne modeli başvurusu</span><span class="sxs-lookup"><span data-stu-id="d73e7-120">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="d73e7-121">ISE nesne modeli hiyerarşisi</span><span class="sxs-lookup"><span data-stu-id="d73e7-121">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

  
