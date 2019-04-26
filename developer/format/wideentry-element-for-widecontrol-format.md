---
title: WideEntry öğesi WideControl (biçimi) için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 014763cb-7716-4931-899c-8375b5d7a3dd
caps.latest.revision: 15
ms.openlocfilehash: d1d13b5c3436871053353814293d9163ea13c7fb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083680"
---
# <a name="wideentry-element-for-widecontrol-format"></a>WideControl için WideEntry Öğesi (Biçim)

Geniş bir görünüm tanımını sağlar.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) WideControl öğesi (biçimi) WideEntries öğesi (biçimi) WideEntry öğesi (biçimi)

## <a name="syntax"></a>Sözdizimi

```xml
<WideEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <WideItem>...</WideItem>
</WideEntry>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Öznitelikler, alt ve üst öğesini aşağıdaki bölümlerde açıklanmaktadır `WideEntry` öğesi. Tek bir belirtmelisiniz `WideItem` alt öğesi.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[EntrySelectedBy öğesi WideEntry (biçimi) için](./entryselectedby-element-for-wideentry-format.md)|İsteğe bağlı öğe.<br /><br /> Bu geniş bir girdi tanımı veya kullanılmak üzere bu tanım için bulunması gereken bir koşulu kullanan .NET türlerini tanımlar.|
|[WideItem öğesi (biçimi)](./wideitem-element-for-widecontrol-format.md)|Gerekli öğe.<br /><br /> Betik değeri görüntülenir ve özelliği tanımlar.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[WideEntries öğesi (biçimi)](./wideentries-element-for-widecontrol-format.md)|Geniş bir görünüm tanımını sağlar.|

## <a name="remarks"></a>Açıklamalar

Geniş bir görünüm tek özellik değeri ya da her nesne için betik değer görüntüleyen bir liste biçimidir. Diğer görünüm türleri farklı olarak, her görünüm tanımı için yalnızca bir öğe öğeyi belirtebilirsiniz. Geniş bir görünüm diğer bileşenler hakkında daha fazla bilgi için bkz. [geniş bir görünüm oluşturma](./creating-a-wide-view.md).

## <a name="example"></a>Örnek

Aşağıdaki örnekte gösterildiği bir `WideEntry` tanımlayan tek bir öğe `WideItem` öğesi. `WideItem` Öğe değeri görünümünde görüntülenen özelliği tanımlar.

```xml
<WideEntries>
  <WideEntry>
    <WideItem>
      <PropertyName>ProcessName</PropertyName>
    </WideItem>
  </WideEntry>
</WideEntries>

```

Geniş bir görünüm tam bir örnek için bkz: [geniş Görünüm (Temel)](./wide-view-basic.md).

## <a name="see-also"></a>Ayrıca bkz:

[Geniş bir görünüm oluşturma](./creating-a-wide-view.md)

[SelectionCondition öğesi WideEntry (biçimi) için](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[SelectionSetName öğesi WideEntry (biçimi) için](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[TypeName öğesi WideEntry (biçimi) için](./typename-element-for-entryselectedby-for-wideentry-format.md)

[WideEntries öğesi (biçimi)](./wideentries-element-for-widecontrol-format.md)

[WideItem öğesi (biçimi)](./wideitem-element-for-widecontrol-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
