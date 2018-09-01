---
ms.date: 08/24/2018
keywords: PowerShell cmdlet'i
title: PowerShell adlarını öğrenme
ms.assetid: b4d0fd22-8298-4ee6-82ae-9b6f2907c986
ms.openlocfilehash: 44c66488a20c38d8528c92d753f6b32dda5a2dcb
ms.sourcegitcommit: c170a1608d20d3c925d79c35fa208f650d014146
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2018
ms.locfileid: "43353275"
---
# <a name="learning-powershell-names"></a><span data-ttu-id="b74ee-103">PowerShell adlarını öğrenme</span><span class="sxs-lookup"><span data-stu-id="b74ee-103">Learning PowerShell names</span></span>

<span data-ttu-id="b74ee-104">Komutlar ve parametreler adlarını öğrenme çoğu komut satırı arabirimine sahip bir önemli zaman yatırımı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="b74ee-104">Learning names of commands and parameters requires a significant time investment with most command-line interfaces.</span></span> <span data-ttu-id="b74ee-105">Sorun birkaç desenleri yoktur.</span><span class="sxs-lookup"><span data-stu-id="b74ee-105">The issue is that there are few patterns.</span></span> <span data-ttu-id="b74ee-106">Anımsama, yalnızca komutları ve düzenli olarak kullanmak için gereken parametreleri bilgi yolu.</span><span class="sxs-lookup"><span data-stu-id="b74ee-106">Memorization is only way to learn the commands and parameters that you need to use on a regular basis.</span></span>

<span data-ttu-id="b74ee-107">Yeni bir komut veya parametresi ile çalışırken, her zaman, zaten tanıdığınız kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="b74ee-107">When you work with a new command or parameter, you can't always use what you already know.</span></span> <span data-ttu-id="b74ee-108">Ve yeni bir ad öğrenin gerekir.</span><span class="sxs-lookup"><span data-stu-id="b74ee-108">You have to find and learn a new name.</span></span> <span data-ttu-id="b74ee-109">Geleneksel olarak, komut satırı arabirimi, küçük bir araçlar kümesi ile başlayın ve artımlı eklemeleriyle büyütün.</span><span class="sxs-lookup"><span data-stu-id="b74ee-109">Traditionally, command-line interfaces start with a small set of tools and grow with incremental additions.</span></span> <span data-ttu-id="b74ee-110">Öğrenmek kolaydır hiçbir standart yapısı olmasının.</span><span class="sxs-lookup"><span data-stu-id="b74ee-110">It's easy to see why there's no standard structure.</span></span>
<span data-ttu-id="b74ee-111">Her komutu ayrı bir aracı olduğundan, bu komut adlarını mantıksal görünüyor.</span><span class="sxs-lookup"><span data-stu-id="b74ee-111">This seems logical for command names since each command is a separate tool.</span></span> <span data-ttu-id="b74ee-112">PowerShell komut adlarını başa çıkmanın daha iyi bir yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="b74ee-112">PowerShell has a better way to handle command names.</span></span>

## <a name="learning-command-names-in-traditional-shells"></a><span data-ttu-id="b74ee-113">Geleneksel Kabuk komut adlarını öğrenme</span><span class="sxs-lookup"><span data-stu-id="b74ee-113">Learning command names in traditional shells</span></span>

<span data-ttu-id="b74ee-114">Çoğu komutlar, işletim sistemi veya uygulama, hizmetler veya işlemleri gibi öğeleri yönetmek için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b74ee-114">Most commands are built to manage elements of the operating system or applications, such as services or processes.</span></span> <span data-ttu-id="b74ee-115">Komutları ailesi ile bir çözüm karşılamayabilir veya adlara sahip.</span><span class="sxs-lookup"><span data-stu-id="b74ee-115">The commands have names that may or may not fit into a family.</span></span> <span data-ttu-id="b74ee-116">Örneğin, Windows sistemlerinde kullanabilirsiniz `net start` ve `net stop` komutları bir hizmeti durdurmak ve başlatmak.</span><span class="sxs-lookup"><span data-stu-id="b74ee-116">For example, on Windows systems, you can use the `net start` and `net stop` commands to start and stop a service.</span></span> <span data-ttu-id="b74ee-117">**SC.exe** Windows için başka bir hizmet denetimi araçtır.</span><span class="sxs-lookup"><span data-stu-id="b74ee-117">**Sc.exe** is another service control tool for Windows.</span></span> <span data-ttu-id="b74ee-118">Bu ada adlandırma desenini içine uymayan **net.exe** hizmet komutları.</span><span class="sxs-lookup"><span data-stu-id="b74ee-118">That name does not fit into the naming pattern for the **net.exe** service commands.</span></span> <span data-ttu-id="b74ee-119">İşlem yönetimi için Windows sahip **tasklist.exe** süreçleri Listele komutu ve **taskkill.exe** işlemleri sonlandırmak için komutu.</span><span class="sxs-lookup"><span data-stu-id="b74ee-119">For process management, Windows has the **tasklist.exe** command to list processes and the **taskkill.exe** command to kill processes.</span></span>

<span data-ttu-id="b74ee-120">Ayrıca, bu komutlar, düzensiz parametresi belirtimlerine sahip.</span><span class="sxs-lookup"><span data-stu-id="b74ee-120">Also, these commands have irregular parameter specifications.</span></span> <span data-ttu-id="b74ee-121">Kullanamazsınız `net start` uzak bir bilgisayarda bir hizmeti başlatmak için komutu.</span><span class="sxs-lookup"><span data-stu-id="b74ee-121">You can't use the `net start` command to start a service on a remote computer.</span></span> <span data-ttu-id="b74ee-122">**Sc.exe** komut, uzak bir bilgisayarda hizmet başlayabilir.</span><span class="sxs-lookup"><span data-stu-id="b74ee-122">The **sc.exe** command can start a service on a remote computer.</span></span> <span data-ttu-id="b74ee-123">Ancak, uzak bilgisayarı belirtmek için adını çift ters eğik çizgi ile önek.</span><span class="sxs-lookup"><span data-stu-id="b74ee-123">But to specify the remote computer, you must prefix its name with a double backslash.</span></span> <span data-ttu-id="b74ee-124">DC01 adlı bir uzak bilgisayarda Biriktirici hizmetini başlatmak için yazdığınız `sc.exe \\DC01 start spooler`.</span><span class="sxs-lookup"><span data-stu-id="b74ee-124">To start the spooler service on a remote computer named DC01, you type `sc.exe \\DC01 start spooler`.</span></span>
<span data-ttu-id="b74ee-125">Listeye DC01 üzerinde çalışan görevler, kullandığınız **/S** parametresi ve ters eğik çizgi olmadan bilgisayar adı.</span><span class="sxs-lookup"><span data-stu-id="b74ee-125">To list tasks running on DC01, you use the **/S** parameter and the computer name without backslashes.</span></span> <span data-ttu-id="b74ee-126">Örneğin, `tasklist /S DC01`.</span><span class="sxs-lookup"><span data-stu-id="b74ee-126">For example, `tasklist /S DC01`.</span></span>

> [!NOTE]
> <span data-ttu-id="b74ee-127">PowerShell v6 önce `sc` için bir diğer ad olduğu `Set-Content` cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="b74ee-127">Prior to PowerShell v6, `sc` was an alias for the `Set-Content` cmdlet.</span></span> <span data-ttu-id="b74ee-128">Çalıştırılacak **sc.exe** komut, dosya uzantısını içermesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="b74ee-128">To run the **sc.exe** command, you must include the file extension.</span></span>

<span data-ttu-id="b74ee-129">Hizmetler ve işlemler iyi tanımlanmış yaşam döngülerine sahiptir yönetilebilir bir bilgisayar öğelerde örnekleridir.</span><span class="sxs-lookup"><span data-stu-id="b74ee-129">Services and processes are examples of manageable elements on a computer that have well-defined life cycles.</span></span> <span data-ttu-id="b74ee-130">Başlangıç veya hizmetleri ve işlemleri durdurun veya tüm hizmetler ve işlemlerin şu anda çalışan bir listesini alın.</span><span class="sxs-lookup"><span data-stu-id="b74ee-130">You may start or stop services and processes, or get a list of all currently running services or processes.</span></span> <span data-ttu-id="b74ee-131">Bunlar arasında önemli teknik farklılıklar olsa da, hizmetler ve işlemler üzerinde gerçekleştirdiğiniz eylemleri kavramsal olarak aynı değildir.</span><span class="sxs-lookup"><span data-stu-id="b74ee-131">Although there are important technical distinctions between them, the actions you perform on services and processes are conceptually the same.</span></span> <span data-ttu-id="b74ee-132">Ayrıca, biz parametreleri belirterek bir eylemin özelleştirmek için yaptığınız seçimlere de kavramsal olarak benzer olabilir.</span><span class="sxs-lookup"><span data-stu-id="b74ee-132">Furthermore, the choices we make to customize an action by specifying parameters may be conceptually similar as well.</span></span>

<span data-ttu-id="b74ee-133">PowerShell anlamak ve cmdlet'lerini kullanmak için bilmeniz gereken farklı ad sayısını azaltmak için bu benzerlikler yararlanan.</span><span class="sxs-lookup"><span data-stu-id="b74ee-133">PowerShell exploits these similarities to reduce the number of distinct names you need to know to understand and use cmdlets.</span></span>

## <a name="cmdlets-use-verb-noun-names-to-reduce-command-memorization"></a><span data-ttu-id="b74ee-134">Cmdlet'leri, komut anımsama azaltmak için fiil-isim adları kullanın.</span><span class="sxs-lookup"><span data-stu-id="b74ee-134">Cmdlets use verb-noun names to reduce command memorization</span></span>

<span data-ttu-id="b74ee-135">PowerShell, bir "fiil-isim" adlandırma sistemi kullanır.</span><span class="sxs-lookup"><span data-stu-id="b74ee-135">PowerShell uses a "verb-noun" naming system.</span></span> <span data-ttu-id="b74ee-136">Her cmdlet adı ile belirli bir isim hecelerine standart fiil oluşur.</span><span class="sxs-lookup"><span data-stu-id="b74ee-136">Each cmdlet name consists of a standard verb hyphenated with a specific noun.</span></span> <span data-ttu-id="b74ee-137">PowerShell fiillerini her zaman İngilizce fiilleri değildir, ancak bunlar belirli eylemleri PowerShell'de express.</span><span class="sxs-lookup"><span data-stu-id="b74ee-137">PowerShell verbs are not always English verbs, but they express specific actions in PowerShell.</span></span> <span data-ttu-id="b74ee-138">İsimleri çok herhangi bir dilde isimleri gibi.</span><span class="sxs-lookup"><span data-stu-id="b74ee-138">Nouns are very much like nouns in any language.</span></span> <span data-ttu-id="b74ee-139">Bunlar, sistem yönetiminde önemli olan nesneler belirli türlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="b74ee-139">They describe specific types of objects that are important in system administration.</span></span> <span data-ttu-id="b74ee-140">Bazı örneklere bakarak bu iki kısımlı adlar öğrenme çaba nasıl azaltmak göstermek kolay bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="b74ee-140">It's easy to demonstrate how these two-part names reduce learning effort by looking at a few examples.</span></span>

<span data-ttu-id="b74ee-141">Standart fiiller önerilen bir dizi PowerShell sahiptir.</span><span class="sxs-lookup"><span data-stu-id="b74ee-141">PowerShell has a recommended set of standard verbs.</span></span> <span data-ttu-id="b74ee-142">İsimleri daha az kısıtlıdır, ancak her zaman fiili temel aldığı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b74ee-142">Nouns are less restricted, but always describe what the verb acts upon.</span></span> <span data-ttu-id="b74ee-143">PowerShell komutları gibi sahip `Get-Process`, `Stop-Process`, `Get-Service`, ve `Stop-Service`.</span><span class="sxs-lookup"><span data-stu-id="b74ee-143">PowerShell has commands such as `Get-Process`, `Stop-Process`, `Get-Service`, and `Stop-Service`.</span></span>

<span data-ttu-id="b74ee-144">Bu örnekte iki isimleri ve fiilleri o kadarlık öğrenme tutarlılık basitleştirin değil.</span><span class="sxs-lookup"><span data-stu-id="b74ee-144">For this example of two nouns and verbs, consistency does not simplify learning that much.</span></span> <span data-ttu-id="b74ee-145">Bu liste 10 fiilleri ve 10 isimleri standartlaştırılmış bir dizi genişletin.</span><span class="sxs-lookup"><span data-stu-id="b74ee-145">Extend that list to a standardized set of 10 verbs and 10 nouns.</span></span> <span data-ttu-id="b74ee-146">Artık yalnızca anlamak için 20 sözcükler vardır.</span><span class="sxs-lookup"><span data-stu-id="b74ee-146">Now you only have 20 words to understand.</span></span>
<span data-ttu-id="b74ee-147">Ancak, bu sözcükleri form 100 farklı komut adlarını birleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="b74ee-147">But those words can be combined to form 100 distinct command names.</span></span>

<span data-ttu-id="b74ee-148">Bir PowerShell komut adını okuyarak ne yaptığını anlamak kolay bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="b74ee-148">It's easy to understand what a PowerShell command does by reading its name.</span></span> <span data-ttu-id="b74ee-149">Bir bilgisayarı kapatmak için komut `Stop-Computer`.</span><span class="sxs-lookup"><span data-stu-id="b74ee-149">The command to shut down a computer is `Stop-Computer`.</span></span> <span data-ttu-id="b74ee-150">Ağdaki tüm bilgisayarlarda listelemek için komut `Get-Computer`.</span><span class="sxs-lookup"><span data-stu-id="b74ee-150">The command to list all computers on a network is `Get-Computer`.</span></span> <span data-ttu-id="b74ee-151">Sistem tarihini almak için komut `Get-Date`.</span><span class="sxs-lookup"><span data-stu-id="b74ee-151">The command to get the system date is `Get-Date`.</span></span>

<span data-ttu-id="b74ee-152">Belirli bir eylemiyle dahil tüm komutları listeleyerek **fiil** parametresi için `Get-Command`.</span><span class="sxs-lookup"><span data-stu-id="b74ee-152">You can list all commands that include a particular verb with the **Verb** parameter for `Get-Command`.</span></span> <span data-ttu-id="b74ee-153">Örneğin, fiili kullanan tüm cmdlet'leri görmek için `Get`, türü:</span><span class="sxs-lookup"><span data-stu-id="b74ee-153">For example, to see all cmdlets that use the verb `Get`, type:</span></span>

```
PS> Get-Command -Verb Get

CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Get-Acl                         Get-Acl [[-Path] <String[]>]...
Cmdlet          Get-Alias                       Get-Alias [[-Name] <String[]...
Cmdlet          Get-AuthenticodeSignature       Get-AuthenticodeSignature [-...
Cmdlet          Get-ChildItem                   Get-ChildItem [[-Path] <Stri...
...
```

<span data-ttu-id="b74ee-154">Kullanım **isim** aynı nesne türünü etkileyen komutlar ailesini görmek için parametre.</span><span class="sxs-lookup"><span data-stu-id="b74ee-154">Use the **Noun** parameter to see a family of commands that affect the same type of object.</span></span> <span data-ttu-id="b74ee-155">Örneğin, aşağıdaki hizmetleri yönetmek için kullanılabilir komutları görmek için komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="b74ee-155">For example, run following command to see the commands  available for managing services:</span></span>

```
PS> Get-Command -Noun Service

CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Get-Service                     Get-Service [[-Name] <String...
Cmdlet          New-Service                     New-Service [-Name] <String>...
Cmdlet          Restart-Service                 Restart-Service [-Name] <Str...
Cmdlet          Resume-Service                  Resume-Service [-Name] <Stri...
Cmdlet          Set-Service                     Set-Service [-Name] <String>...
Cmdlet          Start-Service                   Start-Service [-Name] <Strin...
Cmdlet          Stop-Service                    Stop-Service [-Name] <String...
Cmdlet          Suspend-Service                 Suspend-Service [-Name] <Str...
...
```

## <a name="cmdlets-use-standard-parameters"></a><span data-ttu-id="b74ee-156">Standart parametreler cmdlet'leri kullanın</span><span class="sxs-lookup"><span data-stu-id="b74ee-156">Cmdlets use standard parameters</span></span>

<span data-ttu-id="b74ee-157">Daha önce belirtildiği gibi geleneksel komut satırı arabirimi kullanılan komutlarını her zaman tutarlı parametre adları yok.</span><span class="sxs-lookup"><span data-stu-id="b74ee-157">As noted earlier, commands used in traditional command-line interfaces don't always have consistent parameter names.</span></span> <span data-ttu-id="b74ee-158">Parametreleri genellikle tek bir karakteri ya da yazmak kolaydır, ancak yeni kullanıcılar tarafından kolayca anlaşılır olmayan sözcükler olarak kısaltılır.</span><span class="sxs-lookup"><span data-stu-id="b74ee-158">Parameters are often single-character or abbreviated words that are easy to type but aren't easily understood by new users.</span></span>

<span data-ttu-id="b74ee-159">Çoğu geleneksel komut satırı arabirimlerinden aksine PowerShell parametreleri doğrudan işler ve parametre adları standartlaştırmak parametreleri Geliştirici Kılavuzu ile birlikte bu doğrudan erişim kullanır.</span><span class="sxs-lookup"><span data-stu-id="b74ee-159">Unlike most other traditional command-line interfaces, PowerShell processes parameters directly, and it uses this direct access to the parameters along with developer guidance to standardize parameter names.</span></span> <span data-ttu-id="b74ee-160">Bu kılavuz teşvik eder, ancak her cmdlet standardına uygun garanti etmez.</span><span class="sxs-lookup"><span data-stu-id="b74ee-160">This guidance encourages but does not guarantee that every cmdlet conforms to the standard.</span></span>

<span data-ttu-id="b74ee-161">PowerShell parametresi ayırıcı ayrıca standart hale getirir.</span><span class="sxs-lookup"><span data-stu-id="b74ee-161">PowerShell also standardizes the parameter separator.</span></span> <span data-ttu-id="b74ee-162">Parametre adları her zaman sahip bir '-' için bir PowerShell komutu ile etkileşimlidir.</span><span class="sxs-lookup"><span data-stu-id="b74ee-162">Parameter names always have a '-' prepended to them with a PowerShell command.</span></span> <span data-ttu-id="b74ee-163">Aşağıdaki örnek göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="b74ee-163">Consider the following example:</span></span>

```powershell
Get-Command -Name Clear-Host
```

<span data-ttu-id="b74ee-164">Parametrenin adı **adı**, ancak olarak yazılan `-Name` komut satırında bir parametre olarak kullanıldığında.</span><span class="sxs-lookup"><span data-stu-id="b74ee-164">The parameter's name is **Name**, but it is typed as `-Name` when used on the command line as a parameter.</span></span>

<span data-ttu-id="b74ee-165">Standart parametre adları ve kullanımları genel özelliklerinin bazıları aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b74ee-165">Here are some of the general characteristics of the standard parameter names and usages.</span></span>

### <a name="the-help-parameter-"></a><span data-ttu-id="b74ee-166">Yardım parametresi (?)</span><span class="sxs-lookup"><span data-stu-id="b74ee-166">The Help parameter (?)</span></span>

<span data-ttu-id="b74ee-167">Belirttiğinizde `-Help` veya `-?` parametresi üzerinde herhangi bir cmdlet'i, PowerShell cmdlet Yardımı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="b74ee-167">When you specify the `-Help` or `-?` parameter on any cmdlet, PowerShell displays help for the cmdlet.</span></span> <span data-ttu-id="b74ee-168">Cmdlet yürütülmedi.</span><span class="sxs-lookup"><span data-stu-id="b74ee-168">The cmdlet is not executed.</span></span>

### <a name="common-parameters"></a><span data-ttu-id="b74ee-169">Ortak parametreleri</span><span class="sxs-lookup"><span data-stu-id="b74ee-169">Common parameters</span></span>

<span data-ttu-id="b74ee-170">PowerShell sahip birkaç *ortak parametreleri*.</span><span class="sxs-lookup"><span data-stu-id="b74ee-170">PowerShell has several *common parameters*.</span></span> <span data-ttu-id="b74ee-171">Bu parametreler PowerShell altyapısı tarafından denetlenir.</span><span class="sxs-lookup"><span data-stu-id="b74ee-171">These parameters are controlled by the PowerShell engine.</span></span> <span data-ttu-id="b74ee-172">Ortak parametreleri her zaman aynı şekilde davranır.</span><span class="sxs-lookup"><span data-stu-id="b74ee-172">Common parameters always behave the same way.</span></span> <span data-ttu-id="b74ee-173">Ortak parametreler **WhatIf**, **Onayla**, **ayrıntılı**, **hata ayıklama**, **uyar**, **ErrorAction**, **ErrorVariable**, **OutVariable**, ve **OutBuffer**.</span><span class="sxs-lookup"><span data-stu-id="b74ee-173">The common parameters are **WhatIf**, **Confirm**, **Verbose**, **Debug**, **Warn**, **ErrorAction**, **ErrorVariable**, **OutVariable**, and **OutBuffer**.</span></span>

### <a name="recommended-parameter-names"></a><span data-ttu-id="b74ee-174">Önerilen parametre adları</span><span class="sxs-lookup"><span data-stu-id="b74ee-174">Recommended parameter names</span></span>

<span data-ttu-id="b74ee-175">PowerShell core cmdlet'leri benzer parametreler için standart adları kullanın.</span><span class="sxs-lookup"><span data-stu-id="b74ee-175">The PowerShell core cmdlets use standard names for similar parameters.</span></span> <span data-ttu-id="b74ee-176">Bu standart adlarının kullanılmasını zorunlu değildir, ancak Standardizasyon teşvik etmek için açık yönergeler.</span><span class="sxs-lookup"><span data-stu-id="b74ee-176">The use of these standard names is not enforced, but there is explicit guidance to encourage standardization.</span></span>

<span data-ttu-id="b74ee-177">Örneğin, bir bilgisayara başvuruda bulunan bir parametre için önerilen ad olduğu **ComputerName**, sunucu, konak, sistem, düğümü veya başka bir ortak alternatif yerine.</span><span class="sxs-lookup"><span data-stu-id="b74ee-177">For example, the recommended name for a parameter that refers to a computer is **ComputerName**, rather than Server, Host, System, Node, or some other common alternative.</span></span> <span data-ttu-id="b74ee-178">Diğer önemli önerilen parametre adları **zorla**, **hariç**, **INCLUDE**, **PassThru**, **yolu**, ve **CaseSensitive**.</span><span class="sxs-lookup"><span data-stu-id="b74ee-178">Other important recommended parameter names are **Force**, **Exclude**, **Include**, **PassThru**, **Path**, and **CaseSensitive**.</span></span>