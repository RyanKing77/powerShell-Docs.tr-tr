---
title: Tarih ve saat parametreleri | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 71da921b-7c32-4155-b2f8-b19f30ec774d
caps.latest.revision: 7
ms.openlocfilehash: 49f6c667b0fd9678586559af39a33f982de0a68c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846714"
---
# <a name="date-and-time-parameters"></a>Tarih ve Saat Parametreleri

Aşağıdaki tabloda, önerilen ad ve tarih ve saat bilgilerini işleyen parametreleri için işlevleri listeler. Tarih ve saat parametreleri, genellikle bir sorun oluşturulduğunda veya erişilen kaydetmek için kullanılır.

Erişilen veri türü: SwitchParameter

Bu parametre, cmdlet, erişilen kaynaklar üzerinde çalışır belirtildiğinde tarih ve saat tarafından belirlenen böylece temel uygulama `Before` ve `After` parametreleri.

Bu parametre belirtilmezse, `Created` ve `Modified` parametreleri olmalıdır belirtilemez.

Sonra veri türü: Tarih/saat

Tarih ve saat sonra cmdlet kullanılan belirtmek için bu parametreyi uygulayın. İçin `After` parametresi çalışmak için cmdlet ayrıca olmalıdır bir `Accessed`, `Created`, veya `Modified` parametresi. Ve bu parametre ayarlanmalıdır `true` cmdlet zaman çağrılır.

Önce veri türü: Tarih/saat

Tarih ve saat önüne cmdlet kullanılan belirtmek için bu parametreyi uygulayın. İçin `Before` parametresi çalışmak için cmdlet ayrıca olmalıdır bir `Accessed`, `Created`, veya `Modified` parametresi. Ve bu parametre ayarlanmalıdır `true` cmdlet zaman çağrılır.

Veri türü oluşturdu: SwitchParameter

Bu parametre, cmdlet, oluşturulmuş olan kaynaklar üzerinde çalışır belirtildiğinde tarih ve saat tarafından belirlenen böylece temel uygulama `Before` ve `After` parametreleri.

Bu parametre belirtilmezse, `Accessed` ve `Modified` parametreleri belirtilmelidir.

Tam veri türü: SwitchParameter

Bu parametre, böylece kaynak terimi, belirtilen kaynak adı tam olarak eşleşmelidir uygulayın. Parametre belirtilmediğinde adı ve kaynak terimi tam olarak eşleşmesi gerekmez.

Değiştirilen veri türü: Tarih/saat

Bu parametre, cmdlet değişmiş olan kaynaklarda çalışır belirtildiğinde tarih ve saat tarafından belirlenen böylece temel uygulama `Before` ve `After` parametreleri.

Bu parametre belirtilmezse, `Accessed` ve `Created` parametreleri belirtilmelidir.

## <a name="see-also"></a>Ayrıca bkz:

[Cmdlet parametreleri](./cmdlet-parameters.md)

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK'sı](../windows-powershell-reference.md)
