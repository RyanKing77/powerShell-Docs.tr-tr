---
title: ListEntry öğesi ListControl (biçimi) için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d16bca8-d025-432d-aa84-8b607b8af3ae
caps.latest.revision: 12
ms.openlocfilehash: 1a3bafd4ca94aee70e869c699f7a4ef8befc5511
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065232"
---
# <a name="listentry-element-for-listcontrol-format"></a>ListControl için ListEntry Öğesi (Biçim)

Liste Görünümü tanımını sağlar.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) ListControl öğesi (biçimi) ListEntries öğesi (biçimi) ListEntry öğesi (biçimi)

## <a name="syntax"></a>Sözdizimi

```xml
<ListEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Öznitelikler, alt ve üst öğesini aşağıdaki bölümlerde açıklanmaktadır `ListEntry` öğesi.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[EntrySelectedBy öğesi ListEntry (biçimi) için](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|İsteğe bağlı öğe.<br /><br /> Bu liste görünümü tanımını veya kullanılmak üzere bu tanım için bulunması gereken bir koşulu kullanan .NET nesneleri tanımlar.|
|[ListItems öğesi (biçimi)](./listitems-element-for-listentry-for-listcontrol-format.md)|Gerekli öğe.<br /><br /> Betikleri değerleri tarafından liste görünümü görüntülenir ve özellikleri tanımlar.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[ListEntries öğesi (biçimi)](./listentries-element-for-listcontrol-format.md)|Liste Görünümü tanımını sağlar.|

## <a name="remarks"></a>Açıklamalar

Bir liste görünümü özellik değerlerini ya da her nesne için betik değerlerini görüntüleyen bir liste biçimidir. Liste görünümleri hakkında daha fazla bilgi için bkz: [bir liste görünümü oluşturma](./creating-a-list-view.md).

## <a name="example"></a>Örnek

Bu örnek için liste görünümüne tanımlayan XML öğeleri gösterir [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) nesne.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>...</ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

## <a name="see-also"></a>Ayrıca bkz:

[Bir liste görünümü oluşturma](./creating-a-list-view.md)

[EntrySelectedBy öğesi ListEntry (biçimi) için](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[ListEntries öğesi (biçimi)](./listentries-element-for-listcontrol-format.md)

[ListItems öğesi (biçimi)](./listitems-element-for-listentry-for-listcontrol-format.md)

[Biçimlendirme bir Windows PowerShell yazma ve dosya türleri](./writing-a-powershell-formatting-file.md)
