---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: Galeri, powershell, cmdlet, psgallery
title: "Öğesi sahiplerini yönetme"
ms.openlocfilehash: fcd538148f9ff1ac96324b567d54d643f1756c93
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="managing-item-owners"></a>Öğesi sahiplerini yönetme

PowerShell galerisinde bir öğe sahipliğini kimin öğesi Galerisi'ne yayımlanan tarafından tanımlanır.
Bazen bu meta veriler sahibi meta veri öğesi olmamasına karşın değişebilir olması gereken anlamına gelir başlangıç öğesi yayımlama ötesinde yönetilmesi gerekir.

Tüm öğesi sahiplerinin eştir. Başka bir deyişle, tüm öğesi sahibi öğeyi yeni bir sürümü yayımlayabilirsiniz. Ayrıca, tüm öğesi sahibi diğer öğesi sahibi kaldırabilirsiniz anlamına gelir. Sahibi diğer sahipleri'den daha fazla yetkilisi yoktur.  

## <a name="setting-an-items-initial-owner"></a>Bir öğenin ilk sahibi ayarlama 

Yeni bir öğe için PowerShell Galerisi yayımlandığında, ilk sahibi öğesi yayımlanan kullanıcı tarafından tanımlanır. Bu, API tarafından Yayımla-Module cmdlet'te anahtar kullanılan belirlenir.

## <a name="adding-owners"></a>Sahipleri ekleme

Bir öğe için PowerShell Galerisi yayımlandıktan sonra öğeyi sahipleri olmaya ek kullanıcıları davet kolaydır.

1. [Oturum](https://powershellgallery.com/users/account/LogOn) bir öğenin geçerli sahibi olan hesapla PowerShell Galerisi.
2. 'Öğeler' sekmesini kullanarak, arama veya kullanıcı adınızı tıklatarak bir öğe sayfasına gidin ve ardından [ **Yönet My öğeleri**](https://www.powershellgallery.com/account/Packages).
3. Bir öğenin sahibi olarak oturum açtığında tıklatın sol taraftaki 'Sahiplerini Yönetme' bağlantısı yoktur.
4. Kullanıcı bir sahibi olarak ekleyin ve 'Ekle'yi tıklatın kişinin adını girin.
5. Bir e-posta, bir öğenin bir sahibi olmak için bir davet yeni ikincil sahip seçeneğine sonra gönderilir.
6. Kullanıcı bağlantıyı tıklattığında, bunlar bir tam ortak sahibi diğer kullanıcıların sahipleri kaldırma özelliği de dahil olmak üzere bir öğe üzerinde tam denetime sahip olursunuz.

**Not**: yeni sahibi sahipliği onaylayıncaya kadar bunlar *almayacak* öğeyi sahibi olarak listelenir.
Görüntülerken **sahiplerini yönetme** sayfasında, geçerli sahipleri bir "onay" bekleyen giriş görürsünüz.
Bu davet Kaldırılabilir; yalnızca diğer sahipleri olarak kaldırılabilir.
Davet bu işlem, kullanıcıların diğer kullanıcıların kendi öğeleri sahipleri olarak yanlışlıkla eklemesini engeller.

"Yazar" meta veri tamamen serbest biçimli metin olduğunu unutmayın; yalnızca "sahipleri" denetlenir.


## <a name="removing-owners"></a>Sahipleri kaldırma
Birden çok sahipleri bir öğe içeriyor ve bir kaldırılacak gerektiğinde basit bir işlemdir:

1. [Oturum](https://powershellgallery.com/users/account/LogOn) bir öğenin; geçerli sahibi olan hesapla PowerShell Galerisi
2. Öğeler sekmesini kullanarak, arama veya kullanıcı adınızı tıklatarak bir öğe sayfasına gidin ve ardından [ **Yönet My öğeleri**](https://www.powershellgallery.com/account/Packages).
3. Bir öğenin sahibi olarak oturum açmış olduğunda 'Sahiplerini Yönetme' bağlantısını tıklatın sol taraftaki;
4. Kaldırılacak sahibi yanındaki 'Kaldır' bağlantısını tıklatın.



## <a name="transferring-item-ownership"></a>Öğe sahipliğini aktarma
Biz bazen öğesi sahipliği bir kullanıcıdan başka bir bilgisayara aktarmak için destek isteklerini alır ancak bunu kendiniz neredeyse her zaman gerçekleştirebilirsiniz.
Bir kullanıcıdan sahipliğini aktarma Yukarıdaki iki özelliği yalnızca bir birleşiminden oluşur.

1. İkincil sahip olmak için yeni kullanıcı geçerli sahibi başvurulmasını ve yeni kullanıcı daveti kabul eder;
2. Yeni kullanıcı eski kullanıcı sahipler listesinden kaldırır.

Bu istek altında birkaç forms geldi, ancak işlem aynı şekilde çalışır.

* Öğe sahipliği bir geliştiriciden diğerine değiştiriyor.
* Öğe, yanlışlıkla yanlış hesap kullanılarak yayımlandı


## <a name="orphaned-items"></a>Yalnız bırakılmış öğeleri
Bir son senaryo, değil birçok kez oluştu.
Öğeleri artık duruma gelmiş ve yalnızca öğesi sahip hesabı yeni sahipleri eklemek için kullanılamaz.
Bu senaryonun bazı örnekleri şunlardır:

* Sahibin hesabını artık mevcut bir e-posta adresiyle ilişkili ve kullanıcı parolalarını unutan
* Kayıtlı sahip öğeyi üreten ve madde sahipliği güncelleştirmek için ulaşılamıyor şirket ayrıldı
* Yalnızca öğeleri sayıda etkilediğini bir hata nedeniyle, şekilde galeride ownerless öğedir

PowerShell Galerisi Yöneticiler herhangi bir öğeyi 'Sahiplerini Yönetme' bağlantısını erişebilir.
Öğesinin gerçek sahibiyseniz ve sahipliği izinleri kazanmak için geçerli sahibi ulaşamıyor, 'Rapor kötüye' bağlantısını PowerShell Galerisi Yöneticiler ulaşması galeride kullanın.
Biz, ardından öğenin, sahipliği doğrulamak için bir sürecini takip eder.
Öğenin bir sahibi olması gereken karar verirseniz, biz 'Sahiplerini Yönetme' bağlantıyı öğe için kendisini kullanın ve sahibi olmak için davet gönderin.
Biz yalnızca bu bir sahip olması gerekir ve bu işlem tarafından durumlar değişir doğruladıktan sonra yapın.
Çoğu zaman, biz öğesi'nin proje URL'sini bir proje sahibine başvurun şekilde bulmak için kullanır, ancak proje sahibi ile iletişim için Twitter, e-posta ya da başka araçlar da kullanabiliriz.

