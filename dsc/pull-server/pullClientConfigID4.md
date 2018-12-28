---
ms.date: 12/12/2018
keywords: DSC, powershell, yapılandırma, Kurulum
title: Yapılandırma kimliklerinin PowerShell 4. 0'kullanarak bir çekme istemcisi ayarlama
ms.openlocfilehash: 9adc767e91ff19d373c122a0d493e7b8703d5476
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405880"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-40"></a>Yapılandırma kimliklerinin PowerShell 4. 0'kullanarak bir çekme istemcisi ayarlama

>Şunun için geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0

> [!IMPORTANT]
> Çekme sunucusu (Windows özelliği *DSC hizmet*) ancak desteklenen bir bileşen Windows Server'ın yeni özellikler veya yetenekler sunmak için herhangi bir plan vardır. Geçişi başlıyor önerilir yönetilen istemcilere [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (Windows Server çekme sunucusunda dışında özellikler dahildir) veya topluluk çözümlerden birini listelenen [burada](pullserver.md#community-solutions-for-pull-service).

Çekme istemcisi ayarlama ayarlamadan önce bir çekme sunucusu ayarlamanız gerekir. Bu sırada gerekli olmasa da gidermeye yardımcı olur ve kayıt başarılı olmanıza yardımcı olur. Bir çekme sunucusu kurmak için aşağıdaki kılavuzları kullanabilirsiniz:

- [Bir DSC SMB çekme sunucusu ayarlama](pullServerSmb.md)
- [Bir DSC HTTP çekme sunucusu ayarlama](pullServer.md)

Her hedef düğüm yapılandırmaları, kaynaklar, indirin ve bile durumunu raporlamak için yapılandırılabilir. Aşağıdaki bölümlerde bir SMB paylaşımı ya da HTTP DSC çekme sunucusuna çekme istemcisi yapılandırma işlemini göstermektedir. Düğümün LCM yenilendiğinde atanan tüm yapılandırmaları indirmek için yapılandırılan konuma ulaşır. Tüm gerekli kaynakları düğüm üzerinde mevcut değilse, bunu otomatik olarak bunları yapılandırılan konumdan indirir. Düğüm ile yapılandırılmışsa, bir [rapor sunucusu](reportServer.md), sonra işlemin durumunu bildirir.

## <a name="configure-the-pull-client-lcm"></a>Çekme istemcisi LCM yapılandırma

Aşağıdaki örneklerde hiçbirini yürütme adlı yeni bir çıktı klasörü oluşturur **PullClientConfigID** ve metaconfiguration MOF dosyası var. koyar. Bu durumda, metaconfiguration MOF dosyasını adlandırılacağını `localhost.meta.mof`.

Yapılandırmayı uygulamak için arama **Set-DscLocalConfigurationManager** cmdlet'i ile **yolu** metaconfiguration MOF dosyasının konumuna ayarlayın. Örneğin:

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a>Yapılandırma Kimliği

Aşağıdaki kümesi örneklerden **ConfigurationID** LCM için özelliği bir **GUID** , önceden oluşturulmuş bu amaç için. **ConfigurationID** LCM çekme sunucusunda uygun yapılandırma bulmak için kullanır. Yapılandırma MOF dosyasının çekme sunucusunda adlandırılmalıdır `ConfigurationID.mof`burada *ConfigurationID* değeri **ConfigurationID** hedef düğümün LCM özelliğidir. Daha fazla bilgi için [yayımlama yapılandırmalar çekme sunucusuna (v4/v5)](publishConfigs.md).

Rastgele bir sıra oluşturabilirsiniz **GUID** aşağıdaki örneği kullanarak.

```powershell
[System.Guid]::NewGuid()
```

## <a name="set-up-a-pull-client-to-download-configurations"></a>Yapılandırmaları indirmek için bir çekme istemcisi ayarlama

Her istemci yapılandırılmalıdır **çekme** modu ve çekme sunucusu URL'si yapılandırmasıyla depolandığı verilir. Bunu yapmak için gerekli olan bilgileri yerel Configuration Manager (LCM) yapılandırma gerekir. LCM yapılandırmak için yapılandırma, özel bir tür ile oluşturduğunuz bir **LocalConfigurationManager** blok. LCM yapılandırma hakkında daha fazla bilgi için bkz. [yerel Configuration Manager Yapılandırma](../managing-nodes/metaConfig4.md).

## <a name="http-dsc-pull-server"></a>HTTP DSC çekme sunucusuna

Çekme sunucusu web hizmeti olarak ayarlanıp ayarlanmadığını ayarladığınız **DownloadManagerName** için **WebDownloadManager**. **WebDownloadManager** belirtmenizi gerektiren bir **ServerUrl** için **DownloadManagerCustomData** anahtarı. İçin bir değer belirtebilirsiniz **AllowUnsecureConnection**, aşağıdaki örnekte gösterilen şekilde. Aşağıdaki betiği LCM "PullServer" adlı bir sunucudan çekme yapılandırmaları için yapılandırır.

```powershell
Configuration PullClientConfigId
{
    LocalConfigurationManager
    {
        ConfigurationID = "1C707B86-EF8E-4C29-B7C1-34DA2190AE24";
        RefreshMode = "PULL";
        DownloadManagerName = "WebDownloadManager";
        RebootNodeIfNeeded = $true;
        RefreshFrequencyMins = 30;
        ConfigurationModeFrequencyMins = 30;
        ConfigurationMode = "ApplyAndAutoCorrect";
        DownloadManagerCustomData = @{ServerUrl = "http://PullServer:8080/PSDSCPullServer/PSDSCPullServer.svc"; AllowUnsecureConnection = “TRUE”}
    }
}
PullClientConfigId -Output "."
```

## <a name="smb-share"></a>SMB paylaşımı

Çekme sunucusu bir web hizmeti yerine bir SMB dosya paylaşımı olarak ayarlanmışsa, ayarladığınız **DownloadManagerName** için **DscFileDownloadManager** yerine **WebDownLoadManager**. **DscFileDownloadManager** belirtmenizi gerektiren bir **SourcePath** özelliğinde **DownloadManagerCustomData**. Aşağıdaki betik, "CONTOSO-SERVER" adlı bir sunucu üzerinde "SmbDscShare" adlı bir SMB paylaşımından yapılandırmalar çekme LCM yapılandırır.

```powershell
Configuration PullClientConfigId
{
    LocalConfigurationManager
    {
        ConfigurationID = "1C707B86-EF8E-4C29-B7C1-34DA2190AE24";
        RefreshMode = "PULL";
        DownloadManagerName = "DscFileDownloadManager";
        RebootNodeIfNeeded = $true;
        RefreshFrequencyMins = 30;
        ConfigurationModeFrequencyMins = 30;
        ConfigurationMode = "ApplyAndAutoCorrect";
        DownloadManagerCustomData = @{ServerUrl = "\\CONTOSO-SERVER\SmbDscShare"}
    }
}
PullClientConfigId -Output "."
```

## <a name="next-steps"></a>Sonraki Adımlar

Çekme istemcisi yapılandırıldıktan sonra sonraki adımları gerçekleştirmek için aşağıdaki kılavuzları kullanın:

- [Yapılandırmalar çekme sunucusuna (v4/v5) yayımlama](publishConfigs.md)
- [Paket ve karşıya yükleme kaynakları çekme sunucusuna (v4)](package-upload-resources.md)

## <a name="see-also"></a>Ayrıca bkz:

- [Bir DSC web çekme sunucusu ayarlama](pullServer.md)
- [DSC SMB çekme sunucusu ayarlama](pullServerSMB.md)
