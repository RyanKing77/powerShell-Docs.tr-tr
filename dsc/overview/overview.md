---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: Windows PowerShell Desired State Configuration ' ne genel bakış
ms.openlocfilehash: 3e4f0afa17ab60bfa98f1b86b9830462a7c8e1cf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686316"
---
# <a name="windows-powershell-desired-state-configuration-overview"></a>Windows PowerShell Desired State Configuration ' ne genel bakış

> Şunun için geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0

DSC, BT yönetmenize olanak sağlayan PowerShell bir yönetim platformudur ve yapılandırmayı kod olarak ile geliştirme altyapısı.

- DSC kullanarak iş avantajları genel bakış için bkz. [karar alıcılar için genel Desired State Configuration](decisionMaker.md).
- Mühendislik DSC kullanmanın avantajları genel bakış için bkz. [Desired State Configuration ' ne genel bakış mühendislerin](DscForEngineers.md).
- DSC hızlı şekilde kullanmaya başlamak için bkz: [DSC Hızlı Başlangıç](../quickstarts/website-quickstart.md).

## <a name="key-concepts"></a>Temel kavramları

DSC yapılandırması, dağıtım ve yönetim sistemleri için kullanılan bildirim temelli bir platformdur. Bu, üç birincil bileşenden oluşur:

- [Yapılandırmaları](../configurations/configurations.md) tanımlayın ve örneklerinin yapılandırma bildirim temelli bir PowerShell komut dosyaları.
    Yapılandırma, DSC (ve yapılandırma tarafından çağrılan kaynakları) çalıştıran yalnızca "bunu kolaylaştırır", sistem yapılandırması tarafından düzenlendiği durumunda var olduğu doğrulanıyor.
    DSC yapılandırmaları ıdempotent yapılmıştır: yerel Configuration Manager (LCM) makineleri ne olursa olsun yapılandırma durumu yapılandırıldığından emin olun devam edecek bildirir.
- [Kaynakları](../resources/resources.md) DSC, "bunu olun" parçasıdır. Yerleştirin ve hedef yapılandırmasının belirtilen durumda tutmak kod içerirler.
    Kaynaklar, PowerShell modülleri bulunan ve genel olarak bir dosya ya da Windows işlem veya bir IIS sunucusu veya Azure'da çalışan bir VM olarak belirli bir şey model yazılabilir.
- [Yerel Configuration Manager'ı (LCM)](../managing-nodes/metaConfig.md) DSC kolaylaştıran kaynakları ve yapılandırmaları arasındaki etkileşimi altyapısıdır.
    LCM durumu yapılandırması tarafından tanımlanan korunduğundan emin olmak için kaynaklar tarafından uygulanan denetim akışı kullanarak sistem düzenli olarak yoklar.
    Sistem durumu dışında olduğunda, LCM "bunu yapılandırmasına göre sağlamak için" kaynakları koddaki çağrıları yapar.

## <a name="see-also"></a>Ayrıca bkz:

- [DSC yapılandırmaları](../configurations/configurations.md)
- [DSC kaynakları](../resources/resources.md)
- [Yerel Configuration Manager'ı yapılandırma](../managing-nodes/metaConfig.md)
