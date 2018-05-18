---
ms.date: 06/12/2017
keywords: jea, powershell, güvenlik
title: JEA’yı kullanma
ms.openlocfilehash: 891e4be4c3fadceeff5ede7ac5cab04a5f80e5c1
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
---
# <a name="using-jea"></a><span data-ttu-id="24950-103">JEA’yı kullanma</span><span class="sxs-lookup"><span data-stu-id="24950-103">Using JEA</span></span>

> <span data-ttu-id="24950-104">Uygulandığı öğe: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="24950-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="24950-105">Bu konuda bağlanmak ve JEA uç noktası kullan çeşitli yolları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="24950-105">This topic describes the various ways you can connect to and use a JEA endpoint.</span></span>

## <a name="using-jea-interactively"></a><span data-ttu-id="24950-106">JEA etkileşimli kullanma</span><span class="sxs-lookup"><span data-stu-id="24950-106">Using JEA interactively</span></span>

<span data-ttu-id="24950-107">JEA yapılandırmanızı test veya basit görevleri gerçekleştirmek kullanıcılar varsa, normal bir PowerShell uzaktan iletişim oturumu olduğu gibi JEA kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="24950-107">If you are testing your JEA configuration or have simple tasks for users to perform, you can use JEA the same way you would a regular PowerShell remoting session.</span></span>
<span data-ttu-id="24950-108">Kullanmak için önerilen karmaşık remoting görevlerde [örtük remoting](#using-jea-with-implicit-remoting) bunun yerine, kullanıcılarınız için kullanıcıların çalışır izin vererek kolaylaştırmak için veri yerel olarak nesneleri.</span><span class="sxs-lookup"><span data-stu-id="24950-108">For complex remoting tasks, it is recommended to use [implicit remoting](#using-jea-with-implicit-remoting) instead to make it easier for your users by allowing users to operate with the data objects locally.</span></span>

<span data-ttu-id="24950-109">JEA etkileşimli olarak kullanabilmek için gerekir:</span><span class="sxs-lookup"><span data-stu-id="24950-109">To use JEA interactively, you will need:</span></span>
- <span data-ttu-id="24950-110">Bağlandığınız bilgisayarın adını (yerel makine olabilir)</span><span class="sxs-lookup"><span data-stu-id="24950-110">The name of the computer you are connecting to (can be the local machine)</span></span>
- <span data-ttu-id="24950-111">Bu bilgisayarda kayıtlı JEA uç noktanın adı</span><span class="sxs-lookup"><span data-stu-id="24950-111">The name of the JEA endpoint registered on that computer</span></span>
- <span data-ttu-id="24950-112">JEA uç noktasına erişimi olan bilgisayarın kimlik bilgileri</span><span class="sxs-lookup"><span data-stu-id="24950-112">Credentials for the computer that have access to the JEA endpoint</span></span>

<span data-ttu-id="24950-113">Yandan, bu bilgileri ile JEA kullanarak oturum başlatabilirsiniz [New-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSSession) veya [Enter-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/enter-pssession).</span><span class="sxs-lookup"><span data-stu-id="24950-113">With that information in hand, you can start a JEA session using [New-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSSession) or [Enter-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/enter-pssession).</span></span>

```powershell
$nonAdminCred = Get-Credential
Enter-PSSession -ComputerName localhost -ConfigurationName JEAMaintenance -Credential $nonAdminCred
```

<span data-ttu-id="24950-114">Şu anda açtığınızdan içinde JEA uç noktası erişimi gibi bu hesap, atlayabilirsiniz varsa `-Credential` parametresi.</span><span class="sxs-lookup"><span data-stu-id="24950-114">If the account you're currently logged in as has access to the JEA endpoint, you can omit the `-Credential` parameter.</span></span>

<span data-ttu-id="24950-115">PowerShell yapılan değişiklikler, komut istemine `[localhost]: PS>` uzak JEA oturumla şimdi etkileşim bilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="24950-115">When the PowerShell prompt changes to `[localhost]: PS>` you will know that you are now interacting with the remote JEA session.</span></span>
<span data-ttu-id="24950-116">Çalıştırabilirsiniz `Get-Command` hangi komutlar kullanılabilir denetlemek için.</span><span class="sxs-lookup"><span data-stu-id="24950-116">You can run `Get-Command` to check which commands are available.</span></span>
<span data-ttu-id="24950-117">Kullanılabilir parametrelerin veya izin verilen parametre değerlerini herhangi bir kısıtlamanın varsa öğrenmek için yöneticinize danışın gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="24950-117">You will need to consult with your administrator to learn if there are any restrictions on the available parameters or allowable parameter values.</span></span>

<span data-ttu-id="24950-118">Genellikle powershell'den yollardan bazılarını kullanılabilir olmaması bir hatırlatma JEA oturumları NoLanguage modunda çalışır.</span><span class="sxs-lookup"><span data-stu-id="24950-118">As a reminder, JEA sessions operate in NoLanguage mode, so some of the ways you typically use PowerShell may not be available.</span></span>
<span data-ttu-id="24950-119">Örneğin, verileri depolamak veya cmdlet'leri döndürülen nesnelerin özelliklerini incelemek için değişkenleri kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="24950-119">For instance, you cannot use variables to store data or inspect the properties on objects returned from cmdlets.</span></span>
<span data-ttu-id="24950-120">Aşağıdaki örnekteki nasıl örnek bir PowerShell bugün kullanıyor olabileceğiniz ve aynı almak için iki yaklaşım komut NoLanguage modunda çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="24950-120">The below example shows an example of how you may be using PowerShell today, and two approaches to get the same command working in NoLanguage mode.</span></span>

```powershell
# Using variables in NoLanguage mode is disallowed, so the following will not work
# $vm = Get-VM -Name 'SQL01'
# Start-VM -VM $vm

# You can use pipes to pass data through to commands that accept input from the pipeline
Get-VM -Name 'SQL01' | Start-VM

# You can also wrap subcommands in parentheses and enter them inline as arguments
Start-VM -VM (Get-VM -Name 'SQL01')

# Better yet, use parameter sets that don't require extra data to be passed in when possible
Start-VM -VMName 'SQL01'
```

<span data-ttu-id="24950-121">Bu yaklaşım zorlaştırır daha karmaşık komut çağırmaları için kullanmayı [örtük remoting](#using-jea-with-implicit-remoting) veya [özel işlevler oluşturma](role-capabilities.md#creating-custom-functions) istediğiniz işlevselliği sarmalamak.</span><span class="sxs-lookup"><span data-stu-id="24950-121">For more complex command invocations that make this approach difficult, consider using [implicit remoting](#using-jea-with-implicit-remoting) or [creating custom functions](role-capabilities.md#creating-custom-functions) that wrap the functionality you desire.</span></span>

## <a name="using-jea-with-implicit-remoting"></a><span data-ttu-id="24950-122">JEA örtük remoting ile kullanma</span><span class="sxs-lookup"><span data-stu-id="24950-122">Using JEA with implicit remoting</span></span>

<span data-ttu-id="24950-123">PowerShell burada proxy cmdlet'leri uzak bir makineden yerel bilgisayarınızda içeri aktarabilir ve yerel komutları değilmiş gibi etkileşim bir alternatif uzaktan iletişim modelini destekler.</span><span class="sxs-lookup"><span data-stu-id="24950-123">PowerShell supports an alternative remoting model where you can import proxy cmdlets from a remote machine on your local computer and interact with them as if they were local commands.</span></span>
<span data-ttu-id="24950-124">Bu örtük remoting olarak adlandırılır ve iyi içinde açıklanan [bu *Hey, Scripting Guy!* blog gönderisi](https://blogs.technet.microsoft.com/heyscriptingguy/2013/09/08/remoting-the-implicit-way/).</span><span class="sxs-lookup"><span data-stu-id="24950-124">This is called implicit remoting, and is explained well in [this *Hey, Scripting Guy!* blog post](https://blogs.technet.microsoft.com/heyscriptingguy/2013/09/08/remoting-the-implicit-way/).</span></span>
<span data-ttu-id="24950-125">Örtük remoting JEA cmdlet'leri tam dil modunda çalışmasına izin verdiğinden JEA ile çalışırken, özellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="24950-125">Implicit remoting is particularly useful when working with JEA because it allows you to work with JEA cmdlets in a full language mode.</span></span>
<span data-ttu-id="24950-126">Bu sekme tamamlama, değişkenleri kullanın, nesneleri işlemek ve hatta daha kolay bir JEA uç noktası karşı otomatik hale getirmek için yerel betiklerini kullanın anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="24950-126">This means you can use tab completion, variables, manipulate objects, and even use local scripts to more easily automate against a JEA endpoint.</span></span>
<span data-ttu-id="24950-127">Proxy komutunu Çağır verdiğinizde, verileri uzak makinede JEA uç gönderilir ve orada yürütülen.</span><span class="sxs-lookup"><span data-stu-id="24950-127">Anytime you invoke a proxy command, the data will be sent to the JEA endpoint on the remote machine and executed there.</span></span>

<span data-ttu-id="24950-128">Örtük remoting cmdlet'leri varolan bir PowerShell oturumundan içeri aktararak çalışır.</span><span class="sxs-lookup"><span data-stu-id="24950-128">Implicit remoting works by importing cmdlets from an existing PowerShell session.</span></span>
<span data-ttu-id="24950-129">Ayrıca, her bir proxy cmdlet isimleri için uzak sistem komutlardır ayırt etmek seçtiğiniz bir dizeyle öneki isteğe bağlı olarak seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="24950-129">You can optionally choose to prefix the nouns of each proxy cmdlet with a string of your choosing to distinguish which commands are for the remote system.</span></span>
<span data-ttu-id="24950-130">Proxy komutların tümünü içeren bir geçici betik modülündeki oluşturulur ve yerel PowerShell oturumunuzun süresi için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="24950-130">A temporary script module containing all of the proxy commands will be created and can be used for the duration of your local PowerShell session.</span></span>

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Import the entire PSSession and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA'

# Invoke "Get-Command" on the remote JEA endpoint using the proxy cmdlet
Get-JEACommand
```

> [!IMPORTANT]
> <span data-ttu-id="24950-131">Bazı sistemler varsayılan JEA cmdlet'lerinde kısıtlamaları nedeniyle bir tüm JEA oturum almak mümkün olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="24950-131">Some systems may not be able to import an entire JEA session due to constraints in the default JEA cmdlets.</span></span>
> <span data-ttu-id="24950-132">Bu geçici bir çözüm bulmak için yalnızca ihtiyacınız komutları JEA oturumundan açıkça adlarını sağlayarak içeri `-CommandName` parametresi.</span><span class="sxs-lookup"><span data-stu-id="24950-132">To get around this, only import the commands you need from the JEA session by explicitly providing their names to the `-CommandName` parameter.</span></span>
> <span data-ttu-id="24950-133">Gelecekteki bir güncelleştirme, etkilenen sistemlerinde tüm JEA oturumları alma sorunu ele alınacaktır.</span><span class="sxs-lookup"><span data-stu-id="24950-133">A future update will address the issue with importing entire JEA sessions on affected systems.</span></span>

<span data-ttu-id="24950-134">Varsayılan JEA parametrelerindeki kısıtlamalar nedeniyle JEA oturumu alamıyor varsa, içeri aktarılan kümesinden varsayılan komutları filtrelemek için aşağıdaki adımları izleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="24950-134">If you are unable to import a JEA session due to constraints on the default JEA parameters, you can follow the steps below to filter out the default commands from the imported set.</span></span>
<span data-ttu-id="24950-135">Komutları gibi kullanmaya devam edersiniz `Select-Object` --yalnızca bilgisayarınızda yerine uzak bir JEA oturumunda yerel sürümünü kullanmanız.</span><span class="sxs-lookup"><span data-stu-id="24950-135">You will still be able to use commands like `Select-Object` -- you'll just use the local version installed on your computer instead of the remote one in the JEA session.</span></span>

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

<span data-ttu-id="24950-136">Örtük remoting kullanarak yönlendirilirken cmdlet'leri devam edebilir [Export-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/Export-PSSession).</span><span class="sxs-lookup"><span data-stu-id="24950-136">You can also persist the proxied cmdlets from implicit remoting using [Export-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/Export-PSSession).</span></span>
<span data-ttu-id="24950-137">Örtük remoting hakkında daha fazla bilgi için Yardım belgelerine kullanıma [alma-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/import-pssession) ve [Import-Module](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/import-module).</span><span class="sxs-lookup"><span data-stu-id="24950-137">For more information about implicit remoting, check out the help documentation for [Import-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/import-pssession) and [Import-Module](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/import-module).</span></span>

## <a name="using-jea-programatically"></a><span data-ttu-id="24950-138">JEA programlı şekilde kullanma</span><span class="sxs-lookup"><span data-stu-id="24950-138">Using JEA programatically</span></span>

<span data-ttu-id="24950-139">JEA, Otomasyon sistemleri ve şirket içi Yardım Masası uygulamaları ve web siteleri gibi kullanıcı uygulamaları kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="24950-139">JEA can also be used in automation systems and in user applications, such as in-house helpdesk apps and web sites.</span></span>
<span data-ttu-id="24950-140">Uygulamaları oluşturmaya yönelik Kısıtlanmamış PowerShell uç program JEA uzak oturumda çalışan komutlar sınırlama, farkında olmalıdır uyarısıyla ile iletişim kuran bir yaklaşım aynıdır.</span><span class="sxs-lookup"><span data-stu-id="24950-140">The approach is the same as that for building apps that talk to unconstrained PowerShell endpoints, with the caveat that the program should be aware that JEA is limiting the commands that can be run in the remote session.</span></span>

<span data-ttu-id="24950-141">Basit, tek seferlik görevler için kullanabileceğiniz [Invoke-Command](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/invoke-command) JEA kullanılarak bir komut kümesini çalıştırmak için.</span><span class="sxs-lookup"><span data-stu-id="24950-141">For simple, one-off tasks, you can use [Invoke-Command](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/invoke-command) to run a set of commands using JEA.</span></span>

```powershell
Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Process; Get-Service }
```

<span data-ttu-id="24950-142">JEA oturumuna bağlandığında, hangi komutların kullanılabilir denetlemek için çalıştırın `Get-Command` ve izin verilen parametrelerini denetlemek için sonuçları yinelemek.</span><span class="sxs-lookup"><span data-stu-id="24950-142">To check which commands are available for use when you connect to a JEA session, run `Get-Command` and iterate through the results to check for the allowed parameters.</span></span>

```powershell
$allowedCommands = Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Command }
$allowedCommands | Where-Object { $_.CommandType -in 'Function', 'Cmdlet' } | Format-Table Name, Parameters
```

<span data-ttu-id="24950-143">Bir C# uygulaması oluşturuyorsanız, yapılandırma adı ile belirterek JEA oturumuna bağlandığında bir PowerShell çalışma oluşturabileceğiniz bir [WSManConnectionInfo](https://msdn.microsoft.com/en-us/library/system.management.automation.runspaces.wsmanconnectioninfo(v=vs.85).aspx) nesnesi.</span><span class="sxs-lookup"><span data-stu-id="24950-143">If you are building a C# app, you can create a PowerShell runspace that connects to a JEA session by specifying the configuration name in a [WSManConnectionInfo](https://msdn.microsoft.com/en-us/library/system.management.automation.runspaces.wsmanconnectioninfo(v=vs.85).aspx) object.</span></span>

```csharp

// using System.Management.Automation;
var computerName = "SERVER01";
var configName   = "JEAMaintenance";
var creds        = // create a PSCredential object here (https://msdn.microsoft.com/en-us/library/system.management.automation.pscredential(v=vs.85).aspx)

WSManConnectionInfo connectionInfo = new WSManConnectionInfo(
                    false,                 // Use SSL
                    computerName,          // Computer name
                    5985,                  // WSMan Port
                    "/wsman",              // WSMan Path
                    string.Format(CultureInfo.InvariantCulture, "http://schemas.microsoft.com/powershell/{0}", configName),  // Connection URI with config name
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

## <a name="using-jea-with-powershell-direct"></a><span data-ttu-id="24950-144">JEA PowerShell Direct ile kullanma</span><span class="sxs-lookup"><span data-stu-id="24950-144">Using JEA with PowerShell Direct</span></span>

<span data-ttu-id="24950-145">Hyper-V Windows 10 ve Windows Server 2016 sunar [PowerShell doğrudan](https://msdn.microsoft.com/en-us/virtualization/hyperv_on_windows/user_guide/vmsession), ağ yapılandırması veya uzaktan yönetim bağımsız olarak PowerShell ile sanal makineleri yönetmek Hyper-V yöneticileri sağlayan bir özellik Sanal makinedeki ayarları.</span><span class="sxs-lookup"><span data-stu-id="24950-145">Hyper-V in Windows 10 and Windows Server 2016 offers [PowerShell Direct](https://msdn.microsoft.com/en-us/virtualization/hyperv_on_windows/user_guide/vmsession), a feature which allows Hyper-V administrators to manage virtual machines with PowerShell regardless of the network configuration or remote management settings on the virtual machine.</span></span>

<span data-ttu-id="24950-146">VM'nize ağ bağlantısını kaybedebilir ve ağ ayarlarını düzeltmek için bir veri merkezi yönetim ihtiyacınız varsa yararlı olabilen, VM için bir Hyper-V sınırlı yönetici erişimi vermek için PowerShell doğrudan JEA ile kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="24950-146">You can use PowerShell Direct with JEA to give a Hyper-V administrator limited access to your VM, which can be useful if you lose network connectivity to your VM and need a datacenter admin to fix the network settings.</span></span>

<span data-ttu-id="24950-147">Sanal makinede çalışan işletim sistemini Windows 10 veya Windows Server 2016 olmalıdır ancak ek yapılandırma PowerShell doğrudan JEA kullanmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="24950-147">No additional configuration is required to use JEA over PowerShell Direct, however the operating system running inside the virtual machine must be Windows 10 or Windows Server 2016.</span></span>
<span data-ttu-id="24950-148">Hyper-V Yöneticisi kullanarak JEA uç noktasına bağlanabilir `-VMName` veya `-VMId` PSRemoting cmdlet'ler Parametreler:</span><span class="sxs-lookup"><span data-stu-id="24950-148">The Hyper-V admin can connect to the JEA endpoint by using the `-VMName` or `-VMId` parameters on PSRemoting cmdlets:</span></span>

```powershell
# Entering a JEA session using PowerShell Direct when the VM name is unique
Enter-PSSession -VMName 'SQL01' -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'

# Entering a JEA session using PowerShell Direct using VM ids
$vm = Get-VM -VMName 'MyVM' | Select-Object -First 1
Enter-PSSession -VMId $vm.VMId -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'
```

<span data-ttu-id="24950-149">Kullanmak, Hyper-V yöneticileri için sistemi yönetmek için başka haklara sahip ayrılmış yerel bir kullanıcı oluşturmak önerilir.</span><span class="sxs-lookup"><span data-stu-id="24950-149">It is strongly recommended that you create a dedicated local user with no other rights to manage the system for your Hyper-V administrators to use.</span></span>
<span data-ttu-id="24950-150">Kısıtlanmamış PowerShell kullanarak da dahil olmak üzere varsayılan olarak, bir Windows makinesine, ayrıcalıksız bir kullanıcı hala bağlanabilir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="24950-150">Remember that even an unprivileged user can still log into a Windows machine by default, including using unconstrained PowerShell.</span></span>
<span data-ttu-id="24950-151">İzin verin (bazıları) göz atmak dosya sistemini ve OS ortamınız hakkında daha fazla bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="24950-151">That will allow them to browse (some of) the file system and learn more about your OS environment.</span></span>
<span data-ttu-id="24950-152">Yalnızca PowerShell doğrudan JEA ile kullanarak bir VM'i erişmek için bir Hyper-V Yöneticisi kilitlemek için Hyper-V yöneticisinin JEA hesabın yerel oturum açma hakları Reddet gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="24950-152">To lock down a Hyper-V administrator to only access a VM using PowerShell Direct with JEA, you will need to deny local logon rights to the Hyper-V admin's JEA account.</span></span>