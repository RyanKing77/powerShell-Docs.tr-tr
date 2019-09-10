---
title: PowerShell betikleri ve Işlevleri için yardım yazma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 859a6e22-75b1-43d4-ba62-62c107803b37
caps.latest.revision: 7
ms.openlocfilehash: af989fb2eeba6b68f2e3e6506f3f60d5be6f7d8a
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848091"
---
# <a name="writing-help-for-powershell-scripts-and-functions"></a>PowerShell betikleri ve Işlevleri için yardım yazma

PowerShell betikleri ve işlevleri, başkalarıyla her paylaşılırken tamamen belgelenmelidir.
Cmdlet 'i, komut dosyası ve işlev yardım konularını cmdlet 'ler için yardım görüntülediği biçimde görüntüler ve tüm `Get-Help` parametrelerin betiği ve işlevleri Yardım konuları üzerinde çalışır. `Get-Help`

PowerShell betikleri, komut dosyası ve betikteki her işlevlerle ilgili yardım konuları hakkında bir yardım konusu içerebilir.
Betiklerden bağımsız olarak paylaşılan işlevler kendi yardım konularını içerebilir.

Bu belgede Yardım konularının biçimi ve doğru yerleşimi açıklanmakta ve içerik için yönergeler önerilmektedir.

## <a name="types-of-script-and-function-help"></a>Betik ve Işlev yardımı türleri

### <a name="comment-based-help"></a>Açıklama tabanlı yardım
Betiği veya işlevi açıklayan Yardım konusu, betik veya işlev içinde bir açıklama kümesi olarak uygulanabilir.
Bir komut dosyası ve bir betikteki işlevler için açıklama tabanlı yardım yazarken, açıklama tabanlı yardım yerleştirmekle ilgili kurallara dikkat edin.
Yerleştirme, `Get-Help` cmdlet 'in yardım konusunu betikle veya bir işlevle ilişkilendirmesini belirler.
Açıklama tabanlı yardım konuları yazma hakkında daha fazla bilgi için bkz. [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).

### <a name="xml-based-command-help"></a>XML tabanlı komut yardımı
Komut dosyası veya işlevi açıklayan Yardım konusu, komut yardım şemasını kullanan bir XML dosyasında uygulanabilir.
Betiği veya işlevi xml dosyası ile ilişkilendirmek için, `ExternalHelp` açıklama anahtar sözcüğünü ve ardından XML dosyasının yolunu ve adını kullanın.

Açıklama anahtar sözcüğü mevcut olduğunda, `ExternalHelp` anahtar sözcüğünün değeriyle eşleşen bir yardım dosyası bulamadığında `Get-Help` bile açıklama tabanlı yardım 'dan önceliklidir. `ExternalHelp`

### <a name="online-help"></a>Çevrimiçi yardım
Yardım konularınızı Internet 'te gönderebilir ve ardından doğrudan `Get-Help` konuları açabilirsiniz.
Açıklama tabanlı yardım konuları yazma hakkında daha fazla bilgi için bkz. [çevrimiçi yardımı destekleme](../module/supporting-online-help.md).

Betikler ve işlevler için kavramsal ("hakkında") konuları yazmak için bir yöntem yoktur.
Bununla birlikte, bir komut Yardım konusunun Ilgili bağlantılar bölümünde yer alan konuları ve bunların URL 'Lerini Internet üzerinde kavramsal konular gönderebilirsiniz.

## <a name="content-considerations-for-script-and-function-help"></a>Betik ve Işlev yardımı için içerik konuları

- Kullanılabilir komut yardım bölümlerinin yalnızca birkaçını içeren çok kısa bir yardım konusu yazıyorsanız, betiğin veya işlev parametrelerinin açık açıklamalarını eklediğinizden emin olun. Örnek açıklamaları atlamaya karar verseniz bile, örnekler bölümüne bir veya iki örnek komut ekleyin.

- Tüm açıklamalarda komut dosyası veya işlev olarak komutuna bakın. Bu bilgiler, kullanıcının komutu anlamasına ve yönetmesine yardımcı olur.

  Örneğin, aşağıdaki ayrıntılı açıklama, New-topic komutunun bir komut dosyası olduğunu belirtir. Bu, kullanıcılara, uygulamayı çalıştırırken yolu ve tam adı belirtmeleri gerektiğini hatırlatır.

  > "Yeni konu betiği, giriş dosyasındaki her konu adı için boş bir kavramsal konu oluşturuyor..."

  Aşağıdaki ayrıntılı açıklama, bir işlev `Disable-PSRemoting` olduğunu belirtir. Bu bilgiler özellikle, oturum aynı ada sahip birden çok komut içerdiğinde, bazıları daha yüksek önceliğe sahip bir komutla gizlenmiş olabilecek kullanıcılar için yararlıdır.

  > `Disable-PSRemoting` İşlev yerel bilgisayardaki tüm oturum yapılandırmasını devre dışı bırakır...

- Bir komut dosyası yardım konusunda, betiğin tamamını nasıl kullanacağınızı açıklayın. Ayrıca betikteki işlevlere yönelik yardım konuları yazıyorsanız, betik yardım konusundaki işlevlerden bahsedin ve betik Yardım konusunun Ilgili bağlantılar bölümünde işlev yardım konularına başvurular ekleyin. Buna karşılık, bir işlev bir betiğin parçasıysa, işlev Yardım konusunun işlevin komut dosyasında oynadığı rol ve bağımsız olarak nasıl kullanılabileceğini açıklayın. Ardından işlev Yardım konusunun Ilgili bağlantılar bölümünde betik yardım konusunu listeleyin.

- Betik yardım konusu için örnek yazarken, örnek komutuna komut dosyasının yolunu eklediğinizden emin olun. Bu, komut dosyası geçerli dizinde olduğunda bile, kullanıcılara yolu açıkça belirtmeleri gerektiğini hatırlatır.

- Bir işlev yardım konu başlığında, kullanıcılardan işlevin yalnızca geçerli oturumda mevcut olduğunu ve başka oturumlarda kullanılması gerektiğini, bunu eklemesi veya bir PowerShell profili eklemesi gerektiğini hatırlatın.

- `Get-Help`yalnızca betik dosyası ve yardım konu dosyaları doğru konumlara kaydedildiğinde bir betik veya işlev için yardım konusunu görüntüler. Bu nedenle, PowerShell 'i yükleme veya betik ya da işlev yardım konusuna kaydetme veya yükleme yönergelerini dahil etmek yararlı değildir. Bunun yerine, komut dosyasını veya işlevi dağıtmak için kullandığınız belgeye tüm yükleme yönergelerini ekleyin.

## <a name="see-also"></a>Ayrıca bkz:

[Açıklama tabanlı yardım konuları yazma](./writing-comment-based-help-topics.md)
