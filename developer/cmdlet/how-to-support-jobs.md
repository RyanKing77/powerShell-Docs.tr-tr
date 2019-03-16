---
title: İşleri desteklemek nasıl | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5eac452c-eae2-4193-b4da-0b618bef3677
caps.latest.revision: 9
ms.openlocfilehash: d732bce1af446090c3e5741eebeba737f86c7ca8
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058020"
---
# <a name="how-to-support-jobs"></a><span data-ttu-id="3731d-102">İşleri Destekleme</span><span class="sxs-lookup"><span data-stu-id="3731d-102">How to Support Jobs</span></span>

<span data-ttu-id="3731d-103">Bu örnek cmdlet yazdığınızda işleri desteklemek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="3731d-103">This example shows how to support jobs when you write cmdlets.</span></span> <span data-ttu-id="3731d-104">Kullanıcıların, cmdlet'i bir arka plan işi çalıştırmak istiyorsanız, aşağıdaki yordamda açıklanan kodu içermesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="3731d-104">If you want users to run your cmdlet as a background job, you must include the code described in the following procedure.</span></span> <span data-ttu-id="3731d-105">Arka plan işleri hakkında daha fazla bilgi için bkz: [arka plan işleri](./background-jobs.md).</span><span class="sxs-lookup"><span data-stu-id="3731d-105">For more information about background jobs, see [Background Jobs](./background-jobs.md).</span></span>

## <a name="to-support-jobs"></a><span data-ttu-id="3731d-106">İşleri desteklemek için</span><span class="sxs-lookup"><span data-stu-id="3731d-106">To support jobs</span></span>

1. <span data-ttu-id="3731d-107">Tanımlayan bir `AsJob` kullanıcı cmdlet'i bir iş olarak çalıştırmak karar verebilir böylece parametresi geçin.</span><span class="sxs-lookup"><span data-stu-id="3731d-107">Define an `AsJob` switch parameter so that the user can decide whether to run the cmdlet as a job.</span></span>

    <span data-ttu-id="3731d-108">Aşağıdaki örnek, bir AsJob parametresi bildirimi gösterir.</span><span class="sxs-lookup"><span data-stu-id="3731d-108">The following example shows an AsJob parameter declaration.</span></span>

    ```csharp
    [Parameter()]
    public SwitchParameter AsJob
    {
      get { return asjob; }
      set { asjob = value; }
    }
    private bool asjob;
    ```

    <!-- TODO!!!: review snippet reference      [!CODE [msh_samplesGetProc06#GetProc06AsJobParam](msh_samplesGetProc06#GetProc06AsJobParam)]  -->

2. <span data-ttu-id="3731d-109">Türetilen bir nesne oluşturma [System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="3731d-109">Create an object that derives from the [System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) class.</span></span> <span data-ttu-id="3731d-110">Bu nesne bir özel iş nesnesi veya bir Windows PowerShell tarafından sağlanan iş nesneler olabilir. Bu tür bir [System.Management.Automation.Pseventjob](/dotnet/api/System.Management.Automation.PSEventJob) nesne.</span><span class="sxs-lookup"><span data-stu-id="3731d-110">This object can be a custom job object or one of the job objects provided by Windows PowerShell, such a [System.Management.Automation.Pseventjob](/dotnet/api/System.Management.Automation.PSEventJob) object.</span></span>

    <span data-ttu-id="3731d-111">Aşağıdaki örnek, bir özel iş nesnesi gösterir.</span><span class="sxs-lookup"><span data-stu-id="3731d-111">The following example shows a custom job object.</span></span>

    ```csharp
    private SampleJob job = new SampleJob("Get-ProcAsJob");
    ```

    <!-- TODO!!!: review snippet reference      [!CODE [msh_samplesGetProc06#GetProc06JobObject](msh_samplesGetProc06#GetProc06JobObject)]  -->

3. <span data-ttu-id="3731d-112">Bir kayıt işleme yöntemine ekleyin bir `if` cmdlet'i bir iş olarak çalıştırılıp çalıştırılmayacağını algılamak için deyimi.</span><span class="sxs-lookup"><span data-stu-id="3731d-112">In a record processing method, add an `if` statement to detect whether the cmdlet should run as a job.</span></span> <span data-ttu-id="3731d-113">Aşağıdaki kod [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3731d-113">The following code uses the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

    ```csharp
    protected override void ProcessRecord()
    {
      if (asjob)
      {
        // Add the job definition to the job repository,
        // return the job object, and then create the thread
        // used to run the job.
        JobRepository.Add(job);
        WriteObject(job);
        ThreadPool.QueueUserWorkItem(WorkItem);
      }
      else
      {
        job.ProcessJob();
        foreach (PSObject p in job.Output)
        {
          WriteObject(p);
        }
      }
    }
    ```

    <!-- TODO!!!: review snippet reference      [!CODE [msh_samplesGetProc06#GetProc06ProcessRecord](msh_samplesGetProc06#GetProc06ProcessRecord)]  -->

4. <span data-ttu-id="3731d-114">Özel iş nesneler için iş sınıfı uygulayın.</span><span class="sxs-lookup"><span data-stu-id="3731d-114">For custom job objects, implement the job class.</span></span>

    ```csharp
    private class SampleJob : Job
    {
      internal SampleJob(string command)
          : base(command)
      {
        SetJobState(JobState.NotStarted);
      }
      public override string StatusMessage
      {
        get { throw new NotImplementedException(); }
      }

      public override bool HasMoreData
      {
        get
        {
          return hasMoreData;
        }
      }
      private bool hasMoreData = true;

      public override string Location
      {
        get { throw new NotImplementedException(); }
      }

      public override void StopJob()
      {
        throw new NotImplementedException();
      }

      internal void ProcessJob()
      {
        SetJobState(JobState.Running);
        DoProcessLogic();
        SetJobState(JobState.Completed);
      }

      // Retrieve the processes of the local computer.
      void DoProcessLogic()
      {
        Process[] p = Process.GetProcesses();

        foreach (Process pl in p)
        {
          Output.Add(PSObject.AsPSObject(pl));
        }
        Output.Complete();
      } // End DoProcessLogic.
    } // End SampleJob class.
    ```

    <!-- TODO!!!: review snippet reference      [!CODE [msh_samplesGetProc06#GetProc06JobClass](msh_samplesGetProc06#GetProc06JobClass)]  -->

5. <span data-ttu-id="3731d-115">Cmdlet'i iş gerçekleştiriyorsa, çağrı [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) ardışık düzene bir işlem nesnesi döndürmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3731d-115">If the cmdlet performs the work, call the [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) method to return a process object to the pipeline.</span></span> <span data-ttu-id="3731d-116">İş bir iş olarak gerçekleştirilirse, alt iş projeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3731d-116">If the work is performed as a job, add child job to the job.</span></span>

    ```csharp
    void DoProcessLogic(bool asJob)
    {
      Process[] p = Process.GetProcesses();

      foreach (Process pl in p)
      {
        if (!asjob)
        {
          WriteObject(pl);
        }
        else
        {
          job.ChildJobs[0].Output.Add(new PSObject(pl));
        }
      }
    } // End DoProcessLogic.
    ```

    <!-- TODO!!!: review snippet reference      [!CODE [msh_samplesGetProc06#GetProc06Output](msh_samplesGetProc06#GetProc06Output)]  -->

## <a name="example"></a><span data-ttu-id="3731d-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="3731d-117">Example</span></span>

<span data-ttu-id="3731d-118">Aşağıdaki örnek kod için kod gösterir bir **Get-Proc** işlemleri dahili olarak veya bir arka plan işi kullanarak alabileceğiniz cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="3731d-118">The following sample code shows the code for a **Get-Proc** cmdlet that can retrieve processes internally or by using a background job.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;  // Windows PowerShell namespace.
using System.Threading;              // Thread pool namespace for posting work.
using System.Diagnostics;            // Diagnostics namespace for retrieving
                                     // process objects.

// This sample shows a cmdlet whose work can be done by the cmdlet or by using
// a background job. Background jobs are executed in their own thread,
// independent of the pipeline thread in which the cmdlet is executed.
//
// To load this cmdlet, create a module folder and copy the GetProcessSample06.dll
// assembly into the module folder. Make sure that the path to the module folder
// is added to the $PSModulePath environment variable.
// Module folder path:
//    user/documents/WindowsPowerShell/modules/GetProcessSample06
//
// To import the module, run the following command: Import-Module GetProcessSample06.
// To test the cmdlet, run the following command: Get-Proc -name <process name>
//

//
namespace Microsoft.Samples.PowerShell.Commands
{
  /// <summary>
  ///  This cmdlet retrieves process internally or returns
  ///  a job that retrieves the processes.
  /// </summary>
  [Cmdlet(VerbsCommon.Get, "Proc")]
  public sealed class GetProcCommand : PSCmdlet
  {

    #region Parameters
    /// <summary>
    /// Specify the Name parameter. This parameter accepts
    /// process names from the command line.
    /// </summary>
    [Parameter(
               Position = 0,
               ValueFromPipeline = true,
               ValueFromPipelineByPropertyName = true)]
    [ValidateNotNullOrEmpty]
    public string[] Name
    {
      get { return processNames; }
      set { processNames = value; }
    }
    private string[] processNames;

    /// <summary>
    /// Specify the AsJob parameter. This parameter indicates
    /// whether the cmdlet should retrieve the processes internally
    /// or return a Job object that retrieves the processes.
    [Parameter()]
    public SwitchParameter AsJob
    {
      get { return asjob; }
      set { asjob = value; }
    }
    private bool asjob;

    #endregion Parameters

    #region Cmdlet Overrides

    // Create a custom job object.
    private SampleJob job = new SampleJob("Get-ProcAsJob");

    /// <summary>
    /// Determines if the processes should be retrieved
    /// internally or if a Job object should be returned.
    /// </summary>
    protected override void ProcessRecord()
    {
      if (asjob)
      {
        // Add the job definition to the job repository,
        // return the job object, and then create the thread
        // used to run the job.
        JobRepository.Add(job);
        WriteObject(job);
        ThreadPool.QueueUserWorkItem(WorkItem);
      }
      else
      {
        job.ProcessJob();
        foreach (PSObject p in job.Output)
        {
          WriteObject(p);
        }
      }
    }
    #endregion Overrides

    // Implement a custom job that derives
    // from the System.Management.Automation.Job class.
    private class SampleJob : Job
    {
      internal SampleJob(string command)
          : base(command)
      {
        SetJobState(JobState.NotStarted);
      }
      public override string StatusMessage
      {
        get { throw new NotImplementedException(); }
      }

      public override bool HasMoreData
      {
        get
        {
          return hasMoreData;
        }
      }
      private bool hasMoreData = true;

      public override string Location
      {
        get { throw new NotImplementedException(); }
      }

      public override void StopJob()
      {
        throw new NotImplementedException();
      }

      internal void ProcessJob()
      {
        SetJobState(JobState.Running);
        DoProcessLogic();
        SetJobState(JobState.Completed);
      }

      // Retrieve the processes of the local computer.
      void DoProcessLogic()
      {
        Process[] p = Process.GetProcesses();

        foreach (Process pl in p)
        {
          Output.Add(PSObject.AsPSObject(pl));
        }
        Output.Complete();
      } // End DoProcessLogic.
    } // End SampleJob class.

    void WorkItem(object dummy)
    {
       job.ProcessJob();
    }

    // Display the results of the work. If not a job,
    // process objects are returned. If a job, the
    // output is added to the job as a child job.
    void DoProcessLogic(bool asJob)
    {
      Process[] p = Process.GetProcesses();

      foreach (Process pl in p)
      {
        if (!asjob)
        {
          WriteObject(pl);
        }
        else
        {
          job.ChildJobs[0].Output.Add(new PSObject(pl));
        }
      }
    } // End DoProcessLogic.
  } //End GetProcCommand
}    void DoProcessLogic(bool asJob)
    {
      Process[] p = Process.GetProcesses();

      foreach (Process pl in p)
      {
        if (!asjob)
        {
          WriteObject(pl);
        }
        else
        {
          job.ChildJobs[0].Output.Add(new PSObject(pl));
        }
      }
    } // End DoProcessLogic.
```

<!-- TODO!!!: review snippet reference  [!CODE [msh_samplesGetProc06#GetProc06All](msh_samplesGetProc06#GetProc06All)]  -->
