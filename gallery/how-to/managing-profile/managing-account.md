---
ms.date: 09/05/2018
contributor: JKeithB
keywords: Galeri, powershell, cmdlet, psgallery
title: PowerShell Galerisi Hesap Ayarları
ms.openlocfilehash: ebe784ec5aae5ff3a4d444d12a168ef38aaef65f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084529"
---
# <a name="powershell-gallery-account-settings"></a><span data-ttu-id="03964-103">PowerShell Galerisi Hesap Ayarları</span><span class="sxs-lookup"><span data-stu-id="03964-103">PowerShell Gallery Account Settings</span></span>

<span data-ttu-id="03964-104">PowerShell Galerisi hesabınız için bir kimlik bağlı herkese görünür bir addır.</span><span class="sxs-lookup"><span data-stu-id="03964-104">Your PowerShell Gallery account is a publicly visible name that is linked to an identity.</span></span> <span data-ttu-id="03964-105">Bu kimliği gibi ya da a Microsoft ID, fark `user@hotmail.com` veya `user@outlook.com`, veya bir Azure Active Directory (AAD) hesabı.</span><span class="sxs-lookup"><span data-stu-id="03964-105">That identity is either a Microsoft ID, like `user@hotmail.com` or `user@outlook.com`, or an Azure Active Directory (AAD) account.</span></span>

<span data-ttu-id="03964-106">PowerShell Galerisi aşağıdaki hesap ayarlarını sağlar:</span><span class="sxs-lookup"><span data-stu-id="03964-106">The PowerShell Gallery provides the following account settings:</span></span>

- <span data-ttu-id="03964-107">PowerShell Galerisi hesabınızla ilişkili e-posta hesabı</span><span class="sxs-lookup"><span data-stu-id="03964-107">The email account associated with your PowerShell Gallery account</span></span>
- <span data-ttu-id="03964-108">PowerShell Galerisi'nden e-posta bildirimi seçenekleri</span><span class="sxs-lookup"><span data-stu-id="03964-108">Options for email notifications sent from the PowerShell Gallery</span></span>
- <span data-ttu-id="03964-109">PowerShell Galerisi hesabınızla ilişkili kullanıcı hesabı</span><span class="sxs-lookup"><span data-stu-id="03964-109">The user account associated with your PowerShell Gallery account</span></span>
- <span data-ttu-id="03964-110">PowerShell Galerisi hesabınızla ilişkili resmi</span><span class="sxs-lookup"><span data-stu-id="03964-110">The picture associated with your PowerShell Gallery account</span></span>

## <a name="email-address"></a><span data-ttu-id="03964-111">E-posta adresi</span><span class="sxs-lookup"><span data-stu-id="03964-111">Email address</span></span>

<span data-ttu-id="03964-112">Hedef PowerShell Galerisi bildirimler için e-posta adresidir.</span><span class="sxs-lookup"><span data-stu-id="03964-112">The email address is the destination for PowerShell Gallery notifications.</span></span> <span data-ttu-id="03964-113">Oturum açma hesabı eşleştirilecek yok.</span><span class="sxs-lookup"><span data-stu-id="03964-113">It does not have to match the login account.</span></span> <span data-ttu-id="03964-114">Erişiminiz herhangi bir e-posta hesabı kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="03964-114">You may use any email account you have access to.</span></span> <span data-ttu-id="03964-115">E-posta adresinizi, hiçbir zaman doğrudan diğer kullanıcıların PowerShell Galerisi tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="03964-115">Your email address is never directly provided by the PowerShell Gallery to other users.</span></span>

![E-posta adresini değiştirme](../../Images/PSGallery_AcccountEmailAddress.png)

<span data-ttu-id="03964-117">Yeni bir e-posta adresi girin, PowerShell Galerisi bu adresine bir doğrulama e-posta gönderir.</span><span class="sxs-lookup"><span data-stu-id="03964-117">When you enter a new email address, the PowerShell Gallery sends a verification mail to that address.</span></span> <span data-ttu-id="03964-118">Doğrulama e-posta değiştirme işlemini tamamlamak için PowerShell Galerisi yönelik bir bağlantı içerir.</span><span class="sxs-lookup"><span data-stu-id="03964-118">The verification mail contains a link back to the PowerShell Gallery to complete the change process.</span></span> <span data-ttu-id="03964-119">Doğrulama işlemi tamamlanana kadar tüm bildirimler önceki adresine gönderilir.</span><span class="sxs-lookup"><span data-stu-id="03964-119">Until you complete the verification process, all notifications are sent to the previous address.</span></span>

## <a name="email-notifications"></a><span data-ttu-id="03964-120">E-posta bildirimleri</span><span class="sxs-lookup"><span data-stu-id="03964-120">Email notifications</span></span>

<span data-ttu-id="03964-121">PowerShell Galerisi, aşağıdaki bildirim seçeneklerini sağlar:</span><span class="sxs-lookup"><span data-stu-id="03964-121">PowerShell Gallery provides the following notification options:</span></span>

- <span data-ttu-id="03964-122">Kullanıcılar PowerShell Galerisi'nde benimle iletişime geçebilirsiniz</span><span class="sxs-lookup"><span data-stu-id="03964-122">Users can contact me through the PowerShell Gallery</span></span>
- <span data-ttu-id="03964-123">Bir paket Hesabımı kullanarak PowerShell Galerisi'nde gönderildiğinde bildirim alın</span><span class="sxs-lookup"><span data-stu-id="03964-123">Notify me when an package is pushed to the PowerShell Gallery using my account</span></span>

![E-posta adresini değiştirme](../../Images/PSGallery_AccountEmailOptions.png)

<span data-ttu-id="03964-125">Sayfasında belirtildiği gibi PowerShell Galerisi'ndeki kritik bildirimleri devre dışı bırakılamaz.</span><span class="sxs-lookup"><span data-stu-id="03964-125">As noted on the page, critical notifications from the PowerShell Gallery can't be disabled.</span></span>
<span data-ttu-id="03964-126">Bu görevler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="03964-126">These include:</span></span>

- <span data-ttu-id="03964-127">Güvenlik Uyarıları</span><span class="sxs-lookup"><span data-stu-id="03964-127">Security notifications</span></span>
- <span data-ttu-id="03964-128">PowerShell Galerisi yöneticilerinden hesabı Yönetim bildirimleri</span><span class="sxs-lookup"><span data-stu-id="03964-128">Account management notifications from PowerShell Gallery administrators</span></span>
- <span data-ttu-id="03964-129">Tarafından yapılan gönderiler için PowerShell Galerisi testler hakkında bildirimler çalıştırın</span><span class="sxs-lookup"><span data-stu-id="03964-129">Notifications about the tests run by the PowerShell Gallery for submissions you have made</span></span>

## <a name="change-your-login-account"></a><span data-ttu-id="03964-130">Oturum açma hesabınızı değiştirmek</span><span class="sxs-lookup"><span data-stu-id="03964-130">Change your login account</span></span>

<span data-ttu-id="03964-131">Oturum açma hesabı değiştirmek için geçerli hesabıyla oturum açmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="03964-131">To change the login account, you must be signed in with the current account.</span></span> <span data-ttu-id="03964-132">Değişikliği tamamlamak için aşağıdaki adımları kullanın.</span><span class="sxs-lookup"><span data-stu-id="03964-132">Use the following steps to complete the change.</span></span>

![Oturum açma hesabı ayarları](../../Images/PSGallery_LoginAccountSettings.png)

1. <span data-ttu-id="03964-134">Tıklayarak **hesabını değiştir**.</span><span class="sxs-lookup"><span data-stu-id="03964-134">Click on **Change Account**.</span></span> <span data-ttu-id="03964-135">Bir açılır pencere, oturum açma hesabını değiştirme tüm kullanımları PowerShell galerisinde o hesabın geçerli olduğunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="03964-135">A pop-up window explains that changing the login account applies to all uses of that account in the PowerShell Gallery.</span></span> <span data-ttu-id="03964-136">Bilgileri gözden geçirin ve ardından tıklayın **Tamam** devam etmek için.</span><span class="sxs-lookup"><span data-stu-id="03964-136">Review the information, then click **OK** to continue.</span></span>

   ![Oturum açma hesabı ayarları](../../Images/PSGallery_LoginAccountChange-1.png)

2. <span data-ttu-id="03964-138">Ardından kullanarak oturum açmanız istenir _yeni hesabı_.</span><span class="sxs-lookup"><span data-stu-id="03964-138">You are then prompted to sign in using the _new account_.</span></span>

   ![Oturum açma hesabı ayarları](../../Images/PSGallery_LoginAccountChange-2.png)

3. <span data-ttu-id="03964-140">Tıkladığınızda **sonraki**, geçerli hesap kullanarak oturum açmış bir ileti görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="03964-140">When you click **Next**, you see a message that you are signed in using the current account.</span></span>
   <span data-ttu-id="03964-141">Tıklayın **oturum out ve farklı bir hesapla oturum**.</span><span class="sxs-lookup"><span data-stu-id="03964-141">Click **Sign out and sign in with a different account**.</span></span>

   ![Oturum açma hesabı ayarları](../../Images/PSGallery_LoginAccountChange-3.png)

4. <span data-ttu-id="03964-143">Yeni hesap parolasını girin.</span><span class="sxs-lookup"><span data-stu-id="03964-143">Enter the password of the new account.</span></span> <span data-ttu-id="03964-144">Parolasını girdikten sonra oturum açma hesabı güncelleştirilip güncelleştirilmediğini gösteren hesap ayarları sayfasına dönersiniz.</span><span class="sxs-lookup"><span data-stu-id="03964-144">After entering the password, you are returned to the Account Settings page showing you that the login account has been updated.</span></span>


## <a name="enable-two-factor-authentication-2fa"></a><span data-ttu-id="03964-145">İki öğeli kimlik doğrulamayı (2FA) etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="03964-145">Enable Two-Factor Authentication (2FA)</span></span>

<span data-ttu-id="03964-146">İki öğeli kimlik doğrulama, PowerShell Galerisi'nde el ile yayımlayın tüm kullanıcılar için önerilir.</span><span class="sxs-lookup"><span data-stu-id="03964-146">Two-factor authentication is recommended for all users who publish manually to the PowerShell Gallery.</span></span> <span data-ttu-id="03964-147">İki öğeli kimlik doğrulamasını etkinleştirmek için oturum açma hesabı en az iki forms kimlik doğrulaması kayıtlı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="03964-147">To enable two-factor authentication, the login account must have at least two forms of authentication registered.</span></span> <span data-ttu-id="03964-148">Bir parola biridir ve diğer formları olabilir:</span><span class="sxs-lookup"><span data-stu-id="03964-148">One is a password and the other forms can be:</span></span>

- <span data-ttu-id="03964-149">Kısa mesaj alabilen bir telefon numarası</span><span class="sxs-lookup"><span data-stu-id="03964-149">A phone number that can receive text messages</span></span>
- <span data-ttu-id="03964-150">Cep telefonunuza Microsoft Authenticator gibi bir kayıtlı Doğrulayıcı uygulama</span><span class="sxs-lookup"><span data-stu-id="03964-150">A registered authenticator application, such as Microsoft Authenticator for your mobile phone</span></span>

<span data-ttu-id="03964-151">AAD hesap bilgilerinizi ya da Microsoft kimliği hesabı güvenlik ayarlarınızı bu form kimlik doğrulaması yapılandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="03964-151">These forms of authentication must be configured in your AAD account information or in your Microsoft ID Account Security settings.</span></span>

<span data-ttu-id="03964-152">2fa'yı etkinleştirdikten sonra PowerShell Galerisi'nden oturum açışınızda her yapılandırılmış forms kimlik doğrulaması kullanarak kimlik doğrulaması için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="03964-152">Once 2FA is enabled, you are required to authenticate using the configured forms of authentication every time you sign in to the PowerShell Gallery.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="03964-153">PowerShell Galerisi site için iki öğeli kimlik doğrulamasını etkinleştirmek için tüm kullanımlar, oturum açma hesabınızın 2fa'yı etkinleştirmek gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="03964-153">Enabling two-factor authentication for the PowerShell Gallery site does not require you to enable 2FA for all uses of your login account.</span></span> <span data-ttu-id="03964-154">Daha fazla bilgi için [iki basamaklı doğrulama hakkında](https://support.microsoft.com/help/12408/microsoft-account-about-two-step-verification).</span><span class="sxs-lookup"><span data-stu-id="03964-154">For more information, see [About two-step verification](https://support.microsoft.com/help/12408/microsoft-account-about-two-step-verification).</span></span>

## <a name="change-your-profile-picture"></a><span data-ttu-id="03964-155">Profil resminizi değiştirme</span><span class="sxs-lookup"><span data-stu-id="03964-155">Change your profile picture</span></span>

<span data-ttu-id="03964-156">PowerShell Galerisi depolamak ve profilinizle ilişkili resmi görüntülemek için Gravatar kullanır.</span><span class="sxs-lookup"><span data-stu-id="03964-156">The PowerShell Gallery relies on Gravatar to store and display the picture associated with your profile.</span></span> <span data-ttu-id="03964-157">Profil resminize güncelleştirmek için şurayı ziyaret edin [Gravatar.com](http://www.gravatar.com/).</span><span class="sxs-lookup"><span data-stu-id="03964-157">To update your profile image, visit [Gravatar.com](http://www.gravatar.com/).</span></span>
