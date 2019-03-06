---
title: GetProc04 (VB.NET) örnek kodu | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d22f47b-3679-4587-a559-94454415d2dd
caps.latest.revision: 5
ms.openlocfilehash: 8de99247574de130b91eea78b9af81dafbab48eb
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429627"
---
# <a name="getproc04-vbnet-sample-code"></a><span data-ttu-id="12ece-102">GetProc04 (VB.NET) Örnek Kod</span><span class="sxs-lookup"><span data-stu-id="12ece-102">GetProc04 (VB.NET) Sample Code</span></span>

<span data-ttu-id="12ece-103">Aşağıdaki kod uygulamasını gösterir. bir `Get-Process` olmak üzere sonlandırmasız hatalar raporları cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="12ece-103">The following code shows the implementation of a `Get-Process` cmdlet that reports nonterminating errors.</span></span> <span data-ttu-id="12ece-104">Bu uygulama çağrıları [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) rapor olmak üzere sonlandırmasız hatalar için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="12ece-104">This implementation calls the [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report nonterminating errors.</span></span>

> [!NOTE]
> <span data-ttu-id="12ece-105">İndirebileceğiniz C# .NET Framework 3.0 çalışma zamanı bileşenleri ve Microsoft Windows Yazılım Geliştirme Seti için Windows Vista'yı kullanarak bu Get-Proc cmdlet için kaynak dosyası (getprov04.cs).</span><span class="sxs-lookup"><span data-stu-id="12ece-105">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="12ece-106">Yükleme yönergeleri için bkz: [Windows PowerShell yükleme ve indirme Windows PowerShell SDK'sı](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="12ece-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="12ece-107">İndirilen kaynak dosyaları kullanılabilir  **\<PowerShell örnekleri >** dizin.</span><span class="sxs-lookup"><span data-stu-id="12ece-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="12ece-108">Kod örneği</span><span class="sxs-lookup"><span data-stu-id="12ece-108">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc04#GetProc04vball](Msh_samplesgetproc04#GetProc04vball)]  -->

## <a name="see-also"></a><span data-ttu-id="12ece-109">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="12ece-109">See Also</span></span>

[<span data-ttu-id="12ece-110">Windows PowerShell Programcı Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="12ece-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="12ece-111">Windows PowerShell SDK'sı</span><span class="sxs-lookup"><span data-stu-id="12ece-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)