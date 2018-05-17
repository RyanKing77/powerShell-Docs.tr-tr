---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: Özel Windows PowerShell istenen durum yapılandırması kaynakları oluşturma
ms.openlocfilehash: f1ac626c5ef18b7ed14f3754ab39139db2a2a2d7
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
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