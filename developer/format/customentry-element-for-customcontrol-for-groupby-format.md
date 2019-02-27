---
title: GroupBy (biçimi) için özel denetim için CustomEntry öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2987cb45-f646-45d4-b81b-7871e77af36f
caps.latest.revision: 5
ms.openlocfilehash: dcf4f8b2bbd422067ffdf9b3b4972e279e91edf9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849871"
---
# <a name="customentry-element-for-customcontrol-for-groupby-format"></a>GroupBy CustomControl için CustomEntry Öğesi (Biçim)

Denetim tanımını sağlar. Bu öğe, yeni bir grup nesnelerin nasıl görüntüleneceğini tanımlarken kullanılır.

GroupBy (biçimi) CustomEntries öğesinin GroupBy (biçimi) CustomEntry öğesinin özel denetim özel denetim öğesi görünümü (biçimi) için yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) GroupBy öğesi GroupBy (biçimi) için özel denetim

## <a name="syntax"></a>Sözdizimi

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Aşağıdaki öznitelikler, alt ve üst öğelerinin bölümlerde `CustomEntry` öğesi.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[GroupBy (biçimi) için CustomEntry için EntrySelectedBy öğesi](./entryselectedby-element-for-customentry-for-groupby-format.md)|İsteğe bağlı öğe.<br /><br /> Bu denetim tanımı veya kullanılmak üzere bu tanım için bulunması gereken bir koşulu kullanan .NET türlerini tanımlar.|
|[GroupBy (biçimi) için CustomEntry için CustomItem öğesi](./customitem-element-for-customentry-for-groupby-format.md)|Gerekli öğe.<br /><br /> Denetimin veri görüntüleme şeklini tanımlar.|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[GroupBy (biçimi) için özel denetim için CustomEntries öğesi](./customentries-element-for-customcontrol-for-groupby-format.md)|Denetim için tanımları sağlar.|

## <a name="remarks"></a>Açıklamalar

## <a name="see-also"></a>Ayrıca bkz:

[GroupBy (biçimi) için CustomEntry için EntrySelectedBy öğesi](./entryselectedby-element-for-customentry-for-groupby-format.md)

[GroupBy (biçimi) için CustomEntry için CustomItem öğesi](./customitem-element-for-customentry-for-groupby-format.md)

[GroupBy (biçimi) için özel denetim için CustomEntries öğesi](./customentries-element-for-customcontrol-for-groupby-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
