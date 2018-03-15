---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: ISESnippet Nesnesi
ms.assetid: 98bc8113-c3cd-4201-bdb9-9d9bdb7e266c
ms.openlocfilehash: f1b023291826d5568eb8bdf5a898a00228825276
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2018
---
# <a name="the-isesnippetobject"></a><span data-ttu-id="8153b-103">ISESnippet Nesnesi</span><span class="sxs-lookup"><span data-stu-id="8153b-103">The ISESnippetObject</span></span>
  <span data-ttu-id="8153b-104">Bir **ISESnippet** nesnesidir Microsoft.PowerShell.Host.ISE.ISESnippet sınıfının bir örneği.</span><span class="sxs-lookup"><span data-stu-id="8153b-104">An **ISESnippet** object is an instance of the Microsoft.PowerShell.Host.ISE.ISESnippet class.</span></span> <span data-ttu-id="8153b-105">Üyeleri **$psISE.CurrentPowerShellTab.Snippets** koleksiyonu olan tüm örnekleri **ISESnippet** nesneleri.</span><span class="sxs-lookup"><span data-stu-id="8153b-105">The members of the **$psISE.CurrentPowerShellTab.Snippets** collection are all examples of **ISESnippet** objects.</span></span> <span data-ttu-id="8153b-106">Parçacık oluşturmanın en kolay yolu kullanmaktır [yeni IseSnippet&#91;PSITPro5_ISE&#93; ](https://technet.microsoft.com/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="8153b-106">The easiest way to create a snippet is to use the [New-IseSnippet&#91;PSITPro5_ISE&#93;](https://technet.microsoft.com/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) cmdlet.</span></span>

## <a name="properties"></a><span data-ttu-id="8153b-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="8153b-107">Properties</span></span>

### <a name="author"></a><span data-ttu-id="8153b-108">Yazar</span><span class="sxs-lookup"><span data-stu-id="8153b-108">Author</span></span>
  <span data-ttu-id="8153b-109">Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="8153b-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="8153b-110">Kod parçacığını yazarının adını alır salt okunur özellik.</span><span class="sxs-lookup"><span data-stu-id="8153b-110">The read-only property that gets the name of the author of the snippet.</span></span>

```
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author

```

### <a name="codefragment"></a><span data-ttu-id="8153b-111">CodeFragment</span><span class="sxs-lookup"><span data-stu-id="8153b-111">CodeFragment</span></span>
  <span data-ttu-id="8153b-112">Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="8153b-112">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="8153b-113">Düzenleyiciye eklenecek kod parçası alır salt okunur özellik.</span><span class="sxs-lookup"><span data-stu-id="8153b-113">The read-only property that gets the code fragment to be inserted into the editor.</span></span>

```
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment

```

### <a name="shortcut"></a><span data-ttu-id="8153b-114">Kısayol</span><span class="sxs-lookup"><span data-stu-id="8153b-114">Shortcut</span></span>
  <span data-ttu-id="8153b-115">Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="8153b-115">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="8153b-116">Klavye kısayol menü öğesi için Windows alır salt okunur özellik.</span><span class="sxs-lookup"><span data-stu-id="8153b-116">The read-only property that gets the Windows keyboard shortcut for the menu item.</span></span>

```
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## <a name="see-also"></a><span data-ttu-id="8153b-117">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="8153b-117">See Also</span></span>
- [<span data-ttu-id="8153b-118">The ISESnippetCollection Object</span><span class="sxs-lookup"><span data-stu-id="8153b-118">The ISESnippetCollection Object</span></span>](The-ISESnippetCollection-Object.md)
- [<span data-ttu-id="8153b-119">Nesne modeli komut dosyası Windows PowerShell ISE amacı</span><span class="sxs-lookup"><span data-stu-id="8153b-119">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](purpose-of-the-windows-powershell-ise-scripting-object-model.md)
- [<span data-ttu-id="8153b-120">ISE Nesne Modeli Hiyerarşisi</span><span class="sxs-lookup"><span data-stu-id="8153b-120">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
