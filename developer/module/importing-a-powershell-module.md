---
title: PowerShell modülünü içeri aktararak | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 697791b3-2135-4a39-b9d7-8566ed67acf2
caps.latest.revision: 13
ms.openlocfilehash: bb5d036e5658c365a4fafa2cac05c0bba9f87019
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082258"
---
# <a name="importing-a-powershell-module"></a>PowerShell Modülünü İçeri Aktarma

Bir kez, bir modül yüklü olduğu bir sistemde, büyük olasılıkla modülü içeri aktarmak istediğiniz. Bir kullanıcı kendi PowerShell oturumunda modülün erişebilmesi alma etkin belleğe yüklenen modül işlemidir. PowerShell 2. 0'da, bir çağrı ile yeni yüklediğiniz PowerShell modülünü içeri aktarabilirsiniz [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet'i. PowerShell 3. 0'da, örtülü olarak bir işlevler veya modüldeki cmdlet'ler, bir kullanıcı tarafından çağrıldığında bir modülü içeri aktarmak PowerShell kuramıyor. Her iki sürümde PowerShell bulmak mümkün olduğu bir konumda, modül yükleme varsayıyorsunuz dikkat edin. Daha fazla bilgi için [PowerShell modülünü yükleme](./installing-a-powershell-module.md). Bir modül bildirimi modülünüzde hangi bölümlerinin dışarı sınırlamak için kullanabileceğiniz ve parametrelerinin kullanabileceğiniz `Import-Module` hangi bölümlerinin içeri aktarılan kısıtlamak için çağrı.

## <a name="importing-a-snap-in-powershell-10"></a>Bir ek bileşenini (PowerShell 1.0) alma

Modülleri PowerShell 1.0 yoktu: bunun yerine, kaydetme ve ek bileşenler kullanma gerekiyordu. Modülleri yüklemek ve içeri aktarmak genellikle daha kolay şekilde ancak bu, bu noktada, bu teknolojiyi kullanmanız önerilmez. Daha fazla bilgi için [bir Windows PowerShell ek bileşenini oluşturma](../cmdlet/how-to-create-a-windows-powershell-snap-in.md).

## <a name="importing-a-module-with-import-module-powershell-20"></a>Import-Module (PowerShell 2.0) sahip bir modül içeri aktarma

PowerShell 2.0 kullanan uygun şekilde adlı [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet modülleri içeri aktarmak için. Bu cmdlet çalıştırıldığında, Windows PowerShell Belirtilen modül içinde belirtilen dizinler içinde arar `PSModulePath` değişkeni. Belirtilen dizin bulunduğunda, Windows PowerShell dosyalarını şu sırayla arar: modül bildirim dosyaları (.psd1) komut Modülü dosyaları (.psm1), ikili modül dosyaları (.dll). Arama dizinleri ekleme hakkında daha fazla bilgi için bkz. [PSModulePath yükleme yolunu değiştirmek](./modifying-the-psmodulepath-installation-path.md). Aşağıdaki kodu bir modülün nasıl içeri aktarılacağını açıklar:

```powershell
Import-Module myModule
```

MyModule bulunan varsayarak `PSModulePath`, PowerShell etkin belleğe myModule yük. MyModule üzerinde değil bulunuyorsa bir `PSModulePath` yolu hala açıkça size PowerShell nerede bulacağını:

```powershell
Import-Module -Name C:\myRandomDirectory\myModule -Verbose
```

Ayrıca dışında modülü veriliyor ve hangi etkin belleğe alınan tanımlamak için verbose parametresi. Hem dışarı ve içeri aktarmalar kısıtlamak kullanıcıya sunulan: kimin görünürlüğünü denetleme farktır. Esas olarak, dışarı aktarma, Modül içindeki kod tarafından denetlenir. Buna karşılık, içeri aktarmalar tarafından denetlenen `Import-Module` çağırın. Daha fazla bilgi için **kısıtlama üyeleri olduğunu aktarılır**aşağıdaki.

## <a name="implicitly-importing-a-module-powershell-30"></a>Örtük olarak (PowerShell 3.0) bir modülü içeri aktarma

Windows PowerShell 3. 0'den itibaren bir komut herhangi bir cmdlet veya modül işlevde kullanıldığında modüller otomatik olarak aktarılır. Bu özelliğin bu değeri dahil bir dizindeki tüm modül nasıl çalıştığı **PSModulePath** ortam değişkeni. Modülünüzde üzerinde geçerli bir yol ancak kaydetmezseniz, hala açık kullanarak bunları yükleyebilirsiniz [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) yukarıda açıklanan seçeneği.

Bir modül, "yükleme otomatik olarak da bilinen modül." otomatik olarak içeri aşağıdaki eylemleri tetikleyin

- Bir cmdlet bir komut kullanarak. Örneğin, yazmaya `Get-ExecutionPolicy` içeren Microsoft.PowerShell.Security modülü içe aktarır `Get-ExecutionPolicy` cmdlet'i.

- Kullanarak [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet'ini komutu.  Örneğin, yazmaya `Get-Command Get-JobTrigger` aktarır **PSScheduledJob** içeren modül `Get-JobTrigger` cmdlet'i. A `Get-Command` joker karakterler içeren komutu bulma olduğu kabul edilir ve bir modül içeri tetiklemez.

- Kullanarak [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) bir cmdlet için Yardım almak için cmdlet. Örneğin, yazmaya `Get-Help Get-WinEvent` içeren Microsoft.PowerShell.Diagnostics modülü içe aktarır `Get-WinEvent` cmdlet'i.

Modüller otomatik içe aktarma işlemlerini desteklemesi `Get-Command` cmdlet'i, tüm cmdlet'ler ve İşlevler tüm yüklü modüller, modülün oturuma aktarılmamış bile alır. Daha fazla bilgi için Yardım konusuna bakın [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet'i.

## <a name="the-importing-process"></a>İçeri aktarma işlemi

Bir modülü içeri aktarıldığında, yeni oturum durumu için modülü, oluşturulur ve [System.Management.Automation.PSModuleInfo](/dotnet/api/System.Management.Automation.PSModuleInfo) nesne bellekte oluşturulur. Oturum durumu için içeri aktarılan her modülü oluşturulur (Bu kök modül ve iç içe geçmiş modüllerin içerir). Bir kök modül iç içe geçmiş modüllerin tarafından verilmiş tüm üyeler dahil olmak üzere, bir kök modül öğesinden dışarı aktarılan üye sonra arayanın oturum durumuna alınır.

Meta veri üyelerinin bir modülünden dışarı aktarılan bir ModuleName özellik vardır. Bu özellik, bunları dışarı aktarılan modül adı ile doldurulur.

> [!WARNING]
> Dışarı aktarılan bir üyenin adını onaylanmamış bir fiili kullanıyorsa ya da üyenin adı yasak karakterler kullanıyorsa, bir uyarı görüntülenir, [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet'ini çalıştırın.

Varsayılan olarak, [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet'i işlem hattının herhangi bir nesneyi döndürmüyor. Ancak, cmdlet destekleyen bir `PassThru` döndürmek için kullanılan parametre bir [System.Management.Automation.PSModuleInfo](/dotnet/api/System.Management.Automation.PSModuleInfo) içeri aktarılan her modülü için nesne. Konağa çıkış göndermek için kullanıcıların çalışması gereken [Write-Host](/powershell/module/Microsoft.PowerShell.Utility/Write-Host) cmdlet'i.

## <a name="restricting--the-members-that-are-imported"></a>İçeri aktarılan üye kısıtlama

Bir modül aktarıldığında kullanarak [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet'i, varsayılan olarak, tüm dışarı aktarılan modül üyeleri oturumuna içeri aktarılan tüm komutları dahil olmak üzere aktarılan modül bir iç içe modül tarafından. Varsayılan olarak, değişkenler ve diğer adları dışa aktarılmaz. Dışarı aktarılan üye kısıtlamak için bir [modül bildirimini](./how-to-write-a-powershell-module-manifest.md). İçeri aktarılan üye kısıtlamak için aşağıdaki parametreleri kullanın `Import-Module` cmdlet'i.

- `Function`: Bu parametre, dışa aktarılan işlevleri sınırlar. (Bir modül bildirimi kullanıyorsanız FunctionsToExport anahtar bakın.)

- `Cmdlet`: Bu parametre (bir modül bildirimi, bkz: CmdletsToExport anahtar kullanıyorsanız.) dışarı aktarılan cmdlet'ler kısıtlar.

- `Variable`: Bu parametre (bir modül bildirimi, bkz: VariablesToExport anahtar kullanıyorsanız.), dışarı aktarılan değişkenlerin kısıtlar.

- `Alias`: Bu parametre (bir modül bildirimi, bkz: AliasesToExport anahtar kullanıyorsanız.), dışarı aktarılan diğer adları kısıtlar.

## <a name="see-also"></a>Ayrıca bkz:

[Bir Windows PowerShell modülü yazma](./writing-a-windows-powershell-module.md)
