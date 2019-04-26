---
title: Seçimi kümesini tanımlayan | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 00dbb5ee-93d4-4914-a082-ef4d8b236b5c
caps.latest.revision: 16
ms.openlocfilehash: 596212f2e64401a751cf3dca0ee7d60b80912c00
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066320"
---
# <a name="defining-selection-sets"></a>Seçim Kümeleri Tanımlama

Birden çok görünüm ve denetimleri oluşturma, başvurulan nesne kümeleri seçimi kümeleri olarak tanımlayabilirsiniz. Seçimi kümesi bunları her görünüm veya denetim için sürekli olarak tanımlamak zorunda kalmadan nesneleri bir kez tanımlamanızı sağlar. Genellikle, ilişkili .NET nesneleri kümeniz seçimi ayarlar kullanılır. Örneğin, `FileSystem` biçimlendirme dosyası (FileSystem.format.ps1xml) birkaç görünüm kullanan dosya sistemi türlerini seçimi kümesini tanımlar.

## <a name="where-selection-sets-are-defined-and-referenced"></a>Seçimi ayarlar tanımlanan ve başvurulan olduğu

Tüm görünümler ve biçimlendirme dosyasında tanımlanan denetimleri tarafından kullanılan ortak verileri bir parçası olarak seçimi kümelerini tanımlayın. Aşağıdaki örnek, üç seçim kümesi tanımlamak gösterilmektedir.

```xml
<Configuration>
  <SelectionSets>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
  </SelectionSets>
</Configuration>
```

Bir seçim başvurabilirsiniz aşağıdaki yollarla ayarlar:

- Her görünüm sahip bir `ViewSelectedBy` görünümü kullanarak hangi nesnelerinin görüntülenme şeklini tanımlayan öğe. `ViewSelectedBy` Öğeye sahip bir `SelectionSetName` seçimi belirtir. alt öğe kümesi, görünüm kullanımı tüm tanımları. Sayısına ilişkin bir görünümden başvurabilirsiniz seçimi ayarlar bir kısıtlama yoktur.

- Bir görünüm veya denetim, her tanımındaki `EntrySelectedBy` öğe tanımlar hangi nesnelerin bu tanımı kullanılarak görüntülenir. Nesneleri tarafından tanımlanmış genellikle bir görünüm veya denetimi sadece bir tanım sahiptir, bu nedenle `ViewSelectedBy` öğesi. `EntrySelectedBy` Tanımının öğeye sahip bir `SelectionSetName` seçimi belirtir alt öğesi. Seçimi için bir tanım Ayarla belirtirseniz, diğer alt öğelerini belirtemezsiniz `EntrySelectedBy` öğesi.

- Bir görünüm veya denetim, her tanımındaki `SelectionCondition` öğesi tanımı kullanıldığında koşulu belirtmek için kullanılabilir. `SelectionCondition` Öğeye sahip bir `SelectionSetName` Seçimi Ayarla belirten alt öğesi koşul tetikler. Seçimi kümesinde tanımlanan nesnelerden herhangi birini görüntülendiğinde koşul tetiklenir. Bu koşullar ayarlama hakkında daha fazla bilgi için bkz. [veri görüntülendiğinde için koşulları tanımlama](./defining-conditions-for-displaying-data.md).

## <a name="selection-set-example"></a>Örnek Seçimi Ayarla

Aşağıdaki örnek, doğrudan yapılan bir seçim kümesi gösterir `FileSystem` Windows PowerShell tarafından sağlanan dosya biçimlendirme. Dosyaları biçimlendirme diğer Windows PowerShell hakkında daha fazla bilgi için bkz. [Windows PowerShell biçimlendirme dosyaları](./powershell-formatting-files.md).

```xml
<SelectionSets>
  <SelectionSet>
    <Name>FileSystemTypes</Name>
    <Types>
     <TypeName>System.IO.DirectoryInfo</TypeName>
     <TypeName>System.IO.FileInfo</TypeName>
     <TypeName>Deserialized.System.IO.DirectoryInfo</TypeName>
     <TypeName>Deserialized.System.IO.FileInfo</TypeName>
    </Types>
  </SelectionSet>
</SelectionSets>
```

Önceki seçimi kümesi başvurulduğundan `ViewSelectedBy` Tablo görünümüne öğesidir.

```xml
<ViewDefinitions>
  <View>
    <Name>Files</Name>
    <ViewSelectedBy>
      <SelectionSetName>FileSystemTypes</SelectionSetName>
    </ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
</ViewDefinitions>

```

## <a name="xml-elements"></a>XML öğeleri

 Tanımlayabileceğiniz seçimi ayarlar sayısı sınırı yoktur. Aşağıdaki XML öğeleri, bir seçim kümesi oluşturmak için kullanılır.

- [SelectionSets](./selectionsets-element-format.md) öğe görünümler tarafından başvurulan .NET nesne kümesi ve biçimlendirme dosyanın denetimleri tanımlar.

- [SelectionSet](./selectionset-element-format.md) öğesi, tek bir .NET nesneleri kümesini tanımlar.

- [Adı](./name-element-for-selectionset-format.md) öğe seçimi kümesi başvurmak için kullanılan adı belirtir.

- [Türleri](./types-element-for-selectionset-format.md) öğesi Nesne Seçimi kümesinin .NET türlerini belirtir. (Dosyaları biçimlendirme içinde nesneler .NET türlerine göre belirtilir.)

 Aşağıdaki XML öğeleri, bir seçim kümesi belirtmek için kullanılır.

- Şu öğe görünümü tüm tanımları kullanacak şekilde seçimi belirtir:

    - [SelectionSetName öğesi ViewSelectedBy (biçimi) için](./selectionsetname-element-for-viewselectedby-format.md)

    - [GroupBy (biçimi) için EntrySelectedBy için SelectionSetName öğesi](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

- Aşağıdaki öğeleri tek bir görünüm tanımı tarafından kullanılan seçimi kümesini belirtin:

    - [EntrySelectedBy ListControl (biçimi) için için SelectionSetName öğesi](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

    - [TableControl (biçimi) için EntrySelectedBy için SelectionSetName öğesi](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

    - [EntrySelectedBy WideControl (biçimi) için için SelectionSetName öğesi](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

    - [SelectionSetName öğesi görünümü (biçimi) için özel denetim için EntrySelectedBy için](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

- Aşağıdaki öğeleri yaygın kullanılan seçimi kümesi belirtin ve denetim tanımları görüntüleyin:

    - [SelectionSetName öğesi görünümü (biçimi) için denetimleri için EntrySelectedBy için](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)

    - [İçin yapılandırma (biçimi) için denetimleri için EntrySelectedBy SelectionSetName öğesi](./selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format.md)

- Aşağıdaki öğeleri genişletmek için hangi nesne tanımlarken kullanılan seçimi kümesini belirtin:

    - [EntrySelectedBy EnumerableExpansion (biçimi) için için SelectionSetName öğesi](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

- Aşağıdaki öğeleri seçimi koşulları tarafından kullanılan seçimi kümesi belirtin.

    - [İçin yapılandırma (biçimi) için denetimleri için SelectionCondition SelectionSetName öğesi](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

    - [SelectionSetName öğesi görünümü (biçimi) için denetimleri için SelectionCondition için](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

    - [SelectionSetName öğesi görünümü (biçimi) için özel denetim için SelectionCondition için](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

    - [SelectionCondition EnumerableExpansion (biçimi) için EntrySelectedBy için için SelectionSetName öğesi](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

    - [SelectionCondition ListEntry (biçimi) için EntrySelectedBy için için SelectionSetName öğesi](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)

    - [TableControl (biçimi) için EntrySelectedBy için SelectionCondition için SelectionSetName öğesi](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

    - [SelectionCondition WideEntry (biçimi) için EntrySelectedBy için için SelectionSetName öğesi](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

    - [GroupBy (biçimi) için SelectionCondition için SelectionSetName öğesi](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)

## <a name="see-also"></a>Ayrıca bkz:

[SelectionSets](./selectionsets-element-format.md)

[SelectionSet](./selectionset-element-format.md)

[Ad](./name-element-for-selectionset-format.md)

[Türleri](./types-element-for-selectionset-format.md)

[PowerShell biçimlendirme dosyaları](./powershell-formatting-files.md)

[Veri görüntülendiğinde koşulları tanımlama](./defining-conditions-for-displaying-data.md)

[Bir PowerShell biçimlendirme ve türleri dosyası yazma](./writing-a-powershell-formatting-file.md)
