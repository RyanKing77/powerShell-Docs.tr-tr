---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Yazılım Envanter Günlüğü (SIL)
ms.openlocfilehash: b12cfc4ae1e505bbc4d47596bed9352ce53a98f2
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856171"
---
# <a name="software-inventory-logging-sil"></a>Yazılım Envanter Günlüğü (SIL)

> [!IMPORTANT]
> WMF yükleme sırasında 5.x Windows Server 2012 R2 SIL çalıştıran sunucusu üzerinde bu kez WMF yüklendikten sonra Start-SilLogging cmdlet'ini çalıştırmak için gerekli yükleme işlemi, yazılım envanter günlüğü özelliği errantly durduracak şekilde.

Yazılım envanter günlüğü bir sunucuya, ancak özellikle (yazılımın yüklü olduğu varsayılarak ve çalışan bir IT ortamındaki pek çok sunucu üzerinde yerel olarak yüklü Microsoft yazılımla ilgili doğru bilgileri almanın operasyonel maliyetlerini azaltmaya yardımcı olur ortamı genelinde). Ayarlanmış bir koşuluyla bu verilerin bir toplama sunucusuna iletme ve Tekdüzen, otomatik bir işlem kullanarak günlük verilerini tek bir yerde toplayın.

Yazılım envanteri verilerini her bilgisayar doğrudan sorgulayarak da oturum açabilirsiniz, ancak yazılım stok günlüğü, her sunucu tarafından başlatılan bir (ağ üzerinden) iletme mimarisi kullanarak birçok için tipik olan sunucu bulma zorluklarının üstesinden gelin yazılım envanteri ve varlık yönetimi senaryoları. Yazılım stok günlüğü, HTTPS üzerinden bir toplama sunucusuna iletilen verilerin güvenliğini sağlamak için SSL kullanır. Verileri tek bir yerde depolamak verileri analiz etmek, yönetmek ve gerektiğinde paylaşmak kolaylaştırır.

Bu verilerin hiçbirinin, özellik işlevinin parçası olarak Microsoft'a gönderilir. Yazılım Stok Günlüğü verileri ve işlevselliği, yalnızca sunucu yazılımının lisanslı sahibi ve yöneticilerinin kullanımına yöneliktir.

Daha fazla bilgi ve yazılım envanter günlüğü cmdlet'leri hakkında belgeler için bkz. [yönetme yazılım envanter günlüğü Windows Server 2012 R2'de](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn383584(v=ws.11)).
