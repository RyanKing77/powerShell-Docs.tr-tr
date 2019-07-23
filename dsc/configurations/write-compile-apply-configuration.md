---
ms.date: 12/12/2018
keywords: DSC, PowerShell, yapılandırma, hizmet, kurulum
title: Yapılandırma Yazma, Derleme ve Uygulama
ms.openlocfilehash: 8bcd55518b0409b9a4b02ca95f027a0a77eb5300
ms.sourcegitcommit: 118eb294d5a84a772e6449d42a9d9324e18ef6b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/22/2019
ms.locfileid: "68372186"
---
> Şunun için geçerlidir: Windows PowerShell 4,0, Windows PowerShell 5,0

# <a name="write-compile-and-apply-a-configuration"></a>Yapılandırma Yazma, Derleme ve Uygulama

Bu alıştırma, başlangıçtan sonuna kadar Istenen durum yapılandırması (DSC) yapılandırması oluşturma ve uygulamayı adım adım göstermektedir.
Aşağıdaki örnekte, çok basit bir yapılandırmanın nasıl yazılacağını ve uygulanacağını öğreneceksiniz. Yapılandırma, yerel makinenizde bir "HelloWorld. txt" dosyasının var olduğundan emin olur. Dosyayı silerseniz, DSC bir sonraki güncelleştirilişinde onu yeniden oluşturur.

DSC 'nin ne olduğu ve nasıl çalıştığı hakkında genel bir bakış için, bkz. [geliştiriciler Için Istenen durum yapılandırmasına genel bakış](../overview/overview.md).

## <a name="requirements"></a>Gereksinimler

Bu örneği çalıştırmak için PowerShell 4,0 veya sonraki bir sürümünü çalıştıran bir bilgisayara ihtiyacınız olacaktır.

## <a name="write-the-configuration"></a>Yapılandırmayı yazma

DSC [yapılandırması](configurations.md) , bir veya daha fazla hedef bilgisayar (düğüm) yapılandırmak istediğinizi tanımlayan özel bir PowerShell işlevidir.

PowerShell ıSE veya başka bir PowerShell düzenleyicisinde aşağıdakini yazın:

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

> ! Aynı yapılandırmada birçok DSC kaynaklarıyla çalışabilmek için birden çok modülün içeri aktarılması gereken daha Gelişmiş senaryolarda, her modülün kullanarak `Import-DscResource`ayrı bir satıra yerleştirdiğinizden emin olun.
> Bu, kaynak denetiminde bakım yapmak ve Azure Durum Yapılandırması 'nda DSC ile çalışırken gereklidir.
>
> ```powershell
>  Configuration HelloWorld {
>
>   # Import the module that contains the File resource.
>   Import-DscResource -ModuleName PsDesiredStateConfiguration
>   Import-DscResource -ModuleName xWebAdministration
>
> ```

Dosyayı "HelloWorld. ps1" olarak kaydedin.

Bir yapılandırma tanımlamak bir Işlevi tanımlamaya benzer. **Düğüm** bloğu, bu durumda `localhost`yapılandırılacak hedef düğümü belirtir.

Yapılandırma [tek bir](../resources/resources.md)kaynağı, `File` kaynağı çağırır. Kaynaklar, hedef düğümün yapılandırma tarafından tanımlanan durumda olmasını sağlamaya çalışır.

## <a name="compile-the-configuration"></a>Yapılandırmayı derle

Bir DSC yapılandırmasının bir düğüme uygulanması için öncelikle bir MOF dosyasına derlenmesi gerekir.
Bir işlev gibi yapılandırmayı çalıştırmak, `Node` blok tarafından tanımlanan her düğüm için bir ". mof" dosyası derler.
Yapılandırmayı çalıştırmak için, geçerli kapsamda "HelloWorld. ps1" betiğinizin *kaynağını* yazmanız gerekir.
Daha fazla bilgi için bkz. [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing).

<!-- markdownlint-disable MD038 -->
*Nokta kaynağı* "HelloWorld. ps1" betiğinizi, depoladığınız yolu `. ` (nokta, boşluk) sonra yazarak yazın. Daha sonra, bir Işlev gibi çağırarak yapılandırmanızı çalıştırabilirsiniz.
<!-- markdownlint-enable MD038 -->

```powershell
. C:\Scripts\HelloWorld.ps1
HelloWorld
```

Bu, aşağıdaki çıktıyı oluşturur:

```output
Directory: C:\Scripts\HelloWorld


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

## <a name="apply-the-configuration"></a>Yapılandırmayı Uygula

Artık derlenmiş MOF 'ye sahip olduğunuza göre, [Başlangıç-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet 'ini çağırarak yapılandırmayı hedef düğüme (Bu durumda yerel bilgisayar) uygulayabilirsiniz.

Cmdlet 'i, yapılandırmayı uygulamak için [yerel Configuration Manager (LCM)](../managing-nodes/metaConfig.md), DSC altyapısını söyler. `Start-DscConfiguration`
LCM, yapılandırmayı uygulamak için DSC kaynaklarını çağırma işini yapar.

`Start-DSCConfiguration` Cmdlet 'ini yürütmek için aşağıdaki kodu kullanın. "Localhost. mof" `-Path` parametresinin parametreye depolandığı dizin yolunu belirtin. Cmdlet 'i herhangi bir "\<ComputerName\>. mof" dosyası için belirtilen dizine bakar. `Start-DSCConfiguration` `Start-DSCConfiguration` Cmdlet 'i, bulduğu her ". mof" dosyasını dosya adı ("localhost", "Server01", "DC-02" vb.) tarafından belirtilen ComputerName 'a uygulamayı dener.

> [!NOTE]
> Parametresi belirtilmemişse, `Start-DSCConfiguration` işlemi gerçekleştirmek için bir arka plan işi oluşturur. `-Wait` Parametresinin **belirtilmesi** işlemin ayrıntılı çıkışını izlemenize olanak sağlar. `-Verbose` `-Wait`, ve `-Verbose` isteğe bağlı parametrelerdir.

```powershell
Start-DscConfiguration -Path C:\Scripts\HelloWorld -Verbose -Wait
```

## <a name="test-the-configuration"></a>Yapılandırmayı test etme

`Start-DSCConfiguration` Cmdlet tamamlandıktan sonra, belirttiğiniz konumda bir "HelloWorld. txt" dosyası görmeniz gerekir. İçeriği [Get-Content](/powershell/module/microsoft.powershell.management/get-content) cmdlet 'i ile doğrulayabilirsiniz.

Ayrıca, [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)kullanarak geçerli durumu *Test* edebilirsiniz.

Düğüm, uygulanan yapılandırmayla uyumluysa, çıkış "true" olmalıdır.

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

## <a name="re-applying-the-configuration"></a>Yapılandırma yeniden uygulanıyor

Yapılandırmanızın yeniden uygulandığını görmek için, yapılandırmanız tarafından oluşturulan metin dosyasını kaldırabilirsiniz. `Start-DSCConfiguration` Cmdlet 'ini`-UseExisting` parametresiyle kullanın. Parametresi, en son başarıyla uygulanan yapılandırmayı temsil eden "Current. mof" dosyasını yeniden uygulamaya yönlendirir `Start-DSCConfiguration`. `-UseExisting`

```powershell
Remove-Item -Path C:\Temp\HelloWorld.txt
```

## <a name="next-steps"></a>Sonraki adımlar

- DSC yapılandırmalarında DSC yapılandırması hakkında daha fazla bilgi [edinin.](configurations.md)
- Hangi DSC kaynaklarının kullanılabilir olduğunu ve [DSC kaynaklarında](../resources/resources.md)özel DSC kaynakları oluşturmayı öğrenin.
- [POWERSHELL GALERISI](https://www.powershellgallery.com/)DSC yapılandırma ve kaynaklarını bulun.
