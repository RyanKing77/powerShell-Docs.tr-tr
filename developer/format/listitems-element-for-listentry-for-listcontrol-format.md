---
title: ListItems öğesi ListEntry ListControl (biçimi) için için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2c1da6d-acc7-4fe8-9e7d-6dcddc2787cd
caps.latest.revision: 9
ms.openlocfilehash: c25f18489d9c7abd8889758499dbbacd6ee29304
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065249"
---
# <a name="listitems-element-for-listentry-for-listcontrol-format"></a>ListControl ListEntry için ListItems Öğesi (Biçim)

Betikleri değerleri satır liste görünümü görüntülenir ve özellikleri tanımlar.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) ListControl öğesi (biçimi) ListEntries öğesi liste denetimi (biçimi) ListEntry öğesinin ListControl (biçimi) ListItems öğesinin ListControl (biçimi)

## <a name="syntax"></a>Sözdizimi

```xml
<ListItems>
  <ListItem>...</ListItem>
</ListItems>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Aşağıdaki öznitelikler, alt ve üst öğenin bölümlerde `ListItems` öğesi. İçin belirtilebilir alt öğe sayısı sınırı yoktur. Alt öğelerin sırasını değerleri listesi görünümü'nde görüntülenme sırasını tanımlar.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[LISTITEM öğesinin ListControl (biçimi) için](./listitem-element-for-listitems-for-listcontrol-format.md)|Gerekli öğe.<br /><br /> Betik değeri tarafından liste görünümü görüntülenir ve özelliği tanımlar.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[ListEntry öğesi ListControl (biçimi) için](./listentry-element-for-listcontrol-format.md)|Liste Görünümü tanımını sağlar.|

## <a name="remarks"></a>Açıklamalar

Bu görünüm türü hakkında daha fazla bilgi için bkz: [bir liste görünümü oluşturma](./creating-a-list-view.md).

## <a name="example"></a>Örnek

Bu örnek, liste görünümü üç satırı tanımlayan XML öğeleri gösterir.

```xml
<ListEntry>
    <ListItems>
      <ListItem>
        <Label>Property1: </Label>
        <PropertyName>.NetTypeProperty1</PropertyName>
      </ListItem>
      <ListItem>
        <PropertyName>.NetTypeProperty2</PropertyName>
      </ListItem>
      <ListItem>
        <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
      </ListItem>
  </ListEntry>
```

## <a name="see-also"></a>Ayrıca bkz:

[ListEntry öğesi ListControl (biçimi) için](./listentry-element-for-listcontrol-format.md)

[LISTITEM öğesinin ListControl (biçimi) için](./listitem-element-for-listitems-for-listcontrol-format.md)

[Bir liste görünümü oluşturma](./creating-a-list-view.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
