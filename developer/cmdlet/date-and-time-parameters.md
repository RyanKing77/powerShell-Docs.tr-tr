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
ms.openlocfilehash: 5b1f093de5db364ac806e58c4ed8dbf2948cb6c6
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251362"
---
# <a name="date-and-time-parameters"></a>Tarih ve Saat Parametreleri

Aşağıdaki tabloda, önerilen ad ve tarih ve saat bilgilerini işleyen parametreleri için işlevleri listeler. Tarih ve saat parametreleri, genellikle bir sorun oluşturulduğunda veya erişilen kaydetmek için kullanılır.

|Parametre|İşlevsellik|
|---|---|
|**Erişilen**<br>Veri türü: SwitchParameter|Bu parametre, cmdlet, erişilen kaynaklar üzerinde çalışır belirtildiğinde tarih ve saat tarafından belirlenen böylece temel uygulama **önce** ve **sonra** parametreleri. Bu parametre belirtilmezse, **oluşturulan** ve **değiştirilen** parametreleri olmalıdır belirtilemez.|
|**Sonra**<br>Veri türü: Tarih/saat|Tarih ve saat sonra cmdlet kullanılan belirtmek için bu parametreyi uygulayın. İçin **sonra** çalışmak için parametre cmdlet ayrıca olmalıdır bir **Accessed**, **oluşturulan**, veya **değiştirilen** parametresi. Ve bu parametre ayarlanmalıdır **true** cmdlet zaman çağrılır.|
|**Önce**<br>Veri türü: Tarih/saat|Tarih ve saat önüne cmdlet kullanılan belirtmek için bu parametreyi uygulayın. İçin **önce** çalışmak için parametre cmdlet ayrıca olmalıdır bir **Accessed**, **oluşturulan**, veya **değiştirilen** parametresi. Ve bu parametre ayarlanmalıdır **true** cmdlet zaman çağrılır.|
|**Oluşturulan**<br>Veri türü: SwitchParameter|Bu parametre, cmdlet, oluşturulmuş olan kaynaklar üzerinde çalışır belirtildiğinde tarih ve saat tarafından belirlenen böylece temel uygulama **önce** ve **sonra** parametreleri. Bu parametre belirtilmezse, **Accessed** ve **değiştirilen** parametreleri belirtilmelidir.|
|**Tam**<br>Veri türü: SwitchParameter|Bu parametre, böylece kaynak terimi, belirtilen kaynak adı tam olarak eşleşmelidir uygulayın. Parametre belirtilmediğinde adı ve kaynak terimi tam olarak eşleşmesi gerekmez.|
|**Değiştiren**<br>Veri türü: Tarih/saat|Bu parametre, cmdlet değişmiş olan kaynaklarda çalışır belirtildiğinde tarih ve saat tarafından belirlenen böylece temel uygulama **önce** ve **sonra** parametreleri. Bu parametre belirtilmezse, **Accessed** ve **oluşturulan** parametreleri belirtilmelidir.|
## <a name="see-also"></a>Ayrıca bkz:

[Cmdlet parametreleri](./cmdlet-parameters.md)

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK'sı](../windows-powershell-reference.md)
