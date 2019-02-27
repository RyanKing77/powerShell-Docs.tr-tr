---
title: ListItem ListControl (biçimi) için için FormatString öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd2cac66-88bb-449f-9d47-bd2cd4fe1801
caps.latest.revision: 13
ms.openlocfilehash: e6024ec4f7fc490c92408047c8c15c775e45bf9d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849850"
---
# <a name="formatstring-element-for-listitem-for-listcontrol--format"></a>ListControl ListItem için FormatString Öğesi (Biçim)

Özellik veya betik değerin nasıl görüntüleneceğini tanımlayan bir biçim desenini belirtir.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) ListControl öğesi (biçimi) ListEntries öğesi ListControl (biçimi) ListEntry öğesinin ListControl (biçimi) ListItems öğesinin ListControl (biçimi) LISTITEM öğesinin ListItem ListControl (biçimi) için FormatString öğesinin ListControl (biçimi)

## <a name="syntax"></a>Sözdizimi

```xml
<FormatString>PropertyPattern</FormatString>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Öznitelikler, alt ve üst öğesini aşağıdaki bölümlerde açıklanmaktadır `FormatString` öğesi.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt Öğeler

Yok.

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[LISTITEM öğesinin (biçimi)](./listitem-element-for-listitems-for-listcontrol-format.md)|Betik değeri liste görünümünün bir satır görüntülenir ve özelliği tanımlar.|

## <a name="text-value"></a>Metin Değeri

Verilerin biçimlendirilmesi için kullanılan desen belirtin. Örneğin, türünde herhangi bir özelliği değerini biçimlendirmek için bu düzeni kullanabilirsiniz [System.Timespan](/dotnet/api/System.TimeSpan): {0: aaa} {0} {0:HH}: {0:mm}.

## <a name="remarks"></a>Açıklamalar

Tablo görünümleri, liste görünümleri, geniş görünümleri veya özel görünümlerini oluşturma biçim dizeleri kullanılabilir. Bir görünümü'nde görüntülenen bir değeri biçimlendirme hakkında daha fazla bilgi için bkz. [görüntülenen verileri biçimlendirme](./formatting-displayed-data.md).

Liste görünümlerinde biçim dizeleri kullanma hakkında daha fazla bilgi için bkz. [liste görünümü oluşturma](./creating-a-list-view.md).

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir biçimlendirme dizesi değerini tanımlamak gösterilmektedir `StartTime` özelliği.

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

## <a name="see-also"></a>Ayrıca bkz:

[Bir liste görünümü oluşturma](./creating-a-list-view.md)

[LISTITEM öğesinin (biçimi)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Biçimlendirme bir Windows PowerShell yazma ve dosya türleri](./writing-a-powershell-formatting-file.md)
