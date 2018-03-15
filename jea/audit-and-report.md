---
ms.date: 2017-06-12
author: rpsqrd
ms.topic: conceptual
keywords: "jea, powershell, güvenlik"
title: "Denetim ve JEA üzerinde raporlama"
ms.openlocfilehash: 57148bc3753bdd751bfa21fc3198aca3f8654849
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2018
---
# <a name="auditing-and-reporting-on-jea"></a><span data-ttu-id="4652f-103">Denetim ve JEA üzerinde raporlama</span><span class="sxs-lookup"><span data-stu-id="4652f-103">Auditing and Reporting on JEA</span></span>

> <span data-ttu-id="4652f-104">Uygulandığı öğe: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="4652f-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="4652f-105">JEA dağıtıldıktan sonra düzenli olarak JEA yapılandırma denetim isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="4652f-105">After you've deployed JEA, you will want to regularly audit the JEA configuration.</span></span>
<span data-ttu-id="4652f-106">Bu, doğru kişilerin JEA endpoint erişiminiz varsa ve atanan rollerinin hala uygun değilse değerlendirmenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="4652f-106">This will help you assess if the correct people have access to the JEA endpoint and if their assigned roles are still appropriate.</span></span>

<span data-ttu-id="4652f-107">Bu konuda bir JEA uç noktası denetim çeşitli yolları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4652f-107">This topic describes the various ways you can audit a JEA endpoint.</span></span>

## <a name="find-registered-jea-sessions-on-a-machine"></a><span data-ttu-id="4652f-108">Bir makinede kayıtlı JEA oturumları Bul</span><span class="sxs-lookup"><span data-stu-id="4652f-108">Find registered JEA sessions on a machine</span></span>

<span data-ttu-id="4652f-109">Hangi JEA oturumlarının bir makinede kayıtlı denetlemek için kullanın [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="4652f-109">To check which JEA sessions are registered on a machine, use the [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet.</span></span>

```powershell
# Filter for sessions that are configured as 'RestrictedRemoteServer' to find JEA-like session configurations
PS C:\> Get-PSSessionConfiguration | Where-Object { $_.SessionType -eq 'RestrictedRemoteServer' }


Name          : JEAMaintenance
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : CONTOSO\JEA_DNS_ADMINS AccessAllowed, CONTOSO\JEA_DNS_OPERATORS AccessAllowed, CONTOSO\JEA_DNS_AUDITORS AccessAllowed
```

<span data-ttu-id="4652f-110">Uç noktası için etkili haklar "İzni" özelliğinde listelenir.</span><span class="sxs-lookup"><span data-stu-id="4652f-110">The effective rights for the endpoint are listed in the "Permission" property.</span></span>
<span data-ttu-id="4652f-111">Bu kullanıcılar JEA uç noktası, hangi rollerin ancak (ve uzantılarının, komutları) bağlanmak için izniniz "RoleDefinitions" alanına göre belirlenir için erişime sahip oldukları [oturum yapılandırma dosyası](session-configurations.md) kaydetmek için kullanıldı uç noktası.</span><span class="sxs-lookup"><span data-stu-id="4652f-111">These users have the right to connect to the JEA endpoint, but which roles (and, by extension, commands) they have access to is determined by the "RoleDefinitions" field in the [session configuration file](session-configurations.md) that was used to register the endpoint.</span></span>

<span data-ttu-id="4652f-112">Kayıtlı bir JEA uç noktası rolü eşlemelerin "RoleDefinitions" özelliği verilerde genişleterek değerlendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4652f-112">You can evaluate the role mappings in a registered JEA endpoint by expanding the data in the "RoleDefinitions" property.</span></span>

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{ Name = 'Role Capabilities'; Expression = { $_.Value.RoleCapabilities } }
```

## <a name="find-available-role-capabilities-on-the-machine"></a><span data-ttu-id="4652f-113">Makinede kullanılabilir rol özelliklerini Bul</span><span class="sxs-lookup"><span data-stu-id="4652f-113">Find available role capabilities on the machine</span></span>

<span data-ttu-id="4652f-114">Geçerli bir PowerShell modülü içinde "RoleCapabilities" klasöründe depolanıyorsa Rol Yetenek dosyaları yalnızca JEA tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4652f-114">Role capability files will only be used by JEA if they are stored in a "RoleCapabilities" folder inside a valid PowerShell module.</span></span>
<span data-ttu-id="4652f-115">Bir bilgisayarda kullanılabilen tüm rol özellikleri kullanılabilir modüllerin listesini arayarak bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4652f-115">You can find all role capabilities available on a computer by searching the list of available modules.</span></span>

```powershell
function Find-LocalRoleCapability {
    $results = @()

    # Find modules with a "RoleCapabilities" subfolder and add any PSRC files to the result set
    Get-Module -ListAvailable | ForEach-Object {
        $psrcpath = Join-Path -Path $_.ModuleBase -ChildPath 'RoleCapabilities'
        if (Test-Path $psrcpath) {
            $results += Get-ChildItem -Path $psrcpath -Filter *.psrc
        }
    }

    # Format the results nicely to make it easier to read
    $results | Select-Object @{ Name = 'Name'; Expression = { $_.Name.TrimEnd('.psrc') }}, @{ Name = 'Path'; Expression = { $_.FullName }} | Sort-Object Name
}
```

> [!NOTE]
> <span data-ttu-id="4652f-116">Bu işlev sonuçlarından sırasını mutlaka birden çok rol özellikleri aynı adı paylaşan durumunda hangi rolü özellikleri seçilecektir sırası değildir.</span><span class="sxs-lookup"><span data-stu-id="4652f-116">The order of results from this function is not necessarily the order in which the role capabilities will be selected if multiple role capabilities share the same name.</span></span>

## <a name="check-effective-rights-for-a-specific-user"></a><span data-ttu-id="4652f-117">Belirli bir kullanıcı için etkin haklarını denetleme</span><span class="sxs-lookup"><span data-stu-id="4652f-117">Check effective rights for a specific user</span></span>

<span data-ttu-id="4652f-118">JEA uç nokta ayarlamayı ayarladıktan sonra hangi komutların JEA oturumda belirli bir kullanıcı tarafından kullanılabilir denetlemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4652f-118">Once you have set up a JEA endpoint, you may want to check which commands are available to a specific user in a JEA session.</span></span>
<span data-ttu-id="4652f-119">Kullanabileceğiniz [Get-PSSessionCapability](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Get-PSSessionCapability) geçerli grup üyeliklerini JEA oturumu başlatmak için olsaydı bir kullanıcıya uygulanabilir komutların tümünü numaralandırılamıyor.</span><span class="sxs-lookup"><span data-stu-id="4652f-119">You can use [Get-PSSessionCapability](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Get-PSSessionCapability) to enumerate all of the commands applicable to a user if they were to start a JEA session with their current group memberships.</span></span>
<span data-ttu-id="4652f-120">Çıktısını `Get-PSSessionCapability` çalıştıran belirtilen kullanıcı için aynı `Get-Command -CommandType All` JEA oturumunda.</span><span class="sxs-lookup"><span data-stu-id="4652f-120">The output of `Get-PSSessionCapability` is identical to that of the specified user running `Get-Command -CommandType All` in a JEA session.</span></span>

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

<span data-ttu-id="4652f-121">Kullanıcılarınızın bunları ek JEA haklar gruplarını kalıcı üyesi değilseniz, bu cmdlet bu ek izinler yansıtmayabilir.</span><span class="sxs-lookup"><span data-stu-id="4652f-121">If your users are not permanent members of groups which would grant them additional JEA rights, this cmdlet may not reflect those extra permissions.</span></span>
<span data-ttu-id="4652f-122">Bu genellikle yalnızca zaman ayrıcalıklı erişim yönetimi sistemleri geçici olarak bir güvenlik grubuna ait yapmalarına izin vermek için kullanırken durumdur.</span><span class="sxs-lookup"><span data-stu-id="4652f-122">This is typically the case when using just-in-time privileged access management systems to allow users to temporarily belong to a security group.</span></span>
<span data-ttu-id="4652f-123">Kullanıcıları rollere eşleme ve kullanıcılar yalnızca en az miktarda işlerini başarıyla yapmak için gerekli komutları erişimi aldıklarından emin olmak için her rolün içeriği her zaman dikkatlice değerlendirin.</span><span class="sxs-lookup"><span data-stu-id="4652f-123">Always carefully evaluate the mapping of users to roles and the contents of each role to ensure users are only getting access to the least amount of commands needed to do their jobs successfully.</span></span>

## <a name="powershell-event-logs"></a><span data-ttu-id="4652f-124">PowerShell olay günlükleri</span><span class="sxs-lookup"><span data-stu-id="4652f-124">PowerShell event logs</span></span>

<span data-ttu-id="4652f-125">Sistemde oturum modülü ve/veya betik bloğu etkinleştirilirse, bir kullanıcı kendi JEA oturumlarında çalışan her komut için Windows olay günlüklerini olayları bulmak kuramaz.</span><span class="sxs-lookup"><span data-stu-id="4652f-125">If you enabled module and/or script block logging on the system, you will be able to find events in the Windows event logs for each command a user ran in their JEA sessions.</span></span>
<span data-ttu-id="4652f-126">Bu olayları bulmak için Windows Olay Görüntüleyicisi'ni açın, gitmek **Microsoft-Windows-PowerShell/Operational** olay günlüğü ve olay kimliği olan olaylar için Görünüm **4104**.</span><span class="sxs-lookup"><span data-stu-id="4652f-126">To find these events, open the Windows Event Viewer, navigate to the **Microsoft-Windows-PowerShell/Operational** event log, and look for events with event ID **4104**.</span></span>

<span data-ttu-id="4652f-127">Her olay günlüğü girişi komutu çalıştırıldı oturumu hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="4652f-127">Each event log entry will include information about the session in which the command was run.</span></span>
<span data-ttu-id="4652f-128">JEA oturumları için bu önemli hakkında bilgiler içerir **ConnectedUser**, JEA oturum oluşturan gerçek kullanıcı olduğu yanı sıra **farklıkullanıcı** JEA için kullanılan hesabı tanımlayan komutu yürütün.</span><span class="sxs-lookup"><span data-stu-id="4652f-128">For JEA sessions, this includes important information about the **ConnectedUser**, which is the actual user who created the JEA session, as well as the **RunAsUser** which identifies the account JEA used to execute the command.</span></span>
<span data-ttu-id="4652f-129">Uygulama olay günlükleri bu nedenle dökümleri sahip farklıkullanıcı tarafından yapılan değişiklikleri gösterir veya modül/komut dosyası günlüğü etkin bir kullanıcıya geri belirli komut çağırma izleme yapabilmek önemlidir.</span><span class="sxs-lookup"><span data-stu-id="4652f-129">Application event logs will show changes being made by the RunAsUser, so having transcripts or module/script logging enabled is crucial to be able to trace a specific command invocation back to a user.</span></span>

## <a name="application-event-logs"></a><span data-ttu-id="4652f-130">Uygulama olay günlükleri</span><span class="sxs-lookup"><span data-stu-id="4652f-130">Application event logs</span></span>

<span data-ttu-id="4652f-131">Bir dış uygulama veya hizmet ile etkileşime giren JEA oturumda bir komut çalıştırdığınızda, bu uygulamaları kendi olay günlüklerini olayları oturum açabilir.</span><span class="sxs-lookup"><span data-stu-id="4652f-131">When you run a command in a JEA session that interacts with an external application or service, those applications may log events to their own event logs.</span></span>
<span data-ttu-id="4652f-132">PowerShell günlükleri ve dökümleri, aksine diğer günlük mekanizmaları JEA oturumunun bağlı olan kullanıcı yakalamaz ve bunun yerine yalnızca Çalıştır sanal kullanıcı veya grup yönetilen hizmet hesabı oturum.</span><span class="sxs-lookup"><span data-stu-id="4652f-132">Unlike PowerShell logs and transcripts, other logging mechanisms will not capture the connected user of the JEA session, and will instead only log the virtual run-as user or group managed service account.</span></span>
<span data-ttu-id="4652f-133">Kimin komutun çalıştığını belirlemek için başvurun gerekecektir bir [oturum dökümü](#session-transcripts) veya PowerShell olay günlüklerini saat ve uygulama olay günlüğünde gösterilen kullanıcı ile ilişkilendirilmesi.</span><span class="sxs-lookup"><span data-stu-id="4652f-133">In order to determine who ran the command, you will need to consult a [session transcript](#session-transcripts) or correlate PowerShell event logs with the time and user shown in the application event log.</span></span>

<span data-ttu-id="4652f-134">Günlük ayrıca ilişkilendirmenize yardımcı olur WinRM bağlanan kullanıcı bir uygulama olay günlüğünde kullanıcılarla farklı çalıştır.</span><span class="sxs-lookup"><span data-stu-id="4652f-134">The WinRM log can also help you correlate run as users in an application event log with the connecting user.</span></span>
<span data-ttu-id="4652f-135">Olay Kimliği **193** içinde **Microsoft Windows Windows Uzaktan Yönetimi/Operational** günlük kayıtlarının güvenlik tanımlayıcısı (SID) ve hesap adı için bağlanan kullanıcı ve kullanıcı olarak her zaman bir JEA çalıştırın. oturum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="4652f-135">Event ID **193** in the **Microsoft-Windows-Windows Remote Management/Operational** log records the security identifier (SID) and account name for both the connecting user and run as user every time a JEA session is created.</span></span>

## <a name="session-transcripts"></a><span data-ttu-id="4652f-136">Oturum dökümleri</span><span class="sxs-lookup"><span data-stu-id="4652f-136">Session transcripts</span></span>

<span data-ttu-id="4652f-137">Her bir kullanıcı oturumu için bir dökümü oluşturmak için JEA yapılandırdıysanız, her kullanıcının Eylemler metin kopyasına belirtilen klasörde depolanır.</span><span class="sxs-lookup"><span data-stu-id="4652f-137">If you configured JEA to create a transcript for each user session, a text copy of every user's actions will be stored in the specified folder.</span></span>

<span data-ttu-id="4652f-138">Tüm dökümü dizinleri bulmak için aşağıdaki komutu bilgisayarda yönetici olarak çalıştır JEA ile yapılandırılmış:</span><span class="sxs-lookup"><span data-stu-id="4652f-138">To find all transcript directories, run the following command as an administrator on the computer configured with JEA:</span></span>

```powershell
Get-PSSessionConfiguration | Where-Object { $_.TranscriptDirectory -ne $null } | Format-Table Name, TranscriptDirectory
```

<span data-ttu-id="4652f-139">Oturum, başlatıldığında oturumu ve hangi JEA kimlik atanmış bağlı hangi kullanıcı hakkında bilgi içeren her dökümü başlatır.</span><span class="sxs-lookup"><span data-stu-id="4652f-139">Each transcript starts with information about the time the session started, which user connected to the session, and which JEA identity was assigned to them.</span></span>

```
**********************
Windows PowerShell transcript start
Start time: 20160710144736
Username: CONTOSO\Alice
RunAs User: WinRM Virtual Users\WinRM VA_1_CONTOSO_Alice
Machine: SERVER01 (Microsoft Windows NT 10.0.14393.0)
[...]
```

<span data-ttu-id="4652f-140">Dökümü gövdesinde kullanıcının çağrılan her komutu hakkında bilgileri günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="4652f-140">In the body of the transcript, information is logged about each command the user invoked.</span></span>
<span data-ttu-id="4652f-141">Yürütüldü etkili komutu hala belirleyebilir ancak kullanıcı çalıştırdı komut söz dizimi JEA oturumlarda komutları PowerShell uzaktan iletişim için dönüştürülen şekilde nedeniyle kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="4652f-141">The exact syntax of the command the user ran is unavailable in JEA sessions due to the way commands are transformed for PowerShell remoting, however you can still determine the effective command that was executed.</span></span>
<span data-ttu-id="4652f-142">Bir örnek dökümü parçacığı çalıştıran bir kullanıcıdan aşağıdadır `Get-Service Dns` JEA oturumunda:</span><span class="sxs-lookup"><span data-stu-id="4652f-142">Below is an example transcript snippet from a user running `Get-Service Dns` in a JEA session:</span></span>

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

<span data-ttu-id="4652f-143">Bir kullanıcı çalıştıran her komut için bir "CommandInvocation" satır cmdlet açıklayan yazılır veya kullanıcının çağrılan işlev.</span><span class="sxs-lookup"><span data-stu-id="4652f-143">For each command a user runs, a "CommandInvocation" line will be written, describing the cmdlet or function the user invoked.</span></span>
<span data-ttu-id="4652f-144">Her bir parametre ve komutu ile sağlanan değer hakkında bilgi için her CommandInvocation ParameterBindings izleyin.</span><span class="sxs-lookup"><span data-stu-id="4652f-144">ParameterBindings follow each CommandInvocation to tell you about each parameter and value that was supplied with the command.</span></span>
<span data-ttu-id="4652f-145">Yukarıdaki örnekte, "adı" parametresi "Dns" değeri "Get-Service" cmdlet için sağlanan görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4652f-145">In the above example, you can see that the parameter "Name" was supplied the value "Dns" for the "Get-Service" cmdlet.</span></span>

<span data-ttu-id="4652f-146">Her komut çıktısı ayrıca bir CommandInvocation genellikle dışarı varsayılan olarak tetikler.</span><span class="sxs-lookup"><span data-stu-id="4652f-146">The output of each command will also trigger a CommandInvocation, usually to Out-Default.</span></span> <span data-ttu-id="4652f-147">Inputobject Out-Default komuttan döndürülen PowerShell nesnesidir.</span><span class="sxs-lookup"><span data-stu-id="4652f-147">The InputObject of Out-Default is the PowerShell object returned from the command.</span></span>
<span data-ttu-id="4652f-148">Bu nesnenin ayrıntılarını yazdırılır altında hangi kullanıcı görülen yakından mimicking birkaç satır.</span><span class="sxs-lookup"><span data-stu-id="4652f-148">The details of that object are printed a few lines below, closely mimicking what the user would have seen.</span></span>

## <a name="see-also"></a><span data-ttu-id="4652f-149">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="4652f-149">See also</span></span>

- [<span data-ttu-id="4652f-150">JEA oturumunda denetim kullanıcı eylemleri</span><span class="sxs-lookup"><span data-stu-id="4652f-150">Audit user actions in a JEA session</span></span>](audit-and-report.md)
- [<span data-ttu-id="4652f-151">*PowerShell ♥ mavi takım* güvenlik blog gönderisi</span><span class="sxs-lookup"><span data-stu-id="4652f-151">*PowerShell ♥ the Blue Team* blog post on security</span></span>](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)

