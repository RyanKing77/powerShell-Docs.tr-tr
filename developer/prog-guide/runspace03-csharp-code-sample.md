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
ms.openlocfilehash: e1fc91174a959d6acc306330afb8d5c2e7a9a860
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734993"
---
# <a name="runspace03-c-code-sample"></a><span data-ttu-id="fcdb0-102">RunSpace03 (C#) Kod Örneği</span><span class="sxs-lookup"><span data-stu-id="fcdb0-102">RunSpace03 (C#) Code Sample</span></span>

<span data-ttu-id="fcdb0-103">İşte C# kaynak kodu açıklanan konsol uygulamasının [konsol uygulaması, çalıştırmalar belirtilen kod oluşturma](fd).</span><span class="sxs-lookup"><span data-stu-id="fcdb0-103">Here is the C# source code for the console application described in [Creating a Console Application That Runs a Specified Script](fd).</span></span> <span data-ttu-id="fcdb0-104">Bu örnekte [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) betiğe geçirilen işlem adları listesini kullanarak bilgileri alır işleyen bir betik yürütmek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="fcdb0-104">This sample uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute a script that retrieves process information by using the list of process names passed into the script.</span></span> <span data-ttu-id="fcdb0-105">Bu giriş nesneleri bir betiğe geçirmek nasıl ve çıkış nesnelerini yanı sıra hata nesneleri almayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="fcdb0-105">It shows how to pass input objects to a script and how to retrieve error objects as well as the output objects.</span></span>

> [!NOTE]
> <span data-ttu-id="fcdb0-106">İndirebileceğiniz C# Microsoft .NET Framework 3.0 çalışma zamanı bileşenleri ve Microsoft Windows Yazılım Geliştirme Seti için Windows Vista'yı kullanarak bu örnek için kaynak dosyası (runspace03.cs).</span><span class="sxs-lookup"><span data-stu-id="fcdb0-106">You can download the C# source file (runspace03.cs) for this sample using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="fcdb0-107">Yükleme yönergeleri için bkz: [Windows PowerShell yükleme ve indirme Windows PowerShell SDK'sı](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="fcdb0-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="fcdb0-108">İndirilen kaynak dosyaları kullanılabilir  **\<PowerShell örnekleri >** dizin.</span><span class="sxs-lookup"><span data-stu-id="fcdb0-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="fcdb0-109">Kod örneği</span><span class="sxs-lookup"><span data-stu-id="fcdb0-109">Code Sample</span></span>

[!code-csharp[Runspace03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace03/Runspace03.cs#L11-L88 "Runspace03.cs")]

## <a name="see-also"></a><span data-ttu-id="fcdb0-110">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="fcdb0-110">See Also</span></span>

[<span data-ttu-id="fcdb0-111">Windows PowerShell Programcı Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="fcdb0-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="fcdb0-112">Windows PowerShell SDK'sı</span><span class="sxs-lookup"><span data-stu-id="fcdb0-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)