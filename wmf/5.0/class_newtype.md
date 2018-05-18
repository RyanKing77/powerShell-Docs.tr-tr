---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 9aa7e92632c671751020687ddbfc374eeda7148b
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
---
# <a name="new-language-features-in-powershell-50"></a><span data-ttu-id="b0947-102">PowerShell 5.0 içindeki yeni dil özellikleri</span><span class="sxs-lookup"><span data-stu-id="b0947-102">New language features in PowerShell 5.0</span></span>

<span data-ttu-id="b0947-103">PowerShell 5.0, Windows PowerShell içinde aşağıdaki yeni dil öğeleri sunar:</span><span class="sxs-lookup"><span data-stu-id="b0947-103">PowerShell 5.0 introduces the following new language elements in Windows PowerShell:</span></span>

## <a name="class-keyword"></a><span data-ttu-id="b0947-104">Class anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="b0947-104">Class keyword</span></span>

<span data-ttu-id="b0947-105">**Sınıfı** anahtar sözcüğü yeni bir sınıf tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b0947-105">The **class** keyword defines a new class.</span></span> <span data-ttu-id="b0947-106">True .NET Framework türü budur.</span><span class="sxs-lookup"><span data-stu-id="b0947-106">This is a true .NET Framework type.</span></span>
<span data-ttu-id="b0947-107">Sınıf üyeleri ortak, ancak yalnızca genel modülü kapsam içinde.</span><span class="sxs-lookup"><span data-stu-id="b0947-107">Class members are public, but only public within the module scope.</span></span>
<span data-ttu-id="b0947-108">Tür adı bir dize olarak başvuramaz (örneğin, `New-Object` çalışmıyor), ve bu sürümde, bir tür değişmez değeri kullanamazsınız (örneğin, `[MyClass]`) sınıf tanımlanır komut dosyası/modül dosyası dışında.</span><span class="sxs-lookup"><span data-stu-id="b0947-108">You can't refer to the type name as a string (for example, `New-Object` doesn't work), and in this release, you can't use a type literal (for example, `[MyClass]`) outside the script/module file in which the class is defined.</span></span>

```powershell
class MyClass
{
    ...
}
```

## <a name="enum-keyword-and-enumerations"></a><span data-ttu-id="b0947-109">Enum anahtar sözcüğü ve numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="b0947-109">Enum keyword and enumerations</span></span>

<span data-ttu-id="b0947-110">Desteği **enum** anahtar sözcüğü eklendi, yeni satır ayırıcı olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="b0947-110">Support for the **enum** keyword has been added, which uses newline as the delimiter.</span></span>
<span data-ttu-id="b0947-111">Geçerli sınırlamalar: kendisi açısından bir numaralandırıcı tanımlayamazsınız, ancak aşağıdaki örnekte gösterildiği gibi bir numaralandırma başka bir enum bakımından başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b0947-111">Current limitations: you cannot define an enumerator in terms of itself, but you can initialize an enum in terms of another enum, as shown in the following example.</span></span>
<span data-ttu-id="b0947-112">Ayrıca, şu anda temel türü belirtilemez; her zaman [int].</span><span class="sxs-lookup"><span data-stu-id="b0947-112">Also, the base type cannot currently be specified; it is always [int].</span></span>

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

<span data-ttu-id="b0947-113">Bir numaralandırıcı ayrıştırma zamanı sabiti olmalıdır; çağrılan komut sonucuna ayarlanamıyor.</span><span class="sxs-lookup"><span data-stu-id="b0947-113">An enumerator value must be a parse time constant; you cannot set it to the result of an invoked command.</span></span>

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

<span data-ttu-id="b0947-114">Aşağıdaki örnekte gösterildiği gibi numaralandırmalar aritmetik işlemler destekler.</span><span class="sxs-lookup"><span data-stu-id="b0947-114">Enums support arithmetic operations, as shown in the following example.</span></span>

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

## <a name="import-dscresource"></a><span data-ttu-id="b0947-115">İçeri aktarma DscResource</span><span class="sxs-lookup"><span data-stu-id="b0947-115">Import-DscResource</span></span>

<span data-ttu-id="b0947-116">**İçeri aktarma DscResource** true dinamik anahtar sözcüğü sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="b0947-116">**Import-DscResource** is now a true dynamic keyword.</span></span>
<span data-ttu-id="b0947-117">PowerShell içeren sınıfları aranıyor belirtilen modülünün kök modül ayrıştırır **DscResource** özniteliği.</span><span class="sxs-lookup"><span data-stu-id="b0947-117">PowerShell parses the specified module’s root module, searching for classes that contain the **DscResource** attribute.</span></span>

## <a name="implementingassembly"></a><span data-ttu-id="b0947-118">ImplementingAssembly</span><span class="sxs-lookup"><span data-stu-id="b0947-118">ImplementingAssembly</span></span>

<span data-ttu-id="b0947-119">Yeni bir alan **ImplementingAssembly**, ModuleInfo için eklendi.</span><span class="sxs-lookup"><span data-stu-id="b0947-119">A new field, **ImplementingAssembly**, has been added to ModuleInfo.</span></span> <span data-ttu-id="b0947-120">Komut dosyası sınıfları tanımlıyorsa bir betik modülü için oluşturulan dinamik derleme ya da ikili modülleri için yüklenen derleme ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="b0947-120">It is set to the dynamic assembly created for a script module if the script defines classes, or the loaded assembly for binary modules.</span></span> <span data-ttu-id="b0947-121">Ne zaman ayarlanmadı ModuleType bildirimi =.</span><span class="sxs-lookup"><span data-stu-id="b0947-121">It is not set when ModuleType = Manifest.</span></span>

<span data-ttu-id="b0947-122">Yansıma **ImplementingAssembly** alan bir modüldeki kaynakları bulur.</span><span class="sxs-lookup"><span data-stu-id="b0947-122">Reflection on the **ImplementingAssembly** field discovers resources in a module.</span></span> <span data-ttu-id="b0947-123">Başka bir deyişle, PowerShell veya diğer yönetilen dilleri ile yazılmış kaynakları bulabilir.</span><span class="sxs-lookup"><span data-stu-id="b0947-123">This means you can discover resources written in either PowerShell or other managed languages.</span></span>

<span data-ttu-id="b0947-124">Başlatıcılar alanlarla:</span><span class="sxs-lookup"><span data-stu-id="b0947-124">Fields with initializers:</span></span>

```powershell
[int] $i = 5
```

<span data-ttu-id="b0947-125">Statik desteklenir; herhangi bir sırada belirtilen tür kısıtlamaları bunun gibi bir öznitelik gibi çalışır.</span><span class="sxs-lookup"><span data-stu-id="b0947-125">Static is supported; it works like an attribute, as do the type constraints, so it can be specified in any order.</span></span>

```powershell
static [int] $count = 0
```

<span data-ttu-id="b0947-126">Bir isteğe bağlı türüdür.</span><span class="sxs-lookup"><span data-stu-id="b0947-126">A type is optional.</span></span>

```powershell
$s = "hello"
```

<span data-ttu-id="b0947-127">Tüm ortak üyeleridir.</span><span class="sxs-lookup"><span data-stu-id="b0947-127">All members are public.</span></span>

## <a name="constructors-and-instantiation"></a><span data-ttu-id="b0947-128">Oluşturucular ve örnek oluşturma</span><span class="sxs-lookup"><span data-stu-id="b0947-128">Constructors and instantiation</span></span>

<span data-ttu-id="b0947-129">Windows PowerShell sınıfları oluşturucular olabilir; Bunlar kendi sınıf ile aynı ada sahip.</span><span class="sxs-lookup"><span data-stu-id="b0947-129">Windows PowerShell classes can have constructors; they have the same name as their class.</span></span> <span data-ttu-id="b0947-130">Oluşturucular aşırı yüklenmiş.</span><span class="sxs-lookup"><span data-stu-id="b0947-130">Constructors can be overloaded.</span></span> <span data-ttu-id="b0947-131">Statik oluşturucular desteklenir.</span><span class="sxs-lookup"><span data-stu-id="b0947-131">Static constructors are supported.</span></span> <span data-ttu-id="b0947-132">Başlatma ifadeleri özelliklerle herhangi bir kod oluşturucu içinde çalıştırılmadan önce başlatılır.</span><span class="sxs-lookup"><span data-stu-id="b0947-132">Properties with initialization expressions are initialized before running any code in a constructor.</span></span> <span data-ttu-id="b0947-133">Statik özellikler statik oluşturucu gövdesi önce başlatılır ve örnek özelliklerini statik olmayan Oluşturucusu gövde önce başlatılır.</span><span class="sxs-lookup"><span data-stu-id="b0947-133">Static properties are initialized before the body of a static constructor, and instance properties are initialized before the body of the non-static constructor.</span></span> <span data-ttu-id="b0947-134">Şu anda başka bir oluşturucudan bir oluşturucu çağırmak için hiçbir sözdizimi yoktur (ister C\# sözdizimi ": this()").</span><span class="sxs-lookup"><span data-stu-id="b0947-134">Currently, there is no syntax for calling a constructor from another constructor (like the C\# syntax ": this()").</span></span> <span data-ttu-id="b0947-135">Bir ortak Init yöntemi tanımlamak için geçici bir çözüm değildir.</span><span class="sxs-lookup"><span data-stu-id="b0947-135">The workaround is to define a common Init method.</span></span>

<span data-ttu-id="b0947-136">Bu sürümde başlatmasını sınıfların yollar şunlardır.</span><span class="sxs-lookup"><span data-stu-id="b0947-136">The following are ways of instantiating classes in this release.</span></span>

<span data-ttu-id="b0947-137">Varsayılan Oluşturucu kullanarak örnekleme.</span><span class="sxs-lookup"><span data-stu-id="b0947-137">Instantiating by using the default constructor.</span></span> <span data-ttu-id="b0947-138">Yeni nesne bu sürümde desteklenmiyor unutmayın.</span><span class="sxs-lookup"><span data-stu-id="b0947-138">Note that New-Object is not supported in this release.</span></span>

```powershell
$a = [MyClass]::new()
```

<span data-ttu-id="b0947-139">Bir parametre ile bir oluşturucu çağırma</span><span class="sxs-lookup"><span data-stu-id="b0947-139">Calling a constructor with a parameter</span></span>

```powershell
$b = [MyClass]::new(42)
```

<span data-ttu-id="b0947-140">Birden çok parametre ile bir oluşturucu için bir dizi geçirme</span><span class="sxs-lookup"><span data-stu-id="b0947-140">Passing an array to a constructor with multiple parameters</span></span>
```powershell
$c = [MyClass]::new(@(42,43,44), "Hello")
```

<span data-ttu-id="b0947-141">Bu sürümde, Windows PowerShell içinde tanımlanan sınıflar ile New-Object çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="b0947-141">In this release, New-Object does not work with classes defined in Windows PowerShell.</span></span> <span data-ttu-id="b0947-142">Ayrıca bu sürüm için tür adı yalnızca sözcüksel olarak, modül veya sınıfı tanımlayan betik dışında görünür değil anlamı görünür olur.</span><span class="sxs-lookup"><span data-stu-id="b0947-142">Also for this release, the type name is only visible lexically, meaning it is not visible outside of the module or script that defines the class.</span></span> <span data-ttu-id="b0947-143">İşlevler Windows PowerShell içinde tanımlı bir sınıfın örneklerini döndürebilir ve iyi modül veya komut dosyası dışında çalışma örnekleri.</span><span class="sxs-lookup"><span data-stu-id="b0947-143">Functions can return instances of a class defined in Windows PowerShell, and instances work well outside of the module or script.</span></span>

<span data-ttu-id="b0947-144">`Get-Member -Static` başka bir yöntem gibi aşırı görüntüleyebilmeniz Oluşturucular, listeler.</span><span class="sxs-lookup"><span data-stu-id="b0947-144">`Get-Member -Static` lists constructors, so you can view overloads like any other method.</span></span> <span data-ttu-id="b0947-145">Bu sözdiziminin performansını da New-Object önemli ölçüde daha hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="b0947-145">The performance of this syntax is also considerably faster than New-Object.</span></span>

<span data-ttu-id="b0947-146">Adlı sözde statik yöntemi **yeni** aşağıdaki örnekte gösterildiği gibi .NET türleri ile çalışır.</span><span class="sxs-lookup"><span data-stu-id="b0947-146">The pseudo-static method named **new** works with .NET types, as shown in the following example.</span></span>

```powershell
[hashtable]::new()
```

<span data-ttu-id="b0947-147">Şimdi Oluşturucusu aşırı Get üyeyle ya da bu örnekte gösterildiği gibi görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b0947-147">You can now see constructor overloads with Get-Member, or as shown in this example:</span></span>

```powershell
PS> [hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

## <a name="methods"></a><span data-ttu-id="b0947-148">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b0947-148">Methods</span></span>

<span data-ttu-id="b0947-149">Bir Windows PowerShell sınıf yöntemi yalnızca bir sonlandırma bloğu sahip bir ScriptBlock uygulanır.</span><span class="sxs-lookup"><span data-stu-id="b0947-149">A Windows PowerShell class method is implemented as a ScriptBlock that has only an end block.</span></span> <span data-ttu-id="b0947-150">Tüm yöntemleri ortak.</span><span class="sxs-lookup"><span data-stu-id="b0947-150">All methods are public.</span></span> <span data-ttu-id="b0947-151">Adlı bir yöntem tanımlama örneği aşağıdaki gösterir **DoSomething**.</span><span class="sxs-lookup"><span data-stu-id="b0947-151">The following shows an example of defining a method named **DoSomething**.</span></span>

```powershell
class MyClass
{
    DoSomething($x)
    {
        $this._doSomething($x) # method syntax
    }
    private _doSomething($a) {}
}
```

<span data-ttu-id="b0947-152">Yöntem çağırma:</span><span class="sxs-lookup"><span data-stu-id="b0947-152">Method invocation:</span></span>

```powershell
$b = [MyClass]::new()
$b.DoSomething(42)
```

<span data-ttu-id="b0947-153">Aşırı yüklenmiş yöntemler, varolan bir yöntemi ile aynı adlı ancak belirtilen değerlerine göre--Ayrıştırılan de başka bir deyişle, desteklenir.</span><span class="sxs-lookup"><span data-stu-id="b0947-153">Overloaded methods--that is, those that are named the same as an existing method, but differentiated by their specified values--are also supported.</span></span>

## <a name="properties"></a><span data-ttu-id="b0947-154">Özellikler</span><span class="sxs-lookup"><span data-stu-id="b0947-154">Properties</span></span>

<span data-ttu-id="b0947-155">Tüm ortak özelliklerdir.</span><span class="sxs-lookup"><span data-stu-id="b0947-155">All properties are public.</span></span> <span data-ttu-id="b0947-156">Bir satır başı karakteri veya noktalı virgül özellikleri gerektirir.</span><span class="sxs-lookup"><span data-stu-id="b0947-156">Properties require either a newline or semicolon.</span></span> <span data-ttu-id="b0947-157">Hiçbir nesne türü belirtilirse, özellik türü nesnesidir.</span><span class="sxs-lookup"><span data-stu-id="b0947-157">If no object type is specified, the property type is object.</span></span>

<span data-ttu-id="b0947-158">Doğrulama öznitelikleri veya bağımsız değişken dönüşümü kullanmak özellikleri (örn. `[ValidateSet("aaa")]`) beklendiği gibi çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="b0947-158">Properties that use validation attributes or argument transformation attributes (e.g. `[ValidateSet("aaa")]`) work as expected.</span></span>

## <a name="hidden"></a><span data-ttu-id="b0947-159">Gizli</span><span class="sxs-lookup"><span data-stu-id="b0947-159">Hidden</span></span>

<span data-ttu-id="b0947-160">Yeni bir anahtar sözcük **gizli**, eklendi.</span><span class="sxs-lookup"><span data-stu-id="b0947-160">A new keyword, **Hidden**, has been added.</span></span> <span data-ttu-id="b0947-161">**Gizli** özellikleri ve yöntemleri (oluşturucular dahil) için uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="b0947-161">**Hidden** can be applied to properties and methods (including constructors).</span></span>

<span data-ttu-id="b0947-162">Gizli üyeleri ortaktır, ancak Get-üye çıktısında sürece görünmez Force parametresini eklenir.</span><span class="sxs-lookup"><span data-stu-id="b0947-162">Hidden members are public, but do not appear in the output of Get-Member unless the -Force parameter is added.</span></span>

<span data-ttu-id="b0947-163">Gizli üyeleri ne zaman dahil edilmez tamamlayarak veya IntelliSense tamamlanma gizli üye tanımlama sınıfında oluşmadığı sürece kullanarak sekmesinde.</span><span class="sxs-lookup"><span data-stu-id="b0947-163">Hidden members are not included when tab completing or using Intellisense unless the completion occurs in the class defining the hidden member.</span></span>

<span data-ttu-id="b0947-164">Yeni bir öznitelik **System.Management.Automation.HiddenAttribute** C# kodu Windows PowerShell içinde aynı semantiğini böylece eklendi.</span><span class="sxs-lookup"><span data-stu-id="b0947-164">A new attribute, **System.Management.Automation.HiddenAttribute** has been added so that C# code can have the same semantics within Windows PowerShell.</span></span>

## <a name="return-types"></a><span data-ttu-id="b0947-165">Dönüş türleri</span><span class="sxs-lookup"><span data-stu-id="b0947-165">Return types</span></span>

<span data-ttu-id="b0947-166">Dönüş türü bir sözleşmedir; dönüş değeri, beklenen türe dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="b0947-166">Return type is a contract; the return value is converted to the expected type.</span></span> <span data-ttu-id="b0947-167">Dönüş türü belirtilmişse, dönüş türü void alır.</span><span class="sxs-lookup"><span data-stu-id="b0947-167">If no return type is specified, the return type is void.</span></span> <span data-ttu-id="b0947-168">Hiçbir nesnelerin akış yoktur; nesneleri ardışık düzene kasıtlı olarak veya yanlışlıkla tarafından yazılamaz.</span><span class="sxs-lookup"><span data-stu-id="b0947-168">There is no streaming of objects; objects cannot be written to the pipeline either intentionally or by accident.</span></span>

## <a name="attributes"></a><span data-ttu-id="b0947-169">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b0947-169">Attributes</span></span>

<span data-ttu-id="b0947-170">İki yeni öznitelikler **DscResource** ve **DscProperty** eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="b0947-170">Two new attributes, **DscResource** and **DscProperty** have been added.</span></span>

## <a name="lexical-scoping-of-variables"></a><span data-ttu-id="b0947-171">Sözcük değişkenlerinin kapsamı</span><span class="sxs-lookup"><span data-stu-id="b0947-171">Lexical scoping of variables</span></span>

<span data-ttu-id="b0947-172">Aşağıdaki örnek nasıl sözcük kapsam works'ün bu sürümde gösterir.</span><span class="sxs-lookup"><span data-stu-id="b0947-172">The following shows an example of how lexical scoping works in this release.</span></span>

```powershell
$d = 42 # Script scope

function bar
{
    $d = 0 # Function scope
    [MyClass]::DoSomething()
}

class MyClass
{
    static [object] DoSomething()
    {
        return $d # error, not found dynamically
        return $script:d # no error
        $d = $script:d
        return $d # no error, found lexically
    }
}

$v = bar
$v -eq $d # true
```

## <a name="end-to-end-example"></a><span data-ttu-id="b0947-173">Uçtan uca örnek</span><span class="sxs-lookup"><span data-stu-id="b0947-173">End-to-End Example</span></span>

<span data-ttu-id="b0947-174">Aşağıdaki örnek, bir HTML dinamik bir stil sayfası dili (DSL) uygulamak için birkaç yeni, özel sınıfları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b0947-174">The following example creates several new, custom classes to implement an HTML dynamic style sheet language (DSL).</span></span>
<span data-ttu-id="b0947-175">Ardından, türleri bir modül kapsamı dışında kullanıldığından örnek başlık stilleri ve tabloları gibi öğe sınıfının bir parçası olarak belirli öğe türleri oluşturmak için yardımcı işlevleri ekler.</span><span class="sxs-lookup"><span data-stu-id="b0947-175">Then, the example adds helper functions to create specific element types as part of the element class, such as heading styles and tables, because types cannot be used outside the scope of a module.</span></span>

```powershell
# Classes that define the structure of the document
#
class Html
{
    [string] $docType
    [HtmlHead] $Head
    [Element[]] $Body

    [string] Render()
    {
        $text = "<html>`n<head>`n"
        $text += $this.Head
        $text += "`n</head>`n<body>`n"
        $text += $this.Body -join "`n" # Render all of the body elements
        $text += "</body>`n</html>"
        return $text
    }
    [string] ToString() { return $this.Render() }
}

class HtmlHead
{
    $Title
    $Base
    $Link
    $Style
    $Meta
    $Script
    [string] Render() { return "<title>$($this.Title)</title>" }
    [string] ToString() { return $this.Render() }
}

class Element
{
    [string] $Tag
    [string] $Text
    [hashtable] $Attributes
    [string] Render() {
        $attributesText= ""
        if ($this.Attributes)
        {
            foreach ($attr in $this.Attributes.Keys)
            {
                #BUGBUG - need to validate keys against attribute
                $attributesText += " $attr=`"$($this.Attributes[$attr])\`""
            }
        }
        return "<$($this.tag)${attributesText}>$($this.text)</$($this.tag)>`n"
    }
[string] ToString() { return $this.Render() }
}

#
# Helper functions for creating specific element types on top of the classes.
# These are required because types aren’t visible outside of the module.
#

function H1 { [Element] @{ Tag = "H1" ; Text = $args.foreach{$_} -join " " }}
function H2 { [Element] @{ Tag = "H2" ; Text = $args.foreach{$_} -join " " }}
function H3 { [Element] @{ Tag = "H3" ; Text = $args.foreach{$_} -join " " }}
function P { [Element] @{ Tag = "P" ; Text = $args.foreach{$_} -join " " }}
function B { [Element] @{ Tag = "B" ; Text = $args.foreach{$_} -join " " }}
function I { [Element] @{ Tag = "I" ; Text = $args.foreach{$_} -join " " }}
function HREF
{
    param (
        $Name,
        $Link
    )
    return [Element] @{
        Tag = "A"
        Attributes = @{ HREF = $link }
        Text = $name
    }
}
function Table
{
    param (
    [Parameter(Mandatory)]
    [object[]]
        $Data,
    [Parameter()]
    [string[]]
        $Properties = "*",
    [Parameter()]
    [hashtable]
        $Attributes = @{ border=2; cellpadding=2; cellspacing=2 }
    )
$bodyText = ""
# Add the header tags
$bodyText += $Properties.foreach{TH $_}
# Add the rows
$bodyText += foreach ($row in $Data)
    {
        TR (-join $Properties.Foreach{ TD ($row.$\_) } )
    }

    $table = [Element] @{
        Tag = "Table"
        Attributes = $Attributes
        Text = $bodyText
    }
$table
}
function TH { ([Element] @{ Tag = "TH" ; Text = $args.foreach{$_} -join " " }) }
function TR { ([Element] @{ Tag = "TR" ; Text = $args.foreach{$_} -join " " }) }
function TD { ([Element] @{ Tag = "TD" ; Text = $args.foreach{$_} -join " " }) }
function Style

{
    return [Element] @{
        Tag = "style"
        Text = "$args"
    }
}

# Takes a hash table, casts it to and HTML document
# and then returns the resulting type.
#
function Html ([HTML] $doc) { return $doc }
```
