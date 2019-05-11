---
ms.date: 12/12/2018
keywords: DSC, powershell, yapılandırma, Kurulum
title: Get-Test-Set
ms.openlocfilehash: e4aa7770bb5fc8b916b0c0a6488b1ccc0ef0ade9
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229522"
---
# <a name="get-test-set"></a><span data-ttu-id="644ed-103">Get-Test-Set</span><span class="sxs-lookup"><span data-stu-id="644ed-103">Get-Test-Set</span></span>

><span data-ttu-id="644ed-104">Şunun için geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="644ed-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

![Kaynak Edinme, Sınama ve Ayarlama](/media/get-test-set.png)

<span data-ttu-id="644ed-106">PowerShell Desired State Configuration çevresinde yapılandırılmıştır bir **alma**, **Test**, ve **ayarlamak** işlem.</span><span class="sxs-lookup"><span data-stu-id="644ed-106">PowerShell Desired State Configuration is constructed around a **Get**, **Test**, and **Set** process.</span></span> <span data-ttu-id="644ed-107">DSC [kaynakları](resources.md) her bu işlemlerden her biriyle tamamlamak için yöntemler içerir.</span><span class="sxs-lookup"><span data-stu-id="644ed-107">DSC [resources](resources.md) each contains methods to complete each of these operations.</span></span> <span data-ttu-id="644ed-108">İçinde bir [yapılandırma](../configurations/configurations.md), kaynağın parametrelerini haline anahtarlarını doldurmak için kaynak bloklar tanımladığınız **alma**, **Test**, ve **ayarlamak** yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="644ed-108">In a [Configuration](../configurations/configurations.md), you define resource blocks to fill in keys that become parameters for a resource's **Get**, **Test**, and **Set** methods.</span></span>

<span data-ttu-id="644ed-109">Bu sözdizimi aşağıdaki gibidir bir **hizmet** kaynak blok.</span><span class="sxs-lookup"><span data-stu-id="644ed-109">This is the syntax for a **Service** resource block.</span></span> <span data-ttu-id="644ed-110">**Hizmet** kaynak Windows Hizmetleri yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="644ed-110">The **Service** resource configures Windows services.</span></span>

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

<span data-ttu-id="644ed-111">**Alma**, **Test**, ve **ayarlamak** yöntemlerinin **hizmet** kaynak, bu değerleri kabul parametresi blokları olacaktır.</span><span class="sxs-lookup"><span data-stu-id="644ed-111">The **Get**, **Test**, and **Set** methods of the **Service** resource will have parameter blocks that accept these values.</span></span>

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
> <span data-ttu-id="644ed-112">Dil ve kaynağı tanımlamak için kullanılan yöntemi tanımlar nasıl **alma**, **Test**, ve **ayarlamak** yöntemleri tanımlanmasını.</span><span class="sxs-lookup"><span data-stu-id="644ed-112">The language and method used to define the resource determines how the **Get**, **Test**, and **Set** methods will be defined.</span></span>

<span data-ttu-id="644ed-113">Çünkü **hizmet** kaynak yalnızca bir gerekli anahtar var (`Name`), **hizmet** blok kaynak bu kadar basit olabilir:</span><span class="sxs-lookup"><span data-stu-id="644ed-113">Because the **Service** resource only has one required key (`Name`), a **Service** block resource could be as simple as this:</span></span>

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

<span data-ttu-id="644ed-114">Yukarıdaki yapılandırma derlediğinizde, bir anahtar için belirlediğiniz değerleri oluşturulan ".mof" dosyasında depolanır.</span><span class="sxs-lookup"><span data-stu-id="644ed-114">When you compile the Configuration above, the values you specify for a key are stored in the ".mof" file that is generated.</span></span> <span data-ttu-id="644ed-115">Daha fazla bilgi için [MOF](/windows/desktop/wmisdk/managed-object-format--mof-).</span><span class="sxs-lookup"><span data-stu-id="644ed-115">For more information, see [MOF](/windows/desktop/wmisdk/managed-object-format--mof-).</span></span>

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

<span data-ttu-id="644ed-116">Uygulandığında, [yerel Configuration Manager](../managing-nodes/metaConfig.md) (LCM) değer "Biriktirici" ".mof" dosyasından okuyun ve geçirin `-Name` parametresinin **alma**, **Test**, ve **ayarlamak** "MyService" örneği için yöntemleri **hizmet** kaynak.</span><span class="sxs-lookup"><span data-stu-id="644ed-116">When applied, the [Local Configuration Manager](../managing-nodes/metaConfig.md) (LCM) will read the value "Spooler" from the ".mof" file, and pass it to the `-Name` parameter of the **Get**, **Test**, and **Set** methods for the "MyService" instance of the **Service** resource.</span></span>

## <a name="get"></a><span data-ttu-id="644ed-117">Alma</span><span class="sxs-lookup"><span data-stu-id="644ed-117">Get</span></span>

<span data-ttu-id="644ed-118">**Alma** yöntemi olan bir kaynağın hedef düğümü olarak yapılandırıldığı şekilde kaynak durumunu alır.</span><span class="sxs-lookup"><span data-stu-id="644ed-118">The **Get** method of a resource, retrieves the state of the resource as it is configured on the target Node.</span></span> <span data-ttu-id="644ed-119">Bu durum olarak döndürülen bir [hashtable](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span><span class="sxs-lookup"><span data-stu-id="644ed-119">This state is returned as a [hashtable](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span></span> <span data-ttu-id="644ed-120">Anahtarları **hashtable** yapılandırılabilir değerleri veya parametrelerini kaynak kabul olacaktır.</span><span class="sxs-lookup"><span data-stu-id="644ed-120">The keys of the **hashtable** will be the configurable values, or parameters, the resource accepts.</span></span>

<span data-ttu-id="644ed-121">**Alma** yöntemi eşleştirir doğrudan [Get-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="644ed-121">The **Get** method maps directly to the [Get-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="644ed-122">Çağırdığınızda `Get-DSCConfiguration`, LCM çalıştırmalar **alma** uygulanmış yapılandırmasındaki her bir kaynağın yöntemi.</span><span class="sxs-lookup"><span data-stu-id="644ed-122">When you call `Get-DSCConfiguration`, the LCM runs the **Get** method of each resource in the currently applied configuration.</span></span> <span data-ttu-id="644ed-123">LCM karşılık gelen her bir kaynak örneği parametre olarak ".mof" dosyasında depolanan anahtar değerleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="644ed-123">The LCM uses the key values stored in the ".mof" file as parameters to each corresponding resource instance.</span></span>

<span data-ttu-id="644ed-124">Bu örnek çıktısı, bir **hizmet** "Biriktirici" hizmetini yapılandırır kaynak.</span><span class="sxs-lookup"><span data-stu-id="644ed-124">This is sample output from a **Service** resource that configures the "Spooler" service.</span></span>

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

<span data-ttu-id="644ed-125">Geçerli değer özellikleri çıktı tarafından yapılandırılabilir gösterir **hizmet** kaynak.</span><span class="sxs-lookup"><span data-stu-id="644ed-125">The output shows the current value properties configurable by the **Service** resource.</span></span>

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

## <a name="test"></a><span data-ttu-id="644ed-126">Test</span><span class="sxs-lookup"><span data-stu-id="644ed-126">Test</span></span>

<span data-ttu-id="644ed-127">**Test** yöntemi bir kaynak, hedef düğüm kaynak şu anda uyumlu olup olmadığını belirler *durumu istenen*.</span><span class="sxs-lookup"><span data-stu-id="644ed-127">The **Test** method of a resource determines if the target node is currently compliant with the resource's *desired state*.</span></span> <span data-ttu-id="644ed-128">**Test** yöntemi döndürür `$True` veya `$False` yalnızca düğüm uyumlu olup olmadığını belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="644ed-128">The **Test** method returns `$True` or `$False` only to indicate whether the Node is compliant.</span></span>
<span data-ttu-id="644ed-129">Çağırdığınızda [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration), LCM çağrıları **Test** uygulanmış yapılandırmasındaki her bir kaynağın yöntemi.</span><span class="sxs-lookup"><span data-stu-id="644ed-129">When you call [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration), the LCM calls the **Test** method of each resource in the currently applied configuration.</span></span> <span data-ttu-id="644ed-130">LCM karşılık gelen her bir kaynak örneği parametre olarak ".mof" dosyasında depolanan anahtar değerleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="644ed-130">The LCM uses the key values stored in the ".mof" file as parameters to each corresponding resource instance.</span></span>

<span data-ttu-id="644ed-131">Herhangi tek bir kaynağın sonucunu **Test** olduğu `$False`, `Test-DSCConfiguration` döndürür `$False` belirten düğüm uyumlu değil.</span><span class="sxs-lookup"><span data-stu-id="644ed-131">If the result of any individual resource's **Test** is `$False`, `Test-DSCConfiguration` returns `$False` indicating that the Node is not compliant.</span></span> <span data-ttu-id="644ed-132">Tüm kaynak **Test** yöntemleri dönüş `$True`, `Test-DSCConfiguration` döndürür `$True` düğümü uyumlu olduğunu göstermek için.</span><span class="sxs-lookup"><span data-stu-id="644ed-132">If all resource's **Test** methods return `$True`, `Test-DSCConfiguration` returns `$True` to indicate that the Node is compliant.</span></span>

```powershell
Test-DSCConfiguration
```

```output
True
```

<span data-ttu-id="644ed-133">PowerShell 5. 0'den itibaren `-Detailed` parametresi eklendi.</span><span class="sxs-lookup"><span data-stu-id="644ed-133">Beginning in PowerShell 5.0, the `-Detailed` parameter was added.</span></span> <span data-ttu-id="644ed-134">Belirtme `-Detailed` neden `Test-DSCConfiguration` koleksiyonları uyumlu ve uyumlu olmayan kaynaklar için sonuçları içeren bir nesne döndürmek için.</span><span class="sxs-lookup"><span data-stu-id="644ed-134">Specifying `-Detailed` causes `Test-DSCConfiguration` to return an object containing collections of results for compliant, and non-compliant resources.</span></span>

```powershell
Test-DSCConfiguration -Detailed
```

```output
PSComputerName  ResourcesInDesiredState        ResourcesNotInDesiredState     InDesiredState
--------------  -----------------------        --------------------------     --------------
localhost       {[Service]Spooler}                                            True
```

<span data-ttu-id="644ed-135">Daha fazla bilgi için [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)</span><span class="sxs-lookup"><span data-stu-id="644ed-135">For more information, see [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)</span></span>

## <a name="set"></a><span data-ttu-id="644ed-136">Ayarla</span><span class="sxs-lookup"><span data-stu-id="644ed-136">Set</span></span>

<span data-ttu-id="644ed-137">**Ayarlamak** yöntemi olan bir kaynağın çalışır kaynağın ile uyumlu olması için düğüm zorlamak *durumu istenen*.</span><span class="sxs-lookup"><span data-stu-id="644ed-137">The **Set** method of a resource attempts to force the Node to become compliant with the resource's *desired state*.</span></span> <span data-ttu-id="644ed-138">**Ayarlamak** yöntemi olacak şekilde tasarlanmıştır **etkili**, anlamına **ayarlamak** birden çok kez çalıştırın ve her zaman hata olmadan aynı sonucu elde olabilir.</span><span class="sxs-lookup"><span data-stu-id="644ed-138">The **Set** method is meant to be **idempotent**, which means that **Set** could be run multiple times and always get the same result without errors.</span></span>  <span data-ttu-id="644ed-139">Çalıştırdığınızda [Başlat-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration), her bir kaynak şu anda uygulanan yapılandırmasında LCM başlatıldıkları.</span><span class="sxs-lookup"><span data-stu-id="644ed-139">When you run [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration), the LCM cycles through each resource in the currently applied configuration.</span></span> <span data-ttu-id="644ed-140">LCM ".mof" dosyasından geçerli kaynak örneği için anahtar değerlerini alır ve bunları için parametre olarak kullanan **Test** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="644ed-140">The LCM retrieves key values for the current resource instance from the ".mof" file and uses them as parameters for the **Test** method.</span></span> <span data-ttu-id="644ed-141">Varsa **Test** yöntemi döndürür `$True`, düğüm geçerli kaynak ile uyumludur ve **ayarlamak** yöntemi atlandı.</span><span class="sxs-lookup"><span data-stu-id="644ed-141">If the **Test** method returns `$True`, the Node is compliant with the current resource, and the **Set** method is skipped.</span></span> <span data-ttu-id="644ed-142">Varsa **Test** döndürür `$False`, uyumlu olmayan bir düğümdür.</span><span class="sxs-lookup"><span data-stu-id="644ed-142">If the **Test** returns `$False`, the Node is non-compliant.</span></span>  <span data-ttu-id="644ed-143">LCM kaynak örneğinin anahtar değerleri parametre olarak kaynağın geçirir **ayarlamak** düğümü uyumluluk için geri yükleme yöntemi.</span><span class="sxs-lookup"><span data-stu-id="644ed-143">The LCM passes the resource instance's key values as parameters to the resource's **Set** method, restoring the Node to compliance.</span></span>

<span data-ttu-id="644ed-144">Belirterek `-Verbose` ve `-Wait` parametreleri, ilerleme durumunu izleyebilir `Start-DSCConfiguration` cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="644ed-144">By specifying the `-Verbose` and `-Wait` parameters, you can watch the progress of the `Start-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="644ed-145">Bu örnekte, bir düğüm zaten uyumludur.</span><span class="sxs-lookup"><span data-stu-id="644ed-145">In this example, the Node is already compliant.</span></span> <span data-ttu-id="644ed-146">`Verbose` Çıkış gösterir **ayarlamak** yöntemi atlandı.</span><span class="sxs-lookup"><span data-stu-id="644ed-146">The `Verbose` output indicates that the **Set** method was skipped.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="644ed-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="644ed-147">See also</span></span>

- [<span data-ttu-id="644ed-148">Azure Automation DSC genel bakış</span><span class="sxs-lookup"><span data-stu-id="644ed-148">Azure Automation DSC Overview</span></span>](https://docs.microsoft.com/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="644ed-149">Bir SMB çekme sunucusu ayarlama</span><span class="sxs-lookup"><span data-stu-id="644ed-149">Setting up an SMB pull server</span></span>](../pull-server/pullServerSMB.md)
- [<span data-ttu-id="644ed-150">Çekme istemcisi yapılandırma</span><span class="sxs-lookup"><span data-stu-id="644ed-150">Configuring a pull client</span></span>](../pull-server/pullClientConfigID.md)
