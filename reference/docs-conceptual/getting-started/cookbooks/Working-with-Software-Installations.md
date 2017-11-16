---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: "Yazılım yüklemeleri ile çalışma"
ms.assetid: 51a12fe9-95f6-4ffc-81a5-4fa72a5bada9
ms.openlocfilehash: 2078376a8be19c9ff8ecc44183eb89f14bc388ed
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2017
---
# <a name="working-with-software-installations"></a><span data-ttu-id="567ee-103">Yazılım yüklemeleri ile çalışma</span><span class="sxs-lookup"><span data-stu-id="567ee-103">Working with Software Installations</span></span>
<span data-ttu-id="567ee-104">Windows Installer kullanmak üzere tasarlanmış uygulamaları WMI aracılığıyla kişinin erişilebilir **Win32_Product** sınıfı, ancak kullanımda tüm uygulamalar bugün Windows Installer kullanın.</span><span class="sxs-lookup"><span data-stu-id="567ee-104">Applications that are designed to use Windows Installer can be accessed through WMI's **Win32_Product** class, but not all applications in use today use the Windows Installer.</span></span> <span data-ttu-id="567ee-105">Windows Installer yüklenebilir uygulamaları ile çalışmak için standart teknikleri yelpazedeki sağladığından, bu uygulamaları öncelikle bulunacağınız konularına odaklanır.</span><span class="sxs-lookup"><span data-stu-id="567ee-105">Because the Windows Installer provides the widest range of standard techniques for working with installable applications, we will focus primarily on those applications.</span></span> <span data-ttu-id="567ee-106">Alternatif kurulum yordamları kullanan uygulamalar genellikle Windows Installer tarafından yönetilmez.</span><span class="sxs-lookup"><span data-stu-id="567ee-106">Applications that use alternate setup routines will generally not be managed by the Windows Installer.</span></span> <span data-ttu-id="567ee-107">Bu uygulamalarla çalışmak için belirli teknikler yükleyici yazılım ve uygulama geliştiricisi tarafından kararlara bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="567ee-107">Specific techniques for working with those applications will depend on the installer software and decisions made by the application developer.</span></span>

> [!NOTE]
> <span data-ttu-id="567ee-108">Uygulama dosyaları genellikle bilgisayara kopyalayarak yüklenen uygulamalar, burada açıklanan teknikleri kullanarak tarafından yönetilemez.</span><span class="sxs-lookup"><span data-stu-id="567ee-108">Applications that are installed by copying the application files to the computer usually cannot be managed by using techniques discussed here.</span></span> <span data-ttu-id="567ee-109">"Çalışma ile dosyalar ve klasörler" bölümünde açıklanan teknikleri kullanarak bu uygulamaları dosya ve klasörleri olarak yönetebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="567ee-109">You can manage these applications as files and folders by using the techniques discussed in the "Working With Files and Folders" section.</span></span>

### <a name="listing-windows-installer-applications"></a><span data-ttu-id="567ee-110">Windows Installer uygulamaları listeleme</span><span class="sxs-lookup"><span data-stu-id="567ee-110">Listing Windows Installer Applications</span></span>
<span data-ttu-id="567ee-111">Windows Installer bir yerel veya uzak sistemde yüklü olan uygulamaları listelemek için aşağıdaki basit WMI sorgusu kullanın:</span><span class="sxs-lookup"><span data-stu-id="567ee-111">To list the applications installed with the Windows Installer on a local or remote system, use the following simple WMI query:</span></span>

```
PS> Get-WmiObject -Class Win32_Product -ComputerName .
IdentifyingNumber : {7131646D-CD3C-40F4-97B9-CD9E4E6262EF}
Name              : Microsoft .NET Framework 2.0
Vendor            : Microsoft Corporation
Version           : 2.0.50727
Caption           : Microsoft .NET Framework 2.0
```

<span data-ttu-id="567ee-112">Görüntülenecek Win32_Product nesnenin özelliklerini görüntülemek için değeri olan Format-List cmdlet gibi biçimlendirme cmdlet'leri özellikleri parametresini kullanın \* (Tümü).</span><span class="sxs-lookup"><span data-stu-id="567ee-112">To display all of the properties of the Win32_Product object to the display, use the Properties parameter of the formatting cmdlets, such as the Format-List cmdlet, with a value of \* (all).</span></span>

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

<span data-ttu-id="567ee-113">Ya da kullanabileceğinizi **Get-WmiObject filtre** parametresini kullanarak yalnızca Microsoft .NET Framework 2. 0'ı seçin.</span><span class="sxs-lookup"><span data-stu-id="567ee-113">Or, you could use the **Get-WmiObject Filter** parameter to select only Microsoft .NET Framework 2.0.</span></span> <span data-ttu-id="567ee-114">Bu komutta kullanılan filtresini bir WMI filtresi olduğundan, WMI Sorgu Dili (WQL) sözdizimi, Windows PowerShell sözdizimi kullanır.</span><span class="sxs-lookup"><span data-stu-id="567ee-114">Because the filter used in this command is a WMI filter, it uses WMI Query Language (WQL) syntax, not Windows PowerShell syntax.</span></span> <span data-ttu-id="567ee-115">Bunun yerine:</span><span class="sxs-lookup"><span data-stu-id="567ee-115">Instead,:</span></span>

```
Get-WmiObject -Class Win32_Product -ComputerName . -Filter "Name='Microsoft .NET Framework 2.0'"| Format-List -Property *
```

<span data-ttu-id="567ee-116">WQL boşluk ya da Windows PowerShell içinde özel bir anlamı olan eşittir işareti gibi kullanılabilecek karakterleri sık sorgular unutmayın.</span><span class="sxs-lookup"><span data-stu-id="567ee-116">Note that WQL queries frequently use characters, such as spaces or equal signs, that have a special meaning in Windows PowerShell.</span></span> <span data-ttu-id="567ee-117">Bu nedenle, her zaman filtresi parametresinin değeri tırnak işaretleri içine alın akıllıca olur.</span><span class="sxs-lookup"><span data-stu-id="567ee-117">For this reason, it is prudent to always enclose the value of the Filter parameter in quotation marks.</span></span> <span data-ttu-id="567ee-118">Windows PowerShell kaçış karakteri bir backtick de kullanabilirsiniz (\\`), ancak bunu okunabilirliğini artırmak değil.</span><span class="sxs-lookup"><span data-stu-id="567ee-118">You can also use the Windows PowerShell escape character, a backtick (\\`), although it may not improve readability.</span></span> <span data-ttu-id="567ee-119">Aşağıdaki komutu önceki komutu ile eşdeğerdir ve aynı sonuçları verir, ancak tüm filtre dizesi tırnak içine almak yerine özel karakterler kaçınmak için backtick kullanır.</span><span class="sxs-lookup"><span data-stu-id="567ee-119">The following command is equivalent to the previous command and returns the same results, but uses the backtick to escape special characters, instead of quoting the entire filter string.</span></span>

```
Get-WmiObject -Class Win32_Product -ComputerName . -Filter Name`=`'Microsoft` .NET` Framework` 2.0`' | Format-List -Property *
```

<span data-ttu-id="567ee-120">Sizi ilgilendiren özellikleri listelemek için istenen özellikleri listelemek için biçimlendirme cmdlet'leri özelliği parametresini kullanın.</span><span class="sxs-lookup"><span data-stu-id="567ee-120">To list only the properties that interest you, use the Property parameter of the formatting cmdlets to list the desired properties.</span></span>

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

<span data-ttu-id="567ee-121">Son olarak, yalnızca adlarını bulmak için basit bir yüklü uygulamaların **biçimi genelinde** deyimi basitleştirir çıktı:</span><span class="sxs-lookup"><span data-stu-id="567ee-121">Finally, to find only the names of installed applications, a simple **Format-Wide** statement simplifies the output:</span></span>

```
Get-WmiObject -Class Win32_Product -ComputerName .  | Format-Wide -Column 1
```

<span data-ttu-id="567ee-122">Artık Windows Installer yükleme için kullanılan uygulamalar bakmak için çeşitli yollar sahibiz rağmen biz diğer uygulamaları kabul değil.</span><span class="sxs-lookup"><span data-stu-id="567ee-122">Although we now have several ways to look at applications that used the Windows Installer for installation, we have not considered other applications.</span></span> <span data-ttu-id="567ee-123">Çoğu standart uygulamaları Windows ile bunların kaldırıcı kaydetmek için Biz bu yerel Windows Kayıt Defteri'nde bulma tarafından ile çalışabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="567ee-123">Because most standard applications register their uninstaller with Windows, we can work with those locally by finding them in the Windows registry.</span></span>

### <a name="listing-all-uninstallable-applications"></a><span data-ttu-id="567ee-124">Tüm Uninstallable uygulamaları listeleme</span><span class="sxs-lookup"><span data-stu-id="567ee-124">Listing All Uninstallable Applications</span></span>
<span data-ttu-id="567ee-125">Bir sistem üzerinde her uygulamayı bulmak için hiçbir garanti edilen şekilde olsa da, tüm programlar Program Ekle veya Kaldır iletişim kutusunda görüntülenen listelerini bulmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="567ee-125">Although there is no guaranteed way to find every application on a system, it is possible to find all programs with listings displayed in the Add or Remove Programs dialog box.</span></span> <span data-ttu-id="567ee-126">Ekle veya Kaldır'ı bu uygulamalar aşağıdaki kayıt defteri anahtarında bulur:</span><span class="sxs-lookup"><span data-stu-id="567ee-126">Add or Remove Programs finds these applications in the following registry key:</span></span>

<span data-ttu-id="567ee-127">**HKEY_LOCAL_MACHINE\\yazılım\\Microsoft\\Windows\\CurrentVersion\\kaldırma**.</span><span class="sxs-lookup"><span data-stu-id="567ee-127">**HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\Uninstall**.</span></span>

<span data-ttu-id="567ee-128">Ayrıca, biz uygulamaları bulmak için bu anahtarı inceleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="567ee-128">We can also examine this key to find applications.</span></span> <span data-ttu-id="567ee-129">Kaldırma anahtarını görüntülemek kolaylaştırmak için size bir Windows PowerShell sürücüsü bu kayıt defteri konumuna eşleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="567ee-129">To make it easier to view the Uninstall key, we can map a Windows PowerShell drive to this registry location:</span></span>

```
PS> New-PSDrive -Name Uninstall -PSProvider Registry -Root HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall    

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Uninstall  Registry      HKEY_LOCAL_MACHINE\SOFTWARE\Micr...
```

> [!NOTE]
> <span data-ttu-id="567ee-130">**HKLM:** sürücüsünün köküne eşlenen **HKEY_LOCAL_MACHINE**, o sürücüye kaldırma anahtarını yolunu kullandık.</span><span class="sxs-lookup"><span data-stu-id="567ee-130">The **HKLM:** drive is mapped to the root of **HKEY_LOCAL_MACHINE**, so we used that drive in the path to the Uninstall key.</span></span> <span data-ttu-id="567ee-131">Yerine **HKLM:** şu kayıt defteri yolunu kullanarak belirttiğiniz **HKLM** veya **HKEY_LOCAL_MACHINE**.</span><span class="sxs-lookup"><span data-stu-id="567ee-131">Instead of **HKLM:** we could have specified the registry path by using either **HKLM** or **HKEY_LOCAL_MACHINE**.</span></span> <span data-ttu-id="567ee-132">Var olan bir kayıt defteri sürücüsüne kullanmanın avantajı, biz sekme tamamlama biz bunları yazmaya gerek yoktur anahtarları adlarında doldurmak için kullanabilirsiniz ' dir.</span><span class="sxs-lookup"><span data-stu-id="567ee-132">The advantage of using an existing registry drive is that we can use tab-completion to fill in the keys names, so we do not need to type them.</span></span>

<span data-ttu-id="567ee-133">Biz şimdi "hızla ve kolayca uygulama yüklemeleri için aramak için kullanılan Uninstall" adlı bir sürücüye sahip.</span><span class="sxs-lookup"><span data-stu-id="567ee-133">We now have a drive named "Uninstall" that can be used to quickly and conveniently look for application installations.</span></span> <span data-ttu-id="567ee-134">Biz kaldırma kayıt defteri anahtarlarında sayısı sayım tarafından yüklenen uygulamaların sayısı bulabilirsiniz: Windows PowerShell sürücüsü:</span><span class="sxs-lookup"><span data-stu-id="567ee-134">We can find the number of installed applications by counting the number of registry keys in the Uninstall: Windows PowerShell drive:</span></span>

```
PS> (Get-ChildItem -Path Uninstall:).Count
459
```

<span data-ttu-id="567ee-135">Biz bu uygulamaların daha fazla listesini teknikler, çeşitli kullanarak itibaren arayabilirsiniz **Get-Childıtem**.</span><span class="sxs-lookup"><span data-stu-id="567ee-135">We can search this list of applications further by using a variety of techniques, beginning with **Get-ChildItem**.</span></span> <span data-ttu-id="567ee-136">Uygulamaların bir listesini almak ve bunları kaydetmek için **$UninstallableApplications** değişken, aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="567ee-136">To get a list of applications and save them in the **$UninstallableApplications** variable, use the following command:</span></span>

```
$UninstallableApplications = Get-ChildItem -Path Uninstall:
```

> [!NOTE]
> <span data-ttu-id="567ee-137">Uzun Buraya bir değişken adı daha anlaşılır olması için kullanıyoruz.</span><span class="sxs-lookup"><span data-stu-id="567ee-137">We are using a lengthy variable name here for clarity.</span></span> <span data-ttu-id="567ee-138">Gerçek kullanımda uzun adlar kullanmak için bir neden yoktur.</span><span class="sxs-lookup"><span data-stu-id="567ee-138">In actual use, there is no reason to use long names.</span></span> <span data-ttu-id="567ee-139">Değişken adları için sekme tamamlama kullanabilmenize karşın, 1-2 karakter adları hızı için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="567ee-139">Although you can use tab-completion for variable names, you can also use 1-2 character names for speed.</span></span> <span data-ttu-id="567ee-140">Kod yeniden kullanım için geliştirirken uzun, açıklayıcı adlar en kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="567ee-140">Longer, descriptive names are most useful when you are developing code for reuse.</span></span>

<span data-ttu-id="567ee-141">Kayıt defteri anahtarları kaldırma altındaki kayıt defteri girdilerini değerlerini görüntülemek için kayıt defteri anahtarlarının GetValue yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="567ee-141">To display the values of the registry entries in the registry keys under Uninstall, use the GetValue method of the registry keys.</span></span> <span data-ttu-id="567ee-142">Yönteminin değerini kayıt defteri girdisini adıdır.</span><span class="sxs-lookup"><span data-stu-id="567ee-142">The value of the method is the name of the registry entry.</span></span>

<span data-ttu-id="567ee-143">Örneğin, uygulamaların görünen adları Uninstall anahtarında bulmak için aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="567ee-143">For example, to find the display names of applications in the Uninstall key, use the following command:</span></span>

```
PS> Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue("DisplayName") }
```

<span data-ttu-id="567ee-144">Bu değerler benzersiz garantisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="567ee-144">There is no guarantee that these values are unique.</span></span> <span data-ttu-id="567ee-145">Aşağıdaki örnekte, "Windows Media Kodlayıcısı 9 Series" iki yüklü öğeleri görünür:</span><span class="sxs-lookup"><span data-stu-id="567ee-145">In the following example, two installed items appear as "Windows Media Encoder 9 Series":</span></span>

```
PS> Get-ChildItem -Path Uninstall: | Where-Object -FilterScript { $_.GetValue("DisplayName") -eq "Windows Media Encoder 9 Series"}

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Micros
oft\Windows\CurrentVersion\Uninstall

SKC  VC Name                           Property
---  -- ----                           --------
  0   3 Windows Media Encoder 9        {DisplayName, DisplayIcon, UninstallS...
  0  24 {E38C00D0-A68B-4318-A8A6-F7... {AuthorizedCDFPrefix, Comments, Conta...
```

### <a name="installing-applications"></a><span data-ttu-id="567ee-146">Uygulamaları yükleme</span><span class="sxs-lookup"><span data-stu-id="567ee-146">Installing Applications</span></span>
<span data-ttu-id="567ee-147">Kullanabileceğiniz **Win32_Product** uzaktan veya yerel olarak Windows Installer paketleri yüklemek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="567ee-147">You can use the **Win32_Product** class to install Windows Installer packages, remotely or locally.</span></span>

> [!NOTE]
> <span data-ttu-id="567ee-148">Bir uygulamayı yüklemek için Windows Vista, Windows Server 2008 ve sonraki Windows sürümlerinde Windows PowerShell "Yönetici olarak çalıştır" seçeneğiyle başlatmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="567ee-148">On Windows Vista, Windows Server 2008, and later versions of Windows, to install an application, you must start Windows PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="567ee-149">WMI alt sistemi, Windows PowerShell yolları anlamıyor olduğundan Uzaktan Yükleme, bir Evrensel Adlandırma Kuralı (UNC) ağ yolu .msi paketin yolunu belirtmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="567ee-149">When installing remotely, use a Universal Naming Convention (UNC) network path to specify the path to the .msi package, because the WMI subsystem does not understand Windows PowerShell paths.</span></span> <span data-ttu-id="567ee-150">Örneğin, NewPackage.msi paketini yüklemek için bulunan ağ paylaşımında \\ \\AppServ\\dsp PC01, uzak bilgisayarda Windows PowerShell komut isteminde aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="567ee-150">For example, to install the NewPackage.msi package located in the network share \\\\AppServ\\dsp on the remote computer PC01, type the following command at the Windows PowerShell prompt:</span></span>

```
(Get-WMIObject -ComputerName PC01 -List | Where-Object -FilterScript {$_.Name -eq "Win32_Product"}).Install(\\AppSrv\dsp\NewPackage.msi)
```

<span data-ttu-id="567ee-151">Windows Installer teknolojisi kullanmayın uygulamalar otomatik dağıtım için kullanılabilir uygulamaya özgü yöntemleri sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="567ee-151">Applications that do not use Windows Installer technology may have application-specific methods available for automated deployment.</span></span> <span data-ttu-id="567ee-152">Dağıtım Otomasyon için bir yöntem olup olmadığını belirlemek için uygulamanın belgelerine bakın veya uygulama satıcısının destek sistem başvurun.</span><span class="sxs-lookup"><span data-stu-id="567ee-152">To determine whether there is a method for deployment automation, check the documentation for the application or consult the application vendor's support system.</span></span> <span data-ttu-id="567ee-153">Uygulamanın satıcısına özellikle uygulama yükleme Otomasyon için tasarım değil olsa bile bazı durumlarda, otomasyon için bazı teknikleri yükleyici yazılım üreticisine sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="567ee-153">In some cases, even if the application vendor did not specifically design the application for installation automation, the installer software manufacturer may have some techniques for automation.</span></span>

### <a name="removing-applications"></a><span data-ttu-id="567ee-154">Uygulamaları kaldırma</span><span class="sxs-lookup"><span data-stu-id="567ee-154">Removing Applications</span></span>
<span data-ttu-id="567ee-155">Windows PowerShell kullanarak bir Windows Installer paketi kaldırma yaklaşık bir paket yükleme olarak aynı şekilde çalışır.</span><span class="sxs-lookup"><span data-stu-id="567ee-155">Removing a Windows Installer package by using Windows PowerShell works in approximately the same way as installing a package.</span></span> <span data-ttu-id="567ee-156">Kaldırılacak paketin adına göre seçen örnek aşağıda verilmiştir; Bazı durumlarda Filtrele daha kolay olabilir **Identifyingnumber**:</span><span class="sxs-lookup"><span data-stu-id="567ee-156">Here is an example that selects the package to uninstall based on its name; in some cases it may be easier to filter with the **IdentifyingNumber**:</span></span>

```
(Get-WmiObject -Class Win32_Product -Filter "Name='ILMerge'" -ComputerName . ).Uninstall()
```

<span data-ttu-id="567ee-157">Diğer uygulamaların kaldırılması bile yerel olarak işiniz bittiğinde nedenle oldukça basit değil.</span><span class="sxs-lookup"><span data-stu-id="567ee-157">Removing other applications is not quite so simple, even when done locally.</span></span> <span data-ttu-id="567ee-158">Biz çıkartarak bu uygulamalar için komut satırı kaldırma dizeleri bulabilirsiniz **UninstallString** özelliği.</span><span class="sxs-lookup"><span data-stu-id="567ee-158">We can find the command line uninstallation strings for these applications by extracting the **UninstallString** property.</span></span> <span data-ttu-id="567ee-159">Bu yöntem, eski programları kaldırma anahtarı altında görünen ve Windows Installer uygulamaları için çalışır:</span><span class="sxs-lookup"><span data-stu-id="567ee-159">This method works for Windows Installer applications and for older programs appearing under the Uninstall key:</span></span>

```
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue("UninstallString") }
```

<span data-ttu-id="567ee-160">İsterseniz, çıktı görünen ada göre filtreleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="567ee-160">You can filter the output by the display name, if you like:</span></span>

```
Get-ChildItem -Path Uninstall: | Where-Object -FilterScript { $_.GetValue("DisplayName") -like "Win*"} | ForEach-Object -Process { $_.GetValue("UninstallString") }
```

<span data-ttu-id="567ee-161">Ancak, bu dizeler doğrudan bazı değişiklik yapmadan Windows PowerShell isteminden kullanılamayabilir.</span><span class="sxs-lookup"><span data-stu-id="567ee-161">However, these strings may not be directly usable from the Windows PowerShell prompt without some modification.</span></span>

### <a name="upgrading-windows-installer-applications"></a><span data-ttu-id="567ee-162">Windows Installer uygulamalarını yükseltme</span><span class="sxs-lookup"><span data-stu-id="567ee-162">Upgrading Windows Installer Applications</span></span>
<span data-ttu-id="567ee-163">Uygulama yükseltme için uygulama yükseltme paketi uygulama ve yolun adını bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="567ee-163">To upgrade an application, you need to know the name of the application and the path to the application upgrade package.</span></span> <span data-ttu-id="567ee-164">Bu bilgi ile tek bir Windows PowerShell komut uygulamayla yükseltebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="567ee-164">With that information, you can upgrade an application with a single Windows PowerShell command:</span></span>

```
(Get-WmiObject -Class Win32_Product -ComputerName . -Filter "Name='OldAppName'").Upgrade(\\AppSrv\dsp\OldAppUpgrade.msi)
```

