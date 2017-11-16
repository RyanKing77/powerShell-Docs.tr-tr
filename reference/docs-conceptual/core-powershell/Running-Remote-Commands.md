---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: "Uzak komutları çalıştırma"
ms.assetid: d6938b56-7dc8-44ba-b4d4-cd7b169fd74d
ms.openlocfilehash: 5cf9690b8fe4549a99186f172cb6f0de156a4dea
ms.sourcegitcommit: c5251755c4442487f99ff74fadf7e37bbf039089
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="running-remote-commands"></a><span data-ttu-id="a6630-103">Uzak komutları çalıştırma</span><span class="sxs-lookup"><span data-stu-id="a6630-103">Running Remote Commands</span></span>
<span data-ttu-id="a6630-104">Bir ya da tek bir Windows PowerShell komut bilgisayarlarla yüzlerce komutları çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a6630-104">You can run commands on one or hundreds of computers with a single Windows PowerShell command.</span></span> <span data-ttu-id="a6630-105">Windows PowerShell, WMI, RPC ve WS-Management gibi çeşitli teknolojiler kullanılarak bir uzak bilgisayar destekler.</span><span class="sxs-lookup"><span data-stu-id="a6630-105">Windows PowerShell supports remote computing by using various technologies, including WMI, RPC, and WS-Management.</span></span>

## <a name="remoting-without-configuration"></a><span data-ttu-id="a6630-106">Yapılandırma olmadan uzaktan iletişim</span><span class="sxs-lookup"><span data-stu-id="a6630-106">Remoting Without Configuration</span></span>
<span data-ttu-id="a6630-107">Birçok Windows PowerShell cmdlet'leri veri toplamak ve bir veya daha fazla uzak bilgisayarlarda ayarlarını değiştirmenizi sağlar ComputerName parametresi vardır.</span><span class="sxs-lookup"><span data-stu-id="a6630-107">Many Windows PowerShell cmdlets have the ComputerName parameter that enables you to collect data and change settings on one or more remote computers.</span></span> <span data-ttu-id="a6630-108">Tüm Windows işletim sistemlerinde özel bir yapılandırma Windows PowerShell destekleyen çeşitli iletişimi teknolojileri ve birçok iş kullanırlar.</span><span class="sxs-lookup"><span data-stu-id="a6630-108">They use a variety of communication technologies and many work on all Windows operating systems that Windows PowerShell supports without any special configuration.</span></span>

<span data-ttu-id="a6630-109">Şu cmdlet'leri içerir:</span><span class="sxs-lookup"><span data-stu-id="a6630-109">These cmdlets include:</span></span>
* [<span data-ttu-id="a6630-110">Bilgisayarı yeniden Başlat</span><span class="sxs-lookup"><span data-stu-id="a6630-110">Restart-Computer</span></span>](https://go.microsoft.com/fwlink/?LinkId=821625)
* [<span data-ttu-id="a6630-111">Bağlantıyı Sına</span><span class="sxs-lookup"><span data-stu-id="a6630-111">Test-Connection</span></span>](https://go.microsoft.com/fwlink/?LinkId=821646)
* [<span data-ttu-id="a6630-112">Olay günlüğünü Temizle</span><span class="sxs-lookup"><span data-stu-id="a6630-112">Clear-EventLog</span></span>](https://go.microsoft.com/fwlink/?LinkId=821568)
* [<span data-ttu-id="a6630-113">Get-olay günlüğü</span><span class="sxs-lookup"><span data-stu-id="a6630-113">Get-EventLog</span></span>](https://go.microsoft.com/fwlink/?LinkId=821585)
* [<span data-ttu-id="a6630-114">Get-düzeltme</span><span class="sxs-lookup"><span data-stu-id="a6630-114">Get-HotFix</span></span>](https://go.microsoft.com/fwlink/?LinkId=821586)
  - [<span data-ttu-id="a6630-115">Get-Process</span><span class="sxs-lookup"><span data-stu-id="a6630-115">Get-Process</span></span>](https://go.microsoft.com/fwlink/?linkid=821590)
* [<span data-ttu-id="a6630-116">Get-Service</span><span class="sxs-lookup"><span data-stu-id="a6630-116">Get-Service</span></span>](https://go.microsoft.com/fwlink/?LinkId=821593)
* [<span data-ttu-id="a6630-117">Hizmet belirleme</span><span class="sxs-lookup"><span data-stu-id="a6630-117">Set-Service</span></span>](https://go.microsoft.com/fwlink/?LinkId=821633)
* [<span data-ttu-id="a6630-118">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="a6630-118">Get-WinEvent</span></span>](https://go.microsoft.com/fwlink/?linkid=821529)
* [<span data-ttu-id="a6630-119">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="a6630-119">Get-WmiObject</span></span>](https://go.microsoft.com/fwlink/?LinkId=821595)

<span data-ttu-id="a6630-120">Genellikle, özel bir yapılandırma olmadan remoting destekleyen cmdlet'ler ComputerName parametresi varsa ve oturum parametresi yok.</span><span class="sxs-lookup"><span data-stu-id="a6630-120">Typically, cmdlets that support remoting without special configuration have the ComputerName parameter and do not have the Session parameter.</span></span> <span data-ttu-id="a6630-121">Bu cmdlet'ler oturumunuzda bulmak için şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="a6630-121">To find these cmdlets in your session, type:</span></span>

```
Get-Command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## <a name="windows-powershell-remoting"></a><span data-ttu-id="a6630-122">Windows PowerShell uzaktan iletişim</span><span class="sxs-lookup"><span data-stu-id="a6630-122">Windows PowerShell Remoting</span></span>
<span data-ttu-id="a6630-123">Bir veya daha çok uzak bilgisayarlarda herhangi bir Windows PowerShell komutunu çalıştırın WS-Management protokolü kullanır, Windows PowerShell uzaktan iletişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="a6630-123">Windows PowerShell remoting, which uses the WS-Management protocol, lets you run any Windows PowerShell command on one or many remote computers.</span></span> <span data-ttu-id="a6630-124">Kalıcı bağlantılar kurmak, 1:1 etkileşimli oturumlarını başlatmak ve komut dosyaları birden çok bilgisayarda çalışacak olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="a6630-124">It lets you establish persistent connections, start 1:1 interactive sessions, and run scripts on multiple computers.</span></span>

<span data-ttu-id="a6630-125">Windows PowerShell uzaktan iletişim kullanmak için uzak bilgisayara uzaktan yönetim için yapılandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a6630-125">To use Windows PowerShell remoting, the remote computer must be configured for remote management.</span></span> <span data-ttu-id="a6630-126">Yönergeleri dahil daha fazla bilgi için bkz: [hakkında uzaktan gereksinimleri](https://technet.microsoft.com/en-us/library/dd315349.aspx).</span><span class="sxs-lookup"><span data-stu-id="a6630-126">For more information, including instructions, see [About Remote Requirements](https://technet.microsoft.com/en-us/library/dd315349.aspx).</span></span>

<span data-ttu-id="a6630-127">Windows PowerShell uzaktan iletişimini yapılandırdıktan sonra birçok remoting strateji size kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a6630-127">After you have configured Windows PowerShell remoting, many remoting strategies are available to you.</span></span> <span data-ttu-id="a6630-128">Bu belgenin geri kalanında birkaçı bunları listeler.</span><span class="sxs-lookup"><span data-stu-id="a6630-128">The remainder of this document lists just a few of them.</span></span> <span data-ttu-id="a6630-129">Daha fazla bilgi için bkz: [hakkında uzak](https://technet.microsoft.com/en-us/library/dd347744.aspx) ve [hakkında uzak SSS](https://technet.microsoft.com/en-us/library/dd347744.aspx).</span><span class="sxs-lookup"><span data-stu-id="a6630-129">For more information, see [About Remote](https://technet.microsoft.com/en-us/library/dd347744.aspx) and [About Remote FAQ](https://technet.microsoft.com/en-us/library/dd347744.aspx).</span></span>

### <a name="start-an-interactive-session"></a><span data-ttu-id="a6630-130">Etkileşimli oturum Başlat</span><span class="sxs-lookup"><span data-stu-id="a6630-130">Start an Interactive Session</span></span>
<span data-ttu-id="a6630-131">Tek bir uzak bilgisayarla bir etkileşimli oturum başlatmak için kullanmak [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="a6630-131">To start an interactive session with a single remote computer, use the [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) cmdlet.</span></span>
<span data-ttu-id="a6630-132">Örneğin, Server01 uzak bilgisayarla bir etkileşimli oturum başlatmak için şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="a6630-132">For example, to start an interactive session with the Server01 remote computer, type:</span></span>

```
Enter-PSSession Server01
```

<span data-ttu-id="a6630-133">Bağlı olduğunuz bilgisayar adını görüntülemek için komut istemi değişiklikler.</span><span class="sxs-lookup"><span data-stu-id="a6630-133">The command prompt changes to display the name of the computer to which you are connected.</span></span> <span data-ttu-id="a6630-134">Daha sonra uzak bilgisayarda komut istemine yazın herhangi bir komut çalıştırmak ve sonuçları yerel bilgisayarda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="a6630-134">From then on, any commands that you type at the prompt run on the remote computer and the results are displayed on the local computer.</span></span>

<span data-ttu-id="a6630-135">Etkileşimli oturum sonlandırmak için aşağıdakini yazın:</span><span class="sxs-lookup"><span data-stu-id="a6630-135">To end the interactive session, type:</span></span>

```
Exit-PSSession
```

<span data-ttu-id="a6630-136">Enter-PSSession ve çıkış-PSSession cmdlet'leri hakkında daha fazla bilgi için bkz: [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) ve [çıkış-PSSession](https://go.microsoft.com/fwlink/?LinkID=821478).</span><span class="sxs-lookup"><span data-stu-id="a6630-136">For more information about the Enter-PSSession and Exit-PSSession cmdlets, see [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) and [Exit-PSSession](https://go.microsoft.com/fwlink/?LinkID=821478).</span></span>

### <a name="run-a-remote-command"></a><span data-ttu-id="a6630-137">Uzak bir komutu çalıştırın</span><span class="sxs-lookup"><span data-stu-id="a6630-137">Run a Remote Command</span></span>
<span data-ttu-id="a6630-138">Bir veya daha çok uzak bilgisayarlarda herhangi bir komut çalıştırmak için kullandığınız [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="a6630-138">To run any command on one or many remote computers, use the [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493) cmdlet.</span></span>
<span data-ttu-id="a6630-139">Örneğin, çalıştırmak için bir [Get-UICulture](https://go.microsoft.com/fwlink/?LinkId=821806) komutunu Server01 ve Server02 uzak bilgisayarlarda, türü:</span><span class="sxs-lookup"><span data-stu-id="a6630-139">For example, to run a [Get-UICulture](https://go.microsoft.com/fwlink/?LinkId=821806) command on the Server01 and Server02 remote computers, type:</span></span>

```
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-UICulture}
```

<span data-ttu-id="a6630-140">Çıktı bilgisayarınıza döndürülür.</span><span class="sxs-lookup"><span data-stu-id="a6630-140">The output is returned to your computer.</span></span>

```
LCID    Name     DisplayName               PSComputerName
----    ----     -----------               --------------
1033    en-US    English (United States)   server01.corp.fabrikam.com
1033    en-US    English (United States)   server02.corp.fabrikam.com
```
<span data-ttu-id="a6630-141">Invoke-Command cmdlet'i hakkında daha fazla bilgi için bkz: [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).</span><span class="sxs-lookup"><span data-stu-id="a6630-141">For more information about the Invoke-Command cmdlet, see [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).</span></span>

### <a name="run-a-script"></a><span data-ttu-id="a6630-142">Bir komut dosyasını çalıştır</span><span class="sxs-lookup"><span data-stu-id="a6630-142">Run a Script</span></span>
<span data-ttu-id="a6630-143">Bir veya daha çok uzak bilgisayarda bir komut dosyasını çalıştırmak için Invoke-Command cmdlet'i FilePath parametresini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a6630-143">To run a script on one or many remote computers, use the FilePath parameter of the Invoke-Command cmdlet.</span></span> <span data-ttu-id="a6630-144">Komut dosyası ya da yerel bilgisayarınıza erişilebilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a6630-144">The script must be on or accessible to your local computer.</span></span> <span data-ttu-id="a6630-145">Sonuçlar, yerel bilgisayarınıza döndürülür.</span><span class="sxs-lookup"><span data-stu-id="a6630-145">The results are returned to your local computer.</span></span>

<span data-ttu-id="a6630-146">Örneğin, aşağıdaki komutu DiskCollect.ps1 betik Server01 ve Server02 uzak bilgisayarlarda çalışır.</span><span class="sxs-lookup"><span data-stu-id="a6630-146">For example, the following command runs the DiskCollect.ps1 script on the Server01 and Server02 remote computers.</span></span>

```
Invoke-Command -ComputerName Server01, Server02 -FilePath c:\Scripts\DiskCollect.ps1
```

<span data-ttu-id="a6630-147">Invoke-Command cmdlet'i hakkında daha fazla bilgi için bkz: [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).</span><span class="sxs-lookup"><span data-stu-id="a6630-147">For more information about the Invoke-Command cmdlet, see [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).</span></span>

### <a name="establish-a-persistent-connection"></a><span data-ttu-id="a6630-148">Kalıcı bağlantı kurun</span><span class="sxs-lookup"><span data-stu-id="a6630-148">Establish a Persistent Connection</span></span>
<span data-ttu-id="a6630-149">Bir dizi veri paylaşımı ilgili komutları çalıştırmak için uzak bilgisayarda bir oturumu oluşturmak ve oluşturduğunuz oturumunda komutları çalıştırmak için Invoke-Command cmdlet'ini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a6630-149">To run a series of related commands that share data, create a session on the remote computer and then use the Invoke-Command cmdlet to run commands in the session that you create.</span></span> <span data-ttu-id="a6630-150">Uzak oturum oluşturmak için New-PSSession cmdlet'i kullanın.</span><span class="sxs-lookup"><span data-stu-id="a6630-150">To create a remote session, use the New-PSSession cmdlet.</span></span>

<span data-ttu-id="a6630-151">Örneğin, aşağıdaki komutu Server02 bilgisayarda bir uzak oturum Server01 bilgisayarda ve başka bir uzak oturum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a6630-151">For example, the following command creates a remote session on the Server01 computer and another remote session on the Server02 computer.</span></span> <span data-ttu-id="a6630-152">Bu oturum nesneleri $s değişkenine kaydeder.</span><span class="sxs-lookup"><span data-stu-id="a6630-152">It saves the session objects in the $s variable.</span></span>

```
$s = New-PSSession -ComputerName Server01, Server02
```

<span data-ttu-id="a6630-153">Oturum oluşturulur, bunları herhangi komutu çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a6630-153">Now that the sessions are established, you can run any command in them.</span></span> <span data-ttu-id="a6630-154">Ve oturumları kalıcı olduğundan, bir komut verileri toplamak ve bir sonraki komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="a6630-154">And because the sessions are persistent, you can collect data in one command and use it in a subsequent command.</span></span>

<span data-ttu-id="a6630-155">Örneğin, aşağıdaki komutu oturumlarda $s değişkeninde bir Get-düzeltme komut çalıştırır ve sonuçları $h değişkenine kaydeder.</span><span class="sxs-lookup"><span data-stu-id="a6630-155">For example, the following command runs a Get-HotFix command in the sessions in the $s variable and it saves the results in the $h variable.</span></span> <span data-ttu-id="a6630-156">Her $s oturumlarında $h değişkeni oluşturuldu, ancak yerel oturumunda yok.</span><span class="sxs-lookup"><span data-stu-id="a6630-156">The $h variable is created in each of the sessions in $s, but it does not exist in the local session.</span></span>

```
Invoke-Command -Session $s {$h = Get-HotFix}
```

<span data-ttu-id="a6630-157">Artık aşağıdaki biri gibi sonraki komutlarda $h değişkeninde verileri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a6630-157">Now you can use the data in the $h variable in subsequent commands, such as the following one.</span></span> <span data-ttu-id="a6630-158">Sonuçlar yerel bilgisayarda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="a6630-158">The results are displayed on the local computer.</span></span>

```
Invoke-Command -Session $s {$h | where {$_.InstalledBy -ne "NTAUTHORITY\SYSTEM"}}
```

### <a name="advanced-remoting"></a><span data-ttu-id="a6630-159">Gelişmiş uzaktan iletişim</span><span class="sxs-lookup"><span data-stu-id="a6630-159">Advanced Remoting</span></span>
<span data-ttu-id="a6630-160">Windows PowerShell uzaktan yönetimi yalnızca burada başlar.</span><span class="sxs-lookup"><span data-stu-id="a6630-160">Windows PowerShell remote management just begins here.</span></span> <span data-ttu-id="a6630-161">Yüklü Windows PowerShell cmdlet'lerini kullanarak oluşturmak ve Uzak Oturumlar yapılandırma yerel ve uzak uç gerçekte Çalıştır komutları uzak oturumdan içeri aktarmak için kullanıcıların izin özelleştirilmiş ve kısıtlı oturumları oluşturma örtük olarak uzak oturum bir uzak oturum ve daha fazlasını güvenliğini yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="a6630-161">By using the cmdlets installed with Windows PowerShell, you can establish and configure remote sessions both from the local and remote ends, create customized and restricted sessions, allow users to import commands from a remote session that actually run implicitly on the remote session, configure the security of a remote session, and much more.</span></span>

<span data-ttu-id="a6630-162">Uzak yapılandırmasını kolaylaştırmak için Windows PowerShell WSMan sağlayıcısı içerir.</span><span class="sxs-lookup"><span data-stu-id="a6630-162">To facilitate remote configuration, Windows PowerShell includes a WSMan provider.</span></span> <span data-ttu-id="a6630-163">WSMAN: sağlayıcısı oluşturur sürücü yapılandırma ayarları yerel bilgisayarda ve uzak bilgisayarlarda hiyerarşisini gezinmek olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="a6630-163">The WSMAN: drive that the provider creates lets you navigate through a hierarchy of configuration settings on the local computer and remote computers.</span></span>
<span data-ttu-id="a6630-164">WSMan sağlayıcısı hakkında daha fazla bilgi için bkz: [WSMan sağlayıcısı](https://technet.microsoft.com/en-us/library/dd819476.aspx) ve [WS-Management cmdlet'leri hakkında](https://technet.microsoft.com/en-us/library/dd819481.aspx), veya Windows PowerShell konsolunda "Get-Help wsman" yazın.</span><span class="sxs-lookup"><span data-stu-id="a6630-164">For more information about the WSMan provider, see  [WSMan Provider](https://technet.microsoft.com/en-us/library/dd819476.aspx) and [About WS-Management Cmdlets](https://technet.microsoft.com/en-us/library/dd819481.aspx), or in the Windows PowerShell console, type "Get-Help wsman".</span></span>

<span data-ttu-id="a6630-165">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="a6630-165">For more information, see:</span></span>
- [<span data-ttu-id="a6630-166">Uzak SSS hakkında</span><span class="sxs-lookup"><span data-stu-id="a6630-166">About Remote FAQ</span></span>](https://technet.microsoft.com/en-us/library/dd315359.aspx)
- [<span data-ttu-id="a6630-167">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="a6630-167">Register-PSSessionConfiguration</span></span>](https://go.microsoft.com/fwlink/?LinkId=821508)
- [<span data-ttu-id="a6630-168">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="a6630-168">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821821)

<span data-ttu-id="a6630-169">Remoting hatalarla ilgili Yardım için bkz: [about_Remote_Troubleshooting](https://technet.microsoft.com/en-us/library/dd347642.aspx).</span><span class="sxs-lookup"><span data-stu-id="a6630-169">For help with remoting errors, see [about_Remote_Troubleshooting](https://technet.microsoft.com/en-us/library/dd347642.aspx).</span></span>

## <a name="see-also"></a><span data-ttu-id="a6630-170">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="a6630-170">See Also</span></span>
- [<span data-ttu-id="a6630-171">about_Remote</span><span class="sxs-lookup"><span data-stu-id="a6630-171">about_Remote</span></span>](https://technet.microsoft.com/en-us/library/9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)
- [<span data-ttu-id="a6630-172">about_Remote_FAQ</span><span class="sxs-lookup"><span data-stu-id="a6630-172">about_Remote_FAQ</span></span>](https://technet.microsoft.com/en-us/library/e23702fd-9415-4a98-9975-390a4d3adc42)
- [<span data-ttu-id="a6630-173">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="a6630-173">about_Remote_Requirements</span></span>](https://technet.microsoft.com/en-us/library/da213949-134c-4741-b307-81f4492ba1bd)
- [<span data-ttu-id="a6630-174">about_Remote_Troubleshooting</span><span class="sxs-lookup"><span data-stu-id="a6630-174">about_Remote_Troubleshooting</span></span>](https://technet.microsoft.com/en-us/library/2f890148-8578-49ed-85ea-79a489dd6317)
- [<span data-ttu-id="a6630-175">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="a6630-175">about_PSSessions</span></span>](https://technet.microsoft.com/en-us/library/7a9b4e0e-fa1b-47b0-92f6-6e2995d70acb)
- [<span data-ttu-id="a6630-176">about_WS Management_Cmdlets</span><span class="sxs-lookup"><span data-stu-id="a6630-176">about_WS-Management_Cmdlets</span></span>](https://technet.microsoft.com/en-us/library/6ed3370a-ea10-45a5-9493-696aeace27ed)
- [<span data-ttu-id="a6630-177">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="a6630-177">Invoke-Command</span></span>](https://go.microsoft.com/fwlink/?LinkId=821493)
- [<span data-ttu-id="a6630-178">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="a6630-178">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821821)
- [<span data-ttu-id="a6630-179">Yeni PSSession</span><span class="sxs-lookup"><span data-stu-id="a6630-179">New-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821498)
- [<span data-ttu-id="a6630-180">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="a6630-180">Register-PSSessionConfiguration</span></span>](https://go.microsoft.com/fwlink/?LinkId=821508)
- [<span data-ttu-id="a6630-181">WSMan sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="a6630-181">WSMan Provider</span></span>](https://technet.microsoft.com/en-us/library/66fe1241-e08f-49ca-832f-a84c33ca8735)
