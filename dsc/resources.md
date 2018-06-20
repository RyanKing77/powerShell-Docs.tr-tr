---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: DSC kaynakları
ms.openlocfilehash: 27e16c39699bb96b2829744b5700f75f59f8802f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219819"
---
# <a name="dsc-resources"></a>DSC kaynakları

>İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0

İstenen durum Yapılandırması'nı (DSC) kaynaklar, DSC yapılandırması için yapı taşlarını sağlar. Bir kaynak yapılandırılmış (şema) olabilir ve "Bunu yapmak için" yerel Configuration Manager (LCM'yi) çağıran PowerShell Betiği işlevleri içeren özellikleri sunar.

Bir kaynak olarak bir dosya olarak genel veya bir IIS sunucu ayarı olarak belirli bir şey model oluşturabilirsiniz.  Grupları, kaynaklar gibi tüm gerekli dosyaları, taşınabilir ve nasıl kullanılmaya kaynaklara yönelik tanımlamak için meta verileri içeren bir yapı düzenler bir DSC modülü, birleştirilir.

Aşağıdaki konularda, DSC kaynakları açıklanmaktadır:

- [Yerleşik DSC kaynakları](builtInResource.md)
- [Özel DSC kaynakları oluşturma](authoringResource.md)
- [Linux için yerleşik DSC kaynakları](lnxBuiltInResources.md)