---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: PowerShell 4. 0 ' yapılandırması kimliği kullanan bir çekme istemci ayarlama
ms.openlocfilehash: f9bea92f1a2dce94792d72e03bef884d2729f3c0
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34187775"
---
# <a name="setting-up-a-pull-client-using-configuration-id-in-powershell-40"></a>PowerShell 4. 0 ' yapılandırması kimliği kullanan bir çekme istemci ayarlama

>İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0

Çekme modunu kullanacak şekilde söylediyse ve yapılandırmaları almak için çekme sunucunun nerede ile bağlantı kurabildiğini URL verilen her hedef düğüme sahiptir. Bunu yapmak için gerekli olan bilgileri yerel Configuration Manager (LCM'yi) yapılandırmanız gerekir. LCM'yi yapılandırmak için bir "meta yapılandırmasını" bilinen yapılandırma özel bir tür oluşturun. LCM'yi yapılandırma hakkında daha fazla bilgi için bkz: [Windows PowerShell 4.0 istenen durum yapılandırması yerel Configuration Manager](metaConfig4.md)

Aşağıdaki komut dosyası LCM'yi çekme yapılandırmaları için "PullServer" adlı bir sunucudan yapılandırır:

```powershell
Configuration SimpleMetaConfigurationForPull
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
SimpleMetaConfigurationForPull -Output "."
```

Komut dosyasında **DownloadManagerCustomData** geçişleri URL çekme sunucusunun ve (Bu örneğin), güvenli olmayan bir bağlantı sağlar.

Bu betik çalıştıktan sonra adlı yeni bir çıkış klasörü oluşturur **SimpleMetaConfigurationForPull** ve meta yapılandırmasını MOF dosyası var. yerleştirir.

Yapılandırmayı uygulamak için kullanmak **kümesi DscLocalConfigurationManager** parametrelere sahip **ComputerName** ("localhost" kullanın) ve **yolu** (konumu yolu düğümün localhost.meta.mof dosya hedef). Örneğin:
```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path . –Verbose.
```

## <a name="configuration-id"></a>Yapılandırma Kimliği
Komut dosyası kümeleri **ConfigurationID** bu amaç için daha önce oluşturulmuş bir GUID LCM'yi özelliği (kullanarak bir GUID oluşturabilirsiniz **yeni GUID** cmdlet'i). **ConfigurationID** LCM'yi çekme sunucusunda uygun yapılandırma bulmak için kullanır. Çekme sunucusunda yapılandırma MOF dosyası olarak adlandırılmalıdır `ConfigurationID.mof`, burada *ConfigurationID* değeri **ConfigurationID** hedef düğümün LCM'yi özelliği.

## <a name="pulling-from-an-smb-server"></a>Bir SMB sunucusundan çekme

Belirttiğiniz çekme sunucusuna bir web hizmeti yerine bir SMB dosya paylaşımı olarak ayarlanırsa, **DscFileDownloadManager** yerine **WebDownLoadManager**.
**DscFileDownloadManager** geçen bir **KaynakYolu** özelliği yerine **ServerUrl**. Aşağıdaki komut dosyası "CONTOSO-SERVER" adlı bir sunucuda "SmbDscShare" adlı bir SMB paylaşımına yapılandırmalardan çıkarmak için LCM'yi yapılandırır:

```powershell
Configuration SimpleMetaConfigurationForPull
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
SimpleMetaConfigurationForPull -Output "."
```

## <a name="see-also"></a>Ayrıca bkz:

- [DSC çekme sunucusuna ayarlama](pullServer.md)
- [DSC SMB çekme sunucusu ayarlama](pullServerSMB.md)