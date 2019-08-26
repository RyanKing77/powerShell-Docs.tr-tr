---
ms.date: 07/10/2019
keywords: Jea, PowerShell, güvenlik
title: JEA’yı kullanma
ms.openlocfilehash: 8f3cc9186c61a2ae5b64eb3dc4f72ca83f1a58c5
ms.sourcegitcommit: e894ed833cef57967cdaf002f8c883f66864e836
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2019
ms.locfileid: "70017898"
---
# <a name="using-jea"></a><span data-ttu-id="f7153-103">JEA’yı kullanma</span><span class="sxs-lookup"><span data-stu-id="f7153-103">Using JEA</span></span>

<span data-ttu-id="f7153-104">Bu makalede, bir JEA uç noktası ile bağlantı kurmak için kullanabileceğiniz çeşitli yollar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f7153-104">This article describes the various ways you can connect to and use a JEA endpoint.</span></span>

## <a name="using-jea-interactively"></a><span data-ttu-id="f7153-105">JEA etkileşimli kullanma</span><span class="sxs-lookup"><span data-stu-id="f7153-105">Using JEA interactively</span></span>

<span data-ttu-id="f7153-106">JEA yapılandırmanızı test ediyorsanız veya kullanıcılar için basit görevleriniz varsa, JEA 'yı normal bir PowerShell Remoting oturumunda olduğu gibi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7153-106">If you're testing your JEA configuration or have simple tasks for users, you can use JEA the same way you would a regular PowerShell remoting session.</span></span> <span data-ttu-id="f7153-107">Karmaşık uzaktan iletişim görevleri için, [örtük uzaktan iletişim](#using-jea-with-implicit-remoting)kullanılması önerilir.</span><span class="sxs-lookup"><span data-stu-id="f7153-107">For complex remoting tasks, it's recommended to use [implicit remoting](#using-jea-with-implicit-remoting).</span></span> <span data-ttu-id="f7153-108">Örtük uzaktan iletişim, kullanıcıların veri nesneleriyle yerel olarak çalışmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="f7153-108">Implicit remoting allows users to operate with the data objects locally.</span></span>

<span data-ttu-id="f7153-109">JEA 'yı etkileşimli olarak kullanmak için şunlar gerekir:</span><span class="sxs-lookup"><span data-stu-id="f7153-109">To use JEA interactively, you need:</span></span>

- <span data-ttu-id="f7153-110">Bağlanmakta olduğunuz bilgisayarın adı (yerel makine olabilir)</span><span class="sxs-lookup"><span data-stu-id="f7153-110">The name of the computer you're connecting to (can be the local machine)</span></span>
- <span data-ttu-id="f7153-111">Bu bilgisayarda kayıtlı olan JEA uç noktasının adı</span><span class="sxs-lookup"><span data-stu-id="f7153-111">The name of the JEA endpoint registered on that computer</span></span>
- <span data-ttu-id="f7153-112">Bu bilgisayardaki JEA uç noktasına erişimi olan kimlik bilgileri</span><span class="sxs-lookup"><span data-stu-id="f7153-112">Credentials that have access to the JEA endpoint on that computer</span></span>

<span data-ttu-id="f7153-113">Bu bilgiler verildiğinde, [New-PSSession](/powershell/module/microsoft.powershell.core/New-PSSession) veya [ENTER-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) cmdlet 'lerini kullanarak bir Jea oturumu başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7153-113">Given that information, you can start a JEA session using the [New-PSSession](/powershell/module/microsoft.powershell.core/New-PSSession) or [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) cmdlets.</span></span>

```powershell
$nonAdminCred = Get-Credential
Enter-PSSession -ComputerName localhost -ConfigurationName JEAMaintenance -Credential $nonAdminCred
```

<span data-ttu-id="f7153-114">Geçerli Kullanıcı hesabının JEA uç noktasına erişimi varsa, **kimlik bilgisi** parametresini atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7153-114">If the current user account has access to the JEA endpoint, you can omit the **Credential** parameter.</span></span>

<span data-ttu-id="f7153-115">PowerShell istemi `[localhost]: PS>` , artık uzak Jea oturumu ile etkileşimde bulunabileceğinizi anlarsınız.</span><span class="sxs-lookup"><span data-stu-id="f7153-115">When the PowerShell prompt changes to `[localhost]: PS>` you know that you're now interacting with the remote JEA session.</span></span> <span data-ttu-id="f7153-116">Hangi komutların kullanılabilir `Get-Command` olduğunu denetlemek için komutunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7153-116">You can run `Get-Command` to check which commands are available.</span></span> <span data-ttu-id="f7153-117">Kullanılabilir parametrelerde veya izin verilen parametre değerlerinde herhangi bir kısıtlama olup olmadığını öğrenmek için yöneticinize başvurun.</span><span class="sxs-lookup"><span data-stu-id="f7153-117">Consult with your administrator to learn if there are any restrictions on the available parameters or allowed parameter values.</span></span>

<span data-ttu-id="f7153-118">JEA oturumlarının NoLanguage modunda çalışacağını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f7153-118">Remember, JEA sessions operate in NoLanguage mode.</span></span> <span data-ttu-id="f7153-119">Genellikle PowerShell 'i kullanmanın bazı yolları kullanılamayabilir.</span><span class="sxs-lookup"><span data-stu-id="f7153-119">Some of the ways you typically use PowerShell may not be available.</span></span> <span data-ttu-id="f7153-120">Örneğin, verileri depolamak veya cmdlet 'lerden döndürülen nesnelerde özellikleri incelemek için değişkenleri kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="f7153-120">For instance, you can't use variables to store data or inspect the properties on objects returned from cmdlets.</span></span> <span data-ttu-id="f7153-121">Aşağıdaki örnek, NoLanguage modunda çalışmak üzere aynı komutları almak için iki yaklaşımda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f7153-121">The following example shows two approaches to get the same commands to work in NoLanguage mode.</span></span>

```powershell
# Using variables is prohibited in NoLanguage mode. The following will not work:
# $vm = Get-VM -Name 'SQL01'
# Start-VM -VM $vm

# You can use pipes to pass data through to commands that accept input from the pipeline
Get-VM -Name 'SQL01' | Start-VM

# You can also wrap subcommands in parentheses and enter them inline as arguments
Start-VM -VM (Get-VM -Name 'SQL01')

# You can also use parameter sets that don't require extra data to be passed in
Start-VM -VMName 'SQL01'
```

<span data-ttu-id="f7153-122">Bu yaklaşımı zorlaştırtıran daha karmaşık komut çağırmaları için, [örtük uzaktan iletişim](#using-jea-with-implicit-remoting) kullanmayı veya ihtiyaç duyduğunuz işlevselliği sartıran [özel işlevler oluşturmayı](role-capabilities.md#creating-custom-functions) düşünün.</span><span class="sxs-lookup"><span data-stu-id="f7153-122">For more complex command invocations that make this approach difficult, consider using [implicit remoting](#using-jea-with-implicit-remoting) or [creating custom functions](role-capabilities.md#creating-custom-functions) that wrap the functionality you require.</span></span>

## <a name="using-jea-with-implicit-remoting"></a><span data-ttu-id="f7153-123">JEA 'yı örtük uzaktan iletişim ile kullanma</span><span class="sxs-lookup"><span data-stu-id="f7153-123">Using JEA with implicit remoting</span></span>

<span data-ttu-id="f7153-124">PowerShell, uzak bir makineden proxy cmdlet 'lerini içeri aktarmanızı ve yerel komutlardır gibi etkileşimde bulunmanızı sağlayan örtük bir uzaktan iletişim modeline sahiptir.</span><span class="sxs-lookup"><span data-stu-id="f7153-124">PowerShell has an implicit remoting model that lets you import proxy cmdlets from a remote machine and interact with them as if they were local commands.</span></span> <span data-ttu-id="f7153-125">Örtülü uzaktan iletişim bu **Hey, komut dosyası oluşturma** konusunda açıklanmaktadır!</span><span class="sxs-lookup"><span data-stu-id="f7153-125">Implicit remoting is explained in this **Hey, Scripting Guy!**</span></span> <span data-ttu-id="f7153-126">[blog gönderisi](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/).</span><span class="sxs-lookup"><span data-stu-id="f7153-126">[blog post](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/).</span></span>
<span data-ttu-id="f7153-127">Tam dil modunda JEA cmdlet 'leriyle çalışmanıza olanak sağladığından, JEA ile çalışırken örtük uzaktan iletişim yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="f7153-127">Implicit remoting is useful when working with JEA because it allows you to work with JEA cmdlets in a full language mode.</span></span> <span data-ttu-id="f7153-128">Bir JEA uç noktasına karşı görevleri otomatikleştirmek için sekme tamamlama, değişkenler, nesneleri işleme ve hatta yerel betikleri kullanma gibi işlemleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7153-128">You can use tab completion, variables, manipulate objects, and even use local scripts to automate tasks against a JEA endpoint.</span></span> <span data-ttu-id="f7153-129">Bir ara sunucu komutunu her çağırdığınızda, veriler uzak makinedeki JEA uç noktasına gönderilir ve burada yürütülür.</span><span class="sxs-lookup"><span data-stu-id="f7153-129">Anytime you invoke a proxy command, the data is sent to the JEA endpoint on the remote machine and executed there.</span></span>

<span data-ttu-id="f7153-130">Örtük uzaktan iletişim, cmdlet 'leri mevcut bir PowerShell oturumundan içeri aktararak işe yarar.</span><span class="sxs-lookup"><span data-stu-id="f7153-130">Implicit remoting works by importing cmdlets from an existing PowerShell session.</span></span> <span data-ttu-id="f7153-131">İsteğe bağlı olarak, her proxy cmdlet 'inin adını seçtiğiniz bir dizeyle önek olarak seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7153-131">You can optionally choose to prefix the nouns of each proxy cmdlet with a string of your choosing.</span></span> <span data-ttu-id="f7153-132">Ön ek, uzak sistem için olan komutları ayırt etmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="f7153-132">The prefix allows you to distinguish the commands that are for the remote system.</span></span> <span data-ttu-id="f7153-133">Yerel PowerShell oturumunuz süresince tüm proxy komutlarını içeren geçici bir betik modülü oluşturulur ve içeri aktarılır.</span><span class="sxs-lookup"><span data-stu-id="f7153-133">A temporary script module containing all the proxy commands is created and imported for the duration of your local PowerShell session.</span></span>

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Import the entire PSSession and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA'

# Invoke "Get-Command" on the remote JEA endpoint using the proxy cmdlet
Get-JEACommand
```

> [!IMPORTANT]
> <span data-ttu-id="f7153-134">Varsayılan JEA cmdlet 'lerinde kısıtlamalar nedeniyle bazı sistemler JEA oturumunun tamamını içeri aktaramayabilir.</span><span class="sxs-lookup"><span data-stu-id="f7153-134">Some systems may not be able to import an entire JEA session due to constraints in the default JEA cmdlets.</span></span> <span data-ttu-id="f7153-135">Bu sorunu gidermek için, yalnızca adlarını `-CommandName` parametresine açıkça ekleyerek Jea oturumundan ihtiyacınız olan komutları içeri aktarın.</span><span class="sxs-lookup"><span data-stu-id="f7153-135">To get around this, only import the commands you need from the JEA session by explicitly providing their names to the `-CommandName` parameter.</span></span> <span data-ttu-id="f7153-136">Gelecekteki bir güncelleştirme, etkilenen sistemlerdeki tüm JEA oturumlarını içeri aktarma sorununu ele alır.</span><span class="sxs-lookup"><span data-stu-id="f7153-136">A future update will address the issue with importing entire JEA sessions on affected systems.</span></span>

<span data-ttu-id="f7153-137">Varsayılan parametrelerde JEA kısıtlamaları nedeniyle JEA oturumunu içeri aktaramıyoruz, içeri aktarılan kümeden varsayılan komutları filtrelemek için aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="f7153-137">If you're unable to import a JEA session because of JEA constraints on the default parameters, follow the steps below to filter out the default commands from the imported set.</span></span> <span data-ttu-id="f7153-138">Gibi `Select-Object`komutları kullanmaya devam edebilirsiniz, ancak uzak Jea oturumundan içeri aktarıldığından, bilgisayarınızda yüklü olan yerel sürümü kullanmanız yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="f7153-138">You can continue use commands like `Select-Object`, but you'll just use the local version installed on your computer instead of the one imported from the remote JEA session.</span></span>

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Get a list of all the commands on the JEA endpoint
$commands = Invoke-Command -Session $jeasession -ScriptBlock { Get-Command }

# Filter out the default cmdlets
$jeaDefaultCmdlets = 'Clear-Host', 'Exit-PSSession', 'Get-Command', 'Get-FormatData', 'Get-Help', 'Measure-Object', 'Out-Default', 'Select-Object'
$filteredCommands = $commands.Name | Where-Object { $jeaDefaultCmdlets -notcontains $_ }

# Import only commands explicitly added in role capabilities and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA' -CommandName $filteredCommands
```

<span data-ttu-id="f7153-139">Ayrıca, [Export-PSSession](/powershell/microsoft.powershell.utility/Export-PSSession)kullanarak, proxy cmdlet 'lerini örtük uzaktan iletişim üzerinden kalıcı hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7153-139">You can also persist the proxied cmdlets from implicit remoting using [Export-PSSession](/powershell/microsoft.powershell.utility/Export-PSSession).</span></span>
<span data-ttu-id="f7153-140">Örtük uzaktan iletişim hakkında daha fazla bilgi için, [Import-PSSession](/powershell/microsoft.powershell.utility/import-pssession) ve [Import-Module](/powershell/microsoft.powershell.core/import-module)belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="f7153-140">For more information about implicit remoting, see the documentation for [Import-PSSession](/powershell/microsoft.powershell.utility/import-pssession) and [Import-Module](/powershell/microsoft.powershell.core/import-module).</span></span>

## <a name="using-jea-programmatically"></a><span data-ttu-id="f7153-141">JEA 'yı program aracılığıyla kullanma</span><span class="sxs-lookup"><span data-stu-id="f7153-141">Using JEA programmatically</span></span>

<span data-ttu-id="f7153-142">JEA Ayrıca otomasyon sistemlerinde ve şirket içi yardım masası uygulamaları ve Web siteleri gibi Kullanıcı uygulamalarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f7153-142">JEA can also be used in automation systems and in user applications, such as in-house helpdesk apps and websites.</span></span> <span data-ttu-id="f7153-143">Yaklaşım, kısıtlanmış PowerShell uç noktaları ile iletişim kuran uygulamalar oluşturma ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="f7153-143">The approach is the same as that for building apps that talk to unconstrained PowerShell endpoints.</span></span> <span data-ttu-id="f7153-144">Programın JEA tarafından uygulanan kısıtlamayla çalışacak şekilde tasarlandığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="f7153-144">Ensure the program is designed to work with limitation imposed by JEA.</span></span>

<span data-ttu-id="f7153-145">Basit, tek kapalı görevler için, komutları bir JEA oturumunda çalıştırmak için [Invoke-komutunu](/powershell/module/microsoft.powershell.core/invoke-command) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7153-145">For simple, one-off tasks, you can use [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) to run commands in a JEA session.</span></span>

```powershell
Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Process; Get-Service }
```

<span data-ttu-id="f7153-146">Jea oturumuna bağlanırken kullanılabilecek komutları denetlemek için, izin verilen parametreleri denetlemek üzere sonuçları çalıştırın `Get-Command` ve sonuçları yineleyin.</span><span class="sxs-lookup"><span data-stu-id="f7153-146">To check which commands are available for use when you connect to a JEA session, run `Get-Command` and iterate through the results to check for the allowed parameters.</span></span>

```powershell
$allowedCommands = Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Command }
$allowedCommands | Where-Object { $_.CommandType -in 'Function', 'Cmdlet' } | Format-Table Name, Parameters
```

<span data-ttu-id="f7153-147">Bir C# uygulama oluşturuyorsanız, bir [wsmanconnectionınfo](/dotnet/api/system.management.automation.runspaces.wsmanconnectioninfo) nesnesinde yapılandırma adını belirterek bir Jea oturumuna bağlanan bir PowerShell çalışma alanı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7153-147">If you're building a C# app, you can create a PowerShell runspace that connects to a JEA session by specifying the configuration name in a [WSManConnectionInfo](/dotnet/api/system.management.automation.runspaces.wsmanconnectioninfo) object.</span></span>

```csharp
// using System.Management.Automation;
var computerName = "SERVER01";
var configName   = "JEAMaintenance";
// See https://docs.microsoft.com/dotnet/api/system.management.automation.pscredential
var creds        = // create a PSCredential object here

WSManConnectionInfo connectionInfo = new WSManConnectionInfo(
    false,                 // Use SSL
    computerName,          // Computer name
    5985,                  // WSMan Port
    "/wsman",              // WSMan Path
                           // Connection URI with config name
    string.Format(CultureInfo.InvariantCulture, "http://schemas.microsoft.com/powershell/{0}", configName),
    creds);                // Credentials

// Now, use the connection info to create a runspace where you can run the commands
using (Runspace runspace = RunspaceFactory.CreateRunspace(connectionInfo))
{
    // Open the runspace
    runspace.Open();

    using (PowerShell ps = PowerShell.Create())
    {
        // Set the PowerShell object to use the JEA runspace
        ps.Runspace = runspace;

        // Now you can add and invoke commands
        ps.AddCommand("Get-Command");
        foreach (var result in ps.Invoke())
        {
            Console.WriteLine(result);
        }
    }

    // Close the runspace
    runspace.Close();
}
```

## <a name="using-jea-with-powershell-direct"></a><span data-ttu-id="f7153-148">JEA 'yı doğrudan PowerShell ile kullanma</span><span class="sxs-lookup"><span data-stu-id="f7153-148">Using JEA with PowerShell Direct</span></span>

<span data-ttu-id="f7153-149">Windows 10 ve Windows Server 2016 ' deki Hyper-V, Hyper-V yöneticilerinin sanal makineleri PowerShell ile yönetmesine olanak tanıyan, sanal ağ yapılandırması veya uzaktan yönetim ayarlarından bağımsız olarak [PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct)sunar. Makin.</span><span class="sxs-lookup"><span data-stu-id="f7153-149">Hyper-V in Windows 10 and Windows Server 2016 offers [PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct), a feature that allows Hyper-V administrators to manage virtual machines with PowerShell regardless of the network configuration or remote management settings on the virtual machine.</span></span>

<span data-ttu-id="f7153-150">VM 'nize sınırlı bir Hyper-V Yöneticisi erişimi sağlamak için, JEA ile PowerShell Direct kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7153-150">You can use PowerShell Direct with JEA to give a Hyper-V administrator limited access to your VM.</span></span>
<span data-ttu-id="f7153-151">Bu, sanal makinenizin ağ bağlantısını kaybettiyseniz ve ağ ayarlarını onarmak için bir veri merkezi yöneticisinin olması halinde yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="f7153-151">This can be useful if you lose network connectivity to your VM and need a datacenter admin to fix the network settings.</span></span>

<span data-ttu-id="f7153-152">JEA 'yı PowerShell Direct üzerinden kullanmak için ek yapılandırma gerekmez.</span><span class="sxs-lookup"><span data-stu-id="f7153-152">No additional configuration is required to use JEA over PowerShell Direct.</span></span> <span data-ttu-id="f7153-153">Ancak, sanal makine içinde çalışan konuk işletim sistemi Windows 10, Windows Server 2016 veya üzeri olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f7153-153">However, the guest operating system running inside the virtual machine must be Windows 10, Windows Server 2016, or higher.</span></span> <span data-ttu-id="f7153-154">Hyper-V Yöneticisi, PSRemoting cmdlet 'lerinde `-VMName` veya `-VMId` parametrelerini kullanarak Jea uç noktasına bağlanabilir:</span><span class="sxs-lookup"><span data-stu-id="f7153-154">The Hyper-V admin can connect to the JEA endpoint by using the `-VMName` or `-VMId` parameters on PSRemoting cmdlets:</span></span>

```powershell
# Entering a JEA session using PowerShell Direct when the VM name is unique
Enter-PSSession -VMName 'SQL01' -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'

# Entering a JEA session using PowerShell Direct using VM ids
$vm = Get-VM -VMName 'MyVM' | Select-Object -First 1
Enter-PSSession -VMId $vm.VMId -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'
```

<span data-ttu-id="f7153-155">System 'i bir Hyper-V Yöneticisi tarafından kullanılmak üzere yönetmek için gereken en düşük haklara sahip adanmış bir kullanıcı hesabı oluşturmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="f7153-155">It's recommended you create a dedicated user account with the minimum rights needed to manage the system for use by a Hyper-V administrator.</span></span> <span data-ttu-id="f7153-156">Ayrıcalıksız bir Kullanıcı, kısıtlı PowerShell kullanma dahil olmak üzere varsayılan olarak bir Windows makinesinde oturum açabilir.</span><span class="sxs-lookup"><span data-stu-id="f7153-156">Remember, even an unprivileged user can sign into a Windows machine by default, including using unconstrained PowerShell.</span></span> <span data-ttu-id="f7153-157">Bu sayede dosya sistemine gözatıp işletim sistemi ortamınız hakkında daha fazla bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7153-157">That allows them to browse the file system and learn more about your OS environment.</span></span> <span data-ttu-id="f7153-158">Hyper-V Yöneticisi 'ni kilitlemek ve onları yalnızca JEA ile PowerShell Direct kullanarak bir VM 'ye erişecek şekilde sınırlamak için, Hyper-V yöneticisinin JEA hesabına yerel oturum açma haklarını reddetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f7153-158">To lock down a Hyper-V administrator and limit them to only access a VM using PowerShell Direct with JEA, you must deny local logon rights to the Hyper-V admin's JEA account.</span></span>
