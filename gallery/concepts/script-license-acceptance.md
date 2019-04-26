---
ms.date: 06/09/2017
schema: 2.0.0
keywords: PowerShell
title: Betikler için lisans kabulü gerektiren
ms.openlocfilehash: e7101eb6a480dd87965b7b9be9d49583042b603f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084683"
---
# <a name="requiring-license-acceptance-for-scripts"></a>Betikler için lisans kabulü gerektiren

Betikler için lisans kabulü desteklenmiyor. Bununla birlikte, burada betik lisans kabulü gerektiren bir modülünü bağlıdır senaryo desteklenir.

Betik commands(Install-Script/Save-Script/Update-Script) destekleyen yeni bir parametre - kullanıcı lisansı saw olarak gibi davranır AcceptLicense. -AcceptLicense belirtilmezse; Kullanıcı license.txt bağımlı modülü için gösterilen ve bu lisansı kabul istenir.

## <a name="examples"></a>ÖRNEKLERİ

### <a name="example-1-install-script-with-dependencies-requiring-license-acceptance"></a>Örnek 1: Lisans kabulü gerektiren bağımlılıkları olan komut dosyası yükleme

Betik 'ScriptRequireLicenseAcceptance' modülünde 'ModuleRequireLicenseAcceptance' bağlıdır. Kullanıcı lisansı kabul istenir.

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

### <a name="example-2-install-script-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a>Örnek 2: Lisans kabulü ve - AcceptLicense gerektiren bağımlılıkları olan komut dosyası yükleme

Betik 'ScriptRequireLicenseAcceptance' modülünde 'ModuleRequireLicenseAcceptance' bağlıdır. -AcceptLicense olarak lisansını kabul etmek için kullanıcıya sorulmaz.

```PowerShell
PS> Install-Script -Name ScriptRequireLicenseAcceptance -AcceptLicense
```

## <a name="more-details"></a>Daha fazla ayrıntı

- [Modüller için lisans kabulü desteği gerektirir](module-license-acceptance.md)
- [PowerShellGallery desteğini lisans kabulü gerektir](../how-to/working-with-packages/packages-that-require-license-acceptance.md)
- [Azure Otomasyonuna Dağıtmada Lisans Kabulü Gerektir](../how-to/working-with-packages/deploy-to-azure-automation.md)
