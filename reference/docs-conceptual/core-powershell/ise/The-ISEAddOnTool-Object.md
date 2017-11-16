---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: ISEAddOnTool nesnesi
ms.assetid: ce84d8bc-07ba-41f6-bdde-d6f3fddcd1e3
ms.openlocfilehash: b813fcac547c8069e84741081a3ceb00044bab87
ms.sourcegitcommit: 3720ce4efb6735694cfb53a1b793d949af5d1bc5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/29/2017
---
# <a name="the-iseaddontool-object"></a><span data-ttu-id="d4853-103">ISEAddOnTool nesnesi</span><span class="sxs-lookup"><span data-stu-id="d4853-103">The ISEAddOnTool Object</span></span>
  <span data-ttu-id="d4853-104">Bir **ISEAddonTool** nesnesi ek işlevler Windows PowerShell ISE sağlayan bir yüklü eklenti araç temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d4853-104">An **ISEAddonTool** object represents an installed add-on tool that provides additional functionality toWindows PowerShell ISE.</span></span> <span data-ttu-id="d4853-105">Örnek **komutları** tıklatarak görüntüleyebileceğiniz aracı **Görünüm**, ardından **Göster komutu eklenti**.</span><span class="sxs-lookup"><span data-stu-id="d4853-105">An example is the **Commands** tool that you can display by clicking **View**, then **Show Command Add-on**.</span></span> <span data-ttu-id="d4853-106">Bu araç ardından çeşitli kullanılabilir işleyerek erişilir **ISEAddOnTool** nesneleri.</span><span class="sxs-lookup"><span data-stu-id="d4853-106">This tool is then accessible to you by manipulating the various available **ISEAddOnTool** objects.</span></span>

 <span data-ttu-id="d4853-107">Her eklenti aracı Dikey bölme veya yatay bölme ile ilişkili olabilir.</span><span class="sxs-lookup"><span data-stu-id="d4853-107">Each add-on tool can be associated with either the vertical pane or the horizontal pane.</span></span> <span data-ttu-id="d4853-108">Dikey bölme Windows PowerShell ISE sağ kenarı yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="d4853-108">The vertical pane is docked to the right edge of Windows PowerShell ISE.</span></span> <span data-ttu-id="d4853-109">Yatay bölme alt kenarı yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="d4853-109">The horizontal pane is docked to the bottom edge.</span></span>

 <span data-ttu-id="d4853-110">Windows PowerShell ISE her bir PowerShell sekmede eklenti araçları yüklü kendi kümesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="d4853-110">Each PowerShell tab in Windows PowerShell ISE can have its own set of add-on tools installed.</span></span> <span data-ttu-id="d4853-111">Bkz: [$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-PowerShellTab-Object.md) ve [$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-PowerShellTab-Object.md) şu anda seçili sekmesinde kullanılabilen araçlar koleksiyonuna erişmek için veya herhangi bir aynı özellikleri **PowerShellTab** nesnelerini [$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md) koleksiyon nesnesi.</span><span class="sxs-lookup"><span data-stu-id="d4853-111">See [$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-PowerShellTab-Object.md) and [$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-PowerShellTab-Object.md) to access the collection of tools available to the currently selected tab or the same properties on any of the **PowerShellTab** objects in the [$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md) collection object.</span></span>

## <a name="methods"></a><span data-ttu-id="d4853-112">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d4853-112">Methods</span></span>
 <span data-ttu-id="d4853-113">Bu sınıfın nesneleri için kullanılabilir Windows PowerShell ISE özgü yöntemlerin hiçbiri yok.</span><span class="sxs-lookup"><span data-stu-id="d4853-113">There are no Windows PowerShell ISE-specific methods available for objects of this class.</span></span>

## <a name="properties"></a><span data-ttu-id="d4853-114">Özellikler</span><span class="sxs-lookup"><span data-stu-id="d4853-114">Properties</span></span>

### <a name="control"></a><span data-ttu-id="d4853-115">Denetim</span><span class="sxs-lookup"><span data-stu-id="d4853-115">Control</span></span>
  <span data-ttu-id="d4853-116">Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="d4853-116">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="d4853-117">**Denetim** özelliği komutları eklenti aracının ayrıntılarına yönelik okuma erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d4853-117">The **Control** property provides read access to many of the details of the Commands add-on tool.</span></span>

```
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

### <a name="isvisible"></a><span data-ttu-id="d4853-118">IsVisible</span><span class="sxs-lookup"><span data-stu-id="d4853-118">IsVisible</span></span>
  <span data-ttu-id="d4853-119">Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="d4853-119">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="d4853-120">Eklenti aracı şu anda atanmış bölmesinde görünür olup olmadığını belirten Boolean özelliği.</span><span class="sxs-lookup"><span data-stu-id="d4853-120">The Boolean property that indicates whether the add-on tool is currently visible in its assigned pane.</span></span> <span data-ttu-id="d4853-121">Görünür durumdaysa ayarlayabileceğiniz **IsVisible** özelliğine **$false** aracı Gizle veya ayarlamak için **IsVisible** özelliğine **$true** yapmak için bir eklenti aracı kendi PowerShell sekmesinde görünür. Bir eklenti aracı gizli sonra onu artık üzerinden erişilebilir olduğunu unutmayın **CurrentVisibleHorizontalTool** veya **CurrentVisibleVerticalTool** nesneleri ve bu nedenle kullanarak görünür kurulamaz Bu özellik bu nesne üzerinde.</span><span class="sxs-lookup"><span data-stu-id="d4853-121">If it is visible, you can set the **IsVisible** property to **$false** to hide the tool, or set the **IsVisible** property to **$true** to make an add-on tool visible on its PowerShell tab. Note that after an add-on tool is hidden, it is no longer accessible through the **CurrentVisibleHorizontalTool** or **CurrentVisibleVerticalTool** objects, and therefore cannot be made visible by using this property on that object.</span></span>

```
# Hide the current tool in the vertical tool pane
$psISE.CurrentVisibleVerticalTool.IsVisible = $false
# Show the first tool on the currently selected PowerShell tab
$psISE.CurrentPowerShellTab.VerticalAddOnTools[0].IsVisible=$true

```

### <a name="name"></a><span data-ttu-id="d4853-122">Ad</span><span class="sxs-lookup"><span data-stu-id="d4853-122">Name</span></span>
  <span data-ttu-id="d4853-123">Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="d4853-123">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="d4853-124">Eklenti aracı adını alır salt okunur özellik.</span><span class="sxs-lookup"><span data-stu-id="d4853-124">The read-only property that gets the name of the add-on tool.</span></span>

```
# Gets the name of the visible vertical pane add-on tool.
$psISE.CurrentVisibleVerticalTool.name
Commands

```

## <a name="see-also"></a><span data-ttu-id="d4853-125">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="d4853-125">See Also</span></span>
- [<span data-ttu-id="d4853-126">ISEAddOnToolCollection nesnesi</span><span class="sxs-lookup"><span data-stu-id="d4853-126">The ISEAddOnToolCollection Object</span></span>](The-ISEAddOnToolCollection-Object.md)
- [<span data-ttu-id="d4853-127">Windows PowerShell ISE nesne modeli komut dosyası oluşturma</span><span class="sxs-lookup"><span data-stu-id="d4853-127">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="d4853-128">Windows PowerShell ISE nesne modeli başvurusu</span><span class="sxs-lookup"><span data-stu-id="d4853-128">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md)
- [<span data-ttu-id="d4853-129">ISE nesne modeli hiyerarşisi</span><span class="sxs-lookup"><span data-stu-id="d4853-129">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

