---
title: Runspace10 örnek | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c265084-e072-46ca-9844-c3c0e275d6b0
caps.latest.revision: 7
ms.openlocfilehash: fdf0036c68b608d254ed928ae9ac58616a856200
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059516"
---
# <a name="runspace10-sample"></a><span data-ttu-id="08dd2-102">Runspace10 Örneği</span><span class="sxs-lookup"><span data-stu-id="08dd2-102">Runspace10 Sample</span></span>

<span data-ttu-id="08dd2-103">Bu örnek, bir varsayılan ilk oturum durumu oluşturma işlemi gösterilmektedir bir cmdlet'e ekleme [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState), ilk oturum durumu kullanan bir çalışma alanı oluşturma ve çalıştırma komutunu kullanarak bir [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) nesne.</span><span class="sxs-lookup"><span data-stu-id="08dd2-103">This sample shows how to create a default initial session state, how to add a cmdlet to the [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState), how to create a runspace that uses the initial session state, and how to run the command by using a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

## <a name="requirements"></a><span data-ttu-id="08dd2-104">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="08dd2-104">Requirements</span></span>

<span data-ttu-id="08dd2-105">Bu örnek, Windows PowerShell 2.0 gerektirir.</span><span class="sxs-lookup"><span data-stu-id="08dd2-105">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="08dd2-106">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="08dd2-106">Demonstrates</span></span>

<span data-ttu-id="08dd2-107">Bu örnek aşağıdaki gösterir.</span><span class="sxs-lookup"><span data-stu-id="08dd2-107">This sample demonstrates the following.</span></span>

- <span data-ttu-id="08dd2-108">Oluşturma bir [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) nesne.</span><span class="sxs-lookup"><span data-stu-id="08dd2-108">Creating an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="08dd2-109">(Konak uygulama tarafından tanımlanan) bir cmdlet ekleme [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) nesne.</span><span class="sxs-lookup"><span data-stu-id="08dd2-109">Adding a cmdlet (defined by the Host application) to the [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="08dd2-110">Oluşturma bir [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) nesnesini kullanan bir nesne.</span><span class="sxs-lookup"><span data-stu-id="08dd2-110">Creating a [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) object that uses the object.</span></span>

- <span data-ttu-id="08dd2-111">Oluşturma bir [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) kullanan nesne [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) nesne.</span><span class="sxs-lookup"><span data-stu-id="08dd2-111">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object that uses the [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) object.</span></span>

- <span data-ttu-id="08dd2-112">Komutu ardışık düzene eklenmesi [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) nesne.</span><span class="sxs-lookup"><span data-stu-id="08dd2-112">Adding the command to the pipeline of the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="08dd2-113">Özellikleri ayıklama [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) komutu tarafından döndürülen nesne.</span><span class="sxs-lookup"><span data-stu-id="08dd2-113">Extracting properties from the [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects returned by the command.</span></span>

## <a name="example"></a><span data-ttu-id="08dd2-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="08dd2-114">Example</span></span>

<span data-ttu-id="08dd2-115">Bu örnek, kullanan bir çalışma alanı oluşturur. bir [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) çalışma açıldığında, kullanılabilir olan öğeleri tanımlamak için nesne.</span><span class="sxs-lookup"><span data-stu-id="08dd2-115">This sample creates a runspace that uses an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object to define the elements that are available when the runspace is opened.</span></span> <span data-ttu-id="08dd2-116">Bu örnekte, ilk oturum durumu için (konak uygulama tarafından tanımlanan) Get-Proc cmdlet eklenir ve cmdlet'ini kullanarak zaman uyumlu olarak çalıştırılan bir [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) nesne.</span><span class="sxs-lookup"><span data-stu-id="08dd2-116">In this sample, the Get-Proc cmdlet (defined by the Host application) is added to the initial session state, and the cmdlet is run synchronously by using a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections.Generic;
  using System.Collections.ObjectModel;
  using System.Diagnostics;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using PowerShell = System.Management.Automation.PowerShell;

  #region GetProcCommand

  /// <summary>
  /// Class that implements the GetProcCommand.
  /// </summary>
  [Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
  {
    #region Cmdlet Overrides

    /// <summary>
    /// For each of the requested process names, retrieve and write
    /// the associated processes.
    /// </summary>
    protected override void ProcessRecord()
    {
      // Get the current processes.
      Process[] processes = Process.GetProcesses();

      // Write the processes to the pipeline making them available
      // to the next cmdlet. The second argument (true) tells the
      // system to enumerate the array, and send one process object
      // at a time to the pipeline.
      WriteObject(processes, true);
    }

    #endregion Overrides
  } // End GetProcCommand class.

  #endregion GetProcCommand

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace10
  {
    /// <summary>
    /// This sample shows how to create a default initial session state, how to add
    /// add a cmdlet to the InitialSessionState object, and then how to create
    /// a Runspace object.
    /// </summary>
    /// <param name="args">Parameter is not used.</param>
    /// This sample demonstrates:
    /// 1. Creating an InitialSessionState object.
    /// 2. Adding a cmdlet to the InitialSessionState object.
    /// 3. Creating a runspace that uses the InitialSessionState object.
    /// 4. Creating a PowerShell object that uses the Runspace object.
    /// 5. Running the added command synchronously.
    /// 6. Working with PSObject objects to extract properties
    ///    from the objects returned by the pipeline.
    private static void Main(string[] args)
    {
      // Create a default InitialSessionState object. The default
      // InitialSessionState object contains all the elements provided
      // by Windows PowerShell.
      InitialSessionState iss = InitialSessionState.CreateDefault();

      // Add the get-proc cmdlet to the InitialSessionState object.
      SessionStateCmdletEntry ssce = new SessionStateCmdletEntry("get-proc", typeof(GetProcCommand), null);
      iss.Commands.Add(ssce);

      // Create a Runspace object that uses the InitialSessionState object.
      // Notice that no PSHost object is specified, so the default host is used.
      // See the Hosting samples for information on creating your own custom host.
      using (Runspace myRunSpace = RunspaceFactory.CreateRunspace(iss))
      {
        myRunSpace.Open();

        using (PowerShell powershell = PowerShell.Create())
        {
          powershell.Runspace = myRunSpace;

          // Add the get-proc cmdlet to the pipeline of the PowerShell object.
          powershell.AddCommand("get-proc");

          Collection<PSObject> results = powershell.Invoke();

          Console.WriteLine("Process              HandleCount");
          Console.WriteLine("--------------------------------");

          // Display the output of the pipeline.
          foreach (PSObject result in results)
          {
             Console.WriteLine(
                               "{0,-20} {1}",
                               result.Members["ProcessName"].Value,
                               result.Members["HandleCount"].Value);
          }
        }

        // Close the runspace to release resources.
        myRunSpace.Close();
      }

      System.Console.WriteLine("Hit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="08dd2-117">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="08dd2-117">See Also</span></span>

[<span data-ttu-id="08dd2-118">Bir Windows PowerShell ana bilgisayar uygulaması yazma</span><span class="sxs-lookup"><span data-stu-id="08dd2-118">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)