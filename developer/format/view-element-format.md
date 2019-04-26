---
title: Öğesi (biçimi) görüntüleme | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d837d5d4-ed2e-4d84-a306-0b5d2ad2d0bf
caps.latest.revision: 24
ms.openlocfilehash: 2361c1117757569bef0815018c75764430a9e7a8
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083731"
---
# <a name="view-element-format"></a>Görünüm Öğesi (Biçim)

Bir veya daha fazla .NET nesnelerini görüntüleyen bir görünüm tanımlar. Bir biçimlendirme dosyasında tanımlanan görünümleri sayısı sınırı yoktur.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi)

## <a name="syntax"></a>Sözdizimi

```xml
<View>
  <Name>Friendly name of view.</Name>
  <ViewSelectedBy>...</ViewSelectedBy>
  <Controls>...</Controls>
  <GroupBy>...</GroupBy>
  <TableControl>...</TableControl>
  <ListControl>...</ListControl>
  <WideControl>...</WideControl>
  <CustomControl>...</CustomControl>
</View>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Öznitelikler, alt ve üst öğesini aşağıdaki bölümlerde açıklanmaktadır `View` öğesi. Bir ve yalnızca bir denetim alt öğeleri belirtmeniz gerekir ve görünümü ve görünüm kullanan nesneler adını belirtmeniz gerekir. Özel denetimleri tanımlama, nesneleri nasıl gruplanacağını ve görünüm bant dışı olup olmadığını belirten isteğe bağlı.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[Denetim öğesi görünümü (biçimi)](./controls-element-for-view-format.md)|İsteğe bağlı öğe.<br /><br /> Görünümü içinde adlarına başvurduğu denetimleri kümesini tanımlar.|
|[Özel denetim öğesi (biçimi)](./customcontrol-element-for-groupby-format.md)|İsteğe bağlı öğe.<br /><br /> Görünüm için bir özel denetim biçimini tanımlar.|
|[GroupBy öğesi görünümü (biçimi)](./groupby-element-for-view-format.md)|İsteğe bağlı öğe.<br /><br /> .NET nesneleri üyelerin gruplandırılma tanımlar.|
|[ListControl öğesi (biçimi)](./listcontrol-element-format.md)|İsteğe bağlı öğe.<br /><br /> Görünüm için bir liste biçimini tanımlar.|
|[Name öğesi görünümü (biçimi)](./name-element-for-view-format.md)|Gerekli öğe.<br /><br /> Görünüm başvurmak için kullanılan adını belirtir.|
|[TableControl öğesi (biçimi)](./tablecontrol-element-format.md)|İsteğe bağlı öğe.<br /><br /> Görünüm için bir tablo biçiminde tanımlar.|
|[ViewSelectedBy öğesi görünümü (biçimi)](./viewselectedby-element-format.md)|Gerekli öğe.<br /><br /> Bu görünüm görüntüler .NET nesneleri tanımlar.|
|[WideControl öğesi (biçimi)](./widecontrol-element-format.md)|İsteğe bağlı öğe.<br /><br /> Bir geniş (çoklu değer) tanımlar görünüm için liste biçimini.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[ViewDefinitions öğesi (biçimi)](./viewdefinitions-element-format.md)|Nesneleri görüntülemek için kullanılan görünümleri tanımlar.|

## <a name="remarks"></a>Açıklamalar

Farklı görünümleri özel denetimleri ve bileşenleri hakkında daha fazla bilgi için aşağıdaki konulara bakın:

- [Tablo görünümü bileşenleri](./creating-a-table-view.md)

- [Liste Görünümü bileşenleri](./creating-a-list-view.md)

- [Geniş görünüm bileşenleri](./creating-a-wide-view.md)

- [Özel denetimler](./creating-custom-controls.md)

## <a name="example"></a>Örnek

Bu örnek gösterir bir `View` için bir tablo görünümü tanımlayan öğe [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) nesne.

```xml
<ViewDefinitions>
  <View>
    <Name>service</Name>
    <ViewSelectedBy>
      <TypeName>System.ServiceProcess.ServiceController</TypeName>
    </ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
</ViewDefinitions>

```

## <a name="see-also"></a>Ayrıca bkz:

[ViewDefinitions öğesi (biçimi)](./viewdefinitions-element-format.md)

[Name öğesi görünümü (biçimi)](./name-element-for-view-format.md)

[ViewSelectedBy öğesi (biçimi)](./viewselectedby-element-format.md)

[Denetim öğesi görünümü (biçimi)](./controls-element-for-view-format.md)

[GroupBy öğesi görünümü (biçimi)](./groupby-element-for-view-format.md)

[TableControl öğesi (biçimi)](./tablecontrol-element-format.md)

[ListControl öğesi (biçimi)](./listcontrol-element-format.md)

[WideControl öğesi (biçimi)](./widecontrol-element-format.md)

[Özel denetim öğesi (biçimi)](./customcontrol-element-for-groupby-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
