---
title: ListControl öğesi (biçimi) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 37beeb0b-7a81-4747-becb-e309e17278fb
caps.latest.revision: 12
ms.openlocfilehash: 7a117c25b0d117dc846ba8e060e31e838b5edd52
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065266"
---
# <a name="listcontrol-element-format"></a>ListControl Öğesi (Biçim)

Görünüm için bir liste biçimini tanımlar.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) ListControl öğesi (biçimi)

## <a name="syntax"></a>Sözdizimi

```xml
<ListControl>
  <ListEntries>...</ListEntries>
</ListControl>

```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Öznitelikler, alt ve üst öğesini aşağıdaki bölümlerde açıklanmaktadır `ListControl` öğesi. Bu öğe yalnızca tek bir alt öğe içermelidir.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[ListEntries öğesi (biçimi)](./listentries-element-for-listcontrol-format.md)|Gerekli öğe.<br /><br /> Liste Görünümü tanımını sağlar.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Görünüm öğesi (biçimi)](./view-element-format.md)|Bir veya daha fazla nesne üyeleri görüntülemek için kullanılan bir görünüm tanımlar.|

## <a name="remarks"></a>Açıklamalar

Bir liste görünümü oluşturma hakkında daha fazla bilgi için bkz. [bir liste görünümü oluşturma](./creating-a-list-view.md).

## <a name="example"></a>Örnek

Bu örnek için bir liste görünümü gösterir [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) nesne.

```
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>...</ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

## <a name="see-also"></a>Ayrıca bkz:

[Görünüm öğesi (biçimi)](./view-element-format.md)

[ListEntries öğesi (biçimi)](./listentries-element-for-listcontrol-format.md)

[Bir liste görünümü oluşturma](./creating-a-list-view.md)

[Biçimlendirme bir Windows PowerShell yazma ve dosya türleri](./writing-a-powershell-formatting-file.md)
