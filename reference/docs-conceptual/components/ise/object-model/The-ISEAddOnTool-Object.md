---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: ISEAddOnTool Nesnesi
ms.assetid: ce84d8bc-07ba-41f6-bdde-d6f3fddcd1e3
ms.openlocfilehash: e091f37601c7a4fdaf5deff8c668b18ee7369e74
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086808"
---
# <a name="the-iseaddontool-object"></a>ISEAddOnTool Nesnesi

Bir **Iseaddontool** nesne ek işlevler Windows PowerShell ISE sağlayan bir yüklü eklenti aracını temsil eder. Bir örnek **komutları** tıklayarak görüntüleyebilirsiniz. aracı **görünümü**, ardından **Göster komutu eklenti**. Ardından çeşitli kullanılabilir işleyerek bu araç için erişilebilir olduğundan **Iseaddontool** nesneleri.

Her eklenti aracını bölmeyi dikey veya yatay bölme ile ilişkili olabilir. Dikey bölme için Windows PowerShell ISE öğenin sağ kenarı yerleştirilir. Yatay bölme için alt kenarı yerleştirilir.

Windows PowerShell ıse'de her PowerShell sekme kendi yüklü eklenti araçları kümesine sahip olabilir. Bkz: [$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-PowerShellTab-Object.md) ve [$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-PowerShellTab-Object.md) koleksiyonu şu anda seçilen sekmesi için kullanılabilen araçlara erişmek için veya biriyle aynı özellikleri **PowerShellTab** nesneler [$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md) koleksiyon nesnesi.

## <a name="methods"></a>Yöntemler

Bu sınıfın nesneleri için kullanılabilen hiçbir Windows PowerShell ISE özgü bu yöntemler vardır.

## <a name="properties"></a>Özellikler

### <a name="control"></a>Denetim

Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.

**Denetimi** özelliği komutları eklenti Aracı'nın ayrıntılarına yönelik okuma erişimi sağlar.

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

Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.

Eklenti aracını atanan alt bölmede görünür olup olmadığını belirten Boolean özelliği. Görünür durumdaysa ayarlayabileceğiniz **IsVisible** özelliğini **$false** aracı Gizle veya ayarlamak için **IsVisible** özelliğini **$true** yapma bir eklenti aracı kendi PowerShell sekmesinde görünür. Bir eklenti aracını gizli sonra artık erişilebilir olmadığını unutmayın **CurrentVisibleHorizontalTool** veya **CurrentVisibleVerticalTool** nesneleri ve bu nedenle kullanarak görünür yapılamaz Bu nesne bu özelliği.

```powershell
# Hide the current tool in the vertical tool pane
$psISE.CurrentVisibleVerticalTool.IsVisible = $false
# Show the first tool on the currently selected PowerShell tab
$psISE.CurrentPowerShellTab.VerticalAddOnTools[0].IsVisible = $true
```

### <a name="name"></a>Adı

Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.

Eklenti Aracı'nın adı salt okunur özelliği.

```powershell
# Gets the name of the visible vertical pane add-on tool.
$psISE.CurrentVisibleVerticalTool.Name
Commands
```

## <a name="see-also"></a>Ayrıca bkz:

- [Iseaddontoolcollection nesnesi](The-ISEAddOnToolCollection-Object.md)
- [Windows PowerShell ISE betik oluşturma nesne modelinin amacı](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [ISE Nesne Modeli Hiyerarşisi](The-ISE-Object-Model-Hierarchy.md)