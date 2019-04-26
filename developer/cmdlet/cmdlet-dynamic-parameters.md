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
ms.openlocfilehash: 2fc73b6ef5a862fafb7a3c8fe3da19ac71bafc05
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068547"
---
# <a name="cmdlet-dynamic-parameters"></a>Cmdlet Dinamik Parametreler

Cmdlet'leri kullanıcının belirli bir değerin başka bir parametre bağımsız değişkeni olduğunda gibi özel koşullarda parametrelerini tanımlayabilirsiniz. Bu parametreleri çalışma zamanında eklenir ve denir *dinamik parametreleri* çünkü yalnızca ihtiyacınız olduğunda eklenir. Örneğin, yalnızca belirli anahtar parametresi belirtildiğinde, birkaç parametre ekleyen bir cmdlet tasarlayabilirsiniz.

> [!NOTE]
> Sağlayıcıları ve Windows PowerShell işlevleri dinamik parametreler de tanımlayabilirsiniz.

## <a name="dynamic-parameters-in-windows-powershell-cmdlets"></a>Windows PowerShell cmdlet'lerinde dinamik parametreler

Windows PowerShell sağlayıcısı cmdlet'lerini bazılarını dinamik parametreler kullanır. Örneğin, `Get-Item` ve `Get-ChildItem` cmdlet'leri eklendi bir `CodeSigningCert` zamanında parametre olduğunda `Path` cmdlet parametresi sertifika sağlayıcısı yolunu belirtir. Varsa `Path` cmdlet parametresi, farklı bir sağlayıcı için bir yol belirtir `CodeSigningCert` parametresi kullanılamaz.

Aşağıdaki örneklerde gösterildiği nasıl `CodeSigningCert` parametresi, çalışma zamanında eklenir, `Get-Item` cmdlet'ini çalıştırın.

İlk örnekte, Windows PowerShell çalışma zamanı parametresi eklendi ve cmdlet başarısız olur.

```powershell
Get-Item -Path cert:\CurrentUser -codesigningcert
```

```output
Location   : CurrentUser
StoreNames : {SmartCardRoot, UserDS, AuthRoot, CA...}
```

İkinci örnekte, bir dosya sistemi sürücü belirtilir ve bir hata döndürdü. Hata iletisi gösterir `CodeSigningCert` parametresi bulunamıyor.

```powershell
Get-Item -Path C:\ -codesigningcert
```

```output
Get-Item : A parameter cannot be found that matches parameter name 'codesigningcert'.
At line:1 char:37
+  get-item -path C:\ -codesigningcert <<<<
--------
    CategoryInfo          : InvalidArgument: (:) [Get-Item], ParameterBindingException
    FullyQualifiedErrorId : NamedParameterNotFound,Microsoft.PowerShell.Commands.GetItemCommand
```

## <a name="support-for-dynamic-parameters"></a>Dinamik parametreleri için destek

Dinamik parametreleri desteklemek için cmdlet kod aşağıdaki öğeleri içermelidir.

[System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) dinamik parametreleri alır, yöntem bu arabirim sağlar.

Örnek:

`public class SendGreetingCommand : Cmdlet, IDynamicParameters`

[System.Management.Automation.Idynamicparameters.Getdynamicparameters*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) bu yöntem dinamik parametre tanımları içeren nesneyi alır.

Örnek:

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

Bu sınıf, dinamik parametre sınıfı eklenecek parametreleri tanımlar. Bu sınıf, her bir parametre ve cmdlet tarafından gerekli olan isteğe bağlı diğer ad ve doğrulama öznitelikleri için bir parametre özniteliği içermelidir.

Örnek:

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

Dinamik parametreleri destekleyen bir cmdlet tam bir örnek için bkz: [nasıl dinamik parametreleri bildirmek için](./how-to-declare-dynamic-parameters.md).

## <a name="see-also"></a>Ayrıca bkz:

[System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters)

[System.Management.Automation.Idynamicparameters.Getdynamicparameters*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[Dinamik parametreleri bildirmek nasıl](./how-to-declare-dynamic-parameters.md)

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)
