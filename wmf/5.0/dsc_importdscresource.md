---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: a3b176101bebf7081febd8629bddcfa0ae1e7540
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="import-dscresource-keyword-supports--moduleversion-parameter"></a>İçeri aktarma DscResource anahtar sözcüğü - ModuleVersion parametresini destekler

Yeni bir parametre ekledik `Import-DscResource` dynamic anahtar DSC yapılandırmaları yazarken kullanılabilir. Yapılandırma yazarlar DSC kaynaklarından yüklemek için tam olarak hangi Modül sürümü artık belirtebilirsiniz. Yeni anahtar sözcük sözdizimi şöyledir:

```powershell
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName(s)>] [-ModuleVersion <ModuleVersion>]
```

* **Ad**: içeri aktarmak için bir veya daha fazla kaynakların adları.
* **ModuleName**: modül adlarını veya ModuleSpecification nesneleri içeri aktarmak için bir veya daha fazla modülü.
* **ModuleVersion**: modül ot içe sürümü. Kullandıysanız, ModuleName adıyla yalnızca bir modülü temsil etmesi gerekir.

Windows PowerShell ISE IntelliSense ile görüntülersiniz:

![](../images/Import-DscResource-Modversion.jpg)

**Not**: `–ModuleVersion` parametresi yalnızca kullanılabilir birlikte `–ModuleName` parametresi. Yalnızca kaynak adlarıyla kullanılamaz `–Name` parametresi.

Önce DSC kaynakları yüklenirken Modül sürümü belirtmek için tek yolu örneğin modül belirtimi nesnesini kullanarak, bu: `–ModuleName @{ModuleName="UserConfigProvider";ModuleVersion="3.0"}`