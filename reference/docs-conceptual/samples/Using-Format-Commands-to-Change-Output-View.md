---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Çıkış Görünümünü Değiştirmek İçin Biçimlendirme Komutları Kullanma
ms.assetid: 63515a06-a6f7-4175-a45e-a0537f4f6d05
ms.openlocfilehash: 97d3a9e04abb61bb80a0b8c67d9fb9e885a0b91b
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405913"
---
# <a name="using-format-commands-to-change-output-view"></a>Çıkış Görünümünü Değiştirmek İçin Biçimlendirme Komutları Kullanma

Windows PowerShell, hangi özellikler belirli nesneler için görüntülenen denetlemenize olanak sağlayan cmdlet'ler kümesi vardır. Tüm cmdlet'lerin adlarını fiili ile başlayan **biçimi**. Gösterilecek bir veya daha fazla özellikler seçmenizi sağlar.

**Biçimi** cmdlet'leri **biçimi genelinde**, **Format-List**, **Format-Table**, ve **biçim özel**. Biz yalnızca anlatmaktadır **biçimi genelinde**, **Format-List**, ve **Format-Table** cmdlet'leri Bu Kullanıcı Kılavuzu'nda.

Her biçim cmdlet'inin görüntülemek için belirli özellikler belirtmezseniz, kullanılacak varsayılan özellikleri vardır. Her cmdlet de aynı parametre adı kullanır **özelliği**görüntülemek istediğiniz özellikler belirtmek için. Çünkü **biçimi genelinde** yalnızca tek bir özelliğe gösterir, **özelliği** parametresi yalnızca özellik parametrelerini ancak tek bir değer alır **Format-List** ve **Format-Table** özellik adlarının bir listesini kabul eder.

Komutu kullanırsanız **Get-Process - ad powershell** ile iki örnek Windows PowerShell çalıştırma, şuna benzer bir çıktı alırsınız:

```output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    995       9    30308      27996   152     2.73   2760 powershell
    331       9    23284      29084   143     1.06   3448 powershell
```

Bu bölümün kalanında, biz nasıl kullanılacağı inceleyeceksiniz **biçimi** bu komutun çıktısı görüntülenir şeklini değiştirmek için cmdlet'ler.

### <a name="using-format-wide-for-single-item-output"></a>Biçim genelinde tek öğeli çıkış için kullanma

**Biçimi genelinde** cmdlet'i, varsayılan olarak, yalnızca bir nesne için varsayılan özelliği görüntülenir. Her nesneyle ilişkili bilgileri tek bir sütunda görüntülenir:

```
PS> Get-Process -Name powershell | Format-Wide

powershell                              powershell
```

Varsayılan olmayan bir özellik de belirtebilirsiniz:

```
PS> Get-Process -Name powershell | Format-Wide -Property Id

2760                                    3448
```

#### <a name="controlling-format-wide-display-with-column"></a>Biçim genelinde görüntü sütunu denetleme

İle **biçimi genelinde** cmdlet'i, aynı anda yalnızca tek bir özellik görüntüleyebilirsiniz. Bu, her satırda yalnızca bir öğeyi gösteren basit listelerini görüntülemek için kullanışlıdır. Basit bir listesini almak için değerini ayarlamak **sütun** yazarak 1 parametresi:

```powershell
Get-Command Format-Wide -Property Name -Column 1
```

### <a name="using-format-list-for-a-list-view"></a>Bir liste görünümü için biçim listesi kullanma

**Format-List** cmdlet etiketlenmiş ve ayrı bir satıra görüntülenen her bir özellik içeren bir liste biçiminde bir nesne görüntüler:

```
PS> Get-Process -Name powershell | Format-List

Id      : 2760
Handles : 1242
CPU     : 3.03125
Name    : powershell

Id      : 3448
Handles : 328
CPU     : 1.0625
Name    : powershell
```

İstediğiniz sayıda özelliklerini belirtebilirsiniz:

```
PS> Get-Process -Name powershell | Format-List -Property ProcessName,FileVersion
,StartTime,Id

ProcessName : powershell
FileVersion : 1.0.9567.1
StartTime   : 2006-05-24 13:42:00
Id          : 2760

ProcessName : powershell
FileVersion : 1.0.9567.1
StartTime   : 2006-05-24 13:54:28
Id          : 3448
```

#### <a name="getting-detailed-information-by-using-format-list-with-wildcards"></a>Biçim listesinde joker karakterlerini kullanarak ayrıntılı bilgilerini alma

**Format-List** cmdlet'i değeri olarak bir joker karakter kullanmanıza imkan tanır, **özelliği** parametresi. Bu, ayrıntılı bilgileri görüntülemenize olanak sağlar. Genellikle, nesneleri, Windows PowerShell, varsayılan olarak tüm özellik değerlerini göstermiyor neden olan ihtiyacınız olandan daha fazla bilgi içerir. Tüm bir nesnenin özelliklerini göstermek için kullanma **Format-List-özellik \&#42;** komutu. Aşağıdaki komut, çıktı tek bir işlem için 60'tan fazla satırları oluşturur:

```powershell
Get-Process -Name powershell | Format-List -Property *
```

Ancak **Format-List** komutu, birçok öğeyi içeren çıkış genel bir bakış istediğiniz, daha basit bir tablo görünümüne ise genellikle daha fazla ayrıntı göstermek için kullanışlıdır yararlıdır.

### <a name="using-format-table-for-tabular-output"></a>Biçim tablosu için tablo çıktısı kullanma

Kullanırsanız **Format-Table** cmdlet hiçbir özellik adı ile belirtilen çıkışını biçimlendirmek için **Get-Process** komutunu tam olarak aynı biçimlendirmeleri yapmadan yaptığınız gibi çıktısını alın. Çoğu Windows PowerShell nesneleri gibi işlemler genellikle bir tablo biçiminde görüntülenir nedenidir.

```
PS> Get-Process -Name powershell | Format-Table

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
   1488       9    31568      29460   152     3.53   2760 powershell
    332       9    23140        632   141     1.06   3448 powershell
```

#### <a name="improving-format-table-output-autosize"></a>Tablo biçiminde çıktı (AutoSize) geliştirme

Tablolu bir görünümü birçok karşılaştırılabilir bilgi görüntülemek için kullanışlı olsa da, görüntü verilerini çok darsa yorumlamak zor olabilir. İşlem yolu, kimlik, ad ve şirket görüntülenecek çalışırsanız, örneğin, kısaltılmış çıktı işlem yolu ve şirket sütun için olursunuz:

```
PS> Get-Process -Name powershell | Format-Table -Property Path,Name,Id,Company

Path                Name                                 Id Company
----                ----                                 -- -------
C:\Program Files... powershell                         2836 Microsoft Corpor...
```

Belirtirseniz **AutoSize** çalıştırdığınızda parametresi **Format-Table** komutu, Windows PowerShell, görüntülenecek seçeceğiz gerçek verilere dayalı sütun genişliklerini hesaplar. Böylece **yolu** sütun okunabilir, ancak şirket sütun kesilmiş kalır:

```
PS> Get-Process -Name powershell | Format-Table -Property Path,Name,Id,Company -
AutoSize

Path                                                    Name         Id Company
----                                                    ----         -- -------
C:\Program Files\Windows PowerShell\v1.0\powershell.exe powershell 2836 Micr...
```

**Format-Table** cmdlet veri yine de kesin, ancak bunu yalnızca ekran sonunda bunu yapar. Görüntülenen son farklı özellikler, bunların düzgün görüntülenmesi kendi uzun veri öğesi için gerektiği kadar boyutu verilir. Şirket adı görülebilir ancak yolu konumlarını değiştirme, kısaltılır gördüğünüz **yolu** ve **şirket** içinde **özelliği** değer listesi:

```
PS> Get-Process -Name powershell | Format-Table -Property Company,Name,Id,Path -
AutoSize

Company               Name         Id Path
-------               ----         -- ----
Microsoft Corporation powershell 2836 C:\Program Files\Windows PowerShell\v1...
```

**Format-Table** komut varsayar, nearer daha önemli olan özellik listesi başlangıcına özelliğidir. Başına en yakın özelliklerini görüntülemek çalışır böylece tamamen. Varsa **Format-Table** komutu tüm özelliklerini görüntüleme, uyarı ve görüntüden bazı sütunları kaldırın. Siz bu davranışı gördüğünüz **adı** listesindeki en son özellik:

```
PS> Get-Process -Name powershell | Format-Table -Property Company,Path,Id,Name -
AutoSize

WARNING: column "Name" does not fit into the display and was removed.

Company               Path                                                    I
                                                                              d
-------               ----                                                    -
Microsoft Corporation C:\Program Files\Windows PowerShell\v1.0\powershell.exe 6
```

Yukarıdaki çıktıda kimlik sütunu listenin içine sığması için kesilmiş ve sütun başlıklarından yığılır. Otomatik olarak sütunları yeniden boyutlandırma her zaman, istediğiniz yapmaz.

#### <a name="wrapping-format-table-output-in-columns-wrap"></a>Format-Table çıkış sütunları (kaydırma) sarmalama

Uzun zorlayabilirsiniz **Format-Table** kullanarak kendi görüntü sütunu içinde sarmalamak için veri **kaydırma** parametresi. Kullanarak **kaydırma** parametre tek başına değil gerekmeyen yeterlidir de belirtmezseniz varsayılan ayarları kullandığından, beklediğiniz **AutoSize**:

```
PS> Get-Process -Name powershell | Format-Table -Wrap -Property Name,Id,Company,
Path

Name                                 Id Company             Path
----                                 -- -------             ----
powershell                         2836 Microsoft Corporati C:\Program Files\Wi
                                        on                  ndows PowerShell\v1
                                                            .0\powershell.exe
```

Kullanmanın bir avantajı **kaydırma** kendisi tarafından parametredir, çok fazla işleme yavaş değil. Büyük dizin sistemi özyinelemeli dosya listesini gerçekleştirirseniz, çok uzun sürüyor ve çok miktarda bellek kullanıyorsanız, ilk çıktı öğeleri görüntülemeden önce kullanın **AutoSize**.

Ardından sistem yükü bir kaygınız yoksa **AutoSize** şununla düzgün çalışır **kaydırma** parametresi. Başlangıç sütunlarını her zaman tek bir satırda belirttiğinizde olarak, öğeleri görüntülemek gerektiği kadar genişliği ayrılan **AutoSize** olmadan **kaydırma** parametresi. Tek fark, gerekirse son sütunu sarmalanır.:

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Name,I
d,Company,Path

Name         Id Company               Path
----         -- -------               ----
powershell 2836 Microsoft Corporation C:\Program Files\Windows PowerShell\v1.0\
                                      powershell.exe
```

İlk olarak, geniş sütun belirtirseniz, öncelikle küçük veri öğelerini belirtmek güvenli, bu nedenle bazı sütunları görüntülenmeyebilir. Aşağıdaki örnekte, biz çok geniş bir yol öğesi ilk belirtin ve hatta kaydırma ile biz yine de son kaybetmek **adı** sütun:

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Path,I
d,Company,Name

WARNING: column "Name" does not fit into the display and was removed.

Path                                                      Id Company
----                                                      -- -------
C:\Program Files\Windows PowerShell\v1.0\powershell.exe 2836 Microsoft Corporat
                                                             ion
```

#### <a name="organizing-table-output--groupby"></a>Tablo çıkışına düzenleme (-gruplandırma ölçütü)

Tablo çıktısı denetimi için başka bir kullanışlı parametresi **GroupBy**. Tablo listeleri artık özellikle Karşılaştırılacak zor olabilir. **GroupBy** parametresi çıkışı bir özellik değerine göre gruplandırır. Örneğin, şu işlemler için daha kolay denetleme özelliği listenin şirket değerini atlayarak şirket tarafından gruplandırabilirsiniz:

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Name,I
d,Path -GroupBy Company

   Company: Microsoft Corporation

Name         Id Path
----         -- ----
powershell 1956 C:\Program Files\Windows PowerShell\v1.0\powershell.exe
powershell 2656 C:\Program Files\Windows PowerShell\v1.0\powershell.exe
```