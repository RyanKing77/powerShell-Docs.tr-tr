---
ms.date: 12/12/2018
keywords: DSC, PowerShell, yapılandırma, kurulum
title: Yapılandırma kimliklerini (v4/V5) kullanarak bir çekme sunucusuna yayımlama
ms.openlocfilehash: c258814f480b91eba75c7ce9abf70c558f1f469e
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986569"
---
# <a name="publish-to-a-pull-server-using-configuration-ids-v4v5"></a>Yapılandırma kimliklerini (v4/V5) kullanarak bir çekme sunucusuna yayımlama

Aşağıdaki bölümler, zaten bir çekme sunucusu ayarlamış olduğunuz varsayılmaktadır. Çekme sunucunuzu ayarlamadıysanız Aşağıdaki kılavuzlardan yararlanabilirsiniz:

- [DSC SMB çekme sunucusu ayarlama](pullServerSmb.md)
- [DSC HTTP çekme sunucusu ayarlama](pullServer.md)

Her hedef düğüm, yapılandırmaların, kaynakların indirileceği ve hatta durumunu rapor etmek üzere yapılandırılabilir. Bu makalede, karşıdan yüklenmek üzere kullanılabilir olmaları için kaynakları karşıya yükleme ve istemcileri otomatik olarak kaynakları yükleyecek şekilde yapılandırma işlemlerinin nasıl yapılacağı gösterilir. Düğüm, **çekme** veya **Push** (V5) aracılığıyla atanan bir yapılandırma aldığında, yapılandırma Için gereken tüm kaynakları yerel Configuration Manager (LCM) ' de belirtilen konumdan otomatik olarak indirir.

## <a name="compile-configurations"></a>Derleme yapılandırması

[Yapılandırma](../configurations/configurations.md) bir çekme sunucusunda depolamanın ilk adımı, bunları dosyalar halinde `.mof` derlemek. Bir yapılandırmayı genel hale getirmek ve daha fazla istemci için geçerli olan düğüm `localhost` blosonra kullanın. Aşağıdaki örnekte, belirli bir istemci adı yerine tarafından `localhost` kullanılan bir yapılandırma kabuğu gösterilmektedir.

```powershell
Configuration GenericConfig
{
    Node localhost
    {

    }
}
GenericConfig
```

Genel yapılandırmanızı derledikten sonra bir `localhost.mof` dosyanız olmalıdır.

## <a name="renaming-the-mof-file"></a>MOF dosyasını yeniden adlandırma

Yapılandırma `.mof` dosyalarını, bir çekme sunucusunda **ConfigurationName** veya **ConfigurationId**ile saklayabilirsiniz. Çekme istemcilerinizi nasıl ayarlamayı planladığınıza bağlı olarak, derlenmiş `.mof` dosyalarınızı düzgün şekilde yeniden adlandırmak için aşağıdan bir bölüm seçebilirsiniz.

### <a name="configuration-ids-guid"></a>Yapılandırma kimlikleri (GUID)

Dosyanızı dosya olarak `localhost.mof` `<GUID>.mof` yeniden adlandırmanız gerekir. Aşağıdaki örneği kullanarak veya [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet 'ini kullanarak rastgele bir **GUID** oluşturabilirsiniz.

```powershell
[System.Guid]::NewGuid()
```

Örnek çıkış

```Output
Guid
----
64856475-939e-41fb-aba5-4469f4006059
```

Daha sonra, kabul edilebilir `.mof` herhangi bir yöntemi kullanarak dosyanızı yeniden adlandırabilirsiniz. Aşağıdaki örnek, [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet 'ini kullanır.

```powershell
Rename-Item -Path .\localhost.mof -NewName '64856475-939e-41fb-aba5-4469f4006059.mof'
```

Ortamınızda **GUID 'leri** kullanma hakkında daha fazla bilgi için bkz. [GUID için plan](/powershell/dsc/secureserver#guids).

### <a name="configuration-names"></a>Yapılandırma adları

Dosyanızı dosya olarak `localhost.mof` `<Configuration Name>.mof` yeniden adlandırmanız gerekir. Aşağıdaki örnekte, önceki bölümdeki yapılandırma adı kullanılır. Daha sonra, kabul edilebilir `.mof` herhangi bir yöntemi kullanarak dosyanızı yeniden adlandırabilirsiniz. Aşağıdaki örnek, [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet 'ini kullanır.

```powershell
Rename-Item -Path .\localhost.mof -NewName 'GenericConfig.mof'
```

## <a name="create-the-checksum"></a>Sağlama toplamını oluşturma

Bir `.mof` çekme sunucusunda depolanan her bir dosyanın veya SMB paylaşımının ilişkili `.checksum` bir dosyası olması gerekir.
Bu dosya, istemcilerin ilişkili `.mof` dosyanın değiştiğini bilmesini sağlar ve yeniden indirilmelidir.

[New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) cmdlet 'i Ile bir **sağlama toplamı** oluşturabilirsiniz. Ayrıca, parametresini kullanarak `New-DSCCheckSum` bir dosya dizini için `-Path` de çalıştırabilirsiniz.
Bir sağlama toplamı zaten varsa, bu `-Force` parametre ile yeniden oluşturulmasını zorunlu hale getirebilirsiniz. Aşağıdaki örnek, önceki bölümden `.mof` dosyasını içeren bir dizin belirtti ve `-Force` parametresini kullanır.

```powershell
New-DscChecksum -Path '.\' -Force
```

Çıktı gösterilmez, ancak artık bir `<GUID or Configuration Name>.mof.checksum` dosya görmeniz gerekir.

## <a name="where-to-store-mof-files-and-checksums"></a>MOF dosyalarının ve sağlama toplamlarını nerede depolayabileceğiniz

### <a name="on-a-dsc-http-pull-server"></a>DSC HTTP çekme sunucusunda

HTTP çekme sunucunuzu ayarlarken [DSC http çekme sunucusu ayarlama](pullServer.md)bölümünde açıklandığı gibi, **ModulePath** ve **ConfigurationPath** anahtarlarının dizinlerini belirtirsiniz. **ModulePath** anahtarı, bir modülün paketlenmiş `.zip` dosyalarının nerede depolanması gerektiğini gösterir. **ConfigurationPath** , herhangi bir `.mof` dosya ve `.checksum` dosyanın nerede depolanması gerektiğini gösterir.

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

### <a name="on-an-smb-share"></a>Bir SMB paylaşımında

Bir SMB paylaşımının kullanılması için bir Istek temelli Istemci ayarladığınızda, bir **Configurationdepotorshare**belirlersiniz.
Tüm `.mof` dosyalar ve `.checksum` dosyalar, **configurationdepotorshare** bloğunun **SourcePath** dizininde depolanmalıdır.

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

## <a name="next-steps"></a>Sonraki adımlar

Ardından, belirtilen yapılandırmayı çekmek için çekme Istemcilerini yapılandırmak isteyeceksiniz. Daha fazla bilgi için aşağıdaki kılavuzlardan birine bakın:

- [Yapılandırma kimlikleri (v4) kullanarak çekme Istemcisi ayarlama](pullClientConfigId4.md)
- [Yapılandırma kimliklerini (V5) kullanarak çekme Istemcisi ayarlama](pullClientConfigId.md)
- [Yapılandırma adlarını (V5) kullanarak çekme Istemcisini ayarlama](pullClientConfigNames.md)

## <a name="see-also"></a>Ayrıca bkz.

- [DSC SMB çekme sunucusu ayarlama](pullServerSmb.md)
- [DSC HTTP çekme sunucusu ayarlama](pullServer.md)
- [Kaynakları bir çekme sunucusuna paketleme ve yükleme](package-upload-resources.md)
