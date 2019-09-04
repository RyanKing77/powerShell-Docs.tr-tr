---
ms.date: 12/12/2018
keywords: DSC, PowerShell, yapılandırma, kurulum
title: Yerel Configuration Manager yapılandırma
ms.openlocfilehash: 42544036d87fcea3189fd6d2e55579fe87f137e1
ms.sourcegitcommit: 02eed65c526ef19cf952c2129f280bb5615bf0c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70215395"
---
# <a name="configuring-the-local-configuration-manager"></a>Yerel Configuration Manager yapılandırma

> Şunun için geçerlidir: Windows PowerShell 5,0

Yerel Configuration Manager (LCM), Istenen durum yapılandırması (DSC) altyapısıdır.
LCM her hedef düğümde çalışır ve düğüme gönderilen yapılandırmaların ayrıştırılmasından ve davranmasından sorumludur.
Ayrıca, aşağıdakiler de dahil olmak üzere DSC 'nin çeşitli yönlerini de sorumludur.

- Yenileme modunu belirleme (push veya Pull).
- Bir düğümün yapılandırmaların ne sıklıkta çekmesini ve bu şekilde davranacağını belirtme.
- Düğüm, çekme hizmeti ile ilişkilendiriliyor.
- Kısmi yapılandırma belirtme.

LCM 'yi bu davranışların her birini belirtecek şekilde yapılandırmak için özel bir yapılandırma türü kullanırsınız.
Aşağıdaki bölümlerde LCM 'nin nasıl yapılandırılacağı açıklanır.

Windows PowerShell 5,0, yerel Configuration Manager yönetmeye yönelik yeni ayarlar sunmuştur.
Windows PowerShell 4,0 ' de LCM 'yi yapılandırma hakkında daha fazla bilgi için bkz. [Windows PowerShell 'In önceki sürümlerinde yerel Configuration Manager yapılandırma](metaconfig4.md).

## <a name="writing-and-enacting-an-lcm-configuration"></a>LCM yapılandırmasını yazma ve işleme

LCM 'yi yapılandırmak için, LCM ayarlarını uygulayan özel bir yapılandırma türü oluşturun ve çalıştırın.
LCM yapılandırmasını belirtmek için, DscLocalConfigurationManager özniteliğini kullanırsınız.
Aşağıda, LCM 'yi gönderim moduna ayarlayan basit bir yapılandırma gösterilmektedir.

```powershell
[DSCLocalConfigurationManager()]
configuration LCMConfig
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Push'
        }
    }
}
```

LCM 'ye ayarları uygulama işlemi bir DSC yapılandırması uygulamaya benzer.
Bir LCM yapılandırması oluşturacak, onu bir MOF dosyasına derlemenize ve düğüme uygulayacaksınız.
DSC yapılandırmalarının aksine, [Start-dscconfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet 'ini çağırarak bir LCM yapılandırması davranmayın.
Bunun yerine, LCM yapılandırma MOF 'nin yolunu parametre olarak sağlayarak [set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager)' ı çağırın.
LCM yapılandırmasını uyguladıktan sonra, [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) cmdlet 'ini çağırarak LCM 'nin özelliklerini görebilirsiniz.

LCM yapılandırmasında yalnızca sınırlı sayıda kaynak kümesi için bloklar bulunabilir.
Önceki örnekte, çağrılan tek kaynak **Ayarlar**' dır.
Kullanılabilir diğer kaynaklar şunlardır:

* **Configurationdepotoryweb**: yapılandırmalara YÖNELIK bir http çekme hizmeti belirtir.
* **Configurationdepotorshare**: yapılandırmalara YÖNELIK bir SMB paylaşımının belirtir.
* **Resourcerepositoryweb**: modüller IÇIN bir http çekme hizmeti belirtir.
* **Resourcerepositoryshare**: modüller IÇIN bir SMB paylaşımının belirtir.
* **Reportserverweb**: RAPORLARıN gönderildiği http çekme hizmetini belirtir.
* **Partialconfiguration**: kısmi yapılandırmaları etkinleştirmek için veri sağlar.

## <a name="basic-settings"></a>Temel ayarlar

İstek hizmeti uç noktaları/yolları ve kısmi yapılandırmaların belirtilme dışında, LCM 'nin tüm özellikleri bir **Ayarlar** bloğunda yapılandırılır.
Aşağıdaki özellikler bir **Ayarlar** bloğunda mevcuttur.

|  Özellik  |  Tür  |  Açıklama   |
|----------- |------- |--------------- |
| ActionAfterReboot| dize| Bir yapılandırmanın uygulaması sırasında yeniden başlatmanın ardından ne olacağını belirtir. Olası değerler şunlardır __"devam yapılandırması"__ ve __"stopconfiguration"__ . <ul><li> __Devam yapılandırması__: Makine yeniden başlatıldıktan sonra geçerli yapılandırmayı uygulamaya devam edin. Bu varsayılan değerdir</li><li>__Stopconfiguration__: Makine yeniden başlatıldıktan sonra geçerli yapılandırmayı durdur.</li></ul>|
| AllowModuleOverwrite| bool| Çekme hizmetinden indirilen yeni yapılandırmaların hedef düğümde eskilerinin üzerine yazılmasına izin veriliyorsa __$true__ . Aksi takdirde, $FALSE.|
| Sertifika kimliği| dize| Bir yapılandırmada geçirilen kimlik bilgilerini güvenli hale getirmek için kullanılan bir sertifikanın parmak izi. Daha fazla bilgi için bkz. [Windows PowerShell Istenen durum yapılandırmasında kimlik bilgilerini güvenli hale getirmek](http://blogs.msdn.com/b/powershell/archive/2014/01/31/want-to-secure-credentials-in-windows-powershell-desired-state-configuration.aspx)istiyor musunuz?. <br> __Note:__ Azure Automation DSC çekme hizmeti kullanılıyorsa bu otomatik olarak yönetilir.|
| Configurationdownloadyöneticileri| CimInstance []| Kullanımdan kalktı. Yapılandırma çekme hizmeti uç noktalarını tanımlamak için __Configurationdepotoryweb__ ve __Configurationdepotoryshare__ bloklarını kullanın.|
| ConfigurationId| dize| Daha eski çekme hizmeti sürümleriyle geriye dönük uyumluluk için. Bir çekme hizmetinden alınacak yapılandırma dosyasını tanımlayan bir GUID. Yapılandırma MOF adı ConfigurationId. mof olarak adlandırılmışsa düğüm çekme hizmetinde yapılandırmaları çeker.<br> __Not:__ Bu özelliği ayarlarsanız, __Registrationkey__ kullanarak düğümü bir çekme hizmetine kaydetmek çalışmaz. Daha fazla bilgi için bkz. [yapılandırma adlarıyla bir çekme Istemcisi ayarlama](../pull-server/pullClientConfigNames.md).|
| ConfigurationMode| dize | LCM 'nin yapılandırmayı hedef düğümlere gerçekten nasıl uygulayacağını belirtir. Olası değerler şunlardır. __"Applyonly"__ , __"applyandmonitor"__ ve __"applyandadutocorrect"__ . <ul><li>__Yalnızca Apply:__ DSC, yapılandırmayı uygular ve hedef düğüme yeni bir yapılandırma itilemez veya bir hizmetten yeni bir yapılandırma çekilmediği takdirde hiçbir şey yapmaz. Yeni yapılandırmanın ilk uygulamasından sonra DSC, daha önce yapılandırılmış bir durumdan DRFT 'yi denetlemez. DSC 'nin yapılandırma işlemi, __yalnızca applyyürürlüğe__ girmeden önce başarılı olana kadar yapılandırmayı uygulamayı deneyeceği unutulmamalıdır. </li><li> __Applyandizleyicisi__: Bu varsayılan değerdir. LCM, yeni yapılandırma uygular. Yeni yapılandırmanın ilk uygulamasından sonra, hedef düğüm istenen durumdan Drifts, DSC, günlüklerde tutarsızlığı raporlar. Bu, __Applmanagermonitor__ 'un yürürlüğe girmeden önce, DSC 'nin yapılandırmayı uygulamayı deneyeceği unutulmamalıdır.</li><li>__Applyandadutocorrect__: DSC, yeni yapılandırma uygular. Yeni yapılandırmanın ilk uygulamasından sonra, hedef düğüm istenen durumdan Drifts, DSC günlüklerde tutarsızlığı raporlar ve ardından geçerli yapılandırmayı yeniden uygular.</li></ul>|
| Configurationmodefkarşılandığından Modüldak| UInt32| Dakika cinsinden, geçerli yapılandırmanın denetlenme ve uygulanma sıklığı. ConfigurationMode özelliği ApplyOnly olarak ayarlandıysa bu özellik yoksayılır. Varsayılan değer 15 ' tir.|
| DebugMode| dize| Olası değerler None, __forcemoduleımport__ve __All__ __'tur__. <ul><li>Önbelleğe alınmış kaynakları kullanmak için __none__ olarak ayarlayın. Bu varsayılandır ve üretim senaryolarında kullanılmalıdır.</li><li>__Forcemoduleımport__olarak ayarlandığında, daha önce yüklenmiş ve önbelleğe alınmış olsa bile LCM 'nin DSC kaynak modüllerini yeniden yüklemesine neden olur. Bu, her modül kullanımda yeniden yüklendiğinde DSC işlemlerinin performansını etkiler. Genellikle bu değeri bir kaynakta hata ayıklarken kullanırsınız</li><li>Bu sürümde, __Tümü__ __forcemoduleımport__ ile aynıdır</li></ul> |
| Rebootnodeifgerekliyse| bool| Bu ayarı, `$true` `$global:DSCMachineStatus` kaynakların, bayrağını kullanarak düğümü yeniden başlatması için olarak ayarlayın. Aksi takdirde, düğümü gerektiren herhangi bir yapılandırma için el ile yeniden başlatmanız gerekir. Varsayılan değer `$false` şeklindedir. Bir yeniden başlatma koşulu DSC dışında bir öğe tarafından (örneğin, Windows Installer) işlem yapıldığında bu ayarı kullanmak için, bu ayarı [Xpendingreboot](https://github.com/powershell/xpendingreboot) modülüyle birleştirin.|
| RefreshMode| dize| LCM 'in yapılandırmaların nasıl alınacağını belirtir. Olası değerler şunlardır __"devre dışı"__ , __"Push"__ ve __"çekme"__ . <ul><li>__Devre dışı__: Bu düğüm için DSC yapılandırması devre dışı bırakıldı.</li><li> __Gönderim__: Yapılandırmalar [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet 'i çağırarak başlatılır. Yapılandırma düğüme hemen uygulanır. Bu varsayılan değerdir.</li><li>__Çek__ Düğüm, bir çekme hizmetinden veya SMB yolundan gelen yapılandırmaların düzenli olarak denetlenmesi için yapılandırılır. Bu özellik __Pull__olarak ayarlandıysa, __Configurationdepotoryweb__ veya __CONFIGURATIONDEPOTORYSHARE__ bloğunda BIR http (hizmet) veya SMB (Share) yolu belirtmeniz gerekir.</li></ul>|
| RefreshFrequencyMins| Int32| LCM 'nin, güncelleştirilmiş yapılandırmaların alınacağı bir çekme hizmetini denetlediği dakika cinsinden zaman aralığı. LCM, çekme modunda yapılandırılmamışsa, bu değer yoksayılır. Varsayılan değer 30’dur.|
| Reportyöneticileri| CimInstance []| Kullanımdan kalktı. Raporlama verilerini bir çekme hizmetine göndermek için bir uç nokta tanımlamak üzere __Reportserverweb__ bloklarını kullanın.|
| Resourcemoduleyöneticileri| CimInstance []| Kullanımdan kalktı. Sırasıyla çekme hizmeti HTTP uç noktalarını veya SMB yollarını tanımlamak için __Resourcerepositoryweb__ ve __Resourcerepositoryshare__ bloklarını kullanın.|
| PartialConfigurations| CimInstance| Uygulanmadı. Kullanmayın.|
| StatusRetentionTimeInDays | UInt32| LCM 'nin geçerli yapılandırmanın durumunu tutacağını gün sayısı.|

> [!NOTE]
> LCM, **Configurationmodefkarşılandığından Hacmins** döngüsünü temel alarak başlatır:
>
> - Kullanılarak yeni bir metaconfig uygulandı`Set-DscLocalConfigurationManager`
> - Makinenin yeniden başlatılması
>
> Zamanlayıcı işleminin bir kilitlenme deneyiminden karşılaştığı, 30 saniye içinde algıladığı ve bu süre yeniden başlatılacak olan herhangi bir koşul için.
> Eşzamanlı bir işlem döngüyü gecikebilir ve bu işlemin süresi yapılandırılan süre sıklığını aşarsa, sonraki süreölçer başlatılmaz.
>
> Örnek olarak, metaconfig 15 dakikalık bir çekme sıklığında yapılandırılır ve T1 konumunda bir çekme gerçekleşir.  Düğüm, 16 dakika boyunca çalışmayı tamamlayamadı.  İlk 15 dakikalık zaman yok sayılır ve sonraki çekme T1 + 15 + 15 ' te gerçekleşir.

## <a name="pull-service"></a>Çekme Hizmeti

LCM yapılandırması, aşağıdaki çekme hizmeti uç noktası türlerini tanımlamayı destekler:

- **Yapılandırma sunucusu**: DSC yapılandırmalarına yönelik bir depo. Yapılandırma sunucularını, **Configurationdepotoryweb** (Web tabanlı sunucular için) ve **Configurationdepotoryshare** (SMB tabanlı sunucular için) blokları kullanarak tanımlayın.
- **Kaynak sunucu**: DSC kaynakları için PowerShell modülleri olarak paketlenmiş bir depo. Kaynak sunucularını **Resourcerepositoryweb** (Web tabanlı sunucular için) ve **Resourcerepositoryshare** (SMB tabanlı sunucular için) blokları kullanarak tanımlayın.
- **Rapor sunucusu**: DSC 'nin rapor verilerini göndereceği bir hizmet. Rapor sunucularını **Reportserverweb** bloklarını kullanarak tanımlayın. Rapor sunucusu bir Web hizmeti olmalıdır.

Çekme hizmeti hakkında daha fazla bilgi için bkz. [Istenen durum yapılandırması çekme hizmeti](../pull-server/pullServer.md).

## <a name="configuration-server-blocks"></a>Yapılandırma sunucusu blokları

Web tabanlı bir yapılandırma sunucusu tanımlamak için bir **Configurationdepotoryweb** bloğu oluşturursunuz.
Bir **Configurationdepotoryweb** , aşağıdaki özellikleri tanımlar.

|Özellik|Tür|Açıklama|
|---|---|---|
|AllowUnsecureConnection|bool|Düğümden sunucuya kimlik doğrulaması olmadan bağlantılara izin vermek için **$true** olarak ayarlayın. Kimlik doğrulaması gerektirmek için **$false** olarak ayarlayın.|
|Sertifika kimliği|dize|Sunucuda kimlik doğrulamak için kullanılan sertifikanın parmak izi.|
|ConfigurationNames|String[]|Hedef düğüm tarafından çekilecek yapılandırmaların bir ad dizisi. Bunlar yalnızca, düğüm çekme hizmetine bir **Registrationkey**kullanılarak kayıtlıysa kullanılır. Daha fazla bilgi için bkz. [yapılandırma adlarıyla bir çekme Istemcisi ayarlama](../pull-server/pullClientConfigNames.md).|
|RegistrationKey|dize|Çekme hizmeti ile düğümü kaydeden bir GUID. Daha fazla bilgi için bkz. [yapılandırma adlarıyla bir çekme Istemcisi ayarlama](../pull-server/pullClientConfigNames.md).|
|ServerURL|dize|Yapılandırma hizmetinin URL 'SI.|
|ProxyURL *|dize|Yapılandırma hizmetiyle iletişim kurulurken kullanılacak http proxy 'sinin URL 'si.|
|ProxyCredential *|PSCredential|Http proxy 'si için kullanılacak kimlik bilgileri.|

> [!NOTE]
> * Windows sürümleri 1809 ve üzeri sürümlerde desteklenir.

Şirket içi düğümler için Configurationdepotoryweb değerini yapılandırmayı kolaylaştıran örnek bir betik mevcuttur-bkz. [DSC meta yapılandırmalarını oluşturma](https://docs.microsoft.com/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations)

SMB tabanlı bir yapılandırma sunucusu tanımlamak için bir **Configurationdepotorshare** bloğu oluşturursunuz.
Bir **Configurationdepotorshare** aşağıdaki özellikleri tanımlar.

|Özellik|Tür|Açıklama|
|---|---|---|
|Credential|MSFT_Credential|SMB paylaşımında kimlik doğrulamak için kullanılan kimlik bilgileri.|
|Yolundan|dize|SMB paylaşımının yolu.|

## <a name="resource-server-blocks"></a>Kaynak sunucu blokları

Web tabanlı bir kaynak sunucusu tanımlamak için, **Resourcerepositoryweb** bloğu oluşturursunuz.
**Resourcerepositoryweb** , aşağıdaki özellikleri tanımlar.

|Özellik|Tür|Açıklama|
|---|---|---|
|AllowUnsecureConnection|bool|Düğümden sunucuya kimlik doğrulaması olmadan bağlantılara izin vermek için **$true** olarak ayarlayın. Kimlik doğrulaması gerektirmek için **$false** olarak ayarlayın.|
|Sertifika kimliği|dize|Sunucuda kimlik doğrulamak için kullanılan sertifikanın parmak izi.|
|RegistrationKey|dize|Çekme hizmeti için düğümü tanımlayan bir GUID.|
|ServerURL|dize|Yapılandırma sunucusunun URL 'SI.|
|ProxyURL *|dize|Yapılandırma hizmetiyle iletişim kurulurken kullanılacak http proxy 'sinin URL 'si.|
|ProxyCredential *|PSCredential|Http proxy 'si için kullanılacak kimlik bilgileri.|

> [!NOTE]
> * Windows sürümleri 1809 ve üzeri sürümlerde desteklenir.

Şirket içi düğümler için ResourceRepositoryWeb değerini yapılandırmayı kolaylaştıran örnek bir betik mevcuttur-bkz. [DSC meta yapılandırmalarını oluşturma](https://docs.microsoft.com/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations)

SMB tabanlı bir kaynak sunucusu tanımlamak için, **Resourcerepositoryshare** bloğu oluşturursunuz.
**Resourcerepositoryshare** aşağıdaki özellikleri tanımlar.

|Özellik|Tür|Açıklama|
|---|---|---|
|Credential|MSFT_Credential|SMB paylaşımında kimlik doğrulamak için kullanılan kimlik bilgileri. Kimlik bilgilerini geçirme örneği için bkz. [DSC SMB çekme sunucusu ayarlama](../pull-server/pullServerSMB.md)|
|Yolundan|dize|SMB paylaşımının yolu.|

## <a name="report-server-blocks"></a>Rapor sunucusu blokları

Bir rapor sunucusu tanımlamak için bir **Reportserverweb** bloğu oluşturursunuz.
Rapor sunucusu rolü, SMB tabanlı çekme hizmeti ile uyumlu değil.
**Reportserverweb** , aşağıdaki özellikleri tanımlar.

|Özellik|Tür|Açıklama|
|---|---|---|
|AllowUnsecureConnection|bool|Düğümden sunucuya kimlik doğrulaması olmadan bağlantılara izin vermek için **$true** olarak ayarlayın. Kimlik doğrulaması gerektirmek için **$false** olarak ayarlayın.|
|Sertifika kimliği|dize|Sunucuda kimlik doğrulamak için kullanılan sertifikanın parmak izi.|
|RegistrationKey|dize|Çekme hizmeti için düğümü tanımlayan bir GUID.|
|ServerURL|dize|Yapılandırma sunucusunun URL 'SI.|
|ProxyURL *|dize|Yapılandırma hizmetiyle iletişim kurulurken kullanılacak http proxy 'sinin URL 'si.|
|ProxyCredential *|PSCredential|Http proxy 'si için kullanılacak kimlik bilgileri.|

> [!NOTE]
> * Windows sürümleri 1809 ve üzeri sürümlerde desteklenir.

Şirket içi düğümler için ReportServerWeb değerini yapılandırmayı kolaylaştıran örnek bir betik mevcuttur-bkz. [DSC meta yapılandırmalarını oluşturma](https://docs.microsoft.com/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations)

## <a name="partial-configurations"></a>Kısmi yapılandırma

Kısmi bir yapılandırma tanımlamak için, bir **partialconfiguration** bloğu oluşturursunuz.
Kısmi yapılandırma hakkında daha fazla bilgi için bkz. [DSC kısmi yapılandırmalarına](../pull-server/partialConfigs.md).
**Partialconfiguration** aşağıdaki özellikleri tanımlar.

|Özellik|Tür|Açıklama|
|---|---|---|
|ConfigurationSource|String []|Daha önce **Configurationdepotoryweb** ve **Configurationdepotoryshare** blokları içinde tanımlanan ve kısmi yapılandırmanın çekileceği, yapılandırma sunucularının bir ad dizisi.|
|DependsOn|dizisinde{}|Bu kısmi yapılandırma uygulanmadan önce tamamlanması gereken diğer yapılandırmaların adlarının listesi.|
|Açıklama|dize|Kısmi yapılandırmayı anlatmak için kullanılan metin.|
|ExclusiveResources|String []|Bu kısmi yapılandırmaya özel bir kaynak dizisi.|
|RefreshMode|dize|LCM 'nin bu kısmi yapılandırmayı nasıl kullandığını belirtir. Olası değerler şunlardır __"devre dışı"__ , __"Push"__ ve __"çekme"__ . <ul><li>__Devre dışı__: Bu kısmi yapılandırma devre dışı bırakıldı.</li><li> __Gönderim__: Kısmi yapılandırma, [Yayımla-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet 'i çağırarak düğüme gönderilir. Düğüm için tüm kısmi yapılandırmalar bir hizmetten itilmiş veya çekildikten sonra, bu yapılandırma çağırarak `Start-DscConfiguration –UseExisting`bu yapılandırma başlatılabilir. Bu varsayılan değerdir.</li><li>__Çek__ Düğüm, bir çekme hizmetinden kısmi yapılandırmayı düzenli olarak denetleyecek şekilde yapılandırılmıştır. Bu özellik __Pull__olarak ayarlandıysa, bir __configurationsource__ özelliğinde bir çekme hizmeti belirtmeniz gerekir. Azure Otomasyonu çekme hizmeti hakkında daha fazla bilgi için bkz. [azure Automation DSC genel bakış](https://docs.microsoft.com/azure/automation/automation-dsc-overview).</li></ul>|
|ResourceModuleSource|String []|Bu kısmi yapılandırma için gerekli kaynakların indirileceği kaynak sunucularının adlarından oluşan bir dizi. Bu adlar, daha önce **Resourcerepositoryweb** ve **Resourcerepositoryshare** blokları içinde tanımlanan hizmet uç noktalarına başvurmalıdır.|

__Note:__ kısmi yapılandırmalar Azure Automation DSC desteklenir, ancak düğüm başına her bir Otomasyon hesabından yalnızca bir yapılandırma alınabilir.

## <a name="see-also"></a>Ayrıca bkz:

### <a name="concepts"></a>Kavramlar
[İstenen durum yapılandırmasına genel bakış](../overview/overview.md)

[Azure Automation DSC kullanmaya başlama](https://docs.microsoft.com/azure/automation/automation-dsc-getting-started)

### <a name="other-resources"></a>Diğer Kaynaklar

[Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager)

[Yapılandırma adlarıyla bir çekme istemcisi ayarlama](../pull-server/pullClientConfigNames.md)
