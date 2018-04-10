---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, yapılandırma, Kur
title: Windows PowerShell istenen durum yapılandırması genel bakış
ms.openlocfilehash: 3f357ea11a388a05b73539a63e52e639ee906f68
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="windows-powershell-desired-state-configuration-overview"></a>Windows PowerShell istenen durum yapılandırması genel bakış

> İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0

DSC olan bir yönetim platformunun PowerShell'de BT yönetmenizi sağlar ve geliştirme altyapı kodu yapılandırmaya sahip.

- DSC kullanarak iş avantajları genel bakış için bkz: [istenen durum yapılandırması için genel bakış karar alıcılar](decisionMaker.md).
- Mühendislik DSC kullanmanın yararları genel bakış için bkz: [istenen durum yapılandırması için genel bakış mühendisleri](DscForEngineers.md).
- DSC hızlı şekilde kullanmaya başlamak için bkz: [DSC Hızlı Başlangıç](quickStart.md).

## <a name="key-concepts"></a>Temel kavramları

DSC yapılandırması, dağıtım ve yönetim sistemleri için kullanılan bildirim temelli bir platformdur. Üç birincil bileşenden oluşur:

- [Yapılandırmaları](configurations.md) tanımlamak ve kaynakları örneklerini yapılandırın bildirim temelli bir PowerShell komut dosyaları.
    Yapılandırma, DSC (ve yapılandırma tarafından çağrılan kaynaklar) çalışan işlem yalnızca "bunu kolaylaştırır", sistem yapılandırması tarafından düzenlendiği durumda var olduğu doğrulanıyor.
    DSC yapılandırmaları olan de ıdempotent: yerel Configuration Manager (LCM'yi) makineleri, ne olursa olsun yapılandırma durumu olarak yapılandırıldığından emin olmak devam edecek bildirir.
- [Kaynakları](resources.md) "bunu make" DSC parçasıdır. Put ve yapılandırmasının hedef belirtilen durumda tutun kodu içerir.
    Kaynaklar PowerShell modülleri bulunan ve genel olarak bir dosya veya bir Windows işlemini veya bir IIS sunucusu veya Azure'da çalışan VM olarak belirli bir şey modellemek için yazılabilir.
- [Yerel Configuration Manager (LCM'yi)](metaConfig.md) DSC kolaylaştıran kaynakları ve yapılandırmaları arasındaki etkileşimi altyapısıdır.
    LCM'yi yapılandırması tarafından tanımlanan durumu korunduğundan emin olmak için kaynaklar tarafından uygulanan akış denetimi kullanarak sistem düzenli aralıklarla yoklar.
    Sistem durumu dışında olduğunda LCM'yi kodu "bunu yapılandırmasına göre yapmak için" kaynaklarında çağrılar.

## <a name="see-also"></a>Ayrıca bkz:

- [DSC yapılandırmaları](configurations.md)
- [DSC kaynakları](resources.md)
- [Yerel Yapılandırma Yöneticisi'ni yapılandırma](metaConfig.md)