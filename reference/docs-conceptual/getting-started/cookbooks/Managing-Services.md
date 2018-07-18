---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Hizmetleri Yönetme
ms.assetid: 7a410e4d-514b-4813-ba0c-0d8cef88df31
ms.openlocfilehash: e2388f5d73a320a69faae0772c8403a7d77f8b52
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39094179"
---
# <a name="managing-services"></a>Hizmetleri Yönetme

Çok çeşitli hizmeti görevleri için tasarlanmış, sekiz çekirdeği hizmeti cmdlet'leri vardır. Yalnızca listeleme ve çalışır durumda hizmetler için değiştirme atacağız ancak kullanarak hizmet cmdlet'lerin bir listesi alabilirsiniz **Get-Help \*-hizmet**, ve kullanarak, her hizmet cmdlet'i hakkında daha fazla bilgi bulabilirsiniz  **Get-Help \<Cmdlet-adı\>**, gibi **Get-Help yeni hizmet**.

## <a name="getting-services"></a>Hizmetleri alınıyor

Bir yerel veya uzak bilgisayarda Hizmetleri kullanarak alabilirsiniz **Get-Service** cmdlet'i. Olduğu gibi **Get-Process**kullanarak **Get-Service** komutunu parametresiz tüm hizmetleri döndürür. Ada göre bile bir joker karakter olarak yıldız kullanarak filtreleyebilirsiniz:

```
PS> Get-Service -Name se*

Status   Name               DisplayName
------   ----               -----------
Running  seclogon           Secondary Logon
Running  SENS               System Event Notification
Stopped  ServiceLayer       ServiceLayer
```

Her zaman hizmet gerçek adı nedir açık olduğundan, görünen ada göre hizmetleri bulmanız bulabilirsiniz. Belirli bir ada göre joker karakterler veya görüntü adlarının bir listesini kullanarak bunu yapabilirsiniz:

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

Hizmetleri uzak bilgisayarlarda almak için Get-Service cmdlet'inin ComputerName parametresine kullanabilirsiniz. Tek bir komutla birden çok bilgisayarda Hizmetleri alabilmeniz için ComputerName parametresi birden çok değer ve joker karakterler kabul eder. Örneğin, aşağıdaki komutu hizmetler Server01 uzak bilgisayarda alır.

```powershell
Get-Service -ComputerName Server01
```

## <a name="getting-required-and-dependent-services"></a>Gerekli ve bağımlı hizmetler

Get-Service cmdlet Hizmet Yönetimi'nde çok kullanışlı olan iki parametreye sahiptir. DependentServices parametresi, hizmete bağlı hizmetler alır. Bu hizmetin bağımlı olduğu hizmetleri RequiredServices parametresi alır.

Bu parametrelerin değerlerini DependentServices ServicesDependedOn ve yalnızca görüntüle (RequiredServices alias =) Get-Service döndürür, ancak bunlar basitleştiren System.ServiceProcess.ServiceController nesnesinin özelliklerini komutları ve alma olun Bu bilgiler çok daha kolaydır.

Aşağıdaki komut LanmanWorkstation hizmeti gerektiren hizmetler alır.

```
PS> Get-Service -Name LanmanWorkstation -RequiredServices

Status   Name               DisplayName
------   ----               -----------
Running  MRxSmb20           SMB 2.0 MiniRedirector
Running  bowser             Bowser
Running  MRxSmb10           SMB 1.x MiniRedirector
Running  NSI                Network Store Interface Service
```

Aşağıdaki komutu LanmanWorkstation hizmeti gerektiren hizmetleri alır.

```
PS> Get-Service -Name LanmanWorkstation -DependentServices

Status   Name               DisplayName
------   ----               -----------
Running  SessionEnv         Terminal Services Configuration
Running  Netlogon           Netlogon
Stopped  Browser            Computer Browser
Running  BITS               Background Intelligent Transfer Ser...
```

Bağımlılıkları olan tüm hizmetleri bile alabilirsiniz. Aşağıdaki komutu yapan ve ardından bilgisayarda hizmetlerin durumunu, adı, RequiredServices ve DependentServices özelliklerini görüntülemek için Format-Table cmdlet kullanır.

```powershell
Get-Service -Name * | Where-Object {$_.RequiredServices -or $_.DependentServices} | Format-Table -Property Status, Name, RequiredServices, DependentServices -auto
```

## <a name="stopping-starting-suspending-and-restarting-services"></a>Başlatma, durdurma, askıya alma ve hizmetler yeniden başlatılıyor
Tüm hizmet cmdlet'leri, aynı genel form sahiptir. Hizmetleri ortak ad veya görünen ad belirtilebilir ve listeler ve değerleri joker karakterleri alır. Yazdırma Biriktiricisi durdurmak için kullanın:

```powershell
Stop-Service -Name spooler
```

Bunu durdurulduktan sonra yazdırma biriktiricisini başlatmak için kullanın:

```powershell
Start-Service -Name spooler
```

Yazdırma Biriktiricisi askıya almak için kullanın:

```powershell
Suspend-Service -Name spooler
```

**Restart-Service** cmdlet'i bir hizmeti cmdlet'leri ile aynı şekilde çalışır, ancak daha karmaşık bazı örnekler için göstereceğiz. En basit kullanın, hizmetin adını belirtin:

```
PS> Restart-Service -Name spooler

WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
PS>
```

Başlatma yazdırma biriktiricisi yinelenen bir uyarı iletisi aldığını göreceksiniz. Biraz zaman alır bir hizmet işlemi gerçekleştirdiğinizde, Windows PowerShell, hala görevi bağlanmaya çalıştığı bildirir.

Birden çok hizmeti yeniden başlatmak istiyorsanız, hizmet listesini almak, bunları filtrelemek ve sonra yeniden gerçekleştirin:

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

Bu hizmet cmdlet'leri, ComputerName parametresi yoktur, ancak Invoke-Command cmdlet'ini kullanarak bunları uzak bir bilgisayarda çalıştırabilirsiniz. Örneğin, aşağıdaki komutu Server01 uzak bilgisayarda Biriktirici hizmetini yeniden başlatır.

```powershell
Invoke-Command -ComputerName Server01 {Restart-Service Spooler}
```

## <a name="setting-service-properties"></a>Hizmet özelliklerini ayarlama

Set-Service cmdlet'i, yerel veya uzak bilgisayardaki bir hizmet özelliklerini değiştirir. Hizmet durumu, bir özellik olduğundan, başlatma, durdurma ve hizmet askıya almak için bu cmdlet'i kullanabilirsiniz. Set-Service cmdlet Ayrıca hizmet başlatma türünü değiştirmenize olanak sağlayan bir başlangıç türü parametresi vardır.

Set-Service Windows Vista ve sonraki Windows sürümlerinde kullanmak için "Yönetici olarak çalıştır" seçeneğiyle Windows PowerShell'i açın.

Daha fazla bilgi için [hizmet belirleme [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)

## <a name="see-also"></a>Ayrıca bkz:

- [Get-Service [m2]](https://technet.microsoft.com/en-us/library/0a09cb22-0a1c-4a79-9851-4e53075f9cf6)
- [Hizmet belirleme [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)
- [Restart-Service [m2]](https://technet.microsoft.com/en-us/library/45acf50d-2277-4523-baf7-ce7ced977d0f)
- [Suspend-Service [m2]](https://technet.microsoft.com/en-us/library/c8492b87-0e21-4faf-8054-3c83c2ec2826)