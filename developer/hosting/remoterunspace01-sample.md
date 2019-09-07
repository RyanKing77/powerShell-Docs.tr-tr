---
title: RemoteRunspace01 örneği | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 302f00ef-e145-4668-a26a-03bc96ef4b8f
caps.latest.revision: 10
ms.openlocfilehash: 9cc6933858f4f37e4fa8b3bbe9afb69a73c68572
ms.sourcegitcommit: ffcc1c55f5b3adc063353cb75f2a2183acc2234a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70737572"
---
# <a name="remoterunspace01-sample"></a><span data-ttu-id="ddd77-102">RemoteRunspace01 Örneği</span><span class="sxs-lookup"><span data-stu-id="ddd77-102">RemoteRunspace01 Sample</span></span>

<span data-ttu-id="ddd77-103">Bu örnek, uzak bir bağlantı kurmak için kullanılan bir uzak çalışma alanının nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ddd77-103">This sample shows how to create a remote runspace that is used to establish a remote connection.</span></span>

## <a name="requirements"></a><span data-ttu-id="ddd77-104">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ddd77-104">Requirements</span></span>

 <span data-ttu-id="ddd77-105">Bu örnek, Windows PowerShell 2,0 gerektirir.</span><span class="sxs-lookup"><span data-stu-id="ddd77-105">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="ddd77-106">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="ddd77-106">Demonstrates</span></span>

- <span data-ttu-id="ddd77-107">[System. Management. Automation. Runspaces. Wsmanconnectionınfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) nesnesi oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="ddd77-107">Creating a [System.Management.Automation.Runspaces.Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) object.</span></span>

- <span data-ttu-id="ddd77-108">[System. Management. Automation. Runspaces. Runspaceconnectionınfo. OperationTimeout \*](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConnectionInfo.OperationTimeout) ve [System. Management. Automation. Runspaces. Runspaceconnectionınfo. OpenTimeout \*](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConnectionInfo.OpenTimeout) özelliklerinin [ayarlanması System. Management. Automation. Runspaces. Wsmanconnectionınfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) nesnesi.</span><span class="sxs-lookup"><span data-stu-id="ddd77-108">Setting the [System.Management.Automation.Runspaces.Runspaceconnectioninfo.Operationtimeout\*](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConnectionInfo.OperationTimeout) and [System.Management.Automation.Runspaces.Runspaceconnectioninfo.Opentimeout\*](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConnectionInfo.OpenTimeout) properties of the [System.Management.Automation.Runspaces.Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) object.</span></span>

- <span data-ttu-id="ddd77-109">Uzak bağlantı kurmak için [System. Management. Automation. Runspaces. Wsmanconnectionınfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) nesnesini kullanan bir uzak çalışma alanı oluşturma.</span><span class="sxs-lookup"><span data-stu-id="ddd77-109">Creating a remote runspace that uses the [System.Management.Automation.Runspaces.Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) object to establish the remote connection.</span></span>

- <span data-ttu-id="ddd77-110">Uzak çalışma alanı, uzak bağlantıyı serbest bırakmak için kapatılıyor.</span><span class="sxs-lookup"><span data-stu-id="ddd77-110">Closing the remote runspace to release the remote connection.</span></span>

## <a name="example"></a><span data-ttu-id="ddd77-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="ddd77-111">Example</span></span>

<span data-ttu-id="ddd77-112">Bu örnek, uzak bir bağlantı tanımlar ve bu bağlantı bilgilerini uzak bağlantı kurmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="ddd77-112">This sample defines a remote connection and then uses that connection information to establish a remote connection.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Management.Automation;             // Windows PowerShell namespace.
  using System.Management.Automation.Runspaces;   // Windows PowerShell namespace.

  /// <summary>
  /// This class contains the Main entry point for the application.
  /// </summary>
  internal class RemoteRunspace01
  {
    /// <summary>
    /// This sample shows how to use a WSManConnectionInfo object to set
    /// various timeouts and how to establish a remote connection.
    /// </summary>
    /// <param name="args">This parameter is not used.</param>
    public static void Main(string[] args)
    {
      // Create a WSManConnectionInfo object using the default constructor
      // to connect to the "localHost". The WSManConnectionInfo object can
      // also specify connections to remote computers.
      WSManConnectionInfo connectionInfo = new WSManConnectionInfo();

      // Set the OperationTimeout property. The OperationTimeout is used to tell
      // Windows PowerShell how long to wait (in milliseconds) before timing out
      // for any operation. This includes sending input data to the remote computer,
      // receiving output data from the remote computer, and more. The user can
      // change this timeout depending on whether the connection is to a computer
      // in the data center or across a slow WAN.
      connectionInfo.OperationTimeout = 4 * 60 * 1000; // 4 minutes.

      // Set the OpenTimeout property. OpenTimeout is used to tell Windows PowerShell
      // how long to wait (in milliseconds) before timing out while establishing a
      // remote connection. The user can change this timeout depending on whether the
      // connection is to a computer in the data center or across a slow WAN.
      connectionInfo.OpenTimeout = 1 * 60 * 1000; // 1 minute.

      // Create a remote runspace using the connection information.
      using (Runspace remoteRunspace = RunspaceFactory.CreateRunspace(connectionInfo))
      {
        // Establish the connection by calling the Open() method to open the runspace.
        // The OpenTimeout value set previously will be applied while establishing
        // the connection. Establishing a remote connection involves sending and
        // receiving some data, so the OperationTimeout will also play a role in this process.
        remoteRunspace.Open();

        // Add the code to run commands in the remote runspace here. The
        // OperationTimeout value set previously will play a role here because
        // running commands involves sending and receiving data.

        // Close the connection. Call the Close() method to close the remote
        // runspace. The Dispose() method (called by using primitive) will call
        // the Close() method if it is not already called.
        remoteRunspace.Close();
      }
    }
  }
}
```
