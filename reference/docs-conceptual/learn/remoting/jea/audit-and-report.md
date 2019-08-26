---
ms.date: 07/10/2019
keywords: Jea, PowerShell, güvenlik
title: JEA 'da denetim ve raporlama
ms.openlocfilehash: 2afefe83acecc1fc3643d49766120ffecc25378f
ms.sourcegitcommit: e894ed833cef57967cdaf002f8c883f66864e836
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2019
ms.locfileid: "70017926"
---
# <a name="auditing-and-reporting-on-jea"></a><span data-ttu-id="a325f-103">JEA 'da denetim ve raporlama</span><span class="sxs-lookup"><span data-stu-id="a325f-103">Auditing and Reporting on JEA</span></span>

<span data-ttu-id="a325f-104">JEA 'yı dağıttıktan sonra, JEA yapılandırmasını düzenli olarak denetlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a325f-104">After you've deployed JEA, you need to regularly audit the JEA configuration.</span></span> <span data-ttu-id="a325f-105">Denetim, doğru kişilerin JEA uç noktasına erişiminin olduğunu ve atanan rollerinin hala uygun olduğunu değerlendirmenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="a325f-105">Auditing helps you assess that the correct people have access to the JEA endpoint and their assigned roles are still appropriate.</span></span>

## <a name="find-registered-jea-sessions-on-a-machine"></a><span data-ttu-id="a325f-106">Bir makinede kayıtlı JEA oturumlarını bulma</span><span class="sxs-lookup"><span data-stu-id="a325f-106">Find registered JEA sessions on a machine</span></span>

<span data-ttu-id="a325f-107">Bir makineye hangi JEA oturumlarının kaydedildiğini denetlemek için [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet 'ini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a325f-107">To check which JEA sessions are registered on a machine, use the [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet.</span></span>

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

<span data-ttu-id="a325f-108">Uç nokta için geçerli haklar, **izin** özelliğinde listelenir.</span><span class="sxs-lookup"><span data-stu-id="a325f-108">The effective rights for the endpoint are listed in the **Permission** property.</span></span> <span data-ttu-id="a325f-109">Bu kullanıcıların JEA uç noktasına bağlanma hakkı vardır.</span><span class="sxs-lookup"><span data-stu-id="a325f-109">These users have the right to connect to the JEA endpoint.</span></span> <span data-ttu-id="a325f-110">Ancak, erişimi olan roller ve komutlar, uç noktasını kaydetmek için kullanılan [oturum yapılandırma dosyasındaki](session-configurations.md) **roledefinitions** özelliği tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="a325f-110">However, the roles and commands they have access to is determined by the **RoleDefinitions** property in the [session configuration file](session-configurations.md) that was used to register the endpoint.</span></span> <span data-ttu-id="a325f-111">Kayıtlı bir JEA uç noktasındaki rol eşlemelerini değerlendirmek için **Roledefinitions** özelliğini genişletin.</span><span class="sxs-lookup"><span data-stu-id="a325f-111">Expand the **RoleDefinitions** property to evaluate the role mappings in a registered JEA endpoint.</span></span>

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{
  Name = 'Role Capabilities'
  Expression = { $_.Value.RoleCapabilities }
}
```

## <a name="find-available-role-capabilities-on-the-machine"></a><span data-ttu-id="a325f-112">Makinede kullanılabilir rol yeteneklerini bul</span><span class="sxs-lookup"><span data-stu-id="a325f-112">Find available role capabilities on the machine</span></span>

<span data-ttu-id="a325f-113">Jea, bir PowerShell modülü içindeki `.psrc` **rolecapabilities** klasöründe depolanan dosyalardan rol özellikleri alır.</span><span class="sxs-lookup"><span data-stu-id="a325f-113">JEA gets role capabilities from the `.psrc` files stored in the **RoleCapabilities** folder inside a PowerShell module.</span></span> <span data-ttu-id="a325f-114">Aşağıdaki işlev bir bilgisayardaki kullanılabilir tüm rol yeteneklerini bulur.</span><span class="sxs-lookup"><span data-stu-id="a325f-114">The following function finds all role capabilities available on a computer.</span></span>

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
> <span data-ttu-id="a325f-115">Bu işlevden sonuçların sırası, birden çok rol özelliği aynı adı paylaşıyorsa rol yeteneklerinin seçilme sırası olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a325f-115">The order of results from this function is not necessarily the order in which the role capabilities will be selected if multiple role capabilities share the same name.</span></span>

## <a name="check-effective-rights-for-a-specific-user"></a><span data-ttu-id="a325f-116">Belirli bir kullanıcı için geçerli hakları denetleme</span><span class="sxs-lookup"><span data-stu-id="a325f-116">Check effective rights for a specific user</span></span>

<span data-ttu-id="a325f-117">[Get-PSSessionCapability](/powershell/module/microsoft.powershell.core/Get-PSSessionCapability) cmdlet 'i, BIR Jea uç noktasındaki kullanılabilir tüm komutları bir kullanıcının grup üyeliğine göre numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="a325f-117">The [Get-PSSessionCapability](/powershell/module/microsoft.powershell.core/Get-PSSessionCapability) cmdlet enumerates all the commands available on a JEA endpoint based on a user's group memberships.</span></span>
<span data-ttu-id="a325f-118">Çıkışı `Get-PSSessionCapability` , bir Jea oturumunda çalışan `Get-Command -CommandType All` belirtilen kullanıcı ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="a325f-118">The output of `Get-PSSessionCapability` is identical to that of the specified user running `Get-Command -CommandType All` in a JEA session.</span></span>

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

<span data-ttu-id="a325f-119">Kullanıcılarınız, bunlara ek JEA hakları verecek grupların kalıcı üyeleri değilse, bu cmdlet bu ek izinleri yansıtmayabilir.</span><span class="sxs-lookup"><span data-stu-id="a325f-119">If your users aren't permanent members of groups that would grant them additional JEA rights, this cmdlet may not reflect those extra permissions.</span></span> <span data-ttu-id="a325f-120">Bu durum, kullanıcıların geçici olarak bir güvenlik grubuna ait olmasını sağlamak için tam zamanında ayrıcalıklı erişim yönetimi sistemleri kullanılırken meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="a325f-120">This happens when using just-in-time privileged access management systems to allow users to temporarily belong to a security group.</span></span> <span data-ttu-id="a325f-121">Kullanıcıların yalnızca işlerini başarılı bir şekilde yapması için gereken erişim düzeyini aldığından emin olmak için kullanıcıların rol ve yeteneklere eşlemesini dikkatle değerlendirin.</span><span class="sxs-lookup"><span data-stu-id="a325f-121">Carefully evaluate the mapping of users to roles and capabilities to ensure that users only get the level of access needed to do their jobs successfully.</span></span>

## <a name="powershell-event-logs"></a><span data-ttu-id="a325f-122">PowerShell olay günlükleri</span><span class="sxs-lookup"><span data-stu-id="a325f-122">PowerShell event logs</span></span>

<span data-ttu-id="a325f-123">Sistemde modül veya betik bloğu günlüğünü etkinleştirdiyseniz, bir kullanıcının JEA oturumunda çalıştırdığı her komut için Windows olay günlüklerinde olayları görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a325f-123">If you enabled module or script block logging on the system, you can see events in the Windows event logs for each command a user runs in a JEA session.</span></span> <span data-ttu-id="a325f-124">Bu olayları bulmak için **Microsoft-Windows-PowerShell/işletimsel** olay günlüğünü açın ve olay kimliği **4104**olan olayları arayın.</span><span class="sxs-lookup"><span data-stu-id="a325f-124">To find these events, open **Microsoft-Windows-PowerShell/Operational** event log and look for events with event ID **4104**.</span></span>

<span data-ttu-id="a325f-125">Her olay günlüğü girişi, komutun çalıştırıldığı oturum hakkındaki bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="a325f-125">Each event log entry includes information about the session in which the command was run.</span></span> <span data-ttu-id="a325f-126">JEA oturumlarında, olay **connecteduser** ve **RunAsUser**hakkındaki bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="a325f-126">For JEA sessions, the event includes information about the **ConnectedUser** and the **RunAsUser**.</span></span> <span data-ttu-id="a325f-127">**Connecteduser** , Jea oturumunu oluşturan gerçek Kullanıcı.</span><span class="sxs-lookup"><span data-stu-id="a325f-127">The **ConnectedUser** is the actual user who created the JEA session.</span></span> <span data-ttu-id="a325f-128">**RunAsUser** , komutu yürütmek için kullanılan Jea hesabıdır.</span><span class="sxs-lookup"><span data-stu-id="a325f-128">The **RunAsUser** is the account JEA used to execute the command.</span></span>

<span data-ttu-id="a325f-129">Uygulama olay günlükleri, **RunAsUser**tarafından yapılan değişiklikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="a325f-129">Application event logs show changes being made by the **RunAsUser**.</span></span> <span data-ttu-id="a325f-130">Bu nedenle, belirli bir komut çağrısını **Connecteduser**'a geri izlemek için modül ve betik günlüğü 'nün etkin olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a325f-130">So having module and script logging enabled is required to trace a specific command invocation back to the **ConnectedUser**.</span></span>

## <a name="application-event-logs"></a><span data-ttu-id="a325f-131">Uygulama olay günlükleri</span><span class="sxs-lookup"><span data-stu-id="a325f-131">Application event logs</span></span>

<span data-ttu-id="a325f-132">Dış uygulamalarla veya hizmetlerle etkileşime geçen bir JEA oturumunda çalıştırılan komutlar, olayları kendi olay günlüklerine kaydeder.</span><span class="sxs-lookup"><span data-stu-id="a325f-132">Commands run in a JEA session that interact with external applications or services may log events to their own event logs.</span></span> <span data-ttu-id="a325f-133">PowerShell günlüklerinin ve döküm dosyalarından farklı olarak, diğer oturum açma mekanizmaları JEA oturumunun bağlı kullanıcısını yakalamaz.</span><span class="sxs-lookup"><span data-stu-id="a325f-133">Unlike PowerShell logs and transcripts, other logging mechanisms don't capture the connected user of the JEA session.</span></span> <span data-ttu-id="a325f-134">Bunun yerine, bu uygulamalar yalnızca sanal farklı çalıştır kullanıcısını günlüğe kaydeder.</span><span class="sxs-lookup"><span data-stu-id="a325f-134">Instead, those applications only log the virtual run-as user.</span></span>
<span data-ttu-id="a325f-135">Komutu kimin çalıştırdığını öğrenmek için, bir [oturum döküm dosyasına](#session-transcripts) danışmanız veya PowerShell olay günlüklerinin uygulama olay günlüğünde gösterilen zaman ve kullanıcıyla ilişkilendirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="a325f-135">To determine who ran the command, you need to consult a [session transcript](#session-transcripts) or correlate PowerShell event logs with the time and user shown in the application event log.</span></span>

<span data-ttu-id="a325f-136">WinRM günlüğü aynı zamanda bir uygulama olay günlüğündeki bağlanan kullanıcıyla farklı çalıştır kullanıcılarını ilişkilendirmenize yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="a325f-136">The WinRM log can also help you correlate run-as users to the connecting user in an application event log.</span></span> <span data-ttu-id="a325f-137">**Microsoft-Windows-Windows Uzaktan Yönetimi/işletimsel** GÜNLÜĞÜNDE olay kimliği **193** , hem bağlanan kullanıcı hem de her yeni Jea oturumunda Kullanıcı olarak Çalıştır ' ın güvenlik tanımlayıcısını (SID) ve hesap adını kaydeder.</span><span class="sxs-lookup"><span data-stu-id="a325f-137">Event ID **193** in the **Microsoft-Windows-Windows Remote Management/Operational** log records the security identifier (SID) and account name for both the connecting user and run as user for every new JEA session.</span></span>

## <a name="session-transcripts"></a><span data-ttu-id="a325f-138">Oturum yazılı betikleri</span><span class="sxs-lookup"><span data-stu-id="a325f-138">Session transcripts</span></span>

<span data-ttu-id="a325f-139">JEA 'yı her Kullanıcı oturumu için bir döküm oluşturacak şekilde yapılandırdıysanız, her kullanıcının eylemlerinin bir metin kopyası belirtilen klasörde depolanır.</span><span class="sxs-lookup"><span data-stu-id="a325f-139">If you configured JEA to create a transcript for each user session, a text copy of every user's actions are stored in the specified folder.</span></span>

<span data-ttu-id="a325f-140">Aşağıdaki komut (yönetici olarak) tüm döküm dizinlerini bulur.</span><span class="sxs-lookup"><span data-stu-id="a325f-140">The following command (as an administrator) finds all transcript directories.</span></span>

```powershell
Get-PSSessionConfiguration |
  Where-Object { $_.TranscriptDirectory -ne $null } |
    Format-Table Name, TranscriptDirectory
```

<span data-ttu-id="a325f-141">Her döküm, oturum başladığı saat, oturuma bağlanan kullanıcı ve kendisine hangi JEA kimliği atandığını belirten bilgilerle başlar.</span><span class="sxs-lookup"><span data-stu-id="a325f-141">Each transcript starts with information about the time the session started, which user connected to the session, and which JEA identity was assigned to them.</span></span>

```
**********************
Windows PowerShell transcript start
Start time: 20160710144736
Username: CONTOSO\Alice
RunAs User: WinRM Virtual Users\WinRM VA_1_CONTOSO_Alice
Machine: SERVER01 (Microsoft Windows NT 10.0.14393.0)
[...]
```

<span data-ttu-id="a325f-142">Döküm gövdesi kullanıcının çağırılabilen her komutla ilgili bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="a325f-142">The body of the transcript contains information about each command the user invoked.</span></span> <span data-ttu-id="a325f-143">PowerShell uzaktan iletişim için, komutların dönüştürülebildiğinden, kullanılan komutun tam sözdizimi JEA oturumlarında kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="a325f-143">The exact syntax of the command used is unavailable in JEA sessions because of the way commands are transformed for PowerShell remoting.</span></span> <span data-ttu-id="a325f-144">Ancak, yürütülen etkin komutu yine de belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a325f-144">However, you can still determine the effective command that was executed.</span></span> <span data-ttu-id="a325f-145">Aşağıda, bir Jea oturumunda çalışan `Get-Service Dns` kullanıcıdan bir örnek döküm kod parçacığı verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="a325f-145">Below is an example transcript snippet from a user running `Get-Service Dns` in a JEA session:</span></span>

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

<span data-ttu-id="a325f-146">Bir kullanıcı tarafından çalıştırılan her komut için bir **Commandinvocation** satırı yazılır.</span><span class="sxs-lookup"><span data-stu-id="a325f-146">A **CommandInvocation** line is written for each command a user runs.</span></span> <span data-ttu-id="a325f-147">**ParameterBindings** , komutuyla sağlanan her parametreyi ve değeri kaydeder.</span><span class="sxs-lookup"><span data-stu-id="a325f-147">**ParameterBindings** record each parameter and value supplied with the command.</span></span> <span data-ttu-id="a325f-148">Önceki örnekte, parametre `Get-Service` **adının** cmdlet için değeri **DNS** ile birlikte sağlanmış olduğunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a325f-148">In the previous example, you can see that the parameter **Name** was supplied the with value **Dns** for the `Get-Service` cmdlet.</span></span>

<span data-ttu-id="a325f-149">Her komutun çıktısı aynı zamanda bir **Commandinvocation**(genellikle olarak `Out-Default`) tetikler.</span><span class="sxs-lookup"><span data-stu-id="a325f-149">The output of each command also triggers a **CommandInvocation**, usually to `Out-Default`.</span></span> <span data-ttu-id="a325f-150">**InputObject** `Out-Default` , komutundan döndürülen PowerShell nesnesidir.</span><span class="sxs-lookup"><span data-stu-id="a325f-150">The **InputObject** of `Out-Default` is the PowerShell object returned from the command.</span></span> <span data-ttu-id="a325f-151">Bu nesnenin ayrıntıları aşağıda birkaç satır yazdırılır, bu da kullanıcının gördükiyle ilgili daha yakından bir şeydir.</span><span class="sxs-lookup"><span data-stu-id="a325f-151">The details of that object are printed a few lines below, closely mimicking what the user would have seen.</span></span>

## <a name="see-also"></a><span data-ttu-id="a325f-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a325f-152">See also</span></span>

[<span data-ttu-id="a325f-153">Güvenlik *Için mavi ekip blog gönderisi ♥ PowerShell*</span><span class="sxs-lookup"><span data-stu-id="a325f-153">*PowerShell ♥ the Blue Team* blog post on security</span></span>](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
