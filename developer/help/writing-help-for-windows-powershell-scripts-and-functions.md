---
title: PowerShell betikleri ve işlevleri için Yardım yazma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 859a6e22-75b1-43d4-ba62-62c107803b37
caps.latest.revision: 7
ms.openlocfilehash: 98a3f61ff4fa2367f69357173d4e8e14288ff429
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847848"
---
# <a name="writing-help-for-powershell-scripts-and-functions"></a>PowerShell betikleri ve İşlevler yazma

Diğer kullanıcılarla paylaşılır her PowerShell betikleri ve işlevleri tam olarak belgelenmelidir.
`Get-Help` Cmdlet Yardım cmdlet'leri ve tüm görüntüler olarak bu komut dosyası ve işlev Yardım konuları aynı biçimde görüntüler `Get-Help` parametreleri iş betiği ve işlev Yardım konuları.

PowerShell betiklerini komut hakkında Yardım konusunun ve her işlevleri hakkında Yardım konularında komut dosyasında yer alabilir.
Komut bağımsız olarak paylaşılan işlevleri kendi Yardım konuları içerebilir.

Bu belge, biçimini ve doğru yerleşimini Yardım konularını açıklar ve içerik için yönergeleri önerir.

## <a name="types-of-script-and-function-help"></a>Betik ve işlev türlerini Yardım

### <a name="comment-based-help"></a>Açıklama tabanlı Yardım
Bir betik veya işlevdeki açıklayan Yardım konusu, betik veya işlevdeki açıklamaları kümesi olarak uygulanabilir.
Açıklama tabanlı Yardım işlevleri ve komut dosyası için bir betik yazarken dikkat kuralları açıklama tabanlı Yardım yerleştirmek için ödeme yaparsınız.
Yerleşimini belirler olmadığını `Get-Help` cmdlet Yardım konusu komut dosyası veya bir işlev ile ilişkilendirir.
Açıklama tabanlı Yardım konuları yazma hakkında daha fazla bilgi için bkz. [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).

### <a name="xml-based-command-help"></a>XML-tabanlı komut Yardımı
Komut Yardımı şemasını kullanan bir XML dosyasındaki bir betik veya işlevdeki açıklayan Yardım konusuna uygulanabilir.
Betik veya işlevdeki XML dosyası ile ilişkilendirmek için `ExternalHelp` XML dosyasının adını ve yolunu anahtar sözcüğünü açıklama satırı yapın.

Zaman `ExternalHelp` açıklama anahtar sözcüğü, açıklama tabanlı Yardım öncelik kazanır, bile `Get-Help` değeri ile eşleşen bir Yardım dosyası bulunamıyor `ExternalHelp` anahtar sözcüğü.

### <a name="online-help"></a>Çevrimiçi Yardım
Internet'te, Yardım konuları gönderin ve daha sonra doğrudan `Get-Help` konular açın.
Açıklama tabanlı Yardım konuları yazma hakkında daha fazla bilgi için bkz. [çevrimiçi Yardımı destekleme](../module/supporting-online-help.md).

("") Konular hakkında betikleri ve işlevleri için kavramsal yazma için yerleşik bir yöntem yoktur.
Ancak, Internet listedeki kavramsal konular konular ve bunların URL'lerini komutun Yardım konusunun ilgili bağlantılar bölümünde nakledebilirsiniz.

## <a name="content-considerations-for-script-and-function-help"></a>Yardım içerik konuları için komut dosyası ve işlevi

- Yalnızca birkaç kullanılabilir komut Yardım bölümlerin ile çok kısa bir Yardım konusu yazma, betik veya işlevdeki parametreleri Temizle açıklamalarını eklemeyi unutmayın. Örnek açıklamaları atlamak karar verseniz bir veya iki örnek komut örnekler bölümüne de.

- Komutu farklı bir betik veya işlevdeki tüm açıklamaların bakın. Bu bilgiler kullanıcının anlamak ve komut yönetmek için yardımcı olur.

  Örneğin, aşağıdaki ayrıntılı açıklama Yeni konu komutu bir komut dosyası olduğunu belirtir. Bu, bunlar çalıştırdığınızda tam adını ve yolunu belirtmek için ihtiyaç duydukları kullanıcılar anımsatır.

  > "Yeni konu betik... girdi dosyasındaki, her bir konu adı için boş bir kavramsal konuya oluşturur"

  Aşağıdaki ayrıntılı açıklama bildiren `Disable-PSRemoting` bir işlevdir. Oturum bazıları daha yüksek önceliğe sahip bir komut tarafından gizlenebilir aynı ada sahip birden çok komut içerdiğinde bu bilgiler kullanıcıları için özellikle yararlıdır.

  > `Disable-PSRemoting` İşlevi devre dışı bırakır, yerel bilgisayardaki tüm oturum yapılandırmalarıyla...

- Betik Yardım konusunu, betiği bir bütün olarak kullanmak açıklanmaktadır. Betikte, İşlevler için Yardım konuları da yazıyorsanız, betik Yardım konusu işlevlerde bahsedin ve betik Yardım konusunun ilgili bağlantılar bölümünde işlevi Yardım konuları başvurular içerir. Buna karşılık, bir işlev bir betiğinin bir parçası olduğunda, betik ve nasıl, bağımsız olarak kullanılabileceğine işlevi oynadığı rol işlevi Yardım konusunda açıklanmaktadır. Ardından işlev Yardım konusunun ilgili bağlantılar bölümündeki betik Yardım konusuna listeleyin.

- Örnekler için bir betik Yardım konusu yazma, betik dosyasının yolunu örnek komutta içereceğiniz emin olun. Komut geçerli dizinde olsa bile, yolu açıkça belirtmeniz gerekir, anımsatma yapar.

- İşlev Yardım konusunda kullanıcılara işlevi yalnızca mevcut oturum var ve diğer oturumlarda kullanmak için eklemek veya bir PowerShell profili eklemek için ihtiyaçları hatırlatın.

- `Get-Help` yalnızca doğru konumda Yardım konusu dosyaları ve komut dosyası kaydedildiğinde bir betik veya işlevdeki için Yardım konusunu görüntüler. Bu nedenle, PowerShell, yükleme veya kaydetme veya betik veya işlevdeki bir betik veya işlevdeki Yardım konusundaki yükleme yönergelerini içeren yararlı olmaz. Bunun yerine, betik veya işlevdeki dağıtmak için kullandığınız belgede herhangi bir yükleme yönergeleri içerir.

## <a name="see-also"></a>Ayrıca bkz:

 [Betik ve işlevlerde için XML tabanlı Yardım konuları yazma](./writing-xml-based-help-topics-for-scripts-and-functions.md)

 [Komutları için XML tabanlı Yardım konuları yazma](./writing-xml-based-help-topics-for-commands.md)

 [Açıklama tabanlı Yardım konuları yazma](./writing-comment-based-help-topics.md)
