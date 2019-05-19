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
ms.openlocfilehash: 138c6a43937e72fffaa2a09243e500e9822e6111
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854933"
---
# <a name="adding-user-messages-to-your-cmdlet"></a><span data-ttu-id="dd4b8-102">Cmdlet’inize Kullanıcı İletileri Ekleme</span><span class="sxs-lookup"><span data-stu-id="dd4b8-102">Adding User Messages to Your Cmdlet</span></span>

<span data-ttu-id="dd4b8-103">Cmdlet'leri, kullanıcı için Windows PowerShell çalışma zamanı tarafından görüntülenebilen iletileri çeşitli türlerde yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dd4b8-103">Cmdlets can write several kinds of messages that can be displayed to the user by the Windows PowerShell runtime.</span></span> <span data-ttu-id="dd4b8-104">Bu iletiler, aşağıdaki türleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="dd4b8-104">These messages include the following types:</span></span>

- <span data-ttu-id="dd4b8-105">Genel kullanıcı bilgilerini içeren ayrıntılı iletiler.</span><span class="sxs-lookup"><span data-stu-id="dd4b8-105">Verbose messages that contain general user information.</span></span>

- <span data-ttu-id="dd4b8-106">Sorun giderme bilgilerini içeren bir ileti hata ayıklayın.</span><span class="sxs-lookup"><span data-stu-id="dd4b8-106">Debug messages that contain troubleshooting information.</span></span>

- <span data-ttu-id="dd4b8-107">İlgili olabilecek bir işlemi gerçekleştirmek için cmdlet, bir bildirimi içeren bir uyarı iletilerini beklenmeyen sonuçlar.</span><span class="sxs-lookup"><span data-stu-id="dd4b8-107">Warning messages that contain a notification that the cmdlet is about to perform an operation that can have unexpected results.</span></span>

- <span data-ttu-id="dd4b8-108">Cmdlet hakkında ne kadar bilgi içeren iletileri iş ilerleme durumu raporunu, uzun süren bir işlem gerçekleştirirken tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="dd4b8-108">Progress report messages that contain information about how much work the cmdlet has completed when performing an operation that takes a long time.</span></span>

<span data-ttu-id="dd4b8-109">Cmdlet'inize yazabilirsiniz ileti sayısını veya cmdlet'inize Yazar iletilerin türünü sınırı yoktur.</span><span class="sxs-lookup"><span data-stu-id="dd4b8-109">There are no limits to the number of messages that your cmdlet can write or the type of messages that your cmdlet writes.</span></span> <span data-ttu-id="dd4b8-110">Her ileti, giriş işleme yöntemi, cmdlet'in içinde özel bir çağrı yaparak yazılır.</span><span class="sxs-lookup"><span data-stu-id="dd4b8-110">Each message is written by making a specific call from within the input processing method of your cmdlet.</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="dd4b8-111">Cmdlet tanımlama</span><span class="sxs-lookup"><span data-stu-id="dd4b8-111">Defining the Cmdlet</span></span>

<span data-ttu-id="dd4b8-112">İlk adımda cmdlet'i oluşturma her zaman cmdlet adlandırma ve cmdlet uygulayan .NET sınıf bildirme.</span><span class="sxs-lookup"><span data-stu-id="dd4b8-112">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="dd4b8-113">Cmdlet'ini her türlü kullanıcı bildirimleri yöntemleri işleme kendi girişten yazabilirsiniz; Bu nedenle, genel olarak, cmdlet gerçekleştirir hangi sistem değişiklikleri belirten herhangi bir fiil kullanarak bu cmdlet adı verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dd4b8-113">Any sort of cmdlet can write user notifications from its input processing methods; so, in general, you can name this cmdlet using any verb that indicates what system modifications the cmdlet performs.</span></span> <span data-ttu-id="dd4b8-114">Onaylanan cmdlet fiilleri hakkında daha fazla bilgi için bkz: [Cmdlet fiili adları](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="dd4b8-114">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="dd4b8-115">Stop-Proc cmdlet sistem değiştirmek için tasarlanmıştır; Bu nedenle, [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) .NET sınıfı için bildirimi içermelidir `SupportsShouldProcess` özniteliği anahtar sözcüğü ve ayarlanması `true`.</span><span class="sxs-lookup"><span data-stu-id="dd4b8-115">The Stop-Proc cmdlet is designed to modify the system; therefore, the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) declaration for the .NET class must include the `SupportsShouldProcess` attribute keyword and be set to `true`.</span></span>

<span data-ttu-id="dd4b8-116">Aşağıdaki kod bu Stop-Proc cmdlet'i sınıf için tanımıdır.</span><span class="sxs-lookup"><span data-stu-id="dd4b8-116">The following code is the definition for this Stop-Proc cmdlet class.</span></span> <span data-ttu-id="dd4b8-117">Bu tanımı hakkında daha fazla bilgi için bkz. [bir Cmdlet oluşturma sistemi değiştirir](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="dd4b8-117">For more information about this definition, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="dd4b8-118">Sistem değiştirilmesi için parametreleri tanımlama</span><span class="sxs-lookup"><span data-stu-id="dd4b8-118">Defining Parameters for System Modification</span></span>

<span data-ttu-id="dd4b8-119">Stop-Proc cmdlet, üç parametre tanımlar: `Name`, `Force`, ve `PassThru`.</span><span class="sxs-lookup"><span data-stu-id="dd4b8-119">The Stop-Proc cmdlet defines three parameters: `Name`, `Force`, and `PassThru`.</span></span> <span data-ttu-id="dd4b8-120">Bu parametreleri tanımlama hakkında daha fazla bilgi için bkz. [bir Cmdlet oluşturma sistemi değiştirir](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="dd4b8-120">For more information about defining these parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

<span data-ttu-id="dd4b8-121">Stop-Proc cmdlet'i için parametre bildirimi aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="dd4b8-121">Here is the parameter declaration for the Stop-Proc cmdlet.</span></span>

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

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="dd4b8-122">Bir giriş işleme yöntemi geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="dd4b8-122">Overriding an Input Processing Method</span></span>

<span data-ttu-id="dd4b8-123">Cmdlet'inize işleme yöntemi giriş geçersiz kılmanız gerekir, en sık olacaktır [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span><span class="sxs-lookup"><span data-stu-id="dd4b8-123">Your cmdlet must override an input processing method, most often it will be [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span></span> <span data-ttu-id="dd4b8-124">Bu Stop-Proc cmdlet geçersiz kılmalar [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) giriş işleme yöntemi.</span><span class="sxs-lookup"><span data-stu-id="dd4b8-124">This Stop-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) input processing method.</span></span> <span data-ttu-id="dd4b8-125">Stop-Proc cmdlet bu uygulamada ayrıntılı iletileri, hata ayıklama iletileri ve uyarı iletileri yazmak için çağrı yapılır.</span><span class="sxs-lookup"><span data-stu-id="dd4b8-125">In this implementation of the Stop-Proc cmdlet, calls are made to write verbose messages, debug messages, and warning messages.</span></span>

> [!NOTE]
> <span data-ttu-id="dd4b8-126">Bu yöntem çağırması hakkında daha fazla bilgi için [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) ve [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) yöntemleri bkz [Bir Cmdlet oluşturma sistemi değiştirir](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="dd4b8-126">For more information about how this method calls the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="writing-a-verbose-message"></a><span data-ttu-id="dd4b8-127">Ayrıntılı bir ileti yazma</span><span class="sxs-lookup"><span data-stu-id="dd4b8-127">Writing a Verbose Message</span></span>

<span data-ttu-id="dd4b8-128">[System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) yöntemi belirli hata koşulları için ilişkisiz genel kullanıcı düzeyi bilgileri yazmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dd4b8-128">The [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) method is used to write general user-level information that is unrelated to specific error conditions.</span></span> <span data-ttu-id="dd4b8-129">Sistem Yöneticisi, sonra diğer komutların işleme devam etmek için bu bilgileri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dd4b8-129">The system administrator can then use that information to continue processing other commands.</span></span> <span data-ttu-id="dd4b8-130">Ayrıca, bu yöntem kullanılarak yazılmış herhangi bir bilgi gerektiğinde yerelleştirilmiş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dd4b8-130">In addition, any information written using this method should be localized as needed.</span></span>

<span data-ttu-id="dd4b8-131">Aşağıdaki kod bu Proc Stop cmdlet'inden iki çağrıları gösterir [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) geçersiz kılmasını yönteminden [System.Management.Automation.Cmdlet.ProcessRecord ](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="dd4b8-131">The following code from this Stop-Proc cmdlet shows two calls to the [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

```csharp
message = String.Format("Attempting to stop process \"{0}\".", name);
WriteVerbose(message);
```

```csharp
message = String.Format("Stopped process \"{0}\", pid {1}.",
                        processName, process.Id);

WriteVerbose(message);
```

## <a name="writing-a-debug-message"></a><span data-ttu-id="dd4b8-132">Hata ayıklama iletisi yazma</span><span class="sxs-lookup"><span data-stu-id="dd4b8-132">Writing a Debug Message</span></span>

<span data-ttu-id="dd4b8-133">[System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) yöntemi cmdlet'inin işlemi sorun giderme için kullanılan hata ayıklama ileti yazmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dd4b8-133">The [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) method is used to write debug messages that can be used to troubleshoot the operation of the cmdlet.</span></span> <span data-ttu-id="dd4b8-134">İşleme yöntemi girdi çağrı yapılır.</span><span class="sxs-lookup"><span data-stu-id="dd4b8-134">The call is made from an input processing method.</span></span>

> [!NOTE]
> <span data-ttu-id="dd4b8-135">Windows PowerShell de tanımlayan bir `Debug` ayrıntılı hem de sunar ve hata ayıklama bilgilerini bir parametre.</span><span class="sxs-lookup"><span data-stu-id="dd4b8-135">Windows PowerShell also defines a `Debug` parameter that presents both verbose and debug information.</span></span> <span data-ttu-id="dd4b8-136">Cmdlet'inize bu parametreyi destekliyorsa, bu çağrı gerekmez [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) çağıran koddaki [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) .</span><span class="sxs-lookup"><span data-stu-id="dd4b8-136">If your cmdlet supports this parameter, it does not need to call [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) in the same code that calls [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose).</span></span>

<span data-ttu-id="dd4b8-137">Kod örnek Proc Stop cmdlet'inden aşağıdaki iki bölümü çağrıları Göster [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) geçersiz kılmasını yönteminden [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="dd4b8-137">The following two sections of code from the sample Stop-Proc cmdlet show calls to the [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

<span data-ttu-id="dd4b8-138">Bu hata ayıklama iletisi hemen önce yazılmış [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) çağrılır.</span><span class="sxs-lookup"><span data-stu-id="dd4b8-138">This debug message is written immediately before [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) is called.</span></span>

```csharp
message =
          String.Format("Acquired name for pid {0} : \"{1}\"",
                       process.Id, processName);
WriteDebug(message);
```

<span data-ttu-id="dd4b8-139">Bu hata ayıklama iletisi hemen önce yazılmış [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) çağrılır.</span><span class="sxs-lookup"><span data-stu-id="dd4b8-139">This debug message is written immediately before [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) is called.</span></span>

```csharp
message =
         String.Format("Writing process \"{0}\" to pipeline",
         processName);
WriteDebug(message);
WriteObject(process);
```

<span data-ttu-id="dd4b8-140">Windows PowerShell otomatik olarak yönlendirir herhangi [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) cmdlet'leri ve altyapı izleme çağrıları.</span><span class="sxs-lookup"><span data-stu-id="dd4b8-140">Windows PowerShell automatically routes any [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) calls to the tracing infrastructure and cmdlets.</span></span> <span data-ttu-id="dd4b8-141">Bu, barındırma uygulaması, bir dosya veya bir hata ayıklayıcı cmdlet'inin içinde herhangi bir ek geliştirme iş yapmak zorunda kalmadan izlenecek yöntem çağrılarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="dd4b8-141">This allows the method calls to be traced to the hosting application, a file, or a debugger without your having to do any extra development work within the cmdlet.</span></span> <span data-ttu-id="dd4b8-142">Aşağıdaki komut satırı girişi izleme işlemi uygular.</span><span class="sxs-lookup"><span data-stu-id="dd4b8-142">The following command-line entry implements a tracing operation.</span></span>

<span data-ttu-id="dd4b8-143">**PS > İzleme ifadesi stop-proc-proc.log dosya-komut stop-proc not defteri**</span><span class="sxs-lookup"><span data-stu-id="dd4b8-143">**PS> trace-expression stop-proc -file proc.log -command stop-proc notepad**</span></span>

## <a name="writing-a-warning-message"></a><span data-ttu-id="dd4b8-144">Bir uyarı iletisi yazma</span><span class="sxs-lookup"><span data-stu-id="dd4b8-144">Writing a Warning Message</span></span>

<span data-ttu-id="dd4b8-145">[System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) yöntemi cmdlet'i bir salt okunur dosyanın üzerine beklenmeyen bir sonuç, örneğin, olabilecek bir işlem gerçekleştirmek üzere olduğunda bir uyarı yazmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dd4b8-145">The [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) method is used to write a warning when the cmdlet is about to perform an operation that might have an unexpected result, for example, overwriting a read-only file.</span></span>

<span data-ttu-id="dd4b8-146">Aşağıdaki kod örnek Proc Stop cmdlet'inden çağrısını gösterir [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) geçersiz kılmasını yönteminden [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="dd4b8-146">The following code from the sample Stop-Proc cmdlet shows the call to the [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

```csharp
 if (criticalProcess)
 {
   message =
             String.Format("Stopping the critical process \"{0}\".",
                           processName);
   WriteWarning(message);
} // if (criticalProcess...
```

## <a name="writing-a-progress-message"></a><span data-ttu-id="dd4b8-147">Bir ilerleme iletisi yazma</span><span class="sxs-lookup"><span data-stu-id="dd4b8-147">Writing a Progress Message</span></span>

<span data-ttu-id="dd4b8-148">[System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) işleminin tamamlanma süresi cmdlet'i işlemlerini alırken ilerleme iletilerini yazmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dd4b8-148">The [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) is used to write progress messages when cmdlet operations take an extended amount of time to complete.</span></span> <span data-ttu-id="dd4b8-149">Bir çağrı [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) geçirmeden bir [System.Management.Automation.Progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord) nesnesini işlemek için kullanıcı barındırma uygulamaya gönderilir.</span><span class="sxs-lookup"><span data-stu-id="dd4b8-149">A call to [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) passes a [System.Management.Automation.Progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord) object that is sent to the hosting application for rendering to the user.</span></span>

> [!NOTE]
> <span data-ttu-id="dd4b8-150">Bu Stop-Proc cmdlet çağrısı içermez [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="dd4b8-150">This Stop-Proc cmdlet does not include a call to the [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) method.</span></span>

<span data-ttu-id="dd4b8-151">Aşağıdaki kod, bir öğeyi kopyalamaya çalışırken bir cmdlet tarafından yazılmış bir ilerleme iletisi örneğidir.</span><span class="sxs-lookup"><span data-stu-id="dd4b8-151">The following code is an example of a progress message written by a cmdlet that is attempting to copy an item.</span></span>

```csharp
int myId = 0;
string myActivity = "Copy-item: Copying *.* to c:\abc";
string myStatus = "Copying file bar.txt";
ProgressRecord pr = new ProgressRecord(myId, myActivity, myStatus);
WriteProgress(pr);

pr.RecordType = ProgressRecordType.Completed;
WriteProgress(pr);
```

## <a name="code-sample"></a><span data-ttu-id="dd4b8-152">Kod örneği</span><span class="sxs-lookup"><span data-stu-id="dd4b8-152">Code Sample</span></span>

<span data-ttu-id="dd4b8-153">Tamamlanmış C# örnek kod için bkz: [StopProcessSample02 örnek](./stopprocesssample02-sample.md).</span><span class="sxs-lookup"><span data-stu-id="dd4b8-153">For the complete C# sample code, see [StopProcessSample02 Sample](./stopprocesssample02-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="dd4b8-154">Nesne türleri ve biçimlendirme tanımlayın</span><span class="sxs-lookup"><span data-stu-id="dd4b8-154">Define Object Types and Formatting</span></span>

<span data-ttu-id="dd4b8-155">Windows PowerShell cmdlet arasında .NET nesneleri kullanarak bilgileri geçirir.</span><span class="sxs-lookup"><span data-stu-id="dd4b8-155">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="dd4b8-156">Sonuç olarak, bir cmdlet kendi türü tanımlamanız gerekebilir veya başka bir cmdlet tarafından sağlanan mevcut türü genişletmek cmdlet gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="dd4b8-156">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="dd4b8-157">Yeni türleri tanımlama veya varolan türleri genişletme hakkında daha fazla bilgi için bkz. [genişletme nesne türleri ve biçimlendirme](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="dd4b8-157">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="dd4b8-158">Cmdlet oluşturma</span><span class="sxs-lookup"><span data-stu-id="dd4b8-158">Building the Cmdlet</span></span>

<span data-ttu-id="dd4b8-159">Bir cmdlet uyguladıktan sonra bunu Windows PowerShell ile bir Windows PowerShell ek bileşeni kayıtlı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="dd4b8-159">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="dd4b8-160">Cmdlet'leri kaydetme hakkında daha fazla bilgi için bkz. [kaydetme cmdlet'leri ve sağlayıcıları uygulamalarını barındırmak için nasıl](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="dd4b8-160">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="dd4b8-161">Sınama cmdlet'i</span><span class="sxs-lookup"><span data-stu-id="dd4b8-161">Testing the Cmdlet</span></span>

<span data-ttu-id="dd4b8-162">Windows PowerShell ile cmdlet'ini kaydedildi, komut satırında çalıştırarak test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dd4b8-162">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="dd4b8-163">Şimdi örnek Stop-Proc cmdlet test edin.</span><span class="sxs-lookup"><span data-stu-id="dd4b8-163">Let's test the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="dd4b8-164">Komut satırından cmdlet'leri kullanma hakkında daha fazla bilgi için bkz. [Windows PowerShell ile çalışmaya başlama](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="dd4b8-164">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="dd4b8-165">Aşağıdaki komut satırı girişi Stop-Proc hata ayıklama bilgilerini yazdır "Not" adlı işlemi durdurur ve ayrıntılı bildirimleri sağlamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="dd4b8-165">The following command-line entry uses Stop-Proc to stop the process named "NOTEPAD", provide verbose notifications, and print debug information.</span></span>

    ```powershell
    PS> stop-proc -Name notepad -Verbose -Debug
    ```

<span data-ttu-id="dd4b8-166">Aşağıdaki çıktı görünür.</span><span class="sxs-lookup"><span data-stu-id="dd4b8-166">The following output appears.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="dd4b8-167">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="dd4b8-167">See Also</span></span>

[<span data-ttu-id="dd4b8-168">Sistem değiştiren bir Cmdlet oluşturma</span><span class="sxs-lookup"><span data-stu-id="dd4b8-168">Create a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="dd4b8-169">Bir Windows PowerShell cmdlet'i oluşturma</span><span class="sxs-lookup"><span data-stu-id="dd4b8-169">How to Create a Windows PowerShell Cmdlet</span></span>](http://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[<span data-ttu-id="dd4b8-170">Nesne türlerini genişletme ve biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="dd4b8-170">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="dd4b8-171">Cmdlet, sağlayıcılar kaydetmek ve uygulamaları barındırmak nasıl</span><span class="sxs-lookup"><span data-stu-id="dd4b8-171">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="dd4b8-172">Windows PowerShell SDK'sı</span><span class="sxs-lookup"><span data-stu-id="dd4b8-172">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
