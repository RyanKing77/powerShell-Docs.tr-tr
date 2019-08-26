---
ms.date: 07/10/2019
keywords: Jea, PowerShell, güvenlik
title: JEA oturum yapılandırması
ms.openlocfilehash: 650d0d11ef13605847d0822249e29e3491180629
ms.sourcegitcommit: e894ed833cef57967cdaf002f8c883f66864e836
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2019
ms.locfileid: "70017884"
---
# <a name="jea-session-configurations"></a><span data-ttu-id="5fda3-103">JEA oturum yapılandırması</span><span class="sxs-lookup"><span data-stu-id="5fda3-103">JEA Session Configurations</span></span>

<span data-ttu-id="5fda3-104">Bir JEA uç noktası, bir PowerShell oturum yapılandırma dosyası oluşturup kaydederek sisteme kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="5fda3-104">A JEA endpoint is registered on a system by creating and registering a PowerShell session configuration file.</span></span> <span data-ttu-id="5fda3-105">Oturum yapılandırmalarının, JEA uç noktasını ve hangi rollerin erişebileceğini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5fda3-105">Session configurations define who can use the JEA endpoint and which roles they have access to.</span></span> <span data-ttu-id="5fda3-106">Ayrıca, JEA oturumunun tüm kullanıcıları için uygulanan genel ayarları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5fda3-106">They also define global settings that apply to all users of the JEA session.</span></span>

## <a name="create-a-session-configuration-file"></a><span data-ttu-id="5fda3-107">Oturum yapılandırma dosyası oluşturma</span><span class="sxs-lookup"><span data-stu-id="5fda3-107">Create a session configuration file</span></span>

<span data-ttu-id="5fda3-108">JEA uç noktasını kaydetmek için, bu uç noktanın nasıl yapılandırıldığını belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="5fda3-108">To register a JEA endpoint, you must specify how that endpoint is configured.</span></span> <span data-ttu-id="5fda3-109">Göz önünde bulundurulması gereken birçok seçenek vardır.</span><span class="sxs-lookup"><span data-stu-id="5fda3-109">There are many options to consider.</span></span> <span data-ttu-id="5fda3-110">En önemli seçenekler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="5fda3-110">The most important options are:</span></span>

- <span data-ttu-id="5fda3-111">JEA uç noktasına kimlerin erişimi vardır</span><span class="sxs-lookup"><span data-stu-id="5fda3-111">Who has access to the JEA endpoint</span></span>
- <span data-ttu-id="5fda3-112">Atandıkları roller</span><span class="sxs-lookup"><span data-stu-id="5fda3-112">Which roles they be assigned</span></span>
- <span data-ttu-id="5fda3-113">JEA 'nın, kapakları altında kullandığı kimlik</span><span class="sxs-lookup"><span data-stu-id="5fda3-113">Which identity JEA uses under the covers</span></span>
- <span data-ttu-id="5fda3-114">JEA uç noktasının adı</span><span class="sxs-lookup"><span data-stu-id="5fda3-114">The name of the JEA endpoint</span></span>

<span data-ttu-id="5fda3-115">Bu seçenekler, PowerShell oturum yapılandırma dosyası olarak bilinen bir `.pssc` uzantıya sahip bir PowerShell veri dosyasında tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="5fda3-115">These options are defined in a PowerShell data file with a `.pssc` extension known as a PowerShell session configuration file.</span></span> <span data-ttu-id="5fda3-116">Oturum yapılandırma dosyası herhangi bir metin Düzenleyicisi kullanılarak düzenlenebilir.</span><span class="sxs-lookup"><span data-stu-id="5fda3-116">The session configuration file can be edited using any text editor.</span></span>

<span data-ttu-id="5fda3-117">Boş bir şablon yapılandırma dosyası oluşturmak için aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="5fda3-117">Run the following command to create a blank template configuration file.</span></span>

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> <span data-ttu-id="5fda3-118">Varsayılan olarak şablon dosyasına yalnızca en yaygın yapılandırma seçenekleri dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="5fda3-118">Only the most common configuration options are included in the template file by default.</span></span> <span data-ttu-id="5fda3-119">Oluşturulan pssc içindeki tüm geçerli ayarları dahil etmek için anahtarınıkullanın.`-Full`</span><span class="sxs-lookup"><span data-stu-id="5fda3-119">Use the `-Full` switch to include all applicable settings in the generated PSSC.</span></span>

<span data-ttu-id="5fda3-120">Alanı `-SessionType RestrictedRemoteServer` , oturum yapılandırmasının güvenli yönetim için Jea tarafından kullanıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5fda3-120">The `-SessionType RestrictedRemoteServer` field indicates that the session configuration is used by JEA for secure management.</span></span> <span data-ttu-id="5fda3-121">Bu türün oturumları **Nolanguage** modunda çalışır ve yalnızca aşağıdaki varsayılan komutlara (ve diğer adlara) erişebilir:</span><span class="sxs-lookup"><span data-stu-id="5fda3-121">Sessions of this type operate in **NoLanguage** mode and only have access to the following default commands (and aliases):</span></span>

- <span data-ttu-id="5fda3-122">Temizle-Konak (CLS, net)</span><span class="sxs-lookup"><span data-stu-id="5fda3-122">Clear-Host (cls, clear)</span></span>
- <span data-ttu-id="5fda3-123">Çıkış-PSSession (exsn, çıkış)</span><span class="sxs-lookup"><span data-stu-id="5fda3-123">Exit-PSSession (exsn, exit)</span></span>
- <span data-ttu-id="5fda3-124">Get-komutu (GCM)</span><span class="sxs-lookup"><span data-stu-id="5fda3-124">Get-Command (gcm)</span></span>
- <span data-ttu-id="5fda3-125">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="5fda3-125">Get-FormatData</span></span>
- <span data-ttu-id="5fda3-126">Yardım alın</span><span class="sxs-lookup"><span data-stu-id="5fda3-126">Get-Help</span></span>
- <span data-ttu-id="5fda3-127">Ölçü-nesne (ölçü)</span><span class="sxs-lookup"><span data-stu-id="5fda3-127">Measure-Object (measure)</span></span>
- <span data-ttu-id="5fda3-128">Dışarı-varsayılan</span><span class="sxs-lookup"><span data-stu-id="5fda3-128">Out-Default</span></span>
- <span data-ttu-id="5fda3-129">Select-Object (Seç)</span><span class="sxs-lookup"><span data-stu-id="5fda3-129">Select-Object (select)</span></span>

<span data-ttu-id="5fda3-130">Kullanılabilir PowerShell sağlayıcısı yok veya hiçbir dış program (yürütülebilir dosyalar veya betikler) yok.</span><span class="sxs-lookup"><span data-stu-id="5fda3-130">No PowerShell providers are available, nor are any external programs (executables or scripts).</span></span>

<span data-ttu-id="5fda3-131">Dil modları hakkında daha fazla bilgi için bkz. [about_Language_modes](/powershell/module/microsoft.powershell.core/about/about_language_modes).</span><span class="sxs-lookup"><span data-stu-id="5fda3-131">For more information about language modes, see [about_Language_modes](/powershell/module/microsoft.powershell.core/about/about_language_modes).</span></span>

### <a name="choose-the-jea-identity"></a><span data-ttu-id="5fda3-132">JEA kimliğini seçin</span><span class="sxs-lookup"><span data-stu-id="5fda3-132">Choose the JEA identity</span></span>

<span data-ttu-id="5fda3-133">Arka planda, JEA, bağlı bir kullanıcının komutlarını çalıştırırken kullanılacak bir kimliğe (hesap) ihtiyaç duyuyor.</span><span class="sxs-lookup"><span data-stu-id="5fda3-133">Behind the scenes, JEA needs an identity (account) to use when running a connected user's commands.</span></span>
<span data-ttu-id="5fda3-134">JEA 'nın oturum yapılandırma dosyasında hangi kimliğe kullandığını tanımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="5fda3-134">You define which identity JEA uses in the session configuration file.</span></span>

#### <a name="local-virtual-account"></a><span data-ttu-id="5fda3-135">Yerel sanal hesap</span><span class="sxs-lookup"><span data-stu-id="5fda3-135">Local Virtual Account</span></span>

<span data-ttu-id="5fda3-136">Yerel sanal hesaplar, JEA uç noktası için tanımlanan tüm roller yerel makineyi yönetmek için kullanıldığında ve bir yerel yönetici hesabı komutları başarıyla çalıştırmak için yeterli olduğunda yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="5fda3-136">Local virtual accounts are useful when all roles defined for the JEA endpoint are used to manage the local machine and a local administrator account is sufficient to run the commands successfully.</span></span>
<span data-ttu-id="5fda3-137">Sanal hesaplar, belirli bir kullanıcı için benzersiz olan geçici hesaplardır ve yalnızca PowerShell oturumunun süresi için en son.</span><span class="sxs-lookup"><span data-stu-id="5fda3-137">Virtual accounts are temporary accounts that are unique to a specific user and only last for the duration of their PowerShell session.</span></span> <span data-ttu-id="5fda3-138">Bir üye sunucusunda veya iş istasyonunda, sanal hesaplar yerel bilgisayarın **Yöneticiler** grubuna aittir.</span><span class="sxs-lookup"><span data-stu-id="5fda3-138">On a member server or workstation, virtual accounts belong to the local computer's **Administrators** group.</span></span> <span data-ttu-id="5fda3-139">Active Directory Etki Alanı denetleyicisinde, sanal hesaplar etki alanının **etki alanı yöneticileri** grubuna aittir.</span><span class="sxs-lookup"><span data-stu-id="5fda3-139">On an Active Directory Domain Controller, virtual accounts belong to the domain's **Domain Admins** group.</span></span>

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

<span data-ttu-id="5fda3-140">Oturum yapılandırması tarafından tanımlanan roller tam yönetici ayrıcalığı gerektirmiyorsa, sanal hesabın ait olacağı güvenlik gruplarını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5fda3-140">If the roles defined by the session configuration don't require full administrative privilege, you can specify the security groups to which the virtual account will belong.</span></span> <span data-ttu-id="5fda3-141">Bir üye sunucusunda veya iş istasyonunda, belirtilen güvenlik grupları bir etki alanından gruplar değil yerel gruplar olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5fda3-141">On a member server or workstation, the specified security groups must be local groups, not groups from a domain.</span></span>

<span data-ttu-id="5fda3-142">Bir veya daha fazla güvenlik grubu belirtildiğinde, sanal hesap yerel veya etki alanı yöneticileri grubuna atanmaz.</span><span class="sxs-lookup"><span data-stu-id="5fda3-142">When one or more security groups are specified, the virtual account isn't assigned to the local or domain administrators group.</span></span>

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```

> [!NOTE]
> <span data-ttu-id="5fda3-143">Sanal hesaplara geçici olarak yerel sunucu güvenlik ilkesinde hizmet olarak oturum açma hakkı verilir.</span><span class="sxs-lookup"><span data-stu-id="5fda3-143">Virtual accounts are temporarily granted the Logon as a service right in the local server security policy.</span></span> <span data-ttu-id="5fda3-144">Belirtilen VirtualAccountGroups 'lerden biri zaten ilkede bu hak verildiyse, bireysel sanal hesap artık ilkeden eklenmez ve ilkeye kaldırılmaz.</span><span class="sxs-lookup"><span data-stu-id="5fda3-144">If one of the VirtualAccountGroups specified has already been granted this right in the policy, the individual virtual account will no longer be added and removed from the policy.</span></span> <span data-ttu-id="5fda3-145">Bu, etki alanı denetleyicisi güvenlik ilkesi düzeltmelerinin yakından denetlenmesinde etki alanı denetleyicileri gibi senaryolarda yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="5fda3-145">This can be useful in scenarios such as domain controllers where revisions to the domain controller security policy are closely audited.</span></span> <span data-ttu-id="5fda3-146">Bu, Windows Server 2016 ' de yalnızca Kasım 2018 veya sonraki bir toplu ve Windows Server 2019 ile Ocak 2019 veya üzeri bir toplu toplaması ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5fda3-146">This is only available in Windows Server 2016 with the November 2018 or later rollup and Windows Server 2019 with the January 2019 or later rollup.</span></span>

#### <a name="group-managed-service-account"></a><span data-ttu-id="5fda3-147">Grup tarafından yönetilen hizmet hesabı</span><span class="sxs-lookup"><span data-stu-id="5fda3-147">Group-managed service account</span></span>

<span data-ttu-id="5fda3-148">Grup tarafından yönetilen hizmet hesabı (GMSA), JEA kullanıcılarının dosya paylaşımları ve Web Hizmetleri gibi ağ kaynaklarına erişmesi gerektiğinde kullanılacak uygun bir kimliktir.</span><span class="sxs-lookup"><span data-stu-id="5fda3-148">A group-managed service account (GMSA) is the appropriate identity to use when JEA users need to access network resources such as file shares and web services.</span></span> <span data-ttu-id="5fda3-149">GMSAs, etki alanındaki tüm makineler üzerinde kaynaklarla kimlik doğrulaması yapmak için kullanılan bir etki alanı kimliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="5fda3-149">GMSAs give you a domain identity that is used to authenticate with resources on any machine within the domain.</span></span> <span data-ttu-id="5fda3-150">Bir GMSA 'nın sağladığı haklar, eriştiğiniz kaynaklara göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="5fda3-150">The rights that a GMSA provides are determined by the resources you're accessing.</span></span> <span data-ttu-id="5fda3-151">Makine veya hizmet yöneticisi bu hakları GMSA 'ya açıkça verilmemişse, hiçbir makine veya hizmette yönetici haklarına sahip değilsiniz.</span><span class="sxs-lookup"><span data-stu-id="5fda3-151">You don't have admin rights on any machines or services unless the machine or service administrator has explicitly granted those rights to the GMSA.</span></span>

```powershell
# Configure JEA sessions to use the GMSA in the local computer's domain
# with the sAMAccountName of 'MyJEAGMSA'
GroupManagedServiceAccount = 'Domain\MyJEAGMSA'
```

<span data-ttu-id="5fda3-152">GMSAs yalnızca gerektiğinde kullanılmalıdır:</span><span class="sxs-lookup"><span data-stu-id="5fda3-152">GMSAs should only be used when necessary:</span></span>

- <span data-ttu-id="5fda3-153">Bir GMSA kullanırken eylemleri kullanıcıya geri izlemek zordur.</span><span class="sxs-lookup"><span data-stu-id="5fda3-153">It's difficult to trace back actions to a user when using a GMSA.</span></span> <span data-ttu-id="5fda3-154">Her Kullanıcı aynı farklı çalıştır kimliğini paylaşır.</span><span class="sxs-lookup"><span data-stu-id="5fda3-154">Every user shares the same run-as identity.</span></span> <span data-ttu-id="5fda3-155">Bireysel kullanıcıların eylemleriyle ilişkilendirilmesi için PowerShell oturum dökümünü ve günlüklerini gözden geçirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="5fda3-155">You must review PowerShell session transcripts and logs to correlate individual users with their actions.</span></span>

- <span data-ttu-id="5fda3-156">GMSA, bağlanan kullanıcının erişmesi gerekmeyen birçok ağ kaynağına erişebilir.</span><span class="sxs-lookup"><span data-stu-id="5fda3-156">The GMSA may have access to many network resources that the connecting user doesn't need access to.</span></span> <span data-ttu-id="5fda3-157">En az ayrıcalık ilkesini izlemek için her zaman bir JEA oturumunda etkin izinleri sınırlamayı deneyin.</span><span class="sxs-lookup"><span data-stu-id="5fda3-157">Always try to limit effective permissions in a JEA session to follow the principle of least privilege.</span></span>

> [!NOTE]
> <span data-ttu-id="5fda3-158">Grup tarafından yönetilen hizmet hesapları yalnızca PowerShell 5,1 veya daha yeni bir sürümü kullanan etki alanına katılmış makinelerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5fda3-158">Group managed service accounts are only available on domain-joined machines using PowerShell 5.1 or newer.</span></span>

<span data-ttu-id="5fda3-159">JEA oturumunun güvenliğini sağlama hakkında daha fazla bilgi için bkz. [güvenlik konuları](security-considerations.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="5fda3-159">For more information about securing a JEA session, see the [security considerations](security-considerations.md) article.</span></span>

### <a name="session-transcripts"></a><span data-ttu-id="5fda3-160">Oturum yazılı betikleri</span><span class="sxs-lookup"><span data-stu-id="5fda3-160">Session transcripts</span></span>

<span data-ttu-id="5fda3-161">Kullanıcıların oturumlarının dökümünü otomatik olarak kaydetmek için bir JEA uç noktası yapılandırmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="5fda3-161">It's recommended that you configure a JEA endpoint to automatically record transcripts of users' sessions.</span></span> <span data-ttu-id="5fda3-162">PowerShell oturum dökümü, bağlanan Kullanıcı, bunlara atanan farklı çalıştır kimliği ve Kullanıcı tarafından çalıştırılan komutlar hakkında bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="5fda3-162">PowerShell session transcripts contain information about the connecting user, the run as identity assigned to them, and the commands run by the user.</span></span> <span data-ttu-id="5fda3-163">Bir sistemde belirli bir değişikliği kimin yaptığını anlaması gereken bir denetim takımı için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="5fda3-163">They can be useful to an auditing team who needs to understand who made a specific change to a system.</span></span>

<span data-ttu-id="5fda3-164">Oturum yapılandırma dosyasında otomatik dökümü yapılandırmak için, döküm dosyalarının depolanması gereken bir klasöre bir yol sağlayın.</span><span class="sxs-lookup"><span data-stu-id="5fda3-164">To configure automatic transcription in the session configuration file, provide a path to a folder where the transcripts should be stored.</span></span>

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

<span data-ttu-id="5fda3-165">Transcripts, dizine okuma ve yazma erişimi gerektiren **yerel sistem** hesabı tarafından klasöre yazılır.</span><span class="sxs-lookup"><span data-stu-id="5fda3-165">Transcripts are written to the folder by the **Local System** account, which requires read and write access to the directory.</span></span> <span data-ttu-id="5fda3-166">Standart kullanıcıların klasöre erişimi olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="5fda3-166">Standard users should have no access to the folder.</span></span> <span data-ttu-id="5fda3-167">Yazılı betikleri denetlemek için erişimi olan güvenlik yöneticileri sayısını sınırlayın.</span><span class="sxs-lookup"><span data-stu-id="5fda3-167">Limit the number of security administrators that have access to audit the transcripts.</span></span>

### <a name="user-drive"></a><span data-ttu-id="5fda3-168">Kullanıcı sürücüsü</span><span class="sxs-lookup"><span data-stu-id="5fda3-168">User drive</span></span>

<span data-ttu-id="5fda3-169">Bağlanan kullanıcılarınızın, JEA uç noktasına veya bu bilgisayardan dosya kopyalaması gerekiyorsa, oturum yapılandırma dosyasında Kullanıcı sürücüsünü etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5fda3-169">If your connecting users need to copy files to or from the JEA endpoint, you can enable the user drive in the session configuration file.</span></span> <span data-ttu-id="5fda3-170">Kullanıcı sürücüsü, her bağlanan kullanıcı için benzersiz bir klasöre eşlenmiş bir **PSDrive** ' dır.</span><span class="sxs-lookup"><span data-stu-id="5fda3-170">The user drive is a **PSDrive** that is mapped to a unique folder for each connecting user.</span></span> <span data-ttu-id="5fda3-171">Bu klasör, kullanıcıların tam dosya sistemine erişim izni vermeden veya FileSystem sağlayıcısını açığa çıkarmadan sisteme dosya kopyalamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="5fda3-171">This folder allows users to copy files to or from the system without giving them access to the full file system or exposing the FileSystem provider.</span></span> <span data-ttu-id="5fda3-172">Kullanıcı sürücüsü içeriği, ağ bağlantısının kesintiye uğratılbileceği durumlara uyum sağlamak için oturumlar arasında kalıcıdır.</span><span class="sxs-lookup"><span data-stu-id="5fda3-172">The user drive contents are persistent across sessions to accommodate situations where network connectivity may be interrupted.</span></span>

```powershell
MountUserDrive = $true
```

<span data-ttu-id="5fda3-173">Varsayılan olarak, Kullanıcı Sürücüsü Kullanıcı başına en fazla 50 MB veri depolamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="5fda3-173">By default, the user drive allows you to store a maximum of 50MB of data per user.</span></span> <span data-ttu-id="5fda3-174">Bir kullanıcının kullanıcı sayısını *Userdrivemaximumsize* alanı ile sınırlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5fda3-174">You can limit the amount of data a user can consume with the *UserDriveMaximumSize* field.</span></span>

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

<span data-ttu-id="5fda3-175">Kullanıcı sürücüsündeki verilerin kalıcı olmasını istemiyorsanız, her gece klasörü otomatik olarak temizlemek için sistemde zamanlanmış bir görev yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5fda3-175">If you don't want data in the user drive to be persistent, you can configure a scheduled task on the system to automatically clean up the folder every night.</span></span>

> [!NOTE]
> <span data-ttu-id="5fda3-176">Kullanıcı sürücüsü yalnızca PowerShell 5,1 veya daha yeni bir sürümde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5fda3-176">The user drive is only available in PowerShell 5.1 or newer.</span></span>

<span data-ttu-id="5fda3-177">PSDrives hakkında daha fazla bilgi için bkz. [PowerShell sürücüleri yönetme](/powershell/scripting/samples/managing-windows-powershell-drives).</span><span class="sxs-lookup"><span data-stu-id="5fda3-177">For more information about PSDrives, see [Managing PowerShell drives](/powershell/scripting/samples/managing-windows-powershell-drives).</span></span>

### <a name="role-definitions"></a><span data-ttu-id="5fda3-178">Rol tanımları</span><span class="sxs-lookup"><span data-stu-id="5fda3-178">Role definitions</span></span>

<span data-ttu-id="5fda3-179">Bir oturum yapılandırma dosyasındaki rol tanımları, **kullanıcıların** **rollere**eşlemesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5fda3-179">Role definitions in a session configuration file define the mapping of **users** to **roles**.</span></span> <span data-ttu-id="5fda3-180">Bu alana dahil edilen her kullanıcıya veya gruba, kayıt edildiğinde JEA uç noktası için izin verilir.</span><span class="sxs-lookup"><span data-stu-id="5fda3-180">Every user or group included in this field is granted permission to the JEA endpoint when it's registered.</span></span>
<span data-ttu-id="5fda3-181">Her Kullanıcı veya Grup, Hashtable 'da yalnızca bir kez bir anahtar olarak dahil edilebilir, ancak birden çok rol atanabilir.</span><span class="sxs-lookup"><span data-stu-id="5fda3-181">Each user or group can be included as a key in the hashtable only once, but can be assigned multiple roles.</span></span> <span data-ttu-id="5fda3-182">Rol yeteneğinin adı, `.psrc` uzantısı olmadan rol yetenek dosyasının adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5fda3-182">The name of the role capability should be the name of the role capability file, without the `.psrc` extension.</span></span>

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

<span data-ttu-id="5fda3-183">Kullanıcı, rol tanımında birden fazla gruba aitse, her birinin rollerine erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="5fda3-183">If a user belongs to more than one group in the role definition, they get access to the roles of each.</span></span> <span data-ttu-id="5fda3-184">İki rol aynı cmdlet 'lere erişim izni verildiğinde, en çok izin verilen parametre kümesi kullanıcıya verilir.</span><span class="sxs-lookup"><span data-stu-id="5fda3-184">When two roles grant access to the same cmdlets, the most permissive parameter set is granted to the user.</span></span>

<span data-ttu-id="5fda3-185">Rol tanımları alanındaki yerel kullanıcıları veya grupları belirtirken, bilgisayar adını **localhost** veya joker karakterler değil kullandığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="5fda3-185">When specifying local users or groups in the role definitions field, be sure to use the computer name, not **localhost** or wildcards.</span></span> <span data-ttu-id="5fda3-186">`$env:COMPUTERNAME` Değişkeni inceleyerek bilgisayar adını kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5fda3-186">You can check the computer name by inspecting the `$env:COMPUTERNAME` variable.</span></span>

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a><span data-ttu-id="5fda3-187">Rol yetenek arama sırası</span><span class="sxs-lookup"><span data-stu-id="5fda3-187">Role capability search order</span></span>

<span data-ttu-id="5fda3-188">Yukarıdaki örnekte gösterildiği gibi, rol özelliklerine rol yetenek dosyasının temel adı tarafından başvurulur.</span><span class="sxs-lookup"><span data-stu-id="5fda3-188">As shown in the example above, role capabilities are referenced by the base name of the role capability file.</span></span> <span data-ttu-id="5fda3-189">Bir dosyanın temel adı, uzantısı olmayan dosya adıdır.</span><span class="sxs-lookup"><span data-stu-id="5fda3-189">The base name of a file is the filename without the extension.</span></span> <span data-ttu-id="5fda3-190">Sistemde aynı ada sahip birden çok rol özelliği varsa, PowerShell etkin rol yetenek dosyasını seçmek için örtük arama sırasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="5fda3-190">If multiple role capabilities are available on the system with the same name, PowerShell uses its implicit search order to select the effective role capability file.</span></span> <span data-ttu-id="5fda3-191">JEA, aynı ada sahip tüm rol yetenek dosyalarına erişim vermez.</span><span class="sxs-lookup"><span data-stu-id="5fda3-191">JEA does **not** give access to all role capability files with the same name.</span></span>

<span data-ttu-id="5fda3-192">Jea, `$env:PSModulePath` rol yetenek dosyalarını hangi yolların tarayacağını öğrenmek için ortam değişkenini kullanır.</span><span class="sxs-lookup"><span data-stu-id="5fda3-192">JEA uses the `$env:PSModulePath` environment variable to determine which paths to scan for role capability files.</span></span> <span data-ttu-id="5fda3-193">Bu yolların her biri içinde JEA, "RoleCapabilities" alt klasörü içeren geçerli PowerShell modülleri arar.</span><span class="sxs-lookup"><span data-stu-id="5fda3-193">Within each of those paths, JEA looks for valid PowerShell modules that contain a "RoleCapabilities" subfolder.</span></span> <span data-ttu-id="5fda3-194">Modüller içeri aktarılırken olduğu gibi, JEA aynı ada sahip özel rol yeteneklerine Windows ile gönderilen rol yeteneklerini tercih eder.</span><span class="sxs-lookup"><span data-stu-id="5fda3-194">As with importing modules, JEA prefers role capabilities that are shipped with Windows to custom role capabilities with the same name.</span></span>

<span data-ttu-id="5fda3-195">Diğer tüm adlandırma çakışmaları için öncelik, Windows 'un dizindeki dosyaları numaralandırdığı sıraya göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="5fda3-195">For all other naming conflicts, precedence is determined by the order in which Windows enumerates the files in the directory.</span></span> <span data-ttu-id="5fda3-196">Siparişin alfabetik olması garanti edilmez.</span><span class="sxs-lookup"><span data-stu-id="5fda3-196">The order isn't guaranteed to be alphabetical.</span></span> <span data-ttu-id="5fda3-197">Bağlanan kullanıcı için belirtilen adla eşleşen ilk rol yetenek dosyası bulundu.</span><span class="sxs-lookup"><span data-stu-id="5fda3-197">The first role capability file found that matches the specified name is used for the connecting user.</span></span> <span data-ttu-id="5fda3-198">Rol yetenek arama sırası belirleyici olmadığından, rol özelliklerinin benzersiz dosya adlarına sahip olması **önemle tavsiye edilir** .</span><span class="sxs-lookup"><span data-stu-id="5fda3-198">Since the role capability search order isn't deterministic, it's **strongly recommended** that role capabilities have unique filenames.</span></span>

### <a name="conditional-access-rules"></a><span data-ttu-id="5fda3-199">Koşullu erişim kuralları</span><span class="sxs-lookup"><span data-stu-id="5fda3-199">Conditional access rules</span></span>

<span data-ttu-id="5fda3-200">**Roledefinitions** alanına dahil edilen tüm kullanıcılara ve gruplara otomatik olarak Jea uç noktalarına erişim verilir.</span><span class="sxs-lookup"><span data-stu-id="5fda3-200">All users and groups included in the **RoleDefinitions** field are automatically granted access to JEA endpoints.</span></span> <span data-ttu-id="5fda3-201">Koşullu erişim kuralları, bu erişimi iyileştirmenize ve kullanıcıların atandıkları rolleri etkilemeden ek güvenlik gruplarına ait olmasını gerektirmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="5fda3-201">Conditional access rules allow you to refine this access and require users to belong to additional security groups that don't impact the roles to which they're assigned.</span></span> <span data-ttu-id="5fda3-202">Bu, bir tam zamanında ayrıcalıklı erişim yönetimi çözümünü, akıllı kart kimlik doğrulamasını veya JEA ile diğer çok faktörlü kimlik doğrulama çözümünü bütünleştirmek istediğinizde yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="5fda3-202">This is useful when you want to integrate a just-in-time privileged access management solution, smartcard authentication, or other multifactor authentication solution with JEA.</span></span>

<span data-ttu-id="5fda3-203">Koşullu erişim kuralları, bir oturum yapılandırma dosyasındaki RequiredGroups alanında tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="5fda3-203">Conditional access rules are defined in the RequiredGroups field in a session configuration file.</span></span>
<span data-ttu-id="5fda3-204">Burada, kurallarınızı oluşturmak için ' ve ' ve ' veya ' anahtarlarını kullanan bir Hashtable (isteğe bağlı olarak iç içe) sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5fda3-204">There, you can provide a hashtable (optionally nested) that uses 'And' and 'Or' keys to construct your rules.</span></span> <span data-ttu-id="5fda3-205">Bu alanın nasıl kullanılacağına ilişkin bazı örnekler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="5fda3-205">Here are some examples of how to use this field:</span></span>

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
> <span data-ttu-id="5fda3-206">Koşullu erişim kuralları yalnızca PowerShell 5,1 veya daha yeni sürümlerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5fda3-206">Conditional access rules are only available in PowerShell 5.1 or newer.</span></span>

### <a name="other-properties"></a><span data-ttu-id="5fda3-207">Diğer özellikler</span><span class="sxs-lookup"><span data-stu-id="5fda3-207">Other properties</span></span>

<span data-ttu-id="5fda3-208">Oturum yapılandırma dosyaları bir rol yetenek dosyasının yapabileceği her şeyi de yapabilir, böylece kullanıcılara farklı komutlara erişme izni verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5fda3-208">Session configuration files can also do everything a role capability file can do, just without the ability to give connecting users access to different commands.</span></span> <span data-ttu-id="5fda3-209">Tüm kullanıcıların belirli cmdlet 'lere, işlevlere veya sağlayıcılara erişmesine izin vermek istiyorsanız, oturum yapılandırma dosyasında bu hakkı uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5fda3-209">If you want to allow all users access to specific cmdlets, functions, or providers, you can do so right in the session configuration file.</span></span>
<span data-ttu-id="5fda3-210">Oturum yapılandırma dosyasında desteklenen özelliklerin tam listesi için, öğesini çalıştırın `Get-Help New-PSSessionConfigurationFile -Full`.</span><span class="sxs-lookup"><span data-stu-id="5fda3-210">For a full list of supported properties in the session configuration file, run `Get-Help New-PSSessionConfigurationFile -Full`.</span></span>

## <a name="testing-a-session-configuration-file"></a><span data-ttu-id="5fda3-211">Oturum yapılandırma dosyasını test etme</span><span class="sxs-lookup"><span data-stu-id="5fda3-211">Testing a session configuration file</span></span>

<span data-ttu-id="5fda3-212">[Test-PSSessionConfigurationFile](/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet 'ini kullanarak bir oturum yapılandırmasını test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5fda3-212">You can test a session configuration using the [Test-PSSessionConfigurationFile](/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet.</span></span> <span data-ttu-id="5fda3-213">`.pssc` Dosyayı el ile düzenlediyseniz, oturum yapılandırma dosyanızı test etmeniz önerilir.</span><span class="sxs-lookup"><span data-stu-id="5fda3-213">It's recommended that you test your session configuration file if you've manually edited the `.pssc` file.</span></span> <span data-ttu-id="5fda3-214">Test, sözdiziminin doğru olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="5fda3-214">Testing ensures the syntax is correct.</span></span> <span data-ttu-id="5fda3-215">Bu testte bir oturum yapılandırma dosyası başarısız olursa, sistemde kayıtlı olamaz.</span><span class="sxs-lookup"><span data-stu-id="5fda3-215">If a session configuration file fails this test, it can't be registered on the system.</span></span>

## <a name="sample-session-configuration-file"></a><span data-ttu-id="5fda3-216">Örnek oturum yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="5fda3-216">Sample session configuration file</span></span>

<span data-ttu-id="5fda3-217">Aşağıdaki örnek, JEA için bir oturum yapılandırmasının nasıl oluşturulacağını ve doğrulandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5fda3-217">The following example shows how to create and validate a session configuration for JEA.</span></span> <span data-ttu-id="5fda3-218">Rol tanımları, kolay ve okunabilir olmaları için oluşturulur `$roles` ve değişkeninde depolanır.</span><span class="sxs-lookup"><span data-stu-id="5fda3-218">The role definitions are created and stored in the `$roles` variable for convenience and readability.</span></span> <span data-ttu-id="5fda3-219">Bunun için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="5fda3-219">It isn't a requirement to do so.</span></span>

```powershell
$roles = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}

New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\JEAConfig.pssc -RunAsVirtualAccount -TranscriptDirectory 'C:\ProgramData\JEAConfiguration\Transcripts' -RoleDefinitions $roles -RequiredGroups @{ Or = '2FA-logon', 'smartcard-logon' }
Test-PSSessionConfigurationFile -Path .\JEAConfig.pssc # should yield True
```

## <a name="updating-session-configuration-files"></a><span data-ttu-id="5fda3-220">Oturum yapılandırma dosyaları güncelleştiriliyor</span><span class="sxs-lookup"><span data-stu-id="5fda3-220">Updating session configuration files</span></span>

<span data-ttu-id="5fda3-221">Kullanıcıları rollerle eşleme dahil bir JEA oturum yapılandırmasının özelliklerini değiştirmek için, [kaydını silmeniz](register-jea.md#unregistering-jea-configurations)gerekir.</span><span class="sxs-lookup"><span data-stu-id="5fda3-221">To change the properties of a JEA session configuration, including the mapping of users to roles, you must [unregister](register-jea.md#unregistering-jea-configurations).</span></span> <span data-ttu-id="5fda3-222">Ardından, güncelleştirilmiş bir oturum yapılandırma dosyası kullanarak JEA oturum yapılandırmasını [yeniden kaydedin](register-jea.md) .</span><span class="sxs-lookup"><span data-stu-id="5fda3-222">Then, [re-register](register-jea.md) the JEA session configuration using an updated session configuration file.</span></span>

## <a name="next-steps"></a><span data-ttu-id="5fda3-223">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="5fda3-223">Next steps</span></span>

- [<span data-ttu-id="5fda3-224">JEA yapılandırmasını kaydetme</span><span class="sxs-lookup"><span data-stu-id="5fda3-224">Register a JEA configuration</span></span>](register-jea.md)
- [<span data-ttu-id="5fda3-225">JEA rollerini yazma</span><span class="sxs-lookup"><span data-stu-id="5fda3-225">Author JEA roles</span></span>](role-capabilities.md)
