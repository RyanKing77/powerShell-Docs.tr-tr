---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: Galeri, powershell, cmdlet, psgallery
title: "Bir PowerShell Galerisi hesabı oluşturma"
ms.openlocfilehash: 5af38884d819cb9c600a061109233614bd33666f
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2018
---
## <a name="creating-a-powershell-gallery-account"></a>Bir PowerShell Galerisi hesabı oluşturma

Bir PowerShell Galerisi hesabı herhangi bir şey için PowerShell Galerisi yayımlamadan önce oluşturulmalıdır. PowerShell Galerisi hesapları e-posta etkin bir Azure Active Directory hesabı veya bir Microsoft e-posta hesabıyla (bir etki alanı outlook.com, hotmail.com, vs.) ile bağlantılı olması gerekir

Bir PowerShell Galerisi hesabı oluşturmak için şu adrese gidin https://PowerShellGallery.com ve "Kayıt"'i tıklatın (aşağıdaki görüntü bakın). 

![Yeni hesabı Kaydettir](./images/CreatingAccount-Register.png)

Sonraki sayfada bir Azure Active Directory hesabı kullanmak için "İş veya Okul hesabı" seçin ve hesabınızla oturum açın. -Hotmail.com veya Outlook.com domain - birinde gibi bir Microsoft hesabı kullanmak için "Kişisel hesap" seçin ve oturum açın. 

Oturum açtıktan sonra PowerShell Galerisi için bir kullanıcı adı oluşturmak için istenir. Bağlı kullanım koşulları ve gizlilik ilkesini inceleyin, bir kullanıcı adı girin ve Kaydet'i tıklatın.

Not: Bu hesap adı oluşturulduktan sonra değiştirilemez.  
Bkz: [yönetme öğesi sahiplerinin](https://msdn.microsoft.com/powershell/gallery/psgallery/managing-item-owners) bu konuyla ilgili ek ayrıntılar için.

## <a name="recommended-practices-for-powershell-gallery-accounts"></a>PowerShell Galerisi hesaplar için önerilen uygulamalar

PowerShell Galerisi hesabınızla kullanılan e-posta hesabı etkin bir şekilde izlenmesi önemlidir.
PowerShell Galerisi hesabınızla ilişkili adresini kullanarak e-posta aracılığıyla tüm communiction PowerShell galeri öğeleri sahipleri sahip olur.
Bir öğe sahibine başvurun bağlanamıyoruz, işletim ekibi bazı koşullarda bir öğeyi silmek için gerekebilir.

PowerShell galerisinde genellikle yayımlamak kuruluşlar, Outlook.com veya başka bir Microsoft hesabı etki alanında bu amaç için benzersiz bir hesabı oluşturur.
Çoğu durumda bu hesabı düzenli olarak izlenmiyor. En iyi uygulama bu durumda Outlook iletme genellikle bir sahibi öğesi görüntülemenize tarafından izlenecek kuruluş içinde başka bir hesap için e-posta göndermek için kullanmaktır.

Bir öğesiyle ilişkili birden çok sahipleri varsa, PowerShell Galerisi'nden gelen tüm iletişimlerin tüm sahiplerine gidin.
Bkz: [yönetme öğesi sahiplerinin](https://msdn.microsoft.com/powershell/gallery/psgallery/managing-item-owners) sahipleri için bir öğe ekleme hakkında ek bilgi. 

