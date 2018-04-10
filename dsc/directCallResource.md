---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, yapılandırma, Kur
title: DSC kaynağı yöntemlerini doğrudan çağırma
ms.openlocfilehash: dbf0a4ada4c6cc2e7d65698b87a5a29a2ea84781
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="calling-dsc-resource-methods-directly"></a>DSC kaynağı yöntemlerini doğrudan çağırma

>İçin geçerlidir: Windows PowerShell 5.0

Kullanabileceğiniz [Invoke-DscResource](https://technet.microsoft.com/library/mt517869.aspx) işlevleri veya DSC kaynağı yöntemleri doğrudan çağırmak için cmdlet ( **Get-TargetResource**, **kümesi TargetResource**ve  **Test-TargetResource** MOF tabanlı bir kaynak işlevlerini veya **almak**, **ayarlamak**, ve **Test** sınıf tabanlı bir kaynak yöntemlerinin).
Bu DSC kaynakları kullanmak istediğiniz üçüncü taraflar tarafından ya da yararlı bir araç olarak kaynakları geliştirirken kullanılabilir.

Bu cmdlet genellikle meta yapılandırmasını özelliği ile birlikte kullanılan `refreshMode = 'Disabled'`, ancak bu ne olursa olsun kullanılabilir **refreshMode** ayarlanır.

Çağrılırken **Invoke-DscResource** cmdlet, belirttiğiniz hangi yöntemi veya kullanarak çağrılacak işlevi **yöntemi** parametresi. Bir karma tablosu değeri olarak geçirerek kaynak özelliklerini belirtin **özelliği** parametresi.

Doğrudan kaynak yöntemleri çağırma örnekleri şunlardır:

## <a name="ensure-a-file-is-present"></a>Bir dosya bulunduğundan emin olun

```powershell
$result = Invoke-DscResource -Name File -Method Set -Property @{
                            DestinationPath = "$env:SystemDrive\\DirectAccess.txt";
                            Contents = 'This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="test-that-a-file-is-present"></a>Bir dosya var olup olmadığını test

```powershell
$result = Invoke-DscResource -Name File -Method Test -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="get-the-contents-of-file"></a>Dosyanın içeriğini alma

```powershell
$result = Invoke-DscResource -Name File -Method Get -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result.ItemValue | fl
```

>**Not:** doğrudan bileşik kaynak yöntemleri çağırma desteklenmiyor. Bunun yerine, bileşik kaynak olun temel alınan kaynak yöntemlerini çağırın.

## <a name="see-also"></a>Ayrıca bkz:
- [Özel bir DSC kaynağı MOF ile yazma](authoringResourceMOF.md)
- [PowerShell sınıfları içeren özel bir DSC kaynağı yazma](authoringResourceClass.md)
- [DSC kaynaklarında hata ayıklama](debugResource.md)