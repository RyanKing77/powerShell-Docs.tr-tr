---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, Kur
ms.openlocfilehash: 4a2dfd651f1c74e7441e5f5e357c1c26453adc07
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="software-inventory-logging-sil"></a>Yazılım envanter günlüğü (SIL)

** Önemli: ** *yükleme işlemi errantly yazılım durdurulacak WMF 5.0 Windows Server 2012 R2 sunucusu üzerinde zaten SIL çalıştıran yüklerken, bir kez WMF yüklemeden sonra Start-SilLogging cmdlet'i çalıştırmak gerekli olur Envanter Günlüğü özelliği.*

Yazılım envanter günlüğü bir sunucuya, ancak özellikle (yazılımın yüklü olduğu varsayılarak ve çalışan bir BT ortamındaki çok sayıda sunucuya yerel olarak yüklü olan Microsoft yazılım hakkında kesin bilgi alma, işletim maliyetlerini azaltmaya yardımcı olur ortamı genelinde). Ayarlanan bir sağlanan bu verilerin bir toplama sunucusuna iletme ve Tekdüzen, otomatik bir işlemle kullanarak tek bir yerde günlük verilerini topla.

Yazılım envanteri verilerini her bilgisayar doğrudan sorgulanarak da oturum açabilir, ancak yazılım stok günlüğü, her sunucu tarafından başlatılan bir (ağ üzerinden) iletme mimarisi kullanarak çoğu için tipik olan sunucu bulma güçlüklerini aşabilir yazılım envanteri ve varlık yönetim senaryoları. Yazılım stok günlüğü, HTTPS üzerinden bir birleştirme sunucusuna iletilen verilerin güvenliğini sağlamak için SSL kullanır. Verileri tek bir yerde depolamak verilerin çözümlenmesini, yönetilmesini ve gerektiğinde paylaşmak kolaylaştırır.

Bu verilerin hiçbirinin, özellik işlevinin parçası olarak Microsoft'a gönderilir. Yazılım Stok Günlüğü verileri ve işlevselliği, yalnızca sunucu yazılımının lisanslı sahibi ve yöneticilerinin kullanımına yöneliktir.

Daha fazla bilgi ve yazılım envanter günlüğü cmdlet'leri ile ilgili belgeler için bkz: Windows Server 2012 R2 çevrimiçi kaynakları adresindeki <http://technet.microsoft.com/library/dn383584.aspx>.

