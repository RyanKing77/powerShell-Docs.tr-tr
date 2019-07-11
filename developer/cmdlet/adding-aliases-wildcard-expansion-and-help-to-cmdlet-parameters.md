---
title: Diğer adları, joker karakter genişletmesi, ekleme ve Cmdlet parametreleri için Yardım | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 931ccace-c565-4a98-8dcc-df00f86394b1
caps.latest.revision: 8
ms.openlocfilehash: bc921537062e35aa203fa3ee95d3b7211c89cb28
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67733838"
---
# <a name="adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters"></a><span data-ttu-id="1acd0-102">Cmdlet Parametrelerinize Diğer Adlar, Joker Karakter Genişletmesi ve Yardım Ekleme</span><span class="sxs-lookup"><span data-stu-id="1acd0-102">Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters</span></span>

<span data-ttu-id="1acd0-103">Bu bölümde, diğer adları, joker karakter genişletmesi eklemeyi açıklar ve Yardım iletileri Stop-Proc cmdlet parametreleri (açıklanan [bir Cmdlet oluşturma sistemi değiştirir](./creating-a-cmdlet-that-modifies-the-system.md)).</span><span class="sxs-lookup"><span data-stu-id="1acd0-103">This section describes how to add aliases, wildcard expansion, and Help messages to the parameters of the Stop-Proc cmdlet (described in [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md)).</span></span>

<span data-ttu-id="1acd0-104">Bu Stop-Proc cmdlet Get-Proc cmdlet'ini kullanarak alınan işlemler durdurmaya çalışır (açıklanan [oluşturma bilgisayarınızı ilk Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span><span class="sxs-lookup"><span data-stu-id="1acd0-104">This Stop-Proc cmdlet attempts to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="1acd0-105">Cmdlet tanımlama</span><span class="sxs-lookup"><span data-stu-id="1acd0-105">Defining the Cmdlet</span></span>

<span data-ttu-id="1acd0-106">İlk adımda cmdlet'i oluşturma her zaman cmdlet adlandırma ve cmdlet uygulayan .NET sınıf bildirme.</span><span class="sxs-lookup"><span data-stu-id="1acd0-106">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="1acd0-107">Sistem değiştirmek için bir cmdlet yazıyorsanız olduğundan, buna uygun olarak adlandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1acd0-107">Because you are writing a cmdlet to change the system, it should be named accordingly.</span></span> <span data-ttu-id="1acd0-108">Bu cmdlet, sistem işlemleri durdurur, bu tarafından tanımlanan fiil "Durdur" kullanır, çünkü [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) sınıfıyla isim işlemi göstermek için "işlem".</span><span class="sxs-lookup"><span data-stu-id="1acd0-108">Because this cmdlet stops system processes, it uses the verb "Stop", defined by the [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) class, with the noun "Proc" to indicate process.</span></span> <span data-ttu-id="1acd0-109">Onaylanan cmdlet fiilleri hakkında daha fazla bilgi için bkz: [Cmdlet fiili adları](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="1acd0-109">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="1acd0-110">Aşağıdaki kod bu Stop-Proc cmdlet'in sınıfı tanımıdır.</span><span class="sxs-lookup"><span data-stu-id="1acd0-110">The following code is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="1acd0-111">Sistem değiştirilmesi için parametreleri tanımlama</span><span class="sxs-lookup"><span data-stu-id="1acd0-111">Defining Parameters for System Modification</span></span>

<span data-ttu-id="1acd0-112">Bu destek sistem değişiklikleri ve kullanıcı geri bildirimi parametrelerini tanımlamak, cmdlet gerekir.</span><span class="sxs-lookup"><span data-stu-id="1acd0-112">Your cmdlet needs to define parameters that support system modifications and user feedback.</span></span> <span data-ttu-id="1acd0-113">Cmdlet tanımlamalıdır bir `Name` parametresi veya eşdeğer bir böylece cmdlet'i bir tür tanımlayıcısı tarafından sistem değiştirmek mümkün olacaktır.</span><span class="sxs-lookup"><span data-stu-id="1acd0-113">The cmdlet should define a `Name` parameter or equivalent so that the cmdlet will be able to modify the system by some sort of identifier.</span></span> <span data-ttu-id="1acd0-114">Ayrıca, cmdlet tanımlamalıdır `Force` ve `PassThru` parametreleri.</span><span class="sxs-lookup"><span data-stu-id="1acd0-114">In addition, the cmdlet should define the `Force` and `PassThru` parameters.</span></span> <span data-ttu-id="1acd0-115">Bu parametreler hakkında daha fazla bilgi için bkz. [bir Cmdlet oluşturma sistemi değiştirir](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="1acd0-115">For more information about these parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="defining-a-parameter-alias"></a><span data-ttu-id="1acd0-116">Bir parametre diğer adını tanımlama</span><span class="sxs-lookup"><span data-stu-id="1acd0-116">Defining a Parameter Alias</span></span>

<span data-ttu-id="1acd0-117">Bir parametre diğer adı, başka bir ad veya bir cmdlet parametresi için iyi tanımlanmış bir 1 harf veya harf 2 kısa ad olabilir.</span><span class="sxs-lookup"><span data-stu-id="1acd0-117">A parameter alias can be an alternate name or a well-defined 1-letter or 2-letter short name for a cmdlet parameter.</span></span> <span data-ttu-id="1acd0-118">Her iki durumda da, diğer adlarını kullanma amacıyla komut satırından kullanıcı girişi kolaylaştırmaktır.</span><span class="sxs-lookup"><span data-stu-id="1acd0-118">In both cases, the goal of using aliases is to simplify user entry from the command line.</span></span> <span data-ttu-id="1acd0-119">Windows PowerShell aracılığıyla parametre diğer adlarına destekler [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) kullanan bildiriminin sözdizimi [Alias()] özniteliği.</span><span class="sxs-lookup"><span data-stu-id="1acd0-119">Windows PowerShell supports parameter aliases through the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, which uses the declaration syntax [Alias()].</span></span>

<span data-ttu-id="1acd0-120">Aşağıdaki kod bir diğer ad nasıl eklenir gösterir `Name` parametresi.</span><span class="sxs-lookup"><span data-stu-id="1acd0-120">The following code shows how an alias is added to the `Name` parameter.</span></span>

```csharp
/// <summary>
/// Specify the mandatory Name parameter used to identify the
/// processes to be stopped.
/// </summary>
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true,
           HelpMessage = "The name of one or more processes to stop. Wildcards are permitted."
)]
[Alias("ProcessName")]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;
```

<span data-ttu-id="1acd0-121">Kullanmanın yanı sıra [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) özniteliği, Windows PowerShell çalışma zamanı gerçekleştirir kısmi adıyla eşleşen, bile takma ad yok.</span><span class="sxs-lookup"><span data-stu-id="1acd0-121">In addition to using the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, the Windows PowerShell runtime performs partial name matching, even if no aliases are specified.</span></span> <span data-ttu-id="1acd0-122">Cmdlet'inize varsa, örneğin, bir `FileName` parametresi ve diğer bir deyişle ile başlayan tek parametre `F`, kullanıcı girebilirsiniz `Filename`, `Filenam`, `File`, `Fi`, veya `F` ve hala tanıması Giriş olarak `FileName` parametresi.</span><span class="sxs-lookup"><span data-stu-id="1acd0-122">For example, if your cmdlet has a `FileName` parameter and that is the only parameter that starts with `F`, the user could enter `Filename`, `Filenam`, `File`, `Fi`, or `F` and still recognize the entry as the `FileName` parameter.</span></span>

## <a name="creating-help-for-parameters"></a><span data-ttu-id="1acd0-123">Parametreleri için Yardım'ı oluşturma</span><span class="sxs-lookup"><span data-stu-id="1acd0-123">Creating Help for Parameters</span></span>

<span data-ttu-id="1acd0-124">Windows PowerShell cmdlet parametreleri için Yardım oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="1acd0-124">Windows PowerShell allows you to create Help for cmdlet parameters.</span></span> <span data-ttu-id="1acd0-125">Sistemi değişikliği ve kullanıcı geri bildirimi için kullanılan herhangi bir parametre için bunu yapın.</span><span class="sxs-lookup"><span data-stu-id="1acd0-125">Do this for any parameter used for system modification and user feedback.</span></span> <span data-ttu-id="1acd0-126">Yardım'ı desteklemek üzere her parametre için ayarladığınız `HelpMessage` anahtar öznitelik [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) öznitelik bildirimi.</span><span class="sxs-lookup"><span data-stu-id="1acd0-126">For each parameter to support Help, you can set the `HelpMessage` attribute keyword in the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration.</span></span> <span data-ttu-id="1acd0-127">Bu anahtar sözcük parametresini kullanma konusunda yardım almak için kullanıcıya görüntülenecek metni tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1acd0-127">This keyword defines the text to display to the user for assistance in using the parameter.</span></span> <span data-ttu-id="1acd0-128">Ayrıca `HelpMessageBaseName` ileti için kullanılacak bir kaynak temel adı tanımlamak için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="1acd0-128">You can also set the `HelpMessageBaseName` keyword to identify the base name of a resource to use for the message.</span></span> <span data-ttu-id="1acd0-129">Bu anahtar sözcük ayarlarsanız de ayarlamalısınız `HelpMessageResourceId` kaynak tanımlayıcısını belirtmek için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="1acd0-129">If you set this keyword, you must also set the `HelpMessageResourceId` keyword to specify the resource identifier.</span></span>

<span data-ttu-id="1acd0-130">Aşağıdaki kod bu Proc Stop cmdlet'inden tanımlar `HelpMessage` anahtar sözcüğü için öznitelik `Name` parametresi.</span><span class="sxs-lookup"><span data-stu-id="1acd0-130">The following code from this Stop-Proc cmdlet defines the `HelpMessage` attribute keyword for the `Name` parameter.</span></span>

```csharp
/// <summary>
/// Specify the mandatory Name parameter used to identify the
/// processes to be stopped.
/// </summary>
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true,
           HelpMessage = "The name of one or more processes to stop. Wildcards are permitted."
)]
```

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="1acd0-131">Bir giriş işleme yöntemi geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="1acd0-131">Overriding an Input Processing Method</span></span>

<span data-ttu-id="1acd0-132">Cmdlet'inize işleme yöntemi giriş geçersiz kılmanız gerekir, bu genellikle olacaktır [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span><span class="sxs-lookup"><span data-stu-id="1acd0-132">Your cmdlet must override an input processing method, most often this will be [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span></span> <span data-ttu-id="1acd0-133">Sistem değiştirirken, cmdlet çağırmalıdır [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) ve [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) izin vermek için yöntemleri bir değişiklik yapılmadan önce geri bildirim sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="1acd0-133">When modifying the system, the cmdlet should call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods to allow the user to provide feedback before a change is made.</span></span> <span data-ttu-id="1acd0-134">Bu yöntemler hakkında daha fazla bilgi için bkz. [bir Cmdlet oluşturma sistemi değiştirir](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="1acd0-134">For more information about these methods, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="supporting-wildcard-expansion"></a><span data-ttu-id="1acd0-135">Joker karakter genişletmesi destekleme</span><span class="sxs-lookup"><span data-stu-id="1acd0-135">Supporting Wildcard Expansion</span></span>

<span data-ttu-id="1acd0-136">Birden çok nesne seçimi izin vermek için cmdlet'i kullanabilirsiniz [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) ve [System.Management.Automation.Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) sağlayan sınıflar Giriş parametresi joker karakter genişletmesi desteği.</span><span class="sxs-lookup"><span data-stu-id="1acd0-136">To allow the selection of multiple objects, your cmdlet can use the [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) and [System.Management.Automation.Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) classes to provide wildcard expansion support for parameter input.</span></span> <span data-ttu-id="1acd0-137">Joker karakter düzeni örnekleri olan lsa \* \*.txt ve [a-c]\*.</span><span class="sxs-lookup"><span data-stu-id="1acd0-137">Examples of wildcard patterns are lsa\*, \*.txt, and [a-c]\*.</span></span> <span data-ttu-id="1acd0-138">Desen, tam anlamıyla kullanılması gereken bir karakter içerdiğinde bir kaçış karakteri geriye tırnak işareti karakteri (') kullanın.</span><span class="sxs-lookup"><span data-stu-id="1acd0-138">Use the back-quote character (\`) as an escape character when the pattern contains a character that should be used literally.</span></span>

<span data-ttu-id="1acd0-139">Dosya ve yol adları joker genişletmeleri burada cmdlet'ini birden çok nesne seçimi gerekli olduğunda yolu girişleri için destek isteyebilirsiniz yaygın senaryoları bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="1acd0-139">Wildcard expansions of file and path names are examples of common scenarios where the cmdlet may want to allow support for path inputs when the selection of multiple objects is required.</span></span> <span data-ttu-id="1acd0-140">Burada geçerli klasörde bulunan tüm dosyaları görmek için bir kullanıcının istediği dosya sistemindeki genel durumu gösterir.</span><span class="sxs-lookup"><span data-stu-id="1acd0-140">A common case is in the file system, where a user wants to see all files residing in the current folder.</span></span>

<span data-ttu-id="1acd0-141">Nadiren özelleştirilmiş joker karakter deseni eşleştirme uygulaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1acd0-141">You should need a customized wildcard pattern matching implementation only rarely.</span></span> <span data-ttu-id="1acd0-142">Bu durumda, cmdlet'inize tam POSIX 1003.2, joker karakter genişletmesi 3.13 belirtimi veya aşağıdaki Basitleştirilmiş alt desteklemesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="1acd0-142">In this case, your cmdlet should support either the full POSIX 1003.2, 3.13 specification for wildcard expansion or the following simplified subset:</span></span>

- <span data-ttu-id="1acd0-143">**Soru işareti (?).**</span><span class="sxs-lookup"><span data-stu-id="1acd0-143">**Question mark (?).**</span></span> <span data-ttu-id="1acd0-144">Belirtilen konumda herhangi bir karakterle eşleşir.</span><span class="sxs-lookup"><span data-stu-id="1acd0-144">Matches any character at the specified location.</span></span>

- <span data-ttu-id="1acd0-145">**Yıldız işareti (\*).**</span><span class="sxs-lookup"><span data-stu-id="1acd0-145">**Asterisk (\*).**</span></span> <span data-ttu-id="1acd0-146">Belirtilen konumundan başlayan sıfır veya daha fazla karakter ile eşleşir.</span><span class="sxs-lookup"><span data-stu-id="1acd0-146">Matches zero or more characters starting at the specified location.</span></span>

- <span data-ttu-id="1acd0-147">**Köşeli ayraç ([]) açın.**</span><span class="sxs-lookup"><span data-stu-id="1acd0-147">**Open bracket ([).**</span></span> <span data-ttu-id="1acd0-148">Karakter ya da karakter aralığını içerebilir bir desen köşeli ayraç ifadesi tanıtır.</span><span class="sxs-lookup"><span data-stu-id="1acd0-148">Introduces a pattern bracket expression that can contain characters or a range of characters.</span></span> <span data-ttu-id="1acd0-149">Bir aralık gerekiyorsa, tire (-) aralığını belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1acd0-149">If a range is required, a hyphen (-) is used to indicate the range.</span></span>

- <span data-ttu-id="1acd0-150">**Kapatma köşeli ayraç (]).**</span><span class="sxs-lookup"><span data-stu-id="1acd0-150">**Close bracket (]).**</span></span> <span data-ttu-id="1acd0-151">Bir desen köşeli ayraç ifadesi sona erer.</span><span class="sxs-lookup"><span data-stu-id="1acd0-151">Ends a pattern bracket expression.</span></span>

- <span data-ttu-id="1acd0-152">**Arka-teklif kaçış karakteri (').**</span><span class="sxs-lookup"><span data-stu-id="1acd0-152">**Back-quote escape character (\`).**</span></span> <span data-ttu-id="1acd0-153">Sonraki karakteri tam anlamıyla alınması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="1acd0-153">Indicates that the next character should be taken literally.</span></span> <span data-ttu-id="1acd0-154">(Programlı olarak belirtme) yerine komut satırından geri tırnak karakteri belirtirken, geri teklif kaçış karakteri'nin iki kez belirtilmiş gerekir dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="1acd0-154">Be aware that when specifying the back-quote character from the command line (as opposed to specifying it programmatically), the back-quote escape character must be specified twice.</span></span>

> [!NOTE]
> <span data-ttu-id="1acd0-155">Joker karakter düzenleri hakkında daha fazla bilgi için bkz: [joker karakterleri destekleme Cmdlet parametreleri](./supporting-wildcard-characters-in-cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="1acd0-155">For more information about wildcard patterns, see [Supporting Wildcards in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md).</span></span>

<span data-ttu-id="1acd0-156">Aşağıdaki kod, joker karakter seçeneklerini ayarlayın ve çözümlemek için kullanılan joker karakter deseni tanımlamak gösterilmektedir `Name` Bu cmdlet için parametre.</span><span class="sxs-lookup"><span data-stu-id="1acd0-156">The following code shows how to set wildcard options and define the wildcard pattern used for resolving the `Name` parameter for this cmdlet.</span></span>

```csharp
WildcardOptions options = WildcardOptions.IgnoreCase |
                          WildcardOptions.Compiled;
WildcardPattern wildcard = new WildcardPattern(name,options);
```

<span data-ttu-id="1acd0-157">Aşağıdaki kod, test etme, işlem adı tanımlanmış bir joker karakter deseni ile eşleşip eşleşmediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="1acd0-157">The following code shows how to test whether the process name matches the defined wildcard pattern.</span></span> <span data-ttu-id="1acd0-158">İşlem adı desenle eşleşmez, bu durumda, cmdlet üzerinde sonraki işlem adı alma devam ettiğinden, dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="1acd0-158">Notice that, in this case, if the process name does not match the pattern, the cmdlet continues on to get the next process name.</span></span>

```csharp
if (!wildcard.IsMatch(processName))
{
  continue;
}
```

## <a name="code-sample"></a><span data-ttu-id="1acd0-159">Kod örneği</span><span class="sxs-lookup"><span data-stu-id="1acd0-159">Code Sample</span></span>

<span data-ttu-id="1acd0-160">Tamamlanmış C# örnek kod için bkz: [StopProcessSample03 örnek](./stopprocesssample03-sample.md).</span><span class="sxs-lookup"><span data-stu-id="1acd0-160">For the complete C# sample code, see [StopProcessSample03 Sample](./stopprocesssample03-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="1acd0-161">Nesne türleri ve biçimlendirme tanımlayın</span><span class="sxs-lookup"><span data-stu-id="1acd0-161">Define Object Types and Formatting</span></span>

<span data-ttu-id="1acd0-162">Windows PowerShell cmdlet arasında .net nesneleri kullanarak bilgileri geçirir.</span><span class="sxs-lookup"><span data-stu-id="1acd0-162">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="1acd0-163">Sonuç olarak, bir cmdlet kendi türü tanımlamanız gerekebilir veya başka bir cmdlet tarafından sağlanan mevcut türü genişletmek cmdlet gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="1acd0-163">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="1acd0-164">Yeni türleri tanımlama veya varolan türleri genişletme hakkında daha fazla bilgi için bkz. [genişletme nesne türleri ve biçimlendirme](/previous-versions//ms714665(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="1acd0-164">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="1acd0-165">Cmdlet oluşturma</span><span class="sxs-lookup"><span data-stu-id="1acd0-165">Building the Cmdlet</span></span>

<span data-ttu-id="1acd0-166">Bir cmdlet uyguladıktan sonra bunu Windows PowerShell ile bir Windows PowerShell ek bileşeni kayıtlı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1acd0-166">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="1acd0-167">Cmdlet'leri kaydetme hakkında daha fazla bilgi için bkz. [kaydetme cmdlet'leri ve sağlayıcıları uygulamalarını barındırmak için nasıl](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="1acd0-167">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="1acd0-168">Sınama cmdlet'i</span><span class="sxs-lookup"><span data-stu-id="1acd0-168">Testing the Cmdlet</span></span>

<span data-ttu-id="1acd0-169">Windows PowerShell ile cmdlet'ini kaydedildi, komut satırında çalıştırarak test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1acd0-169">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="1acd0-170">Şimdi örnek Stop-Proc cmdlet test edin.</span><span class="sxs-lookup"><span data-stu-id="1acd0-170">Let's test the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="1acd0-171">Komut satırından cmdlet'leri kullanma hakkında daha fazla bilgi için bkz. [Windows PowerShell ile çalışmaya başlama](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="1acd0-171">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="1acd0-172">Windows PowerShell'i başlatın ve ProcessName diğer kullanarak işlemi durdurmak için Stop-Proc `Name` parametresi.</span><span class="sxs-lookup"><span data-stu-id="1acd0-172">Start Windows PowerShell and use Stop-Proc to stop a process using the ProcessName alias for the `Name` parameter.</span></span>

    ```powershell
    PS> stop-proc -ProcessName notepad
    ```

<span data-ttu-id="1acd0-173">Aşağıdaki çıktı görünür.</span><span class="sxs-lookup"><span data-stu-id="1acd0-173">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (3496)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="1acd0-174">Komut satırında aşağıdaki giriş yapın.</span><span class="sxs-lookup"><span data-stu-id="1acd0-174">Make the following entry on the command line.</span></span> <span data-ttu-id="1acd0-175">Name parametresi zorunlu olduğundan istenir.</span><span class="sxs-lookup"><span data-stu-id="1acd0-175">Because the Name parameter is mandatory, you are prompted for it.</span></span> <span data-ttu-id="1acd0-176">Girme "!?"</span><span class="sxs-lookup"><span data-stu-id="1acd0-176">Entering "!?"</span></span> <span data-ttu-id="1acd0-177">parametresiyle ilgili Yardım metnini getirir.</span><span class="sxs-lookup"><span data-stu-id="1acd0-177">brings up the help text associated with the parameter.</span></span>

    ```powershell
    PS> stop-proc
    ```

<span data-ttu-id="1acd0-178">Aşağıdaki çıktı görünür.</span><span class="sxs-lookup"><span data-stu-id="1acd0-178">The following output appears.</span></span>

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    (Type !? for Help.)
    Name[0]: !?
    The name of one or more processes to stop. Wildcards are permitted.
    Name[0]: notepad
    ```

- <span data-ttu-id="1acd0-179">Artık joker karakter deseni ile eşleşen tüm işlemler durdurmak için şu girdiyi olun "\* Not\*".</span><span class="sxs-lookup"><span data-stu-id="1acd0-179">Now make the following entry to stop all processes that match the wildcard pattern "\*note\*".</span></span> <span data-ttu-id="1acd0-180">Desenle eşleşen her işlemi durdurmadan önce istenir.</span><span class="sxs-lookup"><span data-stu-id="1acd0-180">You are prompted before stopping each process that matches the pattern.</span></span>

    ```powershell
    PS> stop-proc -Name *note*
    ```

<span data-ttu-id="1acd0-181">Aşağıdaki çıktı görünür.</span><span class="sxs-lookup"><span data-stu-id="1acd0-181">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (1112)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

<span data-ttu-id="1acd0-182">Aşağıdaki çıktı görünür.</span><span class="sxs-lookup"><span data-stu-id="1acd0-182">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTEM (3712)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

<span data-ttu-id="1acd0-183">Aşağıdaki çıktı görünür.</span><span class="sxs-lookup"><span data-stu-id="1acd0-183">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTE (3592)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="1acd0-184">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="1acd0-184">See Also</span></span>

[<span data-ttu-id="1acd0-185">Sistem değiştiren bir Cmdlet oluşturma</span><span class="sxs-lookup"><span data-stu-id="1acd0-185">Create a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="1acd0-186">Bir Windows PowerShell cmdlet'i oluşturma</span><span class="sxs-lookup"><span data-stu-id="1acd0-186">How to Create a Windows PowerShell Cmdlet</span></span>](/powershell/developer/cmdlet/writing-a-windows-powershell-cmdlet)

<span data-ttu-id="1acd0-187">[Nesne türlerini genişletme ve biçimlendirme](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="1acd0-187">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="1acd0-188">[Cmdlet, sağlayıcılar kaydetmek ve uygulamaları barındırmak nasıl](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="1acd0-188">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="1acd0-189">Cmdlet parametreleri joker karakterleri destekleme</span><span class="sxs-lookup"><span data-stu-id="1acd0-189">Supporting Wildcards in Cmdlet Parameters</span></span>](./supporting-wildcard-characters-in-cmdlet-parameters.md)

[<span data-ttu-id="1acd0-190">Windows PowerShell SDK'sı</span><span class="sxs-lookup"><span data-stu-id="1acd0-190">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
