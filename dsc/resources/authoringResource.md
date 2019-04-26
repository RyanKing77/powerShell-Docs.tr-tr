---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: Derleme özel Windows PowerShell Desired State Configuration kaynakları
ms.openlocfilehash: 882b6efed4564d2354183d7472b301e1e1758335
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076880"
---
# <a name="build-custom-windows-powershell-desired-state-configuration-resources"></a>Derleme özel Windows PowerShell Desired State Configuration kaynakları

> Uygulama hedefi: Windows PowerShell 4.0, Windows PowerShell 5.0

Windows PowerShell Desired State Configuration (DSC), ortamınızı yapılandırmak için kullanabileceğiniz yerleşik kaynaklara sahip. Bu konuda, kaynakları ve bağlantıları konulara özel bilgiler ve örnekler ile geliştirmeye genel bakış sağlar.

## <a name="dsc-resource-components"></a>DSC kaynak bileşenler

DSC kaynak, bir Windows PowerShell modülüdür. Modülü, kaynak için şemanın (yapılandırılabilir özelliklerin tanımı) hem de (yapılandırması tarafından belirtilen asıl işi yapan kod) uygulaması içerir. DSC kaynak şema MOF dosyasında tanımlanabilir ve uygulama bir betik modülü tarafından gerçekleştirilir. PowerShell sınıflarını sürüm 5 desteği ile başlayarak, uygulama ve şema hem de bir sınıf içinde tanımlanabilir. Aşağıdaki konularda, DSC kaynakları oluşturmak nasıl daha ayrıntılı olarak açıklanmaktadır.

* [MOF ile özel bir DSC kaynağı yazma](authoringResourceMOF.md)
* [DSC kaynak uygulamaC#](authoringResourceMofCS.md)
* [PowerShell sınıfları ile özel bir DSC kaynağı yazma](authoringResourceClass.md)
* [Bileşik kaynaklar: DSC yapılandırma kaynağı olarak kullanma](authoringResourceComposite.md)
* [Kaynak Tasarımcısı aracını kullanma](../authoringResourceMofDesigner.md)
