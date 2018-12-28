---
ms.date: 12/12/2018
keywords: DSC, powershell, yapılandırma, Kurulum
title: Bir çekme yapılandırma kimliklerinin PowerShell 5.0 ve üzeri kullanılarak istemcisi ayarlama
ms.openlocfilehash: 8d8cf478f9127e1b7005d1b9e832e84b11612c9c
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405828"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-50-and-later"></a>Bir çekme yapılandırma kimliklerinin PowerShell 5.0 ve üzeri kullanılarak istemcisi ayarlama

> Şunun için geçerlidir: Windows PowerShell 5.0

> [!IMPORTANT]
> Çekme sunucusu (Windows özelliği *DSC hizmet*) ancak desteklenen bir bileşen Windows Server'ın yeni özellikler veya yetenekler sunmak için herhangi bir plan vardır. Geçişi başlıyor önerilir yönetilen istemcilere [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (Windows Server çekme sunucusunda dışında özellikler dahildir) veya topluluk çözümlerden birini listelenen [burada](pullserver.md#community-solutions-for-pull-service).

Çekme istemcisi ayarlama ayarlamadan önce bir çekme sunucusu ayarlamanız gerekir. Bu sırada gerekli olmasa da gidermeye yardımcı olur ve kayıt başarılı olmanıza yardımcı olur. Bir çekme sunucusu kurmak için aşağıdaki kılavuzları kullanabilirsiniz:

- [Bir DSC SMB çekme sunucusu ayarlama](pullServerSmb.md)
- [Bir DSC HTTP çekme sunucusu ayarlama](pullServer.md)

Her hedef düğüm yapılandırmaları, kaynaklar, indirin ve bile durumunu raporlamak için yapılandırılabilir. Aşağıdaki bölümlerde bir SMB paylaşımı ya da HTTP DSC çekme sunucusuna çekme istemcisi yapılandırma işlemini göstermektedir. Düğümün LCM yenilendiğinde atanan tüm yapılandırmaları indirmek için yapılandırılan konuma ulaşır. Tüm gerekli kaynakları düğüm üzerinde mevcut değilse, bunu otomatik olarak bunları yapılandırılan konumdan indirir. Düğüm ile yapılandırılmışsa, bir [rapor sunucusu](reportServer.md), sonra işlemin durumunu bildirir.

> **Not**: Bu konu, PowerShell 5.0 için geçerlidir. PowerShell 4.0 çekme istemcisi ayarlama hakkında daha fazla bilgi için bkz: [PowerShell 4. 0'yapılandırma Kimliğini kullanarak çekme istemcisi ayarlama](pullClientConfigID4.md)

## <a name="configure-the-pull-client-lcm"></a>Çekme istemcisi LCM yapılandırma

Aşağıdaki örneklerde hiçbirini yürütme adlı yeni bir çıktı klasörü oluşturur **PullClientConfigID** ve metaconfiguration MOF dosyası var. koyar. Bu durumda, metaconfiguration MOF dosyasını adlandırılacağını `localhost.meta.mof`.

Yapılandırmayı uygulamak için arama **Set-DscLocalConfigurationManager** cmdlet'i ile **yolu** metaconfiguration MOF dosyasının konumuna ayarlayın. Örneğin:

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a>Yapılandırma Kimliği

Ayarlar aşağıdaki örneklerden **ConfigurationID** LCM için özelliği bir **GUID** , önceden oluşturulmuş bu amaç için. **ConfigurationID** LCM çekme sunucusunda uygun yapılandırma bulmak için kullanır. Yapılandırma MOF dosyasının çekme sunucusunda adlandırılmalıdır `ConfigurationID.mof`burada *ConfigurationID* değeri **ConfigurationID** hedef düğümün LCM özelliğidir. Daha fazla bilgi için [yayımlama yapılandırmalar çekme sunucusuna (v4/v5)](publishConfigs.md).

Rastgele bir sıra oluşturabilirsiniz **GUID** kullanarak veya aşağıdaki örneği kullanarak [yeni GUID](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet'i.

```powershell
[System.Guid]::NewGuid()
```

Kullanma hakkında daha fazla bilgi için **GUID'leri** ortamınızda bkz [planlama GUID'leri](/powershell/dsc/secureserver#guids).

## <a name="set-up-a-pull-client-to-download-configurations"></a>Yapılandırmaları indirmek için bir çekme istemcisi ayarlama

Her istemci yapılandırılmalıdır **çekme** modu ve çekme sunucusu URL'si yapılandırmasıyla depolandığı verilir. Bunu yapmak için gerekli olan bilgileri yerel Configuration Manager (LCM) yapılandırma gerekir. LCM yapılandırmak için özel bir tür ile donatılmış yapılandırması oluşturun. **DSCLocalConfigurationManager** özniteliği. LCM yapılandırma hakkında daha fazla bilgi için bkz. [yerel Configuration Manager Yapılandırma](../managing-nodes/metaConfig.md).

### <a name="http-dsc-pull-server"></a>HTTP DSC çekme sunucusuna

Aşağıdaki betik, "CONTOSO-PullSrv" adlı bir sunucudan çekme yapılandırmalarına LCM yapılandırır.

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

Betikteki **ConfigurationRepositoryWeb** blok çekme sunucusu tanımlar. **ServerUrl** DSC çekme URL'sini belirtir

### <a name="smb-share"></a>SMB paylaşımı

Aşağıdaki betiği LCM çekme yapılandırmalar için SMB paylaşımından yapılandırır `\\SMBPullServer\Pull`.

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
            SourcePath = '\\SMBPullServer\Pull'
        }
    }
}
PullClientConfigID
```

Betikteki **ConfigurationRepositoryShare** blok, bu durumda, yalnızca bir SMB paylaşımına çekme sunucusu tanımlar.

## <a name="set-up-a-pull-client-to-download-resources"></a>Kaynakları indirmek için bir çekme istemcisi ayarlama

Yalnızca belirtirseniz **ConfigurationRepositoryWeb** veya **ConfigurationRepositoryShare** LCM yapılandırmanızda (önceki örnek) olduğu gibi engelleme, çekme istemcisi aynı kaynaklardan çeker konum, yapılandırmaları alır. Kaynaklar için ayrı konumlar belirtebilirsiniz. Bir kaynak konumu ayrı bir sunucu belirtmek için kullanın **ResourceRepositoryWeb** blok. Bir kaynak konumu SMB paylaşımı belirtmek için kullanın **ResourceRepositoryShare** blok.

> [!NOTE]
> Birleştirebilirsiniz **ConfigurationRepositoryWeb** ile **ResourceRepositoryShare** veya **ConfigurationRepositoryShare** ile **ResourceRepositoryWeb** . Buna örnek olarak, aşağıda gösterilmez.

### <a name="http-dsc-pull-server"></a>HTTP DSC çekme sunucusuna

Çekme istemcisi kendi yapılandırmaları almak için aşağıdaki metaconfiguration yapılandırır **CONTOSO PullSrv** ve kaynaklarıyla **CONTOSO ResourceSrv**.

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
    }
}
PullClientConfigID
```

### <a name="smb-share"></a>SMB paylaşımı

Aşağıdaki örnek, bir istemcinin SMB paylaşımından çekme yapılandırmaları ayarlayan bir metaconfiguration gösterir `\\SMBPullServer\Configurations`ve SMB paylaşımındaki kaynakları `\\SMBPullServer\Resources`.

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
            SourcePath = '\\SMBPullServer\Configurations'
        }

        ResourceRepositoryShare SMBResourceServer
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigID
```

#### <a name="automatically-download-resources-in-push-mode"></a>Anında iletme modunda kaynakları otomatik olarak indir

İçin bile yapılandırılmış PowerShell 5. 0'den itibaren çekme istemcilerinize modülleri bir SMB paylaşımından indirebilir **anında iletme** modu. Bu çekme sunucusu kurmak istediğiniz olmayan senaryolarda özellikle yararlıdır. **ResourceRepositoryShare** blok belirtmeden kullanılabilir bir **ConfigurationRepositoryShare**. Aşağıdaki örnek, bir istemcinin bir SMB paylaşımından çekme kaynaklarına ayarlar bir metaconfiguration gösterir `\\SMBPullServer\Resources`. Düğüm olduğunda **PUSHED** bir yapılandırma, otomatik olarak tüm gerekli kaynakları belirtilen paylaşımından indirir.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Push'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
        }

        ResourceRepositoryShare SMBResourceServer
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigID
```

## <a name="set-up-a-pull-client-to-report-status"></a>Rapor durumu çekme istemcisi ayarlama

Varsayılan olarak, düğüm raporları yapılandırılmış bir çekme sunucusuna göndermezler. Bir tek çekme sunucusu yapılandırmaları, kaynaklar ve raporlama için kullanabilirsiniz, ancak oluşturmak sahip olduğunuz bir **ReportRepositoryWeb** set up reporting bloğu.

### <a name="http-dsc-pull-server"></a>HTTP DSC çekme sunucusuna

Aşağıdaki örnek, bir istemci çekme yapılandırmaları ve kaynakları ve verileri, bir tek çekme sunucusuna rapor veren gönder ayarlar bir metaconfiguration gösterir.

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

Bir rapor sunucusunu belirtmek için kullandığınız bir **ReportRepositoryWeb** blok. Rapor sunucusu bir SMB sunucusu olamaz.
Çekme istemcisi kendi yapılandırmaları almak için aşağıdaki metaconfiguration yapılandırır **CONTOSO PullSrv** ve kaynaklarıyla **CONTOSO ResourceSrv**ve durum raporları göndermek için  **CONTOSO ReportSrv**:

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

### <a name="smb-share"></a>SMB paylaşımı

Rapor sunucusu bir SMB paylaşımı olamaz.

## <a name="next-steps"></a>Sonraki Adımlar

Çekme istemcisi yapılandırıldıktan sonra sonraki adımları gerçekleştirmek için aşağıdaki kılavuzları kullanın:

- [Yapılandırmalar çekme sunucusuna (v4/v5) yayımlama](publishConfigs.md)
- [Paket ve karşıya yükleme kaynakları çekme sunucusuna (v4)](package-upload-resources.md)

## <a name="see-also"></a>Ayrıca bkz:

* [Yapılandırma adları ile çekme istemcisi ayarlama](pullClientConfigNames.md)
