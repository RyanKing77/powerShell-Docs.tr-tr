---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 6c036c2d8f97e559d20dd3ac40133fa06f5dab08
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
---
# <a name="separation-of-node-and-configuration-ids"></a>Düğüm ve Yapılandırma kimliklerinin ayrımı

## <a name="overview"></a>Genel bakış

DSC çekme modunda kullanılırken daha esnek ve kolaylaştırılmış bir deneyim sunmak için çok sayıda özelliği bu sürümde ekledik. Bu özellikler kolayca Kurulum yapılandırmalarını ve birden çok düğüm arasında hala durumu izleme ve raporlama bilgileri her düğüm için ayrı ayrı sırasında dağıtın esnekliğine sahip olanak tanımak için tasarlanmıştır.
Bu özellikler aşağıdaki gibidir:

* Bir bilgisayar yapılandırmasını tanımlayan bir yapılandırma adı. Bu adı birden çok hedef düğümleri tarafından paylaşılabilir
* Tek bir düğüm benzersiz olarak tanımlayan bir aracı kimliği
* Bir çekme sunucusuna yalnızca bir hedef düğümü ilk kez oluşan bir kayıt adımından bağlanır

**Not:** bu özellikler ve işlevsellik eklenmiştir ve varolan çekme özelliklerinin ve kavramlarının değiştirmeyin. Bu yeni özellikleri veya eskiler bu sürümde sevkiyat yeni çekme sunucusuyla kullanabilirsiniz.

Daha fazla bilgi için bkz: [yapılandırma adları kullanarak bir çekme istemci ayarlama](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames)
