---
title: Örnek kod RunSpace10 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5337dc40-c56e-458b-aedc-5f5d401dfd28
caps.latest.revision: 6
ms.openlocfilehash: 77c0675b45bf4ff6f8c6a85ff9a090c13c199c6d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081249"
---
# <a name="runspace10-code-sample"></a><span data-ttu-id="0ab6a-102">RunSpace10 Kod Örneği</span><span class="sxs-lookup"><span data-stu-id="0ab6a-102">RunSpace10 Code Sample</span></span>

<span data-ttu-id="0ab6a-103">Kaynak kodu Runspace10 örneği aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="0ab6a-103">Here is the source code for the Runspace10 sample.</span></span> <span data-ttu-id="0ab6a-104">Bu örnek uygulama bir cmdlet'e ekler [System.Management.Automation.Runspaces.Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) ve sonra çalışma alanı oluşturmak için değiştirilmiş yapılandırma bilgilerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="0ab6a-104">This sample application adds a cmdlet to [System.Management.Automation.Runspaces.Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) and then uses the modified configuration information to create the runspace.</span></span>

> [!NOTE]
> <span data-ttu-id="0ab6a-105">İndirebileceğiniz C# Windows Vista için Windows Yazılım Geliştirme Seti ve Microsoft .NET Framework 3.0 çalışma zamanı bileşenlerini kullanarak kaynak dosyası (runspace10.cs).</span><span class="sxs-lookup"><span data-stu-id="0ab6a-105">You can download the C# source file (runspace10.cs) by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="0ab6a-106">Yükleme yönergeleri için bkz: [Windows PowerShell yükleme ve indirme Windows PowerShell SDK'sı](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="0ab6a-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="0ab6a-107">İndirilen kaynak dosyaları kullanılabilir  **\<PowerShell örnekleri >** dizin.</span><span class="sxs-lookup"><span data-stu-id="0ab6a-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="0ab6a-108">Kod örneği</span><span class="sxs-lookup"><span data-stu-id="0ab6a-108">Code Sample</span></span>

[!code-csharp[Runspace10.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace10/Runspace10.cs#L11-L118 "Runspace10.cs")]

## <a name="see-also"></a><span data-ttu-id="0ab6a-109">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="0ab6a-109">See Also</span></span>

[<span data-ttu-id="0ab6a-110">Windows PowerShell Programcı Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0ab6a-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="0ab6a-111">Windows PowerShell SDK'sı</span><span class="sxs-lookup"><span data-stu-id="0ab6a-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)