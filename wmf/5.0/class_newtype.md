---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: a96a4a58dafa01fb43f5bdffb52ef833816148e7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688479"
---
# <a name="new-language-features-in-powershell-50"></a><span data-ttu-id="c3197-102">PowerShell 5.0 yeni dil özellikleri</span><span class="sxs-lookup"><span data-stu-id="c3197-102">New language features in PowerShell 5.0</span></span>

<span data-ttu-id="c3197-103">PowerShell 5.0, Windows PowerShell içinde aşağıdaki yeni dil öğelerini sunar:</span><span class="sxs-lookup"><span data-stu-id="c3197-103">PowerShell 5.0 introduces the following new language elements in Windows PowerShell:</span></span>

## <a name="class-keyword"></a><span data-ttu-id="c3197-104">Class anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="c3197-104">Class keyword</span></span>

<span data-ttu-id="c3197-105">**Sınıfı** anahtar sözcüğü, yeni bir sınıf tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c3197-105">The **class** keyword defines a new class.</span></span> <span data-ttu-id="c3197-106">Gerçek bir .NET Framework türü budur.</span><span class="sxs-lookup"><span data-stu-id="c3197-106">This is a true .NET Framework type.</span></span>
<span data-ttu-id="c3197-107">Sınıf üyelerine genel, ancak yalnızca ortak modülü kapsamında değildir.</span><span class="sxs-lookup"><span data-stu-id="c3197-107">Class members are public, but only public within the module scope.</span></span>
<span data-ttu-id="c3197-108">Tür adı bir dize olarak başvurulamaz (örneğin, `New-Object` çalışmıyor), ve bu sürümde, bir tür sabit değer kullanamazsınız (örneğin, `[MyClass]`) sınıfı tanımlanır betik/modülü dosyanın dışında.</span><span class="sxs-lookup"><span data-stu-id="c3197-108">You can't refer to the type name as a string (for example, `New-Object` doesn't work), and in this release, you can't use a type literal (for example, `[MyClass]`) outside the script/module file in which the class is defined.</span></span>

```powershell
class MyClass
{
    ...
}
```

## <a name="enum-keyword-and-enumerations"></a><span data-ttu-id="c3197-109">Enum anahtar sözcüğü ve numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="c3197-109">Enum keyword and enumerations</span></span>

<span data-ttu-id="c3197-110">Destek **enum** anahtar sözcüğü eklendi, yeni satır ayırıcı olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="c3197-110">Support for the **enum** keyword has been added, which uses newline as the delimiter.</span></span>
<span data-ttu-id="c3197-111">Geçerli sınırlamalar: bir numaralandırıcı kendisi açısından tanımlayamazsınız ancak aşağıdaki örnekte gösterildiği gibi başka bir sabit listesi açısından enum başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c3197-111">Current limitations: you cannot define an enumerator in terms of itself, but you can initialize an enum in terms of another enum, as shown in the following example.</span></span>
<span data-ttu-id="c3197-112">Ayrıca, şu anda temel türü belirtilemez; her zaman [int].</span><span class="sxs-lookup"><span data-stu-id="c3197-112">Also, the base type cannot currently be specified; it is always [int].</span></span>

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

<span data-ttu-id="c3197-113">Numaralandırıcı değeri ayrıştırma zamanı sabiti olmalıdır; çağrılan bir komutun sonucuna ayarlanamaz.</span><span class="sxs-lookup"><span data-stu-id="c3197-113">An enumerator value must be a parse time constant; you cannot set it to the result of an invoked command.</span></span>

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

<span data-ttu-id="c3197-114">Numaralandırmalar, aşağıdaki örnekte gösterildiği gibi aritmetik işlemleri destekler.</span><span class="sxs-lookup"><span data-stu-id="c3197-114">Enums support arithmetic operations, as shown in the following example.</span></span>

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

## <a name="import-dscresource"></a><span data-ttu-id="c3197-115">Import-DscResource</span><span class="sxs-lookup"><span data-stu-id="c3197-115">Import-DscResource</span></span>

<span data-ttu-id="c3197-116">**Import-DscResource** true dinamik bir anahtar sözcüğü sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="c3197-116">**Import-DscResource** is now a true dynamic keyword.</span></span>
<span data-ttu-id="c3197-117">PowerShell içeren sınıflar için arama belirtilen modülün kök modül ayrıştırır **DscResource** özniteliği.</span><span class="sxs-lookup"><span data-stu-id="c3197-117">PowerShell parses the specified module’s root module, searching for classes that contain the **DscResource** attribute.</span></span>

## <a name="implementingassembly"></a><span data-ttu-id="c3197-118">ImplementingAssembly</span><span class="sxs-lookup"><span data-stu-id="c3197-118">ImplementingAssembly</span></span>

<span data-ttu-id="c3197-119">Yeni bir alan **ImplementingAssembly**, ModuleInfo için eklendi.</span><span class="sxs-lookup"><span data-stu-id="c3197-119">A new field, **ImplementingAssembly**, has been added to ModuleInfo.</span></span> <span data-ttu-id="c3197-120">Sınıflar komut dosyasını tanımlayan bir betik modülü için oluşturulan dinamik derlemenin veya ikili modülleri için yüklü bütünleştirilmiş kodu için ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="c3197-120">It is set to the dynamic assembly created for a script module if the script defines classes, or the loaded assembly for binary modules.</span></span> <span data-ttu-id="c3197-121">Ne zaman ayarlanmadı ModuleType bildirimi =.</span><span class="sxs-lookup"><span data-stu-id="c3197-121">It is not set when ModuleType = Manifest.</span></span>

<span data-ttu-id="c3197-122">Yansıma **ImplementingAssembly** alan Modül içindeki kaynakları bulur.</span><span class="sxs-lookup"><span data-stu-id="c3197-122">Reflection on the **ImplementingAssembly** field discovers resources in a module.</span></span> <span data-ttu-id="c3197-123">Başka bir deyişle, PowerShell veya başka yönetilen dillerde yazılmış kaynakları bulabilir.</span><span class="sxs-lookup"><span data-stu-id="c3197-123">This means you can discover resources written in either PowerShell or other managed languages.</span></span>

<span data-ttu-id="c3197-124">Başlatıcıları olan alanlar:</span><span class="sxs-lookup"><span data-stu-id="c3197-124">Fields with initializers:</span></span>

```powershell
[int] $i = 5
```

<span data-ttu-id="c3197-125">Statik desteklenir. herhangi bir sırada belirtilen tür kısıtlamaları bunun gibi bir öznitelik gibi çalışır.</span><span class="sxs-lookup"><span data-stu-id="c3197-125">Static is supported; it works like an attribute, as do the type constraints, so it can be specified in any order.</span></span>

```powershell
static [int] $count = 0
```

<span data-ttu-id="c3197-126">Bir tür isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="c3197-126">A type is optional.</span></span>

```powershell
$s = "hello"
```

<span data-ttu-id="c3197-127">Tüm üyeleri ortaktır.</span><span class="sxs-lookup"><span data-stu-id="c3197-127">All members are public.</span></span>

## <a name="constructors-and-instantiation"></a><span data-ttu-id="c3197-128">Oluşturucular ve örnek oluşturma</span><span class="sxs-lookup"><span data-stu-id="c3197-128">Constructors and instantiation</span></span>

<span data-ttu-id="c3197-129">Windows PowerShell sınıflarını oluşturucuları olabilir; Bunlar, sınıfı aynı ada sahip.</span><span class="sxs-lookup"><span data-stu-id="c3197-129">Windows PowerShell classes can have constructors; they have the same name as their class.</span></span> <span data-ttu-id="c3197-130">Oluşturucu aşırı yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="c3197-130">Constructors can be overloaded.</span></span> <span data-ttu-id="c3197-131">Statik oluşturucularda desteklenir.</span><span class="sxs-lookup"><span data-stu-id="c3197-131">Static constructors are supported.</span></span> <span data-ttu-id="c3197-132">Başlatma ifadeleri özellikleriyle herhangi bir kod Oluşturucu çalıştırılmadan önce başlatılır.</span><span class="sxs-lookup"><span data-stu-id="c3197-132">Properties with initialization expressions are initialized before running any code in a constructor.</span></span> <span data-ttu-id="c3197-133">Statik özellikler statik Oluşturucu gövdesinde önce başlatılır ve örnek özelliklerini statik olmayan Oluşturucu gövdesinde önce başlatılır.</span><span class="sxs-lookup"><span data-stu-id="c3197-133">Static properties are initialized before the body of a static constructor, and instance properties are initialized before the body of the non-static constructor.</span></span> <span data-ttu-id="c3197-134">Şu anda başka bir oluşturucudan bir oluşturucu çağırmak için hiçbir sözdizimi yoktur (ister C\# söz dizimi ": this()").</span><span class="sxs-lookup"><span data-stu-id="c3197-134">Currently, there is no syntax for calling a constructor from another constructor (like the C\# syntax ": this()").</span></span> <span data-ttu-id="c3197-135">Geçici çözüm, ortak bir Init yöntemi tanımlamaktır.</span><span class="sxs-lookup"><span data-stu-id="c3197-135">The workaround is to define a common Init method.</span></span>

<span data-ttu-id="c3197-136">Bu sürümde örnekleme sınıflarının yolları aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c3197-136">The following are ways of instantiating classes in this release.</span></span>

<span data-ttu-id="c3197-137">Varsayılan oluşturucu kullanılarak örnekleme.</span><span class="sxs-lookup"><span data-stu-id="c3197-137">Instantiating by using the default constructor.</span></span> <span data-ttu-id="c3197-138">New-Object bu sürümde desteklenmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c3197-138">Note that New-Object is not supported in this release.</span></span>

```powershell
$a = [MyClass]::new()
```

<span data-ttu-id="c3197-139">Bir parametresi olan yapılandırıcının</span><span class="sxs-lookup"><span data-stu-id="c3197-139">Calling a constructor with a parameter</span></span>

```powershell
$b = [MyClass]::new(42)
```

<span data-ttu-id="c3197-140">Birden çok parametre ile bir oluşturucu için bir dizi geçirme</span><span class="sxs-lookup"><span data-stu-id="c3197-140">Passing an array to a constructor with multiple parameters</span></span>
```powershell
$c = [MyClass]::new(@(42,43,44), "Hello")
```

<span data-ttu-id="c3197-141">Bu sürümde, Windows PowerShell içinde tanımlanan sınıflar ile New-Object çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="c3197-141">In this release, New-Object does not work with classes defined in Windows PowerShell.</span></span> <span data-ttu-id="c3197-142">Ayrıca bu sürüm için tür adı yalnızca sözcüksel olarak, modül veya sınıf tanımlar betik dışında görünür olmadığı anlamına gelir görülebilir.</span><span class="sxs-lookup"><span data-stu-id="c3197-142">Also for this release, the type name is only visible lexically, meaning it is not visible outside of the module or script that defines the class.</span></span> <span data-ttu-id="c3197-143">İşlevler Windows PowerShell içinde tanımlanmış bir sınıfın örnekleri döndürebilir ve örnekleri de modül veya betik dışında çalışır.</span><span class="sxs-lookup"><span data-stu-id="c3197-143">Functions can return instances of a class defined in Windows PowerShell, and instances work well outside of the module or script.</span></span>

<span data-ttu-id="c3197-144">`Get-Member -Static` gibi başka bir yöntem aşırı yüklemeleri görebilecek şekilde oluşturucuları listeler.</span><span class="sxs-lookup"><span data-stu-id="c3197-144">`Get-Member -Static` lists constructors, so you can view overloads like any other method.</span></span> <span data-ttu-id="c3197-145">Bu söz dizimi performansını da New-Object önemli ölçüde daha hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="c3197-145">The performance of this syntax is also considerably faster than New-Object.</span></span>

<span data-ttu-id="c3197-146">Adlı sözde statik yöntem **yeni** aşağıdaki örnekte gösterildiği gibi .NET türleri ile çalışır.</span><span class="sxs-lookup"><span data-stu-id="c3197-146">The pseudo-static method named **new** works with .NET types, as shown in the following example.</span></span>

```powershell
[hashtable]::new()
```

<span data-ttu-id="c3197-147">Get-Member veya bu örnekte gösterildiği gibi oluşturucu aşırı yüklemeleri artık görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c3197-147">You can now see constructor overloads with Get-Member, or as shown in this example:</span></span>

```powershell
PS> [hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

## <a name="methods"></a><span data-ttu-id="c3197-148">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c3197-148">Methods</span></span>

<span data-ttu-id="c3197-149">Bir Windows PowerShell sınıfı yöntemi yalnızca bir sonlandırma bloğu sahip bir ScriptBlock gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="c3197-149">A Windows PowerShell class method is implemented as a ScriptBlock that has only an end block.</span></span> <span data-ttu-id="c3197-150">Tüm yöntemleri herkese açık.</span><span class="sxs-lookup"><span data-stu-id="c3197-150">All methods are public.</span></span> <span data-ttu-id="c3197-151">Aşağıdaki adlı bir yöntemi tanımlayan bir örnek gösterilmektedir **DoSomething**.</span><span class="sxs-lookup"><span data-stu-id="c3197-151">The following shows an example of defining a method named **DoSomething**.</span></span>

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

<span data-ttu-id="c3197-152">Yöntem çağırma:</span><span class="sxs-lookup"><span data-stu-id="c3197-152">Method invocation:</span></span>

```powershell
$b = [MyClass]::new()
$b.DoSomething(42)
```

<span data-ttu-id="c3197-153">Aşırı yüklenmiş yöntemler varolan bir yöntem ile aynı adlı ancak bunların belirtilen değerleri--Ayrıştırılan o da diğer bir deyişle, desteklenir.</span><span class="sxs-lookup"><span data-stu-id="c3197-153">Overloaded methods--that is, those that are named the same as an existing method, but differentiated by their specified values--are also supported.</span></span>

## <a name="properties"></a><span data-ttu-id="c3197-154">Özellikler</span><span class="sxs-lookup"><span data-stu-id="c3197-154">Properties</span></span>

<span data-ttu-id="c3197-155">Tüm özellikleri ortaktır.</span><span class="sxs-lookup"><span data-stu-id="c3197-155">All properties are public.</span></span> <span data-ttu-id="c3197-156">Noktalı virgül veya yeni satır özellikleri gerektirir.</span><span class="sxs-lookup"><span data-stu-id="c3197-156">Properties require either a newline or semicolon.</span></span> <span data-ttu-id="c3197-157">Hiçbir nesne türü belirtilirse, özellik türü nesnedir.</span><span class="sxs-lookup"><span data-stu-id="c3197-157">If no object type is specified, the property type is object.</span></span>

<span data-ttu-id="c3197-158">Doğrulama öznitelikleri veya bağımsız değişken dönüşümü kullanan özellikler (örneğin `[ValidateSet("aaa")]`) beklendiği gibi çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="c3197-158">Properties that use validation attributes or argument transformation attributes (e.g. `[ValidateSet("aaa")]`) work as expected.</span></span>

## <a name="hidden"></a><span data-ttu-id="c3197-159">Gizli</span><span class="sxs-lookup"><span data-stu-id="c3197-159">Hidden</span></span>

<span data-ttu-id="c3197-160">Yeni bir anahtar sözcük **gizli**, eklendi.</span><span class="sxs-lookup"><span data-stu-id="c3197-160">A new keyword, **Hidden**, has been added.</span></span> <span data-ttu-id="c3197-161">**Gizli** özelliklere ve yöntemlere (oluşturucular dahil) için uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="c3197-161">**Hidden** can be applied to properties and methods (including constructors).</span></span>

<span data-ttu-id="c3197-162">Gizli üyeleri ortaktır, ancak Get-Member çıktısında sürece görünmez Force parametresi eklendi.</span><span class="sxs-lookup"><span data-stu-id="c3197-162">Hidden members are public, but do not appear in the output of Get-Member unless the -Force parameter is added.</span></span>

<span data-ttu-id="c3197-163">Gizli üyeleri ne zaman dahil edilmez tamamlayarak veya gizli üye tanımlama sınıfında tamamlama gerçekleşmediği sürece IntelliSense kullanarak sekmesi.</span><span class="sxs-lookup"><span data-stu-id="c3197-163">Hidden members are not included when tab completing or using Intellisense unless the completion occurs in the class defining the hidden member.</span></span>

<span data-ttu-id="c3197-164">Yeni bir öznitelik **System.Management.Automation.HiddenAttribute** C# kod içinde Windows PowerShell ile aynı semantiğe sahip olabilir, böylece eklendi.</span><span class="sxs-lookup"><span data-stu-id="c3197-164">A new attribute, **System.Management.Automation.HiddenAttribute** has been added so that C# code can have the same semantics within Windows PowerShell.</span></span>

## <a name="return-types"></a><span data-ttu-id="c3197-165">Dönüş türleri</span><span class="sxs-lookup"><span data-stu-id="c3197-165">Return types</span></span>

<span data-ttu-id="c3197-166">Dönüş türü bir sözleşmedir; dönüş değeri beklenen türe dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="c3197-166">Return type is a contract; the return value is converted to the expected type.</span></span> <span data-ttu-id="c3197-167">Dönüş türü belirtilirse, dönüş türü void.</span><span class="sxs-lookup"><span data-stu-id="c3197-167">If no return type is specified, the return type is void.</span></span> <span data-ttu-id="c3197-168">Akış yok nesnelerin yoktur; nesneleri işlem hattının yanlışlıkla veya kasıtlı olarak yazılamaz.</span><span class="sxs-lookup"><span data-stu-id="c3197-168">There is no streaming of objects; objects cannot be written to the pipeline either intentionally or by accident.</span></span>

## <a name="attributes"></a><span data-ttu-id="c3197-169">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c3197-169">Attributes</span></span>

<span data-ttu-id="c3197-170">İki yeni öznitelikler **DscResource** ve **DscProperty** sürümüne eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="c3197-170">Two new attributes, **DscResource** and **DscProperty** have been added.</span></span>

## <a name="lexical-scoping-of-variables"></a><span data-ttu-id="c3197-171">Sözcük değişkenlerinin kapsamı</span><span class="sxs-lookup"><span data-stu-id="c3197-171">Lexical scoping of variables</span></span>

<span data-ttu-id="c3197-172">Aşağıdaki örnek nasıl sözcük kapsam works'ün bu sürümde gösterir.</span><span class="sxs-lookup"><span data-stu-id="c3197-172">The following shows an example of how lexical scoping works in this release.</span></span>

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

## <a name="end-to-end-example"></a><span data-ttu-id="c3197-173">Uçtan uca örneği</span><span class="sxs-lookup"><span data-stu-id="c3197-173">End-to-End Example</span></span>

<span data-ttu-id="c3197-174">Aşağıdaki örnek, bir HTML dinamik stil sayfası dil (DSL) uygulamak için birçok yeni, özel sınıf oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c3197-174">The following example creates several new, custom classes to implement an HTML dynamic style sheet language (DSL).</span></span>
<span data-ttu-id="c3197-175">Ardından, türleri, bir modül kapsamı dışında kullanılamaz çünkü örnek kapsamında başlığının stilleri ve tablolar gibi bir öğe sınıfı belirli bir öğe türleri oluşturmak için yardımcı işlevleri ekler.</span><span class="sxs-lookup"><span data-stu-id="c3197-175">Then, the example adds helper functions to create specific element types as part of the element class, such as heading styles and tables, because types cannot be used outside the scope of a module.</span></span>

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
        TR (-join $Properties.Foreach{ TD ($row.$_) } )
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
