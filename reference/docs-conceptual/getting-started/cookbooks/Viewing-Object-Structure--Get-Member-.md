---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Görüntüleme nesne yapısı Get üyesi
ms.assetid: a1819ed2-2ef3-453a-b2b0-f3589c550481
ms.openlocfilehash: cc93e45e4306b3d623c1d3d1096dd20c1afc59c8
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30950752"
---
# <a name="viewing-object-structure-get-member"></a>Nesne yapısını (Get-üye) görüntüleme

Nesneleri Windows PowerShell'de merkezi bir rol oynar çünkü rasgele nesne türleri ile çalışmak üzere tasarlanmış birçok yerel komutlar vardır. En önemlisi olan **Get-üye** komutu.

Bu komutun çıktısı kanal için bir komut verir nesnelerini çözümlemek için basit tekniği olan **Get-üye** cmdlet'i. **Get-üye** cmdlet'i gösterilmektedir, size, nesne türünün resmi adı ve üyeleri tam bir listesi. Döndürülen öğe sayısını bazen zorlamayı olabilir. Örneğin, bir işlem nesnesi 100'den üyelere sahip olabilir.

Tümünü görmek için işlem nesnesi ve sayfanın çıkış tüm üyelerini görmek için şunu yazın:

```powershell
Get-Process | Get-Member | Out-Host -Paging
```

Bu komutun çıktısı aşağıdakine benzer görünecektir:

```output
TypeName: System.Diagnostics.Process

Name                           MemberType     Definition
----                           ----------     ----------
Handles                        AliasProperty  Handles = Handlecount
Name                           AliasProperty  Name = ProcessName
NPM                            AliasProperty  NPM = NonpagedSystemMemorySize
PM                             AliasProperty  PM = PagedMemorySize
VM                             AliasProperty  VM = VirtualMemorySize
WS                             AliasProperty  WS = WorkingSet
add_Disposed                   Method         System.Void add_Disposed(Event...
...
```

İçin görmeyi istiyoruz öğeleri filtreleyerek Biz bu uzun bilgi listesi daha kullanışlı hale getirebilirsiniz. **Get-üye** komut özellikleri yalnızca üyelerin listesi olanak sağlar. Birkaç forms özellikleri vardır. Biz ayarlarsanız cmdlet herhangi bir türde özelliklerini görüntüler **Get-üye MemberType** parametre değerine **özellikleri**. Sonuç listesi çok uzun, ancak biraz daha kolay yönetilebilir hala şöyledir:

```
PS> Get-Process | Get-Member -MemberType Properties

   TypeName: System.Diagnostics.Process

Name                       MemberType     Definition
----                       ----------     ----------
Handles                    AliasProperty  Handles = Handlecount
Name                       AliasProperty  Name = ProcessName
...
ExitCode                   Property       System.Int32 ExitCode {get;}
...
Handle                     Property       System.IntPtr Handle {get;}
...
CPU                        ScriptProperty System.Object CPU {get=$this.Total...
...
Path                       ScriptProperty System.Object Path {get=$this.Main...
...
```

> [!NOTE]
> İzin verilen MemberType AliasProperty, CodeProperty, özelliği, NoteProperty, ScriptProperty, özellikler, PropertySet, yöntem, CodeMethod, ScriptMethod, yöntemleri, ParameterizedProperty, MemberSet ve tüm değerleri.

Bir işlem için 60 özellikleri vardır. Windows PowerShell genellikle iyi bilinen bir nesne için özellikler sayıda, bunların tümünün gösteren gösterilir neden Yönetilemeyen bir miktar bilgiye üretir.

> [!NOTE]
> Windows PowerShell biten adlara sahip XML dosyalarında depolanan bilgileri kullanarak bir nesne türü görüntülemek nasıl belirler. format.ps1xml. .NET System.Diagnostics.Process nesne olduğundan, işlem nesneleri biçimlendirme verilerini DotNetTypes.format.ps1xml içinde depolanır.

Varsayılan olarak Windows PowerShell görüntüleyen olanlar dışındaki özellikleri bakmak gerekiyorsa, çıktı verilerini kendiniz biçimlendirmek gerekir. Bu biçim cmdlet'leri kullanılarak yapılabilir.