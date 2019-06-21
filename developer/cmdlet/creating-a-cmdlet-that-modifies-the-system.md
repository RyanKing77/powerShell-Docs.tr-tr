---
title: Bir Cmdlet oluşturma sistemi değiştirir | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- should process [PowerShell Programmer's Guide]
- should continue [PowerShell Programmer's Guide]
- user feedback [PowerShell Programmer's Guide]
- confirm impact [PowerShell Programmer's Guide]
ms.assetid: 59be4120-1700-4d92-a308-ef4a32ccf11a
caps.latest.revision: 8
ms.openlocfilehash: 8a65915b88a04e36e773853b903528a65fe11e99
ms.sourcegitcommit: f60fa420bdc81db174e6168d3aeb11371e483162
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/20/2019
ms.locfileid: "67301398"
---
# <a name="creating-a-cmdlet-that-modifies-the-system"></a><span data-ttu-id="4567e-102">Sistemi Değiştiren bir Cmdlet Oluşturma</span><span class="sxs-lookup"><span data-stu-id="4567e-102">Creating a Cmdlet that Modifies the System</span></span>

<span data-ttu-id="4567e-103">Bazı durumlarda bir cmdlet, yalnızca Windows PowerShell çalışma zamanı durumunu sistemin çalışma durumu değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4567e-103">Sometimes a cmdlet must modify the running state of the system, not just the state of the Windows PowerShell runtime.</span></span> <span data-ttu-id="4567e-104">Bu gibi durumlarda cmdlet değişikliği yapmanız gerekip gerekmediğini doğrulamak bir fırsat kullanıcı izin vermelidir.</span><span class="sxs-lookup"><span data-stu-id="4567e-104">In these cases, the cmdlet should allow the user a chance to confirm whether or not to make the change.</span></span>

<span data-ttu-id="4567e-105">Onay desteklemek için bir cmdlet'in iki işlem yapmalısınız.</span><span class="sxs-lookup"><span data-stu-id="4567e-105">To support confirmation a cmdlet must do two things.</span></span>

- <span data-ttu-id="4567e-106">Belirttiğinizde cmdlet onay desteklediğini bildirmek [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) SupportsShouldProcess anahtar sözcüğü ayarlayarak özniteliği `true`.</span><span class="sxs-lookup"><span data-stu-id="4567e-106">Declare that the cmdlet supports confirmation when you specify the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute by setting the SupportsShouldProcess keyword to `true`.</span></span>

- <span data-ttu-id="4567e-107">Çağrı [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) (aşağıdaki örnekte gösterildiği gibi) cmdlet'inin yürütülmesi sırasında.</span><span class="sxs-lookup"><span data-stu-id="4567e-107">Call [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) during the execution of the cmdlet (as shown in the following example).</span></span>

<span data-ttu-id="4567e-108">Onay destekleyerek, bir cmdlet kullanıma sunan `Confirm` ve `WhatIf` Windows PowerShell tarafından sağlanan ve ayrıca geliştirme yönergelere cmdlet'leri için uygun parametreleri ( cmdlet'igeliştirmekılavuzlarıhakkındadahafazlabilgiiçinbkz.[ Cmdlet geliştirme yönergeleri](./cmdlet-development-guidelines.md).).</span><span class="sxs-lookup"><span data-stu-id="4567e-108">By supporting confirmation, a cmdlet exposes the `Confirm` and `WhatIf` parameters that are provided by Windows PowerShell, and also meets the development guidelines for cmdlets (For more information about cmdlet development guidelines, see [Cmdlet Development Guidelines](./cmdlet-development-guidelines.md).).</span></span>

## <a name="changing-the-system"></a><span data-ttu-id="4567e-109">Sistem değiştirme</span><span class="sxs-lookup"><span data-stu-id="4567e-109">Changing the System</span></span>

<span data-ttu-id="4567e-110">"Sistem değiştirme" işlemi, potansiyel olarak Windows PowerShell dışında sistem durumunu değiştiren herhangi bir cmdlet'i ifade eder.</span><span class="sxs-lookup"><span data-stu-id="4567e-110">The act of "changing the system" refers to any cmdlet that potentially changes the state of the system outside Windows PowerShell.</span></span> <span data-ttu-id="4567e-111">Örneğin, bir veritabanı tablosunda bir satıra onaylanması sistemde yapılan tüm değişiklikleri Koleksiyonlar'a etkinleştirme veya bir kullanıcı hesabı devre dışı bırakma işlemi durduruluyor.</span><span class="sxs-lookup"><span data-stu-id="4567e-111">For example, stopping a process, enabling or disabling a user account, or adding a row to a database table are all changes to the system that should be confirmed.</span></span> <span data-ttu-id="4567e-112">Buna karşılık, veri okuma veya geçici bağlantı işlemleri sistem değiştirmeyin ve genellikle onay gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="4567e-112">In contrast, operations that read data or establish transient connections do not change the system and generally do not require confirmation.</span></span> <span data-ttu-id="4567e-113">Onay ayrıca gerekli değildir, etkili sınırlıdır ve Windows PowerShell çalışma zamanı içinde olduğu gibi eylemler için `set-variable`.</span><span class="sxs-lookup"><span data-stu-id="4567e-113">Confirmation is also not needed for actions whose effect is limited to inside the Windows PowerShell runtime, such as `set-variable`.</span></span> <span data-ttu-id="4567e-114">Kalıcı bir değişiklik yapmamanız veya cmdlet'leri bildirmelidir `SupportsShouldProcess` ve çağrı [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) yalnızca kalıcı bir değişiklik yapmak üzere olmaları durumunda.</span><span class="sxs-lookup"><span data-stu-id="4567e-114">Cmdlets that might or might not make a persistent change should declare `SupportsShouldProcess` and call [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) only if they are about to make a persistent change.</span></span>

> [!NOTE]
> <span data-ttu-id="4567e-115">ShouldProcess onay yalnızca cmdlet'ler için geçerli olur.</span><span class="sxs-lookup"><span data-stu-id="4567e-115">ShouldProcess confirmation applies only to cmdlets.</span></span> <span data-ttu-id="4567e-116">Bir komut veya betik .NET yöntemleri veya özellikleri doğrudan çağırma veya Windows PowerShell dışında çağıran uygulamalardan bir sistemin çalışır duruma değiştirir, bu formu onayının kullanılabilir olmaz.</span><span class="sxs-lookup"><span data-stu-id="4567e-116">If a command or script modifies the running state of a system by directly calling .NET methods or properties, or by calling applications outside of Windows PowerShell, this form of confirmation will not be available.</span></span>

## <a name="the-stopproc-cmdlet"></a><span data-ttu-id="4567e-117">StopProc cmdlet'i</span><span class="sxs-lookup"><span data-stu-id="4567e-117">The StopProc Cmdlet</span></span>

<span data-ttu-id="4567e-118">Bu konu Get-Proc cmdlet'ini kullanarak alınan işlemler durdurmaya çalışır bir Stop-Proc cmdlet açıklar (açıklanan [oluşturma bilgisayarınızı ilk Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span><span class="sxs-lookup"><span data-stu-id="4567e-118">This topic describes a Stop-Proc cmdlet that attempts to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="4567e-119">Cmdlet tanımlama</span><span class="sxs-lookup"><span data-stu-id="4567e-119">Defining the Cmdlet</span></span>

<span data-ttu-id="4567e-120">İlk adımda cmdlet'i oluşturma her zaman cmdlet adlandırma ve cmdlet uygulayan .NET sınıf bildirme.</span><span class="sxs-lookup"><span data-stu-id="4567e-120">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="4567e-121">Sistem değiştirmek için bir cmdlet yazıyorsanız olduğundan, buna uygun olarak adlandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4567e-121">Because you are writing a cmdlet to change the system, it should be named accordingly.</span></span> <span data-ttu-id="4567e-122">"Durdur" seçeneğini fiili adı, bu nedenle bu cmdlet'i durakları sistem işlemleri, tanımlanan [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) sınıfıyla isim cmdlet'i işlemlerini durdurduğundan belirtmek için "işlem".</span><span class="sxs-lookup"><span data-stu-id="4567e-122">This cmdlet stops system processes, so the verb name chosen here is "Stop", defined by the [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) class, with the noun "Proc" to indicate that the cmdlet stops processes.</span></span> <span data-ttu-id="4567e-123">Onaylanan cmdlet fiilleri hakkında daha fazla bilgi için bkz: [Cmdlet fiili adları](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="4567e-123">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="4567e-124">Bu Stop-Proc cmdlet için sınıf tanımının verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="4567e-124">The following is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

<span data-ttu-id="4567e-125">Unutmayın, [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) bildirimi `SupportsShouldProcess` özniteliği anahtar sözcüğü ayarlandığında `true` çağrı yapmak cmdlet etkinleştirmek için [ System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) ve [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span><span class="sxs-lookup"><span data-stu-id="4567e-125">Be aware that in the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) declaration, the `SupportsShouldProcess` attribute keyword is set to `true` to enable the cmdlet to make calls to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span></span> <span data-ttu-id="4567e-126">Bu anahtar sözcük kümesi olmadan `Confirm` ve `WhatIf` parametreleri kullanılabilir olmayacak.</span><span class="sxs-lookup"><span data-stu-id="4567e-126">Without this keyword set, the `Confirm` and `WhatIf` parameters will not be available to the user.</span></span>

### <a name="extremely-destructive-actions"></a><span data-ttu-id="4567e-127">Son derece bozucu Eylemler</span><span class="sxs-lookup"><span data-stu-id="4567e-127">Extremely Destructive Actions</span></span>

<span data-ttu-id="4567e-128">Bazı işlemler, bir etkin sabit disk bölümü yeniden biçimlendirme gibi son derece yıkıcı.</span><span class="sxs-lookup"><span data-stu-id="4567e-128">Some operations are extremely destructive, such as reformatting an active hard disk partition.</span></span> <span data-ttu-id="4567e-129">Bu gibi durumlarda cmdlet ayarlamalısınız `ConfirmImpact`  =  `ConfirmImpact.High` bildirirken [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) özniteliği.</span><span class="sxs-lookup"><span data-stu-id="4567e-129">In these cases, the cmdlet should set `ConfirmImpact` = `ConfirmImpact.High` when declaring the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute.</span></span> <span data-ttu-id="4567e-130">Bu ayar bile kullanıcı belirtilmemişse cmdlet isteği kullanıcı onayı zorlar. `Confirm` parametresi.</span><span class="sxs-lookup"><span data-stu-id="4567e-130">This setting forces the cmdlet to request user confirmation even when the user has not specified the `Confirm` parameter.</span></span> <span data-ttu-id="4567e-131">Aşırı kullanımı cmdlet'i geliştiriciler ancak kaçınmalısınız `ConfirmImpact` bir kullanıcı hesabı silme gibi yalnızca potansiyel olarak zararlı işlemler için.</span><span class="sxs-lookup"><span data-stu-id="4567e-131">However, cmdlet developers should avoid overusing `ConfirmImpact` for operations that are just potentially destructive, such as deleting a user account.</span></span> <span data-ttu-id="4567e-132">Unutmayın `ConfirmImpact` ayarlanır [System.Management.Automation.ConfirmImpact](/dotnet/api/System.Management.Automation.ConfirmImpact) **yüksek**.</span><span class="sxs-lookup"><span data-stu-id="4567e-132">Remember that if `ConfirmImpact` is set to [System.Management.Automation.ConfirmImpact](/dotnet/api/System.Management.Automation.ConfirmImpact) **High**.</span></span>

<span data-ttu-id="4567e-133">Benzer şekilde, bazı işlemler teorik olarak çalışan Windows PowerShell dışında bir sistem durumunu değiştirebilir ancak yıkıcı, olması olası değildir.</span><span class="sxs-lookup"><span data-stu-id="4567e-133">Similarly, some operations are unlikely to be destructive, although they do in theory modify the running state of a system outside Windows PowerShell.</span></span> <span data-ttu-id="4567e-134">Bu cmdlet'leri ayarlayabilirsiniz `ConfirmImpact` için [System.Management.Automation.Confirmimpact.Low](/dotnet/api/system.management.automation.confirmimpact?view=powershellsdk-1.1.0).</span><span class="sxs-lookup"><span data-stu-id="4567e-134">Such cmdlets can set `ConfirmImpact` to [System.Management.Automation.Confirmimpact.Low](/dotnet/api/system.management.automation.confirmimpact?view=powershellsdk-1.1.0).</span></span> <span data-ttu-id="4567e-135">Bu kullanıcının yalnızca orta etkisi ve yüksek etkili işlemlerini doğrulamak için burada istedi onay istekleri atlayacaktır.</span><span class="sxs-lookup"><span data-stu-id="4567e-135">This will bypass confirmation requests where the user has asked to confirm only medium-impact and high-impact operations.</span></span>

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="4567e-136">Sistem değiştirilmesi için parametreleri tanımlama</span><span class="sxs-lookup"><span data-stu-id="4567e-136">Defining Parameters for System Modification</span></span>

<span data-ttu-id="4567e-137">Bu bölümde, destek sistem değiştirilmesi için gerekli olanlar da dahil, bir cmdlet parametreleri tanımlayın açıklar.</span><span class="sxs-lookup"><span data-stu-id="4567e-137">This section describes how to define the cmdlet parameters, including those that are needed to support system modification.</span></span> <span data-ttu-id="4567e-138">Bkz: [parametreler, işlem komut satırı girişi ekleme](./adding-parameters-that-process-command-line-input.md) parametreleri tanımlama hakkında genel bilgi gerekiyorsa.</span><span class="sxs-lookup"><span data-stu-id="4567e-138">See [Adding Parameters that Process CommandLine Input](./adding-parameters-that-process-command-line-input.md) if you need general information about defining parameters.</span></span>

<span data-ttu-id="4567e-139">Stop-Proc cmdlet, üç parametre tanımlar: `Name`, `Force`, ve `PassThru`.</span><span class="sxs-lookup"><span data-stu-id="4567e-139">The Stop-Proc cmdlet defines three parameters: `Name`, `Force`, and `PassThru`.</span></span>

<span data-ttu-id="4567e-140">`Name` Karşılık gelen parametre `Name` özelliği işlem giriş nesnesi.</span><span class="sxs-lookup"><span data-stu-id="4567e-140">The `Name` parameter corresponds to the `Name` property of the process input object.</span></span> <span data-ttu-id="4567e-141">Unutmayın, `Name` durdurmak için adlandırılmış bir işlem yoksa cmdlet başarısız olacağından bu parametre zorunludur.</span><span class="sxs-lookup"><span data-stu-id="4567e-141">Be aware that the `Name` parameter in this sample is mandatory, as the cmdlet will fail if it does not have a named process to stop.</span></span>

<span data-ttu-id="4567e-142">`Force` Parametresi çağrısına geçersiz kılmasına izin verir [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span><span class="sxs-lookup"><span data-stu-id="4567e-142">The `Force` parameter allows the user to override calls to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span></span> <span data-ttu-id="4567e-143">Aslında, herhangi bir cmdlet'i çağırır [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) olmalıdır bir `Force` parametre için zaman `Force` belirtilirse, cmdlet çağrısı atlar [ System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) ve işleme devam eder.</span><span class="sxs-lookup"><span data-stu-id="4567e-143">In fact, any cmdlet that calls [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) should have a `Force` parameter so that when `Force` is specified, the cmdlet skips the call to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) and proceeds with the operation.</span></span> <span data-ttu-id="4567e-144">Bu çağrılar etkilemez unutmayın [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess).</span><span class="sxs-lookup"><span data-stu-id="4567e-144">Be aware that this does not affect calls to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess).</span></span>

<span data-ttu-id="4567e-145">`PassThru` Parametresi bir işlemi durdurulduktan sonra cmdlet'i bir çıkış nesnesi aracılığıyla işlem hattı, bu durumda, geçirmediğini belirtmek için kullanıcı olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="4567e-145">The `PassThru` parameter allows the user to indicate whether the cmdlet passes an output object through the pipeline, in this case, after a process is stopped.</span></span> <span data-ttu-id="4567e-146">Bu parametre cmdlet'e giriş nesnenin kendisi yerine bir özelliğe bağlı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="4567e-146">Be aware that this parameter is tied to the cmdlet itself instead of to a property of the input object.</span></span>

<span data-ttu-id="4567e-147">Stop-Proc cmdlet'i için parametre bildirimi aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="4567e-147">Here is the parameter declaration for the Stop-Proc cmdlet.</span></span>

```csharp
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
/// Specify the Force parameter that allows the user to override
/// the ShouldContinue call to force the stop operation. This
/// parameter should always be used with caution.
/// </summary>
[Parameter]
public SwitchParameter Force
{
  get { return force; }
  set { force = value; }
}
private bool force;

/// <summary>
/// Specify the PassThru parameter that allows the user to specify
/// that the cmdlet should pass the process object down the pipeline
/// after the process has been stopped.
/// </summary>
[Parameter]
public SwitchParameter PassThru
{
  get { return passThru; }
  set { passThru = value; }
}
private bool passThru;
```

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="4567e-148">Bir giriş işleme yöntemi geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="4567e-148">Overriding an Input Processing Method</span></span>

<span data-ttu-id="4567e-149">Cmdlet'i, girdi işleme yöntemi geçersiz kılmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4567e-149">The cmdlet must override an input processing method.</span></span> <span data-ttu-id="4567e-150">Aşağıdaki kod gösterir [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) kullanılan örnek Stop-Proc cmdlet'te geçersiz kılma.</span><span class="sxs-lookup"><span data-stu-id="4567e-150">The following code illustrates the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) override used in the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="4567e-151">Bu yöntem her istenen işlem adı için işlem özel bir işlem değil, işlemi durdurmak çalışır ve bir çıkış nesnesi daha sonra gönderir sağlar `PassThru` parametre belirtildi.</span><span class="sxs-lookup"><span data-stu-id="4567e-151">For each requested process name, this method ensures that the process is not a special process, tries to stop the process, and then sends an output object if the `PassThru` parameter is specified.</span></span>

```csharp
protected override void ProcessRecord()
{
  foreach (string name in processNames)
  {
    // For every process name passed to the cmdlet, get the associated
    // process(es). For failures, write a non-terminating error
    Process[] processes;

    try
    {
      processes = Process.GetProcessesByName(name);
    }
    catch (InvalidOperationException ioe)
    {
      WriteError(new ErrorRecord(ioe,"Unable to access the target process by name",
                 ErrorCategory.InvalidOperation, name));
      continue;
    }

    // Try to stop the process(es) that have been retrieved for a name
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
                     ErrorCategory.ReadError, process));
          continue;
        }

        // Call Should Process to confirm the operation first.
        // This is always false if WhatIf is set.
        if (!ShouldProcess(string.Format("{0} ({1})", processName,
                           process.Id)))
        {
          continue;
        }
        // Call ShouldContinue to make sure the user really does want
        // to stop a critical process that could possibly stop the computer.
        bool criticalProcess =
             criticalProcessNames.Contains(processName.ToLower());

        if (criticalProcess &&!force)
        {
          string message = String.Format
                ("The process \"{0}\" is a critical process and should not be stopped. Are you sure you wish to stop the process?",
                processName);

          // It is possible that ProcessRecord is called multiple times
          // when the Name parameter receives objects as input from the
          // pipeline. So to retain YesToAll and NoToAll input that the
          // user may enter across multiple calls to ProcessRecord, this
          // information is stored as private members of the cmdlet.
          if (!ShouldContinue(message, "Warning!",
                              ref yesToAll,
                              ref noToAll))
          {
            continue;
          }
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
            // a non-terminating error.
            string message = String.Format("{0} {1} {2}",
                             "Could not stop process \"", processName,
                             "\".");
            WriteError(new ErrorRecord(e, message,
                       ErrorCategory.CloseError, process));
                       continue;
          } // if ((e is...
          else throw;
        } // catch

        // If the PassThru parameter argument is
        // True, pass the terminated process on.
        if (passThru)
        {
          WriteObject(process);
        }
    } // foreach (Process...
  } // foreach (string...
} // ProcessRecord
```

## <a name="calling-the-shouldprocess-method"></a><span data-ttu-id="4567e-152">ShouldProcess yöntemi çağırma</span><span class="sxs-lookup"><span data-stu-id="4567e-152">Calling the ShouldProcess Method</span></span>

<span data-ttu-id="4567e-153">Yöntemi, cmdlet'in işleme giriş çağırmalıdır [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) çalışma durumuna (örneğin, silme dosyaları) bir değişiklik yapılmadan önce bir işlemin yürütülmesi onaylamak için yöntemi sistemi.</span><span class="sxs-lookup"><span data-stu-id="4567e-153">The input processing method of your cmdlet should call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method to confirm execution of an operation before a change (for example, deleting files) is made to the running state of the system.</span></span> <span data-ttu-id="4567e-154">Bu, kabuktan doğru "WhatIf" ve "Onayla" davranışı sağlamak Windows PowerShell çalışma zamanı sağlar.</span><span class="sxs-lookup"><span data-stu-id="4567e-154">This allows the Windows PowerShell runtime to supply the correct "WhatIf" and "Confirm" behavior within the shell.</span></span>

> [!NOTE]
> <span data-ttu-id="4567e-155">Bir cmdlet onu desteklediğini belirten işlemelisiniz ve yapma başarısız [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) çağrısı, kullanıcı Sistem beklenmedik bir şekilde değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4567e-155">If a cmdlet states that it supports should process and fails to make the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call, the user might modify the system unexpectedly.</span></span>

<span data-ttu-id="4567e-156">Çağrı [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) kullanıcı için herhangi bir komut satırı ayarlarını veya tercih değişkenleri dikkate alarak Windows PowerShell çalışma zamanı ile değiştirilmesi kaynağın adını gönderir kullanıcıya görüntülenen belirlemede.</span><span class="sxs-lookup"><span data-stu-id="4567e-156">The call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) sends the name of the resource to be changed to the user, with the Windows PowerShell runtime taking into account any command-line settings or preference variables in determining what should be displayed to the user.</span></span>

<span data-ttu-id="4567e-157">Aşağıdaki örnek, çağrısını gösterir [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) geçersiz kılmasını gelen [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) yöntemi Stop-Proc cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="4567e-157">The following example shows the call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method in the sample Stop-Proc cmdlet.</span></span>

```csharp
if (!ShouldProcess(string.Format("{0} ({1})", processName,
                   process.Id)))
{
  continue;
}
```

## <a name="calling-the-shouldcontinue-method"></a><span data-ttu-id="4567e-158">ShouldContinue yöntemi çağırma</span><span class="sxs-lookup"><span data-stu-id="4567e-158">Calling the ShouldContinue Method</span></span>

<span data-ttu-id="4567e-159">Çağrı [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) yöntem, kullanıcı için ikincil bir ileti gönderir.</span><span class="sxs-lookup"><span data-stu-id="4567e-159">The call to the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method sends a secondary message to the user.</span></span> <span data-ttu-id="4567e-160">Bu çağrı çağrısından sonra yapılan [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) döndürür `true` ve `Force` parametresi ayarlanmamış `true`.</span><span class="sxs-lookup"><span data-stu-id="4567e-160">This call is made after the call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) returns `true` and if the `Force` parameter was not set to `true`.</span></span> <span data-ttu-id="4567e-161">Kullanıcı, sonra işlemi devam olmadığını düşünelim için geri bildirim sunabilir.</span><span class="sxs-lookup"><span data-stu-id="4567e-161">The user can then provide feedback to say whether the operation should be continued.</span></span> <span data-ttu-id="4567e-162">Cmdlet çağrılarınızı [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) olarak tehlikeli olabilecek bir sistem değişiklikleri veya kullanıcı için tüm için Evet ve Hayır tüm seçenekleri sağlamak istediğinizde için ek bir denetim.</span><span class="sxs-lookup"><span data-stu-id="4567e-162">Your cmdlet calls [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) as an additional check for potentially dangerous system modifications or when you want to provide yes-to-all and no-to-all options to the user.</span></span>

<span data-ttu-id="4567e-163">Aşağıdaki örnek, çağrısını gösterir [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) geçersiz kılmasını gelen [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) yöntemi Stop-Proc cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="4567e-163">The following example shows the call to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method in the sample Stop-Proc cmdlet.</span></span>

```csharp
if (criticalProcess &&!force)
{
  string message = String.Format
        ("The process \"{0}\" is a critical process and should not be stopped. Are you sure you wish to stop the process?",
        processName);

  // It is possible that ProcessRecord is called multiple times
  // when the Name parameter receives objects as input from the
  // pipeline. So to retain YesToAll and NoToAll input that the
  // user may enter across multiple calls to ProcessRecord, this
  // information is stored as private members of the cmdlet.
  if (!ShouldContinue(message, "Warning!",
                      ref yesToAll,
                      ref noToAll))
  {
    continue;
  }
} // if (criticalProcess...
```

## <a name="stopping-input-processing"></a><span data-ttu-id="4567e-164">Durdurma giriş işleme</span><span class="sxs-lookup"><span data-stu-id="4567e-164">Stopping Input Processing</span></span>

<span data-ttu-id="4567e-165">Sistem değişiklikleri yapan bir cmdlet'in yöntemi işleme giriş, giriş işleme durdurma bir yol sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4567e-165">The input processing method of a cmdlet that makes system modifications must provide a way of stopping the processing of input.</span></span> <span data-ttu-id="4567e-166">Bu Stop-Proc cmdlet söz konusu olduğunda, gelen bir çağrı yapılır [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) yönteme [System.Diagnostics.Process.Kill\*](/dotnet/api/System.Diagnostics.Process.Kill) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4567e-166">In the case of this Stop-Proc cmdlet, a call is made from the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to the [System.Diagnostics.Process.Kill\*](/dotnet/api/System.Diagnostics.Process.Kill) method.</span></span> <span data-ttu-id="4567e-167">Çünkü `PassThru` parametrenin ayarlanmış `true`, [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) de çağırır [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) göndermek için işlem hattı için işlem nesnesi.</span><span class="sxs-lookup"><span data-stu-id="4567e-167">Because the `PassThru` parameter is set to `true`, [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) also calls [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) to send the process object to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="4567e-168">Kod örneği</span><span class="sxs-lookup"><span data-stu-id="4567e-168">Code Sample</span></span>

<span data-ttu-id="4567e-169">Tamamlanmış C# örnek kod için bkz: [StopProcessSample01 örnek](./stopprocesssample01-sample.md).</span><span class="sxs-lookup"><span data-stu-id="4567e-169">For the complete C# sample code, see [StopProcessSample01 Sample](./stopprocesssample01-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="4567e-170">Nesne türlerini tanımlama ve biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="4567e-170">Defining Object Types and Formatting</span></span>

<span data-ttu-id="4567e-171">Windows PowerShell cmdlet arasında .net nesneleri kullanarak bilgileri geçirir.</span><span class="sxs-lookup"><span data-stu-id="4567e-171">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="4567e-172">Sonuç olarak, bir cmdlet kendi türü tanımlamanız gerekebilir veya başka bir cmdlet tarafından sağlanan mevcut türü genişletmek cmdlet gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="4567e-172">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="4567e-173">Yeni türleri tanımlama veya varolan türleri genişletme hakkında daha fazla bilgi için bkz. [genişletme nesne türleri ve biçimlendirme](/previous-versions//ms714665(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="4567e-173">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="4567e-174">Cmdlet oluşturma</span><span class="sxs-lookup"><span data-stu-id="4567e-174">Building the Cmdlet</span></span>

<span data-ttu-id="4567e-175">Bir cmdlet uyguladıktan sonra bunu Windows PowerShell ile bir Windows PowerShell ek bileşeni kayıtlı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4567e-175">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="4567e-176">Cmdlet'leri kaydetme hakkında daha fazla bilgi için bkz. [kaydetme cmdlet'leri ve sağlayıcıları uygulamalarını barındırmak için nasıl](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="4567e-176">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="4567e-177">Sınama cmdlet'i</span><span class="sxs-lookup"><span data-stu-id="4567e-177">Testing the Cmdlet</span></span>

<span data-ttu-id="4567e-178">Windows PowerShell ile cmdlet'ini kaydedildi, komut satırında çalıştırarak test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4567e-178">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="4567e-179">Stop-Proc cmdlet test birkaç testi aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="4567e-179">Here are several tests that test the Stop-Proc cmdlet.</span></span> <span data-ttu-id="4567e-180">Komut satırından cmdlet'leri kullanma hakkında daha fazla bilgi için bkz. [Windows PowerShell ile çalışmaya başlama](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="4567e-180">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="4567e-181">Windows PowerShell'i başlatın ve aşağıda gösterildiği gibi durdurmak için Stop-Proc cmdlet'ini kullanın.</span><span class="sxs-lookup"><span data-stu-id="4567e-181">Start Windows PowerShell and use the Stop-Proc cmdlet to stop processing as shown below.</span></span> <span data-ttu-id="4567e-182">Cmdlet belirttiğinden `Name` parametre zorunlu olarak, cmdlet sorgu parametresi için.</span><span class="sxs-lookup"><span data-stu-id="4567e-182">Because the cmdlet specifies the `Name` parameter as mandatory, the cmdlet queries for the parameter.</span></span>

    ```powershell
    PS> stop-proc
    ```

<span data-ttu-id="4567e-183">Aşağıdaki çıktı görünür.</span><span class="sxs-lookup"><span data-stu-id="4567e-183">The following output appears.</span></span>

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    Name[0]:
    ```

- <span data-ttu-id="4567e-184">Artık "Not" adlı işlemi durdurmak için cmdlet kullanalım.</span><span class="sxs-lookup"><span data-stu-id="4567e-184">Now let's use the cmdlet to stop the process named "NOTEPAD".</span></span> <span data-ttu-id="4567e-185">Cmdlet eylemi onaylamanızı ister.</span><span class="sxs-lookup"><span data-stu-id="4567e-185">The cmdlet asks you to confirm the action.</span></span>

    ```powershell
    PS> stop-proc -Name notepad
    ```

<span data-ttu-id="4567e-186">Aşağıdaki çıktı görünür.</span><span class="sxs-lookup"><span data-stu-id="4567e-186">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (4996)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="4567e-187">Stop-Proc "WINLOGON" adlı kritik işlemini durdurmak için gösterildiği gibi kullanın.</span><span class="sxs-lookup"><span data-stu-id="4567e-187">Use Stop-Proc as shown to stop the critical process named "WINLOGON".</span></span> <span data-ttu-id="4567e-188">İstenir ve işletim sisteminin yeniden neden olacağından bu eylemi gerçekleştirme hakkında uyarı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="4567e-188">You are prompted and warned about performing this action because it will cause the operating system to reboot.</span></span>

    ```powershell
    PS> stop-proc -Name Winlogon
    ```

<span data-ttu-id="4567e-189">Aşağıdaki çıktı görünür.</span><span class="sxs-lookup"><span data-stu-id="4567e-189">The following output appears.</span></span>

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    Warning!
    The process " winlogon " is a critical process and should not be stopped. Are you sure you wish to stop the process?
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

- <span data-ttu-id="4567e-190">Artık bir uyarı almadan WINLOGON işlemini durdurmak deneyelim.</span><span class="sxs-lookup"><span data-stu-id="4567e-190">Let's now try to stop the WINLOGON process without receiving a warning.</span></span> <span data-ttu-id="4567e-191">Bu komut girişini kullandığını unutmayın `Force` uyarıyı geçersiz kılmak için parametre.</span><span class="sxs-lookup"><span data-stu-id="4567e-191">Be aware that this command entry uses the `Force` parameter to override the warning.</span></span>

    ```powershell
    PS> stop-proc -Name winlogon -Force
    ```

<span data-ttu-id="4567e-192">Aşağıdaki çıktı görünür.</span><span class="sxs-lookup"><span data-stu-id="4567e-192">The following output appears.</span></span>

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="4567e-193">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="4567e-193">See Also</span></span>

[<span data-ttu-id="4567e-194">Komut satırı giriş parametreleri ekleme</span><span class="sxs-lookup"><span data-stu-id="4567e-194">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

<span data-ttu-id="4567e-195">[Nesne türlerini genişletme ve biçimlendirme](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="4567e-195">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="4567e-196">[Cmdlet, sağlayıcılar kaydetmek ve uygulamaları barındırmak nasıl](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="4567e-196">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="4567e-197">Windows PowerShell SDK'sı</span><span class="sxs-lookup"><span data-stu-id="4567e-197">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="4567e-198">Cmdlet örnekleri</span><span class="sxs-lookup"><span data-stu-id="4567e-198">Cmdlet Samples</span></span>](./cmdlet-samples.md)