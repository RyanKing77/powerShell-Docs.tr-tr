---
title: LISTITEM öğesinin ListControl (biçimi) için ListItems için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f96f4f5-8bd5-43ed-95e7-a7358115999a
caps.latest.revision: 11
ms.openlocfilehash: 1e0a1b2d20853650328b8cfd1513a08f7e167cd6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065776"
---
# <a name="listitem-element-for-listitems-for-listcontrol-format"></a><span data-ttu-id="bc703-102">ListControl ListItems için ListItem Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="bc703-102">ListItem Element for ListItems for ListControl (Format)</span></span>

<span data-ttu-id="bc703-103">Betik değeri liste görünümünün bir satır görüntülenir ve özelliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bc703-103">Defines the property or script whose value is displayed in a row of the list view.</span></span>

<span data-ttu-id="bc703-104">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) ListControl öğesi (biçimi) ListEntries öğesi ListControl (biçimi) ListEntry öğesinin ListControl (biçimi) ListItems öğesinin ListControl (biçimi) ListItem ListControl öğesinin (biçimi)</span><span class="sxs-lookup"><span data-stu-id="bc703-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format) ListItem for ListControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bc703-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bc703-105">Syntax</span></span>

```xml
<ListItem>
  <PropertyName>PropertyToDisplay</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <Label>LabelToDisplay</Label>
  <FormatString>FormatPattern</FormatString>
  <ItemSelectionCondition>...</ItemSelectionCondition>
</ListItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bc703-106">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="bc703-106">Attributes and Elements</span></span>

<span data-ttu-id="bc703-107">Aşağıdaki öznitelikler, alt ve üst öğenin bölümlerde `ListItem` öğesi.</span><span class="sxs-lookup"><span data-stu-id="bc703-107">The following sections describe the attributes, child elements, and parent element of the `ListItem` element.</span></span> <span data-ttu-id="bc703-108">Yalnızca bir özellik veya komut dosyası belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="bc703-108">Only one property or script can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="bc703-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bc703-109">Attributes</span></span>

<span data-ttu-id="bc703-110">Yok</span><span class="sxs-lookup"><span data-stu-id="bc703-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="bc703-111">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="bc703-111">Child Elements</span></span>

|<span data-ttu-id="bc703-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="bc703-112">Element</span></span>|<span data-ttu-id="bc703-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bc703-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bc703-114">ListItem ListControl (biçimi) için için FormatString öğesi</span><span class="sxs-lookup"><span data-stu-id="bc703-114">FormatString Element for ListItem for ListControl (Format)</span></span>](./formatstring-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="bc703-115">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="bc703-115">Optional element.</span></span><br /><br /> <span data-ttu-id="bc703-116">Özellik veya betik değerin nasıl görüntüleneceğini tanımlayan bir biçim dizesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="bc703-116">Specifies a format string that defines how the property or script value is displayed.</span></span>|
|[<span data-ttu-id="bc703-117">ListItem ListControl (biçimi) için için ItemSelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="bc703-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="bc703-118">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="bc703-118">Optional element.</span></span><br /><br /> <span data-ttu-id="bc703-119">Bu liste öğesi için kullanılacak bulunmalıdır koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bc703-119">Defines the condition that must exist for this list item to be used.</span></span>|
|[<span data-ttu-id="bc703-120">ListItem ListControl (biçimi) için için etiket öğesi</span><span class="sxs-lookup"><span data-stu-id="bc703-120">Label Element for ListItem for ListControl (Format)</span></span>](./label-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="bc703-121">İsteğe bağlı öğe</span><span class="sxs-lookup"><span data-stu-id="bc703-121">Optional element</span></span><br /><br /> <span data-ttu-id="bc703-122">Sol özellik veya betik değerin satırında görüntülenen etiketi belirtir.</span><span class="sxs-lookup"><span data-stu-id="bc703-122">Specifies the label that is displayed to the left of the property or script value in the row.</span></span>|
|[<span data-ttu-id="bc703-123">ListItem ListControl (biçimi) için için PropertyName öğesi</span><span class="sxs-lookup"><span data-stu-id="bc703-123">PropertyName Element for ListItem for ListControl (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="bc703-124">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="bc703-124">Optional element.</span></span><br /><br /> <span data-ttu-id="bc703-125">.NET özelliğinin değeri satırda görüntülenen belirtir.</span><span class="sxs-lookup"><span data-stu-id="bc703-125">Specifies the .NET property whose value is displayed in the row.</span></span>|
|[<span data-ttu-id="bc703-126">ListItem ListControl (biçimi) için için ScriptBlock öğesi</span><span class="sxs-lookup"><span data-stu-id="bc703-126">ScriptBlock Element for ListItem for ListControl (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="bc703-127">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="bc703-127">Optional element.</span></span><br /><br /> <span data-ttu-id="bc703-128">Betikte satır değeri görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="bc703-128">Specifies the script whose value is displayed in the row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="bc703-129">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="bc703-129">Parent Elements</span></span>

|<span data-ttu-id="bc703-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="bc703-130">Element</span></span>|<span data-ttu-id="bc703-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bc703-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bc703-132">Liste denetimi (biçimi) için ListItems öğesi</span><span class="sxs-lookup"><span data-stu-id="bc703-132">ListItems Element for List Control (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="bc703-133">Betikleri değerleri liste görünümünde görüntülenir ve özellikleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bc703-133">Defines the properties and scripts whose values are displayed in the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="bc703-134">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bc703-134">Remarks</span></span>

<span data-ttu-id="bc703-135">Bir liste görünümü bileşenler hakkında daha fazla bilgi için bkz. [bir liste görünümü oluşturma](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="bc703-135">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="bc703-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="bc703-136">Example</span></span>

<span data-ttu-id="bc703-137">Bu örnek, liste görünümü üç satırı tanımlayan XML öğeleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="bc703-137">This example shows the XML elements that define three rows of the list view.</span></span> <span data-ttu-id="bc703-138">Bir .NET özelliğinin değeri ilk iki satırını görüntülemek ve son satırını bir betik tarafından oluşturulan bir değer görüntüler.</span><span class="sxs-lookup"><span data-stu-id="bc703-138">The first two rows display the value of a .NET property, and the last row displays a value generated by a script.</span></span>

```xml
<ListEntry>
    <ListItems>
      <ListItem>
        <Label>Property1: </Label>
        <PropertyName>DotNetProperty1</PropertyName>
      </ListItem>
      <ListItem>
        <PropertyName>DotNetProperty2</PropertyName>
      </ListItem>
      <ListItem>
        <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
      </ListItem>
    </ListItems>
</ListEntry>

```

## <a name="see-also"></a><span data-ttu-id="bc703-139">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="bc703-139">See Also</span></span>

[<span data-ttu-id="bc703-140">ListItems öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="bc703-140">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="bc703-141">ListItem (biçimi) için FormatString öğesi</span><span class="sxs-lookup"><span data-stu-id="bc703-141">FormatString Element for ListItem (Format)</span></span>](./formatstring-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="bc703-142">ListItem (biçimi) için etiket öğesi</span><span class="sxs-lookup"><span data-stu-id="bc703-142">Label Element for ListItem (Format)</span></span>](./label-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="bc703-143">ListItem (biçimi) için PropertyName öğesi</span><span class="sxs-lookup"><span data-stu-id="bc703-143">PropertyName Element for ListItem (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="bc703-144">ListItem (biçimi) için ScriptBlock öğesi</span><span class="sxs-lookup"><span data-stu-id="bc703-144">ScriptBlock Element for ListItem (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="bc703-145">Bir liste görünümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="bc703-145">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="bc703-146">Biçimlendirme bir Windows PowerShell yazma ve dosya türleri</span><span class="sxs-lookup"><span data-stu-id="bc703-146">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
