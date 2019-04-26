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
# <a name="accessdbprovidersample04-code-sample"></a><span data-ttu-id="09940-102">AccessDbProviderSample04 Kod Örneği</span><span class="sxs-lookup"><span data-stu-id="09940-102">AccessDbProviderSample04 Code Sample</span></span>

<span data-ttu-id="09940-103">Aşağıdaki kod bölümünde açıklanan Windows PowerShell sağlayıcısı uygulamasını gösterir [bir Windows PowerShell kapsayıcısı sağlayıcısı oluşturma](./creating-a-windows-powershell-container-provider.md).</span><span class="sxs-lookup"><span data-stu-id="09940-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span> <span data-ttu-id="09940-104">Bu sağlayıcı çok katmanlı veri depolarına üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="09940-104">This provider works on multi-layer data stores.</span></span> <span data-ttu-id="09940-105">Bu tür veri deposunun en üst düzey deposunun kök öğe içeriyor ve sonraki her düzeyi bir alt öğeleri düğüm olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="09940-105">For this type of data store, the top level of the store contains the root items and each subsequent level is referred to as a node of child items.</span></span> <span data-ttu-id="09940-106">Bu alt düğümleri üzerinde çalışmak kullanıcı izin vererek, bir kullanıcı hiyerarşik veri deposu etkileşim kurabilir.</span><span class="sxs-lookup"><span data-stu-id="09940-106">By allowing the user to work on these child nodes, a user can interact hierarchically through the data store.</span></span>

## <a name="code-sample"></a><span data-ttu-id="09940-107">Kod örneği</span><span class="sxs-lookup"><span data-stu-id="09940-107">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a><span data-ttu-id="09940-108">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="09940-108">See Also</span></span>

[<span data-ttu-id="09940-109">Windows PowerShell SDK'sı</span><span class="sxs-lookup"><span data-stu-id="09940-109">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)