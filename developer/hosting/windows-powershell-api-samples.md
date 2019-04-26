---
title: Windows PowerShell API örnekleri | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82df2cde-ba12-46d2-b6ec-da5455fd9b57
caps.latest.revision: 8
ms.openlocfilehash: a472f07cb24b0de8e5dcdfcaddd2802575318d7a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082592"
---
# <a name="windows-powershell-api-samples"></a><span data-ttu-id="b41b5-102">Windows PowerShell API’si Örnekleri</span><span class="sxs-lookup"><span data-stu-id="b41b5-102">Windows PowerShell API Samples</span></span>

<span data-ttu-id="b41b5-103">Bu bölüm, işlevselliği kısıtlayabilir çalışma alanları oluşturma ve zaman uyumsuz olarak çalışma alanları sağlamak için bir çalışma alanı havuzu kullanarak komutları çalıştırma gösteren örnek kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="b41b5-103">This section includes sample code that shows how to create runspaces that restrict functionality, and how to asynchronously run commands by using a runspace pool to supply the runspaces.</span></span> <span data-ttu-id="b41b5-104">Microsoft Visual Studio, bir konsol uygulaması oluşturun ve ardından kodu bu bölümdeki konular ana uygulamanıza kopyalamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b41b5-104">You can use Microsoft Visual Studio to create a console application and then copy the code from the topics in this section into your host application.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="b41b5-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="b41b5-105">In This Section</span></span>

<span data-ttu-id="b41b5-106">[PowerShell01 örnek](./windows-powershell01-sample.md) Bu örnek nasıl kullanılacağını gösterir. bir [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) işlevselliğinin bir çalışma alanı sınırlamak için nesne.</span><span class="sxs-lookup"><span data-stu-id="b41b5-106">[PowerShell01 Sample](./windows-powershell01-sample.md) This sample shows how to use an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object to limit the functionality of a runspace.</span></span> <span data-ttu-id="b41b5-107">Bu örnek çıktısı çalışma, bir cmdlet'in özel olarak işaretlemek nasıl, ekleme ve kaldırma cmdlet'leri ve sağlayıcıları, dil modunu kısıtlamak nasıl gösterir ve bir ara sunucu komutu ekleme.</span><span class="sxs-lookup"><span data-stu-id="b41b5-107">The output of this sample demonstrates how to restrict the language mode of the runspace, how to mark a cmdlet as private, how to add and remove cmdlets and providers, how to add a proxy command, and more.</span></span>

<span data-ttu-id="b41b5-108">[PowerShell02 örnek](./windows-powershell02-sample.md) Bu örnek, bir çalışma alanı havuzunun çalışma alanlarını kullanarak zaman uyumsuz olarak komutlarını çalıştırmak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b41b5-108">[PowerShell02 Sample](./windows-powershell02-sample.md) This sample shows how to run commands asynchronously by using the runspaces of a runspace pool.</span></span> <span data-ttu-id="b41b5-109">Örnek komutların bir listesini oluşturur ve gerektiğinde Windows PowerShell altyapısı havuzdan bir çalışma alanı açılırken komutları çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="b41b5-109">The sample generates a list of commands, and then runs those commands while the Windows PowerShell engine opens a runspace from the pool when it is needed.</span></span>