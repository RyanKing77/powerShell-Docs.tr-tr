---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: "Öğeleri doğrudan düzenleme"
ms.assetid: 8cbd4867-917d-41ea-9ff0-b8e765509735
ms.openlocfilehash: d9aa95dcb0da2e8203cbe32d64b95bf33d914166
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2017
---
# <a name="manipulating-items-directly"></a>Öğeleri doğrudan düzenleme
Dosyaları ve dosya sistemi sürücülerine klasörlerde ve Windows PowerShell kayıt defteri sürücüleri, kayıt defteri anahtarlarında gibi Windows PowerShell sürücülerdeki gördüğünüz öğeleri adlı *öğeleri* Windows PowerShell'de. Öğesi bunlarla çalışmak için cmdlet'leri isim sahip **öğesi** adlarında.

Çıktısını **Get-Command - isim öğesi** komut gösterir dokuz Windows PowerShell öğesi cmdlet'leri vardır.

```
PS> Get-Command -Noun Item

CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Clear-Item                      Clear-Item [-Path] <String[]...
Cmdlet          Copy-Item                       Copy-Item [-Path] <String[]>...
Cmdlet          Get-Item                        Get-Item [-Path] <String[]> ...
Cmdlet          Invoke-Item                     Invoke-Item [-Path] <String[...
Cmdlet          Move-Item                       Move-Item [-Path] <String[]>...
Cmdlet          New-Item                        New-Item [-Path] <String[]> ...
Cmdlet          Remove-Item                     Remove-Item [-Path] <String[...
Cmdlet          Rename-Item                     Rename-Item [-Path] <String>...
Cmdlet          Set-Item                        Set-Item [-Path] <String[]> ...
```

### <a name="creating-new-items-new-item"></a>Yeni öğeler (öğesi yeni) oluşturma
Dosya sisteminde yeni bir öğe oluşturmak üzere kullanmanız **yeni öğe** cmdlet'i. Dahil **yolu** öğenin yolu parametresiyle ve **ItemType** parametresi "dosyası" veya "dizin" değerine sahip.

Örneğin, adında yeni bir dizin oluşturmak için "New.Directory"in C:\\Temp dizininde, türü:

```
PS> New-Item -Path c:\temp\New.Directory -ItemType Directory

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18  11:29 AM            New.Directory
```

Bir dosya oluşturmak için değerini değiştirme **ItemType** "dosyası" parametresi. Örneğin, New.Directory dizininde "Dosya1.ref" adlı bir dosya oluşturmak için şunu yazın:

```
PS> New-Item -Path C:\temp\New.Directory\file1.txt -ItemType file

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp\New.Directory

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-18  11:44 AM          0 file1
```

Yeni bir kayıt defteri anahtarı oluşturmak için aynı tekniği kullanabilirsiniz. Aslında, bir kayıt defteri anahtarı yalnızca Windows kayıt defteri öğesi türü bir anahtar olduğundan oluşturmak kolaydır. (Kayıt defteri girdileridir öğesi *özellikleri*.) Örneğin, CurrentVersion alt anahtarda "_Test" adlı bir anahtar oluşturmak için şunu yazın:

```
PS> New-Item -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion_Test

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Micros
oft\Windows\CurrentVersion

SKC  VC Name                           Property
---  -- ----                           --------
  0   0 _Test                          {}
```

Kayıt defteri yolu yazarken, iki nokta üst üste eklediğinizden emin olun (**:**) Windows PowerShell'de sürücü adları, HKLM: ve HKCU:. İki nokta üst üste, Windows PowerShell yolunda sürücü adı tanımıyor.

### <a name="why-registry-values-are-not-items"></a>Neden kayıt defteri değerlerini öğeler değil
Kullandığınızda **Get-Childıtem** bir kayıt defteri anahtarında öğeleri bulmak için cmdlet gerçek kayıt defteri girdileri veya değerlerine hiçbir zaman görürsünüz.

Örneğin, kayıt defteri anahtarı **HKEY_LOCAL_MACHINE\\yazılım\\Microsoft\\Windows\\CurrentVersion\\çalıştırmak** genellikle birkaç kayıt defteri girdileri içerir Bu, sistem başlatıldığında çalışan uygulamaları temsil eder.

Ancak, kullandığınızda **Get-Childıtem** anahtarında alt öğeleri aramak için tüm görürsünüz olan **OptionalComponents** anahtarının alt anahtar:

```
PS> Get-ChildItem HKLM:\Software\Microsoft\Windows\CurrentVersion\Run
   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\Micros
oft\Windows\CurrentVersion\Run
SKC  VC Name                           Property
---  -- ----                           --------
  3   0 OptionalComponents             {}
```

Kayıt defteri girdileri öğeleri olarak işlemek kullanışlı olsa da, bir kayıt defteri girdisi yoluna benzersiz sağlar bir biçimde belirtemezsiniz. Yol gösterimi adlı kayıt defteri alt anahtarı arasında ayrım yapmaz **çalıştırmak** ve **(varsayılan)** kayıt defteri girişini **çalıştırmak** alt anahtarı. Ayrıca, kayıt defteri girişi adları ters eğik çizgi karakteri içerebileceğinden (**\\**), kayıt defteri girişleri öğeleri olsaydı adlı bir kayıt defteri girdisi ayırt etmek için yol gösterimi kullanılamadı sonra  **Windows\\CurrentVersion\\çalıştırmak** ilgili yolda bulunan alt.

### <a name="renaming-existing-items-rename-item"></a>Varolan öğeleri (öğe yeniden adlandırılamadı) yeniden adlandırma
Bir dosya veya klasör adını değiştirmek için kullanmak **öğe yeniden adlandırılamadı** cmdlet'i. Aşağıdaki komut adını değiştirir **Dosya1.ref** dosya **fileOne.txt**.

```
PS> Rename-Item -Path C:\temp\New.Directory\file1.txt fileOne.txt
```

**Öğe yeniden adlandırılamadı** cmdlet, bir dosya veya klasör adını değiştirebilirsiniz, ancak bir öğe taşınamıyor. Temp Dizini New.Directory dizinden dosyayı taşımak denemesi için aşağıdaki komutu başarısız olur.

```
PS> Rename-Item -Path C:\temp\New.Directory\fileOne.txt c:\temp\fileOne.txt
Rename-Item : Cannot rename because the target specified is not a path.
At line:1 char:12
+ Rename-Item  <<<< -Path C:\temp\New.Directory\fileOne c:\temp\fileOne.txt
```

### <a name="moving-items-move-item"></a>Öğeleri (Move-Item) taşıma
Bir dosya veya klasöre taşımak için kullanın **taşıma öğesi** cmdlet'i.

Örneğin, aşağıdaki komutu New.Directory directory C: taşır\\C: sürücüsünün kökündeki geçici dizine. Öğe taşındı doğrulamak için dahil **PassThru** parametresinin **taşıma öğesi** cmdlet'i. Olmadan **Passthru**, **taşıma öğesi** cmdlet herhangi bir sonuç görüntülemez.

```
PS> Move-Item -Path C:\temp\New.Directory -Destination C:\ -PassThru

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18  12:14 PM            New.Directory
```

### <a name="copying-items-copy-item"></a>Öğe (öğeyi Kopyala) kopyalama
Diğer Kabukları kopyalama işlemleri biliyorsanız, davranışını bulabileceğiniz **Copy-Item** olağan dışı olması için Windows PowerShell cmdlet'i. Bir öğeyi tek bir konumdan diğerine kopyaladığınızda Copy-Item içeriğinin varsayılan olarak kopyalamaz.

Örneğin, kopyalama, **New.Directory** dizininden C: sürücüsündeki C:\\geçici dizin, komutun başarılı olur, ancak New.Directory dizindeki dosyaların kopyalanmadı.

```
PS> Copy-Item -Path C:\New.Directory -Destination C:\temp
```

İçeriğini görüntülerseniz **C:\\temp\\New.Directory**, dosya içermiyor bulacaksınız:

```
PS> Get-ChildItem -Path C:\temp\New.Directory
PS>
```

Neden değil **Copy-Item** cmdlet kopyalama içeriğini yeni konuma?

**Copy-Item** cmdlet genel olacak şekilde tasarlanmıştır; bu dosya ve klasörleri kopyalama için yalnızca değil. Ayrıca, bile dosya ve klasörleri kopyalama sırasında yalnızca kapsayıcı ve içerisindeki öğeleri kopyalama isteyebilirsiniz.

Tüm bir klasörün içeriğini kopyalamak için eklemeniz **Recurse** parametresinin **Copy-Item** cmdlet komutu. Dizin içeriğini olmadan kopyaladıysanız, ekleme **zorla** parametresi boş klasörünün üzerine olanak tanır.

```
PS> Copy-Item -Path C:\New.Directory -Destination C:\temp -Recurse -Force -Passthru
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18   1:53 PM            New.Directory

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp\New.Directory

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-18  11:44 AM          0 file1
```

### <a name="deleting-items-remove-item"></a>Öğeleri silme (öğesi Kaldır)
Dosya ve klasörleri silmek için kullanın **Kaldır öğesini** cmdlet'i. Windows PowerShell cmdlet'leri gibi **Kaldır öğesini**, yapabilir önemli, geri alınamaz değişiklikleri genellikle ister onaylama için kendi komutları girdiğinizde. Örneğin, kaldırmayı denerseniz **New.Directory** klasörü, dosyaları içeren klasör için komutu onaylamanız istenir:

```
PS> Remove-Item C:\New.Directory

Confirm
The item at C:\temp\New.Directory has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
 sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

Çünkü **Evet** klasör ve dosyaları, basın silmek için varsayılan yanıt **Enter** anahtarı. Onaylama olmadan klasörü kaldırmak üzere kullanın **-Recurse** parametresi.

```
PS> Remove-Item C:\temp\New.Directory -Recurse
```

### <a name="executing-items-invoke-item"></a>Yürütülen öğeleri (çağırma öğe)
Windows PowerShell kullanan **Invoke-Item** bir dosya veya klasör için varsayılan bir eylem gerçekleştirmek için cmdlet. Bu varsayılan eylem, kayıt defterinde varsayılan uygulama işleyicisi tarafından belirlenir; Dosya Gezgini'nde öğe çift tıklarsanız gibi etkisi aynıdır.

Örneğin, aşağıdaki komutu çalıştırın varsayın:

```
PS> Invoke-Item C:\WINDOWS
```

C: bulunan bir Explorer penceresi\\Windows görüntülenirse, yalnızca C: tıklattığınız sanki\\Windows klasörü.

Çağırmayı varsa **Boot.ini** dosyasını, Windows Vista önce bir sistemde:

```
PS> Invoke-Item C:\boot.ini
```

Boot.ini dosyası, .ini dosya türü Notepad ile ilişkili ise, Not Defteri'nde açılır.

