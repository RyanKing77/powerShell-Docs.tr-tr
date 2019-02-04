---
ms.date: 12/12/2018
keywords: DSC, powershell, yapılandırma, Kurulum
title: Paket ve karşıya yükleme kaynakları için bir çekme sunucusu
ms.openlocfilehash: 29a62f96393a53c9e7da57a5e51732dcb0937194
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688808"
---
# <a name="package-and-upload-resources-to-a-pull-server"></a>Paket ve karşıya yükleme kaynakları için bir çekme sunucusu

Aşağıdaki bölümler, zaten bir çekme sunucusu ayarladığınızı varsayalım. Çekme sunucunuzu ayarlamadıysanız, aşağıdaki kılavuzları kullanabilirsiniz:

- [Bir DSC SMB çekme sunucusu ayarlama](pullServerSmb.md)
- [Bir DSC HTTP çekme sunucusu ayarlama](pullServer.md)

Her hedef düğüm yapılandırmaları, kaynaklar, indirin ve bile durumunu raporlamak için yapılandırılabilir. Bu makale indirilmesi ve kaynakları otomatik olarak indirmek için istemcileri yapılandırın kullanabilmesi için kaynakları karşıya yükleme işlemini gösterir. Düğümün aldığında atanmış bir yapılandırma yoluyla **çekme** veya **anında iletme** (v5) otomatik olarak karşıdan yüklerken LCM içinde belirtilen konumdan yapılandırma için gerekli tüm kaynakları.

## <a name="package-resource-modules"></a>Paket kaynak modülleri

Her kaynak indirmek bir istemci için kullanılabilen bir ".zip" dosyasında depolanmalıdır. Aşağıdaki örneği kullanarak gerekli adımları gösterilir [xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0) kaynak.

> [!NOTE]
> PowerShell 4.0 sürümünü kullanan istemcileri varsa, kaynak klasör yapısı için flaten gerekir ve sürüm klasörleri kaldırın. Daha fazla bilgi için [birden çok kaynak sürümü](../configurations/import-dscresource.md#multiple-resource-versions).

Herhangi bir yardımcı programını, komut dosyası veya tercih ettiğiniz yöntemi kullanarak kaynak dizini sıkıştırabilirsiniz. Windows içinde yapabilecekleriniz *sağ* "xPSDesiredStateConfiguration" dizin ve "Göndermek için" sonra "Sıkıştırılmış klasörü" seçin.

![Sağ tıklayın](../media/right-click.gif)

### <a name="naming-the-resource-archive"></a>Kaynak arşiv adlandırma

Kaynak arşiv şu biçimde adlandırılır gerekir:

```
{ModuleName}_{Version}.zip
```

Yukarıdaki örnekte, "xPSDesiredStateConfiguration.zip" olarak yeniden adlandırıldı "xPSDesiredStateConfiguration_8.4.4.0.zip" olmalıdır.

### <a name="create-checksums"></a>Sağlama toplamları oluşturma

Kaynak modülü sıkıştırılmış ve yeniden oluşturmanıza gerek bir **sağlama toplamı**.  **Sağlama toplamı** , istemci üzerindeki LCM tarafından kaynak değiştirildi ve yeniden indirilmesi gereken belirlemek için kullanılır. Oluşturabileceğiniz bir **sağlama toplamı** ile [yeni DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet'i, aşağıdaki örnekte gösterildiği gibi.

```powershell
New-DscChecksum -Path .\xPSDesiredStateConfiguration_8.4.4.0.zip
```

Hiçbir çıkış gösterilir, ancak artık "xPSDesiredStateConfiguration_8.4.4.0.zip.checksum" görmeniz gerekir. Ayrıca çalıştırabileceğiniz `New-DSCCheckSum` kullanarak dosyaları dizini karşı `-Path` parametresi. Bir sağlama toplamı zaten varsa, ile yeniden oluşturulması zorlayabilirsiniz `-Force` parametresi.

### <a name="where-to-store-resource-archives"></a>Kaynak arşivi depolanacağı konumu

#### <a name="on-a-dsc-http-pull-server"></a>DSC HTTP çekme sunucusunda

Ayarladığınızda, HTTP çekme sunucusu açıklandığı şekilde [bir DSC HTTP çekme sunucusu ayarlama](pullServer.md), dizinler için belirttiğiniz **ModulePath** ve **Yapılandırmayolu** anahtarları. **Yapılandırmayolu** anahtar ".mof" dosyalar nerede depolanacağını belirtir. **ModulePath** DSC kaynak modüllerin depolandığı gösterir.

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

#### <a name="on-an-smb-share"></a>Bir SMB paylaşımında

Belirttiyseniz bir **ResourceRepositoryShare**, kullanarak çekme istemcisi ayarlama arşivler ve sağlama toplamı olarak depoladığınızda **SourcePath** yer **ResourceRepositoryShare** blok.

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Configurations'
}

ResourceRepositoryShare SMBResourceServer
{
    SourcePath = '\\SMBPullServer\Resources'
}
```

Yalnızca belirtilen bir **ConfigurationRepositoryShare**, kullanarak çekme istemcisi ayarlama arşivler ve sağlama toplamı olarak depoladığınızda **SourcePath** yer  **ConfigurationRepositoryShare** blok.

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

#### <a name="updating-resources"></a>Kaynaklar güncelleştiriliyor

Arşivin adı sürüm numarasını değiştirmek veya yeni bir sağlama toplamı oluşturarak kaynaklarını güncelleştirmek için bir düğüm zorlayabilirsiniz. Çekme istemcisi daha yeni sürümleri gerekli kaynakları için kontrol eder, aynı zamanda kendi LCM yenilendiğinde sağlama, güncelleştirilmiş.

## <a name="see-also"></a>Ayrıca bkz.

- [Bir DSC SMB çekme sunucusu ayarlama](pullServerSmb.md)
- [Bir DSC HTTP çekme sunucusu ayarlama](pullServer.md)
