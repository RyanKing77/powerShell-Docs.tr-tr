---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Dosya, Klasör ve Kayıt Defteri Anahtarları ile Çalışma
ms.assetid: e6cf87aa-b5f8-48d5-a75a-7cb7ecb482dc
ms.openlocfilehash: a09b127d4ba37d33cb4c0f0ce0819e645fd4b137
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30952316"
---
# <a name="working-with-files-folders-and-registry-keys"></a>Dosyalar, klasörler ve kayıt defteri anahtarları ile çalışma

Windows PowerShell kullanan isim **öğesi** bir Windows PowerShell sürücüsünde bulunan öğeler başvurmak için. Windows PowerShell dosya sistemi sağlayıcısı ile ilgilenirken bir **öğesi** bir dosya, klasör veya Windows PowerShell sürücüsünü olabilir. Bu görevler ayrıntılı tartışmak istiyoruz şekilde listesi ve bu öğeleri ile çalışma bir kritik temel çoğu yönetim ayarları'nda görevdir.

### <a name="enumerating-files-folders-and-registry-keys-get-childitem"></a>Dosyalar, klasörler ve kayıt defteri anahtarları (Get-Childıtem) numaralandırma

Belirli bir konumdan öğeleri koleksiyonu alma gibi bir ortak görevi olduğundan **Get-Childıtem** cmdlet, özellikle bir klasörü gibi bir kapsayıcı içinde bulunan tüm öğeleri döndürmek için tasarlanmıştır.

Tüm dosya ve klasörlerin doğrudan klasördeki C: içerdiği dönmek isterseniz\\Windows, türü:

```
PS> Get-ChildItem -Path C:\Windows
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-16   8:10 AM          0 0.log
-a---        2005-11-29   3:16 PM         97 acc1.txt
-a---        2005-10-23  11:21 PM       3848 actsetup.log
...
```

Liste, girdiğiniz zaman gördüğünüz için benzer **dir** komutunu **Cmd.exe**, veya **ls** UNIX komut kabuğunda komutu.

Parametreleri kullanarak çok karmaşık listelerini gerçekleştirebileceğiniz **Get-Childıtem** cmdlet'i. Biz birkaç senaryolarında sonraki arar. Sözdizimi görebilirsiniz **Get-Childıtem** yazarak cmdlet:

```powershell
Get-Command -Name Get-ChildItem -Syntax
```

Bu parametreler, karma ve yüksek oranda özelleştirilmiş çıkış almak için eşleşmedi.

#### <a name="listing-all-contained-items--recurse"></a>Tüm bulunan öğeleri listeleme (-Recurse)

Öğeleri bir Windows klasörü içinde ve alt klasörlerin içinde bulunan tüm öğeleri görmek için **Recurse** parametresinin **Get-Childıtem**. Listenin her şeyi Windows klasöründeki ve onun alt klasörlerindeki öğelerde içinde görüntüler. Örneğin:

```
PS> Get-ChildItem -Path C:\WINDOWS -Recurse

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS\AppPatch
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM    1852416 AcGenral.dll
...
```

#### <a name="filtering-items-by-name--name"></a>Öğeleri ada göre filtreleme (-Name)

Yalnızca öğelerin adlarını görüntülemek için kullanın **adı** parametresinin **Get-Childıtem**:

```
PS> Get-ChildItem -Path C:\WINDOWS -Name
addins
AppPatch
assembly
...
```

#### <a name="forcibly-listing-hidden-items--force"></a>Zorla gizli öğeleri listeleme (-Force)

Dosya Gezgini'ni veya Cmd.exe normalde görünmeyen öğeleri çıktısında görüntülenmez bir **Get-Childıtem** komutu. Gizli öğeleri görüntülemek için kullanın **zorla** parametresinin **Get-Childıtem**. Örneğin:

```powershell
Get-ChildItem -Path C:\Windows -Force
```

Zorla normal davranışını geçersiz kılabilirsiniz çünkü bu parametre zorla adlı **Get-Childıtem** komutu. Zorla sistem güvenliği tehlikeye atar herhangi bir işlem gerçekleştirmez olsa da, bir cmdlet normalde gerçekleştireceği değil, bir eylem zorlar yaygın olarak kullanılan bir parametredir.

#### <a name="matching-item-names-with-wildcards"></a>Joker karakterlerle eşleşen öğe adları

**Get-Childıtem** komutu liste öğelerine yolda joker karakterleri kabul eder.

Joker karakter eşleştirme Windows PowerShell altyapısı tarafından işlendiğinden, joker karakterler kabul tüm cmdlet'leri aynı gösterimi kullanabilir ve aynı eşleşen davranışı sahiptir. Windows PowerShell joker gösterimi içerir:

- Yıldız işareti (\*) herhangi bir karakter sıfır veya daha çok tekrarı ile eşleşir.

- Soru işareti (?) tam olarak bir karakterle eşleşir.

- Sol köşeli ayraç (\[) karakteri ve sağ parantez (]) karakteri çevreleyen eşleştirilmesini karakter kümesi.

Burada, joker karakter belirtimi nasıl çalıştığı bazı örnekler verilmiştir.

Son ekini içeren Windows dizinindeki tüm dosyaları bulmak için **.log** ve temel adı tam olarak beş karakter aşağıdaki komutu girin:

```
PS> Get-ChildItem -Path C:\Windows\?????.log

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
...
-a---        2006-05-11   6:31 PM     204276 ocgen.log
-a---        2006-05-11   6:31 PM      22365 ocmsn.log
...
-a---        2005-11-11   4:55 AM         64 setup.log
-a---        2005-12-15   2:24 PM      17719 VxSDM.log
...
```

Harfiyle başlayan tüm dosyaları bulmak için **x** Windows dizinde yazın:

```powershell
Get-ChildItem -Path C:\Windows\x*
```

Adları ile başlayan tüm dosyaları bulmak için **x** veya **z**, türü:

```powershell
Get-ChildItem -Path C:\Windows\[xz]*
```

#### <a name="excluding-items--exclude"></a>Öğeleri hariç (-hariç)

Belirli öğeleri kullanarak dışlayabilirsiniz **hariç** Get-Childıtem parametresi. Bu, tek bir deyimde filtreleme karmaşık gerçekleştirmenize olanak tanır.

Örneğin, Windows Saat hizmeti DLL System32 klasöründe bulmayı denediğiniz ve tüm DLL adı unutmayın "W" ile başlar ve "32" içerdiği varsayalım.

Bir ifade ister **w\&#42; 32\&#42;. dll** koşullarını tüm DLL'ler bulur ancak, aynı zamanda Windows 95 ve 16 bit Windows Uyumluluğu "95" dahil DLL'leri ya da "16" adlarında döndürebilir. Bu sayı adlarını kullanarak olan dosyaları atlayabilirsiniz **hariç** düzeni parametresiyle  **\&#42;\[ 9516]\&#42;**:

```
PS> Get-ChildItem -Path C:\WINDOWS\System32\w*32*.dll -Exclude *[9516]*

Directory: Microsoft.PowerShell.Core\FileSystem::C:\WINDOWS\System32
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM     174592 w32time.dll
-a---        2004-08-04   8:00 AM      22016 w32topl.dll
-a---        2004-08-04   8:00 AM     101888 win32spl.dll
-a---        2004-08-04   8:00 AM     172032 wldap32.dll
-a---        2004-08-04   8:00 AM     264192 wow32.dll
-a---        2004-08-04   8:00 AM      82944 ws2_32.dll
-a---        2004-08-04   8:00 AM      42496 wsnmp32.dll
-a---        2004-08-04   8:00 AM      22528 wsock32.dll
-a---        2004-08-04   8:00 AM      18432 wtsapi32.dll
```

#### <a name="mixing-get-childitem-parameters"></a>Get-Childıtem parametreleri karıştırma

Birkaç parametrelerinden biri kullanabilirsiniz **Get-Childıtem** cmdlet aynı komutta. Parametreleri karışık önce joker karakter eşleştirme anladığınızdan emin olun. Örneğin, aşağıdaki komut, hiçbir sonuç döndürür:

```powershell
Get-ChildItem -Path C:\Windows\*.dll -Recurse -Exclude [a-y]*.dll
```

Windows klasöründeki "z" harfiyle başlayan iki DLL olsa bile, sonuç yok.

Biz joker yolun bir parçası olarak belirtilen çünkü sonuç döndürülmedi. Komut özyinelemeli olmasına rağmen **Get-Childıtem** cmdlet öğeleri Windows klasöründe ".dll" ile biten adlara sahip olanlar için kısıtlanmış.

Dosya adları özel bir desenle eşleşen bir özyinelemeli arama belirtmek için kullanın **-dahil** parametresi.

```
PS> Get-ChildItem -Path C:\Windows -Include *.dll -Recurse -Exclude [a-y]*.dll

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows\System32\Setup

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM       8261 zoneoc.dll

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows\System32

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM     337920 zipfldr.dll
```