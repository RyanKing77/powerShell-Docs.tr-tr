---
ms.date: 06/09/2017
schema: 2.0.0
keywords: PowerShell
title: Komut dosyaları için lisans kabulünü gerektirme
ms.openlocfilehash: 6374c8c8536dd0c8f27580a5b8895b8db18424f9
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/10/2018
---
# <a name="requiring-license-acceptance-for-scripts"></a>Komut dosyaları için lisans kabulünü gerektirme

Lisans kabulünü komut dosyaları için desteklenmiyor. Ancak, bir komut dosyası lisans kabulünü gerektiren bir modülünü yere bağlıdır senaryo desteklenir.

Komut dosyası commands(Install-Script/Save-Script/Update-Script) destekleyen yeni bir parametre - kullanıcı lisansı gördüğünüz olarak gibi davranır AcceptLicense. -AcceptLicense belirtilmezse; Kullanıcı license.txt bağımlı modülü için gösterilen ve lisans kabul etmesi istenir.

## <a name="examples"></a>ÖRNEKLER

### <a name="example-1-install-script-with-dependencies-requiring-license-acceptance"></a>Örnek 1: Lisans kabulünü gerektirme bağımlılıkları olan yükleme betiği

Komut dosyası 'ScriptRequireLicenseAcceptance' Modülü'nü 'ModuleRequireLicenseAcceptance' bağlıdır. Kullanıcı lisansı kabul istenir.

```PowerShell
PS> Install-Script -Name ScriptRequireLicenseAcceptance

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
PS> Install-Script -Name ScriptRequireLicenseAcceptance -AcceptLicense
```

## <a name="more-details"></a>Daha fazla ayrıntı

- [Modüller için lisans kabulünü desteği gerektirir](module-license-acceptance.md)
- [Lisans kabulünü desteğini PowerShellGallery gerektirir](../how-to/working-with-items/items-that-require-license-acceptance.md)
- [Azure Otomasyonuna Dağıtmada Lisans Kabulü Gerektir](../how-to/working-with-items/deploy-to-azure-automation.md)