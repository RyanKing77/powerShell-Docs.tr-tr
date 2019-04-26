---
title: Basit bir Cmdlet yazma | Microsoft Docs
ms.custom: ''
ms.date: 01/15/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 137543d8-0012-4cba-bcd6-98b25aac83bb
caps.latest.revision: 9
ms.openlocfilehash: 8271512d06047f3ff5e45f81d971ffe2c1f6afd7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067748"
---
# <a name="how-to-write-a-cmdlet"></a>Bir cmdlet yazma

Bu makalede, bir cmdlet'in yazma işlemi gösterilmektedir. `Send-Greeting` Cmdlet'i tek bir kullanıcı adı giriş olarak alır ve ardından o kullanıcıya bir karşılama yazar. Bu örnekte, cmdlet kadar iş yapmaz olsa da, bir cmdlet'in ana bölümleri gösterilmektedir.

## <a name="steps-to-write-a-cmdlet"></a>Bir cmdlet yazma adımları

1. Sınıf bir cmdlet olarak bildirmek için kullanın **cmdlet'i** özniteliği. **Cmdlet'i** fiil ve isim için cmdlet adı özniteliğini belirtir.

   Hakkında daha fazla bilgi için **cmdlet'i** özniteliği için bkz: [CmdletAttribute bildirimi](cmdlet-attribute-declaration.md).

2. Sınıfın adını belirtin.

3. Cmdlet aşağıdaki sınıflar birinden türetilen belirtin:

   * [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)
   * [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)

4. Cmdlet parametrelerini tanımlamak için **parametre** özniteliği. Bu durumda, yalnızca bir parametresi belirtilen gereklidir.

   Hakkında daha fazla bilgi için **parametre** özniteliği için bkz: [ParameterAttribute bildirimi](parameter-attribute-declaration.md).

5. Giriş işleme giriş işler yöntemi yok sayın. Bu durumda, [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) yöntemi geçersiz kılınmıştır.

6. Karşılama yazılacak yöntemin kullanın [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject).
   Karşılama şu biçimde görüntülenir:

   ```Output
   Hello <UserName>!
   ```

## <a name="example"></a>Örnek

```csharp
using System.Management.Automation;  // Windows PowerShell assembly.

namespace SendGreeting
{
  // Declare the class as a cmdlet and specify the
  // appropriate verb and noun for the cmdlet name.
  [Cmdlet(VerbsCommunications.Send, "Greeting")]
  public class SendGreetingCommand : Cmdlet
  {
    // Declare the parameters for the cmdlet.
    [Parameter(Mandatory=true)]
    public string Name
    {
      get { return name; }
      set { name = value; }
    }
    private string name;

    // Override the ProcessRecord method to process
    // the supplied user name and write out a
    // greeting to the user by calling the WriteObject
    // method.
    protected override void ProcessRecord()
    {
      WriteObject("Hello " + name + "!");
    }
  }
}
```

## <a name="see-also"></a>Ayrıca bkz.

[System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)

[System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)

[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)

[CmdletAttribute bildirimi](cmdlet-attribute-declaration.md)

[ParameterAttribute bildirimi](parameter-attribute-declaration.md)

[Bir Windows PowerShell cmdlet'i yazma](writing-a-windows-powershell-cmdlet.md)