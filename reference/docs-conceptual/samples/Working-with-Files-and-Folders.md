---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Dosya ve Klasörlerle Çalışma
ms.assetid: c0ceb96b-e708-45f3-803b-d1f61a48f4c1
ms.openlocfilehash: 393e886a4945222198d9b81019250c5d5b905ad3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058939"
---
# <a name="working-with-files-and-folders"></a>Dosya ve Klasörlerle Çalışma

Windows PowerShell sürücülerini gezinme ve bunları öğelerde düzenleme Windows fiziksel disk sürücüsü üzerindeki dosya ve klasörleri yönetmek için benzerdir. Bu bölümde, PowerShell kullanarak belirli dosya ve klasör düzenleme görevlerle başa çıkma açıklanmaktadır.

## <a name="listing-all-the-files-and-folders-within-a-folder"></a>Tüm dosya ve klasörlerin bir klasördeki listeleme

Kullanarak, doğrudan bir klasördeki tüm öğeleri alabilirsiniz **Get-Childıtem**. İsteğe bağlı ekleme **zorla** gizli görüntülemek ya da sistem öğeleri için parametre. Örneğin, bu komut (olan Windows fiziksel sürücü C ile aynı) Windows PowerShell sürücüsü C doğrudan içeriğini görüntüler:

```powershell
Get-ChildItem -Path C:\ -Force
```

Komut Cmd.exe's kullanma gibi doğrudan içerilen öğelerin yalnızca listeler **DIR** komutu veya **ls** UNIX Kabuğu'nda. İçerilen öğelerin göstermek için belirtmeniz gerekir **-Recurse** parametresini de. (Bu, tamamlanması çok uzun zaman alabilir.) Her şeyi C sürücüsünde listelemek için:

```powershell
Get-ChildItem -Path C:\ -Force -Recurse
```

**Get-Childıtem** öğeleriyle filtreleyebilirsiniz kendi **yolu**, **filtre**, **INCLUDE**, ve **hariç** parametreleri, ancak bu genellikle yalnızca adına göre. Karmaşık filtreleme öğelerin diğer özelliklerini kullanarak gerçekleştirebileceğiniz **Where-Object**.

Aşağıdaki komutu, son 1 Ekim 2005'ten sonra değiştirilmiş olan ve 1 megabayt değerinden küçük veya büyük 10 megabayt olan Program dosyaları klasöründeki tüm yürütülebilir dosyaları bulur:

```powershell
Get-ChildItem -Path $env:ProgramFiles -Recurse -Include *.exe | Where-Object -FilterScript {($_.LastWriteTime -gt '2005-10-01') -and ($_.Length -ge 1mb) -and ($_.Length -le 10mb)}
```

## <a name="copying-files-and-folders"></a>Dosya ve klasörleri kopyalama

Kopyalama ile yapılır **Copy-Item**. C: aşağıdaki komutu yedekler\\c: boot.ini\\boot.bak:

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak
```

Hedef dosya zaten var. kopyalama girişimi başarısız olur. Önceden var olan bir hedef üzerine yazmak için kullanın **zorla** parametresi:

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak -Force
```

Bu komut, hedef salt okunur olsa bile çalışır.

Klasörü kopyalama aynı şekilde çalışır. Bu komut ' % s'klasörü C: kopyalar\\temp\\yeni klasöre C: test1\\temp\\DeleteMe yinelemeli olarak:

```powershell
Copy-Item C:\temp\test1 -Recurse C:\temp\DeleteMe
```

Öğelerin seçimini de kopyalayabilirsiniz. Aşağıdaki komut c: herhangi bir yerde bulunan tüm .txt dosyaları kopyalar\\c: veri\\temp\\metin:

```powershell
Copy-Item -Filter *.txt -Path c:\data -Recurse -Destination C:\temp\text
```

Dosya sistemi kopyalarını gerçekleştirmek için diğer araçları kullanmaya devam edebilirsiniz. XCOPY, ROBOCOPY ve COM nesneleri gibi **Scripting.FileSystemObject,** tüm Windows PowerShell içinde çalışacak. Örneğin, Windows Script Host kullanabileceğiniz **Scripting.FileSystem COM** C: ' üzere sınıfı\\c: boot.ini\\boot.bak:

```powershell
(New-Object -ComObject Scripting.FileSystemObject).CopyFile('C:\boot.ini', 'C:\boot.bak')
```

## <a name="creating-files-and-folders"></a>Dosya ve klasör oluşturma

Yeni öğeler oluşturma, aynı tüm Windows PowerShell sağlayıcılarının çalışır. Bir Windows PowerShell sağlayıcısı öğesi birden fazla türü olup olmadığını — Örneğin, dosya sistemi Windows PowerShell sağlayıcısını dizinler ve dosyalar arasında ayıran — öğesi türünü belirtmeniz gerekir.

Bu komut yeni bir klasör C: oluşturur\\temp\\yeni klasör:

```powershell
New-Item -Path 'C:\temp\New Folder' -ItemType Directory
```

Bu komut yeni bir boş dosya C: oluşturur\\temp\\yeni klasör\\dosya.txt

```powershell
New-Item -Path 'C:\temp\New Folder\file.txt' -ItemType File
```

## <a name="removing-all-files-and-folders-within-a-folder"></a>Tüm dosya ve klasörleri bir klasördeki kaldırma

İçerilen öğelerin kullanarak kaldırabilirsiniz **Kaldır öğesini**, ancak başka bir öğe içeriyorsa, kaldırma işlemini onaylamanız istenir. Örneğin, C: klasör silmeye çalışıyorsanız\\temp\\diğer öğeleri içeren DeleteMe Windows PowerShell sizden onay klasörü silmeden önce:

```
Remove-Item -Path C:\temp\DeleteMe

Confirm
The item at C:\temp\DeleteMe has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

İçindeki her öğe için sorulmasını istemiyorsanız belirtin **Recurse** parametresi:

```powershell
Remove-Item -Path C:\temp\DeleteMe -Recurse
```

## <a name="mapping-a-local-folder-as-a-windows-accessible-drive"></a>Bir Windows erişilebilir sürücü gibi yerel bir klasöre eşleme

Yerel bir klasöre de eşleyebilirsiniz kullanarak **subst** komutu. Aşağıdaki komut, yerel Program Files dizininde P: kök erişim izni verilmiş bir yerel sürücüye oluşturur:

```powershell
subst p: $env:programfiles
```

İle olduğu gibi ağ sürücülerini, eşlenen sürücülerini Windows PowerShell kullanarak içinde **subst** için Windows PowerShell Kabuk tarafından anında görülemez.

## <a name="reading-a-text-file-into-an-array"></a>Bir diziye bir metin dosyası okuma

Metin veriler için daha yaygın depolama biçimleri bir dosyada ayrı veri öğeleri olarak kabul ayrı satırlara ile biridir. **Get-Content** cmdlet'i kullanılabilir tek bir adımda tüm dosyayı okumak için burada gösterildiği gibi:

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

**Get-Content** zaten, dosya içeriğinin satır başına bir öğe dizisi olarak dosyadan okunan veriler değerlendirir. Bu denetleyerek doğrulayabilirsiniz **uzunluğu** döndürülen içerik:

```
PS> (Get-Content -Path C:\boot.ini).Length
6
```

Bu komut, doğrudan Windows PowerShell bilgilerini listesini almak için en kullanışlıdır. Örneğin, bilgisayar adlarını veya IP adreslerini listesini bir dosyada C: depolayabilir\\temp\\domainMembers.txt, dosya her satırda bir ada sahip. Kullanabileceğiniz **Get-Content** dosya içeriğini almak ve bunları değişkeninde yerleştirebilirsiniz **$Computers**:

```powershell
$Computers = Get-Content -Path C:\temp\DomainMembers.txt
```

**$Computers** , artık her öğe bir bilgisayar adını içeren bir dizi.
