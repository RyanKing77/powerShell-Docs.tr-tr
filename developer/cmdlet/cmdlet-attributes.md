---
title: Cmdlet öznitelikleri | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes [PowerShell SDK]
- attributes [PowerShell SDK], described
ms.assetid: d3f4f652-d929-4c27-9358-9baa390a094c
caps.latest.revision: 14
ms.openlocfilehash: 326cd408e86402974569fc76d5e473be5a56f0b6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068615"
---
# <a name="cmdlet-attributes"></a>Cmdlet Öznitelikleri

Windows PowerShell içinde kendi kodunuzu işlevselliği uygulamadan cmdlet'lerinizi için ortak işlevselliği eklemek için kullanabileceğiniz çeşitli özniteliklerini tanımlar. Bu cmdlet, ortak özellikler cmdlet'ini olarak tanımlayan parametre özniteliği tarafından döndürülen .NET Framework türlerini belirtir OutputType özniteliğini cmdlet'i bir sınıf olarak bir Microsoft .NET Framework sınıfı tanımlayan cmdlet'i özniteliği içerir Parametreler ve daha fazlası.

## <a name="in-this-section"></a>Bu Bölümde

[Cmdlet kod öznitelikleri](./attributes-in-cmdlet-code.md) cmdlet'i kodda özniteliklerini kullanmanın avantajı açıklanmaktadır.

[Öznitelik türlerini](./attribute-types.md) cmdlet'i sınıf donatmak farklı öznitelikler açıklanmaktadır.

[Diğer ad özniteliği bildirimi](./alias-attribute-declaration.md) bir cmdlet parametresi adı için diğer adlar tanımlamayı açıklar.

[Cmdlet özniteliği bildirimi](./cmdlet-attribute-declaration.md) bir .NET Framework sınıfı bir cmdlet tanımlamayı açıklar.

[Kimlik bilgisi özniteliği bildirimi](./credential-attribute-declaration.md) giriş dize dönüştürme için destek eklemeyi açıklar bir [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) nesne.

[OutputType özniteliğini bildirimi](./outputtype-attribute-declaration.md) cmdlet'i tarafından döndürülen .NET Framework türlerini belirtmek açıklar.

[Parametre özniteliği bildirimi](./parameter-attribute-declaration.md) bir cmdlet parametreleri tanımlamayı açıklar.

[ValidateCount özniteliği bildirimi](./validatecount-attribute-declaration.md) kaç tane bağımsız değişken için bir parametre izin tanımlamayı açıklar.

[ValidateLength özniteliği bildirimi](./validatelength-attribute-declaration.md) parametre bağımsız değişken uzunluğu (karakter cinsinden) tanımlamayı açıklar.

[ValidatePattern özniteliği bildirimi](./validatepattern-attribute-declaration.md) parametre bağımsız değişkeni için geçerli desenleri tanımlamayı açıklar.

[ValidateRange özniteliği bildirimi](./validaterange-attribute-declaration.md) parametre bağımsız değişkeni için geçerli aralık tanımlamayı açıklar.

[ValidateSet özniteliği bildirimi](./validateset-attribute-declaration.md) parametre bağımsız değişkeni için olası değerler tanımlamayı açıklar.

## <a name="reference"></a>Başvuru

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)
