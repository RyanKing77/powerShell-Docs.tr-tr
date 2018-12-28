---
ms.date: 12/12/2018
keywords: DSC, powershell, yapılandırma, Kurulum
title: ', Get, uygulamak ve Test yapılandırmaları bir düğümde'
ms.openlocfilehash: 41f8d2d75d3dd9621de615e7999c2690cb8ce44a
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405869"
---
# <a name="apply-get-and-test-configurations-on-a-node"></a>, Get, uygulamak ve Test yapılandırmaları bir düğümde

Bu kılavuz, bir hedef düğüm yapılandırmaları ile çalışmaya nasıl gösterir. Bu kılavuz, aşağıdaki adımlar ayrılır:

## <a name="apply-a-configuration"></a>Bir yapılandırmasını Uygula

Uygulama ve bir yapılandırmasını yönetmek için bir ".mof" dosyası oluşturmak gerekiyor. Aşağıdaki kod, bu kılavuzda kullanılan basit bir yapılandırmasını temsil eder.

```powershell
Configuration Sample
{
    # This will generate two .mof files, a localhost.mof, and a server02.mof
    Node localhost, server02
    {
        File SampleFile
        {
            DestinationPath = 'C:\Temp\temp.txt'
            Contents = 'This is a simple resource to show Configuration functionality on a Node.'
        }
    }
}

# The -OutputPath parameter is built into every Configuration automatically.
# The value of -OutputPath determines where the .mof file should be stored, once compiled.
Sample -OutputPath "C:\Temp\"
```

Bu yapılandırmanın derlenmesi iki ".mof" dosya ortaya çıkarır.

```output
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a----       11/27/2018   7:29 AM     2.13KB localhost.mof
-a----       11/27/2018   7:29 AM     2.13KB server02.mof
```

Bir yapılandırmayı uygulamak için kullanma [Başlat-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet'i. `-Path` Parametresi ".mof" dosyalarının bulunduğu bir dizini belirtir. Hayır ise `-Computername` belirtilen `Start-DSCConfiguration` '.mof' dosya adı tarafından belirtilen bilgisayar adı her yapılandırma uygulamak dener (\<computername\>.mof). Belirtin `-Verbose` için `Start-DSCConfiguration` daha ayrıntılı çıktıyı görmek için.

```powershell
Start-DSCConfiguration -Path C:\Temp\ -Verbose
```

Varsa `-Wait` belirtilmezse, oluşturulan bir işi görürsünüz. Oluşturulan projeyi bir olacaktır **ChildJob** her ".mof" dosyası için işlenen tarafından `Start-DSCConfiguration`.

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
45     Job45           Configuratio... Running       True            localhost,server02   Start-DSCConfiguration...
```

Bir yapılandırma uzun sürüyor ve durdurmak istiyorsanız, kullanabilirsiniz [Stop-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration) yerel düğüm üzerinde uygulamayı durdurma.

```powershell
Stop-DSCConfiguration -Force
```

İşlem tamamlandıktan sonra tarafından döndürülen iş nesnesi aracılığıyla işlerin durumunu görüntüleyebilirsiniz [Get-Job](/powershell/module/microsoft.powershell.core/get-job).

```powershell
$job = Get-Job
$job.ChildJobs
```

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
49     Job49           Configuratio... Completed     True            localhost            Start-DSCConfiguration...
50     Job50           Configuratio... Completed     True            server02             Start-DSCConfiguration...
```

Görmek için **ayrıntılı** görüntülemek için aşağıdaki komutları kullanın, çıktı **ayrıntılı** her akış **ChildJob**. PowerShell işleri hakkında daha fazla bilgi için bkz. [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).

```powershell
# View the verbose output of the localhost job using array indexing.
$job.ChildJobs[0].Verbose
```

```output
Perform operation 'Invoke CimMethod' with following parameters, ''methodName' = SendConfigurationApply,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' = root/Microsoft/Windows/DesiredStateConfiguration'.
An LCM method call arrived from computer SERVER01 with user sid S-1-5-21-124525095-708259637-1543119021-1282804.
[SERVER01]: LCM:  [ Start  Set      ]
[SERVER01]: LCM:  [ Start  Resource ]  [[File]SampleFile]
[SERVER01]: LCM:  [ Start  Test     ]  [[File]SampleFile]
[SERVER01]:                            [[File]SampleFile] The destination object was found and no action is required.
[SERVER01]: LCM:  [ End    Test     ]  [[File]SampleFile]  in 0.0370 seconds.
[SERVER01]: LCM:  [ Skip   Set      ]  [[File]SampleFile]
[SERVER01]: LCM:  [ End    Resource ]  [[File]SampleFile]
[SERVER01]: LCM:  [ End    Set      ]
[SERVER01]: LCM:  [ End    Set      ]    in  0.2400 seconds.
Operation 'Invoke CimMethod' complete.
```

PowerShell 5. 0'den itibaren `-UseExisting` parametresi eklenmiş `Start-DSCConfiguration`. Belirterek `-UseExisting`, biri tarafından belirtilen yerine var olan uygulanan yapılandırmasını kullanmak için cmdlet toplamasını `-Path` parametresi.

```powershell
Start-DSCConfiguration -UseExisting -Verbose -Wait
```

## <a name="test-a-configuration"></a>Bir yapılandırmayı test etme

Şu anda uygulanan yapılandırmayı kullanarak test [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration). `Test-DSCConfiguration` döndüreceği `True` düğümü uyumlu ise ve `False` değilse.

```powershell
Test-DSCConfiguration
```

PowerShell 5. 0'den itibaren `-Detailed` parametresi, bir nesne koleksiyonları döndüren eklenen **ResourcesInDesiredState** ve **ResourcesNotInDesiredState**

```powershell
Test-DSCConfiguration -Detailed
```

PowerShell 5. 0 ', başlangıç uygulanmadan cse'den bir yapılandırmasını test edebilirsiniz. `-ReferenceConfiguration` Parametreyi kabul eden düğümü karşı test etmek için ".mof" dosyasının yolu. Hayır **ayarlamak** eylemleri düğümü karşı alınır. PowerShell 4. 0'da, bu uygulamadan bir yapılandırmasını test etmek için geçici çözümler vardır, ancak burada açıklanmamaktadır.

## <a name="get-configuration-values"></a>Yapılandırma değerlerini alma

[Get-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet şu anda uygulanan yapılandırmasında yapılandırılan tüm kaynaklar için geçerli değerleri döndürür.

```powershell
Get-DSCConfiguration
```

Bizim örnek yapılandırma çıkışı başarıyla uygulandığında şuna benzer olabilir.

```output
ConfigurationName    : Sample
DependsOn            :
ModuleName           : PSDesiredStateConfiguration
ModuleVersion        :
PsDscRunAsCredential :
ResourceId           : [File]SampleFile
SourceInfo           :
Attributes           : {archive}
Checksum             :
Contents             :
CreatedDate          : 11/27/2018 7:16:06 AM
Credential           :
DestinationPath      : C:\Temp\temp.txt
Ensure               : present
Force                :
MatchSource          :
ModifiedDate         : 11/27/2018 7:16:06 AM
Recurse              :
Size                 : 75
SourcePath           :
SubItems             :
Type                 : file
PSComputerName       :
CimClassName         : MSFT_FileDirectoryConfiguration
```

## <a name="get-configuration-status"></a>Yapılandırma durumunu Al

PowerShell 5. 0'den itibaren [Get-DSCConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet'i düğüme uygulanan yapılandırmaları geçmişini görmenizi sağlar. PowerShell DSC uygulanan son {{N}} yapılandırmaları izler **anında iletme** veya **çekme** modu. Bu, tüm içerir *tutarlılık* LCM tarafından yürütülen denetler. Varsayılan olarak, `Get-DSCConfigurationStatus` yalnızca son geçmiş girişinin gösterir.

```powershell
Get-DSCConfigurationStatus
```

```output
Status     StartDate                 Type            Mode  RebootRequested      NumberOfResources
------     ---------                 ----            ----  ---------------      -----------------
Success    11/27/2018 7:18:40 AM     Consistency     PUSH  False                1
```

Kullanım `-All` tüm yapılandırma durumu geçmişini görmek için parametre.

> [!NOTE]
> Konuyu uzatmamak amacıyla çıktı kesildi.

```powershell
Get-DSCConfigurationStatus -All
```

```output
Status     StartDate                 Type            Mode  RebootRequested      NumberOfResources
------     ---------                 ----            ----  ---------------      -----------------
Success    11/27/2018 7:18:40 AM     Consistency     PUSH  False                1
Success    11/27/2018 7:16:06 AM     Initial         PUSH  False                1
Success    11/27/2018 7:04:53 AM     Initial         PUSH  False                1
Success    11/27/2018 7:03:45 AM     Consistency     PUSH  False                2
Success    11/27/2018 7:03:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:48:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:33:44 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:33:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:18:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:03:44 AM     Consistency     PUSH  False                2
```

## <a name="manage-configuration-documents"></a>Yapılandırma belgelerini yönetme

Birlikte çalışarak LCM yapılandırma düğümünün yönetir **yapılandırma belgelerini**. Bu ".mof" dosyalar "C:\Windows\System32\Configuration" dizininde bulunur.

PowerShell 5. 0'den itibaren [Remove-DSCConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument) gelecekteki tutarlılık denetimleri durdurmak veya uygulandığında hatalı bir yapılandırma kaldırmak için ".mof" dosyaları kaldırmanızı sağlar. `-Stage` Parametresi, kaldırmak istediğiniz hangi ".mof" dosyası belirtmenize olanak sağlar.

```powershell
Remove-DSCConfigurationDocument -Stage Current
```

> [!NOTE]
> PowerShell 4. 0'da, yine de kullanarak doğrudan bu ".mof" dosyaları kaldırabilirsiniz [Kaldır öğesini](/powershell/module/microsoft.powershell.management/remove-item).

## <a name="publish-configurations"></a>Yapılandırmaları yayımlama

PowerShell 5. 0'den itibaren [Yayımla-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet'i eklendi. Bu cmdlet'i ".mof" dosyasını uzak bilgisayara uygulanmadan cse'den yayımlamanıza olanak sağlar.

```powershell
Publish-DscConfiguration -Path '$home\WebServer' -ComputerName "ContosoWebServer" -Credential (get-credential Contoso\webadministrator)
```

## <a name="see-also"></a>Ayrıca bkz:

- [, Test, alma ve ayarlama](../resources/get-test-set.md)
