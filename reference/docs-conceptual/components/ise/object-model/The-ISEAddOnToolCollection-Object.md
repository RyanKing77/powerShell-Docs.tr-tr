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
# <a name="the-iseaddontoolcollection-object"></a>ISEAddOnToolCollection Nesnesi

**Iseaddontoolcollection** nesnedir koleksiyonu **Iseaddontool** nesneleri. Bir örnek **$psISE.CurrentPowerShellTab.VerticalAddOnTools** nesne.

## <a name="methods"></a>Yöntemler

### <a name="add-name-controltype-isvisible-"></a>Ekleme\( adı, ControlType, \[IsVisible\] \)

Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.

Yeni bir eklenti aracı koleksiyon ekler. Yeni eklenen eklenti aracını döndürür. Bu komutu çalıştırmadan önce yerel bilgisayarda eklenti aracını yükleyin ve derlemesi yüklenemiyor.

**Ad** -dize Windows PowerShell ISE'ye eklenen eklenti aracını görünen adını belirtir.

**ControlType** -eklenen denetim türünü belirtir.

**\[IsVisible\]**  -isteğe bağlı Boolean ayarlayın **$true**, eklenti aracını hemen ilişkili araç bölmesinde görünür.

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="remove-item-"></a>Kaldırma\( öğesi \)

Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.

Belirtilen eklenti aracını koleksiyondan kaldırır.

**Öğe** -Microsoft.PowerShell.Host.ISE.ISEAddOnTool Windows PowerShell ISE'den kaldırılacak nesne belirtir.

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="setselectedpowershelltab-pstab-"></a>SetSelectedPowerShellTab\( psTab \)

Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.

PowerShell'i seçer sekmesinde **psTab** parametre belirtir.

**psTab** -Microsoft.PowerShell.Host.ISE.PowerShellTab PowerShell sekmesini seçin.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="remove-pstab-"></a>Kaldırma\( psTab \)

Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.

PowerShell kaldırır sekmesinde **psTab** parametre belirtir.

**psTab** -kaldırmak için sekmesinde Microsoft.PowerShell.Host.ISE.PowerShellTab PowerShell.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

## <a name="see-also"></a>Ayrıca bkz:

- [PowerShellTab nesnesi](The-PowerShellTab-Object.md)
- [Windows PowerShell ISE betik oluşturma nesne modelinin amacı](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [ISE Nesne Modeli Hiyerarşisi](The-ISE-Object-Model-Hierarchy.md)