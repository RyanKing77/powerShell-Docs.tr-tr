---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: İzleme nesnesi yapı Get üyesi
ms.openlocfilehash: 80b36abd303a708195f12d96511e616178d11b5a
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030710"
---
# <a name="viewing-object-structure-get-member"></a>Nesne yapısını (Get-Member) görüntüleme

Nesneleri merkezi bir rol Windows PowerShell'de yürütmek için rasgele nesne türleri ile çalışmak üzere tasarlanmış çeşitli yerel komutlar vardır. En önemli bir **Get-Member** komutu.

Bir komut verir nesnelerini çözümlemek için basit için bu komutun çıkışı yönlendirmek için bir tekniktir **Get-Member** cmdlet'i. **Get-Member** cmdlet'i gösterilmektedir, nesne türünün adını ve üyelerinin tam listesi. Döndürülen öğe sayısını bazen zor olabilir. Örneğin, bir işlem nesnesi, 100'den fazla üye sahip olabilir.

Tümünü görmek için tüm üyelerini bir işlem nesnesi ve sayfa çıktısını görmek için şunu yazın:

```powershell
Get-Process | Get-Member | Out-Host -Paging
```

Bu komutun çıktısı, aşağıdaki gibi görünmelidir:

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

Bu bilgilerin uzun listesi daha kullanışlı için görmek istediğiniz öğeleri filtreleyerek yapabiliyoruz. **Get-Member** komut özellikleri yalnızca üyeleri Listele olanak tanır. Çeşitli özellikler biçimi vardır. Ayarlarsanız cmdlet herhangi bir tür özelliklerini görüntüler **Get-Member MemberType** parametre değerine **özellikleri**. Sonuç listesini yine de çok uzun, ancak biraz daha kolay yönetilebilir:

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
> MemberType izin verilen değerleri AliasProperty, CodeProperty, özelliği, NoteProperty, ScriptProperty, özellikleri, PropertySet, yöntem, CodeMethod, ScriptMethod, yöntemleri, ParameterizedProperty, MemberSet ve tüm verilmiştir.

Bir işlem için 60'tan fazla özellik yok. Windows PowerShell genellikle yalnızca bir dizi iyi bilinen herhangi bir nesne için özellikler, bunların tümünün gösteren gösterilir nedeni yönetilemeyen büyüklükte bir bilgi oluşturur.

> [!NOTE]
> Windows PowerShell nasıl sonlanan adlara sahip XML dosyalarında depolanan bilgileri kullanarak bir nesne türü görüntüleneceğini belirler. format.ps1xml. .NET System.Diagnostics.Process nesneleri olan işlem nesneleri için biçimlendirme veri DotNetTypes.format.ps1xml içinde depolanır.

Varsayılan olarak Windows PowerShell görüntüleyen dışındaki özellikleri bakmak gerekiyorsa, çıktı verilerini kendiniz biçimlendirmek gerekir. Bu biçim cmdlet'lerini kullanarak gerçekleştirebilirsiniz.
