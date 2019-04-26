---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 5b31fe833fb0f9d0f3f2733e777e4608a697d583
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057936"
---
# <a name="side-by-side-module-versioning-support-for-dsc-resources"></a>DSC kaynakları için yan yana modülü sürüm oluşturma desteği

DSC kaynakları içeren olabileceği modüller yan yana yüklü ve DSC yapılandırmaları sistemde yüklü kaynak belirli bir sürümünü kullanabilirsiniz.

Daha fazla bilgi için [birden çok sürümü olan kaynakları kullanma](https://msdn.microsoft.com/powershell/dsc/sxsresource).

## <a name="known-issues"></a>Bilinen sorunlar

Bu sürümde aşağıdaki yan yana yükleme sorunlar bilinmektedir:

-   DSC kaynak aynı yapılandırması içindeki iki farklı sürümlerini kullanan desteklenmiyor.
