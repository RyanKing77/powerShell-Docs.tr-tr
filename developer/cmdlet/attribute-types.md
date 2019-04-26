---
title: Öznitelik türleri | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9b1026ad-f072-4fca-8052-a2d8eb491c2a
caps.latest.revision: 6
ms.openlocfilehash: 52c75b3ca73706da39029d5b3ead52ff7197a5f1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068670"
---
# <a name="attribute-types"></a>Öznitelik Türleri

Cmdlet öznitelikleri işlevselliğe göre gruplanabilir.
Aşağıdaki bölümlerde, kullanılabilen öznitelikleri açıklar ve çalışma zamanı öznitelik çağrıldığında ne yaptığını açıklar.

## <a name="cmdlet-attributes"></a>Cmdlet Öznitelikleri

### <a name="cmdlet"></a>Cmdlet

.NET Framework sınıfı bir cmdlet tanımlar.
Gerekli base özniteliği budur.
Daha fazla bilgi için [cmdlet'i özniteliği bildirimi](./cmdlet-attribute-declaration.md).

## <a name="parameter-attributes"></a>Parametre öznitelikleri

### <a name="parameter"></a>Parametre

Cmdlet sınıftaki ortak özelliği, bir cmdlet parametresi olarak tanımlar.
Daha fazla bilgi için [parametre özniteliği bildirimi](./parameter-attribute-declaration.md).

### <a name="alias"></a>Diğer Ad

Bir parametre için bir veya daha fazla diğer ad belirtir.
Daha fazla bilgi için [diğer ad özniteliği bildirimi](./alias-attribute-declaration.md).

## <a name="argument-validation-attributes"></a>Bağımsız değişken doğrulama öznitelikleri

### <a name="validatecount"></a>ValidateCount

Bağımsız bir cmdlet parametresi için izin verilen minimum ve maksimum sayısını belirtir.
Daha fazla bilgi için [ValidateCount özniteliği bildirimi](./validatecount-attribute-declaration.md).

### <a name="validatelength"></a>ValidateLength

Bir karakter cmdlet parametresi olan bir bağımsız değişken için minimum ve maksimum sayısını belirtir.
Daha fazla bilgi için [ValidateLength özniteliği bildirimi](./validatelength-attribute-declaration.md).

### <a name="validatepattern"></a>ValidatePattern

Cmdlet'i parametre bağımsız değişkenini eşleşmelidir bir normal ifade desenini belirtir.
Daha fazla bilgi için [ValidatePattern özniteliği bildirimi](./validatepattern-attribute-declaration.md).

### <a name="validaterange"></a>ValidateRange

Cmdlet parametresi olan bir bağımsız değişken için minimum ve maksimum değerleri belirtir.
Daha fazla bilgi için [ValidateRange özniteliği bildirimi](./validaterange-attribute-declaration.md).

### <a name="validateset"></a>ValidateSet

Cmdlet parametresi bağımsız değişkeni için geçerli değerler kümesini belirtir.
Daha fazla bilgi için [ValidateSet özniteliği bildirimi](./validateset-attribute-declaration.md).

## <a name="see-also"></a>Ayrıca bkz:

[Windows PowerShell SDK'sı](../windows-powershell-reference.md)
