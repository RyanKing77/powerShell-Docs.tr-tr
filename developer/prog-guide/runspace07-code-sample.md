---
title: Örnek kod RunSpace07 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ad306d9-45c2-4d55-8e64-fdcba43402c5
caps.latest.revision: 6
ms.openlocfilehash: 064e7d7ea2ee173bbcdd75a9f3a6c12582afe17b
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429653"
---
# <a name="runspace07-code-sample"></a><span data-ttu-id="4d31e-102">RunSpace07 Kod Örneği</span><span class="sxs-lookup"><span data-stu-id="4d31e-102">RunSpace07 Code Sample</span></span>

<span data-ttu-id="4d31e-103">İşte kaynak kodunu Runspace07 örnek bölümünde açıklanan yönelik [bir konsol uygulaması olduğunu ekler komutları bir işlem hattı oluşturma](http://msdn.microsoft.com/en-us/01eb7808-e97b-4905-80be-9e2fa38c262e).</span><span class="sxs-lookup"><span data-stu-id="4d31e-103">Here is the source code for the Runspace07 sample described in [Creating a Console Application That Adds Commands to a Pipeline](http://msdn.microsoft.com/en-us/01eb7808-e97b-4905-80be-9e2fa38c262e).</span></span> <span data-ttu-id="4d31e-104">Bu örnek uygulama bir çalışma alanı oluşturur, bir işlem hattı oluşturur, iki komutu ardışık düzene ekler ve sonra işlem hattını yürütür.</span><span class="sxs-lookup"><span data-stu-id="4d31e-104">This sample application creates a runspace, creates a pipeline, adds two commands to the pipeline, and then executes the pipeline.</span></span> <span data-ttu-id="4d31e-105">Ardışık düzenine eklenen komutlar `Get-Process` ve `Measure-Object` cmdlet'leri.</span><span class="sxs-lookup"><span data-stu-id="4d31e-105">The commands added to the pipeline are the `Get-Process` and `Measure-Object` cmdlets.</span></span>

> [!NOTE]
> <span data-ttu-id="4d31e-106">İndirebileceğiniz C# Microsoft .NET Framework 3.0 çalışma zamanı bileşenleri ve Microsoft Windows Yazılım Geliştirme Seti için Windows Vista'yı kullanarak kaynak dosyası (runspace07.cs).</span><span class="sxs-lookup"><span data-stu-id="4d31e-106">You can download the C# source file (runspace07.cs) using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="4d31e-107">Yükleme yönergeleri için bkz: [Windows PowerShell yükleme ve indirme Windows PowerShell SDK'sı](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="4d31e-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="4d31e-108">İndirilen kaynak dosyaları kullanılabilir  **\<PowerShell örnekleri >** dizin.</span><span class="sxs-lookup"><span data-stu-id="4d31e-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="4d31e-109">Kod örneği</span><span class="sxs-lookup"><span data-stu-id="4d31e-109">Code Sample</span></span>

[!code-csharp[Runspace07.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace07/Runspace07.cs#L11-L108 "Runspace07.cs")]

## <a name="see-also"></a><span data-ttu-id="4d31e-110">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="4d31e-110">See Also</span></span>

[<span data-ttu-id="4d31e-111">Windows PowerShell Programcı Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="4d31e-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="4d31e-112">Windows PowerShell SDK'sı</span><span class="sxs-lookup"><span data-stu-id="4d31e-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)