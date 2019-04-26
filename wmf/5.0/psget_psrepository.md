---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 5ac9566979e1b761249f5cc7c62ed44047a2b9f6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058021"
---
# <a name="register-a-powershell-repository"></a><span data-ttu-id="9f03d-102">Bir PowerShell Deposu Kaydetme</span><span class="sxs-lookup"><span data-stu-id="9f03d-102">Register a PowerShell Repository</span></span>
<span data-ttu-id="9f03d-103">PowerShellGet karşı iç depoları çalışmak üzere yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9f03d-103">You can configure PowerShellGet to operate against internal repositories.</span></span> <span data-ttu-id="9f03d-104">Bu, aşağıdaki eklemelerle kullanılarak gerçekleştirilir:</span><span class="sxs-lookup"><span data-stu-id="9f03d-104">This is done by using the following additions:</span></span>
- <span data-ttu-id="9f03d-105">Register-PSRepository: Geçerli kullanıcı için bir depoya kaydeder.</span><span class="sxs-lookup"><span data-stu-id="9f03d-105">Register-PSRepository: Registers a repository for the current user.</span></span>
- <span data-ttu-id="9f03d-106">Kaydı-PSRepository: Geçerli kullanıcı için kayıtlı bir depo kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9f03d-106">Unregister-PSRepository: Removes a registered repository for the current user.</span></span>
- <span data-ttu-id="9f03d-107">Set-PSRepository: Kayıtlı depoyu değerlerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="9f03d-107">Set-PSRepository: Set values for a registered repository.</span></span>
- <span data-ttu-id="9f03d-108">Get-PSRepository: Geçerli kullanıcı için kayıtlı tüm depoları alın.</span><span class="sxs-lookup"><span data-stu-id="9f03d-108">Get-PSRepository: Get all registered repositories for the current user.</span></span>

<span data-ttu-id="9f03d-109">Bir depo kaydedildikten sonra çalışma Find-Module ve Install-Module kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9f03d-109">After a repository is registered, you can use Find-Module and Install-Module to work with it.</span></span>

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
