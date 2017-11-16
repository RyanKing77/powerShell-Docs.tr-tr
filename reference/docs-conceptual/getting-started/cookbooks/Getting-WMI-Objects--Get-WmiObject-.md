---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: Alma WMI nesneleri WmiObject Al
ms.assetid: f0ddfc7d-6b5e-4832-82de-2283597ea70d
ms.openlocfilehash: fbaac2797dd62eb03a2be581b3b5f8be6dafc0ad
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2017
---
# <a name="getting-wmi-objects-get-wmiobject"></a>WMI nesnelerini (Get-WmiObject) alma

## <a name="getting-wmi-objects-get-wmiobject"></a>WMI nesnelerini (Get-WmiObject) alma
Windows Yönetim Araçları (WMI) Windows Sistem Yönetimi için bir çekirdek teknoloji olduğundan çok çeşitli bilgi tek bir yolla kullanıma sunar. Ne kadar WMI WMI nesneleri erişmek için Windows PowerShell cmdlet'ini mümkün hale getirir nedeniyle **Get-WmiObject**, en kullanışlı biri gerçek iş yapmak için. Biz Get-WmiObject WMI nesnelere erişmek için nasıl kullanılacağı ve WMI nesneleri belirli şeyler için nasıl kullanılacağını ele alınacaktır.

### <a name="listing-wmi-classes"></a>WMI sınıflarını listeleme
WMI kullanıcıların çoğunun karşılaştığınız ilk sorun WMI ile ne yapılabilir bulmak çalışıyor. WMI sınıflarını yönetilebilir kaynaklarını tanımlar. WMI sınıflarını, bazıları özellikleri düzinelerce içeren yüzlerce vardır.

**Get-WmiObject** WMI bulunabilirlik sağlayarak bu sorunu giderir. Yazarak yerel bilgisayarda kullanılabilir WMI sınıflarının bir listesini alabilirsiniz:

```
PS> Get-WmiObject -List

__SecurityRelatedClass                  __NTLMUser9X
__PARAMETERS                            __SystemSecurity
__NotifyStatus                          __ExtendedStatus
Win32_PrivilegesStatus                  Win32_TSNetworkAdapterSettingError
Win32_TSRemoteControlSettingError       Win32_TSEnvironmentSettingError
...
```

Aynı bilgileri uzak bir bilgisayardan ComputerName parametresini kullanarak bir bilgisayar adı veya IP adresi belirtme alabilirsiniz:

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
__ProviderRegistration                  __ObjectProviderRegistration
...
```

Uzak bilgisayarlar tarafından döndürülen sınıfı listeleme, bilgisayarda çalışan belirli işletim sistemi ve yüklü uygulamalar tarafından eklenen belirli WMI uzantıları nedeniyle değişebilir.

> [!NOTE]
> Bir uzak bilgisayara bağlanmak için get-WmiObject kullanırken, uzak bilgisayarda WMI çalışıyor olması gerekir ve Varsayılan yapılandırmada kullandığınız hesabın uzak bilgisayarda yerel Yöneticiler grubunda olması gerekir. Uzak sistem Windows PowerShell yüklü olması gerekmez. Bu, Windows PowerShell'i çalışmayan, ancak WMI kullanılabilir yüklü işletim sistemlerini yönetmeyi sağlar.

ComputerName bile, yerel sistem bağlanırken da içerebilir. Yerel bilgisayarın adı, IP adresini (veya geri döngü adresine 127.0.0.1) kullanabilir veya WMI-style '.' bilgisayar adı olarak. IP adresi 192.168.1.90 Admin01 adlı bir bilgisayarda Windows PowerShell çalıştırıyorsanız, aşağıdaki komutları tüm bu bilgisayar için listeleme WMI sınıfı döndürün:

```
Get-WmiObject -List
Get-WmiObject -List -ComputerName .
Get-WmiObject -List -ComputerName Admin01
Get-WmiObject -List -ComputerName 192.168.1.90
Get-WmiObject -List -ComputerName 127.0.0.1
Get-WmiObject -List -ComputerName localhost
```

Get-WmiObject kök/cimv2 ad alanı varsayılan olarak kullanır. Başka bir WMI ad alanı belirtmek istiyorsanız, kullanmak **Namespace** parametre ve karşılık gelen ad alanı yolu belirtin:

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29 -Namespace root

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
...
```

### <a name="displaying-wmi-class-details"></a>WMI sınıfı ayrıntılarını görüntüleme
WMI sınıfı adını biliyorsanız, bilgi hemen almak için kullanabilirsiniz. Örneğin, bir bilgisayar hakkında bilgi almak için kullanılan WMI sınıflarını biri **Win32_OperatingSystem**.

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName .

SystemDirectory : C:\WINDOWS\system32
Organization    : Global Network Solutions
BuildNumber     : 2600
RegisteredUser  : Oliver W. Jones
SerialNumber    : 12345-678-9012345-67890
Version         : 5.1.2600
```

Biz tüm parametreleri gösteren rağmen komut daha kısa bir yol ifade edilebilir. **ComputerName** parametresi gerekli değildir yerel sisteme bağlanırken. En genel durum göstermek ve parametre hakkında anımsatmak kendisine gösteriyoruz. **Namespace** Varsayılanları kök/cimv2 ve de atlanabilir. Son olarak, çoğu cmdlet'leri ortak parametrelerinin adını Atla olanak sağlar. Ad için ilk parametresi, belirtilmişse, Get-WmiObject ile Windows PowerShell, işler **sınıfı** parametresi. Başka bir deyişle, son komut yazarak verilmiş:

```
Get-WmiObject Win32_OperatingSystem
```

**Win32_OperatingSystem** sınıfı burada görüntülenen olandan çok daha fazla özellik içeriyor. Tüm özellikleri görmek için Get-üye kullanabilirsiniz. WMI sınıfının özelliklerine gibi diğer nesne özellikleri otomatik olarak kullanılabilir:

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

#### <a name="displaying-non-default-properties-with-format-cmdlets"></a>Varsayılan olmayan özellikleri biçimi cmdlet'leri ile görüntüleme
İçinde yer alan bilgileri almak istiyorsanız **Win32_OperatingSystem** diğer bir deyişle sınıfı varsayılan olarak görüntülenmiyorsa, onu kullanarak görüntüleyebilirsiniz **biçimi** cmdlet'leri. Kullanılabilir bellek verileri görüntülemek istiyorsanız, örneğin, yazın:

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-Table -Property TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize TotalVisibleMemory FreePhysicalMemory FreeVirtualMemory FreeSpaceInPagingFiles
---------------------- ---------------    ------------------ -==--------------------- ---------------
               2097024          785904                305808           2056724                1558232
```

> [!NOTE]
> Özellik adlarında joker karakterler çalışabilirsiniz **Format-Table**, son ardışık düzen öğesi için azaltılabilir  **Format-Table-özelliği toplam*, boş*

Bellek verileri daha okunabilir bir liste olarak yazarak biçimlendirmek varsa olabilir:

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-List TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize : 2097024
TotalVisibleMemorySize : 785904
FreePhysicalMemory     : 301876
FreeVirtualMemory      : 2056724
FreeSpaceInPagingFiles : 1556644
```

