---
title: Örnek kod AccessDbProviderSample06 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: baab6a56-c199-48d7-a03e-a904b1bb1baa
caps.latest.revision: 7
ms.openlocfilehash: 6e86318573df92b9ec84056631843e0efa096a3b
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795615"
---
# <a name="accessdbprovidersample06-code-sample"></a><span data-ttu-id="22809-102">AccessDbProviderSample06 Kod Örneği</span><span class="sxs-lookup"><span data-stu-id="22809-102">AccessDbProviderSample06 Code Sample</span></span>

<span data-ttu-id="22809-103">Aşağıdaki kod içeriği sağlayıcısı açıklanan Windows PowerShell uygulamasını gösterir [bir Windows PowerShell içerik sağlayıcı oluşturma](./creating-a-windows-powershell-content-provider.md).</span><span class="sxs-lookup"><span data-stu-id="22809-103">The following code shows the implementation of the Windows PowerShell content provider described in [Creating a Windows PowerShell Content Provider](./creating-a-windows-powershell-content-provider.md).</span></span> <span data-ttu-id="22809-104">Bu sağlayıcı veri deposunda öğeleri içeriğini işlemek kullanıcının sağlar.</span><span class="sxs-lookup"><span data-stu-id="22809-104">This provider enables the user to manipulate the contents of the items in a data store.</span></span>

> [!NOTE]
> <span data-ttu-id="22809-105">İndirebileceğiniz C# Windows Yazılım Geliştirme Seti için Windows Vista Microsoft ve Microsoft .NET Framework 3.0 çalışma zamanı bileşenlerini kullanarak bu sağlayıcı için kaynak dosyası (AccessDBSampleProvider06.cs).</span><span class="sxs-lookup"><span data-stu-id="22809-105">You can download the C# source file (AccessDBSampleProvider06.cs) for this provider by using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="22809-106">Yükleme yönergeleri için bkz: [Windows PowerShell yükleme ve indirme Windows PowerShell SDK'sı](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="22809-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="22809-107">İndirilen kaynak dosyaları kullanılabilir  **\<PowerShell örnekleri >** dizin.</span><span class="sxs-lookup"><span data-stu-id="22809-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="22809-108">Diğer Windows PowerShell sağlayıcısı uygulamaları hakkında daha fazla bilgi için bkz. [tasarlama bilgisayarınızı Windows PowerShell sağlayıcısındaki](./designing-your-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="22809-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="22809-109">Kod örneği</span><span class="sxs-lookup"><span data-stu-id="22809-109">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L2399 "AccessDBProviderSample06.cs")]

## <a name="see-also"></a><span data-ttu-id="22809-110">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="22809-110">See Also</span></span>

[<span data-ttu-id="22809-111">Windows PowerShell Programcı Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="22809-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="22809-112">Windows PowerShell SDK'sı</span><span class="sxs-lookup"><span data-stu-id="22809-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)