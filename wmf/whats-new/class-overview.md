---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: PowerShell Sınıfları Kullanarak Özel Türler Oluşturma
ms.openlocfilehash: 0dd5bbaca50abb746e15a7bb64a706c7eceee905
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856241"
---
# <a name="creating-custom-types-using-powershell-classes"></a>PowerShell Sınıfları Kullanarak Özel Türler Oluşturma

PowerShell 5.0, sınıflar ve resmi sözdizimi ve semantiği gibi diğer nesne yönelimli programlama dillerini kullanarak kullanıcı tanımlı türler diğer tanımlama olanağı eklendi. Geliştiriciler ve BT uzmanları geniş bir kullanım için PowerShell Kucak, PowerShell yapıtları (örneğin, DSC kaynakları) geliştirilmesini basitleştirin ve yönetim yüzeyleri kapsamını hızlandırmanız, hedef etkinleştirmektir.

## <a name="supported-scenarios-in-this-release"></a>Bu sürümde desteklenen senaryolar

- PowerShell dilini kullanarak DSC kaynakları ve ilişkili türlerini tanımlayın
- Bilinen nesne yönelimli programlama yapıları, sınıflar, özellikler, yöntemler vb. gibi kullanarak PowerShell'de özel türleri tanımla
- PowerShell ve sınıf temel DSC kaynak sınıfıyla devralma desteği
- PowerShell dilini kullanarak türlerinde hata ayıklama
- Oluşturma ve resmi mekanizmalarını kullanarak ve doğru düzeyde özel durumları işleme

# <a name="declare-base-class"></a>Temel Sınıf Bildirme

Bir PowerShell sınıfı, başka bir PowerShell sınıfı için bir temel tür olarak bildirebilirsiniz.

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

Temel sınıf olarak var olan .NET Framework türleri de kullanabilirsiniz:

```powershell
class MyIntList : system.collections.generic.list[int]
{

}

$list = [MyIntList]::new()

$list.Add(100)

$list[0] # return 100
```

# <a name="call-base-class-constructor"></a>Temel Sınıf Oluşturucusunu Çağırma

Bir temel sınıf oluşturucusunu bir alt sınıfı için anahtar sözcüğünü kullanın **temel**:

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

Bir temel sınıf (parametre) varsayılan bir oluşturucusu varsa, bir açık oluşturucu çağrısı atlayabilirsiniz:

```powershell
class C : B
{
    C([int]$c) {}
}
```

# <a name="call-base-class-method"></a>Temel Sınıf Yöntemini Çağırma

Alt sınıfların mevcut yöntemleri geçersiz kılabilirsiniz. Bunu yapmak için aynı ada ve imzaya kullanarak yöntemleri bildirin:

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

Geçersiz kılınan uygulamaları taban sınıf yöntemlerini çağırmak için temel sınıf için atama (`[baseClass]$this`) çağırma üzerinde:

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

Tüm PowerShell yöntemler sanaldır. Aynı ada ve imzaya sahip yöntemleri bildirerek bir geçersiz kılma için yaptığınız gibi aynı sözdizimini kullanarak bir alt sanal olmayan .NET yöntemleri gizleyebilirsiniz.

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

# <a name="declare-implemented-interface"></a>Uygulanan Arabirimi Bildirme

Belirtilen hiçbir temel türü varsa temel türleri bir iki nokta üst üste (:) hemen sonra veya uygulanan arabirimleri bildirebilirsiniz. Tüm tür adları virgül kullanarak ayırın. Benzer C# söz dizimi.

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

# <a name="new-language-features-in-powershell-50"></a>PowerShell 5.0 yeni dil özellikleri

PowerShell 5.0, PowerShell aşağıdaki yeni dil öğelerini sunar:

## <a name="class-keyword"></a>Class anahtar sözcüğü

`class` Anahtar sözcüğü, yeni bir sınıf tanımlar. Gerçek bir .NET Framework türü budur. Sınıf üyelerine genel, ancak yalnızca ortak modülü kapsamında değildir. Tür adı bir dize olarak başvurulamaz (örneğin, `New-Object` çalışmıyor), ve bu sürümde, bir tür sabit değer kullanamazsınız (örneğin, `[MyClass]`) sınıfı tanımlanır komut veya modül dosyasının dışında.

```powershell
class MyClass
{
    ...
}
```

## <a name="enum-keyword-and-enumerations"></a>Enum anahtar sözcüğü ve numaralandırmalar

Destek `enum` anahtar sözcüğü eklendi, yeni satır ayırıcı olarak kullanır. Şu anda bir numaralandırıcı kendisi açısından tanımlayamazsınız. Ancak, aşağıdaki örnekte gösterildiği gibi başka bir sabit listesi açısından enum başlatabilirsiniz. Ayrıca, temel türü belirtilemez; her zaman `[int]`.

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

Numaralandırıcı değeri ayrıştırma zamanı sabiti olmalıdır. Çağrılan bir komutun sonucuna ayarlanamaz.

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

Numaralandırmalar, aşağıdaki örnekte gösterildiği gibi aritmetik işlemleri destekler.

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

## <a name="import-dscresource"></a>Import-DscResource

`Import-DscResource` true dinamik bir anahtar sözcüğü sunulmuştur. PowerShell içeren sınıflar için arama belirtilen modülün kök modül ayrıştırır **DscResource** özniteliği.

## <a name="implementingassembly"></a>ImplementingAssembly

Yeni bir alan **ImplementingAssembly**, eklenmiş **ModuleInfo**. Sınıflar komut dosyasını tanımlayan bir betik modülü için oluşturulan dinamik derlemenin veya ikili modülleri için yüklü bütünleştirilmiş kodu için ayarlanır. Ne zaman ayarlanmadı **ModuleType** olduğu **bildirim**.

Yansıma **ImplementingAssembly** alan Modül içindeki kaynakları bulur. Başka bir deyişle, PowerShell veya başka yönetilen dillerde yazılmış kaynakları bulabilir.

Başlatıcıları olan alanlar:

```powershell
[int] $i = 5
```

`Static` desteklenir. Tür kısıtlamaları gibi bir öznitelik gibi çalışır. Herhangi bir sırada belirtilebilir.

```powershell
static [int] $count = 0
```

Bir tür isteğe bağlıdır.

```powershell
$s = "hello"
```

Tüm üyeleri ortaktır.

## <a name="constructors-and-instantiation"></a>Oluşturucular ve örnek oluşturma

PowerShell sınıflarını oluşturuculara sahip olabilir. Bunlar, sınıfı aynı ada sahip. Oluşturucu aşırı yüklenebilir. Statik oluşturucularda desteklenir. Başlatma ifadeleri özellikleriyle herhangi bir kod Oluşturucu çalıştırılmadan önce başlatılır. Statik özellikler statik Oluşturucu gövdesinde önce başlatılır ve örnek özelliklerini statik olmayan Oluşturucu gövdesinde önce başlatılır. Şu anda başka bir oluşturucudan bir oluşturucu çağırmak için hiçbir sözdizimi yoktur (ister C\# söz dizimi ": this()"). Geçici çözüm, ortak bir tanımlamaktır `Init()` yöntemi.

### <a name="creating-instances"></a>Örnekler oluşturma

> [!NOTE]
> PowerShell 5.0 `New-Object` PowerShell içinde tanımlanan sınıflar ile çalışmıyor. Ayrıca, tür adı yalnızca sözcüksel olarak, modül veya sınıf tanımlar betik dışında görünür olmadığı anlamına gelir görülebilir. İşlevler, PowerShell içinde tanımlanmış bir sınıfın örnekleri döndürebilir. Bu örnekler, modül veya betik dışında çalışır.

1. Varsayılan oluşturucu kullanılarak örnekleme.

   ```powershell
   $a = [MyClass]::new()
   ```

1. Bir parametresi olan yapılandırıcının

   ```powershell
   $b = [MyClass]::new(42)
   ```

1. Birden çok parametre ile bir oluşturucu için bir dizi geçirme.

   ```powershell
   $c = [MyClass]::new(@(42,43,44), "Hello")
   ```

Sözde statik yöntem `new()` aşağıdaki örnekte gösterildiği gibi .NET türleri ile çalışır.

```powershell
[hashtable]::new()
```

### <a name="discovering-constructors"></a>Oluşturucular keşfetme

Oluşturucu aşırı yüklemeleri ile artık gördüğünüz `Get-Member`, veya bu örnekte gösterildiği gibi:

```powershell
PS> [hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

`Get-Member -Static` gibi başka bir yöntem aşırı yüklemeleri görebilecek şekilde oluşturucuları listeler. Bu söz dizimi performansını da önemli ölçüde daha hızlı bir şekilde `New-Object`.

## <a name="methods"></a>Yöntemler

Bir PowerShell sınıfı yöntemi olarak uygulanan bir **ScriptBlock** olan yalnızca bir sonlandırma bloğu. Tüm yöntemleri herkese açık. Aşağıdaki adlı bir yöntemi tanımlayan bir örnek gösterilmektedir **DoSomething**.

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

Yöntem çağırma:

```powershell
$b = [MyClass]::new()
$b.DoSomething(42)
```

Aşırı yüklenmiş yöntemler de desteklenir.

## <a name="properties"></a>Özellikler

Tüm özellikleri ortaktır. Noktalı virgül veya yeni satır özellikleri gerektirir. Hiçbir nesne türü belirtilirse, özellik türü nesnedir.

Doğrulama veya bağımsız değişken dönüşümü öznitelikleri özellikleri (gibi `[ValidateSet("aaa")]`) beklendiği gibi çalışmayabilir.

## <a name="hidden"></a>Hidden

Yeni bir anahtar sözcük `Hidden`, eklendi. `Hidden` Özellikler ve yöntemler (oluşturucular dahil) için uygulanabilir.

Gizli üyeleri ortaktır, ancak çıktısında görünmez `Get-Member` sürece Force parametresi eklendi. Gizli üyeleri ne zaman dahil edilmez tamamlayarak veya gizli üye tanımlama sınıfında tamamlama gerçekleşmediği sürece IntelliSense kullanarak sekmesi.

Yeni bir öznitelik **System.Management.Automation.HiddenAttribute** bunu eklendi, C\# kod içinde PowerShell ile aynı semantiğe sahip olabilir.

## <a name="return-types"></a>Dönüş türleri

Dönüş türü bir sözleşmedir. Dönüş değeri beklenen türe dönüştürülür. Dönüş türü belirtilirse, dönüş türü olan **void**. Hiçbir akış nesneleri yoktur. Bbjects ardışık düzene yanlışlıkla veya kasıtlı olarak yazılamaz.

## <a name="attributes"></a>Öznitelikler

İki yeni öznitelikler **DscResource** ve **DscProperty** sürümüne eklenmiştir.

## <a name="lexical-scoping-of-variables"></a>Sözcük değişkenlerinin kapsamı

Aşağıdaki örnek nasıl sözcük kapsam works'ün bu sürümde gösterir.

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

## <a name="end-to-end-example"></a>Uçtan uca örneği

Aşağıdaki örnek, bir HTML dinamik stil sayfası dil (DSL) uygulamak için bazı özel sınıflar oluşturur. Ardından, türleri, bir modül kapsamı dışında kullanılamaz çünkü örnek kapsamında başlığının stilleri ve tablolar gibi bir öğe sınıfı belirli bir öğe türleri oluşturmak için yardımcı işlevleri ekler.

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
