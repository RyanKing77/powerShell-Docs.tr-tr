---
ms.date: 03/27/2018
contributor: JKeithB
keywords: Galeri, powershell, psgallery, GDPR
title: PowerShell Galerisi GDPR uyumluluk
ms.openlocfilehash: dca1a82952c284980a84caafa13b2807e47e25a0
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189763"
---
# <a name="powershell-gallery-gdpr-compliance"></a>PowerShell Galerisi GDPR uyumluluk

## <a name="overview"></a>Genel bakış

Mayıs 2018 genel veri koruma düzenleme (GDPR), bir Avrupa gizlilik yasalarına etkinleşir.
GDPR şirketler, devlet dairesi, kar kaybı olmayan ve diğer kuruluşlardan teklif mal ve hizmet Avrupa Birliği (AB) ya da, kişilere toplamak ve analiz etmek için AB Satışlar bağlı veri yeni kuralları uygular.
Bulunduğunuz olsun GDPR geçerlidir.

> [!NOTE]
> Bu makalede PowerShell Galerisi'nden kişisel verilerini silmek adımlar sağlar ve sizin yükümlülüklerin GDPR altında desteklemek için kullanılabilir. GDPR hakkında genel bilgi arıyorsanız bkz [Hizmeti'ne güvenen portal GDPR bölümünü](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).

## <a name="personally-identifiable-data"></a>Kişisel olarak tanımlanabilecek veriler

PowerShell Galerisi kişisel bilgiler içerebilir kullanıcılar tarafından sağlanan aşağıdaki bilgileri depolar:

* PowerShell Galerisi hesabı
* PowerShell Galerisi yayımlanan öğeler
* E-posta yazışmaları PowerShell Galerisi ekibi ile

Kullanıcıların çoğunun bir PowerShell Galerisi hesabı oluşturmayın.
Bir öğe yayımlamak veya PowerShell galerisinde "Kişi sahip" Bu özelliği kullanmak için çalıştırmayacağınız sürece bir hesap gerekli değildir.
Kullanıcı tarafından başlatılan e-posta yazışmaları dışında bir hesap oluşturmadınız kullanıcıların kişisel olarak tanımlanabilecek veriler PowerShell Galerisi depolamaz.

Bir PowerShell Galerisi hesabı oluşturma kullanıcılar öğeleri PowerShell Galerisi yayımlayabilirsiniz.
Bu öğeler PowerShell kodu olması beklenir, ancak kişisel bilgiler dahil olmak üzere diğer bilgiler içerebilir.
Aşağıdaki bilgiler tüm öğelerin nasıl erişebileceğini gösterecektir PowerShell Galerisine yayımlandı.

## <a name="dsr-export-of-powershell-gallery-data"></a>PowerShell Galerisi verilerin DSR aktarma

Aşağıdaki bölümlerde PowerShell Galerisi veri konu isteklerinin (DSR) nasıl destekler? PowerShell galerisinde depolanan bilgileri dışarı aktarma ve bu bilgilerin silme isteği nasıl açıklayarak açıklanmaktadır.

### <a name="email"></a>E-posta

E-posta yazışmaları aşağıdakilerden herhangi birini içerebilir:

* PowerShell Galerisi Kod Analizi tarar, öğeleri PowerShell Galerisi yayımladığınız herhangi bir öğe ile ilgili bir sorun tespit sahiplerine gönderilen e-posta
* "Bize başvurun" sayfasında e-posta adresini kullanarak PowerShell Galerisi takımı herkes tarafından gönderilen e-posta (cgadmin@microsoft.com)
* PowerShell Galerisi bir öğede sahibi e-posta göndermek için PowerShell galerisinde "Kişi sahip" özelliğini kullanan kullanıcılar kayıtlı

PowerShell Galerisi veya tarafından gönderilen e-postaların kötü amaçlı kod PowerShell Galerisi bulunmasına olası güvenlik araştırmalar desteklemek için 90 günlük bir bekletme ilkesi olması.
E-posta İlkesi tarafından 90 gün sonra silinir.

E-posta adresinizi ve PowerShell Galerisi bilgisayardan veya önceki 90 gün içinde gönderilen tüm e-postaları kopyalarını isteyebilir.
Bu ilişkiyi istemek için bir e-posta Gönder cgadmin@microsoft.com, başlıkla: "Bu hesaba ilişkin e-posta talebi DSR".
İleti gövdesinde isteyen hangi bilgilerin belirtin (örneğin: Lütfen bu e-posta adresinden alınan veya gönderilen tüm e-postalar gönderin.) İsteğin 90 gün içinde e-posta adresinizi içeren tüm e-postalar 7 iş günü içinde gönderilir.

### <a name="powershell-gallery-account-information"></a>PowerShell Galerisi hesap bilgileri

Bir PowerShell Galerisi hesabı oluşturduysanız, PowerShell galerisinde aşağıdaki adımları uygulayarak zamandır saklanan tüm kişisel bilgileri bulabilirsiniz:

1. PowerShell Galerisi oturum açın, sonra kullanıcı adınıza tıklayın
2. Görüntülenen sonraki sayfa PowerShell Galerisi hesabı için kullanılan e-posta adresi gösterir hesap sayfa.

PowerShell galerisinde birden fazla hesabı oluşturduysanız, her hesap için bu adımları yinelemeniz gerekecektir.

### <a name="items-in-the-powershell-gallery"></a>PowerShell galerisinde öğeleri

PowerShell Galerisi yayımlanan verme öğeleri kolaylaştırmak için biz "GetPSGalleryItemsForAuthor" komut dosyası için PowerShell Galerisi yayımladınız.
Bu komut dosyası her bir sürümüyle öğesinde depolanan Yazar bilgilere dayanarak PowerShell Galerisi yerleştirin her öğenin bir kopyasını dışa aktarır.

> [!NOTE]
> Öğenizi yayımladığınızda Yazar öğesi bildiriminde depolanır.
> Yazarın PowerShell galerisinde kullandığınız hesabı ile aynı kimlik olduğunu garantisi yoktur.
> Başka bir değer yazar alanı kullanıyorsanız, bu komut dosyası kullanırken bu değer sağlamanız gerekir.

Aşağıdaki PowerShell komutunu kullanarak betiği yükleyebilirsiniz:

```powershell
Save-Script GetPSGalleryItemsForAuthor -path <local folder location> -repository psgallery
```

Aşağıdaki PowerShell komutlarını çalıştırarak komut dosyasını doğrudan, ardından çalıştırabilirsiniz:

```powershell
cd <local folder location >
.\GetPSGalleryItemsForAuthor.ps1
```

Yazar ve kaydedilmesi için öğelerini bir klasörü sisteminizdeki sağlamanız istenir.

## <a name="deleting-personal-data-from-the-powershell-gallery"></a>PowerShell Galerisi'nden kişisel verileri silme

PowerShell Galerisi hesabınız veya PowerShell galerisinde sahip herhangi bir öğeyi silmek için e-posta Gönder cgadmin@microsoft.com başlıkla: "GDPR isteği bu hesaba ilişkin öğeleri için".
İleti gövdesinde hangi bilgilerin silinen istediğiniz durumu. Örneğin:

* Lütfen "öğe adı" Benim öğesinin sürüm x.y.z silin
* Lütfen "öğe adı" öğe tüm sürümlerini silin
* Lütfen PowerShell Galerisi Hesabımı silin

PowerShell Galerisi Yöneticiler 7 iş günü içinde yanıt gönderir.
İstek gönderildikten sonra 30 gün içinde belirtilen öğeler silinecek.
