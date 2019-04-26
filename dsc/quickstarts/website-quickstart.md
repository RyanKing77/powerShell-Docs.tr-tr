---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: Hızlı Başlangıç - DSC ile bir Web sitesi oluşturma
ms.openlocfilehash: d98607939ccd3cc5e660936d8c0a6d54fce7d65f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079133"
---
> Uygulama hedefi: Windows PowerShell 4.0, Windows PowerShell 5.0

# <a name="quickstart---create-a-website-with-dsc"></a>Hızlı Başlangıç - DSC ile bir Web sitesi oluşturma

Bu alıştırmada oluşturmak ve uygulamak başlangıçtan bitişe kadar bir Desired State Configuration ' nı (DSC) yapılandırma gösterilmektedir.
Kullanacağız örnek bir sunucuya sahip olmasını sağlar `Web-Server` (IIS) özelliği etkin ve basit bir "Hello World" Web sitesi için içeriğin mevcut olduğu `inetpub\wwwroot` sunucusunun dizin.

DSC nedir ve nasıl çalıştığını genel bakış için bkz: [karar alıcılar için genel Desired State Configuration](../overview/decisionMaker.md).

## <a name="requirements"></a>Gereksinimler

Bu örneği çalıştırmak için Windows Server 2012 veya sonraki sürümünü ve PowerShell 4.0 veya sonraki sürümü çalıştıran bir bilgisayar gerekir.

## <a name="write-and-place-the-indexhtm-file"></a>Yazma ve index.htm dosyası yerleştirin

İlk olarak, Web sitesi içeriği olarak kullanacağız HTML dosyası oluşturacağız.

Kök klasörünüzde adlı bir klasör oluşturun `test`.

Bir metin düzenleyicisinde, aşağıdaki metni yazın:

```html
<head></head>
<body>
<p>Hello World!</p>
</body>
```

Bu olarak Kaydet `index.htm` içinde `test` daha önce oluşturduğunuz klasör.

## <a name="write-the-configuration"></a>Yapılandırmasını yazın

A [DSC Yapılandırması](../configurations/configurations.md) tanımlayan bir veya daha fazla hedef bilgisayarların (düğümlerin) yapılandırmak istediğiniz nasıl özel bir PowerShell işlevdir.

PowerShell ISE'de aşağıdaki komutu yazın:

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

Anahtar sözcüğü ile birlikte bir PowerShell işlevi gibi görünüyor görebilirsiniz **yapılandırma** işlevin adını önce kullanılır.

**Düğüm** blok belirtir, bu durumda yapılandırılması için hedef düğümü `localhost`.

İki yapılandırma çağırır [kaynakları](../resources/resources.md), **WindowsFeature** ve **dosya**.
Kaynak hedef düğüm yapılandırması tarafından tanımlanmış durumda sağlayarak iş yapın.

## <a name="compile-the-configuration"></a>Yapılandırma derleme

DSC yapılandırması düğüme uygulanacak ilk MOF dosyasına derlenmelidir.
Bunu yapmak için yapılandırmanın bir işlev gibi çalıştırın.
Bir PowerShell konsolunda yapılandırmanızı kaydettiğiniz klasöre gidin ve bir MOF dosyasına yapılandırmayı derlemek için aşağıdaki komutları çalıştırın:

```powershell
. .\WebsiteTest.ps1
WebsiteTest
```

Bu, aşağıdaki çıktıyı oluşturur:

```
Directory: C:\ConfigurationTest\WebsiteTest


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

İlk satırı yapılandırma işlevi konsolunda kullanılabilir hale getirir.
İkinci satır yapılandırması çalıştırılır.
Adlı yeni bir klasörün sonucudur `WebsiteTest` bir alt klasör geçerli klasörde oluşturulur.
`WebsiteTest` Klasör adlı dosyayı içeren `localhost.mof`.
Ardından hedef düğüme uygulanan bu dosyasıdır.

## <a name="apply-the-configuration"></a>Yapılandırmasını Uygula

Derlenmiş MOF olduğuna göre yapılandırma (Bu durumda, yerel bilgisayar) hedef düğüm çağırarak uygulayabileceğiniz [Başlat-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet'i.

`Start-DscConfiguration` Cmdlet'i söyler [yerel Configuration Manager'ı (LCM)](../managing-nodes/metaConfig.md), yapılandırmayı uygulamak için DSC, altyapı olduğu.
LCM yapılandırmayı uygulamak için DSC kaynakları çağırma çalışır.

Bir PowerShell konsolunda yapılandırmanızı kaydettiğiniz klasöre gidin ve aşağıdaki komutu çalıştırın:

```powershell
Start-DscConfiguration .\WebsiteTest
```

## <a name="test-the-configuration"></a>Test yapılandırması

Çağırabilirsiniz [Get-DscConfigurationStatus](/powershell/module/psdesiredstateconfiguration/get-dscconfigurationstatus) Yapılandırması başarılı olup olmadığını görmek için cmdlet.

Ayrıca sonuçları doğrudan, bu durumda göz atarak sınayabilirsiniz `http://localhost/` bir web tarayıcısında.
Bu örnekte ilk adım olarak, oluşturduğunuz "Hello World" HTML sayfası görmeniz gerekir.

## <a name="next-steps"></a>Sonraki adımlar

- DSC yapılandırmalar hakkında daha fazla bilgi edinin [DSC yapılandırmaları](../configurations/configurations.md).
- Hangi DSC kaynakların kullanılabilir olduğundan ve özel DSC kaynakları oluşturmak nasıl [DSC kaynakları](../resources/resources.md).
- DSC yapılandırmaları ve kaynakları Bul [PowerShell Galerisi](https://www.powershellgallery.com/).
