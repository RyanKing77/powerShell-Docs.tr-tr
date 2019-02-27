---
title: ListItem ListControl (biçimi) için için ItemSelectionCondition öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2668aea-37e9-4753-a4e9-7980ae5ec2eb
caps.latest.revision: 10
ms.openlocfilehash: 6bc0ccbcc5bd62429f63ed220da66dc66f44f7ca
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850921"
---
# <a name="itemselectioncondition-element-for-listitem-for-listcontrol-format"></a>ListControl ListItem için ItemSelectionCondition Öğesi (Biçim)

Bu liste öğesi için kullanılacak bulunmalıdır koşulu tanımlar.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) ListControl öğesi (biçimi) ListEntries öğesi ListEntry ListControl (biçimi) ListItems öğesinin ListEntries ListEntry öğesinin ListControl (biçimi) ListItem ListControl (biçimi) için ListControl (biçimi) ItemSelectionCondition öğesinin ListItems için ListControl (biçimi) LISTITEM öğesinin

## <a name="syntax"></a>Sözdizimi

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `ItemSelectionCondition` öğesi.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[PropertyName öğesi için ItemSelectionCondition ListControl (biçimi) için](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)|İsteğe bağlı öğe.<br /><br /> Koşul tetikleyen .NET alan özelliği belirtir.|
|[ItemSelectionCondition ListControl (biçimi) için için ScriptBlock öğesi](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)|İsteğe bağlı öğe.<br /><br /> Koşul tetikleyen betiği belirtir.|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[LISTITEM öğesinin ListControl (biçimi) için ListItems için](./listitem-element-for-listitems-for-listcontrol-format.md)|Betik değeri liste görünümünün bir satır görüntülenir ve özelliği tanımlar.|

## <a name="remarks"></a>Açıklamalar

Bir özellik adı veya bu koşul için bir betik belirtebilirsiniz, ancak ikisini birden belirtemezsiniz.

## <a name="see-also"></a>Ayrıca bkz:

[LISTITEM öğesinin ListControl (biçimi) için ListItems için](./listitem-element-for-listitems-for-listcontrol-format.md)

[PropertyName öğesi için ItemSelectionCondition ListControl (biçimi) için](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)

[ItemSelectionCondition ListControl (biçimi) için için ScriptBlock öğesi](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
