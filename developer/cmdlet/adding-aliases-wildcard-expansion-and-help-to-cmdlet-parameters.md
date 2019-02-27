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
ms.openlocfilehash: 0f025213087e6f308adf8e597fc01c1320251f76
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849143"
---
# <a name="adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters"></a><span data-ttu-id="abdb0-102">Cmdlet Parametrelerinize Diğer Adlar, Joker Karakter Genişletmesi ve Yardım Ekleme</span><span class="sxs-lookup"><span data-stu-id="abdb0-102">Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters</span></span>

<span data-ttu-id="abdb0-103">Bu bölümde, diğer adları, joker karakter genişletmesi eklemeyi açıklar ve Yardım iletileri Stop-Proc cmdlet parametreleri (açıklanan [bir Cmdlet oluşturma sistemi değiştirir](./creating-a-cmdlet-that-modifies-the-system.md)).</span><span class="sxs-lookup"><span data-stu-id="abdb0-103">This section describes how to add aliases, wildcard expansion, and Help messages to the parameters of the Stop-Proc cmdlet (described in [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md)).</span></span>

<span data-ttu-id="abdb0-104">Bu Stop-Proc cmdlet Get-Proc cmdlet'ini kullanarak alınan işlemler durdurmaya çalışır (açıklanan [oluşturma bilgisayarınızı ilk Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span><span class="sxs-lookup"><span data-stu-id="abdb0-104">This Stop-Proc cmdlet attempts to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span></span>

<span data-ttu-id="abdb0-105">Bu bölümdeki konular şunlardır:</span><span class="sxs-lookup"><span data-stu-id="abdb0-105">Topics in this section include the following:</span></span>

- [<span data-ttu-id="abdb0-106">Cmdlet tanımlama</span><span class="sxs-lookup"><span data-stu-id="abdb0-106">Defining the Cmdlet</span></span>](#Defining-the-Cmdlet)

- [<span data-ttu-id="abdb0-107">Sistem değiştirilmesi için parametreleri tanımlama</span><span class="sxs-lookup"><span data-stu-id="abdb0-107">Defining Parameters for System Modification</span></span>](#Defining-Parameters-for-System-Modification)

- [<span data-ttu-id="abdb0-108">Bir parametre diğer adını tanımlama</span><span class="sxs-lookup"><span data-stu-id="abdb0-108">Defining a Parameter Alias</span></span>](#Defining-a-Parameter-Alias)

- [<span data-ttu-id="abdb0-109">Parametreleri için Yardım'ı oluşturma</span><span class="sxs-lookup"><span data-stu-id="abdb0-109">Creating Help for Parameters</span></span>](#Creating-Help-for-Parameters)

- [<span data-ttu-id="abdb0-110">Bir giriş işleme yöntemi geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="abdb0-110">Overriding an Input Processing Method</span></span>](#Overriding-an-Input-Processing-Method)

- [<span data-ttu-id="abdb0-111">Joker karakter genişletmesi destekleme</span><span class="sxs-lookup"><span data-stu-id="abdb0-111">Supporting Wildcard Expansion</span></span>](#Supporting-Wildcard-Expansion)

- [<span data-ttu-id="abdb0-112">Kod örneği</span><span class="sxs-lookup"><span data-stu-id="abdb0-112">Code Sample</span></span>](#Defining-a-Parameter-Alias)

- [<span data-ttu-id="abdb0-113">Nesne türlerini tanımlama ve biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="abdb0-113">Defining Object Types and Formatting</span></span>](#Define-Object-Types-and-Formatting)

- [<span data-ttu-id="abdb0-114">Cmdlet oluşturma</span><span class="sxs-lookup"><span data-stu-id="abdb0-114">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="abdb0-115">Sınama cmdlet'i</span><span class="sxs-lookup"><span data-stu-id="abdb0-115">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a><span data-ttu-id="abdb0-116">Cmdlet tanımlama</span><span class="sxs-lookup"><span data-stu-id="abdb0-116">Defining the Cmdlet</span></span>

<span data-ttu-id="abdb0-117">İlk adımda cmdlet'i oluşturma her zaman cmdlet adlandırma ve cmdlet uygulayan .NET sınıf bildirme.</span><span class="sxs-lookup"><span data-stu-id="abdb0-117">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="abdb0-118">Sistem değiştirmek için bir cmdlet yazıyorsanız olduğundan, buna uygun olarak adlandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="abdb0-118">Because you are writing a cmdlet to change the system, it should be named accordingly.</span></span> <span data-ttu-id="abdb0-119">Bu cmdlet, sistem işlemleri durdurur, bu tarafından tanımlanan fiil "Durdur" kullanır, çünkü [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) sınıfıyla isim işlemi göstermek için "işlem".</span><span class="sxs-lookup"><span data-stu-id="abdb0-119">Because this cmdlet stops system processes, it uses the verb "Stop", defined by the [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) class, with the noun "Proc" to indicate process.</span></span> <span data-ttu-id="abdb0-120">Onaylanan cmdlet fiilleri hakkında daha fazla bilgi için bkz: [Cmdlet fiili adları](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="abdb0-120">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="abdb0-121">Aşağıdaki kod bu Stop-Proc cmdlet'in sınıfı tanımıdır.</span><span class="sxs-lookup"><span data-stu-id="abdb0-121">The following code is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="abdb0-122">Sistem değiştirilmesi için parametreleri tanımlama</span><span class="sxs-lookup"><span data-stu-id="abdb0-122">Defining Parameters for System Modification</span></span>

<span data-ttu-id="abdb0-123">Bu destek sistem değişiklikleri ve kullanıcı geri bildirimi parametrelerini tanımlamak, cmdlet gerekir.</span><span class="sxs-lookup"><span data-stu-id="abdb0-123">Your cmdlet needs to define parameters that support system modifications and user feedback.</span></span> <span data-ttu-id="abdb0-124">Cmdlet tanımlamalıdır bir `Name` parametresi veya eşdeğer bir böylece cmdlet'i bir tür tanımlayıcısı tarafından sistem değiştirmek mümkün olacaktır.</span><span class="sxs-lookup"><span data-stu-id="abdb0-124">The cmdlet should define a `Name` parameter or equivalent so that the cmdlet will be able to modify the system by some sort of identifier.</span></span> <span data-ttu-id="abdb0-125">Ayrıca, cmdlet tanımlamalıdır `Force` ve `PassThru` parametreleri.</span><span class="sxs-lookup"><span data-stu-id="abdb0-125">In addition, the cmdlet should define the `Force` and `PassThru` parameters.</span></span> <span data-ttu-id="abdb0-126">Bu parametreler hakkında daha fazla bilgi için bkz. [bir Cmdlet oluşturma sistemi değiştirir](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="abdb0-126">For more information about these parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="defining-a-parameter-alias"></a><span data-ttu-id="abdb0-127">Bir parametre diğer adını tanımlama</span><span class="sxs-lookup"><span data-stu-id="abdb0-127">Defining a Parameter Alias</span></span>

<span data-ttu-id="abdb0-128">Bir parametre diğer adı, başka bir ad veya bir cmdlet parametresi için iyi tanımlanmış bir 1 harf veya harf 2 kısa ad olabilir.</span><span class="sxs-lookup"><span data-stu-id="abdb0-128">A parameter alias can be an alternate name or a well-defined 1-letter or 2-letter short name for a cmdlet parameter.</span></span> <span data-ttu-id="abdb0-129">Her iki durumda da, diğer adlarını kullanma amacıyla komut satırından kullanıcı girişi kolaylaştırmaktır.</span><span class="sxs-lookup"><span data-stu-id="abdb0-129">In both cases, the goal of using aliases is to simplify user entry from the command line.</span></span> <span data-ttu-id="abdb0-130">Windows PowerShell aracılığıyla parametre diğer adlarına destekler [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) kullanan bildiriminin sözdizimi [Alias()] özniteliği.</span><span class="sxs-lookup"><span data-stu-id="abdb0-130">Windows PowerShell supports parameter aliases through the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, which uses the declaration syntax [Alias()].</span></span>

<span data-ttu-id="abdb0-131">Aşağıdaki kod bir diğer ad nasıl eklenir gösterir `Name` parametresi.</span><span class="sxs-lookup"><span data-stu-id="abdb0-131">The following code shows how an alias is added to the `Name` parameter.</span></span>

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

<span data-ttu-id="abdb0-132">Kullanmanın yanı sıra [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) özniteliği, Windows PowerShell çalışma zamanı gerçekleştirir kısmi adıyla eşleşen, bile takma ad yok.</span><span class="sxs-lookup"><span data-stu-id="abdb0-132">In addition to using the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, the Windows PowerShell runtime performs partial name matching, even if no aliases are specified.</span></span> <span data-ttu-id="abdb0-133">Cmdlet'inize varsa, örneğin, bir `FileName` parametresi ve diğer bir deyişle ile başlayan tek parametre `F`, kullanıcı girebilirsiniz `Filename`, `Filenam`, `File`, `Fi`, veya `F` ve hala tanıması Giriş olarak `FileName` parametresi.</span><span class="sxs-lookup"><span data-stu-id="abdb0-133">For example, if your cmdlet has a `FileName` parameter and that is the only parameter that starts with `F`, the user could enter `Filename`, `Filenam`, `File`, `Fi`, or `F` and still recognize the entry as the `FileName` parameter.</span></span>

## <a name="creating-help-for-parameters"></a><span data-ttu-id="abdb0-134">Parametreleri için Yardım'ı oluşturma</span><span class="sxs-lookup"><span data-stu-id="abdb0-134">Creating Help for Parameters</span></span>

<span data-ttu-id="abdb0-135">Windows PowerShell cmdlet parametreleri için Yardım oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="abdb0-135">Windows PowerShell allows you to create Help for cmdlet parameters.</span></span> <span data-ttu-id="abdb0-136">Sistemi değişikliği ve kullanıcı geri bildirimi için kullanılan herhangi bir parametre için bunu yapın.</span><span class="sxs-lookup"><span data-stu-id="abdb0-136">Do this for any parameter used for system modification and user feedback.</span></span> <span data-ttu-id="abdb0-137">Yardım'ı desteklemek üzere her parametre için ayarladığınız `HelpMessage` anahtar öznitelik [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) öznitelik bildirimi.</span><span class="sxs-lookup"><span data-stu-id="abdb0-137">For each parameter to support Help, you can set the `HelpMessage` attribute keyword in the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration.</span></span> <span data-ttu-id="abdb0-138">Bu anahtar sözcük parametresini kullanma konusunda yardım almak için kullanıcıya görüntülenecek metni tanımlar.</span><span class="sxs-lookup"><span data-stu-id="abdb0-138">This keyword defines the text to display to the user for assistance in using the parameter.</span></span> <span data-ttu-id="abdb0-139">Ayrıca `HelpMessageBaseName` ileti için kullanılacak bir kaynak temel adı tanımlamak için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="abdb0-139">You can also set the `HelpMessageBaseName` keyword to identify the base name of a resource to use for the message.</span></span> <span data-ttu-id="abdb0-140">Bu anahtar sözcük ayarlarsanız de ayarlamalısınız `HelpMessageResourceId` kaynak tanımlayıcısını belirtmek için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="abdb0-140">If you set this keyword, you must also set the `HelpMessageResourceId` keyword to specify the resource identifier.</span></span>

<span data-ttu-id="abdb0-141">Aşağıdaki kod bu Proc Stop cmdlet'inden tanımlar `HelpMessage` anahtar sözcüğü için öznitelik `Name` parametresi.</span><span class="sxs-lookup"><span data-stu-id="abdb0-141">The following code from this Stop-Proc cmdlet defines the `HelpMessage` attribute keyword for the `Name` parameter.</span></span>

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

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="abdb0-142">Bir giriş işleme yöntemi geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="abdb0-142">Overriding an Input Processing Method</span></span>

<span data-ttu-id="abdb0-143">Cmdlet'inize işleme yöntemi giriş geçersiz kılmanız gerekir, bu genellikle olacaktır [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span><span class="sxs-lookup"><span data-stu-id="abdb0-143">Your cmdlet must override an input processing method, most often this will be [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span></span> <span data-ttu-id="abdb0-144">Sistem değiştirirken, cmdlet çağırmalıdır [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) ve [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) izin veren yöntemleri bir değişiklik yapılmadan önce geri bildirim sağlamak için kullanıcı.</span><span class="sxs-lookup"><span data-stu-id="abdb0-144">When modifying the system, the cmdlet should call the [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods to allow the user to provide feedback before a change is made.</span></span> <span data-ttu-id="abdb0-145">Bu yöntemler hakkında daha fazla bilgi için bkz. [bir Cmdlet oluşturma sistemi değiştirir](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="abdb0-145">For more information about these methods, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="supporting-wildcard-expansion"></a><span data-ttu-id="abdb0-146">Joker karakter genişletmesi destekleme</span><span class="sxs-lookup"><span data-stu-id="abdb0-146">Supporting Wildcard Expansion</span></span>

<span data-ttu-id="abdb0-147">Birden çok nesne seçimi izin vermek için cmdlet'i kullanabilirsiniz [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) ve [System.Management.Automation.Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) sağlayan sınıflar Giriş parametresi joker karakter genişletmesi desteği.</span><span class="sxs-lookup"><span data-stu-id="abdb0-147">To allow the selection of multiple objects, your cmdlet can use the [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) and [System.Management.Automation.Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) classes to provide wildcard expansion support for parameter input.</span></span> <span data-ttu-id="abdb0-148">Joker karakter düzeni örnekleri olan lsa \* \*.txt ve [a-c]\*.</span><span class="sxs-lookup"><span data-stu-id="abdb0-148">Examples of wildcard patterns are lsa\*, \*.txt, and [a-c]\*.</span></span> <span data-ttu-id="abdb0-149">Desen, tam anlamıyla kullanılması gereken bir karakter içerdiğinde bir kaçış karakteri geriye tırnak işareti karakteri (') kullanın.</span><span class="sxs-lookup"><span data-stu-id="abdb0-149">Use the back-quote character (\`) as an escape character when the pattern contains a character that should be used literally.</span></span>

<span data-ttu-id="abdb0-150">Dosya ve yol adları joker genişletmeleri burada cmdlet'ini birden çok nesne seçimi gerekli olduğunda yolu girişleri için destek isteyebilirsiniz yaygın senaryoları bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="abdb0-150">Wildcard expansions of file and path names are examples of common scenarios where the cmdlet may want to allow support for path inputs when the selection of multiple objects is required.</span></span> <span data-ttu-id="abdb0-151">Burada geçerli klasörde bulunan tüm dosyaları görmek için bir kullanıcının istediği dosya sistemindeki genel durumu gösterir.</span><span class="sxs-lookup"><span data-stu-id="abdb0-151">A common case is in the file system, where a user wants to see all files residing in the current folder.</span></span>

<span data-ttu-id="abdb0-152">Nadiren özelleştirilmiş joker karakter deseni eşleştirme uygulaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="abdb0-152">You should need a customized wildcard pattern matching implementation only rarely.</span></span> <span data-ttu-id="abdb0-153">Bu durumda, cmdlet'inize tam POSIX 1003.2, joker karakter genişletmesi 3.13 belirtimi veya aşağıdaki Basitleştirilmiş alt desteklemesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="abdb0-153">In this case, your cmdlet should support either the full POSIX 1003.2, 3.13 specification for wildcard expansion or the following simplified subset:</span></span>

- <span data-ttu-id="abdb0-154">**Soru işareti (?).**</span><span class="sxs-lookup"><span data-stu-id="abdb0-154">**Question mark (?).**</span></span> <span data-ttu-id="abdb0-155">Belirtilen konumda herhangi bir karakterle eşleşir.</span><span class="sxs-lookup"><span data-stu-id="abdb0-155">Matches any character at the specified location.</span></span>

- <span data-ttu-id="abdb0-156">**Yıldız işareti (\*).**</span><span class="sxs-lookup"><span data-stu-id="abdb0-156">**Asterisk (\*).**</span></span> <span data-ttu-id="abdb0-157">Belirtilen konumundan başlayan sıfır veya daha fazla karakter ile eşleşir.</span><span class="sxs-lookup"><span data-stu-id="abdb0-157">Matches zero or more characters starting at the specified location.</span></span>

- <span data-ttu-id="abdb0-158">**Köşeli ayraç ([]) açın.**</span><span class="sxs-lookup"><span data-stu-id="abdb0-158">**Open bracket ([).**</span></span> <span data-ttu-id="abdb0-159">Karakter ya da karakter aralığını içerebilir bir desen köşeli ayraç ifadesi tanıtır.</span><span class="sxs-lookup"><span data-stu-id="abdb0-159">Introduces a pattern bracket expression that can contain characters or a range of characters.</span></span> <span data-ttu-id="abdb0-160">Bir aralık gerekiyorsa, tire (-) aralığını belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="abdb0-160">If a range is required, a hyphen (-) is used to indicate the range.</span></span>

- <span data-ttu-id="abdb0-161">**Kapatma köşeli ayraç (]).**</span><span class="sxs-lookup"><span data-stu-id="abdb0-161">**Close bracket (]).**</span></span> <span data-ttu-id="abdb0-162">Bir desen köşeli ayraç ifadesi sona erer.</span><span class="sxs-lookup"><span data-stu-id="abdb0-162">Ends a pattern bracket expression.</span></span>

- <span data-ttu-id="abdb0-163">**Arka-teklif kaçış karakteri (').**</span><span class="sxs-lookup"><span data-stu-id="abdb0-163">**Back-quote escape character (\`).**</span></span> <span data-ttu-id="abdb0-164">Sonraki karakteri tam anlamıyla alınması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="abdb0-164">Indicates that the next character should be taken literally.</span></span> <span data-ttu-id="abdb0-165">(Programlı olarak belirtme) yerine komut satırından geri tırnak karakteri belirtirken, geri teklif kaçış karakteri'nin iki kez belirtilmiş gerekir dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="abdb0-165">Be aware that when specifying the back-quote character from the command line (as opposed to specifying it programmatically), the back-quote escape character must be specified twice.</span></span>

> [!NOTE]
> <span data-ttu-id="abdb0-166">Joker karakter düzenleri hakkında daha fazla bilgi için bkz: [joker karakterleri destekleme Cmdlet parametreleri](./supporting-wildcard-characters-in-cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="abdb0-166">For more information about wildcard patterns, see [Supporting Wildcards in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md).</span></span>

<span data-ttu-id="abdb0-167">Aşağıdaki kod, joker karakter seçeneklerini ayarlayın ve çözümlemek için kullanılan joker karakter deseni tanımlamak gösterilmektedir `Name` Bu cmdlet için parametre.</span><span class="sxs-lookup"><span data-stu-id="abdb0-167">The following code shows how to set wildcard options and define the wildcard pattern used for resolving the `Name` parameter for this cmdlet.</span></span>

```csharp
WildcardOptions options = WildcardOptions.IgnoreCase |
                          WildcardOptions.Compiled;
WildcardPattern wildcard = new WildcardPattern(name,options);
```

<span data-ttu-id="abdb0-168">Aşağıdaki kod, test etme, işlem adı tanımlanmış bir joker karakter deseni ile eşleşip eşleşmediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="abdb0-168">The following code shows how to test whether the process name matches the defined wildcard pattern.</span></span> <span data-ttu-id="abdb0-169">İşlem adı desenle eşleşmez, bu durumda, cmdlet üzerinde sonraki işlem adı alma devam ettiğinden, dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="abdb0-169">Notice that, in this case, if the process name does not match the pattern, the cmdlet continues on to get the next process name.</span></span>

```csharp
if (!wildcard.IsMatch(processName))
{
  continue;
}
```

## <a name="code-sample"></a><span data-ttu-id="abdb0-170">Kod örneği</span><span class="sxs-lookup"><span data-stu-id="abdb0-170">Code Sample</span></span>

<span data-ttu-id="abdb0-171">Tamamlanmış C# örnek kod için bkz: [StopProcessSample03 örnek](./stopprocesssample03-sample.md).</span><span class="sxs-lookup"><span data-stu-id="abdb0-171">For the complete C# sample code, see [StopProcessSample03 Sample](./stopprocesssample03-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="abdb0-172">Nesne türleri ve biçimlendirme tanımlayın</span><span class="sxs-lookup"><span data-stu-id="abdb0-172">Define Object Types and Formatting</span></span>

<span data-ttu-id="abdb0-173">Windows PowerShell cmdlet arasında .net nesneleri kullanarak bilgileri geçirir.</span><span class="sxs-lookup"><span data-stu-id="abdb0-173">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="abdb0-174">Sonuç olarak, bir cmdlet kendi türü tanımlamanız gerekebilir veya başka bir cmdlet tarafından sağlanan mevcut türü genişletmek cmdlet gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="abdb0-174">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="abdb0-175">Yeni türleri tanımlama veya varolan türleri genişletme hakkında daha fazla bilgi için bkz. [genişletme nesne türleri ve biçimlendirme](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="abdb0-175">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="abdb0-176">Cmdlet oluşturma</span><span class="sxs-lookup"><span data-stu-id="abdb0-176">Building the Cmdlet</span></span>

<span data-ttu-id="abdb0-177">Bir cmdlet uyguladıktan sonra bunu Windows PowerShell ile bir Windows PowerShell ek bileşeni kayıtlı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="abdb0-177">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="abdb0-178">Cmdlet'leri kaydetme hakkında daha fazla bilgi için bkz. [kaydetme cmdlet'leri ve sağlayıcıları uygulamalarını barındırmak için nasıl](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="abdb0-178">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="abdb0-179">Sınama cmdlet'i</span><span class="sxs-lookup"><span data-stu-id="abdb0-179">Testing the Cmdlet</span></span>

<span data-ttu-id="abdb0-180">Windows PowerShell ile cmdlet'ini kaydedildi, komut satırında çalıştırarak test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="abdb0-180">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="abdb0-181">Şimdi örnek Stop-Proc cmdlet test edin.</span><span class="sxs-lookup"><span data-stu-id="abdb0-181">Let's test the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="abdb0-182">Komut satırından cmdlet'leri kullanma hakkında daha fazla bilgi için bkz. [Windows PowerShell ile çalışmaya başlama](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="abdb0-182">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="abdb0-183">Windows PowerShell'i başlatın ve ProcessName diğer kullanarak işlemi durdurmak için Stop-Proc `Name` parametresi.</span><span class="sxs-lookup"><span data-stu-id="abdb0-183">Start Windows PowerShell and use Stop-Proc to stop a process using the ProcessName alias for the `Name` parameter.</span></span>

    ```powershell
    PS> stop-proc -ProcessName notepad
    ```

<span data-ttu-id="abdb0-184">Aşağıdaki çıktı görünür.</span><span class="sxs-lookup"><span data-stu-id="abdb0-184">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (3496)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="abdb0-185">Komut satırında aşağıdaki giriş yapın.</span><span class="sxs-lookup"><span data-stu-id="abdb0-185">Make the following entry on the command line.</span></span> <span data-ttu-id="abdb0-186">Name parametresi zorunlu olduğundan istenir.</span><span class="sxs-lookup"><span data-stu-id="abdb0-186">Because the Name parameter is mandatory, you are prompted for it.</span></span> <span data-ttu-id="abdb0-187">Girme "!?"</span><span class="sxs-lookup"><span data-stu-id="abdb0-187">Entering "!?"</span></span> <span data-ttu-id="abdb0-188">parametresiyle ilgili Yardım metnini getirir.</span><span class="sxs-lookup"><span data-stu-id="abdb0-188">brings up the help text associated with the parameter.</span></span>

    ```powershell
    PS> stop-proc
    ```

<span data-ttu-id="abdb0-189">Aşağıdaki çıktı görünür.</span><span class="sxs-lookup"><span data-stu-id="abdb0-189">The following output appears.</span></span>

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    (Type !? for Help.)
    Name[0]: !?
    The name of one or more processes to stop. Wildcards are permitted.
    Name[0]: notepad
    ```

- <span data-ttu-id="abdb0-190">Artık joker karakter deseni ile eşleşen tüm işlemler durdurmak için şu girdiyi olun "\* Not\*".</span><span class="sxs-lookup"><span data-stu-id="abdb0-190">Now make the following entry to stop all processes that match the wildcard pattern "\*note\*".</span></span> <span data-ttu-id="abdb0-191">Desenle eşleşen her işlemi durdurmadan önce istenir.</span><span class="sxs-lookup"><span data-stu-id="abdb0-191">You are prompted before stopping each process that matches the pattern.</span></span>

    ```powershell
    PS> stop-proc -Name *note*
    ```

<span data-ttu-id="abdb0-192">Aşağıdaki çıktı görünür.</span><span class="sxs-lookup"><span data-stu-id="abdb0-192">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (1112)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

<span data-ttu-id="abdb0-193">Aşağıdaki çıktı görünür.</span><span class="sxs-lookup"><span data-stu-id="abdb0-193">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTEM (3712)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

<span data-ttu-id="abdb0-194">Aşağıdaki çıktı görünür.</span><span class="sxs-lookup"><span data-stu-id="abdb0-194">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTE (3592)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="abdb0-195">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="abdb0-195">See Also</span></span>

[<span data-ttu-id="abdb0-196">Sistem değiştiren bir Cmdlet oluşturma</span><span class="sxs-lookup"><span data-stu-id="abdb0-196">Create a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="abdb0-197">Bir Windows PowerShell cmdlet'i oluşturma</span><span class="sxs-lookup"><span data-stu-id="abdb0-197">How to Create a Windows PowerShell Cmdlet</span></span>](https://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[<span data-ttu-id="abdb0-198">Nesne türlerini genişletme ve biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="abdb0-198">Extending Object Types and Formatting</span></span>](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="abdb0-199">Cmdlet, sağlayıcılar kaydetmek ve uygulamaları barındırmak nasıl</span><span class="sxs-lookup"><span data-stu-id="abdb0-199">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="abdb0-200">Cmdlet parametreleri joker karakterleri destekleme</span><span class="sxs-lookup"><span data-stu-id="abdb0-200">Supporting Wildcards in Cmdlet Parameters</span></span>](./supporting-wildcard-characters-in-cmdlet-parameters.md)

[<span data-ttu-id="abdb0-201">Windows PowerShell SDK'sı</span><span class="sxs-lookup"><span data-stu-id="abdb0-201">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
