---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: "Mağaza nesnelere değişkenlerini kullanma"
ms.assetid: b1688d73-c173-491e-9ba6-6d0c1cc852de
ms.openlocfilehash: 9a95d421fa2686608a565987c16fecc41c3c6d20
ms.sourcegitcommit: f069ff0689006fece768f178c10e3e3eeaee09f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2017
---
# <a name="using-variables-to-store-objects"></a>Mağaza nesnelere değişkenlerini kullanma
PowerShell nesneler ile çalışır. PowerShell temelde daha sonra kullanmak için çıktı korumak için nesneleri, adlandırılmış değişkenleri oluşturmanıza olanak sağlar. Diğer değişkenlerle birlikte çalışmaya kullanılıyorsa Kabukları PowerShell değişkenleri nesneleri, metin değil olduğunu unutmayın.

Değişkenleri her zaman belirtilen ilk karakter $ ile ve bunların adları, herhangi bir alfasayısal karakter veya alt çizgi içerebilir.

### <a name="creating-a-variable"></a>Bir değişken oluşturma
Geçerli bir değişken adı yazarak bir değişken oluşturabilirsiniz:

```
PS> $loc
PS>
```

Bu sonuç verir, çünkü **$loc** bir değere sahip değil. Bir değişken oluşturun ve aynı adımını bir değere atayın. Henüz yoksa PowerShell yalnızca değişken oluşturur; Aksi halde, belirtilen değer var olan değişkenine atar. Geçerli konumunuz değişkende saklamak için **$loc**, türü:

```
$loc = Get-Location
```

Bu komut çıktı $loc gönderdiğinden yazdığınızda görüntülenen çıkış yok PowerShell'de, görüntülenen çıktının bir yan etkisi, yönlendirilmiş aksi değil, verileri her zaman ekrana gönderilir olgu ' dir. $Loc yazarak geçerli konumunuz gösterir:

```
PS> $loc

Path
----
C:\temp
```

Kullanabileceğiniz **Get-üye** değişkenleri içeriği hakkında bilgileri görüntülemek için. Get-üyesine $loc cmdlet'ine gösterir, bunun bir **PATHINFO** nesne Get-Location çıktısı gibi:

```
PS> $loc | Get-Member -MemberType Property

   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   System.String Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {...
ProviderPath Property   System.String ProviderPath {get;}
```

### <a name="manipulating-variables"></a>Değişkenleri düzenleme
PowerShell değişkenlerini için çeşitli komutlar sağlar. Tam bir listesi okunabilir bir biçimde yazarak görebilirsiniz:

```
Get-Command -Noun Variable | Format-Table -Property Name,Definition -AutoSize -Wrap
```

Geçerli PowerShell oturumunda oluşturduğunuz değişkenlerinin yanı sıra çeşitli sistem tarafından tanımlanan değişkenler vardır. Kullanabileceğiniz **Kaldır-Variable** cmdlet'ini tüm değişkenlerin PowerShell tarafından denetlenmeyen temizleyin. Tüm değişkenleri temizlemek için aşağıdaki komutu yazın:

```
Remove-Variable -Name * -Force -ErrorAction SilentlyContinue
```

Bu, aşağıya bakın onay istemi oluşturur.

```
Confirm
Are you sure you want to perform this action?
Performing operation "Remove Variable" on Target "Name: Error".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):A
```

Ardından çalıştırırsanız **Get-Variable** cmdlet, kalan PowerShell değişkenleri görürsünüz. Yazarak, ayrıca PowerShell sürücüsü değişken olduğundan, tüm PowerShell değişkenleri görüntüleyebilirsiniz:

```
Get-ChildItem variable:
```

### <a name="using-cmdexe-variables"></a>Cmd.exe değişkenleri kullanma
PowerShell Cmd.exe olmamasına karşın, bir komut kabuğu ortamda çalışır ve hiçbir ortamında kullanılabilir aynı değişkenleri Windows kullanabilirsiniz. Bu değişkenler adlı bir sürücüsü sunulan **env**:. Bu değişkenler yazarak görüntüleyebilirsiniz:

```
Get-ChildItem env:
```

Standart değişken cmdlet'leri çalışmak için tasarlanmamıştır rağmen **env:** değişkenleri kullanmaya devam edebilirsiniz bunları belirterek **env:** öneki. Örneğin, işletim sisteminin kök dizini görmek için komut kabuğunu kullanabilirsiniz **% SystemRoot %** yazarak PowerShell içinde değişken:

```
PS> $env:SystemRoot
C:\WINDOWS
```

Ayrıca, oluşturabilir ve ortam değişkenler PowerShell değiştirebilirsiniz. Başka bir yerde Windows ortam değişkenleri için normal kuralları için Windows Powershell'den erişilen ortam değişkenleri uygun.

