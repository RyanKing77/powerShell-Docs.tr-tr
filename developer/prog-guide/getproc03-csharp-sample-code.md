---
title: GetProc03 (C#) örnek kodu | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebc0d538-69ac-43d5-837d-b6f47344fc6a
caps.latest.revision: 5
ms.openlocfilehash: 4d921dd62999bc68b80838bafa2a3da8d4df3ebb
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057529"
---
# <a name="getproc03-c-sample-code"></a><span data-ttu-id="29f7d-102">GetProc03 (C#) Örnek Kod</span><span class="sxs-lookup"><span data-stu-id="29f7d-102">GetProc03 (C#) Sample Code</span></span>

<span data-ttu-id="29f7d-103">Aşağıdaki kod uygulamasını gösterir. bir `Get-Process` kabul edebilen cmdlet'inin ardışık düzendeki girişi.</span><span class="sxs-lookup"><span data-stu-id="29f7d-103">The following code shows the implementation of a `Get-Process` cmdlet that can accept pipelined input.</span></span> <span data-ttu-id="29f7d-104">Bu uygulama tanımlayan bir `Name` ardışık giriş kabul eden bir parametre ve yerel bilgisayardan sağlanan adlarına göre işlem bilgilerini alır ve ardından kullanır [System.Management.Automation.Cmdlet.WriteObject% 28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) nesneler gönderiliyor işlem hattının çıktı mekanizması olarak yöntemi.</span><span class="sxs-lookup"><span data-stu-id="29f7d-104">This implementation defines a `Name` parameter that accepts pipeline input, retrieves process information from the local computer based on the supplied names, and then uses the [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) method as the output mechanism for sending objects to the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="29f7d-105">İndirebileceğiniz C# .NET Framework 3.0 çalışma zamanı bileşenleri ve Microsoft Windows Yazılım Geliştirme Seti için Windows Vista'yı kullanarak bu Get-Proc cmdlet için kaynak dosyası (getprov03.cs).</span><span class="sxs-lookup"><span data-stu-id="29f7d-105">You can download the C# source file (getprov03.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="29f7d-106">Yükleme yönergeleri için bkz: [Windows PowerShell yükleme ve indirme Windows PowerShell SDK'sı](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="29f7d-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="29f7d-107">İndirilen kaynak dosyaları kullanılabilir  **\<PowerShell örnekleri >** dizin.</span><span class="sxs-lookup"><span data-stu-id="29f7d-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="29f7d-108">Kod örneği</span><span class="sxs-lookup"><span data-stu-id="29f7d-108">Code Sample</span></span>

[!code-csharp[GetProcessSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs#L11-L78 "GetProcessSample03.cs")]

## <a name="see-also"></a><span data-ttu-id="29f7d-109">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="29f7d-109">See Also</span></span>

[<span data-ttu-id="29f7d-110">Windows PowerShell Programcı Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="29f7d-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="29f7d-111">Windows PowerShell SDK'sı</span><span class="sxs-lookup"><span data-stu-id="29f7d-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)