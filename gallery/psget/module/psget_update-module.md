---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: Galeri, powershell, cmdlet, psget
title: Güncelleştirme Modülü
ms.openlocfilehash: 89b0111eda4421606843f108dca90519b2c9379e
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="update-module"></a>Güncelleştirme Modülü

İndirir ve yerel bilgisayarda bir çevrimiçi galeriden belirtilen modülleri en yeni sürümünü yükler.

## <a name="description"></a>Açıklama

Güncelleştirme modülü cmdlet daha yeni bir çevrimiçi galeriden yerel bilgisayarda yükle-Module çalıştırarak yüklü olduğu bir Windows PowerShell modülü sürümü yükler.

Gerekli sürümü belirtmediğiniz sürece varsayılan olarak, en yeni sürümünü çevrimiçi galerisinde kullanılabilir Belirtilen modül, yüklenir. Modül adı belirterek varolan, yüklü bir modül güncelleştirebilirsiniz; Güncelleştirme modülü $env arar: PSModulePath güncelleştirmek istediğiniz modülü için.

Name parametresi olmadan güncelleştirme modülünü çalıştıran yerel bilgisayarda güncelleştirilebilir olan tüm modülleri güncelleştirir.

### <a name="notes"></a>Notlar

- Bu cmdlet, Windows PowerShell 3.0 veya sonraki sürümleri Windows PowerShell, Windows 7 veya Windows 2008 R2 ve Windows'un sonraki sürümleri üzerinde çalışır.
- Yükleme modülünü kullanarak ad parametresiyle belirttiğiniz Modülü yüklü değil, bir hata oluşur. Yalnızca, Update-Module yükle-Module çalıştırarak çevrimiçi galeriden yüklü modülleri çalıştırabilirsiniz.
- Kullanımda olan ikili dosyaları güncelleştirmek güncelleştirme modülü çalışırsa, güncelleştirme modül, sorunu işlemleri tanımlayan ve güncelleştirme modülü işlemleri durdurduktan sonra yeniden denemek için kullanıcıya bildirir bir hata döndürür.
- Güncelleştirme modülü bir modül güncelleştirdiğinde eski ve yeni sürümleri artık yana birimi aynı dizinde; bu nedenle PowerShell 5.0 veya daha yeni sürümleri, bu modülü en son (veya belirtilen) sürümü ekler. Bunu söyleyin ve bu komutların çıktısı örneği göstermek için yararlı olacaktır.


## <a name="cmdlet-syntax"></a>Cmdlet sözdizimi
```powershell
Get-Command -Name Update-Module -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a>Cmdlet çevrimiçi Yardım başvurusu

[Güncelleştirme Modülü](http://go.microsoft.com/fwlink/?LinkID=398576)


## <a name="example-commands"></a>Örnek komutlar

```powershell
PS C:\windows\system32> Update-Module -Name ContosoServer -RequiredVersion 1.5
PS C:\windows\system32> Get-Module -ListAvailable -Name ContosoServer | Format-List Name,Version,ModuleBase
Name : ContosoServer
Version : 2.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\2.0
Name : ContosoServer
Version : 1.5
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\1.5
Name : ContosoServer
Version : 1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\1.0
PS C:\windows\system32> Get-InstalledModule
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer MSPSGallery ContosoServer module
1.5 ContosoServer MSPSGallery ContosoServer module
2.0 ContosoServer MSPSGallery ContosoServer module
PS C:\windows\system32> Update-Module -Name ContosoServer
PS C:\windows\system32> Get-Module -ListAvailable -Name ContosoServer | Format-List Name,Version,ModuleBase
Name : ContosoServer
Version : 2.8.1
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\2.8.1
Name : ContosoServer
Version : 2.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\2.0
Name : ContosoServer
Version : 1.5
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\1.5
Name : ContosoServer
Version : 1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\1.0
PS C:\windows\system32> Get-InstalledModule
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer MSPSGallery ContosoServer module
1.5 ContosoServer MSPSGallery ContosoServer module
2.0 ContosoServer MSPSGallery ContosoServer module
2.8.1 ContosoServer MSPSGallery ContosoServer module
```

### <a name="update-the-module-with-a-prerelease-version-requires--allowprerelease-flag"></a>Bir ön sürümüyle modülü güncelleştirme, - AllowPrerelease bayrağı gerektirir
```powershell
PS C:\windows\system32> Get-InstalledModule
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer MSPSGallery ContosoServer module
1.5 ContosoServer MSPSGallery ContosoServer module
2.0 ContosoServer MSPSGallery ContosoServer module
2.8.1 ContosoServer MSPSGallery ContosoServer module

PS C:\windows\system32> Find-Module ContosoServer -AllowPrerelease

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
3.0.0-alpha    ConstosoServer                      MSPSGallery          The PowerShell Contoso Server deployment tools...

PS C:\windows\system32> Update-Module -Name ContosoServer -AllowPrerelease
PS C:\windows\system32> Get-InstalledModule
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer MSPSGallery ContosoServer module
1.5 ContosoServer MSPSGallery ContosoServer module
2.0 ContosoServer MSPSGallery ContosoServer module
2.8.1 ContosoServer MSPSGallery ContosoServer module
3.0.0-alpha ContosoServer MSPSGallery ContosoServer module

```


### <a name="update-the-testdepwithnestedrequiredmodules1-module-with-dependencies"></a>TestDepWithNestedRequiredModules1 modülü bağımlılıkları ile güncelleştirin.
```powershell
Find-Module -Name TestDepWithNestedRequiredModules1 -Repository LocalRepo -AllVersions

Version    Name                                Repository  Description
-------    ----                                ----------  -----------
1.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
2.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module

Update-Module -Name TestDepWithNestedRequiredModules1 -RequiredVersion 2.0
Get-InstalledModule

Version    Name                                Repository  Description
-------    ----                                ----------  -----------
1.0        NestedRequiredModule1               LocalRepo   NestedRequiredModule1 module
2.5        NestedRequiredModule2               LocalRepo   NestedRequiredModule2 module
2.0        NestedRequiredModule3               LocalRepo   NestedRequiredModule3 module
2.5        NestedRequiredModule3               LocalRepo   NestedRequiredModule3 module
1.0        RequiredModule1                     LocalRepo   RequiredModule1 module
2.5        RequiredModule2                     LocalRepo   RequiredModule2 module
2.0        RequiredModule3                     LocalRepo   RequiredModule3 module
2.5        RequiredModule3                     LocalRepo   RequiredModule3 module
1.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
2.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module



```