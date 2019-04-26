---
ms.date: 12/12/2018
keywords: DSC, powershell, yapılandırma, Kurulum
title: Get-Test-Set
ms.openlocfilehash: 6d059518a49926bc5fb56e37e7d3d4d2c66bddec
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076608"
---
# <a name="get-test-set"></a>Get-Test-Set

>Uygulama hedefi: Windows PowerShell 4.0, Windows PowerShell 5.0

![Kaynak Edinme, Sınama ve Ayarlama](/media/get-test-set.png)

PowerShell Desired State Configuration çevresinde yapılandırılmıştır bir **alma**, **Test**, ve **ayarlamak** işlem. DSC [kaynakları](resources.md) her bu işlemlerden her biriyle tamamlamak için yöntemler içerir. İçinde bir [yapılandırma](../configurations/configurations.md), kaynağın parametrelerini haline anahtarlarını doldurmak için kaynak bloklar tanımladığınız **alma**, **Test**, ve **ayarlamak** yöntemleri.

Bu sözdizimi aşağıdaki gibidir bir **hizmet** kaynak blok. **Hizmet** kaynak Windows Hizmetleri yapılandırır.

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

**Alma**, **Test**, ve **ayarlamak** yöntemlerinin **hizmet** kaynak, bu değerleri kabul parametresi blokları olacaktır.

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
> Dil ve kaynağı tanımlamak için kullanılan yöntemi tanımlar nasıl **alma**, **Test**, ve **ayarlamak** yöntemleri tanımlanmasını.

Çünkü **hizmet** kaynak yalnızca bir gerekli anahtar var (`Name`), **hizmet** blok kaynak bu kadar basit olabilir:

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

Yukarıdaki yapılandırma derlediğinizde, bir anahtar için belirlediğiniz değerleri oluşturulan ".mof" dosyasında depolanır. Daha fazla bilgi için [MOF](/windows/desktop/wmisdk/managed-object-format--mof-).

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

Uygulandığında, [yerel Configuration Manager](../managing-nodes/metaConfig.md) "Biriktirici" değeri ".mof" dosyadan okunan ve geçirin `-Name` parametresinin **alma**, **Test**, ve **ayarlamak** "MyService" örneği için yöntemleri **hizmet** kaynak.

## <a name="get"></a>Alma

**Alma** yöntemi olan bir kaynağın hedef düğümü olarak yapılandırıldığı şekilde kaynak durumunu alır. Bu durum olarak döndürülen bir [hashtable](/powershell/module/microsoft.powershell.core/about/about_hash_tables). Anahtarları **hashtable** yapılandırılabilir değerleri veya parametrelerini kaynak kabul olacaktır.

**Alma** yöntemi eşleştirir doğrudan [Get-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet'i. Çağırdığınızda `Get-DSCConfiguration`, LCM çalıştırmalar **alma** uygulanmış yapılandırmasındaki her bir kaynağın yöntemi. LCM karşılık gelen her bir kaynak örneği parametre olarak ".mof" dosyasında depolanan anahtar değerleri kullanır.

Bu örnek çıktısı, bir **hizmet** "Biriktirici" hizmetini yapılandırır kaynak.

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

Geçerli değer özellikleri çıktı tarafından yapılandırılabilir gösterir **hizmet** kaynak.

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

**Test** yöntemi bir kaynak, hedef düğüm kaynak şu anda uyumlu olup olmadığını belirler *durumu istenen*. **Test** yöntemi döndürür `$True` veya `$False` yalnızca düğüm uyumlu olup olmadığını belirtmek için.
Çağırdığınızda [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration), LCM çağrıları **Test** uygulanmış yapılandırmasındaki her bir kaynağın yöntemi. LCM karşılık gelen her bir kaynak örneği parametre olarak ".mof" dosyasında depolanan anahtar değerleri kullanır.

Herhangi tek bir kaynağın sonucunu **Test** olduğu `$False`, `Test-DSCConfiguration` döndürür `$False` belirten düğüm uyumlu değil. Tüm kaynak **Test** yöntemleri dönüş `$True`, `Test-DSCConfiguration` döndürür `$True` düğümü uyumlu olduğunu göstermek için.

```powershell
Test-DSCConfiguration
```

```output
True
```

PowerShell 5. 0'den itibaren `-Detailed` parametresi eklendi. Belirtme `-Detailed` neden `Test-DSCConfiguration` koleksiyonları uyumlu ve uyumlu olmayan kaynaklar için sonuçları içeren bir nesne döndürmek için.

```powershell
Test-DSCConfiguration -Detailed
```

```output
PSComputerName  ResourcesInDesiredState        ResourcesNotInDesiredState     InDesiredState
--------------  -----------------------        --------------------------     --------------
localhost       {[Service]Spooler}                                            True
```

Daha fazla bilgi için [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)

## <a name="set"></a>Ayarla

**Ayarlamak** yöntemi olan bir kaynağın çalışır kaynağın ile uyumlu olması için düğüm zorlamak *durumu istenen*. **Ayarlamak** yöntemi olacak şekilde tasarlanmıştır **etkili**, anlamına **ayarlamak** birden çok kez çalıştırın ve her zaman hata olmadan aynı sonucu elde olabilir.  Çalıştırdığınızda [Başlat-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration), her bir kaynak şu anda uygulanan yapılandırmasında LCM başlatıldıkları. LCM ".mof" dosyasından geçerli kaynak örneği için anahtar değerlerini alır ve bunları için parametre olarak kullanan **Test** yöntemi. Varsa **Test** yöntemi döndürür `$True`, düğüm geçerli kaynak ile uyumludur ve **ayarlamak** yöntemi atlandı. Varsa **Test** döndürür `$False`, uyumlu olmayan bir düğümdür.  LCM kaynak örneğinin anahtar değerleri parametre olarak kaynağın geçirir **ayarlamak** düğümü uyumluluk için geri yükleme yöntemi.

Belirterek `-Verbose` ve `-Wait` parametreleri, ilerleme durumunu izleyebilir `Start-DSCConfiguration` cmdlet'i. Bu örnekte, bir düğüm zaten uyumludur. `Verbose` Çıkış gösterir **ayarlamak** yöntemi atlandı.

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
- [Bir SMB çekme sunucusu ayarlama](../pull-server/pullServerSMB.md)
- [Çekme istemcisi yapılandırma](../pull-server/pullClientConfigID.md)
