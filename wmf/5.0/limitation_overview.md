---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 4eb2f0bac4f2169a9a06d80cb4fa214a09cdfa86
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892993"
---
# <a name="known-issues-and-limitations"></a><span data-ttu-id="63359-102">Bilinen Sorunlar ve Sınırlamalar</span><span class="sxs-lookup"><span data-stu-id="63359-102">Known Issues and Limitations</span></span>

## <a name="powershell-shortcuts-are-broken-when-used-for-the-first-time"></a><span data-ttu-id="63359-103">İlk kez kullanıldığında PowerShell kısayolları bozuk</span><span class="sxs-lookup"><span data-stu-id="63359-103">PowerShell Shortcuts are broken when used for the first time</span></span>

<span data-ttu-id="63359-104">**Çözüm:** aşağıdaki eylemlerden birini gerçekleştirin:</span><span class="sxs-lookup"><span data-stu-id="63359-104">**Resolution:** Perform one of the following actions:</span></span>

1. <span data-ttu-id="63359-105">Sağ PowerShell kısayolunun tıklayın.</span><span class="sxs-lookup"><span data-stu-id="63359-105">Right click on the PowerShell shortcut.</span></span> <span data-ttu-id="63359-106">Yükseltilmiş olmayan modunda başlatmak için "Windows PowerShell" seçin.</span><span class="sxs-lookup"><span data-stu-id="63359-106">Select “Windows PowerShell” to launch in a non-elevated mode.</span></span>
2. <span data-ttu-id="63359-107">Sağ PowerShell kısayolunun tıklayın.</span><span class="sxs-lookup"><span data-stu-id="63359-107">Right click on the PowerShell shortcut.</span></span> <span data-ttu-id="63359-108">"Windows PowerShell üzerinde" sağ tıklayıp "Yönetici olarak çalıştır bir yükseltilmiş modda başlatmak için" seçin.</span><span class="sxs-lookup"><span data-stu-id="63359-108">Right click on “Windows PowerShell” and select “Run As Administrator” to launch in an elevated mode.</span></span>

<span data-ttu-id="63359-109">Yukarıdaki işlemleri gerçekleştirdikten sonra PowerShell kısayolları çalışır.</span><span class="sxs-lookup"><span data-stu-id="63359-109">Once you have performed either of the above actions, the PowerShell shortcuts will work.</span></span> <span data-ttu-id="63359-110">Bu Eylemler, yalnızca bir kez gerçekleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="63359-110">These actions need to be performed only once.</span></span>

## <a name="powershell-modules-and-dsc-resources-report-errors-about-executionpolicy-on-windows-7"></a><span data-ttu-id="63359-111">PowerShell modülleri ve DSC kaynakları hataları hakkında ExecutionPolicy Windows 7'de raporlar.</span><span class="sxs-lookup"><span data-stu-id="63359-111">PowerShell Modules and DSC Resources report errors about ExecutionPolicy on Windows 7</span></span>

<span data-ttu-id="63359-112">Windows 7'de PowerShell modülleri ve DSC kaynakları ExecutionPolicy hakkında rapor edilen hata neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="63359-112">On Windows 7, the use of PowerShell modules and DSC resources may result in errors reported about ExecutionPolicy.</span></span>

<span data-ttu-id="63359-113">**Çözüm:** (yönetici olarak çalıştır) yükseltilmiş bir PowerShell oturumunda aşağıdaki komutu çalıştırarak ExecutionPolicy RemoteSigned olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="63359-113">**Resolution:** Set the ExecutionPolicy to RemoteSigned by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```

## <a name="connecting-to-an-old-remote-exchange-endpoint-causes-a-crash"></a><span data-ttu-id="63359-114">Kilitlenmeye neden olan eski bir uzak Exchange uç noktasına bağlanma</span><span class="sxs-lookup"><span data-stu-id="63359-114">Connecting to an old remote Exchange endpoint causes a crash</span></span>

<span data-ttu-id="63359-115">Eski değişimi uç noktası, yeni bir uç noktasına yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="63359-115">The old Exchange endpoint redirects to a new endpoint.</span></span> <span data-ttu-id="63359-116">Bir hata olduğunu yeniden yönlendirme mantığının bu sonuçları içindeki bir kilitlenme.</span><span class="sxs-lookup"><span data-stu-id="63359-116">There is a bug in the redirection logic that results in a crash.</span></span>

<span data-ttu-id="63359-117">**Çözüm:** yeni uç nokta doğrudan bağlanın.</span><span class="sxs-lookup"><span data-stu-id="63359-117">**Resolution:** Connect directly to the new endpoint.</span></span>

## <a name="software-inventory-logging-feature-is-erroneously-stopped-after-wmf-50-installation-on-windows-server-2012-r2"></a><span data-ttu-id="63359-118">Windows Server 2012 R2'de WMF 5.0 yüklemeden sonra yazılım envanter günlüğü özelliği deneyebileceğinizi durduruldu</span><span class="sxs-lookup"><span data-stu-id="63359-118">Software Inventory Logging feature is erroneously stopped after WMF 5.0 installation on Windows Server 2012 R2</span></span>

<span data-ttu-id="63359-119">WMF 5.0 bir Windows Server 2012 önceden SIL çalıştıran R2 üzerinde yükleme sırasında yazılım envanter günlüğü özelliği deneyebileceğinizi yüklemeden sonra durdurulur.</span><span class="sxs-lookup"><span data-stu-id="63359-119">When installing WMF 5.0 on a Windows Server 2012 R2 that is already running SIL, the Software Inventory Logging feature is erroneously stopped after installation.</span></span>

<span data-ttu-id="63359-120">**Çözüm:** yükleme işlemi, yazılım envanter günlüğü özelliği errantly durduracak şekilde kez WMF yükleme işleminden sonra Start-SilLogging cmdlet'ini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="63359-120">**Resolution:** Run the Start-SilLogging cmdlet once after the WMF installation, as the installation process will errantly stop the Software Inventory Logging feature.</span></span>

## <a name="get-childitem-does-not-work-if--literalpath-and--recurse-are-used-together"></a><span data-ttu-id="63359-121">`Get-ChildItem` -LiteralPath ve - Recurse birlikte kullanılması durumunda çalışmıyor</span><span class="sxs-lookup"><span data-stu-id="63359-121">`Get-ChildItem` does not work if -LiteralPath and -Recurse are used together</span></span>

<span data-ttu-id="63359-122">Bir dizin adı bir geçersiz joker karakter içeriyorsa `Get-ChildItem` - LiteralPath hem - Recurse birlikte kullanıldığında beklenen sonuçları oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="63359-122">If a directory name contains an invalid wildcard character, then `Get-ChildItem` will not produce expected results when both -LiteralPath and -Recurse are used together.</span></span>

<span data-ttu-id="63359-123">**Çözüm:** ideal değildir, ancak geçerli bir geçici çözüm etmektir özyineleme betikte uygulamak yerine cmdlet'ini kullanır.</span><span class="sxs-lookup"><span data-stu-id="63359-123">**Resolution:** Not ideal, but current workaround is to implement recursion in the script rather than rely on the cmdlet.</span></span>

## <a name="sysprep-fails-after-wmf-50-installation"></a><span data-ttu-id="63359-124">WMF 5.0 yüklemeden sonra Sysprep başarısız</span><span class="sxs-lookup"><span data-stu-id="63359-124">Sysprep fails after WMF 5.0 installation</span></span>

<span data-ttu-id="63359-125">Çalıştırmakta olduğunuz Windows Server sürümüne bağlı olarak bu sorunun iki geçici çözüm yoktur.</span><span class="sxs-lookup"><span data-stu-id="63359-125">There are two workarounds for this issue depending on the version of Windows Server you are running.</span></span>

<span data-ttu-id="63359-126">**Çözüm:**</span><span class="sxs-lookup"><span data-stu-id="63359-126">**Resolution:**</span></span>

- <span data-ttu-id="63359-127">Çalışan sistemler için **Windows Server 2008 R2**</span><span class="sxs-lookup"><span data-stu-id="63359-127">For systems running **Windows Server 2008 R2**</span></span>
  1. <span data-ttu-id="63359-128">Yönetici olarak PowerShell'i açın</span><span class="sxs-lookup"><span data-stu-id="63359-128">Open Powershell as an administrator</span></span>
  2. <span data-ttu-id="63359-129">Aşağıdaki komutu çalıştırın</span><span class="sxs-lookup"><span data-stu-id="63359-129">Run the following command</span></span>

     ```powershell
     Set-SilLogging –TargetUri https://BlankTarget –CertificateThumbprint 0123456789
     ```

  3. <span data-ttu-id="63359-130">Komutunu çalıştırın ve bunlar beklendiği gibi hatayı yoksayın.</span><span class="sxs-lookup"><span data-stu-id="63359-130">Run the command and ignore the error, as they are expected.</span></span>

     ```powershell
     Publish-SilData
     ```

  4. <span data-ttu-id="63359-131">\Windows\System32\Logfiles\SIL\ dizindeki dosyaları sil</span><span class="sxs-lookup"><span data-stu-id="63359-131">Delete the files in  \Windows\System32\Logfiles\SIL\ directory</span></span>

     ```powershell
     Remove-Item -Recurse $env:SystemRoot\System32\Logfiles\SIL\
     ```

  5. <span data-ttu-id="63359-132">Tüm kullanılabilir önemli Windows güncelleştirmelerini yükleyin ve normalde Sysyprep işlemi başlar.</span><span class="sxs-lookup"><span data-stu-id="63359-132">Install all available important Windows Updates, and begin Sysyprep operation normally.</span></span>

- <span data-ttu-id="63359-133">Çalışan sistemler için **Windows Server 2012**</span><span class="sxs-lookup"><span data-stu-id="63359-133">For systems running **Windows Server 2012**</span></span>
  1. <span data-ttu-id="63359-134">WMF 5.0 olması için sunucuda yükledikten sonra Sysprep'd, yönetici olarak oturum açın.</span><span class="sxs-lookup"><span data-stu-id="63359-134">After installing WMF 5.0 on the server to be Sysprep’d, login as administrator.</span></span>
  2. <span data-ttu-id="63359-135">Generize.XML dizin \Windows\System32\Sysprep\ActionFiles\ C:\ Windows dizini dışındaki bir konuma örneğin kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="63359-135">Copy Generize.xml from directory \Windows\System32\Sysprep\ActionFiles\ to a location outside of the Windows directory, C:\ for example.</span></span>
  3. <span data-ttu-id="63359-136">Generalize.xml kopyanızı notepad ile açın.</span><span class="sxs-lookup"><span data-stu-id="63359-136">Open your Generalize.xml copy with notepad.</span></span>
  4. <span data-ttu-id="63359-137">Bulma ve aşağıdaki metni, silinmesi gerekiyor her bir örneğini kaldırma (belgenin sonuna olacaktır).</span><span class="sxs-lookup"><span data-stu-id="63359-137">Find and remove the following text, one instance of each needs to be deleted (they will be near the end of the document).</span></span>

     ```xml
     <sysprepOrder order="0x3200"></sysprepOrder>
     <sysprepOrder order="0x3300"></sysprepOrder>
     ```

  5. <span data-ttu-id="63359-138">Düzenlenen Generalize.xml kopyasını kaydedin ve dosyayı kapatın.</span><span class="sxs-lookup"><span data-stu-id="63359-138">Save the edited copy of Generalize.xml and close the file.</span></span>
  6. <span data-ttu-id="63359-139">Yönetici olarak bir komut istemi açın</span><span class="sxs-lookup"><span data-stu-id="63359-139">Open a command prompt as administrator</span></span>
  7. <span data-ttu-id="63359-140">System32 klasöründe Generalize.xml dosyanın sahipliğini almak için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="63359-140">Run the following command to take ownership of the Generalize.xml file in system32 folder:</span></span>

     ```powershell
     Takeown /f C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
     ```

  8. <span data-ttu-id="63359-141">Dosyayı uygun izni ayarlamak için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="63359-141">Run the following command to set appropriate permission on the file:</span></span>

     ```powershell
     Cacls C:\Windows\System32\ Sysprep\ActionFiles\Generalize.xml /G `<AdministratorUserName>`:F
     ```

     - <span data-ttu-id="63359-142">Evet, onay isteminde yanıtlayın.</span><span class="sxs-lookup"><span data-stu-id="63359-142">Answer Yes at the prompt for confirmation.</span></span>
     - <span data-ttu-id="63359-143">Unutmayın `<AdministratorUserName>` makinede yönetici olan bir kullanıcı adı ile değiştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="63359-143">Note that `<AdministratorUserName>` should be replaced by the username who is administrator on the machine.</span></span> <span data-ttu-id="63359-144">Örneğin, "Yönetici".</span><span class="sxs-lookup"><span data-stu-id="63359-144">For example, "Administrator".</span></span>

  9. <span data-ttu-id="63359-145">Düzenlenebilir ve üzerinde aşağıdaki komutu kullanarak Sysprep'i dizine kaydedilen dosyayı kopyalayın:</span><span class="sxs-lookup"><span data-stu-id="63359-145">Copy the file you edited and saved over to the Sysprep directory using the following command:</span></span>

     ```powershell
     xcopy C:\Generalize.xml C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
     ```

     - <span data-ttu-id="63359-146">(Üzerine yazmak için herhangi bir istem ise çift girilen yol denetleyin unutmayın) üzerine yazmak için Evet olarak yanıtlayın.</span><span class="sxs-lookup"><span data-stu-id="63359-146">Answer Yes to overwrite (note that if there is no prompt to overwrite, double check the path entered).</span></span>
     - <span data-ttu-id="63359-147">Düzenlenen Generalize.xml kopyanızın C:\ için kopyalanan varsayar.</span><span class="sxs-lookup"><span data-stu-id="63359-147">Assumes your edited copy of Generalize.xml was copied to C:\ .</span></span>

  10. <span data-ttu-id="63359-148">Geçici çözüm ile generalize.XML güncellenir.</span><span class="sxs-lookup"><span data-stu-id="63359-148">Generalize.xml is now updated with the workaround.</span></span> <span data-ttu-id="63359-149">Lütfen generalize seçeneği etkinken Sysprep'i çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="63359-149">Please run Sysprep with the generalize option enabled.</span></span>