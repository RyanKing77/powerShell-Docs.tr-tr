---
ms.date: 06/03/2019
keywords: PowerShell cmdlet'i
title: Yazılım Yüklemeleri ile Çalışma
ms.openlocfilehash: 6d2111a332f0e8c1b545186d3d950e936aed1834
ms.sourcegitcommit: 4ec9e10647b752cc62b1eabb897ada3dc03c93eb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66830295"
---
# <a name="working-with-software-installations"></a>Yazılım Yüklemeleri ile Çalışma

Windows Installer'ı kullanmak üzere tasarlanmış uygulamalar WMI'nin erişilebilir **Win32_Product** sınıfı, ancak kullanımda tüm uygulamalar Windows Yükleyici kullanmaya hemen başlayın.
Alternatif kurulum yordamları kullanan uygulamalar, genellikle Windows Installer tarafından yönetilmez.
Bu uygulamalarla çalışmak için belirli teknik kararları uygulama geliştiricisi tarafından yapılan ve yükleyici yazılım bağlıdır. Örneğin, dosyaları bilgisayarınızdaki bir klasöre genellikle kopyalayarak yüklü uygulamaları burada ele alınan teknikleri kullanarak tarafından yönetilemez. Ele alınan teknikleri kullanarak klasörleri ve dosyaları bu uygulamaları yönetebilirsiniz [çalışma ile dosya ve klasörleri](Working-with-Files-and-Folders.md).

> [!CAUTION]
> **Win32_Product** sınıfı en iyi duruma getirilmiş sorgu değil. MSI sağlayıcısı yüklü olan tüm ürünleri listeleme sonra filtre ardışık olarak işlemek için tam listesi ayrıştırmak için kullanılacak WMI filtreleri joker karakter kullanan sorguları neden. Bu ayrıca, yüklü, doğrulama ve onarma yükleme paketleri, tutarlılık denetimi başlatır. Doğrulama, yavaş bir işlemdir ve olay günlüklerini hatalara neden olabilir. Daha fazla bilgi için arama [KB makalesi 974524](https://support.microsoft.com/help/974524).

## <a name="listing-windows-installer-applications"></a>Windows Installer uygulamaları listeleme

Windows Installer bir yerel veya uzak sistemde yüklü uygulamalar listelemek için aşağıdaki basit WMI sorgusunu kullanın:

```powershell
Get-CimInstance -Class Win32_Product |
  Where-Object Name -eq "Microsoft .NET Core Runtime - 2.1.2 (x64)"
```

```Output
Name               Caption                     Vendor                 Version      IdentifyingNumber
----               -------                     ------                 -------      -----------------
Microsoft .NET ... Microsoft .NET Core Runt... Microsoft Corporation  16.72.26629  {ACC73072-9AD5-416C-94B...
```

Tüm özelliklerini görüntülemek için **Win32_Product** nesne görüntülenecek kullanım **özellikleri** biçimlendirme cmdlet'lerinin parametresine gibi `Format-List` cmdlet'iyle değerini `*` (Tümü).

```powershell
Get-CimInstance -Class Win32_Product |
  Where-Object Name -eq "Microsoft .NET Core Runtime - 2.1.2 (x64)" |
    Format-List -Property *
```

```Output
Name                  : Microsoft .NET Core Runtime - 2.1.2 (x64)
Version               : 16.72.26629
InstallState          : 5
Caption               : Microsoft .NET Core Runtime - 2.1.2 (x64)
Description           : Microsoft .NET Core Runtime - 2.1.2 (x64)
IdentifyingNumber     : {ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}
SKUNumber             :
Vendor                : Microsoft Corporation
AssignmentType        : 1
HelpLink              :
HelpTelephone         :
InstallDate           : 20180816
InstallDate2          :
InstallLocation       :
InstallSource         : C:\ProgramData\Package Cache\{ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}v16.72.26629\
Language              : 1033
LocalPackage          : C:\WINDOWS\Installer\414c96e.msi
PackageCache          : C:\WINDOWS\Installer\414c96e.msi
PackageCode           : {D20AC783-1EC5-4A58-9277-F452F5EB9AD9}
PackageName           : dotnet-runtime-2.1.2-win-x64.msi
ProductID             :
RegCompany            :
RegOwner              :
Transforms            :
URLInfoAbout          :
URLUpdateInfo         :
WordCount             : 0
PSComputerName        :
CimClass              : root/cimv2:Win32_Product
CimInstanceProperties : {Caption, Description, IdentifyingNumber, Name...}
CimSystemProperties   : Microsoft.Management.Infrastructure.CimSystemProperties
```

Ya da kullanabileceğinizi `Get-CimInstance` **filtre** parametresini kullanarak yalnızca Microsoft .NET Framework 2. 0'ı seçin. Değerini **filtre** parametresi olmayan Windows PowerShell sözdizimi WMI Sorgu Dili (WQL) söz dizimini kullanır. Örneğin:

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='Microsoft .NET Core Runtime - 2.1.2 (x64)'" |
  Format-List -Property *
```

İlginizi çeken özellikleri listelemek için kullanın **özelliği** istenen özellikleri listelemek için biçimlendirme cmdlet'lerin parametre.

```powershell
Get-CimInstance -Class Win32_Product  -Filter "Name='Microsoft .NET Core Runtime - 2.1.2 (x64)'" |
  Format-List -Property Name,InstallDate,InstallLocation,PackageCache,Vendor,Version,IdentifyingNumber
```

```Output
Name              : Microsoft .NET Core Runtime - 2.1.2 (x64)
InstallDate       : 20180816
InstallLocation   :
PackageCache      : C:\WINDOWS\Installer\414c96e.msi
Vendor            : Microsoft Corporation
Version           : 16.72.26629
IdentifyingNumber : {ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}
```

## <a name="listing-all-uninstallable-applications"></a>Tüm Uninstallable uygulamaları listeleme

Çoğu standart uygulamaları Windows ile bir uninstaller kaydetmek için biz bunları Windows kayıt defterinde bulma tarafından yerel olarak çalışabilirsiniz. Bir sistemde her uygulamayı bulmak için garantili bir yolu yoktur. Ancak, tüm programlar görüntülenen listelerini bulmak olası **Program Ekle veya Kaldır**. **Program Ekle veya Kaldır** bu uygulamalar aşağıdaki kayıt defteri anahtarında bulur:

`HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Uninstall`.

Biz uygulamaları bulmak için bu anahtarı inceleyebilirsiniz. Kaldırma anahtarı görüntülemek daha kolay hale getirmek için şu PowerShell sürücüsünü bu kayıt defteri konumuna eşleyebilirsiniz:

```powershell
New-PSDrive -Name Uninstall -PSProvider Registry -Root HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall
```

```Output
Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Uninstall  Registry      HKEY_LOCAL_MACHINE\SOFTWARE\Micr...
```
Artık adlı bir sürücüsü sahibiz "Kaldır:" hızla ve kolayca uygulama yüklemeleri için aramak için kullanılabilir. Kayıt defteri anahtarlarını kaldırma sayısı sayılarak yüklü uygulamaların sayısını bulabiliriz: PowerShell sürücüsü:

```
(Get-ChildItem -Path Uninstall:).Count
459
```

Biz bu listeyi daha fazla uygulama çeşitli teknikler kullanarak başlayarak arayabilirsiniz **Get-Childıtem**. Uygulamaların bir listesini almak ve bunları kaydetmek için **$UninstallableApplications** değişken, aşağıdaki komutu kullanın:

```powershell
$UninstallableApplications = Get-ChildItem -Path Uninstall:
```

Kayıt defteri anahtarları kaldırma altında kayıt defteri girdilerinin değerlerini görüntülemek için kayıt defteri anahtarlarını GetValue yöntemini kullanın. Yöntem değeri kayıt defteri girişini adıdır.

Örneğin, Uninstall anahtarında uygulamaları görünen adlarını bulmak için aşağıdaki komutu kullanın:

```powershell
$UninstallableApplications | ForEach-Object -Process { $_.GetValue('DisplayName') }
```

Bu değerler benzersiz olmasını garanti yoktur. Aşağıdaki örnekte, "Windows Media Encoder 9 Serisi" yüklü iki öğe görünür:

```powershell
$UninstallableApplications | Where-Object -FilterScript { $_.GetValue("DisplayName") -eq "Windows Media Encoder 9 Series"}
```

```Output
Name                           Property
----                           --------
{ACC73072-9AD5-416C-94BF-D82DD AuthorizedCDFPrefix :
CEA0F1B}                       Comments            :
                               Contact             :
                               DisplayVersion      : 16.72.26629
                               HelpLink            :
                               HelpTelephone       :
                               InstallDate         : 20180816
                               InstallLocation     :
                               InstallSource       : C:\ProgramData\Package
                               Cache\{ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}v16.72.26629\
                               ModifyPath          : MsiExec.exe /X{ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}
                               NoModify            : 1
                               Publisher           : Microsoft Corporation
                               Readme              :
                               Size                :
                               EstimatedSize       : 67156
                               SystemComponent     : 1
                               UninstallString     : MsiExec.exe /X{ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}
                               URLInfoAbout        :
                               URLUpdateInfo       :
                               VersionMajor        : 16
                               VersionMinor        : 72
                               WindowsInstaller    : 1
                               Version             : 273180677
                               Language            : 1033
                               DisplayName         : Microsoft .NET Core Runtime - 2.1.2 (x64)
```

## <a name="installing-applications"></a>Uygulamaları yükleme

Kullanabileceğiniz **Win32_Product** Windows Installer paketleri uzaktan veya yerel olarak yüklemek için sınıf.

> [!NOTE]
> Bir uygulamayı yüklemek için PowerShell "Yönetici olarak çalıştır" seçeneğiyle başlatmanız gerekir.

WMI alt PowerShell yolları anlamıyor çünkü .msi paketin yolu belirtmek için bir Evrensel Adlandırma Kuralı (UNC) ağ yolu uzaktan yüklerken kullanın. Örneğin, NewPackage.msi paketini yüklemek için bulunan ağ paylaşımına `\\AppServ\dsp` uzak bilgisayarda PC01 PowerShell komut isteminde aşağıdaki komutu yazın:

```powershell
Invoke-CimMethod -ClassName Win32_Product -MethodName Install -Arguments @{PackageLocation='\\AppSrv\dsp\NewPackage.msi'}
```

Windows Yükleyici teknolojisi kullanmayan uygulamalar, otomatik dağıtım için uygulamaya özgü yöntemleri olabilir. Uygulama için belgelere bakın veya uygulama satıcısının destek sistemi başvurun.

## <a name="removing-applications"></a>Uygulamaları kaldırma

PowerShell kullanarak bir Windows Installer paketi kaldırma paket yükleme yaklaşık aynı şekilde çalışır. Kaldırmak için paket adına göre seçen bir örneği aşağıda verilmiştir; Bazı durumlarda ile filtrelemek daha kolay olabilir **Identifyingnumber**:

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='ILMerge'" | Invoke-CimMethod -MethodName Uninstall
```

Diğer uygulamaları kaldırma bile yerel olarak işiniz bittiğinde konu bu kadar basit değil. Komut satırı kaldırma dizeleri için bu uygulamaları ayıklayarak bulabiliriz **UninstallString** özelliği.
Bu yöntem, kaldırma anahtarı altında görünen eski programları ve Windows Installer uygulamaları için çalışır:

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

İsterseniz, görünen ada göre çıkışı filtreleyebilirsiniz:

```powershell
Get-ChildItem -Path Uninstall: |
    Where-Object -FilterScript { $_.GetValue('DisplayName') -like 'Win*'} |
        ForEach-Object -Process { $_.GetValue('UninstallString') }
```

Ancak, bu dizeler PowerShell isteminden bazı değişiklik yapmadan doğrudan kullanılabilir olmayabilir.

## <a name="upgrading-windows-installer-applications"></a>Windows Installer uygulamalarını yükseltme

Bir uygulamayı yükseltmek için uygulama yükseltme paketini uygulama ve yolun adını bilmeniz gerekir. Bu bilgileri kullanarak tek bir PowerShell komutu ile bir uygulama yükseltebilirsiniz:

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='OldAppName'" |
  Invoke-CimMethod -MethodName Upgrade -Arguments @{PackageLocation='\\AppSrv\dsp\OldAppUpgrade.msi'}
```
