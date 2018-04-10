---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Dosya ve Klasörlerle Çalışma
ms.assetid: c0ceb96b-e708-45f3-803b-d1f61a48f4c1
ms.openlocfilehash: e47ea00c9d90d7e04a7af0cb1348849410a6e357
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="working-with-files-and-folders"></a>Dosya ve Klasörlerle Çalışma

Windows PowerShell sürücüler gezinme ve bunları öğelerde düzenleme dosya ve klasörleri Windows fiziksel disk sürücülerine düzenleme için benzer. Bu bölümdeki belirli dosya ve klasör işleme görevlerini uğraşmanız nasıl aşağıdakiler ele alınacaktır.

### <a name="listing-all-the-files-and-folders-within-a-folder"></a>Tüm dosya ve klasörlerin bir klasördeki listeleme

Kullanarak doğrudan bir klasördeki tüm öğeleri alabilirsiniz **Get-Childıtem**. İsteğe bağlı eklemek **zorla** görüntüleme gizli veya sistem öğelere parametresi. Örneğin, bu komut, Windows PowerShell (olan Windows fiziksel sürücü C ile aynı) C sürücüsü doğrudan içeriğini görüntüler:

```powershell
Get-ChildItem -Force C:\
```

Komutu Cmd.exe's kullanarak benzer doğrudan içerilen öğelerin yalnızca listeler **DIR** komut veya **ls** UNIX Kabuğu'nda. İçerilen öğelerin gösterebilmeniz belirtmeniz gerekir **-Recurse** parametresini de. (Bu tamamlanması çok uzun bir zaman alabilir.) C sürücüsünde her şeyi listelemek için:

```powershell
Get-ChildItem -Force C:\ -Recurse
```

**Get-Childıtem** öğeleriyle filtreleyebilirsiniz kendi **yolu**, **filtre**, **INCLUDE**, ve **hariç** parametreleri, ancak bu genellikle yalnızca adına göre. Karmaşık öğelerinin diğer özellikleri kullanarak göre filtreleme gerçekleştirebilirsiniz **Where-Object**.

Aşağıdaki komut, 1 Ekim 2005'ten sonra son değiştirildiği ve 1 megabayt değerinden küçük veya 10 megabayt daha büyük olduğu Program dosyaları klasöründeki tüm yürütülebilir dosyaları bulur:

```powershell
Get-ChildItem -Path $env:ProgramFiles -Recurse -Include *.exe | Where-Object -FilterScript {($_.LastWriteTime -gt '2005-10-01') -and ($_.Length -ge 1mb) -and ($_.Length -le 10mb)}
```

### <a name="copying-files-and-folders"></a>Dosya ve klasörleri kopyalama

Kopyalama ile yapılır **Copy-Item**. Aşağıdaki komutu C: yedekler\\boot.ini c:\\boot.bak:

```powershell
Copy-Item -Path c:\boot.ini -Destination c:\boot.bak
```

Hedef dosya zaten varsa, kopyalama denemesi başarısız olur. Önceden varolan bir hedefi üzerine yazmak için zorlama parametresini kullanın:

```powershell
Copy-Item -Path c:\boot.ini -Destination c:\boot.bak -Force
```

Bu komut, hedef salt okunur olduğunda bile çalışır.

Klasör kopyalama aynı şekilde çalışır. Bu komut C: klasörüne kopyalar\\temp\\test1 yeni klasör c:\\temp\\DeleteMe yinelemeli olarak:

```powershell
Copy-Item C:\temp\test1 -Recurse c:\temp\DeleteMe
```

Ayrıca, öğelerin seçimini kopyalayabilirsiniz. Aşağıdaki komutu her yerden c: yer alan tüm .txt dosyaları kopyalar\\c: veri\\temp\\metin:

```powershell
Copy-Item -Filter *.txt -Path c:\data -Recurse -Destination c:\temp\text
```

Dosya sistemi kopyalarını gerçekleştirmek için diğer araçlarını kullanmaya devam edebilirsiniz. XCOPY, ROBOCOPY ve COM nesnelerini gibi **Scripting.FileSystemObject,** tüm Windows PowerShell içinde çalışır. Örneğin, Windows Script Host kullanabilirsiniz **Scripting.FileSystem COM** C: yedeklemek için sınıf\\boot.ini c:\\boot.bak:

```powershell
(New-Object -ComObject Scripting.FileSystemObject).CopyFile('c:\boot.ini', 'c:\boot.bak')
```

### <a name="creating-files-and-folders"></a>Dosyalar ve klasörler oluşturma

Yeni öğeler oluşturma aynı tüm Windows PowerShell sağlayıcılarının çalışır. Bir Windows PowerShell sağlayıcısı öğesi birden fazla türü olup olmadığını — Örneğin, dosya sistemi Windows PowerShell sağlayıcısını dizinler ve dosyalar arasında ayırt — öğesi türünü belirtmeniz gerekir.

Bu komut, yeni bir klasör C: oluşturur\\temp\\yeni klasör:

```powershell
New-Item -Path 'C:\temp\New Folder' -ItemType Directory
```

Bu komut yeni bir boş dosya C: oluşturur\\temp\\yeni klasör\\dosya.txt'yi

```powershell
New-Item -Path 'C:\temp\New Folder\file.txt' -ItemType File
```

### <a name="removing-all-files-and-folders-within-a-folder"></a>Tüm dosya ve klasörlerin bir klasördeki kaldırma

Kapsanan öğelerini kullanarak kaldırabilirsiniz **Kaldır öğesini**, ancak başka bir şey öğe içeriyorsa, kaldırma işlemini onaylamanız istenir. Örneğin, C: klasörü silmeye çalışırsanız\\temp\\diğer öğeleri içeren DeleteMe, Windows PowerShell sizden klasörü silmeden önce onay için:

```
Remove-Item C:\temp\DeleteMe

Confirm
The item at C:\temp\DeleteMe has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

İçerilen her öğe için sorulmasını istemiyorsanız belirtin **Recurse** parametre:

```powershell
Remove-Item C:\temp\DeleteMe -Recurse
```

### <a name="mapping-a-local-folder-as-a-windows-accessible-drive"></a>Bir Windows erişilebilir sürücü gibi yerel bir klasöre eşleme

Ayrıca yerel bir klasöre eşleştirebilirsiniz kullanarak **subst** komutu. Aşağıdaki komut P: kökü yerel bir sürücünün yerel Program Files dizininde oluşturur:

```powershell
subst p: $env:programfiles
```

Ağ sürücüleri gibi yalnızca ile eşlenen sürücülerini Windows PowerShell kullanarak içinde **subst** için Windows PowerShell Kabuğu'nu hemen görülebilir.

### <a name="reading-a-text-file-into-an-array"></a>Bir diziye bir metin dosyası okuma

Metin verileri için daha yaygın depolama biçimleri bir dosyada ayrı veri öğeleri olarak kabul ayrı satırlara sahip biridir. **Get-Content** cmdlet'i tek bir adımda tüm bir dosyayı okumak için kullanılabilecek aşağıda gösterildiği gibi:

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

**Get-Content** zaten dosya içeriğinin satır başına bir öğesiyle bir dizi olarak dosyadan okunan veriler değerlendirir. Bu denetleyerek doğrulayabilirsiniz **uzunluğu** döndürülen içerik:

```
PS> (Get-Content -Path C:\boot.ini).Length
6
```

Bu komut doğrudan Windows PowerShell bilgilerini listesini almak için kullanışlıdır. Örneğin, bir dosyada C: bilgisayar adlarını veya IP adresleri listesi depolayabilir\\temp\\domainMembers.txt dosya her satırda bir ada sahip. Kullanabileceğiniz **Get-Content** dosya içeriğini almak ve bunları değişkende yerleştirin **$Computers**:

```powershell
$Computers = Get-Content -Path C:\temp\DomainMembers.txt
```

**$Computers** olan şimdi her öğe bir bilgisayar adı içeren bir dizi.