---
ms.date: 12/12/2018
keywords: DSC, powershell, yapılandırma, hizmet, Kurulum
title: Yapılandırma Yazma, Derleme ve Uygulama
ms.openlocfilehash: c884af9d92ac375457d6eb75d815ae9a9159e273
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795428"
---
> Şunun için geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0

# <a name="write-compile-and-apply-a-configuration"></a>Yapılandırma Yazma, Derleme ve Uygulama

Bu alıştırmada oluşturmak ve uygulamak başlangıçtan bitişe kadar bir Desired State Configuration ' nı (DSC) yapılandırma gösterilmektedir.
Aşağıdaki örnekte, yazma ve çok basit bir yapılandırmayı uygulamak öğreneceksiniz. Yapılandırma, yerel makinenizde "HelloWorld.txt" dosyasından sağlayacaktır. Dosyayı silerseniz, DSC, sonraki güncelleştirdiğinde yeniden oluşturur.

DSC nedir ve nasıl çalıştığını genel bakış için bkz: [Desired State Configuration geliştiriciler için genel bakış](../overview/overview.md).

## <a name="requirements"></a>Gereksinimler

Bu örneği çalıştırmak için PowerShell 4.0 veya sonraki sürümü çalıştıran bir bilgisayar gerekir.

## <a name="write-the-configuration"></a>Yapılandırmasını yazın

Bir DSC [yapılandırma](configurations.md) tanımlayan bir veya daha fazla hedef bilgisayarların (düğümlerin) yapılandırmak istediğiniz nasıl özel bir PowerShell işlevdir.

PowerShell ISE veya diğer PowerShell Düzenleyicisi, aşağıdaki komutu yazın:

```powershell
Configuration HelloWorld {

    # Import the module that contains the File resource.
    Import-DscResource -ModuleName PsDesiredStateConfiguration

    # The Node statement specifies which targets to compile MOF files for, when this configuration is executed.
    Node 'localhost' {

        # The File resource can ensure the state of files, or copy them from a source to a destination with persistent updates.
        File HelloWorld {
            DestinationPath = "C:\Temp\HelloWorld.txt"
            Ensure = "Present"
            Contents   = "Hello World from DSC!"
        }
    }
}
```

Dosyayı "HelloWorld.ps1" kaydedin.

Bir yapılandırma tanımlanması gibi bir işlevi tanımlayan olur. **Düğüm** blok belirtir, bu durumda yapılandırılması için hedef düğümü `localhost`.

Yapılandırma çağıran bir [kaynakları](../resources/resources.md), `File` kaynak. Kaynak hedef düğüm yapılandırması tarafından tanımlanmış durumda sağlayarak iş yapın.

## <a name="compile-the-configuration"></a>Yapılandırma derleme

DSC yapılandırması düğüme uygulanacak ilk MOF dosyasına derlenmelidir.
Bir işlev gibi bir yapılandırmayı çalıştırma derleme bir ".mof" dosyası tarafından tanımlanan her düğüm için `Node` blok.
Yapılandırma çalıştırmak için için gereken *nokta kaynak* "HelloWorld.ps1" betiğinizi geçerli kapsama.
Daha fazla bilgi için [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing).

<!-- markdownlint-disable MD038 -->
*Nokta kaynak* depolandığı, sonra yolunda yazarak "HelloWorld.ps1" betiğinizi `. ` (nokta, alan). Daha sonra olabilir gibi bir işlev çağırarak yapılandırmanızı çalıştırın.
<!-- markdownlint-enable MD038 -->

```powershell
. C:\Scripts\WebsiteTest.ps1
HelloWolrd
```

Bu, aşağıdaki çıktıyı oluşturur:

```output
Directory: C:\Scripts\HelloWorld


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

## <a name="apply-the-configuration"></a>Yapılandırmasını Uygula

Derlenmiş MOF olduğuna göre yapılandırma (Bu durumda, yerel bilgisayar) hedef düğüm çağırarak uygulayabileceğiniz [Başlat-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet'i.

`Start-DscConfiguration` Cmdlet'i söyler [yerel Configuration Manager'ı (LCM)](../managing-nodes/metaConfig.md), yapılandırmayı uygulamak için DSC, altyapı.
LCM yapılandırmayı uygulamak için DSC kaynakları çağırma çalışır.

Yürütmek için aşağıdaki kodu kullanın `Start-DSCConfiguration` cmdlet'i. İçin "localhost.mof" depolandığı dizin yolunu belirtin `-Path` parametresi. `Start-DSCConfiguration` Cmdlet'i görünüyor için belirtilen dizin aracılığıyla "\<computername\>.mof" dosyaları. `Start-DSCConfiguration` Filename ("localhost", "server01", "dc-02", vb.) tarafından belirtilen computername bulduğu her ".mof" dosyasını uygulamak cmdlet'i çalışır.

> [!NOTE]
> Varsa `-Wait` parametresi belirtilmezse, `Start-DSCConfiguration` işlemi gerçekleştirmek için bir arka plan işi oluşturur. Belirtme `-Verbose` parametresi, izlemek verir **ayrıntılı** işleminin çıktı. `-Wait`, ve `-Verbose` hem isteğe bağlı parametrelerdir.

```powershell
Start-DscConfiguration -Path C:\Scripts\HelloWorld -Verbose -Wait
```

## <a name="test-the-configuration"></a>Test yapılandırması

Bir kez `Start-DSCConfiguration` cmdlet tamamlandıktan sonra belirtilen konumda bir "HelloWorld.txt" dosyası görmeniz gerekir. İçeriğiyle doğrulayabilirsiniz [Get-Content](/powershell/module/microsoft.powershell.management/get-content) cmdlet'i.

Ayrıca *test* geçerli durumunu kullanma [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).

Düğümü şu anda uygulanan yapılandırma ile uyumlu ise çıktısı "True" olmalıdır.

```powershell
Test-DSCConfiguration
```

```output
True
```

```powershell
Get-Content -Path C:\Temp\HelloWorld.txt
```

```output
Hello World from DSC!
```

## <a name="re-applying-the-configuration"></a>Yapılandırmayı yeniden uygulanıyor

Yeniden uygulandığından yapılandırmanızı görmeyi, yapılandırma tarafından oluşturulan metin dosyasını kaldırabilirsiniz. Kullanımı `Start-DSCConfiguration` cmdlet'iyle `-UseExisting` parametresi. `-UseExisting` Parametresi `Start-DSCConfiguration` "current.mof" dosya yeniden Uygula için en son başarılı bir şekilde temsil eden yapılandırma uygulandı.

```powershell
Remove-Item -Path C:\Temp\HelloWorld.txt
```

## <a name="next-steps"></a>Sonraki adımlar

- DSC yapılandırmalar hakkında daha fazla bilgi edinin [DSC yapılandırmaları](configurations.md).
- Hangi DSC kaynakların kullanılabilir olduğundan ve özel DSC kaynakları oluşturmak nasıl [DSC kaynakları](../resources/resources.md).
- DSC yapılandırmaları ve kaynakları Bul [PowerShell Galerisi](https://www.powershellgallery.com/).
