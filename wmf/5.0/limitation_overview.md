---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, Kur
ms.openlocfilehash: e8620cdeb90792e86d091d3e19a169f9dfa690f9
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="known-issues-and-limitations"></a><span data-ttu-id="469ae-102">Bilinen sorunlar ve sınırlamalar</span><span class="sxs-lookup"><span data-stu-id="469ae-102">Known Issues and Limitations</span></span>

<a name="powershell-shortcuts-are-broken-when-used-for-the-first-time"></a><span data-ttu-id="469ae-103">İlk defa kullanıldığında PowerShell kısayolları bozuk</span><span class="sxs-lookup"><span data-stu-id="469ae-103">PowerShell Shortcuts are broken when used for the first time</span></span>
------------------------------------------------------------

<span data-ttu-id="469ae-104">**Çözüm:** aşağıdaki eylemlerden birini gerçekleştirin:</span><span class="sxs-lookup"><span data-stu-id="469ae-104">**Resolution:** Perform one of the following actions:</span></span>

1.  <span data-ttu-id="469ae-105">PowerShell kısayolu sağ tıklatın.</span><span class="sxs-lookup"><span data-stu-id="469ae-105">Right click on the PowerShell shortcut.</span></span> <span data-ttu-id="469ae-106">Yükseltilmiş olmayan modunda başlatmak için "Windows PowerShell" seçin.</span><span class="sxs-lookup"><span data-stu-id="469ae-106">Select “Windows PowerShell” to launch in a non-elevated mode.</span></span>
2.  <span data-ttu-id="469ae-107">PowerShell kısayolu sağ tıklatın.</span><span class="sxs-lookup"><span data-stu-id="469ae-107">Right click on the PowerShell shortcut.</span></span> <span data-ttu-id="469ae-108">"Windows PowerShell üzerinde" sağ tıklatın ve "Yönetici olarak çalıştır yükseltilmiş modda başlatmak için" seçin.</span><span class="sxs-lookup"><span data-stu-id="469ae-108">Right click on “Windows PowerShell” and select “Run As Administrator” to launch in an elevated mode.</span></span>

<span data-ttu-id="469ae-109">Yukarıdaki eylemlerden birini gerçekleştirdikten sonra PowerShell kısayolları çalışır.</span><span class="sxs-lookup"><span data-stu-id="469ae-109">Once you have performed either of the above actions, the PowerShell shortcuts will work.</span></span> <span data-ttu-id="469ae-110">Bu eylem yalnızca bir kez gerçekleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="469ae-110">These actions need to be performed only once.</span></span>


<a name="powershell-modules-and-dsc-resources-report-errors-about-executionpolicy-on-windows-7"></a><span data-ttu-id="469ae-111">PowerShell modülleri ve DSC kaynakları hakkında hata ExecutionPolicy Windows 7</span><span class="sxs-lookup"><span data-stu-id="469ae-111">PowerShell Modules and DSC Resources report errors about ExecutionPolicy on Windows 7</span></span>
-------------------------------------------------------------------------------------
<span data-ttu-id="469ae-112">Windows 7, PowerShell modülleri ve DSC kaynakları kullanımı hakkında ExecutionPolicy bildirilen hataları neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="469ae-112">On Windows 7, the use of PowerShell modules and DSC resources may result in errors reported about ExecutionPolicy.</span></span>

<span data-ttu-id="469ae-113">**Çözüm:** (yönetici olarak çalıştır) yükseltilmiş bir PowerShell oturumunda aşağıdaki komutu çalıştırarak ExecutionPolicy RemoteSigned olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="469ae-113">**Resolution:** Set the ExecutionPolicy to RemoteSigned by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```

<a name="connecting-to-an-old-remote-exchange-endpoint-causes-a-crash"></a><span data-ttu-id="469ae-114">Eski bir uzak Exchange uç noktasına bağlanan bir kilitlenme neden olur.</span><span class="sxs-lookup"><span data-stu-id="469ae-114">Connecting to an old remote Exchange endpoint causes a crash</span></span>
------------------------------------------------------------

<span data-ttu-id="469ae-115">Eski Exchange uç noktası için yeni bir uç noktası yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="469ae-115">The old Exchange endpoint redirects to a new endpoint.</span></span> <span data-ttu-id="469ae-116">Bir hata varsa yeniden yönlendirme mantığında sonucu bir kilitlenme.</span><span class="sxs-lookup"><span data-stu-id="469ae-116">There is a bug in the redirection logic that results in a crash.</span></span>

<span data-ttu-id="469ae-117">**Çözüm:** yeni uç noktası doğrudan bağlanın.</span><span class="sxs-lookup"><span data-stu-id="469ae-117">**Resolution:** Connect directly to the new endpoint.</span></span>


<a name="software-inventory-logging-feature-is-erroneously-stopped-after-wmf-50-installation-on-windows-server-2012-r2"></a><span data-ttu-id="469ae-118">Windows Server 2012 R2 WMF 5.0 yüklemeden sonra yazılım envanter günlüğü özelliği yanlışlıkla durduruldu</span><span class="sxs-lookup"><span data-stu-id="469ae-118">Software Inventory Logging feature is erroneously stopped after WMF 5.0 installation on Windows Server 2012 R2</span></span>
-------------------------------------------------------------------------------------------------------------

<span data-ttu-id="469ae-119">Bir Windows Server 2012 SIL zaten çalışmakta olan R2 üzerinde WMF 5.0 yükleme sırasında yazılım envanter günlüğü özelliği yanlışlıkla yüklendikten sonra durduruldu.</span><span class="sxs-lookup"><span data-stu-id="469ae-119">When installing WMF 5.0 on a Windows Server 2012 R2 that is already running SIL, the Software Inventory Logging feature is erroneously stopped after installation.</span></span>

<span data-ttu-id="469ae-120">**Çözüm:** yükleme işlemini errantly yazılım envanter günlüğü özelliği durduracak şekilde kez WMF yüklendikten sonra Start-SilLogging cmdlet'ini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="469ae-120">**Resolution:** Run the Start-SilLogging cmdlet once after the WMF installation, as the installation process will errantly stop the Software Inventory Logging feature.</span></span>

<a name="get-childitem-does-not-work-if--literalpath-and--recurse-are-used-together"></a><span data-ttu-id="469ae-121">Get-Childıtem - LiteralPath ve - Recurse birlikte kullanılan çalışmaz</span><span class="sxs-lookup"><span data-stu-id="469ae-121">Get-ChildItem does not work if -LiteralPath and -Recurse are used together</span></span>
--------------------------------------------------------------------------

<span data-ttu-id="469ae-122">Ardından bir dizin adı geçersiz joker karakter içeriyorsa, - LiteralPath hem - Recurse birlikte kullanıldığında Get-Childıtem beklenen sonuçları oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="469ae-122">If a directory name contains an invalid wildcard character, then Get-ChildItem will not produce expected results when both -LiteralPath and -Recurse are used together.</span></span>

<span data-ttu-id="469ae-123">**Çözüm:** değil ideal, ancak geçerli geçici bir çözüm değildir yerine özyineleme komut dosyasında uygulamak için cmdlet'ini kullanır.</span><span class="sxs-lookup"><span data-stu-id="469ae-123">**Resolution:** Not ideal, but current workaround is to implement recursion in the script rather than rely on the cmdlet.</span></span>


<a name="sysprep-fails-after-wmf-50-installation"></a><span data-ttu-id="469ae-124">WMF 5.0 yüklendikten sonra Sysprep başarısız</span><span class="sxs-lookup"><span data-stu-id="469ae-124">Sysprep fails after WMF 5.0 installation</span></span>
----------------------------------------

<span data-ttu-id="469ae-125">Çalıştırdığınız Windows Server sürümüne bağlı olarak bu sorunun iki geçici çözüm yoktur.</span><span class="sxs-lookup"><span data-stu-id="469ae-125">There are two workarounds for this issue depending on the version of Windows Server you are running.</span></span>

<span data-ttu-id="469ae-126">**Çözüm:**</span><span class="sxs-lookup"><span data-stu-id="469ae-126">**Resolution:**</span></span>
- <span data-ttu-id="469ae-127">Çalışan sistemler için **Windows Server 2008 R2**</span><span class="sxs-lookup"><span data-stu-id="469ae-127">For systems running **Windows Server 2008 R2**</span></span>
  1. <span data-ttu-id="469ae-128">Yönetici olarak PowerShell'i açın</span><span class="sxs-lookup"><span data-stu-id="469ae-128">Open Powershell as an administrator</span></span>
  2. <span data-ttu-id="469ae-129">Aşağıdaki komutu çalıştırın</span><span class="sxs-lookup"><span data-stu-id="469ae-129">Run the following command</span></span> 
  
  ```powershell
    Set-SilLogging –TargetUri https://BlankTarget –CertificateThumbprint 0123456789
  ```
  3. <span data-ttu-id="469ae-130">Komutunu çalıştırın ve bunlar beklendiği gibi hatayı yok sayıp.</span><span class="sxs-lookup"><span data-stu-id="469ae-130">Run the command and ignore the error, as they are expected.</span></span>
  
  ```powershell
    Publish-SilData
   ```
  4. <span data-ttu-id="469ae-131">\Windows\System32\Logfiles\SIL\ dizindeki dosyaları sil</span><span class="sxs-lookup"><span data-stu-id="469ae-131">Delete the files in  \Windows\System32\Logfiles\SIL\ directory</span></span>
  
  ```powershell
    Remove-Item -Recurse $env:SystemRoot\System32\Logfiles\SIL\
  ```
  5. <span data-ttu-id="469ae-132">Kullanılabilir tüm önemli Windows güncelleştirmeleri yüklemek ve Sysyprep işlemi normalde başlayın.</span><span class="sxs-lookup"><span data-stu-id="469ae-132">Install all available important Windows Updates, and begin Sysyprep operation normally.</span></span>
  
- <span data-ttu-id="469ae-133">Çalışan sistemler için **Windows Server 2012**</span><span class="sxs-lookup"><span data-stu-id="469ae-133">For systems running **Windows Server 2012**</span></span>
  1.    <span data-ttu-id="469ae-134">WMF 5.0 olabilir sunucuya yükledikten sonra Sysprep'd, yönetici olarak oturum açın.</span><span class="sxs-lookup"><span data-stu-id="469ae-134">After installing WMF 5.0 on the server to be Sysprep’d, login as administrator.</span></span>
  2.    <span data-ttu-id="469ae-135">Generize.XML dizin \Windows\System32\Sysprep\ActionFiles\ C:\ Windows dizini dışındaki bir konuma örneğin kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="469ae-135">Copy Generize.xml from directory \Windows\System32\Sysprep\ActionFiles\ to a location outside of the Windows directory, C:\ for example.</span></span>
  3.    <span data-ttu-id="469ae-136">Generalize.xml kopyanızı not defteri ile açın.</span><span class="sxs-lookup"><span data-stu-id="469ae-136">Open your Generalize.xml copy with notepad.</span></span>
  4.    <span data-ttu-id="469ae-137">Bulma ve aşağıdaki metni, silinmesi gerekiyor her bir örneğini kaldırma (belgenin sonuna olacaktır).</span><span class="sxs-lookup"><span data-stu-id="469ae-137">Find and remove the following text, one instance of each needs to be deleted (they will be near the end of the document).</span></span>

    ```
    <sysprepOrder order="0x3200"></sysprepOrder>
    <sysprepOrder order="0x3300"></sysprepOrder>
    ```

  5.    <span data-ttu-id="469ae-138">Generalize.xml düzenlenen kopyasını dosyasını kaydedin ve kapatın.</span><span class="sxs-lookup"><span data-stu-id="469ae-138">Save the edited copy of Generalize.xml and close the file.</span></span>
  6.    <span data-ttu-id="469ae-139">Yönetici olarak bir komut istemi açın</span><span class="sxs-lookup"><span data-stu-id="469ae-139">Open a command prompt as administrator</span></span>
  7.    <span data-ttu-id="469ae-140">System32 klasöründe Generalize.xml dosya sahipliğini almak için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="469ae-140">Run the following command to take ownership of the Generalize.xml file in system32 folder:</span></span>

    ```
    Takeown /f C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml 
    ```

  8.    <span data-ttu-id="469ae-141">Dosyayı uygun izni ayarlamak için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="469ae-141">Run the following command to set appropriate permission on the file:</span></span>

    ```
    Cacls C:\Windows\System32\ Sysprep\ActionFiles\Generalize.xml /G `<AdministratorUserName>`:F 
    ```
      * <span data-ttu-id="469ae-142">Evet komut isteminde onay yanıtı.</span><span class="sxs-lookup"><span data-stu-id="469ae-142">Answer Yes at the prompt for confirmation.</span></span> 
      * <span data-ttu-id="469ae-143">Unutmayın `<AdministratorUserName>` makinedeki yöneticisi olan kullanıcı adı ile değiştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="469ae-143">Note that `<AdministratorUserName>` should be replaced by the username who is administrator on the machine.</span></span> <span data-ttu-id="469ae-144">Örneğin, "Yönetici".</span><span class="sxs-lookup"><span data-stu-id="469ae-144">For example, "Administrator".</span></span>
      
  9.    <span data-ttu-id="469ae-145">Düzenlenen ve üzerinde aşağıdaki komutu kullanarak Sysprep'i dizinine kaydedilir dosyasını kopyalayın:</span><span class="sxs-lookup"><span data-stu-id="469ae-145">Copy the file you edited and saved over to the Sysprep directory using the following command:</span></span>

    ```
    xcopy C:\Generalize.xml C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml 
    ```
      * <span data-ttu-id="469ae-146">(Üzerine yazmak için hiçbir istemi ise girilen yolunu kontrol edin unutmayın) üzerine yazmak için Evet'i yanıtlayın.</span><span class="sxs-lookup"><span data-stu-id="469ae-146">Answer Yes to overwrite (note that if there is no prompt to overwrite, double check the path entered).</span></span>
      * <span data-ttu-id="469ae-147">Düzenlenen Generalize.xml kopyanızı C:\ için kopyalanan varsayar.</span><span class="sxs-lookup"><span data-stu-id="469ae-147">Assumes your edited copy of Generalize.xml was copied to C:\ .</span></span>

  10.   <span data-ttu-id="469ae-148">Generalize.xml geçici çözüm ile güncelleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="469ae-148">Generalize.xml is now updated with the workaround.</span></span> <span data-ttu-id="469ae-149">Lütfen Sysprep etkin generalize seçeneği ile çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="469ae-149">Please run Sysprep with the generalize option enabled.</span></span>

