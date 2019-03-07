---
title: Uzak çalışma alanı örnekleri | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c44df35-b22b-41b0-b34c-ba7ce17b889b
caps.latest.revision: 7
ms.openlocfilehash: e11197e4f919519945ad3846dfef99c9e292aa9a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851110"
---
# <a name="remote-runspace-samples"></a><span data-ttu-id="dc1f3-102">Uzak Çalışma Alanı Örnekleri</span><span class="sxs-lookup"><span data-stu-id="dc1f3-102">Remote Runspace Samples</span></span>

<span data-ttu-id="dc1f3-103">Bu bölüm, WS-Yönetimi tabanlı Windows PowerShell uzaktan iletişimi'ni kullanarak bir bilgisayara bağlanmak için kullanılan çalışma alanları oluşturma işlemini gösteren örnek kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="dc1f3-103">This section includes sample code that shows how to create runspaces that can be used to connect to a computer by using WS-Management-based Windows PowerShell remoting.</span></span> <span data-ttu-id="dc1f3-104">Microsoft Visual Studio, bir konsol uygulaması oluşturun ve ardından kodu bu bölümdeki konular ana uygulamanıza kopyalamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dc1f3-104">You can use Microsoft Visual Studio to create a console application and then copy the code from the topics in this section into your host application.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="dc1f3-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="dc1f3-105">In This Section</span></span>

> [!NOTE]
> <span data-ttu-id="dc1f3-106">Uzak bir bilgisayarda komutları çalıştırma hakkında daha fazla bilgi için bkz. [Windows PowerShell uzaktan iletişimini](https://msdn.microsoft.com/en-us/library/ee706563(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="dc1f3-106">For more information about running commands on a remote computer, see [Windows PowerShell Remoting](https://msdn.microsoft.com/en-us/library/ee706563(v=vs.85).aspx).</span></span>
> <span data-ttu-id="dc1f3-107">Uzak bir bilgisayarda komutları çalıştırma hakkında daha fazla bilgi için bkz. [Windows PowerShell uzaktan iletişim] (https://msdn.microsoft.com/en-us/library/ee706563(v=vs.85).</span><span class="sxs-lookup"><span data-stu-id="dc1f3-107">For more information about running commands on a remote computer, see [Windows PowerShell Remoting](https://msdn.microsoft.com/en-us/library/ee706563(v=vs.85).</span></span>

 <span data-ttu-id="dc1f3-108">[RemoteRunspace01 örnek](./remoterunspace01-sample.md) Bu örnek, bir uzak bağlantı kurmak için kullanılan bir uzak çalışma alanı oluşturma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="dc1f3-108">[RemoteRunspace01 Sample](./remoterunspace01-sample.md) This sample shows how to create a remote runspace that is used to establish a remote connection.</span></span>

 <span data-ttu-id="dc1f3-109">[RemoteRunspacePool01 örnek](./remoterunspacepool01-sample.md) bir uzak çalışma alanı havuzu oluşturun ve bu havuzu kullanarak aynı anda birden çok komut çalıştırmak bu örnek gösterir.</span><span class="sxs-lookup"><span data-stu-id="dc1f3-109">[RemoteRunspacePool01 Sample](./remoterunspacepool01-sample.md) This sample shows how to construct a remote runspace pool and how to run multiple commands concurrently by using this pool.</span></span>

## <a name="see-also"></a><span data-ttu-id="dc1f3-110">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="dc1f3-110">See Also</span></span>