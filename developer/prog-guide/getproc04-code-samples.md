---
title: GetProc04 kod örnekleri | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c00afd46-758a-4aec-b865-2c9d8f6a17ad
caps.latest.revision: 5
ms.openlocfilehash: 67081528ebe14fbb082091c1b9500de82069b48f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081674"
---
# <a name="getproc04-code-samples"></a><span data-ttu-id="93511-102">GetProc04 Kod Örnekleri</span><span class="sxs-lookup"><span data-stu-id="93511-102">GetProc04 Code Samples</span></span>

<span data-ttu-id="93511-103">GetProc04 örnek cmdlet için kod örnekleri aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="93511-103">Here are the code samples for the GetProc04 sample cmdlet.</span></span> <span data-ttu-id="93511-104">Bu `Get-Process` cmdlet örnek açıklanan [bilgisayarınızı cmdlet'e olmak üzere Sonlandırmasız hata raporlama ekleme](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).</span><span class="sxs-lookup"><span data-stu-id="93511-104">This is the `Get-Process` cmdlet sample described in [Adding Nonterminating Error Reporting to Your Cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).</span></span> <span data-ttu-id="93511-105">Bu `Get-Process` cmdlet'i çağrıları [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) işlem bilgileri alınırken bir geçersiz işlem özel durum olduğunda yöntemi.</span><span class="sxs-lookup"><span data-stu-id="93511-105">This `Get-Process` cmdlet calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method whenever an invalid operation exception is thrown while retrieving process information.</span></span>

> [!NOTE]
> <span data-ttu-id="93511-106">İndirebileceğiniz C# .NET Framework 3.0 çalışma zamanı bileşenleri ve Microsoft Windows Yazılım Geliştirme Seti için Windows Vista'yı kullanarak bu Get-Proc cmdlet için kaynak dosyası (getprov04.cs).</span><span class="sxs-lookup"><span data-stu-id="93511-106">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="93511-107">Yükleme yönergeleri için bkz: [Windows PowerShell yükleme ve indirme Windows PowerShell SDK'sı](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="93511-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="93511-108">İndirilen kaynak dosyaları kullanılabilir  **\<PowerShell örnekleri >** dizin.</span><span class="sxs-lookup"><span data-stu-id="93511-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

<span data-ttu-id="93511-109">Tam örnek kod için aşağıdaki konulara bakın.</span><span class="sxs-lookup"><span data-stu-id="93511-109">For complete sample code, see the following topics.</span></span>

|<span data-ttu-id="93511-110">Dil</span><span class="sxs-lookup"><span data-stu-id="93511-110">Language</span></span>|<span data-ttu-id="93511-111">Konu</span><span class="sxs-lookup"><span data-stu-id="93511-111">Topic</span></span>|
|--------------|-----------|
|<span data-ttu-id="93511-112">C#</span><span class="sxs-lookup"><span data-stu-id="93511-112">C#</span></span>|[<span data-ttu-id="93511-113">GetProc04 (C#) örnek kod</span><span class="sxs-lookup"><span data-stu-id="93511-113">GetProc04 (C#) Sample Code</span></span>](./getproc04-csharp-sample-code.md)|
|<span data-ttu-id="93511-114">VB.NET</span><span class="sxs-lookup"><span data-stu-id="93511-114">VB.NET</span></span>|[<span data-ttu-id="93511-115">GetProc04 (VB.NET) örnek kod</span><span class="sxs-lookup"><span data-stu-id="93511-115">GetProc04 (VB.NET) Sample Code</span></span>](./getproc04-vb-net-sample-code.md)|

## <a name="see-also"></a><span data-ttu-id="93511-116">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="93511-116">See Also</span></span>

[<span data-ttu-id="93511-117">Windows PowerShell Programcı Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="93511-117">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="93511-118">Windows PowerShell SDK'sı</span><span class="sxs-lookup"><span data-stu-id="93511-118">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)