---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Hizmetleri Yönetme
ms.assetid: 7a410e4d-514b-4813-ba0c-0d8cef88df31
ms.openlocfilehash: f3231d1922568e552534f3d3face3864d1610d65
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30951207"
---
# <a name="managing-services"></a><span data-ttu-id="3e645-103">Hizmetleri Yönetme</span><span class="sxs-lookup"><span data-stu-id="3e645-103">Managing Services</span></span>

<span data-ttu-id="3e645-104">Çok çeşitli hizmeti görevleri için tasarlanmış sekiz çekirdeği hizmet cmdlet'leri vardır.</span><span class="sxs-lookup"><span data-stu-id="3e645-104">There are eight core Service cmdlets, designed for a wide range of service tasks .</span></span> <span data-ttu-id="3e645-105">Yalnızca listeleme ve çalışır durumda Hizmetleri için değiştirme ele alacağız ancak listesini hizmet cmdlet'leri kullanarak alabileceğiniz **Get-Help \&#42;-hizmet**, ve kullanarakherhizmetcmdlet'ihakkındabilgibulabilirsiniz**Get-Help < Cmdlet adı >**, gibi **Get-Help yeni hizmet**.</span><span class="sxs-lookup"><span data-stu-id="3e645-105">We will look only at listing and changing running state for services, but you can get a list Service cmdlets by using **Get-Help \&#42;-Service**, and you can find information about each Service cmdlet by using **Get-Help<Cmdlet-Name>**, such as **Get-Help New-Service**.</span></span>

## <a name="getting-services"></a><span data-ttu-id="3e645-106">Hizmetleri alma</span><span class="sxs-lookup"><span data-stu-id="3e645-106">Getting Services</span></span>

<span data-ttu-id="3e645-107">Hizmetleri kullanarak bir yerel veya uzak bilgisayarda elde edebilirsiniz **Get-Service** cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="3e645-107">You can get the services on a local or remote computer by using the **Get-Service** cmdlet.</span></span> <span data-ttu-id="3e645-108">İle **Get-Process**kullanarak **Get-Service** parametresiz komutu tüm hizmetleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="3e645-108">As with **Get-Process**, using the **Get-Service** command without parameters returns all services.</span></span> <span data-ttu-id="3e645-109">Joker karakter olarak yıldız bile kullanarak ada göre filtreleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3e645-109">You can filter by name, even using an asterisk as a wildcard:</span></span>

```
PS> Get-Service -Name se*

Status   Name               DisplayName
------   ----               -----------
Running  seclogon           Secondary Logon
Running  SENS               System Event Notification
Stopped  ServiceLayer       ServiceLayer
```

<span data-ttu-id="3e645-110">Her zaman gerçek adı hizmetin nedir açık olduğundan, görünen ada göre hizmetleri bulmanız bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e645-110">Because it is not always obvious what the real name for the service is, you may find you need to find services by display name.</span></span> <span data-ttu-id="3e645-111">Belirli adıyla joker karakterler veya görünen adları listesini kullanarak bunu yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3e645-111">You can do this by specific name, using wildcards, or using a list of display names:</span></span>

```
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

<span data-ttu-id="3e645-112">Uzak bilgisayarlarda hizmetleri almak için Get-Service cmdlet'inin ComputerName parametresini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e645-112">You can use the ComputerName parameter of the Get-Service cmdlet to get the services on remote computers.</span></span> <span data-ttu-id="3e645-113">Tek bir komutla birden çok bilgisayarda hizmetleri alabilmek için ComputerName parametresi birden çok değerleri ve joker karakterleri kabul eder.</span><span class="sxs-lookup"><span data-stu-id="3e645-113">The ComputerName parameter accepts multiple values and wildcard characters, so you can get the services on multiple computers with a single command.</span></span> <span data-ttu-id="3e645-114">Örneğin, aşağıdaki komutu Hizmetleri Server01 uzak bilgisayarda alır.</span><span class="sxs-lookup"><span data-stu-id="3e645-114">For example, the following command gets the services on the Server01 remote computer.</span></span>

```powershell
Get-Service -ComputerName Server01
```

## <a name="getting-required-and-dependent-services"></a><span data-ttu-id="3e645-115">Gerekli ve bağımlı hizmetler</span><span class="sxs-lookup"><span data-stu-id="3e645-115">Getting Required and Dependent Services</span></span>

<span data-ttu-id="3e645-116">Get-Service cmdlet Hizmet Yönetimi'nde çok kullanışlı iki parametreye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="3e645-116">The Get-Service cmdlet has two parameters that are very useful in service administration.</span></span> <span data-ttu-id="3e645-117">DependentServices parametresi hizmete bağlı hizmetler alır.</span><span class="sxs-lookup"><span data-stu-id="3e645-117">The DependentServices parameter gets services that depend on the service.</span></span> <span data-ttu-id="3e645-118">RequiredServices parametresi bu hizmetin bağımlı olduğu hizmetler alır.</span><span class="sxs-lookup"><span data-stu-id="3e645-118">The RequiredServices parameter gets services upon which this service depends.</span></span>

<span data-ttu-id="3e645-119">Bu parametrelerden yalnızca DependentServices ve ServicesDependedOn değerlerini görüntüle (alias = RequiredServices) Get-Service verir, ancak bunlar basitleştirmek System.ServiceProcess.ServiceController nesnesinin özellikleri komutları ve alma yapın Bu bilgiler çok daha kolaydır.</span><span class="sxs-lookup"><span data-stu-id="3e645-119">These parameters just display the values of the DependentServices and ServicesDependedOn (alias=RequiredServices) properties of the System.ServiceProcess.ServiceController object that Get-Service returns, but they simplify commands and make getting this information much simpler.</span></span>

<span data-ttu-id="3e645-120">Aşağıdaki komutu LanmanWorkstation hizmeti gerektiren hizmetler alır.</span><span class="sxs-lookup"><span data-stu-id="3e645-120">The following command gets the services that the LanmanWorkstation service requires.</span></span>

```
PS> Get-Service -Name LanmanWorkstation -RequiredServices

Status   Name               DisplayName
------   ----               -----------
Running  MRxSmb20           SMB 2.0 MiniRedirector
Running  bowser             Bowser
Running  MRxSmb10           SMB 1.x MiniRedirector
Running  NSI                Network Store Interface Service
```

<span data-ttu-id="3e645-121">Aşağıdaki komutu LanmanWorkstation hizmeti gerektiren hizmetleri alır.</span><span class="sxs-lookup"><span data-stu-id="3e645-121">The following command gets the services that require the LanmanWorkstation service.</span></span>

```
PS> Get-Service -Name LanmanWorkstation -DependentServices

Status   Name               DisplayName
------   ----               -----------
Running  SessionEnv         Terminal Services Configuration
Running  Netlogon           Netlogon
Stopped  Browser            Computer Browser
Running  BITS               Background Intelligent Transfer Ser...
```

<span data-ttu-id="3e645-122">Bağımlılıkları olan tüm hizmetleri bile alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e645-122">You can even get all services that have dependencies.</span></span> <span data-ttu-id="3e645-123">Aşağıdaki komutu tam olarak bunu yapar ve sonra bilgisayardaki hizmetlerin durumu, ad, RequiredServices ve DependentServices özelliklerini görüntülemek için Format-Table cmdlet kullanır.</span><span class="sxs-lookup"><span data-stu-id="3e645-123">The following command does just that, and then it uses the Format-Table cmdlet to display the Status, Name, RequiredServices and DependentServices properties of the services on the computer.</span></span>

```powershell
Get-Service -Name * | Where-Object {$_.RequiredServices -or $_.DependentServices} | Format-Table -Property Status, Name, RequiredServices, DependentServices -auto
```

## <a name="stopping-starting-suspending-and-restarting-services"></a><span data-ttu-id="3e645-124">Başlatma, durdurma, askıya alma ve hizmetlerini yeniden başlatma</span><span class="sxs-lookup"><span data-stu-id="3e645-124">Stopping, Starting, Suspending, and Restarting Services</span></span>
<span data-ttu-id="3e645-125">Aynı genel formdaki tüm hizmet cmdlet'leri vardır.</span><span class="sxs-lookup"><span data-stu-id="3e645-125">The Service cmdlets all have the same general form.</span></span> <span data-ttu-id="3e645-126">Hizmetleri ortak ad veya görünen adı belirtilen ve listeleri ve joker karakter değerleri olarak alın.</span><span class="sxs-lookup"><span data-stu-id="3e645-126">Services can be specified by common name or display name, and take lists and wildcards as values.</span></span> <span data-ttu-id="3e645-127">Yazdırma Biriktiricisi durdurmak için kullanın:</span><span class="sxs-lookup"><span data-stu-id="3e645-127">To stop the print spooler, use:</span></span>

```powershell
Stop-Service -Name spooler
```

<span data-ttu-id="3e645-128">Bunu durdurulduktan sonra yazdırma biriktiricisi başlatmak için kullanın:</span><span class="sxs-lookup"><span data-stu-id="3e645-128">To start the print spooler after it is stopped, use:</span></span>

```powershell
Start-Service -Name spooler
```

<span data-ttu-id="3e645-129">Yazdırma Biriktiricisi askıya almak için kullanın:</span><span class="sxs-lookup"><span data-stu-id="3e645-129">To suspend the print spooler, use:</span></span>

```powershell
Suspend-Service -Name spooler
```

<span data-ttu-id="3e645-130">**Restart-Service** cmdlet diğer hizmet cmdlet'leri ile aynı şekilde çalışır, ancak daha karmaşık bazı örnekler için göstereceğiz.</span><span class="sxs-lookup"><span data-stu-id="3e645-130">The **Restart-Service** cmdlet works in the same manner as the other Service cmdlets, but we will show some more complex examples for it.</span></span> <span data-ttu-id="3e645-131">En basit kullanımda hizmetin adını belirtin:</span><span class="sxs-lookup"><span data-stu-id="3e645-131">In the simplest use, you specify the name of the service:</span></span>

```
PS> Restart-Service -Name spooler

WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
PS>
```

<span data-ttu-id="3e645-132">Yazdırma Biriktiricisi hakkında yinelenen bir uyarı iletisi başlamasını almak fark edeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="3e645-132">You will notice that you get a repeated warning message about the Print Spooler starting up.</span></span> <span data-ttu-id="3e645-133">Bazı süren bir hizmet işlemi gerçekleştirdiğinizde, Windows PowerShell bunu hala görevi gerçekleştirmeye çalışıyor olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="3e645-133">When you perform a service operation that takes some time, Windows PowerShell will notify you that it is still attempting to perform the task.</span></span>

<span data-ttu-id="3e645-134">Birden çok hizmetlerini yeniden başlatmak istiyorsanız, hizmetlerin bir listesini almak, bunları filtre ve ardından yeniden gerçekleştirin:</span><span class="sxs-lookup"><span data-stu-id="3e645-134">If you want to restart multiple services, you can get a list of services, filter them, and then perform the restart:</span></span>

```
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

<span data-ttu-id="3e645-135">Bu hizmet cmdlet'leri ComputerName parametresi gerekmez, ancak Invoke-Command cmdlet'i kullanarak bunları uzak bir bilgisayarda çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e645-135">These Service cmdlets do not have a ComputerName parameter, but you can run them on a remote computer by using the Invoke-Command cmdlet.</span></span> <span data-ttu-id="3e645-136">Örneğin, aşağıdaki komutu Server01 uzak bilgisayarda Biriktirici hizmetini yeniden başlatır.</span><span class="sxs-lookup"><span data-stu-id="3e645-136">For example, the following command restarts the Spooler service on the Server01 remote computer.</span></span>

```powershell
Invoke-Command -ComputerName Server01 {Restart-Service Spooler}
```

## <a name="setting-service-properties"></a><span data-ttu-id="3e645-137">Hizmet özelliklerini ayarlama</span><span class="sxs-lookup"><span data-stu-id="3e645-137">Setting Service Properties</span></span>

<span data-ttu-id="3e645-138">Hizmet belirleme cmdlet'ini yerel veya uzak bilgisayardaki bir hizmet özelliklerini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="3e645-138">The Set-Service cmdlet changes the properties of a service on a local or remote computer.</span></span> <span data-ttu-id="3e645-139">Hizmet durumunu bir özellik olduğundan, başlatma, durdurma ve bir hizmet askıya almak için bu cmdlet'i kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e645-139">Because the service status is a property, you can use this cmdlet to start, stop, and suspend a service.</span></span> <span data-ttu-id="3e645-140">Hizmet belirleme cmdlet Ayrıca hizmet başlatma türünü değiştirmenize imkan tanıyan bir StartupType parametreye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="3e645-140">The Set-Service cmdlet also has a StartupType parameter that lets you change the service startup type.</span></span>

<span data-ttu-id="3e645-141">Windows Vista ve Windows'un sonraki sürümleri üzerinde kümesi hizmeti kullanmak için "Yönetici olarak çalıştır" seçeneğiyle Windows PowerShell'i açın.</span><span class="sxs-lookup"><span data-stu-id="3e645-141">To use Set-Service on Windows Vista and later versions of Windows, open Windows PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="3e645-142">Daha fazla bilgi için bkz: [hizmet belirleme [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)</span><span class="sxs-lookup"><span data-stu-id="3e645-142">For more information, see [Set-Service [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)</span></span>

## <a name="see-also"></a><span data-ttu-id="3e645-143">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="3e645-143">See Also</span></span>

- <span data-ttu-id="3e645-144">[Get-Service [m2]](https://technet.microsoft.com/en-us/library/0a09cb22-0a1c-4a79-9851-4e53075f9cf6)</span><span class="sxs-lookup"><span data-stu-id="3e645-144">[Get-Service [m2]](https://technet.microsoft.com/en-us/library/0a09cb22-0a1c-4a79-9851-4e53075f9cf6)</span></span>
- <span data-ttu-id="3e645-145">[Set-Service [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)</span><span class="sxs-lookup"><span data-stu-id="3e645-145">[Set-Service [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)</span></span>
- <span data-ttu-id="3e645-146">[Restart-Service [m2]](https://technet.microsoft.com/en-us/library/45acf50d-2277-4523-baf7-ce7ced977d0f)</span><span class="sxs-lookup"><span data-stu-id="3e645-146">[Restart-Service [m2]](https://technet.microsoft.com/en-us/library/45acf50d-2277-4523-baf7-ce7ced977d0f)</span></span>
- <span data-ttu-id="3e645-147">[Suspend-Service [m2]](https://technet.microsoft.com/en-us/library/c8492b87-0e21-4faf-8054-3c83c2ec2826)</span><span class="sxs-lookup"><span data-stu-id="3e645-147">[Suspend-Service [m2]](https://technet.microsoft.com/en-us/library/c8492b87-0e21-4faf-8054-3c83c2ec2826)</span></span>