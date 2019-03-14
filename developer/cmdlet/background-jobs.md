---
title: Arka plan işleri | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a0ef5ac9-8254-4832-ace8-84b356c10f08
caps.latest.revision: 13
ms.openlocfilehash: ff4fe159eedc47fc69f4d783cd90d2b0e888c0d5
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794714"
---
# <a name="background-jobs"></a><span data-ttu-id="f52b7-102">Arka Plan İşleri</span><span class="sxs-lookup"><span data-stu-id="f52b7-102">Background Jobs</span></span>

<span data-ttu-id="f52b7-103">Dahili olarak veya bir Windows PowerShell cmdlet'leri, eylem gerçekleştirebilir*arka plan işi*.</span><span class="sxs-lookup"><span data-stu-id="f52b7-103">Cmdlets can perform their action internally or as a Windows PowerShell*background job*.</span></span> <span data-ttu-id="f52b7-104">Bir cmdlet bir arka plan işi çalıştığında, iş cmdlet'ini kullanarak işlem hattı iş parçacığından ayrı kendi iş parçacığında zaman uyumsuz olarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="f52b7-104">When a cmdlet runs as a background job, the work is done asynchronously in its own thread separate from the pipeline thread that the cmdlet is using.</span></span> <span data-ttu-id="f52b7-105">Bir cmdlet bir arka plan işi çalıştığında kullanıcı açısından bakıldığında, komut istemini hemen iş işleminin tamamlanması zaman alır ve iş çalışırken kullanıcı kesinti olmadan devam etmek bile döndürür.</span><span class="sxs-lookup"><span data-stu-id="f52b7-105">From the user perspective, when a cmdlet runs as a background job, the command prompt returns immediately even if the job takes an extended amount of time to complete, and the user can continue without interruption while the job runs.</span></span>

## <a name="background-jobs-child-jobs-and-the-job-repository"></a><span data-ttu-id="f52b7-106">Arka plan işleri, alt işler ve iş havuz</span><span class="sxs-lookup"><span data-stu-id="f52b7-106">Background Jobs, Child Jobs, and the Job Repository</span></span>

<span data-ttu-id="f52b7-107">Arka plan işleri destekleyen cmdlet'ler tarafından döndürülen iş nesnesi, iş tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f52b7-107">The job object that is returned by the cmdlets that support background jobs defines the job.</span></span> <span data-ttu-id="f52b7-108">( [Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) cmdlet ayrıca bir iş nesnesi döndürür.) İş, iş, durum bilgisi ve alt projeleri belirtmek için kullanılan tanımlayıcı adını bu tanımında dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="f52b7-108">(The [Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) cmdlet also returns a job object.) The name of the job, an identifier that is used to specify the job, the state information, and the child jobs are included in this definition.</span></span> <span data-ttu-id="f52b7-109">İşi iş gerçekleştirmez.</span><span class="sxs-lookup"><span data-stu-id="f52b7-109">The job does not perform any of the work.</span></span> <span data-ttu-id="f52b7-110">Alt iş asıl işi gerçekleştirdiğinden her bir arka plan iş en az bir alt iş sahiptir.</span><span class="sxs-lookup"><span data-stu-id="f52b7-110">Each background job has at least one child job because the child job performs the actual work.</span></span> <span data-ttu-id="f52b7-111">Böylece iş arka plan işi olarak gerçekleştirilen bir cmdlet'ini çalıştırdığınızda, cmdlet işi ve alt işlerin olarak adlandırılır, ortak bir depoya eklemeniz gerekir *iş depo*.</span><span class="sxs-lookup"><span data-stu-id="f52b7-111">When you run a cmdlet so that the work is performed as a background job, the cmdlet must add the job and the child jobs to a common repository, referred to as the *job repository*.</span></span>

<span data-ttu-id="f52b7-112">Arka plan işleri komut satırında nasıl işleneceğini hakkında daha fazla bilgi için aşağıdakilere bakın:</span><span class="sxs-lookup"><span data-stu-id="f52b7-112">For more information about how background jobs are handled at the command line, see the following:</span></span>

- [<span data-ttu-id="f52b7-113">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="f52b7-113">about_Jobs</span></span>](/powershell/module/microsoft.powershell.core/about/about_jobs)

- [<span data-ttu-id="f52b7-114">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="f52b7-114">about_Job_Details</span></span>](/powershell/module/microsoft.powershell.core/about/about_job_details)

- [<span data-ttu-id="f52b7-115">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="f52b7-115">about_Remote_Jobs</span></span>](/powershell/module/microsoft.powershell.core/about/about_remote_jobs)

## <a name="writing-a-cmdlet-that-runs-as-a-background-job"></a><span data-ttu-id="f52b7-116">Arka plan işi olarak çalıştırılan bir Cmdlet yazma</span><span class="sxs-lookup"><span data-stu-id="f52b7-116">Writing a Cmdlet That Runs as a Background Job</span></span>

<span data-ttu-id="f52b7-117">Arka plan işi olarak çalıştırılabilir bir cmdlet yazmak için aşağıdaki görevleri tamamlamanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="f52b7-117">To write a cmdlet that can be run as a background job, you must complete the following tasks:</span></span>

- <span data-ttu-id="f52b7-118">Tanımlayan bir `asJob` kullanıcı cmdlet'i bir arka plan işi çalıştırmak karar verebilir böylece parametresi geçin.</span><span class="sxs-lookup"><span data-stu-id="f52b7-118">Define an `asJob` switch parameter so that the user can decide whether to run the cmdlet as a background job.</span></span>

- <span data-ttu-id="f52b7-119">Türetilen bir nesne oluşturma [System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f52b7-119">Create an object that derives from the [System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) class.</span></span> <span data-ttu-id="f52b7-120">Bu nesne bir özel iş nesnesi veya gibi Windows PowerShell tarafından sağlanan bir iş nesnesi olabilir bir [System.Management.Automation.Pseventjob](/dotnet/api/System.Management.Automation.PSEventJob) nesne.</span><span class="sxs-lookup"><span data-stu-id="f52b7-120">This object can be a custom job object or a job object provided by Windows PowerShell, such as a [System.Management.Automation.Pseventjob](/dotnet/api/System.Management.Automation.PSEventJob) object.</span></span>

- <span data-ttu-id="f52b7-121">Bir kayıt işleme yöntemine ekleyin bir `if` cmdlet'i bir arka plan işi çalıştırılıp çalıştırılmayacağını algılar deyimi.</span><span class="sxs-lookup"><span data-stu-id="f52b7-121">In a record processing method, add an `if` statement that detects whether the cmdlet should run as a background job.</span></span>

- <span data-ttu-id="f52b7-122">Özel iş nesneler için iş sınıfı uygulayın.</span><span class="sxs-lookup"><span data-stu-id="f52b7-122">For custom job objects, implement the job class.</span></span>

- <span data-ttu-id="f52b7-123">Cmdlet'i bir arka plan işi çalışıp bağlı olarak uygun nesneleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="f52b7-123">Return the appropriate objects, depending on whether the cmdlet is run as a background job.</span></span>

<span data-ttu-id="f52b7-124">Kod örneği için bkz: [destek işleri nasıl](./how-to-support-jobs.md).</span><span class="sxs-lookup"><span data-stu-id="f52b7-124">For a code example, see [How to Support Jobs](./how-to-support-jobs.md).</span></span>

## <a name="background-job-related-apis"></a><span data-ttu-id="f52b7-125">Arka plan işi ile ilgili API'ler</span><span class="sxs-lookup"><span data-stu-id="f52b7-125">Background Job-Related APIs</span></span>

<span data-ttu-id="f52b7-126">Aşağıdaki API'leri arka plan işlerini yönetmek için Windows PowerShell tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="f52b7-126">The following APIs are provided by Windows PowerShell to manage background jobs.</span></span>

<span data-ttu-id="f52b7-127">[System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) özel iş nesneleri türetilir.</span><span class="sxs-lookup"><span data-stu-id="f52b7-127">[System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) Derives custom job objects.</span></span> <span data-ttu-id="f52b7-128">Bu bir soyut sınıftır.</span><span class="sxs-lookup"><span data-stu-id="f52b7-128">This is an abstract class.</span></span>

<span data-ttu-id="f52b7-129">[System.Management.Automation.Jobrepository](/dotnet/api/System.Management.Automation.JobRepository) yönetir ve geçerli etkin arka plan işleri hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="f52b7-129">[System.Management.Automation.Jobrepository](/dotnet/api/System.Management.Automation.JobRepository) Manages and provides information about the current active background jobs.</span></span>

<span data-ttu-id="f52b7-130">[System.Management.Automation.Jobstate](/dotnet/api/System.Management.Automation.JobState) arka plan işinin durumunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f52b7-130">[System.Management.Automation.Jobstate](/dotnet/api/System.Management.Automation.JobState) Defines the state of the background job.</span></span> <span data-ttu-id="f52b7-131">Başlarken, çalışan ve durduruldu durumları içerir.</span><span class="sxs-lookup"><span data-stu-id="f52b7-131">States include Started, Running, and Stopped.</span></span>

<span data-ttu-id="f52b7-132">[System.Management.Automation.Jobstateinfo](/dotnet/api/System.Management.Automation.JobStateInfo) bir arka plan işi durumu hakkında bilgi sağlar ve bir hata nedeniyle, işin geçerli durumuna girdiğinin son durumu değiştirirseniz neden oldu.</span><span class="sxs-lookup"><span data-stu-id="f52b7-132">[System.Management.Automation.Jobstateinfo](/dotnet/api/System.Management.Automation.JobStateInfo) Provides information about the state of a background job and, if the last state change was caused by an error, the reason the job entered its current state.</span></span>

<span data-ttu-id="f52b7-133">[System.Management.Automation.Jobstateeventargs](/dotnet/api/System.Management.Automation.JobStateEventArgs) bir arka plan işi durumu değiştiğinde bir olay bağımsız değişkenleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="f52b7-133">[System.Management.Automation.Jobstateeventargs](/dotnet/api/System.Management.Automation.JobStateEventArgs) Provides the arguments for an event that is raised when a background job changes state.</span></span>

## <a name="windows-powershell-job-cmdlets"></a><span data-ttu-id="f52b7-134">Windows PowerShell iş cmdlet'leri</span><span class="sxs-lookup"><span data-stu-id="f52b7-134">Windows PowerShell Job Cmdlets</span></span>

<span data-ttu-id="f52b7-135">Aşağıdaki cmdlet, arka plan işlerini yönetmek için Windows PowerShell tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="f52b7-135">The following cmdlets are provided by Windows PowerShell to manage background jobs.</span></span>

[<span data-ttu-id="f52b7-136">Get-Job</span><span class="sxs-lookup"><span data-stu-id="f52b7-136">Get-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Get-Job)

<span data-ttu-id="f52b7-137">Geçerli oturumda çalışan Windows PowerShell arka plan işleri alır.</span><span class="sxs-lookup"><span data-stu-id="f52b7-137">Gets Windows PowerShell background jobs that are running in the current session.</span></span>

[<span data-ttu-id="f52b7-138">Alma işlemi</span><span class="sxs-lookup"><span data-stu-id="f52b7-138">Receive-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Receive-Job)

<span data-ttu-id="f52b7-139">Geçerli oturumda Windows PowerShell arka plan işleri sonuçlarını alır.</span><span class="sxs-lookup"><span data-stu-id="f52b7-139">Gets the results of the Windows PowerShell background jobs in the current session.</span></span>

[<span data-ttu-id="f52b7-140">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="f52b7-140">Remove-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Remove-Job)

<span data-ttu-id="f52b7-141">Bir Windows PowerShell arka plan işi siler.</span><span class="sxs-lookup"><span data-stu-id="f52b7-141">Deletes a Windows PowerShell background job.</span></span>

[<span data-ttu-id="f52b7-142">İşi Başlat</span><span class="sxs-lookup"><span data-stu-id="f52b7-142">Start-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Start-Job)

<span data-ttu-id="f52b7-143">Bir Windows PowerShell arka plan işi başlatır.</span><span class="sxs-lookup"><span data-stu-id="f52b7-143">Starts a Windows PowerShell background job.</span></span>

[<span data-ttu-id="f52b7-144">Durdurma işi</span><span class="sxs-lookup"><span data-stu-id="f52b7-144">Stop-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Stop-Job)

<span data-ttu-id="f52b7-145">Bir Windows PowerShell arka plan işi durdurulur.</span><span class="sxs-lookup"><span data-stu-id="f52b7-145">Stops a Windows PowerShell background job.</span></span>

[<span data-ttu-id="f52b7-146">İşi bekleyin</span><span class="sxs-lookup"><span data-stu-id="f52b7-146">Wait-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Wait-Job)

<span data-ttu-id="f52b7-147">Komut isteminden birini veya tümünü oturumda çalışan Windows PowerShell arka plan işleri tamamlanana kadar engeller.</span><span class="sxs-lookup"><span data-stu-id="f52b7-147">Suppresses the command prompt until one or all of the Windows PowerShell background jobs running in the session are complete.</span></span>

## <a name="see-also"></a><span data-ttu-id="f52b7-148">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="f52b7-148">See Also</span></span>

[<span data-ttu-id="f52b7-149">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="f52b7-149">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
