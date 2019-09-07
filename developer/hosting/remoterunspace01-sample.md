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
# <a name="remoterunspace01-sample"></a>RemoteRunspace01 Örneği

Bu örnek, uzak bir bağlantı kurmak için kullanılan bir uzak çalışma alanının nasıl oluşturulacağını gösterir.

## <a name="requirements"></a>Gereksinimler

 Bu örnek, Windows PowerShell 2,0 gerektirir.

## <a name="demonstrates"></a>Gösteriler

- [System. Management. Automation. Runspaces. Wsmanconnectionınfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) nesnesi oluşturuluyor.

- [System. Management. Automation. Runspaces. Runspaceconnectionınfo. OperationTimeout *](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConnectionInfo.OperationTimeout) ve [System. Management. Automation. Runspaces. Runspaceconnectionınfo. OpenTimeout *](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConnectionInfo.OpenTimeout) özelliklerinin [ayarlanması System. Management. Automation. Runspaces. Wsmanconnectionınfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) nesnesi.

- Uzak bağlantı kurmak için [System. Management. Automation. Runspaces. Wsmanconnectionınfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) nesnesini kullanan bir uzak çalışma alanı oluşturma.

- Uzak çalışma alanı, uzak bağlantıyı serbest bırakmak için kapatılıyor.

## <a name="example"></a>Örnek

Bu örnek, uzak bir bağlantı tanımlar ve bu bağlantı bilgilerini uzak bağlantı kurmak için kullanır.

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
