---
title: Cmdlet parametreleri joker karakterleri destekleme | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- wildcards [PowerShell Programer's Guide]
- parameters [PowerShell Programmer's Guide], wildcards
ms.assetid: 9b26e1e9-9350-4a5a-aad5-ddcece658d93
caps.latest.revision: 12
ms.openlocfilehash: 296490e4692e72f823be0b00aee90dc8c3dc9131
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851376"
---
# <a name="supporting-wildcard-characters-in-cmdlet-parameters"></a>Cmdlet Parametrelerinde Joker Karakteri Destekleme

Genellikle, kaynakların bir gruba göre yerine tek bir kaynak karşı çalıştırmak için bir cmdlet tasarım gerekecektir. Örneğin, bir cmdlet tüm dosyaları uzantı ve aynı ada sahip bir veri deposunda bulun gerekebilir. Bir kaynak grubu üzerinde çalıştırılacak bir cmdlet tasarlarken joker karakterleri için destek sağlamalısınız.

> [!NOTE]
> Joker karakterler kullanarak bazen olarak adlandırılır *Glob*.

## <a name="windows-powershell-cmdlets-that-use-wildcards"></a>Joker karakter Windows PowerShell cmdlet'leri

 Birçok Windows PowerShell cmdlet'leri için parametre değerleri joker karakterleri destekler. Örneğin, neredeyse her cmdlet'i olan bir `Name` veya `Path` parametresi bu parametreler için joker karakterleri destekler. (Çoğu cmdlet olsa bir `Path` parametresi de bir `LiteralPath` parametresi joker karakterleri desteklemiyor.) Aşağıdaki komut, bir joker karakter tüm cmdlet'lerinin adında Get fiili içeren geçerli oturumda döndürmek için nasıl kullanıldığını gösterir.

 **PS > get-command get -\***

## <a name="supported-wildcard-characters"></a>Desteklenen joker karakterler

Windows PowerShell, joker karakterleri destekler.

|joker karakter|Açıklama|Örnek|Eşleşmeler|Eşleşmez|
|------------------------|-----------------|-------------|-------------|--------------------|
|*|Belirtilen konumdan başlayarak, sıfır veya daha fazla karakter ile eşleşir|a*|Apple ag||
|?|Belirli bir konumda eşleşen anycharacter|? n|Bir içinde üzerinde|çalıştı|
|[ ]|Bir dizi karakter ile eşleşir|[a-l] ook|kitap, cook, Görünüm|sürdü|
|[ ]|Belirtilen karakter ile eşleşir|[bc] ook|kitap, cook|Ara|

Joker karakterler destekleyen cmdlet'ler tasarlarken, joker karakter birleşimleri için izin verin. Örneğin, aşağıdaki kullanan komut `Get-ChildItem` c:\Techdocs klasöründe olan ve "a" ile "l." harflerle başlayan tüm .txt dosyaları almak için cmdlet

**Get-childıtem c:\techdocs\\[a-l]\*.txt**

Önceki komutun aralığı joker karakter kullanan **[a-l]** dosya adı "a" ile "l." karakterleriyle başlaması gereken belirtmek için Daha sonra komut * joker karakterini dosya adının ilk harfi ve .txt uzantısı arasındaki herhangi bir karakter için bir yer tutucu olarak.

Aşağıdaki örnek, "d" harfi dahil değildir, ancak "a" ile "f." den tüm diğer harfler içeren bir aralık joker karakter deseni kullanır.

**Get-childıtem c:\techdocs\\[a-cef]\*.txt**

## <a name="handling-literal-characters-in-wildcard-patterns"></a>Joker karakter düzenleri bir sabit karakterin işleme

Belirttiğiniz joker karakter deseni, değişmez karakterler içeriyorsa, bir kaçış karakteri vurgulamasını belirtir karakteri (') kullanın. Değişmez karakterler programlı olarak belirttiğinizde, tek bir vurgulamasını belirtir kullanın. Komut isteminde değişmez karakterler belirttiğinizde, iki tik kullanın. Örneğin, şu desene tam anlamıyla alınması gereken iki ayraçlar içerir.

"John Smith \`[*']" (program aracılığıyla belirtilen)

"John Smith \` \`[*\`']" (komut isteminde belirtilen)

Bu, "John Smith [pazarlama]" veya "John Smith [Geliştirme]" eşleştirilir.

## <a name="cmdlet-output-and-wildcard-characters"></a>Cmdlet çıktı ve joker karakterler

Cmdlet parametrelerini joker karakterlerini desteklediğinde, bir cmdlet işlemi genellikle bir dizi çıkışını oluşturur. Bazen, bir kullanıcı aynı anda yalnızca tek bir öğe kullanabilir olduğundan çıkış dizisi desteklemek için hiçbir mantıklı. Örneğin, `Set-Location` kullanıcı tek bir konuma IGNORE_DUP_KEY çıkış dizisi cmdlet'ini destekler. Bu örnekte, cmdlet hala joker karakterleri destekler, ancak tek bir konuma çözümleme zorlar.

## <a name="see-also"></a>Ayrıca bkz:

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)

[WildcardPattern sınıfı](/dotnet/api/system.management.automation.wildcardpattern)
