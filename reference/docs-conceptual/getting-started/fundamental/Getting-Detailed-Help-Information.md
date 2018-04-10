---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Ayrıntılı Yardım Bilgisi Alma
ms.assetid: 6fb4daf7-8607-4a3e-b692-f77631adc1b9
ms.openlocfilehash: bb0fac4eb338354e411458fad575c726a5f0da35
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="getting-detailed-help-information"></a>Ayrıntılı Yardım Bilgisi Alma
Windows PowerShell, Windows PowerShell kavramları ve Windows PowerShell dil açıklayan ayrıntılı Yardım konuları içerir. Ayrıca her bir cmdlet'i ve sağlayıcı için Yardım konularını ve vardır birçok işlevleri ve komut dosyaları için Yardım konularını.

Komut isteminde bu Yardım konularını görüntülemek veya en yakın zamanda güncelleştirilmiş sürümleri bu konularda, Microsoft TechNet Library içinde görüntüleyin. Windows PowerShell, Windows PowerShell Tümleşik komut dosyası ortamı gibi konak birçok program derlenmiş Yardım dosyası (.chm) ve bağlama duyarlı Yardım gibi ek Yardım özellikler sağlar.

## <a name="getting-help-for-cmdlets"></a>Cmdlet'leri için Yardım alma
Windows PowerShell cmdlet'leri hakkında Yardım almak için kullanmak [Get-Help [m2]](https://technet.microsoft.com/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2) cmdlet'i. Örneğin, Yardım almak için [Get-Childıtem [m2]](https://technet.microsoft.com/library/4b270d63-c995-45b8-b5b4-3f8887efbfcc) cmdlet, türü:

```
get-help get-childitem
```

veya

```
get-childitem -?
```

Hatta, Get-Help cmdlet'i hakkında Yardım alabilirsiniz. Örneğin:

```
get-help get-help
```

Oturumunuzda tüm cmdlet'i Yardım konularını listesini almak için şunu yazın:

```
get-help -category cmdlet
```

Aynı anda her Yardım konusunun bir sayfasını görüntülemek için **yardımcı** işlevi veya diğer adını **ADAM**. Örneğin, Yardım için Get-Childıtem cmdlet'i görüntülemek için şunu yazın

```
man get-childitem
```

veya

```
help get-childitem
```

Cmdlet, işlev veya komut dosyası, kendi kullanım örnekleri ve parametre açıklamaları da dahil olmak üzere ilgili ayrıntılı bilgileri görüntülemek için kullanın *ayrıntılı* Get-Help cmdlet parametresi. Örneğin, Get-Childıtem cmdlet hakkında ayrıntılı bilgi almak için şunu yazın:

```
get-help get-childitem -detailed
```

Yardım konusundaki tüm içeriği görüntülemek için kullanın *tam* Get-Help cmdlet parametresi. Örneğin, Get-Childıtem cmdlet için Yardım konusundaki tüm içeriği görüntülemek için şunu yazın:

```
get-help get-childitem -full
```

Almak için Yardım kullanımı bir cmdlet parametreleri hakkında ayrıntılı *parametresi* Get-Help cmdlet parametresi. Örneğin, tüm türü Get-Childıtem cmdlet'i parametreleri için Yardım ayrıntılı almak için:

```
get-help get-childitem -parameter *
```

Yardım konusunun yalnızca örnekler görüntülemek için kullanın *örnek* Get-Help parametresi. Örneğin, yalnızca örnek Get-Childıtem cmdlet için Yardım konusu görüntülemek için şunu yazın:

```
get-help get-childitem -examples
```

Yazdığınız cmdlet'leri için Yardım konuları yazma hakkında daha fazla bilgi için bkz: [yazma Cmdlet Yardım nasıl](https://go.microsoft.com/fwlink/?LinkID=123415) MSDN Kitaplığı'nda.

## <a name="getting-conceptual-help"></a>Kavramsal Yardım alma
Get-Help cmdlet'i Windows PowerShell, Windows PowerShell dili ile ilgili konular da dahil olmak üzere kavramsal konuları hakkında bilgi de görüntüler. Kavramsal Yardım konuları about_line_editing gibi "about_" öneki ile başlar. (Kavramsal konu adını İngilizce bile İngilizce dışındaki sürümlerinde Windows PowerShell girilmesi gerekir.)

Kavramsal konu listesini görüntülemek için şunu yazın:

```
get-help about_*
```

Belirli bir Yardım konusu görüntülemek için konu adı, örneğin yazın:

```
get-help about_command_syntax
```

Get-Help parametrelerinin gibi *ayrıntılı*, *parametresi*, ve *örnekler*, kavramsal Yardım konularının görüntülenmesini üzerinde hiçbir etkisi yoktur.

## <a name="getting-help-about-providers"></a>Sağlayıcılar hakkında Yardım alma
Get-Help cmdlet'i Windows PowerShell sağlayıcıları hakkında bilgi görüntüler. Ardından sağlayıcı adı için bir sağlayıcı Yardım almak için "Get-Help" yazın. Örneğin, kayıt defteri sağlayıcısı için Yardım almak için şunu yazın:

```
get-help registry
```

Tüm listesini almak için oturumunuzu sağlayıcısı Yardım konularında yazın

```
get-help -category provider
```

Get-Help parametrelerinin gibi *ayrıntılı*, *parametresi*, ve *örnekler*, sağlayıcı Yardım konularının görüntülenmesini üzerinde hiçbir etkisi yoktur.

## <a name="getting-help-about-scripts-and-functions"></a>Komut dosyaları ve işlevleri hakkında Yardım alma
Çok sayıda betik ve işlevlerde Windows PowerShell'de Yardım konuları vardır. Betik ve işlevlerde için Yardım konularını görüntülemek için Get-Help cmdlet'ini kullanın.

Bir işlev için Yardım görüntülemek için "get-help işlevi adından" yazın. Örneğin, devre dışı bırak-PSRemoting işlevi için Yardım almak için şunu yazın:

```
get-help disable-psremoting
```

Bir komut dosyası için Yardım görüntülemek için komut dosyasının tam yolunu yazın. Komut dosyası Path ortam değişkeninde listelenen bir yol ise, komut yolundan atlayabilirsiniz.

Örneğin, C: "TestScript.ps1" adlı bir komut dosyası varsa\\PS Test dizin, komut dosyası türü için Yardım konusunu görüntülemek için:

```
get-help c:\ps-test\TestScript.ps1
```

Cmdlet görüntülemek için tasarlanmış olan parametreleri Yardım, gibi *ayrıntılı*, *tam*, *örnekler*, ve *parametresi*, iş için komut dosyası Yardım ve işlevi, çok yardımcı olur. Ancak, görüntülediğinizde tüm Yardım yazarak "get-help \*", yardımcı olmak için işlevleri ve komut dosyaları görünmez.

İşlevleri ve komut dosyalarınız için Yardım konuları yazma hakkında daha fazla bilgi için bkz: [about_Functions [m2]](https://technet.microsoft.com/en-us/library/61d40692-5300-4de9-a9b5-bae31815e105), [about_Scripts](https://technet.microsoft.com/en-us/library/7dc08334-dcfe-450b-b949-0554855623af), ve [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf).

## <a name="getting-help-online"></a>Çevrimiçi Yardım alma
Internet'e bağlıysanız, Yardım almak için en iyi yöntemleri çevrimiçi Yardım konularını görüntülemek için biridir. Çevrimiçi konuları güncelleştirmek kolay olduğundan, bunlar en güncel içeriği sağlamak olasıdır.

Çevrimiçi Yardım almak için deneyin *çevrimiçi* Get-Help cmdlet parametresi. *Çevrimiçi* parametresi yalnızca cmdlet Yardım için Get-Help cmdlet'i çalışır, Yardım işlev ve Yardım komut dosyası. Kullanamazsınız *çevrimiçi* parametresiyle kavramsal (hakkında) konuları veya sağlayıcı Yardım konuları. Bu özellik isteğe bağlı olduğundan, ayrıca, her cmdlet, işlev veya komut dosyası Yardım konusunu çalışmaz.

Ancak, tüm Yardım konuları gelen sağlayıcısı Yardım dahil olmak üzere Windows PowerShell ile ve (hakkında) Yardım konuları, kavramsal çevrimiçi kullanılabilir [Windows PowerShell](http://go.microsoft.com/fwlink/?LinkID=107116) Microsoft TechNet Library bölümü.

Kullanılacak *çevrimiçi* parametresi Get-Help cmdlet'i, aşağıdaki komut biçimi kullanın.

```
get-help <command-name> -online
```

Örneğin, Get-Childıtem cmdlet'i hakkında Yardım konusunun çevrimiçi sürümünü almak için şunu yazın:

```
get-help get-childitem -online
```

Yardım konusunun çevrimiçi sürümünü kullanılabilir durumda, varsayılan tarayıcıda açılır.

Çevrimiçi Yardım için Yardım konusunun destekleniyorsa, Yardım konusunun Internet adresi (URL) de görüntüleyebilirsiniz. Internet adresini Yardım konusunun ilgili bağlantılar bölümünde görüntülenir.

Örneğin, Add-Computer cmdlet çevrimiçi sürümünü URL'sini görmek için şunu yazın:

```
get-help add-computer
```

Konunun ilgili bağlantılar bölümündeki ilk satırı aşağıda gösterilmiştir.

```
Online version: http://go.microsoft.com/fwlink/?LinkID=135194
```

Çevrimiçi desteklemek için Yardım konuları hakkında daha fazla bilgi için bkz: [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf)ve [yazma Cmdlet Yardım nasıl](https://go.microsoft.com/fwlink/?LinkID=123415) MSDN Kitaplığı'nda.

## <a name="see-also"></a>Ayrıca bkz:
- [about_Functions [m2]](https://technet.microsoft.com/en-us/library/61d40692-5300-4de9-a9b5-bae31815e105)
- [about_Scripts](https://technet.microsoft.com/en-us/library/7dc08334-dcfe-450b-b949-0554855623af)
- [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf)
- [Get-Help [m2]](https://technet.microsoft.com/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2)