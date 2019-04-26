---
title: PowerShell cmdlet'leri için Yardım yazma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55908d67-7cbe-482a-a105-5a6da93c5311
caps.latest.revision: 4
ms.openlocfilehash: 8d692cf88d1d356886ef973f0989294d6b51ee6d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083170"
---
# <a name="writing-help-for-powershell-cmdlets"></a>PowerShell cmdlet'leri için Yardım yazma

PowerShell cmdlet'lerini yararlı olabilir, ancak, Yardım konuları açıkça cmdlet yaptığı ve nasıl kullanılacağını açıklayan sürece cmdlet kullanılmayan veya daha da kötüsü, kullanıcıları rahatsız.
XML temelli cmdlet Yardım dosyası biçimi tutarlılığı artırır, ancak çok daha yararlı bir Yardım gerektirir.

Cmdlet Yardım hiçbir zaman yazdıysanız, aşağıdaki yönergeleri gözden geçirin.
Cmdlet Yardım konusunun yazar için gereken XML Şeması, aşağıdaki bölümde açıklanmıştır.
İle başlayan [Cmdlet Yardım dosyası oluşturma](./how-to-create-the-cmdlet-help-file.md).
Bu konu, en üst düzey XML düğümlerini açıklamasını içerir.

## <a name="writing-guidelines-for-cmdlet-help"></a>Cmdlet Yardım için yazma Kılavuzu

### <a name="write-well"></a>İyi yazma
Hiçbir şey iyi-yazılan konunun yerini alır.
Profesyonel bir yazıcı emin değilseniz, yazıcı veya Düzenleyicisi yardımcı olmak üzere bulun.
Yardım metni Microsoft Word'e kopyalayıp dilbilgisi kullanmak için başka bir alternatiftir ve işinizi geliştirmek için yazım denetimi yapar.

### <a name="write-simply"></a>Yalnızca yazma
Basit bir sözcük ve tümcecikleri kullanın.
Terimler kaçının.
Birçok okuyucu yalnızca bir yabancı dildeki sözlük ve Yardım konu başlığınız ile donatılmış göz önünde bulundurun.

### <a name="write-consistently"></a>Tutarlı bir şekilde yazma
İlgili cmdlet (örneğin, get-x ve set-x) benzer Yardımı.
Standart açıklamalar gibi standart parametreler için kullanmak **zorla** ve **Inputobject**.
(Bunları Yardım için çekirdek cmdlet'lerinin kopyalayın.) Standart terimleri kullanın.
Örnek, kullan "parametresi", değil "bağımsız değişken" ve kullanım "cmdlet'i" değil "komut" veya "command-let."

### <a name="start-the-synopsis-with-a-verb"></a>İle bir fiili özeti Başlat
Özeti alanın hangi cmdlet desteklemiyor, bunun ne olduğunu veya nasıl çalıştığını kullanıcıya bildirir.
Bu cmdlet, kendi gereksinimlerini karşılıyorsa, kullanıcıları bilgilendirir ve görev tabanlı bir deyimi fiilleri oluşturun.
"Get", "oluşturma" ve "Değiştir" gibi basit fiilleri kullanın
"Set", "değiştirme" gibi belirsiz ve başvurmaktan sözcükleri olabilen kaçının.

### <a name="focus-on-objects"></a>Nesneler üzerinde odaklanın
Çoğu "cmdlet'leri görünen bir şey Al", ancak bir nesne almak için kendi birincil işlevi olduğu.
Böylece kullanıcılar varsayılan görüntüyü birçok biri olduğunu ve bunlar için farklı şekilde alınan nesnenin özelliklerini ve yöntemlerini kullanabilirsiniz anlamak, Yardım'da nesnede odaklanın.

### <a name="write-detailed-descriptions"></a>Ayrıntılı açıklamalar için yazma
Kısaca cmdlet'in ayrıntılı bir açıklama yapabileceğiniz her şeyi listeleyin.
Bu ayrıntılı bir açıklama listesinde, bir özelliği değiştirmek için ana işlevi olduğu, ancak cmdlet tüm özelliklerini değiştirebilirsiniz.

### <a name="use-conventional-syntax"></a>Geleneksel söz dizimini kullanın
Windows ve UNIX komut satırı Yardımı için ortak olan standart Backus-Naur biçimini kullanın.

### <a name="use-microsoft-net-framework-types-for-parameter-values"></a>Microsoft .NET Framework türleri için parametre değerlerini kullanın.
Parametre değerlerini (söz dizimi ve parametre açıklamaları) için yer tutucular .NET Framework türleri parametre kabul edecek nesnelerin gösterir.
PowerShell ekibi, kullanıcıların .NET Framework hakkında öğretin yardımcı olmak için bu kural geliştirilmiştir.

### <a name="write-complete-parameter-descriptions"></a>Tam parametre açıklamaları yazma
Parametre açıklamaları, iki şey kullanıcıları bildirmelidir: (etkisini) parametrenin ne yapar ve bunların ne için parametre değerleri yazmalısınız.

### <a name="write-practical-examples"></a>Pratik örnekler yazma
Tüm parametreleri kullanma örnekleri göstermesi gerekir, ancak en önemli şey gerçek görevleri cmdlet kullanmayı göstermektir.
Basit bir örnek ile başlayın ve giderek daha karmaşık örnekler yazma.
Son örnekte, bir işlem hattı, cmdlet kullanmayı göstermektedir.

### <a name="use-the-notes-field"></a>Notlar alanı kullanın
Notlar alanı kullanıcılar cmdlet anlamanız gerekir, kavramları açıklamak için kullanın.
Notlar, sık karşılaşılan kayıt hatalarının önüne kullanıcılara yardımcı olmak için de kullanabilirsiniz.
Değiştiklerinde URL'leri kaçının.
Bunun yerine, aranacak kullanıcıların koşulları belirtin.

### <a name="test-your-help"></a>Yardım test
Kodunuzu test yalnızca gibi Yardım test edin.
Arkadaş sahip ve iş arkadaşlarınızla Yardım içeriğiniz okuyun ve geri bildirim sağlayın.
Ayrıca, haber görüşleri gönderebilecekleri.

## <a name="see-also"></a>Ayrıca bkz:

 [Cmdlet Yardım dosyası oluşturma](./how-to-create-the-cmdlet-help-file.md)

 [Cmdlet adı ve özeti için Cmdlet Yardım konusunun ekleme](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [Cmdlet Yardım konuları ayrıntılı bir açıklama ekleme](./how-to-add-a-cmdlet-description.md)

 [Cmdlet Yardım konuları söz dizimi ekleme](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [Cmdlet Yardım konuları parametreleri ekleme](./how-to-add-parameter-information.md)

 [Bir Cmdlet Yardım konusuna giriş türleri ekleme](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [Dönüş değerleri için Cmdlet Yardım konusunun ekleme](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [Ekleme için Cmdlet Yardım konusunun notları](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [Bir Cmdlet Yardım konusunun örneklere ekleme](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [Cmdlet Yardım konuları ilgili bağlantılar ekleme](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [Windows PowerShell SDK'sı](../windows-powershell-reference.md)