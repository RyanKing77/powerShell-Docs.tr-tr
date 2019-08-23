---
title: Cmdlet dinamik parametreleri | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ae2196d-d6c8-4101-8805-4190d293af51
caps.latest.revision: 13
ms.openlocfilehash: 19d31f6b619dff23e7e35bb53d2397f4f41eb728
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986245"
---
# <a name="cmdlet-dynamic-parameters"></a>Cmdlet dinamik parametreleri

Cmdlet 'leri, başka bir parametrenin bağımsız değişkeninin belirli bir değer olduğu durumlar gibi özel koşullar altında Kullanıcı tarafından kullanılabilen parametreleri tanımlayabilir. Bu parametreler çalışma zamanına eklenir ve yalnızca gerektiğinde eklendiğinden dinamik parametreler olarak adlandırılır. Örneğin, yalnızca belirli bir anahtar parametresi belirtildiğinde birkaç parametre ekleyen bir cmdlet tasarlayabilirsiniz.

> [!NOTE]
> Sağlayıcılar ve PowerShell işlevleri, dinamik parametreleri de tanımlayabilir.

## <a name="dynamic-parameters-in-powershell-cmdlets"></a>PowerShell cmdlet 'lerinde dinamik parametreler

PowerShell, çeşitli sağlayıcı cmdlet 'lerinde dinamik parametreler kullanır. Örneğin `Get-Item` , `Get-ChildItem` ve cmdlet 'leri, **yol** parametresi **sertifika** sağlayıcısı yolunu belirttiğinde çalışma zamanında bir **codesigningcert** parametresi ekler. **Yol** parametresi farklı bir sağlayıcı için bir yol belirtirse, **codesigningcert** parametresi kullanılamaz.

Aşağıdaki örneklerde, çalıştırıldığında **codesigningcert** parametresinin çalışma zamanında `Get-Item` nasıl eklendiği gösterilmektedir.

Bu örnekte, PowerShell çalışma zamanı parametresini ekledi ve cmdlet başarılı olur.

```powershell
Get-Item -Path cert:\CurrentUser -CodeSigningCert
```

```Output
Location   : CurrentUser
StoreNames : {SmartCardRoot, UserDS, AuthRoot, CA...}
```

Bu örnekte bir **dosya sistemi** sürücüsü belirtilir ve bir hata döndürülür. Hata iletisi **Codesigningcert** parametresinin bulunamadığını gösterir.

```powershell
Get-Item -Path C:\ -CodeSigningCert
```

```Output
Get-Item : A parameter cannot be found that matches parameter name 'codesigningcert'.
At line:1 char:37
+  get-item -path C:\ -codesigningcert <<<<
--------
    CategoryInfo          : InvalidArgument: (:) [Get-Item], ParameterBindingException
    FullyQualifiedErrorId : NamedParameterNotFound,Microsoft.PowerShell.Commands.GetItemCommand
```

## <a name="support-for-dynamic-parameters"></a>Dinamik parametreler için destek

Dinamik parametreleri desteklemek için aşağıdaki öğelerin cmdlet koduna eklenmesi gerekir.

### <a name="interface"></a>Arabirim

[System. Management. Automation. ıdynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters).
Bu arabirim, dinamik parametreleri alan yöntemi sağlar.

Örneğin:

`public class SendGreetingCommand : Cmdlet, IDynamicParameters`

### <a name="method"></a>Yöntem

[System. Management. Automation. ıdynamicparameters. GetDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters).
Bu yöntem, dinamik parametre tanımlarını içeren nesneyi alır.

Örneğin:

```csharp
 public object GetDynamicParameters()
 {
   if (employee)
   {
     context= new SendGreetingCommandDynamicParameters();
     return context;
   }
   return null;
}
private SendGreetingCommandDynamicParameters context;
```

### <a name="class"></a>Sınıf

Eklenecek dinamik parametreleri tanımlayan bir sınıf. Bu sınıf her bir parametre için bir **parametre** özniteliği ve cmdlet için gereken herhangi bir Isteğe bağlı **diğer ad** ve **doğrulama** özniteliği içermelidir.

Örneğin:

```csharp
public class SendGreetingCommandDynamicParameters
{
  [Parameter]
  [ValidateSet ("Marketing", "Sales", "Development")]
  public string Department
  {
    get { return department; }
    set { department = value; }
  }
  private string department;
}
```

Dinamik parametreleri destekleyen bir cmdlet 'inin tamamen bir örneği için bkz. [dinamik parametreleri bildirme](./how-to-declare-dynamic-parameters.md).

## <a name="see-also"></a>Ayrıca bkz.

[System. Management. Automation. ıdynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters)

[System. Management. Automation. ıdynamicparameters. GetDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[Dinamik parametreleri bildirme](./how-to-declare-dynamic-parameters.md)

[Windows PowerShell cmdlet 'ı yazma](./writing-a-windows-powershell-cmdlet.md)
