---
ms.date: 06/12/2017
keywords: jea, powershell, güvenlik
title: JEA’yı kullanma
ms.openlocfilehash: fa3d3a3c8bc0090ec9ad788585ec5df933134173
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084054"
---
# <a name="using-jea"></a>JEA’yı kullanma

> Şunun için geçerlidir: Windows PowerShell 5.0

Bu konuda çeşitli şekillerde bağlanmak ve bir JEA uç noktası kullanma açıklanmaktadır.

## <a name="using-jea-interactively"></a>JEA etkileşimli kullanma

Jea'yı yapılandırmanızı test veya basit görevleri gerçekleştirmek kullanıcılar için varsa, normal bir PowerShell uzaktan iletişimini oturumu olduğu gibi JEA kullanabilirsiniz.
Görevler karmaşık uzaktan iletişim için kullanılacak önerilir [örtük uzak iletişim](#using-jea-with-implicit-remoting) kullanıcılarınız için birlikte çalışan olanak tanıyarak kolaylaştırmak için verileri yerel olarak nesnelerini.

JEA etkileşimli olarak kullanabilmek için ihtiyacınız olacak:
- Bağlandığınız bilgisayarın adını (yerel makine olabilir)
- Bu bilgisayarda kayıtlı bir JEA uç nokta adı
- JEA uç noktasına erişimi olan kimlik bilgilerini bilgisayar için

El ile bu bilgileri kullanarak bir JEA oturumu kullanmaya başlayabilirsiniz [New-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSSession) veya [Enter-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/enter-pssession).

```powershell
$nonAdminCred = Get-Credential
Enter-PSSession -ComputerName localhost -ConfigurationName JEAMaintenance -Credential $nonAdminCred
```

Şu anda oturum içinde JEA uç noktaya erişime sahip olduğundan, hesap atlayabilirsiniz, `-Credential` parametresi.

Ne zaman PowerShell istemi değişiklikleri `[localhost]: PS>` uzak JEA oturumla artık kurduğuna dair öğrenmiş olacaksınız.
Çalıştırabileceğiniz `Get-Command` hangi komutları kullanılabilir denetlemek için.
Kullanılabilir parametrelerin veya izin verilen parametre değerleri herhangi bir kısıtlama varsa bilgi için yöneticinize başvurmanız gerekir.

Bir anımsatıcı JEA oturumları NoLanguage modunda çalışmak genellikle PowerShell kullanma yollarından bazıları kullanılamayabilir.
Örneğin, veri depolamak veya cmdlet'lerinden döndürülen nesne özellikleri incelemek için değişkenler kullanamazsınız.
Aşağıdaki örnekte gösterildiği nasıl örnek bir PowerShell bugün kullanmakta olduğunuz ve aynı almak için iki yaklaşım komutu NoLanguage modunda çalışıyor.

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

Bu yaklaşım zorlaştıran daha karmaşık komut çağrıları için kullanmayı [örtük uzak iletişim](#using-jea-with-implicit-remoting) veya [özel işlevler oluşturma](role-capabilities.md#creating-custom-functions) , istenen işlevselliği sarmalamak.

## <a name="using-jea-with-implicit-remoting"></a>Jea'yı örtük uzak iletişim ile kullanma

PowerShell, proxy cmdlet'leri, yerel bilgisayarınızda uzak bir makineden içeri aktarma ve komutları yerel olarak bulunuyorlarmış etkileşime bir alternatif uzaktan iletişim modelini destekler.
Bu örtük uzak iletişim olarak adlandırılır ve iyi içinde açıklanan [bu *Hey, Scripting Guy!* blog gönderisi](https://blogs.technet.microsoft.com/heyscriptingguy/2013/09/08/remoting-the-implicit-way/).
Örtük uzak iletişim JEA cmdlet'leri tam dil modunda çalışmasına izin verdiğinden JEA ile çalışırken, özellikle yararlıdır.
Bu sekme tamamlama, değişkenleri kullanın, nesnelerini işleyin ve hatta daha kolay bir JEA uç noktasına karşı otomatik hale getirmek için yerel betiklerini kullanın anlamına gelir.
Bir ara sunucu komutu çağırmak her zaman, veriler uzak makinede JEA uç noktasına gönderilen ve yürütülen vardır.

Örtük uzak iletişim cmdlet'leri var olan bir PowerShell oturumundan içeri aktararak çalışır.
Ayrıca, her proxy cmdlet isimleri için uzak sistem komutlardır ayırt etmek seçtiğiniz bir dize ile ön ek isteğe bağlı olarak seçebilirsiniz.
Proxy komutların tümünü içeren geçici bir betik modülündeki oluşturulur ve süresi boyunca, yerel PowerShell oturumunuzda kullanılabilir.

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Import the entire PSSession and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA'

# Invoke "Get-Command" on the remote JEA endpoint using the proxy cmdlet
Get-JEACommand
```

> [!IMPORTANT]
> Bazı sistemler, tüm bir JEA oturumu varsayılan JEA cmdlet'lerinde kısıtlamaları nedeniyle içeri aktarmak mümkün olmayabilir.
> Bu sorunu aşmak için yalnızca ihtiyacınız olacak komutların JEA oturumundan açıkça adlarını sağlayarak içeri `-CommandName` parametresi.
> Gelecekte yapılacak bir güncelleştirmenin etkilenen sistemlerinde tüm JEA oturumları alma sorunu ele alınacaktır.

Bir JEA oturumu varsayılan JEA parametrelerindeki kısıtlamalar nedeniyle içeri aktarma bulamıyorsanız, içeri aktarılan kümesinden varsayılan komutları filtrelemek için aşağıdaki adımları izleyebilirsiniz.
Komutları gibi kullanmaya devam edersiniz `Select-Object` --yalnızca uzak bir JEA oturumdaki yerine bilgisayarınızda yüklü yerel sürümü kullanmanız gerekir.

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

Örtük uzak iletişim kullanarak proxy cmdlet'leri de kalıcı yapılabilir [Export-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/Export-PSSession).
Örtük uzak iletişim hakkında daha fazla bilgi için Yardım belgelerine göz atın [Import-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/import-pssession) ve [Import-Module](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/import-module).

## <a name="using-jea-programmatically"></a>JEA programlı olarak kullanma

JEA Otomasyon sistemleri ve şirket içi Yardım Masası uygulamaları ve web siteleri gibi kullanıcı uygulamaları içinde de kullanılabilir.
Uygulamaları oluşturma için program JEA uzak oturumu çalıştırma komutları sınırlayan olduğunu bilmeniz gerekir, uyarı ile sınırlandırılmamış PowerShell uç konuşma yaklaşımı aynıdır.

Basit, tek seferlik görevler için kullanabileceğiniz [Invoke-Command](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/invoke-command) jea'yı kullanarak bir komut kümesini çalıştırmak için.

```powershell
Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Process; Get-Service }
```

Bir JEA oturumuna bağlandığında, hangi komutları kullanılabilir olup olmadığını denetlemek için çalıştırın `Get-Command` ve denetlemek için izin verilen parametre sonuçları arasında gezinin.

```powershell
$allowedCommands = Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Command }
$allowedCommands | Where-Object { $_.CommandType -in 'Function', 'Cmdlet' } | Format-Table Name, Parameters
```

Oluşturuyorsanız bir C# uygulama, yapılandırma adı belirterek bir JEA oturumuna bağlandığında bir PowerShell çalışma alanı oluşturabilirsiniz bir [WSManConnectionInfo](https://msdn.microsoft.com/library/system.management.automation.runspaces.wsmanconnectioninfo(v=vs.85).aspx) nesne.

```csharp
// using System.Management.Automation;
var computerName = "SERVER01";
var configName   = "JEAMaintenance";
var creds        = // create a PSCredential object here (https://msdn.microsoft.com/library/system.management.automation.pscredential(v=vs.85).aspx)

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

## <a name="using-jea-with-powershell-direct"></a>Jea'yı PowerShell Direct ile kullanma

Windows 10 ve Windows Server 2016 Hyper-V sunar [PowerShell Direct](https://msdn.microsoft.com/virtualization/hyperv_on_windows/user_guide/vmsession), Hyper-V ağ yapılandırması veya uzaktan yönetim bakılmaksızın PowerShell ile sanal makineleri yönetme olanağı sağlayan bir özellik sanal makine ayarları.

Sanal makinenizde ağ bağlantısını kaybedebilir ve bir veri merkezi yönetim ağ ayarlarını düzeltmek gerekiyorsa bu yararlı olabilir, VM için bir Hyper-V sınırlı yönetici erişimi vermek için PowerShell Direct ile JEA kullanabilirsiniz.

Sanal makinede çalışan işletim sistemini Windows 10 veya Windows Server 2016 olması gerekir ancak ek yapılandırma JEA PowerShell Direct üzerinden kullanmak için gereklidir.
Hyper-V Yöneticisi kullanarak JEA uç noktasına bağlanabileceği `-VMName` veya `-VMId` PSRemoting cmdlet parametreleri:

```powershell
# Entering a JEA session using PowerShell Direct when the VM name is unique
Enter-PSSession -VMName 'SQL01' -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'

# Entering a JEA session using PowerShell Direct using VM ids
$vm = Get-VM -VMName 'MyVM' | Select-Object -First 1
Enter-PSSession -VMId $vm.VMId -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'
```

Kullanmak, Hyper-V yöneticileri için sistemi yönetmek için diğer haklara sahip ayrılmış bir yerel kullanıcı oluşturmanız önemle tavsiye edilir.
Sınırlandırılmamış PowerShell kullanarak da dahil olmak üzere varsayılan olarak, bir Windows makinesine, ayrıcalıksız bir kullanıcı yine de bağlanabilir unutmayın.
Eklemenize olanak tanıyan bunları (bazı) gözatmak dosya sistemini ve işletim sistemi ortamınız hakkında daha fazla bilgi edinin.
Yalnızca PowerShell Direct ile jea'yı kullanarak sanal Makineye erişmek için bir Hyper-V Yöneticisi kilitlemek için Hyper-V yöneticinin JEA hesabı yerel oturum açma haklarını Reddet gerekecektir.
