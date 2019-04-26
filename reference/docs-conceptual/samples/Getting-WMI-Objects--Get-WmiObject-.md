---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: WMI nesnelerini alma Get WmiObject
ms.assetid: f0ddfc7d-6b5e-4832-82de-2283597ea70d
ms.openlocfilehash: 522822ac3ea6f08b20fa5af6c9accb48b01035d3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058259"
---
# <a name="getting-wmi-objects-get-wmiobject"></a><span data-ttu-id="d397c-103">WMI nesnelerini (Get-WmiObject)</span><span class="sxs-lookup"><span data-stu-id="d397c-103">Getting WMI Objects (Get-WmiObject)</span></span>

## <a name="getting-wmi-objects-get-wmiobject"></a><span data-ttu-id="d397c-104">WMI nesnelerini (Get-WmiObject)</span><span class="sxs-lookup"><span data-stu-id="d397c-104">Getting WMI Objects (Get-WmiObject)</span></span>

<span data-ttu-id="d397c-105">Windows Yönetim Araçları (WMI) Windows Sistem Yönetimi için temel bir teknoloji çünkü bir tutum çok çeşitli bilgi sunar.</span><span class="sxs-lookup"><span data-stu-id="d397c-105">Windows Management Instrumentation (WMI) is a core technology for Windows system administration because it exposes a wide range of information in a uniform manner.</span></span> <span data-ttu-id="d397c-106">Ne kadar WMI WMI nesnelerini erişmek için Windows PowerShell cmdlet'i, mümkün kılar nedeniyle **Get-WmiObject**, en yararlı biri gerçek iş yapmak için.</span><span class="sxs-lookup"><span data-stu-id="d397c-106">Because of how much WMI makes possible, the Windows PowerShell cmdlet for accessing WMI objects, **Get-WmiObject**, is one of the most useful for doing real work.</span></span> <span data-ttu-id="d397c-107">Get-WmiObject WMI nesnelere erişmek için nasıl kullanılacağını ve belirli şeyler için WMI nesnelerini kullanmayı tartışmak için kullanacağız.</span><span class="sxs-lookup"><span data-stu-id="d397c-107">We are going to discuss how to use Get-WmiObject to access WMI objects and then how to use WMI objects to do specific things.</span></span>

### <a name="listing-wmi-classes"></a><span data-ttu-id="d397c-108">WMI sınıflarını listeleme</span><span class="sxs-lookup"><span data-stu-id="d397c-108">Listing WMI Classes</span></span>

<span data-ttu-id="d397c-109">WMI kullanıcıların çoğu karşılaştığınız ilk sorun WMI ile ne yapılabilir bulmaya çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="d397c-109">The first problem most WMI users encounter is trying to find out what can be done with WMI.</span></span> <span data-ttu-id="d397c-110">WMI sınıflarını yönetilebilen kaynaklar açıklanır.</span><span class="sxs-lookup"><span data-stu-id="d397c-110">WMI classes describe the resources that can be managed.</span></span> <span data-ttu-id="d397c-111">WMI sınıfları, bazı özellikler onlarca içeren yüzlerce vardır.</span><span class="sxs-lookup"><span data-stu-id="d397c-111">There are hundreds of WMI classes, some of which contain dozens of properties.</span></span>

<span data-ttu-id="d397c-112">**Get-WmiObject** WMI bulunabilir hale getirerek bu sorunu çözüyor.</span><span class="sxs-lookup"><span data-stu-id="d397c-112">**Get-WmiObject** addresses this problem by making WMI discoverable.</span></span> <span data-ttu-id="d397c-113">Yazarak yerel bilgisayarda WMI sınıflarını listesini alabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d397c-113">You can get a list of the WMI classes available on the local computer by typing:</span></span>

```
PS> Get-WmiObject -List

__SecurityRelatedClass                  __NTLMUser9X
__PARAMETERS                            __SystemSecurity
__NotifyStatus                          __ExtendedStatus
Win32_PrivilegesStatus                  Win32_TSNetworkAdapterSettingError
Win32_TSRemoteControlSettingError       Win32_TSEnvironmentSettingError
...
```

<span data-ttu-id="d397c-114">Aynı bilgi uzak bir bilgisayardan ComputerName parametresini kullanarak bilgisayar adını veya IP adresini belirten alabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d397c-114">You can retrieve the same information from a remote computer by using the ComputerName parameter, specifying a computer name or IP address:</span></span>

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
__ProviderRegistration                  __ObjectProviderRegistration
...
```

<span data-ttu-id="d397c-115">Uzak bilgisayarlar tarafından döndürülen sınıf listesi çalıştığı bilgisayar belirli işletim sistemi ve yüklü uygulamalar tarafından eklenen belirli WMI uzantılar nedeniyle değişebilir.</span><span class="sxs-lookup"><span data-stu-id="d397c-115">The class listing returned by remote computers may vary due to the specific operating system the computer is running and the particular WMI extensions added by installed applications.</span></span>

> [!NOTE]
> <span data-ttu-id="d397c-116">Bir uzak bilgisayara bağlanmak için get-WmiObject kullanırken, uzak bilgisayarda WMI çalışıyor olmalıdır ve Varsayılan yapılandırmada, kullanmakta olduğunuz hesap uzak bilgisayardaki yerel Yöneticiler grubunda olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d397c-116">When using Get-WmiObject to connect to a remote computer, the remote computer must be running WMI and, under the default configuration, the account you are using must be in the local administrators group on the remote computer.</span></span> <span data-ttu-id="d397c-117">Uzak sistem Windows PowerShell yüklü olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="d397c-117">The remote system does not need to have Windows PowerShell installed.</span></span> <span data-ttu-id="d397c-118">Bu, Windows PowerShell ile çalışan, ancak WMI kullanılabilir olan işletim sistemlerini yönetmeyi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d397c-118">This allows you to administer operating systems that are not running Windows PowerShell, but do have WMI available.</span></span>

<span data-ttu-id="d397c-119">ComputerName bile, yerel sisteme bağlanırken da içerebilir.</span><span class="sxs-lookup"><span data-stu-id="d397c-119">You can even include the ComputerName when connecting to the local system.</span></span> <span data-ttu-id="d397c-120">Yerel bilgisayarın adı, IP adresini (veya geri döngü adresine 127.0.0.1) kullanabilirsiniz veya WMI-style '.' bilgisayar adı.</span><span class="sxs-lookup"><span data-stu-id="d397c-120">You can use the local computer's name, its IP address (or the loopback address 127.0.0.1), or the WMI-style '.' as the computer name.</span></span> <span data-ttu-id="d397c-121">IP adresi ile 192.168.1.90 Admin01 adlı bir bilgisayarda Windows PowerShell çalıştırıyorsanız, aşağıdaki komutları tüm listelemek o bilgisayar için WMI sınıfını döndürür:</span><span class="sxs-lookup"><span data-stu-id="d397c-121">If you are running Windows PowerShell on a computer named Admin01 with IP address 192.168.1.90, the following commands will all return the WMI class listing for that computer:</span></span>

```powershell
Get-WmiObject -List
Get-WmiObject -List -ComputerName .
Get-WmiObject -List -ComputerName Admin01
Get-WmiObject -List -ComputerName 192.168.1.90
Get-WmiObject -List -ComputerName 127.0.0.1
Get-WmiObject -List -ComputerName localhost
```

<span data-ttu-id="d397c-122">Get-WmiObject kök/cimv2 ad alanı varsayılan olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="d397c-122">Get-WmiObject uses the root/cimv2 namespace by default.</span></span> <span data-ttu-id="d397c-123">Başka bir WMI ad alanını belirtmek istiyorsanız, kullanmanız **Namespace** parametresi ve karşılık gelen ad alanı yolu belirtin:</span><span class="sxs-lookup"><span data-stu-id="d397c-123">If you want to specify another WMI namespace, use the **Namespace** parameter and specify the corresponding namespace path:</span></span>

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29 -Namespace root

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
...
```

### <a name="displaying-wmi-class-details"></a><span data-ttu-id="d397c-124">WMI sınıf ayrıntıları görüntüleme</span><span class="sxs-lookup"><span data-stu-id="d397c-124">Displaying WMI Class Details</span></span>

<span data-ttu-id="d397c-125">WMI sınıfının adını biliyorsanız, bilgi hemen almak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d397c-125">If you already know the name of a WMI class, you can use it to get information immediately.</span></span> <span data-ttu-id="d397c-126">Örneğin, bir bilgisayar hakkında bilgi almak için kullanılan WMI sınıflarını biri olan **Win32_OperatingSystem**.</span><span class="sxs-lookup"><span data-stu-id="d397c-126">For example, one of the WMI classes commonly used for retrieving information about a computer is **Win32_OperatingSystem**.</span></span>

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName .

SystemDirectory : C:\WINDOWS\system32
Organization    : Global Network Solutions
BuildNumber     : 2600
RegisteredUser  : Oliver W. Jones
SerialNumber    : 12345-678-9012345-67890
Version         : 5.1.2600
```

<span data-ttu-id="d397c-127">Şu parametrelerin tümü gösteriliyor olsa da, komutu daha birleştiren bir şekilde ifade edilebilir.</span><span class="sxs-lookup"><span data-stu-id="d397c-127">Although we are showing all of the parameters, the command can be expressed in a more succinct way.</span></span> <span data-ttu-id="d397c-128">**ComputerName** parametresi gerekli değildir yerel sisteme bağlanırken.</span><span class="sxs-lookup"><span data-stu-id="d397c-128">The **ComputerName** parameter is not necessary when connecting to the local system.</span></span> <span data-ttu-id="d397c-129">En genel durumu gösterir ve parametre anımsatmak göstereceğiz.</span><span class="sxs-lookup"><span data-stu-id="d397c-129">We show it to demonstrate the most general case and remind you about the parameter.</span></span> <span data-ttu-id="d397c-130">**Namespace** varsayılan olarak, kök/cimv2 ve de atlanabilir.</span><span class="sxs-lookup"><span data-stu-id="d397c-130">The **Namespace** defaults to root/cimv2, and can be omitted as well.</span></span> <span data-ttu-id="d397c-131">Son olarak, çoğu cmdlet ortak parametrelerinin adını Atla olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="d397c-131">Finally, most cmdlets allow you to omit the name of common parameters.</span></span> <span data-ttu-id="d397c-132">Ad için ilk parametre, belirtilirse Get-WmiObject ile Windows PowerShell, olarak değerlendirir **sınıfı** parametresi.</span><span class="sxs-lookup"><span data-stu-id="d397c-132">With Get-WmiObject, if no name is specified for the first parameter, Windows PowerShell treats it as the **Class** parameter.</span></span> <span data-ttu-id="d397c-133">Başka bir deyişle, son komut yazarak verilmiş:</span><span class="sxs-lookup"><span data-stu-id="d397c-133">This means the last command could have been issued by typing:</span></span>

```powershell
Get-WmiObject Win32_OperatingSystem
```

<span data-ttu-id="d397c-134">**Win32_OperatingSystem** sınıfı burada görüntülenen olandan çok daha fazla özelliklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="d397c-134">The **Win32_OperatingSystem** class has many more properties than those displayed here.</span></span> <span data-ttu-id="d397c-135">Tüm özellikleri görmek için Get-Member'ı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d397c-135">You can use Get-Member to see all the properties.</span></span> <span data-ttu-id="d397c-136">Bir WMI sınıfının özelliklerine gibi diğer nesne özellikleri otomatik olarak kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="d397c-136">The properties of a WMI class are automatically available like other object properties:</span></span>

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

#### <a name="displaying-non-default-properties-with-format-cmdlets"></a><span data-ttu-id="d397c-137">Varsayılan olmayan özellikler biçim cmdlet'leri ile görüntüleme</span><span class="sxs-lookup"><span data-stu-id="d397c-137">Displaying Non-Default Properties with Format Cmdlets</span></span>

<span data-ttu-id="d397c-138">İçindeki bilgileri almak istiyorsanız **Win32_OperatingSystem** diğer bir deyişle sınıfının varsayılan olarak görüntülenmiyorsa, onu kullanarak görüntüleyebilirsiniz **biçimi** cmdlet'leri.</span><span class="sxs-lookup"><span data-stu-id="d397c-138">If you want information contained in the **Win32_OperatingSystem** class that is not displayed by default, you can display it by using the **Format** cmdlets.</span></span> <span data-ttu-id="d397c-139">Kullanılabilir bellek verilerini görüntülemek istiyorsanız, örneğin:</span><span class="sxs-lookup"><span data-stu-id="d397c-139">For example, if you want to display available memory data, type:</span></span>

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-Table -Property TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize TotalVisibleMemory FreePhysicalMemory FreeVirtualMemory FreeSpaceInPagingFiles
---------------------- ---------------    ------------------ -==--------------------- ---------------
               2097024          785904                305808           2056724                1558232
```

> [!NOTE]
> <span data-ttu-id="d397c-140">Özellik adlarında joker karakterler çalışın **Format-Table**, son işlem hattı öğesi için azaltılabilir `Format-Table -Property Total,Free`</span><span class="sxs-lookup"><span data-stu-id="d397c-140">Wildcards work with property names in **Format-Table**, so the final pipeline element can be reduced to `Format-Table -Property Total,Free`</span></span>

<span data-ttu-id="d397c-141">Bellek verileri daha okunabilir bir liste olarak yazarak biçimlendirmek, olabilir:</span><span class="sxs-lookup"><span data-stu-id="d397c-141">The memory data might be more readable if you format it as a list by typing:</span></span>

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-List TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize : 2097024
TotalVisibleMemorySize : 785904
FreePhysicalMemory     : 301876
FreeVirtualMemory      : 2056724
FreeSpaceInPagingFiles : 1556644
```
