---
title: SelectionSetName öğesi ViewSelectedBy (biçimi) için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ab0f033-df09-4435-a8bd-76ec2d01f13b
caps.latest.revision: 13
ms.openlocfilehash: d1de2b30860bac80bf17508f40eec33c2794c4b2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848450"
---
# <a name="selectionsetname-element-for-viewselectedby-format"></a>ViewSelectedBy için SelectionSetName Öğesi (Biçim)

Görünüm tarafından görüntülenen .NET nesneleri kümesini belirtir.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) ViewSelectedBy öğesi (biçimi) SelectionSetName öğesi ViewSelectedBy (biçimi) için

## <a name="syntax"></a>Sözdizimi

```xml
<SelectionSetName>Name of selection set<SelectionSetName>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Öznitelikler, alt ve üst öğesini aşağıdaki bölümlerde açıklanmaktadır `SelectionSetName` öğesi.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt Öğeler

Yok.

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[ViewSelectedBy öğesi (biçimi)](./viewselectedby-element-format.md)|Görünüm tarafından görüntülenen .NET nesneleri tanımlar.|

## <a name="text-value"></a>Metin Değeri

Tarafından tanımlanan seçim kümesinin adını belirtmek `Name` seçimi kümesi için öğesi.

## <a name="remarks"></a>Açıklamalar

Devralma yoluyla ilişkili bir nesne gibi tek bir adı kullanarak başvurmak istediğiniz bir ilgili nesne varsa, seçim kümeleri kullanabilirsiniz. Tanımlama ve başvurma seçimi ayarlar hakkında daha fazla bilgi için bkz. [tanımlama ayarlar nesnelerin](./defining-selection-sets.md).

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir liste görünümü için seçim belirtmek gösterilmektedir. Aynı şemayı, tablo, geniş ve özel görünümleri için kullanılır.

```xml
<View>
  <Name>Name of View</Name>
  <ViewSelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a>Ayrıca bkz:

[Seçimi ayarlar tanımlama](./defining-selection-sets.md)

[ViewSelectedBy öğesi (biçimi)](./viewselectedby-element-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
