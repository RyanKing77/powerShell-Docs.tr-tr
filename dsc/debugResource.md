---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "DSC kaynakları hata ayıklama"
ms.openlocfilehash: 35eb990705bab8190172df899c64c9f34452aa4b
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="debugging-dsc-resources"></a>DSC kaynakları hata ayıklama

> İçin geçerlidir: Windows PowerShell 5.0

PowerShell 5. 0'da, istenen durum yapılandırma (DSC kaynağı bir yapılandırma uygulanması gibi hata ayıklamak izin veren DSC içinde) yeni bir özellik sunulmuştur.

## <a name="enabling-dsc-debugging"></a>DSC hata ayıklamayı etkinleştirme
Bir kaynak ayıklayabilirsiniz önce çağırarak hata ayıklamayı etkinleştirmek sahip [etkinleştir DscDebug](https://technet.microsoft.com/en-us/library/mt517870.aspx) cmdlet'i. Bu cmdlet zorunlu bir parametre alır **BreakAll**. 

Hata ayıklama için bir çağrı sonucunu bakarak etkinleştirildiğini doğrulayın [Get-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx).

Aşağıdaki PowerShell çıkış hata ayıklamasını etkinleştirme sonucunu gösterir:


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


## <a name="starting-a-configuration-with-debug-enabled"></a>Bir yapılandırma ile hata ayıklama etkin başlatılıyor
DSC kaynağı hata ayıklamak için bu kaynağa çağıran bir yapılandırma başlatın. Bu örnekte, biz çağıran basit bir yapılandırma sırasında göreceğiz [WindowsFeature](windowsfeatureResource.md) kaynak "WindowsPowerShellWebAccess" özelliği yüklü olduğundan emin olun:

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
Yapılandırma derledikten sonra başlatılsın çağırarak [başlangıç DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx). Yerel Configuration Manager (LCM'yi) yapılandırmasında ilk kaynak içine çağırdığında yapılandırma durdurur. Kullanırsanız `-Verbose` ve `-Wait` parametreleri, çıktı hata ayıklamayı başlatmak için girmeniz gereken satırları görüntüler.

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
Bu noktada, LCM'yi kaynak adı ve ilk kesme noktası gelir. Çıktıdaki ilk üç satırını işleme ekleyin ve kaynak komut dosyası hata ayıklamayı Başlat gösterilmektedir.

## <a name="debugging-the-resource-script"></a>Kaynak komut dosyası hata ayıklaması

PowerShell ISE yeni bir örneğini başlatın. Konsol bölmesinde çıktısını ilk üç satırını girin `Start-DscConfiguration` değiştirme komutları çıkış `<credentials>` geçerli kullanıcı kimlik bilgileri. Şimdi için benzer bir istem görmeniz gerekir:

```powershell
[TEST-SRV]: [DBG]: [Process:9000]: [RemoteHost]: PS C:\DebugTest>>
```

Kaynak betik betik bölmesinde açılır ve hata ayıklayıcı ilk satırında durdurulur **Test TargetResource** işlevi ( **Test()** sınıf tabanlı bir kaynak yöntemi).
Kaynak komut dosyası adım için işe hata ayıklama komutlarını kullanabilirsiniz artık değişken değerlere göz, çağrı yığını görüntülemek ve benzeri. PowerShell ISE hata ayıklama hakkında daha fazla bilgi için bkz: [hata ayıklama komut dosyalarında Windows PowerShell ISE nasıl](https://technet.microsoft.com/en-us/library/dd819480.aspx). Kaynak betik (veya sınıfı) her satırda bir kesme noktası olarak ayarlandığını unutmayın.

## <a name="disabling-dsc-debugging"></a>DSC hata ayıklama devre dışı bırakma

Çağırdıktan sonra [etkinleştir DscDebug](https://technet.microsoft.com/en-us/library/mt517870.aspx), tüm çağrıları [başlangıç DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) ayıklayıcıya çiğnemekten yapılandırma neden olur. Yapılandırmaları normal olarak çalışmasına izin vermek için çağırarak hata ayıklama devre dışı bırakmalısınız [devre dışı bırakma DscDebug](https://technet.microsoft.com/en-us/library/mt517872.aspx) cmdlet'i.

>**Not:** Rebooting LCM'yi hata ayıklama durumunu değiştirmez. Hata ayıklama etkinleştirilirse yapılandırma başlatma hala ayıklayıcıya bir yeniden başlatmadan sonra çalışmamasına neden olur.


## <a name="see-also"></a>Ayrıca bkz:
- [Özel bir DSC kaynağı MOF ile yazma](authoringResourceMOF.md) 
- [PowerShell sınıfları içeren özel bir DSC kaynağı yazma](authoringResourceClass.md)

