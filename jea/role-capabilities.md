---
ms.date: 06/12/2017
keywords: jea, powershell, güvenlik
title: JEA rol özellikleri
ms.openlocfilehash: 0531baa284e66a42a162329ea20ecfdca6d0b526
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
---
# <a name="jea-role-capabilities"></a><span data-ttu-id="76374-103">JEA rol özellikleri</span><span class="sxs-lookup"><span data-stu-id="76374-103">JEA Role Capabilities</span></span>

> <span data-ttu-id="76374-104">Uygulandığı öğe: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="76374-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="76374-105">JEA uç noktası oluştururken, "tanımlayan bir veya daha fazla rol özellikleri" tanımlamanız gerekir *ne* birisi JEA oturumda yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="76374-105">When creating a JEA endpoint, you will need to define one or more "role capabilities" which describe *what* someone can do in a JEA session.</span></span>
<span data-ttu-id="76374-106">Bir rol özelliği bir uzantıya sahip olan tüm cmdlet'ler, İşlevler, sağlayıcıları ve kullanıcıları bağlamak için kullanılabilir hale getirmek dış programları listeler .psrc PowerShell veri dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="76374-106">A role capability is a PowerShell data file with the .psrc extension that lists all the cmdlets, functions, providers, and external programs that should be made available to connecting users.</span></span>

<span data-ttu-id="76374-107">Bu konuda JEA kullanıcılarınız için bir PowerShell Rol Yetenek dosyasının nasıl oluşturulacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="76374-107">This topic describes how to create a PowerShell role capability file for your JEA users.</span></span>

## <a name="determine-which-commands-to-allow"></a><span data-ttu-id="76374-108">İzin vermek için hangi komutların belirleme</span><span class="sxs-lookup"><span data-stu-id="76374-108">Determine which commands to allow</span></span>

<span data-ttu-id="76374-109">Bir rol özelliği dosyası oluştururken, ilk adım ne rolüne atanan kullanıcıların erişmesi ise.</span><span class="sxs-lookup"><span data-stu-id="76374-109">The first step when creating a role capability file is to consider what the users who are assigned the role will need access to.</span></span>
<span data-ttu-id="76374-110">Bu gereksinimleri toplama işlemi biraz zaman alabilir, ancak çok önemli bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="76374-110">This requirements gathering process can take a while, but it is a very important process.</span></span>
<span data-ttu-id="76374-111">Çok az cmdlet'ler ve İşlevler kullanıcıların erişim verip bunları işlerinin yapılmasını alma engelleyebilir.</span><span class="sxs-lookup"><span data-stu-id="76374-111">Giving users access to too few cmdlets and functions can prevent them from getting their job done.</span></span>
<span data-ttu-id="76374-112">Çok fazla cmdlet'ler ve İşlevler izin veren güvenlik tutum sergilemek zayıflatmanın örtük yönetici ayrıcalıklarını amaçlanan birden fazla yapılması kullanıcılara yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="76374-112">Allowing access to too many cmdlets and functions can lead to users doing more than you intended with their implicit admin privileges, weakening your security stance.</span></span>

<span data-ttu-id="76374-113">Aşağıdaki ipuçları doğru yolda olduğunuz sağlamaya yardımcı olabilir ancak bu işlem hakkında nasıl gidin, kuruluş ve hedeflerini bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="76374-113">How you go about this process will depend on your organization and goals, however the following tips can help ensure you're on the right path.</span></span>

1. <span data-ttu-id="76374-114">**Tanımlamak** komutları kullanıcıların işlerini halletmek için kullanıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="76374-114">**Identify** the commands users are using to get their jobs done.</span></span> <span data-ttu-id="76374-115">Bu, BT personeliniz araştırma, Otomasyon betikleri denetleme veya PowerShell oturumu dökümleri veya günlüklerini çözümleme gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="76374-115">This may involve surveying IT staff, checking automation scripts, or analyzing PowerShell session transcripts or logs.</span></span>
2. <span data-ttu-id="76374-116">**Güncelleştirme** PowerShell eşdeğerlerine komut satırı araçlarını, mümkün olduğunda, en iyi denetim ve JEA özelleştirme deneyimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="76374-116">**Update** use of command line tools to PowerShell equivalents, where possible, for the best auditing and JEA customization experience.</span></span> <span data-ttu-id="76374-117">Dış programları yerel PowerShell cmdlet'leri ve JEA işlevleri olarak granularly olarak kısıtlaması olamaz.</span><span class="sxs-lookup"><span data-stu-id="76374-117">External programs cannot be constrained as granularly as native PowerShell cmdlets and functions in JEA.</span></span>
3. <span data-ttu-id="76374-118">**Kısıtlama** yalnızca gereken belirli parametreleri veya parametre değerlerini izin verirseniz cmdlet'leri kapsamı.</span><span class="sxs-lookup"><span data-stu-id="76374-118">**Restrict** the scope of the cmdlets if necessary to only allow specific parameters or parameter values.</span></span> <span data-ttu-id="76374-119">Kullanıcıların yalnızca bir sistem parçası yönetebileceği olacaksa, bu özellikle önemlidir.</span><span class="sxs-lookup"><span data-stu-id="76374-119">This is particularly important if users should only be able to manage part of a system.</span></span>
4. <span data-ttu-id="76374-120">**Oluşturma** karmaşık komutları ya da JEA içinde sınırlamak zor olan komutları değiştirmek için özel işlevler.</span><span class="sxs-lookup"><span data-stu-id="76374-120">**Create** custom functions to replace complex commands or commands which are difficult to constrain in JEA.</span></span> <span data-ttu-id="76374-121">Karmaşık bir komut sarmalar veya ek doğrulama mantığını uygular basit bir işlev yöneticileri ve son kullanıcı basitleştirmek için ek denetim sunabilir.</span><span class="sxs-lookup"><span data-stu-id="76374-121">A simple function that wraps a complex command or applies additional validation logic can offer additional control for admins and end-user simplicity.</span></span>
5. <span data-ttu-id="76374-122">**Test** izin verilen komutları kullanıcılara ve/veya Otomasyon ile kapsamlı listesi Hizmetleri ve gerektiği gibi ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="76374-122">**Test** the scoped list of allowable commands with your users and/or automation services and adjust as necessary.</span></span>

<span data-ttu-id="76374-123">JEA oturumunda komutları genellikle yönetici (veya tersi durumda yükseltilmiş) ile çalışma ayrıcalıkları olduğunu unutmamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="76374-123">It is important to remember that commands in a JEA session are often run with admin (or otherwise elevated) privileges.</span></span>
<span data-ttu-id="76374-124">Kullanılabilir komutları dikkatli seçimi JEA endpoint bağlanan kullanıcının izinlerini yükseltmesine izin verme sağlamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="76374-124">Careful selection of available commands is important to ensure the JEA endpoint does not allow the connecting user to elevate their permissions.</span></span>
<span data-ttu-id="76374-125">Aşağıda izin veriyorsa kısıtlanmamış bir durumda amaçla kullanılabilir komutlar, bazı örnekler verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="76374-125">Below are some examples of commands that can be used maliciously if allowed in an unconstrained state.</span></span>
<span data-ttu-id="76374-126">Bu kapsamlı bir liste değil ve dikkat gerektiren bir başlangıç noktası olarak kullanılması unutmayın.</span><span class="sxs-lookup"><span data-stu-id="76374-126">Note that this is not an exhaustive list and should only be used as a cautionary starting point.</span></span>

### <a name="examples-of-potentially-dangerous-commands"></a><span data-ttu-id="76374-127">Potansiyel olarak tehlikeli olabilecek komutları örnekleri</span><span class="sxs-lookup"><span data-stu-id="76374-127">Examples of potentially dangerous commands</span></span>

<span data-ttu-id="76374-128">Riski</span><span class="sxs-lookup"><span data-stu-id="76374-128">Risk</span></span> | <span data-ttu-id="76374-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="76374-129">Example</span></span> | <span data-ttu-id="76374-130">İlgili komutları</span><span class="sxs-lookup"><span data-stu-id="76374-130">Related commands</span></span>
-----|---------|-----------------
<span data-ttu-id="76374-131">Bağlanan kullanıcının JEA atlamak için yönetici ayrıcalıkları verme</span><span class="sxs-lookup"><span data-stu-id="76374-131">Granting the connecting user admin privileges to bypass JEA</span></span> | `Add-LocalGroupMember -Member 'CONTOSO\jdoe' -Group 'Administrators'` | <span data-ttu-id="76374-132">`Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`</span><span class="sxs-lookup"><span data-stu-id="76374-132">`Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`</span></span>
<span data-ttu-id="76374-133">Kötü amaçlı yazılım, açıkları veya korumaları atlamak için özel betikler gibi rastgele bir kodu çalıştırma</span><span class="sxs-lookup"><span data-stu-id="76374-133">Running arbitrary code, such as malware, exploits, or custom scripts to bypass protections</span></span> | `Start-Process -FilePath '\\san\share\malware.exe'` | <span data-ttu-id="76374-134">`Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob`</span><span class="sxs-lookup"><span data-stu-id="76374-134">`Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob`</span></span>

## <a name="create-a-role-capability-file"></a><span data-ttu-id="76374-135">Bir rol özelliği dosyası oluşturma</span><span class="sxs-lookup"><span data-stu-id="76374-135">Create a role capability file</span></span>

<span data-ttu-id="76374-136">Yeni bir PowerShell Rol Yetenek dosya ile oluşturabileceğiniz [yeni PSRoleCapabilityFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSRoleCapabilityFile) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="76374-136">You can create a new PowerShell role capability file with the [New-PSRoleCapabilityFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSRoleCapabilityFile) cmdlet.</span></span>

```powershell
New-PSRoleCapabilityFile -Path .\MyFirstJEARole.psrc
```

<span data-ttu-id="76374-137">Sonuçta elde edilen Rol Yetenek dosyasını bir metin Düzenleyicisi'nde açılır ve rolü için istenen komutlarına izin vermek için değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="76374-137">The resulting role capability file can be opened in a text editor and modified to allow the desired commands for the role.</span></span>
<span data-ttu-id="76374-138">PowerShell Yardım belgelerine dosya nasıl yapılandırabileceğiniz çeşitli örnekler içerir.</span><span class="sxs-lookup"><span data-stu-id="76374-138">The PowerShell help documentation contains several examples of how you can configure the file.</span></span>

### <a name="allowing-powershell-cmdlets-and-functions"></a><span data-ttu-id="76374-139">PowerShell cmdlet'leri ve işlevleri izin verme</span><span class="sxs-lookup"><span data-stu-id="76374-139">Allowing PowerShell cmdlets and functions</span></span>

<span data-ttu-id="76374-140">PowerShell cmdlet'lerini veya İşlevler çalıştırmak için Kullanıcıları yetkilendirmek için cmdlet veya işlev adı VisbibleCmdlets veya VisibleFunctions alanları ekleyin.</span><span class="sxs-lookup"><span data-stu-id="76374-140">To authorize users to run PowerShell cmdlets or functions, add the cmdlet or function name to the VisbibleCmdlets or VisibleFunctions fields.</span></span>
<span data-ttu-id="76374-141">Bir cmdlet veya işlevi bir komut olup emin değilseniz, çalıştırabilirsiniz `Get-Command <name>` ve çıkışı "CommandType" özelliğini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="76374-141">If you aren't sure whether a command is a cmdlet or function, you can run `Get-Command <name>` and check the "CommandType" property in the output.</span></span>

```powershell
VisibleCmdlets = 'Restart-Computer', 'Get-NetIPAddress'
```

<span data-ttu-id="76374-142">Bazen belirli cmdlet veya işlevi kapsamını kullanıcılarınızın ihtiyaçları için çok geniş.</span><span class="sxs-lookup"><span data-stu-id="76374-142">Sometimes the scope of a specific cmdlet or function is too broad for your users' needs.</span></span>
<span data-ttu-id="76374-143">DNS Yöneticisi Örneğin, büyük olasılıkla yalnızca gereksinimlerini DNS hizmetini yeniden erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="76374-143">A DNS admin, for example, probably only needs access to restart the DNS service.</span></span>
<span data-ttu-id="76374-144">Kiracılar Self Servis Yönetim Araçları erişimi burada verilen bir çok kiracılı ortamında, kiracılar kendi kaynakları ile yönetme için sınırlı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="76374-144">In a multi-tenant environment where tenants are granted access to self-service management tools, tenants should be limited to managing with their own resources.</span></span>
<span data-ttu-id="76374-145">Bu durumlarda, cmdlet veya işlevi hangi parametreler sunulur kısıtlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="76374-145">For these cases, you can restrict which parameters are exposed from the cmdlet or function.</span></span>

```powershell

VisibleCmdlets = @{ Name = 'Restart-Computer'; Parameters = @{ Name = 'Name' }}

```

<span data-ttu-id="76374-146">Daha gelişmiş senaryolarda, bu parametrelerden biri sağlayabilir hangi değerlerin kısıtlamak gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="76374-146">In more advanced scenarios, you may also need to restrict which values someone can supply to these parameters.</span></span>
<span data-ttu-id="76374-147">Rol özellikleri, izin verilen değerler ya da belirli bir giriş izin verilip verilmediğini belirlemek için değerlendirilen bir normal ifade deseni tanımlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="76374-147">Role capabilities let you define a set of allowed values or a regular expression pattern that is evaluated to determine if a given input is allowed.</span></span>

```powershell
VisibleCmdlets = @{ Name = 'Restart-Service'; Parameters = @{ Name = 'Name'; ValidateSet = 'Dns', 'Spooler' }},
                 @{ Name = 'Start-Website'; Parameters = @{ Name = 'Name'; ValidatePattern = 'HR_*' }}
```

> [!NOTE]
> <span data-ttu-id="76374-148">[Ortak PowerShell parametrelerini](https://technet.microsoft.com/library/hh847884.aspx) kullanılabilir parametrelerin kısıtlıyor olsa bile her zaman izin verilir.</span><span class="sxs-lookup"><span data-stu-id="76374-148">The [common PowerShell parameters](https://technet.microsoft.com/library/hh847884.aspx) are always allowed, even if you restrict the available parameters.</span></span>
> <span data-ttu-id="76374-149">Siz açıkça bunları parametreler alanında listelenmemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="76374-149">You should not explicitly list them in the Parameters field.</span></span>

<span data-ttu-id="76374-150">Aşağıdaki tablo görünür cmdlet veya işlevi özelleştirebilirsiniz çeşitli yolları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="76374-150">The table below describes the various ways you can customize a visible cmdlet or function.</span></span>
<span data-ttu-id="76374-151">Karışık ve herhangi biriyle eşleşen aşağıda VisibleCmdlets alan.</span><span class="sxs-lookup"><span data-stu-id="76374-151">You can mix and match any of the below in the VisibleCmdlets field.</span></span>

<span data-ttu-id="76374-152">Örnek</span><span class="sxs-lookup"><span data-stu-id="76374-152">Example</span></span>                                                                                      | <span data-ttu-id="76374-153">Kullanım örneği</span><span class="sxs-lookup"><span data-stu-id="76374-153">Use case</span></span>
---------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------
<span data-ttu-id="76374-154">`'My-Func'` veya `@{ Name = 'My-Func' }`</span><span class="sxs-lookup"><span data-stu-id="76374-154">`'My-Func'` or `@{ Name = 'My-Func' }`</span></span>                                                       | <span data-ttu-id="76374-155">Kullanıcının çalıştırmasına izin verir `My-Func` parametreleri herhangi bir kısıtlamanın olmadığı.</span><span class="sxs-lookup"><span data-stu-id="76374-155">Allows the user to run `My-Func` without any restrictions on the parameters.</span></span>
`'MyModule\My-Func'`                                                                         | <span data-ttu-id="76374-156">Kullanıcının çalıştırmasına izin verir `My-Func` modülden `MyModule` parametreleri herhangi bir kısıtlamanın olmadığı.</span><span class="sxs-lookup"><span data-stu-id="76374-156">Allows the user to run `My-Func` from the module `MyModule` without any restrictions on the parameters.</span></span>
`'My-*'`                                                                                     | <span data-ttu-id="76374-157">Kullanıcının herhangi bir cmdlet veya işlevi ile fiili çalıştırmasına izin verir `My`.</span><span class="sxs-lookup"><span data-stu-id="76374-157">Allows the user to run any cmdlet or function with the verb `My`.</span></span>
`'*-Func'`                                                                                   | <span data-ttu-id="76374-158">Kullanıcının herhangi bir cmdlet veya işlevi ile isim çalıştırmasına izin verir `Func`.</span><span class="sxs-lookup"><span data-stu-id="76374-158">Allows the user to run any cmdlet or function with the noun `Func`.</span></span>
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'}, @{ Name = 'Param2' }}`               | <span data-ttu-id="76374-159">Kullanıcının çalıştırmasına izin verir `My-Func` ile `Param1` ve/veya `Param2` parametreleri.</span><span class="sxs-lookup"><span data-stu-id="76374-159">Allows the user to run `My-Func` with the `Param1` and/or `Param2` parameters.</span></span> <span data-ttu-id="76374-160">Herhangi bir değer parametreleri sağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="76374-160">Any value can be supplied to the parameters.</span></span>
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidateSet = 'Value1', 'Value2' }}`  | <span data-ttu-id="76374-161">Kullanıcının çalıştırmasına izin verir `My-Func` ile `Param1` parametresi.</span><span class="sxs-lookup"><span data-stu-id="76374-161">Allows the user to run `My-Func` with the `Param1` parameter.</span></span> <span data-ttu-id="76374-162">Yalnızca "Değer1" ve "Değer2" parametresi sağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="76374-162">Only "Value1" and "Value2" can be supplied to the parameter.</span></span>
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidatePattern = 'contoso.*' }}`     | <span data-ttu-id="76374-163">Kullanıcının çalıştırmasına izin verir `My-Func` ile `Param1` parametresi.</span><span class="sxs-lookup"><span data-stu-id="76374-163">Allows the user to run `My-Func` with the `Param1` parameter.</span></span> <span data-ttu-id="76374-164">"Contoso" ile başlayan herhangi bir değer parametresi sağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="76374-164">Any value starting with "contoso" can be supplied to the parameter.</span></span>


> [!WARNING]
> <span data-ttu-id="76374-165">İçin en iyi güvenlik uygulamaları, onu görünen cmdlet'lerini veya İşlevler tanımlarken joker karakterler kullanmak için önerilmez.</span><span class="sxs-lookup"><span data-stu-id="76374-165">For best security practices, it is not recommended to use wildcards when defining visible cmdlets or functions.</span></span>
> <span data-ttu-id="76374-166">Bunun yerine, aynı adlandırma şeması paylaşan başka hiçbir komut istemeden yetkili olduğundan emin olmak için güvenilen her komutun açık olarak listelenmelidir.</span><span class="sxs-lookup"><span data-stu-id="76374-166">Instead, you should explicitly list each trusted command to ensure no other commands that share the same naming scheme are unintentionally authorized.</span></span>

<span data-ttu-id="76374-167">Aynı cmdlet veya işlevi bir ValidatePattern ve ValidateSet uygulanamıyor.</span><span class="sxs-lookup"><span data-stu-id="76374-167">You cannot apply both a ValidatePattern and ValidateSet to the same cmdlet or function.</span></span>

<span data-ttu-id="76374-168">Bunu yaparsanız, ValidatePattern ValidateSet geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="76374-168">If you do, the ValidatePattern will override the ValidateSet.</span></span>

<span data-ttu-id="76374-169">ValidatePattern hakkında daha fazla bilgi için kullanıma [bu *Hey, Scripting Guy!* sonrası](https://blogs.technet.microsoft.com/heyscriptingguy/2011/01/11/validate-powershell-parameters-before-running-the-script/) ve [PowerShell normal ifadeler](https://technet.microsoft.com/library/hh847880.aspx) başvuru içeriği.</span><span class="sxs-lookup"><span data-stu-id="76374-169">For more information about ValidatePattern, check out [this *Hey, Scripting Guy!* post](https://blogs.technet.microsoft.com/heyscriptingguy/2011/01/11/validate-powershell-parameters-before-running-the-script/) and the [PowerShell Regular Expressions](https://technet.microsoft.com/library/hh847880.aspx) reference content.</span></span>

### <a name="allowing-external-commands-and-powershell-scripts"></a><span data-ttu-id="76374-170">Dış komutları ve PowerShell betikleri izin verme</span><span class="sxs-lookup"><span data-stu-id="76374-170">Allowing external commands and PowerShell scripts</span></span>

<span data-ttu-id="76374-171">Yürütülebilir dosyalar ve PowerShell betiklerini (.ps1) JEA oturumunda çalıştırmak kullanıcılara izin vermek için tam yolunu VisibleExternalCommands alandaki her bir program eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="76374-171">To allow users to run executables and PowerShell scripts (.ps1) in a JEA session, you have to add the full path to each program in the VisibleExternalCommands field.</span></span>

```powershell
VisibleExternalCommands = 'C:\Windows\System32\whoami.exe', 'C:\Program Files\Contoso\Scripts\UpdateITSoftware.ps1'
```

<span data-ttu-id="76374-172">Mümkünse, PowerShell cmdlet ya da işlevin eşdeğerlerini parametreleri PowerShell cmdlet'leri/olan işlevlere izin üzerinde denetime sahip olduğundan, yetki dış yürütülebilir dosyaları kullanmak önerilir.</span><span class="sxs-lookup"><span data-stu-id="76374-172">It is advised, where possible, to use PowerShell cmdlet/function equivalents of any external executables you authorize since you have control over which parameters are allowed with PowerShell cmdlets/functions.</span></span>

<span data-ttu-id="76374-173">Birçok yürütülebilir dosyaları, geçerli durumu okuma ve yalnızca farklı parametreler sağlayarak değiştirmek olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="76374-173">Many executables allow you to both read the current state and then change it just by providing different parameters.</span></span>

<span data-ttu-id="76374-174">Örneğin, hangi ağ paylaşımlarına yerel makine tarafından barındırılan denetlemek isteyen bir dosya sunucu yöneticisi rol göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="76374-174">For example, consider the role of a file server admin who wants to check which network shares are hosted by the local machine.</span></span>
<span data-ttu-id="76374-175">Kontrol etmenin bir yolu kullanmaktır `net share`.</span><span class="sxs-lookup"><span data-stu-id="76374-175">One way to check is to use `net share`.</span></span>
<span data-ttu-id="76374-176">Ancak, yönetici, yönetici ayrıcalıklarıyla kazanmak için komutunu kolayca kullanabilirsiniz çünkü net.exe çok tehlikeli izin vererek `net group Administrators unprivilegedjeauser /add`.</span><span class="sxs-lookup"><span data-stu-id="76374-176">However, allowing net.exe is very dangerous becuase the admin could just as easily use the command to gain admin privileges with `net group Administrators unprivilegedjeauser /add`.</span></span>
<span data-ttu-id="76374-177">Daha iyi bir yaklaşım izin vermektir [Get-SmbShare](https://technet.microsoft.com/library/jj635704.aspx) aynı sonucu veren ancak çok daha kısıtlı kapsama sahip.</span><span class="sxs-lookup"><span data-stu-id="76374-177">A better approach is to allow [Get-SmbShare](https://technet.microsoft.com/library/jj635704.aspx) which achieves the same result but has a much more limited scope.</span></span>

<span data-ttu-id="76374-178">Dış komutları kullanılabilir kullanıcılara JEA oturumda yaparken, her zaman başka bir yerde sistemine yerleştirilmiş bir benzer ada (ve büyük olasılıkla malicous) programı yerine yürütülmedi sağlamak için yürütülebilir dosyanın tam yolunu belirtin.</span><span class="sxs-lookup"><span data-stu-id="76374-178">When making external commands available to users in a JEA session, always specify the complete path to the executable to ensure a similarly named (and potentially malicous) program placed elsewhere on the system does not get executed instead.</span></span>

### <a name="allowing-access-to-powershell-providers"></a><span data-ttu-id="76374-179">PowerShell sağlayıcıları erişmesine izin verme</span><span class="sxs-lookup"><span data-stu-id="76374-179">Allowing access to PowerShell providers</span></span>

<span data-ttu-id="76374-180">Varsayılan olarak, hiçbir PowerShell sağlayıcıları JEA oturumlarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="76374-180">By default, no PowerShell providers are available in JEA sessions.</span></span>

<span data-ttu-id="76374-181">Öncelikle hassas bilgileri ve bağlanan kullanıcının duyurulmuş yapılandırma ayarları riskini azaltmak için budur.</span><span class="sxs-lookup"><span data-stu-id="76374-181">This is primarily to reduce the risk of sensitive information and configuration settings being disclosed to the connecting user.</span></span>

<span data-ttu-id="76374-182">Gerekli olduğunda kullanarak PowerShell sağlayıcılarının erişmesine izin vermek `VisibleProviders` komutu.</span><span class="sxs-lookup"><span data-stu-id="76374-182">When necessary, you can allow access to the PowerShell providers using the `VisibleProviders` command.</span></span>
<span data-ttu-id="76374-183">Sağlayıcıları tam listesi için çalıştırın `Get-PSProvider`.</span><span class="sxs-lookup"><span data-stu-id="76374-183">For a full list of providers, run `Get-PSProvider`.</span></span>

```powershell
VisibleProviders = 'Registry'
```

<span data-ttu-id="76374-184">Dosya sistemi, kayıt defteri, sertifika deposu veya diğer hassas sağlayıcıları erişim gerektiren Basit görevler için kullanıcı adına sağlayıcı ile çalışır, özel bir işlev yazma düşünebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="76374-184">For simple tasks that require access to the file system, registry, certificate store, or other sensitive providers, you can also consider writing a custom function that works with the provider on the user's behalf.</span></span>
<span data-ttu-id="76374-185">İşlevler, cmdlet'ler ve JEA oturumunda kullanılabilir dış programları JEA olarak aynı kısıtlamalara tabi değildir – varsayılan olarak herhangi bir sağlayıcıyı erişebilir.</span><span class="sxs-lookup"><span data-stu-id="76374-185">Functions, cmdlets, and external programs that are available in a JEA session are not subject to the same constraints as JEA -- they can access any provider by default.</span></span>
<span data-ttu-id="76374-186">Ayrıca, kullanmayı [kullanıcı sürücü](session-configurations.md#user-drive) zaman dosyaları kopyalanıyor/JEA uç noktasından gereklidir.</span><span class="sxs-lookup"><span data-stu-id="76374-186">Also consider using the [user drive](session-configurations.md#user-drive) when copying files to/from a JEA endpoint is required.</span></span>

### <a name="creating-custom-functions"></a><span data-ttu-id="76374-187">Özel işlevler oluşturma</span><span class="sxs-lookup"><span data-stu-id="76374-187">Creating custom functions</span></span>

<span data-ttu-id="76374-188">Karmaşık görevleri, son kullanıcılarınız için basitleştirmek için bir rol özelliği dosyasındaki özel işlevler yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="76374-188">You can author custom functions in a role capability file to simplify complex tasks for your end users.</span></span>
<span data-ttu-id="76374-189">Gelişmiş doğrulama mantığını cmdlet parametre değerleri için gerektiğinde özel işlevler de yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="76374-189">Custom functions are also useful when you require advanced validation logic for cmdlet parameter values.</span></span>
<span data-ttu-id="76374-190">Basit işlevleri yazabilirsiniz **FunctionDefinitions** alan:</span><span class="sxs-lookup"><span data-stu-id="76374-190">You can write simple functions in the **FunctionDefinitions** field:</span></span>

```powershell
VisibleFunctions = 'Get-TopProcess'

FunctionDefinitions = @{
    Name = 'Get-TopProcess'

    ScriptBlock = {
        param($Count = 10)

        Get-Process | Sort-Object -Property CPU -Descending | Microsoft.PowerShell.Utility\Select-Object -First $Count
    }
}
```

> [!IMPORTANT]
> <span data-ttu-id="76374-191">Özel işlevlerinizi adını eklemek unutmayın **VisibleFunctions** JEA kullanıcılar tarafından çalışma alanı.</span><span class="sxs-lookup"><span data-stu-id="76374-191">Don't forget to add the name of your custom functions to the **VisibleFunctions** field so they can be run by the JEA users.</span></span>


<span data-ttu-id="76374-192">Özel işlevler gövdesi (betik bloğu) sistemi için varsayılan dili modunda çalışır ve JEA'ın dil kısıtlamaları tabi değildir.</span><span class="sxs-lookup"><span data-stu-id="76374-192">The body (script block) of custom functions runs in the default language mode for the system and is not subject to JEA's language constraints.</span></span>
<span data-ttu-id="76374-193">Bu işlevler dosya sistemini ve kayıt defteri erişebilir ve Rol Yetenek dosyasında görünür oluşturulmayan komutları çalıştırmak, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="76374-193">This means that functions can access the file system and registry, and run commands that were not made visible in the role capability file.</span></span>
<span data-ttu-id="76374-194">Parametreleri kullanarak çalıştırmak için rastgele kod izin vererek kaçınmak için dikkatli olun ve yöneltme kullanıcı girişi cmdlet'leri gibi doğrudan kaçının `Invoke-Expression`.</span><span class="sxs-lookup"><span data-stu-id="76374-194">Take care to avoid allowing arbitrary code to be run when using parameters and avoid piping user input directly into cmdlets like `Invoke-Expression`.</span></span>

<span data-ttu-id="76374-195">Yukarıdaki örnekte göreceksiniz tam modül adı (FQMN) `Microsoft.PowerShell.Utility\Select-Object` yerine kestirme kullanılan `Select-Object`.</span><span class="sxs-lookup"><span data-stu-id="76374-195">In the above example, you will notice that the fully qualified module name (FQMN) `Microsoft.PowerShell.Utility\Select-Object` was used instead of the shorthand `Select-Object`.</span></span>
<span data-ttu-id="76374-196">Rol Yetenek dosyalarında tanımlanan proxy işlevleri içeren hala kapsamını JEA oturumları tabi işlevlerdir mevcut komutları sınırlamak için JEA oluşturur.</span><span class="sxs-lookup"><span data-stu-id="76374-196">Functions defined in role capability files are still subject to the scope of JEA sessions, which includes the proxy functions JEA creates to constrain existing commands.</span></span>

<span data-ttu-id="76374-197">Select-Object varsayılan olarak, tüm JEA oturumlarda nesneler üzerinde isteğe bağlı özellikler seçmenizi izin vermeyen kısıtlanmış cmdlet ' dir.</span><span class="sxs-lookup"><span data-stu-id="76374-197">Select-Object is a default, constrained cmdlet in all JEA sessions that doesn't allow you to select arbitrary properties on objects.</span></span>
<span data-ttu-id="76374-198">Kısıtlanmamış Select-Object işlevlerini kullanmak için açıkça FQMN belirterek tam uygulamayı istemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="76374-198">To use the unconstrained Select-Object in functions, you must explicitly request the full implementation by specifying the FQMN.</span></span>
<span data-ttu-id="76374-199">Herhangi bir kısıtlanmış cmdlet'i JEA oturumunda PowerShell'in uygun olarak bir işlevden çağrıldığında aynı davranışı sergiler [komut öncelik](https://msdn.microsoft.com/en-us/powershell/reference/3.0/microsoft.powershell.core/about/about_command_precedence).</span><span class="sxs-lookup"><span data-stu-id="76374-199">Any constrained cmdlet in a JEA session will exhibit the same behavior when invoked from a function, in line with PowerShell's [command precedence](https://msdn.microsoft.com/en-us/powershell/reference/3.0/microsoft.powershell.core/about/about_command_precedence).</span></span>

<span data-ttu-id="76374-200">Çok sayıda özel işlevler yazıyorsanız, bunları yerleştirmek daha kolay olabilir bir [PowerShell betik modülündeki](https://msdn.microsoft.com/en-us/library/dd878340(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="76374-200">If you are writing a lot of custom functions, it may be easier to put them in a [PowerShell Script Module](https://msdn.microsoft.com/en-us/library/dd878340(v=vs.85).aspx).</span></span>
<span data-ttu-id="76374-201">Daha sonra bu işlevler yerleşik ve üçüncü taraf modüllerle gibi VisibleFunctions alanını kullanarak JEA oturumunda görünür yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="76374-201">You can then make those functions visible in the JEA session using the VisibleFunctions field like you would with built-in and third party modules.</span></span>

## <a name="place-role-capabilities-in-a-module"></a><span data-ttu-id="76374-202">Bir modüle rol özellikleri yerleştirin</span><span class="sxs-lookup"><span data-stu-id="76374-202">Place role capabilities in a module</span></span>

<span data-ttu-id="76374-203">Bir rol özelliği dosyayı bulmak PowerShell sırada bir PowerShell modülü "RoleCapabilities" klasöründe depolanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="76374-203">In order for PowerShell to find a role capability file, it must be stored in a "RoleCapabilities" folder in a PowerShell module.</span></span>
<span data-ttu-id="76374-204">Modül dahil herhangi bir klasör depolanabilir `$env:PSModulePath` ortam değişkeni, ancak bu System32 (yerleşik modülleri için ayrılmış) veya bir klasöre yerleştirdiğiniz değil burada güvenilmeyen, kullanıcılara bağlanan dosyaları değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="76374-204">The module can be stored in any folder included in the `$env:PSModulePath` environment variable, however you should not place it in System32 (reserved for built-in modules) or a folder where the untrusted, connecting users could modify the files.</span></span>
<span data-ttu-id="76374-205">Adlı basit bir PowerShell komut dosyası modülü oluşturma örneği aşağıdadır *ContosoJEA* "Program Files" yolunda.</span><span class="sxs-lookup"><span data-stu-id="76374-205">Below is an example of creating a basic PowerShell script module called *ContosoJEA* in the "Program Files" path.</span></span>

```powershell
# Create a folder for the module
$modulePath = Join-Path $env:ProgramFiles "WindowsPowerShell\Modules\ContosoJEA"
New-Item -ItemType Directory -Path $modulePath

# Create an empty script module and module manifest. At least one file in the module folder must have the same name as the folder itself.
New-Item -ItemType File -Path (Join-Path $modulePath "ContosoJEAFunctions.psm1")
New-ModuleManifest -Path (Join-Path $modulePath "ContosoJEA.psd1") -RootModule "ContosoJEAFunctions.psm1"

# Create the RoleCapabilities folder and copy in the PSRC file
$rcFolder = Join-Path $modulePath "RoleCapabilities"
New-Item -ItemType Directory $rcFolder
Copy-Item -Path .\MyFirstJEARole.psrc -Destination $rcFolder
```

<span data-ttu-id="76374-206">Bkz: [bir PowerShell modülü anlama](https://msdn.microsoft.com/en-us/library/dd878324.aspx) PowerShell modülleri, modül bildirimleri ve PSModulePath ortam değişkeni hakkında daha fazla bilgi.</span><span class="sxs-lookup"><span data-stu-id="76374-206">See [Understanding a PowerShell Module](https://msdn.microsoft.com/en-us/library/dd878324.aspx) for more information about PowerShell modules, module manifests, and the PSModulePath environment variable.</span></span>

## <a name="updating-role-capabilities"></a><span data-ttu-id="76374-207">Rol özellikleri güncelleştiriliyor</span><span class="sxs-lookup"><span data-stu-id="76374-207">Updating role capabilities</span></span>


<span data-ttu-id="76374-208">Yalnızca Rol Yetenek dosyasına değişiklikleri kaydederek herhangi bir anda bir rol özelliği dosya güncelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="76374-208">You can update a role capability file at any time by simply saving changes to the role capability file.</span></span>
<span data-ttu-id="76374-209">Rol Yetenek güncelleştirildikten sonra başlatılan tüm yeni JEA oturumların yeniden düzenlenen özellikleri yansıtır.</span><span class="sxs-lookup"><span data-stu-id="76374-209">Any new JEA sessions started after the role capability has been updated will reflect the revised capabilities.</span></span>

<span data-ttu-id="76374-210">Rol özellikleri klasörüne erişimi denetleme çok önemli nedeni budur.</span><span class="sxs-lookup"><span data-stu-id="76374-210">This is why controlling access to the role capabilities folder is so important.</span></span>
<span data-ttu-id="76374-211">Yalnızca yüksek oranda güvenilir Yöneticiler rolü yetenek dosyaları değiştirmek mümkün olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="76374-211">Only highly trusted administrators should be able to change role capability files.</span></span>
<span data-ttu-id="76374-212">Güvenilmeyen bir kullanıcı rolü yetenek dosyaları değiştirirseniz bunlar kolayca kendilerini erişim bunları ayrıcalıklarını yükseltmek izin veren cmdlet'leri verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="76374-212">If an untrusted user can change role capability files, they can easily give themselves access to cmdlets which allow them to elevate their privileges.</span></span>


<span data-ttu-id="76374-213">Rol özellikleri erişimi kilitleme isteyen yöneticiler için yerel sistem içeren modüller ve Rol Yetenek dosya okuma erişimi olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="76374-213">For administrators looking to lock down access to the role capabilities, ensure Local System has read access to the role capability files and containing modules.</span></span>

## <a name="how-role-capabilities-are-merged"></a><span data-ttu-id="76374-214">Rol özellikleri nasıl birleştirilir</span><span class="sxs-lookup"><span data-stu-id="76374-214">How role capabilities are merged</span></span>

<span data-ttu-id="76374-215">Kullanıcıların olanağı verilir birden çok rol özellikleri erişimi rolü eşlemelerin bağlı olarak bir JEA oturumu girdiğinizde [oturum yapılandırma dosyası](session-configurations.md).</span><span class="sxs-lookup"><span data-stu-id="76374-215">Users can be granted access to multiple role capabilities when they enter a JEA session depending on the role mappings in the [session configuration file](session-configurations.md).</span></span>
<span data-ttu-id="76374-216">Bu gerçekleştiğinde, kullanıcıya vermek JEA çalışır *en fazla izne sahip* herhangi bir rol tarafından izin verilen komutlar kümesi.</span><span class="sxs-lookup"><span data-stu-id="76374-216">When this happens, JEA tries to give the user the *most permissive* set of commands allowed by any of the roles.</span></span>

<span data-ttu-id="76374-217">**VisibleCmdlets ve VisibleFunctions**</span><span class="sxs-lookup"><span data-stu-id="76374-217">**VisibleCmdlets and VisibleFunctions**</span></span>

<span data-ttu-id="76374-218">Cmdlet'leri ve bunların parametrelerini ve parametre değerlerini JEA içinde sınırlı olabilir İşlevler, en karmaşık birleştirme mantığı etkiler.</span><span class="sxs-lookup"><span data-stu-id="76374-218">The most complex merge logic affects cmdlets and functions, which can have their parameters and parameter values limited in JEA.</span></span>

<span data-ttu-id="76374-219">Kurallar aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="76374-219">The rules are as follows:</span></span>

1. <span data-ttu-id="76374-220">Bir cmdlet yalnızca bir rol görünür duruma getirildiyse, tüm geçerli parametre kısıtlamalarına sahip kullanıcıya görünür olacaktır.</span><span class="sxs-lookup"><span data-stu-id="76374-220">If a cmdlet is only made visible in one role, it will be visible to the user with any applicable parameter constraints.</span></span>
2. <span data-ttu-id="76374-221">Bir cmdlet birden fazla rolünde görünür hale gelir ve her bir rolü cmdlet aynı kısıtlamalar varsa, cmdlet bu kısıtlamalarına sahip kullanıcıya görünür olacaktır.</span><span class="sxs-lookup"><span data-stu-id="76374-221">If a cmdlet is made visible in more than one role, and each role has the same constraints on the cmdlet, the cmdlet will be visible to the user with those constraints.</span></span>
3. <span data-ttu-id="76374-222">Bir cmdlet birden fazla rolünde görünür hale gelir ve farklı bir parametre kümesi her rolü sağlar, cmdlet ve her rolünde tanımlanan parametrelerin tümüne kullanıcıya görünür.</span><span class="sxs-lookup"><span data-stu-id="76374-222">If a cmdlet is made visible in more than one role, and each role allows a different set of parameters, the cmdlet and all of the parameters defined across every role will be visible to the user.</span></span> <span data-ttu-id="76374-223">Bir rol parametrelerindeki kısıtlamalar yoksa, tüm parametreleri izin verilir.</span><span class="sxs-lookup"><span data-stu-id="76374-223">If one role doesn't have constraints on the parameters, all parameters will be allowed.</span></span>
4. <span data-ttu-id="76374-224">Doğrulama kümesi veya doğrulama düzeni bir cmdlet parametresi için bir rol tanımlar ve diğer rol parametresi verir, ancak parametre değerlerini sınırlamalarına değil, doğrulama kümesi veya desen yoksayılacak.</span><span class="sxs-lookup"><span data-stu-id="76374-224">If one role defines a validate set or validate pattern for a cmdlet parameter, and the other role allows the parameter but does not constrain the parameter values, the validate set or pattern will be ignored.</span></span>
5. <span data-ttu-id="76374-225">Doğrulama kümesi aynı cmdlet parametresi birden çok rolü için tanımlanmış olması durumunda, tüm doğrulama kümelerinden tüm değerleri izin verilir.</span><span class="sxs-lookup"><span data-stu-id="76374-225">If a validate set is defined for the same cmdlet parameter in more than one role, all values from all validate sets will be allowed.</span></span>
6. <span data-ttu-id="76374-226">Birden fazla rol aynı cmdlet parametresinde için bir doğrulama düzeni tanımlanmışsa desenleri hiçbiriyle herhangi bir değere izin verilir.</span><span class="sxs-lookup"><span data-stu-id="76374-226">If a validate pattern is defined for the same cmdlet parameter in more than one role, any values that match any of the patterns will be allowed.</span></span>
7. <span data-ttu-id="76374-227">Doğrulama kümesi bir veya daha fazla rollerinde tanımlandı ve başka bir rol aynı cmdlet parametresi için bir doğrulama düzeni tanımlanan doğrulama kümesi gözardı edilir ve kural (6) için kalan doğrulama modelleri uygular.</span><span class="sxs-lookup"><span data-stu-id="76374-227">If a validate set is defined in one or more roles, and a validate pattern is defined in another role for the same cmdlet parameter, the validate set is ignored and rule (6) applies to the remaining validate patterns.</span></span>

<span data-ttu-id="76374-228">Roller bu kurallara göre nasıl birleştirilir örneği aşağıdadır:</span><span class="sxs-lookup"><span data-stu-id="76374-228">Below is an example of how roles are merged according to these rules:</span></span>

```powershell
# Role A Visible Cmdlets
$roleA = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client' } }
}

# Role B Visible Cmdlets
$roleB = @{
    VisibleCmdlets = @{ Name = 'Get-Service'; Parameters = @{ Name = 'DisplayName'; ValidatePattern = 'DNS.*' } },
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Server' } }
}

# Resulting permisisons for a user who belongs to both role A and B
# - The constraint in role B for the DisplayName parameter on Get-Service is ignored becuase of rule #4
# - The ValidateSets for Restart-Service are merged because both roles use ValidateSet on the same parameter per rule #5
$mergedAandB = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client', 'DNS Server' } }
}
```



<span data-ttu-id="76374-229">**VisibleExternalCommands, VisibleAliases, VisibleProviders, ScriptsToProcess**</span><span class="sxs-lookup"><span data-stu-id="76374-229">**VisibleExternalCommands, VisibleAliases, VisibleProviders, ScriptsToProcess**</span></span>

<span data-ttu-id="76374-230">Rol Yetenek dosyasındaki diğer tüm alanlar yalnızca toplu bir izin verilen dış komutları, diğer adlar, sağlayıcıları ve başlatma komut dosyaları kümesine eklenir.</span><span class="sxs-lookup"><span data-stu-id="76374-230">All other fields in the role capability file are simply added to a cumulative set of allowable external commands, aliases, providers, and startup scripts.</span></span>
<span data-ttu-id="76374-231">Komut, diğer ad, sağlayıcı veya komut dosyası bir rol özelliği de kullanılabilir JEA kullanıcı için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="76374-231">Any command, alias, provider, or script available in one role capability will be available to the JEA user.</span></span>

<span data-ttu-id="76374-232">Bir sağlayıcılardan birleştirilmiş bir dizi emin olmak dikkatli olun rol özellik ve işlevleri/cmdlet'leri/komutları başka bir izin verme bağlanan kullanıcıların istenmeyen sistem kaynaklarına erişim.</span><span class="sxs-lookup"><span data-stu-id="76374-232">Be careful to ensure that the combined set of providers from one role capability and cmdlets/functions/commands from another do not allow connecting users unintentional access to system resources.</span></span>
<span data-ttu-id="76374-233">Örneğin, bir rol izin veriyorsa `Remove-Item` cmdlet ve diğer izin veren `FileSystem` sağlayıcısı olduğunuz risk rastgele dosyaları bilgisayarınıza silme JEA kullanıcı.</span><span class="sxs-lookup"><span data-stu-id="76374-233">For example, if one role allows the `Remove-Item` cmdlet and another allows the `FileSystem` provider, you are at risk of a JEA user deleting arbitrary files on your computer.</span></span>
<span data-ttu-id="76374-234">Kullanıcıların etkili izinleri tanımlama hakkında ek bilgiler bulunabilir [JEA konu denetim](audit-and-report.md).</span><span class="sxs-lookup"><span data-stu-id="76374-234">Additional information about identifying users' effective permissions can be found in the [auditing JEA topic](audit-and-report.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="76374-235">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="76374-235">Next steps</span></span>

- [<span data-ttu-id="76374-236">Oturum yapılandırma dosyası oluşturma</span><span class="sxs-lookup"><span data-stu-id="76374-236">Create a session configuration file</span></span>](session-configurations.md)