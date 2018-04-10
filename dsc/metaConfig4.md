---
ms.date: 10/12/2017
ms.topic: conceptual
keywords: DSC, powershell, yapılandırma, Kur
title: Windows PowerShell önceki sürümlerinde yerel Yapılandırma Yöneticisi'ni yapılandırma
ms.openlocfilehash: f347f93ac36dac44ed70c89ee49917c2c2d75737
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="configuring-the-local-configuration-manager-in-previous-versions-of-windows-powershell"></a>Windows PowerShell önceki sürümlerinde yerel Yapılandırma Yöneticisi'ni yapılandırma

>İçin geçerlidir: Windows PowerShell 4.0

**Windows PowerShell 5.0 ve daha sonra ilgili bilgi için bkz: [yerel Configuration Manager Yapılandırma](metaConfig.md).**

Yerel Configuration Manager, Windows PowerShell istenen durum yapılandırması (DSC) altyapısıdır.
Tüm hedef düğümler üzerinde çalışır ve bir DSC yapılandırma komut dosyasında yer alan yapılandırma kaynakları çağırmak için sorumludur.
Bu konu, yerel Configuration Manager özellikleri listeler ve bir hedef düğümde yerel Configuration Manager ayarları nasıl değiştirileceği açıklanır.

## <a name="local-configuration-manager-properties"></a>Yerel Configuration Manager özellikleri

Ayarlama veya almak yerel Configuration Manager özellikleri listeler.

- **AllowModuleOverwrite**: denetimleri için yapılandırma Hizmeti'nden olup indirilen yeni yapılandırmaların hedef düğümde bulunan eski olanları üzerine izin verilir. Olası değerler True ve False.
- **CertificateID**: kimlik bilgilerini güvenli hale getirmek için kullanılan bir sertifikanın parmak izini geçirilen bir yapılandırmada. Daha fazla bilgi için bkz: [Windows PowerShell istenen durum Yapılandırması'te kimlik bilgilerini güvenlik altına almak istiyorsunuz?](http://blogs.msdn.com/b/powershell/archive/2014/01/31/want-to-secure-credentials-in-windows-powershell-desired-state-configuration.aspx).
- **ConfigurationID**: bir çekme hizmetinden bir özel yapılandırma dosyası almak için kullanılan bir GUID gösterir. GUID doğru yapılandırma dosyasının erişilir sağlar.
- **ConfigurationMode**: nasıl yerel Configuration Manager gerçekte yapılandırması için hedef düğümleri geçerlidir belirtir. Aşağıdaki değerleri alabilir:
  - **ApplyOnly**: Bu seçenek DSC yapılandırmasını uygular ve yeni bir yapılandırma algılandı sürece, başka hiçbir şey yapmaz ya da, yeni bir yapılandırma doğrudan hedef düğüme gönderme veya bir çekme hizmet ve DSC bağlanıyorsanız çekme hizmetiyle denetlediğinde, yeni bir yapılandırma bulur. Hedef düğümün yapılandırma drifts, hiçbir işlem yapılmadı.
  - **ApplyAndMonitor**: (varsayılan değer olan) bu seçeneği, DSC doğrudan hedef düğüme tarafından gönderdiğiniz ya da bir çekme hizmetinde bulunan tüm yeni yapılandırmaları uygular. Yapılandırma dosyasından hedef düğüm yapılandırmasını drifts, bundan sonra DSC günlükleri tutarsızlık bildirir. DSC günlüğü hakkında daha fazla bilgi için bkz: [istenen durum yapılandırması hataları tanılamak için olay günlüklerini kullanarak](http://blogs.msdn.com/b/powershell/archive/2014/01/03/using-event-logs-to-diagnose-errors-in-desired-state-configuration.aspx).
  - **ApplyAndAutoCorrect**: Bu seçenek ile doğrudan hedef düğüme tarafından gönderdiğiniz ya da bir çekme hizmetinde bulunan DSC yeni tüm yapılandırmaları uygular. Bundan sonra yapılandırma dosyasından hedef düğüm yapılandırmasını drifts, DSC günlükleri tutarsızlık raporları ve yapılandırma dosyası uyumlu hale getirmek için hedef düğüm yapılandırması ayarlamak dener.
- **ConfigurationModeFrequencyMins**: hangi girişimlerinin arka planda DSC geçerli yapılandırmasını hedef düğümde uygulamak ne sıklıkta (dakika cinsinden) temsil eder. Varsayılan değer 15'tir. Bu değer RefreshMode birlikte ayarlayabilirsiniz. RefreshMode ÇEKME olarak ayarlandığında, hedef düğüm yapılandırması RefreshFrequencyMins tarafından ayarlanmış bir aralıkta bağlantı kurar ve geçerli yapılandırma indirir. RefreshMode değerini bakılmaksızın ConfigurationModeFrequencyMins tarafından ayarlanmış aralıklarla hedef düğüme indirilen en son yapılandırma tutarlılık altyapısı uygular. RefreshFrequencyMins bir tamsayı olarak ayarlanmalıdır ConfigurationModeFrequencyMins katları.
- **Kimlik bilgisi**: (Get-Credential gibi ile) kimlik bilgileri gösterir yapılandırma hizmetiyle iletişim kurma gibi uzak kaynaklara erişmek için gerekli.
- **DownloadManagerCustomData**: indirme Yöneticisi belirli özel veri içeren bir dizi temsil eder.
- **DownloadManagerName**: yapılandırma ve modül indirme Yöneticisi adını gösterir.
- **RebootNodeIfNeeded**: hedef düğüm üzerinde bazı yapılandırma değişikliklerinin bu değişikliklerin uygulanması için yeniden başlatılmasını gerektirebilir. Değerine sahip **doğru**, yapılandırma bırakıldı hemen sonra bu özellik düğüm yeniden başlatılacak tamamen uygular, daha fazla uyarı olmadan. Varsa **False** (varsayılan değer) yapılandırması tamamlandı, ancak düğüm değişikliklerin etkili olması için el ile yeniden başlatılması gerekir.
- **RefreshFrequencyMins**: bir çekme hizmet ayarladığınızda kullanılır. Ne sıklıkta (dakika cinsinden), yerel Configuration Manager geçerli yapılandırmasını indirmek için bir çekme hizmet iletişim kuracağını temsil eder. Bu değer ConfigurationModeFrequencyMins birlikte ayarlayabilirsiniz. RefreshMode ÇEKME olarak ayarlandığında, hedef düğüm çekme RefreshFrequencyMins tarafından ayarlanmış bir aralıkta bağlantı kurar ve geçerli yapılandırma indirir. ConfigurationModeFrequencyMins tarafından ayarlanmış aralıklarla tutarlılık altyapısı sonra hedef düğüme indirilen son yapılandırmasını uygular. RefreshFrequencyMins tamsayıya ayarlanmamışsa ConfigurationModeFrequencyMins, sistem çarpıma yuvarlar,. Varsayılan değer 30’dur.
- **RefreshMode**: olası değerler şunlardır: **anında** (varsayılan) ve **çekme**. "Gönderme temelli" yapılandırmasında herhangi bir istemci bilgisayar kullanarak bir yapılandırma dosyası, her hedef düğümde yerleştirmeniz gerekir. "Çekme" modunda, bir çekme hizmeti için yerel yapılandırma başvurun ve yapılandırma dosyalarına erişmek için Yöneticisi ayarlamanız gerekir.

### <a name="example-of-updating-local-configuration-manager-settings"></a>Örneği, yerel Configuration Manager ayarları güncelleştiriliyor

Ekleyerek bir hedef düğümü yerel Configuration Manager ayarlarını güncelleştirebilirsiniz bir **LocalConfigurationManager** engelleme bir yapılandırma betiğini düğümü bloğunda içinde aşağıdaki örnekte gösterildiği gibi.

```powershell
Configuration ExampleConfig
{
    Node “Server001”
    {
        LocalConfigurationManager
        {
            ConfigurationID = "646e48cb-3082-4a12-9fd9-f71b9a562d4e"
            ConfigurationModeFrequencyMins = 45
            ConfigurationMode = "ApplyAndAutocorrect"
            RefreshMode = "Pull"
            RefreshFrequencyMins = 90
            DownloadManagerName = "WebDownloadManager"
            DownloadManagerCustomData = (@{ServerUrl="https://$PullService/psdscpullserver.svc"})
            CertificateID = "71AA68562316FE3F73536F1096B85D66289ED60E"
            Credential = $cred
            RebootNodeIfNeeded = $true
            AllowModuleOverwrite = $false
        }
# One or more resource blocks can be added here
    }
}

# The following line invokes the configuration and creates a file called Server001.meta.mof at the specified path
ExampleConfig -OutputPath "c:\users\public\dsc"
```

Önceki örnekte betik çalıştıran belirtir ve istenen ayarları depolayan bir MOF dosyası oluşturur.
Ayarları uygulamak için kullanabileceğiniz **kümesi DscLocalConfigurationManager** aşağıdaki örnekte gösterildiği gibi cmdlet'i.

```powershell
Set-DscLocalConfigurationManager -Path "c:\users\public\dsc"
```

> **Not**: için **yolu** parametresi için belirtilen aynı yol belirtmelisiniz **OutputPath** yapılandırmanın önceki örnekte çağrıldığında parametresi.

Geçerli yerel Configuration Manager ayarları görüntülemek için kullanabileceğiniz **Get-DscLocalConfigurationManager** cmdlet'i.
Varsayılan olarak bu cmdlet herhangi bir parametre ile çağırma olursa, üzerinde çalıştırdığınız düğüm için yerel Configuration Manager ayarlarını alır.
Başka bir düğüme belirtmek için kullanın **CimSession** Bu cmdlet'i parametre.