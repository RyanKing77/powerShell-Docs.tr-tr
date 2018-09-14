---
ms.date: 06/12/2017
keywords: jea, powershell, güvenlik
title: JEA rol özellikleri
ms.openlocfilehash: bd0a995adc60e50049ff99d6b23e7c2aeb745a18
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45522955"
---
# <a name="jea-role-capabilities"></a><span data-ttu-id="a681e-103">JEA rol özellikleri</span><span class="sxs-lookup"><span data-stu-id="a681e-103">JEA Role Capabilities</span></span>

> <span data-ttu-id="a681e-104">İçin geçerlidir: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="a681e-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="a681e-105">Bir JEA uç noktası oluştururken, "tanımlayan bir veya daha fazla rol özellikleri" tanımlamanız gerekir *ne* birisi bir JEA oturumda yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a681e-105">When creating a JEA endpoint, you will need to define one or more "role capabilities" which describe *what* someone can do in a JEA session.</span></span>
<span data-ttu-id="a681e-106">Bir rol özelliği, tüm cmdlet'ler, İşlevler, sağlayıcıları ve kullanıcıları bağlamak için kullanılabilir hale dış programlarda listeleyen .psrc uzantısına sahip bir PowerShell veri dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="a681e-106">A role capability is a PowerShell data file with the .psrc extension that lists all the cmdlets, functions, providers, and external programs that should be made available to connecting users.</span></span>

<span data-ttu-id="a681e-107">Bu konuda JEA kullanıcılarınız için bir PowerShell rol özellik dosyası oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="a681e-107">This topic describes how to create a PowerShell role capability file for your JEA users.</span></span>

## <a name="determine-which-commands-to-allow"></a><span data-ttu-id="a681e-108">İzin vermek için hangi komutları belirleme</span><span class="sxs-lookup"><span data-stu-id="a681e-108">Determine which commands to allow</span></span>

<span data-ttu-id="a681e-109">Bir rol özelliği dosyası oluştururken ilk adım, hangi rolü atanmış kullanıcılar erişmesi göz önünde bulundurun sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="a681e-109">The first step when creating a role capability file is to consider what the users who are assigned the role will need access to.</span></span>
<span data-ttu-id="a681e-110">Bu gereksinimleri toplama işlemi biraz zaman alabilir, ancak çok önemli bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="a681e-110">This requirements gathering process can take a while, but it is a very important process.</span></span>
<span data-ttu-id="a681e-111">Çok az sayıda cmdlet'ler ve İşlevler kullanıcılara erişim verme bunları işin yapılması olmanızı engelleyebilir.</span><span class="sxs-lookup"><span data-stu-id="a681e-111">Giving users access to too few cmdlets and functions can prevent them from getting their job done.</span></span>
<span data-ttu-id="a681e-112">Çok fazla cmdlet'ler ve İşlevler için erişime izin verme, güvenlik tutum sergilemek zayıflatmanın örtük yönetici ayrıcalıklarını istenenden daha yapılması kullanıcılara yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="a681e-112">Allowing access to too many cmdlets and functions can lead to users doing more than you intended with their implicit admin privileges, weakening your security stance.</span></span>

<span data-ttu-id="a681e-113">Aşağıdaki ipuçları, doğru yolda olduğunuzu sağlamaya yardımcı olabilir ancak bu işlem hakkında nasıl gittiğiniz, kuruluş ve hedefleri bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="a681e-113">How you go about this process will depend on your organization and goals, however the following tips can help ensure you're on the right path.</span></span>

1. <span data-ttu-id="a681e-114">**Tanımlamak** komutları kullanıcıların işlerini halletmek için kullanıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="a681e-114">**Identify** the commands users are using to get their jobs done.</span></span> <span data-ttu-id="a681e-115">Bu, BT personeliniz araştırma, Otomasyon betikleri denetimi veya PowerShell oturumu dökümleri ya da günlükleri çözümleme gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="a681e-115">This may involve surveying IT staff, checking automation scripts, or analyzing PowerShell session transcripts or logs.</span></span>
2. <span data-ttu-id="a681e-116">**Güncelleştirme** PowerShell eşdeğerlerine komut satırı araçları, mümkün olduğunda, en iyi denetleme ve JEA özelleştirme deneyimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a681e-116">**Update** use of command line tools to PowerShell equivalents, where possible, for the best auditing and JEA customization experience.</span></span> <span data-ttu-id="a681e-117">Dış programlarda, yerel PowerShell cmdlet'leri ve jea işlevlerle hedefle olarak kısıtlayamaz.</span><span class="sxs-lookup"><span data-stu-id="a681e-117">External programs cannot be constrained as granularly as native PowerShell cmdlets and functions in JEA.</span></span>
3. <span data-ttu-id="a681e-118">**Kısıtlama** cmdlet'ler belirli bir parametre veya parametre değerleri için yalnızca gerekli izin kapsamı.</span><span class="sxs-lookup"><span data-stu-id="a681e-118">**Restrict** the scope of the cmdlets if necessary to only allow specific parameters or parameter values.</span></span> <span data-ttu-id="a681e-119">Kullanıcılar yalnızca bir sistemin parçası yönetmek gerekiyorsa bu özellikle önemlidir.</span><span class="sxs-lookup"><span data-stu-id="a681e-119">This is particularly important if users should only be able to manage part of a system.</span></span>
4. <span data-ttu-id="a681e-120">**Oluşturma** karmaşık komutlar ya da JEA içinde kısıtlamak zor olan komutları değiştirmek için özel işlevler.</span><span class="sxs-lookup"><span data-stu-id="a681e-120">**Create** custom functions to replace complex commands or commands which are difficult to constrain in JEA.</span></span> <span data-ttu-id="a681e-121">Karmaşık bir komut sarmalar veya ek doğrulama mantığını uygular, basit bir işlevi yöneticileri ve son kullanıcı kolaylık olması için ek denetim sunabilir.</span><span class="sxs-lookup"><span data-stu-id="a681e-121">A simple function that wraps a complex command or applies additional validation logic can offer additional control for admins and end-user simplicity.</span></span>
5. <span data-ttu-id="a681e-122">**Test** kapsamlı kullanıcılara ve/veya Otomasyon ile verilen komutların listesini Hizmetleri ve gerektiği gibi ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a681e-122">**Test** the scoped list of allowable commands with your users and/or automation services and adjust as necessary.</span></span>

<span data-ttu-id="a681e-123">Bir JEA oturumunda komutları genellikle yönetici (veya başka türlü yükseltilmiş) ile çalışma ayrıcalıkları olduğunu unutmamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="a681e-123">It is important to remember that commands in a JEA session are often run with admin (or otherwise elevated) privileges.</span></span>
<span data-ttu-id="a681e-124">Kullanılabilir komutları dikkatli seçimi JEA uç noktası bağlanan kullanıcının izinlerini yükseltmesine izin vermiyor sağlamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="a681e-124">Careful selection of available commands is important to ensure the JEA endpoint does not allow the connecting user to elevate their permissions.</span></span>
<span data-ttu-id="a681e-125">Aşağıda bazı örnekler izin veriliyorsa sınırlandırılmamış bir durumda kötü amaçla kullanılabilecek komutlar verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a681e-125">Below are some examples of commands that can be used maliciously if allowed in an unconstrained state.</span></span>
<span data-ttu-id="a681e-126">Bu kapsamlı bir liste değildir ve yalnızca bir uyarı başlangıç noktası olarak kullanılması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a681e-126">Note that this is not an exhaustive list and should only be used as a cautionary starting point.</span></span>

### <a name="examples-of-potentially-dangerous-commands"></a><span data-ttu-id="a681e-127">Potansiyel olarak tehlikeli olabilecek komutlar örnekleri</span><span class="sxs-lookup"><span data-stu-id="a681e-127">Examples of potentially dangerous commands</span></span>

<span data-ttu-id="a681e-128">Risk</span><span class="sxs-lookup"><span data-stu-id="a681e-128">Risk</span></span> | <span data-ttu-id="a681e-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="a681e-129">Example</span></span> | <span data-ttu-id="a681e-130">İlgili komutları</span><span class="sxs-lookup"><span data-stu-id="a681e-130">Related commands</span></span>
-----|---------|-----------------
<span data-ttu-id="a681e-131">Bağlanan kullanıcının JEA atlamak için yönetici ayrıcalıkları verme</span><span class="sxs-lookup"><span data-stu-id="a681e-131">Granting the connecting user admin privileges to bypass JEA</span></span> | `Add-LocalGroupMember -Member 'CONTOSO\jdoe' -Group 'Administrators'` | <span data-ttu-id="a681e-132">`Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`</span><span class="sxs-lookup"><span data-stu-id="a681e-132">`Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`</span></span>
<span data-ttu-id="a681e-133">Kötü amaçlı yazılım, saldırılara veya korumaları atlamak için özel betikler gibi rastgele kod çalıştırma</span><span class="sxs-lookup"><span data-stu-id="a681e-133">Running arbitrary code, such as malware, exploits, or custom scripts to bypass protections</span></span> | `Start-Process -FilePath '\\san\share\malware.exe'` | <span data-ttu-id="a681e-134">`Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob`</span><span class="sxs-lookup"><span data-stu-id="a681e-134">`Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob`</span></span>

## <a name="create-a-role-capability-file"></a><span data-ttu-id="a681e-135">Bir rol özelliği dosyası oluşturma</span><span class="sxs-lookup"><span data-stu-id="a681e-135">Create a role capability file</span></span>

<span data-ttu-id="a681e-136">Yeni bir PowerShell rolü özelliği dosyasıyla oluşturabilirsiniz [yeni PSRoleCapabilityFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSRoleCapabilityFile) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="a681e-136">You can create a new PowerShell role capability file with the [New-PSRoleCapabilityFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSRoleCapabilityFile) cmdlet.</span></span>

```powershell
New-PSRoleCapabilityFile -Path .\MyFirstJEARole.psrc
```

<span data-ttu-id="a681e-137">Sonuçta elde edilen rol özelliği dosyasını bir metin Düzenleyicisi'nde açılır ve rolü için istenen komutlarına izin vermek için değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="a681e-137">The resulting role capability file can be opened in a text editor and modified to allow the desired commands for the role.</span></span>
<span data-ttu-id="a681e-138">PowerShell Yardım belgeleri dosyanın nasıl yapılandırabileceğiniz çeşitli örnekler içerir.</span><span class="sxs-lookup"><span data-stu-id="a681e-138">The PowerShell help documentation contains several examples of how you can configure the file.</span></span>

### <a name="allowing-powershell-cmdlets-and-functions"></a><span data-ttu-id="a681e-139">PowerShell cmdlet'leri ve işlevleri izin verme</span><span class="sxs-lookup"><span data-stu-id="a681e-139">Allowing PowerShell cmdlets and functions</span></span>

<span data-ttu-id="a681e-140">PowerShell cmdlet'lerini veya işlevleri çalıştırmak için Kullanıcıları yetkilendirmek için cmdlet veya işlev adı VisbibleCmdlets veya VisibleFunctions alanları ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a681e-140">To authorize users to run PowerShell cmdlets or functions, add the cmdlet or function name to the VisbibleCmdlets or VisibleFunctions fields.</span></span>
<span data-ttu-id="a681e-141">Bir cmdlet veya işlevi bir komut olup emin değilseniz, çalıştırabileceğiniz `Get-Command <name>` ve çıktıda "CommandType" özelliğini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="a681e-141">If you aren't sure whether a command is a cmdlet or function, you can run `Get-Command <name>` and check the "CommandType" property in the output.</span></span>

```powershell
VisibleCmdlets = 'Restart-Computer', 'Get-NetIPAddress'
```

<span data-ttu-id="a681e-142">Bazen belirli bir cmdlet veya işlev kapsamı için kullanıcılarınızın ihtiyaçlarını çok geniş olabilir.</span><span class="sxs-lookup"><span data-stu-id="a681e-142">Sometimes the scope of a specific cmdlet or function is too broad for your users' needs.</span></span>
<span data-ttu-id="a681e-143">Bir DNS Yöneticisi, örneğin, DNS hizmetini yeniden başlatmak için büyük olasılıkla yalnızca gereksinimlerini erişin.</span><span class="sxs-lookup"><span data-stu-id="a681e-143">A DNS admin, for example, probably only needs access to restart the DNS service.</span></span>
<span data-ttu-id="a681e-144">Burada, kiracılar Self Servis Yönetimi Araçları erişim izni verilen çok kiracılı ortam kiracılar ile kendi kaynaklarını yönetmek için sınırlı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a681e-144">In a multi-tenant environment where tenants are granted access to self-service management tools, tenants should be limited to managing with their own resources.</span></span>
<span data-ttu-id="a681e-145">Bu durumlarda cmdlet ya da işlev hangi parametreler sunulur kısıtlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a681e-145">For these cases, you can restrict which parameters are exposed from the cmdlet or function.</span></span>

```powershell

VisibleCmdlets = @{ Name = 'Restart-Computer'; Parameters = @{ Name = 'Name' }}

```

<span data-ttu-id="a681e-146">Daha gelişmiş senaryolarda, birisi sağlayabilirsiniz hangi değerlerin bu parametrelere sınırlamak gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="a681e-146">In more advanced scenarios, you may also need to restrict which values someone can supply to these parameters.</span></span>
<span data-ttu-id="a681e-147">Rol işlevleri izin verilen değerler ya da belirli bir giriş izin verilip verilmeyeceğini belirlemek için değerlendirilen bir normal ifade deseni kümesi tanımlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="a681e-147">Role capabilities let you define a set of allowed values or a regular expression pattern that is evaluated to determine if a given input is allowed.</span></span>

```powershell
VisibleCmdlets = @{ Name = 'Restart-Service'; Parameters = @{ Name = 'Name'; ValidateSet = 'Dns', 'Spooler' }},
                 @{ Name = 'Start-Website'; Parameters = @{ Name = 'Name'; ValidatePattern = 'HR_*' }}
```

> [!NOTE]
> <span data-ttu-id="a681e-148">[Ortak PowerShell parametrelerini](https://technet.microsoft.com/library/hh847884.aspx) kullanılabilir parametrelerin kısıtlama olsa bile her zaman izin verilir.</span><span class="sxs-lookup"><span data-stu-id="a681e-148">The [common PowerShell parameters](https://technet.microsoft.com/library/hh847884.aspx) are always allowed, even if you restrict the available parameters.</span></span>
> <span data-ttu-id="a681e-149">Siz açıkça bunları parametreler alanında listelenmemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="a681e-149">You should not explicitly list them in the Parameters field.</span></span>

<span data-ttu-id="a681e-150">Aşağıdaki tabloda görünür cmdlet'ini veya işlev özelleştirebilirsiniz çeşitli yolları açıklar.</span><span class="sxs-lookup"><span data-stu-id="a681e-150">The table below describes the various ways you can customize a visible cmdlet or function.</span></span>
<span data-ttu-id="a681e-151">Karışık ve hiçbiriyle aşağıda VisibleCmdlets alan.</span><span class="sxs-lookup"><span data-stu-id="a681e-151">You can mix and match any of the below in the VisibleCmdlets field.</span></span>

<span data-ttu-id="a681e-152">Örnek</span><span class="sxs-lookup"><span data-stu-id="a681e-152">Example</span></span>                                                                                      | <span data-ttu-id="a681e-153">Kullanım örneği</span><span class="sxs-lookup"><span data-stu-id="a681e-153">Use case</span></span>
---------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------
<span data-ttu-id="a681e-154">`'My-Func'` veya `@{ Name = 'My-Func' }`</span><span class="sxs-lookup"><span data-stu-id="a681e-154">`'My-Func'` or `@{ Name = 'My-Func' }`</span></span>                                                       | <span data-ttu-id="a681e-155">Çalıştırılacak verir `My-Func` parametreler üzerinde herhangi bir kısıtlama olmadan.</span><span class="sxs-lookup"><span data-stu-id="a681e-155">Allows the user to run `My-Func` without any restrictions on the parameters.</span></span>
`'MyModule\My-Func'`                                                                         | <span data-ttu-id="a681e-156">Çalıştırılacak verir `My-Func` modülünden `MyModule` parametreler üzerinde herhangi bir kısıtlama olmadan.</span><span class="sxs-lookup"><span data-stu-id="a681e-156">Allows the user to run `My-Func` from the module `MyModule` without any restrictions on the parameters.</span></span>
`'My-*'`                                                                                     | <span data-ttu-id="a681e-157">Herhangi bir cmdlet veya işlevi için fiili ile çalıştırmak kullanıcının `My`.</span><span class="sxs-lookup"><span data-stu-id="a681e-157">Allows the user to run any cmdlet or function with the verb `My`.</span></span>
`'*-Func'`                                                                                   | <span data-ttu-id="a681e-158">Herhangi bir cmdlet veya işlev isim ile çalıştırmak kullanıcının `Func`.</span><span class="sxs-lookup"><span data-stu-id="a681e-158">Allows the user to run any cmdlet or function with the noun `Func`.</span></span>
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'}, @{ Name = 'Param2' }}`               | <span data-ttu-id="a681e-159">Çalıştırılacak verir `My-Func` ile `Param1` ve/veya `Param2` parametreleri.</span><span class="sxs-lookup"><span data-stu-id="a681e-159">Allows the user to run `My-Func` with the `Param1` and/or `Param2` parameters.</span></span> <span data-ttu-id="a681e-160">Parametreleri herhangi bir değer sağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="a681e-160">Any value can be supplied to the parameters.</span></span>
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidateSet = 'Value1', 'Value2' }}`  | <span data-ttu-id="a681e-161">Çalıştırılacak verir `My-Func` ile `Param1` parametresi.</span><span class="sxs-lookup"><span data-stu-id="a681e-161">Allows the user to run `My-Func` with the `Param1` parameter.</span></span> <span data-ttu-id="a681e-162">Yalnızca "Value1" ve "Value2" parametresi sağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="a681e-162">Only "Value1" and "Value2" can be supplied to the parameter.</span></span>
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidatePattern = 'contoso.*' }}`     | <span data-ttu-id="a681e-163">Çalıştırılacak verir `My-Func` ile `Param1` parametresi.</span><span class="sxs-lookup"><span data-stu-id="a681e-163">Allows the user to run `My-Func` with the `Param1` parameter.</span></span> <span data-ttu-id="a681e-164">"Contoso" ile başlayan herhangi bir değer parametresi sağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="a681e-164">Any value starting with "contoso" can be supplied to the parameter.</span></span>


> [!WARNING]
> <span data-ttu-id="a681e-165">En iyi güvenlik uygulamaları bu joker karakterler görünür cmdlet'leri veya işlevlerini tanımlarken kullanmak için önerilmez.</span><span class="sxs-lookup"><span data-stu-id="a681e-165">For best security practices, it is not recommended to use wildcards when defining visible cmdlets or functions.</span></span>
> <span data-ttu-id="a681e-166">Bunun yerine, aynı adlandırma şeması paylaşan başka hiçbir komut istemeden yetkinizin olduğundan emin olmak için güvenilen her komut açıkça listelemelidir.</span><span class="sxs-lookup"><span data-stu-id="a681e-166">Instead, you should explicitly list each trusted command to ensure no other commands that share the same naming scheme are unintentionally authorized.</span></span>

<span data-ttu-id="a681e-167">Aynı cmdlet veya işlevi bir ValidatePattern ve ValidateSet uygulanamıyor.</span><span class="sxs-lookup"><span data-stu-id="a681e-167">You cannot apply both a ValidatePattern and ValidateSet to the same cmdlet or function.</span></span>

<span data-ttu-id="a681e-168">Bunu yaparsanız, ValidatePattern ValidateSet geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="a681e-168">If you do, the ValidatePattern will override the ValidateSet.</span></span>

<span data-ttu-id="a681e-169">ValidatePattern hakkında daha fazla bilgi için kullanıma [bu *Hey, Scripting Guy!* sonrası](https://blogs.technet.microsoft.com/heyscriptingguy/2011/01/11/validate-powershell-parameters-before-running-the-script/) ve [PowerShell normal ifadeler](https://technet.microsoft.com/library/hh847880.aspx) başvuru içeriği.</span><span class="sxs-lookup"><span data-stu-id="a681e-169">For more information about ValidatePattern, check out [this *Hey, Scripting Guy!* post](https://blogs.technet.microsoft.com/heyscriptingguy/2011/01/11/validate-powershell-parameters-before-running-the-script/) and the [PowerShell Regular Expressions](https://technet.microsoft.com/library/hh847880.aspx) reference content.</span></span>

### <a name="allowing-external-commands-and-powershell-scripts"></a><span data-ttu-id="a681e-170">Dış komutları ve PowerShell betiklerini izin verme</span><span class="sxs-lookup"><span data-stu-id="a681e-170">Allowing external commands and PowerShell scripts</span></span>

<span data-ttu-id="a681e-171">Bir JEA oturumda yürütülebilir dosyaları ve PowerShell betikleri (.ps1) çalıştırmak kullanıcılara izin vermek için VisibleExternalCommands alandaki her bir program için tam yolu eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a681e-171">To allow users to run executables and PowerShell scripts (.ps1) in a JEA session, you have to add the full path to each program in the VisibleExternalCommands field.</span></span>

```powershell
VisibleExternalCommands = 'C:\Windows\System32\whoami.exe', 'C:\Program Files\Contoso\Scripts\UpdateITSoftware.ps1'
```

<span data-ttu-id="a681e-172">Mümkünse, PowerShell cmdlet/işlevi eşdeğerleri parametreleri PowerShell cmdlet'leri/olan işlevlere izin üzerinde denetime sahip olduğundan, yetkilendirme dış yürütülebilir dosyaları kullanmak önerilir.</span><span class="sxs-lookup"><span data-stu-id="a681e-172">It is advised, where possible, to use PowerShell cmdlet/function equivalents of any external executables you authorize since you have control over which parameters are allowed with PowerShell cmdlets/functions.</span></span>

<span data-ttu-id="a681e-173">Birçok yürütülebilir dosyaları, hem geçerli durumu okuyun ve ardından farklı parametreler sağlayarak değiştirin olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="a681e-173">Many executables allow you to both read the current state and then change it just by providing different parameters.</span></span>

<span data-ttu-id="a681e-174">Örneğin, hangi ağ paylaşımlara yerel makine tarafından barındırılan denetlemek isteyen bir dosya sunucusu yöneticisi rolünü göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="a681e-174">For example, consider the role of a file server admin who wants to check which network shares are hosted by the local machine.</span></span>
<span data-ttu-id="a681e-175">Denetlenecek tek bir yolu `net share`.</span><span class="sxs-lookup"><span data-stu-id="a681e-175">One way to check is to use `net share`.</span></span>
<span data-ttu-id="a681e-176">Ancak, yönetici, yönetici ayrıcalıklarıyla elde etmek için komut kolayca kullanabilir olduğundan net.exe çok tehlikeli izin vererek `net group Administrators unprivilegedjeauser /add`.</span><span class="sxs-lookup"><span data-stu-id="a681e-176">However, allowing net.exe is very dangerous becuase the admin could just as easily use the command to gain admin privileges with `net group Administrators unprivilegedjeauser /add`.</span></span>
<span data-ttu-id="a681e-177">İzin vermek için daha iyi bir yaklaşım olan [Get-SmbShare](https://technet.microsoft.com/library/jj635704.aspx) aynı sonucu veren, ancak çok daha sınırlı kapsamı vardır.</span><span class="sxs-lookup"><span data-stu-id="a681e-177">A better approach is to allow [Get-SmbShare](https://technet.microsoft.com/library/jj635704.aspx) which achieves the same result but has a much more limited scope.</span></span>

<span data-ttu-id="a681e-178">Dış komutları kullanılabilir kullanıcılara bir JEA oturumda yaparken, her zaman başka bir sistem üzerinde yerleştirilen benzer ada (ve büyük olasılıkla malicous) programı yerine Yürütülmeyen emin olmak için yürütülebilir dosyanın tam yolunu belirtin.</span><span class="sxs-lookup"><span data-stu-id="a681e-178">When making external commands available to users in a JEA session, always specify the complete path to the executable to ensure a similarly named (and potentially malicous) program placed elsewhere on the system does not get executed instead.</span></span>

### <a name="allowing-access-to-powershell-providers"></a><span data-ttu-id="a681e-179">PowerShell sağlayıcıları için erişime izin verme</span><span class="sxs-lookup"><span data-stu-id="a681e-179">Allowing access to PowerShell providers</span></span>

<span data-ttu-id="a681e-180">Varsayılan olarak, PowerShell yok sağlayıcıları JEA oturumlarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a681e-180">By default, no PowerShell providers are available in JEA sessions.</span></span>

<span data-ttu-id="a681e-181">Bu hassas bilgiler ve yapılandırma ayarları için bağlanan kullanıcı ifşa riskini azaltmak için öncelikli olarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="a681e-181">This is primarily to reduce the risk of sensitive information and configuration settings being disclosed to the connecting user.</span></span>

<span data-ttu-id="a681e-182">Gerekli olduğunda kullanarak PowerShell sağlayıcılarının erişime izin verebilir `VisibleProviders` komutu.</span><span class="sxs-lookup"><span data-stu-id="a681e-182">When necessary, you can allow access to the PowerShell providers using the `VisibleProviders` command.</span></span>
<span data-ttu-id="a681e-183">Sağlayıcıları tam listesi için çalıştırma `Get-PSProvider`.</span><span class="sxs-lookup"><span data-stu-id="a681e-183">For a full list of providers, run `Get-PSProvider`.</span></span>

```powershell
VisibleProviders = 'Registry'
```

<span data-ttu-id="a681e-184">Dosya sistemi, kayıt defteri, sertifika deposu veya diğer hassas sağlayıcıları erişmesi Basit görevler için kullanıcı adına sağlayıcısı ile çalıştığından, özel bir işlev yazarken düşünebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a681e-184">For simple tasks that require access to the file system, registry, certificate store, or other sensitive providers, you can also consider writing a custom function that works with the provider on the user's behalf.</span></span>
<span data-ttu-id="a681e-185">İşlevler, cmdlet'leri ve JEA oturumunda kullanılabilir olan dış programları JEA olarak aynı kısıtlamalara tabi değildir; varsayılan olarak herhangi bir sağlayıcı erişebilir.</span><span class="sxs-lookup"><span data-stu-id="a681e-185">Functions, cmdlets, and external programs that are available in a JEA session are not subject to the same constraints as JEA -- they can access any provider by default.</span></span>
<span data-ttu-id="a681e-186">Ayrıca kullanmayı [kullanıcı sürücü](session-configurations.md#user-drive) zaman dosyaları kopyalamak için buralardan bir JEA uç noktası gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a681e-186">Also consider using the [user drive](session-configurations.md#user-drive) when copying files to/from a JEA endpoint is required.</span></span>

### <a name="creating-custom-functions"></a><span data-ttu-id="a681e-187">Özel bir işlev oluşturma</span><span class="sxs-lookup"><span data-stu-id="a681e-187">Creating custom functions</span></span>

<span data-ttu-id="a681e-188">Karmaşık görevleri, son kullanıcılarınız için basitleştirmek için bir rol özelliği dosyasındaki özel işlevler yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a681e-188">You can author custom functions in a role capability file to simplify complex tasks for your end users.</span></span>
<span data-ttu-id="a681e-189">Gelişmiş Doğrulama mantığı cmdlet'i parametre değerlerini gerektirdiğinde özel işlevler de yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="a681e-189">Custom functions are also useful when you require advanced validation logic for cmdlet parameter values.</span></span>
<span data-ttu-id="a681e-190">Basit işlevler yazabilirsiniz **FunctionDefinitions** alan:</span><span class="sxs-lookup"><span data-stu-id="a681e-190">You can write simple functions in the **FunctionDefinitions** field:</span></span>

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
> <span data-ttu-id="a681e-191">Özel işlevlerinizi adını eklemek unutmayın **VisibleFunctions** JEA kullanıcılar tarafından çalışma alanı.</span><span class="sxs-lookup"><span data-stu-id="a681e-191">Don't forget to add the name of your custom functions to the **VisibleFunctions** field so they can be run by the JEA users.</span></span>


<span data-ttu-id="a681e-192">Özel işlev gövdesi (betik bloğu) sistemi için varsayılan dil modda çalışır ve JEA'ın dil kısıtlamalarına tabi değildir.</span><span class="sxs-lookup"><span data-stu-id="a681e-192">The body (script block) of custom functions runs in the default language mode for the system and is not subject to JEA's language constraints.</span></span>
<span data-ttu-id="a681e-193">Bu işlevler dosya sistemi ve kayıt defteri erişebilir ve rol özelliği dosyasında görünür oluşturulmayan komutları çalıştırın, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a681e-193">This means that functions can access the file system and registry, and run commands that were not made visible in the role capability file.</span></span>
<span data-ttu-id="a681e-194">Rastgele kod parametrelerini kullanırken çalıştırılmasına izin vererek kaçınmak için dikkatli ve cmdlet'ler gibi doğrudan yöneltme kullanıcı girişini engellemek `Invoke-Expression`.</span><span class="sxs-lookup"><span data-stu-id="a681e-194">Take care to avoid allowing arbitrary code to be run when using parameters and avoid piping user input directly into cmdlets like `Invoke-Expression`.</span></span>

<span data-ttu-id="a681e-195">Yukarıdaki örnekte, görürsünüz (FQMN) tam modül adı `Microsoft.PowerShell.Utility\Select-Object` toplu yerine kullanılan `Select-Object`.</span><span class="sxs-lookup"><span data-stu-id="a681e-195">In the above example, you will notice that the fully qualified module name (FQMN) `Microsoft.PowerShell.Utility\Select-Object` was used instead of the shorthand `Select-Object`.</span></span>
<span data-ttu-id="a681e-196">Rol özelliği dosyalarında tanımlanan işlevleri proxy işlevleri içeren hala kapsamını JEA oturumları tabi olan mevcut komutları sınırlamak için JEA oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a681e-196">Functions defined in role capability files are still subject to the scope of JEA sessions, which includes the proxy functions JEA creates to constrain existing commands.</span></span>

<span data-ttu-id="a681e-197">Select-Object nesneler üzerinde isteğe bağlı özellikler seçmenizi izin vermeyen kısıtlanmış cmdlet'i tüm JEA oturumlarda bir varsayılan davranıştır.</span><span class="sxs-lookup"><span data-stu-id="a681e-197">Select-Object is a default, constrained cmdlet in all JEA sessions that doesn't allow you to select arbitrary properties on objects.</span></span>
<span data-ttu-id="a681e-198">Sınırlandırılmamış Select-Object işlevleri kullanmak için açıkça FQMN belirterek tam uygulamayı istemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a681e-198">To use the unconstrained Select-Object in functions, you must explicitly request the full implementation by specifying the FQMN.</span></span>
<span data-ttu-id="a681e-199">Bir JEA oturumda kısıtlanmış herhangi bir cmdlet'i PowerShell'in ayarlarına uygun olarak bir işlev çağrıldığında aynı davranışı sergiler [komut öncelik](https://msdn.microsoft.com/powershell/reference/3.0/microsoft.powershell.core/about/about_command_precedence).</span><span class="sxs-lookup"><span data-stu-id="a681e-199">Any constrained cmdlet in a JEA session will exhibit the same behavior when invoked from a function, in line with PowerShell's [command precedence](https://msdn.microsoft.com/powershell/reference/3.0/microsoft.powershell.core/about/about_command_precedence).</span></span>

<span data-ttu-id="a681e-200">Birçok özel işlev yazıyorsanız, bunları yerleştirmek daha kolay olabilir bir [PowerShell betik modülündeki](https://msdn.microsoft.com/library/dd878340(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="a681e-200">If you are writing a lot of custom functions, it may be easier to put them in a [PowerShell Script Module](https://msdn.microsoft.com/library/dd878340(v=vs.85).aspx).</span></span>
<span data-ttu-id="a681e-201">Daha sonra bu işlevleri yerleşik ve üçüncü taraf modülleriyle gibi VisibleFunctions alanını kullanarak JEA oturumdaki görünür yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a681e-201">You can then make those functions visible in the JEA session using the VisibleFunctions field like you would with built-in and third party modules.</span></span>

## <a name="place-role-capabilities-in-a-module"></a><span data-ttu-id="a681e-202">Rol işlevleri bir modülde yerleştirin</span><span class="sxs-lookup"><span data-stu-id="a681e-202">Place role capabilities in a module</span></span>

<span data-ttu-id="a681e-203">Bir rol özelliği dosyayı bulmak PowerShell sırada bir PowerShell modülü "RoleCapabilities" klasöründe depolanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a681e-203">In order for PowerShell to find a role capability file, it must be stored in a "RoleCapabilities" folder in a PowerShell module.</span></span>
<span data-ttu-id="a681e-204">Modül içindeki herhangi bir klasörde depolanan `$env:PSModulePath` ortam değişkeni, ancak System32 (yerleşik modülleri için ayrılmıştır) veya bir klasöre yerleştirmelisiniz değil burada güvenilmeyen, kullanıcıların bağlanma dosyaları değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="a681e-204">The module can be stored in any folder included in the `$env:PSModulePath` environment variable, however you should not place it in System32 (reserved for built-in modules) or a folder where the untrusted, connecting users could modify the files.</span></span>
<span data-ttu-id="a681e-205">Adlı temel bir PowerShell Betiği modülü oluşturma örneği aşağıda verilmiştir *ContosoJEA* "Program Files" yolda.</span><span class="sxs-lookup"><span data-stu-id="a681e-205">Below is an example of creating a basic PowerShell script module called *ContosoJEA* in the "Program Files" path.</span></span>

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

<span data-ttu-id="a681e-206">Bkz: [bir PowerShell modülü anlama](https://msdn.microsoft.com/library/dd878324.aspx) PowerShell modülleri, modül bildirimleri ve PSModulePath ortam değişkeni hakkında daha fazla bilgi.</span><span class="sxs-lookup"><span data-stu-id="a681e-206">See [Understanding a PowerShell Module](https://msdn.microsoft.com/library/dd878324.aspx) for more information about PowerShell modules, module manifests, and the PSModulePath environment variable.</span></span>

## <a name="updating-role-capabilities"></a><span data-ttu-id="a681e-207">Rol özellikleri güncelleştiriliyor</span><span class="sxs-lookup"><span data-stu-id="a681e-207">Updating role capabilities</span></span>


<span data-ttu-id="a681e-208">Değişiklikleri yalnızca Rol özelliği dosyasına kaydederek, bir rol özelliği dosyası herhangi bir zamanda güncelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a681e-208">You can update a role capability file at any time by simply saving changes to the role capability file.</span></span>
<span data-ttu-id="a681e-209">Rol özelliği güncelleştirildikten sonra kullanmaya yeni herhangi JEA oturumları düzeltilmiş özellikleri yansıtır.</span><span class="sxs-lookup"><span data-stu-id="a681e-209">Any new JEA sessions started after the role capability has been updated will reflect the revised capabilities.</span></span>

<span data-ttu-id="a681e-210">Rol özellikleri klasörüne erişimi denetleme bu kadar önemlidir nedeni budur.</span><span class="sxs-lookup"><span data-stu-id="a681e-210">This is why controlling access to the role capabilities folder is so important.</span></span>
<span data-ttu-id="a681e-211">Yalnızca yüksek oranda güvenilir Yöneticiler rolü dosyaları değiştirmek mümkün olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a681e-211">Only highly trusted administrators should be able to change role capability files.</span></span>
<span data-ttu-id="a681e-212">Güvenilmeyen bir kullanıcının rol özellik dosyaları değiştirebilirsiniz, bunlar kolayca kendilerini erişim cmdlet'leri için bunları ayrıcalıklarını yükseltmek izin verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a681e-212">If an untrusted user can change role capability files, they can easily give themselves access to cmdlets which allow them to elevate their privileges.</span></span>


<span data-ttu-id="a681e-213">Rol işlevleri erişimi kilitleme isteyen yöneticiler için yerel sistem içeren modüller ve rol özellik dosyaları okuma erişimi olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="a681e-213">For administrators looking to lock down access to the role capabilities, ensure Local System has read access to the role capability files and containing modules.</span></span>

## <a name="how-role-capabilities-are-merged"></a><span data-ttu-id="a681e-214">Rol işlevleri nasıl birleştirilir</span><span class="sxs-lookup"><span data-stu-id="a681e-214">How role capabilities are merged</span></span>

<span data-ttu-id="a681e-215">Kullanıcı rolü eşlemelerin bağlı olarak bir JEA oturumu girdikleri zaman birden çok rol özelliklere erişim verilebilir [oturum yapılandırma dosyası](session-configurations.md).</span><span class="sxs-lookup"><span data-stu-id="a681e-215">Users can be granted access to multiple role capabilities when they enter a JEA session depending on the role mappings in the [session configuration file](session-configurations.md).</span></span>
<span data-ttu-id="a681e-216">Bu durumda kullanıcıya vermek JEA çalışır *en esnek* herhangi bir rol tarafından izin verilen komutları kümesi.</span><span class="sxs-lookup"><span data-stu-id="a681e-216">When this happens, JEA tries to give the user the *most permissive* set of commands allowed by any of the roles.</span></span>

<span data-ttu-id="a681e-217">**VisibleCmdlets ve VisibleFunctions**</span><span class="sxs-lookup"><span data-stu-id="a681e-217">**VisibleCmdlets and VisibleFunctions**</span></span>

<span data-ttu-id="a681e-218">En karmaşık birleştirme mantığı, cmdlet'ler ve İşlevler, kendi parametreleri ve parametre değerlerini JEA içinde sınırlı olabilir etkiler.</span><span class="sxs-lookup"><span data-stu-id="a681e-218">The most complex merge logic affects cmdlets and functions, which can have their parameters and parameter values limited in JEA.</span></span>

<span data-ttu-id="a681e-219">Kurallar aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="a681e-219">The rules are as follows:</span></span>

1. <span data-ttu-id="a681e-220">Bir cmdlet yalnızca tek bir role görünür duruma getirildiyse, tüm geçerli parametresi kısıtlamalarıyla kullanıcıya görünür olacaktır.</span><span class="sxs-lookup"><span data-stu-id="a681e-220">If a cmdlet is only made visible in one role, it will be visible to the user with any applicable parameter constraints.</span></span>
2. <span data-ttu-id="a681e-221">Bir cmdlet birden fazla rolde görünür hale gelir ve her bir rolü cmdlet aynı kısıtlamalar varsa, cmdlet bu kısıtlamaları olan kullanıcıya görünür olacaktır.</span><span class="sxs-lookup"><span data-stu-id="a681e-221">If a cmdlet is made visible in more than one role, and each role has the same constraints on the cmdlet, the cmdlet will be visible to the user with those constraints.</span></span>
3. <span data-ttu-id="a681e-222">Bir cmdlet birden fazla rolde görünür hale gelir ve farklı bir dizi parametrenin her rolü sağlar, cmdlet ve her rol arasında tanımlanan parametrelerin tümü kullanıcıya görünür olacaktır.</span><span class="sxs-lookup"><span data-stu-id="a681e-222">If a cmdlet is made visible in more than one role, and each role allows a different set of parameters, the cmdlet and all of the parameters defined across every role will be visible to the user.</span></span> <span data-ttu-id="a681e-223">Bir rol parametreler üzerinde kısıtlama yoksa, tüm parametreleri izin verilir.</span><span class="sxs-lookup"><span data-stu-id="a681e-223">If one role doesn't have constraints on the parameters, all parameters will be allowed.</span></span>
4. <span data-ttu-id="a681e-224">Bir rol bir doğrulama kümesi veya bir cmdlet parametresi doğrulama desenini tanımlar ve diğer rol parametresi izin verir, ancak parametre değerlerini kısıtlamaz, doğrulama kümesi veya deseni yoksayılacak.</span><span class="sxs-lookup"><span data-stu-id="a681e-224">If one role defines a validate set or validate pattern for a cmdlet parameter, and the other role allows the parameter but does not constrain the parameter values, the validate set or pattern will be ignored.</span></span>
5. <span data-ttu-id="a681e-225">Doğrulama kümesi aynı cmdlet parametresi birden fazla rol için tanımlanmış olması durumunda, tüm doğrulama kümelerinden tüm değerleri izin verilir.</span><span class="sxs-lookup"><span data-stu-id="a681e-225">If a validate set is defined for the same cmdlet parameter in more than one role, all values from all validate sets will be allowed.</span></span>
6. <span data-ttu-id="a681e-226">Doğrulama düzeni için birden fazla rol aynı cmdlet parametresinde tanımlanmazsa, desenleri hiçbiriyle tüm değerlere izin verilir.</span><span class="sxs-lookup"><span data-stu-id="a681e-226">If a validate pattern is defined for the same cmdlet parameter in more than one role, any values that match any of the patterns will be allowed.</span></span>
7. <span data-ttu-id="a681e-227">Doğrulama kümesi bir veya daha fazla rollerinde tanımlanır ve başka bir rol aynı cmdlet parametresi için bir doğrulama deseni tanımlanır, doğrulama kümesi göz ardı edilir ve kalan doğrulama desenleri için kural (6) uygular.</span><span class="sxs-lookup"><span data-stu-id="a681e-227">If a validate set is defined in one or more roles, and a validate pattern is defined in another role for the same cmdlet parameter, the validate set is ignored and rule (6) applies to the remaining validate patterns.</span></span>

<span data-ttu-id="a681e-228">Rolleri bu kurallara göre nasıl birleştirilmiş bir örnek aşağıdadır:</span><span class="sxs-lookup"><span data-stu-id="a681e-228">Below is an example of how roles are merged according to these rules:</span></span>

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



<span data-ttu-id="a681e-229">**VisibleExternalCommands, VisibleAliases, VisibleProviders, ScriptsToProcess**</span><span class="sxs-lookup"><span data-stu-id="a681e-229">**VisibleExternalCommands, VisibleAliases, VisibleProviders, ScriptsToProcess**</span></span>

<span data-ttu-id="a681e-230">Diğer rol özellik dosyası tüm alanlar yalnızca izin verilen dış komutları, diğer adlar, sağlayıcıları ve başlatma komut dosyaları toplu kümesine eklenir.</span><span class="sxs-lookup"><span data-stu-id="a681e-230">All other fields in the role capability file are simply added to a cumulative set of allowable external commands, aliases, providers, and startup scripts.</span></span>
<span data-ttu-id="a681e-231">Komutu, diğer adı, sağlayıcı veya betik bir rol özelliği kullanılabilir JEA kullanıcılar için uygun olacaktır.</span><span class="sxs-lookup"><span data-stu-id="a681e-231">Any command, alias, provider, or script available in one role capability will be available to the JEA user.</span></span>

<span data-ttu-id="a681e-232">Bir sağlayıcıdan birleştirilmiş bir dizi emin olmak dikkatli olun rol özellik ve işlevleri/cmdlet'leri/komutları başka bir izin verme bağlanan kullanıcıların yanlışlıkla sistem kaynaklarına erişim.</span><span class="sxs-lookup"><span data-stu-id="a681e-232">Be careful to ensure that the combined set of providers from one role capability and cmdlets/functions/commands from another do not allow connecting users unintentional access to system resources.</span></span>
<span data-ttu-id="a681e-233">Örneğin, bir rol izin veriyorsa `Remove-Item` cmdlet ve diğer sağlar `FileSystem` sağlayıcısı olan bilgisayarınızda rastgele dosyalar silinirken bir JEA kullanıcının risk altında.</span><span class="sxs-lookup"><span data-stu-id="a681e-233">For example, if one role allows the `Remove-Item` cmdlet and another allows the `FileSystem` provider, you are at risk of a JEA user deleting arbitrary files on your computer.</span></span>
<span data-ttu-id="a681e-234">Kullanıcıların geçerli izinler tanımlama hakkında daha fazla bilgi bulunabilir [JEA konu denetim](audit-and-report.md).</span><span class="sxs-lookup"><span data-stu-id="a681e-234">Additional information about identifying users' effective permissions can be found in the [auditing JEA topic](audit-and-report.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="a681e-235">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="a681e-235">Next steps</span></span>

- [<span data-ttu-id="a681e-236">Oturum yapılandırma dosyası oluşturma</span><span class="sxs-lookup"><span data-stu-id="a681e-236">Create a session configuration file</span></span>](session-configurations.md)