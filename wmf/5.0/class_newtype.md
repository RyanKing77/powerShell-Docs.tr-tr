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
# <a name="new-language-features-in-powershell-50"></a>PowerShell 5.0 yeni dil özellikleri

PowerShell 5.0, Windows PowerShell içinde aşağıdaki yeni dil öğelerini sunar:

## <a name="class-keyword"></a>Class anahtar sözcüğü

**Sınıfı** anahtar sözcüğü, yeni bir sınıf tanımlar. Gerçek bir .NET Framework türü budur.
Sınıf üyelerine genel, ancak yalnızca ortak modülü kapsamında değildir.
Tür adı bir dize olarak başvurulamaz (örneğin, `New-Object` çalışmıyor), ve bu sürümde, bir tür sabit değer kullanamazsınız (örneğin, `[MyClass]`) sınıfı tanımlanır betik/modülü dosyanın dışında.

```powershell
class MyClass
{
    ...
}
```

## <a name="enum-keyword-and-enumerations"></a>Enum anahtar sözcüğü ve numaralandırmalar

Destek **enum** anahtar sözcüğü eklendi, yeni satır ayırıcı olarak kullanır.
Geçerli sınırlamalar: bir numaralandırıcı kendisi açısından tanımlayamazsınız ancak aşağıdaki örnekte gösterildiği gibi başka bir sabit listesi açısından enum başlatabilirsiniz.
Ayrıca, şu anda temel türü belirtilemez; her zaman [int].

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

Numaralandırıcı değeri ayrıştırma zamanı sabiti olmalıdır; çağrılan bir komutun sonucuna ayarlanamaz.

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

**Import-DscResource** true dinamik bir anahtar sözcüğü sunulmuştur.
PowerShell içeren sınıflar için arama belirtilen modülün kök modül ayrıştırır **DscResource** özniteliği.

## <a name="implementingassembly"></a>ImplementingAssembly

Yeni bir alan **ImplementingAssembly**, ModuleInfo için eklendi. Sınıflar komut dosyasını tanımlayan bir betik modülü için oluşturulan dinamik derlemenin veya ikili modülleri için yüklü bütünleştirilmiş kodu için ayarlanır. Ne zaman ayarlanmadı ModuleType bildirimi =.

Yansıma **ImplementingAssembly** alan Modül içindeki kaynakları bulur. Başka bir deyişle, PowerShell veya başka yönetilen dillerde yazılmış kaynakları bulabilir.

Başlatıcıları olan alanlar:

```powershell
[int] $i = 5
```

Statik desteklenir. herhangi bir sırada belirtilen tür kısıtlamaları bunun gibi bir öznitelik gibi çalışır.

```powershell
static [int] $count = 0
```

Bir tür isteğe bağlıdır.

```powershell
$s = "hello"
```

Tüm üyeleri ortaktır.

## <a name="constructors-and-instantiation"></a>Oluşturucular ve örnek oluşturma

Windows PowerShell sınıflarını oluşturucuları olabilir; Bunlar, sınıfı aynı ada sahip. Oluşturucu aşırı yüklenebilir. Statik oluşturucularda desteklenir. Başlatma ifadeleri özellikleriyle herhangi bir kod Oluşturucu çalıştırılmadan önce başlatılır. Statik özellikler statik Oluşturucu gövdesinde önce başlatılır ve örnek özelliklerini statik olmayan Oluşturucu gövdesinde önce başlatılır. Şu anda başka bir oluşturucudan bir oluşturucu çağırmak için hiçbir sözdizimi yoktur (ister C\# söz dizimi ": this()"). Geçici çözüm, ortak bir Init yöntemi tanımlamaktır.

Bu sürümde örnekleme sınıflarının yolları aşağıda verilmiştir.

Varsayılan oluşturucu kullanılarak örnekleme. New-Object bu sürümde desteklenmediğini unutmayın.

```powershell
$a = [MyClass]::new()
```

Bir parametresi olan yapılandırıcının

```powershell
$b = [MyClass]::new(42)
```

Birden çok parametre ile bir oluşturucu için bir dizi geçirme
```powershell
$c = [MyClass]::new(@(42,43,44), "Hello")
```

Bu sürümde, Windows PowerShell içinde tanımlanan sınıflar ile New-Object çalışmaz. Ayrıca bu sürüm için tür adı yalnızca sözcüksel olarak, modül veya sınıf tanımlar betik dışında görünür olmadığı anlamına gelir görülebilir. İşlevler Windows PowerShell içinde tanımlanmış bir sınıfın örnekleri döndürebilir ve örnekleri de modül veya betik dışında çalışır.

`Get-Member -Static` gibi başka bir yöntem aşırı yüklemeleri görebilecek şekilde oluşturucuları listeler. Bu söz dizimi performansını da New-Object önemli ölçüde daha hızlıdır.

Adlı sözde statik yöntem **yeni** aşağıdaki örnekte gösterildiği gibi .NET türleri ile çalışır.

```powershell
[hashtable]::new()
```

Get-Member veya bu örnekte gösterildiği gibi oluşturucu aşırı yüklemeleri artık görebilirsiniz:

```powershell
PS> [hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

## <a name="methods"></a>Yöntemler

Bir Windows PowerShell sınıfı yöntemi yalnızca bir sonlandırma bloğu sahip bir ScriptBlock gerçekleştirilir. Tüm yöntemleri herkese açık. Aşağıdaki adlı bir yöntemi tanımlayan bir örnek gösterilmektedir **DoSomething**.

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

Aşırı yüklenmiş yöntemler varolan bir yöntem ile aynı adlı ancak bunların belirtilen değerleri--Ayrıştırılan o da diğer bir deyişle, desteklenir.

## <a name="properties"></a>Özellikler

Tüm özellikleri ortaktır. Noktalı virgül veya yeni satır özellikleri gerektirir. Hiçbir nesne türü belirtilirse, özellik türü nesnedir.

Doğrulama öznitelikleri veya bağımsız değişken dönüşümü kullanan özellikler (örneğin `[ValidateSet("aaa")]`) beklendiği gibi çalışmayabilir.

## <a name="hidden"></a>Gizli

Yeni bir anahtar sözcük **gizli**, eklendi. **Gizli** özelliklere ve yöntemlere (oluşturucular dahil) için uygulanabilir.

Gizli üyeleri ortaktır, ancak Get-Member çıktısında sürece görünmez Force parametresi eklendi.

Gizli üyeleri ne zaman dahil edilmez tamamlayarak veya gizli üye tanımlama sınıfında tamamlama gerçekleşmediği sürece IntelliSense kullanarak sekmesi.

Yeni bir öznitelik **System.Management.Automation.HiddenAttribute** C# kod içinde Windows PowerShell ile aynı semantiğe sahip olabilir, böylece eklendi.

## <a name="return-types"></a>Dönüş türleri

Dönüş türü bir sözleşmedir; dönüş değeri beklenen türe dönüştürülür. Dönüş türü belirtilirse, dönüş türü void. Akış yok nesnelerin yoktur; nesneleri işlem hattının yanlışlıkla veya kasıtlı olarak yazılamaz.

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

Aşağıdaki örnek, bir HTML dinamik stil sayfası dil (DSL) uygulamak için birçok yeni, özel sınıf oluşturur.
Ardından, türleri, bir modül kapsamı dışında kullanılamaz çünkü örnek kapsamında başlığının stilleri ve tablolar gibi bir öğe sınıfı belirli bir öğe türleri oluşturmak için yardımcı işlevleri ekler.

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
