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
---
# <a name="managing-services"></a>Hizmetleri Yönetme

Çok çeşitli hizmeti görevleri için tasarlanmış sekiz çekirdeği hizmet cmdlet'leri vardır. Yalnızca listeleme ve çalışır durumda Hizmetleri için değiştirme ele alacağız ancak listesini hizmet cmdlet'leri kullanarak alabileceğiniz **Get-Help \&#42;-hizmet**, ve kullanarakherhizmetcmdlet'ihakkındabilgibulabilirsiniz**Get-Help < Cmdlet adı >**, gibi **Get-Help yeni hizmet**.

## <a name="getting-services"></a>Hizmetleri alma

Hizmetleri kullanarak bir yerel veya uzak bilgisayarda elde edebilirsiniz **Get-Service** cmdlet'i. İle **Get-Process**kullanarak **Get-Service** parametresiz komutu tüm hizmetleri döndürür. Joker karakter olarak yıldız bile kullanarak ada göre filtreleyebilirsiniz:

```
PS> Get-Service -Name se*

Status   Name               DisplayName
------   ----               -----------
Running  seclogon           Secondary Logon
Running  SENS               System Event Notification
Stopped  ServiceLayer       ServiceLayer
```

Her zaman gerçek adı hizmetin nedir açık olduğundan, görünen ada göre hizmetleri bulmanız bulabilirsiniz. Belirli adıyla joker karakterler veya görünen adları listesini kullanarak bunu yapabilirsiniz:

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

Uzak bilgisayarlarda hizmetleri almak için Get-Service cmdlet'inin ComputerName parametresini kullanabilirsiniz. Tek bir komutla birden çok bilgisayarda hizmetleri alabilmek için ComputerName parametresi birden çok değerleri ve joker karakterleri kabul eder. Örneğin, aşağıdaki komutu Hizmetleri Server01 uzak bilgisayarda alır.

```powershell
Get-Service -ComputerName Server01
```

## <a name="getting-required-and-dependent-services"></a>Gerekli ve bağımlı hizmetler

Get-Service cmdlet Hizmet Yönetimi'nde çok kullanışlı iki parametreye sahiptir. DependentServices parametresi hizmete bağlı hizmetler alır. RequiredServices parametresi bu hizmetin bağımlı olduğu hizmetler alır.

Bu parametrelerden yalnızca DependentServices ve ServicesDependedOn değerlerini görüntüle (alias = RequiredServices) Get-Service verir, ancak bunlar basitleştirmek System.ServiceProcess.ServiceController nesnesinin özellikleri komutları ve alma yapın Bu bilgiler çok daha kolaydır.

Aşağıdaki komutu LanmanWorkstation hizmeti gerektiren hizmetler alır.

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

Bağımlılıkları olan tüm hizmetleri bile alabilirsiniz. Aşağıdaki komutu tam olarak bunu yapar ve sonra bilgisayardaki hizmetlerin durumu, ad, RequiredServices ve DependentServices özelliklerini görüntülemek için Format-Table cmdlet kullanır.

```powershell
Get-Service -Name * | Where-Object {$_.RequiredServices -or $_.DependentServices} | Format-Table -Property Status, Name, RequiredServices, DependentServices -auto
```

## <a name="stopping-starting-suspending-and-restarting-services"></a>Başlatma, durdurma, askıya alma ve hizmetlerini yeniden başlatma
Aynı genel formdaki tüm hizmet cmdlet'leri vardır. Hizmetleri ortak ad veya görünen adı belirtilen ve listeleri ve joker karakter değerleri olarak alın. Yazdırma Biriktiricisi durdurmak için kullanın:

```powershell
Stop-Service -Name spooler
```

Bunu durdurulduktan sonra yazdırma biriktiricisi başlatmak için kullanın:

```powershell
Start-Service -Name spooler
```

Yazdırma Biriktiricisi askıya almak için kullanın:

```powershell
Suspend-Service -Name spooler
```

**Restart-Service** cmdlet diğer hizmet cmdlet'leri ile aynı şekilde çalışır, ancak daha karmaşık bazı örnekler için göstereceğiz. En basit kullanımda hizmetin adını belirtin:

```
PS> Restart-Service -Name spooler

WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
PS>
```

Yazdırma Biriktiricisi hakkında yinelenen bir uyarı iletisi başlamasını almak fark edeceksiniz. Bazı süren bir hizmet işlemi gerçekleştirdiğinizde, Windows PowerShell bunu hala görevi gerçekleştirmeye çalışıyor olduğunu bildirir.

Birden çok hizmetlerini yeniden başlatmak istiyorsanız, hizmetlerin bir listesini almak, bunları filtre ve ardından yeniden gerçekleştirin:

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

Bu hizmet cmdlet'leri ComputerName parametresi gerekmez, ancak Invoke-Command cmdlet'i kullanarak bunları uzak bir bilgisayarda çalıştırabilirsiniz. Örneğin, aşağıdaki komutu Server01 uzak bilgisayarda Biriktirici hizmetini yeniden başlatır.

```powershell
Invoke-Command -ComputerName Server01 {Restart-Service Spooler}
```

## <a name="setting-service-properties"></a>Hizmet özelliklerini ayarlama

Hizmet belirleme cmdlet'ini yerel veya uzak bilgisayardaki bir hizmet özelliklerini değiştirir. Hizmet durumunu bir özellik olduğundan, başlatma, durdurma ve bir hizmet askıya almak için bu cmdlet'i kullanabilirsiniz. Hizmet belirleme cmdlet Ayrıca hizmet başlatma türünü değiştirmenize imkan tanıyan bir StartupType parametreye sahiptir.

Windows Vista ve Windows'un sonraki sürümleri üzerinde kümesi hizmeti kullanmak için "Yönetici olarak çalıştır" seçeneğiyle Windows PowerShell'i açın.

Daha fazla bilgi için bkz: [hizmet belirleme [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)

## <a name="see-also"></a>Ayrıca bkz:

- [Get-Service [m2]](https://technet.microsoft.com/en-us/library/0a09cb22-0a1c-4a79-9851-4e53075f9cf6)
- [Set-Service [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)
- [Restart-Service [m2]](https://technet.microsoft.com/en-us/library/45acf50d-2277-4523-baf7-ce7ced977d0f)
- [Suspend-Service [m2]](https://technet.microsoft.com/en-us/library/c8492b87-0e21-4faf-8054-3c83c2ec2826)