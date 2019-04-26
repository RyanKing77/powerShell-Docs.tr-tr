---
title: Özel biçimlendirme dosyaları | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 85d27545-8097-4010-9947-6d8b3ce2eac0
caps.latest.revision: 15
ms.openlocfilehash: 71c1c181058c5646c817b90d9832976a78c6c7de
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068309"
---
# <a name="custom-formatting-files"></a>Özel Biçimlendirme Dosyaları

Cmdlet'ler, İşlevler ve betikleri tarafından döndürülen nesneler için görüntüleme biçimini, biçimlendirme dosyaları (format.ps1xml) kullanılarak tanımlanır. Bu dosyaların bazıları, Windows PowerShell cmdlet'leri tarafından döndürülen nesnelere varsayılan görüntülenme biçimini tanımlamak için Windows PowerShell tarafından sağlanır. Ancak, kendi özel biçimlendirme dosyaları varsayılan görüntü biçimleri üzerine yazmak veya kendi komutları tarafından döndürülen nesne gösterimini tanımlamak için de oluşturabilirsiniz.

Windows PowerShell, görüntülenenler ve verileri nasıl biçimlendirildiğini belirlemek için bu biçimlendirme dosyalarında verileri kullanır. Görüntülenen verileri, bir nesnenin özelliklerini veya bir betik bloğu değerini içerebilir.  Bir nesnenin özelliklerinden doğrudan kullanılabilir olmayan bir değer görüntülemek istiyorsanız, komut dosyası blokları kullanılır. Örneğin, bir nesnenin iki özellik değerini ekleyin ve verileri ayrı bir parçası toplamı görüntülemek isteyebilirsiniz. Kendi biçimlendirme dosya yazdığınızda, tanımlamanız gerekir *görünümleri* görüntülemek istediğiniz nesneleri. Tanımlayabileceğiniz her nesne için tek bir görünümde, tek bir görünümde birden çok nesne için tanımlayabileceğiniz veya aynı nesne için birden çok görünüm tanımlayabilirsiniz. Tanımlayabileceğiniz görünümleri sayısı sınırı yoktur.

> [!IMPORTANT]
> Biçimlendirme dosyaları işlem hattının getirilen nesneyi öğelerini belirlemek değil. Bir nesneyi ardışık düzene döndürüldüğünde, bu nesnenin tüm üyelerine kullanılabilir.

## <a name="format-views"></a>Biçim görünümleri

Bir tablo biçiminde, bir liste biçiminde, geniş bir biçim ve özel bir biçim, biçimlendirme görünümleri nesneleri görüntüleyebilirsiniz. Çoğunlukla, her biçimlendirme tanımı bir görünüm açıklayan XML etiketleri kümesi tarafından tanımlanır. Her görünümü, görünümün adını Görünüm ve Tablo görünümü için sütun ve satır bilgileri gibi görünümün öğeleri kullanan nesneler içerir.

Aşağıdaki görünüm mevcuttur.

Tablo görünümü, bir nesne veya bir betik bloğu değerinde bir veya daha fazla sütun özelliklerini listeler. Her sütun, nesne veya bir betik bloğu değer özelliğini temsil eder. Bir nesne veya özelliklerini ve betik bloğu değerlerini birleşimini özelliklerinin bir alt nesneyi tüm özelliklerini gösteren bir tablo görünümü tanımlayabilirsiniz. Tablodaki her satır, döndürülen nesneyi temsil eder. Bu görünüm hakkında daha fazla bilgi için bkz: [Tablo görünümü](../format/creating-a-table-view.md).

Liste görünümü, bir nesne veya bir betik bloğu değeri tek bir sütunda özelliklerini listeler. Her satır listenin isteğe bağlı bir etiket veya değeri özellik veya betik bloğunun ardından özellik adını görüntüler. Bu görünüm hakkında daha fazla bilgi için bkz: [liste görünümü](../format/creating-a-list-view.md).

Tek bir özellik bir nesnenin ya da bir veya daha fazla sütun bir betik bloğu değer geniş görünüm listeler. Bu görünüm için üst bilgi veya etiket yoktur. Bu görünüm hakkında daha fazla bilgi için bkz: [geniş Görünüm](../format/creating-a-wide-view.md).

Özel Görünüm katı yapısını tablo görünümleri, liste görünümleri veya geniş görünümleri için belirtime uymuyor özelleştirilebilir bir görünümü nesne özelliklerini veya betik bloğu değerleri görüntüler. Tablo görünümü veya liste görünümü gibi başka bir görünüm tarafından kullanılan özel bir görünüm tanımlayabilirsiniz veya tek başına özel görünüm tanımlayabilirsiniz. Bu görünüm hakkında daha fazla bilgi için bkz: [Özel Görünüm](../format/creating-custom-controls.md).

## <a name="view-xml-elements"></a>Görünüm XML öğeleri

Aşağıdaki örnek, iki sütun içeren bir tablo görünümü tanımlamak için kullanılan XML etiketlerinin gösterir. [ViewDefinitions](../format/viewdefinitions-element-format.md) öğedir biçimlendirme dosyasında tanımlanan tüm görünümleri için kapsayıcı öğe. [Görünümü](../format/view-element-format.md) öğe, belirli bir tablo, liste, geniş veya özel görünüm tanımlar. Her görünümü içinde [adı](../format/name-element-for-view-format.md) öğesi, görünümün adını belirtir [ViewSelectedBy](../format/viewselectedby-element-format.md) öğe tanımlar Görünüm ve farklı denetim öğeleri kullanan nesneler (gibi `TableControl` öğesi) görüntüleme biçimi tanımlayın.

```xml
ViewDefinitions
  <View>
    <Name>Name of View</Name>
    <ViewSelectedBy>
      <TypeName>Object to display using this view</TypeName>
      <TypeName>Object to display using this view</TypeName>
    </ViewSelectedBy>
    <TableControl>
      <TableHeaders>
        <TableColumnHeader>
          <Width></Width>
        </TableColumnHeader>
        <TableColumnHeader>
          <Width></Width>
        </TableColumnHeader>
      </TableHeaders>
      <TableRowEntries>
        <TableRowEntry>
          <TableColumnItems>
            <TableColumnItem>
              <PropertyName>Header for column 1</PropertyName>
            </TableColumnItem>
            <TableColumnItem>
              <PropertyName>Header for column 2</PropertyName>
            </TableColumnItem>
          </TableColumnItems>
        </TableRowEntry>
      </TableRowEntries>
    </TableControl)
  </View>
</ViewDefinitions>

```

## <a name="see-also"></a>Ayrıca bkz:

[Tablo görünümü](../format/creating-a-table-view.md)

[Liste Görünümü](../format/creating-a-list-view.md)

[Geniş Görünüm](../format/creating-a-wide-view.md)

[Özel Görünüm](../format/creating-custom-controls.md)

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)
