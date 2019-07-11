---
ms.date: 07/10/2019
keywords: jea, powershell, güvenlik
title: Yeterli yönetim genel bakış
ms.openlocfilehash: 4b74e5be9558810748a8844a325c8213e1b3ebc9
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726654"
---
# <a name="just-enough-administration"></a>Yeterli Yönetim

Yeterli yönetim (JEA) etkinleştiren bir güvenlik teknolojisidir PowerShell tarafından yönetilen her şey için temsilci ' dir. Jea'yı ile şunları yapabilirsiniz:

- **Makinelerinizde yönetici sayısını azaltmak** kullanarak normal kullanıcılar adına ayrıcalıklı eylemler gerçekleştirmek için sanal hesaplar veya grup yönetilen hizmet hesapları.
- **Kullanıcıların ne yaptığını sınırlamak** belirterek hangi cmdlet'ler, İşlevler ve dış komutları çalıştırabilirsiniz.
- **Kullanıcılarınızın neler yaptığını daha iyi anlamak** dökümleri ve günlüklerle gösteren, tam olarak hangi kullanıcıların oturumu sırasında yürütülen bir kullanıcı komutları.

**JEA neden önemlidir?**

Üst düzeyde ayrıcalıklı hesapların sunucularınızı yönetmek için kullanılan bir ciddi bir güvenlik riski. Bir saldırganın tehlikeye Bu hesaplardan birini, bunlar başlatabilir [yana saldırıları](https://aka.ms/pth) kuruluşunuzdaki. Her gizliliği tehlikeye giren hesap bir saldırgan daha fazla hesap ve kaynaklar da erişimi sağlar ve bunları şirket gizli öğeleri ve bir hizmet reddi saldırısı başlatma çalmak için bir adım daha yaklaştınız koyar.

Her zaman yönetim ayrıcalıkları ya da kaldırmak kolay değildir. DNS rolü, Active Directory etki alanı denetleyicisi ile aynı makinede yüklendiği bir ortak senaryoyu ele alalım. DNS Yöneticiler, DNS sunucusu ile sorunları gidermek için yerel yönetici ayrıcalıkları gerektirir. Bunu yapmak için üyelerinin yüksek ayrıcalıklı yapmanız gerekir, ancak **Domain Admins** güvenlik grubu. Bu yaklaşım, o makinedeki tüm kaynaklara erişim ve tam etki alanı DNS yöneticileri denetime etkili bir şekilde sağlar.

JEA ilkesini bu sorunu ele **en az ayrıcalık**. Jea'yı ile bunların erişim işin yapılması için ihtiyaç duydukları yalnızca PowerShell komutlarına DNS Yöneticiler için yönetim uç noktası yapılandırabilirsiniz. Başka bir deyişle, zarar görmüş bir DNS önbelleği onarmak veya DNS sunucusu Active Directory'ye yönelik haklara vermeden olmadan yanlışlıkla yeniden başlatmanız ya da dosya sistemine gözatmak için uygun erişim sağlamak veya potansiyel olarak tehlikeli olabilecek bir komut çalıştırın. JEA oturumu geçici ayrıcalıklı sanal hesaplarını kullanmak için yapılandırıldığında, daha da iyisi, DNS yöneticilerinize kullanarak sunucuya bağlanabilirsiniz **yönetici olmayan** kimlik bilgilerini ve yönetici genellikle gerektiren hala çalıştırma komutları ayrıcalık yok. JEA kullanıcıların yaygın olarak ayrıcalıklı yerel/etki alanı yönetici rollerini kaldırın ve dikkatli bir şekilde her bir makinede ne yapabileceklerini denetlemenizi sağlar.

## <a name="next-steps"></a>Sonraki adımlar

Jea'yı kullanmak için gereksinimler hakkında daha fazla bilgi için bkz: [önkoşulları](prerequisites.md) makalesi.

## <a name="samples-and-dsc-resource"></a>Örnekler ve DSC kaynağı

Örnek JEA yapılandırmaları ve JEA DSC kaynağı bulunabilir [JEA GitHub deposu](https://github.com/PowerShell/JEA).
