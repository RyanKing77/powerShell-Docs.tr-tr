---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: PowerShell uzaktan iletişim'de ikinci atlamayı yapma
ms.openlocfilehash: 06ca43e3e0524d89ec6f66f6553c4c75072beaf3
ms.sourcegitcommit: 221b7daab7f597f8b2e4864cf9b5d9dda9b9879b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52320712"
---
# <a name="making-the-second-hop-in-powershell-remoting"></a><span data-ttu-id="7d3da-103">PowerShell uzaktan iletişim'de ikinci atlamayı yapma</span><span class="sxs-lookup"><span data-stu-id="7d3da-103">Making the second hop in PowerShell Remoting</span></span>

<span data-ttu-id="7d3da-104">"İkinci atlama sorun" aşağıdaki gibi bir durumla ifade eder:</span><span class="sxs-lookup"><span data-stu-id="7d3da-104">The "second hop problem" refers to a situation like the following:</span></span>

1. <span data-ttu-id="7d3da-105">Oturum açtığınız _ServerA_.</span><span class="sxs-lookup"><span data-stu-id="7d3da-105">You are logged in to _ServerA_.</span></span>
2. <span data-ttu-id="7d3da-106">Gelen _ServerA_, bağlanmak için Uzak PowerShell oturumu Başlat _SunucuB_.</span><span class="sxs-lookup"><span data-stu-id="7d3da-106">From _ServerA_, you start a remote PowerShell session to connect to _ServerB_.</span></span>
3. <span data-ttu-id="7d3da-107">Bir komutu çalıştırdığınız _SunucuB_ , PowerShell uzaktan iletişimini oturum üzerinde bir kaynağa erişmeye çalışır. _SunucuC ise_.</span><span class="sxs-lookup"><span data-stu-id="7d3da-107">A command you run on _ServerB_ via your PowerShell Remoting session attempts to access a resource on _ServerC_.</span></span>
4. <span data-ttu-id="7d3da-108">Şirket kaynağına erişim _SunucuC ise_ reddedildi, PowerShell uzaktan iletişimini oturumu oluşturmak için kullanılan kimlik bilgilerini gelen geçirilen değil çünkü _SunucuB_ için _SunucuC ise_.</span><span class="sxs-lookup"><span data-stu-id="7d3da-108">Access to the resource on _ServerC_ is denied, because the credentials you used to create the PowerShell Remoting session are not passed from _ServerB_ to _ServerC_.</span></span>

<span data-ttu-id="7d3da-109">Bu sorunu çözmek için birkaç yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="7d3da-109">There are several ways to address this problem.</span></span> <span data-ttu-id="7d3da-110">Bu konuda, ikinci atlama sorun en popüler çözümleri birkaçı şu konuları inceleyeceğiz.</span><span class="sxs-lookup"><span data-stu-id="7d3da-110">In this topic, we'll look at several of the most popular solutions to the second hop problem.</span></span>

## <a name="credssp"></a><span data-ttu-id="7d3da-111">CredSSP</span><span class="sxs-lookup"><span data-stu-id="7d3da-111">CredSSP</span></span>

<span data-ttu-id="7d3da-112">Kullanabileceğiniz [kimlik bilgileri güvenlik desteği sağlayıcısı (CredSSP)](https://msdn.microsoft.com/library/windows/desktop/bb931352.aspx) kimlik doğrulaması için.</span><span class="sxs-lookup"><span data-stu-id="7d3da-112">You can use the [Credential Security Support Provider (CredSSP)](https://msdn.microsoft.com/library/windows/desktop/bb931352.aspx) for authentication.</span></span> <span data-ttu-id="7d3da-113">CredSSP kimlik bilgilerini uzak sunucuda önbelleğe alır (_SunucuB_), onu kullanarak kimlik bilgisi hırsızlığı saldırılarını kadar açılmasını sağlayın.</span><span class="sxs-lookup"><span data-stu-id="7d3da-113">CredSSP caches credentials on the remote server (_ServerB_), so using it opens you up to credential theft attacks.</span></span> <span data-ttu-id="7d3da-114">Uzak bilgisayarın tehlikede olursa saldırganın kullanıcının kimlik bilgilerine erişebilir.</span><span class="sxs-lookup"><span data-stu-id="7d3da-114">If the remote computer is compromised, the attacker has access to the user's credentials.</span></span> <span data-ttu-id="7d3da-115">CredSSP hem istemci hem de sunucu bilgisayarlarda varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="7d3da-115">CredSSP is disabled by default on both client and server computers.</span></span> <span data-ttu-id="7d3da-116">Yalnızca en çok güvenilen ortamlarda CredSSP etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="7d3da-116">You should enable CredSSP only in the most trusted environments.</span></span> <span data-ttu-id="7d3da-117">Örneğin, bir etki alanı yöneticisi etki alanı denetleyicisi yüksek oranda güvenilir olmadığı için bir etki alanı denetleyicisine bağlanma.</span><span class="sxs-lookup"><span data-stu-id="7d3da-117">For example, a domain administrator connecting to a domain controller because the domain controller is highly trusted.</span></span>

<span data-ttu-id="7d3da-118">PowerShell uzaktan iletişimi için CredSSP kullanırken, güvenlik sorunları hakkında daha fazla bilgi için bkz. [yanlışlıkla Sabotaj: CredSSP Sıralamaların](https://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp).</span><span class="sxs-lookup"><span data-stu-id="7d3da-118">For more information about security concerns when using CredSSP for PowerShell Remoting, see [Accidental Sabotage: Beware of CredSSP](https://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp).</span></span>

<span data-ttu-id="7d3da-119">Kimlik bilgisi hırsızlığı saldırılarını hakkında daha fazla bilgi için bkz: [Azaltıcı Pass--Hash (PtH) saldırılarını ve diğer kimlik bilgisi Hırsızlıklarını](https://www.microsoft.com/en-us/download/details.aspx?id=36036).</span><span class="sxs-lookup"><span data-stu-id="7d3da-119">For more information about credential theft attacks, see [Mitigating Pass-the-Hash (PtH) Attacks and Other Credential Theft](https://www.microsoft.com/en-us/download/details.aspx?id=36036).</span></span>

<span data-ttu-id="7d3da-120">Etkinleştirmek ve PowerShell uzaktan iletişimi için CredSSP kullanma örneği için bkz: [ikinci atlama sorunu çözmek için CredSSP kullanarak](https://blogs.technet.microsoft.com/heyscriptingguy/2012/11/14/enable-powershell-second-hop-functionality-with-credssp/).</span><span class="sxs-lookup"><span data-stu-id="7d3da-120">For an example of how to enable and use CredSSP for PowerShell remoting, see [Using CredSSP to solve the second-hop problem](https://blogs.technet.microsoft.com/heyscriptingguy/2012/11/14/enable-powershell-second-hop-functionality-with-credssp/).</span></span>

### <a name="pros"></a><span data-ttu-id="7d3da-121">Artıları</span><span class="sxs-lookup"><span data-stu-id="7d3da-121">Pros</span></span>

- <span data-ttu-id="7d3da-122">Tüm sunucular için Windows Server 2008 veya daha sonra çalışır.</span><span class="sxs-lookup"><span data-stu-id="7d3da-122">It works for all servers with Windows Server 2008 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="7d3da-123">Eksileri</span><span class="sxs-lookup"><span data-stu-id="7d3da-123">Cons</span></span>

- <span data-ttu-id="7d3da-124">Güvenlik açıkları vardır.</span><span class="sxs-lookup"><span data-stu-id="7d3da-124">Has security vulnerabilities.</span></span>
- <span data-ttu-id="7d3da-125">İstemci ve sunucu rollerini yapılandırılmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="7d3da-125">Requires configuration of both client and server roles.</span></span>

## <a name="kerberos-delegation-unconstrained"></a><span data-ttu-id="7d3da-126">Kerberos temsilcisi seçme (sınırlandırılmamış)</span><span class="sxs-lookup"><span data-stu-id="7d3da-126">Kerberos delegation (unconstrained)</span></span>

<span data-ttu-id="7d3da-127">Ayrıca kullanabilir Kısıtlanmamış Kerberos yetkilendirmesi ikinci atlamayı yapma.</span><span class="sxs-lookup"><span data-stu-id="7d3da-127">You can also used Kerberos unconstrained delegation to make the second hop.</span></span> <span data-ttu-id="7d3da-128">Ancak, bu yöntem, temsilci seçilen kimlik bilgilerinin kullanıldığı bir denetim yok sağlar.</span><span class="sxs-lookup"><span data-stu-id="7d3da-128">However, this method provides no control of where delegated credentials are used.</span></span>

><span data-ttu-id="7d3da-129">**Not:** olan Active Directory hesaplarını **Hesap duyarlıdır ve devredilemez** özellik kümesi için temsilci olarak seçilemez.</span><span class="sxs-lookup"><span data-stu-id="7d3da-129">**Note:** Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="7d3da-130">Daha fazla bilgi için [güvenlik odak: 'Hesap duyarlıdır ve devredilemez' ayrıcalıklı hesaplar için analiz](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) ve [Kerberos kimlik doğrulaması araçları ve ayarları](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="7d3da-130">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="7d3da-131">Artıları</span><span class="sxs-lookup"><span data-stu-id="7d3da-131">Pros</span></span>

- <span data-ttu-id="7d3da-132">Özel kodlama gerektirir.</span><span class="sxs-lookup"><span data-stu-id="7d3da-132">Requires no special coding.</span></span>

### <a name="cons"></a><span data-ttu-id="7d3da-133">Eksileri</span><span class="sxs-lookup"><span data-stu-id="7d3da-133">Cons</span></span>

- <span data-ttu-id="7d3da-134">İkinci atlama için WinRM desteklemez.</span><span class="sxs-lookup"><span data-stu-id="7d3da-134">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="7d3da-135">Bir güvenlik açığı oluşturarak, kimlik bilgilerinin kullanıldığı hiçbir denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="7d3da-135">Provides no control over where credentials are used, creating a security vulnerability.</span></span>

## <a name="kerberos-constrained-delegation"></a><span data-ttu-id="7d3da-136">Kısıtlı Kerberos temsilcisi seçme</span><span class="sxs-lookup"><span data-stu-id="7d3da-136">Kerberos constrained delegation</span></span>

<span data-ttu-id="7d3da-137">İkinci atlamayı yapma, eski Kısıtlı temsilci (değil kaynak tabanlı) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d3da-137">You can use legacy constrained delegation (not resource-based) to make the second hop.</span></span>

><span data-ttu-id="7d3da-138">**Not:** olan Active Directory hesaplarını **Hesap duyarlıdır ve devredilemez** özellik kümesi için temsilci olarak seçilemez.</span><span class="sxs-lookup"><span data-stu-id="7d3da-138">**Note:** Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="7d3da-139">Daha fazla bilgi için [güvenlik odak: 'Hesap duyarlıdır ve devredilemez' ayrıcalıklı hesaplar için analiz](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) ve [Kerberos kimlik doğrulaması araçları ve ayarları](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="7d3da-139">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="7d3da-140">Artıları</span><span class="sxs-lookup"><span data-stu-id="7d3da-140">Pros</span></span>

- <span data-ttu-id="7d3da-141">Özel kodlama gerektirir</span><span class="sxs-lookup"><span data-stu-id="7d3da-141">Requires no special coding</span></span>

### <a name="cons"></a><span data-ttu-id="7d3da-142">Eksileri</span><span class="sxs-lookup"><span data-stu-id="7d3da-142">Cons</span></span>

- <span data-ttu-id="7d3da-143">İkinci atlama için WinRM desteklemez.</span><span class="sxs-lookup"><span data-stu-id="7d3da-143">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="7d3da-144">Uzak sunucuya Active Directory nesne üzerinde yapılandırılmış olması gerekir (_SunucuB_).</span><span class="sxs-lookup"><span data-stu-id="7d3da-144">Must be configured on the Active Directory object of the remote server (_ServerB_).</span></span>
- <span data-ttu-id="7d3da-145">Bir etki alanı ile sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="7d3da-145">Limited to one domain.</span></span> <span data-ttu-id="7d3da-146">Etki alanları veya ormanlar arası olamaz.</span><span class="sxs-lookup"><span data-stu-id="7d3da-146">Cannot cross domains or forests.</span></span>
- <span data-ttu-id="7d3da-147">Nesneleri ve hizmet asıl adları (SPN) güncelleştirmek için hakları gerekir.</span><span class="sxs-lookup"><span data-stu-id="7d3da-147">Requires rights to update objects and Service Principal Names (SPNs).</span></span>

## <a name="resource-based-kerberos-constrained-delegation"></a><span data-ttu-id="7d3da-148">Kaynak tabanlı kısıtlı Kerberos temsilcisi seçme</span><span class="sxs-lookup"><span data-stu-id="7d3da-148">Resource-based Kerberos constrained delegation</span></span>

<span data-ttu-id="7d3da-149">Kaynak tabanlı Kerberos kısıtlı temsilcisi (Windows Server 2012'de sunulmuştur), kaynakların nerede sunucu nesnesinde kimlik bilgileri temsilcisi yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="7d3da-149">Using resource-based Kerberos constrained delegation (introduced in Windows Server 2012), you configure credential delegation on the server object where resources reside.</span></span>
<span data-ttu-id="7d3da-150">Yukarıda açıklanan ikinci atlama senaryoda yapılandırdığınız _SunucuC ise_ belirtmek için burada kabul edeceği kimlik bilgileri temsilcisi.</span><span class="sxs-lookup"><span data-stu-id="7d3da-150">In the second hop scenario described above, you configure _ServerC_ to specify from where it will accept delegated credentials.</span></span>

><span data-ttu-id="7d3da-151">**Not:** olan Active Directory hesaplarını **Hesap duyarlıdır ve devredilemez** özellik kümesi için temsilci olarak seçilemez.</span><span class="sxs-lookup"><span data-stu-id="7d3da-151">**Note:** Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="7d3da-152">Daha fazla bilgi için [güvenlik odak: 'Hesap duyarlıdır ve devredilemez' ayrıcalıklı hesaplar için analiz](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) ve [Kerberos kimlik doğrulaması araçları ve ayarları](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="7d3da-152">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="7d3da-153">Artıları</span><span class="sxs-lookup"><span data-stu-id="7d3da-153">Pros</span></span>

- <span data-ttu-id="7d3da-154">Kimlik bilgileri depolanmaz.</span><span class="sxs-lookup"><span data-stu-id="7d3da-154">Credentials are not stored.</span></span>
- <span data-ttu-id="7d3da-155">PowerShell cmdlet'leri--özel kodlama gerekmeden kullanarak yapılandırmak daha kolay.</span><span class="sxs-lookup"><span data-stu-id="7d3da-155">Relatively easy to configure by using PowerShell cmdlets--no special coding required.</span></span>
- <span data-ttu-id="7d3da-156">Özel etki alanı erişimi gereklidir.</span><span class="sxs-lookup"><span data-stu-id="7d3da-156">No special domain access is required.</span></span>
- <span data-ttu-id="7d3da-157">Etki alanları ve ormanlar arasında çalışır.</span><span class="sxs-lookup"><span data-stu-id="7d3da-157">Works across domains and forests.</span></span>
- <span data-ttu-id="7d3da-158">PowerShell kodu.</span><span class="sxs-lookup"><span data-stu-id="7d3da-158">PowerShell code.</span></span>

### <a name="cons"></a><span data-ttu-id="7d3da-159">Eksileri</span><span class="sxs-lookup"><span data-stu-id="7d3da-159">Cons</span></span>

- <span data-ttu-id="7d3da-160">Windows Server 2012 veya sonraki sürümünü gerektirir.</span><span class="sxs-lookup"><span data-stu-id="7d3da-160">Requires Windows Server 2012 or later.</span></span>
- <span data-ttu-id="7d3da-161">İkinci atlama için WinRM desteklemez.</span><span class="sxs-lookup"><span data-stu-id="7d3da-161">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="7d3da-162">Nesneleri ve hizmet asıl adları (SPN) güncelleştirmek için hakları gerekir.</span><span class="sxs-lookup"><span data-stu-id="7d3da-162">Requires rights to update objects and Service Principal Names (SPNs).</span></span>

### <a name="example"></a><span data-ttu-id="7d3da-163">Örnek</span><span class="sxs-lookup"><span data-stu-id="7d3da-163">Example</span></span>

<span data-ttu-id="7d3da-164">Kaynak yapılandıran örnek üzerinde kısıtlı temsilci tabanlı bir PowerShell göz atalım _SunucuC ise_ temsilci seçilen kimlik bilgilerinden izin vermek için bir _SunucuB_.</span><span class="sxs-lookup"><span data-stu-id="7d3da-164">Let's look at a PowerShell example that configures resource based constrained delegation on _ServerC_ to allow delegated credentials from a _ServerB_.</span></span>
<span data-ttu-id="7d3da-165">Bu örnek, tüm sunucular Windows Server 2012 veya sonraki sürümünü, çalıştığını varsayar ve hangi sunuculardan herhangi biri için her bir etki alanı en az bir Windows Server 2012 etki alanı denetleyicisi olduğunu ait.</span><span class="sxs-lookup"><span data-stu-id="7d3da-165">This example assumes that all servers are running Windows Server 2012 or later, and that there is at least one Windows Server 2012 domain controller each domain to which any of the servers belong.</span></span>

<span data-ttu-id="7d3da-166">Kısıtlanmış temsilciyi yapılandırmak önce eklemelisiniz `RSAT-AD-PowerShell` Active Directory PowerShell modülü yüklemek için özellik ve daha sonra oturumunuz bu modülü içeri aktarın:</span><span class="sxs-lookup"><span data-stu-id="7d3da-166">Before you can configure constrained delegation, you must add the `RSAT-AD-PowerShell` feature to install the Active Directory PowerShell module, and then import that module into your session:</span></span>

```powershell
PS C:\> Add-WindowsFeature RSAT-AD-PowerShell

PS C:\> Import-Module ActiveDirectory
```
<span data-ttu-id="7d3da-167">Birkaç kullanılabilir cmdlet'lerin artık sahip bir **PrincipalsAllowedToDelegateToAccount** parametresi:</span><span class="sxs-lookup"><span data-stu-id="7d3da-167">Several available cmdlets now have a **PrincipalsAllowedToDelegateToAccount** parameter:</span></span>

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

<span data-ttu-id="7d3da-168">**PrincipalsAllowedToDelegateToAccount** parametre ayarlar Active Directory nesne özniteliği **msDS-AllowedToActOnBehalfOfOtherIdentity**, erişim denetimi listesi (ACL) içeriyor, hangi hesapların ilişkili hesabı kimlik bilgilerini temsil izniniz belirtir (Bizim örneğimizde, makine hesabını olacaktır _sunucu_).</span><span class="sxs-lookup"><span data-stu-id="7d3da-168">The **PrincipalsAllowedToDelegateToAccount** parameter sets the Active Directory object attribute **msDS-AllowedToActOnBehalfOfOtherIdentity**, which contains an access control list (ACL) that specifies which accounts have permission to delegate credentials to the associated account (in our example, it will be the machine account for _Server_).</span></span>

<span data-ttu-id="7d3da-169">Artık sunucuları temsil etmek için kullanacağız değişkenleri ayarlayalım:</span><span class="sxs-lookup"><span data-stu-id="7d3da-169">Now let's set up the variables we'll use to represent the servers:</span></span>

```powershell
# Set up variables for reuse
$ServerA = $env:COMPUTERNAME
$ServerB = Get-ADComputer -Identity ServerB
$ServerC = Get-ADComputer -Identity ServerC
```

<span data-ttu-id="7d3da-170">WinRM (ve bu nedenle PowerShell uzaktan iletişimini) varsayılan olarak bilgisayar hesabı olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="7d3da-170">WinRM (and therefore PowerShell remoting) runs as the computer account by default.</span></span> <span data-ttu-id="7d3da-171">Bu bakarak görebilirsiniz **StartName** özelliği `winrm` hizmeti:</span><span class="sxs-lookup"><span data-stu-id="7d3da-171">You can see this by looking at the **StartName** property of the `winrm` service:</span></span>

```powershell
PS C:\> Get-WmiObject win32_service -filter 'name="winrm"' | Format-List StartName

StartName : NT AUTHORITY\NetworkService
```

<span data-ttu-id="7d3da-172">İçin _SunucuC ise_ PowerShell uzaktan iletişimini oturumundan temsilci izni _SunucuB_, biz ayarlayarak erişim izni verir **PrincipalsAllowedToDelegateToAccount** parametresi _SunucuC ise_ için bilgisayar nesnesine göre _SunucuB_:</span><span class="sxs-lookup"><span data-stu-id="7d3da-172">For _ServerC_ to allow delegation from a PowerShell remoting session on _ServerB_, we will grant access by setting the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to the computer object of _ServerB_:</span></span>

```powershell
# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB

# Check the value of the attribute directly
$x = Get-ADComputer -Identity $ServerC -Properties msDS-AllowedToActOnBehalfOfOtherIdentity
$x.'msDS-AllowedToActOnBehalfOfOtherIdentity'.Access

# Check the value of the attribute indirectly
Get-ADComputer -Identity $ServerC -Properties PrincipalsAllowedToDelegateToAccount
```

<span data-ttu-id="7d3da-173">Kerberos [Anahtar Dağıtım Merkezi (KDC)](https://msdn.microsoft.com/library/windows/desktop/aa378170(v=vs.85).aspx) önbellekler 15 dakika boyunca erişim denemesi (negatif önbellek) reddedildi.</span><span class="sxs-lookup"><span data-stu-id="7d3da-173">The Kerberos [Key Distribution Center (KDC)](https://msdn.microsoft.com/library/windows/desktop/aa378170(v=vs.85).aspx) caches denied access attempts (negative cache) for 15 minutes.</span></span> <span data-ttu-id="7d3da-174">Varsa _SunucuB_ daha önce erişmeyi denedi _SunucuC ise_, üzerinde önbelleği temizlemek ihtiyacınız olacak _SunucuB_ aşağıdaki komutunu çağırarak:</span><span class="sxs-lookup"><span data-stu-id="7d3da-174">If _ServerB_ has previously attempted to access _ServerC_, you will need to clear the cache on _ServerB_ by invoking the following command:</span></span>

```powershell
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    klist purge -li 0x3e7
}
```

<span data-ttu-id="7d3da-175">Ayrıca bilgisayarı yeniden başlatın veya önbelleği temizlemek için en az 15 dakika bekleyin.</span><span class="sxs-lookup"><span data-stu-id="7d3da-175">You could also restart the computer, or wait at least 15 minutes to clear the cache.</span></span>

<span data-ttu-id="7d3da-176">Önbelleği temizledikten sonra koddan başarıyla çalıştırabilirsiniz _ServerA_ aracılığıyla _SunucuB_ için _SunucuC ise_:</span><span class="sxs-lookup"><span data-stu-id="7d3da-176">After clearing the cache, you can successfully run code from _ServerA_ through _ServerB_ to _ServerC_:</span></span>

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

<span data-ttu-id="7d3da-177">Bu örnekte, `$using` değişkeni sağlamak için kullanılan `$ServerC` değişken görünür _SunucuB_.</span><span class="sxs-lookup"><span data-stu-id="7d3da-177">In this example, the `$using` variable is used to make the `$ServerC` variable visible to _ServerB_.</span></span> <span data-ttu-id="7d3da-178">Hakkında daha fazla bilgi için `$using` değişken, bkz: [about_Remote_Variables](https://technet.microsoft.com/library/jj149005.aspx).</span><span class="sxs-lookup"><span data-stu-id="7d3da-178">For more information about the `$using` variable, see [about_Remote_Variables](https://technet.microsoft.com/library/jj149005.aspx).</span></span>

<span data-ttu-id="7d3da-179">Kimlik bilgileri için temsilci seçmek birden çok sunucu izin vermek için _SunucuC ise_, değerini **PrincipalsAllowedToDelegateToAccount** parametresi _SunucuC ise_ bir dizi:</span><span class="sxs-lookup"><span data-stu-id="7d3da-179">To allow multiple servers to delegate credentials to _ServerC_, set the value of the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to an array:</span></span>

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

<span data-ttu-id="7d3da-180">Etki alanları arasında ikinci atlama yapmak istiyorsanız, tam etki alanı adı (FQDN) etki alanının etki alanı denetleyicisini kendisine ekleme _SunucuB_ aittir:</span><span class="sxs-lookup"><span data-stu-id="7d3da-180">If you want to make the second hop across domains, add fully-qualified domain name (FQDN) of the domain controller of the domain to which _ServerB_ belongs:</span></span>

```powershell
# For ServerC in Contoso domain and ServerB in other domain
$ServerB = Get-ADComputer -Identity ServerB -Server dc1.alpineskihouse.com
$ServerC = Get-ADComputer -Identity ServerC
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB
```

<span data-ttu-id="7d3da-181">Temsilci SunucuC ise kimlik özelliği kaldırmak için değerini ayarlamak **PrincipalsAllowedToDelegateToAccount** parametresi _SunucuC ise_ için `$null`:</span><span class="sxs-lookup"><span data-stu-id="7d3da-181">To remove the ability to delegate credentials to ServerC, set the value of the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to `$null`:</span></span>

```powershell
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $null
```

### <a name="information-on-resource-based-kerberos-constrained-delegation"></a><span data-ttu-id="7d3da-182">Kaynak tabanlı kısıtlı Kerberos temsilcisi seçme hakkında bilgi</span><span class="sxs-lookup"><span data-stu-id="7d3da-182">Information on resource-based Kerberos constrained delegation</span></span>

- [<span data-ttu-id="7d3da-183">Kerberos kimlik doğrulamasındaki yenilikler</span><span class="sxs-lookup"><span data-stu-id="7d3da-183">What's New in Kerberos Authentication</span></span>](https://technet.microsoft.com/library/hh831747.aspx)
- [<span data-ttu-id="7d3da-184">Nasıl Windows Server 2012 hızları kolaylaştırın, Kerberos kısıtlı temsilcisi, bölüm 1</span><span class="sxs-lookup"><span data-stu-id="7d3da-184">How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 1</span></span>](https://windowsitpro.com/security/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-1)
- [<span data-ttu-id="7d3da-185">Nasıl Windows Server 2012 hızları kolaylaştırın, Kerberos kısıtlı temsilcisi, bölüm 2</span><span class="sxs-lookup"><span data-stu-id="7d3da-185">How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 2</span></span>](https://windowsitpro.com/security/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-2)
- [<span data-ttu-id="7d3da-186">Anlama Kerberos kısıtlı temsilcisi tümleşik Windows kimlik doğrulaması ile Azure Active Directory Uygulama Ara sunucusu dağıtımları için</span><span class="sxs-lookup"><span data-stu-id="7d3da-186">Understanding Kerberos Constrained Delegation for Azure Active Directory Application Proxy Deployments with Integrated Windows Authentication</span></span>](https://aka.ms/kcdpaper)
- <span data-ttu-id="7d3da-187">[[MS-ADA2]: Active Directory şema öznitelikleri M2.210 özniteliği msDS-AllowedToActOnBehalfOfOtherIdentity](https://msdn.microsoft.com/library/hh554126.aspx)</span><span class="sxs-lookup"><span data-stu-id="7d3da-187">[[MS-ADA2]: Active Directory Schema Attributes M2.210 Attribute msDS-AllowedToActOnBehalfOfOtherIdentity](https://msdn.microsoft.com/library/hh554126.aspx)</span></span>
- <span data-ttu-id="7d3da-188">[[MS-SFU]: Kerberos Protokolü uzantıları: kullanıcı için hizmet ve kısıtlanmış temsil protokolü 1.3.2 S4U2proxy](https://msdn.microsoft.com/library/cc246079.aspx)</span><span class="sxs-lookup"><span data-stu-id="7d3da-188">[[MS-SFU]: Kerberos Protocol Extensions: Service for User and Constrained Delegation Protocol 1.3.2 S4U2proxy](https://msdn.microsoft.com/library/cc246079.aspx)</span></span>
- [<span data-ttu-id="7d3da-189">Kaynak tabanlı Kerberos kısıtlı temsil</span><span class="sxs-lookup"><span data-stu-id="7d3da-189">Resource Based Kerberos Constrained Delegation</span></span>](https://blog.kloud.com.au/2013/07/11/kerberos-constrained-delegation/)
- [<span data-ttu-id="7d3da-190">Kısıtlanmış temsilci kullanarak PrincipalsAllowedToDelegateToAccount olmadan uzaktan yönetim</span><span class="sxs-lookup"><span data-stu-id="7d3da-190">Remote Administration Without Constrained Delegation Using PrincipalsAllowedToDelegateToAccount</span></span>](https://blogs.msdn.microsoft.com/taylorb/2012/11/06/remote-administration-without-constrained-delegation-using-principalsallowedtodelegatetoaccount/)

## <a name="pssessionconfiguration-using-runas"></a><span data-ttu-id="7d3da-191">Farklı Çalıştır'ı kullanarak PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="7d3da-191">PSSessionConfiguration using RunAs</span></span>

<span data-ttu-id="7d3da-192">Bir oturum yapılandırması oluşturabilirsiniz _SunucuB_ ve kendi **RunAsCredential** parametresi.</span><span class="sxs-lookup"><span data-stu-id="7d3da-192">You can create a session configuration on _ServerB_ and set its **RunAsCredential** parameter.</span></span>

<span data-ttu-id="7d3da-193">İkinci atlama sorunu çözmek için PSSessionConfiguration ve Farklı Çalıştır'ı kullanma hakkında daha fazla bilgi için bkz: [çoklu atlamalı PowerShell uzaktan iletişim için başka bir çözüm](https://blogs.msdn.microsoft.com/sergey_babkins_blog/2015/03/18/another-solution-to-multi-hop-powershell-remoting/).</span><span class="sxs-lookup"><span data-stu-id="7d3da-193">For information about using PSSessionConfiguration and RunAs to solve the second hop problem, see [Another solution to multi-hop PowerShell remoting](https://blogs.msdn.microsoft.com/sergey_babkins_blog/2015/03/18/another-solution-to-multi-hop-powershell-remoting/).</span></span>

### <a name="pros"></a><span data-ttu-id="7d3da-194">Artıları</span><span class="sxs-lookup"><span data-stu-id="7d3da-194">Pros</span></span>

- <span data-ttu-id="7d3da-195">Herhangi bir sunucu WMF 3.0 veya üstü ile çalışır.</span><span class="sxs-lookup"><span data-stu-id="7d3da-195">Works with any server with WMF 3.0 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="7d3da-196">Eksileri</span><span class="sxs-lookup"><span data-stu-id="7d3da-196">Cons</span></span>

- <span data-ttu-id="7d3da-197">Yapılandırılmasını gerektirir **PSSessionConfiguration** ve **RunAs** Ara her sunucuda (_SunucuB_).</span><span class="sxs-lookup"><span data-stu-id="7d3da-197">Requires configuration of **PSSessionConfiguration** and **RunAs** on every intermediate server (_ServerB_).</span></span>
- <span data-ttu-id="7d3da-198">Bir etki alanı kullanırken parola bakıma gerek duyacağını **RunAs** hesabı</span><span class="sxs-lookup"><span data-stu-id="7d3da-198">Requires password maintenance when using a domain **RunAs** account</span></span>

## <a name="just-enough-administration-jea"></a><span data-ttu-id="7d3da-199">Yeterli Yönetim (JEA)</span><span class="sxs-lookup"><span data-stu-id="7d3da-199">Just Enough Administration (JEA)</span></span>

<span data-ttu-id="7d3da-200">JEA, yönetici bir PowerShell oturumunda çalıştırmak hangi komutları sınırlamanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="7d3da-200">JEA allows you to restrict what commands an administrator can run during a PowerShell session.</span></span> <span data-ttu-id="7d3da-201">İkinci atlama sorunu çözmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7d3da-201">It can be used to solve the second hop problem.</span></span>

<span data-ttu-id="7d3da-202">JEA hakkında daha fazla bilgi için bkz. [yeterli yönetim](https://docs.microsoft.com/powershell/jea/overview).</span><span class="sxs-lookup"><span data-stu-id="7d3da-202">For information about JEA, see [Just Enough Administration](https://docs.microsoft.com/powershell/jea/overview).</span></span>

### <a name="pros"></a><span data-ttu-id="7d3da-203">Artıları</span><span class="sxs-lookup"><span data-stu-id="7d3da-203">Pros</span></span>

- <span data-ttu-id="7d3da-204">Sanal bir hesap kullanırken hiçbir parola Bakım.</span><span class="sxs-lookup"><span data-stu-id="7d3da-204">No password maintenance when using a virtual account.</span></span>

### <a name="cons"></a><span data-ttu-id="7d3da-205">Eksileri</span><span class="sxs-lookup"><span data-stu-id="7d3da-205">Cons</span></span>

- <span data-ttu-id="7d3da-206">WMF 5.0 veya sonraki sürümünü gerektirir.</span><span class="sxs-lookup"><span data-stu-id="7d3da-206">Requires WMF 5.0 or later.</span></span>
- <span data-ttu-id="7d3da-207">Her bir ara sunucu yapılandırma gerektirir (_SunucuB_).</span><span class="sxs-lookup"><span data-stu-id="7d3da-207">Requires configuration on every intermediate server (_ServerB_).</span></span>

## <a name="pass-credentials-inside-an-invoke-command-script-block"></a><span data-ttu-id="7d3da-208">Invoke-Command betik bloğunun Pass kimlik bilgileri</span><span class="sxs-lookup"><span data-stu-id="7d3da-208">Pass credentials inside an Invoke-Command script block</span></span>

<span data-ttu-id="7d3da-209">Kimlik bilgileri içine geçirebilirsiniz **ScriptBlock** çağrısına parametre [Invoke-Command](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/invoke-command) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="7d3da-209">You can pass credentials inside the **ScriptBlock** parameter of a call to the [Invoke-Command](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/invoke-command) cmdlet.</span></span>

### <a name="pros"></a><span data-ttu-id="7d3da-210">Artıları</span><span class="sxs-lookup"><span data-stu-id="7d3da-210">Pros</span></span>

- <span data-ttu-id="7d3da-211">Özel sunucu yapılandırması gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="7d3da-211">Does not require special server configuration.</span></span>
- <span data-ttu-id="7d3da-212">WMF 2.0 veya sonraki sürümünü çalıştıran herhangi bir sunucu üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="7d3da-212">Works on any server running WMF 2.0 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="7d3da-213">Eksileri</span><span class="sxs-lookup"><span data-stu-id="7d3da-213">Cons</span></span>

- <span data-ttu-id="7d3da-214">Garip kod teknik gerektirir.</span><span class="sxs-lookup"><span data-stu-id="7d3da-214">Requires an awkward code technique.</span></span>
- <span data-ttu-id="7d3da-215">WMF 2.0 çalıştırılıyorsa, uzak oturumu bağımsız değişkenleri geçirmek için farklı bir sözdizimi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="7d3da-215">If running WMF 2.0, requires different syntax for passing arguments to a remote session.</span></span>

### <a name="example"></a><span data-ttu-id="7d3da-216">Örnek</span><span class="sxs-lookup"><span data-stu-id="7d3da-216">Example</span></span>

<span data-ttu-id="7d3da-217">Aşağıdaki örnek, kimlik bilgilerini geçirmek nasıl gösterir bir **Invoke-Command** betik bloğu:</span><span class="sxs-lookup"><span data-stu-id="7d3da-217">The following example shows how to pass credentials in an **Invoke-Command** script block:</span></span>

```powershell
# This works without delegation, passing fresh creds
# Note $Using:Cred in nested request
$cred = Get-Credential Contoso\Administrator
Invoke-Command -ComputerName ServerB -Credential $cred -ScriptBlock {
    hostname
    Invoke-Command -ComputerName ServerC -Credential $Using:cred -ScriptBlock {hostname}
}
```

## <a name="see-also"></a><span data-ttu-id="7d3da-218">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="7d3da-218">See also</span></span>

[<span data-ttu-id="7d3da-219">PowerShell Uzaktan İletişim Güvenlik Konuları</span><span class="sxs-lookup"><span data-stu-id="7d3da-219">PowerShell Remoting Security Considerations</span></span>](WinRMSecurity.md)