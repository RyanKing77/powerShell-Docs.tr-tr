---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: PowerShell Uzaktan İletişim’de ikinci atlamayı yapma
ms.openlocfilehash: 1b6e5ad53346324adc7be2d013e154c8600afa4f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086349"
---
# <a name="making-the-second-hop-in-powershell-remoting"></a><span data-ttu-id="e78dd-103">PowerShell Uzaktan İletişim’de ikinci atlamayı yapma</span><span class="sxs-lookup"><span data-stu-id="e78dd-103">Making the second hop in PowerShell Remoting</span></span>

<span data-ttu-id="e78dd-104">"İkinci atlama sorun" aşağıdaki gibi bir durumla ifade eder:</span><span class="sxs-lookup"><span data-stu-id="e78dd-104">The "second hop problem" refers to a situation like the following:</span></span>

1. <span data-ttu-id="e78dd-105">Oturum açtığınız _ServerA_.</span><span class="sxs-lookup"><span data-stu-id="e78dd-105">You are logged in to _ServerA_.</span></span>
2. <span data-ttu-id="e78dd-106">Gelen _ServerA_, bağlanmak için Uzak PowerShell oturumu Başlat _SunucuB_.</span><span class="sxs-lookup"><span data-stu-id="e78dd-106">From _ServerA_, you start a remote PowerShell session to connect to _ServerB_.</span></span>
3. <span data-ttu-id="e78dd-107">Bir komutu çalıştırdığınız _SunucuB_ , PowerShell uzaktan iletişimini oturum üzerinde bir kaynağa erişmeye çalışır. _SunucuC ise_.</span><span class="sxs-lookup"><span data-stu-id="e78dd-107">A command you run on _ServerB_ via your PowerShell Remoting session attempts to access a resource on _ServerC_.</span></span>
4. <span data-ttu-id="e78dd-108">Şirket kaynağına erişim _SunucuC ise_ reddedildi, PowerShell uzaktan iletişimini oturumu oluşturmak için kullanılan kimlik bilgilerini gelen geçirilen değil çünkü _SunucuB_ için _SunucuC ise_.</span><span class="sxs-lookup"><span data-stu-id="e78dd-108">Access to the resource on _ServerC_ is denied, because the credentials you used to create the PowerShell Remoting session are not passed from _ServerB_ to _ServerC_.</span></span>

<span data-ttu-id="e78dd-109">Bu sorunu çözmek için birkaç yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="e78dd-109">There are several ways to address this problem.</span></span> <span data-ttu-id="e78dd-110">Bu konuda, ikinci atlama sorun en popüler çözümleri birkaçı şu konuları inceleyeceğiz.</span><span class="sxs-lookup"><span data-stu-id="e78dd-110">In this topic, we'll look at several of the most popular solutions to the second hop problem.</span></span>

## <a name="credssp"></a><span data-ttu-id="e78dd-111">CredSSP</span><span class="sxs-lookup"><span data-stu-id="e78dd-111">CredSSP</span></span>

<span data-ttu-id="e78dd-112">Kullanabileceğiniz [kimlik bilgileri güvenlik desteği sağlayıcısı (CredSSP)](https://msdn.microsoft.com/library/windows/desktop/bb931352.aspx) kimlik doğrulaması için.</span><span class="sxs-lookup"><span data-stu-id="e78dd-112">You can use the [Credential Security Support Provider (CredSSP)](https://msdn.microsoft.com/library/windows/desktop/bb931352.aspx) for authentication.</span></span> <span data-ttu-id="e78dd-113">CredSSP kimlik bilgilerini uzak sunucuda önbelleğe alır (_SunucuB_), onu kullanarak kimlik bilgisi hırsızlığı saldırılarını kadar açılmasını sağlayın.</span><span class="sxs-lookup"><span data-stu-id="e78dd-113">CredSSP caches credentials on the remote server (_ServerB_), so using it opens you up to credential theft attacks.</span></span> <span data-ttu-id="e78dd-114">Uzak bilgisayarın tehlikede olursa saldırganın kullanıcının kimlik bilgilerine erişebilir.</span><span class="sxs-lookup"><span data-stu-id="e78dd-114">If the remote computer is compromised, the attacker has access to the user's credentials.</span></span> <span data-ttu-id="e78dd-115">CredSSP hem istemci hem de sunucu bilgisayarlarda varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="e78dd-115">CredSSP is disabled by default on both client and server computers.</span></span> <span data-ttu-id="e78dd-116">Yalnızca en çok güvenilen ortamlarda CredSSP etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e78dd-116">You should enable CredSSP only in the most trusted environments.</span></span> <span data-ttu-id="e78dd-117">Örneğin, bir etki alanı yöneticisi etki alanı denetleyicisi yüksek oranda güvenilir olmadığı için bir etki alanı denetleyicisine bağlanma.</span><span class="sxs-lookup"><span data-stu-id="e78dd-117">For example, a domain administrator connecting to a domain controller because the domain controller is highly trusted.</span></span>

<span data-ttu-id="e78dd-118">PowerShell uzaktan iletişimi için CredSSP kullanırken, güvenlik sorunları hakkında daha fazla bilgi için bkz. [yanlışlıkla Sabotaj: CredSSP dikkat](https://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp).</span><span class="sxs-lookup"><span data-stu-id="e78dd-118">For more information about security concerns when using CredSSP for PowerShell Remoting, see [Accidental Sabotage: Beware of CredSSP](https://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp).</span></span>

<span data-ttu-id="e78dd-119">Kimlik bilgisi hırsızlığı saldırılarını hakkında daha fazla bilgi için bkz: [Azaltıcı Pass--Hash (PtH) saldırılarını ve diğer kimlik bilgisi Hırsızlıklarını](https://www.microsoft.com/en-us/download/details.aspx?id=36036).</span><span class="sxs-lookup"><span data-stu-id="e78dd-119">For more information about credential theft attacks, see [Mitigating Pass-the-Hash (PtH) Attacks and Other Credential Theft](https://www.microsoft.com/en-us/download/details.aspx?id=36036).</span></span>

<span data-ttu-id="e78dd-120">Etkinleştirmek ve PowerShell uzaktan iletişimi için CredSSP kullanma örneği için bkz: [ikinci atlama sorunu çözmek için CredSSP kullanarak](https://blogs.technet.microsoft.com/heyscriptingguy/2012/11/14/enable-powershell-second-hop-functionality-with-credssp/).</span><span class="sxs-lookup"><span data-stu-id="e78dd-120">For an example of how to enable and use CredSSP for PowerShell remoting, see [Using CredSSP to solve the second-hop problem](https://blogs.technet.microsoft.com/heyscriptingguy/2012/11/14/enable-powershell-second-hop-functionality-with-credssp/).</span></span>

### <a name="pros"></a><span data-ttu-id="e78dd-121">Uzmanları</span><span class="sxs-lookup"><span data-stu-id="e78dd-121">Pros</span></span>

- <span data-ttu-id="e78dd-122">Tüm sunucular için Windows Server 2008 veya daha sonra çalışır.</span><span class="sxs-lookup"><span data-stu-id="e78dd-122">It works for all servers with Windows Server 2008 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="e78dd-123">Simgeler</span><span class="sxs-lookup"><span data-stu-id="e78dd-123">Cons</span></span>

- <span data-ttu-id="e78dd-124">Güvenlik açıkları vardır.</span><span class="sxs-lookup"><span data-stu-id="e78dd-124">Has security vulnerabilities.</span></span>
- <span data-ttu-id="e78dd-125">İstemci ve sunucu rollerini yapılandırılmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e78dd-125">Requires configuration of both client and server roles.</span></span>

## <a name="kerberos-delegation-unconstrained"></a><span data-ttu-id="e78dd-126">Kerberos temsilcisi seçme (sınırlandırılmamış)</span><span class="sxs-lookup"><span data-stu-id="e78dd-126">Kerberos delegation (unconstrained)</span></span>

<span data-ttu-id="e78dd-127">Ayrıca kullanabilir Kısıtlanmamış Kerberos yetkilendirmesi ikinci atlamayı yapma.</span><span class="sxs-lookup"><span data-stu-id="e78dd-127">You can also used Kerberos unconstrained delegation to make the second hop.</span></span> <span data-ttu-id="e78dd-128">Ancak, bu yöntem, temsilci seçilen kimlik bilgilerinin kullanıldığı bir denetim yok sağlar.</span><span class="sxs-lookup"><span data-stu-id="e78dd-128">However, this method provides no control of where delegated credentials are used.</span></span>

><span data-ttu-id="e78dd-129">**Not:** Olan active Directory hesaplarını **Hesap duyarlıdır ve devredilemez** özellik kümesi için temsilci olarak seçilemez.</span><span class="sxs-lookup"><span data-stu-id="e78dd-129">**Note:** Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="e78dd-130">Daha fazla bilgi için [güvenlik odak: 'Hesap duyarlıdır ve devredilemez' ayrıcalıklı hesaplar için analiz](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) ve [Kerberos kimlik doğrulaması araçları ve ayarları](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="e78dd-130">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="e78dd-131">Uzmanları</span><span class="sxs-lookup"><span data-stu-id="e78dd-131">Pros</span></span>

- <span data-ttu-id="e78dd-132">Özel kodlama gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e78dd-132">Requires no special coding.</span></span>

### <a name="cons"></a><span data-ttu-id="e78dd-133">Simgeler</span><span class="sxs-lookup"><span data-stu-id="e78dd-133">Cons</span></span>

- <span data-ttu-id="e78dd-134">İkinci atlama için WinRM desteklemez.</span><span class="sxs-lookup"><span data-stu-id="e78dd-134">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="e78dd-135">Bir güvenlik açığı oluşturarak, kimlik bilgilerinin kullanıldığı hiçbir denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="e78dd-135">Provides no control over where credentials are used, creating a security vulnerability.</span></span>

## <a name="kerberos-constrained-delegation"></a><span data-ttu-id="e78dd-136">Kısıtlı Kerberos temsilcisi seçme</span><span class="sxs-lookup"><span data-stu-id="e78dd-136">Kerberos constrained delegation</span></span>

<span data-ttu-id="e78dd-137">İkinci atlamayı yapma, eski Kısıtlı temsilci (değil kaynak tabanlı) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e78dd-137">You can use legacy constrained delegation (not resource-based) to make the second hop.</span></span> <span data-ttu-id="e78dd-138">"Herhangi bir kimlik doğrulama protokolünü kullan" seçeneği ile kısıtlı Kerberos temsilcisi yapılandırın protokol geçişi izin vermek için.</span><span class="sxs-lookup"><span data-stu-id="e78dd-138">Configure Kerberos constrained delegation with the option "Use any authentication protocol" to allow protocol transition.</span></span>

> [!NOTE]
> <span data-ttu-id="e78dd-139">Olan active Directory hesaplarını **Hesap duyarlıdır ve devredilemez** özellik kümesi için temsilci olarak seçilemez.</span><span class="sxs-lookup"><span data-stu-id="e78dd-139">Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="e78dd-140">Daha fazla bilgi için [güvenlik odak: 'Hesap duyarlıdır ve devredilemez' ayrıcalıklı hesaplar için analiz](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) ve [Kerberos kimlik doğrulaması araçları ve ayarları](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="e78dd-140">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="e78dd-141">Uzmanları</span><span class="sxs-lookup"><span data-stu-id="e78dd-141">Pros</span></span>

- <span data-ttu-id="e78dd-142">Özel kodlama gerektirir</span><span class="sxs-lookup"><span data-stu-id="e78dd-142">Requires no special coding</span></span>

### <a name="cons"></a><span data-ttu-id="e78dd-143">Simgeler</span><span class="sxs-lookup"><span data-stu-id="e78dd-143">Cons</span></span>

- <span data-ttu-id="e78dd-144">İkinci atlama için WinRM desteklemez.</span><span class="sxs-lookup"><span data-stu-id="e78dd-144">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="e78dd-145">Uzak sunucuya Active Directory nesne üzerinde yapılandırılmış olması gerekir (_SunucuB_).</span><span class="sxs-lookup"><span data-stu-id="e78dd-145">Must be configured on the Active Directory object of the remote server (_ServerB_).</span></span>
- <span data-ttu-id="e78dd-146">Bir etki alanı ile sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="e78dd-146">Limited to one domain.</span></span> <span data-ttu-id="e78dd-147">Etki alanları veya ormanlar arası olamaz.</span><span class="sxs-lookup"><span data-stu-id="e78dd-147">Cannot cross domains or forests.</span></span>
- <span data-ttu-id="e78dd-148">Nesneleri ve hizmet asıl adları (SPN) güncelleştirmek için hakları gerekir.</span><span class="sxs-lookup"><span data-stu-id="e78dd-148">Requires rights to update objects and Service Principal Names (SPNs).</span></span>

## <a name="resource-based-kerberos-constrained-delegation"></a><span data-ttu-id="e78dd-149">Kaynak tabanlı kısıtlı Kerberos temsilcisi seçme</span><span class="sxs-lookup"><span data-stu-id="e78dd-149">Resource-based Kerberos constrained delegation</span></span>

<span data-ttu-id="e78dd-150">Kaynak tabanlı Kerberos kısıtlı temsilcisi (Windows Server 2012'de sunulmuştur), kaynakların nerede sunucu nesnesinde kimlik bilgileri temsilcisi yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="e78dd-150">Using resource-based Kerberos constrained delegation (introduced in Windows Server 2012), you configure credential delegation on the server object where resources reside.</span></span>
<span data-ttu-id="e78dd-151">Yukarıda açıklanan ikinci atlama senaryoda yapılandırdığınız _SunucuC ise_ belirtmek için burada kabul edeceği kimlik bilgileri temsilcisi.</span><span class="sxs-lookup"><span data-stu-id="e78dd-151">In the second hop scenario described above, you configure _ServerC_ to specify from where it will accept delegated credentials.</span></span>

><span data-ttu-id="e78dd-152">**Not:** Olan active Directory hesaplarını **Hesap duyarlıdır ve devredilemez** özellik kümesi için temsilci olarak seçilemez.</span><span class="sxs-lookup"><span data-stu-id="e78dd-152">**Note:** Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="e78dd-153">Daha fazla bilgi için [güvenlik odak: 'Hesap duyarlıdır ve devredilemez' ayrıcalıklı hesaplar için analiz](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) ve [Kerberos kimlik doğrulaması araçları ve ayarları](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="e78dd-153">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="e78dd-154">Uzmanları</span><span class="sxs-lookup"><span data-stu-id="e78dd-154">Pros</span></span>

- <span data-ttu-id="e78dd-155">Kimlik bilgileri depolanmaz.</span><span class="sxs-lookup"><span data-stu-id="e78dd-155">Credentials are not stored.</span></span>
- <span data-ttu-id="e78dd-156">PowerShell cmdlet'leri--özel kodlama gerekmeden kullanarak yapılandırmak daha kolay.</span><span class="sxs-lookup"><span data-stu-id="e78dd-156">Relatively easy to configure by using PowerShell cmdlets--no special coding required.</span></span>
- <span data-ttu-id="e78dd-157">Özel etki alanı erişimi gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e78dd-157">No special domain access is required.</span></span>
- <span data-ttu-id="e78dd-158">Etki alanları ve ormanlar arasında çalışır.</span><span class="sxs-lookup"><span data-stu-id="e78dd-158">Works across domains and forests.</span></span>
- <span data-ttu-id="e78dd-159">PowerShell kodu.</span><span class="sxs-lookup"><span data-stu-id="e78dd-159">PowerShell code.</span></span>

### <a name="cons"></a><span data-ttu-id="e78dd-160">Simgeler</span><span class="sxs-lookup"><span data-stu-id="e78dd-160">Cons</span></span>

- <span data-ttu-id="e78dd-161">Windows Server 2012 veya sonraki sürümünü gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e78dd-161">Requires Windows Server 2012 or later.</span></span>
- <span data-ttu-id="e78dd-162">İkinci atlama için WinRM desteklemez.</span><span class="sxs-lookup"><span data-stu-id="e78dd-162">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="e78dd-163">Nesneleri ve hizmet asıl adları (SPN) güncelleştirmek için hakları gerekir.</span><span class="sxs-lookup"><span data-stu-id="e78dd-163">Requires rights to update objects and Service Principal Names (SPNs).</span></span>

### <a name="example"></a><span data-ttu-id="e78dd-164">Örnek</span><span class="sxs-lookup"><span data-stu-id="e78dd-164">Example</span></span>

<span data-ttu-id="e78dd-165">Kaynak yapılandıran örnek üzerinde kısıtlı temsilci tabanlı bir PowerShell göz atalım _SunucuC ise_ temsilci seçilen kimlik bilgilerinden izin vermek için bir _SunucuB_.</span><span class="sxs-lookup"><span data-stu-id="e78dd-165">Let's look at a PowerShell example that configures resource based constrained delegation on _ServerC_ to allow delegated credentials from a _ServerB_.</span></span>
<span data-ttu-id="e78dd-166">Bu örnek, tüm sunucular Windows Server 2012 veya sonraki sürümünü, çalıştığını varsayar ve hangi sunuculardan herhangi biri için her bir etki alanı en az bir Windows Server 2012 etki alanı denetleyicisi olduğunu ait.</span><span class="sxs-lookup"><span data-stu-id="e78dd-166">This example assumes that all servers are running Windows Server 2012 or later, and that there is at least one Windows Server 2012 domain controller each domain to which any of the servers belong.</span></span>

<span data-ttu-id="e78dd-167">Kısıtlanmış temsilciyi yapılandırmak önce eklemelisiniz `RSAT-AD-PowerShell` Active Directory PowerShell modülü yüklemek için özellik ve daha sonra oturumunuz bu modülü içeri aktarın:</span><span class="sxs-lookup"><span data-stu-id="e78dd-167">Before you can configure constrained delegation, you must add the `RSAT-AD-PowerShell` feature to install the Active Directory PowerShell module, and then import that module into your session:</span></span>

```powershell
PS C:\> Add-WindowsFeature RSAT-AD-PowerShell

PS C:\> Import-Module ActiveDirectory
```
<span data-ttu-id="e78dd-168">Birkaç kullanılabilir cmdlet'lerin artık sahip bir **PrincipalsAllowedToDelegateToAccount** parametresi:</span><span class="sxs-lookup"><span data-stu-id="e78dd-168">Several available cmdlets now have a **PrincipalsAllowedToDelegateToAccount** parameter:</span></span>

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

<span data-ttu-id="e78dd-169">**PrincipalsAllowedToDelegateToAccount** parametre ayarlar Active Directory nesne özniteliği **msDS-AllowedToActOnBehalfOfOtherIdentity**, erişim denetimi listesi (ACL) içeriyor, hangi hesapların ilişkili hesabı kimlik bilgilerini temsil izniniz belirtir (Bizim örneğimizde, makine hesabını olacaktır _sunucu_).</span><span class="sxs-lookup"><span data-stu-id="e78dd-169">The **PrincipalsAllowedToDelegateToAccount** parameter sets the Active Directory object attribute **msDS-AllowedToActOnBehalfOfOtherIdentity**, which contains an access control list (ACL) that specifies which accounts have permission to delegate credentials to the associated account (in our example, it will be the machine account for _Server_).</span></span>

<span data-ttu-id="e78dd-170">Artık sunucuları temsil etmek için kullanacağız değişkenleri ayarlayalım:</span><span class="sxs-lookup"><span data-stu-id="e78dd-170">Now let's set up the variables we'll use to represent the servers:</span></span>

```powershell
# Set up variables for reuse
$ServerA = $env:COMPUTERNAME
$ServerB = Get-ADComputer -Identity ServerB
$ServerC = Get-ADComputer -Identity ServerC
```

<span data-ttu-id="e78dd-171">WinRM (ve bu nedenle PowerShell uzaktan iletişimini) varsayılan olarak bilgisayar hesabı olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="e78dd-171">WinRM (and therefore PowerShell remoting) runs as the computer account by default.</span></span> <span data-ttu-id="e78dd-172">Bu bakarak görebilirsiniz **StartName** özelliği `winrm` hizmeti:</span><span class="sxs-lookup"><span data-stu-id="e78dd-172">You can see this by looking at the **StartName** property of the `winrm` service:</span></span>

```powershell
PS C:\> Get-WmiObject win32_service -filter 'name="winrm"' | Format-List StartName

StartName : NT AUTHORITY\NetworkService
```

<span data-ttu-id="e78dd-173">İçin _SunucuC ise_ PowerShell uzaktan iletişimini oturumundan temsilci izni _SunucuB_, biz ayarlayarak erişim izni verir **PrincipalsAllowedToDelegateToAccount** parametresi _SunucuC ise_ için bilgisayar nesnesine göre _SunucuB_:</span><span class="sxs-lookup"><span data-stu-id="e78dd-173">For _ServerC_ to allow delegation from a PowerShell remoting session on _ServerB_, we will grant access by setting the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to the computer object of _ServerB_:</span></span>

```powershell
# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB

# Check the value of the attribute directly
$x = Get-ADComputer -Identity $ServerC -Properties msDS-AllowedToActOnBehalfOfOtherIdentity
$x.'msDS-AllowedToActOnBehalfOfOtherIdentity'.Access

# Check the value of the attribute indirectly
Get-ADComputer -Identity $ServerC -Properties PrincipalsAllowedToDelegateToAccount
```

<span data-ttu-id="e78dd-174">Kerberos [Anahtar Dağıtım Merkezi (KDC)](https://msdn.microsoft.com/library/windows/desktop/aa378170(v=vs.85).aspx) önbellekler 15 dakika boyunca erişim denemesi (negatif önbellek) reddedildi.</span><span class="sxs-lookup"><span data-stu-id="e78dd-174">The Kerberos [Key Distribution Center (KDC)](https://msdn.microsoft.com/library/windows/desktop/aa378170(v=vs.85).aspx) caches denied access attempts (negative cache) for 15 minutes.</span></span> <span data-ttu-id="e78dd-175">Varsa _SunucuB_ daha önce erişmeyi denedi _SunucuC ise_, üzerinde önbelleği temizlemek ihtiyacınız olacak _SunucuB_ aşağıdaki komutunu çağırarak:</span><span class="sxs-lookup"><span data-stu-id="e78dd-175">If _ServerB_ has previously attempted to access _ServerC_, you will need to clear the cache on _ServerB_ by invoking the following command:</span></span>

```powershell
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    klist purge -li 0x3e7
}
```

<span data-ttu-id="e78dd-176">Ayrıca bilgisayarı yeniden başlatın veya önbelleği temizlemek için en az 15 dakika bekleyin.</span><span class="sxs-lookup"><span data-stu-id="e78dd-176">You could also restart the computer, or wait at least 15 minutes to clear the cache.</span></span>

<span data-ttu-id="e78dd-177">Önbelleği temizledikten sonra koddan başarıyla çalıştırabilirsiniz _ServerA_ aracılığıyla _SunucuB_ için _SunucuC ise_:</span><span class="sxs-lookup"><span data-stu-id="e78dd-177">After clearing the cache, you can successfully run code from _ServerA_ through _ServerB_ to _ServerC_:</span></span>

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

<span data-ttu-id="e78dd-178">Bu örnekte, `$using` değişkeni sağlamak için kullanılan `$ServerC` değişken görünür _SunucuB_.</span><span class="sxs-lookup"><span data-stu-id="e78dd-178">In this example, the `$using` variable is used to make the `$ServerC` variable visible to _ServerB_.</span></span> <span data-ttu-id="e78dd-179">Hakkında daha fazla bilgi için `$using` değişken, bkz: [about_Remote_Variables](https://technet.microsoft.com/library/jj149005.aspx).</span><span class="sxs-lookup"><span data-stu-id="e78dd-179">For more information about the `$using` variable, see [about_Remote_Variables](https://technet.microsoft.com/library/jj149005.aspx).</span></span>

<span data-ttu-id="e78dd-180">Kimlik bilgileri için temsilci seçmek birden çok sunucu izin vermek için _SunucuC ise_, değerini **PrincipalsAllowedToDelegateToAccount** parametresi _SunucuC ise_ bir dizi:</span><span class="sxs-lookup"><span data-stu-id="e78dd-180">To allow multiple servers to delegate credentials to _ServerC_, set the value of the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to an array:</span></span>

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

<span data-ttu-id="e78dd-181">Etki alanları arasında ikinci atlama yapmak istiyorsanız, tam etki alanı adı (FQDN) etki alanının etki alanı denetleyicisini kendisine ekleme _SunucuB_ aittir:</span><span class="sxs-lookup"><span data-stu-id="e78dd-181">If you want to make the second hop across domains, add fully-qualified domain name (FQDN) of the domain controller of the domain to which _ServerB_ belongs:</span></span>

```powershell
# For ServerC in Contoso domain and ServerB in other domain
$ServerB = Get-ADComputer -Identity ServerB -Server dc1.alpineskihouse.com
$ServerC = Get-ADComputer -Identity ServerC
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB
```

<span data-ttu-id="e78dd-182">Temsilci SunucuC ise kimlik özelliği kaldırmak için değerini ayarlamak **PrincipalsAllowedToDelegateToAccount** parametresi _SunucuC ise_ için `$null`:</span><span class="sxs-lookup"><span data-stu-id="e78dd-182">To remove the ability to delegate credentials to ServerC, set the value of the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to `$null`:</span></span>

```powershell
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $null
```

### <a name="information-on-resource-based-kerberos-constrained-delegation"></a><span data-ttu-id="e78dd-183">Kaynak tabanlı kısıtlı Kerberos temsilcisi seçme hakkında bilgi</span><span class="sxs-lookup"><span data-stu-id="e78dd-183">Information on resource-based Kerberos constrained delegation</span></span>

- [<span data-ttu-id="e78dd-184">Kerberos kimlik doğrulamasındaki yenilikler</span><span class="sxs-lookup"><span data-stu-id="e78dd-184">What's New in Kerberos Authentication</span></span>](https://technet.microsoft.com/library/hh831747.aspx)
- [<span data-ttu-id="e78dd-185">Nasıl Windows Server 2012 hızları kolaylaştırın, Kerberos kısıtlı temsilcisi, bölüm 1</span><span class="sxs-lookup"><span data-stu-id="e78dd-185">How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 1</span></span>](https://windowsitpro.com/security/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-1)
- [<span data-ttu-id="e78dd-186">Nasıl Windows Server 2012 hızları kolaylaştırın, Kerberos kısıtlı temsilcisi, bölüm 2</span><span class="sxs-lookup"><span data-stu-id="e78dd-186">How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 2</span></span>](https://windowsitpro.com/security/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-2)
- [<span data-ttu-id="e78dd-187">Anlama Kerberos kısıtlı temsilcisi tümleşik Windows kimlik doğrulaması ile Azure Active Directory Uygulama Ara sunucusu dağıtımları için</span><span class="sxs-lookup"><span data-stu-id="e78dd-187">Understanding Kerberos Constrained Delegation for Azure Active Directory Application Proxy Deployments with Integrated Windows Authentication</span></span>](https://aka.ms/kcdpaper)
- <span data-ttu-id="e78dd-188">[[MS-ADA2]: Active Directory şema öznitelikleri M2.210 özniteliği msDS-AllowedToActOnBehalfOfOtherIdentity](https://msdn.microsoft.com/library/hh554126.aspx)</span><span class="sxs-lookup"><span data-stu-id="e78dd-188">[[MS-ADA2]: Active Directory Schema Attributes M2.210 Attribute msDS-AllowedToActOnBehalfOfOtherIdentity](https://msdn.microsoft.com/library/hh554126.aspx)</span></span>
- <span data-ttu-id="e78dd-189">[[MS-SFU]: Kerberos Protokolü uzantıları: Kullanıcı için hizmet ve kısıtlanmış temsil protokolü 1.3.2 S4U2proxy](https://msdn.microsoft.com/library/cc246079.aspx)</span><span class="sxs-lookup"><span data-stu-id="e78dd-189">[[MS-SFU]: Kerberos Protocol Extensions: Service for User and Constrained Delegation Protocol 1.3.2 S4U2proxy](https://msdn.microsoft.com/library/cc246079.aspx)</span></span>
- [<span data-ttu-id="e78dd-190">Kaynak tabanlı Kerberos kısıtlı temsil</span><span class="sxs-lookup"><span data-stu-id="e78dd-190">Resource Based Kerberos Constrained Delegation</span></span>](https://blog.kloud.com.au/2013/07/11/kerberos-constrained-delegation/)
- [<span data-ttu-id="e78dd-191">Kısıtlanmış temsilci kullanarak PrincipalsAllowedToDelegateToAccount olmadan uzaktan yönetim</span><span class="sxs-lookup"><span data-stu-id="e78dd-191">Remote Administration Without Constrained Delegation Using PrincipalsAllowedToDelegateToAccount</span></span>](https://blogs.msdn.microsoft.com/taylorb/2012/11/06/remote-administration-without-constrained-delegation-using-principalsallowedtodelegatetoaccount/)

## <a name="pssessionconfiguration-using-runas"></a><span data-ttu-id="e78dd-192">Farklı Çalıştır'ı kullanarak PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="e78dd-192">PSSessionConfiguration using RunAs</span></span>

<span data-ttu-id="e78dd-193">Bir oturum yapılandırması oluşturabilirsiniz _SunucuB_ ve kendi **RunAsCredential** parametresi.</span><span class="sxs-lookup"><span data-stu-id="e78dd-193">You can create a session configuration on _ServerB_ and set its **RunAsCredential** parameter.</span></span>

<span data-ttu-id="e78dd-194">İkinci atlama sorunu çözmek için PSSessionConfiguration ve Farklı Çalıştır'ı kullanma hakkında daha fazla bilgi için bkz: [çoklu atlamalı PowerShell uzaktan iletişim için başka bir çözüm](https://blogs.msdn.microsoft.com/sergey_babkins_blog/2015/03/18/another-solution-to-multi-hop-powershell-remoting/).</span><span class="sxs-lookup"><span data-stu-id="e78dd-194">For information about using PSSessionConfiguration and RunAs to solve the second hop problem, see [Another solution to multi-hop PowerShell remoting](https://blogs.msdn.microsoft.com/sergey_babkins_blog/2015/03/18/another-solution-to-multi-hop-powershell-remoting/).</span></span>

### <a name="pros"></a><span data-ttu-id="e78dd-195">Uzmanları</span><span class="sxs-lookup"><span data-stu-id="e78dd-195">Pros</span></span>

- <span data-ttu-id="e78dd-196">Herhangi bir sunucu WMF 3.0 veya üstü ile çalışır.</span><span class="sxs-lookup"><span data-stu-id="e78dd-196">Works with any server with WMF 3.0 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="e78dd-197">Simgeler</span><span class="sxs-lookup"><span data-stu-id="e78dd-197">Cons</span></span>

- <span data-ttu-id="e78dd-198">Yapılandırılmasını gerektirir **PSSessionConfiguration** ve **RunAs** Ara her sunucuda (_SunucuB_).</span><span class="sxs-lookup"><span data-stu-id="e78dd-198">Requires configuration of **PSSessionConfiguration** and **RunAs** on every intermediate server (_ServerB_).</span></span>
- <span data-ttu-id="e78dd-199">Bir etki alanı kullanırken parola bakıma gerek duyacağını **RunAs** hesabı</span><span class="sxs-lookup"><span data-stu-id="e78dd-199">Requires password maintenance when using a domain **RunAs** account</span></span>

## <a name="just-enough-administration-jea"></a><span data-ttu-id="e78dd-200">Yeterli Yönetim (JEA)</span><span class="sxs-lookup"><span data-stu-id="e78dd-200">Just Enough Administration (JEA)</span></span>

<span data-ttu-id="e78dd-201">JEA, yönetici bir PowerShell oturumunda çalıştırmak hangi komutları sınırlamanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="e78dd-201">JEA allows you to restrict what commands an administrator can run during a PowerShell session.</span></span> <span data-ttu-id="e78dd-202">İkinci atlama sorunu çözmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e78dd-202">It can be used to solve the second hop problem.</span></span>

<span data-ttu-id="e78dd-203">JEA hakkında daha fazla bilgi için bkz. [yeterli yönetim](https://docs.microsoft.com/powershell/jea/overview).</span><span class="sxs-lookup"><span data-stu-id="e78dd-203">For information about JEA, see [Just Enough Administration](https://docs.microsoft.com/powershell/jea/overview).</span></span>

### <a name="pros"></a><span data-ttu-id="e78dd-204">Uzmanları</span><span class="sxs-lookup"><span data-stu-id="e78dd-204">Pros</span></span>

- <span data-ttu-id="e78dd-205">Sanal bir hesap kullanırken hiçbir parola Bakım.</span><span class="sxs-lookup"><span data-stu-id="e78dd-205">No password maintenance when using a virtual account.</span></span>

### <a name="cons"></a><span data-ttu-id="e78dd-206">Simgeler</span><span class="sxs-lookup"><span data-stu-id="e78dd-206">Cons</span></span>

- <span data-ttu-id="e78dd-207">WMF 5.0 veya sonraki sürümünü gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e78dd-207">Requires WMF 5.0 or later.</span></span>
- <span data-ttu-id="e78dd-208">Her bir ara sunucu yapılandırma gerektirir (_SunucuB_).</span><span class="sxs-lookup"><span data-stu-id="e78dd-208">Requires configuration on every intermediate server (_ServerB_).</span></span>

## <a name="pass-credentials-inside-an-invoke-command-script-block"></a><span data-ttu-id="e78dd-209">Invoke-Command betik bloğunun Pass kimlik bilgileri</span><span class="sxs-lookup"><span data-stu-id="e78dd-209">Pass credentials inside an Invoke-Command script block</span></span>

<span data-ttu-id="e78dd-210">Kimlik bilgileri içine geçirebilirsiniz **ScriptBlock** çağrısına parametre [Invoke-Command](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/invoke-command) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="e78dd-210">You can pass credentials inside the **ScriptBlock** parameter of a call to the [Invoke-Command](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/invoke-command) cmdlet.</span></span>

### <a name="pros"></a><span data-ttu-id="e78dd-211">Uzmanları</span><span class="sxs-lookup"><span data-stu-id="e78dd-211">Pros</span></span>

- <span data-ttu-id="e78dd-212">Özel sunucu yapılandırması gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="e78dd-212">Does not require special server configuration.</span></span>
- <span data-ttu-id="e78dd-213">WMF 2.0 veya sonraki sürümünü çalıştıran herhangi bir sunucu üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="e78dd-213">Works on any server running WMF 2.0 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="e78dd-214">Simgeler</span><span class="sxs-lookup"><span data-stu-id="e78dd-214">Cons</span></span>

- <span data-ttu-id="e78dd-215">Garip kod teknik gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e78dd-215">Requires an awkward code technique.</span></span>
- <span data-ttu-id="e78dd-216">WMF 2.0 çalıştırılıyorsa, uzak oturumu bağımsız değişkenleri geçirmek için farklı bir sözdizimi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e78dd-216">If running WMF 2.0, requires different syntax for passing arguments to a remote session.</span></span>

### <a name="example"></a><span data-ttu-id="e78dd-217">Örnek</span><span class="sxs-lookup"><span data-stu-id="e78dd-217">Example</span></span>

<span data-ttu-id="e78dd-218">Aşağıdaki örnek, kimlik bilgilerini geçirmek nasıl gösterir bir **Invoke-Command** betik bloğu:</span><span class="sxs-lookup"><span data-stu-id="e78dd-218">The following example shows how to pass credentials in an **Invoke-Command** script block:</span></span>

```powershell
# This works without delegation, passing fresh creds
# Note $Using:Cred in nested request
$cred = Get-Credential Contoso\Administrator
Invoke-Command -ComputerName ServerB -Credential $cred -ScriptBlock {
    hostname
    Invoke-Command -ComputerName ServerC -Credential $Using:cred -ScriptBlock {hostname}
}
```

## <a name="see-also"></a><span data-ttu-id="e78dd-219">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e78dd-219">See also</span></span>

[<span data-ttu-id="e78dd-220">PowerShell Uzaktan İletişim Güvenlik Konuları</span><span class="sxs-lookup"><span data-stu-id="e78dd-220">PowerShell Remoting Security Considerations</span></span>](WinRMSecurity.md)
