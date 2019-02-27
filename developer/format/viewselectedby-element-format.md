---
title: ViewSelectedBy öğesi (biçimi) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: acdeef4d-3554-4f39-a7e6-a684e3848fd7
caps.latest.revision: 19
ms.openlocfilehash: efc1c5d1338889ecd0be7150b7733842ce78979e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851845"
---
# <a name="viewselectedby-element-format"></a>ViewSelectedBy Öğesi (Biçim)

Görünüm tarafından görüntülenen .NET nesneleri tanımlar. Her görünüm en az bir .NET nesnesi belirtmeniz gerekir.

ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) ViewSelectedBy öğesi (biçimi)

## <a name="syntax"></a>Sözdizimi

```xml
<ViewSelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
</ViewSelectedBy>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Aşağıdaki öznitelikler, alt ve üst öğenin bölümlerde `ViewSelectedBy` öğesi. Bu öğe en az birini içermelidir `TypeName` veya `SelectionSetName` alt öğesi. Belirtilebilecek alt öğe sayısına bir sınır yoktur ve bunların sırası önemlidir.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[TypeName öğesi ViewSelectedBy (biçimi) için](./typename-element-for-viewselectedby-format.md)|İsteğe bağlı öğe.<br /><br /> Görünüm tarafından görüntülenen bir .NET nesnesini belirtir.|
|[SelectionSetName öğesi ViewSelectedBy (biçimi) için](./selectionsetname-element-for-viewselectedby-format.md)|İsteğe bağlı öğe.<br /><br /> Görünüm tarafından görüntülenen .NET nesneleri kümesini belirtir.|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Görünüm öğesi (biçimi)](./view-element-format.md)|Bir veya daha fazla .NET nesnelerini görüntüleyen bir görünüm tanımlar.|

## <a name="remarks"></a>Açıklamalar

Bu öğe farklı görünümleri nasıl kullanıldığı hakkında daha fazla bilgi için bkz. [Tablo görünümü bileşenleri](./creating-a-table-view.md), [liste görünüm bileşenleri](./creating-a-list-view.md), [geniş görünüm bileşenleri](./creating-a-wide-view.md)ve [Özel denetim bileşenleri](./creating-custom-controls.md).

`SelectionSetName` Öğesi, biçimlendirme dosyası birden çok görünüm tarafından görüntülenen bir nesne tanımlayan olduğunda kullanılır. Seçimi kümeleri nasıl tanımlandığı ve başvurulan hakkında daha fazla bilgi için bkz. [tanımlama ayarlar nesnelerin](./defining-selection-sets.md).

## <a name="example"></a>Örnek

Aşağıdaki örnek nasıl belirtileceğini gösterir [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) nesne için bir liste görünümü. Aynı şemayı, tablo, geniş ve özel görünümleri için kullanılır.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a>Ayrıca bkz:

[Bir liste görünümü oluşturma](./creating-a-list-view.md)

[Bir tablo görünümü oluşturma](./creating-a-table-view.md)

[Geniş bir görünüm oluşturma](./creating-a-wide-view.md)

[Özel denetimler oluşturma](./creating-custom-controls.md)

[Seçimi ayarlar tanımlama](./defining-selection-sets.md)

[SelectionSetName öğesi ViewSelectedBy (biçimi) için](./selectionsetname-element-for-viewselectedby-format.md)

[TypeName öğesi (biçimi)](./typename-element-for-viewselectedby-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
