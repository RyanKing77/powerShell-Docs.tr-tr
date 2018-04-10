---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 4def20aa95f66ab23c9eee575150bc3db02541d8
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="class-based-dsc-resources"></a>Sınıf tabanlı DSC Kaynakları

## <a name="defining-dsc-resources-with-classes"></a>DSC kaynakları ile sınıfları tanımlama

Geri bildirimi doğrultusunda, sınıf tabanlı DSC kaynakları daha basit ve anlaşılması daha kolay geliştirme yaptık.
Bir sınıf tabanlı DSC kaynağı bir cmdlet DSC kaynak sağlayıcısı arasındaki temel farklılıklar şunlardır:

* MOF dosyası şeması için gerekli değildir.
* A **DSCResource** modül klasöründe alt gerekli değildir.
* PowerShell modülü dosyası birden çok DSC kaynağı sınıfları içerebilir.

Daha fazla bilgi için bkz: [PowerShell sınıfları içeren özel bir DSC kaynağı yazma](https://msdn.microsoft.com/powershell/dsc/authoringresource).