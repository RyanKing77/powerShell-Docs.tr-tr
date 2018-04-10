---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, yapılandırma, Kur
title: DSC kaynakları
ms.openlocfilehash: e393c8fe2e1ba8d68ba9aa1b656d1e5ebfad30e8
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-resources"></a>DSC kaynakları

>İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0

İstenen durum Yapılandırması'nı (DSC) kaynaklar, DSC yapılandırması için yapı taşlarını sağlar. Bir kaynak yapılandırılmış (şema) olabilir ve "Bunu yapmak için" yerel Configuration Manager (LCM'yi) çağıran PowerShell Betiği işlevleri içeren özellikleri sunar.

Bir kaynak olarak bir dosya olarak genel veya bir IIS sunucu ayarı olarak belirli bir şey model oluşturabilirsiniz.  Grupları, kaynaklar gibi tüm gerekli dosyaları, taşınabilir ve nasıl kullanılmaya kaynaklara yönelik tanımlamak için meta verileri içeren bir yapı düzenler bir DSC modülü, birleştirilir.

Aşağıdaki konularda, DSC kaynakları açıklanmaktadır:

- [Yerleşik DSC kaynakları](builtInResource.md)
- [Özel DSC kaynakları oluşturma](authoringResource.md)
- [Linux için yerleşik DSC kaynakları](lnxBuiltInResources.md)