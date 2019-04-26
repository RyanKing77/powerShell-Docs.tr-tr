---
title: GroupBy (biçimi) için EntrySelectedBy için SelectionSetName öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d569c623-2277-49e3-933e-c26262b91cd5
caps.latest.revision: 6
ms.openlocfilehash: 69cd113c444b4e3c5dceabcdfddb439cd1376f6b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064076"
---
# <a name="selectionsetname-element-for-entryselectedby-for-groupby-format"></a>GroupBy EntrySelectedBy için SelectionSetName Öğesi (Biçim)

.NET nesnelerinin listesi girişi için bir dizi belirtir. Bir giriş için belirtilen seçim kümeleri sayısı sınırı yoktur. Bu öğe, yeni bir grup nesnelerin nasıl görüntüleneceğini tanımlarken kullanılır.

GroupBy (biçimi) CustomEntries öğesinin GroupBy (biçimi) CustomEntry öğesinin özel denetim özel denetim öğesi görünümü (biçimi) için yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) GroupBy öğesi GroupBy (biçimi) EntrySelectedBy öğesinin CustomEntry GroupBy (biçimi) SelectionSetName öğesinin EntrySelectedBy GroupBy (biçimi) için özel denetim

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
|[GroupBy (biçimi) için CustomEntry için EntrySelectedBy öğesi](./entryselectedby-element-for-customentry-for-groupby-format.md)|Bu özel giriş veya kullanılmak üzere bu giriş için bulunması gereken bir koşulu kullanan .NET türlerini tanımlar.|

## <a name="text-value"></a>Metin değeri

Seçimi kümesinin adını belirtin.

## <a name="remarks"></a>Açıklamalar

Her özel denetim tanımı en az bir tür adı, seçim kümesi veya seçim koşulu tanımlanmış olması gerekir.

Seçimi ayarlar, genellikle kullanılan nesnelerin bir grup içinde birden çok görünüm tanımlamak istediğinizde kullanılır. Örneğin, bir tablo görünümü ve aynı nesne kümesini bir liste görünümü oluşturmak isteyebilirsiniz. Seçimi ayarlar tanımlama hakkında daha fazla bilgi için bkz. [tanımlama seçimi](./defining-selection-sets.md).

Bir özel denetim görünüm bileşenleri hakkında daha fazla bilgi için bkz. [özel denetimler oluşturma](./creating-custom-controls.md).

## <a name="see-also"></a>Ayrıca bkz:

[GroupBy (biçimi) için CustomEntry için EntrySelectedBy öğesi](./entryselectedby-element-for-customentry-for-groupby-format.md)

[Özel denetimler oluşturma](./creating-custom-controls.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
