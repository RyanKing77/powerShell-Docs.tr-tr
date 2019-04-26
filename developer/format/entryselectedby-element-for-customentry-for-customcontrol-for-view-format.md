---
title: EntrySelectedBy öğesi görünümü (biçimi) için özel denetim için CustomEntry için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7828b45b-eabf-4432-b127-131b4ef0c800
caps.latest.revision: 8
ms.openlocfilehash: e7176f9f6ef67116ea7c07a46797fb0ba84f915d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066286"
---
# <a name="entryselectedby-element-for-customentry-for-customcontrol-for-view-format"></a>Görünüm CustomControl için CustomEntry EntrySelectedBy Öğesi (Biçim)

Bu özel giriş veya kullanılmak üzere bu giriş için bulunması gereken bir koşulu kullanan .NET türlerini tanımlar.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) özel denetim öğesi (biçimi) CustomEntries öğesi görünümü (biçimi) CustomEntry öğesinin CustomEntries EntrySelectedBy görünümü (biçimi) için özel denetim için Öğe için CustomEntry görünümü (biçimi)

## <a name="syntax"></a>Sözdizimi

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `EntrySelectedBy` öğesi.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[EntrySelectedBy CustomEntry (biçimi) için için SelectionCondition öğesi](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|İsteğe bağlı öğe.<br /><br /> Bu tanım için kullanılacak bulunmalıdır koşulu tanımlar.|
|[EntrySelectedBy CustomEntry (biçimi) için için SelectionSetName öğesi](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)|İsteğe bağlı öğe.<br /><br /> Denetim görünüm bu tanımı kullanan .NET türleri kümesini belirtir.|
|[TypeName öğesi için EntrySelectedBy CustomEntry (biçimi) için](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|İsteğe bağlı öğe.<br /><br /> Denetim görünüm bu tanımı kullanan bir .NET türü belirtir.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[İçin görünümün (biçimi) CustomEntries CustomEntry öğesi](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|Belirli bir .NET nesneleri tarafından kullanılan denetimlerini tanımlar.|

## <a name="remarks"></a>Açıklamalar

En az bir türü, seçim kümesi veya bir giriş için seçim koşulu belirtmeniz gerekir. Kullanabileceğiniz bir alt öğe sayısı maksimum sınırı yoktur.

Seçimi koşullar bulunması gereken bir koşul için kullanılacak giriş, gibi bir nesne belirli bir özelliğine sahip olduğunda veya bir özel özellik değerini tanımlamak için kullanılan veya komut dosyası değerlendirilen `true`. Seçimi koşullar hakkında daha fazla bilgi için bkz. [tanımlama koşulları için bir görünüm girişi olduğunda veya öğe kullanılan](./defining-conditions-for-displaying-data.md).

Bir özel denetim görünüm bileşenleri hakkında daha fazla bilgi için bkz. [özel denetim Görünüm](./creating-custom-controls.md).

## <a name="see-also"></a>Ayrıca bkz:

[EntrySelectedBy CustomEntry (biçimi) için için SelectionCondition öğesi](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[EntrySelectedBy CustomEntry (biçimi) için için SelectionSetName öğesi](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

[TypeName öğesi için EntrySelectedBy CustomEntry (biçimi) için](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[İçin görünümün (biçimi) CustomEntries CustomEntry öğesi](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[Özel denetim görünümü](./creating-custom-controls.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
