---
ms.date: 07/10/2019
keywords: jea, powershell, güvenlik
title: JEA’yı kullanma
ms.openlocfilehash: 8f3cc9186c61a2ae5b64eb3dc4f72ca83f1a58c5
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734225"
---
# <a name="using-jea"></a>JEA’yı kullanma

Bu makalede çeşitli şekillerde bağlanmak ve bir JEA uç noktası kullanma.

## <a name="using-jea-interactively"></a>JEA etkileşimli kullanma

Jea'yı yapılandırmanızı test ettiğiniz veya kullanıcılar için basit görevler varsa, normal bir PowerShell uzaktan iletişimini oturumu olduğu gibi JEA kullanabilirsiniz. Görevler karmaşık uzaktan iletişim için kullanılacak önerilir [örtük uzak iletişim](#using-jea-with-implicit-remoting). Örtük uzak iletişim, kullanıcıların yerel olarak veri nesneleriyle çalışmaya sağlar.

JEA etkileşimli olarak kullanabilmek için gerekir:

- Bağlanmakta olduğunuz bilgisayarın adını (yerel makine olabilir)
- Bu bilgisayarda kayıtlı bir JEA uç nokta adı
- Bu bilgisayar üzerinde JEA uç noktasına erişimi olan kimlik bilgileri

Bu bilgiler verildiğinde, JEA oturumu kullanmaya başlayabilirsiniz [New-PSSession](/powershell/module/microsoft.powershell.core/New-PSSession) veya [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) cmdlet'leri.

```powershell
$nonAdminCred = Get-Credential
Enter-PSSession -ComputerName localhost -ConfigurationName JEAMaintenance -Credential $nonAdminCred
```

Geçerli kullanıcı hesabı erişimi JEA uç noktası varsa, atlayabilirsiniz **kimlik bilgisi** parametresi.

Ne zaman PowerShell istemi değişiklikleri `[localhost]: PS>` uzak JEA oturumla artık etkileşim bildirin. Çalıştırabileceğiniz `Get-Command` hangi komutları kullanılabilir denetlemek için. Kullanılabilir parametrelerin veya izin verilen parametre değerleri herhangi bir kısıtlama olup olmadığını öğrenmek için sistem yöneticinize başvurun.

Unutmayın, JEA oturumları NoLanguage modunda çalışır. Genellikle PowerShell kullanma yollarından bazıları kullanılamayabilir. Örneğin, veri depolamak veya cmdlet'lerinden döndürülen nesne özellikleri incelemek için değişkenler kullanamazsınız. Aşağıdaki örnekte NoLanguage modda aynı komutları almak için iki yaklaşım gösterilmektedir.

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

Bu yaklaşım zorlaştıran daha karmaşık komut çağrıları için kullanmayı [örtük uzak iletişim](#using-jea-with-implicit-remoting) veya [özel işlevler oluşturma](role-capabilities.md#creating-custom-functions) gereksinim duyduğunuz işleve kaydır.

## <a name="using-jea-with-implicit-remoting"></a>Jea'yı örtük uzak iletişim ile kullanma

PowerShell proxy cmdlet'leri uzak bir makineden içeri aktarma ve komutları yerel olarak bulunuyorlarmış etkileşime olanak tanıyan bir örtük uzaktan modeline sahiptir. Örtük uzak iletişim, bu konuda açıklanmıştır **Hey, Scripting Guy!** [blog gönderisi](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/).
Örtük uzak iletişim JEA cmdlet'leri tam dil modunda çalışmasına izin verdiğinden JEA ile çalışırken yararlı olur. Sekme tamamlama, değişkenleri kullanın, nesnelerini işleyin ve bile bir JEA uç noktası karşı görevleri otomatik hale getirmek için yerel betiklerini kullanın. Bir ara sunucu komutu çağırmak her zaman, veriler uzak makinede JEA uç noktasına gönderilen ve yürütülen vardır.

Örtük uzak iletişim cmdlet'leri var olan bir PowerShell oturumundan içeri aktararak çalışır. Ayrıca, her proxy cmdlet isimleri, seçtiğiniz bir dize ile ön ek isteğe bağlı olarak seçebilirsiniz. Önek uzak sistemdeki komutları ayırt etmenizi sağlar. Tüm proxy komutları içeren bir geçici betik modülü oluşturulur ve yerel PowerShell oturumunuzda süresince içeri aktarıldı.

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Import the entire PSSession and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA'

# Invoke "Get-Command" on the remote JEA endpoint using the proxy cmdlet
Get-JEACommand
```

> [!IMPORTANT]
> Bazı sistemler, tüm bir JEA oturumu varsayılan JEA cmdlet'lerinde kısıtlamaları nedeniyle içeri aktarmak mümkün olmayabilir. Bu sorunu aşmak için yalnızca ihtiyacınız olacak komutların JEA oturumundan açıkça adlarını sağlayarak içeri `-CommandName` parametresi. Gelecekte yapılacak bir güncelleştirmenin etkilenen sistemlerinde tüm JEA oturumları alma sorunu ele alınacaktır.

Bir JEA oturumu varsayılan parametrelerindeki JEA kısıtlamalar nedeniyle içeri aktarma yapamıyorsanız, içeri aktarılan kümesinden varsayılan komutları filtrelemek için aşağıdaki adımları izleyin. Gibi kullanım komutlar devam `Select-Object`, ancak yalnızca uzak JEA oturumundan içeri aktarılmış bir yerine bilgisayarınızda yüklü yerel sürümünü kullanmanız gerekir.

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

Örtük uzak iletişim kullanarak proxy cmdlet'leri de kalıcı yapılabilir [Export-PSSession](/powershell/microsoft.powershell.utility/Export-PSSession).
Örtük uzak iletişim hakkında daha fazla bilgi için belgelere bakın [Import-PSSession](/powershell/microsoft.powershell.utility/import-pssession) ve [Import-Module](/powershell/microsoft.powershell.core/import-module).

## <a name="using-jea-programmatically"></a>JEA programlı olarak kullanma

JEA Otomasyon sistemleri ve şirket içi Yardım Masası uygulamaları ve Web siteleri gibi kullanıcı uygulamaları içinde de kullanılabilir. Aynı sınırlandırılmamış PowerShell uç noktalar ile iletişim kurmasına uygulama oluşturmaya yönelik bir yaklaşımdır. Program JEA tarafından uygulanan bir kısıtlama olmaksızın çalışacak şekilde tasarlandığından emin olun.

Basit, tek seferlik görevler için kullanabileceğiniz [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) JEA oturumunda komutları çalıştırmak için.

```powershell
Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Process; Get-Service }
```

Bir JEA oturumuna bağlandığında, hangi komutları kullanılabilir olup olmadığını denetlemek için çalıştırın `Get-Command` ve denetlemek için izin verilen parametre sonuçları arasında gezinin.

```powershell
$allowedCommands = Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Command }
$allowedCommands | Where-Object { $_.CommandType -in 'Function', 'Cmdlet' } | Format-Table Name, Parameters
```

Derliyorsanız bir C# uygulama, yapılandırma adı belirterek bir JEA oturumuna bağlandığında bir PowerShell çalışma alanı oluşturabilirsiniz bir [WSManConnectionInfo](/dotnet/api/system.management.automation.runspaces.wsmanconnectioninfo) nesne.

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

## <a name="using-jea-with-powershell-direct"></a>Jea'yı PowerShell Direct ile kullanma

Windows 10 ve Windows Server 2016 Hyper-V sunar [PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct), Hyper-V ağ yapılandırması veya uzaktan yönetim bakılmaksızın PowerShell ile sanal makineleri yönetme olanağı sağlayan bir özelliği sanal makine ayarları.

Sanal makinenizde bir Hyper-V sınırlı yönetici erişimi vermek için PowerShell Direct ile JEA kullanabilirsiniz.
Sanal makinenizde ağ bağlantısı kaybı ve ağ ayarları düzeltmek için bir veri merkezi yönetim gerekiyorsa bu yararlı olabilir.

JEA PowerShell Direct üzerinden kullanmak için ek yapılandırma gerekir. Ancak, sanal makinede çalışan konuk işletim sistemini Windows 10, Windows Server 2016 veya üzeri olmalıdır. Hyper-V Yöneticisi kullanarak JEA uç noktasına bağlanabileceği `-VMName` veya `-VMId` PSRemoting cmdlet parametreleri:

```powershell
# Entering a JEA session using PowerShell Direct when the VM name is unique
Enter-PSSession -VMName 'SQL01' -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'

# Entering a JEA session using PowerShell Direct using VM ids
$vm = Get-VM -VMName 'MyVM' | Select-Object -First 1
Enter-PSSession -VMId $vm.VMId -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'
```

Bir Hyper-V Yöneticisi tarafından kullanmak için sistemi yönetmek için gereken en düşük haklara sahip bir ayrılmış kullanıcı hesabı oluşturmanız önerilir. Unutmayın, ayrıcalıksız bir kullanıcı, sınırlandırılmamış PowerShell kullanarak da dahil olmak üzere varsayılan olarak, bir Windows makinede oturum açabilirsiniz. Dosya sistemine göz atın ve işletim sistemi ortamınızın hakkında daha fazla bilgi sağlar. Bir Hyper-V Yöneticisi kilitlemek ve onlara yalnızca PowerShell Direct ile jea'yı kullanarak bir VM erişimi sınırlamak için Hyper-V yöneticinin JEA hesabı yerel oturum açma haklarını engellemelisiniz.
