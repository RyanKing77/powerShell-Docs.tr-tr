---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 46a278b83edb9d8e3d75b0874603710d416be3b5
ms.sourcegitcommit: f4247d3f91d06ec392c4cd66921ce7d0456a2bd9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/05/2018
ms.locfileid: "50998529"
---
# <a name="import-dscresource-keyword-supports--moduleversion-parameter"></a>Import-DscResource anahtar sözcüğü - ModuleVersion parametresini destekler

Yeni bir parametre ekledik `Import-DscResource` dynamic anahtar sözcüğü DSC yapılandırmaları yazarken kullanılabilir. Yapılandırma yazarları artık DSC kaynaklarından yüklemek için tam olarak hangi modül sürümünün belirtebilirsiniz. Anahtar sözcüğünün yeni sözdizimi aşağıdaki gibidir:

```powershell
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName(s)>] [-ModuleVersion <ModuleVersion>]
```

* **Ad**: içeri aktarmak için bir veya daha fazla kaynak adları.
* **ModuleName**: modül adlarını veya içeri aktarmak için bir veya daha fazla modül ModuleSpecification nesneleri.
* **Moduleversıon**: Modül sürümü almak için. ModuleName kullandıysanız, yalnızca bir modül adına göre temsil etmelidir.

Windows PowerShell ISE'de, IntelliSense ile gösterilir:

![](../images/Import-DscResource-Modversion.jpg)

**Not**: `–ModuleVersion` parametresi yalnızca kullanılabilir birlikte `–ModuleName` parametresi. Yalnızca kaynak adları ile kullanılamaz `–Name` parametresi.

Örneğin modülü belirtimi nesnesini kullanarak daha önce DSC kaynakları yüklenirken Modül sürümü belirtmek için tek yolu şöyleydi: `–ModuleName @{ModuleName="UserConfigProvider";ModuleVersion="3.0"}`
