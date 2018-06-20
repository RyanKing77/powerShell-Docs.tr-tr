---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Windows PowerShell Sürücülerini Yönetme
ms.assetid: bd809e38-8de9-437a-a250-f30a667d11b4
ms.openlocfilehash: cfc5418e9d2efb1a786817e1b941d75e22291742
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30951877"
---
# <a name="managing-windows-powershell-drives"></a>Windows PowerShell Sürücülerini Yönetme

A *Windows PowerShell sürücüsü* Windows PowerShell'de dosya sistemi sürücü gibi erişmek için bir veri deposu konumudur. Dosya sistemi (C: ve D:), kayıt defteri sürücüler gibi Windows PowerShell sağlayıcıları bazı sürücüler için oluşturduğunuz sürücüler (HKCU: ve HKLM:) ve sertifika sürücüsü (Cert:), ve kendi Windows PowerShell sürücü oluşturabilirsiniz. Bu sürücüler oldukça faydalıdır, ancak bunlar yalnızca Windows PowerShell içinde kullanılabilir. Bunları dosya Gezgini veya Cmd.exe gibi diğer Windows araçlarını kullanarak erişemez.

Windows PowerShell kullanan isim **PSDrive**, Windows PowerShell ile çalışmayı komutlar için sürücüler. Windows PowerShell listesini Windows PowerShell oturumunuzda sürücüler için kullanmak **Get-PSDrive** cmdlet'i.

```
PS> Get-PSDrive

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
A          FileSystem    A:\
Alias      Alias
C          FileSystem    C:\                                 ...And Settings\me
cert       Certificate   \
D          FileSystem    D:\
Env        Environment
Function   Function
HKCU       Registry      HKEY_CURRENT_USER
HKLM       Registry      HKEY_LOCAL_MACHINE
Variable   Variable
```

Sisteminizde sürücülerle görüntü sürücüleri farklılık rağmen listenin çıkışına şuna benzer **Get-PSDrive** yukarıda gösterilen komutu.

Dosya sistemi sürücülerine Windows PowerShell sürücülerinin bir alt kümesidir. Dosya sistemi sürücülerine sağlayıcısı sütunundaki FileSystem girdi tarafından tanımlayabilirsiniz. (Dosya sistemi sürücülerine Windows PowerShell'de Windows PowerShell FileSystem sağlayıcı tarafından desteklenir.)

Söz dizimi görmek için **Get-PSDrive** cmdlet, bir **Get-Command** komutunu **sözdizimi** parametre:

```
PS> Get-Command -Name Get-PSDrive -Syntax

Get-PSDrive [[-Name] <String[]>] [-Scope <String>] [-PSProvider <String[]>] [-V
erbose] [-Debug] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-
OutVariable <String>] [-OutBuffer <Int32>]
```

**PSProvider** görüntülemek için Windows PowerShell sürücüleri yalnızca parametre sağlar, belirli bir sağlayıcı tarafından desteklenir. Örneğin, yalnızca Windows PowerShell dosya sistemi sağlayıcısı tarafından desteklenen Windows PowerShell sürücüleri görüntülemek için şunu yazın bir **Get-PSDrive** komutunu **PSProvider** parametresi ve  **Dosya sistemi** değeri:

```
PS> Get-PSDrive -PSProvider FileSystem

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
A          FileSystem    A:\
C          FileSystem    C:\                           ...nd Settings\PowerUser
D          FileSystem    D:\
```

Kayıt defteri kovanları temsil eden Windows PowerShell sürücüleri görüntülemek için kullanın **PSProvider** parametresi yalnızca Windows PowerShell sürücüleri görüntülemek için Windows PowerShell kayıt defteri sağlayıcı tarafından desteklenir:

```
PS> Get-PSDrive -PSProvider Registry

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
HKCU       Registry      HKEY_CURRENT_USER
HKLM       Registry      HKEY_LOCAL_MACHINE
```

Windows PowerShell sürücülerle standart konumu cmdlet'leri de kullanabilirsiniz:

```
PS> Set-Location HKLM:\SOFTWARE
PS> Push-Location .\Microsoft
PS> Get-Location

Path
----
HKLM:\SOFTWARE\Microsoft
```

### <a name="adding-new-windows-powershell-drives-new-psdrive"></a>Yeni Windows PowerShell ekleme (PSDrive yeni) sürücüleri

Kullanarak kendi Windows PowerShell sürücüleri ekleyebilirsiniz **yeni PSDrive** komutu. Sözdizimi almak için **yeni PSDrive** komutu, girin **Get-Command** komutunu **sözdizimi** parametre:

```
PS> Get-Command -Name New-PSDrive -Syntax

New-PSDrive [-Name] <String> [-PSProvider] <String> [-Root] <String> [-Descript
ion <String>] [-Scope <String>] [-Credential <PSCredential>] [-Verbose] [-Debug
] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-OutVariable <St
ring>] [-OutBuffer <Int32>] [-WhatIf] [-Confirm]
```

Yeni bir Windows PowerShell sürücüsü oluşturmak için üç parametre girmeniz gerekir:

- (Herhangi bir geçerli Windows PowerShell adı kullanabilirsiniz) sürücü için bir ad

- PSProvider (dosya sistemi konumları için "FileSystem" ve "Kayıt" kayıt defteri konumları için kullanın)

- Kök, diğer bir deyişle, yeni sürücüsünün kök yolu

Örneğin, ", bilgisayarınızda Microsoft Office uygulamaları gibi içeren klasöre eşlenen Office" adlı bir sürücüsü oluşturabilirsiniz **C:\\Program Files\\Microsoft Office\\11**. Sürücü oluşturmak için aşağıdaki komutu yazın:

```
PS> New-PSDrive -Name Office -PSProvider FileSystem -Root "C:\Program Files\Micr
osoft Office\OFFICE11"

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Office     FileSystem    C:\Program Files\Microsoft Offic...
```

> [!NOTE]
> Genel olarak, yolları büyük küçük harfe duyarlı değildir.

Tüm Windows PowerShell sürücüler--üste adını kullanarak yaptığınız gibi yeni bir Windows PowerShell sürücüye bakın (**:**).

Bir Windows PowerShell sürücüsü birçok görevi daha kolay hale getirebilirsiniz. Örneğin, Windows kayıt defterinde en önemli unsurlardan bazılarının erişimi sıkıcı ve unutmayın zor hale aşırı uzun yolları vardır. Önemli yapılandırma bilgilerini bulunduğu altında **HKEY_LOCAL_MACHINE\\yazılım\\Microsoft\\Windows\\CurrentVersion**. Görüntülemek ve CurrentVersion kayıt defteri anahtarında öğeleri değiştirmek için yazarak bu anahtar kökü belirtilmiş bir Windows PowerShell sürücüsü oluşturabilirsiniz:

```
PS> New-PSDrive -Name cvkey -PSProvider Registry -Root HKLM\Software\Microsoft\W
indows\CurrentVersion

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
cvkey      Registry      HKLM\Software\Microsoft\Windows\...
```

Daha sonra bir konuma değiştirebilirsiniz **cvkey:** sürücü, başka bir sürücü gibi:''

`PS> cd cvkey:`

veya:

```
PS> Set-Location cvkey: -PassThru

Path
----
cvkey:\
```

Yeni PsDrive cmdlet yeni bir sürücüye yalnızca geçerli Windows PowerShell oturumuna ekler. Windows PowerShell penceresini kapatın, yeni sürücü kaybolur. Bir Windows PowerShell sürücüsü kaydetmek için geçerli Windows PowerShell oturumu dışarı aktarmak için dışarı aktarma konsol cmdlet'ini kullanın ve PowerShell.exe kullanmak **PSConsoleFile** parametresini kullanarak içe aktarın. Veya Windows PowerShell profiliniz için yeni bir sürücüye ekleyin.

### <a name="deleting-windows-powershell-drives-remove-psdrive"></a>Windows PowerShell silme (Remove-PSDrive) sürücüleri

Kullanarak Windows Powershell'den sürücüleri silebilirsiniz **Kaldır PSDrive** cmdlet'i. **Kaldır PSDrive** cmdlet kullanımı kolaydır; belirli bir Windows PowerShell sürücüsü silmek için yalnızca Windows PowerShell sürücü adı sağlayın.

Örneğin, eklediyseniz **Office:** gösterildiği gibi Windows PowerShell sürücüsü, **yeni PSDrive** konu silebilirsiniz, yazarak:

```powershell
Remove-PSDrive -Name Office
```

Silmek için **cvkey:** Windows PowerShell sürücüsü, ayrıca görünmesini **yeni PSDrive** konu, aşağıdaki komutu kullanın:

```powershell
Remove-PSDrive -Name cvkey
```

Bir Windows PowerShell sürücüsü silmek kolaydır, ancak sürücüde durumdayken silemezsiniz. Örneğin:

```
PS> cd office:
PS Office:\> remove-psdrive -name office
Remove-PSDrive : Cannot remove drive 'Office' because it is in use.
At line:1 char:15
+ remove-psdrive  <<<< -name office
```

### <a name="adding-and-removing-drives-outside-windows-powershell"></a>Ekleme ve kaldırma dış Windows PowerShell sürücüler

Windows PowerShell algılar eklendiğinde veya kaldırıldığında eşlenen ağ sürücülerini, bağlı USB sürücülerin ve kullanarak silinmiş sürücüler dahil olmak üzere Windows dosya sistemi sürücülerine **net kullanım** komut veya  **WScript.NetworkMapNetworkDrive** ve **RemoveNetworkDrive** bir Windows Komut Dosyası Sistemi'ni (WSH) betikten yöntemleri.