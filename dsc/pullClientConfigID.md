---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: Yapılandırma kimliğini kullanarak çekme istemcisi ayarlama
ms.openlocfilehash: b4a45c4d014b3c4fc0140ad492f81474b260065a
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34187502"
---
# <a name="setting-up-a-pull-client-using-configuration-id"></a>Yapılandırma kimliğini kullanarak çekme istemcisi ayarlama

> İçin geçerlidir: Windows PowerShell 5.0

> [!IMPORTANT]
> Çekme sunucusuna (Windows özelliği *DSC hizmet*) vardır ancak desteklenen bir bileşen Windows Server'ın yeni özellikleri veya yetenekleri sunmak için herhangi bir plan vardır. Geçiş başlamak için önerilen yönetilen istemcilere [Azure Otomasyonu DSC](/azure/automation/automation-dsc-getting-started) (Windows Server çekme sunucusunda ötesinde özellikler içerir) veya topluluk çözümlerden birini listelenen [burada](pullserver.md#community-solutions-for-pull-service).

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