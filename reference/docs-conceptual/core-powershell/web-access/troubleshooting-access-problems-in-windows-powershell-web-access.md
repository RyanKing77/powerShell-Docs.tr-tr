---
ms.date: 2017-08-23
keywords: PowerShell cmdlet'i
title: "windows powershell web erişimi'nde erişim sorunlarını giderme"
ms.openlocfilehash: 6e51df3f4c6ac196c855ad918a91394d02c7d75e
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2018
---
# <a name="troubleshooting-access-problems-in-windows-powershell-web-access"></a><span data-ttu-id="66895-103">Windows PowerShell Web Erişimi’nde Erişim Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="66895-103">Troubleshooting Access Problems in Windows PowerShell Web Access</span></span>

<span data-ttu-id="66895-104">Güncelleştirme: 24 Haziran (23 Ağustos 2017 düzenlendi) 2013</span><span class="sxs-lookup"><span data-stu-id="66895-104">Updated: June 24, 2013 (revised August 23, 2017)</span></span>

<span data-ttu-id="66895-105">İçin geçerlidir: Windows Server 2012 R2, Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="66895-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="66895-106">Aşağıdaki bölümlerde, Windows PowerShell Web erişimi kullanarak bir uzak bilgisayara bağlanmaya çalışılırken bazı yaygın sorunlar belirlemek ve sorunların çözümü için öneriler içermektedir.</span><span class="sxs-lookup"><span data-stu-id="66895-106">The following sections identify some common problems when attempting to connect to a remote computer by using Windows PowerShell Web Access, and includes suggestions for resolving the problems.</span></span>

## <a name="sign-in-failure"></a><span data-ttu-id="66895-107">Oturum açma hatası</span><span class="sxs-lookup"><span data-stu-id="66895-107">Sign-in failure</span></span>

<span data-ttu-id="66895-108">Hata, aşağıdakilerden biri nedeniyle oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="66895-108">Failure could occur because of any of the following.</span></span>

- <span data-ttu-id="66895-109">Bilgisayara kullanıcı erişimine izin veren bir yetkilendirme kuralı ya da uzak bilgisayarda belirli bir oturum yapılandırması yok.</span><span class="sxs-lookup"><span data-stu-id="66895-109">An authorization rule that allows the user access to the computer, or a specific session configuration on the remote computer, does not exist.</span></span>

  <span data-ttu-id="66895-110">Windows PowerShell Web erişimi güvenliği kısıtlayıcıdır; Yetkilendirme kuralları kullanılarak, kullanıcılara uzak bilgisayarlara açık erişim verilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="66895-110">Windows PowerShell Web Access security is restrictive; users must be granted explicit access to remote computers by using authorization rules.</span></span>

  <span data-ttu-id="66895-111">Yetkilendirme kuralları oluşturma hakkında daha fazla bilgi için bkz: [yetkilendirme kuralları ve güvenlik özellikleri, Windows PowerShell Web erişimi](authorization-rules-and-security-features-of-windows-powershell-web-access.md).</span><span class="sxs-lookup"><span data-stu-id="66895-111">For more information about creating authorization rules, see [Authorization Rules and Security Features of Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).</span></span>

- <span data-ttu-id="66895-112">Kullanıcının, hedef bilgisayara yetkili erişimi yok.</span><span class="sxs-lookup"><span data-stu-id="66895-112">The user does not have authorized access to the destination computer.</span></span> <span data-ttu-id="66895-113">Bu, erişim denetim listeleri (ACL’ler) ile belirlenir.</span><span class="sxs-lookup"><span data-stu-id="66895-113">This is determined by access control lists (ACLs).</span></span>

  <span data-ttu-id="66895-114">Daha fazla bilgi için bkz: [Windows PowerShell Web erişimi için oturum açma](use-the-web-based-windows-powershell-console.md#signing-in-to-windows-powershell-web-access), veya Windows PowerShell ekip blogu.</span><span class="sxs-lookup"><span data-stu-id="66895-114">For more information, see [Signing in to Windows PowerShell Web Access](use-the-web-based-windows-powershell-console.md#signing-in-to-windows-powershell-web-access), or the Windows PowerShell Team Blog.</span></span>

- <span data-ttu-id="66895-115">Windows PowerShell uzaktan yönetimi hedef bilgisayarda etkinleştirilmemiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="66895-115">Windows PowerShell remote management might not be enabled on the destination computer.</span></span>

  <span data-ttu-id="66895-116">Uzaktan Yönetim için kullanıcının bağlanmaya çalıştığı bilgisayarda etkin doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="66895-116">Verify remote management is enabled on the computer to which the user is trying to connect.</span></span>

  <span data-ttu-id="66895-117">Daha fazla bilgi için bkz: [bilgisayarınızı yapılandırma uzaktan iletişim için nasıl](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_requirements#how-to-configure-your-computer-for-remoting).</span><span class="sxs-lookup"><span data-stu-id="66895-117">For more information, see [How to Configure Your Computer for Remoting](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_requirements#how-to-configure-your-computer-for-remoting).</span></span>

## <a name="internal-server-error"></a><span data-ttu-id="66895-118">İç sunucu hatası</span><span class="sxs-lookup"><span data-stu-id="66895-118">Internal Server Error</span></span>

<span data-ttu-id="66895-119">Kullanıcılar Windows PowerShell Web erişimi bir Internet Explorer penceresinde oturum açmaya çalıştığında, bunlar gösterilir bir **iç sunucu hatası** sayfasında veya *Internet Explorer* yanıt vermiyor.</span><span class="sxs-lookup"><span data-stu-id="66895-119">When users try to sign in to Windows PowerShell Web Access in an Internet Explorer window, they are shown an **Internal Server Error** page, or *Internet Explorer* stops responding.</span></span>

<span data-ttu-id="66895-120">Bu sorun, Internet Explorer’a özeldir.</span><span class="sxs-lookup"><span data-stu-id="66895-120">This issue is specific to Internet Explorer.</span></span>

### <a name="possible-cause"></a><span data-ttu-id="66895-121">Olası neden</span><span class="sxs-lookup"><span data-stu-id="66895-121">Possible cause</span></span>

<span data-ttu-id="66895-122">Bu, Çince karakterler içeren bir etki alanı adı ile oturum açmış kullanıcılar için veya bir veya daha fazla Çince karakter ağ geçidi sunucusunun parçası ise oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="66895-122">This can occur for users who have signed in with a domain name that contains Chinese characters, or if one or more Chinese characters are part of the gateway server name.</span></span>

#### <a name="workaround"></a><span data-ttu-id="66895-123">Geçici çözüm</span><span class="sxs-lookup"><span data-stu-id="66895-123">Workaround</span></span>

1. [<span data-ttu-id="66895-124">Internet Explorer 10 yüklemesi ve çalıştırması</span><span class="sxs-lookup"><span data-stu-id="66895-124">Install and run Internet Explorer 10</span></span>](http://ie.microsoft.com/testdrive/info/downloads/Default.html)
1. <span data-ttu-id="66895-125">Internet Explorer değiştirme **belge modu** ayarını *ıe10* standartları.</span><span class="sxs-lookup"><span data-stu-id="66895-125">Change Internet Explorer **Document Mode** setting to *IE10* standards.</span></span>
   1. <span data-ttu-id="66895-126">Tuşuna **F12** geliştirici araçları konsolunu açmak için</span><span class="sxs-lookup"><span data-stu-id="66895-126">Press **F12** to open the Developer Tools console</span></span>
   1. <span data-ttu-id="66895-127">Internet Explorer 10'a tıklayın **tarayıcı modu**ve ardından *Internet Explorer 10*.</span><span class="sxs-lookup"><span data-stu-id="66895-127">In Internet Explorer 10, click **Browser Mode**, and then select *Internet Explorer 10*.</span></span>
   1. <span data-ttu-id="66895-128">Tıklatın **belge modu**ve ardından *ıe10* standartları.</span><span class="sxs-lookup"><span data-stu-id="66895-128">Click **Document Mode**, and then click *IE10* standards.</span></span>
   1. <span data-ttu-id="66895-129">Tuşuna **F12** geliştirici araçları konsolunu kapatın.</span><span class="sxs-lookup"><span data-stu-id="66895-129">Press **F12** again to close the Developer Tools console.</span></span>
1. <span data-ttu-id="66895-130">Internet Explorer 10'daki otomatik proxy yapılandırmasını devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="66895-130">Disable automatic proxy configuration in Internet Explorer 10.</span></span>
   1. <span data-ttu-id="66895-131">Tıklatın **Araçları**ve ardından **Internet Seçenekleri**.</span><span class="sxs-lookup"><span data-stu-id="66895-131">Click **Tools**, and then click **Internet Options**.</span></span>
   1. <span data-ttu-id="66895-132">İçinde **Internet Seçenekleri** iletişim kutusundaki **bağlantıları** sekmesini tıklatın, **LAN Ayarları**.</span><span class="sxs-lookup"><span data-stu-id="66895-132">In the **Internet Options** dialog box, on the **Connections** tab, click **LAN settings**.</span></span>
   1. <span data-ttu-id="66895-133">Clear **ayarları otomatik olarak algıla** onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="66895-133">Clear the **Automatically detect settings** check box.</span></span> <span data-ttu-id="66895-134">Tıklatın **Tamam**ve ardından **Tamam** kapatmak için tekrar *Internet Seçenekleri* iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="66895-134">Click **OK**, and then click **OK** again to close the *Internet Options* dialog box.</span></span>

## <a name="cannot-connect-to-a-remote-workgroup-computer"></a><span data-ttu-id="66895-135">Bir uzak çalışma grubu bilgisayarına bağlanılamıyor</span><span class="sxs-lookup"><span data-stu-id="66895-135">Cannot connect to a remote workgroup computer</span></span>

<span data-ttu-id="66895-136">Hedef bilgisayar bir çalışma grubunun üyesi ise, kullanıcı adınızı sağlamak ve bilgisayara oturum açmak için aşağıdaki sözdizimini kullanın: `<workgroup_name>\<user_name>`</span><span class="sxs-lookup"><span data-stu-id="66895-136">If the destination computer is a member of a workgroup, use the following syntax to provide your user name and sign in to the computer: `<workgroup_name>\<user_name>`</span></span>

## <a name="cannot-find-web-server-iis-management-tools-even-though-the-role-was-installed"></a><span data-ttu-id="66895-137">Rol yüklenmiş olsa dahi, Web Sunucusu (IIS) yönetim araçları bulunamıyor</span><span class="sxs-lookup"><span data-stu-id="66895-137">Cannot find Web Server (IIS) management tools, even though the role was installed</span></span>

<span data-ttu-id="66895-138">Windows PowerShell Web erişimi kullanarak yüklediyseniz `Install-WindowsFeature` cmdlet'i, Yönetim Araçları yüklü değil. sürece `-IncludeManagementTools` parametresini cmdlet'e eklenir.</span><span class="sxs-lookup"><span data-stu-id="66895-138">If you installed Windows PowerShell Web Access by using the `Install-WindowsFeature` cmdlet, management tools are not installed unless the `-IncludeManagementTools` parameter is added to the cmdlet.</span></span>

<span data-ttu-id="66895-139">Bir örnek için bkz: [Windows PowerShell cmdlet'lerini kullanarak Windows PowerShell Web erişimi yükleme](install-and-use-windows-powershell-web-access.md#to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets).</span><span class="sxs-lookup"><span data-stu-id="66895-139">For an example, see [To install Windows PowerShell Web Access by using Windows PowerShell cmdlets](install-and-use-windows-powershell-web-access.md#to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets).</span></span>

<span data-ttu-id="66895-140">IIS Yöneticisi konsolunu ekleyebilir ve gerektiğini bildiren araçları seçerek diğer IIS Yönetim Araçları bir **Ekle roller ve Özellikler Sihirbazı** Ağ Geçidi sunucusuna hedeflenmiş oturumu.</span><span class="sxs-lookup"><span data-stu-id="66895-140">You can add the IIS Manager console, and other IIS management tools that you need, by selecting the tools in an **Add Roles and Features Wizard** session that is targeted at the gateway server.</span></span>
<span data-ttu-id="66895-141">Ekle roller ve Özellikler Sihirbazı açıldığında gelen Sunucu Yöneticisi içinde.</span><span class="sxs-lookup"><span data-stu-id="66895-141">The Add Roles and Features Wizard is opened from within Server Manager.</span></span>

## <a name="windows-powershell-web-access-website-is-not-accessible"></a><span data-ttu-id="66895-142">Windows PowerShell Web Erişimi Web sitesi erişilebilir değil</span><span class="sxs-lookup"><span data-stu-id="66895-142">Windows PowerShell Web Access website is not accessible</span></span>

<span data-ttu-id="66895-143">Internet Explorer (IE ESC) Artırılmış Güvenlik Yapılandırması etkinse, Windows PowerShell Web Erişimi Web sitesini güvenilir siteler listesine ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66895-143">If Enhanced Security Configuration is enabled in Internet Explorer (IE ESC), you can add the Windows PowerShell Web Access website to the list of trusted sites.</span></span>

<span data-ttu-id="66895-144">Güvenlik riskleri nedeniyle daha az önerilen bir yaklaşım, IE ESC'yi devre dışı bırakmaktır.</span><span class="sxs-lookup"><span data-stu-id="66895-144">A less recommended approach, due to security risks, is to disable IE ESC.</span></span>
<span data-ttu-id="66895-145">Yerel Sunucu Sayfası Sunucu Yöneticisi'nde bulunan özellikler kutucuğunda IE ESC'yi devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66895-145">You can disable IE ESC in the Properties tile on the Local Server page in Server Manager.</span></span>

## <a name="an-authorization-failure-occurred-verify-that-you-are-authorized-to-connect-to-the-destination-computer"></a><span data-ttu-id="66895-146">Bir Yetkilendirme hatası oluştu.</span><span class="sxs-lookup"><span data-stu-id="66895-146">An authorization failure occurred.</span></span> <span data-ttu-id="66895-147">Hedef bilgisayara bağlanmak için yetkilendirilmiş olduğunuzu doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="66895-147">Verify that you are authorized to connect to the destination computer.</span></span>

<span data-ttu-id="66895-148">Ağ Geçidi sunucusu hedef bilgisayar ve ayrıca bir çalışma grubu içinde olduğunda bağlanmaya çalışıldığında yukarıdaki hata iletisi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="66895-148">The above error message is displayed while trying to connect when the gateway server is the destination computer, and is also in a workgroup.</span></span>

<span data-ttu-id="66895-149">Ağ Geçidi sunucusu hedef sunucu da olduğunda ve bir çalışma grubunda olduğunda kullanıcı adı, bilgisayar adı ve kullanıcı grubu adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="66895-149">When the gateway server is also the destination server, and it is in a workgroup, specify the user name, computer name, and user group name.</span></span>
<span data-ttu-id="66895-150">Bir nokta (.) kendisi tarafından bilgisayar adını temsil etmek için kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="66895-150">Do not use a dot (.) by itself to represent the computer name.</span></span>

### <a name="scenarios-and-proper-values"></a><span data-ttu-id="66895-151">Senaryolar ve uygun değerleri</span><span class="sxs-lookup"><span data-stu-id="66895-151">Scenarios and proper values</span></span>

#### <a name="all-cases"></a><span data-ttu-id="66895-152">Tüm durumları</span><span class="sxs-lookup"><span data-stu-id="66895-152">All cases</span></span>

<span data-ttu-id="66895-153">Parametre</span><span class="sxs-lookup"><span data-stu-id="66895-153">Parameter</span></span> | <span data-ttu-id="66895-154">Değer</span><span class="sxs-lookup"><span data-stu-id="66895-154">Value</span></span>
-- | --
<span data-ttu-id="66895-155">UserName</span><span class="sxs-lookup"><span data-stu-id="66895-155">UserName</span></span> | <span data-ttu-id="66895-156">Sunucu\_adı\\kullanıcı\_adı</span><span class="sxs-lookup"><span data-stu-id="66895-156">Server\_name\\user\_name</span></span><br/><span data-ttu-id="66895-157">Localhost\\kullanıcı\_adı</span><span class="sxs-lookup"><span data-stu-id="66895-157">Localhost\\user\_name</span></span><br/><span data-ttu-id="66895-158">. \\kullanıcı\_adı</span><span class="sxs-lookup"><span data-stu-id="66895-158">.\\user\_name</span></span>
<span data-ttu-id="66895-159">UserGroup</span><span class="sxs-lookup"><span data-stu-id="66895-159">UserGroup</span></span> | <span data-ttu-id="66895-160">Sunucu\_adı\\kullanıcı\_grubu</span><span class="sxs-lookup"><span data-stu-id="66895-160">Server\_name\\user\_group</span></span><br/><span data-ttu-id="66895-161">Localhost\\kullanıcı\_grubu</span><span class="sxs-lookup"><span data-stu-id="66895-161">Localhost\\user\_group</span></span><br/><span data-ttu-id="66895-162">. \\kullanıcı\_grubu</span><span class="sxs-lookup"><span data-stu-id="66895-162">.\\user\_group</span></span>
<span data-ttu-id="66895-163">ComputerGroup</span><span class="sxs-lookup"><span data-stu-id="66895-163">ComputerGroup</span></span> | <span data-ttu-id="66895-164">Sunucu\_adı\\bilgisayar\_grubu</span><span class="sxs-lookup"><span data-stu-id="66895-164">Server\_name\\computer\_group</span></span><br/><span data-ttu-id="66895-165">Localhost\\bilgisayar\_grubu</span><span class="sxs-lookup"><span data-stu-id="66895-165">Localhost\\computer\_group</span></span><br/><span data-ttu-id="66895-166">. \\bilgisayar\_grubu</span><span class="sxs-lookup"><span data-stu-id="66895-166">.\\computer\_group</span></span>

#### <a name="gateway-server-is-in-a-domain"></a><span data-ttu-id="66895-167">Ağ geçidi sunucu bir etki alanında</span><span class="sxs-lookup"><span data-stu-id="66895-167">Gateway server is in a domain</span></span>

<span data-ttu-id="66895-168">Parametre</span><span class="sxs-lookup"><span data-stu-id="66895-168">Parameter</span></span> | <span data-ttu-id="66895-169">Değer</span><span class="sxs-lookup"><span data-stu-id="66895-169">Value</span></span>
-- | --
<span data-ttu-id="66895-170">ComputerName</span><span class="sxs-lookup"><span data-stu-id="66895-170">ComputerName</span></span> | <span data-ttu-id="66895-171">Ağ geçidi sunucusunun tam adı veya Localhost</span><span class="sxs-lookup"><span data-stu-id="66895-171">Fully qualified name of gateway server, or Localhost</span></span>

#### <a name="gateway-server-is-in-a-workgroup"></a><span data-ttu-id="66895-172">Ağ geçidi sunucusu bir çalışma alanında</span><span class="sxs-lookup"><span data-stu-id="66895-172">Gateway server is in a workgroup</span></span>

<span data-ttu-id="66895-173">Parametre</span><span class="sxs-lookup"><span data-stu-id="66895-173">Parameter</span></span> | <span data-ttu-id="66895-174">Değer</span><span class="sxs-lookup"><span data-stu-id="66895-174">Value</span></span>
-- | --
<span data-ttu-id="66895-175">ComputerName</span><span class="sxs-lookup"><span data-stu-id="66895-175">ComputerName</span></span> | <span data-ttu-id="66895-176">Sunucu adı</span><span class="sxs-lookup"><span data-stu-id="66895-176">Server name</span></span>

### <a name="gateway-credentials"></a><span data-ttu-id="66895-177">Ağ Geçidi kimlik bilgileri</span><span class="sxs-lookup"><span data-stu-id="66895-177">Gateway credentials</span></span>

<span data-ttu-id="66895-178">Bir ağ geçidi sunucusuna, aşağıdakilerden biri olarak biçimlendirilmiş kimlik bilgilerini kullanarak, hedef bilgisayar olarak oturum açın.</span><span class="sxs-lookup"><span data-stu-id="66895-178">Sign in to a gateway server as target computer by using credentials formatted as one of the following.</span></span>

- <span data-ttu-id="66895-179">Sunucu\_adı\\kullanıcı\_adı</span><span class="sxs-lookup"><span data-stu-id="66895-179">Server\_name\\user\_name</span></span>
- <span data-ttu-id="66895-180">Localhost\\kullanıcı\_adı</span><span class="sxs-lookup"><span data-stu-id="66895-180">Localhost\\user\_name</span></span>
- <span data-ttu-id="66895-181">. \\kullanıcı\_adı</span><span class="sxs-lookup"><span data-stu-id="66895-181">.\\user\_name</span></span>

## <a name="a-security-identifier-sid-is-displayed-in-an-authorization-rule"></a><span data-ttu-id="66895-182">Güvenlik tanımlayıcısı (SID) bir yetkilendirme kuralında görüntüleniyor</span><span class="sxs-lookup"><span data-stu-id="66895-182">A security identifier (SID) is displayed in an authorization rule</span></span>

<span data-ttu-id="66895-183">Güvenlik tanımlayıcısı (SID) sözdizimi kullanıcı yerine bir yetkilendirme kuralında görüntülenir\_bilgisayarı adlandırma\_adı.</span><span class="sxs-lookup"><span data-stu-id="66895-183">A security identifier (SID) is displayed in an authorization rule instead of the syntax user\_name/computer\_name.</span></span>

<span data-ttu-id="66895-184">Kural artık geçerli değil veya Active Directory Etki Alanı Hizmetleri sorgusu başarısız olmuş.</span><span class="sxs-lookup"><span data-stu-id="66895-184">Either the rule is no longer valid, or the Active Directory Domain Services query failed.</span></span>
<span data-ttu-id="66895-185">Bir yetkilendirme kuralı genelde, Ağ Geçidi sunucusunun bir zamanda bir çalışma grubunda olsa da, daha sonra bir etki alanına katılmış senaryolarda geçerli değildir</span><span class="sxs-lookup"><span data-stu-id="66895-185">An authorization rule is usually not valid in scenarios where the gateway server was at one time in a workgroup, but was later joined to a domain</span></span>

## <a name="cannot-sign-in-with-rule-as-an-ipv6-address-with-a-domain"></a><span data-ttu-id="66895-186">Kural ile bir etki alanıyla IPv6 adresi olarak oturum açamaz</span><span class="sxs-lookup"><span data-stu-id="66895-186">Cannot sign in with rule as an IPv6 address with a domain</span></span>

<span data-ttu-id="66895-187">Bir etki alanıyla IPv6 adresi olarak yetkilendirme kurallarında belirtilmiş bir hedef bilgisayara oturum açılamıyor.</span><span class="sxs-lookup"><span data-stu-id="66895-187">Cannot sign in to a target computer that has been specified in authorization rules as an IPv6 address with a domain.</span></span>

<span data-ttu-id="66895-188">Yetkilendirme kuralları, bir etki alanı adı biçiminde bir IPv6 adresini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="66895-188">Authorization rules do not support an IPv6 address in form of a domain name.</span></span>

<span data-ttu-id="66895-189">Bir IPv6 adresi kullanarak bir hedef bilgisayar belirtmek için, yetkilendirme kuralında özgün IPv6 adresini kullanın (iki nokta üst üste içeren).</span><span class="sxs-lookup"><span data-stu-id="66895-189">To specify a destination computer by using an IPv6 address, use the original IPv6 address (that contains colons) in the authorization rule.</span></span>
<span data-ttu-id="66895-190">Hem etki alanı hem de sayısal (iki nokta üst üste) olan IPv6 adresleri, yetkilendirme kurallarında değil ancak, Windows PowerShell Web erişimi oturum açma sayfasında hedef bilgisayar adı olarak desteklenir.</span><span class="sxs-lookup"><span data-stu-id="66895-190">Both domain and numerical (with colons) IPv6 addresses are supported as the target computer name on the Windows PowerShell Web Access sign-in page, but not in authorization rules.</span></span> 

<span data-ttu-id="66895-191">IPv6 adresleri hakkında daha fazla bilgi için bkz: [IPv6 nasıl çalışır](https://technet.microsoft.com/library/cc781672(v=ws.10).aspx).</span><span class="sxs-lookup"><span data-stu-id="66895-191">For more information about IPv6 addresses, see [How IPv6 Works](https://technet.microsoft.com/library/cc781672(v=ws.10).aspx).</span></span>

## <a name="see-also"></a><span data-ttu-id="66895-192">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="66895-192">See Also</span></span>

- <span data-ttu-id="66895-193">[Yetkilendirme kuralları ve Windows PowerShell Web Erişimi'nın güvenlik özellikleri](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)</span><span class="sxs-lookup"><span data-stu-id="66895-193">[Authorization Rules and Security Features of Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)</span></span>
- <span data-ttu-id="66895-194">[Web tabanlı Windows PowerShell konsolunu kullanma](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)</span><span class="sxs-lookup"><span data-stu-id="66895-194">[Use the Web-based Windows PowerShell Console](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)</span></span>
- [<span data-ttu-id="66895-195">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="66895-195">about_Remote_Requirements</span></span>](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_remote_requirements)
