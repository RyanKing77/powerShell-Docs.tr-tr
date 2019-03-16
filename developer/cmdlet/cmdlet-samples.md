---
title: Cmdlet örnekleri | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b99d53fc-0af9-426b-82ce-09955e031d4b
caps.latest.revision: 13
ms.openlocfilehash: 0fa4a5f804586c51ae6a36121f9aab041b0989cc
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058054"
---
# <a name="cmdlet-samples"></a><span data-ttu-id="59f61-102">Cmdlet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="59f61-102">Cmdlet Samples</span></span>

<span data-ttu-id="59f61-103">Bu bölümde Windows PowerShell 2.0 SDK'sını sağlanan örnek kod açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="59f61-103">This section describes sample code that is provided in the Windows PowerShell 2.0 SDK.</span></span> <span data-ttu-id="59f61-104">Bu bölümdeki konular, kodu kopyalayın veya SDK'sı ile yüklü kaynak dosyalarını açın.</span><span class="sxs-lookup"><span data-stu-id="59f61-104">You can copy code from the topics in this section, or open the source files installed with the SDK.</span></span> <span data-ttu-id="59f61-105">[Windows PowerShell 2.0 Yazılım Geliştirme Seti (SDK)](https://www.microsoft.com/en-us/download/details.aspx?id=2560) Benioku dosyaları, kaynak dosyaları ve her örnek için Visual Studio proje dosyaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="59f61-105">The [Windows PowerShell 2.0 Software Development Kit (SDK)](https://www.microsoft.com/en-us/download/details.aspx?id=2560) provides ReadMe files, source files, and Visual Studio project files for each sample.</span></span> <span data-ttu-id="59f61-106">SDK yüklenmiş altındaki örneklere bulabilirsiniz `<Drive>:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\` klasör.</span><span class="sxs-lookup"><span data-stu-id="59f61-106">With the SDK installed, you can find the samples under the `<Drive>:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\` folder.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="59f61-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="59f61-107">In This Section</span></span>

<span data-ttu-id="59f61-108">[GetProcessSample01 örnek](./getprocesssample01-sample.md) Bu örnek, yerel bilgisayardaki işlemleri alır bir cmdlet yazma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="59f61-108">[GetProcessSample01 Sample](./getprocesssample01-sample.md) This sample shows how to write a cmdlet that retrieves the processes on the local computer.</span></span>

<span data-ttu-id="59f61-109">[GetProcessSample02 örnek](./getprocesssample02-sample.md) Bu örnek, yerel bilgisayardaki işlemleri alır bir cmdlet yazma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="59f61-109">[GetProcessSample02 Sample](./getprocesssample02-sample.md) This sample shows how to write a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="59f61-110">Bunu, alınacak işlemleri belirtmek için kullanılan bir Name parametresi sağlar.</span><span class="sxs-lookup"><span data-stu-id="59f61-110">It provides a Name parameter that can be used to specify the processes to be retrieved.</span></span>

<span data-ttu-id="59f61-111">[GetProcessSample03 örnek](./getprocesssample03-sample.md) Bu örnek, yerel bilgisayardaki işlemleri alır bir cmdlet yazma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="59f61-111">[GetProcessSample03 Sample](./getprocesssample03-sample.md) This sample shows how to write a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="59f61-112">Bu işlem hattı bir nesneden ya da parametre adı ile aynı özellik adı olan bir nesnenin bir özelliğine bir değer alabilen bir Name parametresi sağlar.</span><span class="sxs-lookup"><span data-stu-id="59f61-112">It provides a Name parameter that can accept an object from the pipeline or a value from a property of an object whose property name is the same as the parameter name.</span></span>

<span data-ttu-id="59f61-113">[GetProcessSample04 örnek](./getprocesssample04-sample.md) Bu örnek, yerel bilgisayardaki işlemleri alır bir cmdlet yazma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="59f61-113">[GetProcessSample04 Sample](./getprocesssample04-sample.md) This sample shows how to write a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="59f61-114">Bir işlem alınırken bir hata oluşması halinde olmak üzere sonlandırmasız bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="59f61-114">It generates a nonterminating error if an error occurs while retrieving a process.</span></span>

<span data-ttu-id="59f61-115">[GetProcessSample05 örnek](./getprocesssample05-sample.md) Bu örnek cmdlet Get-Proc tam bir sürümünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="59f61-115">[GetProcessSample05 Sample](./getprocesssample05-sample.md) This sample shows a complete version of the Get-Proc cmdlet.</span></span>

<span data-ttu-id="59f61-116">[StopProcessSample01 örnek](./stopprocesssample01-sample.md) Bu örnek, bir işlemi durdurmak çalışmadan önce kullanıcıdan geri bildirim istekleri bir cmdlet yazma ve nasıl uygulanacağını gösterir. bir `PassThru` kullanıcı döndürmek için cmdlet istediğini gösterir parametresi bir nesne.</span><span class="sxs-lookup"><span data-stu-id="59f61-116">[StopProcessSample01 Sample](./stopprocesssample01-sample.md) This sample shows how to write a cmdlet that requests feedback from the user before it attempts to stop a process, and how to implement a `PassThru` parameter that indicates that the user wants the cmdlet to return an object.</span></span>

<span data-ttu-id="59f61-117">[StopProcessSample02 örnek](./stopprocesssample02-sample.md) Bu örnek, yerel bilgisayarda işlem durdurulurken hata ayıklama, ayrıntılı ve uyarı iletilerini yazan bir cmdlet yazma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="59f61-117">[StopProcessSample02 Sample](./stopprocesssample02-sample.md) This sample shows how to write a cmdlet that writes debug, verbose, and warning messages while stopping processes on the local computer.</span></span>

<span data-ttu-id="59f61-118">[StopProcessSample03 örnek](./stopprocesssample03-sample.md) Bu örnek, bir cmdlet parametreleri, diğer adlar ve, olan yazma işlemi gösterilmektedir joker karakterleri destekler.</span><span class="sxs-lookup"><span data-stu-id="59f61-118">[StopProcessSample03 Sample](./stopprocesssample03-sample.md) This sample shows how to write a cmdlet whose parameters have aliases and that support wildcard characters.</span></span>

<span data-ttu-id="59f61-119">[StopProcessSample04 örnek](./stopprocesssample04-sample.md) Bu örnek, bir cmdlet parametre kümeleri bildirir, varsayılan parametre ayarlama ve Giriş bir nesneyi kabul edebildiğini belirtir yazma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="59f61-119">[StopProcessSample04 Sample](./stopprocesssample04-sample.md) This sample shows how to write a cmdlet that declares parameter sets, specifies the default parameter set, and can accept an input object.</span></span>

<span data-ttu-id="59f61-120">[Events01 örnek](./events01-sample.md) Bu örnek, kaydetmek kullanıcı tarafından harekete geçirilen olayları sağlayan bir cmdlet oluşturma işlemi gösterilmektedir [System.IO.Filesystemwatcher](/dotnet/api/System.IO.FileSystemWatcher).</span><span class="sxs-lookup"><span data-stu-id="59f61-120">[Events01 Sample](./events01-sample.md) This sample shows how to create a cmdlet that allows the user to register for events raised by [System.IO.Filesystemwatcher](/dotnet/api/System.IO.FileSystemWatcher).</span></span> <span data-ttu-id="59f61-121">Bu cmdlet ile kullanıcıları Örneğin, belirli bir dizini altında bir dosya oluşturulduğunda yürütülecek bir eylem kaydedebilir.</span><span class="sxs-lookup"><span data-stu-id="59f61-121">With this cmdlet users can, for example, register an action to execute when a file is created under a specific directory.</span></span> <span data-ttu-id="59f61-122">Bu örnek türetildiği [Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) temel sınıfı.</span><span class="sxs-lookup"><span data-stu-id="59f61-122">This sample derives from the [Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) base class.</span></span>

## <a name="see-also"></a><span data-ttu-id="59f61-123">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="59f61-123">See Also</span></span>

[<span data-ttu-id="59f61-124">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="59f61-124">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
