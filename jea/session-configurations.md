---
ms.date: 2017-06-12
author: rpsqrd
ms.topic: conceptual
keywords: "jea, powershell, güvenlik"
title: "JEA oturum yapılandırmaları"
ms.openlocfilehash: c475a90a59d91b074f954cfb656b00142444c052
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2018
---
# <a name="jea-session-configurations"></a><span data-ttu-id="d5ece-103">JEA oturum yapılandırmaları</span><span class="sxs-lookup"><span data-stu-id="d5ece-103">JEA Session Configurations</span></span>

> <span data-ttu-id="d5ece-104">Uygulandığı öğe: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="d5ece-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="d5ece-105">JEA uç noktası oluşturarak ve belirli bir şekilde bir PowerShell oturumu yapılandırma dosyası kaydediliyor bir sistemde kayıtlı.</span><span class="sxs-lookup"><span data-stu-id="d5ece-105">A JEA endpoint is registered on a system by creating and registering a PowerShell session configuration file in a specific way.</span></span>
<span data-ttu-id="d5ece-106">Oturum yapılandırmaları belirlemek *kimin* JEA endpoint kullanabilirsiniz ve hangi rollere erişime sahip.</span><span class="sxs-lookup"><span data-stu-id="d5ece-106">Session configurations determine *who* can use the JEA endpoint, and which role(s) they will have access to.</span></span>
<span data-ttu-id="d5ece-107">Bunlar aynı zamanda JEA oturumunda herhangi bir rolü kullanıcılar için geçerli genel ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d5ece-107">They also define global settings that apply to users of any role in the JEA session.</span></span>

<span data-ttu-id="d5ece-108">Bu konuda, bir PowerShell oturumu yapılandırma dosyası oluşturun ve JEA uç noktasını kaydetme açıklar.</span><span class="sxs-lookup"><span data-stu-id="d5ece-108">This topic describes how to create a PowerShell session configuration file and register a JEA endpoint.</span></span>

## <a name="create-a-session-configuration-file"></a><span data-ttu-id="d5ece-109">Oturum yapılandırma dosyası oluşturma</span><span class="sxs-lookup"><span data-stu-id="d5ece-109">Create a session configuration file</span></span>

<span data-ttu-id="d5ece-110">JEA uç noktasını kaydetmek için bu uç nasıl yapılandırılmalıdır belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d5ece-110">In order to register a JEA endpoint, you need to specify how that endpoint should be configured.</span></span>
<span data-ttu-id="d5ece-111">Burada, en önemli hangi kimin JEA uç noktası erişimi olması gereken olmaya biri, hangi rollerin olacak bunlar dikkate alınması gereken birçok seçenek atanabilir, hangi kimlik JEA perde arkasında kullanacağı vardır ve ne JEA uç noktanın adı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="d5ece-111">There are many options to consider here, the most important of which being who should have access to the JEA endpoint, which roles will they be assigned, which identity will JEA use under the covers, and what will be the name of the JEA endpoint.</span></span>
<span data-ttu-id="d5ece-112">Bunlar tüm tanımlanmış bir PowerShell oturumu yapılandırma dosyasında hangi .pssc uzantısı ile bir PowerShell veri dosyasını sonlandırıyor.</span><span class="sxs-lookup"><span data-stu-id="d5ece-112">These are all defined in a PowerShell session configuration file, which is a PowerShell data file ending with a .pssc extension.</span></span>

<span data-ttu-id="d5ece-113">JEA uç noktaları için bir iskelet oturum yapılandırma dosyası oluşturmak için aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d5ece-113">To create a skeleton session configuration file for JEA endpoints, run the following command.</span></span>

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> <span data-ttu-id="d5ece-114">Yalnızca en yaygın yapılandırma seçenekleri varsayılan olarak iskelet dosyasına dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="d5ece-114">Only the most common configuration options are included in the skeleton file by default.</span></span>
> <span data-ttu-id="d5ece-115">Kullanım `-Full` anahtar içinde oluşturulan PSSC tüm ilgili ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="d5ece-115">Use the `-Full` switch to include all applicable settings in the generated PSSC.</span></span>

<span data-ttu-id="d5ece-116">Herhangi bir metin düzenleyicisinde oturum yapılandırma dosyası açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d5ece-116">You can open the session configuration file in any text editor.</span></span>
<span data-ttu-id="d5ece-117">`-SessionType RestrictedRemoteServer` Alan, oturum yapılandırması için güvenli yönetim JEA tarafından kullanılacak gösterir.</span><span class="sxs-lookup"><span data-stu-id="d5ece-117">The `-SessionType RestrictedRemoteServer` field indicates that the session configuration will be used by JEA for secure management.</span></span>
<span data-ttu-id="d5ece-118">Bu şekilde yapılandırılan oturumları çalışacağı [NoLanguage modu](https://technet.microsoft.com/library/dn433292.aspx) ve yalnızca aşağıdaki 8 varsayılan komutları (ve diğer adlar) kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="d5ece-118">Sessions configured this way will operate in [NoLanguage mode](https://technet.microsoft.com/library/dn433292.aspx) and only have the following 8 default commands (and aliases) available:</span></span>

- <span data-ttu-id="d5ece-119">Clear-Host (cls, Temizle)</span><span class="sxs-lookup"><span data-stu-id="d5ece-119">Clear-Host (cls, clear)</span></span>
- <span data-ttu-id="d5ece-120">Çıkış-PSSession (exsn, çıkış)</span><span class="sxs-lookup"><span data-stu-id="d5ece-120">Exit-PSSession (exsn, exit)</span></span>
- <span data-ttu-id="d5ece-121">Get-Command (gcm)</span><span class="sxs-lookup"><span data-stu-id="d5ece-121">Get-Command (gcm)</span></span>
- <span data-ttu-id="d5ece-122">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="d5ece-122">Get-FormatData</span></span>
- <span data-ttu-id="d5ece-123">Get-Help</span><span class="sxs-lookup"><span data-stu-id="d5ece-123">Get-Help</span></span>
- <span data-ttu-id="d5ece-124">Ölçü nesnesi (ölçüm)</span><span class="sxs-lookup"><span data-stu-id="d5ece-124">Measure-Object (measure)</span></span>
- <span data-ttu-id="d5ece-125">Dışarı varsayılan</span><span class="sxs-lookup"><span data-stu-id="d5ece-125">Out-Default</span></span>
- <span data-ttu-id="d5ece-126">Select-Object (seçin)</span><span class="sxs-lookup"><span data-stu-id="d5ece-126">Select-Object (select)</span></span>

<span data-ttu-id="d5ece-127">Herhangi bir PowerShell sağlayıcısı kullanılabilir veya tüm dış (yürütülebilir dosyaları, komut dosyaları, vb.) programlardır.</span><span class="sxs-lookup"><span data-stu-id="d5ece-127">No PowerShell providers are available, nor are any external programs (executables, scripts, etc.).</span></span>

<span data-ttu-id="d5ece-128">JEA oturumu için yapılandırmak istediğiniz bazı alanlar vardır.</span><span class="sxs-lookup"><span data-stu-id="d5ece-128">There are several other fields you will want to configure for the JEA session.</span></span>
<span data-ttu-id="d5ece-129">Bunlar aşağıdaki bölümlerde ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="d5ece-129">They are covered in the following sections.</span></span>

### <a name="choose-the-jea-identity"></a><span data-ttu-id="d5ece-130">JEA kimliğini seçin</span><span class="sxs-lookup"><span data-stu-id="d5ece-130">Choose the JEA identity</span></span>

<span data-ttu-id="d5ece-131">Arka planda JEA bağlı kullanıcının komutlarını çalıştırırken kullanılacak bir kimliği (hesap) gerekir.</span><span class="sxs-lookup"><span data-stu-id="d5ece-131">Behind the scenes, JEA needs an identity (account) to use when running a connected user's commands.</span></span>
<span data-ttu-id="d5ece-132">JEA oturum yapılandırma dosyasında kullanacağı hangi kimlik karar verin.</span><span class="sxs-lookup"><span data-stu-id="d5ece-132">You decide which identity JEA will use in the session configuration file.</span></span>

#### <a name="local-virtual-account"></a><span data-ttu-id="d5ece-133">Yerel sanal hesap</span><span class="sxs-lookup"><span data-stu-id="d5ece-133">Local Virtual Account</span></span>

<span data-ttu-id="d5ece-134">Bu JEA bitiş noktası tarafından desteklenen roller tüm yerel makine yönetmek için kullanılır ve yerel yönetici hesabı komutları başarıyla çalıştırmak yeterli ise, yerel sanal hesap kullanmak için JEA yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d5ece-134">If the roles supported by this JEA endpoint are all used to manage the local machine, and a local administrator account is sufficient to run the commands succesfully, you should configure JEA to use a local virtual account.</span></span>
<span data-ttu-id="d5ece-135">Sanal hesap belirli bir kullanıcı için benzersiz ve kendi PowerShell oturumu süresince yalnızca son geçici hesaplardır.</span><span class="sxs-lookup"><span data-stu-id="d5ece-135">Virtual accounts are temporary accounts that are unique to a specific user and only last for the duration of their PowerShell session.</span></span>
<span data-ttu-id="d5ece-136">Üye sunucusu veya iş istasyonu sanal hesaplar yerel bilgisayarın ait **Yöneticiler** grup ve çoğu sistem kaynaklarına erişimi vardır.</span><span class="sxs-lookup"><span data-stu-id="d5ece-136">On a member server or workstation, virtual accounts belong to the local computer's **Administrators** group, and have access to most system resources.</span></span>
<span data-ttu-id="d5ece-137">Bir Active Directory etki alanı denetleyicisinde sanal hesaplar etki alanına ait ait **Domain Admins** grubu.</span><span class="sxs-lookup"><span data-stu-id="d5ece-137">On an Active Directory Domain Controller, virtual accounts belong to the domain's **Domain Admins** group.</span></span>

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

<span data-ttu-id="d5ece-138">Oturum yapılandırması tarafından desteklenen roller gibi geniş ayrıcalıklarına gerek duymuyorsanız, isteğe bağlı olarak sanal hesap ait olacağı güvenlik gruplarını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d5ece-138">If the roles supported by the session configuration do not require such broad privileges, you can optionally specify the security groups to which the virtual account will belong.</span></span>
<span data-ttu-id="d5ece-139">Üye sunucusu veya iş istasyonu belirtilen güvenlik grupları yerel gruplar, olmayan bir etki alanından grupları olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d5ece-139">On a member server or workstation, the specified security groups must be local groups, not groups from a domain.</span></span>

<span data-ttu-id="d5ece-140">Bir veya daha fazla güvenlik grubu belirtilirse, sanal hesap artık yerel veya etki alanı yöneticileri grubuna ait.</span><span class="sxs-lookup"><span data-stu-id="d5ece-140">When one or more security groups is specified, the virtual account will no longer belong to the local or domain administrators group.</span></span>

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```

#### <a name="group-managed-service-account"></a><span data-ttu-id="d5ece-141">Grup Yönetilen Hizmet Hesabı</span><span class="sxs-lookup"><span data-stu-id="d5ece-141">Group Managed Service Account</span></span>


<span data-ttu-id="d5ece-142">Diğer makinelerin veya web Hizmetleri gibi ağ kaynaklarına erişmek için JEA kullanıcının gerektiren senaryolar için bir grup yönetilen hizmet hesabı (gMSA) kullanmak için bir daha uygun kimliğidir.</span><span class="sxs-lookup"><span data-stu-id="d5ece-142">For scenarios requiring the JEA user to access network resources such as other machines or web services, a group managed service account (gMSA) is a more appropriate identity to use.</span></span>
<span data-ttu-id="d5ece-143">gMSA hesapları etki alanındaki herhangi bir makinede kaynaklarına karşı kimlik doğrulaması için kullanılan bir etki alanı kimlik sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d5ece-143">gMSA accounts give you a domain identity which can be used to authenticate against resources on any machine within the domain.</span></span>
<span data-ttu-id="d5ece-144">Erişmeye çalıştığınız hakları kaynaklar tarafından belirlenir. gMSA hesabı sağlar.</span><span class="sxs-lookup"><span data-stu-id="d5ece-144">The rights the gMSA account gives you is determined by the resources you are accessing.</span></span>
<span data-ttu-id="d5ece-145">Makine/Hizmet Yöneticisi Yönetici ayrıcalıkları gMSA hesabını açıkça verildi sürece tüm makineler veya hizmetler üzerinde yönetici hakları otomatik olarak olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="d5ece-145">You will not automatically have admin rights on any machines or services unless the machine/service administrator has explicitly granted the gMSA account admin privileges.</span></span>

```powershell
# Configure JEA sessions to use the gMSA account in the local computer's domain with the sAMAccountName of 'MyJEAgMSA'
GroupManagedServiceAccount = 'Domain\MyJEAgMSA'
```

<span data-ttu-id="d5ece-146">gMSA hesapları yalnızca kullanılmalıdır ağ kaynaklarına erişim olduğunda gereken birkaç nedeni:</span><span class="sxs-lookup"><span data-stu-id="d5ece-146">gMSA accounts should only be used when access to network resources are required for a few reasons:</span></span>

- <span data-ttu-id="d5ece-147">Her kullanıcı aynı Çalıştır kimlik paylaşır beri gMSA hesabı kullanırken, bir kullanıcıya eylemleri geri izlemek için daha zor olduğu.</span><span class="sxs-lookup"><span data-stu-id="d5ece-147">It is harder to trace back actions to a user when using a gMSA account since every user shares the same run-as identity.</span></span> <span data-ttu-id="d5ece-148">PowerShell oturumu dökümleri ve kullanıcılar kendi eylemleri ile ilişkilendirmek için günlükleri danışmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d5ece-148">You will need to consult PowerShell session transcripts and logs to correlate users with their actions.</span></span>

- <span data-ttu-id="d5ece-149">GMSA hesabı bağlanan kullanıcı erişimi gerekmez birçok ağ kaynaklarına erişim olabilir.</span><span class="sxs-lookup"><span data-stu-id="d5ece-149">The gMSA account may have access to many network resources which the connecting user does not need access to.</span></span> <span data-ttu-id="d5ece-150">En az ayrıcalık ilkesini izlemek için bir JEA oturumunda etkili izinleri sınırlamak her zaman deneyin.</span><span class="sxs-lookup"><span data-stu-id="d5ece-150">Always try to limit effective permissions in a JEA session to follow the principle of least privilege.</span></span>

> [!NOTE]
> <span data-ttu-id="d5ece-151">Grup yönetilen hizmet hesapları yalnızca Windows PowerShell 5.1 kullanılabilir veya daha yeni ve etki alanına katılmış makinelerde.</span><span class="sxs-lookup"><span data-stu-id="d5ece-151">Group managed service accounts are only available in Windows PowerShell 5.1 or newer and on domain-joined machines.</span></span>


#### <a name="more-information-about-run-as-users"></a><span data-ttu-id="d5ece-152">Hakkında daha fazla bilgi kullanıcı olarak çalıştırın</span><span class="sxs-lookup"><span data-stu-id="d5ece-152">More information about run as users</span></span>

<span data-ttu-id="d5ece-153">Kimlikleri ve bunlar JEA oturumu güvenlik nasıl faktör olarak çalıştır hakkında ek bilgiler bulunabilir [güvenlik konuları](security-considerations.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="d5ece-153">Additional information about run as identities and how they factor into the security of a JEA session can be found in the [security considerations](security-considerations.md) article.</span></span>

### <a name="session-transcripts"></a><span data-ttu-id="d5ece-154">Oturum dökümleri</span><span class="sxs-lookup"><span data-stu-id="d5ece-154">Session transcripts</span></span>

<span data-ttu-id="d5ece-155">Kullanıcıların oturumunu otomatik olarak kayıt dökümleri JEA oturum yapılandırma dosyasına yapılandırmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="d5ece-155">It is recommended that you configure a JEA session configuration file to automatically record transcripts of users' sessions.</span></span>
<span data-ttu-id="d5ece-156">PowerShell oturumu dökümleri, atanmış kimlik Çalıştır bağlanan kullanıcı hakkındaki bilgileri içerir ve kullanıcı tarafından komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d5ece-156">PowerShell session transcripts contain information about the connecting user, the run as identity assigned to them, and the commands run by the user.</span></span>
<span data-ttu-id="d5ece-157">Bunlar, bir sistem için belirli bir değişiklik gerçekleştiren anlamak için gereken bir denetim ekibi için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="d5ece-157">They can be useful to an auditing team who needs to understand who performed a specific change to a system.</span></span>

<span data-ttu-id="d5ece-158">Oturum yapılandırma dosyasında otomatik transcription yapılandırmak için dökümleri depolanacağı klasörün yolunu girin.</span><span class="sxs-lookup"><span data-stu-id="d5ece-158">To configure automatic transcription in the session configuration file, provide a path to a folder where the transcripts should be stored.</span></span>

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

<span data-ttu-id="d5ece-159">Belirtilen klasör, değiştirme veya silme içindeki tüm veriler kullanıcıların önlemek için yapılandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d5ece-159">The specified folder should be configured to prevent users from modifying or deleting any data in it.</span></span>
<span data-ttu-id="d5ece-160">Dökümleri, okuma ve yazma erişimi dizinine gerektiren yerel sistem hesabı tarafından klasörüne yazılır.</span><span class="sxs-lookup"><span data-stu-id="d5ece-160">Transcripts are written to the folder by the Local System account, which requires read and write access to the directory.</span></span>
<span data-ttu-id="d5ece-161">Standart kullanıcılar klasörüne erişimi olmalıdır ve güvenlik yöneticileri sınırlı sayıda dökümleri denetim erişimi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d5ece-161">Standard users should have no access to the folder, and a limited set of security administrators should have access to audit the transcripts.</span></span>

### <a name="user-drive"></a><span data-ttu-id="d5ece-162">Kullanıcı sürücü</span><span class="sxs-lookup"><span data-stu-id="d5ece-162">User drive</span></span>

<span data-ttu-id="d5ece-163">Bağlanan kullanıcıların dosyaları için/JEA uç noktası bir komut çalıştırmak için kopyalamak gerekiyorsa oturum yapılandırma dosyasındaki kullanıcı sürücü etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d5ece-163">If your connecting users will need to copy files to/from the JEA endpoint in order to run a command, you can enable the user drive in the session configuration file.</span></span>
<span data-ttu-id="d5ece-164">Kullanıcı sürücü bir [PSDrive](https://msdn.microsoft.com/powershell/scripting/getting-started/cookbooks/managing-windows-powershell-drives) bağlanan her kullanıcı için benzersiz bir klasör için eşlenmedi.</span><span class="sxs-lookup"><span data-stu-id="d5ece-164">The user drive is a [PSDrive](https://msdn.microsoft.com/powershell/scripting/getting-started/cookbooks/managing-windows-powershell-drives) that is mapped to a unique folder for each connecting user.</span></span>
<span data-ttu-id="d5ece-165">Bu klasör, bunları bunları tam dosya sistemine erişim veren veya dosya sistemi sağlayıcısı gösterme denetleyicisinden sistem dosyaları kopyalamak bir alan olarak görev yapar.</span><span class="sxs-lookup"><span data-stu-id="d5ece-165">This folder serves as a space for them to copy files to/from the system, without giving them access to the full file system or exposing the FileSystem provider.</span></span>
<span data-ttu-id="d5ece-166">Kullanıcı disk içeriği ağ bağlantısı nerede kesintiye durumlarda oturumlarında kalıcıdır.</span><span class="sxs-lookup"><span data-stu-id="d5ece-166">The user drive contents are persistent across sessions to accommodate situations where network connectivity may be interrupted.</span></span>

```powershell
MountUserDrive = $true
```

<span data-ttu-id="d5ece-167">Varsayılan olarak, kullanıcı sürücüsünde en fazla kullanıcı başına veri 50 MB depolamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="d5ece-167">By default, the user drive allows you to store a maximum of 50MB of data per user.</span></span>
<span data-ttu-id="d5ece-168">Bir kullanıcı ile tüketebileceği veri miktarını sınırlamak *UserDriveMaximumSize* alan.</span><span class="sxs-lookup"><span data-stu-id="d5ece-168">You can limit the amount of data a user can consume with the *UserDriveMaximumSize* field.</span></span>

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

<span data-ttu-id="d5ece-169">Kalıcı olması için kullanıcı sürücüde veri istemiyorsanız, zamanlanmış bir görev klasörü her gece otomatik olarak temizlemek için sistemde yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d5ece-169">If you do not want data in the user drive to be persistent, you can configure a scheduled task on the system to automatically clean up the folder every night.</span></span>

> [!NOTE]
> <span data-ttu-id="d5ece-170">Kullanıcı yalnızca Windows PowerShell 5.1 bulunan ya da daha yeni sürücüdür.</span><span class="sxs-lookup"><span data-stu-id="d5ece-170">The user drive is only available in Windows PowerShell 5.1 or newer.</span></span>

### <a name="role-definitions"></a><span data-ttu-id="d5ece-171">Rol tanımları</span><span class="sxs-lookup"><span data-stu-id="d5ece-171">Role definitions</span></span>

<span data-ttu-id="d5ece-172">Rol tanımları oturum yapılandırma dosyasında tanımlayın eşleme *kullanıcılar* için *rolleri*.</span><span class="sxs-lookup"><span data-stu-id="d5ece-172">Role definitions in a session configuration file define the mapping of *users* to *roles*.</span></span>
<span data-ttu-id="d5ece-173">Otomatik olarak onu kaydedildikten sonra her bir kullanıcı veya grup bu alana dahil JEA endpoint izni verilecektir.</span><span class="sxs-lookup"><span data-stu-id="d5ece-173">Every user or group included in this field will automatically be granted permission to the JEA endpoint when it is registered.</span></span>
<span data-ttu-id="d5ece-174">Her bir kullanıcı veya grup yalnızca bir kez anahtar hashtable olarak dahil edilebilir, ancak birden çok rol atanabilir.</span><span class="sxs-lookup"><span data-stu-id="d5ece-174">Each user or group can be included as a key in the hashtable only once, but can be assigned multiple roles.</span></span>
<span data-ttu-id="d5ece-175">Rol özelliğin adına .psrc uzantısı olmadan Rol Yetenek dosyasının adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d5ece-175">The name of the role capability should be the name of the role capability file, without the .psrc extension.</span></span>

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

<span data-ttu-id="d5ece-176">Bir kullanıcı birden fazla rol tanımı grubuna aitse, her rol için erişim elde.</span><span class="sxs-lookup"><span data-stu-id="d5ece-176">If a user belongs to more than one group in the role definition, they will get access to the roles of each.</span></span>
<span data-ttu-id="d5ece-177">İki rolleri aynı cmdlet'leri erişim izni, en fazla izne sahip parametre kümesi kullanıcıya verilecektir.</span><span class="sxs-lookup"><span data-stu-id="d5ece-177">If two roles grant access to the same cmdlets, the most permissive parameter set will be granted to the user.</span></span>

<span data-ttu-id="d5ece-178">Yerel kullanıcılar veya gruplar rol tanımları alanı belirtirken, bilgisayar adı kullandığınızdan emin olun (değil *localhost* veya *.*) ters eğik çizgi önce.</span><span class="sxs-lookup"><span data-stu-id="d5ece-178">When specifying local users or groups in the role definitions field, be sure to use the computer name (not *localhost* or *.*) before the backslash.</span></span>
<span data-ttu-id="d5ece-179">Bilgisayar adı inceleyerek denetleyebilirsiniz `$env:computername` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="d5ece-179">You can check the computer name by inspecting the `$env:computername` variable.</span></span>

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a><span data-ttu-id="d5ece-180">Rol Yetenek arama sırası</span><span class="sxs-lookup"><span data-stu-id="d5ece-180">Role capability search order</span></span>
<span data-ttu-id="d5ece-181">Yukarıdaki örnekte gösterildiği gibi rol özellikleri Rol Yetenek dosya düz adıyla (dosya adı uzantısı olmadan) başvurulur.</span><span class="sxs-lookup"><span data-stu-id="d5ece-181">As shown in the example above, role capabilities are referenced by the flat name (filename without the extension) of the role capability file.</span></span>
<span data-ttu-id="d5ece-182">Birden çok rol özellikleri varsa düz adında sisteminde PowerShell etkili Rol Yetenek dosyasını seçmek için kendi örtük arama sırası kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="d5ece-182">If multiple role capabilities are available on the system with the same flat name, PowerShell will use its implicit search order to select the effective role capability file.</span></span>
<span data-ttu-id="d5ece-183">İçinde **değil** aynı ada sahip tüm Rol Yetenek dosyaları erişim verin.</span><span class="sxs-lookup"><span data-stu-id="d5ece-183">It will **not** give access to all role capability files with the same name.</span></span>

<span data-ttu-id="d5ece-184">JEA kullanan `$env:PSModulePath` Rol Yetenek dosyaları taramak için hangi yolları belirlemek için ortam değişkeni.</span><span class="sxs-lookup"><span data-stu-id="d5ece-184">JEA uses the `$env:PSModulePath` environment variable to determine which paths to scan for role capability files.</span></span>
<span data-ttu-id="d5ece-185">Her bu yollar içinde bir "RoleCapabilities" alt klasör içeren geçerli PowerShell modülleri için JEA arar.</span><span class="sxs-lookup"><span data-stu-id="d5ece-185">Within each of those paths, JEA will look for valid PowerShell modules that contain a "RoleCapabilities" subfolder.</span></span>
<span data-ttu-id="d5ece-186">Modülleri gibi içeri aktarma ile aynı ada sahip özel rol özellikleri için Windows ile birlikte rol özellikleri JEA tercih eder.</span><span class="sxs-lookup"><span data-stu-id="d5ece-186">As with importing modules, JEA prefers role capabilities that are shipped with Windows to custom role capabilities with the same name.</span></span>
<span data-ttu-id="d5ece-187">Tüm diğer adlandırma çakışmaları için öncelik Windows (alfabetik olması garanti değil) dizindeki dosyaların numaralandırır sıraya göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="d5ece-187">For all other naming conflicts, precedence is determined by the order in which Windows enumerates the files in the directory (not guaranteed to be alphabetically).</span></span>
<span data-ttu-id="d5ece-188">İstenen eşleşen ilk Rol Yetenek dosyası bulundu adı bağlanan kullanıcı için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d5ece-188">The first role capability file found that matches the desired name will be used for the connecting user.</span></span>

<span data-ttu-id="d5ece-189">Rol Yetenek arama sırası iki belirleyici değil veya daha fazla rol özellikleri aynı adı paylaşan beri olan **önemle tavsiye** rol özellikleri makinenize benzersiz adlara sahip olun.</span><span class="sxs-lookup"><span data-stu-id="d5ece-189">Since the role capability search order is not deterministic when two or more role capabilities share the same name, it is **strongly recommended** that you ensure role capabilities have unique names on your machine.</span></span>

### <a name="conditional-access-rules"></a><span data-ttu-id="d5ece-190">Koşullu erişim kuralları</span><span class="sxs-lookup"><span data-stu-id="d5ece-190">Conditional access rules</span></span>

<span data-ttu-id="d5ece-191">Otomatik olarak tüm kullanıcılar ve gruplar RoleDefinitions alanında bulunan JEA Uç noktalara erişimi verilir.</span><span class="sxs-lookup"><span data-stu-id="d5ece-191">All users and groups included in the RoleDefinitions field are automatically granted access to JEA endpoints.</span></span>
<span data-ttu-id="d5ece-192">Koşullu erişim kuralları, bu erişim daraltın ve kullanıcıların, bunlar atanan rollerden etkilemeyen ek güvenlik gruplarına ait zorunlu olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="d5ece-192">Conditional access rules allow you to refine this access and require users to belong to additional security groups which do not impact the roles which they are assigned.</span></span>
<span data-ttu-id="d5ece-193">Bu bir "biraz zaman" ayrıcalıklı tümleştirmek istediğiniz durumlarda yararlı olabilir erişim yönetimi çözümü, akıllı kart kimlik doğrulaması veya başka bir çok faktörlü kimlik doğrulama çözümü JEA ile.</span><span class="sxs-lookup"><span data-stu-id="d5ece-193">This can be useful if you want to integrate a "just in time" privileged access management solution, smartcard authentication, or other multifactor authentication solution with JEA.</span></span>

<span data-ttu-id="d5ece-194">Koşullu erişim kuralları, bir oturum yapılandırma dosyası RequiredGroups alanında tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="d5ece-194">Conditional access rules are defined in the RequiredGroups field in a session configuration file.</span></span>
<span data-ttu-id="d5ece-195">Burada, kullanır (isteğe bağlı olarak iç içe) bir hashtable sağlayabilir 'Ve' ve 'Veya' anahtarları kurallarınızı oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="d5ece-195">There, you can provide a hashtable (optionally nested) that uses 'And' and 'Or' keys to construct your rules.</span></span>
<span data-ttu-id="d5ece-196">Bu alan yararlanmak nasıl bazı örnekleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="d5ece-196">Here are some examples of how to leverage this field:</span></span>

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
> <span data-ttu-id="d5ece-197">Koşullu erişim kuralları yalnızca Windows PowerShell 5.1 bulunan ya da daha yeni.</span><span class="sxs-lookup"><span data-stu-id="d5ece-197">Conditional access rules are only available in Windows PowerShell 5.1 or newer.</span></span>

### <a name="other-properties"></a><span data-ttu-id="d5ece-198">Diğer özellikler</span><span class="sxs-lookup"><span data-stu-id="d5ece-198">Other properties</span></span>
<span data-ttu-id="d5ece-199">Oturum yapılandırma dosyalarını bir rol özelliği dosyası yalnızca farklı komutları bağlanan kullanıcılara erişim vermek özelliği olmadan yapabilirsiniz her şeyi da yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d5ece-199">Session configuration files can also do everything a role capability file can do, just without the ability to give connecting users access to different commands.</span></span>
<span data-ttu-id="d5ece-200">Tüm kullanıcıların belirli cmdlet'ler, İşlevler veya sağlayıcıları erişmesine izin vermek istiyorsanız, bunu yapabilirsiniz sağ oturum yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="d5ece-200">If you want to allow all users access to specific cmdlets, functions, or providers, you can do so right in the session configuration file.</span></span>
<span data-ttu-id="d5ece-201">Desteklenen özellikler oturum yapılandırma dosyasında tam listesi için çalıştırın `Get-Help New-PSSessionConfigurationFile -Full`.</span><span class="sxs-lookup"><span data-stu-id="d5ece-201">For a full list of supported properties in the session configuration file, run `Get-Help New-PSSessionConfigurationFile -Full`.</span></span>

## <a name="testing-a-session-configuration-file"></a><span data-ttu-id="d5ece-202">Bir oturum yapılandırma dosyası test etme</span><span class="sxs-lookup"><span data-stu-id="d5ece-202">Testing a session configuration file</span></span>

<span data-ttu-id="d5ece-203">Bir oturum Yapılandırması kullanılarak test [Test PSSessionConfigurationFile](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="d5ece-203">You can test a session configuration using the [Test-PSSessionConfigurationFile](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet.</span></span>
<span data-ttu-id="d5ece-204">El ile sözdizimi doğru olduğundan emin olmak için bir metin düzenleyicisi kullanarak pssc dosyayı düzenlerseniz, oturum yapılandırma dosyanızı test önerilir.</span><span class="sxs-lookup"><span data-stu-id="d5ece-204">It is strongly recommended that you test your session configuration file if you have edited the pssc file manually using a text editor to ensure the syntax is correct.</span></span>
<span data-ttu-id="d5ece-205">Bir oturum yapılandırma dosyası bu test geçemezse, sistemde başarıyla kaydedilmesi mümkün olmaz.</span><span class="sxs-lookup"><span data-stu-id="d5ece-205">If a session configuration file does not pass this test, it will not be able to be successfully registered on the system.</span></span>

## <a name="sample-session-configuration-file"></a><span data-ttu-id="d5ece-206">Örnek oturum yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="d5ece-206">Sample session configuration file</span></span>

<span data-ttu-id="d5ece-207">Aşağıda nasıl oluşturulacağı ve bir oturum yapılandırması doğrulamak için JEA gösteren tam bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d5ece-207">Below is a complete example showing how to create and validate a session configuration for JEA.</span></span>
<span data-ttu-id="d5ece-208">Rol tanımları oluşturulur ve depolanır Not `$roles` kolaylık sağlamak ve Okunabilirlik için değişken.</span><span class="sxs-lookup"><span data-stu-id="d5ece-208">Note that the role definitions are created and stored in the `$roles` variable for convenience and readability.</span></span>
<span data-ttu-id="d5ece-209">Bunu yapmak için zorunlu değildir.</span><span class="sxs-lookup"><span data-stu-id="d5ece-209">It is not a requirement to do so.</span></span>

```powershell
$roles = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}

New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\JEAConfig.pssc -RunAsVirtualAccount -TranscriptDirectory 'C:\ProgramData\JEAConfiguration\Transcripts' -RoleDefinitions $roles -RequiredGroups @{ Or = '2FA-logon', 'smartcard-logon' }
Test-PSSessionConfigurationFile -Path .\JEAConfig.pssc # should yield True
```

## <a name="updating-session-configuration-files"></a><span data-ttu-id="d5ece-210">Oturum yapılandırma dosyaları güncelleştiriliyor</span><span class="sxs-lookup"><span data-stu-id="d5ece-210">Updating session configuration files</span></span>

<span data-ttu-id="d5ece-211">Rolleri, kullanıcılara eşleme dahil olmak üzere bir JEA oturum yapılandırmasının özelliklerini değiştirmeniz gerekiyorsa, gerekir [kaydı](register-jea.md#unregistering-jea-configurations) ve [yeniden kaydettirin](register-jea.md) JEA oturum yapılandırması.</span><span class="sxs-lookup"><span data-stu-id="d5ece-211">If you need to change properties of a JEA session configuration, including the mapping of users to roles, you must [unregister](register-jea.md#unregistering-jea-configurations) and [re-register](register-jea.md) the JEA session configuration.</span></span>
<span data-ttu-id="d5ece-212">JEA oturum yapılandırmasını yeniden kaydettiğinizde, istediğiniz değişiklikleri içeren güncelleştirilmiş bir PowerShell oturumu yapılandırma dosyası kullanın.</span><span class="sxs-lookup"><span data-stu-id="d5ece-212">When you re-register the JEA session configuration, use an updated PowerShell session configuration file that includes your desired changes.</span></span>

## <a name="next-steps"></a><span data-ttu-id="d5ece-213">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="d5ece-213">Next steps</span></span>

- [<span data-ttu-id="d5ece-214">JEA yapılandırma kaydetme</span><span class="sxs-lookup"><span data-stu-id="d5ece-214">Register a JEA configuration</span></span>](register-jea.md)
- [<span data-ttu-id="d5ece-215">Yazar JEA rolleri</span><span class="sxs-lookup"><span data-stu-id="d5ece-215">Author JEA roles</span></span>](role-capabilities.md)

