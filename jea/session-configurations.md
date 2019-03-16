---
ms.date: 06/12/2017
keywords: jea, powershell, güvenlik
title: JEA oturum yapılandırmaları
ms.openlocfilehash: b98726ea7ed3aabdfd05034c3b70118e327160cd
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056609"
---
# <a name="jea-session-configurations"></a><span data-ttu-id="fdf1e-103">JEA oturum yapılandırmaları</span><span class="sxs-lookup"><span data-stu-id="fdf1e-103">JEA Session Configurations</span></span>

> <span data-ttu-id="fdf1e-104">Şunun için geçerlidir: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="fdf1e-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="fdf1e-105">Bir JEA uç noktası oluşturarak ve belirli bir şekilde bir PowerShell oturumu yapılandırma dosyası kaydedilirken bir sistemde kayıtlı.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-105">A JEA endpoint is registered on a system by creating and registering a PowerShell session configuration file in a specific way.</span></span>
<span data-ttu-id="fdf1e-106">Oturum yapılandırmaları belirlemek *kimin* JEA uç noktası kullanabilir ve hangi rolleri erişimleri.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-106">Session configurations determine *who* can use the JEA endpoint, and which role(s) they will have access to.</span></span>
<span data-ttu-id="fdf1e-107">JEA oturumda herhangi bir rol kullanıcıları için geçerli genel ayarlar da tanımlarlar.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-107">They also define global settings that apply to users of any role in the JEA session.</span></span>

<span data-ttu-id="fdf1e-108">Bu konuda, bir PowerShell oturumu yapılandırma dosyası oluşturun ve bir JEA uç noktasını kaydetme açıklar.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-108">This topic describes how to create a PowerShell session configuration file and register a JEA endpoint.</span></span>

## <a name="create-a-session-configuration-file"></a><span data-ttu-id="fdf1e-109">Oturum yapılandırma dosyası oluşturma</span><span class="sxs-lookup"><span data-stu-id="fdf1e-109">Create a session configuration file</span></span>

<span data-ttu-id="fdf1e-110">Bir JEA uç nokta kaydetmek için uç noktanın nasıl yapılandırılmalıdır belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-110">In order to register a JEA endpoint, you need to specify how that endpoint should be configured.</span></span>
<span data-ttu-id="fdf1e-111">Burada, en önemli hangi JEA uç noktasına erişimi olması gereken olan biri, hangi rollerin bunlar dikkate alınır için birçok seçenek atanabilir, hangi kimlik perde JEA kullanacağı vardır ve hangi JEA uç noktası adı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-111">There are many options to consider here, the most important of which being who should have access to the JEA endpoint, which roles will they be assigned, which identity will JEA use under the covers, and what will be the name of the JEA endpoint.</span></span>
<span data-ttu-id="fdf1e-112">Bu tüm tanımlanmış bir PowerShell oturumu yapılandırma dosyasında, bir PowerShell veri dosyası .pssc uzantısı ile sona eriyor.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-112">These are all defined in a PowerShell session configuration file, which is a PowerShell data file ending with a .pssc extension.</span></span>

<span data-ttu-id="fdf1e-113">Bir JEA uç noktalar için iskelet oturum yapılandırma dosyası oluşturmak için aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-113">To create a skeleton session configuration file for JEA endpoints, run the following command.</span></span>

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> <span data-ttu-id="fdf1e-114">En yaygın yapılandırma seçenekleri çatı dosyasında varsayılan olarak dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-114">Only the most common configuration options are included in the skeleton file by default.</span></span>
> <span data-ttu-id="fdf1e-115">Kullanım `-Full` geçme içinde oluşturulan PSSC tüm ilgili ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-115">Use the `-Full` switch to include all applicable settings in the generated PSSC.</span></span>

<span data-ttu-id="fdf1e-116">Herhangi bir metin düzenleyicisinde oturum yapılandırma dosyasını açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-116">You can open the session configuration file in any text editor.</span></span>
<span data-ttu-id="fdf1e-117">`-SessionType RestrictedRemoteServer` Alan, oturum yapılandırması güvenli yönetimi için JEA tarafından kullanılacak gösterir.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-117">The `-SessionType RestrictedRemoteServer` field indicates that the session configuration will be used by JEA for secure management.</span></span>
<span data-ttu-id="fdf1e-118">Bu şekilde yapılandırılan oturumları çalışır [NoLanguage modu](https://technet.microsoft.com/library/dn433292.aspx) ve yalnızca aşağıdaki 8 varsayılan komutları (ve diğer adları) olan kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="fdf1e-118">Sessions configured this way will operate in [NoLanguage mode](https://technet.microsoft.com/library/dn433292.aspx) and only have the following 8 default commands (and aliases) available:</span></span>

- <span data-ttu-id="fdf1e-119">Clear-Host (cls, Temizle)</span><span class="sxs-lookup"><span data-stu-id="fdf1e-119">Clear-Host (cls, clear)</span></span>
- <span data-ttu-id="fdf1e-120">Çıkış-PSSession (exsn, çıkış)</span><span class="sxs-lookup"><span data-stu-id="fdf1e-120">Exit-PSSession (exsn, exit)</span></span>
- <span data-ttu-id="fdf1e-121">Get-Command (gcm)</span><span class="sxs-lookup"><span data-stu-id="fdf1e-121">Get-Command (gcm)</span></span>
- <span data-ttu-id="fdf1e-122">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="fdf1e-122">Get-FormatData</span></span>
- <span data-ttu-id="fdf1e-123">Get-Help</span><span class="sxs-lookup"><span data-stu-id="fdf1e-123">Get-Help</span></span>
- <span data-ttu-id="fdf1e-124">Ölçü nesnesi (ölçü)</span><span class="sxs-lookup"><span data-stu-id="fdf1e-124">Measure-Object (measure)</span></span>
- <span data-ttu-id="fdf1e-125">Varsayılan dışarı</span><span class="sxs-lookup"><span data-stu-id="fdf1e-125">Out-Default</span></span>
- <span data-ttu-id="fdf1e-126">Select-Object (Seç)</span><span class="sxs-lookup"><span data-stu-id="fdf1e-126">Select-Object (select)</span></span>

<span data-ttu-id="fdf1e-127">PowerShell yok sağlayıcıları kullanılabilir ya da herhangi bir dış (yürütülebilir dosyaları, betikler, vb.) programlardır.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-127">No PowerShell providers are available, nor are any external programs (executables, scripts, etc.).</span></span>

<span data-ttu-id="fdf1e-128">JEA oturumu için yapılandırmak da isteyeceksiniz bazı alanlar vardır.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-128">There are several other fields you will want to configure for the JEA session.</span></span>
<span data-ttu-id="fdf1e-129">Bunlar aşağıdaki bölümlerde ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-129">They are covered in the following sections.</span></span>

### <a name="choose-the-jea-identity"></a><span data-ttu-id="fdf1e-130">JEA kimliğini seçin</span><span class="sxs-lookup"><span data-stu-id="fdf1e-130">Choose the JEA identity</span></span>

<span data-ttu-id="fdf1e-131">Arka planda JEA bağlı kullanıcının komutlarını çalıştırırken kullanılacak bir kimliği (hesap) gerekir.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-131">Behind the scenes, JEA needs an identity (account) to use when running a connected user's commands.</span></span>
<span data-ttu-id="fdf1e-132">JEA oturum yapılandırma dosyasında kullanacağınız kimliği karar sizin.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-132">You decide which identity JEA will use in the session configuration file.</span></span>

#### <a name="local-virtual-account"></a><span data-ttu-id="fdf1e-133">Yerel sanal hesap</span><span class="sxs-lookup"><span data-stu-id="fdf1e-133">Local Virtual Account</span></span>

<span data-ttu-id="fdf1e-134">Rolleri bu JEA uç noktası tarafından desteklenen tüm yerel makine yönetmek için kullanılır ve bir yerel yönetici hesabı başarıyla komutları çalıştırmak yeterli olduğundan, sanal yerel hesap kullanmak için JEA yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-134">If the roles supported by this JEA endpoint are all used to manage the local machine, and a local administrator account is sufficient to run the commands successfully, you should configure JEA to use a local virtual account.</span></span>
<span data-ttu-id="fdf1e-135">Belirli bir kullanıcı için benzersiz ve kendi PowerShell oturumu süresi için yalnızca son geçici hesaplarının sanal hesaplarıdır.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-135">Virtual accounts are temporary accounts that are unique to a specific user and only last for the duration of their PowerShell session.</span></span>
<span data-ttu-id="fdf1e-136">Üye sunucu veya iş istasyonunun Sanal hesaplar yerel bilgisayarın ait **Yöneticiler** grup ve çoğu sistem kaynaklarına erişimi vardır.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-136">On a member server or workstation, virtual accounts belong to the local computer's **Administrators** group, and have access to most system resources.</span></span>
<span data-ttu-id="fdf1e-137">Bir Active Directory etki alanı denetleyicisinde etki alanı için sanal hesaplar ait **Domain Admins** grubu.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-137">On an Active Directory Domain Controller, virtual accounts belong to the domain's **Domain Admins** group.</span></span>

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

<span data-ttu-id="fdf1e-138">Oturum yapılandırması tarafından desteklenen rolleri gibi geniş ayrıcalıkları gerektirmez, isteğe bağlı olarak sanal hesap ait olacak güvenlik gruplarını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-138">If the roles supported by the session configuration do not require such broad privileges, you can optionally specify the security groups to which the virtual account will belong.</span></span>
<span data-ttu-id="fdf1e-139">Üye sunucu veya iş istasyonunun belirli güvenlik grupları yerel gruplar, bir etki alanından grupları değil olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-139">On a member server or workstation, the specified security groups must be local groups, not groups from a domain.</span></span>

<span data-ttu-id="fdf1e-140">Belirtilen bir veya daha fazla güvenlik grubu, sanal hesap yerel veya etki alanı yöneticileri grubuna ait olur.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-140">When one or more security groups is specified, the virtual account will no longer belong to the local or domain administrators group.</span></span>

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```

> [!NOTE]
> <span data-ttu-id="fdf1e-141">Sanal hesaplar, yerel sunucu güvenlik ilkesini içinde bir hizmet olarak oturum açma geçici olarak verilir.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-141">Virtual accounts are temporarily granted the Logon as a service right in the local server security policy.</span></span>  <span data-ttu-id="fdf1e-142">Belirtilen VirtualAccountGroups birini zaten ilkesinde bu hak verilmemişse, tek tek sanal hesap artık eklendi ve ilkeden kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-142">If one of the VirtualAccountGroups specified has already been granted this right in the policy, the individual virtual account will no longer be added and removed from the policy.</span></span>  <span data-ttu-id="fdf1e-143">Bu, burada etki alanı denetleyicisi güvenlik ilkesi uyarlamaları yakından denetlendiği etki alanı denetleyicileri gibi senaryolarda yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-143">This can be useful in scenarios such as domain controllers where revisions to the domain controller security policy are closely audited.</span></span>  <span data-ttu-id="fdf1e-144">Bu seçenek yalnızca Kasım 2018'den Windows Server 2016 veya sonraki toplama ve Windows Server 2019 Ocak 2019 ile'veya sonraki toplama kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-144">This is only available in Windows Server 2016 with the November 2018 or later rollup and Windows Server 2019 with the January 2019 or later rollup.</span></span>

#### <a name="group-managed-service-account"></a><span data-ttu-id="fdf1e-145">Grup Yönetilen Hizmet Hesabı</span><span class="sxs-lookup"><span data-stu-id="fdf1e-145">Group Managed Service Account</span></span>


<span data-ttu-id="fdf1e-146">JEA kullanıcı diğer makineler veya web Hizmetleri gibi ağ kaynaklarına erişmek için gerektiren senaryolar için bir grup yönetilen hizmet hesabı (gMSA) kullanmak için daha uygun bir kimliği var.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-146">For scenarios requiring the JEA user to access network resources such as other machines or web services, a group managed service account (gMSA) is a more appropriate identity to use.</span></span>
<span data-ttu-id="fdf1e-147">gMSA hesabı etki alanı içinde herhangi bir makinede kaynaklarına karşı kimlik doğrulaması için kullanılabilecek bir etki alanı kimliği verir.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-147">gMSA accounts give you a domain identity which can be used to authenticate against resources on any machine within the domain.</span></span>
<span data-ttu-id="fdf1e-148">Erişmeye çalıştığınız hakları kaynaklara göre belirlenir gMSA hesabı sağlar.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-148">The rights the gMSA account gives you is determined by the resources you are accessing.</span></span>
<span data-ttu-id="fdf1e-149">Makine/Hizmet Yöneticisi açıkça gMSA hesabı yönetici ayrıcalıkları vermedikçe, otomatik olarak tüm makineler veya hizmetler üzerinde yönetici hakları yoktur.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-149">You will not automatically have admin rights on any machines or services unless the machine/service administrator has explicitly granted the gMSA account admin privileges.</span></span>

```powershell
# Configure JEA sessions to use the gMSA account in the local computer's domain with the sAMAccountName of 'MyJEAgMSA'
GroupManagedServiceAccount = 'Domain\MyJEAgMSA'
```

<span data-ttu-id="fdf1e-150">gMSA hesabı yalnızca kullanılmalıdır ağ kaynaklarına erişimi olduğunda gerekli birkaç nedeni:</span><span class="sxs-lookup"><span data-stu-id="fdf1e-150">gMSA accounts should only be used when access to network resources are required for a few reasons:</span></span>

- <span data-ttu-id="fdf1e-151">Her kullanıcı Çalıştır aynı kimliği paylaşıyor beri gMSA hesabı kullanılırken bir kullanıcı için Eylemler geri izleme için daha zor olan.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-151">It is harder to trace back actions to a user when using a gMSA account since every user shares the same run-as identity.</span></span> <span data-ttu-id="fdf1e-152">PowerShell oturumu dökümleri ve kullanıcıların eylemlerini ile ilişkilendirmek için günlükleri başvurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-152">You will need to consult PowerShell session transcripts and logs to correlate users with their actions.</span></span>

- <span data-ttu-id="fdf1e-153">Bağlanan kullanıcının erişim gerekmeyen birçok ağ kaynaklarına erişim gMSA hesabı olabilir.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-153">The gMSA account may have access to many network resources which the connecting user does not need access to.</span></span> <span data-ttu-id="fdf1e-154">En düşük öncelik ilkesini izlemek için bir JEA oturumunda etkili izinleri sınırlamak her zaman deneyin.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-154">Always try to limit effective permissions in a JEA session to follow the principle of least privilege.</span></span>

> [!NOTE]
> <span data-ttu-id="fdf1e-155">Grup yönetilen hizmet hesapları, yalnızca Windows PowerShell 5.1 kullanılabilir veya daha yeni ve etki alanına katılmış makinelerde.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-155">Group managed service accounts are only available in Windows PowerShell 5.1 or newer and on domain-joined machines.</span></span>

#### <a name="more-information-about-run-as-users"></a><span data-ttu-id="fdf1e-156">Hakkında daha fazla bilgi kullanıcı olarak çalıştırın</span><span class="sxs-lookup"><span data-stu-id="fdf1e-156">More information about run as users</span></span>

<span data-ttu-id="fdf1e-157">Kimlikleri ve bunların bir JEA oturum güvenliğini nasıl faktörü olarak çalışma hakkında ek bilgiler bulunabilir [güvenlik konuları](security-considerations.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-157">Additional information about run as identities and how they factor into the security of a JEA session can be found in the [security considerations](security-considerations.md) article.</span></span>

### <a name="session-transcripts"></a><span data-ttu-id="fdf1e-158">Oturum dökümleri</span><span class="sxs-lookup"><span data-stu-id="fdf1e-158">Session transcripts</span></span>

<span data-ttu-id="fdf1e-159">Bir JEA oturum yapılandırma dosyasına otomatik olarak kayıt dökümleri, kullanıcıların oturumlarının yapılandırma önerilir.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-159">It is recommended that you configure a JEA session configuration file to automatically record transcripts of users' sessions.</span></span>
<span data-ttu-id="fdf1e-160">PowerShell oturumu dökümleri bağlanan kullanıcının, farklı çalıştır kimlik atanmamış hakkındaki bilgileri içerir ve kullanıcı tarafından komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-160">PowerShell session transcripts contain information about the connecting user, the run as identity assigned to them, and the commands run by the user.</span></span>
<span data-ttu-id="fdf1e-161">Bunlar, belirli bir değişiklik sisteme gerçekleştiren anlaşılması gereken bir denetim ekibine yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-161">They can be useful to an auditing team who needs to understand who performed a specific change to a system.</span></span>

<span data-ttu-id="fdf1e-162">Oturum yapılandırma dosyasında otomatik döküm yapılandırmak için dökümleri nerede depolanması gereken bir klasöre bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-162">To configure automatic transcription in the session configuration file, provide a path to a folder where the transcripts should be stored.</span></span>

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

<span data-ttu-id="fdf1e-163">Belirtilen klasör değiştirmekten veya silmekten içindeki tüm veriler kullanıcıların önlemek için yapılandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-163">The specified folder should be configured to prevent users from modifying or deleting any data in it.</span></span>
<span data-ttu-id="fdf1e-164">Dökümler, okuma ve dizine yazma erişimi gerektiren yerel sistem hesabı tarafından klasörüne yazılır.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-164">Transcripts are written to the folder by the Local System account, which requires read and write access to the directory.</span></span>
<span data-ttu-id="fdf1e-165">Standart kullanıcılar klasörüne erişimi olmalıdır ve güvenlik yöneticileri sınırlı sayıda dökümleri denetim erişimi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-165">Standard users should have no access to the folder, and a limited set of security administrators should have access to audit the transcripts.</span></span>

### <a name="user-drive"></a><span data-ttu-id="fdf1e-166">Kullanıcı sürücü</span><span class="sxs-lookup"><span data-stu-id="fdf1e-166">User drive</span></span>

<span data-ttu-id="fdf1e-167">Bağlanan kullanıcıların bir komutu çalıştırmak için dosyaları JEA uç noktası kopyalamak istiyorsanız, oturum yapılandırma dosyasındaki kullanıcı sürücü etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-167">If your connecting users will need to copy files to/from the JEA endpoint in order to run a command, you can enable the user drive in the session configuration file.</span></span>
<span data-ttu-id="fdf1e-168">Kullanıcı sürücüdür bir [PSDrive](https://msdn.microsoft.com/powershell/scripting/getting-started/cookbooks/managing-windows-powershell-drives) bağlanan her kullanıcı için benzersiz bir klasöre eşlendi.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-168">The user drive is a [PSDrive](https://msdn.microsoft.com/powershell/scripting/getting-started/cookbooks/managing-windows-powershell-drives) that is mapped to a unique folder for each connecting user.</span></span>
<span data-ttu-id="fdf1e-169">Bu klasör, bunları tam dosya sistemine erişim vermeden veya dosya sistemi sağlayıcısı gösterme öğesine/öğesinden sistem dosyalarını kopyalamak için bir alan olarak görev yapar.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-169">This folder serves as a space for them to copy files to/from the system, without giving them access to the full file system or exposing the FileSystem provider.</span></span>
<span data-ttu-id="fdf1e-170">Kullanıcı sürücü içeriğini burada ağ bağlantısı kesilebilir durumlarda oturumları arasında kalıcıdır.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-170">The user drive contents are persistent across sessions to accommodate situations where network connectivity may be interrupted.</span></span>

```powershell
MountUserDrive = $true
```

<span data-ttu-id="fdf1e-171">Varsayılan olarak, kullanıcı sürücüsünde en fazla kullanıcı başına veri 50 MB'ın depolamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-171">By default, the user drive allows you to store a maximum of 50MB of data per user.</span></span>
<span data-ttu-id="fdf1e-172">Bir kullanıcı ile kullanabileceği veri miktarını sınırlamak *UserDriveMaximumSize* alan.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-172">You can limit the amount of data a user can consume with the *UserDriveMaximumSize* field.</span></span>

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

<span data-ttu-id="fdf1e-173">Verilerin kalıcı olmasını kullanıcı sürücüsündeki istemiyorsanız, sistemde klasörü her gece otomatik olarak temizlemek için zamanlanmış bir görev yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-173">If you do not want data in the user drive to be persistent, you can configure a scheduled task on the system to automatically clean up the folder every night.</span></span>

> [!NOTE]
> <span data-ttu-id="fdf1e-174">Kullanıcı yalnızca Windows PowerShell 5.1 bulunan ya da daha yeni sürücüdür.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-174">The user drive is only available in Windows PowerShell 5.1 or newer.</span></span>

### <a name="role-definitions"></a><span data-ttu-id="fdf1e-175">Rol tanımları</span><span class="sxs-lookup"><span data-stu-id="fdf1e-175">Role definitions</span></span>

<span data-ttu-id="fdf1e-176">Rol tanımları oturum yapılandırma dosyasında tanımlama eşleme *kullanıcılar* için *rolleri*.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-176">Role definitions in a session configuration file define the mapping of *users* to *roles*.</span></span>
<span data-ttu-id="fdf1e-177">Otomatik olarak kaydedildiğinde her kullanıcı veya grup bu alanda bulunan JEA uç noktasına izin verilir.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-177">Every user or group included in this field will automatically be granted permission to the JEA endpoint when it is registered.</span></span>
<span data-ttu-id="fdf1e-178">Her bir kullanıcı veya grubu yalnızca bir kez anahtar karma tablosu olarak dahil edilebilir, ancak birden çok rol atanabilir.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-178">Each user or group can be included as a key in the hashtable only once, but can be assigned multiple roles.</span></span>
<span data-ttu-id="fdf1e-179">Rol özelliğin adına .psrc uzantısı olmadan rolü özelliği dosyasının adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-179">The name of the role capability should be the name of the role capability file, without the .psrc extension.</span></span>

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

<span data-ttu-id="fdf1e-180">Bir kullanıcı birden fazla rol tanımı grubuna dahilse, her rol için erişim alırlar.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-180">If a user belongs to more than one group in the role definition, they will get access to the roles of each.</span></span>
<span data-ttu-id="fdf1e-181">İki rol aynı cmdlet'lere erişim sağlıyorsa, en esnek parametre kümesi kullanıcıya verilir.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-181">If two roles grant access to the same cmdlets, the most permissive parameter set will be granted to the user.</span></span>

<span data-ttu-id="fdf1e-182">Yerel kullanıcı veya grup rol tanımları alanını belirtirken, bilgisayar adını kullandığınız emin olun (değil *localhost* veya *.*) önce ters eğik çizgi.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-182">When specifying local users or groups in the role definitions field, be sure to use the computer name (not *localhost* or *.*) before the backslash.</span></span>
<span data-ttu-id="fdf1e-183">Bilgisayar adı inceleyerek denetleyebilirsiniz `$env:computername` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-183">You can check the computer name by inspecting the `$env:computername` variable.</span></span>

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a><span data-ttu-id="fdf1e-184">Rol özellik arama sırası</span><span class="sxs-lookup"><span data-stu-id="fdf1e-184">Role capability search order</span></span>

<span data-ttu-id="fdf1e-185">Yukarıdaki örnekte gösterildiği gibi rol işlevleri rol özellik dosyası düz adıyla (dosya adı uzantısı olmadan) olarak başvurulur.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-185">As shown in the example above, role capabilities are referenced by the flat name (filename without the extension) of the role capability file.</span></span>
<span data-ttu-id="fdf1e-186">Sistem düz aynı ada sahip birden çok rol özellikleri mevcuttur, etkin bir rol özelliği dosyayı seçmek için örtük arama sırası PowerShell kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-186">If multiple role capabilities are available on the system with the same flat name, PowerShell will use its implicit search order to select the effective role capability file.</span></span>
<span data-ttu-id="fdf1e-187">Götürür **değil** aynı ada sahip tüm rol özellik dosyaları için erişim verin.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-187">It will **not** give access to all role capability files with the same name.</span></span>

<span data-ttu-id="fdf1e-188">Jea'yı kullanan `$env:PSModulePath` rol özellik dosyaları taramak için hangi yolları belirlemek için ortam değişkeni.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-188">JEA uses the `$env:PSModulePath` environment variable to determine which paths to scan for role capability files.</span></span>
<span data-ttu-id="fdf1e-189">Her bu yollar içinde bir "RoleCapabilities" alt klasör içeren geçerli PowerShell modülleri için JEA görünecektir.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-189">Within each of those paths, JEA will look for valid PowerShell modules that contain a "RoleCapabilities" subfolder.</span></span>
<span data-ttu-id="fdf1e-190">JEA modülleri alma gibi Windows ile aynı ada sahip özel rol özellikleri için sağlanan rol işlevleri tercih eder.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-190">As with importing modules, JEA prefers role capabilities that are shipped with Windows to custom role capabilities with the same name.</span></span>
<span data-ttu-id="fdf1e-191">Tüm diğer adlandırma çakışmaları için öncelik, Windows (alfabetik olması garanti edilmez) dizindeki dosyaları listeler sıraya göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-191">For all other naming conflicts, precedence is determined by the order in which Windows enumerates the files in the directory (not guaranteed to be alphabetically).</span></span>
<span data-ttu-id="fdf1e-192">İstenen eşleşen ilk rol özellik dosyası bulunamadı. adı bağlanan kullanıcı için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-192">The first role capability file found that matches the desired name will be used for the connecting user.</span></span>

<span data-ttu-id="fdf1e-193">Rol özellik arama sırası, iki belirleyici değil veya daha fazla rol işlevleri aynı adı paylaşan olduğu **önemle tavsiye** rol işlevleri makinenizde benzersiz adlara sahip olun.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-193">Since the role capability search order is not deterministic when two or more role capabilities share the same name, it is **strongly recommended** that you ensure role capabilities have unique names on your machine.</span></span>

### <a name="conditional-access-rules"></a><span data-ttu-id="fdf1e-194">Koşullu erişim kuralları</span><span class="sxs-lookup"><span data-stu-id="fdf1e-194">Conditional access rules</span></span>

<span data-ttu-id="fdf1e-195">Otomatik olarak tüm kullanıcılar ve gruplar RoleDefinitions alanında bulunan JEA uç noktalarına erişimi verilir.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-195">All users and groups included in the RoleDefinitions field are automatically granted access to JEA endpoints.</span></span>
<span data-ttu-id="fdf1e-196">Koşullu erişim kuralları, bu erişimi iyileştirin ve kullanıcıların, atanmış olan rolleri etkilemez ek güvenlik gruplarına ait zorunlu olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-196">Conditional access rules allow you to refine this access and require users to belong to additional security groups which do not impact the roles which they are assigned.</span></span>
<span data-ttu-id="fdf1e-197">Bu bir "tam zamanında" ayrıcalıklı tümleştirmek istiyorsanız yararlı olabilir erişim yönetimi çözümü, akıllı kart kimlik doğrulaması veya diğer çok faktörlü kimlik doğrulaması çözümüyle JEA.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-197">This can be useful if you want to integrate a "just in time" privileged access management solution, smartcard authentication, or other multifactor authentication solution with JEA.</span></span>

<span data-ttu-id="fdf1e-198">Koşullu erişim kuralları, bir oturum yapılandırması dosyasını RequiredGroups alanında tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-198">Conditional access rules are defined in the RequiredGroups field in a session configuration file.</span></span>
<span data-ttu-id="fdf1e-199">Kullanan bir hashtable (iç içe isteğe bağlı olarak) sağlar, 'Ve' ve 'Veya' anahtarlar kurallarınızı oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-199">There, you can provide a hashtable (optionally nested) that uses 'And' and 'Or' keys to construct your rules.</span></span>
<span data-ttu-id="fdf1e-200">Bu alan kullanmayı bazı örnekleri aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="fdf1e-200">Here are some examples of how to leverage this field:</span></span>

```powershell
# Example 1: Connecting users must belong to a security group called "elevated-jea"
RequiredGroups = @{ And = 'elevated-jea' }

# Example 2: Connecting users must have signed on with 2 factor authentication or a smart card
# The 2 factor authentication group name is "2FA-logon" and the smart card group name is "smartcard-logon"
RequiredGroups = @{ Or = '2FA-logon', 'smartcard-logon' }

# Example 3: Connecting users must elevate into "elevated-jea" with their JIT system and have logged on with 2FA or a smart card
RequiredGroups = @{ And = 'elevated-jea', @{ Or = '2FA-logon', 'smartcard-logon' }}
```

> [!NOTE]
> <span data-ttu-id="fdf1e-201">Koşullu erişim kuralları yalnızca, Windows PowerShell 5.1 veya yeni kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-201">Conditional access rules are only available in Windows PowerShell 5.1 or newer.</span></span>

### <a name="other-properties"></a><span data-ttu-id="fdf1e-202">Diğer özellikler</span><span class="sxs-lookup"><span data-stu-id="fdf1e-202">Other properties</span></span>

<span data-ttu-id="fdf1e-203">Oturum yapılandırma dosyalarını da rol özellik dosyası için farklı komutlar bağlantı kullanıcı erişimi vermek için yalnızca özelliği olmadan yapabileceği her şeyi yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-203">Session configuration files can also do everything a role capability file can do, just without the ability to give connecting users access to different commands.</span></span>
<span data-ttu-id="fdf1e-204">Erişimi belirli cmdlet'ler, İşlevler veya sağlayıcıları tüm kullanıcılara izin vermek istiyorsanız, bunu yapabilirsiniz oturum yapılandırma dosyasında sağ.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-204">If you want to allow all users access to specific cmdlets, functions, or providers, you can do so right in the session configuration file.</span></span>
<span data-ttu-id="fdf1e-205">Oturum yapılandırma dosyasında desteklenen özellikler tam listesi için çalıştırma `Get-Help New-PSSessionConfigurationFile -Full`.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-205">For a full list of supported properties in the session configuration file, run `Get-Help New-PSSessionConfigurationFile -Full`.</span></span>

## <a name="testing-a-session-configuration-file"></a><span data-ttu-id="fdf1e-206">Test oturumu yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="fdf1e-206">Testing a session configuration file</span></span>

<span data-ttu-id="fdf1e-207">Kullanarak bir oturum yapılandırması test [Test PSSessionConfigurationFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-207">You can test a session configuration using the [Test-PSSessionConfigurationFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet.</span></span>
<span data-ttu-id="fdf1e-208">El ile söz dizimi doğru olduğundan emin olmak için bir metin düzenleyicisi kullanarak pssc dosyasını düzenlediyseniz oturum yapılandırma dosyanızı test önemle tavsiye edilir.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-208">It is strongly recommended that you test your session configuration file if you have edited the pssc file manually using a text editor to ensure the syntax is correct.</span></span>
<span data-ttu-id="fdf1e-209">Bu test oturumu yapılandırma dosyası geçemezse, başarıyla sistemde kayıtlı olması mümkün olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-209">If a session configuration file does not pass this test, it will not be able to be successfully registered on the system.</span></span>

## <a name="sample-session-configuration-file"></a><span data-ttu-id="fdf1e-210">Örnek oturum yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="fdf1e-210">Sample session configuration file</span></span>

<span data-ttu-id="fdf1e-211">Oluşturma ve oturum yapılandırmasını doğrulamak için JEA gösteren tam bir örnek aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-211">Below is a complete example showing how to create and validate a session configuration for JEA.</span></span>
<span data-ttu-id="fdf1e-212">Rol tanımları oluşturulur ve depolanır Not `$roles` convenience ve Okunabilirlik için değişken.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-212">Note that the role definitions are created and stored in the `$roles` variable for convenience and readability.</span></span>
<span data-ttu-id="fdf1e-213">Bunu yapmak için bir gereksinim değildir.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-213">It is not a requirement to do so.</span></span>

```powershell
$roles = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}

New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\JEAConfig.pssc -RunAsVirtualAccount -TranscriptDirectory 'C:\ProgramData\JEAConfiguration\Transcripts' -RoleDefinitions $roles -RequiredGroups @{ Or = '2FA-logon', 'smartcard-logon' }
Test-PSSessionConfigurationFile -Path .\JEAConfig.pssc # should yield True
```

## <a name="updating-session-configuration-files"></a><span data-ttu-id="fdf1e-214">Oturum yapılandırma dosyalarını güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="fdf1e-214">Updating session configuration files</span></span>

<span data-ttu-id="fdf1e-215">Kullanıcıların rollere, eşleme içeren bir JEA oturum yapılandırması özelliklerini değiştirmek gerekiyorsa, [kaydını](register-jea.md#unregistering-jea-configurations) ve [yeniden kaydettirin](register-jea.md) JEA oturum yapılandırması.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-215">If you need to change properties of a JEA session configuration, including the mapping of users to roles, you must [unregister](register-jea.md#unregistering-jea-configurations) and [re-register](register-jea.md) the JEA session configuration.</span></span>
<span data-ttu-id="fdf1e-216">JEA oturum yapılandırması yeniden kaydettiğinizde, istediğiniz değişiklikleri içeren güncelleştirilmiş bir PowerShell oturumu yapılandırma dosyası kullanın.</span><span class="sxs-lookup"><span data-stu-id="fdf1e-216">When you re-register the JEA session configuration, use an updated PowerShell session configuration file that includes your desired changes.</span></span>

## <a name="next-steps"></a><span data-ttu-id="fdf1e-217">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="fdf1e-217">Next steps</span></span>

- [<span data-ttu-id="fdf1e-218">Bir JEA yapılandırmasını Kaydet</span><span class="sxs-lookup"><span data-stu-id="fdf1e-218">Register a JEA configuration</span></span>](register-jea.md)
- [<span data-ttu-id="fdf1e-219">Yazar JEA rolleri</span><span class="sxs-lookup"><span data-stu-id="fdf1e-219">Author JEA roles</span></span>](role-capabilities.md)
