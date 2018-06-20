---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 42f323590609319388e9a0a2c7c305dfa80c2d49
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34221859"
---
# <a name="class-based-dsc-resources"></a>Sınıf tabanlı DSC Kaynakları

## <a name="defining-dsc-resources-with-classes"></a>DSC kaynakları ile sınıfları tanımlama

Geri bildirimi doğrultusunda, sınıf tabanlı DSC kaynakları daha basit ve anlaşılması daha kolay geliştirme yaptık.
Bir sınıf tabanlı DSC kaynağı bir cmdlet DSC kaynak sağlayıcısı arasındaki temel farklılıklar şunlardır:

* MOF dosyası şeması için gerekli değildir.
* A **DSCResource** modül klasöründe alt gerekli değildir.
* PowerShell modülü dosyası birden çok DSC kaynağı sınıfları içerebilir.

Daha fazla bilgi için bkz: [PowerShell sınıfları içeren özel bir DSC kaynağı yazma](https://msdn.microsoft.com/powershell/dsc/authoringresource).
