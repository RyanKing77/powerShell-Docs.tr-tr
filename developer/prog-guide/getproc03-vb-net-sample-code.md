---
title: GetProc03 (VB.NET) örnek kodu | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff94c452-d4ec-4492-ac20-61ad52f8ae8c
caps.latest.revision: 7
ms.openlocfilehash: da85155c43471150a7b35ac37c1dce0790277084
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845860"
---
# <a name="getproc03-vbnet-sample-code"></a><span data-ttu-id="68636-102">GetProc03 (VB.NET) Örnek Kod</span><span class="sxs-lookup"><span data-stu-id="68636-102">GetProc03 (VB.NET) Sample Code</span></span>

<span data-ttu-id="68636-103">Aşağıdaki kod uygulamasını gösterir. bir `Get-Process` kabul edebilen cmdlet'inin ardışık düzendeki girişi.</span><span class="sxs-lookup"><span data-stu-id="68636-103">The following code shows the implementation of a `Get-Process` cmdlet that can accept pipelined input.</span></span> <span data-ttu-id="68636-104">Bu uygulama tanımlayan bir `Name` ardışık giriş kabul eden bir parametre ve yerel bilgisayardan sağlanan adlarına göre işlem bilgilerini alır ve ardından kullanır [System.Management.Automation.Cmdlet.Writeobject% 28System.Object%2Csystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) nesneler gönderiliyor işlem hattının çıktı mekanizması olarak yöntemi.</span><span class="sxs-lookup"><span data-stu-id="68636-104">This implementation defines a `Name` parameter that accepts pipeline input, retrieves process information from the local computer based on the supplied names, and then uses the [System.Management.Automation.Cmdlet.Writeobject%28System.Object%2Csystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) method as the output mechanism for sending objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="68636-105">Kod örneği</span><span class="sxs-lookup"><span data-stu-id="68636-105">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#getproc03vbAll](Msh_samplesgetproc03#getproc03vbAll)]  -->