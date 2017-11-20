# [Genel bakış](overview.md)

## [Karar Mercileri için İstenen Durum Yapılandırmasına Genel Bakış](decisionMaker.md)

## [Mühendisler için İstenen Durum Yapılandırmasına Genel Bakış](DscForEngineers.md)

## [DSC hızlı başlangıç](quickStart.md)

# [Yapılandırmalar](configurations.md)

## [Yapılandırmaları Kabul Etme](enactingConfigurations.md)

## [Yapılandırma ve ortam verilerini ayırma](separatingEnvData.md)

## [Birden çok sürümü olan kaynakları kullanma](sxsResource.md)

## [DSC’yi kullanıcı kimlik bilgileri ile çalıştırma](runAsUser.md)

## [Çapraz düğüm bağımlılıklarını belirtme](crossNodeDependencies.md)

## [Yapılandırma verileri](configData.md)

### [Yapılandırma verilerinde kimlik bilgisi seçenekleri](configDataCredentials.md)

## [Yapılandırmaları iç içe yerleştirme](compositeConfigs.md)

## [Yapılandırma MOF dosyasının güvenliğini sağlama](secureMOF.md)

## [Kısmi Yapılandırmalar](partialConfigs.md)

## [DSC yapılandırmaları için yardım sayfası yazma](configHelp.md)

## [DSC kullanarak bir sanal makineyi ilk önyüklemede yapılandırma](bootstrapDsc.md)

### [DSCAutomationHostEnabled kayıt defteri anahtarı](DSCAutomationHostEnabled.md)

# [Kaynaklar](resources.md)

## [Yerleşik kaynaklar](builtInResource.md)

### [Archive Kaynağı](archiveResource.md)

### [Environment Kaynağı](environmentResource.md)

### [File Kaynağı](fileResource.md)

### [Group Kaynağı](groupResource.md)

### [GroupSet Kaynağı](groupSetResource.md)

### [Log Kaynağı](logResource.md)

### [Package Kaynağı](packageResource.md)

### [ProcessSet Kaynağı](processSetResource.md)

### [Registry Kaynağı](registryResource.md)

### [Script Kaynağı](scriptResource.md)

### [Service Kaynağı](serviceResource.md)

### [ServiceSet Kaynağı](serviceSetResource.md)

### [User Kaynağı](userResource.md)

### [WaitForAll Kaynağı](waitForAllResource.md)

### [WaitForAny Kaynağı](waitForAnyResource.md)

### [WaitForSome Kaynağı](waitForSomeResource.md)

### [WindowsFeature Kaynağı](windowsfeatureResource.md)

### [WindowsFeatureSet Kaynağı](windowsFeatureSetResource.md)

### [WindowsOptionalFeature Kaynağı](windowsOptionalFeatureResource.md)

### [WindowsOptionalFeatureSet Kaynağı](windowsOptionalFeatureSetResource.md)

### [WindowsPackageCab Kaynağı](windowsPackageCabResource.md)

### [WindowsProcess Kaynağı](windowsProcessResource.md)

## [Özel kaynak yazma](authoringResource.md) 

### [MOF temelli özel kaynaklar](authoringResourceMOF.md)

#### [C#’de MOF temelli kaynak](authoringResourceMofCS.md)

### [Sınıf temelli özel kaynaklar](authoringResourceClass.md)

### [Bileşik kaynaklar](authoringResourceComposite.md)

### [Tek örnekli DSC kaynağı yazma (en iyi uygulama)](singleInstance.md)

### [Kaynak yazma denetim listesi](resourceAuthoringChecklist.md)

## [DSC kaynaklarında hata ayıklama](debugResource.md)

## [DSC kaynağını doğrudan çağırma](directCallResource.md)

# Yerel Configuration Manager

## [Local Configuration Manager’ı (LCM) Yapılandırma](metaConfig.md)

## [PowerShell 4.0’da LCM yapılandırma](metaConfig4.md)

# DSC çekme modeli

## [Web çekme sunucusu ayarlama](pullServer.md)

## [DSC SMB çekme sunucusu ayarlama](pullServerSMB.md)

## [Çekme istemcisi ayarlama](pullClient.md)

### [Yapılandırma adlarını kullanarak çekme istemcisi ayarlama](pullClientConfigNames.md)

### [Yapılandırma kimliğini kullanarak çekme istemcisi ayarlama](pullClientConfigID.md)

## [DSC rapor sunucusu kullanma](reportServer.md)

## [Çekme sunucusu en iyi uygulamaları](secureServer.md)

# [DSC örnekleri](dscExamples.md)

## [DSC, Pester ve Visual Studio Team Services ile CI/CD komut zinciri derleme](dscCiCd.md)

## [Yapılandırma ve ortam verilerini ayırma](separatingEnvData.md)

# [DSC’de sorun giderme](troubleshooting.md)

# [Nano Server’da DSC Kullanma](nanoDsc.md)

# Linux’ta DSC

## [Linux için DSC’ye başlarken](lnxGettingStarted.md)

## [Linux için yerleşik kaynaklar](lnxBuiltInResources.md)

### [nxArchive Kaynağı](lnxArchiveResource.md)

### [nxEnvironment Kaynağı](lnxEnvironmentResource.md)

### [nxFile Kaynağı](lnxFileResource.md)

### [nxFileLine Kaynağı](lnxFileLineResource.md)

### [nxGroup Kaynağı](lnxGroupResource.md)

### [nxPackage Kaynağı](lnxPackageResource.md)

### [nxService Kaynağı](lnxServiceResource.md)

### [nxSshAuthorizedKeys Kaynağı](lnxSshAuthorizedKeysResource.md)

### [nxUser Kaynağı](lnxUserResource.md)

# [Microsoft Azure’da DSC Kullanma](azureDsc.md)

# DSC MOF Başvurusu

## [MSFT_DSCLocalConfigurationManager sınıfı](msft-dsclocalconfigurationmanager.md)

### [MSFT_DSCLocalConfigurationManager sınıfının ApplyConfiguration yöntemi](msft-dsclocalconfigurationmanager-applyconfiguration.md)

### [MSFT_DSCLocalConfigurationManager sınıfının DisableDebugConfiguration yöntemi](msft-dsclocalconfigurationmanager-disabledebugconfiguration.md)

### [MSFT_DSCLocalConfigurationManager sınıfının EnableDebugConfiguration yöntemi](msft-dsclocalconfigurationmanager-enabledebugconfiguration.md)

### [MSFT_DSCLocalConfigurationManager sınıfının GetConfiguration yöntemi](msft-dsclocalconfigurationmanager-getconfiguration.md)

### [MSFT_DSCLocalConfigurationManager sınıfının GetConfigurationResultOutput yöntemi](msft-dsclocalconfigurationmanager-getconfigurationresultoutput.md)

### [MSFT_DSCLocalConfigurationManager sınıfının GetConfigurationStatus yöntemi](msft-dsclocalconfigurationmanager-getconfigurationstatus.md)

### [MSFT_DSCLocalConfigurationManager sınıfının GetMetaConfiguration yöntemi](msft-dsclocalconfigurationmanager-getmetaconfiguration.md)

### [MSFT_DSCLocalConfigurationManager sınıfının PerformRequiredConfigurationChecks yöntemi](msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks.md)

### [MSFT_DSCLocalConfigurationManager sınıfının RemoveConfiguration yöntemi](msft-dsclocalconfigurationmanager-removeconfiguration.md)

### [MSFT_DSCLocalConfigurationManager sınıfının ResourceGet yöntemi](msft-dsclocalconfigurationmanager-resourceget.md)

### [MSFT_DSCLocalConfigurationManager sınıfının ResourceSet yöntemi](msft-dsclocalconfigurationmanager-resourceset.md)

### [MSFT_DSCLocalConfigurationManager sınıfının ResourceTest yöntemi](msft-dsclocalconfigurationmanager-resourcetest.md)

### [MSFT_DSCLocalConfigurationManager sınıfının RollBack yöntemi](msft-dsclocalconfigurationmanager-rollback.md)

### [MSFT_DSCLocalConfigurationManager sınıfının SendConfiguration yöntemi](msft-dsclocalconfigurationmanager-sendconfiguration.md)

### [MSFT_DSCLocalConfigurationManager sınıfının SendConfigurationApply yöntemi](msft-dsclocalconfigurationmanager-sendconfigurationapply.md)

### [MSFT_DSCLocalConfigurationManager sınıfının SendConfigurationApplyAsync yöntemi](msft-dsclocalconfigurationmanager-sendconfigurationapplyasync.md)

### [MSFT_DSCLocalConfigurationManager sınıfının SendMetaConfigurationApply yöntemi](msft-dsclocalconfigurationmanager-sendmetaconfigurationapply.md)

### [MSFT_DSCLocalConfigurationManager sınıfının StopConfiguration yöntemi](msft-dsclocalconfigurationmanager-stopconfiguration.md)

### [MSFT_DSCLocalConfigurationManager sınıfının TestConfiguration yöntemi](msft-dsclocalconfigurationmanager-testconfiguration.md)

# Daha Fazla Kaynak

## [Teknik İncelemeler](whitepapers.md)
