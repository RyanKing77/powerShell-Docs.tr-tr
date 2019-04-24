---
title: Sonlandırıcı olmayan hata raporlama, cmdlet'e ekleme | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2a1531a-a92a-4606-9d54-c5df80d34f33
caps.latest.revision: 8
ms.openlocfilehash: 3741982f81efa04d8fe7ab448fba5f2fdf4b0c01
ms.sourcegitcommit: f4bd4e116e22c8b5bfcb61680a7c42e58b4da93e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59984247"
---
# <a name="adding-non-terminating-error-reporting-to-your-cmdlet"></a><span data-ttu-id="e7fca-102">Cmdlet’inize Sonlandırıcı Olmayan Hata Raporlama Ekleme</span><span class="sxs-lookup"><span data-stu-id="e7fca-102">Adding Non-Terminating Error Reporting to Your Cmdlet</span></span>

<span data-ttu-id="e7fca-103">Cmdlet'leri rapor olmak üzere sonlandırmasız hatalar çağırarak [System.Management.Automation.Cmdlet.WriteError][] yöntemi ve geçerli giriş nesnesi ya da daha fazla gelen çalışmaya devam işlem hattı nesneleri.</span><span class="sxs-lookup"><span data-stu-id="e7fca-103">Cmdlets can report nonterminating errors by calling the [System.Management.Automation.Cmdlet.WriteError][] method and still continue to operate on the current input object or on further incoming pipeline objects.</span></span>
<span data-ttu-id="e7fca-104">Bu bölümde, giriş işleme yöntemlerinden olmak üzere sonlandırmasız hatalar raporları bir cmdlet oluşturma açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e7fca-104">This section explains how to create a cmdlet that reports nonterminating errors from its input processing methods.</span></span>

<span data-ttu-id="e7fca-105">Olmak üzere sonlandırmasız hatalar (aynı zamanda için Sonlandırıcı hataları), cmdlet geçmesi gereken bir [System.Management.Automation.ErrorRecord][] hatayı tanımlayan nesne.</span><span class="sxs-lookup"><span data-stu-id="e7fca-105">For nonterminating errors (as well as terminating errors), the cmdlet must pass an [System.Management.Automation.ErrorRecord][] object identifying the error.</span></span>
<span data-ttu-id="e7fca-106">Her hata kaydı "hata tanımlayıcı" adı verilen benzersiz bir dize tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="e7fca-106">Each error record is identified by a unique string called the "error identifier".</span></span>
<span data-ttu-id="e7fca-107">Tanımlayıcı yanı sıra her bir hata kategorisi tarafından tanımlanan sabitleri tarafından belirtilen bir [System.Management.Automation.ErrorCategory][] sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="e7fca-107">In addition to the identifier, the category of each error is specified by constants defined by a [System.Management.Automation.ErrorCategory][] enumeration.</span></span>
<span data-ttu-id="e7fca-108">Kullanıcı ayarlayarak kategorilerine göre hataları görüntüleyebilirsiniz `$ErrorView` "CategoryView" değişkenini.</span><span class="sxs-lookup"><span data-stu-id="e7fca-108">The user can view errors based on their category by setting the `$ErrorView` variable to "CategoryView".</span></span>

<span data-ttu-id="e7fca-109">Hata kaydı hakkında daha fazla bilgi için bkz: [Windows PowerShell hata kaydı](./windows-powershell-error-records.md).</span><span class="sxs-lookup"><span data-stu-id="e7fca-109">For more information about error records, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="e7fca-110">Cmdlet tanımlama</span><span class="sxs-lookup"><span data-stu-id="e7fca-110">Defining the Cmdlet</span></span>

<span data-ttu-id="e7fca-111">İlk adımda cmdlet'i oluşturma her zaman cmdlet adlandırma ve cmdlet uygulayan .NET sınıf bildirme.</span><span class="sxs-lookup"><span data-stu-id="e7fca-111">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span>
<span data-ttu-id="e7fca-112">Bu cmdlet, burada seçilen fiil adı "Get", bu nedenle işlem bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="e7fca-112">This cmdlet retrieves process information, so the verb name chosen here is "Get".</span></span>
<span data-ttu-id="e7fca-113">(Komut satırı girişi neredeyse her türlü bilgi alma özelliğine sahip olan cmdlet işleyebilir.) Onaylanan cmdlet fiilleri hakkında daha fazla bilgi için bkz: [Cmdlet fiili adları](approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="e7fca-113">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="e7fca-114">Bu Get-Proc cmdlet tanımı aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e7fca-114">The following is the definition for this Get-Proc cmdlet.</span></span>
<span data-ttu-id="e7fca-115">Bu tanımın ayrıntıları verilir [oluşturma bilgisayarınızı ilk Cmdlet](creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="e7fca-115">Details of this definition are given in [Creating Your First Cmdlet](creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-parameters"></a><span data-ttu-id="e7fca-116">Parametreleri tanımlama</span><span class="sxs-lookup"><span data-stu-id="e7fca-116">Defining Parameters</span></span>

<span data-ttu-id="e7fca-117">Gerekirse, cmdlet'inize girişini işleme parametrelerini tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e7fca-117">If necessary, your cmdlet must define parameters for processing input.</span></span>
<span data-ttu-id="e7fca-118">Bu Get-Proc cmdlet tanımlayan bir **adı** açıklandığı parametresi [parametreler, işlem komut satırı girişi ekleme](adding-parameters-that-process-command-line-input.md).</span><span class="sxs-lookup"><span data-stu-id="e7fca-118">This Get-Proc cmdlet defines a **Name** parameter as described in [Adding Parameters that Process Command-Line Input](adding-parameters-that-process-command-line-input.md).</span></span>

<span data-ttu-id="e7fca-119">Parametre bildirimi için işte **adı** bu Get-Proc cmdlet parametresi.</span><span class="sxs-lookup"><span data-stu-id="e7fca-119">Here is the parameter declaration for the **Name** parameter of this Get-Proc cmdlet.</span></span>

```csharp
[Parameter(
           Position = 0,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true
)]
[ValidateNotNullOrEmpty]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;
```

```vb
<Parameter(Position:=0, ValueFromPipeline:=True, _
ValueFromPipelineByPropertyName:=True), ValidateNotNullOrEmpty()> _
Public Property Name() As String()
    Get
        Return processNames
    End Get

    Set(ByVal value As String())
        processNames = value
    End Set

End Property
```

## <a name="overriding-input-processing-methods"></a><span data-ttu-id="e7fca-120">Geçersiz kılma yöntemleri işleme giriş</span><span class="sxs-lookup"><span data-stu-id="e7fca-120">Overriding Input Processing Methods</span></span>

<span data-ttu-id="e7fca-121">Tüm cmdlet'ler tarafından sağlanan yöntemleri işleme giriş en az biri geçersiz kılmanız gerekir [System.Management.Automation.Cmdlet][] sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e7fca-121">All cmdlets must override at least one of the input processing methods provided by the [System.Management.Automation.Cmdlet][] class.</span></span>
<span data-ttu-id="e7fca-122">Bu yöntemleri ele alınmıştır [oluşturma bilgisayarınızı ilk Cmdlet](creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="e7fca-122">These methods are discussed in [Creating Your First Cmdlet](creating-a-cmdlet-without-parameters.md).</span></span>

> [!NOTE]
> <span data-ttu-id="e7fca-123">Cmdlet'inize her bir kayıt olarak bağımsız olarak işlemelidir.</span><span class="sxs-lookup"><span data-stu-id="e7fca-123">Your cmdlet should handle each record as independently as possible.</span></span>

<span data-ttu-id="e7fca-124">Bu Get-Proc cmdlet geçersiz kılmalar [System.Management.Automation.Cmdlet.ProcessRecord][] işlemek için gereken yöntemini **adı** kullanıcı veya bir betik tarafından sağlanan giriş parametresi.</span><span class="sxs-lookup"><span data-stu-id="e7fca-124">This Get-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord][] method to handle the **Name** parameter for input provided by the user or a script.</span></span>
<span data-ttu-id="e7fca-125">Adsız sağlanırsa, bu yöntem işlemleri her istenen işlem adı veya tüm işlemler için alırsınız.</span><span class="sxs-lookup"><span data-stu-id="e7fca-125">This method will get the processes for each requested process name or all processes if no name is provided.</span></span>
<span data-ttu-id="e7fca-126">Bu geçersiz kılma ayrıntıları verilir [oluşturma bilgisayarınızı ilk Cmdlet](creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="e7fca-126">Details of this override are given in [Creating Your First Cmdlet](creating-a-cmdlet-without-parameters.md).</span></span>

### <a name="things-to-remember-when-reporting-errors"></a><span data-ttu-id="e7fca-127">Hata raporlama, bunları unutmayın</span><span class="sxs-lookup"><span data-stu-id="e7fca-127">Things to Remember When Reporting Errors</span></span>

<span data-ttu-id="e7fca-128">[System.Management.Automation.ErrorRecord][] nesne yazılırken bir hata özel durum özellikleri temel alınarak gerektirdiğinde cmdlet geçirir.</span><span class="sxs-lookup"><span data-stu-id="e7fca-128">The [System.Management.Automation.ErrorRecord][] object that the cmdlet passes when writing an error requires an exception at its core.</span></span>
<span data-ttu-id="e7fca-129">Kullanılacak özel durum belirlerken .NET yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="e7fca-129">Follow the .NET guidelines when determining the exception to use.</span></span>
<span data-ttu-id="e7fca-130">Temel olarak, hata anlamsal olarak var olan bir özel durum ile aynı ise, cmdlet kullanın veya bu özel durumdan türetilen.</span><span class="sxs-lookup"><span data-stu-id="e7fca-130">Basically, if the error is semantically the same as an existing exception, the cmdlet should use or derive from that exception.</span></span>
<span data-ttu-id="e7fca-131">Aksi takdirde, yeni özel durum ya da doğrudan özel durum hiyerarşisi türetilmelidir [System.Exception][] sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e7fca-131">Otherwise, it should derive a new exception or exception hierarchy directly from the [System.Exception][] class.</span></span>

<span data-ttu-id="e7fca-132">Hata tanımlayıcıları (ErrorRecord sınıfın FullyQualifiedErrorId özelliği erişilir) oluştururken aşağıdakileri göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="e7fca-132">When creating error identifiers (accessed through the FullyQualifiedErrorId property of the ErrorRecord class) keep the following in mind.</span></span>

- <span data-ttu-id="e7fca-133">Tanılama amacıyla, böylelikle tam tanımlayıcı incelerken, hangi hata belirleyebilirsiniz ve hata geldiği burada hedeflenen kullanım dizeleri.</span><span class="sxs-lookup"><span data-stu-id="e7fca-133">Use strings that are targeted for diagnostic purposes so that when inspecting the fully qualified identifier you can determine what the error is and where the error came from.</span></span>

- <span data-ttu-id="e7fca-134">Biçimlendirilmiş tam hata tanımlayıcısı şu şekilde olabilir.</span><span class="sxs-lookup"><span data-stu-id="e7fca-134">A well formed fully qualified error identifier might be as follows.</span></span>

`CommandNotFoundException,Microsoft.PowerShell.Commands.GetCommandCommand`

<span data-ttu-id="e7fca-135">Önceki örnekte, hata tanımlayıcı (ilk belirteç) hatanın ne olduğunu belirler ve kalan bölümü hata nereden geldiğini belirten olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="e7fca-135">Notice that in the previous example, the error identifier (the first token) designates what the error is and the remaining part indicates where the error came from.</span></span>

- <span data-ttu-id="e7fca-136">Daha karmaşık senaryolarda, inceleme üzerinde ayrıştırılabilir bir nokta ayrılmış belirteç hata tanımlayıcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="e7fca-136">For more complex scenarios, the error identifier can be a dot separated token that can be parsed on inspection.</span></span>
  <span data-ttu-id="e7fca-137">Bu hata tanımlayıcısı ve hata kategorisi yanı sıra hata tanımlayıcı kısımlarına çok dal sağlar.</span><span class="sxs-lookup"><span data-stu-id="e7fca-137">This allows you too branch on the parts of the error identifier as well as the error identifier and error category.</span></span>

<span data-ttu-id="e7fca-138">Cmdlet'i belirli hata tanımlayıcıları farklı kod yolları atamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e7fca-138">The cmdlet should assign specific error identifiers to different code paths.</span></span>
<span data-ttu-id="e7fca-139">Hata tanımlayıcıların ataması için aşağıdaki bilgileri unutmayın:</span><span class="sxs-lookup"><span data-stu-id="e7fca-139">Keep the following information in mind for assignment of error identifiers:</span></span>

- <span data-ttu-id="e7fca-140">Hata tanımlayıcı cmdlet'i süresince sabit kalması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e7fca-140">An error identifier should remain constant throughout the cmdlet life cycle.</span></span>
  <span data-ttu-id="e7fca-141">Hata tanımlayıcı cmdlet'i sürümleri arasında semantiği değiştirmeyin.</span><span class="sxs-lookup"><span data-stu-id="e7fca-141">Do not change the semantics of an error identifier between cmdlet versions.</span></span>

- <span data-ttu-id="e7fca-142">Bildirilen hata tersely karşılık gelen hata tanımlayıcı için metin kullanın.</span><span class="sxs-lookup"><span data-stu-id="e7fca-142">Use text for an error identifier that tersely corresponds to the error being reported.</span></span>
  <span data-ttu-id="e7fca-143">Boşluk veya noktalama işareti kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="e7fca-143">Do not use white space or punctuation.</span></span>

- <span data-ttu-id="e7fca-144">Tekrarlanabilir hata tanımlayıcılar oluşturma cmdlet'inize vardır.</span><span class="sxs-lookup"><span data-stu-id="e7fca-144">Have your cmdlet generate only error identifiers that are reproducible.</span></span>
  <span data-ttu-id="e7fca-145">Örneğin, bir işlem tanımlayıcısını içeren bir tanımlayıcı üretmemelidir.</span><span class="sxs-lookup"><span data-stu-id="e7fca-145">For example, it should not generate an identifier that includes a process identifier.</span></span>
  <span data-ttu-id="e7fca-146">Yalnızca bunlar aynı sorunu yaşayan başka kullanıcılar tarafından görülen tanımlayıcıları karşılık hata tanımlayıcılar bir kullanıcı için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="e7fca-146">Error identifiers are useful to a user only when they correspond to identifiers that are seen by other users experiencing the same problem.</span></span>

<span data-ttu-id="e7fca-147">İşlenmeyen özel durumlar aşağıdaki durumlarda PowerShell tarafından yakalanan değil:</span><span class="sxs-lookup"><span data-stu-id="e7fca-147">Unhandled exceptions are not caught by PowerShell in the following conditions:</span></span>

- <span data-ttu-id="e7fca-148">Bir cmdlet yeni bir iş parçacığı ve iş parçacığı işlenmeyen bir özel durum oluşturduğunda çalışan kodu oluşturur, PowerShell hata yakalayamaz ve işlemini sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="e7fca-148">If a cmdlet creates a new thread and code running in that thread throws an unhandled exception, PowerShell will not catch the error and will terminate the process.</span></span>

- <span data-ttu-id="e7fca-149">Bir nesne işlenmeyen bir özel durum neden kodu yok Edicisi veya atma yöntemleri varsa, PowerShell hata yakalayamaz ve işlemini sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="e7fca-149">If an object has code in its destructor or Dispose methods that causes an unhandled exception, PowerShell will not catch the error and will terminate the process.</span></span>

## <a name="reporting-nonterminating-errors"></a><span data-ttu-id="e7fca-150">Raporlama olmak üzere Sonlandırmasız hatalar</span><span class="sxs-lookup"><span data-stu-id="e7fca-150">Reporting Nonterminating Errors</span></span>

<span data-ttu-id="e7fca-151">Çıkış akışı kullanarak, yöntemleri işleme giriş herhangi biri olmak üzere sonlandırmasız bir hata rapor edebilirsiniz [System.Management.Automation.Cmdlet.WriteError][] yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e7fca-151">Any one of the input processing methods can report a nonterminating error to the output stream using the [System.Management.Automation.Cmdlet.WriteError][] method.</span></span>

<span data-ttu-id="e7fca-152">İşte bir kod örneği bu Get-Proc cmdlet'inden yapılan çağrıyı gösterir [System.Management.Automation.Cmdlet.WriteError][] gelen geçersiz kılmasını içinde [System.Management.Automation.Cmdlet.ProcessRecord][] yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e7fca-152">Here is a code example from this Get-Proc cmdlet that illustrates the call to [System.Management.Automation.Cmdlet.WriteError][] from within the override of the [System.Management.Automation.Cmdlet.ProcessRecord][] method.</span></span>
<span data-ttu-id="e7fca-153">Cmdlet'i bir işlem için belirtilen işlem tanımlayıcısı bulamazsa, bu durumda, bir çağrı yapılır.</span><span class="sxs-lookup"><span data-stu-id="e7fca-153">In this case, the call is made if the cmdlet cannot find a process for a specified process identifier.</span></span>

```csharp
protected override void ProcessRecord()
{
  // If no name parameter passed to cmdlet, get all processes.
  if (processNames == null)
  {
    WriteObject(Process.GetProcesses(), true);
  }
    else
    {
      // If a name parameter is passed to cmdlet, get and write
      // the associated processes.
      // Write a nonterminating error for failure to retrieve
      // a process.
      foreach (string name in processNames)
      {
        Process[] processes;

        try
        {
          processes = Process.GetProcessesByName(name);
        }
        catch (InvalidOperationException ex)
        {
          WriteError(new ErrorRecord(
                     ex,
                     "NameNotFound",
                     ErrorCategory.InvalidOperation,
                     name));
          continue;
        }

        WriteObject(processes, true);
      } // foreach (...
    } // else
  }
```

### <a name="things-to-remember-about-writing-nonterminating-errors"></a><span data-ttu-id="e7fca-154">Olmak üzere Sonlandırmasız hatalar yazmakla ilgili bunları unutmayın</span><span class="sxs-lookup"><span data-stu-id="e7fca-154">Things to Remember About Writing Nonterminating Errors</span></span>

<span data-ttu-id="e7fca-155">Olmak üzere sonlandırmasız bir hata için cmdlet belirli her giriş nesnesi için bir özel hata tanımlayıcı oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e7fca-155">For a nonterminating error, the cmdlet must generate a specific error identifier for each specific input object.</span></span>

<span data-ttu-id="e7fca-156">Bir cmdlet sık olmak üzere sonlandırmasız bir hata tarafından üretilen PowerShell eylem değiştirmesi gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="e7fca-156">A cmdlet frequently needs to modify the PowerShell action produced by a nonterminating error.</span></span>
<span data-ttu-id="e7fca-157">Bunu tanımlayarak yapabilirsiniz `ErrorAction` ve `ErrorVariable` parametreleri.</span><span class="sxs-lookup"><span data-stu-id="e7fca-157">It can do this by defining the `ErrorAction` and `ErrorVariable` parameters.</span></span>
<span data-ttu-id="e7fca-158">Tanımlanıyorsa `ErrorAction` parametresi, cmdlet kullanıcı seçenekleri sunan [System.Management.Automation.ActionPreference][], eylem ayarlayarak da doğrudan etkileyebilir `$ErrorActionPreference` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="e7fca-158">If defining the `ErrorAction` parameter, the cmdlet presents the user options [System.Management.Automation.ActionPreference][], you can also directly influence the action by setting the `$ErrorActionPreference` variable.</span></span>

<span data-ttu-id="e7fca-159">Cmdlet'ini kullanarak değişken için olmak üzere sonlandırmasız hatalar kaydedebilirsiniz `ErrorVariable` , bu ayardan etkilenmez parametresini `ErrorAction`.</span><span class="sxs-lookup"><span data-stu-id="e7fca-159">The cmdlet can save nonterminating errors to a variable using the `ErrorVariable` parameter, which is not affected by the setting of `ErrorAction`.</span></span>
<span data-ttu-id="e7fca-160">Hataları var olan bir hata değişkenine bir artı işareti (+) ekleyerek değişken adının önüne eklenerek.</span><span class="sxs-lookup"><span data-stu-id="e7fca-160">Failures can be appended to an existing error variable by adding a plus sign (+) to the front of the variable name.</span></span>

## <a name="code-sample"></a><span data-ttu-id="e7fca-161">Kod örneği</span><span class="sxs-lookup"><span data-stu-id="e7fca-161">Code Sample</span></span>

<span data-ttu-id="e7fca-162">Tamamlanmış C# örnek kod için bkz: [GetProcessSample04 örnek](./getprocesssample04-sample.md).</span><span class="sxs-lookup"><span data-stu-id="e7fca-162">For the complete C# sample code, see [GetProcessSample04 Sample](./getprocesssample04-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="e7fca-163">Nesne türleri ve biçimlendirme tanımlayın</span><span class="sxs-lookup"><span data-stu-id="e7fca-163">Define Object Types and Formatting</span></span>

<span data-ttu-id="e7fca-164">PowerShell cmdlet arasında .NET nesneleri kullanarak bilgileri geçirir.</span><span class="sxs-lookup"><span data-stu-id="e7fca-164">PowerShell passes information between cmdlets using .NET objects.</span></span>
<span data-ttu-id="e7fca-165">Sonuç olarak, bir cmdlet kendi türü tanımlamanız gerekebilir veya başka bir cmdlet tarafından sağlanan mevcut türü genişletmek cmdlet gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="e7fca-165">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span>
<span data-ttu-id="e7fca-166">Yeni türleri tanımlama veya varolan türleri genişletme hakkında daha fazla bilgi için bkz. [genişletme nesne türleri ve biçimlendirme](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="e7fca-166">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="e7fca-167">Cmdlet oluşturma</span><span class="sxs-lookup"><span data-stu-id="e7fca-167">Building the Cmdlet</span></span>

<span data-ttu-id="e7fca-168">Bir cmdlet uyguladıktan sonra Windows PowerShell ile bir Windows PowerShell ek bileşeni kaydetmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="e7fca-168">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span>
<span data-ttu-id="e7fca-169">Cmdlet'leri kaydetme hakkında daha fazla bilgi için bkz. [kaydetme cmdlet'leri ve sağlayıcıları uygulamalarını barındırmak için nasıl](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="e7fca-169">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="e7fca-170">Sınama cmdlet'i</span><span class="sxs-lookup"><span data-stu-id="e7fca-170">Testing the Cmdlet</span></span>

<span data-ttu-id="e7fca-171">PowerShell ile cmdlet'ini kaydedildi, komut satırında çalıştırarak test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e7fca-171">When your cmdlet has been registered with PowerShell, you can test it by running it on the command line.</span></span>
<span data-ttu-id="e7fca-172">Şimdi hata raporlarını olup olmadığını görmek için örnek Get-Proc cmdlet sınama:</span><span class="sxs-lookup"><span data-stu-id="e7fca-172">Let's test the sample Get-Proc cmdlet to see whether it reports an error:</span></span>

- <span data-ttu-id="e7fca-173">PowerShell'i başlatın ve "TEST" adlı işlem almak için Get-Proc cmdlet'ini kullanın.</span><span class="sxs-lookup"><span data-stu-id="e7fca-173">Start PowerShell, and use the Get-Proc cmdlet to retrieve the processes named "TEST".</span></span>

    ```powershell
    PS> get-proc -name test
    ```

<span data-ttu-id="e7fca-174">Aşağıdaki çıktı görünür.</span><span class="sxs-lookup"><span data-stu-id="e7fca-174">The following output appears.</span></span>

    ```
    get-proc : Operation is not valid due to the current state of the object.
    At line:1 char:9
    + get-proc  <<<< -name test
    ```

## <a name="see-also"></a><span data-ttu-id="e7fca-175">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="e7fca-175">See Also</span></span>

[<span data-ttu-id="e7fca-176">İşlem ardışık düzen giriş parametreleri ekleme</span><span class="sxs-lookup"><span data-stu-id="e7fca-176">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="e7fca-177">Komut satırı giriş parametreleri ekleme</span><span class="sxs-lookup"><span data-stu-id="e7fca-177">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="e7fca-178">İlk Cmdlet'inize oluşturma</span><span class="sxs-lookup"><span data-stu-id="e7fca-178">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="e7fca-179">Nesne türlerini genişletme ve biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="e7fca-179">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="e7fca-180">Cmdlet, sağlayıcılar kaydetmek ve uygulamaları barındırmak nasıl</span><span class="sxs-lookup"><span data-stu-id="e7fca-180">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="e7fca-181">Windows PowerShell başvurusu</span><span class="sxs-lookup"><span data-stu-id="e7fca-181">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="e7fca-182">Cmdlet örnekleri</span><span class="sxs-lookup"><span data-stu-id="e7fca-182">Cmdlet Samples</span></span>](./cmdlet-samples.md)

[System.Exception]: /dotnet/api/System.Exception
[System.Management.Automation.ActionPreference]: /dotnet/api/System.Management.Automation.ActionPreference
[System.Management.Automation.Cmdlet.ProcessRecord]: /dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord
[System.Management.Automation.Cmdlet.WriteError]: /dotnet/api/System.Management.Automation.Cmdlet.WriteError
[System.Management.Automation.Cmdlet]: /dotnet/api/System.Management.Automation.Cmdlet
[System.Management.Automation.ErrorCategory]: /dotnet/api/System.Management.Automation.ErrorCategory
[System.Management.Automation.ErrorRecord]: /dotnet/api/System.Management.Automation.ErrorRecord
