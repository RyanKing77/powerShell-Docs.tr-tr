---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: Dosya ve Klasörlerle Çalışma
ms.openlocfilehash: 743e261d2f5e8bfa39f2731fca7fea6e5678c711
ms.sourcegitcommit: 02eed65c526ef19cf952c2129f280bb5615bf0c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70215525"
---
# <a name="working-with-files-and-folders"></a>Dosya ve Klasörlerle Çalışma

Windows PowerShell sürücülerinden gezinmek ve bunların üzerindeki öğelerin düzenlenmesi, Windows fiziksel disk sürücülerindeki dosya ve klasörleri düzenleme ile benzerdir. Bu bölümde, PowerShell kullanarak belirli dosya ve klasör işleme görevleriyle nasıl başa çıkılabileceği açıklanmaktadır.

## <a name="listing-all-the-files-and-folders-within-a-folder"></a>Bir klasör Içindeki tüm dosya ve klasörleri listeleme

**Get-ChildItem**kullanarak tüm öğeleri doğrudan bir klasör içinde alabilirsiniz. Gizli veya sistem öğelerini göstermek için isteğe bağlı **zorlama** parametresini ekleyin. Örneğin, bu komut Windows PowerShell sürücüsü C 'nin (Windows fiziksel sürücü C ile aynı) doğrudan içeriğini görüntüler:

```powershell
Get-ChildItem -Path C:\ -Force
```

Komut, cmd. exe ' nin **dır** komutunu ya da bir UNIX kabuğundan **ls** gibi yalnızca doğrudan içerilen öğeleri listeler. İçerilen öğeleri göstermek için **-Recurse** parametresini de belirtmeniz gerekir. (Bu işlem, tamamlanması çok uzun zaman alabilir.) C sürücüsündeki her şeyi listelemek için:

```powershell
Get-ChildItem -Path C:\ -Force -Recurse
```

**Get-ChildItem** , öğeleri **yolu**, **filtresi**, **içerme**ve **dışlama** parametreleriyle filtreleyip, ancak bunlar genellikle yalnızca adı temel alır. **WHERE-Object**kullanarak öğelerin diğer özelliklerine göre karmaşık filtreleme gerçekleştirebilirsiniz.

Aşağıdaki komut, 1 Ekim 2005 ' den sonra son değiştirilen ve 1 megabayttan küçük veya 10 megabayttan büyük olmayan program dosyaları klasöründeki tüm yürütülebilir dosyaları bulur:

```powershell
Get-ChildItem -Path $env:ProgramFiles -Recurse -Include *.exe | Where-Object -FilterScript {($_.LastWriteTime -gt '2005-10-01') -and ($_.Length -ge 1mb) -and ($_.Length -le 10mb)}
```

## <a name="copying-files-and-folders"></a>Dosya ve klasörleri kopyalama

Kopyalama, kopyalama **öğesi**ile yapılır. Aşağıdaki komut c:\\Boot. ini dosyasını c:\\Boot. bak öğesine yedekler:

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak
```

Hedef dosya zaten varsa kopyalama girişimi başarısız olur. Önceden var olan bir hedefin üzerine yazmak için **zorla** parametresini kullanın:

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak -Force
```

Bu komut, hedef salt okunurdur olsa bile işe yarar.

Klasör kopyalama aynı şekilde çalışmaktadır. Bu komut c\\: temp\\test1 klasörünü yeni c:\\temp\\klasörüne kopyalar.

```powershell
Copy-Item C:\temp\test1 -Recurse C:\temp\DeleteMe
```

Ayrıca, öğelerin bir seçimini de kopyalayabilirsiniz. Aşağıdaki komut, c:\\Data içinde herhangi bir yerde bulunan tüm. txt dosyalarını\\c: temp\\metnine kopyalar:

```powershell
Copy-Item -Filter *.txt -Path c:\data -Recurse -Destination C:\temp\text
```

Dosya sistemi kopyalarını gerçekleştirmek için diğer araçları kullanmaya devam edebilirsiniz. XCOPY, ROBOCOPY ve **Scripting. Filesystemmobject** gibi com nesneleri Windows PowerShell 'de çalışır. Örneğin, c:\\Boot. ini dosyasını c:\\Boot. bak ' a yedeklemek için Windows Script Host **Scripting. FileSystem com** sınıfını kullanabilirsiniz:

```powershell
(New-Object -ComObject Scripting.FileSystemObject).CopyFile('C:\boot.ini', 'C:\boot.bak')
```

## <a name="creating-files-and-folders"></a>Dosya ve klasör oluşturma

Yeni öğelerin oluşturulması, tüm Windows PowerShell sağlayıcılarıyla aynı şekilde çalışmaktadır. Bir Windows PowerShell sağlayıcısında birden fazla öğe türü varsa — Örneğin, dosya sistemi Windows PowerShell sağlayıcısı dizinler ve dosyalar arasında ayrım yapar; öğe türünü belirtmeniz gerekir.

Bu komut yeni bir klasör oluşturur C:\\temp\\yeni klasör:

```powershell
New-Item -Path 'C:\temp\New Folder' -ItemType Directory
```

Bu komut yeni bir boş dosya oluşturur C:\\temp\\yeni klasör\\File. txt

```powershell
New-Item -Path 'C:\temp\New Folder\file.txt' -ItemType File
```

## <a name="removing-all-files-and-folders-within-a-folder"></a>Bir klasör Içindeki tüm dosya ve klasörleri kaldırma

İçerilen öğeleri **Remove-Item**' ı kullanarak kaldırabilirsiniz, ancak öğe başka bir şey içeriyorsa kaldırma işlemini onaylamanız istenir. Örneğin, diğer öğeleri içeren C:\\temp\\deleteme klasörünü silmeye çalışırsanız, Windows PowerShell, klasörü silmeden önce sizden onay ister:

```
Remove-Item -Path C:\temp\DeleteMe

Confirm
The item at C:\temp\DeleteMe has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

İçerilen her öğe için istenmesini istemiyorsanız, **Recurse** parametresini belirtin:

```powershell
Remove-Item -Path C:\temp\DeleteMe -Recurse
```

## <a name="mapping-a-local-folder-as-a-drive"></a>Yerel bir klasörü sürücü olarak eşleme

Ayrıca, **New-PSDrive** komutunu kullanarak yerel bir klasörü eşleyebilirsiniz. Aşağıdaki komut, yerel Program Files dizininde belirtilen yerel bir sürücü olan P: ' i yalnızca PowerShell oturumundan görünür olarak oluşturur:

```powershell
New-PSDrive -Name P -Root $env:ProgramFiles -PSProvider FileSystem
```

Ağ sürücülerinde olduğu gibi, Windows PowerShell içinde eşlenen sürücüler hemen Windows PowerShell kabuğu tarafından görülebilir.
Dosya Gezgini 'nden görünebilir bir eşlenen sürücü oluşturmak için, **-Persist** parametresi gerekir. Ancak, kalıcı olarak yalnızca uzak yollar kullanılabilir.


## <a name="reading-a-text-file-into-an-array"></a>Bir metin dosyasını bir diziye okuma

Metin verileri için daha yaygın depolama biçimlerinden biri ayrı satırlar olarak değerlendirilen bir dosya içinde farklı veri öğeleri olarak değerlendirilir. **Get-Content** cmdlet 'i, burada gösterildiği gibi, bir adımda tüm bir dosyayı okumak için kullanılabilir:

```
PS> Get-Content -Path C:\boot.ini
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional"
 /noexecute=AlwaysOff /fastdetect
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS=" Microsoft Windows XP Professional
with Data Execution Prevention" /noexecute=optin /fastdetect
```

**Get-Content** , dosya içeriğinin her satırı için bir öğe olarak dosyadaki okunan verileri bir dizi olarak zaten değerlendirir. Döndürülen içeriğin **uzunluğunu** denetleyerek bunu doğrulayabilirsiniz:

```
PS> (Get-Content -Path C:\boot.ini).Length
6
```

Bu komut, Windows PowerShell 'e doğrudan bilgi listesi almak için kullanışlıdır. Örneğin, bir bilgisayar adı veya IP adresi listesini dosyanın her satırında tek bir ada sahip C:\\temp\\domainmembers. txt dosyasında saklayabilirsiniz. Dosya içeriğini almak ve **$Computers**değişkenine koymak için **Get-Content** kullanabilirsiniz:

```powershell
$Computers = Get-Content -Path C:\temp\DomainMembers.txt
```

**$Computers** artık her öğe için bir bilgisayar adı içeren bir dizidir.
