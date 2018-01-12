---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: "Uzak Komut Çalıştırma"
ms.assetid: d6938b56-7dc8-44ba-b4d4-cd7b169fd74d
ms.openlocfilehash: 43f07abd642e7de235647fa151537c46ebe86cae
ms.sourcegitcommit: 6aed37d7f0c9652ae09bb8c11928da7e4783ed7f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/10/2018
---
# <a name="running-remote-commands"></a><span data-ttu-id="25010-103">Uzak Komut Çalıştırma</span><span class="sxs-lookup"><span data-stu-id="25010-103">Running Remote Commands</span></span>

<span data-ttu-id="25010-104">Bir ya da tek bir Windows PowerShell komut bilgisayarlarla yüzlerce komutları çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="25010-104">You can run commands on one or hundreds of computers with a single Windows PowerShell command.</span></span> <span data-ttu-id="25010-105">Windows PowerShell, WMI, RPC ve WS-Management gibi çeşitli teknolojiler kullanılarak bir uzak bilgisayar destekler.</span><span class="sxs-lookup"><span data-stu-id="25010-105">Windows PowerShell supports remote computing by using various technologies, including WMI, RPC, and WS-Management.</span></span>

## <a name="remoting-in-powershell-core"></a><span data-ttu-id="25010-106">PowerShell çekirdek uzaktan çalışma</span><span class="sxs-lookup"><span data-stu-id="25010-106">Remoting in PowerShell Core</span></span>

<span data-ttu-id="25010-107">PowerShell çekirdeği, Windows, macOS ve Linux, PowerShell daha yeni sürümünü destekler WMI, WS-Management ve SSH remoting.</span><span class="sxs-lookup"><span data-stu-id="25010-107">PowerShell Core, the newer edition of PowerShell on Windows, macOS, and Linux, supports WMI, WS-Management, and SSH remoting.</span></span>
<span data-ttu-id="25010-108">(RPC artık desteklenmiyor.)</span><span class="sxs-lookup"><span data-stu-id="25010-108">(RPC is no longer supported.)</span></span>

<span data-ttu-id="25010-109">Bu ayarlama ile ilgili daha fazla bilgi için bkz:</span><span class="sxs-lookup"><span data-stu-id="25010-109">For more information on setting this up, see:</span></span>

* <span data-ttu-id="25010-110">[SSH PowerShell çekirdek Remoting] [ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="25010-110">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
* <span data-ttu-id="25010-111">[WinRM uzaktan PowerShell çekirdek.] [remoting winrm]</span><span class="sxs-lookup"><span data-stu-id="25010-111">[WinRM Remoting in PowerShell Core][winrm-remoting]</span></span>

## <a name="remoting-without-configuration"></a><span data-ttu-id="25010-112">Yapılandırma olmadan uzaktan iletişim</span><span class="sxs-lookup"><span data-stu-id="25010-112">Remoting Without Configuration</span></span>
<span data-ttu-id="25010-113">Birçok Windows PowerShell cmdlet'leri veri toplamak ve bir veya daha fazla uzak bilgisayarlarda ayarlarını değiştirmenizi sağlar ComputerName parametresi vardır.</span><span class="sxs-lookup"><span data-stu-id="25010-113">Many Windows PowerShell cmdlets have the ComputerName parameter that enables you to collect data and change settings on one or more remote computers.</span></span> <span data-ttu-id="25010-114">Tüm Windows işletim sistemlerinde özel bir yapılandırma Windows PowerShell destekleyen çeşitli iletişimi teknolojileri ve birçok iş kullanırlar.</span><span class="sxs-lookup"><span data-stu-id="25010-114">They use a variety of communication technologies and many work on all Windows operating systems that Windows PowerShell supports without any special configuration.</span></span>

<span data-ttu-id="25010-115">Şu cmdlet'leri içerir:</span><span class="sxs-lookup"><span data-stu-id="25010-115">These cmdlets include:</span></span>

* [<span data-ttu-id="25010-116">Bilgisayarı yeniden Başlat</span><span class="sxs-lookup"><span data-stu-id="25010-116">Restart-Computer</span></span>](https://go.microsoft.com/fwlink/?LinkId=821625)
* [<span data-ttu-id="25010-117">Bağlantıyı Sına</span><span class="sxs-lookup"><span data-stu-id="25010-117">Test-Connection</span></span>](https://go.microsoft.com/fwlink/?LinkId=821646)
* [<span data-ttu-id="25010-118">Olay günlüğünü Temizle</span><span class="sxs-lookup"><span data-stu-id="25010-118">Clear-EventLog</span></span>](https://go.microsoft.com/fwlink/?LinkId=821568)
* [<span data-ttu-id="25010-119">Get-olay günlüğü</span><span class="sxs-lookup"><span data-stu-id="25010-119">Get-EventLog</span></span>](https://go.microsoft.com/fwlink/?LinkId=821585)
* [<span data-ttu-id="25010-120">Get-düzeltme</span><span class="sxs-lookup"><span data-stu-id="25010-120">Get-HotFix</span></span>](https://go.microsoft.com/fwlink/?LinkId=821586)
* [<span data-ttu-id="25010-121">Get-Process</span><span class="sxs-lookup"><span data-stu-id="25010-121">Get-Process</span></span>](https://go.microsoft.com/fwlink/?linkid=821590)
* [<span data-ttu-id="25010-122">Get-Service</span><span class="sxs-lookup"><span data-stu-id="25010-122">Get-Service</span></span>](https://go.microsoft.com/fwlink/?LinkId=821593)
* [<span data-ttu-id="25010-123">Hizmet belirleme</span><span class="sxs-lookup"><span data-stu-id="25010-123">Set-Service</span></span>](https://go.microsoft.com/fwlink/?LinkId=821633)
* [<span data-ttu-id="25010-124">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="25010-124">Get-WinEvent</span></span>](https://go.microsoft.com/fwlink/?linkid=821529)
* [<span data-ttu-id="25010-125">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="25010-125">Get-WmiObject</span></span>](https://go.microsoft.com/fwlink/?LinkId=821595)

<span data-ttu-id="25010-126">Genellikle, özel bir yapılandırma olmadan remoting destekleyen cmdlet'ler ComputerName parametresi varsa ve oturum parametresi yok.</span><span class="sxs-lookup"><span data-stu-id="25010-126">Typically, cmdlets that support remoting without special configuration have the ComputerName parameter and do not have the Session parameter.</span></span> <span data-ttu-id="25010-127">Bu cmdlet'ler oturumunuzda bulmak için şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="25010-127">To find these cmdlets in your session, type:</span></span>

```
Get-Command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## <a name="windows-powershell-remoting"></a><span data-ttu-id="25010-128">Windows PowerShell uzaktan iletişim</span><span class="sxs-lookup"><span data-stu-id="25010-128">Windows PowerShell Remoting</span></span>
<span data-ttu-id="25010-129">Bir veya daha çok uzak bilgisayarlarda herhangi bir Windows PowerShell komutunu çalıştırın WS-Management protokolü kullanır, Windows PowerShell uzaktan iletişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="25010-129">Windows PowerShell remoting, which uses the WS-Management protocol, lets you run any Windows PowerShell command on one or many remote computers.</span></span> <span data-ttu-id="25010-130">Kalıcı bağlantılar kurmak, 1:1 etkileşimli oturumlarını başlatmak ve komut dosyaları birden çok bilgisayarda çalışacak olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="25010-130">It lets you establish persistent connections, start 1:1 interactive sessions, and run scripts on multiple computers.</span></span>

<span data-ttu-id="25010-131">Windows PowerShell uzaktan iletişim kullanmak için uzak bilgisayara uzaktan yönetim için yapılandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="25010-131">To use Windows PowerShell remoting, the remote computer must be configured for remote management.</span></span> <span data-ttu-id="25010-132">Yönergeleri dahil daha fazla bilgi için bkz: [hakkında uzaktan gereksinimleri](https://technet.microsoft.com/en-us/library/dd315349.aspx).</span><span class="sxs-lookup"><span data-stu-id="25010-132">For more information, including instructions, see [About Remote Requirements](https://technet.microsoft.com/en-us/library/dd315349.aspx).</span></span>

<span data-ttu-id="25010-133">Windows PowerShell uzaktan iletişimini yapılandırdıktan sonra birçok remoting strateji size kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="25010-133">After you have configured Windows PowerShell remoting, many remoting strategies are available to you.</span></span> <span data-ttu-id="25010-134">Bu belgenin geri kalanında birkaçı bunları listeler.</span><span class="sxs-lookup"><span data-stu-id="25010-134">The remainder of this document lists just a few of them.</span></span> <span data-ttu-id="25010-135">Daha fazla bilgi için bkz: [hakkında uzak](https://technet.microsoft.com/en-us/library/dd347744.aspx) ve [hakkında uzak SSS](https://technet.microsoft.com/en-us/library/dd347744.aspx).</span><span class="sxs-lookup"><span data-stu-id="25010-135">For more information, see [About Remote](https://technet.microsoft.com/en-us/library/dd347744.aspx) and [About Remote FAQ](https://technet.microsoft.com/en-us/library/dd347744.aspx).</span></span>

### <a name="start-an-interactive-session"></a><span data-ttu-id="25010-136">Etkileşimli oturum Başlat</span><span class="sxs-lookup"><span data-stu-id="25010-136">Start an Interactive Session</span></span>
<span data-ttu-id="25010-137">Tek bir uzak bilgisayarla bir etkileşimli oturum başlatmak için kullanmak [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="25010-137">To start an interactive session with a single remote computer, use the [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) cmdlet.</span></span>
<span data-ttu-id="25010-138">Örneğin, Server01 uzak bilgisayarla bir etkileşimli oturum başlatmak için şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="25010-138">For example, to start an interactive session with the Server01 remote computer, type:</span></span>

```
Enter-PSSession Server01
```

<span data-ttu-id="25010-139">Bağlı olduğunuz bilgisayar adını görüntülemek için komut istemi değişiklikler.</span><span class="sxs-lookup"><span data-stu-id="25010-139">The command prompt changes to display the name of the computer to which you are connected.</span></span> <span data-ttu-id="25010-140">Daha sonra uzak bilgisayarda komut istemine yazın herhangi bir komut çalıştırmak ve sonuçları yerel bilgisayarda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="25010-140">From then on, any commands that you type at the prompt run on the remote computer and the results are displayed on the local computer.</span></span>

<span data-ttu-id="25010-141">Etkileşimli oturum sonlandırmak için aşağıdakini yazın:</span><span class="sxs-lookup"><span data-stu-id="25010-141">To end the interactive session, type:</span></span>

```
Exit-PSSession
```

<span data-ttu-id="25010-142">Enter-PSSession ve çıkış-PSSession cmdlet'leri hakkında daha fazla bilgi için bkz: [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) ve [çıkış-PSSession](https://go.microsoft.com/fwlink/?LinkID=821478).</span><span class="sxs-lookup"><span data-stu-id="25010-142">For more information about the Enter-PSSession and Exit-PSSession cmdlets, see [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) and [Exit-PSSession](https://go.microsoft.com/fwlink/?LinkID=821478).</span></span>

### <a name="run-a-remote-command"></a><span data-ttu-id="25010-143">Uzak bir komutu çalıştırın</span><span class="sxs-lookup"><span data-stu-id="25010-143">Run a Remote Command</span></span>
<span data-ttu-id="25010-144">Bir veya daha çok uzak bilgisayarlarda herhangi bir komut çalıştırmak için kullandığınız [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="25010-144">To run any command on one or many remote computers, use the [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493) cmdlet.</span></span>
<span data-ttu-id="25010-145">Örneğin, çalıştırmak için bir [Get-UICulture](https://go.microsoft.com/fwlink/?LinkId=821806) komutunu Server01 ve Server02 uzak bilgisayarlarda, türü:</span><span class="sxs-lookup"><span data-stu-id="25010-145">For example, to run a [Get-UICulture](https://go.microsoft.com/fwlink/?LinkId=821806) command on the Server01 and Server02 remote computers, type:</span></span>

```
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-UICulture}
```

<span data-ttu-id="25010-146">Çıktı bilgisayarınıza döndürülür.</span><span class="sxs-lookup"><span data-stu-id="25010-146">The output is returned to your computer.</span></span>

```
LCID    Name     DisplayName               PSComputerName
----    ----     -----------               --------------
1033    en-US    English (United States)   server01.corp.fabrikam.com
1033    en-US    English (United States)   server02.corp.fabrikam.com
```
<span data-ttu-id="25010-147">Invoke-Command cmdlet'i hakkında daha fazla bilgi için bkz: [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).</span><span class="sxs-lookup"><span data-stu-id="25010-147">For more information about the Invoke-Command cmdlet, see [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).</span></span>

### <a name="run-a-script"></a><span data-ttu-id="25010-148">Bir komut dosyasını çalıştır</span><span class="sxs-lookup"><span data-stu-id="25010-148">Run a Script</span></span>
<span data-ttu-id="25010-149">Bir veya daha çok uzak bilgisayarda bir komut dosyasını çalıştırmak için Invoke-Command cmdlet'i FilePath parametresini kullanın.</span><span class="sxs-lookup"><span data-stu-id="25010-149">To run a script on one or many remote computers, use the FilePath parameter of the Invoke-Command cmdlet.</span></span> <span data-ttu-id="25010-150">Komut dosyası ya da yerel bilgisayarınıza erişilebilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="25010-150">The script must be on or accessible to your local computer.</span></span> <span data-ttu-id="25010-151">Sonuçlar, yerel bilgisayarınıza döndürülür.</span><span class="sxs-lookup"><span data-stu-id="25010-151">The results are returned to your local computer.</span></span>

<span data-ttu-id="25010-152">Örneğin, aşağıdaki komutu DiskCollect.ps1 betik Server01 ve Server02 uzak bilgisayarlarda çalışır.</span><span class="sxs-lookup"><span data-stu-id="25010-152">For example, the following command runs the DiskCollect.ps1 script on the Server01 and Server02 remote computers.</span></span>

```
Invoke-Command -ComputerName Server01, Server02 -FilePath c:\Scripts\DiskCollect.ps1
```

<span data-ttu-id="25010-153">Invoke-Command cmdlet'i hakkında daha fazla bilgi için bkz: [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).</span><span class="sxs-lookup"><span data-stu-id="25010-153">For more information about the Invoke-Command cmdlet, see [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).</span></span>

### <a name="establish-a-persistent-connection"></a><span data-ttu-id="25010-154">Kalıcı bağlantı kurun</span><span class="sxs-lookup"><span data-stu-id="25010-154">Establish a Persistent Connection</span></span>
<span data-ttu-id="25010-155">Bir dizi veri paylaşımı ilgili komutları çalıştırmak için uzak bilgisayarda bir oturumu oluşturmak ve oluşturduğunuz oturumunda komutları çalıştırmak için Invoke-Command cmdlet'ini kullanın.</span><span class="sxs-lookup"><span data-stu-id="25010-155">To run a series of related commands that share data, create a session on the remote computer and then use the Invoke-Command cmdlet to run commands in the session that you create.</span></span> <span data-ttu-id="25010-156">Uzak oturum oluşturmak için New-PSSession cmdlet'i kullanın.</span><span class="sxs-lookup"><span data-stu-id="25010-156">To create a remote session, use the New-PSSession cmdlet.</span></span>

<span data-ttu-id="25010-157">Örneğin, aşağıdaki komutu Server02 bilgisayarda bir uzak oturum Server01 bilgisayarda ve başka bir uzak oturum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="25010-157">For example, the following command creates a remote session on the Server01 computer and another remote session on the Server02 computer.</span></span> <span data-ttu-id="25010-158">Bu oturum nesneleri $s değişkenine kaydeder.</span><span class="sxs-lookup"><span data-stu-id="25010-158">It saves the session objects in the $s variable.</span></span>

```
$s = New-PSSession -ComputerName Server01, Server02
```

<span data-ttu-id="25010-159">Oturum oluşturulur, bunları herhangi komutu çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="25010-159">Now that the sessions are established, you can run any command in them.</span></span> <span data-ttu-id="25010-160">Ve oturumları kalıcı olduğundan, bir komut verileri toplamak ve bir sonraki komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="25010-160">And because the sessions are persistent, you can collect data in one command and use it in a subsequent command.</span></span>

<span data-ttu-id="25010-161">Örneğin, aşağıdaki komutu oturumlarda $s değişkeninde bir Get-düzeltme komut çalıştırır ve sonuçları $h değişkenine kaydeder.</span><span class="sxs-lookup"><span data-stu-id="25010-161">For example, the following command runs a Get-HotFix command in the sessions in the $s variable and it saves the results in the $h variable.</span></span> <span data-ttu-id="25010-162">Her $s oturumlarında $h değişkeni oluşturuldu, ancak yerel oturumunda yok.</span><span class="sxs-lookup"><span data-stu-id="25010-162">The $h variable is created in each of the sessions in $s, but it does not exist in the local session.</span></span>

```
Invoke-Command -Session $s {$h = Get-HotFix}
```

<span data-ttu-id="25010-163">Artık aşağıdaki biri gibi sonraki komutlarda $h değişkeninde verileri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="25010-163">Now you can use the data in the $h variable in subsequent commands, such as the following one.</span></span> <span data-ttu-id="25010-164">Sonuçlar yerel bilgisayarda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="25010-164">The results are displayed on the local computer.</span></span>

```
Invoke-Command -Session $s {$h | where {$_.InstalledBy -ne "NTAUTHORITY\SYSTEM"}}
```

### <a name="advanced-remoting"></a><span data-ttu-id="25010-165">Gelişmiş uzaktan iletişim</span><span class="sxs-lookup"><span data-stu-id="25010-165">Advanced Remoting</span></span>
<span data-ttu-id="25010-166">Windows PowerShell uzaktan yönetimi yalnızca burada başlar.</span><span class="sxs-lookup"><span data-stu-id="25010-166">Windows PowerShell remote management just begins here.</span></span> <span data-ttu-id="25010-167">Yüklü Windows PowerShell cmdlet'lerini kullanarak oluşturmak ve Uzak Oturumlar yapılandırma yerel ve uzak uç gerçekte Çalıştır komutları uzak oturumdan içeri aktarmak için kullanıcıların izin özelleştirilmiş ve kısıtlı oturumları oluşturma örtük olarak uzak oturum bir uzak oturum ve daha fazlasını güvenliğini yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="25010-167">By using the cmdlets installed with Windows PowerShell, you can establish and configure remote sessions both from the local and remote ends, create customized and restricted sessions, allow users to import commands from a remote session that actually run implicitly on the remote session, configure the security of a remote session, and much more.</span></span>

<span data-ttu-id="25010-168">Uzak yapılandırmasını kolaylaştırmak için Windows PowerShell WSMan sağlayıcısı içerir.</span><span class="sxs-lookup"><span data-stu-id="25010-168">To facilitate remote configuration, Windows PowerShell includes a WSMan provider.</span></span> <span data-ttu-id="25010-169">WSMAN: sağlayıcısı oluşturur sürücü yapılandırma ayarları yerel bilgisayarda ve uzak bilgisayarlarda hiyerarşisini gezinmek olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="25010-169">The WSMAN: drive that the provider creates lets you navigate through a hierarchy of configuration settings on the local computer and remote computers.</span></span>
<span data-ttu-id="25010-170">WSMan sağlayıcısı hakkında daha fazla bilgi için bkz: [WSMan sağlayıcısı](https://technet.microsoft.com/en-us/library/dd819476.aspx) ve [WS-Management cmdlet'leri hakkında](https://technet.microsoft.com/en-us/library/dd819481.aspx), veya Windows PowerShell konsolunda "Get-Help wsman" yazın.</span><span class="sxs-lookup"><span data-stu-id="25010-170">For more information about the WSMan provider, see  [WSMan Provider](https://technet.microsoft.com/en-us/library/dd819476.aspx) and [About WS-Management Cmdlets](https://technet.microsoft.com/en-us/library/dd819481.aspx), or in the Windows PowerShell console, type "Get-Help wsman".</span></span>

<span data-ttu-id="25010-171">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="25010-171">For more information, see:</span></span>
- [<span data-ttu-id="25010-172">Uzak SSS hakkında</span><span class="sxs-lookup"><span data-stu-id="25010-172">About Remote FAQ</span></span>](https://technet.microsoft.com/en-us/library/dd315359.aspx)
- [<span data-ttu-id="25010-173">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="25010-173">Register-PSSessionConfiguration</span></span>](https://go.microsoft.com/fwlink/?LinkId=821508)
- [<span data-ttu-id="25010-174">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="25010-174">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821821)

<span data-ttu-id="25010-175">Remoting hatalarla ilgili Yardım için bkz: [about_Remote_Troubleshooting](https://technet.microsoft.com/en-us/library/dd347642.aspx).</span><span class="sxs-lookup"><span data-stu-id="25010-175">For help with remoting errors, see [about_Remote_Troubleshooting](https://technet.microsoft.com/en-us/library/dd347642.aspx).</span></span>

## <a name="see-also"></a><span data-ttu-id="25010-176">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="25010-176">See Also</span></span>
- [<span data-ttu-id="25010-177">about_Remote</span><span class="sxs-lookup"><span data-stu-id="25010-177">about_Remote</span></span>](https://technet.microsoft.com/en-us/library/9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)
- [<span data-ttu-id="25010-178">about_Remote_FAQ</span><span class="sxs-lookup"><span data-stu-id="25010-178">about_Remote_FAQ</span></span>](https://technet.microsoft.com/en-us/library/e23702fd-9415-4a98-9975-390a4d3adc42)
- [<span data-ttu-id="25010-179">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="25010-179">about_Remote_Requirements</span></span>](https://technet.microsoft.com/en-us/library/da213949-134c-4741-b307-81f4492ba1bd)
- [<span data-ttu-id="25010-180">about_Remote_Troubleshooting</span><span class="sxs-lookup"><span data-stu-id="25010-180">about_Remote_Troubleshooting</span></span>](https://technet.microsoft.com/en-us/library/2f890148-8578-49ed-85ea-79a489dd6317)
- [<span data-ttu-id="25010-181">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="25010-181">about_PSSessions</span></span>](https://technet.microsoft.com/en-us/library/7a9b4e0e-fa1b-47b0-92f6-6e2995d70acb)
- [<span data-ttu-id="25010-182">about_WS Management_Cmdlets</span><span class="sxs-lookup"><span data-stu-id="25010-182">about_WS-Management_Cmdlets</span></span>](https://technet.microsoft.com/en-us/library/6ed3370a-ea10-45a5-9493-696aeace27ed)
- [<span data-ttu-id="25010-183">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="25010-183">Invoke-Command</span></span>](https://go.microsoft.com/fwlink/?LinkId=821493)
- [<span data-ttu-id="25010-184">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="25010-184">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821821)
- [<span data-ttu-id="25010-185">Yeni PSSession</span><span class="sxs-lookup"><span data-stu-id="25010-185">New-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821498)
- [<span data-ttu-id="25010-186">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="25010-186">Register-PSSessionConfiguration</span></span>](https://go.microsoft.com/fwlink/?LinkId=821508)
- [<span data-ttu-id="25010-187">WSMan sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="25010-187">WSMan Provider</span></span>](https://technet.microsoft.com/en-us/library/66fe1241-e08f-49ca-832f-a84c33ca8735)

[wsman-remoting]: WSMan-Remoting-in-PowerShell-Core.md
[ssh-resmoting]: SSH-Remoting-in-PowerShell-Core.md
