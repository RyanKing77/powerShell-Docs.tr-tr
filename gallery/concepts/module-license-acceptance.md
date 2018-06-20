---
ms.date: 06/09/2017
schema: 2.0.0
keywords: PowerShell
title: Lisans Kabulü Gerektiren Modüller
ms.openlocfilehash: fe197ea271e18580a221ad4d5245b685bd81775b
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/10/2018
ms.locfileid: "34049092"
---
# <a name="modules-requiring-license-acceptance"></a>Lisans Kabulü Gerektiren Modüller

## <a name="synopsis"></a>ÖZET

Müşteriler açıkça lisans kendi modülü PowerShell Galerisi'nden yüklemeden önce kabul etmesi gereken bazı modülü yayımcıları için yasal Departmanlar gerektirir. Bir kullanıcı yükler, güncelleştirmeleri veya PowerShellGet, doğrudan ya da başka bir öğe için bağımlılık olarak kullanarak bir modülü kaydeder ve bu modül kullanıcıya bir lisans kabul gerektiriyorsa, kullanıcı lisansı kabul veya işlem başarısız belirtmeniz gerekir.

## <a name="publish-requirements-for-modules"></a>Modülleri için gereksinimleri yayımlama

Kullanıcıların lisans kabul etmesini gerektir istediğiniz modülleri gereksinimleri karşılamanız:

- Modül bildirimi PSData bölümünü RequireLicenseAcceptance içermelidir $True =.
- Modül license.txt dosyası kök dizininde içermelidir.
- Modül bildirimi lisans URI içermelidir.
- Modül ve üstü PowerShellGet biçimi sürüm 2.0 ile yayımlanması gerekir.

## <a name="impact-on-installsaveupdate-module"></a>Yükleme/kaydetme/güncelleştirme-Module üzerindeki etkisi

- Yükleme/kaydetme/güncelleştirme cmdlet'leri, yeni bir parametre destekleneceğini – kullanıcının lisans gördüğünüz olarak gibi davranacak AcceptLicense.
- RequiredLicenseAcceptance True ise ve – AcceptLicense belirtilmezse, kullanıcı license.txt gösterilen ve ile istenir: &quot;lisans koşullarını (Evet/Hayır/YesToAll/NoToAll) kabul ediyor musunuz&quot;.
  - Lisans kabul edilirse
    - **Kaydet-Module:** modülü kullanıcıya kopyalanacak&#39;s sistem
    - **Install-Module:** modülü kullanıcıya kopyalanacak&#39;(kapsamına göre) uygun klasöre s sistem
    - **Update-Module:** modülü güncelleştirilir.
  - Lisans reddettiyseniz.
    - İşlem iptal edilir.
- Tüm cmdlet'ler lisans kabulünü gereklidir bildiren için meta veriler (requireLicenseAcceptance ve biçim sürümünü) denetler
  - İstemci biçimindeki sürümü 2.0 eskiyse, işlem başarısız ve istemci güncelleştirmesini kullanıcıya isteyin.
  - Modül biçimi sürüm 2.0 eski yayımlandıysa requireLicenseAcceptance bayrağı yoksayılacak.


 ## <a name="module-dependencies"></a>Modül bağımlılıkları
- (Başka bir modülde bağlıdır) bağımlı bir modül lisans kabulünü sonra lisans kabulü davranış (yukarıda) gerektiriyorsa işlemi kaydetme/yükleme/güncelleştirme sırasında gerekli olacaktır.
- Modül sürümü zaten sistemde yüklü olarak yerel kataloğunda listeleniyorsa, biz lisans denetimi atlar.
- Yükleme/kaydetme/güncelleştirme işlemi sırasında bir bağımlı modül lisans gerektiriyorsa ve lisans kabulünü oluşmaz, işlemi başarısız olacak ve kaydetme/yükleme/güncelleştirme işlemi başarısız oldu öğesi için normal işlemleri izleyin.

 ## <a name="impact-on--force"></a>Etkisini - Force

Belirtmek için – Force değil bir lisans kabul etmek yeterli. – AcceptLicense iznin yüklemek için gereklidir. Zorla belirtilmişse, – RequiredLicenseAcceptance true'dur ve – AcceptLicense belirtilmedi, işlem başarısız olur.

## <a name="examples"></a>ÖRNEKLER

### <a name="example-1-update-module-manifest-to-require-license-acceptance"></a>Örnek 1: Lisans kabulünü gerektirecek şekilde modülü güncelleştirme bildirimi

```PowerShell
PS> Update-ModuleManifest -Path C:\modulemanifest.psd1 -RequireLicenseAcceptance

PrivateData = @{

    PSData = @{
        # Flag to indicate whether the module requires explicit user acceptance
        RequireLicenseAcceptance = $true
    } # End of PSData hashtable

 } # End of PrivateData hashtable
```

Bu komut, bildirim dosyasını güncelleştirir ve RequireLicenseAcceptance bayrağı true olarak ayarlanır.

### <a name="example-2-install-module-requiring-license-acceptance"></a>Örnek 2: Yükleme modül gerektiren lisans kabulü

```PowerShell
PS> Install-Module -Name ModuleRequireLicenseAcceptance

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

Bu komut license.txt dosyasından lisans gösterir ve kullanıcının lisans kabul etmesi istenir.

### <a name="example-3-install-module-requiring-license-acceptance-with--acceptlicense"></a>Örnek 3: Yükleme modül gerektiren lisans kabulünü - AcceptLicense ile

```PowerShell
PS> Install-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```

Modül lisans kabul etmek için hiçbir istemi yüklenir.

### <a name="example-4-install-module-requiring-license-acceptance-with--force"></a>Örnek 4: Yükleme modül gerektiren lisans kabulünü ile - Force

```PowerShell
PS> Install-Module -Name ModuleRequireLicenseAcceptance -Force
PackageManagement\Install-Package : License Acceptance is required for module 'ModuleRequireLicenseAcceptance'. Please specify '-AcceptLicense' to perform this operation.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.1.3.3\PSModule.psm1:1837 char:21
+ ...          $null = PackageManagement\Install-Package @PSBoundParameters
+                      ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (Microsoft.Power....InstallPackage:InstallPackage) [Install-Package], E
   xception
    + FullyQualifiedErrorId : ForceAcceptLicense,Install-PackageUtility,Microsoft.PowerShell.PackageManagement.Cmdlets
   .InstallPackage
```

### <a name="example-5-install-module-with-dependencies-requiring-license-acceptance"></a>Örnek 5: Yükleme modül lisans kabulünü gerektirme bağımlılıkları

Modül 'ModuleWithDependency' Modülü'nü 'ModuleRequireLicenseAcceptance' bağlıdır. Kullanıcı lisansı kabul istenir.

```PowerShell
PS> Install-Module -Name ModuleWithDependency

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

### <a name="example-6-install-module-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a>Örnek 6: Yükleme modül lisans kabulünü ve - AcceptLicense gerektiren bağımlılıkları

Modül 'ModuleWithDependency' Modülü'nü 'ModuleRequireLicenseAcceptance' bağlıdır. Kullanıcı - AcceptLicense belirtildiği şekilde lisans kabul etmek için istenmez.

```PowerShell
PS>  Install-Module -Name ModuleWithDependency -AcceptLicense
```

### <a name="example-7-install-module-requiring-license-acceptance-on-a-client-older-than-psgetformatversion-20"></a>7. örnek: PSGetFormatVersion 2.0 eski bir istemcide lisans kabulünü gerektirme modülünü yükleme

```PowerShell
PS C:\windows\system32> Install-Module -Name ModuleRequireLicenseAcceptance

WARNING: The specified module 'ModuleRequireLicenseAcceptance' with PowerShellGetFormatVersion '2.0' is not supported by the current version of PowerShellGet. Get the latest version of the PowerShellGet module to install this module, 'ModuleRequireLicenseAcceptance'.

```

### <a name="example-8-save-module-requiring-license-acceptance"></a>Örnek 8: Lisans kabulünü gerektirme modülü Kaydet

```PowerShell
PS> Save-Module -Name ModuleRequireLicenseAcceptance -Path C:\Saved

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

Bu komut license.txt dosyasından lisans gösterir ve kullanıcının lisans kabul etmesi istenir.

### <a name="example-9-save-module-requiring-license-acceptance-with--acceptlicense"></a>9. örnek: - AcceptLicense ile lisans kabulünü gerektirme modülü kaydedin

```PowerShell
PS> Save-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense -Path C:\Saved
```

Modül lisans kabul etmek için tüm sorulmadan kaydedilir.

### <a name="example-10-update-module-requiring-license-acceptance"></a>Örnek 10: Güncelleştirme modülü gerektiren lisans kabulü

```PowerShell
PS> Update-Module -Name ModuleRequireLicenseAcceptance

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

Bu komut license.txt dosyasından lisans gösterir ve kullanıcının lisans kabul etmesi istenir.

### <a name="example-11-update-module-requiring-license-acceptance-with--acceptlicense"></a>Örnek 11: Güncelleştirme modülü gerektiren lisans kabulünü - AcceptLicense ile

```PowerShell
PS> Update-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```

Modül lisans kabul etmek için tüm sorulmadan güncelleştirilir.

## <a name="more-details"></a>Daha fazla ayrıntı

### <a name="require-license-acceptance-for-scriptsscript-license-acceptancemd"></a>[Betikler için Lisans Kabulü Gerektir](./script-license-acceptance.md)

### <a name="require-license-acceptance-support-on-powershellgalleryhow-toworking-with-itemsitems-that-require-license-acceptancemd"></a>[Lisans kabulünü desteğini PowerShellGallery gerektirir](../how-to/working-with-items/items-that-require-license-acceptance.md)

### <a name="require-license-acceptance-on-deploy-to-azure-automationhow-toworking-with-itemsdeploy-to-azure-automationmd"></a>[Azure Otomasyonuna Dağıtmada Lisans Kabulü Gerektir](../how-to/working-with-items/deploy-to-azure-automation.md)