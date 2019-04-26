---
ms.date: 06/12/2017
keywords: jea, powershell, güvenlik
title: Yeterli yönetim genel bakış
ms.openlocfilehash: c097838fb25a63d42502eebf751c64c537bdd077
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084921"
---
# <a name="just-enough-administration"></a>Yeterli Yönetim

Yeterli yönetim (JEA) etkinleştiren bir güvenlik teknolojisidir PowerShell ile yönetilebilen her şey için temsilci ' dir.
Jea'yı ile şunları yapabilirsiniz:

- **Makinelerinizde yönetici sayısını azaltmak** normal kullanıcılar adına ayrıcalıklı eylemler gerçekleştirmek ve hizmet hesapları yararlanarak sanal hesaplar veya grup tarafından yönetilen.
- **Kullanıcıların ne yaptığını sınırlamak** belirterek hangi cmdlet'ler, İşlevler ve dış komutları çalıştırabilirsiniz.
- **Kullanıcılarınızın neler yaptığını daha iyi anlamak** dökümleri ve günlüklerle gösteren, tam olarak hangi kullanıcıların oturumu sırasında yürütülen bir kullanıcı komutları.

**Bu neden önemlidir?**

Üst düzeyde ayrıcalıklı hesapların sunucularınızı yönetmek için kullanılan bir ciddi bir güvenlik riski.
Bir saldırganın tehlikeye Bu hesaplardan birini, bunlar başlatabilir [yana saldırıları](http://aka.ms/pth) kuruluşunuzdaki.
Her hesap, tehlikeye bunları daha fazla hesap ve bunları geçirmeden kaynak çalarak şirket gizli öğeleri ve bir hizmet reddi saldırısı başlatmak için bir adım daha yaklaştınız bile için erişim verebilirsiniz.

Her zaman yönetim ayrıcalıkları ya da kaldırmak kolay değildir.
DNS rolü, Active Directory etki alanı denetleyicisi ile aynı makinede yüklendiği bir ortak senaryoyu ele alalım.
DNS Yöneticiler, DNS sunucusu ile sorunları gidermek için ancak bunları yüksek ayrıcalıklı "Domain Admins" güvenlik grubunun üyesi yapmak zorunda Bunu yapmak için yerel yönetici ayrıcalıkları gerektirir.
Bu yaklaşım, o makinedeki tüm kaynaklara erişim ve tam etki alanı DNS yöneticileri denetime etkili bir şekilde sağlar.

JEA yardımcı ilkesini benimseyin yardımcı olarak bu sorunu gidermek *en az ayrıcalık*.
Jea'yı ile bunları erişim işin yapılması için ihtiyaç duydukları tüm PowerShell komutlarına DNS yöneticileri, ancak hiçbir şey için daha fazla yönetim uç noktası yapılandırabilirsiniz.
Başka bir deyişle, zarar görmüş bir DNS önbelleği onarmak veya DNS sunucusu Active Directory'ye yönelik haklara vermeden olmadan yanlışlıkla yeniden başlatmanız ya da dosya sistemine gözatmak için uygun erişim sağlamak veya potansiyel olarak tehlikeli olabilecek bir komut çalıştırın.
JEA oturumu geçici ayrıcalıklı sanal hesaplarını kullanmak için yapılandırıldığında, daha da iyisi, DNS yöneticilerinize kullanarak sunucuya bağlanabilirsiniz *yönetici olmayan* hala genellikle gerektiren komutlar çalıştırabilir ve kimlik bilgileri Yönetici ayrıcalıkları.
Bu özellik kullanıcıların yaygın olarak ayrıcalıklı yerel/etki alanı yönetici rollerini kaldırın ve bunun yerine dikkatli bir şekilde her makinede yapmanız mümkün nedir denetlemenizi sağlar.

## <a name="get-started-with-jea"></a>JEA ile çalışmaya başlama

Jea'yı Windows Server 2016 veya Windows 10 çalıştıran herhangi bir makinede bugün kullanmaya başlayabilirsiniz.
Jea'yı, Windows Management Framework'ün güncelleştirme ile eski işletim sistemlerinde da çalıştırabilirsiniz.
JEA kullanılacağını ve nasıl oluşturulacağını öğrenmek için gereksinimleri hakkında daha fazla bilgi edinmek için kullanın ve bir JEA uç noktası denetim, aşağıdaki konu başlıklarına göz atın:

- [Önkoşullar](prerequisites.md) -JEA kullanmak için ortamınızı ayarlama açıklanmaktadır.
- [Rol işlevleri](role-capabilities.md) -oluşturma, bir kullanıcı bir JEA oturumda yapmak için izin verilenden belirleyen rolleri açıklanır.
- [Oturum yapılandırmaları](session-configurations.md) -Kullanıcıları rollerine eşlemek ve JEA kimlik JEA uç noktalarını yapılandırma açıklanmaktadır
- [Jea'yı kaydetme](register-jea.md) - bir JEA uç noktası oluşturun ve bağlanmak kullanıcılar için kullanılabilir hale getirmek.
- [Jea'yı kullanarak](using-jea.md) -JEA kullanabileceğiniz çeşitli yöntemler öğrenirsiniz.
- [Güvenlik konuları](security-considerations.md) -en iyi güvenlik uygulamaları ve JEA yapılandırma seçenekleri etkilerini gözden geçirin.
- [Denetim ve rapor JEA'da](audit-and-report.md) -denetim ve rapor üzerinde JEA uç noktaları hakkında bilgi edinin.

## <a name="samples-and-dsc-resource"></a>Örnekler ve DSC kaynağı

Örnek JEA yapılandırmaları ve JEA DSC kaynağı bulunabilir [JEA GitHub deposu](https://github.com/PowerShell/JEA).