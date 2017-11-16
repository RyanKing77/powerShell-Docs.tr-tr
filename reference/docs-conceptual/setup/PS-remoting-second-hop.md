---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: "PowerShell uzaktan iletişim içinde ikinci atlama yapma"
ms.openlocfilehash: f3b8280819e43bd67bd608ffd0ba9484c2bbc26c
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2017
---
# <a name="making-the-second-hop-in-powershell-remoting"></a><span data-ttu-id="e35c4-103">PowerShell uzaktan iletişim içinde ikinci atlama yapma</span><span class="sxs-lookup"><span data-stu-id="e35c4-103">Making the second hop in PowerShell Remoting</span></span>

<span data-ttu-id="e35c4-104">"İkinci atlama sorun" aşağıdaki gibi bir durumla başvuruyor:</span><span class="sxs-lookup"><span data-stu-id="e35c4-104">The "second hop problem" refers to a situation like the following:</span></span>

1. <span data-ttu-id="e35c4-105">Oturum açmış _ServerA_.</span><span class="sxs-lookup"><span data-stu-id="e35c4-105">You are logged in to _ServerA_.</span></span>
2. <span data-ttu-id="e35c4-106">Gelen _ServerA_, bağlanmak için Uzak PowerShell oturumu Başlat _SunucuB_.</span><span class="sxs-lookup"><span data-stu-id="e35c4-106">From _ServerA_, you start a remote PowerShell session to connect to _ServerB_.</span></span>
3. <span data-ttu-id="e35c4-107">Çalıştırdığınız bir komut _SunucuB_ , PowerShell uzaktan iletişimi oturum üzerindeki bir kaynağa erişim girişiminde _SunucuC ise_.</span><span class="sxs-lookup"><span data-stu-id="e35c4-107">A command you run on _ServerB_ via your PowerShell Remoting session attempts to access a resource on _ServerC_.</span></span>
4. <span data-ttu-id="e35c4-108">Kaynağa erişim _SunucuC ise_ engellendi, PowerShell uzak oturum oluşturmak için kullanılan kimlik bilgileri gelen değil geçirildiğinden _SunucuB_ için _SunucuC ise_.</span><span class="sxs-lookup"><span data-stu-id="e35c4-108">Access to the resource on _ServerC_ is denied, because the credentials you used to create the PowerShell Remoting session are not passed from _ServerB_ to _ServerC_.</span></span>

<span data-ttu-id="e35c4-109">Bu sorunu gidermek için birkaç yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="e35c4-109">There are several ways to address this problem.</span></span> <span data-ttu-id="e35c4-110">Bu konuda, birkaç ikinci atlama sorun en popüler çözümleri inceleyeceğiz.</span><span class="sxs-lookup"><span data-stu-id="e35c4-110">In this topic, we'll look at several of the most popular solutions to the second hop problem.</span></span>

## <a name="credssp"></a><span data-ttu-id="e35c4-111">CredSSP</span><span class="sxs-lookup"><span data-stu-id="e35c4-111">CredSSP</span></span>

<span data-ttu-id="e35c4-112">Kullanabileceğiniz [kimlik bilgileri güvenlik desteği sağlayıcısı (CredSSP)](https://msdn.microsoft.com/en-us/library/windows/desktop/bb931352.aspx) kimlik doğrulaması için.</span><span class="sxs-lookup"><span data-stu-id="e35c4-112">You can use the [Credential Security Support Provider (CredSSP)](https://msdn.microsoft.com/en-us/library/windows/desktop/bb931352.aspx) for authentication.</span></span> <span data-ttu-id="e35c4-113">CredSSP kimlik bilgileri uzak sunucuda önbelleğe alır (_SunucuB_), bunu kullanarak kimlik bilgisi hırsızlığı saldırıları kadar açar.</span><span class="sxs-lookup"><span data-stu-id="e35c4-113">CredSSP caches credentials on the remote server (_ServerB_), so using it opens you up to credential theft attacks.</span></span> <span data-ttu-id="e35c4-114">Uzak bilgisayar tehlikede olsa saldırganın kullanıcının kimlik bilgilerine erişebilir.</span><span class="sxs-lookup"><span data-stu-id="e35c4-114">If the remote computer is compromised, the attacker has access to the user's credentials.</span></span> <span data-ttu-id="e35c4-115">CredSSP hem istemci hem de sunucu bilgisayarlarda varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="e35c4-115">CredSSP is disabled by default on both client and server computers.</span></span> <span data-ttu-id="e35c4-116">Yalnızca en güvenilir ortamlarında CredSSP etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e35c4-116">You should enable CredSSP only in the most trusted environments.</span></span> <span data-ttu-id="e35c4-117">Örneğin, bir etki alanı yöneticisi etki alanı denetleyicisi yüksek oranda güvenilir olmadığı için bir etki alanı denetleyicisine bağlanma.</span><span class="sxs-lookup"><span data-stu-id="e35c4-117">For example, a domain administrator connecting to a domain controller because the domain controller is highly trusted.</span></span>

<span data-ttu-id="e35c4-118">PowerShell uzaktan iletişim için CredSSP kullanırken, güvenlik sorunları hakkında daha fazla bilgi için bkz: [yanlışlıkla Sabotaj: CredSSP dikkat](http://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp).</span><span class="sxs-lookup"><span data-stu-id="e35c4-118">For more information about security concerns when using CredSSP for PowerShell Remoting, see [Accidental Sabotage: Beware of CredSSP](http://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp).</span></span>

<span data-ttu-id="e35c4-119">Kimlik bilgisi hırsızlığı saldırıları hakkında daha fazla bilgi için bkz: [Azaltıcı Pass--Hash (PtH) saldırılarını ve diğer kimlik bilgisi hırsızlığını](https://www.microsoft.com/en-us/download/details.aspx?id=36036).</span><span class="sxs-lookup"><span data-stu-id="e35c4-119">For more information about credential theft attacks, see [Mitigating Pass-the-Hash (PtH) Attacks and Other Credential Theft](https://www.microsoft.com/en-us/download/details.aspx?id=36036).</span></span>

<span data-ttu-id="e35c4-120">Etkinleştirmek ve PowerShell uzaktan iletişim için CredSSP kullanma örneği için bkz: [ikinci atlama sorunu çözmek için CredSSP kullanarak](https://blogs.technet.microsoft.com/heyscriptingguy/2012/11/14/enable-powershell-second-hop-functionality-with-credssp/).</span><span class="sxs-lookup"><span data-stu-id="e35c4-120">For an example of how to enable and use CredSSP for PowerShell remoting, see [Using CredSSP to solve the second-hop problem](https://blogs.technet.microsoft.com/heyscriptingguy/2012/11/14/enable-powershell-second-hop-functionality-with-credssp/).</span></span>

### <a name="pros"></a><span data-ttu-id="e35c4-121">Artıları</span><span class="sxs-lookup"><span data-stu-id="e35c4-121">Pros</span></span>

- <span data-ttu-id="e35c4-122">Tüm sunucular için Windows Server 2008 veya sonraki sürümleriyle çalışır.</span><span class="sxs-lookup"><span data-stu-id="e35c4-122">It works for all servers with Windows Server 2008 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="e35c4-123">Eksileri</span><span class="sxs-lookup"><span data-stu-id="e35c4-123">Cons</span></span>

- <span data-ttu-id="e35c4-124">Güvenlik açıkları vardır.</span><span class="sxs-lookup"><span data-stu-id="e35c4-124">Has security vulnerabilities.</span></span>
- <span data-ttu-id="e35c4-125">İstemci ve sunucu rollerinin yapılandırılmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e35c4-125">Requires configuration of both client and server roles.</span></span>

## <a name="kerberos-delegation-unconstrained"></a><span data-ttu-id="e35c4-126">Kerberos temsilcisi (kısıtlanmamış)</span><span class="sxs-lookup"><span data-stu-id="e35c4-126">Kerberos delegation (unconstrained)</span></span>

<span data-ttu-id="e35c4-127">Ayrıca kullanabilir Kısıtlanmamış Kerberos yetkilendirmesi ikinci atlama yapma.</span><span class="sxs-lookup"><span data-stu-id="e35c4-127">You can also used Kerberos unconstrained delegation to make the second hop.</span></span> <span data-ttu-id="e35c4-128">Ancak, bu yöntem atanmış kimlik bilgileri kullanıldığı hiçbir denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="e35c4-128">However, this method provides no control of where delegated credentials are used.</span></span>

><span data-ttu-id="e35c4-129">**Not:** olan Active Directory hesaplarını **Hesap duyarlıdır ve devredilemez** özellik kümesi temsilci seçilemez.</span><span class="sxs-lookup"><span data-stu-id="e35c4-129">**Note:** Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="e35c4-130">Daha fazla bilgi için bkz: [güvenlik odak: 'Hesap duyarlıdır ve devredilemez' ayrıcalıklı hesaplar için analiz](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) ve [Kerberos kimlik doğrulaması araçları ve ayarları](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="e35c4-130">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="e35c4-131">Artıları</span><span class="sxs-lookup"><span data-stu-id="e35c4-131">Pros</span></span>

- <span data-ttu-id="e35c4-132">Hiçbir özel kodlama gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e35c4-132">Requires no special coding.</span></span>

### <a name="cons"></a><span data-ttu-id="e35c4-133">Eksileri</span><span class="sxs-lookup"><span data-stu-id="e35c4-133">Cons</span></span>

- <span data-ttu-id="e35c4-134">İkinci atlama için WinRM desteklemez.</span><span class="sxs-lookup"><span data-stu-id="e35c4-134">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="e35c4-135">Bir güvenlik açığı oluşturma, kimlik bilgilerinin kullanıldığı üzerinde hiçbir denetimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e35c4-135">Provides no control over where credentials are used, creating a security vulnerability.</span></span>

## <a name="kerberos-constrained-delegation"></a><span data-ttu-id="e35c4-136">Kısıtlı Kerberos temsilcisi seçme</span><span class="sxs-lookup"><span data-stu-id="e35c4-136">Kerberos constrained delegation</span></span>

<span data-ttu-id="e35c4-137">Eski Kısıtlı temsilci (değil kaynak tabanlı), ikinci atlama yapmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e35c4-137">You can use legacy constrained delegation (not resource-based) to make the second hop.</span></span> 

><span data-ttu-id="e35c4-138">**Not:** olan Active Directory hesaplarını **Hesap duyarlıdır ve devredilemez** özellik kümesi temsilci seçilemez.</span><span class="sxs-lookup"><span data-stu-id="e35c4-138">**Note:** Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="e35c4-139">Daha fazla bilgi için bkz: [güvenlik odak: 'Hesap duyarlıdır ve devredilemez' ayrıcalıklı hesaplar için analiz](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) ve [Kerberos kimlik doğrulaması araçları ve ayarları](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="e35c4-139">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="e35c4-140">Artıları</span><span class="sxs-lookup"><span data-stu-id="e35c4-140">Pros</span></span>

- <span data-ttu-id="e35c4-141">Hiçbir özel kodlama gerektirir</span><span class="sxs-lookup"><span data-stu-id="e35c4-141">Requires no special coding</span></span>

### <a name="cons"></a><span data-ttu-id="e35c4-142">Eksileri</span><span class="sxs-lookup"><span data-stu-id="e35c4-142">Cons</span></span>

- <span data-ttu-id="e35c4-143">İkinci atlama için WinRM desteklemez.</span><span class="sxs-lookup"><span data-stu-id="e35c4-143">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="e35c4-144">Uzak sunucuya Active Directory nesnesinde yapılandırılmış olması gerekir (_SunucuB_).</span><span class="sxs-lookup"><span data-stu-id="e35c4-144">Must be configured on the Active Directory object of the remote server (_ServerB_).</span></span>
- <span data-ttu-id="e35c4-145">Bir etki alanı sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="e35c4-145">Limited to one domain.</span></span> <span data-ttu-id="e35c4-146">Etki alanları veya ormanlar arası olamaz.</span><span class="sxs-lookup"><span data-stu-id="e35c4-146">Cannot cross domains or forests.</span></span>
- <span data-ttu-id="e35c4-147">Nesneleri ve hizmet asıl adları (SPN) güncelleştirmek için hakları gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e35c4-147">Requires rights to update objects and Service Principal Names (SPNs).</span></span>

## <a name="resource-based-kerberos-constrained-delegation"></a><span data-ttu-id="e35c4-148">Kaynak tabanlı kısıtlı Kerberos temsilcisi seçme</span><span class="sxs-lookup"><span data-stu-id="e35c4-148">Resource-based Kerberos constrained delegation</span></span>

<span data-ttu-id="e35c4-149">Kaynak tabanlı Kerberos kısıtlı temsilcisi (Windows Server 2012'de sunulmuştur), kimlik bilgileri temsilcisi kaynakları bulunduğu sunucu nesnesinde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="e35c4-149">Using resource-based Kerberos constrained delegation (introduced in Windows Server 2012), you configure credential delegation on the server object where resources reside.</span></span>
<span data-ttu-id="e35c4-150">Yukarıda açıklanan ikinci atlama senaryoda yapılandırdığınız _SunucuC ise_ belirtmek için burada kabul edeceği kimlik bilgileri temsilcisi.</span><span class="sxs-lookup"><span data-stu-id="e35c4-150">In the second hop scenario described above, you configure _ServerC_ to specify from where it will accept delegated credentials.</span></span>

><span data-ttu-id="e35c4-151">**Not:** olan Active Directory hesaplarını **Hesap duyarlıdır ve devredilemez** özellik kümesi temsilci seçilemez.</span><span class="sxs-lookup"><span data-stu-id="e35c4-151">**Note:** Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="e35c4-152">Daha fazla bilgi için bkz: [güvenlik odak: 'Hesap duyarlıdır ve devredilemez' ayrıcalıklı hesaplar için analiz](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) ve [Kerberos kimlik doğrulaması araçları ve ayarları](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="e35c4-152">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="e35c4-153">Artıları</span><span class="sxs-lookup"><span data-stu-id="e35c4-153">Pros</span></span>

- <span data-ttu-id="e35c4-154">Kimlik bilgileri depolanmaz.</span><span class="sxs-lookup"><span data-stu-id="e35c4-154">Credentials are not stored.</span></span>
- <span data-ttu-id="e35c4-155">Görece kolay PowerShell cmdlet'leri--gerekli özel kodlama kullanılarak yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="e35c4-155">Relatively easy to configure by using PowerShell cmdlets--no special coding required.</span></span>
- <span data-ttu-id="e35c4-156">Özel etki alanı erişimi gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e35c4-156">No special domain access is required.</span></span>
- <span data-ttu-id="e35c4-157">Etki alanları ve ormanlar arasında çalışır.</span><span class="sxs-lookup"><span data-stu-id="e35c4-157">Works across domains and forests.</span></span>
- <span data-ttu-id="e35c4-158">PowerShell kodu.</span><span class="sxs-lookup"><span data-stu-id="e35c4-158">PowerShell code.</span></span>

### <a name="cons"></a><span data-ttu-id="e35c4-159">Eksileri</span><span class="sxs-lookup"><span data-stu-id="e35c4-159">Cons</span></span>

- <span data-ttu-id="e35c4-160">Windows Server 2012 veya sonraki sürümünü gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e35c4-160">Requires Windows Server 2012 or later.</span></span>
- <span data-ttu-id="e35c4-161">İkinci atlama için WinRM desteklemez.</span><span class="sxs-lookup"><span data-stu-id="e35c4-161">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="e35c4-162">Nesneleri ve hizmet asıl adları (SPN) güncelleştirmek için hakları gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e35c4-162">Requires rights to update objects and Service Principal Names (SPNs).</span></span> 

### <a name="example"></a><span data-ttu-id="e35c4-163">Örnek</span><span class="sxs-lookup"><span data-stu-id="e35c4-163">Example</span></span>

<span data-ttu-id="e35c4-164">Kaynak yapılandırır örnek temel Kısıtlı temsilci PowerShell bakalım _SunucuC ise_ yetki verilen kimlik bilgilerinden izin vermek için bir _SunucuB_.</span><span class="sxs-lookup"><span data-stu-id="e35c4-164">Let's look at a PowerShell example that configures resource based constrained delegation on _ServerC_ to allow delegated credentials from a _ServerB_.</span></span>
<span data-ttu-id="e35c4-165">Bu örnek, tüm sunucular Windows Server 2012 veya sonraki sürümünü, çalıştığını varsayar ve hangi sunuculardan herhangi biri için her bir etki alanı en az bir Windows Server 2012 etki alanı denetleyicisi olduğunu ait.</span><span class="sxs-lookup"><span data-stu-id="e35c4-165">This example assumes that all servers are running Windows Server 2012 or later, and that there is at least one Windows Server 2012 domain controller each domain to which any of the servers belong.</span></span>

<span data-ttu-id="e35c4-166">Kısıtlanmış temsilci yapılandırmadan önce eklemelisiniz `RSAT-AD-PowerShell` Active Directory PowerShell modülünü yüklemek için özellik ve oturumunuza bu modülünü içeri aktarın:</span><span class="sxs-lookup"><span data-stu-id="e35c4-166">Before you can configure constrained delegation, you must add the `RSAT-AD-PowerShell` feature to install the Active Directory PowerShell module, and then import that module into your session:</span></span>

```powershell
PS C:\> Add-WindowsFeature RSAT-AD-PowerShell

PS C:\> Import-Module ActiveDirector
```
<span data-ttu-id="e35c4-167">Birkaç kullanılabilir cmdlet'leri şimdi sahip bir **PrincipalsAllowedToDelegateToAccount** parametre:</span><span class="sxs-lookup"><span data-stu-id="e35c4-167">Several available cmdlets now have a **PrincipalsAllowedToDelegateToAccount** parameter:</span></span>

```powershell
PS C:\> Get-Command -ParameterName PrincipalsAllowedToDelegateToAccount

CommandType Name                 ModuleName     
----------- ----                 ----------     
Cmdlet      New-ADComputer       ActiveDirectory
Cmdlet      New-ADServiceAccount ActiveDirectory
Cmdlet      New-ADUser           ActiveDirectory
Cmdlet      Set-ADComputer       ActiveDirectory
Cmdlet      Set-ADServiceAccount ActiveDirectory
Cmdlet      Set-ADUser           ActiveDirectory
```

<span data-ttu-id="e35c4-168">**PrincipalsAllowedToDelegateToAccount** parametre kümeleri Active Directory nesne özniteliği **msDS-AllowedToActOnBehalfOfOtherIdentity**, bir erişim denetimi listesi (ACL) içeren, hangi hesapların ilişkili hesabın kimlik bilgilerini temsil izniniz olan belirtir (örneğimizde, makine hesabını olacaktır _Server_).</span><span class="sxs-lookup"><span data-stu-id="e35c4-168">The **PrincipalsAllowedToDelegateToAccount** parameter sets the Active Directory object attribute **msDS-AllowedToActOnBehalfOfOtherIdentity**, which contains an access control list (ACL) that specifies which accounts have permission to delegate credentials to the associated account (in our example, it will be the machine account for _Server_).</span></span>

<span data-ttu-id="e35c4-169">Şimdi şimdi sunucuları temsil etmek amacıyla değişkenlerini ayarlamak:</span><span class="sxs-lookup"><span data-stu-id="e35c4-169">Now let's set up the variables we'll use to represent the servers:</span></span>

```powershell
# Set up variables for reuse            
$ServerA = $env:COMPUTERNAME            
$ServerB = Get-ADComputer -Identity ServerB            
$ServerC = Get-ADComputer -Identity ServerC            
```

<span data-ttu-id="e35c4-170">WinRM (ve bu nedenle PowerShell uzaktan iletişimini) varsayılan olarak bilgisayar hesabı olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="e35c4-170">WinRM (and therefore PowerShell remoting) runs as the computer account by default.</span></span> <span data-ttu-id="e35c4-171">Bu bakarak bkz **StartName** özelliği `winrm` hizmeti:</span><span class="sxs-lookup"><span data-stu-id="e35c4-171">You can see this by looking at the **StartName** property of the `winrm` service:</span></span>

```powershell
PS C:\> Get-WmiObject win32_service -filter 'name="winrm"' | Format-List StartName

StartName : NT AUTHORITY\NetworkService
```

<span data-ttu-id="e35c4-172">İçin _SunucuC ise_ PowerShell uzaktan iletişim oturumundan temsilci sağlamak için _SunucuB_, biz ayarlayarak erişim izni verecek **PrincipalsAllowedToDelegateToAccount** parametresini _SunucuC ise_ bilgisayar nesnesi _SunucuB_:</span><span class="sxs-lookup"><span data-stu-id="e35c4-172">For _ServerC_ to allow delegation from a PowerShell remoting session on _ServerB_, we will grant access by setting the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to the computer object of _ServerB_:</span></span>

```powershell
# Grant resource-based Kerberos constrained delegation            
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB            
            
# Check the value of the attribute directly            
$x = Get-ADComputer -Identity $ServerC -Properties msDS-AllowedToActOnBehalfOfOtherIdentity            
$x.'msDS-AllowedToActOnBehalfOfOtherIdentity'.Access            
            
# Check the value of the attribute indirectly            
Get-ADComputer -Identity $ServerC -Properties PrincipalsAllowedToDelegateToAccount
```

<span data-ttu-id="e35c4-173">Kerberos [Anahtar Dağıtım Merkezi (KDC)](https://msdn.microsoft.com/library/windows/desktop/aa378170(v=vs.85).aspx) önbellekleri erişim denemesi (negatif önbelleğini) 15 dakika için reddedildi.</span><span class="sxs-lookup"><span data-stu-id="e35c4-173">The Kerberos [Key Distribution Center (KDC)](https://msdn.microsoft.com/library/windows/desktop/aa378170(v=vs.85).aspx) caches denied access attempts (negative cache) for 15 minutes.</span></span> <span data-ttu-id="e35c4-174">Varsa _SunucuB_ önceden erişmeyi denedi _SunucuC ise_, üzerinde önbelleğini temizlemek gerekir _SunucuB_ göre aşağıdaki komutu çalıştırır:</span><span class="sxs-lookup"><span data-stu-id="e35c4-174">If _ServerB_ has previously attempted to access _ServerC_, you will need to clear the cache on _ServerB_ by invoking the following command:</span></span>

```powershell
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {            
    klist purge -li 0x3e7            
}
```

<span data-ttu-id="e35c4-175">Ayrıca bilgisayarı yeniden başlatın veya önbelleğini temizlemek için en az 15 dakika bekleyin.</span><span class="sxs-lookup"><span data-stu-id="e35c4-175">You could also restart the computer, or wait at least 15 minutes to clear the cache.</span></span>

<span data-ttu-id="e35c4-176">Önbelleği temizledikten sonra koddan başarıyla çalıştırabilirsiniz _ServerA_ aracılığıyla _SunucuB_ için _SunucuC ise_:</span><span class="sxs-lookup"><span data-stu-id="e35c4-176">After clearing the cache, you can successfully run code from _ServerA_ through _ServerB_ to _ServerC_:</span></span>

```powershell
# Capture a credential            
$cred = Get-Credential Contoso\Alice            
            
# Test kerberos double hop            
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {            
    Test-Path \\$($using:ServerC.Name)\C$            
    Get-Process lsass -ComputerName $($using:ServerC.Name)            
    Get-EventLog -LogName System -Newest 3 -ComputerName $($using:ServerC.Name)            
}
```

<span data-ttu-id="e35c4-177">Bu örnekte, `$using` değişkeni yapmak için kullanılan `$ServerC` değişkeni görünür _SunucuB_.</span><span class="sxs-lookup"><span data-stu-id="e35c4-177">In this example, the `$using` variable is used to make the `$ServerC` variable visible to _ServerB_.</span></span> <span data-ttu-id="e35c4-178">Hakkında daha fazla bilgi için `$using` değişken, bkz: [about_Remote_Variables](https://technet.microsoft.com/en-us/library/jj149005.aspx).</span><span class="sxs-lookup"><span data-stu-id="e35c4-178">For more information about the `$using` variable, see [about_Remote_Variables](https://technet.microsoft.com/en-us/library/jj149005.aspx).</span></span>

<span data-ttu-id="e35c4-179">Kimlik bilgileri için temsilci seçme birden çok sunucu izin vermek için _SunucuC ise_, değerini **PrincipalsAllowedToDelegateToAccount** parametresini _SunucuC ise_ bir dizi:</span><span class="sxs-lookup"><span data-stu-id="e35c4-179">To allow multiple servers to delegate credentials to _ServerC_, set the value of the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to an array:</span></span>

```powershell
# Set up variables for each server            
$ServerB1 = Get-ADComputer -Identity ServerB1            
$ServerB2 = Get-ADComputer -Identity ServerB2            
$ServerB3 = Get-ADComputer -Identity ServerB3            
$ServerC  = Get-ADComputer -Identity ServerC            
            
# Grant resource-based Kerberos constrained delegation            
Set-ADComputer -Identity $ServerC `
    -PrincipalsAllowedToDelegateToAccount @($ServerB1,$ServerB2,$ServerB3)
```

<span data-ttu-id="e35c4-180">Etki alanları arasında ikinci atlama yapmak istiyorsanız, tam etki alanı adı (FQDN) etki alanının etki alanı denetleyicisini kendisine eklemek _SunucuB_ ait:</span><span class="sxs-lookup"><span data-stu-id="e35c4-180">If you want to make the second hop across domains, add fully-qualified domain name (FQDN) of the domain controller of the domain to which _ServerB_ belongs:</span></span>

```powershell
# For ServerC in Contoso domain and ServerB in other domain            
$ServerB = Get-ADComputer -Identity ServerB -Server dc1.alpineskihouse.com            
$ServerC = Get-ADComputer -Identity ServerC            
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB
```

<span data-ttu-id="e35c4-181">Kimlik bilgileri SunucuC ise için temsilci seçme olanağı kaldırmak için değerini ayarlayın **PrincipalsAllowedToDelegateToAccount** parametresini _SunucuC ise_ için `$null`:</span><span class="sxs-lookup"><span data-stu-id="e35c4-181">To remove the ability to delegate credentials to ServerC, set the value of the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to `$null`:</span></span>

```powershell
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $null
```

### <a name="information-on-resource-based-kerberos-constrained-delegation"></a><span data-ttu-id="e35c4-182">Kaynak tabanlı kısıtlı Kerberos temsilcisi seçme hakkında bilgi</span><span class="sxs-lookup"><span data-stu-id="e35c4-182">Information on resource-based Kerberos constrained delegation</span></span>

- [<span data-ttu-id="e35c4-183">Kerberos kimlik doğrulamasındaki yenilikler nelerdir?</span><span class="sxs-lookup"><span data-stu-id="e35c4-183">What's New in Kerberos Authentication</span></span>](https://technet.microsoft.com/library/hh831747.aspx)
- [<span data-ttu-id="e35c4-184">Windows Server 2012 hızları Kerberos sorunun nasıl kısıtlı temsilcisi, bölüm 1</span><span class="sxs-lookup"><span data-stu-id="e35c4-184">How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 1</span></span>](http://windowsitpro.com/security/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-1)
- [<span data-ttu-id="e35c4-185">Windows Server 2012 hızları Kerberos sorunun nasıl kısıtlı temsilcisi, bölüm 2</span><span class="sxs-lookup"><span data-stu-id="e35c4-185">How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 2</span></span>](http://windowsitpro.com/security/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-2)
- [<span data-ttu-id="e35c4-186">Anlama Kerberos Kısıtlanmış temsilci seçme için tümleşik Windows kimlik doğrulaması ile Azure Active Directory Uygulama proxy'si dağıtımları</span><span class="sxs-lookup"><span data-stu-id="e35c4-186">Understanding Kerberos Constrained Delegation for Azure Active Directory Application Proxy Deployments with Integrated Windows Authentication</span></span>](http://aka.ms/kcdpaper)
- <span data-ttu-id="e35c4-187">[[MS-ADA2]: Active Directory şema öznitelikleri M2.210 özniteliği msDS-AllowedToActOnBehalfOfOtherIdentity](https://msdn.microsoft.com/en-us/library/hh554126.aspx)</span><span class="sxs-lookup"><span data-stu-id="e35c4-187">[[MS-ADA2]: Active Directory Schema Attributes M2.210 Attribute msDS-AllowedToActOnBehalfOfOtherIdentity](https://msdn.microsoft.com/en-us/library/hh554126.aspx)</span></span>
- <span data-ttu-id="e35c4-188">[[MS-SFU]: Kerberos Protokolü uzantıları: kullanıcı için hizmet ve kısıtlanmış temsil protokolü 1.3.2 S4U2proxy](https://msdn.microsoft.com/en-us/library/cc246079.aspx)</span><span class="sxs-lookup"><span data-stu-id="e35c4-188">[[MS-SFU]: Kerberos Protocol Extensions: Service for User and Constrained Delegation Protocol 1.3.2 S4U2proxy](https://msdn.microsoft.com/en-us/library/cc246079.aspx)</span></span>
- [<span data-ttu-id="e35c4-189">Kaynak tabanlı Kerberos Kısıtlı temsilci</span><span class="sxs-lookup"><span data-stu-id="e35c4-189">Resource Based Kerberos Constrained Delegation</span></span>](https://blog.kloud.com.au/2013/07/11/kerberos-constrained-delegation/)
- [<span data-ttu-id="e35c4-190">Kısıtlanmış temsilci PrincipalsAllowedToDelegateToAccount kullanarak olmadan uzaktan yönetim</span><span class="sxs-lookup"><span data-stu-id="e35c4-190">Remote Administration Without Constrained Delegation Using PrincipalsAllowedToDelegateToAccount</span></span>](https://blogs.msdn.microsoft.com/taylorb/2012/11/06/remote-administration-without-constrained-delegation-using-principalsallowedtodelegatetoaccount/)

## <a name="pssessionconfiguration-using-runas"></a><span data-ttu-id="e35c4-191">Runas komutunu kullanarak PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="e35c4-191">PSSessionConfiguration using RunAs</span></span>

<span data-ttu-id="e35c4-192">Bir oturum yapılandırması oluşturabilirsiniz _SunucuB_ ve kendi **RunAsCredential** parametresi.</span><span class="sxs-lookup"><span data-stu-id="e35c4-192">You can create a session configuration on _ServerB_ and set its **RunAsCredential** parameter.</span></span>

<span data-ttu-id="e35c4-193">İkinci atlama sorunu çözmek için PSSessionConfiguration ve Farklı Çalıştır'ı kullanma hakkında daha fazla bilgi için bkz: [çoklu atlamalı PowerShell uzaktan iletişim için başka bir çözüm](https://blogs.msdn.microsoft.com/sergey_babkins_blog/2015/03/18/another-solution-to-multi-hop-powershell-remoting/).</span><span class="sxs-lookup"><span data-stu-id="e35c4-193">For information about using PSSessionConfiguration and RunAs to solve the second hop problem, see [Another solution to multi-hop PowerShell remoting](https://blogs.msdn.microsoft.com/sergey_babkins_blog/2015/03/18/another-solution-to-multi-hop-powershell-remoting/).</span></span>

### <a name="pros"></a><span data-ttu-id="e35c4-194">Artıları</span><span class="sxs-lookup"><span data-stu-id="e35c4-194">Pros</span></span>

- <span data-ttu-id="e35c4-195">WMF 3.0 veya daha sonra herhangi bir sunucu ile çalışır.</span><span class="sxs-lookup"><span data-stu-id="e35c4-195">Works with any server with WMF 3.0 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="e35c4-196">Eksileri</span><span class="sxs-lookup"><span data-stu-id="e35c4-196">Cons</span></span>

- <span data-ttu-id="e35c4-197">Yapılandırmasını gerektirir **PSSessionConfiguration** ve **RunAs** Ara her sunucuda (_SunucuB_).</span><span class="sxs-lookup"><span data-stu-id="e35c4-197">Requires configuration of **PSSessionConfiguration** and **RunAs** on every intermediate server (_ServerB_).</span></span>
- <span data-ttu-id="e35c4-198">Bir etki alanı kullanırken parola bakım gerektiren **RunAs** hesabı</span><span class="sxs-lookup"><span data-stu-id="e35c4-198">Requires password maintenance when using a domain **RunAs** account</span></span>

## <a name="just-enough-administration-jea"></a><span data-ttu-id="e35c4-199">Tam yetecek kadar Yönetim (JEA)</span><span class="sxs-lookup"><span data-stu-id="e35c4-199">Just Enough Administration (JEA)</span></span>

<span data-ttu-id="e35c4-200">JEA, yönetici bir PowerShell oturumunda çalıştırmak hangi komutları sınırlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="e35c4-200">JEA allows you to restrict what commands an administrator can run during a PowerShell session.</span></span> <span data-ttu-id="e35c4-201">İkinci atlama sorunu çözmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e35c4-201">It can be used to solve the second hop problem.</span></span>

<span data-ttu-id="e35c4-202">JEA hakkında daha fazla bilgi için bkz: [yalnızca yeterince Yönetim](https://docs.microsoft.com/en-us/powershell/jea/overview).</span><span class="sxs-lookup"><span data-stu-id="e35c4-202">For information about JEA, see [Just Enough Administration](https://docs.microsoft.com/en-us/powershell/jea/overview).</span></span>

### <a name="pros"></a><span data-ttu-id="e35c4-203">Artıları</span><span class="sxs-lookup"><span data-stu-id="e35c4-203">Pros</span></span>

- <span data-ttu-id="e35c4-204">Sanal hesap kullanırken hiçbir parola Bakım.</span><span class="sxs-lookup"><span data-stu-id="e35c4-204">No password maintenance when using a virtual account.</span></span>

### <a name="cons"></a><span data-ttu-id="e35c4-205">Eksileri</span><span class="sxs-lookup"><span data-stu-id="e35c4-205">Cons</span></span>

- <span data-ttu-id="e35c4-206">WMF 5.0 veya sonrasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e35c4-206">Requires WMF 5.0 or later.</span></span>
- <span data-ttu-id="e35c4-207">Her ara sunucusu üzerindeki yapılandırmayı gerektirir (_SunucuB_).</span><span class="sxs-lookup"><span data-stu-id="e35c4-207">Requires configuration on every intermediate server (_ServerB_).</span></span>

## <a name="pass-credentials-inside-an-invoke-command-script-block"></a><span data-ttu-id="e35c4-208">Invoke-Command betik bloğu içinde geçişi kimlik bilgileri</span><span class="sxs-lookup"><span data-stu-id="e35c4-208">Pass credentials inside an Invoke-Command script block</span></span>

<span data-ttu-id="e35c4-209">Kimlik bilgileri içinde geçirdiğiniz **ScriptBlock** yapılan bir çağrı parametresinin [Invoke-Command](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/invoke-command) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="e35c4-209">You can pass credentials inside the **ScriptBlock** parameter of a call to the [Invoke-Command](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/invoke-command) cmdlet.</span></span>

### <a name="pros"></a><span data-ttu-id="e35c4-210">Artıları</span><span class="sxs-lookup"><span data-stu-id="e35c4-210">Pros</span></span>

- <span data-ttu-id="e35c4-211">Özel sunucu yapılandırması gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="e35c4-211">Does not require special server configuration.</span></span>
- <span data-ttu-id="e35c4-212">WMF 2.0 veya sonraki sürümünü çalıştıran herhangi bir sunucu üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="e35c4-212">Works on any server running WMF 2.0 or later.</span></span>

## <a name="cons"></a><span data-ttu-id="e35c4-213">Eksileri</span><span class="sxs-lookup"><span data-stu-id="e35c4-213">Cons</span></span>

- <span data-ttu-id="e35c4-214">Garip kod teknik gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e35c4-214">Requires an awkward code technique.</span></span>
- <span data-ttu-id="e35c4-215">WMF 2.0 çalıştıran, bir uzak oturum için bağımsız değişkenleri geçirme farklı bir sözdizimi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e35c4-215">If running WMF 2.0, requires different syntax for passing arguments to a remote session.</span></span>

## <a name="example"></a><span data-ttu-id="e35c4-216">Örnek</span><span class="sxs-lookup"><span data-stu-id="e35c4-216">Example</span></span>

<span data-ttu-id="e35c4-217">Aşağıdaki örnek, kimlik bilgileri geçirmek gösterilmiştir bir **Invoke-Command** betik bloğu:</span><span class="sxs-lookup"><span data-stu-id="e35c4-217">The following example shows how to pass credentials in an **Invoke-Command** script block:</span></span>

```powershell
# This works without delegation, passing fresh creds            
# Note $Using:Cred in nested request            
$cred = Get-Credential Contoso\Administrator            
Invoke-Command -ComputerName ServerB -Credential $cred -ScriptBlock {            
    hostname            
    Invoke-Command -ComputerName ServerC -Credential $Using:cred -ScriptBlock {hostname}            
}
```

## <a name="see-also"></a><span data-ttu-id="e35c4-218">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="e35c4-218">See also</span></span>

[<span data-ttu-id="e35c4-219">PowerShell uzaktan iletişim güvenlik konuları</span><span class="sxs-lookup"><span data-stu-id="e35c4-219">PowerShell Remoting Security Considerations</span></span>](WinRMSecurity.md)








 
