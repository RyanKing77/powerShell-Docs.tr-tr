---
title: Parametre kümeleri nasıl | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 46905eb9-64d7-4c55-9c2a-7bc7bf04e14b
caps.latest.revision: 10
ms.openlocfilehash: 6c2e5891a8e3f24969c12a2e57dc5ae8caa68e41
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067901"
---
# <a name="how-to-declare-parameter-sets"></a>Parametre Kümelerini Bildirme

Bu örnek, bir cmdlet parametreleri bildirdiğinizde, iki parametre kümeleri tanımlamak gösterilmektedir. Her parametre kümesi benzersiz bir parametre hem de her iki parametre kümeleri tarafından kullanılan paylaşılan bir parametre vardır. Varsayılan parametre kümesi belirleme de dahil olmak üzere, parametre kümeleri hakkında daha fazla bilgi için bkz. [cmdlet'i parametre ayarlar](./cmdlet-parameter-sets.md).

> [!IMPORTANT]
> Mümkün olduğunda, gerekli bir parametre bir parametrenin benzersiz parametre tanımlayın. Ancak, herhangi bir parametre belirtmeden çalıştırılacak cmdlet'inize istiyorsanız benzersiz parametresi isteğe bağlı bir parametre olabilir. Örneğin, benzersiz parametresinin `Get-Command` cmdlet'i, isteğe bağlıdır.

## <a name="how-to-define-two-parameter-sets"></a>İki parametre kümesi tanımlama

1. Ekleme `ParameterSet` benzersiz parametresi ilk parametre kümesi için parametre özniteliği için anahtar sözcüğü.

   ```csharp
   [Parameter(Position = 0, Mandatory = true,
              ParameterSetName = "Test01")]
   public string UserName
   {
     get { return userName; }
     set { userName = value; }
   }
   private string userName;
   ```

2. Ekleme `ParameterSet` ikinci parametre kümesi benzersiz parametresi için parametre özniteliği için anahtar sözcüğü.

   ```csharp
   [Parameter(Position = 0, Mandatory = true,
              ParameterSetName = "Test02")]
   public string ComputerName
   {
     get { return computerName; }
     set { computerName = value; }
   }
   private string computerName;
   ```

3. Her iki parametre kümelerine ait parametresi için her parametre kümesi için bir parametre özniteliği ekleyin ve sonra ekleyin `ParameterSet` anahtar sözcüğü her kümesi. Her parametre özniteliği, bu parametrenin nasıl tanımlandığını belirtebilirsiniz. Bir parametre, isteğe bağlı bir kümede bulunan ve başka bir zorunlu olabilir.

   ```csharp
   [Parameter(Mandatory= true, ParameterSetName = "Test01")]
   [Parameter(ParameterSetName = "Test02")]
   public string SharedParam
   {
       get { return sharedParam; }
       set { sharedParam = value; }
   }
   private string sharedParam;
   ```

## <a name="see-also"></a>Ayrıca bkz:

[Cmdlet parametre kümeleri](./cmdlet-parameter-sets.md)

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)
