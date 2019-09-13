---
title: Cmdlet parametre kümeleri | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f902fd4d-8f6e-4ef1-b07f-59983039a0d1
caps.latest.revision: 10
ms.openlocfilehash: d8c00c7ffd369a32af151836785a2c5f47b05a68
ms.sourcegitcommit: 889b93d170aeb3d444288e7ccf67e62ce822cb7c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70936195"
---
# <a name="cmdlet-parameter-sets"></a>Cmdlet parametre kümeleri

PowerShell, farklı senaryolar için farklı eylemler gerçekleştirebileceği tek bir cmdlet yazmanızı sağlamak üzere parametre kümelerini kullanır. Parametre kümeleri, kullanıcıya farklı parametreler sergileme olanağı sağlar. Ve, Kullanıcı tarafından belirtilen parametrelere göre farklı bilgiler döndürmek için.

## <a name="examples-of-parameter-sets"></a>Parametre kümelerine örnekler

Örneğin, PowerShell `Get-EventLog` cmdlet 'i, kullanıcının **list** veya **logName** parametresini belirttiğinden bağımsız olarak farklı bilgiler döndürür. **List** parametresi belirtilirse, cmdlet, günlük dosyaları hakkında bilgileri döndürür ancak içerdikleri olay bilgilerini içermez. **LogName** parametresi belirtilmişse, cmdlet belirli bir olay günlüğündeki olaylar hakkında bilgi döndürür. **List** ve **logName** parametreleri iki ayrı parametre kümesini tanımlar.

## <a name="unique-parameter"></a>Unique parametresi

Her parametre kümesi, PowerShell çalışma zamanının uygun parametre kümesini açığa çıkarmak için kullandığı benzersiz bir parametreye sahip olmalıdır. Mümkünse, Unique parametresi zorunlu bir parametre olmalıdır. Bir parametre zorunlu olduğunda, kullanıcının parametresini belirtmesi gerekir ve PowerShell çalışma zamanı, parametre kümesini tanımlamak için bu parametreyi kullanır. Cmdlet 'leriniz herhangi bir parametre belirtilmeden çalışacak şekilde tasarlandıysa, Unique parametresi zorunlu olamaz.

## <a name="multiple-parameter-sets"></a>Birden çok parametre kümesi

Aşağıdaki çizimde, sol sütunda üç geçerli parametre kümesi gösterilmektedir. **A parametresi** ilk parametre kümesi için benzersizdir, **B parametresi** ikinci parametre kümesi için benzersizdir ve **C parametresi** üçüncü parametre kümesine özeldir. Sağ sütunda, parametre kümelerinin benzersiz bir parametresi yoktur.

![ps_parametersets](../media/ps-parametersets.gif)

## <a name="parameter-set-requirements"></a>Parametre kümesi gereksinimleri

Aşağıdaki gereksinimler tüm parametre kümeleri için geçerlidir.

- Her parametre kümesi en az bir benzersiz parametreye sahip olmalıdır. Mümkünse, bu parametreyi zorunlu bir parametre yapın.

- Birden çok Konumsal parametre içeren bir parametre kümesi, her bir parametre için benzersiz konumlar tanımlamalıdır. İki Konumsal parametre aynı konumu belirtemez.

- Bir küme içinde yalnızca bir parametre bir `ValueFromPipeline` `true`değeri olan anahtar sözcüğü bildirebilir.
  Birden çok parametre, `ValueFromPipelineByPropertyName` bir `true`değeri olan anahtar sözcüğü tanımlayabilir.

- Parametre için bir parametre kümesi belirtilmemişse parametre tüm parametre kümelerine aittir.

> [!NOTE]
> Bir cmdlet veya işlev için, 32 parametre kümesi sınırı vardır.

## <a name="default-parameter-sets"></a>Varsayılan parametre kümeleri

Birden çok parametre kümesi tanımlandığında, varsayılan parametre kümesini belirtmek için `DefaultParameterSetName` **cmdlet** özniteliğinin anahtar sözcüğünü kullanabilirsiniz. PowerShell, komut tarafından belirtilen bilgilere göre kullanılacak parametre kümesini belirleyeleyemiyorsa varsayılan parametre kümesini kullanır. **Cmdlet** özniteliği hakkında daha fazla bilgi için bkz. [cmdlet öznitelik bildirimi](./cmdlet-attribute-declaration.md).

## <a name="declaring-parameter-sets"></a>Parametre kümelerini bildirme

Bir parametre kümesi oluşturmak için, parametre kümesindeki her parametre `ParameterSetName` için **parametre** özniteliğini bildirdiğinizde anahtar sözcüğünü belirtmeniz gerekir. Birden çok parametre kümesine ait parametreler için, her parametre kümesi için bir **parametre** özniteliği ekleyin. Bu öznitelik, parametreyi her bir parametre kümesi için farklı tanımlamanıza olanak sağlar. Örneğin, bir parametreyi bir küme içinde zorunlu olarak tanımlayabilir ve başka bir şekilde isteğe bağlı olarak tanımlayabilirsiniz. Ancak, her bir parametre kümesi bir benzersiz parametre içermelidir. Daha fazla bilgi için bkz. [parametre öznitelik bildirimi](parameter-attribute-declaration.md).

Aşağıdaki örnekte **Kullanıcı adı** parametresi, `Test01` parametre kümesinin benzersiz parametresidir ve **ComputerName** parametresi `Test02` parametre kümesinin benzersiz parametresidir. **Sharedparam** parametresi her iki kümeye aittir ve `Test01` parametre kümesi için zorunludur, `Test02` ancak parametre kümesi için isteğe bağlıdır.

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
private string sharedParam;
```
