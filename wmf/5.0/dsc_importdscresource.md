---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 46a278b83edb9d8e3d75b0874603710d416be3b5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684657"
---
# <a name="import-dscresource-keyword-supports--moduleversion-parameter"></a>Import-DscResource anahtar sözcüğü - ModuleVersion parametresini destekler

Yeni bir parametre ekledik `Import-DscResource` dynamic anahtar sözcüğü DSC yapılandırmaları yazarken kullanılabilir. Yapılandırma yazarları artık DSC kaynaklarından yüklemek için tam olarak hangi modül sürümünün belirtebilirsiniz. Anahtar sözcüğünün yeni sözdizimi aşağıdaki gibidir:

```powershell
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName(s)>] [-ModuleVersion <ModuleVersion>]
```

* **Ad**: İçeri aktarmak için bir veya daha fazla kaynak adları.
* **ModuleName**: Modül adlarını veya içeri aktarmak için bir veya daha fazla modül ModuleSpecification nesneleri.
* **Moduleversıon**: Modülü içeri aktarmak için sürümü. ModuleName kullandıysanız, yalnızca bir modül adına göre temsil etmelidir.

Windows PowerShell ISE'de, IntelliSense ile gösterilir:

![](../images/Import-DscResource-Modversion.jpg)

**Not**: `–ModuleVersion` parametresi yalnızca kullanılabilir birlikte `–ModuleName` parametresi. Yalnızca kaynak adları ile kullanılamaz `–Name` parametresi.

Örneğin modülü belirtimi nesnesini kullanarak daha önce DSC kaynakları yüklenirken Modül sürümü belirtmek için tek yolu şöyleydi: `–ModuleName @{ModuleName="UserConfigProvider";ModuleVersion="3.0"}`
