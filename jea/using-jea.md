---
ms.date: 06/12/2017
keywords: jea, powershell, güvenlik
title: JEA’yı kullanma
ms.openlocfilehash: fa3d3a3c8bc0090ec9ad788585ec5df933134173
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054688"
---
# <a name="using-jea"></a><span data-ttu-id="61bb7-103">JEA’yı kullanma</span><span class="sxs-lookup"><span data-stu-id="61bb7-103">Using JEA</span></span>

> <span data-ttu-id="61bb7-104">Şunun için geçerlidir: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="61bb7-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="61bb7-105">Bu konuda çeşitli şekillerde bağlanmak ve bir JEA uç noktası kullanma açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="61bb7-105">This topic describes the various ways you can connect to and use a JEA endpoint.</span></span>

## <a name="using-jea-interactively"></a><span data-ttu-id="61bb7-106">JEA etkileşimli kullanma</span><span class="sxs-lookup"><span data-stu-id="61bb7-106">Using JEA interactively</span></span>

<span data-ttu-id="61bb7-107">Jea'yı yapılandırmanızı test veya basit görevleri gerçekleştirmek kullanıcılar için varsa, normal bir PowerShell uzaktan iletişimini oturumu olduğu gibi JEA kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="61bb7-107">If you are testing your JEA configuration or have simple tasks for users to perform, you can use JEA the same way you would a regular PowerShell remoting session.</span></span>
<span data-ttu-id="61bb7-108">Görevler karmaşık uzaktan iletişim için kullanılacak önerilir [örtük uzak iletişim](#using-jea-with-implicit-remoting) kullanıcılarınız için birlikte çalışan olanak tanıyarak kolaylaştırmak için verileri yerel olarak nesnelerini.</span><span class="sxs-lookup"><span data-stu-id="61bb7-108">For complex remoting tasks, it is recommended to use [implicit remoting](#using-jea-with-implicit-remoting) instead to make it easier for your users by allowing users to operate with the data objects locally.</span></span>

<span data-ttu-id="61bb7-109">JEA etkileşimli olarak kullanabilmek için ihtiyacınız olacak:</span><span class="sxs-lookup"><span data-stu-id="61bb7-109">To use JEA interactively, you will need:</span></span>
- <span data-ttu-id="61bb7-110">Bağlandığınız bilgisayarın adını (yerel makine olabilir)</span><span class="sxs-lookup"><span data-stu-id="61bb7-110">The name of the computer you are connecting to (can be the local machine)</span></span>
- <span data-ttu-id="61bb7-111">Bu bilgisayarda kayıtlı bir JEA uç nokta adı</span><span class="sxs-lookup"><span data-stu-id="61bb7-111">The name of the JEA endpoint registered on that computer</span></span>
- <span data-ttu-id="61bb7-112">JEA uç noktasına erişimi olan kimlik bilgilerini bilgisayar için</span><span class="sxs-lookup"><span data-stu-id="61bb7-112">Credentials for the computer that have access to the JEA endpoint</span></span>

<span data-ttu-id="61bb7-113">El ile bu bilgileri kullanarak bir JEA oturumu kullanmaya başlayabilirsiniz [New-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSSession) veya [Enter-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/enter-pssession).</span><span class="sxs-lookup"><span data-stu-id="61bb7-113">With that information in hand, you can start a JEA session using [New-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSSession) or [Enter-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/enter-pssession).</span></span>

```powershell
$nonAdminCred = Get-Credential
Enter-PSSession -ComputerName localhost -ConfigurationName JEAMaintenance -Credential $nonAdminCred
```

<span data-ttu-id="61bb7-114">Şu anda oturum içinde JEA uç noktaya erişime sahip olduğundan, hesap atlayabilirsiniz, `-Credential` parametresi.</span><span class="sxs-lookup"><span data-stu-id="61bb7-114">If the account you're currently logged in as has access to the JEA endpoint, you can omit the `-Credential` parameter.</span></span>

<span data-ttu-id="61bb7-115">Ne zaman PowerShell istemi değişiklikleri `[localhost]: PS>` uzak JEA oturumla artık kurduğuna dair öğrenmiş olacaksınız.</span><span class="sxs-lookup"><span data-stu-id="61bb7-115">When the PowerShell prompt changes to `[localhost]: PS>` you will know that you are now interacting with the remote JEA session.</span></span>
<span data-ttu-id="61bb7-116">Çalıştırabileceğiniz `Get-Command` hangi komutları kullanılabilir denetlemek için.</span><span class="sxs-lookup"><span data-stu-id="61bb7-116">You can run `Get-Command` to check which commands are available.</span></span>
<span data-ttu-id="61bb7-117">Kullanılabilir parametrelerin veya izin verilen parametre değerleri herhangi bir kısıtlama varsa bilgi için yöneticinize başvurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="61bb7-117">You will need to consult with your administrator to learn if there are any restrictions on the available parameters or allowable parameter values.</span></span>

<span data-ttu-id="61bb7-118">Bir anımsatıcı JEA oturumları NoLanguage modunda çalışmak genellikle PowerShell kullanma yollarından bazıları kullanılamayabilir.</span><span class="sxs-lookup"><span data-stu-id="61bb7-118">As a reminder, JEA sessions operate in NoLanguage mode, so some of the ways you typically use PowerShell may not be available.</span></span>
<span data-ttu-id="61bb7-119">Örneğin, veri depolamak veya cmdlet'lerinden döndürülen nesne özellikleri incelemek için değişkenler kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="61bb7-119">For instance, you cannot use variables to store data or inspect the properties on objects returned from cmdlets.</span></span>
<span data-ttu-id="61bb7-120">Aşağıdaki örnekte gösterildiği nasıl örnek bir PowerShell bugün kullanmakta olduğunuz ve aynı almak için iki yaklaşım komutu NoLanguage modunda çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="61bb7-120">The below example shows an example of how you may be using PowerShell today, and two approaches to get the same command working in NoLanguage mode.</span></span>

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

<span data-ttu-id="61bb7-121">Bu yaklaşım zorlaştıran daha karmaşık komut çağrıları için kullanmayı [örtük uzak iletişim](#using-jea-with-implicit-remoting) veya [özel işlevler oluşturma](role-capabilities.md#creating-custom-functions) , istenen işlevselliği sarmalamak.</span><span class="sxs-lookup"><span data-stu-id="61bb7-121">For more complex command invocations that make this approach difficult, consider using [implicit remoting](#using-jea-with-implicit-remoting) or [creating custom functions](role-capabilities.md#creating-custom-functions) that wrap the functionality you desire.</span></span>

## <a name="using-jea-with-implicit-remoting"></a><span data-ttu-id="61bb7-122">Jea'yı örtük uzak iletişim ile kullanma</span><span class="sxs-lookup"><span data-stu-id="61bb7-122">Using JEA with implicit remoting</span></span>

<span data-ttu-id="61bb7-123">PowerShell, proxy cmdlet'leri, yerel bilgisayarınızda uzak bir makineden içeri aktarma ve komutları yerel olarak bulunuyorlarmış etkileşime bir alternatif uzaktan iletişim modelini destekler.</span><span class="sxs-lookup"><span data-stu-id="61bb7-123">PowerShell supports an alternative remoting model where you can import proxy cmdlets from a remote machine on your local computer and interact with them as if they were local commands.</span></span>
<span data-ttu-id="61bb7-124">Bu örtük uzak iletişim olarak adlandırılır ve iyi içinde açıklanan [bu *Hey, Scripting Guy!* blog gönderisi](https://blogs.technet.microsoft.com/heyscriptingguy/2013/09/08/remoting-the-implicit-way/).</span><span class="sxs-lookup"><span data-stu-id="61bb7-124">This is called implicit remoting, and is explained well in [this *Hey, Scripting Guy!* blog post](https://blogs.technet.microsoft.com/heyscriptingguy/2013/09/08/remoting-the-implicit-way/).</span></span>
<span data-ttu-id="61bb7-125">Örtük uzak iletişim JEA cmdlet'leri tam dil modunda çalışmasına izin verdiğinden JEA ile çalışırken, özellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="61bb7-125">Implicit remoting is particularly useful when working with JEA because it allows you to work with JEA cmdlets in a full language mode.</span></span>
<span data-ttu-id="61bb7-126">Bu sekme tamamlama, değişkenleri kullanın, nesnelerini işleyin ve hatta daha kolay bir JEA uç noktasına karşı otomatik hale getirmek için yerel betiklerini kullanın anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="61bb7-126">This means you can use tab completion, variables, manipulate objects, and even use local scripts to more easily automate against a JEA endpoint.</span></span>
<span data-ttu-id="61bb7-127">Bir ara sunucu komutu çağırmak her zaman, veriler uzak makinede JEA uç noktasına gönderilen ve yürütülen vardır.</span><span class="sxs-lookup"><span data-stu-id="61bb7-127">Anytime you invoke a proxy command, the data will be sent to the JEA endpoint on the remote machine and executed there.</span></span>

<span data-ttu-id="61bb7-128">Örtük uzak iletişim cmdlet'leri var olan bir PowerShell oturumundan içeri aktararak çalışır.</span><span class="sxs-lookup"><span data-stu-id="61bb7-128">Implicit remoting works by importing cmdlets from an existing PowerShell session.</span></span>
<span data-ttu-id="61bb7-129">Ayrıca, her proxy cmdlet isimleri için uzak sistem komutlardır ayırt etmek seçtiğiniz bir dize ile ön ek isteğe bağlı olarak seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="61bb7-129">You can optionally choose to prefix the nouns of each proxy cmdlet with a string of your choosing to distinguish which commands are for the remote system.</span></span>
<span data-ttu-id="61bb7-130">Proxy komutların tümünü içeren geçici bir betik modülündeki oluşturulur ve süresi boyunca, yerel PowerShell oturumunuzda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="61bb7-130">A temporary script module containing all of the proxy commands will be created and can be used for the duration of your local PowerShell session.</span></span>

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Import the entire PSSession and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA'

# Invoke "Get-Command" on the remote JEA endpoint using the proxy cmdlet
Get-JEACommand
```

> [!IMPORTANT]
> <span data-ttu-id="61bb7-131">Bazı sistemler, tüm bir JEA oturumu varsayılan JEA cmdlet'lerinde kısıtlamaları nedeniyle içeri aktarmak mümkün olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="61bb7-131">Some systems may not be able to import an entire JEA session due to constraints in the default JEA cmdlets.</span></span>
> <span data-ttu-id="61bb7-132">Bu sorunu aşmak için yalnızca ihtiyacınız olacak komutların JEA oturumundan açıkça adlarını sağlayarak içeri `-CommandName` parametresi.</span><span class="sxs-lookup"><span data-stu-id="61bb7-132">To get around this, only import the commands you need from the JEA session by explicitly providing their names to the `-CommandName` parameter.</span></span>
> <span data-ttu-id="61bb7-133">Gelecekte yapılacak bir güncelleştirmenin etkilenen sistemlerinde tüm JEA oturumları alma sorunu ele alınacaktır.</span><span class="sxs-lookup"><span data-stu-id="61bb7-133">A future update will address the issue with importing entire JEA sessions on affected systems.</span></span>

<span data-ttu-id="61bb7-134">Bir JEA oturumu varsayılan JEA parametrelerindeki kısıtlamalar nedeniyle içeri aktarma bulamıyorsanız, içeri aktarılan kümesinden varsayılan komutları filtrelemek için aşağıdaki adımları izleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="61bb7-134">If you are unable to import a JEA session due to constraints on the default JEA parameters, you can follow the steps below to filter out the default commands from the imported set.</span></span>
<span data-ttu-id="61bb7-135">Komutları gibi kullanmaya devam edersiniz `Select-Object` --yalnızca uzak bir JEA oturumdaki yerine bilgisayarınızda yüklü yerel sürümü kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="61bb7-135">You will still be able to use commands like `Select-Object` -- you'll just use the local version installed on your computer instead of the remote one in the JEA session.</span></span>

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

<span data-ttu-id="61bb7-136">Örtük uzak iletişim kullanarak proxy cmdlet'leri de kalıcı yapılabilir [Export-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/Export-PSSession).</span><span class="sxs-lookup"><span data-stu-id="61bb7-136">You can also persist the proxied cmdlets from implicit remoting using [Export-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/Export-PSSession).</span></span>
<span data-ttu-id="61bb7-137">Örtük uzak iletişim hakkında daha fazla bilgi için Yardım belgelerine göz atın [Import-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/import-pssession) ve [Import-Module](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/import-module).</span><span class="sxs-lookup"><span data-stu-id="61bb7-137">For more information about implicit remoting, check out the help documentation for [Import-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/import-pssession) and [Import-Module](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/import-module).</span></span>

## <a name="using-jea-programmatically"></a><span data-ttu-id="61bb7-138">JEA programlı olarak kullanma</span><span class="sxs-lookup"><span data-stu-id="61bb7-138">Using JEA programmatically</span></span>

<span data-ttu-id="61bb7-139">JEA Otomasyon sistemleri ve şirket içi Yardım Masası uygulamaları ve web siteleri gibi kullanıcı uygulamaları içinde de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="61bb7-139">JEA can also be used in automation systems and in user applications, such as in-house helpdesk apps and web sites.</span></span>
<span data-ttu-id="61bb7-140">Uygulamaları oluşturma için program JEA uzak oturumu çalıştırma komutları sınırlayan olduğunu bilmeniz gerekir, uyarı ile sınırlandırılmamış PowerShell uç konuşma yaklaşımı aynıdır.</span><span class="sxs-lookup"><span data-stu-id="61bb7-140">The approach is the same as that for building apps that talk to unconstrained PowerShell endpoints, with the caveat that the program should be aware that JEA is limiting the commands that can be run in the remote session.</span></span>

<span data-ttu-id="61bb7-141">Basit, tek seferlik görevler için kullanabileceğiniz [Invoke-Command](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/invoke-command) jea'yı kullanarak bir komut kümesini çalıştırmak için.</span><span class="sxs-lookup"><span data-stu-id="61bb7-141">For simple, one-off tasks, you can use [Invoke-Command](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/invoke-command) to run a set of commands using JEA.</span></span>

```powershell
Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Process; Get-Service }
```

<span data-ttu-id="61bb7-142">Bir JEA oturumuna bağlandığında, hangi komutları kullanılabilir olup olmadığını denetlemek için çalıştırın `Get-Command` ve denetlemek için izin verilen parametre sonuçları arasında gezinin.</span><span class="sxs-lookup"><span data-stu-id="61bb7-142">To check which commands are available for use when you connect to a JEA session, run `Get-Command` and iterate through the results to check for the allowed parameters.</span></span>

```powershell
$allowedCommands = Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Command }
$allowedCommands | Where-Object { $_.CommandType -in 'Function', 'Cmdlet' } | Format-Table Name, Parameters
```

<span data-ttu-id="61bb7-143">Oluşturuyorsanız bir C# uygulama, yapılandırma adı belirterek bir JEA oturumuna bağlandığında bir PowerShell çalışma alanı oluşturabilirsiniz bir [WSManConnectionInfo](https://msdn.microsoft.com/library/system.management.automation.runspaces.wsmanconnectioninfo(v=vs.85).aspx) nesne.</span><span class="sxs-lookup"><span data-stu-id="61bb7-143">If you are building a C# app, you can create a PowerShell runspace that connects to a JEA session by specifying the configuration name in a [WSManConnectionInfo](https://msdn.microsoft.com/library/system.management.automation.runspaces.wsmanconnectioninfo(v=vs.85).aspx) object.</span></span>

```csharp
// using System.Management.Automation;
var computerName = "SERVER01";
var configName   = "JEAMaintenance";
var creds        = // create a PSCredential object here (https://msdn.microsoft.com/library/system.management.automation.pscredential(v=vs.85).aspx)

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

## <a name="using-jea-with-powershell-direct"></a><span data-ttu-id="61bb7-144">Jea'yı PowerShell Direct ile kullanma</span><span class="sxs-lookup"><span data-stu-id="61bb7-144">Using JEA with PowerShell Direct</span></span>

<span data-ttu-id="61bb7-145">Windows 10 ve Windows Server 2016 Hyper-V sunar [PowerShell Direct](https://msdn.microsoft.com/virtualization/hyperv_on_windows/user_guide/vmsession), Hyper-V ağ yapılandırması veya uzaktan yönetim bakılmaksızın PowerShell ile sanal makineleri yönetme olanağı sağlayan bir özellik sanal makine ayarları.</span><span class="sxs-lookup"><span data-stu-id="61bb7-145">Hyper-V in Windows 10 and Windows Server 2016 offers [PowerShell Direct](https://msdn.microsoft.com/virtualization/hyperv_on_windows/user_guide/vmsession), a feature which allows Hyper-V administrators to manage virtual machines with PowerShell regardless of the network configuration or remote management settings on the virtual machine.</span></span>

<span data-ttu-id="61bb7-146">Sanal makinenizde ağ bağlantısını kaybedebilir ve bir veri merkezi yönetim ağ ayarlarını düzeltmek gerekiyorsa bu yararlı olabilir, VM için bir Hyper-V sınırlı yönetici erişimi vermek için PowerShell Direct ile JEA kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="61bb7-146">You can use PowerShell Direct with JEA to give a Hyper-V administrator limited access to your VM, which can be useful if you lose network connectivity to your VM and need a datacenter admin to fix the network settings.</span></span>

<span data-ttu-id="61bb7-147">Sanal makinede çalışan işletim sistemini Windows 10 veya Windows Server 2016 olması gerekir ancak ek yapılandırma JEA PowerShell Direct üzerinden kullanmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="61bb7-147">No additional configuration is required to use JEA over PowerShell Direct, however the operating system running inside the virtual machine must be Windows 10 or Windows Server 2016.</span></span>
<span data-ttu-id="61bb7-148">Hyper-V Yöneticisi kullanarak JEA uç noktasına bağlanabileceği `-VMName` veya `-VMId` PSRemoting cmdlet parametreleri:</span><span class="sxs-lookup"><span data-stu-id="61bb7-148">The Hyper-V admin can connect to the JEA endpoint by using the `-VMName` or `-VMId` parameters on PSRemoting cmdlets:</span></span>

```powershell
# Entering a JEA session using PowerShell Direct when the VM name is unique
Enter-PSSession -VMName 'SQL01' -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'

# Entering a JEA session using PowerShell Direct using VM ids
$vm = Get-VM -VMName 'MyVM' | Select-Object -First 1
Enter-PSSession -VMId $vm.VMId -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'
```

<span data-ttu-id="61bb7-149">Kullanmak, Hyper-V yöneticileri için sistemi yönetmek için diğer haklara sahip ayrılmış bir yerel kullanıcı oluşturmanız önemle tavsiye edilir.</span><span class="sxs-lookup"><span data-stu-id="61bb7-149">It is strongly recommended that you create a dedicated local user with no other rights to manage the system for your Hyper-V administrators to use.</span></span>
<span data-ttu-id="61bb7-150">Sınırlandırılmamış PowerShell kullanarak da dahil olmak üzere varsayılan olarak, bir Windows makinesine, ayrıcalıksız bir kullanıcı yine de bağlanabilir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="61bb7-150">Remember that even an unprivileged user can still log into a Windows machine by default, including using unconstrained PowerShell.</span></span>
<span data-ttu-id="61bb7-151">Eklemenize olanak tanıyan bunları (bazı) gözatmak dosya sistemini ve işletim sistemi ortamınız hakkında daha fazla bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="61bb7-151">That will allow them to browse (some of) the file system and learn more about your OS environment.</span></span>
<span data-ttu-id="61bb7-152">Yalnızca PowerShell Direct ile jea'yı kullanarak sanal Makineye erişmek için bir Hyper-V Yöneticisi kilitlemek için Hyper-V yöneticinin JEA hesabı yerel oturum açma haklarını Reddet gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="61bb7-152">To lock down a Hyper-V administrator to only access a VM using PowerShell Direct with JEA, you will need to deny local logon rights to the Hyper-V admin's JEA account.</span></span>
