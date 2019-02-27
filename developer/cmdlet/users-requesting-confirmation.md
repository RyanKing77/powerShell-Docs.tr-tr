---
title: Onay isteyen kullanıcıların | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6f337498-c534-40ed-968a-09d4d9ca3849
caps.latest.revision: 8
ms.openlocfilehash: e4abbb14b31406b845d9b6af6b6372338fb0d926
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846980"
---
# <a name="users-requesting-confirmation"></a>Onay İsteyen Kullanıcılar

Değerini belirttiğinizde `true` için `SupportsShouldProcess` cmdlet'i özniteliği bildirimi parametresi, kullanıcıların belirtebilirsiniz `Confirm` parametresi komut isteminde.

Varsayılan ortamda kullanıcılar belirtebilir `Confirm` parametresi veya `"-Confirm:$true` onay istenmeden, zaman [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) yöntemi çağrılır. Bu atlar [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) bile yüksek etkili işlemleri için onay istekleri.

Varsa `Confirm` belirtilmezse, [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) çağrı varsa onay istekleri `$ConfirmPreference` tercih değişkeni eşit veya ondan `ConfirmImpact` ayarıyla cmdlet'ini veya sağlayıcısı. Varsayılan ayar `$ConfirmPreference` yüksek. Bu nedenle, varsayılan ortamda yalnızca cmdlet'leri ve etkili bir eylemi belirtin sağlayıcıları onay isteyin.

Varsa `Confirm` yanlış veya `"-Confirm:$false` belirtilen [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) çağrı, kullanıcıdan onayı ister ve `$ConfirmPreference` Kabuk değişkeni yoksayılır.

## <a name="remarks"></a>Açıklamalar

- Cmdlet'leri ve belirttiğiniz sağlayıcılarına `SupportsShouldProcess`, ama `ConfirmImpact`, bu eylemlerin "Orta etkisi" eylem olarak işlenir ve varsayılan olarak istemez. Kendi etki düzeyi varsayılan ayar'dan küçük `$ConfirmPreference` tercih değişkeni.

- Kullanıcı belirtiyorsa `Verbose` parametresi onaylamanız istenmez bile çalışmasını bildirilir.

## <a name="see-also"></a>Ayrıca bkz:

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)
