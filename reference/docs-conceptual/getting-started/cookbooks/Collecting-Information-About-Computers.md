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
# <a name="collecting-information-about-computers"></a>Bilgisayarlar Hakkında Bilgi Toplama

**Get-WmiObject** en önemli genel sistem için yönetim görevleri cmdlet'tir. Tüm kritik alt sistemi ayarlarını, WMI aracılığıyla sunulur. Ayrıca, WMI veri bir veya daha fazla öğe koleksiyonlarında nesneler olarak davranır. Windows PowerShell de nesneler ile çalışır ve tek veya birden çok nesne aynı şekilde işlemek izin veren bir işlem hattına sahip olduğundan, çok az şey Gelişmiş bazı görevleri gerçekleştirmek genel WMI erişim sağlar.

Aşağıdaki örnekler kullanarak belirli bilgiler toplamak nasıl göstermektedir **Get-WmiObject** rasgele bir bilgisayara karşı. Belirttiğimiz **ComputerName** nokta değeri parametreyle (**.**), yerel bilgisayarı temsil eder. Bir ad veya WMI aracılığıyla ulaşabilirsiniz herhangi bir bilgisayar ile ilişkili IP adresi belirtebilirsiniz. Yerel bilgisayar hakkında bilgi almak için kullanmayabilir **- ComputerName.**

### <a name="listing-desktop-settings"></a>Masaüstü ayarlarını listeleme

Masaüstleri hakkında bilgi toplar yerel bilgisayarda bir komut ile başlayan.

```powershell
Get-WmiObject -Class Win32_Desktop -ComputerName .
```

Kullanımda olsun olmasın bu tüm masaüstleri için bilgileri döndürür.

> [!NOTE]
> Bazı WMI sınıfları tarafından döndürülen bilgi çok ayrıntılı ve genellikle WMI sınıfına ilişkin meta verileri içerir. Bu meta verileri özelliklerin çoğu çift alt çizgi ile başlayan adlara sahip olduğundan, Select-Object kullanarak özelliklerini filtre uygulayabilirsiniz. Kullanarak alfabetik karakterler ile başlayan özellikler belirtin **[a-z]*** özellik değeri gibi. Örneğin:

```powershell
Get-WmiObject -Class Win32_Desktop -ComputerName . | Select-Object -Property [a-z]*
```

Meta verileri filtrelemek için bir ardışık düzen işleci (|) Get-WmiObject komutunun sonuçlarını için göndermektir ** Select-Object - özelliği [a-z] ***.

### <a name="listing-bios-information"></a>BIOS bilgilerini listeleme

WMI Win32_BIOS sınıfı yerel bilgisayarda sistem BIOS'unun oldukça compact ve eksiksiz bilgilerini döndürür:

```powershell
Get-WmiObject -Class Win32_BIOS -ComputerName .
```

### <a name="listing-processor-information"></a>İşlemci bilgileri listeleme

WMI'ın kullanarak genel işlemci bilgileri alabilirsiniz **Win32_Processor** bilgileri filtrelemek büyük olasılıkla isteyeceksiniz rağmen sınıf:

```powershell
Get-WmiObject -Class Win32_Processor -ComputerName . | Select-Object -Property [a-z]*
```

İşlemci ailesi için bir genel açıklama dizesi, hemen dönebilirsiniz **SystemType** özelliği:

```
PS> Get-WmiObject -Class Win32_ComputerSystem -ComputerName . | Select-Object -Property SystemType

SystemType
----------
X86-based PC
```

### <a name="listing-computer-manufacturer-and-model"></a>Bilgisayar üreticisi ve modeli listeleme

Bilgisayar modeli bilgi edinilebilir de **Win32_ComputerSystem**. Standart görüntülenen çıktının OEM veri sağlamak için hiçbir filtreleme gerekli değildir:

```
PS> Get-WmiObject -Class Win32_ComputerSystem

Domain              : WORKGROUP
Manufacturer        : Compaq Presario 06
Model               : DA243A-ABA 6415cl NA910
Name                : MyPC
PrimaryOwnerName    : Jane Doe
TotalPhysicalMemory : 804765696
```

Bunun gibi bazı donanım doğrudan döndürmesini, komutları, çıktısını yalnızca sahip olduğunuz verilerin kadar iyidir. Bazı bilgiler donanım üreticileri tarafından düzgün yapılandırılmamış olabilir ve bu nedenle kullanılamıyor olması olabilir.

### <a name="listing-installed-hotfixes"></a>Liste düzeltmelerinin yüklü

Kullanarak tüm yüklü olan düzeltmelerin listeleyebilirsiniz **Win32_QuickFixEngineering**:

```powershell
Get-WmiObject -Class Win32_QuickFixEngineering -ComputerName .
```

Bu sınıf şöyle düzeltmelerin listesi döndürür:

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

Daha kısa çıktı için bazı özellikler dışlamak isteyebilirsiniz. Kullanabilirsiniz ancak **Get-WmiObject'ın özellik** yalnızca seçmek için parametre **HotfixID**, bunu yapmak şekilde gerçekte döndürecektir daha fazla bilgi için varsayılan olarak tüm meta verilerin görüntülendiğinden:

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

Çünkü ek veriler döndürülür özelliği parametresinde **Get-WmiObject** WMI sınıf örneği döndürülen özellikleri için Windows PowerShell nesnesi döndürülen kısıtlar. Çıktı azaltmak için kullanma **Select-Object**:

```
PS> Get-WmiObject -Class Win32_QuickFixEngineering -ComputerName . -Property HotFixId | Select-Object -Property HotFixId

HotFixId
--------
KB910437
```

### <a name="listing-operating-system-version-information"></a>İşletim sistemi sürüm bilgisi listeleme

**Win32_OperatingSystem** sınıf özelliklerini sürüm ve hizmet paketi bilgileri içerir. Sürüm bilgileri gelen Özet almak için bu özellikleri yalnızca açıkça seçebilirsiniz **Win32_OperatingSystem**:

```powershell
Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property BuildNumber,BuildType,OSType,ServicePackMajorVersion,ServicePackMinorVersion
```

Joker karakter olarak da kullanabilirsiniz **Seç-nesnenin özelliği** parametresi. Çünkü ile başlayan tüm özellikleri **yapı** veya **hizmetpaketi** kullanmak önemli olan burada, biz bu aşağıdaki formun kısaltabilir:

```
PS> Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property Build*,OSType,ServicePack*

BuildNumber             : 2600
BuildType               : Uniprocessor Free
OSType                  : 18
ServicePackMajorVersion : 2
ServicePackMinorVersion : 0
```

### <a name="listing-local-users-and-owner"></a>Yerel Kullanıcılar ve sahibi listeleme

Yerel genel kullanıcı bilgilerini — lisanslı kullanıcı sayısı, kullanıcı ve sahip adı geçerli sayısını — bir seçimi bulunabilir **Win32_OperatingSystem** özellikleri. Bu gibi görüntülenecek özellikleri açıkça seçebilirsiniz:

```powershell
Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property NumberOfLicensedUsers,NumberOfUsers,RegisteredUser
```

Joker karakter kullanılması daha kısa bir sürümüdür:

```powershell
Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property *user*
```

### <a name="getting-available-disk-space"></a>Kullanılabilir Disk alanı alma

Yerel sürücüler için boş alan ve disk alanı görmek için WMI Win32_LogicalDisk sınıfını kullanabilirsiniz. Yalnızca 3 bir DriveType ile örnekleri görmek gereken — sabit diskler için WMI kullanır değer.

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

### <a name="getting-logon-session-information"></a>Oturum açma oturumu bilgi alma

WMI Win32_LogonSession sınıfı aracılığıyla kullanıcılarıyla ilişkili oturum açma oturumları hakkında genel bilgi alabilirsiniz:

```powershell
Get-WmiObject -Class Win32_LogonSession -ComputerName .
```

### <a name="getting-the-user-logged-on-to-a-computer"></a>Bir bilgisayarda oturum açmış kullanıcı alma

Win32_ComputerSystem kullanarak belirli bir bilgisayar sistemi için oturum açan kullanıcının görüntüleyebilirsiniz. Bu komut, yalnızca sistem masaüstüne oturum açmış kullanıcı döndürür:

```powershell
Get-WmiObject -Class Win32_ComputerSystem -Property UserName -ComputerName .
```

### <a name="getting-local-time-from-a-computer"></a>Bir bilgisayarın yerel saati alma

Geçerli yerel saat belirli bir bilgisayardaki WMI Win32_LocalTime sınıfı kullanarak alabilirsiniz. Varsayılan olarak bu sınıfın tüm meta veriler görüntülediğinden kullanarak filtre isteyebilirsiniz **Select-Object**:

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

### <a name="displaying-service-status"></a>Hizmet durumunu görüntüleme

Belirli bir bilgisayardaki tüm hizmetlerin durumunu görüntülemek için yerel olarak kullanabileceğiniz **Get-Service** daha önce belirtildiği gibi cmdlet'i. Uzak sistemler için WMI Win32_Service sınıfını kullanabilirsiniz. Ayrıca kullanırsanız **Select-Object** sonuçlara filtre uygulamak için **durum**, **adı**, ve **DisplayName**, çıkış biçimi neredeyse olacaktır aynı **Get-Service**:

```powershell
Get-WmiObject -Class Win32_Service -ComputerName . | Select-Object -Property Status,Name,DisplayName
```

Zaman zaman Hizmetleri için bir ad çok uzun adlarıyla tam görünen izin vermek için kullanmak isteyebilirsiniz **Format-Table** ile **AutoSize** ve **sarmalamak** parametreleri , sütun genişliği en iyi duruma getirme ve kesilmiş yerine sarmalamak uzun adları izin vermek için:

```powershell
Get-WmiObject -Class Win32_Service -ComputerName . | Format-Table -Property Status,Name,DisplayName -AutoSize -Wrap
```