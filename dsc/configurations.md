---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "DSC yapılandırmaları"
ms.openlocfilehash: 3fdee72d5701433a3903697c5a0a32b112136592
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-configurations"></a>DSC yapılandırmaları

>İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0

DSC yapılandırmaları özel türde bir işlevi tanımlayan PowerShell betiklerdir. Bir yapılandırma tanımlamak için PowerShell anahtar sözcüğü kullanın **yapılandırma**.

```powershell
Configuration MyDscConfiguration {

    Node "TEST-PC1" {
        WindowsFeature MyFeatureInstance {
            Ensure = "Present"
            Name =  "RSAT"
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = "Present"
            Name = "Bitlocker"
        }
    }
} 

MyDscConfiguration 
```

Komut dosyasını bir .ps1 dosyası olarak kaydedin.

## <a name="configuration-syntax"></a>Yapılandırma sözdizimi

Bir yapılandırma betiğini aşağıdaki bölümlerden oluşur:

- **Yapılandırma** bloğu. Dış betik bloğu budur. Kullanarak tanımladığınız **yapılandırma** anahtar sözcüğü ve sağlayan bir adı. Bu durumda, yapılandırma "MyDscConfiguration" adıdır.
- Bir veya daha fazla **düğümü** engeller. Bunlar, yapılandırmakta olduğunuz düğümleri (bilgisayarların veya VM'ler) tanımlayın. Yukarıdaki yapılandırmada bir olduğundan **düğümü** "TEST-PC1" adlı bir bilgisayarı hedef blok.
- Bir veya daha fazla kaynak engeller. Burada yapılandırma özellikleri, yapılandırma kaynaklara ilişkin ayarlar budur. Bu durumda, her biri çağrısı "WindowsFeature" kaynak iki kaynak blokları vardır.

İçinde bir **yapılandırma** bloğu, normalde bir PowerShell işlevinde verebilir herhangi bir şey yapabilirsiniz. Örneğin, önceki örnekte, sabit yapılandırmasında, hedef bilgisayarın adını kod gelmedi istiyorsanız düğüm adı için bir parametre ekleyebilirsiniz:

```powershell
Configuration MyDscConfiguration {

    param(
        [string[]]$ComputerName="localhost"
    )
    Node $ComputerName {
        WindowsFeature MyFeatureInstance {
            Ensure = "Present"
            Name =  "RSAT"
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = "Present"
            Name = "Bitlocker"
        }
    }
}

MyDscConfiguration 
```

Bu örnekte, düğümün adı olarak geçirerek belirttiğiniz **ComputerName** yapılandırma derlediğinizde parametresi. Adı varsayılan olarak "localhost".

## <a name="compiling-the-configuration"></a>Yapılandırmayı derleme

Bir yapılandırma yürürlüğe önce bir MOF belgeye derleme gerekir. Bunun için bir PowerShell işlevi gibi yapılandırma çağırarak.  
Bu yapılandırma, yalnızca adını içeren örnek son satırının yapılandırma çağırır.

>**Not:** bir yapılandırma çağrılacak işlev genel kapsamda (işleviyle herhangi diğer PowerShell gibi) olmalıdır. 
>Bu durum ya da göre "nokta betik kaynak belirleme" hale getirebilir veya F5 kullanarak veya tıklayarak yapılandırma komut dosyası çalıştırarak **komut dosyasını Çalıştır** işe düğmesi. 
>Nokta kaynak için komut dosyası, komutu çalıştırmak `. .\myConfig.ps1` burada `myConfig.ps1` yapılandırmanızı içeren komut dosyası adıdır.

Bu yapılandırma, çağırdığınızda:

- Tüm değişkenleri çözümler 
- Geçerli dizinde yapılandırma olarak aynı ada sahip bir klasör oluşturur.
- Adlı bir dosya oluşturur _NodeName_yeni dizininde .mof nerede _NodeName_ hedef düğüm yapılandırmasının adı. 
    Birden fazla düğüm varsa, her düğüm için bir MOF dosyası oluşturulur.

>**Not**: MOF dosyası tüm hedef düğüm için yapılandırma bilgilerini içerir. Bu nedenle, daha güvenli tutmak önemlidir. 
>Daha fazla bilgi için bkz: [MOF dosyası güvenli hale getirme](secureMOF.md).

İlk yapılandırması aşağıdaki klasör yapısını sonuçlarında yukarıda derleme:

```powershell
. .\MyDscConfiguration.ps1
MyDscConfiguration
```

```
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name                                                                                              
----                -------------         ------ ----                                                                                         
-a----       10/23/2015   4:32 PM           2842 TEST-PC1.mof
```  

Yapılandırma ikinci örnekte olduğu gibi bir parametre alırsa, derleme zamanında sağlanması gerekir. İşte, nasıl görünür:

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

Yararlı bir DSC anahtar **DependsOn**. Genellikle (mutlaka rağmen), DSC kaynakları yapılandırma içinde göründükleri sırada uygulanır. Ancak, **DependsOn** belirten diğer kaynaklara bağımlı kaynaklar ve bunların hangi kaynak örnekleri tanımlanan sipariş bakılmaksızın doğru sırada uygulanan LCM'yi sağlar. Bir yapılandırma, örneğin, belirtebilir örneği **kullanıcı** kaynak bağlıdır varlığı üzerinde bir **grup** örneği:

```powershell
Configuration DependsOnExample {
    Node Test-PC1 {
        Group GroupExample {
            Ensure = "Present"
            GroupName = "TestGroup"
        }

        User UserExample {
            Ensure = "Present"
            UserName = "TestUser"
            FullName = "TestUser"
            DependsOn = "[Group]GroupExample"
        }
    }
}

DependsOnExample
```

## <a name="using-new-resources-in-your-configuration"></a>Yapılandırmanızda yeni kaynakları kullanma

Önceki örneklerde çalıştırdıysanız, açıkça almadan kaynak kullanmakta olduğunuz uyarı fark etmiş olabilirsiniz.
Bugün, DSC da PSDesiredStateConfiguration modülünün bir parçası olarak 12 kaynakları ile birlikte gelir. Dış modüllerindeki diğer kaynakları yerleştirilmelidir `$env:PSModulePath` tarafından LCM'yi tanınması için. Yeni bir cmdlet [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx), hangi kaynaklara göre LCM'yi sistemde yüklü ve kullanım için uygun olduğunu belirlemek için kullanılabilir. Bu modüller, yerleştirildi sonra `$env:PSModulePath` ve düzgün şekilde tarafından tanınan [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx), bunlar yine de yapılandırmanızı içinde yüklü olması gerekir. 
**İçeri aktarma DscResource** içinde yalnızca tanınmasını dinamik bir anahtar sözcüktür bir **yapılandırma** (yani olmadığı bir cmdlet) engelle. 
**İçeri aktarma DscResource** iki parametreleri destekler:
- **ModuleName** kullanmanın önerilen yöntem **alma DscResource**. Bu, (bir dize dizisi modül adlarını yanı sıra) içeri aktarılacak kaynakları içeren modülü adını kabul eder. 
- **Ad** almak için kaynak adıdır. Bu "Name" tarafından döndürülen kolay adı değil [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx), ancak kullanıldığında sınıf adı kaynak şemasını tanımlama (olarak döndürülen **ResourceType** tarafından [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx)). 

## <a name="see-also"></a>Ayrıca bkz:
* [Windows PowerShell istenen durum yapılandırması genel bakış](overview.md)
* [DSC kaynakları](resources.md)
* [Yerel Yapılandırma Yöneticisi'ni yapılandırma](metaConfig.md)

