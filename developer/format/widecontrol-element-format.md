---
title: WideControl öğesi (biçimi) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 715ea055-037b-46ad-b70f-87b3f5134403
caps.latest.revision: 14
ms.openlocfilehash: 2742be0389a1bf04af100a490a59c0d938165811
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849493"
---
# <a name="widecontrol-element-format"></a>WideControl Öğesi (Biçim)

Bir geniş (çoklu değer) tanımlar görünüm için liste biçimini. Bu görünüm, tek bir özellik değeri ya da her nesne için betik değeri görüntüler.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) WideControl öğesi (biçimi)

## <a name="syntax"></a>Sözdizimi

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber>PositiveInteger</ColumnNumber>
  <WideEntries>...</WideEntries>
</WideControl>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Aşağıdaki öznitelikler, alt ve üst öğenin bölümlerde `WideControl` öğesi. Belirtemezsiniz `AutoSize` ve `ColumnNumber` aynı anda öğeleri.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[AutoSize öğesi WideControl (biçimi) için](./autosize-element-for-widecontrol-format.md)|İsteğe bağlı öğe.<br /><br /> Sütun boyutu ve sütun sayısı verilerin boyutuna bağlı olarak ayarlanır olup olmadığını belirtir.|
|[ColumnNumber öğesi WideControl (biçimi) için](./columnnumber-element-for-widecontrol-format.md)|İsteğe bağlı öğe.<br /><br /> Geniş görüntülenmesini sütun sayısını belirtir.|
|[WideEntries öğesi (biçimi)](./wideentries-element-for-widecontrol-format.md)|Gerekli öğe.<br /><br /> Geniş bir görünüm tanımını sağlar.|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Görünüm öğesi (biçimi)](./view-element-format.md)|Bir veya daha fazla .NET nesneleri görüntülemek için kullanılan bir görünüm tanımlar.|

## <a name="remarks"></a>Açıklamalar

Geniş bir görünüm tanımlarken, ekleyebileceğiniz `AutoSize` öğesi veya `ColumnNumber` ancak her ikisini de ekleyemezsiniz.

Çoğu durumda, sadece bir tanım her geniş bir görünüm için gereklidir, ancak farklı .NET nesneleri görüntülemek için aynı görünümde kullanmak istiyorsanız birden çok tanım olması mümkündür. Bu gibi durumlarda, her bir nesne veya nesne için ayrı bir tanımı sağlayabilir.

Geniş bir görünüm bileşenleri hakkında daha fazla bilgi için bkz. [geniş görünüm bileşenleri](./creating-a-wide-view.md).

## <a name="example"></a>Örnek

Aşağıdaki örnekte gösterildiği bir `WideControl` özelliği görüntülemek için kullanılan öğe [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) nesne.

```xml
<View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>
    <WideEntries>...</WideEntries>
  </WideControl>
</View>
```

Geniş bir görünüm tam bir örnek için bkz: [geniş Görünüm (Temel)](./wide-view-basic.md).

## <a name="see-also"></a>Ayrıca bkz:

[AutoSize öğesi WideControl (biçimi) için](./autosize-element-for-widecontrol-format.md)

[ColumnNumber öğesi WideControl (biçimi) için](./columnnumber-element-for-widecontrol-format.md)

[Görünüm öğesi (biçimi)](./view-element-format.md)

[WideEntries öğesi (biçimi)](./wideentries-element-for-widecontrol-format.md)

[Geniş Görünüm (Temel)](./wide-view-basic.md)

[Geniş bir görünüm oluşturma](./creating-a-wide-view.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
