---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 5b31fe833fb0f9d0f3f2733e777e4608a697d583
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685637"
---
# <a name="side-by-side-module-versioning-support-for-dsc-resources"></a>DSC kaynakları için yan yana modülü sürüm oluşturma desteği

DSC kaynakları içeren olabileceği modüller yan yana yüklü ve DSC yapılandırmaları sistemde yüklü kaynak belirli bir sürümünü kullanabilirsiniz.

Daha fazla bilgi için [birden çok sürümü olan kaynakları kullanma](https://msdn.microsoft.com/powershell/dsc/sxsresource).

## <a name="known-issues"></a>Bilinen sorunlar

Bu sürümde aşağıdaki yan yana yükleme sorunlar bilinmektedir:

-   DSC kaynak aynı yapılandırması içindeki iki farklı sürümlerini kullanan desteklenmiyor.
