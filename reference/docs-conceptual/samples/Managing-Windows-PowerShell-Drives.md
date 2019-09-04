---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: Windows PowerShell Sürücülerini Yönetme
ms.openlocfilehash: 5d1aba459caeaab2542e17e74534da6713b0faa9
ms.sourcegitcommit: 02eed65c526ef19cf952c2129f280bb5615bf0c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70215515"
---
# <a name="managing-windows-powershell-drives"></a><span data-ttu-id="25955-103">Windows PowerShell Sürücülerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="25955-103">Managing Windows PowerShell Drives</span></span>

<span data-ttu-id="25955-104">*Windows PowerShell sürücüsü* , Windows PowerShell 'de bir dosya sistemi sürücüsü gibi erişebileceğiniz bir veri deposu konumudur.</span><span class="sxs-lookup"><span data-stu-id="25955-104">A *Windows PowerShell drive* is a data store location that you can access like a file system drive in Windows PowerShell.</span></span> <span data-ttu-id="25955-105">Windows PowerShell sağlayıcıları dosya sistemi sürücüleri (C: ve D:), kayıt defteri sürücüleri (HKCU: ve HKLM:) ve sertifika sürücüsü (CERT:) dahil olmak üzere sizin için bazı sürücüler oluşturur ve kendi Windows PowerShell sürücülerinizi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="25955-105">The Windows PowerShell providers create some drives for you, such as the file system drives (including C: and D:), the registry drives (HKCU: and HKLM:), and the certificate drive (Cert:), and you can create your own Windows PowerShell drives.</span></span> <span data-ttu-id="25955-106">Bu sürücüler çok kullanışlıdır, ancak yalnızca Windows PowerShell 'de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="25955-106">These drives are very useful, but they are available only within Windows PowerShell.</span></span> <span data-ttu-id="25955-107">Dosya Gezgini veya cmd. exe gibi diğer Windows araçlarını kullanarak bunlara erişemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="25955-107">You cannot access them by using other Windows tools, such as File Explorer or Cmd.exe.</span></span>

<span data-ttu-id="25955-108">Windows PowerShell, Windows PowerShell sürücüleriyle çalışan komutlar için ad, **PSDrive**' u kullanır.</span><span class="sxs-lookup"><span data-stu-id="25955-108">Windows PowerShell uses the noun, **PSDrive**, for commands that work with Windows PowerShell drives.</span></span> <span data-ttu-id="25955-109">Windows PowerShell oturumunuzda Windows PowerShell sürücülerinin bir listesi için **Get-PSDrive** cmdlet 'ini kullanın.</span><span class="sxs-lookup"><span data-stu-id="25955-109">For a list of the Windows PowerShell drives in your Windows PowerShell session, use the **Get-PSDrive** cmdlet.</span></span>

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

<span data-ttu-id="25955-110">Ekrandaki sürücüler sisteminizdeki sürücülerle aynı olsa da, liste yukarıda gösterilen **Get-PSDrive** komutunun çıktısına benzer şekilde görünür.</span><span class="sxs-lookup"><span data-stu-id="25955-110">Although the drives in the display vary with the drives on your system, the listing will look similar to the output of the **Get-PSDrive** command shown above.</span></span>

<span data-ttu-id="25955-111">Dosya sistemi sürücüleri, Windows PowerShell sürücülerinin bir alt kümesidir.</span><span class="sxs-lookup"><span data-stu-id="25955-111">File system drives are a subset of the Windows PowerShell drives.</span></span> <span data-ttu-id="25955-112">Dosya sistemi sürücüleri sağlayıcı sütununda FileSystem girişi ile tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="25955-112">You can identify the file system drives by the FileSystem entry in the Provider column.</span></span> <span data-ttu-id="25955-113">(Windows PowerShell 'deki dosya sistemi sürücüleri Windows PowerShell dosya sistemi sağlayıcısı tarafından desteklenir.)</span><span class="sxs-lookup"><span data-stu-id="25955-113">(The file system drives in Windows PowerShell are supported by the Windows PowerShell FileSystem provider.)</span></span>

<span data-ttu-id="25955-114">**Get-PSDrive** cmdlet 'inin söz dizimini görmek Için, **sözdizimi** parametresine sahip bir **Get-Command** komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="25955-114">To see the syntax of the **Get-PSDrive** cmdlet, type a **Get-Command** command with the **Syntax** parameter:</span></span>

```
PS> Get-Command -Name Get-PSDrive -Syntax

Get-PSDrive [[-Name] <String[]>] [-Scope <String>] [-PSProvider <String[]>] [-V
erbose] [-Debug] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-
OutVariable <String>] [-OutBuffer <Int32>]
```

<span data-ttu-id="25955-115">**PSProvider** parametresi yalnızca belirli bir sağlayıcı tarafından desteklenen Windows PowerShell sürücüleri görüntülemenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="25955-115">The **PSProvider** parameter lets you display only the Windows PowerShell drives that are supported by a particular provider.</span></span> <span data-ttu-id="25955-116">Örneğin, yalnızca Windows PowerShell dosya sağlayıcısı tarafından desteklenen Windows PowerShell sürücülerinin görüntülenmesi için, **PSProvider** parametresine ve **dosya sistemi** değerine sahip bir **Get-PSDrive** komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="25955-116">For example, to display only the Windows PowerShell drives that are supported by the Windows PowerShell FileSystem provider, type a **Get-PSDrive** command with the **PSProvider** parameter and the **FileSystem** value:</span></span>

```
PS> Get-PSDrive -PSProvider FileSystem

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
A          FileSystem    A:\
C          FileSystem    C:\                           ...nd Settings\PowerUser
D          FileSystem    D:\
```

<span data-ttu-id="25955-117">Kayıt defteri kovanlarını temsil eden Windows PowerShell sürücüleri görüntülemek için **PSProvider** parametresini kullanarak yalnızca Windows PowerShell kayıt defteri sağlayıcısı tarafından desteklenen Windows PowerShell sürücüleri görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="25955-117">To view the Windows PowerShell drives that represent registry hives, use the **PSProvider** parameter to display only the Windows PowerShell drives that are supported by the Windows PowerShell Registry provider:</span></span>

```
PS> Get-PSDrive -PSProvider Registry

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
HKCU       Registry      HKEY_CURRENT_USER
HKLM       Registry      HKEY_LOCAL_MACHINE
```

<span data-ttu-id="25955-118">Standart konum cmdlet 'lerini Windows PowerShell sürücüleriyle de kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="25955-118">You can also use the standard Location cmdlets with the Windows PowerShell drives:</span></span>

```
PS> Set-Location HKLM:\SOFTWARE
PS> Push-Location .\Microsoft
PS> Get-Location

Path
----
HKLM:\SOFTWARE\Microsoft
```

## <a name="adding-new-windows-powershell-drives-new-psdrive"></a><span data-ttu-id="25955-119">Yeni Windows PowerShell sürücüleri ekleme (New-PSDrive)</span><span class="sxs-lookup"><span data-stu-id="25955-119">Adding New Windows PowerShell Drives (New-PSDrive)</span></span>

<span data-ttu-id="25955-120">**New-PSDrive** komutunu kullanarak kendi Windows PowerShell sürücülerinizi ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="25955-120">You can add your own Windows PowerShell drives by using the **New-PSDrive** command.</span></span> <span data-ttu-id="25955-121">**New-PSDrive** komutunun söz dizimini almak Için, **sözdizimi** parametresine sahip **Get-Command** komutunu girin:</span><span class="sxs-lookup"><span data-stu-id="25955-121">To get the syntax for the **New-PSDrive** command, enter the **Get-Command** command with the **Syntax** parameter:</span></span>

```
PS> Get-Command -Name New-PSDrive -Syntax

New-PSDrive [-Name] <String> [-PSProvider] <String> [-Root] <String> [-Descript
ion <String>] [-Scope <String>] [-Credential <PSCredential>] [-Verbose] [-Debug
] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-OutVariable <St
ring>] [-OutBuffer <Int32>] [-WhatIf] [-Confirm]
```

<span data-ttu-id="25955-122">Yeni bir Windows PowerShell sürücüsü oluşturmak için üç parametre sağlamanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="25955-122">To create a new Windows PowerShell drive, you must supply three parameters:</span></span>

- <span data-ttu-id="25955-123">Sürücü için bir ad (geçerli herhangi bir Windows PowerShell adı kullanabilirsiniz)</span><span class="sxs-lookup"><span data-stu-id="25955-123">A name for the drive (you can use any valid Windows PowerShell name)</span></span>

- <span data-ttu-id="25955-124">PSProvider (dosya sistemi konumları için "FileSystem" ve kayıt defteri konumları için "Registry" kullanın)</span><span class="sxs-lookup"><span data-stu-id="25955-124">The PSProvider (use "FileSystem" for file system locations and "Registry" for registry locations)</span></span>

- <span data-ttu-id="25955-125">Kök, diğer bir deyişle, yeni sürücünün kökünün yolu</span><span class="sxs-lookup"><span data-stu-id="25955-125">The root, that is, the path to the root of the new drive</span></span>

<span data-ttu-id="25955-126">Örneğin, bilgisayarınızdaki Microsoft Office uygulamaları içeren klasöre eşlenen "Office" adlı bir sürücü oluşturabilirsiniz. Örneğin, **C:\\program\\Files\\Microsoft Office OFFICE11**.</span><span class="sxs-lookup"><span data-stu-id="25955-126">For example, you can create a drive named "Office" that is mapped to the folder that contains the Microsoft Office applications on your computer, such as **C:\\Program Files\\Microsoft Office\\OFFICE11**.</span></span> <span data-ttu-id="25955-127">Sürücüyü oluşturmak için aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="25955-127">To create the drive, type the following command:</span></span>

```
PS> New-PSDrive -Name Office -PSProvider FileSystem -Root "C:\Program Files\Microsoft Office\OFFICE11"

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Office     FileSystem    C:\Program Files\Microsoft Offic...
```

> [!NOTE]
> <span data-ttu-id="25955-128">Genel olarak, yollar büyük/küçük harfe duyarlı değildir.</span><span class="sxs-lookup"><span data-stu-id="25955-128">In general, paths are not case-sensitive.</span></span>

<span data-ttu-id="25955-129">Yeni Windows PowerShell sürücüsüne, adına ve sonuna iki nokta üst üste ( **:** ) kadar tüm Windows PowerShell sürücülerine başvurursunuz.</span><span class="sxs-lookup"><span data-stu-id="25955-129">You refer to the new Windows PowerShell drive as you do all Windows PowerShell drives -- by its name followed by a colon (**:**).</span></span>

<span data-ttu-id="25955-130">Bir Windows PowerShell sürücüsü birçok görevi çok daha basit hale getirir.</span><span class="sxs-lookup"><span data-stu-id="25955-130">A Windows PowerShell drive can make many tasks much simpler.</span></span> <span data-ttu-id="25955-131">Örneğin, Windows kayıt defterindeki en önemli anahtarların bazılarının çok uzun yolları vardır, bu da erişimi daha kolay ve hatırlayacağınızdır.</span><span class="sxs-lookup"><span data-stu-id="25955-131">For example, some of the most important keys in the Windows registry have extremely long paths, making them cumbersome to access and difficult to remember.</span></span> <span data-ttu-id="25955-132">Kritik yapılandırma bilgileri, **HKEY_LOCAL_MACHINE\\Software\\\\Microsoft\\Windows CurrentVersion**altında bulunur.</span><span class="sxs-lookup"><span data-stu-id="25955-132">Critical configuration information resides under **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion**.</span></span> <span data-ttu-id="25955-133">CurrentVersion kayıt defteri anahtarındaki öğeleri görüntülemek ve değiştirmek için, şunu yazarak bu anahtarda kök olan bir Windows PowerShell sürücüsü oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="25955-133">To view and change items in the CurrentVersion registry key, you can create a Windows PowerShell drive that is rooted in that key by typing:</span></span>

```
PS> New-PSDrive -Name cvkey -PSProvider Registry -Root HKLM\Software\Microsoft\Windows\CurrentVersion

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
cvkey      Registry      HKLM\Software\Microsoft\Windows\...
```

<span data-ttu-id="25955-134">Daha sonra konumu diğer tüm sürücüler gibi **cvkey:** Drive olarak değiştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="25955-134">You can then change location to the **cvkey:** drive as you would any other drive:</span></span>

```
PS> cd cvkey:
```

<span data-ttu-id="25955-135">veya:</span><span class="sxs-lookup"><span data-stu-id="25955-135">or:</span></span>

```
PS> Set-Location cvkey: -PassThru

Path
----
cvkey:\
```

<span data-ttu-id="25955-136">New-PsDrive cmdlet 'i, yeni sürücüyü yalnızca geçerli Windows PowerShell oturumuna ekler.</span><span class="sxs-lookup"><span data-stu-id="25955-136">The New-PsDrive cmdlet adds the new drive only to the current Windows PowerShell session.</span></span> <span data-ttu-id="25955-137">Windows PowerShell penceresini kapatırsanız yeni sürücü kaybedilir.</span><span class="sxs-lookup"><span data-stu-id="25955-137">If you close the Windows PowerShell window, the new drive is lost.</span></span> <span data-ttu-id="25955-138">Bir Windows PowerShell sürücüsünü kaydetmek için, geçerli Windows PowerShell oturumunu dışarı aktarmak için Export-Console cmdlet 'ini kullanın ve ardından içeri aktarmak için PowerShell. exe **Psconsolefile** parametresini kullanın.</span><span class="sxs-lookup"><span data-stu-id="25955-138">To save a Windows PowerShell drive, use the Export-Console cmdlet to export the current Windows PowerShell session, and then use the PowerShell.exe **PSConsoleFile** parameter to import it.</span></span> <span data-ttu-id="25955-139">Ya da yeni sürücüyü Windows PowerShell profilinize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="25955-139">Or, add the new drive to your Windows PowerShell profile.</span></span>

## <a name="deleting-windows-powershell-drives-remove-psdrive"></a><span data-ttu-id="25955-140">Windows PowerShell sürücüleri (Remove-PSDrive) siliniyor</span><span class="sxs-lookup"><span data-stu-id="25955-140">Deleting Windows PowerShell Drives (Remove-PSDrive)</span></span>

<span data-ttu-id="25955-141">**Remove-PSDrive** cmdlet 'Ini kullanarak Windows PowerShell 'den sürücüleri silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="25955-141">You can delete drives from Windows PowerShell by using the **Remove-PSDrive** cmdlet.</span></span> <span data-ttu-id="25955-142">**Remove-PSDrive** cmdlet 'i kullanımı kolaydır; belirli bir Windows PowerShell sürücüsünü silmek için Windows PowerShell sürücü adını sağlamanız yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="25955-142">The **Remove-PSDrive** cmdlet is easy to use; to delete a specific Windows PowerShell drive, you just supply the Windows PowerShell drive name.</span></span>

<span data-ttu-id="25955-143">Örneğin, **Office eklediyseniz:** Windows PowerShell sürücüsü, **New-PSDrive** konusunda gösterildiği gibi, şunu yazarak silebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="25955-143">For example, if you added the **Office:** Windows PowerShell drive, as shown in the **New-PSDrive** topic, you can delete it by typing:</span></span>

```powershell
Remove-PSDrive -Name Office
```

<span data-ttu-id="25955-144">**Cvkey** 'yi silmek için: **Yeni-PSDrive** konusunda da gösterilen Windows PowerShell sürücüsü aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="25955-144">To delete the **cvkey:** Windows PowerShell drive, also shown in the **New-PSDrive** topic, use the following command:</span></span>

```powershell
Remove-PSDrive -Name cvkey
```

<span data-ttu-id="25955-145">Bir Windows PowerShell sürücüsünü silmek kolaydır, ancak bu sürücüyü sürücüden siz silemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="25955-145">It's easy to delete a Windows PowerShell drive, but you can't delete it while you are in the drive.</span></span> <span data-ttu-id="25955-146">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="25955-146">For example:</span></span>

```
PS> cd office:
PS Office:\> remove-psdrive -name office
Remove-PSDrive : Cannot remove drive 'Office' because it is in use.
At line:1 char:15
+ remove-psdrive  <<<< -name office
```

## <a name="adding-and-removing-drives-outside-windows-powershell"></a><span data-ttu-id="25955-147">Windows PowerShell dışında sürücü ekleme ve kaldırma</span><span class="sxs-lookup"><span data-stu-id="25955-147">Adding and Removing Drives Outside Windows PowerShell</span></span>

<span data-ttu-id="25955-148">Windows PowerShell, eşlenen ağ sürücüleri, eklenen USB sürücüleri ve **net use** komutu kullanılarak silinen sürücüler de dahil olmak üzere Windows 'da eklenen veya kaldırılan dosya sistemi sürücüleri algılar.Bir Windows komut dosyası sistemi (WSH) betiğinin WScript. NetworkMapNetworkDrive ve **removenetworkdrive** yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="25955-148">Windows PowerShell detects file system drives that are added or removed in Windows, including network drives that are mapped, USB drives that are attached, and drives that are deleted by using either the **net use** command or the **WScript.NetworkMapNetworkDrive** and **RemoveNetworkDrive** methods from a Windows Script Host (WSH) script.</span></span>
