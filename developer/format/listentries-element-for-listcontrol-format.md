---
title: ListEntries öğesi ListControl (biçimi) için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b62e81cc-4175-40fa-829f-634245b09f86
caps.latest.revision: 12
ms.openlocfilehash: aaf16702e485135b5299ccb43a2b62db2d9f5762
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847365"
---
# <a name="listentries-element-for-listcontrol-format"></a>ListControl için ListEntries Öğesi (Biçim)

Liste Görünümü tanımını sağlar. Liste görünümünde bir veya daha fazla tanımları belirtmeniz gerekir.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) ListControl öğesi (biçimi) ListEntries öğesi (biçimi)

## <a name="syntax"></a>Sözdizimi

```xml
<ListEntries>
  <ListEntry>...</ListEntry>
</ListEntries>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Öznitelikler, alt ve üst öğesini aşağıdaki bölümlerde açıklanmaktadır `ListEntries` öğesi. En az bir alt öğesi belirtilmesi gerekir.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[ListEntry öğesi (biçimi)](./listentry-element-for-listcontrol-format.md)|Liste Görünümü tanımını sağlar.|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[ListControl öğesi (biçimi)](./listcontrol-element-format.md)|Görünüm için bir liste biçimini tanımlar.|

## <a name="remarks"></a>Açıklamalar

Liste görünümleri hakkında daha fazla bilgi için bkz: [liste görünümü](./creating-a-list-view.md).

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

[ListControl öğesi (biçimi)](./listcontrol-element-format.md)

[ListEntry öğesi (biçimi)](./listentry-element-for-listcontrol-format.md)

[Liste Görünümü](./creating-a-list-view.md)

[Biçimlendirme bir Windows PowerShell yazma ve dosya türleri](./writing-a-powershell-formatting-file.md)
