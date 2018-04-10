---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, yapılandırma, Kur
title: Yapılandırma kimliğini kullanarak çekme istemcisi ayarlama
ms.openlocfilehash: 93e533fd4e729e1af0124ad69ca7e384e1cb3aa4
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="setting-up-a-pull-client-using-configuration-id"></a>Yapılandırma kimliğini kullanarak çekme istemcisi ayarlama

> İçin geçerlidir: Windows PowerShell 5.0

Çekme modunu kullanacak şekilde söylediyse ve yapılandırmaları almak için çekme sunucunun nerede ile bağlantı kurabildiğini URL verilen her hedef düğüme sahiptir. Bunu yapmak için gerekli olan bilgileri yerel Configuration Manager (LCM'yi) yapılandırmanız gerekir. Özel türde bir yapılandırma ile donatılmış, oluşturduğunuz LCM'yi yapılandırmak için **DSCLocalConfigurationManager** özniteliği. LCM'yi yapılandırma hakkında daha fazla bilgi için bkz: [yerel Configuration Manager Yapılandırma](metaConfig.md).

> **Not**: Bu konu, PowerShell 5.0 için geçerlidir. PowerShell 4.0 çekme istemcisinde ayarlama hakkında daha fazla bilgi için bkz: [PowerShell 4. 0 ' yapılandırması kimliği kullanan bir çekme istemci ayarlama](pullClientConfigID4.md)

Aşağıdaki komut dosyası LCM'yi "CONTOSO-PullSrv" adlı bir sunucudan çekme yapılandırmaları için yapılandırır.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }
    }
}
PullClientConfigID
```

Komut dosyasında **ConfigurationRepositoryWeb** blok çekme sunucunun tanımlar. **ServerURL**

Bu betik çalıştıktan sonra adlı yeni bir çıkış klasörü oluşturur **PullClientConfigID** ve meta yapılandırmasını MOF dosyası var. yerleştirir. Bu durumda, meta yapılandırmasını MOF dosyası adlandırılacağını `localhost.meta.mof`.

Yapılandırmayı uygulamak için arama **kümesi DscLocalConfigurationManager** cmdlet'i ile **yolu** meta yapılandırmasını MOF dosyasının konumunu ayarlayın. Örneğin: `Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigID –Verbose.`

## <a name="configuration-id"></a>Yapılandırma Kimliği

Komut dosyası kümeleri **ConfigurationID** LCM'yi bu amaç için daha önce oluşturulmuş bir GUID özelliği (kullanarak bir GUID oluşturabilirsiniz **yeni GUID** cmdlet'i). **ConfigurationID** LCM'yi çekme sunucusunda uygun yapılandırma bulmak için kullanır. Çekme sunucusunda yapılandırma MOF dosyası olarak adlandırılmalıdır _ConfigurationID_.mof, burada _ConfigurationID_ değeri **ConfigurationID** hedef özelliği düğümün LCM'yi.

## <a name="smb-pull-server"></a>SMB çekme sunucusuna

Bir istemcinin bir SMB sunucusundan çekme yapılandırmaları ayarlamak için kullanın bir **ConfigurationRepositoryShare** bloğu. İçinde bir **ConfigurationRepositoryShare** bloğu ayarlayarak sunucu yolunu belirtin **KaynakYolu** özelliği. Adlı bir SMB çekme sunucusundan çıkarmak için hedef düğümü aşağıdaki meta yapılandırmasını yapılandırır **SMBPullServer**.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryShare SMBPullServer
        {
            SourcePath = '\\SMBPullServer\PullSource'

        }
    }
}
PullClientConfigID
```

## <a name="resource-and-report-servers"></a>Kaynak ve rapor sunucuları

Yalnızca belirtirseniz bir **ConfigurationRepositoryWeb** veya **ConfigurationRepositoryShare** (önceki örnektekiyle) LCM'yi yapılandırmanızda engellemek, çekme istemci kaynaklardan çeker Belirtilen sunucu, ancak raporları için göndermez. Tek tanıtım sunucu yapılandırmaları, kaynaklar ve raporlama için kullanabilirsiniz, ancak oluşturmak zorunda bir **ReportRepositoryWeb** set up reporting bloğu.

Aşağıdaki örnek, bir istemciye çekme yapılandırmaları ve kaynakları ve veri, bir tek çekme sunucusuna raporlama Gönder ayarlar meta yapılandırmasını gösterir.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }


        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

Kaynaklar ve raporlama için farklı çekme sunucuları da belirtebilirsiniz. Kaynak sunucuyu belirtmek için ya da kullandığınız bir **ResourceRepositoryWeb** (bir web çekme sunucusu için) veya bir **ResourceRepositoryShare** bloğu (SMB çekme sunucusu için).
Bir rapor sunucusu belirtmek için kullandığınız bir **ReportRepositoryWeb** bloğu. Bir rapor sunucusu bir SMB sunucusu olamaz.
Bir çekme istemci kendi yapılandırmalardan almak için şu meta yapılandırmasını yapılandırır **CONTOSO PullSrv** ve kaynaklarıyla **CONTOSO ResourceSrv**ve durum raporları göndermek için  **CONTOSO ReportSrv**:

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

## <a name="see-also"></a>Ayrıca bkz:

* [Bir çekme istemci yapılandırma adları ile ayarlama](pullClientConfigNames.md)