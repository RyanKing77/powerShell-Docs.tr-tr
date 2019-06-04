---
ms.date: 03/18/2019
title: FilterHashtable ile Get-WinEvent sorguları oluşturma
ms.openlocfilehash: 2f598fceb570f189bee776b6ed572b11a6938f64
ms.sourcegitcommit: bc42c9166857147a1ecf9924b718d4a48eb901e3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/03/2019
ms.locfileid: "66471021"
---
# <a name="creating-get-winevent-queries-with-filterhashtable"></a>FilterHashtable ile Get-WinEvent sorguları oluşturma

Özgün Haziran 3 2014 okunacak **Scripting Guy** post, blog gönderimize [kullanım FilterHashTable PowerShell ile filtre olay günlüğü için](https://devblogs.microsoft.com/scripting/use-filterhashtable-to-filter-event-log-with-powershell/).

Bu makalede bir alıntı özgün blog gönderisinin olduğu ve nasıl kullanılacağını açıklar `Get-WinEvent` cmdlet'in **FilterHashtable** olay günlüklerini filtrelemek için parametre. PowerShell'in `Get-WinEvent` cmdlet'tir Windows olay ve tanılama günlüklerini filtrelemek için güçlü bir yöntem. Performansı artıran bir `Get-WinEvent` sorgu kullandığı **FilterHashtable** parametresi.

Büyük olay günlükleri ile çalışırken, bu işlem hattına aşağı nesneleri göndermek için etkin değil bir `Where-Object` komutu. PowerShell 6'da önce `Get-EventLog` cmdlet'i olan günlük verilerini almak için başka bir seçenek. Örneğin, aşağıdaki komutları için filtre verimsiz **Microsoft-Windows-birleştirme** günlükleri:

`Get-EventLog -LogName Application | Where-Object Source -Match defrag`

`Get-WinEvent -LogName Application | Where-Object { $_.ProviderName -Match 'defrag' }`

Aşağıdaki komut, performansı geliştiren bir karma tablo kullanır:

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='*defrag'
}
```

## <a name="blog-posts-about-enumeration"></a>Blog gönderileri numaralandırması

Bu makalede, numaralandırılmış değerlerin bir karma tablosunda kullanma hakkında bilgi gösterir. Bu sabit listesi hakkında daha fazla bilgi için okuma **Scripting Guy** blog gönderilerimize göz atın. Numaralandırılmış değerler döndüren bir işlev oluşturmak için bkz [sabit listeleri ve değerleri](https://devblogs.microsoft.com/scripting/hey-scripting-guy-weekend-scripter-enumerations-and-values).
Daha fazla bilgi için [Scripting Guy dizi blog yazılarını numaralandırma hakkında](https://devblogs.microsoft.com/scripting/?s=about+enumeration).

## <a name="hash-table-keyvalue-pairs"></a>Karma tablo anahtar/değer çiftleri

Verimli sorgular derlemek için kullanma `Get-WinEvent` cmdlet'iyle **FilterHashtable** parametresi.
**FilterHashtable** karma tablo belirli bilgileri Windows olay günlüklerini almak için bir filtre olarak kabul eder. Bir karma tablo kullandığı **anahtar/değer** çiftleri. Karma tabloları hakkında daha fazla bilgi için bkz. [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables).

Varsa **anahtar/değer** çiftleridir aynı satırda, noktalı virgülle ayrılmalıdır. Her varsa **anahtar/değer** çifti ayrı bir satırda, noktalı virgül gerekmez. Örneğin, bu makalede yerleştirir **anahtar/değer** çiftlerini ayrı satırlarda ve noktalı kullanmaz.

Bu örnek, birkaç kullanmaktadır **FilterHashtable** parametrenin **anahtar/değer** çiftleri. Tamamlanan sorgu içeren **günlükadı**, **ProviderName**, **anahtar sözcükleri**, **kimliği**, ve **düzeyi**.

Kabul edilen **anahtar/değer** çiftleri aşağıdaki tabloda gösterilen ve belgeler için dahil edilen [Get-WinEvent](/powershell/module/microsoft.powershell.diagnostics/Get-WinEvent)
**FilterHashtable** parametre.

Aşağıdaki tabloda, anahtar adları, veri türleri görüntüler ve joker karakterler için veri değeri olup olmadığı kabul edilir.

| Anahtar adı     | Değer veri türü    | Joker karakterler kabul ediyor mu? |
|------------- | ------------------ | ---------------------------- |
| Günlükadı      | `<String[]>`       | Evet |
| ProviderName | `<String[]>`       | Evet |
| Yol         | `<String[]>`       | Hayır  |
| Anahtar Sözcükler     | `<Long[]>`         | Hayır  |
| ID           | `<Int32[]>`        | Hayır  |
| Düzey        | `<Int32[]>`        | Hayır  |
| startTime    | `<DateTime>`       | Hayır  |
| EndTime      | `<DateTime>`       | Hayır  |
| Kullanıcı Kimliği       | `<SID>`            | Hayır  |
| Veriler         | `<String[]>`       | Hayır  |
| *            | `<String[]>`       | Hayır  |

## <a name="building-a-query-with-a-hash-table"></a>Bir karma tablo içeren bir sorgu oluşturma

Sonuçları doğrulamak ve sorunları gidermek için karma tablosu oluşturmak için Yardım ettiği **anahtar/değer** birer birer çifti. Verilerden sorguyu alır **uygulama** günlük. Karma tablo eşdeğerdir `Get-WinEvent –LogName Application`.

Başlamak için oluşturmanız `Get-WinEvent` sorgu. Kullanım **FilterHashtable** parametrenin **anahtar/değer** pair anahtarla **günlükadı**, değeri **uygulama**.

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
}
```

İle karma tablo oluşturmaya devam **ProviderName** anahtarı. **ProviderName** görünen adı **kaynak** alanındaki **Windows Olay Görüntüleyicisi'ni**. Örneğin, **.NET çalışma zamanı** aşağıdaki ekran görüntüsünde:

![Windows Olay Görüntüleyicisi'ni kaynakları görüntüsü.](./media/creating-get-winEvent-queries-with-filterhashtable/providername.png)

Karma tablo güncelleştirin ve dahil **anahtar/değer** pair anahtarla ** ProviderName, değeri **.NET çalışma zamanı**.

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
}
```

Sorgunuzu arşivlenen olay günlüklerinden veri almak gerekiyorsa kullanın **yolu** anahtarı. **Yolu** değeri günlük dosyasının tam yolunu belirtir. Daha fazla bilgi için **Scripting Guy** blog gönderisi [PowerShell kullanarak için ayrıştırma kaydedilen hataları için olay günlüklerini](https://devblogs.microsoft.com/scripting/use-powershell-to-parse-saved-event-logs-for-errors).

## <a name="using-enumerated-values-in-a-hash-table"></a>Bir karma tabloda listelenmiş değerler kullanarak

**Anahtar sözcükler** karma tablosundaki sonraki anahtardır. **Anahtar sözcükleri** veri türü olan bir dizi `[long]` değeri tutan çok sayıda türüdür. En büyük değerini bulmak için aşağıdaki komutu kullanın `[long]`:

```powershell
[long]::MaxValue
```

```Output
9223372036854775807
```

İçin **anahtar sözcükleri** anahtar, PowerShell, bir dize olmak üzere bir sayı gibi kullanan **güvenlik**. **Windows Olay Görüntüleyicisi'ni** görüntüler **anahtar sözcükleri** olarak dizeler, ancak bunlar numaralandırılmış değerlerdir. Kullanırsanız karma tablosundaki **anahtar sözcükleri** anahtar bir dize değeri ile bir hata iletisi görüntülenir.

Açık **Windows Olay Görüntüleyicisi'ni** ve **eylemleri** bölmesinde, tıklayarak **geçerli günlüğü Filtrele**.
**Anahtar sözcükleri** aşağıdaki ekran görüntüsünde gösterildiği gibi açılan menü görüntüler kullanılabilir anahtar sözcükler:

![Windows Olay Görüntüleyicisi'ni anahtar sözcükleri görüntüsü.](./media/creating-get-winEvent-queries-with-filterhashtable/keywords.png)

Görüntülemek için aşağıdaki komutu kullanın `StandardEventKeywords` özellik adları.

```powershell
[System.Diagnostics.Eventing.Reader.StandardEventKeywords] | Get-Member -Static -MemberType Property
```

```Output
   TypeName: System.Diagnostics.Eventing.Reader.StandardEventKeywords
Name             MemberType Definition
—-             ———- ———-
AuditFailure     Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
AuditSuccess     Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
CorrelationHint  Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
CorrelationHint2 Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
EventLogClassic  Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
None             Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
ResponseTime     Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
Sqm              Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
WdiContext       Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
WdiDiagnostic    Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
```

Numaralandırılmış değerler bölümünde belgelendirilen **.NET Framework**. Daha fazla bilgi için [StandardEventKeywords numaralandırma](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventkeywords?redirectedfrom=MSDN&view=netframework-4.7.2).

**Anahtar sözcükleri** adları ve listelenmiş değerler aşağıdaki gibidir:

| Adı             |  Değer            |
| ---------------- | ------------------|
| AuditFailure     | 4503599627370496  |
| AuditSuccess     | 9007199254740992  |
| CorrelationHint2 | 18014398509481984 |
| EventLogClassic  | 36028797018963968 |
| SQM              | 2251799813685248  |
| WdiDiagnostic    | 1125899906842624  |
| WdiContext       | 562949953421312   |
| Yanıt süresi     | 281474976710656   |
| Yok             | 0                 |

Karma tablo güncelleştirin ve dahil **anahtar/değer** pair anahtarla **anahtar sözcükleri**ve **EventLogClassic** numaralandırma değeri **36028797018963968** .

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
}
```

### <a name="keywords-static-property-value-optional"></a>Anahtar sözcükler statik özellik değeri (isteğe bağlı)

**Anahtar sözcükleri** anahtar listelenmiş, ancak statik özellik adı karma tablo sorgusu kullanabilirsiniz.
Döndürülen dize kullanmak yerine, özellik adı ile bir değere dönüştürülmelidir **Value__** özelliği.

Örneğin, aşağıdaki kullanan betik **Value__** özelliği.

```powershell
$C = [System.Diagnostics.Eventing.Reader.StandardEventKeywords]::EventLogClassic
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=$C.Value__
}
```

## <a name="filtering-by-event-id"></a>Olay kimliğine göre filtreleme

Daha belirli verileri almak için sorgu sonuçlarına göre filtrelenir **öğesini belirten Olay No.** . **Öğesini belirten Olay No.** karma tablo anahtarı olarak anılan **kimliği** ve belirli bir değerdir **öğesini belirten Olay No.** . **Windows Olay Görüntüleyicisi'ni** görüntüler **öğesini belirten Olay No.** . Bu örnekte **olay kimliği 1023**.

Karma tablo güncelleştirin ve dahil **anahtar/değer** pair anahtarla **kimliği** değeri **1023**.

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
}
```

## <a name="filtering-by-level"></a>Düzeye göre filtreleme

Daha ayrıntılı sonuçları daraltmak ve hataları olan olayları dahil için kullandığınız **düzeyi** anahtarı.
**Windows Olay Görüntüleyicisi'ni** görüntüler **düzeyi** gibi dize değerleri, ancak bunlar numaralandırılmış değerlerdir. Kullanırsanız karma tablosundaki **düzeyi** anahtar bir dize değeri ile bir hata iletisi görüntülenir.

**Düzey** değerleri gibi sahip **hata**, **uyarı**, veya **bilgilendirici**. Görüntülemek için aşağıdaki komutu kullanın `StandardEventLevel` özellik adları.

```powershell
[System.Diagnostics.Eventing.Reader.StandardEventLevel] | Get-Member -Static -MemberType Property
```

```Output
   TypeName: System.Diagnostics.Eventing.Reader.StandardEventLevel

Name          MemberType Definition
----          ---------- ----------
Critical      Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Critical {get;}
Error         Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Error {get;}
Informational Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Informational {get;}
LogAlways     Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel LogAlways {get;}
Verbose       Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Verbose {get;}
Warning       Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Warning {get;}
```

Numaralandırılmış değerler bölümünde belgelendirilen **.NET Framework**. Daha fazla bilgi için [StandardEventLevel numaralandırma](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventlevel?redirectedfrom=MSDN&view=netframework-4.7.2).

**Düzeyi** anahtarının adları ve listelenmiş değerler aşağıdaki gibidir:

| Adı           | Değer |
| -------------- | ----- |
| Verbose        |   5   |
| Bilgi  |   4   |
| Uyarı        |   3   |
| Hata          |   2   |
| Kritik       |   1   |
| LogAlways      |   0   |

Tamamlanan sorgu için karma tablo anahtarı içeren **düzeyi**, değeri **2**.

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
   Level=2
}
```

### <a name="level-static-property-in-enumeration-optional"></a>Sabit listesi (isteğe bağlı) statik özellik düzeyi

**Düzeyi** anahtar listelenmiş, ancak statik özellik adı karma tablo sorgusu kullanabilirsiniz.
Döndürülen dize kullanmak yerine, özellik adı ile bir değere dönüştürülmelidir **Value__** özelliği.

Örneğin, aşağıdaki kullanan betik **Value__** özelliği.

```powershell
$C = [System.Diagnostics.Eventing.Reader.StandardEventLevel]::Informational
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
   Level=$C.Value__
}
```