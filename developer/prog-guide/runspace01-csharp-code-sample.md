---
title: Runspace01 (C#) kod örneği | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d59f8b7c-e800-4633-aa5b-74d4c57e2706
caps.latest.revision: 6
ms.openlocfilehash: ab067485d70523a16493eb57170615ab300eaa98
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67735046"
---
# <a name="runspace01-c-code-sample"></a><span data-ttu-id="c8db8-102">Runspace01 (C#) Kod Örneği</span><span class="sxs-lookup"><span data-stu-id="c8db8-102">Runspace01 (C#) Code Sample</span></span>

<span data-ttu-id="c8db8-103">İşte kod örnekleri için bir çalışma açıklanan [belirtilen bir komutu bir konsol uygulaması, çalışır oluşturma](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program).</span><span class="sxs-lookup"><span data-stu-id="c8db8-103">Here are the code samples for the runspace described in [Creating a Console Application That Runs a Specified Command](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program).</span></span> <span data-ttu-id="c8db8-104">Bunu yapmak için uygulama bir çalışma alanı çağırır ve ardından bir komut çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="c8db8-104">To do this, the application invokes a runspace, and then invokes a command.</span></span> <span data-ttu-id="c8db8-105">(Unutmayın. Bu uygulama çalışma alanı yapılandırma bilgileri belirtmiyor veya açıkça bir işlem hattı oluşturur).</span><span class="sxs-lookup"><span data-stu-id="c8db8-105">(Note that this application does not specify runspace configuration information, nor does it explicitly create a pipeline).</span></span> <span data-ttu-id="c8db8-106">Çağrılan komut `Get-Process` cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="c8db8-106">The command that is invoked is the `Get-Process` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="c8db8-107">İndirebileceğiniz C# Microsoft .NET Framework 3.0 çalışma zamanı bileşenleri ve Microsoft Windows Yazılım Geliştirme Seti için Windows Vista'yı kullanarak bu çalışma alanı için kaynak dosyası (runspace01.cs).</span><span class="sxs-lookup"><span data-stu-id="c8db8-107">You can download the C# source file (runspace01.cs) for this runspace using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="c8db8-108">Yükleme yönergeleri için bkz: [Windows PowerShell yükleme ve indirme Windows PowerShell SDK'sı](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="c8db8-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="c8db8-109">İndirilen kaynak dosyaları kullanılabilir  **\<PowerShell örnekleri >** dizin.</span><span class="sxs-lookup"><span data-stu-id="c8db8-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="c8db8-110">Kod örneği</span><span class="sxs-lookup"><span data-stu-id="c8db8-110">Code Sample</span></span>

[!code-csharp[Runspace01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace01/Runspace01.cs#L11-L62 "Runspace01.cs")]

## <a name="see-also"></a><span data-ttu-id="c8db8-111">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="c8db8-111">See Also</span></span>

[<span data-ttu-id="c8db8-112">Windows PowerShell Programcı Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c8db8-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="c8db8-113">Windows PowerShell SDK'sı</span><span class="sxs-lookup"><span data-stu-id="c8db8-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)