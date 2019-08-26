---
ms.date: 07/10/2019
keywords: Jea, PowerShell, güvenlik
title: JEA’yı kullanma
ms.openlocfilehash: 8f3cc9186c61a2ae5b64eb3dc4f72ca83f1a58c5
ms.sourcegitcommit: e894ed833cef57967cdaf002f8c883f66864e836
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2019
ms.locfileid: "70017898"
---
# <a name="using-jea"></a>JEA’yı kullanma

Bu makalede, bir JEA uç noktası ile bağlantı kurmak için kullanabileceğiniz çeşitli yollar açıklanmaktadır.

## <a name="using-jea-interactively"></a>JEA etkileşimli kullanma

JEA yapılandırmanızı test ediyorsanız veya kullanıcılar için basit görevleriniz varsa, JEA 'yı normal bir PowerShell Remoting oturumunda olduğu gibi kullanabilirsiniz. Karmaşık uzaktan iletişim görevleri için, [örtük uzaktan iletişim](#using-jea-with-implicit-remoting)kullanılması önerilir. Örtük uzaktan iletişim, kullanıcıların veri nesneleriyle yerel olarak çalışmasını sağlar.

JEA 'yı etkileşimli olarak kullanmak için şunlar gerekir:

- Bağlanmakta olduğunuz bilgisayarın adı (yerel makine olabilir)
- Bu bilgisayarda kayıtlı olan JEA uç noktasının adı
- Bu bilgisayardaki JEA uç noktasına erişimi olan kimlik bilgileri

Bu bilgiler verildiğinde, [New-PSSession](/powershell/module/microsoft.powershell.core/New-PSSession) veya [ENTER-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) cmdlet 'lerini kullanarak bir Jea oturumu başlatabilirsiniz.

```powershell
$nonAdminCred = Get-Credential
Enter-PSSession -ComputerName localhost -ConfigurationName JEAMaintenance -Credential $nonAdminCred
```

Geçerli Kullanıcı hesabının JEA uç noktasına erişimi varsa, **kimlik bilgisi** parametresini atlayabilirsiniz.

PowerShell istemi `[localhost]: PS>` , artık uzak Jea oturumu ile etkileşimde bulunabileceğinizi anlarsınız. Hangi komutların kullanılabilir `Get-Command` olduğunu denetlemek için komutunu kullanabilirsiniz. Kullanılabilir parametrelerde veya izin verilen parametre değerlerinde herhangi bir kısıtlama olup olmadığını öğrenmek için yöneticinize başvurun.

JEA oturumlarının NoLanguage modunda çalışacağını unutmayın. Genellikle PowerShell 'i kullanmanın bazı yolları kullanılamayabilir. Örneğin, verileri depolamak veya cmdlet 'lerden döndürülen nesnelerde özellikleri incelemek için değişkenleri kullanamazsınız. Aşağıdaki örnek, NoLanguage modunda çalışmak üzere aynı komutları almak için iki yaklaşımda gösterilmiştir.

```powershell
# Using variables is prohibited in NoLanguage mode. The following will not work:
# $vm = Get-VM -Name 'SQL01'
# Start-VM -VM $vm

# You can use pipes to pass data through to commands that accept input from the pipeline
Get-VM -Name 'SQL01' | Start-VM

# You can also wrap subcommands in parentheses and enter them inline as arguments
Start-VM -VM (Get-VM -Name 'SQL01')

# You can also use parameter sets that don't require extra data to be passed in
Start-VM -VMName 'SQL01'
```

Bu yaklaşımı zorlaştırtıran daha karmaşık komut çağırmaları için, [örtük uzaktan iletişim](#using-jea-with-implicit-remoting) kullanmayı veya ihtiyaç duyduğunuz işlevselliği sartıran [özel işlevler oluşturmayı](role-capabilities.md#creating-custom-functions) düşünün.

## <a name="using-jea-with-implicit-remoting"></a>JEA 'yı örtük uzaktan iletişim ile kullanma

PowerShell, uzak bir makineden proxy cmdlet 'lerini içeri aktarmanızı ve yerel komutlardır gibi etkileşimde bulunmanızı sağlayan örtük bir uzaktan iletişim modeline sahiptir. Örtülü uzaktan iletişim bu **Hey, komut dosyası oluşturma** konusunda açıklanmaktadır! [blog gönderisi](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/).
Tam dil modunda JEA cmdlet 'leriyle çalışmanıza olanak sağladığından, JEA ile çalışırken örtük uzaktan iletişim yararlıdır. Bir JEA uç noktasına karşı görevleri otomatikleştirmek için sekme tamamlama, değişkenler, nesneleri işleme ve hatta yerel betikleri kullanma gibi işlemleri kullanabilirsiniz. Bir ara sunucu komutunu her çağırdığınızda, veriler uzak makinedeki JEA uç noktasına gönderilir ve burada yürütülür.

Örtük uzaktan iletişim, cmdlet 'leri mevcut bir PowerShell oturumundan içeri aktararak işe yarar. İsteğe bağlı olarak, her proxy cmdlet 'inin adını seçtiğiniz bir dizeyle önek olarak seçebilirsiniz. Ön ek, uzak sistem için olan komutları ayırt etmenize olanak sağlar. Yerel PowerShell oturumunuz süresince tüm proxy komutlarını içeren geçici bir betik modülü oluşturulur ve içeri aktarılır.

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Import the entire PSSession and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA'

# Invoke "Get-Command" on the remote JEA endpoint using the proxy cmdlet
Get-JEACommand
```

> [!IMPORTANT]
> Varsayılan JEA cmdlet 'lerinde kısıtlamalar nedeniyle bazı sistemler JEA oturumunun tamamını içeri aktaramayabilir. Bu sorunu gidermek için, yalnızca adlarını `-CommandName` parametresine açıkça ekleyerek Jea oturumundan ihtiyacınız olan komutları içeri aktarın. Gelecekteki bir güncelleştirme, etkilenen sistemlerdeki tüm JEA oturumlarını içeri aktarma sorununu ele alır.

Varsayılan parametrelerde JEA kısıtlamaları nedeniyle JEA oturumunu içeri aktaramıyoruz, içeri aktarılan kümeden varsayılan komutları filtrelemek için aşağıdaki adımları izleyin. Gibi `Select-Object`komutları kullanmaya devam edebilirsiniz, ancak uzak Jea oturumundan içeri aktarıldığından, bilgisayarınızda yüklü olan yerel sürümü kullanmanız yeterlidir.

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Get a list of all the commands on the JEA endpoint
$commands = Invoke-Command -Session $jeasession -ScriptBlock { Get-Command }

# Filter out the default cmdlets
$jeaDefaultCmdlets = 'Clear-Host', 'Exit-PSSession', 'Get-Command', 'Get-FormatData', 'Get-Help', 'Measure-Object', 'Out-Default', 'Select-Object'
$filteredCommands = $commands.Name | Where-Object { $jeaDefaultCmdlets -notcontains $_ }

# Import only commands explicitly added in role capabilities and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA' -CommandName $filteredCommands
```

Ayrıca, [Export-PSSession](/powershell/microsoft.powershell.utility/Export-PSSession)kullanarak, proxy cmdlet 'lerini örtük uzaktan iletişim üzerinden kalıcı hale getirebilirsiniz.
Örtük uzaktan iletişim hakkında daha fazla bilgi için, [Import-PSSession](/powershell/microsoft.powershell.utility/import-pssession) ve [Import-Module](/powershell/microsoft.powershell.core/import-module)belgelerine bakın.

## <a name="using-jea-programmatically"></a>JEA 'yı program aracılığıyla kullanma

JEA Ayrıca otomasyon sistemlerinde ve şirket içi yardım masası uygulamaları ve Web siteleri gibi Kullanıcı uygulamalarında kullanılabilir. Yaklaşım, kısıtlanmış PowerShell uç noktaları ile iletişim kuran uygulamalar oluşturma ile aynıdır. Programın JEA tarafından uygulanan kısıtlamayla çalışacak şekilde tasarlandığından emin olun.

Basit, tek kapalı görevler için, komutları bir JEA oturumunda çalıştırmak için [Invoke-komutunu](/powershell/module/microsoft.powershell.core/invoke-command) kullanabilirsiniz.

```powershell
Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Process; Get-Service }
```

Jea oturumuna bağlanırken kullanılabilecek komutları denetlemek için, izin verilen parametreleri denetlemek üzere sonuçları çalıştırın `Get-Command` ve sonuçları yineleyin.

```powershell
$allowedCommands = Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Command }
$allowedCommands | Where-Object { $_.CommandType -in 'Function', 'Cmdlet' } | Format-Table Name, Parameters
```

Bir C# uygulama oluşturuyorsanız, bir [wsmanconnectionınfo](/dotnet/api/system.management.automation.runspaces.wsmanconnectioninfo) nesnesinde yapılandırma adını belirterek bir Jea oturumuna bağlanan bir PowerShell çalışma alanı oluşturabilirsiniz.

```csharp
// using System.Management.Automation;
var computerName = "SERVER01";
var configName   = "JEAMaintenance";
// See https://docs.microsoft.com/dotnet/api/system.management.automation.pscredential
var creds        = // create a PSCredential object here

WSManConnectionInfo connectionInfo = new WSManConnectionInfo(
    false,                 // Use SSL
    computerName,          // Computer name
    5985,                  // WSMan Port
    "/wsman",              // WSMan Path
                           // Connection URI with config name
    string.Format(CultureInfo.InvariantCulture, "http://schemas.microsoft.com/powershell/{0}", configName),
    creds);                // Credentials

// Now, use the connection info to create a runspace where you can run the commands
using (Runspace runspace = RunspaceFactory.CreateRunspace(connectionInfo))
{
    // Open the runspace
    runspace.Open();

    using (PowerShell ps = PowerShell.Create())
    {
        // Set the PowerShell object to use the JEA runspace
        ps.Runspace = runspace;

        // Now you can add and invoke commands
        ps.AddCommand("Get-Command");
        foreach (var result in ps.Invoke())
        {
            Console.WriteLine(result);
        }
    }

    // Close the runspace
    runspace.Close();
}
```

## <a name="using-jea-with-powershell-direct"></a>JEA 'yı doğrudan PowerShell ile kullanma

Windows 10 ve Windows Server 2016 ' deki Hyper-V, Hyper-V yöneticilerinin sanal makineleri PowerShell ile yönetmesine olanak tanıyan, sanal ağ yapılandırması veya uzaktan yönetim ayarlarından bağımsız olarak [PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct)sunar. Makin.

VM 'nize sınırlı bir Hyper-V Yöneticisi erişimi sağlamak için, JEA ile PowerShell Direct kullanabilirsiniz.
Bu, sanal makinenizin ağ bağlantısını kaybettiyseniz ve ağ ayarlarını onarmak için bir veri merkezi yöneticisinin olması halinde yararlı olabilir.

JEA 'yı PowerShell Direct üzerinden kullanmak için ek yapılandırma gerekmez. Ancak, sanal makine içinde çalışan konuk işletim sistemi Windows 10, Windows Server 2016 veya üzeri olmalıdır. Hyper-V Yöneticisi, PSRemoting cmdlet 'lerinde `-VMName` veya `-VMId` parametrelerini kullanarak Jea uç noktasına bağlanabilir:

```powershell
# Entering a JEA session using PowerShell Direct when the VM name is unique
Enter-PSSession -VMName 'SQL01' -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'

# Entering a JEA session using PowerShell Direct using VM ids
$vm = Get-VM -VMName 'MyVM' | Select-Object -First 1
Enter-PSSession -VMId $vm.VMId -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'
```

System 'i bir Hyper-V Yöneticisi tarafından kullanılmak üzere yönetmek için gereken en düşük haklara sahip adanmış bir kullanıcı hesabı oluşturmanız önerilir. Ayrıcalıksız bir Kullanıcı, kısıtlı PowerShell kullanma dahil olmak üzere varsayılan olarak bir Windows makinesinde oturum açabilir. Bu sayede dosya sistemine gözatıp işletim sistemi ortamınız hakkında daha fazla bilgi edinebilirsiniz. Hyper-V Yöneticisi 'ni kilitlemek ve onları yalnızca JEA ile PowerShell Direct kullanarak bir VM 'ye erişecek şekilde sınırlamak için, Hyper-V yöneticisinin JEA hesabına yerel oturum açma haklarını reddetmeniz gerekir.
