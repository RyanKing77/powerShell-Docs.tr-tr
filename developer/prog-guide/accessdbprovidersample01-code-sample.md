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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849381"
---
# <a name="accessdbprovidersample01-code-sample"></a><span data-ttu-id="d5417-102">AccessDbProviderSample01 Kod Örneği</span><span class="sxs-lookup"><span data-stu-id="d5417-102">AccessDbProviderSample01 Code Sample</span></span>

<span data-ttu-id="d5417-103">Aşağıdaki kod bölümünde açıklanan Windows PowerShell sağlayıcısı uygulamasını gösterir [temel bir Windows PowerShell sağlayıcısı oluşturma](./creating-a-basic-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="d5417-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Basic Windows PowerShell Provider](./creating-a-basic-windows-powershell-provider.md).</span></span> <span data-ttu-id="d5417-104">Bu uygulama başlatma ve durdurma sağlayıcısı için yöntemler sağlar ve bir veri deposuna erişmek için alın veya veri deposuna veri kümesi için bir yol sağlamaz olsa da, tüm sağlayıcıları tarafından gerekli olan temel işlevleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="d5417-104">This implementation provides methods for starting and stopping the provider, and although it does not provide a means to access a data store or to get or set the data in the data store, it does provide the basic functionality that is required by all providers.</span></span>

> [!NOTE]
> <span data-ttu-id="d5417-105">İndirebileceğiniz C# Windows Vista için Windows Yazılım Geliştirme Seti ve Microsoft .NET Framework 3.0 çalışma zamanı bileşenlerini kullanarak bu sağlayıcı için kaynak dosyası (AccessDBSampleProvider01.cs).</span><span class="sxs-lookup"><span data-stu-id="d5417-105">You can download the C# source file (AccessDBSampleProvider01.cs) for this provider by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="d5417-106">Yükleme yönergeleri için bkz: [Windows PowerShell yükleme ve indirme Windows PowerShell SDK'sı](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="d5417-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="d5417-107">İndirilen kaynak dosyaları kullanılabilir  **\<PowerShell örnekleri >** dizin.</span><span class="sxs-lookup"><span data-stu-id="d5417-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="d5417-108">Diğer Windows PowerShell sağlayıcısı uygulamaları hakkında daha fazla bilgi için bkz. [tasarlama bilgisayarınızı Windows PowerShell sağlayıcısındaki](./designing-your-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="d5417-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="d5417-109">Kod örneği</span><span class="sxs-lookup"><span data-stu-id="d5417-109">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs#L11-L30 "AccessDBProviderSample01.cs")]

## <a name="see-also"></a><span data-ttu-id="d5417-110">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="d5417-110">See Also</span></span>

[<span data-ttu-id="d5417-111">Windows PowerShell Programcı Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="d5417-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="d5417-112">Windows PowerShell SDK'sı</span><span class="sxs-lookup"><span data-stu-id="d5417-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)