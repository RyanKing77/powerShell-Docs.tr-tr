---
ms.date: 03/27/2018
contributor: JKeithB
keywords: Galeri, powershell, psgallery, GDPR
title: PowerShell Galerisi GDPR uyumluluğu
ms.openlocfilehash: fb1191d8a1cd12d5994e41238c384eb504d0c261
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687821"
---
# <a name="powershell-gallery-gdpr-compliance"></a>PowerShell Galerisi GDPR uyumluluğu

## <a name="overview"></a>Genel bakış

Mayıs 2018'de genel veri koruma yönetmeliği (GDPR), bir Avrupa gizlilik yasaları etkisi sürdü.
GDPR, yeni şirketler, devlet kurumları, gütmeyen ve teklif mal ve hizmet kişilere Avrupa Birliği (AB) veya AB vatandaşlar için bağlı verileri toplayıp analiz, diğer kuruluşların kuralları uygular.
Burada, nerede olursanız olun GDPR geçerlidir.

> [!NOTE]
> Bu makalede, PowerShell Galerisi'nden kişisel verilerini silme adımlar sağlar ve sizin yükümlülükleriniz GDPR altında desteklemek için kullanılabilir. GDPR hakkında genel bilgiler arıyorsanız bkz [hizmet güveni portalı GDPR bölümünü](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).

## <a name="personally-identifiable-data"></a>Kişisel olarak tanımlanabilen veriler

PowerShell Galerisi, kişisel bilgileri içerebilen kullanıcılar tarafından sağlanan aşağıdaki bilgileri depolar:

- PowerShell Galerisi hesabı
- PowerShell Galerisi'nde yayımlanmış paketleri
- PowerShell Galerisi ekibi ile e-posta yazışmaları

Çoğu kullanıcı, bir PowerShell Galerisi hesabı oluşturmayın.
Paket yayımlama veya PowerShell galerisinde "Kişi sahip" Bu özelliği kullanmak için çalıştırmayacağınız sürece bir hesap gerekli değildir.
Kullanıcı tarafından başlatılan e-posta yazışmaları dışında PowerShell Galerisi bir hesabı oluşturmadığınızı kullanıcılar kişisel verilerini depolamaz.

PowerShell Galerisi hesabı oluşturan kullanıcılar paketleri PowerShell Galerisi'nde yayımlayabilirsiniz.
Bu paketleri, PowerShell kodu olması bekleniyor, ancak kişisel bilgiler dahil olmak üzere diğer bilgileri içerebilir.
Tüm paketleri nasıl alabileceğiniz aşağıdaki bilgileri gösterir PowerShell Galerisi'nden yayımlamış olursunuz.

## <a name="dsr-export-of-powershell-gallery-data"></a>PowerShell Galerisi verileri DSR dışarı aktarma

Aşağıdaki bölümlerde PowerShell Galerisi'nde bilgi dışarı aktarma ve silme, bu bilgilerin nasıl açıklayarak PowerShell Galerisi gdpr veri sahibi istekleri (DSR) nasıl desteklediği açıklanmaktadır.

### <a name="email"></a>E-posta

E-posta yazışmaları aşağıdakilerden herhangi birini içerebilir:

- Kod Analizi tarar, paketler PowerShell Galerisi'nde yayımlanmış herhangi bir paket ile ilgili bir sorun algılandı PowerShell Galerisi sahiplerine gönderilen e-posta
- Hiç kimse tarafından "Bize başvurun" sayfasında e-posta adresini kullanarak PowerShell Galerisi ekibine gönderilen e-posta [cgadmin@microsoft.com](mailto:cgadmin@microsoft.com)
- Kayıtlı bir paket PowerShell galerisinde sahibini e-posta göndermek için PowerShell galerisinde "Kişi sahip" özelliğini kullanan kullanıcılar

PowerShell Galerisi veya tarafından gönderilen e-postaları, olası güvenlik araştırmalar kötü amaçlı kod PowerShell galerisinde bulunmasına desteklemek için 90 günlük bir bekletme ilkesi olması.
E-posta İlkesi tarafından 90 gün sonra silinir.

Gelen e-posta adresinizi ve PowerShell Galerisi veya önceki 90 gün içinde gönderilen tüm e-posta kopyalarını isteyebilir.
Bu yazışma istemek için bir e-posta Gönder [ cgadmin@microsoft.com ](mailto:cgadmin@microsoft.com), başlık ile: "DSR istek bu hesaba ilişkin e-postalar için".
Hangi bilgilerin istiyorsunuz iletisinin gövdesinde, durum (örneğin: Lütfen bu e-posta adresinden alınan veya gönderilen tüm e-posta gönderin.) 7 iş günü içinde e-posta adresinizi isteğin 90 gün içinde ilgili tüm e-postalar gönderilir.

### <a name="powershell-gallery-account-information"></a>PowerShell Galerisi hesap bilgileri

PowerShell Galerisi hesabı oluşturduysanız, PowerShell Galerisi'nde aşağıdaki adımları izleyerek daha fazladır saklanan tüm kişisel bilgileri bulabilirsiniz:

1. PowerShell Galerisi için oturum açın, sonra kullanıcı adınıza tıklayın
2. Sonraki sayfada görüntülenen gösterir PowerShell Galerisi hesabı için kullanılan e-posta adresine hesap sayfası olan

PowerShell galerisinde birden fazla hesabı oluşturduysanız, her hesap için bu adımları yinelemeniz gerekecektir.

### <a name="packages-in-the-powershell-gallery"></a>PowerShell Galerisi paketleri

Dışarı aktarılan paketleri PowerShell Galerisi'nde yayımlanmış kolaylaştırmak için "GetPSGalleryItemsForAuthor" betik PowerShell Galerisi'nde yayımladık.
Bu betik, her pakette depolanan Yazar bilgileri temel alarak PowerShell Galerisi yerleştirerek her paket sürümünün bir kopyasını dışarı aktarır.

> [!NOTE]
> Paketiniz yayımladığınızda Yazar paketi bildiriminde saklanır.
> Yazar PowerShell Galerisi'nde kullandığınız hesap aynı kimliğe olduğunu garanti yoktur.
> Yazar alanı başka bir değer kullanıyorsanız, bu komut dosyası kullanırken bu değer belirtmeniz gerekir.

Aşağıdaki PowerShell komutunu kullanarak betiği yükleyebilirsiniz:

```powershell
Save-Script Get-repository psgallery
```

Betik aşağıdaki PowerShell komutlarını çalıştırarak, doğrudan, ardından çalıştırabilirsiniz:

```powershell
# cd <local folder location>
.\GetPSGalleryItemsForAuthor.ps1
```

Yazar ve kaydedilmesi için paketlerini istediğiniz klasör sisteminize sağlamanız istenir.

## <a name="deleting-personal-data-from-the-powershell-gallery"></a>PowerShell Galerisi'nden kişisel verileri silme

PowerShell Galerisi hesabınız veya PowerShell Galerisi'nde olduğunuz herhangi bir paket silmek için e-posta Gönder cgadmin@microsoft.com başlığıyla: "GDPR istemek için bu hesaba ilişkin öğeleri".
Hangi bilgilerin, silinen istediğiniz iletisinin gövdesindeki durumu. Örneğin:

- Lütfen "Paket adı" my paketinin sürümü x.y.z silin
- Lütfen "Paket adı" my paketin tüm sürümlerini silin
- Lütfen PowerShell Galerisi Hesabımı silin

PowerShell Galerisi Yöneticiler 7 iş günü içinde yanıt gönderir.
Belirtilen paketler istek gönderildikten sonra 30 gün içinde silinecek.
