---
title: Bir tablo görünümü oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1f405afb-70b5-4fe0-9986-bc07401d93fd
caps.latest.revision: 23
ms.openlocfilehash: 862f942facafff6cea66c4f8f1040772c6a62ec3
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057374"
---
# <a name="creating-a-table-view"></a>Tablo Görünümü Oluşturma

Tablo görünümü, bir veya daha fazla sütun verilerini görüntüler. Tablodaki her satır bir .NET nesnesini temsil eder ve bir tablonun her sütunu nesnesinin veya bir betik değer bir özelliği temsil eder. Bir nesnenin tüm özelliklerinin veya bir alt kümesini bir nesnenin özelliklerini gösteren bir tablo görünümü tanımlayabilirsiniz.

## <a name="a-table-view-display"></a>Tablo görünümü görüntüleme

Aşağıdaki örnek Windows PowerShell biçimini gösterir [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) tarafından döndürülen nesne [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet'i. Bu nesne için Windows PowerShell gösteren bir tablo görünümü tanımladığı `Status` özelliği `Name` özelliği (Bu özellik için bir diğer ad özelliktir `ServiceName` özelliği) ve `DisplayName` özelliği. Tablodaki her satır cmdlet'i tarafından döndürülen bir nesneyi temsil eder.

```output
Status   Name               DisplayName
------   ----               -----------
Stopped  AJRouter           AllJoyn Router Service
Stopped  ALG                Application Layer Gateway Service
Stopped  AppIDSvc           Application Identity
Running  Appinfo            Application Information
```

## <a name="defining-the-table-view"></a>Tablo görünümü tanımlama

Tablo görünümü şemasını görüntülemek için aşağıdaki XML gösterir [System.Serviceprocess.Servicecontroller? Displayproperty Fullname =](/dotnet/api/System.ServiceProcess.ServiceController) nesne. Tablo görünümünde görüntülenmesini istediğiniz her bir özellik belirtmeniz gerekir.

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>
    <TableHeaders>
      <TableColumnHeader>
        <Width>8</Width>
      </TableColumnHeader>
      <TableColumnHeader>
        <Width>18</Width>
      </TableColumnHeader>
      <TableColumnHeader>
        <Width>38</Width>
      </TableColumnHeader>
    </TableHeaders>
    <TableRowEntries>
      <TableRowEntry>
        <TableColumnItems>
          <TableColumnItem>
           <PropertyName>Status</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>Name</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>DisplayName</PropertyName>
          </TableColumnItem>
        </TableColumnItems>
      </TableRowEntry>
    </TableRowEntries>
  </TableControl>
</View>
```

Aşağıdaki XML öğeleri, bir liste görünümü tanımlamak için kullanılır:

- [Görünümü](./view-element-format.md) Tablo görünümü üst öğesinin bir öğedir. (Bu liste, geniş ve özel denetim görünümleri için aynı üst öğeye niteliğindedir.)

- [Adı](./name-element-for-view-format.md) öğesi, görünümün adını belirtir. Bu öğe tüm görünümleri için gereklidir.

- [ViewSelectedBy](./viewselectedby-element-format.md) öğe görünümünü kullanın nesneleri tanımlar. Bu öğe gereklidir.

- [GroupBy](./groupby-element-for-view-format.md) (Bu örnekte gösterilmiştir değil) öğesi, yeni bir grup nesne görüntülendiğinde tanımlar. Bir özel özellik veya betik değeri değiştiğinde yeni bir grup başlatıldı. Bu öğe isteğe bağlıdır.

- [Denetimleri](./controls-element-for-view-format.md) (Bu örnekte gösterildiği gibi değil) tablo görünümü tarafından tanımlanan özel denetimleri tanımlar. Denetimler, daha fazla verinin nasıl görüntüleneceğini belirtmek için bir yol sağlar. Bu öğe isteğe bağlıdır. Bir görünüm kendi özel denetimler tanımlayabilirsiniz veya biçimlendirme dosyasında herhangi bir görünüm tarafından kullanılabilen ortak denetimleri kullanabilirsiniz. Özel denetimler hakkında daha fazla bilgi için bkz: [özel denetimler oluşturma](./creating-custom-controls.md).

- [HideTableHeaders](./hidetableheaders-element-format.md) öğeyi (Bu örnekte gösterme) belirten Tablo üst tablonun tüm etiketleri göstermez. Bu öğe isteğe bağlıdır.

- [TableControl](./tablecontrol-element-format.md) Tablo üst bilgisi ve satır bilgilerini tanımlayan bir öğe. Diğer tüm görünümlere benzer bir tablo görünümü nesne özelliklerin değerlerini veya betikler tarafından oluşturulan değerleri görüntüleyebilirsiniz.

## <a name="defining-column-headers"></a>Sütun üst bilgilerini tanımlama

1. [TableHeaders](./tableheaders-element-format.md) öğesi ve onun alt öğeleri tanımlayan ne Tablo üst kısmında görüntülenir.

2. [TableColumnHeader](./tablecolumnheader-element-format.md) öğesi, bir tablo sütununun en üstünde gösterilen tanımlar. Bu öğeleri görüntülenen üstbilgileri istediğiniz sırayla belirtin.

   Kullanabileceğiniz bu öğe sayısı, ancak sayısı için herhangi bir sınır yoktur [TableColumnHeader](./tablecolumnheader-element-format.md) , Tablo görünümünde öğelerin sayısına eşit [TableRowEntry](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) kullandığınız öğeleri.

3. [Etiket](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) öğesi görüntülenen metni belirtir. Bu öğe isteğe bağlıdır.

4. [Genişliği](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) öğesi sütunun genişliği (karakter cinsinden) belirtir. Bu öğe isteğe bağlıdır.

5. [Hizalama](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) öğesi etiketi nasıl görüntüleneceğini belirtir. Etiket sağa sola hizalanmış veya orta. Bu öğe isteğe bağlıdır.

## <a name="defining-the-table-rows"></a>Tablo Satırları tanımlama

Tablo görünümleri, hangi verilerin alt öğelerini kullanarak tablo satırları görüntülendiğini belirten bir veya daha fazla tanımları sağlayabilir [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) öğesi. Tablonun satırlarını için birden çok tanım belirtebilirsiniz, ancak üst satırlar için aynı kalır, hangi satır tanımı kullanılan bağımsız olarak dikkat edin. Genellikle, bir tablo yalnızca bir tanımı sahip olacaktır.

Aşağıdaki örnekte, birkaç özelliklerinin değerlerini görüntüler tek bir tanım görünümü sağlar [System.Diagnostics.Process? Displayproperty Fullname =](/dotnet/api/System.Diagnostics.Process) nesne. Tablo görünümü, bir özelliğin değerini veya bir betik (örnekte gösterilmiştir değil) değerini kendi satırlarda görüntüleyebilirsiniz.

```xml
<TableRowEntries>
      <TableRowEntry>
        <TableColumnItems>
          <TableColumnItem>
           <PropertyName>Status</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>Name</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>DisplayName</PropertyName>
          </TableColumnItem>
        </TableColumnItems>
      </TableRowEntry>
    </TableRowEntries>

```

Aşağıdaki XML öğeleri, bir satır için tanımları sağlamak için kullanılabilir:

- [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) öğesi ve onun alt öğeleri tanımlamak ne tablonun satırlarını içinde görüntülenir.

- [TableRowEntry](./listentry-element-for-listcontrol-format.md) öğesi satırı tanımını sağlar. En az bir [TableRowEntry](./listentry-element-for-listcontrol-format.md) gereklidir; ancak, hiçbir ekleyebileceğiniz öğe sayısı üst sınırı yoktur. Çoğu durumda, yalnızca bir tanımı bir görünüm olacaktır.

- [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) öğesi, belirli bir tanımı tarafından görüntülenen nesneleri belirtir. Bu öğe isteğe bağlıdır ve yalnızca birden çok tanımlarken gerekli [TableRowEntry](./listentry-element-for-listcontrol-format.md) görüntüleme farklı nesneleri öğeleri.

- [Kaydırma](./wrap-element-for-tablerowentry-for-tablecontrol-format.md) öğesi ve sonraki satırda sütun genişliğini aşıyor metin görüntülendiğini belirtir. Varsayılan olarak, sütun genişliğini aşıyor metin kesilir.

- [TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) özelliklerini veya betikleri değerleri satır içinde görüntülenen öğe tanımlar.

- [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) öğe tanımlar özelliği veya betik değerini, satır sütununda görüntülenir. A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) öğesi satırın her sütun için gereklidir. İlk girişi, ilk sütunda, ikinci sütun ve benzeri ikinci girdi görüntülenir.

- [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) öğesi değeri satır içinde görüntülenen özelliği belirtir. Bir özellik ya da bir komut dosyası belirtmeniz gerekir, ancak ikisini birden belirtemezsiniz.

- [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) öğesi değeri satır içinde görüntülenen komut dosyasını belirtir. Bir betik ya da bir özellik belirtmeniz gerekir, ancak ikisini birden belirtemezsiniz.

- [FormatString](./label-element-for-listitem-for-listcontrol-format.md) öğesi özelliği veya betik değerin nasıl görüntüleneceğini tanımlayan bir biçim desenini belirtir. Bu öğe isteğe bağlıdır.

- [Hizalama](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) öğesi, özellik veya komut dosyası değerini nasıl görüntüleneceğini belirtir. Değer, sağa sola hizalanmış veya orta. Bu öğe isteğe bağlıdır.

## <a name="defining-the-objects-that-use-the-table-view"></a>Tablo görünümü kullanan nesneler tanımlama

Tablo görünümü hangi .NET nesnelerini kullanmak tanımlamak için iki yolu vardır. Kullanabileceğiniz [ViewSelectedBy](./viewselectedby-element-format.md) görünümü veya tüm tanımları tarafından görüntülenebilen nesneler tanımlamak için kullanabileceğiniz [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) hangi nesnelerin tarafından görüntülenen tanımlamak için bir Belirli görünüm tanımı. Çoğu durumda, nesneler genellikle tarafından tanımlanan şekilde bir görünümü sadece bir tanım vardır. [ViewSelectedBy](./viewselectedby-element-format.md) öğesi.

Aşağıdaki örnek, tablo görünümü kullanılarak görüntülenecek nesneleri tanımlamak gösterilmektedir [ViewSelectedBy](./viewselectedby-element-format.md) ve [TypeName](./typename-element-for-viewselectedby-format.md) öğeleri. Sınırsız sayıda [TypeName](./typename-element-for-viewselectedby-format.md) öğeleri belirtebilirsiniz ve bunların sırası önemli değildir.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

Aşağıdaki XML öğeleri, Tablo görünümünde tarafından kullanılan nesneleri belirtmek için kullanılabilir:

- [ViewSelectedBy](./viewselectedby-element-format.md) öğe tanımlar hangi nesneler tarafından liste görünümü görüntülenir.

- [TypeName](./typename-element-for-viewselectedby-format.md) öğesi görünüm tarafından görüntülenen .NET nesnesini belirtir. Tam .NET türü adı gereklidir. En az bir türü veya görünümü için seçim belirtmeniz gerekir, ancak belirtilebilir öğelerinin hiçbir üst limiti yoktur.

Aşağıdaki örnekte [ViewSelectedBy](./viewselectedby-element-format.md) ve [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) öğeleri. Bir liste görünümü ve aynı nesneleri için bir tablo görünümü tanımladığınızda gibi birden çok görünüm, görüntülenen nesnelerin ilgili kümesi sahip olduğu kullanım seçimi ayarlar. Seçimi kümesi oluşturma hakkında daha fazla bilgi için bkz. [tanımlama seçimi ayarlar](./defining-selection-sets.md).

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

Aşağıdaki XML öğeleri listesi görünümü tarafından kullanılan nesneleri belirtmek için kullanılabilir:

- [ViewSelectedBy](./viewselectedby-element-format.md) öğe tanımlar hangi nesneler tarafından liste görünümü görüntülenir.

- [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) öğesi görünüm tarafından görüntülenen bir nesne belirtir. En az bir seçimi kümesi veya görünüm türünü belirtmeniz gerekir, ancak belirtilebilir öğelerinin hiçbir üst limiti yoktur.

Aşağıdaki örnek, tablo görünümü kullanarak belirli bir tanımı tarafından görüntülenecek nesneleri tanımlamak gösterilmektedir [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) öğesi. Bu öğe kullanarak, nesne, Nesne Seçimi kümesi veya tanımı kullanıldığında belirten bir seçim koşulu .NET türü adını belirtebilirsiniz. Seçim koşullar oluşturma hakkında daha fazla bilgi için bkz. [görüntüleyen veri koşulları tanımlama](./defining-conditions-for-displaying-data.md).

> [!NOTE]
> Birden çok tablo görünümü tanımını oluştururken farklı bir sütun üst bilgileri belirtilemez. Hangi nesne tablonun satırlarını yalnızca görüntülenenleri belirtebilirsiniz.

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</TableRowEntry>
```

Aşağıdaki XML öğeleri, belirli bir liste görünümü tanımı tarafından kullanılan nesneleri belirtmek için kullanılabilir:

- [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) öğe tanımlar hangi nesnelerin tanımına göre görüntülenir.

- [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) öğe tanımına göre gösterilecek .NET nesnesini belirtir. Bu öğe kullanırken, tam .NET türü adı gereklidir. En az bir türü, seçim kümesi veya tanımı için seçim koşulu belirtmeniz gerekir, ancak belirtilebilir öğelerinin hiçbir üst limiti yoktur.

- [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) (gösterilmemiştir) öğesi bu tanımı tarafından görüntülenebilen bir nesne belirtir. En az bir türü, seçim kümesi veya tanımı için seçim koşulu belirtmeniz gerekir, ancak belirtilebilir öğelerinin hiçbir üst limiti yoktur.

- [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) (gösterilmemiştir) öğesi kullanılmak üzere bu tanım için bulunması gereken bir koşulu belirtir. En az bir türü, seçim kümesi veya tanımı için seçim koşulu belirtmeniz gerekir, ancak belirtilebilir öğelerinin hiçbir üst limiti yoktur. Seçimi koşulları tanımlama hakkında daha fazla bilgi için bkz. [görüntüleyen veri koşulları tanımlama](./defining-conditions-for-displaying-data.md).

## <a name="using-format-strings"></a>Biçim dizeleri kullanma

Daha fazla verinin nasıl görüntüleneceğini tanımlamak için bir görünüm biçimlendirme dizeleri eklenebilir. Aşağıdaki örnek, bir biçimlendirme dizesi değerini tanımlamak gösterilmektedir `StartTime` özelliği.

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

Aşağıdaki XML öğeleri, bir biçim deseni belirtmek için kullanılabilir:

- [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) öğe tanımlar özelliği veya betik değerini, satır sütununda görüntülenir. A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) öğesi satırın her sütun için gereklidir. İlk girişi, ilk sütunda, ikinci sütun ve benzeri ikinci girdi görüntülenir.

- [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) öğesi değeri satır içinde görüntülenen özelliği belirtir. Bir özellik ya da bir komut dosyası belirtmeniz gerekir, ancak ikisini birden belirtemezsiniz.

- [FormatString](./label-element-for-listitem-for-listcontrol-format.md) öğesi özelliği veya betik değerin nasıl görüntüleneceğini tanımlayan bir biçim desenini belirtir.

Aşağıdaki örnekte, `ToString` yöntemi betik değerini biçimlendirmek için çağrılır. Komut, bir nesnenin herhangi bir yöntemi çağırabilir. Bu nedenle, bir nesne gibi bir yöntem varsa `ToString`biçimlendirme parametreleri olan, betik komut çıktı değerini biçimlendirmek için bu yöntem çağırabilirsiniz.

```xml
<ListItem>
  <ScriptBlock>
    [String]::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

Aşağıdaki XML öğesi için arama kullanılabilir `ToString` yöntemi:

- [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) öğe tanımlar özelliği veya betik değerini, satır sütununda görüntülenir. A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) öğesi satırın her sütun için gereklidir. İlk girişi, ilk sütunda, ikinci sütun ve benzeri ikinci girdi görüntülenir.

- [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) öğesi değeri satır içinde görüntülenen komut dosyasını belirtir. Bir betik ya da bir özellik belirtmeniz gerekir, ancak ikisini birden belirtemezsiniz.

## <a name="see-also"></a>Ayrıca bkz:

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
