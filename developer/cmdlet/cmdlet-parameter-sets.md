---
title: Cmdlet parametresi ayarlar | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f902fd4d-8f6e-4ef1-b07f-59983039a0d1
caps.latest.revision: 10
ms.openlocfilehash: a5822ef1ed3c9efb5957c20255783d515de8957a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068529"
---
# <a name="cmdlet-parameter-sets"></a>Cmdlet Parametre Kümeleri

Windows PowerShell, parametre kümeleri sağlamak için farklı senaryolar farklı eylemler gerçekleştiren tek bir cmdlet yazma kullanır. Parametre kümeleri farklı parametreler kullanıcıya kullanıma sunmak ve kullanıcı tarafından belirtilen parametrelere bağlı olarak farklı bilgiler döndürmek için etkinleştirin.

## <a name="examples-of-parameter-sets"></a>Parametre kümeleri örnekleri

Örneğin, `Get-EventLog` cmdlet (Windows PowerShell tarafından sağlanan) olup olmadığını kullanıcının belirttiği bağlı olarak farklı bilgi döndürür `List` veya `LogName` parametresi. Varsa `List` parametresi belirtildiğinde, cmdlet kendilerini ancak içerdikleri olay bilgileri değil yalnızca günlük dosyaları hakkında bilgi döndürür. Varsa `LogName` parametresi belirtildiğinde, cmdlet, belirli bir olay günlüğüne olaylar hakkında bilgi döndürür. `List` Ve `LogName` iki ayrı parametre kümesi parametreleri tanımlayın.

## <a name="unique-parameter"></a>Benzersiz bir parametre

Her parametre kümesi, Windows PowerShell çalışma zamanı uygun parametre kümesi kullanıma sunmak için kullanabileceğiniz benzersiz bir parametreye sahip olmalıdır. Mümkünse, benzersiz bir parametre zorunlu bir parametre olmalıdır. Bir parametre zorunlu olduğunda, kullanıcı bir parametreyi belirtmek için zorlanır ve Windows PowerShell çalışma zamanı bu parametreyi kullanacak şekilde parametreyi tanımlamak için kullanabilirsiniz. Benzersiz parametre cmdlet'inize herhangi bir parametre belirtmeden çalıştırılmak üzere tasarlanmışsa zorunlu olamaz.

## <a name="multiple-parameter-sets"></a>Birden çok parametre kümeleri

Aşağıdaki çizimde, sol sütunda üç geçerli parametre kümeleri gösterir. Bir parametre ilk parametre kümesi için benzersiz olan, parametresi B ikinci parametre kümesi için benzersiz ve üçüncü parametre kümesi için parametre C benzersizdir. Ancak, sağ sütunda, parametre kümeleri benzersiz bir parametre yok.

![ps_parametersets](../media/ps-parametersets.gif)

## <a name="parameter-set-requirements"></a>Parametre kümesi gereksinimleri

Tüm parametre kümeleri için aşağıdaki gereksinimler karşılanmalıdır.

- Her parametre kümesi en az bir benzersiz parametreye sahip olmalıdır. Mümkünse, bu parametre zorunlu bir parametre olun.

- Birden çok konumsal parametreler içeren bir parametre kümesi her parametre için benzersiz konumları tanımlamanız gerekir. Hiçbir iki konumsal parametreler aynı konumu belirtebilirsiniz.

- Bir kümedeki tek bir parametre bildirebilirsiniz `ValueFromPipeline` anahtar sözcüğü değerini `true`. Birden çok parametre tanımlayabilirsiniz `ValueFromPipelineByPropertyName` anahtar sözcüğü değerini `true`.

- Hiçbir parametre kümesi için bir parametre belirtilirse, parametre için tüm parametre kümeleri aittir.

## <a name="default-parameter-sets"></a>Varsayılan parametre kümeleri

Birden fazla parametre kümesine tanımlandığında, kullanabileceğiniz `DefaultParameterSetName` varsayılan parametre kümesi belirtmek için Cmdlet özniteliğinin anahtar sözcüğü. Windows PowerShell kullanmak üzere parametre komutu tarafından sağlanan bilgilere dayanarak belirleyemiyorsa ayarlayın varsayılan parametresini kullanır. Cmdlet özniteliği hakkında daha fazla bilgi için bkz. [cmdlet'i özniteliği bildirimi](./cmdlet-attribute-declaration.md).

## <a name="declaring-parameter-sets"></a>Parametre kümeleri bildirme

Parametre kümesi oluşturmak için belirtmelisiniz `ParameterSetName` Parameter özniteliği parametre kümesindeki her parametre için bildirdiğinizde anahtar sözcüğü. Birden fazla parametre kümesine ait parametreler için her parametre kümesi için bir parametre özniteliği ekleyin. Bu parametre her parametre kümesi için farklı bir şekilde tanımlamanıza olanak sağlar. Örneğin, bir parametre zorunlu bir kümede bulunan ve başka bir isteğe bağlı olarak tanımlayabilirsiniz. Ancak, her parametre kümesi benzersiz bir parametre içermelidir.

Aşağıdaki örnekte, `UserName` parametredir benzersiz Test01 parametre kümesi ve `ComputerName` parametredir benzersiz Test02 parametre kümesi. `SharedParam` Parametresi hem kümelerine ait olan ve Test02 parametre kümesi için isteğe bağlı ancak ayarlamak Test01 parametresi zorunludur.

```csharp
[Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;

[Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test02")]
public string ComputerName
{
  get { return computerName; }
  set { computerName = value; }
}
private string computerName;

[Parameter(Mandatory= true, ParameterSetName = "Test01")]
[Parameter(ParameterSetName = "Test02")]
public string SharedParam
{
    get { return sharedParam; }
    set { sharedParam = value; }
}
private string sharedParam;    [Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```