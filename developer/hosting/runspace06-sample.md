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
ms.openlocfilehash: 8621878a339751d2cef842af6f5b3d5d2e270346
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851446"
---
# <a name="runspace06-sample"></a><span data-ttu-id="83b91-102">Runspace06 Örneği</span><span class="sxs-lookup"><span data-stu-id="83b91-102">Runspace06 Sample</span></span>

<span data-ttu-id="83b91-103">Bu örnek, bir modüle ekleneceği gösterilmiştir bir [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) modülü bir çalışma açıldığında yüklenmesi nesne.</span><span class="sxs-lookup"><span data-stu-id="83b91-103">This sample shows how to add a module to an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object so that the module is loaded when the runspace is opened.</span></span> <span data-ttu-id="83b91-104">Get-Proc cmdlet modülü sağlar (tarafından tanımlanan [GetProcessSample02 örnek](../cmdlet/getprocesssample02-sample.md)) çalıştırılan zaman uyumlu olarak kullanarak bir [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) nesne.</span><span class="sxs-lookup"><span data-stu-id="83b91-104">The module provides a Get-Proc cmdlet (defined by the [GetProcessSample02 Sample](../cmdlet/getprocesssample02-sample.md)) that is run synchronously by using a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

## <a name="requirements"></a><span data-ttu-id="83b91-105">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="83b91-105">Requirements</span></span>

<span data-ttu-id="83b91-106">Bu örnek, Windows PowerShell 2.0 gerektirir.</span><span class="sxs-lookup"><span data-stu-id="83b91-106">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="83b91-107">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="83b91-107">Demonstrates</span></span>

<span data-ttu-id="83b91-108">Bu örnek aşağıdaki gösterir.</span><span class="sxs-lookup"><span data-stu-id="83b91-108">This sample demonstrates the following.</span></span>

- <span data-ttu-id="83b91-109">Oluşturma bir [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) nesne.</span><span class="sxs-lookup"><span data-stu-id="83b91-109">Creating an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="83b91-110">Modül ekleme [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) nesne.</span><span class="sxs-lookup"><span data-stu-id="83b91-110">Adding the module to the [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="83b91-111">Oluşturma bir [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) kullanan nesne [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) nesne.</span><span class="sxs-lookup"><span data-stu-id="83b91-111">Creating a [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) object that uses the [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="83b91-112">Oluşturma bir [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) nesnesini çalışma alanı kullanır.</span><span class="sxs-lookup"><span data-stu-id="83b91-112">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object that uses the runspace.</span></span>

- <span data-ttu-id="83b91-113">İşlem hattı için modülün get-proc cmdlet'i ekleniyor [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) nesne.</span><span class="sxs-lookup"><span data-stu-id="83b91-113">Adding the module's get-proc cmdlet to the pipeline of the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="83b91-114">Komutu eşzamanlı çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="83b91-114">Running the command synchronously.</span></span>

- <span data-ttu-id="83b91-115">Özellikleri ayıklama [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) komutu tarafından döndürülen nesne.</span><span class="sxs-lookup"><span data-stu-id="83b91-115">Extracting properties from the [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) objects returned by the command.</span></span>

## <a name="example"></a><span data-ttu-id="83b91-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="83b91-116">Example</span></span>

<span data-ttu-id="83b91-117">Bu örnek, kullanan bir çalışma alanı oluşturur. bir [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) çalışma açıldığında, kullanılabilir olan öğeleri tanımlamak için nesne.</span><span class="sxs-lookup"><span data-stu-id="83b91-117">This sample creates a runspace that uses an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object to define the elements that are available when the runspace is opened.</span></span> <span data-ttu-id="83b91-118">Bu örnekte, ilk oturum durumu için Get-Proc cmdlet'i tanımlayan bir modül eklenir.</span><span class="sxs-lookup"><span data-stu-id="83b91-118">In this sample, a module that defines a Get-Proc cmdlet is added to the initial session state.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="83b91-119">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="83b91-119">See Also</span></span>

[<span data-ttu-id="83b91-120">Bir Windows PowerShell ana bilgisayar uygulaması yazma</span><span class="sxs-lookup"><span data-stu-id="83b91-120">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)