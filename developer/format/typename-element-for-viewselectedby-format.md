---
title: TypeName öğesi ViewSelectedBy (biçimi) için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0ad807a9-d7d8-4e96-b799-9c6a7677cc2d
caps.latest.revision: 12
ms.openlocfilehash: e2028c479103cc414295dc24a0f9bb69190bfc66
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083765"
---
# <a name="typename-element-for-viewselectedby-format"></a>ViewSelectedBy için TypeName Öğesi (Biçim)

Görünüm tarafından görüntülenen bir .NET nesnesini belirtir.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) ViewSelectedBy öğesi (biçimi) TypeName öğesi ViewSelectedBy (biçimi) için

## <a name="syntax"></a>Sözdizimi

```xml
<TypeName>FullyQualifiedTypeName</TypeName>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Aşağıdaki öznitelikler, alt ve üst öğelerinin bölümlerde `TypeName` öğesi.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt öğeleri

Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[ViewSelectedBy öğesi (biçimi)](./viewselectedby-element-format.md)|Görünüm tarafından görüntülenen .NET nesneleri tanımlar.|

## <a name="text-value"></a>Metin değeri

.NET türünün tam adını belirttiğinizden `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Açıklamalar

Bu öğe farklı görünümleri nasıl kullanıldığı hakkında daha fazla bilgi için bkz. [bir tablo görünümü oluşturma](./creating-a-table-view.md), [bir liste görünümü oluşturma](./creating-a-list-view.md), [geniş bir görünüm oluşturma](./creating-a-wide-view.md), ve [ Özel Görünüm bileşenleri](./creating-custom-controls.md).

## <a name="example"></a>Örnek

Aşağıdaki örnek nasıl belirtileceğini gösterir [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) nesne için bir liste görünümü. Aynı şemayı, tablo, geniş ve özel görünümleri için kullanılır.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a>Ayrıca bkz:

[Bir liste görünümü oluşturma](./creating-a-list-view.md)

[Bir tablo görünümü oluşturma](./creating-a-table-view.md)

[Geniş bir görünüm oluşturma](./creating-a-wide-view.md)

[Özel denetimler oluşturma](./creating-custom-controls.md)

[ViewSelectedBy öğesi (biçimi)](./viewselectedby-element-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
