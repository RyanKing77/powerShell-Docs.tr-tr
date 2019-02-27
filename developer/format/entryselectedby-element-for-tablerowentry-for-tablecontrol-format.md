---
title: TableControl (biçimi) için TableRowEntry için EntrySelectedBy öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49623fcf-1238-4d20-a7ce-238d47d9d565
caps.latest.revision: 15
ms.openlocfilehash: e18564c10898c73128e0a4bc7d077e7c7ffb1c22
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851243"
---
# <a name="entryselectedby-element-for-tablerowentry--for-tablecontrol-format"></a><span data-ttu-id="a7103-102">TableControl TableRowEntry için EntrySelectedBy Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="a7103-102">EntrySelectedBy Element for TableRowEntry  for TableControl (Format)</span></span>

<span data-ttu-id="a7103-103">Tablo görünümü veya bu tanım için kullanılacak bulunmalıdır koşul bu tanımı kullanan .NET türlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a7103-103">Defines the .NET types that use this definition of the table view or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="a7103-104">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) TableControl öğesi (biçimi) TableRowEntries öğesi (biçimi) TableRowEntry öğesi (biçimi) EntrySelectedBy öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="a7103-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a7103-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a7103-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a7103-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a7103-106">Attributes and Elements</span></span>

<span data-ttu-id="a7103-107">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `EntrySelectedBy` öğesi.</span><span class="sxs-lookup"><span data-stu-id="a7103-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a7103-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a7103-108">Attributes</span></span>

<span data-ttu-id="a7103-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="a7103-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a7103-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a7103-110">Child Elements</span></span>

|<span data-ttu-id="a7103-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="a7103-111">Element</span></span>|<span data-ttu-id="a7103-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a7103-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a7103-113">TableControl (biçimi) için EntrySelectedBy için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="a7103-113">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="a7103-114">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="a7103-114">Optional element.</span></span><br /><br /> <span data-ttu-id="a7103-115">Bu tablo görünümü tanımını kullanılacak bulunmalıdır koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a7103-115">Defines the condition that must exist for this table view definition to be used.</span></span>|
|[<span data-ttu-id="a7103-116">TableControl (biçimi) için EntrySelectedBy için SelectionSetName öğesi</span><span class="sxs-lookup"><span data-stu-id="a7103-116">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="a7103-117">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="a7103-117">Optional element.</span></span><br /><br /> <span data-ttu-id="a7103-118">Bu tabloda görünüm tanımını kullanma .NET türleri kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a7103-118">Specifies a set of .NET types that use this table view definition.</span></span>|
|[<span data-ttu-id="a7103-119">TableControl (biçimi) için EntrySelectedBy için TypeName öğesi</span><span class="sxs-lookup"><span data-stu-id="a7103-119">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>](./typename-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="a7103-120">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="a7103-120">Optional element.</span></span><br /><br /> <span data-ttu-id="a7103-121">Bu tablo görünümü tanımını kullanan bir .NET türü belirtir.</span><span class="sxs-lookup"><span data-stu-id="a7103-121">Specifies a .NET type that uses this table view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a7103-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a7103-122">Parent Elements</span></span>

|<span data-ttu-id="a7103-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="a7103-123">Element</span></span>|<span data-ttu-id="a7103-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a7103-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a7103-125">TableControl (biçimi) için TableRowEntry öğesi</span><span class="sxs-lookup"><span data-stu-id="a7103-125">TableRowEntry Element for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)|<span data-ttu-id="a7103-126">Bir tablonun satırında görüntülenen verileri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a7103-126">Defines the data that is displayed in a row of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a7103-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a7103-127">Remarks</span></span>

<span data-ttu-id="a7103-128">En az bir türü, seçim kümesi veya bir tablo görünümü tanımını seçim koşulu belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a7103-128">You must specify at least one type, selection set, or selection condition for a table view definition.</span></span> <span data-ttu-id="a7103-129">Kullanabileceğiniz bir alt öğe sayısı maksimum sınırı yoktur.</span><span class="sxs-lookup"><span data-stu-id="a7103-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="a7103-130">Seçimi koşullar bir nesne belirli bir özelliğine sahip olduğunda gibi kullanılacak tanımı için bulunması gereken bir koşul tanımlamak için kullanılır veya bir özel özellik değerini veya betik değerlendiren `true`.</span><span class="sxs-lookup"><span data-stu-id="a7103-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="a7103-131">Seçimi koşullar hakkında daha fazla bilgi için bkz. [tanımlama koşulları için bir görünüm girişi olduğunda veya öğe kullanılan](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="a7103-131">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="a7103-132">Tablo görünümü bileşenler hakkında daha fazla bilgi için bkz. [bir tablo görünümü oluşturma](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="a7103-132">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="a7103-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="a7103-133">Example</span></span>

<span data-ttu-id="a7103-134">Aşağıdaki örnekte gösterildiği bir `TableRowEntry` özelliklerini görüntülemek için kullanılan öğe [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) nesne.</span><span class="sxs-lookup"><span data-stu-id="a7103-134">The following example shows a `TableRowEntry` element that is used to display the properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </EntrySelectedBy>
  <TableColumnItems>
    <TableColumnItem>
      <PropertyName>PropertyForFirstColumn</PropertyName>
    </TableColumnItem>
    <TableColumnItem>
      <PropertyName>PropertyForSecondColumn</PropertyName>
    </TableColumnItem>
  </TableColumnItems>
</TableRowEntry>
```

## <a name="see-also"></a><span data-ttu-id="a7103-135">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="a7103-135">See Also</span></span>

[<span data-ttu-id="a7103-136">Bir tablo görünümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="a7103-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="a7103-137">TableControl (biçimi) için EntrySelectedBy için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="a7103-137">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="a7103-138">TableControl (biçimi) için EntrySelectedBy için SelectionSetName öğesi</span><span class="sxs-lookup"><span data-stu-id="a7103-138">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="a7103-139">TableControl (biçimi) için TableRowEntry öğesi</span><span class="sxs-lookup"><span data-stu-id="a7103-139">TableRowEntry Element for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)

[<span data-ttu-id="a7103-140">TableControl (biçimi) için EntrySelectedBy için TypeName öğesi</span><span class="sxs-lookup"><span data-stu-id="a7103-140">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>](./typename-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="a7103-141">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="a7103-141">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
