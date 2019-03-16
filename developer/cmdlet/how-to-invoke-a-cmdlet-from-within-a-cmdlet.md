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
# <a name="how-to-invoke-a-cmdlet-from-within-a-cmdlet"></a><span data-ttu-id="af58d-102">Cmdlet İçerisinde Cmdlet Çağırma</span><span class="sxs-lookup"><span data-stu-id="af58d-102">How to Invoke a Cmdlet from Within a Cmdlet</span></span>

<span data-ttu-id="af58d-103">Bu örnek içinde geliştirdiğiniz cmdlet'e çağrılan cmdlet işlevselliğini eklemenizi sağlayan başka bir cmdlet cmdlet'inden çağırmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="af58d-103">This example shows how to invoke a cmdlet from within another cmdlet, which allows you to add the functionality of the invoked cmdlet to the cmdlet you are developing.</span></span> <span data-ttu-id="af58d-104">Bu örnekte, `Get-Process` cmdlet'i, yerel bilgisayarda çalışan işlemler almak için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="af58d-104">In this example, the `Get-Process` cmdlet is invoked to get the processes that are running on the local computer.</span></span> <span data-ttu-id="af58d-105">Çağrı `Get-Process` cmdlet'i için aşağıdaki komutu eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="af58d-105">The call to the `Get-Process` cmdlet is equivalent to the following command.</span></span> <span data-ttu-id="af58d-106">Bu komut, adları "a" ile "t" karakterleriyle başlayan tüm işlemler alır.</span><span class="sxs-lookup"><span data-stu-id="af58d-106">This command retrieves all the processes whose names start with the characters "a" through "t".</span></span>

```powershell
Get-Process -name [a-t]
```

> [!IMPORTANT]
> <span data-ttu-id="af58d-107">Doğrudan öğesinden türetilen cmdlet'leri çağırabilirsiniz [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="af58d-107">You can invoke only those cmdlets that derive directly from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class.</span></span> <span data-ttu-id="af58d-108">Türetilen bir cmdlet çağrılamıyor [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="af58d-108">You cannot invoke a cmdlet that derives from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) class.</span></span>

## <a name="to-invoke-a-cmdlet-from-within-a-cmdlet"></a><span data-ttu-id="af58d-109">Bir cmdlet'ten bir cmdlet içinde çağırmak için</span><span class="sxs-lookup"><span data-stu-id="af58d-109">To invoke a cmdlet from within a cmdlet</span></span>

1. <span data-ttu-id="af58d-110">Çağrılacak cmdlet tanımlayan bir derlemeye başvurulduğundan emin olun ve uygun `using` deyim eklenir.</span><span class="sxs-lookup"><span data-stu-id="af58d-110">Ensure that the assembly that defines the cmdlet to be invoked is referenced and that the appropriate `using` statement is added.</span></span> <span data-ttu-id="af58d-111">Bu örnekte, aşağıdaki ad alanlarını eklenir.</span><span class="sxs-lookup"><span data-stu-id="af58d-111">In this example, the following namespaces are added.</span></span>

    ```csharp
    using System.Diagnostics;
    using System.Management.Automation;   // Windows PowerShell assembly.
    using Microsoft.PowerShell.Commands;  // Windows PowerShell assembly.
    ```

2. <span data-ttu-id="af58d-112">İşleme yöntemi cmdlet'inin girişinde çağrılacak cmdlet'i yeni bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="af58d-112">In the input processing method of the cmdlet, create a new instance of the cmdlet to be invoked.</span></span> <span data-ttu-id="af58d-113">Bu örnekte, bir nesne türü [Microsoft.PowerShell.Commands.Getprocesscommand](/dotnet/api/Microsoft.PowerShell.Commands.GetProcessCommand) cmdlet çalıştırıldığında kullanılan bağımsız değişkenler içeren bir dize ile birlikte oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="af58d-113">In this example, an object of type [Microsoft.PowerShell.Commands.Getprocesscommand](/dotnet/api/Microsoft.PowerShell.Commands.GetProcessCommand) is created along with the string that contains the arguments that are used when the cmdlet is invoked.</span></span>

    ```csharp
    GetProcessCommand gp = new GetProcessCommand();
    gp.Name = new string[] { "[a-t]*" };
    ```

3. <span data-ttu-id="af58d-114">Çağrı [System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) çağrılacak yöntem `Get-Process` cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="af58d-114">Call the [System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method to invoke the `Get-Process` cmdlet.</span></span>

    ```csharp
      foreach (Process p in gp.Invoke<Process>())
      {
        Console.WriteLine(p.ToString());
      }
    }
    ```

## <a name="example"></a><span data-ttu-id="af58d-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="af58d-115">Example</span></span>

<span data-ttu-id="af58d-116">Bu örnekte, `Get-Process` cmdlet'i içinden çağrıldığında [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) bir cmdlet'in yöntemi.</span><span class="sxs-lookup"><span data-stu-id="af58d-116">In this example, the `Get-Process` cmdlet is invoked from within the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method of a cmdlet.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="af58d-117">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="af58d-117">See Also</span></span>

[<span data-ttu-id="af58d-118">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="af58d-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
