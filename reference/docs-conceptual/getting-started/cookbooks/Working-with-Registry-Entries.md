---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Kayıt Defteri Girdileri ile Çalışma
ms.assetid: fd254570-27ac-4cc9-81d4-011afd29b7dc
ms.openlocfilehash: bffdf80931fc4dc570b584623487077dc5d449dc
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="working-with-registry-entries"></a>Kayıt Defteri Girdileri ile Çalışma

Kayıt defteri girişleri anahtarların özelliklerini ve bu nedenle, doğrudan gözatılamaz olduğundan, bunları ile çalışırken, biraz daha farklı bir yaklaşım uygular gerekir.

### <a name="listing-registry-entries"></a>Kayıt defteri girdileri listeleme

Kayıt defteri girdileri incelemek için birçok farklı yolu vardır. En basit yolu, bir anahtar ile ilişkili özellik adlarının almaktır. Örneğin, kayıt defteri anahtarı girişleri adlarını görmek için **HKEY_LOCAL_MACHINE\\yazılım\\Microsoft\\Windows\\CurrentVersion**, kullanın **Get-öğesi** . Kayıt defteri anahtarlarını bir özellik olması "Özelliği" Genel adı ile kayıt defteri girdileri anahtarındaki bir listesidir. Aşağıdaki komutu özellik özelliğini seçer ve böylece bir listede görüntülenen öğelerin genişletir:

```
PS> Get-Item -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion | Select-Object -ExpandProperty Property
DevicePath
MediaPathUnexpanded
ProgramFilesDir
CommonFilesDir
ProductId
```

Kayıt defteri girdilerini daha okunabilir bir formda görüntülemek için kullanın **Get-ItemProperty**:

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

Windows PowerShell ile ilgili özellikler anahtarı için tüm "PS ile" gibi önek **PSPath**, **PSParentPath**, **PSChildName**, ve **PSProvider** .

Kullanabileceğiniz "**.**" geçerli konuma başvuran gösterimi. Kullanabileceğiniz **Set-Location** değiştirmek için **CurrentVersion** kayıt defteri kapsayıcı ilk:

```powershell
Set-Location -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

Alternatif olarak, yerleşik HKLM PSDrive ile kullanabileceğiniz **Set-Location**:

```powershell
Set-Location -Path hklm:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

Daha sonra "**.**" gösterimini bir tam yol belirtmeden özellikleri listelemek geçerli konumu için:

```
PS> Get-ItemProperty -Path .
...
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
...
```

Yolu genişletme çalışır, aynı, bu konumdan, böylece dosya sisteminde olduğu gibi **ItemProperty** için listeleme **HKLM:\\yazılım\\Microsoft\\Windows \\Yardımcı** kullanarak **Get-ItemProperty-yol... \\Yardımcı**.

### <a name="getting-a-single-registry-entry"></a>Bir tek kayıt defteri girişi alma

Bir kayıt defteri anahtarında belirli bir girdi almak istiyorsanız, birkaç olası yaklaşımlardan birini kullanabilirsiniz. Bu örnek değerini bulur **DevicePath** içinde **HKEY_LOCAL_MACHINE\\yazılım\\Microsoft\\Windows\\CurrentVersion**.

Kullanarak **Get-ItemProperty**, kullanın **yolu** anahtarın adını belirtmek için parametre ve **adı** adını belirtmek için parametresini **DevicePath** girişi.

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
> Ancak **Get-ItemProperty** sahip **filtre**, **INCLUDE**, ve **hariç** parametreleri, özellik adına göre filtre uygulamak için kullanılamaz. Bu parametreler kayıt defteri anahtarlarını başvurmak — öğesi yolları olduğu — ve kayıt defteri girdilerini — öğe özellikleri olduğu.

Başka bir seçenek Reg.exe komut satırı aracını kullanmaktır. Reg.exe ile daha fazla yardım için şunu yazın **reg.exe /?** bir komut isteminde. DevicePath girişi bulmak için aşağıdaki komutta gösterildiği gibi reg.exe kullanın:

```
PS> reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion /v DevicePath

! REG.EXE VERSION 3.0

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
    DevicePath  REG_EXPAND_SZ   %SystemRoot%\inf
```

Aynı zamanda **WshShell COM** bu yöntem karakter gibi içeren kayıt defteri girişi adları veya büyük ikili veri ile çalışmaz ancak bazı kayıt defteri girdilerini de bulunacak nesne "\\"). Özellik adı ile öğe yolu sonuna bir \\ ayırıcı:

```
PS> (New-Object -ComObject WScript.Shell).RegRead("HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DevicePath")
%SystemRoot%\inf
```

### <a name="creating-new-registry-entries"></a>Yeni kayıt defteri girdileri oluşturuluyor

"PowerShellPath" adlı yeni bir giriş eklemek için **CurrentVersion** anahtar, kullanım **yeni ItemProperty** anahtarı, giriş adı ve girdisinin değeri yoluyla. Bu örnekte, biz Windows PowerShell değişkenin değerini sürer **$PSHome**, Windows PowerShell için yükleme dizini yolunu depolar.

Aşağıdaki komutu kullanarak yeni giriş anahtarına ekleyebilirsiniz ve komut ayrıca yeni giriş hakkında bilgi verir:

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

**PropertyType** adı olmalıdır bir **Microsoft.Win32.RegistryValueKind** numaralandırma üyesi aşağıdaki tablodan:

|PropertyType değeri|Anlamı|
|----------------------|-----------|
|İkili|İkili veriler|
|DWord|Geçerli bir Uınt32 bir sayı|
|Dizeyi Genişlet|Dinamik olarak genişletilen ortam değişkenleri içerebilir bir dize|
|MultiString|Çok satırlı bir dize|
|Dize|Herhangi bir dize değeri|
|QWord|8 bayt ikili veri|

> [!NOTE]
> Değer bir dizi belirterek birden fazla konuma bir kayıt defteri girişi ekleyebilirsiniz **yolu** parametre:

```powershell
New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion, HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome
```

Ekleyerek önceden var olan bir kayıt defteri girdisinin değeri kılabilirsiniz **zorla** herhangi bir parametre **yeni ItemProperty** komutu.

### <a name="renaming-registry-entries"></a>Kayıt defteri girdileri yeniden adlandırma

Yeniden adlandırmak için **PowerShellPath** "PSHome," kullanım girişe **yeniden adlandırma ItemProperty**:

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome
```

Yeniden adlandırılmış değerini görüntülemek için ekleme **PassThru** komut parametresi.

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome -passthru
```

### <a name="deleting-registry-entries"></a>Kayıt defteri girişlerini silme

PSHome ve PowerShellPath kayıt defteri girdilerini silmek için kullanın **Kaldır ItemProperty**:

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PSHome
Remove-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath
```