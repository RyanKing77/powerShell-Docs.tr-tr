---
title: Dosya genel bakış biçimlendirme | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe888fee-1fe9-459f-9d62-35732c19a7f8
caps.latest.revision: 13
ms.openlocfilehash: d418cff70c1197aa3c331eed909f49198da139e9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851922"
---
# <a name="formatting-file-overview"></a>Biçimlendirme Dosyasına Genel Bakış

(Cmdlet'ler, İşlevler ve betikler) komutları tarafından döndürülen nesneler için görüntüleme biçimi biçimlendirme dosyaları (format.ps1xml dosyaları) kullanılarak tanımlanır. Bu dosyaların birkaç gibi sağlanan PowerShell komutları tarafından döndürülen nesnelere görüntülenme biçimini tanımlamak için PowerShell tarafından sağlanan [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) tarafından döndürülen nesne `Get-Process` cmdlet'i. Ancak, kendi özel biçimlendirme dosyaları varsayılan görüntü biçimleri üzerine de oluşturabilirsiniz veya kendi komutları tarafından döndürülen nesne gösterimini tanımlamak için özel bir biçimlendirme dosyası yazabilirsiniz.

> [!IMPORTANT]
> Biçimlendirme dosyaları işlem hattının getirilen nesneyi öğelerini belirlemek değil. Bir nesneyi ardışık düzene döndürüldüğünde, bu nesnenin tüm üyelerine bazı görüntülenmez olsa bile kullanılabilir.

PowerShell, görüntülenenler ve görüntülenen verileri nasıl biçimlendirildiğini belirlemek için bu biçimlendirme dosyalarında verileri kullanır. Görüntülenen verileri, bir nesnenin özelliklerini veya bir komut dosyası değerini içerebilir. İki özellik bir nesnenin değerini ekleme ve sonra veri bir parçası toplam görüntüleme gibi bir nesnenin özelliklerinden doğrudan kullanılabilir olmayan bir değer görüntülemek istiyorsanız, betikleri kullanılır. Görüntülenen verilerin biçimlendirmesini görünümleri görüntülemek istediğiniz nesnelerin tanımlayarak gerçekleştirilir. Tanımlayabileceğiniz her nesne için tek bir görünümde, tek bir görünümde birden çok nesne için tanımlayabileceğiniz veya aynı nesne için birden çok görünüm tanımlayabilirsiniz. Tanımlayabileceğiniz görünümleri sayısı sınırı yoktur.

## <a name="common-features-of-formatting-files"></a>Biçimlendirme dosyalarının genel özellikleri

Biçimlendirme her dosya, dosya tarafından tanımlanan tüm görünümleri arasında paylaşılabilir bulunan aşağıdaki bileşenleri tanımlayabilirsiniz:

- Varsayılan yapılandırma ayarı, veri sütunun genişliği uzunsa gibi olup olmadığını ve sonraki satırda tabloları satırlarda gösterilen veriler görüntülenir. Bu ayarlar hakkında daha fazla bilgi için bkz. [ortak yapılandırma ayarlarını tanımlayan](./defining-common-configuration-features.md).

- Görünümlerden herhangi birinde biçimlendirme dosyanın tarafından görüntülenebilen nesneler ayarlar. Bu ayarlar hakkında daha fazla bilgi için (denir *seçimi ayarlar*), bkz: [tanımlama ayarlar nesnelerin](./defining-selection-sets.md).

- Biçimlendirme dosyanın tüm görünümler tarafından kullanılan ortak denetimler. Denetimler, verilerin nasıl görüntüleneceğini üzerinde daha hassas bir denetim sağlar. Denetimleri hakkında daha fazla bilgi için bkz. [tanımlama özel denetimler](./creating-custom-controls.md).

## <a name="formatting-views"></a>Biçimlendirme görünümleri

Bir tablo biçiminde, liste biçimini, geniş bir biçim ve özel biçim, biçimlendirme görünümleri nesneleri görüntüleyebilirsiniz. Çoğunlukla, her biçimlendirme tanımı bir görünüm açıklayan XML etiketleri kümesi tarafından tanımlanır. Her görünümü, görünümün adını Görünüm ve Tablo görünümü için sütun ve satır bilgileri gibi görünümün öğeleri kullanan nesneler içerir.

Tablo görünümü bir nesne veya bir betik bloğu değerinde bir veya daha fazla sütun özelliklerini listeler. Her sütunun tek bir özellik nesnesinin veya bir komut dosyası değerini temsil eder. Bir nesne veya özelliklerini ve değerlerini betik birleşimini özelliklerinin bir alt nesneyi tüm özelliklerini gösteren bir tablo görünümü tanımlayabilirsiniz. Tablodaki her satır, döndürülen nesneyi temsil eder. Bir tablo görünümü oluşturma çok benzer bir nesneye kanal zaman `Format-Table` cmdlet'i. Bu görünüm hakkında daha fazla bilgi için bkz: [Tablo görünümü](./creating-a-table-view.md).

Görünüm listeler bir nesne veya bir betik değeri tek bir sütunda özelliklerini listeler. Her satır listenin isteğe bağlı bir etiket veya özellik veya betik değeri tarafından izlenen özellik adını görüntüler. Bir liste görünümü oluşturmak için bir nesneye akışkan çok benzer `Format-List` cmdlet'i. Bu görünüm hakkında daha fazla bilgi için bkz: [liste görünümü](./creating-a-list-view.md).

Tek bir özellik bir nesnenin ya da bir veya daha fazla sütunda betik değerinde geniş görünüm listeler. Bu görünüm için üst bilgi veya etiket yoktur. Geniş bir görünüm oluşturmak için bir nesneye akışkan çok benzer `Format-Wide` cmdlet'i. Bu görünüm hakkında daha fazla bilgi için bkz: [geniş Görünüm](./creating-a-wide-view.md).

Özel Görünüm katı yapısını tablo görünümleri, liste görünümleri veya geniş görünümleri için belirtime uymuyor özelleştirilebilir bir görünümü nesne özelliklerini veya betik değerleri görüntüler. Tablo görünümü veya liste görünümü gibi başka bir görünüm tarafından kullanılan özel bir görünüm tanımlayabilirsiniz veya tek başına bir özel görünüm tanımlayabilirsiniz. Özel görünüm oluşturmak için bir nesneye akışkan çok benzer `Format-Custom` cmdlet'i. Bu görünüm hakkında daha fazla bilgi için bkz: [Özel Görünüm](./creating-custom-controls.md).

## <a name="components-of-a-view"></a>Görünüm bileşenleri

Aşağıdaki XML örnekler bir görünümü temel XML bileşenlerini gösterir. Tek tek XML öğeleri oluşturmak istediğiniz hangi görünüme bağlı olarak farklılık gösterir, ancak temel bileşenler görünümlerinin tüm aynıdır.

Her görünüm ile başlamak sahip bir `Name` öğesi görünümü başvurmak için kullanılan bir kullanıcı dostu adını belirtir. bir `ViewSelectedBy` tanımlayan hangi .NET nesneleri görünüm tarafından görüntülenen öğe ve bir *denetimi* görünümü tanımlayan öğe.

```xml
<ViewDefinitions>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <ListControl>...</ListControl>
  <View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <WideControl>...</WideControl>
  <View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <CustomControl>...</CustomControl>
  </View>
</ViewDefinitions>

```

Denetim öğesi içinde bir veya daha fazla tanımlayabilirsiniz *giriş* öğeleri. Birden çok tanım kullanırsanız, her tanımı hangi .NET nesnelerini kullanmak belirtmeniz gerekir. Genellikle yalnızca bir tanımı ile yalnızca bir giriş her denetim için gereklidir.

```xml
<ListControl>
  <ListEntries>
    <ListEntry>
      <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
    <ListEntry>
        <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
    <ListEntry>
        <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
  </ListEntries>
</ListControl>

```

Her giriş öğesi görünümü içinde belirttiğiniz *öğesi* , görünüm tarafından görüntülenen betikleri ve .NET özellikleri tanımlayan öğeler.

```xml

<ListItems>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
</ListItems>

```

Yukarıdaki örneklerde gösterildiği gibi biçimlendirme dosyası birden çok görünüm içerebilir, bir görünüm, birden çok tanım içerebilir ve her tanım, birden çok öğe içerebilir.

## <a name="example-of-a-table-view"></a>Tablo görünümü örneği

Aşağıdaki örnek, iki sütun içeren bir tablo görünümü tanımlamak için kullanılan XML etiketlerinin gösterir. [ViewDefinitions](./viewdefinitions-element-format.md) öğedir biçimlendirme dosyasında tanımlanan tüm görünümleri için kapsayıcı öğe. [Görünümü](./view-element-format.md) öğe, belirli bir tablo, liste, geniş veya özel görünüm tanımlar. Her [görünümü](./view-element-format.md) öğesi [adı](./name-element-for-view-format.md) öğesi, görünümün adını belirtir [ViewSelectedBy](./viewselectedby-element-format.md) öğesi görünümü ve farklı nesneleri tanımlar öğeleri (gibi `TableControl` aşağıdaki örnekte gösterildiği gibi) görünüm türünü tanımlar.

```xml
<ViewDefinitions>
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

[Bir liste görünümü oluşturma](./creating-a-list-view.md)

[Bir tablo görünümü oluşturma](./creating-a-table-view.md)

[Geniş bir görünüm oluşturma](./creating-a-wide-view.md)

[Özel denetimler oluşturma](./creating-custom-controls.md)

[Bir PowerShell biçimlendirme ve türleri dosyası yazma](./writing-a-powershell-formatting-file.md)
