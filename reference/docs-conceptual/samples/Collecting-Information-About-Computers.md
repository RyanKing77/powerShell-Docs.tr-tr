---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Bilgisayarlar Hakkında Bilgi Toplama
ms.assetid: 9e7b6a2d-34f7-4731-a92c-8b3382eb51bb
ms.openlocfilehash: d837684108656e17ebf26189bd4841c5de01051c
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293172"
---
# <a name="collecting-information-about-computers"></a>Bilgisayarlar Hakkında Bilgi Toplama

Cmdlet'leri **CimCmdlets** modülü genel sistem yönetim görevleri için en önemli cmdlet'leri şunlardır.
Tüm kritik alt sistemi ayarlarını, WMI aracılığıyla sunulur.
Ayrıca, WMI veri bir veya daha fazla öğe koleksiyonları olan nesneler olarak değerlendirir.
Windows PowerShell de nesneleri ile çalışır ve tek veya birden çok nesne aynı şekilde davranma olanak tanıyan bir işlem hattına sahip olduğundan, genel WMI erişim çok az iş ile Gelişmiş bazı görevleri gerçekleştirmenize olanak sağlar.

Aşağıdaki örnekler kullanarak belirli bilgiler toplamak nasıl göstermektedir `Get-CimInstance` rastgele bir bilgisayara karşı.
Belirttiğimiz **ComputerName** nokta parametresi (**.**), yerel bilgisayarı temsil eder.
Adı veya WMI aracılığıyla ulaşabileceği herhangi bir bilgisayar ile ilişkili IP adresi belirtebilirsiniz.
Yerel bilgisayar hakkında bilgi almak için atmanız **ComputerName** parametresi.

## <a name="listing-desktop-settings"></a>Masaüstü ayarlarını listeleme

Masaüstleri hakkında bilgi toplar yerel bilgisayarda bir komutla başlarsınız.

```powershell
Get-CimInstance -ClassName Win32_Desktop -ComputerName .
```

Bu, kullanımda olsun olmasın tüm masaüstleri için bilgi döndürür.

> [!NOTE]
> Bazı WMI sınıfları tarafından döndürülen bilgileri çok ayrıntılı ve genellikle WMI sınıfına ilişkin meta verileri içerir.
Bu meta veri özelliklerini çoğunu başlayan bir ada sahip olduğundan **CIM**, kullanarak özelliklerini filtreleyebilirsiniz `Select-Object`.
Belirtin **- ExcludeProperty** parametresiyle "Cim *" değeri.
Örneğin:

```powershell
Get-CimInstance -ClassName Win32_Desktop -ComputerName . | Select-Object -ExcludeProperty "CIM*"
```

Meta verileri filtrelemek için sonuçları göndermek için ardışık düzen işleci (|) kullanın `Get-CimInstance` komutunu `Select-Object -ExcludeProperty "CIM*"`.

## <a name="listing-bios-information"></a>BIOS bilgilerini listeleme

WMI **Win32_BIOS** sınıfı yerel bilgisayarda sistem BIOS'unun ilgili oldukça compact ve eksiksiz bilgileri döndürür:

```powershell
Get-CimInstance -ClassName Win32_BIOS -ComputerName .
```

## <a name="listing-processor-information"></a>İşlemci bilgilerini listeleme

WMI'ın kullanarak genel işlemci bilgilerini alabilir **Win32_Processor** sınıf, büyük olasılıkla bilgileri filtrelemek istersiniz ancak:

```powershell
Get-CimInstance -ClassName Win32_Processor -ComputerName . | Select-Object -ExcludeProperty "CIM*"
```

İşlemci ailesi için bir genel bir açıklama dizesi, yalnızca dönebilirsiniz **SystemType** özelliği:

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -ComputerName . | Select-Object -Property SystemType

SystemType
----------
X86-based PC
```

## <a name="listing-computer-manufacturer-and-model"></a>Bilgisayar üreticisi ve modeli listeleme

Bilgisayar modeli bilgileri bulunan ayrıca **Win32_ComputerSystem**.
Standart görüntülenen çıktının filtreleme OEM verilerini sağlamak için gerekli değildir:

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem
```

```output
Name PrimaryOwnerName Domain    TotalPhysicalMemory Model                   Manufacturer
---- ---------------- ------    ------------------- -----                   ------------
MyPC Jane Doe         WORKGROUP 804765696           DA243A-ABA 6415cl NA910 Compaq Presario 06
```

Bunun gibi bazı donanım doğrudan döndürmesini, komutları, çıkışı yalnızca sahip olduğunuz verilerin kadar iyidir.
Bazı bilgiler donanım üreticileri tarafından düzgün yapılandırılmamış olabilir ve bu nedenle kullanılamıyor olabilir.

## <a name="listing-installed-hotfixes"></a>Liste düzeltmelerin yüklü

Kullanarak yüklü tüm düzeltmeleri listeleyebilirsiniz **Win32_QuickFixEngineering**:

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName .
```

Bu sınıf, şuna benzer düzeltmelerin listesi döndürür:

```output
Source Description     HotFixID  InstalledBy   InstalledOn PSComputerName
------ -----------     --------  -----------   ----------- --------------
       Security Update KB4048951 Administrator 12/16/2017  .
```

Daha fazla Sözün çıkış için bazı özellikler dışlamak isteyebilirsiniz.
Kullanabilirsiniz, ancak `Get-CimInstance`'s **özelliği** yalnızca seçmek için parametre **HotfixID**, bunun yapılması bu nedenle gerçekten döndürür daha fazla bilgi için varsayılan olarak tüm meta verilerin görüntülendiğinden:

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

Çünkü ek veriler döndürülür özelliği parametreyi `Get-CimInstance` nesne Windows PowerShell'e döndürüldükten WMI sınıf örneği döndürülen özelliklerini sınırlar.
Çıkış azaltmak için kullanma `Select-Object`:

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName . -Property HotFixId | Select-Object -Property HotFixId
```

```output
HotFixId
--------
KB4048951
```

## <a name="listing-operating-system-version-information"></a>İşletim sistemi sürüm bilgilerini listeleme

**Win32_OperatingSystem** sınıfı özellikleri, sürüm ve hizmet paketi bilgileri içerir.
Gelen Özet sürüm bilgisi almak için bu özellikler yalnızca açıkça seçebilirsiniz **Win32_OperatingSystem**:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property BuildNumber,BuildType,OSType,ServicePackMajorVersion,ServicePackMinorVersion
```

Joker karakter olarak kullanabilirsiniz `Select-Object`'s **özelliği** parametresi.
Çünkü ile başlayan tüm özellikleri **derleme** veya **hizmetpaketi** kullanmak için önemli olan burada, biz bunu aşağıdaki forma kısaltabilir:

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

## <a name="listing-local-users-and-owner"></a>Yerel Kullanıcılar ve sahibi listeleme

Yerel genel kullanıcı bilgilerini — lisanslı kullanıcı sayısı, kullanıcılar ve sahibi adı geçerli sayısı — bir seçimle bulunabilir **Win32_OperatingSystem** sınıfının özellikleri.
Şu şekilde görüntülenecek özellikleri açıkça seçebilirsiniz:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property NumberOfLicensedUsers,NumberOfUsers,RegisteredUser
```

Joker karakterler kullanarak daha birleştiren bir sürümdür:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property *user*
```

## <a name="getting-available-disk-space"></a>Kullanılabilir Disk alanı alma

Yerel sürücüler için boş alan ve disk alanı görmek için Win32_LogicalDisk WMI sınıfını kullanabilirsiniz.
Yalnızca 3 ile bir DriveType örneklerini görmek için ihtiyacınız — sabit diskler için WMI kullanır değer.

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

## <a name="getting-logon-session-information"></a>Oturum açma oturum bilgilerini alma

Kullanıcılara ilişkili oturum açma oturumu hakkında genel bilgi alabilirsiniz **Win32_LogonSession** WMI sınıf:

```powershell
Get-CimInstance -ClassName Win32_LogonSession -ComputerName .
```

## <a name="getting-the-user-logged-on-to-a-computer"></a>Bir bilgisayarda oturum açmış kullanıcı alınıyor

Win32_ComputerSystem kullanarak belirli bir bilgisayar sistemi için oturum açan kullanıcının görüntüleyebilirsiniz.
Bu komut, yalnızca sistem masaüstüne oturum açan kullanıcının döndürür:

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -Property UserName -ComputerName .
```

## <a name="getting-local-time-from-a-computer"></a>Bir bilgisayardan yerel saati alma

Belirli bir bilgisayardaki geçerli yerel saat kullanarak alabilirsiniz **Win32_LocalTime** WMI sınıf.

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

## <a name="displaying-service-status"></a>Hizmet durumunu görüntüleme

Belirli bir bilgisayardaki tüm hizmetlerin durumunu görüntülemek için yerel olarak kullanabileceğiniz `Get-Service` cmdlet'i.
Uzak sistemleri için kullanabileceğiniz **Win32_Service** WMI sınıf.
Ayrıca kullanırsanız `Select-Object` sonuçları filtrelemek için **durumu**, **adı**, ve **DisplayName**, çıktı biçimi neredeyseaynıolacaktır`Get-Service`:

```powershell
Get-CimInstance -ClassName Win32_Service -ComputerName . | Select-Object -Property Status,Name,DisplayName
```

Bazen Hizmetleri için son derece uzun adları tam görünümünü sağlamak için kullanmak isteyebilirsiniz `Format-Table` ile **AutoSize** ve **kaydırma** sütun genişliğini iyileştirmek için parametreleri ve kesirli kısmı yerine sarmalamak uzun adları izin ver:

```powershell
Get-CimInstance -ClassName Win32_Service -ComputerName . | Format-Table -Property Status,Name,DisplayName -AutoSize -Wrap
```
