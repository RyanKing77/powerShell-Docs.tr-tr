---
title: Kullanıcı iletileri, cmdlet'e ekleme | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WriteWarning
- notifications, writing
- progress notification
- WriteVerbose
- Stop-Proc
- WriteProgress
- WriteDebug
- notifications, debug
- ProgressRecord
- samples, Stop-Proc cmdlet
- notifications, progress
- notifications, warning
- WriteObject
- WriteError
- verbose notification
- ProcessRecord
- notifications, verbose
- debug notification
- cmdlet, writing notifications
- warning
- code sample, user notifications
- user notifications
ms.assetid: 14c13acb-f0b7-4613-bc7d-c361d14da1a2
caps.latest.revision: 8
ms.openlocfilehash: ffc08d2713c4bfc0938b2e07146102af8b5467d2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846805"
---
# <a name="adding-user-messages-to-your-cmdlet"></a><span data-ttu-id="2675e-102">Cmdlet’inize Kullanıcı İletileri Ekleme</span><span class="sxs-lookup"><span data-stu-id="2675e-102">Adding User Messages to Your Cmdlet</span></span>

<span data-ttu-id="2675e-103">Cmdlet'leri, kullanıcı için Windows PowerShell çalışma zamanı tarafından görüntülenebilen iletileri çeşitli türlerde yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2675e-103">Cmdlets can write several kinds of messages that can be displayed to the user by the Windows PowerShell runtime.</span></span> <span data-ttu-id="2675e-104">Bu iletiler, aşağıdaki türleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="2675e-104">These messages include the following types:</span></span>

- <span data-ttu-id="2675e-105">Genel kullanıcı bilgilerini içeren ayrıntılı iletiler.</span><span class="sxs-lookup"><span data-stu-id="2675e-105">Verbose messages that contain general user information.</span></span>

- <span data-ttu-id="2675e-106">Sorun giderme bilgilerini içeren bir ileti hata ayıklayın.</span><span class="sxs-lookup"><span data-stu-id="2675e-106">Debug messages that contain troubleshooting information.</span></span>

- <span data-ttu-id="2675e-107">İlgili olabilecek bir işlemi gerçekleştirmek için cmdlet, bir bildirimi içeren bir uyarı iletilerini beklenmeyen sonuçlar.</span><span class="sxs-lookup"><span data-stu-id="2675e-107">Warning messages that contain a notification that the cmdlet is about to perform an operation that can have unexpected results.</span></span>

- <span data-ttu-id="2675e-108">Cmdlet hakkında ne kadar bilgi içeren iletileri iş ilerleme durumu raporunu, uzun süren bir işlem gerçekleştirirken tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="2675e-108">Progress report messages that contain information about how much work the cmdlet has completed when performing an operation that takes a long time.</span></span>

<span data-ttu-id="2675e-109">Cmdlet'inize yazabilirsiniz ileti sayısını veya cmdlet'inize Yazar iletilerin türünü sınırı yoktur.</span><span class="sxs-lookup"><span data-stu-id="2675e-109">There are no limits to the number of messages that your cmdlet can write or the type of messages that your cmdlet writes.</span></span> <span data-ttu-id="2675e-110">Her ileti, giriş işleme yöntemi, cmdlet'in içinde özel bir çağrı yaparak yazılır.</span><span class="sxs-lookup"><span data-stu-id="2675e-110">Each message is written by making a specific call from within the input processing method of your cmdlet.</span></span>

## <a name="the-stopproc-cmdlet"></a><span data-ttu-id="2675e-111">StopProc cmdlet'i</span><span class="sxs-lookup"><span data-stu-id="2675e-111">The StopProc Cmdlet</span></span>

<span data-ttu-id="2675e-112">Bu bölümdeki konular şunlardır:</span><span class="sxs-lookup"><span data-stu-id="2675e-112">Topics in this section include the following:</span></span>

- [<span data-ttu-id="2675e-113">Cmdlet tanımlama</span><span class="sxs-lookup"><span data-stu-id="2675e-113">Defining the Cmdlet</span></span>](#Defining-the-Cmdlet)

- [<span data-ttu-id="2675e-114">Sistem değiştirilmesi için parametreleri tanımlama</span><span class="sxs-lookup"><span data-stu-id="2675e-114">Defining Parameters for System Modification</span></span>](#Defining-Parameters-for-System-Modification)

- [<span data-ttu-id="2675e-115">Bir giriş işleme yöntemi geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="2675e-115">Overriding an Input Processing Method</span></span>](#Overriding-an-Input-Processing-Method)

- [<span data-ttu-id="2675e-116">Ayrıntılı bir ileti yazma</span><span class="sxs-lookup"><span data-stu-id="2675e-116">Writing a Verbose Message</span></span>](#Writing-a-Verbose-Message)

- [<span data-ttu-id="2675e-117">Hata ayıklama iletisi yazma</span><span class="sxs-lookup"><span data-stu-id="2675e-117">Writing a Debug Message</span></span>](#Writing-a-Debug-Message)

- [<span data-ttu-id="2675e-118">Bir uyarı iletisi yazma</span><span class="sxs-lookup"><span data-stu-id="2675e-118">Writing a Warning Message</span></span>](#Writing-a-Warning-Message)

- [<span data-ttu-id="2675e-119">Bir ilerleme iletisi yazma</span><span class="sxs-lookup"><span data-stu-id="2675e-119">Writing a Progress Message</span></span>](#Writing-a-Progress-Message)

- [<span data-ttu-id="2675e-120">Kod örneği</span><span class="sxs-lookup"><span data-stu-id="2675e-120">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="2675e-121">Nesne türleri ve biçimlendirme tanımlayın</span><span class="sxs-lookup"><span data-stu-id="2675e-121">Define Object Types and Formatting</span></span>](#Define-Object-Types-and-Formatting)

- [<span data-ttu-id="2675e-122">Cmdlet oluşturma</span><span class="sxs-lookup"><span data-stu-id="2675e-122">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="2675e-123">Sınama cmdlet'i</span><span class="sxs-lookup"><span data-stu-id="2675e-123">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a><span data-ttu-id="2675e-124">Cmdlet tanımlama</span><span class="sxs-lookup"><span data-stu-id="2675e-124">Defining the Cmdlet</span></span>

<span data-ttu-id="2675e-125">İlk adımda cmdlet'i oluşturma her zaman cmdlet adlandırma ve cmdlet uygulayan .NET sınıf bildirme.</span><span class="sxs-lookup"><span data-stu-id="2675e-125">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="2675e-126">Cmdlet'ini her türlü kullanıcı bildirimleri yöntemleri işleme kendi girişten yazabilirsiniz; Bu nedenle, genel olarak, cmdlet gerçekleştirir hangi sistem değişiklikleri belirten herhangi bir fiil kullanarak bu cmdlet adı verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2675e-126">Any sort of cmdlet can write user notifications from its input processing methods; so, in general, you can name this cmdlet using any verb that indicates what system modifications the cmdlet performs.</span></span> <span data-ttu-id="2675e-127">Onaylanan cmdlet fiilleri hakkında daha fazla bilgi için bkz: [Cmdlet fiili adları](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="2675e-127">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="2675e-128">Stop-Proc cmdlet sistem değiştirmek için tasarlanmıştır; Bu nedenle, [System.Management.Automation.Cmdletattribute](/dotnet/api/System.Management.Automation.CmdletAttribute) .NET sınıfı için bildirimi içermelidir `SupportsShouldProcess` özniteliği anahtar sözcüğü ve ayarlanması `true`.</span><span class="sxs-lookup"><span data-stu-id="2675e-128">The Stop-Proc cmdlet is designed to modify the system; therefore, the [System.Management.Automation.Cmdletattribute](/dotnet/api/System.Management.Automation.CmdletAttribute) declaration for the .NET class must include the `SupportsShouldProcess` attribute keyword and be set to `true`.</span></span>

<span data-ttu-id="2675e-129">Aşağıdaki kod bu Stop-Proc cmdlet'i sınıf için tanımıdır.</span><span class="sxs-lookup"><span data-stu-id="2675e-129">The following code is the definition for this Stop-Proc cmdlet class.</span></span> <span data-ttu-id="2675e-130">Bu tanımı hakkında daha fazla bilgi için bkz. [bir Cmdlet oluşturma sistemi değiştirir](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="2675e-130">For more information about this definition, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="2675e-131">Sistem değiştirilmesi için parametreleri tanımlama</span><span class="sxs-lookup"><span data-stu-id="2675e-131">Defining Parameters for System Modification</span></span>

<span data-ttu-id="2675e-132">Stop-Proc cmdlet, üç parametre tanımlar: `Name`, `Force`, ve `PassThru`.</span><span class="sxs-lookup"><span data-stu-id="2675e-132">The Stop-Proc cmdlet defines three parameters: `Name`, `Force`, and `PassThru`.</span></span> <span data-ttu-id="2675e-133">Bu parametreleri tanımlama hakkında daha fazla bilgi için bkz. [bir Cmdlet oluşturma sistemi değiştirir](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="2675e-133">For more information about defining these parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

<span data-ttu-id="2675e-134">Stop-Proc cmdlet'i için parametre bildirimi aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="2675e-134">Here is the parameter declaration for the Stop-Proc cmdlet.</span></span>

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

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="2675e-135">Bir giriş işleme yöntemi geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="2675e-135">Overriding an Input Processing Method</span></span>

<span data-ttu-id="2675e-136">Cmdlet'inize işleme yöntemi giriş geçersiz kılmanız gerekir, en sık olacaktır [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span><span class="sxs-lookup"><span data-stu-id="2675e-136">Your cmdlet must override an input processing method, most often it will be [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span></span> <span data-ttu-id="2675e-137">Bu Stop-Proc cmdlet geçersiz kılmalar [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) giriş işleme yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2675e-137">This Stop-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) input processing method.</span></span> <span data-ttu-id="2675e-138">Stop-Proc cmdlet bu uygulamada ayrıntılı iletileri, hata ayıklama iletileri ve uyarı iletileri yazmak için çağrı yapılır.</span><span class="sxs-lookup"><span data-stu-id="2675e-138">In this implementation of the Stop-Proc cmdlet, calls are made to write verbose messages, debug messages, and warning messages.</span></span>

> [!NOTE]
> <span data-ttu-id="2675e-139">Bu yöntem çağırması hakkında daha fazla bilgi için [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) ve [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) yöntemleri bkz [Bir Cmdlet oluşturma sistemi değiştirir](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="2675e-139">For more information about how this method calls the [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="writing-a-verbose-message"></a><span data-ttu-id="2675e-140">Ayrıntılı bir ileti yazma</span><span class="sxs-lookup"><span data-stu-id="2675e-140">Writing a Verbose Message</span></span>

<span data-ttu-id="2675e-141">[System.Management.Automation.Cmdlet.Writeverbose\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) yöntemi belirli hata koşulları için ilişkisiz genel kullanıcı düzeyi bilgileri yazmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2675e-141">The [System.Management.Automation.Cmdlet.Writeverbose\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) method is used to write general user-level information that is unrelated to specific error conditions.</span></span> <span data-ttu-id="2675e-142">Sistem Yöneticisi, sonra diğer komutların işleme devam etmek için bu bilgileri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2675e-142">The system administrator can then use that information to continue processing other commands.</span></span> <span data-ttu-id="2675e-143">Ayrıca, bu yöntem kullanılarak yazılmış herhangi bir bilgi gerektiğinde yerelleştirilmiş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2675e-143">In addition, any information written using this method should be localized as needed.</span></span>

<span data-ttu-id="2675e-144">Aşağıdaki kod bu Proc Stop cmdlet'inden iki çağrıları gösterir [System.Management.Automation.Cmdlet.Writeverbose\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) geçersiz kılmasını yönteminden [System.Management.Automation.Cmdlet.Processrecord\* ](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2675e-144">The following code from this Stop-Proc cmdlet shows two calls to the [System.Management.Automation.Cmdlet.Writeverbose\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) method from the override of the [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

```csharp
message = String.Format("Attempting to stop process \"{0}\".", name);
WriteVerbose(message);
```

```csharp
message = String.Format("Stopped process \"{0}\", pid {1}.",
                        processName, process.Id);

WriteVerbose(message);
```

## <a name="writing-a-debug-message"></a><span data-ttu-id="2675e-145">Hata ayıklama iletisi yazma</span><span class="sxs-lookup"><span data-stu-id="2675e-145">Writing a Debug Message</span></span>

<span data-ttu-id="2675e-146">[System.Management.Automation.Cmdlet.Writedebug\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) yöntemi cmdlet'inin işlemi sorun giderme için kullanılan hata ayıklama ileti yazmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2675e-146">The [System.Management.Automation.Cmdlet.Writedebug\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) method is used to write debug messages that can be used to troubleshoot the operation of the cmdlet.</span></span> <span data-ttu-id="2675e-147">İşleme yöntemi girdi çağrı yapılır.</span><span class="sxs-lookup"><span data-stu-id="2675e-147">The call is made from an input processing method.</span></span>

> [!NOTE]
> <span data-ttu-id="2675e-148">Windows PowerShell de tanımlayan bir `Debug` ayrıntılı hem de sunar ve hata ayıklama bilgilerini bir parametre.</span><span class="sxs-lookup"><span data-stu-id="2675e-148">Windows PowerShell also defines a `Debug` parameter that presents both verbose and debug information.</span></span> <span data-ttu-id="2675e-149">Cmdlet'inize bu parametreyi destekliyorsa, bu çağrı gerekmez [System.Management.Automation.Cmdlet.Writedebug\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) çağıran koddaki [System.Management.Automation.Cmdlet.Writeverbose\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose).</span><span class="sxs-lookup"><span data-stu-id="2675e-149">If your cmdlet supports this parameter, it does not need to call [System.Management.Automation.Cmdlet.Writedebug\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) in the same code that calls [System.Management.Automation.Cmdlet.Writeverbose\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose).</span></span>

<span data-ttu-id="2675e-150">Kod örnek Proc Stop cmdlet'inden aşağıdaki iki bölümü çağrıları Göster [System.Management.Automation.Cmdlet.Writedebug\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) geçersiz kılmasını yönteminden [ System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2675e-150">The following two sections of code from the sample Stop-Proc cmdlet show calls to the [System.Management.Automation.Cmdlet.Writedebug\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) method from the override of the [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

<span data-ttu-id="2675e-151">Bu hata ayıklama iletisi hemen önce yazılmış [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) çağrılır.</span><span class="sxs-lookup"><span data-stu-id="2675e-151">This debug message is written immediately before [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) is called.</span></span>

```csharp
message =
          String.Format("Acquired name for pid {0} : \"{1}\"",
                       process.Id, processName);
WriteDebug(message);
```

<span data-ttu-id="2675e-152">Bu hata ayıklama iletisi hemen önce yazılmış [System.Management.Automation.Cmdlet.Writeobject\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) çağrılır.</span><span class="sxs-lookup"><span data-stu-id="2675e-152">This debug message is written immediately before [System.Management.Automation.Cmdlet.Writeobject\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) is called.</span></span>

```csharp
message =
         String.Format("Writing process \"{0}\" to pipeline",
         processName);
WriteDebug(message);
WriteObject(process);
```

<span data-ttu-id="2675e-153">Windows PowerShell otomatik olarak yönlendirir herhangi [System.Management.Automation.Cmdlet.Writedebug\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) cmdlet'leri ve altyapı izleme çağrıları.</span><span class="sxs-lookup"><span data-stu-id="2675e-153">Windows PowerShell automatically routes any [System.Management.Automation.Cmdlet.Writedebug\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) calls to the tracing infrastructure and cmdlets.</span></span> <span data-ttu-id="2675e-154">Bu, barındırma uygulaması, bir dosya veya bir hata ayıklayıcı cmdlet'inin içinde herhangi bir ek geliştirme iş yapmak zorunda kalmadan izlenecek yöntem çağrılarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="2675e-154">This allows the method calls to be traced to the hosting application, a file, or a debugger without your having to do any extra development work within the cmdlet.</span></span> <span data-ttu-id="2675e-155">Aşağıdaki komut satırı girişi izleme işlemi uygular.</span><span class="sxs-lookup"><span data-stu-id="2675e-155">The following command-line entry implements a tracing operation.</span></span>

<span data-ttu-id="2675e-156">**PS > İzleme ifadesi stop-proc-proc.log dosya-komut stop-proc not defteri**</span><span class="sxs-lookup"><span data-stu-id="2675e-156">**PS> trace-expression stop-proc -file proc.log -command stop-proc notepad**</span></span>

## <a name="writing-a-warning-message"></a><span data-ttu-id="2675e-157">Bir uyarı iletisi yazma</span><span class="sxs-lookup"><span data-stu-id="2675e-157">Writing a Warning Message</span></span>

<span data-ttu-id="2675e-158">[System.Management.Automation.Cmdlet.Writewarning\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) yöntemi cmdlet'i bir salt okunur dosyanın üzerine beklenmeyen bir sonuç, örneğin, olabilecek bir işlem gerçekleştirmek üzere olduğunda bir uyarı yazmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2675e-158">The [System.Management.Automation.Cmdlet.Writewarning\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) method is used to write a warning when the cmdlet is about to perform an operation that might have an unexpected result, for example, overwriting a read-only file.</span></span>

<span data-ttu-id="2675e-159">Aşağıdaki kod örnek Proc Stop cmdlet'inden çağrısını gösterir [System.Management.Automation.Cmdlet.Writewarning\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) geçersiz kılmasını yönteminden [ System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2675e-159">The following code from the sample Stop-Proc cmdlet shows the call to the [System.Management.Automation.Cmdlet.Writewarning\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) method from the override of the [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

```csharp
 if (criticalProcess)
 {
   message =
             String.Format("Stopping the critical process \"{0}\".",
                           processName);
   WriteWarning(message);
} // if (criticalProcess...
```

## <a name="writing-a-progress-message"></a><span data-ttu-id="2675e-160">Bir ilerleme iletisi yazma</span><span class="sxs-lookup"><span data-stu-id="2675e-160">Writing a Progress Message</span></span>

<span data-ttu-id="2675e-161">[System.Management.Automation.Cmdlet.Writeprogress\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) işleminin tamamlanma süresi cmdlet'i işlemlerini alırken ilerleme iletilerini yazmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2675e-161">The [System.Management.Automation.Cmdlet.Writeprogress\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) is used to write progress messages when cmdlet operations take an extended amount of time to complete.</span></span> <span data-ttu-id="2675e-162">Bir çağrı [System.Management.Automation.Cmdlet.Writeprogress\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) geçirmeden bir [System.Management.Automation.Progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord) nesnesini işlemek için kullanıcı barındırma uygulamaya gönderilir.</span><span class="sxs-lookup"><span data-stu-id="2675e-162">A call to [System.Management.Automation.Cmdlet.Writeprogress\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) passes a [System.Management.Automation.Progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord) object that is sent to the hosting application for rendering to the user.</span></span>

> [!NOTE]
> <span data-ttu-id="2675e-163">Bu Stop-Proc cmdlet çağrısı içermez [System.Management.Automation.Cmdlet.Writeprogress\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2675e-163">This Stop-Proc cmdlet does not include a call to the [System.Management.Automation.Cmdlet.Writeprogress\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) method.</span></span>

<span data-ttu-id="2675e-164">Aşağıdaki kod, bir öğeyi kopyalamaya çalışırken bir cmdlet tarafından yazılmış bir ilerleme iletisi örneğidir.</span><span class="sxs-lookup"><span data-stu-id="2675e-164">The following code is an example of a progress message written by a cmdlet that is attempting to copy an item.</span></span>

```csharp
int myId = 0;
string myActivity = "Copy-item: Copying *.* to c:\abc";
string myStatus = "Copying file bar.txt";
ProgressRecord pr = new ProgressRecord(myId, myActivity, myStatus);
WriteProgress(pr);

pr.RecordType = ProgressRecordType.Completed;
WriteProgress(pr);
```

## <a name="code-sample"></a><span data-ttu-id="2675e-165">Kod örneği</span><span class="sxs-lookup"><span data-stu-id="2675e-165">Code Sample</span></span>

<span data-ttu-id="2675e-166">Tamamlanmış C# örnek kod için bkz: [StopProcessSample02 örnek](./stopprocesssample02-sample.md).</span><span class="sxs-lookup"><span data-stu-id="2675e-166">For the complete C# sample code, see [StopProcessSample02 Sample](./stopprocesssample02-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="2675e-167">Nesne türleri ve biçimlendirme tanımlayın</span><span class="sxs-lookup"><span data-stu-id="2675e-167">Define Object Types and Formatting</span></span>

<span data-ttu-id="2675e-168">Windows PowerShell cmdlet arasında .NET nesneleri kullanarak bilgileri geçirir.</span><span class="sxs-lookup"><span data-stu-id="2675e-168">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="2675e-169">Sonuç olarak, bir cmdlet kendi türü tanımlamanız gerekebilir veya başka bir cmdlet tarafından sağlanan mevcut türü genişletmek cmdlet gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="2675e-169">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="2675e-170">Yeni türleri tanımlama veya varolan türleri genişletme hakkında daha fazla bilgi için bkz. [genişletme nesne türleri ve biçimlendirme](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="2675e-170">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="2675e-171">Cmdlet oluşturma</span><span class="sxs-lookup"><span data-stu-id="2675e-171">Building the Cmdlet</span></span>

<span data-ttu-id="2675e-172">Bir cmdlet uyguladıktan sonra bunu Windows PowerShell ile bir Windows PowerShell ek bileşeni kayıtlı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2675e-172">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="2675e-173">Cmdlet'leri kaydetme hakkında daha fazla bilgi için bkz. [kaydetme cmdlet'leri ve sağlayıcıları uygulamalarını barındırmak için nasıl](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="2675e-173">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="2675e-174">Sınama cmdlet'i</span><span class="sxs-lookup"><span data-stu-id="2675e-174">Testing the Cmdlet</span></span>

<span data-ttu-id="2675e-175">Windows PowerShell ile cmdlet'ini kaydedildi, komut satırında çalıştırarak test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2675e-175">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="2675e-176">Şimdi örnek Stop-Proc cmdlet test edin.</span><span class="sxs-lookup"><span data-stu-id="2675e-176">Let's test the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="2675e-177">Komut satırından cmdlet'leri kullanma hakkında daha fazla bilgi için bkz. [Windows PowerShell ile çalışmaya başlama](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="2675e-177">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="2675e-178">Aşağıdaki komut satırı girişi Stop-Proc hata ayıklama bilgilerini yazdır "Not" adlı işlemi durdurur ve ayrıntılı bildirimleri sağlamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="2675e-178">The following command-line entry uses Stop-Proc to stop the process named "NOTEPAD", provide verbose notifications, and print debug information.</span></span>

    ```powershell
    PS> stop-proc -Name notepad -Verbose -Debug
    ```

<span data-ttu-id="2675e-179">Aşağıdaki çıktı görünür.</span><span class="sxs-lookup"><span data-stu-id="2675e-179">The following output appears.</span></span>

    ```
    VERBOSE: Attempting to stop process " notepad ".
    DEBUG: Acquired name for pid 5584 : "notepad"

    Confirm
    Continue with this operation?
    [Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend  [?] Help (default is "Y"): Y

    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (5584)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    VERBOSE: Stopped process "notepad", pid 5584.
    ```

## <a name="see-also"></a><span data-ttu-id="2675e-180">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="2675e-180">See Also</span></span>

[<span data-ttu-id="2675e-181">Sistem değiştiren bir Cmdlet oluşturma</span><span class="sxs-lookup"><span data-stu-id="2675e-181">Create a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="2675e-182">Bir Windows PowerShell cmdlet'i oluşturma</span><span class="sxs-lookup"><span data-stu-id="2675e-182">How to Create a Windows PowerShell Cmdlet</span></span>](http://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[<span data-ttu-id="2675e-183">Nesne türlerini genişletme ve biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="2675e-183">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="2675e-184">Cmdlet, sağlayıcılar kaydetmek ve uygulamaları barındırmak nasıl</span><span class="sxs-lookup"><span data-stu-id="2675e-184">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="2675e-185">Windows PowerShell SDK'sı</span><span class="sxs-lookup"><span data-stu-id="2675e-185">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
