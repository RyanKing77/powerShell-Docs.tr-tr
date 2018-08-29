---
ms.date: 08/27/2018
keywords: PowerShell cmdlet'i
title: Nesne Depolamak için Değişkenleri Kullanma
ms.assetid: b1688d73-c173-491e-9ba6-6d0c1cc852de
ms.openlocfilehash: 3168b64039a601857f9c684108de5770f88329e3
ms.sourcegitcommit: 59727f71dc204785a1bcdedc02716d8340a77aeb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2018
ms.locfileid: "43134067"
---
# <a name="using-variables-to-store-objects"></a>Nesneleri depolamak için değişkenleri kullanma

PowerShell nesneleri ile çalışır. PowerShell değişkenleri olarak bilinen adlandırılmış nesneleri oluşturmanızı sağlar.
Değişken adları alt çizgi karakteri can herhangi bir alfasayısal karakter içerebilir. PowerShell'de kullanıldığında, bir değişkeni her zaman kullanarak belirtilen \$ karakteri ve ardından tarafından değişken adı.

## <a name="creating-a-variable"></a>Bir değişken oluşturma

Geçerli bir değişken adı yazarak bir değişken oluşturabilirsiniz:

```
PS> $loc
PS>
```

Bu örnekte sonuç verir, çünkü `$loc` bir değere sahip değil. Bir değişken oluşturun ve aynı adımda bir değer atayın. PowerShell, yoksa yalnızca değişkeni oluşturur.
Aksi takdirde, belirtilen değer var olan değişkenine atar. Aşağıdaki örnek geçerli konumu değişkeninde depolar. `$loc`:

```powershell
$loc = Get-Location
```

Bu komut yazarken PowerShell hiçbir çıktı görüntüler. PowerShell için 'Get-konum' çıktısını gönderir `$loc`. PowerShell'de, atanan veya yeniden yönlendirilen değil veri ekranına gönderilir. Yazarak `$loc` geçerli konumunuzu gösterir:

```
PS> $loc

Path
----
C:\temp
```

Kullanabileceğiniz `Get-Member` değişkenlerin içeriğini hakkındaki bilgileri görüntülemek için. `Get-Member` gösteren `$loc` olduğu bir **PATHINFO** çıktısı gibi bir nesne `Get-Location`:

```powershell
PS> $loc | Get-Member -MemberType Property

   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   System.String Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {...
ProviderPath Property   System.String ProviderPath {get;}
```

## <a name="manipulating-variables"></a>Değişkenleri düzenleme

PowerShell değişkenlerini için çeşitli komutlar sağlar. Okunabilir bir biçimde yapılandırılabilip yazarak görebilirsiniz:

```powershell
Get-Command -Noun Variable | Format-Table -Property Name,Definition -AutoSize -Wrap
```

PowerShell, ayrıca çeşitli sistem tarafından tanımlanan değişkenler oluşturur. Kullanabileceğiniz `Remove-Variable` PowerShell tarafından denetlenmez, değişkenleri, geçerli oturumdan kaldırmak için cmdlet. Tüm değişkenleri temizlemek için aşağıdaki komutu yazın:

```powershell
Remove-Variable -Name * -Force -ErrorAction SilentlyContinue
```

Önceki komutu çalıştırdıktan sonra `Get-Variable` cmdlet'i, PowerShell sistem değişkenlerini gösterir.

PowerShell, ayrıca bir değişken sürücü oluşturur. Değişken sürücü kullanarak tüm PowerShell değişkenlerini görüntülemek için aşağıdaki örneği kullanın:

```powershell
Get-ChildItem variable:
```

## <a name="using-cmdexe-variables"></a>Cmd.exe değişkenlerini kullanma

PowerShell, Windows işlemi Cmd.exe dahil olmak üzere tüm kullanılabilir aynı ortam değişkenlerini kullanabilirsiniz. Bu değişkenler adlı bir sürücüsü sunulan `env:`. Bu değişkenler, aşağıdaki komutu yazarak görüntüleyebilirsiniz:

```powershell
Get-ChildItem env:
```

Standart `*-Variable` cmdlet'leri olmayan ortam değişkenleri ile çalışacak şekilde tasarlanmıştır. Ortam değişkenlerini kullanarak erişilen `env:` sürücü öneki. Örneğin, **% SystemRoot %** Cmd.exe değişkeninde işletim sisteminin kök dizin adı içerir. PowerShell'de, kullandığınız `$env:SystemRoot` aynı değere erişmek için.

```
PS> $env:SystemRoot
C:\WINDOWS
```

Ayrıca, oluşturabilir ve PowerShell içinde ortam değişkenlerinden değiştirebilirsiniz. PowerShell ortam değişkenlerinde başka bir yerde işletim sisteminde kullanılan ortam değişkenleri için bu kuralların izleyin. Aşağıdaki örnek, yeni bir ortam değişkeni oluşturur:

```powershell
$env:LIB_PATH='/usr/local/lib'
```

Zorunlu olmasa da, tüm büyük harfleri kullanılacak ortam değişken adları için ortak olan.