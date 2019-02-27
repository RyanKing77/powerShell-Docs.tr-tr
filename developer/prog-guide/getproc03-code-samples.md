---
title: GetProc03 kod örnekleri | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ad39c7d-2f64-49d1-9be0-d2295e4302b3
caps.latest.revision: 5
ms.openlocfilehash: 8cb02b9f2510b90f405651deaf551e9622f5a298
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847729"
---
# <a name="getproc03-code-samples"></a><span data-ttu-id="6316d-102">GetProc03 Kod Örnekleri</span><span class="sxs-lookup"><span data-stu-id="6316d-102">GetProc03 Code Samples</span></span>

<span data-ttu-id="6316d-103">GetProc03 örnek cmdlet için kod örnekleri aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6316d-103">Here are the code samples for the GetProc03 sample cmdlet.</span></span> <span data-ttu-id="6316d-104">Bu `Get-Process` cmdlet örnek açıklanan [söz konusu işlem ardışık düzen giriş parametreleri ekleme](../cmdlet/adding-parameters-that-process-pipeline-input.md).</span><span class="sxs-lookup"><span data-stu-id="6316d-104">This is the `Get-Process` cmdlet sample described in [Adding Parameters that Process Pipeline Input](../cmdlet/adding-parameters-that-process-pipeline-input.md).</span></span> <span data-ttu-id="6316d-105">Bu `Get-Process` cmdlet'i kullanan bir `Name` kabul eden bir işlem hattı nesnesinden giriş parametresi ve yerel bilgisayardan sağlanan adlarına göre işlem bilgilerini alır ve sonra komut satırında işlemleri hakkındaki bilgileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="6316d-105">This `Get-Process` cmdlet uses a `Name` parameter that accepts input from a pipeline object, retrieves process information from the local computer based on the supplied names, and then displays information about the processes at the command line.</span></span>

> [!NOTE]
> <span data-ttu-id="6316d-106">İndirebileceğiniz C# .NET Framework 3.0 çalışma zamanı bileşenleri ve Microsoft Windows Yazılım Geliştirme Seti için Windows Vista'yı kullanarak bu Get-Proc cmdlet için kaynak dosyası (getprov03.cs).</span><span class="sxs-lookup"><span data-stu-id="6316d-106">You can download the C# source file (getprov03.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="6316d-107">Yükleme yönergeleri için bkz: [Windows PowerShell yükleme ve indirme Windows PowerShell SDK'sı](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="6316d-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="6316d-108">İndirebileceğiniz C# .NET Framework 3.0 çalışma zamanı bileşenleri ve Microsoft Windows Yazılım Geliştirme Seti için Windows Vista'yı kullanarak bu Get-Proc cmdlet için kaynak dosyası (getprov03.cs).</span><span class="sxs-lookup"><span data-stu-id="6316d-108">You can download the C# source file (getprov03.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="6316d-109">Yükleme yönergeleri için bkz: [Windows PowerShell yükleme ve indirme Windows PowerShell SDK'sı](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="6316d-109">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="6316d-110">İndirilen kaynak dosyaları kullanılabilir  **\<PowerShell örnekleri >** dizin.</span><span class="sxs-lookup"><span data-stu-id="6316d-110">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

<span data-ttu-id="6316d-111">Tam örnek kod için aşağıdaki konulara bakın.</span><span class="sxs-lookup"><span data-stu-id="6316d-111">For complete sample code, see the following topics.</span></span>

|<span data-ttu-id="6316d-112">Dil</span><span class="sxs-lookup"><span data-stu-id="6316d-112">Language</span></span>|<span data-ttu-id="6316d-113">Konu</span><span class="sxs-lookup"><span data-stu-id="6316d-113">Topic</span></span>|
|--------------|-----------|
|<span data-ttu-id="6316d-114">C#</span><span class="sxs-lookup"><span data-stu-id="6316d-114">C#</span></span>|[<span data-ttu-id="6316d-115">GetProc03 (C#) örnek kod</span><span class="sxs-lookup"><span data-stu-id="6316d-115">GetProc03 (C#) Sample Code</span></span>](./getproc03-csharp-sample-code.md)|
|<span data-ttu-id="6316d-116">VB.NET</span><span class="sxs-lookup"><span data-stu-id="6316d-116">VB.NET</span></span>|[<span data-ttu-id="6316d-117">GetProc03 (VB.NET) örnek kod</span><span class="sxs-lookup"><span data-stu-id="6316d-117">GetProc03 (VB.NET) Sample Code</span></span>](./getproc03-vb-net-sample-code.md)|

## <a name="see-also"></a><span data-ttu-id="6316d-118">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="6316d-118">See Also</span></span>

[<span data-ttu-id="6316d-119">Windows PowerShell Programcı Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="6316d-119">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="6316d-120">Windows PowerShell SDK'sı</span><span class="sxs-lookup"><span data-stu-id="6316d-120">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)