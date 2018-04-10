---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, yapılandırma, Kur
title: Özel Windows PowerShell istenen durum yapılandırması kaynakları oluşturma
ms.openlocfilehash: 7da4741a773d40da75c6ef667c35f86e1bae74bf
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="build-custom-windows-powershell-desired-state-configuration-resources"></a>Özel Windows PowerShell istenen durum yapılandırması kaynakları oluşturma

> İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0

Windows PowerShell istenen durum yapılandırması (DSC) ortamınızı yapılandırmak için kullanabileceğiniz yerleşik kaynaklara sahip. (Daha fazla bilgi için bkz: [yerleşik Windows PowerShell istenen durum yapılandırması kaynakları](builtInResource.md).) Bu konu, kaynakları ve belirli bilgi ve örnekler ile konulara bağlantılar geliştirmeye genel bakış sağlar.

## <a name="dsc-resource-components"></a>DSC kaynağı bileşenleri

DSC kaynağı bir Windows PowerShell modülüdür. Modül kaynak için (yapılandırılabilir özellikleri tanımı) şema ve uygulama (yapılandırması tarafından belirtilen asıl işi yapan kod) içerir. DSC kaynağı şeması MOF dosyası içinde tanımlanabilir ve uygulama betik modülü tarafından gerçekleştirilir. Sürüm 5 PowerShell sınıflarda desteği ile başlayarak, şema ve uygulama hem de bir sınıfta tanımlanabilir. Aşağıdaki konularda, DSC kaynakları oluşturmak nasıl daha ayrıntılı olarak açıklanmaktadır.

* [Özel bir DSC kaynağı MOF ile yazma](authoringResourceMOF.md)
* [DSC kaynağı C# ' ta uygulama](authoringResourceMofCS.md)
* [PowerShell sınıfları içeren özel bir DSC kaynağı yazma](authoringResourceClass.md)
* [Bileşik kaynaklar: DSC yapılandırması bir kaynak olarak kullanma](authoringResourceComposite.md)
* [Kaynak Tasarımcısı aracını kullanma](authoringResourceMofDesigner.md)