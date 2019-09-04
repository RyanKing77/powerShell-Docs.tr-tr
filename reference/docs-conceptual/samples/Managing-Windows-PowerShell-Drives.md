---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: Windows PowerShell Sürücülerini Yönetme
ms.openlocfilehash: 5d1aba459caeaab2542e17e74534da6713b0faa9
ms.sourcegitcommit: 02eed65c526ef19cf952c2129f280bb5615bf0c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70215515"
---
# <a name="managing-windows-powershell-drives"></a>Windows PowerShell Sürücülerini Yönetme

*Windows PowerShell sürücüsü* , Windows PowerShell 'de bir dosya sistemi sürücüsü gibi erişebileceğiniz bir veri deposu konumudur. Windows PowerShell sağlayıcıları dosya sistemi sürücüleri (C: ve D:), kayıt defteri sürücüleri (HKCU: ve HKLM:) ve sertifika sürücüsü (CERT:) dahil olmak üzere sizin için bazı sürücüler oluşturur ve kendi Windows PowerShell sürücülerinizi oluşturabilirsiniz. Bu sürücüler çok kullanışlıdır, ancak yalnızca Windows PowerShell 'de kullanılabilir. Dosya Gezgini veya cmd. exe gibi diğer Windows araçlarını kullanarak bunlara erişemezsiniz.

Windows PowerShell, Windows PowerShell sürücüleriyle çalışan komutlar için ad, **PSDrive**' u kullanır. Windows PowerShell oturumunuzda Windows PowerShell sürücülerinin bir listesi için **Get-PSDrive** cmdlet 'ini kullanın.

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

Ekrandaki sürücüler sisteminizdeki sürücülerle aynı olsa da, liste yukarıda gösterilen **Get-PSDrive** komutunun çıktısına benzer şekilde görünür.

Dosya sistemi sürücüleri, Windows PowerShell sürücülerinin bir alt kümesidir. Dosya sistemi sürücüleri sağlayıcı sütununda FileSystem girişi ile tanımlayabilirsiniz. (Windows PowerShell 'deki dosya sistemi sürücüleri Windows PowerShell dosya sistemi sağlayıcısı tarafından desteklenir.)

**Get-PSDrive** cmdlet 'inin söz dizimini görmek Için, **sözdizimi** parametresine sahip bir **Get-Command** komutu yazın:

```
PS> Get-Command -Name Get-PSDrive -Syntax

Get-PSDrive [[-Name] <String[]>] [-Scope <String>] [-PSProvider <String[]>] [-V
erbose] [-Debug] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-
OutVariable <String>] [-OutBuffer <Int32>]
```

**PSProvider** parametresi yalnızca belirli bir sağlayıcı tarafından desteklenen Windows PowerShell sürücüleri görüntülemenize olanak sağlar. Örneğin, yalnızca Windows PowerShell dosya sağlayıcısı tarafından desteklenen Windows PowerShell sürücülerinin görüntülenmesi için, **PSProvider** parametresine ve **dosya sistemi** değerine sahip bir **Get-PSDrive** komutu yazın:

```
PS> Get-PSDrive -PSProvider FileSystem

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
A          FileSystem    A:\
C          FileSystem    C:\                           ...nd Settings\PowerUser
D          FileSystem    D:\
```

Kayıt defteri kovanlarını temsil eden Windows PowerShell sürücüleri görüntülemek için **PSProvider** parametresini kullanarak yalnızca Windows PowerShell kayıt defteri sağlayıcısı tarafından desteklenen Windows PowerShell sürücüleri görüntülenir:

```
PS> Get-PSDrive -PSProvider Registry

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
HKCU       Registry      HKEY_CURRENT_USER
HKLM       Registry      HKEY_LOCAL_MACHINE
```

Standart konum cmdlet 'lerini Windows PowerShell sürücüleriyle de kullanabilirsiniz:

```
PS> Set-Location HKLM:\SOFTWARE
PS> Push-Location .\Microsoft
PS> Get-Location

Path
----
HKLM:\SOFTWARE\Microsoft
```

## <a name="adding-new-windows-powershell-drives-new-psdrive"></a>Yeni Windows PowerShell sürücüleri ekleme (New-PSDrive)

**New-PSDrive** komutunu kullanarak kendi Windows PowerShell sürücülerinizi ekleyebilirsiniz. **New-PSDrive** komutunun söz dizimini almak Için, **sözdizimi** parametresine sahip **Get-Command** komutunu girin:

```
PS> Get-Command -Name New-PSDrive -Syntax

New-PSDrive [-Name] <String> [-PSProvider] <String> [-Root] <String> [-Descript
ion <String>] [-Scope <String>] [-Credential <PSCredential>] [-Verbose] [-Debug
] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-OutVariable <St
ring>] [-OutBuffer <Int32>] [-WhatIf] [-Confirm]
```

Yeni bir Windows PowerShell sürücüsü oluşturmak için üç parametre sağlamanız gerekir:

- Sürücü için bir ad (geçerli herhangi bir Windows PowerShell adı kullanabilirsiniz)

- PSProvider (dosya sistemi konumları için "FileSystem" ve kayıt defteri konumları için "Registry" kullanın)

- Kök, diğer bir deyişle, yeni sürücünün kökünün yolu

Örneğin, bilgisayarınızdaki Microsoft Office uygulamaları içeren klasöre eşlenen "Office" adlı bir sürücü oluşturabilirsiniz. Örneğin, **C:\\program\\Files\\Microsoft Office OFFICE11**. Sürücüyü oluşturmak için aşağıdaki komutu yazın:

```
PS> New-PSDrive -Name Office -PSProvider FileSystem -Root "C:\Program Files\Microsoft Office\OFFICE11"

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Office     FileSystem    C:\Program Files\Microsoft Offic...
```

> [!NOTE]
> Genel olarak, yollar büyük/küçük harfe duyarlı değildir.

Yeni Windows PowerShell sürücüsüne, adına ve sonuna iki nokta üst üste ( **:** ) kadar tüm Windows PowerShell sürücülerine başvurursunuz.

Bir Windows PowerShell sürücüsü birçok görevi çok daha basit hale getirir. Örneğin, Windows kayıt defterindeki en önemli anahtarların bazılarının çok uzun yolları vardır, bu da erişimi daha kolay ve hatırlayacağınızdır. Kritik yapılandırma bilgileri, **HKEY_LOCAL_MACHINE\\Software\\\\Microsoft\\Windows CurrentVersion**altında bulunur. CurrentVersion kayıt defteri anahtarındaki öğeleri görüntülemek ve değiştirmek için, şunu yazarak bu anahtarda kök olan bir Windows PowerShell sürücüsü oluşturabilirsiniz:

```
PS> New-PSDrive -Name cvkey -PSProvider Registry -Root HKLM\Software\Microsoft\Windows\CurrentVersion

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
cvkey      Registry      HKLM\Software\Microsoft\Windows\...
```

Daha sonra konumu diğer tüm sürücüler gibi **cvkey:** Drive olarak değiştirebilirsiniz:

```
PS> cd cvkey:
```

veya:

```
PS> Set-Location cvkey: -PassThru

Path
----
cvkey:\
```

New-PsDrive cmdlet 'i, yeni sürücüyü yalnızca geçerli Windows PowerShell oturumuna ekler. Windows PowerShell penceresini kapatırsanız yeni sürücü kaybedilir. Bir Windows PowerShell sürücüsünü kaydetmek için, geçerli Windows PowerShell oturumunu dışarı aktarmak için Export-Console cmdlet 'ini kullanın ve ardından içeri aktarmak için PowerShell. exe **Psconsolefile** parametresini kullanın. Ya da yeni sürücüyü Windows PowerShell profilinize ekleyin.

## <a name="deleting-windows-powershell-drives-remove-psdrive"></a>Windows PowerShell sürücüleri (Remove-PSDrive) siliniyor

**Remove-PSDrive** cmdlet 'Ini kullanarak Windows PowerShell 'den sürücüleri silebilirsiniz. **Remove-PSDrive** cmdlet 'i kullanımı kolaydır; belirli bir Windows PowerShell sürücüsünü silmek için Windows PowerShell sürücü adını sağlamanız yeterlidir.

Örneğin, **Office eklediyseniz:** Windows PowerShell sürücüsü, **New-PSDrive** konusunda gösterildiği gibi, şunu yazarak silebilirsiniz:

```powershell
Remove-PSDrive -Name Office
```

**Cvkey** 'yi silmek için: **Yeni-PSDrive** konusunda da gösterilen Windows PowerShell sürücüsü aşağıdaki komutu kullanın:

```powershell
Remove-PSDrive -Name cvkey
```

Bir Windows PowerShell sürücüsünü silmek kolaydır, ancak bu sürücüyü sürücüden siz silemezsiniz. Örneğin:

```
PS> cd office:
PS Office:\> remove-psdrive -name office
Remove-PSDrive : Cannot remove drive 'Office' because it is in use.
At line:1 char:15
+ remove-psdrive  <<<< -name office
```

## <a name="adding-and-removing-drives-outside-windows-powershell"></a>Windows PowerShell dışında sürücü ekleme ve kaldırma

Windows PowerShell, eşlenen ağ sürücüleri, eklenen USB sürücüleri ve **net use** komutu kullanılarak silinen sürücüler de dahil olmak üzere Windows 'da eklenen veya kaldırılan dosya sistemi sürücüleri algılar.Bir Windows komut dosyası sistemi (WSH) betiğinin WScript. NetworkMapNetworkDrive ve **removenetworkdrive** yöntemleri.
