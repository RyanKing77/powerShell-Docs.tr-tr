---
title: StopProcessSample02 örnek | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 213ca1a4-e9fe-4969-b7d0-2fca070c6142
caps.latest.revision: 10
ms.openlocfilehash: 594c06367baedd1f9bfdbfff9f0e072d579b4099
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057239"
---
# <a name="stopprocesssample02-sample"></a><span data-ttu-id="9e470-102">StopProcessSample02 Örneği</span><span class="sxs-lookup"><span data-stu-id="9e470-102">StopProcessSample02 Sample</span></span>

<span data-ttu-id="9e470-103">Bu örnek, yerel bilgisayarda işlem durdurulurken hata ayıklama (WriteDebug), ayrıntılı (WriteVerbose) ve (WriteWarning) uyarı iletilerini yazan bir cmdlet yazma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9e470-103">This sample shows how to write a cmdlet that writes debug (WriteDebug), verbose (WriteVerbose), and warning (WriteWarning) messages while stopping processes on the local computer.</span></span> <span data-ttu-id="9e470-104">Bu cmdlet benzer `Stop-Process` Windows PowerShell 2.0 tarafından sağlanan cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="9e470-104">This cmdlet is similar to the `Stop-Process` cmdlet provided by Windows PowerShell 2.0.</span></span>

### <a name="how-to-build-the-sample-by-using-visual-studio"></a><span data-ttu-id="9e470-105">Visual Studio kullanarak örneği oluşturmak nasıl.</span><span class="sxs-lookup"><span data-stu-id="9e470-105">How to build the sample by using Visual Studio.</span></span>

1. <span data-ttu-id="9e470-106">Windows Internet Explorer'ı açın ve örnekler dizini altında StopProcessSample02 dizinine gidin.</span><span class="sxs-lookup"><span data-stu-id="9e470-106">Open Windows Internet Explorer and navigate to the StopProcessSample02 directory under the Samples directory.</span></span>

    <span data-ttu-id="9e470-107">Windows PowerShell 2.0 yüklü SDK ile StopProcessSample02 klasöre gidin.</span><span class="sxs-lookup"><span data-stu-id="9e470-107">With the Windows PowerShell 2.0 SDK installed, navigate to the StopProcessSample02 folder.</span></span> <span data-ttu-id="9e470-108">C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\StopProcessSample02 varsayılan konumdur.</span><span class="sxs-lookup"><span data-stu-id="9e470-108">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\StopProcessSample02.</span></span>

2. <span data-ttu-id="9e470-109">Çözüm (.sln) dosyasını simgesini çift tıklatın.</span><span class="sxs-lookup"><span data-stu-id="9e470-109">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="9e470-110">Bu örnek projeyi Microsoft Visual Studio'da açılır.</span><span class="sxs-lookup"><span data-stu-id="9e470-110">This opens the sample project in Microsoft Visual Studio.</span></span>

3. <span data-ttu-id="9e470-111">İçinde **derleme** menüsünde **Çözümü Derle**.</span><span class="sxs-lookup"><span data-stu-id="9e470-111">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="9e470-112">Kitaplık için örneği varsayılan \bin veya \bin\debug'dır klasörleri oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9e470-112">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="9e470-113">Örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="9e470-113">How to run the sample</span></span>

1. <span data-ttu-id="9e470-114">Aşağıdaki modül klasörü oluşturun:</span><span class="sxs-lookup"><span data-stu-id="9e470-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/StopProcessSample02`

2. <span data-ttu-id="9e470-115">Örnek derleme modülü klasöre kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="9e470-115">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="9e470-116">Windows PowerShell’i başlatın.</span><span class="sxs-lookup"><span data-stu-id="9e470-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="9e470-117">Windows PowerShell içinde derlemesini yüklemek için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="9e470-117">Run the following command to load the assembly into Windows PowerShell:</span></span>

    `import-module stopprossessample02`

5. <span data-ttu-id="9e470-118">Cmdlet'i çalıştırmak için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="9e470-118">Run the following command to run the cmdlet:</span></span>

    `stop-proc`

## <a name="requirements"></a><span data-ttu-id="9e470-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9e470-119">Requirements</span></span>

<span data-ttu-id="9e470-120">Bu örnek, Windows PowerShell 2.0 gerektirir.</span><span class="sxs-lookup"><span data-stu-id="9e470-120">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="9e470-121">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="9e470-121">Demonstrates</span></span>

<span data-ttu-id="9e470-122">Bu örnek aşağıdaki gösterir.</span><span class="sxs-lookup"><span data-stu-id="9e470-122">This sample demonstrates the following.</span></span>

- <span data-ttu-id="9e470-123">Cmdlet özniteliğini kullanarak bir cmdlet'i sınıf bildirme.</span><span class="sxs-lookup"><span data-stu-id="9e470-123">Declaring a cmdlet class by using the Cmdlet attribute.</span></span>

- <span data-ttu-id="9e470-124">Bir cmdlet parametreleri parametre özniteliği kullanılarak bildirme.</span><span class="sxs-lookup"><span data-stu-id="9e470-124">Declaring a cmdlet parameters by using the Parameter attribute.</span></span>

- <span data-ttu-id="9e470-125">Ayrıntılı iletileri yazma.</span><span class="sxs-lookup"><span data-stu-id="9e470-125">Writing verbose messages.</span></span> <span data-ttu-id="9e470-126">Ayrıntılı iletileri yazmak için kullanılan yöntemi hakkında daha fazla bilgi için bkz. [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose).</span><span class="sxs-lookup"><span data-stu-id="9e470-126">For more information about the method used to write verbose messages, see [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose).</span></span>

- <span data-ttu-id="9e470-127">Hata iletileri yazma.</span><span class="sxs-lookup"><span data-stu-id="9e470-127">Writing error messages.</span></span> <span data-ttu-id="9e470-128">Hata iletisi yazmak için kullanılan yöntemi hakkında daha fazla bilgi için bkz. [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError).</span><span class="sxs-lookup"><span data-stu-id="9e470-128">For more information about the method used to write error messages, see [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError).</span></span>

- <span data-ttu-id="9e470-129">Yazma uyarı iletileri.</span><span class="sxs-lookup"><span data-stu-id="9e470-129">Writing warning messages.</span></span> <span data-ttu-id="9e470-130">Uyarı iletisi yazmak için kullanılan yöntemi hakkında daha fazla bilgi için bkz. [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning).</span><span class="sxs-lookup"><span data-stu-id="9e470-130">For more information about the method used to write warning messages, see [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning).</span></span>

## <a name="example"></a><span data-ttu-id="9e470-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="9e470-131">Example</span></span>

<span data-ttu-id="9e470-132">Bu örnek, hata ayıklama, ayrıntılı ve uyarı iletileri kullanarak yazma işlemi gösterilmektedir `WriteDebug`, `WriteVerbose`, ve `WriteWarning` yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="9e470-132">This sample shows how to write debug, verbose, and warning messages by using the `WriteDebug`, `WriteVerbose`, and `WriteWarning` methods.</span></span>

```csharp
using System;
using System.Diagnostics;
using System.Collections;
using Win32Exception = System.ComponentModel.Win32Exception;
using System.Management.Automation;             //Windows PowerShell namespace
using System.Globalization;

namespace Microsoft.Samples.PowerShell.Commands
{
   #region StopProcCommand

    /// <summary>
   /// This class implements the stop-proc cmdlet.
   /// </summary>
   [Cmdlet(VerbsLifecycle.Stop, "Proc",
       SupportsShouldProcess = true)]
   public class StopProcCommand : Cmdlet
   {
       #region Parameters

      /// <summary>
      /// This parameter provides the list of process names on
      /// which the Stop-Proc cmdlet will work.
      /// </summary>
       [Parameter(
          Position = 0,
          Mandatory = true,
          ValueFromPipeline = true,
          ValueFromPipelineByPropertyName = true
       )]
       public string[] Name
       {
          get { return processNames; }
          set { processNames = value; }
       }
       private string[] processNames;

       /// <summary>
       /// This parameter overrides the ShouldContinue call to force
       /// the cmdlet to stop its operation. This parameter should always
       /// be used with caution.
       /// </summary>
       [Parameter]
       public SwitchParameter Force
       {
           get { return force; }
           set { force = value; }
       }
       private bool force;

       /// <summary>
       /// This parameter indicates that the cmdlet should return
       /// an object to the pipeline after the processing has been
       /// completed.
       /// </summary>
       [Parameter]
       public SwitchParameter PassThru
       {
           get { return passThru; }
           set { passThru = value; }
       }
       private bool passThru;

       #endregion Parameters

       #region Cmdlet Overrides

       /// <summary>
       /// The ProcessRecord method does the following for each of the
       /// requested process names:
       /// 1) Check that the process is not a critical process.
       /// 2) Attempt to stop that process.
       /// If no process is requested then nothing occurs.
       /// </summary>
       protected override void ProcessRecord()
       {
           foreach (string name in processNames)
           {
               string message = null;

               // For every process name passed to the cmdlet, get the associated
               // processes.
               // Write a nonterminating error for failure to retrieve
               // a process.

               // Write a user-friendly verbose message to the pipeline. These
               // messages are intended to give the user detailed information
               // on the operations performed by the cmdlet. These messages will
               // appear with the -Verbose option.
               message = String.Format(CultureInfo.CurrentCulture,
                              "Attempting to stop process \"{0}\".", name);
               WriteVerbose(message);

               Process[] processes;

               try
               {
                   processes = Process.GetProcessesByName(name);
               }
               catch (InvalidOperationException ioe)
               {
                   WriteError(new ErrorRecord(ioe,
                                     "UnableToAccessProcessByName",
                                         ErrorCategory.InvalidOperation,
                                             name));
                   continue;
               }

               // Try to stop the processes that have been retrieved.
               foreach (Process process in processes)
               {
                   string processName;

                   try
                   {
                       processName = process.ProcessName;
                   }
                   catch (Win32Exception e)
                   {
                       WriteError(new ErrorRecord(e, "ProcessNameNotFound",
                                         ErrorCategory.ObjectNotFound, process));
                       continue;
                   }

                   // Write a debug message to the host that can be used when
                   // troubleshooting a problem. All debug messages will appear
                   // with the -Debug option.
                   message = String.Format(CultureInfo.CurrentCulture,
                                 "Acquired name for pid {0} : \"{1}\"",
                                        process.Id, processName);
                   WriteDebug(message);

                   // Confirm the operation first.
                   // This is always false if the WhatIf parameter is specified.
                   if (!ShouldProcess(string.Format(CultureInfo.CurrentCulture,
                                        "{0} ({1})",
                                            processName, process.Id)))
                   {
                       continue;
                   }

                   // Make sure that the user really wants to stop a critical
                   // process that can possibly stop the computer.
                   bool criticalProcess = criticalProcessNames.Contains(processName.ToLower(CultureInfo.CurrentCulture));

                   if (criticalProcess && !force)
                   {
                       message = String.Format(CultureInfo.CurrentCulture,
                                    "The process \"{0}\" is a critical process and should not be stopped. Are you sure you wish to stop the process?",
                                        processName);

                       // It is possible that the ProcessRecord method is called
                       // multiple times when objects are received as inputs from
                       // the pipeline. So to retain YesToAll and NoToAll input that
                       // the user may enter across multiple calls to this function,
                       // they are stored as private members of the cmdlet.
                       if (!ShouldContinue(message, "Warning!",
                                    ref yesToAll, ref noToAll))
                       {
                           continue;
                       }
                   } // if (criticalProcess...

                   // Display a warning message if the cmdlet is stopping a
                   // critical process.
                   if (criticalProcess)
                   {
                       message = String.Format(CultureInfo.CurrentCulture,
                                     "Stopping the critical process \"{0}\".",
                                          processName);
                       WriteWarning(message);
                   } // if (criticalProcess...

                   // Stop the named process.
                   try
                   {
                       process.Kill();
                   }
                   catch (Exception e)
                   {
                       if ((e is Win32Exception) || (e is SystemException) ||
                           (e is InvalidOperationException))
                       {
                           // This process could not be stopped so write
                           // a nonterminating error.
                           WriteError(new ErrorRecord(
                                            e,
                                            "CouldNotStopProcess",
                                            ErrorCategory.CloseError,
                                            process)
                                      );
                           continue;
                       } // if ((e is...
                           else throw;
                   } // catch

                   message = String.Format(CultureInfo.CurrentCulture,
                                  "Stopped process \"{0}\", pid {1}.",
                                        processName, process.Id);

                   WriteVerbose(message);

                   // If the PassThru parameter is specified,
                   // return the terminated process object to the pipeline.
                   if (passThru)
                   {
                       message = String.Format(CultureInfo.CurrentCulture,
                                     "Writing process \"{0}\" to pipeline",
                                          processName);
                       WriteDebug(message);
                       WriteObject(process);
                   } // if (passThru...
               } // foreach (Process...
            } // foreach (string...
        } // ProcessRecord

       #endregion Cmdlet Overrides

       #region Private Data

       private bool yesToAll, noToAll;

       /// <summary>
       /// Partial list of critical processes that should not be
       /// stopped.  Lower case is used for case insensitive matching.
       /// </summary>
       private ArrayList criticalProcessNames = new ArrayList(
          new string[] { "system", "winlogon", "spoolsv" }
       );

       #endregion Private Data

   } // StopProcCommand

   #endregion StopProcCommand
}
```

## <a name="see-also"></a><span data-ttu-id="9e470-133">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="9e470-133">See Also</span></span>

[<span data-ttu-id="9e470-134">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="9e470-134">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
