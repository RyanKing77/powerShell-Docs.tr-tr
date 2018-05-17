---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 4bfedd585958f84889954bd9ee022ea47ac191b2
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
---
# <a name="software-inventory-logging-sil"></a>Yazılım Envanter Günlüğü (SIL)

** Önemli: ** *yükleme işlemi errantly yazılım durdurulacak WMF 5.0 Windows Server 2012 R2 sunucusu üzerinde zaten SIL çalıştıran yüklerken, bir kez WMF yüklemeden sonra Start-SilLogging cmdlet'i çalıştırmak gerekli olur Envanter Günlüğü özelliği.*

Yazılım envanter günlüğü bir sunucuya, ancak özellikle (yazılımın yüklü olduğu varsayılarak ve çalışan bir BT ortamındaki çok sayıda sunucuya yerel olarak yüklü olan Microsoft yazılım hakkında kesin bilgi alma, işletim maliyetlerini azaltmaya yardımcı olur ortamı genelinde). Ayarlanan bir sağlanan bu verilerin bir toplama sunucusuna iletme ve Tekdüzen, otomatik bir işlemle kullanarak tek bir yerde günlük verilerini topla.

Yazılım envanteri verilerini her bilgisayar doğrudan sorgulanarak da oturum açabilir, ancak yazılım stok günlüğü, her sunucu tarafından başlatılan bir (ağ üzerinden) iletme mimarisi kullanarak çoğu için tipik olan sunucu bulma güçlüklerini aşabilir yazılım envanteri ve varlık yönetim senaryoları. Yazılım stok günlüğü, HTTPS üzerinden bir birleştirme sunucusuna iletilen verilerin güvenliğini sağlamak için SSL kullanır. Verileri tek bir yerde depolamak verilerin çözümlenmesini, yönetilmesini ve gerektiğinde paylaşmak kolaylaştırır.

Bu verilerin hiçbirinin, özellik işlevinin parçası olarak Microsoft'a gönderilir. Yazılım Stok Günlüğü verileri ve işlevselliği, yalnızca sunucu yazılımının lisanslı sahibi ve yöneticilerinin kullanımına yöneliktir.

Daha fazla bilgi ve yazılım envanter günlüğü cmdlet'leri ile ilgili belgeler için bkz: Windows Server 2012 R2 çevrimiçi kaynakları adresindeki <http://technet.microsoft.com/library/dn383584.aspx>.
