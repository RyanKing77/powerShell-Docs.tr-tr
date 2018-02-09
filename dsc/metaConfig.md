---
ms.date: 2017-10-11
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "Yerel Yapılandırma Yöneticisi'ni yapılandırma"
ms.openlocfilehash: b8e0749cf2f67e395e9fd8eaf9cde33b97c0cb67
ms.sourcegitcommit: 755d7bc0740573d73613cedcf79981ca3dc81c5e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2018
---
# <a name="configuring-the-local-configuration-manager"></a>Yerel Yapılandırma Yöneticisi'ni yapılandırma

> İçin geçerlidir: Windows PowerShell 5.0

Yerel Configuration Manager (LCM'yi) İstenen durum yapılandırması (DSC) altyapısıdır.
LCM'yi her hedef düğüm üzerinde çalışır ve ayrıştırma ve düğüme gönderilen yapılandırmaları ederek ilerlemesini kabul ederek sorumludur.
DSC, aşağıdakiler de dahil olmak üzere diğer yönlerini sayısı için sorumlu değildir.

- Yenileme modu (iterek ister çekerek) belirleme.
- Sıklıkla bir düğüm çeker ve yapılandırmaları enacts belirtme.
- Düğüm çekme hizmeti ile ilişkilendirme.
- Kısmi yapılandırmaları belirtme.

Bu davranışların her biri belirtmek için LCM'yi yapılandırmak için yapılandırma özel bir tür kullanın.
Aşağıdaki bölümlerde LCM'yi yapılandırma açıklanmaktadır.

Windows PowerShell 5.0, yerel Configuration Manager'ı yönetmek için yeni ayarları kullanıma sunuldu.
Windows PowerShell 4. 0 ' LCM'yi yapılandırma hakkında daha fazla bilgi için bkz: [önceki sürümleri, Windows PowerShell'de yerel Configuration Manager Yapılandırma](metaconfig4.md).

## <a name="writing-and-enacting-an-lcm-configuration"></a>Yazma ve LCM'yi yapılandırma ederek ilerlemesini kabul ederek

LCM'yi yapılandırmak için oluşturma ve özel türde bir LCM'yi ayarlarını uygulayan yapılandırma çalıştırın.
Bir LCM'yi yapılandırmasını belirtmek için DscLocalConfigurationManager özniteliğini kullanın.
Aşağıdaki anında iletme moduna LCM'yi ayarlar basit bir yapılandırma gösterir.

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

İçin LCM'yi ayarlarının uygulanması işleminin DSC yapılandırması uygulayarak benzer.
LCM'yi yapılandırma oluşturma MOF dosyasına derlemek ve düğümü için geçerli.
DSC yapılandırmaları, bir LCM'yi yapılandırma çağırarak yürürlüğe değil [başlangıç DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet'i.
Bunun yerine, çağırmanız [kümesi DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621.aspx), bir parametre olarak MOF LCM'yi yapılandırma yoluna sağlama.
LCM'yi yapılandırma yürürlüğe sonra çağırarak LCM'yi özelliklerini görebilirsiniz [Get-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx) cmdlet'i.

Bir LCM'yi yapılandırma yalnızca sınırlı bir kaynak kümesi için blok içerebilir.
Önceki örnekte, adında yalnızca kaynaktır **ayarları**.
Diğer kullanılabilir kaynaklar şunlardır:

* **ConfigurationRepositoryWeb**: yapılandırmaları için bir HTTP istek hizmeti belirtir.
* **ConfigurationRepositoryShare**: bir SMB paylaşımı yapılandırmaları için belirtir.
* **ResourceRepositoryWeb**: modülleri için bir HTTP istek hizmeti belirtir.
* **ResourceRepositoryShare**: bir SMB paylaşımı modülleri için belirtir.
* **ReportServerWeb**: raporları gönderildiği bir HTTP istek hizmeti belirtir.
* **PartialConfiguration**: Kısmi yapılandırmaları etkinleştirmek için veri sağlar.

## <a name="basic-settings"></a>Temel ayarlar

Çekme hizmet uç noktaları/yolları ve kısmi yapılandırmaları belirtme dışındaki tüm LCM'yi özelliklerinin yapılandırılan bir **ayarları** bloğu.
Aşağıdaki özellikler kullanılabilir olan bir **ayarları** bloğu.

|  Özellik  |  Tür  |  Açıklama   |
|----------- |------- |--------------- |
| ActionAfterReboot| dize| Bir yeniden başlatmadan sonra bir yapılandırma uygulanması sırasında neler belirtir. Olası değerler şunlardır: __"ContinueConfiguration"__ ve __"StopConfiguration"__. <ul><li> __ContinueConfiguration__: Makine yeniden başlatıldıktan sonra geçerli yapılandırmayı uygulama devam edin. Bu varsayılan değerdir</li><li>__StopConfiguration__: Makine yeniden başlatıldıktan sonra geçerli yapılandırmasını durdurun.</li></ul>|
| AllowModuleOverwrite| bool| __$TRUE__ çekme hizmetten indirilen yeni yapılandırmaların hedef düğümde bulunan eski olanları üzerine yazmak için izinleri olup olmadığını. Aksi takdirde $FALSE.|
| CertificateID| dize| Kimlik bilgilerinin güvenliğini sağlamak için kullanılan bir sertifikanın parmak izini bir yapılandırmada geçirildi. Daha fazla bilgi için bkz: [Windows PowerShell istenen durum Yapılandırması'te kimlik bilgilerini güvenli hale getirmek istediğiniz](http://blogs.msdn.com/b/powershell/archive/2014/01/31/want-to-secure-credentials-in-windows-powershell-desired-state-configuration.aspx)? <br> __Not:__ bu Azure Automation DSC çekme hizmeti kullanıyorsanız otomatik olarak yönetilir.|
| ConfigurationDownloadManagers| CimInstance[]| Kullanımdan kalktı. Kullanım __ConfigurationRepositoryWeb__ ve __ConfigurationRepositoryShare__ yapılandırma çekme tanımlamak için blokları hizmet uç noktaları.|
| ConfigurationID| dize| Geriye dönük uyumluluk eski çekme ile hizmet için sürümleri. Bir çekme hizmetinden almak için yapılandırma dosyasını tanımlayan bir GUID. Düğüm yapılandırmasının adı MOF olarak adlandırılmışsa ConfigurationID.mof yapılandırmaları çekme hizmette çeker.<br> __Not:__ bu özelliği ayarlarsanız, düğüm çekme hizmeti ile kullanarak kaydetme __RegistrationKey__ çalışmıyor. Daha fazla bilgi için bkz: [yapılandırmasına sahip bir çekme istemcisi ayarlama](pullClientConfigNames.md).|
| ConfigurationMode| dize | Nasıl LCM'yi gerçekten yapılandırması için hedef düğümleri geçerlidir belirtir. Olası değerler şunlardır: __"ApplyOnly"__,__"ApplyAndMonitor"__, ve __"ApplyAndAutoCorrect"__. <ul><li>__ApplyOnly__: DSC yapılandırmasını uygular ve yeni bir yapılandırma hedef düğüme veya yeni bir yapılandırma bir hizmetinden çekilir itildiği sürece başka hiçbir şey yapmaz. Yeni yapılandırma ilk uygulamadan sonra DSC önceden yapılandırılmış bir durumdan kayması kontrol etmez. Önce başarılı olana kadar yapılandırmayı uygulamak DSC deneyecek Not __ApplyOnly__ etkisi alır. </li><li> __ApplyAndMonitor__: Bu varsayılan değerdir. LCM'yi yeni tüm yapılandırmalar için geçerlidir. Hedef düğüm istenen durumundan drifts yeni yapılandırma ilk uygulamadan sonra günlükleri tutarsızlık DSC bildirir. Önce başarılı olana kadar yapılandırmayı uygulamak DSC deneyecek Not __ApplyAndMonitor__ etkisi alır.</li><li>__ApplyAndAutoCorrect__: DSC tüm yeni yapılandırmaları uygular. DSC hedef düğüm istenen durumundan drifts, yeni yapılandırma ilk uygulamadan sonra günlükleri tutarsızlık raporları ve geçerli yapılandırma yeniden uygular.</li></ul>|
| ConfigurationModeFrequencyMins| UInt32| Sıklıkla, dakika cinsinden geçerli yapılandırmasını teslim uygulanan ve. ConfigurationMode özelliği için ApplyOnly ayarlanmışsa, bu özellik yoksayılır. Varsayılan değer 15'tir.|
| DebugMode| dize| Olası değerler şunlardır: __hiçbiri__, __ForceModuleImport__, ve __tüm__. <ul><li>Kümesine __hiçbiri__ önbelleğe alınmış kaynakları kullanmak için. Bu varsayılandır ve üretim senaryolarında kullanılmalıdır.</li><li>Ayarını __ForceModuleImport__, daha önce yüklenen ve önbelleğe alınmış olsa bile herhangi bir DSC kaynağı modül yeniden yüklemek LCM'yi neden olur. Her modülü kullanmak üzere yeniden gibi bu DSC işlemlerinin performansını etkiler. Kaynak hata ayıklama sırasında bu değer genellikle kullanırsınız</li><li>Bu sürümde, __tüm__ aynı __ForceModuleImport__</li></ul> |
| RebootNodeIfNeeded| bool| Bu ayar __$true__ otomatik olarak yeniden başlatma uygulandığından gerektiren bir yapılandırma sonra düğümü yeniden başlatma için. Aksi takdirde, el ile düğümü gerektirdiği herhangi bir yapılandırma için yeniden başlatma gerekir. Varsayılan değer __$false__. Bir yeniden başlatma koşulu DSC (örneğin, Windows Installer) dışında bir şey tarafından geçirilmeden olduğunda bu ayarı kullanmak için bu ayar ile birleştirerek [xPendingReboot](https://github.com/powershell/xpendingreboot) modülü.|
| RefreshMode| dize| Nasıl LCM'yi yapılandırmalarını alır belirtir. Olası değerler şunlardır: __"Disabled"__, __"Gönderme"__, ve __"Çekme"__. <ul><li>__Devre dışı__: Bu düğümün DSC yapılandırmaları devre dışı.</li><li> __Anında__: yapılandırmaları başlatılan çağırarak [başlangıç DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet'i. Yapılandırma düğüme hemen uygulanır. Bu varsayılan değerdir.</li><li>__Çekme:__ düğüm yapılandırmaları çekme hizmeti veya SMB yolundan düzenli olarak denetlemek için yapılandırılmış. Bu özellik ayarlanmışsa __çekme__, HTTP (hizmeti) veya SMB (paylaşım) yolunda belirtmelisiniz bir __ConfigurationRepositoryWeb__ veya __ConfigurationRepositoryShare__ bloğu.</li></ul>|
| RefreshFrequencyMins| Uint32| Zaman aralığını dakika cinsinden en LCM'yi güncelleştirilmiş yapılandırmalarını almak için bir çekme hizmeti denetler. LCM'yi çekme modunda yapılandırılmamışsa, bu değer yoksayılır. Varsayılan değer 30’dur.|
| ReportManagers| CimInstance[]| Kullanımdan kalktı. Kullanım __ReportServerWeb__ blokları göndermek için bir uç nokta tanımlamak için bir çekme hizmetine veri raporlama.|
| ResourceModuleManagers| CimInstance[]| Kullanımdan kalktı. Kullanım __ResourceRepositoryWeb__ ve __ResourceRepositoryShare__ blokları çekme tanımlamak için HTTP uç noktaları veya SMB yolları, sırasıyla hizmet.|
| PartialConfigurations| CimInstance| Henüz uygulanmadı. Kullanmayın.|
| StatusRetentionTimeInDays | UInt32| Geçerli yapılandırma durumunu LCM'yi tutar gün sayısı.|

## <a name="pull-service"></a>Çekme Hizmeti

LCM'yi yapılandırma çekme hizmet uç noktaları aşağıdaki türlerini tanımlama destekler:

- **Yapılandırma sunucusu**: DSC yapılandırmaları için depo. Kullanarak yapılandırma sunucularına tanımlayın **ConfigurationRepositoryWeb** (için web tabanlı sunucular) ve **ConfigurationRepositoryShare** (için SMB tabanlı sunucular) engeller.
- **Kaynak sunucuda**: PowerShell modülleri paketlenmiş DSC kaynakları için depo. Kaynak sunucuları kullanarak tanımlayın **ResourceRepositoryWeb** (için web tabanlı sunucular) ve **ResourceRepositoryShare** (için SMB tabanlı sunucular) engeller.
- **Rapor sunucusu**: DSC rapor veri gönderen bir hizmet. Rapor sunucusu kullanarak tanımlayın **ReportServerWeb** engeller. Bir rapor sunucusu web hizmeti olması gerekir.

Çekme hizmeti hakkında daha fazla ayrıntı görmek için [istenen durum yapılandırması çekme hizmeti](pullServer.md).

## <a name="configuration-server-blocks"></a>Yapılandırma sunucusu blokları

Bir web tabanlı yapılandırma sunucusu tanımlamak için oluşturduğunuz bir **ConfigurationRepositoryWeb** bloğu.
A **ConfigurationRepositoryWeb** aşağıdaki özellikleri tanımlar.

|Özellik|Tür|Açıklama|
|---|---|---|
|AllowUnsecureConnection|bool|Kümesine **$TRUE** kimlik doğrulaması olmadan sunucu düğümünden bağlantılara izin vermek için. Kümesine **$FALSE** kimlik doğrulaması istemek için.|
|CertificateID|dize|Sunucuya kimlik doğrulaması için kullanılan bir sertifika parmak izi.|
|ConfigurationNames|String[]|Hedef düğüm tarafından alınmasını yapılandırmaları adlarının dizisini. Yalnızca düğüm çekme hizmetiyle kullanarak kayıtlı değilse bu kullanılan bir **RegistrationKey**. Daha fazla bilgi için bkz: [yapılandırmasına sahip bir çekme istemcisi ayarlama](pullClientConfigNames.md).|
|RegistrationKey|dize|Düğüm çekme hizmetine kaydolur GUID. Daha fazla bilgi için bkz: [yapılandırmasına sahip bir çekme istemcisi ayarlama](pullClientConfigNames.md).|
|ServerURL|dize|Yapılandırma hizmeti URL'si.|

Şirket içi düğümler için kullanılabilir - ConfigurationRepositoryWeb değerini yapılandırma basitleştirmek için bir örnek komut dosyası bkz [oluşturma DSC metaconfigurations](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations)

Bir SMB tabanlı yapılandırma sunucusu tanımlamak için oluşturduğunuz bir **ConfigurationRepositoryShare** bloğu.
A **ConfigurationRepositoryShare** aşağıdaki özellikleri tanımlar.

|Özellik|Tür|Açıklama|
|---|---|---|
|kimlik bilgisi|MSFT_Credential|SMB paylaşımı kimliğini doğrulamak için kullanılan kimlik bilgileri.|
|Kaynak yolu|dize|SMB paylaşım yolu.|

## <a name="resource-server-blocks"></a>Kaynak sunucu blokları

Bir web tabanlı kaynak sunucusu tanımlamak için oluşturduğunuz bir **ResourceRepositoryWeb** bloğu.
A **ResourceRepositoryWeb** aşağıdaki özellikleri tanımlar.

|Özellik|Tür|Açıklama|
|---|---|---|
|AllowUnsecureConnection|bool|Kümesine **$TRUE** kimlik doğrulaması olmadan sunucu düğümünden bağlantılara izin vermek için. Kümesine **$FALSE** kimlik doğrulaması istemek için.|
|CertificateID|dize|Sunucuya kimlik doğrulaması için kullanılan bir sertifika parmak izi.|
|RegistrationKey|dize|Çekme hizmet düğüme tanımlayan bir GUID.|
|ServerURL|dize|Yapılandırma sunucusu URL'si.|

Şirket içi düğümler için kullanılabilir - ResourceRepositoryWeb değerini yapılandırma basitleştirmek için bir örnek komut dosyası bkz [oluşturma DSC metaconfigurations](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations)

Bir SMB tabanlı kaynak sunucusu tanımlamak için oluşturduğunuz bir **ResourceRepositoryShare** bloğu.
**ResourceRepositoryShare** aşağıdaki özellikleri tanımlar.

|Özellik|Tür|Açıklama|
|---|---|---|
|kimlik bilgisi|MSFT_Credential|SMB paylaşımı kimliğini doğrulamak için kullanılan kimlik bilgileri. Örneği geçirme kimlik bilgileri için bkz: [DSC SMB çekme sunucusu kurma](pullServerSMB.md)|
|Kaynak yolu|dize|SMB paylaşım yolu.|

## <a name="report-server-blocks"></a>Rapor sunucusu blokları

Bir rapor sunucusu tanımlamak için oluşturduğunuz bir **ReportServerWeb** bloğu.
Rapor sunucusu rolü tabanlı SMB çekme hizmeti ile uyumlu değil.
**ReportServerWeb** aşağıdaki özellikleri tanımlar.

|Özellik|Tür|Açıklama|
|---|---|---|
|AllowUnsecureConnection|bool|Kümesine **$TRUE** kimlik doğrulaması olmadan sunucu düğümünden bağlantılara izin vermek için. Kümesine **$FALSE** kimlik doğrulaması istemek için.|
|CertificateID|dize|Sunucuya kimlik doğrulaması için kullanılan bir sertifika parmak izi.|
|RegistrationKey|dize|Çekme hizmet düğüme tanımlayan bir GUID.|
|ServerURL|dize|Yapılandırma sunucusu URL'si.|

Şirket içi düğümler için kullanılabilir - ReportServerWeb değerini yapılandırma basitleştirmek için bir örnek komut dosyası bkz [oluşturma DSC metaconfigurations](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations)

## <a name="partial-configurations"></a>Kısmi yapılandırmaları

Kısmi yapılandırmasını tanımlamak için oluşturduğunuz bir **PartialConfiguration** bloğu.
Kısmi yapılandırmaları hakkında daha fazla bilgi için bkz: [DSC kısmi yapılandırmaları](partialConfigs.md).
**PartialConfiguration** aşağıdaki özellikleri tanımlar.

|Özellik|Tür|Açıklama|
|---|---|---|
|ConfigurationSource|string[]|Bir dizi önceden tanımlanmış yapılandırma sunucularının adını **ConfigurationRepositoryWeb** ve **ConfigurationRepositoryShare** burada kısmi yapılandırma çekilmesini gelen blokları.|
|dependsOn|dize {}|Bu kısmi yapılandırma uygulanmadan önce tamamlanması gereken diğer yapılandırmaları adları listesi.|
|Açıklama|dize|Kısmi yapılandırmasını tanımlamak için kullanılan metin.|
|ExclusiveResources|string[]|Kaynakları kısmi bu yapılandırma için özel bir dizi.|
|RefreshMode|dize|Nasıl LCM'yi Bu kısmi yapılandırmasını alır belirtir. Olası değerler şunlardır: __"Disabled"__, __"Gönderme"__, ve __"Çekme"__. <ul><li>__Devre dışı__: Bu kısmi yapılandırması devre dışı bırakıldı.</li><li> __Anında__: Kısmi yapılandırması düğüme çağırarak itildiği [Yayımla DscConfiguration](https://technet.microsoft.com/en-us/library/mt517875.aspx) cmdlet'i. Düğüm için tüm kısmi yapılandırmaları gönderilir ya da bir hizmetinden çekilen sonra yapılandırma çağırarak başlatılabilir `Start-DscConfiguration –UseExisting`. Bu varsayılan değerdir.</li><li>__Çekme:__ düğümü düzenli olarak bir çekme hizmetinden kısmi yapılandırma denetlemek için yapılandırılmıştır. Bu özellik ayarlanmışsa __çekme__, çekme hizmetinde belirtmelisiniz bir __ConfigurationSource__ özelliği. Azure Otomasyonu çekme hizmeti hakkında daha fazla bilgi için bkz: [Azure Automation DSC genel bakış](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview).</li></ul>|
|ResourceModuleSource|string[]|Kısmi bu yapılandırma için gerekli kaynakları indirileceği kaynak sunucularının adları dizisi. Bu adları önceden tanımlanmış hizmet uç noktalarına başvurmalıdır **ResourceRepositoryWeb** ve **ResourceRepositoryShare** engeller.|

__Not:__ kısmi yapılandırmaları Azure Automation DSC'ye desteklenir, ancak yalnızca bir yapılandırma çekilen düğüm başına her automation hesabı.

## <a name="see-also"></a>Ayrıca bkz:

### <a name="concepts"></a>Kavramlar
[İstenen durum yapılandırması genel bakış](overview.md)

[Azure Otomasyonu DSC ile çalışmaya başlama](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-getting-started)

### <a name="other-resources"></a>Diğer Kaynaklar

[Set-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621.aspx)

[Bir çekme istemci yapılandırma adları ile ayarlama](pullClientConfigNames.md)
