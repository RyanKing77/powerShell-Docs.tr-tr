---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 9a9bdac652512640209c20e3deb20d7abc0142c6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
---
# <a name="register-a-powershell-repository"></a>Bir PowerShell Deposu Kaydetme
PowerShellGet karşı iç depoları çalışmak üzere yapılandırabilirsiniz. Bu, aşağıdaki eklemelerle kullanarak gerçekleştirilir:
- Register-PSRepository: geçerli kullanıcı için depo kaydeder.
- Unregister-PSRepository: geçerli kullanıcı için kayıtlı depo kaldırır.
- Set-PSRepository: bir kayıtlı deposu değerlerini ayarlayın.
- Get-PSRepository: geçerli kullanıcı için tüm kayıtlı depoları alın.

Bir depo kaydedildikten sonra ile çalışmak için bulma modülü ve Install-Module kullanabilirsiniz.

```powershell
\#Register a default repository
Register-PSRepository –Name DemoRepo –SourceLocation “https://www.myget.org/F/powershellgetdemo/api/v2” –PublishLocation “<https://www.myget.org/F/powershellgetdemo/api/v2>/package” –InstallationPolicy –Trusted

\#Get all of the registered repositories
Get-PSRepository
Name SourceLocation
---- --------------
PSGallery https://msconfiggallery.cloudapp...
DemoRepo https://www.myget.org/F/powershe...

\#Search only the new repository for modules
Find-Module -Repository DemoRepo
Repository Version Name
---------- ------- ----
DemoRepo 1.0.1 xActiveDirectory
DemoRepo 1.1.1 SomeModule

\#By default, PowerShellGet operates against all registered repositories when none is specified. In this example, the “SomeModule” module is installed from the DemoRepo.
Install-Module SomeModule

\#Removing a repository
Unregister-PSRepository DemoRepo
```
