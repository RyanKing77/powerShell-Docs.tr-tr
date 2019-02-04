---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: WMI nesnelerini alma Get WmiObject
ms.assetid: f0ddfc7d-6b5e-4832-82de-2283597ea70d
ms.openlocfilehash: 522822ac3ea6f08b20fa5af6c9accb48b01035d3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688465"
---
# <a name="getting-wmi-objects-get-wmiobject"></a>WMI nesnelerini (Get-WmiObject)

## <a name="getting-wmi-objects-get-wmiobject"></a>WMI nesnelerini (Get-WmiObject)

Windows Yönetim Araçları (WMI) Windows Sistem Yönetimi için temel bir teknoloji çünkü bir tutum çok çeşitli bilgi sunar. Ne kadar WMI WMI nesnelerini erişmek için Windows PowerShell cmdlet'i, mümkün kılar nedeniyle **Get-WmiObject**, en yararlı biri gerçek iş yapmak için. Get-WmiObject WMI nesnelere erişmek için nasıl kullanılacağını ve belirli şeyler için WMI nesnelerini kullanmayı tartışmak için kullanacağız.

### <a name="listing-wmi-classes"></a>WMI sınıflarını listeleme

WMI kullanıcıların çoğu karşılaştığınız ilk sorun WMI ile ne yapılabilir bulmaya çalışıyor. WMI sınıflarını yönetilebilen kaynaklar açıklanır. WMI sınıfları, bazı özellikler onlarca içeren yüzlerce vardır.

**Get-WmiObject** WMI bulunabilir hale getirerek bu sorunu çözüyor. Yazarak yerel bilgisayarda WMI sınıflarını listesini alabilirsiniz:

```
PS> Get-WmiObject -List

__SecurityRelatedClass                  __NTLMUser9X
__PARAMETERS                            __SystemSecurity
__NotifyStatus                          __ExtendedStatus
Win32_PrivilegesStatus                  Win32_TSNetworkAdapterSettingError
Win32_TSRemoteControlSettingError       Win32_TSEnvironmentSettingError
...
```

Aynı bilgi uzak bir bilgisayardan ComputerName parametresini kullanarak bilgisayar adını veya IP adresini belirten alabilirsiniz:

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
__ProviderRegistration                  __ObjectProviderRegistration
...
```

Uzak bilgisayarlar tarafından döndürülen sınıf listesi çalıştığı bilgisayar belirli işletim sistemi ve yüklü uygulamalar tarafından eklenen belirli WMI uzantılar nedeniyle değişebilir.

> [!NOTE]
> Bir uzak bilgisayara bağlanmak için get-WmiObject kullanırken, uzak bilgisayarda WMI çalışıyor olmalıdır ve Varsayılan yapılandırmada, kullanmakta olduğunuz hesap uzak bilgisayardaki yerel Yöneticiler grubunda olması gerekir. Uzak sistem Windows PowerShell yüklü olması gerekmez. Bu, Windows PowerShell ile çalışan, ancak WMI kullanılabilir olan işletim sistemlerini yönetmeyi sağlar.

ComputerName bile, yerel sisteme bağlanırken da içerebilir. Yerel bilgisayarın adı, IP adresini (veya geri döngü adresine 127.0.0.1) kullanabilirsiniz veya WMI-style '.' bilgisayar adı. IP adresi ile 192.168.1.90 Admin01 adlı bir bilgisayarda Windows PowerShell çalıştırıyorsanız, aşağıdaki komutları tüm listelemek o bilgisayar için WMI sınıfını döndürür:

```powershell
Get-WmiObject -List
Get-WmiObject -List -ComputerName .
Get-WmiObject -List -ComputerName Admin01
Get-WmiObject -List -ComputerName 192.168.1.90
Get-WmiObject -List -ComputerName 127.0.0.1
Get-WmiObject -List -ComputerName localhost
```

Get-WmiObject kök/cimv2 ad alanı varsayılan olarak kullanır. Başka bir WMI ad alanını belirtmek istiyorsanız, kullanmanız **Namespace** parametresi ve karşılık gelen ad alanı yolu belirtin:

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29 -Namespace root

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
...
```

### <a name="displaying-wmi-class-details"></a>WMI sınıf ayrıntıları görüntüleme

WMI sınıfının adını biliyorsanız, bilgi hemen almak için kullanabilirsiniz. Örneğin, bir bilgisayar hakkında bilgi almak için kullanılan WMI sınıflarını biri olan **Win32_OperatingSystem**.

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName .

SystemDirectory : C:\WINDOWS\system32
Organization    : Global Network Solutions
BuildNumber     : 2600
RegisteredUser  : Oliver W. Jones
SerialNumber    : 12345-678-9012345-67890
Version         : 5.1.2600
```

Şu parametrelerin tümü gösteriliyor olsa da, komutu daha birleştiren bir şekilde ifade edilebilir. **ComputerName** parametresi gerekli değildir yerel sisteme bağlanırken. En genel durumu gösterir ve parametre anımsatmak göstereceğiz. **Namespace** varsayılan olarak, kök/cimv2 ve de atlanabilir. Son olarak, çoğu cmdlet ortak parametrelerinin adını Atla olanak sağlar. Ad için ilk parametre, belirtilirse Get-WmiObject ile Windows PowerShell, olarak değerlendirir **sınıfı** parametresi. Başka bir deyişle, son komut yazarak verilmiş:

```powershell
Get-WmiObject Win32_OperatingSystem
```

**Win32_OperatingSystem** sınıfı burada görüntülenen olandan çok daha fazla özelliklere sahiptir. Tüm özellikleri görmek için Get-Member'ı kullanabilirsiniz. Bir WMI sınıfının özelliklerine gibi diğer nesne özellikleri otomatik olarak kullanılabilir:

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Get-Member -MemberType Property

   TypeName: System.Management.ManagementObject#root\cimv2\Win32_OperatingSyste
m

Name                                      MemberType Definition
----                                      ---------- ----------
__CLASS                                   Property   System.String __CLASS {...
...
BootDevice                                Property   System.String BootDevic...
BuildNumber                               Property   System.String BuildNumb...
...
```

#### <a name="displaying-non-default-properties-with-format-cmdlets"></a>Varsayılan olmayan özellikler biçim cmdlet'leri ile görüntüleme

İçindeki bilgileri almak istiyorsanız **Win32_OperatingSystem** diğer bir deyişle sınıfının varsayılan olarak görüntülenmiyorsa, onu kullanarak görüntüleyebilirsiniz **biçimi** cmdlet'leri. Kullanılabilir bellek verilerini görüntülemek istiyorsanız, örneğin:

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-Table -Property TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize TotalVisibleMemory FreePhysicalMemory FreeVirtualMemory FreeSpaceInPagingFiles
---------------------- ---------------    ------------------ -==--------------------- ---------------
               2097024          785904                305808           2056724                1558232
```

> [!NOTE]
> Özellik adlarında joker karakterler çalışın **Format-Table**, son işlem hattı öğesi için azaltılabilir `Format-Table -Property Total,Free`

Bellek verileri daha okunabilir bir liste olarak yazarak biçimlendirmek, olabilir:

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-List TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize : 2097024
TotalVisibleMemorySize : 785904
FreePhysicalMemory     : 301876
FreeVirtualMemory      : 2056724
FreeSpaceInPagingFiles : 1556644
```
