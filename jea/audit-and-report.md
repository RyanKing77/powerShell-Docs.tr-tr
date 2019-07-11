---
ms.date: 07/10/2019
keywords: jea, powershell, güvenlik
title: JEA'da raporlama ve denetleme
ms.openlocfilehash: 2afefe83acecc1fc3643d49766120ffecc25378f
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726746"
---
# <a name="auditing-and-reporting-on-jea"></a><span data-ttu-id="e5b7a-103">JEA'da raporlama ve denetleme</span><span class="sxs-lookup"><span data-stu-id="e5b7a-103">Auditing and Reporting on JEA</span></span>

<span data-ttu-id="e5b7a-104">JEA dağıttıktan sonra düzenli olarak bir JEA yapılandırma denetim gerekir.</span><span class="sxs-lookup"><span data-stu-id="e5b7a-104">After you've deployed JEA, you need to regularly audit the JEA configuration.</span></span> <span data-ttu-id="e5b7a-105">Yardımcı denetim doğru kişilerin JEA uç noktasına erişebildiğinden ve atanan rollerinin hala uygun değerlendirin.</span><span class="sxs-lookup"><span data-stu-id="e5b7a-105">Auditing helps you assess that the correct people have access to the JEA endpoint and their assigned roles are still appropriate.</span></span>

## <a name="find-registered-jea-sessions-on-a-machine"></a><span data-ttu-id="e5b7a-106">Bir makinede kayıtlı JEA oturumu bulun</span><span class="sxs-lookup"><span data-stu-id="e5b7a-106">Find registered JEA sessions on a machine</span></span>

<span data-ttu-id="e5b7a-107">Hangi JEA oturumlarının bir makinede kayıtlı denetlemek için kullanmak [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="e5b7a-107">To check which JEA sessions are registered on a machine, use the [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet.</span></span>

```powershell
# Filter for sessions that are configured as 'RestrictedRemoteServer' to find JEA-like session configurations
Get-PSSessionConfiguration | Where-Object { $_.SessionType -eq 'RestrictedRemoteServer' }
```

```Output
Name          : JEAMaintenance
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : CONTOSO\JEA_DNS_ADMINS AccessAllowed, CONTOSO\JEA_DNS_OPERATORS AccessAllowed,
                CONTOSO\JEA_DNS_AUDITORS AccessAllowed
```

<span data-ttu-id="e5b7a-108">Uç noktası için etkin hakları listelenen **izni** özelliği.</span><span class="sxs-lookup"><span data-stu-id="e5b7a-108">The effective rights for the endpoint are listed in the **Permission** property.</span></span> <span data-ttu-id="e5b7a-109">Bu kullanıcılar JEA uç noktasını bağlamak hakkına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="e5b7a-109">These users have the right to connect to the JEA endpoint.</span></span> <span data-ttu-id="e5b7a-110">Ancak, roller ve erişim sahibi oldukları komutları tarafından belirlenir **RoleDefinitions** özelliğinde [oturum yapılandırma dosyası](session-configurations.md) uç noktasını kaydetmek için kullanıldı.</span><span class="sxs-lookup"><span data-stu-id="e5b7a-110">However, the roles and commands they have access to is determined by the **RoleDefinitions** property in the [session configuration file](session-configurations.md) that was used to register the endpoint.</span></span> <span data-ttu-id="e5b7a-111">Genişletin **RoleDefinitions** kayıtlı bir JEA uç noktası rolü eşlemelerin değerlendirmek için özellik.</span><span class="sxs-lookup"><span data-stu-id="e5b7a-111">Expand the **RoleDefinitions** property to evaluate the role mappings in a registered JEA endpoint.</span></span>

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{
  Name = 'Role Capabilities'
  Expression = { $_.Value.RoleCapabilities }
}
```

## <a name="find-available-role-capabilities-on-the-machine"></a><span data-ttu-id="e5b7a-112">Makinede kullanılabilir rol işlevleri Bul</span><span class="sxs-lookup"><span data-stu-id="e5b7a-112">Find available role capabilities on the machine</span></span>

<span data-ttu-id="e5b7a-113">JEA alır rol özelliklerinden `.psrc` depolanan dosyaların **RoleCapabilities** klasörün içinde bir PowerShell modülü.</span><span class="sxs-lookup"><span data-stu-id="e5b7a-113">JEA gets role capabilities from the `.psrc` files stored in the **RoleCapabilities** folder inside a PowerShell module.</span></span> <span data-ttu-id="e5b7a-114">Aşağıdaki işlev bir bilgisayar üzerinde kullanılabilen tüm rol özellikleri bulur.</span><span class="sxs-lookup"><span data-stu-id="e5b7a-114">The following function finds all role capabilities available on a computer.</span></span>

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
    $results | Select-Object @{ Name = 'Name'; Expression = { $_.Name.TrimEnd('.psrc') }}, @{
        Name = 'Path'; Expression = { $_.FullName }
    } | Sort-Object Name
}
```

> [!NOTE]
> <span data-ttu-id="e5b7a-115">Bu işlev sonuçlardan sırasını mutlaka aynı adlı birden çok rol işlevleri paylaşırsanız, hangi rol işlevleri seçilir sırası değildir.</span><span class="sxs-lookup"><span data-stu-id="e5b7a-115">The order of results from this function is not necessarily the order in which the role capabilities will be selected if multiple role capabilities share the same name.</span></span>

## <a name="check-effective-rights-for-a-specific-user"></a><span data-ttu-id="e5b7a-116">Belirli bir kullanıcı için etkin haklarını denetleyin</span><span class="sxs-lookup"><span data-stu-id="e5b7a-116">Check effective rights for a specific user</span></span>

<span data-ttu-id="e5b7a-117">[Get-PSSessionCapability](/powershell/module/microsoft.powershell.core/Get-PSSessionCapability) cmdlet'i, bir kullanıcının grup üyeliklerini temel alan bir JEA uç noktası kullanılabilir tüm komutları numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="e5b7a-117">The [Get-PSSessionCapability](/powershell/module/microsoft.powershell.core/Get-PSSessionCapability) cmdlet enumerates all the commands available on a JEA endpoint based on a user's group memberships.</span></span>
<span data-ttu-id="e5b7a-118">Çıkışı `Get-PSSessionCapability` çalıştıran belirtilen kullanıcı için aynı `Get-Command -CommandType All` bir JEA oturumda.</span><span class="sxs-lookup"><span data-stu-id="e5b7a-118">The output of `Get-PSSessionCapability` is identical to that of the specified user running `Get-Command -CommandType All` in a JEA session.</span></span>

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

<span data-ttu-id="e5b7a-119">Bu cmdlet, kullanıcılarınızın bunları ek JEA hakkı grupların kalıcı üyesi değilseniz, bu ek izinleri yansıtmayabilir.</span><span class="sxs-lookup"><span data-stu-id="e5b7a-119">If your users aren't permanent members of groups that would grant them additional JEA rights, this cmdlet may not reflect those extra permissions.</span></span> <span data-ttu-id="e5b7a-120">Bu kullanırken, just-ın-time ayrıcalıklı erişim yönetimi sistemleri, kullanıcıların geçici olarak bir güvenlik grubuna ait olur.</span><span class="sxs-lookup"><span data-stu-id="e5b7a-120">This happens when using just-in-time privileged access management systems to allow users to temporarily belong to a security group.</span></span> <span data-ttu-id="e5b7a-121">Rolleri ve özellikleri, kullanıcıların yalnızca kullanıcıların işlerini başarıyla yapmak için gereken erişim düzeyini aldığından emin olmak için kullanıcı eşleme dikkatlice değerlendirin.</span><span class="sxs-lookup"><span data-stu-id="e5b7a-121">Carefully evaluate the mapping of users to roles and capabilities to ensure that users only get the level of access needed to do their jobs successfully.</span></span>

## <a name="powershell-event-logs"></a><span data-ttu-id="e5b7a-122">PowerShell olay günlükleri</span><span class="sxs-lookup"><span data-stu-id="e5b7a-122">PowerShell event logs</span></span>

<span data-ttu-id="e5b7a-123">Sistemde oturum modülü veya betik bloğu etkinleştirilirse, bir kullanıcı bir JEA oturumda çalışan her komut için Windows olay günlüğündeki olayları görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e5b7a-123">If you enabled module or script block logging on the system, you can see events in the Windows event logs for each command a user runs in a JEA session.</span></span> <span data-ttu-id="e5b7a-124">Bu olayları bulmak için açın **Microsoft-Windows-PowerShell/Operational** olay günlüğü ve olay kimliği ile olayları arayın **4104**.</span><span class="sxs-lookup"><span data-stu-id="e5b7a-124">To find these events, open **Microsoft-Windows-PowerShell/Operational** event log and look for events with event ID **4104**.</span></span>

<span data-ttu-id="e5b7a-125">Her olay günlüğü girişi, komutun çalıştırıldığı oturumu hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="e5b7a-125">Each event log entry includes information about the session in which the command was run.</span></span> <span data-ttu-id="e5b7a-126">JEA oturumlarında, olay hakkında bilgiler içerir **ConnectedUser** ve **farklıkullanıcı**.</span><span class="sxs-lookup"><span data-stu-id="e5b7a-126">For JEA sessions, the event includes information about the **ConnectedUser** and the **RunAsUser**.</span></span> <span data-ttu-id="e5b7a-127">**ConnectedUser** JEA oturumu oluşturan gerçek kullanıcı.</span><span class="sxs-lookup"><span data-stu-id="e5b7a-127">The **ConnectedUser** is the actual user who created the JEA session.</span></span> <span data-ttu-id="e5b7a-128">**Farklıkullanıcı** JEA komutu yürütmek için kullanılan hesaptır.</span><span class="sxs-lookup"><span data-stu-id="e5b7a-128">The **RunAsUser** is the account JEA used to execute the command.</span></span>

<span data-ttu-id="e5b7a-129">Uygulama olay günlüklerini göster tarafından yapılan değişiklikleri **farklıkullanıcı**.</span><span class="sxs-lookup"><span data-stu-id="e5b7a-129">Application event logs show changes being made by the **RunAsUser**.</span></span> <span data-ttu-id="e5b7a-130">Modülü ve komut dosyası ünlüğe kaydetme etkin olan belirli bir komut çağrısı geri izleme için gerekli olacak şekilde **ConnectedUser**.</span><span class="sxs-lookup"><span data-stu-id="e5b7a-130">So having module and script logging enabled is required to trace a specific command invocation back to the **ConnectedUser**.</span></span>

## <a name="application-event-logs"></a><span data-ttu-id="e5b7a-131">Uygulama olay günlükleri</span><span class="sxs-lookup"><span data-stu-id="e5b7a-131">Application event logs</span></span>

<span data-ttu-id="e5b7a-132">Dış uygulamalarla etkileşim kuran bir JEA oturumunda komutları çalıştırmak veya hizmetleri olayları kendi olay günlüklerine Kaydet.</span><span class="sxs-lookup"><span data-stu-id="e5b7a-132">Commands run in a JEA session that interact with external applications or services may log events to their own event logs.</span></span> <span data-ttu-id="e5b7a-133">PowerShell günlükleri ve dökümler aksine, diğer günlük mekanizmaları JEA oturumun bağlı olan kullanıcı yakalamayın.</span><span class="sxs-lookup"><span data-stu-id="e5b7a-133">Unlike PowerShell logs and transcripts, other logging mechanisms don't capture the connected user of the JEA session.</span></span> <span data-ttu-id="e5b7a-134">Bunun yerine, bu uygulamalar, yalnızca sanal Çalıştır kullanıcı oturum.</span><span class="sxs-lookup"><span data-stu-id="e5b7a-134">Instead, those applications only log the virtual run-as user.</span></span>
<span data-ttu-id="e5b7a-135">Başvurun gerek kimin komutun çalıştığını belirlemek için bir [oturumu döküm](#session-transcripts) veya PowerShell olay günlükleri uygulama olay günlüğünde gösterilen kullanıcı ve saat ile ilişkilendirin.</span><span class="sxs-lookup"><span data-stu-id="e5b7a-135">To determine who ran the command, you need to consult a [session transcript](#session-transcripts) or correlate PowerShell event logs with the time and user shown in the application event log.</span></span>

<span data-ttu-id="e5b7a-136">WinRM günlük Çalıştır bağlanan kullanıcının bir uygulama olay günlüğüne kullanıcılara bağıntısını da yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="e5b7a-136">The WinRM log can also help you correlate run-as users to the connecting user in an application event log.</span></span> <span data-ttu-id="e5b7a-137">Olay Kimliği **193** içinde **Microsoft Windows Windows Uzaktan Yönetimi/Operational** günlük her yeni JEA için güvenlik tanımlayıcısı (SID) ve hem bağlanan kullanıcı ve farklı çalıştır hesabı adını kullanıcı olarak kaydeder oturumu.</span><span class="sxs-lookup"><span data-stu-id="e5b7a-137">Event ID **193** in the **Microsoft-Windows-Windows Remote Management/Operational** log records the security identifier (SID) and account name for both the connecting user and run as user for every new JEA session.</span></span>

## <a name="session-transcripts"></a><span data-ttu-id="e5b7a-138">Oturum dökümleri</span><span class="sxs-lookup"><span data-stu-id="e5b7a-138">Session transcripts</span></span>

<span data-ttu-id="e5b7a-139">Jea'yı her bir kullanıcı oturumu için bir döküm oluşturmak için yapılandırılmışsa, her kullanıcının eylemleri metin kopyasını belirtilen klasörde depolanır.</span><span class="sxs-lookup"><span data-stu-id="e5b7a-139">If you configured JEA to create a transcript for each user session, a text copy of every user's actions are stored in the specified folder.</span></span>

<span data-ttu-id="e5b7a-140">Aşağıdaki komutu (Yönetici) olarak tüm döküm dizinleri bulur.</span><span class="sxs-lookup"><span data-stu-id="e5b7a-140">The following command (as an administrator) finds all transcript directories.</span></span>

```powershell
Get-PSSessionConfiguration |
  Where-Object { $_.TranscriptDirectory -ne $null } |
    Format-Table Name, TranscriptDirectory
```

<span data-ttu-id="e5b7a-141">Transkript her zaman oturum başlatıldığında, oturum ve JEA kimliği atanmış bağlı kullanıcı hakkında bilgi ile başlar.</span><span class="sxs-lookup"><span data-stu-id="e5b7a-141">Each transcript starts with information about the time the session started, which user connected to the session, and which JEA identity was assigned to them.</span></span>

```
**********************
Windows PowerShell transcript start
Start time: 20160710144736
Username: CONTOSO\Alice
RunAs User: WinRM Virtual Users\WinRM VA_1_CONTOSO_Alice
Machine: SERVER01 (Microsoft Windows NT 10.0.14393.0)
[...]
```

<span data-ttu-id="e5b7a-142">Transkripti gövdesinin kullanıcı çağrılan her komut hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="e5b7a-142">The body of the transcript contains information about each command the user invoked.</span></span> <span data-ttu-id="e5b7a-143">Kullanılan komut söz dizimi nedeniyle PowerShell uzaktan iletişim için komutları dönüştürülme biçimini JEA oturumlarda kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="e5b7a-143">The exact syntax of the command used is unavailable in JEA sessions because of the way commands are transformed for PowerShell remoting.</span></span> <span data-ttu-id="e5b7a-144">Ancak, yine de yürütülen etkili komut belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e5b7a-144">However, you can still determine the effective command that was executed.</span></span> <span data-ttu-id="e5b7a-145">Çalıştıran bir kullanıcıdan bir örnek dökümü kod parçacığı aşağıda verilmiştir `Get-Service Dns` bir JEA oturumda:</span><span class="sxs-lookup"><span data-stu-id="e5b7a-145">Below is an example transcript snippet from a user running `Get-Service Dns` in a JEA session:</span></span>

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

<span data-ttu-id="e5b7a-146">A **CommandInvocation** satır, bir kullanıcının her komut için yazılır.</span><span class="sxs-lookup"><span data-stu-id="e5b7a-146">A **CommandInvocation** line is written for each command a user runs.</span></span> <span data-ttu-id="e5b7a-147">**ParameterBindings** her parametresi ve değeri bu komutla birlikte kaydedin.</span><span class="sxs-lookup"><span data-stu-id="e5b7a-147">**ParameterBindings** record each parameter and value supplied with the command.</span></span> <span data-ttu-id="e5b7a-148">Önceki örnekte görebileceğiniz gibi parametre **adı** sağlanan değerle **Dns** için `Get-Service` cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="e5b7a-148">In the previous example, you can see that the parameter **Name** was supplied the with value **Dns** for the `Get-Service` cmdlet.</span></span>

<span data-ttu-id="e5b7a-149">Her çıkış komutunu da Tetikleyiciler bir **CommandInvocation**, genellikle `Out-Default`.</span><span class="sxs-lookup"><span data-stu-id="e5b7a-149">The output of each command also triggers a **CommandInvocation**, usually to `Out-Default`.</span></span> <span data-ttu-id="e5b7a-150">**Inputobject** , `Out-Default` komuttan PowerShell nesne döndürülür.</span><span class="sxs-lookup"><span data-stu-id="e5b7a-150">The **InputObject** of `Out-Default` is the PowerShell object returned from the command.</span></span> <span data-ttu-id="e5b7a-151">Bu nesnenin ayrıntılarını yazdırılır aşağıda yakından kullanıcı gördünüz yakından taklit eden birkaç satır kod.</span><span class="sxs-lookup"><span data-stu-id="e5b7a-151">The details of that object are printed a few lines below, closely mimicking what the user would have seen.</span></span>

## <a name="see-also"></a><span data-ttu-id="e5b7a-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e5b7a-152">See also</span></span>

[<span data-ttu-id="e5b7a-153">*PowerShell mavi takımın ♥* güvenlik blog gönderisi</span><span class="sxs-lookup"><span data-stu-id="e5b7a-153">*PowerShell ♥ the Blue Team* blog post on security</span></span>](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
