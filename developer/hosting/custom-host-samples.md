---
title: Özel ana bilgisayar örnekleri | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55aee25b-bbcb-4d41-a4c0-fb8e30c4cdc1
caps.latest.revision: 11
ms.openlocfilehash: 1e58b74cf1c37c70ebfb0f4970cfbf8a8263ec5c
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794153"
---
# <a name="custom-host-samples"></a><span data-ttu-id="5c52f-102">Özel Konak Örnekleri</span><span class="sxs-lookup"><span data-stu-id="5c52f-102">Custom Host Samples</span></span>

<span data-ttu-id="5c52f-103">Bu bölüm, özel bir ana bilgisayar yazmak için örnek kod içerir.</span><span class="sxs-lookup"><span data-stu-id="5c52f-103">This section includes sample code for writing a custom host.</span></span> <span data-ttu-id="5c52f-104">Microsoft Visual Studio, bir konsol uygulaması oluşturun ve ardından kodu bu bölümdeki konular ana uygulamanıza kopyalamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5c52f-104">You can use Microsoft Visual Studio to create a console application and then copy the code from the topics in this section into your host application.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="5c52f-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="5c52f-105">In This Section</span></span>

 <span data-ttu-id="5c52f-106">[Host01 örnek](./host01-sample.md) Bu örnek, temel özel bir ana bilgisayar kullanan bir konak uygulamanın nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5c52f-106">[Host01 Sample](./host01-sample.md) This sample shows how to implement a host application that uses a basic custom host.</span></span>

 <span data-ttu-id="5c52f-107">[Host02 örnek](./host02-sample.md) Bu örnek, bir özel ana bilgisayar uygulaması ile birlikte Windows PowerShell'i çalışma zamanı kullanan bir ana bilgisayar uygulaması yazma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5c52f-107">[Host02 Sample](./host02-sample.md) This sample shows how to write a host application that uses the Windows PowerShell runtime along with a custom host implementation.</span></span> <span data-ttu-id="5c52f-108">Ana bilgisayar uygulaması çalışır Almanca için konak kültürü ayarlar [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet ve görüntüler sonuçları aynı görmek bunları pwrsh.exe ve geçerli veri ve saat sonra yazdırır Almanca kullanarak.</span><span class="sxs-lookup"><span data-stu-id="5c52f-108">The host application sets the host culture to German, runs the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet and displays the results as you would see them using pwrsh.exe, and then prints out the current data and time in German.</span></span>

 <span data-ttu-id="5c52f-109">[Host03 örnek](./host03-sample.md) Bu örnek komut satırından komutları okur, komutları yürütür ve sonuçları konsola görüntüler etkileşimli konsol tabanlı konak uygulamanın nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5c52f-109">[Host03 Sample](./host03-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>

 <span data-ttu-id="5c52f-110">[Host04 örnek](./host04-sample.md) Bu örnek komut satırından komutları okur, komutları yürütür ve sonuçları konsola görüntüler etkileşimli konsol tabanlı konak uygulamanın nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5c52f-110">[Host04 Sample](./host04-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span> <span data-ttu-id="5c52f-111">Bu ana bilgisayar uygulaması birden çok seçenek belirtmesini sağlayan görüntüleme yönergeleri de destekler.</span><span class="sxs-lookup"><span data-stu-id="5c52f-111">This host application also supports displaying prompts that allow the user to specify multiple choices.</span></span>

 <span data-ttu-id="5c52f-112">[Konak05 örnek](./host05-sample.md) Bu örnek komut satırından komutları okur, komutları yürütür ve sonuçları konsola görüntüler etkileşimli konsol tabanlı konak uygulamanın nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5c52f-112">[Host05 Sample](./host05-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span> <span data-ttu-id="5c52f-113">Ayrıca bu ana bilgisayar uygulaması kullanarak uzak bilgisayarlara çağrıları destekleyen [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) ve [çıkış-PsSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) cmdlet'leri</span><span class="sxs-lookup"><span data-stu-id="5c52f-113">This host application also supports calls to remote computers by using the [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) and [Exit-PsSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) cmdlets</span></span>

 <span data-ttu-id="5c52f-114">[Host06 örnek](./host06-sample.md) Bu örnek komut satırından komutları okur, komutları yürütür ve sonuçları konsola görüntüler etkileşimli konsol tabanlı konak uygulamanın nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5c52f-114">[Host06 Sample](./host06-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span> <span data-ttu-id="5c52f-115">Ayrıca, bu örnek, kullanıcı tarafından girilen metin rengi belirtmek için belirteç Oluşturucu API kullanır.</span><span class="sxs-lookup"><span data-stu-id="5c52f-115">In addition, this sample uses the Tokenizer APIs to specify the color of the text that is entered by the user.</span></span>

## <a name="see-also"></a><span data-ttu-id="5c52f-116">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="5c52f-116">See Also</span></span>
