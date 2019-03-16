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
ms.openlocfilehash: ed9ff9fc1668a89e1ac0ceac8f0800a15b349226
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059567"
---
# <a name="users-requesting-confirmation"></a>Onay İsteyen Kullanıcılar

Değerini belirttiğinizde `true` için `SupportsShouldProcess` cmdlet'i özniteliği bildirimi parametresi, kullanıcıların belirtebilirsiniz `Confirm` parametresi komut isteminde.

Varsayılan ortamda kullanıcılar belirtebilir `Confirm` parametresi veya `"-Confirm:$true` onay istenmeden, zaman [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) yöntemi çağrılır. Bu atlar [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) bile yüksek etkili işlemleri için onay istekleri.

Varsa `Confirm` belirtilmezse, [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) çağrı varsa onay istekleri `$ConfirmPreference` tercih değişkeni eşit veya ondan `ConfirmImpact` ayarıyla cmdlet'ini veya sağlayıcısı. Varsayılan ayar `$ConfirmPreference` yüksek. Bu nedenle, varsayılan ortamda yalnızca cmdlet'leri ve etkili bir eylemi belirtin sağlayıcıları onay isteyin.

Varsa `Confirm` yanlış veya `"-Confirm:$false` belirtilen [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) çağrı, kullanıcıdan onayı ister ve `$ConfirmPreference` Kabuk değişkeni yoksayılır.

## <a name="remarks"></a>Açıklamalar

- Cmdlet'leri ve belirttiğiniz sağlayıcılarına `SupportsShouldProcess`, ama `ConfirmImpact`, bu eylemlerin "Orta etkisi" eylem olarak işlenir ve varsayılan olarak istemez. Kendi etki düzeyi varsayılan ayar'dan küçük `$ConfirmPreference` tercih değişkeni.

- Kullanıcı belirtiyorsa `Verbose` parametresi onaylamanız istenmez bile çalışmasını bildirilir.

## <a name="see-also"></a>Ayrıca bkz:

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)
