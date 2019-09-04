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
# <a name="get-test-set"></a>Al-test-ayarla

>Şunun için geçerlidir: Windows PowerShell 4,0, Windows PowerShell 5,0

![Kaynak Edinme, Sınama ve Ayarlama](../media/get-test-set.png)

PowerShell Istenen durum yapılandırması, bir **Get**, **Test**ve **set** işlemi etrafında oluşturulur. DSC [kaynakları](resources.md) , bu işlemlerin her birini tamamlamaya yönelik yöntemler içerir. Bir [yapılandırmada](../configurations/configurations.md), kaynak bloklarını bir kaynağın **Get**, **Test**ve **set** yöntemlerinin parametreleri olacak şekilde belirten anahtarları dolduracak şekilde tanımlarsınız.

Bu, bir **hizmet** kaynağı bloğunun sözdizimidir. **Hizmet** kaynağı Windows hizmetlerini yapılandırır.

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

**Hizmet** kaynağının **Get**, **Test**ve **set** yöntemlerinin bu değerleri kabul eden parametre blokları olacaktır.

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
> Kaynağı tanımlamak için kullanılan dil ve Yöntem **Get**, **Test**ve **set** yöntemlerinin nasıl tanımlanacağını belirler.

**Hizmet** kaynağında yalnızca bir gerekli anahtar (`Name`) bulunduğundan, bir **hizmet** bloğu kaynağı şu kadar basit olabilir:

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

Yukarıdaki yapılandırmayı derlerken, bir anahtar için belirttiğiniz değerler oluşturulan ". mof" dosyasında depolanır. Daha fazla bilgi için bkz. [MOF](/windows/desktop/wmisdk/managed-object-format--mof-).

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

Uygulandığında, [yerel Configuration Manager](../managing-nodes/metaConfig.md) (LCM) ". mof" dosyasındaki " `-Name` Kuyruklayıcı" değerini okur ve bunu, **"hizmetim" örneği için Get, test ve set yöntemlerinin parametresine iletir. Hizmet** kaynağı.

## <a name="get"></a>Alma

Bir kaynağın **Get** yöntemi, hedef düğümde yapılandırıldığı şekilde kaynağın durumunu alır. Bu durum bir [Hashtable](/powershell/module/microsoft.powershell.core/about/about_hash_tables)olarak döndürülür. **Hashtable** 'ın anahtarları yapılandırılabilir değerler veya parametreler olacaktır, kaynak kabul eder.

**Get** yöntemi doğrudan [Get-dscconfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet 'ine eşlenir. ' İ çağırdığınızda `Get-DSCConfiguration`, LCM, uygulanmış olan yapılandırmadaki her bir kaynağın **Get** yöntemini çalıştırır. LCM, her bir karşılık gelen kaynak örneğine parametre olarak ". mof" dosyasında depolanan anahtar değerlerini kullanır.

Bu, "biriktirici" hizmetini yapılandıran bir **hizmet** kaynağının örnek çıktısıdır.

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

Çıktı, **hizmet** kaynağı tarafından yapılandırılabilen geçerli değer özelliklerini gösterir.

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

## <a name="test"></a>Test

Bir kaynağın **Test** yöntemi, hedef düğümün Şu anda kaynağın *istenen durumuyla*uyumlu olup olmadığını belirler. **Test** yöntemi, `$True` `$False` yalnızca düğümün uyumlu olup olmadığını belirtmek için öğesini döndürür.
[Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)' ı çağırdığınızda, LCM geçerli olarak uygulanan yapılandırmadaki her bir kaynağın **Test** yöntemini çağırır. LCM, her bir karşılık gelen kaynak örneğine parametre olarak ". mof" dosyasında depolanan anahtar değerlerini kullanır.

Tek bir kaynağın **testinin** `$False`sonucu varsa, `Test-DSCConfiguration` düğümün uyumlu olmadığını gösteren döndürür `$False` . Tüm kaynakların **Test** yöntemleri `$True`döndürülürse, `Test-DSCConfiguration` düğümün uyumlu olduğunu `$True` göstermek için döndürür.

```powershell
Test-DSCConfiguration
```

```output
True
```

PowerShell 5,0 ' den başlayarak, `-Detailed` parametresi eklenmiştir. Uyumlu `-Detailed` ve `Test-DSCConfiguration` uyumlu olmayan kaynaklar için sonuç koleksiyonları içeren bir nesne döndürme nedenlerini belirtme.

```powershell
Test-DSCConfiguration -Detailed
```

```output
PSComputerName  ResourcesInDesiredState        ResourcesNotInDesiredState     InDesiredState
--------------  -----------------------        --------------------------     --------------
localhost       {[Service]Spooler}                                            True
```

Daha fazla bilgi için bkz. [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)

## <a name="set"></a>Ayarla

Bir kaynağın **set** yöntemi, düğümü kaynağın *istenen durumuyla*uyumlu hale getirmeye çalışır. **Set** yönteminin **ıdempotent**olması amaçlanmıştır, yani **küme** birden çok kez çalıştırılabilir ve hata olmadan her zaman aynı sonucu alabilir.  [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration)çalıştırdığınızda, LCM, o anda uygulanan yapılandırmadaki her bir kaynak boyunca geçiş yapar. LCM, ". mof" dosyasındaki geçerli kaynak örneğinin anahtar değerlerini alır ve bunları **Test** yöntemi için parametreler olarak kullanır. **Test** yöntemi döndürürse `$True`, düğüm geçerli kaynakla uyumludur ve **set** yöntemi atlanır. **Test** döndürürse `$False`, düğüm uyumlu değildir.  LCM, kaynak örneğinin anahtar değerlerini kaynağın **ayarlama** yöntemine parametreler olarak geçirir ve düğümü uyumluluğa geri yükler.

`-Verbose` `Start-DSCConfiguration` Ve parametrelerinibelirterek,cmdlet'ininilerlemesiniizleyebilirsiniz`-Wait` . Bu örnekte, düğüm zaten uyumludur. Çıktı, set yönteminin atlandığını gösterir. `Verbose`

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

## <a name="see-also"></a>Ayrıca bkz.

- [Azure Automation DSC genel bakış](https://docs.microsoft.com/azure/automation/automation-dsc-overview)
- [SMB çekme sunucusu ayarlama](../pull-server/pullServerSMB.md)
- [Çekme istemcisini yapılandırma](../pull-server/pullClientConfigID.md)
