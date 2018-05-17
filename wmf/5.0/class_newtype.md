---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 9aa7e92632c671751020687ddbfc374eeda7148b
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
---
# <a name="new-language-features-in-powershell-50"></a>PowerShell 5.0 içindeki yeni dil özellikleri

PowerShell 5.0, Windows PowerShell içinde aşağıdaki yeni dil öğeleri sunar:

## <a name="class-keyword"></a>Class anahtar sözcüğü

**Sınıfı** anahtar sözcüğü yeni bir sınıf tanımlar. True .NET Framework türü budur.
Sınıf üyeleri ortak, ancak yalnızca genel modülü kapsam içinde.
Tür adı bir dize olarak başvuramaz (örneğin, `New-Object` çalışmıyor), ve bu sürümde, bir tür değişmez değeri kullanamazsınız (örneğin, `[MyClass]`) sınıf tanımlanır komut dosyası/modül dosyası dışında.

```powershell
class MyClass
{
    ...
}
```

## <a name="enum-keyword-and-enumerations"></a>Enum anahtar sözcüğü ve numaralandırmalar

Desteği **enum** anahtar sözcüğü eklendi, yeni satır ayırıcı olarak kullanır.
Geçerli sınırlamalar: kendisi açısından bir numaralandırıcı tanımlayamazsınız, ancak aşağıdaki örnekte gösterildiği gibi bir numaralandırma başka bir enum bakımından başlatabilirsiniz.
Ayrıca, şu anda temel türü belirtilemez; her zaman [int].

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

Bir numaralandırıcı ayrıştırma zamanı sabiti olmalıdır; çağrılan komut sonucuna ayarlanamıyor.

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

Aşağıdaki örnekte gösterildiği gibi numaralandırmalar aritmetik işlemler destekler.

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

## <a name="import-dscresource"></a>İçeri aktarma DscResource

**İçeri aktarma DscResource** true dinamik anahtar sözcüğü sunulmuştur.
PowerShell içeren sınıfları aranıyor belirtilen modülünün kök modül ayrıştırır **DscResource** özniteliği.

## <a name="implementingassembly"></a>ImplementingAssembly

Yeni bir alan **ImplementingAssembly**, ModuleInfo için eklendi. Komut dosyası sınıfları tanımlıyorsa bir betik modülü için oluşturulan dinamik derleme ya da ikili modülleri için yüklenen derleme ayarlanır. Ne zaman ayarlanmadı ModuleType bildirimi =.

Yansıma **ImplementingAssembly** alan bir modüldeki kaynakları bulur. Başka bir deyişle, PowerShell veya diğer yönetilen dilleri ile yazılmış kaynakları bulabilir.

Başlatıcılar alanlarla:

```powershell
[int] $i = 5
```

Statik desteklenir; herhangi bir sırada belirtilen tür kısıtlamaları bunun gibi bir öznitelik gibi çalışır.

```powershell
static [int] $count = 0
```

Bir isteğe bağlı türüdür.

```powershell
$s = "hello"
```

Tüm ortak üyeleridir.

## <a name="constructors-and-instantiation"></a>Oluşturucular ve örnek oluşturma

Windows PowerShell sınıfları oluşturucular olabilir; Bunlar kendi sınıf ile aynı ada sahip. Oluşturucular aşırı yüklenmiş. Statik oluşturucular desteklenir. Başlatma ifadeleri özelliklerle herhangi bir kod oluşturucu içinde çalıştırılmadan önce başlatılır. Statik özellikler statik oluşturucu gövdesi önce başlatılır ve örnek özelliklerini statik olmayan Oluşturucusu gövde önce başlatılır. Şu anda başka bir oluşturucudan bir oluşturucu çağırmak için hiçbir sözdizimi yoktur (ister C\# sözdizimi ": this()"). Bir ortak Init yöntemi tanımlamak için geçici bir çözüm değildir.

Bu sürümde başlatmasını sınıfların yollar şunlardır.

Varsayılan Oluşturucu kullanarak örnekleme. Yeni nesne bu sürümde desteklenmiyor unutmayın.

```powershell
$a = [MyClass]::new()
```

Bir parametre ile bir oluşturucu çağırma

```powershell
$b = [MyClass]::new(42)
```

Birden çok parametre ile bir oluşturucu için bir dizi geçirme
```powershell
$c = [MyClass]::new(@(42,43,44), "Hello")
```

Bu sürümde, Windows PowerShell içinde tanımlanan sınıflar ile New-Object çalışmaz. Ayrıca bu sürüm için tür adı yalnızca sözcüksel olarak, modül veya sınıfı tanımlayan betik dışında görünür değil anlamı görünür olur. İşlevler Windows PowerShell içinde tanımlı bir sınıfın örneklerini döndürebilir ve iyi modül veya komut dosyası dışında çalışma örnekleri.

`Get-Member -Static` başka bir yöntem gibi aşırı görüntüleyebilmeniz Oluşturucular, listeler. Bu sözdiziminin performansını da New-Object önemli ölçüde daha hızlıdır.

Adlı sözde statik yöntemi **yeni** aşağıdaki örnekte gösterildiği gibi .NET türleri ile çalışır.

```powershell
[hashtable]::new()
```

Şimdi Oluşturucusu aşırı Get üyeyle ya da bu örnekte gösterildiği gibi görebilirsiniz:

```powershell
PS> [hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

## <a name="methods"></a>Yöntemler

Bir Windows PowerShell sınıf yöntemi yalnızca bir sonlandırma bloğu sahip bir ScriptBlock uygulanır. Tüm yöntemleri ortak. Adlı bir yöntem tanımlama örneği aşağıdaki gösterir **DoSomething**.

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

Aşırı yüklenmiş yöntemler, varolan bir yöntemi ile aynı adlı ancak belirtilen değerlerine göre--Ayrıştırılan de başka bir deyişle, desteklenir.

## <a name="properties"></a>Özellikler

Tüm ortak özelliklerdir. Bir satır başı karakteri veya noktalı virgül özellikleri gerektirir. Hiçbir nesne türü belirtilirse, özellik türü nesnesidir.

Doğrulama öznitelikleri veya bağımsız değişken dönüşümü kullanmak özellikleri (örn. `[ValidateSet("aaa")]`) beklendiği gibi çalışmayabilir.

## <a name="hidden"></a>Gizli

Yeni bir anahtar sözcük **gizli**, eklendi. **Gizli** özellikleri ve yöntemleri (oluşturucular dahil) için uygulanabilir.

Gizli üyeleri ortaktır, ancak Get-üye çıktısında sürece görünmez Force parametresini eklenir.

Gizli üyeleri ne zaman dahil edilmez tamamlayarak veya IntelliSense tamamlanma gizli üye tanımlama sınıfında oluşmadığı sürece kullanarak sekmesinde.

Yeni bir öznitelik **System.Management.Automation.HiddenAttribute** C# kodu Windows PowerShell içinde aynı semantiğini böylece eklendi.

## <a name="return-types"></a>Dönüş türleri

Dönüş türü bir sözleşmedir; dönüş değeri, beklenen türe dönüştürülür. Dönüş türü belirtilmişse, dönüş türü void alır. Hiçbir nesnelerin akış yoktur; nesneleri ardışık düzene kasıtlı olarak veya yanlışlıkla tarafından yazılamaz.

## <a name="attributes"></a>Öznitelikler

İki yeni öznitelikler **DscResource** ve **DscProperty** eklenmiştir.

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

## <a name="end-to-end-example"></a>Uçtan uca örnek

Aşağıdaki örnek, bir HTML dinamik bir stil sayfası dili (DSL) uygulamak için birkaç yeni, özel sınıfları oluşturur.
Ardından, türleri bir modül kapsamı dışında kullanıldığından örnek başlık stilleri ve tabloları gibi öğe sınıfının bir parçası olarak belirli öğe türleri oluşturmak için yardımcı işlevleri ekler.

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
