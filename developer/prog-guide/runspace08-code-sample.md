---
title: Örnek kod RunSpace08 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f286201-8a02-4b00-9a2c-1b833ccdbdbf
caps.latest.revision: 7
ms.openlocfilehash: 1a09cfee3bb317de6c1ca4dde86a87d72a498e6e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848639"
---
# <a name="runspace08-code-sample"></a><span data-ttu-id="8c80e-102">RunSpace08 Kod Örneği</span><span class="sxs-lookup"><span data-stu-id="8c80e-102">RunSpace08 Code Sample</span></span>

<span data-ttu-id="8c80e-103">İşte kaynak kodunu Runspace08 örnek bölümünde açıklanan yönelik [bir konsol uygulaması, ekler parametreleri için bir komut oluşturma](http://msdn.microsoft.com/en-us/848b2b46-60f1-4a86-b448-cfc7c0cccfba).</span><span class="sxs-lookup"><span data-stu-id="8c80e-103">Here is the source code for the Runspace08 sample described in [Creating a Console Application That Adds Parameters to a Command](http://msdn.microsoft.com/en-us/848b2b46-60f1-4a86-b448-cfc7c0cccfba).</span></span> <span data-ttu-id="8c80e-104">Bu örnek uygulama bir çalışma alanı oluşturur, bir işlem hattı oluşturur, ardışık iki komut ekler, iki parametre ikinci komuta ekler ve sonra işlem hattını yürütür.</span><span class="sxs-lookup"><span data-stu-id="8c80e-104">This sample application creates a runspace, creates a pipeline, adds two commands to the pipeline, adds two parameters to the second command, and then executes the pipeline.</span></span> <span data-ttu-id="8c80e-105">Ardışık düzenine eklenen komutlar `Get-Process` ve `Sort-Object` cmdlet'leri.</span><span class="sxs-lookup"><span data-stu-id="8c80e-105">The commands that are added to the pipeline are the `Get-Process` and `Sort-Object` cmdlets.</span></span>

## <a name="code-sample"></a><span data-ttu-id="8c80e-106">Kod örneği</span><span class="sxs-lookup"><span data-stu-id="8c80e-106">Code Sample</span></span>

[!code-csharp[Runspace08.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace08/Runspace08.cs#L11-L86 "Runspace08.cs")]

## <a name="see-also"></a><span data-ttu-id="8c80e-107">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="8c80e-107">See Also</span></span>

[<span data-ttu-id="8c80e-108">Windows PowerShell SDK'sı</span><span class="sxs-lookup"><span data-stu-id="8c80e-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)