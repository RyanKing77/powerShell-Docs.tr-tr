---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Kayıt Defteri Girdileri ile Çalışma
ms.assetid: fd254570-27ac-4cc9-81d4-011afd29b7dc
ms.openlocfilehash: 8483b6f98739697b24a13055dfffbc7b5bacc2cc
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686813"
---
# <a name="working-with-registry-entries"></a>Kayıt Defteri Girdileri ile Çalışma

Kayıt defteri girdileri tuşunun özelliklerini ve bu nedenle, doğrudan gözatılamaz olduğundan bunlarla çalışırken biraz farklı bir yaklaşım olması gerekir.

### <a name="listing-registry-entries"></a>Kayıt defteri girdileri listeleme

Kayıt defteri girdilerini incelemek için birçok farklı yolu vardır. En basit yolu, bir anahtar ile ilişkili özellik adlarını almaktır. Örneğin, kayıt defteri anahtarı girişleri adlarını görmek için `HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion`, kullanın `Get-Item`. Kayıt defteri anahtarlarını bir özelliğe sahip genel "Özelliği" adı ile kayıt defteri girdileri anahtarında bir listesidir.
Aşağıdaki komut, özellik özelliğini seçer ve böylece bunlar bir listede görüntülenen öğelerin genişletir:

```powershell
Get-Item -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion |
  Select-Object -ExpandProperty Property
```

```Output
DevicePath
MediaPathUnexpanded
ProgramFilesDir
CommonFilesDir
ProductId
```

Kayıt defteri girdilerini daha okunabilir bir formda görüntülemek için kullanın `Get-ItemProperty`:

```powershell
Get-ItemProperty -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

```Output
PSPath              : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SO
                      FTWARE\Microsoft\Windows\CurrentVersion
PSParentPath        : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SO
                      FTWARE\Microsoft\Windows
PSChildName         : CurrentVersion
PSDrive             : HKLM
PSProvider          : Microsoft.PowerShell.Core\Registry
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
CommonFilesDir      : C:\Program Files\Common Files
ProductId           : 76487-338-1167776-22465
WallPaperDir        : C:\WINDOWS\Web\Wallpaper
MediaPath           : C:\WINDOWS\Media
ProgramFilesPath    : C:\Program Files
PF_AccessoriesName  : Accessories
(default)           :
```

Anahtar için Windows PowerShell ile ilgili özelliklerin tümünü "PS ile" gibi ön ekli **pspath değeri**, **PSParentPath**, **PSChildName**, ve **PSProvider** .

Kullanabileceğiniz `*.*` geçerli konuma başvuran için gösterimi. Kullanabileceğiniz `Set-Location` değiştirmek için **CurrentVersion** kapsayıcı kayıt defteri ilk:

```powershell
Set-Location -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

Alternatif olarak, yerleşik HKLM PSDrive ile kullanabileceğiniz `Set-Location`:

```powershell
Set-Location -Path hklm:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

Ardından `*.*` gösterimi tam bir yol belirtmeden özellikleri listelemek şu anki konum için:

```powershell
Get-ItemProperty -Path .
```

```Output
...
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
...
```

Yolu genişletme çalışır, aynı, bu konumdan, yani, dosya sisteminde çalıştığı gibi **Itemproperty** için listeleme `HKLM:\SOFTWARE\Microsoft\Windows\Help` kullanarak `Get-ItemProperty -Path ..\Help`.

### <a name="getting-a-single-registry-entry"></a>Tek bir kayıt defteri girişi alınırken

Bir kayıt defteri anahtarı içinde belirli bir girdi almak istiyorsanız, birkaç olası yaklaşımlardan birini kullanabilirsiniz. Bu örnekte değerini bulur **DevicePath** içinde `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion`.

Kullanarak `Get-ItemProperty`, kullanın **yolu** anahtarın adını belirtmek için parametre ve **adı** adını belirtmek için parametre **DevicePath** girişi.

```powershell
Get-ItemProperty -Path HKLM:\Software\Microsoft\Windows\CurrentVersion -Name DevicePath
```

```Output
PSPath       : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows\CurrentVersion
PSParentPath : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows
PSChildName  : CurrentVersion
PSDrive      : HKLM
PSProvider   : Microsoft.PowerShell.Core\Registry
DevicePath   : C:\WINDOWS\inf
```

Bu komut, standart Windows PowerShell özellikleri döndürür. yanı sıra **DevicePath** özelliği.

> [!NOTE]
> Ancak `Get-ItemProperty` sahip **filtre**, **Ekle**, ve **hariç** parametreleri, özellik adına göre filtre uygulamak için kullanılamaz. Bu parametreleri öğe yolları ve kayıt defteri girişleri kayıt defteri anahtarları için bakın. Öğe özellikleri olan kayıt defteri girdileri.

Başka bir seçenek Reg.exe komut satırı aracını kullanmaktır. Reg.exe ile daha fazla yardım için şunu yazın `reg.exe /?` bir komut isteminde. Reg.exe DevicePath giriş bulmak için aşağıdaki komutta gösterildiği gibi kullanın:

```powershell
reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion /v DevicePath
```

```Output
! REG.EXE VERSION 3.0

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
    DevicePath  REG_EXPAND_SZ   %SystemRoot%\inf
```

Ayrıca **WshShell** bu yöntem, büyük ikili veri gibi karakterler kayıt defteri girişi adları ile veya çalışmıyor olsa da, bazı kayıt defteri girdilerini bulmak için de COM nesnesi "\\"). Öğe yolu ile özellik adının sonuna bir \\ ayırıcı:

```powershell
(New-Object -ComObject WScript.Shell).RegRead("HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DevicePath")
```

```Output
%SystemRoot%\inf
```

### <a name="setting-a-single-registry-entry"></a>Tek bir kayıt defteri girdisi ayarlama

Belirli bir girdi kayıt defteri anahtarında değiştirmek istiyorsanız, birkaç olası yaklaşımlardan birini kullanabilirsiniz. Bu örnek **yolu** altında girdisi `HKEY_CURRENT_USER\Environment`. **Yolu** giriş yürütülebilir dosyaları nerede bulacağını belirler.

1. Geçerli değerini almak **yolu** girişini kullanarak `Get-ItemProperty`.
2. İle ayırarak, yeni değer eklemek bir `;`.
3. Kullanım `Set-ItemProperty` belirtilen anahtar, giriş adı ve kayıt defteri girişini değiştirmek için değer.

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path += ";C:\src\bin\"
Set-ItemProperty -Path HKCU:\Environment -Name Path -Value $newpath
```

> [!NOTE]
> Ancak `Set-ItemProperty` sahip **filtre**, **Ekle**, ve **hariç** parametreleri, özellik adına göre filtre uygulamak için kullanılamaz. Bu parametreler kayıt defteri anahtarlarını başvuran — öğe yolları olduğu — ve kayıt defteri girdilerini — öğesi özellikleri olan.

Başka bir seçenek Reg.exe komut satırı aracını kullanmaktır. Reg.exe ile daha fazla yardım için şunu yazın **reg.exe /?**
bir komut isteminde.

Aşağıdaki örnek değişiklikleri **yolu** yukarıdaki örnekte eklenen yolun kaldırarak girişi.
`Get-ItemProperty` öğesinden döndürülen dizeyi ayrıştırmak zorunda kalmamak için geçerli değerini almak için kullanılır `reg query`. **SubString** ve **lastIndexOf** eklenen son yolunu almak için kullanılan yöntemleri **yolu** girişi.

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path.SubString(0, $value.Path.LastIndexOf(';'))
reg add HKCU\Environment /v Path /d $newpath /f
```

```Output
The operation completed successfully.
```

### <a name="creating-new-registry-entries"></a>Yeni kayıt defteri girdileri oluşturuluyor

"PowerShellPath" adlı yeni bir giriş eklemek için **CurrentVersion** anahtar, kullanım `New-ItemProperty` yoluyla anahtar, giriş adı ve giriş değeri. Bu örnekte, biz Windows PowerShell değişkeninin değeri sürer `$PSHome`, Windows PowerShell için yükleme dizini yolunu depolar.

Aşağıdaki komutu kullanarak yeni giriş anahtarı ekleyebilirsiniz ve komut ayrıca yeni giriş hakkındaki bilgileri döndürür:

```powershell
New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome
```

```Output
PSPath         : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
PSParentPath   : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows
PSChildName    : CurrentVersion
PSDrive        : HKLM
PSProvider     : Microsoft.PowerShell.Core\Registry
PowerShellPath : C:\Program Files\Windows PowerShell\v1.0
```

**PropertyType** adı olmalıdır bir **Microsoft.Win32.RegistryValueKind** numaralandırma üyesi aşağıdaki tabloda:

|PropertyType değeri|Anlamı|
|----------------------|-----------|
|İkili|İkili veriler|
|DWord|Geçerli bir UInt32 bir sayı|
|Dizeyi Genişlet|Dinamik olarak genişletilen ortam değişkenleri içerebilir bir dize|
|MultiString|Çok satırlı string|
|Dize|Herhangi bir dize değeri|
|QWord|8 bayt ikili veri|

> [!NOTE]
> Bir dizi değerlerini belirterek, birden fazla konuma bir kayıt defteri girişi ekleyebilirsiniz **yolu** parametresi:

```powershell
New-ItemProperty -Name PowerShellPath -PropertyType String -Value $PSHome `
  -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion, HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

Önceden var olan bir kayıt defteri girdisinin değeri ekleyerek de kılabilirsiniz **zorla** herhangi bir parametre `New-ItemProperty` komutu.

### <a name="renaming-registry-entries"></a>Kayıt defteri girdileri yeniden adlandırma

Yeniden adlandırmak için **PowerShellPath** "PSHome," kullanım girişe `Rename-ItemProperty`:

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome
```

Yeniden adlandırılan değerini görüntülemek için Ekle **PassThru** komut parametresi.

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome -passthru
```

### <a name="deleting-registry-entries"></a>Kayıt defteri girdileri silme

PSHome ve PowerShellPath kayıt defteri girdileri silmek için kullanın `Remove-ItemProperty`:

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PSHome
Remove-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath
```
