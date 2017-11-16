---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: "Windows PowerShell yönetme sürücüler"
ms.assetid: bd809e38-8de9-437a-a250-f30a667d11b4
ms.openlocfilehash: e2908246bb584291f04b67dc8635caec93d3b72e
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2017
---
# <a name="managing-windows-powershell-drives"></a><span data-ttu-id="f9921-103">Windows PowerShell yönetme sürücüler</span><span class="sxs-lookup"><span data-stu-id="f9921-103">Managing Windows PowerShell Drives</span></span>
<span data-ttu-id="f9921-104">A *Windows PowerShell sürücüsü* Windows PowerShell'de dosya sistemi sürücü gibi erişmek için bir veri deposu konumudur.</span><span class="sxs-lookup"><span data-stu-id="f9921-104">A *Windows PowerShell drive* is a data store location that you can access like a file system drive in Windows PowerShell.</span></span> <span data-ttu-id="f9921-105">Dosya sistemi (C: ve D:), kayıt defteri sürücüler gibi Windows PowerShell sağlayıcıları bazı sürücüler için oluşturduğunuz sürücüler (HKCU: ve HKLM:) ve sertifika sürücüsü (Cert:), ve kendi Windows PowerShell sürücü oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f9921-105">The Windows PowerShell providers create some drives for you, such as the file system drives (including C: and D:), the registry drives (HKCU: and HKLM:), and the certificate drive (Cert:), and you can create your own Windows PowerShell drives.</span></span> <span data-ttu-id="f9921-106">Bu sürücüler oldukça faydalıdır, ancak bunlar yalnızca Windows PowerShell içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f9921-106">These drives are very useful, but they are available only within Windows PowerShell.</span></span> <span data-ttu-id="f9921-107">Bunları dosya Gezgini veya Cmd.exe gibi diğer Windows araçlarını kullanarak erişemez.</span><span class="sxs-lookup"><span data-stu-id="f9921-107">You cannot access them by using other Windows tools, such as File Explorer or Cmd.exe.</span></span>

<span data-ttu-id="f9921-108">Windows PowerShell kullanan isim **PSDrive**, Windows PowerShell ile çalışmayı komutlar için sürücüler.</span><span class="sxs-lookup"><span data-stu-id="f9921-108">Windows PowerShell uses the noun, **PSDrive**, for commands that work with Windows PowerShell drives.</span></span> <span data-ttu-id="f9921-109">Windows PowerShell listesini Windows PowerShell oturumunuzda sürücüler için kullanmak **Get-PSDrive** cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="f9921-109">For a list of the Windows PowerShell drives in your Windows PowerShell session, use the **Get-PSDrive** cmdlet.</span></span>

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

<span data-ttu-id="f9921-110">Sisteminizde sürücülerle görüntü sürücüleri farklılık rağmen listenin çıkışına şuna benzer **Get-PSDrive** yukarıda gösterilen komutu.</span><span class="sxs-lookup"><span data-stu-id="f9921-110">Although the drives in the display vary with the drives on your system, the listing will look similar to the output of the **Get-PSDrive** command shown above.</span></span>

<span data-ttu-id="f9921-111">Dosya sistemi sürücülerine Windows PowerShell sürücülerinin bir alt kümesidir.</span><span class="sxs-lookup"><span data-stu-id="f9921-111">File system drives are a subset of the Windows PowerShell drives.</span></span> <span data-ttu-id="f9921-112">Dosya sistemi sürücülerine sağlayıcısı sütunundaki FileSystem girdi tarafından tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f9921-112">You can identify the file system drives by the FileSystem entry in the Provider column.</span></span> <span data-ttu-id="f9921-113">(Dosya sistemi sürücülerine Windows PowerShell'de Windows PowerShell FileSystem sağlayıcı tarafından desteklenir.)</span><span class="sxs-lookup"><span data-stu-id="f9921-113">(The file system drives in Windows PowerShell are supported by the Windows PowerShell FileSystem provider.)</span></span>

<span data-ttu-id="f9921-114">Söz dizimi görmek için **Get-PSDrive** cmdlet, bir **Get-Command** komutunu **sözdizimi** parametre:</span><span class="sxs-lookup"><span data-stu-id="f9921-114">To see the syntax of the **Get-PSDrive** cmdlet, type a **Get-Command** command with the **Syntax** parameter:</span></span>

```
PS> Get-Command -Name Get-PSDrive -Syntax
Get-PSDrive [[-Name] <String[]>] [-Scope <String>] [-PSProvider <String[]>] [-V
erbose] [-Debug] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-
OutVariable <String>] [-OutBuffer <Int32>]
```

<span data-ttu-id="f9921-115">**PSProvider** görüntülemek için Windows PowerShell sürücüleri yalnızca parametre sağlar, belirli bir sağlayıcı tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="f9921-115">The **PSProvider** parameter lets you display only the Windows PowerShell drives that are supported by a particular provider.</span></span> <span data-ttu-id="f9921-116">Örneğin, yalnızca Windows PowerShell dosya sistemi sağlayıcısı tarafından desteklenen Windows PowerShell sürücüleri görüntülemek için şunu yazın bir **Get-PSDrive** komutunu **PSProvider** parametresi ve  **Dosya sistemi** değeri:</span><span class="sxs-lookup"><span data-stu-id="f9921-116">For example, to display only the Windows PowerShell drives that are supported by the Windows PowerShell FileSystem provider, type a **Get-PSDrive** command with the **PSProvider** parameter and the **FileSystem** value:</span></span>

```
PS> Get-PSDrive -PSProvider FileSystem

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
A          FileSystem    A:\
C          FileSystem    C:\                           ...nd Settings\PowerUser
D          FileSystem    D:\
```

<span data-ttu-id="f9921-117">Kayıt defteri kovanları temsil eden Windows PowerShell sürücüleri görüntülemek için kullanın **PSProvider** parametresi yalnızca Windows PowerShell sürücüleri görüntülemek için Windows PowerShell kayıt defteri sağlayıcı tarafından desteklenir:</span><span class="sxs-lookup"><span data-stu-id="f9921-117">To view the Windows PowerShell drives that represent registry hives, use the **PSProvider** parameter to display only the Windows PowerShell drives that are supported by the Windows PowerShell Registry provider:</span></span>

<pre>PS> Get-PSDrive -PSProvider Registry
Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
HKCU       Registry      HKEY_CURRENT_USER
HKLM       Registry      HKEY_LOCAL_MACHINE</pre>

<span data-ttu-id="f9921-118">Windows PowerShell sürücülerle standart konumu cmdlet'leri de kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f9921-118">You can also use the standard Location cmdlets with the Windows PowerShell drives:</span></span>

<pre>PS> Set-Location HKLM:\SOFTWARE
PS> Push-Location .\Microsoft
PS> Get-Location
Path
----
HKLM:\SOFTWARE\Microsoft</pre>

### <a name="adding-new-windows-powershell-drives-new-psdrive"></a><span data-ttu-id="f9921-119">Yeni Windows PowerShell ekleme (PSDrive yeni) sürücüleri</span><span class="sxs-lookup"><span data-stu-id="f9921-119">Adding New Windows PowerShell Drives (New-PSDrive)</span></span>
<span data-ttu-id="f9921-120">Kullanarak kendi Windows PowerShell sürücüleri ekleyebilirsiniz **yeni PSDrive** komutu.</span><span class="sxs-lookup"><span data-stu-id="f9921-120">You can add your own Windows PowerShell drives by using the **New-PSDrive** command.</span></span> <span data-ttu-id="f9921-121">Sözdizimi almak için **yeni PSDrive** komutu, girin **Get-Command** komutunu **sözdizimi** parametre:</span><span class="sxs-lookup"><span data-stu-id="f9921-121">To get the syntax for the **New-PSDrive** command, enter the **Get-Command** command with the **Syntax** parameter:</span></span>

```
PS> Get-Command -Name New-PSDrive -Syntax
New-PSDrive [-Name] <String> [-PSProvider] <String> [-Root] <String> [-Descript
ion <String>] [-Scope <String>] [-Credential <PSCredential>] [-Verbose] [-Debug
] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-OutVariable <St
ring>] [-OutBuffer <Int32>] [-WhatIf] [-Confirm]
```

<span data-ttu-id="f9921-122">Yeni bir Windows PowerShell sürücüsü oluşturmak için üç parametre girmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="f9921-122">To create a new Windows PowerShell drive, you must supply three parameters:</span></span>

- <span data-ttu-id="f9921-123">(Herhangi bir geçerli Windows PowerShell adı kullanabilirsiniz) sürücü için bir ad</span><span class="sxs-lookup"><span data-stu-id="f9921-123">A name for the drive (you can use any valid Windows PowerShell name)</span></span>

- <span data-ttu-id="f9921-124">PSProvider (dosya sistemi konumları için "FileSystem" ve "Kayıt" kayıt defteri konumları için kullanın)</span><span class="sxs-lookup"><span data-stu-id="f9921-124">The PSProvider (use "FileSystem" for file system locations and "Registry" for registry locations)</span></span>

- <span data-ttu-id="f9921-125">Kök, diğer bir deyişle, yeni sürücüsünün kök yolu</span><span class="sxs-lookup"><span data-stu-id="f9921-125">The root, that is, the path to the root of the new drive</span></span>

<span data-ttu-id="f9921-126">Örneğin, ", bilgisayarınızda Microsoft Office uygulamaları gibi içeren klasöre eşlenen Office" adlı bir sürücüsü oluşturabilirsiniz **C:\\Program Files\\Microsoft Office\\11**.</span><span class="sxs-lookup"><span data-stu-id="f9921-126">For example, you can create a drive named "Office" that is mapped to the folder that contains the Microsoft Office applications on your computer, such as **C:\\Program Files\\Microsoft Office\\OFFICE11**.</span></span> <span data-ttu-id="f9921-127">Sürücü oluşturmak için aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="f9921-127">To create the drive, type the following command:</span></span>

```
PS> New-PSDrive -Name Office -PSProvider FileSystem -Root "C:\Program Files\Micr
osoft Office\OFFICE11"

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Office     FileSystem    C:\Program Files\Microsoft Offic...
```

> [!NOTE]
> <span data-ttu-id="f9921-128">Genel olarak, yolları büyük küçük harfe duyarlı değildir.</span><span class="sxs-lookup"><span data-stu-id="f9921-128">In general, paths are not case-sensitive.</span></span>

<span data-ttu-id="f9921-129">Tüm Windows PowerShell sürücüler--üste adını kullanarak yaptığınız gibi yeni bir Windows PowerShell sürücüye bakın (**:**).</span><span class="sxs-lookup"><span data-stu-id="f9921-129">You refer to the new Windows PowerShell drive as you do all Windows PowerShell drives -- by its name followed by a colon (**:**).</span></span>

<span data-ttu-id="f9921-130">Bir Windows PowerShell sürücüsü birçok görevi daha kolay hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f9921-130">A Windows PowerShell drive can make many tasks much simpler.</span></span> <span data-ttu-id="f9921-131">Örneğin, Windows kayıt defterinde en önemli unsurlardan bazılarının erişimi sıkıcı ve unutmayın zor hale aşırı uzun yolları vardır.</span><span class="sxs-lookup"><span data-stu-id="f9921-131">For example, some of the most important keys in the Windows registry have extremely long paths, making them cumbersome to access and difficult to remember.</span></span> <span data-ttu-id="f9921-132">Önemli yapılandırma bilgilerini bulunduğu altında **HKEY_LOCAL_MACHINE\\yazılım\\Microsoft\\Windows\\CurrentVersion**.</span><span class="sxs-lookup"><span data-stu-id="f9921-132">Critical configuration information resides under **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion**.</span></span> <span data-ttu-id="f9921-133">Görüntülemek ve CurrentVersion kayıt defteri anahtarında öğeleri değiştirmek için yazarak bu anahtar kökü belirtilmiş bir Windows PowerShell sürücüsü oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f9921-133">To view and change items in the CurrentVersion registry key, you can create a Windows PowerShell drive that is rooted in that key by typing:</span></span>

<pre>PS> New-PSDrive -Name cvkey -PSProvider Registry -Root HKLM\Software\Microsoft\W
indows\CurrentVersion
Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
cvkey      Registry      HKLM\Software\Microsoft\Windows\...</pre>

<span data-ttu-id="f9921-134">Daha sonra bir konuma değiştirebilirsiniz **cvkey:** sürücü, başka bir sürücü gibi:''</span><span class="sxs-lookup"><span data-stu-id="f9921-134">You can then change location to the **cvkey:** drive as you would any other drive:``</span></span>

`PS> cd cvkey:`

<span data-ttu-id="f9921-135">veya:</span><span class="sxs-lookup"><span data-stu-id="f9921-135">or:</span></span>

<pre>PS> Set-Location cvkey: -PassThru
Path
----
cvkey:\</pre>

<span data-ttu-id="f9921-136">Yeni PsDrive cmdlet yeni bir sürücüye yalnızca geçerli Windows PowerShell oturumuna ekler.</span><span class="sxs-lookup"><span data-stu-id="f9921-136">The New-PsDrive cmdlet adds the new drive only to the current Windows PowerShell session.</span></span> <span data-ttu-id="f9921-137">Windows PowerShell penceresini kapatın, yeni sürücü kaybolur.</span><span class="sxs-lookup"><span data-stu-id="f9921-137">If you close the Windows PowerShell window, the new drive is lost.</span></span> <span data-ttu-id="f9921-138">Bir Windows PowerShell sürücüsü kaydetmek için geçerli Windows PowerShell oturumu dışarı aktarmak için dışarı aktarma konsol cmdlet'ini kullanın ve PowerShell.exe kullanmak **PSConsoleFile** parametresini kullanarak içe aktarın.</span><span class="sxs-lookup"><span data-stu-id="f9921-138">To save a Windows PowerShell drive, use the Export-Console cmdlet to export the current Windows PowerShell session, and then use the PowerShell.exe **PSConsoleFile** parameter to import it.</span></span> <span data-ttu-id="f9921-139">Veya Windows PowerShell profiliniz için yeni bir sürücüye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f9921-139">Or, add the new drive to your Windows PowerShell profile.</span></span>

### <a name="deleting-windows-powershell-drives-remove-psdrive"></a><span data-ttu-id="f9921-140">Windows PowerShell silme (Remove-PSDrive) sürücüleri</span><span class="sxs-lookup"><span data-stu-id="f9921-140">Deleting Windows PowerShell Drives (Remove-PSDrive)</span></span>
<span data-ttu-id="f9921-141">Kullanarak Windows Powershell'den sürücüleri silebilirsiniz **Kaldır PSDrive** cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="f9921-141">You can delete drives from Windows PowerShell by using the **Remove-PSDrive** cmdlet.</span></span> <span data-ttu-id="f9921-142">**Kaldır PSDrive** cmdlet kullanımı kolaydır; belirli bir Windows PowerShell sürücüsü silmek için yalnızca Windows PowerShell sürücü adı sağlayın.</span><span class="sxs-lookup"><span data-stu-id="f9921-142">The **Remove-PSDrive** cmdlet is easy to use; to delete a specific Windows PowerShell drive, you just supply the Windows PowerShell drive name.</span></span>

<span data-ttu-id="f9921-143">Örneğin, eklediyseniz **Office:** gösterildiği gibi Windows PowerShell sürücüsü, **yeni PSDrive** konu silebilirsiniz, yazarak:</span><span class="sxs-lookup"><span data-stu-id="f9921-143">For example, if you added the **Office:** Windows PowerShell drive, as shown in the **New-PSDrive** topic, you can delete it by typing:</span></span>

```
PS> Remove-PSDrive -Name Office
```

<span data-ttu-id="f9921-144">Silmek için **cvkey:** Windows PowerShell sürücüsü, ayrıca görünmesini **yeni PSDrive** konu, aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="f9921-144">To delete the **cvkey:** Windows PowerShell drive, also shown in the **New-PSDrive** topic, use the following command:</span></span>

```
PS> Remove-PSDrive -Name cvkey
```

<span data-ttu-id="f9921-145">Bir Windows PowerShell sürücüsü silmek kolaydır, ancak sürücüde durumdayken silemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="f9921-145">It's easy to delete a Windows PowerShell drive, but you can't delete it while you are in the drive.</span></span> <span data-ttu-id="f9921-146">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="f9921-146">For example:</span></span>

```
PS> cd office:
PS Office:\> remove-psdrive -name office
Remove-PSDrive : Cannot remove drive 'Office' because it is in use.
At line:1 char:15
+ remove-psdrive  <<<< -name office
```

### <a name="adding-and-removing-drives-outside-windows-powershell"></a><span data-ttu-id="f9921-147">Ekleme ve kaldırma dış Windows PowerShell sürücüler</span><span class="sxs-lookup"><span data-stu-id="f9921-147">Adding and Removing Drives Outside Windows PowerShell</span></span>
<span data-ttu-id="f9921-148">Windows PowerShell algılar eklendiğinde veya kaldırıldığında eşlenen ağ sürücülerini, bağlı USB sürücülerin ve kullanarak silinmiş sürücüler dahil olmak üzere Windows dosya sistemi sürücülerine **net kullanım** komut veya  **WScript.NetworkMapNetworkDrive** ve **RemoveNetworkDrive** bir Windows Komut Dosyası Sistemi'ni (WSH) betikten yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="f9921-148">Windows PowerShell detects file system drives that are added or removed in Windows, including network drives that are mapped, USB drives that are attached, and drives that are deleted by using either the **net use** command or the **WScript.NetworkMapNetworkDrive** and **RemoveNetworkDrive** methods from a Windows Script Host (WSH) script.</span></span>

