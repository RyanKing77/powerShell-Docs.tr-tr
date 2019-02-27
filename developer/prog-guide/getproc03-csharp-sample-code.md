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
ms.openlocfilehash: c24d18a2b80f8f9b62b5418fed35f54f7c7da23c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846399"
---
# <a name="getproc03-c-sample-code"></a><span data-ttu-id="441a6-102">GetProc03 (C#) Örnek Kod</span><span class="sxs-lookup"><span data-stu-id="441a6-102">GetProc03 (C#) Sample Code</span></span>

<span data-ttu-id="441a6-103">Aşağıdaki kod uygulamasını gösterir. bir `Get-Process` kabul edebilen cmdlet'inin ardışık düzendeki girişi.</span><span class="sxs-lookup"><span data-stu-id="441a6-103">The following code shows the implementation of a `Get-Process` cmdlet that can accept pipelined input.</span></span> <span data-ttu-id="441a6-104">Bu uygulama tanımlayan bir `Name` ardışık giriş kabul eden bir parametre ve yerel bilgisayardan sağlanan adlarına göre işlem bilgilerini alır ve ardından kullanır [System.Management.Automation.Cmdlet.Writeobject% 28System.Object%2Csystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) nesneler gönderiliyor işlem hattının çıktı mekanizması olarak yöntemi.</span><span class="sxs-lookup"><span data-stu-id="441a6-104">This implementation defines a `Name` parameter that accepts pipeline input, retrieves process information from the local computer based on the supplied names, and then uses the [System.Management.Automation.Cmdlet.Writeobject%28System.Object%2Csystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) method as the output mechanism for sending objects to the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="441a6-105">İndirebileceğiniz C# .NET Framework 3.0 çalışma zamanı bileşenleri ve Microsoft Windows Yazılım Geliştirme Seti için Windows Vista'yı kullanarak bu Get-Proc cmdlet için kaynak dosyası (getprov03.cs).</span><span class="sxs-lookup"><span data-stu-id="441a6-105">You can download the C# source file (getprov03.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="441a6-106">Yükleme yönergeleri için bkz: [Windows PowerShell yükleme ve indirme Windows PowerShell SDK'sı](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="441a6-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="441a6-107">İndirebileceğiniz C# .NET Framework 3.0 çalışma zamanı bileşenleri ve Microsoft Windows Yazılım Geliştirme Seti için Windows Vista'yı kullanarak bu Get-Proc cmdlet için kaynak dosyası (getprov03.cs).</span><span class="sxs-lookup"><span data-stu-id="441a6-107">You can download the C# source file (getprov03.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="441a6-108">Yükleme yönergeleri için bkz: [Windows PowerShell yükleme ve indirme Windows PowerShell SDK'sı](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="441a6-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="441a6-109">İndirilen kaynak dosyaları kullanılabilir  **\<PowerShell örnekleri >** dizin.</span><span class="sxs-lookup"><span data-stu-id="441a6-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="441a6-110">Kod örneği</span><span class="sxs-lookup"><span data-stu-id="441a6-110">Code Sample</span></span>

[!code-csharp[GetProcessSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs#L11-L78 "GetProcessSample03.cs")]

## <a name="see-also"></a><span data-ttu-id="441a6-111">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="441a6-111">See Also</span></span>

[<span data-ttu-id="441a6-112">Windows PowerShell Programcı Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="441a6-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="441a6-113">Windows PowerShell SDK'sı</span><span class="sxs-lookup"><span data-stu-id="441a6-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)