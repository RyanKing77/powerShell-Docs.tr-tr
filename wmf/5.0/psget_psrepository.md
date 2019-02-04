---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 5ac9566979e1b761249f5cc7c62ed44047a2b9f6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685238"
---
# <a name="register-a-powershell-repository"></a>Bir PowerShell Deposu Kaydetme
PowerShellGet karşı iç depoları çalışmak üzere yapılandırabilirsiniz. Bu, aşağıdaki eklemelerle kullanılarak gerçekleştirilir:
- Register-PSRepository: Geçerli kullanıcı için bir depoya kaydeder.
- Kaydı-PSRepository: Geçerli kullanıcı için kayıtlı bir depo kaldırır.
- Set-PSRepository: Kayıtlı depoyu değerlerini ayarlayın.
- Get-PSRepository: Geçerli kullanıcı için kayıtlı tüm depoları alın.

Bir depo kaydedildikten sonra çalışma Find-Module ve Install-Module kullanabilirsiniz.

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
