---
ms.date: 09/05/2018
contributor: JKeithB
keywords: Galeri, powershell, cmdlet, psgallery
title: PowerShell Galerisi hesap ayarları
ms.openlocfilehash: dd7b8b3a99b5b7fbfec5d7f82b81dd6d5cfb906c
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45523392"
---
# <a name="powershell-gallery-account-settings"></a>PowerShell Galerisi hesap ayarları

PowerShell Galerisi hesabınız için bir kimlik bağlı herkese görünür bir addır. Bu kimliği gibi ya da a Microsoft ID, fark `user@hotmail.com` veya `user@outlook.com`, veya bir Azure Active Directory (AAD) hesabı.

PowerShell Galerisi aşağıdaki hesap ayarlarını sağlar:

- PowerShell Galerisi hesabınızla ilişkili e-posta hesabı
- PowerShell Galerisi'nden e-posta bildirimi seçenekleri
- PowerShell Galerisi hesabınızla ilişkili kullanıcı hesabı
- PowerShell Galerisi hesabınızla ilişkili resmi

## <a name="email-address"></a>E-posta adresi

Hedef PowerShell Galerisi bildirimler için e-posta adresidir. Oturum açma hesabı eşleştirilecek yok. Erişiminiz herhangi bir e-posta hesabı kullanabilir. E-posta adresinizi, hiçbir zaman doğrudan diğer kullanıcıların PowerShell Galerisi tarafından sağlanır.

![E-posta adresini değiştirme](../../Images/PSGallery_AcccountEmailAddress.png)

Yeni bir e-posta adresi girin, PowerShell Galerisi bu adresine bir doğrulama e-posta gönderir. Doğrulama e-posta değiştirme işlemini tamamlamak için PowerShell Galerisi yönelik bir bağlantı içerir. Doğrulama işlemi tamamlanana kadar tüm bildirimler önceki adresine gönderilir.

## <a name="email-notifications"></a>E-posta bildirimleri

PowerShell Galerisi, aşağıdaki bildirim seçeneklerini sağlar:

- Kullanıcılar PowerShell Galerisi'nde benimle iletişime geçebilirsiniz
- Bir öğe Hesabımı kullanarak PowerShell Galerisi'nde gönderildiğinde bildirim alın

![E-posta adresini değiştirme](../../Images/PSGallery_AccountEmailOptions.png)

Sayfasında belirtildiği gibi PowerShell Galerisi'ndeki kritik bildirimleri devre dışı bırakılamaz.
Bu görevler şunlardır:

- Güvenlik Uyarıları
- PowerShell Galerisi yöneticilerinden hesabı Yönetim bildirimleri
- Tarafından yapılan gönderiler için PowerShell Galerisi testler hakkında bildirimler çalıştırın

## <a name="change-your-login-account"></a>Oturum açma hesabınızı değiştirmek

Oturum açma hesabı değiştirmek için geçerli hesabıyla oturum açmanız gerekir. Değişikliği tamamlamak için aşağıdaki adımları kullanın.

![Oturum açma hesabı ayarları](../../Images/PSGallery_LoginAccountSettings.png)

1. Tıklayarak **hesabını değiştir**. Bir açılır pencere, oturum açma hesabını değiştirme tüm kullanımları PowerShell galerisinde o hesabın geçerli olduğunu açıklar. Bilgileri gözden geçirin ve ardından tıklayın **Tamam** devam etmek için.

   ![Oturum açma hesabı ayarları](../../Images/PSGallery_LoginAccountChange-1.png)

2. Ardından kullanarak oturum açmanız istenir _yeni hesabı_.

   ![Oturum açma hesabı ayarları](../../Images/PSGallery_LoginAccountChange-2.png)

3. Tıkladığınızda **sonraki**, geçerli hesap kullanarak oturum açmış bir ileti görürsünüz.
   Tıklayın **oturum out ve farklı bir hesapla oturum**.

   ![Oturum açma hesabı ayarları](../../Images/PSGallery_LoginAccountChange-3.png)

4. Yeni hesap parolasını girin. Parolasını girdikten sonra oturum açma hesabı güncelleştirilip güncelleştirilmediğini gösteren hesap ayarları sayfasına dönersiniz.


## <a name="enable-two-factor-authentication-2fa"></a>İki öğeli kimlik doğrulamayı (2FA) etkinleştirme

İki öğeli kimlik doğrulama, PowerShell Galerisi'nde el ile yayımlayın tüm kullanıcılar için önerilir. İki öğeli kimlik doğrulamasını etkinleştirmek için oturum açma hesabı en az iki forms kimlik doğrulaması kayıtlı olması gerekir. Bir parola biridir ve diğer formları olabilir:

- Kısa mesaj alabilen bir telefon numarası
- Cep telefonunuza Microsoft Authenticator gibi bir kayıtlı Doğrulayıcı uygulama

AAD hesap bilgilerinizi ya da Microsoft kimliği hesabı güvenlik ayarlarınızı bu form kimlik doğrulaması yapılandırılmalıdır.

2fa'yı etkinleştirdikten sonra PowerShell Galerisi'nden oturum açışınızda her yapılandırılmış forms kimlik doğrulaması kullanarak kimlik doğrulaması için gereklidir.

> [!IMPORTANT]
> PowerShell Galerisi site için iki öğeli kimlik doğrulamasını etkinleştirmek için tüm kullanımlar, oturum açma hesabınızın 2fa'yı etkinleştirmek gerektirmez. Daha fazla bilgi için [iki basamaklı doğrulama hakkında](https://support.microsoft.com/help/12408/microsoft-account-about-two-step-verification).

## <a name="change-your-profile-picture"></a>Profil resminizi değiştirme

PowerShell Galerisi depolamak ve profilinizle ilişkili resmi görüntülemek için Gravatar kullanır. Profil resminize güncelleştirmek için şurayı ziyaret edin [Gravatar.com](http://www.gravatar.com/).
