---
ms.date: 12/12/2018
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC yapılandırmaları
ms.openlocfilehash: 6af27f442de3080facd65892c713c989d0e388c5
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405777"
---
# <a name="dsc-configurations"></a>DSC yapılandırmaları

> Şunun için geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0

DSC, özel bir işlev türü tanımlayan PowerShell betiklerini yapılandırmalardır.
Bir yapılandırmasını tanımlamak için PowerShell anahtar sözcüğünü kullanın. **yapılandırma**.

```powershell
Configuration MyDscConfiguration {
    Node "TEST-PC1" {
        WindowsFeature MyFeatureInstance {
            Ensure = 'Present'
            Name = 'RSAT'
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}
MyDscConfiguration
```

Betik olarak Kaydet bir `.ps1` dosya.

## <a name="configuration-syntax"></a>Yapılandırma sözdizimi

Bir yapılandırma betiği aşağıdaki bölümden oluşur:

- **Yapılandırma** blok. Dış betik bloğundaki budur. Kullanarak tanımladığınız **yapılandırma** anahtar sözcüğü ve bir ad sağlar. Bu durumda, yapılandırma "MyDscConfiguration" adıdır.
- Bir veya daha fazla **düğüm** engeller. Bunlar, yapılandırmakta olduğunuz düğüm (bilgisayarların veya Vm'leri) tanımlar. Yukarıdaki yapılandırmada, bir tane olduğunu **düğüm** bir bilgisayarı hedef blok, "TEST-PC1" adlı. Düğümü blok birden çok bilgisayar adlarını kabul edebilir.
- Bir veya daha fazla kaynak engeller. Burada, yapılandırma kaynaklarını özelliklerini yapılandırmayı ayarlar budur. Bu durumda, iki kaynak blok, her biri "WindowsFeature" kaynak çağrısı vardır.

İçinde bir **yapılandırma** blok, normalde bir PowerShell işlevde verebilecek her şeyi yapabilirsiniz. Örneğin, önceki örnekte sabit yapılandırmasında, hedef bilgisayarın adını kod gelmedi isterseniz düğüm adı için bir parametre ekleyebilirsiniz:

Bu örnekte, düğümün adı olarak geçirerek belirttiğiniz **ComputerName** yapılandırma derlediğinizde parametresi. Adı varsayılan olarak "localhost".

```powershell
Configuration MyDscConfiguration
{
    param
    (
        [string[]]$ComputerName='localhost'
    )

    Node $ComputerName
    {
        WindowsFeature MyFeatureInstance
        {
            Ensure = 'Present'
            Name = 'RSAT'
        }

        WindowsFeature My2ndFeatureInstance
        {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}

MyDscConfiguration
```

**Düğüm** blok birden çok bilgisayar adları da kabul edebilir. Yukarıdaki örnekte kullanabilir `-ComputerName` parametresi veya doğrudan bilgisayarlara geçişi bir virgülle ayrılmış listesi **düğüm** blok.

```powershell
MyDscConfiguration -ComputerName "localhost", "Server01"
```

Bilgisayarlara listesini belirtirken **düğüm** blok, gelen bir yapılandırması dizi gösterimi kullanmanız gerekir.

```powershell
Configuration MyDscConfiguration
{
    Node @('localhost', 'Server01')
    {
        WindowsFeature MyFeatureInstance
        {
            Ensure = 'Present'
            Name = 'RSAT'
        }

        WindowsFeature My2ndFeatureInstance
        {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}

MyDscConfiguration
```

## <a name="compiling-the-configuration"></a>Yapılandırma derleme

Bir yapılandırma yürürlüğe koymasına önce MOF belgeye derlemeniz gerekir.
Bunun için bir PowerShell işlevini çağırırdı gibi yapılandırma çağırarak.
Yalnızca yapılandırma adını içeren örnek son satırının yapılandırma çağırır.

> [!NOTE]
> Bir yapılandırma çağırmak için işlev genel kapsamda (ile diğer PowerShell bir işlev gibi) olmalıdır.
> Bu sorun ya da göre "nokta betik kaynak belirleme" hale getirebilir veya F5'i kullanarak ya da tıklandığında yapılandırma betiğini çalıştırarak **betiğini Çalıştır** işe düğmesi.
> Nokta kaynak için betik komutu çalıştırmak `. .\myConfig.ps1` burada `myConfig.ps1` yapılandırmanızı içeren betik dosyasının adıdır.

Bu yapılandırma, çağırdığınızda bu:

- Tüm değişkenler çözümler
- Geçerli dizin yapılandırma olarak aynı ada sahip bir klasör oluşturur.
- Adlı bir dosya oluşturur _NodeName_.mof yeni dizininde nereye _NodeName_ hedef düğüm yapılandırmasının adı.
  Birden fazla düğüm varsa, her düğüm için bir MOF dosyası oluşturulur.

> [!NOTE]
> MOF dosyası tüm hedef düğüm için yapılandırma bilgilerini içerir. Bu nedenle, güvenliğini sağlamak önemlidir.
> Daha fazla bilgi için [MOF dosyasının güvenliğini sağlama](../pull-server/secureMOF.md).

İlk yapılandırması aşağıdaki klasör yapısındaki sonuçları yukarıda derleme:

```powershell
. .\MyDscConfiguration.ps1
MyDscConfiguration
```

```
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       10/23/2015   4:32 PM           2842 localhost.mof
```

Yapılandırma ikinci örnekte olduğu gibi bir parametre alırsa, derleme zamanında sağlanması gerekir. Bu nasıl görüneceğini aşağıda verilmiştir:

```powershell
. .\MyDscConfiguration.ps1
MyDscConfiguration -ComputerName 'MyTestNode'
```

```
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       10/23/2015   4:32 PM           2842 MyTestNode.mof
```

## <a name="using-new-resources-in-your-configuration"></a>Yapılandırmanızda yeni kaynakları kullanma

Önceki örneklerde çalıştırdıysanız, açıkça içeri aktarmadan bir kaynağı kullanmakta olduğunuz uyarı fark etmiş olabilirsiniz.
Bugün, DSC ile 12 kaynağı da PSDesiredStateConfiguration modülün bir parçası gelir.

Cmdlet'in [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), sistemde yüklenmiş ve kullanıma göre LCM hangi kaynakların belirlemek için kullanılabilir.
Bu modüller, yerleştirildi sonra `$env:PSModulePath` ve tarafından tanınır [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), bunların hala yapılandırmanızı içinde yüklü olması gerekir.

**Import-DscResource** içinde yalnızca tanınabilmesi dinamik bir anahtar sözcüğü bir **yapılandırma** blok, bir cmdlet değildir.
**Import-DscResource** iki parametrelerini destekler:

- **ModuleName** kullanmanın önerilen yöntem **Import-DscResource**. Bu, (bir dize dizisi modülü adlarının yanı sıra) içeri aktarılacak kaynakları içeren modül adını kabul eder.
- **Adı** alınacak kaynağın adı. Bu kolay adı "Name" döndürdüğü değil [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), ancak kullanıldığında sınıf adı kaynak şemasını tanımlama (olarak döndürülen **ResourceType** tarafından [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)).

Kullanma hakkında daha fazla bilgi için `Import-DSCResource`, bkz: [Import-DSCResource kullanma](import-dscresource.md)

## <a name="powershell-v4-and-v5-differences"></a>PowerShell v4 ve v5 farklılıkları

DSC kaynakları PowerShell 4. 0'depolanması gereken yere farklar vardır. Daha fazla bilgi için [kaynak konumu](import-dscresource.md#resource-location).

## <a name="see-also"></a>Ayrıca bkz:

- [Windows PowerShell Desired State Configuration ' ne genel bakış](../overview/overview.md)
- [DSC kaynakları](../resources/resources.md)
- [Yerel Configuration Manager'ı yapılandırma](../managing-nodes/metaConfig.md)
