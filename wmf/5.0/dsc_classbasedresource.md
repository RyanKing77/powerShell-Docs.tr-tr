---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, Kur
ms.openlocfilehash: d40e5475c4132d6377c9a4559262a41b4842180a
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="class-based-dsc-resources"></a>Sınıf tabanlı DSC kaynakları

## <a name="defining-dsc-resources-with-classes"></a>DSC kaynakları ile sınıfları tanımlama

Geri bildirimi doğrultusunda, sınıf tabanlı DSC kaynakları daha basit ve anlaşılması daha kolay geliştirme yaptık. Bir sınıf tabanlı DSC kaynağı bir cmdlet DSC kaynak sağlayıcısı arasındaki temel farklılıklar şunlardır:

* MOF dosyası şeması için gerekli değildir.
* A **DSCResource** modül klasöründe alt gerekli değildir.
* PowerShell modülü dosyası birden çok DSC kaynağı sınıfları içerebilir.

Daha fazla bilgi için bkz: [PowerShell sınıfları içeren özel bir DSC kaynağı yazma](https://msdn.microsoft.com/powershell/dsc/authoringresource).

