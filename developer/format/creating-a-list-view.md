---
title: Bir liste görünümü oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c7a40ca-1786-46f0-bab5-6ce229daa7ee
caps.latest.revision: 14
ms.openlocfilehash: 25d24063501196d44e0f806a55bb699c82f771ce
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850718"
---
# <a name="creating-a-list-view"></a>Liste Görünümü Oluşturma

Bir liste görünümü verilerini tek bir sütunda (sırayla) görüntüler. Listede görüntülenen verileri, bir .NET özelliğinin değerini veya bir betik değeri olabilir.

## <a name="a-list-view-display"></a>Bir liste görünümü görüntüleme

Aşağıdaki çıktı, Windows PowerShell özelliklerinin nasıl görüntülediğini gösterir [System.Serviceprocess.Servicecontroller? Displayproperty Fullname =](/dotnet/api/System.ServiceProcess.ServiceController) tarafından döndürülen nesneleri [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet'i. Bu örnekte, üç nesneler, önceki nesneden boş bir satır tarafından ayrılmış her bir nesne ile döndürüldü.

```powershell
Get-Service | format-list
```

```output
Name                : AEADIFilters
DisplayName         : Andrea ADI Filters Service
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32OwnProcess

Name                : AeLookupSvc
DisplayName         : Application Experience
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32ShareProcess

Name                : AgereModemAudio
DisplayName         : Agere Modem Call Progress Audio
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32OwnProcess
...
```

## <a name="defining-the-list-view"></a>Liste görünümü tanımlama

Aşağıdaki XML çeşitli özelliklerini görüntülemek için liste görünümü şeması gösterir [System.Serviceprocess.Servicecontroller? Displayproperty Fullname =](/dotnet/api/System.ServiceProcess.ServiceController) nesne. Liste görünümünde görüntülenmesini istediğiniz her bir özellik belirtmeniz gerekir.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>
          <ListItem>
            <PropertyName>Name</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>DisplayName</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>Status</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>ServiceType</PropertyName>
          </ListItem>
        </ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

Aşağıdaki XML öğeleri, bir liste görünümü tanımlamak için kullanılır:

- [Görünümü](./view-element-format.md) liste görünümü üst öğesinin bir öğedir. (Aynı üst öğeye tablosu, geniş ve özel denetim görünümleri için budur.)

- [Adı](./name-element-for-view-format.md) öğesi, görünümün adını belirtir. Bu öğe tüm görünümleri için gereklidir.

- [ViewSelectedBy](./viewselectedby-element-format.md) öğe görünümünü kullanın nesneleri tanımlar. Bu öğe gereklidir.

- [GroupBy](./groupby-element-for-view-format.md) öğe yeni bir grup nesne görüntülendiğinde tanımlar. Bir özel özellik veya betik değeri değiştiğinde yeni bir grup başlatıldı. Bu öğe isteğe bağlıdır.

- [Denetimleri](./controls-element-for-view-format.md) öğe listesi görünümü tarafından tanımlanan özel denetimleri tanımlar. Denetimler, daha fazla verinin nasıl görüntüleneceğini belirtmek için bir yol sağlar. Bu öğe isteğe bağlıdır. Bir görünüm kendi özel denetimler tanımlayabilirsiniz veya biçimlendirme dosyasında herhangi bir görünüm tarafından kullanılabilen ortak denetimleri kullanabilirsiniz. Özel denetimler hakkında daha fazla bilgi için bkz: [özel denetimler oluşturma](./creating-custom-controls.md).

- [ListControl](./listcontrol-element-format.md) nasıl biçimlendirildiğini ve ne görünümünde görüntülenen öğe tanımlar. Diğer tüm görünümlere benzer bir liste görünümü nesne özelliklerin değerlerini veya komut dosyası tarafından oluşturulan değerleri görüntüleyebilirsiniz.

Basit Liste Görünümü tanımlayan bir tam biçimlendirme dosyası örneği için bkz: [liste görünümü (Temel)](./list-view-basic.md).

## <a name="providing-definitions-for-your-list-view"></a>Liste Görünümü tanımlarında sağlama

Liste görünümleri, alt öğelerini kullanarak bir veya daha fazla tanımları sağlayabilir [ListControl](./listcontrol-element-format.md) öğesi. Genellikle, bir görünümü sadece bir tanım sahip olacaktır. Aşağıdaki örnekte, çeşitli özelliklerini görüntüler tek bir tanım görünümü sağlar [System.Diagnostics.Process? Displayproperty Fullname =](/dotnet/api/System.Diagnostics.Process) nesne. Bir liste görünümü, bir özelliğin değerini veya bir betik (örnekte gösterilmiştir değil) değerini görüntüleyebilirsiniz.

```xml
<ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>
          <ListItem>
            <PropertyName>Name</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>DisplayName</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>Status</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>ServiceType</PropertyName>
          </ListItem>
        </ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>

```

Aşağıdaki XML öğeleri, bir liste görünümü tanımlarında sağlamak için kullanılabilir:

- [ListControl](./listcontrol-element-format.md) öğesi ve onun alt öğeleri tanımlayan ne Görünümü'nde görüntülenir.

- [ListEntries](./listentries-element-for-listcontrol-format.md) öğesi, görünümün tanımını sağlar. Çoğu durumda, yalnızca bir tanımı bir görünüm olacaktır. Bu öğe gereklidir.

- [ListEntry](./listentry-element-for-listcontrol-format.md) öğesi, görünümün tanımını sağlar. En az bir [ListEntry](./listentry-element-for-listcontrol-format.md) gereklidir; ancak, hiçbir ekleyebileceğiniz öğe sayısı üst sınırı yoktur. Çoğu durumda, yalnızca bir tanımı bir görünüm olacaktır.

- [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) öğesi, belirli bir tanımı tarafından görüntülenen nesneleri belirtir. Bu öğe isteğe bağlıdır ve yalnızca birden çok tanımlarken gerekli [ListEntry](./listentry-element-for-listcontrol-format.md) görüntüleme farklı nesneleri öğeleri.

- [ListItems](./listitems-element-for-listentry-for-listcontrol-format.md) öğesi betikleri değerleri, liste görünümü satırlarda görüntülenir ve özelliklerini belirtir.

- [ListItem](./listitems-element-for-listentry-for-listcontrol-format.md) öğeyi belirten bir özellik veya betik değeri liste görünümünün bir satır görüntülenir. Bir liste görünümü, en az bir özellik ya da komut dosyasını belirtmeniz gerekir. Belirtilen satır sayısı maksimum sınırı yoktur.

- [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) öğesi değeri satır içinde görüntülenen özelliği belirtir. Bir özellik ya da bir komut dosyası belirtmeniz gerekir, ancak ikisini birden belirtemezsiniz.

- [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) öğesi değeri satır içinde görüntülenen komut dosyasını belirtir. Bir betik ya da bir özellik belirtmeniz gerekir, ancak ikisini birden belirtemezsiniz.

- [Etiket](./label-element-for-listitem-for-listcontrol-format.md) öğesi sıradaki özelliği veya betik değer solunda görüntülenen etiketi belirtir. Bu öğe isteğe bağlıdır. Bir etiket belirtilmezse, özelliği veya komut dosyası adı görüntülenir. Tam bir örnek için bkz. [liste görünümü (etiketler)](./list-view-labels.md).

- [ItemSelectionCondition](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) öğesi görüntülenecek satır için bulunması gereken bir koşulu belirtir. Liste görünümüne koşul ekleme hakkında daha fazla bilgi için bkz. [görüntüleyen veri koşulları tanımlama](./defining-conditions-for-displaying-data.md). Bu öğe isteğe bağlıdır.

- [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) öğesi özelliği veya komut dosyası değerini görüntülemek için kullanılan bir desen belirtir. Bu öğe isteğe bağlıdır.

Basit Liste Görünümü tanımlayan bir tam biçimlendirme dosyası örneği için bkz: [liste görünümü (Temel)](./list-view-basic.md).

## <a name="defining-the-objects-that-use-the-list-view"></a>Liste görünümüne kullanan nesneler tanımlama

Liste görünümüne hangi .NET nesnelerini kullanmak tanımlamak için iki yolu vardır. Kullanabileceğiniz [ViewSelectedBy](./viewselectedby-element-format.md) görünümü veya tüm tanımları tarafından görüntülenebilen nesneler tanımlamak için kullanabileceğiniz [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) hangi nesnelerin tarafından görüntülenen tanımlamak için bir Belirli görünüm tanımı. Çoğu durumda, nesneler genellikle tarafından tanımlanan şekilde bir görünümü sadece bir tanım vardır. [ViewSelectedBy](./viewselectedby-element-format.md) öğesi.

Aşağıdaki örnek, liste görünümü kullanarak görüntülenen nesneleri tanımlamak gösterilmektedir [ViewSelectedBy](./viewselectedby-element-format.md) ve [TypeName](./typename-element-for-viewselectedby-format.md) öğeleri. Sınırsız sayıda [TypeName](./typename-element-for-viewselectedby-format.md) öğeleri belirtebilirsiniz ve bunların sırası önemli değildir.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

Aşağıdaki XML öğeleri listesi görünümü tarafından kullanılan nesneleri belirtmek için kullanılabilir:

- [ViewSelectedBy](./viewselectedby-element-format.md) öğe tanımlar hangi nesneler tarafından liste görünümü görüntülenir.

- [TypeName](./typename-element-for-viewselectedby-format.md) öğesi görünüm tarafından görüntülenen .NET nesnesini belirtir. Tam .NET türü adı gereklidir. En az bir türü veya görünümü için seçim belirtmeniz gerekir, ancak belirtilebilir öğelerinin hiçbir üst limiti yoktur.

Eksiksiz bir biçimlendirme dosyası örneği için bkz. [liste görünümü (Temel)](./list-view-basic.md).

Aşağıdaki örnekte [ViewSelectedBy](./viewselectedby-element-format.md) ve [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) öğeleri. Bir liste görünümü ve aynı nesneleri için bir tablo görünümü tanımladığınızda gibi birden çok görünüm, görüntülenen nesnelerin ilgili kümesi sahip olduğu kullanım seçimi ayarlar. Seçimi kümesi oluşturma hakkında daha fazla bilgi için bkz. [tanımlama seçimi ayarlar](./defining-selection-sets.md).

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

Aşağıdaki XML öğeleri listesi görünümü tarafından kullanılan nesneleri belirtmek için kullanılabilir:

- [ViewSelectedBy](./viewselectedby-element-format.md) öğe tanımlar hangi nesneler tarafından liste görünümü görüntülenir.

- [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) öğesi görünüm tarafından görüntülenen bir nesne belirtir. En az bir seçimi kümesi veya görünüm türünü belirtmeniz gerekir, ancak belirtilebilir öğelerinin hiçbir üst limiti yoktur.

Aşağıdaki örnek, liste görünümünü kullanarak, belirli bir tanımı tarafından görüntülenecek nesneleri tanımlamak gösterilmektedir [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) öğesi. Bu öğe kullanarak, nesne, Nesne Seçimi kümesi veya tanımı kullanıldığında belirten bir seçim koşulu .NET türü adını belirtebilirsiniz. Seçim koşullar oluşturma hakkında daha fazla bilgi için bkz. [görüntüleyen veri koşulları tanımlama](./defining-conditions-for-displaying-data.md).

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</ListEntry>
```

Aşağıdaki XML öğeleri, belirli bir liste görünümü tanımı tarafından kullanılan nesneleri belirtmek için kullanılabilir:

- [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) öğe tanımlar hangi nesnelerin tanımına göre görüntülenir.

- [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) öğe tanımına göre gösterilecek .NET nesnesini belirtir. Bu öğe kullanırken, tam .NET türü adı gereklidir. En az bir türü, seçim kümesi veya tanımı için seçim koşulu belirtmeniz gerekir, ancak belirtilebilir öğelerinin hiçbir üst limiti yoktur.

- [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) (gösterilmemiştir) öğesi bu tanımı tarafından görüntülenebilen bir nesne belirtir. En az bir türü, seçim kümesi veya tanımı için seçim koşulu belirtmeniz gerekir, ancak belirtilebilir öğelerinin hiçbir üst limiti yoktur.

- [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) (gösterilmemiştir) öğesi kullanılmak üzere bu tanım için bulunması gereken bir koşulu belirtir. En az bir türü, seçim kümesi veya tanımı için seçim koşulu belirtmeniz gerekir, ancak belirtilebilir öğelerinin hiçbir üst limiti yoktur. Seçimi koşulları tanımlama hakkında daha fazla bilgi için bkz. [görüntüleyen veri koşulları tanımlama](./defining-conditions-for-displaying-data.md).

## <a name="displaying-groups-of-objects-in-a-list-view"></a>Nesne bir liste görünümü görüntüleme

Liste Görünümü gruplar tarafından görüntülenen nesneleri ayırabilirsiniz. Yalnızca belirli bir özellik veya betik değeri değiştiğinde Windows PowerShell'in yeni bir grup başlatır. Bu bir grubu tanımlayan gelmez. Aşağıdaki örnekte, yeni bir grup başlatıldığında her değeri [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) özellik değişiklikleri.

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

Aşağıdaki XML öğeleri bir grup başlatıldığında tanımlamak için kullanılır:

- [GroupBy](./groupby-element-for-view-format.md) öğesi, özellik veya yeni Grup başlar ve Grup nasıl görüntüleneceğini tanımlar betiği tanımlar.

- [PropertyName](./propertyname-element-for-groupby-format.md) değeri değiştiğinde yeni bir grup başlatan özellik öğesi belirtir. Bir özellik veya grubu başlatmak için komut dosyasını belirtmeniz gerekir, ancak ikisini birden belirtemezsiniz.

- [ScriptBlock](./scriptblock-element-for-groupby-format.md) öğesi değeri değiştiğinde yeni bir grup başlatan komut dosyasını belirtir. Bir betiği veya grup başlatmak için özellik belirtmeniz gerekir, ancak ikisini birden belirtemezsiniz.

- [Etiket](./label-element-for-groupby-format.md) her grubu başında görüntülenen etiket öğe tanımlar. Bu öğe tarafından belirtilen metin ek olarak, Windows PowerShell öncesi ve sonrası etiketi boş bir satır ekler ve yeni Grup tetiklenen değeri görüntüler. Bu öğe isteğe bağlıdır.

- [Özel denetim](./customcontrol-element-for-groupby-format.md) öğe verileri görüntülemek için kullanılan bir denetimi tanımlar. Bu öğe isteğe bağlıdır.

- [CustomControlName](./customcontrolname-element-for-groupby-format.md) öğeyi belirten bir ortak veya verileri görüntülemek için kullanılan denetim görüntüleyin. Bu öğe isteğe bağlıdır.

Grupları tanımlayan bir tam biçimlendirme dosyası örneği için bkz. [liste görünümü (gruplandırma ölçütü)](./list-view-groupby.md).

## <a name="using-format-strings"></a>Biçim dizeleri kullanma

Daha fazla verinin nasıl görüntüleneceğini tanımlamak için bir görünüm biçimlendirme dizeleri eklenebilir. Aşağıdaki örnek, bir biçimlendirme dizesi değerini tanımlamak gösterilmektedir `StartTime` özelliği.

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

Aşağıdaki XML öğeleri, bir biçim deseni belirtmek için kullanılabilir:

- [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) öğesi görünüm tarafından görüntülenen verileri belirtir.

- [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) öğesi değeri görünüm tarafından görüntülenen özelliği belirtir. Bir özellik ya da bir komut dosyası belirtmeniz gerekir, ancak ikisini birden belirtemezsiniz.

- [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) öğesi Görünümü'nde özellik veya betik değerin nasıl görüntüleneceğini tanımlayan bir biçim desenini belirtir.

- [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) (gösterilmemiştir) öğesi değeri görünüm tarafından görüntülenen komut dosyasını belirtir. Bir betik ya da bir özellik belirtmeniz gerekir, ancak ikisini birden belirtemezsiniz.

Aşağıdaki örnekte, `ToString` yöntemi betik değerini biçimlendirmek için çağrılır. Komut, bir nesnenin herhangi bir yöntemi çağırabilir. Bu nedenle, bir nesne gibi bir yöntem varsa `ToString`biçimlendirme parametreleri olan, betik komut çıktı değerini biçimlendirmek için bu yöntem çağırabilirsiniz.

```xml
<ListItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

Aşağıdaki XML öğesi için arama kullanılabilir `ToString` yöntemi:

- [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) öğesi görünüm tarafından görüntülenen verileri belirtir.

- [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) (gösterilmemiştir) öğesi değeri görünüm tarafından görüntülenen komut dosyasını belirtir. Bir betik ya da bir özellik belirtmeniz gerekir, ancak ikisini birden belirtemezsiniz.

## <a name="see-also"></a>Ayrıca bkz:

[Bir Windows PowerShell cmdlet'i yazma](../cmdlet/writing-a-windows-powershell-cmdlet.md)
