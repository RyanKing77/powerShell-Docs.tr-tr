---
title: Bir tablo görünümü oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1f405afb-70b5-4fe0-9986-bc07401d93fd
caps.latest.revision: 23
ms.openlocfilehash: 832527ea4b042812c39934cd7e124201c6dc2ea4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850662"
---
# <a name="creating-a-table-view"></a><span data-ttu-id="22836-102">Tablo Görünümü Oluşturma</span><span class="sxs-lookup"><span data-stu-id="22836-102">Creating a Table View</span></span>

<span data-ttu-id="22836-103">Tablo görünümü, bir veya daha fazla sütun verilerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="22836-103">A table view displays data in one or more columns.</span></span> <span data-ttu-id="22836-104">Tablodaki her satır bir .NET nesnesini temsil eder ve bir tablonun her sütunu nesnesinin veya bir betik değer bir özelliği temsil eder.</span><span class="sxs-lookup"><span data-stu-id="22836-104">Each row in the table represents a .NET object, and each column of the table represents a property of the object or a script value.</span></span> <span data-ttu-id="22836-105">Bir nesnenin tüm özelliklerinin veya bir alt kümesini bir nesnenin özelliklerini gösteren bir tablo görünümü tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="22836-105">You can define a table view that displays all the properties of an object or a subset of the properties of an object.</span></span>

## <a name="a-table-view-display"></a><span data-ttu-id="22836-106">Tablo görünümü görüntüleme</span><span class="sxs-lookup"><span data-stu-id="22836-106">A Table View Display</span></span>

<span data-ttu-id="22836-107">Aşağıdaki örnek Windows PowerShell biçimini gösterir [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) tarafından döndürülen nesne [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="22836-107">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object that is returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="22836-108">Bu nesne için Windows PowerShell gösteren bir tablo görünümü tanımladığı `Status` özelliği `Name` özelliği (Bu özellik için bir diğer ad özelliktir `ServiceName` özelliği) ve `DisplayName` özelliği.</span><span class="sxs-lookup"><span data-stu-id="22836-108">For this object, Windows PowerShell has defined a table view that displays the `Status` property, the `Name` property (this property is an alias property for the `ServiceName` property), and the `DisplayName` property.</span></span> <span data-ttu-id="22836-109">Tablodaki her satır cmdlet'i tarafından döndürülen bir nesneyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="22836-109">Each row in the table represents an object returned by the cmdlet.</span></span>

```output
Status   Name               DisplayName
------   ----               -----------
Stopped  AJRouter           AllJoyn Router Service
Stopped  ALG                Application Layer Gateway Service
Stopped  AppIDSvc           Application Identity
Running  Appinfo            Application Information
```

## <a name="defining-the-table-view"></a><span data-ttu-id="22836-110">Tablo görünümü tanımlama</span><span class="sxs-lookup"><span data-stu-id="22836-110">Defining the Table View</span></span>

<span data-ttu-id="22836-111">Tablo görünümü şemasını görüntülemek için aşağıdaki XML gösterir [System.Serviceprocess.Servicecontroller? Displayproperty Fullname =](/dotnet/api/System.ServiceProcess.ServiceController) nesne.</span><span class="sxs-lookup"><span data-stu-id="22836-111">The following XML shows the table view schema for displaying the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="22836-112">Tablo görünümünde görüntülenmesini istediğiniz her bir özellik belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="22836-112">You must specify each property that you want displayed in the table view.</span></span>

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>
    <TableHeaders>
      <TableColumnHeader>
        <Width>8</Width>
      </TableColumnHeader>
      <TableColumnHeader>
        <Width>18</Width>
      </TableColumnHeader>
      <TableColumnHeader>
        <Width>38</Width>
      </TableColumnHeader>
    </TableHeaders>
    <TableRowEntries>
      <TableRowEntry>
        <TableColumnItems>
          <TableColumnItem>
           <PropertyName>Status</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>Name</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>DisplayName</PropertyName>
          </TableColumnItem>
        </TableColumnItems>
      </TableRowEntry>
    </TableRowEntries>
  </TableControl>
</View>
```

<span data-ttu-id="22836-113">Aşağıdaki XML öğeleri, bir liste görünümü tanımlamak için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="22836-113">The following XML elements are used to define a list view:</span></span>

- <span data-ttu-id="22836-114">[Görünümü](./view-element-format.md) Tablo görünümü üst öğesinin bir öğedir.</span><span class="sxs-lookup"><span data-stu-id="22836-114">The [View](./view-element-format.md) element is the parent element of the table view.</span></span> <span data-ttu-id="22836-115">(Bu liste, geniş ve özel denetim görünümleri için aynı üst öğeye niteliğindedir.)</span><span class="sxs-lookup"><span data-stu-id="22836-115">(This is the same parent element for the list, wide, and custom control views.)</span></span>

- <span data-ttu-id="22836-116">[Adı](./name-element-for-view-format.md) öğesi, görünümün adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="22836-116">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="22836-117">Bu öğe tüm görünümleri için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="22836-117">This element is required for all views.</span></span>

- <span data-ttu-id="22836-118">[ViewSelectedBy](./viewselectedby-element-format.md) öğe görünümünü kullanın nesneleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="22836-118">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="22836-119">Bu öğe gereklidir.</span><span class="sxs-lookup"><span data-stu-id="22836-119">This element is required.</span></span>

- <span data-ttu-id="22836-120">[GroupBy](./groupby-element-for-view-format.md) (Bu örnekte gösterilmiştir değil) öğesi, yeni bir grup nesne görüntülendiğinde tanımlar.</span><span class="sxs-lookup"><span data-stu-id="22836-120">The [GroupBy](./groupby-element-for-view-format.md) element (not shown in this example) defines when a new group of objects is displayed.</span></span> <span data-ttu-id="22836-121">Bir özel özellik veya betik değeri değiştiğinde yeni bir grup başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="22836-121">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="22836-122">Bu öğe isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="22836-122">This element is optional.</span></span>

- <span data-ttu-id="22836-123">[Denetimleri](./controls-element-for-view-format.md) (Bu örnekte gösterildiği gibi değil) tablo görünümü tarafından tanımlanan özel denetimleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="22836-123">The [Controls](./controls-element-for-view-format.md) element (not shown in this example) defines the custom controls that are defined by the table view.</span></span> <span data-ttu-id="22836-124">Denetimler, daha fazla verinin nasıl görüntüleneceğini belirtmek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="22836-124">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="22836-125">Bu öğe isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="22836-125">This element is optional.</span></span> <span data-ttu-id="22836-126">Bir görünüm kendi özel denetimler tanımlayabilirsiniz veya biçimlendirme dosyasında herhangi bir görünüm tarafından kullanılabilen ortak denetimleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="22836-126">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="22836-127">Özel denetimler hakkında daha fazla bilgi için bkz: [özel denetimler oluşturma](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="22836-127">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="22836-128">[HideTableHeaders](./hidetableheaders-element-format.md) öğeyi (Bu örnekte gösterme) belirten Tablo üst tablonun tüm etiketleri göstermez.</span><span class="sxs-lookup"><span data-stu-id="22836-128">The [HideTableHeaders](./hidetableheaders-element-format.md) element (not show in this example) specifies that the table will not show any labels at the top of the table.</span></span> <span data-ttu-id="22836-129">Bu öğe isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="22836-129">This element is optional.</span></span>

- <span data-ttu-id="22836-130">[TableControl](./tablecontrol-element-format.md) Tablo üst bilgisi ve satır bilgilerini tanımlayan bir öğe.</span><span class="sxs-lookup"><span data-stu-id="22836-130">The [TableControl](./tablecontrol-element-format.md) element that defines the header and row information of the table.</span></span> <span data-ttu-id="22836-131">Diğer tüm görünümlere benzer bir tablo görünümü nesne özelliklerin değerlerini veya betikler tarafından oluşturulan değerleri görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="22836-131">Similar to all other views, a table view can display the values of object properties or values generated by scripts.</span></span>

## <a name="defining-column-headers"></a><span data-ttu-id="22836-132">Sütun üst bilgilerini tanımlama</span><span class="sxs-lookup"><span data-stu-id="22836-132">Defining Column Headers</span></span>

1. <span data-ttu-id="22836-133">[TableHeaders](./tableheaders-element-format.md) öğesi ve onun alt öğeleri tanımlayan ne Tablo üst kısmında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="22836-133">The [TableHeaders](./tableheaders-element-format.md) element and its child elements define what is displayed at the top of the table.</span></span>

2. <span data-ttu-id="22836-134">[TableColumnHeader](./tablecolumnheader-element-format.md) öğesi, bir tablo sütununun en üstünde gösterilen tanımlar.</span><span class="sxs-lookup"><span data-stu-id="22836-134">The [TableColumnHeader](./tablecolumnheader-element-format.md) element defines what is displayed at the top of a column of the table.</span></span> <span data-ttu-id="22836-135">Bu öğeleri görüntülenen üstbilgileri istediğiniz sırayla belirtin.</span><span class="sxs-lookup"><span data-stu-id="22836-135">Specify these elements in the order that you want the headers displayed.</span></span>

   <span data-ttu-id="22836-136">Kullanabileceğiniz bu öğe sayısı, ancak sayısı için herhangi bir sınır yoktur [TableColumnHeader](./tablecolumnheader-element-format.md) , Tablo görünümünde öğelerin sayısına eşit [TableRowEntry](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md) kullandığınız öğeleri.</span><span class="sxs-lookup"><span data-stu-id="22836-136">There is no limit to the number of these element that you can use, but the number of [TableColumnHeader](./tablecolumnheader-element-format.md) elements in your table view must equal the number of [TableRowEntry](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md) elements that you use.</span></span>

3. <span data-ttu-id="22836-137">[Etiket](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) öğesi görüntülenen metni belirtir.</span><span class="sxs-lookup"><span data-stu-id="22836-137">The [Label](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies the text that is displayed.</span></span> <span data-ttu-id="22836-138">Bu öğe isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="22836-138">This element is optional.</span></span>

4. <span data-ttu-id="22836-139">[Genişliği](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) öğesi sütunun genişliği (karakter cinsinden) belirtir.</span><span class="sxs-lookup"><span data-stu-id="22836-139">The [Width](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies the width (in characters) of the column.</span></span> <span data-ttu-id="22836-140">Bu öğe isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="22836-140">This element is optional.</span></span>

5. <span data-ttu-id="22836-141">[Hizalama](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) öğesi etiketi nasıl görüntüleneceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="22836-141">The [Alignment](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies how the label is displayed.</span></span> <span data-ttu-id="22836-142">Etiket sağa sola hizalanmış veya orta.</span><span class="sxs-lookup"><span data-stu-id="22836-142">The label can be aligned to the left, to the right, or centered.</span></span> <span data-ttu-id="22836-143">Bu öğe isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="22836-143">This element is optional.</span></span>

## <a name="defining-the-table-rows"></a><span data-ttu-id="22836-144">Tablo Satırları tanımlama</span><span class="sxs-lookup"><span data-stu-id="22836-144">Defining the Table Rows</span></span>

<span data-ttu-id="22836-145">Tablo görünümleri, hangi verilerin alt öğelerini kullanarak tablo satırları görüntülendiğini belirten bir veya daha fazla tanımları sağlayabilir [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="22836-145">Table views can provide one or more definitions that specify what data is displayed in the rows of the table by using the child elements of the [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) element.</span></span> <span data-ttu-id="22836-146">Tablonun satırlarını için birden çok tanım belirtebilirsiniz, ancak üst satırlar için aynı kalır, hangi satır tanımı kullanılan bağımsız olarak dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="22836-146">Notice that you can specify multiple definitions for the rows of the table, but the headers for the rows remains the same, regardless of what row definition is used.</span></span> <span data-ttu-id="22836-147">Genellikle, bir tablo yalnızca bir tanımı sahip olacaktır.</span><span class="sxs-lookup"><span data-stu-id="22836-147">Typically, a table will have only one definition.</span></span>

<span data-ttu-id="22836-148">Aşağıdaki örnekte, birkaç özelliklerinin değerlerini görüntüler tek bir tanım görünümü sağlar [System.Diagnostics.Process? Displayproperty Fullname =](/dotnet/api/System.Diagnostics.Process) nesne.</span><span class="sxs-lookup"><span data-stu-id="22836-148">In the following example, the view provides a single definition that displays the values of several properties of the [System.Diagnostics.Process?Displayproperty=Fullname](/dotnet/api/System.Diagnostics.Process) object.</span></span> <span data-ttu-id="22836-149">Tablo görünümü, bir özelliğin değerini veya bir betik (örnekte gösterilmiştir değil) değerini kendi satırlarda görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="22836-149">A table view can display the value of a property or the value of a script (not shown in the example) in its rows.</span></span>

```xml
<TableRowEntries>
      <TableRowEntry>
        <TableColumnItems>
          <TableColumnItem>
           <PropertyName>Status</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>Name</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>DisplayName</PropertyName>
          </TableColumnItem>
        </TableColumnItems>
      </TableRowEntry>
    </TableRowEntries>

```

<span data-ttu-id="22836-150">Aşağıdaki XML öğeleri, bir satır için tanımları sağlamak için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="22836-150">The following XML elements can be used to provide definitions for a row:</span></span>

- <span data-ttu-id="22836-151">[TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) öğesi ve onun alt öğeleri tanımlamak ne tablonun satırlarını içinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="22836-151">The [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) element and its child elements define what is displayed in the rows of the table.</span></span>

- <span data-ttu-id="22836-152">[TableRowEntry](./listentry-element-for-listcontrol-format.md) öğesi satırı tanımını sağlar.</span><span class="sxs-lookup"><span data-stu-id="22836-152">The [TableRowEntry](./listentry-element-for-listcontrol-format.md) element provides a definition of the row.</span></span> <span data-ttu-id="22836-153">En az bir [TableRowEntry](./listentry-element-for-listcontrol-format.md) gereklidir; ancak, hiçbir ekleyebileceğiniz öğe sayısı üst sınırı yoktur.</span><span class="sxs-lookup"><span data-stu-id="22836-153">At least one [TableRowEntry](./listentry-element-for-listcontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="22836-154">Çoğu durumda, yalnızca bir tanımı bir görünüm olacaktır.</span><span class="sxs-lookup"><span data-stu-id="22836-154">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="22836-155">[EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) öğesi, belirli bir tanımı tarafından görüntülenen nesneleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="22836-155">The [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="22836-156">Bu öğe isteğe bağlıdır ve yalnızca birden çok tanımlarken gerekli [TableRowEntry](./listentry-element-for-listcontrol-format.md) görüntüleme farklı nesneleri öğeleri.</span><span class="sxs-lookup"><span data-stu-id="22836-156">This element is optional and is needed only when you define multiple [TableRowEntry](./listentry-element-for-listcontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="22836-157">[Kaydırma](./wrap-element-for-tablerowentry-for-tablecontrl-format.md) öğesi ve sonraki satırda sütun genişliğini aşıyor metin görüntülendiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="22836-157">The [Wrap](./wrap-element-for-tablerowentry-for-tablecontrl-format.md) element specifies that text that exceeds the column width is displayed on the next line.</span></span> <span data-ttu-id="22836-158">Varsayılan olarak, sütun genişliğini aşıyor metin kesilir.</span><span class="sxs-lookup"><span data-stu-id="22836-158">By default, text that exceeds the column width is truncated.</span></span>

- <span data-ttu-id="22836-159">[TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) özelliklerini veya betikleri değerleri satır içinde görüntülenen öğe tanımlar.</span><span class="sxs-lookup"><span data-stu-id="22836-159">The [TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) element defines the properties or scripts whose values are displayed in the row.</span></span>

- <span data-ttu-id="22836-160">[TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) öğe tanımlar özelliği veya betik değerini, satır sütununda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="22836-160">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="22836-161">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) öğesi satırın her sütun için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="22836-161">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="22836-162">İlk girişi, ilk sütunda, ikinci sütun ve benzeri ikinci girdi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="22836-162">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="22836-163">[PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) öğesi değeri satır içinde görüntülenen özelliği belirtir.</span><span class="sxs-lookup"><span data-stu-id="22836-163">The [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="22836-164">Bir özellik ya da bir komut dosyası belirtmeniz gerekir, ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="22836-164">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="22836-165">[ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) öğesi değeri satır içinde görüntülenen komut dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="22836-165">The [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="22836-166">Bir betik ya da bir özellik belirtmeniz gerekir, ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="22836-166">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="22836-167">[FormatString](./label-element-for-listitem-for-listcontrol-format.md) öğesi özelliği veya betik değerin nasıl görüntüleneceğini tanımlayan bir biçim desenini belirtir.</span><span class="sxs-lookup"><span data-stu-id="22836-167">The [FormatString](./label-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed.</span></span> <span data-ttu-id="22836-168">Bu öğe isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="22836-168">This element is optional.</span></span>

- <span data-ttu-id="22836-169">[Hizalama](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) öğesi, özellik veya komut dosyası değerini nasıl görüntüleneceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="22836-169">The [Alignment](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies how the value of the property or script is displayed.</span></span> <span data-ttu-id="22836-170">Değer, sağa sola hizalanmış veya orta.</span><span class="sxs-lookup"><span data-stu-id="22836-170">The value can be aligned to the left, to the right, or centered.</span></span> <span data-ttu-id="22836-171">Bu öğe isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="22836-171">This element is optional.</span></span>

## <a name="defining-the-objects-that-use-the-table-view"></a><span data-ttu-id="22836-172">Tablo görünümü kullanan nesneler tanımlama</span><span class="sxs-lookup"><span data-stu-id="22836-172">Defining the Objects That Use the Table View</span></span>

<span data-ttu-id="22836-173">Tablo görünümü hangi .NET nesnelerini kullanmak tanımlamak için iki yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="22836-173">There are two ways to define which .NET objects use the table view.</span></span> <span data-ttu-id="22836-174">Kullanabileceğiniz [ViewSelectedBy](./viewselectedby-element-format.md) görünümü veya tüm tanımları tarafından görüntülenebilen nesneler tanımlamak için kullanabileceğiniz [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) hangi nesnelerin tarafından görüntülenen tanımlamak için bir Belirli görünüm tanımı.</span><span class="sxs-lookup"><span data-stu-id="22836-174">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="22836-175">Çoğu durumda, nesneler genellikle tarafından tanımlanan şekilde bir görünümü sadece bir tanım vardır. [ViewSelectedBy](./viewselectedby-element-format.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="22836-175">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="22836-176">Aşağıdaki örnek, tablo görünümü kullanılarak görüntülenecek nesneleri tanımlamak gösterilmektedir [ViewSelectedBy](./viewselectedby-element-format.md) ve [TypeName](./typename-element-for-viewselectedby-format.md) öğeleri.</span><span class="sxs-lookup"><span data-stu-id="22836-176">The following example shows how to define the objects that are displayed by the table view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="22836-177">Sınırsız sayıda [TypeName](./typename-element-for-viewselectedby-format.md) öğeleri belirtebilirsiniz ve bunların sırası önemli değildir.</span><span class="sxs-lookup"><span data-stu-id="22836-177">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

<span data-ttu-id="22836-178">Aşağıdaki XML öğeleri, Tablo görünümünde tarafından kullanılan nesneleri belirtmek için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="22836-178">The following XML elements can be used to specify the objects that are used by the table view:</span></span>

- <span data-ttu-id="22836-179">[ViewSelectedBy](./viewselectedby-element-format.md) öğe tanımlar hangi nesneler tarafından liste görünümü görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="22836-179">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="22836-180">[TypeName](./typename-element-for-viewselectedby-format.md) öğesi görünüm tarafından görüntülenen .NET nesnesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="22836-180">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET object that is displayed by the view.</span></span> <span data-ttu-id="22836-181">Tam .NET türü adı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="22836-181">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="22836-182">En az bir türü veya görünümü için seçim belirtmeniz gerekir, ancak belirtilebilir öğelerinin hiçbir üst limiti yoktur.</span><span class="sxs-lookup"><span data-stu-id="22836-182">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="22836-183">Aşağıdaki örnekte [ViewSelectedBy](./viewselectedby-element-format.md) ve [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) öğeleri.</span><span class="sxs-lookup"><span data-stu-id="22836-183">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="22836-184">Bir liste görünümü ve aynı nesneleri için bir tablo görünümü tanımladığınızda gibi birden çok görünüm, görüntülenen nesnelerin ilgili kümesi sahip olduğu kullanım seçimi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="22836-184">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a list view and a table view for the same objects.</span></span> <span data-ttu-id="22836-185">Seçimi kümesi oluşturma hakkında daha fazla bilgi için bkz. [tanımlama seçimi ayarlar](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="22836-185">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

<span data-ttu-id="22836-186">Aşağıdaki XML öğeleri listesi görünümü tarafından kullanılan nesneleri belirtmek için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="22836-186">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="22836-187">[ViewSelectedBy](./viewselectedby-element-format.md) öğe tanımlar hangi nesneler tarafından liste görünümü görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="22836-187">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="22836-188">[SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) öğesi görünüm tarafından görüntülenen bir nesne belirtir.</span><span class="sxs-lookup"><span data-stu-id="22836-188">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="22836-189">En az bir seçimi kümesi veya görünüm türünü belirtmeniz gerekir, ancak belirtilebilir öğelerinin hiçbir üst limiti yoktur.</span><span class="sxs-lookup"><span data-stu-id="22836-189">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="22836-190">Aşağıdaki örnek, tablo görünümü kullanarak belirli bir tanımı tarafından görüntülenecek nesneleri tanımlamak gösterilmektedir [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="22836-190">The following example shows how to define the objects displayed by a specific definition of the table view using the [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element.</span></span> <span data-ttu-id="22836-191">Bu öğe kullanarak, nesne, Nesne Seçimi kümesi veya tanımı kullanıldığında belirten bir seçim koşulu .NET türü adını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="22836-191">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="22836-192">Seçim koşullar oluşturma hakkında daha fazla bilgi için bkz. [görüntüleyen veri koşulları tanımlama](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="22836-192">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

> [!NOTE]
> <span data-ttu-id="22836-193">Birden çok tablo görünümü tanımını oluştururken farklı bir sütun üst bilgileri belirtilemez.</span><span class="sxs-lookup"><span data-stu-id="22836-193">When creating multiple definitions of the table view you cannot specify different column headers.</span></span> <span data-ttu-id="22836-194">Hangi nesne tablonun satırlarını yalnızca görüntülenenleri belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="22836-194">You can specify only what is displayed in the rows of the table, such as what objects are displayed.</span></span>

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</TableRowEntry>
```

<span data-ttu-id="22836-195">Aşağıdaki XML öğeleri, belirli bir liste görünümü tanımı tarafından kullanılan nesneleri belirtmek için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="22836-195">The following XML elements can be used to specify the objects that are used by a specific definition of the list view:</span></span>

- <span data-ttu-id="22836-196">[EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) öğe tanımlar hangi nesnelerin tanımına göre görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="22836-196">The [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="22836-197">[TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) öğe tanımına göre gösterilecek .NET nesnesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="22836-197">The [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) element specifies the .NET object that is displayed by the definition.</span></span> <span data-ttu-id="22836-198">Bu öğe kullanırken, tam .NET türü adı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="22836-198">When using this element, the fully qualified .NET type name is required.</span></span> <span data-ttu-id="22836-199">En az bir türü, seçim kümesi veya tanımı için seçim koşulu belirtmeniz gerekir, ancak belirtilebilir öğelerinin hiçbir üst limiti yoktur.</span><span class="sxs-lookup"><span data-stu-id="22836-199">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="22836-200">[SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) (gösterilmemiştir) öğesi bu tanımı tarafından görüntülenebilen bir nesne belirtir.</span><span class="sxs-lookup"><span data-stu-id="22836-200">The [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="22836-201">En az bir türü, seçim kümesi veya tanımı için seçim koşulu belirtmeniz gerekir, ancak belirtilebilir öğelerinin hiçbir üst limiti yoktur.</span><span class="sxs-lookup"><span data-stu-id="22836-201">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="22836-202">[SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) (gösterilmemiştir) öğesi kullanılmak üzere bu tanım için bulunması gereken bir koşulu belirtir.</span><span class="sxs-lookup"><span data-stu-id="22836-202">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="22836-203">En az bir türü, seçim kümesi veya tanımı için seçim koşulu belirtmeniz gerekir, ancak belirtilebilir öğelerinin hiçbir üst limiti yoktur.</span><span class="sxs-lookup"><span data-stu-id="22836-203">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="22836-204">Seçimi koşulları tanımlama hakkında daha fazla bilgi için bkz. [görüntüleyen veri koşulları tanımlama](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="22836-204">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="22836-205">Biçim dizeleri kullanma</span><span class="sxs-lookup"><span data-stu-id="22836-205">Using Format Strings</span></span>

<span data-ttu-id="22836-206">Daha fazla verinin nasıl görüntüleneceğini tanımlamak için bir görünüm biçimlendirme dizeleri eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="22836-206">Formatting strings can be added to a view to further define how the data is displayed.</span></span> <span data-ttu-id="22836-207">Aşağıdaki örnek, bir biçimlendirme dizesi değerini tanımlamak gösterilmektedir `StartTime` özelliği.</span><span class="sxs-lookup"><span data-stu-id="22836-207">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

<span data-ttu-id="22836-208">Aşağıdaki XML öğeleri, bir biçim deseni belirtmek için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="22836-208">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="22836-209">[TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) öğe tanımlar özelliği veya betik değerini, satır sütununda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="22836-209">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="22836-210">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) öğesi satırın her sütun için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="22836-210">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="22836-211">İlk girişi, ilk sütunda, ikinci sütun ve benzeri ikinci girdi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="22836-211">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="22836-212">[PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) öğesi değeri satır içinde görüntülenen özelliği belirtir.</span><span class="sxs-lookup"><span data-stu-id="22836-212">The [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="22836-213">Bir özellik ya da bir komut dosyası belirtmeniz gerekir, ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="22836-213">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="22836-214">[FormatString](./label-element-for-listitem-for-listcontrol-format.md) öğesi özelliği veya betik değerin nasıl görüntüleneceğini tanımlayan bir biçim desenini belirtir.</span><span class="sxs-lookup"><span data-stu-id="22836-214">The [FormatString](./label-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed.</span></span>

<span data-ttu-id="22836-215">Aşağıdaki örnekte, `ToString` yöntemi betik değerini biçimlendirmek için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="22836-215">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="22836-216">Komut, bir nesnenin herhangi bir yöntemi çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="22836-216">Scripts can call any method of an object.</span></span> <span data-ttu-id="22836-217">Bu nedenle, bir nesne gibi bir yöntem varsa `ToString`biçimlendirme parametreleri olan, betik komut çıktı değerini biçimlendirmek için bu yöntem çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="22836-217">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<ListItem>
  <ScriptBlock>
    [String]::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

<span data-ttu-id="22836-218">Aşağıdaki XML öğesi için arama kullanılabilir `ToString` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="22836-218">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="22836-219">[TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) öğe tanımlar özelliği veya betik değerini, satır sütununda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="22836-219">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="22836-220">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) öğesi satırın her sütun için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="22836-220">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="22836-221">İlk girişi, ilk sütunda, ikinci sütun ve benzeri ikinci girdi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="22836-221">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="22836-222">[ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) öğesi değeri satır içinde görüntülenen komut dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="22836-222">The [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="22836-223">Bir betik ya da bir özellik belirtmeniz gerekir, ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="22836-223">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="22836-224">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="22836-224">See Also</span></span>

[<span data-ttu-id="22836-225">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="22836-225">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
