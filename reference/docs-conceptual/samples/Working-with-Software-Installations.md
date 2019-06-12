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
# <a name="working-with-software-installations"></a><span data-ttu-id="44613-103">Yazılım Yüklemeleri ile Çalışma</span><span class="sxs-lookup"><span data-stu-id="44613-103">Working with Software Installations</span></span>

<span data-ttu-id="44613-104">Windows Installer'ı kullanmak üzere tasarlanmış uygulamalar WMI'nin erişilebilir **Win32_Product** sınıfı, ancak kullanımda tüm uygulamalar Windows Yükleyici kullanmaya hemen başlayın.</span><span class="sxs-lookup"><span data-stu-id="44613-104">Applications that are designed to use Windows Installer can be accessed through WMI's **Win32_Product** class, but not all applications in use today use the Windows Installer.</span></span>
<span data-ttu-id="44613-105">Alternatif kurulum yordamları kullanan uygulamalar, genellikle Windows Installer tarafından yönetilmez.</span><span class="sxs-lookup"><span data-stu-id="44613-105">Applications that use alternate setup routines are not usually managed by the Windows Installer.</span></span>
<span data-ttu-id="44613-106">Bu uygulamalarla çalışmak için belirli teknik kararları uygulama geliştiricisi tarafından yapılan ve yükleyici yazılım bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="44613-106">Specific techniques for working with those applications depends on the installer software and decisions made by the application developer.</span></span> <span data-ttu-id="44613-107">Örneğin, dosyaları bilgisayarınızdaki bir klasöre genellikle kopyalayarak yüklü uygulamaları burada ele alınan teknikleri kullanarak tarafından yönetilemez.</span><span class="sxs-lookup"><span data-stu-id="44613-107">For example, applications installed by copying the files to a folder on the computer usually cannot be managed by using techniques discussed here.</span></span> <span data-ttu-id="44613-108">Ele alınan teknikleri kullanarak klasörleri ve dosyaları bu uygulamaları yönetebilirsiniz [çalışma ile dosya ve klasörleri](Working-with-Files-and-Folders.md).</span><span class="sxs-lookup"><span data-stu-id="44613-108">You can manage these applications as files and folders by using the techniques discussed in [Working With Files and Folders](Working-with-Files-and-Folders.md).</span></span>

> [!CAUTION]
> <span data-ttu-id="44613-109">**Win32_Product** sınıfı en iyi duruma getirilmiş sorgu değil.</span><span class="sxs-lookup"><span data-stu-id="44613-109">The **Win32_Product** class is not query optimized.</span></span> <span data-ttu-id="44613-110">MSI sağlayıcısı yüklü olan tüm ürünleri listeleme sonra filtre ardışık olarak işlemek için tam listesi ayrıştırmak için kullanılacak WMI filtreleri joker karakter kullanan sorguları neden.</span><span class="sxs-lookup"><span data-stu-id="44613-110">Queries that use wildcard filters cause WMI to use the MSI provider to enumerate all installed products then parse the full list sequentially to handle the filter.</span></span> <span data-ttu-id="44613-111">Bu ayrıca, yüklü, doğrulama ve onarma yükleme paketleri, tutarlılık denetimi başlatır.</span><span class="sxs-lookup"><span data-stu-id="44613-111">This also initiates a consistency check of packages installed, verifying and repairing the install.</span></span> <span data-ttu-id="44613-112">Doğrulama, yavaş bir işlemdir ve olay günlüklerini hatalara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="44613-112">The validation is a slow process and may result in errors in the event logs.</span></span> <span data-ttu-id="44613-113">Daha fazla bilgi için arama [KB makalesi 974524](https://support.microsoft.com/help/974524).</span><span class="sxs-lookup"><span data-stu-id="44613-113">For more information seek [KB article 974524](https://support.microsoft.com/help/974524).</span></span>

## <a name="listing-windows-installer-applications"></a><span data-ttu-id="44613-114">Windows Installer uygulamaları listeleme</span><span class="sxs-lookup"><span data-stu-id="44613-114">Listing Windows Installer Applications</span></span>

<span data-ttu-id="44613-115">Windows Installer bir yerel veya uzak sistemde yüklü uygulamalar listelemek için aşağıdaki basit WMI sorgusunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="44613-115">To list the applications installed with the Windows Installer on a local or remote system, use the following simple WMI query:</span></span>

```powershell
Get-CimInstance -Class Win32_Product |
  Where-Object Name -eq "Microsoft .NET Core Runtime - 2.1.2 (x64)"
```

```Output
Name               Caption                     Vendor                 Version      IdentifyingNumber
----               -------                     ------                 -------      -----------------
Microsoft .NET ... Microsoft .NET Core Runt... Microsoft Corporation  16.72.26629  {ACC73072-9AD5-416C-94B...
```

<span data-ttu-id="44613-116">Tüm özelliklerini görüntülemek için **Win32_Product** nesne görüntülenecek kullanım **özellikleri** biçimlendirme cmdlet'lerinin parametresine gibi `Format-List` cmdlet'iyle değerini `*` (Tümü).</span><span class="sxs-lookup"><span data-stu-id="44613-116">To display all the properties of the **Win32_Product** object to the display, use the **Properties** parameter of the formatting cmdlets, such as the `Format-List` cmdlet, with a value of `*` (all).</span></span>

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

<span data-ttu-id="44613-117">Ya da kullanabileceğinizi `Get-CimInstance` **filtre** parametresini kullanarak yalnızca Microsoft .NET Framework 2. 0'ı seçin.</span><span class="sxs-lookup"><span data-stu-id="44613-117">Or, you could use the `Get-CimInstance` **Filter** parameter to select only Microsoft .NET Framework 2.0.</span></span> <span data-ttu-id="44613-118">Değerini **filtre** parametresi olmayan Windows PowerShell sözdizimi WMI Sorgu Dili (WQL) söz dizimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="44613-118">The value of the **Filter** parameter uses WMI Query Language (WQL) syntax, not Windows PowerShell syntax.</span></span> <span data-ttu-id="44613-119">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="44613-119">For example:</span></span>

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='Microsoft .NET Core Runtime - 2.1.2 (x64)'" |
  Format-List -Property *
```

<span data-ttu-id="44613-120">İlginizi çeken özellikleri listelemek için kullanın **özelliği** istenen özellikleri listelemek için biçimlendirme cmdlet'lerin parametre.</span><span class="sxs-lookup"><span data-stu-id="44613-120">To list only the properties that interest you, use the **Property** parameter of the formatting cmdlets to list the desired properties.</span></span>

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

## <a name="listing-all-uninstallable-applications"></a><span data-ttu-id="44613-121">Tüm Uninstallable uygulamaları listeleme</span><span class="sxs-lookup"><span data-stu-id="44613-121">Listing All Uninstallable Applications</span></span>

<span data-ttu-id="44613-122">Çoğu standart uygulamaları Windows ile bir uninstaller kaydetmek için biz bunları Windows kayıt defterinde bulma tarafından yerel olarak çalışabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44613-122">Because most standard applications register an uninstaller with Windows, we can work with those locally by finding them in the Windows registry.</span></span> <span data-ttu-id="44613-123">Bir sistemde her uygulamayı bulmak için garantili bir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="44613-123">There is no guaranteed way to find every application on a system.</span></span> <span data-ttu-id="44613-124">Ancak, tüm programlar görüntülenen listelerini bulmak olası **Program Ekle veya Kaldır**.</span><span class="sxs-lookup"><span data-stu-id="44613-124">However, it is possible to find all programs with listings displayed in **Add or Remove Programs**.</span></span> <span data-ttu-id="44613-125">**Program Ekle veya Kaldır** bu uygulamalar aşağıdaki kayıt defteri anahtarında bulur:</span><span class="sxs-lookup"><span data-stu-id="44613-125">**Add or Remove Programs** finds these applications in the following registry key:</span></span>

<span data-ttu-id="44613-126">`HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Uninstall`.</span><span class="sxs-lookup"><span data-stu-id="44613-126">`HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Uninstall`.</span></span>

<span data-ttu-id="44613-127">Biz uygulamaları bulmak için bu anahtarı inceleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44613-127">We can examine this key to find applications.</span></span> <span data-ttu-id="44613-128">Kaldırma anahtarı görüntülemek daha kolay hale getirmek için şu PowerShell sürücüsünü bu kayıt defteri konumuna eşleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="44613-128">To make it easier to view the Uninstall key, we can map a PowerShell drive to this registry location:</span></span>

```powershell
New-PSDrive -Name Uninstall -PSProvider Registry -Root HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall
```

```Output
Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Uninstall  Registry      HKEY_LOCAL_MACHINE\SOFTWARE\Micr...
```
<span data-ttu-id="44613-129">Artık adlı bir sürücüsü sahibiz "Kaldır:" hızla ve kolayca uygulama yüklemeleri için aramak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="44613-129">We now have a drive named "Uninstall:" that can be used to quickly and conveniently look for application installations.</span></span> <span data-ttu-id="44613-130">Kayıt defteri anahtarlarını kaldırma sayısı sayılarak yüklü uygulamaların sayısını bulabiliriz: PowerShell sürücüsü:</span><span class="sxs-lookup"><span data-stu-id="44613-130">We can find the number of installed applications by counting the number of registry keys in the Uninstall: PowerShell drive:</span></span>

```
(Get-ChildItem -Path Uninstall:).Count
459
```

<span data-ttu-id="44613-131">Biz bu listeyi daha fazla uygulama çeşitli teknikler kullanarak başlayarak arayabilirsiniz **Get-Childıtem**.</span><span class="sxs-lookup"><span data-stu-id="44613-131">We can search this list of applications further by using a variety of techniques, beginning with **Get-ChildItem**.</span></span> <span data-ttu-id="44613-132">Uygulamaların bir listesini almak ve bunları kaydetmek için **$UninstallableApplications** değişken, aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="44613-132">To get a list of applications and save them in the **$UninstallableApplications** variable, use the following command:</span></span>

```powershell
$UninstallableApplications = Get-ChildItem -Path Uninstall:
```

<span data-ttu-id="44613-133">Kayıt defteri anahtarları kaldırma altında kayıt defteri girdilerinin değerlerini görüntülemek için kayıt defteri anahtarlarını GetValue yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="44613-133">To display the values of the registry entries in the registry keys under Uninstall, use the GetValue method of the registry keys.</span></span> <span data-ttu-id="44613-134">Yöntem değeri kayıt defteri girişini adıdır.</span><span class="sxs-lookup"><span data-stu-id="44613-134">The value of the method is the name of the registry entry.</span></span>

<span data-ttu-id="44613-135">Örneğin, Uninstall anahtarında uygulamaları görünen adlarını bulmak için aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="44613-135">For example, to find the display names of applications in the Uninstall key, use the following command:</span></span>

```powershell
$UninstallableApplications | ForEach-Object -Process { $_.GetValue('DisplayName') }
```

<span data-ttu-id="44613-136">Bu değerler benzersiz olmasını garanti yoktur.</span><span class="sxs-lookup"><span data-stu-id="44613-136">There is no guarantee that these values are unique.</span></span> <span data-ttu-id="44613-137">Aşağıdaki örnekte, "Windows Media Encoder 9 Serisi" yüklü iki öğe görünür:</span><span class="sxs-lookup"><span data-stu-id="44613-137">In the following example, two installed items appear as "Windows Media Encoder 9 Series":</span></span>

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

## <a name="installing-applications"></a><span data-ttu-id="44613-138">Uygulamaları yükleme</span><span class="sxs-lookup"><span data-stu-id="44613-138">Installing Applications</span></span>

<span data-ttu-id="44613-139">Kullanabileceğiniz **Win32_Product** Windows Installer paketleri uzaktan veya yerel olarak yüklemek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="44613-139">You can use the **Win32_Product** class to install Windows Installer packages, remotely or locally.</span></span>

> [!NOTE]
> <span data-ttu-id="44613-140">Bir uygulamayı yüklemek için PowerShell "Yönetici olarak çalıştır" seçeneğiyle başlatmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="44613-140">To install an application, you must start PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="44613-141">WMI alt PowerShell yolları anlamıyor çünkü .msi paketin yolu belirtmek için bir Evrensel Adlandırma Kuralı (UNC) ağ yolu uzaktan yüklerken kullanın.</span><span class="sxs-lookup"><span data-stu-id="44613-141">When installing remotely, use a Universal Naming Convention (UNC) network path to specify the path to the .msi package, because the WMI subsystem does not understand PowerShell paths.</span></span> <span data-ttu-id="44613-142">Örneğin, NewPackage.msi paketini yüklemek için bulunan ağ paylaşımına `\\AppServ\dsp` uzak bilgisayarda PC01 PowerShell komut isteminde aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="44613-142">For example, to install the NewPackage.msi package located in the network share `\\AppServ\dsp` on the remote computer PC01, type the following command at the PowerShell prompt:</span></span>

```powershell
Invoke-CimMethod -ClassName Win32_Product -MethodName Install -Arguments @{PackageLocation='\\AppSrv\dsp\NewPackage.msi'}
```

<span data-ttu-id="44613-143">Windows Yükleyici teknolojisi kullanmayan uygulamalar, otomatik dağıtım için uygulamaya özgü yöntemleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="44613-143">Applications that do not use Windows Installer technology may have application-specific methods for automated deployment.</span></span> <span data-ttu-id="44613-144">Uygulama için belgelere bakın veya uygulama satıcısının destek sistemi başvurun.</span><span class="sxs-lookup"><span data-stu-id="44613-144">Check the documentation for the application or consult the application vendor's support system.</span></span>

## <a name="removing-applications"></a><span data-ttu-id="44613-145">Uygulamaları kaldırma</span><span class="sxs-lookup"><span data-stu-id="44613-145">Removing Applications</span></span>

<span data-ttu-id="44613-146">PowerShell kullanarak bir Windows Installer paketi kaldırma paket yükleme yaklaşık aynı şekilde çalışır.</span><span class="sxs-lookup"><span data-stu-id="44613-146">Removing a Windows Installer package using PowerShell works in approximately the same way as installing a package.</span></span> <span data-ttu-id="44613-147">Kaldırmak için paket adına göre seçen bir örneği aşağıda verilmiştir; Bazı durumlarda ile filtrelemek daha kolay olabilir **Identifyingnumber**:</span><span class="sxs-lookup"><span data-stu-id="44613-147">Here is an example that selects the package to uninstall based on its name; in some cases it may be easier to filter with the **IdentifyingNumber**:</span></span>

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='ILMerge'" | Invoke-CimMethod -MethodName Uninstall
```

<span data-ttu-id="44613-148">Diğer uygulamaları kaldırma bile yerel olarak işiniz bittiğinde konu bu kadar basit değil.</span><span class="sxs-lookup"><span data-stu-id="44613-148">Removing other applications is not quite so simple, even when done locally.</span></span> <span data-ttu-id="44613-149">Komut satırı kaldırma dizeleri için bu uygulamaları ayıklayarak bulabiliriz **UninstallString** özelliği.</span><span class="sxs-lookup"><span data-stu-id="44613-149">We can find the command line uninstallation strings for these applications by extracting the **UninstallString** property.</span></span>
<span data-ttu-id="44613-150">Bu yöntem, kaldırma anahtarı altında görünen eski programları ve Windows Installer uygulamaları için çalışır:</span><span class="sxs-lookup"><span data-stu-id="44613-150">This method works for Windows Installer applications and for older programs appearing under the Uninstall key:</span></span>

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

<span data-ttu-id="44613-151">İsterseniz, görünen ada göre çıkışı filtreleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="44613-151">You can filter the output by the display name, if you like:</span></span>

```powershell
Get-ChildItem -Path Uninstall: |
    Where-Object -FilterScript { $_.GetValue('DisplayName') -like 'Win*'} |
        ForEach-Object -Process { $_.GetValue('UninstallString') }
```

<span data-ttu-id="44613-152">Ancak, bu dizeler PowerShell isteminden bazı değişiklik yapmadan doğrudan kullanılabilir olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="44613-152">However, these strings may not be directly usable from the PowerShell prompt without some modification.</span></span>

## <a name="upgrading-windows-installer-applications"></a><span data-ttu-id="44613-153">Windows Installer uygulamalarını yükseltme</span><span class="sxs-lookup"><span data-stu-id="44613-153">Upgrading Windows Installer Applications</span></span>

<span data-ttu-id="44613-154">Bir uygulamayı yükseltmek için uygulama yükseltme paketini uygulama ve yolun adını bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="44613-154">To upgrade an application, you need to know the name of the application and the path to the application upgrade package.</span></span> <span data-ttu-id="44613-155">Bu bilgileri kullanarak tek bir PowerShell komutu ile bir uygulama yükseltebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="44613-155">With that information, you can upgrade an application with a single PowerShell command:</span></span>

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='OldAppName'" |
  Invoke-CimMethod -MethodName Upgrade -Arguments @{PackageLocation='\\AppSrv\dsp\OldAppUpgrade.msi'}
```
