---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC kaynaklarında hata ayıklama
ms.openlocfilehash: c088e13a25ba31ceebaf52b2d24b5d32b96ae2fc
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076812"
---
# <a name="debugging-dsc-resources"></a><span data-ttu-id="9fa33-103">DSC kaynaklarında hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="9fa33-103">Debugging DSC resources</span></span>

> <span data-ttu-id="9fa33-104">Uygulama hedefi: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="9fa33-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="9fa33-105">PowerShell 5. 0'da, yeni bir özellik Desired State Configuration (bir DSC kaynağı bir yapılandırma uygulanmakta olduğu gibi hata ayıklama olanak tanıyan DSC içinde) kullanıma sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="9fa33-105">In PowerShell 5.0, a new feature was introduced in Desired State Configuration (DSC) that allows you to debug a DSC resource as a configuration is being applied.</span></span>

## <a name="enabling-dsc-debugging"></a><span data-ttu-id="9fa33-106">DSC hata ayıklamayı etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="9fa33-106">Enabling DSC debugging</span></span>
<span data-ttu-id="9fa33-107">Bir kaynak ayıklayabilirsiniz önce çağrı yaparak hata ayıklamayı etkinleştirmek sahip [etkinleştir DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="9fa33-107">Before you can debug a resource, you have to enable debugging by calling the [Enable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug) cmdlet.</span></span>
<span data-ttu-id="9fa33-108">Bu cmdlet zorunlu bir parametre alır **BreakAll**.</span><span class="sxs-lookup"><span data-stu-id="9fa33-108">This cmdlet takes a mandatory parameter, **BreakAll**.</span></span>

<span data-ttu-id="9fa33-109">Hata ayıklama yapılan bir çağrının sonucu bakarak etkinleştirildiğini doğrulayın [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager).</span><span class="sxs-lookup"><span data-stu-id="9fa33-109">You can verify that debugging has been enabled by looking at the result of a call to [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager).</span></span>

<span data-ttu-id="9fa33-110">Aşağıdaki PowerShell çıktısı, hata ayıklamayı etkinleştirme sonucunu göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="9fa33-110">The following PowerShell output shows the result of enabling debugging:</span></span>


```powershell
PS C:\DebugTest> $LCM = Get-DscLocalConfigurationManager

PS C:\DebugTest> $LCM.DebugMode
NONE

PS C:\DebugTest> Enable-DscDebug -BreakAll

PS C:\DebugTest> $LCM = Get-DscLocalConfigurationManager

PS C:\DebugTest> $LCM.DebugMode
ForceModuleImport
ResourceScriptBreakAll

PS C:\DebugTest>
```


## <a name="starting-a-configuration-with-debug-enabled"></a><span data-ttu-id="9fa33-111">Bir yapılandırma ile etkin hata ayıklama başlatılıyor</span><span class="sxs-lookup"><span data-stu-id="9fa33-111">Starting a configuration with debug enabled</span></span>
<span data-ttu-id="9fa33-112">DSC kaynak hata ayıklamak için bu kaynağa çağıran bir yapılandırma başlatın.</span><span class="sxs-lookup"><span data-stu-id="9fa33-112">To debug a DSC resource, you start a configuration that calls that resource.</span></span>
<span data-ttu-id="9fa33-113">Bu örnekte, çağıran basit bir yapılandırma sırasında atacağız **WindowsFeature** kaynağı "WindowsPowerShellWebAccess" özelliği yüklü olduğundan emin olun:</span><span class="sxs-lookup"><span data-stu-id="9fa33-113">For this example, we'll look at a simple configuration that calls the **WindowsFeature** resource to ensure that the "WindowsPowerShellWebAccess" feature is installed:</span></span>

```powershell
Configuration PSWebAccess
    {
    Import-DscResource -ModuleName 'PsDesiredStateConfiguration'
    Node localhost
        {
        WindowsFeature PSWA
            {
            Name = 'WindowsPowerShellWebAccess'
            Ensure = 'Present'
            }
        }
    }
PSWebAccess
```
<span data-ttu-id="9fa33-114">Yapılandırma derledikten sonra Başlat, çağırarak [Başlat-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).</span><span class="sxs-lookup"><span data-stu-id="9fa33-114">After compiling the configuration, start it by calling [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).</span></span>
<span data-ttu-id="9fa33-115">Yerel Configuration Manager (LCM) yapılandırma ilk kaynağına çağırdığında yapılandırma durdurur.</span><span class="sxs-lookup"><span data-stu-id="9fa33-115">The configuration will stop when the Local Configuration Manager (LCM) calls into the first resource in the configuration.</span></span>
<span data-ttu-id="9fa33-116">Kullanırsanız `-Verbose` ve `-Wait` parametreleri, hata ayıklamayı başlatmak için girmeniz gereken satırları çıktıyı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="9fa33-116">If you use the `-Verbose` and `-Wait` parameters, the output displays the lines you need to enter to start debugging.</span></span>

```powershell
Start-DscConfiguration .\PSWebAccess -Wait -Verbose
VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' = SendConfigurationApply,'className' = MSFT_DSCLocalConfiguration
Manager,'namespaceName' = root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer TEST-SRV with user sid S-1-5-21-2127521184-1604012920-1887927527-108583.
VERBOSE: An LCM method call arrived from computer TEST-SRV with user sid S-1-5-21-2127521184-1604012920-1887927527-108583.
VERBOSE: [TEST-SRV]: LCM:  [ Start  Set      ]
WARNING: [TEST-SRV]:                            [DSCEngine] Warning LCM is in Debug 'ResourceScriptBreakAll' mode.  Resource script processing will
be stopped to wait for PowerShell script debugger to attach.
VERBOSE: [TEST-SRV]:                            [DSCEngine] Importing the module C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateCo
nfiguration\DscResources\MSFT_RoleResource\MSFT_RoleResource.psm1 in force mode.
VERBOSE: [TEST-SRV]: LCM:  [ Start  Resource ]  [[WindowsFeature]PSWA]
VERBOSE: [TEST-SRV]: LCM:  [ Start  Test     ]  [[WindowsFeature]PSWA]
VERBOSE: [TEST-SRV]:                            [[WindowsFeature]PSWA] Importing the module MSFT_RoleResource in force mode.
WARNING: [TEST-SRV]:                            [[WindowsFeature]PSWA] Resource is waiting for PowerShell script debugger to attach.
Use the following commands to begin debugging this resource script:
Enter-PSSession -ComputerName TEST-SRV -Credential <credentials>
Enter-PSHostProcess -Id 9000 -AppDomainName DscPsPluginWkr_AppDomain
Debug-Runspace -Id 9
```
<span data-ttu-id="9fa33-117">Bu noktada, LCM kaynak adı ve ilk kesme noktasına gelen.</span><span class="sxs-lookup"><span data-stu-id="9fa33-117">At this point, the LCM has called the resource, and come to the first break point.</span></span>
<span data-ttu-id="9fa33-118">Son üç satır çıktıda işleme ve kaynak betiği hata ayıklamayı Başlat gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9fa33-118">The last three lines in the output show you how to attach to the process and start debugging the resource script.</span></span>

## <a name="debugging-the-resource-script"></a><span data-ttu-id="9fa33-119">Kaynak betiği hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="9fa33-119">Debugging the resource script</span></span>

<span data-ttu-id="9fa33-120">PowerShell ISE yeni bir örneğini başlatın.</span><span class="sxs-lookup"><span data-stu-id="9fa33-120">Start a new instance of the PowerShell ISE.</span></span>
<span data-ttu-id="9fa33-121">Konsol bölmesinde, son üç satır çıktısı girin `Start-DscConfiguration` değiştirerek komutları çıktı `<credentials>` geçerli kullanıcı kimlik bilgileriyle.</span><span class="sxs-lookup"><span data-stu-id="9fa33-121">In the console pane, enter the last three lines of output from the `Start-DscConfiguration` output as commands, replacing `<credentials>` with valid user credentials.</span></span>
<span data-ttu-id="9fa33-122">Şimdi şuna benzer şekilde bir uyarı görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="9fa33-122">You should now see a prompt that looks similar to:</span></span>

```powershell
[TEST-SRV]: [DBG]: [Process:9000]: [RemoteHost]: PS C:\DebugTest>>
```

<span data-ttu-id="9fa33-123">Kaynak betiği betik bölmesinde açılır ve hata ayıklayıcı durduruldu ilk satırında **Test TargetResource** işlevi ( **Test()** sınıf tabanlı bir kaynak yöntemi).</span><span class="sxs-lookup"><span data-stu-id="9fa33-123">The resource script will open in the script pane, and the debugger is stopped at the first line of the **Test-TargetResource** function (the **Test()** method of a class-based resource).</span></span>
<span data-ttu-id="9fa33-124">Hata ayıklama komutları ISE'de kaynak betiği adımlamak için artık, değişken değerleri arayın, çağrı yığınını görüntüleme ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="9fa33-124">Now you can use the debug commands in the ISE to step through the resource script, look at variable values, view the call stack, and so on.</span></span> <span data-ttu-id="9fa33-125">Kaynak betiği (veya sınıf) her satırda bir kesme noktası olarak ayarlandığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="9fa33-125">Remember that every line in the resource script (or class) is set as a break point.</span></span>

## <a name="disabling-dsc-debugging"></a><span data-ttu-id="9fa33-126">DSC hata ayıklama devre dışı bırakma</span><span class="sxs-lookup"><span data-stu-id="9fa33-126">Disabling DSC debugging</span></span>

<span data-ttu-id="9fa33-127">Arama sonra [etkinleştir DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug), tüm çağrıları [Başlat-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) hata ayıklayıcıya bozucu yapılandırmasında sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="9fa33-127">After calling [Enable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug), all calls to [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) will result in the configuration breaking into the debugger.</span></span> <span data-ttu-id="9fa33-128">Yapılandırmaları normal olarak çalışmasına izin vermek için çağrı yaparak hata ayıklamayı devre dışı bırakmalısınız [devre dışı bırak DscDebug](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="9fa33-128">To allow configurations to run normally, you must disable debugging by calling the [Disable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug) cmdlet.</span></span>

><span data-ttu-id="9fa33-129">**Not:** Yeniden başlatma LCM hata ayıklama durumunu değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="9fa33-129">**Note:** Rebooting does not change the debug state of the LCM.</span></span> <span data-ttu-id="9fa33-130">Hata ayıklama etkinleştirilirse bir yapılandırması başlatılıyor yine de hata ayıklayıcıya bir yeniden başlatma sonrası çalışmamasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="9fa33-130">If debugging is enabled, starting a configuration will still break into the debugger after a reboot.</span></span>

## <a name="see-also"></a><span data-ttu-id="9fa33-131">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="9fa33-131">See Also</span></span>

- [<span data-ttu-id="9fa33-132">MOF ile özel bir DSC kaynağı yazma</span><span class="sxs-lookup"><span data-stu-id="9fa33-132">Writing a custom DSC resource with MOF</span></span>](../resources/authoringResourceMOF.md)
- [<span data-ttu-id="9fa33-133">PowerShell sınıfları ile özel bir DSC kaynağı yazma</span><span class="sxs-lookup"><span data-stu-id="9fa33-133">Writing a custom DSC resource with PowerShell classes</span></span>](../resources/authoringResourceClass.md)
