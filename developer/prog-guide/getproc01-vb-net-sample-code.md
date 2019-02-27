---
title: GetProc01 (VB.NET) örnek kodu | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3ee87f67-6d2c-48cc-b300-3ae917c6dc88
caps.latest.revision: 5
ms.openlocfilehash: 1f11c89f60aef44905cbce3fe669def26119d12e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846861"
---
# <a name="getproc01-vbnet-sample-code"></a><span data-ttu-id="56ecd-102">GetProc01 (VB.NET) Örnek Kod</span><span class="sxs-lookup"><span data-stu-id="56ecd-102">GetProc01 (VB.NET) Sample Code</span></span>

<span data-ttu-id="56ecd-103">Aşağıdaki kod GetProc01 örnek cmdlet uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="56ecd-103">The following code shows the implementation of the GetProc01 sample cmdlet.</span></span> <span data-ttu-id="56ecd-104">Cmdlet için alma işlemi asıl işi bırakarak basitleştirilmiştir fark [System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="56ecd-104">Notice that the cmdlet is simplified by leaving the actual work of process retrieval to the [System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses) method.</span></span>

> [!NOTE]
> <span data-ttu-id="56ecd-105">İndirebileceğiniz C# .NET Framework 3.0 çalışma zamanı bileşenleri ve Microsoft Windows Yazılım Geliştirme Seti için Windows Vista'yı kullanarak bu Get-Proc cmdlet için kaynak dosyası (getproc01.cs).</span><span class="sxs-lookup"><span data-stu-id="56ecd-105">You can download the C# source file (getproc01.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="56ecd-106">Yükleme yönergeleri için bkz: [Windows PowerShell yükleme ve indirme Windows PowerShell SDK'sı](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="56ecd-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="56ecd-107">İndirebileceğiniz C# .NET Framework 3.0 çalışma zamanı bileşenleri ve Microsoft Windows Yazılım Geliştirme Seti için Windows Vista'yı kullanarak bu Get-Proc cmdlet için kaynak dosyası (getproc01.cs).</span><span class="sxs-lookup"><span data-stu-id="56ecd-107">You can download the C# source file (getproc01.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="56ecd-108">Yükleme yönergeleri için bkz: [Windows PowerShell yükleme ve indirme Windows PowerShell SDK'sı](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="56ecd-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="56ecd-109">İndirilen kaynak dosyaları kullanılabilir  **\<PowerShell örnekleri >** dizin.</span><span class="sxs-lookup"><span data-stu-id="56ecd-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="56ecd-110">Kod örneği</span><span class="sxs-lookup"><span data-stu-id="56ecd-110">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [msh_samplesgetproc01#getproc01vball](msh_samplesgetproc01#getproc01vball)]  -->

## <a name="see-also"></a><span data-ttu-id="56ecd-111">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="56ecd-111">See Also</span></span>

[<span data-ttu-id="56ecd-112">Windows PowerShell Programcı Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="56ecd-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="56ecd-113">Windows PowerShell SDK'sı</span><span class="sxs-lookup"><span data-stu-id="56ecd-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)