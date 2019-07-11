---
ms.date: 07/10/2019
keywords: jea, powershell, güvenlik
title: JEA’yı kullanma
ms.openlocfilehash: 8f3cc9186c61a2ae5b64eb3dc4f72ca83f1a58c5
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734225"
---
# <a name="using-jea"></a><span data-ttu-id="e582b-103">JEA’yı kullanma</span><span class="sxs-lookup"><span data-stu-id="e582b-103">Using JEA</span></span>

<span data-ttu-id="e582b-104">Bu makalede çeşitli şekillerde bağlanmak ve bir JEA uç noktası kullanma.</span><span class="sxs-lookup"><span data-stu-id="e582b-104">This article describes the various ways you can connect to and use a JEA endpoint.</span></span>

## <a name="using-jea-interactively"></a><span data-ttu-id="e582b-105">JEA etkileşimli kullanma</span><span class="sxs-lookup"><span data-stu-id="e582b-105">Using JEA interactively</span></span>

<span data-ttu-id="e582b-106">Jea'yı yapılandırmanızı test ettiğiniz veya kullanıcılar için basit görevler varsa, normal bir PowerShell uzaktan iletişimini oturumu olduğu gibi JEA kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e582b-106">If you're testing your JEA configuration or have simple tasks for users, you can use JEA the same way you would a regular PowerShell remoting session.</span></span> <span data-ttu-id="e582b-107">Görevler karmaşık uzaktan iletişim için kullanılacak önerilir [örtük uzak iletişim](#using-jea-with-implicit-remoting).</span><span class="sxs-lookup"><span data-stu-id="e582b-107">For complex remoting tasks, it's recommended to use [implicit remoting](#using-jea-with-implicit-remoting).</span></span> <span data-ttu-id="e582b-108">Örtük uzak iletişim, kullanıcıların yerel olarak veri nesneleriyle çalışmaya sağlar.</span><span class="sxs-lookup"><span data-stu-id="e582b-108">Implicit remoting allows users to operate with the data objects locally.</span></span>

<span data-ttu-id="e582b-109">JEA etkileşimli olarak kullanabilmek için gerekir:</span><span class="sxs-lookup"><span data-stu-id="e582b-109">To use JEA interactively, you need:</span></span>

- <span data-ttu-id="e582b-110">Bağlanmakta olduğunuz bilgisayarın adını (yerel makine olabilir)</span><span class="sxs-lookup"><span data-stu-id="e582b-110">The name of the computer you're connecting to (can be the local machine)</span></span>
- <span data-ttu-id="e582b-111">Bu bilgisayarda kayıtlı bir JEA uç nokta adı</span><span class="sxs-lookup"><span data-stu-id="e582b-111">The name of the JEA endpoint registered on that computer</span></span>
- <span data-ttu-id="e582b-112">Bu bilgisayar üzerinde JEA uç noktasına erişimi olan kimlik bilgileri</span><span class="sxs-lookup"><span data-stu-id="e582b-112">Credentials that have access to the JEA endpoint on that computer</span></span>

<span data-ttu-id="e582b-113">Bu bilgiler verildiğinde, JEA oturumu kullanmaya başlayabilirsiniz [New-PSSession](/powershell/module/microsoft.powershell.core/New-PSSession) veya [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) cmdlet'leri.</span><span class="sxs-lookup"><span data-stu-id="e582b-113">Given that information, you can start a JEA session using the [New-PSSession](/powershell/module/microsoft.powershell.core/New-PSSession) or [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) cmdlets.</span></span>

```powershell
$nonAdminCred = Get-Credential
Enter-PSSession -ComputerName localhost -ConfigurationName JEAMaintenance -Credential $nonAdminCred
```

<span data-ttu-id="e582b-114">Geçerli kullanıcı hesabı erişimi JEA uç noktası varsa, atlayabilirsiniz **kimlik bilgisi** parametresi.</span><span class="sxs-lookup"><span data-stu-id="e582b-114">If the current user account has access to the JEA endpoint, you can omit the **Credential** parameter.</span></span>

<span data-ttu-id="e582b-115">Ne zaman PowerShell istemi değişiklikleri `[localhost]: PS>` uzak JEA oturumla artık etkileşim bildirin.</span><span class="sxs-lookup"><span data-stu-id="e582b-115">When the PowerShell prompt changes to `[localhost]: PS>` you know that you're now interacting with the remote JEA session.</span></span> <span data-ttu-id="e582b-116">Çalıştırabileceğiniz `Get-Command` hangi komutları kullanılabilir denetlemek için.</span><span class="sxs-lookup"><span data-stu-id="e582b-116">You can run `Get-Command` to check which commands are available.</span></span> <span data-ttu-id="e582b-117">Kullanılabilir parametrelerin veya izin verilen parametre değerleri herhangi bir kısıtlama olup olmadığını öğrenmek için sistem yöneticinize başvurun.</span><span class="sxs-lookup"><span data-stu-id="e582b-117">Consult with your administrator to learn if there are any restrictions on the available parameters or allowed parameter values.</span></span>

<span data-ttu-id="e582b-118">Unutmayın, JEA oturumları NoLanguage modunda çalışır.</span><span class="sxs-lookup"><span data-stu-id="e582b-118">Remember, JEA sessions operate in NoLanguage mode.</span></span> <span data-ttu-id="e582b-119">Genellikle PowerShell kullanma yollarından bazıları kullanılamayabilir.</span><span class="sxs-lookup"><span data-stu-id="e582b-119">Some of the ways you typically use PowerShell may not be available.</span></span> <span data-ttu-id="e582b-120">Örneğin, veri depolamak veya cmdlet'lerinden döndürülen nesne özellikleri incelemek için değişkenler kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="e582b-120">For instance, you can't use variables to store data or inspect the properties on objects returned from cmdlets.</span></span> <span data-ttu-id="e582b-121">Aşağıdaki örnekte NoLanguage modda aynı komutları almak için iki yaklaşım gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e582b-121">The following example shows two approaches to get the same commands to work in NoLanguage mode.</span></span>

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

<span data-ttu-id="e582b-122">Bu yaklaşım zorlaştıran daha karmaşık komut çağrıları için kullanmayı [örtük uzak iletişim](#using-jea-with-implicit-remoting) veya [özel işlevler oluşturma](role-capabilities.md#creating-custom-functions) gereksinim duyduğunuz işleve kaydır.</span><span class="sxs-lookup"><span data-stu-id="e582b-122">For more complex command invocations that make this approach difficult, consider using [implicit remoting](#using-jea-with-implicit-remoting) or [creating custom functions](role-capabilities.md#creating-custom-functions) that wrap the functionality you require.</span></span>

## <a name="using-jea-with-implicit-remoting"></a><span data-ttu-id="e582b-123">Jea'yı örtük uzak iletişim ile kullanma</span><span class="sxs-lookup"><span data-stu-id="e582b-123">Using JEA with implicit remoting</span></span>

<span data-ttu-id="e582b-124">PowerShell proxy cmdlet'leri uzak bir makineden içeri aktarma ve komutları yerel olarak bulunuyorlarmış etkileşime olanak tanıyan bir örtük uzaktan modeline sahiptir.</span><span class="sxs-lookup"><span data-stu-id="e582b-124">PowerShell has an implicit remoting model that lets you import proxy cmdlets from a remote machine and interact with them as if they were local commands.</span></span> <span data-ttu-id="e582b-125">Örtük uzak iletişim, bu konuda açıklanmıştır **Hey, Scripting Guy!**</span><span class="sxs-lookup"><span data-stu-id="e582b-125">Implicit remoting is explained in this **Hey, Scripting Guy!**</span></span> <span data-ttu-id="e582b-126">[blog gönderisi](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/).</span><span class="sxs-lookup"><span data-stu-id="e582b-126">[blog post](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/).</span></span>
<span data-ttu-id="e582b-127">Örtük uzak iletişim JEA cmdlet'leri tam dil modunda çalışmasına izin verdiğinden JEA ile çalışırken yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="e582b-127">Implicit remoting is useful when working with JEA because it allows you to work with JEA cmdlets in a full language mode.</span></span> <span data-ttu-id="e582b-128">Sekme tamamlama, değişkenleri kullanın, nesnelerini işleyin ve bile bir JEA uç noktası karşı görevleri otomatik hale getirmek için yerel betiklerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="e582b-128">You can use tab completion, variables, manipulate objects, and even use local scripts to automate tasks against a JEA endpoint.</span></span> <span data-ttu-id="e582b-129">Bir ara sunucu komutu çağırmak her zaman, veriler uzak makinede JEA uç noktasına gönderilen ve yürütülen vardır.</span><span class="sxs-lookup"><span data-stu-id="e582b-129">Anytime you invoke a proxy command, the data is sent to the JEA endpoint on the remote machine and executed there.</span></span>

<span data-ttu-id="e582b-130">Örtük uzak iletişim cmdlet'leri var olan bir PowerShell oturumundan içeri aktararak çalışır.</span><span class="sxs-lookup"><span data-stu-id="e582b-130">Implicit remoting works by importing cmdlets from an existing PowerShell session.</span></span> <span data-ttu-id="e582b-131">Ayrıca, her proxy cmdlet isimleri, seçtiğiniz bir dize ile ön ek isteğe bağlı olarak seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e582b-131">You can optionally choose to prefix the nouns of each proxy cmdlet with a string of your choosing.</span></span> <span data-ttu-id="e582b-132">Önek uzak sistemdeki komutları ayırt etmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e582b-132">The prefix allows you to distinguish the commands that are for the remote system.</span></span> <span data-ttu-id="e582b-133">Tüm proxy komutları içeren bir geçici betik modülü oluşturulur ve yerel PowerShell oturumunuzda süresince içeri aktarıldı.</span><span class="sxs-lookup"><span data-stu-id="e582b-133">A temporary script module containing all the proxy commands is created and imported for the duration of your local PowerShell session.</span></span>

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Import the entire PSSession and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA'

# Invoke "Get-Command" on the remote JEA endpoint using the proxy cmdlet
Get-JEACommand
```

> [!IMPORTANT]
> <span data-ttu-id="e582b-134">Bazı sistemler, tüm bir JEA oturumu varsayılan JEA cmdlet'lerinde kısıtlamaları nedeniyle içeri aktarmak mümkün olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="e582b-134">Some systems may not be able to import an entire JEA session due to constraints in the default JEA cmdlets.</span></span> <span data-ttu-id="e582b-135">Bu sorunu aşmak için yalnızca ihtiyacınız olacak komutların JEA oturumundan açıkça adlarını sağlayarak içeri `-CommandName` parametresi.</span><span class="sxs-lookup"><span data-stu-id="e582b-135">To get around this, only import the commands you need from the JEA session by explicitly providing their names to the `-CommandName` parameter.</span></span> <span data-ttu-id="e582b-136">Gelecekte yapılacak bir güncelleştirmenin etkilenen sistemlerinde tüm JEA oturumları alma sorunu ele alınacaktır.</span><span class="sxs-lookup"><span data-stu-id="e582b-136">A future update will address the issue with importing entire JEA sessions on affected systems.</span></span>

<span data-ttu-id="e582b-137">Bir JEA oturumu varsayılan parametrelerindeki JEA kısıtlamalar nedeniyle içeri aktarma yapamıyorsanız, içeri aktarılan kümesinden varsayılan komutları filtrelemek için aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="e582b-137">If you're unable to import a JEA session because of JEA constraints on the default parameters, follow the steps below to filter out the default commands from the imported set.</span></span> <span data-ttu-id="e582b-138">Gibi kullanım komutlar devam `Select-Object`, ancak yalnızca uzak JEA oturumundan içeri aktarılmış bir yerine bilgisayarınızda yüklü yerel sürümünü kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e582b-138">You can continue use commands like `Select-Object`, but you'll just use the local version installed on your computer instead of the one imported from the remote JEA session.</span></span>

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

<span data-ttu-id="e582b-139">Örtük uzak iletişim kullanarak proxy cmdlet'leri de kalıcı yapılabilir [Export-PSSession](/powershell/microsoft.powershell.utility/Export-PSSession).</span><span class="sxs-lookup"><span data-stu-id="e582b-139">You can also persist the proxied cmdlets from implicit remoting using [Export-PSSession](/powershell/microsoft.powershell.utility/Export-PSSession).</span></span>
<span data-ttu-id="e582b-140">Örtük uzak iletişim hakkında daha fazla bilgi için belgelere bakın [Import-PSSession](/powershell/microsoft.powershell.utility/import-pssession) ve [Import-Module](/powershell/microsoft.powershell.core/import-module).</span><span class="sxs-lookup"><span data-stu-id="e582b-140">For more information about implicit remoting, see the documentation for [Import-PSSession](/powershell/microsoft.powershell.utility/import-pssession) and [Import-Module](/powershell/microsoft.powershell.core/import-module).</span></span>

## <a name="using-jea-programmatically"></a><span data-ttu-id="e582b-141">JEA programlı olarak kullanma</span><span class="sxs-lookup"><span data-stu-id="e582b-141">Using JEA programmatically</span></span>

<span data-ttu-id="e582b-142">JEA Otomasyon sistemleri ve şirket içi Yardım Masası uygulamaları ve Web siteleri gibi kullanıcı uygulamaları içinde de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e582b-142">JEA can also be used in automation systems and in user applications, such as in-house helpdesk apps and websites.</span></span> <span data-ttu-id="e582b-143">Aynı sınırlandırılmamış PowerShell uç noktalar ile iletişim kurmasına uygulama oluşturmaya yönelik bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="e582b-143">The approach is the same as that for building apps that talk to unconstrained PowerShell endpoints.</span></span> <span data-ttu-id="e582b-144">Program JEA tarafından uygulanan bir kısıtlama olmaksızın çalışacak şekilde tasarlandığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="e582b-144">Ensure the program is designed to work with limitation imposed by JEA.</span></span>

<span data-ttu-id="e582b-145">Basit, tek seferlik görevler için kullanabileceğiniz [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) JEA oturumunda komutları çalıştırmak için.</span><span class="sxs-lookup"><span data-stu-id="e582b-145">For simple, one-off tasks, you can use [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) to run commands in a JEA session.</span></span>

```powershell
Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Process; Get-Service }
```

<span data-ttu-id="e582b-146">Bir JEA oturumuna bağlandığında, hangi komutları kullanılabilir olup olmadığını denetlemek için çalıştırın `Get-Command` ve denetlemek için izin verilen parametre sonuçları arasında gezinin.</span><span class="sxs-lookup"><span data-stu-id="e582b-146">To check which commands are available for use when you connect to a JEA session, run `Get-Command` and iterate through the results to check for the allowed parameters.</span></span>

```powershell
$allowedCommands = Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Command }
$allowedCommands | Where-Object { $_.CommandType -in 'Function', 'Cmdlet' } | Format-Table Name, Parameters
```

<span data-ttu-id="e582b-147">Derliyorsanız bir C# uygulama, yapılandırma adı belirterek bir JEA oturumuna bağlandığında bir PowerShell çalışma alanı oluşturabilirsiniz bir [WSManConnectionInfo](/dotnet/api/system.management.automation.runspaces.wsmanconnectioninfo) nesne.</span><span class="sxs-lookup"><span data-stu-id="e582b-147">If you're building a C# app, you can create a PowerShell runspace that connects to a JEA session by specifying the configuration name in a [WSManConnectionInfo](/dotnet/api/system.management.automation.runspaces.wsmanconnectioninfo) object.</span></span>

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

## <a name="using-jea-with-powershell-direct"></a><span data-ttu-id="e582b-148">Jea'yı PowerShell Direct ile kullanma</span><span class="sxs-lookup"><span data-stu-id="e582b-148">Using JEA with PowerShell Direct</span></span>

<span data-ttu-id="e582b-149">Windows 10 ve Windows Server 2016 Hyper-V sunar [PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct), Hyper-V ağ yapılandırması veya uzaktan yönetim bakılmaksızın PowerShell ile sanal makineleri yönetme olanağı sağlayan bir özelliği sanal makine ayarları.</span><span class="sxs-lookup"><span data-stu-id="e582b-149">Hyper-V in Windows 10 and Windows Server 2016 offers [PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct), a feature that allows Hyper-V administrators to manage virtual machines with PowerShell regardless of the network configuration or remote management settings on the virtual machine.</span></span>

<span data-ttu-id="e582b-150">Sanal makinenizde bir Hyper-V sınırlı yönetici erişimi vermek için PowerShell Direct ile JEA kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e582b-150">You can use PowerShell Direct with JEA to give a Hyper-V administrator limited access to your VM.</span></span>
<span data-ttu-id="e582b-151">Sanal makinenizde ağ bağlantısı kaybı ve ağ ayarları düzeltmek için bir veri merkezi yönetim gerekiyorsa bu yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="e582b-151">This can be useful if you lose network connectivity to your VM and need a datacenter admin to fix the network settings.</span></span>

<span data-ttu-id="e582b-152">JEA PowerShell Direct üzerinden kullanmak için ek yapılandırma gerekir.</span><span class="sxs-lookup"><span data-stu-id="e582b-152">No additional configuration is required to use JEA over PowerShell Direct.</span></span> <span data-ttu-id="e582b-153">Ancak, sanal makinede çalışan konuk işletim sistemini Windows 10, Windows Server 2016 veya üzeri olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e582b-153">However, the guest operating system running inside the virtual machine must be Windows 10, Windows Server 2016, or higher.</span></span> <span data-ttu-id="e582b-154">Hyper-V Yöneticisi kullanarak JEA uç noktasına bağlanabileceği `-VMName` veya `-VMId` PSRemoting cmdlet parametreleri:</span><span class="sxs-lookup"><span data-stu-id="e582b-154">The Hyper-V admin can connect to the JEA endpoint by using the `-VMName` or `-VMId` parameters on PSRemoting cmdlets:</span></span>

```powershell
# Entering a JEA session using PowerShell Direct when the VM name is unique
Enter-PSSession -VMName 'SQL01' -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'

# Entering a JEA session using PowerShell Direct using VM ids
$vm = Get-VM -VMName 'MyVM' | Select-Object -First 1
Enter-PSSession -VMId $vm.VMId -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'
```

<span data-ttu-id="e582b-155">Bir Hyper-V Yöneticisi tarafından kullanmak için sistemi yönetmek için gereken en düşük haklara sahip bir ayrılmış kullanıcı hesabı oluşturmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="e582b-155">It's recommended you create a dedicated user account with the minimum rights needed to manage the system for use by a Hyper-V administrator.</span></span> <span data-ttu-id="e582b-156">Unutmayın, ayrıcalıksız bir kullanıcı, sınırlandırılmamış PowerShell kullanarak da dahil olmak üzere varsayılan olarak, bir Windows makinede oturum açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e582b-156">Remember, even an unprivileged user can sign into a Windows machine by default, including using unconstrained PowerShell.</span></span> <span data-ttu-id="e582b-157">Dosya sistemine göz atın ve işletim sistemi ortamınızın hakkında daha fazla bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e582b-157">That allows them to browse the file system and learn more about your OS environment.</span></span> <span data-ttu-id="e582b-158">Bir Hyper-V Yöneticisi kilitlemek ve onlara yalnızca PowerShell Direct ile jea'yı kullanarak bir VM erişimi sınırlamak için Hyper-V yöneticinin JEA hesabı yerel oturum açma haklarını engellemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="e582b-158">To lock down a Hyper-V administrator and limit them to only access a VM using PowerShell Direct with JEA, you must deny local logon rights to the Hyper-V admin's JEA account.</span></span>
