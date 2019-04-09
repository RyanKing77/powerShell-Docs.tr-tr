---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Komut zincirinden nesne kaldırma nesne
ms.assetid: 01df8b22-2d22-4e2c-a18d-c004cd3cc284
ms.openlocfilehash: 1f7d064c7bf2dd551ea96b29762fbccad8174084
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293155"
---
# <a name="removing-objects-from-the-pipeline-where-object"></a>Nesneler (Where-Object) komut zincirinden nesne kaldırma

Windows PowerShell'de, genellikle oluşturmak ve istediğinizden daha daha fazla nesne için bir işlem hattı geçirin. Kullanarak görüntülemek için belirli nesnelerin özelliklerini belirtebilirsiniz **biçimi** cmdlet'leri, ancak bu yardımcı tüm nesneleri görüntüler kaldırmanın sorunlu. Yalnızca başlangıçta oluşturulan nesnelerin bir alt kümesinde eylemleri gerçekleştirebilmek için bir işlem hattı bitmeden önce nesneleri filtrelemek isteyebilirsiniz.

Windows PowerShell içeren bir `Where-Object` her nesne işlem hattında test etmek ve yalnızca bu başarılı işlem hattı belirli test koşulunu karşılıyorsa olanak tanıyan cmdlet'i. Test geçmeyin nesneleri ardışık düzen tarafından kaldırılır. Test koşulu değeri olarak sağladığınız `Where-Object` **FilterScript** parametresi.

## <a name="performing-simple-tests-with-where-object"></a>Where-Object içeren basit testler gerçekleştirme

Değerini **FilterScript** olduğu bir *betik bloğu* -ayraçları içine alınmış bir veya daha fazla Windows PowerShell komutlarını {} -true veya false değerlendiren. Bu komut dosyası blokları çok basit olabilir ancak bunları oluşturmak için Karşılaştırma işleçleri başka bir Windows PowerShell kavramı hakkında bilmek gerekir. Karşılaştırma işleci, içerdiği her bir tarafta görüntülenen öğe karşılaştırır. Karşılaştırma işleçleri ile başlayan bir '-' karakteri ve ardından bir adı. Temel Karşılaştırma işleçleri, neredeyse her türlü nesnesi üzerinde çalışır. Daha gelişmiş Karşılaştırma işleçleri yalnızca metin veya diziler üzerinde çalışabilir.

> [!NOTE]
> Varsayılan metin ile çalışırken, Windows PowerShell Karşılaştırma işleçleri büyük/küçük harf duyarsızdır.

Dikkat edilecek noktalar ayrıştırma nedeniyle <> gibi simgeler ve = Karşılaştırma işleçleri kullanılmaz. Bunun yerine, Karşılaştırma işleçleri harfini oluşur. Aşağıdaki tabloda temel Karşılaştırma işleçleri listelenir.

|Karşılaştırma işleci|Anlamı|Örnek (true değerini döndürür)|
|-----------------------|-----------|--------------------------|
|-eq|eşittir|1 - eq 1|
|-ne|Eşit değildir|1 - ne 2|
|-lt|Olan küçüktür|1 - lt 2|
|-le|küçüktür veya eşittir|1 - le 2|
|-gt|büyüktür|2 - gt 1|
|-ge|büyüktür veya eşittir|2 -ge 1|
|-gibi|(Metni için joker karakter karşılaştırma) gibidir|"dosyam.doc"-gibi "f\*.yoğun?"|
|-notlike|(Metni için joker karakter karşılaştırma) gibi değil|"dosyam.doc"-notlike "p\*.doc"|
|-içerir|İçerir|1,2,3 - 1 içerir|
|-notcontains|İçermez|1,2,3 - notcontains 4|

WHERE-Object komut dosyası blokları kullanmak özel değişkeni `$_` işlem hattındaki geçerli nesneye başvurmak için. Nasıl çalıştığına ilişkin bir örnek aşağıda verilmiştir. Sayıdan oluşan bir liste olması ve yalnızca 3'ten az olan ayarlara dönmek istiyorsanız, Where-Object yazarak sayıları filtrelemek için kullanabilirsiniz:

```
PS> 1,2,3,4 | Where-Object -FilterScript {$_ -lt 3}
1
2
```

## <a name="filtering-based-on-object-properties"></a>Nesne özellikleri tabanlı filtreleme

Bu yana `$_` başvurur geçerli işlem hattı nesnesine biz özelliklerini testlerimiz için erişebilirsiniz.

Örneğin, WMI Win32_SystemDriver sınıfında biz göz atabilirsiniz. Sistem sürücüleri belirli bir sistemde yüzlerce olabilir, ancak yalnızca sistem sürücüleri, hangi şu anda çalışıyor gibi belirli bir kümesini ilginizi çekebilir. Win32_SystemDriver üyeleri görüntülemek için Get-Member kullanıyorsanız (**Get-WmiObject-sınıfı Win32_SystemDriver | Get-Member - MemberType özelliği**), ilgili özellik durumudur ve sürücü çalışırken "Çalışıyor" değerine sahip olduğunu görürsünüz. Sistem sürücüleri yalnızca çalışan olanları yazarak seçerek filtreleyebilirsiniz:

```powershell
Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq 'Running'}
```

Bu, yine de uzun bir liste oluşturur. Yalnızca StartMode değeri de test ederek otomatik olarak başlatılacak şekilde ayarlandığı sürücüleri seçmek için filtre isteyebilirsiniz:

```
PS> Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq "Running"} | Where-Object -FilterScript {$_.StartMode -eq "Auto"}

DisplayName : RAS Asynchronous Media Driver
Name        : AsyncMac
State       : Running
Status      : OK
Started     : True

DisplayName : Audio Stub Driver
Name        : audstub
State       : Running
Status      : OK
Started     : True
```

Bu birçok bilgi sürücüleri çalıştığını bildiğimiz artık ihtiyacımız sağlıyor. Aslında, tek bilgi büyük olasılıkla bu noktada ihtiyacımız var. adı ve görünen adı Aşağıdaki komutu, çok daha basit çıktısında kaynaklanan yalnızca bu iki özellik içerir:

```
PS> Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq "Running"} | Where-Object -FilterScript {$_.StartMode -eq "Manual"} | Format-Table -Property Name,DisplayName

Name                                    DisplayName
----                                    -----------
AsyncMac                                RAS Asynchronous Media Driver
Fdc                                     Floppy Disk Controller Driver
Flpydisk                                Floppy Disk Driver
Gpc                                     Generic Packet Classifier
IpNat                                   IP Network Address Translator
mouhid                                  Mouse HID Driver
MRxDAV                                  WebDav Client Redirector
mssmbios                                Microsoft System Management BIOS Driver
```

Yukarıdaki komutta iki Where-Object öğe vardır, ancak bunlar içinde tek bir Where-Object öğesi kullanarak ifade edilebilir ve bunun gibi mantıksal işleç:

```powershell
Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript { ($_.State -eq 'Running') -and ($_.StartMode -eq 'Manual') } | Format-Table -Property Name,DisplayName
```

Aşağıdaki tabloda standart mantıksal işleçleri listelenir.

|Mantıksal işleci|Anlamı|Örnek (true değerini döndürür)|
|--------------------|-----------|--------------------------|
|- ve|Mantıksal ve; Her iki tarafında da true ise true|(1 - eq 1) - ve (2 - eq 2).|
|- veya|Mantıksal veya; Her iki taraf doğru ise true|(1 - eq 1) - veya (1 - eq 2).|
|-değil|Mantıksal değil; TRUE ve false tersine çevirir.|-değil (1 - eq 2)|
|\!|Mantıksal değil; TRUE ve false tersine çevirir.|\!(1 - eq 2)|
