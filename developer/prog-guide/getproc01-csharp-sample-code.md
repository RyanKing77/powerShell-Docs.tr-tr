---
title: GetProc01 (C#) örnek kodu | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 65094bb7-1972-44b3-b8b0-5f639860b58c
caps.latest.revision: 5
ms.openlocfilehash: 32c8214935a8c9f455426b76966d8c7fb33353d4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081742"
---
# <a name="getproc01-c-sample-code"></a><span data-ttu-id="2a5c4-102">GetProc01 (C#) Örnek Kod</span><span class="sxs-lookup"><span data-stu-id="2a5c4-102">GetProc01 (C#) Sample Code</span></span>

<span data-ttu-id="2a5c4-103">Aşağıdaki kod GetProc01 örnek cmdlet uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2a5c4-103">The following code shows the implementation of the GetProc01 sample cmdlet.</span></span> <span data-ttu-id="2a5c4-104">Cmdlet için alma işlemi asıl işi bırakarak basitleştirilmiştir fark [System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2a5c4-104">Notice that the cmdlet is simplified by leaving the actual work of process retrieval to the [System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses) method.</span></span>

> [!NOTE]
> <span data-ttu-id="2a5c4-105">İndirebileceğiniz C# .NET Framework 3.0 çalışma zamanı bileşenleri ve Microsoft Windows Yazılım Geliştirme Seti için Windows Vista'yı kullanarak bu Get-Proc cmdlet için kaynak dosyası (getproc01.cs).</span><span class="sxs-lookup"><span data-stu-id="2a5c4-105">You can download the C# source file (getproc01.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="2a5c4-106">Yükleme yönergeleri için bkz: [Windows PowerShell yükleme ve indirme Windows PowerShell SDK'sı](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="2a5c4-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="2a5c4-107">İndirilen kaynak dosyaları kullanılabilir  **\<PowerShell örnekleri >** dizin.</span><span class="sxs-lookup"><span data-stu-id="2a5c4-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="2a5c4-108">Kod örneği</span><span class="sxs-lookup"><span data-stu-id="2a5c4-108">Code Sample</span></span>

[!code-csharp[GetProcessSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs#L11-L126 "GetProcessSample01.cs")]

## <a name="see-also"></a><span data-ttu-id="2a5c4-109">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="2a5c4-109">See Also</span></span>

[<span data-ttu-id="2a5c4-110">Windows PowerShell Programcı Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="2a5c4-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="2a5c4-111">Windows PowerShell SDK'sı</span><span class="sxs-lookup"><span data-stu-id="2a5c4-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)