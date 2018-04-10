---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, yapılandırma, Kur
title: Yapılandırma adlarını kullanarak çekme istemcisi ayarlama
ms.openlocfilehash: dd0526b118b404854b1e9b445ca50bdaafdd01c7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="setting-up-a-pull-client-using-configuration-names"></a>Yapılandırma adlarını kullanarak çekme istemcisi ayarlama

> İçin geçerlidir: Windows PowerShell 5.0

Çekme modunu kullanacak şekilde söylediyse ve yapılandırmaları almak için çekme sunucunun nerede ile bağlantı kurabildiğini URL verilen her hedef düğüme sahiptir.
Bunu yapmak için gerekli olan bilgileri yerel Configuration Manager (LCM'yi) yapılandırmanız gerekir.
Özel türde bir yapılandırma ile donatılmış, oluşturduğunuz LCM'yi yapılandırmak için **DSCLocalConfigurationManager** özniteliği.
LCM'yi yapılandırma hakkında daha fazla bilgi için bkz: [yerel Configuration Manager Yapılandırma](metaConfig.md).

> **Not**: Bu konu, PowerShell 5.0 için geçerlidir.
PowerShell 4.0 çekme istemcisinde ayarlama hakkında daha fazla bilgi için bkz: [PowerShell 4. 0 ' yapılandırması kimliği kullanan bir çekme istemci ayarlama](pullClientConfigID4.md)

Aşağıdaki komut dosyasını, "CONTOSO-PullSrv" adlı bir sunucudan çekme yapılandırmaları için LCM'yi yapılandırır:

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('ClientConfig')
        }
    }
}
PullClientConfigNames
```

Komut dosyasında **ConfigurationRepositoryWeb** blok çekme sunucunun tanımlar.
**ServerURL** özelliği, çekme sunucu için uç noktaya belirtir.

**RegistrationKey** çekme sunucusuna ilişkin tüm istemci düğümleri ve çekme sunucu arasında paylaşılan bir anahtar bir özelliktir.
Aynı değere çekme sunucusunda bir dosyada depolanır.

**ConfigurationNames** istemci düğümü için hedeflenen yapılandırmaları adını belirten bir dizi bir özelliktir.
Çekme sunucusunda yapılandırma MOF dosyası bu istemci düğüm adlı için *ConfigurationNames*.mof, burada *ConfigurationNames* değeri ile eşleşen **ConfigurationNames**  özelliği bu meta yapılandırmasını ayarlayın.

>**Not:** birden fazla değer belirtirseniz, **ConfigurationNames**, de belirtmeniz gerekir **PartialConfiguration** yapılandırmanızda engeller.
Kısmi yapılandırmaları hakkında daha fazla bilgi için bkz: [PowerShell istenen durum yapılandırması kısmi yapılandırmaları](partialConfigs.md).

Bu betik çalıştıktan sonra adlı yeni bir çıkış klasörü oluşturur **PullClientConfigNames** ve meta yapılandırmasını MOF dosyası var. yerleştirir.
Bu durumda, meta yapılandırmasını MOF dosyası adlandırılacağını `localhost.meta.mof`.

Yapılandırmayı uygulamak için arama **kümesi DscLocalConfigurationManager** cmdlet'i ile **yolu** meta yapılandırmasını MOF dosyasının konumunu ayarlayın.

```powershell
Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigNames –Verbose.
```

> **Not**: Kayıt anahtarlarını yalnızca web çekme sunucularıyla çalışır.
Hala kullanmalısınız **ConfigurationID** bir SMB çekme sunucusuyla.
Bir çekme sunucusuna kullanarak yapılandırma hakkında bilgi için **ConfigurationID**, bkz: [yapılandırma Kimliğini kullanarak bir çekme istemci ayarı](PullClientConfigNames.md)

## <a name="resource-and-report-servers"></a>Kaynak ve rapor sunucuları

Yalnızca belirtirseniz bir **ConfigurationRepositoryWeb** veya **ConfigurationRepositoryShare** (önceki örnektekiyle) LCM'yi yapılandırmanızda engellemek, çekme istemci kaynaklardan çeker Belirtilen sunucu, ancak raporları için göndermez.
Tek tanıtım sunucu yapılandırmaları, kaynaklar ve raporlama için kullanabilirsiniz, ancak oluşturmak zorunda bir **ReportRepositoryWeb** set up reporting bloğu.
Aşağıdaki örnek, bir istemciye çekme yapılandırmaları ve kaynakları ve veri, bir tek çekme sunucusuna raporlama Gönder ayarlar meta yapılandırmasını gösterir.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigNames
```

Kaynaklar ve raporlama için farklı çekme sunucuları da belirtebilirsiniz.
Kaynak sunucuyu belirtmek için ya da kullandığınız bir **ResourceRepositoryWeb** (bir web çekme sunucusu için) veya bir **ResourceRepositoryShare** bloğu (SMB çekme sunucusu için).
Bir rapor sunucusu belirtmek için kullandığınız bir **ReportRepositoryWeb** bloğu.
Bir rapor sunucusu bir SMB sunucusu olamaz.
Bir çekme istemci kendi yapılandırmalardan almak için şu meta yapılandırmasını yapılandırır **CONTOSO PullSrv** ve kaynaklarıyla **CONTOSO ResourceSrv**ve durum raporları göndermek için  **CONTOSO ReportSrv**:

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }

        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-ResourceSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '30ef9bd8-9acf-4e01-8374-4dc35710fc90'
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-ReportSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '6b392c6a-818c-4b24-bf38-47124f1e2f14'
        }
    }
}
PullClientConfigNames
```

## <a name="see-also"></a>Ayrıca bkz:

* [Bir çekme istemci yapılandırması kimliği ile ayarlama](PullClientConfigNames.md)
* [DSC çekme sunucusuna ayarlama](pullServer.md)