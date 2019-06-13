---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Windows PowerShell Sürücülerini Yönetme
ms.openlocfilehash: 32efa282fb787753942e43acab53c7b6eaeb88e3
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030149"
---
# <a name="managing-windows-powershell-drives"></a>Windows PowerShell Sürücülerini Yönetme

A *Windows PowerShell sürücüsünü* gibi Windows PowerShell bir dosya sistemi sürücüsüne erişiminiz bir veri deposu konumdur. Dosya sistemi (C: ve D:), kayıt defteri sürücüler gibi Windows PowerShell sağlayıcıları bazı sürücüler için oluşturduğunuz sürücüler (HKCU: ve HKLM:) ve sertifika sürücü (Cert:), kendi Windows PowerShell sürücülerini de oluşturabilirsiniz. Bu sürücüler oldukça faydalıdır, ancak bunlar yalnızca Windows PowerShell içinde kullanılabilir. Bunları dosya Gezgini veya Cmd.exe gibi diğer Windows araçlarını kullanarak erişemez.

Windows PowerShell kullanan bir isim **PSDrive**, Windows PowerShell ile çalışmayı komutları için sürücüler. Windows PowerShell oturumunuzda bir listesi için Windows PowerShell sürücülerini, kullanın **Get-PSDrive** cmdlet'i.

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

Sisteminizde sürücülerle görüntüsündeki sürücüleri farklı olsa da, listenin çıktısına benzer görünecektir **Get-PSDrive** yukarıda gösterilen komutu.

Dosya sistemi sürücüleri, Windows PowerShell sürücülerini bir alt kümesidir. Dosya sistemi giriş sağlayıcısı sütunda tarafından dosya sistemi sürücüleri tespit edebilirsiniz. (Dosya sistemi sürücüleri Windows PowerShell'de Windows PowerShell dosya sistemi sağlayıcısı tarafından desteklenir.)

Söz dizimi görmek için **Get-PSDrive** cmdlet'i, bir **Get-Command** komutunu **söz dizimi** parametresi:

```
PS> Get-Command -Name Get-PSDrive -Syntax

Get-PSDrive [[-Name] <String[]>] [-Scope <String>] [-PSProvider <String[]>] [-V
erbose] [-Debug] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-
OutVariable <String>] [-OutBuffer <Int32>]
```

**PSProvider** görüntülemek için Windows PowerShell Bu sürücüleri yalnızca parametresi sağlar, belirli bir sağlayıcı tarafından desteklenir. Windows PowerShell dosya sistemi sağlayıcısı tarafından desteklenen Windows PowerShell sürücülerini görüntülemek için örneğin bir **Get-PSDrive** komutunu **PSProvider** parametresi ve  **Dosya sistemi** değeri:

```
PS> Get-PSDrive -PSProvider FileSystem

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
A          FileSystem    A:\
C          FileSystem    C:\                           ...nd Settings\PowerUser
D          FileSystem    D:\
```

Kayıt defteri kovanları temsil eden Windows PowerShell sürücülerini görüntülemek için kullanın **PSProvider** parametre yalnızca, Windows PowerShell sürücülerini görüntülemek için Windows PowerShell ile kayıt defteri sağlayıcı tarafından desteklenir:

```
PS> Get-PSDrive -PSProvider Registry

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
HKCU       Registry      HKEY_CURRENT_USER
HKLM       Registry      HKEY_LOCAL_MACHINE
```

Windows PowerShell'i sürücülerle standart konumu cmdlet'leri de kullanabilirsiniz:

```
PS> Set-Location HKLM:\SOFTWARE
PS> Push-Location .\Microsoft
PS> Get-Location

Path
----
HKLM:\SOFTWARE\Microsoft
```

## <a name="adding-new-windows-powershell-drives-new-psdrive"></a>Yeni Windows PowerShell ekleme (PSDrive yeni) sürücüleri

Kullanarak kendi Windows PowerShell sürücülerini ekleyebilirsiniz **yeni PSDrive** komutu. Sözdizimi almak için **yeni PSDrive** komutu, girin **Get-Command** komutunu **söz dizimi** parametresi:

```
PS> Get-Command -Name New-PSDrive -Syntax

New-PSDrive [-Name] <String> [-PSProvider] <String> [-Root] <String> [-Descript
ion <String>] [-Scope <String>] [-Credential <PSCredential>] [-Verbose] [-Debug
] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-OutVariable <St
ring>] [-OutBuffer <Int32>] [-WhatIf] [-Confirm]
```

Yeni bir Windows PowerShell sürücüsü oluşturmak için üç parametre belirtmeniz gerekir:

- (Herhangi bir geçerli Windows PowerShell adı kullanabilirsiniz) sürücü için bir ad

- ' % S'PSProvider (dosya sistemi konumları için "dosya" ve "Kayıt" kayıt defteri konumları için kullanın)

- Kök, diğer bir deyişle, yeni sürücüsünün kök yolu

Örneğin, ", bilgisayarınızda Microsoft Office uygulamaları gibi içeren klasörle eşlendi Office" adlı bir sürücüsü oluşturabilirsiniz **C:\\Program dosyaları\\Microsoft Office\\11**. Sürücü oluşturmak için aşağıdaki komutu yazın:

```
PS> New-PSDrive -Name Office -PSProvider FileSystem -Root "C:\Program Files\Micr
osoft Office\OFFICE11"

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Office     FileSystem    C:\Program Files\Microsoft Offic...
```

> [!NOTE]
> Genel olarak, yolları büyük küçük harfe duyarlı değildir.

--Üste adına göre tüm Windows PowerShell sürücülerini yaptığınız gibi yeni Windows PowerShell sürücüsüne bakın ( **:** ).

Bir Windows PowerShell sürücüsü, birçok görevi çok daha kolay hale getirebilirsiniz. Örneğin, en önemli Windows kayıt defteri anahtarları erişimi hantal ve hatırlamak zor hale son derece uzun yollar vardır. Önemli yapılandırma bilgileri bulunduğu altında **HKEY_LOCAL_MACHINE\\yazılım\\Microsoft\\Windows\\CurrentVersion**. Görüntüleyip CurrentVersion kayıt defteri anahtarında öğeleri değiştirmek için yazarak bu anahtar kökü belirtilmiş bir Windows PowerShell sürücüsü oluşturabilirsiniz:

```
PS> New-PSDrive -Name cvkey -PSProvider Registry -Root HKLM\Software\Microsoft\W
indows\CurrentVersion

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
cvkey      Registry      HKLM\Software\Microsoft\Windows\...
```

Ardından bir konuma değiştirebilirsiniz **cvkey:** sürücü, başka bir sürücü gibi:''

`PS> cd cvkey:`

veya:

```
PS> Set-Location cvkey: -PassThru

Path
----
cvkey:\
```

New-PsDrive cmdlet'i yeni bir sürücüye yalnızca geçerli Windows PowerShell oturumuna ekler. Windows PowerShell penceresini kapatırsanız yeni sürücü kaybolur. Bir Windows PowerShell sürücüsü kaydetmek için geçerli Windows PowerShell oturumunda dışarı aktarmak için konsol içi dışarı aktarma cmdlet'ini kullanın ve ardından PowerShell.exe **PSConsoleFile** parametresini kullanarak içe aktarın. Veya Windows PowerShell profiliniz için yeni bir sürücüye ekleyin.

## <a name="deleting-windows-powershell-drives-remove-psdrive"></a>Windows PowerShell siliniyor (Remove-PSDrive) sürücüleri

Kullanarak Windows Powershell'den sürücüleri silebilirsiniz **Remove-PSDrive** cmdlet'i. **Remove-PSDrive** cmdlet'i kullanımı kolay; belirli bir Windows PowerShell sürücüsü silmek için yalnızca Windows PowerShell sürücüsü ad sağlayın.

Örneğin, eklediğiniz **Office:** Windows PowerShell sürücüsü, gösterildiği gibi **yeni PSDrive** konu silebilirsiniz, yazarak:

```powershell
Remove-PSDrive -Name Office
```

Silinecek **cvkey:** Windows PowerShell sürücüsü de görünmesini **yeni PSDrive** konu, aşağıdaki komutu kullanın:

```powershell
Remove-PSDrive -Name cvkey
```

Bir Windows PowerShell sürücüsü silmek kolaydır, ancak sürücü çalışırken silinemiyor. Örneğin:

```
PS> cd office:
PS Office:\> remove-psdrive -name office
Remove-PSDrive : Cannot remove drive 'Office' because it is in use.
At line:1 char:15
+ remove-psdrive  <<<< -name office
```

## <a name="adding-and-removing-drives-outside-windows-powershell"></a>Ekleme ve kaldırma dışında Windows PowerShell sürücüsü

Windows PowerShell algılar eklendiğinde veya kaldırıldığında, eşlenen ağ sürücülerini, bağlı USB sürücülerin ve kullanarak silinen sürücüler dahil olmak üzere, Windows dosya sistemi sürücüleri **net kullanım** komut veya  **WScript.NetworkMapNetworkDrive** ve **RemoveNetworkDrive** bir Windows komut dosyası sistemi (WSH) komut dosyasındaki yöntemleri.
