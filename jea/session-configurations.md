---
ms.date: 07/10/2019
keywords: jea, powershell, güvenlik
title: JEA oturum yapılandırmaları
ms.openlocfilehash: 650d0d11ef13605847d0822249e29e3491180629
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726556"
---
# <a name="jea-session-configurations"></a><span data-ttu-id="4e3b1-103">JEA oturum yapılandırmaları</span><span class="sxs-lookup"><span data-stu-id="4e3b1-103">JEA Session Configurations</span></span>

<span data-ttu-id="4e3b1-104">Bir JEA uç noktası oluşturma ve bir PowerShell oturumu yapılandırma dosyası kaydedilirken bir sistemde kayıtlı.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-104">A JEA endpoint is registered on a system by creating and registering a PowerShell session configuration file.</span></span> <span data-ttu-id="4e3b1-105">JEA uç noktası kullanan ve hangi rollerin erişimleri oturum yapılandırmaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-105">Session configurations define who can use the JEA endpoint and which roles they have access to.</span></span> <span data-ttu-id="4e3b1-106">Bunlar ayrıca JEA oturumun tüm kullanıcılar için geçerli genel ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-106">They also define global settings that apply to all users of the JEA session.</span></span>

## <a name="create-a-session-configuration-file"></a><span data-ttu-id="4e3b1-107">Oturum yapılandırma dosyası oluşturma</span><span class="sxs-lookup"><span data-stu-id="4e3b1-107">Create a session configuration file</span></span>

<span data-ttu-id="4e3b1-108">Bir JEA uç noktasını kaydetmek için uç noktanın nasıl yapılandırıldığını belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-108">To register a JEA endpoint, you must specify how that endpoint is configured.</span></span> <span data-ttu-id="4e3b1-109">Dikkate alınması gereken birçok seçenek vardır.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-109">There are many options to consider.</span></span> <span data-ttu-id="4e3b1-110">En önemli Seçenekler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="4e3b1-110">The most important options are:</span></span>

- <span data-ttu-id="4e3b1-111">JEA uç noktası erişimi kimler</span><span class="sxs-lookup"><span data-stu-id="4e3b1-111">Who has access to the JEA endpoint</span></span>
- <span data-ttu-id="4e3b1-112">Hangi rollerin bunlar atanması</span><span class="sxs-lookup"><span data-stu-id="4e3b1-112">Which roles they be assigned</span></span>
- <span data-ttu-id="4e3b1-113">Hangi kimlik JEA perde kullanır.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-113">Which identity JEA uses under the covers</span></span>
- <span data-ttu-id="4e3b1-114">JEA uç noktası adı</span><span class="sxs-lookup"><span data-stu-id="4e3b1-114">The name of the JEA endpoint</span></span>

<span data-ttu-id="4e3b1-115">Bu seçenekler, bir PowerShell veri dosyasında tanımlanan bir `.pssc` uzantısı bir PowerShell oturumu yapılandırma dosyası bilinir.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-115">These options are defined in a PowerShell data file with a `.pssc` extension known as a PowerShell session configuration file.</span></span> <span data-ttu-id="4e3b1-116">Oturum yapılandırma dosyası, herhangi bir metin düzenleyicisi kullanarak düzenlenebilir.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-116">The session configuration file can be edited using any text editor.</span></span>

<span data-ttu-id="4e3b1-117">Boş şablon yapılandırma dosyasını oluşturmak için aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-117">Run the following command to create a blank template configuration file.</span></span>

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> <span data-ttu-id="4e3b1-118">En yaygın yapılandırma seçenekleri varsayılan olarak şablon dosyasına dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-118">Only the most common configuration options are included in the template file by default.</span></span> <span data-ttu-id="4e3b1-119">Kullanım `-Full` geçme içinde oluşturulan PSSC tüm ilgili ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-119">Use the `-Full` switch to include all applicable settings in the generated PSSC.</span></span>

<span data-ttu-id="4e3b1-120">`-SessionType RestrictedRemoteServer` Alanının oturum yapılandırması tarafından JEA güvenli yönetimi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-120">The `-SessionType RestrictedRemoteServer` field indicates that the session configuration is used by JEA for secure management.</span></span> <span data-ttu-id="4e3b1-121">Bu tür oturumları olarak çalışır **NoLanguage** modu ve yalnızca aşağıdaki varsayılan komutları (ve diğer adları) erişimi:</span><span class="sxs-lookup"><span data-stu-id="4e3b1-121">Sessions of this type operate in **NoLanguage** mode and only have access to the following default commands (and aliases):</span></span>

- <span data-ttu-id="4e3b1-122">Clear-Host (cls, Temizle)</span><span class="sxs-lookup"><span data-stu-id="4e3b1-122">Clear-Host (cls, clear)</span></span>
- <span data-ttu-id="4e3b1-123">Çıkış-PSSession (exsn, çıkış)</span><span class="sxs-lookup"><span data-stu-id="4e3b1-123">Exit-PSSession (exsn, exit)</span></span>
- <span data-ttu-id="4e3b1-124">Get-Command (gcm)</span><span class="sxs-lookup"><span data-stu-id="4e3b1-124">Get-Command (gcm)</span></span>
- <span data-ttu-id="4e3b1-125">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="4e3b1-125">Get-FormatData</span></span>
- <span data-ttu-id="4e3b1-126">Get-Help</span><span class="sxs-lookup"><span data-stu-id="4e3b1-126">Get-Help</span></span>
- <span data-ttu-id="4e3b1-127">Ölçü nesnesi (ölçü)</span><span class="sxs-lookup"><span data-stu-id="4e3b1-127">Measure-Object (measure)</span></span>
- <span data-ttu-id="4e3b1-128">Varsayılan dışarı</span><span class="sxs-lookup"><span data-stu-id="4e3b1-128">Out-Default</span></span>
- <span data-ttu-id="4e3b1-129">Select-Object (Seç)</span><span class="sxs-lookup"><span data-stu-id="4e3b1-129">Select-Object (select)</span></span>

<span data-ttu-id="4e3b1-130">PowerShell yok sağlayıcıları kullanılabilir ya da herhangi bir dış (yürütülebilir dosyalar veya betikler) programlardır.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-130">No PowerShell providers are available, nor are any external programs (executables or scripts).</span></span>

<span data-ttu-id="4e3b1-131">Dil modları hakkında daha fazla bilgi için bkz. [about_Language_modes](/powershell/module/microsoft.powershell.core/about/about_language_modes).</span><span class="sxs-lookup"><span data-stu-id="4e3b1-131">For more information about language modes, see [about_Language_modes](/powershell/module/microsoft.powershell.core/about/about_language_modes).</span></span>

### <a name="choose-the-jea-identity"></a><span data-ttu-id="4e3b1-132">JEA kimliğini seçin</span><span class="sxs-lookup"><span data-stu-id="4e3b1-132">Choose the JEA identity</span></span>

<span data-ttu-id="4e3b1-133">Arka planda JEA bağlı kullanıcının komutlarını çalıştırırken kullanılacak bir kimliği (hesap) gerekir.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-133">Behind the scenes, JEA needs an identity (account) to use when running a connected user's commands.</span></span>
<span data-ttu-id="4e3b1-134">JEA oturum yapılandırma dosyasında kullanan hangi kimlik tanımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-134">You define which identity JEA uses in the session configuration file.</span></span>

#### <a name="local-virtual-account"></a><span data-ttu-id="4e3b1-135">Yerel sanal hesap</span><span class="sxs-lookup"><span data-stu-id="4e3b1-135">Local Virtual Account</span></span>

<span data-ttu-id="4e3b1-136">JEA uç noktası için tanımlanan tüm rolleri yerel makine yönetmek için kullanılır ve yerel yönetici hesabı başarıyla komutları çalıştırmak yeterli yerel sanal hesaplar yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-136">Local virtual accounts are useful when all roles defined for the JEA endpoint are used to manage the local machine and a local administrator account is sufficient to run the commands successfully.</span></span>
<span data-ttu-id="4e3b1-137">Belirli bir kullanıcı için benzersiz ve kendi PowerShell oturumu süresi için yalnızca son geçici hesaplarının sanal hesaplarıdır.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-137">Virtual accounts are temporary accounts that are unique to a specific user and only last for the duration of their PowerShell session.</span></span> <span data-ttu-id="4e3b1-138">Üye sunucu veya iş istasyonunun Sanal hesaplar yerel bilgisayarın ait **Yöneticiler** grubu.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-138">On a member server or workstation, virtual accounts belong to the local computer's **Administrators** group.</span></span> <span data-ttu-id="4e3b1-139">Bir Active Directory etki alanı denetleyicisinde etki alanı için sanal hesaplar ait **Domain Admins** grubu.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-139">On an Active Directory Domain Controller, virtual accounts belong to the domain's **Domain Admins** group.</span></span>

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

<span data-ttu-id="4e3b1-140">Oturum yapılandırması tarafından tanımlanan rolleri tam yönetici ayrıcalığı gerektirmeyen sanal hesap ait olacak güvenlik gruplarını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-140">If the roles defined by the session configuration don't require full administrative privilege, you can specify the security groups to which the virtual account will belong.</span></span> <span data-ttu-id="4e3b1-141">Üye sunucu veya iş istasyonunun belirli güvenlik grupları yerel gruplar, bir etki alanından grupları değil olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-141">On a member server or workstation, the specified security groups must be local groups, not groups from a domain.</span></span>

<span data-ttu-id="4e3b1-142">Bir veya daha fazla güvenlik grubu belirtildiğinde, sanal hesap yerel veya etki alanı yöneticileri grubuna atanmadı.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-142">When one or more security groups are specified, the virtual account isn't assigned to the local or domain administrators group.</span></span>

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```

> [!NOTE]
> <span data-ttu-id="4e3b1-143">Sanal hesaplar, yerel sunucu güvenlik ilkesini içinde bir hizmet olarak oturum açma geçici olarak verilir.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-143">Virtual accounts are temporarily granted the Logon as a service right in the local server security policy.</span></span> <span data-ttu-id="4e3b1-144">Belirtilen VirtualAccountGroups birini zaten ilkesinde bu hak verilmemişse, tek tek sanal hesap artık eklendi ve ilkeden kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-144">If one of the VirtualAccountGroups specified has already been granted this right in the policy, the individual virtual account will no longer be added and removed from the policy.</span></span> <span data-ttu-id="4e3b1-145">Bu, burada etki alanı denetleyicisi güvenlik ilkesi uyarlamaları yakından denetlendiği etki alanı denetleyicileri gibi senaryolarda yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-145">This can be useful in scenarios such as domain controllers where revisions to the domain controller security policy are closely audited.</span></span> <span data-ttu-id="4e3b1-146">Bu seçenek yalnızca Kasım 2018'den Windows Server 2016 veya sonraki toplama ve Windows Server 2019 Ocak 2019 ile'veya sonraki toplama kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-146">This is only available in Windows Server 2016 with the November 2018 or later rollup and Windows Server 2019 with the January 2019 or later rollup.</span></span>

#### <a name="group-managed-service-account"></a><span data-ttu-id="4e3b1-147">Grup yönetilen hizmet hesabı</span><span class="sxs-lookup"><span data-stu-id="4e3b1-147">Group-managed service account</span></span>

<span data-ttu-id="4e3b1-148">Grup yönetilen hizmet hesabı (GMSA) JEA kullanıcıların dosya paylaşımları ve web Hizmetleri gibi ağ kaynaklarına erişmek gerektiğinde kullanmak için uygun bir kimliği var.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-148">A group-managed service account (GMSA) is the appropriate identity to use when JEA users need to access network resources such as file shares and web services.</span></span> <span data-ttu-id="4e3b1-149">Gmsa'lar etki alanındaki herhangi bir makinede kaynakları ile kimlik doğrulaması için kullanılan bir etki alanı kimliği verir.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-149">GMSAs give you a domain identity that is used to authenticate with resources on any machine within the domain.</span></span> <span data-ttu-id="4e3b1-150">Kaynaklar tarafından belirlenen bir GMSA sağladığı hakları eriştiğiniz.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-150">The rights that a GMSA provides are determined by the resources you're accessing.</span></span> <span data-ttu-id="4e3b1-151">Makine veya Hizmet Yöneticisi gmsa'nın bu hakları açıkça vermedikçe tüm makineler veya hizmetler üzerinde yönetici haklarına sahip değilsiniz.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-151">You don't have admin rights on any machines or services unless the machine or service administrator has explicitly granted those rights to the GMSA.</span></span>

```powershell
# Configure JEA sessions to use the GMSA in the local computer's domain
# with the sAMAccountName of 'MyJEAGMSA'
GroupManagedServiceAccount = 'Domain\MyJEAGMSA'
```

<span data-ttu-id="4e3b1-152">Gmsa'lar yalnızca gerekli olduğunda kullanılmalıdır:</span><span class="sxs-lookup"><span data-stu-id="4e3b1-152">GMSAs should only be used when necessary:</span></span>

- <span data-ttu-id="4e3b1-153">Bir gmsa'yı kullanarak bir kullanıcıya eylemleri geri izleme zordur.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-153">It's difficult to trace back actions to a user when using a GMSA.</span></span> <span data-ttu-id="4e3b1-154">Her kullanıcı Çalıştır aynı kimliği paylaşıyor.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-154">Every user shares the same run-as identity.</span></span> <span data-ttu-id="4e3b1-155">PowerShell oturumu dökümleri ve bireysel kullanıcıların eylemlerini ile ilişkilendirmek için günlükleri gözden geçirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-155">You must review PowerShell session transcripts and logs to correlate individual users with their actions.</span></span>

- <span data-ttu-id="4e3b1-156">GMSA bağlanan kullanıcının erişmesi gereken olmayan birçok ağ kaynaklarına erişiminiz olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-156">The GMSA may have access to many network resources that the connecting user doesn't need access to.</span></span> <span data-ttu-id="4e3b1-157">En düşük öncelik ilkesini izlemek için bir JEA oturumunda etkili izinleri sınırlamak her zaman deneyin.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-157">Always try to limit effective permissions in a JEA session to follow the principle of least privilege.</span></span>

> [!NOTE]
> <span data-ttu-id="4e3b1-158">Grup yönetilen hizmet hesapları yalnızca PowerShell 5.1 kullanarak etki alanına katılmış makinelerde veya yeni kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-158">Group managed service accounts are only available on domain-joined machines using PowerShell 5.1 or newer.</span></span>

<span data-ttu-id="4e3b1-159">Bir JEA oturum güvenliğini sağlama hakkında daha fazla bilgi için bkz. [güvenlik konuları](security-considerations.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-159">For more information about securing a JEA session, see the [security considerations](security-considerations.md) article.</span></span>

### <a name="session-transcripts"></a><span data-ttu-id="4e3b1-160">Oturum dökümleri</span><span class="sxs-lookup"><span data-stu-id="4e3b1-160">Session transcripts</span></span>

<span data-ttu-id="4e3b1-161">Bir JEA uç noktası için kullanıcıların oturumu otomatik olarak kayıt dökümleri yapılandırma önerilir.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-161">It's recommended that you configure a JEA endpoint to automatically record transcripts of users' sessions.</span></span> <span data-ttu-id="4e3b1-162">PowerShell oturumu dökümleri bağlanan kullanıcının, farklı çalıştır kimlik atanmamış hakkındaki bilgileri içerir ve kullanıcı tarafından komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-162">PowerShell session transcripts contain information about the connecting user, the run as identity assigned to them, and the commands run by the user.</span></span> <span data-ttu-id="4e3b1-163">Bunlar, bir sistemde belirli bir değişikliği kimin yaptığını anlamak için gereken bir denetim takımı yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-163">They can be useful to an auditing team who needs to understand who made a specific change to a system.</span></span>

<span data-ttu-id="4e3b1-164">Oturum yapılandırma dosyasında otomatik döküm yapılandırmak için dökümleri nerede depolanması gereken bir klasöre bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-164">To configure automatic transcription in the session configuration file, provide a path to a folder where the transcripts should be stored.</span></span>

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

<span data-ttu-id="4e3b1-165">Dökümler tarafından belirtilen klasöre yazılır **yerel sistem** hesabı okuma ve dizine yazma erişimi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-165">Transcripts are written to the folder by the **Local System** account, which requires read and write access to the directory.</span></span> <span data-ttu-id="4e3b1-166">Standart kullanıcılar klasörüne erişimi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-166">Standard users should have no access to the folder.</span></span> <span data-ttu-id="4e3b1-167">Dökümler denetim erişimi güvenlik yöneticileri sayısını sınırlayın.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-167">Limit the number of security administrators that have access to audit the transcripts.</span></span>

### <a name="user-drive"></a><span data-ttu-id="4e3b1-168">Kullanıcı sürücü</span><span class="sxs-lookup"><span data-stu-id="4e3b1-168">User drive</span></span>

<span data-ttu-id="4e3b1-169">Bağlanan kullanıcıların veya JEA uç noktasından dosyaları kopyalamak gerekiyorsa, oturum yapılandırma dosyasındaki kullanıcı sürücü etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-169">If your connecting users need to copy files to or from the JEA endpoint, you can enable the user drive in the session configuration file.</span></span> <span data-ttu-id="4e3b1-170">Kullanıcı sürücüdür bir **PSDrive** bağlanan her kullanıcı için benzersiz bir klasöre eşlendi.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-170">The user drive is a **PSDrive** that is mapped to a unique folder for each connecting user.</span></span> <span data-ttu-id="4e3b1-171">Bu klasör, dosyaları ya da sistemden tam dosya sistemine erişim vermeden veya dosya sistemi sağlayıcısı gösterme kopyalamak kullanıcıların sağlar.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-171">This folder allows users to copy files to or from the system without giving them access to the full file system or exposing the FileSystem provider.</span></span> <span data-ttu-id="4e3b1-172">Kullanıcı sürücü içeriğini burada ağ bağlantısı kesilebilir durumlarda oturumları arasında kalıcıdır.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-172">The user drive contents are persistent across sessions to accommodate situations where network connectivity may be interrupted.</span></span>

```powershell
MountUserDrive = $true
```

<span data-ttu-id="4e3b1-173">Varsayılan olarak, kullanıcı sürücüsünde en fazla kullanıcı başına veri 50 MB'ın depolamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-173">By default, the user drive allows you to store a maximum of 50MB of data per user.</span></span> <span data-ttu-id="4e3b1-174">Bir kullanıcı ile kullanabileceği veri miktarını sınırlamak *UserDriveMaximumSize* alan.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-174">You can limit the amount of data a user can consume with the *UserDriveMaximumSize* field.</span></span>

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

<span data-ttu-id="4e3b1-175">Verilerin kalıcı olmasını kullanıcı sürücüsündeki istemiyorsanız, sistemde klasörü her gece otomatik olarak temizlemek için zamanlanmış bir görev yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-175">If you don't want data in the user drive to be persistent, you can configure a scheduled task on the system to automatically clean up the folder every night.</span></span>

> [!NOTE]
> <span data-ttu-id="4e3b1-176">Kullanıcı yalnızca PowerShell 5.1 bulunan ya da daha yeni sürücüdür.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-176">The user drive is only available in PowerShell 5.1 or newer.</span></span>

<span data-ttu-id="4e3b1-177">PSDrives hakkında daha fazla bilgi için bkz: [yönetme PowerShell sürücüleri](/powershell/scripting/samples/managing-windows-powershell-drives).</span><span class="sxs-lookup"><span data-stu-id="4e3b1-177">For more information about PSDrives, see [Managing PowerShell drives](/powershell/scripting/samples/managing-windows-powershell-drives).</span></span>

### <a name="role-definitions"></a><span data-ttu-id="4e3b1-178">Rol tanımları</span><span class="sxs-lookup"><span data-stu-id="4e3b1-178">Role definitions</span></span>

<span data-ttu-id="4e3b1-179">Rol tanımları oturum yapılandırma dosyasında tanımlama eşleme **kullanıcılar** için **rolleri**.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-179">Role definitions in a session configuration file define the mapping of **users** to **roles**.</span></span> <span data-ttu-id="4e3b1-180">Kaydedildiğinde her kullanıcı veya grup bu alanda bulunan JEA uç noktasına izin verilir.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-180">Every user or group included in this field is granted permission to the JEA endpoint when it's registered.</span></span>
<span data-ttu-id="4e3b1-181">Her bir kullanıcı veya grubu yalnızca bir kez anahtar karma tablosu olarak dahil edilebilir, ancak birden çok rol atanabilir.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-181">Each user or group can be included as a key in the hashtable only once, but can be assigned multiple roles.</span></span> <span data-ttu-id="4e3b1-182">Rol özelliğin adına rolü özelliği dosyasının adı olmadan olmalıdır `.psrc` uzantısı.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-182">The name of the role capability should be the name of the role capability file, without the `.psrc` extension.</span></span>

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

<span data-ttu-id="4e3b1-183">Bir kullanıcı birden fazla rol tanımı grubuna dahilse, her rol erişim elde edin.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-183">If a user belongs to more than one group in the role definition, they get access to the roles of each.</span></span> <span data-ttu-id="4e3b1-184">İki rol aynı cmdlet'lere izin verdiğinizde, en esnek parametre kümesi kullanıcıya verilir.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-184">When two roles grant access to the same cmdlets, the most permissive parameter set is granted to the user.</span></span>

<span data-ttu-id="4e3b1-185">Yerel kullanıcı veya grup rol tanımları alanını belirtirken, bilgisayar adı kullanmadığınızdan emin olması **localhost** veya joker karakterler.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-185">When specifying local users or groups in the role definitions field, be sure to use the computer name, not **localhost** or wildcards.</span></span> <span data-ttu-id="4e3b1-186">Bilgisayar adı inceleyerek denetleyebilirsiniz `$env:COMPUTERNAME` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-186">You can check the computer name by inspecting the `$env:COMPUTERNAME` variable.</span></span>

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a><span data-ttu-id="4e3b1-187">Rol özellik arama sırası</span><span class="sxs-lookup"><span data-stu-id="4e3b1-187">Role capability search order</span></span>

<span data-ttu-id="4e3b1-188">Yukarıdaki örnekte gösterildiği gibi rol işlevleri rolü özelliği dosyasının temel adı tarafından başvurulur.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-188">As shown in the example above, role capabilities are referenced by the base name of the role capability file.</span></span> <span data-ttu-id="4e3b1-189">Temel dosya adı uzantısı olmadan dosya adıdır.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-189">The base name of a file is the filename without the extension.</span></span> <span data-ttu-id="4e3b1-190">PowerShell, örtük arama sırası sistem aynı ada sahip birden çok rol özellikleri mevcuttur, etkin bir rol özelliği dosyayı seçmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-190">If multiple role capabilities are available on the system with the same name, PowerShell uses its implicit search order to select the effective role capability file.</span></span> <span data-ttu-id="4e3b1-191">JEA mu **değil** aynı ada sahip tüm rol özellik dosyaları için erişim verin.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-191">JEA does **not** give access to all role capability files with the same name.</span></span>

<span data-ttu-id="4e3b1-192">Jea'yı kullanan `$env:PSModulePath` rol özellik dosyaları taramak için hangi yolları belirlemek için ortam değişkeni.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-192">JEA uses the `$env:PSModulePath` environment variable to determine which paths to scan for role capability files.</span></span> <span data-ttu-id="4e3b1-193">Her bu yollar içinde bir "RoleCapabilities" alt klasör içeren geçerli PowerShell modülleri için JEA arar.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-193">Within each of those paths, JEA looks for valid PowerShell modules that contain a "RoleCapabilities" subfolder.</span></span> <span data-ttu-id="4e3b1-194">JEA modülleri alma gibi Windows ile aynı ada sahip özel rol özellikleri için sağlanan rol işlevleri tercih eder.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-194">As with importing modules, JEA prefers role capabilities that are shipped with Windows to custom role capabilities with the same name.</span></span>

<span data-ttu-id="4e3b1-195">Tüm diğer adlandırma çakışmaları için öncelik, Windows dizinde dosyaları listeler sıraya göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-195">For all other naming conflicts, precedence is determined by the order in which Windows enumerates the files in the directory.</span></span> <span data-ttu-id="4e3b1-196">Sipariş alfabetik olmasını garanti yoktur.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-196">The order isn't guaranteed to be alphabetical.</span></span> <span data-ttu-id="4e3b1-197">Belirtilen eşleşen ilk rol özellik dosyası bulunamadı. adı bağlanan kullanıcı için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-197">The first role capability file found that matches the specified name is used for the connecting user.</span></span> <span data-ttu-id="4e3b1-198">Rol özellik arama beri sırası belirlenimci değildir, bu **önemle tavsiye** rol işlevleri benzersiz dosya adları vardır.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-198">Since the role capability search order isn't deterministic, it's **strongly recommended** that role capabilities have unique filenames.</span></span>

### <a name="conditional-access-rules"></a><span data-ttu-id="4e3b1-199">Koşullu erişim kuralları</span><span class="sxs-lookup"><span data-stu-id="4e3b1-199">Conditional access rules</span></span>

<span data-ttu-id="4e3b1-200">Tüm kullanıcıları ve grupları dahil **RoleDefinitions** alan JEA uç noktalarına erişimi otomatik olarak verilir.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-200">All users and groups included in the **RoleDefinitions** field are automatically granted access to JEA endpoints.</span></span> <span data-ttu-id="4e3b1-201">Koşullu erişim kuralları, bu erişimi iyileştirin ve kendisine atanmış oldukları roller etkisini ek güvenlik gruplarına ait gerektirmek olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-201">Conditional access rules allow you to refine this access and require users to belong to additional security groups that don't impact the roles to which they're assigned.</span></span> <span data-ttu-id="4e3b1-202">Just-ın-time ayrıcalıklı erişim yönetimi çözümü, akıllı kart kimlik doğrulaması veya diğer çok faktörlü kimlik doğrulama çözümü JEA ile tümleştirmek istediğiniz durumlarda kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-202">This is useful when you want to integrate a just-in-time privileged access management solution, smartcard authentication, or other multifactor authentication solution with JEA.</span></span>

<span data-ttu-id="4e3b1-203">Koşullu erişim kuralları, bir oturum yapılandırması dosyasını RequiredGroups alanında tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-203">Conditional access rules are defined in the RequiredGroups field in a session configuration file.</span></span>
<span data-ttu-id="4e3b1-204">Kullanan bir hashtable (iç içe isteğe bağlı olarak) sağlar, 'Ve' ve 'Veya' anahtarlar kurallarınızı oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-204">There, you can provide a hashtable (optionally nested) that uses 'And' and 'Or' keys to construct your rules.</span></span> <span data-ttu-id="4e3b1-205">Bu alan ilişkin bazı örnekler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="4e3b1-205">Here are some examples of how to use this field:</span></span>

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
> <span data-ttu-id="4e3b1-206">Koşullu erişim kuralları yalnızca PowerShell 5.1 bulunan ya da daha yeni.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-206">Conditional access rules are only available in PowerShell 5.1 or newer.</span></span>

### <a name="other-properties"></a><span data-ttu-id="4e3b1-207">Diğer özellikler</span><span class="sxs-lookup"><span data-stu-id="4e3b1-207">Other properties</span></span>

<span data-ttu-id="4e3b1-208">Oturum yapılandırma dosyalarını da rol özellik dosyası için farklı komutlar bağlantı kullanıcı erişimi vermek için yalnızca özelliği olmadan yapabileceği her şeyi yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-208">Session configuration files can also do everything a role capability file can do, just without the ability to give connecting users access to different commands.</span></span> <span data-ttu-id="4e3b1-209">Erişimi belirli cmdlet'ler, İşlevler veya sağlayıcıları tüm kullanıcılara izin vermek istiyorsanız, bunu yapabilirsiniz oturum yapılandırma dosyasında sağ.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-209">If you want to allow all users access to specific cmdlets, functions, or providers, you can do so right in the session configuration file.</span></span>
<span data-ttu-id="4e3b1-210">Oturum yapılandırma dosyasında desteklenen özellikler tam listesi için çalıştırma `Get-Help New-PSSessionConfigurationFile -Full`.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-210">For a full list of supported properties in the session configuration file, run `Get-Help New-PSSessionConfigurationFile -Full`.</span></span>

## <a name="testing-a-session-configuration-file"></a><span data-ttu-id="4e3b1-211">Test oturumu yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="4e3b1-211">Testing a session configuration file</span></span>

<span data-ttu-id="4e3b1-212">Kullanarak bir oturum yapılandırması test [Test PSSessionConfigurationFile](/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-212">You can test a session configuration using the [Test-PSSessionConfigurationFile](/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet.</span></span> <span data-ttu-id="4e3b1-213">El ile düzenlendi, oturum yapılandırma dosyanızı sınamanız önerilir `.pssc` dosya.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-213">It's recommended that you test your session configuration file if you've manually edited the `.pssc` file.</span></span> <span data-ttu-id="4e3b1-214">Test, söz dizimi doğru olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-214">Testing ensures the syntax is correct.</span></span> <span data-ttu-id="4e3b1-215">Bir oturum yapılandırma dosyası bu test başarısız olursa, sistemde kaydedilemez.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-215">If a session configuration file fails this test, it can't be registered on the system.</span></span>

## <a name="sample-session-configuration-file"></a><span data-ttu-id="4e3b1-216">Örnek oturum yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="4e3b1-216">Sample session configuration file</span></span>

<span data-ttu-id="4e3b1-217">Aşağıdaki örnek, oluşturma ve JEA için bir oturum yapılandırması doğrulama gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-217">The following example shows how to create and validate a session configuration for JEA.</span></span> <span data-ttu-id="4e3b1-218">Rol tanımları oluşturulur ve depolanır `$roles` convenience ve Okunabilirlik için değişken.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-218">The role definitions are created and stored in the `$roles` variable for convenience and readability.</span></span> <span data-ttu-id="4e3b1-219">Bu, bunu yapmak için bir gereksinim değildir.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-219">It isn't a requirement to do so.</span></span>

```powershell
$roles = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}

New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\JEAConfig.pssc -RunAsVirtualAccount -TranscriptDirectory 'C:\ProgramData\JEAConfiguration\Transcripts' -RoleDefinitions $roles -RequiredGroups @{ Or = '2FA-logon', 'smartcard-logon' }
Test-PSSessionConfigurationFile -Path .\JEAConfig.pssc # should yield True
```

## <a name="updating-session-configuration-files"></a><span data-ttu-id="4e3b1-220">Oturum yapılandırma dosyalarını güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="4e3b1-220">Updating session configuration files</span></span>

<span data-ttu-id="4e3b1-221">Kullanıcıların rollere, eşleme içeren bir JEA oturum yapılandırması özelliklerini değiştirmek için şunları yapmalısınız [kaydını](register-jea.md#unregistering-jea-configurations).</span><span class="sxs-lookup"><span data-stu-id="4e3b1-221">To change the properties of a JEA session configuration, including the mapping of users to roles, you must [unregister](register-jea.md#unregistering-jea-configurations).</span></span> <span data-ttu-id="4e3b1-222">Ardından, [yeniden kaydettirin](register-jea.md) bir güncelleştirilmiş oturum yapılandırma dosyası kullanarak JEA oturum yapılandırması.</span><span class="sxs-lookup"><span data-stu-id="4e3b1-222">Then, [re-register](register-jea.md) the JEA session configuration using an updated session configuration file.</span></span>

## <a name="next-steps"></a><span data-ttu-id="4e3b1-223">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="4e3b1-223">Next steps</span></span>

- [<span data-ttu-id="4e3b1-224">Bir JEA yapılandırmasını Kaydet</span><span class="sxs-lookup"><span data-stu-id="4e3b1-224">Register a JEA configuration</span></span>](register-jea.md)
- [<span data-ttu-id="4e3b1-225">Yazar JEA rolleri</span><span class="sxs-lookup"><span data-stu-id="4e3b1-225">Author JEA roles</span></span>](role-capabilities.md)
