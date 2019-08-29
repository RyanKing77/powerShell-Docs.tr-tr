---
title: Cmdlet Parametrelerinde Joker Karakteri Destekleme
ms.custom: ''
ms.date: 08/26/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.openlocfilehash: 19644c5bc186a5554d6b134a67fc7c4d7aa7b64c
ms.sourcegitcommit: a02ccbeaa17c0e513d6c4a21b877c88ac7725458
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70104455"
---
# <a name="supporting-wildcard-characters-in-cmdlet-parameters"></a>Cmdlet Parametrelerinde Joker Karakteri Destekleme

Genellikle, tek bir kaynağa karşı değil, bir grup kaynağa karşı çalışacak bir cmdlet tasarlamanız gerekir. Örneğin, bir cmdlet 'in aynı ada veya uzantıya sahip bir veri deposundaki tüm dosyaları bulması gerekebilir. Bir kaynak grubuna karşı çalıştırılacak bir cmdlet tasarlarken joker karakter desteği sağlamalısınız.

> [!NOTE]
> Joker karakter kullanmak bazen *Glob*olarak adlandırılır.

## <a name="windows-powershell-cmdlets-that-use-wildcards"></a>Joker karakterler kullanan Windows PowerShell cmdlet 'Leri

 Birçok Windows PowerShell cmdlet 'i parametre değerleri için joker karakterleri destekler. Örneğin, bir `Name` veya `Path` parametresi olan neredeyse her cmdlet bu parametreler için joker karakterleri destekler. (Bir `Path` parametresi olan çoğu cmdlet 'in de joker karakterleri desteklemeyen `LiteralPath` bir parametresi olsa da). Aşağıdaki komut, geçerli oturumdaki adı Get fiilini içeren tüm cmdlet 'leri döndürmek için bir joker karakterin nasıl kullanıldığını gösterir.

 `Get-Command get-*`

## <a name="supported-wildcard-characters"></a>Desteklenen joker karakterler

Windows PowerShell aşağıdaki joker karakterleri destekler.

| Liyorsa |                             Açıklama                             |  Örnek   |     Eşleşmeler      | Eşleşmez |
| -------- | ------------------------------------------------------------------- | ---------- | ---------------- | -------------- |
| *        | Belirtilen konumdan başlayarak sıfır veya daha fazla karakterle eşleşir | `a*`       | A, AG, Apple     |                |
| ?        | Belirtilen konumdaki herhangi bir karakterle eşleşir                     | `?n`       | Bir, üzerinde,       | Çalıştır            |
| [ ]      | Bir karakter aralığıyla eşleşir                                       | `[a-l]ook` | kitap, Cook, görünüm | Nook, gerçekleşti     |
| [ ]      | Belirtilen karakterlerle eşleşir                                    | `[bn]ook`  | kitap, Nook       | Cook, Look     |

Joker karakterleri destekleyen cmdlet 'leri tasarladığınızda, joker karakter bileşimleri için izin verin. Örneğin, aşağıdaki komut, c:\techdocs `Get-ChildItem` klasöründe olan ve "a"-"l" harfleriyle başlayan tüm. txt dosyalarını almak için cmdlet 'ini kullanır.

`Get-ChildItem c:\techdocs\[a-l]\*.txt`

Önceki komut, "a"- `[a-l]` "l" karakterleriyle başlaması gerektiğini belirtmek için Aralık joker karakterini kullanır ve `*` joker karakteri, dosya adının ilk harfi ve **. txt** uzantısı.

Aşağıdaki örnek, "d" harfini dışlayan, ancak "a" ile "f" arasındaki diğer tüm harfleri içeren bir Aralık joker karakter modelini kullanır.

`Get-ChildItem c:\techdocs\[a-cef]\*.txt`

## <a name="handling-literal-characters-in-wildcard-patterns"></a>Joker karakter desenlerinde değişmez karakterleri işleme

Belirttiğiniz joker karakter deseninin joker karakter olarak yorumlanmamalıdır sabit karakterler içeriyorsa, bir kaçış karakteri olarak backtick karakterini (`` ` ``) kullanın. PowerShell API 'sinin tamsayı karakterlerini belirttiğinizde, tek bir geri nokta kullanın. PowerShell komut isteminde sabit karakterler belirttiğinizde, iki geri ölçü kullanın.

Örneğin, aşağıdaki model, tam anlamıyla alınması gereken iki köşeli ayraç içerir.

PowerShell API 'sinde kullanıldığında şunu kullanın:

- "John Smith \`[* ']"

PowerShell komut isteminden kullanıldığında:

- "John Smith \` \`[*\`']"

Bu kalıp "John Smith [Marketing]" veya "John Smith [Development]" ile eşleşir. Örneğin:

```
PS> "John Smith [Marketing]" -like "John Smith ``[*``]"
True

PS> "John Smith [Development]" -like "John Smith ``[*``]"
True
```

## <a name="cmdlet-output-and-wildcard-characters"></a>Cmdlet çıktısı ve joker karakterler

Cmdlet parametreleri joker karakterleri destekledikleri zaman, işlem genellikle bir dizi çıktısı üretir.
Bazen, Kullanıcı yalnızca tek bir öğe kullanabileceğinden, bir dizi çıkışını desteklemeye yönelik bir fikir vermez. Örneğin, `Set-Location` Kullanıcı yalnızca tek bir konum ayarlamadığı için cmdlet dizi çıkışını desteklemez. Bu örnekte, cmdlet joker karakterleri hala destekliyor, ancak çözümü tek bir konuma zorlar.

## <a name="see-also"></a>Ayrıca bkz:

[Windows PowerShell cmdlet 'ı yazma](./writing-a-windows-powershell-cmdlet.md)

[Yada CardModel sınıfı](/dotnet/api/system.management.automation.wildcardpattern)
