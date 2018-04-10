---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: ISEAddOnTool Nesnesi
ms.assetid: ce84d8bc-07ba-41f6-bdde-d6f3fddcd1e3
ms.openlocfilehash: e091f37601c7a4fdaf5deff8c668b18ee7369e74
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="the-iseaddontool-object"></a>ISEAddOnTool Nesnesi

Bir **ISEAddonTool** nesnesi ek işlevler Windows PowerShell ISE sağlayan bir yüklü eklenti araç temsil eder. Örnek **komutları** tıklatarak görüntüleyebileceğiniz aracı **Görünüm**, ardından **Göster komutu eklenti**. Bu araç ardından çeşitli kullanılabilir işleyerek erişilir **ISEAddOnTool** nesneleri.

Her eklenti aracı Dikey bölme veya yatay bölme ile ilişkili olabilir. Dikey bölme Windows PowerShell ISE sağ kenarı yerleştirilir. Yatay bölme alt kenarı yerleştirilir.

Windows PowerShell ISE her bir PowerShell sekmede eklenti araçları yüklü kendi kümesi olabilir. Bkz: [$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-PowerShellTab-Object.md) ve [$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-PowerShellTab-Object.md) şu anda seçili sekmesinde kullanılabilen araçlar koleksiyonuna erişmek için veya herhangi bir aynı özellikleri **PowerShellTab** nesnelerini [$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md) koleksiyon nesnesi.

## <a name="methods"></a>Yöntemler

Bu sınıfın nesneleri için kullanılabilir Windows PowerShell ISE özgü yöntemlerin hiçbiri yok.

## <a name="properties"></a>Özellikler

### <a name="control"></a>Denetim

Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.

**Denetim** özelliği komutları eklenti aracının ayrıntılarına yönelik okuma erişimi sağlar.

```powershell
# View the properties of the Commands add-on tool.
# (assumes that it is visible in the vertical pane)
$psISE.CurrentVisibleVerticalTool.Control
HostObject                  : Microsoft.PowerShell.Host.ISE.ObjectModelRoot
Content                     :
HasContent                  :
ContentTemplate             :
ContentTemplateSelector     :
ContentStringFormat         :
BorderBrush                 :
BorderThickness             :
Background                  :
Foreground                  :
FontFamily                  :
FontSize                    :
FontStretch                 :
FontStyle                   :
FontWeight                  :
HorizontalContentAlignment  :
VerticalContentAlignment    :
TabIndex                    :
IsTabStop                   :
Padding                     :
Template                    : System.Windows.Controls.ControlTemplate
Style                       :
OverridesDefaultStyle       :
UseLayoutRounding           :
Triggers                    : {}
TemplatedParent             :
Resources                   : {System.Windows.Controls.TabItem}
DataContext                 :
BindingGroup                :
Language                    :
Name                        :
Tag                         :
InputScope                  :
ActualWidth                 : 370.75
ActualHeight                : 676.559097412109
LayoutTransform             :
Width                       :
MinWidth                    :
MaxWidth                    :
Height                      :
MinHeight                   :
MaxHeight                   :
FlowDirection               : LeftToRight
Margin                      :
HorizontalAlignment         :
VerticalAlignment           :
FocusVisualStyle            :
Cursor                      :
ForceCursor                 :
IsInitialized               : True
IsLoaded                    :
ToolTip                     :
ContextMenu                 :
Parent                      :
HasAnimatedProperties       :
InputBindings               :
CommandBindings             :
AllowDrop                   :
DesiredSize                 : 227.66,676.559097412109
IsMeasureValid              : True
IsArrangeValid              : True
RenderSize                  : 370.75,676.559097412109
RenderTransform             :
RenderTransformOrigin       :
IsMouseDirectlyOver         : False
IsMouseOver                 : False
IsStylusOver                : False
IsKeyboardFocusWithin       : False
IsMouseCaptured             :
IsMouseCaptureWithin        : False
IsStylusDirectlyOver        : False
IsStylusCaptured            :
IsStylusCaptureWithin       : False
IsKeyboardFocused           : False
IsInputMethodEnabled        :
Opacity                     :
OpacityMask                 :
BitmapEffect                :
Effect                      :
BitmapEffectInput           :
CacheMode                   :
Uid                         :
Visibility                  : Visible
ClipToBounds                : False
Clip                        :
SnapsToDevicePixels         : False
IsFocused                   :
IsEnabled                   :
IsHitTestVisible            :
IsVisible                   : True
Focusable                   :
PersistId                   : 1
IsManipulationEnabled       :
AreAnyTouchesOver           : False
AreAnyTouchesDirectlyOver   :
AreAnyTouchesCapturedWithin : False
AreAnyTouchesCaptured       :
TouchesCaptured             : {}
TouchesCapturedWithin       : {}
TouchesOver                 : {}
TouchesDirectlyOver         : {}
DependencyObjectType        : System.Windows.DependencyObjectType
IsSealed                    : False
Dispatcher                  : System.Windows.Threading.Dispatcher
```

### <a name="isvisible"></a>IsVisible

Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.

Eklenti aracı şu anda atanmış bölmesinde görünür olup olmadığını belirten Boolean özelliği. Görünür durumdaysa ayarlayabileceğiniz **IsVisible** özelliğine **$false** aracı Gizle veya ayarlamak için **IsVisible** özelliğine **$true** yapmak için bir eklenti aracı kendi PowerShell sekmesinde görünür. Bir eklenti aracı gizli sonra onu artık üzerinden erişilebilir olduğunu unutmayın **CurrentVisibleHorizontalTool** veya **CurrentVisibleVerticalTool** nesneleri ve bu nedenle kullanarak görünür kurulamaz Bu özellik bu nesne üzerinde.

```powershell
# Hide the current tool in the vertical tool pane
$psISE.CurrentVisibleVerticalTool.IsVisible = $false
# Show the first tool on the currently selected PowerShell tab
$psISE.CurrentPowerShellTab.VerticalAddOnTools[0].IsVisible = $true
```

### <a name="name"></a>Ad

Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.

Eklenti aracı adını alır salt okunur özellik.

```powershell
# Gets the name of the visible vertical pane add-on tool.
$psISE.CurrentVisibleVerticalTool.Name
Commands
```

## <a name="see-also"></a>Ayrıca bkz:

- [The ISEAddOnToolCollection Object](The-ISEAddOnToolCollection-Object.md)
- [Nesne modeli komut dosyası Windows PowerShell ISE amacı](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [ISE Nesne Modeli Hiyerarşisi](The-ISE-Object-Model-Hierarchy.md)