---
ms.date: 08/14/2018
keywords: PowerShell cmdlet'i
title: Uzak Komut Çalıştırma
ms.assetid: d6938b56-7dc8-44ba-b4d4-cd7b169fd74d
ms.openlocfilehash: 2001b5509acde6ec4259bb1442944958a67aa66f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688598"
---
# <a name="running-remote-commands"></a><span data-ttu-id="44181-103">Uzak Komut Çalıştırma</span><span class="sxs-lookup"><span data-stu-id="44181-103">Running Remote Commands</span></span>

<span data-ttu-id="44181-104">Bir ya da tek bir PowerShell komutu bilgisayarlarla yüzlerce komutları çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44181-104">You can run commands on one or hundreds of computers with a single PowerShell command.</span></span> <span data-ttu-id="44181-105">Windows PowerShell, WMI, RPC ve WS-Yönetimi dahil olmak üzere çeşitli teknolojiler kullanarak uzak bilgisayar destekler.</span><span class="sxs-lookup"><span data-stu-id="44181-105">Windows PowerShell supports remote computing by using various technologies, including WMI, RPC, and WS-Management.</span></span>

<span data-ttu-id="44181-106">PowerShell Core destekler, WMI, WS-Management ve SSH uzaktan iletişim.</span><span class="sxs-lookup"><span data-stu-id="44181-106">PowerShell Core supports WMI, WS-Management, and SSH remoting.</span></span> <span data-ttu-id="44181-107">RPC artık desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="44181-107">RPC is no longer supported.</span></span>

<span data-ttu-id="44181-108">Uzak PowerShell core'da hakkında daha fazla bilgi için aşağıdaki makalelere bakın:</span><span class="sxs-lookup"><span data-stu-id="44181-108">For more information about remoting in PowerShell Core, see the following articles:</span></span>

- <span data-ttu-id="44181-109">[SSH PowerShell core'da uzaktan iletişim][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="44181-109">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="44181-110">[PowerShell core'da WSMan uzaktan iletişim][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="44181-110">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

## <a name="windows-powershell-remoting-without-configuration"></a><span data-ttu-id="44181-111">Windows PowerShell uzaktan iletişimini yapılandırma olmadan</span><span class="sxs-lookup"><span data-stu-id="44181-111">Windows PowerShell Remoting Without Configuration</span></span>

<span data-ttu-id="44181-112">Birçok Windows PowerShell cmdlet'lerini sağlar, veri toplamak ve bir veya daha fazla uzak bilgisayar ayarlarını değiştirmek ComputerName parametresine sahip.</span><span class="sxs-lookup"><span data-stu-id="44181-112">Many Windows PowerShell cmdlets have the ComputerName parameter that enables you to collect data and change settings on one or more remote computers.</span></span> <span data-ttu-id="44181-113">Bu cmdlet'ler, farklı iletişim protokolleri kullanın ve özel bir yapılandırma olmadan tüm Windows işletim sistemlerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="44181-113">These cmdlets use varying communication protocols and work on all Windows operating systems without any special configuration.</span></span>

<span data-ttu-id="44181-114">Şu cmdlet'leri içerir:</span><span class="sxs-lookup"><span data-stu-id="44181-114">These cmdlets include:</span></span>

- [<span data-ttu-id="44181-115">Bilgisayarı yeniden Başlat</span><span class="sxs-lookup"><span data-stu-id="44181-115">Restart-Computer</span></span>](/powershell/module/microsoft.powershell.management/restart-computer)
- [<span data-ttu-id="44181-116">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="44181-116">Test-Connection</span></span>](/powershell/module/microsoft.powershell.management/test-connection)
- [<span data-ttu-id="44181-117">EventLog Temizle</span><span class="sxs-lookup"><span data-stu-id="44181-117">Clear-EventLog</span></span>](/powershell/module/microsoft.powershell.management/clear-eventlog)
- [<span data-ttu-id="44181-118">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="44181-118">Get-EventLog</span></span>](/powershell/module/microsoft.powershell.management/get-eventlog)
- [<span data-ttu-id="44181-119">Get-HotFix</span><span class="sxs-lookup"><span data-stu-id="44181-119">Get-HotFix</span></span>](/powershell/module/microsoft.powershell.management/get-hotfix)
- [<span data-ttu-id="44181-120">Get-Process</span><span class="sxs-lookup"><span data-stu-id="44181-120">Get-Process</span></span>](/powershell/module/microsoft.powershell.management/get-process)
- [<span data-ttu-id="44181-121">Get-Service</span><span class="sxs-lookup"><span data-stu-id="44181-121">Get-Service</span></span>](/powershell/module/microsoft.powershell.management/get-service)
- [<span data-ttu-id="44181-122">Hizmet belirleme</span><span class="sxs-lookup"><span data-stu-id="44181-122">Set-Service</span></span>](/powershell/module/microsoft.powershell.management/set-service)
- [<span data-ttu-id="44181-123">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="44181-123">Get-WinEvent</span></span>](/powershell/module/microsoft.powershell.diagnostics/get-winevent)
- [<span data-ttu-id="44181-124">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="44181-124">Get-WmiObject</span></span>](/powershell/module/microsoft.powershell.management/get-wmiobject)

<span data-ttu-id="44181-125">Genellikle, özel bir yapılandırma olmadan uzaktan iletişimini destekleyen cmdlet'ler ComputerName parametresine sahip ve oturum parametresi yok.</span><span class="sxs-lookup"><span data-stu-id="44181-125">Typically, cmdlets that support remoting without special configuration have the ComputerName parameter and don't have the Session parameter.</span></span> <span data-ttu-id="44181-126">Bu cmdlet'ler oturumunuzda bulmak için şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="44181-126">To find these cmdlets in your session, type:</span></span>

```powershell
Get-Command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## <a name="windows-powershell-remoting"></a><span data-ttu-id="44181-127">Windows PowerShell uzaktan iletişimi</span><span class="sxs-lookup"><span data-stu-id="44181-127">Windows PowerShell Remoting</span></span>

<span data-ttu-id="44181-128">WS-Management protokolü kullanarak, Windows PowerShell uzaktan iletişimini, bir veya daha fazla uzak bilgisayar üzerinde herhangi bir Windows PowerShell komutunu çalıştırmak olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="44181-128">Using the WS-Management protocol, Windows PowerShell remoting lets you run any Windows PowerShell command on one or more remote computers.</span></span> <span data-ttu-id="44181-129">Kalıcı bağlantılar kurmanın, etkileşimli bir oturum başlatın ve uzak bilgisayarlarda betikleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="44181-129">You can establish persistent connections, start interactive sessions, and run scripts on remote computers.</span></span>

<span data-ttu-id="44181-130">Windows PowerShell uzaktan iletişimini kullanmak için uzak bilgisayara uzaktan yönetim için yapılandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="44181-130">To use Windows PowerShell remoting, the remote computer must be configured for remote management.</span></span>
<span data-ttu-id="44181-131">Yönergeleri de dahil daha fazla bilgi için bkz. [uzak gereksinimlerin](/powershell/module/microsoft.powershell.core/about/about_remote_requirements).</span><span class="sxs-lookup"><span data-stu-id="44181-131">For more information, including instructions, see [About Remote Requirements](/powershell/module/microsoft.powershell.core/about/about_remote_requirements).</span></span>

<span data-ttu-id="44181-132">Windows PowerShell uzaktan iletişimini yapılandırdıktan sonra birçok remoting stratejileri sizin için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="44181-132">Once you have configured Windows PowerShell remoting, many remoting strategies are available to you.</span></span>
<span data-ttu-id="44181-133">Bu makalede, yalnızca birkaç tanesi listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="44181-133">This article lists just a few of them.</span></span> <span data-ttu-id="44181-134">Daha fazla bilgi için [hakkında uzak](/powershell/module/microsoft.powershell.core/about/about_remote).</span><span class="sxs-lookup"><span data-stu-id="44181-134">For more information, see [About Remote](/powershell/module/microsoft.powershell.core/about/about_remote).</span></span>

### <a name="start-an-interactive-session"></a><span data-ttu-id="44181-135">Etkileşimli bir oturum Başlat</span><span class="sxs-lookup"><span data-stu-id="44181-135">Start an Interactive Session</span></span>

<span data-ttu-id="44181-136">Tek bir uzak bilgisayar ile etkileşimli bir oturum başlatmak için kullanın [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="44181-136">To start an interactive session with a single remote computer, use the [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) cmdlet.</span></span>
<span data-ttu-id="44181-137">Örneğin, Server01 uzak bilgisayarla etkileşimli bir oturum başlatmak için şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="44181-137">For example, to start an interactive session with the Server01 remote computer, type:</span></span>

```powershell
Enter-PSSession Server01
```

<span data-ttu-id="44181-138">Uzak bilgisayarın adını görüntülemek için komut istemi değişiklikler.</span><span class="sxs-lookup"><span data-stu-id="44181-138">The command prompt changes to display the name of the remote computer.</span></span> <span data-ttu-id="44181-139">Uzak bilgisayarda herhangi bir komut isteminde çalıştırın ve sonuçları yerel bilgisayarda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="44181-139">Any commands that you type at the prompt run on the remote computer and the results are displayed on the local computer.</span></span>

<span data-ttu-id="44181-140">Etkileşimli oturumu sona erdirmek için şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="44181-140">To end the interactive session, type:</span></span>

```powershell
Exit-PSSession
```

<span data-ttu-id="44181-141">Enter-PSSession ve çıkış-PSSession cmdlet'ler hakkında daha fazla bilgi için bkz:</span><span class="sxs-lookup"><span data-stu-id="44181-141">For more information about the Enter-PSSession and Exit-PSSession cmdlets, see:</span></span>

- [<span data-ttu-id="44181-142">PSSession girin</span><span class="sxs-lookup"><span data-stu-id="44181-142">Enter-PSSession</span></span>](/powershell/module/microsoft.powershell.core/enter-pssession)
- [<span data-ttu-id="44181-143">Çıkış-PSSession</span><span class="sxs-lookup"><span data-stu-id="44181-143">Exit-PSSession</span></span>](/powershell/module/microsoft.powershell.core/exit-pssession)

### <a name="run-a-remote-command"></a><span data-ttu-id="44181-144">Uzak komut çalıştırma</span><span class="sxs-lookup"><span data-stu-id="44181-144">Run a Remote Command</span></span>

<span data-ttu-id="44181-145">Bir veya daha çok bilgisayarda bir komut çalıştırmak için kullanın [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="44181-145">To run a command on one or more computers, use the [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) cmdlet.</span></span> <span data-ttu-id="44181-146">Örneğin, çalıştırılacak bir [Get-UICulture](/powershell/module/microsoft.powershell.utility/get-uiculture) komutunu Server01 ve Server02 uzak bilgisayarlarda, türü:</span><span class="sxs-lookup"><span data-stu-id="44181-146">For example, to run a [Get-UICulture](/powershell/module/microsoft.powershell.utility/get-uiculture) command on the Server01 and Server02 remote computers, type:</span></span>

```powershell
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-UICulture}
```

<span data-ttu-id="44181-147">Çıkış bilgisayarınıza döndürülür.</span><span class="sxs-lookup"><span data-stu-id="44181-147">The output is returned to your computer.</span></span>

```output
LCID    Name     DisplayName               PSComputerName
----    ----     -----------               --------------
1033    en-US    English (United States)   server01.corp.fabrikam.com
1033    en-US    English (United States)   server02.corp.fabrikam.com
```

### <a name="run-a-script"></a><span data-ttu-id="44181-148">Betik çalıştırma</span><span class="sxs-lookup"><span data-stu-id="44181-148">Run a Script</span></span>

<span data-ttu-id="44181-149">Bir veya birden çok uzak bilgisayarda bir betik çalıştırmak için FilePath parametresini kullanın. `Invoke-Command` cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="44181-149">To run a script on one or many remote computers, use the FilePath parameter of the `Invoke-Command` cmdlet.</span></span> <span data-ttu-id="44181-150">Betik veya yerel bilgisayarınıza erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="44181-150">The script must be on or accessible to your local computer.</span></span> <span data-ttu-id="44181-151">Sonuçları, yerel bilgisayarınıza döndürülür.</span><span class="sxs-lookup"><span data-stu-id="44181-151">The results are returned to your local computer.</span></span>

<span data-ttu-id="44181-152">Örneğin, aşağıdaki komutu, uzak bilgisayarlarda, Server01 ve Server02 DiskCollect.ps1 betiği çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="44181-152">For example, the following command runs the DiskCollect.ps1 script on the remote computers, Server01 and Server02.</span></span>

```powershell
Invoke-Command -ComputerName Server01, Server02 -FilePath c:\Scripts\DiskCollect.ps1
```

### <a name="establish-a-persistent-connection"></a><span data-ttu-id="44181-153">Kalıcı bir bağlantı kurun</span><span class="sxs-lookup"><span data-stu-id="44181-153">Establish a Persistent Connection</span></span>

<span data-ttu-id="44181-154">Kullanım `New-PSSession` kalıcı oturum uzak bir bilgisayar oluşturmak için cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="44181-154">Use the `New-PSSession` cmdlet to create a persistent session on a remote computer.</span></span> <span data-ttu-id="44181-155">Aşağıdaki örnek, Uzak Oturumlar Server01 ve Server02 oluşturur.</span><span class="sxs-lookup"><span data-stu-id="44181-155">The following example creates remote sessions on Server01 and Server02.</span></span> <span data-ttu-id="44181-156">Oturum nesneleri depolanan `$s` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="44181-156">The session objects are stored in the `$s` variable.</span></span>

```powershell
$s = New-PSSession -ComputerName Server01, Server02
```

<span data-ttu-id="44181-157">Oturumları kurulur, bunları herhangi bir komutu çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44181-157">Now that the sessions are established, you can run any command in them.</span></span> <span data-ttu-id="44181-158">Ve oturumları kalıcı olduğundan, bir komuttan toplayabilir ve başka bir komutta kullanın.</span><span class="sxs-lookup"><span data-stu-id="44181-158">And because the sessions are persistent, you can collect data from one command and use it in another command.</span></span>

<span data-ttu-id="44181-159">Örneğin, oturumlarında $s değişkenine Get-HotFix komutu şu komutu çalıştırır ve sonuçları $h değişkeninde kaydeder.</span><span class="sxs-lookup"><span data-stu-id="44181-159">For example, the following command runs a Get-HotFix command in the sessions in the $s variable and it saves the results in the $h variable.</span></span> <span data-ttu-id="44181-160">$H değişken her $s oturumlarda oluşturulur, ancak yerel oturumu yok.</span><span class="sxs-lookup"><span data-stu-id="44181-160">The $h variable is created in each of the sessions in $s, but it doesn't exist in the local session.</span></span>

```powershell
Invoke-Command -Session $s {$h = Get-HotFix}
```

<span data-ttu-id="44181-161">Veriler artık `$h` aynı oturumda diğer komutlarla değişken.</span><span class="sxs-lookup"><span data-stu-id="44181-161">Now you can use the data in the `$h` variable with other commands in the same session.</span></span> <span data-ttu-id="44181-162">Sonuçlar, yerel bilgisayarda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="44181-162">The results are displayed on the local computer.</span></span> <span data-ttu-id="44181-163">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="44181-163">For example:</span></span>

```powershell
Invoke-Command -Session $s {$h | where {$_.InstalledBy -ne "NTAUTHORITY\SYSTEM"}}
```

### <a name="advanced-remoting"></a><span data-ttu-id="44181-164">Gelişmiş uzaktan iletişim</span><span class="sxs-lookup"><span data-stu-id="44181-164">Advanced Remoting</span></span>

<span data-ttu-id="44181-165">Windows PowerShell uzaktan yönetimi yalnızca burada başlar.</span><span class="sxs-lookup"><span data-stu-id="44181-165">Windows PowerShell remote management just begins here.</span></span> <span data-ttu-id="44181-166">Windows PowerShell ile yüklenen cmdlet'ler kullanarak oluşturmak ve Uzak Oturumlar yerel ve uzak uç çalıştırdığı komutları uzak oturum bağlantısını almak için kullanıcıların izin özelleştirilmiş ve kısıtlı oturumları oluşturma örtük uzak oturum uzak oturumu ve daha fazlasını güvenliğini yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="44181-166">By using the cmdlets installed with Windows PowerShell, you can establish and configure remote sessions both from the local and remote ends, create customized and restricted sessions, allow users to import commands from a remote session that actually run implicitly on the remote session, configure the security of a remote session, and much more.</span></span>

<span data-ttu-id="44181-167">Windows PowerShell WSMan sağlayıcısı içerir.</span><span class="sxs-lookup"><span data-stu-id="44181-167">Windows PowerShell includes a WSMan provider.</span></span> <span data-ttu-id="44181-168">Sağlayıcı oluşturur bir `WSMAN:` bir hiyerarşi yapılandırma ayarlarını yerel bilgisayarda ve uzak bilgisayarlar arasında gezinmek sağlayan sürücü.</span><span class="sxs-lookup"><span data-stu-id="44181-168">The provider creates a `WSMAN:` drive that lets you navigate through a hierarchy of configuration settings on the local computer and remote computers.</span></span>

<span data-ttu-id="44181-169">WSMan sağlayıcısı hakkında daha fazla bilgi için bkz. [WSMan sağlayıcısı](https://technet.microsoft.com/library/dd819476.aspx) ve [WS-Management cmdlet'leri hakkında](/powershell/module/microsoft.powershell.core/about/about_ws-management_cmdlets), veya Windows PowerShell konsolunda `Get-Help wsman`.</span><span class="sxs-lookup"><span data-stu-id="44181-169">For more information about the WSMan provider, see [WSMan Provider](https://technet.microsoft.com/library/dd819476.aspx) and [About WS-Management Cmdlets](/powershell/module/microsoft.powershell.core/about/about_ws-management_cmdlets), or in the Windows PowerShell console, type `Get-Help wsman`.</span></span>

<span data-ttu-id="44181-170">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="44181-170">For more information, see:</span></span>

- [<span data-ttu-id="44181-171">Uzak SSS hakkında</span><span class="sxs-lookup"><span data-stu-id="44181-171">About Remote FAQ</span></span>](https://technet.microsoft.com/library/dd315359.aspx)
- [<span data-ttu-id="44181-172">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="44181-172">Register-PSSessionConfiguration</span></span>](https://go.microsoft.com/fwlink/?LinkId=821508)
- [<span data-ttu-id="44181-173">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="44181-173">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821821)

<span data-ttu-id="44181-174">Uzaktan iletişimini hatalarla ilgili Yardım için bkz. [about_Remote_Troubleshooting](https://technet.microsoft.com/library/dd347642.aspx).</span><span class="sxs-lookup"><span data-stu-id="44181-174">For help with remoting errors, see [about_Remote_Troubleshooting](https://technet.microsoft.com/library/dd347642.aspx).</span></span>

## <a name="see-also"></a><span data-ttu-id="44181-175">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="44181-175">See Also</span></span>

- [<span data-ttu-id="44181-176">about_Remote</span><span class="sxs-lookup"><span data-stu-id="44181-176">about_Remote</span></span>](https://technet.microsoft.com/library/9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)
- [<span data-ttu-id="44181-177">about_Remote_FAQ</span><span class="sxs-lookup"><span data-stu-id="44181-177">about_Remote_FAQ</span></span>](https://technet.microsoft.com/library/e23702fd-9415-4a98-9975-390a4d3adc42)
- [<span data-ttu-id="44181-178">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="44181-178">about_Remote_Requirements</span></span>](https://technet.microsoft.com/library/da213949-134c-4741-b307-81f4492ba1bd)
- [<span data-ttu-id="44181-179">about_Remote_Troubleshooting</span><span class="sxs-lookup"><span data-stu-id="44181-179">about_Remote_Troubleshooting</span></span>](https://technet.microsoft.com/library/2f890148-8578-49ed-85ea-79a489dd6317)
- [<span data-ttu-id="44181-180">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="44181-180">about_PSSessions</span></span>](https://technet.microsoft.com/library/7a9b4e0e-fa1b-47b0-92f6-6e2995d70acb)
- [<span data-ttu-id="44181-181">about_WS Management_Cmdlets</span><span class="sxs-lookup"><span data-stu-id="44181-181">about_WS-Management_Cmdlets</span></span>](https://technet.microsoft.com/library/6ed3370a-ea10-45a5-9493-696aeace27ed)
- [<span data-ttu-id="44181-182">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="44181-182">Invoke-Command</span></span>](/powershell/module/microsoft.powershell.core/invoke-command)
- [<span data-ttu-id="44181-183">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="44181-183">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821821)
- [<span data-ttu-id="44181-184">Yeni-PSSession</span><span class="sxs-lookup"><span data-stu-id="44181-184">New-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821498)
- [<span data-ttu-id="44181-185">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="44181-185">Register-PSSessionConfiguration</span></span>](https://go.microsoft.com/fwlink/?LinkId=821508)
- [<span data-ttu-id="44181-186">WSMan sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="44181-186">WSMan Provider</span></span>](https://technet.microsoft.com/library/66fe1241-e08f-49ca-832f-a84c33ca8735)

[wsman-remoting]: WSMan-Remoting-in-PowerShell-Core.md
[ssh-remoting]: SSH-Remoting-in-PowerShell-Core.md