---
ms.date: 06/12/2017
keywords: jea, powershell, güvenlik
title: JEA'da raporlama ve denetleme
ms.openlocfilehash: 2388c735840d8d3683aa8bc9869b9fb0371e5902
ms.sourcegitcommit: 6749f67c32e05999e10deb9d45f90f45ac21a599
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48851229"
---
# <a name="auditing-and-reporting-on-jea"></a><span data-ttu-id="ccec1-103">JEA'da raporlama ve denetleme</span><span class="sxs-lookup"><span data-stu-id="ccec1-103">Auditing and Reporting on JEA</span></span>

> <span data-ttu-id="ccec1-104">İçin geçerlidir: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="ccec1-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="ccec1-105">JEA dağıttıktan sonra düzenli olarak JEA yapılandırmayı denetlemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ccec1-105">After you've deployed JEA, you will want to regularly audit the JEA configuration.</span></span>
<span data-ttu-id="ccec1-106">Bu, doğru kişilerin JEA uç noktasına erişebildiğinden ve atanan rollerinin hala uygun değerlendirmenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="ccec1-106">This will help you assess if the correct people have access to the JEA endpoint and if their assigned roles are still appropriate.</span></span>

<span data-ttu-id="ccec1-107">Bu konu, bir JEA uç noktası denetleyebilirsiniz çeşitli yolları açıklar.</span><span class="sxs-lookup"><span data-stu-id="ccec1-107">This topic describes the various ways you can audit a JEA endpoint.</span></span>

## <a name="find-registered-jea-sessions-on-a-machine"></a><span data-ttu-id="ccec1-108">Bir makinede kayıtlı JEA oturumu bulun</span><span class="sxs-lookup"><span data-stu-id="ccec1-108">Find registered JEA sessions on a machine</span></span>

<span data-ttu-id="ccec1-109">Hangi JEA oturumlarının bir makinede kayıtlı denetlemek için kullanmak [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="ccec1-109">To check which JEA sessions are registered on a machine, use the [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet.</span></span>

```powershell
# Filter for sessions that are configured as 'RestrictedRemoteServer' to find JEA-like session configurations
PS C:\> Get-PSSessionConfiguration | Where-Object { $_.SessionType -eq 'RestrictedRemoteServer' }


Name          : JEAMaintenance
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : CONTOSO\JEA_DNS_ADMINS AccessAllowed, CONTOSO\JEA_DNS_OPERATORS AccessAllowed, CONTOSO\JEA_DNS_AUDITORS AccessAllowed
```

<span data-ttu-id="ccec1-110">Uç noktası için etkin hakları "İzni" özelliğinde listelenir.</span><span class="sxs-lookup"><span data-stu-id="ccec1-110">The effective rights for the endpoint are listed in the "Permission" property.</span></span>
<span data-ttu-id="ccec1-111">Bu kullanıcılar JEA uç noktası, ancak hangi rollerin (ve uzantısıyla komutları) bağlanma izniniz "RoleDefinitions" alanı tarafından belirlenir için erişime sahip oldukları [oturum yapılandırma dosyası](session-configurations.md) kaydetmek için kullanılan uç nokta.</span><span class="sxs-lookup"><span data-stu-id="ccec1-111">These users have the right to connect to the JEA endpoint, but which roles (and, by extension, commands) they have access to is determined by the "RoleDefinitions" field in the [session configuration file](session-configurations.md) that was used to register the endpoint.</span></span>

<span data-ttu-id="ccec1-112">Kayıtlı bir JEA uç noktası rolü eşlemelerin "RoleDefinitions" özelliğinde veri genişleterek değerlendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ccec1-112">You can evaluate the role mappings in a registered JEA endpoint by expanding the data in the "RoleDefinitions" property.</span></span>

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{ Name = 'Role Capabilities'; Expression = { $_.Value.RoleCapabilities } }
```

## <a name="find-available-role-capabilities-on-the-machine"></a><span data-ttu-id="ccec1-113">Makinede kullanılabilir rol işlevleri Bul</span><span class="sxs-lookup"><span data-stu-id="ccec1-113">Find available role capabilities on the machine</span></span>

<span data-ttu-id="ccec1-114">Geçerli bir PowerShell modülü içinde bir "RoleCapabilities" klasöründe depolanıyorsa rol özellik dosyaları yalnızca JEA tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ccec1-114">Role capability files will only be used by JEA if they are stored in a "RoleCapabilities" folder inside a valid PowerShell module.</span></span>
<span data-ttu-id="ccec1-115">Tüm rol özellikleri bir bilgisayarda kullanılabilir modüllerin listesini arayarak bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ccec1-115">You can find all role capabilities available on a computer by searching the list of available modules.</span></span>

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
> <span data-ttu-id="ccec1-116">Bu işlev sonuçlardan sırasını mutlaka aynı adlı birden çok rol işlevleri paylaşırsanız, hangi rol işlevleri seçilir sırası değildir.</span><span class="sxs-lookup"><span data-stu-id="ccec1-116">The order of results from this function is not necessarily the order in which the role capabilities will be selected if multiple role capabilities share the same name.</span></span>

## <a name="check-effective-rights-for-a-specific-user"></a><span data-ttu-id="ccec1-117">Belirli bir kullanıcı için etkin haklarını denetleyin</span><span class="sxs-lookup"><span data-stu-id="ccec1-117">Check effective rights for a specific user</span></span>

<span data-ttu-id="ccec1-118">Bir JEA uç noktası ayarladıktan sonra hangi komutları belirli bir kullanıcıya bir JEA oturumunda kullanılabilir denetlemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ccec1-118">Once you have set up a JEA endpoint, you may want to check which commands are available to a specific user in a JEA session.</span></span>
<span data-ttu-id="ccec1-119">Kullanabileceğiniz [Get-PSSessionCapability](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Get-PSSessionCapability) olsaydı ile geçerli grup üyeliklerini bir JEA oturumu başlatmak için bir kullanıcı için geçerli komutların tümü numaralandırılamadı.</span><span class="sxs-lookup"><span data-stu-id="ccec1-119">You can use [Get-PSSessionCapability](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Get-PSSessionCapability) to enumerate all of the commands applicable to a user if they were to start a JEA session with their current group memberships.</span></span>
<span data-ttu-id="ccec1-120">Çıkışı `Get-PSSessionCapability` çalıştıran belirtilen kullanıcı için aynı `Get-Command -CommandType All` bir JEA oturumda.</span><span class="sxs-lookup"><span data-stu-id="ccec1-120">The output of `Get-PSSessionCapability` is identical to that of the specified user running `Get-Command -CommandType All` in a JEA session.</span></span>

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

<span data-ttu-id="ccec1-121">Bu cmdlet, kullanıcılarınızın bunları JEA ek haklar verilir gruplarının kalıcı üyesi değilseniz, bu ek izinleri yansıtmayabilir.</span><span class="sxs-lookup"><span data-stu-id="ccec1-121">If your users are not permanent members of groups which would grant them additional JEA rights, this cmdlet may not reflect those extra permissions.</span></span>
<span data-ttu-id="ccec1-122">Bu genellikle kullanıcıların geçici olarak bir güvenlik grubuna ait izin vermek için tam zamanında ayrıcalıklı erişim yönetimi sistemleri kullanılırken geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="ccec1-122">This is typically the case when using just-in-time privileged access management systems to allow users to temporarily belong to a security group.</span></span>
<span data-ttu-id="ccec1-123">Rollere kullanıcı eşleme ve kullanıcılar yalnızca komutlar başarıyla işlerini yapmak için gereken en az miktarda erişim aldıklarından emin olmak için her rolün içeriğini her zaman dikkatli bir şekilde değerlendirin.</span><span class="sxs-lookup"><span data-stu-id="ccec1-123">Always carefully evaluate the mapping of users to roles and the contents of each role to ensure users are only getting access to the least amount of commands needed to do their jobs successfully.</span></span>

## <a name="powershell-event-logs"></a><span data-ttu-id="ccec1-124">PowerShell olay günlükleri</span><span class="sxs-lookup"><span data-stu-id="ccec1-124">PowerShell event logs</span></span>

<span data-ttu-id="ccec1-125">Sistemde oturum modülü ve/veya betik bloğu etkinleştirilirse, bir kullanıcı JEA oturumlarını çalıştırdığınız her komut için Windows olay günlüklerindeki olaylarını bulmak mümkün olacaktır.</span><span class="sxs-lookup"><span data-stu-id="ccec1-125">If you enabled module and/or script block logging on the system, you will be able to find events in the Windows event logs for each command a user ran in their JEA sessions.</span></span>
<span data-ttu-id="ccec1-126">Bu olayları bulmak için Windows Olay Görüntüleyicisi'ni açın, gitmek **Microsoft-Windows-PowerShell/Operational** olay günlüğü ve olay kimliği ile olayları arayın **4104**.</span><span class="sxs-lookup"><span data-stu-id="ccec1-126">To find these events, open the Windows Event Viewer, navigate to the **Microsoft-Windows-PowerShell/Operational** event log, and look for events with event ID **4104**.</span></span>

<span data-ttu-id="ccec1-127">Her olay günlüğü girişi komutun çalıştırıldığı oturumu hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="ccec1-127">Each event log entry will include information about the session in which the command was run.</span></span>
<span data-ttu-id="ccec1-128">JEA oturumları için bu önemli hakkında bilgiler içerir **ConnectedUser**, JEA oturumu oluşturan gerçek kullanıcı olduğu yanı sıra **farklıkullanıcı** JEA için kullanılan hesabı tanımlayan komutu yürütün.</span><span class="sxs-lookup"><span data-stu-id="ccec1-128">For JEA sessions, this includes important information about the **ConnectedUser**, which is the actual user who created the JEA session, as well as the **RunAsUser** which identifies the account JEA used to execute the command.</span></span>
<span data-ttu-id="ccec1-129">Bu nedenle dökümleri sahip farklıkullanıcı tarafından yapılan değişiklikleri gösterir uygulama olay günlüklerini veya modül/komut dosyası ünlüğe kaydetme etkin bir özel komut çağırma geri kullanıcıya kadar izleyebiliyor olmanız önemlidir.</span><span class="sxs-lookup"><span data-stu-id="ccec1-129">Application event logs will show changes being made by the RunAsUser, so having transcripts or module/script logging enabled is crucial to be able to trace a specific command invocation back to a user.</span></span>

## <a name="application-event-logs"></a><span data-ttu-id="ccec1-130">Uygulama olay günlükleri</span><span class="sxs-lookup"><span data-stu-id="ccec1-130">Application event logs</span></span>

<span data-ttu-id="ccec1-131">Bir dış uygulama veya hizmeti ile etkileşime giren bir JEA oturumda bir komut çalıştırdığınızda, söz konusu uygulamaların kendi olay günlüklerine olayları oturum açabilir.</span><span class="sxs-lookup"><span data-stu-id="ccec1-131">When you run a command in a JEA session that interacts with an external application or service, those applications may log events to their own event logs.</span></span>
<span data-ttu-id="ccec1-132">PowerShell günlükleri ve dökümler, aksine diğer günlük mekanizmaları JEA oturumun bağlı olan kullanıcı yakalamaz ve bunun yerine yalnızca Çalıştır sanal kullanıcı veya grup yönetilen hizmet hesabı günlüğe kaydedecektir.</span><span class="sxs-lookup"><span data-stu-id="ccec1-132">Unlike PowerShell logs and transcripts, other logging mechanisms will not capture the connected user of the JEA session, and will instead only log the virtual run-as user or group managed service account.</span></span>
<span data-ttu-id="ccec1-133">Kimin komutun çalıştığını belirlemek için başvurun gerekecektir bir [oturumu döküm](#session-transcripts) veya PowerShell olay günlükleri uygulama olay günlüğünde gösterilen kullanıcı ve saat ile ilişkilendirin.</span><span class="sxs-lookup"><span data-stu-id="ccec1-133">In order to determine who ran the command, you will need to consult a [session transcript](#session-transcripts) or correlate PowerShell event logs with the time and user shown in the application event log.</span></span>

<span data-ttu-id="ccec1-134">Günlük da ilişkilendirmenize yardımcı olabilir WinRM uygulama olay günlüğüne kullanıcı bağlanan kullanıcı ile çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ccec1-134">The WinRM log can also help you correlate run as users in an application event log with the connecting user.</span></span>
<span data-ttu-id="ccec1-135">Olay Kimliği **193** içinde **Microsoft Windows Windows Uzaktan Yönetimi/Operational** günlük kayıtlarının güvenlik tanımlayıcısı (SID) ve hesap için bağlama kullanıcı adı ve kullanıcı olarak bir JEA her defasında Çalıştır oturum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ccec1-135">Event ID **193** in the **Microsoft-Windows-Windows Remote Management/Operational** log records the security identifier (SID) and account name for both the connecting user and run as user every time a JEA session is created.</span></span>

## <a name="session-transcripts"></a><span data-ttu-id="ccec1-136">Oturum dökümleri</span><span class="sxs-lookup"><span data-stu-id="ccec1-136">Session transcripts</span></span>

<span data-ttu-id="ccec1-137">Jea'yı her bir kullanıcı oturumu için bir döküm oluşturmak için yapılandırılmışsa, her kullanıcının eylemleri metin kopyasını belirtilen klasörde depolanır.</span><span class="sxs-lookup"><span data-stu-id="ccec1-137">If you configured JEA to create a transcript for each user session, a text copy of every user's actions will be stored in the specified folder.</span></span>

<span data-ttu-id="ccec1-138">Tüm döküm dizinleri bulmak için aşağıdaki komutu bilgisayarda yönetici olarak çalıştırın JEA ile yapılandırılmış:</span><span class="sxs-lookup"><span data-stu-id="ccec1-138">To find all transcript directories, run the following command as an administrator on the computer configured with JEA:</span></span>

```powershell
Get-PSSessionConfiguration | Where-Object { $_.TranscriptDirectory -ne $null } | Format-Table Name, TranscriptDirectory
```

<span data-ttu-id="ccec1-139">Transkript her zaman oturum başlatıldığında, oturum ve JEA kimliği atanmış bağlı kullanıcı hakkında bilgi ile başlar.</span><span class="sxs-lookup"><span data-stu-id="ccec1-139">Each transcript starts with information about the time the session started, which user connected to the session, and which JEA identity was assigned to them.</span></span>

```
**********************
Windows PowerShell transcript start
Start time: 20160710144736
Username: CONTOSO\Alice
RunAs User: WinRM Virtual Users\WinRM VA_1_CONTOSO_Alice
Machine: SERVER01 (Microsoft Windows NT 10.0.14393.0)
[...]
```

<span data-ttu-id="ccec1-140">Transkripti gövdesinde kullanıcının çağrılan her komut hakkında bilgileri günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="ccec1-140">In the body of the transcript, information is logged about each command the user invoked.</span></span>
<span data-ttu-id="ccec1-141">Yürütülen etkili komut hala belirleyebilirsiniz ancak kullanıcı çalıştırılan komut söz dizimi JEA oturumlarında komutları PowerShell uzaktan iletişim için dönüştürülme biçimini nedeniyle kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="ccec1-141">The exact syntax of the command the user ran is unavailable in JEA sessions due to the way commands are transformed for PowerShell remoting, however you can still determine the effective command that was executed.</span></span>
<span data-ttu-id="ccec1-142">Çalıştıran bir kullanıcıdan bir örnek dökümü kod parçacığı aşağıda verilmiştir `Get-Service Dns` bir JEA oturumda:</span><span class="sxs-lookup"><span data-stu-id="ccec1-142">Below is an example transcript snippet from a user running `Get-Service Dns` in a JEA session:</span></span>

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

<span data-ttu-id="ccec1-143">Bir kullanıcı çalıştırır, her komut için "CommandInvocation" satır cmdlet açıklayan yazılır veya kullanıcının çağrılan işlev.</span><span class="sxs-lookup"><span data-stu-id="ccec1-143">For each command a user runs, a "CommandInvocation" line will be written, describing the cmdlet or function the user invoked.</span></span>
<span data-ttu-id="ccec1-144">Her bir parametre ve komutu ile sağlanan değeri hakkında bilgi için her CommandInvocation ParameterBindings izleyin.</span><span class="sxs-lookup"><span data-stu-id="ccec1-144">ParameterBindings follow each CommandInvocation to tell you about each parameter and value that was supplied with the command.</span></span>
<span data-ttu-id="ccec1-145">Yukarıdaki örnekte, "ad" parametresi ' % s'değeri "Dns" "Get-Service" cmdlet için sağlanan görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ccec1-145">In the above example, you can see that the parameter "Name" was supplied the value "Dns" for the "Get-Service" cmdlet.</span></span>

<span data-ttu-id="ccec1-146">Her komutun çıktısı da bir CommandInvocation genellikle dışarı varsayılan tetikler.</span><span class="sxs-lookup"><span data-stu-id="ccec1-146">The output of each command will also trigger a CommandInvocation, usually to Out-Default.</span></span>
<span data-ttu-id="ccec1-147">Inputobject Out-Default, komuttan döndürülen PowerShell nesnedir.</span><span class="sxs-lookup"><span data-stu-id="ccec1-147">The InputObject of Out-Default is the PowerShell object returned from the command.</span></span>
<span data-ttu-id="ccec1-148">Bu nesnenin ayrıntılarını yazdırılır aşağıda yakından kullanıcı gördünüz yakından taklit eden birkaç satır kod.</span><span class="sxs-lookup"><span data-stu-id="ccec1-148">The details of that object are printed a few lines below, closely mimicking what the user would have seen.</span></span>

## <a name="see-also"></a><span data-ttu-id="ccec1-149">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="ccec1-149">See also</span></span>

- [<span data-ttu-id="ccec1-150">*PowerShell mavi takımın ♥* güvenlik blog gönderisi</span><span class="sxs-lookup"><span data-stu-id="ccec1-150">*PowerShell ♥ the Blue Team* blog post on security</span></span>](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)
