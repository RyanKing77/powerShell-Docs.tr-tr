---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: Bir çekme PowerShell 5.0 ve üzeri yapılandırma adlarını kullanarak istemcisi ayarlama
ms.openlocfilehash: fd038a105da7a83ecad9b571e611b65c8ec847b3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688080"
---
# <a name="set-up-a-pull-client-using-configuration-names-in-powershell-50-and-later"></a>Bir çekme PowerShell 5.0 ve üzeri yapılandırma adlarını kullanarak istemcisi ayarlama

> Şunun için geçerlidir: Windows PowerShell 5.0

> [!IMPORTANT]
> Çekme sunucusu (Windows özelliği *DSC hizmet*) ancak desteklenen bir bileşen Windows Server'ın yeni özellikler veya yetenekler sunmak için herhangi bir plan vardır. Geçişi başlıyor önerilir yönetilen istemcilere [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (Windows Server çekme sunucusunda dışında özellikler dahildir) veya topluluk çözümlerden birini listelenen [burada](pullserver.md#community-solutions-for-pull-service).

Çekme istemcisi ayarlama ayarlamadan önce bir çekme sunucusu ayarlamanız gerekir. Bu sırada gerekli olmasa da gidermeye yardımcı olur ve kayıt başarılı olmanıza yardımcı olur. Bir çekme sunucusu kurmak için aşağıdaki kılavuzları kullanabilirsiniz:

- [Bir DSC SMB çekme sunucusu ayarlama](pullServerSmb.md)
- [Bir DSC HTTP çekme sunucusu ayarlama](pullServer.md)

Her hedef düğüm yapılandırmaları, kaynaklar, indirin ve bile durumunu raporlamak için yapılandırılabilir. Aşağıdaki bölümlerde bir SMB paylaşımı ya da HTTP DSC çekme sunucusuna çekme istemcisi yapılandırma işlemini göstermektedir. Düğümün LCM yenilendiğinde atanan tüm yapılandırmaları indirmek için yapılandırılan konuma ulaşır. Tüm gerekli kaynakları düğüm üzerinde mevcut değilse, bunu otomatik olarak bunları yapılandırılan konumdan indirir. Düğüm ile yapılandırılmışsa, bir [rapor sunucusu](reportServer.md), sonra işlemin durumunu bildirir.

> **Not**: Bu konu, PowerShell 5.0 için geçerlidir.
PowerShell 4.0 çekme istemcisi ayarlama hakkında daha fazla bilgi için bkz: [PowerShell 4. 0'yapılandırma Kimliğini kullanarak çekme istemcisi ayarlama](pullClientConfigID4.md)

## <a name="configure-the-pull-client-lcm"></a>Çekme istemcisi LCM yapılandırma

Aşağıdaki örneklerde hiçbirini yürütme adlı yeni bir çıktı klasörü oluşturur **PullClientConfigName** ve metaconfiguration MOF dosyası var. koyar. Bu durumda, metaconfiguration MOF dosyasını adlandırılacağını `localhost.meta.mof`.

Yapılandırmayı uygulamak için arama **Set-DscLocalConfigurationManager** cmdlet'i ile **yolu** metaconfiguration MOF dosyasının konumuna ayarlayın. Örneğin:

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigName –Verbose.
```

## <a name="configuration-name"></a>Yapılandırma adı

Ayarlar aşağıdaki örneklerden **ConfigurationName** LCM önceden derlenmiş bir yapılandırma adı özelliği bu amaç için oluşturulan. **ConfigurationName** LCM çekme sunucusunda uygun yapılandırma bulmak için kullanır. Yapılandırma MOF dosyasının çekme sunucusunda adlandırılmalıdır `<ConfigurationName>.mof`, bu durumda, "ClientConfig.mof". Daha fazla bilgi için [yayımlama yapılandırmalar çekme sunucusuna (v4/v5)](publishConfigs.md).

## <a name="set-up-a-pull-client-to-download-configurations"></a>Yapılandırmaları indirmek için bir çekme istemcisi ayarlama

Her istemci yapılandırılmalıdır **çekme** modu ve çekme sunucusu URL'si yapılandırmasıyla depolandığı verilir. Bunu yapmak için gerekli olan bilgileri yerel Configuration Manager (LCM) yapılandırma gerekir. LCM yapılandırmak için özel bir tür ile donatılmış yapılandırması oluşturun. **DSCLocalConfigurationManager** özniteliği. LCM yapılandırma hakkında daha fazla bilgi için bkz. [yerel Configuration Manager Yapılandırma](../managing-nodes/metaConfig.md).

Aşağıdaki betik, "CONTOSO-PullSrv" adlı bir sunucudan çekme yapılandırmalarına LCM yapılandırır.

- Betikteki **ConfigurationRepositoryWeb** blok çekme sunucusu tanımlar. **ServerURL** özelliği, çekme sunucusu için uç nokta belirtir.

- **RegistrationKey** bir çekme sunucusu için tüm istemci düğümleri bu çekme sunucusu arasında paylaşılan bir anahtar özelliğidir. Bir dosyayı çekme sunucusunda aynı değeri depolanır.
  > **Not**: Kayıt anahtarları yalnızca çalışın **web** çekme sunucuları. Yine de kullanmalısınız **ConfigurationID** ile bir **SMB** çekme sunucusu.
  > Bir çekme sunucusu kullanarak yapılandırma hakkında bilgi için **ConfigurationID**, bkz: [yapılandırma Kimliğini kullanarak çekme istemcisi ayarlama](pullClientConfigId.md)

- **ConfigurationNames** istemci düğümü için hedeflenen yapılandırmaları adlarını belirten bir dizi bir özelliktir.
  >**Not:** Birden fazla değer belirtirseniz **ConfigurationNames**, de belirtmeniz gerekir **PartialConfiguration** yapılandırmanızda engeller.
  >Kısmi yapılandırmalar hakkında daha fazla bilgi için bkz. [PowerShell Desired State Configuration kısmi yapılandırmalar](partialConfigs.md).

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

## <a name="set-up-a-pull-client-to-download-resources"></a>Kaynakları indirmek için bir çekme istemcisi ayarlama

Yalnızca belirtirseniz bir **ConfigurationRepositoryWeb** veya **ConfigurationRepositoryShare** (önceki örnekteki) LCM yapılandırmanızda engelleme, çekme istemcisi aynı kaynaklardan çeker ".mof" dosyalarınızın depolandığı konum. İstemciler kaynakları yükleyebileceğiniz farklı konumlar belirtebilirsiniz. Kaynak sunucuyu belirtmek için ya da kullandığınız bir **ResourceRepositoryWeb** (için web çekme sunucusu) veya bir **ResourceRepositoryShare** bloğu (SMB çekme sunucusu için).

Aşağıdaki örnek, bir istemcinin yapılandırmaları bir çekme sunucusu ve kaynaklardan bir SMB paylaşımından indirmek için ayarlar bir metaconfiguration gösterir.

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

        ResourceRepositoryShare SMBResources
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigNames
```

## <a name="set-up-a-pull-client-to-report-status"></a>Rapor durumu çekme istemcisi ayarlama

Bir tek çekme sunucusu yapılandırmaları, kaynaklar ve raporlama için kullanabilirsiniz. Raporlama için istemcileri varsayılan olarak yapılandırılmamış. Oluşturmak zorunda için durumu rapor edebilmiş istemciyi yapılandırmak için bir **ReportRepositoryWeb** blok. Aşağıdaki örnek, bir istemci çekme yapılandırmaları ve kaynakları ve verileri, bir tek çekme sunucusuna rapor veren gönder ayarlar bir metaconfiguration gösterir.

> [!NOTE]
> Rapor sunucusu bir SMB paylaşımı olamaz.

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
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }
    }
}
PullClientConfigNames
```

## <a name="see-also"></a>Ayrıca bkz:

* [Yapılandırma kimliği ile çekme istemcisi ayarlama](PullClientConfigNames.md)
* [Bir DSC web çekme sunucusu ayarlama](pullServer.md)
