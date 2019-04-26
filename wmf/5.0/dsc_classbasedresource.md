---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: a1e90a0b96f74decb55343292b97befaf1a85f8a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058123"
---
# <a name="class-based-dsc-resources"></a>Sınıf tabanlı DSC Kaynakları

## <a name="defining-dsc-resources-with-classes"></a>DSC kaynakları ile sınıfları tanımlama

Geri bildirimi doğrultusunda, DSC kaynaklarını daha basit ve daha kolay anlaşılır sınıf tabanlı geliştirme yaptık.
Cmdlet'i DSC kaynak sağlayıcısı ile bir sınıf tabanlı DSC kaynağı arasındaki temel farklılıklar şunlardır:

* Şema için bir MOF dosyası gerekli değildir.
* A **DSCResource** modülü klasöründeki alt gerekli değildir.
* Bir PowerShell modülü dosyası birden çok DSC kaynak sınıfları içerebilir.

Daha fazla bilgi için [PowerShell sınıfları ile özel bir DSC kaynağı yazma](https://msdn.microsoft.com/powershell/dsc/authoringresource).
