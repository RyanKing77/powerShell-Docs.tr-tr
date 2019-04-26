---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC kaynağı yöntemlerini doğrudan çağırma
ms.openlocfilehash: cf237f638593706e5959e2bcc0d851b0e55baf0e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079634"
---
# <a name="calling-dsc-resource-methods-directly"></a>DSC kaynağı yöntemlerini doğrudan çağırma

>Uygulama hedefi: Windows PowerShell 5.0

Kullanabileceğiniz [Invoke-DscResource](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource) işlevleri veya DSC kaynak yöntemlerine doğrudan çağırmak için cmdlet ( **Get-TargetResource**, **kümesi TargetResource**ve  **Test-TargetResource** MOF temelli kaynak işlevleri veya **alma**, **ayarlayın**, ve **Test** sınıf tabanlı bir kaynak yöntemleri).
Bu DSC kaynakları kullanmak istediğiniz Üçüncü taraflardan ya da faydalı bir araç kaynakları geliştirirken kullanılabilir.

Bu cmdlet genellikle metaconfiguration özelliğiyle birlikte `refreshMode = 'Disabled'`, ancak bunu ne olursa olsun kullanılabilir **refreshMode** ayarlanır.

Çağrılırken **Invoke-DscResource** cmdlet'i, belirttiğiniz hangi yöntemi veya kullanılarak çağrılacak işlev **yöntemi** parametresi. Bir karma tablo değeri olarak geçirerek kaynak özelliklerini belirtin **özelliği** parametresi.

Kaynak yöntemlerine doğrudan çağırma örnekleri şunlardır:

## <a name="ensure-a-file-is-present"></a>Bir dosya mevcut olduğundan emin olun

```powershell
$result = Invoke-DscResource -Name File -Method Set -Property @{
                            DestinationPath = "$env:SystemDrive\\DirectAccess.txt";
                            Contents = 'This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="test-that-a-file-is-present"></a>Bir dosyanın var olup olmadığını test

```powershell
$result = Invoke-DscResource -Name File -Method Test -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="get-the-contents-of-file"></a>Dosya içeriğini Al

```powershell
$result = Invoke-DscResource -Name File -Method Get -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result.ItemValue | fl
```

>**Not:** Bileşik kaynak yöntemlerine doğrudan çağırma desteklenmiyor. Bunun yerine, temel alınan kaynakların bileşik kaynağı olun yöntemleri çağırın.

## <a name="see-also"></a>Ayrıca bkz:
- [MOF ile özel bir DSC kaynağı yazma](../resources/authoringResourceMOF.md)
- [PowerShell sınıfları ile özel bir DSC kaynağı yazma](../resources/authoringResourceClass.md)
- [DSC kaynaklarında hata ayıklama](../troubleshooting/debugResource.md)