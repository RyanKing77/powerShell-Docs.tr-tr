---
title: Etkinlik parametreleri | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6e4e0cf6-19e0-44b8-8b40-d6f6075276cf
caps.latest.revision: 5
ms.openlocfilehash: 489d8bcdabe904d6a3d2bc6cdb9d7e23d09cbef2
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251226"
---
# <a name="activity-parameters"></a>Etkinlik Parametreleri

Aşağıdaki tabloda, etkinlik parametreleri için işlevselliği ve önerilen adlarını listeler.

|Parametre|İşlevsellik|
|---|---|
|**Ekleme**<br>Veri türü: SwitchParameter|Parametresi belirtildiğinde kullanıcı içerik kaynak sonuna ekleyebilirsiniz, böylece bu parametre uygulayın.|
|**CaseSensitive**<br>Veri türü: SwitchParameter|Parametresi belirtildiğinde kullanıcı büyük/küçük harfe duyarlılık gerektirebilir için bu parametreyi uygulayın.|
|**Komutu**<br>Veri türü: Dize|Kullanıcı çalıştırılacak bir komut dizesi belirtmek için bu parametreyi uygulayın.|
|**CompatibleVersion**<br>Veri türü: System.Version nesnesi|Cmdlet'i önceki sürümleriyle uyumluluk için ile uyumlu olması gereken semantiği kullanıcı belirtmek için bu parametreyi uygulayın.|
|**Sıkıştırma**<br>Veri türü: SwitchParameter|Parametresi belirtildiğinde veri sıkıştırma kullanılmasını sağlamak amacıyla, bu parametre uygulayın.|
|**Sıkıştırma**<br>Veri türü: Anahtar sözcüğü|Kullanıcı veri sıkıştırma için kullanılacak algoritmasını belirtmek için bu parametreyi uygulayın.|
|**Sürekli**<br>Veri türü: SwitchParameter|Bu parametre, kullanıcının cmdlet kapsayıcınızın parametresi belirtildiğinde veriler işlenir böylece uygulayın. Parametre belirtilmezse, cmdlet önceden tanımlanmış bir miktarda veri işler ve sonra da işlemi sonlandırır.|
|**Oluşturma**<br>Veri türü: SwitchParameter|Parametresi belirtildiğinde bir zaten mevcut değilse bir kaynak oluşturulduğunu belirtmek için bu parametreyi uygulayın.|
|**Silme**<br>Veri türü: SwitchParameter|Cmdlet parametresi belirtildiğinde kendi işlemi tamamlandığında, kaynaklar silinir, bu parametre uygulayın.|
|**Boşaltma**<br>Veri türü: SwitchParameter|Parametresi belirtildiğinde cmdlet yeni veri işlemeden önce bekleyen iş öğeleri işlenir belirtmek için bu parametreyi uygulayın. Parametre belirtilmezse, iş öğelerinin hemen işlenir.|
|**silme**<br>Veri türü: Int32|Bu parametre, kullanıcının kaç kez silinmeden önce bir kaynak silinir belirtebilirsiniz böylece uygulayın.|
|**errorLevel**<br>Veri türü: Int32|Kullanıcı raporuna hatalarının düzeyini belirtmek için bu parametreyi uygulayın.|
|**Hariç tutma**<br>Veri türü: String[]|Bu parametre, böylece kullanıcı etkinliği bir şey hariç tutabilirsiniz uygulayın. Giriş filtrelerini kullanma hakkında daha fazla bilgi için bkz. [filtre parametrelerini](input-filter-parameters.md).|
|**Filtre**<br>Veri türü: Anahtar sözcüğü|Bu parametre, kullanıcının cmdlet'i eylemi gerçekleştirmek bağlı kaynaklar seçen bir filtre belirtebilirsiniz böylece uygulayın. Giriş filtrelerini kullanma hakkında daha fazla bilgi için bkz. [filtre parametrelerini](./input-filter-parameters.md).|
|**İzleyin**<br>Veri türü: SwitchParameter|Bu parametre, böylece parametresi belirtildiğinde ilerleme izlenir uygulayın.|
|**Zorla**<br>Veri türü: SwitchParameter|Parametresi belirtildiğinde kısıtlamaları karşılaşılan olsa bile bir eylem kullanıcının gerçekleştirebileceği belirtmek için bu parametreyi uygulayın. Parametresi, güvenliği tehlikeye izin vermez. Örneğin, bu parametre, salt okunur dosyanın üzerine bir kullanıcı olanak sağlar.|
|**İçerir**<br>Veri türü: String[]|Bu parametre, böylece kullanıcı bir şey bir etkinlik içerebilir uygulayın. Giriş filtrelerini kullanma hakkında daha fazla bilgi için bkz. [filtre parametrelerini](input-filter-parameters.md).|
|**Artımlı**<br>Veri türü: SwitchParameter|Parametresi belirtildiğinde işleme artımlı olarak gerçekleştirildiğini belirtmek için bu parametreyi uygulayın. Örneğin, bu parametre yalnızca son yedeklemeden bu yana dosyaları yedekleme artımlı yedeklemeler sağlar.|
|**Inputobject**<br>Veri türü: Nesne|Bu parametre, cmdlet diğer cmdlet'lerinden giriş aldığı durumlarda uygulayın. Tanımladığınızda bir **Inputobject** parametresi her zaman belirtin **ValueFromPipeline** bildirdiğinizde, anahtar sözcüğü **parametre** özniteliği. Giriş filtrelerini kullanma hakkında daha fazla bilgi için bkz. [filtre parametrelerini](./input-filter-parameters.md).|
|**Ekle**<br>Veri türü: SwitchParameter|Parametresi belirtildiğinde cmdlet, bir öğe ekler. Bu parametre uygulayın.|
|**Etkileşimli**<br>Veri türü: SwitchParameter|Parametresi belirtildiğinde kullanıcıyla cmdlet'i etkileşimli olarak çalışır. böylece, bu parametre uygulayın.|
|**aralığı**<br>Veri türü: HashTable|Bu parametre değerleri içeren bir karma tablo anahtar sözcüklerin kullanıcı belirtebilirsiniz böylece uygulayın. Örnek değerler için aşağıdaki örnekte **aralığı** parametresi: `-interval @{ResumeScan=15; Retry=3}`.|
|**Günlük**<br>Veri türü: SwitchParameter|Parametresi belirtildiğinde bu parametre denetimi cmdlet'inin eylemleri uygulayın.|
|**NoClobber**<br>Veri türü: SwitchParameter|Bu parametre, böylece parametresi belirtildiğinde kaynağın üzerine yazılmaz uygulayın. Bu parametre, genellikle yeni nesneler oluşturabilir ve böylece aynı ada sahip mevcut nesnelerin üzerine yazılmasını engellenebilir cmdlet'leri için geçerlidir.|
|**Bildir**<br>Veri türü: SwitchParameter|Bu parametre, böylece kullanıcı parametresi belirtildiğinde etkinlik tamamlandıktan bildirilir uygulayın.|
|**NotifyAddress**<br>Veri türü: E-posta adresi|Kullanıcı bildirim göndermek için kullanılacak e-posta adresini belirtmek için bu parametreyi uygulamak, **bildirim** parametre belirtildi.|
|**Üzerine yaz**<br>Veri türü: SwitchParameter|Bu parametre, böylece parametresi belirtildiğinde cmdlet tüm mevcut verilerin üzerine yazar uygulayın.|
|**Sor**<br>Veri türü: Dize|Bu parametre, kullanıcının cmdlet için bir istem belirtebilirsiniz böylece uygulayın.|
|**Sessiz**<br>Veri türü: SwitchParameter|Cmdlet parametresi belirtildiğinde kullanıcı geri bildirim sırasında eylemlerini engeller. Bu parametre uygulayın.|
|**Recurse**<br>Veri türü: SwitchParameter|Parametresi belirtildiğinde cmdlet yinelemeli olarak eylemlerini kaynaklardaki gerçekleştirir. böylece, bu parametre uygulayın.|
|**Onar**<br>Veri türü: SwitchParameter|Bu parametre, böylece cmdlet parametresi belirtildiğinde bir şey bozuk durumdan düzeltmek dener uygulayın.|
|**RepairString**<br>Veri türü: Dize|Kullanıcı bir dize ne zaman kullanılacağını belirtmek için bu parametreyi uygulamak **onarım** parametre belirtildi.|
|**yeniden deneme**<br>Veri türü: Int32|Kullanıcı bir eylem cmdlet çalışacağı deneme sayısını belirtmek için bu parametreyi uygulayın.|
|**Seçin**<br>Veri türü: Anahtar sözcük dizisi|Kullanıcının bir dizi öğelerinin türlerini belirtmek için bu parametreyi uygulayın.|
|**Stream**<br>Veri türü: SwitchParameter|Bu parametre, parametre belirtildiğinde birden çok çıkış nesnelerini ardışık düzeninden kullanıcı akışını şekilde uygulayın.|
|**Katı**<br>Veri türü: SwitchParameter|Bu parametre, böylece parametresi belirtildiğinde tüm hataları sonlandıran hatalar olarak işlenmesini uygulayın.|
|**TempLocation**<br>Veri türü: Dize|Kullanıcı cmdlet'inin işlemi sırasında kullanılan geçici veri konumunu belirtmek için bu parametreyi uygulayın.|
|**zaman aşımı**<br>Veri türü: Int32|Bu parametre, kullanıcının zaman aşımı aralığı (milisaniye cinsinden) belirtebilirsiniz böylece uygulayın.|
|**Kes**<br>Veri türü: SwitchParameter|Bu parametre, böylece parametresi belirtildiğinde cmdlet eylemlerini kısaltabilir uygulayın. Bu parametre belirtilmemişse cmdlet başka bir eylem gerçekleştirir.|
|**Doğrulayın**<br>Veri türü: SwitchParameter|Cmdlet parametresi belirtildiğinde bir eylem oluşup oluşmadığını belirlemek için test edecek, bu parametre uygulayın.|
|**bekleme**<br>Veri türü: SwitchParameter|Bu parametre, cmdlet parametresi belirtildiğinde devam etmeden önce kullanıcı girişi beklemesi uygulayın.
|**Bekleme süresi**<br>Veri türü: Int32|Kullanıcı Süresi (saniye cinsinden) belirtmek için bu parametreyi uygulamak cmdlet için kullanıcı bekler, giriş ne zaman **bekleyin** parametre belirtildi.|

## <a name="see-also"></a>Ayrıca bkz:

[Cmdlet parametreleri](./cmdlet-parameters.md)

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK'sı](../windows-powershell-reference.md)
