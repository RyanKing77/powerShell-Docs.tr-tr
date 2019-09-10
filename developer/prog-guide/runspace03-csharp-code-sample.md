---
title: RunSpace03 (C#) kod örneği | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9ac8ab99-1856-4d6f-b30d-c0a18b8dd1fc
caps.latest.revision: 6
ms.openlocfilehash: 9afdb97b8ae2919f091ca5bacccedbe37c2e1584
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848034"
---
# <a name="runspace03-c-code-sample"></a><span data-ttu-id="ab036-102">RunSpace03 (C#) Kod Örneği</span><span class="sxs-lookup"><span data-stu-id="ab036-102">RunSpace03 (C#) Code Sample</span></span>

<span data-ttu-id="ab036-103">"Belirli bir C# betiği çalıştıran bir konsol uygulaması oluşturma" bölümünde açıklanan konsol uygulaması için kaynak kodu aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ab036-103">Here is the C# source code for the console application described in "Creating a Console Application That Runs a Specified Script".</span></span> <span data-ttu-id="ab036-104">Bu örnek, komut dosyasına geçirilen işlem adlarının listesini kullanarak işlem bilgilerini alan bir betiği yürütmek için [System. Management. Automation. Runspaceınvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) sınıfını kullanır.</span><span class="sxs-lookup"><span data-stu-id="ab036-104">This sample uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute a script that retrieves process information by using the list of process names passed into the script.</span></span> <span data-ttu-id="ab036-105">Giriş nesnelerinin bir betiğe nasıl geçirileceğini ve hata nesnelerinin yanı sıra çıkış nesnelerinin nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ab036-105">It shows how to pass input objects to a script and how to retrieve error objects as well as the output objects.</span></span>

> [!NOTE]
> <span data-ttu-id="ab036-106">Windows Vista için Microsoft C# Windows yazılım geliştirme seti ve Microsoft .NET Framework 3,0 çalışma zamanı bileşenleri kullanarak bu örnek için kaynak dosyasını (runspace03.cs) indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ab036-106">You can download the C# source file (runspace03.cs) for this sample using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="ab036-107">İndirme yönergeleri için bkz. [Windows PowerShell 'ı yükleme ve Windows PowerShell SDK 'Sını indirme](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="ab036-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="ab036-108">İndirilen kaynak dosyaları,  **\<PowerShell örnekleri >** dizininde bulunur.</span><span class="sxs-lookup"><span data-stu-id="ab036-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="ab036-109">Kod örneği</span><span class="sxs-lookup"><span data-stu-id="ab036-109">Code Sample</span></span>

[!code-csharp[Runspace03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace03/Runspace03.cs#L11-L88 "Runspace03.cs")]

## <a name="see-also"></a><span data-ttu-id="ab036-110">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="ab036-110">See Also</span></span>

[<span data-ttu-id="ab036-111">Windows PowerShell Programcı Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ab036-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="ab036-112">Windows PowerShell SDK 'Sı</span><span class="sxs-lookup"><span data-stu-id="ab036-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)