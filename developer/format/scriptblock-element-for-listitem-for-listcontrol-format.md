---
title: ListItem ListControl (biçimi) için için ScriptBlock öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 74e30938-00ef-46fd-84e5-f0a83706a50e
caps.latest.revision: 11
ms.openlocfilehash: 76b600256af3f957f7fe0578f9fef810262aa5d5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846504"
---
# <a name="scriptblock-element-for-listitem-for-listcontrol-format"></a>ListControl ListItem için ScriptBlock Öğesi (Biçim)

Betikte satır değeri görüntülenir.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) ListControl öğesi (biçimi) ListEntries öğesi ListEntry ListControl (biçimi) ListItems öğesinin ListEntries ListEntry öğesinin ListControl (biçimi) ListItem ListControl (biçimi) için ListControl (biçimi) ScriptBlock öğesinin ListItems için ListControl (biçimi) LISTITEM öğesinin

## <a name="syntax"></a>Sözdizimi

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Öznitelikler, alt ve üst öğesini aşağıdaki bölümlerde açıklanmaktadır `ScriptBlock` öğesi.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt Öğeler

Yok.

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[LISTITEM öğesinin (biçimi)](./listitem-element-for-listitems-for-listcontrol-format.md)|Betik değeri liste görünümünün bir satır görüntülenir ve özelliği tanımlar.|

## <a name="text-value"></a>Metin Değeri

Değeri satır içinde görüntülenen komut dosyasını belirtin.

## <a name="remarks"></a>Açıklamalar

Bu öğe belirtildiğinde, belirtemezsiniz [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) öğesi.

Liste görünümünde betikleri belirtme hakkında daha fazla bilgi için bkz. [liste görünümü](./creating-a-list-view.md).

## <a name="example"></a>Örnek

Aşağıdaki örnek, değeri görüntülenen özelliği belirtmek gösterilmektedir.

```xml
<ListItem>
  <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
</ListItem>

```

## <a name="see-also"></a>Ayrıca bkz:

[ListItem ListControl (biçimi) için için PropertyName öğesi](./propertyname-element-for-listitem-for-listcontrol-format.md)

[Bir liste görünümü oluşturma](./creating-a-list-view.md)

[LISTITEM öğesinin ListControl (biçimi) için ListItems için](./listitem-element-for-listitems-for-listcontrol-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
