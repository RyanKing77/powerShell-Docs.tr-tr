---
title: Seçimi kümesini tanımlayan | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 00dbb5ee-93d4-4914-a082-ef4d8b236b5c
caps.latest.revision: 16
ms.openlocfilehash: 596212f2e64401a751cf3dca0ee7d60b80912c00
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066320"
---
# <a name="defining-selection-sets"></a><span data-ttu-id="9fc36-102">Seçim Kümeleri Tanımlama</span><span class="sxs-lookup"><span data-stu-id="9fc36-102">Defining Selection Sets</span></span>

<span data-ttu-id="9fc36-103">Birden çok görünüm ve denetimleri oluşturma, başvurulan nesne kümeleri seçimi kümeleri olarak tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9fc36-103">When creating multiple views and controls, you can define sets of objects that are referred to as selection sets.</span></span> <span data-ttu-id="9fc36-104">Seçimi kümesi bunları her görünüm veya denetim için sürekli olarak tanımlamak zorunda kalmadan nesneleri bir kez tanımlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="9fc36-104">A selection set enables you to define the objects one time, without having to define them repeatedly for each view or control.</span></span> <span data-ttu-id="9fc36-105">Genellikle, ilişkili .NET nesneleri kümeniz seçimi ayarlar kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9fc36-105">Typically, selection sets are used when you have a set of related .NET objects.</span></span> <span data-ttu-id="9fc36-106">Örneğin, `FileSystem` biçimlendirme dosyası (FileSystem.format.ps1xml) birkaç görünüm kullanan dosya sistemi türlerini seçimi kümesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9fc36-106">For example, The `FileSystem` formatting file (FileSystem.format.ps1xml) defines a selection set of the file system types that several views use.</span></span>

## <a name="where-selection-sets-are-defined-and-referenced"></a><span data-ttu-id="9fc36-107">Seçimi ayarlar tanımlanan ve başvurulan olduğu</span><span class="sxs-lookup"><span data-stu-id="9fc36-107">Where Selection Sets are Defined and Referenced</span></span>

<span data-ttu-id="9fc36-108">Tüm görünümler ve biçimlendirme dosyasında tanımlanan denetimleri tarafından kullanılan ortak verileri bir parçası olarak seçimi kümelerini tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="9fc36-108">You define selection sets as part of the common data that can be used by all the views and controls defined in the formatting file.</span></span> <span data-ttu-id="9fc36-109">Aşağıdaki örnek, üç seçim kümesi tanımlamak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9fc36-109">The following example shows how to define three selection sets.</span></span>

```xml
<Configuration>
  <SelectionSets>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
  </SelectionSets>
</Configuration>
```

<span data-ttu-id="9fc36-110">Bir seçim başvurabilirsiniz aşağıdaki yollarla ayarlar:</span><span class="sxs-lookup"><span data-stu-id="9fc36-110">You can reference a selection sets in the following ways:</span></span>

- <span data-ttu-id="9fc36-111">Her görünüm sahip bir `ViewSelectedBy` görünümü kullanarak hangi nesnelerinin görüntülenme şeklini tanımlayan öğe.</span><span class="sxs-lookup"><span data-stu-id="9fc36-111">Each view has a `ViewSelectedBy` element that defines which objects are displayed by using the view.</span></span> <span data-ttu-id="9fc36-112">`ViewSelectedBy` Öğeye sahip bir `SelectionSetName` seçimi belirtir. alt öğe kümesi, görünüm kullanımı tüm tanımları.</span><span class="sxs-lookup"><span data-stu-id="9fc36-112">The `ViewSelectedBy` element has a `SelectionSetName` child element that specifies the selection set that all the definitions of the view use.</span></span> <span data-ttu-id="9fc36-113">Sayısına ilişkin bir görünümden başvurabilirsiniz seçimi ayarlar bir kısıtlama yoktur.</span><span class="sxs-lookup"><span data-stu-id="9fc36-113">There is no restriction on the number of selection sets that you can reference from a view.</span></span>

- <span data-ttu-id="9fc36-114">Bir görünüm veya denetim, her tanımındaki `EntrySelectedBy` öğe tanımlar hangi nesnelerin bu tanımı kullanılarak görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="9fc36-114">In each definition of a view or control, the `EntrySelectedBy` element defines which objects are displayed by using that definition.</span></span> <span data-ttu-id="9fc36-115">Nesneleri tarafından tanımlanmış genellikle bir görünüm veya denetimi sadece bir tanım sahiptir, bu nedenle `ViewSelectedBy` öğesi.</span><span class="sxs-lookup"><span data-stu-id="9fc36-115">Typically a view or control has only one definition so the objects are defined by the `ViewSelectedBy` element.</span></span> <span data-ttu-id="9fc36-116">`EntrySelectedBy` Tanımının öğeye sahip bir `SelectionSetName` seçimi belirtir alt öğesi.</span><span class="sxs-lookup"><span data-stu-id="9fc36-116">The `EntrySelectedBy` element of the definition has a `SelectionSetName` child element that specifies the selection set.</span></span> <span data-ttu-id="9fc36-117">Seçimi için bir tanım Ayarla belirtirseniz, diğer alt öğelerini belirtemezsiniz `EntrySelectedBy` öğesi.</span><span class="sxs-lookup"><span data-stu-id="9fc36-117">If you specify the selection set for a definition, you cannot specify any of the other child elements of the `EntrySelectedBy` element.</span></span>

- <span data-ttu-id="9fc36-118">Bir görünüm veya denetim, her tanımındaki `SelectionCondition` öğesi tanımı kullanıldığında koşulu belirtmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9fc36-118">In each definition of a view or control, the `SelectionCondition` element can be used to specify a condition for when the definition is used.</span></span> <span data-ttu-id="9fc36-119">`SelectionCondition` Öğeye sahip bir `SelectionSetName` Seçimi Ayarla belirten alt öğesi koşul tetikler.</span><span class="sxs-lookup"><span data-stu-id="9fc36-119">The `SelectionCondition` element has a `SelectionSetName` child element that specifies the selection set that triggers the condition.</span></span> <span data-ttu-id="9fc36-120">Seçimi kümesinde tanımlanan nesnelerden herhangi birini görüntülendiğinde koşul tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="9fc36-120">The condition is triggered when any of the objects defined in the selection set are displayed.</span></span> <span data-ttu-id="9fc36-121">Bu koşullar ayarlama hakkında daha fazla bilgi için bkz. [veri görüntülendiğinde için koşulları tanımlama](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="9fc36-121">For more information about how to set these conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="selection-set-example"></a><span data-ttu-id="9fc36-122">Örnek Seçimi Ayarla</span><span class="sxs-lookup"><span data-stu-id="9fc36-122">Selection Set Example</span></span>

<span data-ttu-id="9fc36-123">Aşağıdaki örnek, doğrudan yapılan bir seçim kümesi gösterir `FileSystem` Windows PowerShell tarafından sağlanan dosya biçimlendirme.</span><span class="sxs-lookup"><span data-stu-id="9fc36-123">The following example shows a selection set that is taken directly from the `FileSystem` formatting file provided by Windows PowerShell.</span></span> <span data-ttu-id="9fc36-124">Dosyaları biçimlendirme diğer Windows PowerShell hakkında daha fazla bilgi için bkz. [Windows PowerShell biçimlendirme dosyaları](./powershell-formatting-files.md).</span><span class="sxs-lookup"><span data-stu-id="9fc36-124">For more information about other Windows PowerShell formatting files, see [Windows PowerShell Formatting Files](./powershell-formatting-files.md).</span></span>

```xml
<SelectionSets>
  <SelectionSet>
    <Name>FileSystemTypes</Name>
    <Types>
     <TypeName>System.IO.DirectoryInfo</TypeName>
     <TypeName>System.IO.FileInfo</TypeName>
     <TypeName>Deserialized.System.IO.DirectoryInfo</TypeName>
     <TypeName>Deserialized.System.IO.FileInfo</TypeName>
    </Types>
  </SelectionSet>
</SelectionSets>
```

<span data-ttu-id="9fc36-125">Önceki seçimi kümesi başvurulduğundan `ViewSelectedBy` Tablo görünümüne öğesidir.</span><span class="sxs-lookup"><span data-stu-id="9fc36-125">The previous selection set is referenced in the `ViewSelectedBy` element of a table view.</span></span>

```xml
<ViewDefinitions>
  <View>
    <Name>Files</Name>
    <ViewSelectedBy>
      <SelectionSetName>FileSystemTypes</SelectionSetName>
    </ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
</ViewDefinitions>

```

## <a name="xml-elements"></a><span data-ttu-id="9fc36-126">XML öğeleri</span><span class="sxs-lookup"><span data-stu-id="9fc36-126">XML Elements</span></span>

 <span data-ttu-id="9fc36-127">Tanımlayabileceğiniz seçimi ayarlar sayısı sınırı yoktur.</span><span class="sxs-lookup"><span data-stu-id="9fc36-127">There is no limit to the number of selection sets that you can define.</span></span> <span data-ttu-id="9fc36-128">Aşağıdaki XML öğeleri, bir seçim kümesi oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9fc36-128">The following XML elements are used to create a selection set.</span></span>

- <span data-ttu-id="9fc36-129">[SelectionSets](./selectionsets-element-format.md) öğe görünümler tarafından başvurulan .NET nesne kümesi ve biçimlendirme dosyanın denetimleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9fc36-129">The [SelectionSets](./selectionsets-element-format.md) element defines the sets of .NET objects that are referenced by the views and controls of the formatting file.</span></span>

- <span data-ttu-id="9fc36-130">[SelectionSet](./selectionset-element-format.md) öğesi, tek bir .NET nesneleri kümesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9fc36-130">The [SelectionSet](./selectionset-element-format.md) element defines a single set of .NET objects.</span></span>

- <span data-ttu-id="9fc36-131">[Adı](./name-element-for-selectionset-format.md) öğe seçimi kümesi başvurmak için kullanılan adı belirtir.</span><span class="sxs-lookup"><span data-stu-id="9fc36-131">The [Name](./name-element-for-selectionset-format.md) element specifies the name that is used to reference the selection set.</span></span>

- <span data-ttu-id="9fc36-132">[Türleri](./types-element-for-selectionset-format.md) öğesi Nesne Seçimi kümesinin .NET türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9fc36-132">The [Types](./types-element-for-selectionset-format.md) element specifies the .NET types of the objects of the selection set.</span></span> <span data-ttu-id="9fc36-133">(Dosyaları biçimlendirme içinde nesneler .NET türlerine göre belirtilir.)</span><span class="sxs-lookup"><span data-stu-id="9fc36-133">(Within formatting files, objects are specified by their .NET type.)</span></span>

 <span data-ttu-id="9fc36-134">Aşağıdaki XML öğeleri, bir seçim kümesi belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9fc36-134">The following XML elements are used to specify a selection set.</span></span>

- <span data-ttu-id="9fc36-135">Şu öğe görünümü tüm tanımları kullanacak şekilde seçimi belirtir:</span><span class="sxs-lookup"><span data-stu-id="9fc36-135">The following element specifies the selection set to use in all the definitions of the view:</span></span>

    - [<span data-ttu-id="9fc36-136">SelectionSetName öğesi ViewSelectedBy (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="9fc36-136">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)

    - [<span data-ttu-id="9fc36-137">GroupBy (biçimi) için EntrySelectedBy için SelectionSetName öğesi</span><span class="sxs-lookup"><span data-stu-id="9fc36-137">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

- <span data-ttu-id="9fc36-138">Aşağıdaki öğeleri tek bir görünüm tanımı tarafından kullanılan seçimi kümesini belirtin:</span><span class="sxs-lookup"><span data-stu-id="9fc36-138">The following elements specify the selection set used by a single view definition:</span></span>

    - [<span data-ttu-id="9fc36-139">EntrySelectedBy ListControl (biçimi) için için SelectionSetName öğesi</span><span class="sxs-lookup"><span data-stu-id="9fc36-139">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

    - [<span data-ttu-id="9fc36-140">TableControl (biçimi) için EntrySelectedBy için SelectionSetName öğesi</span><span class="sxs-lookup"><span data-stu-id="9fc36-140">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

    - [<span data-ttu-id="9fc36-141">EntrySelectedBy WideControl (biçimi) için için SelectionSetName öğesi</span><span class="sxs-lookup"><span data-stu-id="9fc36-141">SelectionSetName Element for EntrySelectedBy for WideControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

    - [<span data-ttu-id="9fc36-142">SelectionSetName öğesi görünümü (biçimi) için özel denetim için EntrySelectedBy için</span><span class="sxs-lookup"><span data-stu-id="9fc36-142">SelectionSetName Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

- <span data-ttu-id="9fc36-143">Aşağıdaki öğeleri yaygın kullanılan seçimi kümesi belirtin ve denetim tanımları görüntüleyin:</span><span class="sxs-lookup"><span data-stu-id="9fc36-143">The following elements specify the selection set used by common and view control definitions:</span></span>

    - [<span data-ttu-id="9fc36-144">SelectionSetName öğesi görünümü (biçimi) için denetimleri için EntrySelectedBy için</span><span class="sxs-lookup"><span data-stu-id="9fc36-144">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)

    - [<span data-ttu-id="9fc36-145">İçin yapılandırma (biçimi) için denetimleri için EntrySelectedBy SelectionSetName öğesi</span><span class="sxs-lookup"><span data-stu-id="9fc36-145">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format.md)

- <span data-ttu-id="9fc36-146">Aşağıdaki öğeleri genişletmek için hangi nesne tanımlarken kullanılan seçimi kümesini belirtin:</span><span class="sxs-lookup"><span data-stu-id="9fc36-146">The following elements specify the selection set used when you define which object to expand:</span></span>

    - [<span data-ttu-id="9fc36-147">EntrySelectedBy EnumerableExpansion (biçimi) için için SelectionSetName öğesi</span><span class="sxs-lookup"><span data-stu-id="9fc36-147">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

- <span data-ttu-id="9fc36-148">Aşağıdaki öğeleri seçimi koşulları tarafından kullanılan seçimi kümesi belirtin.</span><span class="sxs-lookup"><span data-stu-id="9fc36-148">The following elements specify the selection set used by selection conditions.</span></span>

    - [<span data-ttu-id="9fc36-149">İçin yapılandırma (biçimi) için denetimleri için SelectionCondition SelectionSetName öğesi</span><span class="sxs-lookup"><span data-stu-id="9fc36-149">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

    - [<span data-ttu-id="9fc36-150">SelectionSetName öğesi görünümü (biçimi) için denetimleri için SelectionCondition için</span><span class="sxs-lookup"><span data-stu-id="9fc36-150">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

    - [<span data-ttu-id="9fc36-151">SelectionSetName öğesi görünümü (biçimi) için özel denetim için SelectionCondition için</span><span class="sxs-lookup"><span data-stu-id="9fc36-151">SelectionSetName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

    - [<span data-ttu-id="9fc36-152">SelectionCondition EnumerableExpansion (biçimi) için EntrySelectedBy için için SelectionSetName öğesi</span><span class="sxs-lookup"><span data-stu-id="9fc36-152">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

    - [<span data-ttu-id="9fc36-153">SelectionCondition ListEntry (biçimi) için EntrySelectedBy için için SelectionSetName öğesi</span><span class="sxs-lookup"><span data-stu-id="9fc36-153">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)

    - [<span data-ttu-id="9fc36-154">TableControl (biçimi) için EntrySelectedBy için SelectionCondition için SelectionSetName öğesi</span><span class="sxs-lookup"><span data-stu-id="9fc36-154">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

    - [<span data-ttu-id="9fc36-155">SelectionCondition WideEntry (biçimi) için EntrySelectedBy için için SelectionSetName öğesi</span><span class="sxs-lookup"><span data-stu-id="9fc36-155">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

    - [<span data-ttu-id="9fc36-156">GroupBy (biçimi) için SelectionCondition için SelectionSetName öğesi</span><span class="sxs-lookup"><span data-stu-id="9fc36-156">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)

## <a name="see-also"></a><span data-ttu-id="9fc36-157">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="9fc36-157">See Also</span></span>

[<span data-ttu-id="9fc36-158">SelectionSets</span><span class="sxs-lookup"><span data-stu-id="9fc36-158">SelectionSets</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="9fc36-159">SelectionSet</span><span class="sxs-lookup"><span data-stu-id="9fc36-159">SelectionSet</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="9fc36-160">Ad</span><span class="sxs-lookup"><span data-stu-id="9fc36-160">Name</span></span>](./name-element-for-selectionset-format.md)

[<span data-ttu-id="9fc36-161">Türleri</span><span class="sxs-lookup"><span data-stu-id="9fc36-161">Types</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="9fc36-162">PowerShell biçimlendirme dosyaları</span><span class="sxs-lookup"><span data-stu-id="9fc36-162">PowerShell Formatting Files</span></span>](./powershell-formatting-files.md)

[<span data-ttu-id="9fc36-163">Veri görüntülendiğinde koşulları tanımlama</span><span class="sxs-lookup"><span data-stu-id="9fc36-163">Defining Conditions for when Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="9fc36-164">Bir PowerShell biçimlendirme ve türleri dosyası yazma</span><span class="sxs-lookup"><span data-stu-id="9fc36-164">Writing a PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
