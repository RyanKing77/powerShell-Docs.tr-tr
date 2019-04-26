---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 0bc085588190f134c4a687c952509aa256b5f840
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085210"
---
# <a name="just-enough-administration-jea"></a>Yeterli Yönetim (JEA)
Yeterli yönetim, WMF 5.0, rol tabanlı yönetim üzerinden PowerShell uzaktan iletişimini sağlayan yeni bir özelliktir.  Altyapınız kısıtlanmış uç noktası, yönetici olmayanların belirli komutları, betikleri ve yürütülebilir dosyalar, bir yönetici olarak çalıştırmak sağlayarak genişletir.  Bu, ortamınızda tam yönetici sayısını azaltmak ve güvenliğinizi artırmak sağlar.  JEA, her şeyi, PowerShell aracılığıyla yönetmek için çalışır; PowerShell ile bir şey yönetebilir, JEA daha güvenli bir şekilde yapmanıza yardımcı olabilir.  Yeterli yönetim ayrıntılı bilgi için kullanıma [Kılavuzu deneyimi](http://aka.ms/JEA).

Eski kısıtlanmış uç noktaları JEA güçlü ve kolayca yapılandırılabilir.  Kullanıcı özellikleri jea tabletleri ayrıntılı olarak, hangi parametre kümeleri ve değerleri, belirli bir komut için sağlanabilir kısıtlama aşağı denetlenebilir. Kullanıcının Eylemler yönetici eylemleri gerçekleştirmek için haklara sahip tek seferlik bir sanal hesabı bağlamında çalışır.  Kullanıcı tarafından çağrılan komutları güvenlik denetimleri için kaydedilebilir.

JEA kısıtlanmış uç noktaları ile yapılandırılan oluşturmanızı sağlayarak çalışır.  Bu uç noktaları, birkaç önemli özelliklere sahiptir:

1. Bunları "olarak ayrıcalıklı sanal yalnızca bu uzak oturumu boyunca var olan hesap Çalıştır" bağlanan kullanıcılar.  Varsayılan olarak, bu sanal hesap bir etki alanı yöneticileri etki alanı denetleyicilerinde yanı sıra yerleşik Yöneticiler grubunun üyesi olan (Not: Bu izinleri yapılandırılabilir). Bir kullanıcı olarak bağlanma ve farklı, ayrıcalıklı bir kullanıcısı olarak çalıştıran ayrıcalıklı olmayan kullanıcılara sistemlerinize yönetici hakları vermeden belirli yönetim görevlerini gerçekleştirmek izin verebilirsiniz.
2. Uç nokta aşağı kilitli.  Bu PowerShell Hayır dil modda çalışır anlamına gelir.  Yalnızca belirli komutları, betikleri ve yürütülebilir dosyalar, kullanıcı tarafından görülebilir.
3. Bağlanan farklı kullanıcılar, farklı bir grup üyeliğine dayalı bir özellik kümesi ile sunulur.  Aynı uç noktasında farklı özellikleri farklı rolleri sağlayabilir.
