---
title: Verileri görüntülemek için koşulları tanımlama | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c1e05821-6aec-437b-84a5-218a5727f88b
caps.latest.revision: 10
ms.openlocfilehash: 8a5b84b6a461e9fc340a5981578d95ca2ac6b9f7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846567"
---
# <a name="defining-conditions-for-displaying-data"></a><span data-ttu-id="aaafc-102">Veri Görüntülemek İçin Koşulları Tanımlama</span><span class="sxs-lookup"><span data-stu-id="aaafc-102">Defining Conditions for Displaying Data</span></span>

<span data-ttu-id="aaafc-103">Hangi verilerin bir görünüm veya denetimi tarafından görüntülenen tanımlarken, görüntülenecek verileri için bulunması gereken bir koşul belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aaafc-103">When defining what data is displayed by a view or a control, you can specify a condition that must exist for the data to be displayed.</span></span> <span data-ttu-id="aaafc-104">Belirli bir özelliğe göre veya bir komut dosyasına koşul tetiklenebilir veya özellik değeri değerlendirilen `true`.</span><span class="sxs-lookup"><span data-stu-id="aaafc-104">The condition can be triggered by a specific property, or when a script or property value evaluates to `true`.</span></span> <span data-ttu-id="aaafc-105">Seçim koşulu karşılandığında, görünüm veya denetim tanımı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="aaafc-105">When the selection condition is met, the definition of the view or control is used.</span></span>

## <a name="specifying-a-selection-condition-for-a-definition"></a><span data-ttu-id="aaafc-106">Tanımı için bir seçim koşulu belirtme</span><span class="sxs-lookup"><span data-stu-id="aaafc-106">Specifying a Selection Condition for a Definition</span></span>

<span data-ttu-id="aaafc-107">Bir görünüm veya denetim için bir tanım oluşturulurken `EntrySelectedBy` öğesi, hangi nesnelerin tanımı kullanır veya tanımı kullanılmak üzere hangi koşul bulunmalıdır belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="aaafc-107">When creating a definition for a view or control, the `EntrySelectedBy` element is used to specify which objects will use the definition or what condition must exist for the definition to be used.</span></span> <span data-ttu-id="aaafc-108">Koşul tarafından belirtilen `SelectionCondition` öğesi.</span><span class="sxs-lookup"><span data-stu-id="aaafc-108">The condition is specified by the `SelectionCondition` element.</span></span>

<span data-ttu-id="aaafc-109">Aşağıdaki örnekte, bir seçim koşulu bir tablo görünümü için bir tanım belirtildi.</span><span class="sxs-lookup"><span data-stu-id="aaafc-109">In the following example, a selection condition is specified for a definition of a table view.</span></span> <span data-ttu-id="aaafc-110">Bu örnekte, yalnızca belirtilen komut için değerlendirilirken tanımı kullanılır `true`.</span><span class="sxs-lookup"><span data-stu-id="aaafc-110">In this example, the definition is used only when the specified script is evaluated to `true`.</span></span>

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <SelectionCondition>
      <ScriptBlock>ScriptToEvaluate</ScriptBlock>
    </SelectionCondition>
  </EntrySelectedBy>
  <TableColumnItems>
  </TableColumnItems>
</TableRowEntry>

```

<span data-ttu-id="aaafc-111">Tanımı bir görünüm veya denetim için belirttiğiniz seçimi koşullar sayısı sınırı yoktur.</span><span class="sxs-lookup"><span data-stu-id="aaafc-111">There is no limit to the number of selection conditions that you can specify for a definition of a view or control.</span></span> <span data-ttu-id="aaafc-112">Yalnızca gereksinimler aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="aaafc-112">The only requirements are the following:</span></span>

- <span data-ttu-id="aaafc-113">Seçim koşulu, bir özellik adı veya koşulu tetiklemesine komut dosyasını belirtmeniz gerekir, ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="aaafc-113">The selection condition must specify one property name or script to trigger the condition, but cannot specify both.</span></span>

- <span data-ttu-id="aaafc-114">Seçim koşulu .NET türleri herhangi bir sayıda belirtebilirsiniz veya seçimi ayarlar, ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="aaafc-114">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

## <a name="specifying-a-selection-condition-for-an-item"></a><span data-ttu-id="aaafc-115">Bir öğe için bir seçim koşulu belirtme</span><span class="sxs-lookup"><span data-stu-id="aaafc-115">Specifying a Selection Condition for an Item</span></span>

<span data-ttu-id="aaafc-116">Bir öğenin bir liste görünümü veya denetimi ekleyerek kullanıldığında belirtebilirsiniz `ItemSelectionCondition` öğesi tanımı öğesi.</span><span class="sxs-lookup"><span data-stu-id="aaafc-116">You can also specify when an item of a list view or control is used by including the `ItemSelectionCondition` element in the item definition.</span></span> <span data-ttu-id="aaafc-117">Aşağıdaki örnekte, bir liste görünümü öğesi için bir seçim koşulu belirtildi.</span><span class="sxs-lookup"><span data-stu-id="aaafc-117">In the following example, a selection condition is specified for an item of a list view.</span></span> <span data-ttu-id="aaafc-118">Bu örnekte, komut dosyası için değerlendirilirken öğesi kullanılır `true`.</span><span class="sxs-lookup"><span data-stu-id="aaafc-118">In this example, the item is used only when the script is evaluated to `true`.</span></span>

```xml
<ListItem>
  <ItemSelectionCondition>
    <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  </ItemSelectionCondition>
</ListItem>

```

<span data-ttu-id="aaafc-119">Bir öğe için yalnızca bir seçim koşulu belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aaafc-119">You can specify only one selection condition for an item.</span></span> <span data-ttu-id="aaafc-120">Ve koşul, bir özellik adı veya koşulu tetiklemesine komut dosyasını belirtmeniz gerekir ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="aaafc-120">And the condition must specify one property name or script to trigger the condition, but cannot specify both.</span></span>

## <a name="xml-elements"></a><span data-ttu-id="aaafc-121">XML öğeleri</span><span class="sxs-lookup"><span data-stu-id="aaafc-121">XML Elements</span></span>

 <span data-ttu-id="aaafc-122">Aşağıdaki XML öğeleri, bir seçim koşulu oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="aaafc-122">The following XML elements are used to create a selection condition.</span></span>

- <span data-ttu-id="aaafc-123">Aşağıdaki öğeler görünümü tanımları seçimi koşullarını belirtin:</span><span class="sxs-lookup"><span data-stu-id="aaafc-123">The following elements specify selection conditions for view definitions:</span></span>

    - [<span data-ttu-id="aaafc-124">TableControl (biçimi) için EntrySelectedBy için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="aaafc-124">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

    - [<span data-ttu-id="aaafc-125">EntrySelectedBy ListControl (biçimi) için için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="aaafc-125">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

    - [<span data-ttu-id="aaafc-126">EntrySelectedBy WideControl (biçimi) için için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="aaafc-126">SelectionCondition Element for EntrySelectedBy for WideControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

    - [<span data-ttu-id="aaafc-127">Özel denetim (biçimi) için EntrySelectedBy için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="aaafc-127">SelectionCondition Element for EntrySelectedBy for CustomControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

- <span data-ttu-id="aaafc-128">Aşağıdaki öğelerin seçimini belirtin genel koşulları ve görünüm denetimi tanımları:</span><span class="sxs-lookup"><span data-stu-id="aaafc-128">The following elements specify selection conditions for common and view control definitions:</span></span>

    - [<span data-ttu-id="aaafc-129">İçin yapılandırma (biçimi) için denetimleri için EntrySelectedBy SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="aaafc-129">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

    - [<span data-ttu-id="aaafc-130">SelectionCondition öğesi görünümü (biçimi) için denetimleri için EntrySelectedBy için</span><span class="sxs-lookup"><span data-stu-id="aaafc-130">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

- <span data-ttu-id="aaafc-131">Şu öğe için koleksiyon nesnelerini genişleterek seçim koşulu belirtir:</span><span class="sxs-lookup"><span data-stu-id="aaafc-131">The following element specifies the selection condition for expanding collection objects:</span></span>

    - [<span data-ttu-id="aaafc-132">EntrySelectedBy EnumerableExpansion (biçimi) için için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="aaafc-132">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

- <span data-ttu-id="aaafc-133">Şu öğe için yeni bir veri grubu görüntüleme seçim koşulu belirtir:</span><span class="sxs-lookup"><span data-stu-id="aaafc-133">The following element specifies the selection condition for displaying a new group of data:</span></span>

    - [<span data-ttu-id="aaafc-134">GroupBy (biçimi) için EntrySelectedBy için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="aaafc-134">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

- <span data-ttu-id="aaafc-135">Aşağıdaki öğe, bir liste görünümü için bir öğe seçim koşulu belirtir:</span><span class="sxs-lookup"><span data-stu-id="aaafc-135">The following element specifies an item selection condition for a list view:</span></span>

    - [<span data-ttu-id="aaafc-136">ListItem ListControl (biçimi) için için ItemSelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="aaafc-136">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

- <span data-ttu-id="aaafc-137">Aşağıdaki öğeler, denetimler için bir öğe seçim koşulu belirtin:</span><span class="sxs-lookup"><span data-stu-id="aaafc-137">The following elements specify an item selection condition for controls:</span></span>

    - [<span data-ttu-id="aaafc-138">İçin yapılandırma (biçimi) için denetimleri için ExpressionBinding ItemSelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="aaafc-138">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

    - [<span data-ttu-id="aaafc-139">ItemSelectionCondition öğesi görünümü (biçimi) için denetimleri için ExpressionBinding için</span><span class="sxs-lookup"><span data-stu-id="aaafc-139">ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

    - [<span data-ttu-id="aaafc-140">Özel denetim (biçimi) için ExpressionBinding için ItemSelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="aaafc-140">ItemSelectionCondition Element for ExpressionBinding for CustomControl (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

## <a name="see-also"></a><span data-ttu-id="aaafc-141">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="aaafc-141">See Also</span></span>

[<span data-ttu-id="aaafc-142">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="aaafc-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
