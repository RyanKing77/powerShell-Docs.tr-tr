---
ms.date: 03/27/2018
contributor: JKeithB
keywords: Galeri, powershell, psgallery, GDPR
title: PowerShell Galerisi GDPR uyumluluğu
ms.openlocfilehash: 14b82fa07df52f02f0d7577cb0eef70faa4285a2
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893255"
---
# <a name="powershell-gallery-gdpr-compliance"></a>PowerShell Galerisi GDPR uyumluluğu

## <a name="overview"></a>Genel bakış

Mayıs 2018'de genel veri koruma yönetmeliği (GDPR), bir Avrupa gizlilik yasaları etkinleşir.
GDPR, yeni şirketler, devlet kurumları, gütmeyen ve teklif mal ve hizmet kişilere Avrupa Birliği (AB) veya AB vatandaşlar için bağlı verileri toplayıp analiz, diğer kuruluşların kuralları uygular.
Burada, nerede olursanız olun GDPR geçerlidir.

> [!NOTE]
> Bu makalede, PowerShell Galerisi'nden kişisel verilerini silme adımlar sağlar ve sizin yükümlülükleriniz GDPR altında desteklemek için kullanılabilir. GDPR hakkında genel bilgiler arıyorsanız bkz [hizmet güveni portalı GDPR bölümünü](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).

## <a name="personally-identifiable-data"></a>Kişisel olarak tanımlanabilen veriler

PowerShell Galerisi, kişisel bilgileri içerebilen kullanıcılar tarafından sağlanan aşağıdaki bilgileri depolar:

- PowerShell Galerisi hesabı
- PowerShell Galerisi'nde yayımlanmış öğeler
- PowerShell Galerisi ekibi ile e-posta yazışmaları

Çoğu kullanıcı, bir PowerShell Galerisi hesabı oluşturmayın.
Bir öğe yayımlayın veya PowerShell galerisinde "Kişi sahip" Bu özelliği kullanmak için çalıştırmayacağınız sürece bir hesap gerekli değildir.
Kullanıcı tarafından başlatılan e-posta yazışmaları dışında PowerShell Galerisi bir hesabı oluşturmadığınızı kullanıcılar kişisel verilerini depolamaz.

PowerShell Galerisi hesabı oluşturan kullanıcılar öğeleri PowerShell Galerisi'nde yayımlayabilirsiniz.
Bu öğeleri PowerShell kodu olması bekleniyor, ancak kişisel bilgiler dahil olmak üzere diğer bilgileri içerebilir.
Tüm öğeleri nasıl alabileceğiniz aşağıdaki bilgileri gösterir PowerShell Galerisi'nden yayımlamış olursunuz.

## <a name="dsr-export-of-powershell-gallery-data"></a>PowerShell Galerisi verileri DSR dışarı aktarma

Aşağıdaki bölümlerde PowerShell Galerisi'nde bilgi dışarı aktarma ve silme, bu bilgilerin nasıl açıklayarak PowerShell Galerisi gdpr veri sahibi istekleri (DSR) nasıl desteklediği açıklanmaktadır.

### <a name="email"></a>E-posta

E-posta yazışmaları aşağıdakilerden herhangi birini içerebilir:

- Kod Analizi tarar, öğeler PowerShell Galerisi'nde yayımlanmış herhangi bir öğe ile ilgili bir sorun algıladı PowerShell Galerisi sahiplerine gönderilen e-posta
- Hiç kimse tarafından "Bize başvurun" sayfasında e-posta adresini kullanarak PowerShell Galerisi ekibine gönderilen e-posta [cgadmin@microsoft.com](mailto:cgadmin@microsoft.com)
- PowerShell galerisinde bir öğenin sahibi e-posta göndermek için PowerShell galerisinde "Kişi sahip" özelliğini kullanan kullanıcılar kayıtlı

PowerShell Galerisi veya tarafından gönderilen e-postaları, olası güvenlik araştırmalar kötü amaçlı kod PowerShell galerisinde bulunmasına desteklemek için 90 günlük bir bekletme ilkesi olması.
E-posta İlkesi tarafından 90 gün sonra silinir.

Gelen e-posta adresinizi ve PowerShell Galerisi veya önceki 90 gün içinde gönderilen tüm e-posta kopyalarını isteyebilir.
Bu yazışma istemek için bir e-posta Gönder [ cgadmin@microsoft.com ](mailto:cgadmin@microsoft.com), başlıklı: "Bu hesaba ilişkin e-postalar için DSR istek".
Hangi bilgilerin istiyorsunuz iletisinin gövdesinde, durum (örneğin: Lütfen bu e-posta adresinden alınan veya gönderilen tüm e-posta gönderin.) 7 iş günü içinde e-posta adresinizi isteğin 90 gün içinde ilgili tüm e-postalar gönderilir.

### <a name="powershell-gallery-account-information"></a>PowerShell Galerisi hesap bilgileri

PowerShell Galerisi hesabı oluşturduysanız, PowerShell Galerisi'nde aşağıdaki adımları izleyerek daha fazladır saklanan tüm kişisel bilgileri bulabilirsiniz:

1. PowerShell Galerisi için oturum açın, sonra kullanıcı adınıza tıklayın
2. Sonraki sayfada görüntülenen gösterir PowerShell Galerisi hesabı için kullanılan e-posta adresine hesap sayfası olan

PowerShell galerisinde birden fazla hesabı oluşturduysanız, her hesap için bu adımları yinelemeniz gerekecektir.

### <a name="items-in-the-powershell-gallery"></a>PowerShell galeride bulunan öğeler

Dışarı aktarılan öğeleri PowerShell Galerisi'nde yayımlanmış kolaylaştırmak için "GetPSGalleryItemsForAuthor" betik PowerShell Galerisi'nde yayımladık.
Bu betik, her öğesinde depolanan Yazar bilgileri temel alarak PowerShell Galerisi yerleştirerek her öğe sürümünün bir kopyasını dışarı aktarır.

> [!NOTE]
> Öğenizi yayımladığınızda Yazar öğesi bildiriminde saklanır.
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

Yazar ve kaydedilmesi için öğeleri istediğiniz klasör sisteminize sağlamanız istenir.

## <a name="deleting-personal-data-from-the-powershell-gallery"></a>PowerShell Galerisi'nden kişisel verileri silme

PowerShell Galerisi hesabınız veya PowerShell Galerisi'nde olduğunuz herhangi bir öğeyi silmek için e-posta Gönder cgadmin@microsoft.com başlığıyla: "Bu hesaba ilişkin öğeleri için GDPR isteği".
Hangi bilgilerin, silinen istediğiniz iletisinin gövdesindeki durumu. Örneğin:

- Lütfen "öğe adı" my öğesinin sürümü x.y.z silin
- Lütfen "öğe adı" öğe tüm sürümleri sil
- Lütfen PowerShell Galerisi Hesabımı silin

PowerShell Galerisi Yöneticiler 7 iş günü içinde yanıt gönderir.
Belirtilen öğelerin istek gönderildikten sonra 30 gün içinde silinecek.