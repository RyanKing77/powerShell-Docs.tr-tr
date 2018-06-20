---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Bilgisayarlar Hakkında Bilgi Toplama
ms.assetid: 9e7b6a2d-34f7-4731-a92c-8b3382eb51bb
ms.openlocfilehash: ca92474eaf6fa546c3d6450f5a282e45157018a8
ms.sourcegitcommit: 4a841ebda3339ae2477e0f5f5be8c01740221232
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33677323"
---
# <a name="collecting-information-about-computers"></a>Bilgisayarlar Hakkında Bilgi Toplama

Cmdlet'leri **CimCmdlets** modülü olan genel sistem yönetim görevleri için en önemli cmdlet'leri.
Tüm kritik alt sistemi ayarlarını, WMI aracılığıyla sunulur.
Ayrıca, WMI veri bir veya daha fazla öğe koleksiyonlarında nesneler olarak davranır.
Windows PowerShell de nesneler ile çalışır ve tek veya birden çok nesne aynı şekilde işlemek izin veren bir işlem hattına sahip olduğundan, çok az şey Gelişmiş bazı görevleri gerçekleştirmek genel WMI erişim sağlar.

Aşağıdaki örnekler kullanarak belirli bilgiler toplamak nasıl göstermektedir `Get-CimInstance` rasgele bir bilgisayara karşı.
Belirttiğimiz **ComputerName** nokta değeri parametreyle (**.**), yerel bilgisayarı temsil eder.
Bir ad veya WMI aracılığıyla ulaşabilirsiniz herhangi bir bilgisayar ile ilişkili IP adresi belirtebilirsiniz.
Yerel bilgisayar hakkında bilgi almak için kullanmayabilir **ComputerName** parametresi.

### <a name="listing-desktop-settings"></a>Masaüstü ayarlarını listeleme

Masaüstleri hakkında bilgi toplar yerel bilgisayarda bir komut ile başlayan.

```powershell
Get-CimInstance -ClassName Win32_Desktop -ComputerName .
```

Kullanımda olsun olmasın bu tüm masaüstleri için bilgileri döndürür.

> [!NOTE]
> Bazı WMI sınıfları tarafından döndürülen bilgi çok ayrıntılı ve genellikle WMI sınıfına ilişkin meta verileri içerir.
Bu meta verileri özelliklerin çoğu ile başlayan adlara sahip olduğundan **CIM**, kullanarak özelliklerini filtreleyebilirsiniz `Select-Object`.
Belirtin **- ExcludeProperty** parametresiyle "CIM *" değeri olarak.
Örneğin:

```powershell
Get-CimInstance -ClassName Win32_Desktop -ComputerName . | Select-Object -ExcludeProperty "CIM*"
```

Meta verileri filtrelemek için sonuçlarını göndermek için bir ardışık düzen işleci (|) kullanın `Get-CimInstance` komutu `Select-Object -ExcludeProperty "CIM*"`.

### <a name="listing-bios-information"></a>BIOS bilgilerini listeleme

WMI **Win32_BIOS** sınıfı yerel bilgisayarda oldukça compact ve tam sistem BIOS'unun hakkında bilgi verir:

```powershell
Get-CimInstance -ClassName Win32_BIOS -ComputerName .
```

### <a name="listing-processor-information"></a>İşlemci bilgileri listeleme

WMI'ın kullanarak genel işlemci bilgileri alabilirsiniz **Win32_Processor** bilgileri filtrelemek büyük olasılıkla isteyeceksiniz rağmen sınıf:

```powershell
Get-CimInstance -ClassName Win32_Processor -ComputerName . | Select-Object -ExcludeProperty "CIM*"
```

İşlemci ailesi için bir genel açıklama dizesi, hemen dönebilirsiniz **SystemType** özelliği:

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -ComputerName . | Select-Object -Property SystemType

SystemType
----------
X86-based PC
```

### <a name="listing-computer-manufacturer-and-model"></a>Bilgisayar üreticisi ve modeli listeleme

Bilgisayar modeli bilgi edinilebilir de **Win32_ComputerSystem**.
Standart görüntülenen çıktının OEM veri sağlamak için hiçbir filtreleme gerekli değildir:

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem
```

```output
Name PrimaryOwnerName Domain    TotalPhysicalMemory Model                   Manufacturer
---- ---------------- ------    ------------------- -----                   ------------
MyPC Jane Doe         WORKGROUP 804765696           DA243A-ABA 6415cl NA910 Compaq Presario 06
```

Bunun gibi bazı donanım doğrudan döndürmesini, komutları, çıktısını yalnızca sahip olduğunuz verilerin kadar iyidir.
Bazı bilgiler donanım üreticileri tarafından düzgün yapılandırılmamış olabilir ve bu nedenle kullanılamıyor olması olabilir.

### <a name="listing-installed-hotfixes"></a>Liste düzeltmelerinin yüklü

Kullanarak tüm yüklü olan düzeltmelerin listeleyebilirsiniz **Win32_QuickFixEngineering**:

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName .
```

Bu sınıf şöyle düzeltmelerin listesi döndürür:

```output
Source Description     HotFixID  InstalledBy   InstalledOn PSComputerName
------ -----------     --------  -----------   ----------- --------------
       Security Update KB4048951 Administrator 12/16/2017  .
```

Daha kısa çıktı için bazı özellikler dışlamak isteyebilirsiniz.
Kullanabilirsiniz ancak `Get-CimInstance`'s **özelliği** yalnızca seçmek için parametre **HotfixID**, bunu yapmak şekilde gerçekte döndürecektir daha fazla bilgi için varsayılan olarak tüm meta verilerin görüntülendiğinden:

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName . -Property HotFixID
```

```output
PSShowComputerName    : True
InstalledOn           :
Caption               :
Description           :
InstallDate           :
Name                  :
Status                :
CSName                :
FixComments           :
HotFixID              : KB4048951
InstalledBy           :
ServicePackInEffect   :
PSComputerName        : .
CimClass              : root/cimv2:Win32_QuickFixEngineering
CimInstanceProperties : {Caption, Description, InstallDate, Name...}
CimSystemProperties   : Microsoft.Management.Infrastructure.CimSystemProperties
```

Çünkü ek veriler döndürülür özelliği parametresinde `Get-CimInstance` WMI sınıf örneği döndürülen özellikleri için Windows PowerShell nesnesi döndürülen kısıtlar.
Çıktı azaltmak için kullanma `Select-Object`:

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName . -Property HotFixId | Select-Object -Property HotFixId
```

```output
HotFixId
--------
KB4048951
```

### <a name="listing-operating-system-version-information"></a>İşletim sistemi sürüm bilgisi listeleme

**Win32_OperatingSystem** sınıf özelliklerini sürüm ve hizmet paketi bilgileri içerir.
Sürüm bilgileri gelen Özet almak için bu özellikleri yalnızca açıkça seçebilirsiniz **Win32_OperatingSystem**:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property BuildNumber,BuildType,OSType,ServicePackMajorVersion,ServicePackMinorVersion
```

Joker karakter olarak da kullanabilirsiniz `Select-Object`'s **özelliği** parametresi.
Çünkü ile başlayan tüm özellikleri **yapı** veya **hizmetpaketi** kullanmak önemli olan burada, biz bu aşağıdaki formun kısaltabilir:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property Build*,OSType,ServicePack*
```

```output
BuildNumber             : 16299
BuildType               : Multiprocessor Free
OSType                  : 18
ServicePackMajorVersion : 0
ServicePackMinorVersion : 0
```

### <a name="listing-local-users-and-owner"></a>Yerel Kullanıcılar ve sahibi listeleme

Yerel genel kullanıcı bilgilerini — lisanslı kullanıcı sayısı, kullanıcı ve sahip adı geçerli sayısını — bir seçimi bulunabilir **Win32_OperatingSystem** sınıfı özellikleri.
Bu gibi görüntülenecek özellikleri açıkça seçebilirsiniz:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property NumberOfLicensedUsers,NumberOfUsers,RegisteredUser
```

Joker karakter kullanılması daha kısa bir sürümüdür:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property *user*
```

### <a name="getting-available-disk-space"></a>Kullanılabilir Disk alanı alma

Yerel sürücüler için boş alan ve disk alanı görmek için Win32_LogicalDisk WMI sınıfını kullanabilirsiniz.
Yalnızca 3 bir DriveType ile örnekleri görmek gereken — sabit diskler için WMI kullanır değer.

```powershell
Get-CimInstance -ClassName Win32_LogicalDisk -Filter "DriveType=3" -ComputerName .

DeviceID DriveType ProviderName VolumeName Size         FreeSpace   PSComputerName
-------- --------- ------------ ---------- ----         ---------   --------------
C:       3                      Local Disk 203912880128 65541357568 .
Q:       3                      New Volume 122934034432 44298250240 .

Get-CimInstance -ClassName Win32_LogicalDisk -Filter "DriveType=3" -ComputerName . | Measure-Object -Property FreeSpace,Size -Sum | Select-Object -Property Property,Sum

Property           Sum
--------           ---
FreeSpace 109839607808
Size      326846914560
```

### <a name="getting-logon-session-information"></a>Oturum açma oturumu bilgi alma

Kullanıcılara ilişkili oturum açma oturumları hakkındaki genel bilgileri elde edebilirsiniz **Win32_LogonSession** WMI sınıfı:

```powershell
Get-CimInstance -ClassName Win32_LogonSession -ComputerName .
```

### <a name="getting-the-user-logged-on-to-a-computer"></a>Bir bilgisayarda oturum açmış kullanıcı alma

Win32_ComputerSystem kullanarak belirli bir bilgisayar sistemi için oturum açan kullanıcının görüntüleyebilirsiniz.
Bu komut, yalnızca sistem masaüstüne oturum açmış kullanıcı döndürür:

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -Property UserName -ComputerName .
```

### <a name="getting-local-time-from-a-computer"></a>Bir bilgisayarın yerel saati alma

Belirli bir bilgisayardaki geçerli yerel saat kullanarak alabilirsiniz **Win32_LocalTime** WMI sınıfı.

```powershell
Get-CimInstance -ClassName Win32_LocalTime -ComputerName .

Day          : 15
DayOfWeek    : 4
Hour         : 12
Milliseconds :
Minute       : 11
Month        : 6
Quarter      : 2
Second       : 52
WeekInMonth  : 3
Year         : 2017
PSComputerName : .
```

### <a name="displaying-service-status"></a>Hizmet durumunu görüntüleme

Belirli bir bilgisayardaki tüm hizmetlerin durumunu görüntülemek için yerel olarak kullanabileceğiniz `Get-Service` cmdlet'i.
Uzak sistemler için kullandığınız **Win32_Service** WMI sınıfı.
Ayrıca kullanırsanız `Select-Object` sonuçlara filtre uygulamak için **durum**, **adı**, ve **DisplayName**, çıktı biçimi neredeyseaynıolacaktır`Get-Service`:

```powershell
Get-CimInstance -ClassName Win32_Service -ComputerName . | Select-Object -Property Status,Name,DisplayName
```

Zaman zaman Hizmetleri için bir ad çok uzun adlarıyla tam görünen izin vermek için kullanmak isteyebilirsiniz `Format-Table` ile **AutoSize** ve **sarmalamak** sütun genişliği en iyi duruma getirmek için parametreleri ve kesirli kısmı yerine sarmalamak uzun adları izin ver:

```powershell
Get-CimInstance -ClassName Win32_Service -ComputerName . | Format-Table -Property Status,Name,DisplayName -AutoSize -Wrap
```
