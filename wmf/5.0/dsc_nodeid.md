---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, Kur
ms.openlocfilehash: 5b9eea1c90bfd5a8cee3897d832bf7775a750308
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="separation-of-node-and-configuration-ids"></a>Düğüm ve yapılandırma kimlikleri ayrımı

## <a name="overview"></a>Genel bakış

DSC çekme modunda kullanılırken daha esnek ve kolaylaştırılmış bir deneyim sunmak için çok sayıda özelliği bu sürümde ekledik. Bu özellikler kolayca Kurulum yapılandırmalarını ve birden çok düğüm arasında hala durumu izleme ve raporlama bilgileri her düğüm için ayrı ayrı sırasında dağıtın esnekliğine sahip olanak tanımak için tasarlanmıştır. Bu özellikler aşağıdaki gibidir:

* Bir bilgisayar yapılandırmasını tanımlayan bir yapılandırma adı. Bu adı birden çok hedef düğümleri tarafından paylaşılabilir 
* Tek bir düğüm benzersiz olarak tanımlayan bir aracı kimliği
* Bir çekme sunucusuna yalnızca bir hedef düğümü ilk kez oluşan bir kayıt adımından bağlanır

**Not:** bu özellikler ve işlevsellik eklenmiştir ve varolan çekme özelliklerinin ve kavramlarının değiştirmeyin. Bu yeni özellikleri veya eskiler bu sürümde sevkiyat yeni çekme sunucusuyla kullanabilirsiniz.

Daha fazla bilgi için bkz: [yapılandırma adları kullanarak bir çekme istemci ayarlama](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames)

