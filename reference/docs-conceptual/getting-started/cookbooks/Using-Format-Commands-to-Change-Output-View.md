---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Çıkış Görünümünü Değiştirmek İçin Biçimlendirme Komutları Kullanma
ms.assetid: 63515a06-a6f7-4175-a45e-a0537f4f6d05
ms.openlocfilehash: 97d3a9e04abb61bb80a0b8c67d9fb9e885a0b91b
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30952792"
---
# <a name="using-format-commands-to-change-output-view"></a>Çıkış Görünümünü Değiştirmek İçin Biçimlendirme Komutları Kullanma

Windows PowerShell hangi özelliklerin belirli nesneler için görüntülenen denetlemenize izin cmdlet'ler kümesi vardır. Tüm cmdlet'ler adlarını fiil ile başlayan **biçimi**. Bunlar göstermek için bir veya daha fazla özellikleri seçmenize olanak tanır.

**Biçimi** cmdlet'leri **biçimi genelinde**, **Format-List**, **Format-Table**, ve **biçimi-özel**. Biz yalnızca anlatmaktadır **biçimi genelinde**, **Format-List**, ve **Format-Table** cmdlet'leri Bu Kullanıcı Kılavuzu'nda.

Her biçim cmdlet'ine görüntülemek için belirli özellikler belirtmezseniz, kullanılacak varsayılan özellikleri vardır. Her cmdlet de aynı parametre adı kullanan **özelliği**, görüntülemek istediğiniz hangi özelliklerini belirtmek için. Çünkü **biçimi genelinde** yalnızca tek bir özellik gösterir, **özelliği** parametresi yalnızca özellik parametrelerinin ancak tek bir değer alır **Format-List** ve **Format-Table** özellik adlarının bir listesini kabul eder.

Komutunu kullanırsanız **Get-Process - ad powershell** Windows PowerShell çalışan iki örnekleriyle şuna benzer bir çıktı alın:

```output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    995       9    30308      27996   152     2.73   2760 powershell
    331       9    23284      29084   143     1.06   3448 powershell
```

Bu bölümde kalan biz nasıl kullanılacağını inceleyeceksiniz **biçimi** bu komutun çıktısı görüntülenir şeklini değiştirmek için cmdlet'leri.

### <a name="using-format-wide-for-single-item-output"></a>Biçim genelinde tek öğe çıkışı için kullanma

**Biçimi genelinde** cmdlet'i, varsayılan olarak, yalnızca bir nesnenin varsayılan özelliğine görüntüler. Her nesne ile ilişkili bilgileri tek bir sütunda görüntülenir:

```
PS> Get-Process -Name powershell | Format-Wide

powershell                              powershell
```

Ayrıca, varsayılan olmayan bir özellik belirtebilirsiniz:

```
PS> Get-Process -Name powershell | Format-Wide -Property Id

2760                                    3448
```

#### <a name="controlling-format-wide-display-with-column"></a>Sütun biçimi genelinde ekranıyla denetleme

İle **biçimi genelinde** cmdlet, aynı anda yalnızca tek bir özellik görüntüleyebilirsiniz. Bu, satır başına yalnızca tek bir öğe Göster basit listelerini görüntülemek için kullanışlıdır. Basit bir listesini almak için değerini ayarlamak **sütun** parametresi yazarak 1:

```powershell
Get-Command Format-Wide -Property Name -Column 1
```

### <a name="using-format-list-for-a-list-view"></a>Bir liste görünümü için Format-List kullanma

**Format-List** cmdlet etiketli ve ayrı bir satırda görüntülenen her bir özellik içeren bir liste biçiminde bir nesne görüntüler:

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

#### <a name="getting-detailed-information-by-using-format-list-with-wildcards"></a>Joker karakter olarak Format-List kullanarak alma ayrıntılı bilgi

**Format-List** cmdlet'i bir joker karakter değeri olarak kullanmanıza imkan tanır kendi **özelliği** parametresi. Bu, ayrıntılı bilgileri görüntülemenize olanak sağlar. Genellikle, Windows PowerShell, varsayılan olarak tüm özellik değerlerini göstermez neden olan gereksinim duyduğunuz daha fazla bilgi nesneleri içerir. Tüm nesne özelliklerini görüntülemek için kullanın **Format-List-özelliği \&#42;** komutu. Aşağıdaki komut 60 satırlık bir tek bir işlem için çıktı üretir:

```powershell
Get-Process -Name powershell | Format-List -Property *
```

Ancak **Format-List** komutu çok sayıda öğe içeren çıktı genel bir bakış istediğiniz, daha basit bir tablo görünümü ise genellikle daha fazla ayrıntı, göstermek için yararlıdır yararlıdır.

### <a name="using-format-table-for-tabular-output"></a>Biçim tablosu için tablo çıktısı kullanarak

Kullanırsanız **Format-Table** hiçbir özellik adları cmdlet'iyle belirtilen çıktısını biçimlendirmek için **Get-Process** komutu tam olarak aynı herhangi bir biçimlendirme yapmadan yaptığınız gibi çıktısını alırsınız. Çoğu Windows PowerShell nesneler gibi işlemleri genellikle bir tablo biçiminde görüntülenen nedenidir.

```
PS> Get-Process -Name powershell | Format-Table

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
   1488       9    31568      29460   152     3.53   2760 powershell
    332       9    23140        632   141     1.06   3448 powershell
```

#### <a name="improving-format-table-output-autosize"></a>Tablo Biçimlendir çıkış (AutoSize) artırma

Bir tablo görünümü çok sayıda karşılaştırılabilir bilgi görüntülemek için yararlı olsa da, görüntü verilerini çok darsa yorumlamaya zor olabilir. İşlem yolu, kimliği, ad ve şirket görüntülemeye, örneğin, kesilmiş çıktı işlem yolu ve şirket sütun için alırsınız:

```
PS> Get-Process -Name powershell | Format-Table -Property Path,Name,Id,Company

Path                Name                                 Id Company
----                ----                                 -- -------
C:\Program Files... powershell                         2836 Microsoft Corpor...
```

Belirtirseniz **AutoSize** çalıştırdığınızda parametre **Format-Table** komutu, Windows PowerShell bulacağınızı görüntülemek için gerçek verileri temel alan sütun genişliklerini hesaplar. Böylece **yolu** sütun okunabilir ancak şirket sütun kesilmiş kalır:

```
PS> Get-Process -Name powershell | Format-Table -Property Path,Name,Id,Company -
AutoSize

Path                                                    Name         Id Company
----                                                    ----         -- -------
C:\Program Files\Windows PowerShell\v1.0\powershell.exe powershell 2836 Micr...
```

**Format-Table** cmdlet veri hala kesmek, ancak bunu yalnızca ekran sonunda görüntülemez. Görüntülenen son farklı özellikleri düzgün görüntülemek kendi uzun veri öğesi için gerektiği kadar boyutu verilir. Şirket adı görülebilir ancak yolu konumlarını değiştirme, kısaltılır görebilirsiniz **yolu** ve **şirket** içinde **özelliği** değer listesi:

```
PS> Get-Process -Name powershell | Format-Table -Property Company,Name,Id,Path -
AutoSize

Company               Name         Id Path
-------               ----         -- ----
Microsoft Corporation powershell 2836 C:\Program Files\Windows PowerShell\v1...
```

**Format-Table** komut varsayar, nearer bir özellik listesi başlangıcına daha önemli olduğunu özelliğidir. Başına en yakın özelliklerini görüntülemek deneme şekilde tamamen. Varsa **Format-Table** komutu tüm özelliklerini görüntüleyemiyor, bu görüntüden bazı sütunları kaldırmak ve bir uyarı sağlayın. Bunu yaparsanız, bu davranış görebilirsiniz **adı** listedeki son özellik:

```
PS> Get-Process -Name powershell | Format-Table -Property Company,Path,Id,Name -
AutoSize

WARNING: column "Name" does not fit into the display and was removed.

Company               Path                                                    I
                                                                              d
-------               ----                                                    -
Microsoft Corporation C:\Program Files\Windows PowerShell\v1.0\powershell.exe 6
```

Yukarıdaki çıktıda ID sütunu listenin içine sığması için kesilir ve sütun başlıkları Yığılmış. Otomatik olarak sütunları yeniden boyutlandırma her zaman istediğinizi yapmaz.

#### <a name="wrapping-format-table-output-in-columns-wrap"></a>Kaydırma Tablo Biçimlendir çıkış sütunlarında (kaydırma)

Uzun zorlayabilirsiniz **Format-Table** kullanarak, görüntü sütunu içinde kaydırmak için veri **sarmalamak** parametresi. Kullanarak **sarmalamak** parametresi tek başına mutlaka yapmaması de belirtmezseniz varsayılan ayarları kullandığından, beklediğiniz **AutoSize**:

```
PS> Get-Process -Name powershell | Format-Table -Wrap -Property Name,Id,Company,
Path

Name                                 Id Company             Path
----                                 -- -------             ----
powershell                         2836 Microsoft Corporati C:\Program Files\Wi
                                        on                  ndows PowerShell\v1
                                                            .0\powershell.exe
```

Kullanmanın bir avantajı **sarmalamak** kendisi tarafından parametredir, çok fazla işleme yavaş değil. Özyinelemeli dosya listesini büyük dizin sistemi gerçekleştirirseniz, çok uzun sürebilir ve kullanıyorsanız ilk çıkış öğeleri görüntülenmeden önce bir miktarda bellek kullanmak **AutoSize**.

Ardından sistem yükü bir kaygınız yoksa **AutoSize** ile iyi çalışır **sarmalamak** parametresi. İlk sütun her zaman belirttiğinizde gibi bir satıra öğeleri görüntülemek gerektiği kadar genişliği ayrılan **AutoSize** olmadan **sarmalamak** parametresi. Tek fark, gerekirse son sütun sarılır şöyledir:

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Name,I
d,Company,Path

Name         Id Company               Path
----         -- -------               ----
powershell 2836 Microsoft Corporation C:\Program Files\Windows PowerShell\v1.0\
                                      powershell.exe
```

İlk olarak, en geniş sütunları belirtirseniz, en küçük veri öğeleri ilk belirtmek güvenli olması için bazı sütunları görüntülenmeyebilir. Aşağıdaki örnekte, biz çok geniş yol öğesi ilk belirtin ve hatta kaydırma ile biz yine son kaybedersiniz **adı** sütun:

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Path,I
d,Company,Name

WARNING: column "Name" does not fit into the display and was removed.

Path                                                      Id Company
----                                                      -- -------
C:\Program Files\Windows PowerShell\v1.0\powershell.exe 2836 Microsoft Corporat
                                                             ion
```

#### <a name="organizing-table-output--groupby"></a>Tablo çıktısı düzenleme (-GroupBy)

Tablo çıkış denetimi için başka bir yararlı parametresi **GroupBy**. Artık Tablo listelerini özellikle karşılaştırmak zor olabilir. **GroupBy** parametresi bir özellik değerine dayalı çıktı grupları. Örneğin, biz işlemler daha kolay denetleme özelliği listenin şirket değerinden atlama şirket tarafından gruplayabilirsiniz.

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Name,I
d,Path -GroupBy Company

   Company: Microsoft Corporation

Name         Id Path
----         -- ----
powershell 1956 C:\Program Files\Windows PowerShell\v1.0\powershell.exe
powershell 2656 C:\Program Files\Windows PowerShell\v1.0\powershell.exe
```