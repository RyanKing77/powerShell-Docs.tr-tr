---
title: Örnek kod AccessDbProviderSample01 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 35540d2a-c18f-4179-b869-1a3dc5a8c1bd
caps.latest.revision: 6
ms.openlocfilehash: 01b95e18794501c2aff13d1e51b7400ae6fb8730
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081997"
---
# <a name="accessdbprovidersample01-code-sample"></a>AccessDbProviderSample01 Kod Örneği

Aşağıdaki kod bölümünde açıklanan Windows PowerShell sağlayıcısı uygulamasını gösterir [temel bir Windows PowerShell sağlayıcısı oluşturma](./creating-a-basic-windows-powershell-provider.md). Bu uygulama başlatma ve durdurma sağlayıcısı için yöntemler sağlar ve bir veri deposuna erişmek için alın veya veri deposuna veri kümesi için bir yol sağlamaz olsa da, tüm sağlayıcıları tarafından gerekli olan temel işlevleri sağlar.

> [!NOTE]
> İndirebileceğiniz C# Windows Vista için Windows Yazılım Geliştirme Seti ve Microsoft .NET Framework 3.0 çalışma zamanı bileşenlerini kullanarak bu sağlayıcı için kaynak dosyası (AccessDBSampleProvider01.cs). Yükleme yönergeleri için bkz: [Windows PowerShell yükleme ve indirme Windows PowerShell SDK'sı](/powershell/developer/installing-the-windows-powershell-sdk).
>
> İndirilen kaynak dosyaları kullanılabilir  **\<PowerShell örnekleri >** dizin.
>
> Diğer Windows PowerShell sağlayıcısı uygulamaları hakkında daha fazla bilgi için bkz. [tasarlama bilgisayarınızı Windows PowerShell sağlayıcısındaki](./designing-your-windows-powershell-provider.md).

## <a name="code-sample"></a>Kod örneği

[!code-csharp[AccessDBProviderSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs#L11-L30 "AccessDBProviderSample01.cs")]

## <a name="see-also"></a>Ayrıca bkz:

[Windows PowerShell Programcı Kılavuzu](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK'sı](../windows-powershell-reference.md)