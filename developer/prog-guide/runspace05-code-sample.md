---
title: Örnek kod RunSpace05 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9688cd69-07ea-4ea0-8822-0a4850bcf86c
caps.latest.revision: 7
ms.openlocfilehash: 2b5ac097e8a52832b0f8cfb93b84eef56fc64858
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845832"
---
# <a name="runspace05-code-sample"></a><span data-ttu-id="441fd-102">RunSpace05 Kod Örneği</span><span class="sxs-lookup"><span data-stu-id="441fd-102">RunSpace05 Code Sample</span></span>

<span data-ttu-id="441fd-103">Açıklanan Runspace05 örnek kaynak kodu işte [kullanarak bir çalışma alanı RunspaceConfiguration yapılandırma](http://msdn.microsoft.com/en-us/42681d19-2d05-4975-befd-afb1990e79b2).</span><span class="sxs-lookup"><span data-stu-id="441fd-103">Here is the source code for the Runspace05 sample that is described in [Configuring a Runspace Using RunspaceConfiguration](http://msdn.microsoft.com/en-us/42681d19-2d05-4975-befd-afb1990e79b2).</span></span> <span data-ttu-id="441fd-104">Bu örnek, çalışma alanı yapılandırma bilgileri oluşturmak, bir çalışma alanı oluşturma, tek bir komutla bir işlem hattı oluşturursunuz ve ardından işlem hattı yürütme işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="441fd-104">This sample shows how to create the runspace configuration information, create a runspace, create a pipeline with a single command, and then execute the pipeline.</span></span> <span data-ttu-id="441fd-105">Yürütülen komut `Get-Process` cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="441fd-105">The command that is executed is the `Get-Process` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="441fd-106">İndirebileceğiniz C# Windows Yazılım Geliştirme Seti için Windows Vista Microsoft ve Microsoft .NET Framework 3.0 çalışma zamanı bileşenlerini kullanarak kaynak dosyası (runspace05.cs).</span><span class="sxs-lookup"><span data-stu-id="441fd-106">You can download the C# source file (runspace05.cs) by using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="441fd-107">Yükleme yönergeleri için bkz: [Windows PowerShell yükleme ve indirme Windows PowerShell SDK'sı](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="441fd-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="441fd-108">İndirebileceğiniz C# Windows Yazılım Geliştirme Seti için Windows Vista Microsoft ve Microsoft .NET Framework 3.0 çalışma zamanı bileşenlerini kullanarak kaynak dosyası (runspace05.cs).</span><span class="sxs-lookup"><span data-stu-id="441fd-108">You can download the C# source file (runspace05.cs) by using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="441fd-109">Yükleme yönergeleri için bkz: [Windows PowerShell yükleme ve indirme Windows PowerShell SDK'sı](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="441fd-109">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="441fd-110">İndirilen kaynak dosyaları kullanılabilir  **\<PowerShell örnekleri >** dizin.</span><span class="sxs-lookup"><span data-stu-id="441fd-110">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="441fd-111">Kod örneği</span><span class="sxs-lookup"><span data-stu-id="441fd-111">Code Sample</span></span>

[!code-csharp[Runspace05.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace05/Runspace05.cs#L11-L86 "Runspace05.cs")]

## <a name="see-also"></a><span data-ttu-id="441fd-112">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="441fd-112">See Also</span></span>

[<span data-ttu-id="441fd-113">Windows PowerShell Programcı Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="441fd-113">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="441fd-114">Windows PowerShell SDK'sı</span><span class="sxs-lookup"><span data-stu-id="441fd-114">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)