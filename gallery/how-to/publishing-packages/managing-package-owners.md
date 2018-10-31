---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeri, powershell, cmdlet, psgallery
title: Paket sahiplerini yönetme
ms.openlocfilehash: 5cf26a7195ac446177cbb7f3a055e8e0a78569cc
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50004217"
---
# <a name="managing-package-owners"></a>Paket sahiplerini yönetme

PowerShell Galerisi paketinde sahipliğini kimin paket galeride yayımlanmış tarafından tanımlanır.
Bazen bu meta veriler sahip meta veriler paket durumdayken değişebilir olması gerekir yani ilk paket yayımlama ötesinde yönetiliyor olması gerekir.

Tüm paket sahipleri eştir.
Bu, paket sahibinden herhangi bir paketin yeni bir sürümü yayımlayabilirsiniz anlamına gelir. Ayrıca, herhangi bir paket sahibinden tüm paket sahibi tarafından kaldırılabilir anlamına gelir.
Diğer sahipleri değerinden daha fazla yetkilisi sahibi yok.

## <a name="setting-a-packages-initial-owner"></a>Bir paketin ilk sahip ayarlama

PowerShell Galerisi'nde yeni paketi yayımlandığında, ilk sahip paket yayımlanan kullanıcı tarafından tanımlanır. Bu, API tarafından Publish-Module cmdlet'inde anahtar kullanılan belirlenir.

## <a name="adding-owners"></a>Sahipleri ekleme

Bir paket için PowerShell Galerisi yayımlandıktan sonra ek kullanıcılar sahipleri bir paketin olmaya davet etmek kolay bir işlemdir.

1. [Oturum](https://powershellgallery.com/users/account/LogOn) bir paketin geçerli sahibi olan hesabının PowerShell Galeriye.
2. 'Items' sekmesini kullanarak, arama veya kullanıcı adınızı tıklatarak bir paket sayfasına gidin ve ardından [ **My paketlerini Yönet**](https://www.powershellgallery.com/account/Packages).
3. Bir paketin sahibi olarak oturum açtığınızda, sol tarafta tıklayın Yönet'sahipleri ' bağlantısı bulunur.
4. Sahip olarak ekleyebilir ve 'Ekle' seçeneğine tıklayın kişinin kullanıcı adı girin.
5. E-posta, daha sonra yeni ikincil sahip için bir paket sahibi olmaya davetiye gönderilir.
6. Kullanıcı bağlantıyı tıklattığında, sahipleri olarak diğer kullanıcıları kaldırma olanağı dahil olmak üzere, bir paketi üzerinde tam denetimle tam bir ortak sahip değildirler.

**Not**: yeni sahip, sahiplik doğrulayana kadar bunlar *yapmamayı* paketinin sahibi listelenir.
Görüntülerken **sahiplerini yönetme** sayfasında, geçerli sahipleri bir "onay" bekleyen giriş görürsünüz.
Bu davet Kaldırılabilir; diğer sahipleri olarak kaldırılabilir.
Bu işlem davet, kullanıcılar diğer kullanıcılar paketlerini sahipleri olarak hatalı bir şekilde eklemesini önler.

"Yazar" meta veri tamamen serbest biçimli metin olduğunu unutmayın; yalnızca "sahip" denetlenir.


## <a name="removing-owners"></a>Sahibi kaldırılıyor

Bir paket birden fazla sahibe sahip ve bir kaldırılması gerektiğinde, basit bir işlemdir:

1. [Oturum](https://powershellgallery.com/users/account/LogOn) paketinin; geçerli sahibi olan hesapla PowerShell Galerisi
2. Paketleri sekmesini kullanarak, arama veya kullanıcı adınızı tıklatarak bir paket sayfasına gidin ve ardından [ **My paketlerini Yönet**](https://www.powershellgallery.com/account/Packages).
3. Bir paketin sahibi olarak oturum açıldığında, sol tarafta tıklayın Yönet'sahipleri ' bağlantısı bulunur;
4. Kaldırılacak sahibi yanındaki 'remove' bağlantısına tıklayın.



## <a name="transferring-package-ownership"></a>Paket sahipliğini devretme

Bazen bir kullanıcı başka bir paket sahipliğini devretmek için destek isteklerini aldığımız ancak neredeyse her zaman bu işlemi kendiniz gerçekleştirebilirsiniz.
Bir kullanıcıdan sahipliğini aktarma Yukarıdaki iki özelliği yalnızca bir birleşiminden oluşur.

1. Geçerli sahip bir ortak sahip olmak için yeni kullanıcı davet eder ve yeni kullanıcı daveti kabul eder;
2. Yeni kullanıcı eski kullanıcı sahipleri listesinden kaldırır.

Bu istek birkaç formlar geldi ancak işlemi çalışır.

- Paket sahipliğini başka bir geliştiriciden değişiyor
- Paket, yanlışlıkla yanlış hesap kullanmanın yayımlandı


## <a name="orphaned-packages"></a>Yalnız bırakılmış paketleri

Son senaryolardan biri, değil birçok kez oluştu.
Paketler artık hale gelmiştir ve yalnızca paket sahip hesabı yeni sahip eklemek için kullanılamaz.
Bu senaryonun bazı örnekleri şunlardır:

- Sahibin hesabını artık mevcut bir e-posta adresiyle ilişkili ve kullanıcı parolasını unutmuş
- Kayıtlı sahip bir paket oluşturur ve paket sahipliği güncelleştirmek için ulaşılamıyor şirketten
- Yalnızca birkaç paketleri etkiledi bir hata nedeniyle, paket şekilde galeride ownerless

PowerShell Galerisi Yöneticiler, herhangi bir paket 'Sahipleri Yönet' bağlantısını erişebilir.
Bir paket gerçek sahibi ve sahiplik izin almak için geçerli sahibi erişilemiyor, 'uygunsuz bağlantıyı PowerShell Galerisi Yöneticiler ulaşmak için galeride kullanın.
Biz, ardından, paket sahipliğini doğrulamak için bir sürecini takip eder.
Paketinin sahibi olmanız karar verirseniz, biz paket için kendimize 'Sahipleri Yönet' bağlantısını kullanın ve sahibi olmaya davetiye gönderin.
Yalnızca bu sahibi olmanız ve bu işlem tarafından durumlarda değişir doğruladıktan sonra yapacağız.
Çoğu zaman, proje sahibiyle iletişim kurmak için bir yolunu bulmak için paketin proje URL'si kullanacağız, ancak proje sahibi ile iletişim kurulmasından Twitter, e-posta ya da başka araçlar da kullanabiliriz.
