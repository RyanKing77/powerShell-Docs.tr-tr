---
title: Runspace06 örnek | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 471c85f3-9287-45c2-b4bc-833caa1b7634
caps.latest.revision: 8
ms.openlocfilehash: 3850aec88bc800718a82f51c91fbd0cb3c705089
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082660"
---
# <a name="runspace06-sample"></a>Runspace06 Örneği

Bu örnek, bir modüle ekleneceği gösterilmiştir bir [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) modülü bir çalışma açıldığında yüklenmesi nesne. Get-Proc cmdlet modülü sağlar (tarafından tanımlanan [GetProcessSample02 örnek](../cmdlet/getprocesssample02-sample.md)) çalıştırılan zaman uyumlu olarak kullanarak bir [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) nesne.

## <a name="requirements"></a>Gereksinimler

Bu örnek, Windows PowerShell 2.0 gerektirir.

## <a name="demonstrates"></a>Gösteriler

Bu örnek aşağıdaki gösterir.

- Oluşturma bir [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) nesne.

- Modül ekleme [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) nesne.

- Oluşturma bir [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) kullanan nesne [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) nesne.

- Oluşturma bir [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) nesnesini çalışma alanı kullanır.

- İşlem hattı için modülün get-proc cmdlet'i ekleniyor [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) nesne.

- Komutu eşzamanlı çalışıyor.

- Özellikleri ayıklama [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) komutu tarafından döndürülen nesne.

## <a name="example"></a>Örnek

Bu örnek, kullanan bir çalışma alanı oluşturur. bir [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) çalışma açıldığında, kullanılabilir olan öğeleri tanımlamak için nesne. Bu örnekte, ilk oturum durumu için Get-Proc cmdlet'i tanımlayan bir modül eklenir.

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections.ObjectModel;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace06
  {
    /// <summary>
    /// This sample shows how to define an initial session state that is
    /// used when creating a runspace. The sample invokes a command from
    /// a binary module that is loaded by the initial session state.
    /// </summary>
    /// <param name="args">Parameter not used.</param>
    /// <remarks>
    /// This sample assumes that user has coppied the GetProcessSample02.dll
    /// that is produced by the GetProcessSample02 sample to the current
    /// directory.
    /// This sample demonstrates the following:
    /// 1. Creating a default initial session state.
    /// 2. Adding a module to the initial session state.
    /// 3. Creating a runspace that uses the initial session state.
    /// 4. Creating a PowerShell object that uses the runspace.
    /// 5. Adding the module's get-proc cmdlet to the PowerShell object.
    /// 6. Running the command synchronously.
    /// 7. Using PSObject objects to extract and display properties from
    ///    the objects returned by the cmdlet.
    /// </remarks>
    private static void Main(string[] args)
    {
        // Create the default initial session state and add the module.
      InitialSessionState iss = InitialSessionState.CreateDefault();
      iss.ImportPSModule(new string[] { @".\GetProcessSample02.dll" });

      // Create a runspace. Notice that no PSHost object is supplied to the
      // CreateRunspace method so the default host is used. See the Host
      // samples for more information on creating your own custom host.
      using (Runspace myRunSpace = RunspaceFactory.CreateRunspace(iss))
      {
        myRunSpace.Open();

        // Create a PowerShell object.
        using (PowerShell powershell = PowerShell.Create())
        {
          // Add the cmdlet and specify the runspace.
          powershell.AddCommand(@"GetProcessSample02\get-proc");
          powershell.Runspace = myRunSpace;

          Collection<PSObject> results = powershell.Invoke();

          Console.WriteLine("Process              HandleCount");
          Console.WriteLine("--------------------------------");

          // Display the results.
          foreach (PSObject result in results)
          {
            Console.WriteLine(
                              "{0,-20} {1}",
                              result.Members["ProcessName"].Value,
                              result.Members["HandleCount"].Value);
          }
        }

        // Close the runspace to release any resources.
        myRunSpace.Close();
      }

      System.Console.WriteLine("Hit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="see-also"></a>Ayrıca bkz:

[Bir Windows PowerShell ana bilgisayar uygulaması yazma](./writing-a-windows-powershell-host-application.md)