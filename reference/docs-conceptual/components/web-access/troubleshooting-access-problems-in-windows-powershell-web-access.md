---
ms.date: 08/23/2017
keywords: PowerShell cmdlet'i
title: windows powershell web erişiminde erişim sorunlarını giderme
ms.openlocfilehash: 314e4a8098988111739705d55b68ff5ed2f5eff3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086604"
---
# <a name="troubleshooting-access-problems-in-windows-powershell-web-access"></a><span data-ttu-id="bd9cf-103">Windows PowerShell Web Erişimi’nde Erişim Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="bd9cf-103">Troubleshooting Access Problems in Windows PowerShell Web Access</span></span>

<span data-ttu-id="bd9cf-104">Güncelleme tarihi: Haziran 24 (23 Ağustos 2017 düzenlendi) 2013</span><span class="sxs-lookup"><span data-stu-id="bd9cf-104">Updated: June 24, 2013 (revised August 23, 2017)</span></span>

<span data-ttu-id="bd9cf-105">Uygulama hedefi: Windows Server 2012 R2, Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="bd9cf-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="bd9cf-106">Aşağıdaki bölümlerde, Windows PowerShell Web Erişimi'ni kullanarak bir uzak bilgisayara bağlanmaya çalışırken bazı yaygın sorunlar belirlemek ve sorunları çözmek için öneriler içerir.</span><span class="sxs-lookup"><span data-stu-id="bd9cf-106">The following sections identify some common problems when attempting to connect to a remote computer by using Windows PowerShell Web Access, and includes suggestions for resolving the problems.</span></span>

## <a name="sign-in-failure"></a><span data-ttu-id="bd9cf-107">Oturum açma hatası</span><span class="sxs-lookup"><span data-stu-id="bd9cf-107">Sign-in failure</span></span>

<span data-ttu-id="bd9cf-108">Hata, aşağıdakilerden biri nedeniyle oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="bd9cf-108">Failure could occur because of any of the following.</span></span>

- <span data-ttu-id="bd9cf-109">Bilgisayara kullanıcı erişimine izin veren bir yetkilendirme kuralı ya da uzak bilgisayarda belirli bir oturum yapılandırması yok.</span><span class="sxs-lookup"><span data-stu-id="bd9cf-109">An authorization rule that allows the user access to the computer, or a specific session configuration on the remote computer, does not exist.</span></span>

  <span data-ttu-id="bd9cf-110">Windows PowerShell Web erişimi güvenliği kısıtlayıcıdır; Yetkilendirme kuralları kullanarak, kullanıcılar uzak bilgisayarlara açık erişim verilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="bd9cf-110">Windows PowerShell Web Access security is restrictive; users must be granted explicit access to remote computers by using authorization rules.</span></span>

  <span data-ttu-id="bd9cf-111">Yetkilendirme kuralları oluşturma hakkında daha fazla bilgi için bkz. [yetkilendirme kuralları ve güvenlik özellikleri, Windows PowerShell Web erişimi](authorization-rules-and-security-features-of-windows-powershell-web-access.md).</span><span class="sxs-lookup"><span data-stu-id="bd9cf-111">For more information about creating authorization rules, see [Authorization Rules and Security Features of Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).</span></span>

- <span data-ttu-id="bd9cf-112">Kullanıcının, hedef bilgisayara yetkili erişimi yok.</span><span class="sxs-lookup"><span data-stu-id="bd9cf-112">The user does not have authorized access to the destination computer.</span></span> <span data-ttu-id="bd9cf-113">Bu, erişim denetim listeleri (ACL’ler) ile belirlenir.</span><span class="sxs-lookup"><span data-stu-id="bd9cf-113">This is determined by access control lists (ACLs).</span></span>

  <span data-ttu-id="bd9cf-114">Daha fazla bilgi için [Windows PowerShell Web erişimi için oturum açarken](use-the-web-based-windows-powershell-console.md#signing-in-to-windows-powershell-web-access), veya Windows PowerShell ekibi blogu.</span><span class="sxs-lookup"><span data-stu-id="bd9cf-114">For more information, see [Signing in to Windows PowerShell Web Access](use-the-web-based-windows-powershell-console.md#signing-in-to-windows-powershell-web-access), or the Windows PowerShell Team Blog.</span></span>

- <span data-ttu-id="bd9cf-115">Windows PowerShell uzaktan yönetimi hedef bilgisayarda etkinleştirilmemiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="bd9cf-115">Windows PowerShell remote management might not be enabled on the destination computer.</span></span>

  <span data-ttu-id="bd9cf-116">Uzaktan Yönetim, kullanıcının bağlanmaya çalıştığı bilgisayarda etkin olup olmadığını doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="bd9cf-116">Verify remote management is enabled on the computer to which the user is trying to connect.</span></span>

  <span data-ttu-id="bd9cf-117">Daha fazla bilgi için [bilgisayarınızı uzaktan yapılandırmak için nasıl](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_requirements#how-to-configure-your-computer-for-remoting).</span><span class="sxs-lookup"><span data-stu-id="bd9cf-117">For more information, see [How to Configure Your Computer for Remoting](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_requirements#how-to-configure-your-computer-for-remoting).</span></span>

## <a name="internal-server-error"></a><span data-ttu-id="bd9cf-118">İç sunucu hatası</span><span class="sxs-lookup"><span data-stu-id="bd9cf-118">Internal Server Error</span></span>

<span data-ttu-id="bd9cf-119">Kullanıcılar Windows PowerShell Web Erişimi'nde bir Internet Explorer penceresi oturum açmayı denediğinde gösterilen bir **iç sunucu hatası** sayfasında veya *Internet Explorer* yanıt vermiyor.</span><span class="sxs-lookup"><span data-stu-id="bd9cf-119">When users try to sign in to Windows PowerShell Web Access in an Internet Explorer window, they are shown an **Internal Server Error** page, or *Internet Explorer* stops responding.</span></span>

<span data-ttu-id="bd9cf-120">Bu sorun, Internet Explorer’a özeldir.</span><span class="sxs-lookup"><span data-stu-id="bd9cf-120">This issue is specific to Internet Explorer.</span></span>

### <a name="possible-cause"></a><span data-ttu-id="bd9cf-121">Olası neden</span><span class="sxs-lookup"><span data-stu-id="bd9cf-121">Possible cause</span></span>

<span data-ttu-id="bd9cf-122">Bu, Çince karakterler içeren bir etki alanı adı ile oturum açmış kullanıcılar için veya bir veya daha fazla Çince karakter ağ geçidi sunucusunun parçası ise oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="bd9cf-122">This can occur for users who have signed in with a domain name that contains Chinese characters, or if one or more Chinese characters are part of the gateway server name.</span></span>

#### <a name="workaround"></a><span data-ttu-id="bd9cf-123">Geçici Çözüm</span><span class="sxs-lookup"><span data-stu-id="bd9cf-123">Workaround</span></span>

1. [<span data-ttu-id="bd9cf-124">Yükleme ve Internet Explorer 10 çalıştırma</span><span class="sxs-lookup"><span data-stu-id="bd9cf-124">Install and run Internet Explorer 10</span></span>](https://ie.microsoft.com/testdrive/info/downloads/Default.html)
1. <span data-ttu-id="bd9cf-125">Internet Explorer değiştirme **belge modu** ayarını *ıe10* standartları.</span><span class="sxs-lookup"><span data-stu-id="bd9cf-125">Change Internet Explorer **Document Mode** setting to *IE10* standards.</span></span>
   1. <span data-ttu-id="bd9cf-126">Tuşuna **F12** geliştirici araçları konsolunu açmak için</span><span class="sxs-lookup"><span data-stu-id="bd9cf-126">Press **F12** to open the Developer Tools console</span></span>
   1. <span data-ttu-id="bd9cf-127">Internet Explorer 10'da tıklayın **tarayıcı modu**ve ardından *Internet Explorer 10*.</span><span class="sxs-lookup"><span data-stu-id="bd9cf-127">In Internet Explorer 10, click **Browser Mode**, and then select *Internet Explorer 10*.</span></span>
   1. <span data-ttu-id="bd9cf-128">Tıklayın **belge modu**ve ardından *ıe10* standartları.</span><span class="sxs-lookup"><span data-stu-id="bd9cf-128">Click **Document Mode**, and then click *IE10* standards.</span></span>
   1. <span data-ttu-id="bd9cf-129">Tuşuna **F12** geliştirici araçları konsolunu kapatın.</span><span class="sxs-lookup"><span data-stu-id="bd9cf-129">Press **F12** again to close the Developer Tools console.</span></span>
1. <span data-ttu-id="bd9cf-130">Internet Explorer 10 otomatik proxy yapılandırmasını devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="bd9cf-130">Disable automatic proxy configuration in Internet Explorer 10.</span></span>
   1. <span data-ttu-id="bd9cf-131">Tıklayın **Araçları**ve ardından **Internet Seçenekleri**.</span><span class="sxs-lookup"><span data-stu-id="bd9cf-131">Click **Tools**, and then click **Internet Options**.</span></span>
   1. <span data-ttu-id="bd9cf-132">İçinde **Internet Seçenekleri** iletişim kutusundaki **bağlantıları** sekmesinde **LAN Ayarları**.</span><span class="sxs-lookup"><span data-stu-id="bd9cf-132">In the **Internet Options** dialog box, on the **Connections** tab, click **LAN settings**.</span></span>
   1. <span data-ttu-id="bd9cf-133">NET **ayarlarını otomatik olarak algıla** onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="bd9cf-133">Clear the **Automatically detect settings** check box.</span></span> <span data-ttu-id="bd9cf-134">Tıklayın **Tamam**ve ardından **Tamam** kapatmak için tekrar *Internet Seçenekleri* iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="bd9cf-134">Click **OK**, and then click **OK** again to close the *Internet Options* dialog box.</span></span>

## <a name="cannot-connect-to-a-remote-workgroup-computer"></a><span data-ttu-id="bd9cf-135">Bir uzak çalışma grubu bilgisayarına bağlanılamıyor</span><span class="sxs-lookup"><span data-stu-id="bd9cf-135">Cannot connect to a remote workgroup computer</span></span>

<span data-ttu-id="bd9cf-136">Hedef bilgisayarın bir çalışma grubunun bir üyesi ise, kullanıcı adınızı sağlamak ve bilgisayara oturum açmak için aşağıdaki sözdizimini kullanın: `<workgroup_name>\<user_name>`</span><span class="sxs-lookup"><span data-stu-id="bd9cf-136">If the destination computer is a member of a workgroup, use the following syntax to provide your user name and sign in to the computer: `<workgroup_name>\<user_name>`</span></span>

## <a name="cannot-find-web-server-iis-management-tools-even-though-the-role-was-installed"></a><span data-ttu-id="bd9cf-137">Rol yüklenmiş olsa dahi, Web Sunucusu (IIS) yönetim araçları bulunamıyor</span><span class="sxs-lookup"><span data-stu-id="bd9cf-137">Cannot find Web Server (IIS) management tools, even though the role was installed</span></span>

<span data-ttu-id="bd9cf-138">Windows PowerShell Web erişimi kullanarak yüklediyseniz `Install-WindowsFeature` cmdlet'i, Yönetim Araçları yüklü değil sürece `-IncludeManagementTools` parametresi için cmdlet eklendi.</span><span class="sxs-lookup"><span data-stu-id="bd9cf-138">If you installed Windows PowerShell Web Access by using the `Install-WindowsFeature` cmdlet, management tools are not installed unless the `-IncludeManagementTools` parameter is added to the cmdlet.</span></span>

<span data-ttu-id="bd9cf-139">Bir örnek için bkz. [Windows PowerShell cmdlet'lerini kullanarak Windows PowerShell Web erişimi yüklemek için](install-and-use-windows-powershell-web-access.md#to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets).</span><span class="sxs-lookup"><span data-stu-id="bd9cf-139">For an example, see [To install Windows PowerShell Web Access by using Windows PowerShell cmdlets](install-and-use-windows-powershell-web-access.md#to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets).</span></span>

<span data-ttu-id="bd9cf-140">IIS Yöneticisi konsolunu ekleyebilir ve diğer IIS Yönetim Araçları'nı seçerek ihtiyacınız olduğunu araçları bir **Ekle roller ve Özellikler Sihirbazı** Ağ Geçidi sunucusuna hedeflenmiş oturumu.</span><span class="sxs-lookup"><span data-stu-id="bd9cf-140">You can add the IIS Manager console, and other IIS management tools that you need, by selecting the tools in an **Add Roles and Features Wizard** session that is targeted at the gateway server.</span></span>
<span data-ttu-id="bd9cf-141">Rol ve Özellik Ekleme Sihirbazı açılır gelen Sunucu Yöneticisi içinde.</span><span class="sxs-lookup"><span data-stu-id="bd9cf-141">The Add Roles and Features Wizard is opened from within Server Manager.</span></span>

## <a name="windows-powershell-web-access-website-is-not-accessible"></a><span data-ttu-id="bd9cf-142">Windows PowerShell Web Erişimi Web sitesi erişilebilir değil</span><span class="sxs-lookup"><span data-stu-id="bd9cf-142">Windows PowerShell Web Access website is not accessible</span></span>

<span data-ttu-id="bd9cf-143">Internet Explorer (IE ESC) Artırılmış Güvenlik Yapılandırması etkinse, Windows PowerShell Web Erişimi Web sitesi Güvenilen siteler listesine ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bd9cf-143">If Enhanced Security Configuration is enabled in Internet Explorer (IE ESC), you can add the Windows PowerShell Web Access website to the list of trusted sites.</span></span>

<span data-ttu-id="bd9cf-144">Güvenlik riskleri nedeniyle daha az önerilen bir yaklaşım, IE ESC'yi devre dışı bırakmaktır.</span><span class="sxs-lookup"><span data-stu-id="bd9cf-144">A less recommended approach, due to security risks, is to disable IE ESC.</span></span>
<span data-ttu-id="bd9cf-145">Üzerinde Sunucu Yöneticisi'nde yerel sunucu sayfası özellikler kutucuğundaki IE ESC'yi devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bd9cf-145">You can disable IE ESC in the Properties tile on the Local Server page in Server Manager.</span></span>

## <a name="an-authorization-failure-occurred-verify-that-you-are-authorized-to-connect-to-the-destination-computer"></a><span data-ttu-id="bd9cf-146">Bir Yetkilendirme hatası oluştu.</span><span class="sxs-lookup"><span data-stu-id="bd9cf-146">An authorization failure occurred.</span></span> <span data-ttu-id="bd9cf-147">Hedef bilgisayara bağlanmak için yetkilendirilmiş olduğunuzu doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="bd9cf-147">Verify that you are authorized to connect to the destination computer.</span></span>

<span data-ttu-id="bd9cf-148">Ağ Geçidi sunucusu hedef bilgisayar ve ayrıca bir çalışma grubunda olduğunda, bağlantı kurulmaya çalışılırken yukarıdaki hata iletisi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="bd9cf-148">The above error message is displayed while trying to connect when the gateway server is the destination computer, and is also in a workgroup.</span></span>

<span data-ttu-id="bd9cf-149">Ağ Geçidi sunucusu hedef sunucu da olduğunda ve bir çalışma grubundaysa, kullanıcı adı, bilgisayar adı ve kullanıcı grubu adı belirtin.</span><span class="sxs-lookup"><span data-stu-id="bd9cf-149">When the gateway server is also the destination server, and it is in a workgroup, specify the user name, computer name, and user group name.</span></span>
<span data-ttu-id="bd9cf-150">Bir nokta (.) kendisi tarafından bilgisayar adını temsil etmek için kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="bd9cf-150">Do not use a dot (.) by itself to represent the computer name.</span></span>

### <a name="scenarios-and-proper-values"></a><span data-ttu-id="bd9cf-151">Senaryolar ve uygun değerleri</span><span class="sxs-lookup"><span data-stu-id="bd9cf-151">Scenarios and proper values</span></span>

#### <a name="all-cases"></a><span data-ttu-id="bd9cf-152">Tüm durumlarda</span><span class="sxs-lookup"><span data-stu-id="bd9cf-152">All cases</span></span>

<span data-ttu-id="bd9cf-153">Parametre</span><span class="sxs-lookup"><span data-stu-id="bd9cf-153">Parameter</span></span> | <span data-ttu-id="bd9cf-154">Değer</span><span class="sxs-lookup"><span data-stu-id="bd9cf-154">Value</span></span>
-- | --
<span data-ttu-id="bd9cf-155">UserName</span><span class="sxs-lookup"><span data-stu-id="bd9cf-155">UserName</span></span> | <span data-ttu-id="bd9cf-156">Sunucu\_adı\\kullanıcı\_adı</span><span class="sxs-lookup"><span data-stu-id="bd9cf-156">Server\_name\\user\_name</span></span><br/><span data-ttu-id="bd9cf-157">Localhost\\kullanıcı\_adı</span><span class="sxs-lookup"><span data-stu-id="bd9cf-157">Localhost\\user\_name</span></span><br/><span data-ttu-id="bd9cf-158">. \\kullanıcı\_adı</span><span class="sxs-lookup"><span data-stu-id="bd9cf-158">.\\user\_name</span></span>
<span data-ttu-id="bd9cf-159">UserGroup</span><span class="sxs-lookup"><span data-stu-id="bd9cf-159">UserGroup</span></span> | <span data-ttu-id="bd9cf-160">Sunucu\_adı\\kullanıcı\_grubu</span><span class="sxs-lookup"><span data-stu-id="bd9cf-160">Server\_name\\user\_group</span></span><br/><span data-ttu-id="bd9cf-161">Localhost\\kullanıcı\_grubu</span><span class="sxs-lookup"><span data-stu-id="bd9cf-161">Localhost\\user\_group</span></span><br/><span data-ttu-id="bd9cf-162">. \\kullanıcı\_grubu</span><span class="sxs-lookup"><span data-stu-id="bd9cf-162">.\\user\_group</span></span>
<span data-ttu-id="bd9cf-163">ComputerGroup</span><span class="sxs-lookup"><span data-stu-id="bd9cf-163">ComputerGroup</span></span> | <span data-ttu-id="bd9cf-164">Sunucu\_adı\\bilgisayar\_grubu</span><span class="sxs-lookup"><span data-stu-id="bd9cf-164">Server\_name\\computer\_group</span></span><br/><span data-ttu-id="bd9cf-165">Localhost\\bilgisayar\_grubu</span><span class="sxs-lookup"><span data-stu-id="bd9cf-165">Localhost\\computer\_group</span></span><br/><span data-ttu-id="bd9cf-166">. \\bilgisayar\_grubu</span><span class="sxs-lookup"><span data-stu-id="bd9cf-166">.\\computer\_group</span></span>

#### <a name="gateway-server-is-in-a-domain"></a><span data-ttu-id="bd9cf-167">Ağ geçidi sunucu bir etki alanında</span><span class="sxs-lookup"><span data-stu-id="bd9cf-167">Gateway server is in a domain</span></span>

<span data-ttu-id="bd9cf-168">Parametre</span><span class="sxs-lookup"><span data-stu-id="bd9cf-168">Parameter</span></span> | <span data-ttu-id="bd9cf-169">Değer</span><span class="sxs-lookup"><span data-stu-id="bd9cf-169">Value</span></span>
-- | --
<span data-ttu-id="bd9cf-170">ComputerName</span><span class="sxs-lookup"><span data-stu-id="bd9cf-170">ComputerName</span></span> | <span data-ttu-id="bd9cf-171">Ağ geçidi sunucusunun tam adı veya Localhost</span><span class="sxs-lookup"><span data-stu-id="bd9cf-171">Fully qualified name of gateway server, or Localhost</span></span>

#### <a name="gateway-server-is-in-a-workgroup"></a><span data-ttu-id="bd9cf-172">Ağ geçidi sunucusu bir çalışma alanında</span><span class="sxs-lookup"><span data-stu-id="bd9cf-172">Gateway server is in a workgroup</span></span>

<span data-ttu-id="bd9cf-173">Parametre</span><span class="sxs-lookup"><span data-stu-id="bd9cf-173">Parameter</span></span> | <span data-ttu-id="bd9cf-174">Değer</span><span class="sxs-lookup"><span data-stu-id="bd9cf-174">Value</span></span>
-- | --
<span data-ttu-id="bd9cf-175">ComputerName</span><span class="sxs-lookup"><span data-stu-id="bd9cf-175">ComputerName</span></span> | <span data-ttu-id="bd9cf-176">Sunucu adı</span><span class="sxs-lookup"><span data-stu-id="bd9cf-176">Server name</span></span>

### <a name="gateway-credentials"></a><span data-ttu-id="bd9cf-177">Ağ Geçidi kimlik bilgileri</span><span class="sxs-lookup"><span data-stu-id="bd9cf-177">Gateway credentials</span></span>

<span data-ttu-id="bd9cf-178">Bir ağ geçidi sunucusuna, aşağıdakilerden biri olarak biçimlendirilmiş kimlik bilgilerini kullanarak, hedef bilgisayar olarak oturum açın.</span><span class="sxs-lookup"><span data-stu-id="bd9cf-178">Sign in to a gateway server as target computer by using credentials formatted as one of the following.</span></span>

- <span data-ttu-id="bd9cf-179">Sunucu\_adı\\kullanıcı\_adı</span><span class="sxs-lookup"><span data-stu-id="bd9cf-179">Server\_name\\user\_name</span></span>
- <span data-ttu-id="bd9cf-180">Localhost\\kullanıcı\_adı</span><span class="sxs-lookup"><span data-stu-id="bd9cf-180">Localhost\\user\_name</span></span>
- <span data-ttu-id="bd9cf-181">. \\kullanıcı\_adı</span><span class="sxs-lookup"><span data-stu-id="bd9cf-181">.\\user\_name</span></span>

## <a name="a-security-identifier-sid-is-displayed-in-an-authorization-rule"></a><span data-ttu-id="bd9cf-182">Güvenlik tanımlayıcısı (SID) bir yetkilendirme kuralında görüntüleniyor</span><span class="sxs-lookup"><span data-stu-id="bd9cf-182">A security identifier (SID) is displayed in an authorization rule</span></span>

<span data-ttu-id="bd9cf-183">Güvenlik tanımlayıcısı (SID) söz dizimi kullanıcı yerine bir yetkilendirme kuralı görüntülenen\_adı/bilgisayar\_adı.</span><span class="sxs-lookup"><span data-stu-id="bd9cf-183">A security identifier (SID) is displayed in an authorization rule instead of the syntax user\_name/computer\_name.</span></span>

<span data-ttu-id="bd9cf-184">Kural artık geçerli değil veya Active Directory Etki Alanı Hizmetleri sorgusu başarısız olmuş.</span><span class="sxs-lookup"><span data-stu-id="bd9cf-184">Either the rule is no longer valid, or the Active Directory Domain Services query failed.</span></span>
<span data-ttu-id="bd9cf-185">Bir yetkilendirme kuralı genelde burada ağ geçidi sunucusu aynı anda bir çalışma grubunda olan, ancak daha sonra bir etki alanına katılmış senaryolarda geçerli değil</span><span class="sxs-lookup"><span data-stu-id="bd9cf-185">An authorization rule is usually not valid in scenarios where the gateway server was at one time in a workgroup, but was later joined to a domain</span></span>

## <a name="cannot-sign-in-with-rule-as-an-ipv6-address-with-a-domain"></a><span data-ttu-id="bd9cf-186">Kural ile bir etki alanıyla IPv6 adresi olarak imzalanamıyor</span><span class="sxs-lookup"><span data-stu-id="bd9cf-186">Cannot sign in with rule as an IPv6 address with a domain</span></span>

<span data-ttu-id="bd9cf-187">Bir etki alanıyla IPv6 adresi olarak yetkilendirme kurallarında belirtilmiş bir hedef bilgisayara oturum açılamıyor.</span><span class="sxs-lookup"><span data-stu-id="bd9cf-187">Cannot sign in to a target computer that has been specified in authorization rules as an IPv6 address with a domain.</span></span>

<span data-ttu-id="bd9cf-188">Yetkilendirme kuralları, bir etki alanı adı biçiminde bir IPv6 adresini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="bd9cf-188">Authorization rules do not support an IPv6 address in form of a domain name.</span></span>

<span data-ttu-id="bd9cf-189">Bir IPv6 adresi kullanarak bir hedef bilgisayar belirtmek için, yetkilendirme kuralında özgün IPv6 adresini kullanın (iki nokta üst üste içeren).</span><span class="sxs-lookup"><span data-stu-id="bd9cf-189">To specify a destination computer by using an IPv6 address, use the original IPv6 address (that contains colons) in the authorization rule.</span></span>
<span data-ttu-id="bd9cf-190">Hem etki alanı hem de sayısal (iki nokta üst üste ile) IPv6 adresleri, yetkilendirme kurallarında değil ancak, Windows PowerShell Web erişimi oturum açma sayfasında hedef bilgisayar adı olarak desteklenir.</span><span class="sxs-lookup"><span data-stu-id="bd9cf-190">Both domain and numerical (with colons) IPv6 addresses are supported as the target computer name on the Windows PowerShell Web Access sign-in page, but not in authorization rules.</span></span>

<span data-ttu-id="bd9cf-191">IPv6 adresleri hakkında daha fazla bilgi için bkz. [IPv6 nasıl çalışır](https://technet.microsoft.com/library/cc781672(v=ws.10).aspx).</span><span class="sxs-lookup"><span data-stu-id="bd9cf-191">For more information about IPv6 addresses, see [How IPv6 Works](https://technet.microsoft.com/library/cc781672(v=ws.10).aspx).</span></span>

## <a name="see-also"></a><span data-ttu-id="bd9cf-192">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="bd9cf-192">See Also</span></span>

- <span data-ttu-id="bd9cf-193">[Yetkilendirme kuralları ve güvenlik özellikleri Windows PowerShell Web erişimi](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)</span><span class="sxs-lookup"><span data-stu-id="bd9cf-193">[Authorization Rules and Security Features of Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)</span></span>
- <span data-ttu-id="bd9cf-194">[Web tabanlı Windows PowerShell konsolunu kullanma](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)</span><span class="sxs-lookup"><span data-stu-id="bd9cf-194">[Use the Web-based Windows PowerShell Console](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)</span></span>
- [<span data-ttu-id="bd9cf-195">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="bd9cf-195">about_Remote_Requirements</span></span>](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_requirements)