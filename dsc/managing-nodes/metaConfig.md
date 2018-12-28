---
ms.date: 12/12/2018
keywords: DSC, powershell, yapılandırma, Kurulum
title: Yerel Configuration Manager'ı yapılandırma
ms.openlocfilehash: c3ced2376c7d99477c40ae078dcecd775538b350
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405797"
---
# <a name="configuring-the-local-configuration-manager"></a>Yerel Configuration Manager'ı yapılandırma

> Şunun için geçerlidir: Windows PowerShell 5.0

Yerel Configuration Manager (LCM) Desired State Configuration (DSC) altyapısıdır.
LCM her hedef düğüm üzerinde çalışır ve ayrıştırma ve düğüme gönderilen yapılandırmaları kabul etme sorumludur.
Ayrıca, DSC, aşağıdakiler dahil olmak üzere diğer yönlerine bir sayısı için sorumlu değildir.

- Yenileme modu (itme veya çekme) belirleme.
- Bir düğüm ne sıklıkta çeker ve yapılandırmaları enacts belirtme.
- Düğüm çekme hizmetiyle ilişkilendirme.
- Kısmi yapılandırmalar belirtme.

Bu davranışların her biri belirtmek için LCM yapılandırmak için özel yapılandırma türünü kullanın.
Aşağıdaki bölümlerde LCM yapılandırma açıklanmaktadır.

Windows PowerShell 5.0, yerel Configuration Manager'ı yönetmek için yeni ayarlar kullanıma sunuldu.
Windows PowerShell 4. 0'lcm yapılandırma hakkında daha fazla bilgi için bkz: [önceki sürümleri, Windows PowerShell'de yerel Configuration Manager Yapılandırma](metaconfig4.md).

## <a name="writing-and-enacting-an-lcm-configuration"></a>Yazma ve kabul etme LCM yapılandırma

LCM yapılandırmak için oluşturma ve LCM ayarlarını uygulayan yapılandırma özel bir tür çalıştırın.
LCM yapılandırma belirtmek için DscLocalConfigurationManager özniteliğini kullanın.
LCM gönderme modunda ayarlar basit bir yapılandırma gösterilmektedir.

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

LCM için ayarlarının uygulanması işleminin benzer bir DSC yapılandırması uygulanamıyor.
LCM yapılandırma oluşturmak için bir MOF dosyası derleme ve düğüme uygulamak.
DSC yapılandırmaları, bir LCM yapılandırma çağırarak geçireceğini değil [Başlat-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet'i.
Bunun yerine çağrı [Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager), parametre olarak MOF LCM yapılandırma yolu sağlama.
LCM yapılandırma geçireceğini sonra çağırarak LCM özelliklerini görebilirsiniz [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) cmdlet'i.

LCM yapılandırma, yalnızca sınırlı bir kaynak kümesi için blok içerebilir.
Önceki örnekte, adı verilen tek kaynaktır **ayarları**.
Diğer kullanılabilir kaynakları şunlardır:

* **ConfigurationRepositoryWeb**: yapılandırmalar için bir HTTP çekme hizmetini belirtir.
* **ConfigurationRepositoryShare**: bir SMB paylaşımı yapılandırmaları için belirtir.
* **ResourceRepositoryWeb**: modül için bir HTTP çekme hizmetini belirtir.
* **ResourceRepositoryShare**: modüller için SMB paylaşımı belirtir.
* **ReportServerWeb**: raporlar gönderildiği bir HTTP çekme hizmetini belirtir.
* **PartialConfiguration**: Kısmi yapılandırmalar etkinleştirmek için veri sağlar.

## <a name="basic-settings"></a>Temel ayarları

Çekme hizmet uç noktaları/yolları ve kısmi yapılandırmalar belirtilmesi dışında tüm LCM özelliklerinin yapılandırılmış bir **ayarları** blok.
Aşağıdaki özellikler kullanılabilir bir **ayarları** blok.

|  Özellik  |  Tür  |  Açıklama   |
|----------- |------- |--------------- |
| ActionAfterReboot| dize| Uygulama yapılandırması sırasında bir yeniden başlatmadan sonra ne olacağını belirtir. Olası değerler şunlardır: __"ContinueConfiguration"__ ve __"StopConfiguration"__. <ul><li> __ContinueConfiguration__: Geçerli yapılandırmayı makine yeniden başlatma işleminden sonra devam edin. Varsayılan değer budur.</li><li>__StopConfiguration__: Makine yeniden başlatıldıktan sonra geçerli yapılandırmasını durdurun.</li></ul>|
| AllowModuleOverwrite| bool| __$TRUE__ yeni yapılandırmalar çekme hizmetten indirilen hedef düğümde bulunan eski değiştirene izinleri olup olmadığını. Aksi halde $FALSE değerini alır.|
| CertificateID| dize| Bir yapılandırmada geçirilen kimlik bilgileri korumak için kullanılan sertifika parmak izi. Daha fazla bilgi için [Windows PowerShell Desired State Configuration kimlik bilgilerini güvenli hale getirmek istediğiniz](http://blogs.msdn.com/b/powershell/archive/2014/01/31/want-to-secure-credentials-in-windows-powershell-desired-state-configuration.aspx)? <br> __Not:__ bu Azure Automation DSC çekme hizmetini kullanarak, otomatik olarak yönetilir.|
| ConfigurationDownloadManagers| Cimınstance]| Kullanımdan kalktı. Kullanım __ConfigurationRepositoryWeb__ ve __ConfigurationRepositoryShare__ blokları, yapılandırma çekme tanımlamak için hizmet uç noktalarını.|
| ConfigurationID| dize| Geriye dönük uyumluluk eski çekme ile hizmet için sürümleri. Bir çekme hizmetinden almak için yapılandırma dosyasını tanımlayan bir GUID. Düğüm yapılandırmasının adı ConfigurationID.mof MOF adlandırılmışsa yapılandırmaları çekme hizmetini çeker.<br> __Not:__ Bu özelliği ayarlarsanız, düğüm ile bir çekme hizmetini kullanarak kaydetme __RegistrationKey__ çalışmıyor. Daha fazla bilgi için [yapılandırma adları ile çekme istemcisi ayarlama](../pull-server/pullClientConfigNames.md).|
| ConfigurationMode| dize | LCM gerçekten yapılandırmasını hedef düğümlere uygulanması hakkında belirtir. Olası değerler __"ApplyOnly"__,__"ApplyAndMonitor"__, ve __"ApplyAndAutoCorrect"__. <ul><li>__ApplyOnly__: DSC yapılandırmasını uygular ve yeni bir yapılandırma, hedef düğüme veya bir hizmetten yeni yapılandırma çekildiğinde gönderildiğinde sürece başka hiçbir şey yapmaz. Yeni yapılandırma ilk uygulamadan sonra önceden yapılandırılmış bir durumdan kayması için DSC denetlemez. DSC yapılandırması önce başarılı oluncaya kadar uygulamayı deneyecek Not __ApplyOnly__ etkinleşir. </li><li> __ApplyAndMonitor__: Bu varsayılan değerdir. LCM herhangi bir yeni yapılandırmalar geçerlidir. Hedef düğüm istenen durumundan drifts sonra ilk uygulama yeni bir yapılandırma günlüklerini tutarsızlık DSC bildirir. DSC yapılandırması önce başarılı oluncaya kadar uygulamayı deneyecek Not __ApplyAndMonitor__ etkinleşir.</li><li>__ApplyAndAutoCorrect__: DSC, herhangi bir yeni yapılandırmalar geçerlidir. DSC hedef düğüm istenen durumundan drifts, ilk uygulama yeni bir yapılandırma sonrasında günlükleri tutarsızlık raporları ve sonra geçerli yapılandırmasını yeniden uygular.</li></ul>|
| ConfigurationModeFrequencyMins| UInt32| Sıklıkla, dakika cinsinden geçerli yapılandırmasını teslim uygulanan ve. İçin ApplyOnly ConfigurationMode özelliği ayarlanmışsa bu özellik yoksayılır. Varsayılan değer 15'tir.|
| DebugMode| dize| Olası değerler __hiçbiri__, __ForceModuleImport__, ve __tüm__. <ul><li>Kümesine __hiçbiri__ önbelleğe alınan kaynakları kullanmak için. Bu varsayılandır ve üretim senaryolarında kullanılmalıdır.</li><li>Ayarını __ForceModuleImport__, daha önce yüklenen ve önbelleğe alınmış olsa bile DSC kaynak modüllerin yeniden yüklemek LCM neden olur. Her modülü kullanmak üzere yeniden gibi bu DSC işlemlerinin performansını etkiler. Genellikle bu değer bir kaynak hata ayıklama sırasında kullanacağınız</li><li>Bu sürümde, __tüm__ aynı __ForceModuleImport__</li></ul> |
| RebootNodeIfNeeded| bool| Bu ayar __$true__ otomatik olarak yeniden başlatma uygulandığından gerektiren bir yapılandırmadan sonra düğümü yeniden başlatma için. Aksi takdirde, düğüm gerektiren herhangi bir yapılandırma için el ile yeniden başlatmanız gerekir. Varsayılan değer __$false__. Bir yeniden başlatma koşulu DSC (örneğin, Windows Yükleyici) dışında bir şey tarafından geçirilmeden olduğunda bu ayarı kullanmak için bu ayarı ile birleştirerek [xPendingReboot](https://github.com/powershell/xpendingreboot) modülü.|
| RefreshMode| dize| LCM yapılandırmaları nasıl alacağına belirtir. Olası değerler şunlardır: __"Disabled"__, __"Gönderme"__, ve __"Pull"__. <ul><li>__Devre dışı bırakılmış__: DSC yapılandırmaları için bu düğümü devre dışı bırakıldı.</li><li> __Anında iletme__: Yapılandırmaları başlatılan çağırarak [Başlat-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet'i. Yapılandırma düğüme hemen uygulanır. Bu varsayılan değerdir.</li><li>__Çekme:__ Düğüm, yapılandırma çekme hizmetini veya SMB yolundan düzenli olarak denetlemek için yapılandırılır. Bu özellik ayarlanırsa __çekme__, HTTP (hizmet) veya SMB (paylaşım) yolu belirtmeniz gerekir bir __ConfigurationRepositoryWeb__ veya __ConfigurationRepositoryShare__ blok.</li></ul>|
| RefreshFrequencyMins| Uint32| LCM güncelleştirilmiş yapılandırmaları almak için bir çekme hizmetini denetleyen dakika cinsinden zaman aralığı. LCM çekme modunda yapılandırılmamışsa, bu değer yoksayılır. Varsayılan değer 30’dur.|
| ReportManagers| Cimınstance]| Kullanımdan kalktı. Kullanım __ReportServerWeb__ blokları göndermek için bir uç nokta için bir çekme hizmetini veri raporlama.|
| ResourceModuleManagers| Cimınstance]| Kullanımdan kalktı. Kullanım __ResourceRepositoryWeb__ ve __ResourceRepositoryShare__ blokları çekme tanımlamak için HTTP uç noktaları veya SMB yolları, sırasıyla hizmet.|
| PartialConfigurations| Cimınstance| Henüz uygulanmadı. Kullanmayın.|
| StatusRetentionTimeInDays | UInt32| Geçerli yapılandırma durumunu LCM tutar gün sayısı.|

## <a name="pull-service"></a>Çekme Hizmeti

LCM yapılandırma çekme hizmet uç noktaları aşağıdaki türde tanımlama destekler:

- **Yapılandırma sunucusu**: DSC yapılandırmaları için depo. Yapılandırma sunucusu kullanarak tanımladığınız **ConfigurationRepositoryWeb** (web tabanlı sunucular için) ve **ConfigurationRepositoryShare** (için SMB tabanlı sunucular) engeller.
- **Kaynak sunucuda**: DSC kaynakları, PowerShell modülleri olarak paketlenmiş bir deposu. Kaynak sunucuları kullanarak tanımladığınız **ResourceRepositoryWeb** (web tabanlı sunucular için) ve **ResourceRepositoryShare** (için SMB tabanlı sunucular) engeller.
- **Rapor sunucusu**: DSC rapor verileri gönderir. bir hizmet. Rapor sunucuları kullanarak tanımladığınız **ReportServerWeb** engeller. Rapor sunucusu web hizmeti olması gerekir.

Çekme hizmetini hakkında daha fazla ayrıntı görmek için [Desired State Configuration çekme hizmetini](../pull-server/pullServer.md).

## <a name="configuration-server-blocks"></a>Yapılandırma sunucusu blokları

Web tabanlı yapılandırma sunucusunu tanımlamak için oluşturduğunuz bir **ConfigurationRepositoryWeb** blok.
A **ConfigurationRepositoryWeb** aşağıdaki özellikleri tanımlar.

|Özellik|Tür|Açıklama|
|---|---|---|
|AllowUnsecureConnection|bool|Kümesine **$TRUE** sunucu kimlik doğrulaması olmadan düğümünden bağlantılara izin vermek için. Kümesine **$FALSE** kimlik doğrulaması isteme.|
|CertificateID|dize|Sunucuya kimlik doğrulaması için kullanılan sertifika parmak izi.|
|ConfigurationNames|String]|Hedef düğüm tarafından çekilmesi yapılandırmaların adlarının dizisi. Yalnızca düğüm ile çekme hizmetini kullanarak kayıtlı değilse bu kullanılan bir **RegistrationKey**. Daha fazla bilgi için [yapılandırma adları ile çekme istemcisi ayarlama](../pull-server/pullClientConfigNames.md).|
|RegistrationKey|dize|Düğüm çekme hizmetine kaydeder. bir GUID. Daha fazla bilgi için [yapılandırma adları ile çekme istemcisi ayarlama](../pull-server/pullClientConfigNames.md).|
|ServerURL|dize|Yapılandırma hizmeti URL'si.|

Şirket içi düğümler için kullanılabilir - ConfigurationRepositoryWeb değeri yapılandırma basitleştirmek için bir örnek betiği bkz [oluşturma DSC metaconfigurations](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations)

Bir SMB tabanlı yapılandırma sunucusunu tanımlamak için oluşturduğunuz bir **ConfigurationRepositoryShare** blok.
A **ConfigurationRepositoryShare** aşağıdaki özellikleri tanımlar.

|Özellik|Tür|Açıklama|
|---|---|---|
|Kimlik bilgisi|MSFT_Credential|SMB paylaşımı kimliğini doğrulamak için kullanılan kimlik bilgileri.|
|Kaynak yolu|dize|SMB paylaşımı yolu.|

## <a name="resource-server-blocks"></a>Kaynak sunucu blokları

Bir web tabanlı bir kaynak sunucusunu tanımlamak için oluşturduğunuz bir **ResourceRepositoryWeb** blok.
A **ResourceRepositoryWeb** aşağıdaki özellikleri tanımlar.

|Özellik|Tür|Açıklama|
|---|---|---|
|AllowUnsecureConnection|bool|Kümesine **$TRUE** sunucu kimlik doğrulaması olmadan düğümünden bağlantılara izin vermek için. Kümesine **$FALSE** kimlik doğrulaması isteme.|
|CertificateID|dize|Sunucuya kimlik doğrulaması için kullanılan sertifika parmak izi.|
|RegistrationKey|dize|Çekme hizmetini düğüme tanımlayan bir GUID.|
|ServerURL|dize|Yapılandırma sunucusu URL'si.|

Şirket içi düğümler için kullanılabilir - ResourceRepositoryWeb değeri yapılandırma basitleştirmek için bir örnek betiği bkz [oluşturma DSC metaconfigurations](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations)

Bir SMB tabanlı kaynak sunucusunu tanımlamak için oluşturduğunuz bir **ResourceRepositoryShare** blok.
**ResourceRepositoryShare** aşağıdaki özellikleri tanımlar.

|Özellik|Tür|Açıklama|
|---|---|---|
|Kimlik bilgisi|MSFT_Credential|SMB paylaşımı kimliğini doğrulamak için kullanılan kimlik bilgileri. Kimlik bilgilerini geçirerek bir örnek için bkz [bir DSC SMB çekme sunucusu ayarlama](../pull-server/pullServerSMB.md)|
|Kaynak yolu|dize|SMB paylaşımı yolu.|

## <a name="report-server-blocks"></a>Rapor sunucusu blokları

Bir rapor sunucusunu tanımlamak için oluşturduğunuz bir **ReportServerWeb** blok.
Rapor sunucusu rolü, SMB tabanlı çekme hizmeti ile uyumlu değil.
**ReportServerWeb** aşağıdaki özellikleri tanımlar.

|Özellik|Tür|Açıklama|
|---|---|---|
|AllowUnsecureConnection|bool|Kümesine **$TRUE** sunucu kimlik doğrulaması olmadan düğümünden bağlantılara izin vermek için. Kümesine **$FALSE** kimlik doğrulaması isteme.|
|CertificateID|dize|Sunucuya kimlik doğrulaması için kullanılan sertifika parmak izi.|
|RegistrationKey|dize|Çekme hizmetini düğüme tanımlayan bir GUID.|
|ServerURL|dize|Yapılandırma sunucusu URL'si.|

Şirket içi düğümler için kullanılabilir - ReportServerWeb değeri yapılandırma basitleştirmek için bir örnek betiği bkz [oluşturma DSC metaconfigurations](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations)

## <a name="partial-configurations"></a>Kısmi yapılandırmalar

Kısmi bir yapılandırmasını tanımlamak için oluşturduğunuz bir **PartialConfiguration** blok.
Kısmi yapılandırmalar hakkında daha fazla bilgi için bkz: [DSC kısmi yapılandırmalar](../pull-server/partialConfigs.md).
**PartialConfiguration** aşağıdaki özellikleri tanımlar.

|Özellik|Tür|Açıklama|
|---|---|---|
|ConfigurationSource|String]|Yapılandırma sunucusu, daha önce tanımlanan bir ad dizisini **ConfigurationRepositoryWeb** ve **ConfigurationRepositoryShare** blokları, burada kısmi yapılandırma çekilmesini öğesinden.|
|DependsOn|dize{}|Bu kısmi yapılandırma uygulanmadan önce tamamlanması gereken diğer yapılandırmaları adları listesi.|
|Açıklama|dize|Kısmi yapılandırmasını tanımlamak için kullanılan metin.|
|ExclusiveResources|String]|Kaynaklar için kısmi bu yapılandırma özel bir dizi.|
|RefreshMode|dize|LCM kısmi yapılandırmanın nasıl alacağına belirtir. Olası değerler şunlardır: __"Disabled"__, __"Gönderme"__, ve __"Pull"__. <ul><li>__Devre dışı bırakılmış__: Kısmi bu yapılandırmayı devre dışı bırakıldı.</li><li> __Anında iletme__: Kısmi yapılandırma düğüme çağırarak gönderildiğinde [Yayımla-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet'i. Düğüm için tüm kısmi yapılandırmalar gönderilen veya bir hizmetten oluşan bir derleme sonra yapılandırmayı çağırarak başlatılabilir `Start-DscConfiguration –UseExisting`. Bu varsayılan değerdir.</li><li>__Çekme:__ Düğüm, bir çekme hizmetini kısmi yapılandırmasından düzenli olarak denetlemek için yapılandırılır. Bu özellik ayarlanırsa __çekme__, çekme hizmetinde belirtmelisiniz bir __ConfigurationSource__ özelliği. Azure Otomasyonu çekme hizmeti hakkında daha fazla bilgi için bkz. [Azure Automation DSC genel bakış](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview).</li></ul>|
|ResourceModuleSource|String]|Kaynak sunucuları kısmi bu yapılandırma için gerekli kaynakları indirileceği adları dizisi. Bu adlar, önceden tanımlı bir hizmet uç noktalarına başvurması gerekir **ResourceRepositoryWeb** ve **ResourceRepositoryShare** engeller.|

__Not:__ kısmi yapılandırmaları Azure Automation DSC ile desteklenir, ancak yalnızca bir yapılandırma, düğüm başına her Otomasyon hesabından istenebilecek.

## <a name="see-also"></a>Ayrıca bkz:

### <a name="concepts"></a>Kavramlar
[Desired State Configuration ' ne genel bakış](../overview/overview.md)

[Azure Otomasyonu DSC ile çalışmaya başlama](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-getting-started)

### <a name="other-resources"></a>Diğer Kaynaklar

[Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager)

[Yapılandırma adları ile çekme istemcisi ayarlama](../pull-server/pullClientConfigNames.md)
