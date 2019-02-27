---
title: Bir Windows PowerShell sağlayıcısı yazma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a54ce657-e0e0-4b3e-b9dc-aed39876f933
caps.latest.revision: 11
ms.openlocfilehash: 58252956184703fdcdb3aa9b1db617c6e91294c1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849654"
---
# <a name="writing-a-windows-powershell-provider"></a><span data-ttu-id="23710-102">Windows PowerShell Sağlayıcısı Yazma</span><span class="sxs-lookup"><span data-stu-id="23710-102">Writing a Windows PowerShell Provider</span></span>

<span data-ttu-id="23710-103">"Bir Windows PowerShell sağlayıcısı yazma" için Windows PowerShell sağlayıcıları tasarlama program yöneticileri ve sağlayıcı kod uygulama geliştiriciler içindir.</span><span class="sxs-lookup"><span data-stu-id="23710-103">"Writing a Windows PowerShell Provider" is for program managers who are designing Windows PowerShell providers and for developers who are implementing provider code.</span></span> <span data-ttu-id="23710-104">Windows PowerShell sağlayıcıları nasıl çalıştığını anlamanıza yardımcı olur ve tasarlama ya da kendi sağlayıcılarınızı yazma konusu başlatmak için kullanabileceğiniz örnek kodu sağlar.</span><span class="sxs-lookup"><span data-stu-id="23710-104">It will help you understand how Windows PowerShell providers work, and it provides sample code that you can use to start designing or writing your own providers.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="23710-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="23710-105">In This Section</span></span>

<span data-ttu-id="23710-106">[Windows PowerShell sağlayıcısı hızlı](./windows-powershell-provider-quickstart.md) kod örneği ve bir çok temel sağlayıcısının gözden geçirme.</span><span class="sxs-lookup"><span data-stu-id="23710-106">[Windows PowerShell Provider QuickStart](./windows-powershell-provider-quickstart.md) Example code and walkthrough of a very basic provider.</span></span>

<span data-ttu-id="23710-107">[Windows PowerShell sağlayıcısı genel bakış](./windows-powershell-provider-overview.md) Bu bölüm, Windows PowerShell sağlayıcıları nedir ve nasıl çalıştığını açıklayan konulara içerir.</span><span class="sxs-lookup"><span data-stu-id="23710-107">[Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md) This section contains topics that describe what Windows PowerShell providers are and how they work.</span></span>

<span data-ttu-id="23710-108">[Bir öğe sağlayıcısı yazma](./writing-an-item-provider.md) örnek kod ve, alma ve ayarlama öğelerini destekleyen yöntemler Kılavuzu.</span><span class="sxs-lookup"><span data-stu-id="23710-108">[Writing an item provider](./writing-an-item-provider.md) Example code and walkthrough of methods that support getting and setting items.</span></span>

<span data-ttu-id="23710-109">[Bir kapsayıcı sağlayıcısı yazma](./writing-a-container-provider.md) örnek kod ve kapsayıcıları (alt öğeleri olarak diğer öğelere sahip öğeleri) destekleyen yöntemler Kılavuzu.</span><span class="sxs-lookup"><span data-stu-id="23710-109">[Writing a container provider](./writing-a-container-provider.md) Example code and walkthrough of methods that support containers (items that have other items as children).</span></span>

<span data-ttu-id="23710-110">[Bir gezinti sağlayıcısı yazma](./writing-a-navigation-provider.md) örnek kod ve iç içe geçmiş kapsayıcılar, göreli yolları ve bir yol diğerine taşıma öğeleri destekleyen yöntemler Kılavuzu.</span><span class="sxs-lookup"><span data-stu-id="23710-110">[Writing a navigation provider](./writing-a-navigation-provider.md) Example code and walkthrough of methods that support nested containers, relative paths, and moving items from one path to another.</span></span>

<span data-ttu-id="23710-111">[Sağlayıcı örnekleri](./provider-samples.md) Bu bölüm, sağlayıcıları örnekleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="23710-111">[Provider Samples](./provider-samples.md) This section provides samples of providers.</span></span>

## <a name="see-also"></a><span data-ttu-id="23710-112">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="23710-112">See Also</span></span>

[<span data-ttu-id="23710-113">Windows PowerShell SDK'sı</span><span class="sxs-lookup"><span data-stu-id="23710-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)