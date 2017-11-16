---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: "Cmdlet ile verileri yeniden yönlendirme"
ms.assetid: 2a4acd33-041d-43a5-a3e9-9608a4c52b0c
ms.openlocfilehash: e570ca1c2c665a4a5d23abb50d4102a012b160e9
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2017
---
# <a name="redirecting-data-with-out--cmdlets"></a>Verilerle çıkış - yeniden yönlendirme * cmdlet'leri
Windows PowerShell doğrudan çıktı veri denetlemenize olanak sağlayan birkaç cmdlet'leri sağlar. Bu cmdlet'ler iki önemli özellikleri paylaşır.

İlk olarak, bunlar genellikle metin çeşit verileri dönüştürün. Metin girişi gerektiren sistem bileşenleri verileri çıktı çünkü bunu. Bu metin olarak nesneleri temsil etmek ihtiyaç duydukları anlamına gelir. Bu nedenle, Windows PowerShell konsol penceresinde gördüğünüz metin biçimlendirilir.

İkinci olarak, bu cmdlet'ler Windows PowerShell fiil kullanın **çıkışı** bunlar bilgileri Windows Powershell'den başka bir yere için göndermek için. **Dışarı konak** cmdlet'tir hiçbir özel durum: Windows PowerShell dışında ana penceresi görüntülenir. Windows PowerShell dışında veri gönderildiğinde, aslında kaldırıldığı için bu önemlidir. Bir ardışık düzen konak penceresine bu sayfaları verileri oluşturmayı deneyin ve ardından bir liste olarak biçimlendirmek aşağıda gösterildiği gibi çalışır, bu görebilirsiniz:

```
PS> Get-Process | Out-Host -Paging | Format-List
```

İşlem bilgileri sayfaların listesi biçimde görüntülemek için komutu bekleyebilirsiniz. Bunun yerine, varsayılan Tablo listesi görüntülenir:

```
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    101       5     1076       3316    32     0.05   2888 alg
...
    618      18    39348      51108   143   211.20    740 explorer
    257       8     9752      16828    79     3.02   2560 explorer
...
<SPACE> next page; <CR> next line; Q quit
...
```

**Dışarı konak** cmdlet verileri doğrudan konsola gönderir böylece **Format-List** komutu hiçbir zaman alan biçimlendirmek için herhangi bir şey.

Bu komut yapısı doğru yerleştirilecek yoludur **dışarı konak** cmdlet'ini aşağıda gösterildiği gibi ardışık düzen sonunda. Bu, disk belleği olan ve görüntülenen önce listede Biçimlendirilecek işlem verileri neden olur.

```
PS> Get-Process | Format-List | Out-Host -Paging

Id      : 2888
Handles : 101
CPU     : 0.046875
Name    : alg
...

Id      : 740
Handles : 612
CPU     : 211.703125
Name    : explorer

Id      : 2560
Handles : 257
CPU     : 3.015625
Name    : explorer
...
<SPACE> next page; <CR> next line; Q quit
...
```

Bu tümüne uygulanır **çıkışı** cmdlet'leri. Bir **çıkışı** cmdlet'inin ardışık düzen sonunda her zaman görünmelidir.

> [!NOTE]
> Tüm **çıkışı** cmdlet'leri yürürlükte biçimlendirme satır uzunluğu sınırları dahil olmak üzere konsol penceresi için kullanarak bir metin olarak çıkış işleme.

#### <a name="paging-console-output-out-host"></a>Konsol çıktısı disk belleği (dışarı ana bilgisayar)
Varsayılan olarak, Windows PowerShell verileri tam olarak ne olduğunu konak penceresine gönderir cmdlet dışarı ana bilgisayar içermiyor. Birincil kullanım dışarı konak cmdlet'tir disk belleği veri daha önce bahsedildiği gibi. Örneğin, aşağıdaki komut kullandığı Get-Command cmdlet'i çıktısını sayfası dışarı ana bilgisayar:

```
PS> Get-Command | Out-Host -Paging
```

Aynı zamanda **daha fazla** sayfa verilerine işlevi. Windows PowerShell'de **daha fazla** çağıran bir işlev değil **dışarı ana bilgisayar-disk belleği**. Aşağıdaki komutu kullanarak gösteren **daha fazla** işlevi Get-Command çıktısını sayfasında:

```
PS> Get-Command | more
```

Daha fazla işlevi bağımsız değişken olarak bir veya daha fazla dosya adlarını dahil ederseniz, işlevi belirtilen dosyaları okuma ve içeriklerini ana sayfa:

```
PS> more c:\boot.ini
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
...
```

#### <a name="discarding-output-out-null"></a>Çıkış atma (dışarı Null)
**Dışarı Null** cmdlet hemen aldığı herhangi bir giriş atmak için tasarlanmıştır. Bu, bir yan-bir komutu çalıştırmak, sonuç elde gereksiz verileri atılıyor için kullanışlıdır. Ne zaman aşağıdaki komutu yazın, herhangi bir şey komuttan ulaşırsınız değil:

```
PS> Get-Command | Out-Null
```

**Dışarı Null** cmdlet hata çıkış atma değil. Örneğin, aşağıdaki komutu girin, bir ileti Windows PowerShell 'Olan NotACommand' tanımıyor bildiren görüntülenir:

```
PS> Get-Command Is-NotACommand | Out-Null
Get-Command : 'Is-NotACommand' is not recognized as a cmdlet, function, operabl
e program, or script file.
At line:1 char:12
+ Get-Command  <<<< Is-NotACommand | Out-Null
```

#### <a name="printing-data-out-printer"></a>Yazdırma veri (Out-yazıcı)
Kullanarak verileri yazdırabilirsiniz **Out-yazıcı** cmdlet'i. **Out-yazıcı** cmdlet'i bir yazıcı adı belirtmezseniz, varsayılan yazıcı kullanır. Görünen adını belirterek herhangi bir Windows tabanlı yazıcıyı kullanabilirsiniz. Yazıcı bağlantı noktası eşlemesi veya hatta gerçek fiziksel yazıcı herhangi bir tür için gerek yoktur. Yüklü Microsoft Office belge görüntü oluşturma araçlarının varsa, örneğin, verileri bir görüntü dosyasına yazarak gönderebilirsiniz:

```
PS> Get-Command Get-Command | Out-Printer -Name "Microsoft Office Document Image Writer"
```

#### <a name="saving-data-out-file"></a>Verileri kaydetme (out-File)
Kullanarak bir dosyaya konsol penceresi yerine çıktı gönderebilirsiniz **out-File** cmdlet'i. Aşağıdaki komut satırını işlemlerin listesini dosyasına gönderir **C:\\temp\\processlist.txt**:

```
PS> Get-Process | Out-File -FilePath C:\temp\processlist.txt
```

Kullanarak sonuçlarını **out-File** cmdlet geleneksel çıktı yeniden yönlendirme için kullanılıyorsa, beklediğiniz olmayabilir. Davranışını anlamak için bağlamı bilmeniz gerekir **out-File** cmdlet'i çalışır.

Varsayılan olarak, **out-File** cmdlet'i bir Unicode dosyası oluşturur. Bu en iyi uzun vadede varsayılandır ancak ASCII dosyalarını beklediğiniz araçları ile varsayılan çıkış biçimi düzgün çalışmaz anlamına gelir. Varsayılan çıkış biçimi için ASCII kullanarak değiştirebileceğiniz **kodlama** parametre:

```
PS> Get-Process | Out-File -FilePath C:\temp\processlist.txt -Encoding ASCII
```

**Out-File** dosya biçimleri gibi konsol çıktısı aramak için içeriği. Bu, çoğu durumda konsol penceresinde olduğu gibi kesilecek çıkış neden olur. Örneğin aşağıdaki komutu çalıştırın:

```
PS> Get-Command | Out-File -FilePath c:\temp\output.txt
```

Çıktı şuna benzeyecektir:

```
CommandType     Name                            Definition                     
-----------     ----                            ----------                     
Cmdlet          Add-Content                     Add-Content [-Path] <String[...
Cmdlet          Add-History                     Add-History [[-InputObject] ...
...
```

Ekran genişliği eşleşecek şekilde satır sarmalayan zorlamaz çıkış almak için kullanabileceğiniz **genişliği** çizgi genişliğini belirlemek için parametre. Çünkü **genişliği** 32 bit tamsayı parametresi sahip olabilir en fazla 2147483647 değerdir. Çizgi genişliği bu maksimum değere ayarlamak için aşağıdaki komutu yazın:

```
Get-Command | Out-File -FilePath c:\temp\output.txt -Width 2147483647
```

**Out-File** konsolda görüntülenen gibi çıkışı kaydetmek istediğinizde cmdlet en kullanışlıdır. Çıktı biçimi üzerinde daha hassas denetim için daha gelişmiş araçlar gerekir. Sonraki bölümde nesnesi düzenleme hakkında ayrıntılarla birlikte de ele alacağız.

