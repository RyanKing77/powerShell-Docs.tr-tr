---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Nesne Sıralama
ms.assetid: 8530caa8-3ed4-4c56-aed7-1295dd9ba199
ms.openlocfilehash: 06aa15d89888f1ecbe60b8e1dfb4efebb1d73673
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086060"
---
# <a name="sorting-objects"></a>Nesne Sıralama

Biz barkodları taramanızı daha kolay hale getirmek için görüntülenen verileri düzenleyebilirsiniz `Sort-Object` cmdlet'i. `Sort-Object` Sıralanacak bir veya daha fazla özellik adını alır ve bu özelliklerin değerlerine göre sıralanmış verileri döndürür.

## <a name="basic-sorting"></a>Temel sıralama

Alt dizinleri ve dosyaları geçerli dizin listeleme sorununu göz önünde bulundurun.
Sıralamada kullanmak istiyorsanız **LastWriteTime** göre ve ardından **adı**, biz yazarak bunu yapabilirsiniz:

```powershell
Get-ChildItem |
  Sort-Object -Property LastWriteTime, Name |
  Format-Table -Property LastWriteTime, Name
```

```output
LastWriteTime          Name
-------------          ----
11/6/2017 10:10:11 AM  .localization-config
11/6/2017 10:10:11 AM  .openpublishing.build.ps1
11/6/2017 10:10:11 AM  appveyor.yml
11/6/2017 10:10:11 AM  LICENSE
11/6/2017 10:10:11 AM  LICENSE-CODE
11/6/2017 10:10:11 AM  ThirdPartyNotices
11/6/2017 10:10:15 AM  tests
6/6/2018 7:58:59 PM    CONTRIBUTING.md
6/6/2018 7:58:59 PM    README.md
...
```

Belirterek nesneleri ters sırada sıralayabilirsiniz **azalan** parametresi geçin.

```powershell
Get-ChildItem |
  Sort-Object -Property LastWriteTime, Name -Descending |
  Format-Table -Property LastWriteTime, Name
```

```output
LastWriteTime          Name
-------------          ----
12/1/2018 10:13:50 PM  reference
12/1/2018 10:13:50 PM  dsc
...
6/6/2018 7:58:59 PM    README.md
6/6/2018 7:58:59 PM    CONTRIBUTING.md
11/6/2017 10:10:15 AM  tests
11/6/2017 10:10:11 AM  ThirdPartyNotices
11/6/2017 10:10:11 AM  LICENSE-CODE
11/6/2017 10:10:11 AM  LICENSE
11/6/2017 10:10:11 AM  appveyor.yml
11/6/2017 10:10:11 AM  .openpublishing.build.ps1
11/6/2017 10:10:11 AM  .localization-config
```

## <a name="using-hash-tables"></a>Karma tabloları kullanma

Bir dizi içinde karma tabloları kullanarak farklı özellikleri farklı siparişleri sıralayabilirsiniz.
Her karma tablo kullanan bir **ifade** özellik adını bir dize olarak belirtmek için anahtarı ve bir **artan** veya **azalan** göre sıralama düzeni belirlemek için anahtar `$true` veya `$false`.
**İfade** anahtarı zorunludur.
**Artan** veya **azalan** anahtardır isteğe bağlı.

Aşağıdaki örnek, azalan nesneleri sıralar **LastWriteTime** sırası ve artan **adı** sırası.

```powershell
Get-ChildItem |
  Sort-Object -Property @{ Expression = 'LastWriteTime'; Descending = $true }, @{ Expression = 'Name'; Ascending = $true } |
  Format-Table -Property LastWriteTime, Name
```

```output
LastWriteTime          Name
-------------          ----
12/1/2018 10:13:50 PM  dsc
12/1/2018 10:13:50 PM  reference
11/29/2018 6:56:01 PM  .openpublishing.redirection.json
11/29/2018 6:56:01 PM  gallery
11/24/2018 10:33:22 AM developer
11/20/2018 7:22:19 PM  .markdownlint.json
...
```

De bir scriptblock ayarlayabilirsiniz **ifade** anahtarı.
Çalıştırırken `Sort-Object` cmdlet'ini scriptblock yürütülür ve sonuçları sıralamak için kullanılır.

Aşağıdaki örnek nesneleri arasındaki zaman aralığı göre azalan düzende sıralar **CreationTime** ve **LastWriteTime**.

```powershell
Get-ChildItem |
  Sort-Object -Property @{ Expression = { $_.LastWriteTime - $_.CreationTime }; Descending = $true } |
  Format-Table -Property LastWriteTime, CreationTime
```

```output
LastWriteTime          CreationTime
-------------          ------------
12/1/2018 10:13:50 PM  11/6/2017 10:10:11 AM
12/1/2018 10:13:50 PM  11/6/2017 10:10:11 AM
11/7/2018 6:52:24 PM   11/6/2017 10:10:11 AM
11/7/2018 6:52:24 PM   11/6/2017 10:10:15 AM
11/3/2018 9:58:17 AM   11/6/2017 10:10:11 AM
10/26/2018 4:50:21 PM  11/6/2017 10:10:11 AM
11/17/2018 1:10:57 PM  11/29/2017 5:48:30 PM
11/12/2018 6:29:53 PM  12/7/2017 7:57:07 PM
...
```

## <a name="tips"></a>İpuçları

Atlayabilirsiniz **özelliği** parametre adı şu şekilde:

```powershell
Sort-Object LastWriteTime, Name
```

Yanında, başvurabilirsiniz `Sort-Object` yerleşik diğer tarafından `sort`:

```powershell
sort LastWriteTime, Name
```

Karma tabloları içindeki anahtarları sıralamak için aşağıdaki gibi kısaltılmış:

```powershell
Sort-Object @{ e = 'LastWriteTime'; d = $true }, @{ e = 'Name'; a = $true }
```

Bu örnekte, **e** anlamına gelen **ifade**, **d** anlamına gelen **azalan**ve **bir** anlamına gelen **artan**.

Okunabilirliği artırmak için karma tablo ayrı bir değişken içine koyabilirsiniz:

```powershell
$order = @(
  @{ Expression = 'LastWriteTime'; Descending = $true }
  @{ Expression = 'Name'; Ascending = $true }
)

Get-ChildItem |
  Sort-Object $order |
  Format-Table LastWriteTime, Name
```