---
title: Uzak çalışma alanları oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 057a666f-731b-423d-9d80-7be6b1836244
caps.latest.revision: 5
ms.openlocfilehash: f6cc69df8afe64cea867f5d7f9a7d45753a54d6f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082983"
---
# <a name="creating-remote-runspaces"></a><span data-ttu-id="cc4b8-102">Uzak çalışma alanları oluşturma</span><span class="sxs-lookup"><span data-stu-id="cc4b8-102">Creating remote runspaces</span></span>

<span data-ttu-id="cc4b8-103">Windows PowerShell komutlarını süren bir `ComputerName` parametresi Windows PowerShell çalıştıran herhangi bir bilgisayarda çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="cc4b8-103">Windows PowerShell commands that take a `ComputerName` parameter can be run on any computer that runs Windows PowerShell.</span></span> <span data-ttu-id="cc4b8-104">Almaz komutlarını çalıştırmak için bir `ComputerName` parametresi, WS-Management belirtilen bilgisayara bağlayan bir çalışma alanı yapılandırmak için vb. Bu bilgisayarda komutları çalıştırmak.</span><span class="sxs-lookup"><span data-stu-id="cc4b8-104">To run commands that do not take a `ComputerName` parameter, you can use WS-Management to configure a runspace that connects to a specified computer, and run commands on that computer.</span></span>

## <a name="using-a-wsmanconnection-to-create-a-remote-runspace"></a><span data-ttu-id="cc4b8-105">Bir uzak çalışma alanı oluşturmak için bir WSManConnection kullanma</span><span class="sxs-lookup"><span data-stu-id="cc4b8-105">Using a WSManConnection to create a remote runspace</span></span>

 <span data-ttu-id="cc4b8-106">Uzak bilgisayara bağlayan bir çalışma alanı oluşturmak için oluşturduğunuz bir [System.Management.Automation.Runspaces.Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) nesne.</span><span class="sxs-lookup"><span data-stu-id="cc4b8-106">To create a runspace that connects to a remote computer, you create a [System.Management.Automation.Runspaces.Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) object.</span></span> <span data-ttu-id="cc4b8-107">Ayarlayarak hedef uç nokta bağlantısı için belirttiğiniz [System.Management.Automation.Runspaces.Wsmanconnectioninfo.Connectionuri\*](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo.ConnectionUri) nesnesinin özelliği.</span><span class="sxs-lookup"><span data-stu-id="cc4b8-107">You specify the target endpoint for the connection by setting the [System.Management.Automation.Runspaces.Wsmanconnectioninfo.Connectionuri\*](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo.ConnectionUri) property of the object.</span></span> <span data-ttu-id="cc4b8-108">Ardından çağırarak bir çalışma alanı oluşturma [System.Management.Automation.Runspaces.Runspacefactory.Createrunspace\*](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory.CreateRunspace) yöntemi belirtme [System.Management.Automation.Runspaces.Wsmanconnectioninfo ](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) nesnesinin `connectionInfo` parametresi.</span><span class="sxs-lookup"><span data-stu-id="cc4b8-108">You then create a runspace by calling the [System.Management.Automation.Runspaces.Runspacefactory.Createrunspace\*](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory.CreateRunspace) method, specifying the [System.Management.Automation.Runspaces.Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) object as the `connectionInfo` parameter.</span></span>

 <span data-ttu-id="cc4b8-109">Aşağıdaki örnek, bir uzak bilgisayara bağlanan bir çalışma alanı oluşturma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="cc4b8-109">The following example shows how to create a runspace that connects to a remote computer.</span></span> <span data-ttu-id="cc4b8-110">Örnekte, `RemoteComputerUri` gerçek bir uzak bilgisayar URI'si için bir yer tutucu olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cc4b8-110">In the example, `RemoteComputerUri` is used as a placeholder for the actual URI of a remote computer.</span></span>

```csharp
namespace Samples
{
  using System;
  using System.Collections.ObjectModel;
  using System.Management.Automation;            // Windows PowerShell namespace.
  using System.Management.Automation.Runspaces;  // Windows PowerShell namespace.

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class RemoteRunspace02
  {
    /// <summary>
    /// This sample shows how to create a remote runspace that
    /// runs commands on the local computer.
    /// </summary>
    /// <param name="args">Parameter not used.</param>
    private static void Main(string[] args)
    {
      // Create a WSManConnectionInfo object using the default constructor
      // to connect to the "localHost". The WSManConnectionInfo object can
      // also be used to specify connections to remote computers.
      WSManConnectionInfo connectionInfo = new WSManConnectionInfo();

      // Set the OperationTimeout property and OpenTimeout properties.
      // The OperationTimeout property is used to tell Windows PowerShell
      // how long to wait (in milliseconds) before timing out for an
      // operation. The OpenTimeout property is used to tell Windows
      // PowerShell how long to wait (in milliseconds) before timing out
      // while establishing a remote connection.
      connectionInfo.OperationTimeout = 4 * 60 * 1000; // 4 minutes.
      connectionInfo.OpenTimeout = 1 * 60 * 1000; // 1 minute.

      // Create a remote runspace using the connection information.
      //using (Runspace remoteRunspace = RunspaceFactory.CreateRunspace())
      using (Runspace remoteRunspace = RunspaceFactory.CreateRunspace(connectionInfo))
      {
        // Establish the connection by calling the Open() method to open the runspace.
        // The OpenTimeout value set previously will be applied while establishing
        // the connection. Establishing a remote connection involves sending and
        // receiving some data, so the OperationTimeout will also play a role in this process.
          remoteRunspace.Open();

        // Create a PowerShell object to run commands in the remote runspace.
        using (PowerShell powershell = PowerShell.Create())
        {
          powershell.Runspace = remoteRunspace;
          powershell.AddCommand("get-process");
          powershell.Invoke();

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

        // Close the connection. Call the Close() method to close the remote
        // runspace. The Dispose() method (called by using primitive) will call
        // the Close() method if it is not already called.
        remoteRunspace.Close();
      }
    }
  }
}
```
