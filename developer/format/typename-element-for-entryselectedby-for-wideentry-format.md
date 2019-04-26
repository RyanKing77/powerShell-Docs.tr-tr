---
title: TypeName öğesi EntrySelectedBy WideEntry (biçimi) için için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 81a91c74-6229-4b64-aa2b-9123e8b7e9e5
caps.latest.revision: 11
ms.openlocfilehash: be35f6e9e2ad0b2d9a21a91c053aa0f70cafaf9c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083935"
---
# <a name="typename-element-for-entryselectedby-for-wideentry-format"></a>WideEntry EntrySelectedBy için TypeName Öğesi (Biçim)

Tanımı bir .NET türünü belirtir. Bu nesne görüntülenen her tanımı kullanılır.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) WideControl öğesi (biçimi) WideEntries öğesi (biçimi) WideEntry öğesi (biçimi) EntrySelectedBy öğesi WideEntry (TypeName öğesinin WideEntry (biçimi) Biçimi)

## <a name="syntax"></a>Sözdizimi

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Öznitelikler, alt ve üst öğesini aşağıdaki bölümlerde açıklanmaktadır `TypeName` öğesi.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt öğeleri

Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[EntrySelectedBy öğesi WideEntry (biçimi) için](./entryselectedby-element-for-wideentry-format.md)|Bu geniş bir girdi veya kullanılmak üzere bu giriş için bulunması gereken bir koşulu kullanan .NET türlerini tanımlar.|

## <a name="text-value"></a>Metin değeri

.NET türünün tam adını belirttiğinizden `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Açıklamalar

Her geniş bir girdi, bir veya daha fazla .NET türleri, seçim kümesi veya tanımı kullanılmak üzere mevcut olmalıdır seçim koşulu belirtmeniz gerekir.

Geniş bir görünüm diğer bileşenler hakkında daha fazla bilgi için bkz. [geniş bir görünüm oluşturma](./creating-a-wide-view.md).

## <a name="see-also"></a>Ayrıca bkz:

[Geniş bir görünüm oluşturma](./creating-a-wide-view.md)

[EntrySelectedBy öğesi WideEntry (biçimi) için](./entryselectedby-element-for-wideentry-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
