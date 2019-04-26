---
title: SelectionSetName öğesi EntrySelectedBy ListEntry (biçimi) için için SelectionCondition için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eae67e47-6c60-4741-8430-78d2cb6067b1
caps.latest.revision: 10
ms.openlocfilehash: ccfc0b772ad3b2d1979c7c832a5153de870035d7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075520"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format"></a>ListEntry EntrySelectedBy için SelectionCondition SelectionSetName Öğesi (Biçim)

Tetikleme koşulu .NET türleri kümesini belirtir. Bu türlerinden herhangi birini mevcut olduğunda, koşul karşılanır ve nesne bu liste görünümü tanımını kullanarak görüntülenir.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünümü öğesi (biçimi) ListControl öğesi (biçimi) ListEntries öğesi (biçimi) ListEntry öğesi (biçimi) EntrySelectedBy öğesi SelectionCondition öğesinin ListEntry (biçimi) EntrySelectedBy EntrySelectedBy ListEntry (biçimi) için için SelectionCondition SelectionSetName öğesinin ListEntry (biçimi)

## <a name="syntax"></a>Sözdizimi

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `SelectionSetName` öğesi.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt öğeleri

Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[EntrySelectedBy ListEntry (biçimi) için için SelectionCondition öğesi](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|Bu liste görünümü tanımını kullanılacak bulunmalıdır koşulu tanımlar.|

## <a name="text-value"></a>Metin değeri

Seçimi kümesinin adını belirtin.

## <a name="remarks"></a>Açıklamalar

Seçim koşulu, bir seçim kümesi veya .NET türü belirtebilirsiniz, ancak ikisini birden belirtemezsiniz. Seçimi koşulları kullanma hakkında daha fazla bilgi için bkz. [veri görüntülendiğinde için koşulları tanımlama](./defining-conditions-for-displaying-data.md).

Seçimi ayarlar biçimlendirme dosyayı tanımlayan herhangi bir görünüm tarafından kullanılan .NET nesneleri ortak gruplarıdır. Oluşturma ve başvuran seçimi ayarlar hakkında daha fazla bilgi için bkz. [tanımlama ayarlar nesnelerin](./defining-selection-sets.md).

Bir liste görünümü diğer bileşenler hakkında daha fazla bilgi için bkz. [bir liste görünümü oluşturma](./creating-a-list-view.md).

## <a name="see-also"></a>Ayrıca bkz:

[Bir liste görünümü oluşturma](./creating-a-list-view.md)

[Veri görüntülendiğinde koşulları tanımlama](./defining-conditions-for-displaying-data.md)

[EntrySelectedBy ListEntry (biçimi) için için SelectionCondition öğesi](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
