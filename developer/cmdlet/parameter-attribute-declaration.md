---
title: Parametre özniteliği bildirimi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, Parameter
- Parameter attribute, described
- Parameter attribute
ms.assetid: 08433d0b-169b-42c8-9335-2881d9034698
caps.latest.revision: 13
ms.openlocfilehash: a3488d5fb3f7eb3df28d0242d6c39d07145a3c8d
ms.sourcegitcommit: 10c347a8c3dcbf8962295601834f5ba85342a87b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/07/2019
ms.locfileid: "56852146"
---
# <a name="parameter-attribute-declaration"></a>Parametre Özniteliği Bildirimi

Parametre özniteliği, bir cmdlet parametresi olarak cmdlet'i sınıfın ortak bir özelliği tanımlar.

## <a name="syntax"></a>Sözdizimi

```csharp
[Parameter()]
[Parameter(Named Parameters...)]
```

#### <a name="parameters"></a>Parametreler

`Mandatory` ([System.Boolean](/dotnet/api/System.Boolean)) isteğe bağlı parametre adı. `True` cmdlet parametresi gereklidir gösterir. Windows PowerShell cmdlet çalıştırıldığında bir gerekli parametresi sağlanmadı değilse, kullanıcı için bir parametre değeri ister. Varsayılan değer: `false`.

`ParameterSetName` ([System.String](/dotnet/api/System.String)) isteğe bağlı parametre adı. Bu cmdlet parametresi ait olduğu parametre belirtir. Hiçbir parametre kümesi belirtilirse, parametre için tüm parametre kümeleri aittir.

`Position` ([System.Integer](/dotnet/api/System.Integer)) isteğe bağlı parametre adı. Bir Windows PowerShell komutu içinde parametre konumunu belirtir.

`ValueFromPipeline` ([System.Boolean](/dotnet/api/System.Boolean)) isteğe bağlı parametre adı. `True` cmdlet parametresi değerini bir işlem hattı nesnesinden aldığını gösterir. Cmdlet tam erişirse, bu anahtar sözcük belirtin. nesne, nesnenin yalnızca bir özellik. Varsayılan değer: `false`.

`ValueFromPipelineByPropertyName` ([System.Boolean](/dotnet/api/System.Boolean)) isteğe bağlı parametre adı. `True` cmdlet parametresi değerini aynı ada veya bu parametre aynı ada sahip bir işlem hattı nesnenin bir özelliğini aldığını gösterir. Cmdlet varsa, örneğin, bir `Name` parametresi ve işlem hattı nesne de sahip bir `Name` özelliği, değeri `Name` özelliği atanır `Name` cmdlet parametresi. Varsayılan değer: `false`.

`ValueFromRemainingArguments` ([System.Boolean](/dotnet/api/System.Boolean)) isteğe bağlı parametre adı. `True` cmdlet parametresi cmdlet'e geçirilen tüm kalan bağımsız değişkenleri kabul ettiğini gösterir. Varsayılan değer: `false`.

`HelpMessage` İsteğe bağlı parametre adı. Parametre kısa bir açıklamasını belirtir. Windows PowerShell cmdlet'i çalıştırdığınızda ve zorunlu bir parametre belirtilmezse bu iletiyi görüntüler.

`HelpMessageBaseName` İsteğe bağlı parametre adı. Kaynak Tanımlayıcıları bulunduğu konumu belirtir. Örneğin, bu parametre Yerelleştirmek istediğiniz Yardım iletileri içeren bir kaynak derlemesi belirtebilirsiniz.

`HelpMessageResourceId` İsteğe bağlı parametre adı. Yardım iletisi kaynak tanımlayıcısını belirtir.

## <a name="remarks"></a>Açıklamalar

- Bu öznitelik bildirmek hakkında daha fazla bilgi için bkz. [Cmdlet parametreleri bildirmek için nasıl](./how-to-declare-cmdlet-parameters.md).

- Bir cmdlet parametreleri herhangi bir sayıda olabilir. Ancak, daha iyi bir kullanıcı deneyimi için parametre sayısını sınırlayın.

- Parametreler, genel statik olmayan alanlar veya özellikler üzerine bildirilmelidir. Parametre özellikleri bildirilmesi gerekir. Özelliği, genel ayarlama erişimcisine sahip olmalıdır ve `ValueFromPipeline` veya `ValueFromPipelineByPropertyName` anahtar sözcüğü belirtilmediğinde, özelliği bir ortak get erişimcisine sahip olmalıdır.

- Konumsal parametreler belirttiğinizde, bir parametre kümesi en az beş konumsal parametreler sayısını sınırlayın. Ve konumsal parametreler bitişik olması gerekmez. 5, 100 ve 250 konumları aynı pozisyon 0, 1 ve 2 çalışır.

- Zaman `Position` anahtar sözcüğü belirtilmezse, cmdlet parametresi adlarıyla başvurulmalıdır.

- Parametre kümeleri kullandığınızda, aşağıdakilere dikkat edin:

    - Her parametre kümesi en az bir benzersiz parametreye sahip olmalıdır. İyi cmdlet'i tasarım benzersiz Bu parametre aynı zamanda mümkünse zorunlu olması gerektiğini gösterir. Cmdlet'inize parametresiz çalıştırılmak üzere tasarlanmışsa, benzersiz bir parametre zorunlu olamaz.

    - Hiçbir parametre kümesi ile aynı konumda birden fazla konumsal parametre içermelidir.

    - Parametre kümesi yalnızca bir parametresi bildirmelidir `ValueFromPipeline = true`. Birden çok parametre tanımlayabilirsiniz `ValueFromPipelineByPropertyName = true`.

    - Birden çok parametre tanımlayabilirsiniz `ValueFromPipelineByPropertyName = true`.

- Parametre adları yönergeleri hakkında daha fazla bilgi için bkz. [Cmdlet parametresi adları](standard-cmdlet-parameter-names-and-types.md).

- Parametre özniteliği tarafından tanımlanan [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) sınıfı.

## <a name="see-also"></a>Ayrıca bkz:

[System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)

[Cmdlet parametresi adları](standard-cmdlet-parameter-names-and-types.md)

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)
