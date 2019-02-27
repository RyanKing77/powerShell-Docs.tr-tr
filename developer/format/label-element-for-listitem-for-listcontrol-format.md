---
title: Etiket öğesi için ListItem ListControl (biçimi) için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c693ff46-d1ad-4dc7-93ac-41ff2fc6c103
caps.latest.revision: 9
ms.openlocfilehash: c1293d5a1f942704ac01388c66bd9009fd340e82
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845958"
---
# <a name="label-element-for-listitem-for-listcontrol-format"></a>ListControl ListItem için Etiket Öğesi (Biçim)

Sol özellik veya betik değerin satırında görüntülenen etiketi belirtir.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) ListControl öğesi (biçimi) ListEntries öğesi ListControl (biçimi) ListItems ListEntry ListControl öğesi (için için ListEntry öğesinin ListControl (biçimi) ListItem ListControl (biçimi) için ListControl (biçimi) etiketi öğesinin ListItems için LISTITEM öğesinin biçimi)

## <a name="syntax"></a>Sözdizimi

```xml
<Label>Label for displayed value</Label>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Öznitelikler, alt ve üst öğesini aşağıdaki bölümlerde açıklanmaktadır `Label` öğesi.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt Öğeler

Yok.

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[LISTITEM öğesinin ListControl (biçimi) için ListItems için](./listitem-element-for-listitems-for-listcontrol-format.md)|Betik değeri liste görünümünün bir satır görüntülenir ve özelliği tanımlar.|

## <a name="text-value"></a>Metin Değeri

Görüntü özelliği ya da komut değeri solundaki olacak şekilde bir etiket belirtin.

## <a name="remarks"></a>Açıklamalar

Bir etiket belirtilmezse, özelliği veya komut dosyası adı görüntülenir. Liste görünümünde etiketler kullanma hakkında daha fazla bilgi için bkz. [bir liste görünümü oluşturma](./creating-a-list-view.md).

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir etiket için bir satır eklemek gösterilmektedir.

```xml
<ListItem>
  <Label>Property1: </Label>
  <PropertyName>DotNetProperty1</PropertyName>
</ListItem>

```

## <a name="see-also"></a>Ayrıca bkz:

[Bir liste görünümü oluşturma](./creating-a-list-view.md)

[LISTITEM öğesinin (biçimi)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
