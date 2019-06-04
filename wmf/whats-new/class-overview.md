---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: PowerShell Sınıfları Kullanarak Özel Türler Oluşturma
ms.openlocfilehash: c2c50fb65ce4931fcf6ae529b4146df391c831c4
ms.sourcegitcommit: bc42c9166857147a1ecf9924b718d4a48eb901e3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/03/2019
ms.locfileid: "66470940"
---
# <a name="creating-custom-types-using-powershell-classes"></a><span data-ttu-id="7e150-103">PowerShell Sınıfları Kullanarak Özel Türler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="7e150-103">Creating Custom Types using PowerShell Classes</span></span>

<span data-ttu-id="7e150-104">PowerShell 5.0, sınıflar ve resmi sözdizimi ve semantiği gibi diğer nesne yönelimli programlama dillerini kullanarak kullanıcı tanımlı türler diğer tanımlama olanağı eklendi.</span><span class="sxs-lookup"><span data-stu-id="7e150-104">PowerShell 5.0 added the ability to define classes and other user-defined types using formal syntax and semantics like other object-oriented programming languages.</span></span> <span data-ttu-id="7e150-105">Geliştiriciler ve BT uzmanları geniş bir kullanım için PowerShell Kucak, PowerShell yapıtları (örneğin, DSC kaynakları) geliştirilmesini basitleştirin ve yönetim yüzeyleri kapsamını hızlandırmanız, hedef etkinleştirmektir.</span><span class="sxs-lookup"><span data-stu-id="7e150-105">The goal is to enable developers and IT professionals to embrace PowerShell for a wider range of use cases, simplify development of PowerShell artifacts (such as DSC resources), and accelerate coverage of management surfaces.</span></span>

## <a name="supported-scenarios-in-this-release"></a><span data-ttu-id="7e150-106">Bu sürümde desteklenen senaryolar</span><span class="sxs-lookup"><span data-stu-id="7e150-106">Supported scenarios in this release</span></span>

- <span data-ttu-id="7e150-107">PowerShell dilini kullanarak DSC kaynakları ve ilişkili türlerini tanımlayın</span><span class="sxs-lookup"><span data-stu-id="7e150-107">Define DSC resources and their associated types by using the PowerShell language</span></span>
- <span data-ttu-id="7e150-108">Bilinen nesne yönelimli programlama yapıları, sınıflar, özellikler, yöntemler vb. gibi kullanarak PowerShell'de özel türleri tanımla</span><span class="sxs-lookup"><span data-stu-id="7e150-108">Define custom types in PowerShell by using familiar object-oriented programming constructs, such as classes, properties, methods, etc.</span></span>
- <span data-ttu-id="7e150-109">PowerShell ve sınıf temel DSC kaynak sınıfıyla devralma desteği</span><span class="sxs-lookup"><span data-stu-id="7e150-109">Inheritance support with class in PowerShell and class base DSC resource</span></span>
- <span data-ttu-id="7e150-110">PowerShell dilini kullanarak türlerinde hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="7e150-110">Debug types by using the PowerShell language</span></span>
- <span data-ttu-id="7e150-111">Oluşturma ve resmi mekanizmalarını kullanarak ve doğru düzeyde özel durumları işleme</span><span class="sxs-lookup"><span data-stu-id="7e150-111">Generate and handle exceptions by using formal mechanisms, and at the right level</span></span>

## <a name="declare-base-class"></a><span data-ttu-id="7e150-112">Temel Sınıf Bildirme</span><span class="sxs-lookup"><span data-stu-id="7e150-112">Declare Base Class</span></span>

<span data-ttu-id="7e150-113">Bir PowerShell sınıfı, başka bir PowerShell sınıfı için bir temel tür olarak bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7e150-113">You can declare a PowerShell class as a base type for another PowerShell class.</span></span>

```powershell
class bar
{
   [int]foo()
       {
           return 100500
       }
}

class baz : bar {}

[baz]::new().foo() # return 100500
```

<span data-ttu-id="7e150-114">Temel sınıf olarak var olan .NET Framework türleri de kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7e150-114">You can also use existing .NET Framework types as base classes:</span></span>

```powershell
class MyIntList : system.collections.generic.list[int]
{

}

$list = [MyIntList]::new()

$list.Add(100)

$list[0] # return 100
```

### <a name="call-base-class-constructor"></a><span data-ttu-id="7e150-115">Temel Sınıf Oluşturucusunu Çağırma</span><span class="sxs-lookup"><span data-stu-id="7e150-115">Call Base Class Constructor</span></span>

<span data-ttu-id="7e150-116">Bir temel sınıf oluşturucusunu bir alt sınıfı için anahtar sözcüğünü kullanın **temel**:</span><span class="sxs-lookup"><span data-stu-id="7e150-116">To call a base class constructor from a subclass, use the keyword **base**:</span></span>

```powershell
class A
{
    [int]$a

    A([int]$a)
    {
        $this.a = $a
    }
}

class B : A
{
    B() : base(103) {}
}

[B]::new().a # return 103
```

<span data-ttu-id="7e150-117">Bir temel sınıf (parametre) varsayılan bir oluşturucusu varsa, bir açık oluşturucu çağrısı atlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7e150-117">If a base class has a default (no parameter) constructor, you can omit an explicit constructor call:</span></span>

```powershell
class C : B
{
    C([int]$c) {}
}
```

### <a name="call-base-class-method"></a><span data-ttu-id="7e150-118">Temel Sınıf Yöntemini Çağırma</span><span class="sxs-lookup"><span data-stu-id="7e150-118">Call Base Class Method</span></span>

<span data-ttu-id="7e150-119">Alt sınıfların mevcut yöntemleri geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7e150-119">You can override existing methods in subclasses.</span></span> <span data-ttu-id="7e150-120">Bunu yapmak için aynı ada ve imzaya kullanarak yöntemleri bildirin:</span><span class="sxs-lookup"><span data-stu-id="7e150-120">To do this, declare methods by using the same name and signature:</span></span>

```powershell
class baseClass
{
    [int]foo() {return 100500}
}

class childClass1 : baseClass
{
    [int]foo() {return 200600}
}

[childClass1]::new().foo() # return 200600
```

<span data-ttu-id="7e150-121">Geçersiz kılınan uygulamaları taban sınıf yöntemlerini çağırmak için temel sınıf için atama (`[baseClass]$this`) çağırma üzerinde:</span><span class="sxs-lookup"><span data-stu-id="7e150-121">To call base class methods from overridden implementations, cast to the base class (`[baseClass]$this`) on invocation:</span></span>

```powershell
class childClass2 : baseClass
{
    [int]foo()
    {
        return 3 * ([baseClass]$this).foo()
    }
}

[childClass2]::new().foo() # return 301500
```

<span data-ttu-id="7e150-122">Tüm PowerShell yöntemler sanaldır.</span><span class="sxs-lookup"><span data-stu-id="7e150-122">All PowerShell methods are virtual.</span></span> <span data-ttu-id="7e150-123">Aynı ada ve imzaya sahip yöntemleri bildirerek bir geçersiz kılma için yaptığınız gibi aynı sözdizimini kullanarak bir alt sanal olmayan .NET yöntemleri gizleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7e150-123">You can hide non-virtual .NET methods in a subclass by using the same syntax as you do for an override, by declaring methods with same name and signature.</span></span>

```powershell
class MyIntList : system.collections.generic.list[int]
{
    # Add is final in system.collections.generic.list
    [void] Add([int]$arg)
    {
        ([system.collections.generic.list[int]]$this).Add($arg * 2)
    }
}

$list = [MyIntList]::new()
$list.Add(100)
$list[0] # return 200
```

### <a name="declare-implemented-interface"></a><span data-ttu-id="7e150-124">Uygulanan Arabirimi Bildirme</span><span class="sxs-lookup"><span data-stu-id="7e150-124">Declare Implemented Interface</span></span>

<span data-ttu-id="7e150-125">Belirtilen hiçbir temel türü varsa temel türleri bir iki nokta üst üste (:) hemen sonra veya uygulanan arabirimleri bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7e150-125">You can declare implemented interfaces after base types, or immediately after a colon (:), if there is no base type specified.</span></span> <span data-ttu-id="7e150-126">Tüm tür adları virgül kullanarak ayırın.</span><span class="sxs-lookup"><span data-stu-id="7e150-126">Separate all type names by using commas.</span></span> <span data-ttu-id="7e150-127">Benzer C# söz dizimi.</span><span class="sxs-lookup"><span data-stu-id="7e150-127">It's similar to C# syntax.</span></span>

```powershell
class MyComparable : system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}

class MyComparableBar : bar, system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}
```

## <a name="new-language-features-in-powershell-50"></a><span data-ttu-id="7e150-128">PowerShell 5.0 yeni dil özellikleri</span><span class="sxs-lookup"><span data-stu-id="7e150-128">New language features in PowerShell 5.0</span></span>

<span data-ttu-id="7e150-129">PowerShell 5.0, PowerShell aşağıdaki yeni dil öğelerini sunar:</span><span class="sxs-lookup"><span data-stu-id="7e150-129">PowerShell 5.0 introduces the following new language elements in PowerShell:</span></span>

### <a name="class-keyword"></a><span data-ttu-id="7e150-130">Class anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="7e150-130">Class keyword</span></span>

<span data-ttu-id="7e150-131">`class` Anahtar sözcüğü, yeni bir sınıf tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7e150-131">The `class` keyword defines a new class.</span></span> <span data-ttu-id="7e150-132">Gerçek bir .NET Framework türü budur.</span><span class="sxs-lookup"><span data-stu-id="7e150-132">This is a true .NET Framework type.</span></span> <span data-ttu-id="7e150-133">Sınıf üyelerine genel, ancak yalnızca ortak modülü kapsamında değildir.</span><span class="sxs-lookup"><span data-stu-id="7e150-133">Class members are public, but only public within the module scope.</span></span> <span data-ttu-id="7e150-134">Tür adı bir dize olarak başvurulamaz (örneğin, `New-Object` çalışmıyor), ve bu sürümde, bir tür sabit değer kullanamazsınız (örneğin, `[MyClass]`) sınıfı tanımlanır komut veya modül dosyasının dışında.</span><span class="sxs-lookup"><span data-stu-id="7e150-134">You can't refer to the type name as a string (for example, `New-Object` doesn't work), and in this release, you can't use a type literal (for example, `[MyClass]`) outside the script or module file in which the class is defined.</span></span>

```powershell
class MyClass
{
    ...
}
```

### <a name="enum-keyword-and-enumerations"></a><span data-ttu-id="7e150-135">Enum anahtar sözcüğü ve numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="7e150-135">Enum keyword and enumerations</span></span>

<span data-ttu-id="7e150-136">Destek `enum` anahtar sözcüğü eklendi, yeni satır ayırıcı olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="7e150-136">Support for the `enum` keyword has been added, which uses newline as the delimiter.</span></span> <span data-ttu-id="7e150-137">Şu anda bir numaralandırıcı kendisi açısından tanımlayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="7e150-137">Currently, you cannot define an enumerator in terms of itself.</span></span> <span data-ttu-id="7e150-138">Ancak, aşağıdaki örnekte gösterildiği gibi başka bir sabit listesi açısından enum başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7e150-138">However, you can initialize an enum in terms of another enum, as shown in the following example.</span></span> <span data-ttu-id="7e150-139">Ayrıca, temel türü belirtilemez; her zaman `[int]`.</span><span class="sxs-lookup"><span data-stu-id="7e150-139">Also, the base type cannot be specified; it is always `[int]`.</span></span>

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

<span data-ttu-id="7e150-140">Numaralandırıcı değeri ayrıştırma zamanı sabiti olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7e150-140">An enumerator value must be a parse time constant.</span></span> <span data-ttu-id="7e150-141">Çağrılan bir komutun sonucuna ayarlanamaz.</span><span class="sxs-lookup"><span data-stu-id="7e150-141">You cannot set it to the result of an invoked command.</span></span>

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

<span data-ttu-id="7e150-142">Numaralandırmalar, aşağıdaki örnekte gösterildiği gibi aritmetik işlemleri destekler.</span><span class="sxs-lookup"><span data-stu-id="7e150-142">Enums support arithmetic operations, as shown in the following example.</span></span>

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

### <a name="import-dscresource"></a><span data-ttu-id="7e150-143">Import-DscResource</span><span class="sxs-lookup"><span data-stu-id="7e150-143">Import-DscResource</span></span>

<span data-ttu-id="7e150-144">`Import-DscResource` true dinamik bir anahtar sözcüğü sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="7e150-144">`Import-DscResource` is now a true dynamic keyword.</span></span> <span data-ttu-id="7e150-145">PowerShell içeren sınıflar için arama belirtilen modülün kök modül ayrıştırır **DscResource** özniteliği.</span><span class="sxs-lookup"><span data-stu-id="7e150-145">PowerShell parses the specified module's root module, searching for classes that contain the **DscResource** attribute.</span></span>

### <a name="implementingassembly"></a><span data-ttu-id="7e150-146">ImplementingAssembly</span><span class="sxs-lookup"><span data-stu-id="7e150-146">ImplementingAssembly</span></span>

<span data-ttu-id="7e150-147">Yeni bir alan **ImplementingAssembly**, eklenmiş **ModuleInfo**.</span><span class="sxs-lookup"><span data-stu-id="7e150-147">A new field, **ImplementingAssembly**, has been added to **ModuleInfo**.</span></span> <span data-ttu-id="7e150-148">Sınıflar komut dosyasını tanımlayan bir betik modülü için oluşturulan dinamik derlemenin veya ikili modülleri için yüklü bütünleştirilmiş kodu için ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="7e150-148">It is set to the dynamic assembly created for a script module if the script defines classes, or the loaded assembly for binary modules.</span></span> <span data-ttu-id="7e150-149">Ne zaman ayarlanmadı **ModuleType** olduğu **bildirim**.</span><span class="sxs-lookup"><span data-stu-id="7e150-149">It is not set when **ModuleType** is **Manifest**.</span></span>

<span data-ttu-id="7e150-150">Yansıma **ImplementingAssembly** alan Modül içindeki kaynakları bulur.</span><span class="sxs-lookup"><span data-stu-id="7e150-150">Reflection on the **ImplementingAssembly** field discovers resources in a module.</span></span> <span data-ttu-id="7e150-151">Başka bir deyişle, PowerShell veya başka yönetilen dillerde yazılmış kaynakları bulabilir.</span><span class="sxs-lookup"><span data-stu-id="7e150-151">This means you can discover resources written in either PowerShell or other managed languages.</span></span>

<span data-ttu-id="7e150-152">Başlatıcıları olan alanlar:</span><span class="sxs-lookup"><span data-stu-id="7e150-152">Fields with initializers:</span></span>

```powershell
[int] $i = 5
```

<span data-ttu-id="7e150-153">`Static` desteklenir.</span><span class="sxs-lookup"><span data-stu-id="7e150-153">`Static` is supported.</span></span> <span data-ttu-id="7e150-154">Tür kısıtlamaları gibi bir öznitelik gibi çalışır.</span><span class="sxs-lookup"><span data-stu-id="7e150-154">It works like an attribute, as do the type constraints.</span></span> <span data-ttu-id="7e150-155">Herhangi bir sırada belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="7e150-155">It can be specified in any order.</span></span>

```powershell
static [int] $count = 0
```

<span data-ttu-id="7e150-156">Bir tür isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="7e150-156">A type is optional.</span></span>

```powershell
$s = "hello"
```

<span data-ttu-id="7e150-157">Tüm üyeleri ortaktır.</span><span class="sxs-lookup"><span data-stu-id="7e150-157">All members are public.</span></span>

### <a name="constructors-and-instantiation"></a><span data-ttu-id="7e150-158">Oluşturucular ve örnek oluşturma</span><span class="sxs-lookup"><span data-stu-id="7e150-158">Constructors and instantiation</span></span>

<span data-ttu-id="7e150-159">PowerShell sınıflarını oluşturuculara sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="7e150-159">PowerShell classes can have constructors.</span></span> <span data-ttu-id="7e150-160">Bunlar, sınıfı aynı ada sahip.</span><span class="sxs-lookup"><span data-stu-id="7e150-160">They have the same name as their class.</span></span> <span data-ttu-id="7e150-161">Oluşturucu aşırı yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="7e150-161">Constructors can be overloaded.</span></span> <span data-ttu-id="7e150-162">Statik oluşturucularda desteklenir.</span><span class="sxs-lookup"><span data-stu-id="7e150-162">Static constructors are supported.</span></span> <span data-ttu-id="7e150-163">Başlatma ifadeleri özellikleriyle herhangi bir kod Oluşturucu çalıştırılmadan önce başlatılır.</span><span class="sxs-lookup"><span data-stu-id="7e150-163">Properties with initialization expressions are initialized before running any code in a constructor.</span></span> <span data-ttu-id="7e150-164">Statik özellikler statik Oluşturucu gövdesinde önce başlatılır ve örnek özelliklerini statik olmayan Oluşturucu gövdesinde önce başlatılır.</span><span class="sxs-lookup"><span data-stu-id="7e150-164">Static properties are initialized before the body of a static constructor, and instance properties are initialized before the body of the non-static constructor.</span></span> <span data-ttu-id="7e150-165">Şu anda başka bir oluşturucudan bir oluşturucu çağırmak için hiçbir sözdizimi yoktur (ister C\# söz dizimi ": this()").</span><span class="sxs-lookup"><span data-stu-id="7e150-165">Currently, there is no syntax for calling a constructor from another constructor (like the C\# syntax ": this()").</span></span> <span data-ttu-id="7e150-166">Geçici çözüm, ortak bir tanımlamaktır `Init()` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7e150-166">The workaround is to define a common `Init()` method.</span></span>

#### <a name="creating-instances"></a><span data-ttu-id="7e150-167">Örnekler oluşturma</span><span class="sxs-lookup"><span data-stu-id="7e150-167">Creating instances</span></span>

> [!NOTE]
> <span data-ttu-id="7e150-168">PowerShell 5.0 `New-Object` PowerShell içinde tanımlanan sınıflar ile çalışmıyor.</span><span class="sxs-lookup"><span data-stu-id="7e150-168">In PowerShell 5.0, `New-Object` does not work with classes defined in PowerShell.</span></span> <span data-ttu-id="7e150-169">Ayrıca, tür adı yalnızca sözcüksel olarak, modül veya sınıf tanımlar betik dışında görünür olmadığı anlamına gelir görülebilir.</span><span class="sxs-lookup"><span data-stu-id="7e150-169">Also, the type name is only visible lexically, meaning it is not visible outside of the module or script that defines the class.</span></span> <span data-ttu-id="7e150-170">İşlevler, PowerShell içinde tanımlanmış bir sınıfın örnekleri döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="7e150-170">Functions can return instances of a class defined in PowerShell.</span></span> <span data-ttu-id="7e150-171">Bu örnekler, modül veya betik dışında çalışır.</span><span class="sxs-lookup"><span data-stu-id="7e150-171">Those instances work outside of the module or script.</span></span>

1. <span data-ttu-id="7e150-172">Varsayılan oluşturucu kullanılarak örnekleme.</span><span class="sxs-lookup"><span data-stu-id="7e150-172">Instantiating by using the default constructor.</span></span>

   ```powershell
   $a = [MyClass]::new()
   ```

1. <span data-ttu-id="7e150-173">Bir parametresi olan yapılandırıcının</span><span class="sxs-lookup"><span data-stu-id="7e150-173">Calling a constructor with a parameter</span></span>

   ```powershell
   $b = [MyClass]::new(42)
   ```

1. <span data-ttu-id="7e150-174">Birden çok parametre ile bir oluşturucu için bir dizi geçirme.</span><span class="sxs-lookup"><span data-stu-id="7e150-174">Passing an array to a constructor with multiple parameters.</span></span>

   ```powershell
   $c = [MyClass]::new(@(42,43,44), "Hello")
   ```

<span data-ttu-id="7e150-175">Sözde statik yöntem `new()` aşağıdaki örnekte gösterildiği gibi .NET türleri ile çalışır.</span><span class="sxs-lookup"><span data-stu-id="7e150-175">The pseudo-static method `new()` works with .NET types, as shown in the following example.</span></span>

```powershell
[hashtable]::new()
```

#### <a name="discovering-constructors"></a><span data-ttu-id="7e150-176">Oluşturucular keşfetme</span><span class="sxs-lookup"><span data-stu-id="7e150-176">Discovering constructors</span></span>

<span data-ttu-id="7e150-177">Oluşturucu aşırı yüklemeleri ile artık gördüğünüz `Get-Member`, veya bu örnekte gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="7e150-177">You can now see constructor overloads with `Get-Member`, or as shown in this example:</span></span>

```powershell
PS> [hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

<span data-ttu-id="7e150-178">`Get-Member -Static` gibi başka bir yöntem aşırı yüklemeleri görebilecek şekilde oluşturucuları listeler.</span><span class="sxs-lookup"><span data-stu-id="7e150-178">`Get-Member -Static` lists constructors, so you can view overloads like any other method.</span></span> <span data-ttu-id="7e150-179">Bu söz dizimi performansını da önemli ölçüde daha hızlı bir şekilde `New-Object`.</span><span class="sxs-lookup"><span data-stu-id="7e150-179">The performance of this syntax is also considerably faster than `New-Object`.</span></span>

### <a name="methods"></a><span data-ttu-id="7e150-180">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="7e150-180">Methods</span></span>

<span data-ttu-id="7e150-181">Bir PowerShell sınıfı yöntemi olarak uygulanan bir **ScriptBlock** olan yalnızca bir sonlandırma bloğu.</span><span class="sxs-lookup"><span data-stu-id="7e150-181">A PowerShell class method is implemented as a **ScriptBlock** that has only an end block.</span></span> <span data-ttu-id="7e150-182">Tüm yöntemleri herkese açık.</span><span class="sxs-lookup"><span data-stu-id="7e150-182">All methods are public.</span></span> <span data-ttu-id="7e150-183">Aşağıdaki adlı bir yöntemi tanımlayan bir örnek gösterilmektedir **DoSomething**.</span><span class="sxs-lookup"><span data-stu-id="7e150-183">The following shows an example of defining a method named **DoSomething**.</span></span>

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

<span data-ttu-id="7e150-184">Yöntem çağırma:</span><span class="sxs-lookup"><span data-stu-id="7e150-184">Method invocation:</span></span>

```powershell
$b = [MyClass]::new()
$b.DoSomething(42)
```

<span data-ttu-id="7e150-185">Aşırı yüklenmiş yöntemler de desteklenir.</span><span class="sxs-lookup"><span data-stu-id="7e150-185">Overloaded methods are also supported.</span></span>

### <a name="properties"></a><span data-ttu-id="7e150-186">Özellikler</span><span class="sxs-lookup"><span data-stu-id="7e150-186">Properties</span></span>

<span data-ttu-id="7e150-187">Tüm özellikleri ortaktır.</span><span class="sxs-lookup"><span data-stu-id="7e150-187">All properties are public.</span></span> <span data-ttu-id="7e150-188">Noktalı virgül veya yeni satır özellikleri gerektirir.</span><span class="sxs-lookup"><span data-stu-id="7e150-188">Properties require either a newline or semicolon.</span></span> <span data-ttu-id="7e150-189">Hiçbir nesne türü belirtilirse, özellik türü nesnedir.</span><span class="sxs-lookup"><span data-stu-id="7e150-189">If no object type is specified, the property type is object.</span></span>

<span data-ttu-id="7e150-190">Doğrulama veya bağımsız değişken dönüşümü öznitelikleri özellikleri (gibi `[ValidateSet("aaa")]`) beklendiği gibi çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="7e150-190">Properties that use validation or argument transformation attributes (like `[ValidateSet("aaa")]`) work as expected.</span></span>

### <a name="hidden"></a><span data-ttu-id="7e150-191">Hidden</span><span class="sxs-lookup"><span data-stu-id="7e150-191">Hidden</span></span>

<span data-ttu-id="7e150-192">Yeni bir anahtar sözcük `Hidden`, eklendi.</span><span class="sxs-lookup"><span data-stu-id="7e150-192">A new keyword, `Hidden`, has been added.</span></span> <span data-ttu-id="7e150-193">`Hidden` Özellikler ve yöntemler (oluşturucular dahil) için uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="7e150-193">`Hidden` can be applied to properties and methods (including constructors).</span></span>

<span data-ttu-id="7e150-194">Gizli üyeleri ortaktır, ancak çıktısında görünmez `Get-Member` sürece `-Force` parametresi eklendi.</span><span class="sxs-lookup"><span data-stu-id="7e150-194">Hidden members are public, but do not appear in the output of `Get-Member` unless the `-Force` parameter is added.</span></span> <span data-ttu-id="7e150-195">Gizli üyeleri ne zaman dahil edilmez tamamlayarak veya gizli üye tanımlama sınıfında tamamlama gerçekleşmediği sürece IntelliSense kullanarak sekmesi.</span><span class="sxs-lookup"><span data-stu-id="7e150-195">Hidden members are not included when tab completing or using Intellisense unless the completion occurs in the class defining the hidden member.</span></span>

<span data-ttu-id="7e150-196">Yeni bir öznitelik **System.Management.Automation.HiddenAttribute** bunu eklendi, C\# kod içinde PowerShell ile aynı semantiğe sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="7e150-196">A new attribute, **System.Management.Automation.HiddenAttribute** has been added so that C\# code can have the same semantics within PowerShell.</span></span>

### <a name="return-types"></a><span data-ttu-id="7e150-197">Dönüş türleri</span><span class="sxs-lookup"><span data-stu-id="7e150-197">Return types</span></span>

<span data-ttu-id="7e150-198">Dönüş türü bir sözleşmedir.</span><span class="sxs-lookup"><span data-stu-id="7e150-198">Return type is a contract.</span></span> <span data-ttu-id="7e150-199">Dönüş değeri beklenen türe dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="7e150-199">The return value is converted to the expected type.</span></span> <span data-ttu-id="7e150-200">Dönüş türü belirtilirse, dönüş türü olan **void**.</span><span class="sxs-lookup"><span data-stu-id="7e150-200">If no return type is specified, the return type is **void**.</span></span> <span data-ttu-id="7e150-201">Hiçbir akış nesneleri yoktur.</span><span class="sxs-lookup"><span data-stu-id="7e150-201">There is no streaming of objects.</span></span> <span data-ttu-id="7e150-202">Nesneleri işlem hattının yanlışlıkla veya kasıtlı olarak yazılamaz.</span><span class="sxs-lookup"><span data-stu-id="7e150-202">Objects cannot be written to the pipeline either intentionally or by accident.</span></span>

### <a name="attributes"></a><span data-ttu-id="7e150-203">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7e150-203">Attributes</span></span>

<span data-ttu-id="7e150-204">İki yeni öznitelikler **DscResource** ve **DscProperty** sürümüne eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="7e150-204">Two new attributes, **DscResource** and **DscProperty** have been added.</span></span>

### <a name="lexical-scoping-of-variables"></a><span data-ttu-id="7e150-205">Sözcük değişkenlerinin kapsamı</span><span class="sxs-lookup"><span data-stu-id="7e150-205">Lexical scoping of variables</span></span>

<span data-ttu-id="7e150-206">Aşağıdaki örnek nasıl sözcük kapsam works'ün bu sürümde gösterir.</span><span class="sxs-lookup"><span data-stu-id="7e150-206">The following shows an example of how lexical scoping works in this release.</span></span>

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

## <a name="end-to-end-example"></a><span data-ttu-id="7e150-207">Uçtan uca örneği</span><span class="sxs-lookup"><span data-stu-id="7e150-207">End-to-End Example</span></span>

<span data-ttu-id="7e150-208">Aşağıdaki örnek, bir HTML dinamik stil sayfası dil (DSL) uygulamak için bazı özel sınıflar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7e150-208">The following example creates some custom classes to implement an HTML dynamic style sheet language (DSL).</span></span> <span data-ttu-id="7e150-209">Ardından, türleri, bir modül kapsamı dışında kullanılamaz çünkü örnek kapsamında başlığının stilleri ve tablolar gibi bir öğe sınıfı belirli bir öğe türleri oluşturmak için yardımcı işlevleri ekler.</span><span class="sxs-lookup"><span data-stu-id="7e150-209">Then, the example adds helper functions to create specific element types as part of the element class, such as heading styles and tables, because types cannot be used outside the scope of a module.</span></span>

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
# These are required because types aren't visible outside of the module.
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
