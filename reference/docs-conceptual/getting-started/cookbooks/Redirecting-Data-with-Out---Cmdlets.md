---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Out Cmdlet’leri ile Verileri Yeniden Yönlendirme
ms.assetid: 2a4acd33-041d-43a5-a3e9-9608a4c52b0c
ms.openlocfilehash: f08879f436ce751b176af020aba21e90f09aa61f
ms.sourcegitcommit: 221b7daab7f597f8b2e4864cf9b5d9dda9b9879b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52321018"
---
# <a name="redirecting-data-with-out--cmdlets"></a>Out - ile verileri yeniden yönlendirme * cmdlet'leri

Windows PowerShell doğrudan çıkış veri denetlemenize olanak sağlayan birçok cmdlet sağlar. Bu cmdlet'ler iki önemli özellikleri paylaşır.

İlk olarak, bunlar genellikle bazı metin biçimindeki verilere dönüştürün. Bunlar, metin girişi gerektiren sistem bileşenleri için veri çıktı çünkü bunlar bunu yapabilirsiniz. Bu nesnelerin metin olarak göstermek ihtiyaç duydukları anlamına gelir. Bu nedenle, bir Windows PowerShell konsol penceresi gördüğünüz gibi metin biçimlendirilir.

İkinci olarak, bu cmdlet'ler Windows PowerShell fiili kullanın **kullanıma** çünkü bunlar bilgileri Windows Powershell'den başka bir yere için gönderin. **Dışarı konak** cmdlet'tir hiçbir özel durum: Windows PowerShell dışında ana penceresi görüntülenir. Bu önemlidir, çünkü Windows PowerShell dışında veri gönderildiğinde, aslında kaldırılır. Bu sayfa verileri ana penceresi için bir işlem hattı oluşturmayı deneyin ve ardından bir liste olarak biçimlendirmek burada gösterildiği gibi çalışır, bu görebilirsiniz:

```powershell
Get-Process | Out-Host -Paging | Format-List
```

İşlem bilgileri sayfaların liste biçiminde görüntülemek için komut bekleyebilirsiniz. Bunun yerine, varsayılan Tablo listesini görüntüler:

```output
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

**Dışarı konak** cmdlet verileri doğrudan konsola gönderir böylece **Format-List** komutu hiçbir zaman aldığı biçimlendirmek için herhangi bir şey.

Bu komut yapısı doğru şekilde eklemektir **dışarı konak** cmdlet'ini aşağıda gösterildiği gibi işlem hattının sonunda. Bu, disk belleği ve görüntülenen önce listesindeki Biçimlendirilecek verilerini işleme neden olur.

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

Bu tümüne uygulanır **kullanıma** cmdlet'leri. Bir **kullanıma** cmdlet'i her zaman ardışık düzen sonunda görünmelidir.

> [!NOTE]
> Tüm **kullanıma** cmdlet'leri işleme çıkış metin olarak geçerli satırı uzunluk sınırları dahil olmak üzere, konsol penceresi için biçimlendirme kullanma.

#### <a name="paging-console-output-out-host"></a>Konsol çıktısı sayfalama (dışarı barındırma)

Varsayılan olarak, Windows PowerShell verileri tam olarak ne olduğunu ana penceresine gönderir cmdlet dışarı konak yapar. Birincil kullanım dışarı konak cmdlet'tir verilerini sayfalama daha önce bahsedildiği gibi. Örneğin, aşağıdaki komutu kullanır Get-Command cmdlet'in çıktısı, sayfa için dışarı barındırın:

```powershell
Get-Command | Out-Host -Paging
```

Ayrıca **daha fazla** sayfa verilerine işlevi. Windows PowerShell'de **daha fazla** çağıran bir işlev, **dışarı ana-disk belleği**. Aşağıdaki komutu kullanarak gösterir **daha fazla** işlevini alma komutunun çıktısı sayfasında:

```powershell
Get-Command | more
```

Daha fazla işlev bağımsız değişkenleri olarak bir veya daha fazla dosya adlarını dahil ederseniz, işlev belirtilen dosyaları okur ve içeriklerini ana sayfasında:

```
PS> more c:\boot.ini
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
...
```

#### <a name="discarding-output-out-null"></a>Çıkış atma (dışarı Null)

**Dışarı Null** cmdlet'i hemen aldığı herhangi bir giriş atmak için tasarlanmıştır. Bu, yan komutu çalıştırmanın etkisi size gereksiz verileri atılıyor için kullanışlıdır. Aşağıdaki komutu yazın, hiçbir şey komuttan ulaşırsınız değil:

```powershell
Get-Command | Out-Null
```

**Dışarı Null** cmdlet'i hata çıkış atma değil. Örneğin, aşağıdaki komutu girin, bir ileti Windows PowerShell 'Olan NotACommand' tanımıyor bildiren görüntülenir:

```
PS> Get-Command Is-NotACommand | Out-Null
Get-Command : 'Is-NotACommand' is not recognized as a cmdlet, function, operabl
e program, or script file.
At line:1 char:12
+ Get-Command  <<<< Is-NotACommand | Out-Null
```

#### <a name="printing-data-out-printer"></a>Yazdırma veri (Out-yazıcı)

Kullanarak verileri yazdırabilirsiniz **Out-yazıcı** cmdlet'i. **Out-yazıcı** cmdlet'i bir yazıcının adı belirtmezseniz varsayılan yazıcıyı kullanır. Görüntü adı belirterek herhangi bir Windows tabanlı yazıcı kullanabilirsiniz. Her türden yazıcı bağlantı noktası eşlemesi ya da gerçek fiziksel bir yazıcı için gerek yoktur. Yüklü Microsoft Office belge görüntüleme araçları varsa, örneğin, verileri bir görüntü dosyasına yazarak gönderebilirsiniz:

```powershell
Get-Command Get-Command | Out-Printer -Name 'Microsoft Office Document Image Writer'
```

#### <a name="saving-data-out-file"></a>Verileri kaydetme (dışarı dosya)

Kullanarak bir dosyaya konsol penceresinde yerine çıkış gönderebilirsiniz **dışarı dosya** cmdlet'i. Aşağıdaki komut satırını işlemlerin bir listesi için dosya gönderir. **C:\\temp\\processlist.txt**:

```powershell
Get-Process | Out-File -FilePath C:\temp\processlist.txt
```

Kullanarak sonuçları **dışarı dosya** cmdlet'i geleneksel çıktı yeniden yönlendirme için kullanılan beklediğiniz olmayabilir. Davranışını anlamak için hangi bağlamda bilmeniz gerekir **dışarı dosya** cmdlet'i çalışır.

Varsayılan olarak, **dışarı dosya** cmdlet'i bir Unicode dosyası oluşturur. Bu en iyi uzun vadede varsayılandır ancak ASCII dosyalarını beklediğiniz araçları ile varsayılan çıkış biçimini düzgün çalışmaz anlamına gelir. Varsayılan çıkış biçimini kullanarak ASCII'ye değiştirebilirsiniz **kodlama** parametresi:

```powershell
Get-Process | Out-File -FilePath C:\temp\processlist.txt -Encoding ASCII
```

**Dosya Dışarı** dosya biçimleri gibi konsol çıktısı aramak için içeriği. Bu, çoğu durumda bir konsol penceresi içinde olduğu gibi kesilecek çıkış neden olur. Örneğin aşağıdaki komutu çalıştırın:

```powershell
Get-Command | Out-File -FilePath c:\temp\output.txt
```

Çıkış şuna benzeyecektir:

```output
CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Add-Content                     Add-Content [-Path] <String[...
Cmdlet          Add-History                     Add-History [[-InputObject] ...
...
```

Ekran genişliği eşleştirilecek satırı sarar zorlamaz çıktısını almak için kullanabileceğiniz **genişliği** çizgi genişliği belirtmek için parametre. Çünkü **genişliği** bir 32 bit tam sayı parametresi sahip olabilir en büyük değer 2147483647'dir. Çizgi genişliği bu maksimum değeri ayarlamak için aşağıdaki komutu yazın:

```powershell
Get-Command | Out-File -FilePath c:\temp\output.txt -Width 2147483647
```

**Dışarı dosya** cmdlet'tir en kullanışlı konsolda görüntülenen gibi çıkış kaydetmek istediğinizde. Çıkış biçimi üzerinde daha hassas denetim için daha gelişmiş araçlar gerekir. Nesne düzenlemesini hakkında ayrıntılarla birlikte sonraki bölümde de atacağız.