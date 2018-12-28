---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC ile sürekli tümleştirme ve sürekli dağıtım işlem hattı oluşturma
ms.openlocfilehash: c305d9bc7e0f8c659129b5a20d0b7e8b34d09ba8
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405870"
---
# <a name="building-a-continuous-integration-and-continuous-deployment-pipeline-with-dsc"></a><span data-ttu-id="38426-103">DSC ile sürekli tümleştirme ve sürekli dağıtım işlem hattı oluşturma</span><span class="sxs-lookup"><span data-stu-id="38426-103">Building a Continuous Integration and Continuous Deployment pipeline with DSC</span></span>

<span data-ttu-id="38426-104">Bu örnek, PowerShell, DSC, Pester ve Visual Studio Team Foundation Server (TFS) kullanarak sürekli tümleştirme/sürekli dağıtım (CI/CD) işlem hattı oluşturma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="38426-104">This example demonstrates how to build a Continuous Integration/Continuous Deployment (CI/CD) pipeline by using PowerShell, DSC, Pester, and Visual Studio Team Foundation Server (TFS).</span></span>

<span data-ttu-id="38426-105">İşlem hattı oluşturulan ve yapılandırıldıktan sonra tam olarak dağıtma, yapılandırma ve test bir DNS sunucusu kullanabilir ve ana bilgisayar kayıtları ilişkili.</span><span class="sxs-lookup"><span data-stu-id="38426-105">After the pipeline is built and configured, you can use it to fully deploy, configure and test a DNS server and associated host records.</span></span>
<span data-ttu-id="38426-106">Bu işlem, bir geliştirme ortamında kullanılan bir işlem hattı ilk bölümünü benzetimini yapar.</span><span class="sxs-lookup"><span data-stu-id="38426-106">This process simulates the first part of a pipeline that would be used in a development environment.</span></span>

<span data-ttu-id="38426-107">Otomatik bir CI/CD işlem hattı yazılımları daha hızlı bir şekilde güncelleştirmenize yardımcı olur ve daha güvenilir bir şekilde tüm kod test edilmesini ve kodunuzun geçerli bir derleme olduğundan emin olduktan kullanılabilir her zaman.</span><span class="sxs-lookup"><span data-stu-id="38426-107">An automated CI/CD pipeline helps you update software faster and more reliably, ensuring that all code is tested, and that a current build of your code is available at all times.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="38426-108">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="38426-108">Prerequisites</span></span>

<span data-ttu-id="38426-109">Bu örneği kullanmak için aşağıdaki bilgi sahibi olmanız:</span><span class="sxs-lookup"><span data-stu-id="38426-109">To use this example, you should be familiar with the following:</span></span>

- <span data-ttu-id="38426-110">CI-CD kavramları.</span><span class="sxs-lookup"><span data-stu-id="38426-110">CI-CD concepts.</span></span> <span data-ttu-id="38426-111">İyi bir referans şu yolda bulunabilir: [yayın işlem hattı modelini](http://aka.ms/thereleasepipelinemodelpdf).</span><span class="sxs-lookup"><span data-stu-id="38426-111">A good reference can be found at [The Release Pipeline Model](http://aka.ms/thereleasepipelinemodelpdf).</span></span>
- <span data-ttu-id="38426-112">[Git](https://git-scm.com/) kaynak denetimi</span><span class="sxs-lookup"><span data-stu-id="38426-112">[Git](https://git-scm.com/) source control</span></span>
- <span data-ttu-id="38426-113">[Pester](https://github.com/pester/Pester) testi çerçevesi</span><span class="sxs-lookup"><span data-stu-id="38426-113">The [Pester](https://github.com/pester/Pester) testing framework</span></span>
- [<span data-ttu-id="38426-114">Team Foundation Server</span><span class="sxs-lookup"><span data-stu-id="38426-114">Team Foundation Server</span></span>](https://www.visualstudio.com/tfs/)

## <a name="what-you-will-need"></a><span data-ttu-id="38426-115">İhtiyacınız</span><span class="sxs-lookup"><span data-stu-id="38426-115">What you will need</span></span>

<span data-ttu-id="38426-116">Derleme ve bu örneği çalıştırmak için çeşitli bilgisayarlar ve/veya sanal makine ile bir ortam gerekir.</span><span class="sxs-lookup"><span data-stu-id="38426-116">To build and run this example, you will need an environment with several computers and/or virtual machines.</span></span>

### <a name="client"></a><span data-ttu-id="38426-117">İstemci</span><span class="sxs-lookup"><span data-stu-id="38426-117">Client</span></span>

<span data-ttu-id="38426-118">Bu, burada tüm ayarlama ve örnek çalıştırma işlemleri gerçekleştirirsiniz bilgisayardır.</span><span class="sxs-lookup"><span data-stu-id="38426-118">This is the computer where you'll do all of the work setting up and running the example.</span></span>

<span data-ttu-id="38426-119">İstemci bilgisayarın bir Windows bilgisayarda aşağıdakilerin yüklü olması gerekir:</span><span class="sxs-lookup"><span data-stu-id="38426-119">The client computer must be a Windows computer with the following installed:</span></span>

- [<span data-ttu-id="38426-120">Git</span><span class="sxs-lookup"><span data-stu-id="38426-120">Git</span></span>](https://git-scm.com/)
- <span data-ttu-id="38426-121">öğesinden kopyalanan bir yerel git deposu https://github.com/PowerShell/Demo_CI</span><span class="sxs-lookup"><span data-stu-id="38426-121">a local git repo cloned from https://github.com/PowerShell/Demo_CI</span></span>
- <span data-ttu-id="38426-122">bir metin düzenleyicisi gibi [Visual Studio Code](https://code.visualstudio.com/)</span><span class="sxs-lookup"><span data-stu-id="38426-122">a text editor, such as [Visual Studio Code](https://code.visualstudio.com/)</span></span>

### <a name="tfssrv1"></a><span data-ttu-id="38426-123">TFSSrv1</span><span class="sxs-lookup"><span data-stu-id="38426-123">TFSSrv1</span></span>

<span data-ttu-id="38426-124">Tanımladığınız derleme TFS sunucusunu barındıran bilgisayarın ve serbest bırakın.</span><span class="sxs-lookup"><span data-stu-id="38426-124">The computer that hosts the TFS server where you will define your build and release.</span></span>
<span data-ttu-id="38426-125">Bu bilgisayarda yüklü olmalıdır [Team Foundation Server 2017](https://www.visualstudio.com/tfs/) yüklü.</span><span class="sxs-lookup"><span data-stu-id="38426-125">This computer must have [Team Foundation Server 2017](https://www.visualstudio.com/tfs/) installed.</span></span>

### <a name="buildagent"></a><span data-ttu-id="38426-126">BuildAgent</span><span class="sxs-lookup"><span data-stu-id="38426-126">BuildAgent</span></span>

<span data-ttu-id="38426-127">Windows çalıştıran bilgisayar, projeyi derler Aracısı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="38426-127">The computer that runs the Windows build agent that builds the project.</span></span>
<span data-ttu-id="38426-128">Bu bilgisayarda bir Windows derleme aracısı sürümünün yüklü ve çalışıyor olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="38426-128">This computer must have a Windows build agent installed and running.</span></span>
<span data-ttu-id="38426-129">Bkz: [Windows üzerinde aracı dağıtma](/azure/devops/pipelines/agents/v2-windows) yapı aracısını yüklemek ve bir Windows çalıştırmak yönergeler için.</span><span class="sxs-lookup"><span data-stu-id="38426-129">See [Deploy an agent on Windows](/azure/devops/pipelines/agents/v2-windows) for instructions on how to install and run a Windows build agent.</span></span>

<span data-ttu-id="38426-130">Ayrıca her ikisini de yüklemeniz gerekir `xDnsServer` ve `xNetworking` DSC modülleri bu bilgisayarda.</span><span class="sxs-lookup"><span data-stu-id="38426-130">You also need to install both the `xDnsServer` and `xNetworking` DSC modules on this computer.</span></span>

### <a name="testagent1"></a><span data-ttu-id="38426-131">TestAgent1</span><span class="sxs-lookup"><span data-stu-id="38426-131">TestAgent1</span></span>

<span data-ttu-id="38426-132">Bu örnekte DSC yapılandırması tarafından bir DNS sunucusu olarak yapılandırılmış bilgisayardır.</span><span class="sxs-lookup"><span data-stu-id="38426-132">This is the computer that is configured as a DNS server by the DSC configuration in this example.</span></span>
<span data-ttu-id="38426-133">Bilgisayarda çalışmalıdır [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span><span class="sxs-lookup"><span data-stu-id="38426-133">The computer must be running [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span></span>

### <a name="testagent2"></a><span data-ttu-id="38426-134">TestAgent2</span><span class="sxs-lookup"><span data-stu-id="38426-134">TestAgent2</span></span>

<span data-ttu-id="38426-135">Bu örnekte yapılandırır Web sitesini barındıran bilgisayarın budur.</span><span class="sxs-lookup"><span data-stu-id="38426-135">This is the computer that hosts the website this example configures.</span></span>
<span data-ttu-id="38426-136">Bilgisayarda çalışmalıdır [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span><span class="sxs-lookup"><span data-stu-id="38426-136">The computer must be running [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span></span>

## <a name="add-the-code-to-tfs"></a><span data-ttu-id="38426-137">TFS için kod ekleyin</span><span class="sxs-lookup"><span data-stu-id="38426-137">Add the code to TFS</span></span>

<span data-ttu-id="38426-138">TFS'de bir Git deposu oluşturuluyor ve istemci bilgisayardaki yerel deponuzdan kod aktararak başlayacağız.</span><span class="sxs-lookup"><span data-stu-id="38426-138">We'll start out by creating a Git repository in TFS, and importing the code from your local repository on the client computer.</span></span>
<span data-ttu-id="38426-139">Şimdi, zaten Demo_CI depo istemci bilgisayarınıza değil kopyaladıysanız, aşağıdaki git komutunu çalıştırarak yapın:</span><span class="sxs-lookup"><span data-stu-id="38426-139">If you have not already cloned the Demo_CI repository to your client computer, do so now by running the following git command:</span></span>

`git clone https://github.com/PowerShell/Demo_CI`

1. <span data-ttu-id="38426-140">İstemci bilgisayarınızda, TFS sunucunuz bir web tarayıcısında gidin.</span><span class="sxs-lookup"><span data-stu-id="38426-140">On your client computer, navigate to your TFS server in a web browser.</span></span>
1. <span data-ttu-id="38426-141">TFS içinde [yeni takım projesi oluşturma](/azure/devops/organizations/projects/create-project) Demo_CI adlı.</span><span class="sxs-lookup"><span data-stu-id="38426-141">In TFS, [Create a new team project](/azure/devops/organizations/projects/create-project) named Demo_CI.</span></span>

   <span data-ttu-id="38426-142">Emin olun **sürüm denetimi** ayarlanır **Git**.</span><span class="sxs-lookup"><span data-stu-id="38426-142">Make sure that **Version control** is set to **Git**.</span></span>
1. <span data-ttu-id="38426-143">İstemci bilgisayarınızda, bir uzak TFS'de aşağıdaki komutla yeni oluşturduğunuz depoya ekleyin:</span><span class="sxs-lookup"><span data-stu-id="38426-143">On your client computer, add a remote to the repository you just created in TFS with the following command:</span></span>

   `git remote add tfs <YourTFSRepoURL>`

   <span data-ttu-id="38426-144">Burada `<YourTFSRepoURL>` önceki adımda oluşturduğunuz TFS depo kopya URL'si.</span><span class="sxs-lookup"><span data-stu-id="38426-144">Where `<YourTFSRepoURL>` is the clone URL to the TFS repository you created in the previous step.</span></span>

   <span data-ttu-id="38426-145">Bu URL'yi bulmak nereye bilmiyorsanız, bkz. [var olan bir Git deposu kopyalama](/azure/devops/repos/git/clone).</span><span class="sxs-lookup"><span data-stu-id="38426-145">If you don't know where to find this URL, see [Clone an existing Git repo](/azure/devops/repos/git/clone).</span></span>
1. <span data-ttu-id="38426-146">Kodu yerel deponuzdan aşağıdaki komutla TFS deponuzu şuraya gönder:</span><span class="sxs-lookup"><span data-stu-id="38426-146">Push the code from your local repository to your TFS repository with the following command:</span></span>

   `git push tfs --all`
1. <span data-ttu-id="38426-147">TFS depo Demo_CI kodu ile doldurulur.</span><span class="sxs-lookup"><span data-stu-id="38426-147">The TFS repository will be populated with the Demo_CI code.</span></span>

> [!NOTE]
> <span data-ttu-id="38426-148">Bu örnekte kodda `ci-cd-example` Git deponun dalı.</span><span class="sxs-lookup"><span data-stu-id="38426-148">This example uses the code in the `ci-cd-example` branch of the Git repo.</span></span>
> <span data-ttu-id="38426-149">TFS projenizin içinde varsayılan dal olarak bu dalı belirttiğinizden emin olun ve CI/CD Tetikleyicileri oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="38426-149">Be sure to specify this branch as the default branch in your TFS project, and for the CI/CD triggers you create.</span></span>

## <a name="understanding-the-code"></a><span data-ttu-id="38426-150">Kod anlama</span><span class="sxs-lookup"><span data-stu-id="38426-150">Understanding the code</span></span>

<span data-ttu-id="38426-151">Şu derleme ve dağıtım işlem hattı oluşturmadan önce bazı kodları neler olup bittiğini anlamak için göz atalım.</span><span class="sxs-lookup"><span data-stu-id="38426-151">Before we create the build and deployment pipelines, let's look at some of the code to understand what is going on.</span></span>
<span data-ttu-id="38426-152">İstemci bilgisayarınızda, sık kullandığınız metin düzenleyicisinde açın ve Demo_CI Git deponuzun kök dizinine gidin.</span><span class="sxs-lookup"><span data-stu-id="38426-152">On your client computer, open your favorite text editor and navigate to the root of your Demo_CI Git repository.</span></span>

### <a name="the-dsc-configuration"></a><span data-ttu-id="38426-153">DSC yapılandırması</span><span class="sxs-lookup"><span data-stu-id="38426-153">The DSC configuration</span></span>

<span data-ttu-id="38426-154">Dosyayı açmak `DNSServer.ps1` (yerel Demo_CI depo kökünden `./InfraDNS/Configs/DNSServer.ps1`).</span><span class="sxs-lookup"><span data-stu-id="38426-154">Open the file `DNSServer.ps1` (from the root of the local Demo_CI repository, `./InfraDNS/Configs/DNSServer.ps1`).</span></span>

<span data-ttu-id="38426-155">Bu dosya, DNS sunucusunu ayarlar DSC yapılandırması içerir.</span><span class="sxs-lookup"><span data-stu-id="38426-155">This file contains the DSC configuration that sets up the DNS server.</span></span> <span data-ttu-id="38426-156">Bu tamamen şöyledir:</span><span class="sxs-lookup"><span data-stu-id="38426-156">Here it is in its entirety:</span></span>

```powershell
configuration DNSServer
{
    Import-DscResource -module 'xDnsServer','xNetworking', 'PSDesiredStateConfiguration'

    Node $AllNodes.Where{$_.Role -eq 'DNSServer'}.NodeName
    {
        WindowsFeature DNS
        {
            Ensure  = 'Present'
            Name    = 'DNS'
        }

        xDnsServerPrimaryZone $Node.zone
        {
            Ensure    = 'Present'
            Name      = $Node.Zone
            DependsOn = '[WindowsFeature]DNS'
        }

        foreach ($ARec in $Node.ARecords.keys) {
            xDnsRecord $ARec
            {
                Ensure    = 'Present'
                Name      = $ARec
                Zone      = $Node.Zone
                Type      = 'ARecord'
                Target    = $Node.ARecords[$ARec]
                DependsOn = '[WindowsFeature]DNS'
            }
        }

        foreach ($CName in $Node.CNameRecords.keys) {
            xDnsRecord $CName
            {
                Ensure    = 'Present'
                Name      = $CName
                Zone      = $Node.Zone
                Type      = 'CName'
                Target    = $Node.CNameRecords[$CName]
                DependsOn = '[WindowsFeature]DNS'
            }
        }
    }
}
```

<span data-ttu-id="38426-157">Bildirim `Node` deyimi:</span><span class="sxs-lookup"><span data-stu-id="38426-157">Notice the `Node` statement:</span></span>

```powershell
Node $AllNodes.Where{$_.Role -eq 'DNSServer'}.NodeName
```

<span data-ttu-id="38426-158">Bu rolü sahip olarak tanımlanmış olan tüm düğümleri bulur `DNSServer` içinde [yapılandırma verilerini](../configurations/configData.md), tarafından oluşturulan `DevEnv.ps1` betiği.</span><span class="sxs-lookup"><span data-stu-id="38426-158">This finds any nodes that were defined as having a role of `DNSServer` in the [configuration data](../configurations/configData.md), which is created by the `DevEnv.ps1` script.</span></span>

<span data-ttu-id="38426-159">Daha fazla bilgi edinebilirsiniz `Where` yönteminde [about_arrays](/powershell/reference/3.0/Microsoft.PowerShell.Core/About/about_Arrays.md)</span><span class="sxs-lookup"><span data-stu-id="38426-159">You can read more about the `Where` method in [about_arrays](/powershell/reference/3.0/Microsoft.PowerShell.Core/About/about_Arrays.md)</span></span>

<span data-ttu-id="38426-160">Düğüm tanımlamak için yapılandırma verilerini kullanarak CI düğüm bilgileri büyük olasılıkla ortamlar arasında değişir ve yapılandırma verilerini kullanarak yapılandırma kodunu değiştirmeden değişiklikleri düğüm bilgileri kolayca yapmanıza olanak verir çünkü yaparken önemlidir.</span><span class="sxs-lookup"><span data-stu-id="38426-160">Using configuration data to define nodes is important when doing CI because node information will likely change between environments, and using configuration data allows you to easily make changes to node information without changing the configuration code.</span></span>

<span data-ttu-id="38426-161">İlk kaynak blok yapılandırma çağırır **WindowsFeature** DNS özelliği etkinleştirildiğinden emin olmak için.</span><span class="sxs-lookup"><span data-stu-id="38426-161">In the first resource block, the configuration calls the **WindowsFeature** to ensure that the DNS feature is enabled.</span></span>
<span data-ttu-id="38426-162">Çağrı kaynaklardan izleyin kaynak bloklar [xDnsServer](https://github.com/PowerShell/xDnsServer) modülü birincil bölge ve DNS kayıtlarını yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="38426-162">The resource blocks that follow call resources from the [xDnsServer](https://github.com/PowerShell/xDnsServer) module to configure the primary zone and DNS records.</span></span>

<span data-ttu-id="38426-163">Dikkat iki `xDnsRecord` blokları içinde kaydırılır `foreach` yapılandırma verilerinde diziler üzerinden yineleme döngüleri.</span><span class="sxs-lookup"><span data-stu-id="38426-163">Notice that the two `xDnsRecord` blocks are wrapped in `foreach` loops that iterate through arrays in the configuration data.</span></span>
<span data-ttu-id="38426-164">Yapılandırma verilerini tarafından yeniden oluşturulur `DevEnv.ps1` betiğini sonraki göz atacağız.</span><span class="sxs-lookup"><span data-stu-id="38426-164">Again, the configuration data is created by the `DevEnv.ps1` script, which we'll look at next.</span></span>

### <a name="configuration-data"></a><span data-ttu-id="38426-165">Yapılandırma verileri</span><span class="sxs-lookup"><span data-stu-id="38426-165">Configuration data</span></span>

<span data-ttu-id="38426-166">`DevEnv.ps1` Dosyası (yerel Demo_CI depo kökünden `./InfraDNS/DevEnv.ps1`) ortama özgü yapılandırma verilerini bir hashtable içinde belirtir ve ardından bir çağrı o hashtable geçirir `New-DscConfigurationDataDocument` içindetanımlananişlevi`DscPipelineTools.psm` (`./Assets/DscPipelineTools/DscPipelineTools.psm1`).</span><span class="sxs-lookup"><span data-stu-id="38426-166">The `DevEnv.ps1` file (from the root of the local Demo_CI repository, `./InfraDNS/DevEnv.ps1`) specifies the environment-specific configuration data in a hashtable, and then passes that hashtable to a call to the `New-DscConfigurationDataDocument` function, which is defined in `DscPipelineTools.psm` (`./Assets/DscPipelineTools/DscPipelineTools.psm1`).</span></span>

<span data-ttu-id="38426-167">`DevEnv.ps1` Dosyası:</span><span class="sxs-lookup"><span data-stu-id="38426-167">The `DevEnv.ps1` file:</span></span>

```powershell
param(
    [parameter(Mandatory=$true)]
    [string]
    $OutputPath
)

Import-Module $PSScriptRoot\..\Assets\DscPipelineTools\DscPipelineTools.psd1 -Force

# Define Unit Test Environment
$DevEnvironment = @{
    Name                        = 'DevEnv';
    Roles = @(
        @{  Role                = 'DNSServer';
            VMName              = 'TestAgent1';
            Zone                = 'Contoso.com';
            ARecords            = @{'TFSSrv1'= '10.0.0.10';'Client'='10.0.0.15';'BuildAgent'='10.0.0.30';'TestAgent1'='10.0.0.40';'TestAgent2'='10.0.0.50'};
            CNameRecords        = @{'DNS' = 'TestAgent1.contoso.com'};
        }
    )
}

Return New-DscConfigurationDataDocument -RawEnvData $DevEnvironment -OutputPath $OutputPath
```

<span data-ttu-id="38426-168">`New-DscConfigurationDataDocument` İşlevi (tanımlanan `\Assets\DscPipelineTools\DscPipelineTools.psm1`) programlı olarak hashtable (düğüm veri) ve dizi (düğümü olmayan veriler) olarak geçirilen bir yapılandırma verileri belgesi oluşturur `RawEnvData` ve `OtherEnvData` parametreleri.</span><span class="sxs-lookup"><span data-stu-id="38426-168">The `New-DscConfigurationDataDocument` function (defined in `\Assets\DscPipelineTools\DscPipelineTools.psm1`) programmatically creates a configuration data document from the hashtable (node data) and array (non-node data) that are passed as the `RawEnvData` and `OtherEnvData` parameters.</span></span>

<span data-ttu-id="38426-169">Bizim durumumuzda, yalnızca `RawEnvData` parametresi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="38426-169">In our case, only the `RawEnvData` parameter is used.</span></span>

### <a name="the-psake-build-script"></a><span data-ttu-id="38426-170">Psake derleme betiği</span><span class="sxs-lookup"><span data-stu-id="38426-170">The psake build script</span></span>

<span data-ttu-id="38426-171">[Psake](https://github.com/psake/psake) betik içinde tanımlanan derleme `Build.ps1` (Demo_CI depo kökünden `./InfraDNS/Build.ps1`) yapının bir parçası olan görevleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="38426-171">The [psake](https://github.com/psake/psake) build script defined in `Build.ps1` (from the root of the Demo_CI repository, `./InfraDNS/Build.ps1`) defines tasks that are part of the build.</span></span>
<span data-ttu-id="38426-172">Ayrıca, her görevin bağlı diğer görevleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="38426-172">It also defines which other tasks each task depends on.</span></span>
<span data-ttu-id="38426-173">Psake komut çağrıldığında, belirtilen görev sağlar (veya adlı görev `Default` belirtilmezse) çalıştırır ve tüm bağımlılıklar da çalıştırın (bağımlılıkları bağımlılıklarını çalıştırın böylece özyinelemeli budur ve benzeri).</span><span class="sxs-lookup"><span data-stu-id="38426-173">When invoked, the psake script ensures that the specified task (or the task named `Default` if none is specified) runs, and that all dependencies also run (this is recursive, so that dependencies of dependencies run, and so on).</span></span>

<span data-ttu-id="38426-174">Bu örnekte, `Default` görev olarak tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="38426-174">In this example, the `Default` task is defined as:</span></span>

```powershell
Task Default -depends UnitTests
```

<span data-ttu-id="38426-175">`Default` Görevi hiçbir uygulamaya sahip, ancak bir bağımlılığa sahip `CompileConfigs` görev.</span><span class="sxs-lookup"><span data-stu-id="38426-175">The `Default` task has no implementation itself, but has a dependency on the `CompileConfigs` task.</span></span>
<span data-ttu-id="38426-176">Görev bağımlılıkları sonuç zincirini derleme betiğindeki tüm görevler çalıştırmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="38426-176">The resulting chain of task dependencies ensures that all tasks in the build script are run.</span></span>

<span data-ttu-id="38426-177">Bu örnekte, bir çağrı tarafından psake betik çağrılır `Invoke-PSake` içinde `Initiate.ps1` (Demo_CI deponun kökünde bulunur) dosyası:</span><span class="sxs-lookup"><span data-stu-id="38426-177">In this example, the psake script is invoked by a call to `Invoke-PSake` in the `Initiate.ps1` file (located at the root of the Demo_CI repository):</span></span>

```powershell
param(
    [parameter()]
    [ValidateSet('Build','Deploy')]
    [string]
    $fileName
)

#$Error.Clear()

Invoke-PSake $PSScriptRoot\InfraDNS\$fileName.ps1

<#if($Error.count)
{
    Throw "$fileName script failed. Check logs for failure details."
}
#>
```

<span data-ttu-id="38426-178">Derleme tanımı için TFS örneğimizde oluşturduğumuzda, bizim psake komut dosyası olarak sağlamanız `fileName` bu komut için parametre.</span><span class="sxs-lookup"><span data-stu-id="38426-178">When we create the build definition for our example in TFS, we will supply our psake script file as the `fileName` parameter for this script.</span></span>

<span data-ttu-id="38426-179">Derleme betiği aşağıdaki görevleri tanımlar:</span><span class="sxs-lookup"><span data-stu-id="38426-179">The build script defines the following tasks:</span></span>

#### <a name="generateenvironmentfiles"></a><span data-ttu-id="38426-180">GenerateEnvironmentFiles</span><span class="sxs-lookup"><span data-stu-id="38426-180">GenerateEnvironmentFiles</span></span>

<span data-ttu-id="38426-181">Çalıştırmaları `DevEnv.ps1`, yapılandırma verileri dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="38426-181">Runs `DevEnv.ps1`, which generates the configuration data file.</span></span>

#### <a name="installmodules"></a><span data-ttu-id="38426-182">InstallModules</span><span class="sxs-lookup"><span data-stu-id="38426-182">InstallModules</span></span>

<span data-ttu-id="38426-183">Yapılandırma tarafından gerekli modülleri yükler `DNSServer.ps1`.</span><span class="sxs-lookup"><span data-stu-id="38426-183">Installs the modules required by the configuration `DNSServer.ps1`.</span></span>

#### <a name="scriptanalysis"></a><span data-ttu-id="38426-184">ScriptAnalysis</span><span class="sxs-lookup"><span data-stu-id="38426-184">ScriptAnalysis</span></span>

<span data-ttu-id="38426-185">Çağrıları [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer).</span><span class="sxs-lookup"><span data-stu-id="38426-185">Calls the [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer).</span></span>

#### <a name="unittests"></a><span data-ttu-id="38426-186">UnitTests</span><span class="sxs-lookup"><span data-stu-id="38426-186">UnitTests</span></span>

<span data-ttu-id="38426-187">Çalıştırmaları [Pester](https://github.com/pester/Pester/wiki) birim testleri.</span><span class="sxs-lookup"><span data-stu-id="38426-187">Runs the [Pester](https://github.com/pester/Pester/wiki) unit tests.</span></span>

#### <a name="compileconfigs"></a><span data-ttu-id="38426-188">CompileConfigs</span><span class="sxs-lookup"><span data-stu-id="38426-188">CompileConfigs</span></span>

<span data-ttu-id="38426-189">Yapılandırma derleme (`DNSServer.ps1`) tarafından oluşturulan yapılandırma verilerini bir MOF dosyasına kullanarak `GenerateEnvironmentFiles` görev.</span><span class="sxs-lookup"><span data-stu-id="38426-189">Compiles the configuration (`DNSServer.ps1`) into a MOF file, using the configuration data generated by the `GenerateEnvironmentFiles` task.</span></span>

#### <a name="clean"></a><span data-ttu-id="38426-190">Clean</span><span class="sxs-lookup"><span data-stu-id="38426-190">Clean</span></span>

<span data-ttu-id="38426-191">Örnek için kullanılan klasörleri oluşturur ve herhangi bir test sonuçları, yapılandırma verileri dosyalarınızı ve modülleri önceki çalıştırmalardan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="38426-191">Creates the folders used for the example, and removes any test results, configuration data files, and modules from previous runs.</span></span>

### <a name="the-psake-deploy-script"></a><span data-ttu-id="38426-192">Betik psake dağıtma</span><span class="sxs-lookup"><span data-stu-id="38426-192">The psake deploy script</span></span>

<span data-ttu-id="38426-193">[Psake](https://github.com/psake/psake) tanımlı dağıtım betiği `Deploy.ps1` (Demo_CI depo kökünden `./InfraDNS/Deploy.ps1`) dağıtma ve çalıştırma yapılandırma görevlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="38426-193">The [psake](https://github.com/psake/psake) deployment script defined in `Deploy.ps1` (from the root of the Demo_CI repository, `./InfraDNS/Deploy.ps1`) defines tasks that deploy and run the configuration.</span></span>

<span data-ttu-id="38426-194">`Deploy.ps1` Aşağıdaki görevleri tanımlar:</span><span class="sxs-lookup"><span data-stu-id="38426-194">`Deploy.ps1` defines the following tasks:</span></span>

#### <a name="deploymodules"></a><span data-ttu-id="38426-195">DeployModules</span><span class="sxs-lookup"><span data-stu-id="38426-195">DeployModules</span></span>

<span data-ttu-id="38426-196">Üzerinde bir PowerShell oturumu başlatır `TestAgent1` ve yapılandırması için gereken DSC kaynakları içeren modülleri yükler.</span><span class="sxs-lookup"><span data-stu-id="38426-196">Starts a PowerShell session on `TestAgent1` and installs the modules containing the DSC resources required for the configuration.</span></span>

#### <a name="deployconfigs"></a><span data-ttu-id="38426-197">DeployConfigs</span><span class="sxs-lookup"><span data-stu-id="38426-197">DeployConfigs</span></span>

<span data-ttu-id="38426-198">Çağrıları [Başlat-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) yapılandırma çalıştırılacak cmdlet'i `TestAgent1`.</span><span class="sxs-lookup"><span data-stu-id="38426-198">Calls the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet to run the configuration on `TestAgent1`.</span></span>

#### <a name="integrationtests"></a><span data-ttu-id="38426-199">IntegrationTests</span><span class="sxs-lookup"><span data-stu-id="38426-199">IntegrationTests</span></span>

<span data-ttu-id="38426-200">Çalıştırmaları [Pester](https://github.com/pester/Pester/wiki) tümleştirme testleri.</span><span class="sxs-lookup"><span data-stu-id="38426-200">Runs the [Pester](https://github.com/pester/Pester/wiki) integration tests.</span></span>

#### <a name="acceptancetests"></a><span data-ttu-id="38426-201">AcceptanceTests</span><span class="sxs-lookup"><span data-stu-id="38426-201">AcceptanceTests</span></span>

<span data-ttu-id="38426-202">Çalıştırmaları [Pester](https://github.com/pester/Pester/wiki) kabul testleri.</span><span class="sxs-lookup"><span data-stu-id="38426-202">Runs the [Pester](https://github.com/pester/Pester/wiki) acceptance tests.</span></span>

#### <a name="clean"></a><span data-ttu-id="38426-203">Clean</span><span class="sxs-lookup"><span data-stu-id="38426-203">Clean</span></span>

<span data-ttu-id="38426-204">Önceki çalıştırmaları yüklü modüllerin kaldırır ve test sonucu klasör var olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="38426-204">Removes any modules installed in previous runs, and ensures that the test result folder exists.</span></span>

### <a name="test-scripts"></a><span data-ttu-id="38426-205">Test betikleri</span><span class="sxs-lookup"><span data-stu-id="38426-205">Test scripts</span></span>

<span data-ttu-id="38426-206">Kabul, tümleştirme ve birim testleri betiklerde tanımlanmış `Tests` klasörü (Demo_CI depo kökünden `./InfraDNS/Tests`), her adlı dosyaları `DNSServer.tests.ps1` kendi klasörlerine içinde.</span><span class="sxs-lookup"><span data-stu-id="38426-206">Acceptance, Integration, and Unit tests are defined in scripts in the `Tests` folder (from the root of the Demo_CI repository, `./InfraDNS/Tests`), each in files named `DNSServer.tests.ps1` in their respective folders.</span></span>

<span data-ttu-id="38426-207">Test betikleri kullanım [Pester](https://github.com/pester/Pester/wiki) ve [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) söz dizimi.</span><span class="sxs-lookup"><span data-stu-id="38426-207">The test scripts use [Pester](https://github.com/pester/Pester/wiki) and [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.</span></span>

#### <a name="unit-tests"></a><span data-ttu-id="38426-208">Birim testleri</span><span class="sxs-lookup"><span data-stu-id="38426-208">Unit tests</span></span>

<span data-ttu-id="38426-209">Birim test DSC yapılandırmaları kendilerini yapılandırmaları çalıştırdıklarında beklenen yapacağı emin olmak için test eder.</span><span class="sxs-lookup"><span data-stu-id="38426-209">The unit tests test the DSC configurations themselves to ensure that the configurations will do what is expected when they run.</span></span>
<span data-ttu-id="38426-210">Komut dosyası kullanan birim testi [Pester](https://github.com/pester/Pester/wiki).</span><span class="sxs-lookup"><span data-stu-id="38426-210">The unit test script uses [Pester](https://github.com/pester/Pester/wiki).</span></span>

#### <a name="integration-tests"></a><span data-ttu-id="38426-211">Tümleştirme testleri</span><span class="sxs-lookup"><span data-stu-id="38426-211">Integration tests</span></span>

<span data-ttu-id="38426-212">Tümleştirme testleri test yapılandırması sistemindeki diğer bileşenleri ile tümleştirildiğinde, sistem beklendiği şekilde yapılandırıldığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="38426-212">The integration tests test the configuration of the system to ensure that when integrated with other components, the system is configured as expected.</span></span> <span data-ttu-id="38426-213">DSC ile yapılandırıldıktan sonra bu testleri hedef düğümde çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="38426-213">These tests run on the target node after it has been configured with DSC.</span></span>
<span data-ttu-id="38426-214">Tümleştirme test betiği bir karışımını kullanır [Pester](https://github.com/pester/Pester/wiki) ve [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) söz dizimi.</span><span class="sxs-lookup"><span data-stu-id="38426-214">The integration test script uses a mixture of [Pester](https://github.com/pester/Pester/wiki) and [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.</span></span>

#### <a name="acceptance-tests"></a><span data-ttu-id="38426-215">Kabul testleri</span><span class="sxs-lookup"><span data-stu-id="38426-215">Acceptance tests</span></span>

<span data-ttu-id="38426-216">Kabul testleri beklendiği gibi davrandığından emin olmak için sistemi test edin.</span><span class="sxs-lookup"><span data-stu-id="38426-216">Acceptance tests test the system to ensure that it behaves as expected.</span></span>
<span data-ttu-id="38426-217">Örneğin, bir web sayfası doğru bilgileri sorgulandığında döndürür emin olmak için test eder.</span><span class="sxs-lookup"><span data-stu-id="38426-217">For example, it tests to ensure a web page returns the right information when queried.</span></span>
<span data-ttu-id="38426-218">Bu testleri uzaktan gerçek dünya senaryolarını test etmek için hedef düğümü çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="38426-218">These tests run remotely from the target node in order to test real world scenarios.</span></span>
<span data-ttu-id="38426-219">Tümleştirme test betiği bir karışımını kullanır [Pester](https://github.com/pester/Pester/wiki) ve [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) söz dizimi.</span><span class="sxs-lookup"><span data-stu-id="38426-219">The integration test script uses a mixture of [Pester](https://github.com/pester/Pester/wiki) and [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.</span></span>

## <a name="define-the-build"></a><span data-ttu-id="38426-220">Yapı tanımlama</span><span class="sxs-lookup"><span data-stu-id="38426-220">Define the build</span></span>

<span data-ttu-id="38426-221">TFS için Kodumuzun yükledikten ve ne işe yaradığını adresindeki, aranan derleme araçlarımızı tanımlayalım göre.</span><span class="sxs-lookup"><span data-stu-id="38426-221">Now that we've uploaded our code to TFS and looked at what it does, let's define our build.</span></span>

<span data-ttu-id="38426-222">Burada, biz yalnızca yapı ekleyeceksiniz derleme adımları ele alacağız.</span><span class="sxs-lookup"><span data-stu-id="38426-222">Here, we'll cover only the build steps that you'll add to the build.</span></span> <span data-ttu-id="38426-223">TFS'de bir yapı tanımı oluşturma hakkında yönergeler için bkz: [oluşturma ve derleme tanımını sıraya](/azure/devops/pipelines/get-started-designer).</span><span class="sxs-lookup"><span data-stu-id="38426-223">For instructions on how to create a build definition in TFS, see [Create and queue a build definition](/azure/devops/pipelines/get-started-designer).</span></span>

<span data-ttu-id="38426-224">Yeni bir derleme tanımı oluştur (seçin **boş** şablonu) "InfraDNS" adlı.</span><span class="sxs-lookup"><span data-stu-id="38426-224">Create a new build definition (select the **Empty** template) named "InfraDNS".</span></span>
<span data-ttu-id="38426-225">Aşağıdaki adımlar, yapı tanımı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="38426-225">Add the following steps to you build definition:</span></span>

- <span data-ttu-id="38426-226">PowerShell Betiği</span><span class="sxs-lookup"><span data-stu-id="38426-226">PowerShell Script</span></span>
- <span data-ttu-id="38426-227">Test sonuçlarını yayımlama</span><span class="sxs-lookup"><span data-stu-id="38426-227">Publish Test Results</span></span>
- <span data-ttu-id="38426-228">Dosyaları Kopyala</span><span class="sxs-lookup"><span data-stu-id="38426-228">Copy Files</span></span>
- <span data-ttu-id="38426-229">Yapıt yayımlama</span><span class="sxs-lookup"><span data-stu-id="38426-229">Publish Artifact</span></span>

<span data-ttu-id="38426-230">Bu derleme adımları, her bir adımın özelliklerini şu şekilde düzenlemek ekledikten sonra:</span><span class="sxs-lookup"><span data-stu-id="38426-230">After adding these build steps, edit the properties of each step as follows:</span></span>

### <a name="powershell-script"></a><span data-ttu-id="38426-231">PowerShell Betiği</span><span class="sxs-lookup"><span data-stu-id="38426-231">PowerShell Script</span></span>

1. <span data-ttu-id="38426-232">Ayarlama **türü** özelliğini `File Path`.</span><span class="sxs-lookup"><span data-stu-id="38426-232">Set the **Type** property to `File Path`.</span></span>
1. <span data-ttu-id="38426-233">Ayarlama **betik yolu** özelliğini `initiate.ps1`.</span><span class="sxs-lookup"><span data-stu-id="38426-233">Set the **Script Path** property to `initiate.ps1`.</span></span>
1. <span data-ttu-id="38426-234">Ekleme `-fileName build` için **bağımsız değişkenleri** özelliği.</span><span class="sxs-lookup"><span data-stu-id="38426-234">Add `-fileName build` to the **Arguments** property.</span></span>

<span data-ttu-id="38426-235">Bu derleme adımı `initiate.ps1` dosyasını psake derleme betiğini çağırır.</span><span class="sxs-lookup"><span data-stu-id="38426-235">This build step runs the `initiate.ps1` file, which calls the psake build script.</span></span>

### <a name="publish-test-results"></a><span data-ttu-id="38426-236">Test sonuçlarını yayımlama</span><span class="sxs-lookup"><span data-stu-id="38426-236">Publish Test Results</span></span>

1. <span data-ttu-id="38426-237">Ayarlama **Test sonucu biçimi** için `NUnit`</span><span class="sxs-lookup"><span data-stu-id="38426-237">Set **Test Result Format** to `NUnit`</span></span>
1. <span data-ttu-id="38426-238">Ayarlama **Test sonuçları dosyaları** için `InfraDNS/Tests/Results/*.xml`</span><span class="sxs-lookup"><span data-stu-id="38426-238">Set **Test Results Files** to `InfraDNS/Tests/Results/*.xml`</span></span>
1. <span data-ttu-id="38426-239">Ayarlama **Test çalıştırması başlığı** için `Unit`.</span><span class="sxs-lookup"><span data-stu-id="38426-239">Set **Test Run Title** to `Unit`.</span></span>
1. <span data-ttu-id="38426-240">Emin **denetimi seçenekleri** **etkin** ve **her zaman Çalıştır** seçili olan iki.</span><span class="sxs-lookup"><span data-stu-id="38426-240">Make sure **Control Options** **Enabled** and **Always run** are both selected.</span></span>

<span data-ttu-id="38426-241">Bu derleme adımı incelemiştik, daha önce Pester betikte birim testlerini çalıştırır ve sonuçları depolar `InfraDNS/Tests/Results/*.xml` klasör.</span><span class="sxs-lookup"><span data-stu-id="38426-241">This build step runs the unit tests in the Pester script we looked at earlier, and stores the results in the `InfraDNS/Tests/Results/*.xml` folder.</span></span>

### <a name="copy-files"></a><span data-ttu-id="38426-242">Dosyaları Kopyala</span><span class="sxs-lookup"><span data-stu-id="38426-242">Copy Files</span></span>

1. <span data-ttu-id="38426-243">Her biri aşağıdaki satırları ekleyin **içeriği**:</span><span class="sxs-lookup"><span data-stu-id="38426-243">Add each of the following lines to **Contents**:</span></span>

   ```
   initiate.ps1
   **\deploy.ps1
   **\Acceptance\**
   **\Integration\**
   ```

1. <span data-ttu-id="38426-244">Ayarlama **TargetFolder** için `$(Build.ArtifactStagingDirectory)\`</span><span class="sxs-lookup"><span data-stu-id="38426-244">Set **TargetFolder** to `$(Build.ArtifactStagingDirectory)\`</span></span>

<span data-ttu-id="38426-245">Bu adımı yapı kopyalar ve test betikleri hazırlama dizine kadar sonraki adım, derleme yapıları olarak yayımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="38426-245">This step copies the build and test scripts to the staging directory so that the can be published as build artifacts by the next step.</span></span>

### <a name="publish-artifact"></a><span data-ttu-id="38426-246">Yapıt yayımlama</span><span class="sxs-lookup"><span data-stu-id="38426-246">Publish Artifact</span></span>

1. <span data-ttu-id="38426-247">Ayarlama **yayımlama yolu** için `$(Build.ArtifactStagingDirectory)\`</span><span class="sxs-lookup"><span data-stu-id="38426-247">Set **Path to Publish** to `$(Build.ArtifactStagingDirectory)\`</span></span>
1. <span data-ttu-id="38426-248">Ayarlama **Yapıt adı** için `Deploy`</span><span class="sxs-lookup"><span data-stu-id="38426-248">Set **Artifact Name** to `Deploy`</span></span>
1. <span data-ttu-id="38426-249">Ayarlama **Yapıt türü** için `Server`</span><span class="sxs-lookup"><span data-stu-id="38426-249">Set **Artifact Type** to `Server`</span></span>
1. <span data-ttu-id="38426-250">Seçin `Enabled` içinde **Denetim seçenekleri**</span><span class="sxs-lookup"><span data-stu-id="38426-250">Select `Enabled` in **Control Options**</span></span>

## <a name="enable-continuous-integration"></a><span data-ttu-id="38426-251">Sürekli tümleştirmeyi etkinleştir</span><span class="sxs-lookup"><span data-stu-id="38426-251">Enable continuous integration</span></span>

<span data-ttu-id="38426-252">Biz, dilediğiniz zaman oluşturmak proje neden olan bir tetikleyici ayarlarsınız artık bir değişiklik için iade `ci-cd-example` git deponun dalı.</span><span class="sxs-lookup"><span data-stu-id="38426-252">Now we'll set up a trigger that causes the project to build any time a change is checked in to the `ci-cd-example` branch of the git repository.</span></span>

1. <span data-ttu-id="38426-253">TFS'de tıklayın **derleme ve yayınlama** sekmesi</span><span class="sxs-lookup"><span data-stu-id="38426-253">In TFS, click the **Build & Release** tab</span></span>
1. <span data-ttu-id="38426-254">Seçin `DNS Infra` derleme tanımı ve tıklayın **Düzenle**</span><span class="sxs-lookup"><span data-stu-id="38426-254">Select the `DNS Infra` build definition, and click **Edit**</span></span>
1. <span data-ttu-id="38426-255">Tıklayın **Tetikleyicileri** sekmesi</span><span class="sxs-lookup"><span data-stu-id="38426-255">Click the **Triggers** tab</span></span>
1. <span data-ttu-id="38426-256">Seçin **sürekli tümleştirme (CI)** seçip `refs/heads/ci-cd-example` dal aşağı açılan listesinde</span><span class="sxs-lookup"><span data-stu-id="38426-256">Select **Continuous integration (CI)**, and select `refs/heads/ci-cd-example` in the branch drop-down list</span></span>
1. <span data-ttu-id="38426-257">Tıklayın **Kaydet** ardından **Tamam**</span><span class="sxs-lookup"><span data-stu-id="38426-257">Click **Save** and then **OK**</span></span>

<span data-ttu-id="38426-258">Artık TFS git deposu Tetikleyicileri otomatik bir yapı değiştirin.</span><span class="sxs-lookup"><span data-stu-id="38426-258">Now any change in the TFS git repository triggers an automated build.</span></span>

## <a name="create-the-release-definition"></a><span data-ttu-id="38426-259">Yayın tanımı oluşturma</span><span class="sxs-lookup"><span data-stu-id="38426-259">Create the release definition</span></span>

<span data-ttu-id="38426-260">Böylece proje her kodu iade ile geliştirme ortamına dağıtılan bir yayın tanımı oluşturalım.</span><span class="sxs-lookup"><span data-stu-id="38426-260">Let's create a release definition so that the project is deployed to the development environment with every code check-in.</span></span>

<span data-ttu-id="38426-261">Bunu yapmak için ile ilişkili yeni bir yayın tanımı Ekle `InfraDNS` daha önce oluşturduğunuz tanımı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="38426-261">To do this, add a new release definition associated with the `InfraDNS` build definition you created previously.</span></span>
<span data-ttu-id="38426-262">Seçtiğinizden emin olun **sürekli dağıtım** böylece dilediğiniz zaman yeni bir derleme tamamlandığında yeni bir yayın tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="38426-262">Be sure to select **Continuous deployment** so that a new release will be triggered any time a new build is completed.</span></span>
<span data-ttu-id="38426-263">([Nasıl yapılır: Yayın tanımına iş](https://www.visualstudio.com/en-us/docs/build/actions/work-with-release-definitions)) ve şu şekilde yapılandırın:</span><span class="sxs-lookup"><span data-stu-id="38426-263">([How to: Work with release definitions](https://www.visualstudio.com/en-us/docs/build/actions/work-with-release-definitions)) and configure it as follows:</span></span>

<span data-ttu-id="38426-264">Aşağıdaki adımlar, yayın tanımına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="38426-264">Add the following steps to the release definition:</span></span>

- <span data-ttu-id="38426-265">PowerShell Betiği</span><span class="sxs-lookup"><span data-stu-id="38426-265">PowerShell Script</span></span>
- <span data-ttu-id="38426-266">Test sonuçlarını yayımlama</span><span class="sxs-lookup"><span data-stu-id="38426-266">Publish Test Results</span></span>
- <span data-ttu-id="38426-267">Test sonuçlarını yayımlama</span><span class="sxs-lookup"><span data-stu-id="38426-267">Publish Test Results</span></span>

<span data-ttu-id="38426-268">Adımları aşağıdaki gibi düzenleyin:</span><span class="sxs-lookup"><span data-stu-id="38426-268">Edit the steps as follows:</span></span>

### <a name="powershell-script"></a><span data-ttu-id="38426-269">PowerShell Betiği</span><span class="sxs-lookup"><span data-stu-id="38426-269">PowerShell Script</span></span>

1. <span data-ttu-id="38426-270">Ayarlama **betik yolu** alanı `$(Build.DefinitionName)\Deploy\initiate.ps1"`</span><span class="sxs-lookup"><span data-stu-id="38426-270">Set the **Script Path** field to `$(Build.DefinitionName)\Deploy\initiate.ps1"`</span></span>
1. <span data-ttu-id="38426-271">Ayarlama **bağımsız değişkenleri** alanı `-fileName Deploy`</span><span class="sxs-lookup"><span data-stu-id="38426-271">Set the **Arguments** field to `-fileName Deploy`</span></span>

### <a name="first-publish-test-results"></a><span data-ttu-id="38426-272">İlk Test sonuçlarını yayımlama</span><span class="sxs-lookup"><span data-stu-id="38426-272">First Publish Test Results</span></span>

1. <span data-ttu-id="38426-273">Seçin `NUnit` için **Test sonucu biçimi** alan</span><span class="sxs-lookup"><span data-stu-id="38426-273">Select `NUnit` for the **Test Result Format** field</span></span>
1. <span data-ttu-id="38426-274">Ayarlama **Test Sonuç dosyaları** alanı `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Integration*.xml`</span><span class="sxs-lookup"><span data-stu-id="38426-274">Set the **Test Result Files** field to `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Integration*.xml`</span></span>
1. <span data-ttu-id="38426-275">Ayarlama **Test çalıştırması başlığı** için `Integration`</span><span class="sxs-lookup"><span data-stu-id="38426-275">Set the **Test Run Title** to `Integration`</span></span>
1. <span data-ttu-id="38426-276">Altında **denetimi seçenekleri**, kontrol **her zaman çalıştır**</span><span class="sxs-lookup"><span data-stu-id="38426-276">Under **Control Options**, check **Always run**</span></span>

### <a name="second-publish-test-results"></a><span data-ttu-id="38426-277">İkinci Test sonuçlarını yayımlama</span><span class="sxs-lookup"><span data-stu-id="38426-277">Second Publish Test Results</span></span>

1. <span data-ttu-id="38426-278">Seçin `NUnit` için **Test sonucu biçimi** alan</span><span class="sxs-lookup"><span data-stu-id="38426-278">Select `NUnit` for the **Test Result Format** field</span></span>
1. <span data-ttu-id="38426-279">Ayarlama **Test Sonuç dosyaları** alanı `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Acceptance*.xml`</span><span class="sxs-lookup"><span data-stu-id="38426-279">Set the **Test Result Files** field to `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Acceptance*.xml`</span></span>
1. <span data-ttu-id="38426-280">Ayarlama **Test çalıştırması başlığı** için `Acceptance`</span><span class="sxs-lookup"><span data-stu-id="38426-280">Set the **Test Run Title** to `Acceptance`</span></span>
1. <span data-ttu-id="38426-281">Altında **denetimi seçenekleri**, kontrol **her zaman çalıştır**</span><span class="sxs-lookup"><span data-stu-id="38426-281">Under **Control Options**, check **Always run**</span></span>

## <a name="verify-your-results"></a><span data-ttu-id="38426-282">Sonuçları denetleyin</span><span class="sxs-lookup"><span data-stu-id="38426-282">Verify your results</span></span>

<span data-ttu-id="38426-283">Şimdi, istediğiniz zaman, değişiklikleri gönderir `ci-cd-example` dal TFS'de yeni bir derleme başlar.</span><span class="sxs-lookup"><span data-stu-id="38426-283">Now, any time you push changes in the `ci-cd-example` branch to TFS, a new build will start.</span></span>
<span data-ttu-id="38426-284">Derleme işlemi başarıyla tamamlarsa, yeni bir dağıtım tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="38426-284">If the build completes successfully, a new deployment is triggered.</span></span>

<span data-ttu-id="38426-285">İstemci makinesinde bir tarayıcı açıp giderek dağıtımının sonucu denetleyebilirsiniz `www.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="38426-285">You can check the result of the deployment by opening a browser on the client machine and navigating to `www.contoso.com`.</span></span>

## <a name="next-steps"></a><span data-ttu-id="38426-286">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="38426-286">Next steps</span></span>

<span data-ttu-id="38426-287">Bu örnek DNS sunucusunu yapılandırır `TestAgent1` böylece URL `www.contoso.com` çözümler `TestAgent2`, ancak bir Web sitesi gerçekten dağıtmaz.</span><span class="sxs-lookup"><span data-stu-id="38426-287">This example configures the DNS server `TestAgent1` so that the URL `www.contoso.com` resolves to `TestAgent2`, but it does not actually deploy a website.</span></span>
<span data-ttu-id="38426-288">Bunu yapmak için çatıyı altında deposunda sağlanan `WebApp` klasör.</span><span class="sxs-lookup"><span data-stu-id="38426-288">The skeleton for doing so is provided in the repo under the `WebApp` folder.</span></span>
<span data-ttu-id="38426-289">Kendi Web sitesini dağıtmak için psake betikleri, Pester testler ve DSC yapılandırmaları oluşturmak için sağlanan saptamalar kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="38426-289">You can use the stubs provided to create psake scripts, Pester tests, and DSC configurations to deploy your own website.</span></span>
