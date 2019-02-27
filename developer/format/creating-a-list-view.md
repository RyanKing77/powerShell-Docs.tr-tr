---
title: Bir liste görünümü oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c7a40ca-1786-46f0-bab5-6ce229daa7ee
caps.latest.revision: 14
ms.openlocfilehash: 25d24063501196d44e0f806a55bb699c82f771ce
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850718"
---
# <a name="creating-a-list-view"></a><span data-ttu-id="1d0ab-102">Liste Görünümü Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1d0ab-102">Creating a List View</span></span>

<span data-ttu-id="1d0ab-103">Bir liste görünümü verilerini tek bir sütunda (sırayla) görüntüler.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-103">A list view displays data in a single column (in sequential order).</span></span> <span data-ttu-id="1d0ab-104">Listede görüntülenen verileri, bir .NET özelliğinin değerini veya bir betik değeri olabilir.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-104">The data displayed in the list can be the value of a .NET property or the value of a script.</span></span>

## <a name="a-list-view-display"></a><span data-ttu-id="1d0ab-105">Bir liste görünümü görüntüleme</span><span class="sxs-lookup"><span data-stu-id="1d0ab-105">A List View Display</span></span>

<span data-ttu-id="1d0ab-106">Aşağıdaki çıktı, Windows PowerShell özelliklerinin nasıl görüntülediğini gösterir [System.Serviceprocess.Servicecontroller? Displayproperty Fullname =](/dotnet/api/System.ServiceProcess.ServiceController) tarafından döndürülen nesneleri [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-106">The following output shows how Windows PowerShell displays the properties of [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects that are returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="1d0ab-107">Bu örnekte, üç nesneler, önceki nesneden boş bir satır tarafından ayrılmış her bir nesne ile döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-107">In this example, three objects were returned, with each object separated from the preceding object by a blank line.</span></span>

```powershell
Get-Service | format-list
```

```output
Name                : AEADIFilters
DisplayName         : Andrea ADI Filters Service
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32OwnProcess

Name                : AeLookupSvc
DisplayName         : Application Experience
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32ShareProcess

Name                : AgereModemAudio
DisplayName         : Agere Modem Call Progress Audio
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32OwnProcess
...
```

## <a name="defining-the-list-view"></a><span data-ttu-id="1d0ab-108">Liste görünümü tanımlama</span><span class="sxs-lookup"><span data-stu-id="1d0ab-108">Defining the List View</span></span>

<span data-ttu-id="1d0ab-109">Aşağıdaki XML çeşitli özelliklerini görüntülemek için liste görünümü şeması gösterir [System.Serviceprocess.Servicecontroller? Displayproperty Fullname =](/dotnet/api/System.ServiceProcess.ServiceController) nesne.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-109">The following XML shows the list view schema for displaying several properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="1d0ab-110">Liste görünümünde görüntülenmesini istediğiniz her bir özellik belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-110">You must specify each property that you want displayed in the list view.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>
          <ListItem>
            <PropertyName>Name</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>DisplayName</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>Status</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>ServiceType</PropertyName>
          </ListItem>
        </ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

<span data-ttu-id="1d0ab-111">Aşağıdaki XML öğeleri, bir liste görünümü tanımlamak için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="1d0ab-111">The following XML elements are used to define a list view:</span></span>

- <span data-ttu-id="1d0ab-112">[Görünümü](./view-element-format.md) liste görünümü üst öğesinin bir öğedir.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-112">The [View](./view-element-format.md) element is the parent element of the list view.</span></span> <span data-ttu-id="1d0ab-113">(Aynı üst öğeye tablosu, geniş ve özel denetim görünümleri için budur.)</span><span class="sxs-lookup"><span data-stu-id="1d0ab-113">(This is the same parent element for the table, wide, and custom control views.)</span></span>

- <span data-ttu-id="1d0ab-114">[Adı](./name-element-for-view-format.md) öğesi, görünümün adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-114">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="1d0ab-115">Bu öğe tüm görünümleri için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-115">This element is required for all views.</span></span>

- <span data-ttu-id="1d0ab-116">[ViewSelectedBy](./viewselectedby-element-format.md) öğe görünümünü kullanın nesneleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-116">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="1d0ab-117">Bu öğe gereklidir.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-117">This element is required.</span></span>

- <span data-ttu-id="1d0ab-118">[GroupBy](./groupby-element-for-view-format.md) öğe yeni bir grup nesne görüntülendiğinde tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-118">The [GroupBy](./groupby-element-for-view-format.md) element defines when a new group of objects is displayed.</span></span> <span data-ttu-id="1d0ab-119">Bir özel özellik veya betik değeri değiştiğinde yeni bir grup başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-119">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="1d0ab-120">Bu öğe isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-120">This element is optional.</span></span>

- <span data-ttu-id="1d0ab-121">[Denetimleri](./controls-element-for-view-format.md) öğe listesi görünümü tarafından tanımlanan özel denetimleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-121">The [Controls](./controls-element-for-view-format.md) element defines the custom controls that are defined by the list view.</span></span> <span data-ttu-id="1d0ab-122">Denetimler, daha fazla verinin nasıl görüntüleneceğini belirtmek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-122">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="1d0ab-123">Bu öğe isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-123">This element is optional.</span></span> <span data-ttu-id="1d0ab-124">Bir görünüm kendi özel denetimler tanımlayabilirsiniz veya biçimlendirme dosyasında herhangi bir görünüm tarafından kullanılabilen ortak denetimleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-124">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="1d0ab-125">Özel denetimler hakkında daha fazla bilgi için bkz: [özel denetimler oluşturma](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="1d0ab-125">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="1d0ab-126">[ListControl](./listcontrol-element-format.md) nasıl biçimlendirildiğini ve ne görünümünde görüntülenen öğe tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-126">The [ListControl](./listcontrol-element-format.md) element defines what is displayed in the view and how it is formatted.</span></span> <span data-ttu-id="1d0ab-127">Diğer tüm görünümlere benzer bir liste görünümü nesne özelliklerin değerlerini veya komut dosyası tarafından oluşturulan değerleri görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-127">Similar to all other views, a list view can display the values of object properties or values generated by script.</span></span>

<span data-ttu-id="1d0ab-128">Basit Liste Görünümü tanımlayan bir tam biçimlendirme dosyası örneği için bkz: [liste görünümü (Temel)](./list-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="1d0ab-128">For an example of a complete formatting file that defines a simple list view, see [List View (Basic)](./list-view-basic.md).</span></span>

## <a name="providing-definitions-for-your-list-view"></a><span data-ttu-id="1d0ab-129">Liste Görünümü tanımlarında sağlama</span><span class="sxs-lookup"><span data-stu-id="1d0ab-129">Providing Definitions for Your List View</span></span>

<span data-ttu-id="1d0ab-130">Liste görünümleri, alt öğelerini kullanarak bir veya daha fazla tanımları sağlayabilir [ListControl](./listcontrol-element-format.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-130">List views can provide one or more definitions by using the child elements of the [ListControl](./listcontrol-element-format.md) element.</span></span> <span data-ttu-id="1d0ab-131">Genellikle, bir görünümü sadece bir tanım sahip olacaktır.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-131">Typically, a view will have only one definition.</span></span> <span data-ttu-id="1d0ab-132">Aşağıdaki örnekte, çeşitli özelliklerini görüntüler tek bir tanım görünümü sağlar [System.Diagnostics.Process? Displayproperty Fullname =](/dotnet/api/System.Diagnostics.Process) nesne.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-132">In the following example, the view provides a single definition that displays several properties of the [System.Diagnostics.Process?Displayproperty=Fullname](/dotnet/api/System.Diagnostics.Process) object.</span></span> <span data-ttu-id="1d0ab-133">Bir liste görünümü, bir özelliğin değerini veya bir betik (örnekte gösterilmiştir değil) değerini görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-133">A list view can display the value of a property or the value of a script (not shown in the example).</span></span>

```xml
<ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>
          <ListItem>
            <PropertyName>Name</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>DisplayName</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>Status</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>ServiceType</PropertyName>
          </ListItem>
        </ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>

```

<span data-ttu-id="1d0ab-134">Aşağıdaki XML öğeleri, bir liste görünümü tanımlarında sağlamak için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="1d0ab-134">The following XML elements can be used to provide definitions for a list view:</span></span>

- <span data-ttu-id="1d0ab-135">[ListControl](./listcontrol-element-format.md) öğesi ve onun alt öğeleri tanımlayan ne Görünümü'nde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-135">The [ListControl](./listcontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span>

- <span data-ttu-id="1d0ab-136">[ListEntries](./listentries-element-for-listcontrol-format.md) öğesi, görünümün tanımını sağlar.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-136">The [ListEntries](./listentries-element-for-listcontrol-format.md) element provides the definitions of the view.</span></span> <span data-ttu-id="1d0ab-137">Çoğu durumda, yalnızca bir tanımı bir görünüm olacaktır.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-137">In most cases, a view will have only one definition.</span></span> <span data-ttu-id="1d0ab-138">Bu öğe gereklidir.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-138">This element is required.</span></span>

- <span data-ttu-id="1d0ab-139">[ListEntry](./listentry-element-for-listcontrol-format.md) öğesi, görünümün tanımını sağlar.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-139">The [ListEntry](./listentry-element-for-listcontrol-format.md) element provides a definition of the view.</span></span> <span data-ttu-id="1d0ab-140">En az bir [ListEntry](./listentry-element-for-listcontrol-format.md) gereklidir; ancak, hiçbir ekleyebileceğiniz öğe sayısı üst sınırı yoktur.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-140">At least one [ListEntry](./listentry-element-for-listcontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="1d0ab-141">Çoğu durumda, yalnızca bir tanımı bir görünüm olacaktır.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-141">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="1d0ab-142">[EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) öğesi, belirli bir tanımı tarafından görüntülenen nesneleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-142">The [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="1d0ab-143">Bu öğe isteğe bağlıdır ve yalnızca birden çok tanımlarken gerekli [ListEntry](./listentry-element-for-listcontrol-format.md) görüntüleme farklı nesneleri öğeleri.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-143">This element is optional and is needed only when you define multiple [ListEntry](./listentry-element-for-listcontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="1d0ab-144">[ListItems](./listitems-element-for-listentry-for-listcontrol-format.md) öğesi betikleri değerleri, liste görünümü satırlarda görüntülenir ve özelliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-144">The [ListItems](./listitems-element-for-listentry-for-listcontrol-format.md) element specifies the properties and scripts whose values are displayed in the rows of the list view.</span></span>

- <span data-ttu-id="1d0ab-145">[ListItem](./listitems-element-for-listentry-for-listcontrol-format.md) öğeyi belirten bir özellik veya betik değeri liste görünümünün bir satır görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-145">The [ListItem](./listitems-element-for-listentry-for-listcontrol-format.md) element specifies a property or script whose value is displayed in a row of the list view.</span></span> <span data-ttu-id="1d0ab-146">Bir liste görünümü, en az bir özellik ya da komut dosyasını belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-146">A list view must specify at least one property or script.</span></span> <span data-ttu-id="1d0ab-147">Belirtilen satır sayısı maksimum sınırı yoktur.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-147">There is no maximum limit to the number of rows that can be specified.</span></span>

- <span data-ttu-id="1d0ab-148">[PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) öğesi değeri satır içinde görüntülenen özelliği belirtir.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-148">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="1d0ab-149">Bir özellik ya da bir komut dosyası belirtmeniz gerekir, ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-149">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="1d0ab-150">[ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) öğesi değeri satır içinde görüntülenen komut dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-150">The [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="1d0ab-151">Bir betik ya da bir özellik belirtmeniz gerekir, ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-151">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="1d0ab-152">[Etiket](./label-element-for-listitem-for-listcontrol-format.md) öğesi sıradaki özelliği veya betik değer solunda görüntülenen etiketi belirtir.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-152">The [Label](./label-element-for-listitem-for-listcontrol-format.md) element specifies the label that is displayed to the left of the property or script value in the row.</span></span> <span data-ttu-id="1d0ab-153">Bu öğe isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-153">This element is optional.</span></span> <span data-ttu-id="1d0ab-154">Bir etiket belirtilmezse, özelliği veya komut dosyası adı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-154">If a label is not specified, the name of the property or the script is displayed.</span></span> <span data-ttu-id="1d0ab-155">Tam bir örnek için bkz. [liste görünümü (etiketler)](./list-view-labels.md).</span><span class="sxs-lookup"><span data-stu-id="1d0ab-155">For a complete example, see [List View (Labels)](./list-view-labels.md).</span></span>

- <span data-ttu-id="1d0ab-156">[ItemSelectionCondition](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) öğesi görüntülenecek satır için bulunması gereken bir koşulu belirtir.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-156">The [ItemSelectionCondition](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) element specifies a condition that must exist for the row to be displayed.</span></span> <span data-ttu-id="1d0ab-157">Liste görünümüne koşul ekleme hakkında daha fazla bilgi için bkz. [görüntüleyen veri koşulları tanımlama](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="1d0ab-157">For more information about adding conditions to the list view, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span> <span data-ttu-id="1d0ab-158">Bu öğe isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-158">This element is optional.</span></span>

- <span data-ttu-id="1d0ab-159">[FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) öğesi özelliği veya komut dosyası değerini görüntülemek için kullanılan bir desen belirtir.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-159">The [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) element specifies a pattern that is used to display the value of the property or script.</span></span> <span data-ttu-id="1d0ab-160">Bu öğe isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-160">This element is optional.</span></span>

<span data-ttu-id="1d0ab-161">Basit Liste Görünümü tanımlayan bir tam biçimlendirme dosyası örneği için bkz: [liste görünümü (Temel)](./list-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="1d0ab-161">For an example of a complete formatting file that defines a simple list view, see [List View (Basic)](./list-view-basic.md).</span></span>

## <a name="defining-the-objects-that-use-the-list-view"></a><span data-ttu-id="1d0ab-162">Liste görünümüne kullanan nesneler tanımlama</span><span class="sxs-lookup"><span data-stu-id="1d0ab-162">Defining the Objects That Use the List View</span></span>

<span data-ttu-id="1d0ab-163">Liste görünümüne hangi .NET nesnelerini kullanmak tanımlamak için iki yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-163">There are two ways to define which .NET objects use the list view.</span></span> <span data-ttu-id="1d0ab-164">Kullanabileceğiniz [ViewSelectedBy](./viewselectedby-element-format.md) görünümü veya tüm tanımları tarafından görüntülenebilen nesneler tanımlamak için kullanabileceğiniz [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) hangi nesnelerin tarafından görüntülenen tanımlamak için bir Belirli görünüm tanımı.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-164">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="1d0ab-165">Çoğu durumda, nesneler genellikle tarafından tanımlanan şekilde bir görünümü sadece bir tanım vardır. [ViewSelectedBy](./viewselectedby-element-format.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-165">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="1d0ab-166">Aşağıdaki örnek, liste görünümü kullanarak görüntülenen nesneleri tanımlamak gösterilmektedir [ViewSelectedBy](./viewselectedby-element-format.md) ve [TypeName](./typename-element-for-viewselectedby-format.md) öğeleri.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-166">The following example shows how to define the objects that are displayed by the list view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="1d0ab-167">Sınırsız sayıda [TypeName](./typename-element-for-viewselectedby-format.md) öğeleri belirtebilirsiniz ve bunların sırası önemli değildir.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-167">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

<span data-ttu-id="1d0ab-168">Aşağıdaki XML öğeleri listesi görünümü tarafından kullanılan nesneleri belirtmek için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="1d0ab-168">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="1d0ab-169">[ViewSelectedBy](./viewselectedby-element-format.md) öğe tanımlar hangi nesneler tarafından liste görünümü görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-169">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="1d0ab-170">[TypeName](./typename-element-for-viewselectedby-format.md) öğesi görünüm tarafından görüntülenen .NET nesnesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-170">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET object that is displayed by the view.</span></span> <span data-ttu-id="1d0ab-171">Tam .NET türü adı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-171">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="1d0ab-172">En az bir türü veya görünümü için seçim belirtmeniz gerekir, ancak belirtilebilir öğelerinin hiçbir üst limiti yoktur.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-172">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="1d0ab-173">Eksiksiz bir biçimlendirme dosyası örneği için bkz. [liste görünümü (Temel)](./list-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="1d0ab-173">For an example of a complete formatting file, see [List View (Basic)](./list-view-basic.md).</span></span>

<span data-ttu-id="1d0ab-174">Aşağıdaki örnekte [ViewSelectedBy](./viewselectedby-element-format.md) ve [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) öğeleri.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-174">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="1d0ab-175">Bir liste görünümü ve aynı nesneleri için bir tablo görünümü tanımladığınızda gibi birden çok görünüm, görüntülenen nesnelerin ilgili kümesi sahip olduğu kullanım seçimi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-175">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a list view and a table view for the same objects.</span></span> <span data-ttu-id="1d0ab-176">Seçimi kümesi oluşturma hakkında daha fazla bilgi için bkz. [tanımlama seçimi ayarlar](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="1d0ab-176">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

<span data-ttu-id="1d0ab-177">Aşağıdaki XML öğeleri listesi görünümü tarafından kullanılan nesneleri belirtmek için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="1d0ab-177">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="1d0ab-178">[ViewSelectedBy](./viewselectedby-element-format.md) öğe tanımlar hangi nesneler tarafından liste görünümü görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-178">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="1d0ab-179">[SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) öğesi görünüm tarafından görüntülenen bir nesne belirtir.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-179">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="1d0ab-180">En az bir seçimi kümesi veya görünüm türünü belirtmeniz gerekir, ancak belirtilebilir öğelerinin hiçbir üst limiti yoktur.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-180">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="1d0ab-181">Aşağıdaki örnek, liste görünümünü kullanarak, belirli bir tanımı tarafından görüntülenecek nesneleri tanımlamak gösterilmektedir [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-181">The following example shows how to define the objects displayed by a specific definition of the list view using the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element.</span></span> <span data-ttu-id="1d0ab-182">Bu öğe kullanarak, nesne, Nesne Seçimi kümesi veya tanımı kullanıldığında belirten bir seçim koşulu .NET türü adını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-182">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="1d0ab-183">Seçim koşullar oluşturma hakkında daha fazla bilgi için bkz. [görüntüleyen veri koşulları tanımlama](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="1d0ab-183">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</ListEntry>
```

<span data-ttu-id="1d0ab-184">Aşağıdaki XML öğeleri, belirli bir liste görünümü tanımı tarafından kullanılan nesneleri belirtmek için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="1d0ab-184">The following XML elements can be used to specify the objects that are used by a specific definition of the list view:</span></span>

- <span data-ttu-id="1d0ab-185">[EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) öğe tanımlar hangi nesnelerin tanımına göre görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-185">The [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="1d0ab-186">[TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) öğe tanımına göre gösterilecek .NET nesnesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-186">The [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) element specifies the .NET object that is displayed by the definition.</span></span> <span data-ttu-id="1d0ab-187">Bu öğe kullanırken, tam .NET türü adı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-187">When using this element, the fully qualified .NET type name is required.</span></span> <span data-ttu-id="1d0ab-188">En az bir türü, seçim kümesi veya tanımı için seçim koşulu belirtmeniz gerekir, ancak belirtilebilir öğelerinin hiçbir üst limiti yoktur.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-188">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="1d0ab-189">[SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) (gösterilmemiştir) öğesi bu tanımı tarafından görüntülenebilen bir nesne belirtir.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-189">The [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="1d0ab-190">En az bir türü, seçim kümesi veya tanımı için seçim koşulu belirtmeniz gerekir, ancak belirtilebilir öğelerinin hiçbir üst limiti yoktur.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-190">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="1d0ab-191">[SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) (gösterilmemiştir) öğesi kullanılmak üzere bu tanım için bulunması gereken bir koşulu belirtir.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-191">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="1d0ab-192">En az bir türü, seçim kümesi veya tanımı için seçim koşulu belirtmeniz gerekir, ancak belirtilebilir öğelerinin hiçbir üst limiti yoktur.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-192">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="1d0ab-193">Seçimi koşulları tanımlama hakkında daha fazla bilgi için bkz. [görüntüleyen veri koşulları tanımlama](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="1d0ab-193">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="displaying-groups-of-objects-in-a-list-view"></a><span data-ttu-id="1d0ab-194">Nesne bir liste görünümü görüntüleme</span><span class="sxs-lookup"><span data-stu-id="1d0ab-194">Displaying Groups of Objects in a List View</span></span>

<span data-ttu-id="1d0ab-195">Liste Görünümü gruplar tarafından görüntülenen nesneleri ayırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-195">You can separate the objects that are displayed by the list view into groups.</span></span> <span data-ttu-id="1d0ab-196">Yalnızca belirli bir özellik veya betik değeri değiştiğinde Windows PowerShell'in yeni bir grup başlatır. Bu bir grubu tanımlayan gelmez.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-196">This does not mean that you define a group, only that Windows PowerShell starts a new group whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="1d0ab-197">Aşağıdaki örnekte, yeni bir grup başlatıldığında her değeri [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) özellik değişiklikleri.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-197">In the following example, a new group is started whenever the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="1d0ab-198">Aşağıdaki XML öğeleri bir grup başlatıldığında tanımlamak için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="1d0ab-198">The following XML elements are used to define when a group is started:</span></span>

- <span data-ttu-id="1d0ab-199">[GroupBy](./groupby-element-for-view-format.md) öğesi, özellik veya yeni Grup başlar ve Grup nasıl görüntüleneceğini tanımlar betiği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-199">The [GroupBy](./groupby-element-for-view-format.md) element defines the property or script that starts the new group and defines how the group is displayed.</span></span>

- <span data-ttu-id="1d0ab-200">[PropertyName](./propertyname-element-for-groupby-format.md) değeri değiştiğinde yeni bir grup başlatan özellik öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-200">The [PropertyName](./propertyname-element-for-groupby-format.md) element specifies the property that starts a new group whenever its value changes.</span></span> <span data-ttu-id="1d0ab-201">Bir özellik veya grubu başlatmak için komut dosyasını belirtmeniz gerekir, ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-201">You must specify a property or script to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="1d0ab-202">[ScriptBlock](./scriptblock-element-for-groupby-format.md) öğesi değeri değiştiğinde yeni bir grup başlatan komut dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-202">The [ScriptBlock](./scriptblock-element-for-groupby-format.md) element specifies the script that starts a new group whenever its value changes.</span></span> <span data-ttu-id="1d0ab-203">Bir betiği veya grup başlatmak için özellik belirtmeniz gerekir, ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-203">You must specify a script or property to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="1d0ab-204">[Etiket](./label-element-for-groupby-format.md) her grubu başında görüntülenen etiket öğe tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-204">The [Label](./label-element-for-groupby-format.md) element defines a label that is displayed at the beginning of each group.</span></span> <span data-ttu-id="1d0ab-205">Bu öğe tarafından belirtilen metin ek olarak, Windows PowerShell öncesi ve sonrası etiketi boş bir satır ekler ve yeni Grup tetiklenen değeri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-205">In addition to the text specified by this element, Windows PowerShell displays the value that triggered the new group and adds a blank line before and after the label.</span></span> <span data-ttu-id="1d0ab-206">Bu öğe isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-206">This element is optional.</span></span>

- <span data-ttu-id="1d0ab-207">[Özel denetim](./customcontrol-element-for-groupby-format.md) öğe verileri görüntülemek için kullanılan bir denetimi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-207">The [CustomControl](./customcontrol-element-for-groupby-format.md) element defines a control that is used to display the data.</span></span> <span data-ttu-id="1d0ab-208">Bu öğe isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-208">This element is optional.</span></span>

- <span data-ttu-id="1d0ab-209">[CustomControlName](./customcontrolname-element-for-groupby-format.md) öğeyi belirten bir ortak veya verileri görüntülemek için kullanılan denetim görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-209">The [CustomControlName](./customcontrolname-element-for-groupby-format.md) element specifies a common or view control that is used to display the data.</span></span> <span data-ttu-id="1d0ab-210">Bu öğe isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-210">This element is optional.</span></span>

<span data-ttu-id="1d0ab-211">Grupları tanımlayan bir tam biçimlendirme dosyası örneği için bkz. [liste görünümü (gruplandırma ölçütü)](./list-view-groupby.md).</span><span class="sxs-lookup"><span data-stu-id="1d0ab-211">For an example of a complete formatting file that defines groups, see [List View (GroupBy)](./list-view-groupby.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="1d0ab-212">Biçim dizeleri kullanma</span><span class="sxs-lookup"><span data-stu-id="1d0ab-212">Using Format Strings</span></span>

<span data-ttu-id="1d0ab-213">Daha fazla verinin nasıl görüntüleneceğini tanımlamak için bir görünüm biçimlendirme dizeleri eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-213">Formatting strings can be added to a view to further define how the data is displayed.</span></span> <span data-ttu-id="1d0ab-214">Aşağıdaki örnek, bir biçimlendirme dizesi değerini tanımlamak gösterilmektedir `StartTime` özelliği.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-214">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

<span data-ttu-id="1d0ab-215">Aşağıdaki XML öğeleri, bir biçim deseni belirtmek için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="1d0ab-215">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="1d0ab-216">[ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) öğesi görünüm tarafından görüntülenen verileri belirtir.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-216">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="1d0ab-217">[PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) öğesi değeri görünüm tarafından görüntülenen özelliği belirtir.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-217">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="1d0ab-218">Bir özellik ya da bir komut dosyası belirtmeniz gerekir, ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-218">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="1d0ab-219">[FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) öğesi Görünümü'nde özellik veya betik değerin nasıl görüntüleneceğini tanımlayan bir biçim desenini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-219">The [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>

- <span data-ttu-id="1d0ab-220">[ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) (gösterilmemiştir) öğesi değeri görünüm tarafından görüntülenen komut dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-220">The [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="1d0ab-221">Bir betik ya da bir özellik belirtmeniz gerekir, ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-221">You must specify either a script or a property, but you cannot specify both.</span></span>

<span data-ttu-id="1d0ab-222">Aşağıdaki örnekte, `ToString` yöntemi betik değerini biçimlendirmek için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-222">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="1d0ab-223">Komut, bir nesnenin herhangi bir yöntemi çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-223">Scripts can call any method of an object.</span></span> <span data-ttu-id="1d0ab-224">Bu nedenle, bir nesne gibi bir yöntem varsa `ToString`biçimlendirme parametreleri olan, betik komut çıktı değerini biçimlendirmek için bu yöntem çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-224">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<ListItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

<span data-ttu-id="1d0ab-225">Aşağıdaki XML öğesi için arama kullanılabilir `ToString` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="1d0ab-225">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="1d0ab-226">[ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) öğesi görünüm tarafından görüntülenen verileri belirtir.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-226">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="1d0ab-227">[ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) (gösterilmemiştir) öğesi değeri görünüm tarafından görüntülenen komut dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-227">The [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="1d0ab-228">Bir betik ya da bir özellik belirtmeniz gerekir, ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="1d0ab-228">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="1d0ab-229">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="1d0ab-229">See Also</span></span>

[<span data-ttu-id="1d0ab-230">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="1d0ab-230">Writing a Windows PowerShell Cmdlet</span></span>](../cmdlet/writing-a-windows-powershell-cmdlet.md)
