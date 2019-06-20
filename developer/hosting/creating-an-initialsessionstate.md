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
ms.openlocfilehash: 9140d03e046def2fbbcc2a842b9ea1b9e1fa2985
ms.sourcegitcommit: 13f24786ed39ca1c07eff2b73a1974c366e31cb8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2019
ms.locfileid: "67263840"
---
# <a name="creating-an-initialsessionstate"></a>InitialSessionState Oluşturma

Bir çalışma alanında PowerShell komutlarını çalıştırın.
PowerShell uygulamanızı barındırmak için oluşturmanız gerekir bir [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) nesne.
Her çalışma alanı olan bir [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) ilişkili nesne.
InitialSessionState gibi komutların, değişkenlerin ve modülleri o çalışma için kullanılabilir olan bir çalışma özelliklerini belirtir.

## <a name="create-a-default-initialsessionstate"></a>Varsayılan bir InitialSessionState oluşturur

[CreateDefault](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault) ve [CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) yöntemlerinin **InitialSessionState** sınıfı oluşturmak için kullanılabilir bir **InitialSessionState**nesne.
**CreateDefault** yöntemi oluşturur bir **InitialSessionState** tüm sırasında yüklenen yerleşik komutlardır **CreateDefault2** yöntemi yalnızca komutlar yükler PowerShell (Microsoft.PowerShell.Core modülündeki komutlar) barındırmak için gereklidir.

Daha fazla ana bilgisayar uygulamanızda kullanılabilir komutları sınırlamak istiyorsanız, kısıtlı bir çalışma alanı oluşturmanız gerekir.
Bilgi için [kısıtlı bir çalışma alanı oluşturma](creating-a-constrained-runspace.md).

Aşağıdaki kod nasıl oluşturulacağını gösterir. bir **InitialSessionState**, bir çalışma alanı için atama, işlem hattı, bir çalışma, komutları eklemek ve komutları çağırır.
Ekleme ve bunları çağırırken komutları hakkında daha fazla bilgi için bkz. [ekleme ve bunları çağırırken komutları](adding-and-invoking-commands.md).

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

      // Call the PowerShell.Create() method to create the PowerShell object,
      // and then specify the runspace and commands to the pipeline.
      // and create the command pipeline.
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

## <a name="see-also"></a>Ayrıca bkz:

[Kısıtlı bir çalışma alanı oluşturma](creating-a-constrained-runspace.md)

[Ekleme ve bunları çağırırken komutları](adding-and-invoking-commands.md)
