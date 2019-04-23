---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Windows PowerShell Sürücülerini Yönetme
ms.assetid: bd809e38-8de9-437a-a250-f30a667d11b4
ms.openlocfilehash: 9ac5136fb28b450ea6397cab2f36082c50f22e1f
ms.sourcegitcommit: f4bd4e116e22c8b5bfcb61680a7c42e58b4da93e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59984281"
---
# <a name="managing-windows-powershell-drives"></a><span data-ttu-id="8d151-103">Windows PowerShell Sürücülerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="8d151-103">Managing Windows PowerShell Drives</span></span>

<span data-ttu-id="8d151-104">A *Windows PowerShell sürücüsünü* gibi Windows PowerShell bir dosya sistemi sürücüsüne erişiminiz bir veri deposu konumdur.</span><span class="sxs-lookup"><span data-stu-id="8d151-104">A *Windows PowerShell drive* is a data store location that you can access like a file system drive in Windows PowerShell.</span></span> <span data-ttu-id="8d151-105">Dosya sistemi (C: ve D:), kayıt defteri sürücüler gibi Windows PowerShell sağlayıcıları bazı sürücüler için oluşturduğunuz sürücüler (HKCU: ve HKLM:) ve sertifika sürücü (Cert:), kendi Windows PowerShell sürücülerini de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d151-105">The Windows PowerShell providers create some drives for you, such as the file system drives (including C: and D:), the registry drives (HKCU: and HKLM:), and the certificate drive (Cert:), and you can create your own Windows PowerShell drives.</span></span> <span data-ttu-id="8d151-106">Bu sürücüler oldukça faydalıdır, ancak bunlar yalnızca Windows PowerShell içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8d151-106">These drives are very useful, but they are available only within Windows PowerShell.</span></span> <span data-ttu-id="8d151-107">Bunları dosya Gezgini veya Cmd.exe gibi diğer Windows araçlarını kullanarak erişemez.</span><span class="sxs-lookup"><span data-stu-id="8d151-107">You cannot access them by using other Windows tools, such as File Explorer or Cmd.exe.</span></span>

<span data-ttu-id="8d151-108">Windows PowerShell kullanan bir isim **PSDrive**, Windows PowerShell ile çalışmayı komutları için sürücüler.</span><span class="sxs-lookup"><span data-stu-id="8d151-108">Windows PowerShell uses the noun, **PSDrive**, for commands that work with Windows PowerShell drives.</span></span> <span data-ttu-id="8d151-109">Windows PowerShell oturumunuzda bir listesi için Windows PowerShell sürücülerini, kullanın **Get-PSDrive** cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="8d151-109">For a list of the Windows PowerShell drives in your Windows PowerShell session, use the **Get-PSDrive** cmdlet.</span></span>

```
PS> Get-PSDrive

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
A          FileSystem    A:\
Alias      Alias
C          FileSystem    C:\                                 ...And Settings\me
cert       Certificate   \
D          FileSystem    D:\
Env        Environment
Function   Function
HKCU       Registry      HKEY_CURRENT_USER
HKLM       Registry      HKEY_LOCAL_MACHINE
Variable   Variable
```

<span data-ttu-id="8d151-110">Sisteminizde sürücülerle görüntüsündeki sürücüleri farklı olsa da, listenin çıktısına benzer görünecektir **Get-PSDrive** yukarıda gösterilen komutu.</span><span class="sxs-lookup"><span data-stu-id="8d151-110">Although the drives in the display vary with the drives on your system, the listing will look similar to the output of the **Get-PSDrive** command shown above.</span></span>

<span data-ttu-id="8d151-111">Dosya sistemi sürücüleri, Windows PowerShell sürücülerini bir alt kümesidir.</span><span class="sxs-lookup"><span data-stu-id="8d151-111">File system drives are a subset of the Windows PowerShell drives.</span></span> <span data-ttu-id="8d151-112">Dosya sistemi giriş sağlayıcısı sütunda tarafından dosya sistemi sürücüleri tespit edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d151-112">You can identify the file system drives by the FileSystem entry in the Provider column.</span></span> <span data-ttu-id="8d151-113">(Dosya sistemi sürücüleri Windows PowerShell'de Windows PowerShell dosya sistemi sağlayıcısı tarafından desteklenir.)</span><span class="sxs-lookup"><span data-stu-id="8d151-113">(The file system drives in Windows PowerShell are supported by the Windows PowerShell FileSystem provider.)</span></span>

<span data-ttu-id="8d151-114">Söz dizimi görmek için **Get-PSDrive** cmdlet'i, bir **Get-Command** komutunu **söz dizimi** parametresi:</span><span class="sxs-lookup"><span data-stu-id="8d151-114">To see the syntax of the **Get-PSDrive** cmdlet, type a **Get-Command** command with the **Syntax** parameter:</span></span>

```
PS> Get-Command -Name Get-PSDrive -Syntax

Get-PSDrive [[-Name] <String[]>] [-Scope <String>] [-PSProvider <String[]>] [-V
erbose] [-Debug] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-
OutVariable <String>] [-OutBuffer <Int32>]
```

<span data-ttu-id="8d151-115">**PSProvider** görüntülemek için Windows PowerShell Bu sürücüleri yalnızca parametresi sağlar, belirli bir sağlayıcı tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="8d151-115">The **PSProvider** parameter lets you display only the Windows PowerShell drives that are supported by a particular provider.</span></span> <span data-ttu-id="8d151-116">Windows PowerShell dosya sistemi sağlayıcısı tarafından desteklenen Windows PowerShell sürücülerini görüntülemek için örneğin bir **Get-PSDrive** komutunu **PSProvider** parametresi ve  **Dosya sistemi** değeri:</span><span class="sxs-lookup"><span data-stu-id="8d151-116">For example, to display only the Windows PowerShell drives that are supported by the Windows PowerShell FileSystem provider, type a **Get-PSDrive** command with the **PSProvider** parameter and the **FileSystem** value:</span></span>

```
PS> Get-PSDrive -PSProvider FileSystem

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
A          FileSystem    A:\
C          FileSystem    C:\                           ...nd Settings\PowerUser
D          FileSystem    D:\
```

<span data-ttu-id="8d151-117">Kayıt defteri kovanları temsil eden Windows PowerShell sürücülerini görüntülemek için kullanın **PSProvider** parametre yalnızca, Windows PowerShell sürücülerini görüntülemek için Windows PowerShell ile kayıt defteri sağlayıcı tarafından desteklenir:</span><span class="sxs-lookup"><span data-stu-id="8d151-117">To view the Windows PowerShell drives that represent registry hives, use the **PSProvider** parameter to display only the Windows PowerShell drives that are supported by the Windows PowerShell Registry provider:</span></span>

```
PS> Get-PSDrive -PSProvider Registry

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
HKCU       Registry      HKEY_CURRENT_USER
HKLM       Registry      HKEY_LOCAL_MACHINE
```

<span data-ttu-id="8d151-118">Windows PowerShell'i sürücülerle standart konumu cmdlet'leri de kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8d151-118">You can also use the standard Location cmdlets with the Windows PowerShell drives:</span></span>

```
PS> Set-Location HKLM:\SOFTWARE
PS> Push-Location .\Microsoft
PS> Get-Location

Path
----
HKLM:\SOFTWARE\Microsoft
```

## <a name="adding-new-windows-powershell-drives-new-psdrive"></a><span data-ttu-id="8d151-119">Yeni Windows PowerShell ekleme (PSDrive yeni) sürücüleri</span><span class="sxs-lookup"><span data-stu-id="8d151-119">Adding New Windows PowerShell Drives (New-PSDrive)</span></span>

<span data-ttu-id="8d151-120">Kullanarak kendi Windows PowerShell sürücülerini ekleyebilirsiniz **yeni PSDrive** komutu.</span><span class="sxs-lookup"><span data-stu-id="8d151-120">You can add your own Windows PowerShell drives by using the **New-PSDrive** command.</span></span> <span data-ttu-id="8d151-121">Sözdizimi almak için **yeni PSDrive** komutu, girin **Get-Command** komutunu **söz dizimi** parametresi:</span><span class="sxs-lookup"><span data-stu-id="8d151-121">To get the syntax for the **New-PSDrive** command, enter the **Get-Command** command with the **Syntax** parameter:</span></span>

```
PS> Get-Command -Name New-PSDrive -Syntax

New-PSDrive [-Name] <String> [-PSProvider] <String> [-Root] <String> [-Descript
ion <String>] [-Scope <String>] [-Credential <PSCredential>] [-Verbose] [-Debug
] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-OutVariable <St
ring>] [-OutBuffer <Int32>] [-WhatIf] [-Confirm]
```

<span data-ttu-id="8d151-122">Yeni bir Windows PowerShell sürücüsü oluşturmak için üç parametre belirtmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="8d151-122">To create a new Windows PowerShell drive, you must supply three parameters:</span></span>

- <span data-ttu-id="8d151-123">(Herhangi bir geçerli Windows PowerShell adı kullanabilirsiniz) sürücü için bir ad</span><span class="sxs-lookup"><span data-stu-id="8d151-123">A name for the drive (you can use any valid Windows PowerShell name)</span></span>

- <span data-ttu-id="8d151-124">' % S'PSProvider (dosya sistemi konumları için "dosya" ve "Kayıt" kayıt defteri konumları için kullanın)</span><span class="sxs-lookup"><span data-stu-id="8d151-124">The PSProvider (use "FileSystem" for file system locations and "Registry" for registry locations)</span></span>

- <span data-ttu-id="8d151-125">Kök, diğer bir deyişle, yeni sürücüsünün kök yolu</span><span class="sxs-lookup"><span data-stu-id="8d151-125">The root, that is, the path to the root of the new drive</span></span>

<span data-ttu-id="8d151-126">Örneğin, ", bilgisayarınızda Microsoft Office uygulamaları gibi içeren klasörle eşlendi Office" adlı bir sürücüsü oluşturabilirsiniz **C:\\Program dosyaları\\Microsoft Office\\11**.</span><span class="sxs-lookup"><span data-stu-id="8d151-126">For example, you can create a drive named "Office" that is mapped to the folder that contains the Microsoft Office applications on your computer, such as **C:\\Program Files\\Microsoft Office\\OFFICE11**.</span></span> <span data-ttu-id="8d151-127">Sürücü oluşturmak için aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="8d151-127">To create the drive, type the following command:</span></span>

```
PS> New-PSDrive -Name Office -PSProvider FileSystem -Root "C:\Program Files\Micr
osoft Office\OFFICE11"

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Office     FileSystem    C:\Program Files\Microsoft Offic...
```

> [!NOTE]
> <span data-ttu-id="8d151-128">Genel olarak, yolları büyük küçük harfe duyarlı değildir.</span><span class="sxs-lookup"><span data-stu-id="8d151-128">In general, paths are not case-sensitive.</span></span>

<span data-ttu-id="8d151-129">--Üste adına göre tüm Windows PowerShell sürücülerini yaptığınız gibi yeni Windows PowerShell sürücüsüne bakın (**:**).</span><span class="sxs-lookup"><span data-stu-id="8d151-129">You refer to the new Windows PowerShell drive as you do all Windows PowerShell drives -- by its name followed by a colon (**:**).</span></span>

<span data-ttu-id="8d151-130">Bir Windows PowerShell sürücüsü, birçok görevi çok daha kolay hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d151-130">A Windows PowerShell drive can make many tasks much simpler.</span></span> <span data-ttu-id="8d151-131">Örneğin, en önemli Windows kayıt defteri anahtarları erişimi hantal ve hatırlamak zor hale son derece uzun yollar vardır.</span><span class="sxs-lookup"><span data-stu-id="8d151-131">For example, some of the most important keys in the Windows registry have extremely long paths, making them cumbersome to access and difficult to remember.</span></span> <span data-ttu-id="8d151-132">Önemli yapılandırma bilgileri bulunduğu altında **HKEY_LOCAL_MACHINE\\yazılım\\Microsoft\\Windows\\CurrentVersion**.</span><span class="sxs-lookup"><span data-stu-id="8d151-132">Critical configuration information resides under **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion**.</span></span> <span data-ttu-id="8d151-133">Görüntüleyip CurrentVersion kayıt defteri anahtarında öğeleri değiştirmek için yazarak bu anahtar kökü belirtilmiş bir Windows PowerShell sürücüsü oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8d151-133">To view and change items in the CurrentVersion registry key, you can create a Windows PowerShell drive that is rooted in that key by typing:</span></span>

```
PS> New-PSDrive -Name cvkey -PSProvider Registry -Root HKLM\Software\Microsoft\W
indows\CurrentVersion

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
cvkey      Registry      HKLM\Software\Microsoft\Windows\...
```

<span data-ttu-id="8d151-134">Ardından bir konuma değiştirebilirsiniz **cvkey:** sürücü, başka bir sürücü gibi:''</span><span class="sxs-lookup"><span data-stu-id="8d151-134">You can then change location to the **cvkey:** drive as you would any other drive:\`\`</span></span>

`PS> cd cvkey:`

<span data-ttu-id="8d151-135">veya:</span><span class="sxs-lookup"><span data-stu-id="8d151-135">or:</span></span>

```
PS> Set-Location cvkey: -PassThru

Path
----
cvkey:\
```

<span data-ttu-id="8d151-136">New-PsDrive cmdlet'i yeni bir sürücüye yalnızca geçerli Windows PowerShell oturumuna ekler.</span><span class="sxs-lookup"><span data-stu-id="8d151-136">The New-PsDrive cmdlet adds the new drive only to the current Windows PowerShell session.</span></span> <span data-ttu-id="8d151-137">Windows PowerShell penceresini kapatırsanız yeni sürücü kaybolur.</span><span class="sxs-lookup"><span data-stu-id="8d151-137">If you close the Windows PowerShell window, the new drive is lost.</span></span> <span data-ttu-id="8d151-138">Bir Windows PowerShell sürücüsü kaydetmek için geçerli Windows PowerShell oturumunda dışarı aktarmak için konsol içi dışarı aktarma cmdlet'ini kullanın ve ardından PowerShell.exe **PSConsoleFile** parametresini kullanarak içe aktarın.</span><span class="sxs-lookup"><span data-stu-id="8d151-138">To save a Windows PowerShell drive, use the Export-Console cmdlet to export the current Windows PowerShell session, and then use the PowerShell.exe **PSConsoleFile** parameter to import it.</span></span> <span data-ttu-id="8d151-139">Veya Windows PowerShell profiliniz için yeni bir sürücüye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8d151-139">Or, add the new drive to your Windows PowerShell profile.</span></span>

## <a name="deleting-windows-powershell-drives-remove-psdrive"></a><span data-ttu-id="8d151-140">Windows PowerShell siliniyor (Remove-PSDrive) sürücüleri</span><span class="sxs-lookup"><span data-stu-id="8d151-140">Deleting Windows PowerShell Drives (Remove-PSDrive)</span></span>

<span data-ttu-id="8d151-141">Kullanarak Windows Powershell'den sürücüleri silebilirsiniz **Remove-PSDrive** cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="8d151-141">You can delete drives from Windows PowerShell by using the **Remove-PSDrive** cmdlet.</span></span> <span data-ttu-id="8d151-142">**Remove-PSDrive** cmdlet'i kullanımı kolay; belirli bir Windows PowerShell sürücüsü silmek için yalnızca Windows PowerShell sürücüsü ad sağlayın.</span><span class="sxs-lookup"><span data-stu-id="8d151-142">The **Remove-PSDrive** cmdlet is easy to use; to delete a specific Windows PowerShell drive, you just supply the Windows PowerShell drive name.</span></span>

<span data-ttu-id="8d151-143">Örneğin, eklediğiniz **Office:** Windows PowerShell sürücüsü, gösterildiği gibi **yeni PSDrive** konu silebilirsiniz, yazarak:</span><span class="sxs-lookup"><span data-stu-id="8d151-143">For example, if you added the **Office:** Windows PowerShell drive, as shown in the **New-PSDrive** topic, you can delete it by typing:</span></span>

```powershell
Remove-PSDrive -Name Office
```

<span data-ttu-id="8d151-144">Silinecek **cvkey:** Windows PowerShell sürücüsü de görünmesini **yeni PSDrive** konu, aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="8d151-144">To delete the **cvkey:** Windows PowerShell drive, also shown in the **New-PSDrive** topic, use the following command:</span></span>

```powershell
Remove-PSDrive -Name cvkey
```

<span data-ttu-id="8d151-145">Bir Windows PowerShell sürücüsü silmek kolaydır, ancak sürücü çalışırken silinemiyor.</span><span class="sxs-lookup"><span data-stu-id="8d151-145">It's easy to delete a Windows PowerShell drive, but you can't delete it while you are in the drive.</span></span> <span data-ttu-id="8d151-146">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="8d151-146">For example:</span></span>

```
PS> cd office:
PS Office:\> remove-psdrive -name office
Remove-PSDrive : Cannot remove drive 'Office' because it is in use.
At line:1 char:15
+ remove-psdrive  <<<< -name office
```

## <a name="adding-and-removing-drives-outside-windows-powershell"></a><span data-ttu-id="8d151-147">Ekleme ve kaldırma dışında Windows PowerShell sürücüsü</span><span class="sxs-lookup"><span data-stu-id="8d151-147">Adding and Removing Drives Outside Windows PowerShell</span></span>

<span data-ttu-id="8d151-148">Windows PowerShell algılar eklendiğinde veya kaldırıldığında, eşlenen ağ sürücülerini, bağlı USB sürücülerin ve kullanarak silinen sürücüler dahil olmak üzere, Windows dosya sistemi sürücüleri **net kullanım** komut veya  **WScript.NetworkMapNetworkDrive** ve **RemoveNetworkDrive** bir Windows komut dosyası sistemi (WSH) komut dosyasındaki yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="8d151-148">Windows PowerShell detects file system drives that are added or removed in Windows, including network drives that are mapped, USB drives that are attached, and drives that are deleted by using either the **net use** command or the **WScript.NetworkMapNetworkDrive** and **RemoveNetworkDrive** methods from a Windows Script Host (WSH) script.</span></span>