---
title: Örnek kod AccessDbProviderSample04 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9374c4a-e499-4516-9eb6-107c59df98d9
caps.latest.revision: 7
ms.openlocfilehash: 43f01b9cd6af3ab6c26f88ee0c1e9269499b2bc3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081963"
---
# <a name="accessdbprovidersample04-code-sample"></a>AccessDbProviderSample04 Kod Örneği

Aşağıdaki kod bölümünde açıklanan Windows PowerShell sağlayıcısı uygulamasını gösterir [bir Windows PowerShell kapsayıcısı sağlayıcısı oluşturma](./creating-a-windows-powershell-container-provider.md). Bu sağlayıcı çok katmanlı veri depolarına üzerinde çalışır. Bu tür veri deposunun en üst düzey deposunun kök öğe içeriyor ve sonraki her düzeyi bir alt öğeleri düğüm olarak adlandırılır. Bu alt düğümleri üzerinde çalışmak kullanıcı izin vererek, bir kullanıcı hiyerarşik veri deposu etkileşim kurabilir.

## <a name="code-sample"></a>Kod örneği

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a>Ayrıca bkz:

[Windows PowerShell SDK'sı](../windows-powershell-reference.md)