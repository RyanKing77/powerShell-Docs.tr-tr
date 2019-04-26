---
ms.date: 12/12/2018
keywords: DSC, powershell, yapılandırma, Kurulum
title: Bir çekme yapılandırma kimliklerinin (v4/v5) kullanarak sunucuda yayımlayın
ms.openlocfilehash: 0144fec43d7a8d65b79891567cc0dc3952175343
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079515"
---
# <a name="publish-to-a-pull-server-using-configuration-ids-v4v5"></a>Bir çekme yapılandırma kimliklerinin (v4/v5) kullanarak sunucuda yayımlayın

Aşağıdaki bölümler, zaten bir çekme sunucusu ayarladığınızı varsayalım. Çekme sunucunuzu ayarlamadıysanız, aşağıdaki kılavuzları kullanabilirsiniz:

- [Bir DSC SMB çekme sunucusu ayarlama](pullServerSmb.md)
- [Bir DSC HTTP çekme sunucusu ayarlama](pullServer.md)

Her hedef düğüm yapılandırmaları, kaynaklar, indirin ve bile durumunu raporlamak için yapılandırılabilir. Bu makale indirilmesi ve kaynakları otomatik olarak indirmek için istemcileri yapılandırın kullanabilmesi için kaynakları karşıya yükleme işlemini gösterir. Düğümün aldığında atanmış bir yapılandırma yoluyla **çekme** veya **anında iletme** (v5) otomatik olarak karşıdan yüklerken LCM içinde belirtilen konumdan yapılandırma için gerekli tüm kaynakları.

## <a name="compile-configurations"></a>Derleme yapılandırmaları

Depolama ilk adımı [yapılandırmaları](../configurations/configurations.md) bunları ".mof" dosyalarına derlemek için bir çekme sunucusu olduğunu. Genel ve daha fazla istemci için geçerli bir yapılandırma oluşturmak için kullanın `localhost` , düğüm bloğundaki. Aşağıdaki örnek, kullanan bir yapılandırma Kabuk gösterir `localhost` belirli istemci adı yerine.

```powershell
Configuration GenericConfig
{
    Node localhost
    {

    }
}
GenericConfig
```

Genel yapılandırma derlediğiniz sonra "localhost.mof" dosyası olmalıdır.

## <a name="renaming-the-mof-file"></a>MOF dosyasını yeniden adlandırma

Bir çekme sunucusu tarafından yapılandırma ".mof" dosyalarını depoladığınız **ConfigurationName** veya **ConfigurationID**. Nasıl çekme istemcilerinize ayarlanacak planladığınıza bağlı olarak, bir bölümü doğru derlenmiş ".mof" dosyaları yeniden adlandırmak için aşağıdaki seçebilirsiniz.

### <a name="configuration-ids-guid"></a>Yapılandırma Kimliği (GUID)

"Localhost.mof" dosyanızı yeniden adlandırmanız gerekir "<GUID>.mof" dosya. Rastgele bir sıra oluşturabilirsiniz **GUID** kullanarak veya aşağıdaki örneği kullanarak [yeni GUID](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet'i.

```powershell
[System.Guid]::NewGuid()
```

Örnek çıktı

```output
Guid
----
64856475-939e-41fb-aba5-4469f4006059
```

Ardından, kabul edilebilir herhangi bir yöntemi kullanarak ".mof" dosyanızı yeniden adlandırabilirsiniz. Aşağıdaki örnekte [öğeyi yeniden adlandır](/powershell/module/microsoft.powershell.management/rename-item) cmdlet'i.

```powershell
Rename-Item -Path .\localhost.mof -NewName '64856475-939e-41fb-aba5-4469f4006059.mof'
```

Kullanma hakkında daha fazla bilgi için **GUID'leri** ortamınızda bkz [planlama GUID'leri](/powershell/dsc/secureserver#guids).

### <a name="configuration-names"></a>Yapılandırma adları

"Localhost.mof" dosyanızı yeniden adlandırmanız gerekir "<Configuration Name>.mof" dosya. Aşağıdaki örnekte, önceki bölümde yapılandırma adı kullanılır. Ardından, kabul edilebilir herhangi bir yöntemi kullanarak ".mof" dosyanızı yeniden adlandırabilirsiniz. Aşağıdaki örnekte [öğeyi yeniden adlandır](/powershell/module/microsoft.powershell.management/rename-item) cmdlet'i.

```powershell
Rename-Item -Path .\localhost.mof -NewName 'GenericConfig.mof'
```

## <a name="create-the-checksum"></a>Sağlama toplamı oluşturma

Her ".mof" dosya ilişkili ".checksum" dosyasına sahip olacak şekilde gereksinimlerinize bir çekme sunucusu veya SMB paylaşımı üzerinde depolanır. Bu dosya, ilişkili ".mof" dosya değiştirildi ve yeniden indirilmesi gerektiğini bilmeniz istemcilerin izin verir.

Oluşturabileceğiniz bir **sağlama toplamı** ile [yeni DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) cmdlet'i. Ayrıca çalıştırabileceğiniz `New-DSCCheckSum` kullanarak dosyaları dizini karşı `-Path` parametresi. Bir sağlama toplamı zaten varsa, ile yeniden oluşturulması zorlayabilirsiniz `-Force` parametresi. Aşağıdaki örnek, önceki bölümde ".mof" dosyasını içeren bir dizinin belirtilmiş ve kullandığı `-Force` parametresi.

```powershell
New-DscChecksum -Path '.\' -Force
```

Hiçbir çıkış gösterilir, ancak artık görmelisiniz bir "<GUID or Configuration Name>. mof.checksum" dosya.

## <a name="where-to-store-mof-files-and-checksums"></a>MOF dosyaları ve sağlamalar depolanacağı konumu

### <a name="on-a-dsc-http-pull-server"></a>DSC HTTP çekme sunucusunda

Ayarladığınızda, HTTP çekme sunucusu açıklandığı şekilde [bir DSC HTTP çekme sunucusu ayarlama](pullServer.md), dizinler için belirttiğiniz **ModulePath** ve **Yapılandırmayolu** anahtarları. **Yapılandırmayolu** anahtar ".mof" dosyalar nerede depolanacağını belirtir. **Yapılandırmayolu** dosyaları ".mof" ve ".checksum" dosyaları burada depolanmalıdır gösterir.

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

SMB paylaşımı kullanmak üzere bir çekme istemcisi ayarlama, belirttiğiniz bir **ConfigurationRepositoryShare**. Tüm dosyaları ".mof" ve ".checksum" dosyaları ardından depolanması gereken **SourcePath** yer **ConfigurationRepositoryShare** blok.

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

## <a name="next-steps"></a>Sonraki Adımlar

Ardından, belirtilen yapılandırmayı almayı çekme istemcileri yapılandırmak isteyeceksiniz. Daha fazla bilgi için aşağıdaki kılavuzlara birine bakın:

- [Bir çekme yapılandırma kimliklerinin (v4) kullanarak istemcisi ayarlama](pullClientConfigId4.md)
- [Bir çekme yapılandırma kimliklerinin (v5) kullanarak istemcisi ayarlama](pullClientConfigId.md)
- [Bir çekme (v5) yapılandırma adlarını kullanarak istemcisi ayarlama](pullClientConfigNames.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Bir DSC SMB çekme sunucusu ayarlama](pullServerSmb.md)
- [Bir DSC HTTP çekme sunucusu ayarlama](pullServer.md)
- [Paket ve karşıya yükleme kaynakları için bir çekme sunucusu](package-upload-resources.md)
