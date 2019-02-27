---
title: StopProcessSample04 (C#) örnek kodu | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 778ce1a2-e16d-4af5-b15b-77ca4326bdc4
caps.latest.revision: 5
ms.openlocfilehash: 5a9e7a9ea13c9a62440b7cd80285751c901bcdd4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851516"
---
# <a name="stopprocesssample04-c-sample-code"></a><span data-ttu-id="e9081-102">StopProcessSample04 (C#) Örnek Kod</span><span class="sxs-lookup"><span data-stu-id="e9081-102">StopProcessSample04 (C#) Sample Code</span></span>

<span data-ttu-id="e9081-103">İşte tam C# StopProc04 örnek cmdlet için kod örneği.</span><span class="sxs-lookup"><span data-stu-id="e9081-103">Here is the complete C# sample code for the StopProc04 sample cmdlet.</span></span> <span data-ttu-id="e9081-104">Bu kodudur `Stop-Process` cmdlet'i açıklanan [bir cmdlet'e parametre kümeleri ekleme](../cmdlet/adding-parameter-sets-to-a-cmdlet.md).</span><span class="sxs-lookup"><span data-stu-id="e9081-104">This is the code for the `Stop-Process` cmdlet described in [Adding Parameter Sets to a Cmdlet](../cmdlet/adding-parameter-sets-to-a-cmdlet.md).</span></span> <span data-ttu-id="e9081-105">`Stop-Process` Cmdlet Get-Proc cmdlet'i kullanılarak alınır işlemleri durdurmak için tasarlanmıştır (açıklanan [oluşturma bilgisayarınızı ilk Cmdlet](../cmdlet/creating-a-cmdlet-without-parameters.md)).</span><span class="sxs-lookup"><span data-stu-id="e9081-105">The `Stop-Process` cmdlet is designed to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](../cmdlet/creating-a-cmdlet-without-parameters.md)).</span></span>

> [!NOTE]
> <span data-ttu-id="e9081-106">İndirebileceğiniz C# .NET Framework 3.0 çalışma zamanı bileşenleri ve Microsoft Windows Yazılım Geliştirme Seti için Windows Vista'yı kullanarak bu Stop-Proc cmdlet'in (stopprocesssample04.cs) kaynak dosyası.</span><span class="sxs-lookup"><span data-stu-id="e9081-106">You can download the C# (stopprocesssample04.cs) source file for this Stop-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="e9081-107">Yükleme yönergeleri için bkz: [Windows PowerShell yükleme ve indirme Windows PowerShell SDK'sı](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="e9081-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="e9081-108">İndirebileceğiniz C# .NET Framework 3.0 çalışma zamanı bileşenleri ve Microsoft Windows Yazılım Geliştirme Seti için Windows Vista'yı kullanarak bu Stop-Proc cmdlet'in (stopprocesssample04.cs) kaynak dosyası.</span><span class="sxs-lookup"><span data-stu-id="e9081-108">You can download the C# (stopprocesssample04.cs) source file for this Stop-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="e9081-109">Yükleme yönergeleri için bkz: [Windows PowerShell yükleme ve indirme Windows PowerShell SDK'sı](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="e9081-109">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="e9081-110">İndirilen kaynak dosyaları kullanılabilir  **\<PowerShell örnekleri >** dizin.</span><span class="sxs-lookup"><span data-stu-id="e9081-110">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

[!code-csharp[StopProcessSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/StopProcessSample04/StopProcessSample04.cs#L11-L435 "StopProcessSample04.cs")]

## <a name="see-also"></a><span data-ttu-id="e9081-111">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="e9081-111">See Also</span></span>

[<span data-ttu-id="e9081-112">Windows PowerShell Programcı Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e9081-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="e9081-113">Windows PowerShell SDK'sı</span><span class="sxs-lookup"><span data-stu-id="e9081-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)