---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Öğeleri Doğrudan İşleme
ms.assetid: 8cbd4867-917d-41ea-9ff0-b8e765509735
ms.openlocfilehash: 688f9194bd16793331325999c69e88df3e94c976
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405954"
---
# <a name="manipulating-items-directly"></a>Öğeleri Doğrudan İşleme

Dosyaları ve klasörleri, dosya sistemi sürücüleri ve Windows PowerShell kayıt defteri sürücülere kayıt defteri anahtarları gibi Windows PowerShell sürücülerini gördüğünüz öğeleri adlı *öğeleri* Windows PowerShell'de. İsim öğesi onlarla çalışmak için cmdlet'leri sahip **öğesi** adlarında.

Çıkışı **Get-Command - isim öğesi** komut, dokuz Windows PowerShell öğe cmdlet'leri olduğunu gösterir.

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

### <a name="creating-new-items-new-item"></a>Yeni öğeler (yeni öğe) oluşturma

Dosya sisteminde yeni bir öğe oluşturmak için kullanın **yeni öğe** cmdlet'i. Dahil **yolu** öğesi yolu bir parametreyle ve **Itemtype** parametresi "dosya" veya "dizin" değerine sahip.

Örneğin, adında yeni bir dizin oluşturmak için "C: New.Directory"in\\Temp Dizini, türü:

```
PS> New-Item -Path c:\temp\New.Directory -ItemType Directory

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18  11:29 AM            New.Directory
```

Bir dosya oluşturmak için değerini değiştirmek **Itemtype** "file" parametresi. Örneğin, New.Directory dizinde "Dosya1.ref" adlı bir dosya oluşturmak için şunu yazın:

```
PS> New-Item -Path C:\temp\New.Directory\file1.txt -ItemType file

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp\New.Directory

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-18  11:44 AM          0 file1
```

Yeni bir kayıt defteri anahtarı oluşturmak için aynı tekniği kullanabilirsiniz. Aslında, bir kayıt defteri anahtarı bir anahtar yalnızca Windows kayıt defteri öğesi türünde olduğu için oluşturmak çok kolaydır. (Kayıt defteri girişlerinin öğesi *özellikleri*.) Örneğin, CurrentVersion alt anahtarda "_Test" adlı bir anahtar oluşturmak için şunu yazın:

```
PS> New-Item -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion_Test

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Micros
oft\Windows\CurrentVersion

SKC  VC Name                           Property
---  -- ----                           --------
  0   0 _Test                          {}
```

Bir kayıt defteri yolu yazarken, iki nokta üst üste eklediğinizden emin olun (**:**) Windows PowerShell sürücüsü adları, HKLM: ve HKCU:. İki nokta üst üste, Windows PowerShell yolunda sürücü adı algılamaz.

### <a name="why-registry-values-are-not-items"></a>Neden kayıt defteri değerlerini öğeler değil

Kullanırken **Get-Childıtem** cmdlet'i bir kayıt defteri anahtarında öğeleri bulmak için hiçbir zaman gerçek kayıt defteri girdileri veya değerlerine görürsünüz.

Örneğin, kayıt defteri anahtarı **HKEY_LOCAL_MACHINE\\yazılım\\Microsoft\\Windows\\CurrentVersion\\çalıştırma** genellikle birkaç kayıt defteri girdilerini içeren temsil eden sistem başlatıldığında çalıştırılan uygulamalar.

Ancak, kullandığınızda **Get-Childıtem** anahtarında alt öğelerini aramak için görürsünüz olan **OptionalComponents** anahtarının alt anahtar:

```
PS> Get-ChildItem HKLM:\Software\Microsoft\Windows\CurrentVersion\Run

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\Micros
oft\Windows\CurrentVersion\Run
SKC  VC Name                           Property
---  -- ----                           --------
  3   0 OptionalComponents             {}
```

Kayıt defteri girdileri öğeleri olarak ele almanız kullanışlı olsa da, bir kayıt defteri girişi için bir yol benzersiz olmasını sağlar, şekilde belirtemezsiniz. Yol gösterimi adlı kayıt defteri alt anahtarı arasında ayrım yapmaz **çalıştırma** ve **(varsayılan)** kayıt defteri girişini **çalıştırma** alt. Ayrıca, kayıt defteri girişi adları ters eğik çizgi karakteri içerdiğinden (**\\**), kayıt defteri girdileri adlı bir kayıt defteri girişi ayırmak için bir yol gösterimi kullanılamadı sonra öğeleri olsaydı  **Windows\\CurrentVersion\\çalıştırma** yolda bulunan alt.

### <a name="renaming-existing-items-rename-item"></a>Var olan öğeleri (öğeyi yeniden adlandır) yeniden adlandırma

Bir dosya veya klasör adını değiştirmek için kullanın **öğeyi yeniden adlandır** cmdlet'i. Aşağıdaki komut adını değiştirir **Dosya1.ref** dosyasını **fileOne.txt**.

```powershell
Rename-Item -Path C:\temp\New.Directory\file1.txt fileOne.txt
```

**Öğeyi yeniden adlandır** cmdlet'i, bir dosya veya klasör adını değiştirebilirsiniz, ancak bu öğeyi taşıyamazsınız. Dosyayı New.Directory dizinden Temp dizinine taşımak deneme için aşağıdaki komutu başarısız olur.

```
PS> Rename-Item -Path C:\temp\New.Directory\fileOne.txt c:\temp\fileOne.txt
Rename-Item : Cannot rename because the target specified is not a path.
At line:1 char:12
+ Rename-Item  <<<< -Path C:\temp\New.Directory\fileOne c:\temp\fileOne.txt
```

### <a name="moving-items-move-item"></a>(Öğe taşıma) öğeleri taşıma

Bir dosyayı veya klasörü taşı için kullanın **taşıma öğesi** cmdlet'i.

Örneğin, aşağıdaki komutu C: New.Directory dizini taşır\\C: sürücüsünün kökündeki geçici dizini. Öğesi taşındığını doğrulamak için dahil **PassThru** parametresinin **taşıma öğesi** cmdlet'i. Olmadan **Passthru**, **taşıma öğesi** cmdlet'i tüm sonuçları görüntülenmeyecek.

```
PS> Move-Item -Path C:\temp\New.Directory -Destination C:\ -PassThru

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18  12:14 PM            New.Directory
```

### <a name="copying-items-copy-item"></a>Öğe (Copy-Item) kopyalama

Diğer Kabuk kopyalama işlemlerine biliyorsanız, davranışını bulabileceğiniz **Copy-Item** olağan dışı olması için Windows PowerShell cmdlet'i. Bir öğeyi bir konumdan diğerine kopyaladığınızda Copy-Item varsayılan olarak, içeriğinin kopyalamaz.

Örneğin, kopyalama, **New.Directory** dizininden C: sürücüsü dışında C:\\geçici dizin, komut başarılı, ancak New.Directory dizindeki dosyaların kopyalanmaz.

```powershell
Copy-Item -Path C:\New.Directory -Destination C:\temp
```

İçeriğini görüntülediğinizde **C:\\temp\\New.Directory**, hiçbir dosya içerdiği bulabilirsiniz:

```
PS> Get-ChildItem -Path C:\temp\New.Directory
PS>
```

Neden olmayan **Copy-Item** cmdlet'i kopyalayın içeriğini yeni konuma?

**Copy-Item** cmdlet'i genel olacak şekilde tasarlanmıştır; yalnızca dosya ve klasörleri kopyalama için değil. Ayrıca, hatta dosya ve klasörleri kopyalama, yalnızca kapsayıcı ve içindeki öğelerin kopyalama isteyebilirsiniz.

Tüm içeriğini bir klasöre kopyalamak için eklemeniz **Recurse** parametresinin **Copy-Item** cmdlet'inde komutu. Dizin içeriğini olmadan kopyaladıysanız, ekleme **zorla** boş klasörün üzerine olanak tanıyan bir parametre.

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

### <a name="deleting-items-remove-item"></a>Öğeleri silme (öğe Kaldır)

Dosya ve klasörleri silmek için kullanın **Kaldır öğesini** cmdlet'i. Windows PowerShell cmdlet'leri gibi **Kaldır öğesini**önemli olun, geri alınamaz değişiklikleri genellikle ister onay kendi komutları girdiğinizde. Örneğin kaldırmayı denerseniz, **New.Directory** klasör, dosya klasör içerdiği için komutu onaylamanız istenir:

```
PS> Remove-Item C:\New.Directory

Confirm
The item at C:\temp\New.Directory has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
 sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

Çünkü **Evet** klasör ve dosyaları, tuşuna silmek için varsayılan yanıt **Enter** anahtarı. Onaylama olmadan klasörü kaldırmak için **-Recurse** parametresi.

```powershell
Remove-Item C:\temp\New.Directory -Recurse
```

### <a name="executing-items-invoke-item"></a>Yürütülen öğeleri (Invoke-öğe)

Windows PowerShell kullanan **Invoke-Item** bir dosya veya klasör için bir varsayılan eylem gerçekleştirmek için cmdlet. Bu varsayılan eylem, kayıt defterindeki varsayılan uygulama işleyicisi tarafından belirlenir; öğenin dosya Gezgini'nde çift tıklayın, etkisi aynıdır.

Örneğin, aşağıdaki komutu çalıştırın varsayalım:

```powershell
Invoke-Item C:\WINDOWS
```

C: bulunan bir Gezgin penceresi\\yalnızca Windows görünür C: tıklattığınız gibi\\Windows klasörü.

Çağırma **Boot.ini** dosyasını, bir sistemde Windows Vista önce:

```powershell
Invoke-Item C:\boot.ini
```

Boot.ini dosyası, .ini dosya türü Notepad ile ilişkili ise, Not Defteri'nde açılır.