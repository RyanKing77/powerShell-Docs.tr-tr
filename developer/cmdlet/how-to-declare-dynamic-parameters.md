---
title: Dinamik parametreleri bildirmek nasıl | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: db04f1df-def5-4456-8869-336024cda723
caps.latest.revision: 8
ms.openlocfilehash: a9c530cdc66302eb6b3d9d2b284eeb486c3b2ba9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067935"
---
# <a name="how-to-declare-dynamic-parameters"></a>Dinamik Parametre Bildirme

Bu örnek cmdlet zamanında eklenen dinamik parametrelerin gösterir. Bu örnekte, `Department` parametresi, cmdlet'e eklendiğinde, kullanıcının belirttiği zaman `Employee` parametresi geçin. Dinamik parametreler hakkında daha fazla bilgi için bkz. [Cmdlet dinamik parametreleri](./cmdlet-dynamic-parameters.md).

## <a name="to-define-dynamic-parameters"></a>Dinamik parametreler tanımlamak için

1. Cmdlet'i sınıf bildiriminde ekleme [System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) arabirim gösterildiği gibi.

   ```csharp
   public class SendGreetingCommand : Cmdlet, IDynamicParameters
   ```

2. Çağrı [System.Management.Automation.Idynamicparameters.Getdynamicparameters*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) yöntemi dinamik parametreler tanımlandığı nesnesini döndürür. Bu örnekte, yöntem olduğunda çağrılır `Employee` parametre belirtildi.

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

3. Eklenecek dinamik parametreleri tanımlayan bir sınıf bildirme. Dinamik parametreleri bildirmek için statik cmdlet parametreleri bildirmek için kullanılan öznitelikleri kullanabilirsiniz.

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

## <a name="example"></a>Örnek

Bu örnekte, `Department` kullanıcının belirttiği zaman parametresi eklendi `Employee` parametresi. `Department` Parametresi isteğe bağlı bir parametredir ve ValidateSet özniteliği izin verilen bağımsız değişkenlerini belirtmek için kullanılır.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;     // PowerShell assembly.

namespace SendGreeting
{
  // Declare the cmdlet class that supports the
  // IDynamicParameters interface.
  [Cmdlet(VerbsCommunications.Send, "Greeting")]
  public class SendGreetingCommand : Cmdlet, IDynamicParameters
  {
    // Declare the parameters for the cmdlet.
    [Parameter(Mandatory = true)]
    public string Name
    {
      get { return name; }
      set { name = value; }
    }
    private string name;

    [Parameter]
    [Alias ("FTE")]
    public SwitchParameter Employee
    {
      get { return employee; }
      set { employee = value; }
    }
    private Boolean employee;

    // Implement GetDynamicParameters to
    // retrieve the dynamic parameter.
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

    // Overide the ProcessRecord method to process the
    // supplied user name and write out a greeting to
    // the user by calling the WriteObject method.
    protected override void ProcessRecord()
    {
      WriteObject("Hello " + name + "! ");
      if (employee)
      {
        WriteObject("Department: " + context.Department);
      }
    }
  }

  // Define the dynamic parameters to be added
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
}
```

## <a name="see-also"></a>Ayrıca bkz:

[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)

[System.Management.Automation.Idynamicparameters.Getdynamicparameters*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[Cmdlet dinamik parametreleri](./cmdlet-dynamic-parameters.md)

[Windows PowerShell SDK'sı](../windows-powershell-reference.md)