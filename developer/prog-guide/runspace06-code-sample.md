---
title: Örnek kod RunSpace06 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d71f86d5-eb62-4b16-aa95-5fd3f314ffd3
caps.latest.revision: 6
ms.openlocfilehash: b6fdad90f7339e941d77646936b1b5952cd65500
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734940"
---
# <a name="runspace06-code-sample"></a><span data-ttu-id="f3f1c-102">RunSpace06 Kod Örneği</span><span class="sxs-lookup"><span data-stu-id="f3f1c-102">RunSpace06 Code Sample</span></span>

<span data-ttu-id="f3f1c-103">İşte kaynak kodunu Runspace06 örnek bölümünde açıklanan yönelik [bir Windows PowerShell ek bileşenini kullanarak bir çalışma alanı yapılandırma](https://msdn.microsoft.com/en-us/a7289ee8-9732-49ee-91c7-d533e9538b83).</span><span class="sxs-lookup"><span data-stu-id="f3f1c-103">Here is the source code for the Runspace06 sample described in [Configuring a Runspace Using a Windows PowerShell Snap-in](https://msdn.microsoft.com/en-us/a7289ee8-9732-49ee-91c7-d533e9538b83).</span></span> <span data-ttu-id="f3f1c-104">Bu örnek uygulama, bir Windows PowerShell, ardından bir işlem hattını tek bir komutla çalıştırmak için kullanılan eklentisinde, temel bir çalışma alanı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f3f1c-104">This sample application creates a runspace based on a Windows PowerShell snap-in, which is then used to run a pipeline with a single command.</span></span> <span data-ttu-id="f3f1c-105">Bunu yapmak için uygulama çalışma alanı yapılandırma bilgileri oluşturur, bir çalışma alanı oluşturur, tek bir komutla bir işlem hattı oluşturur ve sonra işlem hattını yürütür.</span><span class="sxs-lookup"><span data-stu-id="f3f1c-105">To do this, the application creates the runspace configuration information, creates a runspace, creates a pipeline with a single command, and then executes the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="f3f1c-106">İndirebileceğiniz C# Windows Vista için Windows Yazılım Geliştirme Seti ve Microsoft .NET Framework 3.0 çalışma zamanı bileşenlerini kullanarak kaynak dosyası (runspace06.cs).</span><span class="sxs-lookup"><span data-stu-id="f3f1c-106">You can download the C# source file (runspace06.cs) by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="f3f1c-107">Yükleme yönergeleri için bkz: [Windows PowerShell yükleme ve indirme Windows PowerShell SDK'sı](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="f3f1c-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="f3f1c-108">İndirilen kaynak dosyaları kullanılabilir  **\<PowerShell örnekleri >** dizin.</span><span class="sxs-lookup"><span data-stu-id="f3f1c-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="f3f1c-109">Kod örneği</span><span class="sxs-lookup"><span data-stu-id="f3f1c-109">Code Sample</span></span>

[!code-csharp[Runspace06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace06/Runspace06.cs#L11-L85 "Runspace06.cs")]

## <a name="see-also"></a><span data-ttu-id="f3f1c-110">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="f3f1c-110">See Also</span></span>

[<span data-ttu-id="f3f1c-111">Windows PowerShell Programcı Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f3f1c-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="f3f1c-112">Windows PowerShell SDK'sı</span><span class="sxs-lookup"><span data-stu-id="f3f1c-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)