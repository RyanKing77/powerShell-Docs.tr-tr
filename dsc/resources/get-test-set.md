---
ms.date: 12/12/2018
keywords: DSC, PowerShell, yapılandırma, kurulum
title: Al-test-ayarla
ms.openlocfilehash: 68738107cd4a222a13dd4afa158f0370953158ad
ms.sourcegitcommit: 02eed65c526ef19cf952c2129f280bb5615bf0c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70215417"
---
# <a name="get-test-set"></a><span data-ttu-id="09e79-103">Al-test-ayarla</span><span class="sxs-lookup"><span data-stu-id="09e79-103">Get-Test-Set</span></span>

><span data-ttu-id="09e79-104">Şunun için geçerlidir: Windows PowerShell 4,0, Windows PowerShell 5,0</span><span class="sxs-lookup"><span data-stu-id="09e79-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

![Kaynak Edinme, Sınama ve Ayarlama](../media/get-test-set.png)

<span data-ttu-id="09e79-106">PowerShell Istenen durum yapılandırması, bir **Get**, **Test**ve **set** işlemi etrafında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="09e79-106">PowerShell Desired State Configuration is constructed around a **Get**, **Test**, and **Set** process.</span></span> <span data-ttu-id="09e79-107">DSC [kaynakları](resources.md) , bu işlemlerin her birini tamamlamaya yönelik yöntemler içerir.</span><span class="sxs-lookup"><span data-stu-id="09e79-107">DSC [resources](resources.md) each contains methods to complete each of these operations.</span></span> <span data-ttu-id="09e79-108">Bir [yapılandırmada](../configurations/configurations.md), kaynak bloklarını bir kaynağın **Get**, **Test**ve **set** yöntemlerinin parametreleri olacak şekilde belirten anahtarları dolduracak şekilde tanımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="09e79-108">In a [Configuration](../configurations/configurations.md), you define resource blocks to fill in keys that become parameters for a resource's **Get**, **Test**, and **Set** methods.</span></span>

<span data-ttu-id="09e79-109">Bu, bir **hizmet** kaynağı bloğunun sözdizimidir.</span><span class="sxs-lookup"><span data-stu-id="09e79-109">This is the syntax for a **Service** resource block.</span></span> <span data-ttu-id="09e79-110">**Hizmet** kaynağı Windows hizmetlerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="09e79-110">The **Service** resource configures Windows services.</span></span>

```syntax
Service [String] #ResourceName
{
    Name = [string]
    [BuiltInAccount = [string]{ LocalService | LocalSystem | NetworkService }]
    [Credential = [PSCredential]]
    [Dependencies = [string[]]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [DisplayName = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Path = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [StartupType = [string]{ Automatic | Disabled | Manual }]
    [State = [string]{ Running | Stopped }]
}
```

<span data-ttu-id="09e79-111">**Hizmet** kaynağının **Get**, **Test**ve **set** yöntemlerinin bu değerleri kabul eden parametre blokları olacaktır.</span><span class="sxs-lookup"><span data-stu-id="09e79-111">The **Get**, **Test**, and **Set** methods of the **Service** resource will have parameter blocks that accept these values.</span></span>

```powershell
    param
    (
        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [System.String]
        $Name,

        [System.String]
        [ValidateSet("Automatic", "Manual", "Disabled")]
        $StartupType,

        [System.String]
        [ValidateSet("LocalSystem", "LocalService", "NetworkService")]
        $BuiltInAccount,

        [System.Management.Automation.PSCredential]
        [ValidateNotNull()]
        $Credential,

        [System.String]
        [ValidateSet("Running", "Stopped")]
        $State="Running",

        [System.String]
        [ValidateNotNullOrEmpty()]
        $DisplayName,

        [System.String]
        [ValidateNotNullOrEmpty()]
        $Description,

        [System.String]
        [ValidateNotNullOrEmpty()]
        $Path,

        [System.String[]]
        [ValidateNotNullOrEmpty()]
        $Dependencies,

        [System.String]
        [ValidateSet("Present", "Absent")]
        $Ensure="Present"
    )
```

> [!NOTE]
> <span data-ttu-id="09e79-112">Kaynağı tanımlamak için kullanılan dil ve Yöntem **Get**, **Test**ve **set** yöntemlerinin nasıl tanımlanacağını belirler.</span><span class="sxs-lookup"><span data-stu-id="09e79-112">The language and method used to define the resource determines how the **Get**, **Test**, and **Set** methods will be defined.</span></span>

<span data-ttu-id="09e79-113">**Hizmet** kaynağında yalnızca bir gerekli anahtar (`Name`) bulunduğundan, bir **hizmet** bloğu kaynağı şu kadar basit olabilir:</span><span class="sxs-lookup"><span data-stu-id="09e79-113">Because the **Service** resource only has one required key (`Name`), a **Service** block resource could be as simple as this:</span></span>

```powershell
Configuration TestConfig
{
    Import-DSCResource -Name Service
    Node localhost
    {
        Service "MyService"
        {
            Name = "Spooler"
        }
    }
}
```

<span data-ttu-id="09e79-114">Yukarıdaki yapılandırmayı derlerken, bir anahtar için belirttiğiniz değerler oluşturulan ". mof" dosyasında depolanır.</span><span class="sxs-lookup"><span data-stu-id="09e79-114">When you compile the Configuration above, the values you specify for a key are stored in the ".mof" file that is generated.</span></span> <span data-ttu-id="09e79-115">Daha fazla bilgi için bkz. [MOF](/windows/desktop/wmisdk/managed-object-format--mof-).</span><span class="sxs-lookup"><span data-stu-id="09e79-115">For more information, see [MOF](/windows/desktop/wmisdk/managed-object-format--mof-).</span></span>

```
instance of MSFT_ServiceResource as $MSFT_ServiceResource1ref
{
SourceInfo = "::5::1::Service";
 ModuleName = "PsDesiredStateConfiguration";
 ResourceID = "[Service]MyService";
 Name = "Spooler";

ModuleVersion = "1.0";

 ConfigurationName = "Test";

};
```

<span data-ttu-id="09e79-116">Uygulandığında, [yerel Configuration Manager](../managing-nodes/metaConfig.md) (LCM) ". mof" dosyasındaki " `-Name` Kuyruklayıcı" değerini okur ve bunu, **"hizmetim" örneği için Get, test ve set yöntemlerinin parametresine iletir. Hizmet** kaynağı.</span><span class="sxs-lookup"><span data-stu-id="09e79-116">When applied, the [Local Configuration Manager](../managing-nodes/metaConfig.md) (LCM) will read the value "Spooler" from the ".mof" file, and pass it to the `-Name` parameter of the **Get**, **Test**, and **Set** methods for the "MyService" instance of the **Service** resource.</span></span>

## <a name="get"></a><span data-ttu-id="09e79-117">Alma</span><span class="sxs-lookup"><span data-stu-id="09e79-117">Get</span></span>

<span data-ttu-id="09e79-118">Bir kaynağın **Get** yöntemi, hedef düğümde yapılandırıldığı şekilde kaynağın durumunu alır.</span><span class="sxs-lookup"><span data-stu-id="09e79-118">The **Get** method of a resource, retrieves the state of the resource as it is configured on the target Node.</span></span> <span data-ttu-id="09e79-119">Bu durum bir [Hashtable](/powershell/module/microsoft.powershell.core/about/about_hash_tables)olarak döndürülür.</span><span class="sxs-lookup"><span data-stu-id="09e79-119">This state is returned as a [hashtable](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span></span> <span data-ttu-id="09e79-120">**Hashtable** 'ın anahtarları yapılandırılabilir değerler veya parametreler olacaktır, kaynak kabul eder.</span><span class="sxs-lookup"><span data-stu-id="09e79-120">The keys of the **hashtable** will be the configurable values, or parameters, the resource accepts.</span></span>

<span data-ttu-id="09e79-121">**Get** yöntemi doğrudan [Get-dscconfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet 'ine eşlenir.</span><span class="sxs-lookup"><span data-stu-id="09e79-121">The **Get** method maps directly to the [Get-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="09e79-122">' İ çağırdığınızda `Get-DSCConfiguration`, LCM, uygulanmış olan yapılandırmadaki her bir kaynağın **Get** yöntemini çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="09e79-122">When you call `Get-DSCConfiguration`, the LCM runs the **Get** method of each resource in the currently applied configuration.</span></span> <span data-ttu-id="09e79-123">LCM, her bir karşılık gelen kaynak örneğine parametre olarak ". mof" dosyasında depolanan anahtar değerlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="09e79-123">The LCM uses the key values stored in the ".mof" file as parameters to each corresponding resource instance.</span></span>

<span data-ttu-id="09e79-124">Bu, "biriktirici" hizmetini yapılandıran bir **hizmet** kaynağının örnek çıktısıdır.</span><span class="sxs-lookup"><span data-stu-id="09e79-124">This is sample output from a **Service** resource that configures the "Spooler" service.</span></span>

```output
ConfigurationName    : Test
DependsOn            :
ModuleName           : PsDesiredStateConfiguration
ModuleVersion        : 1.1
PsDscRunAsCredential :
ResourceId           : [Service]Spooler
SourceInfo           :
BuiltInAccount       : LocalSystem
Credential           :
Dependencies         : {RPCSS, http}
Description          : This service spools print jobs and handles interaction with the printer.  If you turn off
                       this service, you won’t be able to print or see your printers.
DisplayName          : Print Spooler
Ensure               :
Name                 : Spooler
Path                 : C:\WINDOWS\System32\spoolsv.exe
StartupType          : Automatic
State                : Running
Status               :
PSComputerName       :
CimClassName         : MSFT_ServiceResource
```

<span data-ttu-id="09e79-125">Çıktı, **hizmet** kaynağı tarafından yapılandırılabilen geçerli değer özelliklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="09e79-125">The output shows the current value properties configurable by the **Service** resource.</span></span>

```syntax
Service [String] #ResourceName
{
    Name = [string]
    [BuiltInAccount = [string]{ LocalService | LocalSystem | NetworkService }]
    [Credential = [PSCredential]]
    [Dependencies = [string[]]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [DisplayName = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Path = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [StartupType = [string]{ Automatic | Disabled | Manual }]
    [State = [string]{ Running | Stopped }]
}
```

## <a name="test"></a><span data-ttu-id="09e79-126">Test</span><span class="sxs-lookup"><span data-stu-id="09e79-126">Test</span></span>

<span data-ttu-id="09e79-127">Bir kaynağın **Test** yöntemi, hedef düğümün Şu anda kaynağın *istenen durumuyla*uyumlu olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="09e79-127">The **Test** method of a resource determines if the target node is currently compliant with the resource's *desired state*.</span></span> <span data-ttu-id="09e79-128">**Test** yöntemi, `$True` `$False` yalnızca düğümün uyumlu olup olmadığını belirtmek için öğesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="09e79-128">The **Test** method returns `$True` or `$False` only to indicate whether the Node is compliant.</span></span>
<span data-ttu-id="09e79-129">[Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)' ı çağırdığınızda, LCM geçerli olarak uygulanan yapılandırmadaki her bir kaynağın **Test** yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="09e79-129">When you call [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration), the LCM calls the **Test** method of each resource in the currently applied configuration.</span></span> <span data-ttu-id="09e79-130">LCM, her bir karşılık gelen kaynak örneğine parametre olarak ". mof" dosyasında depolanan anahtar değerlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="09e79-130">The LCM uses the key values stored in the ".mof" file as parameters to each corresponding resource instance.</span></span>

<span data-ttu-id="09e79-131">Tek bir kaynağın **testinin** `$False`sonucu varsa, `Test-DSCConfiguration` düğümün uyumlu olmadığını gösteren döndürür `$False` .</span><span class="sxs-lookup"><span data-stu-id="09e79-131">If the result of any individual resource's **Test** is `$False`, `Test-DSCConfiguration` returns `$False` indicating that the Node is not compliant.</span></span> <span data-ttu-id="09e79-132">Tüm kaynakların **Test** yöntemleri `$True`döndürülürse, `Test-DSCConfiguration` düğümün uyumlu olduğunu `$True` göstermek için döndürür.</span><span class="sxs-lookup"><span data-stu-id="09e79-132">If all resource's **Test** methods return `$True`, `Test-DSCConfiguration` returns `$True` to indicate that the Node is compliant.</span></span>

```powershell
Test-DSCConfiguration
```

```output
True
```

<span data-ttu-id="09e79-133">PowerShell 5,0 ' den başlayarak, `-Detailed` parametresi eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="09e79-133">Beginning in PowerShell 5.0, the `-Detailed` parameter was added.</span></span> <span data-ttu-id="09e79-134">Uyumlu `-Detailed` ve `Test-DSCConfiguration` uyumlu olmayan kaynaklar için sonuç koleksiyonları içeren bir nesne döndürme nedenlerini belirtme.</span><span class="sxs-lookup"><span data-stu-id="09e79-134">Specifying `-Detailed` causes `Test-DSCConfiguration` to return an object containing collections of results for compliant, and non-compliant resources.</span></span>

```powershell
Test-DSCConfiguration -Detailed
```

```output
PSComputerName  ResourcesInDesiredState        ResourcesNotInDesiredState     InDesiredState
--------------  -----------------------        --------------------------     --------------
localhost       {[Service]Spooler}                                            True
```

<span data-ttu-id="09e79-135">Daha fazla bilgi için bkz. [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)</span><span class="sxs-lookup"><span data-stu-id="09e79-135">For more information, see [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)</span></span>

## <a name="set"></a><span data-ttu-id="09e79-136">Ayarla</span><span class="sxs-lookup"><span data-stu-id="09e79-136">Set</span></span>

<span data-ttu-id="09e79-137">Bir kaynağın **set** yöntemi, düğümü kaynağın *istenen durumuyla*uyumlu hale getirmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="09e79-137">The **Set** method of a resource attempts to force the Node to become compliant with the resource's *desired state*.</span></span> <span data-ttu-id="09e79-138">**Set** yönteminin **ıdempotent**olması amaçlanmıştır, yani **küme** birden çok kez çalıştırılabilir ve hata olmadan her zaman aynı sonucu alabilir.</span><span class="sxs-lookup"><span data-stu-id="09e79-138">The **Set** method is meant to be **idempotent**, which means that **Set** could be run multiple times and always get the same result without errors.</span></span>  <span data-ttu-id="09e79-139">[Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration)çalıştırdığınızda, LCM, o anda uygulanan yapılandırmadaki her bir kaynak boyunca geçiş yapar.</span><span class="sxs-lookup"><span data-stu-id="09e79-139">When you run [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration), the LCM cycles through each resource in the currently applied configuration.</span></span> <span data-ttu-id="09e79-140">LCM, ". mof" dosyasındaki geçerli kaynak örneğinin anahtar değerlerini alır ve bunları **Test** yöntemi için parametreler olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="09e79-140">The LCM retrieves key values for the current resource instance from the ".mof" file and uses them as parameters for the **Test** method.</span></span> <span data-ttu-id="09e79-141">**Test** yöntemi döndürürse `$True`, düğüm geçerli kaynakla uyumludur ve **set** yöntemi atlanır.</span><span class="sxs-lookup"><span data-stu-id="09e79-141">If the **Test** method returns `$True`, the Node is compliant with the current resource, and the **Set** method is skipped.</span></span> <span data-ttu-id="09e79-142">**Test** döndürürse `$False`, düğüm uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="09e79-142">If the **Test** returns `$False`, the Node is non-compliant.</span></span>  <span data-ttu-id="09e79-143">LCM, kaynak örneğinin anahtar değerlerini kaynağın **ayarlama** yöntemine parametreler olarak geçirir ve düğümü uyumluluğa geri yükler.</span><span class="sxs-lookup"><span data-stu-id="09e79-143">The LCM passes the resource instance's key values as parameters to the resource's **Set** method, restoring the Node to compliance.</span></span>

<span data-ttu-id="09e79-144">`-Verbose` `Start-DSCConfiguration` Ve parametrelerinibelirterek,cmdlet'ininilerlemesiniizleyebilirsiniz`-Wait` .</span><span class="sxs-lookup"><span data-stu-id="09e79-144">By specifying the `-Verbose` and `-Wait` parameters, you can watch the progress of the `Start-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="09e79-145">Bu örnekte, düğüm zaten uyumludur.</span><span class="sxs-lookup"><span data-stu-id="09e79-145">In this example, the Node is already compliant.</span></span> <span data-ttu-id="09e79-146">Çıktı, set yönteminin atlandığını gösterir. `Verbose`</span><span class="sxs-lookup"><span data-stu-id="09e79-146">The `Verbose` output indicates that the **Set** method was skipped.</span></span>

```
PS> Start-DSCConfiguration -Verbose -Wait -UseExisting

VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' =
ApplyConfiguration,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' =
root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer SERVER01 with user sid
S-1-5-21-124525095-708259637-1543119021-1282804.
VERBOSE: [SERVER01]:                            [] Starting consistency engine.
VERBOSE: [SERVER01]:                            [] Checking consistency for current configuration.
VERBOSE: [SERVER01]:                            [DSCEngine] Importing the module
C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\DscResources\MSFT_ServiceResource\MSFT
_ServiceResource.psm1 in force mode.
VERBOSE: [SERVER01]: LCM:  [ Start  Resource ]  [[Service]Spooler]
VERBOSE: [SERVER01]: LCM:  [ Start  Test     ]  [[Service]Spooler]
VERBOSE: [SERVER01]:                            [[Service]Spooler] Importing the module MSFT_ServiceResource in
force mode.
VERBOSE: [SERVER01]: LCM:  [ End    Test     ]  [[Service]Spooler]  in 0.2540 seconds.
VERBOSE: [SERVER01]: LCM:  [ Skip   Set      ]  [[Service]Spooler]
VERBOSE: [SERVER01]: LCM:  [ End    Resource ]  [[Service]Spooler]
VERBOSE: [SERVER01]:                            [] Consistency check completed.
VERBOSE: Operation 'Invoke CimMethod' complete.
VERBOSE: Time taken for configuration job to complete is 1.379 seconds
```

## <a name="see-also"></a><span data-ttu-id="09e79-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="09e79-147">See also</span></span>

- [<span data-ttu-id="09e79-148">Azure Automation DSC genel bakış</span><span class="sxs-lookup"><span data-stu-id="09e79-148">Azure Automation DSC Overview</span></span>](https://docs.microsoft.com/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="09e79-149">SMB çekme sunucusu ayarlama</span><span class="sxs-lookup"><span data-stu-id="09e79-149">Setting up an SMB pull server</span></span>](../pull-server/pullServerSMB.md)
- [<span data-ttu-id="09e79-150">Çekme istemcisini yapılandırma</span><span class="sxs-lookup"><span data-stu-id="09e79-150">Configuring a pull client</span></span>](../pull-server/pullClientConfigID.md)
