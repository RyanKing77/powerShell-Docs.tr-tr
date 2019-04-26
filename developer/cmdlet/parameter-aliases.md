---
title: Parametre diğer adlarına | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c9096a1-46fa-48ea-9b8a-a583484b9d68
caps.latest.revision: 13
ms.openlocfilehash: 6545e71ea18d10621ee9c203e70f64dece460ef5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067595"
---
# <a name="parameter-aliases"></a>Parametre Diğer Adları

Cmdlet parametreleri, diğer adlar da olabilir. Diğer adları yerine parametre adları, yazın veya bir komut parametresini kullanabilirsiniz.

## <a name="benefits-of-using-aliases"></a>Diğer ad kullanmanın avantajları

Diğer adlar parametreleri ekleyerek, aşağıdaki avantajları sağlar.

- Böylece kullanıcı, cmdlet çağrıldığında tam parametre adı kullanmak zorunda değil, bir kısayol sağlayabilirsiniz. Örneğin, "Bilgisayaradı" parametre adı yerine "CN =" diğer ad kullanabilirsiniz.

- Aynı parametre için farklı adlar sağlamak istiyorsanız, birden fazla diğer ad tanımlayabilirsiniz. Farklı yollarla aynı veriye başvurmaktadır birden çok kullanıcı gruplarıyla çalışma varsa birden çok diğer adlarını tanımlamak isteyebilirsiniz.

- Bir parametrenin adı değişirse, var olan betikler için geriye dönük uyumluluk sağlayabilirsiniz.

- Diğer ad özniteliği ValueFromPipelineByName özniteliği ile birlikte kullanarak, farklı nesne türlerine bağlanacak cmdlet'inize izin veren bir parametre tanımlayabilirsiniz. Örneğin, iki farklı türde nesneler vardı ve yazıcı özelliği ilk nesneniz ve bir düzenleyici özelliğini ikinci nesneniz varsayalım. Cmdlet'inize sahip bir parametreye sahipse, yazıcı ve düzenleyici diğer adlar ve cmdlet ardışık giriş özellik adları göre kabul, cmdlet'inize iki parametre diğer adlarına kullanarak her iki nesnelere bağlayabilirsiniz.

Belirli parametreleri ile kullanılabilecek diğer adları hakkında daha fazla bilgi için bkz. [genel parametre adları](./common-parameter-names.md).

## <a name="defining-parameter-aliases"></a>Parametre diğer adlarına tanımlama

Bir parametre için bir diğer ad tanımlamak için aşağıdaki parametreyi bildirimde gösterildiği gibi diğer ad özniteliği bildirin. Bu örnekte, birden çok diğer adı için aynı parametre olarak tanımlanır. (Daha fazla bilgi için[Cmdlet parametreleri bildirmek için nasıl](./how-to-declare-cmdlet-parameters.md).)

```csharp
[Alias("UN","Writer","Editor")]
[Parameter()]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

## <a name="see-also"></a>Ayrıca bkz:

[Genel parametre adları](./common-parameter-names.md)

[Cmdlet parametreleri bildirmek nasıl](./how-to-declare-cmdlet-parameters.md)

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)
