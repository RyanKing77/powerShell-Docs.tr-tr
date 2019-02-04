---
ms.date: 09/10/2018
contributor: JKeithB
keywords: Galeri, powershell, cmdlet, psgallery
title: API anahtarları yönetme
ms.openlocfilehash: 954eb27c25babdb8efe50c13caf5f2d287c6b3e3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687723"
---
# <a name="managing-api-keys"></a>API anahtarları yönetme

PowerShell Galerisi gereksinimleri yayımlama aralığı desteklemek için birden çok API anahtarı oluşturma destekler. Bir API anahtarı için bir veya daha fazla paket uygulayabilirsiniz, belirli ayrıcalıklar verir ve bir sona erme tarihi vardır.

> [!IMPORTANT]
> Kapsamı belirlenmiş bir API anahtarı giriş önce PowerShell Galerisi yayımlanan kullanıcılar, "tam erişim API anahtarı" gerekir. Tam erişim anahtarlarını kapsamlı API anahtarlarına yerleşik güvenlik geliştirmeleri yok. Tam erişim anahtarları asla süresi dolar ve kullanıcı tarafından sahip olunan her şeye uygulayın. Bu anahtarı silmek, yeniden kullanılamaz.

Aşağıdaki görüntüde, kapsamlı bir API anahtarı oluştururken kullanılabilen seçenekler gösterilmektedir.

![API anahtarları oluşturma](../../Images/PSGallery_KeyScoped.png)

Bu örnekte, oluşturduğumuz adlı bir API anahtarı **AzureRMDataFactory**. Bu anahtar değeri 'AzureRM.DataFactory' ile başlayan ve 365 gün boyunca geçerlidir adlarla paketleri göndermek için kullanılabilir. Aynı kuruluştaki farklı ekipler farklı paketleri çalışırken tipik bir senaryodur. Takım üyeleri, üzerinde çalıştıkları belirli bir paket için ayrıcalıkları verir bir anahtara sahip.
Süre sonu değeri eski veya unutulan anahtarları kullanımını engeller.

## <a name="using-glob-patterns"></a>Glob desenleri kullanma

Birden çok paket üzerinde çalışıyorsanız, birden çok paket grubu olarak eşleşecek şekilde Glob desenlerinin kullanabilirsiniz. API anahtarı izinleri glob deseni ile eşleşen tüm yeni paketleri için geçerlidir. Örneğin, önceki örnekte bir **Glob deseni** 'AzureRM.DataFactory*' değeri. 'Paket glob deseni eşleştiğinden bu anahtarı kullanarak AzureRm.DataFactoryV2.Netcore' adlı bir paket gönderebilirsiniz.

## <a name="create-api-keys-securely"></a>API anahtarları güvenli bir şekilde oluşturun

Güvenlik için yeni oluşturulan bir anahtar değeri ekranda asla gösterilir ve yalnızca aşağıda gösterilen şekilde Kopyala düğmesini ile kullanılabilir.

![Yeni API anahtarı değerini alma](../../Images/PSGallery_CopyCreatedKey.png)

> [!IMPORTANT]
> API anahtarı değerini yalnızca, hemen oluşturma veya yenilediğinizden sonra da kopyalayabilirsiniz. Görüntülenmeyecek ve sayfa yenilendikten sonra yeniden erişilemez. Anahtar değeri kaybederseniz yeniden kullanın ve yeniden oluşturuldu sonra anahtarı kopyalayın.

## <a name="key-permissions-and-expiration"></a>Anahtar izinleri ve sona erme tarihi

Kapsamlı API anahtarları, aşağıdaki izinlerden birini atayabilirsiniz:

- Yeni paketleri gönder
- Güncelleştirme paketleri veya New bildirme
- Paket listeden Kaldır

Her yeni anahtarı bir zaman aşımı vardır. Süre sonu değeri, gün içinde ölçülür. Süre sonu için olası değerler şunlardır:

- 1 gün
- 90 gün
- 180 gün
- 270 günde bir
- 365 gün (varsayılan)

Anahtar oluşturulduktan sonra bu ayarlar değiştirilemez. Her zaman geçerli olsun yeni bir anahtar oluşturulamıyor.

## <a name="editing-and-deleting-existing-api-keys"></a>Düzenleme ve mevcut API anahtarları silme

Varolan bir anahtarın bazı ayarları değiştirebilirsiniz. Daha önce belirtildiği gibi mevcut bir API anahtarı için güvenlik kapsamı değiştiremez veya sona erme değiştirin. Takımdaki herhangi biri seçeneği, aşağıdaki ekran görüntüsünde gösterilir:

![Yeni API anahtarı değerini alma](../../Images/PSGallery_EditAPIKey.png)

Bir anahtar tarafından denetlenen paketlerini değiştirmek için tek paketler listesinden seçim yapabilir veya glob deseni değiştirmek.

Tıklayarak **yeniden** yeni bir anahtar değeri oluşturur. Yalnızca anahtar ilk oluşturulduğunda gerekir gibi **kopyalama** güncelleştirmeden hemen sonra anahtar değeri. **Kopyalama** seçeneği kullanılamaz bu sayfadan çıktıktan sonra.

Tıklayarak **Sil** bir onay iletisi görüntüler. Bir anahtar silindikten sonra kullanılamaz.

## <a name="key-expiration"></a>Anahtarı süre sonu

On gün süresi dolmadan önce PowerShell Galerisi API anahtarını hesap sahibi uyarı e-posta gönderir. Süre dolduktan sonra anahtarı kullanılamıyor. Hangi anahtar artık geçerli olmayan gösteren API Anahtar Yönetimi sayfasının en üstündeki bir uyarı iletisi görüntülenir. Yeni bir anahtar değeri oluşturur.
