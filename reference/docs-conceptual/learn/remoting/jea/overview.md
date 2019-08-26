---
ms.date: 07/10/2019
keywords: Jea, PowerShell, güvenlik
title: Yalnızca yeterince yönetime genel bakış
ms.openlocfilehash: 4b74e5be9558810748a8844a325c8213e1b3ebc9
ms.sourcegitcommit: e894ed833cef57967cdaf002f8c883f66864e836
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2019
ms.locfileid: "70017863"
---
# <a name="just-enough-administration"></a>Yeterli Yönetim

Yalnızca yeterli yönetim (JEA), PowerShell tarafından yönetilen herhangi bir şey için Temsilcili yönetim sağlayan bir güvenlik teknolojisidir. JEA ile şunları yapabilirsiniz:

- Düzenli kullanıcılar adına ayrıcalıklı eylemler gerçekleştirmek için sanal hesapları veya grup tarafından yönetilen hizmet hesaplarını kullanarak **makinelerinizdeki yöneticilerin sayısını azaltın** .
- Hangi cmdlet 'leri, işlevleri ve dış komutları çalıştırabileceklerini belirterek **Kullanıcıların neler yapabileceğini sınırlayın** .
- Kullanıcılarınızın oturumu sırasında hangi komutların yürütüldüğünü tam olarak gösteren yazılı betikler ve günlüklerle **ne yaptığını daha iyi anlayın** .

**Neden JEA önemli?**

Sunucularınızı yönetmek için kullanılan, yüksek ayrıcalıklı hesaplar önemli bir güvenlik riski oluşturur. Bir saldırgan bu hesaplardan birinin güvenliğini tehlikeye atamalıdır, kuruluşunuzda [yan yana saldırıları](https://aka.ms/pth) başlatabilir. Güvenliği aşılmış her hesap, bir saldırganın daha fazla hesap ve kaynağa erişmesini sağlar ve şirket gizli dizilerini çalmaya, hizmet reddi saldırısı başlatmaya ve daha fazlasını bir adım daha yakına geçirir.

Her iki yönetici ayrıcalıklarını da kaldırmak her zaman kolay değildir. DNS rolünün Active Directory Etki Alanı denetleyicinize göre aynı makineye yüklendiği yaygın senaryoyu göz önünde bulundurun. DNS yöneticileriniz, DNS sunucusuyla ilgili sorunları gidermek için yerel yönetici ayrıcalıkları gerektirir. Ancak bunu yapmak için, bunları yüksek ayrıcalıklı **etki alanı yöneticileri** güvenlik grubunun üyesi yapmanız gerekir. Bu yaklaşım, tüm etki alanınız üzerinde DNS yöneticileri denetimi ve o makinedeki tüm kaynaklara erişim sağlar.

JEA bu sorunu **en az ayrıcalık**ilkesiyle gidermektedir. JEA ile, DNS yöneticileri için onlara yalnızca işlerini yapmak için ihtiyaç duydukları PowerShell komutlarına erişim sağlayan bir yönetim uç noktası yapılandırabilirsiniz. Bu, zarar görmüş bir DNS önbelleğini onarmak için uygun erişimi sağlayabilmeniz veya dosya sistemine gözatılmanıza ya da dosya sistemine gözatmanıza ya da tehlikeli olabilecek betikler çalıştırmanıza gerek Active Directory kalmadan DNS sunucusunu yeniden başlatmanıza olanak sağlar. Daha sonra, JEA oturumu geçici ayrıcalıklı sanal hesapları kullanmak üzere yapılandırıldığında, DNS yöneticileriniz **yönetici olmayan** kimlik bilgilerini kullanarak sunucuya bağlanabilir ve genellikle yönetici ayrıcalıkları gerektiren komutları çalıştırmaya devam edebilir. JEA, kullanıcıları yaygın ayrıcalıklı yerel/etki alanı yöneticisi rollerinden kaldırmanıza ve her makinede neler yapabileceğini dikkatlice denetlemenize olanak sağlar.

## <a name="next-steps"></a>Sonraki adımlar

JEA kullanma gereksinimleri hakkında daha fazla bilgi edinmek için bkz. [Önkoşullar](prerequisites.md) makalesi.

## <a name="samples-and-dsc-resource"></a>Örnekler ve DSC kaynağı

Örnek JEA yapılandırmalarının ve JEA DSC kaynağı [Jea GitHub deposunda](https://github.com/PowerShell/JEA)bulunabilir.
