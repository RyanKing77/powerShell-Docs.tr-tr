---
title: Dosya genel bakış biçimlendirme | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe888fee-1fe9-459f-9d62-35732c19a7f8
caps.latest.revision: 13
ms.openlocfilehash: d418cff70c1197aa3c331eed909f49198da139e9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851922"
---
# <a name="formatting-file-overview"></a><span data-ttu-id="8fb51-102">Biçimlendirme Dosyasına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8fb51-102">Formatting File Overview</span></span>

<span data-ttu-id="8fb51-103">(Cmdlet'ler, İşlevler ve betikler) komutları tarafından döndürülen nesneler için görüntüleme biçimi biçimlendirme dosyaları (format.ps1xml dosyaları) kullanılarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="8fb51-103">The display format for the objects that are returned by commands (cmdlets, functions, and scripts) are defined by using formatting files (format.ps1xml files).</span></span> <span data-ttu-id="8fb51-104">Bu dosyaların birkaç gibi sağlanan PowerShell komutları tarafından döndürülen nesnelere görüntülenme biçimini tanımlamak için PowerShell tarafından sağlanan [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) tarafından döndürülen nesne `Get-Process` cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="8fb51-104">Several of these files are provided by PowerShell to define the display format for those objects returned by PowerShell-provided commands, such as the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object returned by the `Get-Process` cmdlet.</span></span> <span data-ttu-id="8fb51-105">Ancak, kendi özel biçimlendirme dosyaları varsayılan görüntü biçimleri üzerine de oluşturabilirsiniz veya kendi komutları tarafından döndürülen nesne gösterimini tanımlamak için özel bir biçimlendirme dosyası yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8fb51-105">However, you can also create your own custom formatting files to overwrite the default display formats or you can write a custom formatting file to define the display of objects returned by your own commands.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8fb51-106">Biçimlendirme dosyaları işlem hattının getirilen nesneyi öğelerini belirlemek değil.</span><span class="sxs-lookup"><span data-stu-id="8fb51-106">Formatting files do not determine the elements of an object that are returned to the pipeline.</span></span> <span data-ttu-id="8fb51-107">Bir nesneyi ardışık düzene döndürüldüğünde, bu nesnenin tüm üyelerine bazı görüntülenmez olsa bile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8fb51-107">When an object is returned to the pipeline, all members of that object are available even if some are not displayed.</span></span>

<span data-ttu-id="8fb51-108">PowerShell, görüntülenenler ve görüntülenen verileri nasıl biçimlendirildiğini belirlemek için bu biçimlendirme dosyalarında verileri kullanır.</span><span class="sxs-lookup"><span data-stu-id="8fb51-108">PowerShell uses the data in these formatting files to determine what is displayed and how the displayed data is formatted.</span></span> <span data-ttu-id="8fb51-109">Görüntülenen verileri, bir nesnenin özelliklerini veya bir komut dosyası değerini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="8fb51-109">The displayed data can include the properties of an object or the value of a script.</span></span> <span data-ttu-id="8fb51-110">İki özellik bir nesnenin değerini ekleme ve sonra veri bir parçası toplam görüntüleme gibi bir nesnenin özelliklerinden doğrudan kullanılabilir olmayan bir değer görüntülemek istiyorsanız, betikleri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8fb51-110">Scripts are used if you want to display some value that is not available directly from the properties of an object, such as adding the value of two properties of an object and then displaying the sum as a piece of data.</span></span> <span data-ttu-id="8fb51-111">Görüntülenen verilerin biçimlendirmesini görünümleri görüntülemek istediğiniz nesnelerin tanımlayarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="8fb51-111">Formatting of the displayed data is done by defining views for the objects that you want to display.</span></span> <span data-ttu-id="8fb51-112">Tanımlayabileceğiniz her nesne için tek bir görünümde, tek bir görünümde birden çok nesne için tanımlayabileceğiniz veya aynı nesne için birden çok görünüm tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8fb51-112">You can define a single view for each object, you can define a single view for multiple objects, or you can define multiple views for the same object.</span></span> <span data-ttu-id="8fb51-113">Tanımlayabileceğiniz görünümleri sayısı sınırı yoktur.</span><span class="sxs-lookup"><span data-stu-id="8fb51-113">There is no limit to the number of views that you can define.</span></span>

## <a name="common-features-of-formatting-files"></a><span data-ttu-id="8fb51-114">Biçimlendirme dosyalarının genel özellikleri</span><span class="sxs-lookup"><span data-stu-id="8fb51-114">Common Features of Formatting Files</span></span>

<span data-ttu-id="8fb51-115">Biçimlendirme her dosya, dosya tarafından tanımlanan tüm görünümleri arasında paylaşılabilir bulunan aşağıdaki bileşenleri tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8fb51-115">Each formatting file can define the following components that can be shared across all the views defined by the file:</span></span>

- <span data-ttu-id="8fb51-116">Varsayılan yapılandırma ayarı, veri sütunun genişliği uzunsa gibi olup olmadığını ve sonraki satırda tabloları satırlarda gösterilen veriler görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="8fb51-116">Default configuration setting, such as whether the data displayed in the rows of tables will be displayed on the next line if the data is longer than the width of the column.</span></span> <span data-ttu-id="8fb51-117">Bu ayarlar hakkında daha fazla bilgi için bkz. [ortak yapılandırma ayarlarını tanımlayan](./defining-common-configuration-features.md).</span><span class="sxs-lookup"><span data-stu-id="8fb51-117">For more information about these settings, see [Defining Common Configuration Settings](./defining-common-configuration-features.md).</span></span>

- <span data-ttu-id="8fb51-118">Görünümlerden herhangi birinde biçimlendirme dosyanın tarafından görüntülenebilen nesneler ayarlar.</span><span class="sxs-lookup"><span data-stu-id="8fb51-118">Sets of objects that can be displayed by any of the views of the formatting file.</span></span> <span data-ttu-id="8fb51-119">Bu ayarlar hakkında daha fazla bilgi için (denir *seçimi ayarlar*), bkz: [tanımlama ayarlar nesnelerin](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="8fb51-119">For more information about these sets (referred to as *selection sets*), see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

- <span data-ttu-id="8fb51-120">Biçimlendirme dosyanın tüm görünümler tarafından kullanılan ortak denetimler.</span><span class="sxs-lookup"><span data-stu-id="8fb51-120">Common controls that can be used by all the views of the formatting file.</span></span> <span data-ttu-id="8fb51-121">Denetimler, verilerin nasıl görüntüleneceğini üzerinde daha hassas bir denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="8fb51-121">Controls give you finer control on how data is displayed.</span></span> <span data-ttu-id="8fb51-122">Denetimleri hakkında daha fazla bilgi için bkz. [tanımlama özel denetimler](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="8fb51-122">For more information about controls, see [Defining Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="formatting-views"></a><span data-ttu-id="8fb51-123">Biçimlendirme görünümleri</span><span class="sxs-lookup"><span data-stu-id="8fb51-123">Formatting Views</span></span>

<span data-ttu-id="8fb51-124">Bir tablo biçiminde, liste biçimini, geniş bir biçim ve özel biçim, biçimlendirme görünümleri nesneleri görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8fb51-124">Formatting views can display objects in a table format, list format, wide format, and custom format.</span></span> <span data-ttu-id="8fb51-125">Çoğunlukla, her biçimlendirme tanımı bir görünüm açıklayan XML etiketleri kümesi tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="8fb51-125">For the most part, each formatting definition is described by a set of XML tags that describe the view.</span></span> <span data-ttu-id="8fb51-126">Her görünümü, görünümün adını Görünüm ve Tablo görünümü için sütun ve satır bilgileri gibi görünümün öğeleri kullanan nesneler içerir.</span><span class="sxs-lookup"><span data-stu-id="8fb51-126">Each view contains the name of the view, the objects that use the view, and the elements of the view, such as the column and row information for a table view.</span></span>

<span data-ttu-id="8fb51-127">Tablo görünümü bir nesne veya bir betik bloğu değerinde bir veya daha fazla sütun özelliklerini listeler.</span><span class="sxs-lookup"><span data-stu-id="8fb51-127">Table View Lists the properties of an object or a script block value in one or more columns.</span></span> <span data-ttu-id="8fb51-128">Her sütunun tek bir özellik nesnesinin veya bir komut dosyası değerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8fb51-128">Each column represents a single property of the object or a script value.</span></span> <span data-ttu-id="8fb51-129">Bir nesne veya özelliklerini ve değerlerini betik birleşimini özelliklerinin bir alt nesneyi tüm özelliklerini gösteren bir tablo görünümü tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8fb51-129">You can define a table view that displays all the properties of an object, a subset of the properties of an object, or a combination of properties and script values.</span></span> <span data-ttu-id="8fb51-130">Tablodaki her satır, döndürülen nesneyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8fb51-130">Each row of the table represents a returned object.</span></span> <span data-ttu-id="8fb51-131">Bir tablo görünümü oluşturma çok benzer bir nesneye kanal zaman `Format-Table` cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="8fb51-131">Creating a table view is very similar to when you pipe an object to the `Format-Table` cmdlet.</span></span> <span data-ttu-id="8fb51-132">Bu görünüm hakkında daha fazla bilgi için bkz: [Tablo görünümü](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="8fb51-132">For more information about this view, see [Table View](./creating-a-table-view.md).</span></span>

<span data-ttu-id="8fb51-133">Görünüm listeler bir nesne veya bir betik değeri tek bir sütunda özelliklerini listeler.</span><span class="sxs-lookup"><span data-stu-id="8fb51-133">List View Lists the properties of an object or a script value in a single column.</span></span> <span data-ttu-id="8fb51-134">Her satır listenin isteğe bağlı bir etiket veya özellik veya betik değeri tarafından izlenen özellik adını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="8fb51-134">Each row of the list displays an optional label or the property name followed by the value of the property or script.</span></span> <span data-ttu-id="8fb51-135">Bir liste görünümü oluşturmak için bir nesneye akışkan çok benzer `Format-List` cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="8fb51-135">Creating a list view is very similar to piping an object to the `Format-List` cmdlet.</span></span> <span data-ttu-id="8fb51-136">Bu görünüm hakkında daha fazla bilgi için bkz: [liste görünümü](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="8fb51-136">For more information about this view, see [List View](./creating-a-list-view.md).</span></span>

<span data-ttu-id="8fb51-137">Tek bir özellik bir nesnenin ya da bir veya daha fazla sütunda betik değerinde geniş görünüm listeler.</span><span class="sxs-lookup"><span data-stu-id="8fb51-137">Wide View Lists a single property of an object or a script value in one or more columns.</span></span> <span data-ttu-id="8fb51-138">Bu görünüm için üst bilgi veya etiket yoktur.</span><span class="sxs-lookup"><span data-stu-id="8fb51-138">There is no label or header for this view.</span></span> <span data-ttu-id="8fb51-139">Geniş bir görünüm oluşturmak için bir nesneye akışkan çok benzer `Format-Wide` cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="8fb51-139">Creating a wide view is very similar to piping an object to the `Format-Wide` cmdlet.</span></span> <span data-ttu-id="8fb51-140">Bu görünüm hakkında daha fazla bilgi için bkz: [geniş Görünüm](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="8fb51-140">For more information about this view, see [Wide View](./creating-a-wide-view.md).</span></span>

<span data-ttu-id="8fb51-141">Özel Görünüm katı yapısını tablo görünümleri, liste görünümleri veya geniş görünümleri için belirtime uymuyor özelleştirilebilir bir görünümü nesne özelliklerini veya betik değerleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="8fb51-141">Custom View Displays a customizable view of object properties or script values that does not adhere to the rigid structure of table views, list views, or wide views.</span></span> <span data-ttu-id="8fb51-142">Tablo görünümü veya liste görünümü gibi başka bir görünüm tarafından kullanılan özel bir görünüm tanımlayabilirsiniz veya tek başına bir özel görünüm tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8fb51-142">You can define a stand-alone custom view, or you can define a custom view that is used by another view, such as a table view or list view.</span></span> <span data-ttu-id="8fb51-143">Özel görünüm oluşturmak için bir nesneye akışkan çok benzer `Format-Custom` cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="8fb51-143">Creating a custom view is very similar to piping an object to the `Format-Custom` cmdlet.</span></span> <span data-ttu-id="8fb51-144">Bu görünüm hakkında daha fazla bilgi için bkz: [Özel Görünüm](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="8fb51-144">For more information about this view, see [Custom View](./creating-custom-controls.md).</span></span>

## <a name="components-of-a-view"></a><span data-ttu-id="8fb51-145">Görünüm bileşenleri</span><span class="sxs-lookup"><span data-stu-id="8fb51-145">Components of a View</span></span>

<span data-ttu-id="8fb51-146">Aşağıdaki XML örnekler bir görünümü temel XML bileşenlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="8fb51-146">The following XML examples show the basic XML components of a view.</span></span> <span data-ttu-id="8fb51-147">Tek tek XML öğeleri oluşturmak istediğiniz hangi görünüme bağlı olarak farklılık gösterir, ancak temel bileşenler görünümlerinin tüm aynıdır.</span><span class="sxs-lookup"><span data-stu-id="8fb51-147">The individual XML elements vary depending on which view you want to create, but the basic components of the views are all the same.</span></span>

<span data-ttu-id="8fb51-148">Her görünüm ile başlamak sahip bir `Name` öğesi görünümü başvurmak için kullanılan bir kullanıcı dostu adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="8fb51-148">To start with, each view has a `Name` element that specifies a user friendly name that is used to reference the view.</span></span> <span data-ttu-id="8fb51-149">bir `ViewSelectedBy` tanımlayan hangi .NET nesneleri görünüm tarafından görüntülenen öğe ve bir *denetimi* görünümü tanımlayan öğe.</span><span class="sxs-lookup"><span data-stu-id="8fb51-149">a `ViewSelectedBy` element that defines which .NET objects are displayed by the view, and a *control* element that defines the view.</span></span>

```xml
<ViewDefinitions>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <ListControl>...</ListControl>
  <View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <WideControl>...</WideControl>
  <View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <CustomControl>...</CustomControl>
  </View>
</ViewDefinitions>

```

<span data-ttu-id="8fb51-150">Denetim öğesi içinde bir veya daha fazla tanımlayabilirsiniz *giriş* öğeleri.</span><span class="sxs-lookup"><span data-stu-id="8fb51-150">Within the control element, you can define one or more *entry* elements.</span></span> <span data-ttu-id="8fb51-151">Birden çok tanım kullanırsanız, her tanımı hangi .NET nesnelerini kullanmak belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8fb51-151">If you use multiple definitions, you must specify which .NET objects use each definition.</span></span> <span data-ttu-id="8fb51-152">Genellikle yalnızca bir tanımı ile yalnızca bir giriş her denetim için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="8fb51-152">Typically only one entry, with only one definition, is needed for each control.</span></span>

```xml
<ListControl>
  <ListEntries>
    <ListEntry>
      <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
    <ListEntry>
        <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
    <ListEntry>
        <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
  </ListEntries>
</ListControl>

```

<span data-ttu-id="8fb51-153">Her giriş öğesi görünümü içinde belirttiğiniz *öğesi* , görünüm tarafından görüntülenen betikleri ve .NET özellikleri tanımlayan öğeler.</span><span class="sxs-lookup"><span data-stu-id="8fb51-153">Within each entry element of a view, you specify the *item* elements that define the .NET properties or scripts that are displayed by that view.</span></span>

```xml

<ListItems>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
</ListItems>

```

<span data-ttu-id="8fb51-154">Yukarıdaki örneklerde gösterildiği gibi biçimlendirme dosyası birden çok görünüm içerebilir, bir görünüm, birden çok tanım içerebilir ve her tanım, birden çok öğe içerebilir.</span><span class="sxs-lookup"><span data-stu-id="8fb51-154">As shown in the preceding examples, the formatting file can contain multiple views, a view can contain multiple definitions, and each definition can contain multiple items.</span></span>

## <a name="example-of-a-table-view"></a><span data-ttu-id="8fb51-155">Tablo görünümü örneği</span><span class="sxs-lookup"><span data-stu-id="8fb51-155">Example of a Table View</span></span>

<span data-ttu-id="8fb51-156">Aşağıdaki örnek, iki sütun içeren bir tablo görünümü tanımlamak için kullanılan XML etiketlerinin gösterir.</span><span class="sxs-lookup"><span data-stu-id="8fb51-156">The following example shows the XML tags used to define a table view that contains two columns.</span></span> <span data-ttu-id="8fb51-157">[ViewDefinitions](./viewdefinitions-element-format.md) öğedir biçimlendirme dosyasında tanımlanan tüm görünümleri için kapsayıcı öğe.</span><span class="sxs-lookup"><span data-stu-id="8fb51-157">The [ViewDefinitions](./viewdefinitions-element-format.md) element is the container element for all the views defined in the formatting file.</span></span> <span data-ttu-id="8fb51-158">[Görünümü](./view-element-format.md) öğe, belirli bir tablo, liste, geniş veya özel görünüm tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8fb51-158">The [View](./view-element-format.md) element defines the specific table, list, wide, or custom view.</span></span> <span data-ttu-id="8fb51-159">Her [görünümü](./view-element-format.md) öğesi [adı](./name-element-for-view-format.md) öğesi, görünümün adını belirtir [ViewSelectedBy](./viewselectedby-element-format.md) öğesi görünümü ve farklı nesneleri tanımlar öğeleri (gibi `TableControl` aşağıdaki örnekte gösterildiği gibi) görünüm türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8fb51-159">Within each [View](./view-element-format.md) element, the [Name](./name-element-for-view-format.md) element specifies the name of the view, the [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view, and the different control elements (such as the `TableControl` element shown in the following example) define the type of the view.</span></span>

```xml
<ViewDefinitions>
  <View>
    <Name>Name of View</Name>
    <ViewSelectedBy>
      <TypeName>Object to display using this view</TypeName>
      <TypeName>Object to display using this view</TypeName>
    </ViewSelectedBy>
    <TableControl>
      <TableHeaders>
        <TableColumnHeader>
          <Width></Width>
        </TableColumnHeader>
        <TableColumnHeader>
          <Width></Width>
        </TableColumnHeader>
      </TableHeaders>
      <TableRowEntries>
        <TableRowEntry>
          <TableColumnItems>
            <TableColumnItem>
              <PropertyName>Header for column 1</PropertyName>
            </TableColumnItem>
            <TableColumnItem>
              <PropertyName>Header for column 2</PropertyName>
            </TableColumnItem>
          </TableColumnItems>
        </TableRowEntry>
      </TableRowEntries>
    </TableControl)
  </View>
</ViewDefinitions>

```

## <a name="see-also"></a><span data-ttu-id="8fb51-160">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="8fb51-160">See Also</span></span>

[<span data-ttu-id="8fb51-161">Bir liste görünümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="8fb51-161">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="8fb51-162">Bir tablo görünümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="8fb51-162">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="8fb51-163">Geniş bir görünüm oluşturma</span><span class="sxs-lookup"><span data-stu-id="8fb51-163">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="8fb51-164">Özel denetimler oluşturma</span><span class="sxs-lookup"><span data-stu-id="8fb51-164">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="8fb51-165">Bir PowerShell biçimlendirme ve türleri dosyası yazma</span><span class="sxs-lookup"><span data-stu-id="8fb51-165">Writing a PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
