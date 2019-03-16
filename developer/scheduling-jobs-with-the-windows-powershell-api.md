---
title: Windows PowerShell API’si ile İşleri Zamanlama
ms.date: 09/13/2016
ms.topic: article
ms.openlocfilehash: 4e1d4ed6bffd858b92bf29b1dc6d8503454fafda
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057493"
---
# <a name="scheduling-jobs-with-the-windows-powershell-api"></a><span data-ttu-id="216ad-102">Windows PowerShell API’si ile İşleri Zamanlama</span><span class="sxs-lookup"><span data-stu-id="216ad-102">Scheduling Jobs with the Windows PowerShell API</span></span>

<span data-ttu-id="216ad-103">N:Microsoft.PowerShell.ScheduledJob ad alanı tarafından kullanıma sunulan nesneleri, zamanlanmış bir iş oluşturma, çalışırken tanımlayın ve çalıştıktan sonra tamamlanan işle ilgili sonuçları almak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="216ad-103">You can use the objects exposed by the N:Microsoft.PowerShell.ScheduledJob namespace to create a scheduled job, define when it runs, and get results about the completed job after it has run.</span></span>

## <a name="triggering-the-job"></a><span data-ttu-id="216ad-104">İş tetikleme</span><span class="sxs-lookup"><span data-stu-id="216ad-104">Triggering the Job</span></span>

<span data-ttu-id="216ad-105">Zamanlanmış bir iş oluşturmanın ilk adımı, işin çalışması gereken zamanla belirtilmesidir.</span><span class="sxs-lookup"><span data-stu-id="216ad-105">The first step in creating a scheduled job is specifying when the job should run.</span></span> <span data-ttu-id="216ad-106">Bunu yapmak, oluşturma ve yapılandırma T:Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger nesne.</span><span class="sxs-lookup"><span data-stu-id="216ad-106">Do this by creating and configuring a T:Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger object.</span></span> <span data-ttu-id="216ad-107">Aşağıdaki kod, tek bir kez 20 saniye sonra çalıştırılacak bir iş zamanlamaları bir tetikleyici oluşturur.</span><span class="sxs-lookup"><span data-stu-id="216ad-107">The following code creates a trigger that schedules a job to run a single time 20 seconds in the future.</span></span>

```csharp
ScheduledJobTrigger jobTrigger = ScheduledJobTrigger.CreateOnceTrigger(
    DateTime.Now.AddSeconds(20),        // Create trigger to start job 20 seconds after now.
    TimeSpan.Zero,                      // No random delay
    null,                               // No repetition interval time
    null,                               // No repetition interval duration
    1,                                  // Trigger Id
    true);                              // Create trigger enabled
```

## <a name="defining-the-job"></a><span data-ttu-id="216ad-108">İş tanımlama</span><span class="sxs-lookup"><span data-stu-id="216ad-108">Defining the Job</span></span>

<span data-ttu-id="216ad-109">Bir Windows PowerShell iş, bir parametre sözlüğünü oluşturarak tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="216ad-109">You define a Windows PowerShell job by creating a parameter dictionary.</span></span> <span data-ttu-id="216ad-110">Şu parametreler desteklenir.</span><span class="sxs-lookup"><span data-stu-id="216ad-110">The following parameters are supported.</span></span>

|<span data-ttu-id="216ad-111">Parametre adı</span><span class="sxs-lookup"><span data-stu-id="216ad-111">Parameter Name</span></span>|<span data-ttu-id="216ad-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="216ad-112">Description</span></span>|
|---|---|
|<span data-ttu-id="216ad-113">Adı</span><span class="sxs-lookup"><span data-stu-id="216ad-113">Name</span></span>|<span data-ttu-id="216ad-114">İş adı.</span><span class="sxs-lookup"><span data-stu-id="216ad-114">The name of the job.</span></span>|
|<span data-ttu-id="216ad-115">ScriptBock</span><span class="sxs-lookup"><span data-stu-id="216ad-115">ScriptBock</span></span>|<span data-ttu-id="216ad-116">İşin ne yaptığını belirten bir Windows PowerShell komut dosyası bloğu.</span><span class="sxs-lookup"><span data-stu-id="216ad-116">A Windows PowerShell script block that specifies what the job does.</span></span>|
|<span data-ttu-id="216ad-117">FilePath</span><span class="sxs-lookup"><span data-stu-id="216ad-117">FilePath</span></span>|<span data-ttu-id="216ad-118">Bir işin ne yaptığını belirten bir Windows PowerShell komut dosyası bloğu içeren dosyanın yolu.</span><span class="sxs-lookup"><span data-stu-id="216ad-118">A path to a file that contains Windows PowerShell script block that specifies what the job does.</span></span>|
|<span data-ttu-id="216ad-119">InitializationScript</span><span class="sxs-lookup"><span data-stu-id="216ad-119">InitializationScript</span></span>|<span data-ttu-id="216ad-120">İşi başlatan bir Windows PowerShell komut dosyası bloğu.</span><span class="sxs-lookup"><span data-stu-id="216ad-120">A Windows PowerShell script block that initializes the job.</span></span>|
|<span data-ttu-id="216ad-121">ArgumentList</span><span class="sxs-lookup"><span data-stu-id="216ad-121">ArgumentList</span></span>|<span data-ttu-id="216ad-122">Proje alan bağımsız değişkenlerini belirtin nesneleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="216ad-122">An array of objects that specify arguments that the job takes.</span></span>|
|<span data-ttu-id="216ad-123">RunAs32</span><span class="sxs-lookup"><span data-stu-id="216ad-123">RunAs32</span></span>|<span data-ttu-id="216ad-124">İş bir 32 bit işlemde çalıştırılıp çalıştırılmayacağını belirleyen bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="216ad-124">A boolean value that specifies whether to run the job in a 32-bit process.</span></span>|

<span data-ttu-id="216ad-125">Aşağıdaki kod, bir parametre sözlük nesnesi oluşturur ve ad hem de ScriptBlock parametreleri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="216ad-125">The following code creates a parameter dictionary object and sets the Name and ScriptBlock parameters.</span></span>

```csharp
string schedJobDefName = "MySampleSchedJob";
Dictionary<string, object> jobDefParameters = new Dictionary<string, object>();
jobDefParameters.Add("Name", schedJobDefName);      // Unique name is required.

ScriptBlock scriptBlock = ScriptBlock.Create(@"1..5 | foreach {sleep 1; ""SchedJobOutput $_""}");
jobDefParameters.Add("ScriptBlock", scriptBlock);  // A scriptblock or script FilePath
                                                   // is required.
```

## <a name="creating-the-invocation-and-job-definition-objects"></a><span data-ttu-id="216ad-126">Çağırma ve iş tanımı nesneleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="216ad-126">Creating the Invocation and Job Definition Objects</span></span>

<span data-ttu-id="216ad-127">Ardından işi çalıştırmak için ScheduledJobInvocationInfo ve ScheduledJobDefinition nesneleri oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="216ad-127">You then create ScheduledJobInvocationInfo and ScheduledJobDefinition objects to run the job.</span></span> <span data-ttu-id="216ad-128">Aşağıdaki kod bunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="216ad-128">The following code demonstrates this.</span></span>

```csharp
ScheduledJobInvocationInfo jobInvocationInfo = new ScheduledJobInvocationInfo(
    nw JobDefinition(typeof(ScheduledJobSourceAdapter), scriptBlock.ToString(), schedJobDefName),
    jobDefParameters);

schedJobDefinition = new ScheduledJobDefinition(
    jobInvocationInfo,                          // Defines the PowerShell job to run.
    new ScheduledJobTrigger[1] { jobTrigger },  // Defines when to run the PowerShell job.
    null,                                       // No custom options.  We accept default.
    null);                                      // No credentials.  PowerShell job is run
                                                // in default Task Scheduler process, account.
```

## <a name="registering-the-job-with-the-task-scheduler"></a><span data-ttu-id="216ad-129">İş ile Görev Zamanlayıcısı'nı kaydetme</span><span class="sxs-lookup"><span data-stu-id="216ad-129">Registering the Job with the Task Scheduler</span></span>

<span data-ttu-id="216ad-130">Aşağıdaki kod, Windows Görev Zamanlayıcısı ile iş kaydeder.</span><span class="sxs-lookup"><span data-stu-id="216ad-130">The following code registers the job with the Windows Task Scheduler.</span></span>

```csharp
schedJobDefinition.Register();
registrationSucceeded = true;
Console.WriteLine("Scheduled job has been registered.  Waiting 30 seconds for it to be started and run.");
```

## <a name="complete-code-example"></a><span data-ttu-id="216ad-131">Tam kod örneği</span><span class="sxs-lookup"><span data-stu-id="216ad-131">Complete Code Example</span></span>

<span data-ttu-id="216ad-132">Kendisinden önceki kod parçacıkları alınan tam kod örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="216ad-132">The following is the complete code example from which the previous snippets were taken.</span></span>

```csharp
using System;
using System.Threading;
using System.Collections.Generic;
using System.Management.Automation;             // Windows PowerShell namespace.
using Microsoft.PowerShell.ScheduledJob;        // Windows PowerShell ScheduledJob namespace.

namespace Microsoft.Samples.PowerShell.ScheduledJob
{
    /// <summary>
    /// This class contains the Main entry point for the application.
    /// </summary>
    public class ScheduledJobSample
    {
        /// <summary>
        /// This sample shows how to use the PowerShell ScheduledJob API to create
        /// a simple PowerShell scheduled job, register it with a trigger object
        /// that defines when the job will run and retrieve job run results from
        /// the job file store.
        /// </summary>
        /// <param name="args"></param>
        public static void Main(string[] args)
        {
            // ScheduledJobDefinition contains all elements of a PowerShell scheduled
            // job including the PowerShell job script or script file path, scheduling
            // triggers, and scheduling options.
            ScheduledJobDefinition schedJobDefinition = null;
            bool registrationSucceeded = false;

            try
            {
                // First create a scheduled job trigger object.  This object will
                // define when the PowerShell job is scheduled to run.  For this
                // example we will create a trigger to run the job just one time
                // 20 seconds after the trigger object is created.
                // Note: If you are stepping through this code in a debugger you
                // may want to increase the 20 seconds value so that the trigger time
                // remains in the future once you register the scheduled job.
                ScheduledJobTrigger jobTrigger = ScheduledJobTrigger.CreateOnceTrigger(
                    DateTime.Now.AddSeconds(20),        // Create trigger to start job 20 seconds after now.
                    TimeSpan.Zero,                      // No random delay
                    null,                               // No repetition interval time
                    null,                               // No repetition interval duration
                    1,                                  // Trigger Id
                    true);                              // Create trigger enabled

                // Create a parameter dictionary that defines the PowerShell job.
                // For this example we will create a simple script that runs for
                // 5 seconds generating output.
                // Here are the parameters supported to define the PowerShell job.
                // Name                 - Job name string.
                // ScriptBlock          - PowerShell ScriptBlock type.
                // FilePath             - PowerShell script file path string.
                // InitializationScript - PowerShell Scriptblock type.
                // ArgumentList         - object[] type.
                // RunAs32              - Switch (boolean type).
                string schedJobDefName = "MySampleSchedJob";
                Dictionary<string, object> jobDefParameters = new Dictionary<string, object>();
                jobDefParameters.Add("Name", schedJobDefName);      // Unique name is required.

                ScriptBlock scriptBlock = ScriptBlock.Create(@"1..5 | foreach {sleep 1; ""SchedJobOutput $_""}");
                jobDefParameters.Add("ScriptBlock", scriptBlock);  // A scriptblock or script FilePath
                                                                   // is required.

                // Now create a JobInvocation object that contains all information about
                // the PowerShell job to run.
                ScheduledJobInvocationInfo jobInvocationInfo = new ScheduledJobInvocationInfo(
                    new JobDefinition(typeof(ScheduledJobSourceAdapter), scriptBlock.ToString(), schedJobDefName),
                    jobDefParameters);

                // Finally create the scheduled job definition object that pulls all
                // of this information together.
                schedJobDefinition = new ScheduledJobDefinition(
                    jobInvocationInfo,                          // Defines the PowerShell job to run.
                    new ScheduledJobTrigger[1] { jobTrigger },  // Defines when to run the PowerShell job.
                    null,                                       // No custom options.  We accept default.
                    null);                                      // No credentials.  PowerShell job is run
                                                                // in default Task Scheduler process, account.

                // Next we register this scheduled job object with Windows Task Scheduler.
                // The Task Scheduler will run the PowerShell script based on the provided job trigger.
                schedJobDefinition.Register();
                registrationSucceeded = true;
                Console.WriteLine("Scheduled job has been registered.  Waiting 30 seconds for it to be started and run.");

                // You can see this PowerShell job task registered in the Task Scheduler UI.
                // Look under path: Task Scheduler Library\Microsoft\Windows\PowerShell\ScheduledJobs

                // Wait for Task Scheduler to run the PowerShell job.  This should happen in 20 seconds
                // and then the job will take about 5 seconds to run.  If PowerShell job task doesn't
                // run try increasing the trigger time in the ScheduledJobTrigger object.  You can also
                // run this task manually from the Task Scheduler UI.
                for (int count = 1; count < 31; ++count)
                {
                    Thread.Sleep(1000);
                    Console.WriteLine(count + " seconds elapsed");
                }

                Console.WriteLine();
                Console.WriteLine("Job run results.");
                Console.WriteLine();

                // Since the PowerShell job runs in a non-interactive Task Scheduler
                // process the job status and output data is written to a file based
                // job store and the directory location is the current user local app
                // data ($env:LOCALAPPDATA).
                // This job store can be accessed through the ScheduledJobSourceAdapter class.
                ScheduledJobSourceAdapter schedJobSourceAdapter = new ScheduledJobSourceAdapter();
                IList<Job2> jobRuns = schedJobSourceAdapter.GetJobs();
                foreach (var jobRun in jobRuns)
                {
                    // Check for jobs in finished state.
                    // Note that job data is not written to the job store until the job
                    // has reached a finished state.
                    JobState jobState = jobRun.JobStateInfo.State;
                    if (jobState == JobState.Completed ||
                        jobState == JobState.Stopped ||
                        jobState == JobState.Failed)
                    {
                        // Write job run finished state.
                        Console.WriteLine("Job Status: " + jobRun.JobStateInfo.State);
                        Console.WriteLine();
                        Console.WriteLine("Job Data");

                        // Write output data.
                        foreach (var item in jobRun.Output)
                        {
                            Console.WriteLine(item.ToString());
                        }

                        // Write any errors.
                        foreach (var item in jobRun.Error)
                        {
                            Console.WriteLine(item.ToString());
                        }
                    }
                }

                Console.WriteLine();
                Console.WriteLine("Press any key to continue...");
                Console.ReadKey();
            }
            catch (ScheduledJobException e)
            {
                Console.WriteLine("Error: " + e.Message);
            }
            finally
            {
                // Unregister this scheduled job or an error will be thrown when
                // running this sample code again (scheduled job already exists.)
                // because all registered scheduled jobs must have a unique name.
                if (registrationSucceeded)
                {
                    schedJobDefinition.Remove(true);
                }
            }
        }
    }
}
```
