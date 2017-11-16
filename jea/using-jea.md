---
ms.date: 2017-06-12
author: rpsqrd
ms.topic: conceptual
keywords: "jea, powershell, güvenlik"
title: JEA kullanma
ms.openlocfilehash: 9996a432bca27240e0f08adf932126ced116985d
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="using-jea"></a>JEA kullanma

> Uygulandığı öğe: Windows PowerShell 5.0

Bu konuda bağlanmak ve JEA uç noktası kullan çeşitli yolları açıklanmaktadır.

## <a name="using-jea-interactively"></a>JEA etkileşimli kullanma

JEA yapılandırmanızı test veya basit görevleri gerçekleştirmek kullanıcılar varsa, normal bir PowerShell uzaktan iletişim oturumu olduğu gibi JEA kullanabilirsiniz.
Kullanmak için önerilen karmaşık remoting görevlerde [örtük remoting](#using-jea-with-implicit-remoting) bunun yerine, kullanıcılarınız için kullanıcıların çalışır izin vererek kolaylaştırmak için veri yerel olarak nesneleri.

JEA etkileşimli olarak kullanabilmek için gerekir:
- Bağlandığınız bilgisayarın adını (yerel makine olabilir)
- Bu bilgisayarda kayıtlı JEA uç noktanın adı
- JEA uç noktasına erişimi olan bilgisayarın kimlik bilgileri

Yandan, bu bilgileri ile JEA kullanarak oturum başlatabilirsiniz [New-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSSession) veya [Enter-PSSession](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/enter-pssession).

```powershell
$nonAdminCred = Get-Credential
Enter-PSSession -ComputerName localhost -ConfigurationName JEAMaintenance -Credential $nonAdminCred
```

Şu anda açtığınızdan içinde JEA uç noktası erişimi gibi bu hesap, atlayabilirsiniz varsa `-Credential` parametresi.

PowerShell yapılan değişiklikler, komut istemine `[localhost]: PS>` uzak JEA oturumla şimdi etkileşim bilirsiniz.
Çalıştırabilirsiniz `Get-Command` hangi komutlar kullanılabilir denetlemek için.
Kullanılabilir parametrelerin veya izin verilen parametre değerlerini herhangi bir kısıtlamanın varsa öğrenmek için yöneticinize danışın gerekecektir.

Genellikle powershell'den yollardan bazılarını kullanılabilir olmaması bir hatırlatma JEA oturumları NoLanguage modunda çalışır.
Örneğin, verileri depolamak veya cmdlet'leri döndürülen nesnelerin özelliklerini incelemek için değişkenleri kullanamazsınız.
Aşağıdaki örnekteki nasıl örnek bir PowerShell bugün kullanıyor olabileceğiniz ve aynı almak için iki yaklaşım komut NoLanguage modunda çalışıyor.

```powershell
# Using variables in NoLanguage mode is disallowed, so the following will not work
# $vm = Get-VM -Name 'SQL01'
# Start-VM -VM $vm

# You can use pipes to pass data through to commands that accept input from the pipeline
Get-VM -Name 'SQL01' | Start-VM

# You can also wrap subcommands in parentheses and enter them inline as arguments
Start-VM -VM (Get-VM -Name 'SQL01')

# Better yet, use parameter sets that don't require extra data to be passed in when possible
Start-VM -VMName 'SQL01'
```

Bu yaklaşım zorlaştırır daha karmaşık komut çağırmaları için kullanmayı [örtük remoting](#using-jea-with-implicit-remoting) veya [özel işlevler oluşturma](role-capabilities.md#creating-custom-functions) istediğiniz işlevselliği sarmalamak.

## <a name="using-jea-with-implicit-remoting"></a>JEA örtük remoting ile kullanma

PowerShell burada proxy cmdlet'leri uzak bir makineden yerel bilgisayarınızda içeri aktarabilir ve yerel komutları değilmiş gibi etkileşim bir alternatif uzaktan iletişim modelini destekler.
Bu örtük remoting olarak adlandırılır ve iyi içinde açıklanan [bu *Hey, Scripting Guy!* blog gönderisi](https://blogs.technet.microsoft.com/heyscriptingguy/2013/09/08/remoting-the-implicit-way/).
Örtük remoting JEA cmdlet'leri tam dil modunda çalışmasına izin verdiğinden JEA ile çalışırken, özellikle yararlıdır.
Bu sekme tamamlama, değişkenleri kullanın, nesneleri işlemek ve hatta daha kolay bir JEA uç noktası karşı otomatik hale getirmek için yerel betiklerini kullanın anlamına gelir.
Proxy komutunu Çağır verdiğinizde, verileri uzak makinede JEA uç gönderilir ve orada yürütülen.

Örtük remoting cmdlet'leri varolan bir PowerShell oturumundan içeri aktararak çalışır.
Ayrıca, her bir proxy cmdlet isimleri için uzak sistem komutlardır ayırt etmek seçtiğiniz bir dizeyle öneki isteğe bağlı olarak seçebilirsiniz.
Proxy komutların tümünü içeren bir geçici betik modülündeki oluşturulur ve yerel PowerShell oturumunuzun süresi için kullanılabilir.

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Import the entire PSSession and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA'

# Invoke "Get-Command" on the remote JEA endpoint using the proxy cmdlet
Get-JEACommand
```

> [!IMPORTANT]
> Bazı sistemler varsayılan JEA cmdlet'lerinde kısıtlamaları nedeniyle bir tüm JEA oturum almak mümkün olmayabilir.
> Bu geçici bir çözüm bulmak için yalnızca ihtiyacınız komutları JEA oturumundan açıkça adlarını sağlayarak içeri `-CommandName` parametresi.
> Gelecekteki bir güncelleştirme, etkilenen sistemlerinde tüm JEA oturumları alma sorunu ele alınacaktır.

Varsayılan JEA parametrelerindeki kısıtlamalar nedeniyle JEA oturumu alamıyor varsa, içeri aktarılan kümesinden varsayılan komutları filtrelemek için aşağıdaki adımları izleyebilirsiniz.
Komutları gibi kullanmaya devam edersiniz `Select-Object` --yalnızca bilgisayarınızda yerine uzak bir JEA oturumunda yerel sürümünü kullanmanız.

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

Örtük remoting kullanarak yönlendirilirken cmdlet'leri devam edebilir [Export-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/Export-PSSession).
Örtük remoting hakkında daha fazla bilgi için Yardım belgelerine kullanıma [alma-PSSession](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.utility/import-pssession) ve [Import-Module](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/import-module).

## <a name="using-jea-programatically"></a>JEA programlı şekilde kullanma

JEA, Otomasyon sistemleri ve şirket içi Yardım Masası uygulamaları ve web siteleri gibi kullanıcı uygulamaları kullanılabilir.
Uygulamaları oluşturmaya yönelik Kısıtlanmamış PowerShell uç program JEA uzak oturumda çalışan komutlar sınırlama, farkında olmalıdır uyarısıyla ile iletişim kuran bir yaklaşım aynıdır.

Basit, tek seferlik görevler için kullanabileceğiniz [Invoke-Command](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/invoke-command) JEA kullanılarak bir komut kümesini çalıştırmak için.

```powershell
Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Process; Get-Service }
```

JEA oturumuna bağlandığında, hangi komutların kullanılabilir denetlemek için çalıştırın `Get-Command` ve izin verilen parametrelerini denetlemek için sonuçları yinelemek.

```powershell
$allowedCommands = Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Command }
$allowedCommands | Where-Object { $_.CommandType -in 'Function', 'Cmdlet' } | Format-Table Name, Parameters
```

Bir C# uygulaması oluşturuyorsanız, yapılandırma adı ile belirterek JEA oturumuna bağlandığında bir PowerShell çalışma oluşturabileceğiniz bir [WSManConnectionInfo](https://msdn.microsoft.com/en-us/library/system.management.automation.runspaces.wsmanconnectioninfo(v=vs.85).aspx) nesnesi.

```csharp

// using System.Management.Automation;
var computerName = "SERVER01";
var configName   = "JEAMaintenance";
var creds        = // create a PSCredential object here (https://msdn.microsoft.com/en-us/library/system.management.automation.pscredential(v=vs.85).aspx)

WSManConnectionInfo connectionInfo = new WSManConnectionInfo(
                    false,                 // Use SSL
                    computerName,          // Computer name
                    5985,                  // WSMan Port
                    "/wsman",              // WSMan Path
                    string.Format(CultureInfo.InvariantCulture, "http://schemas.microsoft.com/powershell/{0}", configName),  // Connection URI with config name
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

## <a name="using-jea-with-powershell-direct"></a>JEA PowerShell Direct ile kullanma

Hyper-V Windows 10 ve Windows Server 2016 sunar [PowerShell doğrudan](https://msdn.microsoft.com/en-us/virtualization/hyperv_on_windows/user_guide/vmsession), ağ yapılandırması veya uzaktan yönetim bağımsız olarak PowerShell ile sanal makineleri yönetmek Hyper-V yöneticileri sağlayan bir özellik Sanal makinedeki ayarları.

VM'nize ağ bağlantısını kaybedebilir ve ağ ayarlarını düzeltmek için bir veri merkezi yönetim ihtiyacınız varsa yararlı olabilen, VM için bir Hyper-V sınırlı yönetici erişimi vermek için PowerShell doğrudan JEA ile kullanabilirsiniz.

Sanal makinede çalışan işletim sistemini Windows 10 veya Windows Server 2016 olmalıdır ancak ek yapılandırma PowerShell doğrudan JEA kullanmak için gereklidir.
Hyper-V Yöneticisi kullanarak JEA uç noktasına bağlanabilir `-VMName` veya `-VMId` PSRemoting cmdlet'ler Parametreler:

```powershell
# Entering a JEA session using PowerShell Direct when the VM name is unique
Enter-PSSession -VMName 'SQL01' -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'

# Entering a JEA session using PowerShell Direct using VM ids
$vm = Get-VM -VMName 'MyVM' | Select-Object -First 1
Enter-PSSession -VMId $vm.VMId -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'
```

Kullanmak, Hyper-V yöneticileri için sistemi yönetmek için başka haklara sahip ayrılmış yerel bir kullanıcı oluşturmak önerilir.
Kısıtlanmamış PowerShell kullanarak da dahil olmak üzere varsayılan olarak, bir Windows makinesine, ayrıcalıksız bir kullanıcı hala bağlanabilir unutmayın.
İzin verin (bazıları) göz atmak dosya sistemini ve OS ortamınız hakkında daha fazla bilgi edinin.
Yalnızca PowerShell doğrudan JEA ile kullanarak bir VM'i erişmek için bir Hyper-V Yöneticisi kilitlemek için Hyper-V yöneticisinin JEA hesabın yerel oturum açma hakları Reddet gerekecektir.

