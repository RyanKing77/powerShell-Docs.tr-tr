---
title: PowerShell modülünü yükleme | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb82827e-fdb7-4cbf-b3d4-093e72b3ff0e
caps.latest.revision: 28
ms.openlocfilehash: 60ac4bf9089232a9fa879e835e32da53422489fd
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229444"
---
# <a name="installing-a-powershell-module"></a>PowerShell Modülü Yükleme

PowerShell modülü oluşturduktan sonra böylece sizin veya başkalarının kullanabilir, büyük olasılıkla bir sistemde modülünü yüklemek isteyebilirsiniz. Genel olarak bakıldığında, bu Modülü (IE, .psm1 veya ikili bir birleştirme, modül bildirimi ve ilişkili diğer dosyalar) .iso dosyalarını bir dizin o bilgisayardaki kopyalama oluşur. Çok küçük bir proje için bu kopyalama ve yapıştırma Windows Gezgini'ni kullanarak dosyaları tek bir uzak bilgisayara olarak basit olabilir. Ancak, daha büyük çözümler için daha karmaşık bir yükleme işlemi kullanmak isteyebilirsiniz. Modülünüzün sisteme nereden bağımsız olarak PowerShell çeşitli bulabilir ve modüllerinizi bilgilendirir teknikler kullanabilirsiniz. Bu nedenle, yükleme için ana sorunu PowerShell modülünüzde bulamadı olacağını sağlamaktır. Daha fazla bilgi için [PowerShell modülünü içeri aktararak](./importing-a-powershell-module.md).

## <a name="rules-for-installing-modules"></a>Modülleri yüklemek için kurallar

Aşağıdaki bilgileri kullanın, başka bir taraftan size modülleri ve başkalarına dağıttığınız modüller için oluşturduğunuz modülleri dahil olmak üzere tüm modülleri ile ilgilidir.

### <a name="install-modules-in-psmodulepath"></a>İçinde PSModulePath modülleri yükleme

Mümkün olduğunda, listelenen bir yolda tüm modülleri yükleme **PSModulePath** ortam değişkeni veya modül yola ekleyin **PSModulePath** ortam değişken değeri.

**PSModulePath** ortam değişkeni ($Env: PSModulePath) Windows PowerShell modülleri konumları içerir. Cmdlet modülleri bulmak için bu ortam değişkeninin değeri kullanır.

Varsayılan olarak, **PSModulePath** ortam değişken değerini, aşağıdaki sistem ve kullanıcı modülü dizini içeriyor, ancak ekleyin ve değerini düzenleyin.

- `$PSHome\Modules` (%Windir%\System32\WindowsPowerShell\v1.0\Modules)

  > [!WARNING]
  > Bu konum, Windows ile birlikte gelen modüller için ayrılmıştır. Modüller, bu konuma yüklemeyin.

- `$Home\Documents\WindowsPowerShell\Modules` (% UserProfile%\Documents\WindowsPowerShell\Modules)

- `$Env:ProgramFiles\WindowsPowerShell\Modules` (%ProgramFiles%\WindowsPowerShell\Modules)

  Değeri alınacak **PSModulePath** ortam değişkeni, aşağıdaki komutlardan birini kullanın.

  ```powershell
  $Env:PSModulePath
  [Environment]::GetEnvironmentVariable("PSModulePath")
  ```

  Modül yolu değerine eklenecek **PSModulePath** ortam değişkeni değeri, komutu aşağıdaki biçimi kullanın. Bu biçimi kullanan **SetEnvironmentVariable** yöntemi **System.Environment** oturumu bağımsız değişiklik için sınıf **PSModulePath** ortamı değişken.

  ```powershell
  #Save the current value in the $p variable.
  $p = [Environment]::GetEnvironmentVariable("PSModulePath")

  #Add the new path to the $p variable. Begin with a semi-colon separator.
  $p += ";C:\Program Files (x86)\MyCompany\Modules\"

  #Add the paths in $p to the PSModulePath value.
  [Environment]::SetEnvironmentVariable("PSModulePath",$p)

  ```

  > [!IMPORTANT]
  > Yolu ekledikten sonra **PSModulePath**, değişikliği hakkında bir ortam iletisi yayın. Değişiklik yayın değişiklikleri alması diğer uygulamaları gibi Kabuk sağlar. Değişiklik yayınlamak için ürün yükleme kodunuzu göndermek sahip bir **WM_SETTINGCHANGE** ile ileti `lParam` "Ortam" dizeye ayarlayın. Modül yükleme kodunuzu güncelleştirdi sonra iletiyi göndermeyi unutmayın **PSModulePath**.

### <a name="use-the-correct-module-directory-name"></a>Doğru modül dizin adı kullanın

İyi biçimlendirilmiş bir modül temel modül dizinde en az bir dosya adı ile aynı ada sahip bir dizini içinde depolanan bir modüldür. Bir modül doğru biçimlendirilmemiş, Windows PowerShell, bir modül olarak algılamaz.

"Temel"dosyasının adı, dosya adı uzantısı olmadan adıdır. İyi biçimlendirilmiş bir modülde modülü dosyalarını içeren dizin adını temel modülünde en az bir dosya adı eşleşmelidir.

Örneğin, örnek Fabrikam modülü, modül dosyaları içeren dizine "Fabrikam" olarak adlandırılır ve en az bir dosya "Fabrikam" temel adına sahip. Bu durumda, Fabrikam.psd1 hem Fabrikam.dll "Fabrikam" temel adına sahip.

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

### <a name="effect-of-incorrect-installation"></a>Yanlış yükleme etkisi

Modül doğru biçimlendirilmemiş ve konumuna değerinde bulunmayan **PSModulePath** ortam değişkeni, Windows PowerShell temel bulma özelliklerini aşağıdaki gibi çalışmaz.

- Modül Otomatik Yükleme özelliğini otomatik olarak modül içeri aktarılamıyor.

- `ListAvailable` Parametresinin [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet modülü bulunamıyor.

- [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet modülü bulunamıyor. Modülü içeri aktarmak için kök modül dosyası veya modül bildirim dosyası tam yolunu belirtmeniz gerekir.

  Aşağıdaki gibi ek özellikler modülün oturuma aktarılır sürece çalışmaz. İyi biçimlendirilmiş modüllerde **PSModulePath** ortam değişkeni, bu özellikler çalışır olduğunda bile modülün oturuma aktarılmaz.

- [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet modülünde komutları bulamıyor.

- [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) ve [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlet'leri güncelleştirilemiyor veya modül için Yardım kaydedin.

- [Show komutunu](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) cmdlet'i bulun ve modüldeki komutlar görüntüler.

  Modüldeki komutlar eksik `Show-Command` penceresi içinde Windows PowerShell Tümleşik komut dosyası ortamı (ISE).

## <a name="where-to-install-modules"></a>Where modüllerini yüklemek için

Bu bölümde, Windows PowerShell modüllerini yüklemek için dosya sistemindeki nerede açıklanmaktadır. Konumun modülü nasıl kullanıldığına bağlıdır.

### <a name="installing-modules-for-a-specific-user"></a>Belirli bir kullanıcı için modülleri yükleme

Kendi modülünüzü oluşturmak veya bir Windows PowerShell topluluğu Web sitesi gibi başka bir tarafın bir modülü Al ve modül yalnızca, kullanıcı hesabınız için kullanılabilir olmasını istiyorsanız kullanıcıya özgü modüller dizininizde modülünü yükleyin.

`$home\Documents\WindowsPowerShell\Modules\<Module Folder>\<Module Files>`

Kullanıcıya özgü modüller dizin değerine eklenir **PSModulePath** varsayılan ortam değişkeni.

### <a name="installing-modules-for-all-users-in-program-files"></a>Modüller için tüm kullanıcıların Program dosyaları yükleme

Bir modül bilgisayardaki kullanıcı hesaplarının tümünü kullanılabilir olmasını istiyorsanız, modül Program Files konumunda yükleyin.

`$Env:ProgramFiles\WindowsPowerShell\Modules\<Module Folder>\<Module Files>`

> [!NOTE]
> Program dosyalarının konumu PSModulePath ortam değişkeninin değeri için Windows PowerShell 4.0 ve sonraki sürümlerinde varsayılan olarak eklenir. Windows PowerShell'in önceki sürümleri için el ile Program dosyalarının konumu ((%ProgramFiles%\WindowsPowerShell\Modules) oluşturabilir ve yukarıda açıklandığı gibi bu yolu PSModulePath ortam değişkeninize ekleyin.

### <a name="installing-modules-in-a-product-directory"></a>Bir ürün dizinde modülleri yükleme

Modülü diğer taraflara dağıtıyorsanız, yukarıda açıklanan varsayılan Program dosyalarının konumu kullanın veya kendi şirketinize özgü veya ürüne özgü alt % ProgramFiles % dizin oluşturun.

Örneğin, Fabrikam teknolojileri, kurgusal bir şirkette Fabrikam Manager ürün için bir Windows PowerShell modülünü sunulmamaktadır. Kendi Modülü Yükleyicisi modülleri alt Fabrikam Manager ürün alt dizinde oluşturur.

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

Fabrikam Modülü Yükleyicisi Fabrikam modülü bulmak Windows PowerShell modülü bulma özellikleri etkinleştirmek için değeri olarak modül konumu ekler **PSModulePath** ortam değişkeni.

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam Technologies\Fabrikam Manager\Modules\"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

### <a name="installing-modules-in-the-common-files-directory"></a>Common Files dizininde modülleri yükleme

Bir modülün birden fazla ürün sürümünü veya bir ürünün birden çok bileşen tarafından kullanılır, modül bir %ProgramFiles%\Common Files\Modules alt modülü özgü alt dizinde yükleyin.

Aşağıdaki örnekte, Fabrikam alt dizininde Fabrikam Modülü yüklü `%ProgramFiles%\Common Files\Modules` alt. Her bir modülü kendi alt modülleri alt bulunduğu unutmayın.

```
C:\Program Files
  Common Files
    Modules
      Fabrikam
        Fabrikam.psd1 (module manifest)
        Fabrikam.dll (module assembly)
```

Ardından, yükleyici değerini garantiler **PSModulePath** ortam değişkeni ortak dosyaları modülleri alt dizini yolunu içerir.

```powershell
$m = $env:ProgramFiles + '\Common Files\Modules'
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$q = $p -split ';'
if ($q -notContains $m) {
    $q += ";$m"
}
$p = $q -join ';'
[Environment]::SetEnvironmentVariable("PSModulePath", $p)
```

## <a name="installing-multiple-versions-of-a-module"></a>Bir modülün birden fazla sürümünü yükleme

Birden çok sürümünü aynı modülü yüklemek için aşağıdaki yordamı kullanın.

1. Her modülü sürümü için bir dizin oluşturun. Sürüm numarası, dizin adı içerir.
2. Bir modül bildirimi her modülü sürümü için oluşturursunuz. Bulunan değerin **ModuleVersion** anahtar bildirimde, modülü sürüm numarası girin. Bildirim dosyası (.psd1) modülü için sürüme özgü dizine kaydedin.
3. Modül kök klasör yolu değeri olarak Ekle **PSModulePath** ortam değişkeni, aşağıdaki örneklerde gösterildiği gibi.

Son kullanıcı modülün belirli bir sürümünü almak için kullanabileceğiniz `MinimumVersion` veya `RequiredVersion` parametrelerinin [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet'i.

Örneğin, Fabrikam modülü 8.0 ve 9.0 sürümlerine ait yapılmıştı, Fabrikam modülü dizin yapısı aşağıdaki gibi olabilir.

 ```
C:\Program Files
Fabrikam Manager
  Fabrikam8
    Fabrikam
      Fabrikam.psd1 (module manifest: ModuleVersion = "8.0")
      Fabrikam.dll (module assembly)
  Fabrikam9
    Fabrikam
      Fabrikam.psd1 (module manifest: ModuleVersion = "9.0")
      Fabrikam.dll (module assembly)
```

Modül yolları her ikisi de yükleyici ekler **PSModulePath** ortam değişken değeri.

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam\Fabrikam8;C:\Program Files\Fabrikam\Fabrikam9"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

Bu adımlar tamamlandığında **ListAvailable** parametresinin [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet'i Fabrikam modüllerin her ikisi de alır. Belirli bir modülü içeri aktarmak için kullanın `MinimumVersion` veya `RequiredVersion` parametrelerinin [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet'i.

Aynı oturuma iki modülü de içeri aktarılır ve modüller aynı ada sahip cmdlet'leri içerir, en son alınan cmdlet'lerin oturumunda etkili olur.

## <a name="handling-command-name-conflicts"></a>İşleme komut adı çakışmaları

Bir modül aktarır komutları kullanıcı oturumunda komutları ile aynı ada sahip komut adı çakışmaları oluşabilir.

Bir oturum ile aynı ada sahip iki komut içerdiğinde, Windows PowerShell önceliklidir komut türü çalıştırır. Bir oturumu aynı ada ve aynı türe sahip iki komut içerdiğinde, Windows PowerShell oturuma son eklenen komut çalışır. Varsayılan olarak çalıştırılmaz bir komutu çalıştırmak için kullanıcılar, modül adı ile komut adı kazanabilir.

Oturum içeriyorsa, örneğin, bir `Get-Date` işlevi ve `Get-Date` cmdlet'i, Windows PowerShell işlev varsayılan olarak çalıştırır. Cmdlet'i çalıştırmak için komutu modül adı ile gibi yazın:

```powershell
Microsoft.PowerShell.Utility\Get-Date
```

Modül yazarları ad çakışmalarını önlemek için kullanabilirsiniz **DefaultCommandPrefix** tüm komutlar için bir isim öneki belirtmek için modül bildirimindeki anahtar modülünden dışarı aktarılan.

Kullanıcılar **önek** parametresinin `Import-Module` cmdlet'ini alternatif bir önek kullanın. Değerini **önek** parametre değerini göre önceliklidir **DefaultCommandPrefix** anahtarı.

## <a name="see-also"></a>Ayrıca bkz:

[about_Command_Precedence](/powershell/module/microsoft.powershell.core/about/about_command_precedence)

[Bir Windows PowerShell modülü yazma](./writing-a-windows-powershell-module.md)
