---
title: Parametresiz bir cmdlet'i oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmers Guide], creating
- cmdlets [PowerShell Programmers Guide], basic cmdlet
ms.assetid: 54236ef3-82db-45f8-9114-1ecb7ff65d3e
caps.latest.revision: 8
ms.openlocfilehash: 7f10acf59dedbb4af17bc5250e8624282ba22656
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854961"
---
# <a name="creating-a-cmdlet-without-parameters"></a><span data-ttu-id="b10d0-102">Parametresiz Cmdlet Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b10d0-102">Creating a Cmdlet without Parameters</span></span>

<span data-ttu-id="b10d0-103">Bu bölümde, bir cmdlet'i parametreleri kullanımı ve yerel bilgisayardan bilgilerini alır ve ardından işlem hattının bilgi Yazar oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="b10d0-103">This section describes how to create a cmdlet that retrieves information from the local computer without the use of parameters, and then writes the information to the pipeline.</span></span> <span data-ttu-id="b10d0-104">Burada açıklanan cmdlet'i yerel bilgisayar işlemleri hakkındaki bilgileri alır ve ardından bu bilgileri komut satırında görüntüleyen bir Get-Proc cmdlet'tir.</span><span class="sxs-lookup"><span data-stu-id="b10d0-104">The cmdlet described here is a Get-Proc cmdlet that retrieves information about the processes of the local computer, and then displays that information at the command line.</span></span>

> [!NOTE]
> <span data-ttu-id="b10d0-105">Cmdlet'leri yazarken Windows PowerShell® başvuru derlemeleri diske (varsayılan olarak C:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0) yüklendiğini dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="b10d0-105">Be aware that when writing cmdlets, the Windows PowerShell® reference assemblies are downloaded onto disk (by default at C:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0).</span></span> <span data-ttu-id="b10d0-106">Genel Derleme Önbelleği'ne (GAC) yüklü değil.</span><span class="sxs-lookup"><span data-stu-id="b10d0-106">They are not installed in the Global Assembly Cache (GAC).</span></span>

## <a name="naming-the-cmdlet"></a><span data-ttu-id="b10d0-107">Cmdlet adlandırma</span><span class="sxs-lookup"><span data-stu-id="b10d0-107">Naming the Cmdlet</span></span>

<span data-ttu-id="b10d0-108">Cmdlet adı cmdlet eylemde gösteren bir fiil ve cmdlet temel aldığı öğeleri gösteren bir isim oluşur.</span><span class="sxs-lookup"><span data-stu-id="b10d0-108">A cmdlet name consists of a verb that indicates the action the cmdlet takes and a noun that indicates the items that the cmdlet acts upon.</span></span> <span data-ttu-id="b10d0-109">Bu örnek Get-Proc cmdlet işlem nesneleri getireceğinden "tarafından tanımlanan Al," fiili kullanan [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) numaralandırma ve isim cmdlet işlem öğeler üzerinde çalıştığını göstermek için "işlem".</span><span class="sxs-lookup"><span data-stu-id="b10d0-109">Because this sample Get-Proc cmdlet retrieves process objects, it uses the verb "Get", defined by the [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) enumeration, and the noun "Proc" to indicate that the cmdlet works on process items.</span></span>

<span data-ttu-id="b10d0-110">Cmdlet'leri adlandırırken şu karakterlerin hiçbirini kullanmayın: #, () {} [] & - / \ $;: "' <> &#124; ?</span><span class="sxs-lookup"><span data-stu-id="b10d0-110">When naming cmdlets, do not use any of the following characters: # , () {} [] & - /\ $ ; : " '<> &#124; ?</span></span> <span data-ttu-id="b10d0-111">@ \` .</span><span class="sxs-lookup"><span data-stu-id="b10d0-111">@ \` .</span></span>

### <a name="choosing-a-noun"></a><span data-ttu-id="b10d0-112">Bir isim seçme</span><span class="sxs-lookup"><span data-stu-id="b10d0-112">Choosing a Noun</span></span>

<span data-ttu-id="b10d0-113">Belirli bir isim seçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b10d0-113">You should choose a noun that is specific.</span></span> <span data-ttu-id="b10d0-114">Ürün adının kısaltılmış bir sürümü ile önek tekil bir isim kullanmak en iyisidir.</span><span class="sxs-lookup"><span data-stu-id="b10d0-114">It is best to use a singular noun prefixed with a shortened version of the product name.</span></span> <span data-ttu-id="b10d0-115">Bu tür bir örnek cmdlet adı "`Get-SQLServer`".</span><span class="sxs-lookup"><span data-stu-id="b10d0-115">An example cmdlet name of this type is "`Get-SQLServer`".</span></span>

### <a name="choosing-a-verb"></a><span data-ttu-id="b10d0-116">Fiil seçme</span><span class="sxs-lookup"><span data-stu-id="b10d0-116">Choosing a Verb</span></span>

<span data-ttu-id="b10d0-117">Onaylanan cmdlet fiili adları kümesinden fiil kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b10d0-117">You should use a verb from the set of approved cmdlet verb names.</span></span> <span data-ttu-id="b10d0-118">Onaylanan cmdlet fiilleri hakkında daha fazla bilgi için bkz: [Cmdlet fiili adları](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="b10d0-118">For more information about the approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="b10d0-119">Cmdlet'i sınıf tanımlama</span><span class="sxs-lookup"><span data-stu-id="b10d0-119">Defining the Cmdlet Class</span></span>

<span data-ttu-id="b10d0-120">Cmdlet adı seçtikten sonra cmdlet uygulamak için bir .NET sınıfı tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="b10d0-120">Once you have chosen a cmdlet name, define a .NET class to implement the cmdlet.</span></span> <span data-ttu-id="b10d0-121">Bu örnek Get-Proc cmdlet'in sınıf tanımı aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="b10d0-121">Here is the class definition for this sample Get-Proc cmdlet:</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

<span data-ttu-id="b10d0-122">Sınıf tanımı önce dikkat [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) özniteliğiyle sözdizimi `[Cmdlet(verb, noun, ...)]`, bu sınıfı bir cmdlet olarak tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b10d0-122">Notice that previous to the class definition, the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute, with the syntax `[Cmdlet(verb, noun, ...)]`, is used to identify this class as a cmdlet.</span></span> <span data-ttu-id="b10d0-123">Bu tüm cmdlet'ler için yalnızca gerekli öznitelik ve doğru bir şekilde çağırmak Windows PowerShell çalışma zamanı sağlar.</span><span class="sxs-lookup"><span data-stu-id="b10d0-123">This is the only required attribute for all cmdlets, and it allows the Windows PowerShell runtime to call them correctly.</span></span> <span data-ttu-id="b10d0-124">Daha fazla gerekirse sınıf tanımlamak için öznitelik anahtar sözcükleri ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b10d0-124">You can set attribute keywords to further declare the class if necessary.</span></span> <span data-ttu-id="b10d0-125">Bizim örnek GetProcCommand sınıfı özniteliği bildirimi yalnızca Get-Proc cmdlet isim ve fiili adlarını bildirir dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="b10d0-125">Be aware that the attribute declaration for our sample GetProcCommand class declares only the noun and verb names for the Get-Proc cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="b10d0-126">Tüm Windows PowerShell öznitelik sınıfları için ayarlayabileceğiniz bir anahtar öznitelik sınıfının özelliklerine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="b10d0-126">For all Windows PowerShell attribute classes, the keywords that you can set correspond to properties of the attribute class.</span></span>

<span data-ttu-id="b10d0-127">Cmdlet'inin sınıfı adlandırırken sınıf adında cmdlet adı yansıtacak şekilde iyi bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="b10d0-127">When naming the class of the cmdlet, it is a good practice to reflect the cmdlet name in the class name.</span></span> <span data-ttu-id="b10d0-128">Bunu yapmak için "Eylem" ve "Ad" fiil ve isim kullanılan cmdlet adı ile değiştirin ve formu "VerbNounCommand" kullanın.</span><span class="sxs-lookup"><span data-stu-id="b10d0-128">To do this, use the form "VerbNounCommand" and replace "Verb" and "Noun" with the verb and noun used in the cmdlet name.</span></span> <span data-ttu-id="b10d0-129">Önceki sınıf tanımında gösterildiği örnek Get-Proc cmdlet türetilen GetProcCommand adlı bir sınıf tanımlar [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) temel sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b10d0-129">As is shown in the previous class definition, the sample Get-Proc cmdlet defines a class called GetProcCommand, which derives from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) base class.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b10d0-130">Windows PowerShell çalışma zamanı doğrudan erişen bir cmdlet tanımlamak istiyorsanız, .NET sınıfınıza öğesinden türetilmelidir [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) temel sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b10d0-130">If you want to define a cmdlet that accesses the Windows PowerShell runtime directly, your .NET class should derive from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) base class.</span></span> <span data-ttu-id="b10d0-131">Bu sınıf hakkında daha fazla bilgi için bkz: [bir Cmdlet tanımlar, parametre kümeleri oluşturma](./adding-parameter-sets-to-a-cmdlet.md).</span><span class="sxs-lookup"><span data-stu-id="b10d0-131">For more information about this class, see [Creating a Cmdlet that Defines Parameter Sets](./adding-parameter-sets-to-a-cmdlet.md).</span></span>

> [!NOTE]
> <span data-ttu-id="b10d0-132">Sınıf bir cmdlet için genel olarak açıkça işaretlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="b10d0-132">The class for a cmdlet must be explicitly marked as public.</span></span> <span data-ttu-id="b10d0-133">Genel olarak işaretlenmemiş sınıflar için iç varsayılan ve Windows PowerShell çalışma zamanı tarafından bulunmaz.</span><span class="sxs-lookup"><span data-stu-id="b10d0-133">Classes that are not marked as public will default to internal and will not be found by the Windows PowerShell runtime.</span></span>

<span data-ttu-id="b10d0-134">Windows PowerShell kullanan [Microsoft.PowerShell.Commands](/dotnet/api/Microsoft.PowerShell.Commands) cmdlet'i sınıflarına için ad alanı.</span><span class="sxs-lookup"><span data-stu-id="b10d0-134">Windows PowerShell uses the [Microsoft.PowerShell.Commands](/dotnet/api/Microsoft.PowerShell.Commands) namespace for its cmdlet classes.</span></span> <span data-ttu-id="b10d0-135">Bir API ad alanınız, örneğin, xxx.PS.Commands komutları ad alanında cmdlet'i sınıflarınızı yerleştirmek için önerilir.</span><span class="sxs-lookup"><span data-stu-id="b10d0-135">It is recommended to place your cmdlet classes in a Commands namespace of your API namespace, for example, xxx.PS.Commands.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="b10d0-136">Bir giriş işleme yöntemi geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="b10d0-136">Overriding an Input Processing Method</span></span>

<span data-ttu-id="b10d0-137">[System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) sınıfı en az biri cmdlet'inize geçersiz kılması gerekir, üç ana giriş işleme yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="b10d0-137">The [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class provides three main input processing methods, at least one of which your cmdlet must override.</span></span> <span data-ttu-id="b10d0-138">Windows PowerShell kayıtları nasıl işlediği hakkında daha fazla bilgi için bkz. [nasıl Windows PowerShell çalışır](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).</span><span class="sxs-lookup"><span data-stu-id="b10d0-138">For more information about how Windows PowerShell processes records, see [How Windows PowerShell Works](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).</span></span>

<span data-ttu-id="b10d0-139">Tüm giriş türleri için Windows PowerShell çalışma zamanı çağırır [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) işlemeyi etkinleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="b10d0-139">For all types of input, the Windows PowerShell runtime calls [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) to enable processing.</span></span> <span data-ttu-id="b10d0-140">Bazı ön işleme veya Kurulum cmdlet'inize gerçekleştirmesi gerekiyorsa, bu yöntemi geçersiz kılarak, bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b10d0-140">If your cmdlet must perform some preprocessing or setup, it can do this by overriding this method.</span></span>

> [!NOTE]
> <span data-ttu-id="b10d0-141">Windows PowerShell cmdlet çağrıldığında sağlanan parametre değerleri kümesi tanımlamak için "kayıt" terimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="b10d0-141">Windows PowerShell uses the term "record" to describe the set of parameter values supplied when a cmdlet is called.</span></span>

<span data-ttu-id="b10d0-142">Ardışık giriş cmdlet'inize kabul ederse kılmalı [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) yöntemi ve isteğe bağlı olarak [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b10d0-142">If your cmdlet accepts pipeline input, it must override the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method, and optionally the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="b10d0-143">Örneğin, tüm giriş kullanarak toplar, bir cmdlet'i her iki yöntem de kılabilir [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) ve ardından Giriş bir öğe yerine bir bütün olarak teker teker olarak çalışır `Sort-Object` cmdlet yapıyorsa.</span><span class="sxs-lookup"><span data-stu-id="b10d0-143">For example, a cmdlet might override both methods if it gathers all input using [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) and then operates on the input as a whole rather than one element at a time, as the `Sort-Object` cmdlet does.</span></span>

<span data-ttu-id="b10d0-144">Ardışık giriş cmdlet'inize almaz, geçersiz kılmalıdır [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b10d0-144">If your cmdlet does not take pipeline input, it should override the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="b10d0-145">Bu yöntem yerine sık kullanıldığını unutmayın [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) zaman cmdlet çalışamaz bir öğede bir kerede bir sıralama cmdlet için olduğu gibi.</span><span class="sxs-lookup"><span data-stu-id="b10d0-145">Be aware that this method is frequently used in place of [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) when the cmdlet cannot operate on one element at a time, as is the case for a sorting cmdlet.</span></span>

<span data-ttu-id="b10d0-146">Bu örnek Get-Proc cmdlet ardışık giriş alması gerektiğinden, onu geçersiz kılar [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) yöntemi ve varsayılan uygulamaları için kullandığı [ System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) ve [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing).</span><span class="sxs-lookup"><span data-stu-id="b10d0-146">Because this sample Get-Proc cmdlet must receive pipeline input, it overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method and uses the default implementations for [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) and [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing).</span></span> <span data-ttu-id="b10d0-147">[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) geçersiz kılma işlemlerini alır ve komut satırını kullanarak Yazar [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b10d0-147">The [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) override retrieves processes and writes them to the command line using the [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) method.</span></span>

```csharp
protected override void ProcessRecord()
{
  // Get the current processes
  Process[] processes = Process.GetProcesses();

  // Write the processes to the pipeline making them available
  // to the next cmdlet. The second parameter of this call tells
  // PowerShell to enumerate the array, and send one process at a
  // time to the pipeline.
  WriteObject(processes, true);
}
```

```vb
Protected Overrides Sub ProcessRecord()

    '/ Get the current processes.
    Dim processes As Process()
    processes = Process.GetProcesses()

    '/ Write the processes to the pipeline making them available
    '/ to the next cmdlet. The second parameter of this call tells
    '/ PowerShell to enumerate the array, and send one process at a
    '/ time to the pipeline.
    WriteObject(processes, True)

End Sub 'ProcessRecord
```

#### <a name="things-to-remember-about-input-processing"></a><span data-ttu-id="b10d0-148">Giriş işleme hakkında bunları unutmayın</span><span class="sxs-lookup"><span data-stu-id="b10d0-148">Things to Remember About Input Processing</span></span>

- <span data-ttu-id="b10d0-149">Komut satırında kullanıcı tarafından sağlanan açık bir nesnenin (örneğin, bir dize) girişi için varsayılan kaynağıdır.</span><span class="sxs-lookup"><span data-stu-id="b10d0-149">The default source for input is an explicit object (for example, a string) provided by the user on the command line.</span></span> <span data-ttu-id="b10d0-150">Daha fazla bilgi için [bir cmdlet'e işlem komut satırı girişi oluşturma](./adding-parameters-that-process-command-line-input.md).</span><span class="sxs-lookup"><span data-stu-id="b10d0-150">For more information, see [Creating a Cmdlet to Process Command Line Input](./adding-parameters-that-process-command-line-input.md).</span></span>

- <span data-ttu-id="b10d0-151">İşleme yöntemi giriş giriş işlem hattında bir Yukarı Akış cmdlet'i çıkış nesnesinin de alabilir.</span><span class="sxs-lookup"><span data-stu-id="b10d0-151">An input processing method can also receive input from the output object of an upstream cmdlet on the pipeline.</span></span> <span data-ttu-id="b10d0-152">Daha fazla bilgi için [işlem ardışık Giriş bir cmdlet'e oluşturma](./adding-parameters-that-process-pipeline-input.md).</span><span class="sxs-lookup"><span data-stu-id="b10d0-152">For more information, see [Creating a Cmdlet to Process Pipeline Input](./adding-parameters-that-process-pipeline-input.md).</span></span> <span data-ttu-id="b10d0-153">Unutmayın, cmdlet komut satırı bir bileşiminden girişi almak ve işlem hattı kaynakları.</span><span class="sxs-lookup"><span data-stu-id="b10d0-153">Be aware that your cmdlet can receive input from a combination of command-line and pipeline sources.</span></span>

- <span data-ttu-id="b10d0-154">Aşağı Akış cmdlet'i, uzun süre veya hiç döndürmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="b10d0-154">The downstream cmdlet might not return for a long time, or not at all.</span></span> <span data-ttu-id="b10d0-155">Bu nedenle, işleme yöntemi, cmdlet'inde giriş kilitleri çağrı sırasında tutmak zorunda değil [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), özellikle kilit kapsamı cmdlet'i örneği genişletir.</span><span class="sxs-lookup"><span data-stu-id="b10d0-155">For that reason, the input processing method in your cmdlet should not hold locks during calls to [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), especially locks for which the scope extends beyond the cmdlet instance.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b10d0-156">Cmdlet hiçbir zaman çağırmalıdır [System.Console.Writeline\*](/dotnet/api/System.Console.WriteLine) ya da eşdeğerine.</span><span class="sxs-lookup"><span data-stu-id="b10d0-156">Cmdlets should never call [System.Console.Writeline\*](/dotnet/api/System.Console.WriteLine) or its equivalent.</span></span>

- <span data-ttu-id="b10d0-157">Cmdlet'inize sona erdiğinde temizlemek için nesne değişkenleri olabilir. işleme (örneğin, bir dosya tanıtıcısı olarak açarsa [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) yöntemi ve tanıtıcı tarafındankullanılmaküzereaçıktutar[ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)).</span><span class="sxs-lookup"><span data-stu-id="b10d0-157">Your cmdlet might have object variables to clean up when it is finished processing (for example, if it opens a file handle in the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method and keeps the handle open for use by [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)).</span></span> <span data-ttu-id="b10d0-158">Windows PowerShell çalışma zamanı her zaman arama olduğunu unutmamak önemlidir [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) nesne temizlemesi gerçekleştirmesi gereken yöntemini.</span><span class="sxs-lookup"><span data-stu-id="b10d0-158">It is important to remember that the Windows PowerShell runtime does not always call the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method, which should perform object cleanup.</span></span>

<span data-ttu-id="b10d0-159">Örneğin, [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) cmdlet midway iptal edilir ya da bir sonlandırma, herhangi bir bölümünü cmdlet'i hata meydana gelir, çağrılabilir değil.</span><span class="sxs-lookup"><span data-stu-id="b10d0-159">For example, [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) might not be called if the cmdlet is canceled midway or if a terminating error occurs in any part of the cmdlet.</span></span> <span data-ttu-id="b10d0-160">Bu nedenle, nesne temizleme gerektiren bir cmdlet tam uygulamalıdır [System.IDisposable](/dotnet/api/System.IDisposable) deseni, çalışma zamanı, her ikisi de çağırabilirsiniz Sonlandırıcı dahil olmak üzere [ System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) ve [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) işleme sonunda.</span><span class="sxs-lookup"><span data-stu-id="b10d0-160">Therefore, a cmdlet that requires object cleanup should implement the complete [System.IDisposable](/dotnet/api/System.IDisposable) pattern, including the finalizer, so that the runtime can call both [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) and [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) at the end of processing.</span></span>

## <a name="code-sample"></a><span data-ttu-id="b10d0-161">Kod örneği</span><span class="sxs-lookup"><span data-stu-id="b10d0-161">Code Sample</span></span>

<span data-ttu-id="b10d0-162">Tamamlanmış C# örnek kod için bkz: [GetProcessSample01 örnek](./getprocesssample01-sample.md).</span><span class="sxs-lookup"><span data-stu-id="b10d0-162">For the complete C# sample code, see [GetProcessSample01 Sample](./getprocesssample01-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="b10d0-163">Nesne türlerini tanımlama ve biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="b10d0-163">Defining Object Types and Formatting</span></span>

<span data-ttu-id="b10d0-164">Windows PowerShell cmdlet arasında .NET nesneleri kullanarak bilgileri geçirir.</span><span class="sxs-lookup"><span data-stu-id="b10d0-164">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="b10d0-165">Sonuç olarak, bir cmdlet kendi türü tanımlamanız gerekebilir veya başka bir cmdlet tarafından sağlanan mevcut türü genişletmek cmdlet gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="b10d0-165">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="b10d0-166">Yeni türleri tanımlama veya varolan türleri genişletme hakkında daha fazla bilgi için bkz. [genişletme nesne türleri ve biçimlendirme](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="b10d0-166">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="b10d0-167">Cmdlet oluşturma</span><span class="sxs-lookup"><span data-stu-id="b10d0-167">Building the Cmdlet</span></span>

<span data-ttu-id="b10d0-168">Bir cmdlet uyguladıktan sonra Windows PowerShell ile bir Windows PowerShell ek bileşeni kaydetmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="b10d0-168">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="b10d0-169">Cmdlet'leri kaydetme hakkında daha fazla bilgi için bkz. [kaydetme cmdlet'leri ve sağlayıcıları uygulamalarını barındırmak için nasıl](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="b10d0-169">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="b10d0-170">Sınama cmdlet'i</span><span class="sxs-lookup"><span data-stu-id="b10d0-170">Testing the Cmdlet</span></span>

<span data-ttu-id="b10d0-171">Windows PowerShell ile cmdlet'ini kaydedildi, komut satırında çalıştırarak test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b10d0-171">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="b10d0-172">Bizim örnek Get-Proc cmdlet'i için kod küçüktür, ancak yine de Windows PowerShell çalışma zamanı ve kullanışlı hale getirmek için yeterli olan mevcut bir .NET nesnesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="b10d0-172">The code for our sample Get-Proc cmdlet is small, but it still uses the Windows PowerShell runtime and an existing .NET object, which is enough to make it useful.</span></span> <span data-ttu-id="b10d0-173">Şimdi, Get-Proc neler yapabileceğinizi ve nasıl çıktısını kullanılabilir daha iyi anlamak için test edin.</span><span class="sxs-lookup"><span data-stu-id="b10d0-173">Let's test it to better understand what Get-Proc can do and how its output can be used.</span></span> <span data-ttu-id="b10d0-174">Komut satırından cmdlet'leri kullanma hakkında daha fazla bilgi için bkz. [Windows PowerShell ile çalışmaya başlama](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="b10d0-174">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

1. <span data-ttu-id="b10d0-175">Windows PowerShell'i başlatın ve bilgisayar üzerinde çalışan geçerli işlemler alın.</span><span class="sxs-lookup"><span data-stu-id="b10d0-175">Start Windows PowerShell, and get the current processes running on the computer.</span></span>

    ```powershell
    get-proc
    ```

    <span data-ttu-id="b10d0-176">Aşağıdaki çıktı görünür.</span><span class="sxs-lookup"><span data-stu-id="b10d0-176">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    254      7       7664   12048  66     173.75  1200  QCTRAY
    32       2       1372   2628   31       0.04  1860  DLG
    271      6       1216   3688   33       0.03  3816  lg
    27       2       560    1920   24       0.01  1768  TpScrex
    ...
    ```

2. <span data-ttu-id="b10d0-177">Cmdlet'i sonuçları daha kolay düzenlemesi için bir değişkene atayın.</span><span class="sxs-lookup"><span data-stu-id="b10d0-177">Assign a variable to the cmdlet results for easier manipulation.</span></span>

    ```powershell
    $p=get-proc
    ```

3. <span data-ttu-id="b10d0-178">İşlem sayısını alın.</span><span class="sxs-lookup"><span data-stu-id="b10d0-178">Get the number of processes.</span></span>

    ```powershell
    $p.length
    ```

    <span data-ttu-id="b10d0-179">Aşağıdaki çıktı görünür.</span><span class="sxs-lookup"><span data-stu-id="b10d0-179">The following output appears.</span></span>

    ```output
    63
    ```

4. <span data-ttu-id="b10d0-180">Belirli bir işlem alın.</span><span class="sxs-lookup"><span data-stu-id="b10d0-180">Retrieve a specific process.</span></span>

    ```powershell
    $p[6]
    ```

    <span data-ttu-id="b10d0-181">Aşağıdaki çıktı görünür.</span><span class="sxs-lookup"><span data-stu-id="b10d0-181">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id    ProcessName
    -------  ------  -----  -----  -----  ------  --    -----------
    1033     3       2400   3336   35     0.53    1588  rundll32
    ```

5. <span data-ttu-id="b10d0-182">Bu işlemin başlangıç zamanı alın.</span><span class="sxs-lookup"><span data-stu-id="b10d0-182">Get the start time of this process.</span></span>

    ```powershell
    $p[6].starttime
    ```

    <span data-ttu-id="b10d0-183">Aşağıdaki çıktı görünür.</span><span class="sxs-lookup"><span data-stu-id="b10d0-183">The following output appears.</span></span>

    ```output
    Tuesday, July 26, 2005 9:34:15 AM
    ```

    ```powershell
    $p[6].starttime.dayofyear
    ```

    ```output
    207
    ```

6. <span data-ttu-id="b10d0-184">Tanıtıcı sayısı 500'den büyük olan işlemleri Al ve sonucu sıralayın.</span><span class="sxs-lookup"><span data-stu-id="b10d0-184">Get the processes for which the handle count is greater than 500, and sort the result.</span></span>

    ```powershell
    $p | Where-Object {$_.HandleCount -gt 500 } | Sort-Object HandleCount
    ```

    <span data-ttu-id="b10d0-185">Aşağıdaki çıktı görünür.</span><span class="sxs-lookup"><span data-stu-id="b10d0-185">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    568      14      2164   4972   39     5.55    824  svchost
    716       7      2080   5332   28    25.38    468  csrss
    761      21      33060  56608  440  393.56    3300 WINWORD
    791      71      7412   4540   59     3.31    492  winlogon
    ...
    ```

7. <span data-ttu-id="b10d0-186">Kullanım `Get-Member` her işlem için kullanılabilen özellikleri listelemek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="b10d0-186">Use the `Get-Member` cmdlet to list the properties available for each process.</span></span>

    ```powershell
    $p | Get-Member -MemberType property
    ```

    ```output
        TypeName: System.Diagnostics.Process
    ```

    <span data-ttu-id="b10d0-187">Aşağıdaki çıktı görünür.</span><span class="sxs-lookup"><span data-stu-id="b10d0-187">The following output appears.</span></span>

    ```output
    Name                     MemberType Definition
    ----                     ---------- ----------
    BasePriority             Property   System.Int32 BasePriority {get;}
    Container                Property   System.ComponentModel.IContainer Conta...
    EnableRaisingEvents      Property   System.Boolean EnableRaisingEvents {ge...
    ...
    ```

## <a name="see-also"></a><span data-ttu-id="b10d0-188">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="b10d0-188">See Also</span></span>

[<span data-ttu-id="b10d0-189">Komut satırı girişi işlemek için bir Cmdlet oluşturma</span><span class="sxs-lookup"><span data-stu-id="b10d0-189">Creating a Cmdlet to Process Command Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="b10d0-190">İşlem hattı girdiyi işlemek üzere bir Cmdlet oluşturma</span><span class="sxs-lookup"><span data-stu-id="b10d0-190">Creating a Cmdlet to Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="b10d0-191">Bir Windows PowerShell cmdlet'i oluşturma</span><span class="sxs-lookup"><span data-stu-id="b10d0-191">How to Create a Windows PowerShell Cmdlet</span></span>](https://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[<span data-ttu-id="b10d0-192">Nesne türlerini genişletme ve biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="b10d0-192">Extending Object Types and Formatting</span></span>](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="b10d0-193">Windows PowerShell nasıl çalışır?</span><span class="sxs-lookup"><span data-stu-id="b10d0-193">How Windows PowerShell Works</span></span>](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[<span data-ttu-id="b10d0-194">Cmdlet, sağlayıcılar kaydetmek ve uygulamaları barındırmak nasıl</span><span class="sxs-lookup"><span data-stu-id="b10d0-194">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="b10d0-195">Windows PowerShell başvurusu</span><span class="sxs-lookup"><span data-stu-id="b10d0-195">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="b10d0-196">Cmdlet örnekleri</span><span class="sxs-lookup"><span data-stu-id="b10d0-196">Cmdlet Samples</span></span>](./cmdlet-samples.md)