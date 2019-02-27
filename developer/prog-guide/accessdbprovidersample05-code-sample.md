---
title: Örnek kod AccessDbProviderSample05 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fea5d923-8001-4407-8975-743918bc8c80
caps.latest.revision: 6
ms.openlocfilehash: 92c2d4d200ea917f0111ef9424de71611270fba4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845853"
---
# <a name="accessdbprovidersample05-code-sample"></a><span data-ttu-id="60f98-102">AccessDbProviderSample05 Kod Örneği</span><span class="sxs-lookup"><span data-stu-id="60f98-102">AccessDbProviderSample05 Code Sample</span></span>

<span data-ttu-id="60f98-103">Aşağıdaki kod bölümünde açıklanan Windows PowerShell Gezinti sağlayıcısı uygulamasını gösterir [bir Windows PowerShell Gezinti sağlayıcı oluşturma](./creating-a-windows-powershell-navigation-provider.md).</span><span class="sxs-lookup"><span data-stu-id="60f98-103">The following code shows the implementation of the Windows PowerShell navigation provider described in [Creating a Windows PowerShell Navigation Provider](./creating-a-windows-powershell-navigation-provider.md).</span></span> <span data-ttu-id="60f98-104">Bu sağlayıcı özyinelemeli komutları, iç içe geçmiş kapsayıcılar ve veri deposuna gidin izin göreli yolları destekler.</span><span class="sxs-lookup"><span data-stu-id="60f98-104">This provider supports recursive commands, nested containers, and relative paths that allow it to navigate the data store.</span></span>

## <a name="code-sample"></a><span data-ttu-id="60f98-105">Kod örneği</span><span class="sxs-lookup"><span data-stu-id="60f98-105">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample05.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs#L11-L1960 "AccessDBProviderSample05.cs")]

## <a name="see-also"></a><span data-ttu-id="60f98-106">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="60f98-106">See Also</span></span>

[<span data-ttu-id="60f98-107">Windows PowerShell SDK'sı</span><span class="sxs-lookup"><span data-stu-id="60f98-107">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)