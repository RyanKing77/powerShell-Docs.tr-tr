---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC ile sürekli tümleştirme ve sürekli dağıtım işlem hattı oluşturma
ms.openlocfilehash: 2d049cd640f0df9b018a88ad106e59dbeed7bcee
ms.sourcegitcommit: f60fa420bdc81db174e6168d3aeb11371e483162
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/20/2019
ms.locfileid: "67301505"
---
# <a name="building-a-continuous-integration-and-continuous-deployment-pipeline-with-dsc"></a>DSC ile sürekli tümleştirme ve sürekli dağıtım işlem hattı oluşturma

Bu örnek, PowerShell, DSC, Pester ve Visual Studio Team Foundation Server (TFS) kullanarak sürekli tümleştirme/sürekli dağıtım (CI/CD) işlem hattı oluşturma gösterilmektedir.

İşlem hattı oluşturulan ve yapılandırıldıktan sonra tam olarak dağıtma, yapılandırma ve test bir DNS sunucusu kullanabilir ve ana bilgisayar kayıtları ilişkili.
Bu işlem, bir geliştirme ortamında kullanılan bir işlem hattı ilk bölümünü benzetimini yapar.

Otomatik bir CI/CD işlem hattı yazılımları daha hızlı bir şekilde güncelleştirmenize yardımcı olur ve daha güvenilir bir şekilde tüm kod test edilmesini ve kodunuzun geçerli bir derleme olduğundan emin olduktan kullanılabilir her zaman.

## <a name="prerequisites"></a>Önkoşullar

Bu örneği kullanmak için aşağıdaki bilgi sahibi olmanız:

- CI-CD kavramları. İyi bir referans şu yolda bulunabilir: [yayın işlem hattı modelini](https://aka.ms/thereleasepipelinemodelpdf).
- [Git](https://git-scm.com/) kaynak denetimi
- [Pester](https://github.com/pester/Pester) testi çerçevesi
- [Team Foundation Server](https://visualstudio.microsoft.com/tfs/)

## <a name="what-you-will-need"></a>İhtiyacınız

Derleme ve bu örneği çalıştırmak için çeşitli bilgisayarlar ve/veya sanal makine ile bir ortam gerekir.

### <a name="client"></a>İstemci

Bu, burada tüm ayarlama ve örnek çalıştırma işlemleri gerçekleştirirsiniz bilgisayardır.

İstemci bilgisayarın bir Windows bilgisayarda aşağıdakilerin yüklü olması gerekir:

- [Git](https://git-scm.com/)
- öğesinden kopyalanan bir yerel git deposu https://github.com/PowerShell/Demo_CI
- bir metin düzenleyicisi gibi [Visual Studio Code](https://code.visualstudio.com/)

### <a name="tfssrv1"></a>TFSSrv1

Tanımladığınız derleme TFS sunucusunu barındıran bilgisayarın ve serbest bırakın.
Bu bilgisayarda yüklü olmalıdır [Team Foundation Server 2017](https://visualstudio.microsoft.com/tfs/) yüklü.

### <a name="buildagent"></a>BuildAgent

Windows çalıştıran bilgisayar, projeyi derler Aracısı oluşturun.
Bu bilgisayarda bir Windows derleme aracısı sürümünün yüklü ve çalışıyor olması gerekir.
Bkz: [Windows üzerinde aracı dağıtma](/azure/devops/pipelines/agents/v2-windows) yapı aracısını yüklemek ve bir Windows çalıştırmak yönergeler için.

Ayrıca her ikisini de yüklemeniz gerekir `xDnsServer` ve `xNetworking` DSC modülleri bu bilgisayarda.

### <a name="testagent1"></a>TestAgent1

Bu örnekte DSC yapılandırması tarafından bir DNS sunucusu olarak yapılandırılmış bilgisayardır.
Bilgisayarda çalışmalıdır [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).

### <a name="testagent2"></a>TestAgent2

Bu örnekte yapılandırır Web sitesini barındıran bilgisayarın budur.
Bilgisayarda çalışmalıdır [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).

## <a name="add-the-code-to-tfs"></a>TFS için kod ekleyin

TFS'de bir Git deposu oluşturuluyor ve istemci bilgisayardaki yerel deponuzdan kod aktararak başlayacağız.
Şimdi, zaten Demo_CI depo istemci bilgisayarınıza değil kopyaladıysanız, aşağıdaki git komutunu çalıştırarak yapın:

`git clone https://github.com/PowerShell/Demo_CI`

1. İstemci bilgisayarınızda, TFS sunucunuz bir web tarayıcısında gidin.
1. TFS içinde [yeni takım projesi oluşturma](/azure/devops/organizations/projects/create-project) Demo_CI adlı.

   Emin olun **sürüm denetimi** ayarlanır **Git**.
1. İstemci bilgisayarınızda, bir uzak TFS'de aşağıdaki komutla yeni oluşturduğunuz depoya ekleyin:

   `git remote add tfs <YourTFSRepoURL>`

   Burada `<YourTFSRepoURL>` önceki adımda oluşturduğunuz TFS depo kopya URL'si.

   Bu URL'yi bulmak nereye bilmiyorsanız, bkz. [var olan bir Git deposu kopyalama](/azure/devops/repos/git/clone).
1. Kodu yerel deponuzdan aşağıdaki komutla TFS deponuzu şuraya gönder:

   `git push tfs --all`
1. TFS depo Demo_CI kodu ile doldurulur.

> [!NOTE]
> Bu örnekte kodda `ci-cd-example` Git deponun dalı.
> TFS projenizin içinde varsayılan dal olarak bu dalı belirttiğinizden emin olun ve CI/CD Tetikleyicileri oluşturursunuz.

## <a name="understanding-the-code"></a>Kod anlama

Şu derleme ve dağıtım işlem hattı oluşturmadan önce bazı kodları neler olup bittiğini anlamak için göz atalım.
İstemci bilgisayarınızda, sık kullandığınız metin düzenleyicisinde açın ve Demo_CI Git deponuzun kök dizinine gidin.

### <a name="the-dsc-configuration"></a>DSC yapılandırması

Dosyayı açmak `DNSServer.ps1` (yerel Demo_CI depo kökünden `./InfraDNS/Configs/DNSServer.ps1`).

Bu dosya, DNS sunucusunu ayarlar DSC yapılandırması içerir. Bu tamamen şöyledir:

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

Bildirim `Node` deyimi:

```powershell
Node $AllNodes.Where{$_.Role -eq 'DNSServer'}.NodeName
```

Bu rolü sahip olarak tanımlanmış olan tüm düğümleri bulur `DNSServer` içinde [yapılandırma verilerini](../configurations/configData.md), tarafından oluşturulan `DevEnv.ps1` betiği.

Daha fazla bilgi edinebilirsiniz `Where` yönteminde [about_arrays](/powershell/module/microsoft.powershell.core/about/about_arrays)

Düğüm tanımlamak için yapılandırma verilerini kullanarak CI düğüm bilgileri büyük olasılıkla ortamlar arasında değişir ve yapılandırma verilerini kullanarak yapılandırma kodunu değiştirmeden değişiklikleri düğüm bilgileri kolayca yapmanıza olanak verir çünkü yaparken önemlidir.

İlk kaynak blok yapılandırma çağırır **WindowsFeature** DNS özelliği etkinleştirildiğinden emin olmak için.
Çağrı kaynaklardan izleyin kaynak bloklar [xDnsServer](https://github.com/PowerShell/xDnsServer) modülü birincil bölge ve DNS kayıtlarını yapılandırın.

Dikkat iki `xDnsRecord` blokları içinde kaydırılır `foreach` yapılandırma verilerinde diziler üzerinden yineleme döngüleri.
Yapılandırma verilerini tarafından yeniden oluşturulur `DevEnv.ps1` betiğini sonraki göz atacağız.

### <a name="configuration-data"></a>Yapılandırma verileri

`DevEnv.ps1` Dosyası (yerel Demo_CI depo kökünden `./InfraDNS/DevEnv.ps1`) ortama özgü yapılandırma verilerini bir hashtable içinde belirtir ve ardından bir çağrı o hashtable geçirir `New-DscConfigurationDataDocument` içindetanımlananişlevi`DscPipelineTools.psm` (`./Assets/DscPipelineTools/DscPipelineTools.psm1`).

`DevEnv.ps1` Dosyası:

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

`New-DscConfigurationDataDocument` İşlevi (tanımlanan `\Assets\DscPipelineTools\DscPipelineTools.psm1`) programlı olarak hashtable (düğüm veri) ve dizi (düğümü olmayan veriler) olarak geçirilen bir yapılandırma verileri belgesi oluşturur `RawEnvData` ve `OtherEnvData` parametreleri.

Bizim durumumuzda, yalnızca `RawEnvData` parametresi kullanılır.

### <a name="the-psake-build-script"></a>Psake derleme betiği

[Psake](https://github.com/psake/psake) betik içinde tanımlanan derleme `Build.ps1` (Demo_CI depo kökünden `./InfraDNS/Build.ps1`) yapının bir parçası olan görevleri tanımlar.
Ayrıca, her görevin bağlı diğer görevleri tanımlar.
Psake komut çağrıldığında, belirtilen görev sağlar (veya adlı görev `Default` belirtilmezse) çalıştırır ve tüm bağımlılıklar da çalıştırın (bağımlılıkları bağımlılıklarını çalıştırın böylece özyinelemeli budur ve benzeri).

Bu örnekte, `Default` görev olarak tanımlanır:

```powershell
Task Default -depends UnitTests
```

`Default` Görevi hiçbir uygulamaya sahip, ancak bir bağımlılığa sahip `CompileConfigs` görev.
Görev bağımlılıkları sonuç zincirini derleme betiğindeki tüm görevler çalıştırmasını sağlar.

Bu örnekte, bir çağrı tarafından psake betik çağrılır `Invoke-PSake` içinde `Initiate.ps1` (Demo_CI deponun kökünde bulunur) dosyası:

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

Derleme tanımı için TFS örneğimizde oluşturduğumuzda, bizim psake komut dosyası olarak sağlamanız `fileName` bu komut için parametre.

Derleme betiği aşağıdaki görevleri tanımlar:

#### <a name="generateenvironmentfiles"></a>GenerateEnvironmentFiles

Çalıştırmaları `DevEnv.ps1`, yapılandırma verileri dosyası oluşturur.

#### <a name="installmodules"></a>InstallModules

Yapılandırma tarafından gerekli modülleri yükler `DNSServer.ps1`.

#### <a name="scriptanalysis"></a>ScriptAnalysis

Çağrıları [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer).

#### <a name="unittests"></a>UnitTests

Çalıştırmaları [Pester](https://github.com/pester/Pester/wiki) birim testleri.

#### <a name="compileconfigs"></a>CompileConfigs

Yapılandırma derleme (`DNSServer.ps1`) tarafından oluşturulan yapılandırma verilerini bir MOF dosyasına kullanarak `GenerateEnvironmentFiles` görev.

#### <a name="clean"></a>Clean

Örnek için kullanılan klasörleri oluşturur ve herhangi bir test sonuçları, yapılandırma verileri dosyalarınızı ve modülleri önceki çalıştırmalardan kaldırır.

### <a name="the-psake-deploy-script"></a>Betik psake dağıtma

[Psake](https://github.com/psake/psake) tanımlı dağıtım betiği `Deploy.ps1` (Demo_CI depo kökünden `./InfraDNS/Deploy.ps1`) dağıtma ve çalıştırma yapılandırma görevlerini tanımlar.

`Deploy.ps1` Aşağıdaki görevleri tanımlar:

#### <a name="deploymodules"></a>DeployModules

Üzerinde bir PowerShell oturumu başlatır `TestAgent1` ve yapılandırması için gereken DSC kaynakları içeren modülleri yükler.

#### <a name="deployconfigs"></a>DeployConfigs

Çağrıları [Başlat-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) yapılandırma çalıştırılacak cmdlet'i `TestAgent1`.

#### <a name="integrationtests"></a>IntegrationTests

Çalıştırmaları [Pester](https://github.com/pester/Pester/wiki) tümleştirme testleri.

#### <a name="acceptancetests"></a>AcceptanceTests

Çalıştırmaları [Pester](https://github.com/pester/Pester/wiki) kabul testleri.

#### <a name="clean"></a>Clean

Önceki çalıştırmaları yüklü modüllerin kaldırır ve test sonucu klasör var olmasını sağlar.

### <a name="test-scripts"></a>Test betikleri

Kabul, tümleştirme ve birim testleri betiklerde tanımlanmış `Tests` klasörü (Demo_CI depo kökünden `./InfraDNS/Tests`), her adlı dosyaları `DNSServer.tests.ps1` kendi klasörlerine içinde.

Test betikleri kullanım [Pester](https://github.com/pester/Pester/wiki) ve [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) söz dizimi.

#### <a name="unit-tests"></a>Birim testleri

Birim test DSC yapılandırmaları kendilerini yapılandırmaları çalıştırdıklarında beklenen yapacağı emin olmak için test eder.
Komut dosyası kullanan birim testi [Pester](https://github.com/pester/Pester/wiki).

#### <a name="integration-tests"></a>Tümleştirme testleri

Tümleştirme testleri test yapılandırması sistemindeki diğer bileşenleri ile tümleştirildiğinde, sistem beklendiği şekilde yapılandırıldığından emin olun. DSC ile yapılandırıldıktan sonra bu testleri hedef düğümde çalıştırın.
Tümleştirme test betiği bir karışımını kullanır [Pester](https://github.com/pester/Pester/wiki) ve [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) söz dizimi.

#### <a name="acceptance-tests"></a>Kabul testleri

Kabul testleri beklendiği gibi davrandığından emin olmak için sistemi test edin.
Örneğin, bir web sayfası doğru bilgileri sorgulandığında döndürür emin olmak için test eder.
Bu testleri uzaktan gerçek dünya senaryolarını test etmek için hedef düğümü çalıştırın.
Tümleştirme test betiği bir karışımını kullanır [Pester](https://github.com/pester/Pester/wiki) ve [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) söz dizimi.

## <a name="define-the-build"></a>Yapı tanımlama

TFS için Kodumuzun yükledikten ve ne işe yaradığını adresindeki, aranan derleme araçlarımızı tanımlayalım göre.

Burada, biz yalnızca yapı ekleyeceksiniz derleme adımları ele alacağız. TFS'de bir yapı tanımı oluşturma hakkında yönergeler için bkz: [oluşturma ve derleme tanımını sıraya](/azure/devops/pipelines/create-first-pipeline).

Yeni bir derleme tanımı oluştur (seçin **boş** şablonu) "InfraDNS" adlı.
Aşağıdaki adımlar, yapı tanımı ekleyin:

- PowerShell Betiği
- Test sonuçlarını yayımlama
- Dosyaları Kopyala
- Yapıt yayımlama

Bu derleme adımları, her bir adımın özelliklerini şu şekilde düzenlemek ekledikten sonra:

### <a name="powershell-script"></a>PowerShell Betiği

1. Ayarlama **türü** özelliğini `File Path`.
1. Ayarlama **betik yolu** özelliğini `initiate.ps1`.
1. Ekleme `-fileName build` için **bağımsız değişkenleri** özelliği.

Bu derleme adımı `initiate.ps1` dosyasını psake derleme betiğini çağırır.

### <a name="publish-test-results"></a>Test sonuçlarını yayımlama

1. Ayarlama **Test sonucu biçimi** için `NUnit`
1. Ayarlama **Test sonuçları dosyaları** için `InfraDNS/Tests/Results/*.xml`
1. Ayarlama **Test çalıştırması başlığı** için `Unit`.
1. Emin **denetimi seçenekleri** **etkin** ve **her zaman Çalıştır** seçili olan iki.

Bu derleme adımı incelemiştik, daha önce Pester betikte birim testlerini çalıştırır ve sonuçları depolar `InfraDNS/Tests/Results/*.xml` klasör.

### <a name="copy-files"></a>Dosyaları Kopyala

1. Her biri aşağıdaki satırları ekleyin **içeriği**:

   ```
   initiate.ps1
   **\deploy.ps1
   **\Acceptance\**
   **\Integration\**
   ```

1. Ayarlama **TargetFolder** için `$(Build.ArtifactStagingDirectory)\`

Bu adımı yapı kopyalar ve test betikleri hazırlama dizine kadar sonraki adım, derleme yapıları olarak yayımlanabilir.

### <a name="publish-artifact"></a>Yapıt yayımlama

1. Ayarlama **yayımlama yolu** için `$(Build.ArtifactStagingDirectory)\`
1. Ayarlama **Yapıt adı** için `Deploy`
1. Ayarlama **Yapıt türü** için `Server`
1. Seçin `Enabled` içinde **Denetim seçenekleri**

## <a name="enable-continuous-integration"></a>sürekli tümleştirmeyi etkinleştir

Biz, dilediğiniz zaman oluşturmak proje neden olan bir tetikleyici ayarlarsınız artık bir değişiklik için iade `ci-cd-example` git deponun dalı.

1. TFS'de tıklayın **derleme ve yayınlama** sekmesi
1. Seçin `DNS Infra` derleme tanımı ve tıklayın **Düzenle**
1. Tıklayın **Tetikleyicileri** sekmesi
1. Seçin **sürekli tümleştirme (CI)** seçip `refs/heads/ci-cd-example` dal aşağı açılan listesinde
1. Tıklayın **Kaydet** ardından **Tamam**

Artık TFS git deposu Tetikleyicileri otomatik bir yapı değiştirin.

## <a name="create-the-release-definition"></a>Yayın tanımı oluşturma

Böylece proje her kodu iade ile geliştirme ortamına dağıtılan bir yayın tanımı oluşturalım.

Bunu yapmak için ile ilişkili yeni bir yayın tanımı Ekle `InfraDNS` daha önce oluşturduğunuz tanımı oluşturun.
Seçtiğinizden emin olun **sürekli dağıtım** böylece dilediğiniz zaman yeni bir derleme tamamlandığında yeni bir yayın tetiklenir.
([Yayın işlem hatları nelerdir? ](/azure/devops/pipelines/release/)) ve şu şekilde yapılandırın:

Aşağıdaki adımlar, yayın tanımına ekleyin:

- PowerShell Betiği
- Test sonuçlarını yayımlama
- Test sonuçlarını yayımlama

Adımları aşağıdaki gibi düzenleyin:

### <a name="powershell-script"></a>PowerShell Betiği

1. Ayarlama **betik yolu** alanı `$(Build.DefinitionName)\Deploy\initiate.ps1"`
1. Ayarlama **bağımsız değişkenleri** alanı `-fileName Deploy`

### <a name="first-publish-test-results"></a>İlk Test sonuçlarını yayımlama

1. Seçin `NUnit` için **Test sonucu biçimi** alan
1. Ayarlama **Test Sonuç dosyaları** alanı `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Integration*.xml`
1. Ayarlama **Test çalıştırması başlığı** için `Integration`
1. Altında **denetimi seçenekleri**, kontrol **her zaman çalıştır**

### <a name="second-publish-test-results"></a>İkinci Test sonuçlarını yayımlama

1. Seçin `NUnit` için **Test sonucu biçimi** alan
1. Ayarlama **Test Sonuç dosyaları** alanı `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Acceptance*.xml`
1. Ayarlama **Test çalıştırması başlığı** için `Acceptance`
1. Altında **denetimi seçenekleri**, kontrol **her zaman çalıştır**

## <a name="verify-your-results"></a>Sonuçları denetleyin

Şimdi, istediğiniz zaman, değişiklikleri gönderir `ci-cd-example` dal TFS'de yeni bir derleme başlar.
Derleme işlemi başarıyla tamamlarsa, yeni bir dağıtım tetiklenir.

İstemci makinesinde bir tarayıcı açıp giderek dağıtımının sonucu denetleyebilirsiniz `www.contoso.com`.

## <a name="next-steps"></a>Sonraki adımlar

Bu örnek DNS sunucusunu yapılandırır `TestAgent1` böylece URL `www.contoso.com` çözümler `TestAgent2`, ancak bir Web sitesi gerçekten dağıtmaz.
Bunu yapmak için çatıyı altında deposunda sağlanan `WebApp` klasör.
Kendi Web sitesini dağıtmak için psake betikleri, Pester testler ve DSC yapılandırmaları oluşturmak için sağlanan saptamalar kullanabilirsiniz.
