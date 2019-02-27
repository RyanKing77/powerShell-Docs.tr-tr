---
title: LISTITEM öğesinin ListControl (biçimi) için ListItems için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f96f4f5-8bd5-43ed-95e7-a7358115999a
caps.latest.revision: 11
ms.openlocfilehash: 1e0a1b2d20853650328b8cfd1513a08f7e167cd6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846224"
---
# <a name="listitem-element-for-listitems-for-listcontrol-format"></a>ListControl ListItems için ListItem Öğesi (Biçim)

Betik değeri liste görünümünün bir satır görüntülenir ve özelliği tanımlar.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) ListControl öğesi (biçimi) ListEntries öğesi ListControl (biçimi) ListEntry öğesinin ListControl (biçimi) ListItems öğesinin ListControl (biçimi) ListItem ListControl öğesinin (biçimi)

## <a name="syntax"></a>Sözdizimi

```xml
<ListItem>
  <PropertyName>PropertyToDisplay</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <Label>LabelToDisplay</Label>
  <FormatString>FormatPattern</FormatString>
  <ItemSelectionCondition>...</ItemSelectionCondition>
</ListItem>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Aşağıdaki öznitelikler, alt ve üst öğenin bölümlerde `ListItem` öğesi. Yalnızca bir özellik veya komut dosyası belirtilebilir.

### <a name="attributes"></a>Öznitelikler

Yok

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[ListItem ListControl (biçimi) için için FormatString öğesi](./formatstring-element-for-listitem-for-listcontrol-format.md)|İsteğe bağlı öğe.<br /><br /> Özellik veya betik değerin nasıl görüntüleneceğini tanımlayan bir biçim dizesi belirtir.|
|[ListItem ListControl (biçimi) için için ItemSelectionCondition öğesi](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|İsteğe bağlı öğe.<br /><br /> Bu liste öğesi için kullanılacak bulunmalıdır koşulu tanımlar.|
|[ListItem ListControl (biçimi) için için etiket öğesi](./label-element-for-listitem-for-listcontrol-format.md)|İsteğe bağlı öğe<br /><br /> Sol özellik veya betik değerin satırında görüntülenen etiketi belirtir.|
|[ListItem ListControl (biçimi) için için PropertyName öğesi](./propertyname-element-for-listitem-for-listcontrol-format.md)|İsteğe bağlı öğe.<br /><br /> .NET özelliğinin değeri satırda görüntülenen belirtir.|
|[ListItem ListControl (biçimi) için için ScriptBlock öğesi](./scriptblock-element-for-listitem-for-listcontrol-format.md)|İsteğe bağlı öğe.<br /><br /> Betikte satır değeri görüntülenir.|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Liste denetimi (biçimi) için ListItems öğesi](./listitems-element-for-listentry-for-listcontrol-format.md)|Betikleri değerleri liste görünümünde görüntülenir ve özellikleri tanımlar.|

## <a name="remarks"></a>Açıklamalar

Bir liste görünümü bileşenler hakkında daha fazla bilgi için bkz. [bir liste görünümü oluşturma](./creating-a-list-view.md).

## <a name="example"></a>Örnek

Bu örnek, liste görünümü üç satırı tanımlayan XML öğeleri gösterir. Bir .NET özelliğinin değeri ilk iki satırını görüntülemek ve son satırını bir betik tarafından oluşturulan bir değer görüntüler.

```xml
<ListEntry>
    <ListItems>
      <ListItem>
        <Label>Property1: </Label>
        <PropertyName>DotNetProperty1</PropertyName>
      </ListItem>
      <ListItem>
        <PropertyName>DotNetProperty2</PropertyName>
      </ListItem>
      <ListItem>
        <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
      </ListItem>
    </ListItems>
</ListEntry>

```

## <a name="see-also"></a>Ayrıca bkz:

[ListItems öğesi (biçimi)](./listitems-element-for-listentry-for-listcontrol-format.md)

[ListItem (biçimi) için FormatString öğesi](./formatstring-element-for-listitem-for-listcontrol-format.md)

[ListItem (biçimi) için etiket öğesi](./label-element-for-listitem-for-listcontrol-format.md)

[ListItem (biçimi) için PropertyName öğesi](./propertyname-element-for-listitem-for-listcontrol-format.md)

[ListItem (biçimi) için ScriptBlock öğesi](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[Bir liste görünümü oluşturma](./creating-a-list-view.md)

[Biçimlendirme bir Windows PowerShell yazma ve dosya türleri](./writing-a-powershell-formatting-file.md)
