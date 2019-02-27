---
title: GetProc02 (C#) örnek kodu | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e4e1eee3-316b-43a4-8a60-313391619be6
caps.latest.revision: 6
ms.openlocfilehash: 740e8d60b71654b82020d16b2964165f3ee1e600
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851229"
---
# <a name="getproc02-c-sample-code"></a><span data-ttu-id="0ef4f-102">GetProc02 (C#) Örnek Kod</span><span class="sxs-lookup"><span data-stu-id="0ef4f-102">GetProc02 (C#) Sample Code</span></span>

<span data-ttu-id="0ef4f-103">Aşağıdaki kod uygulamasını gösterir. bir `Get-Process` komut satırı girişi kabul eden cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="0ef4f-103">The following code shows the implementation of a `Get-Process` cmdlet that accepts command-line input.</span></span> <span data-ttu-id="0ef4f-104">Bu uygulama tanımlar dikkat edin bir `Name` parametresi komut satırı girişi ve izin vermek için kullandığı [System.Management.Automation.Cmdlet.Writeobject%28System.Object%2Csystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) çıkışın gösterdiği gibi yöntemi mekanizması, çıkış göndermek için işlem hattına nesneleri.</span><span class="sxs-lookup"><span data-stu-id="0ef4f-104">Notice that this implementation defines a `Name` parameter to allow command-line input, and it uses the [System.Management.Automation.Cmdlet.Writeobject%28System.Object%2Csystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) method as the output mechanism for sending output objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="0ef4f-105">Kod örneği</span><span class="sxs-lookup"><span data-stu-id="0ef4f-105">Code Sample</span></span>

[!code-csharp[GetProcessSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample02/GetProcessSample02.cs#L11-L76 "GetProcessSample02.cs")]

## <a name="see-also"></a><span data-ttu-id="0ef4f-106">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="0ef4f-106">See Also</span></span>

[<span data-ttu-id="0ef4f-107">Windows PowerShell SDK'sı</span><span class="sxs-lookup"><span data-stu-id="0ef4f-107">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)