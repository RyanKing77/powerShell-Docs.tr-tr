---
ms.date: 06/09/2017
schema: 2.0.0
keywords: PowerShell
title: Lisans Kabulü Gerektiren Modüller
ms.openlocfilehash: 369e32d5278a2e1bf1d3f2ae67f670c524b9f878
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075231"
---
# <a name="modules-requiring-license-acceptance"></a>Lisans Kabulü Gerektiren Modüller

## <a name="synopsis"></a>ÖZETİ

Müşteriler açıkça lisans kendi modülü PowerShell Galerisi'nden yüklemeden önce kabul etmesi gereken bazı modülü yayımcılar için yasal Departmanlar gerektirir. Bir kullanıcı yükler, güncelleştirmeleri veya PowerShellGet, doğrudan ya da başka bir paket için bir bağımlılık olarak kullanarak bir modülü kaydeder ve bu modül lisansı kabul etmesi gerekir, kullanıcı lisansı kabul veya işlem başarısız belirtmeniz gerekir.

## <a name="publish-requirements-for-modules"></a>Modüller için gereksinimleri yayımlama

Kullanıcıların lisans kabul etmesini gerektirmek için istediğiniz modülleri gereksinimleri yerine getirmek:

- Modül bildirimini PSData bölümünü RequireLicenseAcceptance içermelidir $True =.
- Modül kök dizininde license.txt dosyasına içermelidir.
- Modül bildirimini lisans URI içermelidir.
- PowerShellGet biçimi sürüm 2.0 ve üstüyle modülü yayımlanması gerekir.

## <a name="impact-on-installsaveupdate-module"></a>Yükleme/kaydetme/Update-Module etkisi

- Yükleme/kaydetme/güncelleştirme cmdlet'leri yeni bir parametre destekleyeceği – kullanıcı lisansı saw olarak gibi davranır AcceptLicense.
- RequiredLicenseAcceptance true'dur ve – AcceptLicense belirtilmezse, kullanıcı license.txt gösterilen ve ile istenir: &quot;Bu lisans koşullarını (Evet/Hayır/YesToAll/NoToAll) kabul etmezseniz&quot;.
  - Lisans kabul edilirse
    - **Save-Module:** modülü kullanıcıya kopyalanacak&#39;s sistem
    - **Install-Module:** modülü kullanıcıya kopyalanacak&#39;s sistem uygun klasöre (kapsamınıza bağlı olarak)
    - **Update-Module:** modülü güncelleştirilir.
  - Lisansı'nı reddetmeniz durumunda.
    - İşlem iptal edilecek.
    - Tüm cmdlet'ler lisans kabulü gerekli olduğuna ilişkin meta verileri (requireLicenseAcceptance ve biçim sürümünü) denetler.
    - İstemci biçimindeki sürümü 2.0 eskiyse, işlem başarısız ve istemci güncelleştirmesi için kullanıcıya sor.
    - Modül biçimi sürüm 2.0 eski yayımlandıysa requireLicenseAcceptance bayrağı yoksayılacak.

## <a name="module-dependencies"></a>Modül bağımlılıklarının

- Yükleme/kaydetme/güncelleştirme sırasında işlemi (başka bir modüldeki bağlıdır) bağımlı bir modül lisans kabulü sonra lisans kabulü davranışı (yukarıda) gerektiriyorsa, gerekli olacaktır.
- Modül sürümü sistemde yüklü olarak yerel kataloğunda zaten listedeyse, biz lisansı denetleniyor atlar.
- Yükleme/kaydetme/güncelleştirme işlemi sırasında lisansı bağımlı bir modül gerektirir ve lisans kabulü oluşmaz, işlemi başarısız ve kaydetme/yükleme/güncelleştirme işlemi başarısız oldu paketi için normal işlemleri izleyin.

## <a name="impact-on--force"></a>-Force üzerindeki etki

Belirtme `–Force` değil bir lisansı kabul etmek yeterli. `–AcceptLicense` yüklemek için izin gerekiyor. Varsa `–Force` , RequiredLicenseAcceptance True, yeterli belirtilir ve `–AcceptLicense` belirtilmezse, işlem başarısız olur.

## <a name="examples"></a>ÖRNEKLERİ

### <a name="example-1-update-module-manifest-to-require-license-acceptance"></a>Örnek 1: Güncelleştirme modül lisans kabulü gerektir için bildirim.

```powershell
Update-ModuleManifest -Path C:\modulemanifest.psd1 -RequireLicenseAcceptance -PrivateData @{
    PSData = @{
        # Flag to indicate whether the module requires explicit user acceptance
        RequireLicenseAcceptance = $true
    } # End of PSData hashtable

 } # End of PrivateData hashtable
```

Bu komut, bildirim dosyasını güncelleştirir ve RequireLicenseAcceptance bayrağı true olarak ayarlanır.

### <a name="example-2-install-module-requiring-license-acceptance"></a>Örnek 2: Lisans kabulü gerektiren bir modülünü yükleme

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance
```

```output
License Acceptance

License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

Bu komut, lisans license.txt dosyasından gösterir ve bu lisansı kabul etmesi ister.

### <a name="example-3-install-module-requiring-license-acceptance-with--acceptlicense"></a>Örnek 3: -AcceptLicense ile lisans kabulü gerektiren bir modülünü yükleme

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```

Modül lisansını kabul etmek için herhangi bir istem olmadan yüklenir.

### <a name="example-4-install-module-requiring-license-acceptance-with--force"></a>Örnek 4: -Force ile lisans kabulü gerektiren bir modülünü yükleme

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance -Force
```

```output
PackageManagement\Install-Package : License Acceptance is required for module 'ModuleRequireLicenseAcceptance'. Please specify '-AcceptLicense' to perform this operation.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.1.3.3\PSModule.psm1:1837 char:21
+ ...          $null = PackageManagement\Install-Package @PSBoundParameters
+                      ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (Microsoft.Power....InstallPackage:InstallPackage) [Install-Package], E
   xception
    + FullyQualifiedErrorId : ForceAcceptLicense,Install-PackageUtility,Microsoft.PowerShell.PackageManagement.Cmdlets
   .InstallPackage
```

### <a name="example-5-install-module-with-dependencies-requiring-license-acceptance"></a>Örnek 5: Lisans kabulü gerektiren bağımlılıklarla modülünü yükleme

Modül 'ModuleWithDependency' modülünde 'ModuleRequireLicenseAcceptance' bağlıdır. Kullanıcı lisansı kabul istenir.

```powershell
Install-Module -Name ModuleWithDependency
```

```output
License Acceptance
MIT License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

### <a name="example-6-install-module-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a>Örnek 6: Lisans kabulü ve - AcceptLicense gerektiren bağımlılıklarla modülünü yükleme

Modül 'ModuleWithDependency' modülünde 'ModuleRequireLicenseAcceptance' bağlıdır. -AcceptLicense olarak lisansını kabul etmek için kullanıcıya sorulmaz.

```powershell
Install-Module -Name ModuleWithDependency -AcceptLicense
```

### <a name="example-7-install-module-requiring-license-acceptance-on-a-client-older-than-psgetformatversion-20"></a>Örnek 7: PSGetFormatVersion 2.0 eski bir istemcide lisans kabulü gerektiren bir modülünü yükleme

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance
```

```output
WARNING: The specified module 'ModuleRequireLicenseAcceptance' with PowerShellGetFormatVersion '2.0' is not supported by the current version of PowerShellGet. Get the latest version of the PowerShellGet module to install this module, 'ModuleRequireLicenseAcceptance'.
```

### <a name="example-8-save-module-requiring-license-acceptance"></a>8. örnek: Modül lisans kabulü gerektiren Kaydet

```powershell
Save-Module -Name ModuleRequireLicenseAcceptance -Path C:\Saved
```

```output
License Acceptance

License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

Bu komut, lisans license.txt dosyasından gösterir ve bu lisansı kabul etmesi ister.

### <a name="example-9-save-module-requiring-license-acceptance-with--acceptlicense"></a>9. örnek: -AcceptLicense ile lisans kabulü gerektiren modülü Kaydet

```powershell
Save-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense -Path C:\Saved
```

Modül lisansını kabul etmek için herhangi bir istem olmadan kaydedilir.

### <a name="example-10-update-module-requiring-license-acceptance"></a>10. örnek: Lisans kabulü gerektiren modülü güncelleştirme

```powershell
Update-Module -Name ModuleRequireLicenseAcceptance
```

```output
License Acceptance

License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

Bu komut, lisans license.txt dosyasından gösterir ve bu lisansı kabul etmesi ister.

### <a name="example-11-update-module-requiring-license-acceptance-with--acceptlicense"></a>11. örnek: -AcceptLicense ile lisans kabulü gerektiren modülü güncelleştirme

```powershell
Update-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```

Modül lisansını kabul etmek için herhangi bir istem olmadan güncelleştirilir.

## <a name="more-details"></a>Daha fazla ayrıntı

[Betikler için Lisans Kabulü Gerektir](./script-license-acceptance.md)

[PowerShellGallery desteğini lisans kabulü gerektir](../how-to/working-with-packages/packages-that-require-license-acceptance.md)

[Azure Otomasyonuna Dağıtmada Lisans Kabulü Gerektir](../how-to/working-with-packages/deploy-to-azure-automation.md)
