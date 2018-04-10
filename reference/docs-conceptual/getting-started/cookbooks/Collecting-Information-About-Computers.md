---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Bilgisayarlar Hakkında Bilgi Toplama
ms.assetid: 9e7b6a2d-34f7-4731-a92c-8b3382eb51bb
ms.openlocfilehash: c914a7133a1ac0a05346233db802175f7f29c6b2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="collecting-information-about-computers"></a><span data-ttu-id="ba90f-103">Bilgisayarlar Hakkında Bilgi Toplama</span><span class="sxs-lookup"><span data-stu-id="ba90f-103">Collecting Information About Computers</span></span>

<span data-ttu-id="ba90f-104">**Get-WmiObject** en önemli genel sistem için yönetim görevleri cmdlet'tir.</span><span class="sxs-lookup"><span data-stu-id="ba90f-104">**Get-WmiObject** is the most important cmdlet for general system management tasks.</span></span> <span data-ttu-id="ba90f-105">Tüm kritik alt sistemi ayarlarını, WMI aracılığıyla sunulur.</span><span class="sxs-lookup"><span data-stu-id="ba90f-105">All critical subsystem settings are exposed through WMI.</span></span> <span data-ttu-id="ba90f-106">Ayrıca, WMI veri bir veya daha fazla öğe koleksiyonlarında nesneler olarak davranır.</span><span class="sxs-lookup"><span data-stu-id="ba90f-106">Furthermore, WMI treats data as objects that are in collections of one or more items.</span></span> <span data-ttu-id="ba90f-107">Windows PowerShell de nesneler ile çalışır ve tek veya birden çok nesne aynı şekilde işlemek izin veren bir işlem hattına sahip olduğundan, çok az şey Gelişmiş bazı görevleri gerçekleştirmek genel WMI erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="ba90f-107">Because Windows PowerShell also works with objects and has a pipeline that allows you to treat single or multiple objects in the same way, generic WMI access allows you to perform some advanced tasks with very little work.</span></span>

<span data-ttu-id="ba90f-108">Aşağıdaki örnekler kullanarak belirli bilgiler toplamak nasıl göstermektedir **Get-WmiObject** rasgele bir bilgisayara karşı.</span><span class="sxs-lookup"><span data-stu-id="ba90f-108">The following examples demonstrate how to collect specific information by using **Get-WmiObject** against an arbitrary computer.</span></span> <span data-ttu-id="ba90f-109">Belirttiğimiz **ComputerName** nokta değeri parametreyle (**.**), yerel bilgisayarı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ba90f-109">We specify the **ComputerName** parameter with the dot value (**.**), which represents the local computer.</span></span> <span data-ttu-id="ba90f-110">Bir ad veya WMI aracılığıyla ulaşabilirsiniz herhangi bir bilgisayar ile ilişkili IP adresi belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba90f-110">You can specify a name or IP address associated with any computer you can reach through WMI.</span></span> <span data-ttu-id="ba90f-111">Yerel bilgisayar hakkında bilgi almak için kullanmayabilir **- ComputerName.**</span><span class="sxs-lookup"><span data-stu-id="ba90f-111">To retrieve information about the local computer, you could omit the **-ComputerName.**</span></span>

### <a name="listing-desktop-settings"></a><span data-ttu-id="ba90f-112">Masaüstü ayarlarını listeleme</span><span class="sxs-lookup"><span data-stu-id="ba90f-112">Listing Desktop Settings</span></span>

<span data-ttu-id="ba90f-113">Masaüstleri hakkında bilgi toplar yerel bilgisayarda bir komut ile başlayan.</span><span class="sxs-lookup"><span data-stu-id="ba90f-113">We'll begin with a command that collects information about the desktops on the local computer.</span></span>

```powershell
Get-WmiObject -Class Win32_Desktop -ComputerName .
```

<span data-ttu-id="ba90f-114">Kullanımda olsun olmasın bu tüm masaüstleri için bilgileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="ba90f-114">This returns information for all desktops, whether they are in use or not.</span></span>

> [!NOTE]
> <span data-ttu-id="ba90f-115">Bazı WMI sınıfları tarafından döndürülen bilgi çok ayrıntılı ve genellikle WMI sınıfına ilişkin meta verileri içerir.</span><span class="sxs-lookup"><span data-stu-id="ba90f-115">Information returned by some WMI classes can be very detailed, and often include metadata about the WMI class.</span></span> <span data-ttu-id="ba90f-116">Bu meta verileri özelliklerin çoğu çift alt çizgi ile başlayan adlara sahip olduğundan, Select-Object kullanarak özelliklerini filtre uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba90f-116">Because most of these metadata properties have names that begin with a double underscore, you can filter the properties using Select-Object.</span></span> <span data-ttu-id="ba90f-117">Kullanarak alfabetik karakterler ile başlayan özellikler belirtin **[a-z]**\* özellik değeri gibi.</span><span class="sxs-lookup"><span data-stu-id="ba90f-117">Specify only properties that begin with alphabetic characters by using **[a-z]**\* as the Property value.</span></span> <span data-ttu-id="ba90f-118">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="ba90f-118">For example:</span></span>

```powershell
Get-WmiObject -Class Win32_Desktop -ComputerName . | Select-Object -Property [a-z]*
```

<span data-ttu-id="ba90f-119">Meta verileri filtrelemek için bir ardışık düzen işleci (|) Get-WmiObject komutunun sonuçlarını için göndermektir \*\* Select-Object - özelliği [a-z] \*\*\*.</span><span class="sxs-lookup"><span data-stu-id="ba90f-119">To filter out the metadata, use a pipeline operator (|) to send the results of the Get-WmiObject command to \*\*Select-Object -Property [a-z]\*\*\*.</span></span>

### <a name="listing-bios-information"></a><span data-ttu-id="ba90f-120">BIOS bilgilerini listeleme</span><span class="sxs-lookup"><span data-stu-id="ba90f-120">Listing BIOS Information</span></span>

<span data-ttu-id="ba90f-121">WMI Win32_BIOS sınıfı yerel bilgisayarda sistem BIOS'unun oldukça compact ve eksiksiz bilgilerini döndürür:</span><span class="sxs-lookup"><span data-stu-id="ba90f-121">The WMI Win32_BIOS class returns fairly compact and complete information about the system BIOS on the local computer:</span></span>

```powershell
Get-WmiObject -Class Win32_BIOS -ComputerName .
```

### <a name="listing-processor-information"></a><span data-ttu-id="ba90f-122">İşlemci bilgileri listeleme</span><span class="sxs-lookup"><span data-stu-id="ba90f-122">Listing Processor Information</span></span>

<span data-ttu-id="ba90f-123">WMI'ın kullanarak genel işlemci bilgileri alabilirsiniz **Win32_Processor** bilgileri filtrelemek büyük olasılıkla isteyeceksiniz rağmen sınıf:</span><span class="sxs-lookup"><span data-stu-id="ba90f-123">You can retrieve general processor information by using WMI's **Win32_Processor** class, although you will likely want to filter the information:</span></span>

```powershell
Get-WmiObject -Class Win32_Processor -ComputerName . | Select-Object -Property [a-z]*
```

<span data-ttu-id="ba90f-124">İşlemci ailesi için bir genel açıklama dizesi, hemen dönebilirsiniz **SystemType** özelliği:</span><span class="sxs-lookup"><span data-stu-id="ba90f-124">For a generic description string of the processor family, you can just return the **SystemType** property:</span></span>

```
PS> Get-WmiObject -Class Win32_ComputerSystem -ComputerName . | Select-Object -Property SystemType

SystemType
----------
X86-based PC
```

### <a name="listing-computer-manufacturer-and-model"></a><span data-ttu-id="ba90f-125">Bilgisayar üreticisi ve modeli listeleme</span><span class="sxs-lookup"><span data-stu-id="ba90f-125">Listing Computer Manufacturer and Model</span></span>

<span data-ttu-id="ba90f-126">Bilgisayar modeli bilgi edinilebilir de **Win32_ComputerSystem**.</span><span class="sxs-lookup"><span data-stu-id="ba90f-126">Computer model information is also available from **Win32_ComputerSystem**.</span></span> <span data-ttu-id="ba90f-127">Standart görüntülenen çıktının OEM veri sağlamak için hiçbir filtreleme gerekli değildir:</span><span class="sxs-lookup"><span data-stu-id="ba90f-127">The standard displayed output will not need any filtering to provide OEM data:</span></span>

```
PS> Get-WmiObject -Class Win32_ComputerSystem

Domain              : WORKGROUP
Manufacturer        : Compaq Presario 06
Model               : DA243A-ABA 6415cl NA910
Name                : MyPC
PrimaryOwnerName    : Jane Doe
TotalPhysicalMemory : 804765696
```

<span data-ttu-id="ba90f-128">Bunun gibi bazı donanım doğrudan döndürmesini, komutları, çıktısını yalnızca sahip olduğunuz verilerin kadar iyidir.</span><span class="sxs-lookup"><span data-stu-id="ba90f-128">Your output from commands such as this, which return information directly from some hardware, is only as good as the data you have.</span></span> <span data-ttu-id="ba90f-129">Bazı bilgiler donanım üreticileri tarafından düzgün yapılandırılmamış olabilir ve bu nedenle kullanılamıyor olması olabilir.</span><span class="sxs-lookup"><span data-stu-id="ba90f-129">Some information is not correctly configured by hardware manufacturers and may therefore be unavailable.</span></span>

### <a name="listing-installed-hotfixes"></a><span data-ttu-id="ba90f-130">Liste düzeltmelerinin yüklü</span><span class="sxs-lookup"><span data-stu-id="ba90f-130">Listing Installed Hotfixes</span></span>

<span data-ttu-id="ba90f-131">Kullanarak tüm yüklü olan düzeltmelerin listeleyebilirsiniz **Win32_QuickFixEngineering**:</span><span class="sxs-lookup"><span data-stu-id="ba90f-131">You can list all installed hotfixes by using **Win32_QuickFixEngineering**:</span></span>

```powershell
Get-WmiObject -Class Win32_QuickFixEngineering -ComputerName .
```

<span data-ttu-id="ba90f-132">Bu sınıf şöyle düzeltmelerin listesi döndürür:</span><span class="sxs-lookup"><span data-stu-id="ba90f-132">This class returns a list of hotfixes that looks like this:</span></span>

```output
Description         : Update for Windows XP (KB910437)
FixComments         : Update
HotFixID            : KB910437
Install Date        :
InstalledBy         : Administrator
InstalledOn         : 12/16/2005
Name                :
ServicePackInEffect : SP3
Status              :
```

<span data-ttu-id="ba90f-133">Daha kısa çıktı için bazı özellikler dışlamak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba90f-133">For more succinct output, you may want to exclude some properties.</span></span> <span data-ttu-id="ba90f-134">Kullanabilirsiniz ancak **Get-WmiObject'ın özellik** yalnızca seçmek için parametre **HotfixID**, bunu yapmak şekilde gerçekte döndürecektir daha fazla bilgi için varsayılan olarak tüm meta verilerin görüntülendiğinden:</span><span class="sxs-lookup"><span data-stu-id="ba90f-134">Although you can use the **Get-WmiObject's Property** parameter to choose only the **HotFixID**, doing so will actually return more information, because all the metadata is displayed by default:</span></span>

```
PS> Get-WmiObject -Class Win32_QuickFixEngineering -ComputerName . -Property HotFixID

HotFixID         : KB910437
__GENUS          : 2
__CLASS          : Win32_QuickFixEngineering
__SUPERCLASS     :
__DYNASTY        :
__RELPATH        :
__PROPERTY_COUNT : 1
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
```

<span data-ttu-id="ba90f-135">Çünkü ek veriler döndürülür özelliği parametresinde **Get-WmiObject** WMI sınıf örneği döndürülen özellikleri için Windows PowerShell nesnesi döndürülen kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="ba90f-135">The additional data is returned, because the Property parameter in **Get-WmiObject** restricts the properties returned from WMI class instances, not the object returned to Windows PowerShell.</span></span> <span data-ttu-id="ba90f-136">Çıktı azaltmak için kullanma **Select-Object**:</span><span class="sxs-lookup"><span data-stu-id="ba90f-136">To reduce the output, use **Select-Object**:</span></span>

```
PS> Get-WmiObject -Class Win32_QuickFixEngineering -ComputerName . -Property HotFixId | Select-Object -Property HotFixId

HotFixId
--------
KB910437
```

### <a name="listing-operating-system-version-information"></a><span data-ttu-id="ba90f-137">İşletim sistemi sürüm bilgisi listeleme</span><span class="sxs-lookup"><span data-stu-id="ba90f-137">Listing Operating System Version Information</span></span>

<span data-ttu-id="ba90f-138">**Win32_OperatingSystem** sınıf özelliklerini sürüm ve hizmet paketi bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="ba90f-138">The **Win32_OperatingSystem** class properties include version and service pack information.</span></span> <span data-ttu-id="ba90f-139">Sürüm bilgileri gelen Özet almak için bu özellikleri yalnızca açıkça seçebilirsiniz **Win32_OperatingSystem**:</span><span class="sxs-lookup"><span data-stu-id="ba90f-139">You can explicitly select only these properties to get a version information summary from **Win32_OperatingSystem**:</span></span>

```powershell
Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property BuildNumber,BuildType,OSType,ServicePackMajorVersion,ServicePackMinorVersion
```

<span data-ttu-id="ba90f-140">Joker karakter olarak da kullanabilirsiniz **Seç-nesnenin özelliği** parametresi.</span><span class="sxs-lookup"><span data-stu-id="ba90f-140">You can also use wildcards with the **Select-Object's Property** parameter.</span></span> <span data-ttu-id="ba90f-141">Çünkü ile başlayan tüm özellikleri **yapı** veya **hizmetpaketi** kullanmak önemli olan burada, biz bu aşağıdaki formun kısaltabilir:</span><span class="sxs-lookup"><span data-stu-id="ba90f-141">Because all the properties beginning with either **Build** or **ServicePack** are important to use here, we can shorten this to the following form:</span></span>

```
PS> Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property Build*,OSType,ServicePack*

BuildNumber             : 2600
BuildType               : Uniprocessor Free
OSType                  : 18
ServicePackMajorVersion : 2
ServicePackMinorVersion : 0
```

### <a name="listing-local-users-and-owner"></a><span data-ttu-id="ba90f-142">Yerel Kullanıcılar ve sahibi listeleme</span><span class="sxs-lookup"><span data-stu-id="ba90f-142">Listing Local Users and Owner</span></span>

<span data-ttu-id="ba90f-143">Yerel genel kullanıcı bilgilerini — lisanslı kullanıcı sayısı, kullanıcı ve sahip adı geçerli sayısını — bir seçimi bulunabilir **Win32_OperatingSystem** özellikleri.</span><span class="sxs-lookup"><span data-stu-id="ba90f-143">Local general user information—number of licensed users, current number of users, and owner name—can be found with a selection of **Win32_OperatingSystem** properties.</span></span> <span data-ttu-id="ba90f-144">Bu gibi görüntülenecek özellikleri açıkça seçebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ba90f-144">You can explicitly select the properties to display like this:</span></span>

```powershell
Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property NumberOfLicensedUsers,NumberOfUsers,RegisteredUser
```

<span data-ttu-id="ba90f-145">Joker karakter kullanılması daha kısa bir sürümüdür:</span><span class="sxs-lookup"><span data-stu-id="ba90f-145">A more succinct version using wildcards is:</span></span>

```powershell
Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property *user*
```

### <a name="getting-available-disk-space"></a><span data-ttu-id="ba90f-146">Kullanılabilir Disk alanı alma</span><span class="sxs-lookup"><span data-stu-id="ba90f-146">Getting Available Disk Space</span></span>

<span data-ttu-id="ba90f-147">Yerel sürücüler için boş alan ve disk alanı görmek için WMI Win32_LogicalDisk sınıfını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba90f-147">To see the disk space and free space for local drives, you can use the WMI Win32_LogicalDisk class.</span></span> <span data-ttu-id="ba90f-148">Yalnızca 3 bir DriveType ile örnekleri görmek gereken — sabit diskler için WMI kullanır değer.</span><span class="sxs-lookup"><span data-stu-id="ba90f-148">You need to see only instances with a DriveType of 3—the value WMI uses for fixed hard disks.</span></span>

```
PS> Get-WmiObject -Class Win32_LogicalDisk -Filter "DriveType=3" -ComputerName .

DeviceID     : C:
DriveType    : 3
ProviderName :
FreeSpace    : 65541357568
Size         : 203912880128
VolumeName   : Local Disk

DeviceID     : Q:
DriveType    : 3
ProviderName :
FreeSpace    : 44298250240
Size         : 122934034432
VolumeName   : New Volume

PS> Get-WmiObject -Class Win32_LogicalDisk -Filter "DriveType=3" -ComputerName . | Measure-Object -Property FreeSpace,Size -Sum | Select-Object -Property Property,Sum

Property           Sum
--------           ---
FreeSpace 109839607808
Size      326846914560
```

### <a name="getting-logon-session-information"></a><span data-ttu-id="ba90f-149">Oturum açma oturumu bilgi alma</span><span class="sxs-lookup"><span data-stu-id="ba90f-149">Getting Logon Session Information</span></span>

<span data-ttu-id="ba90f-150">WMI Win32_LogonSession sınıfı aracılığıyla kullanıcılarıyla ilişkili oturum açma oturumları hakkında genel bilgi alabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ba90f-150">You can get general information about logon sessions associated with users through the WMI Win32_LogonSession class:</span></span>

```powershell
Get-WmiObject -Class Win32_LogonSession -ComputerName .
```

### <a name="getting-the-user-logged-on-to-a-computer"></a><span data-ttu-id="ba90f-151">Bir bilgisayarda oturum açmış kullanıcı alma</span><span class="sxs-lookup"><span data-stu-id="ba90f-151">Getting the User Logged on to a Computer</span></span>

<span data-ttu-id="ba90f-152">Win32_ComputerSystem kullanarak belirli bir bilgisayar sistemi için oturum açan kullanıcının görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba90f-152">You can display the user logged on to a particular computer system using Win32_ComputerSystem.</span></span> <span data-ttu-id="ba90f-153">Bu komut, yalnızca sistem masaüstüne oturum açmış kullanıcı döndürür:</span><span class="sxs-lookup"><span data-stu-id="ba90f-153">This command returns only the user logged on to the system desktop:</span></span>

```powershell
Get-WmiObject -Class Win32_ComputerSystem -Property UserName -ComputerName .
```

### <a name="getting-local-time-from-a-computer"></a><span data-ttu-id="ba90f-154">Bir bilgisayarın yerel saati alma</span><span class="sxs-lookup"><span data-stu-id="ba90f-154">Getting Local Time from a Computer</span></span>

<span data-ttu-id="ba90f-155">Geçerli yerel saat belirli bir bilgisayardaki WMI Win32_LocalTime sınıfı kullanarak alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba90f-155">You can retrieve the current local time on a specific computer by using the WMI Win32_LocalTime class.</span></span> <span data-ttu-id="ba90f-156">Varsayılan olarak bu sınıfın tüm meta veriler görüntülediğinden kullanarak filtre isteyebilirsiniz **Select-Object**:</span><span class="sxs-lookup"><span data-stu-id="ba90f-156">Because this class by default displays all metadata, you may want to filter it using **Select-Object**:</span></span>

```
PS> Get-WmiObject -Class Win32_LocalTime -ComputerName . | Select-Object -Property [a-z]*

Day          : 15
DayOfWeek    : 4
Hour         : 12
Milliseconds :
Minute       : 11
Month        : 6
Quarter      : 2
Second       : 52
WeekInMonth  : 3
Year         : 2006
```

### <a name="displaying-service-status"></a><span data-ttu-id="ba90f-157">Hizmet durumunu görüntüleme</span><span class="sxs-lookup"><span data-stu-id="ba90f-157">Displaying Service Status</span></span>

<span data-ttu-id="ba90f-158">Belirli bir bilgisayardaki tüm hizmetlerin durumunu görüntülemek için yerel olarak kullanabileceğiniz **Get-Service** daha önce belirtildiği gibi cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="ba90f-158">To view the status of all services on a specific computer, you can locally use the **Get-Service** cmdlet as mentioned earlier.</span></span> <span data-ttu-id="ba90f-159">Uzak sistemler için WMI Win32_Service sınıfını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba90f-159">For remote systems, you can use the WMI Win32_Service class.</span></span> <span data-ttu-id="ba90f-160">Ayrıca kullanırsanız **Select-Object** sonuçlara filtre uygulamak için **durum**, **adı**, ve **DisplayName**, çıkış biçimi neredeyse olacaktır aynı **Get-Service**:</span><span class="sxs-lookup"><span data-stu-id="ba90f-160">If you also use **Select-Object** to filter the results to **Status**, **Name**, and **DisplayName**, the output format will be almost identical to that from **Get-Service**:</span></span>

```powershell
Get-WmiObject -Class Win32_Service -ComputerName . | Select-Object -Property Status,Name,DisplayName
```

<span data-ttu-id="ba90f-161">Zaman zaman Hizmetleri için bir ad çok uzun adlarıyla tam görünen izin vermek için kullanmak isteyebilirsiniz **Format-Table** ile **AutoSize** ve **sarmalamak** parametreleri , sütun genişliği en iyi duruma getirme ve kesilmiş yerine sarmalamak uzun adları izin vermek için:</span><span class="sxs-lookup"><span data-stu-id="ba90f-161">To allow the complete display of names for the occasional services with extremely long names, you may want to use **Format-Table** with the **AutoSize** and **Wrap** parameters, to optimize column width and allow long names to wrap instead of being truncated:</span></span>

```powershell
Get-WmiObject -Class Win32_Service -ComputerName . | Format-Table -Property Status,Name,DisplayName -AutoSize -Wrap
```