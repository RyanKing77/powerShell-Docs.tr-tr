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
ms.openlocfilehash: 32e2b8acf33bc733c5e4cab94a721076ff46225d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849094"
---
# <a name="activity-parameters"></a>Etkinlik Parametreleri

Aşağıdaki tabloda, etkinlik parametreleri için işlevselliği ve önerilen adlarını listeler.

Veri türü ekleyin: SwitchParameter

Parametresi belirtildiğinde kullanıcı içerik kaynak sonuna ekleyebilirsiniz, böylece bu parametre uygulayın.

CaseSensitive veri türü: SwitchParameter

Parametresi belirtildiğinde kullanıcı büyük/küçük harfe duyarlılık gerektirebilir için bu parametreyi uygulayın.

Komut veri türü: Dize

Kullanıcı çalıştırılacak bir komut dizesi belirtmek için bu parametreyi uygulayın.

CompatibleVersion veri türü: System.Version nesnesi

Cmdlet'i önceki sürümleriyle uyumluluk için ile uyumlu olması gereken semantiği kullanıcı belirtmek için bu parametreyi uygulayın.

Veri türü sıkıştırma: SwitchParameter

Parametresi belirtildiğinde veri sıkıştırma kullanılmasını sağlamak amacıyla, bu parametre uygulayın.

Veri türü sıkıştırma: Anahtar sözcüğü

Kullanıcı veri sıkıştırma için kullanılacak algoritmasını belirtmek için bu parametreyi uygulayın.

Sürekli veri türü: SwitchParameter

Bu parametre, kullanıcının cmdlet kapsayıcınızın parametresi belirtildiğinde veriler işlenir böylece uygulayın. Parametre belirtilmezse, cmdlet önceden tanımlanmış bir miktarda veri işler ve sonra da işlemi sonlandırır.

Veri türü oluşturun: SwitchParameter

Parametresi belirtildiğinde bir zaten mevcut değilse bir kaynak oluşturulduğunu belirtmek için bu parametreyi uygulayın.

Veri türü silin: SwitchParameter

Cmdlet parametresi belirtildiğinde kendi işlemi tamamlandığında, kaynaklar silinir, bu parametre uygulayın.

Veri türü Boşalt: SwitchParameter

Parametresi belirtildiğinde cmdlet yeni veri işlemeden önce bekleyen iş öğeleri işlenir belirtmek için bu parametreyi uygulayın. Parametre belirtilmezse, iş öğelerinin hemen işlenir.

Veri türü sil: Int32

Bu parametre, kullanıcının kaç kez silinmeden önce bir kaynak silinir belirtebilirsiniz böylece uygulayın.

ErrorLevel veri türü: Int32

Kullanıcı raporuna hatalarının düzeyini belirtmek için bu parametreyi uygulayın.

Veri türü hariç tut: String[]

Bu parametre, böylece kullanıcı etkinliği bir şey hariç tutabilirsiniz uygulayın. Giriş filtrelerini kullanma hakkında daha fazla bilgi için bkz. [filtre parametrelerini](./input-filter-parameters.md).

Filtre veri türü: Anahtar sözcüğü

Bu parametre, kullanıcının cmdlet'i eylemi gerçekleştirmek bağlı kaynaklar seçen bir filtre belirtebilirsiniz böylece uygulayın. Giriş filtrelerini kullanma hakkında daha fazla bilgi için bkz. [filtre parametrelerini](./input-filter-parameters.md).

Veri türü izleyin: SwitchParameter

Bu parametre, böylece parametresi belirtildiğinde ilerleme izlenir uygulayın.

Zorlama veri türü: SwitchParameter

Parametresi belirtildiğinde kısıtlamaları karşılaşılan olsa bile bir eylem kullanıcının gerçekleştirebileceği belirtmek için bu parametreyi uygulayın. Parametresi, güvenliği tehlikeye izin vermez. Örneğin, bu parametre, salt okunur dosyanın üzerine bir kullanıcı olanak sağlar.

Veri türü şunlardır: String[]

Bu parametre, böylece kullanıcı bir şey bir etkinlik içerebilir uygulayın. Giriş filtrelerini kullanma hakkında daha fazla bilgi için bkz. [filtre parametrelerini](./input-filter-parameters.md).

Artımlı veri türü: SwitchParameter

Parametresi belirtildiğinde işleme artımlı olarak gerçekleştirildiğini belirtmek için bu parametreyi uygulayın. Örneğin, bu parametre yalnızca son yedeklemeden bu yana dosyaları yedekleme artımlı yedeklemeler sağlar.

Inputobject veri türü: Nesne

Bu parametre, cmdlet diğer cmdlet'lerinden giriş aldığı durumlarda uygulayın. Tanımladığınızda bir `InputObject` parametresi her zaman belirtin `ValueFromPipeline` bildirdiğinizde, anahtar sözcüğü **parametre** özniteliği. Giriş filtrelerini kullanma hakkında daha fazla bilgi için bkz. [filtre parametrelerini](./input-filter-parameters.md).

Veri türü ekleyin: SwitchParameter

Parametresi belirtildiğinde cmdlet, bir öğe ekler. Bu parametre uygulayın.

Etkileşimli veri türü: SwitchParameter

Parametresi belirtildiğinde kullanıcıyla cmdlet'i etkileşimli olarak çalışır. böylece, bu parametre uygulayın.

Aralık veri türü: HashTable

Bu parametre değerleri içeren bir karma tablo anahtar sözcüklerin kullanıcı belirtebilirsiniz böylece uygulayın. Örnek değerler için aşağıdaki örnekte `Interval` parametresi: `-interval @{ResumeScan=15; Retry=3}`.

Günlük veri türü: SwitchParameter

Parametresi belirtildiğinde bu parametre denetimi cmdlet'inin eylemleri uygulayın.

NoClobber veri türü: SwitchParameter

Bu parametre, böylece parametresi belirtildiğinde kaynağın üzerine yazılmaz uygulayın. Bu parametre, genellikle yeni nesneler oluşturabilir ve böylece aynı ada sahip mevcut nesnelerin üzerine yazılmasını engellenebilir cmdlet'leri için geçerlidir.

Veri türü bildirmek: SwitchParameter

Bu parametre, böylece kullanıcı parametresi belirtildiğinde etkinlik tamamlandıktan bildirilir uygulayın.

NotifyAddress veri türü: E-posta adresi

Kullanıcı bildirim göndermek için kullanılacak e-posta adresini belirtmek için bu parametreyi uygulamak, `Notify` parametre belirtildi.

Veri türü üzerine yaz: SwitchParameter

Bu parametre, böylece parametresi belirtildiğinde cmdlet tüm mevcut verilerin üzerine yazar uygulayın.

Komut istemi veri türü: Dize

Bu parametre, kullanıcının cmdlet için bir istem belirtebilirsiniz böylece uygulayın.

Sessiz veri türü: SwitchParameter

Cmdlet parametresi belirtildiğinde kullanıcı geri bildirim sırasında eylemlerini engeller. Bu parametre uygulayın.

Veri türü recurse: SwitchParameter

Parametresi belirtildiğinde cmdlet yinelemeli olarak eylemlerini kaynaklardaki gerçekleştirir. böylece, bu parametre uygulayın.

Onarım veri türü: SwitchParameter

Bu parametre, böylece cmdlet parametresi belirtildiğinde bir şey bozuk durumdan düzeltmek dener uygulayın.

RepairString veri türü: Dize

Kullanıcı bir dize ne zaman kullanılacağını belirtmek için bu parametreyi uygulamak `Repair` parametre belirtildi.

Veri türü yeniden deneme: Int32

Kullanıcı bir eylem cmdlet çalışacağı deneme sayısını belirtmek için bu parametreyi uygulayın.

Veri türünü seçin: Anahtar sözcük dizisi

Kullanıcının bir dizi öğelerinin türlerini belirtmek için bu parametreyi uygulayın.

Stream veri türü: SwitchParameter

Bu parametre, parametre belirtildiğinde birden çok çıkış nesnelerini ardışık düzeninden kullanıcı akışını şekilde uygulayın.

Katı veri türü: SwitchParameter

Bu parametre, böylece parametresi belirtildiğinde tüm hataları sonlandıran hatalar olarak işlenmesini uygulayın.

TempLocation veri türü: Dize

Kullanıcı cmdlet'inin işlemi sırasında kullanılan geçici veri konumunu belirtmek için bu parametreyi uygulayın.

Zaman aşımı veri türü: Int32

Bu parametre, kullanıcının zaman aşımı aralığı (milisaniye cinsinden) belirtebilirsiniz böylece uygulayın.

Veri türü kesin: SwitchParameter

Bu parametre, böylece parametresi belirtildiğinde cmdlet eylemlerini kısaltabilir uygulayın. Bu parametre belirtilmemişse cmdlet başka bir eylem gerçekleştirir.

Veri türünü doğrulayın: SwitchParameter

Cmdlet parametresi belirtildiğinde bir eylem oluşup oluşmadığını belirlemek için test edecek, bu parametre uygulayın.

Veri türü bekleyin: SwitchParameter

Bu parametre, cmdlet parametresi belirtildiğinde devam etmeden önce kullanıcı girişi beklemesi uygulayın.

WaitTime veri türü: Int32

Kullanıcı Süresi (saniye cinsinden) belirtmek için bu parametreyi uygulamak cmdlet için kullanıcı bekler, giriş ne zaman `Wait` parametre belirtildi.

## <a name="see-also"></a>Ayrıca bkz:

[Cmdlet parametreleri](./cmdlet-parameters.md)

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK'sı](../windows-powershell-reference.md)
