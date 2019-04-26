---
title: Parametre olarak özellikleri bildirme | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f71ea35d-cff5-4e44-a5c6-3a747ed4c4d9
caps.latest.revision: 9
ms.openlocfilehash: 6f6640afb15b3608669538f9b5f53d7a8a5c380d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068275"
---
# <a name="declaring-properties-as-parameters"></a>Özellikleri Parametre Olarak Bildirme

Bu konu, bir cmdlet parametreleri bildirmek önce anlamanız gereken temel bilgileri sağlar.

Cmdlet Sınıfınız içinde bir cmdlet parametreleri bildirmek için her parametreyi temsil eden genel özelliklerini tanımlamak ve ardından her bir özellik için bir veya daha fazla parametre öznitelikleri ekleyin. Windows PowerShell çalışma zamanı parametre öznitelikleri özelliği bir cmdlet parametresi olarak tanımlamak için kullanır. Parametre özniteliği bildirmek için temel söz dizimi `[Parameter()]`.

Gerekli parametre olarak tanımlanmış bir özellik bir örneği aşağıda verilmiştir.

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

Parametreleri hakkında hatırlamak işlemlerden bazıları aşağıda verilmiştir.

- Bir parametre açıkça genel olarak işaretlenmelidir. İç ortak varsayılan olarak işaretlenmez ve Windows PowerShell çalışma zamanı tarafından bulunmaz parametreler.

- Parametreleri daha iyi parametre doğrulaması sağlamak için Microsoft .NET Framework türleri'olarak tanımlanmamalıdır. Örneğin, bir değerler kümesi dışında bir değer sınırlı parametreleri bir numaralandırma türü tanımlanmalıdır. Bir Tekdüzen Kaynak Tanımlayıcısı (URI) değeri parametre türünden olmalıdır [System.Uri](/dotnet/api/System.Uri).

- Temel dize parametreleri tüm serbest biçimli metin özellikleri kaçının.

- Bir parametre, parametre kümeleri herhangi bir sayıda ekleyebilirsiniz. Parametre kümeleri hakkında daha fazla bilgi için bkz. [cmdlet'i parametre ayarlar](./cmdlet-parameter-sets.md).

Windows PowerShell, ayrıca her cmdlet için otomatik olarak kullanılabilen ortak parametreler kümesini sağlar. Bu parametreler ve bunların diğer adları hakkında daha fazla bilgi için bkz. [Cmdlet genel parametreleri](./common-parameter-names.md).

## <a name="see-also"></a>Ayrıca bkz:

[Cmdlet ortak parametreleri](./common-parameter-names.md)

[Cmdlet parametresi türü](./types-of-cmdlet-parameters.md)

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)
