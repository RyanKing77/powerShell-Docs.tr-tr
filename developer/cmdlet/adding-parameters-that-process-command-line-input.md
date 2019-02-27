---
title: Komut satırı giriş parametreleri ekleme | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmer's Guide], parameters
- Get-Proc cmdlet [PowerShell Programmer's Guide]
- cmdlets [PowerShell Programmer's Guide], command line input
- command line input [PowerShell Programmer's Guide]
- parameters [PowerShell Programmer's Guide]
- cmdlets [PowerShell Programmer's Guide], creating
ms.assetid: da0b32f8-7b51-440e-a061-3177b5759e0e
caps.latest.revision: 9
ms.openlocfilehash: e010e28ec705932063bb418b260a1087fc3eef9e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846819"
---
# <a name="adding-parameters-that-process-command-line-input"></a><span data-ttu-id="31d34-102">Komut Satırı Girişini İşleyen Parametreler Ekleme</span><span class="sxs-lookup"><span data-stu-id="31d34-102">Adding Parameters That Process Command-Line Input</span></span>

<span data-ttu-id="31d34-103">Bir giriş bir cmdlet için komut satırı kaynağıdır.</span><span class="sxs-lookup"><span data-stu-id="31d34-103">One source of input for a cmdlet is the command line.</span></span> <span data-ttu-id="31d34-104">Bu konuda, bir parametre eklemeyi açıklar **Get-Proc** cmdlet (açıklanan [oluşturma bilgisayarınızı ilk Cmdlet](./creating-a-cmdlet-without-parameters.md)) cmdlet'ini ve yerel bilgisayardan üzerinde açık göre giriş işleyebilmesi nesneleri cmdlet'e geçirilen.</span><span class="sxs-lookup"><span data-stu-id="31d34-104">This topic describes how to add a parameter to the **Get-Proc** cmdlet (which is described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)) so that the cmdlet can process input from the local computer based on explicit objects passed to the cmdlet.</span></span> <span data-ttu-id="31d34-105">**Get-Proc** açıklanan cmdlet'i burada adlarına göre işlemler alır ve ardından bir komut isteminde işlemleri hakkındaki bilgileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="31d34-105">The **Get-Proc** cmdlet described here retrieves processes based on their names, and then displays information about the processes at a command prompt.</span></span>

<span data-ttu-id="31d34-106">Bu konuda aşağıdaki bölümleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="31d34-106">The following sections are in this topic:</span></span>

- [<span data-ttu-id="31d34-107">Cmdlet'i sınıf tanımlama</span><span class="sxs-lookup"><span data-stu-id="31d34-107">Defining the Cmdlet Class</span></span>](#Defining-the-Cmdlet-Class)

- [<span data-ttu-id="31d34-108">Parametreleri bildirme</span><span class="sxs-lookup"><span data-stu-id="31d34-108">Declaring Parameters</span></span>](#Declaring-Parameters)

- [<span data-ttu-id="31d34-109">Parametre doğrulaması destekleme</span><span class="sxs-lookup"><span data-stu-id="31d34-109">Supporting Parameter Validation</span></span>](#Supporting-Parameter-Validation)

- [<span data-ttu-id="31d34-110">Bir giriş işleme yöntemi geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="31d34-110">Overriding an Input Processing Method</span></span>](#Overriding-an-Input-Processing-Method)

- [<span data-ttu-id="31d34-111">Kod örneği</span><span class="sxs-lookup"><span data-stu-id="31d34-111">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="31d34-112">Nesne türlerini tanımlama ve biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="31d34-112">Defining Object Types and Formatting</span></span>](#Defining-Object-Types-and-Formatting)

- [<span data-ttu-id="31d34-113">Cmdlet oluşturma</span><span class="sxs-lookup"><span data-stu-id="31d34-113">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="31d34-114">Sınama cmdlet'i</span><span class="sxs-lookup"><span data-stu-id="31d34-114">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="31d34-115">Cmdlet'i sınıf tanımlama</span><span class="sxs-lookup"><span data-stu-id="31d34-115">Defining the Cmdlet Class</span></span>

<span data-ttu-id="31d34-116">İlk cmdlet oluşturma cmdlet'i adlandırma ve cmdlet uygulayan .NET Framework sınıf bildirimi adımdır.</span><span class="sxs-lookup"><span data-stu-id="31d34-116">The first step in cmdlet creation is cmdlet naming and the declaration of the .NET Framework class that implements the cmdlet.</span></span> <span data-ttu-id="31d34-117">Burada seçilen fiil adı "Get", bu nedenle bu cmdlet, işlem bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="31d34-117">This cmdlet retrieves process information, so the verb name chosen here is "Get."</span></span> <span data-ttu-id="31d34-118">(Komut satırı girişi neredeyse her türlü bilgi alma özelliğine sahip olan cmdlet işleyebilir.) Onaylanan cmdlet fiilleri hakkında daha fazla bilgi için bkz: [Cmdlet fiili adları](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="31d34-118">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="31d34-119">Sınıf bildirimi işte **Get-Proc** cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="31d34-119">Here's the class declaration for the **Get-Proc** cmdlet.</span></span> <span data-ttu-id="31d34-120">Bu tanımı hakkında ayrıntılar verilmiştir [oluşturma bilgisayarınızı ilk Cmdlet](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="31d34-120">Details about this definition are provided in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="declaring-parameters"></a><span data-ttu-id="31d34-121">Parametreleri bildirme</span><span class="sxs-lookup"><span data-stu-id="31d34-121">Declaring Parameters</span></span>

<span data-ttu-id="31d34-122">Bir cmdlet parametresi cmdlet giriş sağlamak kullanıcının sağlar.</span><span class="sxs-lookup"><span data-stu-id="31d34-122">A cmdlet parameter enables the user to provide input to the cmdlet.</span></span> <span data-ttu-id="31d34-123">Aşağıdaki örnekte, **Get-Proc** ve `Get-Member` ardışık cmdlet'leri adlarının ve `MemberType` parametresi için `Get-Member` cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="31d34-123">In the following example, **Get-Proc** and `Get-Member` are the names of pipelined cmdlets, and `MemberType` is a parameter for the `Get-Member` cmdlet.</span></span> <span data-ttu-id="31d34-124">Parametresinin "özelliği" bağımsız değişken</span><span class="sxs-lookup"><span data-stu-id="31d34-124">The parameter has the argument "property."</span></span>

<span data-ttu-id="31d34-125">**PS > get-proc; `get-member` - membertype özelliği**</span><span class="sxs-lookup"><span data-stu-id="31d34-125">**PS> get-proc ; `get-member` -membertype property**</span></span>

<span data-ttu-id="31d34-126">Bir cmdlet için parametreleri bildirmek için önce parametreleri temsil eden özelliklerinin tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="31d34-126">To declare parameters for a cmdlet, you must first define the properties that represent the parameters.</span></span> <span data-ttu-id="31d34-127">İçinde **Get-Proc** cmdlet'i, yalnızca bir parametredir `Name`, bu durumda temsil eden almak için .NET Framework işlem nesnesinin adı.</span><span class="sxs-lookup"><span data-stu-id="31d34-127">In the **Get-Proc** cmdlet, the only parameter is `Name`, which in this case represents the name of the .NET Framework process object to retrieve.</span></span> <span data-ttu-id="31d34-128">Bu nedenle, cmdlet'i sınıfı bir dizi adını kabul etmek için dize türünde bir özelliğini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="31d34-128">Therefore, the cmdlet class defines a property of type string to accept an array of names.</span></span>

<span data-ttu-id="31d34-129">Parametre bildirimi için işte `Name` parametresinin **Get-Proc** cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="31d34-129">Here's the parameter declaration for the `Name` parameter of the **Get-Proc** cmdlet.</span></span>

```csharp
/// <summary>
/// Specify the cmdlet Name parameter.
/// </summary>
  [Parameter(Position = 0)]
  [ValidateNotNullOrEmpty]
  public string[] Name
  {
    get { return processNames; }
    set { processNames = value; }
  }
  private string[] processNames;

  #endregion Parameters
```

```vb
<Parameter(Position:=0), ValidateNotNullOrEmpty()> _
Public Property Name() As String()
    Get
        Return processNames
    End Get

    Set(ByVal value As String())
        processNames = value
    End Set

End Property
```

<span data-ttu-id="31d34-130">Bu özellik, Windows PowerShell çalışma zamanı bildirmek için `Name` parametresi bir [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) özniteliği, property tanımına eklenir.</span><span class="sxs-lookup"><span data-stu-id="31d34-130">To inform the Windows PowerShell runtime that this property is the `Name` parameter, a [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute is added to the property definition.</span></span> <span data-ttu-id="31d34-131">Bu öznitelik bildirmek için temel söz dizimi `[Parameter()]`.</span><span class="sxs-lookup"><span data-stu-id="31d34-131">The basic syntax for declaring this attribute is `[Parameter()]`.</span></span>

> [!NOTE]
> <span data-ttu-id="31d34-132">Bir parametre açıkça genel olarak işaretlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="31d34-132">A parameter must be explicitly marked as public.</span></span> <span data-ttu-id="31d34-133">İç ortak varsayılan olarak işaretlenmez ve Windows PowerShell çalışma zamanı tarafından bulunamadı parametreler.</span><span class="sxs-lookup"><span data-stu-id="31d34-133">Parameters that are not marked as public default to internal and are not found by the Windows PowerShell runtime.</span></span>

<span data-ttu-id="31d34-134">Bu cmdlet için bir dize dizisi kullanan `Name` parametresi.</span><span class="sxs-lookup"><span data-stu-id="31d34-134">This cmdlet uses an array of strings for the `Name` parameter.</span></span> <span data-ttu-id="31d34-135">Bu cmdlet birden fazla öğe kabul etmek izin verdiğinden Mümkünse, cmdlet'inize ayrıca bir parametre bir dizi olarak tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="31d34-135">If possible, your cmdlet should also define a parameter as an array, because this allows the cmdlet to accept more than one item.</span></span>

#### <a name="things-to-remember-about-parameter-definitions"></a><span data-ttu-id="31d34-136">Parametre tanımları hakkında bunları unutmayın</span><span class="sxs-lookup"><span data-stu-id="31d34-136">Things to Remember About Parameter Definitions</span></span>

- <span data-ttu-id="31d34-137">Önceden tanımlanmış Windows PowerShell parametre adları ve veri türleri cmdlet'inize Windows PowerShell cmdlet'leri ile uyumlu olduğundan emin olmak mümkün olduğunca yeniden.</span><span class="sxs-lookup"><span data-stu-id="31d34-137">Predefined Windows PowerShell parameter names and data types should be reused as much as possible to ensure that your cmdlet is compatible with Windows PowerShell cmdlets.</span></span> <span data-ttu-id="31d34-138">Örneğin, önceden tanımlanmış tüm cmdlet'leri kullanıyorsanız `Id` kullanıcı olacak bir kaynak bir kolayca belirlemek için parametre adı parametrenin kullanıyordur hangi cmdlet bağımsız olarak anlamı anlama.</span><span class="sxs-lookup"><span data-stu-id="31d34-138">For example, if all cmdlets use the predefined `Id` parameter name to identify a resource, user will easily understand the meaning of the parameter, regardless of what cmdlet they are using.</span></span> <span data-ttu-id="31d34-139">Temelde, parametre adları, ortak dil çalışma zamanı (CLR) değişken adları için kullanılanlarla aynı kurallara izleyin.</span><span class="sxs-lookup"><span data-stu-id="31d34-139">Basically, parameter names follow the same rules as those used for variable names in the common language runtime (CLR).</span></span> <span data-ttu-id="31d34-140">Parametre adlandırma hakkında daha fazla bilgi için bkz. [Cmdlet parametresi adları](https://msdn.microsoft.com/en-us/c4500737-0a05-4d01-911b-394424c65bfb).</span><span class="sxs-lookup"><span data-stu-id="31d34-140">For more information about parameter naming, see [Cmdlet Parameter Names](https://msdn.microsoft.com/en-us/c4500737-0a05-4d01-911b-394424c65bfb).</span></span>

- <span data-ttu-id="31d34-141">Windows PowerShell, tutarlı bir kullanıcı deneyimi sağlamak için birkaç parametre adlarını saklar.</span><span class="sxs-lookup"><span data-stu-id="31d34-141">Windows PowerShell reserves a few parameter names to provide a consistent user experience.</span></span> <span data-ttu-id="31d34-142">Bu parametre adlarını kullanmayın: `WhatIf`, `Confirm`, `Verbose`, `Debug`, `Warn`, `ErrorAction`, `ErrorVariable`, `OutVariable`, ve `OutBuffer`.</span><span class="sxs-lookup"><span data-stu-id="31d34-142">Do not use these parameter names: `WhatIf`, `Confirm`, `Verbose`, `Debug`, `Warn`, `ErrorAction`, `ErrorVariable`, `OutVariable`, and `OutBuffer`.</span></span> <span data-ttu-id="31d34-143">Ayrıca, aşağıdaki diğer adlar için bu parametre adları ayrılmıştır: `vb`, `db`, `ea`, `ev`, `ov`, ve `ob`.</span><span class="sxs-lookup"><span data-stu-id="31d34-143">Additionally, the following aliases for these parameter names are reserved: `vb`, `db`, `ea`, `ev`, `ov`, and `ob`.</span></span>

- <span data-ttu-id="31d34-144">`Name` cmdlet'lerinizi kullanmak için önerilen bir basit ve ortak parametre adıdır.</span><span class="sxs-lookup"><span data-stu-id="31d34-144">`Name` is a simple and common parameter name, recommended for use in your cmdlets.</span></span> <span data-ttu-id="31d34-145">Belirli bir cmdlet için benzersiz ve hatırlamak zor olan bir karmaşık adı yerine böyle bir parametre adı seçmek daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="31d34-145">It is better to choose a parameter name like this than a complex name that is unique to a specific cmdlet and hard to remember.</span></span>

- <span data-ttu-id="31d34-146">Varsayılan olarak, kabuk durumu korur. ancak Windows PowerShell'de, büyük küçük harf duyarsız parametrelerdir.</span><span class="sxs-lookup"><span data-stu-id="31d34-146">Parameters are case-insensitive in Windows PowerShell, although by default the shell preserves case.</span></span> <span data-ttu-id="31d34-147">Büyük küçük harf duyarlılığı bağımsız değişkenlerinin işlemi cmdlet'inin bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="31d34-147">Case-sensitivity of the arguments depends on the operation of the cmdlet.</span></span> <span data-ttu-id="31d34-148">Bağımsız değişkenler olarak komut satırında belirtilen parametresi geçirilir.</span><span class="sxs-lookup"><span data-stu-id="31d34-148">Arguments are passed to a parameter as specified at the command line.</span></span>

- <span data-ttu-id="31d34-149">Diğer parametre bildirimleri örnekleri için bkz: [Cmdlet parametreleri](./cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="31d34-149">For examples of other parameter declarations, see [Cmdlet Parameters](./cmdlet-parameters.md).</span></span>

## <a name="declaring-parameters-as-positional-or-named"></a><span data-ttu-id="31d34-150">Konumsal veya adlandırılmış parametreleri bildirme</span><span class="sxs-lookup"><span data-stu-id="31d34-150">Declaring Parameters as Positional or Named</span></span>

<span data-ttu-id="31d34-151">Bir cmdlet her parametre konumsal veya adlandırılmış bir parametre olarak ayarlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="31d34-151">A cmdlet must set each parameter as either a positional or named parameter.</span></span> <span data-ttu-id="31d34-152">Her iki tür parametreleri tek bağımsız değişken, virgül ve Boole ayarları tarafından ayrılmış birden çok bağımsız değişkeni kabul eder.</span><span class="sxs-lookup"><span data-stu-id="31d34-152">Both kinds of parameters accept single arguments, multiple arguments separated by commas, and Boolean settings.</span></span> <span data-ttu-id="31d34-153">Bir Boole parametresi olarak da adlandırılan bir *geçiş*, yalnızca Boole ayarları işler.</span><span class="sxs-lookup"><span data-stu-id="31d34-153">A Boolean parameter, also called a *switch*, handles only Boolean settings.</span></span> <span data-ttu-id="31d34-154">Anahtar parametresinin varolup olmadığını belirlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="31d34-154">The switch is used to determine the presence of the parameter.</span></span> <span data-ttu-id="31d34-155">Önerilen varsayılan `false`.</span><span class="sxs-lookup"><span data-stu-id="31d34-155">The recommended default is `false`.</span></span>

<span data-ttu-id="31d34-156">Örnek **Get-Proc** cmdlet'i tanımlar `Name` parametre pozisyon 0 ile konumsal bir parametre olarak.</span><span class="sxs-lookup"><span data-stu-id="31d34-156">The sample **Get-Proc** cmdlet defines the `Name` parameter as a positional parameter with position 0.</span></span> <span data-ttu-id="31d34-157">Başka bir deyişle, ilk bağımsız değişkeni komut satırında kullanıcının girdiği Bu parametre için otomatik olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="31d34-157">This means that the first argument the user enters on the command line is automatically inserted for this parameter.</span></span> <span data-ttu-id="31d34-158">Adlandırılmış parametre tanımlamak istiyorsanız, komut satırından, parametre adı kullanıcı belirtmeniz gerekir bırakın `Position` öznitelik bildiriminin dışında anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="31d34-158">If you want to define a named parameter, for which the user must specify the parameter name from the command line, leave the `Position` keyword out of the attribute declaration.</span></span>

> [!NOTE]
> <span data-ttu-id="31d34-159">Parametre olarak adlandırılmalıdır yoksa, kullanıcılar, parametre adı gerekmez. böylece en çok kullanılan parametreleri konumsal yapmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="31d34-159">Unless parameters must be named, we recommend that you make the most-used parameters positional so that users will not have to type the parameter name.</span></span>

## <a name="declaring-parameters-as-mandatory-or-optional"></a><span data-ttu-id="31d34-160">Parametreler, zorunlu veya isteğe bağlı olarak bildirme</span><span class="sxs-lookup"><span data-stu-id="31d34-160">Declaring Parameters as Mandatory or Optional</span></span>

<span data-ttu-id="31d34-161">Bir cmdlet her parametrenin isteğe bağlı veya zorunlu bir parametre olarak ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="31d34-161">A cmdlet must set each parameter as either an optional or a mandatory parameter.</span></span> <span data-ttu-id="31d34-162">Örnekteki **Get-Proc** cmdlet'ini `Name` çünkü parametre olarak isteğe bağlı tanımlanır `Mandatory` anahtar sözcüğü, öznitelik bildiriminde ayarlanmadı.</span><span class="sxs-lookup"><span data-stu-id="31d34-162">In the sample **Get-Proc** cmdlet, the `Name` parameter is defined as optional because the `Mandatory` keyword is not set in the attribute declaration.</span></span>

## <a name="supporting-parameter-validation"></a><span data-ttu-id="31d34-163">Parametre doğrulaması destekleme</span><span class="sxs-lookup"><span data-stu-id="31d34-163">Supporting Parameter Validation</span></span>

<span data-ttu-id="31d34-164">Örnek **Get-Proc** cmdlet'i bir giriş doğrulama özniteliği ekler [System.Management.Automation.Validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute), `Name` parametresi doğrulamasını etkinleştirmek için Giriş ne olduğunu `null` ya da boş.</span><span class="sxs-lookup"><span data-stu-id="31d34-164">The sample **Get-Proc** cmdlet adds an input validation attribute, [System.Management.Automation.Validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute), to the `Name` parameter to enable validation that the input is neither `null` nor empty.</span></span> <span data-ttu-id="31d34-165">Bu öznitelik Windows PowerShell tarafından sağlanan çeşitli doğrulama özniteliklerinin biridir.</span><span class="sxs-lookup"><span data-stu-id="31d34-165">This attribute is one of several validation attributes provided by Windows PowerShell.</span></span> <span data-ttu-id="31d34-166">Diğer doğrulama öznitelikleri örnekleri için bkz. [parametre girişi doğrulama](./validating-parameter-input.md).</span><span class="sxs-lookup"><span data-stu-id="31d34-166">For examples of other validation attributes, see [Validating Parameter Input](./validating-parameter-input.md).</span></span>

```
[Parameter(Position = 0)]
[ValidateNotNullOrEmpty]
public string[] Name
```

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="31d34-167">Bir giriş işleme yöntemi geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="31d34-167">Overriding an Input Processing Method</span></span>

<span data-ttu-id="31d34-168">Komut satırı girdi işlemek üzere cmdlet'inize ise, yöntem işleme uygun giriş geçersiz kılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="31d34-168">If your cmdlet is to handle command-line input, it must override the appropriate input processing methods.</span></span> <span data-ttu-id="31d34-169">Temel giriş işleme yöntemleri de sunulan [oluşturma bilgisayarınızı ilk Cmdlet](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="31d34-169">The basic input processing methods are introduced in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

<span data-ttu-id="31d34-170">**Get-Proc** cmdlet'i geçersiz kılmalar [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) işlemek için yöntemi `Name` kullanıcı veya bir betik tarafından sağlanan parametre girişi.</span><span class="sxs-lookup"><span data-stu-id="31d34-170">The **Get-Proc** cmdlet overrides the [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to handle the `Name` parameter input provided by the user or a script.</span></span> <span data-ttu-id="31d34-171">Adsız sağlanırsa, bu yöntem işlemleri her istenen işlem adı ya da tüm işlemler için alır.</span><span class="sxs-lookup"><span data-stu-id="31d34-171">This method gets the processes for each requested process name, or all for processes if no name is provided.</span></span> <span data-ttu-id="31d34-172">Dikkat [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), çağrı [System.Management.Automation.Cmdlet.Writeobject%28System.Object%2Csystem.Boolean%29](/dotnet/api/system.management.automation.cmdlet.writeobject?view=powershellsdk-1.1.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) çıktı mekanizması, çıkış göndermek için işlem hattına nesneleri.</span><span class="sxs-lookup"><span data-stu-id="31d34-172">Notice that in [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), the call to [System.Management.Automation.Cmdlet.Writeobject%28System.Object%2Csystem.Boolean%29](/dotnet/api/system.management.automation.cmdlet.writeobject?view=powershellsdk-1.1.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) is the output mechanism for sending output objects to the pipeline.</span></span> <span data-ttu-id="31d34-173">Bu çağrı, ikinci parametresinin `enumerateCollection`, ayarlanır `true` çıkış dizisi süreç nesneleri numaralandırır ve bir işlem aynı anda komut satırına yazmak için Windows PowerShell çalışma zamanı bildirmek için.</span><span class="sxs-lookup"><span data-stu-id="31d34-173">The second parameter of this call, `enumerateCollection`, is set to `true` to inform the Windows PowerShell runtime to enumerate the output array of process objects and write one process at a time to the command line.</span></span>

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
    }
  }
}
```

```vb
Protected Overrides Sub ProcessRecord()

    '/ If no process names are passed to the cmdlet, get all processes.
    If processNames Is Nothing Then
        Dim processes As Process()
        processes = Process.GetProcesses()
    End If

    '/ If process names are specified, write the processes to the
    '/ pipeline to display them or make them available to the next cmdlet.

    For Each name As String In processNames
        '/ The second parameter of this call tells PowerShell to enumerate the
        '/ array, and send one process at a time to the pipeline.
        WriteObject(Process.GetProcessesByName(name), True)
    Next

End Sub 'ProcessRecord
```

## <a name="code-sample"></a><span data-ttu-id="31d34-174">Kod örneği</span><span class="sxs-lookup"><span data-stu-id="31d34-174">Code Sample</span></span>

<span data-ttu-id="31d34-175">Tamamlanmış C# örnek kod için bkz: [GetProcessSample02 örnek](./getprocesssample02-sample.md).</span><span class="sxs-lookup"><span data-stu-id="31d34-175">For the complete C# sample code, see [GetProcessSample02 Sample](./getprocesssample02-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="31d34-176">Nesne türlerini tanımlama ve biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="31d34-176">Defining Object Types and Formatting</span></span>

<span data-ttu-id="31d34-177">Windows PowerShell cmdlet'lerini kullanarak .NET Framework nesneleri arasında bilgi geçirir.</span><span class="sxs-lookup"><span data-stu-id="31d34-177">Windows PowerShell passes information between cmdlets by using .NET Framework objects.</span></span> <span data-ttu-id="31d34-178">Sonuç olarak, bir cmdlet'in kendi türü tanımlamanız gerekebilir veya bir cmdlet başka bir cmdlet tarafından sağlanan mevcut türü genişletmek gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="31d34-178">Consequently, a cmdlet might need to define its own type, or a cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="31d34-179">Yeni türleri tanımlama veya varolan türleri genişletme hakkında daha fazla bilgi için bkz. [genişletme nesne türleri ve biçimlendirme](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="31d34-179">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="31d34-180">Cmdlet oluşturma</span><span class="sxs-lookup"><span data-stu-id="31d34-180">Building the Cmdlet</span></span>

<span data-ttu-id="31d34-181">Bir cmdlet uyguladıktan sonra bir Windows PowerShell ek bileşenini kullanarak Windows PowerShell ile kaydetmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="31d34-181">After you implement a cmdlet, you must register it with Windows PowerShell by using a Windows PowerShell snap-in.</span></span> <span data-ttu-id="31d34-182">Cmdlet'leri kaydetme hakkında daha fazla bilgi için bkz. [kaydetme cmdlet'leri ve sağlayıcıları uygulamalarını barındırmak için nasıl](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="31d34-182">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="31d34-183">Sınama cmdlet'i</span><span class="sxs-lookup"><span data-stu-id="31d34-183">Testing the Cmdlet</span></span>

<span data-ttu-id="31d34-184">Windows PowerShell ile cmdlet'ini kaydettiğinizde, komut satırında çalıştırarak test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="31d34-184">When your cmdlet is registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="31d34-185">Örnek cmdlet kodunu test etmek için iki yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="31d34-185">Here are two ways to test the code for the sample cmdlet.</span></span> <span data-ttu-id="31d34-186">Komut satırından cmdlet'leri kullanma hakkında daha fazla bilgi için bkz. [Windows PowerShell ile çalışmaya başlama](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="31d34-186">For more information about using cmdlets from the command line, see [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="31d34-187">Windows PowerShell komut isteminde, Internet Explorer işlemi, "IEXPLORE." adlı listelemek için aşağıdaki komutu kullanın.</span><span class="sxs-lookup"><span data-stu-id="31d34-187">At the Windows PowerShell prompt, use the following command to list the Internet Explorer process, which is named "IEXPLORE."</span></span>

    ```powershell
    PS> get-proc -name iexplore
    ```

<span data-ttu-id="31d34-188">Aşağıdaki çıktı görünür.</span><span class="sxs-lookup"><span data-stu-id="31d34-188">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----   ------ --   -----------
        354      11  10036   18992    85   0.67   3284   iexplore
    ```

- <span data-ttu-id="31d34-189">"IEXPLORE" adlı Internet Explorer, Outlook ve not defteri işlemleri listelemek için "OUTLOOK" ve "Not", aşağıdaki komutu kullanın.</span><span class="sxs-lookup"><span data-stu-id="31d34-189">To list the Internet Explorer, Outlook, and Notepad processes named "IEXPLORE," "OUTLOOK," and "NOTEPAD," use the following command.</span></span> <span data-ttu-id="31d34-190">Birden çok işlem varsa, bunların tümünün görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="31d34-190">If there are multiple processes, all of them are displayed.</span></span>

    ```powershell
    PS> get-proc -name iexplore, outlook, notepad
    ```

<span data-ttu-id="31d34-191">Aşağıdaki çıktı görünür.</span><span class="sxs-lookup"><span data-stu-id="31d34-191">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----  ------   --    -----------
        732      21  24696    5000    138   2.25  2288   iexplore
        715      19  20556   14116    136   1.78  3860   iexplore
       3917      62  74096   58112    468 191.56  1848   OUTLOOK
         39       2   1024    3280     30   0.09  1444   notepad
         39       2   1024     356     30   0.08  3396   notepad
    ```

## <a name="see-also"></a><span data-ttu-id="31d34-192">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="31d34-192">See Also</span></span>

[<span data-ttu-id="31d34-193">İşlem ardışık düzen giriş parametreleri ekleme</span><span class="sxs-lookup"><span data-stu-id="31d34-193">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="31d34-194">İlk Cmdlet'inize oluşturma</span><span class="sxs-lookup"><span data-stu-id="31d34-194">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="31d34-195">Nesne türlerini genişletme ve biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="31d34-195">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="31d34-196">Cmdlet, sağlayıcılar kaydetmek ve uygulamaları barındırmak nasıl</span><span class="sxs-lookup"><span data-stu-id="31d34-196">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="31d34-197">Windows PowerShell başvurusu</span><span class="sxs-lookup"><span data-stu-id="31d34-197">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="31d34-198">Cmdlet örnekleri</span><span class="sxs-lookup"><span data-stu-id="31d34-198">Cmdlet Samples</span></span>](./cmdlet-samples.md)
