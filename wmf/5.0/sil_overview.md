---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 7e87ed4bc9a86be52d4d06d3e87386a1111227c5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686939"
---
# <a name="software-inventory-logging-sil"></a>Yazılım Envanter Günlüğü (SIL)

**ÖNEMLİ:** *WMF 5.0 bir Windows Server 2012 R2 SIL zaten çalışan sunucusunda yüklerken WMF yüklendikten sonra yükleme işlemi, yazılım envanter günlüğü özelliği errantly durduracak şekilde Start-SilLogging cmdlet'i bir kez çalıştırmak gereklidir.*

Yazılım envanter günlüğü bir sunucuya, ancak özellikle (yazılımın yüklü olduğu varsayılarak ve çalışan bir IT ortamındaki pek çok sunucu üzerinde yerel olarak yüklü Microsoft yazılımla ilgili doğru bilgileri almanın operasyonel maliyetlerini azaltmaya yardımcı olur ortamı genelinde). Ayarlanmış bir koşuluyla bu verilerin bir toplama sunucusuna iletme ve Tekdüzen, otomatik bir işlem kullanarak günlük verilerini tek bir yerde toplayın.

Yazılım envanteri verilerini her bilgisayar doğrudan sorgulayarak da oturum açabilirsiniz, ancak yazılım stok günlüğü, her sunucu tarafından başlatılan bir (ağ üzerinden) iletme mimarisi kullanarak birçok için tipik olan sunucu bulma zorluklarının üstesinden gelin yazılım envanteri ve varlık yönetimi senaryoları. Yazılım stok günlüğü, HTTPS üzerinden bir toplama sunucusuna iletilen verilerin güvenliğini sağlamak için SSL kullanır. Verileri tek bir yerde depolamak verileri analiz etmek, yönetmek ve gerektiğinde paylaşmak kolaylaştırır.

Bu verilerin hiçbirinin, özellik işlevinin parçası olarak Microsoft'a gönderilir. Yazılım Stok Günlüğü verileri ve işlevselliği, yalnızca sunucu yazılımının lisanslı sahibi ve yöneticilerinin kullanımına yöneliktir.

Daha fazla bilgi ve yazılım envanter günlüğü cmdlet'leri hakkında belgeler için Windows Server 2012 R2'in çevrimiçi kaynakları bkz <http://technet.microsoft.com/library/dn383584.aspx>.
