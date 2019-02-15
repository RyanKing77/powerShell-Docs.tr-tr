---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: Hızlı Başlangıç - DSC ile bir Web sitesi oluşturma
ms.openlocfilehash: d98607939ccd3cc5e660936d8c0a6d54fce7d65f
ms.sourcegitcommit: 6ae5b50a4b3ffcd649de1525c3ce6f15d3669082
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2019
ms.locfileid: "56265493"
---
> Şunun için geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0

# <a name="quickstart---create-a-website-with-dsc"></a>Hızlı Başlangıç - DSC ile bir Web sitesi oluşturma

Bu alıştırmada oluşturma ve istenen durum Yapılandırması'nı (DSC) yapılandırma başlangıçtan bitişe kadar uygulama anlatılmaktadır.
Bir sunucu olduğunu kullanırız örnek sağlar `Web-Server` (IIS) özelliği etkin ve basit bir "Hello World" Web sitesi için içeriğin mevcut olduğunu `inetpub\wwwroot` o sunucunun dizin.

DSC nedir ve nasıl çalıştığı genel bakış için bkz: [istenen durum yapılandırması için genel bakış karar alıcılar](../overview/decisionMaker.md).

## <a name="requirements"></a>Gereksinimler

Bu örneği çalıştırmak için Windows Server 2012 veya sonraki sürümünü ve PowerShell 4.0 veya sonraki sürümü çalıştıran bir bilgisayar gerekir.

## <a name="write-and-place-the-indexhtm-file"></a>Yazma ve index.htm dosyasını yerleştirin

İlk olarak, Web sitesi içeriği olarak kullanacağız HTML dosyası oluşturacağız.

Kök klasörünüzde adlı bir klasör oluşturun `test`.

Bir metin Düzenleyicisi'nde, aşağıdaki metni yazın:

```html
<head></head>
<body>
<p>Hello World!</p>
</body>
```

Bu olarak Kaydet `index.htm` içinde `test` daha önce oluşturduğunuz klasör.

## <a name="write-the-configuration"></a>Yazma yapılandırması

A [DSC Yapılandırması](../configurations/configurations.md) tanımlayan bir veya daha fazla hedef bilgisayarların (düğümlerin) yapılandırmak istediğiniz nasıl özel bir PowerShell işlevdir.

PowerShell ISE aşağıdaki komutu yazın:

```powershell
Configuration WebsiteTest {

    # Import the module that contains the resources we're using.
    Import-DscResource -ModuleName PsDesiredStateConfiguration

    # The Node statement specifies which targets this configuration will be applied to.
    Node 'localhost' {

        # The first resource block ensures that the Web-Server (IIS) feature is enabled.
        WindowsFeature WebServer {
            Ensure = "Present"
            Name   = "Web-Server"
        }

        # The second resource block ensures that the website content copied to the website root folder.
        File WebsiteContent {
            Ensure = 'Present'
            SourcePath = 'c:\test\index.htm'
            DestinationPath = 'c:\inetpub\wwwroot'
        }
    }
}
```

Dosyayı Farklı Kaydet `WebsiteTest.ps1`.

Bir PowerShell işleviyle anahtar sözcüğü eklenmesi gibi görünüyor görebilirsiniz **yapılandırma** işlevi adı önce kullanıldı.

**Düğümü** blok belirtir, bu durumda yapılandırılması için hedef düğümü `localhost`.

Yapılandırmanın iki çağırır [kaynakları](../resources/resources.md), **WindowsFeature** ve **dosya**.
Kaynakları hedef düğüm yapılandırması tarafından tanımlanan durumda sağlama iş yapın.

## <a name="compile-the-configuration"></a>Yapılandırmayı derleme

DSC yapılandırması bir düğüme uygulanacak ilk MOF dosyasına derlenmelidir.
Bunu yapmak için yapılandırmanın bir işlev gibi çalıştırın.
Bir PowerShell konsolunda yapılandırmanızı kaydettiğiniz klasöre gidin ve bir MOF dosyasına yapılandırmayı derlemek için aşağıdaki komutları çalıştırın:

```powershell
. .\WebsiteTest.ps1
WebsiteTest
```

Şu çıkışı üretir:

```
Directory: C:\ConfigurationTest\WebsiteTest


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

İlk satırı yapılandırma işlevi konsolunda kullanılabilir hale getirir.
İkinci satır yapılandırması çalıştırılır.
Yeni bir klasör adında sonucudur `WebsiteTest` bir alt klasör geçerli klasörde oluşturulur.
`WebsiteTest` Adlı bir dosyayı içeren klasör `localhost.mof`.
Daha sonra hedef düğüme uygulanan bu dosyasıdır.

## <a name="apply-the-configuration"></a>Yapılandırmasını Uygula

Derlenmiş MOF sahip olduğunuza göre yapılandırma (Bu durumda, yerel bilgisayar) hedef düğüm çağırarak uygulayabileceğiniz [başlangıç DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet'i.

`Start-DscConfiguration` Cmdlet söyler [yerel Configuration Manager (LCM'yi)](../managing-nodes/metaConfig.md), yapılandırmayı uygulamak için DSC altyapısı olduğu.
Yapılandırmayı uygulamak için DSC kaynakları çağırma işini LCM'yi yapar.

Bir PowerShell konsolunda yapılandırmanızı kaydettiğiniz klasöre gidin ve aşağıdaki komutu çalıştırın:

```powershell
Start-DscConfiguration .\WebsiteTest
```

## <a name="test-the-configuration"></a>Yapılandırmayı test etme

Çağırabilirsiniz [Get-DscConfigurationStatus](/powershell/module/psdesiredstateconfiguration/get-dscconfigurationstatus) yapılandırmanın başarılı olup olmadığını görmek için cmdlet.

Ayrıca sonuçları doğrudan, bu durumda göz atarak sınayabilirsiniz `http://localhost/` bir web tarayıcısında.
Bu örnekte ilk adım olarak, oluşturduğunuz "Hello World" HTML sayfası görmeniz gerekir.

## <a name="next-steps"></a>Sonraki adımlar

- DSC yapılandırmaları hakkında daha fazla bilgi [DSC yapılandırmaları](../configurations/configurations.md).
- Hangi DSC kaynakları kullanılabilir ve özel DSC kaynakları oluşturma bkz [DSC kaynakları](../resources/resources.md).
- DSC yapılandırmaları ve kaynakları bulmak [PowerShell Galerisi](https://www.powershellgallery.com/).
