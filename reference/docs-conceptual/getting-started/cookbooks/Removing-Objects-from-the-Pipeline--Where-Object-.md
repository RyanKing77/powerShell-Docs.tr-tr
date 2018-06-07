---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Ardışık düzen tarafından nesneleri kaldırılıyor burada nesnesi
ms.assetid: 01df8b22-2d22-4e2c-a18d-c004cd3cc284
ms.openlocfilehash: 46f210e1418098f4809174cd975ab8d783580285
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34753847"
---
# <a name="removing-objects-from-the-pipeline-where-object"></a>Ardışık Düzen (Where-Object) nesneleri kaldırılıyor

Windows PowerShell'de, genellikle oluşturmak ve istediğinizden daha daha çok nesneyi ardışık düzene geçirin. Kullanarak görüntülemek için belirli nesnelerin özelliklerini belirtebilirsiniz **biçimi** cmdlet'leri, ancak bu yardımcı görüntüden tüm nesneleri kaldırmanın sorunlu. Yalnızca bir alt kümesini başlangıçta oluşturulan nesneler üzerinde eylemleri gerçekleştirebilirsiniz nesneleri bir ardışık düzen sonundan önce Filtre isteyebilirsiniz.

Windows PowerShell içeren bir `Where-Object` her nesne ardışık düzeninde test ve yalnızca belirli test koşulu karşılıyorsa ardışık düzeni iletmektir izin veren cmdlet'i. Test geçmeyin nesneler ardışık düzen tarafından kaldırılır. Test durumu değeri olarak sağladığınız `Where-Object` **FilterScript** parametresi.

### <a name="performing-simple-tests-with-where-object"></a>Where-Object ile basit testleri gerçekleştirme

Değeri **FilterScript** olan bir *betik bloğu* -kaşlı ayraç çevrelenmiş bir veya daha fazla Windows PowerShell komutlarını {} -true veya false değerlendirir. Bu komut dosyası blokları çok basit olabilir, ancak bunları oluşturmak için başka bir Windows PowerShell kavram hakkında Karşılaştırma işleçleri bilerek gerekir. Bir karşılaştırma işleci bunu her bir tarafta görüntülenen öğeleri karşılaştırır. Karşılaştırma işleçleri ile başlar bir '-' karakteri ve bir ad tarafından izlenir. Temel Karşılaştırma işleçleri neredeyse her türlü nesnesi üzerinde çalışır. Daha gelişmiş Karşılaştırma işleçleri yalnızca metin veya diziler üzerinde çalışabilir.

> [!NOTE]
> Metin ile çalışırken, varsayılan olarak, Windows PowerShell Karşılaştırma işleçleri büyük/küçük harf duyarlıdır.

Dikkat edilecek noktalar ayrıştırma nedeniyle <> gibi simgeler ve = Karşılaştırma işleçleri kullanılmaz. Bunun yerine, Karşılaştırma işleçleri harfini oluşur. Temel Karşılaştırma işleçleri aşağıdaki tabloda listelenmiştir.

|Karşılaştırma işleci|Anlamı|Örnek (true verir)|
|-----------------------|-----------|--------------------------|
|-eq|eşittir|1 - eq 1|
|-ne|Eşit değil|1 - ne 2|
|-lt|Olan küçüktür|1 - lt 2|
|-le|Küçük veya eşittir|1 - le 2|
|-gt|Değerinden büyük|2 - gt 1|
|-ge|Büyüktür veya eşittir|2 -ge 1|
|-gibi|(Metni için joker karakter karşılaştırma) benzer|"dosyam.doc"-gibi "f\*.yoğun?"|
|-notlike|(Metni için joker karakter karşılaştırma) gibi değil|"dosyam.doc"-notlike "p\*.doc"|
|-içerir|içerir|1,2,3 - 1 içerir|
|-notcontains|İçermiyor|1,2,3 - notcontains 4|

WHERE-Object komut dosyası blokları özel değişkeni '$_' ardışık düzeninde geçerli nesneye başvurma kullanın. Burada, nasıl çalıştığına ilişkin bir örnek verilmiştir. Sayıdan oluşan bir liste varsa ve yalnızca 3'ten az olan ayarlara dönmek isterseniz, Where-Object yazarak sayıları filtrelemek için kullanabilirsiniz:

```
PS> 1,2,3,4 | Where-Object -FilterScript {$_ -lt 3}
1
2
```

### <a name="filtering-based-on-object-properties"></a>Nesne özellikleri bağlı filtreleme

$_ Geçerli ardışık düzen nesnesine başvuruyor beri özelliklerini testlerimiz için erişebilirsiniz.

Örnek olarak, biz WMI Win32_SystemDriver sınıfında bakabilirsiniz. Belirli bir sistemi üzerinde sistem sürücüleri yüzlerce olabilir, ancak yalnızca sistem sürücüleri, çalıştırmakta olduğunuz olanlar gibi belirli bir dizi ilginizi çekebilir. Win32_SystemDriver üyeleri görüntülemek için Get-üye kullanıyorsanız (**Get-WmiObject-sınıfı Win32_SystemDriver | Get-Member - MemberType özelliği**) durumudur ilgili özellik ve sürücü çalıştırırken "Çalışır" bir değere sahip olduğundan görürsünüz. Sistem sürücüleri yalnızca çalışan olanları yazarak seçerek filtreleyebilirsiniz:

```powershell
Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq 'Running'}
```

Bu hala uzun bir liste oluşturur. Yalnızca StartMode değer de test ederek otomatik olarak başlayacak şekilde ayarlayın sürücüleri seçmek için filtre isteyebilirsiniz:

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

Bu bize, çok sayıda sürücülerin çalışmakta olduğunu biliyoruz çünkü artık ihtiyacımız bilgi verir. Aslında, büyük olasılıkla bu noktada ihtiyacımız yalnızca bilgilerdir adı ve görünen ad. Aşağıdaki komutu kadar basit çıktısında kaynaklanan yalnızca bu iki özellik içerir:

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

Yukarıdaki komutta iki Where-Object öğesi vardır, ancak bunlar içinde tek bir Where-Object öğesi kullanılarak ifade edilebilir ve bu gibi mantıksal işleç:

```powershell
Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript { ($_.State -eq 'Running') -and ($_.StartMode -eq 'Manual') } | Format-Table -Property Name,DisplayName
```

Standart mantıksal işleçleri aşağıdaki tabloda listelenmiştir.

|Mantıksal işleci|Anlamı|Örnek (true verir)|
|--------------------|-----------|--------------------------|
|- ve|Mantıksal ve; Her iki tarafında da doğru olduğunda true|(1 - eq 1) - ve (2 - eq 2).|
|- veya|Mantıksal veya; Her iki taraf doğru ise true|(1 - eq 1) - veya (1 - eq 2).|
|-değil|Mantıksal değil; çevirmelerinin true ve false|-değil (1 - eq 2)|
|\!|Mantıksal değil; çevirmelerinin true ve false|\!(1 - eq 2)|
