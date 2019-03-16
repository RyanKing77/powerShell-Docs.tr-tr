---
title: PowerShell modülünü yükleme | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb82827e-fdb7-4cbf-b3d4-093e72b3ff0e
caps.latest.revision: 28
ms.openlocfilehash: 7c2bfca50de4645676eafc01bbf23d9797e8b758
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059788"
---
# <a name="installing-a-powershell-module"></a><span data-ttu-id="4ba0e-102">PowerShell Modülü Yükleme</span><span class="sxs-lookup"><span data-stu-id="4ba0e-102">Installing a PowerShell Module</span></span>

<span data-ttu-id="4ba0e-103">PowerShell modülü oluşturduktan sonra böylece sizin veya başkalarının kullanabilir, büyük olasılıkla bir sistemde modülünü yüklemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-103">After you have created your PowerShell module, you will likely want to install the module on a system, so that you or others may use it.</span></span> <span data-ttu-id="4ba0e-104">Genel olarak bakıldığında, bu yalnızca modül (IE, .psm1 veya ikili bir birleştirme, modül bildirimi ve ilişkili diğer dosyalar) .iso dosyalarını bir dizin o bilgisayardaki kopyalama oluşur.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-104">Generally speaking, this simply consists of copying the module files (ie, the .psm1, or the binary assembly, the module manifest, and any other associated files) onto a directory on that computer.</span></span> <span data-ttu-id="4ba0e-105">Çok küçük bir proje için bu kopyalama ve yapıştırma Windows Gezgini'ni kullanarak dosyaları tek bir uzak bilgisayara olarak basit olabilir. Ancak, daha büyük çözümler için daha karmaşık bir yükleme işlemi kullanmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-105">For a very small project, this may be as simple as copying and pasting the files with Windows Explorer onto a single remote computer; however, for larger solutions you may wish to use a more sophisticated installation process.</span></span> <span data-ttu-id="4ba0e-106">Modülünüzün sisteme nereden bağımsız olarak PowerShell çeşitli bulabilir ve modüllerinizi bilgilendirir teknikler kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-106">Regardless of how you get your module onto the system, PowerShell can use a number of techniques that will let users find and use your modules.</span></span> <span data-ttu-id="4ba0e-107">(Daha fazla bilgi için [PowerShell modülünü içeri aktararak](./importing-a-powershell-module.md).) Bu nedenle, yükleme için ana sorunu PowerShell modülünüzde bulamadı olacağını sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-107">(For more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md).) Therefore, the main issue for installation is ensuring that PowerShell will be able to find your module.</span></span>

<span data-ttu-id="4ba0e-108">Bu konu, aşağıdaki bölümleri içerir:</span><span class="sxs-lookup"><span data-stu-id="4ba0e-108">This topic contains the following sections:</span></span>

- <span data-ttu-id="4ba0e-109">Modülleri yüklemek için kurallar</span><span class="sxs-lookup"><span data-stu-id="4ba0e-109">Rules for Installing Modules</span></span>

- <span data-ttu-id="4ba0e-110">Where modüllerini yüklemek için</span><span class="sxs-lookup"><span data-stu-id="4ba0e-110">Where to Install Modules</span></span>

- <span data-ttu-id="4ba0e-111">Bir modülün birden fazla sürümünü yükleme</span><span class="sxs-lookup"><span data-stu-id="4ba0e-111">Installing Multiple Versions of a Module</span></span>

- <span data-ttu-id="4ba0e-112">İşleme komut adı çakışmaları</span><span class="sxs-lookup"><span data-stu-id="4ba0e-112">Handling Command Name Conflicts</span></span>

## <a name="rules-for-installing-modules"></a><span data-ttu-id="4ba0e-113">Modülleri yüklemek için kurallar</span><span class="sxs-lookup"><span data-stu-id="4ba0e-113">Rules for Installing Modules</span></span>

<span data-ttu-id="4ba0e-114">Aşağıdaki bilgileri kullanın, başka bir taraftan size modülleri ve başkalarına dağıttığınız modüller için oluşturduğunuz modülleri dahil olmak üzere tüm modülleri ile ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-114">The following information pertains to all modules, including modules that you create for your own use, modules that you get from other parties, and modules that you distribute to others.</span></span>

### <a name="install-modules-in-psmodulepath"></a><span data-ttu-id="4ba0e-115">İçinde PSModulePath modülleri yükleme</span><span class="sxs-lookup"><span data-stu-id="4ba0e-115">Install Modules in PSModulePath</span></span>

<span data-ttu-id="4ba0e-116">Mümkün olduğunda, listelenen bir yolda tüm modülleri yükleme **PSModulePath** ortam değişkeni veya modül yola ekleyin **PSModulePath** ortam değişken değeri.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-116">Whenever possible, install all modules in a path that is listed in the **PSModulePath** environment variable or add the module path to the **PSModulePath** environment variable value.</span></span>

<span data-ttu-id="4ba0e-117">**PSModulePath** ortam değişkeni ($Env: PSModulePath) Windows PowerShell modülleri konumları içerir.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-117">The **PSModulePath** environment variable ($Env:PSModulePath) contains the locations of Windows PowerShell modules.</span></span> <span data-ttu-id="4ba0e-118">Cmdlet modülleri bulmak için bu ortam değişkeninin değeri kullanır.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-118">Cmdlets rely on the value of this environment variable to find modules.</span></span>

<span data-ttu-id="4ba0e-119">Varsayılan olarak, **PSModulePath** ortam değişken değerini, aşağıdaki sistem ve kullanıcı modülü dizini içeriyor, ancak ekleyin ve değerini düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-119">By default, the **PSModulePath** environment variable value contains the following system and user module directories, but you can add to and edit the value.</span></span>

- <span data-ttu-id="4ba0e-120">$PSHome\Modules (%Windir%\System32\WindowsPowerShell\v1.0\Modules)</span><span class="sxs-lookup"><span data-stu-id="4ba0e-120">$PSHome\Modules (%Windir%\System32\WindowsPowerShell\v1.0\Modules)</span></span>

  > [!WARNING]
  > <span data-ttu-id="4ba0e-121">Bu konum, Windows ile birlikte gelen modüller için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-121">This location is reserved for modules that ship with Windows.</span></span> <span data-ttu-id="4ba0e-122">Modüller, bu konuma yüklemeyin.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-122">Do not install modules to this location.</span></span>

- <span data-ttu-id="4ba0e-123">$Home\Documents\WindowsPowerShell\Modules (%UserProfile%\Documents\WindowsPowerShell\Modules)</span><span class="sxs-lookup"><span data-stu-id="4ba0e-123">$Home\Documents\WindowsPowerShell\Modules (%UserProfile%\Documents\WindowsPowerShell\Modules)</span></span>

- <span data-ttu-id="4ba0e-124">$Env:ProgramFiles\WindowsPowerShell\Modules (%ProgramFiles%\WindowsPowerShell\Modules)</span><span class="sxs-lookup"><span data-stu-id="4ba0e-124">$Env:ProgramFiles\WindowsPowerShell\Modules (%ProgramFiles%\WindowsPowerShell\Modules)</span></span>

  <span data-ttu-id="4ba0e-125">Değeri alınacak **PSModulePath** ortam değişkeni, aşağıdaki komutlardan birini kullanın.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-125">To get the value of the **PSModulePath** environment variable, use either of the following commands.</span></span>

  ```powershell
  $Env:PSModulePath
  [Environment]::GetEnvironmentVariable("PSModulePath")
  ```

  <span data-ttu-id="4ba0e-126">Modül yolu değerine eklenecek **PSModulePath** ortam değişkeni değeri, komutu aşağıdaki biçimi kullanın.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-126">To add a module path to value of the **PSModulePath** environment variable value, use the following command format.</span></span> <span data-ttu-id="4ba0e-127">Bu biçimi kullanan **SetEnvironmentVariable** yöntemi **System.Environment** oturumu bağımsız değişiklik için sınıf **PSModulePath** ortamı değişken.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-127">This format uses the **SetEnvironmentVariable** method of the **System.Environment** class to make a session-independent change to the **PSModulePath** environment variable.</span></span>

  ```powershell

  #Save the current value in the $p variable.
  $p = [Environment]::GetEnvironmentVariable("PSModulePath")

  #Add the new path to the $p variable. Begin with a semi-colon separator.
  $p += ";C:\Program Files (x86)\MyCompany\Modules\"

  #Add the paths in $p to the PSModulePath value.
  [Environment]::SetEnvironmentVariable("PSModulePath",$p)

  ```

  > [!IMPORTANT]
  > <span data-ttu-id="4ba0e-128">Yolu ekledikten sonra **PSModulePath**, değişikliği hakkında bir ortam iletisi yayın.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-128">Once you have added the path to **PSModulePath**, you should broadcast an environment message about the change.</span></span> <span data-ttu-id="4ba0e-129">Değişiklik yayın değişiklikleri alması diğer uygulamaları gibi Kabuk sağlar.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-129">Broadcasting the change allows other applications, such as the shell, to pick up the change.</span></span> <span data-ttu-id="4ba0e-130">Değişiklik yayınlamak için ürün yükleme kodunuzu göndermek sahip bir **WM_SETTINGCHANGE** ile ileti `lParam` "Ortam" dizeye ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-130">To broadcast the change, have your product installation code send a **WM_SETTINGCHANGE** message with `lParam` set to the string "Environment".</span></span> <span data-ttu-id="4ba0e-131">Modül yükleme kodunuzu güncelleştirdi sonra iletiyi göndermeyi unutmayın **PSModulePath**.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-131">Be sure to send the message after your module installation code has updated **PSModulePath**.</span></span>

### <a name="use-the-correct-module-directory-name"></a><span data-ttu-id="4ba0e-132">Doğru modül dizin adı kullanın</span><span class="sxs-lookup"><span data-stu-id="4ba0e-132">Use the Correct Module Directory Name</span></span>

<span data-ttu-id="4ba0e-133">"İyi biçimlendirilmiş" modülü temel modül dizinde en az bir dosya adı ile aynı ada sahip bir dizini içinde depolanan bir modüldür.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-133">A "well-formed" module is a module that is stored in a directory that has the same name as the base name of at least one file in the module directory.</span></span> <span data-ttu-id="4ba0e-134">Bir modül doğru biçimlendirilmemiş, Windows PowerShell, bir modül olarak algılamaz.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-134">If a module is not well-formed, Windows PowerShell does not recognize it as a module.</span></span>

<span data-ttu-id="4ba0e-135">"Temel"dosyasının adı, dosya adı uzantısı olmadan adıdır.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-135">The "base name" of a file is the name without the file name extension.</span></span> <span data-ttu-id="4ba0e-136">İyi biçimlendirilmiş bir modülde modülü dosyalarını içeren dizin adını temel modülünde en az bir dosya adı eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-136">In a well-formed module, the name of the directory that contains the module files must match the base name of at least one file in the module.</span></span>

<span data-ttu-id="4ba0e-137">Örneğin, örnek Fabrikam modülü, modül dosyaları içeren dizine "Fabrikam" olarak adlandırılır ve en az bir dosya "Fabrikam" temel adına sahip.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-137">For example, in the sample Fabrikam module, the directory that contains the module files is named "Fabrikam" and at least one file has the "Fabrikam" base name.</span></span> <span data-ttu-id="4ba0e-138">Bu durumda, Fabrikam.psd1 hem Fabrikam.dll "Fabrikam" temel adına sahip.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-138">In this case, both Fabrikam.psd1 and Fabrikam.dll have the "Fabrikam" base name.</span></span>

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

### <a name="effect-of-incorrect-installation"></a><span data-ttu-id="4ba0e-139">Yanlış yükleme etkisi</span><span class="sxs-lookup"><span data-stu-id="4ba0e-139">Effect of Incorrect Installation</span></span>

<span data-ttu-id="4ba0e-140">Modül doğru biçimlendirilmemiş ve konumuna değerinde bulunmayan **PSModulePath** ortam değişkeni, Windows PowerShell temel bulma özelliklerini aşağıdaki gibi çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-140">If the module is not well-formed and its location is not included in the value of the **PSModulePath** environment variable, basic discovery features of Windows PowerShell, such as the following, do not work.</span></span>

- <span data-ttu-id="4ba0e-141">Modül Otomatik Yükleme özelliğini otomatik olarak modül içeri aktarılamıyor.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-141">The Module Auto-Loading feature cannot import the module automatically.</span></span>

- <span data-ttu-id="4ba0e-142">`ListAvailable` Parametresinin [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet modülü bulunamıyor.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-142">The `ListAvailable` parameter of the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet cannot find the module.</span></span>

- <span data-ttu-id="4ba0e-143">[Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet modülü bulunamıyor.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-143">The [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet cannot find the module.</span></span> <span data-ttu-id="4ba0e-144">Modülü içeri aktarmak için kök modül dosyası veya modül bildirim dosyası tam yolunu belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-144">To import the module, you must provide the full path to the root module file or module manifest file.</span></span>

  <span data-ttu-id="4ba0e-145">Aşağıdaki gibi ek özellikler modülün oturuma aktarılır sürece çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-145">Additional features, such as the following, do not work unless the module is imported into the session.</span></span> <span data-ttu-id="4ba0e-146">İyi biçimlendirilmiş modüllerde **PSModulePath** ortam değişkeni, bu özellikler çalışır olduğunda bile modülün oturuma aktarılmaz.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-146">In well-formed modules in the **PSModulePath** environment variable, these features work even when the module is not imported into the session.</span></span>

- <span data-ttu-id="4ba0e-147">[Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet modülünde komutları bulamıyor.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-147">The [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet cannot find commands in the module.</span></span>

- <span data-ttu-id="4ba0e-148">[Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) ve [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlet'leri güncelleştirilemiyor veya modül için Yardım kaydedin.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-148">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets cannot update or save help for the module.</span></span>

- <span data-ttu-id="4ba0e-149">[Show komutunu](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) cmdlet'i bulun ve modüldeki komutlar görüntüler.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-149">The [Show-Command](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) cmdlet cannot find and display the commands in the module.</span></span>

  <span data-ttu-id="4ba0e-150">Modüldeki komutlar eksik `Show-Command` penceresi içinde Windows PowerShell Tümleşik komut dosyası ortamı (ISE).</span><span class="sxs-lookup"><span data-stu-id="4ba0e-150">The commands in the module are missing from the `Show-Command` window in Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

## <a name="where-to-install-modules"></a><span data-ttu-id="4ba0e-151">Where modüllerini yüklemek için</span><span class="sxs-lookup"><span data-stu-id="4ba0e-151">Where to Install Modules</span></span>

<span data-ttu-id="4ba0e-152">Bu bölümde, Windows PowerShell modüllerini yüklemek için dosya sistemindeki nerede açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-152">This section explains where in the file system to install Windows PowerShell modules.</span></span> <span data-ttu-id="4ba0e-153">Konumun modülü nasıl kullanıldığına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-153">The location depends on how the module is used.</span></span>

### <a name="installing-modules-for-a-specific-user"></a><span data-ttu-id="4ba0e-154">Belirli bir kullanıcı için modülleri yükleme</span><span class="sxs-lookup"><span data-stu-id="4ba0e-154">Installing Modules for a Specific User</span></span>

<span data-ttu-id="4ba0e-155">Kendi modülünüzü oluşturmak veya bir Windows PowerShell topluluğu Web sitesi gibi başka bir tarafın bir modülü Al ve modül yalnızca, kullanıcı hesabınız için kullanılabilir olmasını istiyorsanız kullanıcıya özgü modüller dizininizde modülünü yükleyin.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-155">If you create your own module or get a module from another party, such as a Windows PowerShell community website, and you want the module to be available for your user account only, install the module in your user-specific Modules directory.</span></span>

```
$home\Documents\WindowsPowerShell\Modules\<Module Folder>\<Module Files>
```

<span data-ttu-id="4ba0e-156">Kullanıcıya özgü modüller dizin değerine eklenir **PSModulePath** varsayılan ortam değişkeni.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-156">The user-specific Modules directory is added to the value of the **PSModulePath** environment variable by default.</span></span>

### <a name="installing-modules-for-all-users-in-program-files"></a><span data-ttu-id="4ba0e-157">Modüller için tüm kullanıcıların Program dosyaları yükleme</span><span class="sxs-lookup"><span data-stu-id="4ba0e-157">Installing Modules for all Users in Program Files</span></span>

<span data-ttu-id="4ba0e-158">Bir modül bilgisayardaki kullanıcı hesaplarının tümünü kullanılabilir olmasını istiyorsanız, modül Program Files konumunda yükleyin.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-158">If you want a module to be available to all user accounts on the computer, install the module in the Program Files location.</span></span>

```
$Env:ProgramFiles\WindowsPowerShell\Modules\<Module Folder>\<Module Files>
```

> [!NOTE]
> <span data-ttu-id="4ba0e-159">Program dosyalarının konumu PSModulePath ortam değişkeninin değeri için Windows PowerShell 4.0 ve sonraki sürümlerinde varsayılan olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-159">The Program Files location is added to the value of the PSModulePath environment variable by default in Windows PowerShell 4.0 and later.</span></span> <span data-ttu-id="4ba0e-160">Windows PowerShell'in önceki sürümleri için el ile Program dosyalarının konumu ((%ProgramFiles%\WindowsPowerShell\Modules) oluşturabilir ve yukarıda açıklandığı gibi bu yolu PSModulePath ortam değişkeninize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-160">For earlier versions of Windows PowerShell, you can manually create the Program Files location ((%ProgramFiles%\WindowsPowerShell\Modules) and add this path to your PSModulePath environment variable as described above.</span></span>

### <a name="installing-modules-in-a-product-directory"></a><span data-ttu-id="4ba0e-161">Bir ürün dizinde modülleri yükleme</span><span class="sxs-lookup"><span data-stu-id="4ba0e-161">Installing Modules in a Product Directory</span></span>

<span data-ttu-id="4ba0e-162">Modülü diğer taraflara dağıtıyorsanız, yukarıda açıklanan varsayılan Program dosyalarının konumu kullanın veya kendi şirketinize özgü veya ürüne özgü alt % ProgramFiles % dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-162">If you are distributing the module to other parties, use the default Program Files location described above, or create your own company-specific or product-specific subdirectory of the %ProgramFiles% directory.</span></span>

<span data-ttu-id="4ba0e-163">Örneğin, Fabrikam teknolojileri, kurgusal bir şirkette Fabrikam Manager ürün için bir Windows PowerShell modülünü sunulmamaktadır.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-163">For example, Fabrikam Technologies, a fictitious company, is shipping a Windows PowerShell module for their Fabrikam Manager product.</span></span> <span data-ttu-id="4ba0e-164">Kendi Modülü Yükleyicisi modülleri alt Fabrikam Manager ürün alt dizinde oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-164">Their module installer creates a Modules subdirectory in the Fabrikam Manager product subdirectory.</span></span>

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

<span data-ttu-id="4ba0e-165">Fabrikam Modülü Yükleyicisi Fabrikam modülü bulmak Windows PowerShell modülü bulma özellikleri etkinleştirmek için değeri olarak modül konumu ekler **PSModulePath** ortam değişkeni.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-165">To enable the Windows PowerShell module discovery features to find the Fabrikam module, the Fabrikam module installer adds the module location to the value of the **PSModulePath** environment variable.</span></span>

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += "C:\Program Files\Fabrikam Technologies\Fabrikam Manager\Modules\"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

### <a name="installing-modules-in-the-common-files-directory"></a><span data-ttu-id="4ba0e-166">Common Files dizininde modülleri yükleme</span><span class="sxs-lookup"><span data-stu-id="4ba0e-166">Installing Modules in the Common Files Directory</span></span>

<span data-ttu-id="4ba0e-167">Bir modülün birden fazla ürün sürümünü veya bir ürünün birden çok bileşen tarafından kullanılır, modül bir %ProgramFiles%\Common Files\Modules alt modülü özgü alt dizinde yükleyin.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-167">If a module is used by multiple components of a product or by multiple versions of a product, install the module in a module-specific subdirectory of the %ProgramFiles%\Common Files\Modules subdirectory.</span></span>

<span data-ttu-id="4ba0e-168">Aşağıdaki örnekte, Fabrikam modülü %ProgramFiles%\Common Files\Modules alt Fabrikam alt dizininde yüklenir.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-168">In the following example, the Fabrikam module is installed in a Fabrikam subdirectory of the %ProgramFiles%\Common Files\Modules subdirectory.</span></span> <span data-ttu-id="4ba0e-169">Her bir modülü kendi alt modülleri alt bulunduğu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-169">Note that each module resides in its own subdirectory in the Modules subdirectory.</span></span>

```
C:\Program Files
  Common Files
    Modules
      Fabrikam
        Fabrikam.psd1 (module manifest)
        Fabrikam.dll (module assembly)

```

<span data-ttu-id="4ba0e-170">Ardından, yükleyici değerini garantiler **PSModulePath** ortam değişkeni ortak dosyaları modülleri alt dizini yolunu içerir.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-170">Then, the installer assures the value of the **PSModulePath** environment variable includes the path of the common files modules subdirectory.</span></span>

```powershell
$m = $env:ProgramFiles + '\Common Files\Modules'
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$q = $p -split ';'
if ($q -notContains $m) {
    $q += ";$m"
}
$p = $q -join ';'
[Environment]::SetEnvironmentVariable("PSModulePath", $p)
```

## <a name="installing-multiple-versions-of-a-module"></a><span data-ttu-id="4ba0e-171">Bir modülün birden fazla sürümünü yükleme</span><span class="sxs-lookup"><span data-stu-id="4ba0e-171">Installing Multiple Versions of a Module</span></span>

<span data-ttu-id="4ba0e-172">Birden çok sürümünü aynı modülü yüklemek için aşağıdaki yordamı kullanın.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-172">To install multiple versions of the same module, use the following procedure.</span></span>

1. <span data-ttu-id="4ba0e-173">Her modülü sürümü için bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-173">Create a directory for each version of the module.</span></span> <span data-ttu-id="4ba0e-174">Sürüm numarası, dizin adı içerir.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-174">Include the version number in the directory name.</span></span>

2. <span data-ttu-id="4ba0e-175">Bir modül bildirimi her modülü sürümü için oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-175">Create a module manifest for each version of the module.</span></span> <span data-ttu-id="4ba0e-176">Bulunan değerin **ModuleVersion** anahtar bildirimde, modülü sürüm numarası girin.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-176">In the value of the **ModuleVersion** key in the manifest, enter the module version number.</span></span> <span data-ttu-id="4ba0e-177">Bildirim dosyası (.psd1) modülü için sürüme özgü dizine kaydedin.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-177">Save the manifest file (.psd1) in the version-specific directory for the module.</span></span>

3. <span data-ttu-id="4ba0e-178">Modül kök klasör yolu değeri olarak Ekle **PSModulePath** ortam değişkeni, aşağıdaki örneklerde gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-178">Add the module root folder path to the value of the **PSModulePath** environment variable, as shown in the following examples.</span></span>

<span data-ttu-id="4ba0e-179">Son kullanıcı modülün belirli bir sürümünü almak için kullanabileceğiniz `MinimumVersion` veya `RequiredVersion` parametrelerinin [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-179">To import a particular version of the module, the end-user can use the `MinimumVersion` or `RequiredVersion` parameters of the [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span></span>

<span data-ttu-id="4ba0e-180">Örneğin, Fabrikam modülü 8.0 ve 9.0 sürümlerine ait yapılmıştı, Fabrikam modülü dizin yapısı aşağıdaki gibi olabilir.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-180">For example, if the Fabrikam module is available in versions 8.0 and 9.0, the Fabrikam module directory structure might resemble the following.</span></span>

 ```
C:\Program Files
Fabrikam Manager
  Fabrikam8
    Fabrikam
      Fabrikam.psd1 (module manifest: ModuleVersion = "8.0")
      Fabrikam.dll (module assembly)
  Fabrikam9
    Fabrikam
      Fabrikam.psd1 (module manifest: ModuleVersion = "9.0")
      Fabrikam.dll (module assembly)
```

<span data-ttu-id="4ba0e-181">Modül yolları her ikisi de yükleyici ekler **PSModulePath** ortam değişken değeri.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-181">The installer adds both of the module paths to the **PSModulePath** environment variable value.</span></span>

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam\Fabrikam8;C:\Program Files\Fabrikam\Fabrikam9"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

<span data-ttu-id="4ba0e-182">Bu adımlar tamamlandığında **ListAvailable** parametresinin [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet'i Fabrikam modüllerin her ikisi de alır.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-182">When these steps are complete, the **ListAvailable** parameter of the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet gets both of the Fabrikam modules.</span></span> <span data-ttu-id="4ba0e-183">Belirli bir modülü içeri aktarmak için kullanın `MinimumVersion` veya `RequiredVersion` parametrelerinin [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-183">To import a particular module, use the `MinimumVersion` or `RequiredVersion` parameters of the [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span></span>

<span data-ttu-id="4ba0e-184">Aynı oturuma iki modülü de içeri aktarılır ve modüller aynı ada sahip cmdlet'leri içerir, en son alınan cmdlet'lerin oturumunda etkili olur.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-184">If both modules are imported into the same session, and the modules contain cmdlets with the same names, the cmdlets that are imported last are effective in the session.</span></span>

## <a name="handling-command-name-conflicts"></a><span data-ttu-id="4ba0e-185">İşleme komut adı çakışmaları</span><span class="sxs-lookup"><span data-stu-id="4ba0e-185">Handling Command Name Conflicts</span></span>

<span data-ttu-id="4ba0e-186">Bir modül aktarır komutları kullanıcı oturumunda komutları ile aynı ada sahip komut adı çakışmaları oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-186">Command name conflicts can occur when the commands that a module exports have the same name as commands in the user's session.</span></span>

<span data-ttu-id="4ba0e-187">Bir oturum ile aynı ada sahip iki komut içerdiğinde, Windows PowerShell önceliklidir komut türü çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-187">When a session contains two commands that have the same name, Windows PowerShell runs the command type that takes precedence.</span></span> <span data-ttu-id="4ba0e-188">Bir oturumu aynı ada ve aynı türe sahip iki komut içerdiğinde, Windows PowerShell oturuma son eklenen komut çalışır.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-188">When a session contains two commands that have the same name and the same type, Windows PowerShell runs the command that was added to the session most recently.</span></span> <span data-ttu-id="4ba0e-189">Varsayılan olarak çalıştırılmaz bir komutu çalıştırmak için kullanıcılar, modül adı ile komut adı kazanabilir.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-189">To run a command that is not run by default, users can qualify the command name with the module name.</span></span>

<span data-ttu-id="4ba0e-190">Oturum içeriyorsa, örneğin, bir `Get-Date` işlevi ve `Get-Date` cmdlet'i, Windows PowerShell işlev varsayılan olarak çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-190">For example, if the session contains a `Get-Date` function and the `Get-Date` cmdlet, Windows PowerShell runs the function by default.</span></span> <span data-ttu-id="4ba0e-191">Cmdlet'i çalıştırmak için komutu modül adı ile gibi yazın:</span><span class="sxs-lookup"><span data-stu-id="4ba0e-191">To run the cmdlet, preface the command with the module name, such as:</span></span>

```powershell
Microsoft.PowerShell.Utility\Get-Date
```

<span data-ttu-id="4ba0e-192">Modül yazarları ad çakışmalarını önlemek için kullanabilirsiniz **DefaultCommandPrefix** tüm komutlar için bir isim öneki belirtmek için modül bildirimindeki anahtar modülünden dışarı aktarılan.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-192">To prevent name conflicts, module authors can use the **DefaultCommandPrefix** key in the module manifest to specify a noun prefix for all commands exported from the module.</span></span>

<span data-ttu-id="4ba0e-193">Kullanıcılar **önek** parametresinin `Import-Module` cmdlet'ini alternatif bir önek kullanın.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-193">Users can use the **Prefix** parameter of the `Import-Module` cmdlet to use an alternate prefix.</span></span> <span data-ttu-id="4ba0e-194">Değerini **önek** parametre değerini göre önceliklidir **DefaultCommandPrefix** anahtarı.</span><span class="sxs-lookup"><span data-stu-id="4ba0e-194">The value of the **Prefix** parameter takes precedence over the value of the **DefaultCommandPrefix** key.</span></span>

## <a name="see-also"></a><span data-ttu-id="4ba0e-195">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="4ba0e-195">See Also</span></span>

[<span data-ttu-id="4ba0e-196">about_Command_Precedence</span><span class="sxs-lookup"><span data-stu-id="4ba0e-196">about_Command_Precedence</span></span>](/powershell/module/microsoft.powershell.core/about/about_command_precedence)

[<span data-ttu-id="4ba0e-197">Bir Windows PowerShell modülü yazma</span><span class="sxs-lookup"><span data-stu-id="4ba0e-197">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
