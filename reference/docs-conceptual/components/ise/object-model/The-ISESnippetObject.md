---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: ISESnippet Nesnesi
ms.assetid: 98bc8113-c3cd-4201-bdb9-9d9bdb7e266c
ms.openlocfilehash: f80080f4207cf226fb7466c4842446d08c081347
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685455"
---
# <a name="the-isesnippetobject"></a>ISESnippet Nesnesi

Bir **ISESnippet** nesnedir Microsoft.PowerShell.Host.ISE.ISESnippet sınıfının örneği. Üyeleri **$psISE.CurrentPowerShellTab.Snippets** koleksiyonu olan tüm örnekleri **ISESnippet** nesneleri. Bir kod parçacığı oluşturmak için en kolay yolu kullanmaktır [yeni IseSnippet&#91;PSITPro5_ISE&#93; ](https://technet.microsoft.com/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) cmdlet'i.

## <a name="properties"></a>Özellikler

### <a name="author"></a>Yazar

Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.

Kod parçacığı yazarının adını alan salt okunur özelliği.

```powershell
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author
```

### <a name="codefragment"></a>CodeFragment

Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.

Düzenleyiciye eklenmesi için kod parçasını alan salt okunur özelliği.

```powershell
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment
```

### <a name="shortcut"></a>Kısayol

Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.

Klavye kısayol menü öğesi için Windows salt okunur özelliği.

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## <a name="see-also"></a>Ayrıca bkz:

- [Isesnippetcollection nesnesi](The-ISESnippetCollection-Object.md)
- [Windows PowerShell ISE betik oluşturma nesne modelinin amacı](purpose-of-the-windows-powershell-ise-scripting-object-model.md)
- [ISE Nesne Modeli Hiyerarşisi](The-ISE-Object-Model-Hierarchy.md)