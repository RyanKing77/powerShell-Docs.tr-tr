---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Yazılım Yüklemeleri ile Çalışma
ms.assetid: 51a12fe9-95f6-4ffc-81a5-4fa72a5bada9
ms.openlocfilehash: 9369e3c5ac670895cd4fbd3ebc895c50efd02051
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293240"
---
# <a name="working-with-software-installations"></a><span data-ttu-id="0f1a7-103">Yazılım Yüklemeleri ile Çalışma</span><span class="sxs-lookup"><span data-stu-id="0f1a7-103">Working with Software Installations</span></span>

<span data-ttu-id="0f1a7-104">Windows Installer'ı kullanmak üzere tasarlanmış uygulamalar WMI'nin erişilebilir **Win32_Product** sınıfı, ancak kullanımda tüm uygulamalar Windows Yükleyici kullanmaya hemen başlayın.</span><span class="sxs-lookup"><span data-stu-id="0f1a7-104">Applications that are designed to use Windows Installer can be accessed through WMI's **Win32_Product** class, but not all applications in use today use the Windows Installer.</span></span> <span data-ttu-id="0f1a7-105">Windows Installer yüklenebilir uygulamalarla çalışmak için standart teknikleri yelpazedeki sağladığından, biz öncelikle bu uygulamalar üzerinde odaklanır.</span><span class="sxs-lookup"><span data-stu-id="0f1a7-105">Because the Windows Installer provides the widest range of standard techniques for working with installable applications, we will focus primarily on those applications.</span></span> <span data-ttu-id="0f1a7-106">Alternatif kurulum yordamları kullanan uygulamalar genellikle Windows Installer tarafından yönetilmez.</span><span class="sxs-lookup"><span data-stu-id="0f1a7-106">Applications that use alternate setup routines will generally not be managed by the Windows Installer.</span></span> <span data-ttu-id="0f1a7-107">Bu uygulamalarla çalışmak için belirli teknik kararları uygulama geliştiricisi tarafından yapılan ve yükleyici yazılım bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="0f1a7-107">Specific techniques for working with those applications will depend on the installer software and decisions made by the application developer.</span></span>

> [!NOTE]
> <span data-ttu-id="0f1a7-108">Uygulama dosyaları genellikle bilgisayara kopyalayarak yüklü uygulamaları burada ele alınan teknikleri kullanarak tarafından yönetilemez.</span><span class="sxs-lookup"><span data-stu-id="0f1a7-108">Applications that are installed by copying the application files to the computer usually cannot be managed by using techniques discussed here.</span></span> <span data-ttu-id="0f1a7-109">Bu uygulamalar olarak dosyalar ve klasörler "Çalışma ile dosyalar ve klasörler" bölümünde ele alınan teknikleri kullanarak yönetebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0f1a7-109">You can manage these applications as files and folders by using the techniques discussed in the "Working With Files and Folders" section.</span></span>

## <a name="listing-windows-installer-applications"></a><span data-ttu-id="0f1a7-110">Windows Installer uygulamaları listeleme</span><span class="sxs-lookup"><span data-stu-id="0f1a7-110">Listing Windows Installer Applications</span></span>

<span data-ttu-id="0f1a7-111">Windows Installer bir yerel veya uzak sistemde yüklü uygulamalar listelemek için aşağıdaki basit WMI sorgusunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="0f1a7-111">To list the applications installed with the Windows Installer on a local or remote system, use the following simple WMI query:</span></span>

```
PS> Get-WmiObject -Class Win32_Product -ComputerName .

IdentifyingNumber : {7131646D-CD3C-40F4-97B9-CD9E4E6262EF}
Name              : Microsoft .NET Framework 2.0
Vendor            : Microsoft Corporation
Version           : 2.0.50727
Caption           : Microsoft .NET Framework 2.0
```

<span data-ttu-id="0f1a7-112">Görüntülenecek Win32_Product nesne özelliklerini görüntülemek için değeri olan Format-List cmdlet'i gibi biçimlendirme cmdlet'lerinin özellikleri parametresini kullanın \* (Tümü).</span><span class="sxs-lookup"><span data-stu-id="0f1a7-112">To display all of the properties of the Win32_Product object to the display, use the Properties parameter of the formatting cmdlets, such as the Format-List cmdlet, with a value of \* (all).</span></span>

```
PS> Get-WmiObject -Class Win32_Product -ComputerName . | Where-Object -FilterScript {$_.Name -eq "Microsoft .NET Framework 2.0"} | Format-List -Property *

Name              : Microsoft .NET Framework 2.0
Version           : 2.0.50727
InstallState      : 5
Caption           : Microsoft .NET Framework 2.0
Description       : Microsoft .NET Framework 2.0
IdentifyingNumber : {7131646D-CD3C-40F4-97B9-CD9E4E6262EF}
InstallDate       : 20060506
InstallDate2      : 20060506000000.000000-000
InstallLocation   :
PackageCache      : C:\WINDOWS\Installer\619ab2.msi
SKUNumber         :
Vendor            : Microsoft Corporation
```

<span data-ttu-id="0f1a7-113">Ya da kullanabileceğinizi **Get-WmiObject filtre** parametresini kullanarak yalnızca Microsoft .NET Framework 2. 0'ı seçin.</span><span class="sxs-lookup"><span data-stu-id="0f1a7-113">Or, you could use the **Get-WmiObject Filter** parameter to select only Microsoft .NET Framework 2.0.</span></span> <span data-ttu-id="0f1a7-114">Bu komutta kullanılan filtrede bir WMI filtresi olduğundan, Windows PowerShell sözdizimi değil WMI Sorgu Dili (WQL) söz dizimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="0f1a7-114">Because the filter used in this command is a WMI filter, it uses WMI Query Language (WQL) syntax, not Windows PowerShell syntax.</span></span> <span data-ttu-id="0f1a7-115">Bunun yerine:</span><span class="sxs-lookup"><span data-stu-id="0f1a7-115">Instead,:</span></span>

```powershell
Get-WmiObject -Class Win32_Product -ComputerName . -Filter "Name='Microsoft .NET Framework 2.0'"| Format-List -Property *
```

<span data-ttu-id="0f1a7-116">WQL boşluk ya da Windows PowerShell içinde özel bir anlamı olan eşittir işareti gibi kullanım karakterleri sık sorgular unutmayın.</span><span class="sxs-lookup"><span data-stu-id="0f1a7-116">Note that WQL queries frequently use characters, such as spaces or equal signs, that have a special meaning in Windows PowerShell.</span></span> <span data-ttu-id="0f1a7-117">Bu nedenle, her zaman filtresi parametresinin değerini tırnak içine alın akıllıca olur.</span><span class="sxs-lookup"><span data-stu-id="0f1a7-117">For this reason, it is prudent to always enclose the value of the Filter parameter in quotation marks.</span></span> <span data-ttu-id="0f1a7-118">Windows PowerShell kaçış karakteri olan bir vurgulamasını belirtir de kullanabilirsiniz (\`), ancak bunu okunabilirliği artırmak değildir.</span><span class="sxs-lookup"><span data-stu-id="0f1a7-118">You can also use the Windows PowerShell escape character, a backtick (\`), although it may not improve readability.</span></span> <span data-ttu-id="0f1a7-119">Aşağıdaki komut önceki komutu eşdeğerdir ve aynı sonuçları döndürür, ancak tüm filtre dize Alıntısı yerine özel karakterler, kaçış için vurgulamasını belirtir kullanır.</span><span class="sxs-lookup"><span data-stu-id="0f1a7-119">The following command is equivalent to the previous command and returns the same results, but uses the backtick to escape special characters, instead of quoting the entire filter string.</span></span>

```powershell
Get-WmiObject -Class Win32_Product -ComputerName . -Filter Name`=`'Microsoft` .NET` Framework` 2.0`' | Format-List -Property *
```

<span data-ttu-id="0f1a7-120">İlginizi çeken özelliklerini listelemek için istenen özellikleri listelemek için özellik parametresi biçimlendirme cmdlet'leri kullanın.</span><span class="sxs-lookup"><span data-stu-id="0f1a7-120">To list only the properties that interest you, use the Property parameter of the formatting cmdlets to list the desired properties.</span></span>

```
Get-WmiObject -Class Win32_Product -ComputerName . | Format-List -Property Name,InstallDate,InstallLocation,PackageCache,Vendor,Version,IdentifyingNumber
...
Name              : HighMAT Extension to Microsoft Windows XP CD Writing Wizard
InstallDate       : 20051022
InstallLocation   : C:\Program Files\HighMAT CD Writing Wizard\
PackageCache      : C:\WINDOWS\Installer\113b54.msi
Vendor            : Microsoft Corporation
Version           : 1.1.1905.1
IdentifyingNumber : {FCE65C4E-B0E8-4FBD-AD16-EDCBE6CD591F}
...
```

<span data-ttu-id="0f1a7-121">Son olarak, yalnızca adlarını bulmak için uygulamalar, basit bir yüklü **biçimi genelinde** deyimi çıkış kolaylaştırır:</span><span class="sxs-lookup"><span data-stu-id="0f1a7-121">Finally, to find only the names of installed applications, a simple **Format-Wide** statement simplifies the output:</span></span>

```powershell
Get-WmiObject -Class Win32_Product -ComputerName .  | Format-Wide -Column 1
```

<span data-ttu-id="0f1a7-122">Şimdi Windows Installer yükleme için kullanılan uygulamaların bakmak için çeşitli yollar vardır ancak diğer uygulamaları dikkate değil.</span><span class="sxs-lookup"><span data-stu-id="0f1a7-122">Although we now have several ways to look at applications that used the Windows Installer for installation, we have not considered other applications.</span></span> <span data-ttu-id="0f1a7-123">Çoğu standart uygulamaları Windows ile kendi uninstaller kaydetmek için biz bunları Windows kayıt defterinde bulma tarafından yerel olarak çalışabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0f1a7-123">Because most standard applications register their uninstaller with Windows, we can work with those locally by finding them in the Windows registry.</span></span>

## <a name="listing-all-uninstallable-applications"></a><span data-ttu-id="0f1a7-124">Tüm Uninstallable uygulamaları listeleme</span><span class="sxs-lookup"><span data-stu-id="0f1a7-124">Listing All Uninstallable Applications</span></span>

<span data-ttu-id="0f1a7-125">Bir sistemde her uygulamayı bulmak için garantili yolu olsa da, Program Ekle veya Kaldır iletişim kutusunda görüntülenen listeleri içeren tüm programları bulmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="0f1a7-125">Although there is no guaranteed way to find every application on a system, it is possible to find all programs with listings displayed in the Add or Remove Programs dialog box.</span></span> <span data-ttu-id="0f1a7-126">Ekle veya Kaldır bu uygulamalar aşağıdaki kayıt defteri anahtarında bulur:</span><span class="sxs-lookup"><span data-stu-id="0f1a7-126">Add or Remove Programs finds these applications in the following registry key:</span></span>

<span data-ttu-id="0f1a7-127">**HKEY_LOCAL_MACHINE\\yazılım\\Microsoft\\Windows\\CurrentVersion\\kaldırma**.</span><span class="sxs-lookup"><span data-stu-id="0f1a7-127">**HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\Uninstall**.</span></span>

<span data-ttu-id="0f1a7-128">Biz de uygulamaları bulmak için bu anahtarı inceleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0f1a7-128">We can also examine this key to find applications.</span></span> <span data-ttu-id="0f1a7-129">Kaldırma anahtarı görüntülemek kolaylaştırmak için şu Windows PowerShell sürücüsünü bu kayıt defteri konumuna eşleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0f1a7-129">To make it easier to view the Uninstall key, we can map a Windows PowerShell drive to this registry location:</span></span>

```
PS> New-PSDrive -Name Uninstall -PSProvider Registry -Root HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Uninstall  Registry      HKEY_LOCAL_MACHINE\SOFTWARE\Micr...
```

> [!NOTE]
> <span data-ttu-id="0f1a7-130">**HKLM:** sürücünün köküne eşlenen **HKEY_LOCAL_MACHINE**, bu sürücüyü kaldırma anahtar yolunu kullandık.</span><span class="sxs-lookup"><span data-stu-id="0f1a7-130">The **HKLM:** drive is mapped to the root of **HKEY_LOCAL_MACHINE**, so we used that drive in the path to the Uninstall key.</span></span> <span data-ttu-id="0f1a7-131">Yerine **HKLM:** şu kayıt defteri yolunu kullanarak belirtmiş olabilirsiniz **HKLM** veya **HKEY_LOCAL_MACHINE**.</span><span class="sxs-lookup"><span data-stu-id="0f1a7-131">Instead of **HKLM:** we could have specified the registry path by using either **HKLM** or **HKEY_LOCAL_MACHINE**.</span></span> <span data-ttu-id="0f1a7-132">Var olan kayıt defteri sürücüsüne kullanmanın avantajı biz sekme tamamlama biz bunları türüne gerek yoktur, anahtarları adlarında doldurmak için kullanabilmenizdedir.</span><span class="sxs-lookup"><span data-stu-id="0f1a7-132">The advantage of using an existing registry drive is that we can use tab-completion to fill in the keys names, so we do not need to type them.</span></span>

<span data-ttu-id="0f1a7-133">Artık uygulama yüklemeleri için hızla ve kolayca aramak için kullanılan "Kaldır" adlı bir sürücüsü sahibiz.</span><span class="sxs-lookup"><span data-stu-id="0f1a7-133">We now have a drive named "Uninstall" that can be used to quickly and conveniently look for application installations.</span></span> <span data-ttu-id="0f1a7-134">Kayıt defteri anahtarlarını kaldırma sayısı sayılarak yüklü uygulamaların sayısını bulabiliriz: Windows PowerShell sürücüsü:</span><span class="sxs-lookup"><span data-stu-id="0f1a7-134">We can find the number of installed applications by counting the number of registry keys in the Uninstall: Windows PowerShell drive:</span></span>

```
PS> (Get-ChildItem -Path Uninstall:).Count
459
```

<span data-ttu-id="0f1a7-135">Biz bu listeyi daha fazla uygulama çeşitli teknikler kullanarak başlayarak arayabilirsiniz **Get-Childıtem**.</span><span class="sxs-lookup"><span data-stu-id="0f1a7-135">We can search this list of applications further by using a variety of techniques, beginning with **Get-ChildItem**.</span></span> <span data-ttu-id="0f1a7-136">Uygulamaların bir listesini almak ve bunları kaydetmek için **$UninstallableApplications** değişken, aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="0f1a7-136">To get a list of applications and save them in the **$UninstallableApplications** variable, use the following command:</span></span>

```powershell
$UninstallableApplications = Get-ChildItem -Path Uninstall:
```

> [!NOTE]
> <span data-ttu-id="0f1a7-137">Uzun Buraya bir değişken adı anlaşılması için kullanıyoruz.</span><span class="sxs-lookup"><span data-stu-id="0f1a7-137">We are using a lengthy variable name here for clarity.</span></span> <span data-ttu-id="0f1a7-138">Gerçek kullanımda uzun adlarını kullanmak için bir neden yoktur.</span><span class="sxs-lookup"><span data-stu-id="0f1a7-138">In actual use, there is no reason to use long names.</span></span> <span data-ttu-id="0f1a7-139">Değişken adları için sekme tamamlama kullanabilirsiniz, ancak 1-2 karakter adları hızı için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0f1a7-139">Although you can use tab-completion for variable names, you can also use 1-2 character names for speed.</span></span> <span data-ttu-id="0f1a7-140">Kod yeniden kullanımı için geliştirirken, uzun, açıklayıcı adlar ekseriyetle faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="0f1a7-140">Longer, descriptive names are most useful when you are developing code for reuse.</span></span>

<span data-ttu-id="0f1a7-141">Kayıt defteri anahtarları kaldırma altında kayıt defteri girdilerinin değerlerini görüntülemek için kayıt defteri anahtarlarını GetValue yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="0f1a7-141">To display the values of the registry entries in the registry keys under Uninstall, use the GetValue method of the registry keys.</span></span> <span data-ttu-id="0f1a7-142">Yöntem değeri kayıt defteri girişini adıdır.</span><span class="sxs-lookup"><span data-stu-id="0f1a7-142">The value of the method is the name of the registry entry.</span></span>

<span data-ttu-id="0f1a7-143">Örneğin, Uninstall anahtarında uygulamaları görünen adlarını bulmak için aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="0f1a7-143">For example, to find the display names of applications in the Uninstall key, use the following command:</span></span>

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('DisplayName') }
```

<span data-ttu-id="0f1a7-144">Bu değerler benzersiz olmasını garanti yoktur.</span><span class="sxs-lookup"><span data-stu-id="0f1a7-144">There is no guarantee that these values are unique.</span></span> <span data-ttu-id="0f1a7-145">Aşağıdaki örnekte, "Windows Media Encoder 9 Serisi" yüklü iki öğe görünür:</span><span class="sxs-lookup"><span data-stu-id="0f1a7-145">In the following example, two installed items appear as "Windows Media Encoder 9 Series":</span></span>

```
PS> Get-ChildItem -Path Uninstall: | Where-Object -FilterScript { $_.GetValue("DisplayName") -eq "Windows Media Encoder 9 Series"}

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Micros
oft\Windows\CurrentVersion\Uninstall

SKC  VC Name                           Property
---  -- ----                           --------
  0   3 Windows Media Encoder 9        {DisplayName, DisplayIcon, UninstallS...
  0  24 {E38C00D0-A68B-4318-A8A6-F7... {AuthorizedCDFPrefix, Comments, Conta...
```

## <a name="installing-applications"></a><span data-ttu-id="0f1a7-146">Uygulamaları yükleme</span><span class="sxs-lookup"><span data-stu-id="0f1a7-146">Installing Applications</span></span>

<span data-ttu-id="0f1a7-147">Kullanabileceğiniz **Win32_Product** Windows Installer paketleri uzaktan veya yerel olarak yüklemek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="0f1a7-147">You can use the **Win32_Product** class to install Windows Installer packages, remotely or locally.</span></span>

> [!NOTE]
> <span data-ttu-id="0f1a7-148">Bir uygulamayı yüklemek için Windows Vista, Windows Server 2008 ve sonraki Windows sürümlerinde, Windows PowerShell "Yönetici olarak çalıştır" seçeneğiyle başlatmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0f1a7-148">On Windows Vista, Windows Server 2008, and later versions of Windows, to install an application, you must start Windows PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="0f1a7-149">WMI alt sistemi, Windows PowerShell yolları anlamıyor çünkü .msi paketin yolu belirtmek için bir Evrensel Adlandırma Kuralı (UNC) ağ yolu uzaktan yüklerken kullanın.</span><span class="sxs-lookup"><span data-stu-id="0f1a7-149">When installing remotely, use a Universal Naming Convention (UNC) network path to specify the path to the .msi package, because the WMI subsystem does not understand Windows PowerShell paths.</span></span> <span data-ttu-id="0f1a7-150">Örneğin, NewPackage.msi paketini yüklemek için bulunan ağ paylaşımına \\ \\AppServ\\dsp PC01, uzak bilgisayarda Windows PowerShell komut isteminde aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="0f1a7-150">For example, to install the NewPackage.msi package located in the network share \\\\AppServ\\dsp on the remote computer PC01, type the following command at the Windows PowerShell prompt:</span></span>

```powershell
(Get-WMIObject -ComputerName PC01 -List | Where-Object -FilterScript {$_.Name -eq 'Win32_Product'}).Install(\\AppSrv\dsp\NewPackage.msi)
```

<span data-ttu-id="0f1a7-151">Windows Yükleyici teknolojisi kullanmayan uygulamalar, otomatik dağıtım için uygulamaya özgü yöntemleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="0f1a7-151">Applications that do not use Windows Installer technology may have application-specific methods available for automated deployment.</span></span> <span data-ttu-id="0f1a7-152">Bir dağıtım otomasyonunu yöntemi olup olmadığını belirlemek için uygulama için belgelere bakın veya uygulama satıcısının destek sistemi başvurun.</span><span class="sxs-lookup"><span data-stu-id="0f1a7-152">To determine whether there is a method for deployment automation, check the documentation for the application or consult the application vendor's support system.</span></span> <span data-ttu-id="0f1a7-153">Bazı durumlarda bile uygulamanın satıcısına özellikle uygulama için yükleme Otomasyon tasarlamak değil yükleyici yazılımın Otomasyon için bazı teknikleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="0f1a7-153">In some cases, even if the application vendor did not specifically design the application for installation automation, the installer software manufacturer may have some techniques for automation.</span></span>

## <a name="removing-applications"></a><span data-ttu-id="0f1a7-154">Uygulamaları kaldırma</span><span class="sxs-lookup"><span data-stu-id="0f1a7-154">Removing Applications</span></span>

<span data-ttu-id="0f1a7-155">Windows PowerShell kullanarak bir Windows Installer paketi kaldırma paket yükleme yaklaşık aynı şekilde çalışır.</span><span class="sxs-lookup"><span data-stu-id="0f1a7-155">Removing a Windows Installer package by using Windows PowerShell works in approximately the same way as installing a package.</span></span> <span data-ttu-id="0f1a7-156">Kaldırmak için paket adına göre seçen bir örneği aşağıda verilmiştir; Bazı durumlarda ile filtrelemek daha kolay olabilir **Identifyingnumber**:</span><span class="sxs-lookup"><span data-stu-id="0f1a7-156">Here is an example that selects the package to uninstall based on its name; in some cases it may be easier to filter with the **IdentifyingNumber**:</span></span>

```powershell
(Get-WmiObject -Class Win32_Product -Filter "Name='ILMerge'" -ComputerName . ).Uninstall()
```

<span data-ttu-id="0f1a7-157">Diğer uygulamaları kaldırma bile yerel olarak işiniz bittiğinde konu bu kadar basit değil.</span><span class="sxs-lookup"><span data-stu-id="0f1a7-157">Removing other applications is not quite so simple, even when done locally.</span></span> <span data-ttu-id="0f1a7-158">Komut satırı kaldırma dizeleri için bu uygulamaları ayıklayarak bulabiliriz **UninstallString** özelliği.</span><span class="sxs-lookup"><span data-stu-id="0f1a7-158">We can find the command line uninstallation strings for these applications by extracting the **UninstallString** property.</span></span> <span data-ttu-id="0f1a7-159">Bu yöntem, kaldırma anahtarı altında görünen eski programları ve Windows Installer uygulamaları için çalışır:</span><span class="sxs-lookup"><span data-stu-id="0f1a7-159">This method works for Windows Installer applications and for older programs appearing under the Uninstall key:</span></span>

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

<span data-ttu-id="0f1a7-160">İsterseniz, görünen ada göre çıkışı filtreleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0f1a7-160">You can filter the output by the display name, if you like:</span></span>

```powershell
Get-ChildItem -Path Uninstall: | Where-Object -FilterScript { $_.GetValue('DisplayName') -like 'Win*'} | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

<span data-ttu-id="0f1a7-161">Ancak, bu dizeler Windows PowerShell isteminden bazı değişiklik yapmadan doğrudan kullanılabilir olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="0f1a7-161">However, these strings may not be directly usable from the Windows PowerShell prompt without some modification.</span></span>

## <a name="upgrading-windows-installer-applications"></a><span data-ttu-id="0f1a7-162">Windows Installer uygulamalarını yükseltme</span><span class="sxs-lookup"><span data-stu-id="0f1a7-162">Upgrading Windows Installer Applications</span></span>

<span data-ttu-id="0f1a7-163">Bir uygulamayı yükseltmek için uygulama yükseltme paketini uygulama ve yolun adını bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="0f1a7-163">To upgrade an application, you need to know the name of the application and the path to the application upgrade package.</span></span> <span data-ttu-id="0f1a7-164">Bu bilgileri kullanarak bir Windows PowerShell komutu ile bir uygulama yükseltebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0f1a7-164">With that information, you can upgrade an application with a single Windows PowerShell command:</span></span>

```powershell
(Get-WmiObject -Class Win32_Product -ComputerName . -Filter "Name='OldAppName'").Upgrade(\\AppSrv\dsp\OldAppUpgrade.msi)
```