---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: ce5afc2f90f78433b64bf5b41946fc7506c43504
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219659"
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
