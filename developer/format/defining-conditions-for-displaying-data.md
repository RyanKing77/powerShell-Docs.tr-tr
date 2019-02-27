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
# <a name="defining-conditions-for-displaying-data"></a>Veri Görüntülemek İçin Koşulları Tanımlama

Hangi verilerin bir görünüm veya denetimi tarafından görüntülenen tanımlarken, görüntülenecek verileri için bulunması gereken bir koşul belirtebilirsiniz. Belirli bir özelliğe göre veya bir komut dosyasına koşul tetiklenebilir veya özellik değeri değerlendirilen `true`. Seçim koşulu karşılandığında, görünüm veya denetim tanımı kullanılır.

## <a name="specifying-a-selection-condition-for-a-definition"></a>Tanımı için bir seçim koşulu belirtme

Bir görünüm veya denetim için bir tanım oluşturulurken `EntrySelectedBy` öğesi, hangi nesnelerin tanımı kullanır veya tanımı kullanılmak üzere hangi koşul bulunmalıdır belirtmek için kullanılır. Koşul tarafından belirtilen `SelectionCondition` öğesi.

Aşağıdaki örnekte, bir seçim koşulu bir tablo görünümü için bir tanım belirtildi. Bu örnekte, yalnızca belirtilen komut için değerlendirilirken tanımı kullanılır `true`.

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

Tanımı bir görünüm veya denetim için belirttiğiniz seçimi koşullar sayısı sınırı yoktur. Yalnızca gereksinimler aşağıda verilmiştir:

- Seçim koşulu, bir özellik adı veya koşulu tetiklemesine komut dosyasını belirtmeniz gerekir, ancak ikisini birden belirtemezsiniz.

- Seçim koşulu .NET türleri herhangi bir sayıda belirtebilirsiniz veya seçimi ayarlar, ancak ikisini birden belirtemezsiniz.

## <a name="specifying-a-selection-condition-for-an-item"></a>Bir öğe için bir seçim koşulu belirtme

Bir öğenin bir liste görünümü veya denetimi ekleyerek kullanıldığında belirtebilirsiniz `ItemSelectionCondition` öğesi tanımı öğesi. Aşağıdaki örnekte, bir liste görünümü öğesi için bir seçim koşulu belirtildi. Bu örnekte, komut dosyası için değerlendirilirken öğesi kullanılır `true`.

```xml
<ListItem>
  <ItemSelectionCondition>
    <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  </ItemSelectionCondition>
</ListItem>

```

Bir öğe için yalnızca bir seçim koşulu belirtebilirsiniz. Ve koşul, bir özellik adı veya koşulu tetiklemesine komut dosyasını belirtmeniz gerekir ancak ikisini birden belirtemezsiniz.

## <a name="xml-elements"></a>XML öğeleri

 Aşağıdaki XML öğeleri, bir seçim koşulu oluşturmak için kullanılır.

- Aşağıdaki öğeler görünümü tanımları seçimi koşullarını belirtin:

    - [TableControl (biçimi) için EntrySelectedBy için SelectionCondition öğesi](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

    - [EntrySelectedBy ListControl (biçimi) için için SelectionCondition öğesi](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

    - [EntrySelectedBy WideControl (biçimi) için için SelectionCondition öğesi](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

    - [Özel denetim (biçimi) için EntrySelectedBy için SelectionCondition öğesi](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

- Aşağıdaki öğelerin seçimini belirtin genel koşulları ve görünüm denetimi tanımları:

    - [İçin yapılandırma (biçimi) için denetimleri için EntrySelectedBy SelectionCondition öğesi](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

    - [SelectionCondition öğesi görünümü (biçimi) için denetimleri için EntrySelectedBy için](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

- Şu öğe için koleksiyon nesnelerini genişleterek seçim koşulu belirtir:

    - [EntrySelectedBy EnumerableExpansion (biçimi) için için SelectionCondition öğesi](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

- Şu öğe için yeni bir veri grubu görüntüleme seçim koşulu belirtir:

    - [GroupBy (biçimi) için EntrySelectedBy için SelectionCondition öğesi](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

- Aşağıdaki öğe, bir liste görünümü için bir öğe seçim koşulu belirtir:

    - [ListItem ListControl (biçimi) için için ItemSelectionCondition öğesi](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

- Aşağıdaki öğeler, denetimler için bir öğe seçim koşulu belirtin:

    - [İçin yapılandırma (biçimi) için denetimleri için ExpressionBinding ItemSelectionCondition öğesi](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

    - [ItemSelectionCondition öğesi görünümü (biçimi) için denetimleri için ExpressionBinding için](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

    - [Özel denetim (biçimi) için ExpressionBinding için ItemSelectionCondition öğesi](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

## <a name="see-also"></a>Ayrıca bkz:

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
