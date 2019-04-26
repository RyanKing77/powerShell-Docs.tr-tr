---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 7a1725e3858c59a6d31699add22b042359c48463
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058208"
---
# <a name="separation-of-node-and-configuration-ids"></a>Düğüm ve Yapılandırma kimliklerinin ayrımı

## <a name="overview"></a>Genel bakış

DSC çekme modunda kullanılırken daha esnek ve kolaylaştırılmış bir deneyim sağlamak amacıyla bir dizi özelliği bu sürümde ekledik. Bu özellikler, kolay kurulum ve yine de durum izleme ve raporlama bilgileri her düğüm için ayrı ayrı sırasında birden fazla düğümde yapılandırmaları dağıtma esnekliğine sahip olmasını sağlamak için tasarlanmıştır.
Bu özellikler aşağıdaki gibidir:

* Bir bilgisayar yapılandırmasını tanımlayan bir yapılandırma adı. Bu ad, birden çok hedef düğümler tarafından paylaşılabilir
* Tek bir düğüme benzersiz olarak tanımlayan bir Aracısı kimliği
* Kayıt adımı yalnızca bir hedef düğümü ilk kez oluşan bir çekme sunucusuna bağlanır.

**Not:** Bu özellikler ve İşlevler eklendi ve mevcut çekme özellikler ve kavramlar değiştirmeyin. Bu yeni özelliklerin veya eskiler bu sürümünde yeni çekme sunucusu ile kullanabilirsiniz.

Daha fazla bilgi için [yapılandırma adlarını kullanarak çekme istemcisi ayarlama](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames)
