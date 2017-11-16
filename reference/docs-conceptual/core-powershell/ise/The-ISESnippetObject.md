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
# <a name="the-isesnippetobject"></a>ISESnippetObject
  Bir **ISESnippet** nesnesidir Microsoft.PowerShell.Host.ISE.ISESnippet sınıfının bir örneği. Üyeleri **$psISE.CurrentPowerShellTab.Snippets** koleksiyonu olan tüm örnekleri **ISESnippet** nesneleri. Parçacık oluşturmanın en kolay yolu kullanmaktır [yeni IseSnippet &#91; PSITPro5_ISE &#93; ](https://technet.microsoft.com/en-us/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) cmdlet'i.

## <a name="properties"></a>Özellikler

### <a name="author"></a>Yazar
  Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil. 

 Kod parçacığını yazarının adını alır salt okunur özellik.

```
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author

```

### <a name="codefragment"></a>CodeFragment
  Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil. 

 Düzenleyiciye eklenecek kod parçası alır salt okunur özellik.

```
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment

```

### <a name="shortcut"></a>Kısayol
  Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil. 

 Klavye kısayol menü öğesi için Windows alır salt okunur özellik.

```
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## <a name="see-also"></a>Ayrıca bkz:
- [ISESnippetCollection nesnesi](The-ISESnippetCollection-Object.md) 
- [Windows PowerShell ISE nesne modeli komut dosyası oluşturma](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Windows PowerShell ISE nesne modeli başvurusu](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [ISE nesne modeli hiyerarşisi](The-ISE-Object-Model-Hierarchy.md)

  
