---
title: Geniş bir görünüm oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d4303c5-b451-4ccb-9831-b17a17ceac20
caps.latest.revision: 16
ms.openlocfilehash: 651de5d3bc2619f20438f3951ac5a8c4b0bf46d4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848562"
---
# <a name="creating-a-wide-view"></a>Geniş Görünüm Oluşturma

Geniş bir görünüm, görüntülenen her nesne için tek bir değer görüntüler. Görüntülenen değer, bir .NET nesnesini özelliğinin değerini veya bir komut dosyası değerini olabilir. Varsayılan olarak, bu görünüm için üst bilgi veya etiket yoktur.

## <a name="a-wide-view-display"></a>Geniş görünüm görüntüleme

Aşağıdaki örnek Windows PowerShell biçimini gösterir [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) tarafından döndürülen nesne [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) çıktısını cmdlet'iyle yönetilir, cmdlet [ Biçim genelinde](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) cmdlet'i. (Varsayılan olarak, [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet'i bir tablo görünümü verir.) Bu örnekte, iki sütunlu, döndürülen her nesne için işlemin adını görüntülemek için kullanılır. Nesnenin özellik adını gösterilmiyorsa, yalnızca özelliğinin değeri.

```
Get-Process | format-wide
AEADISRV                     agrsmsvc
Ati2evxx                     Ati2evxx
audiodg                      CCC
CcmExec                      communicator
Crypserv                     csrss
csrss                        DevDtct2
DM1Service                   dpupdchk
dwm                          DxStudio
EXCEL                        explorer
GoogleToolbarNotifier        GrooveMonitor
hpqwmiex                     hpservice
Idle                         InoRpc
InoRT                        InoTask
ipoint                       lsass
lsm                          MOM
MSASCui                      notepad
...                          ...

```

## <a name="defining-the-wide-view"></a>Geniş bir görünüm tanımlama

Aşağıdaki XML geniş view schema gösterir [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) nesne.

```xml
View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <GroupBy>...</GroupBy>
  <Controls>...</Controls>
  <WideControl>
    <WideEntries>
      <WideEntry>
        <WideItem>
          <PropertyName>ProcessName</PropertyName>
        </WideItem>
      </WideEntry>
    </WideEntries>
  </WideControl>
</View>

```

Aşağıdaki XML öğeleri, geniş bir görünüm tanımlamak için kullanılır:

- [Görünümü](./view-element-format.md) geniş görünüm üst öğesinin bir öğedir. (Bu tablo, liste ve özel denetim görünümleri için aynı üst öğe,.)

- [Adı](./name-element-for-view-format.md) öğesi, görünümün adını belirtir. Bu öğe tüm görünümleri için gereklidir.

- [ViewSelectedBy](./viewselectedby-element-format.md) öğe görünümünü kullanın nesneleri tanımlar. Bu öğe gereklidir.

- [GroupBy](./groupby-element-for-view-format.md) öğe yeni bir grup nesne görüntülendiğinde tanımlar. Bir özel özellik veya betik değeri değiştiğinde yeni bir grup başlatıldı. Bu öğe isteğe bağlıdır.

- [Denetimleri](./controls-element-for-view-format.md) öğeleri geniş görünüm tarafından tanımlanan özel denetimleri tanımlar. Denetimler, daha fazla verinin nasıl görüntüleneceğini belirtmek için bir yol sağlar. Bu öğe isteğe bağlıdır. Bir görünüm kendi özel denetimler tanımlayabilirsiniz veya biçimlendirme dosyasında herhangi bir görünüm tarafından kullanılabilen ortak denetimleri kullanabilirsiniz. Özel denetimler hakkında daha fazla bilgi için bkz: [özel denetimler oluşturma](./creating-custom-controls.md).

- [WideControl](./widecontrol-element-format.md) öğesi ve onun alt öğeleri tanımlayan ne Görünümü'nde görüntülenir. Önceki örnekte, görünümün görüntülemek üzere tasarlanmış [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) özelliği.

Basit bir geniş görünüm tanımlayan bir tam biçimlendirme dosyası örneği için bkz. [geniş Görünüm (Temel)](./wide-view-basic.md).

## <a name="providing-definitions-for-your-wide-view"></a>Geniş görünümünüz için tanımları sağlama

Geniş görünümler, alt öğelerini kullanarak bir veya daha fazla tanımları sağlayabilir [WideControl](./widecontrol-element-format.md) öğesi. Genellikle, bir görünümü sadece bir tanım sahip olacaktır. Aşağıdaki örnekte, değerini görüntüler tek bir tanım görünümü sağlar [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) özelliği. Geniş bir görünüm, bir özelliğin değerini veya bir betik (örnekte gösterilmiştir değil) değerini görüntüleyebilirsiniz.

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber></ColumnNumber>
  <WideEntries>
    <WideEntry>
      <WideItem>
        <PropertyName>ProcessName</PropertyName>
      </WideItem>
    </WideEntry>
  </WideEntries>
</WideControl>
```

Aşağıdaki XML öğeleri, geniş bir görünüm tanımlarında sağlamak için kullanılabilir:

- [WideControl](./widecontrol-element-format.md) öğesi ve onun alt öğeleri tanımlayan ne Görünümü'nde görüntülenir.

- [AutoSize](./autosize-element-for-widecontrol-format.md) öğesi sütun boyutu ve sütun sayısı verilerin boyutuna bağlı olarak ayarlanır olup olmadığını belirtir. Bu öğe isteğe bağlıdır.

- [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) öğesi geniş görüntülenmesini sütun sayısını belirtir. Bu öğe isteğe bağlıdır.

- [WideEntries](./wideentries-element-for-widecontrol-format.md) öğesi, görünümün tanımını sağlar. Çoğu durumda, yalnızca bir tanımı bir görünüm olacaktır. Bu öğe gereklidir.

- [WideEntry](./wideentry-element-for-widecontrol-format.md) öğesi, görünümün tanımını sağlar. En az bir [WideEntry](./wideentry-element-for-widecontrol-format.md) gereklidir; ancak, hiçbir ekleyebileceğiniz öğe sayısı üst sınırı yoktur. Çoğu durumda, yalnızca bir tanımı bir görünüm olacaktır.

- [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) öğesi, belirli bir tanımı tarafından görüntülenen nesneleri belirtir. Bu öğe isteğe bağlıdır ve yalnızca birden çok tanımlarken gerekli [WideEntry](./wideentry-element-for-widecontrol-format.md) görüntüleme farklı nesneleri öğeleri.

- [WideItem](./wideitem-element-for-widecontrol-format.md) öğesi görünüm tarafından görüntülenen verileri belirtir. Diğer görünüm türleri aksine, geniş bir denetim, yalnızca bir öğe görüntüleyebilir.

- [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) öğesi değeri görünüm tarafından görüntülenen özelliği belirtir. Bir özellik ya da bir komut dosyası belirtmeniz gerekir, ancak ikisini birden belirtemezsiniz.

- [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) öğesi değeri görünüm tarafından görüntülenen komut dosyasını belirtir. Bir betik ya da bir özellik belirtmeniz gerekir, ancak ikisini birden belirtemezsiniz.

- [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) verileri görüntülemek için kullanılan bir model öğesi belirtir. Bu öğe isteğe bağlıdır.

Geniş görünüm tanımı tanımlayan bir tam biçimlendirme dosyası örneği için bkz: [geniş Görünüm (Temel)](./wide-view-basic.md).

## <a name="defining-the-objects-that-use-the-wide-view"></a>Geniş görünüm kullanan nesneler tanımlama

Hangi .NET nesneleri kullanan geniş görünüm tanımlamak için iki yolu vardır. Kullanabileceğiniz [ViewSelectedBy](./viewselectedby-element-format.md) görünümü veya tüm tanımları tarafından görüntülenebilen nesneler tanımlamak için kullanabileceğiniz [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) hangi nesnelerin tarafından görüntülenen tanımlamak için bir Belirli görünüm tanımı. Çoğu durumda, nesneler genellikle tarafından tanımlanan şekilde bir görünümü sadece bir tanım vardır. [ViewSelectedBy](./viewselectedby-element-format.md) öğesi.

Aşağıdaki örnek, geniş görünüm kullanarak görüntülenen nesneleri tanımlamak gösterilmektedir [ViewSelectedBy](./viewselectedby-element-format.md) ve [TypeName](./typename-element-for-viewselectedby-format.md) öğeleri. Sınırsız sayıda [TypeName](./typename-element-for-viewselectedby-format.md) öğeleri belirtebilirsiniz ve bunların sırası önemli değildir.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

Aşağıdaki XML öğeleri, geniş bir görünüm tarafından kullanılan nesneleri belirtmek için kullanılabilir:

- [ViewSelectedBy](./viewselectedby-element-format.md) öğesi, hangi nesnelerin geniş görünüm tarafından görüntülenen tanımlar.

- [TypeName](./typename-element-for-viewselectedby-format.md) öğesi görünüm tarafından görüntülenen .NET belirtir. Tam .NET türü adı gereklidir. En az bir türü veya görünümü için seçim belirtmeniz gerekir, ancak belirtilebilir öğelerinin hiçbir üst limiti yoktur.

Eksiksiz bir biçimlendirme dosyası örneği için bkz. [geniş Görünüm (Temel)](./wide-view-basic.md).

Aşağıdaki örnekte [ViewSelectedBy](./viewselectedby-element-format.md) ve [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) öğeleri. Geniş bir görünüm ve aynı nesneleri için bir tablo görünümü tanımladığınızda gibi birden çok görünüm, görüntülenen nesnelerin ilgili kümesi sahip olduğu kullanma seçimi ayarlar. Seçimi kümesi oluşturma hakkında daha fazla bilgi için bkz. [tanımlama seçimi ayarlar](./defining-selection-sets.md).

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

Aşağıdaki XML öğeleri, geniş bir görünüm tarafından kullanılan nesneleri belirtmek için kullanılabilir:

- [ViewSelectedBy](./viewselectedby-element-format.md) öğesi, hangi nesnelerin geniş görünüm tarafından görüntülenen tanımlar.

- [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) öğesi görünüm tarafından görüntülenen bir nesne belirtir. En az bir seçimi kümesi veya görünüm türünü belirtmeniz gerekir, ancak belirtilebilir öğelerinin hiçbir üst limiti yoktur.

Aşağıdaki örnek, geniş görünüm kullanarak belirli bir tanımı tarafından görüntülenecek nesneleri tanımlamak gösterilmektedir [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) öğesi. Bu öğe kullanarak, nesne, Nesne Seçimi kümesi veya tanımı kullanıldığında belirten bir seçim koşulu .NET türü adını belirtebilirsiniz. Seçim koşullar oluşturma hakkında daha fazla bilgi için bkz. [görüntüleyen veri koşulları tanımlama](./defining-conditions-for-displaying-data.md).

```xml
<WideEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</WideEntry>
```

Aşağıdaki XML öğeleri, belirli bir geniş görünüm tanımı tarafından kullanılan nesneleri belirtmek için kullanılabilir:

- [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) öğe tanımlar hangi nesnelerin tanımına göre görüntülenir.

- [TypeName](./typename-element-for-viewselectedby-format.md) öğe tanımına göre görüntülenen .NET belirtir. Bu öğe kullanırken tam .NET türü adı gereklidir. En az bir türü, seçim kümesi veya tanımı için seçim koşulu belirtmeniz gerekir, ancak belirtilebilir öğelerinin hiçbir üst limiti yoktur.

- [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) (gösterilmemiştir) öğesi bu tanımı tarafından görüntülenebilen bir nesne belirtir. En az bir türü, seçim kümesi veya tanımı için seçim koşulu belirtmeniz gerekir, ancak belirtilebilir öğelerinin hiçbir üst limiti yoktur.

- [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) (gösterilmemiştir) öğesi kullanılmak üzere bu tanım için bulunması gereken bir koşulu belirtir. En az bir türü, seçim kümesi veya tanımı için seçim koşulu belirtmeniz gerekir, ancak belirtilebilir öğelerinin hiçbir üst limiti yoktur. Seçimi koşulları tanımlama hakkında daha fazla bilgi için bkz. [görüntüleyen veri koşulları tanımlama](./defining-conditions-for-displaying-data.md).

## <a name="displaying-groups-of-objects-in-a-wide-view"></a>Geniş bir görünüm nesnelerin gruplarını görüntüleme

Gruplar halinde geniş görünüm tarafından görüntülenen nesneleri ayırabilirsiniz. Yalnızca belirli bir özellik veya betik değeri değiştiğinde Windows PowerShell'in yeni bir grup başlatır. Bu bir grubu tanımlayan gelmez. Aşağıdaki örnekte, yeni bir grup başlatıldığında her değeri [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) özellik değişiklikleri.

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

Grupları tanımlayan bir tam biçimlendirme dosyası örneği için bkz. [geniş Görünüm (gruplandırma ölçütü)](./wide-view-groupby.md).

## <a name="using-format-strings"></a>Biçim dizeleri kullanma

Daha fazla verinin nasıl görüntüleneceğini tanımlamak için geniş bir görünüm için biçimlendirme dizeleri eklenebilir. Aşağıdaki örnek, bir biçimlendirme dizesi değerini tanımlamak gösterilmektedir `StartTime` özelliği.

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

Aşağıdaki XML öğeleri, bir biçim deseni belirtmek için kullanılabilir:

- [WideItem](./wideitem-element-for-widecontrol-format.md) öğesi görünüm tarafından görüntülenen verileri belirtir.

- [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) öğesi değeri görünüm tarafından görüntülenen özelliği belirtir. Bir özellik ya da bir komut dosyası belirtmeniz gerekir, ancak ikisini birden belirtemezsiniz.

- [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) öğesi Görünümü'nde özellik veya betik değerin nasıl görüntüleneceğini tanımlayan bir biçim deseni belirtir

- [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) (gösterilmemiştir) öğesi değeri görünüm tarafından görüntülenen komut dosyasını belirtir. Bir betik ya da bir özellik belirtmeniz gerekir, ancak ikisini birden belirtemezsiniz.

Aşağıdaki örnekte, `ToString` yöntemi betik değerini biçimlendirmek için çağrılır. Komut, bir nesnenin herhangi bir yöntemi çağırabilir. Bu nedenle, bir nesne gibi bir yöntem varsa `ToString`biçimlendirme parametreleri olan, betik komut çıktı değerini biçimlendirmek için bu yöntem çağırabilirsiniz.

```xml
<WideItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</WideItem>
```

Aşağıdaki XML öğesi için arama kullanılabilir `ToString` yöntemi:

- [WideItem](./wideitem-element-for-widecontrol-format.md) öğesi görünüm tarafından görüntülenen verileri belirtir.

- [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) (gösterilmemiştir) öğesi değeri görünüm tarafından görüntülenen komut dosyasını belirtir. Bir betik ya da bir özellik belirtmeniz gerekir, ancak ikisini birden belirtemezsiniz.

## <a name="see-also"></a>Ayrıca bkz:

[Geniş Görünüm (Temel)](./wide-view-basic.md)

[Geniş Görünüm (gruplandırma ölçütü)](./wide-view-groupby.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
