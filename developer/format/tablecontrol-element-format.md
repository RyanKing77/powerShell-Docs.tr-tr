---
title: TableControl öğesi (biçimi) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1550b068-dfbc-4ae0-9aa1-72c9a680ec59
caps.latest.revision: 15
ms.openlocfilehash: dd48e82452e83f93e2e005c9db53bbc51d8b2eb4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848856"
---
# <a name="tablecontrol-element-format"></a>TableControl Öğesi (Biçim)

Bir görünüm için bir tablo biçiminde tanımlar.

ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) TableControl öğesi (biçimi)

## <a name="syntax"></a>Sözdizimi

```xml
<TableControl>
  <AutoSize/>
  <HideTableHeaders/>
  <TableHeaders>...</TableHeaders>
  <TableRowEntries>...</TableRowEntries>
</TableControl>

```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Aşağıdaki öznitelikler, alt ve üst öğenin bölümlerde `TableControl` öğesi. Tablonun satırlarını belirtmeniz gerekir. Diğer tüm alt öğeler isteğe bağlıdır.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[TableControl (biçimi) için AutoSize öğesi](./autosize-element-for-tablecontrol-format.md)|İsteğe bağlı öğe.<br /><br /> Sütun boyutu ve sütun sayısı verilerin boyutuna bağlı olarak ayarlanır olup olmadığını belirtir.|
|[TableControl (biçimi) için HideTableHeaders öğesi](./hidetableheaders-element-format.md)|İsteğe bağlı öğe.<br /><br /> Tablo üstbilgisinin değil görüntülenip görüntülenmeyeceğini belirtir.|
|[TableControl (biçimi) için TableHeaders öğesi](./tableheaders-element-format.md)|Gerekli öğe.<br /><br /> Etiketler, genişliğini ve Tablo görünümünde sütunları için veri hizalaması tanımlar.|
|[TableRowEntries öğesi TableCotrol (biçimi) için](./tablerowentries-element-for-tablecontrol-format.md)|İsteğe bağlı öğe.<br /><br /> Tablo görünümü tanımını sağlar.|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Görünüm öğesi (biçimi)](./view-element-format.md)|Bir veya daha fazla nesne üyeleri görüntülemek için kullanılan bir görünüm tanımlar.|

## <a name="remarks"></a>Açıklamalar

Tablo görünümü bileşenler hakkında daha fazla bilgi için bkz. [bir tablo görünümü oluşturma](./creating-a-table-view.md).

## <a name="example"></a>Örnek

Bu örnek gösterir bir `TableControl` özelliklerini görüntülemek için kullanılan öğe [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) nesne.

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>
    <TableHeaders>...</TableHeaders>
    <TableRowEntries>...</TableRowEntries>
  </TableControl>
</View>

```

## <a name="see-also"></a>Ayrıca bkz:

[Bir tablo görünümü oluşturma](./creating-a-table-view.md)

[Görünüm öğesi (biçimi)](./view-element-format.md)

[TableControl (biçimi) için AutoSize öğesi](./autosize-element-for-tablecontrol-format.md)

[HideTableHeaders öğesi (biçimi)](./hidetableheaders-element-format.md)

[TableHeaders öğesi (biçimi)](./tableheaders-element-format.md)

[TableRowEntries öğesi (biçimi)](./tablerowentries-element-for-tablecontrol-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
