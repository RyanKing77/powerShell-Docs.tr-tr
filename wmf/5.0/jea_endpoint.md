---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 3acd266a75bc61ffe4bce467cfb804ac7865c629
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057256"
---
# <a name="creating-and-connecting-to-a-jea-endpoint"></a><span data-ttu-id="15d1a-102">Bir JEA Uç Noktası Oluşturma ve Buna Bağlanma</span><span class="sxs-lookup"><span data-stu-id="15d1a-102">Creating and Connecting to a JEA Endpoint</span></span>

<span data-ttu-id="15d1a-103">Bir JEA uç noktası oluşturmak için oluşturmak ve ile oluşturulan bir özel olarak yapılandırılmış PowerShell oturumu yapılandırma dosyasını kaydetmek gereken **yeni PSSessionConfigurationFile** cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="15d1a-103">To create a JEA endpoint, you need to create and register a specially-configured PowerShell Session Configuration file, which can be generated with the **New-PSSessionConfigurationFile** cmdlet.</span></span>

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -TranscriptDirectory "C:\ProgramData\JEATranscripts" -RunAsVirtualAccount -RoleDefinitions @{ 'CONTOSO\NonAdmin_Operators' = @{ RoleCapabilities = 'Maintenance' }} -Path "$env:ProgramData\JEAConfiguration\Demo.pssc"
```

<span data-ttu-id="15d1a-104">Bu, şuna benzer bir oturum yapılandırma dosyası oluşturur:</span><span class="sxs-lookup"><span data-stu-id="15d1a-104">This will create a session configuration file that looks like this:</span></span>

```powershell
@{

    # Version number of the schema used for this document
    SchemaVersion = '2.0.0.0'

    # ID used to uniquely identify this document
    GUID = 'a384fdd3-5830-4a2c-ac86-cdd1822c3afd'

    # Author of this document
    Author = 'Administrator'

    # Description of the functionality provided by these settings
    # Description = ''

    # Session type defaults to apply for this session configuration. Can be 'RestrictedRemoteServer' (recommended), 'Empty', or 'Default'
    SessionType = 'RestrictedRemoteServer'

    # Directory to place session transcripts for this session configuration
    TranscriptDirectory = 'C:\ProgramData\JEATranscripts'

    # Whether to run this session configuration as the machine's (virtual) administrator account
    RunAsVirtualAccount = $true

    # Groups associated with machine's (virtual) administrator account
    # RunAsVirtualAccountGroups = 'Remote Desktop Users', 'Remote Management Users'

    # Scripts to run when applied to a session
    # ScriptsToProcess = 'C:\ConfigData\InitScript1.ps1', 'C:\ConfigData\InitScript2.ps1'

    # User roles (security groups), and the Role Capabilities that should be applied to them when applied to a session
    RoleDefinitions = @{ 'CONTOSO\NonAdmin_Operators' = @{ 'RoleCapabilities' = 'Maintenance' } }
}
```

<span data-ttu-id="15d1a-105">Bir JEA uç noktası oluştururken, aşağıdaki parametreleri komut (ve karşılık gelen anahtarları dosyasındaki) ayarlamanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="15d1a-105">When creating a JEA endpoint, the following parameters of the command (and corresponding keys in the file) must be set:</span></span>

1. <span data-ttu-id="15d1a-106">SessionType RestrictedRemoteServer için</span><span class="sxs-lookup"><span data-stu-id="15d1a-106">SessionType to RestrictedRemoteServer</span></span>
2. <span data-ttu-id="15d1a-107">İçin RunAsVirtualAccount **$true**</span><span class="sxs-lookup"><span data-stu-id="15d1a-107">RunAsVirtualAccount to **$true**</span></span>
3. <span data-ttu-id="15d1a-108">"Omuz" dökümleri sonra her oturum kaydedileceği dizine TranscriptPath</span><span class="sxs-lookup"><span data-stu-id="15d1a-108">TranscriptPath to the directory where "over the shoulder" transcripts will be saved after each session</span></span>
4. <span data-ttu-id="15d1a-109">RoleDefinitions grupları tanımlayan bir hashtable için "Rolü becerilerine." erişimi</span><span class="sxs-lookup"><span data-stu-id="15d1a-109">RoleDefinitions to a hashtable that defines which groups have access to which "Role Capabilities."</span></span> <span data-ttu-id="15d1a-110">Bu alan tanımlar **kimin** yapabilirsiniz **ne** Bu uç noktada.</span><span class="sxs-lookup"><span data-stu-id="15d1a-110">This field defines **who** can do **what** on this endpoint.</span></span> <span data-ttu-id="15d1a-111">Rol işlevleri, kısa bir süre sonra açıklanacaktır özel dosyalardır.</span><span class="sxs-lookup"><span data-stu-id="15d1a-111">Role Capabilities are special files that will be explained shortly.</span></span>

<span data-ttu-id="15d1a-112">Hangi grupların hangi rolü özelliklere erişim vardı RoleDefinitions alanı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="15d1a-112">The RoleDefinitions field defines which groups had access to which Role Capabilities.</span></span> <span data-ttu-id="15d1a-113">Bir rol özelliği kullanıcıları bağlamak için kullanıma sunulacak özellikler kümesini tanımlayan bir dosyadır.</span><span class="sxs-lookup"><span data-stu-id="15d1a-113">A Role Capability is a file that defines a set of capabilities that will be exposed to connecting users.</span></span>
<span data-ttu-id="15d1a-114">Rol işlevleri ile oluşturabileceğiniz **yeni PSRoleCapabilityFile** komutu.</span><span class="sxs-lookup"><span data-stu-id="15d1a-114">You can create Role Capabilities with the **New-PSRoleCapabilityFile** command.</span></span>

```powershell
New-PSRoleCapabilityFile -Path "$env:ProgramFiles\WindowsPowerShell\Modules\DemoModule\RoleCapabilities\Maintenance.psrc"
```

<span data-ttu-id="15d1a-115">Bu işlem şuna benzer bir şablon rolü özelliği oluşturur:</span><span class="sxs-lookup"><span data-stu-id="15d1a-115">This will generate a template role capability that looks like this:</span></span>

```powershell
@{
    # ID used to uniquely identify this document
    GUID = '9287a34f-3f0e-4fbe-9dd7-f1361ba9fd65'

    # Author of this document
    Author = 'Administrator'

    # Description of the functionality provided by these settings
    # Description = ''

    # Company associated with this document
    CompanyName = 'Unknown'

    # Copyright statement for this document
    Copyright = '(c) 2015 Administrator. All rights reserved.'

    # Modules to import when applied to a session
    # ModulesToImport = 'MyCustomModule', @{ ModuleName = 'MyCustomModule'; ModuleVersion = '1.0.0.0'; GUID = '4d30d5f0-cb16-4898-812d-f20a6c596bdf' }

    # Aliases to make visible when applied to a session
    # VisibleAliases = 'Item1', 'Item2'

    # Cmdlets to make visible when applied to a session
    # VisibleCmdlets = 'Invoke-Cmdlet1', @{ Name = 'Invoke-Cmdlet2'; Parameters = @{ Name = 'Parameter1'; ValidateSet = 'Item1', 'Item2' }, @{ Name = 'Parameter2'; ValidatePattern = 'L*' } }

    # Functions to make visible when applied to a session
    # VisibleFunctions = 'Invoke-Function1', @{ Name = 'Invoke-Function2'; Parameters = @{ Name = 'Parameter1'; ValidateSet = 'Item1', 'Item2' }, @{ Name = 'Parameter2'; ValidatePattern = 'L*' } }

    # External commands (scripts and applications) to make visible when applied to a session
    # VisibleExternalCommands = 'Item1', 'Item2'

    # Providers to make visible when applied to a session
    # VisibleProviders = 'Item1', 'Item2'

    # Scripts to run when applied to a session
    # ScriptsToProcess = 'C:\ConfigData\InitScript1.ps1', 'C:\ConfigData\InitScript2.ps1'

    # Aliases to be defined when applied to a session
    # AliasDefinitions = @{ Name = 'Alias1'; Value = 'Invoke-Alias1'}, @{ Name = 'Alias2'; Value = 'Invoke-Alias2'}

    # Functions to define when applied to a session
    # FunctionDefinitions = @{ Name = 'MyFunction'; ScriptBlock = { param($MyInput) $MyInput } }

    # Variables to define when applied to a session
    # VariableDefinitions = @{ Name = 'Variable1'; Value = { 'Dynamic' + 'InitialValue' } }, @{ Name = 'Variable2'; Value = 'StaticInitialValue' }

    # Environment variables to define when applied to a session
    # EnvironmentVariables = @{ Variable1 = 'Value1'; Variable2 = 'Value2' }

    # Type files (.ps1xml) to load when applied to a session
    # TypesToProcess = 'C:\ConfigData\MyTypes.ps1xml', 'C:\ConfigData\OtherTypes.ps1xml'

    # Format files (.ps1xml) to load when applied to a session
    # FormatsToProcess = 'C:\ConfigData\MyFormats.ps1xml', 'C:\ConfigData\OtherFormats.ps1xml'

    # Assemblies to load when applied to a session
    # AssembliesToLoad = 'System.Web', 'System.OtherAssembly, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a'

}
```

<span data-ttu-id="15d1a-116">Bir JEA oturum yapılandırması tarafından kullanılacak rol özellikleri "RoleCapabilities" adlı bir dizinde geçerli bir PowerShell modülü olarak kaydedilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="15d1a-116">To be used by a JEA session configuration, Role Capabilities must be saved as a valid PowerShell module in a directory named "RoleCapabilities".</span></span> <span data-ttu-id="15d1a-117">Bir modülün birden çok rol özellik dosyaları, isterseniz olabilir.</span><span class="sxs-lookup"><span data-stu-id="15d1a-117">A module may have multiple role capability files, if desired.</span></span>

<span data-ttu-id="15d1a-118">Cmdlet'leri, işlevleri, diğer adlar ve bir kullanıcı bir JEA oturumuna bağlanırken erişebilir betikleri yapılandırmaya başlamak için kendi kurallarınızı açıklamalı şablonlara göz aşağıdaki rol özelliği dosyasına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="15d1a-118">To start configuring which cmdlets, functions, aliases, and scripts a user may access when connecting to a JEA session, add your own rules to the Role Capability file following the commented out templates.</span></span> <span data-ttu-id="15d1a-119">Rol işlevleri nasıl yapılandırabileceğinizi içinde daha ayrıntılı görünüm için tam denetleyin [Kılavuzu deneyimi](http://aka.ms/JEA).</span><span class="sxs-lookup"><span data-stu-id="15d1a-119">For a deeper look into how you can configure Role Capabilities, check out the full [experience guide](http://aka.ms/JEA).</span></span>

<span data-ttu-id="15d1a-120">Son olarak, oturum yapılandırmasının ve ilişkili rol işlevleri özelleştirme tamamladıktan sonra bu oturum yapılandırmasını kaydedin ve çalıştırarak uç noktası oluşturma `Register-PSSessionConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="15d1a-120">Finally, once you have finished customizing your session configuration and related Role Capabilities, register this session configuration and create the endpoint by running `Register-PSSessionConfiguration`.</span></span>

```powershell
Register-PSSessionConfiguration -Name Maintenance -Path "C:\ProgramData\JEAConfiguration\Demo.pssc"
```

## <a name="connect-to-a-jea-endpoint"></a><span data-ttu-id="15d1a-121">Bir JEA uç noktasına bağlanma</span><span class="sxs-lookup"><span data-stu-id="15d1a-121">Connect to a JEA Endpoint</span></span>

<span data-ttu-id="15d1a-122">Bir JEA uç noktaya bağlanmak için başka bir PowerShell uç noktası çalışmalar bağlanma aynı şekilde çalışır.</span><span class="sxs-lookup"><span data-stu-id="15d1a-122">Connecting to a JEA Endpoint works the same way connecting to any other PowerShell endpoint works.</span></span>
<span data-ttu-id="15d1a-123">Yalnızca "ConfigurationName" parametresi olarak JEA uç nokta adınız vermek zorunda **New-PSSession**, **Invoke-Command**, veya **Enter-PSSession**.</span><span class="sxs-lookup"><span data-stu-id="15d1a-123">You simply have to give your JEA endpoint name as the "ConfigurationName" parameter for **New-PSSession**, **Invoke-Command**, or **Enter-PSSession**.</span></span>

```powershell
Enter-PSSession -ConfigurationName Maintenance -ComputerName localhost
```

<span data-ttu-id="15d1a-124">JEA oturuma bağlandıktan sonra komut izin verilenler listesinde erişiminiz rol işlevleri çalışan için sınırlı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="15d1a-124">Once you have connected to the JEA session, you will be limited to running the commands whitelisted in the Role Capabilities that you have access to.</span></span> <span data-ttu-id="15d1a-125">Rolünüz için izin verilmiyor herhangi bir komutu çalıştırmayı denerseniz, bir hatayla karşılaşırsınız.</span><span class="sxs-lookup"><span data-stu-id="15d1a-125">If you try to run any command not allowed for your role, you will encounter an error.</span></span>