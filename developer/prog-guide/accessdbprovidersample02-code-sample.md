---
title: Örnek kod AccessDbProviderSample02 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b89a4903-3efc-4b08-9b20-2baadf1d1b66
caps.latest.revision: 6
ms.openlocfilehash: 22a7bdf43a294d1e28f78ccf3412173892fdd53e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847274"
---
# <a name="accessdbprovidersample02-code-sample"></a><span data-ttu-id="673dd-102">AccessDbProviderSample02 Kod Örneği</span><span class="sxs-lookup"><span data-stu-id="673dd-102">AccessDbProviderSample02 Code Sample</span></span>

<span data-ttu-id="673dd-103">Aşağıdaki kod bölümünde açıklanan Windows PowerShell sağlayıcısı uygulamasını gösterir [sürücü bir Windows PowerShell sağlayıcısı oluşturma](./creating-a-windows-powershell-drive-provider.md).</span><span class="sxs-lookup"><span data-stu-id="673dd-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Windows PowerShell Drive Provider](./creating-a-windows-powershell-drive-provider.md).</span></span> <span data-ttu-id="673dd-104">Bu uygulama bir yol oluşturur, bir Access veritabanına bir bağlantı kurar ve ardından sürücü kaldırır.</span><span class="sxs-lookup"><span data-stu-id="673dd-104">This implementation creates a path, makes a connection to an Access database, and then removes the drive.</span></span>

> [!NOTE]
> <span data-ttu-id="673dd-105">İndirebileceğiniz C# Microsoft .NET Framework 3.0 çalışma zamanı bileşenleri ve Microsoft Windows Yazılım Geliştirme Seti için Windows Vista'yı kullanarak bu sağlayıcı için kaynak dosyası (AccessDBSampleProvider02.cs).</span><span class="sxs-lookup"><span data-stu-id="673dd-105">You can download the C# source file (AccessDBSampleProvider02.cs) for this provider using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="673dd-106">Yükleme yönergeleri için bkz: [Windows PowerShell yükleme ve indirme Windows PowerShell SDK'sı](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="673dd-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="673dd-107">İndirebileceğiniz C# Microsoft .NET Framework 3.0 çalışma zamanı bileşenleri ve Microsoft Windows Yazılım Geliştirme Seti için Windows Vista'yı kullanarak bu sağlayıcı için kaynak dosyası (AccessDBSampleProvider02.cs).</span><span class="sxs-lookup"><span data-stu-id="673dd-107">You can download the C# source file (AccessDBSampleProvider02.cs) for this provider using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="673dd-108">Yükleme yönergeleri için bkz: [Windows PowerShell yükleme ve indirme Windows PowerShell SDK'sı](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="673dd-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="673dd-109">İndirilen kaynak dosyaları kullanılabilir  **\<PowerShell örnekleri >** dizin.</span><span class="sxs-lookup"><span data-stu-id="673dd-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="673dd-110">Diğer Windows PowerShell sağlayıcısı uygulamaları hakkında daha fazla bilgi için bkz. [tasarlama bilgisayarınızı Windows PowerShell sağlayıcısındaki](./designing-your-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="673dd-110">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="673dd-111">Kod örneği</span><span class="sxs-lookup"><span data-stu-id="673dd-111">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L11-L154 "AccessDBProviderSample02.cs")]


## <a name="see-also"></a><span data-ttu-id="673dd-112">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="673dd-112">See Also</span></span>

[<span data-ttu-id="673dd-113">Windows PowerShell Programcı Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="673dd-113">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="673dd-114">Windows PowerShell SDK'sı</span><span class="sxs-lookup"><span data-stu-id="673dd-114">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)