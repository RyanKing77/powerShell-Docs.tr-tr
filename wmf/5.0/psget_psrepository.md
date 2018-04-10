---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 269f4112704067f291728e4c1d745d68ec6ccd6f
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="register-a-powershell-repository"></a><span data-ttu-id="a4c90-102">Bir PowerShell Deposu Kaydetme</span><span class="sxs-lookup"><span data-stu-id="a4c90-102">Register a PowerShell Repository</span></span>
<span data-ttu-id="a4c90-103">PowerShellGet karşı iç depoları çalışmak üzere yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a4c90-103">You can configure PowerShellGet to operate against internal repositories.</span></span> <span data-ttu-id="a4c90-104">Bu, aşağıdaki eklemelerle kullanarak gerçekleştirilir:</span><span class="sxs-lookup"><span data-stu-id="a4c90-104">This is done by using the following additions:</span></span>
- <span data-ttu-id="a4c90-105">Register-PSRepository: geçerli kullanıcı için depo kaydeder.</span><span class="sxs-lookup"><span data-stu-id="a4c90-105">Register-PSRepository: Registers a repository for the current user.</span></span>
- <span data-ttu-id="a4c90-106">Unregister-PSRepository: geçerli kullanıcı için kayıtlı depo kaldırır.</span><span class="sxs-lookup"><span data-stu-id="a4c90-106">Unregister-PSRepository: Removes a registered repository for the current user.</span></span>
- <span data-ttu-id="a4c90-107">Set-PSRepository: bir kayıtlı deposu değerlerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a4c90-107">Set-PSRepository: Set values for a registered repository.</span></span>
- <span data-ttu-id="a4c90-108">Get-PSRepository: geçerli kullanıcı için tüm kayıtlı depoları alın.</span><span class="sxs-lookup"><span data-stu-id="a4c90-108">Get-PSRepository: Get all registered repositories for the current user.</span></span>

<span data-ttu-id="a4c90-109">Bir depo kaydedildikten sonra ile çalışmak için bulma modülü ve Install-Module kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a4c90-109">After a repository is registered, you can use Find-Module and Install-Module to work with it.</span></span>

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