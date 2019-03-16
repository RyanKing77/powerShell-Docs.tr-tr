---
title: Bir Cmdlet'ten bir Cmdlet içinde çağırmak nasıl | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: efa4dc9c-ddee-46a3-978a-9dbb61e9bb6f
caps.latest.revision: 12
ms.openlocfilehash: 57543a88d04eb66c9d109249a99ddd272b02ef9d
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055912"
---
# <a name="how-to-invoke-a-cmdlet-from-within-a-cmdlet"></a>Cmdlet İçerisinde Cmdlet Çağırma

Bu örnek içinde geliştirdiğiniz cmdlet'e çağrılan cmdlet işlevselliğini eklemenizi sağlayan başka bir cmdlet cmdlet'inden çağırmak nasıl gösterir. Bu örnekte, `Get-Process` cmdlet'i, yerel bilgisayarda çalışan işlemler almak için çağrılır. Çağrı `Get-Process` cmdlet'i için aşağıdaki komutu eşdeğerdir. Bu komut, adları "a" ile "t" karakterleriyle başlayan tüm işlemler alır.

```powershell
Get-Process -name [a-t]
```

> [!IMPORTANT]
> Doğrudan öğesinden türetilen cmdlet'leri çağırabilirsiniz [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) sınıfı. Türetilen bir cmdlet çağrılamıyor [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) sınıfı.

## <a name="to-invoke-a-cmdlet-from-within-a-cmdlet"></a>Bir cmdlet'ten bir cmdlet içinde çağırmak için

1. Çağrılacak cmdlet tanımlayan bir derlemeye başvurulduğundan emin olun ve uygun `using` deyim eklenir. Bu örnekte, aşağıdaki ad alanlarını eklenir.

    ```csharp
    using System.Diagnostics;
    using System.Management.Automation;   // Windows PowerShell assembly.
    using Microsoft.PowerShell.Commands;  // Windows PowerShell assembly.
    ```

2. İşleme yöntemi cmdlet'inin girişinde çağrılacak cmdlet'i yeni bir örneğini oluşturun. Bu örnekte, bir nesne türü [Microsoft.PowerShell.Commands.Getprocesscommand](/dotnet/api/Microsoft.PowerShell.Commands.GetProcessCommand) cmdlet çalıştırıldığında kullanılan bağımsız değişkenler içeren bir dize ile birlikte oluşturulur.

    ```csharp
    GetProcessCommand gp = new GetProcessCommand();
    gp.Name = new string[] { "[a-t]*" };
    ```

3. Çağrı [System.Management.Automation.Cmdlet.Invoke*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) çağrılacak yöntem `Get-Process` cmdlet'i.

    ```csharp
      foreach (Process p in gp.Invoke<Process>())
      {
        Console.WriteLine(p.ToString());
      }
    }
    ```

## <a name="example"></a>Örnek

Bu örnekte, `Get-Process` cmdlet'i içinden çağrıldığında [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) bir cmdlet'in yöntemi.

```csharp
using System;
using System.Diagnostics;
using System.Management.Automation;   // Windows PowerShell assembly.
using Microsoft.PowerShell.Commands;  // Windows PowerShell assembly.

namespace SendGreeting
{
  // Declare the class as a cmdlet and specify an
  // appropriate verb and noun for the cmdlet name.
  [Cmdlet(VerbsCommunications.Send, "GreetingInvoke")]
  public class SendGreetingInvokeCommand : Cmdlet
  {
    // Declare the parameters for the cmdlet.
    [Parameter(Mandatory = true)]
    public string Name
    {
      get { return name; }
      set { name = value; }
    }
    private string name;

    // Override the BeginProcessing method to invoke
    // the Get-Process cmdlet.
    protected override void BeginProcessing()
    {
      GetProcessCommand gp = new GetProcessCommand();
      gp.Name = new string[] { "[a-t]*" };
      foreach (Process p in gp.Invoke<Process>())
      {
        Console.WriteLine(p.ToString());
      }
    }

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

## <a name="see-also"></a>Ayrıca bkz:

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)
