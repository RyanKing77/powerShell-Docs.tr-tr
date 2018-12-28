---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Kayıt Defteri Girdileri ile Çalışma
ms.assetid: fd254570-27ac-4cc9-81d4-011afd29b7dc
ms.openlocfilehash: bffdf80931fc4dc570b584623487077dc5d449dc
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405912"
---
# <a name="working-with-registry-entries"></a>Kayıt Defteri Girdileri ile Çalışma

Kayıt defteri girdileri tuşunun özelliklerini ve bu nedenle, doğrudan gözatılamaz olduğundan bunlarla çalışırken biraz farklı bir yaklaşım olması gerekir.

### <a name="listing-registry-entries"></a>Kayıt defteri girdileri listeleme

Kayıt defteri girdilerini incelemek için birçok farklı yolu vardır. En basit yolu, bir anahtar ile ilişkili özellik adlarını almaktır. Örneğin, kayıt defteri anahtarı girişleri adlarını görmek için **HKEY_LOCAL_MACHINE\\yazılım\\Microsoft\\Windows\\CurrentVersion**, kullanın **Get-öğe** . Kayıt defteri anahtarlarını bir özelliğe sahip genel "Özelliği" adı ile kayıt defteri girdileri anahtarında bir listesidir. Aşağıdaki komut, özellik özelliğini seçer ve böylece bunlar bir listede görüntülenen öğelerin genişletir:

```
PS> Get-Item -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion | Select-Object -ExpandProperty Property
DevicePath
MediaPathUnexpanded
ProgramFilesDir
CommonFilesDir
ProductId
```

Kayıt defteri girdilerini daha okunabilir bir formda görüntülemek için kullanın **Get-Itemproperty**:

```
PS> Get-ItemProperty -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion

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

Kullanabileceğiniz "**.**" için geçerli konuma başvuran gösterimi. Kullanabileceğiniz **Set-Location** değiştirmek için **CurrentVersion** kapsayıcı kayıt defteri ilk:

```powershell
Set-Location -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

Alternatif olarak, yerleşik HKLM PSDrive ile kullanabileceğiniz **Set-Location**:

```powershell
Set-Location -Path hklm:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

Daha sonra "**.**" gösterim tam bir yol belirtmeden özellikleri listelemek şu anki konum için:

```
PS> Get-ItemProperty -Path .
...
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
...
```

Yolu genişletme çalışır, aynı, bu konumdan, yani, dosya sisteminde çalıştığı gibi **Itemproperty** için listeleme **HKLM:\\yazılım\\Microsoft\\Windows \\Yardımcı** kullanarak **Itemproperty Get-yolu... \\Yardımcı**.

### <a name="getting-a-single-registry-entry"></a>Tek bir kayıt defteri girişi alınırken

Bir kayıt defteri anahtarı içinde belirli bir girdi almak istiyorsanız, birkaç olası yaklaşımlardan birini kullanabilirsiniz. Bu örnekte değerini bulur **DevicePath** içinde **HKEY_LOCAL_MACHINE\\yazılım\\Microsoft\\Windows\\CurrentVersion**.

Kullanarak **Get-Itemproperty**, kullanın **yolu** anahtarın adını belirtmek için parametre ve **adı** adını belirtmek için parametre **DevicePath** girişi.

```
PS> Get-ItemProperty -Path HKLM:\Software\Microsoft\Windows\CurrentVersion -Name DevicePath

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
> Ancak **Get-Itemproperty** sahip **filtre**, **Ekle**, ve **hariç** parametreleri, özellik adına göre filtre uygulamak için kullanılamaz. Bu parametreler kayıt defteri anahtarlarını başvuran — öğe yolları olduğu — ve kayıt defteri girdilerini — öğesi özellikleri olan.

Başka bir seçenek Reg.exe komut satırı aracını kullanmaktır. Reg.exe ile daha fazla yardım için şunu yazın **reg.exe /?** bir komut isteminde. Reg.exe DevicePath giriş bulmak için aşağıdaki komutta gösterildiği gibi kullanın:

```
PS> reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion /v DevicePath

! REG.EXE VERSION 3.0

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
    DevicePath  REG_EXPAND_SZ   %SystemRoot%\inf
```

Ayrıca **WshShell COM** büyük ikili veri gibi karakterler kayıt defteri girişi adları ile veya bu yöntem çalışmaz ancak bazı kayıt defteri girdilerini de bulunacak nesne "\\"). Öğe yolu ile özellik adının sonuna bir \\ ayırıcı:

```
PS> (New-Object -ComObject WScript.Shell).RegRead("HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DevicePath")
%SystemRoot%\inf
```

### <a name="creating-new-registry-entries"></a>Yeni kayıt defteri girdileri oluşturuluyor

"PowerShellPath" adlı yeni bir giriş eklemek için **CurrentVersion** anahtar, kullanım **yeni Itemproperty** yoluyla anahtar, giriş adı ve giriş değeri. Bu örnekte, biz Windows PowerShell değişkeninin değeri sürer **$PSHome**, Windows PowerShell için yükleme dizini yolunu depolar.

Aşağıdaki komutu kullanarak yeni giriş anahtarı ekleyebilirsiniz ve komut ayrıca yeni giriş hakkındaki bilgileri döndürür:

```
PS> New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome

PSPath         : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWAR
                 E\Microsoft\Windows\CurrentVersion
PSParentPath   : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWAR
                 E\Microsoft\Windows
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
New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion, HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome
```

Önceden var olan bir kayıt defteri girdisinin değeri ekleyerek de kılabilirsiniz **zorla** herhangi bir parametre **yeni Itemproperty** komutu.

### <a name="renaming-registry-entries"></a>Kayıt defteri girdileri yeniden adlandırma

Yeniden adlandırmak için **PowerShellPath** "PSHome," kullanım girişe **yeniden adlandırma Itemproperty**:

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome
```

Yeniden adlandırılan değerini görüntülemek için Ekle **PassThru** komut parametresi.

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome -passthru
```

### <a name="deleting-registry-entries"></a>Kayıt defteri girdileri silme

PSHome ve PowerShellPath kayıt defteri girdileri silmek için kullanın **Remove-Itemproperty**:

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PSHome
Remove-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath
```