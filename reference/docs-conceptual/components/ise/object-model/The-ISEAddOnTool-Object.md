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
# <a name="the-iseaddontool-object"></a><span data-ttu-id="3ac98-103">ISEAddOnTool Nesnesi</span><span class="sxs-lookup"><span data-stu-id="3ac98-103">The ISEAddOnTool Object</span></span>

<span data-ttu-id="3ac98-104">Bir **Iseaddontool** nesne ek işlevler Windows PowerShell ISE sağlayan bir yüklü eklenti aracını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3ac98-104">An **ISEAddonTool** object represents an installed add-on tool that provides additional functionality toWindows PowerShell ISE.</span></span> <span data-ttu-id="3ac98-105">Bir örnek **komutları** tıklayarak görüntüleyebilirsiniz. aracı **görünümü**, ardından **Göster komutu eklenti**.</span><span class="sxs-lookup"><span data-stu-id="3ac98-105">An example is the **Commands** tool that you can display by clicking **View**, then **Show Command Add-on**.</span></span> <span data-ttu-id="3ac98-106">Ardından çeşitli kullanılabilir işleyerek bu araç için erişilebilir olduğundan **Iseaddontool** nesneleri.</span><span class="sxs-lookup"><span data-stu-id="3ac98-106">This tool is then accessible to you by manipulating the various available **ISEAddOnTool** objects.</span></span>

<span data-ttu-id="3ac98-107">Her eklenti aracını bölmeyi dikey veya yatay bölme ile ilişkili olabilir.</span><span class="sxs-lookup"><span data-stu-id="3ac98-107">Each add-on tool can be associated with either the vertical pane or the horizontal pane.</span></span> <span data-ttu-id="3ac98-108">Dikey bölme için Windows PowerShell ISE öğenin sağ kenarı yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="3ac98-108">The vertical pane is docked to the right edge of Windows PowerShell ISE.</span></span> <span data-ttu-id="3ac98-109">Yatay bölme için alt kenarı yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="3ac98-109">The horizontal pane is docked to the bottom edge.</span></span>

<span data-ttu-id="3ac98-110">Windows PowerShell ıse'de her PowerShell sekme kendi yüklü eklenti araçları kümesine sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="3ac98-110">Each PowerShell tab in Windows PowerShell ISE can have its own set of add-on tools installed.</span></span> <span data-ttu-id="3ac98-111">Bkz: [$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-PowerShellTab-Object.md) ve [$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-PowerShellTab-Object.md) koleksiyonu şu anda seçilen sekmesi için kullanılabilen araçlara erişmek için veya biriyle aynı özellikleri **PowerShellTab** nesneler [$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md) koleksiyon nesnesi.</span><span class="sxs-lookup"><span data-stu-id="3ac98-111">See [$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-PowerShellTab-Object.md) and [$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-PowerShellTab-Object.md) to access the collection of tools available to the currently selected tab or the same properties on any of the **PowerShellTab** objects in the [$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md) collection object.</span></span>

## <a name="methods"></a><span data-ttu-id="3ac98-112">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="3ac98-112">Methods</span></span>

<span data-ttu-id="3ac98-113">Bu sınıfın nesneleri için kullanılabilen hiçbir Windows PowerShell ISE özgü bu yöntemler vardır.</span><span class="sxs-lookup"><span data-stu-id="3ac98-113">There are no Windows PowerShell ISE-specific methods available for objects of this class.</span></span>

## <a name="properties"></a><span data-ttu-id="3ac98-114">Özellikler</span><span class="sxs-lookup"><span data-stu-id="3ac98-114">Properties</span></span>

### <a name="control"></a><span data-ttu-id="3ac98-115">Denetim</span><span class="sxs-lookup"><span data-stu-id="3ac98-115">Control</span></span>

<span data-ttu-id="3ac98-116">Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="3ac98-116">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="3ac98-117">**Denetimi** özelliği komutları eklenti Aracı'nın ayrıntılarına yönelik okuma erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="3ac98-117">The **Control** property provides read access to many of the details of the Commands add-on tool.</span></span>

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

### <a name="isvisible"></a><span data-ttu-id="3ac98-118">IsVisible</span><span class="sxs-lookup"><span data-stu-id="3ac98-118">IsVisible</span></span>

<span data-ttu-id="3ac98-119">Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="3ac98-119">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="3ac98-120">Eklenti aracını atanan alt bölmede görünür olup olmadığını belirten Boolean özelliği.</span><span class="sxs-lookup"><span data-stu-id="3ac98-120">The Boolean property that indicates whether the add-on tool is currently visible in its assigned pane.</span></span> <span data-ttu-id="3ac98-121">Görünür durumdaysa ayarlayabileceğiniz **IsVisible** özelliğini **$false** aracı Gizle veya ayarlamak için **IsVisible** özelliğini **$true** yapma bir eklenti aracı kendi PowerShell sekmesinde görünür. Bir eklenti aracını gizli sonra artık erişilebilir olmadığını unutmayın **CurrentVisibleHorizontalTool** veya **CurrentVisibleVerticalTool** nesneleri ve bu nedenle kullanarak görünür yapılamaz Bu nesne bu özelliği.</span><span class="sxs-lookup"><span data-stu-id="3ac98-121">If it is visible, you can set the **IsVisible** property to **$false** to hide the tool, or set the **IsVisible** property to **$true** to make an add-on tool visible on its PowerShell tab. Note that after an add-on tool is hidden, it is no longer accessible through the **CurrentVisibleHorizontalTool** or **CurrentVisibleVerticalTool** objects, and therefore cannot be made visible by using this property on that object.</span></span>

```powershell
# Hide the current tool in the vertical tool pane
$psISE.CurrentVisibleVerticalTool.IsVisible = $false
# Show the first tool on the currently selected PowerShell tab
$psISE.CurrentPowerShellTab.VerticalAddOnTools[0].IsVisible = $true
```

### <a name="name"></a><span data-ttu-id="3ac98-122">Adı</span><span class="sxs-lookup"><span data-stu-id="3ac98-122">Name</span></span>

<span data-ttu-id="3ac98-123">Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="3ac98-123">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="3ac98-124">Eklenti Aracı'nın adı salt okunur özelliği.</span><span class="sxs-lookup"><span data-stu-id="3ac98-124">The read-only property that gets the name of the add-on tool.</span></span>

```powershell
# Gets the name of the visible vertical pane add-on tool.
$psISE.CurrentVisibleVerticalTool.Name
Commands
```

## <a name="see-also"></a><span data-ttu-id="3ac98-125">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="3ac98-125">See Also</span></span>

- [<span data-ttu-id="3ac98-126">Iseaddontoolcollection nesnesi</span><span class="sxs-lookup"><span data-stu-id="3ac98-126">The ISEAddOnToolCollection Object</span></span>](The-ISEAddOnToolCollection-Object.md)
- [<span data-ttu-id="3ac98-127">Windows PowerShell ISE betik oluşturma nesne modelinin amacı</span><span class="sxs-lookup"><span data-stu-id="3ac98-127">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="3ac98-128">ISE Nesne Modeli Hiyerarşisi</span><span class="sxs-lookup"><span data-stu-id="3ac98-128">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)