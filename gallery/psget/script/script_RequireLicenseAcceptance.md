---
ms.date: 2017-06-09
schema: 2.0.0
keywords: PowerShell
title: RequireLicenseAcceptanceScript
ms.openlocfilehash: 7092fb2e63b9e2b1eca59cd418317631bff8b172
ms.sourcegitcommit: cd66d4f49ea762a31887af2c72d087b219ddbe10
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/11/2017
---
# <a name="requiring-license-acceptance-for-scripts"></a>Komut dosyaları için lisans kabulünü gerektirme

Lisans kabulünü komut dosyaları için desteklenmiyor. Ancak, bir komut dosyası lisans kabulünü gerektiren bir modülünü yere bağlıdır senaryo desteklenir.

Komut dosyası commands(Install-Script/Save-Script/Update-Script) destekleyen yeni bir parametre - kullanıcı lisansı gördüğünüz olarak gibi davranır AcceptLicense. -AcceptLicense belirtilmezse; Kullanıcı license.txt bağımlı modülü için gösterilen ve lisans kabul etmesi istenir.

## <a name="examples"></a>ÖRNEKLER

### <a name="example-1-install-script-with-dependencies-requiring-license-acceptance"></a>Örnek 1: Lisans kabulünü gerektirme bağımlılıkları olan yükleme betiği
Komut dosyası 'ScriptRequireLicenseAcceptance' Modülü'nü 'ModuleRequireLicenseAcceptance' bağlıdır. Kullanıcı lisansı kabul istenir.
```PowerShell
PS C:\> Install-Script -Name ScriptRequireLicenseAcceptance

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

### <a name="example-2-install-script-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a>Örnek 2: Lisans kabulünü ve - AcceptLicense gerektiren bağımlılıkları olan yükleme betiği
Komut dosyası 'ScriptRequireLicenseAcceptance' Modülü'nü 'ModuleRequireLicenseAcceptance' bağlıdır. Kullanıcı - AcceptLicense belirtildiği şekilde lisans kabul etmek için istenmez.
```PowerShell
PS C:\> Install-Script -Name ScriptRequireLicenseAcceptance -AcceptLicense
```

## <a name="more-details"></a>Daha fazla ayrıntı
### <a name="require-license-acceptance-support-for-modulesmodulerequirelicenseacceptancemd"></a>[Modüller için lisans kabulünü desteği gerektirir](../module/RequireLicenseAcceptance.md)

### <a name="require-license-acceptance-support-on-powershellgallerypsgallerypsgalleryrequireslicenseacceptancemd"></a>[Lisans kabulünü desteğini PowerShellGallery gerektirir](../../psgallery/psgallery_requires_license_acceptance.md)

### <a name="require-license-acceptance-on-deploy-to-azure-automationpsgallerypsgallerydeploytoazureautomationrequirelicenseacceptancemd"></a>[Lisans kabulünü gerektiren üzerinde Azure Automation'ı dağıtma](../../psgallery/psgallery_deploy_to_azure_automation_requireLicenseAcceptance.md)
