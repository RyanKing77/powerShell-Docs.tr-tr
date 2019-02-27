---
title: Ardışık Düzen giriş parametreleri ekleme | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmer's Guide], pipeline input
- parameters [PowerShell Programer's Guide], pipeline input
ms.assetid: 09bf70a9-7c76-4ffe-b3f0-a1d5f10a0931
caps.latest.revision: 8
ms.openlocfilehash: c790d20a792bcdb4a34485e53375560e129433a8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845790"
---
# <a name="adding-parameters-that-process-pipeline-input"></a><span data-ttu-id="a1253-102">Komut Zinciri Girişini İşleyen Parametreler Ekleme</span><span class="sxs-lookup"><span data-stu-id="a1253-102">Adding Parameters that Process Pipeline Input</span></span>

<span data-ttu-id="a1253-103">Giriş bir cmdlet için bir kaynak, bir Yukarı Akış cmdlet'inden kaynaklanan işlem hattında bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="a1253-103">One source of input for a cmdlet is an object on the pipeline that originates from an upstream cmdlet.</span></span> <span data-ttu-id="a1253-104">Bu bölümde, Get-Proc cmdlet'e parametre eklemeyi açıklar (açıklanan [oluşturma bilgisayarınızı ilk Cmdlet](./creating-a-cmdlet-without-parameters.md)) cmdlet'i, işlem hattı nesneleri işleyebilmesi.</span><span class="sxs-lookup"><span data-stu-id="a1253-104">This section describes how to add a parameter to the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)) so that the cmdlet can process pipeline objects.</span></span>

<span data-ttu-id="a1253-105">Bu Get-Proc cmdlet'i kullanan bir `Name` kabul eden bir işlem hattı nesnesinden giriş parametresi ve yerel bilgisayardan sağlanan adlarına göre işlem bilgilerini alır ve sonra komut satırında işlemleri hakkındaki bilgileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="a1253-105">This Get-Proc cmdlet uses a `Name` parameter that accepts input from a pipeline object, retrieves process information from the local computer based on the supplied names, and then displays information about the processes at the command line.</span></span>

<span data-ttu-id="a1253-106">Bu bölümdeki konular şunlardır:</span><span class="sxs-lookup"><span data-stu-id="a1253-106">Topics in this section include the following:</span></span>

- [<span data-ttu-id="a1253-107">Cmdlet'i sınıf tanımlama</span><span class="sxs-lookup"><span data-stu-id="a1253-107">Defining the Cmdlet Class</span></span>](#Defining-the-Cmdlet-Class)

- [<span data-ttu-id="a1253-108">Ardışık düzendeki girişi tanımlama</span><span class="sxs-lookup"><span data-stu-id="a1253-108">Defining Input from the Pipeline</span></span>](#Defining-Input-from-the-Pipeline)

- [<span data-ttu-id="a1253-109">Bir giriş işleme yöntemi geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="a1253-109">Overriding an Input Processing Method</span></span>](#Overriding-an-Input-Processing-Method)

- [<span data-ttu-id="a1253-110">Kod örneği</span><span class="sxs-lookup"><span data-stu-id="a1253-110">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="a1253-111">Nesne türlerini tanımlama ve biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="a1253-111">Defining Object Types and Formatting</span></span>](#Defining-Object-Types-and-Formatting)

- [<span data-ttu-id="a1253-112">Cmdlet oluşturma</span><span class="sxs-lookup"><span data-stu-id="a1253-112">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="a1253-113">Sınama cmdlet'i</span><span class="sxs-lookup"><span data-stu-id="a1253-113">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="a1253-114">Cmdlet'i sınıf tanımlama</span><span class="sxs-lookup"><span data-stu-id="a1253-114">Defining the Cmdlet Class</span></span>

<span data-ttu-id="a1253-115">İlk adımda cmdlet'i oluşturma her zaman cmdlet adlandırma ve cmdlet uygulayan .NET sınıf bildirme.</span><span class="sxs-lookup"><span data-stu-id="a1253-115">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="a1253-116">Bu cmdlet, burada seçilen fiil adı "Get", bu nedenle işlem bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="a1253-116">This cmdlet retrieves process information, so the verb name chosen here is "Get".</span></span> <span data-ttu-id="a1253-117">(Komut satırı girişi neredeyse her türlü bilgi alma özelliğine sahip olan cmdlet işleyebilir.) Onaylanan cmdlet fiilleri hakkında daha fazla bilgi için bkz: [Cmdlet fiili adları](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="a1253-117">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="a1253-118">Bu Get-Proc cmdlet tanımı aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a1253-118">The following is the definition for this Get-Proc cmdlet.</span></span> <span data-ttu-id="a1253-119">Bu tanımın ayrıntıları verilir [oluşturma bilgisayarınızı ilk Cmdlet](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="a1253-119">Details of this definition are given in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-input-from-the-pipeline"></a><span data-ttu-id="a1253-120">Ardışık düzendeki girişi tanımlama</span><span class="sxs-lookup"><span data-stu-id="a1253-120">Defining Input from the Pipeline</span></span>

<span data-ttu-id="a1253-121">Bu bölümde, bir cmdlet için ardışık düzendeki girişi tanımlamak açıklar.</span><span class="sxs-lookup"><span data-stu-id="a1253-121">This section describes how to define input from the pipeline for a cmdlet.</span></span> <span data-ttu-id="a1253-122">Bu Get-Proc cmdlet temsil eden bir özelliğini tanımlar `Name` açıklandığı parametresi [parametreler, işlem komut satırı girişi ekleme](./adding-parameters-that-process-command-line-input.md).</span><span class="sxs-lookup"><span data-stu-id="a1253-122">This Get-Proc cmdlet defines a property that represents the `Name` parameter as described in [Adding Parameters that Process Command Line Input](./adding-parameters-that-process-command-line-input.md).</span></span> <span data-ttu-id="a1253-123">(Parametre bildirme hakkında genel bilgi için bu konuya bakın.)</span><span class="sxs-lookup"><span data-stu-id="a1253-123">(See that topic for general information about declaring parameters.)</span></span>

<span data-ttu-id="a1253-124">Ancak, bir cmdlet, işlem hattı girdiyi işlemek üzere gerektiğinde parametrelerinin değerleri girmek için Windows PowerShell çalışma zamanı tarafından bağlı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a1253-124">However, when a cmdlet needs to process pipeline input, it must have its parameters bound to input values by the Windows PowerShell runtime.</span></span> <span data-ttu-id="a1253-125">Bunu yapmak için eklemelisiniz `ValueFromPipeline` anahtar sözcüğü veya ekleme `ValueFromPipelineByProperty` anahtar [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) öznitelik bildirimi.</span><span class="sxs-lookup"><span data-stu-id="a1253-125">To do this, you must add the `ValueFromPipeline` keyword or add the `ValueFromPipelineByProperty` keyword to the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration.</span></span> <span data-ttu-id="a1253-126">Belirtin `ValueFromPipeline` tam giriş nesnesi cmdlet'i erişirse, anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="a1253-126">Specify the `ValueFromPipeline` keyword if the cmdlet accesses the complete input object.</span></span> <span data-ttu-id="a1253-127">Belirtin `ValueFromPipelineByProperty` cmdlet'i yalnızca nesnenin bir özelliğini erişiyorsa.</span><span class="sxs-lookup"><span data-stu-id="a1253-127">Specify the `ValueFromPipelineByProperty` if the cmdlet accesses only a property of the object.</span></span>

<span data-ttu-id="a1253-128">Parametre bildirimi için işte `Name` parametresi Get-Proc cmdlet'in ardışık giriş kabul eder.</span><span class="sxs-lookup"><span data-stu-id="a1253-128">Here is the parameter declaration for the `Name` parameter of this Get-Proc cmdlet that accepts pipeline input.</span></span>

[!code-csharp[GetProcessSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs#L35-L44 "GetProcessSample03.cs")]

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

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#GetProc03VBNameParameter](Msh_samplesgetproc03#GetProc03VBNameParameter)]  -->

<span data-ttu-id="a1253-129">Önceki bildirim kümeleri `ValueFromPipeline` anahtar `true` böylece aynı türde parametre olarak nesne ise, Windows PowerShell çalışma zamanı gelen nesnesine parametre bağlama ya da aynı türüne dönüştürülebilen.</span><span class="sxs-lookup"><span data-stu-id="a1253-129">The previous declaration sets the `ValueFromPipeline` keyword to `true` so that the Windows PowerShell runtime will bind the parameter to the incoming object if the object is the same type as the parameter, or if it can be coerced to the same type.</span></span> <span data-ttu-id="a1253-130">`ValueFromPipelineByPropertyName` De anahtar sözcüğü ayarlanmasını `true` gelen nesne için Windows PowerShell çalışma zamanını kontrol eder, böylece bir `Name` özelliği.</span><span class="sxs-lookup"><span data-stu-id="a1253-130">The `ValueFromPipelineByPropertyName` keyword is also set to `true` so that the Windows PowerShell runtime will check the incoming object for a `Name` property.</span></span> <span data-ttu-id="a1253-131">Gelen nesne, böyle bir özellik varsa, çalışma zamanı bağlayacaksınız `Name` parametresi `Name` gelen nesnesinin özelliği.</span><span class="sxs-lookup"><span data-stu-id="a1253-131">If the incoming object has such a property, the runtime will bind the `Name` parameter to the `Name` property of the incoming object.</span></span>

> [!NOTE]
> <span data-ttu-id="a1253-132">Ayarını `ValueFromPipeline` özniteliğinin anahtar sözcüğü bir parametre ayarı önceliklidir `ValueFromPipelineByPropertyName` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="a1253-132">The setting of the `ValueFromPipeline` attribute keyword for a parameter takes precedence over the setting for the `ValueFromPipelineByPropertyName` keyword.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="a1253-133">Bir giriş işleme yöntemi geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="a1253-133">Overriding an Input Processing Method</span></span>

<span data-ttu-id="a1253-134">İşlem hattı girdi işlemek üzere cmdlet'inize ise, yöntem işleme uygun giriş geçersiz kılmak gerekir.</span><span class="sxs-lookup"><span data-stu-id="a1253-134">If your cmdlet is to handle pipeline input, it needs to override the appropriate input processing methods.</span></span> <span data-ttu-id="a1253-135">Temel giriş işleme yöntemleri de sunulan [oluşturma bilgisayarınızı ilk Cmdlet](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="a1253-135">The basic input processing methods are introduced in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

<span data-ttu-id="a1253-136">Bu Get-Proc cmdlet geçersiz kılmalar [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) işlemek için gereken yöntemini `Name` kullanıcı veya bir betik tarafından sağlanan parametre girişi.</span><span class="sxs-lookup"><span data-stu-id="a1253-136">This Get-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to handle the `Name` parameter input provided by the user or a script.</span></span> <span data-ttu-id="a1253-137">Adsız sağlanırsa, bu yöntem işlemleri her istenen işlem adı veya tüm işlemler için alırsınız.</span><span class="sxs-lookup"><span data-stu-id="a1253-137">This method will get the processes for each requested process name or all processes if no name is provided.</span></span> <span data-ttu-id="a1253-138">İçinde dikkat [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), çağrı [System.Management.Automation.Cmdlet.Writeobject%28System.Object%2Csystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) olduğu Çıkış nesnelerini ardışık düzenine gönderme için çıkış mekanizması.</span><span class="sxs-lookup"><span data-stu-id="a1253-138">Notice that within [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), the call to [System.Management.Automation.Cmdlet.Writeobject%28System.Object%2Csystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) is the output mechanism for sending output objects to the pipeline.</span></span> <span data-ttu-id="a1253-139">Bu çağrı, ikinci parametresinin `enumerateCollection`, ayarlanır `true` işlem nesneleri dizisi numaralandırabilir ve bir işlem aynı anda komut satırına yazma Windows PowerShell çalışma zamanı söylemek için.</span><span class="sxs-lookup"><span data-stu-id="a1253-139">The second parameter of this call, `enumerateCollection`, is set to `true` to tell the Windows PowerShell runtime to enumerate the array of process objects, and write one process at a time to the command line.</span></span>

```csharp
protected override void ProcessRecord()
{
  // If no process names are passed to the cmdlet, get all processes.
  if (processNames == null)
  {
      // Write the processes to the pipeline making them available
      // to the next cmdlet. The second argument of this call tells
      // PowerShell to enumerate the array, and send one process at a
      // time to the pipeline.
      WriteObject(Process.GetProcesses(), true);
  }
  else
  {
    // If process names are passed to the cmdlet, get and write
    // the associated processes.
    foreach (string name in processNames)
    {
      WriteObject(Process.GetProcessesByName(name), true);
    } // End foreach (string name...).
  }
}
```

```vb
Protected Overrides Sub ProcessRecord()
    Dim processes As Process()

    '/ If no process names are passed to the cmdlet, get all processes.
    If processNames Is Nothing Then
        processes = Process.GetProcesses()
    Else

        '/ If process names are specified, write the processes to the
        '/ pipeline to display them or make them available to the next cmdlet.
        For Each name As String In processNames
            '/ The second parameter of this call tells PowerShell to enumerate the
            '/ array, and send one process at a time to the pipeline.
            WriteObject(Process.GetProcessesByName(name), True)
        Next
    End If

End Sub 'ProcessRecord
```

## <a name="code-sample"></a><span data-ttu-id="a1253-140">Kod örneği</span><span class="sxs-lookup"><span data-stu-id="a1253-140">Code Sample</span></span>

<span data-ttu-id="a1253-141">Tamamlanmış C# örnek kod için bkz: [GetProcessSample03 örnek](./getprocesssample03-sample.md).</span><span class="sxs-lookup"><span data-stu-id="a1253-141">For the complete C# sample code, see [GetProcessSample03 Sample](./getprocesssample03-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="a1253-142">Nesne türlerini tanımlama ve biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="a1253-142">Defining Object Types and Formatting</span></span>

<span data-ttu-id="a1253-143">Windows PowerShell cmdlet arasında .net nesneleri kullanarak bilgileri geçirir.</span><span class="sxs-lookup"><span data-stu-id="a1253-143">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="a1253-144">Sonuç olarak, bir cmdlet kendi türü tanımlamanız gerekebilir veya başka bir cmdlet tarafından sağlanan mevcut türü genişletmek cmdlet gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="a1253-144">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="a1253-145">Yeni türleri tanımlama veya varolan türleri genişletme hakkında daha fazla bilgi için bkz. [genişletme nesne türleri ve biçimlendirme](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="a1253-145">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="a1253-146">Cmdlet oluşturma</span><span class="sxs-lookup"><span data-stu-id="a1253-146">Building the Cmdlet</span></span>

<span data-ttu-id="a1253-147">Bir cmdlet uyguladıktan sonra bunu Windows PowerShell ile bir Windows PowerShell ek bileşeni kayıtlı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a1253-147">After implementing a cmdlet it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="a1253-148">Cmdlet'leri kaydetme hakkında daha fazla bilgi için bkz. [kaydetme cmdlet'leri ve sağlayıcıları uygulamalarını barındırmak için nasıl](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="a1253-148">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="a1253-149">Sınama cmdlet'i</span><span class="sxs-lookup"><span data-stu-id="a1253-149">Testing the Cmdlet</span></span>

<span data-ttu-id="a1253-150">Windows PowerShell ile cmdlet'ini kaydedildi, komut satırında çalıştırarak test edin.</span><span class="sxs-lookup"><span data-stu-id="a1253-150">When your cmdlet has been registered with Windows PowerShell, test it by running it on the command line.</span></span> <span data-ttu-id="a1253-151">Örneğin, örnek cmdlet kodu test edin.</span><span class="sxs-lookup"><span data-stu-id="a1253-151">For example, test the code for the sample cmdlet.</span></span> <span data-ttu-id="a1253-152">Komut satırından cmdlet'leri kullanma hakkında daha fazla bilgi için bkz. [Windows PowerShell ile çalışmaya başlama](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="a1253-152">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="a1253-153">Windows PowerShell komut isteminde, işlem hattı aracılığıyla işlem adları almak için aşağıdaki komutları girin.</span><span class="sxs-lookup"><span data-stu-id="a1253-153">At the Windows PowerShell prompt, enter the following commands to retrieve the process names through the pipeline.</span></span>

    ```powershell
    PS> type ProcessNames | get-proc
    ```

<span data-ttu-id="a1253-154">Aşağıdaki çıktı görünür.</span><span class="sxs-lookup"><span data-stu-id="a1253-154">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
    -------  ------  -----   ----- -----   ------    --  -----------
        809      21  40856    4448    147    9.50  2288  iexplore
        737      21  26036   16348    144   22.03  3860  iexplore
         39       2   1024     388     30    0.08  3396  notepad
       3927      62  71836   26984    467  195.19  1848  OUTLOOK
    ```

- <span data-ttu-id="a1253-155">Sahip işlem nesneleri almak için aşağıdaki satırları girin bir `Name` "IEXPLORE" adlı işlemlerden özelliği.</span><span class="sxs-lookup"><span data-stu-id="a1253-155">Enter the following lines to get the process objects that have a `Name` property from the processes called "IEXPLORE".</span></span> <span data-ttu-id="a1253-156">Bu örnekte `Get-Process` (Windows PowerShell tarafından sağlanan) cmdlet'i "IEXPLORE" işlemleri almak için Yukarı Akış komutu.</span><span class="sxs-lookup"><span data-stu-id="a1253-156">This example uses the `Get-Process` cmdlet (provided by Windows PowerShell) as an upstream command to retrieve the "IEXPLORE" processes.</span></span>

    ```powershell
    PS> get-process iexplore | get-proc
    ```

<span data-ttu-id="a1253-157">Aşağıdaki çıktı görünür.</span><span class="sxs-lookup"><span data-stu-id="a1253-157">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
    -------  ------  -----      ----- -----   ------     -- -----------
        801      21  40720    6544    142    9.52  2288  iexplore
        726      21  25872   16652    138   22.09  3860  iexplore
        801      21  40720    6544    142    9.52  2288  iexplore
        726      21  25872   16652    138   22.09  3860  iexplore
    ```

## <a name="see-also"></a><span data-ttu-id="a1253-158">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="a1253-158">See Also</span></span>

[<span data-ttu-id="a1253-159">Komut satırı giriş parametreleri ekleme</span><span class="sxs-lookup"><span data-stu-id="a1253-159">Adding Parameters that Process Command Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="a1253-160">İlk Cmdlet'inize oluşturma</span><span class="sxs-lookup"><span data-stu-id="a1253-160">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="a1253-161">Nesne türlerini genişletme ve biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="a1253-161">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="a1253-162">Cmdlet, sağlayıcılar kaydetmek ve uygulamaları barındırmak nasıl</span><span class="sxs-lookup"><span data-stu-id="a1253-162">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="a1253-163">Windows PowerShell başvurusu</span><span class="sxs-lookup"><span data-stu-id="a1253-163">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="a1253-164">Cmdlet örnekleri</span><span class="sxs-lookup"><span data-stu-id="a1253-164">Cmdlet Samples</span></span>](./cmdlet-samples.md)
