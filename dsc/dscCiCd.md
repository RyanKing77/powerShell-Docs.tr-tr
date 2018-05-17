---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: DSC sahip sürekli tümleştirme ve sürekli dağıtımı işlem hattı oluşturma
ms.openlocfilehash: ce0f2ed79f5f96a1c38e0beaf32529aba7538963
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
---
# <a name="building-a-continuous-integration-and-continuous-deployment-pipeline-with-dsc"></a>DSC sahip sürekli tümleştirme ve sürekli dağıtımı işlem hattı oluşturma

Bu örnek bir sürekli tümleştirme/sürekli dağıtımı (CI/CD) ardışık PowerShell, DSC, Pester ve Visual Studio Team Foundation Server (TFS) kullanarak nasıl oluşturulacağını gösterir.

Ardışık Düzen yerleşik yapılandırıldıktan sonra tam olarak dağıtmak, yapılandırmak ve bir DNS sunucusu sınamak için kullanabilir ve ana bilgisayar kayıtları ilişkili.
Bu işlem bir geliştirme ortamında kullanılacak bir ardışık düzen ilk bölümü benzetimini yapar.

Daha güvenilir bir şekilde tüm kod sınanır ve kodunuzun geçerli bir yapı olduğundan emin olduktan kullanılabilir her zaman ve otomatik bir CI/CD ardışık yazılım daha hızlı güncelleştirmenize yardımcı olur.

## <a name="prerequisites"></a>Önkoşullar

Bu örneği kullanmak için aşağıdaki bilgi sahibi olmanız:

- CI CD kavramlar. İyi bir başvuru bulunabilir [yayın ardışık düzen modeli](http://aka.ms/thereleasepipelinemodelpdf).
- [Git](https://git-scm.com/) kaynak denetimi
- [Pester](https://github.com/pester/Pester) framework test etme
- [Team Foundation Server](https://www.visualstudio.com/tfs/)

## <a name="what-you-will-need"></a>İhtiyacınız olacak

Derleme ve bu örneği çalıştırmak için çeşitli bilgisayarlar ve/veya sanal makineleri olan bir ortamda gerekir.

### <a name="client"></a>İstemci

Bu, tüm ayarlama ve örnek çalışan iş yeri gerçekleştirirsiniz bilgisayardır.

İstemci bilgisayar bir Windows bilgisayara aşağıdakilerin yüklü olması gerekir:
- [Git](https://git-scm.com/)
- öğesinden kopyalanan bir yerel git deposu https://github.com/PowerShell/Demo_CI
- bir metin düzenleyicisi gibi [Visual Studio Code](https://code.visualstudio.com/)

### <a name="tfssrv1"></a>TFSSrv1

Tanımladığınız yapınızın TFS sunucusu barındıran bilgisayarda ve bırakın.
Bu bilgisayarda [Team Foundation Server 2017](https://www.visualstudio.com/tfs/) yüklü.

### <a name="buildagent"></a>BuildAgent

Windows çalıştıran bilgisayar proje derlemeler Aracısı oluşturun.
Bu bilgisayarda yüklü ve çalışan aracısını Windows olmalıdır.
Bkz: [Windows'da bir aracı dağıtmak](https://www.visualstudio.com/en-us/docs/build/actions/agents/v2-windows) yapı aracısını yüklemek ve bir Windows çalıştırmak yönergeler için.

Her ikisi de yüklemeniz gerekir `xDnsServer` ve `xNetworking` bu bilgisayarda DSC modüller.

### <a name="testagent1"></a>TestAgent1

Bu örnekte DSC yapılandırması tarafından bir DNS sunucusu olarak yapılandırılan bilgisayardır.
Bilgisayar çalıştırmalıdır [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).

### <a name="testagent2"></a>TestAgent2

Bu örnek yapılandırır Web sitesini barındıran bilgisayar budur.
Bilgisayar çalıştırmalıdır [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).

## <a name="add-the-code-to-tfs"></a>TFS için kod ekleme

Bir Git deposu TFS'de oluşturarak ve istemci bilgisayardaki yerel deponuza kodunu alma başlayacağız.
Zaten Demo_CI depo istemci bilgisayarınıza kopyaladığınız değil, artık aşağıdaki git komutu çalıştırarak yapın:

`git clone https://github.com/PowerShell/Demo_CI`

1. İstemci bilgisayarınızda, TFS sunucunuz bir web tarayıcısında gidin.
1. TFS, [yeni takım projesi oluşturma](https://www.visualstudio.com/en-us/docs/setup-admin/create-team-project) Demo_CI adlı.

    Olduğundan emin olun **sürüm denetimi** ayarlanır **Git**.
1. İstemci bilgisayarınızda, bir uzak aşağıdaki komutla TFS'de yeni oluşturduğunuz deponuza ekleyin:

    `git remote add tfs <YourTFSRepoURL>`

    Burada `<YourTFSRepoURL>` önceki adımda oluşturduğunuz TFS deponuza kopya URL.

    Bu URL nerede bulacağını bilmiyorsanız, bkz: [var olan bir Git deposuna kopyalama](https://www.visualstudio.com/en-us/docs/git/tutorial/clone).
1. Kod yerel depodan aşağıdaki komutla TFS deponuza iletin:

    `git push tfs --all`
1. TFS depo Demo_CI kodu ile doldurulur.

>**Not:** Bu örnek kodda kullanır `ci-cd-example` Git deposuna dalı.
>TFS projenizin ve oluşturduğunuz CI/CD Tetikleyiciler için varsayılan dalı olarak bu dal belirttiğinizden emin olun.

## <a name="understanding-the-code"></a>Kodu anlama

Derleme ve dağıtım ardışık düzen oluşturuyoruz önce neler olup bittiğini anlamak için kodu bazıları bakalım.
İstemci bilgisayarınızda, sık kullandığınız metin düzenleyiciyi açın ve Demo_CI Git deponuzu kök dizinine gidin.

### <a name="the-dsc-configuration"></a>DSC yapılandırması

Dosyayı açmak `DNSServer.ps1` (yerel Demo_CI depo kök `./InfraDNS/Configs/DNSServer.ps1`).

Bu dosya, DNS sunucusunu ayarlar DSC yapılandırması içerir. Aşağıda tamamının verilmiştir:

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

Bu rolü sahip olarak tanımlanmış olan tüm düğümleri bulur `DNSServer` içinde [yapılandırma verilerini](configData.md), tarafından oluşturulan `DevEnv.ps1` komut dosyası.

Düğümleri tanımlamak için yapılandırma verilerini kullanarak CI çünkü düğüm bilgi büyük olasılıkla ortamlar arasında değişir ve yapılandırma verilerini kullanarak kolayca düğümü bilgileri yapılandırma kodunu değiştirmeden değişiklik sağlar yapmak önemlidir.

İlk kaynak bloğunda yapılandırma çağırır [WindowsFeature](windowsFeatureResource.md) DNS özelliği etkinleştirildiğinden emin olmak için.
Çağrı kaynaklardan izleyin kaynak blokları [xDnsServer](https://github.com/PowerShell/xDnsServer) modülünü birincil bölge ve DNS kayıtlarını yapılandırmak için.

Dikkat iki `xDnsRecord` blokları sarılır `foreach` yapılandırma verilerini dizilerde yinelemek döngüler.
Yapılandırma verilerini tarafından yeniden oluşturulan `DevEnv.ps1` biz sonraki göreceğiz komut dosyası.

### <a name="configuration-data"></a>Yapılandırma verileri

`DevEnv.ps1` Dosyası (yerel Demo_CI depo kök `./InfraDNS/DevEnv.ps1`) ortama özgü yapılandırma verilerini bir hashtable belirtir ve ardından bir çağrı bu hashtable geçirir `New-DscConfigurationDataDocument` içindetanımlananişlevi`DscPipelineTools.psm` (`./Assets/DscPipelineTools/DscPipelineTools.psm1`).

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

`New-DscConfigurationDataDocument` İşlevi (tanımlanan `\Assets\DscPipelineTools\DscPipelineTools.psm1`) programlı olarak geçirilen hashtable (düğüm veri) ve dizi (düğüm olmayan veriler) yapılandırma verileri belgesi oluşturur `RawEnvData` ve `OtherEnvData` parametreleri.

Bu örnekte, yalnızca `RawEnvData` parametresi kullanılır.

### <a name="the-psake-build-script"></a>Psake derleme betiğindeki

[Psake](https://github.com/psake/psake) tanımlanan komut dosyası derleme `Build.ps1` (Demo_CI depo kök `./InfraDNS/Build.ps1`) yapının bir parçası olan görevleri tanımlar.
Ayrıca, her görevin bağımlı diğer görevleri tanımlar.
Psake betik çağrıldığında, belirtilen görev sağlar (veya adlı görev `Default` belirtilmemişse) çalıştırır ve tüm bağımlılıkları da çalıştırın (bağımlılıkları bağımlılıklarını çalıştırmak için bu, yinelemelidir ve benzeri).

Bu örnekte, `Default` görev olarak tanımlanır:

```powershell
Task Default -depends UnitTests
```

`Default` Görev hiçbir uygulama, ancak bir bağımlılık içeriyor `CompileConfigs` görev.
Görev bağımlılıkları elde edilen zincirine derleme betiğindeki tüm görevler çalıştırılan sağlar.

Bu örnekte, psake komut dosyası için bir çağrı tarafından çağrılan `Invoke-PSake` içinde `Initiate.ps1` dosyası (Demo_CI depo kök dizininde bulunan):

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

Biz TFS örneğimizde için derleme tanımını oluşturduğunuzda, biz bizim psake komut dosyası olarak sağlayacak `fileName` bu komut için parametre.

Derleme betiğinin aşağıdaki görevleri tanımlar:

#### <a name="generateenvironmentfiles"></a>GenerateEnvironmentFiles

Çalıştırır `DevEnv.ps1`, yapılandırma veri dosyası oluşturur.

#### <a name="installmodules"></a>InstallModules

Yapılandırma tarafından gerekli modüllerini yükler `DNSServer.ps1`.

#### <a name="scriptanalysis"></a>ScriptAnalysis

Çağrıları [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer).

#### <a name="unittests"></a>UnitTests

Çalıştırır [Pester](https://github.com/pester/Pester/wiki) birim testleri.

#### <a name="compileconfigs"></a>CompileConfigs

Yapılandırma derler (`DNSServer.ps1`) tarafından oluşturulan yapılandırma verilerini bir MOF dosyasına kullanarak `GenerateEnvironmentFiles` görev.

#### <a name="clean"></a>Clean

Örnek için kullanılan klasörleri oluşturur ve tüm test sonuçları, yapılandırma veri dosyaları ve modüller önceki dosyadan kaldırır.

### <a name="the-psake-deploy-script"></a>Psake komut dosyası dağıtma

[Psake](https://github.com/psake/psake) tanımlanan dağıtım betiği `Deploy.ps1` (Demo_CI depo kök `./InfraDNS/Deploy.ps1`) dağıtma ve yapılandırma çalıştırma görevleri tanımlar.

`Deploy.ps1` Aşağıdaki görevleri tanımlar:

#### <a name="deploymodules"></a>DeployModules

Üzerinde bir PowerShell oturumu başlatır `TestAgent1` ve yapılandırma için gerekli DSC kaynakları içeren modüller yükler.

#### <a name="deployconfigs"></a>DeployConfigs

Çağrıları [başlangıç DscConfiguration](/reference/5.1/PSDesiredStateConfiguration/Start-DscConfiguration.md) yapılandırma çalıştırmak için cmdlet `TestAgent1`.

#### <a name="integrationtests"></a>IntegrationTests

Çalıştırır [Pester](https://github.com/pester/Pester/wiki) tümleştirme testleri.

#### <a name="acceptancetests"></a>AcceptanceTests

Çalıştırır [Pester](https://github.com/pester/Pester/wiki) kabul testleri.

#### <a name="clean"></a>Clean

Önceki çalıştırmalarında yüklü tüm modüllerin kaldırır ve test sonucu klasörün var olduğunu sağlar.

### <a name="test-scripts"></a>Test komut dosyaları

Kabul, tümleştirme ve birim testlerini komut dosyalarında tanımlanmış `Tests` klasörü (Demo_CI depo kök `./InfraDNS/Tests`), her adlı dosyaları `DNSServer.tests.ps1` ilgili klasörlerine içinde.

Test komut dosyası kullan [Pester](https://github.com/pester/Pester/wiki) ve [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) sözdizimi.

#### <a name="unit-tests"></a>Birim testleri

Birim testi DSC yapılandırmaları kendilerini yapılandırmaları çalıştırdıklarında gerekenin yapacağınız emin olmak için test eder.
Komut dosyası kullanan birim testi [Pester](https://github.com/pester/Pester/wiki).

#### <a name="integration-tests"></a>Tümleştirme testleri

Tümleştirme testleri diğer bileşenlerle tümleştirildiğinde sistem beklendiği şekilde yapılandırıldığından emin olmak için sistem yapılandırmasını sınayın. DSC ile yapılandırıldıktan sonra hedef düğümde bu testleri çalıştırın.
Bir karışımını tümleştirme test betiğini kullanır [Pester](https://github.com/pester/Pester/wiki) ve [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) sözdizimi.

#### <a name="acceptance-tests"></a>Kabul testleri

Kabul testleri sistem beklendiği gibi davranır emin olmak için test edin.
Örneğin, bir web sayfası doğru bilgileri sorgulandığında döndürür emin olmak için sınar.
Bu testler hedef düğümden gerçek dünya senaryoları test etmek amacıyla uzaktan çalıştırın.
Bir karışımını tümleştirme test betiğini kullanır [Pester](https://github.com/pester/Pester/wiki) ve [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) sözdizimi.

## <a name="define-the-build"></a>Yapı tanımlayın

TFS için kodumuza karşıya artık ve bunu yapar Aranan göre şimdi bizim yapı tanımlayın.

Burada, biz yalnızca yapı ekleyeceksiniz oluşturma adımlarının ele alacağız. Yapı tanımı içinde TFS oluşturma hakkında daha fazla yönerge için bkz: [oluşturma ve sıra bir derleme tanımınız](https://www.visualstudio.com/en-us/docs/build/define/create).

Yeni bir derleme tanımı oluşturun (seçin **boş** şablonu) "InfraDNS" adlı.
Aşağıdaki adımlar, yapı tanımı ekleyin:

- PowerShell Betiği
- Test sonuçlarını yayımlama
- Dosyaları kopyalama
- Yapı yayımlama

Bu derleme adımları, her adım özelliklerini şu şekilde düzenleyerek ekledikten sonra:

### <a name="powershell-script"></a>PowerShell Betiği

1. Ayarlama **türü** özelliğine `File Path`.
1. Ayarlama **betik yolu** özelliğine `initiate.ps1`.
1. Ekleme `-fileName build` için **bağımsız değişkenleri** özelliği.

Bu derleme adımı çalışır `initiate.ps1` psake yapı komut dosyasını çağıran dosya.

### <a name="publish-test-results"></a>Test sonuçlarını yayımlama

1. Ayarlama **Test Sonuç biçimi** için `NUnit`
1. Ayarlama **Test sonuçları dosyaları** için `InfraDNS/Tests/Results/*.xml`
1. Ayarlama **çalıştırma başlığı Test** için `Unit`.
1. Emin olun **denetim seçeneklerini** **etkin** ve **her zaman Çalıştır** seçilidir hem.

Bu derleme adımı biz arama sırasında daha önce Pester komut dosyasında birim testleri çalıştırır ve sonuçları depolar `InfraDNS/Tests/Results/*.xml` klasör.

### <a name="copy-files"></a>Dosyaları kopyalama

1. Her aşağıdaki satırları ekleyin **içeriği**:

    ```
    initiate.ps1
    **\deploy.ps1
    **\Acceptance\**
    **\Integration\**
    ```

1. Ayarlama **TargetFolder** için `$(Build.ArtifactStagingDirectory)\`

Bu adım yapı kopyalar ve test komutlar hazırlama dizinine kadar sonraki adım yapıları oluşturma gibi yayımlanabilir.

### <a name="publish-artifact"></a>Yapı yayımlama

1. Ayarlama **yayımlamak için yol** için `$(Build.ArtifactStagingDirectory)\`
1. Ayarlama **yapı adı** için `Deploy`
1. Ayarlama **yapay nesne türü** için `Server`
1. Seçin `Enabled` içinde **seçeneklerini denetle**

## <a name="enable-continuous-integration"></a>Sürekli Tümleştirme etkinleştir

İstediğiniz zaman oluşturmak proje neden olan bir tetikleyici yaparız artık bir değişiklik için iade `ci-cd-example` git deponun dalı.

1. TFS'de, tıklatın **yapı & yayın** sekmesi
1. Seçin `DNS Infra` yapı tanımı öğesini tıklatıp **Düzenle**
1. Tıklatın **Tetikleyicileri** sekmesi
1. Seçin **sürekli tümleştirme (CI)** seçip `refs/heads/ci-cd-example` şube aşağı açılan listesinde
1. Tıklatın **kaydetmek** ve ardından **Tamam**

Artık TFS git deposu Tetikleyicileri otomatik derleme değiştirin.

## <a name="create-the-release-definition"></a>Yayın tanımı oluşturun

Böylece proje her kod iade geliştirme ortamı dağıtılmış bir sürüm tanımı oluşturalım.

Bunu yapmak için ilişkili yeni bir sürüm tanımı eklemek `InfraDNS` yapı daha önce oluşturduğunuz tanımı.
Seçtiğinizden emin olun **sürekli dağıtım** böylece yeni bir yapı tamamlandığında dilediğiniz zaman yeni bir sürüm tetiklenir.
([Nasıl yapılır: çalışma yayın tanımlarla](https://www.visualstudio.com/en-us/docs/build/actions/work-with-release-definitions)) ve aşağıdaki gibi yapılandırın:

Aşağıdaki adımları yayın tanımına ekleyin:

- PowerShell Betiği
- Test sonuçlarını yayımlama
- Test sonuçlarını yayımlama

Adımları aşağıdaki gibi düzenleyin:

### <a name="powershell-script"></a>PowerShell Betiği

1. Ayarlama **betik yolu** alanı `$(Build.DefinitionName)\Deploy\initiate.ps1"`
1. Ayarlama **bağımsız değişkenleri** alanı `-fileName Deploy`

### <a name="first-publish-test-results"></a>İlk Test sonuçlarını yayımlama

1. Seçin `NUnit` için **Test Sonuç biçimi** alan
1. Ayarlama **Test sonuç dosyalarını** alanı `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Integration*.xml`
1. Ayarlama **çalıştırma başlığı Test** için `Integration`
1. Altında **denetim seçeneklerini**, denetleme **her zaman çalıştır**

### <a name="second-publish-test-results"></a>İkinci Test sonuçlarını yayımlama

1. Seçin `NUnit` için **Test Sonuç biçimi** alan
1. Ayarlama **Test sonuç dosyalarını** alanı `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Acceptance*.xml`
1. Ayarlama **çalıştırma başlığı Test** için `Acceptance`
1. Altında **denetim seçeneklerini**, denetleme **her zaman çalıştır**

## <a name="verify-your-results"></a>Sonuçlarınızı doğrulayın

Şimdi, dilediğiniz zaman, anında değişiklikleri `ci-cd-example` TFS, yeni bir yapı dala başlayacak.
Yapılandırma başarıyla tamamlanırsa, yeni bir dağıtım tetiklenir.

İstemci makinesinde bir tarayıcı açıp giderek dağıtımının sonucu denetleyebilirsiniz `www.contoso.com`.

## <a name="next-steps"></a>Sonraki adımlar

Bu örnek DNS sunucusu yapılandırır `TestAgent1` böylece URL `www.contoso.com` çözümler `TestAgent2`, ancak bir Web sitesi gerçekte dağıtmaz.
Bunu yapmak için çatıyı depodaki altında sağlanan `WebApp` klasör.
Psake komut dosyaları, Pester testleri ve DSC yapılandırmaları oluşturmak için sağlanan saplamalar kendi Web sitenizi dağıtmak için kullanabilirsiniz.