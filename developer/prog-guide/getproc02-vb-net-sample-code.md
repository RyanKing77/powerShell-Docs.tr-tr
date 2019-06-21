---
title: GetProc02 (VB.NET) örnek kodu | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f3497546-5b3a-4e29-84ba-cd9747be64b3
caps.latest.revision: 6
ms.openlocfilehash: 4ec63ed32bd2906f5b027523aa0f253b51a5d873
ms.sourcegitcommit: f60fa420bdc81db174e6168d3aeb11371e483162
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/20/2019
ms.locfileid: "67301344"
---
# <a name="getproc02-vbnet-sample-code"></a><span data-ttu-id="2884e-102">GetProc02 (VB.NET) Örnek Kod</span><span class="sxs-lookup"><span data-stu-id="2884e-102">GetProc02 (VB.NET) Sample Code</span></span>

<span data-ttu-id="2884e-103">Aşağıdaki kod uygulamasını gösterir. bir `Get-Process` komut satırı girişi kabul eden cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="2884e-103">The following code shows the implementation of a `Get-Process` cmdlet that accepts command-line input.</span></span> <span data-ttu-id="2884e-104">Bu uygulama tanımlar dikkat edin bir `Name` parametresi komut satırı girişi ve izin vermek için kullandığı [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) yöntemi, çıkış göndermek için çıkış mekanizması olarak nesneleri için işlem hattı.</span><span class="sxs-lookup"><span data-stu-id="2884e-104">Notice that this implementation defines a `Name` parameter to allow command-line input, and it uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending output objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="2884e-105">Kod örneği</span><span class="sxs-lookup"><span data-stu-id="2884e-105">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc02#getproc02vball](Msh_samplesgetproc02#getproc02vball)]  -->

## <a name="see-also"></a><span data-ttu-id="2884e-106">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="2884e-106">See Also</span></span>

[<span data-ttu-id="2884e-107">Windows PowerShell SDK'sı</span><span class="sxs-lookup"><span data-stu-id="2884e-107">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
