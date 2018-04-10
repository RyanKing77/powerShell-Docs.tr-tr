---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, yapılandırma, Kur
title: DSC sahip sürekli tümleştirme ve sürekli dağıtımı işlem hattı oluşturma
ms.openlocfilehash: a3803a8e6fe6ff1b93758a73ccd54754d7bb2a84
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="building-a-continuous-integration-and-continuous-deployment-pipeline-with-dsc"></a><span data-ttu-id="64954-103">DSC sahip sürekli tümleştirme ve sürekli dağıtımı işlem hattı oluşturma</span><span class="sxs-lookup"><span data-stu-id="64954-103">Building a Continuous Integration and Continuous Deployment pipeline with DSC</span></span>

<span data-ttu-id="64954-104">Bu örnek bir sürekli tümleştirme/sürekli dağıtımı (CI/CD) ardışık PowerShell, DSC, Pester ve Visual Studio Team Foundation Server (TFS) kullanarak nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="64954-104">This example demonstrates how to build a Continuous Integration/Continuous Deployment (CI/CD) pipeline by using PowerShell, DSC, Pester, and Visual Studio Team Foundation Server (TFS).</span></span>

<span data-ttu-id="64954-105">Ardışık Düzen yerleşik yapılandırıldıktan sonra tam olarak dağıtmak, yapılandırmak ve bir DNS sunucusu sınamak için kullanabilir ve ana bilgisayar kayıtları ilişkili.</span><span class="sxs-lookup"><span data-stu-id="64954-105">After the pipeline is built and configured, you can use it to fully deploy, configure and test a DNS server and associated host records.</span></span>
<span data-ttu-id="64954-106">Bu işlem bir geliştirme ortamında kullanılacak bir ardışık düzen ilk bölümü benzetimini yapar.</span><span class="sxs-lookup"><span data-stu-id="64954-106">This process simulates the first part of a pipeline that would be used in a development environment.</span></span>

<span data-ttu-id="64954-107">Daha güvenilir bir şekilde tüm kod sınanır ve kodunuzun geçerli bir yapı olduğundan emin olduktan kullanılabilir her zaman ve otomatik bir CI/CD ardışık yazılım daha hızlı güncelleştirmenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="64954-107">An automated CI/CD pipeline helps you update software faster and more reliably, ensuring that all code is tested, and that a current build of your code is available at all times.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="64954-108">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="64954-108">Prerequisites</span></span>

<span data-ttu-id="64954-109">Bu örneği kullanmak için aşağıdaki bilgi sahibi olmanız:</span><span class="sxs-lookup"><span data-stu-id="64954-109">To use this example, you should be familiar with the following:</span></span>

- <span data-ttu-id="64954-110">CI CD kavramlar.</span><span class="sxs-lookup"><span data-stu-id="64954-110">CI-CD concepts.</span></span> <span data-ttu-id="64954-111">İyi bir başvuru bulunabilir [yayın ardışık düzen modeli](http://aka.ms/thereleasepipelinemodelpdf).</span><span class="sxs-lookup"><span data-stu-id="64954-111">A good reference can be found at [The Release Pipeline Model](http://aka.ms/thereleasepipelinemodelpdf).</span></span>
- <span data-ttu-id="64954-112">[Git](https://git-scm.com/) kaynak denetimi</span><span class="sxs-lookup"><span data-stu-id="64954-112">[Git](https://git-scm.com/) source control</span></span>
- <span data-ttu-id="64954-113">[Pester](https://github.com/pester/Pester) framework test etme</span><span class="sxs-lookup"><span data-stu-id="64954-113">The [Pester](https://github.com/pester/Pester) testing framework</span></span>
- [<span data-ttu-id="64954-114">Team Foundation Server</span><span class="sxs-lookup"><span data-stu-id="64954-114">Team Foundation Server</span></span>](https://www.visualstudio.com/tfs/)

## <a name="what-you-will-need"></a><span data-ttu-id="64954-115">İhtiyacınız olacak</span><span class="sxs-lookup"><span data-stu-id="64954-115">What you will need</span></span>

<span data-ttu-id="64954-116">Derleme ve bu örneği çalıştırmak için çeşitli bilgisayarlar ve/veya sanal makineleri olan bir ortamda gerekir.</span><span class="sxs-lookup"><span data-stu-id="64954-116">To build and run this example, you will need an environment with several computers and/or virtual machines.</span></span>

### <a name="client"></a><span data-ttu-id="64954-117">İstemci</span><span class="sxs-lookup"><span data-stu-id="64954-117">Client</span></span>

<span data-ttu-id="64954-118">Bu, tüm ayarlama ve örnek çalışan iş yeri gerçekleştirirsiniz bilgisayardır.</span><span class="sxs-lookup"><span data-stu-id="64954-118">This is the computer where you'll do all of the work setting up and running the example.</span></span>

<span data-ttu-id="64954-119">İstemci bilgisayar bir Windows bilgisayara aşağıdakilerin yüklü olması gerekir:</span><span class="sxs-lookup"><span data-stu-id="64954-119">The client computer must be a Windows computer with the following installed:</span></span>
- [<span data-ttu-id="64954-120">Git</span><span class="sxs-lookup"><span data-stu-id="64954-120">Git</span></span>](https://git-scm.com/)
- <span data-ttu-id="64954-121">öğesinden kopyalanan bir yerel git deposu https://github.com/PowerShell/Demo_CI</span><span class="sxs-lookup"><span data-stu-id="64954-121">a local git repo cloned from https://github.com/PowerShell/Demo_CI</span></span>
- <span data-ttu-id="64954-122">bir metin düzenleyicisi gibi [Visual Studio Code](https://code.visualstudio.com/)</span><span class="sxs-lookup"><span data-stu-id="64954-122">a text editor, such as [Visual Studio Code](https://code.visualstudio.com/)</span></span>

### <a name="tfssrv1"></a><span data-ttu-id="64954-123">TFSSrv1</span><span class="sxs-lookup"><span data-stu-id="64954-123">TFSSrv1</span></span>

<span data-ttu-id="64954-124">Tanımladığınız yapınızın TFS sunucusu barındıran bilgisayarda ve bırakın.</span><span class="sxs-lookup"><span data-stu-id="64954-124">The computer that hosts the TFS server where you will define your build and release.</span></span>
<span data-ttu-id="64954-125">Bu bilgisayarda [Team Foundation Server 2017](https://www.visualstudio.com/tfs/) yüklü.</span><span class="sxs-lookup"><span data-stu-id="64954-125">This computer must have [Team Foundation Server 2017](https://www.visualstudio.com/tfs/) installed.</span></span>

### <a name="buildagent"></a><span data-ttu-id="64954-126">BuildAgent</span><span class="sxs-lookup"><span data-stu-id="64954-126">BuildAgent</span></span>

<span data-ttu-id="64954-127">Windows çalıştıran bilgisayar proje derlemeler Aracısı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="64954-127">The computer that runs the Windows build agent that builds the project.</span></span>
<span data-ttu-id="64954-128">Bu bilgisayarda yüklü ve çalışan aracısını Windows olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="64954-128">This computer must have a Windows build agent installed and running.</span></span>
<span data-ttu-id="64954-129">Bkz: [Windows'da bir aracı dağıtmak](https://www.visualstudio.com/en-us/docs/build/actions/agents/v2-windows) yapı aracısını yüklemek ve bir Windows çalıştırmak yönergeler için.</span><span class="sxs-lookup"><span data-stu-id="64954-129">See [Deploy an agent on Windows](https://www.visualstudio.com/en-us/docs/build/actions/agents/v2-windows) for instructions on how to install and run a Windows build agent.</span></span>

<span data-ttu-id="64954-130">Her ikisi de yüklemeniz gerekir `xDnsServer` ve `xNetworking` bu bilgisayarda DSC modüller.</span><span class="sxs-lookup"><span data-stu-id="64954-130">You also need to install both the `xDnsServer` and `xNetworking` DSC modules on this computer.</span></span>

### <a name="testagent1"></a><span data-ttu-id="64954-131">TestAgent1</span><span class="sxs-lookup"><span data-stu-id="64954-131">TestAgent1</span></span>

<span data-ttu-id="64954-132">Bu örnekte DSC yapılandırması tarafından bir DNS sunucusu olarak yapılandırılan bilgisayardır.</span><span class="sxs-lookup"><span data-stu-id="64954-132">This is the computer that is configured as a DNS server by the DSC configuration in this example.</span></span>
<span data-ttu-id="64954-133">Bilgisayar çalıştırmalıdır [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span><span class="sxs-lookup"><span data-stu-id="64954-133">The computer must be running [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span></span>

### <a name="testagent2"></a><span data-ttu-id="64954-134">TestAgent2</span><span class="sxs-lookup"><span data-stu-id="64954-134">TestAgent2</span></span>

<span data-ttu-id="64954-135">Bu örnek yapılandırır Web sitesini barındıran bilgisayar budur.</span><span class="sxs-lookup"><span data-stu-id="64954-135">This is the computer that hosts the website this example configures.</span></span>
<span data-ttu-id="64954-136">Bilgisayar çalıştırmalıdır [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span><span class="sxs-lookup"><span data-stu-id="64954-136">The computer must be running [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span></span>

## <a name="add-the-code-to-tfs"></a><span data-ttu-id="64954-137">TFS için kod ekleme</span><span class="sxs-lookup"><span data-stu-id="64954-137">Add the code to TFS</span></span>

<span data-ttu-id="64954-138">Bir Git deposu TFS'de oluşturarak ve istemci bilgisayardaki yerel deponuza kodunu alma başlayacağız.</span><span class="sxs-lookup"><span data-stu-id="64954-138">We'll start out by creating a Git repository in TFS, and importing the code from your local repository on the client computer.</span></span>
<span data-ttu-id="64954-139">Zaten Demo_CI depo istemci bilgisayarınıza kopyaladığınız değil, artık aşağıdaki git komutu çalıştırarak yapın:</span><span class="sxs-lookup"><span data-stu-id="64954-139">If you have not already cloned the Demo_CI repository to your client computer, do so now by running the following git command:</span></span>

`git clone https://github.com/PowerShell/Demo_CI`

1. <span data-ttu-id="64954-140">İstemci bilgisayarınızda, TFS sunucunuz bir web tarayıcısında gidin.</span><span class="sxs-lookup"><span data-stu-id="64954-140">On your client computer, navigate to your TFS server in a web browser.</span></span>
1. <span data-ttu-id="64954-141">TFS, [yeni takım projesi oluşturma](https://www.visualstudio.com/en-us/docs/setup-admin/create-team-project) Demo_CI adlı.</span><span class="sxs-lookup"><span data-stu-id="64954-141">In TFS, [Create a new team project](https://www.visualstudio.com/en-us/docs/setup-admin/create-team-project) named Demo_CI.</span></span>

    <span data-ttu-id="64954-142">Olduğundan emin olun **sürüm denetimi** ayarlanır **Git**.</span><span class="sxs-lookup"><span data-stu-id="64954-142">Make sure that **Version control** is set to **Git**.</span></span>
1. <span data-ttu-id="64954-143">İstemci bilgisayarınızda, bir uzak aşağıdaki komutla TFS'de yeni oluşturduğunuz deponuza ekleyin:</span><span class="sxs-lookup"><span data-stu-id="64954-143">On your client computer, add a remote to the repository you just created in TFS with the following command:</span></span>

    `git remote add tfs <YourTFSRepoURL>`

    <span data-ttu-id="64954-144">Burada `<YourTFSRepoURL>` önceki adımda oluşturduğunuz TFS deponuza kopya URL.</span><span class="sxs-lookup"><span data-stu-id="64954-144">Where `<YourTFSRepoURL>` is the clone URL to the TFS repository you created in the previous step.</span></span>

    <span data-ttu-id="64954-145">Bu URL nerede bulacağını bilmiyorsanız, bkz: [var olan bir Git deposuna kopyalama](https://www.visualstudio.com/en-us/docs/git/tutorial/clone).</span><span class="sxs-lookup"><span data-stu-id="64954-145">If you don't know where to find this URL, see [Clone an existing Git repo](https://www.visualstudio.com/en-us/docs/git/tutorial/clone).</span></span>
1. <span data-ttu-id="64954-146">Kod yerel depodan aşağıdaki komutla TFS deponuza iletin:</span><span class="sxs-lookup"><span data-stu-id="64954-146">Push the code from your local repository to your TFS repository with the following command:</span></span>

    `git push tfs --all`
1. <span data-ttu-id="64954-147">TFS depo Demo_CI kodu ile doldurulur.</span><span class="sxs-lookup"><span data-stu-id="64954-147">The TFS repository will be populated with the Demo_CI code.</span></span>

><span data-ttu-id="64954-148">**Not:** Bu örnek kodda kullanır `ci-cd-example` Git deposuna dalı.</span><span class="sxs-lookup"><span data-stu-id="64954-148">**Note:** This example uses the code in the `ci-cd-example` branch of the Git repo.</span></span>
><span data-ttu-id="64954-149">TFS projenizin ve oluşturduğunuz CI/CD Tetikleyiciler için varsayılan dalı olarak bu dal belirttiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="64954-149">Be sure to specify this branch as the default branch in your TFS project, and for the CI/CD triggers you create.</span></span>

## <a name="understanding-the-code"></a><span data-ttu-id="64954-150">Kodu anlama</span><span class="sxs-lookup"><span data-stu-id="64954-150">Understanding the code</span></span>

<span data-ttu-id="64954-151">Derleme ve dağıtım ardışık düzen oluşturuyoruz önce neler olup bittiğini anlamak için kodu bazıları bakalım.</span><span class="sxs-lookup"><span data-stu-id="64954-151">Before we create the build and deployment pipelines, let's look at some of the code to understand what is going on.</span></span>
<span data-ttu-id="64954-152">İstemci bilgisayarınızda, sık kullandığınız metin düzenleyiciyi açın ve Demo_CI Git deponuzu kök dizinine gidin.</span><span class="sxs-lookup"><span data-stu-id="64954-152">On your client computer, open your favorite text editor and navigate to the root of your Demo_CI Git repository.</span></span>

### <a name="the-dsc-configuration"></a><span data-ttu-id="64954-153">DSC yapılandırması</span><span class="sxs-lookup"><span data-stu-id="64954-153">The DSC configuration</span></span>

<span data-ttu-id="64954-154">Dosyayı açmak `DNSServer.ps1` (yerel Demo_CI depo kök `./InfraDNS/Configs/DNSServer.ps1`).</span><span class="sxs-lookup"><span data-stu-id="64954-154">Open the file `DNSServer.ps1` (from the root of the local Demo_CI repository, `./InfraDNS/Configs/DNSServer.ps1`).</span></span>

<span data-ttu-id="64954-155">Bu dosya, DNS sunucusunu ayarlar DSC yapılandırması içerir.</span><span class="sxs-lookup"><span data-stu-id="64954-155">This file contains the DSC configuration that sets up the DNS server.</span></span> <span data-ttu-id="64954-156">Aşağıda tamamının verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="64954-156">Here it is in its entirety:</span></span>

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

<span data-ttu-id="64954-157">Bildirim `Node` deyimi:</span><span class="sxs-lookup"><span data-stu-id="64954-157">Notice the `Node` statement:</span></span>

```powershell
Node $AllNodes.Where{$_.Role -eq 'DNSServer'}.NodeName
```

<span data-ttu-id="64954-158">Bu rolü sahip olarak tanımlanmış olan tüm düğümleri bulur `DNSServer` içinde [yapılandırma verilerini](configData.md), tarafından oluşturulan `DevEnv.ps1` komut dosyası.</span><span class="sxs-lookup"><span data-stu-id="64954-158">This finds any nodes that were defined as having a role of `DNSServer` in the [configuration data](configData.md), which is created by the `DevEnv.ps1` script.</span></span>

<span data-ttu-id="64954-159">Düğümleri tanımlamak için yapılandırma verilerini kullanarak CI çünkü düğüm bilgi büyük olasılıkla ortamlar arasında değişir ve yapılandırma verilerini kullanarak kolayca düğümü bilgileri yapılandırma kodunu değiştirmeden değişiklik sağlar yapmak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="64954-159">Using configuration data to define nodes is important when doing CI because node information will likely change between environments, and using configuration data allows you to easily make changes to node information without changing the configuration code.</span></span>

<span data-ttu-id="64954-160">İlk kaynak bloğunda yapılandırma çağırır [WindowsFeature](windowsFeatureResource.md) DNS özelliği etkinleştirildiğinden emin olmak için.</span><span class="sxs-lookup"><span data-stu-id="64954-160">In the first resource block, the configuration calls the [WindowsFeature](windowsFeatureResource.md) to ensure that the DNS feature is enabled.</span></span>
<span data-ttu-id="64954-161">Çağrı kaynaklardan izleyin kaynak blokları [xDnsServer](https://github.com/PowerShell/xDnsServer) modülünü birincil bölge ve DNS kayıtlarını yapılandırmak için.</span><span class="sxs-lookup"><span data-stu-id="64954-161">The resource blocks that follow call resources from the [xDnsServer](https://github.com/PowerShell/xDnsServer) module to configure the primary zone and DNS records.</span></span>

<span data-ttu-id="64954-162">Dikkat iki `xDnsRecord` blokları sarılır `foreach` yapılandırma verilerini dizilerde yinelemek döngüler.</span><span class="sxs-lookup"><span data-stu-id="64954-162">Notice that the two `xDnsRecord` blocks are wrapped in `foreach` loops that iterate through arrays in the configuration data.</span></span>
<span data-ttu-id="64954-163">Yapılandırma verilerini tarafından yeniden oluşturulan `DevEnv.ps1` biz sonraki göreceğiz komut dosyası.</span><span class="sxs-lookup"><span data-stu-id="64954-163">Again, the configuration data is created by the `DevEnv.ps1` script, which we'll look at next.</span></span>

### <a name="configuration-data"></a><span data-ttu-id="64954-164">Yapılandırma verileri</span><span class="sxs-lookup"><span data-stu-id="64954-164">Configuration data</span></span>

<span data-ttu-id="64954-165">`DevEnv.ps1` Dosyası (yerel Demo_CI depo kök `./InfraDNS/DevEnv.ps1`) ortama özgü yapılandırma verilerini bir hashtable belirtir ve ardından bir çağrı bu hashtable geçirir `New-DscConfigurationDataDocument` içindetanımlananişlevi`DscPipelineTools.psm` (`./Assets/DscPipelineTools/DscPipelineTools.psm1`).</span><span class="sxs-lookup"><span data-stu-id="64954-165">The `DevEnv.ps1` file (from the root of the local Demo_CI repository, `./InfraDNS/DevEnv.ps1`) specifies the environment-specific configuration data in a hashtable, and then passes that hashtable to a call to the `New-DscConfigurationDataDocument` function, which is defined in `DscPipelineTools.psm` (`./Assets/DscPipelineTools/DscPipelineTools.psm1`).</span></span>

<span data-ttu-id="64954-166">`DevEnv.ps1` Dosyası:</span><span class="sxs-lookup"><span data-stu-id="64954-166">The `DevEnv.ps1` file:</span></span>

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

<span data-ttu-id="64954-167">`New-DscConfigurationDataDocument` İşlevi (tanımlanan `\Assets\DscPipelineTools\DscPipelineTools.psm1`) programlı olarak geçirilen hashtable (düğüm veri) ve dizi (düğüm olmayan veriler) yapılandırma verileri belgesi oluşturur `RawEnvData` ve `OtherEnvData` parametreleri.</span><span class="sxs-lookup"><span data-stu-id="64954-167">The `New-DscConfigurationDataDocument` function (defined in `\Assets\DscPipelineTools\DscPipelineTools.psm1`) programmatically creates a configuration data document from the hashtable (node data) and array (non-node data) that are passed as the `RawEnvData` and `OtherEnvData` parameters.</span></span>

<span data-ttu-id="64954-168">Bu örnekte, yalnızca `RawEnvData` parametresi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="64954-168">In our case, only the `RawEnvData` parameter is used.</span></span>

### <a name="the-psake-build-script"></a><span data-ttu-id="64954-169">Psake derleme betiğindeki</span><span class="sxs-lookup"><span data-stu-id="64954-169">The psake build script</span></span>

<span data-ttu-id="64954-170">[Psake](https://github.com/psake/psake) tanımlanan komut dosyası derleme `Build.ps1` (Demo_CI depo kök `./InfraDNS/Build.ps1`) yapının bir parçası olan görevleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="64954-170">The [psake](https://github.com/psake/psake) build script defined in `Build.ps1` (from the root of the Demo_CI repository, `./InfraDNS/Build.ps1`) defines tasks that are part of the build.</span></span>
<span data-ttu-id="64954-171">Ayrıca, her görevin bağımlı diğer görevleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="64954-171">It also defines which other tasks each task depends on.</span></span>
<span data-ttu-id="64954-172">Psake betik çağrıldığında, belirtilen görev sağlar (veya adlı görev `Default` belirtilmemişse) çalıştırır ve tüm bağımlılıkları da çalıştırın (bağımlılıkları bağımlılıklarını çalıştırmak için bu, yinelemelidir ve benzeri).</span><span class="sxs-lookup"><span data-stu-id="64954-172">When invoked, the psake script ensures that the specified task (or the task named `Default` if none is specified) runs, and that all dependencies also run (this is recursive, so that dependencies of dependencies run, and so on).</span></span>

<span data-ttu-id="64954-173">Bu örnekte, `Default` görev olarak tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="64954-173">In this example, the `Default` task is defined as:</span></span>

```powershell
Task Default -depends UnitTests
```

<span data-ttu-id="64954-174">`Default` Görev hiçbir uygulama, ancak bir bağımlılık içeriyor `CompileConfigs` görev.</span><span class="sxs-lookup"><span data-stu-id="64954-174">The `Default` task has no implementation itself, but has a dependency on the `CompileConfigs` task.</span></span>
<span data-ttu-id="64954-175">Görev bağımlılıkları elde edilen zincirine derleme betiğindeki tüm görevler çalıştırılan sağlar.</span><span class="sxs-lookup"><span data-stu-id="64954-175">The resulting chain of task dependencies ensures that all tasks in the build script are run.</span></span>

<span data-ttu-id="64954-176">Bu örnekte, psake komut dosyası için bir çağrı tarafından çağrılan `Invoke-PSake` içinde `Initiate.ps1` dosyası (Demo_CI depo kök dizininde bulunan):</span><span class="sxs-lookup"><span data-stu-id="64954-176">In this example, the psake script is invoked by a call to `Invoke-PSake` in the `Initiate.ps1` file (located at the root of the Demo_CI repository):</span></span>

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

<span data-ttu-id="64954-177">Biz TFS örneğimizde için derleme tanımını oluşturduğunuzda, biz bizim psake komut dosyası olarak sağlayacak `fileName` bu komut için parametre.</span><span class="sxs-lookup"><span data-stu-id="64954-177">When we create the build definition for our example in TFS, we will supply our psake script file as the `fileName` parameter for this script.</span></span>

<span data-ttu-id="64954-178">Derleme betiğinin aşağıdaki görevleri tanımlar:</span><span class="sxs-lookup"><span data-stu-id="64954-178">The build script defines the following tasks:</span></span>

#### <a name="generateenvironmentfiles"></a><span data-ttu-id="64954-179">GenerateEnvironmentFiles</span><span class="sxs-lookup"><span data-stu-id="64954-179">GenerateEnvironmentFiles</span></span>

<span data-ttu-id="64954-180">Çalıştırır `DevEnv.ps1`, yapılandırma veri dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="64954-180">Runs `DevEnv.ps1`, which generates the configuration data file.</span></span>

#### <a name="installmodules"></a><span data-ttu-id="64954-181">InstallModules</span><span class="sxs-lookup"><span data-stu-id="64954-181">InstallModules</span></span>

<span data-ttu-id="64954-182">Yapılandırma tarafından gerekli modüllerini yükler `DNSServer.ps1`.</span><span class="sxs-lookup"><span data-stu-id="64954-182">Installs the modules required by the configuration `DNSServer.ps1`.</span></span>

#### <a name="scriptanalysis"></a><span data-ttu-id="64954-183">ScriptAnalysis</span><span class="sxs-lookup"><span data-stu-id="64954-183">ScriptAnalysis</span></span>

<span data-ttu-id="64954-184">Çağrıları [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer).</span><span class="sxs-lookup"><span data-stu-id="64954-184">Calls the [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer).</span></span>

#### <a name="unittests"></a><span data-ttu-id="64954-185">UnitTests</span><span class="sxs-lookup"><span data-stu-id="64954-185">UnitTests</span></span>

<span data-ttu-id="64954-186">Çalıştırır [Pester](https://github.com/pester/Pester/wiki) birim testleri.</span><span class="sxs-lookup"><span data-stu-id="64954-186">Runs the [Pester](https://github.com/pester/Pester/wiki) unit tests.</span></span>

#### <a name="compileconfigs"></a><span data-ttu-id="64954-187">CompileConfigs</span><span class="sxs-lookup"><span data-stu-id="64954-187">CompileConfigs</span></span>

<span data-ttu-id="64954-188">Yapılandırma derler (`DNSServer.ps1`) tarafından oluşturulan yapılandırma verilerini bir MOF dosyasına kullanarak `GenerateEnvironmentFiles` görev.</span><span class="sxs-lookup"><span data-stu-id="64954-188">Compiles the configuration (`DNSServer.ps1`) into a MOF file, using the configuration data generated by the `GenerateEnvironmentFiles` task.</span></span>

#### <a name="clean"></a><span data-ttu-id="64954-189">Clean</span><span class="sxs-lookup"><span data-stu-id="64954-189">Clean</span></span>

<span data-ttu-id="64954-190">Örnek için kullanılan klasörleri oluşturur ve tüm test sonuçları, yapılandırma veri dosyaları ve modüller önceki dosyadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="64954-190">Creates the folders used for the example, and removes any test results, configuration data files, and modules from previous runs.</span></span>

### <a name="the-psake-deploy-script"></a><span data-ttu-id="64954-191">Psake komut dosyası dağıtma</span><span class="sxs-lookup"><span data-stu-id="64954-191">The psake deploy script</span></span>

<span data-ttu-id="64954-192">[Psake](https://github.com/psake/psake) tanımlanan dağıtım betiği `Deploy.ps1` (Demo_CI depo kök `./InfraDNS/Deploy.ps1`) dağıtma ve yapılandırma çalıştırma görevleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="64954-192">The [psake](https://github.com/psake/psake) deployment script defined in `Deploy.ps1` (from the root of the Demo_CI repository, `./InfraDNS/Deploy.ps1`) defines tasks that deploy and run the configuration.</span></span>

<span data-ttu-id="64954-193">`Deploy.ps1` Aşağıdaki görevleri tanımlar:</span><span class="sxs-lookup"><span data-stu-id="64954-193">`Deploy.ps1` defines the following tasks:</span></span>

#### <a name="deploymodules"></a><span data-ttu-id="64954-194">DeployModules</span><span class="sxs-lookup"><span data-stu-id="64954-194">DeployModules</span></span>

<span data-ttu-id="64954-195">Üzerinde bir PowerShell oturumu başlatır `TestAgent1` ve yapılandırma için gerekli DSC kaynakları içeren modüller yükler.</span><span class="sxs-lookup"><span data-stu-id="64954-195">Starts a PowerShell session on `TestAgent1` and installs the modules containing the DSC resources required for the configuration.</span></span>

#### <a name="deployconfigs"></a><span data-ttu-id="64954-196">DeployConfigs</span><span class="sxs-lookup"><span data-stu-id="64954-196">DeployConfigs</span></span>

<span data-ttu-id="64954-197">Çağrıları [başlangıç DscConfiguration](/reference/5.1/PSDesiredStateConfiguration/Start-DscConfiguration.md) yapılandırma çalıştırmak için cmdlet `TestAgent1`.</span><span class="sxs-lookup"><span data-stu-id="64954-197">Calls the [Start-DscConfiguration](/reference/5.1/PSDesiredStateConfiguration/Start-DscConfiguration.md) cmdlet to run the configuration on `TestAgent1`.</span></span>

#### <a name="integrationtests"></a><span data-ttu-id="64954-198">IntegrationTests</span><span class="sxs-lookup"><span data-stu-id="64954-198">IntegrationTests</span></span>

<span data-ttu-id="64954-199">Çalıştırır [Pester](https://github.com/pester/Pester/wiki) tümleştirme testleri.</span><span class="sxs-lookup"><span data-stu-id="64954-199">Runs the [Pester](https://github.com/pester/Pester/wiki) integration tests.</span></span>

#### <a name="acceptancetests"></a><span data-ttu-id="64954-200">AcceptanceTests</span><span class="sxs-lookup"><span data-stu-id="64954-200">AcceptanceTests</span></span>

<span data-ttu-id="64954-201">Çalıştırır [Pester](https://github.com/pester/Pester/wiki) kabul testleri.</span><span class="sxs-lookup"><span data-stu-id="64954-201">Runs the [Pester](https://github.com/pester/Pester/wiki) acceptance tests.</span></span>

#### <a name="clean"></a><span data-ttu-id="64954-202">Clean</span><span class="sxs-lookup"><span data-stu-id="64954-202">Clean</span></span>

<span data-ttu-id="64954-203">Önceki çalıştırmalarında yüklü tüm modüllerin kaldırır ve test sonucu klasörün var olduğunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="64954-203">Removes any modules installed in previous runs, and ensures that the test result folder exists.</span></span>

### <a name="test-scripts"></a><span data-ttu-id="64954-204">Test komut dosyaları</span><span class="sxs-lookup"><span data-stu-id="64954-204">Test scripts</span></span>

<span data-ttu-id="64954-205">Kabul, tümleştirme ve birim testlerini komut dosyalarında tanımlanmış `Tests` klasörü (Demo_CI depo kök `./InfraDNS/Tests`), her adlı dosyaları `DNSServer.tests.ps1` ilgili klasörlerine içinde.</span><span class="sxs-lookup"><span data-stu-id="64954-205">Acceptance, Integration, and Unit tests are defined in scripts in the `Tests` folder (from the root of the Demo_CI repository, `./InfraDNS/Tests`), each in files named `DNSServer.tests.ps1` in their respective folders.</span></span>

<span data-ttu-id="64954-206">Test komut dosyası kullan [Pester](https://github.com/pester/Pester/wiki) ve [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) sözdizimi.</span><span class="sxs-lookup"><span data-stu-id="64954-206">The test scripts use [Pester](https://github.com/pester/Pester/wiki) and [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.</span></span>

#### <a name="unit-tests"></a><span data-ttu-id="64954-207">Birim testleri</span><span class="sxs-lookup"><span data-stu-id="64954-207">Unit tests</span></span>

<span data-ttu-id="64954-208">Birim testi DSC yapılandırmaları kendilerini yapılandırmaları çalıştırdıklarında gerekenin yapacağınız emin olmak için test eder.</span><span class="sxs-lookup"><span data-stu-id="64954-208">The unit tests test the DSC configurations themselves to ensure that the configurations will do what is expected when they run.</span></span>
<span data-ttu-id="64954-209">Komut dosyası kullanan birim testi [Pester](https://github.com/pester/Pester/wiki).</span><span class="sxs-lookup"><span data-stu-id="64954-209">The unit test script uses [Pester](https://github.com/pester/Pester/wiki).</span></span>

#### <a name="integration-tests"></a><span data-ttu-id="64954-210">Tümleştirme testleri</span><span class="sxs-lookup"><span data-stu-id="64954-210">Integration tests</span></span>

<span data-ttu-id="64954-211">Tümleştirme testleri diğer bileşenlerle tümleştirildiğinde sistem beklendiği şekilde yapılandırıldığından emin olmak için sistem yapılandırmasını sınayın.</span><span class="sxs-lookup"><span data-stu-id="64954-211">The integration tests test the configuration of the system to ensure that when integrated with other components, the system is configured as expected.</span></span> <span data-ttu-id="64954-212">DSC ile yapılandırıldıktan sonra hedef düğümde bu testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="64954-212">These tests run on the target node after it has been configured with DSC.</span></span>
<span data-ttu-id="64954-213">Bir karışımını tümleştirme test betiğini kullanır [Pester](https://github.com/pester/Pester/wiki) ve [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) sözdizimi.</span><span class="sxs-lookup"><span data-stu-id="64954-213">The integration test script uses a mixture of [Pester](https://github.com/pester/Pester/wiki) and [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.</span></span>

#### <a name="acceptance-tests"></a><span data-ttu-id="64954-214">Kabul testleri</span><span class="sxs-lookup"><span data-stu-id="64954-214">Acceptance tests</span></span>

<span data-ttu-id="64954-215">Kabul testleri sistem beklendiği gibi davranır emin olmak için test edin.</span><span class="sxs-lookup"><span data-stu-id="64954-215">Acceptance tests test the system to ensure that it behaves as expected.</span></span>
<span data-ttu-id="64954-216">Örneğin, bir web sayfası doğru bilgileri sorgulandığında döndürür emin olmak için sınar.</span><span class="sxs-lookup"><span data-stu-id="64954-216">For example, it tests to ensure a web page returns the right information when queried.</span></span>
<span data-ttu-id="64954-217">Bu testler hedef düğümden gerçek dünya senaryoları test etmek amacıyla uzaktan çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="64954-217">These tests run remotely from the target node in order to test real world scenarios.</span></span>
<span data-ttu-id="64954-218">Bir karışımını tümleştirme test betiğini kullanır [Pester](https://github.com/pester/Pester/wiki) ve [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) sözdizimi.</span><span class="sxs-lookup"><span data-stu-id="64954-218">The integration test script uses a mixture of [Pester](https://github.com/pester/Pester/wiki) and [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.</span></span>

## <a name="define-the-build"></a><span data-ttu-id="64954-219">Yapı tanımlayın</span><span class="sxs-lookup"><span data-stu-id="64954-219">Define the build</span></span>

<span data-ttu-id="64954-220">TFS için kodumuza karşıya artık ve bunu yapar Aranan göre şimdi bizim yapı tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="64954-220">Now that we've uploaded our code to TFS and looked at what it does, let's define our build.</span></span>

<span data-ttu-id="64954-221">Burada, biz yalnızca yapı ekleyeceksiniz oluşturma adımlarının ele alacağız.</span><span class="sxs-lookup"><span data-stu-id="64954-221">Here, we'll cover only the build steps that you'll add to the build.</span></span> <span data-ttu-id="64954-222">Yapı tanımı içinde TFS oluşturma hakkında daha fazla yönerge için bkz: [oluşturma ve sıra bir derleme tanımınız](https://www.visualstudio.com/en-us/docs/build/define/create).</span><span class="sxs-lookup"><span data-stu-id="64954-222">For instructions on how to create a build definition in TFS, see [Create and queue a build definition](https://www.visualstudio.com/en-us/docs/build/define/create).</span></span>

<span data-ttu-id="64954-223">Yeni bir derleme tanımı oluşturun (seçin **boş** şablonu) "InfraDNS" adlı.</span><span class="sxs-lookup"><span data-stu-id="64954-223">Create a new build definition (select the **Empty** template) named "InfraDNS".</span></span>
<span data-ttu-id="64954-224">Aşağıdaki adımlar, yapı tanımı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="64954-224">Add the following steps to you build definition:</span></span>

- <span data-ttu-id="64954-225">PowerShell Script</span><span class="sxs-lookup"><span data-stu-id="64954-225">PowerShell Script</span></span>
- <span data-ttu-id="64954-226">Test sonuçlarını yayımlama</span><span class="sxs-lookup"><span data-stu-id="64954-226">Publish Test Results</span></span>
- <span data-ttu-id="64954-227">Dosyaları kopyalama</span><span class="sxs-lookup"><span data-stu-id="64954-227">Copy Files</span></span>
- <span data-ttu-id="64954-228">Yapı yayımlama</span><span class="sxs-lookup"><span data-stu-id="64954-228">Publish Artifact</span></span>

<span data-ttu-id="64954-229">Bu derleme adımları, her adım özelliklerini şu şekilde düzenleyerek ekledikten sonra:</span><span class="sxs-lookup"><span data-stu-id="64954-229">After adding these build steps, edit the properties of each step as follows:</span></span>

### <a name="powershell-script"></a><span data-ttu-id="64954-230">PowerShell Script</span><span class="sxs-lookup"><span data-stu-id="64954-230">PowerShell Script</span></span>

1. <span data-ttu-id="64954-231">Ayarlama **türü** özelliğine `File Path`.</span><span class="sxs-lookup"><span data-stu-id="64954-231">Set the **Type** property to `File Path`.</span></span>
1. <span data-ttu-id="64954-232">Ayarlama **betik yolu** özelliğine `initiate.ps1`.</span><span class="sxs-lookup"><span data-stu-id="64954-232">Set the **Script Path** property to `initiate.ps1`.</span></span>
1. <span data-ttu-id="64954-233">Ekleme `-fileName build` için **bağımsız değişkenleri** özelliği.</span><span class="sxs-lookup"><span data-stu-id="64954-233">Add `-fileName build` to the **Arguments** property.</span></span>

<span data-ttu-id="64954-234">Bu derleme adımı çalışır `initiate.ps1` psake yapı komut dosyasını çağıran dosya.</span><span class="sxs-lookup"><span data-stu-id="64954-234">This build step runs the `initiate.ps1` file, which calls the psake build script.</span></span>

### <a name="publish-test-results"></a><span data-ttu-id="64954-235">Test sonuçlarını yayımlama</span><span class="sxs-lookup"><span data-stu-id="64954-235">Publish Test Results</span></span>

1. <span data-ttu-id="64954-236">Ayarlama **Test Sonuç biçimi** için `NUnit`</span><span class="sxs-lookup"><span data-stu-id="64954-236">Set **Test Result Format** to `NUnit`</span></span>
1. <span data-ttu-id="64954-237">Ayarlama **Test sonuçları dosyaları** için `InfraDNS/Tests/Results/*.xml`</span><span class="sxs-lookup"><span data-stu-id="64954-237">Set **Test Results Files** to `InfraDNS/Tests/Results/*.xml`</span></span>
1. <span data-ttu-id="64954-238">Ayarlama **çalıştırma başlığı Test** için `Unit`.</span><span class="sxs-lookup"><span data-stu-id="64954-238">Set **Test Run Title** to `Unit`.</span></span>
1. <span data-ttu-id="64954-239">Emin olun **denetim seçeneklerini** **etkin** ve **her zaman Çalıştır** seçilidir hem.</span><span class="sxs-lookup"><span data-stu-id="64954-239">Make sure **Control Options** **Enabled** and **Always run** are both selected.</span></span>

<span data-ttu-id="64954-240">Bu derleme adımı biz arama sırasında daha önce Pester komut dosyasında birim testleri çalıştırır ve sonuçları depolar `InfraDNS/Tests/Results/*.xml` klasör.</span><span class="sxs-lookup"><span data-stu-id="64954-240">This build step runs the unit tests in the Pester script we looked at earlier, and stores the results in the `InfraDNS/Tests/Results/*.xml` folder.</span></span>

### <a name="copy-files"></a><span data-ttu-id="64954-241">Dosyaları kopyalama</span><span class="sxs-lookup"><span data-stu-id="64954-241">Copy Files</span></span>

1. <span data-ttu-id="64954-242">Her aşağıdaki satırları ekleyin **içeriği**:</span><span class="sxs-lookup"><span data-stu-id="64954-242">Add each of the following lines to **Contents**:</span></span>

    ```
    initiate.ps1
    **\deploy.ps1
    **\Acceptance\**
    **\Integration\**
    ```

1. <span data-ttu-id="64954-243">Ayarlama **TargetFolder** için `$(Build.ArtifactStagingDirectory)\`</span><span class="sxs-lookup"><span data-stu-id="64954-243">Set **TargetFolder** to `$(Build.ArtifactStagingDirectory)\`</span></span>

<span data-ttu-id="64954-244">Bu adım yapı kopyalar ve test komutlar hazırlama dizinine kadar sonraki adım yapıları oluşturma gibi yayımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="64954-244">This step copies the build and test scripts to the staging directory so that the can be published as build artifacts by the next step.</span></span>

### <a name="publish-artifact"></a><span data-ttu-id="64954-245">Yapı yayımlama</span><span class="sxs-lookup"><span data-stu-id="64954-245">Publish Artifact</span></span>

1. <span data-ttu-id="64954-246">Ayarlama **yayımlamak için yol** için `$(Build.ArtifactStagingDirectory)\`</span><span class="sxs-lookup"><span data-stu-id="64954-246">Set **Path to Publish** to `$(Build.ArtifactStagingDirectory)\`</span></span>
1. <span data-ttu-id="64954-247">Ayarlama **yapı adı** için `Deploy`</span><span class="sxs-lookup"><span data-stu-id="64954-247">Set **Artifact Name** to `Deploy`</span></span>
1. <span data-ttu-id="64954-248">Ayarlama **yapay nesne türü** için `Server`</span><span class="sxs-lookup"><span data-stu-id="64954-248">Set **Artifact Type** to `Server`</span></span>
1. <span data-ttu-id="64954-249">Seçin `Enabled` içinde **seçeneklerini denetle**</span><span class="sxs-lookup"><span data-stu-id="64954-249">Select `Enabled` in **Control Options**</span></span>

## <a name="enable-continuous-integration"></a><span data-ttu-id="64954-250">Sürekli Tümleştirme etkinleştir</span><span class="sxs-lookup"><span data-stu-id="64954-250">Enable continuous integration</span></span>

<span data-ttu-id="64954-251">İstediğiniz zaman oluşturmak proje neden olan bir tetikleyici yaparız artık bir değişiklik için iade `ci-cd-example` git deponun dalı.</span><span class="sxs-lookup"><span data-stu-id="64954-251">Now we'll set up a trigger that causes the project to build any time a change is checked in to the `ci-cd-example` branch of the git repository.</span></span>

1. <span data-ttu-id="64954-252">TFS'de, tıklatın **yapı & yayın** sekmesi</span><span class="sxs-lookup"><span data-stu-id="64954-252">In TFS, click the **Build & Release** tab</span></span>
1. <span data-ttu-id="64954-253">Seçin `DNS Infra` yapı tanımı öğesini tıklatıp **Düzenle**</span><span class="sxs-lookup"><span data-stu-id="64954-253">Select the `DNS Infra` build definition, and click **Edit**</span></span>
1. <span data-ttu-id="64954-254">Tıklatın **Tetikleyicileri** sekmesi</span><span class="sxs-lookup"><span data-stu-id="64954-254">Click the **Triggers** tab</span></span>
1. <span data-ttu-id="64954-255">Seçin **sürekli tümleştirme (CI)**seçip `refs/heads/ci-cd-example` şube aşağı açılan listesinde</span><span class="sxs-lookup"><span data-stu-id="64954-255">Select **Continuous integration (CI)**, and select `refs/heads/ci-cd-example` in the branch drop-down list</span></span>
1. <span data-ttu-id="64954-256">Tıklatın **kaydetmek** ve ardından **Tamam**</span><span class="sxs-lookup"><span data-stu-id="64954-256">Click **Save** and then **OK**</span></span>

<span data-ttu-id="64954-257">Artık TFS git deposu Tetikleyicileri otomatik derleme değiştirin.</span><span class="sxs-lookup"><span data-stu-id="64954-257">Now any change in the TFS git repository triggers an automated build.</span></span>

## <a name="create-the-release-definition"></a><span data-ttu-id="64954-258">Yayın tanımı oluşturun</span><span class="sxs-lookup"><span data-stu-id="64954-258">Create the release definition</span></span>

<span data-ttu-id="64954-259">Böylece proje her kod iade geliştirme ortamı dağıtılmış bir sürüm tanımı oluşturalım.</span><span class="sxs-lookup"><span data-stu-id="64954-259">Let's create a release definition so that the project is deployed to the development environment with every code check-in.</span></span>

<span data-ttu-id="64954-260">Bunu yapmak için ilişkili yeni bir sürüm tanımı eklemek `InfraDNS` yapı daha önce oluşturduğunuz tanımı.</span><span class="sxs-lookup"><span data-stu-id="64954-260">To do this, add a new release definition associated with the `InfraDNS` build definition you created previously.</span></span>
<span data-ttu-id="64954-261">Seçtiğinizden emin olun **sürekli dağıtım** böylece yeni bir yapı tamamlandığında dilediğiniz zaman yeni bir sürüm tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="64954-261">Be sure to select **Continuous deployment** so that a new release will be triggered any time a new build is completed.</span></span>
<span data-ttu-id="64954-262">([Nasıl yapılır: çalışma yayın tanımlarla](https://www.visualstudio.com/en-us/docs/build/actions/work-with-release-definitions)) ve aşağıdaki gibi yapılandırın:</span><span class="sxs-lookup"><span data-stu-id="64954-262">([How to: Work with release definitions](https://www.visualstudio.com/en-us/docs/build/actions/work-with-release-definitions)) and configure it as follows:</span></span>

<span data-ttu-id="64954-263">Aşağıdaki adımları yayın tanımına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="64954-263">Add the following steps to the release definition:</span></span>

- <span data-ttu-id="64954-264">PowerShell Script</span><span class="sxs-lookup"><span data-stu-id="64954-264">PowerShell Script</span></span>
- <span data-ttu-id="64954-265">Test sonuçlarını yayımlama</span><span class="sxs-lookup"><span data-stu-id="64954-265">Publish Test Results</span></span>
- <span data-ttu-id="64954-266">Test sonuçlarını yayımlama</span><span class="sxs-lookup"><span data-stu-id="64954-266">Publish Test Results</span></span>

<span data-ttu-id="64954-267">Adımları aşağıdaki gibi düzenleyin:</span><span class="sxs-lookup"><span data-stu-id="64954-267">Edit the steps as follows:</span></span>

### <a name="powershell-script"></a><span data-ttu-id="64954-268">PowerShell Script</span><span class="sxs-lookup"><span data-stu-id="64954-268">PowerShell Script</span></span>

1. <span data-ttu-id="64954-269">Ayarlama **betik yolu** alanı `$(Build.DefinitionName)\Deploy\initiate.ps1"`</span><span class="sxs-lookup"><span data-stu-id="64954-269">Set the **Script Path** field to `$(Build.DefinitionName)\Deploy\initiate.ps1"`</span></span>
1. <span data-ttu-id="64954-270">Ayarlama **bağımsız değişkenleri** alanı `-fileName Deploy`</span><span class="sxs-lookup"><span data-stu-id="64954-270">Set the **Arguments** field to `-fileName Deploy`</span></span>

### <a name="first-publish-test-results"></a><span data-ttu-id="64954-271">İlk Test sonuçlarını yayımlama</span><span class="sxs-lookup"><span data-stu-id="64954-271">First Publish Test Results</span></span>

1. <span data-ttu-id="64954-272">Seçin `NUnit` için **Test Sonuç biçimi** alan</span><span class="sxs-lookup"><span data-stu-id="64954-272">Select `NUnit` for the **Test Result Format** field</span></span>
1. <span data-ttu-id="64954-273">Ayarlama **Test sonuç dosyalarını** alanı `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Integration*.xml`</span><span class="sxs-lookup"><span data-stu-id="64954-273">Set the **Test Result Files** field to `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Integration*.xml`</span></span>
1. <span data-ttu-id="64954-274">Ayarlama **çalıştırma başlığı Test** için `Integration`</span><span class="sxs-lookup"><span data-stu-id="64954-274">Set the **Test Run Title** to `Integration`</span></span>
1. <span data-ttu-id="64954-275">Altında **denetim seçeneklerini**, denetleme **her zaman çalıştır**</span><span class="sxs-lookup"><span data-stu-id="64954-275">Under **Control Options**, check **Always run**</span></span>

### <a name="second-publish-test-results"></a><span data-ttu-id="64954-276">İkinci Test sonuçlarını yayımlama</span><span class="sxs-lookup"><span data-stu-id="64954-276">Second Publish Test Results</span></span>

1. <span data-ttu-id="64954-277">Seçin `NUnit` için **Test Sonuç biçimi** alan</span><span class="sxs-lookup"><span data-stu-id="64954-277">Select `NUnit` for the **Test Result Format** field</span></span>
1. <span data-ttu-id="64954-278">Ayarlama **Test sonuç dosyalarını** alanı `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Acceptance*.xml`</span><span class="sxs-lookup"><span data-stu-id="64954-278">Set the **Test Result Files** field to `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Acceptance*.xml`</span></span>
1. <span data-ttu-id="64954-279">Ayarlama **çalıştırma başlığı Test** için `Acceptance`</span><span class="sxs-lookup"><span data-stu-id="64954-279">Set the **Test Run Title** to `Acceptance`</span></span>
1. <span data-ttu-id="64954-280">Altında **denetim seçeneklerini**, denetleme **her zaman çalıştır**</span><span class="sxs-lookup"><span data-stu-id="64954-280">Under **Control Options**, check **Always run**</span></span>

## <a name="verify-your-results"></a><span data-ttu-id="64954-281">Sonuçlarınızı doğrulayın</span><span class="sxs-lookup"><span data-stu-id="64954-281">Verify your results</span></span>

<span data-ttu-id="64954-282">Şimdi, dilediğiniz zaman, anında değişiklikleri `ci-cd-example` TFS, yeni bir yapı dala başlayacak.</span><span class="sxs-lookup"><span data-stu-id="64954-282">Now, any time you push changes in the `ci-cd-example` branch to TFS, a new build will start.</span></span>
<span data-ttu-id="64954-283">Yapılandırma başarıyla tamamlanırsa, yeni bir dağıtım tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="64954-283">If the build completes successfully, a new deployment is triggered.</span></span>

<span data-ttu-id="64954-284">İstemci makinesinde bir tarayıcı açıp giderek dağıtımının sonucu denetleyebilirsiniz `www.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="64954-284">You can check the result of the deployment by opening a browser on the client machine and navigating to `www.contoso.com`.</span></span>

## <a name="next-steps"></a><span data-ttu-id="64954-285">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="64954-285">Next steps</span></span>

<span data-ttu-id="64954-286">Bu örnek DNS sunucusu yapılandırır `TestAgent1` böylece URL `www.contoso.com` çözümler `TestAgent2`, ancak bir Web sitesi gerçekte dağıtmaz.</span><span class="sxs-lookup"><span data-stu-id="64954-286">This example configures the DNS server `TestAgent1` so that the URL `www.contoso.com` resolves to `TestAgent2`, but it does not actually deploy a website.</span></span>
<span data-ttu-id="64954-287">Bunu yapmak için çatıyı depodaki altında sağlanan `WebApp` klasör.</span><span class="sxs-lookup"><span data-stu-id="64954-287">The skeleton for doing so is provided in the repo under the `WebApp` folder.</span></span>
<span data-ttu-id="64954-288">Psake komut dosyaları, Pester testleri ve DSC yapılandırmaları oluşturmak için sağlanan saplamalar kendi Web sitenizi dağıtmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="64954-288">You can use the stubs provided to create psake scripts, Pester tests, and DSC configurations to deploy your own website.</span></span>