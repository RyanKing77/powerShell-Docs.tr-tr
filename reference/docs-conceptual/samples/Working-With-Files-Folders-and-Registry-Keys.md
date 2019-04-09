---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Dosya, Klasör ve Kayıt Defteri Anahtarları ile Çalışma
ms.assetid: e6cf87aa-b5f8-48d5-a75a-7cb7ecb482dc
ms.openlocfilehash: cd20cc50b573435ba80b52b51e164e60625dc1b6
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293104"
---
# <a name="working-with-files-folders-and-registry-keys"></a>Dosya, klasör ve kayıt defteri anahtarları ile çalışma

Windows PowerShell kullanan isim **öğesi** bir Windows PowerShell sürücüsünde bulunan öğeleri başvurmak için. Windows PowerShell dosya sistemi sağlayıcısı ile ilgilenirken bir **öğesi** bir dosya, klasör ya da Windows PowerShell sürücüsünü olabilir. Bu görevleri ayrıntılı tartışmak istediğimiz şekilde listeleme ve bu öğeleri ile çalışma bir kritik temel çoğu yönetim ayarları'nda görevdir.

## <a name="enumerating-files-folders-and-registry-keys-get-childitem"></a>Dosyaları, klasörleri ve kayıt defteri anahtarlarını (Get-Childıtem) numaralandırma

Belirli bir konumdan bir öğe koleksiyonu alma gibi genel bir görev, olduğundan **Get-Childıtem** cmdlet'i, özellikle bir klasörü gibi bir kapsayıcı içinde bulunan tüm öğeleri döndürmek için tasarlanmıştır.

Tüm dosyaları ve klasörleri doğrudan klasördeki C: bulunan dönmek istiyorsanız\\Windows, türü:

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

Listenin, girdiğinizde gördüğünüz için benzer **dir** komutunu **Cmd.exe**, veya **ls** UNIX komut kabuğu'nda komutu.

Çok karmaşık listelerini parametrelerini kullanarak gerçekleştirebileceğiniz **Get-Childıtem** cmdlet'i. Biz birkaç senaryolarında sonraki görünecektir. Söz dizimi gördüğünüz **Get-Childıtem** yazarak cmdlet:

```powershell
Get-Command -Name Get-ChildItem -Syntax
```

Bu parametre, karma ve üst düzeyde özelleştirilmiş çıktısını almak için eşleşen.

### <a name="listing-all-contained-items--recurse"></a>Tüm bulunan öğeleri listeleme (-Recurse)

Windows klasörünün içindeki öğeleri hem de alt klasörleri içinde yer alan tüm öğeleri görmek için **Recurse** parametresinin **Get-Childıtem**. Listenin her şeyi Windows klasörü ve alt öğelerinde içinde görüntüler. Örneğin:

```
PS> Get-ChildItem -Path C:\WINDOWS -Recurse

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS\AppPatch
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM    1852416 AcGenral.dll
...
```

### <a name="filtering-items-by-name--name"></a>Öğeleri ada göre filtreleme (-adı)

Yalnızca öğelerin adlarını görüntülemek için kullanın **adı** parametresinin **Get-Childıtem**:

```
PS> Get-ChildItem -Path C:\WINDOWS -Name
addins
AppPatch
assembly
...
```

### <a name="forcibly-listing-hidden-items--force"></a>Gizli öğeleri zorla listeleme (-Force)

Dosya Gezgini veya Cmd.exe normalde görünmeyen öğeleri çıktısında görüntülenmez bir **Get-Childıtem** komutu. Gizli öğeleri görüntülemek için kullanın **zorla** parametresinin **Get-Childıtem**. Örneğin:

```powershell
Get-ChildItem -Path C:\Windows -Force
```

Zorla normal davranışı geçersiz kılabilirsiniz olduğundan bu parametreyi zorla adlı **Get-Childıtem** komutu. Zorla sistemin güvenliği tehlikeye atar herhangi bir eylem gerçekleştiremeyecek olsa da, bir cmdlet normalde gerçekleştirecek değil, bir eylem zorlar yaygın olarak kullanılan bir parametredir.

### <a name="matching-item-names-with-wildcards"></a>Joker karakterlerle eşleşen öğe adları

**Get-Childıtem** komut listeye öğe yolunda joker karakterler kabul eder.

Joker karakter eşlemesi Windows PowerShell altyapısı tarafından işlendiğinden, joker karakterleri kabul eden tüm cmdlet'ler aynı gösterimini kullanın ve eşleşen aynı davranışa sahip. Windows PowerShell joker karakter gösterimi içerir:

- Yıldız işareti (\*) sıfır veya daha çok tekrarı herhangi bir karakterle eşleşir.

- Soru işareti (?) tam olarak bir karakterle eşleşir.

- Sol köşeli ayraç (\[) karakteri ve sağ köşeli ayraç (]) karakteri kapsamak eşleşmesi gereken karakter kümesi.

Joker karakter belirtimi nasıl çalıştığına ilişkin bazı örnekleri aşağıda verilmiştir.

Sonekine sahip Windows dizinindeki tüm dosyaları bulmak için **.log** ve tam olarak beş temel adı karakter aşağıdaki komutu girin:

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

Harfi ile başlayan tüm dosyaları bulmak için **x** Windows dizini yazın:

```powershell
Get-ChildItem -Path C:\Windows\x*
```

Adları ile başlayan tüm dosyaları bulmak için **x** veya **z**, türü:

```powershell
Get-ChildItem -Path C:\Windows\[xz]*
```

### <a name="excluding-items--exclude"></a>Öğeleri hariç (-hariç)

Kullanarak belirli öğeleri hariç tutabilirsiniz **hariç** Get-childıtem komutunun parametre. Bu, tek bir deyimde filtreleme karmaşık gerçekleştirmenize olanak sağlar.

Örneğin, Windows Saat hizmeti DLL System32 klasöründe bulmaya çalıştığınız ve tüm DLL adı hatırlayabileceğiniz "W" ile başlayan ve "32" içerdiğinden varsayalım.

Bir ifade ister **w\&#42; 32\&#42;. dll** koşulları karşılayan tüm DLL'leri bulur ancak onu Windows 95 ve 16-bit Windows Uyumluluk "95" içeren bir dll veya "16" adlarında döndürebilir. Adlarını kullanarak bu sayılardan birine sahip dosyaları atlayabilirsiniz **hariç** deseni parametresi  **\&#42;\[ 9516]\&#42;**:

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

### <a name="mixing-get-childitem-parameters"></a>Get-Childıtem parametreleri karıştırma

Birkaç parametrelerinden biri kullanabileceğiniz **Get-Childıtem** aynı komutta cmdlet'i. Parametreleri karıştırmak önce joker karakterlerle eşleşen anladığınızdan emin olun. Örneğin, aşağıdaki komut, sonuç döndürür:

```powershell
Get-ChildItem -Path C:\Windows\*.dll -Recurse -Exclude [a-y]*.dll
```

Windows klasöründeki "z" harfiyle başlayan iki DLL bulunsa bile hiçbir sonuç yok.

Biz joker karakter yolun bir parçası olarak belirtilen çünkü hiçbir sonuç döndürülmedi. Komut özyinelemeli olmasına rağmen **Get-Childıtem** cmdlet öğeleri Windows klasöründe ".dll" ile sonlanan adlara sahip olanlar için kısıtlanmış.

Adları, özel bir desenle eşleşen dosyaları için yinelemeli arama belirtmek için kullanın **-dahil** parametresi.

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