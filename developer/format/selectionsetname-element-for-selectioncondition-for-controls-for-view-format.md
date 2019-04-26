---
title: SelectionSetName öğesi görünümü (biçimi) için denetimleri için SelectionCondition için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: daea8c6f-873a-4639-9eee-599642822958
caps.latest.revision: 6
ms.openlocfilehash: 697f2ea284393ebddd77a862c408f27f3d332900
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063896"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-view-format"></a>Görünüm Denetimleri için SelectionCondition SelectionSetName Öğesi (Biçim)

Tetikleme koşulu .NET türleri kümesini belirtir. Bu türlerinden herhangi birini mevcut olduğunda, koşul karşılanır ve nesne bu denetimi kullanarak görüntülenir. Bu öğe bir görünüm tarafından kullanılan denetimler tanımlarken kullanılır.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) denetimleri (biçimi) öğesi denetim öğesi denetimi için CustomEntries öğesi görünümü (biçimi) için denetimleri için özel denetim öğesi görünümü (biçimi) için denetimleri için Görünümü (biçimi) CustomEntry öğesinin CustomEntries CustomEntry EntrySelectedBy denetimleri için View (Görünüm (biçimi) SelectionCondition öğesinin denetimleri için görüntüleme (biçimi) EntrySelectedBy öğesinin denetimleri için denetimler için özel denetim Biçimi) SelectionSetName öğesi görünümü (biçimi) için denetimleri için SelectionCondition için

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
|[SelectionCondition öğesi görünümü (biçimi) için denetimleri için EntrySelectedBy için](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|Kullanılacak denetimi tanımı bulunması gereken bir koşulu tanımlar.|

## <a name="text-value"></a>Metin değeri

Seçimi kümesinin adını belirtin.

## <a name="remarks"></a>Açıklamalar

Seçimi ayarlar biçimlendirme dosyayı tanımlayan herhangi bir görünüm tarafından kullanılan .NET nesneleri ortak gruplarıdır. Oluşturma ve başvuran seçimi ayarlar hakkında daha fazla bilgi için bkz. [tanımlama seçimi](./defining-selection-sets.md).

Seçim koşulu, bir seçim kümesi veya .NET türü belirtebilirsiniz, ancak ikisini birden belirtemezsiniz. Seçimi koşulları kullanma hakkında daha fazla bilgi için bkz. [görüntüleyen veri koşulları tanımlama](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Ayrıca bkz:

[SelectionCondition öğesi görünümü (biçimi) için denetimleri için EntrySelectedBy için](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[Veri görüntülendiğinde koşulları tanımlama](./defining-conditions-for-displaying-data.md)

[Seçimi ayarlar tanımlama](./defining-selection-sets.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
