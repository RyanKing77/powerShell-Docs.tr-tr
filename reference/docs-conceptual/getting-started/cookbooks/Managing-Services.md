---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Hizmetleri Yönetme
ms.assetid: 7a410e4d-514b-4813-ba0c-0d8cef88df31
ms.openlocfilehash: 81fd8802215da80ce22fa3fd4750b1df6efe8206
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/26/2018
ms.locfileid: "39268084"
---
# <a name="managing-services"></a><span data-ttu-id="91ace-103">Hizmetleri Yönetme</span><span class="sxs-lookup"><span data-stu-id="91ace-103">Managing Services</span></span>

<span data-ttu-id="91ace-104">Çok çeşitli hizmeti görevleri için tasarlanmış, sekiz çekirdeği hizmeti cmdlet'leri vardır.</span><span class="sxs-lookup"><span data-stu-id="91ace-104">There are eight core Service cmdlets, designed for a wide range of service tasks .</span></span> <span data-ttu-id="91ace-105">Yalnızca listeleme ve çalışır durumda hizmetler için değiştirme atacağız ancak kullanarak hizmet cmdlet'lerin bir listesi alabilirsiniz `Get-Help \*-Service`, ve kullanarak, her hizmet cmdlet'i hakkında daha fazla bilgi bulabilirsiniz `Get-Help <Cmdlet-Name>`, gibi `Get-Help New-Service`.</span><span class="sxs-lookup"><span data-stu-id="91ace-105">We will look only at listing and changing running state for services, but you can get a list of Service cmdlets by using `Get-Help \*-Service`, and you can find information about each Service cmdlet by using `Get-Help <Cmdlet-Name>`, such as `Get-Help New-Service`.</span></span>

## <a name="getting-services"></a><span data-ttu-id="91ace-106">Hizmetleri alınıyor</span><span class="sxs-lookup"><span data-stu-id="91ace-106">Getting Services</span></span>

<span data-ttu-id="91ace-107">Bir yerel veya uzak bilgisayarda Hizmetleri kullanarak alabilirsiniz `Get-Service` cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="91ace-107">You can get the services on a local or remote computer by using the `Get-Service` cmdlet.</span></span> <span data-ttu-id="91ace-108">Olduğu gibi `Get-Process`kullanarak `Get-Service` komutunu parametresiz tüm hizmetleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="91ace-108">As with `Get-Process`, using the `Get-Service` command without parameters returns all services.</span></span> <span data-ttu-id="91ace-109">Ada göre bile bir joker karakter olarak yıldız kullanarak filtreleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="91ace-109">You can filter by name, even using an asterisk as a wildcard:</span></span>

```powershell
PS> Get-Service -Name se*

Status   Name               DisplayName
------   ----               -----------
Running  seclogon           Secondary Logon
Running  SENS               System Event Notification
Stopped  ServiceLayer       ServiceLayer
```

<span data-ttu-id="91ace-110">Her zaman hizmet gerçek adı nedir açık olduğundan, görünen ada göre hizmetleri bulmanız bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="91ace-110">Because it is not always obvious what the real name for the service is, you may find you need to find services by display name.</span></span> <span data-ttu-id="91ace-111">Belirli bir ada göre joker karakterler veya görüntü adlarının bir listesini kullanarak bunu yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="91ace-111">You can do this by specific name, using wildcards, or using a list of display names:</span></span>

```powershell
PS> Get-Service -DisplayName se*

Status   Name               DisplayName
------   ----               -----------
Running  lanmanserver       Server
Running  SamSs              Security Accounts Manager
Running  seclogon           Secondary Logon
Stopped  ServiceLayer       ServiceLayer
Running  wscsvc             Security Center

PS> Get-Service -DisplayName ServiceLayer,Server

Status   Name               DisplayName
------   ----               -----------
Running  lanmanserver       Server
Stopped  ServiceLayer       ServiceLayer
```

<span data-ttu-id="91ace-112">Hizmetleri uzak bilgisayarlarda almak için Get-Service cmdlet'inin ComputerName parametresine kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="91ace-112">You can use the ComputerName parameter of the Get-Service cmdlet to get the services on remote computers.</span></span> <span data-ttu-id="91ace-113">Tek bir komutla birden çok bilgisayarda Hizmetleri alabilmeniz için ComputerName parametresi birden çok değer ve joker karakterler kabul eder.</span><span class="sxs-lookup"><span data-stu-id="91ace-113">The ComputerName parameter accepts multiple values and wildcard characters, so you can get the services on multiple computers with a single command.</span></span> <span data-ttu-id="91ace-114">Örneğin, aşağıdaki komutu hizmetler Server01 uzak bilgisayarda alır.</span><span class="sxs-lookup"><span data-stu-id="91ace-114">For example, the following command gets the services on the Server01 remote computer.</span></span>

```powershell
Get-Service -ComputerName Server01
```

## <a name="getting-required-and-dependent-services"></a><span data-ttu-id="91ace-115">Gerekli ve bağımlı hizmetler</span><span class="sxs-lookup"><span data-stu-id="91ace-115">Getting Required and Dependent Services</span></span>

<span data-ttu-id="91ace-116">Get-Service cmdlet Hizmet Yönetimi'nde çok kullanışlı olan iki parametreye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="91ace-116">The Get-Service cmdlet has two parameters that are very useful in service administration.</span></span> <span data-ttu-id="91ace-117">DependentServices parametresi, hizmete bağlı hizmetler alır.</span><span class="sxs-lookup"><span data-stu-id="91ace-117">The DependentServices parameter gets services that depend on the service.</span></span> <span data-ttu-id="91ace-118">Bu hizmetin bağımlı olduğu hizmetleri RequiredServices parametresi alır.</span><span class="sxs-lookup"><span data-stu-id="91ace-118">The RequiredServices parameter gets services upon which this service depends.</span></span>

<span data-ttu-id="91ace-119">Bu parametrelerin değerlerini DependentServices ServicesDependedOn ve yalnızca görüntüle (RequiredServices alias =) Get-Service döndürür, ancak bunlar basitleştiren System.ServiceProcess.ServiceController nesnesinin özelliklerini komutları ve alma olun Bu bilgiler çok daha kolaydır.</span><span class="sxs-lookup"><span data-stu-id="91ace-119">These parameters just display the values of the DependentServices and ServicesDependedOn (alias=RequiredServices) properties of the System.ServiceProcess.ServiceController object that Get-Service returns, but they simplify commands and make getting this information much simpler.</span></span>

<span data-ttu-id="91ace-120">Aşağıdaki komut LanmanWorkstation hizmeti gerektiren hizmetler alır.</span><span class="sxs-lookup"><span data-stu-id="91ace-120">The following command gets the services that the LanmanWorkstation service requires.</span></span>

```powershell
PS> Get-Service -Name LanmanWorkstation -RequiredServices

Status   Name               DisplayName
------   ----               -----------
Running  MRxSmb20           SMB 2.0 MiniRedirector
Running  bowser             Bowser
Running  MRxSmb10           SMB 1.x MiniRedirector
Running  NSI                Network Store Interface Service
```

<span data-ttu-id="91ace-121">Aşağıdaki komutu LanmanWorkstation hizmeti gerektiren hizmetleri alır.</span><span class="sxs-lookup"><span data-stu-id="91ace-121">The following command gets the services that require the LanmanWorkstation service.</span></span>

```powershell
PS> Get-Service -Name LanmanWorkstation -DependentServices

Status   Name               DisplayName
------   ----               -----------
Running  SessionEnv         Terminal Services Configuration
Running  Netlogon           Netlogon
Stopped  Browser            Computer Browser
Running  BITS               Background Intelligent Transfer Ser...
```

<span data-ttu-id="91ace-122">Bağımlılıkları olan tüm hizmetleri bile alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="91ace-122">You can even get all services that have dependencies.</span></span> <span data-ttu-id="91ace-123">Aşağıdaki komutu yapan ve ardından bilgisayarda hizmetlerin durumunu, adı, RequiredServices ve DependentServices özelliklerini görüntülemek için Format-Table cmdlet kullanır.</span><span class="sxs-lookup"><span data-stu-id="91ace-123">The following command does just that, and then it uses the Format-Table cmdlet to display the Status, Name, RequiredServices and DependentServices properties of the services on the computer.</span></span>

```powershell
Get-Service -Name * | Where-Object {$_.RequiredServices -or $_.DependentServices} | Format-Table -Property Status, Name, RequiredServices, DependentServices -auto
```

## <a name="stopping-starting-suspending-and-restarting-services"></a><span data-ttu-id="91ace-124">Başlatma, durdurma, askıya alma ve hizmetler yeniden başlatılıyor</span><span class="sxs-lookup"><span data-stu-id="91ace-124">Stopping, Starting, Suspending, and Restarting Services</span></span>

<span data-ttu-id="91ace-125">Tüm hizmet cmdlet'leri, aynı genel form sahiptir.</span><span class="sxs-lookup"><span data-stu-id="91ace-125">The Service cmdlets all have the same general form.</span></span> <span data-ttu-id="91ace-126">Hizmetleri ortak ad veya görünen ad belirtilebilir ve listeler ve değerleri joker karakterleri alır.</span><span class="sxs-lookup"><span data-stu-id="91ace-126">Services can be specified by common name or display name, and take lists and wildcards as values.</span></span> <span data-ttu-id="91ace-127">Yazdırma Biriktiricisi durdurmak için kullanın:</span><span class="sxs-lookup"><span data-stu-id="91ace-127">To stop the print spooler, use:</span></span>

```powershell
Stop-Service -Name spooler
```

<span data-ttu-id="91ace-128">Bunu durdurulduktan sonra yazdırma biriktiricisini başlatmak için kullanın:</span><span class="sxs-lookup"><span data-stu-id="91ace-128">To start the print spooler after it is stopped, use:</span></span>

```powershell
Start-Service -Name spooler
```

<span data-ttu-id="91ace-129">Yazdırma Biriktiricisi askıya almak için kullanın:</span><span class="sxs-lookup"><span data-stu-id="91ace-129">To suspend the print spooler, use:</span></span>

```powershell
Suspend-Service -Name spooler
```

<span data-ttu-id="91ace-130">`Restart-Service` Cmdlet'i bir hizmeti cmdlet'leri ile aynı şekilde çalışır, ancak daha karmaşık bazı örnekler için göstereceğiz.</span><span class="sxs-lookup"><span data-stu-id="91ace-130">The `Restart-Service` cmdlet works in the same manner as the other Service cmdlets, but we will show some more complex examples for it.</span></span> <span data-ttu-id="91ace-131">En basit kullanın, hizmetin adını belirtin:</span><span class="sxs-lookup"><span data-stu-id="91ace-131">In the simplest use, you specify the name of the service:</span></span>

```powershell
PS> Restart-Service -Name spooler

WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
PS>
```

<span data-ttu-id="91ace-132">Başlatma yazdırma biriktiricisi yinelenen bir uyarı iletisi aldığını göreceksiniz.</span><span class="sxs-lookup"><span data-stu-id="91ace-132">You will notice that you get a repeated warning message about the Print Spooler starting up.</span></span> <span data-ttu-id="91ace-133">Biraz zaman alır bir hizmet işlemi gerçekleştirdiğinizde, Windows PowerShell, hala görevi bağlanmaya çalıştığı bildirir.</span><span class="sxs-lookup"><span data-stu-id="91ace-133">When you perform a service operation that takes some time, Windows PowerShell will notify you that it is still attempting to perform the task.</span></span>

<span data-ttu-id="91ace-134">Birden çok hizmeti yeniden başlatmak istiyorsanız, hizmet listesini almak, bunları filtrelemek ve sonra yeniden gerçekleştirin:</span><span class="sxs-lookup"><span data-stu-id="91ace-134">If you want to restart multiple services, you can get a list of services, filter them, and then perform the restart:</span></span>

```powershell
PS> Get-Service | Where-Object -FilterScript {$_.CanStop} | Restart-Service

WARNING: Waiting for service 'Computer Browser (Browser)' to finish stopping...
WARNING: Waiting for service 'Computer Browser (Browser)' to finish stopping...
Restart-Service : Cannot stop service 'Logical Disk Manager (dmserver)' because
 it has dependent services. It can only be stopped if the Force flag is set.
At line:1 char:57
+ Get-Service | Where-Object -FilterScript {$_.CanStop} | Restart-Service <<<<
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
```

<span data-ttu-id="91ace-135">Bu hizmet cmdlet'leri, ComputerName parametresi yoktur, ancak Invoke-Command cmdlet'ini kullanarak bunları uzak bir bilgisayarda çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="91ace-135">These Service cmdlets do not have a ComputerName parameter, but you can run them on a remote computer by using the Invoke-Command cmdlet.</span></span> <span data-ttu-id="91ace-136">Örneğin, aşağıdaki komutu Server01 uzak bilgisayarda Biriktirici hizmetini yeniden başlatır.</span><span class="sxs-lookup"><span data-stu-id="91ace-136">For example, the following command restarts the Spooler service on the Server01 remote computer.</span></span>

```powershell
Invoke-Command -ComputerName Server01 {Restart-Service Spooler}
```

## <a name="setting-service-properties"></a><span data-ttu-id="91ace-137">Hizmet özelliklerini ayarlama</span><span class="sxs-lookup"><span data-stu-id="91ace-137">Setting Service Properties</span></span>

<span data-ttu-id="91ace-138">`Set-Service` Cmdlet'i, yerel veya uzak bilgisayardaki bir hizmet özelliklerini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="91ace-138">The `Set-Service` cmdlet changes the properties of a service on a local or remote computer.</span></span> <span data-ttu-id="91ace-139">Hizmet durumu, bir özellik olduğundan, başlatma, durdurma ve hizmet askıya almak için bu cmdlet'i kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="91ace-139">Because the service status is a property, you can use this cmdlet to start, stop, and suspend a service.</span></span>
<span data-ttu-id="91ace-140">Set-Service cmdlet Ayrıca hizmet başlatma türünü değiştirmenize olanak sağlayan bir başlangıç türü parametresi vardır.</span><span class="sxs-lookup"><span data-stu-id="91ace-140">The Set-Service cmdlet also has a StartupType parameter that lets you change the service startup type.</span></span>

<span data-ttu-id="91ace-141">Kullanılacak `Set-Service` Windows Vista ve sonraki Windows sürümlerinde, Windows PowerShell ile "Yönetici olarak çalıştır" seçeneğini açın.</span><span class="sxs-lookup"><span data-stu-id="91ace-141">To use `Set-Service` on Windows Vista and later versions of Windows, open Windows PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="91ace-142">Daha fazla bilgi için [hizmet belirleme [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)</span><span class="sxs-lookup"><span data-stu-id="91ace-142">For more information, see [Set-Service [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)</span></span>

## <a name="see-also"></a><span data-ttu-id="91ace-143">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="91ace-143">See Also</span></span>

- <span data-ttu-id="91ace-144">[Get-Service [m2]](https://technet.microsoft.com/en-us/library/0a09cb22-0a1c-4a79-9851-4e53075f9cf6)</span><span class="sxs-lookup"><span data-stu-id="91ace-144">[Get-Service [m2]](https://technet.microsoft.com/en-us/library/0a09cb22-0a1c-4a79-9851-4e53075f9cf6)</span></span>
- <span data-ttu-id="91ace-145">[Hizmet belirleme [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)</span><span class="sxs-lookup"><span data-stu-id="91ace-145">[Set-Service [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)</span></span>
- <span data-ttu-id="91ace-146">[Restart-Service [m2]](https://technet.microsoft.com/en-us/library/45acf50d-2277-4523-baf7-ce7ced977d0f)</span><span class="sxs-lookup"><span data-stu-id="91ace-146">[Restart-Service [m2]](https://technet.microsoft.com/en-us/library/45acf50d-2277-4523-baf7-ce7ced977d0f)</span></span>
- <span data-ttu-id="91ace-147">[Suspend-Service [m2]](https://technet.microsoft.com/en-us/library/c8492b87-0e21-4faf-8054-3c83c2ec2826)</span><span class="sxs-lookup"><span data-stu-id="91ace-147">[Suspend-Service [m2]](https://technet.microsoft.com/en-us/library/c8492b87-0e21-4faf-8054-3c83c2ec2826)</span></span>