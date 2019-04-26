---
title: Bir InitialSessionState oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ae707db-52e0-408c-87fa-b35c42eaaab1
caps.latest.revision: 5
ms.openlocfilehash: 3a7c47487b632d00643fce0aa082e0dc9a9bb626
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083000"
---
# <a name="creating-an-initialsessionstate"></a><span data-ttu-id="84894-102">InitialSessionState Oluşturma</span><span class="sxs-lookup"><span data-stu-id="84894-102">Creating an InitialSessionState</span></span>

<span data-ttu-id="84894-103">Bir çalışma alanında Windows PowerShell komutlarını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="84894-103">Windows PowerShell commands run in a runspace.</span></span> <span data-ttu-id="84894-104">Windows PowerShell uygulamanızı barındırmak için oluşturmanız gerekir bir [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) nesne.</span><span class="sxs-lookup"><span data-stu-id="84894-104">To host Windows PowerShell in your application, you must create a [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) object.</span></span> <span data-ttu-id="84894-105">Her çalışma alanı olan bir [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) ilişkili nesne.</span><span class="sxs-lookup"><span data-stu-id="84894-105">Every runspace has an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object associated with it.</span></span> <span data-ttu-id="84894-106">[System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) gibi komutların, değişkenlerin ve modülleri olan bu çalışma alanı için kullanılabilir çalışma alanı özelliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="84894-106">The [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) specifies characteristics of the runspace, such as which commands, variables, and modules are available for that runspace.</span></span>

## <a name="create-a-default-initialsessionstate"></a><span data-ttu-id="84894-107">Varsayılan bir InitialSessionState oluşturur</span><span class="sxs-lookup"><span data-stu-id="84894-107">Create a default InitialSessionState</span></span>

 <span data-ttu-id="84894-108">[System.Management.Automation.Runspaces.Initialsessionstate.Createdefault\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault)ve [System.Management.Automation.Runspaces.Initialsessionstate.Createdefault2\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) yöntemleri kullanılabilir Oluşturulacak [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) nesneleri.</span><span class="sxs-lookup"><span data-stu-id="84894-108">The [System.Management.Automation.Runspaces.Initialsessionstate.Createdefault\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault)and [System.Management.Automation.Runspaces.Initialsessionstate.Createdefault2\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) methods can be used to create [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objects.</span></span> <span data-ttu-id="84894-109">[System.Management.Automation.Runspaces.Initialsessionstate.Createdefault\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault) bir InitialSessionState tüm yerleşik komutlar sırasında yüklenen oluşturur [ System.Management.Automation.Runspaces.Initialsessionstate.Createdefault2\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) yalnızca Windows PowerShell (Microsoft.PowerShell.Core modülündeki komutlar. ana bilgisayar için gerekli komutları yükler</span><span class="sxs-lookup"><span data-stu-id="84894-109">[System.Management.Automation.Runspaces.Initialsessionstate.Createdefault\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault) creates an InitialSessionState with all of the built-in commands loaded, while [System.Management.Automation.Runspaces.Initialsessionstate.Createdefault2\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) loads only the commands required to host Windows PowerShell (the commands from the Microsoft.PowerShell.Core module.</span></span>

 <span data-ttu-id="84894-110">Daha fazla ana bilgisayar uygulamanızda kullanılabilir komutları sınırlamak istiyorsanız, kısıtlı bir çalışma alanı oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="84894-110">If you want to further limit the commands available in your host application you need to create a constrained runspace.</span></span> <span data-ttu-id="84894-111">Kısıtlı bir çalışma alanı oluşturma hakkında bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="84894-111">For information, see Creating a constrained runspace.</span></span>

 <span data-ttu-id="84894-112">Aşağıdaki kod, bir InitialSessionState oluşturmak, bir çalışma alanı için atama, işlem hattı, bir çalışma, komutları eklemek ve komutları çağırır gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="84894-112">The following code shows how to create an InitialSessionState, assign it to a runspace, add commands to the pipeline in that runspace, and invoke the commands.</span></span> <span data-ttu-id="84894-113">Ekleme ve bunları çağırırken komutları ekleme ve bunları çağırırken komutları hakkında daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="84894-113">For more information about adding and invoking commands, see Adding and invoking commands.</span></span>

```csharp

namespace SampleHost
{
  using System;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;

  class HostP4b
  {
    static void Main(string[] args)
    {
      // Call the InitialSessionState.CreateDefault method to create
      // an empty InitialSessionState object, and then add the
      // elements that will be available when the runspace is opened.
      InitialSessionState iss = InitialSessionState.CreateDefault();
      SessionStateVariableEntry var1 = new
          SessionStateVariableEntry("test1",
                                    "MyVar1",
                                    "Initial session state MyVar1 test");
      iss.Variables.Add(var1);

      SessionStateVariableEntry var2 = new
          SessionStateVariableEntry("test2",
                                    "MyVar2",
                                    "Initial session state MyVar2 test");
      iss.Variables.Add(var2);

      // Call the RunspaceFactory.CreateRunspace(InitialSessionState)
      // method to create the runspace where the pipeline is run.
      Runspace rs = RunspaceFactory.CreateRunspace(iss);
      rs.Open();

      // Call the PowerShell.Create() method to create the PowerShell
      // object,and then specify the runspace and commands to the pipeline.
      // and  create the command pipeline.
      PowerShell ps = PowerShell.Create();
      ps.Runspace = rs;
      ps.AddCommand("Get-Variable");
      ps.AddArgument("test*");

      Console.WriteLine("Variable             Value");
      Console.WriteLine("--------------------------");

      // Call the PowerShell.Invoke() method to run
      // the pipeline synchronously.
        foreach (PSObject result in ps.Invoke())
        {
          Console.WriteLine("{0,-20}{1}",
                  result.Members["Name"].Value,
                  result.Members["Value"].Value);
        } // End foreach.

        // Close the runspace to free resources.
        rs.Close();

    } // End Main.
  } // End SampleHost.
}
```

## <a name="see-also"></a><span data-ttu-id="84894-114">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="84894-114">See Also</span></span>

 [<span data-ttu-id="84894-115">Kısıtlı bir çalışma alanı oluşturma</span><span class="sxs-lookup"><span data-stu-id="84894-115">Creating a constrained runspace</span></span>](./creating-a-constrained-runspace.md)
