---
ms.date: 09/11/2018
contributor: JKeithB
keywords: Galeri, powershell, cmdlet, psgallery
title: PowerShell Galerisi hesabı oluşturma
ms.openlocfilehash: e4cf73edb03267cff6bbcc0cf3b754225e45be9f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685273"
---
# <a name="creating-a-powershell-gallery-account"></a>PowerShell Galerisi hesabı oluşturma

Her şeyi PowerShell Galerisi'nden yayımlamadan önce PowerShell Galerisi hesabı oluşturmanız gerekir.
PowerShell Galerisi hesapları bir e-posta etkin bir oturum açma hesabına bağlanması gerekir. Bu hesap Azure Active Directory hesabını veya bir e-posta hesabından outlook.com veya hotmail.com gibi a Microsoft ID olabilir.

PowerShell Galerisi hesabı oluşturmak için Git [ https://PowerShellGallery.com ](https://PowerShellGallery.com) tıklayın **oturum** aşağıdaki görüntüde gösterildiği gibi.

![Yeni hesabı Kaydet](../../Images/CreateAccount-Register.png)

Bir Azure Active Directory hesabını kullanmayı tercih **iş veya Okul hesabı**ve hesabınızla oturum açın. A Microsoft ID kullanmayı tercih **kişisel hesap** ve oturum açın.

Ardından, PowerShell Galerisi için bir kullanıcı adı oluşturmanız istenir. Kullanım koşulları ve gizlilik ilkesi gözden geçirin, bir kullanıcı adı girin ve ardından **kaydetme**.

> [!NOTE]
> Hesap adı, oluşturulduktan sonra değiştirilemez. Daha fazla bilgi için [paketinin sahiplerini yönetme](managing-package-owners.md).

## <a name="recommended-practices-for-powershell-gallery-accounts"></a>PowerShell Galerisi hesaplar için önerilen uygulamalar

PowerShell Galerisi hesabınızla kullanılan e-posta hesabı etkin bir şekilde izlemek önemlidir. PowerShell Galerisi paketlerin sahibi olan tüm iletişim bu e-posta adresidir. PowerShell Galerisi operasyon ekibinin bir paket sahibi ile iletişim kuramıyor, biz bir paketi silmek için gerekli.

PowerShell Galerisi için sık sık yayımlayın kuruluşların bu amaç için benzersiz bir dış hesap oluşturun. Kuruluşunuzda bir adresine bildirimleri iletecek şekilde e-posta iletme kullanmanızı öneririz.

Birden çok sahipleri bir paket ile ilişkili olduğunda, tüm PowerShell Galerisi bildirimleri tüm sahiplerine gönderilir. Daha fazla bilgi için [paketinin sahiplerini yönetme](managing-package-owners.md).
