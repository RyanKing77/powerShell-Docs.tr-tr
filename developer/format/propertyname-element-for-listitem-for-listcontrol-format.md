---
title: ListItem ListControl (biçimi) için için PropertyName öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 01ae8cbe-acdc-4043-bd6e-1118a5691a55
caps.latest.revision: 12
ms.openlocfilehash: 405184f7bdbf1955f1df7766bf2723c244dcc27f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064926"
---
# <a name="propertyname-element-for-listitem-for-listcontrol-format"></a>ListControl ListItem için PropertyName Öğesi (Biçim)

.NET özelliğinin değeri, listede görüntülenen belirtir.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) ListControl öğesi (biçimi) ListEntries öğesi (biçimi) ListEntry öğesi (biçimi) ListItems öğesi (biçimi) LISTITEM öğesinin (biçimi) PropertyName öğesi ListItem (biçimi)

## <a name="syntax"></a>Sözdizimi

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Öznitelikler, alt ve üst öğesini aşağıdaki bölümlerde açıklanmaktadır `PropertyName` öğesi.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt öğeleri

Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[LISTITEM öğesinin (biçimi)](./listitem-element-for-listitems-for-listcontrol-format.md)|Özellik veya betik değeri liste görünümünün satırda görüntülenen tanımlar.|

## <a name="text-value"></a>Metin değeri

Özellik değeri görüntülenen adını belirtin.

## <a name="remarks"></a>Açıklamalar

Bu öğe belirtildiğinde, belirtemezsiniz [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) öğesi.

Özellik değeri görüntülenmesinin yanı sıra değeri veya değerin görünümünü değiştirmek için kullanılan biçim dizesi için bir etiket de belirtebilirsiniz. Liste görünümünde veri belirtme hakkında daha fazla bilgi için bkz. [bir liste görünümü oluşturma](./creating-a-list-view.md).

## <a name="example"></a>Örnek

Aşağıdaki örnek, özellik değeri görüntülenir ve etiket belirtmek gösterilmektedir.

```xml
ListItem>
  <Label>NameOfProperty</Label>
  <PropertyName>.NetTypeProperty</PropertyName>
</ListItem>

```

## <a name="see-also"></a>Ayrıca bkz:

[ListItem ListControl (biçimi) için için ScriptBlock öğesi](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[Bir liste görünümü oluşturma](./creating-a-list-view.md)

[LISTITEM öğesinin ListControl(Format) için](./listitem-element-for-listitems-for-listcontrol-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
