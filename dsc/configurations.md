---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC yapılandırmaları
ms.openlocfilehash: 171068acb51f44e31c81e63f6640222ef71bee38
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093703"
---
# <a name="dsc-configurations"></a>DSC yapılandırmaları

> Uygulama hedefi: Windows PowerShell 4.0, Windows PowerShell 5.0

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

Komut dosyasını bir .ps1 dosyası olarak kaydedin.

## <a name="configuration-syntax"></a>Yapılandırma sözdizimi

Bir yapılandırma betiği aşağıdaki bölümden oluşur:

- **Yapılandırma** blok. Dış betik bloğundaki budur. Kullanarak tanımladığınız **yapılandırma** anahtar sözcüğü ve bir ad sağlar. Bu durumda, yapılandırma "MyDscConfiguration" adıdır.
- Bir veya daha fazla **düğüm** engeller. Bunlar, yapılandırmakta olduğunuz düğüm (bilgisayarların veya Vm'leri) tanımlar. Yukarıdaki yapılandırmada, bir tane olduğunu **düğüm** bir bilgisayarı hedef blok, "TEST-PC1" adlı.
- Bir veya daha fazla kaynak engeller. Burada, yapılandırma kaynaklarını özelliklerini yapılandırmayı ayarlar budur. Bu durumda, iki kaynak blok, her biri "WindowsFeature" kaynak çağrısı vardır.

İçinde bir **yapılandırma** blok, normalde bir PowerShell işlevde verebilecek her şeyi yapabilirsiniz. Örneğin, önceki örnekte sabit yapılandırmasında, hedef bilgisayarın adını kod gelmedi isterseniz düğüm adı için bir parametre ekleyebilirsiniz:

```powershell
Configuration MyDscConfiguration {
    param(
        [string[]]$ComputerName='localhost'
    )
    Node $ComputerName {
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
MyDscConfiguration -ComputerName $ComputerName
```

Bu örnekte, düğümün adı olarak geçirerek belirttiğiniz **ComputerName** yapılandırma derlediğinizde parametresi. Adı varsayılan olarak "localhost".

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
> Daha fazla bilgi için [MOF dosyasının güvenliğini sağlama](secureMOF.md).

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

## <a name="using-dependson"></a>DependsOn kullanma

Yararlı bir DSC anahtar sözcüğü **DependsOn**. Genellikle (mutlaka rağmen), DSC kaynakları içine yapılandırmayı göründükleri sırayla uygulanır.
Ancak, **DependsOn** belirten bağımlı kaynaklar diğer kaynaklara ve bunlar hangi kaynak örnekleri tanımlanmış sırasını bağımsız olarak doğru sırayla uygulanır LCM sağlar.
Örneğin, bir yapılandırma, belirtebilirsiniz örneği **kullanıcı** kaynak varlığını bağlıdır bir **grubu** örneği:

```powershell
Configuration DependsOnExample {
    Node Test-PC1 {
        Group GroupExample {
            Ensure = 'Present'
            GroupName = 'TestGroup'
        }

        User UserExample {
            Ensure = 'Present'
            UserName = 'TestUser'
            FullName = 'TestUser'
            DependsOn = '[Group]GroupExample'
        }
    }
}
```

## <a name="using-new-resources-in-your-configuration"></a>Yapılandırmanızda yeni kaynakları kullanma

Önceki örneklerde çalıştırdıysanız, açıkça içeri aktarmadan bir kaynağı kullanmakta olduğunuz uyarı fark etmiş olabilirsiniz.
Bugün, DSC ile 12 kaynağı da PSDesiredStateConfiguration modülün bir parçası gelir.
Diğer kaynakları harici modüllerdeki yerleştirilmelidir `$env:PSModulePath` LCM tarafından tanınması için.
Yeni bir cmdlet [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), sistemde yüklenmiş ve kullanıma göre LCM hangi kaynakların belirlemek için kullanılabilir.
Bu modüller, yerleştirildi sonra `$env:PSModulePath` ve tarafından tanınır [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), bunların hala yapılandırmanızı içinde yüklü olması gerekir.
**Import-DscResource** içinde yalnızca tanınabilmesi dinamik bir anahtar sözcüğü bir **yapılandırma** blok (yani olmadığı bir cmdlet'i).
**Import-DscResource** iki parametrelerini destekler:

- **ModuleName** kullanmanın önerilen yöntem **Import-DscResource**. Bu, (bir dize dizisi modülü adlarının yanı sıra) içeri aktarılacak kaynakları içeren modül adını kabul eder.
- **Adı** alınacak kaynağın adı. Bu kolay adı "Name" döndürdüğü değil [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), ancak kullanıldığında sınıf adı kaynak şemasını tanımlama (olarak döndürülen **ResourceType** tarafından [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx)).

## <a name="see-also"></a>Ayrıca bkz:

- [Windows PowerShell Desired State Configuration ' ne genel bakış](overview.md)
- [DSC kaynakları](resources.md)
- [Yerel Configuration Manager'ı yapılandırma](metaConfig.md)