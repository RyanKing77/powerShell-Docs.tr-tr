---
ms.date: 08/23/2018
keywords: PowerShell cmdlet'i
title: PowerShell işlem hatları anlama
ms.openlocfilehash: 3033a4fe1a704fbbfa76e6d38662c8b22c3dbd9b
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030384"
---
# <a name="understanding-pipelines"></a>Anlama işlem hatları

İşlem hatları kanal bağlı parçalarını bir dizi gibi davranır. İşlem hattı taşıyarak öğeleri her bir kesim geçirin. PowerShell'de bir işlem hattı oluşturmak için yöneltme işleci birlikte komutların Bağlan "|". Her komutun çıkışı, sonraki komut için giriş olarak kullanılır.

İşlem hatları için kullanılan gösterim diğer Kabukları içinde kullanılan gösterim benzer. İlk bakışta, işlem hatlarını nasıl PowerShell'de farklı belirgin olmayabilir. Metin ekranda gördüğünüz olsa da, PowerShell komutları arasında değil metin nesneleri geçirir.

## <a name="the-powershell-pipeline"></a>PowerShell işlem hattını

İşlem hatları tartışmaya komut satırı arabirimi içinde kullanılan en değerli kavram olarak oldukça basittir. Düzgün kullanıldığında, işlem hatları karmaşık komutlarını kullanarak çabayı azaltmak ve komutlar için iş akışını görmek kolaylaştırır. Her komut bir işlem hattı (işlem hattı öğesi olarak adlandırılır), ardışık düzende sonraki komuta çıktısını geçirir. öğe tarafından. Komutlar, aynı anda birden fazla öğe işlemek zorunda değilsiniz. Daha az kaynak tüketimi ve çıkış hemen başlama başlamak olanağı sonucudur.

Örneğin, kullanırsanız `Out-Host` çıkış sayfa sayfa görünümünü yalnızca başka bir komuttan çıkış görünüyor zorlamak için cmdlet'i sayfalarına parçalanmış ekranda görüntülenen normal metin ister:

```powershell
Get-ChildItem -Path C:\WINDOWS\System32 | Out-Host -Paging
```

```Output
    Directory: C:\WINDOWS\system32

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        4/12/2018   2:15 AM                0409
d-----        5/13/2018  11:31 PM                1033
d-----        4/11/2018   4:38 PM                AdvancedInstallers
d-----        5/13/2018  11:13 PM                af-ZA
d-----        5/13/2018  11:13 PM                am-et
d-----        4/11/2018   4:38 PM                AppLocker
d-----        5/13/2018  11:31 PM                appmgmt
d-----        7/11/2018   2:05 AM                appraiser
d---s-        4/12/2018   2:20 AM                AppV
d-----        5/13/2018  11:10 PM                ar-SA
d-----        5/13/2018  11:13 PM                as-IN
d-----        8/14/2018   9:03 PM                az-Latn-AZ
d-----        5/13/2018  11:13 PM                be-BY
d-----        5/13/2018  11:10 PM                BestPractices
d-----        5/13/2018  11:10 PM                bg-BG
d-----        5/13/2018  11:13 PM                bn-BD
d-----        5/13/2018  11:13 PM                bn-IN
d-----        8/14/2018   9:03 PM                Boot
d-----        8/14/2018   9:03 PM                bs-Latn-BA
d-----        4/11/2018   4:38 PM                Bthprops
d-----        4/12/2018   2:19 AM                ca-ES
d-----        8/14/2018   9:03 PM                ca-ES-valencia
d-----        5/13/2018  10:46 PM                CatRoot
d-----        8/23/2018   5:07 PM                catroot2
<SPACE> next page; <CR> next line; Q quit
...
```

Ayrıca disk belleği azaltır CPU kullanımı için işleme aktardığından `Out-Host` tam bir sayfa görüntüleme hazır olduğunda cmdlet'i. Çıktı, sonraki sayfaya kullanılabilir hale gelene kadar yürütme işlem hattında önünde cmdlet'ler duraklatın.

Aşağıdaki komutları karşılaştırarak yöneltme CPU ve bellek kullanımı Windows Görev Yöneticisi'nde nasıl etkilediğini görebilirsiniz:

- `Get-ChildItem C:\Windows -Recurse`
- `Get-ChildItem C:\Windows -Recurse | Out-Host -Paging`

> [!NOTE]
> **Sayfalama** parametresi tüm PowerShell konaklar tarafından desteklenmez. Örneğin, çalıştığınızda kullanılacak **sayfalama** parametresi PowerShell ISE'de aşağıdaki hatayı görürsünüz:
>
> ```Output
> out-lineoutput : The method or operation is not implemented.
> At line:1 char:1
> + Get-ChildItem C:\Windows -Recurse | Out-Host -Paging
> + ~~~~~~~~~~~~~~~~~~~~~~~~~~~
>     + CategoryInfo          : NotSpecified: (:) [out-lineoutput], NotImplementedException
>     + FullyQualifiedErrorId : System.NotImplementedException,Microsoft.PowerShell.Commands.OutLineOutputCommand
> ```

## <a name="objects-in-the-pipeline"></a>İşlem hattı nesneleri

PowerShell'de bir cmdlet çalıştırdığınızda, konsol penceresindeki metin olarak nesneleri temsil etmek gerekli olduğundan, metin çıktısı görürsünüz. Metin çıktısı çıkış nesnesinin özelliklerini görüntülenmeyebilir.

Örneğin, düşünün `Get-Location` cmdlet'i. Çalıştırırsanız `Get-Location` geçerli konumunuzu C sürücüsünün kök olsa da, şu çıktıyı görürsünüz:

```
PS> Get-Location

Path
----
C:\
```

Metin çıkışı bir özetidir bilgilerinin tarafından döndürülen nesne değil tam bir temsilini `Get-Location`. Çıkış başlığı, ekranda görünen verileri biçimlendirir, oluşturduğunuz işlem tarafından eklenir.

Çıktı için kanal zaman `Get-Member` cmdlet'i tarafından döndürülen nesne hakkında bilgi alma `Get-Location`.

```powershell
Get-Location | Get-Member
```

```Output
   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Equals       Method     bool Equals(System.Object obj)
GetHashCode  Method     int GetHashCode()
GetType      Method     type GetType()
ToString     Method     string ToString()
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   string Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {get;}
ProviderPath Property   string ProviderPath {get;}
```

`Get-Location` döndürür bir **PATHINFO** geçerli yol ve diğer bilgileri içeren nesne.
